# Cross-Session Analysis Template

Perform a longitudinal comparison across multiple transcripts from the same engineer to identify behavioral patterns and trends.

---

## Prompt

```
@evaluation-framework

Please perform a cross-session aggregation analysis on the following agent transcripts from the same engineer.

### Engineer Information

- **Name**: [Name]
- **Role**: [Title / Role]
- **Analysis Period**: [Start date] – [End date]

### Transcript List

#### Session 1: [Task summary]
- Date: [YYYY-MM-DD]
- Type: [New feature / Bug fix / Refactor / Other]

[Paste transcript or use @file to reference]

#### Session 2: [Task summary]
- Date: [YYYY-MM-DD]
- Type: [New feature / Bug fix / Refactor / Other]

[Paste transcript or use @file to reference]

#### Session N: ...

(Add more sessions as needed)

### Analysis Requirements

Please produce a cross-session aggregation report:

1. **Engineer Profile** — Overall behavioral characteristics based on all sessions

2. **Phase Coverage Consistency**
   - Which Phases are consistently present across all sessions?
   - Which Phases are consistently skipped?
   - Is there a trend of improvement or regression over time?

3. **Phase 3 Tier Distribution Trend**
   - Tier 1/2/3 ratios for each session
   - Overall distribution pattern: which Tier dominates?
   - Is there a migration trend from Tier 3 toward Tier 1?

4. **Stable Patterns vs. Occasional Behaviors**
   - Strengths that recur across multiple sessions
   - Gaps that recur across multiple sessions
   - Anomalies (positive or negative) that appear only in specific sessions

5. **Task Type Impact**
   - Behavioral differences across task types (feature development vs. bug fix vs. refactor)
   - How task complexity affects the engineer's AI-native behavior quality

6. **AI-Native Maturity Trajectory**
   - Maturity trend over the analysis period
   - Current position on the AI-assisted ↔ AI-native spectrum
   - Most valuable next improvement direction

7. **Personalized Training Recommendations**
   - 2–3 priority training suggestions based on stable patterns (not one-off behaviors)
   - Each recommendation backed by specific session evidence
```

---

## Instructions

1. Collect multiple transcripts from the same engineer over a period of time (3–5 recommended, across different task types)
2. Arrange them in chronological order
3. Fill in the template above and submit to Cursor Agent
4. Cross-session analysis reveals long-term patterns invisible in single-transcript reviews
