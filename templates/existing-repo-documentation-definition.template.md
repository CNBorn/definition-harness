# Documentation Definition

This document defines the documentation model and update rules for `<docs path>`.

## Scope

- Covers stable behavior, rationale, process, planning, and operator documentation in this repository.
- Keeps existing useful documentation instead of requiring a full docs migration.
- Defines which scopes have adopted Definition Harness rules.

## Documentation Path

- Stable project documentation lives in `<docs path>/`. Temporary working documents are optional and use the repo-local path when enabled.
- `README.md` is the entry file: how to run, development commands, the reading route, validation commands, and a few always-visible constraints.
- `AGENTS.md` is <a relative symlink to `README.md` | a pointer file that names `README.md` | a separate agent entry that does not repeat `README.md`>.
- The entry file only routes. It links to owning definitions and does not restate their steps, parameters, defaults, limits, or constraints.
- Each always-visible constraint is one sentence and a link to its owner.
- The adopted-scope table in this document is the only document index. The entry file links here and does not list definitions.
- Content without an owner, such as code structure or test coverage lists, goes to its owner or stays in code and tests, not in the entry file.
- The entry file uses the documentation language. Do not keep translated copies of entry or definition content.

## Stable Docs

- `*-definition.md`: current behavior, constraints, contracts, and observable outcomes.
- `*-principles.md`: stable rationale that guides future definitions and implementation decisions.
- `*-evaluation-definition.md`: stable criteria, commands, scenarios, tools, or evidence expectations used to evaluate a behavior scope.
- `architecture.md`: boundaries, ownership, dependency direction, and lifecycle invariants.
- `development-flow.md`: planning, validation, documentation, and PR closure rules.
- `agent-workflow-definition.md`: repository-side contract for delegated agent work.
- runbooks: operational procedures and incident response instructions.

Stable docs are allowed to be partial. They are authoritative only for their stated scope.

## Naming And Navigation

- Preserve existing docs paths, filenames, directory structure, and useful navigation during compatible adoption.
- For new docs, prefer a flat directory with at most two semantic naming levels: `<domain>-definition.md` and optional `<domain>-<topic>-definition.md`. Use the same scope prefixes for principles and evaluation definitions when useful.
- Multiword domains and topics do not add levels. Type suffixes do not add levels.
- A shared prefix aids discovery; it does not establish authority. Link applicable system definitions, principles, and cross-domain constraints explicitly.
- Create domain definitions only for actual baseline rules. Topics may stand alone; principles may be shared.
- Unless requested by the user or required by explicit repo-local policy, agents must not create or expand a manual inventory of every Markdown file, including exhaustive lists or tables inside other docs.
- Use focused entry points and related-document links. Adopted-scope tables describe authority and validation boundaries, not a complete file inventory.
- Generated inventories and one-time discovery output are permitted. Do not copy generated listings into stable docs for manual upkeep.
- An opted-in inventory is navigation, not behavior authority.

## Writing And Diagrams

- Use short sentences, active voice, concrete verbs, and one term per concept. These principles are inspired by STE; full ASD-STE100 compliance is not required.
- Remove repeated explanations and empty sections. Keep conditions, exceptions, values, failure behavior, and stable rationale.
- Use tables for comparisons. Use editable Mermaid diagrams when flows or dependencies are clearer than in prose.
- Label what arrows mean. Keep acceptance criteria explicit in text or tables and verify changed diagrams render.
- Keep each rule in one authoritative place and link to it elsewhere.

## Optional Temporary Docs

Default adoption captures final behavior, stable rationale, and reusable evaluation criteria in repository docs, with final validation evidence in the PR. Create the following files only when requested by the user or required by explicit repo-local policy:

- `*-context.md`: feature background, requirements, options, and planning decisions.
- `*-implementation-guide.md`: execution instructions for a specific implementation slice.
- `*-acceptance-contract.md`: completion criteria for a specific active work item.
- `*-progress.md`: active work tracking, handoff notes, blockers, and validation logs.
- `IN_PROGRESS.md`: short-lived state for active multi-step work.

Temporary docs may support work, but they must not become long-term behavior authority. Before closing a feature, move lasting behavior or rationale into the stable docs or runbooks that own it, or into PR history.

Delegation, task duration, multiple iterations, or crossing sessions does not itself require repository progress files. Execution state may stay in the external harness or session. When repository tracking is opted in, `IN_PROGRESS.md` may index a detailed `*-progress.md` artifact. Existing tracking conventions remain valid.

## Adopted Scopes

List each scope that has adopted Definition Harness rules.

| Scope | Stable docs | Validation expectations | Notes |
| --- | --- | --- | --- |
| `<scope>` | `<docs path>/<scope>-definition.md` | `<command or test target>` | `<boundary or owner>` |

## Rules For Adopted Scopes

- Read the relevant definition and principles before changing behavior.
- Update `*-definition.md` when current behavior changes.
- Update `*-principles.md` when stable rationale changes.
- Add or update tests around observable claims in definitions.
- Add or update `*-evaluation-definition.md` only when the scope needs stable scenario, visual, workload, rubric, or operational evidence beyond ordinary tests.
- Ground judgment-heavy rubrics in real examples, repeated failures, or review feedback.
- Record validation commands and documentation impact in the PR.
- Keep implementation steps, file inventories, migration history, and unresolved options out of definitions.

## Rules For Non-Adopted Scopes

- Existing repo practices may continue.
- Prefer adding a definition when a non-adopted scope becomes high-risk, high-change, or hard for agents to reason about.
- Do not create long-lived `*-context.md` files as substitutes for behavior definitions.

## On-Demand Definition Audit

- Run a Definition Audit only when requested by the user or initiated by explicit repo-local policy. It is not a default CI or per-PR gate.
- Use Definition Harness's `definition-audit-definition.md`, or an adapted local contract, for the procedure and report requirements.
- Read selected claims before inspecting implementation. Include applicable system definitions, principles, evaluation criteria, architecture constraints, and workflow rules.
- Record repository state, scope, claim references, implementation evidence, and test evidence. Separate supported claims, conflicts, insufficient evidence, and unclear definitions.
- Report test coverage and unreviewed areas separately. Do not assume code, tests, or documentation is correct when they disagree.
- Report differences before repairs. Keep reports in the session or PR unless repository retention is requested or required.

## Architecture Update Rule

Update `architecture.md` only when boundaries, ownership, dependency direction, or lifecycle invariants change.

Do not add routine implementation detail, file inventories, or low-level step-by-step logic to architecture docs.

## Entry File Update Rule

- Behavior or operation changes update only the definition that owns them.
- A new adopted scope updates only the adopted-scope table.
- Update the entry file only when how to run, development commands, the reading route, or validation commands change.

## Pre-Merge Checklist

- Behavior changes in adopted scopes are reflected in matching definitions.
- Stable rationale changes are reflected in matching principles.
- Stable evaluation criteria changes are reflected in matching evaluation definitions.
- Temporary planning docs are cleaned up or marked as historical.
- Final behavior and evaluation evidence are reviewable without repository progress or handoff files.
- Validation commands were run and recorded.
- The entry file and architecture docs were checked for relevance. The entry file does not restate definition content.
