---
name: researcher
description: "Multi-methodology research orchestrator with intelligent methodology selection for technology, marketing, and software contexts"
allowed-tools: Read, Write, WebFetch, WebSearch, Glob, AskUserQuestion
---

# Researcher

**Multi-methodology research orchestrator** with intelligent methodology selection wizard.

Supports 7 research methodologies for technology evaluation, user understanding, market analysis, and organizational research - from quick 3-day assessments to comprehensive 8-week studies.

---

## Overview

### What This Skill Does

Guides you from **research problem → methodology selection → execution** with:
- **Intelligent selection**: 8-12 question wizard recommends best methodology
- **7 methodologies**: Evidence synthesis, design science, UX, market, mixed methods, case study, organizational culture
- **Business-focused**: Practical timelines (REA: 3-7 days, Culture Assessment: 1-2 weeks)
- **Educational**: Learn why each methodology fits your needs

### When to Use This Skill

**✅ Use `/researcher` when you need**:
- Technology evaluation or vendor assessment
- User research or product validation
- Market opportunity analysis
- Data culture assessment or change readiness
- Complex problems needing multiple perspectives
- Rigorous evidence for decision-making

**❌ Skip this skill for**:
- Quick Google searches (faster to search directly)
- Pure data analysis (use statistical software)
- Research already complete (use `/context-curator` for insights extraction)

---

## Quick Start

### Decision Tree

**Choose your entry based on problem type:**

- **Evaluate technology or synthesize best practices?** → Evidence Synthesis & Systematic Review
- **Building or evaluating technology?** → Design Science Research
- **Understanding users or customers?** → UX Research
- **Market opportunity or competitive analysis?** → Market Research
- **Complex problem needing multiple angles?** → Mixed Methods Research
- **Deep dive on specific case?** → Case Study Research
- **Data culture or organizational change?** → Organizational & Culture Research

**Not sure?** → Use the wizard (recommended)

---

### Three Ways to Use This Skill

#### 1. Methodology Wizard (Recommended for First-Time)

```bash
/researcher
```

- Answer 8-12 questions about your research problem
- Get intelligent recommendation with rationale
- Learn why each methodology fits (or doesn't)
- See alternatives if unsure

**Time**: 5-10 minutes for wizard
**Output**: Personalized methodology recommendation

---

#### 2. Direct Access (If You Know Which Methodology)

```bash
/researcher --method=[methodology-name]
```

**Available methods**:
- `evidence-synthesis` (or `systematic-review`, `prisma`, `rea`)
- `design-science` (or `dsr`)
- `ux-research` (or `ux`)
- `market-research` (or `market`)
- `mixed-methods` (or `mixed`)
- `case-study` (or `case`)
- `organizational-culture` (or `culture`, `ethnographic`)

**Example**:
```bash
/researcher --method=ux-research
```

---

#### 3. Browse Methodologies (Explore All Options)

See detailed comparison: [[methodology-taxonomy]]

---

## Supported Methodologies

### Evidence Synthesis & Systematic Review

**What**: Technology evaluation and best practice synthesis (REA: 3-7 days) or full academic literature synthesis (PRISMA 2020: 2-8 weeks)

**When to use**:
- Technology/vendor evaluation (compare ML frameworks, data platforms)
- Best practice research (data governance, AI adoption patterns)
- Strategic briefings (emerging tech assessments for executives)
- Academic publication (PRISMA 2020 compliant)

**VP Data use cases**: Technology selection, vendor assessment, best practice synthesis

**Consulting use cases**: Client technology evaluations, emerging tech research, proposal backing

**Duration**: 3 days (REA) to 8 weeks (Full PRISMA)
**Complexity**: Medium-High
**Experience**: REA (some), Full PRISMA (experienced)

→ [[evidence-synthesis/workflow]]

---

### Design Science Research

**What**: Iterative technology artifact development and evaluation through build-evaluate cycles

**When to use**:
- Building data platforms or ML systems
- Prototyping new tools or frameworks
- Proof-of-concept development
- Evaluating technical solutions iteratively

**VP Data use cases**: Data platform development, ML pipeline evaluation, governance frameworks

**Consulting use cases**: Client solution prototyping, proof of concepts, technical deliverables

**Duration**: 4-12 weeks (2-4 build-evaluate cycles)
**Complexity**: High
**Experience**: Some to experienced

→ [[design-science/workflow]]

---

### UX/User Research

**What**: Understanding user needs, behaviors, and attitudes through 12+ methods (interviews, surveys, usability testing, etc.)

**When to use**:
- Dashboard UX or self-service analytics usability
- Product design and user validation
- Understanding adoption barriers
- Design system evaluation

**VP Data use cases**: Dashboard UX, data product design, self-service analytics usability

**Consulting use cases**: User validation, digital transformation UX, product design

**Duration**: 1-4 weeks
**Complexity**: Low-Medium
**Experience**: Beginner-friendly

→ [[ux-research/workflow]]

---

### Market Research

**What**: Market analysis, competitive intelligence, and opportunity assessment

**When to use**:
- Competitive intelligence on data tools or AI platforms
- Market opportunity assessment
- Market entry strategy
- Industry trend analysis

**VP Data use cases**: Competitive intelligence, AI/ML market trends, data tool evaluations

**Consulting use cases**: Competitive positioning, market entry strategies, client industry research

**Duration**: 1-4 weeks
**Complexity**: Low-Medium
**Experience**: Beginner-friendly

→ [[market-research/workflow]]

---

### Mixed Methods Research

**What**: Combining qualitative and quantitative methods for complex, interdisciplinary problems

**When to use**:
- Data culture + usage metrics (qual + quant)
- AI adoption + business impact studies
- Complex problems needing multiple perspectives
- Exploratory research with validation

**VP Data use cases**: Data culture + metrics, AI adoption + impact, complex strategic problems

**Consulting use cases**: Complex client problems, hypothesis-driven + data-driven analysis

**Duration**: 3-8 weeks
**Complexity**: High
**Experience**: Experienced recommended

**Three approaches**:
- Convergent (parallel qual + quant)
- Explanatory Sequential (quant → qual)
- Exploratory Sequential (qual → quant)

→ [[mixed-methods/workflow]]

---

### Case Study Research

**What**: In-depth study of specific instances or implementations in real-world context

**When to use**:
- Data transformation success stories
- Implementation pattern analysis
- Technology adoption case studies
- Post-implementation retrospectives

**VP Data use cases**: Data transformation cases, implementation patterns, success stories

**Consulting use cases**: Client success stories, implementation retrospectives, case examples

**Duration**: 2-6 weeks
**Complexity**: Medium
**Experience**: Some experience helpful

→ [[case-study/workflow]]

---

### Organizational & Culture Research

**What**: Data culture assessment, tool adoption research, change management (Culture Assessment: 1-2 weeks, Applied Research: 2-4 weeks, Focused Ethnography: 4-8 weeks)

**When to use**:
- Data culture assessment (barriers, enablers)
- Tool adoption research (why aren't teams using self-service analytics?)
- Change management and readiness
- Post-merger integration

**VP Data use cases**: Data culture assessment, tool adoption barriers, change management

**Consulting use cases**: Organizational change management, digital transformation readiness, culture integration

**Duration**: 1-8 weeks (depending on approach)
**Complexity**: Medium-High
**Experience**: Culture Assessment (some), Ethnography (experienced)

**Three approaches**:
- Structured Culture Assessment (1-2 weeks, OCAI/Denison tools)
- Applied Organizational Research (2-4 weeks, surveys + interviews)
- Focused Ethnography (4-8 weeks, deep immersion)

→ [[organizational-culture/workflow]]

---

## Methodology Selection Wizard

### How It Works

**Full Mode** (`/researcher`):
1. **8-12 questions** about your research problem
2. **Educational content** explaining why each question matters
3. **Intelligent scoring** across all 7 methodologies
4. **Personalized recommendation** with rationale
5. **Alternative options** if unsure

**Time**: 5-10 minutes
**Accuracy**: High (95%+)
**Output**: Methodology recommendation + execution guide

---

### Speed Mode

**For experienced researchers**: `/researcher --quick`

- **3 questions**: Goal, timeline, experience
- **Fast path**: 2-3 minutes
- **Accuracy**: Good (80%)

---

### Browse Mode

**Not sure what you need?** Browse all methodologies:

→ [[methodology-taxonomy]] for full comparison matrix

---

## Integration

### Works With Other Skills

- **`/planner`**: Structure multi-phase research projects with milestones
- **`/compare`**: Compare methodology options or research approaches
- **`/context-curator`**: Extract research insights into persistent context
- **`/auditor`**: Quality assessment of research process and outputs
- **`/diagram`**: Visualize research findings, frameworks, citation networks

---

### Common Patterns

**Sequential combinations**:
- Evidence Synthesis → Design Science: Review literature → Build artifact
- UX Research → Design Science: Understand users → Iterative development
- Market Research → UX Research: Market opportunity → User validation

**Parallel combinations**:
- UX Research + Market Research: User needs + market dynamics (Mixed Methods)
- Evidence Synthesis + Case Study: Best practices + real-world implementation

→ [[integration-patterns]] for detailed examples

---

## Troubleshooting

### "I don't know which methodology to use"

**Solution**: Use the methodology wizard (`/researcher`) - it will ask questions to help you discover the right approach.

**Why this helps**: The wizard considers your problem type, timeline, experience, and constraints to recommend the best fit.

---

### "The wizard recommended [X] but I want [Y]"

**Solution**: You can override the recommendation:

```bash
/researcher --method=[Y]
```

The wizard is a guide, not a requirement. If you have specific reasons for choosing a different methodology, go ahead.

**When to override**: You have domain expertise, tried the recommended approach before, or have organizational constraints.

---

### "Can I combine multiple methodologies?"

**Solution**: Yes! Many research projects benefit from combining approaches.

**Common combinations**:
- Systematic Review + Design Science (literature → prototype)
- UX Research + Market Research (users + market)
- Case Study + Organizational Culture (implementation + culture context)

→ See [[integration-patterns]] for combination strategies

---

### "My timeline is too short for the recommended methodology"

**Solution**: Consider these options:

1. **Use lighter-weight variant**: REA instead of Full PRISMA, Culture Assessment instead of Ethnography
2. **Choose faster methodology**: UX Research or Market Research (1-2 weeks)
3. **Reduce scope**: Focus on specific sub-question, fewer participants
4. **Extend timeline**: If possible, negotiate for more time

**Rerun wizard** with adjusted timeline to get new recommendation.

---

### "I'm getting conflicting results from qualitative and quantitative data"

**Solution**: This is normal in mixed methods research!

Contradictions often reveal important insights:
- Different phenomena (qual and quant measuring different things)
- Methodological artifacts (measurement issues)
- Genuine complexity (real-world ambiguity)

→ See [[mixed-methods/resolving-contradictions]] for integration strategies

---

### "The methodology workflow is too complex"

**Solution**: Start with Phase 1 only.

Most workflows are designed for comprehensive research, but can be adapted:
- **Lite version**: Execute Phase 1-2 only
- **Focused scope**: Narrow research question
- **Reduced sample**: Fewer participants/sources

**Remember**: Some rigor is better than no research at all.

---

## Known Limitations

### Methodology Scope

**Included**: 7 most relevant for technology, marketing, and software contexts

**Not included** (but may add in future):
- Experimental research (RCTs, A/B testing as primary method)
- Action research (practitioner-led change research)
- Grounded theory (theory development from data)
- Phenomenology (lived experience research)
- Meta-analysis (statistical synthesis of studies)
- Delphi studies (expert consensus methods)

**Why these 7?**: Most applicable to VP Data and technology consulting contexts, well-documented, practical timelines.

---

### Experience Requirements

**Beginner-friendly**:
- ✅ UX Research (basic methods)
- ✅ Market Research (secondary research)
- ✅ Rapid Evidence Assessment (REA)

**Some experience helpful**:
- ⚠️ Case Study
- ⚠️ Design Science (single cycle)
- ⚠️ Culture Assessment

**Advanced skills required**:
- ❌ Full Systematic Review (PRISMA 2020)
- ❌ Mixed Methods (coordinating multiple data streams)
- ❌ Focused Ethnography (cultural sensitivity, reflexivity)

**Wizard will warn** about experience mismatches.

---

### Tool Constraints

**Requires**:
- Web access for literature/market research (WebSearch, WebFetch)
- External tools for some methods (survey platforms, analysis software)
- Manual data collection (participant recruitment, interviews)

**Does not provide**:
- Automated statistical analysis (use R, Python, SPSS)
- Participant recruitment (external)
- Survey hosting (use Qualtrics, SurveyMonkey)
- Full automation (guidance only, not execution)

---

### When This Skill May Not Help

**Too simple**:
- One-off quick questions (Google faster)
- Obvious answers (don't need formal research)

**Too complex**:
- Multi-year research programs (break into phases)
- Requires specialized equipment (lab research)

**Wrong tool**:
- Pure data analysis (use statistical software)
- Research already complete (use `/context-curator` for extraction)

---

## Examples

### Scenario 1: Technology Evaluation

**Goal**: Evaluate AI agent architectures for production deployment

**Wizard recommendation**: Mixed Methods (Evidence Synthesis + Design Science)
- Phase 1 (2 weeks): REA on agent architectures in literature
- Phase 2 (4 weeks): Prototype 2-3 architectures and evaluate

**Outcome**: Literature synthesis + prototype evaluation + production recommendation

→ [[examples#technology-evaluation]]

---

### Scenario 2: Product UX Issue

**Goal**: Understand why users abandon checkout flow

**Wizard recommendation**: UX Research (User Interviews + Usability Testing)
- Phase 1 (1 week): 8 user interviews to identify pain points
- Phase 2 (1 week): Usability testing on checkout flow

**Outcome**: 8 pain points identified, design recommendations, wireframe mockups

→ [[examples#product-ux-issue]]

---

### Scenario 3: Market Opportunity Assessment

**Goal**: Assess SaaS market opportunity for data quality tool

**Wizard recommendation**: Market Research (Competitive Analysis + Customer Surveys)
- Phase 1 (1 week): Competitive landscape analysis (20 competitors)
- Phase 2 (2 weeks): Customer surveys (n=150) + interviews (n=10)

**Outcome**: Market sizing ($2.5B TAM), positioning strategy, go-to-market recommendations

→ [[examples#market-opportunity]]

---

For detailed walkthroughs: [[examples]]

---

## Related Documentation

**Core files**:
- [[methodology-taxonomy]] - Complete methodology comparison
- [[methodology-selection-wizard]] - Wizard implementation details (for developers)
- [[integration-patterns]] - How researcher works with other skills
- [[examples]] - Real-world scenarios

**Methodology workflows**:
- [[evidence-synthesis/workflow]]
- [[design-science/workflow]]
- [[ux-research/workflow]]
- [[market-research/workflow]]
- [[mixed-methods/workflow]]
- [[case-study/workflow]]
- [[organizational-culture/workflow]]

---

## Version History

**v1.0** (2026-02-08):
- Initial release with 7 methodologies
- Intelligent methodology selection wizard
- Business-focused framing (VP Data, consulting use cases)
- Progressive disclosure (<350 lines main SKILL.md)
- Comprehensive reference documentation

---

**Created**: 2026-02-08
**Status**: ✅ Ready for Milestone 3 (methodology workflow implementation)

**Next**: Implement individual methodology workflows

---

**First Use**: Describe your research problem and let the wizard guide you to the right methodology.
