---
name: refactor
description: Restructure existing code to improve boundaries, responsibilities, dependency direction, extensibility, testability, or maintainability while preserving intended behavior. Use when asked to refactor, extract modules, split large components, redesign internal APIs, untangle dependencies, or migrate an implementation incrementally.
---

# Refactor

Change structure deliberately while keeping behavior controlled and reviewable.

## Frame the refactor

1. Read repository instructions and inspect current work before editing.
2. State the concrete structural problem: mixed responsibilities, unstable dependency direction, duplicated policy, poor test seam, oversized module, or another observable cost.
3. Define invariants that must remain stable, including public APIs, data formats, error semantics, side effects, and performance-sensitive behavior.
4. Identify success criteria that can be checked in the resulting code. Avoid vague goals such as making code cleaner.

## Build a safety net

- Locate existing tests at the public or behavioral boundary.
- Add characterization coverage before structural movement when important behavior is not protected.
- Capture representative edge cases, not implementation details.
- Use type checks, contracts, snapshots, or golden data where they are appropriate and stable.

## Design the target shape

Choose boundaries around cohesive responsibilities and stable concepts. Make dependency direction explicit. Prefer small interfaces at real seams over speculative abstraction layers.

Plan incremental steps in which the code remains runnable:

1. Introduce the seam or target abstraction.
2. Move one responsibility or caller at a time.
3. Verify after each meaningful step.
4. Remove the obsolete path only after all consumers move.
5. Tighten names, visibility, and duplication after the structural change works.

Use adapters or temporary compatibility layers when they reduce migration risk, and remove them before completion unless they serve an ongoing compatibility contract.

## Control scope

- Keep product behavior changes separate unless explicitly requested.
- Avoid mixing broad formatting, dependency upgrades, or unrelated cleanup into the refactor.
- Preserve performance characteristics unless a measured tradeoff is intentional.
- Do not replace one large module with many thin pass-through files that obscure flow.
- Stop expanding once the stated structural problem and success criteria are satisfied.

## Verify

Run focused tests throughout, then the relevant full suite, lint, types, and build. Compare important outputs or behavior before and after. Review the final dependency graph and diff for cycles, leaked internals, dead compatibility code, and accidental API change.

## Handoff

Describe the old and new boundaries, the preserved invariants, migration or compatibility decisions, and the checks performed. Call out follow-up work only when it is genuinely outside the agreed scope.
