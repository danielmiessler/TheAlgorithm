<div align="center">
  <img src="assets/algorithm-blocks.png" alt="TheAlgorithm" width="600">

  # TheAlgorithm

  **An experiment in systematic problem-solving**

  [![Docs](https://img.shields.io/badge/docs-reference-blue.svg)](./TheAlgorithm.md)
  [![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
  [![LifeOS](https://img.shields.io/badge/LifeOS-integrated-purple.svg)](https://github.com/danielmiessler/LifeOS)
  [![Status](https://img.shields.io/badge/status-experimental-orange.svg)]()

  [The Idea](#the-idea) • [How It Works](#how-it-works) • [LifeOS Integration](#-lifeos-integration) • [Versioning](#versioning) • [Documentation](#documentation)
</div>

---

## 🎯 The Idea

TheAlgorithm is the universal mechanism inside [LifeOS](https://github.com/danielmiessler/LifeOS) — the **Life Operating System** I'm building to magnify human capability. LifeOS turns AI from a chatbot you talk to into a system that runs your life — knowing your goals, people, workflows, current state, and ideal state — and continuously hill-climbs you from one to the other. The mechanism that does the climbing is TheAlgorithm.

It's universal because every task — shipping code, writing an essay, making a hire, sending an email, designing a feature — is a transition from **CURRENT STATE → IDEAL STATE** pursued through verifiable iteration.

The bigger story is the **Human 2.0 → Human 3.0** transition: from corporate existence where value is defined by job title, to creative self-expression where individuals define themselves through unique value creation. AI is what makes that possible — but only if you have the scaffolding to point it at your real life, your real goals, and your real definition of "done." LifeOS is the scaffolding. TheAlgorithm is what runs at its center.

**The goal:** Euphoric Surprise — answers that click in a way you couldn't have predicted but instantly recognize as true.

**The method:** Reverse-engineer vague human intent into a hard-to-vary explanation of "done," then hill-climb against it with verifiable iteration.

---

## 💡 The Core Insight (David Deutsch)

Knowledge is **hard-to-vary explanation** — a description of reality (or of a goal) where every detail plays a functional role, so contrary evidence has nowhere to flee. That's what Ideal State Criteria (ISC) are: the irreducible, independently verifiable structure of "done."

Most goals enter the system as **opacity** — vague human intent, half-articulated, riddled with implicit assumptions. The job of TheAlgorithm is **opacity → transparency**: reverse-engineer the request into an explicit, articulated, testable spec — the PRD — and then climb against it. Articulation is the act of making the implicit explicit. The PRD is where articulation lives.

Three system-level tests every PRD must pass (v4.0.0 doctrine):

- **Coverage** — every facet of "done" is captured by at least one ISC (no gaps)
- **Tightness** — no subset of ISCs could be removed while still satisfying the goal (no aggregate redundancy)
- **Uniqueness** — no meaningfully different ISC set would satisfy the same goal (the goal is precisely specified, not under-determined)

A good PRD cannot be varied without destroying the goal. A bad PRD has fluff that could be weakened without changing the outcome. The continuous test, applied at every phase: *"Can I vary this without destroying the goal? If yes, it needs refinement."*

**Euphoric surprise is the experiential side of the same coin.** Hard-to-variability is the *epistemic* test of a good explanation; euphoric surprise is what it *feels like* to encounter one. They aren't separate optimization targets — they're the same phenomenon viewed from inside vs. outside. If the PRD captures the goal as a hard-to-vary explanation, and the work satisfies the PRD, the user encounters a hard-to-vary explanation in form — and that produces the 9–10 rating.

<div align="center">
  <img src="assets/algorithm-foundational.png" alt="Algorithm Foundational Concepts" width="900">
  <p><em>Current → Ideal State, via verifiable iteration against a hard-to-vary explanation</em></p>
</div>

---

## ⚙️ How It Works

Six pieces compose TheAlgorithm:

### 1. Seven Discrete Phases
Inspired by the scientific method. Always separate, always announced via voice transitions.

```
OBSERVE  → Intent Echo; reverse-engineer the request; preflight gates; reproduce-first; write ISCs
THINK    → PRD-level Hard-to-Vary Audit (Coverage / Tightness / Uniqueness); per-ISC variation test
PLAN     → Enumerate deliverables; choose capabilities; consult feedback memory; scan for parallelism
BUILD    → Create the artifacts
EXECUTE  → Run them; verify each ISC inline against tool evidence — never "should work"
VERIFY   → Live-Probe (Rule 1); Commitment-Boundary Advisor (Rule 2); Cross-Vendor Audit at E4/E5 (Rule 2a); Fluff Sweep
LEARN    → Re-Read Check against the user's original message; capture insight; close the loop
```

### 2. Ideal State Criteria (ISC) with Six Categories
Every ISC is atomic, 8–12 words, binary testable, and tagged:

| Tag | Meaning | Constraint |
|-----|---------|-----------|
| `[F]` | Functional — core behavior, correctness | No limit |
| `[S]` | Structural — files, patterns, architecture | Max 40% of total |
| `[B]` | Behavioral — runtime output, observable results | Min 20% of total |
| `[N]` | Negative — must NOT happen, no regressions | Min 2 per PRD |
| `[E]` | Edge — prerequisites, error handling, boundaries | Min 10% of total |
| `[A]` | Antecedent — preconditions for experiential outcomes (novel juxtaposition, elegance in constraint) | Required ≥1 when goal is experiential |

Each ISC is one load-bearing component of the explanation. The PRD-level audit tests the system; per-ISC HVA tests the lines.

### 3. PRD as System of Record
Every Algorithm run writes a PRD to disk — the single source of truth for criteria, decisions, verification status, and phase state. PRDs survive across sessions and compactions. The AI writes; hooks read.

### 4. Effort Tiers (E1–E5)
Tasks scale across five tiers, with proportional doctrine weight:

| Tier | Budget | ISC Floor | When |
|------|--------|-----------|------|
| **E1 Standard** | <90s | 6 | Normal request (default) |
| **E2 Extended** | <3min | 14 | Quality must be extraordinary |
| **E3 Advanced** | <10min | 28 | Substantial multi-file work |
| **E4 Deep** | <30min | 48 | Complex design |
| **E5 Comprehensive** | <2hr+ | 72 | No time pressure |

Higher tiers earn the cost of full ceremony; lower tiers stay fast.

### 5. Verification Doctrine
Three rules govern every VERIFY pass — none optional:

- **Rule 1 (Live-Probe)** — no ISC flips to `[x]` without tool-based evidence captured in the same or following block. "Should work" is a failure condition.
- **Rule 2 (Commitment-Boundary Advisor)** — second-opinion gate before any durable deliverable. Mandatory at Extended+.
- **Rule 2a (Cross-Vendor Audit, Cato, E4/E5 only)** — GPT-5.4 via `codex exec` reviews the same artifacts the Anthropic-family Advisor reviewed, surfacing the blind spots same-vendor reviewers would share.

### 6. Euphoric Surprise
The end goal isn't passing the criteria — it's the experience the user has when they read the response. A hard-to-vary explanation arriving with novelty: an answer that clicks in a way they couldn't have predicted but instantly recognize as true. The doctrine doesn't try to manufacture this feeling — it builds the conditions where it can happen, then trusts the explanation to do the rest.

---

## 🔗 LifeOS Integration

I'm using this in LifeOS - every interaction follows the algorithm structure. It's working well so far, but I'm still experimenting.

### Configuration

LifeOS can load TheAlgorithm three ways:

**1. Always Latest (Default)**
```json
{
  "algorithmSource": "latest"
}
```
Pulls from: `TheAlgorithm.md` (main branch)

**2. Pin to Specific Version**
```json
{
  "algorithmSource": "v0.1"
}
```
Pulls from: `versions/v0.1.md` (doesn't change)

**3. Use Your Own Version**
```json
{
  "algorithmSource": "local",
  "algorithmLocalPath": "/path/to/your-algorithm.md"
}
```
Test your own ideas before publishing

### How LifeOS Uses It

```typescript
// LifeOS fetches at build time
const algorithm = await fetchAlgorithm({
  version: config.algorithmSource,
  cacheDir: "~/.claude/cache/algorithm",
  localOverride: process.env.ALGORITHM_LOCAL_OVERRIDE
});
```

**Caching:**
- Specific versions: Cached permanently
- Latest: Refreshes on builds
- Fallback: Uses bundled version if fetch fails

---

## 📦 Versioning

I'm using semantic versioning:

```
TheAlgorithm/
  TheAlgorithm.md           # Current version
  versions/
    v0.1.md                 # Frozen snapshots
    v0.2.md
  CHANGELOG.md              # What changed
```

**Version bumps:**
- **MAJOR** (0.x → 1.0): Breaking changes to format
- **MINOR** (0.1 → 0.2): New features, backward compatible
- **PATCH** (0.1.0 → 0.1.1): Typos, clarifications

| Your Config | Behavior |
|-------------|----------|
| `"latest"` | Auto-updates with each change |
| `"v0.1"` | Stays on v0.1 until you change it |
| `"local"` | Uses your file |

---

## 📚 Documentation

The full spec is in **[TheAlgorithm.md](./TheAlgorithm.md)**:
- All 7 phases in detail
- ISC criteria requirements
- Examples and anti-patterns
- Common failure modes

**To try it:**
1. Read the philosophy above to get the idea
2. Check out the spec to see how it works
3. Look at [LifeOS](https://github.com/danielmiessler/LifeOS) to see it in action
4. Fork it and try your own version

---

## 🎓 Key Concepts

### ISC (Ideal State Criteria)

Instead of "fix the auth bug", try:
- "All authentication tests pass after fix applied" (8 words, testable)

Instead of "improve the UI", try:
- "Login button centered on screen with correct spacing" (8 words, verifiable)

The constraint forces clarity.

### Anti-Criteria

What must NOT happen:
- "No credentials exposed in git commit history"
- "No breaking changes to existing public API endpoints"
- "Database migrations do not lose any user data"

### Euphoric Surprise

I'm aiming for reactions like:
- "Wow, I didn't expect that!"
- "This is exactly what I needed and more"
- "How did it know to do that?"

Instead of:
- "Good enough"
- "Met requirements"
- "No complaints"

Not sure if this is achievable consistently, but that's the experiment.

---

## 🔄 Version History

> The Algorithm has gone through five major eras since v0.1: the **0.x experimental era** (Jan–Feb 2026, format and ISC discovery), the **1.x consolidation** (Feb 2026, zero-delay output and effort-tier rebalancing), the **2.x → 4.x doctrine era** (Feb–Apr 2026, seven-phase enforcement, verification doctrine, hard-to-vary epistemology), the **5.x ISA-rename + checkpoint era** (Apr 2026, PRD → ISA vocabulary, BPE compaction, per-step durability), and the **6.x ISA-as-system-of-record + mode-classifier era** (Apr–May 2026, ISA elevated to universal primitive with five identities, twelve-section frame, classifier-driven mode selection, closed-enumeration thinking-capability vocabulary). Entries below are abridged — every version has its own embedded `CHANGES FROM …` block at the top of `versions/TheAlgorithm_vX.Y.Z.md`.

*Note: mode/tier selection was retired in mid-2026 — current LifeOS releases run a single unified loop. Kept here as history.*

### v6.3.0 (2026-04-29) — latest entry here; the shipping version lives in [LifeOS](https://github.com/danielmiessler/LifeOS)
- **Thinking-capability vocabulary closed-enumeration release** — the 19 thinking capabilities (IterativeDepth, ApertureOscillation, FeedbackMemoryConsult, Advisor, ReReadCheck, FirstPrinciples, SystemsThinking, RootCauseAnalysis, Council, RedTeam, Science, BeCreative, Ideate, BitterPillEngineering, Evals, WorldThreatModel, Fabric patterns, ContextSearch, ISA) are printed verbatim INSIDE the doctrine read at run time
- **Capability-Name Audit Gate** — fires at OBSERVE→THINK; thinking names in `🏹 CAPABILITIES SELECTED` must appear verbatim in the closed list, phantom names do NOT count toward the floor and are a CRITICAL FAILURE
- **Closed-enumeration discipline** — adding new thinking capabilities now requires editing `capabilities.md` AND bumping the Algorithm minor version + updating doctrine; closed-enum drift is no longer silent

### v6.2.0 (2026-04-28)
- **ISA twelve-section frame** — fixed-order body: Problem, Vision, Out of Scope, Principles, Constraints, Goal, Criteria, Test Strategy, Features, Decisions, Changelog, Verification
- **Three-guardrail taxonomy** — Principles bind the thinking, Constraints bind the solution space, Out of Scope binds the vision, Anti-criteria bind the test surface
- **Tier completeness gate (HARD)** — required sections per tier; E1 = Goal+Criteria; E4 = all twelve; E5 + active Interview workflow before BUILD
- **ISA Skill release** — owns the canonical template and six workflows (Scaffold, Interview, CheckCompleteness, Reconcile, Seed, Append); Algorithm OBSERVE invokes `Skill("ISA")` to scaffold, LEARN routes Decisions/Changelog/Verification through the canonical Append writer
- **ID-stability rule** — ISC IDs never re-number on edit (splits become ISC-N.M, drops become tombstones); makes deterministic Reconcile safe
- **Ephemeral feature files formalized** — Ralph Loop / Maestro pattern; derived view from master, ISC-keyed merge

### v6.1.0 (2026-04-28)
- **Thinking-floor hardening** — capability floor splits into two axes: thinking-capability count is now a HARD FLOOR that cannot be relaxed via show-your-math (E2 ≥2, E3 ≥4, E4 ≥6, E5 ≥8)
- **Delegation-capability count remains soft** and show-your-math relaxable (E2 ≥1, E3 ≥2, E4 ≥2, E5 ≥4)
- Closes the v6.0.0 escape valve where "show your math" was used to skip thinking-capability floors entirely on Deep tasks

### v6.0.0 (2026-04-27)
- **Frame shift release: ISA elevated to universal primitive with five identities** — ideal state articulation, test harness, build verification, done condition, hard-to-vary explanation. One document, no parallel acceptance.yaml/acceptance.ts artifacts
- **Unit reframed from "task" to "thing being articulated"** — project ISAs at `<project>/ISA.md` for any persistent thing (apps, CLI tools, libraries, content pipelines, the Algorithm itself); task ISAs at `MEMORY/WORK/{slug}/ISA.md` for ad-hoc one-shot work
- **Mode-selection regression fixed** — deterministic NATIVE→ALGORITHM floor via 5 triggers (doctrine-affecting, architectural-locator, multi-project, soft-user-signal, hard-to-vary) plus 3-axis test (retrievability/blast-radius/hard-to-vary depth)
- **Capability floors restored at v4.1.0 numbers** — soft floors with "show your math" override

### v5.7.0 (2026-04-27)
- ISA-as-living-articulation reframing — explicit doctrine that the ISA evolves through pursuit, with `refined:` decisions logged inline and git history as the trail

### v5.6.0 (2026-04-27)
- **Master-loop reframing** — doctrine intro tightens to "moving people from current state to ideal state by writing down what done looks like as testable claims, then refining the writing until every claim survives every test it can be subjected to"
- **Testability declared identical to hard-to-variability operationalized** — same property, two angles
- ISA-Level audit (Coverage / Tightness / Uniqueness) recurs at every phase boundary, not just THINK

### v5.5.0 (2026-04-27)
- BPE compaction: dropped the residual `ISC-A-N` numbering convention for anti-criteria

### v5.4.0 (2026-04-27)
- **Unified Learning Router in LEARN phase** — replaces the narrow "Knowledge capture" step with a router that handles every kind of learning: knowledge, operational rules, skill gotchas, project state, business facts, identity edits, doctrine changes, hook proposals, permission changes
- Routing table mirrors LifeOS Self-Healing Infrastructure so Algorithm and constitution agree
- Documentation-sync downstream: any inline write to a system file triggers documentation-update workflow

### v5.3.0 (2026-04-27)
- **BPE-driven removal of ISC category tags** — `[F]`/`[S]`/`[B]`/`[N]`/`[E]`/`[A]` deleted from on-disk format; collapses to `- [ ] ISC-N: criterion text`
- Two doctrinal kinds preserved as prefix conventions, not bracket letters: anti-criteria via `Anti:` prefix, antecedent via `Antecedent:` prefix
- Parser is backward-compatible — legacy bracketed ISAs still parse

### v5.2.0 (2026-04-26)
- Reintroduces per-tier ISC count floors at E2+ as soft minimums on the count axis only: E2 ≥16, E3 ≥32, E4 ≥128, E5 ≥256
- E1 stays floor-free; no category percentages, no capability-mix splits — just count

### v5.1.0 (2026-04-26)
- **Per-step durability via `CheckpointPerISC` hook** — PostToolUse on ISA edits, auto-commits a git checkpoint per ISC transition with `--no-verify --no-gpg-sign`
- Sidecar idempotency state, allowlist for opt-in repos
- Inspection + preview-only rollback via `Checkpoint.ts {list|show|rollback}`

### v5.0.0 (2026-04-26)
- **BPE compaction** — Bitter Pill Engineering applied to the Algorithm itself; prescriptive scaffolding (ISC count floors per tier, min-capability counts, category percentage caps and minimums) removed
- Replaced with two operational rules: **ISC granularity** (split until each criterion is one binary tool probe) and **capability binding-commitment** (named = invoked, no minimum count)
- Tier time budgets remain the only quantitative anchor; all doctrine preserved verbatim

### v4.1.0 (2026-04-23)
- **Vocabulary release: PRD → ISA (Ideal State Artifact)** — no doctrine changes
- ISA pronounces as a single English word ("EYE-suh"); PRD forced letter-by-letter robot speech in voice-rendered work
- ISA + ISC pair as a single compositional story; "Artifact" implies tangible verifiable output (engineering noun)
- Filename change with alias period: new sessions write `MEMORY/WORK/{slug}/ISA.md`; hooks read both `ISA.md` and `PRD.md` for one minor version

### v4.0.1 (2026-04-22)
- **`[A]` category parser fix** — `prd-utils.ts` was silently dropping the v3.30 Antecedent ISC category at parse time
- **Reflection JSONL fields** — `prd_level_audit` and `hva` counts now captured per run for measurable doctrine effectiveness
- Patch release on top of v4.0.0; no doctrine changes

### v4.0.0 (2026-04-25)
- **Frame-shift release: the PRD itself is the hard-to-vary explanation** — Deutschian doctrine elevated from per-ISC to PRD-level
- **PRD-Level Hard-to-Vary Audit (PLA)** — new mandatory THINK-phase block testing Coverage / Tightness / Uniqueness *before* per-ISC HVA
- **Doctrine preamble at the top of the file** — Current → Ideal State, opacity → transparency, euphoric surprise as the same phenomenon as hard-to-variability viewed from inside vs outside
- **7/7 SUMMARY gains a `PRD:` field** — surfaces PLA outcome (`tight | gap | over | under`) alongside per-ISC counts

### v3.30.0 (2026-04-25)
- **Doctrine grounding release** — ISC explicitly grounded as hard-to-vary explanations of "done" (David Deutsch)
- **R1 Hard-to-Vary ISC Quality Gate** — sixth ISC gate, applies the variation test
- **R3 `[A]` Antecedent category** — sixth ISC tag, encodes preconditions for experiential goals
- **R4 Hard-to-Vary Audit (HVA)** — mandatory THINK-phase per-ISC audit at E2+
- **R5 Euphoric Surprise Prediction** — replaces SATISFACTION PREDICTION; forces articulation of the insight at the center of the deliverable
- **R8 Fluff Sweep in VERIFY** — re-applies the variation test to passed ISCs to catch silent relaxation

### v3.29.0 (2026-04-22)
- **Missed-ask doctrine release** — closes the 82% of low-rated sessions clustering into "you missed what I asked"
- **RR1 Re-Read Check** — primary agent re-reads the user's last message at end of VERIFY, lists each ask against shipped work, blocks `phase: complete` on any miss
- **RR2 Deliverable Manifest tier-extension** — required at any effort tier when 2+ explicit sub-tasks exist (was Extended+ only)
- **RR3 SYNTHESIS auto-load at SessionStart** — weekly complaint-cluster patterns surface into dynamic context

### v3.28.0 (2026-04-21)
- **Proportional-weight tuning** — Effort Levels rebalanced for dramatic speed range across tiers
- E1 target now <90s (was <2min), E2 <3min (was <8min), E3 <10min (was <16min); E4/E5 unchanged
- Reflection JSONL write narrowed to E2+; Satisfaction Prediction optional at E1

### v3.27.0 (2026-04-19)
- **Rule 2a Cross-Vendor Audit (Cato, E4/E5 only)** — auditor running GPT-5.4 via `codex exec` reviews the same artifacts the Anthropic-family Advisor reviewed, surfaces correlated blind spots
- Calibrated against Self-MoA research: catch-rate target 30%, deprecate empirically if not earned

### v3.26.0 (2026-04-17)
- **Doctrine tightening** driven by reflection-mining of 871 algorithm-reflections entries
- **T1 Deliverable Manifest gate** — PLAN-phase enumerated sub-task list; closes "said X Y Z, shipped X"
- **T2 Inline Verification mandate** — no ISC may flip to `[x]` in the same tool block as the work without a verification call
- **T3 Reproduce-First blocking gate** — `🔁 REPRODUCED:` line required before any Read/Grep on suspect code path

### v3.25.0 (2026-04-15)
- **Capabilities expansion** — SystemsThinking and RootCauseAnalysis added to the capability lattice for structural-cause and incident investigation work

### v3.24.0 (2026-04-13)
- **Hardening release** on top of v3.23 — five RedTeam-identified escape hatches closed
- Hard cap of 2 advisor re-calls per conflict; measured-duration short-task check; `[DEFERRED-VERIFY]` ISC status; durable-deliverable concrete binding; `synthesizeAdvisorState()` for state-gaming mitigation

### v3.23.0 (2026-04-11)
- **Verification Doctrine** — three rules: Live-Probe (mandatory tool-evidence in VERIFY), Commitment-Boundary Advisor (`advisor()` second opinion before durable deliverables), Conflict-Surfacing
- **PLAN-phase Feedback Memory Consult** and **Parallelism Opportunity Scan** added

### v3.10.0 – v3.21.0 (2026-03 to early April)
- Intent Echo at OBSERVE line 1; Reverse Engineering block formalized
- Preflight Gates (Diagnostic / Deploy / External Service / Research)
- Custom Agents vs Agent Teams routing rules
- Fast-path mode for verbatim/research-only Standard tasks
- Mode detection externalized to `mode-detection.md`; capabilities externalized to `capabilities.md`

### v3.0.0 – v3.9.0 (2026-02 to 2026-03)
- **Seven-phase doctrine made canonical** — OBSERVE, THINK, PLAN, BUILD, EXECUTE, VERIFY, LEARN as discrete phases with mandatory headers and voice transitions
- **PRD as system of record** — `~/.claude/LIFEOS/MEMORY/WORK/{slug}/ISA.md` is the single source of truth; hooks read, AI writes
- **ISC category system** — `[F]` Functional, `[S]` Structural, `[B]` Behavioral, `[N]` Negative, `[E]` Edge with proportional caps
- **Splitting Test** — every criterion checked against And/With, independent failure, scope words, domain boundary
- **Effort Levels** — E1 Standard / E2 Extended / E3 Advanced / E4 Deep / E5 Comprehensive with ISC floors and capability minimums
- Voice announcements via inline curl with session_id and phase fields for dual-source phase tracking

### v2.1.1 (2026-02 to 2026-03)
- **Capability Discovery** — explicit selection process from a CAPABILITIES list; mandatory skill trigger scan at every effort level
- **Constitutional Principles** consolidated; ISC-before-work, phases-are-discrete, PRDs-auto-sync, voice-curls-at-every-phase

### v1.6.0 (2026-02-16)
- **Verify Completion Gate** added at end of VERIFY phase

### v1.3.0 – v1.5.0 (2026-02-15)
- **Zero-Delay Output** mandate — `♻️` header and `🗒️ TASK` line as first output tokens
- **Self-Interrogation** in OBSERVE — five questions about gaps, prohibitions, and constraints (scaled by effort)
- **Context Recovery** step — narrow window to recover prior-session work referenced by the user
- ISC Scale Tiers table aligned with Structure rules (v1.4.0 fix)

### v0.5.8 – v0.5.9 (2026-02-13)
- Iteration on visible algorithm progression format and inline verification methods

### v0.5.3 (2026-02-12)
- **PRD Integration** — Every Algorithm run creates or continues a PRD (Product Requirements Document) on disk as persistent memory
- **Dual-Tracking** — ISC lives in both working memory (TaskCreate) and persistent memory (PRD file) with sync rules
- **ISC Quality Gate** — 6-check gate (count, word count, state-not-action, binary testable, anti-criteria, coverage) blocks THINK until passed
- **Effort Level System** — 8 tiers (Instant→Loop) replacing TIME SLA, with phase budget guides and auto-compress at 150% overage
- **Plan Mode Integration** — Structured ISC construction workshop at PLAN phase for Extended+ effort levels
- **Inline Verification Methods** — Each criterion carries `| Verify: CLI|Test|Static|Browser|Grep|Read|Custom` suffix
- **Confidence Tags** — `[E]`xplicit, `[I]`nferred, `[R]`everse-engineered on each criterion for THINK phase pressure testing
- **ISC Scale Tiers** — Simple (4-8), Medium (12-40), Large (40-150), Massive (150-500+) with structure rules
- **Capability Registry** — 25 capabilities across 6 sections (Foundation, Thinking, Agents, Collaboration, Execution, Verification)
- **Full Scan Mandate** — Every task evaluates all 25 capabilities; format scales by effort level (one-line → compact → full matrix)
- **No Silent Stalls** — Critical execution principle: no chained infrastructure, no sleep, 5s timeouts, background for long ops
- **Discrete Phase Enforcement** — BUILD and EXECUTE are always separate phases, never merged
- **Loop Mode Effort Decay** — Late iterations auto-drop effort level as criteria converge (Extended→Standard→Fast)
- **Agent Teams / Swarm** — Multi-agent coordination with shared task lists and child PRD decomposition
- **PRD Status Progression** — DRAFT→CRITERIA_DEFINED→PLANNED→IN_PROGRESS→VERIFYING→COMPLETE/FAILED/BLOCKED
- **Voice Phase Announcements** — Effort-level-gated voice curls (none for Instant/Fast, entry+verify for Standard, all for Extended+)

### v0.3.4 (2026-02-03)
- **CAPABILITY AUDIT block** — Mandatory in OBSERVE phase, shows CONSIDERED vs SELECTED capabilities
- **TIME SLA system** — Instant/Fast/Standard/Deep determines agent budget
- **Reverse Engineering expansion** — Explicit/implied wants AND don't-wants, plus gotchas
- **Agent Instructions** — CRITICAL requirement for context, SLA, and output format when spawning agents
- **Algorithm Concept section** — Full 9-point philosophy explaining why ISC matters
- **Voice Phase Announcements** — Progress visibility during long operations

### v0.2.34 (2026-02-02)
- **Builder-Validator Pair Pattern** -- New `Pair` composition pattern: every work unit gets a Builder agent and an independent Validator agent
- **Agent Self-Validation** -- Agents receive validation contracts (mechanical checks) and verify their own output before reporting completion
- **ISC Dependency Graph** -- ISC criteria declare dependencies via `addBlockedBy`/`addBlocks` for wave-based parallel execution

### v0.2.33 (2026-02-02)
- **Continuous Recommendation** -- Replaces Two-Pass Selection; CapabilityRecommender is re-invocable at any phase boundary with enriched context
- **Dynamic Ecosystem Discovery** -- Hook reads Agents/ directory and skill-index.json at runtime instead of hardcoded lists
- **Holistic Capability Matrix** -- Hook output is a coherent strategy (strategy, agents, skills, timing, pattern, sequence, quality, constraints)

### v0.2.32 (2026-02-02)
- **Structured Evidence Requirements** -- ISC verification requires evidence type, source, and content (no more "verified" without proof)
- **Retry Loop** -- DIAGNOSE -> CHANGE -> RE-EXECUTE loop (max 3 iterations) when VERIFY fails; change is mandatory
- **Ownership Check** -- VERIFY begins with approach reflection: what I did, alternatives, and whether I'd choose the same again

### v0.2.31 (2026-02-02)
- **Structural Agent Enforcement** -- New AgentExecutionGuard hook (PreToolUse on Task) warns on foreground agent spawns
- **Three-Layer Architecture** -- Detection (CapabilityRecommender) -> Enforcement (AgentExecutionGuard) -> Capture (AgentOutputCapture)
- **Enforce Structurally, Not Instructionally** -- Philosophy principle #10; hooks fire regardless of context pressure

### v0.2.30 (2026-02-02)
- **Mandatory Background Agents** -- All Task calls must use run_in_background: true with polling; foreground agents banned
- **Non-Blocking Voice** -- Voice curl commands use `&` suffix for fire-and-forget execution
- **Agent Progress Reporting** -- Poll and report agent status every 15-30 seconds

### v0.2.29 (2026-02-01)
- **Timing-Aware Execution** -- New timing tiers (fast/standard/deep) flow from hook through agents; model selection follows timing
- **Agent Prompt Scoping** -- Every agent prompt MUST include `## Scope` with validated timing tier
- **Model Selection Interaction** -- fast->haiku, standard->sonnet, deep->opus (preference, not hard rule)

### v0.2.28 (2026-02-01)
- **Git Worktrees** -- Parallel solution attempts in isolated worktrees when multiple approaches exist for the same problem
- **Tournament Pattern** -- New composition pattern: `[A, B, C] -> Evaluate -> Winner` for competing solutions
- **Compete, Don't Guess** -- Philosophy principle #8; try all viable approaches and pick the winner

### v0.2.27 (2026-01-31)
- **Never-Block Rule** -- Operations > 10s MUST run as background agents with progress reporting
- **TIME TRIAGE** -- Mandatory PLAN phase section: estimate duration, choose execution mode, set update intervals
- **Quick Answer First** -- For verification tasks, report result immediately, then offer to investigate

### v0.2.26 (2026-01-31)
- **Voice Line Constraint** -- The spoken summary at the end of every response must be 8-24 words
- **Internal phases unconstrained** -- OBSERVE through LEARN remain as detailed as needed; only the voice line is constrained

### v0.2.25 (2026-01-30)
- **Parallel-by-Default Execution** -- Independent tasks MUST run concurrently; serial execution only for data dependencies
- **Fan-out Default** -- 3+ independent workstreams automatically use the Fan-out pattern

### v0.2.24 (2026-01-29)
- **Mandatory Structured Questions** -- All questions to the user must use a structured question tool with options, not inline text
- **Interaction Contract** -- Ensures consistent UX, trackable answers, and explicit question handling

### v0.2.23 (2026-01-28)
- **Two-Pass Capability Selection** -- Hook provides draft hints (Pass 1), THINK validates against ISC (Pass 2)
- **Thinking Tools Assessment** -- Six thinking tools evaluated with justify-exclusion principle for every FULL request
- **Skill Check in THINK** -- Hook skill hints validated against ISC criteria

### v0.2.22 (2026-01-28)
- **Nothing Escapes the Algorithm** -- Reframed modes as depth levels, not whether the Algorithm runs
- **Capability Selection Block** -- First-class element in THINK phase with justification and composition patterns
- **7 Composition Patterns** -- Pipeline, TDD Loop, Fan-out, Fan-in, Gate, Escalation, Specialist
- **Execution Tiers** -- Conceptual framework for recursive sub-algorithm execution (Tiers 0-3)
- **AI-Powered Depth Detection** -- Inference-based depth classification over keyword matching

### v0.1 (2026-01-24)
- Initial release
- Seven-phase execution
- ISC criteria system
- LifeOS integration

---

## 🤝 Contributing

I'm actively experimenting with this, so feedback is welcome:
- **Issues**: Suggest improvements or point out problems
- **Discussions**: Question the approach or share ideas
- **PRs**: Fix typos, improve examples, add clarity

If you want to propose major changes, open an issue first so we can discuss.

---

## 🔗 Related Projects

- **[LifeOS](https://github.com/danielmiessler/LifeOS)** - Where I'm using this
- **[Fabric](https://github.com/danielmiessler/fabric)** - Related pattern system

---

## 📄 License

MIT License - See [LICENSE](LICENSE) file

---

## 👤 Author

**Daniel Miessler**
- Website: [danielmiessler.com](https://danielmiessler.com)
- Twitter: [@danielmiessler](https://twitter.com/danielmiessler)
- YouTube: [@unsupervised-learning](https://youtube.com/@unsupervised-learning)

---

<div align="center">

  **"I think the key is capturing and maintaining what IDEAL STATE actually means as you learn more."**

  ⭐ Star this if you find the idea interesting!

</div>
