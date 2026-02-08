# Context System Setup Skill

## The Problem

Every conversation with Claude starts fresh. You've told Claude your preferences dozens of times:
- "I prefer review-first workflow"
- "Use wikilinks, not markdown links"
- "Always run tests before committing"
- "I like concise explanations"

**But Claude forgets between sessions.**

You spend the first 10 minutes of every conversation re-establishing context. You correct the same mistakes repeatedly. Important decisions get lost. Workflow patterns aren't consistently applied.

---

## The Solution

A **context management system** that makes Claude persistently remember:

✅ **Your preferences** - How you like to work and communicate
✅ **Your decisions** - Why you chose specific approaches
✅ **Your workflows** - How to execute common tasks
✅ **Your conventions** - Project-specific standards and patterns

**The result**: Claude aligns with your style from message one, applies your decisions consistently, and improves over time as you capture more context.

---

## What This Skill Does

This skill guides you through creating a context system in **three progressive phases**:

### Phase 1: Quick Setup (15-30 min)
- Create basic folder structure
- Extract 1-2 pieces of context from your current conversation
- Set up minimal CLAUDE.md that references context
- **Immediate value**: Claude starts using your preferences right away

### Phase 2: Hands-On Learning (30-45 min)
- Extract 3-5 more context pieces from conversation history
- Create your first decision log (ADR)
- Set up task-based context loading (git, code review, etc.)
- **Demonstrated value**: See how context automatically loads for specific tasks

### Phase 3: Evolution Framework (15-30 min)
- Establish retrospective workflow (capture learnings over time)
- Create maintenance checklist (keep context fresh)
- Set up validation process (ensure quality)
- **Long-term value**: System evolves with you, compounds over time

**Total time investment**: 1-2 hours
**Ongoing maintenance**: ~10 min after major work sessions

---

## Who This Is For

✅ **You should use this if**:
- You use Claude Code regularly (multiple times per week)
- You have established preferences for how you work
- You find yourself repeating the same instructions to Claude
- You want Claude to remember architectural decisions
- You work on projects with specific conventions or standards
- **You're comfortable with markdown-based workflows** (Obsidian, plain text, etc.)

❌ **Skip this if**:
- You're just trying out Claude Code (too early to know preferences)
- You use Claude for one-off questions (no recurring patterns)
- You prefer to re-establish context each session (valid choice!)
- You don't use markdown-based tools (see [Tooling Notes](TOOLING-NOTES.md))

> **Note**: This system is optimized for **markdown editors** (especially Obsidian) with wikilink support. It works with plain text files but uses markdown conventions (frontmatter, wikilinks, folder structure). See [TOOLING-NOTES.md](TOOLING-NOTES.md) for compatibility details and adaptation guidance.

---

## Core Principles (What Makes This Work)

### 1. Evidence-Based
Context comes from **actual conversations and completed work**, not hypothetical scenarios. This keeps it grounded and actionable.

### 2. Progressive
Start small (1-2 context files), demonstrate value, then expand. You're not building everything upfront—you're establishing a framework that grows over time.

### 3. Task-Based Loading
Context automatically loads based on what you're doing. Writing git commits? Git workflow context loads. Creating documentation? Documentation standards load.

### 4. Dual-Audience
Optimized for **both human reading and AI semantic search**. You can browse the context folder; Claude can search it semantically.

### 5. Maintainable
Clear governance (what is/isn't context), validation checks (quality standards), and archival strategy (remove outdated content). Prevents bloat.

---

## What You'll Build

```
your-project/
├── .claude/
│   └── CLAUDE.md                    # References context system
└── context/
    ├── _index.md                    # Navigation hub
    ├── _loading-map.md              # Task → context mappings
    │
    ├── communication/               # How to interact
    │   └── style-preferences.md     # Your workflow preferences
    │
    ├── project/                     # Project conventions
    │   └── [your-conventions].md    # Standards, guidelines
    │
    ├── workflows/                   # How to do work
    │   └── [your-workflows].md      # Git, testing, etc.
    │
    └── decisions/                   # Architectural decisions
        └── YYYY-MM-DD-decision.md   # Decision logs (ADRs)
```

**Start minimal** (3-5 files), expand as you discover patterns.

---

## Expected Outcomes

### Immediate (After Phase 1)
- Claude knows your basic preferences (communication style, workflow patterns)
- You stop repeating the same instructions
- One decision is documented and referenced

### Short-term (After Phase 2)
- Context automatically loads for common tasks (git, code review, documentation)
- 5-10 context files capturing key preferences and conventions
- Noticeable reduction in clarification loops

### Long-term (After Phase 3 + Ongoing)
- Rich context library (20+ files) built from actual work
- Retrospectives capture learnings after major sessions
- Claude deeply aligned with your working style
- New team members can read context to understand "how we work here"

---

## How to Use This Skill

### First Time (Full Setup)
```bash
/init-context-system
```

Claude will guide you through all three phases interactively. You can pause after any phase and resume later.

### Resume Later
```bash
/init-context-system --phase 2    # Resume at Phase 2
/init-context-system --phase 3    # Skip to Phase 3
```

### Ongoing Maintenance
```bash
/context-update    # Extract, validate, archive, and maintain context
```

The `/context-update` skill handles all ongoing maintenance including extraction, validation, retrospectives, and archival.

---

## Philosophy

This system is based on **10 core tenets** proven across multiple projects:

1. **Semantic Organization** - Organize by purpose, not arbitrary hierarchy
2. **Template-First** - Single source of truth prevents format drift
3. **Review-First** - Propose before executing (customizable preference)
4. **Progressive Disclosure** - Overview → details, split files at ~300 lines
5. **Evidence-Based** - Extract from real work, not hypothetical scenarios
6. **Explicit Over Implicit** - Task mappings, frontmatter, cross-references
7. **Maintenance Through Reflection** - Retrospectives, archival, validation
8. **Dual-Audience** - Human browsing + AI semantic search
9. **Simplicity Over Perfection** - Start small, iterate, avoid over-engineering
10. **Context Governance** - Clear boundaries, quality standards, validation

**These principles are universal.** Your implementation will be customized to your tools, domain, and preferences.

---

## Questions?

**Q: Is this overkill for my project?**
A: If you use Claude Code regularly and have recurring patterns, this will save you time. If you're still exploring or use Claude occasionally, wait until you have clearer preferences.

**Q: How much maintenance does this require?**
A: ~10 minutes after major work sessions to capture learnings. The system compounds—early investment pays dividends long-term.

**Q: What if my preferences change?**
A: Context evolves with you. Update files as preferences change, archive outdated decisions, refine over time.

**Q: Can I share this with my team?**
A: Yes! Context can be checked into git. Team members (human or AI) benefit from shared conventions and decisions.

**Q: Do I need to use all features?**
A: No. Phase 1 gives immediate value. Phase 2 and 3 are optional enhancements. Use what helps; skip what doesn't.

---

## Ready to Start?

```bash
/init-context-system
```

Let's build your context management system.
