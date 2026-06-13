# Documentation Definition

This document defines the documentation model and update rules for `<docs path>`.

## Scope

- Covers stable behavior, rationale, process, planning, and operator documentation in this repository.
- Keeps existing useful documentation instead of requiring a full docs migration.
- Defines which scopes have adopted Definition Harness rules.

## Documentation Path

- Stable and temporary project documentation lives in `<docs path>/`.
- `README.md` remains the entrypoint for setup, commands, and user/operator-facing workflows.
- `AGENTS.md` remains the concise agent map for repository rules and validation commands.

## Stable Docs

- `*-definition.md`: current behavior, constraints, contracts, and observable outcomes.
- `*-principles.md`: stable rationale that guides future definitions and implementation decisions.
- `*-evaluation-definition.md`: stable criteria, commands, scenarios, tools, or evidence expectations used to evaluate a behavior scope.
- `architecture.md`: boundaries, ownership, dependency direction, and lifecycle invariants.
- `development-flow.md`: planning, validation, documentation, and PR closure rules.
- `agent-workflow-definition.md`: repository-side contract for long-running agent-assisted work.
- runbooks: operational procedures and incident response instructions.

Stable docs are allowed to be partial. They are authoritative only for their stated scope.

## Temporary Docs

- `*-context.md`: feature background, requirements, options, and planning decisions.
- `*-implementation-guide.md`: execution instructions for a specific implementation slice.
- `*-acceptance-contract.md`: completion criteria for a specific active work item.
- `*-progress.md`: active work tracking, handoff notes, blockers, and validation logs.
- `IN_PROGRESS.md`: short-lived state for active multi-step work.

Temporary docs may support work, but they must not become long-term behavior authority. Before closing a feature, move lasting behavior or rationale into the relevant stable docs, README, runbooks, or PR history.

For long-running agent-assisted work, `IN_PROGRESS.md` may be used as a short active-work index that points to a detailed `*-progress.md` artifact. Progress artifacts should capture enough state for another capable worker to resume without relying on chat history.

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
- Add or update `*-evaluation-definition.md` only when the scope needs stable scenario, visual, workload, or operational evidence beyond ordinary tests.
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
- Long-running progress artifacts are resolved or up to date.
- Validation commands were run and recorded.
- README and architecture docs were checked for relevance.
