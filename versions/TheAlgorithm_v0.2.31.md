# The Algorithm — v0.2.31 Release Notes

**Release date:** 2026-02-02
**Full spec:** See [TheAlgorithm_v0.2.34.md](TheAlgorithm_v0.2.34.md) for the complete current specification.

## What's New in v0.2.31

- **Structural Agent Enforcement** — New `AgentExecutionGuard` hook (PreToolUse on Task) warns on every foreground agent spawn. Instructions degraded under context pressure; hooks fire regardless. This closes the enforcement gap that v0.2.27-v0.2.30 tried to solve with text alone.
- **Enforcement Gap Analysis** — New section documenting why v0.2.30's instructional-only approach failed. Three root causes: instructions degrade under context pressure, foreground is the easy default, no consequence for violations.
- **Hook Decision Tree** — AgentExecutionGuard uses a fast decision tree: background=true->pass, Explore->pass, haiku->pass, FAST scope->pass, else->warn. No blocking, no I/O, <10ms.
- **Philosophy Principle #10** — "Enforce structurally, not instructionally." When a rule matters, use a hook.
- **Updated Common Failures** — "Relying on instructions when hooks exist" added. Foreground agent failure now annotated as "ENFORCED v0.2.31."
- **Three-Layer Architecture** — Detection (CapabilityRecommender) -> Enforcement (AgentExecutionGuard) -> Capture (AgentOutputCapture). The missing middle layer is now filled.

## Key Sections Added

### Agent Execution — Structurally Enforced (v0.2.31)

#### The Enforcement Gap (Why v0.2.30 Failed)

v0.2.27 through v0.2.30 added progressively stronger TEXT about background execution. None of it worked consistently because:
- Instructions compete with 15K+ tokens of other instructions
- The "easy path" (foreground) requires zero effort; background requires explicit params
- No structural mechanism prevented foreground agents from spawning
- No consequence existed for violations

**v0.2.31 fixes this with a PreToolUse hook (`AgentExecutionGuard`) that fires on every Task call.**

#### How Enforcement Works

```
PreToolUse:Task -> AgentExecutionGuard
  |-- run_in_background: true  -> PASS (silent)
  |-- model: "haiku"           -> PASS (fast-tier)
  |-- subagent_type: "Explore" -> PASS (quick lookup)
  |-- prompt contains FAST     -> PASS (scoped fast)
  |-- all other cases          -> WARNING injected
```

#### The Principle: Enforce Structurally, Not Instructionally

| Approach | Mechanism | Reliability |
|----------|-----------|-------------|
| Instructional | "Please do X" in system prompt | ~60% — degrades with context pressure |
| Structural | Hook fires at point of action | ~95% — fires regardless of context |

**When a rule matters, enforce it with a hook. When it's a preference, instruct it in the system prompt.**

### Three-Layer Architecture

```
Detection:    CapabilityRecommender (UserPromptSubmit)
Enforcement:  AgentExecutionGuard (PreToolUse:Task)
Capture:      AgentOutputCapture (PostToolUse:Task)
```

The missing middle layer (Enforcement) is now filled. Detection tells the agent what to do. Enforcement catches violations at the point of action. Capture records results for learning.

### Philosophy Addition

**Principle #10:** "Enforce structurally, not instructionally — when a rule matters, use a hook. Instructions degrade under context pressure; hooks fire regardless."
