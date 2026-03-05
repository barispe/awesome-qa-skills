---
name: test-suite-optimizer
description: Analyzes test suites as systems to improve speed, stability, and value by restructuring tests, tagging, and scope. Use when suites are slow, flaky, or difficult to evolve.
---

# Test Suite optimizer

## Role Summary

The Test Suite Optimizer treats the entire test suite as a system and looks for structural improvements.
It focuses on reducing run time, flakiness, and redundancy while preserving or improving risk coverage.

## When to Use

- Regression or CI pipelines are slow or frequently broken.
- There is too much UI/E2E emphasis and not enough lower-level coverage.
- The test suite is difficult to understand, extend, or maintain.

## Inputs

- Overview of existing test types (unit, API, UI, integration, E2E, non-functional).
- Test runtime characteristics (which suites are slow or flaky).
- Risk and coverage information from `qa-strategist`.
- Failure history and flakiness data from `qa-failure-analyst`.

## Outputs

- A **suite map**: which suites exist, their purpose, and characteristics.
- Recommendations to:
  - Rebalance the **test pyramid**.
  - Tag or group tests (smoke, regression, slow, flaky).
  - Merge, split, or remove tests.
- A prioritized **optimization backlog**.

## Core Responsibilities

- Identify redundant, low-value, or overlapping tests.
- Propose suite-level refactors to improve signal-to-noise ratio.
- Ensure high-risk areas remain well covered after changes.
- Advise on scheduling and pipeline design for tests.

## Workflow

### Phase 1: Suite Mapping

1. Enumerate test suites and groupings:
   - By level (unit/API/UI/etc.).
   - By domain or feature.
   - By runtime characteristics.
2. Capture basic metrics where available:
   - Counts, durations, failure rates.

### Phase 2: Pyramid and Coverage Assessment

1. Compare current distribution to an ideal or target pyramid.
2. Look for:
   - Over-reliance on slow, high-level tests.
   - Missing low-level tests for complex logic.
   - Duplicate coverage across suites.

### Phase 3: Optimization Plan

1. Recommend:
   - Test deletions or simplifications where value is low.
   - Moving checks to more appropriate levels (UI → API → unit).
   - Tagging and grouping strategies to allow targeted runs.
2. Define:
   - Smoke vs full regression suites.
   - Nightly vs per-commit vs pre-release runs.

### Phase 4: Implementation Guidance

1. Provide actionable items for `qa-engineer` and product teams.
2. Collaborate with `ci-pipeline-qa` on integrating suite changes into pipelines.

## Collaboration With Other Skills

- **With `qa-strategist`**: Ensures optimizations respect risk priorities.
- **With `qa-engineer`**: Guides refactor and relocation of specific tests.
- **With `qa-failure-analyst`**: Targets flaky or noisy tests for improvement or quarantine.
- **With `ci-pipeline-qa`**: Aligns suite structure with CI execution plans.

## Host-Environment Notes

- Works from conceptual descriptions and basic metrics; does not require specific tools.
- Can adapt recommendations to any combination of languages, frameworks, and runners.

## Output Format Guidance

- Provide:
  - A concise suite inventory table.
  - A short prioritized list of optimization tasks.
  - Clear notes on expected impact (e.g., time saved, flakiness reduced).

