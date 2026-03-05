## Awesome QA Skills – Agentic QA Systems

This repository provides a **set of reusable QA role skills** for agentic AI systems (Cursor, other IDE agents, orchestration frameworks) that focus on **test automation and QA engineering workflows**.

Each skill is a small, self-contained directory with a `SKILL.md` file that defines:

- **What the role does** (its purpose and responsibilities).
- **When to use it** in the QA lifecycle.
- **Inputs and outputs** the role expects and produces.
- **Workflow and collaboration** with other QA roles.
- **Host-environment-agnostic notes** so it can work in almost any agentic system without special dependencies.

You can copy any subset of these skill folders into your own projects or global skill directory and load them as role definitions.

---

## Repository Structure

- `qa-moderator/`
- `qa-scout/`
- `qa-strategist/`
- `qa-engineer/`
- `qa-critic/`
- `qa-reporter/`
- `qa-oracle-designer/`
- `qa-data-steward/`
- `qa-environment-manager/`
- `qa-failure-analyst/`
- `qa-performance-tester/`
- `qa-accessibility-inspector/`
- `cypress-to-playwright-migrator/`
- `playwright-to-cypress-migrator/`
- `playwright-master/`
- `cypress-master/`
- `test-suite-optimizer/`
- `selector-architect/`
- `visual-regression-architect/`
- `mobile-qa-strategist/`
- `api-contract-testing-architect/`
- `security-test-advisor/`
- `ci-pipeline-qa/`
- `exploratory-testing-guide/`
- `requirements-to-tests/`
- `api-test-designer/`
- `release-sign-off/`
- `flaky-test-prevention/`

Each directory contains a single `SKILL.md` file describing that role.

There is **no required `.cursor` folder structure** here on purpose: you are free to place these skills wherever your system expects them (for example, `.cursor/skills/` in a Cursor project, or any custom path in another orchestrator).

---

## Skills Overview

### `qa-moderator` – QA Orchestrator

**Purpose**: Coordinates all QA roles and ensures the work progresses through sensible phases instead of looping or skipping steps.

**Key responsibilities**:
- Detect the current **mode** (exploration, strategy, implementation, review, reporting).
- Decide **which QA role** should act next and why.
- Maintain shared context about the system under test, risks, and current coverage.
- Drive **convergence** from high-level ideas to implemented tests and final reports.

**Typical use**:
- Always-on coordinator for multi-role QA workflows.
- Useful whenever you have more than one role active (scout, strategist, engineer, critic, reporter, specialists).

---

### `qa-scout` – System Explorer

**Purpose**: Discovers the **interaction surface** of the system under test: endpoints, pages, flows, data shapes, and auth behavior.

**Key responsibilities**:
- Map **API endpoints**: methods, paths, headers, auth, payload and response shapes.
- Map **pages/screens** and major user flows in UIs.
- Document **auth and state** (login, roles, sessions, tokens).
- Produce structured discovery artifacts for downstream roles.

**Typical use**:
- New or poorly documented systems and features.
- Any time you need to know *where* to hook tests in (API and UI).

---

### `qa-strategist` – Test Strategy and Coverage Planner

**Purpose**: Turns system understanding into a **risk-based test strategy** and coverage plan, deciding what to test where and at which level.

**Key responsibilities**:
- Identify and rank **risks** (impact × likelihood).
- Map risks to appropriate **test levels** (unit, API, UI, integration, E2E, non-functional).
- Define **coverage goals**: happy paths, edge cases, negative cases.
- Produce a prioritized **test backlog** for implementation.

**Typical use**:
- Greenfield or large new features that need a structured QA approach.
- When extending coverage to new areas and you want strategic focus, not just ad-hoc tests.

---

### `qa-engineer` – Test Automation Implementer

**Purpose**: Implements and maintains **automated tests, fixtures, helpers, and selectors** based on the strategy and discovery artifacts.

**Key responsibilities**:
- Turn test ideas into **concrete test code** in the project’s frameworks.
- Maintain **fixtures**, data factories, and helpers.
- Design and maintain **robust selectors** and patterns for UI tests.
- Define **execution instructions** (commands/config) for running tests.

**Typical use**:
- Whenever you need actual test code written or updated.
- Refactoring and stabilizing existing test suites as the product evolves.

---

### `qa-critic` – QA Reviewer and Gap Finder

**Purpose**: Reviews test strategies and test code, focusing on **gaps, weak spots, and brittleness** rather than just style.

**Key responsibilities**:
- Compare risks and requirements against current tests to find **coverage gaps**.
- Spot **brittle patterns** (fragile selectors, over-mocking, overly strict snapshots).
- Suggest **new edge cases and negative scenarios**.
- Prioritize critical issues vs suggestions vs nice-to-have improvements.

**Typical use**:
- After initial strategy or test implementation passes.
- As an always-on reviewer whenever tests or plans change.

---

### `qa-reporter` – Test Results and Coverage Communicator

**Purpose**: Produces **human-readable summaries** of what was tested, what passed/failed, coverage status, and residual risk.

**Key responsibilities**:
- Summarize **test activities and results** (by run, feature, or release).
- Describe **coverage and gaps** relative to strategy and risks.
- Explain **residual risks** in practical terms.
- Recommend **next steps** for engineering and QA.

**Typical use**:
- End-of-run or end-of-release reporting.
- Communicating QA status to engineers, PMs, and leadership.

---

### `qa-oracle-designer` – Assertions and Oracles Designer

**Purpose**: Defines **what it means for tests to pass**: expected results, invariants, and contracts, with assertions that are strong but not overly brittle.

**Key responsibilities**:
- Specify **oracles** per scenario: expected outputs, state changes, and invariants.
- Choose appropriate **assertion styles** (exact, partial, property-based, contract).
- Identify which fields are **required, constrained, or ignorable** in checks.
- Balance detection of real regressions vs resisting harmless changes.

**Typical use**:
- Complex business logic or integrations where correctness isn’t obvious.
- Situations where tests are currently either too weak or too fragile.

---

### `qa-data-steward` – Test Data Strategy Owner

**Purpose**: Owns **test data strategy**: how data is created, anonymized, reset, and shared, so tests are realistic, safe, and stable.

**Key responsibilities**:
- Decide when to use **synthetic vs production-like data**.
- Design reusable **factories/builders/fixtures** for core domain entities.
- Ensure **privacy and compliance** (masking/anonymization) when using real data.
- Improve **determinism and isolation** to reduce data-related flakiness.

**Typical use**:
- Data-heavy domains or complex schemas.
- When tests are flaky or unreliable due to inconsistent data.

---

### `qa-environment-manager` – Environment and Dependency Coordinator

**Purpose**: Designs and documents the **environment matrix** for testing (local, CI, staging, etc.), including dependencies and setup/teardown patterns.

**Key responsibilities**:
- Inventory test environments and their **capabilities and constraints**.
- Map **test types to environments** (what runs where and why).
- Define **setup/teardown and isolation** practices.
- Collaborate on fixing **environment-related flakiness**.

**Typical use**:
- When adding new test types (integration, E2E, performance).
- When environment differences are causing inconsistent results.

---

### `qa-failure-analyst` – Failure and Flakiness Investigator

**Purpose**: Investigates **failing or flaky tests**, classifies root causes, and recommends where to fix (product, tests, or environment).

**Key responsibilities**:
- Group and **triage failures** by tests, components, and symptoms.
- Distinguish **product bugs vs test bugs vs environment issues**.
- Analyze **flakiness** patterns (timing, data, shared state).
- Propose **targeted fixes** and stabilization work.

**Typical use**:
- After significant test runs with failures or flaky suites.
- Ongoing stabilization of CI and regression pipelines.

---

### `qa-performance-tester` – Performance and Load Specialist

**Purpose**: Designs and interprets **performance and load tests** for critical flows, focusing on throughput, latency, and resource usage.

**Key responsibilities**:
- Identify **performance-critical flows and endpoints**.
- Design **load scenarios** (baseline, peak, stress, soak).
- Interpret metrics for **regressions and bottlenecks**.
- Recommend **next steps** (profiling, optimizations, additional tests).

**Typical use**:
- Before major releases affecting scalability.
- After performance incidents or regressions.

---

### `qa-accessibility-inspector` – Accessibility-Focused QA

**Purpose**: Evaluates UIs for **accessibility**: keyboard navigation, screen reader behavior, semantics, and visual contrast.

**Key responsibilities**:
- Check **keyboard-only navigation** and focus behavior.
- Review **semantics and labeling** for screen readers.
- Highlight **color contrast** and reliance on color-only cues.
- Recommend **concrete accessibility improvements**.

**Typical use**:
- Any release or feature with user-facing UI changes.
- Ongoing accessibility reviews to maintain standards.

---

### `cypress-to-playwright-migrator` – Cypress → Playwright Migration

**Purpose**: Guides systematic migration of Cypress tests to Playwright, mapping patterns, selectors, and helpers while preserving behavior and minimizing flakiness.

**Key responsibilities**:
- Inventory existing Cypress usage (commands, network stubbing, fixtures, custom commands).
- Provide Playwright equivalents and highlight behavioral differences.
- Propose incremental migration strategies and coexistence patterns.

**Typical use**:
- When moving an existing Cypress UI test suite to Playwright in stages.

---

### `playwright-to-cypress-migrator` – Playwright → Cypress Migration

**Purpose**: Guides migration of Playwright tests to Cypress, adapting fixtures, locators, and helpers to Cypress’s model while preserving intent.

**Key responsibilities**:
- Analyze current Playwright usage (fixtures, locators, routing, tracing).
- Map core patterns to Cypress equivalents and call out non-1:1 areas.
- Suggest safe coexistence and validation strategies.

**Typical use**:
- When standardizing on Cypress after initial adoption of Playwright.

---

### `playwright-master` – Advanced Playwright Patterns

**Purpose**: Provides advanced Playwright patterns, best practices, and troubleshooting guidance for stable, fast, and maintainable UI/API tests.

**Key responsibilities**:
- Recommend project structure, fixtures, and config patterns for Playwright.
- Improve selectors, auth/state handling, and test stability.
- Leverage tracing, screenshots, and debugging features effectively.

**Typical use**:
- Designing or refactoring Playwright-heavy test suites.

---

### `cypress-master` – Advanced Cypress Patterns

**Purpose**: Provides advanced Cypress patterns, best practices, and troubleshooting guidance for stable, maintainable UI tests.

**Key responsibilities**:
- Clarify good use of the command queue, waiting, and assertions.
- Recommend plugin, support file, and custom command patterns.
- Tackle common Cypress-specific flakiness and complexity.

**Typical use**:
- Designing or refactoring Cypress-based test suites.

---

### `test-suite-optimizer` – Suite-Level Optimization

**Purpose**: Analyzes test suites as systems to improve speed, stability, and value by restructuring tests, tagging, and scope.

**Key responsibilities**:
- Map existing suites, runtimes, and failure patterns.
- Rebalance the test pyramid and remove redundant or low-value tests.
- Propose tagging and grouping strategies for smoke vs regression vs slow tests.

**Typical use**:
- When regression or CI pipelines are slow, flaky, or hard to evolve.

---

### `selector-architect` – Selector Strategy Designer

**Purpose**: Designs robust selector strategies and abstractions for UI tests to reduce brittleness and improve readability across frameworks.

**Key responsibilities**:
- Define preferred selector types (roles, test IDs, semantics) and anti-patterns.
- Recommend page/screen object or similar abstractions.
- Guide refactors away from fragile selectors in critical paths.

**Typical use**:
- Starting or cleaning up UI test suites with flaky selectors.

---

### `visual-regression-architect` – Visual Testing Strategy

**Purpose**: Designs visual regression testing strategies that catch meaningful UI regressions without overwhelming teams with noise.

**Key responsibilities**:
- Decide which components/pages/flows warrant visual coverage.
- Define snapshot/image comparison granularity, tolerances, and masking rules.
- Integrate visual tests into pipelines and review processes.

**Typical use**:
- Introducing or taming visual/snapshot-based test suites.

---

### `mobile-qa-strategist` – Mobile-Focused QA Strategy

**Purpose**: Designs risk-based test strategies specifically for mobile apps, accounting for devices, OS versions, and mobile-specific behaviors.

**Key responsibilities**:
- Define device/OS matrices and platform-specific risks.
- Plan coverage for permissions, lifecycle events, connectivity changes, and UX.
- Prioritize mobile automation and manual exploration work.

**Typical use**:
- Planning QA for native or hybrid mobile applications.

---

### `api-contract-testing-architect` – API Contract Strategy

**Purpose**: Designs API contract testing strategies between services and clients, focusing on compatibility and safe evolution.

**Key responsibilities**:
- Identify service–consumer relationships and critical contracts.
- Decide what to validate at contract level vs integration vs E2E.
- Plan versioning and change-handling for contracts.

**Typical use**:
- Building or maturing contract testing in service-based systems.

---

### `security-test-advisor` – Security-Oriented QA Ideas

**Purpose**: Brings pragmatic security-focused test ideas into QA planning and implementation (without replacing dedicated security reviews).

**Key responsibilities**:
- Propose tests around input validation, auth/session handling, and authorization.
- Highlight rate limiting and abuse scenarios QA can cover.
- Suggest which checks to automate vs execute manually.

**Typical use**:
- Adding basic security coverage to web/API features and flows.

---

### `ci-pipeline-qa` – CI/CD Test Execution Design

**Purpose**: Designs how tests run in CI/CD pipelines, deciding which suites run when and with what gating.

**Key responsibilities**:
- Map suites to pipeline stages (PR, merge, nightly, pre-release).
- Define gating rules and flakiness handling strategies.
- Balance fast feedback with deep coverage.

**Typical use**:
- Integrating or optimizing tests within CI pipelines.

---

### `exploratory-testing-guide` – Structured Exploratory Testing

**Purpose**: Provides structured guidance for high-value exploratory testing sessions, from charters to debriefs.

**Key responsibilities**:
- Define focused exploratory charters and scopes.
- Structure session notes so findings are actionable.
- Feed new risks and candidates for automation back into the QA loop.

**Typical use**:
- Exploring new or high-risk areas where automation is not yet in place.

---

### `requirements-to-tests` – Requirements Traceability and Acceptance Criteria

**Purpose**: Translates product requirements and acceptance criteria into testable scenarios and maintains traceability between requirements and tests.

**Key responsibilities**:
- Turn requirements and acceptance criteria into concrete, testable scenarios.
- Build and maintain requirement → test scenario → test mapping.
- Identify coverage gaps (requirements with no tests; tests with no requirement).
- Clarify or refine ambiguous or untestable criteria.

**Typical use**:
- New features with written acceptance criteria that need test scenarios.
- Audits of whether current tests cover stated requirements; release sign-off preparation.

---

### `api-test-designer` – Systematic API Test Design

**Purpose**: Designs systematic API test coverage for REST, GraphQL, or gRPC: success paths, errors, auth, payloads, and edge cases.

**Key responsibilities**:
- Design test scenarios per endpoint (success, validation, auth, authorization, edge).
- Specify request/response examples and assertion focus.
- Prioritize and hand off scenarios for implementation.

**Typical use**:
- Building or refining API-level test suites after endpoint discovery.

---

### `release-sign-off` – Release Go/No-Go Criteria

**Purpose**: Defines clear go/no-go criteria and checklists for release readiness so sign-off is consistent and auditable.

**Key responsibilities**:
- Define must-have and should-have release criteria.
- Produce sign-off checklists and decision rules.
- Record deferred risks and exceptions with follow-up.

**Typical use**:
- Defining or updating release criteria; preparing for a specific release or go/no-go meeting.

---

### `flaky-test-prevention` – Proactive Test Stability

**Purpose**: Encodes patterns and practices to prevent flaky tests before they appear: waiting, isolation, data, and timing.

**Key responsibilities**:
- Identify stability risks in test design and implementation.
- Recommend waiting strategies, isolation, and data practices.
- Provide do/avoid checklists and stability guidelines.

**Typical use**:
- Designing new tests or refactoring existing ones for stability; establishing team guidelines.

---

## Using These Skills in Your Own Systems

These skills are intentionally **tool-agnostic**:

- They do **not** depend on specific tool names (like `HttpClientTool` or `FileWriterTool`).
- They describe **capabilities** (“HTTP client”, “file writer”, “test runner”) so each host system can map them to its own tools.

### Example: Using with Cursor

In a Cursor project, you can:

1. Copy any of these skill directories into your project under `.cursor/skills/`:
   - e.g., `.cursor/skills/qa-moderator/`, `.cursor/skills/qa-engineer/`, etc.
2. Or copy them into your **global skills directory** (e.g., `~/.cursor/skills/`) to reuse across projects.

The agent can then read `SKILL.md` for each role to behave according to your QA workflow design.

### Example: Using with Other Agentic Systems

For other systems:

1. Place these directories wherever your framework expects role definitions.
2. At runtime, load `SKILL.md` content and inject it as a **system or role prompt** for that agent.
3. Use `qa-moderator` as your **orchestrator** and let it coordinate other QA roles as needed.

---

## License and Contributions

You can adapt these skills to match your own QA practices, naming conventions, and toolchains.
If you extend them, consider keeping the same general structure (summary, when-to-use, inputs/outputs, workflow, collaboration, host-environment notes) so others can easily plug your additions into their systems.

