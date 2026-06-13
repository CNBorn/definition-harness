# Definition Harness

Current version is tracked in `VERSION`.

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
5. Read `documentation/agent-workflow-definition.md` when work is expected to span multiple sessions, agents, or unattended execution.
6. Use templates from `templates/` only after adapting paths and validation commands to the target repo.

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
Use Definition Harness from <repo URL> in scoped-adoption mode.

Do not reorganize the whole docs tree. Keep this repo's existing docs path if it has one.

Pick one high-risk or high-change scope, add local documentation rules for stable vs temporary docs, create or update one behavior definition for that scope, and update tests/validation expectations around the observable claims.
```

### Scoped Adoption For One Existing Scope

```text
Use Definition Harness from <repo URL> to adopt only <scope name> in this existing repository.

First inspect the current docs, code, tests, AGENTS.md, README, and PR template. Do not reorganize unrelated docs or adopt the whole repo.

Create or update the local documentation rules so <scope name> is listed as an adopted scope. Then create or update one current-state definition for <scope name>, identify the validation commands or tests that should protect it, and make the smallest routing updates needed so future PRs keep that scope's docs, code, and tests aligned.
```

### Repository That Already Adopted An Earlier Version

```text
Review Definition Harness from <repo URL> and apply only compatible improvements.

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
- `development-flow.md` defines when planning, docs, tests, validation, and PR closure must be checked together.
- `agent-workflow-definition.md` defines the repository-side contract for long-running agent-assisted work.
- `AGENTS.md` is a concise map for agents, not the full knowledge base.

The governing idea is three-pillar independence:

- docs describe behavior and intent
- code implements behavior
- tests verify behavior

None of the three should silently substitute for another.

## What Adoption Sets Up

Adoption should leave the target repository with a small set of explicit boundaries:

- where stable docs live, such as `documentation/` or an existing `docs/`
- which docs are stable authority and which are temporary planning notes
- which scopes are adopted now, and which remain under existing repo practice
- which validation commands prove changes in adopted scopes
- which progress, acceptance, or evaluation artifacts are used for long-running work
- when `AGENTS.md`, README, architecture docs, definitions, principles, and tests must be updated

For a new repo, the agent usually adds starter docs such as:

- `AGENTS.md`
- `documentation/documentation-definition.md`
- `documentation/development-flow.md`
- `documentation/agent-workflow-definition.md`
- `documentation/architecture.md`
- one first `*-definition.md`
- a PR template with Docs and Validation sections

For an existing repo, the agent should usually add less:

- local documentation rules for the existing docs path
- one adopted-scope definition
- optional principles for stable rationale
- optional evaluation definitions for scopes that need explicit scenario, visual, workload, or operational evidence
- minimal `AGENTS.md`, README, or PR-template routing updates

Existing repositories that already use the earlier `documentation/` model do not need to rename directories, rewrite definitions, or restructure their docs for the current version.

## Scoped Adoption

Scoped adoption is for older repositories that already have code, docs, habits, and partially reliable local knowledge.

Instead of reorganizing the whole repo, choose one subsystem, workflow, API surface, operator process, or product area and make that scope harnessed.

For that adopted scope, define the current behavior, set validation expectations, and make future PRs keep docs, code, and tests aligned. Existing notes and planning docs can stay, but they should not replace the adopted scope's definition.

Examples:

- A mature Django app with years of mixed docs can keep `docs/`, then adopt only the homepage splash selector first. That scope gets `docs/homepage-splash-definition.md`, validation expectations, and a rule that future splash behavior changes update the definition.
- A game repo that already has many `documentation/*-definition.md` files can keep its structure unchanged. The current version only adds optional compatibility and harness-evolution guidance.
- A public API surface can be adopted before the rest of the service. Write `docs/<api>-definition.md`, keep implementation notes out of it, and require endpoint tests to cover the documented response and failure behavior.
- A performance-sensitive browse module can start with principles plus one concrete definition. The PR should include query-count, benchmark, or reproducible workload evidence for the adopted path.

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

## Use With Agent Harnesses

Definition Harness is not an agent runtime. It does not provide model routing, tool loops, schedulers, sandboxes, approval systems, or evaluator services.

It is the repository contract that makes long-running agent runtimes safer, more resumable, and easier to review. External tools can execute against:

- concise `AGENTS.md` routing
- stable definitions and principles
- architecture and development-flow rules
- progress and handoff artifacts
- acceptance contracts
- evaluation definitions
- validation and closure expectations

When the harness describes initializer, implementer, evaluator, or closer roles, those are work roles. They may be performed by one agent, multiple agents, a human operator, CI, browser automation, or an external agent framework.

## More Detail

- `ADOPTION.md`: how to adopt gradually while preserving compatibility
- `CHANGELOG.md`: version-level changes
- `POSITIONING.md`: why this exists and how it differs from disposable spec workflows
- `examples/helpdesk-platform/`: non-game example documentation
- `documentation/agent-workflow-definition.md`: repo-side contract for long-running agent-assisted work
- `documentation/documentation-definition.md`: document types, naming, and update rules
- `documentation/development-flow.md`: planning, validation, and PR closure
- `documentation/harness-evolution-principles.md`: compatibility rules for evolving this harness
