# Agent Skills

[![skills.sh](https://skills.sh/b/LaurentMaxhuni/agent-skills)](https://skills.sh/LaurentMaxhuni/agent-skills)

A focused collection of reusable skills for improving software quality. Each skill is intentionally narrow: it defines a practical workflow, safety boundaries, verification expectations, and a concise handoff format without prescribing a specific framework or toolchain.

## Skills

| Skill | Use it for |
| --- | --- |
| [`frontend-polish`](skills/frontend-polish/SKILL.md) | Refining visual hierarchy, consistency, interaction states, and perceived quality |
| [`frontend-audit`](skills/frontend-audit/SKILL.md) | Producing an evidence-backed frontend quality review without silently changing code |
| [`responsive-fixer`](skills/responsive-fixer/SKILL.md) | Diagnosing and fixing layout failures across viewport sizes and input modes |
| [`accessibility-pass`](skills/accessibility-pass/SKILL.md) | Improving semantics, keyboard use, focus, forms, contrast, and assistive-technology support |
| [`bug-hunt`](skills/bug-hunt/SKILL.md) | Reproducing, isolating, fixing, and regression-testing software defects |
| [`code-cleanup`](skills/code-cleanup/SKILL.md) | Simplifying code and removing clutter while preserving behavior |
| [`refactor`](skills/refactor/SKILL.md) | Restructuring code safely when boundaries, responsibilities, or dependencies need to change |
| [`database-review`](skills/database-review/SKILL.md) | Reviewing schemas, migrations, queries, integrity, performance, and operational safety |
| [`devops-audit`](skills/devops-audit/SKILL.md) | Auditing CI/CD, infrastructure, containers, reliability, observability, and recovery |

## Install

Copy or symlink any directory under `skills/` into the skills directory used by your agent. Keep the directory name unchanged so its metadata and invocation name remain aligned.

For Codex, a typical user-level destination is:

```text
~/.codex/skills/<skill-name>/
```

## Use

Invoke a skill explicitly when you want predictable routing:

```text
Use $bug-hunt to reproduce and fix the intermittent checkout failure.
Use $frontend-audit to review this dashboard and prioritize the findings.
```

Skills may also be selected automatically when a request matches the description in a skill's YAML frontmatter.

## Design principles

- Inspect the repository and its local instructions before acting.
- Preserve unrelated work and existing product intent.
- Separate evidence from inference and prioritize root causes.
- Make the smallest coherent change that satisfies the request.
- Verify in proportion to risk and report any validation gaps honestly.
- Treat audits as read-only unless the user also asks for implementation.
