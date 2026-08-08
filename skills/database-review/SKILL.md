---
name: database-review
description: Review relational database schemas, migrations, queries, transactions, indexes, constraints, data access patterns, and operational rollout safety. Use when asked to assess SQL or ORM changes for correctness, integrity, concurrency, security, performance, compatibility, or safe deployment. Treat review requests as read-only unless fixes are explicitly requested.
---

# Database Review

Review the database as a stateful production system, not only as static SQL. Do not execute mutations against a live or unidentified database.

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

For every finding, include severity, exact location, failure scenario, evidence, and a concrete remediation. Separate confirmed defects from risks requiring production metrics or an execution plan. Prioritize integrity and availability before micro-optimization.

## Verify

Use isolated or disposable environments for execution plans and migration tests. Run schema checks, database tests, and relevant application tests. State which engine, data scale, and concurrency conditions were not verified.
