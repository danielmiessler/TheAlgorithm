<div align="center">
  <img src="assets/logo.png" alt="TheAlgorithm" width="200">

  # TheAlgorithm

  **A General Problem-Solving Framework for Achieving Euphoric Surprise**

  [![Version](https://img.shields.io/badge/version-0.1-blue.svg)](https://github.com/danielmiessler/TheAlgorithm/releases)
  [![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
  [![PAI](https://img.shields.io/badge/PAI-integrated-purple.svg)](https://github.com/danielmiessler/PAI)
  [![Status](https://img.shields.io/badge/status-active-success.svg)]()

  [Philosophy](#philosophy) • [How It Works](#how-it-works) • [PAI Integration](#pai-integration) • [Versioning](#versioning) • [Documentation](#documentation)
</div>

---

## 🎯 Overview

TheAlgorithm is a general problem-solving framework designed to systematically transition from **current state** to **ideal state** through verifiable, granular criteria. It serves as the methodological foundation for the [PAI (Personal AI Infrastructure)](https://github.com/danielmiessler/PAI) system.

**The Goal:** Produce "Euphoric Surprise" from every response.

**The Method:** Hill-climbing toward Ideal State through testable criteria.

---

## 💡 Philosophy

### The Core Insight

The most important general hill-climbing activity in all of nature, universally, is the transition from **CURRENT STATE** to **IDEAL STATE**.

This simple truth has profound implications:

1. **Verifiable Progress Requires Granular State**
   Anything you want to iteratively improve must have state that's verifiable at a granular level.

2. **Criteria Must Be Testable**
   You cannot hill-climb without discrete, granular, binary, and testable criteria.

3. **Ideal State Is The North Star**
   You cannot build those criteria without perfect understanding of what the IDEAL STATE looks like.

4. **Dynamic Maintenance Is Critical**
   The capture and dynamic maintenance of IDEAL STATE is the single most important activity in the process of hill climbing towards Euphoric Surprise.

<div align="center">
  <img src="assets/algorithm-phases.png" alt="The Seven-Phase Algorithm" width="900">
  <p><em>The seven-phase execution flow: OBSERVE → THINK → PLAN → BUILD → EXECUTE → VERIFY → LEARN</em></p>
</div>

---

## ⚙️ How It Works

TheAlgorithm operationalizes these principles through:

### 1. **Ideal State Criteria (ISC)**
Discrete, granular, binary, testable criteria that define success
- **Exactly 8 words** - Forces precision
- **Granular** - Atomic, single-concern
- **Discrete** - Clear boundaries, not overlapping
- **Testable** - Binary YES/NO in <2 seconds
- **State-based** - Describes what IS true, not what to DO

### 2. **Seven-Phase Execution**
A scientific-method-inspired inner loop:

```
OBSERVE  → Gather current state, context, and user intent
THINK    → Analyze underlying meaning and ideal outcome
PLAN     → Build ISC criteria and select capabilities
BUILD    → Construct solution components
EXECUTE  → Take actions toward criteria
VERIFY   → Confirm all criteria with evidence
LEARN    → Capture insights and next steps
```

### 3. **Euphoric Surprise**
The standard for every output. Not "good enough" - **surprising delight**.

---

## 🔗 PAI Integration

TheAlgorithm powers PAI's response system. Every PAI interaction follows the algorithm's structure.

### Configuration

PAI can consume TheAlgorithm in three ways:

**1. Always Latest (Default)**
```json
{
  "algorithmSource": "latest"
}
```
Fetches from: `TheAlgorithm.md` (main branch)

**2. Pin to Specific Version**
```json
{
  "algorithmSource": "v0.1"
}
```
Fetches from: `versions/v0.1.md` (immutable)

**3. Use Custom Local Version**
```json
{
  "algorithmSource": "local",
  "algorithmLocalPath": "/path/to/custom-algorithm.md"
}
```
Uses your modified version for testing

### Integration Pattern

PAI's build system fetches TheAlgorithm at build time:

```typescript
// PAI BuildSkill.ts
const algorithm = await fetchAlgorithm({
  version: config.algorithmSource,
  cacheDir: "~/.claude/cache/algorithm",
  localOverride: process.env.ALGORITHM_LOCAL_OVERRIDE
});
```

**Caching Strategy:**
- Specific versions (v0.1, v0.2): Cached permanently
- Latest: TTL-based refresh on builds
- Fallback: Bundled version if fetch fails

### URL Patterns

```bash
# Latest version
https://raw.githubusercontent.com/danielmiessler/TheAlgorithm/main/TheAlgorithm.md

# Specific version (immutable)
https://raw.githubusercontent.com/danielmiessler/TheAlgorithm/main/versions/v0.1.md

# Git tag (alternative)
https://raw.githubusercontent.com/danielmiessler/TheAlgorithm/v0.1/TheAlgorithm.md
```

---

## 📦 Versioning

TheAlgorithm uses a hybrid versioning strategy optimized for both PAI automation and human browsing:

### Repository Structure

```
TheAlgorithm/
  TheAlgorithm.md           # Always points to latest
  versions/
    v0.1.md                 # Frozen snapshot
    v0.2.md                 # Frozen snapshot
  CHANGELOG.md              # Version history
  README.md                 # This file
```

### Version Strategy

- **Semantic Versioning**: `MAJOR.MINOR.PATCH`
  - **MAJOR**: Breaking changes to ISC format or core concepts
  - **MINOR**: New features (sections, optional fields) - backward compatible
  - **PATCH**: Typos, clarifications, examples - no structural changes

- **Git Tags**: All releases also tagged (`v0.1`, `v0.2`)
- **GitHub Releases**: Formal releases with changelogs

### When to Upgrade

| Your PAI Config | When to Change |
|-----------------|----------------|
| `"latest"` | Automatic - always uses current |
| `"v0.1"` | Manual - change when you want to upgrade |
| `"local"` | Never - you control the file |

**Breaking Changes:** Major version bumps (v0.x → v1.0) require reviewing your PAI configuration.

---

## 📚 Documentation

### Complete Specification

See **[TheAlgorithm.md](./TheAlgorithm.md)** for:
- Full execution format (all 7 phases)
- ISC criteria requirements and examples
- Progressive output requirements
- Common failure modes and fixes
- Complete capabilities matrix
- Anti-patterns to avoid

### Quick Start

1. **Read the philosophy** (above) to understand the "why"
2. **Review the specification** ([TheAlgorithm.md](./TheAlgorithm.md)) for the "how"
3. **See it in action** in [PAI](https://github.com/danielmiessler/PAI)
4. **Customize if needed** by forking and using local configuration

---

## 🎓 Key Concepts

### ISC (Ideal State Criteria)

The core innovation. Instead of vague goals like "make it better," ISC forces precision:

**Bad:** "Fix the authentication bug"
**Good:** "All authentication tests pass after fix applied" (8 words, testable)

**Bad:** "Improve the UI"
**Good:** "Login button centered on screen with correct spacing" (8 words, verifiable)

### Anti-Criteria

What must NOT happen. Equally important as positive criteria:

**Example Anti-Criteria:**
- "No credentials exposed in git commit history"
- "No breaking changes to existing public API endpoints"
- "Database migrations do not lose any user data"

### Euphoric Surprise

The audacious standard. Not:
- ✗ "Good enough"
- ✗ "Met requirements"
- ✗ "No complaints"

But:
- ✓ "Wow, I didn't expect that!"
- ✓ "This is exactly what I needed and more"
- ✓ "How did it know to do that?"

---

## 🔄 Version History

### v0.1 (2026-01-24)
- Initial release
- Seven-phase execution format
- ISC criteria system
- Progressive output requirements
- Capabilities matrix
- PAI integration patterns

---

## 🌟 Principles in Action

### 1. Single Source of Truth
`TheAlgorithm.md` is always current. Historical versions archived in `versions/`.

### 2. Immutable Versions
Once `v0.1.md` is published, it never changes. This enables permanent URLs and reliable caching.

### 3. Progressive Enhancement
Start with "latest", pin to specific version when stability matters more than features.

### 4. Local Override
Developers can test algorithm changes locally before publishing.

### 5. Graceful Degradation
PAI falls back to bundled version if network fetch fails.

---

## 🤝 Contributing

TheAlgorithm evolves through:
- **Issues**: Propose clarifications or improvements
- **Discussions**: Philosophical questions about the approach
- **Pull Requests**: Typos, examples, documentation improvements

**Major Changes:** Open an issue first to discuss before investing effort.

---

## 🔗 Related Projects

- **[PAI](https://github.com/danielmiessler/PAI)** - Personal AI Infrastructure (primary implementation)
- **[Fabric](https://github.com/danielmiessler/fabric)** - AI pattern system

---

## 📄 License

MIT License - See [LICENSE](LICENSE) file for details

---

## 👤 Author

**Daniel Miessler**
- Website: [danielmiessler.com](https://danielmiessler.com)
- Twitter: [@danielmiessler](https://twitter.com/danielmiessler)
- YouTube: [@unsupervised-learning](https://youtube.com/@unsupervised-learning)

---

<div align="center">

  **"The capture and dynamic maintenance of IDEAL STATE is the single most important activity in the process of hill climbing towards Euphoric Surprise."**

  ⭐ Star this repo if TheAlgorithm helps you achieve better outcomes!

</div>
