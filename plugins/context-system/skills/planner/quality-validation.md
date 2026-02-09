# Quality Validation Guide

**Purpose**: Detailed criteria and validation procedures for the 5 quality dimensions.

**When to Use**: During Phase 2 (Plan Creation) to validate plan quality before user approval.

**Evidence-Based**: All criteria derived from systematic review of agentic planning research (2024-2026).

---

## Overview

Every plan created by `/planner` is validated across 5 dimensions:

1. **Completeness**: All necessary steps defined
2. **Feasibility**: Plan is achievable with available resources
3. **Efficiency**: Minimal redundancy, optimal approach
4. **Maintainability**: Human-readable, editable, resumable  
5. **Adaptability**: Can evolve based on execution results

**Validation level**: All 5 dimensions must pass before plan approval.

---

## Dimension 1: Completeness

### Definition
Plan includes all necessary steps to achieve the goal from current state.

### Validation Checklist

- [ ] **Goal clearly stated**: One-sentence objective with measurable outcome
- [ ] **Success criteria specified**: 3-5 concrete criteria for "done"
- [ ] **All milestones defined**: Major checkpoints from start to finish
- [ ] **Tasks decomposed**: Each milestone broken into specific tasks
- [ ] **Actions specified**: Each task has concrete steps
- [ ] **Prerequisites identified**: Dependencies clear for each task
- [ ] **Tools specified**: Each action lists required tools

### Validation Questions

1. **Trace test**: Can you reach the goal by following this plan step-by-step?
2. **Gap check**: Are there any missing steps between current state and goal?
3. **Prerequisite check**: Can each task start when planned, or are dependencies missing?

### Common Failures

**Missing prerequisites** (task can't start without stated dependency), **vague success criteria** ("it works" not measurable), **missing steps** (gaps between milestones)

### Validation Procedure

1. **Read through plan start to finish**
2. **Identify any gaps** ("How do we get from step X to step Y?")
3. **Check prerequisites** (Can each task start when planned?)
4. **Verify success criteria** (Can we measure these?)
5. **Ask**: Would another person understand all steps?

**Pass criteria**: No gaps, all prerequisites clear, success measurable

---

## Dimension 2: Feasibility

### Definition
Plan steps are achievable with available tools, within constraints, grounded in reality (no hallucinations).

### Validation Checklist

- [ ] **All tools exist**: No hallucinated capabilities
- [ ] **Constraints respected**: Time, resources, technical limits honored
- [ ] **Dependencies satisfied**: Required services/APIs available
- [ ] **No impossible actions**: Each step is actually achievable
- [ ] **Timeline realistic**: Estimates match typical completion times
- [ ] **Permissions available**: Can actually perform actions

### Validation Questions

1. **Tool check**: Do all referenced tools actually exist and work as described?
2. **Reality check**: Is each action actually possible with current setup?
3. **Timeline check**: Are estimates realistic, not overly optimistic?

### Common Failures

**Hallucinated tools** (referencing non-existent tools), **unrealistic timelines** (hours for multi-day work), **impossible constraints** (task violates stated constraint)

### Validation Procedure

1. **Cross-reference tool inventory**: Check every tool mentioned exists
2. **Validate against constraints**: Ensure no constraint violations
3. **Sanity check estimates**: Compare to typical task durations
4. **Check permissions**: Verify can actually perform actions
5. **Test assumptions**: Are assumptions realistic?

**Pass criteria**: All tools exist, constraints respected, realistic estimates

---

## Dimension 3: Efficiency

### Definition
Plan minimizes redundant work, uses optimal tools, identifies parallelization opportunities.

### Validation Checklist

- [ ] **No redundant steps**: Each action necessary, no duplicates
- [ ] **Optimal tool selection**: Right tool for each job
- [ ] **Minimal action count**: Fewest steps to goal
- [ ] **Parallel opportunities identified**: Independent tasks marked
- [ ] **No over-engineering**: Appropriate complexity for task

### Validation Questions

1. **Redundancy check**: Could any steps be removed without compromising goal?
2. **Tool optimization**: Are we using the best tool for each task?
3. **Parallelization**: Can any tasks happen concurrently?

### Common Issues

**Redundant steps** (testing same thing multiple times), **missed parallelization** (independent tasks done sequentially), **wrong tool selection** (manual when automated option exists)

### Validation Procedure

1. **Review each step**: Ask "Is this necessary?"
2. **Check tool choices**: Could a better tool be used?
3. **Map dependencies**: Identify independent tasks
4. **Calculate critical path**: What's the minimum time?
5. **Look for patterns**: Repetitive work that could be automated?

**Pass criteria**: No redundancy, good tool choices, parallelization identified

---

## Dimension 4: Maintainability

### Definition
Plan is human-readable, editable, resumable, and well-documented.

### Validation Checklist

- [ ] **Human-readable format**: Markdown (not complex JSON)
- [ ] **Clear structure**: Consistent sections, good organization
- [ ] **Documented rationale**: Why this approach (not just what)
- [ ] **Version tracked**: Can be committed to git
- [ ] **Resumable**: Can pick up where left off
- [ ] **Search-friendly**: Tags, clear naming

### Validation Questions

1. **Readability**: Could someone else understand this plan?
2. **Editability**: Easy to modify if requirements change?
3. **Resumability**: If interrupted, easy to continue?

### Common Issues

**Poor structure** (no hierarchy, vague), **missing rationale** (doesn't explain why this approach), **not resumable** (no execution log or progress tracking)

### Validation Procedure

1. **Readability test**: Give to someone unfamiliar, can they understand?
2. **Edit test**: Try changing a requirement, easy to update plan?
3. **Resume test**: Imagine interrupted mid-execution, clear where to continue?
4. **Search test**: Can you find this plan later using tags/title?

**Pass criteria**: Clear structure, documented rationale, trackable progress

---

## Dimension 5: Adaptability

### Definition
Plan can evolve based on execution results, has error recovery, defined replanning triggers.

### Validation Checklist

- [ ] **Milestones enable checkpoints**: Natural replan boundaries
- [ ] **Risks identified**: What could go wrong
- [ ] **Mitigation defined**: How to address risks
- [ ] **Replanning triggers**: When to reconsider plan
- [ ] **Error recovery paths**: What to do if step fails
- [ ] **Assumptions documented**: What might invalidate plan

### Validation Questions

1. **Failure scenarios**: What if step X fails? Is there a recovery path?
2. **Assumption changes**: What if assumption Y proves wrong?
3. **Checkpoint clarity**: Are replan opportunities clear?

### Common Issues

**No error recovery** (no fallback if steps fail), **undocumented assumptions** (plan breaks if assumptions change), **no replanning triggers** (unclear when to replan)

### Validation Procedure

1. **Identify failure points**: What could go wrong at each step?
2. **Check recovery paths**: Is there a "plan B" for each risk?
3. **Review assumptions**: Are they documented? What if they change?
4. **Verify checkpoints**: Are milestone boundaries clear replan points?
5. **Test adaptability**: If requirements changed 50%, could plan adapt?

**Pass criteria**: Risks mitigated, checkpoints clear, assumptions documented

---

## Overall Quality Score

### Scoring Method

Each dimension: Pass (1) or Fail (0)
Overall: All 5 must pass

**Quality Score = 5/5 required for approval**

### Example Validation

```markdown
## Quality Validation Results

### Completeness: ✅ PASS
- All steps defined
- Prerequisites clear
- Success criteria measurable

### Feasibility: ✅ PASS
- All tools validated (Passport.js exists, Google OAuth available)
- Timeline realistic (3 days estimated, 5 days available)
- No hallucinated capabilities

### Efficiency: ✅ PASS
- No redundant steps
- Testing tasks can run in parallel
- Optimal tool choices (Passport.js for OAuth)

### Maintainability: ✅ PASS
- Clear markdown structure
- Rationale documented
- Execution log for tracking

### Adaptability: ✅ PASS
- Milestone checkpoints defined
- Risks identified (OAuth API changes, credential approval)
- Replanning triggers clear

**Overall: 5/5 PASS** ✅
Plan approved for execution
```

### If Validation Fails

**One dimension fails**: Fix that dimension, re-validate

**Multiple dimensions fail**: Consider replanning with different approach

**All dimensions fail**: Start over with clearer requirements

---

## Validation in Practice

### Quick Validation (5 minutes)

For simple plans, quick checklist:
- [ ] Can I trace from current state to goal? (Completeness)
- [ ] Do all tools actually exist? (Feasibility)
- [ ] Any obvious redundancy? (Efficiency)
- [ ] Would another person understand this? (Maintainability)
- [ ] What if step X fails - is there a plan? (Adaptability)

### Thorough Validation (15-20 minutes)

For complex plans, detailed review:
1. Read plan completely
2. Check each dimension systematically
3. Document issues found
4. Propose fixes
5. Re-validate after fixes

---

## Automated vs Manual Validation

### Can Be Automated
- Tool existence check (grep tool inventory)
- Structure validation (sections present?)
- Timeline sanity check (compare to typical durations)
- Link validation (all wikilinks resolve?)

### Requires Human Judgment
- Goal clarity (is it specific enough?)
- Approach quality (is this the best way?)
- Risk completeness (did we miss major risks?)
- Adaptability (are checkpoints well-chosen?)

**Current**: Manual validation during Phase 2
**Future**: Could add automated checks as validation helpers

---

## Quality Validation Template

Use this in Phase 2:

```markdown
## Quality Validation

### Completeness
**Check**: All steps defined, prerequisites clear, success measurable
**Result**: [ ] Pass / [ ] Fail
**Issues**: [list any problems]
**Fixes**: [how to address]

### Feasibility  
**Check**: Tools exist, constraints respected, timeline realistic
**Result**: [ ] Pass / [ ] Fail
**Issues**: [list any problems]
**Fixes**: [how to address]

### Efficiency
**Check**: No redundancy, optimal tools, parallelization identified
**Result**: [ ] Pass / [ ] Fail  
**Issues**: [list any problems]
**Fixes**: [how to address]

### Maintainability
**Check**: Readable, editable, resumable, documented
**Result**: [ ] Pass / [ ] Fail
**Issues**: [list any problems]
**Fixes**: [how to address]

### Adaptability
**Check**: Checkpoints clear, risks mitigated, assumptions documented
**Result**: [ ] Pass / [ ] Fail
**Issues**: [list any problems]
**Fixes**: [how to address]

**Overall Score**: [X]/5
**Decision**: [ ] Approve / [ ] Revise
```

---

**Validation Version**: 1.0
**Created**: 2026-02-08
**Evidence-Based**: Systematic review of agentic planning research (2024-2026)
