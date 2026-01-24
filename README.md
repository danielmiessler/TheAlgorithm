<div align="center">
  <img src="assets/algorithm-blocks.png" alt="TheAlgorithm" width="600">

  # TheAlgorithm

  **An experiment in systematic problem-solving**

  [![Version](https://img.shields.io/badge/version-0.1-blue.svg)](https://github.com/danielmiessler/TheAlgorithm/releases)
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
