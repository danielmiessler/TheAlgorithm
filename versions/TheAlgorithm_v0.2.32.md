# The Algorithm — v0.2.32 Release Notes

**Release date:** 2026-02-02
**Full spec:** See [TheAlgorithm_v0.2.34.md](TheAlgorithm_v0.2.34.md) for the complete current specification.

## What's New in v0.2.32

- **Structured Evidence Requirements** — ISC verification now requires three fields: evidence type (screenshot/test_output/file_content/tool_result/manual_check), evidence source (which tool or file), and evidence content (actual proof, cannot be empty). Closes the "8/8 PASSED with no proof" gap.
- **Retry Loop** — When VERIFY has failed criteria, enters DIAGNOSE -> CHANGE -> RE-EXECUTE loop (max 3 iterations). Change is mandatory — re-running the same approach is explicitly prohibited. Root cause must be owned, not blamed on external factors.
- **Ownership Check in VERIFY** — VERIFY phase now begins with a mandatory ownership check: state the approach taken, alternatives that existed, and whether you'd choose the same approach again. Catches the failure mode where the wrong approach "passes" verification because ISC criteria were technically met but the user's actual need wasn't served.
- **Updated FULL Mode Format** — VERIFY template now shows ownership check and structured evidence format.
- **Updated Common Failures** — Added: ISC complete without evidence, retrying same approach, skipping ownership check, blaming external factors.
- **Philosophy Principle #11** — "Verify with evidence, retry with change."
- **Hook Rename: FormatReminder -> CapabilityRecommender** — The UserPromptSubmit hook was renamed to reflect its actual function: AI-powered prompt classification across 5 dimensions (depth, capabilities, skills, thinking tools, timing). The "FormatReminder" name was a vestige of v0.2.20 when the hook literally reminded the model to use the Algorithm format. It now recommends capabilities for the Continuous Recommendation system. All active references updated; historical changelog entries preserved with original name.

## Key Sections Added

### Evidence Requirements (NEW in v0.2.32)

When marking an ISC criterion as completed, you MUST provide three pieces of structured evidence:

| Field | Required | Description |
|-------|----------|-------------|
| **Evidence Type** | Yes | `screenshot`, `test_output`, `file_content`, `tool_result`, or `manual_check` |
| **Evidence Source** | Yes | Which tool or file produced the proof |
| **Evidence Content** | Yes | The actual proof — **CANNOT be empty** |

#### What Counts as Evidence

| Evidence Type | Good Example | Bad Example |
|---------------|-------------|-------------|
| `screenshot` | "Browser screenshot shows login form rendered correctly" | "Page looks fine" |
| `test_output` | "bun test: 12 passed, 0 failed, 0 skipped" | "Tests pass" |
| `file_content` | "Line 47 of auth.ts now reads `if (!token) return 401`" | "Code updated" |
| `tool_result` | "curl returns 200 with body `{\"status\":\"ok\"}`" | "API works" |
| `manual_check` | "Grep for 'API_KEY' in repo returns 0 matches" | "No secrets found" |

### Ownership Check (NEW in v0.2.32)

The three mandatory questions before grading ISC:

| Question | What It Catches |
|----------|----------------|
| **What approach did I take?** | Forces explicit statement of the choice made |
| **What alternatives existed?** | Surfaces paths not taken |
| **Would I choose the same approach again?** | Catches regret before it becomes "8/8 PASSED" on wrong work |

### Retry Loop (NEW in v0.2.32)

```
--- RETRY (Iteration 1/3) ---

DIAGNOSE:
| Failed:     [which ISC criteria failed]
| Root cause: [why — not external blame, what I did wrong]
| Evidence:   [what specifically went wrong]

CHANGE:
| Different:  [what will be materially different this time]
| Why:        [evidence this change addresses root cause]

RE-EXECUTE:
[Execute the changed approach]

-> Return to VERIFY
```

**Rules:**
1. Max 3 iterations — then escalate to user
2. Change is mandatory — cannot re-run same approach
3. Root cause, not blame — own the diagnosis
4. Tool variation — if same tool failed twice, try different approach

### Philosophy Addition

**Principle #11:** "Verify with evidence, retry with change — claims without proof are assumptions. Failures without diagnosis are coin flips. Own the outcome."
