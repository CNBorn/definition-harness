# Definition Audit For <Scope>

Use this task for an on-demand audit. Adapt paths and limits to the target repository.
Read Definition Harness's `documentation/definition-audit-definition.md`, or the adapted local contract, before starting.

## Request

Run a Definition Audit for `<adopted scope or explicitly requested set of scopes>`.
Read local AGENTS instructions and documentation rules. Record the repository revision and relevant uncommitted changes.
State the scope, governing documents, exclusions, and any execution limits before claiming coverage.

## Review

1. Read the selected definitions and applicable system definitions, principles, evaluation definitions, architecture constraints, and operator or process instructions before inspecting implementation.
2. Extract checkable claims with their conditions, defaults, exceptions, and document references. Keep principle-based judgment distinct from observable behavior requirements.
3. Trace each claim through relevant implementation paths, configuration, and tests. Run relevant available checks within the permitted environment and record what they exercised.
4. Report supported claims, conflicts, insufficient evidence, and unclear definitions. Record test coverage separately.
5. Within the selected scope, report material implemented behavior without a governing definition. Report documentation conflicts and unresolved intent decisions without assuming which pillar is wrong.

## Deliverable

Report findings in this session or PR. Do not create repository report files unless separately requested or required by explicit local policy.
Include a claim-to-evidence table, actionable findings, commands and results, evidence limits, and coverage of reviewed and unreviewed areas.
Missing tests are not proof of incorrect implementation. Passing tests or static inspection are not proof of all runtime behavior.
If limits prevent completion, report the audit as partial.

Capture findings before any repairs. This task requests an audit only; propose corrections as follow-up work.
