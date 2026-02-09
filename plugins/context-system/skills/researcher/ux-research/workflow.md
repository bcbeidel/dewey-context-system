# UX Research Workflow

**Purpose**: Understand user needs, behaviors, and attitudes to inform product design decisions.

**Version**: 1.0
**Created**: 2026-02-08
**Status**: Production

---

## Overview

UX research uses systematic methods to understand users and inform design decisions. From quick usability tests (1 week) to comprehensive studies (4 weeks).

**Core principle**: Real users over synthetic users - actual target users, not AI-generated personas.

**When to use**: Dashboard UX, self-service analytics, product design, understanding adoption barriers, design validation.

---

## Quick Start

**Choose your entry point**:

- **New to UX research?** → Start with "What is UX Research?" below
- **Know your research question?** → Jump to Phase 1: Planning
- **Need method guidance?** → See [[methods-catalog]]
- **Want examples?** → See [[examples]]

---

## What is UX Research?

### Core Principles (Nielsen Norman Group)

**Key practices**:
1. **Use multiple methods**: Nearly all projects benefit from combining insights
2. **Mix qual + quant**: Pair qualitative (why) with quantitative (how many)
3. **Real users**: Authentic research with actual target users, not synthetic/fake users
4. **Appropriate sample**: Quality over quantity for qualitative, statistical rigor for quantitative

**Source**: [[../../context/research/ux-research-standards]]

---

### Three Dimensions of Methods

**1. Attitudinal vs. Behavioral**
- **Attitudinal**: What people *say* (interviews, surveys)
- **Behavioral**: What people *do* (usability tests, analytics)

**2. Qualitative vs. Quantitative**
- **Qualitative**: Understanding context and why (interviews, observations)
- **Quantitative**: Measuring patterns and how many (surveys, metrics)

**3. Context of Use**
- **Natural use**: In real environment (field studies, diary studies)
- **Scripted use**: Controlled tasks (usability testing, experiments)

**Best practice**: Combine methods across dimensions for robust insights.

---

## Four-Phase Workflow

### Timeline

**Typical UX research project**: 1-4 weeks

**Phase breakdown**:
- Phase 1: Planning (1-2 days)
- Phase 2: Data Collection (3-7 days)
- Phase 3: Analysis (2-5 days)
- Phase 4: Communication (1-3 days)

---

## Phase 1: Planning

**Goal**: Define research questions, select methods, recruit participants, prepare materials.

**Duration**: 1-2 days

---

### Activities

**1. Define research questions** (2-4 hours)
- What do you want to learn?
- What decisions will this research inform?
- What are your assumptions or hypotheses?

**Good research questions**:
- "What pain points do users experience in the checkout flow?"
- "How do analysts currently explore data before creating dashboards?"
- "What's preventing teams from adopting self-service analytics?"

**Bad research questions**:
- "Is our design good?" (too vague)
- "Do users like feature X?" (leading, binary)

---

**2. Select research methods** (1-2 hours)
- Match methods to research questions
- Consider timeline and resources
- Plan to use 2-3 methods for triangulation

**Quick method selector**:
- **Exploratory** (don't know much yet): User interviews, contextual inquiry
- **Evaluative** (testing specific design): Usability testing, heuristic evaluation
- **Measurement** (how much/how many): Surveys, analytics analysis

**See**: [[methods-catalog]] for detailed method descriptions

---

**3. Recruit participants** (2-4 hours setup, ongoing)
- Define target users (who are they?)
- Determine sample size (see guidelines below)
- Create screener to qualify participants
- Schedule sessions

**Sample size guidelines**:

**Qualitative**:
- User interviews: 5-8 per user segment
- Usability testing: 5 users (Nielsen research: 85% of issues found)
- Contextual inquiry: 6-12 users
- Focus groups: 3-5 groups of 6-8 people each

**Quantitative**:
- Surveys: 100+ for patterns, 400+ for segmentation
- A/B tests: Calculate based on effect size (use calculator)
- Analytics: Depends on traffic volume

---

**4. Prepare materials** (2-4 hours)
- Create discussion/interview guides
- Develop usability test tasks
- Design survey questionnaires
- Prepare consent forms

**Discussion guide template**:
```markdown
# User Interview Guide

## Introduction (5 min)
- Thank participant
- Explain purpose
- Explain confidentiality
- Get consent

## Warm-up (5 min)
- Background questions
- Build rapport

## Core Questions (30-40 min)
[Open-ended questions about topic]
- Question 1: [Main question]
  - Probe: [If needed, ask follow-up]
- Question 2: [Main question]
  - Probe: [If needed, ask follow-up]

## Wrap-up (5 min)
- Anything else to share?
- Questions for me?
- Thank you

Total time: 45-60 min
```

---

### Phase 1 Outputs

- ✅ Research questions defined
- ✅ Methods selected (2-3 methods)
- ✅ Participants recruited
- ✅ Materials prepared (guides, surveys, prototypes)
- ✅ Schedule confirmed

---

## Phase 2: Data Collection

**Goal**: Conduct research sessions and gather data systematically.

**Duration**: 3-7 days (depending on method and sample size)

---

### Best Practices for Sessions

**1. User interviews** (45-60 minutes each)
- Start with easy warm-up questions
- Ask open-ended questions ("Tell me about..." not "Do you like...")
- Use probes ("Can you say more about that?" "Walk me through...")
- Listen more than talk (80/20 rule)
- Record sessions (with consent)
- Take notes even when recording

**See**: [[methods-catalog#user-interviews]]

---

**2. Usability testing** (45-60 minutes each)
- Give realistic tasks, not instructions
- Encourage think-aloud (say what you're thinking)
- Don't help - observe where they struggle
- Note: task success, time, errors, verbalizations
- Probe after tasks ("What were you expecting?")

**See**: [[methods-catalog#usability-testing]]

---

**3. Surveys** (send, wait, remind)
- Pilot test with 3-5 people first
- Use mix of question types (rating scales, multiple choice, open-ended)
- Keep surveys short (<10 minutes)
- Send reminders after 3-5 days
- Incentivize if possible

**Survey testing methods** (run all three):
- **Cognitive walkthroughs**: Test question clarity
- **Mechanical tests**: Check skip logic, branching
- **Usability tests**: Observe people taking survey

**See**: [[methods-catalog#surveys]]

---

**4. Contextual inquiry** (2-3 hours each)
- Observe users in their environment
- Master-apprentice model (they teach you)
- Minimize interruptions while observing
- Ask about tools, workarounds, pain points
- Take photos/videos (with consent)

**See**: [[methods-catalog#contextual-inquiry]]

---

### Data Collection Tips

**Do**:
- ✅ Record everything (audio/video/screen with consent)
- ✅ Take notes even when recording
- ✅ Note non-verbal cues (facial expressions, tone)
- ✅ Thank participants sincerely
- ✅ Be flexible - follow interesting threads

**Don't**:
- ❌ Lead participants ("Don't you think...")
- ❌ Explain or justify design during sessions
- ❌ Rush through - let participants think
- ❌ Ignore edge cases - they reveal insights

---

### Phase 2 Outputs

- ✅ Session recordings (audio/video/screen)
- ✅ Session notes (observations, quotes, insights)
- ✅ Quantitative data (survey responses, metrics, task success rates)
- ✅ Artifacts (photos, screenshots, examples)

---

## Phase 3: Analysis

**Goal**: Synthesize findings, identify patterns, prioritize insights.

**Duration**: 2-5 days

---

### Activities

**1. Organize data** (1 day)
- Transcribe recordings (or use AI tools like Otter, Dovetail)
- Compile notes into shared space (Miro, Notion, spreadsheet)
- Tag/code qualitative data by theme
- Clean quantitative data (survey responses, metrics)

---

**2. Identify patterns** (1-2 days)

**For qualitative data**:
- **Affinity diagramming**: Group similar observations
- **Thematic coding**: Identify recurring themes
- **Quote extraction**: Find representative quotes
- **Pattern recognition**: What repeats across participants?

**For quantitative data**:
- **Descriptive statistics**: Means, medians, distributions
- **Cross-tabulation**: Compare segments
- **Correlation analysis**: What relates to what?
- **Visualizations**: Charts, graphs for patterns

---

**3. Synthesize insights** (1-2 days)

**Combine qual + quant**:
- Do quantitative patterns align with qualitative themes?
- Do qualitative insights explain quantitative patterns?
- Use joint displays to show integration

**Example joint display**:
| Theme (Qual) | Frequency (Quant) | Representative Quote | Action Priority |
|--------------|-------------------|----------------------|-----------------|
| Slow performance | 78% reported in survey | "Takes forever to load..." | High |
| Confusing navigation | 45% reported | "I never know where to find things" | Medium |

---

**4. Prioritize findings** (1 day)

**Criteria for prioritization**:
- **Frequency**: How many users experience this?
- **Severity**: How much does it impact users?
- **Business impact**: How does it affect key metrics?
- **Feasibility**: How easy to fix?

**Prioritization matrix**:
```
High Impact, Easy Fix → DO FIRST
High Impact, Hard Fix → PLAN FOR
Low Impact, Easy Fix → QUICK WINS
Low Impact, Hard Fix → DEPRIORITIZE
```

---

### Phase 3 Outputs

- ✅ Findings synthesized (themes, patterns, insights)
- ✅ Qualitative + quantitative integrated
- ✅ Insights prioritized (high/medium/low)
- ✅ Supporting evidence compiled (quotes, data, examples)

---

## Phase 4: Communication

**Goal**: Present findings and recommendations to stakeholders.

**Duration**: 1-3 days

---

### Deliverables

**1. Research report** (1-2 days)

**Structure**:
```markdown
# UX Research Report: [Project Name]

## Executive Summary (1 page)
- Research goals
- Methods used
- Key findings (top 3-5)
- Top recommendations

## Background (1 page)
- Research questions
- Participants (who, how many)
- Methods and timeline

## Findings (3-5 pages)
### Finding 1: [Insight]
- Evidence: [Quotes, data, screenshots]
- Impact: [Why it matters]
- Recommendation: [What to do]

### Finding 2: [Insight]
[Same structure]

## Prioritized Recommendations (1 page)
[Priority matrix or ordered list]

## Appendices
- Participant screener
- Discussion guide
- Raw data (link)
- Supplementary insights
```

---

**2. Presentation** (prepare in 1 day, present in 1 hour)

**Slide structure** (10-15 slides):
1. Title slide
2. Research goals
3. Methods overview
4. Key finding 1 (with evidence)
5. Key finding 2 (with evidence)
6. Key finding 3 (with evidence)
7. Prioritized recommendations
8. Next steps
9. Q&A

**Presentation tips**:
- Lead with insights, not process
- Use visuals (photos, quotes, videos)
- Tell stories, not just data
- Be clear about confidence level
- Connect findings to business goals

---

**3. One-pager** (for executives)

**Single page summary**:
- Problem researched
- Methods (1 sentence)
- Key findings (3-5 bullets)
- Top recommendations (3 bullets)
- Impact if implemented

---

### Making Research Actionable

**Good recommendations**:
- **Specific**: "Add search functionality to dashboard nav" (not "improve navigation")
- **Evidence-based**: Link to finding (#3: Confusing navigation)
- **Prioritized**: Label as high/medium/low priority
- **Feasible**: Acknowledged within team capability

**Bad recommendations**:
- Vague ("improve UX")
- Not grounded in data ("users probably want...")
- Overly prescriptive ("change button to blue #0000FF")

---

### Phase 4 Outputs

- ✅ Research report (detailed findings)
- ✅ Presentation (stakeholder-ready)
- ✅ One-pager (executive summary)
- ✅ Raw data archived (for future reference)

---

## Combining Methods

### Common Combinations

**Discovery → Validation**:
1. User interviews (discover pain points)
2. Survey (measure how widespread)
3. Usability test (validate solution)

**Triangulation**:
1. User interviews (what they say)
2. Contextual inquiry (what they do)
3. Analytics (what data shows)

**Qualitative → Quantitative**:
1. User interviews (generate themes)
2. Survey (quantify themes across population)

**See**: [[../../context/research/mixed-methods-research-standards]] for formal mixed methods approach

---

## Measuring Success

### Paired with Metrics

**Pair qualitative methods with quantitative metrics**:
- User interviews + **System Usability Scale (SUS)**: Understand usability + benchmark
- Usability testing + **Single Ease Question (SEQ)**: Identify issues + measure task difficulty
- Field studies + **Analytics data**: Understand context + measure behavior

**SUS** (System Usability Scale):
- 10-item standardized questionnaire
- Score 0-100 (68+ = above average)
- Use for benchmarking and tracking over time

**SEQ** (Single Ease Question):
- "Overall, how difficult or easy was it to complete this task?" (1-7 scale)
- Quick post-task metric

---

## Troubleshooting

### "I'm not finding clear patterns in my data"

**Common causes**:
- Too few participants (need 5-8 per segment for qualitative)
- Too broad research questions
- Participants don't represent actual users

**Solutions**:
1. Recruit more participants (especially if high variability)
2. Narrow focus to specific user segment or workflow
3. Revisit screener - are you getting right participants?
4. Look for smaller patterns (even 2-3 participants = signal)

---

### "Qualitative and quantitative findings don't align"

**This is normal and valuable!**

**Causes**:
- Survey measures stated preferences, interviews reveal actual behavior
- Different user segments emphasize different issues
- Qualitative finds new issues surveys didn't ask about

**Solutions**:
1. Report both findings honestly
2. Investigate contradictions (often most insightful)
3. Consider follow-up research to resolve
4. Accept complexity - real users are nuanced

**See**: [[../../context/research/mixed-methods-research-standards#handling-contradictions]]

---

### "Stakeholders dismissing findings as 'just opinions'"

**Solutions**:
1. **Quantify where possible**: "7 of 8 participants struggled with..."
2. **Show evidence**: Include video clips, quotes, task success rates
3. **Link to business metrics**: "This likely causes 30% cart abandonment..."
4. **Be transparent**: Acknowledge limitations, explain methodology
5. **Benchmark**: Use SUS or other standardized measures

---

## Known Limitations

**When UX research may not be appropriate**:
- Decision already made (research won't influence)
- Timeline too short for quality work (<3 days)
- Can't access representative users
- Resources insufficient for proper research

**UX research requires**:
- Access to target users (for recruitment)
- Time for proper data collection (3-7 days minimum)
- Some experience with research methods (or guidance)
- Stakeholder willingness to act on findings

---

## Integration with Other Methods

**Common combinations**:
- **UX + Market Research**: User needs + market opportunity
- **UX + Design Science**: User research → Iterative prototyping
- **UX + Case Study**: User research in specific organizational context

---

## Related Documentation

**Core reference**:
- [[../../context/research/ux-research-standards]] - Research standards (Nielsen Norman Group)
- [[methods-catalog]] - 20 UX research methods detailed
- [[examples]] - Real UX research projects

**Other methodologies**:
- [[../mixed-methods/workflow]] - For formal qual + quant integration
- [[../design-science/workflow]] - For user-centered artifact development

---

## Sources

Based on:
- Nielsen Norman Group research methods framework
- [[../../context/research/ux-research-standards]]
- Industry best practices (2024-2025)

---

**First Use**: Define your research question, then work through Phase 1 to select appropriate methods
