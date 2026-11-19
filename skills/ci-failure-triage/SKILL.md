---
name: ci-failure-triage
description: Diagnose a specific failing CI run, check, job, or matrix configuration using its logs and pipeline definition. Use for red builds, failures that only happen in CI, and intermittent CI failures. Apply a fix when requested.
---

# CI failure triage

## Locate the causal failure

1. Identify the run, tested commit or merge revision, job, and relevant matrix entry. Inspect the workflow, scripts, and configuration from that revision when available.
2. Read the failing step with its preceding output. Find the earliest failure that explains the job result. Distinguish it from downstream skips, retries, summary errors, and cleanup failures. Check other failed jobs separately when they have independent causes.
3. Record the command, working directory, runner and runtime versions, install and lockfile settings, relevant environment variable names, and the smallest relevant log excerpt. Redact secret values and sensitive log data.

## Reproduce under matching conditions

- Run the failing command on the same revision with matching settings where practical. Record differences in OS, container, tools, or credentials. Treat a pass under different conditions as evidence for that environment only.
- Compare with a nearby successful run to identify candidate causes. Test the leading explanation by holding other conditions steady and varying the suspected factor. For an intermittent failure, compare attempts on the same revision and report what changed, along with the observed frequency when known.
- If logs or conditions are unavailable, report what the evidence supports and identify the missing artifact or environment detail. Keep unconfirmed causes labeled as hypotheses.

## Report or repair

For diagnosis, stop after reporting the failing job and step, cause or hypothesis, reproduction outcome, and next discriminating check if one is needed. For a requested repair, change the smallest causal part and rerun the affected check under matching conditions when possible. A local result and a hosted CI result are separate evidence. Use hosted reruns and deployment actions only within the authorized scope.
