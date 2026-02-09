# Phase 2: Plan Creation

**Purpose**: Create detailed, validated plan through hierarchical decomposition and quality validation.

**Time**: 15-30 minutes

**Your role**: Review plan summary, provide feedback, refine approach

**Output**: Approved plan ready for finalization

---

## Overview

Phase 2 transforms the requirements and context from Phase 1 into a structured, validated plan. This is where hierarchical decomposition happens: breaking the goal into milestones, tasks, and actions.

**What makes Phase 2 effective**:
- Evidence-based decomposition (hierarchical structure from research)
- Strategy-appropriate approach (decompose-first, interleaved, or milestone-based)
- Explicit dependency mapping (sequential vs. parallel work)
- Risk identification upfront (what could go wrong)
- 5-dimension quality validation (completeness, feasibility, efficiency, maintainability, adaptability)
- User review and approval (human-in-loop)

---

## Step-by-Step Workflow

### Step 1: Hierarchical Decomposition

**Goal**: Break goal into 4 levels of abstraction

**Evidence**: GoalAct framework showed 12.22% improvement using hierarchical execution (arXiv:2504.16563)

**Hierarchy**:
1. **Goal** (from Phase 1): Overall objective
2. **Milestones**: Major checkpoints (3-7 milestones typical)
3. **Tasks**: Concrete work units (2-5 tasks per milestone)
4. **Actions**: Individual steps (3-10 actions per task)

**Example**:
```
Goal: Add OAuth2 authentication to API

Milestone 1: Design OAuth2 Flow
  Task 1.1: Research provider options
    Action 1: Review Auth0 documentation
    Action 2: Review Okta documentation
    Action 3: Compare pricing and features
    Action 4: Document recommendation

  Task 1.2: Design user flow
    Action 1: Map current session flow
    Action 2: Design OAuth redirect flow
    Action 3: Document state management
    Action 4: Get security review

Milestone 2: Implement OAuth Integration
  Task 2.1: Set up provider configuration
    ...
```

**Decomposition questions**:
- **What are the major phases?** (milestones)
- **What concrete work happens in each phase?** (tasks)
- **What specific steps achieve each task?** (actions)

**Stopping criteria**:
- Actions are concrete enough to execute (not vague like "do OAuth")
- Each action uses specific tools (Read, Write, Bash, WebSearch, etc.)
- Actions have clear inputs and outputs

---

### Step 2: Apply Planning Strategy

**Goal**: Use the strategy selected in Phase 1

**Three strategies** (see [[phase-1-setup-discovery]] Step 5):

#### Decompose-First (Default)
- **When**: Well-defined problem, known requirements
- **How**: Fully decompose all milestones, tasks, and actions upfront
- **Output**: Complete plan with all details before execution

**Example application**:
```markdown
## Milestones

### Milestone 1: Design OAuth2 Flow
[Fully detailed with all tasks and actions]

### Milestone 2: Implement OAuth Integration
[Fully detailed with all tasks and actions]

### Milestone 3: Testing and Validation
[Fully detailed with all tasks and actions]

[All milestones defined before execution begins]
```

#### Interleaved (Exploratory)
- **When**: Uncertain requirements, exploratory work
- **How**: Detail first milestone fully, sketch remaining milestones, refine as you execute
- **Output**: Detailed first milestone, high-level remaining milestones

**Example application**:
```markdown
## Milestones

### Milestone 1: Reproduce Issue (DETAILED)
[Fully detailed with all tasks and actions]

### Milestone 2: Identify Root Cause (SKETCH)
**Goal**: Determine why API timeouts occur
**Approach**: TBD based on Milestone 1 findings
**Tasks**: [Will refine after Milestone 1]

### Milestone 3: Implement Fix (SKETCH)
**Goal**: Fix identified issue
**Approach**: TBD based on root cause
```

#### Milestone-Based (Long-Horizon)
- **When**: Multi-day or multi-week project
- **How**: High-level milestones with checkpoint reviews, detail one milestone at a time
- **Output**: Milestone overview, separate detailed plan per milestone

**Example application**:
```markdown
## High-Level Milestones

### Milestone 1: Extract Authentication Service (Week 1)
**Status**: Current milestone
**Detailed plan**: [linked or inline]

### Milestone 2: Extract User Service (Week 2)
**Status**: Pending (will detail after Milestone 1)
**High-level goals**: [sketch only]

[Remaining milestones sketched, detailed later]
```

---

### Step 3: Dependency Mapping

**Goal**: Identify sequential vs. parallel work

**Sequential dependencies**:
```
Milestone 1 → Milestone 2 → Milestone 3
(Must complete in order)

Task 1.1 → Task 1.2
(Task 1.2 requires Task 1.1 output)
```

**Parallel opportunities**:
```
Task 2.1 ∥ Task 2.2 ∥ Task 2.3
(All tasks independent, can run concurrently)
```

**Dependency graph** (for complex plans):
```
    [Milestone 1]
         ↓
    [Milestone 2] → [Milestone 3]
         ↓            ↓
    [Milestone 4] ← [Milestone 5]
```

**Mapping process**:
1. **Identify prerequisites**: What must be done first?
2. **Find independent work**: What can happen in parallel?
3. **Mark blocking tasks**: What blocks progress?
4. **Calculate critical path**: What's the minimum timeline?

**Document in plan**:
```markdown
## Dependencies & Sequencing

**Sequential** (must be done in order):
- Milestone 1 → Milestone 2 (design before implementation)
- Task 1.1 → Task 1.2 (research before decision)

**Parallel** (can be done concurrently):
- Task 2.1 ∥ Task 2.2 ∥ Task 2.3 (independent implementations)
- Testing and documentation can happen in parallel

**Critical path**: Milestone 1 → Milestone 2 → Milestone 3 (sequential)
**Total time estimate**: 2-3 days (assuming parallelization)
```

---

### Step 4: Risk Identification

**Goal**: Identify what could go wrong and plan mitigation

**Risk categories**:
1. **Technical risks**: Tool limitations, technical constraints
2. **Dependency risks**: External services, APIs, libraries
3. **Resource risks**: Time, access, knowledge gaps
4. **Assumption risks**: Invalid assumptions, missing information

**Risk template**:
```markdown
## Risks & Mitigation

| Risk | Likelihood | Impact | Mitigation Strategy |
|------|------------|--------|---------------------|
| OAuth provider API changes | Low | High | Pin to specific API version |
| Token refresh complexity | High | Medium | Use library with built-in refresh |
| Existing users can't migrate | Low | High | Keep session auth working in parallel |
```

**For each risk, identify**:
- **What**: Specific risk description
- **Likelihood**: Low / Medium / High
- **Impact**: Low / Medium / High (if it happens)
- **Mitigation**: How to prevent or address

**High-risk items** (Likelihood × Impact):
- High × High → Immediate mitigation required
- High × Medium or Medium × High → Mitigation plan needed
- Low × High → Contingency plan
- Low × Low → Document but don't over-plan

---

### Step 5: Quality Validation

**Goal**: Validate plan across 5 dimensions before user review

**See**: [[quality-validation]] for detailed validation procedures

**5-Dimension Framework**:

#### 1. Completeness
- [ ] All steps defined from current state to goal
- [ ] Prerequisites identified for each task
- [ ] Success criteria specified
- [ ] No gaps in workflow

**Quick check**: Can you trace from current state to goal by following the plan?

#### 2. Feasibility
- [ ] All required tools available (no hallucinations)
- [ ] Constraints respected (time, resources, technical limits)
- [ ] Timeline realistic (not overly optimistic)
- [ ] No impossible actions

**Quick check**: Do all referenced tools actually exist?

#### 3. Efficiency
- [ ] No redundant steps
- [ ] Optimal action count (minimal necessary work)
- [ ] Parallel opportunities identified
- [ ] Right tools for each task

**Quick check**: Could any steps be removed without compromising the goal?

#### 4. Maintainability
- [ ] Human-readable format (markdown, clear structure)
- [ ] Clear structure (consistent sections)
- [ ] Documented rationale (why this approach)
- [ ] Resumable (can pick up where left off)

**Quick check**: Would another person understand this plan?

#### 5. Adaptability
- [ ] Replanning checkpoints defined (milestone boundaries)
- [ ] Risk mitigation specified
- [ ] Error recovery paths identified
- [ ] Flexible to changes

**Quick check**: What happens if a key assumption changes?

**Validation outcome**:
- **Pass (5/5)**: Proceed to user review
- **Fail (< 5)**: Fix failing dimensions, re-validate

---

### Step 6: User Review & Approval

**Goal**: Present plan summary, get feedback, refine

**Presentation format**:

```markdown
> I've created a plan for "[goal]". Here's the summary:
>
> **Strategy**: Decompose-first (well-defined problem)
>
> **Milestones**:
> 1. Design OAuth2 Flow (2-3 hours)
> 2. Implement OAuth Integration (1 day)
> 3. Testing and Validation (4-6 hours)
> 4. Deployment (2-3 hours)
>
> **Total Estimate**: 2-3 days
>
> **Key Risks**:
> - OAuth provider API changes (mitigation: pin version)
> - Token refresh complexity (mitigation: use library)
>
> **Quality Validation**: 5/5 dimensions passed
>
> **Next Steps**:
> 1. I'll save the plan to /projects/authentication-system/plans/
> 2. You can review the full plan file
> 3. Edit if needed (it's markdown)
> 4. When ready, we start execution
>
> Does this approach make sense? Any changes before I finalize?
```

**User response options**:
- ✅ **"Looks good"** → Proceed to Phase 3 (finalization)
- 🔄 **"Change X"** → Revise plan, re-validate, present again
- ❓ **"What about Y?"** → Clarify, potentially adjust plan
- ❌ **"Different approach"** → Return to Phase 1, reconsider strategy

**Iteration**:
- Plans rarely perfect on first pass
- Iterate until user approves
- Document changes (why approach evolved)
- Keep revision history in plan file

---

## Phase 2 Outputs

At the end of Phase 2, you should have:

**1. Hierarchical Plan Structure**
```
Goal → 3-7 Milestones → 2-5 Tasks per milestone → 3-10 Actions per task
```

**2. Dependency Map**
- Sequential dependencies identified
- Parallel opportunities marked
- Critical path calculated

**3. Risk Assessment**
- Key risks identified
- Mitigation strategies defined
- High-risk items flagged

**4. Quality Validation**
- 5/5 dimensions passed
- Issues addressed
- Ready for execution

**5. User Approval**
- User reviewed summary
- Feedback incorporated
- Approach confirmed

**6. Plan Draft** (in memory, ready for Phase 3)
- All content prepared
- Frontmatter defined
- Markdown formatted
- Ready to save

---

## Common Issues & Solutions

### Issue: "Plan is too detailed (>10 pages)"

**Cause**: Over-decomposition, too many actions per task

**Solution**:
- Use milestone-based strategy (detail one milestone at a time)
- Raise abstraction level (fewer, higher-level actions)
- Break into separate plans (per major component)
- Focus on next 2-3 milestones only

---

### Issue: "Plan feels too vague"

**Cause**: Under-decomposition, actions not concrete enough

**Solution**:
- Decompose further (break actions into sub-actions)
- Add concrete examples for each action
- Specify tools for each action
- Add expected outputs

---

### Issue: "Can't identify dependencies"

**Cause**: Unclear prerequisites, complex task interactions

**Solution**:
- List all tasks, mark prerequisites for each
- Ask: "What must be done before this task?"
- Draw dependency graph (visualize relationships)
- Test with "Can I do X before Y?" questions

---

### Issue: "Quality validation fails"

**Cause**: Missing steps, hallucinated tools, unrealistic timeline

**Solution**:
- **Completeness**: Trace workflow, identify gaps
- **Feasibility**: Validate tool inventory from Phase 1
- **Efficiency**: Remove redundant steps
- **Maintainability**: Add rationale, improve structure
- **Adaptability**: Add replanning triggers, risk mitigation

---

## Time Management

**Typical Phase 2 timing**:
- Hierarchical decomposition: 5-10 minutes
- Apply strategy: 2-3 minutes (already selected in Phase 1)
- Dependency mapping: 3-5 minutes
- Risk identification: 2-4 minutes
- Quality validation: 3-5 minutes
- User review: 2-5 minutes (iteration may extend)

**Total**: 15-30 minutes

**If taking longer**:
- Over-detailed decomposition (+10 minutes): Raise abstraction level
- Complex dependencies (+10 minutes): Draw diagram, simplify
- Multiple validation failures (+15 minutes): Return to Phase 1, reconsider approach
- User iterations (+5-15 minutes each): Normal for complex projects

**Maximum reasonable time**: 45 minutes

If Phase 2 is taking >45 minutes:
- Goal too broad (break into multiple projects)
- Strategy mismatch (use interleaved or milestone-based)
- Unclear requirements (return to Phase 1, gather more context)

---

## Next Steps

After completing Phase 2:

1. **Review outputs**: Confirm all 6 outputs present
2. **Save plan draft**: Keep in memory for Phase 3
3. **Proceed to Phase 3**: Plan finalization and saving

**→ Continue to**: [[phase-3-finalization]]
