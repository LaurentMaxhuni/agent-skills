---
name: feature-wiring
description: Connect a requested feature to its real application entry point and verify the outcome across the layers it uses. Use when wiring UI controls, forms, routes, or commands to existing services, persistence, or workflows, or when completing a partially implemented feature.
---

# Feature wiring

## Trace the real path

1. Identify the user action or invocation and the observable result it should produce. For a form, trace the route, submit handler, validation, write, and confirmation. For a command, trace the public invocation and its output or side effects.
2. Follow an existing working feature through the same boundaries. Reuse the project's routing, data access, authorization, and error handling where they fit. Identify where the requested path currently stops or relies on temporary data.
3. Keep the work to the requested behavior. For an explicitly scoped prototype, use the requested fixture or mock and state its limits in the handoff.

## Wire the missing pieces

- Register or connect the feature through the entry point users already reach. Connect the intended state, service, or store, and preserve the behavior existing callers rely on.
- Keep validation and access checks at the boundary that owns them. When a request can fail or be repeated, account for the relevant failure paths, duplicate submissions, and resulting state.
- Run the project's supported CLI for any required scaffolding or generator-managed files. See [CLI scaffolding](../cli-scaffolding/SKILL.md) when available.

## Verify through the entry point

Exercise the actual route, control, or command in a suitable test or local environment. Check the user-visible outcome and confirm any downstream effect in the intended service or store. For example, reopen or reload the record to verify persistence, or open a downloaded file and inspect its contents. Exercise a relevant failure and check the resulting state. When the feature promises a retry or recovery path, exercise it through to a successful outcome.

Use the project's relevant checks to cover the changed layers. Report the path exercised, the observed outcome, and any boundary covered only by a substitute or still unverified.
