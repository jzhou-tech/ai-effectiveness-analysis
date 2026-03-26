# Single Transcript Analysis Template

Use this template in a Cursor Agent conversation. Make sure to reference the `@evaluation-framework` rule.

---

## Prompt

```
@evaluation-framework

Please analyze the following agent transcript per the AI-Native Engineering Effectiveness Evaluation Framework.

### Basic Information

- **Engineer**: [Name]
- **Project / Task**: [Project name and specific task description]
- **Date**: [YYYY-MM-DD]
- **Session Type**: [New feature / Bug fix / Refactor / Technical investigation / Other]

### Transcript

[Paste the full agent transcript here, or use @file to reference an exported Markdown file]

### Analysis Requirements

Please produce an evaluation report with the following structure:

1. **Session Overview** — Summarize the session content, type, and complexity
2. **Phase-by-Phase Findings** — Analyze each phase, citing transcript excerpts as evidence
3. **Phase 3 Tier Distribution** — Provide approximate Tier 1/2/3 ratios with representative examples
4. **Pattern Summary** — Identify core strengths and gaps
5. **AI-Native Maturity Assessment** — Place the engineer on the AI-assisted ↔ AI-native spectrum

For each finding:
- Cite specific dialogue excerpts from the transcript as evidence
- Distinguish between "strengths (worth promoting)" and "gaps (training needed)"
- Provide concrete, actionable improvement recommendations
```

---

## Instructions

1. Export the target transcript using `export_new.py export` from the [cursor-chat-export](https://github.com/jzhou-tech/cursor-chat-export) project
2. Open this project in Cursor
3. Start a new Agent conversation, copy the prompt above, and fill in the details
4. Reference the exported Markdown file via `@file`, or paste the content directly
5. The AI will produce a structured evaluation report following the framework
