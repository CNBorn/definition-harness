# Adoption Guide

Adopt Definition Harness in a new repository or one scope of an existing repository.
Adoption is gradual by scope. Each adopted scope follows the docs, tests, and validation rules consistently.

## Compatibility

Version 1.4.1 adds [entry-file](documentation/documentation-definition.md#entry-file) rules. The entry file routes readers and links to the owning definitions, index, and constraints; it does not restate them. One `README.md` with `AGENTS.md` as a symlink is the recommended layout, not a requirement.
Version 1.4 adds shallow naming guidance, focused navigation defaults, and an on-demand Definition Audit contract without requiring migration.
Version 1.3's final-state capture defaults and concise writing guidance remain in effect.
Repositories using the earlier `documentation/` model, including versions 1.1 through 1.3, keep their valid structure.
Do not rename docs paths, rewrite definitions, or delete useful docs just to adopt newer guidance.
Existing repositories may retain explicit policies for working artifacts.
Existing naming, directory structure, and useful navigation remain valid. Do not delete an existing index solely to adopt 1.4.
For new navigation, agents must not create or expand a manual inventory of every Markdown file unless requested by the user or required by explicit local policy.
Adopted-scope tables and focused entry points remain valid. Audits are opt-in and do not add a default CI gate or require report files.
Separate `README.md` and `AGENTS.md` files remain valid. Converting `AGENTS.md` to a symlink is optional.
Existing adopters need no action for 1.4.1. The entry-file rules apply to new and changed entry content.
When a definition changes and the entry file restates it, replace the restatement with a link instead of editing both. A full cleanup is optional; see [Shrink An Existing Entry File](#shrink-an-existing-entry-file).

## Adoption Modes

| Mode | Use when | Required setup |
| --- | --- | --- |
| Full repository | The repo is new or already uses structured behavior docs. | Stable docs, a routing-only entry file, validation commands, and PR docs/validation reporting. |
| Scoped | The repo has existing code, docs, and practices. Recommended for legacy repos. | Keep its docs path. List adopted scopes in local documentation rules. Add definitions and validation for those scopes. |

Complete documentation coverage is not required for scoped adoption.
Unadopted scopes keep existing practices. Prefer adoption when a scope becomes high-risk or hard to understand.

### Starter Files

| Mode | Usual additions |
| --- | --- |
| Full repository | Entry file from `templates/entry-file.template.md` with `AGENTS.md` as a symlink; `documentation-definition.md`; `development-flow.md`; `agent-workflow-definition.md`; `architecture.md`; one first definition; a PR template with Docs and Validation sections |
| Scoped | Local documentation rules from `templates/existing-repo-documentation-definition.template.md`; one adopted-scope definition; principles or evaluation definitions only when needed; the smallest entry-file or PR-template routing update |

Copy only the files you need. Adapt paths and validation commands to the target repository before use.
A manual adoption copies these files, records validation commands once in the entry file, creates the first definition for a high-risk or high-change scope, and requires PRs to report validation, risks, and documentation impact.

### Scoped Adoption Examples

- A mature Django app keeps `docs/` and adopts only the homepage splash selector. That scope gets `docs/homepage-splash-definition.md` and validation expectations.
- A game repository with many `documentation/*-definition.md` files keeps its structure and adopts only the newer writing and diagram guidance.
- A public API is adopted before the rest of the service. Endpoint tests cover the documented response and failure behavior.
- A performance-sensitive module starts with principles and one definition. Its PRs include query-count, benchmark, or workload evidence.

See `examples/helpdesk-platform/` for example documentation of a non-game product.

## Adoption Prompts

Point a coding agent at the Definition Harness repository URL with the prompt for your case. A local checkout is not required.

New repository:

```text
Use Definition Harness from <repo URL> as the documentation and development-flow pattern for this project.
Read its README and ADOPTION.md, then follow the full-repository adoption mode: add the starter files, adapt paths and validation commands to this project's stack, and create the first definition for the highest-risk subsystem.
```

Existing repository with partial or messy docs:

```text
Use Definition Harness from <repo URL> in scoped-adoption mode.
Do not reorganize the whole docs tree. Keep this repo's existing docs path.
Pick one high-risk or high-change scope, add local documentation rules, create or update one behavior definition for that scope, and update tests and validation expectations around its observable claims.
```

One existing scope:

```text
Use Definition Harness from <repo URL> to adopt only <scope name> in this existing repository.
First inspect the current docs, code, tests, entry files (README.md, AGENTS.md), and PR template. Do not reorganize unrelated docs.
Add <scope name> to the adopted-scope table in the local documentation rules, create or update its current-state definition, and identify the tests or validation commands that protect it.
```

Repository that adopted an earlier version:

```text
Review Definition Harness from <repo URL> and apply only compatible improvements.
Do not rename documentation directories or rewrite existing definitions to match the new version.
Report the compatibility impact before making changes. Report where README.md or AGENTS.md restates content that a definition owns, lists definitions, carries content without an owner, or keeps a translated copy. Propose changes using "Shrink An Existing Entry File" in ADOPTION.md. Converting AGENTS.md to a symlink is optional; ask before doing it.
```

For an on-demand audit, use `templates/definition-audit.template.md`.

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
| How to run, development commands, the reading route, and validation commands | Entry file (`README.md`) |
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

## Entry File

Follow [Entry File](documentation/documentation-definition.md#entry-file) for roles, layouts, ownership, and symlink limits.
For a new repository, start from `templates/entry-file.template.md`. The recommended layout links the agent path to it:

```sh
ln -s README.md AGENTS.md
```

In an existing repository, shrink `README.md` to a routing-only entry with the steps below before converting `AGENTS.md` to a symlink.
Agents load the symlinked file in every session. Record the agent entry size before and after the change in the PR.

### Shrink An Existing Entry File

Use these steps when an entry file restates definitions or carries content without an owner. The steps are optional for existing adopters.

1. Review the entry file section by section. For each section, find the document that owns the content.
2. If a definition or another stable document owns the content, delete it from the entry file.
3. If no document owns the content, move it to its owner first, then delete it. Behavior goes to a definition. Code structure, test coverage, and generated file names may stay in code and tests.
4. Replace definition lists with one link to the local documentation definition or its adopted-scope table.
5. Keep one language, the documentation language. Delete a translated copy after its facts are covered.
6. Keep each always-visible constraint as one sentence and a link.
7. Check for orphans. Each document that the removed text linked must still be reachable from its owner, the adopted-scope table, or another stable document. Add the missing link to the owner.
8. Record deleted and moved sections, with their new owners, in the PR.

## PR Closure

- Confirm docs, code, and tests agree for adopted scopes.
- Record validation commands, results, and required evidence.
- Update the entry file only when how to run, development commands, the reading route, or validation commands change. A new scope updates the adopted-scope table.
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
