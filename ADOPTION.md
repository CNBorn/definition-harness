# Adoption Guide

This guide describes how to adopt Definition Harness in a new repository or in an existing repository that already has its own documentation habits.

## Version 1.1 Compatibility Rule

Definition Harness 1.1 is backward-compatible with repositories that already adopted the earlier `documentation/` model.

Existing repositories do not need to rename `documentation/`, rewrite stable definitions, or restructure their docs to use the 1.1 guidance. Version 1.1 adds a clearer scoped-adoption model for older repositories and partially adopted repositories.

## Core Adoption Principle

Adoption is gradual by scope, not gradual by discipline.

A repository may adopt the harness one subsystem, workflow, API surface, operator process, or product area at a time. Once a scope is adopted, that scope should follow the documentation, testing, and validation rules consistently.

This avoids two failure modes:

- forcing a full documentation migration before the repo is ready
- creating loose planning docs that slowly become stale behavior authority

## Adoption Modes

### Full Repository Adoption

Use this mode when the repository is new or already comfortable treating structured documentation as the behavior system of record.

Expected shape:

- `documentation/` or the repository's chosen equivalent contains stable behavior docs
- `AGENTS.md` points agents to the documentation model and validation rules
- PRs report documentation impact and validation evidence
- behavior changes update matching `*-definition.md` files

This is the model used by repos that already look like the original Definition Harness structure. Version 1.1 does not require those repos to change shape.

### Scoped Adoption

Use this mode for older repositories, mixed documentation systems, or teams that want to start with one important area.

Expected shape:

- the repo keeps its existing docs path if it already has one, such as `docs/`
- adopted scopes are listed in the repo-local documentation rules
- each adopted behavior scope has a `*-definition.md`
- stable rationale uses `*-principles.md` when the rationale matters beyond one PR
- companion evaluation definitions are added only when a scope needs stable scenario, visual, workload, rubric, or operational evidence
- temporary planning docs are allowed, but they do not become long-term behavior authority

Scoped adoption is the recommended path for legacy repositories.

## Stable And Temporary Docs

Repo-local documentation rules should distinguish stable docs from temporary docs.

Stable docs:

- `*-definition.md`: current behavior, constraints, contracts, and observable outcomes
- `*-principles.md`: stable rationale that shapes future behavior and implementation decisions
- `*-evaluation-definition.md`: stable criteria, commands, scenarios, tools, or evidence expectations used to evaluate a behavior scope
- `architecture.md`: boundaries, ownership, dependency direction, and lifecycle invariants
- `development-flow.md`: planning, validation, documentation, and PR closure rules
- `agent-workflow-definition.md`: repository-side contract for delegated agent work
- runbooks: operator procedures and incident response instructions

Temporary docs:

- `*-acceptance-contract.md`: completion criteria for a specific active work item
- `*-context.md`: feature background, requirements, options, and decisions captured during planning
- `*-implementation-guide.md`: execution instructions for a specific implementation slice
- `*-progress.md`: work tracking, handoff notes, blockers, and validation logs
- `IN_PROGRESS.md`: short-lived state for active multi-step work

Temporary docs may support work, but stable behavior should be moved into definitions, principles, architecture docs, runbooks, README, or PR history before the work is considered closed.

For delegated agent work, `IN_PROGRESS.md` may act as a short active-work index that points to a detailed `*-progress.md` artifact. The progress artifact should capture enough state for another capable worker to resume without relying on chat history.

## Minimum Rule For An Adopted Scope

For a behavior scope:

1. Create or update one `*-definition.md`.
2. Document current behavior, not an aspirational future state.
3. Keep implementation steps, file inventories, and migration history out of the definition.
4. Add or update tests around the observable claims.
5. Record validation commands and documentation impact in the PR.
6. Update the definition when behavior changes later.
7. Add an evaluation definition only when the scope needs stable scenario, visual, workload, rubric, or operational evidence beyond ordinary tests.
8. For judgment-heavy scopes, base rubric criteria on real review feedback, baseline outputs, or repeated failure patterns.

For a rationale-only scope:

1. Create or update one `*-principles.md`.
2. State stable decision rules, not temporary preferences.
3. Link related definitions when behavior becomes concrete.

For an architecture scope:

1. Update `architecture.md` only when boundaries, ownership, dependency direction, or lifecycle invariants change.
2. Keep routine implementation detail in code, definitions, tests, or PR history.

For delegated agent work:

1. Use a progress artifact when work needs attention-independent progress, multiple implementation/evaluation iterations, handoff, unattended execution, or work across multiple sessions, context windows, or agents.
2. Treat initializer, implementer, evaluator, and closer as work roles, not required agent processes.
3. Keep acceptance contracts temporary unless their criteria become stable evaluation rules.
4. Include outcome, verification, constraints, iteration policy, and error handling in the active goal or acceptance contract.
5. Resolve progress artifacts before closure by deleting them, marking them historical, or moving durable knowledge into stable docs.

## Existing Docs Policy

Do not delete or rename existing documentation just to adopt the harness.

Instead:

- keep useful existing docs
- classify them as stable, temporary, operational, or historical
- add definitions only for scopes that need durable behavior authority
- clean up temporary planning docs after the feature has shipped and stabilized

If the repository already uses `docs/`, keep `docs/`. If it already uses `documentation/`, keep `documentation/`.

## AGENTS.md Guidance

`AGENTS.md` should be a map, not the full knowledge base.

For scoped adoption, `AGENTS.md` should name:

- the docs path
- the repo-local documentation rules file
- the adopted scopes or where to find them
- the validation commands expected for common changes
- any deployment or migration guardrails
- any delegated agent work conventions used by external agent harnesses

Avoid moving full subsystem behavior into `AGENTS.md`. Put stable behavior in definitions.

## PR Closure Rule

Before a PR is ready:

- docs, code, and tests agree for any adopted scope
- temporary planning docs are either cleaned up or clearly marked as historical
- delegated-work progress artifacts are resolved or up to date
- validation commands and results are recorded
- README is updated when setup, commands, user workflows, or operator workflows change
- architecture docs are updated only when boundaries or ownership changed

## Versioning Guidance

Definition Harness versions should preserve adopted repository compatibility unless a breaking change is explicitly called out.

For non-breaking updates:

- add new guidance without requiring existing docs to move
- keep prior file naming valid
- include migration notes only where adoption can improve gradually
- verify that a fully adopted older repo can keep using its current structure

For breaking updates:

- state the breaking change clearly
- provide a migration path
- explain why compatibility could not be preserved
