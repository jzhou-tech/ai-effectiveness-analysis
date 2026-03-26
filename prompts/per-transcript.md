# Single Transcript Analysis

Use this template in a Cursor Agent conversation. Reference the `@evaluation-framework` rule before submitting.

---

## Prompt

```
@evaluation-framework

Analyze the following agent transcript against the AI-Native Engineering Effectiveness Evaluation Framework.

### Session metadata

- **Engineer**: [Name]
- **Project / Task**: [What was being built or investigated]
- **Date**: [YYYY-MM-DD]
- **Session type**: [New feature / Bug fix / Refactor / Investigation / Other]

### Transcript

[Paste the full agent transcript, or use @file to reference an exported Markdown file]

### Required output

Produce a structured evaluation covering:

1. **Session Overview**
   - Engineer, project, date, session type, complexity
   - Brief summary of what was accomplished

2. **Phase-by-Phase Findings**
   For each of the four phases (Requirement Clarification & Spec Definition, Planning & Task Decomposition, Orchestration/Verification/Critical Engagement, Continuous Alignment/Adaptation/Knowledge Capture):
   - Evidence observed — quote specific transcript excerpts
   - Assessment: Strong / Adequate / Weak / Not Applicable
   - Specific gaps identified, mapped to the framework's "Common gaps" list
   - Training implications per phase
   - Account for session scope — not every session requires all four phases

3. **Phase 3 Tier Distribution**
   - Approximate percentage: Tier 1 (Proactive Interrogation) / Tier 2 (Directed Verification Design) / Tier 3 (Reactive Correction)
   - Representative examples from each observed tier
   - Overall characterization — where does the engineer concentrate their verification effort?

4. **Pattern Summary**
   - Top strengths with evidence (behaviors worth promoting)
   - Top gaps with evidence (behaviors needing training)
   - Priority training recommendations, referencing specific framework training implications

5. **AI-Native Maturity Assessment**
   - Position on the AI-assisted ↔ AI-native spectrum
   - Specific behaviors that indicate current position
   - What "next level" looks like for this engineer
```

---

## Instructions

1. Export the target transcript using `export_new.py export` from [cursor-chat-export](https://github.com/jzhou-tech/cursor-chat-export)
2. Open this project in Cursor
3. Start a new Agent conversation, copy the prompt above, and fill in the metadata
4. Reference the exported Markdown via `@file`, or paste content directly
5. The AI will produce a structured evaluation following the framework's output format
