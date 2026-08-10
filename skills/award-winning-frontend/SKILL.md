---
name: award-winning-frontend
description: Create or transform a web frontend into a high-craft, Awwwards-level experience with distinctive art direction, custom typography, coherent iconography, responsive layouts, purposeful 3D, parallax, scroll-driven animation, and polished interaction details. Use when a user asks for a beautiful, cinematic, immersive, experimental, premium, motion-rich, or award-quality website or landing page. Verify current library APIs and choose maintained dependencies that fit the existing stack.
---

# Award-Winning Frontend

Build an editorial-quality frontend where art direction, typography, motion, content clarity, and performance reinforce one another. Treat visual ambition as a system, not a pile of effects.

## Establish the brief

Before implementation, ask one compact intake message if the request is missing an output-changing decision:

- Product or story, audience, primary action, and required content
- Brand assets, exact copy, imagery, video, references, and anti-references
- Existing repository, framework, styling system, browser/device support, and deployment target
- Desired intensity of motion, whether 3D is meaningful, and reduced-motion or performance requirements
- Required pages, sections, interactions, and deadline or asset constraints

Proceed when the intent is clear. Do not silently rewrite supplied copy, invent brand claims, or choose an unrelated visual direction. If the user is building a portfolio, pair this skill with `portfolio-maker` when both intake fidelity and advanced motion are needed.

## Inspect the current stack

1. Read repository instructions, package manifests, lockfiles, routes, shared components, tokens, and existing media.
2. Run the current interface when practical and identify the baseline, real content, and existing interaction conventions.
3. Preserve sound architecture and avoid dependency sprawl. Select the smallest set of maintained tools that gives the requested result.
4. When a library API or version matters, check its current official documentation and the installed package metadata. Never guess a "latest" version or API from memory.

## Define the visual system first

Write a one-sentence art direction internally, then encode it in reusable tokens and primitives:

- One strong concept, clear hierarchy, and a deliberate grid or composition
- A restrained color system with intentional contrast, surface, and accent roles
- A type system with a display voice and a highly readable text voice; use a distinctive variable or custom font pairing when it serves the concept
- A consistent icon family with a defined stroke or fill language and optical sizing
- A small vocabulary of depth, texture, border, shadow, and motion behaviors

Load only the needed font families, subsets, and weights. Prefer the framework's font loader or a maintained font package such as Fontsource when appropriate; self-host when it improves performance or control. Keep font fallbacks and metric-compatible loading so text does not jump.

## Build in layers

Implement in this order so effects do not conceal structural weakness:

1. Semantic content structure, navigation, and responsive layout
2. Typography, spacing rhythm, color roles, media treatment, and interactive states
3. Entrance choreography and section transitions
4. Scroll-linked depth, parallax, and pointer interactions
5. 3D scenes, shader work, or other high-cost flourishes only where they express the concept

Use a single motion language: consistent easing, duration families, stagger rules, and depth cues. Every animation must clarify hierarchy, create orientation, reveal content, or express a meaningful interaction.

## Use advanced effects deliberately

- Prefer compositor-friendly transforms and opacity. Use `IntersectionObserver`, CSS scroll-driven animation, or a motion library instead of long-running scroll handlers that force layout work.
- Choose the current maintained tool that fits the existing stack. Examples include Motion or GSAP for orchestration, Lenis only when custom smooth scrolling is justified, and Three.js/React Three Fiber or a hosted 3D scene when genuine spatial content is required. Verify current APIs before coding.
- Keep parallax amplitude subtle enough that content remains readable. Disable or simplify it on small or low-power devices when it adds cost without meaning.
- Lazy-load 3D and heavy media, provide a static or CSS fallback, cap pixel ratio and scene complexity, and avoid blocking the first meaningful paint.
- Use custom cursors, magnetic controls, page transitions, and hover reveals only as enhancements. Never make essential information or controls depend on hover, pointer precision, or animation completion.
- Use one coherent icon library, such as the project's existing set or a maintained set like Lucide or Phosphor. Do not mix arbitrary icon styles or use emoji as interface icons; label icon-only actions.

## Keep the experience usable

- Honor `prefers-reduced-motion`: remove nonessential movement, keep essential state changes understandable, and never hide content behind an animation that may be disabled.
- Preserve semantic headings, landmarks, keyboard access, visible focus, contrast, readable line length, and comfortable touch targets.
- Test mobile, tablet, desktop, portrait, landscape, zoom, slow media, and long content. Do not ship a desktop composition that merely overflows on mobile.
- Respect browser history and native navigation. Do not trap scrolling, disable selection without a strong reason, or replace standard controls with inaccessible gestures.
- Reserve media dimensions to limit layout shift and keep loading, error, empty, and fallback states visually intentional.

## Protect performance

- Measure before and after when possible. Watch initial JavaScript, font and image weight, long tasks, layout shift, animation frame rate, and memory used by 3D.
- Use `will-change` only during an active animation, avoid forced synchronous layout, and keep high-frequency updates on the compositor or a requestAnimationFrame loop with bounded work.
- Split heavy scenes and libraries from the initial route, optimize images and video, and avoid adding a library for an effect that CSS or existing primitives can handle.
- Keep effects graceful under reduced motion, touch input, low bandwidth, and weak GPUs.

## Review the craft

1. Run lint, typecheck, tests, and the production build.
2. Exercise the primary path with keyboard and pointer/touch input at representative viewports.
3. Inspect the first paint, the complete scroll, hover/focus/active states, reduced motion, and the 3D fallback.
4. Check that every effect has a job, every font and icon choice is consistent, and no decorative layer competes with content or calls to action.
5. Remove generic gradients, random glass cards, excessive bounces, duplicated dependencies, and effects that do not survive mobile or accessibility review.

## Handoff

Summarize the art direction, libraries and font/icon sources selected, key motion systems, responsive and reduced-motion behavior, performance checks, commands run, and any unverified browser or device gap.
