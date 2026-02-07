# Guidance Locations for Agent Consistency

This document maps all locations where Claude agents look for guidance and how the context-update skill maintains consistency across them.

## Guidance Location Hierarchy

```
┌─────────────────────────────────────────────────────────────┐
│                         CLAUDE.md                           │
│                   (Vault-wide instructions)                 │
│                                                             │
│  - What is Claude Code?                                    │
│  - Obsidian vault structure                                │
│  - Markdown formatting rules                               │
│  - Core commands                                           │
│  - Custom skills overview                                  │
│  - Best practices                                          │
└─────────────────────────────────────────────────────────────┘
                              │
                              ↓
        ┌─────────────────────────────────────────┐
        │           context/ folder               │
        │     (Persistent categorized context)    │
        │                                         │
        │  communication/  - How to communicate   │
        │  project/        - Knowledge & standards│
        │  workflows/      - How to do tasks     │
        │  decisions/      - What & why          │
        │  private/        - Sensitive (ignored)  │
        └─────────────────────────────────────────┘
                              │
                    ┌─────────┴─────────┐
                    ↓                   ↓
        ┌──────────────────┐  ┌──────────────────┐
        │ .claude/skills/  │  │ extras/templates/│
        │ (Task workflows) │  │ (Note structures)│
        │                  │  │                  │
        │ - recipe-scraper │  │ - Recipe         │
        │ - book-notes     │  │ - Book Notes     │
        │ - mental-model   │  │ - Mental Model   │
        │ - context-update │  │ - Daily Note     │
        │ - daily-note     │  │ - Person         │
        └──────────────────┘  └──────────────────┘
```

## Location Details

### 1. CLAUDE.md
**File**: `/CLAUDE.md`
**Purpose**: Top-level project instructions read by all Claude instances
**Scope**: Vault-wide conventions and critical guidelines

**Contains**:
- Tool overview and capabilities
- Obsidian vault structure
- Markdown formatting rules (wikilinks, frontmatter, tags)
- Recipe format overview
- Mental model format overview
- Custom skills list
- Common workflows
- Best practices

**Update when**:
- Vault structure changes (new folder)
- Core conventions change (e.g., "always use lowercase tags")
- New major features added
- Critical workflows established

**DON'T update for**:
- Specific preferences → use `context/communication/`
- Detailed guidelines → use `context/project/`
- Temporary patterns → monitor first

### 2. context/ Folder
**Path**: `/context/`
**Purpose**: Persistent, categorized context for Claude alignment
**Scope**: All preferences, patterns, and knowledge

#### 2a. Communication (`context/communication/`)
How Claude should communicate with the user.

**Files** (follows overview + detail pattern):
- `style-preferences.md` - **Overview** linking to focused guides
- `communication-clarity.md` - Simplicity, progressive disclosure, accuracy
- `workflow-patterns.md` - Review-first, reflection, proposing changes
- `teaching-approach.md` - Explanation over automation, educational style
- `critique-preference.md` - Constructive critique guidelines
- `response-format.md` - Output structure, markdown usage
- `terminology.md` - Project-specific terms and definitions

**Update when**:
- Communication preference stated
- Repeated correction made
- Style pattern observed

**Note**: Large communication topics use overview + focused guide pattern for task-based loading

#### 2b. Project Knowledge (`context/project/`)
Project-specific conventions and standards.

**Files** (follows overview + detail pattern):
- `vault-conventions.md` - **Overview** of Obsidian conventions
- `obsidian-wikilinks.md` - Link syntax and conventions
- `obsidian-frontmatter.md` - YAML frontmatter standards
- `obsidian-tags.md` - Tag naming conventions (lowercase)
- `obsidian-features.md` - Callouts, embeds, block references
- `recipe-conventions.md` - Recipe organization standards
- `context-governance.md` - How to maintain context
- `context-archival-strategy.md` - Decision/retrospective archival process
- `data-accuracy-standards.md` - Source verification

**Update when**:
- New convention established
- Standard defined
- Architecture choice made
- Quality bar set

**Note**: vault-conventions split into focused Obsidian-specific files for better task-based loading

#### 2c. Workflows (`context/workflows/`)
Common patterns for executing tasks, organized by category.

**Structure**:
- `processes/` - Step-by-step workflows
- `standards/` - Quality checklists and validation criteria
- `retrospectives/` - Recent session learnings (5-7 most recent)
  - `archive/YYYY/` - Archived retrospectives

**Process Files** (follows overview + detail pattern):
- `note-creation.md` - How to create different note types
- `git-practices.md` - **Overview** of git conventions
- `git-commit-conventions.md` - Commit messages, co-authorship, HEREDOC
- `git-workflow.md` - Branches, PRs, remote operations
- `git-safety.md` - Safety rules, file staging, destructive commands
- `phased-execution.md` - Breaking work into phases

**Standards Files**:
- `book-notes-quality-checklist.md` - Book notes validation
- `mental-model-quality-checklist.md` - Mental model validation
- `skill-execution-standards.md` - Skill development standards

**Update when**:
- Workflow pattern emerges
- Process clarified
- Quality check defined
- Decision pattern identified

**Note**: git-practices split into focused files for task-based loading (commits vs PRs vs safety)

#### 2d. Decisions (`context/decisions/`)
Significant decisions with full context and rationale.

**Structure**:
- Active decisions: `YYYY-MM-DD-decision-name.md`
- Archived decisions: `archive/YYYY/YYYY-MM-DD-decision-name.md`

**Files**: `YYYY-MM-DD-decision-name.md` (active) or in `archive/YYYY/` subdirectory

**Format**:
```yaml
---
title: Decision Title
date: YYYY-MM-DD
tags: [context, decision]
status: active|superseded|deprecated
---

# Decision: Title

## Context
What led to this decision?

## Decision
What was decided?

## Rationale
Why? What factors were considered?

## Alternatives Considered
- Option A: Why not chosen
- Option B: Why not chosen

## Implications
What does this mean for future work?

## Related
- [[Related Context]]
```

**Update when**:
- Significant choice made
- Architecture decision
- Convention established
- Approach selected

#### 2e. Private Context (`context/private/`)
**Git-ignored** - sensitive information only.

**Structure mirrors public**:
- `personal/` - Work context, projects, goals
- `preferences/` - Sensitive preferences
- `decisions/` - Private decisions

**Update when**:
- Personal information involved
- Work-related confidential info
- Private goals/plans discussed
- Sensitive preferences stated

### 3. Skills (`.claude/skills/`)
**Path**: `/.claude/skills/[skill-name]/SKILL.md`
**Purpose**: Domain-specific task workflows and instructions
**Scope**: How to execute specific types of tasks

**Structure**:
```
.claude/skills/[skill-name]/
├── SKILL.md              # Main skill instructions
├── QUICK-REFERENCE.md    # (optional) Usage guide
└── [supporting-files]    # Templates, examples, etc.
```

**Current skills**:
- `recipe-scraper/` - Scrape and format recipes
- `book-notes/` - Create book notes
- `mental-model/` - Create mental model notes
- `context-update/` - Extract and update context

**Update when**:
- Task workflow changes
- New requirements added
- Quality standards change
- Related context affects execution

**Reference context**:
```markdown
**See**: [[context/project/recipe-conventions]] for current standards
```

### 4. Commands (`.claude/commands/`)
**Path**: `/.claude/commands/[command-name].md`
**Purpose**: Simple, single-file commands
**Scope**: Straightforward tasks without complex workflows

**Current commands**:
- `daily-note.md` - Create daily journal entry

**Update when**:
- Command workflow changes
- Output format evolves
- Related context established

### 5. Templates (`extras/templates/`)
**Path**: `/extras/templates/Template, [Type].md`
**Purpose**: Canonical structure for each note type
**Scope**: Frontmatter, structure, format for specific note types

**Current templates**:
- `Template, Recipe.md` - Recipe format
- `Template, Book Notes.md` - Book notes format
- `Template, Mental Model.md` - Mental model format
- `Template, Daily Note.md` - Daily journal format
- `Template, Person.md` - People notes format
- `Template, Employee Review.md` - Review format

**Update when**:
- Frontmatter fields change
- Structure evolves
- New conventions added
- Format requirements change

**Critical**: Skills MUST read templates before creating notes!

## Consistency Validation Checklist

When updating context, verify consistency across:

### Level 1: Context System
- [ ] Context file created/updated
- [ ] `context/_index.md` updated with link
- [ ] Cross-references added to related context
- [ ] Private context properly separated if needed

### Level 2: Documentation
- [ ] CLAUDE.md updated if vault-wide change
- [ ] No conflicting guidance in CLAUDE.md
- [ ] Examples remain accurate

### Level 3: Skills & Commands
- [ ] Affected skills reference new context
- [ ] Skill workflows still valid
- [ ] Commands updated if affected
- [ ] No conflicting instructions

### Level 4: Templates
- [ ] Templates match current conventions
- [ ] Frontmatter fields consistent
- [ ] Structure follows standards
- [ ] Examples still accurate

### Level 5: Cross-References
- [ ] All wikilinks valid (no broken links)
- [ ] Related context properly linked
- [ ] Skills link to relevant context
- [ ] CLAUDE.md links to context for details

## Update Flow

```
┌──────────────────────────────────────────────┐
│ 1. Extract context from conversation/changes │
└──────────────┬───────────────────────────────┘
               │
               ↓
┌──────────────────────────────────────────────┐
│ 2. Categorize (communication/project/etc)    │
└──────────────┬───────────────────────────────┘
               │
               ↓
┌──────────────────────────────────────────────┐
│ 3. Create/update context files              │
└──────────────┬───────────────────────────────┘
               │
               ↓
┌──────────────────────────────────────────────┐
│ 4. Update context/_index.md                 │
└──────────────┬───────────────────────────────┘
               │
               ↓
┌──────────────────────────────────────────────┐
│ 5. Check if CLAUDE.md needs update          │
│    (vault-wide changes only)                │
└──────────────┬───────────────────────────────┘
               │
               ↓
┌──────────────────────────────────────────────┐
│ 6. Check if skills need updates             │
│    (workflow changes, new context)          │
└──────────────┬───────────────────────────────┘
               │
               ↓
┌──────────────────────────────────────────────┐
│ 7. Check if templates need updates          │
│    (structure/field changes)                │
└──────────────┬───────────────────────────────┘
               │
               ↓
┌──────────────────────────────────────────────┐
│ 8. Validate consistency across all         │
└──────────────┬───────────────────────────────┘
               │
               ↓
┌──────────────────────────────────────────────┐
│ 9. Present summary to user for review      │
└──────────────┬───────────────────────────────┘
               │
               ↓
┌──────────────────────────────────────────────┐
│ 10. Commit changes                          │
└──────────────────────────────────────────────┘
```

## Examples of Multi-Location Updates

### Example 1: New Recipe Convention
**Context**: Decided to use lowercase tags for all recipes

**Updates**:
1. ✅ `context/decisions/2026-01-25-lowercase-tag-standardization.md` - Document decision
2. ✅ `context/project/recipe-conventions.md` - Add to conventions
3. ✅ `context/_index.md` - Add links to both
4. ✅ `CLAUDE.md` - Update recipe format section
5. ✅ `.claude/skills/recipe-scraper/SKILL.md` - Update tag guidelines
6. ✅ `extras/templates/Template, Recipe.md` - Update example tags

### Example 2: Communication Preference
**Context**: User prefers no emojis unless requested

**Updates**:
1. ✅ `context/communication/communication-clarity.md` - Document preference (or create new file)
2. ✅ `context/communication/style-preferences.md` - Link to focused guide if applicable
3. ✅ `context/_index.md` - Add link
4. ❌ CLAUDE.md - No update (not vault-wide)
5. ❌ Skills - No update (doesn't affect workflows)
6. ❌ Templates - No update (doesn't affect structure)

### Example 3: New Workflow Pattern
**Context**: Always use phased execution for complex tasks

**Updates**:
1. ✅ `context/workflows/processes/phased-execution.md` - Document pattern
2. ✅ `context/_index.md` - Add link
3. ✅ `context/_loading-map.md` - Map to relevant tasks
4. ✅ `CLAUDE.md` - Add to "Common Workflows" section
5. ❌ Skills - No update (general pattern, not skill-specific)
6. ❌ Templates - No update (doesn't affect note structure)

## Maintenance

**Regular checks**:
- After major work: Extract immediately
- Weekly: Light context review
- Monthly: Comprehensive validation
- Quarterly: Full consistency audit

**Validation frequency**:
- Cross-references: Every update
- CLAUDE.md alignment: Monthly
- Skills consistency: After skill updates
- Template accuracy: After template changes

## See Also

- [[context/_index]] - Context system overview
- [[context/project/context-governance]] - Maintenance guidelines
- [[CLAUDE.md]] - Vault-wide instructions
- [SKILL.md](SKILL.md) - Full context-update skill documentation
