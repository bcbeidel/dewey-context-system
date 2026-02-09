# Phase 1: Review & Extract

## Step 1: Understand Scope
Ask the user what to review:
- Recent conversation(s)
- Recent git changes
- Specific topic or area
- Full context audit
- **Session retrospective** (after significant work)

## Step 2: Identify Guidance Locations

**CRITICAL**: Verify directory structure exists before proceeding.

**Check infrastructure**:
```bash
# Verify context directory structure exists
ls -la context/

# If missing, scaffold core directories:
mkdir -p context/communication
mkdir -p context/project
mkdir -p context/workflows/processes
mkdir -p context/workflows/standards
mkdir -p context/workflows/retrospectives
mkdir -p context/decisions
mkdir -p context/private
```

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

**If context/_index.md missing**: Create basic index pointing to governance docs.

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

