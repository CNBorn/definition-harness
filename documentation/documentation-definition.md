# Documentation Definition

This document defines the documentation model and authoring rules for `documentation/`.

## Scope

- Covers system and workflow documentation under `documentation/`.
- `README.md` is governed separately for quickstart, setup, commands, and user/operator-facing workflows.
- `AGENTS.md` is the entrypoint for agent instructions, not the full knowledge base.
- `ADOPTION.md` governs compatibility and scoped adoption for existing repositories.

## Document Types

Not all files in `documentation/` are definitions or principles. The core document types are:

- **Definition** (`*-definition.md`): normative behavioral requirements for a system, service, workflow, interface, or policy surface.
- **Principle** (`*-principles.md`): stable rationale that shapes definitions and implementation decisions.
- **Architecture reference** (`architecture.md`): high-level boundaries, ownership rules, dependency direction, and integration model.
- **Process document** (`development-flow.md`): how work is planned, executed, verified, and closed.

Related root-level documents:

- `ADOPTION.md`: repository adoption modes, compatibility expectations, and stable-vs-temporary doc rules for existing repositories.

## Documentation Entities

### Definition

A Definition is a normative statement set that describes behavior, constraints, terminology, and observable outcomes for a scope.

- A definition is authoritative for its scope.
- Definitions exist at system level or item/workflow level.
- Definitions may reference governing principles and adjacent definitions.

### Principle

A Principle is a stable intent rule that explains why definitions are shaped the way they are.

- Principles guide decisions when implementation details evolve.
- Principles do not replace concrete behavioral rules.
- Multiple definitions can share the same principle set.

## Definition Levels

### System Definition

Describes rules for a broad subsystem or business domain.

- Scope examples: authentication, billing, job orchestration, search, import/export, notifications.
- System definitions set baseline rules and constraints for all items within the domain.
- File naming: `<system>-definition.md`.

### Item Or Workflow Definition

Describes a specific workflow, interface surface, authored policy, or concrete instance inside a broader system.

- Scope examples: password reset flow, invoice finalization job, webhook retry policy, CLI `deploy` command, customer import pipeline.
- Item/workflow definitions apply system-level rules to concrete behavior.
- Item/workflow definitions must not violate inherited system-level rules.
- If an item needs behavior that conflicts with system rules, update the system definition first.

## Principles File Convention

- Principles docs follow `<scope>-principles.md` naming.
- Not every system needs its own principles file; shared principles can cover multiple definitions.
- `documentation-principles.md` governs documentation authoring itself.
- `programming-principles.md` governs implementation patterns when the repo chooses to include it.

## Writing Rules

- Document only the current state of the product and codebase.
- Write in present tense and keep behavior descriptions factual.
- Remove or rewrite stale statements when behavior changes.
- Keep historical notes and migration discussion in PR descriptions or project history, not in definitions.
- When documenting tuned or constrained values, include the constant name and value when practical.
- Use canonical in-code and in-product terminology consistently.
- Keep docs scannable: behavior summary first, key defaults and constraints second.
- Keep `architecture.md` high-level and stable; avoid file-by-file inventories and volatile implementation detail.
- Avoid coupling definition text to source file paths unless the path itself is part of the contract.

## Traceability

- Traceability between docs and tests relies on shared naming and terminology, not mandatory inline cross-references.
- Definition docs do not need to enumerate which tests verify them.
- Tests do not need to name the specific doc they satisfy.
- The mapping should be discoverable: a definition covering "ticket routing" should naturally map to code and tests that use the same terms.

## Canonical Paths

- `documentation/` for behavior, architecture, and process docs.
- `README.md` for setup, commands, and user/operator-facing workflow instructions.
- `AGENTS.md` for concise navigation and project instructions for agents.
- `ADOPTION.md` for adopting the harness in new, existing, or partially adopted repositories.

Adopting repositories may use `docs/` or another established docs path. If they do, keep references consistent and record the local path in `AGENTS.md` and the repo-local documentation definition.

## Scoped Adoption

Definition Harness may be adopted one scope at a time.

- A scope can be a subsystem, workflow, API surface, operator process, or product area.
- A repository does not need complete documentation coverage before one scope can adopt the harness.
- Once a scope is adopted, its definitions, principles, tests, and validation expectations should be kept aligned consistently.
- Existing full-adoption repositories that already use the `documentation/` model do not need to change structure for scoped adoption.

## Temporary Planning Docs

Temporary planning docs may exist, but they are not long-term behavior authority.

Examples:

- `*-context.md`
- `*-implementation-guide.md`
- `*-progress.md`
- `IN_PROGRESS.md`

Before closing work, move lasting behavior or rationale into definitions, principles, architecture docs, README, runbooks, or PR history.

## Update Rules

When behavior changes, verify the relevant definition docs are still accurate.

- Definition docs use `<scope>-definition.md` naming so matching docs can be found by scope name.
- When changing a system, scan `documentation/` for the matching definition files by terminology.
- Check `architecture.md` when boundaries or ownership rules change.
- Check `README.md` when commands, setup, or operational workflows change.
- Check `AGENTS.md` when project guidance or validation expectations change.

## Pre-Merge Checklist

- Search for stale names, outdated workflows, or renamed concepts and remove old references.
- Confirm docs match the current implementation, not an intermediate local state.
- Verify `tested` and `documented` independently before merge.
