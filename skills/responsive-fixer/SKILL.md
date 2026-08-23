---
name: responsive-fixer
description: Diagnose and fix responsive web layout defects across mobile, tablet, desktop, zoom levels, orientations, and input modes. Use when content overflows, layouts collapse, controls become unusable, or a frontend must adapt cleanly across viewport sizes while preserving content and behavior.
---

# Responsive Fixer

Repair responsive behavior from the layout system outward. Avoid accumulating viewport-specific patches.

## Hard rules

These requirements bind every run of this skill. Adapt a rule only when it is genuinely impossible to satisfy, and report the adaptation and its reason in the handoff. Silently skipping a rule is a failed task.

- Work through the sections above in order. Complete inspection before editing.
- Touch only what the request requires. Justify any scope expansion explicitly.
- Never claim a check ran when it did not, cite a file, line, or result not actually observed, or describe unverified behavior as verified.
- Reproduce the failure and record the width where behavior breaks before editing. Never ship speculative fixes for a problem you did not observe.
- After fixing, sweep continuously across widths, test zoom and height-sensitive orientations, and confirm keyboard focus stays visible and unobscured.
- Run relevant lint, type, and test commands and treat unexpected failures as blocking.

## Stop and ask

When the failure cannot be reproduced, ask for the environment, viewport, and reproduction steps instead of guessing. Ask before dropping essential content or actions at any supported width.

## Reproduce the failure

1. Read repository instructions and identify the page shell, layout primitives, breakpoints, and styling conventions.
2. Reproduce the problem at the reported viewport. Record the first width at which behavior breaks, not only a device preset.
3. Inspect narrow, medium, and wide widths around that boundary. Also check zoom, long content, and both pointer and touch interaction when relevant.
4. Trace the failing element through its containing blocks before editing the leaf component.

## Diagnose the root cause

Check for:

- Fixed widths, minimum sizes, or absolute positioning that resist available space
- Flex or grid children that cannot shrink because of intrinsic sizing
- Missing wrapping, clamping, or safe overflow behavior
- Viewport units that ignore browser chrome or container context
- Media without bounded dimensions or stable aspect ratios
- Dense toolbars, tables, navigation, and forms with no content-priority strategy
- Breakpoints chosen by device names instead of actual content failure
- Fixed or sticky elements that obscure content or keyboard focus

Prefer fluid sizing, intrinsic layout, wrapping, `minmax()`, container-aware behavior, and content-driven breakpoints. Add a breakpoint only when the composition genuinely needs to change.

## Implement the fix

- Correct shared layout primitives when multiple symptoms have the same cause.
- Keep essential content and actions available at every supported width.
- Reflow before truncating; truncate only when full content remains accessible elsewhere.
- Preserve DOM order and reading order when rearranging visually.
- Keep tap targets usable and avoid interactions that depend only on hover.
- Reserve space for media and asynchronous content to limit layout shift.
- Make wide data usable with an intentional pattern such as scrolling, prioritization, or alternate presentation.
- Avoid arbitrary pixel nudges that work at only one captured viewport.

## Verify

1. Sweep continuously across widths instead of checking presets alone.
2. Test portrait and landscape where the layout is sensitive to height.
3. Test browser zoom or an equivalently reduced CSS viewport.
4. Exercise long labels, unbroken strings, empty states, errors, and dynamic content.
5. Confirm keyboard focus remains visible and unobscured.
6. Run relevant lint, type, and test commands. Verification is a completion gate: record the actual outcome of every check and report failures verbatim.

## Handoff

Structure the handoff in four labeled parts: (1) What changed: the root cause and the layout rule corrected. (2) Evidence: the breaking width reproduced, the viewport range swept, zoom and orientation results, and check outcomes. (3) Gaps: device-specific conditions not verified. (4) Follow-ups: deferred issues. Do not claim verification at viewports you did not inspect.
