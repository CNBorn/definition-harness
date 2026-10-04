# Definition Audit Definition

Definition Audit is an on-demand review of agreement between governing documentation, implementation, tests, and other required evidence.
It reports conflicts and uncertainty for a stated scope and repository state.

## Scope

- Include the selected behavior definitions and their applicable system definitions, principles, evaluation definitions, and architecture constraints.
- Include process rules, README instructions, and runbooks when they govern the audited behavior or workflow.
- The name does not exclude principles or other relevant authority. Keep each document's role distinct.
- Default to the requested adopted scope. Audit all adopted scopes only when requested. Do not assume undocumented areas are adopted.
- An audit may cover a rationale-only or process scope. Report which claims can be checked and which require human judgment.

## Invocation

A user or explicit repo-local policy may initiate an audit independently of a code change.
It is not a default CI or per-PR requirement. Ordinary development validation remains required.
Useful triggers include scoped adoption, substantial refactors, release preparation, and suspected drift.

Before inspecting implementation, record:

- requested scope, governing documents, and exclusions
- repository revision and any relevant uncommitted changes
- available validation commands, environments, and evidence
- limits on execution, time, or cost, when supplied

If the scope is unclear, resolve it before claiming complete coverage.
Scope expansion must be explicit. Related documents may be read without claiming their entire scope was audited.

## Audit Procedure

1. Read repository guidance and the selected governing documents. Follow explicit inheritance and related constraints; do not infer authority from filename prefixes.
2. Extract checkable claims before reading implementation. Keep conditions, defaults, exceptions, and failure behavior with each claim. Cite its document and section or line.
3. Identify conflicting or ambiguous documentation. Keep principle-based judgment separate from concrete behavior and architecture requirements.
4. Trace each claim through relevant entry points, configuration, implementation paths, and tests. A keyword match alone is not implementation evidence.
5. Run existing checks or focused, reversible scenarios when permitted and useful. Record commands, results, and what they actually exercised. Report unavailable environments and checks not run.
6. Classify each claim and record evidence limits. Within the selected scope, also report material implemented behavior that lacks a governing definition; do not infer whole-repository documentation requirements.
7. Report findings, coverage, and unresolved decisions. Recommend follow-up separately from the audit result.

Read definitions as statements of current behavior, not as plans for unimplemented features.
When documentation and implementation disagree, do not presume that either is correct.
Use principles, approved decisions, and change history to explain possible causes. Leave unresolved intent decisions explicit.

## Claim Results

| Result | Meaning |
| --- | --- |
| Supported | Inspected evidence supports the claim within the stated conditions. State whether support comes from static inspection, executed checks, or other evidence. |
| Conflict | Evidence demonstrates incompatible documentation, implementation, or test expectations. Cite both sides and the conditions of the conflict. |
| Insufficient evidence | The claim is understood, but available evidence cannot establish agreement or conflict. Explain what is missing. |
| Unclear definition | The governing text is ambiguous, contradictory in meaning, or lacks an observable criterion. State the clarification needed. |

Record test coverage separately: relevant tests found, relevant checks run and their results, or no relevant tests found.
Missing tests do not prove an implementation conflict. Passing tests do not prove every claim.
An unsuccessful source search does not prove absent behavior. Static support does not establish runtime or deployment behavior.
Principle-based findings must cite the decision rule, observed choice, and reasoning. Mark judgment or unresolved tradeoffs explicitly.

## Report Contract

The report must include:

- scope, repository state, governing documents, and exclusions
- a claim-to-evidence table with claim references, results, implementation evidence, and separate test evidence
- actionable findings with observed behavior, expected behavior or principle, impact, evidence, and recommended next action
- documentation conflicts and material behavior without a definition within the selected scope
- commands run, results, and evidence or environments that were unavailable
- coverage: claims reviewed, unresolved claims, and documents or areas not checked
- any scope or execution limits that prevented completion

Use claim references local to the report. Permanent rule identifiers and source/test mappings in definitions are not required.
Locate evidence precisely enough for another reader to inspect it at the recorded repository state.
Do not report an incomplete or inconclusive audit as a clean result.
Even a report with no conflicts must state its evidence and coverage limits; it is not proof of universal conformance.

## Changes And Retention

The audit reports differences. It does not authorize repairs or changes to governing rules.
When the user also requests repairs, capture findings before making changes and verify the affected claims afterward.
Do not rewrite definitions to match code merely to clear a finding.

Keep the report in the session or PR by default. Create a repository report only when requested or required by explicit repo-local policy.
Capture lasting behavior, rationale, and reusable checks in their existing authoritative documents after an agreed correction.
An audit report is evidence, not new behavior authority.

## Boundaries

- Agents, people, or external tools may perform the audit. Separate agents are not required.
- Definition Harness specifies the contract; it does not provide an audit runtime, scheduler, or command.
- Audits complement tests, CI, and code review. They do not replace required validation.
