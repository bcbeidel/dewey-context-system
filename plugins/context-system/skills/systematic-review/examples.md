# Usage Examples & Customization

**Purpose**: Practical examples of literature review skill usage and customization options.

---

## Example 1: Thesis Literature Review

### Scenario
Graduate student preparing comprehensive literature review for thesis on spaced repetition effectiveness.

### Command
```bash
/systematic-review --topic="Spaced Repetition Effectiveness"
```

### Parameters
- **Papers**: 10-20 academic papers
- **Output**: Comprehensive 15-20 page review
- **Depth**: Full systematic review
- **Time**: 8-12 hours of work

### What Gets Created
1. Individual paper extraction notes (one per paper)
2. Methodology comparison table
3. Thematic findings synthesis
4. Citation network map
5. Research gap analysis
6. Final comprehensive literature review document

### Use Cases
- Graduate thesis
- Dissertation
- Comprehensive exam preparation
- Major research project foundation

---

## Example 2: Research Paper Background

### Scenario
Writing research paper, need literature review section to establish context and justify study.

### Command
```bash
/systematic-review --topic="LLM Security" --depth=focused
```

### Parameters
- **Papers**: 5-8 key papers
- **Output**: Concise 3-5 page review for background section
- **Depth**: Focused on most relevant studies
- **Time**: 2-4 hours of work

### What Gets Created
1. Focused paper extractions (5-8 papers)
2. Brief methodology comparison
3. Key findings synthesis
4. Targeted gap analysis leading to your research question
5. Condensed literature review suitable for paper Section 2

### Use Cases
- Research paper background section
- Conference paper literature review
- Grant proposal justification
- Technical report foundation

---

## Example 3: Learning Domain Exploration

### Scenario
Personal learning goal: deeply understand academic foundation of topic through scholarly research.

### Command
```bash
/systematic-review --topic="Mental Models in Decision Making"
```

### Parameters
- **Papers**: 8-12 papers (mix of classic and recent)
- **Output**: Standard literature review with focus on understanding
- **Depth**: Moderate, emphasis on synthesis and insights
- **Time**: 4-6 hours

### What Gets Created
1. Paper extractions with personal notes emphasized
2. Conceptual synthesis (what patterns emerge)
3. Theoretical framework understanding
4. Personal insights and connections
5. Review document for future reference

### Use Cases
- Deep dive into topic
- Understanding research foundation
- Preparing to write about topic
- Building expertise systematically

---

## Example 4: Quick Topic Assessment

### Scenario
Need to quickly understand state of research in a domain before deciding if deeper investigation warranted.

### Command
```bash
/systematic-review --topic="Blockchain in Healthcare" --depth=quick
```

### Parameters
- **Papers**: 3-5 key papers
- **Output**: Brief summary (2-3 pages)
- **Depth**: Highlights only
- **Time**: 1-2 hours

### What Gets Created
1. Quick extractions of key papers
2. Summary table of main findings
3. Brief assessment of research maturity
4. Quick gap identification
5. Executive summary document

### Use Cases
- Preliminary research
- Topic selection for larger project
- Rapid domain assessment
- Feasibility evaluation

---

## Customization Options

### Review Depth

```bash
# Comprehensive systematic review (20+ papers)
/systematic-review [topic] --depth=comprehensive

# Standard focused review (10-15 papers)
/systematic-review [topic] --depth=focused

# Quick overview (5-8 papers)
/systematic-review [topic] --depth=moderate

# Rapid assessment (3-5 papers)
/systematic-review [topic] --depth=quick
```

**Depth Comparison**:

| Depth | Papers | Pages | Time | Best For |
|-------|--------|-------|------|----------|
| Comprehensive | 20+ | 15-20 | 8-12h | Dissertation, thesis |
| Focused | 10-15 | 8-12 | 4-6h | Research papers |
| Moderate | 5-8 | 4-6 | 2-4h | Background sections |
| Quick | 3-5 | 2-3 | 1-2h | Preliminary research |

---

### Citation Style

```bash
# APA 7th edition (default, most common)
/systematic-review [topic] --citation=apa

# Chicago style
/systematic-review [topic] --citation=chicago

# MLA style
/systematic-review [topic] --citation=mla
```

**Citation Format Examples**:

**APA**: Author, A. A. (2020). Title of article. *Journal Name*, *12*(3), 45-67. https://doi.org/xxx

**Chicago**: Author, First. "Title of Article." *Journal Name* 12, no. 3 (2020): 45-67.

**MLA**: Author, First. "Title of Article." *Journal Name*, vol. 12, no. 3, 2020, pp. 45-67.

---

### Output Format

```bash
# Complete review document (default)
/systematic-review [topic] --format=full

# Executive summary only
/systematic-review [topic] --format=summary

# Comparison table focus
/systematic-review [topic] --format=table

# Annotated bibliography style
/systematic-review [topic] --format=annotated
```

**Format Descriptions**:

**Full**: Complete literature review with all sections (introduction, methodology, findings, gaps, conclusion)

**Summary**: Executive summary focusing on key findings and gaps (1-2 pages)

**Table**: Emphasis on methodology comparison table with brief synthesis

**Annotated**: Annotated bibliography format (each paper summarized individually, plus synthesis)

---

### Combined Customization

```bash
# Comprehensive review, Chicago style, full format
/systematic-review "Cognitive Load Theory" --depth=comprehensive --citation=chicago --format=full

# Quick review, APA style, summary format
/systematic-review "AI in Education" --depth=quick --citation=apa --format=summary

# Focused review, default settings
/systematic-review "Memory Consolidation"
```

---

## Time Investment Guidelines

### Comprehensive Review (20+ papers)
**Total Time**: 8-12 hours

- **Paper collection**: 1-2 hours
- **Paper reading & extraction**: 4-6 hours (20-30 min per paper)
- **Synthesis & analysis**: 2-3 hours
- **Writing & editing**: 2-3 hours

### Focused Review (10-15 papers)
**Total Time**: 4-6 hours

- **Paper collection**: 30-60 minutes
- **Paper reading & extraction**: 2-3 hours (15-20 min per paper)
- **Synthesis & analysis**: 1-2 hours
- **Writing & editing**: 1-2 hours

### Moderate Review (5-8 papers)
**Total Time**: 2-4 hours

- **Paper collection**: 30 minutes
- **Paper reading & extraction**: 1-2 hours (15 min per paper)
- **Synthesis & analysis**: 30-60 minutes
- **Writing & editing**: 30-60 minutes

### Quick Review (3-5 papers)
**Total Time**: 1-2 hours

- **Paper collection**: 15-30 minutes
- **Paper reading & extraction**: 30-60 minutes (10 min per paper)
- **Synthesis & analysis**: 15-30 minutes
- **Writing & editing**: 15-30 minutes

---

## Integration Examples

### With `/research-synthesis`

**When to use which**:

```bash
# Academic papers, formal citations, systematic methodology
/systematic-review "Spaced Repetition Research"

# General sources (podcasts, books, articles, blogs)
/research-synthesis "Learning Science Insights"
```

**Combined workflow**:
1. Start with `/research-synthesis` for broad understanding (podcasts, books)
2. Follow with `/systematic-review` for academic rigor (research papers)
3. Result: Both practical insights and scholarly foundation

---

### With `/mental-model`

**Extract mental models from research**:

```bash
# First: Review academic literature
/systematic-review "Decision Making Under Uncertainty"

# Second: Create mental model from theoretical framework
/mental-model "Prospect Theory"
# Based on: Findings from literature review
```

**Workflow**:
1. Literature review identifies key theoretical frameworks
2. Extract most useful framework as mental model
3. Mental model becomes practical tool based on research

---

### With `/learn`

**Learn concepts from research findings**:

```bash
# First: Review research
/systematic-review "Spaced Repetition Effectiveness"

# Second: Learn the principles discovered
/learn start "Optimal spacing intervals"
# Based on: Research findings from review
```

**Workflow**:
1. Literature review establishes evidence-based principles
2. Use `/learn` to internalize these principles
3. Apply research-backed techniques to your own learning

---

## Best Practices by Use Case

### For Academic Writing (Thesis/Dissertation)
- Use comprehensive depth
- Include all phases (scoping through output)
- Emphasize methodological rigor
- Document search strategy thoroughly
- Include PRISMA-style flowchart if applicable

### For Research Papers
- Use focused depth
- Emphasize findings that justify your study
- Highlight research gaps your work addresses
- Keep citations current (majority from last 5 years)
- Synthesize thematically (not paper-by-paper)

### For Personal Learning
- Use moderate depth
- Emphasize conceptual understanding
- Connect to personal knowledge and experience
- Create mental models from frameworks
- Focus on practical implications

### For Quick Assessment
- Use quick depth
- Identify key findings rapidly
- Assess research maturity
- Determine if deeper investigation warranted
- Focus on recency and influence (highly cited papers)

---

## What Works Well

### Strengths of Literature Review Skill
- Systematic comparison of research studies
- Identifying consensus and contradictions in literature
- Tracking theoretical development over time
- Finding and articulating research gaps
- Creating academic-quality review documents
- Organizing large amounts of research systematically

### Optimal Conditions
- Access to academic papers (PDFs or full-text)
- Clear research question defined
- 5-20 papers (manageable scope)
- Papers in similar domain (allows meaningful synthesis)
- Mix of methodologies (enables rich comparison)

---

## Limitations & Challenges

### What's Challenging

**Paper Access**:
- Skill cannot access paywalled papers
- User must provide papers (PDFs, URLs, or access)
- Consider using institutional library access

**Technical Complexity**:
- Highly technical statistical analysis may require expertise
- Domain-specific jargon needs user familiarity
- Advanced methodologies may need clarification

**Scale Limitations**:
- Very large reviews (50+ papers) become unwieldy
- Consider breaking into sub-topics
- Use systematic review software for massive projects

**Subjective Judgment**:
- Quality assessment has subjective elements
- Gap identification requires domain knowledge
- Synthesis decisions involve interpretation

### Workarounds

**For paywalled papers**: Use Google Scholar, ResearchGate, author websites, request from authors

**For technical complexity**: Focus on practical interpretation, note methods used, seek clarification when needed

**For large reviews**: Break into themes, do multiple smaller reviews, use reference management software

---

## Success Criteria

**You know the review is successful when**:
- You understand the research landscape in the domain
- You can identify areas of consensus and debate
- You know what gaps exist in current knowledge
- You can explain theoretical frameworks used
- You have a publication-ready review document
- You can articulate future research directions
- You feel confident discussing the topic academically

---

**Related**: [[SKILL|Back to Overview]]
