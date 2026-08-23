---
name: database-review
description: Review relational database schemas, migrations, queries, transactions, indexes, constraints, data access patterns, and operational rollout safety. Use when asked to assess SQL or ORM changes for correctness, integrity, concurrency, security, performance, compatibility, or safe deployment. Treat review requests as read-only unless fixes are explicitly requested.
---

# Database Review

Review the database as a stateful production system, not only as static SQL. Do not execute mutations against a live or unidentified database.

## Hard rules

These requirements bind every run of this skill. Adapt a rule only when it is genuinely impossible to satisfy, and report the adaptation and its reason in the handoff. Silently skipping a rule is a failed task.

- Never execute mutations, migrations, or destructive statements against a live or unidentified database. Use isolated or disposable environments only, and say which environment produced any plan or measurement.
- Treat destructive or irreversible operations as blocked until scope, safeguards, and rollback are explicit and agreed.
- Separate confirmed defects from risks requiring production metrics or execution plans. Label assumptions when production facts are unavailable.
- Support every finding with evidence at file and line where possible. A statement without location and failure scenario is a question to resolve, not a finding.

## Stop and ask

Stop before implementing any destructive or irreversible migration step whose safeguards are unspecified. Ask when table sizes, traffic patterns, tenancy, or uptime expectations are unknown and the recommendation would change materially depending on them.

## Establish context

1. Read repository instructions and identify the database engine and version, ORM or migration tool, schema source of truth, and deployment model.
2. Determine table sizes, traffic patterns, tenancy model, uptime expectations, and rollback constraints from available evidence. Label assumptions when production facts are unavailable.
3. Inspect both the change and its callers. A query cannot be assessed fully without expected cardinality, frequency, parameter shape, and transaction context.

## Review correctness and integrity

Check:

- Primary keys, foreign keys, uniqueness, nullability, defaults, and domain constraints
- Type choices, precision, collation, time zones, identifiers, and serialization boundaries
- Transaction boundaries, isolation assumptions, lock ordering, retries, and idempotency
- Race-prone read-then-write flows and invariants enforced only in application code
- Cascades, soft deletion, retention, auditability, and tenant isolation
- ORM behavior such as implicit queries, N+1 access, eager loading, and partial updates

## Review performance

- Match indexes to actual filters, joins, ordering, selectivity, and write cost.
- Look for full scans, repeated queries, unbounded result sets, offset pagination at scale, and avoidable round trips.
- Use engine-appropriate plans and representative statistics when available; do not claim a query is slow from syntax alone.
- Consider hot rows, long transactions, connection pool pressure, cache behavior, replication lag, and storage growth.

## Review migrations and rollout

Assess each phase separately:

1. Expand: add compatible structures without breaking old code.
2. Backfill: make work resumable, bounded, observable, and safe under concurrent writes.
3. Switch: deploy code that reads and writes the new shape with a clear compatibility window.
4. Contract: remove old structures only after verifying all consumers and data.

Check lock duration, table rewrites, validation strategy, mixed-version deployments, rollback feasibility, and recovery from partial completion. Treat destructive or irreversible operations as high risk and require explicit scope and safeguards before implementation.

## Report findings

For every finding, include severity, exact location, failure scenario, evidence, and a concrete remediation. Separate confirmed defects from risks requiring production metrics or an execution plan. Prioritize integrity and availability before micro-optimization. Structure the final report in four labeled parts: (1) Findings ordered by severity, each with location, failure scenario, evidence, and remediation. (2) Evidence: checks, plans, and measurements actually performed, and the environment that produced them. (3) Risks and unknowns: what needs production metrics or an execution plan to confirm. (4) Assumptions: every production fact assumed instead of verified.

## Verify

Use isolated or disposable environments for execution plans and migration tests. Run schema checks, database tests, and relevant application tests. State which engine, data scale, and concurrency conditions were not verified. Verification is a completion gate: record the actual outcome of every check and report failures verbatim.
