---
name: dependency-upgrade
description: Upgrade a requested dependency or dependency group with the project's package manager, apply necessary migrations, and verify the affected behavior. Use for targeted library, framework, tooling, or transitive dependency upgrades.
---

# Dependency upgrade

## Establish the target

1. Identify the affected package or workspace, its declared and resolved versions, and the callers that rely on it. For a transitive dependency, trace which direct package brings it in.
2. Use the requested version or range. If the request gives a goal without a version, select a supported version that meets it and record the choice. Check the upstream migration or release notes for the version range being crossed and verify runtime, peer dependency, and configuration requirements that affect this project.
3. Capture relevant baseline check results when practical. Keep the upgrade scoped to the named dependency and changes it requires.

## Apply the upgrade

- Run the repository's supported package manager command in the affected workspace. For Node.js work, follow the repository's package manager instructions and use `pnpm` when available unless the project requires a different manager. Let the package manager write and update the lockfile.
- For a transitive update, prefer a compatible upgrade of the direct dependency. Use the repository's supported override mechanism if the transitive version needs one, and record why it was necessary.
- Apply the documented migration steps that affect actual callers and configuration. Run a supported migration or code generation CLI when the project provides one.
- Review the manifest and lockfile diff together. Confirm the intended resolved version and trace collateral changes such as peers or additional versions to the requested upgrade. If resolution drifts outside scope, diagnose it with the package manager and regenerate with a narrower command when available. Report any remaining unrelated drift as unresolved.

## Verify the upgrade

Confirm the updated lockfile works through the project's normal install or lockfile check. Use the lockfile diff to verify upgrade scope. Run relevant tests, build or type checks, and an exercise of the behavior most exposed to the upgrade. Record the previous and new versions, the commands run, collateral changes and their causes, and any remaining compatibility or verification gap.
