# Planner Skill Examples

**Purpose**: Real-world walkthroughs demonstrating the three planning strategies in action.

**When to use**: Learning how to use /planner, understanding strategy selection, seeing complete workflow examples.

---

## Overview

This document provides three complete examples showing how /planner works for different task types:

1. **Feature Implementation** (Decompose-First Strategy) - Well-defined problem
2. **Debugging** (Interleaved Strategy) - Exploratory work
3. **Large Project** (Milestone-Based Strategy) - Long-horizon task

Each example includes:
- Phase 1: Setup & Discovery
- Phase 2: Plan Creation
- Phase 3: Finalization
- Execution notes
- Lessons learned

---

## Example 1: Feature Implementation (Decompose-First)

### Scenario
**Goal**: Add OAuth2 authentication with Google to existing Express API

**Context**:
- Current: Session-based authentication only
- Stack: Node.js + Express + PostgreSQL
- Timeline: Need working prototype in 5 days
- Constraint: Must maintain backward compatibility (sessions continue working)

---

### Phase 1: Setup & Discovery

**User invokes**: `/planner --project authentication-system`

**Step 1: Gather Requirements** (AskUserQuestion):
```
Q: What's your goal for this planning session?
A: Add OAuth2 authentication with Google provider to our API

Q: What project is this for?
A: authentication-system

Q: What does success look like?
A: Users can log in with Google account, existing session auth still works, passes security review

Q: Any constraints or deadlines?
A: 5 days for prototype, can't modify User model schema (in production use), must be backward compatible

Q: Is this well-defined or exploratory?
A: Well-defined - I know what I want, just need structured approach
```

**Step 2-3: Explore Context & Validate Tools**:
- Found: `routes/auth.js` (session implementation)
- Found: `models/User.js` (current schema)
- Validated: Node.js, npm, Git, PostgreSQL available
- Missing: Passport.js (will install), Google OAuth credentials (will create)

**Step 4: Identify Constraints**:
- Time: 5 days for prototype
- Technical: Cannot modify User model schema
- Scope: Google only (GitHub later), API only (web UI separate)

**Step 5: Strategy Selection**:
→ **Decompose-First** (well-defined problem, clear requirements, known approach)

**Step 6: Feasibility Check**:
- Feasible: ✅ Passport.js available, Google OAuth accessible, 5 days sufficient
- Estimate: 2-3 days implementation + 1-2 days testing
- Blockers: Need Google OAuth credentials (can create same day)

**Step 7: Summary & Approval**:
User approved: "Looks good, proceed with planning"

---

### Phase 2: Plan Creation

**Hierarchical Decomposition**:

**Goal**: Add OAuth2 authentication with Google provider

**Milestones**:
1. Design OAuth2 Flow (2-3 hours)
2. Implement OAuth Integration (1 day)
3. Testing and Validation (4-6 hours)
4. Deployment Preparation (2-3 hours)

**Milestone 1 breakdown**:
```
Milestone 1: Design OAuth2 Flow
  Task 1.1: Research Passport.js
    Action 1: Review Passport.js documentation
    Action 2: Review passport-google-oauth20 package
    Action 3: Document authentication flow

  Task 1.2: Design user flow
    Action 1: Map current session flow
    Action 2: Design OAuth redirect flow
    Action 3: Document token storage approach
    Action 4: Get security team review
```

(Similar breakdown for Milestones 2-4)

**Dependencies**:
- Sequential: M1 → M2 → M3 → M4 (design before implementation)
- Parallel: Task 3.1 (unit tests) ∥ Task 3.2 (integration tests)

**Risks**:
- OAuth provider API changes (Mitigation: Pin to specific version)
- Token refresh complexity (Mitigation: Use Passport.js built-in handling)
- Session migration issues (Mitigation: Keep both auth methods working in parallel)

**Quality Validation**: 5/5 dimensions passed

**User Review**: "Plan looks comprehensive, approved!"

---

### Phase 3: Finalization

**Saved plan**: `/projects/authentication-system/plans/oauth2-google-integration-2026-02-08.md`

**Git branch**: `feature/oauth2-google-authentication`

**Execution guidance**:
- Start with Milestone 1, Task 1.1
- Update execution log after each task
- Review at milestone boundaries

---

### Execution Notes

**Milestone 1** (Day 1, 3 hours):
- Completed on schedule
- Passport.js well-documented, easy to understand
- Security review approved design

**Milestone 2** (Day 2-3, 1.5 days):
- Took longer than estimated (1.5 days vs. 1 day)
- Reason: Token refresh logic more complex than expected
- Solution: Used passport-google-oauth20 built-in refresh handling

**Milestone 3** (Day 4, 6 hours):
- Completed on schedule
- All tests passing
- Integration tests caught edge case (expired tokens)

**Milestone 4** (Day 4-5, 3 hours):
- Completed on schedule
- Deployment docs written
- Ready for staging

**Final**: Completed in 4 days (estimated 2-3 days, within 5-day deadline)

---

### Lessons Learned

**What worked**:
- Decompose-first strategy perfect for well-defined problem
- Tool validation prevented surprises (Passport.js was right choice)
- Security review in design phase saved time later
- Parallel testing accelerated Milestone 3

**What didn't**:
- Initial time estimates too optimistic (1 day → 1.5 days for implementation)
- Underestimated token refresh complexity

**Patterns identified**:
- Always include security review in design phase for auth changes
- OAuth library selection critical (Passport.js saved significant time)
- Keep old auth method working during migration (reduces risk)

---

## Example 2: Debugging (Interleaved)

### Scenario
**Goal**: Fix intermittent API timeouts on production `/search` endpoint

**Context**:
- Happens randomly (not reproducible locally)
- Affects ~5% of search requests
- Started 3 days ago (no recent deployments)
- Stack: Node.js + Express + PostgreSQL + Redis cache

---

### Phase 1: Setup & Discovery

**Step 5: Strategy Selection**:
→ **Interleaved** (exploratory work, uncertain root cause, need to discover)

**Rationale**: Don't know cause yet, need hypothesis-testing approach

---

### Phase 2: Plan Creation (Partial)

**Milestone 1: Reproduce Issue** (DETAILED):
```
Task 1.1: Check production logs
  Action 1: Grep logs for timeout errors
  Action 2: Identify affected requests pattern
  Action 3: Collect error samples

Task 1.2: Attempt local reproduction
  Action 1: Use production data sample
  Action 2: Simulate load with k6
  Action 3: Monitor for timeouts
```

**Milestone 2: Identify Root Cause** (SKETCH):
- Goal: Determine why timeouts occur
- Hypotheses: (1) Slow queries, (2) Redis connection issues, (3) Connection pool exhaustion
- Approach: Test hypotheses based on Milestone 1 findings

**Milestone 3: Implement Fix** (SKETCH):
- Goal: Fix identified issue
- Approach: TBD based on root cause

---

### Execution & Replanning

**Milestone 1 Execution** (Day 1, 2 hours):
- Logs show timeouts correlate with specific search terms (large result sets)
- Local reproduction successful: Queries with >10K results timeout
- Discovery: PostgreSQL query slow on unindexed column

**Replan after Milestone 1**:
```
Milestone 2: Add Database Index (DETAILED - refined based on findings)
  Task 2.1: Analyze query execution plan
    Action 1: Run EXPLAIN on slow query
    Action 2: Identify missing index
    Action 3: Design index strategy

  Task 2.2: Create index
    Action 1: Test index creation on staging
    Action 2: Validate query performance improves
    Action 3: Apply to production (off-peak hours)
```

**Milestone 2 Execution** (Day 2, 3 hours):
- Added B-tree index on search_terms column
- Query time: 8s → 50ms (160x improvement)
- Tested with production data: No more timeouts

**Milestone 3: Not Needed** (root cause resolved in Milestone 2)

**Final**: Completed in 1.5 days (open-ended exploratory task)

---

### Lessons Learned

**What worked**:
- Interleaved strategy perfect for debugging (discover-then-plan)
- Hypothesis-based approach structured investigation
- Partial decomposition saved time (didn't over-plan upfront)

**Pattern identified**:
- For debugging: Detail first milestone (reproduce), sketch remaining (adapt based on findings)

---

## Example 3: Large Project (Milestone-Based)

### Scenario
**Goal**: Migrate monolithic Node.js app to microservices

**Context**:
- Large codebase (~50K lines)
- Multi-week effort (6-8 weeks estimated)
- Team of 3 developers
- Cannot interrupt existing feature development

---

### Phase 1: Setup & Discovery

**Step 5: Strategy Selection**:
→ **Milestone-Based** (long-horizon, needs checkpoint reviews, team coordination)

---

### Phase 2: Plan Creation (High-Level)

**Milestone overview** (6 milestones, 1-2 weeks each):

1. **Extract Authentication Service** (Week 1-2)
2. **Extract User Service** (Week 3-4)
3. **Extract Payment Service** (Week 5-6)
4. **Set Up API Gateway** (Week 7)
5. **Migrate Database** (Week 8)
6. **Decommission Monolith** (Week 9-10)

**First milestone detailed**:
```
Milestone 1: Extract Authentication Service (Week 1-2)
  Task 1.1: Identify auth boundaries
    Action 1: Map all auth-related code
    Action 2: Document dependencies
    Action 3: Design service interface

  Task 1.2: Create service scaffold
    Action 1: Set up new Express app
    Action 2: Configure database connection
    Action 3: Set up testing infrastructure

  [8 more tasks...]
```

**Remaining milestones**: High-level goals only (will detail after each milestone review)

---

### Execution with Checkpoint Reviews

**Milestone 1** (Weeks 1-2):
- Completed on schedule
- **Checkpoint review**: Authentication service deployed, 15% of endpoints migrated
- **Decision**: Continue with Milestone 2 (User Service)
- **Detailed planning**: Created detailed plan for Milestone 2

**Milestone 2** (Weeks 3-4):
- Completed 1 week ahead (3 weeks instead of 4)
- **Checkpoint review**: User service deployed, patterns established
- **Discovery**: Realized Payment Service simpler than expected (1 week vs. 2)
- **Replan**: Adjusted timeline, combined Milestone 3 and setup for Milestone 4

**Milestones 3-6**: Continued pattern with checkpoint reviews after each

**Final**: Completed in 8 weeks (estimated 6-8 weeks, on target)

---

### Lessons Learned

**What worked**:
- Milestone-based strategy perfect for long-horizon (6-8 weeks)
- Checkpoint reviews enabled adaptation (adjusted timeline mid-project)
- Detailed planning one milestone at a time prevented wasted planning effort
- Team coordination clear (each milestone was team-sized chunk)

**Pattern identified**:
- For large projects: High-level roadmap upfront, detail one milestone at a time
- Checkpoint reviews essential (replanning opportunities)

---

## Common Workflows

### Workflow 1: Start New Project

```bash
/planner --project myapp --goal "build user dashboard"
→ Phase 1: Requirements gathering
→ Phase 2: Hierarchical planning
→ Phase 3: Save plan, start work
```

### Workflow 2: Resume Interrupted Work

```bash
# Find your plan
ls /projects/myapp/plans/*.md

# Review plan file (read where you left off in execution log)
# Continue with next task in plan
```

### Workflow 3: Replan After Discovery

```bash
# During execution, major change discovered
/planner --replan
→ Skill loads current plan
→ Asks what changed
→ Creates updated plan (increments version)
→ Save as new file (with replan date)
```

### Workflow 4: Team Collaboration

```bash
# One person creates plan
/planner --project team-feature --goal "add notifications"

# Commit plan to git
git add /projects/team-feature/plans/*.md
git commit -m "docs: add plan for notifications feature"
git push

# Team reviews plan file (markdown, human-readable)
# Team executes plan collaboratively (update execution log)
```

---

## Tips for Success

### Before Planning
- Have clear goal (one sentence)
- Know project name (where to save plan)
- Understand constraints (deadlines, limitations)
- Allocate time (30-60 minutes for planning)

### During Planning
- Answer questions thoroughly (better input = better plan)
- Review plan summary carefully (catch issues early)
- Don't over-plan (balance detail with flexibility)
- Trust the validation (5-dimension quality check)

### During Execution
- Update execution log regularly (track progress)
- Review at milestones (assess if on track)
- Replan when needed (don't rigidly follow outdated plan)
- Extract learnings (`/context-curator` at completion)

---

## Strategy Selection Cheatsheet

| Task Type | Recommended Strategy | Example |
|-----------|---------------------|---------|
| Well-defined feature | Decompose-First | "Add OAuth2 authentication" |
| Bug investigation | Interleaved | "Fix timeout errors" |
| Multi-week project | Milestone-Based | "Migrate to microservices" |
| Research/exploration | Interleaved | "Research best architecture" |
| Refactoring | Decompose-First | "Extract repository pattern" |
| Performance optimization | Interleaved | "Optimize slow queries" |

**When in doubt**: Start with Decompose-First, switch to Interleaved if you discover uncertainty.

---

**Examples complete! Ready to use /planner with confidence.**
