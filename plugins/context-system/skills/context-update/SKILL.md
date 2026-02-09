---
name: context-update
description: "Review conversations and changes to extract and update context that improves Claude alignment with project preferences"
allowed-tools: Read, Write, Edit, Glob, Grep, Bash, AskUserQuestion
---

# Context Update

Periodically review conversations and recent changes to extract preferences, patterns, and decisions that should be captured in the context system.

**CRITICAL**: This skill ensures consistency across ALL guidance locations that agents reference.

---

## Core Principles

### 1. Multi-Location Consistency
Context must be consistent across all agent guidance locations: CLAUDE.md, context/, .claude/skills/, and extras/templates/.

### 2. Granular, Focused Files
Follow Teresa Torres's context organization: single responsibility, overview + detail pattern, task-based loading, remove bloat.

### 3. Context Categories
Extract and categorize context into: communication, project, workflows, decisions, and private.

### 4. Close the Feedback Loop
Context extraction is incomplete without skill improvement. Document patterns AND improve tools. **The test**: If a retrospective identifies a recurring problem, the solution should include skill improvements, not just documentation.

### 5. Progressive Enhancement
Build context over time: start with high-value insights, add examples, refine based on patterns, remove obsolete context, archive when superseded.

**For detailed principles**: See [GUIDANCE-LOCATIONS.md](GUIDANCE-LOCATIONS.md)

---

## Quick Start

Choose your entry point:
- **Session retrospective?** → See [phase-1-discovery.md](phase-1-discovery.md) Step 3
- **Extract from conversation?** → See [extraction-patterns.md](extraction-patterns.md)
- **Update existing context?** → See [phase-3-updates.md](phase-3-updates.md)
- **Need examples?** → See [examples.md](examples.md)

---

## Workflow Overview

### Phase 1: Review & Extract
Understand what needs review, identify current guidance locations, and extract relevant context from conversations, git changes, or patterns.

**See**: [phase-1-discovery.md](phase-1-discovery.md) for complete guide

**Key steps**:
- Step 1: Understand scope (conversation, git, topic, audit, retrospective)
- Step 2: Identify guidance locations (CLAUDE.md, context/, skills, templates)
- Step 3: Extract context (communication, project, workflow, decisions, private)

### Phase 2: Categorize & Organize
Map extracted insights to context structure, check for existing coverage, and plan updates to avoid duplication.

**See**: [phase-2-organization.md](phase-2-organization.md)

**Key steps**:
- Step 4: Map to context structure (category, specificity, existing files)
- Step 5: Check existing context (avoid duplication, ensure consistency)

### Phase 3: Update Context
Create or update context files, update indexes, modify CLAUDE.md if needed, **update skills** (mandatory!), update templates, and consider archival or file splitting.

**See**: [phase-3-updates.md](phase-3-updates.md)

**Key steps**:
- Step 6: Create or update context files (use templates)
- Step 7: Update indexes (_index.md, _loading-map.md)
- Step 8: Update CLAUDE.md (vault-level only)
- Step 9: **Update skills** (MANDATORY - close feedback loop!)
- Step 10: Update templates (if applicable)
- Step 11: Consider archival (decisions/retros >3 months old)
- Step 11b: Consider file splitting (files >400-500 lines)

**CRITICAL**: Step 9 (Update Skills) is mandatory when learnings affect skill execution. Don't just document problems - fix the skills!

### Phase 4: Validate & Commit
Verify consistency across all guidance locations, review with user, and commit changes.

**See**: [phase-4-validation.md](phase-4-validation.md)

**Key steps**:
- Step 12: Cross-reference check (all locations consistent)
- Step 13: Review with user (present summary)
- Step 14: Commit changes (follow git conventions)

---

## Extraction Patterns

**See**: [extraction-patterns.md](extraction-patterns.md) for detailed patterns

**Quick reference**:
- **From conversations**: Explicit preferences, corrections, repeated patterns, decisions with rationale
- **From git**: New conventions, structural changes, template updates, repeated patterns
- **From patterns**: Task breakdown, decision-making, quality verification, documentation structure

---

## Examples

**See**: [examples.md](examples.md) for 5 complete examples:
1. Extract communication preference
2. Extract decision
3. Update multiple locations
4. Split large context file
5. Retrospective → Context + Skill Improvement (full feedback loop)

---

## Guidance Location Reference

### 1. CLAUDE.md
**Purpose**: Vault-wide instructions for all Claude interactions

**Update when**: Major vault organization changes, new folder added, core conventions change, critical workflows established

**Don't update for**: Specific preferences (use context/), detailed guidelines (use context/), temporary patterns

### 2. context/ Folder
**Purpose**: Persistent, categorized context for alignment

**Update when**: New preference discovered, pattern identified, decision made, workflow clarified, standards established

**Structure**:
- `communication/` - How to communicate (style-preferences overview → clarity, workflow-patterns, teaching)
- `project/` - Project knowledge and standards (vault-conventions, governance, archival)
- `workflows/processes/` - Step-by-step workflows (git-practices overview → commit, workflow, safety)
- `workflows/standards/` - Quality checklists
- `workflows/retrospectives/` - Session learnings (recent only, archive/YYYY/ for old)
- `decisions/` - What was decided and why (archive/YYYY/ for old)
- `private/` - Sensitive context (git-ignored)

### 3. .claude/skills/*/SKILL.md
**Purpose**: Domain-specific task workflows

**Update when**: Task workflow changes, new requirements added, context affects skill execution, quality standards change

**Reference context**: Use `**See**: file` format

### 4. extras/templates/*.md
**Purpose**: Note templates for consistency

**Update when**: Frontmatter fields change, structure evolves, new conventions added, format requirements change

**For complete guidance location reference**: See [GUIDANCE-LOCATIONS.md](GUIDANCE-LOCATIONS.md)

---

## Quality Guidelines

### Context Note Quality
**Good context notes**: Specific and actionable, include concrete examples, explain the "why" not just "what", link to related context, kept current

**Avoid**: Vague guidance, obvious information, outdated patterns, conflicting guidelines, over-engineering

### Decision Log Quality
**Good decisions**: State problem clearly, document what was decided, explain why (rationale), list alternatives considered, note implications

**Avoid**: Decisions without context, missing rationale, no alternatives mentioned, unclear implications

### Cross-Reference Quality
**Ensure**: All context files in indexes, related context linked together, skills reference relevant context, CLAUDE.md links to context, no broken wikilinks

---

## Edge Cases

### Conflicting Context
If new context conflicts with existing: Review both, determine which is current, update or deprecate old context, document the change, check all references

### Unclear Category
If context doesn't fit cleanly: Ask user for guidance, consider creating new category, document in multiple places with cross-references, update indexes appropriately

### Too Much Context
If context becomes overwhelming: Consolidate related items, archive outdated context, create higher-level summaries, link to details from summaries

### Private vs Public
If unclear whether context is sensitive: Err on side of caution (make private), ask user if uncertain, can always move from private to public later, check for PII/work details/personal info

---

## Maintenance Cadence

**Suggested frequency**:
- **After major work**: Extract decisions and patterns immediately
- **Weekly**: Light review of recent conversations
- **Monthly**: Comprehensive context audit
- **Quarterly**: Cross-reference validation and cleanup

**Ask user to establish their preferred cadence.**

---

## Related Documentation

- [GUIDANCE-LOCATIONS.md](GUIDANCE-LOCATIONS.md) - Complete guide to where context lives
- [QUICK-REFERENCE.md](QUICK-REFERENCE.md) - Quick reference card for context updates
- [[context-system/_index]] - Context system documentation
- [[context-system/context-governance]] - Context maintenance guidelines
- [[context-system/context-archival-strategy]] - Archival process for decisions/retrospectives

---

## Remember

**DO**:
- Extract context progressively
- Use concrete examples
- Update all relevant locations (including skills!)
- Close the feedback loop: retrospective → context → skill improvement
- Verify cross-references
- Keep context current
- Ask user when uncertain
- Create new skills for reusable patterns
- Update existing skills when better patterns emerge

**DON'T**:
- Create context prematurely
- Duplicate across locations
- Leave broken references
- Skip validation checks
- Update without user review
- Mix private and public context
- Stop at documentation (update the actual skills too!)
