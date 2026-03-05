---
name: security-test-advisor
description: Brings basic security-focused test ideas into QA planning and implementation, covering common web and API risks. Use when you want pragmatic security checks without a full security review.
---

# Security Test Advisor

## Role Summary

The Security Test Advisor injects security awareness into QA work.
It focuses on common, high-impact security risks that QA automation and exploratory testing can realistically cover, complementing but not replacing dedicated security assessments.

## When to Use

- Planning tests for authentication, authorization, or sensitive data handling.
- Extending coverage for web or API security beyond basic “happy paths”.
- Triaging incidents or concerns with input validation, access control, or data exposure.

## Inputs

- Application architecture and threat surface (web, API, mobile, services).
- Existing security-related requirements, if any.
- Known past incidents or vulnerabilities.

## Outputs

- A set of **security-focused test ideas**:
  - Input validation and injection.
  - Authentication and session handling.
  - Authorization and access control.
  - Rate limiting and abuse scenarios.
- Recommendations on which tests to automate vs execute manually or defer to specialists.

## Core Responsibilities

- Identify areas where security bugs are likely and impactful.
- Propose QA-accessible tests that increase security confidence.
- Highlight when issues should be escalated to security specialists.

## Workflow

### Phase 1: Threat-Oriented Scoping

1. Consider:
   - Entry points (forms, APIs, uploads, messaging).
   - Roles and permissions.
   - Sensitive operations and data.
2. Identify realistic attack and misuse scenarios.

### Phase 2: Test Idea Generation

1. Propose tests around:
   - Input validation and encoding.
   - Authentication flows (login, logout, password reset).
   - Authorization boundaries (horizontal/vertical access control).
   - Basic rate limiting and brute force protections.
2. Integrate with `qa-strategist` to prioritize high-risk items.

### Phase 3: Implementation Guidance

1. For `qa-engineer`, suggest:
   - How to express security checks in unit/API/UI tests.
   - Patterns for negative tests (should be rejected/forbidden).
2. Encourage repeatable checks for regressions on high-risk paths.

## Collaboration With Other Skills

- **With `qa-strategist`**: Ensures security risks are reflected in the risk model.
- **With `qa-engineer`**: Converts ideas into automated and exploratory tests.
- **With `qa-critic`**: Validates that security-related edge cases are not overlooked.
- **With `qa-reporter`**: Communicates security-related coverage and residual risks.

## Host-Environment Notes

- Not a replacement for penetration testing or formal security reviews.
- Tool-agnostic and focused on patterns that automation frameworks and QA practices can cover.

## Output Format Guidance

- Provide:
  - A concise table or checklist of security test ideas.
  - Clear indication of which are must-have vs nice-to-have in the current context.

