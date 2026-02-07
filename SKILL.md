---
name: init-context-system
description: "Set up a context management system for persistent Claude preferences, decisions, and workflows"
allowed-tools: Read, Write, Edit, Glob, Grep, Bash, AskUserQuestion
---

# Context System Setup Skill

**Purpose**: Guide users through creating a context management system that makes Claude persistently remember their preferences, decisions, and workflows across conversations.

**Approach**: Progressive setup in three phases (Quick Setup → Hands-On → Evolution Framework). Each phase delivers immediate value and builds on the previous.

---

## Skill Invocation Patterns

### Full Setup (First Time)
User invokes: `/init-context-system`
→ Guide through Phase 1 → Phase 2 → Phase 3 (with approval gates)

### Resume at Phase
User invokes: `/init-context-system --phase 2`
→ Skip to specified phase (validate previous phases completed)

### Maintenance Operations
User invokes: `/init-context-system --extract`
→ Extract context from recent conversation

User invokes: `/init-context-system --validate`
→ Run validation checks on context system

User invokes: `/init-context-system --archive`
→ Archive outdated decisions/retrospectives

---

## Pre-Flight Checks

**Before starting any phase, verify**:

1. **Working directory**: User should be in a project root (has `.claude/` directory or can create one)
2. **Context system exists?**: Check if `context/` folder already exists
3. **User intent**: If context system exists, ask if they want to extend it or start fresh
4. **Read README**: If this is the first invocation, briefly mention the README exists at `.claude/skills/init-context-system/README.md` for reference

**If context system already exists**:
```
I notice you already have a context system. Would you like to:
1. Extend it (add more context)
2. Validate it (run quality checks)
3. Archive old content
4. Start fresh (rebuild from scratch)
```

---

## Phase 1: Quick Setup (15-30 min)

**Goal**: Create minimal context system and demonstrate immediate value.

**Expected outcome**: User has 3-5 context files, CLAUDE.md references context, Claude starts using preferences immediately.

---

### Step 1.1: Explain Phase 1

Say:
```
Let's set up your context management system in three phases. Phase 1 takes 15-30 minutes and gives you immediate value—Claude will start remembering your preferences right away.

We'll:
1. Create the folder structure
2. Extract 1-2 preferences from our conversation
3. Set up basic CLAUDE.md
4. Create a loading map so context loads automatically

Ready to begin?
```

Wait for user approval.

---

### Step 1.2: Create Folder Structure

Create these directories:
```
context/
├── communication/
├── project/
├── workflows/
└── decisions/
```

Use Bash: `mkdir -p context/{communication,project,workflows,decisions}`

Say:
```
✓ Created context folder structure

These folders organize context by purpose:
- communication/ → How you like to work with Claude
- project/ → Project-specific conventions and standards
- workflows/ → How to execute common tasks (git, testing, etc.)
- decisions/ → Architectural decisions (why you chose specific approaches)
```

---

### Step 1.3: Extract Initial Context from Conversation

**Ask the user**:
```
Let me extract some initial context from our conversation. To start, I'll identify 1-2 clear preferences or patterns.

Looking at our conversation so far, I see:
[List 1-3 patterns you've observed]

Which of these should I document first? (Choose 1-2)
```

Use AskUserQuestion to let user select which patterns to document first.

**Common patterns to look for**:
- Communication style (concise vs detailed, review-first vs action-first)
- Workflow preferences (propose before executing, explain reasoning)
- Tool preferences (specific tools, frameworks, approaches)
- Quality standards (testing requirements, code style, documentation)

---

### Step 1.4: Create First Context File(s)

Based on user selection, create 1-2 context files in appropriate folders.

**Use the template structure**:
```markdown
---
title: [Context Title]
created: [YYYY-MM-DD]
keywords: [keyword1, keyword2, keyword3]
applies-to: [task-type1, task-type2]
tags: [context, communication/project/workflows]
type: communication/project/workflows
---

# [Context Title]

## Summary

[One-paragraph summary of this context]

## Details

### [Key Point 1]

**Preference:** [Clear statement of preference]

**Pattern:**
[How this preference manifests in practice]

**Examples:**

**Good:**
```
[Example of following this preference]
```

**Avoid:**
```
[Example of NOT following this preference]
```

## Related Context

- [[Link to related context files]]

---

*Last updated: [YYYY-MM-DD]*
```

**After creating each file, show the user**:
```
Created: context/[folder]/[filename].md

[Show brief excerpt]

Does this accurately capture your preference?
```

Wait for user confirmation before proceeding.

---

### Step 1.5: Create Context Index

Create `context/_index.md` using this template:

```markdown
---
title: Context Index
tags: [context, moc]
created: [YYYY-MM-DD]
---

# Context Index

This folder contains context that helps Claude align with project intent and preferences. Context is gathered from our conversations to improve consistency and alignment over time.

---

## How Claude Uses This Context

### 1. Task-Based Loading

When you work on specific tasks, relevant context is loaded automatically via [[context/_loading-map]].

### 2. Explicit References

You can reference context explicitly: "As noted in [[context/communication/style-preferences]]..."

### 3. Progressive Growth

This system starts small and grows over time as we discover patterns and preferences through actual work.

---

## Communication

How Claude should communicate and format responses.

[List files created, e.g., - [[context/communication/style-preferences]] - Communication preferences]

## Project Knowledge

Project-specific conventions and standards.

[List files created in project/, or note "None yet - will add as conventions emerge"]

## Workflows

Common patterns and workflows.

[List files created in workflows/, or note "None yet - will add as workflows are documented"]

## Decisions

Architectural and process decisions.

[List files created in decisions/, or note "None yet - decisions will be logged as they're made"]

---

## Maintenance

**When to Update Context**:
- After discovering new preferences or patterns
- When making significant decisions
- Periodically reviewing conversations for insights

**How to Update**:
Use `/init-context-system --extract` to extract context from recent conversations, or manually create/update files following the template structure.

---

*Created: [YYYY-MM-DD]*
```

---

### Step 1.6: Create Loading Map

Create `context/_loading-map.md`:

```markdown
---
title: Context Loading Map
created: [YYYY-MM-DD]
keywords: [context-loading, task-mapping, automatic-context]
applies-to: [all-tasks]
tags: [context, meta]
---

# Context Loading Map

> When Claude is performing specific tasks, which context files are relevant?

This map helps Claude automatically load the right context for common workflows.

---

## Task: General Communication

**Load:**
[List the context files created in Phase 1, e.g., - [[context/communication/style-preferences]] - Your communication preferences]

**When:**
- Starting any conversation
- User asks for review or feedback
- User asks for explanations

---

## Adding More Task Mappings

As you create more context files, add task mappings here. Common task types:

- **Git Operations** → Load git workflow context
- **Creating Notes/Files** → Load project conventions, templates
- **Code Review** → Load critique preferences, quality standards
- **Testing** → Load testing standards, workflow
- **Documentation** → Load documentation standards

---

*Last updated: [YYYY-MM-DD]*
```

---

### Step 1.7: Update or Create CLAUDE.md

Check if `.claude/CLAUDE.md` exists:
- If **exists**: Add a section about the context system
- If **not exists**: Create minimal CLAUDE.md

**If creating new CLAUDE.md**:
```markdown
# Project Context

This project uses a context management system to help Claude remember preferences, decisions, and workflows across conversations.

## Context System

Context is organized in the `/context` folder:
- **[[context/communication/]]** - How to communicate and collaborate
- **[[context/project/]]** - Project conventions and standards
- **[[context/workflows/]]** - How to execute common tasks
- **[[context/decisions/]]** - Architectural decisions and rationale

## How It Works

1. **Task-Based Loading**: Context automatically loads based on what you're doing (see [[context/_loading-map]])
2. **Explicit References**: You can reference context in requests (e.g., "Follow [[context/communication/style-preferences]]")
3. **Progressive Growth**: System starts small, grows as we discover patterns

## Quick Reference

- [[context/_index]] - Full context index
- [[context/_loading-map]] - Task-to-context mappings

---

[Rest of your existing CLAUDE.md content, if any]
```

**If updating existing CLAUDE.md**:
Insert the context system section near the top (after any overview, before detailed sections).

---

### Step 1.8: Phase 1 Complete - Demonstrate Value

Say:
```
✓ Phase 1 Complete!

You now have a working context management system:

📁 Context structure created
📝 [N] context file(s) capturing your preferences:
   - [List files created]
🗺️ Loading map created (context loads automatically)
📖 CLAUDE.md updated (references context system)

**Immediate value**: In our next conversation, I'll automatically load your preferences without you having to remind me.

**Test it now**: Try asking me to do something, and I'll apply the context we just created.

---

Ready for Phase 2? (This demonstrates deeper value by showing task-based loading)

Options:
1. Continue to Phase 2 now (30-45 min)
2. Pause here, resume later with `/init-context-system --phase 2`
3. Skip Phase 2 and just use what we've built
```

Wait for user decision.

---

## Phase 2: Hands-On Learning (30-45 min)

**Goal**: Extract more context, create first decision log, set up task-based loading for common tasks. Demonstrate how context automatically loads.

**Expected outcome**: User has 8-12 context files, 1-2 decision logs, task-based loading for 2-3 common tasks (git, code review, documentation, etc.).

---

### Step 2.1: Explain Phase 2

Say:
```
Phase 2 builds on what we created. We'll:
1. Extract 3-5 more pieces of context from your project
2. Create your first decision log (ADR)
3. Set up task-based loading for common tasks (git, code review, etc.)
4. Show how context automatically loads when you work

This takes 30-45 minutes and demonstrates the real power of the system.

Ready?
```

Wait for approval.

---

### Step 2.2: Discover More Context

**Strategy**: Look for context in three places:

1. **Current conversation**: Patterns in how user has interacted with you
2. **CLAUDE.md**: Existing preferences or standards documented
3. **Project files**: Conventions evident in code, docs, or config files

**Approach**:
```
Let me discover more context by examining:
1. Our conversation (preferences you've expressed)
2. Your CLAUDE.md (documented standards)
3. Your project (conventions in code/docs)

This will take a moment...
```

Use Glob, Grep, and Read to explore:
- Read `.claude/CLAUDE.md` if it exists (extract conventions)
- Glob for common config files: `.prettierrc`, `.eslintrc`, `pyproject.toml`, etc. (extract standards)
- Look at conversation history for repeated patterns

**Present findings**:
```
I found [N] potential context items:

[List 5-7 items with brief descriptions]

Which of these should we document? (Choose 3-5)
```

Use AskUserQuestion to let user select items to document.

---

### Step 2.3: Create Additional Context Files

For each selected item, create appropriate context file:

- **Conventions** → `context/project/[convention-name].md`
- **Workflows** → `context/workflows/[workflow-name].md`
- **Standards** → `context/project/[standard-name].md`

Use the same template structure as Phase 1.

After creating each file:
1. Show brief summary
2. Ask for confirmation
3. Update `context/_index.md` to include the new file

---

### Step 2.4: Create First Decision Log

Say:
```
Decision logs (ADRs - Architectural Decision Records) document *why* you chose specific approaches. This prevents you from re-litigating decisions later.

Have you made any significant architectural or process decisions recently? Examples:
- "Use flat folder structure vs nested"
- "Use TypeScript over JavaScript"
- "Deploy to AWS Lambda vs EC2"
- "Use Obsidian wikilinks, not markdown links"
```

If user has a decision to document:

Create `context/decisions/YYYY-MM-DD-decision-title.md`:

```markdown
---
title: [Decision Title]
date: [YYYY-MM-DD]
status: accepted
tags: [context, decision, adr]
---

# [Decision Title]

**Date**: [YYYY-MM-DD]
**Status**: Accepted

---

## Context

What is the issue we're trying to address?

[Describe the problem or decision point]

---

## Decision

What approach did we choose?

[Clear statement of the decision]

---

## Rationale

Why did we choose this approach?

**Pros:**
- [Advantage 1]
- [Advantage 2]

**Cons:**
- [Tradeoff 1]
- [Tradeoff 2]

**Alternatives Considered:**
1. **[Alternative 1]**: [Why we didn't choose this]
2. **[Alternative 2]**: [Why we didn't choose this]

---

## Consequences

What are the implications of this decision?

**Positive:**
- [Positive consequence 1]

**Negative:**
- [Negative consequence or constraint 1]

**Neutral:**
- [Things that change but aren't good/bad]

---

## Related

- [[Link to related decisions or context]]

---

*Created: [YYYY-MM-DD]*
```

Show the user, get confirmation, then update `context/_index.md`.

---

### Step 2.5: Set Up Task-Based Loading

Say:
```
Now let's set up task-based loading. When you do specific tasks (git commits, code review, documentation), relevant context will automatically load.

Which tasks do you do regularly? (Choose 2-3)
```

Present options:
- Git operations (commits, PRs)
- Code review
- Creating documentation
- Writing tests
- Creating notes/files
- Other (user specifies)

For each selected task, update `context/_loading-map.md` with a task mapping:

```markdown
## Task: [Task Name]

**Load:**
- [[context/path/to/relevant-file]] - [Brief description]
- [[context/path/to/another-file]] - [Brief description]

**When:**
- [Trigger 1]
- [Trigger 2]
- [Trigger 3]

---
```

**Example mappings**:

**Git Operations**:
```markdown
## Task: Git Operations

**Load:**
- [[context/workflows/git-practices]] - Git workflow and commit conventions
- [[context/project/quality-standards]] - Quality gates before committing

**When:**
- User requests creating commits
- User requests creating pull requests
- /commit skill is invoked
- Working with version control

---
```

**Code Review**:
```markdown
## Task: Code Review

**Load:**
- [[context/communication/critique-preference]] - How to provide feedback
- [[context/project/quality-standards]] - What to review for
- [[context/workflows/review-process]] - Step-by-step review workflow

**When:**
- User requests reviewing code
- User asks for improvements or suggestions
- /review-pr skill is invoked

---
```

After adding task mappings, say:
```
✓ Task-based loading configured

Now when you [task 1], I'll automatically load [context files].
When you [task 2], I'll load [different context files].

Want to test it? Try asking me to [example task], and watch the context load automatically.
```

---

### Step 2.6: Create Workflow Context (If Needed)

If user selected git operations or other workflow-heavy tasks, offer to create workflow context:

```
I notice you selected [task]. Would you like me to create a workflow document for this? It would capture:
- Step-by-step process
- Quality checkpoints
- Common pitfalls
- Best practices
```

If yes, create `context/workflows/[workflow-name].md` with structure:

```markdown
---
title: [Workflow Name]
created: [YYYY-MM-DD]
keywords: [workflow, process, [domain]]
applies-to: [[task-type]]
tags: [context, workflows]
type: workflows
---

# [Workflow Name]

## Summary

[One-paragraph overview of this workflow]

## When to Use

[Describe situations where this workflow applies]

## Process

### Step 1: [Step Name]

[Description]

**Actions:**
- [Action 1]
- [Action 2]

**Checkpoints:**
- ✓ [Validation 1]
- ✓ [Validation 2]

### Step 2: [Step Name]

[Continue for each step]

## Common Pitfalls

**Pitfall 1**: [Description]
**How to avoid**: [Prevention strategy]

## Best Practices

- [Best practice 1]
- [Best practice 2]

## Related Context

- [[Link to related workflows or standards]]

---

*Last updated: [YYYY-MM-DD]*
```

---

### Step 2.7: Update Index and Validate

1. Update `context/_index.md` with all new files created in Phase 2
2. Run a quick validation:
   - Check all wikilinks resolve
   - Verify frontmatter is present on all files
   - Ensure _loading-map references valid files

Report any issues found and fix them.

---

### Step 2.8: Phase 2 Complete - Demonstrate Value

Say:
```
✓ Phase 2 Complete!

Context system expanded:
📝 [N] total context files (added [X] in Phase 2)
📋 [N] decision logs documenting architectural choices
🗺️ Task-based loading configured for:
   - [Task 1]
   - [Task 2]
   - [Task 3]

**Test the system**: Try one of these:
- "Create a git commit for [files]" → Git context loads automatically
- "Review this code" → Review context loads automatically
- [Other example based on tasks configured]

---

Ready for Phase 3? (This sets up long-term evolution)

Options:
1. Continue to Phase 3 now (15-30 min)
2. Pause here, resume later with `/init-context-system --phase 3`
3. Stop here and use what we've built (Phase 3 is optional)
```

Wait for user decision.

---

## Phase 3: Evolution Framework (15-30 min)

**Goal**: Establish processes for long-term maintenance and evolution of the context system.

**Expected outcome**: User has retrospective workflow, maintenance checklist, validation process. System can evolve over time without decay.

---

### Step 3.1: Explain Phase 3

Say:
```
Phase 3 is about long-term sustainability. We'll set up:
1. Retrospective workflow (capture learnings after major work)
2. Maintenance checklist (keep context fresh)
3. Validation process (ensure quality)

This takes 15-30 minutes and ensures your context system stays valuable long-term.

Ready?
```

Wait for approval.

---

### Step 3.2: Create Retrospective Workflow

Create `context/workflows/retrospective-workflow.md`:

```markdown
---
title: Retrospective Workflow
created: [YYYY-MM-DD]
keywords: [retrospective, reflection, learnings, context-extraction]
applies-to: [context-maintenance, after-major-work]
tags: [context, workflows]
type: workflows
---

# Retrospective Workflow

## Summary

After major work sessions, capture learnings through retrospectives. This prevents valuable patterns from being lost and helps the context system evolve.

## When to Create a Retrospective

**Triggers:**
- Completed multi-hour work session (2+ hours)
- Finished a significant milestone (shipped feature, completed project phase)
- Discovered new patterns or approaches
- Encountered repeated issues that need documentation

**Frequency:**
- Minimum: Monthly
- Recommended: After each major work session
- Opportunistic: Whenever you notice "I should document this"

## Process

### Step 1: Reflect on the Session

Ask yourself:
- What did we accomplish?
- What went well?
- What could improve?
- What patterns emerged?
- What should we remember for next time?

### Step 2: Use the Retrospective Extraction Command

```bash
/init-context-system --extract
```

This will:
1. Review recent conversation
2. Identify patterns and learnings
3. Suggest context to extract or update
4. Create a retrospective document

### Step 3: Review and Refine

Claude will propose context extractions. Review each:
- Does this pattern actually exist?
- Is it specific enough to be actionable?
- Does it belong in context (vs project docs)?

### Step 4: Update Context System

For each validated learning:
- Create new context file (if new pattern)
- Update existing file (if refinement)
- Create decision log (if architectural choice)
- Update loading map (if new task mapping)

### Step 5: Archive the Retrospective

Move retrospective to `context/workflows/retrospectives/`:
- Active retrospectives: `context/workflows/retrospectives/YYYY-MM-DD-topic.md`
- Archived (after extraction): `context/workflows/retrospectives/archive/YYYY/`

## Best Practices

**Do:**
- Extract context while session is fresh
- Focus on patterns, not one-off situations
- Include examples (good and bad)
- Link to related context

**Don't:**
- Extract every conversation detail (signal vs noise)
- Create hypothetical context ("might need this later")
- Duplicate what's already documented
- Skip the extraction step (you'll forget)

## Related Context

- [[context/project/context-governance]] - What is/isn't context
- [[context/_loading-map]] - Where to add new task mappings

---

*Last updated: [YYYY-MM-DD]*
```

---

### Step 3.3: Create Maintenance Checklist

Create `context/workflows/maintenance-checklist.md`:

```markdown
---
title: Context System Maintenance Checklist
created: [YYYY-MM-DD]
keywords: [maintenance, validation, quality, context-health]
applies-to: [context-maintenance]
tags: [context, workflows]
type: workflows
---

# Context System Maintenance Checklist

## Summary

Regular maintenance keeps the context system valuable. Run these checks periodically to ensure quality.

## Maintenance Schedule

**Weekly** (if using daily):
- Quick scan: Any repeated clarifications? → Extract context

**Monthly**:
- Run validation checks
- Review recent retrospectives
- Update stale context

**Quarterly**:
- Archive old decisions/retrospectives
- Refactor large files (split if >300 lines)
- Prune unused context

**Annually**:
- Full audit: Does context still reflect reality?
- Major refactoring if needed

## Validation Checks

### Automated Checks (via `/init-context-system --validate`)

Run: `/init-context-system --validate`

This checks:
- ✓ All wikilinks resolve
- ✓ All context files have frontmatter
- ✓ Loading map references valid files
- ✓ No duplicate file names
- ✓ File sizes (warn if >300 lines)

### Manual Checks

**1. Accuracy**
- [ ] Context still reflects current preferences?
- [ ] Decisions still valid (not superseded)?
- [ ] Workflows match actual practice?

**2. Completeness**
- [ ] New patterns discovered recently? → Extract them
- [ ] Recurring questions? → Document answers
- [ ] New tasks need loading map entries?

**3. Quality**
- [ ] Examples clear and helpful?
- [ ] No vague or ambiguous statements?
- [ ] Related context linked appropriately?

**4. Organization**
- [ ] Files in correct folders?
- [ ] Index up to date?
- [ ] Loading map complete?

## Archival Process

### When to Archive

**Archive decisions** when:
- Decision superseded by newer decision
- Decision no longer relevant (tech/approach changed)
- Keep for history but not active reference

**Archive retrospectives** when:
- Learnings extracted into permanent context
- >6 months old and no longer referenced
- Historical record but not active guidance

### How to Archive

Run: `/init-context-system --archive`

Or manually:
```bash
mkdir -p context/workflows/retrospectives/archive/[YEAR]
mkdir -p context/decisions/archive/[YEAR]

# Move old files
mv context/decisions/YYYY-MM-DD-old-decision.md context/decisions/archive/YYYY/
```

Update `context/_index.md` to move archived items to "Archived" section.

## Refactoring Large Files

If context file exceeds ~300 lines:

**Option 1: Split into Overview + Details**
- Create overview file (summary, links to details)
- Create detail files (focused subtopics)
- Update loading map to reference both

**Example:**
```
Before: context/project/conventions.md (500 lines)

After:
- context/project/conventions.md (overview, 100 lines)
- context/project/conventions-formatting.md (150 lines)
- context/project/conventions-naming.md (150 lines)
- context/project/conventions-organization.md (150 lines)
```

**Option 2: Extract Distinct Topics**
- Identify separate concerns in large file
- Split into separate files by topic
- Update cross-references

## Quick Maintenance Commands

```bash
# Extract context from recent conversation
/init-context-system --extract

# Validate context system
/init-context-system --validate

# Archive old content
/init-context-system --archive

# Full system (all checks + cleanup)
/init-context-system --maintain
```

---

*Last updated: [YYYY-MM-DD]*
```

---

### Step 3.4: Create Context Governance Document

Create `context/project/context-governance.md`:

```markdown
---
title: Context System Governance
created: [YYYY-MM-DD]
keywords: [context-governance, boundaries, standards, what-is-context]
applies-to: [context-creation, context-maintenance]
tags: [context, project, meta]
type: project
---

# Context System Governance

## Summary

Guidelines for what belongs in the context system and how to maintain quality.

## What Is Context?

**Context is**: Instructions for how Claude should work with you on this project.

**Context includes:**
- ✅ Your preferences (communication style, workflow patterns)
- ✅ Architectural decisions (why you chose specific approaches)
- ✅ Project conventions (standards, naming, organization)
- ✅ Workflows (how to execute common tasks)
- ✅ Quality standards (what "done" means)

**Context is NOT:**
- ❌ Public-facing documentation (use README, docs/)
- ❌ General knowledge or tutorials (use wiki, learning/)
- ❌ Project planning or status (use project management tools)
- ❌ Code or implementation details (use source files)
- ❌ One-off instructions (just tell Claude directly)

**Rule of thumb**: If you'd need to re-explain it to Claude in a new conversation, it's context. If it's for other humans or external audiences, it's not.

## Boundaries

### Communication vs Project vs Workflows

**Communication** (`context/communication/`):
- How you like to collaborate
- Feedback and critique style
- Response formatting
- Teaching vs doing balance

**Project** (`context/project/`):
- Conventions and standards
- Quality requirements
- Technology choices
- Organizational structure

**Workflows** (`context/workflows/`):
- Step-by-step processes
- How to execute tasks
- Quality checkpoints
- Common patterns

### Decisions vs Workflows vs Context

**Decision** (ADR):
- **What**: A significant architectural or process choice
- **Why**: Multiple valid options, chose one for specific reasons
- **When to create**: When you make a consequential decision
- **Example**: "Use flat folder structure with MOCs for navigation"

**Workflow**:
- **What**: Step-by-step process for executing a task
- **Why**: Ensure consistency and quality
- **When to create**: When you do a task repeatedly
- **Example**: "How to create a git commit with tests and quality checks"

**Context** (other):
- **What**: Preferences, conventions, standards
- **Why**: Align Claude with your style
- **When to create**: When you notice recurring patterns
- **Example**: "Use lowercase tags throughout project"

## Quality Standards

### All Context Files Must Have

1. **Frontmatter**:
   ```yaml
   ---
   title: [Clear title]
   created: [YYYY-MM-DD]
   keywords: [keyword1, keyword2]
   applies-to: [task-type1, task-type2]
   tags: [context, communication/project/workflows]
   type: communication/project/workflows
   ---
   ```

2. **Summary section**: One-paragraph overview

3. **Clear examples**: Show good and bad patterns

4. **Related context**: Link to related files

5. **Last updated date**: At bottom of file

### Context Should Be

- **Specific**: "Use lowercase tags" not "use consistent formatting"
- **Actionable**: Clear enough for Claude to apply
- **Evidence-based**: Extracted from real work, not hypothetical
- **Maintainable**: Easy to update when preferences change

### Context Should NOT Be

- **Vague**: "Write good code" (what does "good" mean?)
- **Obvious**: "Use proper grammar" (Claude already does this)
- **Contradictory**: Check for conflicts with existing context
- **Stale**: Update or archive outdated content

## Creation Process

1. **Identify pattern**: Notice recurring preference or decision
2. **Validate**: Is this a real pattern or one-off situation?
3. **Choose location**: communication/ project/ workflows/ decisions/?
4. **Use template**: Follow template structure
5. **Include examples**: Show good and bad patterns
6. **Link related context**: Cross-reference related files
7. **Update index**: Add to `context/_index.md`
8. **Update loading map**: Add task mapping if applicable

## Maintenance Process

1. **Extract regularly**: After major work sessions
2. **Validate periodically**: Run `/init-context-system --validate`
3. **Archive outdated**: Move old decisions/retrospectives
4. **Refactor large files**: Split if >300 lines
5. **Update as needed**: Preferences change, context should too

## Related Context

- [[context/_index]] - Context system overview
- [[context/_loading-map]] - Task-based context loading
- [[context/workflows/retrospective-workflow]] - How to extract context
- [[context/workflows/maintenance-checklist]] - Maintenance schedule

---

*Last updated: [YYYY-MM-DD]*
```

---

### Step 3.5: Create Templates for Future Use

Create `context/templates/` folder with reusable templates:

```bash
mkdir -p context/templates
```

**Template 1**: `context/templates/context-template.md`
```markdown
---
title: [Context Title]
created: [YYYY-MM-DD]
keywords: [keyword1, keyword2, keyword3]
applies-to: [task-type1, task-type2]
tags: [context, communication/project/workflows]
type: communication/project/workflows
---

# [Context Title]

## Summary

[One-paragraph summary]

## Details

### [Key Point]

**Preference/Pattern**: [Clear statement]

**In practice:**
[How this manifests]

**Examples:**

**Good:**
```
[Example following this]
```

**Avoid:**
```
[Example not following this]
```

## Related Context

- [[Link to related context]]

---

*Last updated: [YYYY-MM-DD]*
```

**Template 2**: `context/templates/decision-template.md`
(Use the ADR template from Step 2.4)

**Template 3**: `context/templates/workflow-template.md`
(Use the workflow template from Step 2.6)

---

### Step 3.6: Update Loading Map for Maintenance Tasks

Add to `context/_loading-map.md`:

```markdown
## Task: Context System Maintenance

**Load:**
- [[context/project/context-governance]] - What is/isn't context
- [[context/workflows/retrospective-workflow]] - How to extract context
- [[context/workflows/maintenance-checklist]] - Validation and maintenance
- [[context/templates/]] - Templates for creating new context

**When:**
- User invokes `/init-context-system --extract`
- User invokes `/init-context-system --validate`
- User invokes `/init-context-system --archive`
- User asks about updating or maintaining context

---
```

---

### Step 3.7: Create Quick Reference Card

Create `context/QUICK-REFERENCE.md`:

```markdown
# Context System Quick Reference

## Daily Use

**Extract context from conversation:**
```bash
/init-context-system --extract
```

**Reference context in requests:**
```
"Follow [[context/communication/style-preferences]] when responding"
"Use the workflow from [[context/workflows/git-practices]]"
```

## Maintenance

**Validate context system:**
```bash
/init-context-system --validate
```

**Archive old content:**
```bash
/init-context-system --archive
```

**Full maintenance (validate + archive + cleanup):**
```bash
/init-context-system --maintain
```

## Creating New Context

**1. Identify the type:**
- Communication → `context/communication/`
- Convention → `context/project/`
- Workflow → `context/workflows/`
- Decision → `context/decisions/`

**2. Use template:**
- Copy from `context/templates/context-template.md`
- Fill in frontmatter and content
- Include examples (good and bad)

**3. Integrate:**
- Update `context/_index.md`
- Add to `context/_loading-map.md` if task-specific
- Link from related context files

## File Structure

```
context/
├── _index.md              # Main index
├── _loading-map.md        # Task → context mappings
├── QUICK-REFERENCE.md     # This file
│
├── communication/         # How to interact
├── project/              # Conventions & standards
├── workflows/            # How to do work
├── decisions/            # Architectural decisions
└── templates/            # Templates for new context
```

## Common Tasks

**Add new preference:**
1. Create file in `context/communication/`
2. Update `context/_index.md`
3. Add to loading map if task-specific

**Document decision:**
1. Create ADR in `context/decisions/YYYY-MM-DD-title.md`
2. Use decision template
3. Update `context/_index.md`

**Create workflow:**
1. Create file in `context/workflows/`
2. Use workflow template
3. Add task mapping to loading map

**Split large file (>300 lines):**
1. Create overview file (summary + links)
2. Create focused detail files
3. Update all cross-references
4. Update loading map

## Getting Help

- Read [[context/_index]] for full documentation
- Check [[context/project/context-governance]] for boundaries
- Review [[context/workflows/maintenance-checklist]] for maintenance

---

*Created: [YYYY-MM-DD]*
```

---

### Step 3.8: Phase 3 Complete - Long-Term Success

Say:
```
✓ Phase 3 Complete!

Your context system is now fully set up for long-term success:

📋 Retrospective workflow established
✅ Maintenance checklist created
📖 Governance guidelines documented
📄 Templates available for future context
🔧 Maintenance commands configured

**Long-term sustainability:**
- After major work: `/init-context-system --extract` (capture learnings)
- Monthly: `/init-context-system --validate` (ensure quality)
- Quarterly: `/init-context-system --archive` (remove stale content)

**Your context system now:**
- Remembers your preferences across conversations ✓
- Loads context automatically based on tasks ✓
- Captures decisions and rationale ✓
- Evolves with you through retrospectives ✓
- Stays maintainable through validation ✓

**Quick Reference**: See `context/QUICK-REFERENCE.md` for common commands

---

🎉 Setup complete! Your context system is ready to use.

**Test it**: Start a new conversation and notice how I remember your preferences without you having to remind me.

**Next steps**:
1. Use the system naturally
2. Run `/init-context-system --extract` after major work
3. Watch your context library grow over time

Questions about using the system?
```

---

## Maintenance Operations

### Extract Context (`/init-context-system --extract`)

**Purpose**: Extract context from recent conversation or work session

**Process**:
1. Ask user: "How far back should I look?" (current conversation, last week, specific timeframe)
2. Review conversation/commits/files from that period
3. Identify patterns:
   - Repeated preferences
   - Decisions made
   - Workflows followed
   - Conventions applied
4. Present findings:
   ```
   I identified [N] potential context items:

   1. [Pattern 1] - Would document as [file name]
   2. [Pattern 2] - Would update [existing file]
   3. [Decision] - Would create ADR

   Which should I extract?
   ```
5. For each selected:
   - Create new file OR update existing
   - Update index if new
   - Update loading map if task-specific
6. Offer to create retrospective document
7. Summarize what was extracted

---

### Validate Context (`/init-context-system --validate`)

**Purpose**: Run quality checks on context system

**Checks**:

1. **Structure validation**:
   - ✓ Required folders exist (communication, project, workflows, decisions)
   - ✓ `_index.md` exists
   - ✓ `_loading-map.md` exists

2. **File validation**:
   - ✓ All context files have frontmatter
   - ✓ Frontmatter has required fields (title, created, keywords, applies-to, tags, type)
   - ✓ Files have summary section
   - ⚠️ Warn if file >300 lines (suggest splitting)

3. **Link validation**:
   - ✓ All wikilinks in context files resolve
   - ✓ Loading map references valid files
   - ✓ Index lists all context files
   - ⚠️ Warn about orphaned files (not referenced anywhere)

4. **Content validation**:
   - ⚠️ Files without examples (suggest adding)
   - ⚠️ Files without "Related Context" section
   - ⚠️ Vague or ambiguous language (manual review needed)

5. **Freshness validation**:
   - ⚠️ Files not updated in >6 months (may be stale)
   - ⚠️ Decisions without status field
   - ⚠️ Retrospectives not archived after extraction

**Report format**:
```
Context System Validation Report
================================

✅ PASSED (12 checks)
⚠️ WARNINGS (3 issues)
❌ ERRORS (0 critical issues)

Warnings:
─────────
⚠️ context/project/conventions.md is 427 lines (recommend splitting)
⚠️ context/communication/style-preferences.md missing examples
⚠️ context/decisions/2024-01-15-old-decision.md not updated in 8 months (archive?)

Recommendations:
────────────────
1. Split large files using overview + details pattern
2. Add examples to style-preferences.md
3. Review old decision - still valid or archive?

Run `/init-context-system --archive` to archive old content.
```

If errors found, offer to fix them.

---

### Archive Content (`/init-context-system --archive`)

**Purpose**: Move outdated decisions and retrospectives to archive folders

**Process**:
1. Scan for archival candidates:
   - Decisions >1 year old with status "superseded" or "deprecated"
   - Retrospectives >6 months old with learnings extracted
   - Any files user manually marks for archival

2. Present candidates:
   ```
   Found [N] items that could be archived:

   Decisions:
   - [Decision 1] ([date]) - [reason to archive]
   - [Decision 2] ([date]) - [reason to archive]

   Retrospectives:
   - [Retro 1] ([date]) - learnings extracted to [context files]
   - [Retro 2] ([date]) - learnings extracted to [context files]

   Archive these items?
   ```

3. For each item to archive:
   ```bash
   # Create archive folder if needed
   mkdir -p context/decisions/archive/[YEAR]
   mkdir -p context/workflows/retrospectives/archive/[YEAR]

   # Move files
   mv context/decisions/[file].md context/decisions/archive/[YEAR]/
   mv context/workflows/retrospectives/[file].md context/workflows/retrospectives/archive/[YEAR]/
   ```

4. Update `context/_index.md`:
   - Move archived items to "Archived" section
   - Add note about archive location

5. Update any references to archived files (mark as [archived])

6. Report summary:
   ```
   ✓ Archived [N] items:
   - [N] decisions → context/decisions/archive/
   - [N] retrospectives → context/workflows/retrospectives/archive/

   Archived items are preserved for history but no longer actively referenced.
   ```

---

### Full Maintenance (`/init-context-system --maintain`)

**Purpose**: Run full maintenance sweep (validate + archive + cleanup)

**Process**:
1. Run validation checks (as in --validate)
2. Run archival process (as in --archive)
3. Additional cleanup:
   - Check for duplicate content
   - Verify loading map completeness (all workflows have task mapping?)
   - Check index completeness (all files listed?)
4. Offer optional tasks:
   - "Found [N] large files - split them?"
   - "Found [N] files without examples - add them?"
5. Generate comprehensive report

---

## Error Handling

### Context System Already Exists

If context/ folder exists when user invokes `/init-context-system`:

```
I notice you already have a context system set up.

Current state:
- [N] context files
- [N] decisions
- [N] workflows
- Last updated: [date from most recent file]

What would you like to do?

1. Extend it (add more context) → Phase 2
2. Set up evolution framework → Phase 3
3. Validate and maintain → Run checks
4. Archive old content → Clean up
5. Start fresh (backup and rebuild) → Warning: will move existing to backup/
```

Use AskUserQuestion to get user intent.

---

### No CLAUDE.md Found

If `.claude/CLAUDE.md` doesn't exist:

```
I notice you don't have a .claude/CLAUDE.md file yet. This is the main entry point for project context.

I can:
1. Create minimal CLAUDE.md (recommended)
2. Skip CLAUDE.md and just use context/ folder
3. Create comprehensive CLAUDE.md with full project documentation

What would you prefer?
```

---

### User Stops Mid-Phase

If user stops or declines to continue:

```
No problem! You can resume anytime:

Resume at Phase 2: `/init-context-system --phase 2`
Resume at Phase 3: `/init-context-system --phase 3`

Or continue maintenance:
- Extract context: `/init-context-system --extract`
- Validate system: `/init-context-system --validate`

Your progress so far:
- [Summarize what was completed]

Questions about using what we've built?
```

---

## Best Practices for Claude

### DO:

- ✅ **Ask before creating**: Show user what you'll create, get confirmation
- ✅ **Explain value**: Connect each step to immediate or long-term benefit
- ✅ **Use examples from their project**: Reference actual files, conventions, patterns they use
- ✅ **Offer to pause**: After each phase, let user stop or continue
- ✅ **Validate user's patterns**: "I noticed you do X - should I document that?"
- ✅ **Show, don't just tell**: Display file contents, explain structure

### DON'T:

- ❌ **Auto-create everything**: Get approval before creating files
- ❌ **Use generic examples**: Personalize to their project and domain
- ❌ **Rush through phases**: Give user time to understand each step
- ❌ **Skip validation**: Always check links, frontmatter, completeness
- ❌ **Create hypothetical context**: Extract only what's actually practiced
- ❌ **Assume phase completion**: Get explicit "continue to Phase N" approval

---

## Skill Meta-Notes

**Skill complexity**: HIGH (multi-phase, interactive, creates many files)

**User investment**: 1-2 hours (but progressive, can pause)

**Maintenance**: Low ongoing (10 min after major work sessions)

**Value proposition**:
- Immediate: Stop repeating preferences
- Short-term: Task-based context loading
- Long-term: System evolves with you, compounds over time

**Success criteria**:
- User has working context system after Phase 1
- User sees value (context loading automatically)
- User maintains it (retrospectives, validation)
- Context library grows over time (20+ files after a few months)

---

*Last updated: 2026-02-07*
