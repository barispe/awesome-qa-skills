---
name: flaky-test-prevention
description: Encodes patterns and practices to prevent flaky tests before they appear: waiting, isolation, data, timing, and environment. Use when designing new tests or refactoring existing ones for stability.
---

# Flaky Test Prevention

## Role Summary

The Flaky Test Prevention skill focuses on **proactive** practices that reduce the likelihood of flaky tests.
It complements `qa-failure-analyst` (which triages existing flakiness) by guiding test design and implementation toward stability from the start.

## When to Use

- Designing or implementing new tests (especially UI, integration, or E2E).
- Refactoring tests that are already flaky or suspected to become flaky.
- Reviewing test code or patterns for stability risks.
- Establishing team guidelines for writing stable tests.

## Inputs

- Test code or test design under review.
- Framework and environment context (Playwright, Cypress, API tests, CI vs local).
- Known failure modes from `qa-failure-analyst` or past flakiness reports.

## Outputs

- **Stability guidelines** tailored to the project's stack and test levels.
- **Concrete recommendations** for the tests at hand: what to change and why.
- **Anti-pattern checklist**: practices to avoid (e.g., fixed sleeps, shared mutable state).
- **Pattern suggestions**: recommended ways to wait, isolate data, and handle timing.

## Core Responsibilities

- Identify root causes of flakiness in design: timing, order dependence, shared state, environment, data.
- Recommend **waiting strategies**: assertion-based retries, explicit conditions, avoid fixed sleeps.
- Recommend **isolation**: per-test data, clean state, no cross-test dependencies.
- Recommend **environment and data** practices that reduce non-determinism.

## Workflow

### Phase 1: Stability Risk Scan

1. Review test structure for common flakiness drivers:
   - **Timing**: fixed delays, race conditions, animations, async without proper waiting.
   - **Order**: tests depending on execution order or shared state.
   - **Data**: shared DB/state, non-deterministic data, external services.
   - **Environment**: ports, filesystem, time zones, locale, network.
2. Note framework-specific risks (e.g., Cypress command queue, Playwright auto-waiting).

### Phase 2: Waiting and Synchronization

1. For UI and async flows:
   - Prefer waiting on **observable outcomes** (element visible, text present, network idle) over fixed timeouts.
   - Recommend framework-appropriate patterns (e.g., Playwright's built-in waiting, Cypress retry-until).
2. For API or integration tests:
   - Ensure responses and side effects are asserted before proceeding.
   - Avoid assuming immediate consistency (e.g., eventual consistency, caches).

### Phase 3: Isolation and Data

1. Encourage:
   - Independent test data per test or per worker.
   - Setup/teardown that leaves no residue for the next test.
   - No reliance on global state or "first run" assumptions.
2. Work with `qa-data-steward` and `qa-environment-manager` on data and env patterns that support isolation.

### Phase 4: Guidelines and Checklist

1. Produce a short **stability playbook** for the project:
   - Do: wait on conditions, isolate data, use deterministic IDs/dates.
   - Avoid: fixed sleeps, shared mutable state, order-dependent tests.
2. Provide a **review checklist** that `qa-engineer` or `qa-critic` can use when adding or changing tests.

## Collaboration With Other Skills

- **With `qa-engineer`**: Applies prevention patterns during test implementation.
- **With `qa-failure-analyst`**: Feeds failure patterns back into prevention guidelines; analyst triages, prevention encodes fixes.
- **With `qa-critic`**: Critic flags fragile tests; prevention suggests concrete refactors.
- **With `qa-data-steward`**: Aligns on deterministic, isolated data strategies.
- **With `qa-environment-manager`**: Aligns on environment stability and isolation.
- **With `playwright-master` and `cypress-master`**: Uses framework-specific best practices for waiting and isolation.

## Host-Environment Notes

- Tool-agnostic at the concept level; can be applied across unit, API, UI, and E2E tests.
- When framework context is known, can reference framework-specific APIs for waiting and isolation.

## Output Format Guidance

- Use **Do / Avoid** lists for quick scanning.
- For each recommendation, give a **short rationale** (e.g., "Avoid fixed sleep: timing varies across envs").
- Provide **code-level suggestions** or pseudocode where it helps (e.g., "Wait for element then assert" vs "Sleep 2s then assert").
