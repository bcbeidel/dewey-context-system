# Phase 1: Setup & Discovery

**Purpose**: Understand the goal, gather context, and prepare for structured planning.

**Time**: 10-15 minutes

**Your role**: Answer questions, provide context, clarify requirements

**Output**: Clear goal, validated constraints, available tools, chosen strategy

---

## Overview

Phase 1 establishes the foundation for a good plan. Without proper setup, plans often miss critical context, hallucinate unavailable tools, or pursue the wrong approach.

**What makes Phase 1 effective**:
- Interactive requirement gathering (not assumptions)
- Actual context exploration (read code, check files)
- Tool validation (verify what's really available)
- Strategy matching (right approach for task nature)

---

## Step-by-Step Workflow

### Step 1: Gather Core Requirements (AskUserQuestion)

**Goal**: Understand what success looks like

**Questions to ask**:

1. **"What's your goal for this planning session?"**
   - Look for: One clear sentence
   - Example: "Add OAuth2 authentication to our API"
   - Bad example: "Make the app better" (too vague)

2. **"What project is this for?"**
   - Look for: Project name (for plan storage path)
   - Example: "authentication-system"
   - Will save to: `/projects/authentication-system/plans/`

3. **"What does success look like?"**
   - Look for: Concrete criteria
   - Example: "Users can log in with Google/GitHub, existing sessions still work"
   - Bad example: "It works" (not specific enough)

4. **"Any constraints or deadlines?"**
   - Time: "Need this done by end of week"
   - Scope: "Can't break existing functionality"
   - Resources: "No budget for paid services"
   - Technical: "Must work with PostgreSQL 12"

5. **"Is this a well-defined problem, or more exploratory?"**
   - Well-defined: "I know what I want, just need structured approach"
   - Exploratory: "Not sure best approach, need to discover"
   - Long-horizon: "Multi-day or multi-week effort"

**Interactive Pattern**:
```markdown
> I'll ask you a few questions to understand what you're planning:

> **Question 1**: What's your goal for this planning session?
[User answers]

> **Question 2**: What project is this for?
[User answers]

> **Question 3**: What does success look like? (What are the specific outcomes you want?)
[User answers]

> **Question 4**: Any constraints, deadlines, or things I should know about?
[User answers]

> **Question 5**: Is this a well-defined problem (you know what you want), or more exploratory (need to figure out approach)?
[User answers]

> Great! Let me explore the context and validate what tools are available...
```

---

### Step 2: Explore Existing Context

**Goal**: Understand current state before planning changes

**Actions**:
1. Check if project directory exists (`ls /projects/[project-name]/`)
2. Look for existing plans (review if relevant)
3. Identify relevant code/files (based on goal, find related directories)
4. Review existing patterns (current implementation, tech stack)

**Document findings**: Current state, tech stack, relevant files

---

### Step 3: Validate Tool Availability

**Goal**: Create explicit tool inventory (prevent hallucinations)

**Check**:
1. Development tools (`which git node npm python docker`, check versions)
2. Project tools (package managers, test runners)
3. Claude Code capabilities (Read/Write/Edit always available, Bash available with permissions)
4. External APIs/services (OAuth accounts, API keys, service access)

**Create tool inventory**: List available (✅), not available (❌), and constraints

---

### Step 4: Identify Constraints & Risks

**Goal**: Document what can/can't be done

**Constraints** (4 types):
1. **Time**: Hard deadline, soft deadline, or when ready
2. **Technical**: Database schema, backward compatibility, library restrictions, security audit
3. **Resource**: Budget, dependencies, team size
4. **Scope**: Feature limits, platform limits, environment limits

**Risks**: Identify what could go wrong, assess likelihood/impact (Low/Medium/High), plan mitigation

---

### Step 5: Determine Planning Strategy

**Goal**: Choose approach that fits task nature

**Decision tree**:

**Is this a well-defined problem?**
- Requirements clear? ✅
- Approach known? ✅
- Constraints understood? ✅
→ **Use: Decompose-First strategy**

**Is this exploratory work?**
- Requirements uncertain? ✅
- Best approach unknown? ✅
- Need to discover during work? ✅
→ **Use: Interleaved strategy**

**Is this a long-horizon task?**
- Multi-day or multi-week? ✅
- Many major components? ✅
- Needs checkpoint reviews? ✅
→ **Use: Milestone-Based strategy**

**Explain strategy to user**:
```markdown
> Based on your goal "Add OAuth2 authentication", this is a **well-defined problem** with clear requirements.

> **I'll use the Decompose-First strategy**: We'll fully decompose the goal into milestones, tasks, and actions upfront. This gives you a complete roadmap before execution starts.

> This works well because:
> - Requirements are clear (OAuth2 with Google)
> - Approach is known (use Passport.js)
> - Constraints understood (keep sessions working)

> Does this approach make sense, or would you prefer a different strategy?
```

**If strategy unclear**:
```markdown
> I'm not sure whether to use full upfront planning (decompose-first) or incremental planning (interleaved).

> **Two options**:
> 1. **Decompose-first**: Plan all steps now (best if you know exactly what you want)
> 2. **Interleaved**: Plan high-level, discover details as we go (best if exploring)

> Which matches your needs better?
```

---

### Step 6: Validate Feasibility

**Goal**: Reality check before investing in detailed planning

**Questions to answer**:

1. **Can this goal be achieved?**
   - With available tools?
   - Within constraints?
   - With current knowledge?

2. **Is the timeline realistic?**
   - Estimate: rough order of magnitude
   - Compare: against deadline
   - Red flag: If >2x deadline, discuss

3. **Are there blockers?**
   - Missing critical tools?
   - Impossible constraints?
   - Unknown unknowns?

**Feasibility check**:
```markdown
## Feasibility Assessment

**Goal**: Add OAuth2 authentication with Google

**Can it be done?** ✅ Yes
- Passport.js library available
- Google OAuth APIs accessible
- Express compatible

**Timeline realistic?** ✅ Yes (with caveat)
- Rough estimate: 2-3 days for MVP
- Your deadline: 5 days
- Margin: Sufficient for testing

**Blockers?** ⚠️ One
- Need Google OAuth app credentials (can create today)

**Recommendation**: Proceed with planning. No major concerns.
```

**If not feasible**:
```markdown
## Feasibility Assessment

**Goal**: Migrate to microservices by end of week

**Can it be done?** ❌ Not in timeline
- Estimate: 6-8 weeks for safe migration
- Your deadline: 5 days
- Gap: 10x mismatch

**Recommendation**:
1. **Revise timeline**: Push deadline to realistic date
2. **Reduce scope**: Maybe just extract one service?
3. **Different approach**: Modularize first, extract later?

> I don't think we can safely complete "migrate to microservices" in 5 days. The risk of breaking production is too high.

> Would you like to:
> A) Revise the timeline (need 6-8 weeks)
> B) Reduce scope (just extract one service as proof-of-concept)
> C) Take a different approach (I can suggest alternatives)
```

---

### Step 7: Summarize & Get Approval

**Goal**: Confirm understanding before detailed planning

**Present summary**:
```markdown
> Let me confirm what we're planning:

> **Goal**: Add OAuth2 authentication with Google provider
> **Project**: authentication-system
> **Success Criteria**:
> - Users can log in with Google account
> - Existing session-based auth still works
> - Passes security review

> **Strategy**: Decompose-First (full upfront planning)

> **Context**:
> - Current: Express sessions, local auth only
> - Stack: Node.js + Express + PostgreSQL
> - Need: Google OAuth credentials (can create)

> **Constraints**:
> - Timeline: 5 days for prototype
> - Cannot modify User model
> - Must maintain backward compatibility

> **Available Tools**:
> - ✅ Node.js, npm, Git, PostgreSQL
> - ❌ Need to install Passport.js
> - ❌ Need Google OAuth credentials

> **Estimated Effort**: 2-3 days (fits within deadline)

> Does this match your understanding? Any corrections before I create the detailed plan?
```

**User response options**:
- ✅ "Yes, looks good" → Proceed to Phase 2
- 🔄 "Change X" → Adjust and re-confirm
- ❌ "This won't work because..." → Revise approach

---

## Phase 1 Outputs

At the end of Phase 1, you should have:

**1. Clear Goal Statement**
```
Goal: Add OAuth2 authentication with Google provider to API
Success: Users can log in with Google, existing sessions work
```

**2. Project Identification**
```
Project: authentication-system
Plans saved to: /projects/authentication-system/plans/
```

**3. Context Summary**
```
Current State: Express sessions, local auth
Tech Stack: Node.js 18, Express 4, PostgreSQL 12
Key Files: routes/auth.js, models/User.js, middleware/auth.js
```

**4. Tool Inventory**
```
Available: Node.js, npm, Git, PostgreSQL, Jest
Missing: Passport.js (will install), Google OAuth creds (will create)
Constraints: Cannot modify User model, must keep sessions working
```

**5. Strategy Selection**
```
Strategy: Decompose-First
Rationale: Well-defined problem, clear requirements, known approach
```

**6. Feasibility Confirmation**
```
Feasible: ✅ Yes
Estimated: 2-3 days
Deadline: 5 days
Blockers: None (credentials can be created same day)
```

**7. User Approval**
```
User confirmed: All details correct, proceed to detailed planning
```

---

## Common Issues & Solutions

**Vague goal** ("Make app better"): Ask for specifics - performance, UI, features, reliability, or security?

**Unclear strategy** ("Fix production issues"): Determine if known issue (decompose-first) or need investigation (interleaved)

**Conflicting constraints** (Database migration tomorrow, needs 2 weeks): Present options - extend timeline, reduce scope, different approach, or emergency path

**Missing critical tool** (Need Docker, can't install): Options - request exception, alternative testing, test in staging, or revise approach

---

## Validation Checklist

Before moving to Phase 2, verify:

- [ ] **Goal is clear**: One sentence, specific outcome
- [ ] **Project identified**: Know where to save plan
- [ ] **Success criteria defined**: Can verify when done
- [ ] **Constraints documented**: Know limitations
- [ ] **Context explored**: Reviewed relevant code/files
- [ ] **Tools validated**: Explicit inventory, no hallucinations
- [ ] **Strategy selected**: Matches task nature
- [ ] **Feasibility confirmed**: Can be done with available resources
- [ ] **User approved**: Confirmed understanding

**If all checked**: ✅ Ready for Phase 2 (Plan Creation)

**If any missing**: Return to that step, gather info, then proceed

---

## Time Management

**Typical Phase 1 timing**:
- Interactive Q&A: 3-5 minutes
- Context exploration: 3-5 minutes
- Tool validation: 2-3 minutes
- Constraint identification: 1-2 minutes
- Strategy selection: 1-2 minutes
- Feasibility check: 1-2 minutes
- Summary & approval: 1-2 minutes

**Total**: 10-15 minutes

**If taking longer**:
- Complex context: +5 minutes (large codebase)
- Tool issues: +5 minutes (missing dependencies)
- Feasibility concerns: +10 minutes (need alternatives)

**Maximum reasonable time**: 30 minutes

If Phase 1 is taking >30 minutes, likely the problem is:
- Goal too broad (need to narrow scope)
- Context too complex (need to focus on relevant subset)
- Missing information (need user to provide more details)

---

## Next Steps

After completing Phase 1:

1. **Review outputs**: Confirm all 7 outputs present
2. **Save notes**: Document findings (will include in plan)
3. **Proceed to Phase 2**: Begin detailed plan creation

**→ Continue to**: [[phase-2-plan-creation]]
