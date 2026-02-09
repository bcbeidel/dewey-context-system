---
title: Context Loading Map
type: reference
domain: context-system
created: YYYY-MM-DD
---

# Context Loading Map

**Purpose**: Map task types to relevant context domains for efficient, targeted loading.

**Why**: Loading only relevant context reduces token usage and improves response quality.

---

## How to Use This Map

**For Claude**:
1. Identify task type from user request
2. Load domains listed for that task type
3. Start with domain `_index.md` files
4. Load specific files as needed

**For Humans**:
- Find your task category
- See which domains are relevant
- Navigate to those domains

---

## Task → Context Mappings

### Skill Development

**Task**: Developing, auditing, or refactoring Claude Code skills

**Load**:
- [[skills/_index|Skills]] - Structure, execution, quality standards
- [[auditing/_index|Auditing]] - Quality validation, audit checklists
- [[communication/_index|Communication]] - Style preferences (always)

**Examples**:
- "Create a new skill for X"
- "Audit existing skills for quality"
- "Refactor skill to use progressive disclosure"

---

### Research & Synthesis

**Task**: Conducting research, literature reviews, evidence synthesis

**Load**:
- [[research/_index|Research]] - Methodologies, PRISMA 2020 standards
- [[processes/_index|Processes]] - Research workflows
- [[communication/_index|Communication]] - Style preferences (always)

**Examples**:
- "Conduct systematic review on X"
- "Research best practices for Y"
- "Synthesize findings from multiple sources"

---

### Planning & Execution

**Task**: Planning multi-step tasks, project execution, milestone tracking

**Load**:
- [[processes/_index|Processes]] - Planning best practices, phased execution
- [[skills/_index|Skills]] - Agentic planning best practices
- [[decisions/_index|Decisions]] - Past architectural choices
- [[communication/_index|Communication]] - Style preferences (always)

**Examples**:
- "Plan implementation for feature X"
- "Create execution roadmap"
- "Break down complex task into steps"

---

### Quality Auditing

**Task**: Auditing quality, compliance, security, or performance

**Load**:
- [[auditing/_index|Auditing]] - ISO 19011 standards, security validation
- [[skills/_index|Skills]] - Audit checklists
- [[decisions/_index|Decisions]] - Past standards decisions
- [[communication/_index|Communication]] - Style preferences (always)

**Examples**:
- "Audit skills for quality compliance"
- "Security validation of code"
- "Performance audit"

---

### Decision Making

**Task**: Making architectural decisions, choosing between alternatives

**Load**:
- [[decisions/_index|Decisions]] - Past decisions, ADR template
- [[processes/_index|Processes]] - Decision-making workflows
- [[communication/_index|Communication]] - Style preferences (always)

**Examples**:
- "Should we adopt pattern X or Y?"
- "Choose between technology A and B"
- "Document decision about Z"

---

### Context Maintenance

**Task**: Maintaining context system, extracting learnings, curating content

**Load**:
- [[context-system/_index|Context System]] - Organization principles
- [[skills/_index|Skills]] - Execution standards (for skill updates)
- [[communication/_index|Communication]] - Style preferences (always)

**Examples**:
- "Extract learnings from this session"
- "Update context with new preferences"
- "Validate context quality"

---

## Universal Context

**Always load**:
- [[communication/_index|Communication]] - Foundational preferences apply to all tasks

**Frequently relevant**:
- [[decisions/_index|Decisions]] - Reference past choices to maintain consistency
- [[context-system/_index|Context System]] - Understand how to navigate

---

## Adding New Mappings

When adding new task types:

1. **Identify task category**: What type of work is this?
2. **Determine relevant domains**: Which domains provide useful context?
3. **Add mapping**: Document task → domains relationship
4. **Update loading map**: Add to this file
5. **Validate**: Test that loading suggested domains helps with task

---

## Optimization Guidelines

**Load selectively**:
- ✅ Load domains directly relevant to task
- ✅ Start with `_index.md` files for quick overview
- ❌ Don't load all domains for every task
- ❌ Don't load full files when index provides enough context

**Task complexity affects loading**:
- **Simple tasks**: Load 1-2 domain indexes
- **Moderate tasks**: Load 2-3 domains with specific files
- **Complex tasks**: Load 3-4 domains with comprehensive files

---

**Created**: [Date]
**Last Updated**: [Date]
**Maintained By**: `/context-curator` skill
