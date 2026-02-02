# The Algorithm — v0.2.28 Release Notes

**Release date:** 2026-02-01
**Full spec:** See [TheAlgorithm_v0.2.34.md](TheAlgorithm_v0.2.34.md) for the complete current specification.

## What's New in v0.2.28

- **Git Worktrees** — New capability for parallel solution attempts using isolated git worktrees. When multiple valid approaches exist for the same problem, spawn separate worktrees with independent agents instead of picking one approach and hoping. Each agent works in full isolation on its own branch.
- **Tournament Composition Pattern** — New pattern `[A, B, C] -> Evaluate -> Winner` for competing solutions. Differs from Fan-out (all results used) in that only the best solution gets merged.
- **Worktrees in Capability Selection** — THINK phase now includes worktree-specific fields (approach descriptions, evaluator agent) when Tournament pattern is selected.
- **Updated Available Capabilities** — Added Worktrees alongside Research, Engineer, Architect, etc.
- **Updated Composition Patterns** — Added Tournament pattern to the named patterns table.

## Key Sections Added

### Git Worktrees (NEW in v0.2.28)

#### The Problem Worktrees Solve

Parallel agents run concurrent tasks within the **same working tree**. This works for independent work items on different files. But when multiple agents need to try different approaches to the **same problem** — touching the same files — they conflict.

Git worktrees solve this by giving each agent its own checked-out copy of the repo on a separate branch. Each agent works in full isolation. Then you compare results and merge the winner.

#### When to Use Worktrees

| Use Worktrees | Use Parallel Agents |
|---------------|---------------------|
| Multiple valid approaches to the **same** problem | Independent tasks on **different** files |
| Complex refactoring with competing strategies | Simple, non-conflicting work items |
| "Try it N ways and pick the best" | "Do N independent things at once" |
| Agents would edit the **same files** differently | Agents touch **different files** |

#### How It Works

```
1. PLAN identifies N competing approaches
2. CREATE worktrees (one per approach)
3. LAUNCH agents in parallel (one per worktree)
4. EVALUATE results against ISC criteria
5. MERGE winner back
6. CLEAN UP worktrees
```

### The Tournament Pattern

```
Shape:  [A, B, C] -> Evaluate -> Winner
Where:  Each competitor runs in its own worktree
```

- **Fan-out** = independent tasks, all results used -> `[A, B, C] -> D`
- **Tournament** = competing solutions to same problem, best one wins -> `[A, B, C] -> Evaluate -> Winner`

#### Practical Constraints

- **Max worktrees:** 3-5
- **Cleanup is mandatory** — always remove worktrees after merging
- **Each worktree gets its own agent** — isolation is the point
- **Use `/tmp/` for worktree paths**

### Philosophy Addition

**Principle #8:** "Compete, don't guess — when multiple approaches are viable, try them all in parallel and pick the winner."
