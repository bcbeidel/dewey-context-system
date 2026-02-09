# Market Research Workflow

**Purpose**: Understand market dynamics, competitive landscape, and business opportunities.

**Version**: 1.0
**Created**: 2026-02-08
**Status**: Production

---

## Overview

Market research combines qualitative (why) and quantitative (how many) methods to inform strategic business decisions about markets, competitors, and opportunities.

**Core principle**: Triangulate findings from multiple sources (primary + secondary, qual + quant) for robust insights.

**When to use**: Market opportunity assessment, competitive intelligence, market entry strategy, positioning decisions.

---

## Quick Start

**Choose your entry point**:

- **New to market research?** → Start with "What is Market Research?" below
- **Ready to start?** → Jump to Phase 1: Define Objectives
- **Need competitive analysis template?** → See [[competitive-analysis-template]]
- **Want examples?** → See [[examples]]

---

## What is Market Research?

### Two Main Approaches

**1. Qualitative Methods** (understand the "why")
- Focus groups: Group discussions (6-10 people)
- In-depth interviews: 1-on-1 deep dives
- Ethnographic observation: Observe customer behavior
- Online communities: Ongoing discussions

**2. Quantitative Methods** (measure the "how many")
- Surveys: Large-scale questionnaires (n=100+)
- Sales data analysis: Historical transaction data
- Web analytics: Traffic, conversions, behavior metrics
- Market sizing: TAM, SAM, SOM calculations

**Best practice**: Combine both for comprehensive understanding.

**Source**: [[../../context/research/market-research-standards]]

---

## Four-Phase Workflow

### Timeline

**Typical market research project**: 1-4 weeks

**Phase breakdown**:
- Phase 1: Define Objectives (1-2 days)
- Phase 2: Data Collection (1-3 weeks)
- Phase 3: Analysis & Synthesis (3-5 days)
- Phase 4: Communication (1-2 days)

---

## Phase 1: Define Objectives

**Goal**: Clarify what decisions this research will inform and what you need to learn.

**Duration**: 1-2 days

---

### Activities

**1. Identify business decision** (2-4 hours)
- What decision needs to be made?
- Who will make the decision?
- What information would help?

**Example decisions**:
- "Should we enter the data quality tools market?"
- "How should we position against competitor X?"
- "What features would drive market adoption?"

---

**2. Define research objectives** (2-4 hours)
- What do you need to learn?
- What are your hypotheses?
- What are the key questions?

**Good objectives**:
- "Estimate total addressable market (TAM) for data quality SaaS"
- "Identify top 5 competitors and their positioning"
- "Understand customer pain points in current solutions"

**Bad objectives**:
- "Learn about the market" (too vague)
- "Prove our product is better" (biased)

---

**3. Determine research approach** (1-2 hours)

**Choose based on objective**:

| Objective | Primary Approach | Secondary Approach |
|-----------|-----------------|-------------------|
| Market sizing | Secondary research + modeling | Expert interviews |
| Competitive analysis | Secondary (competitor intel) | Mystery shopping |
| Customer needs | Primary (interviews, surveys) | Secondary (reviews, forums) |
| Market trends | Secondary (reports, articles) | Expert interviews |
| Positioning | Competitive analysis + customer research | Surveys |

---

**4. Set success criteria** (1 hour)
- What would "good enough" look like?
- What level of confidence do you need?
- What constraints do you have (time, budget)?

**Template**:
```markdown
# Market Research Objectives

## Business Decision
[What decision will this inform?]

## Research Objectives
1. [Primary objective with success criteria]
2. [Secondary objective with success criteria]

## Key Questions
- [Question 1]
- [Question 2]
- [Question 3]

## Approach
- Primary research: [Methods, sample size]
- Secondary research: [Sources, depth]

## Success Criteria
- [Metric 1: e.g., Confidence level ±10% on market size]
- [Metric 2: e.g., Identify 10+ competitors]

## Constraints
- Timeline: [X weeks]
- Budget: [$X or resource constraints]
```

---

### Phase 1 Outputs

- ✅ Research objectives defined
- ✅ Key questions documented
- ✅ Research approach selected
- ✅ Success criteria set

---

## Phase 2: Data Collection

**Goal**: Gather data from multiple sources (primary and secondary).

**Duration**: 1-3 weeks (varies by scope)

---

### Secondary Research (1-2 weeks)

**What**: Analyze existing information from published sources.

**When to start**: Always start with secondary - it's faster and cheaper.

**Sources**:

**Public sources** (free):
- Government data: Census, BLS, industry reports
- Industry associations: Trade group reports
- Company data: 10-K filings, investor reports, press releases
- Academic research: Journal articles, white papers
- News and media: Industry publications, analyst articles
- Review sites: G2, Capterra, Trustpilot

**Paid sources**:
- Market research reports: Gartner, Forrester, IBISWorld
- Analyst briefings: Custom research
- Subscription databases: Statista, Bloomberg, PitchBook

**Digital sources**:
- Competitor websites: Features, pricing, messaging
- Social media: Mentions, sentiment, engagement
- SEO tools: Keyword rankings, traffic estimates (Semrush, Ahrefs)

**Process**:
1. Define scope (what to research)
2. Identify sources (where to look)
3. Systematic collection (gather data)
4. Document sources (track for citations)

---

### Competitive Analysis (3-5 days)

**Six-step framework**:

1. **Define scope**: What aspects to analyze (features, pricing, positioning, etc.)
2. **Identify competitors**: Direct, indirect, emerging
3. **Gather data**: Multiple sources per competitor
4. **Analyze SWOT**: Strengths, weaknesses, opportunities, threats
5. **Compare**: Side-by-side comparison across criteria
6. **Synthesize**: Patterns, gaps, opportunities

**See**: [[competitive-analysis-template]] for structured template

**Tools**:
- **Crayon, Kompyte, Klue**: AI-enabled competitive intelligence
- **SimilarWeb, Semrush**: Traffic and SEO data
- **G2, Capterra**: Customer reviews and ratings

**Best practice**: Create shared intelligence hub (Confluence, Notion) for ongoing tracking.

---

### Primary Research (1-2 weeks)

**When to use**: Secondary research insufficient, need fresh insights, validate hypotheses.

**Methods**:

**Qualitative** (n=5-15):
- **Customer interviews**: 30-60 min, understand needs and pain points
- **Expert interviews**: Industry experts, analysts
- **Focus groups**: 6-10 people, 90 min, group dynamics

**Quantitative** (n=100+):
- **Surveys**: Online questionnaires, measure preferences and behaviors
- **A/B tests**: Test messaging, pricing, features
- **Behavioral data**: Web analytics, usage metrics

**Process**:
1. Design research instruments (interview guides, surveys)
2. Recruit participants (target market)
3. Conduct research (interviews, surveys)
4. Document findings (notes, recordings, data)

**See**: [[../ux-research/workflow]] for detailed primary research methods

---

### Market Sizing (2-3 days)

**Three-tier approach**:

**TAM (Total Addressable Market)**:
- Total demand if you had 100% market share
- Top-down: Start with total industry, narrow to segment
- Example: "Global data quality market = $2.1B"

**SAM (Serviceable Available Market)**:
- Portion of TAM you can realistically reach
- Consider: Geography, target customer, distribution channels
- Example: "North America mid-market = $350M"

**SOM (Serviceable Obtainable Market)**:
- Portion you can realistically capture in near term
- Consider: Competition, resources, timeline
- Example: "Realistic 3-year target = $15M (5% of SAM)"

**Methods**:
- **Top-down**: Industry reports → narrow to segment
- **Bottom-up**: Unit economics × addressable customers
- **Value theory**: Value delivered × customers willing to pay

---

### Phase 2 Outputs

- ✅ Secondary research summary
- ✅ Competitive analysis (SWOT, comparison matrix)
- ✅ Primary research data (interview notes, survey responses)
- ✅ Market sizing estimates (TAM, SAM, SOM)
- ✅ Source documentation

---

## Phase 3: Analysis & Synthesis

**Goal**: Synthesize findings, identify patterns, generate insights.

**Duration**: 3-5 days

---

### Activities

**1. Organize data** (1 day)
- Compile all sources into shared workspace
- Tag/categorize findings by theme
- Create data inventory (what you have)

---

**2. Cross-source analysis** (1-2 days)

**Triangulate findings**:
- What do multiple sources agree on?
- Where do sources conflict?
- What patterns emerge?

**Example joint display**:
| Finding | Source 1 (Gartner) | Source 2 (Interviews) | Source 3 (Reviews) | Confidence |
|---------|-------------------|---------------------|-------------------|------------|
| Price sensitivity high | "Budget constraints" | 7/10 mentioned price | Avg rating: 3.2/5 on value | High |

---

**3. Competitive positioning** (1 day)

**Create positioning map**:
- X-axis: Key dimension 1 (e.g., ease of use)
- Y-axis: Key dimension 2 (e.g., power/features)
- Plot competitors and identify gaps

**Identify differentiation opportunities**:
- Where are competitors clustered?
- Where are gaps in the market?
- What do customers want that no one offers?

---

**4. Synthesize insights** (1-2 days)

**Answer research objectives**:
- Did we answer our key questions?
- What are the top 5-7 insights?
- What are the implications?

**Prioritize insights by**:
- **Strength of evidence**: Multiple sources = higher confidence
- **Business impact**: How much does it matter?
- **Actionability**: Can we do something about it?

---

### Phase 3 Outputs

- ✅ Insights synthesized (top 5-7)
- ✅ Competitive positioning map
- ✅ Market opportunity assessment
- ✅ Gaps and opportunities identified
- ✅ Recommendations drafted

---

## Phase 4: Communication

**Goal**: Present findings and recommendations to stakeholders.

**Duration**: 1-2 days

---

### Deliverables

**1. Executive summary** (1 page)

**Structure**:
```markdown
# Market Research Executive Summary

## Objective
[What we researched and why]

## Key Findings
1. [Finding 1 with implication]
2. [Finding 2 with implication]
3. [Finding 3 with implication]

## Market Opportunity
- TAM: [$X]
- SAM: [$Y]
- SOM (3-year): [$Z]

## Top Recommendations
1. [Recommendation 1]
2. [Recommendation 2]
3. [Recommendation 3]

## Next Steps
[What to do with this research]
```

---

**2. Detailed report** (10-20 pages)

**Structure**:
1. **Executive Summary** (1 page)
2. **Methodology** (1-2 pages): Sources, approach, limitations
3. **Market Overview** (2-3 pages): Size, trends, segments
4. **Competitive Landscape** (3-5 pages): SWOT, positioning, comparison
5. **Customer Insights** (2-4 pages): Needs, pain points, preferences
6. **Opportunities** (2-3 pages): Market gaps, differentiation
7. **Recommendations** (2-3 pages): Strategic recommendations
8. **Appendices**: Raw data, sources, detailed tables

---

**3. Presentation** (10-15 slides)

**Slide structure**:
1. Title + agenda
2. Research objectives
3. Methodology overview
4. Market size and trends (1-2 slides)
5. Competitive landscape (2-3 slides)
6. Customer insights (2-3 slides)
7. Opportunities (1-2 slides)
8. Recommendations (1-2 slides)
9. Next steps
10. Q&A

**Presentation tips**:
- Lead with insights, not data
- Use visuals (charts, positioning maps)
- Tell a story (setup → findings → implications)
- Be clear about confidence levels
- Link to business strategy

---

**4. Competitive intelligence hub** (ongoing)

**2024 trend**: Centralized platform for ongoing tracking.

**What to include**:
- Competitor profiles (updated quarterly)
- Live alerts on competitor changes
- Share-of-voice tracking
- Sentiment analysis
- Feature comparison matrices

**Tools**: Confluence, Notion, Crayon, Kompyte

---

### Phase 4 Outputs

- ✅ Executive summary (1 page)
- ✅ Detailed report (10-20 pages)
- ✅ Presentation (stakeholder-ready)
- ✅ Competitive intelligence hub (if ongoing)

---

## Specialized Techniques

### Social Media Analytics (2024 Trend)

**Evolution**: Social media analytics becoming serious competitive analysis tool.

**Applications**:
- **Sentiment tracking**: How competitors resonate with customers
- **Share-of-voice**: Brand mention volume comparison
- **Engagement**: Quality of audience interaction
- **Trends**: Emerging topics and conversations

**Tools**: Brandwatch, Sprout Social, Hootsuite Insights, Talkwalker

---

### AI-Enabled Competitive Intelligence

**2024 tools**:
- **Crayon**: Automated competitive intelligence tracking
- **Kompyte**: Real-time competitor monitoring
- **Klue**: Competitive enablement platform

**Capabilities**:
- Auto-alerts on competitor changes (pricing, features, messaging)
- Multi-competitor monitoring at scale
- Trend analysis and pattern recognition
- Integration with CRM and sales tools

---

## Troubleshooting

### "I can't find reliable market size data"

**Common for niche markets**.

**Solutions**:
1. **Bottom-up modeling**: Estimate based on customers × pricing
2. **Adjacent markets**: Use related market data as proxy
3. **Expert interviews**: Ask industry experts for estimates
4. **Triangulate**: Use multiple methods, create range (low/mid/high)
5. **Primary research**: Survey customers about spend

**Be transparent**: Report methodology and confidence level.

---

### "Competitors don't disclose key information"

**Normal - companies protect competitive data**.

**Workarounds**:
1. **Mystery shopping**: Experience as customer
2. **Review mining**: G2, Capterra, Trustpilot for features and pricing
3. **Job postings**: Infer strategy from hiring (e.g., "AI engineer" = AI focus)
4. **Customer interviews**: Ask customers about competitors
5. **Sales team**: Competitive intelligence from deals

---

### "Secondary research is outdated"

**Common in fast-moving markets**.

**Solutions**:
1. **Weight recent sources**: Prioritize 2024-2025 data
2. **Supplement with primary**: Validate with recent interviews
3. **Track trends, not absolutes**: Growth rates may be more reliable than point estimates
4. **Use real-time sources**: Social media, news, earnings calls
5. **Update regularly**: Quarterly refresh for fast markets

---

## Known Limitations

**When market research may not be appropriate**:
- Market too new (no data exists yet)
- Market too niche (can't find representative data)
- Decision already made (research won't influence)
- Moving too fast (research outdated by completion)

**Market research requires**:
- Available data (secondary) or accessible customers (primary)
- 1-4 weeks timeline minimum
- Resources for data collection (subscriptions, recruiting)
- Stakeholder willingness to act on findings

---

## Integration with Other Methods

**Common combinations**:
- **Market + UX Research**: Market opportunity + user needs
- **Market + Case Study**: Market analysis + customer success stories
- **Market + Evidence Synthesis**: Industry trends + academic research

---

## Related Documentation

**Core reference**:
- [[../../context/research/market-research-standards]] - Research standards and sources
- [[competitive-analysis-template]] - Structured competitive analysis
- [[examples]] - Real market research projects

**Other methodologies**:
- [[../ux-research/workflow]] - For primary research methods
- [[../evidence-synthesis/workflow]] - For industry literature review

---

## Sources

Based on:
- [[../../context/research/market-research-standards]]
- Industry best practices (2024-2025)
- U.S. Small Business Administration market research guidance

---

**First Use**: Define your business decision and research objectives, then work through Phase 1
