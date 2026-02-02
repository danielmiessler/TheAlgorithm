# The Algorithm — v0.2.33 Release Notes

**Release date:** 2026-02-02
**Full spec:** See [TheAlgorithm_v0.2.34.md](TheAlgorithm_v0.2.34.md) for the complete current specification.

## What's New in v0.2.33

- **Continuous Recommendation** — Replaces Two-Pass Capability Selection. The CapabilityRecommender hook is now re-invocable at any phase boundary with enriched context. Pass 1 fires automatically on UserPromptSubmit with the raw prompt. Pass 2 is explicitly re-invoked in THINK with OBSERVE findings and ISC criteria. Optional Pass N at later phases when significant new information emerges. Each pass produces a more informed capability matrix.
- **Dynamic Ecosystem Discovery** — The hook reads `Agents/` directory and `skill-index.json` at runtime instead of hardcoded agent and skill lists. Agents with "Researcher" in the name are identified as research-capable. The Agents skill enables custom agent composition. When new agents or skills are added, the hook automatically discovers them — no code changes needed.
- **Smart Tier Inference** — CapabilityRecommender now uses smart tier (Opus) instead of standard (Sonnet) for deeper strategic reasoning about capability composition.
- **Holistic Capability Matrix** — Hook output is now a coherent strategy with: strategy summary, recommended agents (with roles and counts), skills, thinking tools, timing, composition pattern, sequence, quality requirements, and constraints. Replaces prescriptive "use this exact agent" recommendations.
- **Strategy-First Output** — The capability matrix includes a `strategy` field — a natural language summary of the recommended approach. This is the most important field. Agents, skills, and patterns are tactical details that implement the strategy.
- **Updated THINK Phase Template** — Now includes RE-CLASSIFY step showing Pass 1 vs Pass 2 evolution. CAPABILITY SELECTION renamed to CAPABILITY MATRIX.
- **Updated Available Capabilities** — References Agents/ directory instead of hardcoded agent table. Categories instead of individual names.
- **Updated Common Failures** — Added: hardcoding agent/skill lists, skipping Pass 2 re-invocation, treating matrix as checklist.
- **Philosophy Principle #12** — "Trust the intelligence, feed it the ecosystem."

## Key Sections Added

### Continuous Recommendation (v0.2.33, replaces Two-Pass Selection)

The CapabilityRecommender produces a **holistic capability matrix** — not a prescriptive list of agents to use.

#### How It Works

The hook is **re-invocable**. It can run multiple times during a single response:

| Pass | When | Input | Authority |
|------|------|-------|-----------|
| **Pass 1** | UserPromptSubmit (automatic) | Raw prompt only | Draft — starting point |
| **Pass 2** | After OBSERVE completes | Raw prompt + reverse-engineering + ISC criteria | Refined — informed by context |
| **Pass N** | Any phase boundary (optional) | All prior context + phase-specific findings | Most informed — best recommendation |

#### The Capability Matrix

```json
{
  "depth": "FULL",
  "strategy": "Redesign the hook architecture using pipeline pattern",
  "agents": [
    { "type": "Architect", "role": "Design the new hook interface", "count": 1 },
    { "type": "Engineer", "role": "Implement hook changes", "count": 1 }
  ],
  "skills": ["CreateSkill:UpdateSkill"],
  "thinking": ["firstprinciples", "council"],
  "timing": "deep",
  "pattern": "Pipeline",
  "sequence": "Architect -> [Engineer, Engineer]",
  "quality": "High — architectural change affecting all future sessions",
  "constraints": ["Must maintain backward compatibility"]
}
```

The strategy field is the most important — it's the natural language summary of the recommended approach.

### Dynamic Ecosystem Discovery

The hook reads the ecosystem at runtime instead of hardcoding agent and skill lists:

**Agents:** Reads the `Agents/` directory. Each `.md` file is an agent type. Agents with "Researcher" in the name are research-capable.

**Skills:** Reads `skill-index.json`. Each entry has a name, description, workflows, and tier.

**Benefit:** When new agents or skills are added to the ecosystem, the hook automatically discovers them. No code changes needed.

### Why Continuous Recommendation?

| Phase | New Information | Impact on Recommendation |
|-------|----------------|--------------------------|
| OBSERVE | Reverse-engineering reveals hidden requirements | Changes which agents and skills are needed |
| THINK | ISC criteria crystallize success conditions | Changes quality level and pattern |
| BUILD | Implementation reveals unexpected complexity | Changes timing and agent count |
| EXECUTE | Partial results show approach isn't working | Changes approach entirely via retry |

### Philosophy Addition

**Principle #12:** "Trust the intelligence, feed it the ecosystem — don't hardcode what agents or skills exist. Discover them dynamically, give the model the map, and let strategic reasoning do the routing."
