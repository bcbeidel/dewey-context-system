# Protocol Phase: PRISMA-P & PROSPERO

**Purpose**: Create and register systematic review protocol before starting the review to ensure transparency, prevent duplication, and establish a priori methods.

**PRISMA-P**: Preferred Reporting Items for Systematic review and Meta-Analysis Protocols

**PROSPERO**: International prospective register of systematic reviews

---

## Why Protocol Matters

### Benefits of Pre-Registration

**Transparency**: Public record of intended methods prevents post-hoc modifications

**Credibility**: Demonstrates protocol established before review began

**Prevents Duplication**: Allows others to see review is in progress

**Methodological Rigor**: Forces careful planning before execution

**Publication Requirements**: Many journals require protocol registration

### When to Create Protocol

**Timing**: Before starting literature search and data extraction

**Exception**: Quick preliminary reviews (3-5 papers) may skip formal protocol

**Best Practice**: Always create protocol for:
- Dissertation/thesis reviews
- Publication-intended reviews
- Grant-funded research
- Systematic reviews with meta-analysis

---

## PRISMA-P: 17-Item Protocol Checklist

Use this checklist when writing your review protocol:

### Administrative Information (Items 1-3)

- [ ] **#1 - Title**:
  - **1a**: Identify as protocol for systematic review
  - **1b**: If update, state this and cite previous review

**Example**: "Protocol for a Systematic Review of Spaced Repetition Effectiveness for Long-term Knowledge Retention"

- [ ] **#2 - Registration**: Provide registry name and number (PROSPERO recommended)

**Example**: "PROSPERO CRD42026123456"

- [ ] **#3 - Authors**:
  - **3a**: Contact information for lead author
  - **3b**: Contributions of each author
  - **3c**: Amendments: Describe any protocol amendments with rationale

---

### Introduction (Items 4-5)

- [ ] **#4 - Rationale**: Describe rationale in context of existing knowledge

**Example**: "Despite widespread use of spaced repetition in educational technology, no recent systematic review has synthesized evidence on its effectiveness across different populations and retention intervals."

- [ ] **#5 - Objectives**: Provide explicit statement using PICO framework

**PICO Framework**:
- **P**opulation: Who is being studied?
- **I**ntervention: What is being evaluated?
- **C**omparator: What is it compared to?
- **O**utcome: What is being measured?

**Example**: "To evaluate the effectiveness of spaced repetition (I) compared to massed practice (C) for long-term knowledge retention (O) in adult learners (P)."

---

### Methods (Items 6-14)

#### Eligibility Criteria (Item 6)
- [ ] **#6**: Specify inclusion/exclusion criteria using PICO

**Template**:
```markdown
## Eligibility Criteria

### Inclusion Criteria
**Population**: [Define target population]
**Intervention**: [Define intervention of interest]
**Comparator**: [Define comparison condition]
**Outcomes**: [Define primary and secondary outcomes]
**Study Design**: [RCT, observational, etc.]
**Language**: [English only or other languages]
**Publication Status**: [Published, preprints, grey literature]

### Exclusion Criteria
- [List specific exclusion criteria]
- [E.g., conference abstracts without full text]
- [E.g., non-human studies]
```

#### Information Sources (Item 7)
- [ ] **#7**: Describe all information sources and planned dates

**Template**:
```markdown
## Information Sources

### Bibliographic Databases
- PubMed/MEDLINE (inception to [date])
- Web of Science (inception to [date])
- PsycINFO (1806 to [date])
- Scopus (inception to [date])

### Grey Literature
- ProQuest Dissertations & Theses
- Conference proceedings: [specify which conferences]

### Other Sources
- Citation searching of included studies
- Hand-searching key journals: [list journals]
- Contacting experts in the field
```

#### Search Strategy (Item 8)
- [ ] **#8**: Present draft search strategy for at least one database

**Must Include**:
- Full Boolean query
- All keywords and synonyms
- Search filters (date, language)
- Field codes (Title, Abstract, MeSH)

**Example**:
```markdown
## Search Strategy (PubMed)

(("spaced repetition"[Title/Abstract] OR "distributed practice"[Title/Abstract] OR "spacing effect"[MeSH Terms])
AND
("knowledge retention"[Title/Abstract] OR "long-term memory"[Title/Abstract] OR "learning"[MeSH Terms])
AND
("randomized controlled trial"[Publication Type] OR "clinical trial"[Publication Type]))
AND
("2010"[Date - Publication] : "2026"[Date - Publication])
AND
(English[Language])

**Date Run**: [Will be run on date search is executed]
```

#### Study Records (Items 9-10)
- [ ] **#9 - Data management**:
  - **9a**: Describe screening process (title/abstract, then full-text)
  - **9b**: Describe data management methods (software, deduplication)

**Example**: "Records will be managed in Covidence. Duplicates removed automatically. Two reviewers will independently screen titles/abstracts, then full texts. Disagreements resolved through discussion or third reviewer."

- [ ] **#10 - Selection process**: Describe process for selecting studies

**Example**: "Selection will follow PRISMA guidelines. Two reviewers will independently assess eligibility. Cohen's kappa will be calculated for inter-rater reliability. Target kappa ≥ 0.8."

#### Data Collection (Items 11-12)
- [ ] **#11 - Data collection process**:
  - **11a**: Describe data extraction methods
  - **11b**: State how data will be obtained from investigators

**Example**: "Standardized extraction form will be piloted on 3 studies. Two reviewers will independently extract data. For missing data, authors will be contacted with maximum 2 follow-up attempts over 4 weeks."

- [ ] **#12 - Data items**: List and define all variables to be collected

**Categories**:
- Study characteristics (author, year, country, funding)
- Population characteristics (age, sample size, demographics)
- Intervention details (duration, frequency, delivery method)
- Comparator details
- Outcomes (with units, time points)
- Effect sizes and confidence intervals

---

#### Outcomes & Risk of Bias (Items 13-14)

- [ ] **#13 - Outcomes and prioritization**:
  - **13a**: List and define primary and secondary outcomes
  - **13b**: Describe methods for assessment (e.g., time points)

**Example**:
```markdown
## Outcomes

### Primary Outcome
- Knowledge retention at ≥ 1 month post-intervention (measured by test performance)

### Secondary Outcomes
- Knowledge retention at 1 week, 6 months, 12 months
- Transfer of learning to novel contexts
- Participant satisfaction
- Time investment required
```

- [ ] **#14 - Risk of bias in individual studies**: Describe methods for assessing risk of bias

**Common Tools**:
- **Cochrane Risk of Bias 2 (RoB 2)**: For RCTs
- **ROBINS-I**: For non-randomized studies
- **Newcastle-Ottawa Scale**: For observational studies
- **ROBIS**: For systematic reviews

**Example**: "Risk of bias will be assessed using Cochrane RoB 2 tool. Two reviewers will independently assess: randomization process, deviations from intended interventions, missing outcome data, measurement of outcome, selection of reported results. Overall bias rating: low, some concerns, high."

---

#### Synthesis (Item 15)
- [ ] **#15**:
  - **15a**: Describe planned synthesis methods
  - **15b**: Describe methods for meta-analysis (if planned)
  - **15c**: Describe potential effect modifiers and subgroup analyses
  - **15d**: Describe sensitivity analyses

**Template**:
```markdown
## Data Synthesis

### Synthesis Method
[Narrative synthesis | Meta-analysis | Both]

**Narrative Synthesis**: If studies are too heterogeneous for meta-analysis, findings will be synthesized thematically and organized by outcome.

**Meta-Analysis**: If ≥3 studies report same outcome with comparable methods:
- Random-effects model using DerSimonian-Laird method
- Standardized mean difference (SMD) as effect measure
- Forest plots for visualization
- I² statistic for heterogeneity assessment
  - I² < 25%: Low heterogeneity
  - I² 25-75%: Moderate heterogeneity
  - I² > 75%: High heterogeneity

### Subgroup Analyses (Planned)
- By age group (children vs adults)
- By retention interval (< 1 month vs ≥ 1 month)
- By intervention duration (< 4 weeks vs ≥ 4 weeks)

### Sensitivity Analyses
- Exclude studies with high risk of bias
- Exclude studies with small sample size (N < 30)
- Fixed-effect vs random-effects model comparison
```

---

#### Meta-Biases & Confidence (Items 16-17)

- [ ] **#16 - Meta-biases**: Describe assessments for publication bias

**Methods**:
- **Funnel plots**: Visual assessment (if ≥10 studies)
- **Egger's test**: Statistical test for funnel plot asymmetry
- **Trim-and-fill**: Adjust for publication bias
- **Grey literature search**: Reduce publication bias

- [ ] **#17 - Confidence in cumulative evidence**: Describe methods for assessing certainty

**GRADE Framework** (Recommended):
- **High**: Very confident in effect estimate
- **Moderate**: Moderately confident
- **Low**: Limited confidence
- **Very Low**: Very little confidence

**GRADE Domains**:
1. Risk of bias
2. Inconsistency
3. Indirectness
4. Imprecision
5. Publication bias

---

## PROSPERO Registration

### What is PROSPERO?

International prospective register for systematic review protocols. Covers:
- Systematic reviews
- Rapid reviews
- Umbrella reviews

**Domains**: Healthcare, public health, social welfare, education, justice

### How to Register

**Step 1: Create Account**
- Go to [PROSPERO](https://www.crd.york.ac.uk/prospero/)
- Register for free account
- Verify email

**Step 2: Complete Registration Form**
PROSPERO form includes:
- Administrative details (title, authors, funding)
- Review question (PICO)
- Eligibility criteria
- Search strategy
- Data extraction methods
- Risk of bias assessment
- Synthesis methods

**Tip**: PROSPERO fields align with PRISMA-P items. Use your protocol to complete registration.

**Step 3: Submit for Review**
- PROSPERO staff review for completeness (not scientific merit)
- Typical review time: 1-3 weeks
- Registration number assigned upon approval

**Step 4: Public Record**
- Protocol becomes publicly searchable
- You can update protocol (amendments tracked)
- Include registration number in all publications

### Registration Timeline

**Ideal**: Register before starting systematic search

**Acceptable**: Register before completing data extraction

**Too Late**: After analysis complete (cannot register)

**Important**: Date of registration is public. Early registration demonstrates prospective planning.

---

## Protocol Document Structure

Create comprehensive protocol document following this template:

```markdown
---
title: "Protocol for Systematic Review of [Topic]"
registration: "PROSPERO [number]"
date: "YYYY-MM-DD"
version: "1.0"
---

# Protocol for Systematic Review of [Topic]

## Administrative Information

### Title
[Full protocol title]

### Registration
PROSPERO Registration Number: [CRD42026XXXXXX]

### Authors
[List all authors with affiliations and contributions]

### Amendments
None (initial protocol) | [Document any amendments with dates and rationale]

---

## Introduction

### Rationale
[Why this review is needed, context of existing knowledge]

### Objectives
[Explicit statement using PICO]

---

## Methods

### Eligibility Criteria
[Detailed inclusion/exclusion criteria with PICO]

### Information Sources
[All databases, grey literature, other sources with dates]

### Search Strategy
[Full Boolean query for each database]

### Study Selection
[Screening process, number of reviewers, disagreement resolution]

### Data Extraction
[Extraction form, pilot testing, data items collected]

### Risk of Bias Assessment
[Tool to be used, domains assessed, number of reviewers]

### Data Synthesis
[Narrative, meta-analysis, or both; effect measures; heterogeneity]

### Subgroup & Sensitivity Analyses
[Planned subgroups and sensitivity analyses]

### Publication Bias Assessment
[Methods for assessing publication bias]

### Confidence in Evidence
[GRADE or other framework]

---

## References
[Cite foundational studies, methodological papers]

---

## Appendices

### Appendix A: Search Strategies (All Databases)
[Full search strings for each database]

### Appendix B: Data Extraction Form
[Full extraction form with all fields]

### Appendix C: Risk of Bias Tool
[Detailed criteria for each domain]
```

---

## Protocol Templates by Review Type

### Standard Systematic Review
Use full PRISMA-P 17-item checklist above.

### Rapid Review (Streamlined)
- Focused question (narrow PICO)
- Limited databases (2-3 major ones)
- Single reviewer with verification
- Narrative synthesis (no meta-analysis)
- 4-8 week timeline

### Scoping Review
- Broader question (may not use PICO)
- Use PRISMA-ScR extension
- May include more diverse study types
- Typically narrative synthesis
- Focus on mapping literature landscape

---

## Common Protocol Pitfalls

### Issues to Avoid:

❌ **Vague eligibility criteria**: Be specific about PICO elements

❌ **Incomplete search strategy**: Must include full Boolean queries

❌ **No risk of bias plan**: Must specify tool and domains

❌ **Missing subgroup plans**: Pre-specify subgroups to avoid p-hacking

❌ **No publication bias plan**: Required if meta-analysis planned

❌ **Registering after data extraction**: Registration must be prospective

### Quality Indicators:

✅ **PROSPERO registration** before starting search

✅ **PICO clearly defined** with operational definitions

✅ **Full search strategies** for all databases

✅ **Risk of bias tool** specified with domains

✅ **Analysis plan** detailed (including subgroups)

✅ **2+ reviewers** for screening and extraction

---

## Updating Your Protocol

### When to Amend

Amendments acceptable for:
- Adding databases not originally planned
- Modifying search terms based on initial results
- Adding outcomes discovered during review
- Changing risk of bias tool if original inappropriate

**Important**: Document all amendments with dates and rationale (PRISMA-P Item 3c)

### How to Amend

**PROSPERO**: Update record and note amendments in "Revision notes"

**Protocol Document**: Create version 1.1, 1.2, etc. with changelog

**Publication**: Report all amendments in methods section

---

## Tools & Resources

### Protocol Templates
- [Cochrane Protocol Template](https://training.cochrane.org/handbook/current/chapter-02)
- [PRISMA-P Checklist](http://www.prisma-statement.org/documents/PRISMA-P-checklist.pdf)
- [JBI Protocol Template](https://jbi.global/critical-appraisal-tools)

### Registration Platforms
- [PROSPERO](https://www.crd.york.ac.uk/prospero/) - Primary platform
- [Open Science Framework (OSF)](https://osf.io/) - Alternative for non-health reviews

### Software Tools
- [Covidence](https://www.covidence.org/) - Screening and extraction (PRISMA export)
- [RevMan](https://training.cochrane.org/online-learning/core-software/revman) - Cochrane's review manager
- [DistillerSR](https://www.evidencepartners.com/) - Systematic review software

---

## Next Steps

After completing protocol:
1. **Register on PROSPERO** (before starting search)
2. **Begin systematic search** → [[SKILL#Phase 1]]
3. **Follow PRISMA 2020** during execution → [[prisma-compliance]]
4. **Assess quality** upon completion → [[quality-assessment]]

---

## References

**Primary Sources**:
- Moher, D., et al. (2015). Preferred reporting items for systematic review and meta-analysis protocols (PRISMA-P) 2015 statement. *Systematic Reviews*, 4:1. [PMC4320440](https://pmc.ncbi.nlm.nih.gov/articles/PMC4320440/)
- Shamseer, L., et al. (2015). Preferred reporting items for systematic review and meta-analysis protocols (PRISMA-P) 2015: elaboration and explanation. *BMJ*, 350:g7647.

**Registration Resources**:
- [PROSPERO Registry](https://www.crd.york.ac.uk/prospero/)
- [PROSPERO User Guide](https://www.crd.york.ac.uk/prospero/#guidancenotes)

**Protocol Guides**:
- [UW Libraries: Writing a Protocol](https://guides.lib.uw.edu/hsl/sr/protocol)
- [UNC: Protocol & Registration](https://guides.lib.unc.edu/systematic-reviews/protocol)

---

**Related**: [[prisma-compliance]] | [[quality-assessment]] | [[SKILL|Back to Overview]]
