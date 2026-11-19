---
name: first-run-check
description: Verify a project's README, quickstart, or onboarding instructions from a clean environment through actual startup or first successful invocation. Use to find missing prerequisites, stale commands, hidden configuration, or setup steps that rely on a warm checkout.
---

# First-run check

## Start from the reader's environment

1. Identify the documented setup path and target revision, OS, and runtime. Verify it in a clean, disposable checkout or environment with the documented prerequisites and fresh project state. Record any preinstalled tool, reused cache, or platform difference that could hide a setup requirement. If only a configured checkout is available, report its results as partial evidence and mark clean setup unverified.
2. Inspect documented prerequisites, environment templates, and setup scripts before running them. Use local or explicitly authorized test services. Record required configuration names without exposing values, and use the documented package manager unless repository or user instructions require another.
3. Follow the documented sequence and capture the first blocker with the exact failing command and a short sanitized diagnostic. If a higher-priority project instruction conflicts with a documented command, record the conflict and test the supported command as a separate attempt.

## Verify the first real outcome

- After setup, run the documented start command or first example. Confirm an observable result such as a reachable page, expected health response, or command output. Use the configured path and port from the project or its runtime output.
- If you use an extra prerequisite, corrected command, or undocumented setup step, record it separately and verify the result after that change. A successful workaround verifies the workaround.
- Stop any service you started for the check when it is no longer needed. Keep changes to project files within the user-requested scope. For a verification request, report documentation gaps. For a requested documentation fix, verify the revised steps from a clean state.

Report the environment, commands and outcomes, first blocker, and evidence of startup or the first successful invocation. State which setup paths still need a check.
