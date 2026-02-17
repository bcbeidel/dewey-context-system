# Open Source Research: Context Quality Tools

## Strategic Summary

No existing tool solves Dewey's core problem. The ecosystem is mature at **creation** (generating agent instructions) and **distribution** (installing/sharing skills across platforms) but almost entirely absent at **quality** (validating content is accurate, fresh, well-sourced) and **maintenance** (ongoing curation as a discipline). The closest tools are complementary, not competitive: Vale for prose linting, RAGAS for context quality scoring, STORM for upstream content generation, and agnix for structural config validation. Dewey's specific niche — treating knowledge curation as an ongoing lifecycle with multi-tier health assessment — is genuinely unoccupied.

## What We Need

A system that ensures curated knowledge consumed by AI agents (and humans) is:
- Structurally sound (right sections, right depth, right size)
- Content-quality validated (readable, well-sourced, not duplicative)
- Fresh (not stale, verified against sources)
- Traceable (provenance, source evaluation, citation grounding)
- Progressively disclosed (metadata → summary → body → deep reference)
- Cross-file consistent (manifest in sync, links resolve, no duplicates)

## Landscape Map

### Layer 1: Creation (Mature)

Tools that generate agent instructions and knowledge content.

| Tool | Stars | What It Does | Quality/Curation? |
|------|-------|-------------|-------------------|
| [anthropics/skills](https://github.com/anthropics/skills) | 70,669 | Official Claude Code skill library | No |
| [awesome-cursorrules](https://github.com/PatrickJS/awesome-cursorrules) | 37,870 | Collection of .cursorrules templates | No |
| [STORM](https://github.com/stanford-oval/storm) | 27,902 | LLM-powered Wikipedia-style article generation with citations | Generates quality content, doesn't maintain it |
| [Skill Seekers](https://github.com/yusufkaraaslan/Skill_Seekers) | 9,569 | Converts docs/repos/PDFs into agent-ready formats | No |
| [openai/skills](https://github.com/openai/skills) | 8,725 | Official Codex skill catalog | No |

**Gap:** All one-shot creation. None maintain content quality over time.

### Layer 2: Distribution (Mature)

Tools that install, share, and discover skills across platforms.

| Tool | Stars | What It Does | Quality/Curation? |
|------|-------|-------------|-------------------|
| [everything-claude-code](https://github.com/affaan-m/everything-claude-code) | 47,019 | Complete Claude Code configuration collection | No |
| [claude-mem](https://github.com/thedotmack/claude-mem) | 28,623 | Session memory capture and injection | Runtime memory, not domain knowledge |
| [awesome-copilot](https://github.com/github/awesome-copilot) | 21,410 | GitHub Copilot instruction collection | No |
| [VoltAgent awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills) | 7,204 | 300+ community skills directory | No |
| [vercel-labs/skills](https://github.com/vercel-labs/skills) | 6,086 | `npx skills` — package manager for 35+ agents | No |
| [SkillKit](https://github.com/rohitg00/skillkit) | 336 | Universal skill package manager, 44 agents | No |
| [Skillport](https://github.com/gotalab/skillport) | 314 | CLI + MCP skill distribution | No |

**Gap:** None validate what's inside the packages they distribute.

### Layer 3: Context Assembly (Growing)

Tools that structure and optimize what goes into LLM context windows.

| Tool | Stars | What It Does | Quality/Curation? |
|------|-------|-------------|-------------------|
| [Context7](https://github.com/upstash/context7) | 45,899 | MCP server for live documentation injection | Fetches on-demand, no curation |
| [LlamaIndex](https://github.com/run-llama/llama_index) | 47,025 | Framework for building agents over data | Retrieval optimization, not content quality |
| [DSPy](https://github.com/stanfordnlp/dspy) | 32,235 | Programmatic LLM optimization framework | Optimizes pipelines, not content |
| [Haystack](https://github.com/deepset-ai/haystack) | 24,211 | Modular AI orchestration with pipelines | Pipeline assembly, not content quality |
| [Repomix](https://github.com/yamadashy/repomix) | 21,888 | Pack entire repo into AI-friendly file | Brute-force dump, opposite of curation |
| [LLMLingua](https://github.com/microsoft/LLMLingua) | 5,837 | Token compression (up to 20x) | Compression, not quality |
| [QMD](https://github.com/tobi/qmd) | 8,841 | Local search engine for markdown knowledge | Retrieval only |

**Gap:** Focused on dynamic retrieval or brute-force packing. None serve curated, static knowledge.

### Layer 4: Agent Memory (Growing)

Runtime memory systems for agents — dynamic, per-session, auto-captured.

| Tool | Stars | What It Does | Quality/Curation? |
|------|-------|-------------|-------------------|
| [RAGFlow](https://github.com/infiniflow/ragflow) | 73,331 | Enterprise RAG engine | Scale over curation |
| [Mem0](https://github.com/mem0ai/mem0) | 47,463 | Universal memory layer for agents | Auto-captured user memory, not curated knowledge |
| [Graphiti](https://github.com/getzep/graphiti) | 22,832 | Temporally-aware knowledge graphs | Temporal tracking is relevant; graph infrastructure is heavy |
| [Letta](https://github.com/letta-ai/letta) | 21,130 | Stateful agents with persistent memory | Agent state, not reference knowledge |
| [Cognee](https://github.com/topoteretes/cognee) | 12,347 | Knowledge engine for agent memory | Auto-extraction, not human curation |

**Gap:** These are runtime memory. Dewey is a curated reference library. Different problem.

### Layer 5: Content Quality (Sparse — Dewey's Niche)

Tools that validate documentation or content quality.

| Tool | Stars | What It Does | Overlap with Dewey |
|------|-------|-------------|-------------------|
| [Vale](https://github.com/errata-ai/vale) | 5,243 | Prose style linter (extensible YAML rules) | **Complementary.** Fills Dewey's prose quality gap. |
| [markdownlint](https://github.com/DavidAnson/markdownlint) | 5,844 | Markdown formatting linter | **Complementary.** Catches formatting issues Dewey ignores. |
| [RAGAS](https://github.com/explodinggradients/ragas) | 12,623 | Context quality evaluation (relevancy, recall) | **Most relevant.** LLM-as-judge for context quality. |
| [textstat](https://github.com/textstat/textstat) | 1,348 | Readability metrics (FK, SMOG, etc.) | Dewey has its own FK implementation (stdlib-only). |
| [lychee](https://github.com/lycheeverse/lychee) | 3,340 | Fast link checker | Dewey has `check_source_accessibility`. |
| [mdschema](https://github.com/jackchuka/mdschema) | 44 | Schema-based markdown structure validation | Similar concept; Dewey's is depth-aware. |
| [agnix](https://github.com/avifenesh/agnix) | 41 | Linter for agent config files (SKILL.md, CLAUDE.md) | Validates structure, not content quality. |

**Gap:** No tool combines structural validation + content quality + freshness + provenance + cross-file consistency. That's Dewey.

## What No Tool Does

| Dewey Capability | Closest Alternative | Why It's Not Enough |
|------------------|--------------------|--------------------|
| 18 per-file content validators | agnix (structural linting) | agnix checks "is this well-formed?" not "is the content accurate and fresh?" |
| 6 cross-file validators | remark-validate-links (link checking) | Only checks link resolution, not manifest sync, duplicate detection, or plan consistency |
| Tier 2 LLM-assisted quality | **Nothing found** | No tool uses an LLM to evaluate existing knowledge for source drift, depth accuracy, or why-quality |
| Tier 3 human decision queue | **Nothing found** | No tool surfaces curation decisions requiring human judgment |
| Freshness monitoring | Graphiti (temporal graphs) | Different architecture; no tool checks frontmatter dates on markdown files |
| Utilization tracking | claude-mem (session memory) | claude-mem captures session history; Dewey tracks which knowledge files agents actually read |
| Curation plan / coverage | **Nothing found** | No tool maintains "what knowledge should exist" and tracks progress |
| Source provenance validation | **Nothing found** | No tool checks source diversity, citation grounding, or source authority |
| Depth-aware section structure | DITA-OT / mdschema | DITA is XML/Java; mdschema is Go and not depth-aware |

## Build vs. Use Analysis

### Use existing tools (for what they're good at)

**Vale** could complement Dewey's Tier 1 validators:
- Prose style checking (passive voice, weasel words, jargon)
- Terminology consistency
- Readability scoring (alternative to Dewey's homegrown FK)
- Frontmatter-aware scoping

**RAGAS** concepts could inform Tier 2:
- Context relevancy scoring (signal-to-noise ratio of a knowledge entry)
- LLM-as-judge evaluation patterns

**STORM** could feed Dewey's curation pipeline:
- Generate draft articles with citations from web research
- Co-STORM for collaborative human-LLM curation

### Build custom (what Dewey uniquely provides)

Everything in the quality and maintenance layers:
- Frontmatter validation against depth-specific schemas
- Freshness monitoring from `last_validated` dates
- Source provenance (diversity, citation grounding, accessibility)
- Cross-file consistency (manifest sync, duplicate detection, link graph)
- Utilization-informed curation recommendations
- Propose/promote workflow with validation gates
- Multi-tier health model (deterministic + LLM-assisted + human judgment)

### Recommendation

**Build.** Dewey's core value proposition — knowledge curation as an ongoing discipline with health monitoring — has no existing solution. The creation and distribution layers are well-served by the Agent Skills ecosystem. The quality and maintenance layers are genuinely unoccupied.

Optionally integrate **Vale** as a complementary prose quality layer if the stdlib-only constraint is relaxed for optional external tools (similar to how `--check-links` is opt-in today).

## Sources

Research artifacts with full details per tool:
- Knowledge curation tools: 32 tools surveyed across 10 categories
- LLM context optimization: 19 tools surveyed across 8 categories
- Documentation linting: 18 tools surveyed across 9 categories
- Agent knowledge delivery: 27 tools surveyed across 8 categories
