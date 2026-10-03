# Documentation Definition

This document defines document types, writing rules, and update rules for `documentation/`.

## Scope And Paths

- `documentation/` holds behavior, rationale, architecture, evaluation, and process docs.
- `README.md` covers setup, commands, and user/operator workflows.
- `AGENTS.md` maps agents to repository rules and validation commands.
- `ADOPTION.md` defines adoption modes and compatibility.

Keep an adopting repository's existing docs path. Record it in `AGENTS.md` and the local documentation definition.

## Document Types

| Type | File | Purpose |
| --- | --- | --- |
| Definition | `<scope>-definition.md` | Current behavior, constraints, terms, and observable outcomes. Authoritative for its scope. |
| Principle | `<scope>-principles.md` | Stable rationale and decision rules. Guides definitions without replacing them. |
| Evaluation definition | `<scope>-evaluation-definition.md` | Reusable checks, scenarios, rubrics, and required evidence. Complements behavior definitions. |
| Architecture reference | `architecture.md` | Boundaries, ownership, dependency direction, and lifecycle invariants. |
| Process document | `development-flow.md` | Planning, implementation, validation, and closure rules. |

### Definition Levels

- A system definition sets baseline rules for a domain, such as authentication, billing, or job orchestration.
- An item/workflow definition applies those rules to a specific flow, policy, command, or interface.
- An item/workflow must obey its system definition. Update the system rules before introducing a conflicting behavior.

Definitions may reference shared principles and adjacent definitions. A scope does not need its own principles file.
`documentation-principles.md` governs authoring. `programming-principles.md`, when included, governs implementation.

### Evaluation Definitions

Use a separate evaluation definition when ordinary tests cannot express all required evidence.

- Define scenarios, browser checks, workload measurements, logs, or review criteria as needed.
- For judgment-based review, define observable rubric dimensions, examples, failure patterns, and human calibration. Add weights only when justified.
- Base criteria on real review needs. Keep tools vendor-neutral unless the repo standardizes on one.

## Writing Rules

Document the final implemented behavior, stable rationale, and reusable evaluation criteria. Put final validation results in the PR.
Keep history and migration discussion in PRs or project history.

### Clear Technical Language

Use selected principles from [ASD-STE100](https://www.asd-ste100.org/STE_faq.html). This framework does not require its controlled dictionary or claim STE compliance.

- Use short sentences, active voice, and concrete verbs. Give each sentence one main rule or action.
- When a condition controls an action, state the condition first.
- Use one term for one concept. Preserve canonical product names, code identifiers, and domain vocabulary.
- Name the actor and outcome. Replace vague words such as "appropriately" with observable conditions or values.
- Keep requirements explicit: `must` is required, `should` is recommended, and `may` is permitted.
- Remove filler, repeated explanations, and empty template sections. Preserve exceptions, failure behavior, limits, and rationale.
- Apply these principles in the document's language. Do not shorten text by omitting facts or sentence parts needed for clarity.

Write in present tense. Put the behavior summary first, then defaults and constraints.
Include constant names and values when useful. Rewrite stale claims when behavior changes.
Keep architecture docs high-level. Mention source paths only when they form part of the contract.

### Tables And Diagrams

Use the smallest format that makes the information easy to check.

| Information | Preferred format |
| --- | --- |
| A rule, constraint, or rationale | Short prose or a list |
| Comparable options, roles, states, or condition/result cases | Table |
| Branching flows, dependencies, ownership, or data movement | Diagram when relationships are clearer than in prose |
| Measurements or trends | Chart or table with units and conditions |

- Prefer editable Mermaid diagrams in Markdown for software relationships.
- Label nodes and arrows. Say whether arrows mean calls, data flow, dependencies, or state transitions.
- Show the stable model or workflow. Update a diagram with the rules it represents.
- Replace repeated relational prose with the diagram. Keep conditions, exceptions, and acceptance criteria explicit in text or tables.
- Keep each rule authoritative in one place. Link to it instead of repeating it.
- A simple rule does not need a diagram. Verify diagram syntax and rendered labels when adding or changing one.

## Traceability

Use shared names across docs, code, and tests so the mapping is discoverable.
Definitions need not list individual tests, and tests need not cite document paths.

## Scoped Adoption

A scope may be a subsystem, workflow, API, operator process, or product area.
Complete repository coverage is not required. For each adopted scope, keep definitions, principles, tests, and validation expectations aligned.
Existing full-adoption repositories keep their structure.

## Optional Working Docs

Create working docs only when requested by the user or required by explicit repo-local policy.
Delegation, duration, multiple iterations, or crossing sessions does not itself require these files.
Planning and execution state may stay in the task, session, or external harness.

| File | Optional purpose |
| --- | --- |
| `*-acceptance-contract.md` | Completion criteria for active work. May include future behavior. |
| `*-context.md` | Planning context, options, and decisions. |
| `*-implementation-guide.md` | Instructions for a specific implementation slice. |
| `*-progress.md` | Checkpoints, blockers, validation logs, and handoff state. |
| `IN_PROGRESS.md` | Active state or an index to a progress file. |

Working docs are not long-term behavior authority.
When opted in, progress files must contain enough current state to resume without chat history.
Before closure, move lasting behavior, rationale, and evaluation rules into stable docs, README, or runbooks.
Keep one-time decisions in PR history. Delete working files unless they are intentionally retained as history.

## Update And Review

When behavior changes, search docs by scope terminology and check the relevant definitions.

| Change | Check |
| --- | --- |
| Behavior, defaults, or contracts | Matching definitions |
| Stable rationale | Matching principles |
| Checks, rubrics, or evidence requirements | Matching evaluation definitions |
| Boundaries, ownership, dependencies, or lifecycle | `architecture.md` |
| Setup, commands, or user/operator workflows | `README.md` |
| Agent routing or validation guidance | `AGENTS.md` |

Before merge, remove stale terminology and confirm docs match the final implementation.
Verify `tested` and `documented` separately.
