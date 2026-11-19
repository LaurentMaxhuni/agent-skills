---
name: cli-scaffolding
description: Run the project's supported CLI to initialize repositories, apps, and packages or to generate framework-managed files. Use when starting a project, adding an app or package to a workspace, setting up tool integrations, or adding routes, migrations, or other files covered by a generator.
---

# CLI scaffolding

**Run the supported CLI for project initialization, integration setup, and files the stack expects a generator to create.** Execute the generator and inspect its initial output before editing the generated files.

Write a requested standalone HTML file or similar self-contained artifact directly when it needs no project setup, even in an empty directory. Follow the same approach for source files the stack expects developers to author by hand. If the request also includes project setup, run the initializer for that setup.

## Select and run the generator

1. Inspect repository instructions, the destination, and any existing manifests, lockfiles, or workspace configuration. Use the user's chosen stack and versions. In an existing project, follow the established package manager and use the repository's generator when it defines one. Otherwise use the framework or tool's official CLI. For a new Node.js project, use `pnpm` when available unless the user or repository specifies a different manager.
2. Confirm the exact command and flags in the installed CLI's help or the official docs for the selected version. Use the CLI for each supported setup step, including project initialization, integration setup, and generator-managed files. Use the package manager's CLI for dependency changes so it updates the manifest and lockfile together.
3. Execute the command in the intended directory with the requested options. Inspect the destination first. If the generator would overwrite existing files, use its supported merge mode or generate into an empty staging directory and reconcile the output without overwriting existing work.

## Handle a blocked command

If a required generator command fails, inspect the error and any partial output before retrying. Try a supported invocation that fits the project when available. If the required scaffolding still cannot be generated, report the attempted command or missing CLI capability and leave that step blocked. Continue any independent work within scope. Manual scaffolding requires the user's explicit authorization.

Creating equivalent starter files through an editor, patch, shell file writes, or a custom script is manual scaffolding. An install or build command run afterward does not count as generation.

## Customize and verify

Inspect the generated files and workspace changes before editing them. Then implement the requested application code and customize generated files as needed. Run the project's relevant verification commands, such as a build or smoke test. In the handoff, record the scaffold commands actually executed, the verification results, and any blocked steps.
