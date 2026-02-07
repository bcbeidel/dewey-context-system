# Announcement Drafts

## GitHub Discussions (Claude Code)

**Title**: Context System Plugin - Make Claude Remember Your Preferences Across Sessions

**Body**:

Hi everyone! 👋

I've been frustrated with having to re-explain my preferences to Claude at the start of every conversation ("use review-first workflow", "run tests before committing", etc.). So I built a plugin to solve this.

### What It Does

**Context System** creates a persistent memory for Claude that remembers:
- Your preferences (how you like to work)
- Your decisions (why you chose specific approaches)
- Your workflows (how to execute common tasks)
- Your conventions (project-specific standards)

Result: Claude aligns with your style from message one and improves over time through evidence-based extraction.

### Installation

One command:
```bash
git clone https://github.com/bcbeidel/skill-context-system.git ~/.claude/plugins/skill-context-system
```

Then run `/init-context-system` in any project.

### Two Skills Included

**`/init-context-system`** - Initial setup (3-phase guided process)
**`/context-update`** - Ongoing maintenance (extract, validate, archive)

### Key Features

- 🎯 Progressive setup (start small, expand as you see value)
- 📊 Evidence-based (extracts from actual work, not hypothetical)
- 🔄 Task-based loading (context auto-loads for git, code review, etc.)
- 📝 Templates & examples included
- 🧩 Adaptable to your workflow

### Repository

https://github.com/bcbeidel/skill-context-system

MIT licensed, production-ready, comprehensive documentation.

### Compatibility

Optimized for markdown-based workflows (Obsidian, Logseq, plain text). See TOOLING-NOTES.md for adaptation to other tools.

---

Would love feedback, issues, or contributions! Let me know if you try it.

---

## Twitter/X

**Tweet 1** (Main announcement):
```
🚀 New Claude Code plugin: Context System

Tired of re-explaining your preferences to Claude every session?

This plugin makes Claude remember:
✅ Your preferences
✅ Your decisions
✅ Your workflows
✅ Your conventions

One command: git clone https://github.com/bcbeidel/skill-context-system.git ~/.claude/plugins/skill-context-system

https://github.com/bcbeidel/skill-context-system

#ClaudeAI #AI #DeveloperTools
```

**Tweet 2** (Features thread):
```
Why I built this:

Every conversation with Claude started fresh. I'd spend 10 minutes re-explaining:
- "Use review-first workflow"
- "Run tests before committing"
- "Follow conventional commits"

Now Claude remembers automatically. 🧠

Features 🧵
```

```
1/ Two skills included:

/init-context-system - 3-phase setup (30-90 min once)
/context-update - Ongoing maintenance (extract learnings)

Progressive approach: start small, expand as you see value
```

```
2/ Evidence-based extraction

Captures patterns from actual work, not hypothetical scenarios.

Creates:
- Communication preferences
- Workflow documentation
- Decision logs (ADRs)
- Task-based context loading
```

```
3/ Task-based auto-loading

When you do git operations → Git workflow context loads automatically
When you review code → Review standards load automatically

No manual context switching. Just works. ⚡
```

```
4/ Built on 10 universal principles:

- Semantic organization
- Template-first architecture
- Evidence-based extraction
- Progressive disclosure
- Maintenance through reflection

The meta-problem solution is universal, implementation is markdown-optimized.
```

```
5/ Open source (MIT), production-ready

📦 12 files, 3,400+ lines of documentation
📝 Templates & real-world examples
🔄 Built-in maintenance workflows
📖 Comprehensive guides

Try it: git clone https://github.com/bcbeidel/skill-context-system.git ~/.claude/plugins/skill-context-system

https://github.com/bcbeidel/skill-context-system
```

---

## LinkedIn

**Title**: Solving the "Claude Forgets" Problem with Context Management

**Post**:

I've spent the last few weeks solving a problem that many AI-assisted developers face: Claude forgets your preferences between sessions.

**The Problem**

Every conversation with Claude Code starts fresh. You repeatedly explain:
- "I prefer review-first workflow"
- "Use wikilinks, not markdown links"
- "Always run tests before committing"

You spend the first 10 minutes of every session re-establishing context.

**The Solution**

I built a Claude Code plugin that creates a persistent context management system. Think of it as long-term memory for Claude.

**What It Remembers**
- Your preferences (how you like to work)
- Your decisions (why you chose specific approaches)
- Your workflows (how to execute common tasks)
- Your conventions (project-specific standards)

**How It Works**

1. Install: `git clone https://github.com/bcbeidel/skill-context-system.git ~/.claude/plugins/skill-context-system`
2. Setup: `/init-context-system` (3-phase guided process)
3. Maintain: `/context-update` (extract learnings after major work)

**Key Innovation: Evidence-Based Extraction**

Rather than hypothetical scenarios, the system extracts patterns from actual conversations and work. Context compounds over time—the more you use it, the better it gets.

**Built on Universal Principles**

The architecture solves a meta-problem (persistent context across conversations) using 10 universal tenets:
- Semantic organization by purpose
- Template-first architecture (single source of truth)
- Task-based context loading (auto-loads relevant context)
- Progressive disclosure (start small, expand)
- Maintenance through reflection (retrospectives)

**Open Source & Production-Ready**

MIT licensed, 3,400+ lines of documentation, templates and examples included.

GitHub: https://github.com/bcbeidel/skill-context-system

**Who Should Use This**

If you use Claude Code regularly and find yourself repeating preferences, this will save you significant time and improve Claude's alignment with your working style.

Would love feedback from the community!

#AI #DeveloperTools #Productivity #OpenSource #ClaudeAI

---

## Reddit (r/ClaudeAI)

**Title**: [Plugin] Context System - Make Claude Remember Your Preferences Across Sessions

**Post**:

Hey r/ClaudeAI! I built a plugin to solve a problem I kept running into: having to re-explain my preferences to Claude at the start of every conversation.

**TL;DR**

Plugin that makes Claude persistently remember your preferences, decisions, and workflows. One command install, works everywhere.

```bash
git clone https://github.com/bcbeidel/skill-context-system.git ~/.claude/plugins/skill-context-system
```

**The Problem**

Every Claude Code session starts fresh. I'd spend 10+ minutes re-explaining:
- "Use review-first workflow"
- "Run tests before committing"
- "Follow conventional commit format"

It was frustrating and repetitive.

**The Solution**

Context System creates persistent memory for Claude:

- **Your preferences** - Communication style, workflow patterns
- **Your decisions** - Architectural choices with rationale (ADRs)
- **Your workflows** - Git practices, code review standards, etc.
- **Your conventions** - Project-specific standards

**How It Works**

1. Install the plugin (one command, works everywhere)
2. Run `/init-context-system` - 3-phase guided setup
3. Use `/context-update` - Extract learnings after major work

**Key Features**

- **Evidence-based**: Extracts from actual conversations, not hypothetical
- **Task-based loading**: Context auto-loads for git, code review, docs
- **Progressive**: Start small (Phase 1), expand as you see value
- **Templates included**: Don't reinvent the wheel
- **MIT licensed**: Open source, production-ready

**What Makes This Different**

Most "memory" solutions are ad-hoc. This is architectured around 10 universal principles:
- Semantic organization by purpose
- Template-first (single source of truth)
- Progressive disclosure (overview → details)
- Maintenance through reflection

It's not just storing preferences—it's a system for continuous alignment.

**Compatibility**

Optimized for markdown-based workflows (Obsidian, Logseq, plain text). Adaptable to other tools.

**GitHub**: https://github.com/bcbeidel/skill-context-system

**Try It**

```bash
git clone https://github.com/bcbeidel/skill-context-system.git ~/.claude/plugins/skill-context-system
/init-context-system
```

Happy to answer questions or take feedback!

---

## Hacker News (Show HN)

**Title**: Show HN: Context System – Make Claude remember your preferences across sessions

**Post**:

I built a Claude Code plugin that solves the "Claude forgets between sessions" problem.

Every conversation with Claude Code starts fresh. You repeatedly explain your preferences ("use review-first workflow", "run tests before committing"), spending 10+ minutes re-establishing context each session.

Context System creates persistent memory for Claude. It extracts preferences, decisions, workflows, and conventions from actual conversations and makes them available across all future sessions.

Key features:
- One-command plugin install (works everywhere)
- Evidence-based extraction (from real work, not hypothetical)
- Task-based auto-loading (git operations load git context)
- Progressive setup (start small, expand)
- Two skills: /init-context-system (setup) + /context-update (maintenance)

Built on 10 universal principles (semantic organization, template-first architecture, progressive disclosure, etc.). The meta-problem solution is tool-agnostic; current implementation is optimized for markdown-based workflows.

MIT licensed, production-ready, comprehensive docs.

GitHub: https://github.com/bcbeidel/skill-context-system

```bash
git clone https://github.com/bcbeidel/skill-context-system.git ~/.claude/plugins/skill-context-system
```

Would love feedback from the community!

---

## Awesome Claude Code (Pull Request)

**File to edit**: README.md in https://github.com/hesreallyhim/awesome-claude-code

**Section**: Plugins or Skills (whichever section exists)

**Entry**:

```markdown
### Context Management
- [context-system](https://github.com/bcbeidel/skill-context-system) - Make Claude persistently remember your preferences, decisions, and workflows across sessions. Includes two skills: `/init-context-system` (3-phase setup) and `/context-update` (ongoing maintenance). Evidence-based extraction, task-based auto-loading, templates included.
```

---

## Blog Post Outline (Optional)

If you want to write a more detailed blog post:

**Title**: "Building a Long-Term Memory System for Claude Code"

**Outline**:
1. The Problem: Context Doesn't Persist
2. Why This Matters: The Cognitive Load of Re-Explaining
3. The Solution: Evidence-Based Context Management
4. Architecture: 10 Universal Principles
5. Implementation: Two Skills, Progressive Setup
6. Results: Time Saved, Better Alignment
7. Lessons Learned: What Worked, What Didn't
8. Try It Yourself

