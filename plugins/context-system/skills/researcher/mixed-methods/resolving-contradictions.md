# Resolving Contradictions in Mixed Methods Research

**Purpose**: Framework for handling disagreements between qualitative and quantitative findings.

**Created**: 2026-02-08

---

## Overview

**Contradictions are normal** in mixed methods research and often reveal valuable insights.

**Don't force agreement** - investigate why methods disagree.

**Core principle**: Divergence between qual and quant is data, not a problem. It reveals complexity that single-method research misses.

---

## Types of Contradictions

### Type 1: Direct Contradiction

**What it looks like**:
- Quant: 75% satisfaction (high)
- Qual: Most interview participants expressed dissatisfaction
- **Result**: Methods disagree on the same construct

**Common causes**:
- Different samples (quant = general population, qual = vocal minority)
- Social desirability bias (public vs private opinions)
- Measurement mismatch (survey item doesn't capture qual nuance)

---

### Type 2: Partial Contradiction

**What it looks like**:
- Quant: Moderate correlation (r = .35)
- Qual: Some themes support, some contradict
- **Result**: Mixed evidence, pattern not clear-cut

**Common causes**:
- Moderating variables (relationship varies by subgroup)
- Contextual factors (different conditions)
- Temporal dynamics (relationship changes over time)

---

### Type 3: Unexpected Absence

**What it looks like**:
- Quant: No significant difference found
- Qual: Participants emphasized major difference
- **Result**: Qual sees pattern quant misses

**Common causes**:
- Insufficient statistical power
- Measurement insensitivity (quant tool too crude)
- Non-linear relationships (qual captures, quant assumes linear)

---

### Type 4: Unexpected Presence

**What it looks like**:
- Quant: Strong significant effect
- Qual: Participants don't mention it
- **Result**: Quant sees pattern qual misses

**Common causes**:
- Below awareness (people don't notice pattern)
- Outside interview scope (questions didn't probe)
- Statistical artifact (multiple testing, outliers)

---

## Five-Step Resolution Framework

### Step 1: Verify the Contradiction

**Don't assume contradiction exists** - check carefully.

**Questions to ask**:

**Are methods measuring the same thing?**
- Survey item: "Overall, how satisfied are you?" (global judgment)
- Interview: "Tell me about your experiences" (specific incidents)
- **Not really a contradiction** - different constructs

**Are samples comparable?**
- Survey: All employees (n=500)
- Interviews: Recent hires only (n=15)
- **Not really a contradiction** - different populations

**Is timing the same?**
- Survey: Collected in January (before layoffs)
- Interviews: Collected in March (after layoffs)
- **Not really a contradiction** - context changed

**Is the contradiction statistically meaningful?**
- Quant: 52% agree (barely above midpoint)
- Qual: Mixed reactions (some agree, some don't)
- **Not really a contradiction** - both show ambivalence

**If contradictions are artifacts of design, document and move on. Real contradictions warrant investigation.**

---

### Step 2: Examine Methodological Explanations

**Four methodological sources of contradiction**:

**A. Sampling Differences**

**Symptom**: Different conclusions from different samples

**Investigation**:
- Compare demographics (age, gender, tenure, role)
- Check sampling method (random vs convenience vs purposive)
- Examine response rates (who didn't respond to survey?)
- Consider selection bias (who volunteered for interviews?)

**Example**:
- Quant (random sample, 65% response): Moderate support for policy
- Qual (volunteers): Strong opposition to policy
- **Explanation**: Opponents more motivated to participate in interviews

**Resolution**: Report findings as "general moderate support (survey) with vocal opposition among concerned stakeholders (interviews)"

---

**B. Measurement Differences**

**Symptom**: Instruments capture different aspects or sensitivities

**Investigation**:
- Compare operationalizations (what exactly was measured?)
- Check response formats (Likert scale vs open-ended)
- Consider social desirability (survey anonymous, interview face-to-face?)
- Examine item wording (leading questions, ambiguous terms)

**Example**:
- Quant: "Rate your manager" (1-5 scale) → 4.2 average (positive)
- Qual: "Describe your relationship with manager" → Many critical comments
- **Explanation**: Scale question triggers positive bias, open-ended reveals nuance

**Resolution**: Report findings as "ratings generally positive, but interviews reveal specific concerns about [X, Y, Z]"

---

**C. Temporal Differences**

**Symptom**: Findings differ because context changed

**Investigation**:
- Check data collection dates
- Identify events between collections (policy changes, layoffs, incidents)
- Consider seasonality or cycles
- Interview participants about changes

**Example**:
- Quant (pre-acquisition): High trust in leadership
- Qual (post-acquisition): Distrust and anxiety
- **Explanation**: Acquisition changed context

**Resolution**: Report findings as "trust high before acquisition but declined after due to uncertainty about future"

---

**D. Analytical Differences**

**Symptom**: Analysis choices led to different conclusions

**Investigation**:
- Re-examine statistical assumptions (outliers, transformations, tests)
- Review qualitative coding (alternative interpretations possible?)
- Check aggregation levels (individual vs team vs organization)
- Consider analyst bias or preconceptions

**Example**:
- Quant: No correlation between X and Y (r = .08, p = .23)
- Qual: Participants clearly describe X → Y relationship
- **Re-analysis**: Non-linear relationship (U-shaped), linear correlation missed it

**Resolution**: Rerun quant with non-linear tests, update interpretation

---

### Step 3: Examine Substantive Explanations

**If methods are sound, contradiction reveals true complexity.**

**Four substantive sources**:

**A. Moderating Variables (Subgroup Differences)**

**Symptom**: Relationship holds for some groups, not others

**Investigation**:
- Stratify quant by demographics or context
- Review qual for subgroup patterns
- Test interactions in quant (if sample allows)

**Example**:
- Quant (overall): Training has no effect on performance
- Qual: Experienced workers say "training is useless", new workers say "training is essential"
- **Explanation**: Effect moderated by experience

**Resolution**:
```markdown
Training effectiveness depends on experience level:
- Experienced workers (quant: β = -.05, ns; qual: "redundant with what we know")
- New workers (quant: β = .42, p < .01; qual: "critical for getting started")

Meta-inference: Training should be differentiated by experience level.
```

---

**B. Public vs Private Attitudes**

**Symptom**: What people say publicly (survey) differs from private views (interview)

**Investigation**:
- Consider social desirability
- Check anonymity of methods (survey anonymous? interview identified?)
- Look for power dynamics (interviewing subordinates about leadership?)
- Review qual for hedging, contradictions, or off-the-record comments

**Example**:
- Quant (anonymous survey): 45% support controversial policy
- Qual (identified interviews): 80% express support
- **Explanation**: Fear of professional repercussions in interviews, honesty in anonymous survey

**Resolution**: "Public support higher than private support, suggesting social desirability or professional pressure"

---

**C. Stated vs Revealed Preferences**

**Symptom**: What people say (qual) differs from what they do (quant behavioral data)

**Investigation**:
- Compare self-report to behavioral data
- Look for aspiration vs reality gaps
- Consider awareness (do people know their behavior?)

**Example**:
- Quant (usage analytics): Feature used by 12% of users
- Qual (interviews): 70% say "I use this feature regularly"
- **Explanation**: Over-reporting due to social desirability or misremembering

**Resolution**: "Users perceive feature as important (qual) but actual usage is low (quant), suggesting usability barriers or misalignment between intent and behavior"

---

**D. Level of Analysis Differences**

**Symptom**: Individual level (qual) differs from aggregate level (quant)

**Investigation**:
- Check if aggregation obscures patterns
- Look for ecological fallacy (aggregate → individual) or atomistic fallacy (individual → aggregate)
- Consider emergence (team dynamics ≠ sum of individuals)

**Example**:
- Quant (team level): High-performing teams have high cohesion (r = .65)
- Qual (individual level): Several individuals on high-performing teams feel isolated
- **Explanation**: Team-level cohesion coexists with individual-level isolation

**Resolution**: "Teams can be cohesive at aggregate while some members feel isolated, revealing within-team variance that aggregate measures mask"

---

### Step 4: Synthesize Integrated Understanding

**Goal**: Generate meta-inference that explains contradiction

**Four synthesis strategies**:

**Strategy A: Complementarity** (Both are right, different aspects)

**Example**:
- Quant: High overall satisfaction (72%)
- Qual: Specific frustrations with Process X
- **Synthesis**: "Employees are generally satisfied but frustrated with Process X specifically"

**Meta-inference**: Overall positivity coexists with specific pain points

---

**Strategy B: Conditionality** (Both are right, different contexts)

**Example**:
- Quant: No effect of mentoring on retention
- Qual: Mentoring highly valued by some, irrelevant to others
- **Synthesis**: "Mentoring effectiveness depends on career stage and relationship quality"

**Meta-inference**: Universal claim doesn't hold; need conditional understanding

---

**Strategy C: Complexity** (Relationship is more complex than linear)

**Example**:
- Quant: Linear model shows autonomy → satisfaction (β = .15, weak)
- Qual: Too little autonomy = frustration, too much = overwhelm, moderate = ideal
- **Synthesis**: "Autonomy has curvilinear relationship (inverted U) with satisfaction"

**Meta-inference**: Qualitative depth reveals non-linear pattern quantitative linear model misses

---

**Strategy D: Evolution** (Findings differ because phenomenon is changing)

**Example**:
- Quant (longitudinal): Declining engagement over time
- Qual (recent interviews): Participants describe high engagement
- **Synthesis**: "Engagement declined historically but recent initiatives have reversed trend"

**Meta-inference**: Temporal dynamics require considering when data collected

---

### Step 5: Report Contradiction Transparently

**Don't hide contradictions** - they're part of findings.

**Reporting template**:

```markdown
## Contradictory Findings: [Topic]

### Quantitative Finding
[Describe quant result with statistics]

### Qualitative Finding
[Describe qual result with quotes]

### Investigation
We investigated this contradiction by [methods]:
- [Investigation step 1 finding]
- [Investigation step 2 finding]

### Resolution
The contradiction appears to stem from [methodological/substantive explanation].

### Integrated Interpretation
[Meta-inference that explains both findings]

**Example**: "While the survey showed overall high satisfaction (72%), interviews revealed specific frustration with Process X. This is not a contradiction but rather reflects that employees can be generally satisfied while experiencing specific pain points. The quantitative measure captures aggregate sentiment while qualitative depth identifies localized issues."

### Implications
[What does this teach us?]
```

---

## Common Contradiction Patterns

### Pattern 1: The Vocal Minority

**Symptoms**:
- Quant: Minority view (20-30%)
- Qual: Dominant in interviews (70-80% of participants)

**Explanation**: Minorities often more motivated to participate in interviews

**Resolution**: Report as "vocal minority" with both prevalence (quant) and depth (qual)

---

### Pattern 2: The Satisfied Silent Majority

**Symptoms**:
- Quant: Majority satisfied (70%+)
- Qual: Few positive comments, many complaints

**Explanation**: Satisfied people have less to say, complaints are more detailed

**Resolution**: Report as "widespread satisfaction with specific areas for improvement"

---

### Pattern 3: The Unaware Pattern

**Symptoms**:
- Quant: Strong statistical relationship
- Qual: Participants don't mention it

**Explanation**: People unaware of factors influencing them (implicit biases, unconscious patterns)

**Resolution**: Report as "behavioral data reveals pattern not explicitly recognized by participants"

---

### Pattern 4: The Measurement Mismatch

**Symptoms**:
- Quant: Global measure (e.g., "overall satisfaction")
- Qual: Specific experiences (e.g., "manager didn't respond to my email")

**Explanation**: Different levels of abstraction

**Resolution**: Don't compare directly; instead report "global satisfaction is X, driven by specific factors including Y (qual)"

---

## When Contradictions Can't Be Resolved

**Sometimes contradictions remain unresolved** - that's OK!

**Report as**:
```markdown
## Unresolved Contradiction: [Topic]

Quantitative and qualitative findings diverge on [topic], and investigation has not identified a clear explanation.

**Possible explanations**:
1. [Hypothesis 1]
2. [Hypothesis 2]

**Recommendation**: Future research should [specific follow-up studies]

**Pragmatic guidance**: Given the uncertainty, we recommend [cautious action based on both findings]
```

**Example**:
"Survey data suggests Policy X is popular (68% support), but interviews reveal widespread concerns. We cannot definitively explain this divergence. Possible explanations include social desirability bias in interviews or measurement issues in the survey. We recommend pilot implementation with close monitoring rather than full rollout."

---

## Contradiction Resolution Checklist

When you encounter contradiction, work through this checklist:

- [ ] **Verify**: Are methods actually measuring the same construct?
- [ ] **Sample**: Do sample differences explain divergence?
- [ ] **Measurement**: Do instruments capture construct differently?
- [ ] **Timing**: Did context change between data collections?
- [ ] **Analysis**: Are analytical choices sound?
- [ ] **Subgroups**: Does relationship vary by group?
- [ ] **Public/Private**: Are responses influenced by social desirability?
- [ ] **Stated/Revealed**: Do attitudes differ from behavior?
- [ ] **Level**: Are findings at different levels of analysis?
- [ ] **Synthesis**: What meta-inference explains both findings?
- [ ] **Report**: Have contradictions been transparently documented?

---

## Examples of Well-Resolved Contradictions

### Example 1: Training Effectiveness Study

**Contradiction**:
- Quant: Training has no effect on performance (r = .08, p = .31)
- Qual: 14/15 participants said "training was valuable"

**Investigation**: Examined subgroups

**Resolution**: Effect moderated by role complexity
- Simple roles: β = -.12 (training didn't help, already knew content)
- Complex roles: β = .51 (training critical for performance)
- Overall: β = .08 (effects cancel out)

**Meta-inference**: One-size-fits-all training is ineffective; need role-differentiated approach

---

### Example 2: Remote Work Satisfaction

**Contradiction**:
- Quant: Remote work satisfaction declined from 85% (2020) to 62% (2022)
- Qual: Participants describe remote work as "great" and "liberating"

**Investigation**: Examined timing and sample

**Resolution**: Temporal dynamics + sample differences
- Survey: Repeated cross-sectional (different people each wave)
- Interviews: Current remote workers (survivors, who chose to stay remote)
- Explanation: Dissatisfied workers returned to office, satisfied workers remained remote

**Meta-inference**: Decline reflects sorting, not dissatisfaction among those who remain remote

---

### Example 3: Feature Adoption

**Contradiction**:
- Quant: 12% feature adoption rate (usage analytics)
- Qual: 75% of interviewees said "I use this regularly"

**Investigation**: Defined "use" operationally

**Resolution**: Measurement mismatch + stated vs revealed
- Quant definition: Used in past 30 days
- Qual definition: Used ever or "would use if needed"
- Explanation: Over-reporting + different time frames

**Meta-inference**: Users perceive feature as valuable (qual) but actual regular usage is low (quant), suggesting occasional use or misalignment between perceived and actual utility

---

## Related Documentation

- [[workflow]] - Complete mixed methods workflow (Phase 4: Integration)
- [[design-selection-guide]] - Choosing design to minimize contradictions
- [[examples]] - Real projects with contradiction resolution
- [[../../context/research/mixed-methods-research-standards]] - Creswell & Plano Clark divergence framework

---

## Sources

Based on:
- Creswell, J. W., & Plano Clark, V. L. (2017). *Designing and Conducting Mixed Methods Research* (3rd ed.), Ch. 8
- Erzberger, C., & Kelle, U. (2003). Making inferences in mixed methods: The rules of integration
- Moran-Ellis, J., et al. (2006). Triangulation and integration: Processes, claims and implications
