---
title: Skill Execution Standards
created: 2026-01-25
keywords:
- skills
- template-first
- quality-gates
- self-review
- skill-development
- standards
applies-to:
- skill-creation
- skill-execution
- all-skills
tags:
- context
- quality
- skills
- workflow
---
# Universal Skill Execution Standards

These standards apply to ALL skills in this vault. Every skill should follow this pattern.

## Core Principles

### 1. Template-First Architecture
**Always read the template before creating notes**

- Templates are single source of truth
- Skills should never hardcode formats
- Read → Parse → Follow (not: Hardcode → Create)
- See: [[2026-01-25-template-first-skill-architecture]]

### 2. Quality Gate Before Delivery
**Self-review work before presenting to user**

Before marking work complete, ask:
- What problems exist that I haven't mentioned?
- What would a skeptical reader notice?
- Have I verified claims and attributions?
- Is all metadata accurate (no fake dates, no empty TODOs)?
- Is this "ready for review" or am I claiming "complete"?

### 3. Primary Sources Over Secondary
**Verify information at the source**

- Find original books/papers, not just blog posts
- Include specific citations (year, publisher, page/chapter)
- Verify famous quotes actually appear in attributed works
- Note when attribution is uncertain
- Document research process

### 4. Honest Metadata > Complete Metadata
**Accuracy beats completeness**

- Don't invent dates when unknown
- Remove empty fields rather than leave TODOs
- Use today's date if creating standardized content
- Acknowledge limitations and uncertainty
- No placeholder data

### 5. Critique Framing
**Frame as "ready for review" not "complete"**

- Identify issues before user has to
- Point out limitations proactively
- Provide options, not declarations
- Focus on improvement over celebration
- See: [[communication/critique-preference]]

### 6. Skill Composition
**Automatically integrate related skills when value is obvious**

- If a skill would almost always benefit from another skill's output, integrate it automatically
- Don't require users to manually chain commands when the integration is obvious and always desired
- Example: Data import skill could automatically validate format using quality checklist
- Example: Code generation skill could auto-format using project style standards

**When to auto-integrate:**
- The integration provides clear, consistent value
- The related skill rarely fails or degrades gracefully
- The user would run both commands together 90%+ of the time

**When NOT to auto-integrate:**
- The related skill is slow or expensive
- The integration is only useful sometimes
- Users need control over when the second skill runs
- The failure mode is unclear or disruptive

**Implementation:**
- Call related skill early in workflow
- Handle failures gracefully (degrade, don't break)
- Document the integration in skill README
- Make integration transparent (user knows it's happening)

## Universal Workflow Pattern

### Phase 1: Preparation
1. **Read template**: Get current format from `extras/templates/`
2. **Check communication prefs**: Review `context/communication/` for user preferences
3. **Review similar notes**: Look at existing examples in target directory
4. **Research thoroughly**: Find primary sources, verify attributions

### Phase 2: Creation
1. **Follow template exactly**: Parse structure, don't hardcode
2. **Use accurate metadata**: Real dates or omit; no placeholders
3. **Cite primary sources**: Specific citations with page numbers
4. **Create specific content**: No generic examples or vague guidance

### Phase 3: Quality Gate (CRITICAL)
**This is where previous sessions failed - don't skip this**

1. **Self-critique checklist**:
   - [ ] Have I read this as a skeptical user would?
   - [ ] Are all claims verifiable?
   - [ ] Is metadata accurate (no fake dates)?
   - [ ] Are there empty TODO fields to remove?
   - [ ] Have I identified limitations?

2. **Content-specific checks** (if applicable):
   - [ ] One-sentence summaries are truly one sentence
   - [ ] Examples are specific, not generic
   - [ ] "When to apply" guidance is actionable
   - [ ] Attributions are verified in original sources

3. **Format consistency**:
   - [ ] Matches template structure
   - [ ] Uses wikilinks for internal references
   - [ ] Proper heading hierarchy
   - [ ] Clean, no formatting artifacts

### Phase 4: Delivery
1. **Frame appropriately**: "Ready for your review" not "Complete ✅"
2. **Document issues proactively**: Point out limitations before user notices
3. **Provide context**: What's uncertain, what trade-offs exist
4. **Invite feedback**: Make it easy for user to critique

## Common Pitfalls (From 2026-01-25 Session)

### Metadata Issues
- ❌ Fake dates: `created: 2024-01-15` when you don't know
- ✅ Honest dates: `created: 2026-01-25` (today) or omit field
- ❌ Empty TODOs: `related: []` creating maintenance debt
- ✅ Clean: Only add field when populated

### Content Quality
- ❌ Secondary sources only: "According to blog post..."
- ✅ Primary sources: "Gibson, J.J. (1977), pp. 67-82..."
- ❌ Generic examples: "A company faces challenges..."
- ✅ Specific examples: "When debugging production bug, use X because Y"
- ❌ Vague guidance: "Use this for strategic planning"
- ✅ Actionable guidance: "Use when problem too complex to solve directly"

### Delivery Issues
- ❌ Premature celebration: "All done! ✅"
- ✅ Invitation to review: "Ready for your review. Note: dates are from today since originals unknown"
- ❌ Hiding problems: Hope user doesn't notice issues
- ✅ Proactive disclosure: "Found attribution issue with X quote"

## Attribution Red Flags

Watch for these in ANY content creation:

- "X famously said..." → Verify in X's works
- "According to tradition..." → Find earliest documented source
- Popular quotes → Often misattributed (e.g., "invert, always invert")
- No specific citations → Can't verify
- Secondary sources chain → Trace to primary

## Quality Checklists by Skill Type

### Content Creation Skills
- **Structured notes**: Template followed, required fields complete, formatting consistent
- **Data extraction**: Source cited, data validated, format standardized
- **Documentation**: Accuracy verified, examples included, cross-references valid
- **Generated content**: Template followed, quality gates passed, user review obtained

### Analysis & Research Skills
- **Context updates**: Patterns extracted from actual behavior, not aspiration
- **File operations**: Verify file exists before edit, check syntax after
- **Research**: Primary sources cited, uncertainty acknowledged

## Skill-Specific Standards

Each skill SHOULD have its own quality checklist in its directory referencing these universal standards.

### Example Structure
```
.claude/skills/skill-name/
├── SKILL.md                    # Main skill definition
├── quality-checklist.md        # Skill-specific standards
└── template.md                 # Supporting templates
```

### Minimum Requirements
Every skill must:
1. Read template first (template-first architecture)
2. Apply universal quality gate before delivery
3. Reference communication preferences
4. Document skill-specific quality standards

### Skill Testing Standards

**CRITICAL**: Skills require Claude Code restart to load changes.

**Testing requirements after refactoring**:
1. **Exit Claude Code** (if running)
2. **Restart Claude Code**: `claude-code` or with task context
3. **Test each refactored skill**:
   - Invoke with `/skill-name`
   - Verify SKILL.md loads correctly
   - Check if reference files load on-demand
   - Confirm workflow executes as expected
4. **Document any issues** for follow-up

**Add to refactoring checklist**:
- [ ] Skills tested after restart
- [ ] All reference files load correctly
- [ ] Workflow executes end-to-end
- [ ] No broken links or missing files

**See**: [[skills/refactoring-workflow]] for complete refactoring process including testing phase.

## When to Create a Retro

Create a retrospective document when:
- Significant issues discovered during execution
- New patterns emerge that apply beyond current task
- User requests critique and multiple improvements result
- Quality standards need updating based on learnings

**Template**: See `context/workflows/[date]-[topic]-retro.md` format

## Examples from Real Sessions

### Poor Execution ❌
**Mental model session initial delivery**:
- Used fake dates (2024-01-15)
- Left empty `related: []` fields
- Cited books without page numbers
- Announced "Complete ✅" without self-review
- User had to request critique

### Good Execution ✅
**Mental model session refined delivery**:
- Researched primary sources with specific citations
- Removed empty fields
- Found attribution issues (Jacobi quote)
- Documented uncertainty transparently
- Framed as "ready for review"

## Integration with Communication Preferences

Before ANY delivery, check:
- [[communication/critique-preference]] - Honest critique expected
- [[communication/style-preferences]] - (if exists) User formatting preferences
- [[obsidian/vault-conventions]] - Obsidian-specific requirements

**Remember**: User prefers constructive critique over excessive praise. Quality gate is an opportunity to provide that critique yourself before delivery.

## Continuous Improvement

These standards evolve. When you discover issues:
1. Document in retro
2. Update relevant checklist
3. Add to "Common Pitfalls"
4. Share learnings across skills

## Related Documentation

- [[communication/style-preferences]] - Communication style preferences
- [[decisions/_index]] - Decision documentation patterns
- [[skills/progressive-disclosure-standard]] - Keep skills maintainable
- [[skills/audit-checklist]] - Quality validation checklist

## Quick Reference Card

**Before delivering ANY skill output:**

1. ✓ Read template first
2. ✓ Research primary sources
3. ✓ Use honest metadata
4. ✓ Self-review with critical eye
5. ✓ Frame as "ready for review"
6. ✓ Proactively identify limitations
7. ✓ Consider automatic skill integration where valuable

**Ask yourself**: "If I were the user, what would make me say 'you should have caught that'?"

That's your quality gate.
