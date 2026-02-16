<objective>
Gather user feedback, classify it, draft a GitHub issue, get user confirmation, and submit to the Dewey repository.
</objective>

<process>
## Step 1: Check prerequisites

Verify that `gh` is available and authenticated:

```bash
gh auth status 2>&1
```

If `gh` is not installed, tell the user:

> "The `gh` CLI is required to submit feedback. Install it from https://cli.github.com/ and run `gh auth login`."

If `gh` is installed but not authenticated, tell the user:

> "You need to authenticate with GitHub first. Run `gh auth login` and try again."

Stop here if either check fails. Do not proceed to drafting.

## Step 2: Classify the feedback

Based on the user's input, classify into one of:

| Category | Signal patterns | GitHub label |
|----------|----------------|--------------|
| **Bug** | "broke", "error", "doesn't work", "failed", "crash", "wrong", "unexpected" | `bug` |
| **Enhancement** | "would be nice", "could you add", "feature", "idea", "suggestion", "improve" | `enhancement` |
| **General** | Praise, confusion, questions, mixed feedback, anything that doesn't clearly fit above | `enhancement,feedback` |

If classification is ambiguous, ask **one** clarifying question: "Would you describe this as a bug (something broke) or an idea for improvement?"

## Step 3: Draft the issue

### For bugs

Compose the issue body following this structure:

```markdown
## What Happened

[Extract from user's description: what they observed]

## What Should Have Happened

[Extract or infer: what the user expected instead]

## Steps to Reproduce

[Extract any reproduction steps. If the user didn't provide steps, write "Not provided -- please add if you can."]

## Context

[Any environment details the user mentioned. If none, write "Not provided."]
```

### For enhancements and general feedback

Compose the issue body following this structure:

```markdown
## Summary

[One paragraph summarizing the feedback or idea]

## Why This Matters

[Extract or infer the motivation from the user's message]

## What Needs to Happen

[If the user described specific changes, list them. Otherwise write "To be determined based on discussion."]
```

### For all issues

Append this footer to the body:

```markdown

---
*Submitted via Dewey report-issue skill*
```

Draft a concise title (under 70 characters) that captures the core of the feedback.

## Step 4: Preview and confirm

Show the user the full issue that will be created:

```
Title: <title>
Labels: <labels>

<body>
```

Ask: "Does this look right? I can adjust the title, labels, or body before submitting."

If the user requests changes, revise and preview again. Do not submit until the user confirms.

## Step 5: Submit

Create the issue:

```bash
gh issue create --repo bcbeidel/dewey --title "<title>" --label "<labels>" --body "<body>"
```

Display the resulting issue URL to the user.

If the `gh` command fails (e.g., permission denied, network error), show the error and suggest the user can manually create an issue at https://github.com/bcbeidel/dewey/issues/new.
</process>

<success_criteria>
- Prerequisites checked before any drafting work
- Feedback classified into bug, enhancement, or general
- Issue body follows the appropriate template structure
- User saw a preview and explicitly confirmed before submission
- Issue created on bcbeidel/dewey with correct labels
- Issue URL displayed to the user
</success_criteria>
