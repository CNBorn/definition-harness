# Agent Workflow Definition

This document defines the repository-side contract for delegated agent work.

## Scope

- Covers final-state documentation, evaluation expectations, responsibility boundaries, and optional working artifacts for delegated work.
- Applies when a task requires attention-independent progress, multiple implementation/evaluation iterations, handoff, unattended execution, or work across multiple context windows, sessions, or agents.
- Does not define an agent runtime, model provider, tool loop, scheduler, sandbox, approval system, or observability backend.

## Behavior Summary

Definition Harness supports delegated agent work by keeping final behavior, stable rationale, and reusable evaluation expectations in repository files. Final validation evidence is recorded in the PR. Execution state may stay in the external harness or session.

External harnesses may use coding-agent products, orchestration frameworks, custom scripts, CI jobs, browser automation, or human operators. The repository contract stays vendor-neutral.

## Core Rules

- Durable behavior, rationale, and evaluation criteria must not depend on chat history as their only source.
- `AGENTS.md` remains a concise map to repository rules, not a full subsystem manual.
- Stable behavior belongs in `*-definition.md`.
- Stable rationale belongs in `*-principles.md`.
- Stable evaluation criteria belong in `*-evaluation-definition.md` when ordinary tests are not enough.
- Repository documentation captures the final implemented state by default, without implementation diaries or progress logs.
- Create progress, handoff, implementation-guide, context, or acceptance-contract files only when the user requests them or an explicit repo-local policy requires them. Task duration, delegation, and multiple iterations or sessions do not themselves opt in.
- Active execution state and future-facing acceptance criteria may stay in the task, external harness, or session. When repository tracking is opted in, use the relevant temporary artifacts.
- Temporary artifacts must be resolved before closure by deleting them, marking them historical, or moving lasting knowledge into stable docs.

## Work Roles

The following roles are responsibility boundaries, not required agent processes.

### Initializer Role

The initializer establishes the starting state for delegated work.

- Reads `AGENTS.md`, `README.md`, `documentation/documentation-definition.md`, `documentation/development-flow.md`, and relevant scope docs.
- Identifies affected definitions, principles, architecture docs, README sections, tests, and validation commands.
- Establishes scope, non-goals, completion criteria, constraints, and validation expectations in the task or external harness.
- Creates or updates a repository progress artifact only when tracking is opted in.

### Implementer Role

The implementer changes the repository in focused slices.

- Works from the delegated goal and relevant definitions, using a progress artifact if tracking is opted in.
- Updates code, tests, docs, and operator instructions together when behavior changes.
- Provides final behavior documentation and validation evidence for review. Per-iteration implementation logs are optional.
- Avoids expanding scope without updating non-goals and affected docs.

### Evaluator Role

The evaluator checks the result independently from implementation.

- Verifies behavior against definitions and acceptance criteria.
- Runs or reviews validation commands, scenario checks, screenshots, logs, benchmark evidence, rubric scores, or other required evaluation artifacts.
- Identifies documentation drift, untested claims, broken workflows, and unresolved risks.
- Calibrates rubric-based judgments against human review when the evaluation depends on taste, quality, usability, or other judgment-heavy criteria.
- Reports findings in the PR, issue, external harness, or review system used by the repository; a progress file is optional.

### Closer Role

The closer prepares work for review or merge.

- Confirms behavior, tests, docs, and validation evidence agree.
- Moves durable behavior or rationale out of temporary artifacts and into stable docs.
- Resolves temporary artifacts if any were created, following repo-local retention rules.
- Records validation, docs impact, risks, and remaining follow-up in the PR.

## Optional Progress Artifacts

Use this section only when the user or repo-local policy has opted into repository progress tracking. External harnesses may handle continuation and handoff without repository progress files.

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
- `Iteration policy`: how to evaluate, revise, and choose the next attempt. Repository attempt logs are optional.
- `Error handling`: when to stop and report instead of continuing.

These fields can live in the task or external harness prompt. Acceptance contracts and progress artifacts are optional repository copies when opted in. Durable behavior belongs in definitions, and stable evaluation rules belong in evaluation definitions.

## Non-goals

- No vendor-specific agent orchestration.
- No required multi-agent implementation.
- No replacement for CI, tests, code review, or operational runbooks.
- No requirement that every task use delegated-work artifacts.
