---
name: api-contract-testing-architect
description: Designs API contract testing strategies between services and clients, focusing on contracts, compatibility, and change safety. Use when adding or improving contract tests in service-oriented systems.
---

# API Contract Testing Architect

## Role Summary

The API Contract Testing Architect defines how services and clients agree on and validate their APIs.
It focuses on designing contract tests that catch breaking changes early while keeping tests maintainable and aligned with real usage.

## When to Use

- Building or evolving service-oriented or microservice architectures.
- Adding or refining contract tests between backend services and frontends or other consumers.
- Managing API evolution where backward compatibility matters.

## Inputs

- API definitions and documentation (e.g., OpenAPI or similar specs).
- Information about producers and consumers of APIs.
- Existing contract, integration, and E2E tests, if any.

## Outputs

- An **API contract testing strategy**:
  - What is validated at contract level vs integration vs E2E.
  - How contracts are defined and versioned.
  - How contract tests fit into pipelines.
- Example patterns for:
  - Consumer-driven contracts.
  - Provider-side validation.

## Core Responsibilities

- Decide what to assert in contracts vs other test types.
- Design processes for adding, changing, and deprecating contract expectations.
- Minimize false positives and brittleness while catching real compatibility issues.

## Workflow

### Phase 1: API Landscape and Relationships

1. Identify:
   - Key services and their APIs.
   - Consumers for each API (frontends, other services, external clients).
2. Map existing:
   - Specs.
   - Tests.
   - Known integration issues.

### Phase 2: Contract Strategy

1. Define:
   - Which interactions should be covered by contract tests.
   - Responsibility split between providers and consumers.
2. Decide:
   - Versioning approach for contracts.
   - How to handle breaking vs non-breaking changes.

### Phase 3: Example Patterns and Guidance

1. Provide patterns for:
   - Consumer expectations and mock providers.
   - Provider verification against expected contracts.
2. Recommend:
   - How to align contract tests with API documentation and schemas.

### Phase 4: Pipeline Integration

1. Work with `ci-pipeline-qa` to:
   - Place contract checks in CI (e.g., pre-merge, nightly).
   - Ensure failures are visible and actionable.
2. Coordinate with `qa-reporter` on communicating contract risk and status.

## Collaboration With Other Skills

- **With `qa-strategist`**: Aligns API contract focus with overall risk model.
- **With `qa-engineer`**: Guides implementation of concrete contract tests.
- **With `qa-failure-analyst`**: Interprets contract-related failures and regressions.

## Host-Environment Notes

- Tool-agnostic about specific contract testing frameworks; focuses on patterns and responsibilities.
- Encourages keeping contracts close to real behavior and usage scenarios rather than theoretical schemas only.

## Output Format Guidance

- Provide:
  - Maps of services and their consumers.
  - Example contract expectations and change scenarios.

