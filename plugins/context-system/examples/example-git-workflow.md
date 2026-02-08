---
title: Git Workflow Conventions
created: 2026-02-07
keywords: [git, commits, branches, workflow, version-control]
applies-to: [git-operations, commits, pull-requests]
tags: [context, workflows]
type: workflows
---

# Git Workflow Conventions

## Summary

Git conventions for commits, branches, and pull requests that ensure quality, traceability, and collaboration effectiveness.

## Commit Workflow

### Step 1: Review Changes

Before staging files, review what's changed:

```bash
git status        # See all changed files
git diff          # See unstaged changes
git diff --staged # See staged changes
```

**Checkpoints:**
- ✓ Understand what each change does
- ✓ No unintended changes included
- ✓ No sensitive data (API keys, credentials) in changes

---

### Step 2: Stage Files Selectively

**Preference:** Stage specific files by name, not `git add .` or `git add -A`

```bash
# Good - explicit file staging
git add src/components/Button.tsx
git add src/styles/button.css
git add tests/button.test.tsx

# Avoid - blanket staging
git add .
git add -A
```

**Rationale:**
- Prevents accidentally committing sensitive files (`.env`, credentials)
- Prevents committing large binaries or build artifacts
- Forces conscious decision about what to include
- Makes review more intentional

**Exceptions:**
- New projects where you want all files
- User explicitly says "commit all changes"
- After running cleanup that removed unwanted files

---

### Step 3: Write Clear Commit Message

**Format:** `type(scope): subject`

**Types:**
- `feat:` - New feature
- `fix:` - Bug fix
- `docs:` - Documentation changes
- `refactor:` - Code refactoring (no behavior change)
- `test:` - Adding or updating tests
- `chore:` - Maintenance (dependencies, config, etc.)

**Subject guidelines:**
- Use imperative mood ("add" not "added" or "adds")
- Lowercase first letter (after type)
- No period at the end
- 50 characters or less
- Describe WHAT and WHY, not HOW

**Body (optional):**
- Wrap at 72 characters
- Explain motivation for change
- Contrast with previous behavior
- Reference issues/tickets if applicable

**Examples:**

**Good:**
```
feat(auth): add JWT token refresh mechanism

Users were being logged out every 15 minutes due to token expiration.
Now tokens auto-refresh in the background, improving UX.

Closes #123
```

```
fix(api): handle null response from external service

External API occasionally returns null instead of empty array,
causing application crashes. Added null checks and default values.
```

**Avoid:**
```
updated files
[Too vague - what was updated and why?]
```

```
Fixed bug
[Which bug? How was it fixed?]
```

---

### Step 4: Review Before Committing

**Checklist:**
- [ ] All tests pass (`npm test`, `pytest`, etc.)
- [ ] Code follows project conventions (linting, formatting)
- [ ] No console.log / debugging statements left in code
- [ ] Commit message is clear and follows format
- [ ] Only relevant changes are staged
- [ ] No merge conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`)

**Command:**
```bash
git diff --staged  # Final review of what's being committed
git commit -m "feat(auth): add JWT token refresh mechanism"
```

---

### Step 5: Verify Success

After committing:
```bash
git status  # Should show "nothing to commit, working tree clean"
git log -1  # Review the commit that was just created
```

---

## Branch Workflow

### Branch Naming

**Format:** `type/short-description`

**Examples:**
- `feature/user-authentication`
- `fix/login-validation-bug`
- `refactor/api-client-structure`
- `docs/readme-update`

**Conventions:**
- Lowercase with hyphens
- Descriptive but concise
- Include ticket number if applicable: `feature/AUTH-123-jwt-refresh`

---

### Creating Branches

```bash
# Create branch from main
git checkout main
git pull origin main
git checkout -b feature/user-authentication

# Or in one step (Git 2.23+)
git switch -c feature/user-authentication
```

---

### Pushing to Remote

**First push:**
```bash
git push -u origin feature/user-authentication
```

**Subsequent pushes:**
```bash
git push
```

---

## Pull Request Workflow

### Before Creating PR

**Checklist:**
- [ ] All commits follow commit conventions
- [ ] Branch is up-to-date with main/target branch
- [ ] All tests pass
- [ ] Code reviewed locally
- [ ] Documentation updated if needed

---

### Creating Pull Request

**Title:** Clear, concise summary (similar to commit message)

**Description template:**
```markdown
## Summary
[Brief description of what this PR does]

## Changes
- [Change 1]
- [Change 2]
- [Change 3]

## Testing
[How this was tested]

## Screenshots (if applicable)
[Add screenshots for UI changes]

## Related Issues
Closes #123
```

---

### Review Process

**As author:**
- Respond to feedback promptly
- Address all comments (fix or explain why not)
- Re-request review after changes
- Keep PR scope focused (avoid scope creep)

**As reviewer:**
- Check code quality, not just correctness
- Look for edge cases and error handling
- Verify tests cover the changes
- Consider performance and security implications

---

## Git Safety

### NEVER Do These (Without User Permission)

**Destructive operations:**
- `git push --force` (especially to main/master)
- `git reset --hard` (loses uncommitted changes)
- `git clean -f` (deletes untracked files)
- `git checkout .` (discards all changes)
- `git branch -D` (force-delete branch)

**Before any destructive operation:**
1. Explain what it does
2. Explain what data could be lost
3. Wait for explicit user approval
4. Suggest safer alternatives if available

---

### Always Check First

Before git operations:
```bash
git status        # Current state
git branch        # Which branch am I on?
git remote -v     # Where will this push to?
```

---

## Related Context

- [[context/communication/style-preferences]] - Review-first workflow applies to git operations
- [[context/project/quality-standards]] - Quality gates before committing

## Notes

### Commit Message Flexibility

The `type(scope):` format is preferred but not required. User's project may have different conventions. Check for:
- Existing commit history: `git log --oneline -20`
- Contributing guidelines: `CONTRIBUTING.md`
- Project documentation

Adapt to their conventions, or use these if no convention exists.

---

*Last updated: 2026-02-07*
