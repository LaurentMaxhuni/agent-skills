---
name: carousel-maker
description: Build a production-quality, original, non-boxy Instagram-style post and carousel UI as functional HTML, CSS, and JavaScript. Use when a user asks for an Instagram post mockup, social post preview, swipeable carousel, campaign carousel, or a vanilla web implementation of a multi-slide post. Adapt the art direction to supplied copy, logos, assets, DESIGN.md, BRAND.md, design tokens, or other project guidance instead of applying a fixed visual style; source high-quality web assets when needed and use coherent icon libraries such as Devicon, Simple Icons, Lucide, Phosphor, or the existing project set.
---

# Carousel Maker

Build a working social-post interface, not a static screenshot. Make the carousel feel like a considered product surface with a clear visual idea, believable content structure, and interaction details that survive real use.

## Hard rules

These requirements bind every run of this skill. Adapt a rule only when it is genuinely impossible to satisfy, and report the adaptation and its reason in the handoff. Silently skipping a rule is a failed task.

- Work through the sections above in order. Complete inspection before editing.
- Touch only what the request requires. Justify any scope expansion explicitly.
- Never claim a check ran when it did not, cite a file, line, or result not actually observed, or describe unverified behavior as verified.
- Re-read the final diff before handoff. Remove debug artifacts, temporary probes, and unrelated changes.
- Name every added dependency, vendored asset, and pinned URL in the handoff with its source and reason.
- Run lint, typecheck, and tests, or serve the page locally and check the console and network panel for errors before handoff.
- Exercise previous and next controls, pagination, keyboard shortcuts, touch swipe, and direct selection until state stays correct after repeated navigation.
- Ship an export feature that saves every slide as a high-quality image: all slides, not only the active one, captured at the post's true target-ratio resolution with a device-pixel ratio of 2 or more, lossless PNG output, and predictable filenames (`slide-01.png`, `slide-02.png`, ...).
- Never ship emoji as interface icons, mixed icon families, fabricated logos or SVGs, or invented engagement numbers and testimonials.

## Stop and ask

Send one compact intake message before building when the purpose, exact copy, assets, slide count, target ratio, or interaction scope would change the result and the answer is not already supplied. If web access is unavailable and required assets cannot be sourced, say so plainly instead of fabricating them.

## Hold the whole interface to a high design bar

The carousel, post chrome, controls, and responsive behavior are all part of the deliverable. A beautiful slide inside a generic, boxy, default-looking shell is still a failure.

- Choose one clear visual thesis from the brief and make the post frame, typography, media, controls, spacing, and motion support it. The result should feel authored rather than assembled from a template.
- Do not trap the work in a centered white card, a stack of nested rounded rectangles, a generic dashboard grid, or evenly spaced boxes unless the supplied design system explicitly calls for that. Prefer deliberate edge-to-edge media, asymmetry, rhythm, cropping, layering, and whitespace where they serve the content.
- Design the surrounding UI as carefully as the carousel: profile/header treatment, progress indicators, action row, captions, focus states, loading/error states, and mobile-to-desktop transitions must belong to the same visual system.
- Use optical spacing and intentional alignment, not only framework defaults. Tune type metrics, image crops, control hit areas, and baseline rhythm at the actual target ratio.
- Do a visual critique pass before handoff. If the result could be described as a generic AI template, looks overly boxy, or has decoration without a job, revise the composition, hierarchy, assets, or interaction states.

## Establish the brief and inspect the sources

1. Read repository instructions, package manifests, routes, existing components, design tokens, and the current frontend before editing.
2. Search for `DESIGN.md`, `BRAND.md`, `brand.md`, `design-system.md`, token files, `/design`, `/assets`, `/public`, and supplied images or fonts. Treat these as authoritative when they exist.
3. Preserve supplied copy, names, handles, facts, metrics, links, and assets. Never invent brand claims, engagement numbers, testimonials, or project outcomes. If content is missing, use clearly labeled placeholder content that is easy to replace.
4. Ask one compact intake message when a missing decision would change the output: the post purpose and audience, exact copy and assets, slide count, target ratio (`1:1` or `4:5`), and whether local-only interactions or a backend are required. Proceed when the intent is clear.
5. Derive one concise art direction from the brief and source material. Support genuinely different directions—editorial, minimal, tactile, raw, playful, luxury, technical, or high-energy—as the content demands. Do not force every carousel into the same dark gradient, glass card, bento grid, or oversized rounded-pill treatment.

## Use real assets and provided logos

- Inspect the repository and user attachments for logos, wordmarks, avatars, product screenshots, illustrations, photography, fonts, and brand marks before inventing anything. If a logo is provided, use that exact asset wherever the brand appears; do not replace it with plain text, an emoji, a generic icon, or a hand-drawn imitation.
- Preserve supplied logo proportions, transparency, clear space, and intended colors unless the user explicitly requests a treatment. Use the correct variant for its background, add meaningful alternative text when it conveys identity, and test that it remains legible at the actual size.
- When an important visual asset is missing, use web search or image search to find a high-quality, appropriate source before drawing a substitute. Prefer official brand media kits or CDNs for logos, Devicon or Simple Icons for technology and brand marks, and reputable image libraries or public-domain sources for photography and illustration. Check the source, license, dimensions, transparency, and usage constraints.
- Prefer a real PNG, JPG, WebP, or vetted SVG from a trustworthy source. Never fabricate a complex logo, icon, illustration, or decorative scene as a quick inline SVG. Do not trace or approximate a brand mark, generate a fake SVG, or use a random low-quality result just to fill space.
- If web access is unavailable or no suitable asset can be used, choose typography, color, texture, or layout that works without the missing artwork. A restrained composition is better than a bad placeholder. If an external asset is used, pin the URL or package version where possible, vendor it locally when appropriate, and record its source in the handoff.

## Choose the content and layout model

- Use a single slide data model as the source of truth. Each slide should have the content and media fields it needs rather than duplicating nearly identical markup.
- Define the intended post ratio and reserve media space with `aspect-ratio` or equivalent dimensions. Keep text, logos, and controls inside deliberate safe areas.
- Build the complete post shell when requested: profile/header context, media stage, slide position, carousel controls, caption or supporting copy, and action row. Include only the regions that serve the brief.
- For multi-slide content, make the carousel unmistakable. Use a track or an equivalent state-driven renderer with one active slide, visible position feedback, and a clear next/previous affordance. Do not present a row of static images and call it a carousel.
- Keep the information hierarchy obvious at a glance. Establish the hook, supporting detail, and call to action across slides instead of putting every sentence on every frame.

## Implement the vanilla experience

When the request calls for HTML, CSS, and JavaScript, deliver them as understandable source files with a clear entry point. Preserve an existing framework when the repository already has one, but do not silently replace a requested vanilla implementation with a framework.

- Use semantic landmarks and buttons for controls. Keep the active slide, pagination, and control state in JavaScript rather than relying on fragile CSS-only tricks.
- Implement previous/next controls, pagination indicators, and direct slide selection. Support `ArrowLeft`, `ArrowRight`, `Home`, and `End`; keep focus visible and move focus intentionally when a user selects a slide.
- Support touch swipes with a sensible threshold and pointer input where appropriate. Prevent accidental clicks after a drag, avoid hijacking page scrolling, and provide a non-gesture path for every action.
- Make local UX controls real: like/save toggles, share or copy fallback, comment expansion, filters, or other controls must update visible state and have accessible names. Remove controls that are not in scope instead of shipping dead buttons.
- Do not autoplay by default. If autoplay is requested, provide pause/resume, pause when the document is hidden, stop on interaction, and honor `prefers-reduced-motion`.
- Announce meaningful slide changes without creating noisy screen-reader output. Keep pagination text, `aria-current`, disabled or looped control state, and the live region synchronized.
- Handle missing, slow, or broken media intentionally. Reserve dimensions, provide useful fallback styling, and do not let an image error collapse the composition.
- Build the slide-export path on the same data model: render each slide into an offscreen capture sized to the reserved aspect ratio, wait for `document.fonts.ready` and image decode before capture, and save each frame through `canvas.toBlob` as PNG. Prefer native canvas or SVG `foreignObject` serialization; add a capture library only when fidelity demands it, vendor it locally, and record it in the handoff. External media must be CORS-clean or vendored so the canvas does not taint. Surface progress, completion, and failure states in the interface, and give the export control an accessible name.
- Keep data, state transitions, and DOM updates small and inspectable. Avoid a monolithic event handler and avoid adding a dependency for behavior that a few tested lines of JavaScript can provide.

## Build a visual system from evidence

- Encode the chosen direction in tokens for color roles, type scale, spacing, border treatment, shadows, media treatment, and motion. Reuse the repository's tokens when they are sound.
- Use typography to create hierarchy and rhythm. Load only the needed families and weights; keep a metric-compatible fallback and readable line lengths.
- Give each slide a reason to exist. Vary composition, crop, emphasis, or pacing when the story benefits from it, while keeping navigation and brand cues consistent.
- Use contrast, overlays, and texture to support legibility. Keep text readable over media at every slide state, including hover, focus, and small screens.
- Keep motion purposeful: slide movement should communicate position, and secondary reveals should clarify hierarchy. Use compositor-friendly transforms and opacity, and simplify nonessential motion on small or low-power devices.

## Use a coherent icon system

- Prefer the project's existing icon library. Otherwise choose one maintained interface set such as Lucide or Phosphor for controls, and use one consistent stroke or fill language throughout.
- Use Devicon for developer tools, languages, frameworks, and technology brands when those marks are part of the content. Use Simple Icons or another appropriate maintained brand set for non-developer brands. Treat brand marks as content, not as a second unrelated control-icon style.
- Verify the current package or CDN API and pin a version when using a vanilla static page. Use the web to confirm the real asset or API rather than guessing SVG paths or inventing icon markup. If network access is not appropriate, vendor only the needed assets locally and document their source.
- Never use emoji as interface icons, mix arbitrary icon families, or draw low-quality substitute logos. Label icon-only controls and make their hit areas comfortable on touch screens.

## Avoid AI-slop output

- Do not default to purple/blue gradients, floating glass panels, random blobs, excessive pills, generic dashboard cards, or a huge display headline with no content purpose.
- Do not add decorative effects before solving hierarchy, spacing, content fit, responsive behavior, and interaction states.
- Do not copy a single reference style when the user provides multiple references or brand guidance. Extract the transferable constraints—tone, type, color roles, density, imagery, and motion—then make an original composition.
- Do not use fake testimonials, invented social proof, stock-looking filler, or repetitive placeholder copy. Make placeholders explicit and replaceable.
- Make the work feel authored: align edges, tune optical spacing, choose intentional crops, vary slide pacing, and give every border, shadow, texture, and animation a job.

## Verify the result

1. Run the relevant lint, typecheck, tests, and production build or serve the static page through a local server.
2. Exercise previous/next, dots, keyboard shortcuts, touch swipe, direct selection, the export control, and every enabled action. Confirm the active state and announcement stay correct after repeated navigation.
3. Inspect at narrow phone widths, `1:1` and `4:5` media ratios, tablet, desktop, landscape, zoom, long captions, missing media, and reduced-motion mode.
4. Check keyboard order, visible focus, accessible names, contrast, touch target size, text clipping, and whether essential content is available without hover or animation.
5. Export every slide through the shipped feature. Confirm one correctly named file per slide, open the first and last exports at full size to check for missing fonts, broken media, clipped text, or color shifts, and confirm dimensions match the target ratio at the promised pixel ratio.
6. Check the console and network panel for errors, verify icons render from the intended source, and remove dead code, unused dependencies, and unverified external assets.
7. Inspect the finished interface as a visual artifact at the target size. Replace any hand-made or visibly low-quality SVG, fake logo, generic placeholder image, boxy nesting, or unintentional template treatment before handoff. These checks are a completion gate: record their actual outcomes and report failures verbatim.

## Handoff

Structure the handoff in four labeled parts: (1) What changed: the art direction and its sources, the carousel data model, interaction and export behavior, and icon libraries or vendored assets used. (2) Evidence: commands run with outcomes, interactions exercised, viewports and ratios checked, console and network results. (3) Gaps: unverified devices, missing assets, or absent backend integration. (4) Follow-ups: deferred issues. Do not claim interactions or asset quality that were not exercised.
