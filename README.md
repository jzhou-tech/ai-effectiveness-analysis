# AI-Native Engineering Effectiveness Analysis

Analyze engineer–AI Agent interactions using the **AI-Native Engineering Effectiveness Evaluation Framework**. Identify effectiveness patterns, skill gaps, and training priorities.

## Workflow

```
cursor-chat-export (sister project)        this project
┌──────────────────────┐            ┌───────────────────────────┐
│  export_new.py       │            │  Cursor Agent +           │
│  Export transcripts   │──────────→│  evaluation-framework     │
│  to Markdown files   │            │  Analyze per framework    │
└──────────────────────┘            └───────────────────────────┘
```

1. Export agent transcripts via `python export_new.py export` in the [cursor-chat-export](https://github.com/jzhou-tech/cursor-chat-export) project
2. Place the exported Markdown files in this project (or reference them directly in Cursor)
3. Open this project in Cursor, start an Agent conversation, and reference the `evaluation-framework` rule
4. Use the prompt templates under `prompts/` to run the analysis

## Project Structure

```
ai-effectiveness-analysis/
├── .cursor/rules/
│   └── evaluation-framework.mdc   # Cursor Rule: full evaluation framework + AI role definition
├── prompts/
│   ├── per-transcript.md          # Single transcript analysis template
│   ├── cross-session.md           # Multi-session longitudinal comparison template
│   └── team-aggregation.md        # Team-level aggregation template
├── reports/                       # (git-ignored) Generated evaluation reports
└── README.md
```

## Framework Overview

The framework evaluates engineer behavior across four phases of AI-native development:

| Phase | Name | Focus |
|-------|------|-------|
| 1 | Requirement Clarification & Spec Definition | Upfront spec quality, constraint surfacing, ambiguity resolution |
| 2 | Planning & Task Decomposition | Task breakdown, dependency ordering, risk identification |
| 3 | Orchestration, Verification & Critical Engagement | Execution steering, output validation, critical questioning |
| 4 | Continuous Alignment, Adaptation & Knowledge Capture | Mid-course correction, knowledge persistence, retrospective capture |

Phase 3 further distinguishes three tiers of engagement:

- **Tier 1 — Proactive Interrogation**: Engineer proactively raises edge cases, integration risks, or architectural concerns that the AI has not surfaced (highest value)
- **Tier 2 — Directed Quality Assurance**: Engineer directs the AI to write tests, review code, or discuss trade-offs
- **Tier 3 — Reactive Correction**: Engineer corrects only when the AI produces obvious errors (baseline)

## Usage

### Analyze a Single Conversation

In a Cursor Agent chat:

```
@evaluation-framework

Please analyze the following transcript per the framework:
Engineer: Jane Doe
Project: User authentication refactor
Date: 2026-03-25

[paste or reference transcript content]
```

### Cross-Session Comparison

Use the `prompts/cross-session.md` template. Provide multiple transcripts from the same engineer to track growth over time.

### Team Aggregation

Use the `prompts/team-aggregation.md` template. Aggregate individual analyses to identify team-wide patterns and training needs.

## Related Projects

- [cursor-chat-export](https://github.com/jzhou-tech/cursor-chat-export) — CLI tools for exporting Cursor chat history to Markdown
