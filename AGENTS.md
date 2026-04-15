# AGENTS Instructions

## Objective

Keep documentation, code, tests, and operator-facing instructions aligned.

## Core Rules

- Treat `documentation/` as the repository's behavior system of record.
- Follow `documentation/documentation-definition.md` for document types, naming, and update rules.
- Follow `documentation/development-flow.md` for planning, execution, validation, and PR closure.
- When behavior changes, verify the matching `*-definition.md` files are still accurate.
- When stable rationale changes, update the relevant `*-principles.md` files.
- Update `documentation/architecture.md` only when boundaries, ownership, dependency direction, or lifecycle invariants change.
- Update `README.md` when setup steps, commands, user workflows, or operator workflows change.
- Prefer precise, testable statements over aspirational wording.
- Keep important project knowledge in repository files, not only in prompt text or chat history.
- Before opening or updating a PR, run the repo-appropriate validation commands and record the results.

## Recommended Local Customization

Tailor this file to include:

- the repo's canonical validation commands
- any deployment or migration guardrails
- documentation paths if your repo uses `docs/` instead of `documentation/`
- product-specific instructions that agents repeatedly need
