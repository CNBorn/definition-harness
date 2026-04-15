# Definition Harness

A spec-anchored repository harness for making software projects more legible and evolvable for both humans and coding agents.

This kit was extracted from a game repo, but the model is intentionally software-agnostic. It works for APIs, backend services, CLIs, data systems, desktop apps, web apps, internal tools, and games.

It is meant for both:

- greenfield, AI-native repositories
- older pre-agentic repositories that need structure added gradually over time

## What This Is

- A repo-local framework for writing authoritative behavior documentation.
- A lightweight repository harness that keeps intent, behavior, and verification in the same iterative system.
- A starter pack for repositories that need stronger human and agent legibility.

## Why It Exists

Many teams now have two unsatisfying options:

- rely on prompts and tribal knowledge, which does not age well
- adopt a heavy spec-first workflow that fits greenfield work better than messy existing systems

This kit is for the middle path.

It lets a repository grow while gradually accumulating durable knowledge about:

- stable intent
- current behavior
- architectural boundaries
- expected validation

That means spikes, documentation, code, and tests can evolve together instead of living in separate, disposable artifacts.

## Why This Worked For Me

I first used this on a fairly complex video game project built with heavy agent assistance. I did not start with deep knowledge of every game-programming detail, and I did not have full control over every low-level implementation choice. The practical problem was how to keep a complex project on the rails while still moving quickly.

This structure helped because it kept the product-side thinking explicit while giving the LLM room to iterate on the technical side. Principles and definitions captured intent and current behavior in the repo. Types, tests, coverage, CI, and other checks helped keep that freedom from turning into drift.

So far, that combination has worked surprisingly well. It let me keep pushing in a domain I was still learning without turning the project into pure prompt-driven chaos. That is the reason I wanted to publish it as its own repo.

It has limits. It does not replace engineering judgment or validation. But it seems to offer a useful balance: enough structure to keep a project reined in, enough flexibility to iterate fast. It fits greenfield projects naturally, and it can also be added gradually to an existing codebase by starting with one important subsystem.

## What Makes It Distinct

This repo is not just "spec-driven." Its center of gravity is different.

- It is `spec-anchored across the repository`, not only centered on a single feature spec.
- It is `persistent after implementation`; the docs remain part of the operating model after the task ships.
- It uses a `layered documentation substrate`:
  - principles for stable intent
  - definitions for current, testable behavior
  - architecture and process docs for boundaries and workflow
- It treats `docs, code, and tests as independent pillars` that check one another.
- It is `retrofit-friendly`; you can start with one critical subsystem instead of imposing a repo-wide process on day one.
- It works with each repository's native quality tooling instead of prescribing one language stack.

## The Surrounding Quality Loop

The documentation framework is only one part of the larger system.

What makes the approach useful in practice is that it sits inside a broader quality loop:

- typed or schema-validated boundaries
- static analysis and lint rules that encode repo standards
- automated tests
- coverage or another clear signal for change risk on new and modified code
- CI gates
- PR templates and explicit validation reporting
- reproducible workload or scenario validation for domain-specific regressions

In other words, the documentation layer preserves intent and behavior, while the engineering toolchain helps prevent silent drift.

This part of the harness is generalized at the pattern level, not at the tool-name level.

The kit does not require TypeScript, Vitest, ESLint, or any other specific stack.
It requires each adopting repository to define its own native quality loop in those categories.

Examples:

- Python: `mypy` or `pyright`, `ruff`, `pytest`, coverage, CI
- Go: `go test`, `golangci-lint`, race detector, coverage, benchmarks
- Rust: `cargo test`, `clippy`, coverage, CI
- Java/Kotlin: Gradle or Maven checks, JUnit, static analysis, coverage
- Ruby: RuboCop, RSpec or Minitest, coverage, optional type tooling

In the originating project, the language-specific implementation of that broader loop included:

- strict TypeScript with checks like `noUncheckedIndexedAccess`, `exactOptionalPropertyTypes`, and `noImplicitOverride`
- ESLint with TypeScript rules such as `explicit-module-boundary-types` and `no-explicit-any`
- Vitest unit tests and coverage reporting
- patch coverage enforcement with a higher bar on changed code
- CI that runs lint, typecheck, test coverage, and domain-specific deterministic regression checks
- PR templates that require validation and documentation reporting
- reproducible validation workloads for performance- and behavior-sensitive changes

That combination is important. The docs are not carrying quality alone.

## What This Is Not

This is not:

- just prompt engineering
- just a heavier feature-spec workflow
- only for new AI-native projects
- a replacement for normal engineering quality controls

This repo uses `harness` in a broader engineering sense: a lightweight set of structures and feedback loops that help a repository become more legible and governable over time.

In current agentic usage, "harness" usually means one of these:

- An agent harness or scaffold that gives a model tools, state, and an execution loop.
- An evaluation harness that runs tasks, graders, and aggregated scoring.

That terminology is used explicitly by Anthropic in its agent eval guidance, and OpenAI uses "harness engineering" to describe the broader practice of making repositories legible and enforceable for agents. This repo is best understood as the repository knowledge and documentation layer inside that broader practice, not as a model runtime harness or eval runner.

References:

- [Anthropic: Demystifying evals for AI agents](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents)
- [OpenAI: Harness engineering](https://openai.com/index/harness-engineering/)
- [OpenAI: AGENTS.md and open standards](https://openai.com/index/agentic-ai-foundation/)

## Core Model

The kit is built around a few simple rules:

- Definitions describe current behavior and constraints.
- Principles describe stable rationale.
- Architecture docs describe boundaries and ownership, not implementation trivia.
- Development flow keeps docs, code, and tests moving together.
- `AGENTS.md` points agents toward the real sources of truth instead of trying to be one giant manual.

The governing idea is three-pillar independence:

- Docs describe behavior and intent.
- Code implements behavior.
- Tests verify behavior.

Each pillar checks the others. None of them should silently substitute for another.

## Adoption Model

This kit is intentionally incremental.

You do not need to start with a complete specification stack.

For an existing repo, the recommended adoption path is:

1. Pick the highest-risk or highest-change subsystem.
2. Write one system definition and one or two workflow/item definitions.
3. Tighten tests around the observable claims in those docs.
4. Add the update rules to `AGENTS.md`, PR expectations, and `README.md`.
5. Repeat outward over time.

This makes the framework practical for legacy repos, exploratory work, and teams that are still learning the domain while building.

## Positioning

If you need a one-line description:

`Definition Harness is a spec-anchored repository harness that helps software projects accumulate durable intent, behavior, and verification in-repo over time.`

For a longer explanation, see [POSITIONING.md](POSITIONING.md).

## Repository Layout

```text
AGENTS.md
POSITIONING.md
documentation/
  architecture.md
  code-structure-principles.md
  development-flow.md
  documentation-definition.md
  documentation-principles.md
  programming-principles.md
templates/
  architecture.template.md
  item-definition.template.md
  principles.template.md
  README-docs-section.template.md
  system-definition.template.md
.github/
  PULL_REQUEST_TEMPLATE.md
examples/
  helpdesk-platform/
```

## Quick Start

1. Copy `AGENTS.md`, `documentation/`, `.github/PULL_REQUEST_TEMPLATE.md`, and optionally `templates/` into the target repo.
2. Rewrite `documentation/architecture.md` for the target system.
3. Author the first few system definitions for your highest-risk or highest-change domains.
4. Add project-specific validation commands to `AGENTS.md` and `README.md`.
5. Require docs, tests, and validation evidence in PRs.
6. Expand to adjacent subsystems over time instead of trying to document everything at once.

If your org standard prefers `docs/` instead of `documentation/`, that is fine. Keep naming and references consistent everywhere if you rename it.

## How To Use

Use this harness as a lightweight operating model, not as a one-time document import.

The normal loop is:

1. Define or update the relevant principles and definitions for the area you are changing.
2. Implement or revise the behavior in code.
3. Add or update tests around the observable claims in those docs.
4. Run the repo's mechanical checks.
5. Merge only when docs, code, and tests all still agree.

For a new repo:

1. Start with `architecture.md`, `documentation-definition.md`, and `development-flow.md`.
2. Add one or two system definitions for the most important product or platform domains.
3. Add project-specific validation commands to `AGENTS.md` and `README.md`.
4. Require PRs to report validation, risks, and documentation changes.
5. Expand the documentation surface as the codebase grows.

The point is not to fully spec everything up front. The point is to make durable intent and current behavior easier to find, review, and update as the project evolves.

## How To Incorporate It Into An Existing Repo

This harness is designed to be added gradually to an already-running codebase.

Recommended approach:

1. Pick one subsystem that is high-risk, high-churn, poorly explained, or important to the product.
2. Write a small `architecture.md` update if the system boundaries are unclear.
3. Add one system definition and, if useful, one or two workflow/item definitions for that subsystem.
4. Base those docs on the current behavior, not on an idealized future rewrite.
5. Add or tighten tests around the claims you just wrote down.
6. Update `AGENTS.md`, the PR template, and the README so future changes are expected to keep those docs current.
7. Repeat on adjacent subsystems over time.

A few practical rules help:

- do not try to document the whole repo in one pass
- do not start with the least important subsystem just because it is easier
- do not write aspirational docs that the code does not actually satisfy
- prefer current-state clarity first, cleanup and redesign second

If the repo already has `docs/`, architecture notes, ADRs, or runbooks, keep them. This harness does not require a reset. Fold the useful parts into a clearer structure and update rules over time.

## Suggested First Project Docs

Start with these before trying to document everything:

- `documentation/architecture.md`
- `documentation/<core-system>-definition.md`
- `documentation/<core-workflow>-definition.md`
- `documentation/<core-scope>-principles.md`
- `documentation/programming-principles.md`

Good early candidates are:

- authentication
- billing
- background jobs
- sync/import pipelines
- operator workflows
- public API behavior

## Why This Helps Agents

Agents work better when repository knowledge is structured, discoverable, and current.

- Small, scoped docs are easier to retrieve than one giant instruction file.
- Definition naming creates a natural bridge between code, tests, and docs.
- The same structure also helps new human contributors reason about the repo.

This is why the kit includes both `AGENTS.md` and a structured `documentation/` directory.

The same structure also helps humans work effectively in codebases where they do not yet fully know the domain. That matters for agent-assisted work, but it also matters for ordinary teams inheriting legacy systems.

Agents also benefit from surrounding mechanical checks. A repository becomes much safer for agent-driven work when clear documentation is combined with typed interfaces, tests, lint, coverage, and CI feedback.

## Included Example

`examples/helpdesk-platform/` shows the same documentation model applied to a support software product instead of a game. It demonstrates:

- a system definition
- a workflow/item definition
- a principles document
- an architecture reference

## Publishing

This folder is already initialized as its own git repo. To publish it:

1. Create a remote repository.
2. Add the remote.
3. Push `main`.

There is no build step. The value is in the files and conventions.
