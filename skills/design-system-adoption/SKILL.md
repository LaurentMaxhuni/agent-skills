---
name: design-system-adoption
description: Build or migrate selected screens using the project's existing components, semantic tokens, and themes. Use when asked to adopt a design system, replace one-off UI with shared components, or build a feature inside an established visual system.
---

# Design system adoption

## Find the existing building blocks

1. Identify the screens and states in scope. Read the local design guidance, tokens, component APIs, variants, and representative screens or stories. Use the project's existing patterns as the starting point when it has no formal component catalog.
2. Match each requested control or layout role to an existing component, composition, or token. Check interactive and accessibility behavior as well as appearance. For a migration, capture the current behavior and any intentional visual differences before editing.

## Adopt the system in the requested screens

- Use the existing components through their public APIs. Use semantic tokens for their intended roles so theme changes continue to work. Compose existing pieces for screen-specific layouts.
- Extend a shared component or token when a genuine gap calls for reuse. Follow its existing extension patterns and check the consumers affected by the change. Keep screen-specific values local to the screen.
- Preserve the requested copy, behavior, and states during a migration. Use the design system's supported generator for managed components when one exists. See [CLI scaffolding](../cli-scaffolding/SKILL.md) when available.

## Verify the result in context

Render the changed screens at relevant sizes and in supported themes, including any explicitly requested theme. Compare migrated controls against the baseline for behavior, interaction states, focus, and keyboard use. If a shared component or token changed, verify representative existing consumers and run the relevant project checks. Report the screens migrated, shared changes, and any relevant state or theme that could not be checked.
