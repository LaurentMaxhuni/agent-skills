---
name: frontend-audit
description: Audit an existing frontend for usability, visual consistency, responsive behavior, accessibility, performance, maintainability, and implementation quality. Use when asked to review, assess, critique, inspect, or produce findings for a web interface. Treat the task as read-only unless the user explicitly asks to implement fixes.
---

# Frontend Audit

Produce a prioritized, evidence-backed review. Do not edit code unless implementation is explicitly requested.

## Scope the review

1. Read repository instructions and map the framework, routes, styling system, shared components, and test setup.
2. Determine the surfaces in scope from the request. If scope is broad, sample the highest-traffic paths, shared shells, forms, and reusable primitives.
3. Run the application when practical and inspect both rendered behavior and source code. Do not infer a visible defect from source alone when it can be verified.

## Review lenses

Inspect the following where relevant:

- Product clarity: hierarchy, labels, navigation, feedback, empty states, and error recovery
- Visual system: typography, spacing, color roles, alignment, iconography, and component consistency
- Responsive behavior: reflow, overflow, density, touch targets, and content priority
- Accessibility: semantics, keyboard flow, focus, forms, contrast, motion, and announcements
- Performance: asset weight, rendering work, layout shift, data waterfalls, and loading strategy
- Code health: duplicated patterns, brittle selectors, state ownership, component boundaries, and test gaps
- Robustness: loading, empty, partial, error, long-content, localization, and permission states

## Record findings

Include a finding only when it is supported by concrete evidence. For each finding, provide:

- Severity: `critical`, `high`, `medium`, or `low`
- Location: route, component, file and line when available
- Evidence: what was observed and under which state or viewport
- Impact: the user, business, accessibility, performance, or maintenance consequence
- Recommendation: the smallest practical remediation

Use severity consistently:

- `critical`: blocks a core path, exposes users to serious harm, or makes the product unusable
- `high`: materially harms a common task or broad group of users
- `medium`: creates meaningful friction, inconsistency, or maintenance risk
- `low`: localized fit-and-finish issue with limited impact

Distinguish confirmed defects from risks that need measurement. Consolidate repeated symptoms under their shared root cause. Do not inflate the report with subjective preferences or praise.

## Validate the report

Recheck high-severity findings, remove duplicates, and confirm that recommendations fit the repository's architecture. Report the commands, viewports, routes, and tools exercised, plus any coverage gaps.

## Handoff

Lead with findings ordered by severity. Follow with open questions and a short audit-coverage summary. If no actionable findings remain, say so and identify residual risk or untested areas.
