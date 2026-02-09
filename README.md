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
- `/context-curator` - Domain-agnostic extraction and maintenance
- `/audit` - ISO 19011 systematic audits
- `/standards-sync` - Sync with external best practices
- `/compare` - Weighted decision matrices
- `/diagram` - Mermaid diagram generation
- `/systematic-review` - PRISMA 2020 compliant research synthesis

**[Get Started with Plugin →](./plugins/context-system/README.md)**

---

## What's New in v0.0.2

**Release Date**: February 2026

### Quality Enhancements ✨
- ✅ **Troubleshooting sections** added to all 7 skills (100% coverage)
- ✅ **Known limitations** documented for every skill (realistic expectations)
- ✅ **Formatting standardization** (wikilinks without bold wrapping)
- ✅ **Quick Start sections** for all complex workflows

### Progressive Disclosure Refinement 📐
- ✅ **Optimal reference file counts** achieved (3-8 per skill)
- ✅ **compare** extracted to 172 lines + 4 references (was 387 lines, 0 refs)
- ✅ **standards-sync** extracted to 253 lines + 4 references (was 389 lines, 0 refs)
- ✅ **context-curator** slimmed to 231 lines + 8 references (was 474 lines, 5 refs)
- ✅ **audit** streamlined to 316 lines + 7 references (was 430 lines, 2 refs)
- ✅ All skills now 200-350 line SKILL.md target (Approach B - Moderate Progressive Disclosure)

### Best Practices Integration 🎯
- ✅ Applied comprehensive Q1 2026 skills audit findings
- ✅ Integrated [Anthropic](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices), [LangChain](https://www.langchain.com/state-of-agent-engineering), and production AI research
- ✅ Followed weighted decision matrix (Approach B: Moderate Progressive Disclosure wins 8.6/10)
- ✅ 100% compliance with external best practices

---

## Design Principles

### Progressive Disclosure
Skills load **overview first, details on-demand**. You see what you need when you need it - not everything at once.

- Main SKILL.md: Quick Start + workflow summaries (200-350 lines)
- Reference files: Detailed guides loaded only when relevant (3-8 per skill)
- **Benefit**: Faster navigation, less cognitive load, efficient context usage

### Production-Ready Quality
Every skill includes:
- **Troubleshooting sections** - What to do when things fail
- **Known limitations** - What the skill can't do (and workarounds)
- **Quick Start guides** - Get started without reading everything
- **Real examples** - See patterns in action

### Evidence-Based Standards
Built on best practices from leading sources:
- **[Anthropic Skill Best Practices](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices)** - Progressive disclosure, context efficiency
- **[LangChain State of AI Engineering 2026](https://www.langchain.com/state-of-agent-engineering)** - Production patterns, observability
- **[Production AI Systems Research](https://medium.com/generative-ai-revolution-ai-native-transformation/the-first-production-ai-agents-study-reveals-why-agentic-engineering-becomes-mandatory-in-2026-ec5e00514e5e)** - 306 practitioners, 20 case studies
- **[ISO 19011:2018](https://www.iso.org/standard/70017.html)** - Audit framework (systematic quality assessment)
- **[PRISMA 2020](https://www.prisma-statement.org/)** - Research synthesis standards

Not theoretical - these patterns work in production.

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
│       │   ├── context-curator/
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
