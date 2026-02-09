# Guidance Locations for Agent Consistency

This document maps all locations where Claude agents look for guidance and how the context-curator skill maintains consistency across them.

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
        │ - context-curator │  │ - Daily Note     │
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

**Structure** (As of 2026-02-08): 17 **concept-based** domains organized by primary topic

**Organization Principles**:
- ✅ **Flat structure**: Max 2 folder levels (context/domain/file.md)
- ✅ **Concept-based**: By topic (skills/, security/), not type (preferences/, standards/)
- ✅ **Discoverable**: Every domain has `_index.md` with "When to Use" guidance
- ✅ **LLM-friendly**: Clear entry points via [[_index|Context Index]]

**See**: [[decisions/2026-02-08-concept-based-context-organization]] for full rationale

---

#### Domain Reference

**Development & Security** (23 files):
- `skills/` - Skill development standards, auditing, refactoring
- `security/` - OWASP, OAuth, credentials, validation
- `python/` - Python coding standards, error handling
- `git/` - Git practices, commits, workflows, safety
- `auditing/` - Quality auditing processes

**Vault & Organization** (22 files):
- `obsidian/` - Vault conventions, recipes, frontmatter, tags
- `processes/` - Note creation, phased planning, team planning
- `documentation/` - Documentation standards and patterns
- `data/` - Data accuracy and validation standards

**Learning & Communication** (25 files):
- `communication/` - Communication style, coaching, critique (was: `context/communication/`)
- `research/` - Research gathering, analysis, synthesis
- `workshops/` - Workshop preparation, execution, facilitation
- `learning/` - Mental models, book notes, presentations
- `patterns/` - Reusable workflow patterns (audit, sync)

**Meta & History** (37 files):
- `decisions/` - Architectural Decision Records (was: `context/decisions/`)
- `retrospectives/` - Project retrospectives (was: `context/workflows/retrospectives/`)
- `context-system/` - Meta files, governance, loading map (was: various `context/*` files)

---

#### How to Add New Context

**Step 1**: Identify primary concept
- What's the main topic? (security, git, research, etc.)
- Does it fit an existing domain?

**Step 2**: Place in appropriate domain
- Add file to `context/{domain}/file.md`
- Follow max 2-level depth rule

**Step 3**: Update domain index
- Add to domain's `_index.md` file listing
- Update "Quick Links" if top priority

**Step 4**: Add to main index if needed
- Update [[_index|Context Index]] if significant

**Step 5**: Consider cross-references
- Link to related domains
- Update related `_index.md` files

---

#### 2a. Communication Domain (`context/communication/`)
How Claude should communicate with the user.

**When to Use**: Always load for communication style preferences

**Files**:
- `style-preferences.md` - Core communication preferences
- `clarity.md` - Simplicity, progressive disclosure
- `workflow-patterns.md` - Review-first, reflection
- `teaching-approach.md` - Educational explanations
- `critique-preference.md` - Constructive critique
- `response-format.md` - Output structure
- `terminology.md` - Project terms
- Plus: coaching context, audience adaptation

**Update when**:
- Communication preference stated
- Repeated correction made
- Style pattern observed

**See**: [[communication/_index|Communication Domain Index]]

---

#### 2b. Skills Domain (`context/skills/`)
Standards for Claude Code skill development (MOVED from `context/project/skill-*` and `context/workflows/standards/skill-*`).

**When to Use**: When developing, auditing, or refactoring skills

**Files**:
- `structure-standard.md` - SKILL.md template
- `execution-standards.md` - Quality requirements
- `refactoring-workflow.md` - Refactoring process
- `reference-organization.md` - Reference file patterns
- `audit-checklist.md` - Quality checklist
- Plus: audit implementation, standards sync

**Update when**:
- Skill standards change
- New quality requirements
- Refactoring patterns emerge

**See**: [[skills/_index|Skills Domain Index]]

---

#### 2c. Security Domain (`context/security/`)
Security best practices (MOVED from `context/project/security-*`).

**When to Use**: When implementing OAuth, managing credentials, or addressing OWASP concerns

**Files**:
- `best-practices-claude-skills.md` - Comprehensive OWASP Top 10 guide
- `auth-and-credentials.md` - OAuth 2.1, PKCE, credential storage
- `python-security-and-testing.md` - Input validation, testing
- `practices.md` - Core security requirements
- `errors-and-limits.md` - Error sanitization, rate limiting

**Update when**:
- OWASP standards updated
- Security vulnerability pattern identified
- New authentication method added

**See**: [[security/_index|Security Domain Index]]

---

#### 2d. Other Key Domains

**Obsidian** (`context/obsidian/`): Vault conventions, wikilinks, frontmatter, tags, recipes
**Git** (`context/git/`): Git practices, commits, safety, workflows
**Python** (`context/python/`): Python coding standards, error handling
**Processes** (`context/processes/`): Note creation, phased planning, team planning
**Learning** (`context/learning/`): Mental models, book notes, presentations
**Research** (`context/research/`): Research gathering, analysis, synthesis

**See**: [[_index|Context Index]] for complete domain listing with "When to Use" guidance

---

#### 2e. Decisions (`context/decisions/`)
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
- Related Context
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
- `context-curator/` - Extract and update context

**Update when**:
- Task workflow changes
- New requirements added
- Quality standards change
- Related context affects execution

**Reference context**:
```markdown
**See**: [[obsidian/recipe-conventions]] for current standards
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

- [[context-system/_index]] - Context system overview
- [[context-system/context-governance]] - Maintenance guidelines
- CLAUDE - Vault-wide instructions
- [SKILL.md](SKILL.md) - Full context-curator skill documentation
