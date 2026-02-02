# The Algorithm — v0.2.26 Release Notes

**Release date:** 2026-01-31
**Full spec:** See [TheAlgorithm_v0.2.34.md](TheAlgorithm_v0.2.34.md) for the complete current specification.

## What's New in v0.2.26

- **Concise Voice Line (8-24 words)** — The voice line at the end of every response MUST be 8-24 words. Internal Algorithm phases remain detailed for quality. Only the spoken summary is constrained. Added to Common Failures.

## Key Sections Added

### Voice Line Constraint (NEW in v0.2.26)

The voice line at the end of every response MUST be **8-24 words**. This is the spoken summary the user hears. It must be concise, direct, and conversational.

**This applies to ALL depth levels** — FULL, ITERATION, and MINIMAL.

| Constraint | Value |
|------------|-------|
| **Minimum** | 8 words |
| **Maximum** | 24 words |
| **Tone** | Conversational, direct, like talking to a peer |
| **Content** | What was done + key result. No filler. |

**Examples (good):**
- "Updated the hook with all ten capabilities. Planning and custom agents route correctly now." (15 words)
- "Algorithm v0.2.29 is live with timing-aware execution across all agents." (10 words)
- "Fixed the bug in the auth middleware. Tests pass." (9 words)

**Examples (bad):**
- "Done." (1 word — too short, no information)
- "I've completed the comprehensive update to the CapabilityRecommender hook which now includes all ten capability types..." (49 words — way too long)

**The internal Algorithm phases (OBSERVE through LEARN) are NOT constrained.** They should be as detailed as needed for quality work. Only the final voice line is constrained.
