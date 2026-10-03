# Development Flow

This document describes how feature work should be planned, executed, and closed.

## Scope Guard (Before Coding)

- State whether the work is in scope for the current goal or release slice.
- Explicitly list non-goals to avoid accidental scope creep.
- Confirm key product, operator, and technical decisions before implementation.
- Identify which definitions are likely to be affected before editing code.

## Execution Flow

1. Plan the work in concrete implementation steps.
2. Identify unit-testable and integration-testable behavior before editing code.
3. Implement the behavior.
4. Add or update tests in the same change.
5. Update behavior documentation in the same change.
6. Update `README.md` if commands or user/operator workflows changed.
7. Run the repository's validation commands and record results.

## Performance Or Reliability Change Loop

Use this loop when a change targets performance, scalability, reliability, or operational behavior.

1. Capture a baseline using a reproducible workload or scenario.
2. Implement the change with enough instrumentation to attribute the result.
3. Re-run the same workload and compare before/after behavior.
4. Confirm the workload actually exercised the target path.
5. Record commands, workload settings, and key deltas in the PR.

## Code Organization Changes

- Follow `documentation/code-structure-principles.md` when the repo includes it.
- Keep behavior unchanged unless the change explicitly includes behavioral scope.
- Prefer focused moves plus import rewrites over broad rewrites that mix ownership cleanup with logic changes.

## Architecture Doc Update Rule

- Update `documentation/architecture.md` only when boundaries, ownership rules, dependency direction, or lifecycle invariants change.
- Do not add routine implementation detail, file inventories, or low-level step-by-step logic to `architecture.md`.

## Continuity For Multi-Step Work

Plans, iteration state, and handoff notes may stay in the external harness or session. By default, repository docs capture final behavior, stable rationale, and reusable evaluation criteria; the PR records final validation evidence.

Create `IN_PROGRESS.md`, `*-progress.md`, implementation guides, context files, or acceptance contracts only when requested by the user or required by explicit repo-local policy. Multiple steps, sessions, iterations, or unattended execution do not themselves require repository tracking.

When tracking is opted in, `IN_PROGRESS.md` may hold active state or index a detailed `*-progress.md` artifact. Keep it current and resolve it when work is complete. Move durable knowledge into stable docs before closure.

## Delegated Agent Work

Use this flow when work is delegated to an agent or external harness and requires attention-independent progress, multiple implementation/evaluation iterations, handoff, unattended execution, or work across multiple context windows, sessions, or agents.

### Repository Contract

Delegated agent work should produce final documentation and evaluation evidence that another capable worker can review without relying on chat history.

Before implementation, establish the goal, non-goals, affected scopes, constraints, and validation expectations in the task or external harness. This does not require repository planning or progress files.

### Work Roles

The following roles are responsibility boundaries, not required runtime components:

- `Initializer`: reads repo guidance, maps the affected scope, confirms completion criteria and commands, and identifies the first safe slice. Creates a progress artifact only when opted in.
- `Implementer`: makes focused changes and aligns tests and docs with the final behavior. Provides final validation evidence for review.
- `Evaluator`: independently checks behavior, validation output, docs alignment, and user/operator impact. The evaluator may be a human, CI job, browser automation, external agent, or test harness.
- `Closer`: confirms final behavior is documented, resolves temporary artifacts if any were created, records validation, and leaves the worktree ready for review.

One person or agent may perform multiple roles. These responsibilities apply whether or not repository progress tracking is enabled.

### Iteration Loop

1. Read `AGENTS.md`, the relevant definitions, `development-flow.md`, and the delegated goal. Read an active progress artifact if tracking is opted in.
2. Select one implementation slice with an observable validation path.
3. Implement the slice and update tests, docs, or operator instructions in the same change when needed.
4. Run targeted validation before broad validation.
5. Evaluate the result and select the next action in the external harness or session. Retain evidence needed for final validation reporting; repository attempt logs are optional.
6. Re-evaluate scope before starting the next slice.

### Handoff When Needed

When pausing or handing off delegated work, communicate blockers, incomplete changes, and the next safe action through the external harness or session. Use repository handoff files only when tracking is opted in. Incomplete work must be reported as incomplete; it must not be documented as the final implemented behavior.

## Required Pre-Merge Checks

- Behavior is implemented and verified.
- Unit-testable or integration-testable changes have adequate coverage.
- Behavior docs are updated and aligned with the current implementation.
- Performance or reliability changes include before/after evidence when relevant.
- Final validation evidence and unresolved risks are reported; repository progress or handoff files are not required.
- Validation commands pass.
- Architecture docs are updated only when boundary or ownership changes require it.
- Temporary planning artifacts, if created, are resolved according to repo-local retention rules.

## PR Description Requirements

Every PR description should include:

- `Summary`: short statement of what changed.
- `ELI5 (Branch vs Main)`: plain-language explanation of what is different from `main`.
- `Scope`: what the PR intentionally changes.
- `Non-goals`: what the PR intentionally does not change.
- `Validation`: commands run and results.
- `Docs`: what documentation changed, or an explicit statement that no docs were needed.
- `Risks`: known risks, regression surfaces, and mitigations.

Add `Metrics` or `Operations` sections when the change materially affects performance, reliability, migrations, or operational runbooks.
