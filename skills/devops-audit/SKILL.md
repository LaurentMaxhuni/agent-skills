---
name: devops-audit
description: Audit CI/CD, infrastructure as code, containers, deployment configuration, environments, secrets handling, observability, reliability, backups, and operational readiness. Use when asked to review DevOps, delivery pipelines, cloud or container setup, production readiness, release safety, or operational risk. Treat audits as read-only unless the user explicitly asks for changes.
---

# DevOps Audit

Produce an evidence-based operational review. Never expose secret values, mutate infrastructure, deploy, rotate credentials, or change external systems during an audit.

## Map the delivery system

1. Read repository instructions and inventory pipeline definitions, infrastructure code, container files, runtime manifests, environment configuration, and operational documentation.
2. Trace the path from commit to build artifact to deployment and rollback.
3. Identify environments, trust boundaries, credentials, state stores, external dependencies, and manual gates.
4. Distinguish repository evidence from assumptions about the live platform. Inspect live systems only when explicitly authorized and available.

## Audit by control area

### Build and supply chain

Check reproducibility, dependency pinning, provenance, artifact immutability, cache safety, vulnerability scanning, secret exposure, and separation between untrusted code and privileged credentials.

### CI/CD

Check trigger scope, required checks, concurrency, cancellation, retry behavior, promotion between environments, approval gates, rollback, and whether the exact tested artifact is deployed.

### Infrastructure and runtime

Check state management, drift controls, least privilege, network exposure, encryption, resource limits, health probes, graceful shutdown, autoscaling assumptions, and environment parity.

### Reliability and operations

Check service objectives, actionable telemetry, alert ownership, runbooks, dependency failure behavior, capacity, timeouts, retries, idempotency, and safe degradation.

### Data protection and recovery

Check backup coverage, retention, encryption, restore testing, recovery objectives, destructive safeguards, and regional or provider failure assumptions. A configured backup is not evidence of a successful restore.

### Cost and maintainability

Check orphaned resources, unbounded scaling, inefficient retention, duplicated configuration, unsupported versions, ownership, and documentation of exceptional procedures.

## Analyze risk

Trace how a failure propagates across components instead of listing configuration preferences. For each finding, include:

- Severity and affected environment or component
- Evidence with file and line when available
- Trigger and plausible failure sequence
- Impact and blast radius
- Specific remediation and rollout precautions

Use `critical` for an imminent or easily triggered path to severe compromise, irreversible loss, or broad outage; `high` for material production risk; `medium` for meaningful weakness with prerequisites or limited scope; and `low` for defense-in-depth or maintainability improvements.

Do not print credentials or copy secret values into reports. Refer only to secret names and locations.

## Validate and hand off

Recheck high-severity findings, remove duplicates, and note compensating controls. Lead with prioritized findings, then summarize system coverage, unknowns, and recommended sequencing. If no actionable finding is confirmed, state residual risks and unverified live controls.
