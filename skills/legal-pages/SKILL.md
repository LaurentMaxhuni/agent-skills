---
name: legal-pages
description: Plan, generate, and wire in the legal pages a website needs, including a Privacy Policy, Terms of Service, and Cookie Policy as the core set, plus optional Acceptable Use, Disclaimer, and EULA modules. Use when a user asks to add legal pages, terms, a privacy or cookie policy, or footer legal links to a new or existing site. Produces clearly marked templates that must be reviewed by a qualified lawyer, never presents generated text as legal advice, and never invents company facts or jurisdictions.
---

# Legal Pages

Add the legal pages a website actually needs, wired into its routing and navigation, as clearly marked templates ready for legal review.

## Hard rules

These requirements bind every run of this skill. Adapt a rule only when it is genuinely impossible to satisfy, and report the adaptation and its reason in the handoff. Silently skipping a rule is a failed task.

- Work through the sections above in order. Complete inspection before editing.
- Touch only what the request requires. Justify any scope expansion explicitly.
- Never claim a check ran when it did not, cite a file, line, or result not actually observed, or describe unverified behavior as verified.
- Re-read the final diff before handoff. Remove debug artifacts, temporary probes, and unrelated changes.
- Name every added dependency, environment variable, and configuration change in the handoff with the reason for it.
- Never present generated text as legal advice. Include a clearly marked, non-removable notice recommending review by a qualified lawyer for the applicable jurisdictions at the top of every generated page's source, and state the template nature of the output in the handoff.
- Never invent company details, registration numbers, addresses, contact points, jurisdictions, or data-processing practices. Use clearly replaceable placeholders for missing facts and record every one in the handoff.
- Mark jurisdiction-specific content (for example GDPR, CCPA/CPRA, ePrivacy, LGPD) in explicitly flagged sections. Do not silently mix regimes; list in the handoff any jurisdiction the user needs that the generated text does not reliably cover.
- Every generated page must be reachable through the site's routing and linked from the footer or an equivalent persistent location. An orphaned legal page is a failed task.
- Match the site's existing framework, routing, and styling system. Do not introduce a new stack to host legal pages.
- Run the relevant lint, typecheck, test, and build commands before handoff and inspect every generated page rendered.

## Stop and ask

Send one compact intake message before writing when any output-changing decision is open. When a missing decision would materially change the page set or a clause's substance, ask about that decision specifically instead of picking a silent default.

## Collect the brief

If the request leaves an output-changing decision open, ask one compact, structured intake message before writing. Ask only for information that changes the result:

- Legal entity or site owner name, and a contact point for privacy and legal inquiries
- Applicable jurisdictions: where the site operates, targets users, or is established
- Which optional modules are needed: Acceptable Use, Disclaimer, EULA
- What data the site collects and through which surfaces: forms, accounts, purchases, analytics
- Third-party services present: analytics, payments, advertising, embeds, hosting, email
- Whether the product has users who generate content, is a paid application, or distributes software, which drive the Acceptable Use and EULA modules
- Cookie and tracking usage, whether a consent banner exists, and whether one must be added
- Desired URLs for the pages and where they should be linked

When the answers are sufficient, proceed without forcing another approval round. Otherwise choose a reversible default, record it, and use an explicit placeholder for every missing fact.

## Inspect the site

1. Read repository instructions and identify the framework, routing conventions, styling approach, and existing static or content pages to imitate.
2. Inventory the data collection surfaces: forms, authentication, checkout, analytics scripts, cookies, local storage, and third-party tags actually present in the code.
3. Inspect the existing footer, navigation, and layout components to determine where legal links belong and how simple content pages are structured.
4. Check whether a consent mechanism exists and whether any privacy or terms files already exist elsewhere in the repository before creating duplicates.

## Select the page set

- Always generate a Privacy Policy and Terms of Service.
- Generate a Cookie Policy when the site sets cookies or loads tracking or embedding scripts; otherwise record the exclusion and its reason.
- Add the Acceptable Use module when users can post, upload, or communicate; the Disclaimer module when the site provides informational, professional, or opinion content; the EULA module when the product ships installable or licensed software. Justify each included or excluded module against the inspection evidence.
- Do not add filler pages to imitate a template. Every generated page must map to a stated need or intake answer.

## Generate the pages

- Write each page in the site's existing language, tone, and content-page structure, using semantic headings and plain prose rather than dense legalese where the meaning allows it.
- Cover the substance for each page type: Privacy Policy (data collected, purposes, legal bases where applicable, sharing and processors, retention, user rights, children, contact); Terms of Service (acceptance, eligibility, accounts, acceptable behavior, purchases, intellectual property, disclaimers, limitation of liability, termination, governing law, dispute resolution); Cookie Policy (categories used, purposes, third parties, control options).
- For the optional modules: Acceptable Use (prohibited content and conduct, enforcement, reporting), Disclaimer (informational and liability scope), EULA (license grant, restrictions, updates, termination).
- Cross-link related pages where they reference each other, and keep every jurisdiction-specific obligation inside its flagged section.
- Use bracketed placeholders for every missing fact so they are easy to find and replace, and keep the lawyer-review notice at the top of each page's source.

## Wire them in

- Create routes consistent with the site's URL conventions, such as `/privacy`, `/terms`, and `/cookies`, unless the intake specifies otherwise.
- Link every generated page from the footer or the equivalent persistent location, reusing the existing layout and link components.
- Add correct document titles and metadata for each page when the stack supports it.
- Add a consent banner only when the intake or inspection established that one is required and the user asked for it; otherwise record it as a follow-up.

## Verify

1. Run the relevant lint, typecheck, test, and build commands.
2. Visit every generated page rendered and confirm it inherits the site's layout, styling, and navigation without breaking anything.
3. Confirm every footer or nav link points to the intended page, and that every cross-link between pages resolves.
4. Confirm the lawyer-review notice is present in every generated page and every placeholder is enumerated.
5. Review the result against the brief and the inspection evidence. Remove any page, clause, or claim that was not requested or justified. Verification is a completion gate: record the actual outcome of every check and report failures verbatim.

## Handoff

Structure the handoff in four labeled parts: (1) What changed: generated pages, routes, links, and reversible defaults chosen on the behalf of the user, plus an explicit statement that the pages are templates, not legal advice. (2) Evidence: commands run with their real outcomes, plus pages visited and links checked. (3) Gaps: every placeholder added, any jurisdiction the generated text does not reliably cover, and anything not verified. (4) Follow-ups: deferred issues, such as consent banners or module pages excluded by choice. Do not claim legal completeness that was not established.