# Context System - Claude Code Skill

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> **Make Claude persistently remember your preferences, decisions, and workflows across conversations.**

A comprehensive [Claude Code](https://github.com/anthropics/claude-code) skill that guides you through creating a context management system—solving the problem of Claude forgetting your preferences between sessions.

---

## The Problem

Every conversation with Claude starts fresh. You repeatedly explain:
- "I prefer review-first workflow"
- "Use wikilinks, not markdown links"
- "Always run tests before committing"

**But Claude forgets between sessions.** You spend the first 10 minutes of every conversation re-establishing context.

## The Solution

This plugin provides **6 production-validated skills** for persistent context management:

### Context Management
- ✅ `/context-curator` - Bootstrap and maintain context with automated quality gates

### Research & Planning
- ✅ `/researcher` - Multi-methodology research orchestrator (7 methodologies: DSR, UX, Market, Mixed Methods, Case Study, Org Culture, Evidence Synthesis)
- ✅ `/planner` - Evidence-based planning with quality validation

### Meta-Skills (Advanced Patterns)
- ✅ `/auditor` - ISO 19011 systematic audits
- ✅ `/standards-sync` - Sync external best practices (OWASP, PRISMA, ISO)

**Result**: Claude aligns with your style from message one and improves over time.

---

## What's New in v0.0.3 (February 2026)

### New Capabilities

**🎯 /planner - Evidence-Based Planning**
- Structured planning for multi-step tasks with hierarchical decomposition
- 5-dimension quality validation (completeness, feasibility, efficiency, maintainability, adaptability)
- 3 planning strategies: decompose-first, interleaved, milestone-based
- Saves plans to `/projects/` for resumable execution

**🔬 /researcher - Multi-Methodology Research Orchestrator**
- **7 research methodologies** with intelligent selection wizard:
  - Design Science Research (technology innovation)
  - UX Research (user experience, usability)
  - Market Research (competitive analysis, sizing)
  - Mixed Methods (qualitative + quantitative)
  - Case Study (organizational deep-dives)
  - Organizational Culture (assessment, analysis)
  - Evidence Synthesis (PRISMA 2020 systematic reviews)
- Replaces single-purpose `/systematic-review` skill
- All PRISMA 2020 features preserved in evidence-synthesis methodology

**⚡ /context-curator - Enhanced Quality Gates**
- Automated index validation script (catches 100% of structural issues)
- Comprehensive Step 7: Update indexes with 5-substep validation (7.1-7.5)
- Comprehensive Step 12: Quality validation with 9-substep checks (12.1-12.9)
- Documentation synchronization guidance (README.md + CLAUDE.md)
- Two mandatory quality gates prevent incomplete curation

### Migration

**⚠️ /systematic-review → /researcher**
- **Removed in v0.0.3**
- All features migrated to `/researcher/evidence-synthesis/`
- Use `/researcher --methodology=evidence-synthesis` for systematic reviews
- Full PRISMA 2020 compliance preserved

### Impact

- **+2 new skills** (planner, researcher)
- **+1 enhanced skill** (context-curator with quality gates)
- **+7 research methodologies** (was 1, now 7)
- **100% automated validation** (prevents index drift)

---

## What's New in v0.0.2 (February 2026)

### Production-Ready Enhancements
- ✅ **Troubleshooting & Known Limitations** in every skill
- ✅ **Optimal skill sizes** (200-350 lines) with progressive disclosure
- ✅ **Reference file optimization** (3-8 refs per skill)
- ✅ **100% compliance** with Anthropic best practices

### Major Improvements
- **standards-sync**: 389 → 253 lines (+4 refs) - Streamlined external best practices sync
- **context-curator**: 474 → 231 lines (+3 refs) - Clearer extraction workflow
- **auditor**: 430 → 316 lines (+5 refs) - More actionable audit process

### Why v0.0.2 Matters

**Every skill now has**:
- **Troubleshooting** - Debug failures quickly
- **Known limitations** - Realistic expectations
- **Quick Starts** - Find what you need fast
- **Optimal size** - Easy to navigate, not overwhelming

**Result**: Professional-grade skills that are easier to use and understand.

---

## Quick Start

**1. Add the marketplace** (in Claude Code):
```
/plugin marketplace add bcbeidel/context-system
```

**2. Install the plugin:**
```
/plugin
```
Then navigate to the "Discover" tab and install "context-system"

**3. Start using it** (in any project):
```
/context-curator
```

**Done!** On first run, context-curator will offer to bootstrap the context system with best practices for using the distributed skills. Then just run `/context-curator` after work sessions to extract learnings.

---

## Installation

### Recommended: Marketplace Installation ⭐

**Step 1: Add the marketplace**

In Claude Code, run:
```
/plugin marketplace add bcbeidel/context-system
```

**Step 2: Install the plugin**

Run `/plugin` and navigate to the **Discover** tab. You'll see the `context-system` plugin. Install it.

**Step 3: Verify**

In any project directory, run:
```
/context-curator
```

On first run, you'll see the bootstrap offer. The plugin is now available globally across all your projects!

---

### Alternative: Direct Git Installation

<details>
<summary>Click to expand direct installation method</summary>

If you prefer to install directly without the marketplace:

```bash
# Clone to Claude plugins directory
git clone https://github.com/bcbeidel/context-system.git \
  ~/.claude/plugins/context-system
```

The skills will be available in all your projects immediately.

**Verify**:
```bash
# Check plugin is installed
ls ~/.claude/plugins/context-system
```

</details>

---

**That's it!** Start with `/context-curator` to bootstrap (5 min) or begin curating immediately. Claude will remember your preferences.

---

## What You Get

### First Run: Automated Bootstrap (5 min)
- **Core domains** for skill support (skills/, research/, auditing/, communication/, decisions/, processes/)
- **Best practices** pre-populated for distributed skills (auditor, researcher, planner, agent development)
- **Ready to use** immediately after bootstrap

### Ongoing: Progressive Enhancement
- **Extract learnings** from work sessions (`/context-curator` after major work)
- **Capture decisions** (ADRs) as you make architectural choices
- **Build preferences** over time (communication style, workflow patterns)
- **Evolves with you** - system gets smarter as you use it

### Result
- **Stop repeating yourself** - preferences persist across sessions
- **Consistent quality** - standards enforced automatically
- **Compound value** - early investment pays long-term dividends

---

## Key Features

- **🚀 5 Production Skills**: Research & planning, meta-skills, context management
- **🎯 Automated Bootstrap**: First-run setup in 5 minutes with best practices included
- **📊 Evidence-Based**: Extract from actual work, not hypothetical scenarios
- **🔄 Task-Based Loading**: Context automatically loads for git, code review, documentation, etc.
- **🏛️ Grounded in Standards**: ISO 19011, PRISMA 2020, OWASP best practices
- **📝 Templates & Examples**: Prevent reinventing structure
- **🧩 Adaptable**: Universal principles + customizable implementation

---

## File Structure

```
your-project/
├── .claude/
│   ├── CLAUDE.md                    # References context system
│   └── skills/
│       └── [your-custom-skills]/    # Your project-specific skills
└── context/
    ├── _index.md                    # Navigation hub
    ├── context-system/              # Meta (organizing principles, loading map)
    ├── communication/               # Core domain (always created)
    ├── decisions/                   # Core domain (always created)
    ├── python/                      # User domain (if applicable)
    ├── security/                    # User domain (if applicable)
    ├── research/                    # User domain (if applicable)
    └── [your-other-domains]/        # Based on discovery questions
```

---

## Included Skills

This plugin includes **5 skills** organized in 3 categories:

### Context Management

#### `/context-curator` - Context Extraction & Maintenance
**Bootstrap on first run, then curate regularly** to extract learnings from conversations.

**What it does**:
- **First run**: Offers to bootstrap context system with best practices for distributed skills
- **Ongoing**: Extracts preferences, patterns, and decisions from work sessions
- Discovers YOUR domains dynamically (reads context/_index.md)
- Maps context to appropriate domain by topic
- Validates quality with automated checks

**Key features**:
- Automated bootstrap (5 min setup)
- Quality gates at Steps 7.5 and 12.9
- Index validation script (catches structural issues)
- Documentation sync guidance

**Usage**:
```bash
/context-curator                   # First run: bootstrap offer, then curate
```

---

### Research & Planning

#### `/researcher` - Multi-Methodology Research
**Conduct research** using 7 methodologies with intelligent selection.

**What it does**:
- Guides methodology selection (Design Science, UX, Market, Mixed Methods, Case Study, Org Culture, Evidence Synthesis)
- Structured execution for each methodology
- PRISMA 2020 compliance (evidence synthesis)
- Quality assessment and validation

**Usage**:
```bash
/researcher                        # Interactive methodology selection
```

**Use when**: Academic research, market analysis, user research, organizational studies.

---

#### `/planner` - Evidence-Based Planning
**Create structured plans** for multi-step tasks with quality validation.

**What it does**:
- 3 planning strategies (decompose-first, interleaved, milestone-based)
- 5-dimension quality validation
- Saves plans to /projects/ (resumable)
- Markdown + YAML format

**Usage**:
```bash
/planner                           # Interactive planning
```

**Use when**: Multi-step tasks (3+ steps), complex problems, long-horizon work.

---

### Meta-Skills (Advanced Patterns)

#### `/auditor` - ISO 19011 Systematic Audits
**Orchestrate quality/compliance/security audits** across any artifact type.

**What it does**:
- Risk-based prioritization
- Automated + manual checks
- Evidence-based assessment
- Trend tracking across audit cycles

**Usage**:
```bash
/auditor                    # Interactive setup
```

**Use when**: Quarterly audits, before releases, when quality degrades.

---

#### `/standards-sync` - Standards Synchronization
**Sync external best practices** (OWASP, PRISMA, ISO) with internal standards.

**What it does**:
- Monitors external authorities
- Evaluates relevance
- Updates internal standards
- Migrates implementations

**Usage**:
```bash
/standards-sync
```

**Use when**: Quarterly sync cycles, after external updates.

---

## Detailed Usage

### `/context-curator` - Bootstrap & Maintain

**First run** bootstraps the context system, **then run regularly** to maintain and evolve:
```bash
/context-curator
```

**What it does**:
- Reviews recent conversations or work sessions
- Identifies patterns and preferences
- Extracts context into appropriate files
- Maintains consistency across CLAUDE.md, context/, skills/, and templates/
- Creates retrospectives after major work
- Validates context quality
- Archives outdated content

**When to use**:
- After completing major work sessions
- Monthly context reviews
- When you notice recurring patterns
- After making architectural decisions
- When context needs validation or cleanup

---

## Who This Is For

✅ **You should use this if you**:
- Use Claude Code regularly (multiple times per week)
- Have established preferences for how you work
- Find yourself repeating the same instructions to Claude
- Want Claude to remember architectural decisions
- Work with **markdown-based tools** (Obsidian, Logseq, plain text)

❌ **Skip this if you**:
- Just trying out Claude Code (too early for patterns)
- Use Claude for one-off questions
- Don't use markdown-based workflows

> **Note**: This skill is optimized for **markdown editors** with wikilink support. See [TOOLING-NOTES.md](TOOLING-NOTES.md) for compatibility and adaptation guidance.

---

## Documentation

- **[SKILL-README.md](SKILL-README.md)** - Detailed explanation of the problem, solution, and philosophy
- **[skills/](skills/)** - 7 production skills (see skills/README.md for details)
- **[TOOLING-NOTES.md](TOOLING-NOTES.md)** - Markdown/Obsidian bias explained + adaptation guidance
- **[templates/](templates/)** - Reusable templates for context files
- **[examples/](examples/)** - Real-world examples showing patterns

---

## Core Principles

The system is built on **10 universal tenets**:

1. **Concept-Based Organization** - Organize by topic (python/, security/) not type (standards/, workflows/)
2. **Template-First** - Single source of truth prevents format drift
3. **Review-First** - Propose before executing (customizable)
4. **Progressive Disclosure** - Overview → details, split at ~400 lines
5. **Evidence-Based** - Extract from real work, not hypothetical
6. **Explicit Over Implicit** - Task mappings, frontmatter, cross-references
7. **Maintenance Through Reflection** - Retrospectives capture learnings
8. **Dual-Audience** - Human browsing + AI semantic search
9. **Simplicity Over Perfection** - Start small, iterate
10. **Standards Grounding** - Link to external authorities (Anthropic, OWASP, ISO)

---

## Examples

### Example 1: Communication Preferences
See [examples/example-style-preferences.md](examples/example-style-preferences.md) for a complete example of documenting communication preferences (review-first workflow, explanations with reasoning, critique preferences).

### Example 2: Git Workflow
See [examples/example-git-workflow.md](examples/example-git-workflow.md) for a complete workflow example (commit conventions, branch naming, PR process, safety rules).

### Example 3: Loading Map
See [examples/example-loading-map.md](examples/example-loading-map.md) for task-based context loading (maps tasks like "git operations" to relevant context files).

---

## Maintenance

After major work sessions:
```bash
/context-curator     # Extract learnings, validate, maintain
```

**What `/context-curator` does**:
- Extracts context from recent conversations
- Validates context quality and consistency
- Creates retrospectives
- Archives outdated content
- Maintains alignment across all guidance locations

Run it regularly (after major work, monthly, or when you notice patterns) to keep your context system fresh and valuable.

The system compounds over time—early investment pays long-term dividends.

---

## Contributing

Contributions welcome! See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

**Ways to contribute**:
- Report issues or suggest improvements
- Share examples from your projects
- Adapt skill for other tools (Notion, Confluence, etc.)
- Improve documentation
- Add features (validation checks, more templates, etc.)

---

## Adaptations

This skill is optimized for markdown-based workflows (Obsidian, Logseq, plain text).

**Want to adapt for other tools?**
- See [TOOLING-NOTES.md](TOOLING-NOTES.md) for guidance on adapting to Notion, GitHub wikis, Confluence, etc.
- The **meta-problem solution is universal**, but **implementation is markdown-specific**

---

## License

MIT License - see [LICENSE](LICENSE) for details.

---

## Acknowledgments

Built with [Claude Code](https://github.com/anthropics/claude-code) using patterns discovered across multiple projects. Special thanks to the Claude Code community for feedback and testing.

---

## Questions?

- **Issues**: [GitHub Issues](https://github.com/bcbeidel/context-system/issues)
- **Discussions**: [GitHub Discussions](https://github.com/bcbeidel/context-system/discussions)

---

**Ready to make Claude remember?**

```bash
# Install globally
git clone https://github.com/bcbeidel/context-system.git \
  ~/.claude/plugins/context-system

# Start using in any project
/context-curator
```
