# Positioning

## Short Version

Definition Harness is a spec-anchored repository harness for making software projects legible and evolvable over time.

It is not only for greenfield AI-native projects. It is designed so older repositories can add structure gradually, subsystem by subsystem, without adopting a heavy process all at once.

## The Problem

Many repositories have one of these failure modes:

- important intent lives in prompts, chat logs, or people's heads
- implementation moves faster than durable documentation
- tests verify behavior, but the repository cannot clearly explain what the behavior is supposed to be
- specs exist only as temporary planning docs and disappear after implementation

These problems hurt both humans and agents.

Humans lose context and make local changes without enough system understanding.
Agents can move quickly, but without durable in-repo guidance they drift, overfit to local patterns, or produce changes that are hard to review.

## The Core Idea

This kit treats the repository itself as the place where durable product and engineering knowledge should live.

The model is:

- `principles` capture stable intent
- `definitions` capture current, testable behavior
- `architecture` captures boundaries and ownership
- `development flow` keeps docs, code, and tests evolving together
- `AGENTS.md` acts as a map, not as an oversized manual

The goal is not just better prompting. The goal is a codebase that gradually becomes easier to reason about.

Just as important: this documentation layer is meant to live inside a larger quality system, not replace one.

## What Makes It Different From Typical Spec-Mode Workflows

Many spec-driven workflows are centered on the lifecycle of a piece of work:

`idea -> spec -> plan -> tasks -> implementation`

That is useful, but it is not the main focus here.

This kit is centered on the lifecycle of repository knowledge:

`intent -> behavior -> implementation -> verification -> maintenance`

The difference matters.

- In many spec-mode systems, the feature spec is the center.
- In this kit, the repository's long-lived knowledge layer is the center.

That makes the framework:

- more persistent
- more maintainable
- more suitable for refactors and long-term operation
- more useful for future humans and future agent runs

## Why "Spec-Anchored"

This framework is best described as `spec-anchored`.

The definitions are not disposable planning artifacts. They remain in the repository and continue shaping:

- maintenance
- refactors
- tests
- reviews
- future agent behavior

The docs are part of the operating model of the repository, not just pre-coding paperwork.

## Why Call It A Harness

If you use the word `harness` here, use it carefully.

In current agentic terminology, `agent harness` usually means the runtime scaffold that gives a model tools, state, and an execution loop. `evaluation harness` usually means the infrastructure that runs tasks and graders.

This repo is neither of those.

It is closer to a `repository harness` or `engineering harness`:

- a lightweight set of structures
- feedback loops
- naming conventions
- update rules
- quality gates

Together, those make the repository safer and more legible as it grows.

## Why It Works For Legacy Repositories

This approach does not require a perfect greenfield setup.

You can adopt it gradually:

1. Start with one unstable or high-value subsystem.
2. Write a small number of principles and definitions.
3. Align tests with the new behavioral claims.
4. Make future changes update those docs.
5. Expand outward over time.

That makes it practical for:

- inherited codebases
- partially documented systems
- exploratory projects
- teams still learning the domain

## Relationship To Quality Tooling

This framework does not replace engineering controls such as:

- typed or schema-validated boundaries
- static analysis and linting
- automated tests
- coverage or another change-risk signal
- CI enforcement

It works with them.

The repository harness helps the project preserve intent and behavior.
The engineering toolchain helps prevent that behavior from degrading silently.

Together, they create a more stable environment for both human and agent contribution.

This part is generalized by function, not by specific vendor or language tool.

Every adopting repository should define its own native toolchain for those roles.

Examples:

- Python: type checker or schema validation, linter, `pytest`, coverage, CI
- Go: `go test`, linter, race detector, benchmarks, CI
- Rust: compiler checks, `clippy`, `cargo test`, coverage, CI
- JVM projects: build checks, static analysis, JUnit, coverage, CI

In the originating project, one concrete implementation of that broader pattern included:

- strict TypeScript compilation
- ESLint with explicit TypeScript boundary rules
- Vitest unit testing
- coverage reporting plus stricter patch-coverage checks
- CI gates for lint, typecheck, coverage, and deterministic regression validation
- PR templates that require explicit validation and documentation reporting
- reproducible workload and scenario-based validation for performance- and behavior-sensitive changes

That example matters because it shows the real shape of the method:

not "documentation instead of engineering rigor,"
but documentation combined with mechanical checks and domain-specific validation loops.

## Practical Value

In practice, this approach is useful when:

- you want agents to move quickly without losing the plot
- you are working in a domain you do not fully know yet
- you need a way to preserve what has been learned from spikes and iteration
- you want the codebase to become more understandable over time instead of less

That is the real promise of the kit:

not heavier process for its own sake, but a way for a software project to keep accumulating usable intent, behavior, and verification as it grows.
