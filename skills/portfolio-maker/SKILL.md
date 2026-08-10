---
name: portfolio-maker
description: Plan and build a faithful, polished portfolio website for a person, studio, agency, artist, creator, or professional. Use when a user wants a new portfolio, case-study site, resume site, personal brand site, or a portfolio generated from supplied copy, links, assets, or design requirements. Ask for the missing essentials before implementation, preserve the user's wording and intent, and deliver a working responsive frontend.
---

# Portfolio Maker

Turn the user's story, work, and constraints into a working portfolio. Optimize for fidelity first, then craft.

## Collect the brief

If the request leaves an output-changing decision open, ask one compact, structured intake message before building. Do not start by proposing a visual style or by rewriting the brief.

Ask only for information that changes the result:

- Goal, audience, and primary action (contact, hire, book, buy, or explore)
- Exact name, role, bio, project descriptions, links, contact details, and preferred ordering
- Sections or pages required, and any sections to exclude
- Logo, colors, typography, photography, video, case-study, and social assets
- Existing repository, framework, styling system, deployment target, and browser constraints
- Desired interaction level plus accessibility, performance, or deadline constraints

When the answers are sufficient, proceed without forcing another approval round. If a missing decision would materially change the site structure, ask about that decision specifically. Otherwise choose a reversible default and record it.

## Protect the user's intent

- Treat supplied copy as source material, not an invitation to copywrite. Preserve wording, spelling, capitalization, claims, names, links, hierarchy, and tone unless editing is requested.
- Never invent clients, metrics, awards, testimonials, employers, services, credentials, or project outcomes. Use an explicit, easy-to-replace placeholder when an asset or fact is missing.
- Preserve supplied visual direction and reference assets. Do not substitute a trend, palette, layout, or art direction merely because it is fashionable.
- Keep portfolio content in a central data/config layer when the project allows it, so the user can update projects and links without hunting through layout code.

## Inspect before building

1. Read repository instructions and identify the framework, routes, styling approach, shared components, assets, and available scripts.
2. Decide whether to extend the existing app or create the smallest compatible site structure. Preserve working architecture and dependencies.
3. Run the interface when practical. Inspect the current baseline, representative routes, and supplied assets before changing them.
4. Convert the brief into a short page map and content map. Remove template sections that do not serve the user's goal.

## Shape the experience

- Make the first viewport answer who the person or studio is, what they do, and what the visitor should do next.
- Use a clear project hierarchy: title, role, outcome or contribution when provided, medium, and a path to deeper work.
- Choose sections from the brief, such as selected work, about, capabilities, process, writing, resume, testimonials, or contact. Do not add filler to imitate a template.
- Keep navigation, project order, external links, and calls to action faithful to the brief.
- Use real media when available. Give every image a meaningful alternative and preserve focal points across breakpoints.

## Implement

- Establish a small, coherent system for typography, color roles, spacing, radii, borders, elevation, and interactive states before styling individual sections.
- Use semantic HTML, readable type, predictable focus order, visible focus, keyboard-complete controls, and usable touch targets.
- Make the layout responsive by content and container behavior, not by patching a few device widths.
- Add motion only when it supports orientation or hierarchy. Keep content available without animation and honor `prefers-reduced-motion`.
- Keep loading, empty, missing-media, error, and external-link states intentional where they can occur.
- Include useful page metadata, document titles, social preview data, and descriptive URLs when the stack supports them.

## Verify

1. Run the relevant lint, typecheck, test, and production build commands.
2. Inspect narrow, medium, and wide viewports, including long project titles and missing or slow media.
3. Test keyboard navigation, focus visibility, contrast, reduced motion, image alternatives, and external links.
4. Confirm every user-supplied link and call to action points to the requested destination.
5. Review the result against the brief. Remove any copy, section, visual treatment, or effect that was not requested or justified by the user's intent.

## Handoff

Report the implemented routes and files, the assumptions made, any missing user assets or facts, the commands run, and any verification gap. Keep the handoff factual; do not claim polish or functionality that was not exercised.
