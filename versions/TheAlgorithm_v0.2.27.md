# The Algorithm — v0.2.27 Release Notes

**Release date:** 2026-01-31
**Full spec:** See [TheAlgorithm_v0.2.34.md](TheAlgorithm_v0.2.34.md) for the complete current specification.

## What's New in v0.2.27

- **Never-Block Rule** — Operations > 10 seconds MUST run as background agents with progress reporting. User interface never locks during long tasks.
- **TIME TRIAGE** — New mandatory section in PLAN phase. Estimate duration, choose execution mode (inline/background/background+updates), set update intervals.
- **Quick Answer First Pattern** — For verification tasks, report result immediately, then offer to investigate. Don't block user with automatic deep dives.
- **Background Agent Patterns** — Documented patterns for async execution with progress updates. Clear thresholds for inline vs background execution.
- **Updated Common Failures** — Added: blocking user > 10s, missing TIME TRIAGE, over-investigating before answering.
- **Updated Philosophy** — Added principle: "Time matters — user attention is precious, never block without reason."

## Key Sections Added

### Never-Block Rule (NEW in v0.2.27)

#### The Core Principle

**Never lock the user out of the interface.** Any operation expected to take > 10 seconds MUST run as a background agent with progress reporting.

#### Execution Mode Decision Tree

Use TIME TRIAGE in PLAN phase to classify:

| Duration | Mode | Pattern |
|----------|------|---------|
| **< 10s** | Inline | Run directly, report result |
| **10s - 2min** | Background | Spawn agent with `run_in_background: true`, report when done |
| **> 2min** | Background + Updates | Spawn agent, check progress every 30s-1min, report updates |

#### TIME TRIAGE (PLAN Phase)

```
TIME TRIAGE:
| Estimated duration: [5s | 30s | 2min | 10min+]
| Execution mode:     [inline | background | background+updates]
| Update interval:    [none | 30s | 1min | on-completion]
| Reason:             [why this timing/mode]
```

#### Quick Answer First

For verification/testing tasks:
1. Run the test (inline or background)
2. Report result IMMEDIATELY when available
3. Offer: "Want me to investigate why?" if it failed
4. Only investigate if user says yes
5. Investigation runs in background if > 10s

#### What Runs in Background

**MUST use background mode:**
- Agent spawns expected to take > 10s
- Multi-file searches across large codebases
- Network operations (scraping, API calls with retries)
- LLM calls > 2000 tokens
- Pipeline/workflow execution
- Browser automation tests
- Any investigation/debugging work

**CAN run inline:**
- Single file reads < 1MB
- Quick command execution (< 5s)
- Simple calculations
- Status checks
- File writes

### Philosophy Addition

**Principle #7:** "Time matters — user attention is precious, never block without reason."
