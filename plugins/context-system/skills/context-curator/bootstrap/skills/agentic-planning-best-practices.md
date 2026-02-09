---
title: Agentic Planning Best Practices
date: 2026-02-08
type: best-practices
domain: skills
source: systematic-review-agentic-planning-2026
tags: [planning, agentic-systems, llm, best-practices]
---

# Agentic Planning Best Practices

**Purpose**: Evidence-based guidelines for planning in LLM-based agentic systems, synthesized from academic research and industry practices (2024-2026).

**Source**: [[../projects/agentic-planning-skill/systematic-review-protocol|Systematic Review: Agentic Planning (2026-02-08)]]

**When to Use**: When designing or implementing planning capabilities in LLM-based agents, particularly for multi-step tasks requiring decomposition, execution, and adaptation.

---

## Core Principles

### 1. Plan-Execute Separation

**Principle**: Separate strategic planning (thinking) from tactical execution (acting).

**Evidence**: Research shows plan-then-execute patterns improve predictability, cost-efficiency, and reasoning quality over reactive patterns like ReAct (arXiv:2509.08646).

**Implementation**:
- **Planning Phase**: Read-only exploration, requirement gathering, strategy formation
- **Execution Phase**: Action-taking, tool use, state modification
- **Boundary**: Clear approval gate between planning and execution

**Example**:
- Claude Code Plan Mode: User approves plan before execution begins
- LangGraph: Separate planner and executor nodes in workflow graph

**Trade-offs**:
- ✅ More predictable (full plan visible upfront)
- ✅ Cost-efficient (reduce trial-and-error)
- ❌ Less adaptive (requires replanning for changes)

---

### 2. Hierarchical Decomposition

**Principle**: Break complex goals into multiple levels of abstraction.

**Evidence**: GoalAct framework showed 12.22% improvement using hierarchical execution with high-level skills (arXiv:2504.16563).

**Hierarchy Levels**:
1. **Goal**: Overall objective (user-defined)
2. **Milestones**: Major checkpoints (coarse-grained)
3. **Tasks**: Concrete work units (medium-grained)
4. **Actions**: Individual tool calls or steps (fine-grained)

**Decomposition Strategies**:

**Decompose-First** (static):
- Fully decompose before taking action
- Best for: Well-defined problems, known constraints
- Example: "Build authentication system" → [design schema, implement routes, add tests, document]

**Interleaved** (adaptive):
- Partial decomposition, execute, discover more
- Best for: Exploratory tasks, uncertain requirements
- Example: "Debug intermittent error" → [reproduce, hypothesis, test, refine]

**Trade-offs**:
- **Decompose-first**: More upfront planning, better predictability
- **Interleaved**: Lower initial cost, more adaptive

**Guideline**: Use decompose-first by default; switch to interleaved when requirements unclear.

---

### 3. Adaptive Replanning

**Principle**: Plans are living documents that evolve based on execution results.

**Evidence**: Long-horizon tasks benefit from iterative refinement and milestone-based replanning (arXiv:2503.09572). GoalAct's "continuously updated global plan" outperforms static planning.

**Replanning Triggers**:
- **Failure**: Step execution fails (tool error, prerequisite missing)
- **Surprise**: Unexpected state encountered
- **Opportunity**: Discovered shortcut or optimization
- **Requirement change**: User updates goals

**Replanning Patterns**:
1. **Checkpoint-based**: Re-plan at milestone boundaries
2. **Error-triggered**: Re-plan when step fails
3. **Continuous**: Update plan after every step (GoalAct style)

**Implementation**:
- Save original plan (baseline)
- Track deviations (plan vs. actual)
- Document why replanning occurred
- Get user approval for significant changes

---

### 4. Human-in-the-Loop Integration

**Principle**: Critical decisions require human approval.

**Evidence**: LangGraph persistence architecture specifically enables human-in-loop workflows through checkpointing. Claude Code Plan Mode requires explicit user approval before execution.

**Approval Gates**:
1. **Plan approval**: Before execution begins
2. **High-risk actions**: Destructive operations (delete, overwrite)
3. **Replan approval**: Significant plan changes
4. **Milestone review**: Periodic progress checks

**Interactive Mechanisms**:
- **AskUserQuestion**: Gather requirements during planning (Claude Code pattern)
- **Editable plans**: User can modify plan file directly (Ctrl+G in Claude Code)
- **Checkpoints**: Review state at any step (LangGraph pattern)

**Guidelines**:
- Default to asking (err on side of caution)
- Make approval requests specific (what, why, risk)
- Provide context for decisions

---

## Storage & Format Standards

### Storage Location

**Recommendation**: `/projects/[project-name]/plans/[plan-name].md`

**Rationale**:
- Centralized project-specific location
- Version-controllable (git)
- Human-browsable (filesystem)
- LLM-accessible (predictable path)

**Structure**:
```
/projects/
  authentication-system/
    plans/
      initial-design-2026-02-08.md
      replan-after-api-change-2026-02-09.md
    context/
      requirements.md
      decisions.md
  feature-x/
    plans/
      ...
```

**Alternative Patterns**:
- Claude Code: `.claude/plans/` (tool-specific)
- LangGraph: Checkpoint stores (programmatic)
- Hybrid: Plans in `/projects/`, execution state in tool-specific location

---

### Format: Markdown with YAML Frontmatter

**Recommendation**: Markdown body + YAML frontmatter

**Evidence**:
- Markdown is most token-efficient format (10-15% savings vs. JSON)
- LLMs produce higher quality output in markdown vs. structured formats
- Human-readable and editable
- Supports both prose and structure

**Template Structure**:

```markdown
---
title: "[Descriptive Plan Name]"
project: "[project-name]"
created: YYYY-MM-DD
updated: YYYY-MM-DD
status: draft | approved | in-progress | completed | archived
version: 1.0
goal: "[One-sentence goal]"
estimated_duration: "[hours/days]"
tags: [planning, feature-x, ...]
---

# [Plan Name]

## Goal

[Clear statement of what success looks like]

## Context

[Relevant background, requirements, constraints]

## Milestones

### Milestone 1: [Name]
**Goal**: [What this achieves]
**Estimated effort**: [time estimate]
**Success criteria**: [How to verify]

#### Tasks
1. **[Task name]**: [Description]
   - Actions: [Specific steps]
   - Tools: [Tools needed]
   - Prerequisites: [Dependencies]

2. **[Task name]**: [Description]
   ...

### Milestone 2: [Name]
...

## Dependencies

- [ ] Dependency 1
- [ ] Dependency 2

## Risks

- **Risk**: [Description]
  - **Mitigation**: [How to address]

## Approval

- [ ] Plan reviewed
- [ ] Approved by: [name/date]
- [ ] Ready for execution

## Execution Log

[Track progress, deviations, replanning decisions]

### [Date] - Milestone 1 Started
- Started task 1
- Note: [any deviations or discoveries]

### [Date] - Replan Required
- Reason: [Why replanning]
- Changes: [What changed]
- Approved by: [name]
```

**Rationale**:
- **Frontmatter**: Structured metadata for programmatic access
- **Markdown body**: Human-readable plan content, LLM-friendly generation
- **Sections**: Standard structure enables parsing, validation
- **Checkboxes**: Track progress inline
- **Execution log**: Document actual vs. planned

---

## Execution Patterns

### Sequential Execution (Default)

**Pattern**: Execute plan steps in order, one at a time.

**When to use**:
- Dependencies between steps
- Debugging required (easier with sequential)
- Unknown execution time per step

**Example**:
```
1. Read current authentication code
2. Design new schema (depends on step 1)
3. Implement migration (depends on step 2)
4. Test migration (depends on step 3)
```

**Implementation**:
- Execute step N
- Verify success
- Proceed to step N+1

---

### Parallel Execution (Optimization)

**Pattern**: Execute independent steps concurrently.

**When to use**:
- Steps have no dependencies
- Time-critical tasks
- Resource utilization optimization

**Example**:
```
Parallel group:
  - Write unit tests (independent)
  - Update documentation (independent)
  - Prepare deployment config (independent)
```

**Implementation**:
- Identify independent tasks (dependency analysis)
- Execute in parallel (async agents, threads)
- Synchronize at milestone boundary

**Guideline**: Default to sequential, parallelize only when clearly independent.

---

### Checkpoint-Based Replanning

**Pattern**: Re-evaluate plan at milestone boundaries.

**When to use**:
- Long-horizon tasks (multi-hour or multi-day)
- Exploratory work (uncertain requirements)
- High-risk changes

**Implementation**:
1. Complete milestone
2. Review results vs. expectations
3. Assess remaining plan validity
4. Replan if needed (with user approval)
5. Continue to next milestone

**Example**:
```
Milestone 1: Database schema design [COMPLETE]
→ Review: Schema more complex than expected
→ Replan: Add migration testing milestone
→ Approved: Yes
→ Continue with updated plan

Milestone 2: Implement migration [IN PROGRESS]
...
```

---

## Quality Criteria

### Completeness

**Definition**: Plan includes all necessary steps to achieve goal.

**Checklist**:
- [ ] Goal clearly stated
- [ ] All milestones defined
- [ ] Tasks decomposed to actionable steps
- [ ] Prerequisites identified
- [ ] Success criteria specified
- [ ] Dependencies mapped

**Validation**:
- Trace: Can you reach goal from current state following plan?
- Coverage: Are all aspects of goal addressed?
- Preconditions: Are all prerequisites available?

---

### Feasibility

**Definition**: Plan steps are achievable with available tools and resources.

**Checklist**:
- [ ] All required tools available
- [ ] No hallucinated capabilities (grounded in reality)
- [ ] Constraints respected (time, resources, permissions)
- [ ] Dependencies satisfied
- [ ] Risks identified and mitigated

**Validation**:
- Tool check: Verify each tool referenced exists
- Constraint check: Verify resource availability
- Reality check: Can this actually be done?

**Common Issues**:
- Hallucinated tools (agent invents non-existent capabilities)
- Unrealistic timelines
- Missing permissions

**Mitigation**:
- Explicit tool inventory (what's available?)
- Constraint declaration (what's not allowed?)
- Validation step (sanity check plan before execution)

---

### Efficiency

**Definition**: Plan minimizes redundant work and optimizes resource use.

**Metrics**:
- **Action count**: Fewest steps to goal
- **Redundancy**: No duplicate work
- **Parallelization**: Independent tasks identified
- **Tool selection**: Appropriate tool for each task

**Optimization**:
- Remove redundant steps
- Combine related actions
- Identify parallel opportunities
- Use most efficient tools

**Trade-off**: Efficiency vs. safety (sometimes redundancy = validation)

---

### Maintainability

**Definition**: Plan is understandable, editable, and resumable.

**Checklist**:
- [ ] Human-readable format
- [ ] Clear structure (consistent sections)
- [ ] Inline documentation (why decisions made)
- [ ] Version tracked (git-compatible)
- [ ] Resumable (can pick up where left off)

**Guidelines**:
- Use consistent naming (plans, milestones, tasks)
- Document rationale (why this approach?)
- Track changes (execution log)
- Enable search (tags, frontmatter)

---

### Adaptability

**Definition**: Plan can evolve in response to execution results.

**Checklist**:
- [ ] Milestones allow replanning checkpoints
- [ ] Risks identified with mitigation
- [ ] Error recovery specified
- [ ] Fallback options documented

**Replanning Indicators**:
- Execution time vastly different from estimate
- Prerequisite missing or blocked
- Unexpected state discovered
- Requirement changed

**Implementation**:
- Document assumptions (what might change?)
- Identify decision points (where to re-evaluate?)
- Specify triggers (when to replan?)

---

## Common Pitfalls & Mitigations

### Pitfall 1: Plan Drift

**Problem**: Execution diverges from plan without updating plan document.

**Symptoms**:
- Plan says "do X", but doing "Y"
- Plan no longer reflects reality
- Hard to resume or review progress

**Mitigation**:
- **Execution log**: Document all deviations in plan file
- **Checkpoint reviews**: Regularly compare planned vs. actual
- **Update plan**: Replan formally when drift is significant

**Example**:
```markdown
## Execution Log

### 2026-02-08 - Deviation from Plan
**Planned**: Implement OAuth2
**Actual**: Discovered existing OAuth1 requires migration first
**Decision**: Add migration milestone before OAuth2 implementation
**Status**: Plan updated, user approved
```

---

### Pitfall 2: Context Window Overflow

**Problem**: Long plans exceed LLM context limits.

**Symptoms**:
- Plan truncated mid-execution
- Loss of early context
- Repeated questions about previous decisions

**Mitigation**:
- **Hierarchical plans**: Break into milestone-level plans
- **Context compression**: Summarize completed milestones
- **Memory/RAG**: Store plan externally, retrieve relevant sections
- **Checkpoint-based**: Reset context at milestone boundaries

**Pattern**:
```
/projects/[project]/plans/
  main-plan.md (high-level milestones only)
  milestone-1-detailed.md (detailed task plan)
  milestone-2-detailed.md (detailed task plan)
```

---

### Pitfall 3: Hallucinated Tools/Capabilities

**Problem**: Plan includes non-existent tools or capabilities.

**Symptoms**:
- "Use tool X" but tool X doesn't exist
- "Call API Y" but no API access configured
- Impossible actions

**Mitigation**:
- **Tool inventory**: Declare available tools upfront
- **Validation step**: Check plan feasibility before approval
- **Grounding**: Reference actual tool documentation
- **Constraints**: Explicitly state limitations

**Example Validation**:
```markdown
## Available Tools (Validated)
- ✅ Git (read, commit, push)
- ✅ File operations (read, write, edit)
- ✅ Bash (command execution)
- ❌ Database access (not configured)
- ❌ External API (no credentials)

## Plan Validation
- [x] All tools referenced are available
- [x] No hallucinated capabilities
- [x] Constraints respected
```

---

### Pitfall 4: Over-Planning

**Problem**: Spending too much time planning for simple tasks.

**Symptoms**:
- 30-minute plan for 5-minute task
- Analysis paralysis
- Diminishing returns on planning effort

**Mitigation**:
- **Complexity threshold**: Skip formal planning for simple tasks (<30 minutes)
- **Progressive planning**: Start with high-level, elaborate as needed
- **Time-boxing**: Limit planning phase (e.g., 20% of estimated total time)

**Guideline**:
- Simple task: Just do it (no formal plan)
- Medium task: Outline milestones (lightweight plan)
- Complex task: Full planning process (formal plan)

---

### Pitfall 5: Ignoring Human Expertise

**Problem**: Agent proceeds with plan despite user concerns or better knowledge.

**Symptoms**:
- User says "this won't work" but agent insists
- Plan ignores domain constraints user mentioned
- Wasted effort on predetermined failure

**Mitigation**:
- **Approval gates**: Require explicit user approval
- **Editable plans**: Let user modify plan directly
- **Interactive requirements**: Use AskUserQuestion liberally
- **Iterative refinement**: Multiple review cycles before execution

---

## Integration Patterns

### With Existing Code

**Pattern**: Plans reference and interact with existing codebase.

**Best Practices**:
- **Discovery phase**: Explore existing code before planning
- **Respect patterns**: Follow existing conventions
- **Minimal disruption**: Prefer incremental changes
- **Test integration**: Validate changes work with existing code

**Example**:
```markdown
## Context: Existing Authentication System

**Current Implementation**:
- Uses session-based auth (Express sessions)
- User model in models/User.js
- Auth routes in routes/auth.js
- Middleware in middleware/auth.js

**Plan Constraints**:
- Must maintain backward compatibility
- Follow existing error handling pattern
- Reuse existing User model
- Update tests in test/auth.test.js
```

---

### With Human Workflows

**Pattern**: Plans integrate into human development workflows (git, PRs, code review).

**Best Practices**:
- **Git integration**: Commit plan files, track changes
- **Branch per plan**: Separate branch for each major plan
- **PR linking**: Link plans to pull requests
- **Review process**: Plans reviewed like code

**Example Workflow**:
```
1. Create plan: /projects/feature-x/plans/initial-2026-02-08.md
2. User reviews and approves plan
3. Create branch: feature-x-implementation
4. Execute plan (commit work referencing plan)
5. Create PR (include plan in description)
6. Code review (verify implementation matches plan)
7. Merge and archive plan
```

---

### With Other Skills

**Pattern**: Planning skill coordinates with other specialized skills.

**Integration Points**:
- **Research skills**: Gather information before planning
- **Audit skills**: Validate plan quality
- **Execution skills**: Carry out plan steps
- **Review skills**: Assess results vs. plan

**Example**:
```
Workflow:
1. /research → Gather context
2. /plan → Create structured plan
3. [Execution phase]
4. /audit → Verify plan completion
5. /context-update → Extract learnings
```

---

## LLM-Specific Considerations

### Cross-LLM Portability

**Goal**: Plans that work across different LLMs (Claude, GPT, etc.).

**Guidelines**:
- **Standard format**: Use markdown + frontmatter (widely supported)
- **Clear instructions**: Don't rely on LLM-specific features
- **Explicit tool names**: Use common tool names ("file_read" not "Read")
- **Human-readable**: Assume human might execute plan manually

**Testing**: Validate plan with multiple LLMs before declaring portable.

---

### Token Efficiency

**Consideration**: Long plans consume significant tokens.

**Optimization Strategies**:
- **Markdown over JSON**: 10-15% token savings
- **Hierarchical structure**: Load only relevant sections
- **Summarization**: Compress completed work
- **External storage**: Store full plan, load summaries

**Guideline**: Balance completeness with token budget.

---

### Extended Thinking

**Pattern**: LLMs with extended thinking (e.g., Claude 4.6 Opus) benefit from planning.

**Best Practices**:
- **Planning phase**: Enable extended thinking for plan creation
- **Execution phase**: Standard thinking for action execution
- **Replanning phase**: Extended thinking for complex re-evaluation

**Configuration**:
```json
{
  "planning_mode": {
    "extended_thinking": true,
    "effort_level": "high"
  },
  "execution_mode": {
    "extended_thinking": false,
    "effort_level": "medium"
  }
}
```

---

## Summary: Quick Reference

### When Planning is Needed
- ✅ Multi-step tasks (3+ steps)
- ✅ Complex problems requiring decomposition
- ✅ Long-horizon work (hours to days)
- ✅ High-risk changes
- ✅ User requests explicit plan

### When Planning is Overkill
- ❌ Simple, single-step tasks
- ❌ Well-practiced patterns (routine work)
- ❌ Time-critical fixes (act fast, plan later)

### Core Decisions

| Aspect | Recommendation | Rationale |
|--------|---------------|-----------|
| **Format** | Markdown + YAML frontmatter | Token-efficient, human-readable, LLM-friendly |
| **Location** | `/projects/[project]/plans/` | Version-controllable, centralized |
| **Structure** | Goal → Milestones → Tasks → Actions | Hierarchical decomposition (proven effective) |
| **Strategy** | Decompose-first (default), interleaved (exploratory) | Balance predictability with adaptability |
| **Execution** | Sequential (default), parallel (optimized) | Predictability over speed |
| **Adaptation** | Checkpoint-based replanning | Resilience through adaptive replanning |
| **Human-in-loop** | Approval gates at phase boundaries | Safety and alignment |

### Quality Checklist
- [ ] **Complete**: All steps defined, prerequisites identified
- [ ] **Feasible**: Grounded in available tools and resources
- [ ] **Efficient**: Minimal redundancy, optimal action count
- [ ] **Maintainable**: Human-readable, editable, resumable
- [ ] **Adaptable**: Replanning checkpoints, error recovery

---

## Related Context

- [[structure-standard]] - Skill structure requirements
- [[execution-standards]] - Quality standards for skill execution
- [[reference-organization]] - How to organize reference files
- [[/projects/agentic-planning-skill/]] - Planning skill implementation

---

## References

**Academic Sources**:
- arXiv:2402.02716 - Understanding the planning of LLM agents (Survey)
- arXiv:2509.08646 - Plan-then-Execute architecture guide
- arXiv:2504.16563 - GoalAct (Global planning + hierarchical execution)
- arXiv:2503.09572 - Plan-and-Act for long-horizon tasks
- arXiv:2507.21504 - Evaluation and benchmarking of LLM agents

**Industry Sources**:
- Claude Code Documentation (Anthropic, 2026)
- LangGraph Documentation (LangChain, 2025)
- AutoGPT Architecture (Open source, 2024)
- ImprovingAgents.com - LLM format benchmarks (2024-2025)

**Full Review**: [[../projects/agentic-planning-skill/systematic-review-protocol]]

---

**Created**: 2026-02-08
**Status**: Evidence-based synthesis from systematic review
**Next Review**: 2026-08-08 (6 months, or when significant new research emerges)
