# Cross-Session Longitudinal Analysis

Compare multiple transcripts from the same engineer over time. Individual sessions may only show some phases; patterns across multiple sessions give a more reliable picture of an engineer's habits (see framework §4 Scope & Applicability — "Accumulation").

---

## Prompt

```
@evaluation-framework

Perform a cross-session longitudinal analysis on the following agent transcripts from the same engineer.

### Engineer

- **Name**: [Name]
- **Role**: [Title / Level]
- **Analysis period**: [Start date] – [End date]

### Sessions

#### Session 1: [Task summary]
- Date: [YYYY-MM-DD]
- Type: [New feature / Bug fix / Refactor / Investigation / Other]

[Paste transcript or @file reference]

#### Session 2: [Task summary]
- Date: [YYYY-MM-DD]
- Type: [New feature / Bug fix / Refactor / Investigation / Other]

[Paste transcript or @file reference]

(Add more sessions — 3–5 across different task types recommended)

### Required output

1. **Engineer Profile**
   Overall behavioral characteristics derived from the full session set.

2. **Phase Coverage Consistency**
   - Which phases appear consistently? Which are consistently absent?
   - Trend over time — improvement, regression, or stable?
   - Weight phase importance relative to task complexity (per framework §4 Scope & Applicability — "Context matters").

3. **Phase 3 Tier Distribution Trend**
   - Per-session Tier 1 / Tier 2 / Tier 3 breakdown
   - Dominant tier across sessions
   - Migration trend — is the engineer shifting from Reactive Correction toward Proactive Interrogation over time?

4. **Stable Patterns vs. Occasional Behaviors**
   - Strengths recurring across multiple sessions (reliable habits)
   - Gaps recurring across multiple sessions (systemic weaknesses)
   - One-off anomalies — positive or negative — tied to specific session context

5. **Task Type Impact**
   - Behavioral differences by task type (feature dev vs. bug fix vs. refactor vs. investigation)
   - How task complexity and novelty affect AI-native behavior quality
   - Whether the engineer appropriately scales planning effort to task scope (per framework Phase 2 — design uncertainty × execution scope)

6. **AI-Native Maturity Trajectory**
   - Position on the AI-assisted ↔ AI-native spectrum at start and end of the analysis period
   - Rate and direction of change
   - Most valuable next improvement direction

7. **Personalized Training Recommendations**
   - 2–3 priority recommendations based on stable patterns, not one-off behaviors
   - Each backed by specific session evidence
   - Mapped to framework training implications (spec-driven development, planning discipline, critical review techniques, persistent knowledge management, etc.)
```

---

## Instructions

1. Collect 3–5 transcripts from the same engineer, ideally spanning different task types and a meaningful time period
2. Arrange chronologically
3. Fill in the template and submit to Cursor Agent
4. Cross-session analysis surfaces long-term habits invisible in any single transcript
