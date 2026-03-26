# Team Aggregation Template

Aggregate individual engineer analyses into team-level effectiveness insights and training plans.

---

## Prompt

```
@evaluation-framework

Please produce a team-level summary report based on the following individual engineer analyses.

### Team Information

- **Team Name**: [Team name]
- **Team Size**: [Number of members]
- **Analysis Period**: [Start date] – [End date]
- **Coverage**: [X engineers analyzed, Y total sessions]

### Individual Analysis Summaries

#### Engineer 1: [Name]
- Role: [Title]
- Sessions analyzed: [N]
- Phase coverage: [Which Phases are strong / weak]
- Tier distribution: [Tier 1: X% / Tier 2: Y% / Tier 3: Z%]
- Core strengths: [Brief summary]
- Core gaps: [Brief summary]
- AI-Native maturity: [AI-assisted / Transitioning / AI-native]

#### Engineer 2: [Name]
...

(Add all analyzed engineers)

### Analysis Requirements

Please produce a team summary report:

1. **Team AI-Native Maturity Overview**
   - Distribution of team members on the AI-assisted ↔ AI-native spectrum
   - Overall team maturity level assessment

2. **Phase-Level Team Patterns**
   - Overall coverage of each Phase across the team
   - Team-wide strengths (Phases where most members perform well)
   - Team-wide gaps (Phases where most members are weak)

3. **Phase 3 Tier Team Distribution**
   - Team-wide Tier 1/2/3 behavior distribution
   - Tier distribution comparison: high-performing vs. developing engineers
   - Whether the team is generally stuck at a particular Tier

4. **Training Priority Matrix**
   - Ranked by impact scope (how many benefit) × improvement potential (gap size)
   - Top 3 priority training topics
   - Specific training content recommendations for each topic

5. **Best Practice Examples**
   - Outstanding behaviors from the team worth showcasing (with engineer and session references)
   - Recommendations for promoting these practices team-wide

6. **Action Plan**
   - Short-term (1–2 weeks): Quick wins that can be implemented immediately
   - Medium-term (1–2 months): Training and tooling improvements
   - Long-term (1 quarter): Culture and process changes
   - Tracking metrics: How to measure improvement
```

---

## Instructions

1. Complete individual-level analyses first using `per-transcript.md` and `cross-session.md`
2. Summarize each engineer's analysis results into the template above
3. Submit to Cursor Agent for team-level aggregation
4. The team summary is suitable for management reporting and training planning
