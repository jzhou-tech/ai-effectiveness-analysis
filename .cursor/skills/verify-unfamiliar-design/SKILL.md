---
name: verify-unfamiliar-design
description: >-
  Guide the engineer through verifying AI-generated solution designs when they
  lack domain knowledge or codebase familiarity. Use when the user says they are
  unfamiliar with the system, asks how to verify an AI plan, questions whether
  an AI design is correct, or starts work on an unfamiliar requirement or
  codebase.
---

# Verify Unfamiliar Design

When the engineer lacks domain knowledge or codebase familiarity, use the 4-Anchor verification method to build confidence in AI-generated designs incrementally.

This skill operationalizes Phase 3 (Orchestration / Verification / Critical Engagement) of the [AI-Native Engineering Effectiveness Evaluation Framework](../../.cursor/rules/evaluation-framework.mdc).

## When to Activate

- Engineer states they are unfamiliar with the domain, requirement, or codebase
- Engineer asks how to verify an AI-generated plan or design
- Engineer is starting a new feature in an unfamiliar area
- Engineer questions the correctness of AI output but doesn't know how to check it

## Step 1: Assess Available Anchors

Before proposing any design, identify which independent verification sources exist:

| Anchor | What to look for | If missing |
|--------|-----------------|------------|
| **1 — Existing implementation** | Closest similar feature in the codebase | Find closest *pattern* (any API with similar shape: aggregation, export, comparison) |
| **2 — Actual data** | Dev/staging DB access, real data to query | Seed test records with known values; manually compute expected results |
| **3 — Other teams' artifacts** | DE pipelines, FE components, QA tests for the same domain | Create your own verification data; add extra multi-perspective review round |
| **4 — Design spec** | Figma, PRD, architecture decision records | Write a mini-spec: "Given X, user should see Y" — use that as the anchor |

**Tell the engineer which anchors are available and which need compensation.**

## Step 2: Orient Before Designing

1. Ask the engineer about their context level: "What do you already know about this domain and codebase?"
2. Find the closest existing implementation. Analyze its architecture, data flow, patterns, and edge case handling.
3. Establish source priority: Design spec = UI truth, DB = data truth, PRD = intent context.
4. Present the orientation findings to the engineer before proposing any design.

## Step 3: Design with Validation Gates

Propose a plan, then immediately cross-check against all available anchors:

- **Anchor 1 check**: Does the plan's architecture match established codebase patterns?
- **Anchor 2 check**: Do data assumptions hold against actual dev/staging data? Generate verification SQL if possible.
- **Anchor 3 check**: Does calculation/business logic match what other teams independently built?
- **Anchor 4 check**: Does every UI element trace back to a concrete data source (UI -> API -> SQL -> DB)?

### Mandatory: Legacy Bug Trap Check

For any logic referenced from existing code, explicitly verify:

> "The existing implementation does [X] at this point. Is this actually correct from first principles, or could it be a legacy bug? Cross-check against actual data (Anchor 2) and other teams' implementations (Anchor 3)."

**Never assume existing code is correct.** Use existing code for structural patterns (architecture, data flow, naming) — not for logic correctness.

### Anchor Conflict Resolution

When sources disagree, apply this priority:

1. **Actual data (DB) > documentation** — data is what runs in production
2. **Design spec > existing code** — code may have legacy bugs; design represents intent
3. **Unresolvable conflict** -> flag for human escalation

## Step 4: Implement with Continuous Verification

- Build in small increments. After each increment, verify against real data.
- When discrepancies arise, trace whether the issue is in the new code, the AI's design, or the referenced existing code.
- Run multi-perspective review: ask the engineer to consider the design as a frontend consumer, as a QA engineer, and as a DBA.

## Step 5: Check Stopping Criteria

Verification is sufficient to proceed when ALL of the following are true:

- [ ] Every UI-visible metric has a traceable audit trail (UI -> API -> SQL -> DB)
- [ ] At least one real-data validation per calculation path
- [ ] No unresolved conflicts between anchors
- [ ] For any missing anchor, at least one extra multi-perspective review round was done
- [ ] For any logic copied from existing code, the legacy bug trap check was performed

**If any criterion is not met, do not approve the design. Identify the gap and address it.**

## When to Recommend Human Escalation

Stop AI-only verification and recommend involving a domain expert when:

- Anchor conflicts remain unresolved after 2 rounds of analysis
- The feature touches regulatory, security, or financial logic
- Architectural decisions have long-term consequences (data model, cross-service boundaries)
- The engineer cannot answer questions about the design's key decisions (the "grill-me" test: ask probing questions about the design — if the engineer can't answer, they need more context from a human)

## Adapting to Feature Type

The anchors map differently depending on the type of work:

| Feature type | Anchor 1 | Anchor 2 | Anchor 3 | Anchor 4 |
|---|---|---|---|---|
| Data / API | Closest existing API | Dev/staging DB query | DE pipeline SQL | Figma metrics |
| UI interaction | Similar UI component | Browser dev tools / rendered behavior | Design system docs | Figma interaction spec |
| Infrastructure | Existing deploy configs | Actual cloud resource state | DevOps runbooks | Architecture decision records |
| Auth / permissions | Existing RBAC impl | Live permission matrix | Security team docs | PRD access requirements |

## Output: Confidence Artifacts

At the end of verification, produce:

1. **Anchor coverage summary**: which anchors were checked, which were missing, how gaps were compensated
2. **Calculation audit trail** (for data features): UI metric -> API field -> SQL -> DB column -> source system
3. **Unresolved items**: anything flagged for human review, with context for the reviewer
