---
name: playwright-to-cypress-migrator
description: Guides migration of Playwright test suites to Cypress, mapping fixtures, locators, and helpers while preserving behavior and minimizing flakiness. Use when moving an existing Playwright-based UI test suite to Cypress.
---

# Playwright to Cypress Migrator

## Role Summary

The Playwright to Cypress Migrator provides patterns and workflows for porting tests from Playwright to Cypress.
It focuses on preserving behavior while adapting to Cypress’s command queue, retry model, and ecosystem.

## When to Use

- You have an existing Playwright suite and must standardize on Cypress.
- You are incrementally migrating tests while both frameworks coexist.
- You need clear guidance on Playwright → Cypress pattern mapping.

## Inputs

- Overview of current Playwright usage (fixtures, locators, tracing, network mocking).
- Representative Playwright test files, including auth and shared helpers.
- Target Cypress setup (folder structure, plugins, config) if it exists.

## Outputs

- A **migration strategy** specifying which tests move first and how.
- Pattern mappings (Playwright → Cypress) for:
  - Locators and selectors.
  - Fixtures and shared setup.
  - Network mocking and test isolation patterns.
- Example converted tests with notes on differences and trade-offs.

## Core Responsibilities

- Identify how Playwright fixtures and patterns are used.
- Provide Cypress equivalents and highlight behavior differences.
- Recommend an incremental migration approach, including safe coexistence.
- Surface constraints where 1:1 feature parity is not possible.

## Workflow

### Phase 1: Inventory and Patterns

1. Identify core Playwright usages:
   - Test fixtures (`test.beforeEach`, fixtures in config).
   - Locators (`page.getByRole`, `page.locator`).
   - Network mocking (`page.route`, context-level intercepts).
   - Tracing, screenshots, and videos.
2. Group tests by complexity and dependencies.

### Phase 2: Mapping to Cypress

1. Define pattern mappings such as:
   - Locators: Playwright locator strategies → Cypress `cy.get`, `cy.contains`, and data-test-id conventions.
   - Fixtures: Playwright test fixtures → Cypress `before`, `beforeEach`, or custom commands/helpers.
   - Network mocking: Playwright routing → `cy.intercept` and fixtures.
2. Note key differences:
   - Cypress command queue and implicit retries.
   - Single-browser model vs Playwright’s multi-context patterns.

### Phase 3: Migration Plan

1. Prioritize:
   - Critical smoke flows.
   - Tests that use simpler Playwright features first.
2. Define coexistence:
   - Directory layout for Playwright vs Cypress tests.
   - Clear naming conventions to avoid confusion.

### Phase 4: Example Conversions and Validation

1. For each migration sample:
   - Show Playwright structure.
   - Show the Cypress version with equivalent assertions and flows.
2. Suggest validation:
   - Temporarily run both versions.
   - Track differences in failure patterns or flakiness.

## Collaboration With Other Skills

- **With `selector-architect`**: Revisit selector strategy while porting tests.
- **With `qa-engineer`**: Implement Cypress tests and helpers.
- **With `qa-critic`**: Review migrated tests for quality and robustness.
- **With `test-suite-optimizer`**: Decide which Playwright tests to migrate vs retire.

## Host-Environment Notes

- Assumes only that both Cypress and Playwright are (or were) part of the toolchain; does not assume specific configs.
- If tooling is available, can generate suggested Cypress test code to replace or mirror Playwright tests.

## Output Format Guidance

- Provide mapping tables for your project’s main Playwright patterns and their Cypress equivalents.
- Use short, focused examples to illustrate migrations rather than monolithic rewrites.

