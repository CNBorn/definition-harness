# Adopt Definition Harness For <Scope>

Use this task when adopting Definition Harness for one subsystem, workflow, API surface, operator process, or product area in an existing repository.

## Goal

Make `<scope>` easier for humans and agents to change by giving it durable behavior documentation, clear validation expectations, and a local update rule.

## Non-goals

- Do not document the whole repository.
- Do not rename the repository's docs directory just for this task.
- Do not turn implementation notes or migration history into stable behavior rules.
- Do not rewrite unrelated docs.

## Steps

1. Inventory existing docs and code terminology for `<scope>`.
2. Identify whether the repo already has local documentation rules.
3. Create or update `<docs path>/<scope>-definition.md` for current behavior.
4. Create or update `<docs path>/<scope>-principles.md` only if stable rationale needs to guide future changes.
5. Add `<scope>` to the adopted-scope list in the repo-local documentation rules.
6. Add or update tests for the observable claims in the definition.
7. Update `AGENTS.md` only if agents need a new routing rule or validation command.
8. Update `README.md` only if setup, commands, user workflows, or operator workflows changed.
9. Record validation and docs impact in the PR.

## Definition Requirements

The definition should include:

- scope and non-goals
- behavior summary
- current rules and constraints
- inputs, triggers, or public surfaces
- state or contract boundaries
- defaults, limits, or policy values when relevant
- verification notes

The definition should not include:

- file-by-file implementation inventories
- temporary options that were rejected
- migration history
- instructions for one specific coding pass

## Completion Criteria

- The adopted scope has at least one stable definition.
- Any needed principles are captured separately.
- Tests or validation targets align with the definition's observable claims.
- The repo-local documentation rules list the scope as adopted.
- Temporary planning docs are not the only place where lasting behavior is described.
