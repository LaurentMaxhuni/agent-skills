---
name: accessibility-pass
description: Audit and improve practical web accessibility, including semantics, keyboard interaction, focus management, forms, names and descriptions, contrast, motion, media, and dynamic announcements. Use when asked for an accessibility pass, WCAG-oriented improvements, keyboard fixes, screen-reader support, or inclusive interaction design. Do not claim formal compliance from a limited review.
---

# Accessibility Pass

Make the interface more usable with standards-based HTML and established platform behavior. Treat a request to audit as read-only; implement changes when the user asks to improve or fix.

## Hard rules

These requirements bind every run of this skill. Adapt a rule only when it is genuinely impossible to satisfy, and report the adaptation and its reason in the handoff. Silently skipping a rule is a failed task.

- Complete the primary user flow with the keyboard alone after the last structural change. This check is mandatory, not best-effort.
- Run the configured automated accessibility checks and relevant tests; automated success never substitutes for keyboard and semantic inspection.
- Never state or imply WCAG conformance from this pass. Report standards only as targets unless a complete, qualified assessment was performed.
- When auditing, stay read-only until asked to implement; when fixing, re-check accessible names and focus after each structural change.

## Stop and ask

Ask when the conformance target or assistive-technology support scope is unstated and would change what the pass covers. Confirm the switch before implementing anything if the request begins as an audit.

## Establish context

1. Read repository instructions and identify supported browsers, component libraries, test tools, and any stated conformance target.
2. Map the primary task flow, page landmarks, dialogs, forms, menus, and dynamic regions in scope.
3. Inspect rendered behavior as well as source. Automated checks are a supplement to keyboard and semantic inspection, not a substitute.

## Review in user-task order

Check:

- Document language, title, headings, landmarks, and meaningful reading order
- Native interactive elements before custom roles or scripted behavior
- Accessible names, descriptions, labels, instructions, and error association
- Complete keyboard access, logical focus order, visible focus, and no keyboard traps
- Focus movement and restoration for dialogs, route changes, inserted content, and removed controls
- Status and error announcements that do not interrupt unnecessarily
- Contrast of text, controls, focus indicators, and meaningful graphics
- Zoom, text resizing, reflow, touch target size, and orientation behavior
- Reduced motion, animation controls, flashing content, and timeout handling
- Text alternatives, captions, transcripts, and decorative-media treatment
- Authentication and form flows that remain understandable without color or memory alone

## Implement safely

- Prefer native HTML semantics and browser behavior.
- Preserve visible labels; do not use ARIA to conceal unclear interface copy.
- Add ARIA only when native semantics cannot express the required behavior.
- Follow the expected keyboard model for the chosen widget pattern.
- Keep error messages specific, persistent enough to use, and connected to their fields.
- Make focus indicators clearly perceptible without removing useful outlines.
- Avoid positive `tabindex`, redundant roles, and broad live regions.
- Fix the underlying component when a defect repeats across instances.

## Verify

1. Complete the primary flow with a keyboard only.
2. Inspect the accessibility tree or use a screen reader for complex widgets and dynamic changes when available.
3. Run the project's automated accessibility checks and relevant tests.
4. Check narrow reflow, zoom, reduced motion, errors, loading, and empty states.
5. Recheck accessible names and focus after every structural change.

Automated success does not establish WCAG conformance. Report the standard and level only as a target unless a complete, qualified conformance assessment was performed. Verification is a completion gate: the keyboard-only flow completion and every check above must have recorded outcomes before this work is done, with failures reported verbatim.

## Handoff

Structure the handoff in four labeled parts: (1) Findings: fixed or observed issues ordered by user impact. (2) Evidence: manual and automated checks performed with their real outcomes. (3) Gaps: untested assistive technologies, content, or flows. (4) Limits: state plainly that this pass does not establish WCAG conformance.
