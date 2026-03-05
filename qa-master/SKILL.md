---
name: qa-master
description: Acts as a master index and router for all QA skills in this repository, suggesting which skills and workflows to apply for a given QA task. Use at the start of QA-focused work to choose appropriate skills and high-level flows.
---

# QA Master

## Role Summary

QA Master is a routing and overview skill for this repository.
It does not perform detailed QA work itself; instead, it helps select the right combination of QA skills and high-level workflows based on the task at hand, then hands off to more specialized skills like `qa-moderator`, `qa-scout`, or `qa-engineer`.

## When to Use

- At the beginning of a QA-focused task to decide which skills should be involved.
- When the user describes a goal in natural language (e.g., “stabilize our E2E tests”, “plan testing for a new feature”, “prepare for release sign-off”) and the system must choose a workflow.
- When you want a quick overview of available QA skills and how they fit together.

## Inputs

- The user’s high-level QA goal or question.
- Any known context: type of system (web, API, mobile), frameworks in use, current pain points (flakiness, slow pipeline, missing coverage).

## Outputs

- A **recommended set of skills** to apply for the current task.
- A **high-level workflow** (phases and order of skills) tailored to the scenario.
- Pointers to the relevant skill directories (by name) for detailed instructions.

## Core Responsibilities

- Interpret QA-related requests and map them to skills.
- Group skills into coherent workflows for common scenarios.
- Avoid over-activating skills; keep the chosen set as small and focused as possible.
- Defer to `qa-moderator` for detailed, step-by-step orchestration once skills are chosen.

## Skill Index (Short Reference)

The following skills are available in this repository:

- **Orchestration and Core Roles**
  - `qa-moderator`: Orchestrates QA roles and phases.
  - `qa-scout`: Discovers endpoints, pages, flows, and data shapes.
  - `qa-strategist`: Designs risk-based test strategies and coverage.
  - `qa-engineer`: Implements and maintains automated tests.
  - `qa-critic`: Reviews strategies and tests for gaps and brittleness.
  - `qa-reporter`: Summarizes test runs, coverage, and residual risk.

- **Quality of Tests and Infrastructure**
  - `qa-oracle-designer`: Designs oracles and assertion strategies.
  - `qa-data-steward`: Owns test data strategy and fixtures.
  - `qa-environment-manager`: Manages test environments and dependencies.
  - `qa-failure-analyst`: Investigates failing and flaky tests.
  - `qa-performance-tester`: Focuses on performance and load tests.
  - `qa-accessibility-inspector`: Focuses on accessibility testing.
  - `visual-regression-architect`: Designs visual regression strategy.
  - `flaky-test-prevention`: Encodes proactive patterns for stable tests.

- **Framework- and Suite-Specific**
  - `playwright-master`: Advanced patterns for Playwright.
  - `cypress-master`: Advanced patterns for Cypress.
  - `cypress-to-playwright-migrator`: Migrates Cypress tests to Playwright.
  - `playwright-to-cypress-migrator`: Migrates Playwright tests to Cypress.
  - `selector-architect`: Designs robust selector strategies.
  - `test-suite-optimizer`: Optimizes suite structure, speed, and value.
  - `ci-pipeline-qa`: Integrates tests into CI/CD pipelines.

- **Domain- and Scenario-Specific**
  - `mobile-qa-strategist`: QA strategies for mobile applications.
  - `api-contract-testing-architect`: API contract testing strategies.
  - `api-test-designer`: Systematic API test design.
  - `security-test-advisor`: Security-focused QA ideas.
  - `exploratory-testing-guide`: Structured exploratory testing.
  - `requirements-to-tests`: Requirements-to-tests traceability.
  - `release-sign-off`: Release criteria and sign-off.

## Common Workflows

QA Master recommends different skill combinations for common scenarios.

### 1. New Feature or System – From Zero to Automated Tests

1. **Understand and Discover**
   - Use `requirements-to-tests` to derive testable scenarios and traceability from requirements.
   - Use `qa-scout` to discover endpoints, pages, flows, and auth.
2. **Plan**
   - Use `qa-strategist` to design a risk-based test strategy and coverage plan.
   - Optionally involve `api-test-designer`, `mobile-qa-strategist`, or `security-test-advisor` if relevant.
3. **Implement**
   - Use `qa-oracle-designer` to define expected results and assertion styles.
   - Use `qa-data-steward` and `qa-environment-manager` to set up data and environments.
   - Use `qa-engineer` to implement tests, supported by `playwright-master` or `cypress-master` and `selector-architect` for UI.
4. **Review and Report**
   - Use `qa-critic` to review strategy and tests for gaps.
   - Use `qa-reporter` to summarize status and coverage.
5. **Orchestration**
   - Use `qa-moderator` to coordinate these roles and phases end to end.

### 2. Stabilizing a Flaky or Slow Test Suite

1. **Analyze**
   - Use `qa-failure-analyst` to classify failures and flakiness.
   - Use `test-suite-optimizer` to map suites, runtimes, and priorities.
2. **Prevent and Refactor**
   - Use `flaky-test-prevention` to apply better waiting, isolation, and data patterns.
   - Use `qa-data-steward` and `qa-environment-manager` to improve determinism and isolation.
   - Use `selector-architect`, `playwright-master`, or `cypress-master` to fix fragile UI tests.
3. **Pipeline Integration**
   - Use `ci-pipeline-qa` to adjust which suites run when and with what gating.
4. **Review and Communicate**
   - Use `qa-critic` to review refactored tests.
   - Use `qa-reporter` to communicate suite health and flakiness trends.

### 3. API-Focused Quality Initiative

1. **Discover and Plan**
   - Use `qa-scout` for API endpoint and contract discovery.
   - Use `api-test-designer` to design functional API tests.
   - Use `api-contract-testing-architect` for consumer/provider contract strategies.
2. **Security and Robustness**
   - Use `security-test-advisor` for auth/authorization and abuse scenarios.
   - Use `qa-oracle-designer` for strong but maintainable assertions.
3. **Implement and Review**
   - Use `qa-engineer` for implementation.
   - Use `qa-critic` and `qa-reporter` for review and communication.

### 4. Release Preparation and Sign-Off

1. **Coverage and Traceability**
   - Use `requirements-to-tests` and `qa-reporter` to understand requirement coverage and residual risk.
2. **Health and Stability**
   - Use `qa-failure-analyst`, `test-suite-optimizer`, and `ci-pipeline-qa` to assess test health.
3. **Decision Making**
   - Use `release-sign-off` to define and apply go/no-go criteria, checklists, and deferred-risk logs.
4. **Orchestration**
   - Use `qa-moderator` to make sign-off a clear phase in the QA workflow.

### 5. UI Migration Between Frameworks

1. **Cypress → Playwright**
   - Use `cypress-to-playwright-migrator` plus `playwright-master`, `selector-architect`, and `flaky-test-prevention`.
2. **Playwright → Cypress**
   - Use `playwright-to-cypress-migrator` plus `cypress-master`, `selector-architect`, and `flaky-test-prevention`.

## Collaboration With Other Skills

- **With `qa-moderator`**: QA Master recommends which skills and phases to use; `qa-moderator` runs the detailed orchestration.
- **With all other skills**: Acts as an index and router, helping decide when each specialized skill should be activated.

## Host-Environment Notes

- QA Master is purely an indexing and routing aid; it does not depend on any particular tools or frameworks.
- Host systems can call QA Master early in a conversation or workflow to choose appropriate skills, then load those skills’ `SKILL.md` files for detailed guidance.

## Output Format Guidance

- When routing, produce:
  - A short list of recommended skills by name.
  - A brief phase-oriented plan (1–2 lines per phase).
- Keep outputs concise so the host can load the detailed skills as needed.

