---
name: release-sign-off
description: Defines clear go/no-go criteria and checklists for release readiness, so sign-off is consistent and auditable. Use when preparing releases or establishing release quality gates.
---

# Release Sign-Off

## Role Summary

The Release Sign-Off skill defines what "ready to release" means for a given product or release type.
It produces clear criteria, checklists, and decision rules so that releases are consistent, defensible, and aligned with risk tolerance.

## When to Use

- Defining or updating release criteria for a product or project.
- Preparing for a specific release (pre-release review, go/no-go meeting).
- After incidents, when tightening or clarifying release gates.

## Inputs

- Release scope (features, fixes, dependencies).
- Current test results and known issues (from `qa-reporter`, `qa-failure-analyst`).
- Risk tolerance and business context (e.g., hotfix vs major release).
- Any compliance or audit requirements for evidence of testing.

## Outputs

- **Release criteria document**: what must be true for a go decision.
- **Sign-off checklist**: concrete items to verify (tests passing, no critical bugs, docs updated, etc.).
- **Decision log template**: who decided, when, and what was checked.
- **Deferred-risk log**: known issues accepted for this release with mitigation or follow-up.

## Core Responsibilities

- Turn vague "quality bar" into explicit, checkable criteria.
- Balance thoroughness with practicality (avoid impossible or meaningless gates).
- Document what was checked and what was explicitly accepted as residual risk.
- Support audit trails when required.

## Workflow

### Phase 1: Define Release Type and Scope

1. Clarify release type: major, minor, patch, hotfix, or other.
2. List in-scope changes: features, fixes, infra, config.
3. Note any special constraints: deadlines, dependencies, compliance.

### Phase 2: Define Go/No-Go Criteria

1. Define **must-have** criteria, for example:
   - Critical/smoke tests: all pass (or defined exceptions).
   - No open P0/P1 bugs in scope (or approved exceptions).
   - Key flows manually verified or automated and passing.
   - Known regressions addressed or explicitly deferred.
2. Define **should-have** criteria (recommended but not blocking):
   - Full regression suite green or within accepted flakiness.
   - Performance or security checks completed.
   - Documentation or runbooks updated.
3. Specify **who** can sign off and **what** evidence is required (e.g., test report, bug list).

### Phase 3: Build the Checklist

1. Turn criteria into a step-by-step checklist:
   - Item to verify.
   - How to verify (e.g., "Run suite X", "Confirm no P0 in Jira").
   - Pass/fail or done/not done.
2. Add placeholders for sign-off date and approver(s) if needed.

### Phase 4: Deferred Risks and Exceptions

1. Provide a simple format for **accepted risks**:
   - Issue or gap.
   - Why it is accepted for this release.
   - Mitigation or follow-up (e.g., ticket, monitoring).
2. Ensure exceptions to criteria are recorded, not implicit.

## Collaboration With Other Skills

- **With `qa-reporter`**: Uses run summaries and coverage reports as evidence for criteria.
- **With `requirements-to-tests`**: Uses requirement coverage to justify "feature complete" or coverage criteria.
- **With `qa-failure-analyst`**: Incorporates failure and flakiness status into go/no-go evidence.
- **With `ci-pipeline-qa`**: Aligns criteria with what the pipeline can demonstrate (e.g., "main branch green").
- **With `qa-moderator`**: Ensures sign-off is a defined phase in the QA workflow.

## Host-Environment Notes

- Does not require specific issue trackers or test tools; criteria and checklists can be expressed in markdown or docs.
- If the host has templates or tools for release notes or sign-off, can output in a compatible structure.

## Output Format Guidance

- Use **numbered checklists** for sign-off items with clear pass/fail.
- Use a **short criteria summary** at the top (e.g., "Go if: 1–4 satisfied and no unresolved P0").
- Keep **deferred-risk** entries brief: issue, reason accepted, follow-up.
