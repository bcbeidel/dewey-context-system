---
title: Phased Execution Workflow
created: 2026-01-25
updated: 2026-01-25
keywords: [phased-approach, reflection, iteration, consistency-checks, verification, documentation-alignment]
applies-to: [complex-tasks, multi-phase-work, large-projects]
tags: [context, workflow]
type: workflow
---

# Phased Execution Workflow

## Summary

Workflow for breaking complex tasks into phases with reflection loops and consistency checks. Emphasizes iterative design, verification between phases, and keeping documentation/implementation in sync.

## Details

### Core Philosophy

**Break complex work into discrete phases with reflection between each phase.**

**Pattern:**
1. **Phase 1**: Initial work (research, analysis, proposal)
2. **Review & Reflect**: What did we accomplish? What's missing?
3. **Phase 2**: Next step based on reflection
4. **Review & Reflect**: Check for consistency and gaps
5. **Phase 3**: Complete remaining work
6. **Final Review**: Verify everything aligns

**Why phases?**
- Prevents rushing to implementation without full understanding
- Creates checkpoints for course correction
- Surfaces issues early
- Allows user to provide feedback before going too far
- Reduces rework from misalignment

---

### Phase Structure Template

**Each phase should have:**

1. **Objective**: What are we trying to accomplish?
2. **Actions**: What specific steps will we take?
3. **Deliverable**: What will exist at the end of this phase?
4. **Review Questions**: What should we check before proceeding?

**Example:**

```
Phase 1: Analyze Current State
- Objective: Understand existing recipe organization
- Actions: Review files, identify patterns, document current state
- Deliverable: Analysis of 166 recipes with patterns identified
- Review: Do we understand the problem space well enough to propose a solution?

Phase 2: Design Structure
- Objective: Propose organization approach
- Actions: Design flat structure, plan MOC system, draft documentation
- Deliverable: Detailed proposal with rationale
- Review: Does this approach solve the core problems? Are there gaps?

Phase 3: Implement
- Objective: Apply structure to all recipes
- Actions: Migrate files, create MOCs, update frontmatter
- Deliverable: 166 recipes in new structure
- Review: Does implementation match design? Are docs/skills/templates aligned?
```

---

### Reflection Between Phases

**After completing each phase, actively reflect:**

**Reflection questions:**
- What did we just accomplish?
- What did we learn during this phase?
- Does the result match our intent?
- What issues or inconsistencies did we introduce?
- What should we do next?
- Are there gaps we need to address?

**How to reflect:**

```
Claude: Phase 1 complete. Let me reflect on what we've built:

Accomplished:
- ✓ Analyzed 166 existing recipes
- ✓ Identified inconsistent tag capitalization (Dinner vs dinner)
- ✓ Found 10 different cooking time formats

Learned:
- Tags are used inconsistently
- No structured fields for filtering
- Some recipes missing key metadata

Issues spotted:
- Current structure doesn't support multi-categorization
- Folder hierarchy would break existing links

Recommendation:
Phase 2 should focus on designing a flat structure with tag standardization.

Before we proceed, are there other aspects we should consider?
```

---

### Consistency Checks

**Critical:** After making changes, verify that related artifacts stay in sync.

**Artifacts that must align:**
1. **Documentation** (references/ai-assistants/CLAUDE.md, guides, READMEs)
2. **Implementation** (actual files, structure)
3. **Templates** (in extras/templates/)
4. **Skills** (.claude/skills/ and .claude/commands/)
5. **Examples** (sample files referenced in docs)

**Consistency check workflow:**

```
After implementing changes:

1. Check documentation
   → Does references/ai-assistants/CLAUDE.md reflect the new structure?
   → Do guides reference the correct locations?

2. Check templates
   → Does Template, Recipe.md match the new format?
   → Are frontmatter fields aligned?

3. Check skills
   → Does recipe-scraper skill follow the new conventions?
   → Do skills read the updated templates?

4. Check examples
   → Do example recipes demonstrate the new structure?
   → Are cross-references accurate?
```
