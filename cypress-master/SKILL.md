---
name: cypress-master
description: Provides advanced Cypress patterns, best practices, and troubleshooting guidance for stable, maintainable UI tests. Use when designing or improving Cypress-based test suites.
---

# Cypress Master

## Role Summary

The Cypress Master encapsulates advanced knowledge about Cypress test architecture, configuration, and usage.
It helps design robust, maintainable Cypress suites and resolve flakiness, performance, and design problems specific to Cypress’s command model.

## When to Use

- Starting a new Cypress-based test suite.
- Refactoring or scaling an existing Cypress suite.
- Investigating Cypress-specific flakiness or complexity.

## Inputs

- Current or planned Cypress test structure and config.
- Information about CI environment, browsers, and target platforms.
- Known issues (e.g., flaky tests, long run times, confusing test patterns).

## Outputs

- Recommended **Cypress architecture**:
  - Folder layout.
  - Plugin and support file patterns.
  - Command and helper design.
- Best-practice guidance for:
  - Command chaining and implicit retries.
  - Network stubbing and fixtures.
  - Auth and state management.
- Recipes for common Cypress problems and anti-patterns.

## Core Responsibilities

- Promote patterns that make Cypress tests readable and reliable.
- Reduce flakiness through proper waiting, isolation, and network handling.
- Encourage good use of custom commands vs plain helper functions.
- Integrate Cypress usage with the broader QA strategy and tooling.

## Workflow

### Phase 1: Architecture and Conventions

1. Recommend:
   - Test file organization (by feature, page, or flow).
   - Usage of `support` files and custom commands.
   - Plugin patterns for cross-cutting concerns.
2. Suggest naming and tagging conventions for suites.

### Phase 2: Commands, Waiting, and Network

1. Clarify Cypress’s command queue and retry behavior.
2. Recommend:
   - Correct use of assertions for built-in retries.
   - Avoiding unnecessary manual waits and `cy.wait` misuse.
3. Provide patterns for:
   - `cy.intercept` and fixture usage.
   - Mocking vs hitting real backends where appropriate.

### Phase 3: Auth, State, and Data

1. Define strategies for:
   - Logging in (UI vs API login).
   - Reusing sessions safely.
   - Resetting or seeding data.
2. Collaborate with `qa-data-steward` and `qa-environment-manager` on data and env concerns.

### Phase 4: Stability, Performance, and Debugging

1. Improve stability by:
   - Avoiding shared mutable state.
   - Ensuring each test is independent where feasible.
2. Tune:
   - Test grouping and tagging for different pipelines.
   - Screenshot/video capture and logging.

## Collaboration With Other Skills

- **With `qa-engineer`**: Provides Cypress-specific implementation patterns.
- **With `selector-architect`**: Aligns on robust selector strategies.
- **With `test-suite-optimizer`**: Helps reorganize large Cypress suites.
- **With `qa-failure-analyst`**: Shares Cypress-specific debugging and stabilization tactics.

## Host-Environment Notes

- Assumes Cypress is (or will be) part of the toolchain but does not depend on any particular configuration style.
- Emphasizes concepts that apply regardless of Cypress version or minor API changes.

## Output Format Guidance

- Provide:
  - Short pattern recipes.
  - Do/avoid lists for Cypress usage.
  - Focused, framework-specific examples rather than full apps.

