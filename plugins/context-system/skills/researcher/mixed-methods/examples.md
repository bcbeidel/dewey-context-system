# Mixed Methods Research Examples

**Purpose**: Real-world mixed methods project walkthroughs across different designs.

**Created**: 2026-02-08

---

## Example 1: Employee Turnover Study (Explanatory Sequential)

### Context

**Business decision**: Why is turnover increasing in engineering department?

**Stakeholders**: CHRO, VP Engineering, Talent team

**Timeline**: 5 weeks

**Design chosen**: Explanatory Sequential (QUAN → qual)
- Priority: Quantitative (measure turnover patterns)
- Purpose: Qualitative explains quant findings

---

### Phase 1: Quantitative Data Collection (Week 1-2)

**Data source**: HR database (N=450 engineers, 3-year history)

**Variables**:
- Turnover (left company: yes/no)
- Tenure (months at company)
- Role level (junior, mid, senior, lead)
- Team size
- Manager tenure
- Promotion history
- Performance ratings

**Analysis** (Week 2):
- Descriptive: 22% annual turnover (vs 15% industry average)
- Cox regression: Tenure, role level, manager tenure predict turnover
- Survival analysis: Turnover spikes at 18 months, 36 months

**Key finding**: Mid-level engineers (2-4 years tenure) have highest turnover (32% vs 15% junior, 12% senior)

**Question for Phase 2**: WHY do mid-level engineers leave at higher rates?

---

### Connection Point (Week 2-3)

**Participant selection strategy**:
- Interview recent leavers (exited in past 6 months)
- Focus on mid-level engineers (where spike occurred)
- Recruit: 12 participants (8 voluntary exits, 4 stayed but considered leaving)

**Interview protocol designed from quant**:
- "You left at [X months]. What was happening at that point?"
- "As a mid-level engineer, what career factors mattered most?"
- "What would have made you stay?"

---

### Phase 2: Qualitative Data Collection (Week 3-4)

**Interviews**: 12 participants, 45-60 min each

**Key themes** (Week 4 analysis):

**Theme 1: The "Mid-Level Trap"** (10/12 participants)
- "I was too experienced for junior work but not given senior opportunities"
- "Stuck doing implementation without influence on architecture"
- "Other companies offered senior roles, here I'd wait 2+ years"

**Theme 2: Compensation Ceiling** (9/12 participants)
- "To get a significant raise, I had to leave"
- "Internal bands capped at 10%, external offers were 30%+ more"
- "Company values tenure over skill growth"

**Theme 3: Manager Quality** (7/12 participants)
- "My manager had been in role only 6 months when I left"
- "Didn't get technical mentorship I needed to grow"
- "New manager didn't know how to advocate for my promotion"

**Theme 4: Competing Offers** (8/12 participants)
- "Recruiters target engineers with 2-4 years experience"
- "Easy to interview, had proof of competence"
- "Exciting opportunities at growing companies"

---

### Phase 3: Integration (Week 4-5)

**Joint display**:

| Quant Finding | Qual Explanation | Integrated Insight |
|---------------|------------------|-------------------|
| Turnover peaks at 18-36 months | "Mid-level trap" theme (10/12) | **Mid-level engineers outgrow junior work but aren't promoted fast enough** |
| Manager tenure predicts turnover (r = -.34) | Manager quality theme (7/12) | **New managers lack skills to mentor and advocate for mid-level engineers** |
| Role level predicts retention (OR = 2.1 for mid) | Compensation + opportunities themes | **Mid-level engineers have highest external demand but lowest internal mobility** |

**Meta-inference**: Mid-level engineers face "growth ceiling" - skills outpace role, but promotion pipeline is slow. This coincides with peak external demand, creating perfect exit conditions.

---

### Deliverables (Week 5)

**Report sections**:
1. Quant findings: Turnover patterns and predictors
2. Qual findings: Lived experiences of leavers
3. **Integrated findings**: "The Mid-Level Trap" phenomenon
4. Recommendations grounded in integration

**Recommendations**:
1. **Accelerate mid-level promotions** (addresses trap)
   - Evidence: Quant shows 18-36 month spike + qual reveals growth frustration

2. **Manager training for new managers** (addresses mentorship gap)
   - Evidence: Quant shows manager tenure effect + qual reveals coaching needs

3. **Competitive compensation reviews at 2-year mark** (addresses external pressure)
   - Evidence: Qual reveals 30%+ external offers + quant shows timing

4. **Senior opportunities for mid-level** (addresses scope limitation)
   - Evidence: Qual reveals desire for influence + quant shows senior retention is higher

---

### Key Learnings

**What worked**:
- Quant identified WHERE turnover concentrated (mid-level, 18-36 months)
- Qual explained WHY (growth ceiling, compensation, manager quality)
- Integration created actionable "Mid-Level Trap" framing

**What didn't**:
- Initial interview protocol too broad - revised after first 3 interviews
- Wish we had interviewed managers too (qual limitation)

**Outcome**: CHRO implemented all 4 recommendations, mid-level turnover dropped from 32% to 19% over next 12 months

---

## Example 2: Product Feature Adoption (Convergent Design)

### Context

**Business decision**: New collaboration feature has low adoption - why?

**Stakeholders**: VP Product, Head of Research

**Timeline**: 4 weeks

**Design chosen**: Convergent (parallel qual + quant)
- Priority: Equal (want comprehensive understanding)
- Purpose: Triangulation (validate across methods)

---

### Phase 1: Parallel Data Collection (Week 1-3)

**Quantitative Component** (Week 1-2, n=1,200):

**Survey questions**:
- "Have you tried the collaboration feature?" (awareness)
- "How often do you use it?" (adoption)
- "How likely are you to recommend?" (NPS)
- "What prevents you from using it?" (barriers - multiple choice)

**Results**:
- Awareness: 68% (good)
- Tried: 45% (moderate)
- Regular use: 12% (poor)
- Top barriers: "Unclear value" (52%), "Too complex" (41%), "Team doesn't use" (38%)

---

**Qualitative Component** (Week 2-3, n=18):

**Interview selection**:
- 6 non-users (never tried)
- 6 light users (tried once)
- 6 power users (weekly+)

**Key themes**:

**Non-users** (6 participants):
- "Didn't know it existed until survey"
- "Have tools that work, why switch?"
- "Seems like extra steps for same outcome"

**Light users** (6 participants):
- "Tried it, couldn't figure out how to invite team"
- "Takes too long to set up, just used Slack"
- "Cool idea but no one else uses it"

**Power users** (6 participants):
- "Game-changer for async collaboration"
- "But only works if whole team commits"
- "Wish it integrated with our existing tools"

---

### Phase 2: Separate Analysis (Week 3)

**Quant analysis**:
- Adoption funnel: 68% aware → 45% tried → 12% regular
- Biggest drop: Tried → regular (33% conversion)
- Barrier regression: "Team doesn't use" predicts non-adoption (OR = 4.2)

**Qual analysis**:
- Non-users lack awareness or motivation
- Light users face usability issues
- Power users need team adoption to get value
- Network effects critical (collaboration = multi-player)

---

### Phase 3: Integration (Week 4)

**Joint display**:

| Theme (Qual) | Frequency (Qual) | Survey Finding (Quant) | % Reporting (Quant) | Integration |
|--------------|------------------|------------------------|---------------------|-------------|
| Unclear value | Non-users (6/6) | "Unclear value" barrier | 52% | **Confirms**: Value prop not landing |
| Usability issues | Light users (6/6) | "Too complex" barrier | 41% | **Confirms**: Onboarding friction |
| Network effects | Power users (6/6) | "Team doesn't use" barrier | 38% (predicts non-adoption, OR=4.2) | **Strong confirms**: Collaboration requires critical mass |
| Awareness gaps | Non-users (4/6) | 32% unaware | 32% | **Confirms**: Discovery problem |
| Integration desire | Power users (4/6) | Not measured | N/A | **New insight**: Add to quant next iteration |

**Meta-inferences**:

1. **Three adoption barriers** (triangulated across methods):
   - Discovery/Awareness (quant: 32% unaware, qual: non-users didn't know)
   - Usability (quant: 41% "too complex", qual: light users struggled)
   - Network effects (quant: 38% "team doesn't use", OR=4.2, qual: power users need team commitment)

2. **Adoption funnel diagnoses**:
   - Awareness → Tried: Communication problem
   - Tried → Regular: Usability + network effects (interdependent)

3. **Critical insight from integration**: Feature is inherently multi-player but marketed/onboarded as single-player. Network effects barrier is structural, not just adoption lag.

---

### Deliverables (Week 4)

**Integrated findings presentation**:

**Slide 1: Adoption funnel** (quant)
- 68% → 45% → 12%
- Conversion drops at trial-to-regular

**Slide 2: Three barriers** (joint display)
- Discovery, Usability, Network effects
- Both methods converge on same 3 barriers

**Slide 3: The network effects trap** (integration)
- Feature requires team adoption to deliver value
- Individual users can't get value alone
- Current onboarding treats as single-player
- **This is why 33% convert from trial to regular** (need critical mass)

**Recommendations**:
1. **Team-based onboarding** (addresses network effects)
   - Pilot with entire teams, not individuals
   - Measure team adoption, not individual

2. **Simplify initial setup** (addresses usability)
   - Reduce steps to first success
   - Guided walkthrough for first collaboration

3. **Better value communication** (addresses awareness)
   - Show collaborative outcomes, not features
   - Use existing power users as advocates

---

### Key Learnings

**What worked**:
- Triangulation validated findings across methods (high confidence)
- Qual segmentation (non/light/power users) explained quant funnel
- Joint display made patterns visually obvious

**What didn't**:
- Wish we'd included behavioral analytics (actual usage patterns, not just survey)
- Qual sample didn't include churned power users (survivorship bias)

**Outcome**: Product team implemented team-based onboarding, adoption increased from 12% to 28% over 6 months

---

## Example 3: Culture Assessment (Exploratory Sequential)

### Context

**Business decision**: What defines our organizational culture? How do we measure it?

**Stakeholders**: CEO, Leadership team

**Timeline**: 7 weeks

**Design chosen**: Exploratory Sequential (QUAL → quan)
- Priority: Qualitative (understand culture dimensions)
- Purpose: Development (create culture measurement instrument)

---

### Phase 1: Qualitative Exploration (Week 1-4)

**Methods**:
- **Ethnography**: 2 weeks observing 4 teams (meetings, Slack, interactions)
- **Interviews**: 25 participants (all levels, all departments)
- **Document analysis**: Internal memos, all-hands transcripts, Slack archives

**Research question**: "What cultural values and norms are enacted daily?"

**Thematic analysis** (Week 4):

**Theme 1: Speed Over Perfection** (20/25 participants)
- "We ship fast, iterate later"
- "Bias toward action - don't wait for perfect"
- Observed: Decisions made in hours, not weeks
- Slack norm: "⚡" emoji = fast execution

**Theme 2: Transparent Debate** (18/25 participants)
- "Disagree openly, commit publicly"
- "Healthy conflict expected, even with leadership"
- Observed: All-hands where IC challenged CEO's decision
- Slack norm: Decisions documented with rationale

**Theme 3: Ownership Mindset** (22/25 participants)
- "Own outcomes, not just tasks"
- "We don't have product managers - engineers own product"
- Observed: Engineers making UX and business decisions
- Doc analysis: "Driver" role rotates across team

**Theme 4: Learning Mode** (17/25 participants)
- "Comfortable with 'I don't know'"
- "Sharing mistakes is celebrated"
- Observed: Weekly "failure Friday" presentations
- Slack norm: "TIL" (today I learned) channel very active

**Theme 5: Customer Proximity** (19/25 participants)
- "Talk to customers weekly, everyone"
- "Data + stories, not just data"
- Observed: Customer calls open to all employees
- Norm: New hires shadow customer calls in first week

---

### Connection Point (Week 4-5)

**Goal**: Transform qual themes → quant scales

**Process**:
1. Extract key dimensions from themes (5 dimensions)
2. Generate scale items for each dimension (5-7 items per dimension)
3. Review items with qual participants (member checking)
4. Pilot with 20 employees, refine wording

**Scale development**:

**Dimension 1: Speed Orientation** (5 items)
- "We prioritize speed over perfection" (1=strongly disagree, 5=strongly agree)
- "Decisions are made quickly"
- "We iterate rapidly based on feedback"
- "Waiting for perfect information is discouraged"
- "Bias toward action is valued"

**[Similar process for other 4 dimensions]**

**Result**: 28-item culture scale (5 dimensions × 5-6 items)

---

### Phase 2: Quantitative Testing (Week 5-6)

**Survey**: All employees (n=285, 78% response rate)

**Scale validation** (Week 6 analysis):

**Factor analysis**:
- 5-factor solution emerges (matches qual themes)
- Clean factor loadings (.60-.85)
- Dimensions are distinguishable (inter-correlations .25-.45)

**Reliability**:
- Speed Orientation: α = .84 (good)
- Transparent Debate: α = .81 (good)
- Ownership Mindset: α = .88 (excellent)
- Learning Mode: α = .79 (acceptable)
- Customer Proximity: α = .86 (good)

**Descriptive results**:
- Speed Orientation: M = 4.2/5.0 (high)
- Transparent Debate: M = 4.0/5.0 (high)
- Ownership Mindset: M = 4.3/5.0 (high)
- Learning Mode: M = 3.9/5.0 (moderate-high)
- Customer Proximity: M = 4.1/5.0 (high)

**Demographic differences**:
- Tenure: New hires rate all dimensions slightly lower (3.7-3.9 vs 4.0-4.3)
- Department: Engineering highest on Ownership (4.5), Sales highest on Customer Proximity (4.4)

---

### Phase 3: Integration (Week 7)

**Integration summary**:

**Development process validated**:
- Qual identified 5 culture dimensions grounded in actual behavior
- Quant confirmed 5 dimensions are measurable and distinct
- Factor analysis matched qual themes exactly (construct validity)

**Convergence** (qual themes → quant scales):
| Qual Theme | Quant Dimension | Qual Evidence | Quant Result | Integration |
|------------|-----------------|---------------|--------------|-------------|
| Speed Over Perfection | Speed Orientation | 20/25 described | M = 4.2, α = .84 | **Culture strength confirmed**, quantifiable |
| Transparent Debate | Transparent Debate | 18/25 described | M = 4.0, α = .81 | **Norms are shared**, measurable |
| Ownership Mindset | Ownership Mindset | 22/25 described | M = 4.3, α = .88 | **Strongest dimension** (highest M, highest α) |
| Learning Mode | Learning Mode | 17/25 described | M = 3.9, α = .79 | **Moderate strength**, room to strengthen |
| Customer Proximity | Customer Proximity | 19/25 described | M = 4.1, α = .86 | **High across company**, differentiates from competitors |

**Meta-inferences**:

1. **Culture is strong and shared**: All 5 dimensions have high means (3.9-4.3) and good reliability, indicating consensus

2. **Ownership is defining characteristic**: Highest mean (4.3) and reliability (.88) - this is what makes culture distinctive

3. **Learning Mode is opportunity area**: Lowest mean (3.9) and reliability (.79) - theme was present in qual but less consistently enacted

4. **Culture varies by tenure**: New hires rate lower across all dimensions, suggesting socialization takes time or onboarding gaps

---

### Deliverables (Week 7)

**Three deliverables**:

**1. Culture Profile Report** (for leadership)
- 5 dimensions identified and validated
- Current state scores (all high)
- Comparison: Tenure, department
- Recommendations for strengthening

**2. Culture Measurement Instrument** (for ongoing use)
- 28-item validated scale
- Can be used quarterly to track culture change
- Benchmark established (current results)

**3. Onboarding Implications** (for People team)
- New hires rate culture lower (not yet enculturated)
- Recommendation: Strengthen onboarding focus on Ownership Mindset (defining trait)
- Recommendation: Explicit Learning Mode rituals (lowest dimension, needs reinforcement)

---

### Key Learnings

**What worked**:
- Qual exploration was critical - couldn't have identified 5 dimensions from survey alone
- Grounded instrument in participant language (high face validity)
- Factor analysis validated qual themes exactly (rare and powerful)

**What didn't**:
- Wished we'd done qual with customers too (would External perception match internal?)
- Survey was long (28 items) - could trim to 15-20 items in future iterations

**Outcome**:
- Instrument now used quarterly to track culture evolution
- New hire onboarding revised to emphasize Ownership Mindset earlier
- "Learning Mode" initiatives launched (doubled "failure Friday" frequency, added mentorship program)
- 6 months later, Learning Mode score increased from 3.9 to 4.2

---

## Common Patterns Across Examples

### Pattern 1: Integration Produces Meta-Inferences

All examples show that combining methods reveals insights neither alone could:

- **Example 1**: "Mid-Level Trap" (quant showed where, qual explained why, integration named phenomenon)
- **Example 2**: "Network effects trap" (quant showed adoption drop, qual revealed multi-player nature, integration diagnosed structural issue)
- **Example 3**: "Ownership as defining trait" (qual identified theme, quant measured strength, integration prioritized for onboarding)

**Lesson**: Don't just report qual + quant separately. The meta-inference from integration is the payoff.

---

### Pattern 2: Design Matches Purpose

All examples chose design deliberately based on purpose:

- **Example 1**: Explanatory Sequential - quant found pattern, needed qual to explain → QUAN → qual
- **Example 2**: Convergent - wanted comprehensive view, triangulation → QUAL + QUAN
- **Example 3**: Exploratory Sequential - needed to develop instrument → QUAL → quan

**Lesson**: Design selection matters. Mismatch between design and purpose weakens study.

---

### Pattern 3: Connection Points Are Explicit

All examples documented how methods connected:

- **Example 1**: Quant results → participant selection + interview protocol design
- **Example 2**: Simultaneous but structured comparison via joint display
- **Example 3**: Qual themes → scale items with member checking

**Lesson**: Integration doesn't happen automatically. Plan and document connection points.

---

### Pattern 4: Contradictions Weren't Found (But Could Be)

None of these examples had major contradictions, but real projects often do.

**If Example 2 had contradiction**:
- Quant: 52% say "unclear value"
- Qual: All 18 participants clearly articulated value
- **Investigation**: Sample difference (qual recruited from trial users, survey included non-users who never saw feature)
- **Resolution**: Value is clear to those who try it, but marketing doesn't communicate value to drive trial

**Lesson**: Plan for contradictions (see [[resolving-contradictions]]), don't ignore them.

---

## Anti-Patterns to Avoid

### Anti-Pattern 1: Mixing Without Integration

**Problem**: Qual and quant collected but reported separately, no attempt to combine

**Better**: Always create joint display or integration narrative. Meta-inferences are the point.

---

### Anti-Pattern 2: Unequal Effort, Equal Claims

**Problem**: Large quant survey (n=1,200) + 3 interviews, claim "mixed methods"

**Better**: Balance effort. If one method is supplemental, acknowledge priority explicitly.

---

### Anti-Pattern 3: Sequential Without Connection

**Problem**: Do qual, then quant, but quant doesn't build on qual findings

**Better**: Document connection. How did Phase 1 inform Phase 2 design?

---

### Anti-Pattern 4: Ignoring Divergence

**Problem**: Qual and quant disagree, report only converging findings

**Better**: Investigate divergence (see [[resolving-contradictions]]). Contradictions reveal complexity.

---

## Template for Your Project

```markdown
# Mixed Methods Project: [Your Topic]

## Context
- Decision: [What decision]
- Stakeholders: [Who cares]
- Timeline: [How long]
- Design: [Convergent, Explanatory Sequential, or Exploratory Sequential]
- Rationale: [Why this design]

## Phase 1: [Quant/Qual] Data Collection
**Method**: [Survey, experiment, interviews, ethnography]
**Sample**: [n=X, how recruited]
**Key findings**: [Top 3-5 results]

## [Connection Point or Parallel Collection]
[If sequential: How did Phase 1 inform Phase 2?]
[If convergent: How were methods coordinated?]

## Phase 2: [Qual/Quant] Data Collection (if sequential)
**Method**: [Method]
**Sample**: [n=X]
**Key findings**: [Top 3-5 results]

## Integration
**Joint display**: [Table comparing qual and quant]
**Meta-inferences**: [What emerges from combining?]
**Contradictions**: [Any divergence? How resolved?]

## Deliverables
1. [Deliverable 1]
2. [Deliverable 2]

## Outcome
[What happened after the research]
```

---

## Related Documentation

- [[workflow]] - Complete mixed methods workflow
- [[design-selection-guide]] - Choosing the right design
- [[resolving-contradictions]] - Handling divergent findings
- [[../../context/research/mixed-methods-research-standards]] - Creswell & Plano Clark framework
