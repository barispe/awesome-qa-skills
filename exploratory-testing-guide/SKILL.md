---
name: exploratory-testing-guide
description: Provides structured guidance for high-value exploratory testing sessions, including charters, note-taking, and debriefs. Use when planning or conducting exploratory/manual QA work.
---

# Exploratory Testing Guide

## Role Summary

The Exploratory Testing Guide structures exploratory testing so it is focused, repeatable, and actionable.
It helps testers plan sessions, capture insights, and feed results back into automation and strategy.

## When to Use

- Exploring new or high-risk features without existing tests.
- Investigating areas with frequent bugs or unclear behavior.
- Complementing automated regression suites with human-driven exploration.

## Inputs

- Feature description or area under test.
- Known risks, past bugs, or open questions.
- Timebox or resource constraints for exploratory work.

## Outputs

- **Session charters** (goals and scope).
- Structured **session notes** capturing observations, ideas, and issues.
- A debrief summarizing:
  - Findings and suspected risks.
  - Candidates for automation.
  - Follow-up questions and tasks.

## Core Responsibilities

- Focus exploratory work on high-value questions.
- Encourage diverse test ideas and heuristics.
- Ensure findings are recorded in a way that others can act on.

## Workflow

### Phase 1: Chartering

1. Define:
   - Mission (what you want to learn or validate).
   - Scope (features, flows, or components).
   - Constraints (time, environment).
2. Capture this as a short, clear charter.

### Phase 2: Session Execution

1. Use test heuristics (e.g., CRUD, boundaries, error paths, roles, time) to generate ideas.
2. Record:
   - Steps taken.
   - Observations (expected vs actual).
   - Ideas for further exploration.
   - Potential issues and their suspected impact.

### Phase 3: Debrief and Follow-Up

1. Summarize:
   - What was explored.
   - What was found (bugs, risks, questions).
2. Identify:
   - Test ideas for `qa-strategist` and `qa-engineer` to turn into regression tests.
   - Open questions or design issues to raise with the team.

## Collaboration With Other Skills

- **With `qa-strategist`**: Feeds new risks and ideas into the formal strategy.
- **With `qa-engineer`**: Suggests high-value automation candidates.
- **With `qa-reporter`**: Provides exploratory findings for inclusion in releases.
- **With `qa-critic`**: Shares areas where automated coverage is still weak.

## Host-Environment Notes

- Tool-agnostic and suitable for any combination of manual and automated testing.
- Can be applied even when little or no automation exists yet.

## Output Format Guidance

- Use:
  - Simple charter templates.
  - Bullet-point session notes.
  - Brief debrief summaries that are easy for others to consume.

