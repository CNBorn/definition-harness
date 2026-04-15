# Programming Principles

This document captures implementation principles for application and domain code.

## Prefer Pure Logic For Core Rules

- Put core business or product rules in functions that are as pure and explicit as practical.
- Make inputs and outputs visible.
- Avoid hiding important behavior inside framework callbacks or ambient state when a clear function boundary is possible.

## Keep Orchestrators Thin

- Orchestration layers should mostly gather context, call rule functions or services, apply returned changes, and trigger side effects.
- Do not bury core policy in glue code if it needs direct verification.

## Validate At Boundaries

- Parse and validate data at external boundaries.
- Convert external shapes into internal contracts before domain logic depends on them.
- Keep boundary validation close to the adapter that owns it.

## Unit Test Policy

- Pure rule functions and stable service policies should have unit tests.
- Use integration tests where behavior depends on infrastructure or multiple layers.
- Add tests in the same change as new or modified behavior when the behavior is testable.

## Coverage Policy

- Coverage is a regression guardrail, not a vanity metric.
- Prefer meaningful assertions over coverage-only tests.
- New and changed behavior should keep patch coverage healthy when the repository uses coverage gating.
- If a change cannot reasonably meet a coverage target, explain why in the PR and get maintainer agreement.
