---
name: requirements-to-tests
description: Translates product requirements and acceptance criteria into testable scenarios and maintains traceability between requirements and tests. Use when turning specs into test coverage or auditing coverage of delivered features.
---

# Requirements to Tests

## Role Summary

The Requirements-to-Tests skill bridges product or stakeholder requirements with concrete test scenarios and coverage.
It ensures acceptance criteria are testable, produces a clear mapping from requirements to tests, and helps answer "did we test what was asked?"

## When to Use

- New features or stories with written acceptance criteria that need test scenarios.
- Audits or reviews of whether current tests cover stated requirements.
- Release or sign-off preparation when traceability is needed.

## Inputs

- Product requirements, user stories, or feature specs.
- Acceptance criteria (explicit or inferred).
- Existing test inventory or suite descriptions, if available.

## Outputs

- **Testable scenarios** derived from each requirement or acceptance criterion.
- A **traceability view**: requirement ID → acceptance criterion → test scenario(s) → test level/type.
- Gaps where requirements have no tests or tests have no linked requirement.
- Refined or clarified acceptance criteria when they are ambiguous or untestable.

## Core Responsibilities

- Turn vague or high-level requirements into concrete, testable conditions.
- Propose clear acceptance criteria when missing or unclear.
- Maintain a bidirectional view: requirements → tests and tests → requirements.
- Flag untestable or conflicting criteria for product/PM clarification.

## Workflow

### Phase 1: Ingest and Clarify Requirements

1. List each requirement, story, or feature and its stated acceptance criteria.
2. For each criterion, ask: Is it testable? Observable? Unambiguous?
3. Note missing criteria or ambiguities and suggest refinements.

### Phase 2: Derive Test Scenarios

1. For each acceptance criterion, derive one or more test scenarios:
   - Preconditions.
   - Actions or inputs.
   - Expected outcome (pass/fail condition).
2. Assign a suggested test level (unit, API, UI, integration, manual) where helpful.

### Phase 3: Build Traceability

1. Create a mapping table or list:
   - Requirement / story ID.
   - Acceptance criterion.
   - Test scenario(s).
   - Existing test(s) that cover it, or "to be implemented".
2. Identify:
   - Requirements with no tests.
   - Tests with no linked requirement (orphans or legacy).

### Phase 4: Gap Report and Handoff

1. Summarize coverage: X of Y requirements have at least one test.
2. Hand off test scenarios to `qa-strategist` or `qa-engineer` for prioritization and implementation.
3. Suggest how to keep traceability updated (e.g., tags, IDs in test names, or a lightweight matrix).

## Collaboration With Other Skills

- **With `qa-strategist`**: Feeds test scenarios into the backlog; strategist prioritizes by risk.
- **With `qa-engineer`**: Provides concrete scenarios to implement; engineer may refine for automation.
- **With `qa-critic`**: Uses traceability to validate that high-value requirements are covered.
- **With `release-sign-off`**: Supplies requirement coverage view for go/no-go decisions.

## Host-Environment Notes

- Does not depend on specific requirement or test management tools; works with plain text, docs, or structured formats.
- If the host has tools for requirements or test cases, can output in a format that fits (e.g., table, CSV, or structured snippets).

## Output Format Guidance

- Use **tables** for traceability: Requirement ID | Criterion | Test scenario | Test(s) | Status.
- Use **bullet lists** for derived scenarios under each criterion.
- Clearly separate **covered**, **not covered**, and **needs clarification** items.
