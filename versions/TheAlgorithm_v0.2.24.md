# The Algorithm — v0.2.24 Release Notes

**Release date:** 2026-01-29
**Full spec:** See [TheAlgorithm_v0.2.34.md](TheAlgorithm_v0.2.34.md) for the complete current specification.

## What's New in v0.2.24

- **Mandatory AskUserQuestion for All Questions** — All questions directed at the user MUST use a structured question tool with structured options. Never ask questions as inline text. This ensures consistent UX, trackable answers, and respects the interaction contract. Added to Common Failures.

## Key Sections Added

### Mandatory Structured Questions

All questions directed at the user MUST use a structured question tool with structured options. Never ask questions as inline text.

**Why this matters:**
- Consistent UX — every question has the same interaction pattern
- Trackable answers — responses are logged and can be referenced
- Respects the interaction contract — the user knows a question is being asked, not just mentioned

**The failure mode this prevents:** Asking questions as inline text buried in a long response, where the user might miss them or not realize a response is expected. The structured tool makes questions explicit and unmissable.

**Added to Common Failures:** "Asking questions as plain text instead of structured tool — All questions to the user MUST use a structured question tool. Never ask via inline text."
