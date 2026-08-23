---
name: frontend-audit
description: Audit an existing frontend for usability, visual consistency, responsive behavior, accessibility, performance, maintainability, and implementation quality. Use when asked to review, assess, critique, inspect, or produce findings for a web interface. Treat the task as read-only unless the user explicitly asks to implement fixes.
---

# Frontend Audit

Produce a prioritized, evidence-backed review. Do not edit code unless implementation is explicitly requested.

## Hard rules

These requirements bind every run of this skill. Adapt a rule only when it is genuinely impossible to satisfy, and report the adaptation and its reason in the handoff. Silently skipping a rule is a failed task.

- Base every statement on something actually inspected. Never claim a check, file read, route visit, or observation that did not happen.
- Stay read-only. If the user asks for fixes during the audit, confirm the switch to implementation mode explicitly before editing anything.
- Give every finding concrete evidence: location, the observed state or viewport, and impact. Label anything not directly observed as a risk needing measurement, never as a defect.
- Report coverage honestly: which commands, routes, viewports, and tools were exercised, and which were not.

## Stop and ask

Confirm before implementing anything if the user asks for fixes during a read-only audit. Ask when the scope is so broad that sampling choices would materially change the conclusions, so the user can set priorities first.

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

Validation is a completion gate: recheck every high-severity finding against observed evidence before the report is final. Recheck high-severity findings, remove duplicates, and confirm that recommendations fit the repository's architecture. Report the commands, viewports, routes, and tools exercised, plus any coverage gaps.

## Handoff

Lead with findings ordered by severity. Follow with open questions and an explicit coverage summary naming every command, route, viewport, and tool exercised, plus everything not covered and why. Every reported finding must trace back to recorded evidence. If no actionable findings remain, say so and identify residual risk or untested areas.
