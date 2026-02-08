# Getting Started with Context System

Welcome! This guide helps you choose the right path for building your context management system.

> **📖 Standards-Based Approach**: All patterns grounded in [Anthropic Best Practices](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices), [ISO 19011](https://www.iso.org/standard/70017.html), [OWASP](https://owasp.org/www-project-top-ten/), and [PRISMA 2020](http://www.prisma-statement.org/).
>
> **See**: [Standards & Sources](./standards-sources.md) for complete verification URLs.

---

## What You'll Get

### 🚀 **Context Management Plugin**
**Production-ready skills** for persistent context:

**Setup & Maintenance**:
- `/init-context-system` - Discovery-driven setup wizard
- `/context-update` - Domain-agnostic extraction

**Meta-Skills**:
- `/audit` - ISO 19011 systematic audits
- `/standards-sync` - Sync external best practices

**Utilities**:
- `/compare` - Weighted decision matrices
- `/diagram` - Mermaid diagrams
- `/systematic-review` - PRISMA 2020 research

**Time investment**: 1-2 hours for initial setup

---

## Quick Start (Plugin)

### Step 1: Install the Plugin

In Claude Code, add the marketplace:
```bash
/plugin marketplace add bcbeidel/context-system
```

Then install via the Discover tab:
```bash
/plugin
```

Navigate to **Discover** → Install "context-system"

### Step 2: Run the Setup Wizard

```bash
/init-context-system
```

Follow the guided 3-phase setup:

**Phase 1 (15-30 min)** - Basic structure + 1-2 preferences
**Phase 2 (30-45 min)** - Extract 5-10 context pieces
**Phase 3 (15-30 min)** - Evolution framework

You can pause after any phase and resume later.

### Step 3: Start Using the Skills

Once setup is complete, you have access to:

**Maintenance**:
```bash
/context-update    # Extract learnings from conversations
```

**Quality**:
```bash
/audit             # Run systematic audits
/standards-sync    # Sync external best practices
```

**Utilities**:
```bash
/compare           # Decision matrices
/diagram           # Generate Mermaid diagrams
/systematic-review # PRISMA 2020 research
```

### Step 4: Iterate and Improve

The context system **improves over time**:

1. **Weekly**: Run `/context-update` after significant work
2. **Monthly**: Quick audit check (spot check quality)
3. **Quarterly**: Run `/audit` for comprehensive review
4. **Quarterly**: Run `/standards-sync` to stay current

---

## Understanding the Approach

### Key Patterns

**1. Concept-Based Organization**
Organize context by **topic** (python/, security/, skills/) not **type** (preferences/, workflows/).

**Authority**: [Anthropic Best Practices](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices)

**Why**: LLMs can instantly find relevant context. "Where's security content?" → `context/security/`

**2. Standards Grounding**
All patterns anchored to external authorities:
- Anthropic: Skill best practices, progressive disclosure
- ISO 19011: Audit methodology
- OWASP: Security best practices
- PRISMA 2020: Research synthesis

**Why**: When standards evolve, adapt via `/standards-sync`

**3. Domain Discovery**
Setup asks questions to identify YOUR relevant domains, then creates personalized structure.

**Why**: Works for Python developers, researchers, or knowledge workers—adapts to you

**4. Evidence-Based Maintenance**
Use `/audit` to systematically validate context quality and track improvements.

**Why**: Reproducible quality improvement with trend tracking

---

## Common Questions

### "How do I get started?"

Follow the plugin installation above:
1. Add marketplace: `/plugin marketplace add bcbeidel/context-system`
2. Install plugin via Discover tab
3. Run setup wizard: `/init-context-system`
4. Follow the 3-phase guided setup
5. Start using `/context-update` regularly

---

### "How much should I customize?"

**Start with defaults** from the plugin. Add customization when:
- You notice repeated corrections (capture as context)
- You have project-specific conventions (document in project domain)
- External standards are relevant (use standards-sync)

**Don't over-engineer upfront**. Let the system evolve based on real needs.

---

### "What if I work on multiple projects?"

The context system works at **multiple levels**:

**Global** (`~/.claude/context/`):
- Communication preferences
- General conventions
- Universal workflows

**Project-specific** (`project/.claude/context/`):
- Project conventions
- Domain-specific standards
- Team agreements

Claude loads both, with project-specific overriding global.

---

### "How do I know if it's working?"

**Positive signals**:
- Claude aligns with your style without prompting
- You spend less time correcting
- Decisions don't get re-litigated
- Patterns become consistent

**Negative signals**:
- You still repeat yourself frequently
- Context feels outdated
- Claude doesn't reference context

**Run `/audit` quarterly** to validate quality objectively.

---

## Next Steps

1. Install plugin: `/plugin marketplace add bcbeidel/context-system`
2. Run setup: `/init-context-system`
3. Start iterating with `/context-update`
4. Run `/audit` quarterly for quality validation
5. Run `/standards-sync` quarterly to stay current

---

## Additional Resources

- **[Plugin Documentation](../plugins/context-system/README.md)** - Detailed skill documentation
- **[Standards & Sources](./standards-sources.md)** - External authority mapping
- **[Skill Reference](../plugins/context-system/skills/README.md)** - All 7 skills explained

---

## Support

- **Issues**: https://github.com/bcbeidel/context-system/issues
- **Discussions**: https://github.com/bcbeidel/context-system/discussions

---

**Remember**: This is a **progressive system**. Start small, iterate based on real use, and let it evolve with you.
