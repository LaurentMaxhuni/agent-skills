---
name: code-cleanup
description: Simplify and tidy existing code while preserving observable behavior. Use when asked to clean up, remove dead code, reduce duplication, improve naming, organize imports, tighten types, clarify control flow, or remove stale comments without undertaking a broader architectural refactor.
---

# Code Cleanup

Improve clarity with a small diff and a strict behavior-preservation boundary.

## Hard rules

These requirements bind every run of this skill. Adapt a rule only when it is genuinely impossible to satisfy, and report the adaptation and its reason in the handoff. Silently skipping a rule is a failed task.

- Work through the sections above in order. Complete inspection before editing.
- Touch only what the request requires. Justify any scope expansion explicitly.
- Never claim a check ran when it did not, cite a file, line, or result not actually observed, or describe unverified behavior as verified.
- Capture baseline check results before editing and compare against them afterward. Cleanup never ships with skipped or failing checks.
- Delete only what is proven unused across runtime paths, dynamic loading, configuration, templates, and external consumers.
- Make zero behavior and zero public-interface changes. Route that need to refactoring and tell the user instead of crossing the boundary silently.

## Stop and ask

When a requested cleanup would change observable behavior or a public interface, stop and get explicit agreement before proceeding. When confidence that code is unused is incomplete, keep the code and note the uncertainty instead of deleting.

## Define the boundary

1. Read repository instructions and inspect the working tree before editing.
2. Identify the exact files or subsystem in scope and the checks that define current behavior.
3. Separate mechanical cleanup from semantic change. If a requested cleanup requires behavior or public API changes, surface that boundary and treat it as refactoring work.

## Clean in low-risk passes

Prefer changes such as:

- Remove proven-dead imports, variables, branches, helpers, files, and dependencies.
- Replace duplicated local expressions with a clear shared value or helper when that reduces cognitive load.
- Simplify nested control flow with guard clauses and explicit names.
- Tighten types without adding casts that merely silence the checker.
- Align naming and organization with repository conventions.
- Remove comments that restate code; retain rationale, invariants, and non-obvious constraints.
- Normalize formatting through the project's formatter rather than manual churn.

Keep abstractions proportional. Do not extract a helper used once unless it names a meaningful concept or materially simplifies the caller. Do not combine unrelated cleanup across the repository merely because it is nearby.

## Preserve behavior

- Keep public interfaces, serialized shapes, error behavior, ordering, timing assumptions, and side effects stable.
- Confirm code is unused across runtime paths, dynamic loading, configuration, templates, and external consumers before deleting it.
- Preserve user-authored changes and generated-file workflows.
- Split uncertain or behavioral changes from safe cleanup so each can be reviewed independently.

## Verify

Run formatting, lint, type checks, and the most relevant tests. For deletions, search for references after the edit. Review the diff for accidental API changes, reordered side effects, or broad formatting noise. Verification is a completion gate: record actual before-and-after outcomes and report failures verbatim.

## Handoff

Structure the handoff in four labeled parts: (1) What changed: what became simpler and why it is safe. (2) Evidence: checks run with before-and-after outcomes, and reference searches performed for deletions. (3) Gaps: behavior paths no check covered. (4) Follow-ups: deliberately deferred structural issues. Do not describe unchanged behavior as a new feature.
