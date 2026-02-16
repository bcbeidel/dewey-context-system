---
name: report-issue
description: Submit bug reports, feature ideas, or general feedback for the Dewey plugin to the project's GitHub issue tracker
---

<essential_principles>
## What This Skill Does

Lets plugin users submit feedback to the Dewey GitHub repository without needing to know the repo URL or issue template structure. Claude gathers freeform input, classifies it, drafts a GitHub issue, shows a preview, and submits via `gh`.

## Core Approach

1. **Gather** -- The user describes what's on their mind in natural language.
2. **Classify** -- Claude determines whether it's a bug, enhancement, or general feedback.
3. **Draft** -- Claude composes a structured GitHub issue body.
4. **Confirm** -- The user reviews and approves before anything is posted.
5. **Submit** -- `gh issue create` posts to the Dewey repo.

## Design Philosophy

- **Freeform intake** -- The user says what they want. Claude extracts structure.
- **User controls content** -- No automatic capture of conversation history or environment details. The user sees and approves everything before submission.
- **One command, one outcome** -- A GitHub issue on `bcbeidel/dewey`.

## Key Variables

- `$ARGUMENTS` -- Optional free-text feedback passed directly to the skill
- `${CLAUDE_PLUGIN_ROOT}` -- Root directory of the Dewey plugin
</essential_principles>

<intake>
This skill activates on `/dewey:report-issue` or when the user expresses feedback intent: "report a bug in dewey", "I have feedback about the plugin", "something isn't working in dewey", "I'd like to suggest a feature for dewey", or similar phrases.

## Step 1: Gather feedback

If `$ARGUMENTS` contains substantive feedback, use it directly. Do not re-ask.

If invoked with no arguments and no prior conversational context, ask one open-ended question:

> "What feedback do you have about Dewey? This could be a bug report, a feature idea, or anything else on your mind."

## Step 2: Route

All feedback routes to the same workflow. There is only one.

Route to `workflows/report-issue-submit.md`.
</intake>

<workflows_index>
## Available Workflows

All workflows in `workflows/`:

| Workflow | Purpose |
|----------|---------|
| report-issue-submit.md | Gather feedback, classify, draft GitHub issue, confirm with user, submit |
</workflows_index>

<success_criteria>
Feedback submission is successful when:

- The user's feedback is captured accurately in the issue body
- The issue is classified with the correct label (bug or enhancement)
- The user reviewed and approved the issue before submission
- The issue was created on `bcbeidel/dewey` and the URL was shown to the user
</success_criteria>
