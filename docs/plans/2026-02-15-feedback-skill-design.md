# Report-Issue Skill Design

**Date:** 2026-02-15
**Status:** Approved

## Goal

Let plugin users submit feedback (bugs, enhancements, general) to the Dewey GitHub repo without needing to know the repo URL or issue template structure. Claude gathers freeform input, classifies it, drafts a GitHub issue, previews it, and submits via `gh`.

## Naming

Named `report-issue` instead of `feedback` because `feedback` is a reserved Claude Code command.

## Audience

Plugin users who installed Dewey into their own Claude Code projects. They may not know the GitHub repo URL or have visited the issue tracker.

## Structure

```
dewey/skills/report-issue/
  SKILL.md                            # Entry point + intake + routing
  workflows/
    report-issue-submit.md            # gather -> classify -> draft -> confirm -> submit
```

No Python scripts. No references. Claude handles conversation and judgment; `gh` handles the operation.

## Conversation Flow

1. **Intake** -- Free-text intake (same pattern as curate). If `$ARGUMENTS` provided, treat as the feedback itself.
2. **Classify** -- Claude reads user input and classifies as `bug`, `enhancement`, or `general` (general maps to enhancement label + feedback label).
3. **Draft** -- Claude composes issue body following existing templates. For bugs: What Happened, What Should Have Happened, Steps to Reproduce, Context. For enhancements: Summary, Why This Matters, What Needs to Happen.
4. **Preview** -- Show user the full issue (title, labels, body) and ask for confirmation.
5. **Submit** -- `gh issue create --repo bcbeidel/dewey` with title, labels, and body. Display resulting issue URL.

## Error Handling

Check `gh auth status` before drafting. If `gh` not available or not authenticated, tell user what to install/run and stop. No local fallback.

## Approach (Chosen)

Conversational intake + direct `gh issue create`. No Python intermediary. Minimal moving parts. Matches curate skill's free-text intake pattern.

## What It Doesn't Do

- No local file fallback (YAGNI)
- No conversation context auto-capture (privacy -- user controls what goes in the issue)
- No duplicate detection against existing issues (add later if needed)
