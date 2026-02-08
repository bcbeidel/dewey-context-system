---
title: Context Loading Map
created: 2026-02-07
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
- [[context/communication/style-preferences]] - Communication and workflow preferences

**When:**
- Starting any conversation
- User asks for review or feedback
- User asks for explanations

---

## Task: Git Operations

**Load:**
- [[context/workflows/git-workflow]] - Git conventions and commit process
- [[context/communication/style-preferences]] - Review-first workflow

**Specific subtasks:**
- **Creating commits** → Focus on commit message format, file staging
- **Creating PRs** → Focus on PR description, review process
- **General git work** → Load full workflow

**When:**
- User requests creating commits
- User requests creating pull requests
- `/commit` skill is invoked
- Working with version control

---

## Task: Code Review

**Load:**
- [[context/communication/style-preferences]] - Critique preference, review-first
- [[context/project/quality-standards]] - What to review for
- [[context/workflows/code-review-process]] - Step-by-step review workflow

**When:**
- User requests reviewing code
- User asks for improvements or suggestions
- `/review-pr` skill is invoked
- Evaluating code quality

---

## Task: Creating Documentation

**Load:**
- [[context/project/documentation-standards]] - Documentation structure and style
- [[context/communication/style-preferences]] - Concise communication, explanations
- [[context/workflows/documentation-workflow]] - How to create docs

**When:**
- User requests creating README or docs
- Writing technical documentation
- Creating onboarding guides
- Working with files in `docs/` folder

---

## Task: Testing

**Load:**
- [[context/project/testing-standards]] - Test coverage requirements, patterns
- [[context/workflows/testing-workflow]] - How to write and run tests
- [[context/project/quality-standards]] - Quality gates

**When:**
- User requests writing tests
- Running test suites
- Debugging test failures
- Working with test files (`*.test.*`, `*_test.*`)

---

## Task: Creating Notes/Files

**Load:**
- [[context/project/file-organization]] - Where files go, naming conventions
- [[context/project/obsidian-conventions]] - Wikilinks, frontmatter, tags
- [[context/workflows/note-creation]] - Template-first approach

**When:**
- User requests creating new notes
- Skills are being executed (`/daily-note`, `/book-notes`, etc.)
- Working with markdown files

---

## Task: Context System Maintenance

**Load:**
- [[context/project/context-governance]] - What is/isn't context, boundaries
- [[context/workflows/retrospective-workflow]] - How to extract context
- [[context/workflows/maintenance-checklist]] - Validation and maintenance

**When:**
- User invokes `/context-update`
- User invokes `/context-update`
- User asks about updating or maintaining context
- After major work sessions (retrospective time)

---

## Adding More Task Mappings

As you create more context files, add task mappings here.

**Template:**
```markdown
## Task: [Task Name]

**Load:**
- [[context/path/to/file]] - [Brief description of what this provides]
- [[context/path/to/another]] - [Brief description]

**When:**
- [Trigger condition 1]
- [Trigger condition 2]
- [When user does X]

---
```

**Common task types to consider**:
- Deployment operations
- Database migrations
- Security reviews
- Performance optimization
- Refactoring
- Bug fixing
- Architecture design

---

## Usage Notes

### For Claude

When you identify the user's task type:
1. Check this map for relevant context
2. Load all listed files for that task
3. Apply the context automatically
4. Mention which context you're following (e.g., "Following [[context/workflows/git-workflow]]...")

### For Users

When adding new context:
1. Consider which tasks it applies to
2. Add task mappings here
3. Be specific about "When" triggers
4. Test that context loads correctly

---

*Last updated: 2026-02-07*
