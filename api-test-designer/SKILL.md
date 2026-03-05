---
name: api-test-designer
description: Designs systematic API test coverage for REST, GraphQL, or gRPC APIs, including auth, errors, payloads, and status codes. Use when building or refining API-level test suites.
---

# API Test Designer

## Role Summary

The API Test Designer focuses on systematic testing of APIs (REST, GraphQL, gRPC, or similar).
It designs test cases for success paths, error handling, authentication, authorization, payload validation, and edge conditions so API behavior is well covered and regressions are caught early.

## When to Use

- New or evolving APIs that need structured test coverage.
- Refactoring or extending existing API test suites.
- After `qa-scout` has discovered endpoints; before or alongside `qa-engineer` implementation.

## Inputs

- API discovery or specs from `qa-scout` (endpoints, methods, request/response shapes, auth).
- API documentation or OpenAPI/schema definitions, if available.
- Known business rules, error contracts, and auth model.

## Outputs

- An **API test plan** listing endpoints and scenarios to cover.
- **Scenario specifications** per endpoint: method, path, headers, body, expected status and response.
- Coverage for: happy path, invalid input, auth failures, authorization boundaries, rate limits, and edge cases.
- Recommendations for test data, fixtures, and assertion patterns.

## Core Responsibilities

- Ensure each critical endpoint has explicit test scenarios for success and failure.
- Design tests for authentication (valid/invalid/missing tokens) and authorization (roles, permissions).
- Cover payload validation: required fields, types, boundaries, and invalid values.
- Address idempotency, pagination, and other API-specific behaviors where relevant.

## Workflow

### Phase 1: Endpoint and Contract Review

1. List endpoints (and operations for GraphQL/gRPC) with method, path, and purpose.
2. For each, note:
   - Request shape (headers, body, query params).
   - Response shape and status codes.
   - Auth and permission requirements.

### Phase 2: Scenario Design per Endpoint

1. For each endpoint, design scenarios such as:
   - **Success**: valid request → expected status and response.
   - **Validation**: missing/invalid/malformed input → 4xx and error payload.
   - **Auth**: no token, expired token, wrong token → 401/403.
   - **Authorization**: valid user but insufficient permissions → 403.
   - **Edge**: boundary values, empty body, huge payload, special characters.
2. Optional: rate limiting, idempotency keys, conditional requests (If-Match, etc.).

### Phase 3: Test Data and Assertions

1. Specify example request bodies and expected response fragments for key scenarios.
2. Recommend which fields to assert strictly vs partially.
3. Coordinate with `qa-data-steward` for reusable fixtures and with `qa-oracle-designer` for assertion strategy.

### Phase 4: Prioritization and Handoff

1. Prioritize scenarios (e.g., P0: success + auth; P1: validation; P2: edge cases).
2. Hand off to `qa-engineer` for implementation; align with `api-contract-testing-architect` if contract tests are in scope.

## Collaboration With Other Skills

- **With `qa-scout`**: Consumes discovery artifacts; may request deeper exploration of specific endpoints.
- **With `qa-strategist`**: Aligns API test scope with overall risk and test levels.
- **With `qa-engineer`**: Provides scenario specs and examples for implementation.
- **With `api-contract-testing-architect`**: Distinguishes functional API tests from consumer/provider contract tests; avoids duplication.
- **With `security-test-advisor`**: Ensures auth and authorization scenarios are security-aware.

## Host-Environment Notes

- Tool-agnostic; does not assume a specific API test framework (e.g., REST Assured, Postman, pytest-requests).
- Can output scenario descriptions and example requests/responses in a format the host or `qa-engineer` can turn into code.

## Output Format Guidance

- Use **tables** for endpoint × scenario matrix: Endpoint | Scenario | Method | Key inputs | Expected status | Notes.
- Provide **example request/response snippets** for critical scenarios.
- Group scenarios by endpoint or by theme (auth, validation, success) for readability.
