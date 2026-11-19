---
name: bug-hunt
description: Reproduce, isolate, and explain software defects across application code, tests, integrations, and runtime behavior. Use for regressions, crashes, incorrect output, race conditions, flaky tests, intermittent failures, and root-cause investigations. Apply a focused fix and regression check when the user requests a repair.
---

# Bug Hunt

Move from symptom to evidence to root cause. Do not treat a plausible code smell as the confirmed defect.

## Choose the scope

For a diagnosis-only request, reproduce and isolate the issue using read-only inspection and existing diagnostics. Then report the cause or the best-supported hypothesis, the evidence, and any verification gaps. Stop there. Proceed to Fix and Verify when the user requests a repair.

## Hard rules

These requirements bind every run of this skill. Adapt a rule only when it is genuinely impossible to satisfy, and report the adaptation and its reason in the handoff. Silently skipping a rule is a failed task.

- Complete inspection and isolate the cause before editing to fix the defect.
- Touch only what the request requires. Justify any scope expansion explicitly.
- Never claim a check ran when it did not, cite a file, line, or result not actually observed, or describe unverified behavior as verified.
- A root cause claim needs support from a reproduction or a discriminating experiment. Label anything less as an unconfirmed hypothesis.
- When fixing, add a regression test that fails before the fix and passes after it. Skip this only when genuinely impractical, and name the reason in the handoff.
- To verify a fix, run the focused regression, surrounding suite, static checks, and build, and record their actual outcomes. Repeat formerly intermittent reproductions enough to confirm the fix.

## Stop and ask

When reproducing requires access to systems, data, credentials, or environments you do not have, ask rather than assume. Ask before a fix that changes public behavior or an interface beyond repairing the defect.

## Reproduce

1. Read repository instructions, current changes, and the relevant execution path.
2. Capture the exact command, input, environment, state, and observed failure.
3. Find the smallest reliable reproduction. If the issue is intermittent, run controlled repetitions and record frequency instead of guessing.
4. Establish expected behavior from tests, contracts, documentation, history, or nearby implementation.

If reproduction is blocked, continue with safe inspection and clearly label hypotheses as unconfirmed.

## Isolate

- Trace data and control flow across the failure boundary.
- Reduce the input, code path, or dependency set while preserving the failure.
- Compare working and failing cases.
- Check recent diffs and history when they can identify a regression boundary.
- When the user requests a repair, add temporary diagnostics at narrow boundaries if needed. Remove those diagnostics before handoff.
- For concurrency bugs, reason about ordering, ownership, cancellation, retries, idempotency, and shared state.
- For flaky tests, distinguish a product race from leaked test state, nondeterministic data, timing assumptions, or infrastructure noise.

Write a causal hypothesis that explains every important observation. Test the hypothesis with a discriminating experiment before editing broadly.

## Fix

1. Change the earliest trustworthy point that violates the intended contract.
2. Prefer the smallest coherent fix that addresses the class of failure, not only the captured input.
3. Preserve unrelated behavior and user changes.
4. Add or strengthen a regression test that fails before the fix and passes after it when practical.
5. Remove temporary probes and debug artifacts.

Avoid weakening assertions, adding arbitrary delays, swallowing errors, or retrying a deterministic failure unless the product contract explicitly requires those behaviors.

## Verify

Run the focused regression first, then the relevant surrounding suite, static checks, and build. Repeat formerly intermittent reproductions enough to increase confidence. Inspect the final diff for accidental scope growth. Verification is a completion gate: record actual outcomes and report failures verbatim.

## Handoff

Report the root cause or unconfirmed hypothesis, the evidence for it, any verification gaps, and residual risk. When a repair was requested, also describe the fix, how it addresses the cause, and the actual regression check results.
