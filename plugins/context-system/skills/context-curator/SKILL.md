---
name: context-curator
description: "Review conversations and changes to extract and update context that improves Claude alignment with project preferences"
allowed-tools: Read, Write, Edit, Glob, Grep, Bash, AskUserQuestion
---

# Context Curator

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
Create or update context files, **update indexes with comprehensive validation**, update CLAUDE.md and README.md when criteria met, **update skills** (mandatory!), update templates, and consider archival or file splitting.

**See**: [phase-3-updates.md](phase-3-updates.md)

**Key steps**:
- Step 6: Create or update context files (use templates)
- **Step 7: Update indexes & validate structure** (COMPREHENSIVE - with automated checks)
  - 7.1-7.3: Update domain and main indexes systematically
  - 7.4: Run automated validation (all checks must pass)
  - 7.5: Validation checkpoint (cannot proceed until ✅)
- Step 8: Update CLAUDE.md and README.md (when criteria met: skills changed, file counts ±10, domains added)
- Step 9: **Update skills** (MANDATORY - close feedback loop!)
- Step 10: Update templates (if applicable)
- Step 11: Consider archival (decisions/retros >3 months old)
- Step 11b: Consider file splitting (files >400-500 lines)

**CRITICAL**:
- Step 7 includes automated validation script that must pass before proceeding
- Step 9 (Update Skills) is mandatory when learnings affect skill execution
- Quality gates prevent incomplete curation

### Phase 4: Validate & Commit
**Comprehensive quality validation** across all guidance locations, verify with user, and commit changes.

**See**: [phase-4-validation.md](phase-4-validation.md)

**Key steps**:
- **Step 12: Cross-reference check & quality validation** (COMPREHENSIVE)
  - 12.1: Standard validation checklist
  - 12.2: Re-run index audit (automated)
  - 12.3: File size compliance check
  - 12.4: Frontmatter validation
  - 12.5: Cross-reference integrity
  - 12.6: Skill quality gate (if skills updated)
  - 12.7: Self-critique quality gate
  - 12.8: Validation summary report
  - 12.9: Validation checkpoint (cannot proceed until ✅)
- Step 13: Review with user (present summary)
- Step 14: Commit changes (follow git conventions)

**Quality gates enforced**:
- All automated checks must pass (✅) before user review
- Implements validation from [[context-system/context-validation-checks]]
- Implements quality gates from [[skills/execution-standards]]

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

---

## Quality Tools & Validation

### Automated Validation Script

**Location**: `.claude/scripts/context-curator-validate-indexes.sh`

**Purpose**: Automated index completeness and accuracy validation

**Checks performed**:
1. Domain index completeness (all files indexed)
2. Main index total accuracy (matches actual count)
3. Domain count consistency (domain ↔ main index alignment)

**Usage**:
```bash
# From vault root
.claude/scripts/context-curator-validate-indexes.sh

# Returns:
# - Exit 0 if all ✅ (all checks passed)
# - Exit 1 if any ❌ (validation failed)
```

**When to run**:
- After Step 7 (index updates) - mandatory before proceeding
- After Step 12.2 (comprehensive validation) - verify fixes
- Any time you update context files (quick check)

---

### Index Update Template

**Location**: `index-update-template.md`

**Purpose**: Quick reference for fixing validation failures

**Contains**:
- Domain index update commands (copy-paste ready)
- Main index update commands (file count, domain count)
- Validation re-run instructions

**Use when**: Validation script shows ❌ or ⚠️ and you need quick fix commands

---

### Quality Standards Enforced

**From** [[context-system/context-validation-checks]]:
- ✅ Check 1: File size compliance (300/400/500 thresholds)
- ✅ Check 2-3: Frontmatter validation (required fields, consistency)
- ✅ Check 5: Cross-reference integrity (no broken wikilinks)
- ✅ Check 8: Index and loading map updates (comprehensive)

**From** [[skills/execution-standards]]:
- ✅ Quality Gate Before Delivery (Phase 3)
- ✅ Self-critique checklist (Step 12.7)
- ✅ Honest framing (ready for review, not "complete")

**From** [[skills/audit-checklist]]:
- ✅ Structure & format compliance (SKILL.md size, frontmatter)
- ✅ Progressive disclosure compliance (3-6 reference files)
- ✅ Quality markers (Quick Start, Troubleshooting, Limitations)

**Result**: Two quality gates (Step 7.5 and Step 12.9) prevent incomplete curation
