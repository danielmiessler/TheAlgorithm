# The Algorithm — v0.2.29 Release Notes

**Release date:** 2026-02-01
**Full spec:** See [TheAlgorithm_v0.2.34.md](TheAlgorithm_v0.2.34.md) for the complete current specification.

## What's New in v0.2.29

- **Timing-Aware Execution** — New timing classification (fast|standard|deep) flows from hook through main agent to all sub-agents. Quick questions get concise answers; deep work gets thorough analysis. Hook classifies timing in Pass 1, THINK validates in Pass 2.
- **Agent Prompt Scoping** — Every agent prompt MUST include a `## Scope` section with the validated timing tier. Agents without scope default to verbose, wasting time on simple tasks.
- **Timing in Capability Selection** — THINK phase Capability Selection block now includes a `Timing:` line showing the validated tier and override reason if applicable.
- **Model Selection Interaction** — Timing tier influences preferred model: fast->haiku, standard->sonnet, deep->opus. Preference, not hard rule.
- **Updated Two-Pass Selection** — Pass 1 now includes timing hints. Pass 2 validates timing against reverse-engineered request and ISC criteria.
- **Updated Common Failures** — Added: missing timing scope in agent prompts, ignoring timing hint from hook.
- **Updated Philosophy** — Added principle: "Scope matches intent."

## Key Sections Added

### Timing-Aware Execution (NEW in v0.2.29)

#### The Problem

Sub-agents don't know how much effort is appropriate. A quick status check spawns an agent that writes 1500 words of analysis. A deep architecture review gets a surface-level response. The mismatch wastes time (too much) or quality (too little).

#### Timing Tiers

| Tier | When | Agent Output | Target Time | Model Preference |
|------|------|-------------|-------------|------------------|
| **fast** | Quick lookup, simple question, status check, single fact | Under 500 words, direct answer, no preamble | < 1 min | haiku |
| **standard** | Normal implementation, typical work, moderate analysis | Focused work, under 1500 words | 1-3 min | sonnet |
| **deep** | User explicitly says "comprehensive", "thorough", "extensive", "full audit" | Full analysis, no word limit | As needed | opus |

**Default:** `standard`. When in doubt, standard is correct.

#### The Signal Chain

```
1. Hook classifies timing (fast|standard|deep) from raw prompt
2. Main agent reads hint in system-reminder
3. THINK phase validates timing against OBSERVE (Pass 2)
4. Every agent prompt includes ## Scope with time budget
5. Agents respect constraints
```

#### Agent Prompt Scoping

When spawning any agent, include a `## Scope` section in the prompt that matches the validated timing tier:

**fast:**
```
## Scope
Timing: FAST — direct answer only.
- Under 500 words
- No preamble, no exploration, no alternatives
- Answer the question, report the result, done
```

**standard:**
```
## Scope
Timing: STANDARD — focused implementation.
- Under 1500 words
- Stay on task, minimal tangents
- Deliver the work, verify it works
```

**deep:**
```
## Scope
Timing: DEEP — comprehensive analysis.
- No word limit
- Explore alternatives, consider edge cases
- Thorough verification and documentation
```

#### Model Selection Interaction

| Timing | Preferred Model | Rationale |
|--------|----------------|-----------|
| **fast** | `haiku` | Speed over depth. Simple tasks don't need heavy models. |
| **standard** | `sonnet` | Balance of capability and speed. Default for most work. |
| **deep** | `opus` | Maximum intelligence for comprehensive analysis. |

### Philosophy Addition

**Principle #9:** "Scope matches intent — a quick question deserves a quick answer, deep work deserves deep analysis."
