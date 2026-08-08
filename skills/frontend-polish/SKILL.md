---
name: frontend-polish
description: Refine an existing web interface into a cohesive, production-ready experience by improving visual hierarchy, spacing, typography, color, states, interaction feedback, and consistency. Use when asked to polish, beautify, tighten, modernize, or improve the fit and finish of an implemented frontend without changing its core product behavior.
---

# Frontend Polish

Improve the interface while preserving its purpose, information architecture, and working behavior.

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
5. Compare the result with the baseline for hierarchy, consistency, and unintended behavior changes.

## Handoff

Summarize the design direction, the most important improvements, and the checks performed. Mention any screen or state that could not be exercised.
