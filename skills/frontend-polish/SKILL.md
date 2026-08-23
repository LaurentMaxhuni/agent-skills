---
name: frontend-polish
description: Refine an existing web interface into a cohesive, production-ready experience by improving visual hierarchy, spacing, typography, color, states, interaction feedback, and consistency. Use when asked to polish, beautify, tighten, modernize, or improve the fit and finish of an implemented frontend without changing its core product behavior.
---

# Frontend Polish

Improve the interface while preserving its purpose, information architecture, and working behavior.

## Hard rules

These requirements bind every run of this skill. Adapt a rule only when it is genuinely impossible to satisfy, and report the adaptation and its reason in the handoff. Silently skipping a rule is a failed task.

- Work through the sections above in order. Complete inspection before editing.
- Touch only what the request requires. Justify any scope expansion explicitly.
- Never claim a check ran when it did not, cite a file, line, or result not actually observed, or describe unverified behavior as verified.
- Re-read the final diff before handoff. Remove debug artifacts, temporary probes, and unrelated changes.
- Name every added dependency, environment variable, and configuration change in the handoff with the reason for it.
- Run the most relevant lint, type, and test commands and treat unexpected failures as blocking.
- Inspect every changed screen at narrow, medium, and wide viewports, and exercise keyboard focus plus every interactive state touched by the change.
- Preserve product behavior. A polish pass must not alter information architecture, copy meaning, or working behavior; surface any needed behavior change instead of shipping it silently.

## Stop and ask

Ask before proceeding when achieving the requested look would require changing product behavior, removing or rewriting content, or replacing an existing design system the user chose.

## Establish the baseline

1. Read repository instructions and identify the framework, design system, styling approach, and relevant routes or components.
2. Run the existing interface when practical. Inspect representative states at desktop and mobile sizes.
3. Identify the product's existing visual language before introducing new patterns. Reuse tokens and components when they are sound.
4. Note functional, responsive, or accessibility defects encountered during inspection. Fix those that block the requested polish; keep unrelated expansion out of scope.

## Choose a direction

State a compact design intent internally before editing: the hierarchy, density, mood, and interaction character the product should express. Derive it from the product and existing brand rather than applying generic decoration.

Prioritize improvements in this order:

1. Information hierarchy and layout
2. Typography and readable measure
3. Spacing rhythm and alignment
4. Color roles and contrast
5. Component consistency
6. Interaction and system states
7. Decorative detail and motion

Fix high-leverage primitives before patching many isolated instances.

## Implement the polish

- Use a deliberate type scale, limited font weights, and predictable line heights.
- Establish a small spacing rhythm and align edges across related regions.
- Give primary, secondary, and destructive actions distinct emphasis.
- Define hover, focus, active, disabled, loading, empty, error, and success states where relevant.
- Prefer shared variables, tokens, and variants over repeated one-off values.
- Keep icons stylistically consistent and label ambiguous icon-only controls.
- Use borders, shadows, gradients, and blur only when they clarify depth or emphasis.
- Keep animation brief, purposeful, and compatible with reduced-motion preferences.
- Preserve content clarity at narrow widths; do not hide essential actions merely to make a layout fit.
- Avoid wholesale rewrites when targeted changes can produce a coherent result.

## Verify

1. Run the most relevant lint, type, and test commands.
2. Inspect changed screens at narrow, medium, and wide viewports.
3. Exercise keyboard focus and all interactive states touched by the change.
4. Check long labels, empty data, validation errors, and loading content when those states exist.
5. Compare the result with the baseline for hierarchy, consistency, and unintended behavior changes. Verification is a completion gate: record the actual outcome of every check and report failures verbatim.

## Handoff

Structure the handoff in four labeled parts: (1) What changed: the design direction and the most important improvements. (2) Evidence: checks run with their real outcomes and the screens inspected. (3) Gaps: any screen or state that could not be exercised. (4) Follow-ups: deferred issues. Do not claim polish that was not verified in the rendered interface.
