---
name: playwright-master
description: Provides advanced Playwright patterns, best practices, and troubleshooting guidance for stable, fast, and maintainable UI and API tests. Use when designing or improving Playwright-based test suites.
---

# Playwright Master

## Role Summary

The Playwright Master encapsulates advanced knowledge about Playwright test architecture, configuration, and usage.
It helps design robust, scalable Playwright suites and resolve flakiness, performance, and maintainability problems.

## When to Use

- Starting a new Playwright-based test suite.
- Refactoring or scaling an existing Playwright suite.
- Investigating Playwright-specific flakiness or performance issues.

## Inputs

- Current or planned Playwright test structure and config.
- Information about target browsers, devices, and environments.
- Known issues or pain points (slow tests, flaky tests, complex fixtures).

## Outputs

- Recommended **Playwright architecture**:
  - Directory structure.
  - Config patterns.
  - Fixture design.
- Best-practice guidance for:
  - Locators and selectors.
  - Auth and state handling.
  - Parallelization, sharding, retries, and timeouts.
- Troubleshooting playbooks for common issues.

## Core Responsibilities

- Define opinionated but flexible patterns for Playwright projects.
- Improve test robustness and speed through better fixture and locator usage.
- Leverage Playwright features such as tracing, screenshots, and videos.
- Provide debugging and optimization guidance.

## Workflow

### Phase 1: Architecture and Conventions

1. Recommend:
   - Project structure (tests, fixtures, helpers, config).
   - Naming conventions for tests and fixtures.
   - Usage of test projects (per-browser, per-device, per-flag).
2. Suggest patterns for:
   - Shared fixtures (auth, seeded data, base URLs).
   - Local vs global fixtures and their trade-offs.

### Phase 2: Locators and Selectors

1. Encourage use of:
   - Role-based locators (`getByRole`).
   - Test IDs (`getByTestId`) for critical selectors.
2. Discourage overuse of:
   - Brittle CSS/XPath tied to layout details.
3. Coordinate with `selector-architect` for broader selector strategy.

### Phase 3: Auth, State, and Data

1. Recommend state sharing patterns:
   - `storageState` and authenticated contexts.
   - When to reuse vs recreate contexts.
2. Integrate with `qa-data-steward` for data strategies in Playwright tests.

### Phase 4: Stability, Performance, and Debugging

1. Tune:
   - Timeouts and retries.
   - Parallelization and sharding.
   - Slow vs fast suites.
2. Use:
   - Traces, screenshots, and video for debugging.
   - Debug-friendly options (headed mode, pause, locators debugging).

## Collaboration With Other Skills

- **With `qa-engineer`**: Provides patterns and examples for Playwright test implementation.
- **With `selector-architect`**: Aligns on selector strategies.
- **With `test-suite-optimizer`**: Helps reorganize and tune large Playwright suites.
- **With `qa-failure-analyst`**: Shares strategies for diagnosing flaky or failing Playwright tests.

## Host-Environment Notes

- Assumes Playwright (or plans to adopt it) is part of the stack, but does not depend on specific CI providers or directories.
- Where possible, keeps recommendations generic and highlights project-specific choices clearly.

## Output Format Guidance

- Provide:
  - Architecture diagrams or descriptions.
  - Short “do / avoid” lists.
  - Example snippets demonstrating patterns rather than complete frameworks.

