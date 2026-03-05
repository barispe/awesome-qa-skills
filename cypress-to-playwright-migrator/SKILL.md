---
name: cypress-to-playwright-migrator
description: Guides systematic migration of Cypress test suites to Playwright, mapping patterns, selectors, and helpers while preserving behavior and minimizing flakiness. Use when moving an existing Cypress-based UI test suite to Playwright.
---

# Cypress to Playwright Migrator

## Role Summary

The Cypress to Playwright Migrator provides patterns and workflows for porting tests from Cypress to Playwright.
It focuses on preserving behavior, improving robustness where possible, and creating a repeatable migration approach instead of ad-hoc rewrites.

## When to Use

- You have an existing Cypress test suite and want to standardize on Playwright.
- You are incrementally migrating tests while both frameworks coexist.
- You need guidance on 1:1 and non-1:1 pattern mapping between Cypress and Playwright.

## Inputs

- Overview of current Cypress usage (commands, custom commands, plugins, patterns).
- Representative Cypress test files (including network stubs, fixtures, auth patterns).
- Target Playwright setup (test runner, config, project structure) if it exists.

## Outputs

- A **migration strategy** (by feature, suite, or component).
- Pattern mappings (Cypress → Playwright) for:
  - Locators and selectors.
  - Network stubbing and fixtures.
  - Custom commands and shared helpers.
- Per-test or per-suite **migration guides** and example converted tests.

## Core Responsibilities

- Identify core Cypress patterns in the current suite.
- Provide Playwright equivalents and highlight differences in behavior.
- Recommend an incremental migration plan with safe coexistence of both frameworks.
- Surface risks and opportunities to improve robustness during migration.

## Workflow

### Phase 1: Inventory and Patterns

1. Identify common Cypress usage:
   - `cy.get`, `cy.contains`, aliasing, and chains.
   - `cy.intercept`, fixtures, network stubbing.
   - Custom commands (`Cypress.Commands.add`).
   - Use of `before`, `beforeEach`, and global setup.
2. Categorize tests:
   - Simple UI flows.
   - Heavy network stubbing.
   - Auth-intensive or stateful flows.

### Phase 2: Mapping to Playwright

1. Define pattern mappings such as:
   - Element selection: `cy.get('[data-test=foo]')` → `page.getByTestId('foo')` (or equivalent locator).
   - Network intercepts: `cy.intercept` → Playwright route handlers or mocks.
   - Fixtures: Cypress fixtures → Playwright test fixtures or helper modules.
2. Note behavioral differences:
   - Implicit retries vs explicit waits.
   - Command queue vs explicit `await`.
   - Test isolation and browser/context lifecycle.

### Phase 3: Migration Plan

1. Choose migration order:
   - High-value, low-risk tests first (e.g., core smoke flows).
   - Areas with heavy Cypress-specific features later.
2. Decide coexistence pattern:
   - Separate directories by framework.
   - Clear naming or tagging conventions.

### Phase 4: Example Conversions and Validation

1. For each test or group of tests:
   - Outline “before” (Cypress) and “after” (Playwright) structures.
   - Ensure equivalent coverage and oracles.
2. Suggest validation steps:
   - Run both versions in parallel temporarily.
   - Compare failure modes and flakiness.

## Collaboration With Other Skills

- **With `selector-architect`**: Improve selectors during migration for long-term stability.
- **With `qa-engineer`**: Implement specific converted tests and helpers.
- **With `qa-critic`**: Review migrated tests for robustness and coverage.
- **With `test-suite-optimizer`**: Decide which Cypress tests should be migrated, re-scoped, or retired.

## Host-Environment Notes

- Does not assume specific directory layouts or tooling beyond Cypress and Playwright test frameworks.
- If code-editing tools are available, can output suggested new Playwright test files and modifications in place of Cypress tests.

## Output Format Guidance

- Use side-by-side or stepwise comparisons when showing migrations.
- Capture reusable mapping tables (Cypress API → Playwright API) for your project’s conventions.

