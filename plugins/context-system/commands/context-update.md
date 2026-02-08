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
Context must be consistent across all agent guidance locations:
- **CLAUDE.md** - Vault-wide instructions and conventions
- **context/** - Persistent context notes
- **.claude/skills/** - Skill-specific workflows
- **extras/templates/** - Note templates

### 2. Granular, Focused Files
Follow Teresa Torres's context organization principles:
- **Single responsibility** - Each file covers one focused topic
- **Overview + detail pattern** - Large topics get overview file + focused guides
- **Task-based loading** - Structure enables loading only relevant context
- **Remove bloat** - Archive completed work, split large multi-topic files

Examples:
- git-practices.md → git-commit-conventions.md + git-workflow.md + git-safety.md
- style-preferences.md → communication-clarity.md + workflow-patterns.md + teaching-approach.md

### 3. Context Categories
Extract and categorize context into:
- **Communication** - Style, formatting, terminology preferences
- **Project** - Vault conventions, standards, architectural decisions
- **Workflows** - Common patterns and processes
- **Decisions** - Significant choices with rationale
- **Private** - Sensitive information (git-ignored)

### 4. Progressive Enhancement
Build context over time:
- Start with high-value insights
- Add examples from real usage
- Refine based on patterns
- Remove obsolete context
- Archive when superseded or aged out

---

## Workflow

### Phase 1: Review & Extract

#### Step 1: Understand Scope
Ask the user what to review:
- Recent conversation(s)
- Recent git changes
- Specific topic or area
- Full context audit
- **Session retrospective** (after significant work)

#### Step 2: Identify Guidance Locations
Read current state of all guidance locations:

```bash
# Main instructions
Read: CLAUDE.md

# Context index
Read: context/_index.md

# Existing context files (check which exist)
Glob: context/**/*.md

# Skills
Glob: .claude/skills/*/SKILL.md

# Templates
Glob: extras/templates/*.md
```

#### Step 3: Extract Context
Review the specified scope and extract:

**Session Retrospective** (if applicable):
- What went well during execution?
- What went poorly or could improve?
- What patterns emerged (vs one-off issues)?
- What quality issues were discovered?
- What should be applied to future sessions?
- Should a retro document be created?

When creating a retro, use template: `context/workflows/retrospectives/[date]-[topic]-retro.md`

**Communication Context**:
- Style preferences (tone, detail level, emoji usage)
- Response formatting (structure, markdown usage)
- Terminology (project-specific terms)
- Communication patterns

**Project Knowledge**:
- Vault conventions (file organization, naming)
- Technical standards (code quality, testing)
- Architectural decisions
- Tool preferences

**Workflow Patterns**:
- How tasks are approached
- Common sequences of actions
- Decision-making processes
- Quality checks

**Decisions**:
- What was decided
- Why it was decided
- Alternatives considered
- Implications

**Private Context**:
- Work-related information
- Personal preferences
- Sensitive details
- Goals and objectives

### Phase 2: Categorize & Organize

#### Step 4: Map to Context Structure
For each extracted insight, determine:

1. **Category**: communication | project | workflow | decision | private
2. **Specificity**: vault-wide vs. domain-specific (recipes, mental models, etc.)
3. **Existing file**: Does a context file already cover this?
4. **Cross-references**: What other context/guidance relates?

#### Step 5: Check Existing Context
Read relevant existing context files to:
- Avoid duplication
- Ensure consistency
- Find merge opportunities
- Identify conflicts

### Phase 3: Update Context

#### Step 6: Create or Update Context Files

**For new context notes:**
```bash
# Read template first
Read: context/TEMPLATE.md

# Create note following template structure
Write: context/[category]/[descriptive-name].md
```

**For decision logs:**
```bash
# Read decision template
Read: context/decisions/TEMPLATE-decision.md

# Create decision log with date prefix
Write: context/decisions/YYYY-MM-DD-decision-name.md
```

**For private context:**
```bash
# Save to git-ignored private folder
Write: context/private/[category]/[descriptive-name].md
```

**Context note structure:**
```yaml
---
title: Context Title
created: YYYY-MM-DD
updated: YYYY-MM-DD
keywords: [keyword1, keyword2, keyword3]
applies-to: [task-type1, task-type2]
tags: [context, category]
type: [communication|project|workflow|decision|personal]
---

# Context Title

## Summary
Brief overview (1-2 sentences)

## Details
Specific guidelines, preferences, or patterns

## Examples
Concrete examples from actual usage

## Related Context
- [[Other Context Note]]
- [[Related Guidance]]

## Notes
Additional clarifications or edge cases

---

*Last updated: YYYY-MM-DD*
```

#### Step 7: Update Indexes

**Update context/_index.md:**
- Add new context files to appropriate section
- Maintain clear organization (processes, standards, retrospectives)
- Update cross-references

**Update context/private/_index.md (if applicable):**
- Add private context files
- Keep structure consistent with public index

**Update context/_loading-map.md (if applicable):**
- Add new task types if workflows create them
- Map tasks to relevant context files
- Update "When" sections to trigger appropriate loading
- Ensure new context is discoverable by Claude

#### Step 8: Update CLAUDE.md (if needed)

Check if CLAUDE.md needs updates for:
- Vault-wide conventions that changed
- New major sections or folders
- Updated workflows
- Critical guidelines

**Only update CLAUDE.md for vault-level guidance**, not specific preferences.

#### Step 9: Update Skills (if applicable)

Check if any skills need updates:
- Read affected skill files
- Update workflows if context changed them
- Add references to new context
- Ensure consistency with new patterns

#### Step 10: Update Templates (if applicable)

Check if templates need updates:
- Frontmatter fields changed
- Structure evolved
- New conventions added

#### Step 11: Consider Archival (if applicable)

**Check for archival candidates:**
- Decisions older than 3 months that are superseded or deprecated
- Retrospectives older than 3 months (after extracting learnings)
- Context files no longer relevant

**See [[context/project/context-archival-strategy]] for complete guidelines:**
- When to archive decisions and retrospectives
- Step-by-step archival process
- Archive directory structure (decisions/archive/YYYY/, retrospectives/archive/YYYY/)
- Quality gates before archiving
- Maintenance schedule (monthly, quarterly, annual)

**Key considerations:**
- Extract learnings from retrospectives before archiving
- Update status field (superseded/deprecated) before archiving
- Move to `context/decisions/archive/YYYY/` or `context/workflows/retrospectives/archive/YYYY/`
- Update all cross-references
- Keep most recent 5-7 retrospectives active

#### Step 11b: Consider File Splitting (if applicable)

**Check for splitting candidates:**
- Context files over 400-500 lines covering multiple distinct topics
- Files that would benefit from focused, single-responsibility structure

**Splitting pattern (overview + focused guides):**
1. Create focused files for each distinct topic (e.g., git-commit-conventions.md, git-workflow.md, git-safety.md)
2. Convert original file to overview that links to focused guides
3. Update context/_index.md and context/_loading-map.md
4. Update all cross-references throughout context system

**Benefits:**
- Easier to load only relevant context for specific tasks
- Single responsibility per file
- Better task-based loading via loading map

### Phase 4: Validate & Commit

#### Step 12: Cross-Reference Check

Verify consistency across all guidance locations:

**Checklist**:
- [ ] CLAUDE.md reflects vault-wide conventions
- [ ] Context files are properly categorized
- [ ] Indexes link to all context files
- [ ] Skills reference relevant context
- [ ] Templates match current standards
- [ ] No conflicting guidance exists
- [ ] Private context is git-ignored

#### Step 13: Review with User

Present summary:
```
## Context Updates Summary

### New Context Files
- [context/communication/style-preferences.md] - Communication style guidelines
- [context/decisions/2026-01-25-decision.md] - Decision about X

### Updated Files
- [context/_index.md] - Added new entries
- [CLAUDE.md] - Updated vault structure
- [.claude/skills/recipe-scraper/SKILL.md] - Added context reference

### Key Changes
- Extracted preference: [description]
- Documented decision: [description]
- Updated convention: [description]

### Cross-Reference Validation
✅ All guidance locations consistent
✅ Indexes updated
✅ No conflicts detected
```

Ask user to review before committing.

#### Step 14: Commit Changes

Create commit following git conventions:
```bash
git add context/ CLAUDE.md .claude/skills/ extras/templates/
git commit -m "docs(context): extract context from [source]

- Add [new context files]
- Update [modified files]
- Document [key insights]

Co-Authored-By: Claude Sonnet 4.5 <noreply@anthropic.com>"
```

---

## Context Extraction Patterns

### From Conversations

**Look for:**
- Explicit preferences ("I prefer...", "Always...")
- Corrections ("Actually, it should be...", "Don't do...")
- Repeated patterns (same request multiple times)
- Decisions with rationale ("We chose X because...")
- Clarifications ("To be clear...", "What I mean is...")

**Examples:**
```
User: "I prefer you don't use emojis in commit messages"
→ Communication preference

User: "Always read the template first before creating notes"
→ Workflow pattern

User: "We decided to use lowercase tags for consistency"
→ Decision with rationale
```

### From Git Changes

**Look for:**
- New conventions in committed files
- Structural changes (folders, organization)
- Template updates
- Documentation additions
- Repeated patterns across commits

**Check:**
```bash
# Recent commits
git log -10 --oneline

# Changes in key areas
git diff HEAD~5 CLAUDE.md
git diff HEAD~5 context/
git diff HEAD~5 .claude/skills/
git diff HEAD~5 extras/templates/
```

### From Patterns

**Identify:**
- How tasks are broken down
- How decisions are made
- How quality is verified
- How documentation is structured
- How errors are handled

---

## Guidance Location Reference

### 1. CLAUDE.md
**Purpose**: Vault-wide instructions for all Claude interactions

**Update when:**
- Major vault organization changes
- New folder added
- Core conventions change
- Critical workflows established

**Don't update for:**
- Specific preferences (use context/)
- Detailed guidelines (use context/)
- Temporary patterns

### 2. context/ Folder
**Purpose**: Persistent, categorized context for alignment

**Update when:**
- New preference discovered
- Pattern identified
- Decision made
- Workflow clarified
- Standards established

**Structure:**
- `communication/` - How to communicate
  - style-preferences.md (overview) → links to clarity, workflow-patterns, teaching-approach
  - communication-clarity.md - Simplicity, progressive disclosure, accuracy
  - workflow-patterns.md - Review-first, reflection, proposing changes
  - teaching-approach.md - Explanation over automation
- `project/` - Project knowledge and standards
  - vault-conventions.md (overview) → links to wikilinks, frontmatter, tags, features
  - context-governance.md - How to maintain context
  - context-archival-strategy.md - Archival process for decisions/retrospectives
- `workflows/processes/` - Step-by-step workflows
  - git-practices.md (overview) → links to commit-conventions, workflow, safety
  - git-commit-conventions.md - Commit messages, co-authorship
  - git-workflow.md - Branches, PRs, remote operations
  - git-safety.md - Safety rules, file staging
- `workflows/standards/` - Quality checklists
- `workflows/retrospectives/` - Session learnings (recent only)
  - `archive/YYYY/` - Archived retrospectives
- `decisions/` - What was decided and why
  - `archive/YYYY/` - Archived decisions
- `private/` - Sensitive context

### 3. .claude/skills/*/SKILL.md
**Purpose**: Domain-specific task workflows

**Update when:**
- Task workflow changes
- New requirements added
- Context affects skill execution
- Quality standards change

**Reference context:**
```markdown
**See**: [[context/project/recipe-conventions]] for current standards
```

### 4. extras/templates/*.md
**Purpose**: Note templates for consistency

**Update when:**
- Frontmatter fields change
- Structure evolves
- New conventions added
- Format requirements change

---

## Quality Guidelines

### Context Note Quality

**Good context notes:**
- Are specific and actionable
- Include concrete examples
- Explain the "why" not just "what"
- Link to related context
- Are kept current

**Avoid:**
- Vague guidance ("be good", "make it nice")
- Obvious information
- Outdated patterns
- Conflicting guidelines
- Over-engineering

### Decision Log Quality

**Good decisions:**
- State the problem/question clearly
- Document what was decided
- Explain why (rationale)
- List alternatives considered
- Note implications

**Avoid:**
- Decisions without context
- Missing rationale
- No alternatives mentioned
- Unclear implications

### Cross-Reference Quality

**Ensure:**
- All context files in indexes
- Related context linked together
- Skills reference relevant context
- CLAUDE.md links to context
- No broken wikilinks

---

## Edge Cases

### Conflicting Context
If new context conflicts with existing:
1. Review both contexts
2. Determine which is current
3. Update or deprecate old context
4. Document the change
5. Check all references

### Unclear Category
If context doesn't fit cleanly:
1. Ask user for guidance
2. Consider creating new category
3. Document in multiple places with cross-references
4. Update indexes appropriately

### Too Much Context
If context becomes overwhelming:
1. Consolidate related items
2. Archive outdated context
3. Create higher-level summaries
4. Link to details from summaries

### Private vs Public
If unclear whether context is sensitive:
1. Err on side of caution (make private)
2. Ask user if uncertain
3. Can always move from private to public later
4. Check for PII, work details, personal info

---

## Maintenance Cadence

**Suggested frequency:**
- **After major work**: Extract decisions and patterns immediately
- **Weekly**: Light review of recent conversations
- **Monthly**: Comprehensive context audit
- **Quarterly**: Cross-reference validation and cleanup

**Ask user to establish their preferred cadence.**

---

## Examples

### Example 1: Extract Communication Preference

**Conversation snippet:**
```
User: "Can you avoid using emojis in your responses unless I explicitly request them?"
Claude: "I'll avoid using emojis in my responses unless you explicitly request them."
```

**Extraction:**
```yaml
---
title: Emoji Usage
created: 2026-01-25
updated: 2026-01-25
tags: [context, communication]
type: communication
---

# Emoji Usage

## Summary
Avoid using emojis in responses unless explicitly requested by user.

## Details
Do not include emojis in:
- Regular responses
- Code comments
- Commit messages
- File content
- Documentation

Only use emojis when:
- User explicitly requests: "use emojis" or "add emoji"
- Context clearly calls for it (e.g., user is using them)

## Examples

**Avoid** ✗:
```
✅ Updated the recipe! 🎉
```

**Preferred** ✓:
```
Updated the recipe successfully.
```

## Related Context
- [[context/communication/style-preferences]]
- [[context/communication/response-format]]

---

*Last updated: 2026-01-25*
```

### Example 2: Extract Decision

**Conversation snippet:**
```
User: "Let's use lowercase tags for all recipes to keep them consistent"
Claude: "I'll update all recipe tags to lowercase for consistency"
```

**Extraction:**
```yaml
---
title: Lowercase Tag Standardization
date: 2026-01-25
tags: [context, decision, recipes]
status: active
---

# Decision: Lowercase Tag Standardization

## Context
Recipe collection had mixed case tags (Dinner, dinner, DINNER) making filtering and organization difficult.

## Decision
All tags in recipe frontmatter must be lowercase.

## Rationale
1. **Consistency**: Easier to search and filter
2. **Simplicity**: One clear rule to follow
3. **Obsidian compatibility**: Tag queries are case-sensitive
4. **Scalability**: Works with hundreds of recipes

### Alternatives Considered
- **Title Case**: More readable but inconsistent in Obsidian
- **Mixed case**: User preference, but creates chaos
- **ALL CAPS**: Too aggressive, poor UX

## Implications
- All existing recipes need tag updates
- Recipe template must reflect this
- Recipe scraper skill must enforce this
- Documentation must be clear about this rule

## Related
- [[context/project/recipe-conventions]]
- [[recipes/_index/Recipe System Documentation]]

---

*Status: Active as of 2026-01-25*
```

### Example 3: Update Multiple Locations

**Scenario**: New convention that skills must read templates first

**Updates required:**

1. **context/project/vault-conventions.md** (update):
```markdown
# Template-First Architecture

All skills that create notes must read the relevant template first...
```

2. **context/_index.md** (update):
```markdown
- [[context/project/vault-conventions]] - Template-first architecture
```

3. **CLAUDE.md** (update):
```markdown
**How Skills Use Templates**:
1. The skill MUST read the template file first using the Read tool
```

4. **.claude/skills/recipe-scraper/SKILL.md** (verify):
```markdown
### Step 1: Read Template (REQUIRED)
```

5. **context/decisions/2026-01-25-template-first-skill-architecture.md** (new):
```markdown
# Decision: Template-First Skill Architecture

Document the decision and rationale...
```

### Example 4: Split Large Context File

**Scenario**: git-practices.md (467 lines) covers 3 distinct topics

**Splitting approach:**

1. **Create focused files:**
   - context/workflows/processes/git-commit-conventions.md (155 lines)
   - context/workflows/processes/git-workflow.md (124 lines)
   - context/workflows/processes/git-safety.md (133 lines)

2. **Convert to overview (82 lines):**
   - git-practices.md becomes navigation hub linking to focused guides

3. **Update indexes:**
   - context/_index.md: Add all 4 files (overview + 3 focused)
   - context/_loading-map.md: Map subtasks (creating commits → git-commit-conventions)

4. **Update cross-references:**
   - Search for references to git-practices throughout context/
   - Update to reference specific focused guide where appropriate

**Benefits:**
- Creating commits → load only git-commit-conventions + git-safety
- Creating PRs → load only git-workflow
- General git work → load git-practices overview

---

## Remember

✅ **DO:**
- Extract context progressively
- Use concrete examples
- Update all relevant locations
- Verify cross-references
- Keep context current
- Ask user when uncertain

❌ **DON'T:**
- Create context prematurely
- Duplicate across locations
- Leave broken references
- Skip validation checks
- Update without user review
- Mix private and public context
