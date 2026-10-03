# Development Flow

This document defines how work is planned, implemented, verified, and closed.

## Scope Guard

Before coding:

- Confirm the goal or release slice and its non-goals.
- Confirm key product, operator, and technical decisions.
- Identify affected definitions and the unit/integration behavior to verify.

## Execution

1. Plan concrete steps in the task or external harness.
2. Implement behavior and update tests in the same change.
3. Update matching definitions and any affected operator instructions.
4. Update `README.md` when setup, commands, or user/operator workflows change.
5. Run repository validation and record commands and results in the PR.

Use `documentation/documentation-definition.md` for writing rules, diagrams, and document update rules.

## Performance And Reliability

For performance, scalability, reliability, or operational changes:

1. Measure a baseline with a reproducible workload.
2. Implement the change with enough instrumentation to explain the result.
3. Run the same workload and confirm it exercised the target path.
4. Record commands, settings, and before/after results in the PR.

## Code Organization And Architecture

- Follow `documentation/code-structure-principles.md` when present.
- Keep behavior unchanged unless the agreed scope includes behavior changes.
- Keep moves and import rewrites focused. Separate ownership cleanup from logic changes.
- Update `architecture.md` only for boundary, ownership, dependency, or lifecycle changes.
- Keep file inventories and routine implementation details out of architecture docs.

## Delegated Work And Continuity

Follow `documentation/agent-workflow-definition.md` for work roles, goal fields, and the evaluation loop.

Repository docs capture final behavior, stable rationale, and reusable evaluation criteria.
The PR records final validation evidence. Plans, attempts, and handoff state may stay in the task, session, or external harness.

Create progress, implementation-guide, context, or acceptance files only when the user requests them or explicit repo-local policy requires them.
Multiple steps, sessions, attempts, or unattended execution do not themselves require repository tracking.

When opted in, `IN_PROGRESS.md` may hold active state or index a `*-progress.md` file.
Keep working files current. Resolve them before closure and move lasting knowledge into stable docs.

### During Iteration

- Read repo guidance, relevant definitions, and the delegated goal. Read progress files only if tracking is enabled.
- Select a focused slice with an observable validation path.
- Update code, tests, and affected docs together.
- Run targeted checks, then required broader validation.
- Evaluate the result and recheck scope before the next attempt.
- Keep evidence for final validation reporting. Repository attempt logs are optional.

### Handoff

Report blockers, incomplete changes, and the next safe action through the session or external harness.
Use repository handoff files only when tracking is enabled. Never describe incomplete work as the final implemented behavior.

## Pre-Merge Checks

- Behavior, tests, and current-state docs agree.
- Unit/integration behavior has adequate coverage.
- Required validation passes; commands, evidence, and unresolved risks are reported.
- Performance/reliability changes include before/after evidence when relevant.
- README and architecture updates follow their scope rules.
- Any working artifacts are resolved under repo-local retention rules.

`tested` and `documented` are separate checks. Progress and handoff files are not required.

## PR Description

| Section | Required content |
| --- | --- |
| Summary | What changed. |
| ELI5 (Branch vs Main) | Plain-language difference from `main`. |
| Scope | Intentional changes. |
| Non-goals | Intentional exclusions. |
| Validation | Commands, results, and required evaluation evidence. |
| Docs | Updated docs, or why none were needed. |
| Risks | Regression surfaces and mitigations. |

Add Metrics or Operations when performance, reliability, migrations, or runbooks need extra explanation.
Framework or template changes must state compatibility impact.
