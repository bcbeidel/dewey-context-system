# Rapid Evidence Assessment (REA)

**Purpose**: Streamlined evidence synthesis for time-constrained contexts (1-2 weeks vs 4-8 weeks for full systematic review).

**Created**: 2026-02-08

---

## Overview

**Rapid Evidence Assessment (REA)** is a pragmatic variant of systematic review that maintains rigor while accommodating real-world time constraints.

**When to use REA**:
- Time-constrained (need insights in 1-2 weeks, not 2 months)
- Internal decision-making (not for academic publication)
- Exploratory research (scoping the landscape)
- Business contexts (VP-level decision support)

**When full systematic review is better**:
- Academic publication required
- High-stakes policy decisions
- External validation needed
- Time available (4-8 weeks)

---

## REA vs Full Systematic Review

| Aspect | Full Systematic Review | Rapid Evidence Assessment |
|--------|----------------------|---------------------------|
| **Timeline** | 4-8 weeks | 1-2 weeks |
| **Protocol** | Registered (PROSPERO) | Documented (internal) |
| **Search** | Comprehensive (5-10 databases) | Targeted (2-3 key databases) |
| **Screening** | Duplicate reviewers | Single reviewer + spot checks |
| **Extraction** | Duplicate extraction | Single extraction + validation |
| **Quality assessment** | Full AMSTAR-2/ROBIS | Abbreviated (key criteria only) |
| **Output** | Publication-ready (15-30 pages) | Executive report (5-15 pages) |
| **PRISMA compliance** | Full 27-item checklist | PRISMA-inspired (key items) |

**Trade-off**: REA sacrifices comprehensiveness and external validity for speed and pragmatism.

---

## Four-Phase REA Workflow

### Timeline

**Total**: 1-2 weeks (7-10 working days)

**Phase breakdown**:
- Phase 1: Rapid Scoping (1-2 days)
- Phase 2: Targeted Search & Screening (2-3 days)
- Phase 3: Rapid Synthesis (2-3 days)
- Phase 4: Executive Reporting (1-2 days)

---

## Phase 1: Rapid Scoping

**Goal**: Define focused research question and establish boundaries.

**Duration**: 1-2 days

---

### Activities

**1. Define focused research question** (2-3 hours):

**Use PICO framework** (simplified):
- **P**opulation: Who/what?
- **I**ntervention/Topic: What are you investigating?
- **O**utcome: What do you want to know?

**Example (business context)**:
- **P**: Software development teams
- **I**: Agile retrospective practices
- **O**: Impact on team performance and morale

**Research question**: "What evidence exists on the effectiveness of agile retrospectives for improving team performance and morale?"

**Note**: REA questions are narrower than full systematic review (by design).

---

**2. Establish pragmatic inclusion criteria** (1 hour):

**Inclusion**:
- **Recency**: Past 5-10 years (prioritize recent evidence)
- **Quality**: Peer-reviewed + high-quality grey literature (e.g., major consulting reports)
- **Relevance**: Directly addresses research question
- **Language**: English (or accessible languages)

**Exclusion**:
- Older than 10 years (unless seminal work)
- Opinion pieces without data
- Tangentially related studies

**Pragmatic rule**: When in doubt, include at this stage (screen out during extraction if not relevant)

---

**3. Identify key databases** (30 min):

**Academic** (choose 2-3 most relevant):
- Google Scholar (broad, fast)
- PubMed (health/life sciences)
- PsycINFO (psychology/behavior)
- Scopus or Web of Science (multidisciplinary)
- SSRN (social sciences, working papers)

**Grey literature** (choose 1-2):
- Industry reports (Gartner, Forrester, McKinsey)
- Organizational websites (e.g., Scrum Alliance, Agile Alliance)
- Preprints (arXiv, bioRxiv)

**Rule**: 2-3 academic databases + 1-2 grey literature sources = sufficient coverage for REA

---

**4. Draft simple search strategy** (1-2 hours):

**Simplified Boolean search**:
- **Core terms**: Primary keywords (2-4 terms)
- **Synonyms**: Key alternatives
- **Boolean**: AND, OR (skip complex nesting)

**Example**:
```
("agile retrospective" OR "sprint retrospective" OR "team retrospective") AND
("performance" OR "effectiveness" OR "morale" OR "satisfaction")
```

**Rule**: Simpler searches okay for REA (accept some missed papers for speed)

---

**5. Document lightweight protocol** (1 hour):

**Internal protocol** (no PROSPERO registration):
- Research question
- Inclusion/exclusion criteria
- Databases and search terms
- Screening and extraction approach
- Synthesis plan

**Save as**: `/projects/[project-name]/rea-protocol-[topic]-[YYYY-MM-DD].md`

**Purpose**: Transparency and reproducibility (internal), not external registration

---

### Phase 1 Outputs

- ✅ Focused research question (PICO)
- ✅ Inclusion/exclusion criteria
- ✅ 2-3 key databases identified
- ✅ Simple search strategy
- ✅ Lightweight protocol documented

---

## Phase 2: Targeted Search & Screening

**Goal**: Identify relevant papers efficiently.

**Duration**: 2-3 days

---

### Activities

**1. Execute searches** (2-4 hours):

**Process**:
- Run search in each database
- Record results per database (for documentation)
- Aim for 50-200 initial results (if too many, narrow search; if too few, broaden)

**Example**:
- Google Scholar: 87 results
- PubMed: 34 results
- Gartner/Forrester reports: 5 relevant reports
- Total: 126 results

---

**2. Rapid deduplication** (1 hour):
- Export to reference manager (Zotero, Mendeley)
- Run auto-deduplication
- Quick manual check (don't spend hours on perfect deduplication)

**Example**: 126 → 98 unique

---

**3. Title/abstract screening** (3-6 hours):

**Single reviewer** (you):
- Review each title/abstract
- Classify: Include, Exclude, Maybe
- **Quick decision-making**: When uncertain, include (screen out during extraction)

**Rule**: Aim for 15-30 papers max for extraction (manageable in REA timeline)

**Quality spot check** (optional, 30 min):
- Have colleague review 10-20% of your exclusions
- Check for systematic over-exclusion
- Adjust if needed

**Example**: 98 screened → 28 potentially relevant

---

**4. Full-text screening** (2-3 hours):
- Retrieve PDFs
- Skim full text (intro, methods, results, conclusions)
- Apply inclusion criteria strictly now
- Document exclusions

**Example**: 28 full-text screened → 18 included

---

**5. Lightweight PRISMA flow** (15 min):

**Simplified format**:
```
Database search (n=126)
    ↓
Unique records (n=98)
    ↓
Title/abstract screen (n=98) → Excluded (n=70)
    ↓
Full-text screen (n=28) → Excluded (n=10)
    ↓
Included in REA (n=18)
```

**Purpose**: Document process for transparency (even if not publishing)

---

### Phase 2 Outputs

- ✅ Searches executed (2-3 databases)
- ✅ Screening completed (single reviewer)
- ✅ Final included papers (n=10-30 typical for REA)
- ✅ Simplified PRISMA flow diagram

---

## Phase 3: Rapid Synthesis

**Goal**: Extract and synthesize findings efficiently.

**Duration**: 2-3 days

---

### Activities

**1. Streamlined extraction** (15-20 min per paper):

**Essential fields only**:
- **Citation**: Author, year, title
- **Study type**: RCT, observational, qualitative, review, grey literature
- **Sample**: Who, how many, context
- **Key findings**: 2-3 main results (focus on outcomes of interest)
- **Quality indicator**: High/Medium/Low (quick judgment, not formal tool)

**Rule**: Don't extract everything - focus on answering your research question

**Template** (simplified):
```markdown
# Author (Year)

**Study type**: [RCT/Observational/Qualitative/Review/Report]
**Sample**: [n=X, population, context]

**Key findings**:
1. [Finding 1 relevant to research question]
2. [Finding 2]
3. [Finding 3]

**Quality**: [High/Medium/Low]
**Notable limitation**: [If any major concern]
```

---

**2. Abbreviated quality assessment** (5-10 min per paper):

**Quick quality indicators**:
- **High**: Peer-reviewed, strong methods, adequate sample, clear findings
- **Medium**: Peer-reviewed but small sample OR grey lit with strong methods
- **Low**: Weak methods, unclear findings, potential bias

**Rule**: Don't use formal tools (AMSTAR-2, ROBIS) - too time-consuming for REA

**Flag major quality concerns** but don't exclude based on quality (unlike full systematic review)

---

**3. Rapid thematic synthesis** (1-2 days):

**Process**:
1. Read all extracted findings
2. Identify 3-5 major themes (recurring patterns)
3. Organize evidence by theme
4. Write short narrative per theme

**Example themes** (agile retrospectives):
- **Theme 1: Psychological safety enables candid feedback** (12/18 papers)
  - Evidence: Smith (2020) found teams with high safety had 3x more actionable retrospective items
  - Evidence: Brown (2022) qualitative study showed fear of blame silences team members

- **Theme 2: Action tracking increases effectiveness** (9/18 papers)
  - Evidence: Chen (2021) showed retrospectives with action tracking improved velocity by 15%
  - Evidence: Gartner (2023) report found 67% of high-performing teams track retro actions

- **Theme 3: Facilitation matters** (7/18 papers)
  - Evidence: Davis (2019) compared facilitated vs self-facilitated, found facilitated had better outcomes

**Rule**: Synthesis is thematic (by topic), not paper-by-paper

---

**4. Quick gap identification** (1-2 hours):

**Identify obvious gaps**:
- What's missing? (populations, contexts, methods)
- What's unclear? (contradictory findings)
- What's outdated? (no recent research)

**Example**:
- **Gap 1**: Most studies in tech industry, no evidence for non-tech contexts
- **Gap 2**: Quantitative outcomes focus on velocity, qualitative on morale - need mixed methods
- **Gap 3**: No long-term studies (>1 year) - sustainability unknown

---

### Phase 3 Outputs

- ✅ Extraction completed (10-30 papers, streamlined template)
- ✅ Quality flagged (High/Medium/Low)
- ✅ Thematic synthesis (3-5 themes with evidence)
- ✅ Gaps identified (3-5 major gaps)

---

## Phase 4: Executive Reporting

**Goal**: Communicate findings in actionable executive format.

**Duration**: 1-2 days

---

### Report Structure (REA Executive Report)

**Length**: 5-15 pages (vs 15-30 for full systematic review)

**Format**: Executive-friendly (not academic journal style)

---

**1. Executive Summary** (1 page):

```markdown
# Rapid Evidence Assessment: [Topic]

## Research Question
[One sentence: What we investigated]

## Key Findings
1. [Finding 1 with implication]
2. [Finding 2 with implication]
3. [Finding 3 with implication]

## Recommendation
[Primary recommendation based on evidence]

## Evidence Base
- Papers reviewed: [n=X]
- Databases: [List]
- Quality: [X high, Y medium, Z low]

## Limitations
[Key limitation of REA - e.g., limited search scope, single reviewer]
```

---

**2. Background** (1 page):
- Why this question matters
- Context for stakeholders
- Scope and boundaries of REA

---

**3. Methods** (1-2 pages):
- Research question (PICO)
- Databases searched
- Inclusion/exclusion criteria
- Screening and extraction approach
- **Limitations of REA** (acknowledge single reviewer, limited databases)

---

**4. Findings** (3-5 pages):
- **Thematic synthesis** (3-5 themes)
- Evidence per theme (citations, key results)
- Quality of evidence (how confident are we?)
- Simplified methodology table (optional)

**Example theme presentation**:
```markdown
### Finding 1: Psychological Safety Enables Candid Feedback

**Evidence**:
- Smith et al. (2020): Teams with high psychological safety generated 3x more actionable retrospective items (n=40 teams, 6-month study)
- Brown (2022): Qualitative interviews (n=25 team members) revealed fear of blame prevents honest feedback
- Gartner Report (2023): Survey of 500 teams found psychological safety correlated with retrospective satisfaction (r=.62)

**Quality**: High (peer-reviewed studies + industry report converge)

**Implication**: Organizations should invest in psychological safety training before optimizing retrospective formats.
```

---

**5. Gaps & Limitations** (1-2 pages):
- Research gaps (what evidence is missing)
- Limitations of this REA (search scope, single reviewer, time constraints)
- Future research needs

---

**6. Recommendations** (1-2 pages):
- Practical recommendations based on evidence
- Confidence level per recommendation (strong/moderate/weak evidence)
- Implementation considerations

**Example**:
```markdown
## Recommendations

### Recommendation 1: Establish Psychological Safety First [Strong Evidence]
Before optimizing retrospective formats, invest in psychological safety training for teams and managers. Evidence consistently shows safety is prerequisite for effective retrospectives.

**Actions**:
- Manager training on responding to feedback non-defensively
- Establish ground rules (e.g., "no blame" norm)
- Model vulnerability from leadership

**Evidence base**: 12/18 papers, including RCTs and large-scale surveys
```

---

**7. References** (1-2 pages):
- All papers cited (author, year, title, source)
- Simplified citation format (not full academic)

---

**8. Appendix** (optional):
- Search strings
- PRISMA flow diagram
- Methodology comparison table (if useful)

---

### Alternative Format: Slide Deck

**For executive presentation** (15-20 slides):

1. Executive summary (1 slide)
2. Research question and scope (1 slide)
3. Methods overview (1 slide)
4. Key findings (1 slide per theme, 3-5 slides)
5. Evidence quality assessment (1 slide)
6. Gaps and limitations (1 slide)
7. Recommendations (2-3 slides)
8. Q&A

---

### Phase 4 Outputs

- ✅ Executive report (5-15 pages) OR slide deck (15-20 slides)
- ✅ Recommendations with evidence quality indicators
- ✅ Limitations acknowledged

---

## REA Quality Standards

### Must-Haves (Non-Negotiable)

- ✅ Documented protocol (even if internal)
- ✅ Systematic search (2-3 databases minimum)
- ✅ Explicit inclusion/exclusion criteria
- ✅ PRISMA flow diagram (simplified)
- ✅ Thematic synthesis (not paper-by-paper summary)
- ✅ Limitations acknowledged

### Nice-to-Haves (If Time Permits)

- Quality spot check (colleague reviews sample of exclusions)
- Duplicate extraction (for 10-20% of papers)
- Formal quality assessment tool (abbreviated version)
- Full PRISMA checklist (even if not all items applicable)

---

## REA vs Corner-Cutting

**REA is systematic but pragmatic**. It is NOT:
- ❌ Cherry-picking papers that support your view
- ❌ Google Scholar first-page-only review
- ❌ Narrative review dressed up as systematic
- ❌ Skipping documentation of methods

**REA maintains rigor through**:
- ✅ Documented protocol
- ✅ Explicit criteria
- ✅ Systematic search (even if limited)
- ✅ Transparent limitations

---

## When to Use REA vs Full Systematic Review

### Use REA when:
- Timeline: 1-2 weeks available
- Purpose: Internal decision-making, scoping
- Audience: Executives, internal stakeholders
- Stakes: Moderate (not life-or-death policy)
- Resources: Solo or small team

### Use Full Systematic Review when:
- Timeline: 4-8 weeks available
- Purpose: Academic publication, external validation
- Audience: Academic journals, policy-makers, external stakeholders
- Stakes: High (evidence-based policy, clinical guidelines)
- Resources: Team with duplicate reviewers

### Use Both (Sequential):
- **Phase 1**: REA to scope landscape (1-2 weeks)
- **Decision point**: Is comprehensive review warranted?
- **Phase 2** (if yes): Full systematic review (4-8 weeks)

---

## Common Mistakes in REA

### Mistake 1: No Protocol

**Problem**: Starting search without defining question and criteria

**Fix**: Always document protocol first (even 1-page is sufficient)

---

### Mistake 2: Google Scholar Only

**Problem**: Only searching one database, missing key papers

**Fix**: Minimum 2-3 databases (Google Scholar + domain-specific database + grey lit source)

---

### Mistake 3: Paper-by-Paper Summary

**Problem**: Summarizing each paper sequentially (not synthesis)

**Fix**: Organize by theme, synthesize evidence across papers

---

### Mistake 4: Ignoring Limitations

**Problem**: Presenting REA as if it were full systematic review

**Fix**: Transparently acknowledge limitations (single reviewer, limited search, time constraints)

---

### Mistake 5: No Quality Assessment

**Problem**: Treating all evidence as equally credible

**Fix**: At minimum, flag High/Medium/Low quality per paper

---

## REA Checklist

**Before starting**:
- [ ] Research question defined (PICO)
- [ ] Inclusion/exclusion criteria established
- [ ] 2-3 key databases identified
- [ ] Lightweight protocol documented

**During search & screening**:
- [ ] Searches executed and documented
- [ ] Results per database recorded
- [ ] Screening completed (single reviewer)
- [ ] PRISMA flow diagram created

**During synthesis**:
- [ ] Data extracted (streamlined template)
- [ ] Quality flagged (High/Medium/Low)
- [ ] Thematic synthesis completed (NOT paper-by-paper)
- [ ] Gaps identified

**During reporting**:
- [ ] Executive summary written (1 page)
- [ ] Methods documented (with limitations)
- [ ] Findings synthesized thematically
- [ ] Recommendations provided with evidence levels
- [ ] Limitations transparently acknowledged

---

## REA Template

```markdown
# Rapid Evidence Assessment: [Topic]

**Date**: [YYYY-MM-DD]
**Conducted by**: [Name]
**Timeframe**: [Start date - End date]

---

## Executive Summary

**Research Question**: [One sentence]

**Key Findings**:
1. [Finding 1]
2. [Finding 2]
3. [Finding 3]

**Primary Recommendation**: [Based on evidence]

**Evidence Base**: [n=X papers, Y databases, quality distribution]

**Limitations**: [Key REA limitations]

---

## Background

[Why this question matters, context, scope]

---

## Methods

**Research Question (PICO)**:
- Population: [Who/what]
- Intervention/Topic: [What investigated]
- Outcome: [What measured]

**Inclusion Criteria**: [List]
**Exclusion Criteria**: [List]

**Databases**: [2-3 databases + grey lit sources]

**Search Terms**: [Keywords and Boolean]

**Screening**: Single reviewer, [n=X] papers screened, [n=Y] included

**Extraction**: Streamlined template, focus on [key elements]

**Quality Assessment**: High/Medium/Low classification

**Limitations**: Single reviewer, limited databases, [other limitations]

---

## Findings

### Theme 1: [Theme Name]

**Evidence**: [Cite 3-5 key papers with results]

**Quality**: [High/Medium/Low overall]

**Implication**: [What this means]

### Theme 2: [Theme Name]

[Repeat structure]

---

## Gaps & Limitations

**Research Gaps**: [What evidence is missing]

**REA Limitations**: [Acknowledge methodological compromises]

---

## Recommendations

### Recommendation 1: [Action] [Evidence Level: Strong/Moderate/Weak]

[Description, rationale, implementation suggestions]

**Evidence base**: [n=X papers, quality]

---

## References

[All papers cited]

---

## Appendix

**PRISMA Flow Diagram**: [Simplified diagram]

**Search Strings**: [Full Boolean strings per database]
```

---

## Related Documentation

- [[workflow]] - Full systematic review workflow (4-8 weeks)
- [[protocol-phase]] - Detailed protocol guidance
- [[paper-processing]] - Data extraction templates
- [[../../context/research/evidence-synthesis-standards]] - PRISMA 2020 standards

---

## Sources

Based on:
- Grant, M. J., & Booth, A. (2009). A typology of reviews. *Health Information & Libraries Journal*, 26(2), 91-108.
- Tricco, A. C., et al. (2015). A scoping review of rapid review methods. *BMC Medicine*, 13, 224.
- Khangura, S., et al. (2012). Evidence summaries: The evolution of a rapid review approach. *Systematic Reviews*, 1, 10.
- UK Government Rapid Evidence Assessment Toolkit

---

**Use REA when**: Time-constrained (1-2 weeks), internal decision-making, pragmatic evidence needed

**Use Full Systematic Review when**: Academic publication, high-stakes policy, comprehensive evidence required, time available (4-8 weeks)
