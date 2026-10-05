# Documentation Definition

This document defines document types, writing rules, and update rules for `documentation/`.

## Scope And Paths

- `documentation/` holds behavior, rationale, architecture, evaluation, and process docs.
- `README.md` is the entry file. It covers how to run, development commands, the reading route, and validation commands.
- `AGENTS.md` is the agent entry. It may be a symlink to `README.md`. See [Entry File](#entry-file).
- `ADOPTION.md` defines adoption modes and compatibility.

Keep an adopting repository's existing docs path. Record it in the entry file and the local documentation definition.

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

### Shallow Naming

For new documentation, prefer a flat directory and at most two semantic naming levels: domain and optional topic.
Keep existing paths, filenames, and local naming conventions in adopted repositories.

| Scope | Definition | Optional principles |
| --- | --- | --- |
| Domain | `<domain>-definition.md` | `<domain>-principles.md` |
| Topic within a domain | `<domain>-<topic>-definition.md` | `<domain>-<topic>-principles.md` |

For example, `authentication-definition.md`, `authentication-session-definition.md`, and `authentication-password-reset-definition.md` share a domain prefix.
Multiword domains and topics do not add semantic levels. Document-type suffixes, including `evaluation-definition`, do not add levels either.

- Use stable domain terms. Do not encode source layout, numeric ordering, or a deeper category chain in filenames.
- A shared prefix groups documents for discovery. It does not establish authority or inheritance.
- State applicable system definitions under `Inherits From` or an equivalent explicit link. Name related principles and cross-domain constraints in the document.
- Each stated inheritance relationship applies the system rules to the item's scope. Related links alone do not imply inheritance.
- Create a domain definition only when it has baseline rules to own. A topic may stand alone.
- Shared principles may govern several definitions. A topic does not need its own principles file.
- Apply consistent terms in the document's language. Existing naming conventions do not require translation.

### Entry File

The entry file routes readers to rules. It does not restate them. [Small Routing Entry](documentation-principles.md#small-routing-entry) gives the rationale.

Entry duties are roles, not files:

| Role | Content |
| --- | --- |
| Human entry | Purpose, setup, how to run, and development command invocations |
| Agent entry | Reading route, validation commands, and the few constraints that every session must see |

One file may perform both roles. The recommended layout is one entry file:

| Layout | Status |
| --- | --- |
| `README.md` holds both roles. `AGENTS.md` is a relative symlink to it. | Recommended. Not required. |
| `README.md` holds both roles. `AGENTS.md` is a pointer file that names `README.md`. | Valid when the repository cannot store symlinks. |
| `README.md` holds the human role. A separate `AGENTS.md` holds the agent role. | Valid. Neither file repeats the other. |

Ownership:

- A definition owns each user or operator workflow, operation, value, or limit that it describes. The entry file links to that definition and may show the command that starts the workflow.
- The entry file must not restate steps, parameters, defaults, limits, or constraints that a definition owns.
- The entry file describes a workflow directly only when no definition owns it, such as installation and development commands.
- Each always-visible constraint is one sentence and a link to the document that owns it.
- The local documentation definition, through its adopted-scope table when one exists, is the only document index. The entry file links to it and does not list definitions.
- Content without an owner does not go in the entry file. Move it to the document that owns it, or leave it to code and tests. Examples are code structure, test coverage lists, generated file names, and per-feature descriptions.
- Write the entry file in the repository's documentation language, which is the language of its definitions. Do not keep a translated copy of the entry file or of definition content.
- Other tool-specific entry paths, such as `CLAUDE.md`, may also be relative symlinks to `README.md`.

Update the entry file only for the changes listed in [Update And Review](#update-and-review).
To shrink an existing entry file, follow [Shrink An Existing Entry File](../ADOPTION.md#shrink-an-existing-entry-file).

Symlink limits:

- A Windows checkout without `core.symlinks` enabled writes `AGENTS.md` as a text file that contains `README.md`. Agents that read this file then open `README.md`.
- Raw-file URLs return the link target, not the content. Point remote readers at `README.md`.
- A repository can check the link in validation: `test "$(readlink AGENTS.md)" = README.md`.

### Navigation And Inventories

The entry file routes readers to rules and to the local documentation definition.
Unless the user requests one or explicit repo-local policy requires one, agents must not create or expand a manually maintained inventory of every Markdown file.
This rule applies to standalone indexes and exhaustive tables or lists inside other documents.

- Use a short, task-oriented set of entry points and explicit related-document links.
- Adopted-scope tables may record authority and validation boundaries. They do not need to enumerate every document in a scope.
- Generated inventories and one-time discovery output are permitted. Do not copy generated listings into stable docs for manual upkeep.
- Preserve existing navigation during compatible adoption. Do not delete or reorganize it solely to adopt this guidance.
- An opted-in inventory remains navigation. It does not define behavior or replace the linked authority.

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
Definition audits may build claim-to-evidence mappings for a run. Permanent rule IDs or source/test inventories are not required.
See [Definition Audit](definition-audit-definition.md) for the audit contract.

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
Before closure, move lasting behavior, rationale, and evaluation rules into the stable docs or runbooks that own them.
Keep one-time decisions in PR history. Delete working files unless they are intentionally retained as history.

## Update And Review

When behavior changes, search docs by scope terminology and check the relevant definitions.

| Change | Check |
| --- | --- |
| Behavior, defaults, or contracts | Matching definitions |
| Stable rationale | Matching principles |
| Checks, rubrics, or evidence requirements | Matching evaluation definitions |
| Boundaries, ownership, dependencies, or lifecycle | `architecture.md` |
| User/operator workflows or operations that a definition owns | That definition only |
| New adopted scope | Adopted-scope table only |
| How to run, development commands, reading route, or validation commands | Entry file. See [Entry File](#entry-file). |

Before merge, remove stale terminology and confirm docs match the final implementation.
Verify `tested` and `documented` separately.
