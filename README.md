<div align="center">
  <img src="assets/algorithm-blocks.png" alt="TheAlgorithm" width="600">

  # TheAlgorithm

  **An experiment in systematic problem-solving**

  [![Version](https://img.shields.io/badge/version-0.3.4-blue.svg)](https://github.com/danielmiessler/TheAlgorithm/releases)
  [![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
  [![PAI](https://img.shields.io/badge/PAI-integrated-purple.svg)](https://github.com/danielmiessler/PAI)
  [![Status](https://img.shields.io/badge/status-experimental-orange.svg)]()

  [The Idea](#the-idea) • [How It Works](#how-it-works) • [PAI Integration](#pai-integration) • [Versioning](#versioning) • [Documentation](#documentation)
</div>

---

## 🎯 The Idea

I've been working on a general problem-solving framework that I'm calling TheAlgorithm. The core idea is pretty simple: systematically move from **current state** to **ideal state** through verifiable criteria.

I'm using it as the foundation for my [PAI (Personal AI Infrastructure)](https://github.com/danielmiessler/PAI) system, and early results are promising.

**The goal:** Every response should surprise and delight ("Euphoric Surprise")

**The method:** Hill-climb toward the ideal state using testable criteria

This is v0.1 - my first real attempt at codifying this. I'm sure it'll evolve significantly as I learn what works and what doesn't.

---

## 💡 The Core Insight

I think the most important thing in any iterative improvement process is the transition from **CURRENT STATE** to **IDEAL STATE**.

This seems obvious, but I don't think most systems actually operationalize it well. Here's what I'm exploring:

1. **You need granular, verifiable state**
   If you can't measure where you are, you can't tell if you're making progress.

2. **Criteria need to be testable**
   Vague goals like "make it better" don't work. You need discrete, binary tests.

3. **Ideal state is your north star**
   You can't build good criteria without understanding what "done" looks like.

4. **The ideal state changes**
   As you learn more, your understanding of "ideal" evolves. The system needs to capture that.

<div align="center">
  <img src="assets/algorithm-foundational.png" alt="Algorithm Foundational Concepts" width="900">
  <p><em>The pieces I'm working with</em></p>
</div>

---

## ⚙️ How It Works

I'm testing three main components:

### 1. **Ideal State Criteria (ISC)**
Specific, testable statements about what success looks like:
- **Exactly 8 words** - Keeps them focused
- **Granular** - One thing per criterion
- **Discrete** - Clear boundaries
- **Testable** - Binary YES/NO you can check quickly
- **State-based** - What IS true, not what to DO

### 2. **Seven-Phase Execution**
A loop inspired by the scientific method:

```
OBSERVE  → What's the current state and what was requested?
THINK    → What's the underlying intent and ideal outcome?
PLAN     → What criteria define success?
BUILD    → Create the solution components
EXECUTE  → Take actions toward the criteria
VERIFY   → Confirm each criterion with evidence
LEARN    → Capture insights for next time
```

### 3. **Euphoric Surprise**
I'm shooting for responses that make you go "wow, I didn't expect that!" instead of just "yeah, that works."

Is this realistic? Not sure yet. But setting a high bar seems better than settling for "good enough."

---

## 🔗 PAI Integration

I'm using this in PAI - every interaction follows the algorithm structure. It's working well so far, but I'm still experimenting.

### Configuration

PAI can load TheAlgorithm three ways:

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

### How PAI Uses It

```typescript
// PAI fetches at build time
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
3. Look at [PAI](https://github.com/danielmiessler/PAI) to see it in action
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
- PAI integration

---

## 🤝 Contributing

I'm actively experimenting with this, so feedback is welcome:
- **Issues**: Suggest improvements or point out problems
- **Discussions**: Question the approach or share ideas
- **PRs**: Fix typos, improve examples, add clarity

If you want to propose major changes, open an issue first so we can discuss.

---

## 🔗 Related Projects

- **[PAI](https://github.com/danielmiessler/PAI)** - Where I'm using this
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
