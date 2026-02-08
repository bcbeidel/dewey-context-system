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

This skill creates a **context management system** that makes Claude persistently remember:

✅ Your preferences (how you like to work)
✅ Your decisions (why you chose specific approaches)
✅ Your workflows (how to execute common tasks)
✅ Your conventions (project-specific standards)

**Result**: Claude aligns with your style from message one and improves over time.

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

**3. Run the setup** (in any project):
```
/init-context-system
```

**Done!** Follow the 3-phase guided setup. Claude will remember your preferences across all projects.

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
/init-context-system
```

You should see the setup wizard. The plugin is now available globally across all your projects!

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

**That's it!** Follow the guided setup (3 phases, 1-2 hours total). Claude will now remember your preferences.

---

## What You Get

### Phase 1: Quick Setup (15-30 min)
- Basic folder structure (`context/communication`, `context/project`, `context/workflows`, `context/decisions`)
- Extract 1-2 preferences from your conversation
- Task-based context loading (context loads automatically)
- **Immediate value**: Stop repeating yourself

### Phase 2: Hands-On Learning (30-45 min)
- Extract 5-10 context pieces from conversation history
- Create your first decision log (ADR)
- Set up task-based loading for git, code review, etc.
- **Demonstrated value**: See context loading automatically for tasks

### Phase 3: Evolution Framework (15-30 min)
- Retrospective workflow (capture learnings over time)
- Maintenance checklist (keep context fresh)
- Validation process (ensure quality)
- **Long-term value**: System evolves with you, compounds over time

---

## Key Features

- **🚀 Two Skills Included**: `/init-context-system` for setup, `/context-update` for maintenance
- **🎯 Progressive Setup**: Start small (Phase 1), expand as you see value
- **📊 Evidence-Based**: Extract from actual work, not hypothetical scenarios
- **🔄 Task-Based Loading**: Context automatically loads for git, code review, documentation, etc.
- **🔄 Continuous Maintenance**: `/context-update` extracts learnings from conversations
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
    ├── _loading-map.md              # Task → context mappings
    ├── communication/               # How to interact
    ├── project/                     # Conventions & standards
    ├── workflows/                   # How to do work
    └── decisions/                   # Architectural decisions
```

---

## Usage

This plugin includes **two skills**:

### 1. `/init-context-system` - Initial Setup

**Run once** to set up the structure:
```bash
/init-context-system
```
Guided through all 3 phases interactively. Can pause after any phase.

**Resume at specific phase**:
```bash
/init-context-system --phase 2    # Resume at Phase 2
/init-context-system --phase 3    # Skip to Phase 3
```

---

### 2. `/context-update` - Ongoing Maintenance

**Run regularly** to maintain and evolve:
```bash
/context-update
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
- **[commands/](commands/)** - Skill implementation files (init-context-system.md, context-update.md)
- **[TOOLING-NOTES.md](TOOLING-NOTES.md)** - Markdown/Obsidian bias explained + adaptation guidance
- **[templates/](templates/)** - Reusable templates for context files
- **[examples/](examples/)** - Real-world examples showing patterns

---

## Core Principles

The system is built on **10 universal tenets**:

1. **Semantic Organization** - Organize by purpose (communication/project/workflows/decisions)
2. **Template-First** - Single source of truth prevents format drift
3. **Review-First** - Propose before executing (customizable)
4. **Progressive Disclosure** - Overview → details, split at ~300 lines
5. **Evidence-Based** - Extract from real work, not hypothetical
6. **Explicit Over Implicit** - Task mappings, frontmatter, cross-references
7. **Maintenance Through Reflection** - Retrospectives capture learnings
8. **Dual-Audience** - Human browsing + AI semantic search
9. **Simplicity Over Perfection** - Start small, iterate
10. **Context Governance** - Clear boundaries, quality standards

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
/context-update     # Extract learnings, validate, maintain
```

**What `/context-update` does**:
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

# Run in any project
/init-context-system
```
