# Phase 1: Review & Extract

## Step 0: Bootstrap Check (First Run Only)

**Before starting curation, check if context system exists.**

### Check for Context Directory

```bash
# Check if context folder exists
ls context/ 2>/dev/null
```

### If Missing: Offer Bootstrap

**If `context/` doesn't exist**, ask user:

> **Context system not found.** Would you like me to bootstrap it with best practices for using the distributed skills (auditor, researcher, planner, context-curator, agent development)?
>
> This will create:
> - Core domains (skills/, research/, auditing/, communication/, decisions/, processes/)
> - Best practice standards for each skill
> - Index files for navigation
> - Ready-to-use structure
>
> Create context system? (y/n)

### If Yes: Bootstrap Context System

**Create core domains**:
```bash
mkdir -p context/skills
mkdir -p context/research
mkdir -p context/auditing
mkdir -p context/communication
mkdir -p context/decisions
mkdir -p context/processes
mkdir -p context/context-system
```

**Copy best practices from bootstrap templates**:

```bash
# Find this skill's bootstrap directory
SKILL_DIR="$(dirname "${BASH_SOURCE[0]}")"
BOOTSTRAP_DIR="$SKILL_DIR/bootstrap"

# Copy all template files to user's context directory
cp -r "$BOOTSTRAP_DIR"/* context/

# Result: 27 files (19 content + 8 indexes) across 7 domains
```

**What gets copied** (27 files total):
- **Main index** (1): Context system overview with all domains
- **skills/** (4 + index): Progressive disclosure, execution standards, audit checklist, planning practices
- **research/** (7 + index): All 7 methodology standards (DSR, UX, Market, Mixed Methods, Case Study, Org Culture, Evidence Synthesis)
- **auditing/** (2 + index): ISO 19011 audit pattern, security validation
- **processes/** (1 + index): Planning best practices
- **communication/** (1 + index): Style preferences template
- **decisions/** (1 + index): ADR index and template
- **context-system/** (2 + index): System overview, loading map

**Create main index** (`context/_index.md`):
```bash
# Copy main index template if exists, or create from scratch
# List all 7 domains with descriptions
# Add quick start task mappings
# Include navigation guidance
```

**Output**: Context system ready for use

### If No: Skip Bootstrap

User can create their own structure or run `/context-curator` again later to bootstrap.

---

## Step 1: Understand Scope
Ask the user what to review:
- Recent conversation(s)
- Recent git changes
- Specific topic or area
- Full context audit
- **Session retrospective** (after significant work)

## Step 2: Identify Guidance Locations

**Read current state of all guidance locations**:

```bash
# Main instructions
Read: CLAUDE.md

# Context index (create if missing)
Read: context/_index.md

# Existing context files (check which exist)
Glob: context/**/*.md

# Skills
Glob: .claude/skills/*/SKILL.md

# Templates
Glob: extras/templates/*.md
```

## Step 3: Extract Context
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

