---
name: code-cleanup
description: Simplify and tidy existing code while preserving observable behavior. Use when asked to clean up, remove dead code, reduce duplication, improve naming, organize imports, tighten types, clarify control flow, or remove stale comments without undertaking a broader architectural refactor.
---

# Code Cleanup

Improve clarity with a small diff and a strict behavior-preservation boundary.

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

Run formatting, lint, type checks, and the most relevant tests. For deletions, search for references after the edit. Review the diff for accidental API changes, reordered side effects, or broad formatting noise.

## Handoff

Summarize what became simpler, identify any deliberately deferred structural issue, and list the checks run. Do not describe unchanged behavior as a new feature.
