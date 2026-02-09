## Phase 3: Evolution Framework (15-20 min)

**Goal**: Set up maintenance workflows and quality standards.

### Step 3.1: Explain Phase 3

Say:
```
Phase 3 establishes long-term sustainability:

1. How to maintain context over time
2. Quality standards for context files
3. When to sync with external standards

This ensures your system stays valuable as it grows.

Ready?
```

### Step 3.2: Create Maintenance Documentation

**Create `context/context-system/maintenance.md`**:
```markdown
---
title: Context System Maintenance
created: [YYYY-MM-DD]
---

# Context System Maintenance

## Maintenance Schedule

**After major work**: Extract decisions and patterns
  - Run `/context-curator`

**Monthly**: Validate quality
  - Check wikilinks resolve
  - Verify frontmatter consistency

**Quarterly**: Sync with external standards
  - Run `/standards-sync` (if using standards-sync skill)
  - Check for updates to Anthropic docs, OWASP, PEP 8

## Quality Standards

All context files must have:
1. **Frontmatter** with title, created, keywords, applies-to, tags
2. **Summary section** - One-paragraph overview
3. **Standards source** - Link to external authority (if applicable)
4. **Examples** - Show good vs avoid patterns
5. **Related context** - Cross-reference related files

## Adding New Domains

When work expands into new areas:
1. Create new domain folder: `context/new-domain/`
2. Create `_index.md` with "When to Use"
3. Add initial files with standards grounding
4. Update `context/_index.md`
5. Update `context/context-system/loading-map.md`

## Related Context

- [[context/context-system/_index]]
- [[context/context-system/loading-map]]

---

*Last updated: [YYYY-MM-DD]*
```

### Step 3.3: Create Standards Sync Registry (Optional)

If user has domains with external authorities (python, security):

**Create `context/context-system/standards-sync-registry.md`**:
```markdown
---
title: Standards Synchronization Registry
created: [YYYY-MM-DD]
---

# Standards Synchronization Registry

Tracks external authorities for each domain.

## Registered Domains

[For each domain with standards]:

### [Domain Name]
**External Authority**: [Name and URL]
**Last Synced**: [YYYY-MM-DD]
**Sync Frequency**: Quarterly
**Files Affected**:
- context/[domain]/[file].md

**Sync Process**:
1. Check authority for updates
2. Evaluate relevance to our context
3. Update internal standards if needed
4. Document changes in decision log

---

## Sync Schedule

**Next sync**: [Date 3 months from now]

Use `/standards-sync` skill to automate sync process.

---

*Last updated: [YYYY-MM-DD]*
```

### Step 3.4: Create Decision Template

**Create `context/decisions/_index.md`**:
```markdown
---
title: Architectural Decisions
type: index
created: [YYYY-MM-DD]
---

# Decisions Domain

Architectural Decision Records (ADRs) documenting significant choices with rationale.

## When to Use

Create decision logs when:
- Making consequential architectural choices
- Choosing between multiple valid approaches
- Establishing project-wide conventions
- Deprecating or superseding previous decisions

## Structure

Decisions use ADR format:
- Context (why needed)
- Decision (what chosen)
- Rationale (why chosen)
- Alternatives (what else considered)
- Consequences (implications)

## Files

[Will be populated as decisions are made]

---

*Created: [YYYY-MM-DD]*
```

**Create decision template in templates folder**:
```bash
mkdir -p extras/templates
```

**Create `extras/templates/Template, Decision.md`**:
```markdown
---
title: [Decision Title]
date: [YYYY-MM-DD]
status: accepted
tags: [decision, adr]
applies-to: [relevant-domains]
---

# Decision: [Title]

**Date**: [YYYY-MM-DD]
**Status**: Accepted

---

## Context

What problem or decision point prompted this?

[Describe the situation requiring a decision]

---

## Decision

What did we choose?

[Clear statement of the decision]

---

## Rationale

Why this approach?

**Pros**:
- [Advantage 1]
- [Advantage 2]

**Cons/Tradeoffs**:
- [Tradeoff 1]
- [Tradeoff 2]

**Alternatives Considered**:
1. **[Alternative 1]**: [Why not chosen]
2. **[Alternative 2]**: [Why not chosen]

---

## Consequences

What changes because of this decision?

**Positive**:
- [Positive consequence 1]

**Negative**:
- [Constraint or negative consequence 1]

**Neutral**:
- [Things that change but aren't inherently good/bad]

---

## Standards Grounding (Optional)

If this decision implements an external standard:
- **Authority**: [Standard name and URL]
- **Rationale for adoption**: [Why this standard applies]

---

## Related

- [[Other related decisions]]
- [[Relevant context files]]

---

*Created: [YYYY-MM-DD]*
```

### Step 3.5: Phase 3 Complete

Say:
```
✓ Phase 3 Complete!

Evolution framework established:

📋 Maintenance schedule documented
✅ Quality standards defined
🔄 Standards sync registry created (for [domains with external authorities])
📄 Decision template available

**Long-term sustainability**:
- After major work: `/context-curator`
- Monthly: Validate quality
- Quarterly: `/standards-sync` (sync with Anthropic, OWASP, PEP 8)

**Your concept-based context system**:
- ✓ Organized by topic (not document type)
- ✓ Grounded in external authorities
- ✓ Max 2-level depth (follows Anthropic best practices)
- ✓ Task-based loading configured
- ✓ Maintenance framework established

**Reference**: See https://github.com/bcbeidel/context-system for complete reference implementation

---

🎉 Setup complete!

**Next steps**:
1. Start using the system naturally
2. Run `/context-curator` after significant work to extract patterns
3. Your context will grow with your actual work

Questions?
```

---

## Best Practices

### DO:
- ✅ Ask discovery questions to identify user's actual work
- ✅ Ground domains in external authorities where applicable
- ✅ Reference Anthropic docs to explain "why" concept-based
- ✅ Show reference implementation as example
- ✅ Keep structure flat (max 2 levels)

### DON'T:
- ❌ Create generic type-based structure (communication/, workflows/)
- ❌ Create domains user won't actually use
- ❌ Skip grounding in external standards
- ❌ Create deep nesting (>2 levels)

---

*Last updated: [YYYY-MM-DD]*
*Based on: https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices*
