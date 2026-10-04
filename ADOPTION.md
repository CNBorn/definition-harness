# Adoption Guide

Adopt Definition Harness in a new repository or one scope of an existing repository.
Adoption is gradual by scope. Each adopted scope follows the docs, tests, and validation rules consistently.

## Compatibility

Version 1.4 adds shallow naming guidance, focused navigation defaults, and an on-demand Definition Audit contract without requiring migration.
Version 1.3's final-state capture defaults and concise writing guidance remain in effect.
Repositories using the earlier `documentation/` model, including versions 1.1 through 1.3, keep their valid structure.
Do not rename docs paths, rewrite definitions, or delete useful docs just to adopt newer guidance.
Existing repositories may retain explicit policies for working artifacts.
Existing naming, directory structure, and useful navigation remain valid. Do not delete an existing index solely to adopt 1.4.
For new navigation, agents must not create or expand a manual inventory of every Markdown file unless requested by the user or required by explicit local policy.
Adopted-scope tables and focused entry points remain valid. Audits are opt-in and do not add a default CI gate or require report files.

## Adoption Modes

| Mode | Use when | Required setup |
| --- | --- | --- |
| Full repository | The repo is new or already uses structured behavior docs. | Stable docs, an `AGENTS.md` map, validation commands, and PR docs/validation reporting. |
| Scoped | The repo has existing code, docs, and practices. Recommended for legacy repos. | Keep its docs path. List adopted scopes in local documentation rules. Add definitions and validation for those scopes. |

Complete documentation coverage is not required for scoped adoption.
Unadopted scopes keep existing practices. Prefer adoption when a scope becomes high-risk or hard to understand.

## What To Capture

Store final behavior, stable rationale, and reusable evaluation criteria in repository docs.
Record final validation evidence in the PR.
Use short, concrete language. Use tables or diagrams when they clarify comparisons or relationships.
Follow the local documentation definition for writing and update rules.

| Knowledge | Stable home |
| --- | --- |
| Current behavior, constraints, and outcomes | `*-definition.md` |
| Stable rationale | `*-principles.md`, when needed |
| Reusable checks, scenarios, or rubrics | `*-evaluation-definition.md`, when ordinary tests are not enough |
| Ownership, boundaries, dependencies, and lifecycle | `architecture.md` |
| Planning, validation, and closure rules | `development-flow.md` |
| Delegated-work responsibilities | `agent-workflow-definition.md` |
| Setup and user/operator workflows | `README.md` |
| Operational and incident procedures | Runbooks |

## Optional Working Docs

Plans and execution state may stay in the task, session, or external harness.
Create context, implementation-guide, acceptance-contract, progress, or handoff files only when requested by the user or required by explicit repo-local policy.
Delegation, task duration, multiple sessions, and repeated attempts do not themselves require these files.

When opted in, `IN_PROGRESS.md` may index a detailed `*-progress.md` file.
Keep the state current and resolve it before closure. Move lasting knowledge into stable docs.
Existing tracking conventions remain valid.

## Adopt One Scope

### Behavior

1. Create or update a definition for current behavior.
2. Keep implementation steps, file inventories, and migration history out of it.
3. Add tests for its observable claims and record validation in the PR.
4. Add the scope to local documentation rules.
5. Keep the definition aligned when behavior changes.

Add principles only when rationale must guide future decisions.
Add an evaluation definition only when stable scenario, visual, workload, rubric, or operational evidence needs a separate contract.
Ground rubrics in real examples and review failures.

For new docs, prefer a flat directory with `<domain>-definition.md` and optional `<domain>-<topic>-definition.md` names.
Use at most two semantic naming levels. Keep explicit links to governing definitions and principles; shared prefixes do not establish inheritance.
Do not create empty domain definitions or rename existing files just to match this convention.

### Rationale And Architecture

- Rationale-only scopes use principles. Link related definitions when behavior becomes concrete.
- Update architecture only when boundaries, ownership, dependency direction, or lifecycle invariants change.

### Delegated Work

Use the initializer, implementer, evaluator, and closer responsibilities in the agent workflow definition.
Roles do not require separate agents.
Define outcome, verification, constraints, iteration policy, and error handling in the task or external harness.
Repository acceptance and progress files remain optional.

## Existing Docs

Keep useful existing documents and classify them as stable, working, operational, or historical.
Add definitions where durable behavior authority is needed.
After work ships, resolve any working docs under local retention rules.

## AGENTS.md

Keep it a map. Include the docs path, local rules file, adopted scopes, validation commands, deployment/migration guardrails, and delegated-work conventions.
Put subsystem behavior in definitions.

## PR Closure

- Confirm docs, code, and tests agree for adopted scopes.
- Record validation commands, results, and required evidence.
- Update README for setup, commands, and user/operator workflow changes.
- Update architecture only for changes within its scope.
- Resolve any working docs or mark them historical.

Final behavior and evidence must be reviewable without repository progress files.
Follow `documentation/development-flow.md` for the PR format.

## Optional Definition Audit

A user or explicit local policy may request a [Definition Audit](documentation/definition-audit-definition.md) for an adopted scope.
Adapt or reference the audit contract and task template; copying them into every adopting repository is not required.
Include the scope's applicable principles, evaluation definitions, architecture constraints, and operator rules.
Read claims first, then compare implementation and evidence. Report conflicts, unclear claims, insufficient evidence, and unreviewed areas.
Keep test coverage separate from conformance findings. Do not assume which pillar needs correction.
Keep the report in the session or PR unless repository retention is requested or required. Perform agreed repairs separately.

## Framework Versions

Non-breaking updates preserve paths, filenames, and valid adoption shapes.
New guidance and templates may be adopted gradually; migration is optional.
Breaking updates must state the incompatibility, explain why it is needed, and provide a migration path.
