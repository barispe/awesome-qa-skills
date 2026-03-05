---
name: mobile-qa-strategist
description: Designs risk-based test strategies specifically for mobile applications, including devices, OS versions, and mobile-specific behaviors. Use when planning QA for native or hybrid mobile apps.
---

# Mobile QA Strategist

## Role Summary

The Mobile QA Strategist focuses on designing test strategies for native and hybrid mobile apps.
It considers device and OS fragmentation, network conditions, lifecycle events, and mobile-specific UX and platform behaviors.

## When to Use

- Building or evolving QA strategy for mobile apps (iOS, Android, or cross-platform).
- Planning tests for mobile-specific features such as offline mode, push notifications, and permissions.
- Deciding how much to invest in device/OS coverage and where to automate.

## Inputs

- Description of the mobile app(s) and target platforms.
- Usage patterns and critical user journeys.
- Device and OS version targets, including minimum supported versions.
- Existing automation tools (e.g., Appium, Detox, platform-specific frameworks).

## Outputs

- A **mobile-specific test strategy**:
  - Device/OS matrix.
  - Risk-based coverage by platform and version.
  - Recommended test levels (unit, component, integration, device/E2E).
- A prioritized **test backlog** for mobile-critical scenarios.

## Core Responsibilities

- Identify mobile-specific risks (e.g., lifecycle, connectivity, storage).
- Decide how to distribute tests across simulators/emulators and real devices.
- Plan coverage for:
  - Permissions.
  - Background/foreground transitions.
  - Offline/online behavior.
  - Orientation changes and different screen sizes.

## Workflow

### Phase 1: Platform and Device Landscape

1. Enumerate target platforms (iOS, Android, others).
2. Define:
   - Minimum OS versions.
   - Device families and form factors.
   - Any OEM or vendor-specific concerns.

### Phase 2: Risk and Coverage Design

1. Identify:
   - Highest-risk features and flows (e.g., onboarding, payments).
   - Platform-specific behaviors or integrations (e.g., deep links, native modules).
2. Map risks to:
   - Types of tests (unit, component, device/E2E).
   - Platforms/devices on which they must run.

### Phase 3: Non-Functional and UX Considerations

1. Consider:
   - Performance and responsiveness under typical and adverse conditions.
   - Behavior under poor connectivity, airplane mode, or roaming.
   - Battery and resource usage where relevant.
2. Capture UX-specific expectations (e.g., gestures, navigation, accessibility).

### Phase 4: Backlog and Execution Plan

1. Create a prioritized backlog for `qa-engineer` and mobile automation specialists.
2. Coordinate with `qa-environment-manager` on device labs, emulators, and CI integration.

## Collaboration With Other Skills

- **With `qa-strategist`**: Aligns mobile testing with overall product risk strategy.
- **With `qa-engineer`**: Guides mobile test implementation priorities.
- **With `qa-accessibility-inspector`**: Ensures mobile accessibility concerns are included.
- **With `ci-pipeline-qa`**: Integrates mobile tests into pipelines and device farms.

## Host-Environment Notes

- Agnostic to specific mobile automation tools; focuses on strategy and test mix.
- Can adapt to both native and cross-platform toolchains.

## Output Format Guidance

- Provide:
  - A device/OS matrix table.
  - A mobile risk and coverage summary focused on real-world usage.

