---
name: ci-pipeline-qa
description: Designs how tests run in CI/CD pipelines, deciding which suites run when and with what gating, to balance speed, feedback quality, and risk. Use when integrating or optimizing tests in CI.
---

# CI Pipeline QA

## Role Summary

The CI Pipeline QA skill focuses on integrating tests into continuous integration and delivery pipelines.
It balances fast feedback, reliability, and risk coverage by deciding which tests run at which stages and under what conditions.

## When to Use

- Introducing automated tests into CI/CD for the first time.
- Reworking pipelines that are slow, flaky, or block developers too often.
- Adding new test types (e.g., E2E, performance, contract tests) into existing pipelines.

## Inputs

- Current CI/CD workflows and stages.
- Existing test suites and their characteristics (duration, flakiness, coverage).
- Release cadence, risk tolerance, and team preferences.

## Outputs

- A **test execution matrix**:
  - Which suites run on PR, on merge, nightly, or pre-release.
  - Gating rules (what blocks merges or releases).
- Recommendations for:
  - Parallelization, sharding, and caching.
  - Handling flaky tests (quarantine, retries, non-blocking modes).

## Core Responsibilities

- Align test execution with risk and cost constraints.
- Avoid overloading PRs with long or noisy tests.
- Ensure critical regressions are caught before release.
- Provide predictable, actionable feedback to developers.

## Workflow

### Phase 1: Pipeline and Suite Mapping

1. Map existing pipelines:
   - Trigger points (PR, push to main, nightly, release).
   - Stages and jobs.
2. Overlay test suites and their:
   - Durations.
   - Failure rates.
   - Coverage roles (smoke, regression, etc.).

### Phase 2: Execution Strategy

1. Decide:
   - Minimal checks for PR (fast, high-signal tests).
   - Deeper checks for merge to main and nightly runs.
   - Pre-release or pre-deploy gates.
2. Incorporate:
   - Contract tests.
   - Performance and visual tests, where appropriate.

### Phase 3: Flakiness and Feedback Handling

1. Integrate with `qa-failure-analyst` and `test-suite-optimizer` to:
   - Identify flaky tests and decide how to treat them.
   - Reduce noise over time.
2. Recommend:
   - Retry strategies.
   - Quarantine patterns.
   - Reporting mechanisms in CI.

### Phase 4: Documentation and Evolution

1. Document:
   - Which tests run where.
   - What failures mean and who responds.
2. Periodically revisit the strategy as suites and pipelines evolve.

## Collaboration With Other Skills

- **With `test-suite-optimizer`**: Aligns suite structure with pipeline stages.
- **With `qa-reporter`**: Surfaces CI testing status and trends.
- **With `api-contract-testing-architect`** and **`visual-regression-architect`**: Places their tests in appropriate pipeline stages.

## Host-Environment Notes

- Agnostic to CI platforms (GitHub Actions, GitLab CI, others); focuses on conceptual workflows and matrices.
- Does not require direct access to pipeline configuration files but can suggest conceptual changes for teams to implement.

## Output Format Guidance

- Provide:
  - A simple matrix or table mapping suites to pipeline stages.
  - Bullet-point rules for gating and flakiness handling.

