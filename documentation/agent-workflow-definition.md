# Agent Workflow Definition

This document defines the repository-side contract for long-running agent-assisted work.

## Scope

- Covers artifacts, responsibility boundaries, and closure rules that help humans or external agent harnesses resume, evaluate, and review work.
- Applies when a task spans multiple context windows, sessions, agents, or unattended execution periods.
- Does not define an agent runtime, model provider, tool loop, scheduler, sandbox, approval system, or observability backend.

## Behavior Summary

Definition Harness makes long-running agent work safer by keeping durable knowledge and active execution state in repository files.

External harnesses may use coding-agent products, orchestration frameworks, custom scripts, CI jobs, browser automation, or human operators. The repository contract stays vendor-neutral.

## Core Rules

- Long-running work must not depend on chat history as the only source of state.
- `AGENTS.md` remains a concise map to repository rules, not a full subsystem manual.
- Stable behavior belongs in `*-definition.md`.
- Stable rationale belongs in `*-principles.md`.
- Stable evaluation criteria belong in `*-evaluation-definition.md` when ordinary tests are not enough.
- Active execution state belongs in `IN_PROGRESS.md` or `*-progress.md`.
- Future-facing acceptance criteria belong in temporary acceptance contracts until they are implemented or discarded.
- Temporary artifacts must be resolved before closure by deleting them, marking them historical, or moving lasting knowledge into stable docs.

## Work Roles

The following roles are responsibility boundaries, not required agent processes.

### Initializer Role

The initializer establishes the starting state for long-running work.

- Reads `AGENTS.md`, `README.md`, `documentation/documentation-definition.md`, `documentation/development-flow.md`, and relevant scope docs.
- Identifies affected definitions, principles, architecture docs, README sections, tests, and validation commands.
- Creates or updates the active progress artifact.
- Records scope, non-goals, assumptions, open questions, and first implementation slice.

### Implementer Role

The implementer changes the repository in focused slices.

- Works from the active progress artifact and relevant definitions.
- Updates code, tests, docs, and operator instructions together when behavior changes.
- Records what changed, what was validated, and what remains.
- Avoids expanding scope without updating non-goals and affected docs.

### Evaluator Role

The evaluator checks the result independently from implementation.

- Verifies behavior against definitions and acceptance criteria.
- Runs or reviews validation commands, scenario checks, screenshots, logs, benchmark evidence, or other required evaluation artifacts.
- Identifies documentation drift, untested claims, broken workflows, and unresolved risks.
- Records findings in the progress artifact, PR, issue, or review system used by the repository.

### Closer Role

The closer prepares work for review or merge.

- Confirms behavior, tests, docs, and validation evidence agree.
- Moves durable behavior or rationale out of temporary artifacts and into stable docs.
- Cleans up temporary progress artifacts or marks them historical.
- Records validation, docs impact, risks, and remaining follow-up in the PR.

## Progress Artifact Requirements

A progress artifact should be enough for another capable worker to resume the task.

It should include:

- goal and non-goals
- current state
- affected docs and adopted scopes
- implementation checklist
- validation commands and latest results
- open questions and blockers
- files or areas touched
- latest handoff note
- next recommended action

## Evaluation Evidence

Evaluation evidence should match the risk of the change.

Examples:

- unit or integration test output
- typecheck, lint, or build output
- reproducible workload results
- benchmark before/after data
- browser or UI scenario checks
- screenshots or videos for visual workflows
- logs or traces for operational behavior
- manual review notes for judgment-heavy behavior

The repository should specify required evidence in the relevant definition, evaluation definition, development flow, README, or PR template.

## Non-goals

- No vendor-specific agent orchestration.
- No required multi-agent implementation.
- No replacement for CI, tests, code review, or operational runbooks.
- No requirement that every task use long-running work artifacts.
