---
name: refactor
description: Restructure existing code to improve boundaries, responsibilities, dependency direction, extensibility, testability, or maintainability while preserving intended behavior. Use when asked to refactor, extract modules, split large components, redesign internal APIs, untangle dependencies, or migrate an implementation incrementally.
---

# Refactor

Change structure deliberately while keeping behavior controlled and reviewable.

## Hard rules

These requirements bind every run of this skill. Adapt a rule only when it is genuinely impossible to satisfy, and report the adaptation and its reason in the handoff. Silently skipping a rule is a failed task.

- Work through the sections above in order. Complete inspection before editing.
- Touch only what the request requires. Justify any scope expansion explicitly.
- Never claim a check ran when it did not, cite a file, line, or result not actually observed, or describe unverified behavior as verified.
- Define invariants and checkable success criteria before moving any code. Refactoring without them is out of scope.
- Keep the code runnable and verify after each meaningful step; never batch the whole movement into a single unverifiable leap.
- Mix in nothing: no formatting churn, dependency upgrades, unrelated cleanup, or product behavior changes.

## Stop and ask

When success criteria cannot be made checkable with available tests or tooling, agree on how to verify before starting. Get explicit approval before any target shape that changes a public interface or observable behavior.

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

Run focused tests throughout, then the relevant full suite, lint, types, and build. Compare important outputs or behavior before and after. Review the final dependency graph and diff for cycles, leaked internals, dead compatibility code, and accidental API change. Verification is a completion gate: run focused checks after every meaningful step and record actual outcomes.

## Handoff

Structure the handoff in four labeled parts: (1) What changed: the old and new boundaries and preserved invariants. (2) Evidence: checks run after each step with outcomes, and diff review results. (3) Gaps: invariants or behaviors no check covered. (4) Follow-ups: only work genuinely outside the agreed scope.
