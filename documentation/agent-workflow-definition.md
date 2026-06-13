# Agent Workflow Definition

This document defines the repository-side contract for delegated agent work.

## Scope

- Covers artifacts, responsibility boundaries, and closure rules that help humans or external agent harnesses resume, evaluate, and review delegated work.
- Applies when a task requires attention-independent progress, multiple implementation/evaluation iterations, handoff, unattended execution, or work across multiple context windows, sessions, or agents.
- Does not define an agent runtime, model provider, tool loop, scheduler, sandbox, approval system, or observability backend.

## Behavior Summary

Definition Harness makes delegated agent work safer by keeping durable knowledge, active execution state, and evaluation expectations in repository files.

External harnesses may use coding-agent products, orchestration frameworks, custom scripts, CI jobs, browser automation, or human operators. The repository contract stays vendor-neutral.

## Core Rules

- Delegated work must not depend on chat history as the only source of state.
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

The initializer establishes the starting state for delegated work.

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
- Runs or reviews validation commands, scenario checks, screenshots, logs, benchmark evidence, rubric scores, or other required evaluation artifacts.
- Identifies documentation drift, untested claims, broken workflows, and unresolved risks.
- Calibrates rubric-based judgments against human review when the evaluation depends on taste, quality, usability, or other judgment-heavy criteria.
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
- rubric scores and reviewer rationale for judgment-heavy behavior
- manual review notes for judgment-heavy behavior

The repository should specify required evidence in the relevant definition, evaluation definition, development flow, README, or PR template.

## Rubric-Based Evaluation

Use rubric-based evaluation when correctness depends on quality judgments that ordinary tests cannot express, such as design quality, originality, writing quality, usability, support response quality, or operator judgment.

A stable rubric should include:

- baseline examples that show the current evaluator target or failure mode
- scoring dimensions with clear definitions
- criteria that are observable in the artifact being reviewed
- examples of acceptable outputs and anti-patterns
- any weights or priority rules that correct known model or team tendencies
- calibration notes that compare evaluator judgments against human review

Rubrics should be earned from review experience. Do not create broad taste rules before seeing real outputs or repeated failure patterns.

## Delegated Goal Shape

When a task is delegated to an external agent harness, the goal should include:

- `Outcome`: the desired end state.
- `Verification`: how completion is proven.
- `Constraints`: what may or may not change.
- `Iteration policy`: what to record or reconsider after each attempt.
- `Error handling`: when to stop and report instead of continuing.

These fields can live in an acceptance contract, a progress artifact, or an external harness prompt. Durable behavior still belongs in definitions, and stable evaluation rules belong in evaluation definitions.

## Non-goals

- No vendor-specific agent orchestration.
- No required multi-agent implementation.
- No replacement for CI, tests, code review, or operational runbooks.
- No requirement that every task use delegated-work artifacts.
