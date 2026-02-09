---
name: planner
description: "Create structured, evidence-based plans for multi-step tasks with hierarchical decomposition, quality validation, and human approval gates"
allowed-tools: Read, Write, Edit, Glob, Grep, AskUserQuestion
version: 1.0.0
---

# Planner

**Purpose**: Create structured, evidence-based plans for multi-step tasks that work consistently across different LLMs. Plans are stored in markdown format with YAML frontmatter in the project directory.

**When to Use**:
- Multi-step tasks (3+ distinct steps)
- Complex problems requiring decomposition
- Long-horizon work (hours to days)
- Tasks where you want a clear roadmap before execution
- When you need a plan that can be reviewed, edited, and resumed

**What This Skill Does**:
1. **Gathers requirements** through interactive questions
2. **Explores context** (existing code, constraints, resources)
3. **Creates hierarchical plan** (Goal → Milestones → Tasks → Actions)
4. **Validates quality** across 5 dimensions
5. **Saves plan** to `/projects/[project-name]/plans/`
6. **Provides execution guidance** for next steps

**What This Skill Doesn't Do**:
- Execute the plan (separate phase)
- Replace quick decision-making for simple tasks
- Guarantee success (plans are guides, not guarantees)
- Work without user input (requires engagement)

**Evidence-Based**: Grounded in systematic review of agentic planning research (2024-2026, 12 sources including academic papers and industry practices).

---

## Quick Start

### When Should You Use /planner?

**✅ Use /planner for**:
- "Add OAuth2 authentication to our API" (multi-step feature)
- "Refactor the database layer to use repository pattern" (complex refactor)
- "Debug intermittent production errors" (uncertain, needs structure)
- "Migrate from monolith to microservices" (long-horizon project)

**❌ Skip /planner for**:
- "Fix typo in README" (single step)
- "Add console.log for debugging" (trivial)
- "Emergency hotfix for critical bug" (act fast, plan later)
- "Run existing tests" (routine task)

**Rule of thumb**: If it takes <30 minutes and has <3 steps, just do it. Otherwise, plan it.

---

### First Time Using?

**Quick example**:
```
> /planner

# Skill will ask:
- What's your goal?
- What project is this for?
- Any constraints or deadlines?
- What does success look like?

# Then it will:
- Explore your codebase/context
- Create a structured plan
- Validate quality
- Save to /projects/[name]/plans/
- Give you next steps
```

**Time investment**: 30-55 minutes for planning, saves hours during execution.

---

## Three-Phase Workflow

### Phase 1: Setup & Discovery (10-15 minutes)

**Goal**: Understand what you want to achieve and the context

**What happens**:
1. **Interactive Q&A**: Skill asks questions to clarify goal
2. **Context exploration**: Reviews existing code, files, constraints
3. **Tool inventory**: Validates what's actually available
4. **Strategy selection**: Chooses planning approach based on task nature

**Your role**: Answer questions, provide context, clarify requirements

**Output**: Clear goal, constraints, available tools, chosen strategy

→ **Details**: See [[phase-1-setup-discovery]]

---

### Phase 2: Plan Creation (15-30 minutes)

**Goal**: Create detailed, validated plan

**What happens**:
1. **Hierarchical decomposition**: Break goal into milestones → tasks → actions
2. **Dependency mapping**: Identify sequential vs. parallel work
3. **Risk identification**: What could go wrong, how to mitigate
4. **Quality validation**: Check completeness, feasibility, efficiency, maintainability, adaptability
5. **User review**: Present plan, get feedback, refine

**Your role**: Review plan summary, provide feedback, approve approach

**Output**: Approved plan ready for execution

→ **Details**: See [[phase-2-plan-creation]]

---

### Phase 3: Plan Finalization (5-10 minutes)

**Goal**: Save plan and prepare for execution

**What happens**:
1. **Save plan**: Write to `/projects/[project-name]/plans/[plan-name]-[date].md`
2. **Link resources**: Connect to related context, code, documentation
3. **Execution guidance**: Provide clear next steps
4. **Optional setup**: Create git branch, set reminders

**Your role**: Review saved plan location, prepare to execute

**Output**: Plan file saved, ready to start work

→ **Details**: See [[phase-3-finalization]]

---

## Planning Strategies (Auto-Selected)

The skill automatically chooses the best strategy based on your task:

### 1. Decompose-First (Default)

**Best for**: Well-defined problems with known requirements

**How it works**: Fully decompose goal into all steps upfront before any execution

**Example tasks**:
- "Add OAuth2 authentication"
- "Refactor to use repository pattern"
- "Implement payment processing"

**Pros**: Predictable, complete picture upfront
**Cons**: Less adaptive to surprises

---

### 2. Interleaved

**Best for**: Exploratory tasks with uncertain requirements

**How it works**: Partial decomposition → execute → discover → replan → repeat

**Example tasks**:
- "Debug intermittent API timeouts"
- "Optimize slow database queries"
- "Research best architecture for new feature"

**Pros**: Adaptive, lower upfront cost
**Cons**: Less predictable timeline

---

### 3. Milestone-Based

**Best for**: Long-horizon tasks (multi-day or multi-week)

**How it works**: High-level milestones with checkpoint reviews, detailed planning per milestone

**Example tasks**:
- "Migrate monolith to microservices"
- "Redesign entire authentication system"
- "Build new admin dashboard from scratch"

**Pros**: Manageable chunks, replanning checkpoints
**Cons**: More overhead for coordination

**Note**: Skill will ask about task nature if strategy unclear. You can also force a strategy with `--strategy [name]`.

---

## Plan Storage & Format

### Where Plans Are Saved

```
/projects/[project-name]/plans/[plan-name]-[YYYY-MM-DD].md
```

**Examples**:
```
/projects/authentication-system/
  plans/
    oauth2-migration-2026-02-08.md
    replan-after-testing-2026-02-10.md

/projects/api-refactor/
  plans/
    initial-design-2026-02-08.md
```

**Benefits**:
- ✅ Version controlled (git)
- ✅ Human browsable (filesystem)
- ✅ Project-specific organization
- ✅ Date-based history
- ✅ LLM can easily locate

---

### Plan Format

**Markdown + YAML frontmatter** (evidence: 10-15% more token-efficient than JSON, human-readable)

**Structure**:
```markdown
---
title: "OAuth2 Migration Plan"
project: "authentication-system"
status: approved
goal: "Migrate from session auth to OAuth2"
---

# OAuth2 Migration Plan

## Goal
[Clear success criteria]

## Milestones
### Milestone 1: Design OAuth2 Flow
#### Task 1.1: Research provider options
**Actions**:
1. Review Auth0 vs. Okta documentation
2. Compare pricing and features
3. Document recommendation

## Execution Log
[Track actual vs. planned progress]
```

→ **Full template**: See [[plan-template]]

---

## Quality Validation (Built-In)

Every plan is validated across **5 dimensions** (evidence-based from systematic review):

### 1. Completeness
✓ All steps defined
✓ Prerequisites identified
✓ Success criteria clear
✓ Dependencies mapped

### 2. Feasibility
✓ No hallucinated tools
✓ Constraints respected
✓ Resources available
✓ Actions achievable

### 3. Efficiency
✓ Minimal redundancy
✓ Optimal action count
✓ Parallel opportunities identified
✓ Right tools for each task

### 4. Maintainability
✓ Human-readable format
✓ Clear structure
✓ Documented rationale
✓ Resumable

### 5. Adaptability
✓ Replanning checkpoints
✓ Risk mitigation defined
✓ Error recovery specified
✓ Flexible to changes

**Validation happens automatically** during Phase 2. Failed checks will prompt for corrections.

→ **Detailed criteria**: See [[quality-validation]]

---

## Command-Line Options

### Basic Usage
```bash
/planner                    # Interactive mode (recommended)
```

### With Pre-Specified Info
```bash
/planner --project auth                      # Skip project name question
/planner --goal "migrate to oauth2"          # Pre-specify goal
/planner --project auth --goal "add oauth2"  # Both
```

### Advanced Options
```bash
/planner --strategy decompose    # Force specific strategy
/planner --strategy interleaved  # Force exploratory approach
/planner --strategy milestone    # Force milestone-based

/planner --quick                 # Skip some validation (faster, riskier)
/planner --verbose               # Show detailed reasoning
/planner --dry-run               # Preview without saving

/planner --resume latest         # Resume previous planning session
```

---

## Integration with Other Skills

### Before Planning
- **`/systematic-review`**: Research best practices for your domain
- **`/auditor`**: Review existing code to inform plan
- **`/context-curator`**: Load relevant context before planning

### During Planning
- **`/compare`**: Compare alternative approaches using decision matrix
- **`/diagram`**: Visualize plan structure or dependencies

### After Planning
- **`/auditor`**: Validate plan quality against standards
- **`/context-curator`**: Extract learnings from planning process

### During Execution
- Update plan's execution log as you work
- Reference plan file when executing tasks
- `/planner --replan` when significant adjustments needed

---

## Troubleshooting

**Common issues** (see [[examples]] for detailed solutions):
- Plan too long → Use milestone-based strategy
- Missing tools → Validate tool inventory in Phase 1
- Plan diverging → Use interleaved strategy for exploratory tasks
- Can't find plan → Check `/projects/[project-name]/plans/`

---

## Limitations

**Not for**: Simple tasks (<30 min), emergencies, routine patterns
**Requires**: Multi-step tasks (3+ steps), 20-60 min planning time, user engagement
**Note**: LLM quality varies, very long plans may exceed context (use milestone strategy)

---

## Examples

See [[examples]] for detailed walkthroughs of:

1. **Feature Implementation**: "Add OAuth2 authentication" (decompose-first strategy)
2. **Debugging**: "Fix intermittent API timeouts" (interleaved strategy)
3. **Large Project**: "Refactor to microservices" (milestone-based strategy)

Each example includes:
- Full planning session transcript
- Complete plan file
- Execution notes
- Lessons learned

---

## Reference Documentation

### Detailed Guides
- [[phase-1-setup-discovery]] - Requirement gathering, context exploration
- [[phase-2-plan-creation]] - Decomposition, validation, user review
- [[phase-3-finalization]] - Saving, linking, execution guidance

### Supporting Documents
- [[quality-validation]] - Detailed quality criteria and validation procedures
- [[plan-template]] - Complete plan template with all sections
- [[examples]] - Real-world scenarios and complete walkthroughs

### Related Context
- [[../../context/skills/agentic-planning-best-practices]] - Evidence-based best practices
- [[../../projects/agentic-planning-skill/systematic-review-summary]] - Research synthesis

---

## Success Criteria

**Success**: Plan saved to `/projects/[name]/plans/`, human-readable, all validations passed, ready to execute
**Iterate if**: Too vague (add detail), too rigid (use interleaved), too long (use milestone-based)

---

## Version History

**v1.0.0** (2026-02-08):
- Initial release
- Evidence-based design from systematic review
- Three planning strategies
- Five-dimension quality validation
- Comprehensive template structure

---

**Created**: 2026-02-08
**Based On**: Systematic Review of Agentic Planning Best Practices (2024-2026)
**Evidence**: 12 sources (7 academic, 5 industry)
**Maintenance**: Review annually or when significant new research emerges
