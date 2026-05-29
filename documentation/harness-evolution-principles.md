# Harness Evolution Principles

This document defines stable principles for evolving Definition Harness itself.

## Intent

Definition Harness should improve without forcing unnecessary churn on repositories that already adopted an earlier version.

The framework may become clearer, stricter, or better documented over time, but compatibility should be an explicit design concern for every version change.

## Principle 1: Preserve Adopted Repository Compatibility

- Existing adopted repositories should not need to rename docs paths, rewrite stable definitions, or restructure working documentation systems for a non-breaking version.
- Full-adoption repositories using `documentation/` remain valid unless a breaking version explicitly says otherwise.
- Scoped-adoption repositories using `docs/` or another established docs path remain valid when their local documentation rules are consistent.

## Principle 2: Additive Guidance Before Migration

- Prefer adding guidance, templates, and clarification over requiring migration.
- When a new concept is introduced, explain how it relates to the previous model.
- Migration guidance should be optional for non-breaking releases and mandatory only for explicitly breaking releases.

## Principle 3: Compatibility Is Tested Against Adoption Shapes

Before changing core rules or templates, evaluate at least these adoption shapes:

- a full-adoption repository with `documentation/`, many definitions, and strict PR documentation rules
- a scoped-adoption legacy repository with an existing `docs/` directory and mixed stable/temporary docs
- a new repository copying the current starter files

The change should not make any valid prior adoption shape invalid unless the release is intentionally breaking.

## Principle 4: Version Changes Need Operator-Facing Notes

- Update `VERSION` when the framework version changes.
- Update `CHANGELOG.md` with the behavior of the version change.
- Update `README.md` when the agent landing path changes.
- Update `ADOPTION.md` when adoption modes, compatibility rules, or migration expectations change.
- PRs that change framework rules or templates should explain compatibility impact.

## Principle 5: Keep Meta-Rules In The Repository

Important rules for evolving the harness belong in repository files, not only in prompts or discussion history.

Use:

- `documentation/harness-evolution-principles.md` for stable evolution principles
- `ADOPTION.md` for adopter-facing compatibility and adoption guidance
- `CHANGELOG.md` for version-level changes
- PR descriptions for one-time migration notes, rejected options, and validation details
