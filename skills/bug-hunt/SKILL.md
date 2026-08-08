---
name: bug-hunt
description: Reproduce, isolate, explain, and fix software defects across application code, tests, integrations, and runtime behavior. Use for regressions, crashes, incorrect output, race conditions, flaky tests, intermittent failures, and requests to find a bug's root cause. Add focused regression coverage and avoid unrelated refactoring.
---

# Bug Hunt

Move from symptom to evidence to root cause. Do not treat a plausible code smell as the confirmed defect.

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
- Instrument narrow boundaries with temporary diagnostics when needed; do not leave noisy logging or sensitive data behind.
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

Run the focused regression first, then the relevant surrounding suite, static checks, and build. Repeat formerly intermittent reproductions enough to increase confidence. Inspect the final diff for accidental scope growth.

## Handoff

Report the root cause, why the fix addresses it, the regression coverage added, and the exact verification performed. State plainly when the result remains a likely diagnosis rather than a reproduced fix.
