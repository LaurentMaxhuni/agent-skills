---
name: api-contract-change
description: Make an intentional change to an API request, response, status, event, or schema and carry it through implementation, code generation, and consumers. Use when adding or modifying externally observable API behavior.
---

# API contract change

## Locate the source of truth

1. Find the authoritative contract, its producer, and its known consumers. Depending on the stack, the contract may live in an OpenAPI document, protocol definition, GraphQL schema, event schema, or typed route declarations.
2. Identify what should change and what existing consumers should still observe. Check input defaults, optional or missing fields, response shape, status and error behavior, and version constraints that matter to the request.
3. Determine whether producers and consumers can update together. When old consumers will remain, preserve compatibility or use the project's versioning or migration approach for an explicitly requested breaking change. Record consumers whose upgrade timing is unknown.

## Carry the change through

- Update the contract in its authoritative location and make implementation, validation, and serialization agree with it. Preserve existing authorization behavior unless the request changes it.
- Run the repository's supported CLI or code generation script to refresh managed clients and types. Inspect the generated diff and update affected in-repo callers, fixtures, and examples. See [CLI scaffolding](../cli-scaffolding/SKILL.md) when available.
- Keep the change limited to the requested contract and the work consumers need to use it. For mixed-version deployment, identify any required release order or compatibility window.

## Verify producer and consumer behavior

Exercise the changed API at its public entry point and through a real consumer or its integration test where available. Check representative valid and invalid inputs, the response or error shape, and cases with optional values present and absent when relevant. When older clients must keep working, test a previous client version or an unchanged consumer fixture against the new API. Mark older-client compatibility unverified if you cannot exercise it. Run relevant schema, generation, and consumer checks. Report the contract change, verified consumers, and any compatibility or rollout gap.
