# Phase 3: Plan Finalization

**Purpose**: Save plan file and prepare for execution.

**Time**: 5-10 minutes

**Your role**: Review saved plan location, prepare to execute

**Output**: Plan file saved to `/projects/[project-name]/plans/`, ready to start work

---

## Overview

Phase 3 takes the approved plan from Phase 2 and finalizes it: saving to the correct location, linking to relevant resources, and providing clear execution guidance. This phase ensures the plan is persistent, discoverable, and actionable.

**What makes Phase 3 effective**:
- Consistent storage location (all plans in `/projects/`)
- Standard format (Markdown + YAML frontmatter)
- Proper linking (context, code, documentation)
- Clear next steps (execution guidance)
- Optional setup (git branch, reminders)

---

## Step-by-Step Workflow

### Step 1: Save Plan to File

**Goal**: Write plan to persistent storage in standard location

**Storage location**: `/projects/[project-name]/plans/[plan-name]-[YYYY-MM-DD].md`

**Evidence**: Research shows centralized, version-controllable plan storage improves discoverability and LLM-accessibility.

**Process**:

#### 1.1 Verify Project Directory

```bash
# Check if project directory exists
ls -la /projects/[project-name]/

# If not exists, create it
mkdir -p /projects/[project-name]/plans/
```

**Project directory structure**:
```
/projects/
  [project-name]/
    plans/                    # All plans for this project
      [plan-name]-YYYY-MM-DD.md
      replan-[reason]-YYYY-MM-DD.md
    context/                  # Project-specific context (optional)
      requirements.md
      decisions.md
    resources/                # Project resources (optional)
```

#### 1.2 Generate Plan Filename

**Naming convention**: `[descriptive-name]-[YYYY-MM-DD].md`

**Good names** (specific, descriptive):
- `oauth2-migration-2026-02-08.md`
- `database-performance-optimization-2026-02-08.md`
- `replan-after-api-changes-2026-02-10.md`

**Avoid** (vague, generic):
- `plan.md` (not descriptive)
- `my-plan-1.md` (not meaningful)
- `2026-02-08.md` (date only, no context)

**Naming logic**:
1. Take goal statement from Phase 1
2. Convert to kebab-case
3. Keep concise (3-5 words)
4. Add date suffix

**Example**:
```
Goal: "Add OAuth2 authentication to API"
→ oauth2-authentication-2026-02-08.md
```

#### 1.3 Write Plan File

**Use plan template** from [[plan-template]].

**Frontmatter** (YAML):
```yaml
---
title: "[Descriptive Plan Name]"
project: "[project-name]"
created: YYYY-MM-DD
updated: YYYY-MM-DD
status: approved
version: 1.0
goal: "[One-sentence goal from Phase 1]"
estimated_duration: "[hours/days from Phase 2]"
complexity: low | medium | high
strategy: decompose-first | interleaved | milestone-based
tags: [planning, feature-name, ...]
---
```

**Body sections**:
1. Goal (with success criteria)
2. Context (background, constraints, assumptions)
3. Available Tools (from Phase 1)
4. Milestones (with tasks and actions from Phase 2)
5. Dependencies & Sequencing (from Phase 2)
6. Risks & Mitigation (from Phase 2)
7. Replanning Triggers
8. Quality Validation (5-dimension checklist)
9. Approval (user approved date)
10. Execution Log (for tracking during execution)
11. Notes (additional context, references)

**Write command**:
```bash
# Plan content prepared in memory
Write /projects/[project-name]/plans/[plan-name]-[date].md
```

---

### Step 2: Link Resources

**Goal**: Connect plan to related context, code, and documentation

#### 2.1 Link to Context Files

**Context system links** (wikilinks):
```markdown
## Related Context

**Project Context**:
- [[projects/[project-name]/context/requirements]]
- [[projects/[project-name]/context/decisions]]

**Domain Standards**:
- [[context/security/oauth-best-practices]]
- [[context/python/coding-conventions]]
```

**Why link to context**:
- Future LLMs can load relevant context
- Humans can navigate related information
- Creates knowledge graph across vault

#### 2.2 Link to Code Files

**Code references** (file paths):
```markdown
## Related Code

**Entry points**:
- `src/server.js` - Main server file
- `src/routes/auth.js` - Current auth implementation

**Key modules**:
- `src/models/User.js` - User model
- `src/middleware/auth.js` - Auth middleware
```

**Why link to code**:
- Execution can quickly locate relevant files
- Documents what parts of codebase are affected
- Helps with resumability (if interrupted)

#### 2.3 Link to Documentation

**External documentation**:
```markdown
## External Resources

**Provider Documentation**:
- [Auth0 Documentation](https://auth0.com/docs)
- [OAuth 2.0 Specification](https://oauth.net/2/)

**Internal Documentation**:
- `docs/authentication.md` - Current auth docs
- `docs/api-reference.md` - API endpoints
```

**Why link to docs**:
- Quick reference during execution
- Validates feasibility (docs exist)
- Helps onboarding if others work on plan

---

### Step 3: Provide Execution Guidance

**Goal**: Give clear next steps for plan execution

**Execution guidance format**:

```markdown
## Execution Guidance

### Getting Started

1. **Review full plan**: Read complete plan file (not just summary)
2. **Set up environment**: Ensure all tools from "Available Tools" section are ready
3. **Create git branch** (optional): `git checkout -b feature/oauth2-authentication`
4. **Start Milestone 1**: Begin with first task

### Tracking Progress

**Update execution log as you work**:
```markdown
### [YYYY-MM-DD] - Milestone 1 Started
- Current task: Task 1.1
- Status: In progress
- Notes: [any deviations or discoveries]
```

**After each milestone**:
- Review at milestone boundary
- Assess: on track or need replan?
- Update status in frontmatter if needed

### Replanning Triggers

**When to create new plan version**:
- Any milestone takes >2x estimated time
- Required tool becomes unavailable
- Unexpected blocker discovered
- Requirements change significantly

**Replanning process**:
1. Stop at milestone boundary
2. Document what changed in current plan
3. Run `/planner --replan`
4. Get user approval for new direction

### Next Steps

**Immediate actions**:
1. Start with Milestone 1, Task 1.1
2. Use tools validated in Phase 1
3. Update execution log as you progress
4. Commit changes regularly
```

---

### Step 4: Optional Setup

**Goal**: Set up tooling and notifications for plan execution

#### 4.1 Create Git Branch (Recommended)

**If plan involves code changes**:
```bash
# Create feature branch from plan name
git checkout -b feature/[plan-name]

# Example
git checkout -b feature/oauth2-authentication
```

**Benefits**:
- Isolates work from main branch
- Enables review before merging
- Easy to revert if needed
- Tracks all plan-related commits

**Document in plan**:
```markdown
## Git Branch

**Branch created**: `feature/oauth2-authentication`
**Base branch**: `main`
**Created**: 2026-02-08
```

#### 4.2 Set Reminders (Optional)

**For long-horizon plans**:
```markdown
## Milestones & Deadlines

- [ ] Milestone 1: Design OAuth2 Flow (due: 2026-02-09)
- [ ] Milestone 2: Implement Integration (due: 2026-02-10)
- [ ] Milestone 3: Testing (due: 2026-02-11)
- [ ] Milestone 4: Deployment (due: 2026-02-12)
```

**Set calendar reminders** (outside of plan file):
- Milestone review dates
- Checkpoint meetings (if team project)
- Deadline alerts

#### 4.3 Share with Team (If Collaborative)

**If working with others**:
```bash
# Commit plan to git
git add /projects/[project-name]/plans/[plan-name].md
git commit -m "docs: add plan for [goal]"
git push origin main

# Share plan file location with team
# Team members can review and provide feedback
```

**Benefits**:
- Team alignment on approach
- Collaborative review
- Shared execution tracking
- Distributed work (if tasks parallelizable)

---

## Phase 3 Outputs

At the end of Phase 3, you should have:

**1. Plan File Saved**
```
/projects/[project-name]/plans/[plan-name]-YYYY-MM-DD.md
```

**2. Proper Linking**
- Context files linked (wikilinks)
- Code files referenced (file paths)
- Documentation linked (URLs/paths)

**3. Execution Guidance**
- Clear next steps defined
- Tracking process documented
- Replanning triggers specified

**4. Optional Setup Complete**
- Git branch created (if code changes)
- Reminders set (if long-horizon)
- Team notified (if collaborative)

**5. Ready to Execute**
- User knows where plan is saved
- User knows how to start
- User knows how to track progress

---

## Common Issues & Solutions

### Issue: "Can't find plan file after saving"

**Cause**: Wrong project name, incorrect path, typo in filename

**Solution**:
```bash
# List all plans across all projects
ls /projects/*/plans/*.md

# Find most recent plan
ls -t /projects/*/plans/*.md | head -1

# Search by keyword
find /projects -name "*oauth*"
```

**Prevention**: Echo filepath after saving, verify in tool output

---

### Issue: "Wikilinks not resolving"

**Cause**: Incorrect wikilink syntax, referenced file doesn't exist

**Solution**:
- Use exact filename without extension: `[[context/security/oauth-best-practices]]`
- Verify file exists: `ls /context/security/oauth-best-practices.md`
- Check for typos in path

**Prevention**: Verify all wikilinks after creating plan

---

### Issue: "Git branch creation failed"

**Cause**: Uncommitted changes, branch name conflict, not in git repo

**Solution**:
```bash
# Check git status
git status

# Commit or stash changes first
git stash

# Try different branch name if conflict
git checkout -b feature/oauth2-authentication-v2
```

**Prevention**: Check git status before creating branch

---

### Issue: "Execution log not being updated"

**Cause**: User forgets to update, unclear how to update

**Solution**:
- Remind user at each milestone boundary
- Provide example log entry
- Make log section prominent in plan template

**Prevention**: Include log template in execution guidance

---

## Time Management

**Typical Phase 3 timing**:
- Save plan to file: 2-3 minutes
- Link resources: 2-3 minutes
- Execution guidance: 1-2 minutes
- Optional setup: 2-5 minutes

**Total**: 5-10 minutes (15 minutes with full optional setup)

**If taking longer**:
- Complex linking (+5 minutes): Many context files to link
- Git issues (+5 minutes): Branch conflicts, merge needed
- Team coordination (+10 minutes): Sharing, discussion

**Maximum reasonable time**: 20 minutes

---

## Next Steps

After completing Phase 3:

1. **Confirm plan saved**: User verifies file location
2. **Review plan file**: User reads complete plan (not just summary)
3. **Begin execution**: Start with Milestone 1, Task 1.1
4. **Track progress**: Update execution log regularly

**Plan is complete! Ready for execution.**

---

## Maintenance During Execution

**Update execution log regularly**:
- After each task: Document actual time, output, deviations
- After each milestone: Review status, assess if on track or need replan
- When complete: Final retrospective, extract learnings with `/context-curator`

**When to replan**:
- Milestone takes >2x estimated time
- Major blocker discovered
- Requirements changed

**Replan process**: Stop at milestone boundary, document deviation, run `/planner --replan`

---

**Phase 3 complete! Plan is saved and ready for execution.**
