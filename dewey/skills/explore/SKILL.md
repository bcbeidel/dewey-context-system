---
name: explore
description: Discover what knowledge domains to capture through guided conversation about your problems, tasks, and goals
---

<essential_principles>
## What This Skill Does

Helps users who don't yet know what role or domains to build a knowledge base for. Runs a structured conversation that surfaces knowledge domains organically by exploring the user's problems, recurring tasks, and goals.

## Core Approach

1. **Ask about problems** -- What's frustrating, slow, or error-prone?
2. **Ask WHY** -- Surface the underlying knowledge gap, not just the symptom
3. **Identify recurring tasks** -- Where would an expert guide help most?
4. **Map to knowledge domains** -- Group related problems and tasks into 3-5 coherent areas
5. **Propose a role framing** -- Give the knowledge base a clear identity
6. **Hand off to /dewey:init** -- Create the structure with the agreed domains

## Design Philosophy

- **The user is the expert** -- We help them articulate what they already know, not prescribe what they should capture
- **ONE question at a time** -- Don't overwhelm; let the conversation breathe
- **WHY reveals the real gap** -- "I can't get my dashboards right" could mean data visualization, BI tool mastery, or data modeling -- the WHY tells you which
- **Pure conversation** -- No scripts, no file operations until the handoff to init

## Key Variables

- `$ARGUMENTS` -- Optional context the user provides (e.g., "I work in marketing")
- `${CLAUDE_PLUGIN_ROOT}` -- Root directory of the Dewey plugin
</essential_principles>

<intake>
Discovering what knowledge domains to capture.

**Before starting, check the knowledge base state:**

1. **Knowledge base exists and `.dewey/curation-plan.md` exists** -- The user already has a plan. Suggest using `/dewey:curate plan` to review it or `/dewey:curate add` to work on the next topic. Only proceed with exploration if the user explicitly wants to expand into new domains.
2. **Knowledge base exists but no `.dewey/curation-plan.md`** -- Nudge the user toward building a curation plan: "You have a knowledge base but no curation plan yet. Want to build one before exploring new areas? I can propose starter topics based on your existing structure." If they agree, read AGENTS.md and the knowledge base directory structure, propose 2-4 starter topics per domain area, and write `.dewey/curation-plan.md`. If they decline, proceed with exploration.
3. **No knowledge base initialized** (no AGENTS.md or knowledge base directory) -- Proceed normally with the exploration conversation.

**No arguments needed.** This is an interactive conversation.

If `$ARGUMENTS` contains context (e.g., "I work in marketing" or "I manage a data team"), use it as a starting point to tailor the opening question. Otherwise, start with a general exploration of problems and challenges.
</intake>

<routing>
## Routing

All invocations route to the single discovery workflow:

- Any arguments (or none) -> Route to `workflows/explore-discovery.md`
</routing>

<workflows_index>
## Available Workflows

All workflows in `workflows/`:

| Workflow | Purpose |
|----------|---------|
| explore-discovery.md | Guided conversation to discover role, domains, and knowledge structure |
</workflows_index>

<success_criteria>
Explore is successful when:

- User has a clear role framing that feels natural to them
- 3-5 domain areas identified with clear rationale tied to their problems and tasks
- User confirms the proposed structure
- Knowledge base initialized via `/dewey:init` with the agreed role and domains
</success_criteria>
