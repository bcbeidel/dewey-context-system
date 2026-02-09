# PRISMA 2020 Compliance Guide

**Purpose**: Ensure systematic reviews meet PRISMA 2020 reporting standards for transparency, reproducibility, and publication readiness.

**PRISMA**: Preferred Reporting Items for Systematic reviews and Meta-Analyses

**Version**: PRISMA 2020 (replaces PRISMA 2009)

---

## PRISMA 2020 Overview

PRISMA 2020 provides a **27-item checklist** for transparent reporting of systematic reviews. The statement includes:
- **Main checklist**: 27 items for full systematic review
- **Abstract checklist**: 12 items for review abstracts
- **Flow diagram**: Visual representation of study selection process

**Applicability**: Designed for health intervention reviews but applicable to social, educational, and other interventions.

**Key Improvements from 2009**:
- Updated search reporting requirements
- Enhanced risk of bias assessment guidance
- Improved synthesis reporting
- New items for certainty of evidence
- Revised flow diagrams

---

## PRISMA 2020: 27-Item Checklist

Use this checklist when writing your systematic review to ensure all required elements are included.

### Title (Item 1)
- [ ] **#1**: Identify the report as a systematic review

**Example**: "Effectiveness of Spaced Repetition for Long-term Knowledge Retention: A Systematic Review"

---

### Abstract (Items 2-8)

- [ ] **#2**: Provide structured abstract (Objectives, Methods, Results, Conclusions)
- [ ] **#3**: Specify review question or objective
- [ ] **#4**: Specify study characteristics (PICO: Population, Intervention, Comparator, Outcome)
- [ ] **#5**: Describe databases and date ranges searched
- [ ] **#6**: Specify methods for risk of bias assessment
- [ ] **#7**: Present results with summary statistics
- [ ] **#8**: Interpret results and implications

**See**: [[#Abstract Checklist]] below for detailed guidance

---

### Introduction (Items 9-10)

- [ ] **#9 - Rationale**: Describe rationale for review in context of existing knowledge
- [ ] **#10 - Objectives**: Provide explicit statement of objectives or questions (use PICO when applicable)

**Example Objective**: "To evaluate the effectiveness of spaced repetition compared to massed practice for long-term knowledge retention in adult learners."

---

### Methods (Items 11-17)

#### Eligibility & Search
- [ ] **#11 - Eligibility criteria**: Specify inclusion/exclusion criteria (PICO framework)
- [ ] **#12 - Information sources**: Specify all databases, registers, websites, dates searched
- [ ] **#13 - Search strategy**: Present full search strategy for at least one database (include all keywords, Boolean operators)

#### Study Selection & Data Collection
- [ ] **#14 - Selection process**: State process for selecting studies (screening, eligibility, inclusion). Note number of reviewers.
- [ ] **#15 - Data collection process**: State process for extracting data. Note number of reviewers, pilot testing.
- [ ] **#16a - Data items (outcomes)**: List and define all outcomes assessed
- [ ] **#16b - Data items (other)**: List and define all other variables collected (e.g., population characteristics, funding sources)

#### Assessment of Risk & Certainty
- [ ] **#17 - Study risk of bias**: Describe methods for assessing risk of bias (tool used, outcomes assessed, number of reviewers)

---

### Results (Items 18-24)

#### Study Selection & Characteristics
- [ ] **#18 - Study selection**: Describe results of search and selection process with flow diagram
- [ ] **#19 - Study characteristics**: Cite each included study and present characteristics (e.g., sample size, PICO elements, follow-up)
- [ ] **#20 - Risk of bias in studies**: Present risk of bias assessments for each study

#### Synthesis
- [ ] **#21 - Results of individual studies**: Present all outcomes for each study (summary statistics, effect estimates, confidence intervals)
- [ ] **#22a - Results of syntheses**: Present results of syntheses (meta-analyses or other)
- [ ] **#22b - Heterogeneity**: Present assessment of heterogeneity (statistical measures)
- [ ] **#23 - Reporting biases**: Present results of assessment for publication bias or selective reporting
- [ ] **#24 - Certainty of evidence**: Present certainty of evidence assessments (e.g., GRADE)

---

### Discussion (Items 25-26)

- [ ] **#25a - Discussion (interpretation)**: Provide interpretation of results in context of other evidence
- [ ] **#25b - Discussion (limitations)**: Discuss limitations at study and review level
- [ ] **#25c - Discussion (implications)**: Discuss implications for practice, policy, and future research
- [ ] **#26 - Funding**: Describe sources of financial/non-financial support and role of funders

---

### Other (Item 27)

- [ ] **#27a - Registration**: Provide registration information (registry name, number)
- [ ] **#27b - Protocol availability**: Indicate where protocol can be accessed
- [ ] **#27c - Conflicts of interest**: Declare conflicts of interest
- [ ] **#27d - Code/data availability**: Report availability of data, code, and materials

---

## PRISMA 2020: Abstract Checklist

Use for writing review abstracts (200-250 words):

### Structure (Items 1-2)
- [ ] **A1 - Title**: Identify as systematic review, meta-analysis, or both
- [ ] **A2 - Objectives**: Provide review question including PICO

### Methods (Items 3-6)
- [ ] **A3 - Eligibility**: Specify inclusion/exclusion criteria
- [ ] **A4 - Information sources**: Specify databases and search dates
- [ ] **A5 - Risk of bias**: Specify methods for risk of bias assessment
- [ ] **A6 - Synthesis**: Describe synthesis methods (narrative, meta-analysis)

### Results (Items 7-10)
- [ ] **A7 - Studies included**: Give number of included studies and participants
- [ ] **A8 - Summary measures**: Present summary of results for main outcomes
- [ ] **A9 - Effect estimates**: Present effect estimates with confidence intervals
- [ ] **A10 - Certainty of evidence**: Present certainty of evidence assessment

### Discussion (Items 11-12)
- [ ] **A11 - Interpretation**: Provide general interpretation of results
- [ ] **A12 - Funding**: Specify primary funding source
- [ ] **A13 - Registration**: Provide registration number

**Example Abstract Structure**:
```markdown
## Abstract

**Objectives**: [PICO question]

**Methods**: Systematic review following PRISMA 2020. Searched PubMed, Web of Science, PsycINFO (inception-December 2025). Included [criteria]. Risk of bias assessed using [tool]. Meta-analysis conducted using [method].

**Results**: Included N studies (N participants). [Main outcome]: [effect estimate] (95% CI: X-Y). Certainty of evidence: [GRADE rating].

**Conclusions**: [Interpretation]. [Implications]. Registration: PROSPERO [number].

**Funding**: [Source]
```

---

## PRISMA Flow Diagram

The PRISMA flow diagram visualizes the study selection process. Generate using this template:

```markdown
## PRISMA Flow Diagram

### Identification
- **Records identified from databases** (n = ___):
  - PubMed (n = ___)
  - Web of Science (n = ___)
  - PsycINFO (n = ___)
- **Records identified from other sources** (n = ___):
  - Citation searching (n = ___)
  - Hand searching (n = ___)
- **Records removed before screening**:
  - Duplicate records removed (n = ___)
  - Records marked as ineligible (n = ___)
- **Records screened** (n = ___)

### Screening
- **Records excluded** (n = ___)
  - Reason 1 (n = ___)
  - Reason 2 (n = ___)
  - Reason 3 (n = ___)

### Eligibility
- **Reports sought for retrieval** (n = ___)
- **Reports not retrieved** (n = ___)
- **Reports assessed for eligibility** (n = ___)
- **Reports excluded** (n = ___):
  - Exclusion reason 1 (n = ___)
  - Exclusion reason 2 (n = ___)
  - Exclusion reason 3 (n = ___)

### Included
- **Studies included in review** (n = ___)
- **Reports of included studies** (n = ___)
```

**Visual Representation**: Can be converted to Mermaid diagram using `/diagram` skill.

---

## Implementing PRISMA in Your Review

### During Protocol Phase (Before Starting)
1. Complete PRISMA-P checklist → [[protocol-phase]]
2. Register protocol on PROSPERO
3. Document search strategy with full Boolean operators
4. Specify risk of bias assessment tool (Cochrane RoB 2, ROBIS)

### During Review Execution
1. Track numbers for flow diagram at each stage
2. Use standardized data extraction form (aligned with Item #15)
3. Have 2+ reviewers for screening and extraction
4. Document all decisions and disagreements

### During Write-Up
1. Use PRISMA 2020 checklist as outline
2. Complete abstract checklist
3. Generate flow diagram
4. Include full search strategy in appendix
5. Report all 27 items

### Before Submission
1. Run through full 27-item checklist
2. Verify abstract meets 13-item checklist
3. Ensure flow diagram included
4. Check registration and protocol availability stated
5. Consider PRISMA compliance statement: "This review was conducted and reported according to PRISMA 2020 guidelines."

---

## PRISMA Extensions

For specialized reviews, use these extensions:

- **PRISMA-NMA**: Network meta-analyses
- **PRISMA-IPD**: Individual participant data
- **PRISMA-Harms**: Reviews of adverse effects
- **PRISMA-DTA**: Diagnostic test accuracy
- **PRISMA-ScR**: Scoping reviews

**See**: [PRISMA Extensions](https://www.prisma-statement.org/extensions)

---

## Common PRISMA Compliance Issues

### Issues to Avoid:

❌ **Incomplete search strategy**: Must report full Boolean query, not just keywords

❌ **Missing flow diagram**: Required for transparency

❌ **Unclear selection process**: Must state number of reviewers, disagreement resolution

❌ **No risk of bias assessment**: Required for all included studies

❌ **Missing registration**: PROSPERO registration strongly recommended

❌ **Abstract doesn't follow structure**: Use 13-item abstract checklist

### Quality Indicators:

✅ **Pre-registered protocol** (PROSPERO)

✅ **2+ independent reviewers** for screening and extraction

✅ **Full search strategy** in appendix

✅ **Risk of bias** assessed for all studies

✅ **Certainty of evidence** rated (GRADE)

✅ **PRISMA compliance statement** in methods

---

## Tools & Resources

### PRISMA Resources
- **Official website**: [prisma-statement.org](https://www.prisma-statement.org/)
- **Checklist PDF**: [PRISMA 2020 Checklist](https://www.prisma-statement.org/prisma-2020-checklist)
- **Flow diagram template**: [PRISMA Flow Diagram](https://www.prisma-statement.org/prisma-2020-flow-diagram)
- **Explanation & Elaboration**: [Full guidance with examples](https://pmc.ncbi.nlm.nih.gov/articles/PMC8005925/)

### Software Tools
- **Covidence**: Screening and data extraction platform with PRISMA export
- **RevMan**: Cochrane's review management software
- **PRISMA Flow Diagram Generator**: [Online tool](http://prisma.thetacollaborative.ca/)

---

## Next Steps

After ensuring PRISMA compliance:
1. **Quality assessment** → [[quality-assessment]] (AMSTAR-2, ROBIS)
2. **Protocol phase** → [[protocol-phase]] (PRISMA-P, PROSPERO)
3. **Full review** → [[workflow]] (Complete systematic review workflow)

---

## References

**Primary Sources**:
- Page, M. J., et al. (2021). The PRISMA 2020 statement: An updated guideline for reporting systematic reviews. *BMJ*, 372:n71. [PMC8007028](https://pmc.ncbi.nlm.nih.gov/articles/PMC8007028/)
- Page, M. J., et al. (2021). PRISMA 2020 explanation and elaboration. *BMJ*, 372:n160. [PMC8005925](https://pmc.ncbi.nlm.nih.gov/articles/PMC8005925/)

**Official Resources**:
- [PRISMA Statement Official Website](https://www.prisma-statement.org/)
- [EQUATOR Network: PRISMA](https://www.equator-network.org/reporting-guidelines/prisma/)

---

**Related**: [[protocol-phase]] | [[quality-assessment]] | [[workflow|Back to Overview]]
