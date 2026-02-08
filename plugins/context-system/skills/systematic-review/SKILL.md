---
name: systematic-review
description: "Conduct PRISMA 2020 compliant systematic reviews with protocol registration, quality assessment, and publication-ready reporting"
allowed-tools: Read, Write, WebFetch, Glob, AskUserQuestion
---

# Systematic Review Builder

Conducts PRISMA 2020 compliant systematic reviews of academic papers and research articles with protocol registration (PROSPERO), quality assessment (AMSTAR-2, ROBIS), methodology comparison, findings synthesis, and research gap identification.

**Problem Solved**: Research synthesis skill handles general sources, but academic papers require specialized structure (abstract, methodology, findings, citations, theoretical frameworks).

**Use Case**: Academic research, thesis preparation, comprehensive literature review, understanding research landscape in a domain.

---

## Core Principles

### 1. Academic Rigor
Literature reviews require:
- Proper citation with author names and years
- Methodology comparison across studies
- Clear distinction between findings and interpretation
- Identification of theoretical frameworks
- Research gaps and future directions

### 2. Systematic Rather Than Narrative
Follow systematic review methodology (PRISMA 2020):
- Create protocol before starting (PRISMA-P)
- Register protocol (PROSPERO)
- Define research question (PICO framework)
- Establish inclusion/exclusion criteria
- Document comprehensive search strategy
- Extract data systematically with duplicate reviewers
- Assess risk of bias using established tools
- Synthesize findings thematically
- Report transparently (PRISMA 2020 checklist)

### 3. Critical Analysis Over Summary
Don't just summarize papers—analyze:
- Methodological strengths and limitations
- Contradicting findings
- Evolution of thought over time
- Gaps in current research

### 4. Citation Network Awareness
Track who cites whom:
- Foundational papers (highly cited)
- Recent developments
- Theoretical lineage
- Competing schools of thought

---

## Quick Start

**Choose your entry point**:

- **New to literature reviews?** → Start with workflow overview below
- **Creating protocol?** → [[protocol-phase]] (PRISMA-P, PROSPERO)
- **PRISMA 2020 compliance?** → [[prisma-compliance]] (27-item checklist)
- **Quality assessment?** → [[quality-assessment]] (AMSTAR-2, ROBIS)
- **Processing papers?** → [[paper-processing]]
- **Comparing methodologies?** → [[methodology-comparison]]
- **Mapping citations?** → [[citation-mapping]]
- **Finding research gaps?** → [[gap-analysis]]
- **Need examples?** → [[examples]]

---

## Workflow Overview

Literature reviews follow a six-phase systematic process (PRISMA 2020):

### Phase 0: Protocol (PRISMA-P)

**Goal**: Create and register review protocol before starting to ensure transparency and rigor.

**Activities**:
1. Define review question (PICO framework)
2. Establish inclusion/exclusion criteria
3. Document planned search strategy
4. Specify risk of bias assessment methods
5. Pre-specify synthesis and subgroup analyses
6. Register on PROSPERO

**Output**: Registered protocol document (PRISMA-P 17-item checklist)

**Why This Matters**:
- Prevents post-hoc modifications (p-hacking)
- Ensures transparency (public record)
- Avoids duplication (others can see review in progress)
- Required by many journals

**Time Estimate**: 2-4 hours for protocol creation + 1-3 weeks for PROSPERO approval

**See**: [[protocol-phase]] for detailed PRISMA-P checklist, PROSPERO registration, and protocol templates

**Note**: Quick preliminary reviews (3-5 papers) may skip formal protocol, but comprehensive reviews should always have registered protocols.

---

### Phase 1: Scoping

**Goal**: Define research question and identify papers to review.

**Activities**:
1. Define research question
2. Establish inclusion/exclusion criteria
3. Document search strategy
4. Collect papers (user provides or WebSearch)

**Output**: List of papers with basic metadata

**Scoping Questions**:
- **Research Question**: What are you investigating?
- **Topic**: Broad subject area
- **Time Period**: Years to include (e.g., 2015-2026)
- **Inclusion Criteria**: What types of papers?
- **Exclusion Criteria**: What to leave out?

**Example**:
```markdown
**Research Question**: How effective is spaced repetition for long-term knowledge retention?

**Inclusion Criteria**:
- Empirical studies with quantitative results
- Published in peer-reviewed journals
- Studies on human learners

**Exclusion Criteria**:
- Opinion pieces without data
- Non-English publications
- Pre-2010 studies
```

**Source Collection Methods**:
1. User provides PDFs or URLs
2. WebSearch for relevant papers
3. Check vault (`/learning/`, `/reading/`) for existing papers

---

### Phase 2: Paper Processing

**Goal**: Extract systematic data from each paper to enable comparison.

**Activities**:
1. Extract metadata (authors, year, journal, DOI)
2. Document study design (method, sample, variables)
3. Record key findings (with effect sizes)
4. Identify theoretical framework
5. Note strengths and limitations

**Output**: Individual extraction file for each paper using standard template

**See**: [[paper-processing]] for detailed extraction template and best practices

**Time Estimate**: 15-30 minutes per paper

---

### Phase 3: Cross-Paper Synthesis

**Goal**: Compare methodologies and synthesize findings thematically (NOT paper-by-paper).

**Activities**:
1. Create methodology comparison table
2. Organize findings by theme (consensus, debate, patterns)
3. Map citation networks and theoretical lineage
4. Identify foundational vs. contemporary works

**Output**:
- Methodology comparison table
- Thematic synthesis document
- Citation network map

**Critical Principle**: Organize by theme, not by paper. Synthesis ≠ summary.

**See**:
- [[methodology-comparison]] for comparison tables and thematic synthesis
- [[citation-mapping]] for tracking theoretical lineage

**Time Estimate**: 2-4 hours depending on review size

---

### Phase 4: Gap Analysis

**Goal**: Identify what's missing in current research.

**Activities**:
1. Identify methodological gaps (limited methods)
2. Identify population gaps (understudied groups)
3. Identify content gaps (unexplored topics)
4. Identify theoretical gaps (underdeveloped theory)
5. Identify contextual gaps (missing real-world studies)

**Output**: Comprehensive research gap analysis with specific recommendations

**Gap Types**:
- **Methodological**: What research methods are missing?
- **Population**: What groups are understudied?
- **Content**: What topics haven't been explored?
- **Theoretical**: What theory needs development?
- **Contextual**: What real-world applications are missing?

**See**: [[gap-analysis]] for gap identification templates and examples

**Time Estimate**: 1-2 hours

---

### Phase 5: Literature Review Output

**Goal**: Generate comprehensive, publication-ready literature review document.

**Structure**:
1. Abstract (150-250 words)
2. Introduction (background, research question, scope)
3. Methodology (paper selection, data extraction, quality assessment)
4. Overview of studies (timeline, methods, samples)
5. Synthesized findings (thematic organization)
6. Methodological comparison
7. Theoretical frameworks
8. Critical analysis
9. Research gaps and future directions
10. Implications (practice, policy, research)
11. Conclusion
12. References
13. Appendices

**Output**: Complete academic literature review (length varies by depth: 3-20 pages)

**See**: gap analysis for complete structure and templates

**File Location**: `/reading/systematic-reviews/[topic]-systematic-review-[YYYY].md`

---

## Quick Reference

For detailed information on specific topics, see the reference documentation:

### Core Documentation
- **[[best-practices]]** - Paper selection, critical reading, citation practices, synthesis quality
- **[[quality-checklist]]** - PRISMA 2020 compliance checklist, quality assessment requirements
- **[[integration-patterns]]** - Integration with other skills, customization options, depth guidelines
- **[[strengths-limitations]]** - What works well, optimal conditions, challenges, workarounds

### Workflow Guides
- **[[protocol-phase]]** - PRISMA-P protocol creation, PROSPERO registration
- **[[paper-processing]]** - Extract systematic data from papers
- **[[methodology-comparison]]** - Compare methods and synthesize findings
- **[[citation-mapping]]** - Map citation networks and theoretical lineage
- **[[gap-analysis]]** - Identify research gaps and generate final output

### PRISMA & Quality
- **[[prisma-compliance]]** - PRISMA 2020 27-item checklist, flow diagram, abstract checklist
- **[[quality-assessment]]** - AMSTAR-2, ROBIS, robustness checks

### Examples & Integration
- **[[examples]]** - Usage examples, customization options, integration patterns

---

## Related Skills

- **`/research-synthesis`** - General multi-source synthesis (non-academic)
- **`/mental-model`** - Extract theoretical frameworks as mental models
- **`/learn`** - Learn concepts from research findings
- **`/diagram`** - Visualize theoretical frameworks and citation networks

---

## External Resources

- [PRISMA 2020 Statement](https://www.prisma-statement.org/prisma-2020-statement) - Official guideline
- [PRISMA 2020 Checklist](https://www.prisma-statement.org/prisma-2020-checklist) - 27-item checklist
- [PROSPERO Registry](https://www.crd.york.ac.uk/prospero/) - Protocol registration
- [AMSTAR-2](https://amstar.ca/Amstar-2.php) - Quality assessment tool
- [ROBIS](https://www.bristol.ac.uk/population-health-sciences/projects/robis/) - Risk of bias tool
- [Cochrane Handbook](https://training.cochrane.org/handbook) - Evidence synthesis methods
- [Google Scholar](https://scholar.google.com/) - Paper discovery
- [Connected Papers](https://www.connectedpapers.com/) - Citation network visualization

---

## Source

**Created**: 2026-02-01
**Refactored**: 2026-02-08 (progressive disclosure - extracted best practices, quality checklist, integration patterns, strengths/limitations)
**Updated**: 2026-02-07 (PRISMA 2020 integration, quality assessment)

**Based On**:
- PRISMA 2020 Statement (Page et al., 2021)
- PRISMA-P 2015 Protocol Guidelines (Moher et al., 2015)
- AMSTAR-2 Quality Assessment (Shea et al., 2017)
- ROBIS Risk of Bias Tool (Whiting et al., 2016)
- Cochrane Handbook for Systematic Reviews
- Academic research standards and best practices
- Research synthesis patterns from `/research-synthesis`

**Research**: Claude Skills Research   2026 02

---

**First Use**: Choose an academic topic you want to deeply understand through scholarly research

**Success Criteria**: Comprehensive understanding of research landscape, gaps, and future directions
