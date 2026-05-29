# Definition Harness

Version: 1.1.0

Definition Harness is a spec-anchored repository harness for keeping software behavior, intent, tests, and operator-facing instructions aligned over time.

It is designed for:

- new repositories that want structured docs from the start
- older repositories that need to adopt structure one scope at a time
- agent-assisted projects where durable in-repo knowledge matters more than prompt-only context

## For Agents

When a user points you at this repository for project rules:

1. Treat this README as the landing page.
2. Read `ADOPTION.md` when the target repo is old, partially documented, or already has `docs/`.
3. Read `documentation/documentation-definition.md` for document types and update rules.
4. Read `documentation/development-flow.md` for planning, validation, and PR closure.
5. Use templates from `templates/` only after adapting paths and validation commands to the target repo.

Do not assume every adopting repository must immediately copy the full structure. Adoption is gradual by scope, not gradual by discipline.

## Quick Start

You can use Definition Harness without checking it out locally. Point your coding agent at this repository URL and tell it how you want to adopt the pattern.

### New Repository

```text
Use Definition Harness from <repo URL> as the documentation and development-flow pattern for this project.

Start by reading its README, ADOPTION.md, documentation/documentation-definition.md, and documentation/development-flow.md.

Then add the minimal starter files to this repo, adapt paths and validation commands to this project's stack, and create the first definition for the highest-risk subsystem.
```

### Existing Repository With Partial Or Messy Docs

```text
Use Definition Harness 1.1 from <repo URL> in scoped-adoption mode.

Do not reorganize the whole docs tree. Keep this repo's existing docs path if it has one.

Pick one high-risk or high-change scope, add local documentation rules for stable vs temporary docs, create or update one behavior definition for that scope, and update tests/validation expectations around the observable claims.
```

### Repository That Already Adopted An Earlier Version

```text
Review Definition Harness 1.1 from <repo URL> and apply only compatible improvements.

Do not rename documentation directories or rewrite existing definitions just to match the new version.

Check whether scoped-adoption or harness-evolution guidance should be referenced by AGENTS.md, README.md, or local documentation rules, and report any compatibility impact before making changes.
```

### Manual Checklist

If you are applying the pattern by hand instead of through an agent:

1. Copy only the starter files you need.
2. Keep the target repo's existing docs path if it already has one.
3. Add repo-specific validation commands to `AGENTS.md` and README.
4. Create the first definition for a high-risk or high-change scope.
5. Require PRs to report validation, risks, and documentation impact.

## Core Model

- `*-definition.md` files describe current behavior, constraints, contracts, and observable outcomes.
- `*-principles.md` files describe stable rationale that should guide future decisions.
- `architecture.md` describes boundaries, ownership, dependency direction, and lifecycle invariants.
- `development-flow.md` keeps docs, code, tests, validation, and PR closure in sync.
- `AGENTS.md` is a concise map for agents, not the full knowledge base.

The governing idea is three-pillar independence:

- docs describe behavior and intent
- code implements behavior
- tests verify behavior

None of the three should silently substitute for another.

## What Is New In 1.1

Version 1.1 adds scoped adoption guidance for older and partially adopted repositories.

The compatibility rule is:

Existing repositories that already use the earlier `documentation/` model do not need to rename directories, rewrite definitions, or restructure their docs.

Version 1.1 adds:

- `ADOPTION.md`: scoped adoption, stable vs temporary docs, and compatibility guidance
- `templates/existing-repo-documentation-definition.template.md`: local docs rules for repos that already have mixed docs
- `templates/adopted-scope.template.md`: one-subsystem adoption task template
- `CHANGELOG.md`: version-level change notes
- `VERSION`: current harness version marker

## Scoped Adoption

Scoped adoption means a repository can adopt the harness one subsystem, workflow, API surface, operator process, or product area at a time.

The scope can be small. The discipline inside that scope should be real.

For an adopted behavior scope:

- create or update one `*-definition.md`
- document current behavior, not an aspirational rewrite
- keep implementation steps and migration history out of definitions
- add or update tests around observable claims
- record validation and documentation impact in the PR
- update the definition when behavior changes later

For rationale-only scopes, use `*-principles.md`. For boundary or ownership changes, update `architecture.md`.

Temporary planning docs such as `*-context.md`, `*-implementation-guide.md`, `*-progress.md`, and `IN_PROGRESS.md` may support work, but they should not become long-term behavior authority.

See `ADOPTION.md` for the full model.

Examples:

- A mature Django app with years of mixed docs can keep `docs/`, then adopt only the homepage splash selector first. That scope gets `docs/homepage-splash-definition.md`, validation expectations, and a rule that future splash behavior changes update the definition.
- A game repo that already has many `documentation/*-definition.md` files can keep its structure unchanged. Version 1.1 only adds optional compatibility and harness-evolution guidance.
- A public API surface can be adopted before the rest of the service. Write `docs/<api>-definition.md`, keep implementation notes out of it, and require endpoint tests to cover the documented response and failure behavior.
- A performance-sensitive browse module can start with principles plus one concrete definition. The PR should include query-count, benchmark, or reproducible workload evidence for the adopted path.

## Repository Layout

```text
AGENTS.md
ADOPTION.md
CHANGELOG.md
POSITIONING.md
VERSION
documentation/
  architecture.md
  code-structure-principles.md
  development-flow.md
  documentation-definition.md
  documentation-principles.md
  harness-evolution-principles.md
  programming-principles.md
templates/
  adopted-scope.template.md
  architecture.template.md
  existing-repo-documentation-definition.template.md
  item-definition.template.md
  principles.template.md
  README-docs-section.template.md
  system-definition.template.md
.github/
  PULL_REQUEST_TEMPLATE.md
examples/
  helpdesk-platform/
```

## Quality Loop

Definition Harness does not replace normal engineering controls.

Each adopting repository should define its own native quality loop:

- typed or schema-validated boundaries
- static analysis and lint rules
- automated tests
- coverage or another change-risk signal where useful
- CI gates
- PR validation and documentation reporting
- domain-specific reproducible workloads when behavior, performance, or reliability needs them

The docs preserve intent and behavior. The toolchain helps prevent silent drift.

## More Detail

- `ADOPTION.md`: how to adopt gradually while preserving compatibility
- `CHANGELOG.md`: version-level changes
- `POSITIONING.md`: why this exists and how it differs from disposable spec workflows
- `examples/helpdesk-platform/`: non-game example documentation
- `documentation/documentation-definition.md`: document types, naming, and update rules
- `documentation/development-flow.md`: planning, validation, and PR closure
- `documentation/harness-evolution-principles.md`: compatibility rules for evolving this harness
