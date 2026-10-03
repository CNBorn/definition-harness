# Documentation Definition

This document defines the documentation model and update rules for `<docs path>`.

## Scope

- Covers stable behavior, rationale, process, planning, and operator documentation in this repository.
- Keeps existing useful documentation instead of requiring a full docs migration.
- Defines which scopes have adopted Definition Harness rules.

## Documentation Path

- Stable project documentation lives in `<docs path>/`. Temporary working documents are optional and use the repo-local path when enabled.
- `README.md` remains the entrypoint for setup, commands, and user/operator-facing workflows.
- `AGENTS.md` remains the concise agent map for repository rules and validation commands.

## Stable Docs

- `*-definition.md`: current behavior, constraints, contracts, and observable outcomes.
- `*-principles.md`: stable rationale that guides future definitions and implementation decisions.
- `*-evaluation-definition.md`: stable criteria, commands, scenarios, tools, or evidence expectations used to evaluate a behavior scope.
- `architecture.md`: boundaries, ownership, dependency direction, and lifecycle invariants.
- `development-flow.md`: planning, validation, documentation, and PR closure rules.
- `agent-workflow-definition.md`: repository-side contract for delegated agent work.
- runbooks: operational procedures and incident response instructions.

Stable docs are allowed to be partial. They are authoritative only for their stated scope.

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

Temporary docs may support work, but they must not become long-term behavior authority. Before closing a feature, move lasting behavior or rationale into the relevant stable docs, README, runbooks, or PR history.

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

## Architecture Update Rule

Update `architecture.md` only when boundaries, ownership, dependency direction, or lifecycle invariants change.

Do not add routine implementation detail, file inventories, or low-level step-by-step logic to architecture docs.

## README Update Rule

Update `README.md` when setup steps, commands, user workflows, operator workflows, or public usage instructions change.

## Pre-Merge Checklist

- Behavior changes in adopted scopes are reflected in matching definitions.
- Stable rationale changes are reflected in matching principles.
- Stable evaluation criteria changes are reflected in matching evaluation definitions.
- Temporary planning docs are cleaned up or marked as historical.
- Final behavior and evaluation evidence are reviewable without repository progress or handoff files.
- Validation commands were run and recorded.
- README and architecture docs were checked for relevance.
