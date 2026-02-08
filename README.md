# Context System for Claude Code

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**A production-validated approach to persistent context management for AI-assisted development.**

Make Claude remember your preferences, conventions, and decisions across conversations—without repeating yourself.

---

## The Problem

Every conversation with Claude starts fresh. You repeatedly explain:
- "I prefer review-first workflow"
- "Use wikilinks, not markdown links"
- "Always run tests before committing"

**Claude forgets between sessions.** The first 10 minutes of every conversation is context setup.

---

## The Solution

This repository provides a **marketplace plugin** with 7 production-ready skills:

### 🚀 **Context Management Plugin**
Pre-built skills to bootstrap your context system:
- `/init-context-system` - Discovery-driven setup wizard
- `/context-update` - Domain-agnostic extraction and maintenance
- `/audit` - ISO 19011 systematic audits
- `/standards-sync` - Sync with external best practices
- `/compare` - Weighted decision matrices
- `/diagram` - Mermaid diagram generation
- `/systematic-review` - PRISMA 2020 compliant research synthesis

**[Get Started with Plugin →](./plugins/context-system/README.md)**

---

## Key Patterns Demonstrated

### 1. **Concept-Based Organization**
Organize context by **topic** (skills, security, python), not **type** (preferences, standards, workflows).

**Authority**: [Anthropic Skill Best Practices](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices) - "Purpose-based organization, max 2 levels"

**Why it works**: LLMs can instantly find relevant context. "Where's security content?" → `context/security/`

### 2. **ISO 19011 Audit Framework**
Systematic, evidence-based audits with:
- Risk-based prioritization
- Automated + manual checks
- Trend tracking
- Standards feedback loop

**Authority**: [ISO 19011:2018](https://www.iso.org/standard/70017.html) - "Guidelines for auditing management systems"

**Why it works**: Reproducible quality improvement with evidence-based assessment and trend tracking.

### 3. **Standards Synchronization**
Continuous cycle: Monitor external standards → Evaluate → Update internal → Migrate implementations → Measure

**Why it works**: Prevents standards drift. Stays aligned with OWASP, PRISMA, ISO, Anthropic best practices.

### 4. **Meta-Skills**
Skills that orchestrate other skills:
- `/audit` - Audits other skills (inception!)
- `/standards-sync` - Syncs external standards automatically

**Why it works**: Patterns become executable, not just documentation.

---

## What's Included

```
context-system/
├── plugins/                        # Marketplace plugin
│   └── context-system/
│       ├── skills/                # 7 production skills
│       │   ├── init-context-system/
│       │   ├── context-update/
│       │   ├── audit/
│       │   ├── standards-sync/
│       │   ├── compare/
│       │   ├── diagram/
│       │   └── systematic-review/
│       ├── templates/             # Reusable templates
│       ├── examples/              # Real-world examples
│       └── README.md              # Installation guide
│
└── docs/                          # Pattern documentation
    ├── getting-started.md         # Quick start guide
    └── standards-sources.md       # Standards mapping
```

---

## Installation

**Step 1:** Add the marketplace in Claude Code:
```
/plugin marketplace add bcbeidel/context-system
```

**Step 2:** Install the plugin:
```
/plugin
```
Navigate to **Discover** tab → Install "context-system"

**Step 3:** Run setup:
```
/init-context-system
```

**Done!** Follow the guided 3-phase setup.

---

## Core Principles

> **📖 All patterns grounded in external authorities**: [Anthropic Best Practices](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices), [ISO 19011](https://www.iso.org/standard/70017.html), [OWASP Top 10](https://owasp.org/www-project-top-ten/), [PRISMA 2020](http://www.prisma-statement.org/)
>
> **See**: [Standards & Sources Documentation](./docs/standards-sources.md) for complete mapping

### 1. **Explicit Over Implicit**
Capture preferences explicitly. Don't hope Claude "remembers" or infers them.

### 2. **Context as Code**
Treat context like code: version controlled, refactorable, with clear governance.

### 3. **Progressive Enhancement**
Start small. Add context when you notice repeated corrections. No need to document everything upfront.

### 4. **Grounded in Standards**
All patterns anchored to external authorities with verification URLs. When standards evolve, we adapt via `/standards-sync`.

### 5. **Evidence-Based Approach**
Use systematic audits (`/audit`) to validate context quality and track improvements over time.

---

## Documentation

- **[Getting Started Guide](./docs/getting-started.md)** - Plugin installation and first steps
- **[Standards & Sources](./docs/standards-sources.md)** - Mapping to external authorities
- **[Plugin README](./plugins/context-system/README.md)** - Detailed skill documentation
- **[Skill Reference](./plugins/context-system/skills/README.md)** - All 7 skills explained

---

## Use Cases

### ✅ **You Should Use This If**:
- You're tired of re-explaining preferences to Claude every session
- You want reproducible quality in your AI workflows
- You're building a team knowledge base for Claude
- You want to learn advanced Claude Code patterns

### ⚠️ **This May Not Be For You If**:
- You rarely use Claude Code
- You prefer starting fresh each conversation
- You want a turnkey solution (this requires adaptation)

---

## Contributing

This is a reference implementation, not a framework. Contributions welcome for:
- ✅ Bug fixes in plugin skills
- ✅ Documentation improvements
- ✅ Additional pattern examples
- ✅ Case studies from your adaptations

See [CONTRIBUTING.md](./plugins/context-system/CONTRIBUTING.md)

---

## License

MIT License - see [LICENSE](./LICENSE)

**On Personal Content**: The patterns and architecture are freely shareable. Adapt as needed for your context.

---

## Questions?

- **"How do I get started?"** → Use the [marketplace plugin](./plugins/context-system/README.md)
- **"Can I use this with other AI tools?"** → Principles apply, but implementation is Claude Code-specific
- **"How much context is too much?"** → Start small. Add only when you notice repeated corrections
- **"What if I don't want to use all the patterns?"** → Pick what's relevant. Progressive adoption is fine

---

**Built by**: Brandon Beidel
**Powered by**: Claude Sonnet 4.5 via Claude Code
**Last Updated**: February 2026
