# Bootstrap Templates

**Purpose**: Pre-configured best practices for bootstrapping a context system that supports the distributed skills.

**Used by**: `/context-curator` skill during first-run bootstrap.

---

## What's Included

### Skills Domain (4 files)
Best practices for Claude Code skill development:
- `progressive-disclosure-standard.md` - Keep SKILL.md <500 lines with reference extraction
- `execution-standards.md` - Quality requirements for skill execution
- `audit-checklist.md` - Quality validation checklist
- `agentic-planning-best-practices.md` - Evidence-based planning practices (supports `/planner`)

### Research Domain (7 files)
Research methodology standards (supports `/researcher`):
- `design-science-research-standards.md` - Technology innovation research
- `ux-research-standards.md` - User experience and usability research
- `market-research-standards.md` - Competitive analysis and market sizing
- `mixed-methods-research-standards.md` - Qualitative + quantitative combination
- `case-study-research-standards.md` - Organizational deep-dives
- `organizational-culture-standards.md` - Culture assessment and analysis
- `evidence-synthesis-standards.md` - PRISMA 2020 systematic reviews

### Auditing Domain (2 files)
Quality and compliance standards (supports `/auditor`):
- `iso-19011-audit-pattern.md` - ISO 19011:2018 audit principles and patterns
- `security-validation-and-audit.md` - Security validation and audit checklists

### Processes Domain (1 file)
General process best practices:
- `planning-best-practices.md` - Phased planning approach (supports `/planner`)

### Communication Domain (1 file)
User preference templates:
- `style-preferences.md` - Template for documenting communication preferences (user fills in)

### Decisions Domain (1 file)
Decision documentation guidance:
- `_index.md` - ADR (Architectural Decision Record) template and guidance

### Context-System Domain (2 files)
Context system meta-documentation:
- `_index.md` - Context system overview, organization principles, maintenance guidance
- `_loading-map.md` - Task → context domain mappings for efficient loading

---

## Total: 27 Files

- **19 content files**: Best practices, standards, templates
- **8 index files**: Navigation (1 main + 7 domain indexes)

Organized across 7 domains to support:
- ✅ `/context-curator` (context organization and quality)
- ✅ `/researcher` (7 research methodologies)
- ✅ `/planner` (planning best practices)
- ✅ `/auditor` (ISO 19011 quality audits)
- ✅ Agent development (skill development standards)

---

## How Bootstrap Works

1. User runs `/context-curator` for first time
2. Skill detects missing `context/` directory
3. Offers to bootstrap: "Create context system with best practices?"
4. If yes:
   - Creates `context/` directory structure (7 domains)
   - Copies 19 best practice files from skill's `bootstrap/` directory to `context/`
   - User gets functional context system immediately
5. Proceeds with normal curation workflow

---

## Maintenance

**Source of truth**: These files are extracted from the reference implementation (`bcbeidel/notes` repository) where they're battle-tested.

**Updates**: When best practices evolve in the reference implementation, sync changes using `/publisher` skill.

**Quality**: All files follow:
- Progressive disclosure (<150 lines for main files)
- Frontmatter with metadata
- Clear "When to Use" guidance
- Cross-references to related context

---

## Customization

Users can:
- **Edit files**: Customize templates after bootstrap
- **Add files**: Create new context files in any domain
- **Remove files**: Delete files that aren't relevant
- **Add domains**: Create new domains for project-specific needs

The bootstrap provides a **foundation**, not a constraint.

---

**Created**: 2026-02-09
**Source**: Reference implementation (bcbeidel/notes)
**Maintained by**: `/publisher` skill for sync operations
