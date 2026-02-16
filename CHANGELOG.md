# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2026-02-16

Complete rewrite of Dewey from a context-optimization tool (analyze/split) into a
knowledge-base management plugin for Claude Code.

### Added

- **Curate skill** — single entry point for all knowledge-base content operations:
  discover domains, scaffold structure, add/update topics, ingest URLs, manage
  proposals and curation plans
- **Health skill** — three-tier validation and reporting system:
  - Tier 1: 18 per-file validators and 6 cross-file validators (deterministic, CI-friendly)
  - Tier 2: LLM-assisted pre-screener with 9 triggers for nuanced quality checks
  - Tier 3: Human decision queue for subjective judgment calls
- **Report-issue skill** — submit bug reports, feature ideas, or feedback to GitHub
- **Auto-fix** — automated remediation for common Tier 1 issues
- **History tracking** — snapshot-based health history for trend analysis
- **Utilization tracking** — PostToolUse hook logs knowledge-base reads; feeds
  recommendations for stale-high-use, expand-depth, low-utilization, and
  never-referenced files
- **Readability checks** — Flesch-Kincaid grade-level bounds per content depth
- **Source quality validators** — placeholder detection, source diversity,
  citation grounding, and source accessibility checking
- **Duplicate content detection** — exact paragraph hashing plus Jaccard similarity
- **Naming convention enforcement** — directory and file slug validation
- **Curation plan workflow** — structured planning before content creation
- **Proposal lifecycle** — propose, review, and promote content through validation gates
- **12 design principles** grounded in agent context research and cognitive science

### Changed

- Consolidated explore, init, and curate skills into a single `curate` skill with
  free-text intake and intent classification
- Renamed all "KB"/"kb" references to "knowledge base"/"knowledge-base" throughout
  the codebase (identifiers, CLI flags, marker comments, file names, prose)
- Migrated all SKILL.md files to pure XML structure

### Removed

- `analyze` skill (LLM-driven semantic analysis of context files)
- `split` skill (automated context file splitting)
- `explore` skill (merged into curate)
- `init` skill (merged into curate)

[1.0.0]: https://github.com/bcbeidel/dewey/releases/tag/v1.0.0
