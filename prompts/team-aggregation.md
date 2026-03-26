# Team-Level Aggregation

Aggregate individual engineer analyses to surface systemic patterns and inform team-wide training. This template operationalizes the framework's "Applying Findings — At the team level" guidance.

---

## Prompt

```
@evaluation-framework

Produce a team-level summary report based on the individual analyses below.

### Team metadata

- **Team**: [Team name]
- **Size**: [Number of engineers]
- **Analysis period**: [Start date] – [End date]
- **Coverage**: [X engineers analyzed across Y total sessions]

### Individual summaries

#### [Engineer 1 name]
- Role: [Title]
- Sessions analyzed: [N]
- Phase coverage: [Strong / Weak per phase]
- Phase 3 Tier distribution: [T1: X% / T2: Y% / T3: Z%]
- Core strengths: [Brief]
- Core gaps: [Brief]
- AI-native maturity: [AI-assisted / Transitioning / AI-native (emerging) / AI-native (mature)]

#### [Engineer 2 name]
...

(Include all analyzed engineers)

### Required output

1. **Team AI-Native Maturity Distribution**
   - Spectrum distribution: how many engineers at each maturity level
   - Overall team maturity assessment
   - Comparison against AI-native development expectations

2. **Phase-Level Team Patterns**
   - Per-phase coverage across the team
   - Team-wide strengths — phases where most members perform well
   - Team-wide gaps — phases where most members are weak
   - Apply the framework's diagnostic logic:
     - If most skip Phase 2 → team needs planning discipline training, not more AI tooling
     - If most operate at Tier 3 in Phase 3 → team needs critical thinking training, not more prompt engineering tips
     - If most treat AI as code generator → team needs AI-native workflow training (author → architect/orchestrator shift)

3. **Phase 3 Tier Team Distribution**
   - Aggregate Tier 1 / Tier 2 / Tier 3 distribution
   - High-performing vs. developing engineer comparison
   - Whether the team is systematically stuck at a particular tier

4. **Training Priority Matrix**
   - Ranked by impact scope (how many benefit) × improvement potential (gap size)
   - Top 3 priority training topics with specific content recommendations
   - Map each topic to framework training implications

5. **Best Practice Showcase**
   - Outstanding behaviors from specific engineers worth promoting team-wide
   - Concrete examples with engineer and session references
   - How to disseminate these practices (pairing, demos, rules/skills, etc.)

6. **Action Plan**
   - Short-term (1–2 weeks): Quick wins — Cursor rules, shared prompts, lightweight process changes
   - Medium-term (1–2 months): Structured training, tooling improvements, workflow changes
   - Long-term (1 quarter): Culture shifts, persistent knowledge practices, re-evaluation cadence
   - Tracking metrics: How to measure whether interventions shift transcript patterns (per framework "Over time" guidance)
```

---

## Instructions

1. Complete individual-level analyses first using `per-transcript.md` (and optionally `cross-session.md`)
2. Summarize each engineer's results into the template above
3. Submit to Cursor Agent for team-level aggregation
4. The output is designed for engineering management reporting and training planning
