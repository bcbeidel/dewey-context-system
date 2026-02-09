# Research Methodology Examples

**Purpose**: Real-world examples demonstrating methodology selection and execution across different research contexts.

**Created**: 2026-02-08

---

## Example 1: "Should we build this feature?"

### Context

**Role**: VP Product at SaaS company
**Question**: "Users are requesting collaborative editing. Should we build it?"
**Timeline**: 3 weeks
**Stakeholders**: CEO, Engineering, Design

---

### Methodology Selection (via wizard)

**Wizard questions answered**:
- **Goal**: Make decision (go/no-go on feature)
- **Evidence needed**: User needs + market dynamics
- **Timeline**: 3 weeks
- **Existing research**: Some user feedback, no systematic analysis
- **Primary users**: Technology consulting, marketing agencies

**Wizard recommendation**: **Market Research** (need both user validation and competitive landscape)

**Rationale**: Decision requires understanding both customer needs (do they really need this?) and market dynamics (do competitors have it? is it table stakes?).

---

### Execution

**Week 1: Secondary Research**
- Competitive analysis: 8 competitors analyzed
- 6/8 have collaborative editing (table stakes signal)
- G2 reviews analyzed: 127 mentions of "real-time collaboration" as need

**Week 2: Primary Research**
- Interviews: 12 customers (6 current users + 6 prospects who chose competitor)
- Key finding: "We chose [Competitor] because we needed teams to work together" (4/6 prospects)
- Current users: "We use Google Docs for collaboration then copy back" (workaround)

**Week 3: Analysis & Decision**
- Market gap: Feature is table stakes (6/8 competitors have it)
- Customer validation: High demand (10/12 customers want it)
- Competitive pressure: Losing deals due to absence
- **Decision**: BUILD (high confidence, multiple sources converge)

**Recommendation to CEO**: "Build collaborative editing. Evidence shows it's table stakes (6/8 competitors), causing deal losses (4/6 prospects cited it), and current customers work around absence (Google Docs). ROI positive."

---

### Lessons Learned

**What worked**:
- Triangulation (competitive + customer + review data) gave high confidence
- 3 weeks sufficient for go/no-go decision (didn't need months)
- Mixed qual (interviews) + quant (competitor count, review mentions) balanced depth and breadth

**What didn't**:
- Wish we'd interviewed lost deals earlier (waited until Week 2)
- Could have surveyed broader user base for quantification

**Outcome**: Feature built, launched Q3, retention increased 15% (users no longer churning due to collaboration needs)

---

## Example 2: "Why did our reorg fail?"

### Context

**Role**: Head of People at tech company
**Question**: "We reorganized 6 months ago, but morale and performance declined. What happened?"
**Timeline**: 8 weeks
**Stakeholders**: CEO, Leadership team

---

### Methodology Selection

**Wizard questions answered**:
- **Goal**: Understand why (explanatory)
- **Evidence**: Need depth, context, real-world complexity
- **Timeline**: 8 weeks
- **Phenomenon**: Recent event, observable, bounded

**Wizard recommendation**: **Case Study Research** (explanatory)

**Rationale**: Need to understand causal mechanisms (why did reorg fail?) in specific real-world context. Case study enables deep investigation with multiple data sources.

---

### Execution

**Phase 1: Case Definition** (Week 1)
- **Boundaries**: Reorganization (Jan 2024 - July 2024), Engineering org (120 people)
- **Data sources**: Interviews, documents (emails, memos), archival (engagement surveys, turnover), observations (team meetings)

**Phase 2: Data Collection** (Week 2-6)
- Interviews: 25 participants (leadership, managers, ICs)
- Documents: 50+ emails, org charts, reorg announcement, retro notes
- Archival: Engagement scores (pre: 4.1/5, post: 3.2/5), turnover (10 people left)
- Observations: Attended 6 team meetings

**Phase 3: Analysis** (Week 7)
- **Chronology**: Jan announcement → Feb implementation → March confusion → April-July decline
- **Themes identified**:
  1. **Top-down design** (15/25 mentioned): "No one asked us how to organize"
  2. **Unclear rationale** (18/25): "We still don't know why we reorganized"
  3. **Broken relationships** (12/25): "I lost my team, had to rebuild trust"
  4. **Role confusion** (14/25): "Unclear who owns what now"

**Phase 4: Explanation** (Week 7)
- **Why reorg failed**:
  1. Lack of input → No buy-in → Resistance
  2. Unclear rationale → Perceived arbitrary → Distrust of leadership
  3. Broke high-functioning teams → Lost relationships → Performance drop
  4. Poor communication → Role confusion → Coordination overhead

**Rival explanations examined**:
- Not due to structure itself (structure was reasonable)
- Not due to individual leaders (same leaders, pre-reorg they were effective)
- **Root cause**: Process of reorg (top-down, unclear why, broke relationships)

**Phase 5: Reporting** (Week 8)
- Case study report (20 pages)
- Presentation to leadership (25 slides)
- **Recommendations**: If reorg needed in future:
  1. Involve teams in design (co-create, don't dictate)
  2. Communicate clear rationale (why are we doing this?)
  3. Preserve high-functioning teams when possible
  4. Invest in relationship-building post-reorg (team offsites, 1-on-1s)

---

### Lessons Learned

**What worked**:
- Multiple data sources (triangulation) revealed consistent themes
- Chronology helped establish causal sequence
- Rival explanations strengthened argument (showed we considered alternatives)

**What didn't**:
- Interviews were retrospective (6 months later, some memory loss)
- Wish we'd observed during reorg (real-time data better than retrospective)

**Outcome**: Leadership committed to co-creation approach for future reorgs, engagement recovered over next 6 months (3.2 → 3.9)

---

## Example 3: "What does research say about developer productivity?"

### Context

**Role**: Director of Engineering
**Question**: "We're investing in developer experience. What does research say about what actually improves productivity?"
**Timeline**: 2 weeks (needed fast insights)
**Stakeholders**: VP Engineering, Team leads

---

### Methodology Selection

**Wizard questions answered**:
- **Goal**: Understand current knowledge
- **Evidence type**: Academic research preferred
- **Timeline**: 2 weeks (tight!)
- **Depth**: Need synthesis, not single paper

**Wizard recommendation**: **Evidence Synthesis (REA variant)**

**Rationale**: Academic question, but time-constrained (2 weeks). Rapid Evidence Assessment balances rigor with pragmatism.

---

### Execution

**Phase 1: Rapid Scoping** (Day 1-2)
- **Research question**: "What factors improve software developer productivity?"
- **Databases**: Google Scholar, ACM Digital Library, IEEE Xplore
- **Inclusion**: Empirical studies, published 2015-2025, peer-reviewed

**Phase 2: Search & Screening** (Day 3-4)
- Search results: 156 papers
- Title/abstract screen: 156 → 32 relevant
- Full-text screen: 32 → 18 included

**Phase 3: Rapid Synthesis** (Day 5-8)
- Data extraction (18 papers, 20 min each = 6 hours)
- **Themes identified** (from synthesis):
  1. **Flow state** (12/18 papers): Minimize interruptions, focus time
  2. **Tooling quality** (10/18): Fast builds, good IDEs, automation
  3. **Code quality** (8/18): Tech debt slows productivity
  4. **Psychological safety** (7/18): Safe to ask questions, admit mistakes
  5. **Clear goals** (9/18): Know what to build, why it matters

**Phase 4: Executive Reporting** (Day 9-10)
- Executive summary (1 page)
- Detailed report (12 pages)
- Recommendations:
  1. **High confidence** (strong evidence): Protect focus time, invest in tooling
  2. **Moderate confidence** (mixed evidence): Reduce tech debt, improve psychological safety
  3. **Weak evidence** (few studies): Team size effects unclear

---

### Lessons Learned

**What worked**:
- REA variant provided actionable insights in 2 weeks (full systematic review would take 6-8 weeks)
- Thematic synthesis (not paper-by-paper) made findings digestible for executives
- Confidence levels (high/moderate/weak) set expectations appropriately

**What didn't**:
- Single reviewer (me) - no duplicate screening or extraction
- Limited databases (3 vs 5-7 for full systematic review)
- Acknowledged these limitations transparently in report

**Outcome**: Invested in "focus time" initiative (no-meeting Wednesdays), upgraded CI/CD to faster builds, both evidence-backed with research citations

---

## Example 4: "How do high-performing teams collaborate?"

### Context

**Role**: Organizational researcher (academic)
**Question**: "What collaboration practices distinguish high-performing teams from average teams?"
**Timeline**: 12 weeks (dissertation chapter)
**Stakeholders**: Dissertation committee, academic community

---

### Methodology Selection

**Wizard questions answered**:
- **Goal**: Understand AND measure (exploratory + confirmatory)
- **Evidence**: Need depth (practices) and breadth (prevalence)
- **Timeline**: 12 weeks
- **Phenomenon**: Collaboration practices (behavioral)

**Wizard recommendation**: **Mixed Methods Research** (Exploratory Sequential design)

**Rationale**: Don't know what collaboration practices matter (need exploration), but want to measure prevalence (need quantification). Qual → Quant sequence fits.

---

### Execution

**Phase 1: Qualitative Exploration** (Week 1-4)
- Ethnography: Observed 4 teams (2 high-performing, 2 average) for 2 weeks each
- Interviews: 20 team members (10 per performance level)
- **Themes identified**:
  1. **Explicit coordination** (8/10 high-performing): Daily standups, clear owners, written decisions
  2. **Psychological safety** (9/10 high-performing): Openly admit mistakes, ask "dumb" questions
  3. **Knowledge sharing** (7/10 high-performing): Documentation culture, pair programming
  4. **Transparent priorities** (8/10 high-performing): Everyone knows top 3 priorities
  5. **Rapid feedback loops** (6/10 high-performing): Quick code reviews, frequent demos

**Connection Point** (Week 5)
- Transform themes → survey scale items
- **Explicit coordination scale** (5 items):
  - "Our team has daily standups" (1=Never, 5=Always)
  - "Decisions are documented in writing"
  - "It's clear who owns each work item"
  - [2 more items]
- **[Similar scales for other 4 themes]**

**Phase 2: Quantitative Testing** (Week 6-9)
- Survey: 300 team members across 40 teams
- Performance ratings: Manager-rated team performance (1-5 scale)
- **Analysis**:
  - Factor analysis validated 5 scales (α > .80 for all)
  - Correlation: All 5 practices → team performance (r = .35-.58)
  - Regression: Psychological safety strongest predictor (β = .52, p < .001)

**Phase 3: Integration** (Week 10-11)
- Joint display:

| Practice (Qual) | High-Perf Teams (Qual) | Scale α (Quant) | Correlation with Performance (Quant) |
|-----------------|------------------------|-----------------|--------------------------------------|
| Explicit coordination | 8/10 | .84 | r = .42** |
| Psychological safety | 9/10 | .88 | r = .58*** |
| Knowledge sharing | 7/10 | .81 | r = .35** |
| Transparent priorities | 8/10 | .86 | r = .47*** |
| Rapid feedback | 6/10 | .82 | r = .38** |

- **Meta-inference**: Qualitative observation validated at scale. Psychological safety most critical (both qual + quant converge).

**Phase 4: Dissertation Chapter** (Week 12)
- Integrated findings (20 pages)
- Theoretical contribution: 5-factor model of team collaboration
- Practical contribution: Validated measurement instrument
- Limitations: Cross-sectional (can't prove causality), tech teams only

---

### Lessons Learned

**What worked**:
- Exploratory sequential perfect for instrument development
- Qual provided ecological validity (real practices, participant language)
- Quant validated qual insights at scale (n=300)

**What didn't**:
- 12 weeks was tight (wish we had 16 weeks for deeper qual phase)
- Qual sample was small (n=20, but sufficient for theme saturation)

**Outcome**: Dissertation chapter accepted, instrument published, 3 organizations using instrument for team assessments

---

## Example 5: "How do we improve our culture?"

### Context

**Role**: CEO of 200-person company
**Question**: "Our culture feels off. What is it, and how do we improve it?"
**Timeline**: 6 weeks
**Stakeholders**: Leadership team, all employees

---

### Methodology Selection

**Wizard questions answered**:
- **Goal**: Diagnose culture (what is it?) and guide change (how to improve?)
- **Evidence**: Need both measurement (quant) and meaning (qual)
- **Timeline**: 6 weeks
- **Phenomenon**: Organizational culture

**Wizard recommendation**: **Organizational & Culture Research** (Combined approach: Structured assessment + Ethnography)

**Rationale**: Culture research is the specialty methodology for this. Combined approach provides numbers (for tracking) and depth (for understanding).

---

### Execution

**Phase 1: Structured Assessment** (Week 1-2)
- Denison Organizational Culture Survey deployed
- Response rate: 82% (164/200 employees)
- **Results**:
  - Mission: 72/100 (strong - people know where we're going)
  - Adaptability: 38/100 (weak - rigid, slow to change)
  - Involvement: 58/100 (moderate - mixed empowerment)
  - Consistency: 68/100 (good - stable processes)

- **Insight**: Low adaptability is the problem area

**Phase 2: Ethnographic Depth** (Week 3-5)
- **Focus**: Why is adaptability low? (targeted ethnography)
- Observations: 10 meetings (decision-making, planning)
- Interviews: 15 participants (managers, ICs)
- **Themes explaining low adaptability**:
  1. **Approval-seeking** (11/15): "Everything needs CEO sign-off"
  2. **Fear of failure** (9/15): "If it fails, you're blamed"
  3. **Process over speed** (10/15): "6-step approval for minor changes"
  4. **Risk aversion** (12/15): "We say no to new ideas by default"

**Phase 3: Integration** (Week 6)
- Joint display:

| Denison Trait | Score | Ethnographic Evidence | Explanation |
|---------------|-------|-----------------------|-------------|
| Adaptability (LOW) | 38/100 | Approval-seeking, fear, process, risk aversion | CEO bottleneck + blame culture + over-process → can't adapt quickly |
| Involvement (MID) | 58/100 | Mixed empowerment ("some teams autonomous, others micromanaged") | Inconsistent empowerment |
| Mission (HIGH) | 72/100 | "Everyone knows our vision" | Clear strategy communication |

- **Root cause**: Culture optimized for consistency (don't make mistakes) at expense of adaptability (try new things)

**Phase 4: Recommendations** (Week 6)
1. **Decentralize decisions** (increase Involvement → enables Adaptability)
   - Clear decision rights (what teams own vs what CEO owns)
   - Pilot with 2 teams, expand if successful

2. **Ritualize learning from failure** (reduce fear)
   - Monthly "Failure Fridays" - share experiments that didn't work
   - CEO models vulnerability (shares own failures)

3. **Simplify approval process** (reduce Consistency overhead)
   - 6-step → 2-step for low-risk changes
   - Reserve heavy process for high-risk only

4. **Re-measure in 6 months** (track culture change)
   - Denison re-survey to quantify improvement
   - Target: Adaptability 38 → 55 (moderate), Involvement 58 → 68 (good)

---

### Lessons Learned

**What worked**:
- Denison quantified problem (Adaptability = 38)
- Ethnography explained mechanisms (approval-seeking, fear, process, risk)
- Integration made recommendations specific and evidence-based

**What didn't**:
- 6 weeks felt rushed (would have preferred 8 weeks for more ethnographic depth)
- Ethnography focused on problem area (Adaptability) - didn't explore strengths as deeply

**Outcome**:
- All 4 recommendations implemented
- 6-month re-survey: Adaptability 38 → 52 (+14), Involvement 58 → 65 (+7)
- Anecdotal: Teams report feeling more empowered, speed of decision-making improved

---

## Common Patterns Across Examples

### Pattern 1: Match Methodology to Question Type

**Examples show**:
- **Decision question** (Example 1) → Market Research
- **Explanatory question** (Example 2) → Case Study
- **Literature question** (Example 3) → Evidence Synthesis
- **Exploratory + confirmatory** (Example 4) → Mixed Methods
- **Cultural diagnostic** (Example 5) → Organizational Culture

**Lesson**: Question type determines methodology (not arbitrary choice)

---

### Pattern 2: Time Constraints Drive Variant Selection

**Examples show**:
- 2 weeks available (Example 3) → REA (not full systematic review)
- 3 weeks (Example 1) → Market Research (rapid, not multi-month)
- 12 weeks (Example 4) → Mixed Methods (sequential phases fit timeline)

**Lesson**: Methodology must fit timeline (practical variants exist for speed)

---

### Pattern 3: Triangulation Increases Confidence

**All examples used multiple evidence sources**:
- Example 1: Competitive + customer + reviews
- Example 2: Interviews + documents + archival + observations
- Example 3: 18 academic papers across themes
- Example 4: Qual themes → quant validation (method triangulation)
- Example 5: Survey scores → ethnographic depth

**Lesson**: Single source insufficient, multiple sources validate findings

---

### Pattern 4: Integration Produces Action

**All examples resulted in specific actions**:
- Example 1: BUILD feature (go/no-go decision)
- Example 2: 4 recommendations for future reorgs
- Example 3: Focus time + tooling investments
- Example 4: 5-factor collaboration model + instrument
- Example 5: 4 culture change interventions

**Lesson**: Research must be actionable (not just descriptive)

---

## Methodology Selection Quick Reference

**Use this to map your situation to examples**:

| Your Situation | Similar Example | Recommended Methodology |
|----------------|-----------------|-------------------------|
| Should we build/do X? | Example 1 | Market Research |
| Why did X happen? | Example 2 | Case Study (explanatory) |
| What does literature say? | Example 3 | Evidence Synthesis (REA if time-constrained) |
| Explore then measure | Example 4 | Mixed Methods (exploratory sequential) |
| What is our culture? | Example 5 | Organizational Culture (combined) |
| How does system/tool work? | - | Design Science Research |
| What are user needs? | - | UX Research |
| Compare multiple cases | - | Case Study (multiple cases) |

---

## Related Documentation

**Methodologies** (see individual methodology directories for detailed examples):
- [[design-science/examples]]
- [[ux-research/methods-catalog]]
- [[market-research/examples]]
- [[mixed-methods/examples]]
- [[case-study/examples]]
- [[organizational-culture/examples]]
- [[evidence-synthesis/examples]]

**Integration**:
- [[integration-patterns]] - How to combine methodologies

**Selection**:
- [[methodology-selection-wizard]] - Interactive wizard for choosing methodology

---

**Use these examples**: To understand how methodology choice maps to real research questions and contexts
