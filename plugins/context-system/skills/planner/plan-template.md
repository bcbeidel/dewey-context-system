# Plan Template

**Purpose**: Standard template for all plans created by `/planner` skill.

**Usage**: Copy this structure when creating new plans. All sections are included; remove optional sections if not needed for your specific plan.

---

```markdown
---
title: "[Descriptive Plan Name]"
project: "[project-name]"
created: YYYY-MM-DD
updated: YYYY-MM-DD
status: draft | approved | in-progress | completed | archived
version: 1.0
goal: "[One-sentence goal statement]"
estimated_duration: "[hours/days]"
complexity: low | medium | high
strategy: decompose-first | interleaved | milestone-based
tags: [planning, feature-name, ...]
---

# [Plan Name]

## Goal

[Clear, specific statement of what success looks like]

**Success Criteria**:
- [ ] Criterion 1 (measurable outcome)
- [ ] Criterion 2 (measurable outcome)
- [ ] Criterion 3 (measurable outcome)

---

## Context

### Background
[Relevant context: why are we doing this? what's the current state?]

### Constraints
- **Time**: [deadline or duration]
- **Resources**: [available tools, APIs, services]
- **Technical**: [platform, framework, version requirements]
- **Scope**: [what's included, what's excluded]

### Assumptions
- [Assumption 1: things we're assuming to be true]
- [Assumption 2: if these change, plan may need revision]

---

## Available Tools

**Validated** (confirmed available):
- ✅ Tool 1: [purpose/usage]
- ✅ Tool 2: [purpose/usage]
- ✅ Tool 3: [purpose/usage]

**Not Available** (need to acquire or work without):
- ❌ Tool X: [reason not available]
- ❌ Service Y: [would be helpful but can't use]

---

## Milestones

### Milestone 1: [Milestone Name]

**Goal**: [What this milestone achieves]
**Estimated Effort**: [time estimate]
**Success Criteria**: [How to verify milestone completion]
**Dependencies**: [None | Requires: X, Y, Z]

#### Tasks

##### Task 1.1: [Task Name]

**Description**: [Clear description of what needs to be done]

**Actions**:
1. [Specific step with tool/command]
2. [Specific step with tool/command]
3. [Specific step with tool/command]

**Tools**: [Tools used for this task]
**Estimated Time**: [minutes/hours]
**Prerequisites**: [What must be done first]
**Output**: [What this produces]

##### Task 1.2: [Task Name]

**Description**: [What needs to be done]

**Actions**:
1. [Specific step]
2. [Specific step]
3. [Specific step]

**Tools**: [Tools used]
**Estimated Time**: [time]
**Prerequisites**: [dependencies]
**Output**: [deliverable]

[Continue with more tasks...]

---

### Milestone 2: [Milestone Name]

**Goal**: [What this achieves]
**Estimated Effort**: [time]
**Success Criteria**: [verification method]
**Dependencies**: [Requires Milestone 1]

#### Tasks

##### Task 2.1: [Task Name]
[Same structure as above...]

---

### Milestone 3: [Milestone Name]

[Same structure as above...]

---

## Dependencies & Sequencing

**Sequential** (must be done in order):
```
Milestone 1 → Milestone 2 → Milestone 3
Task 1.1 → Task 1.2
```

**Parallel** (can be done concurrently):
```
Task 2.1 ∥ Task 2.2 ∥ Task 2.3
```

**Dependency Graph** (optional, for complex plans):
```
    [Task 1.1]
         ↓
    [Task 1.2] → [Task 2.1]
         ↓            ↓
    [Task 1.3] → [Task 2.2]
                     ↓
                [Task 3.1]
```

---

## Risks & Mitigation

| Risk | Likelihood | Impact | Mitigation Strategy |
|------|------------|--------|---------------------|
| [Risk description] | Low/Med/High | Low/Med/High | [How to prevent or address] |
| [Risk description] | Low/Med/High | Low/Med/High | [Mitigation approach] |
| [Risk description] | Low/Med/High | Low/Med/High | [Backup plan] |

---

## Replanning Triggers

**When to reconsider this plan**:
- [ ] Any milestone takes >2x estimated time
- [ ] Required tool becomes unavailable
- [ ] Unexpected blocker discovered (list specific blockers)
- [ ] Requirements change significantly
- [ ] New information invalidates assumptions

**Replanning Process**:
1. Stop execution at current milestone boundary
2. Document what changed and why
3. Create new plan version (increment version number)
4. Get user approval for new direction
5. Resume with updated plan

---

## Quality Validation

### Completeness
- [ ] All steps defined from current state to goal
- [ ] Prerequisites identified for each task
- [ ] Success criteria specified
- [ ] Dependencies mapped

### Feasibility
- [ ] All required tools available (no hallucinations)
- [ ] Constraints respected
- [ ] Timeline realistic
- [ ] No impossible actions

### Efficiency
- [ ] No redundant steps
- [ ] Optimal action count
- [ ] Parallel opportunities identified
- [ ] Right tools for each task

### Maintainability
- [ ] Human-readable format
- [ ] Clear structure
- [ ] Documented rationale
- [ ] Resumable if interrupted

### Adaptability
- [ ] Replanning checkpoints defined
- [ ] Risk mitigation specified
- [ ] Error recovery paths identified
- [ ] Flexible to changes

---

## Approval

- [ ] Plan reviewed by user
- [ ] All questions answered
- [ ] Concerns addressed
- [ ] Ready for execution

**Approved by**: [name]
**Date**: [YYYY-MM-DD]

---

## Execution Log

[Track progress, deviations, and replanning decisions during execution]

### [YYYY-MM-DD] - Plan Created
- Status: Draft
- Strategy: [chosen strategy]
- Estimated duration: [time]

### [YYYY-MM-DD] - Plan Approved
- Approved by: [name]
- Ready to begin execution
- Starting with: Milestone 1, Task 1.1

### [YYYY-MM-DD] - Milestone 1 Started
- Current task: Task 1.1
- Status: In progress
- Notes: [any deviations or discoveries]

### [YYYY-MM-DD] - Task 1.1 Complete
- Actual time: [vs estimated]
- Output: [what was produced]
- Deviation: [any differences from plan]
- Next: Task 1.2

### [YYYY-MM-DD] - Milestone 1 Checkpoint
- Status: [on track / behind / ahead]
- Deviations: [list any]
- Decision: [continue as planned / need replan]
- Notes: [lessons learned, adjustments]

### [YYYY-MM-DD] - Replan Required
- Reason: [what changed]
- Impact: [which milestones affected]
- New approach: [high-level changes]
- Approved by: [name]
- Updated: [increment version number]

### [YYYY-MM-DD] - Plan Completed
- Final status: Completed
- Total time: [actual vs estimated]
- Success criteria: [all met? partial?]
- Retrospective: [what worked, what didn't]

---

## Notes

[Additional context, references, learnings, ideas for future]

**References**:
- [Link to related documentation]
- [Link to similar plans]
- [Link to research or examples]

**Learnings**:
- [What worked well]
- [What could be improved]
- [Patterns discovered]

**Future Enhancements**:
- [Ideas for later]
- [Out of scope but worth noting]

---

## Related Resources

**Code**:
- [Link to relevant code files]
- [Entry points]
- [Key modules]

**Documentation**:
- [Project docs]
- [API docs]
- [Architecture diagrams]

**Context**:
- [Related plans]
- [Decision documents]
- [Team discussions]

---

**Plan Version**: 1.0
**Last Updated**: [YYYY-MM-DD]
**Status**: [current status]
```

---

## Template Customization

### Optional Sections (Can Remove)

**For simple plans**, you might not need:
- Dependencies & Sequencing section (if no complex dependencies)
- Dependency Graph (if simple sequential flow)
- Replanning Triggers (if short task, unlikely to need replan)
- Related Resources section (if all context in plan itself)

**Keep these sections** (essential):
- Goal and Success Criteria
- Milestones and Tasks
- Quality Validation
- Execution Log

---

### Section Variations by Strategy

**Decompose-First Strategy**:
- Use full template
- All milestones detailed upfront
- Complete task breakdown

**Interleaved Strategy**:
- Lighter milestone definition initially
- More emphasis on Replanning Triggers
- Execution log tracks discoveries
- Plan evolves in execution log section

**Milestone-Based Strategy**:
- High-level milestone overview in main plan
- Separate detailed plans per milestone
- Link from main plan to milestone-specific plans

---

## Example: Minimal Plan (Simple Task)

For a simple task (1-2 milestones, <1 day):

```markdown
---
title: "Add Input Validation to User Form"
project: "web-app"
created: 2026-02-08
status: approved
goal: "Add client-side validation to user registration form"
estimated_duration: "3 hours"
complexity: low
---

# Add Input Validation to User Form

## Goal
Add client-side validation (email format, password strength) to user registration form.

**Success Criteria**:
- [ ] Email field validates format
- [ ] Password shows strength indicator
- [ ] Form prevents submit if invalid

## Milestone 1: Implement Validation

### Task 1.1: Add Email Validation
**Actions**:
1. Add email regex pattern to form
2. Show error message for invalid format
3. Test with various inputs

**Time**: 45 minutes

### Task 1.2: Add Password Strength
**Actions**:
1. Implement strength checker (length, chars)
2. Add visual indicator (weak/medium/strong)
3. Prevent weak passwords

**Time**: 1 hour

### Task 1.3: Testing
**Actions**:
1. Test all validation scenarios
2. Verify error messages clear
3. Check accessibility

**Time**: 45 minutes

## Quality Validation
- [x] Complete (all steps defined)
- [x] Feasible (standard patterns)
- [x] Efficient (minimal approach)

## Execution Log
[Track progress here]
```

---

## Example: Comprehensive Plan (Complex Project)

For complex, multi-week project, use full template with:
- Multiple detailed milestones (5-10)
- Comprehensive risk analysis
- Detailed dependency mapping
- Thorough replanning triggers
- Complete validation checklist

See [[examples]] for full walkthrough.

---

## Plan File Naming

**Convention**: `[descriptive-name]-[YYYY-MM-DD].md`

**Good names**:
- `oauth2-migration-2026-02-08.md` (specific feature)
- `database-performance-optimization-2026-02-08.md` (clear scope)
- `replan-after-api-changes-2026-02-10.md` (indicates replan)

**Avoid**:
- `plan.md` (not descriptive)
- `my-plan-1.md` (not meaningful)
- `2026-02-08.md` (date only, no context)

---

## Version Management

**Version numbering** (in frontmatter):
- **1.0**: Initial plan
- **1.1**: Minor updates (small adjustments, no major changes)
- **2.0**: Major replan (significant approach change)

**When to create new file vs. update**:
- **Update existing**: Minor tweaks, execution log updates
- **New file**: Major replan, different approach, version 2.0+

**Example progression**:
```
oauth2-migration-2026-02-08.md (v1.0 - initial)
oauth2-migration-2026-02-08.md (v1.1 - updated after testing)
oauth2-replan-2026-02-10.md (v2.0 - major changes, new file)
```

---

## Quick Reference: Required vs Optional

### ✅ Required (Always Include)
- Frontmatter (all fields)
- Goal statement
- Success criteria
- At least one Milestone
- At least one Task per milestone
- Quality validation checklist
- Approval section
- Execution log section

### 📋 Recommended (Usually Include)
- Context (background, constraints)
- Available tools
- Dependencies & sequencing
- Risks & mitigation
- Replanning triggers

### 🔧 Optional (Include if Relevant)
- Dependency graph (complex plans only)
- Related resources (if many references)
- Notes section (for additional context)
- Multiple tasks per milestone (simple plans may have 1-2)

---

**Template Version**: 1.0
**Created**: 2026-02-08
**Based On**: Systematic review of agentic planning best practices
