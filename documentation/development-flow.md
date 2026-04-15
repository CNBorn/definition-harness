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

For work that spans multiple steps or sessions, use `IN_PROGRESS.md` to track:

- agreed scope and decisions
- implementation checklist
- open questions
- pending validation

Keep it current during execution and delete it when the work is complete.

## Required Pre-Merge Checks

- Behavior is implemented and verified.
- Unit-testable or integration-testable changes have adequate coverage.
- Behavior docs are updated and aligned with the current implementation.
- Performance or reliability changes include before/after evidence when relevant.
- Validation commands pass.
- Architecture docs are updated only when boundary or ownership changes require it.
- Temporary planning artifacts are cleaned up.

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
