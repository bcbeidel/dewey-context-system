# Quality Assessment: AMSTAR-2, ROBIS & Robustness

**Purpose**: Assess methodological quality and risk of bias in systematic reviews to ensure trustworthy, reproducible results.

**Key Tools**:
- **AMSTAR-2**: Assess quality of systematic reviews
- **ROBIS**: Risk of bias in systematic reviews
- **Robustness Checks**: Internal and external validation

---

## Why Quality Assessment Matters

### Quality vs. Risk of Bias

**Quality Assessment (AMSTAR-2)**: Evaluates methodological rigor of the review process itself

**Risk of Bias (ROBIS)**: Evaluates potential for bias in review conclusions

**Both are necessary** for trustworthy systematic reviews.

### When to Use Each Tool

| Tool | Purpose | When to Use |
|------|---------|-------------|
| **AMSTAR-2** | Assess overall quality | After completing review (self-assessment) or when appraising others' reviews |
| **ROBIS** | Assess risk of bias | When relying on existing reviews or conducting overview of reviews |
| **Robustness Checks** | Validate findings | Throughout review process (internal) and before publication (external) |

---

## AMSTAR-2: Quality Assessment Tool

**AMSTAR**: A MeaSurement Tool to Assess systematic Reviews
**Version**: AMSTAR-2 (2017 update)

**Purpose**: Critical appraisal of systematic reviews of randomized and non-randomized healthcare interventions.

### AMSTAR-2: 16-Item Checklist

**Critical Domains** (marked with *): Substantial impact on validity

#### Planning & Protocol (Items 1-2)
- [ ] **#1**: Did the research questions and inclusion criteria include PICO?
- [ ] **#2***: Did report contain statement that review methods established before conduct AND justify deviations?

**Quality Indicator**: Pre-registered protocol (PROSPERO) strongly signals Item #2 compliance.

#### Search & Selection (Items 3-7)
- [ ] **#3**: Did reviewers explain their selection of study designs?
- [ ] **#4***: Did reviewers use comprehensive literature search strategy?
  - ≥2 databases searched
  - Date ranges provided
  - Search strategy provided
  - Justification for exclusions
- [ ] **#5***: Did reviewers perform study selection in duplicate?
- [ ] **#6**: Did reviewers perform data extraction in duplicate?
- [ ] **#7***: Did reviewers provide list of excluded studies AND justify exclusions?

#### Risk of Bias & Data (Items 8-10)
- [ ] **#8**: Did reviewers describe included studies in adequate detail?
  - Population, intervention, comparator, outcomes, study design
- [ ] **#9***: Did reviewers use satisfactory technique for assessing risk of bias?
  - Used established tool (RoB 2, ROBINS-I)
  - Assessed all relevant domains
  - Justification for tool choice
- [ ] **#10**: Did reviewers report sources of funding for included studies?

#### Synthesis & Meta-Analysis (Items 11-13)
- [ ] **#11***: If meta-analysis, did reviewers use appropriate methods for combining results?
  - Statistical appropriateness
  - Assessment of heterogeneity
  - Investigation of heterogeneity sources
- [ ] **#12**: If meta-analysis, did reviewers assess potential impact of risk of bias on results?
  - Sensitivity analysis excluding high-risk studies
  - Discussion of how bias may affect results
- [ ] **#13***: Did reviewers account for risk of bias when interpreting results?

#### Publication Bias & Conflicts (Items 14-16)
- [ ] **#14**: Did reviewers provide satisfactory explanation for heterogeneity?
- [ ] **#15***: If quantitative synthesis, did reviewers investigate publication bias AND discuss impact?
  - Funnel plot (if ≥10 studies)
  - Statistical tests (Egger's test)
  - Discussion of potential impact
- [ ] **#16**: Did reviewers report potential conflicts of interest?
  - Review level (funding sources)
  - Individual study level

---

### AMSTAR-2: Rating System

**Overall Confidence Rating**:

| Rating | Criteria |
|--------|----------|
| **High** | 0-1 non-critical weakness | Review provides accurate summary |
| **Moderate** | >1 non-critical weakness | May not provide accurate summary |
| **Low** | 1 critical flaw ± non-critical | Should not be relied upon |
| **Critically Low** | >1 critical flaw ± non-critical | Should not be relied upon |

**Critical Domains** (Item 2, 4, 7, 9, 11, 13, 15): Flaws here substantially decrease validity.

**Non-Critical Domains**: Flaws here may not invalidate conclusions but reduce confidence.

### Using AMSTAR-2 for Self-Assessment

**During Review**:
1. Use AMSTAR-2 as planning checklist (ensures rigorous methods)
2. Document methods to address each item
3. Build evidence for high-quality rating

**After Review**:
1. Complete full 16-item checklist
2. Identify any weaknesses
3. Address weaknesses before publication (if possible)
4. Disclose limitations transparently

**In Publications**:
```markdown
## Quality Assurance

This systematic review was conducted following AMSTAR-2 guidelines to ensure methodological quality. Self-assessment using AMSTAR-2 yielded a rating of [High/Moderate/Low/Critically Low] confidence, with [N] critical and [N] non-critical weaknesses identified: [list and address].
```

---

## ROBIS: Risk of Bias Assessment

**ROBIS**: Risk Of Bias In Systematic reviews
**Purpose**: Evaluate risk of bias in systematic review conclusions.

### ROBIS: 4-Phase Assessment

#### Phase 1: Assess Relevance (Optional)
Determine if review is relevant to your question. Not scored.

#### Phase 2: Identify Concerns with Review Process

Assess risk of bias in 4 domains:

**Domain 1: Study Eligibility Criteria**
- [ ] Were criteria appropriate for review question?
- [ ] Were criteria unambiguous?
- [ ] Were all relevant studies likely included?

**Concerns**: High | Low | Unclear

**Domain 2: Identification and Selection of Studies**
- [ ] Did search likely include all relevant studies?
- [ ] Were restrictions appropriate (e.g., language, publication status)?
- [ ] Were efforts made to minimize error in selection?

**Concerns**: High | Low | Unclear

**Domain 3: Data Collection and Study Appraisal**
- [ ] Were efforts made to minimize error in data collection?
- [ ] Were sufficient study characteristics collected?
- [ ] Was risk of bias appropriately assessed?

**Concerns**: High | Low | Unclear

**Domain 4: Synthesis and Findings**
- [ ] Was synthesis appropriate given study designs and interventions?
- [ ] Was heterogeneity minimal or adequately investigated?
- [ ] Were findings robust (e.g., sensitivity analyses)?

**Concerns**: High | Low | Unclear

#### Phase 3: Overall Risk of Bias

Consider concerns from all 4 domains:

**Question**: "Do weaknesses in the review process introduce bias into review findings?"

**Rating**: Low | High | Unclear

**Rationale**: [Justify overall rating based on domain assessments]

---

### Using ROBIS for Self-Assessment

**During Review**:
Use ROBIS domains as quality checkpoints:
- Domain 1: Verify eligibility criteria are clear and justified
- Domain 2: Ensure comprehensive search without inappropriate restrictions
- Domain 3: Implement duplicate extraction and rigorous risk of bias assessment
- Domain 4: Use appropriate synthesis methods and investigate heterogeneity

**After Review**:
1. Complete ROBIS assessment
2. If "High" concerns identified, revise methods if possible
3. Disclose remaining limitations transparently

**Example**:
```markdown
## Risk of Bias Assessment (ROBIS)

Self-assessment using ROBIS indicated [Low/High/Unclear] overall risk of bias:

- **Domain 1 (Eligibility)**: Low concern - PICO clearly defined, inclusion/exclusion justified
- **Domain 2 (Search)**: Low concern - 5 databases searched, no language restrictions, grey literature included
- **Domain 3 (Data Collection)**: Low concern - Duplicate extraction, Cochrane RoB 2 used, disagreements resolved by third reviewer
- **Domain 4 (Synthesis)**: Moderate concern - High heterogeneity (I²=78%) but investigated through subgroup analysis

**Overall**: Low risk of bias, though heterogeneity limits strength of conclusions.
```

---

## Robustness Checks: Internal & External Validation

**Purpose**: Test whether findings are stable under different assumptions and independent scrutiny.

### Internal Validation (Within Review Team)

**Conducted by**: Review authors during execution

**Methods**:

1. **Inter-Rater Reliability**:
   - Calculate Cohen's kappa for screening (target: ≥0.8)
   - Calculate Cohen's kappa for risk of bias assessment
   - Document agreement rates

2. **Sensitivity Analyses**:
   - Exclude high risk of bias studies
   - Exclude small sample studies (N < 30)
   - Fixed-effect vs random-effects model
   - Different effect measures (OR vs RR)

3. **Subgroup Analyses**:
   - Test pre-specified subgroups
   - Look for consistent effects across subgroups
   - Investigate if heterogeneity explained

4. **Leave-One-Out Analysis**:
   - Sequentially remove each study
   - Re-run meta-analysis
   - Check if conclusions change (identifies influential studies)

5. **Publication Bias Tests**:
   - Funnel plot visual inspection
   - Egger's test (p < 0.05 suggests asymmetry)
   - Trim-and-fill adjustment
   - Compare published vs grey literature

**Reporting**:
```markdown
## Sensitivity Analyses

### Primary Analysis
Overall effect: SMD = 0.72 (95% CI: 0.58-0.86), p < 0.001

### Sensitivity Analyses
| Analysis | Effect Size | 95% CI | Conclusion |
|----------|-------------|--------|------------|
| Exclude high RoB | SMD = 0.68 | 0.52-0.84 | Effect persists |
| Studies N ≥ 50 only | SMD = 0.75 | 0.59-0.91 | Effect persists |
| Fixed-effect model | SMD = 0.70 | 0.65-0.75 | Effect persists |

**Conclusion**: Findings are robust across sensitivity analyses.
```

### External Validation (Peer Review)

**Conducted by**: Independent reviewers (friendly or formal peer review)

**Process**:

1. **Protocol Review** (Pre-Publication):
   - Independent researcher reviews protocol
   - Checks for clarity, completeness, feasibility
   - Provides feedback before data collection

2. **Methods Review** (During Execution):
   - Independent check of search strategy (e.g., librarian review)
   - Sample verification of data extraction (10-20% of studies)
   - Independent risk of bias assessment (subset of studies)

3. **Results Review** (Pre-Publication):
   - Independent verification of statistical analyses
   - Check flow diagram numbers add up correctly
   - Verify conclusions follow from data

**Validation Checklist**:
- [ ] Search strategy reviewed by information specialist
- [ ] Data extraction verified for 10-20% of studies
- [ ] Statistical analyses verified independently
- [ ] PRISMA checklist verified complete
- [ ] Conflicts of interest declared

---

## Recommended Quality Workflow

### During Planning (Protocol Phase)
1. ✅ Register on PROSPERO (addresses AMSTAR-2 Item #2)
2. ✅ Use PICO framework (addresses AMSTAR-2 Item #1)
3. ✅ Plan duplicate screening/extraction (addresses AMSTAR-2 Items #5, #6)
4. ✅ Pre-specify subgroup analyses (addresses ROBIS Domain 4)

### During Execution
1. ✅ Calculate inter-rater reliability after initial screening
2. ✅ Use established risk of bias tool (addresses AMSTAR-2 Item #9)
3. ✅ Document all deviations from protocol
4. ✅ Track all exclusions with reasons (addresses AMSTAR-2 Item #7)

### During Synthesis
1. ✅ Assess heterogeneity (I² statistic)
2. ✅ Investigate heterogeneity sources (subgroup analysis)
3. ✅ Conduct sensitivity analyses
4. ✅ Assess publication bias (funnel plot, Egger's test)

### Before Publication
1. ✅ Complete AMSTAR-2 self-assessment
2. ✅ Complete ROBIS self-assessment
3. ✅ Complete PRISMA 2020 checklist
4. ✅ Conduct all planned sensitivity analyses
5. ✅ Have independent reviewer verify flow diagram
6. ✅ Disclose all limitations transparently

---

## Common Quality Issues

### Critical Issues (Must Address):

❌ **No protocol or late registration**: Suggests post-hoc modifications

❌ **Single reviewer only**: High risk of selection/extraction errors

❌ **Incomplete search**: Missing databases or no grey literature

❌ **No risk of bias assessment**: Cannot judge study quality

❌ **Unexplained heterogeneity**: Meta-analysis may be inappropriate

❌ **No publication bias assessment**: Results may be inflated

### Best Practices:

✅ **Pre-registered protocol** (PROSPERO before starting search)

✅ **Comprehensive search** (≥3 databases + grey literature)

✅ **Duplicate screening and extraction** (Cohen's kappa reported)

✅ **Established risk of bias tool** (RoB 2, ROBINS-I)

✅ **Sensitivity analyses** (test robustness of findings)

✅ **Publication bias assessed** (funnel plot + statistical tests)

✅ **GRADE certainty rating** (explicit confidence in evidence)

---

## Quality Reporting Template

Include this section in your systematic review:

```markdown
## Quality Assurance

### Methodological Quality
This systematic review followed PRISMA 2020 guidelines and was assessed using AMSTAR-2 criteria. Self-assessment yielded a [High/Moderate/Low] confidence rating.

**Strengths**:
- Pre-registered protocol (PROSPERO CRD[number])
- Comprehensive search (5 databases + grey literature)
- Duplicate screening and extraction (κ = 0.85)
- Systematic risk of bias assessment (Cochrane RoB 2)

**Limitations**:
- [List any AMSTAR-2 items not fully met]
- [E.g., "Unable to assess funding sources for all included studies"]

### Risk of Bias
ROBIS assessment indicated [Low/High/Unclear] overall risk of bias. [Justify rating based on 4 domains].

### Robustness of Findings
Sensitivity analyses confirmed findings are robust:
- Effect persists when excluding high-risk studies
- Effect persists in large studies only (N ≥ 50)
- No publication bias detected (Egger's test p = 0.24)

### Certainty of Evidence
GRADE assessment: [High/Moderate/Low/Very Low] certainty
- [Justify GRADE rating]
```

---

## Tools & Resources

### AMSTAR-2 Resources
- [AMSTAR-2 Website](https://amstar.ca/Amstar-2.php)
- [AMSTAR-2 Checklist PDF](https://amstar.ca/docs/AMSTAR-2.pdf)
- [AMSTAR-2 Guidance](https://amstar.ca/docs/AMSTAR_2_Guidance.pdf)

### ROBIS Resources
- [ROBIS Website](https://www.bristol.ac.uk/population-health-sciences/projects/robis/)
- [ROBIS Tool PDF](https://www.bristol.ac.uk/media-library/sites/social-community-medicine/images/centres/cresyda/ROBIS%20Tool.pdf)

### Statistical Tools
- **RevMan**: Cochrane's free software (meta-analysis, sensitivity analyses)
- **R metafor package**: Advanced meta-analysis
- **Comprehensive Meta-Analysis (CMA)**: Commercial software

### Quality Frameworks
- [GRADE Handbook](https://gdt.gradepro.org/app/handbook/handbook.html)
- [Cochrane Handbook (Chapter 8: Risk of Bias)](https://training.cochrane.org/handbook/current/chapter-08)

---

## Integration with Review Workflow

Quality assessment is integrated throughout:

**Phase 0 (Protocol)**: Plan for quality (AMSTAR-2 Items #1-4) → [[protocol-phase]]

**Phase 1-2 (Search & Selection)**: Duplicate processes (AMSTAR-2 Items #5-6)

**Phase 3 (Data Extraction)**: Systematic risk of bias (AMSTAR-2 Item #9)

**Phase 4 (Synthesis)**: Sensitivity & publication bias (AMSTAR-2 Items #11-15)

**Phase 5 (Write-Up)**: PRISMA compliance (transparent reporting) → [[prisma-compliance]]

---

## References

**Primary Sources**:
- Shea, B. J., et al. (2017). AMSTAR 2: a critical appraisal tool for systematic reviews. *BMJ*, 358:j4008. [Link](https://www.bmj.com/content/358/bmj.j4008)
- Whiting, P., et al. (2016). ROBIS: A new tool to assess risk of bias in systematic reviews. *BMJ*, 366:l4898. [PMC4728584](https://pmc.ncbi.nlm.nih.gov/articles/PMC4728584/)

**Best Practices**:
- Lim, W. M., et al. (2025). Systematic Literature Reviews: Reflections, Recommendations, and Robustness Check. *Journal of Consumer Behaviour*. [Wiley](https://onlinelibrary.wiley.com/doi/full/10.1002/cb.2479)

---

**Related**: [[prisma-compliance]] | [[protocol-phase]] | [[workflow|Back to Overview]]
