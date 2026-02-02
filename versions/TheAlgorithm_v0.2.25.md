# The Algorithm — v0.2.25 Release Notes

**Release date:** 2026-01-30
**Full spec:** See [TheAlgorithm_v0.2.34.md](TheAlgorithm_v0.2.34.md) for the complete current specification.

## What's New in v0.2.25

- **Parallel-by-Default Execution** — Independent tasks MUST run concurrently via parallel agent spawning. Serial execution is only for tasks with data dependencies. Fan-out is the default pattern for 3+ independent workstreams. Added to Common Failures: sequential execution of independent tasks.

## Key Sections Added

### Parallel Execution (NEW in v0.2.25)

#### The Parallel Principle

When the BUILD/EXECUTE phase has multiple independent tasks (no data dependencies between them), they **MUST** be launched as concurrent agents in a **SINGLE message** with multiple Task tool calls. Serial execution of independent tasks is a failure mode.

**The Rule:** "If tasks don't depend on each other, they run at the same time. Period."

#### Dependency Analysis

Before executing, classify each task as:

| Classification | Definition | Action |
|----------------|-----------|--------|
| **Independent** | No input from other tasks, can run immediately | Launch in parallel |
| **Dependent** | Requires output from another task, must wait | Execute after dependency completes |

#### Fan-out is Default

When ISC criteria map to 3+ independent workstreams, use the **Fan-out** pattern automatically. Don't ask, don't wait, just launch them all.

This applies to:
- Multiple file edits with no cross-dependencies
- Multiple research queries on different topics
- Multiple audits/scans of independent systems
- Multiple creation tasks with no shared state

#### Parallel vs Serial Examples

| Execution | Tasks | Why |
|-----------|-------|-----|
| **PARALLEL** | Fix file A + Fix file B + Fix file C | Independent files, no shared state |
| **PARALLEL** | Research topic + Scan for patterns + Audit files | Independent investigations, no data flow between them |
| **SERIAL** | Read file -> Edit file -> Verify edit | Each step depends on the previous step's output |
| **SERIAL** | Create branch -> Commit -> Push | Sequential git operations, strict ordering required |

#### How It Works in Practice

1. **PLAN phase** identifies all tasks from ISC criteria
2. **BUILD/EXECUTE phase** classifies each task as Independent or Dependent
3. All Independent tasks launch simultaneously as parallel agents in one message
4. Dependent tasks wait for their prerequisites, then launch
5. **VERIFY phase** collects results from all parallel streams

This is not optional. When independent tasks exist and you execute them one at a time, you are wasting the user's time. The Algorithm demands parallel execution as the default.
