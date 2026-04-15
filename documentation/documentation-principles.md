# Documentation Principles

This document captures the guiding principles for documentation under `documentation/`.

## Three-Pillar Independence

Documentation, code, and tests are independent pillars that check each other.

- Documentation describes what the system should do and why.
- Code implements behavior.
- Tests verify behavior.
- Each pillar is authoritative in its own domain and does not duplicate another's responsibility.
- When documentation and runtime behavior disagree:
  - code and tests usually move together, so the most common case is a stale definition
  - a failing test derived from a definition claim is a valuable signal that behavior may have drifted from intent

## Current-State Only

Documentation describes the system as it exists now, not as it used to be or might become later.

- Write in present tense.
- Remove or rewrite stale statements when behavior changes.
- Keep migration notes, tradeoffs, and historical context in PR descriptions or design history, not in active definitions.

## Implementation Decoupling

Definitions describe behavior and constraints, not internal file layout.

- Do not couple definition text to source paths or transient module names.
- Definitions should survive a refactor without needing major rewrites.
- `architecture.md` is the intentional exception because its purpose is boundary and ownership description.

## Testable Precision

Definitions must be specific enough that a developer can derive verification from the text.

- Prefer concrete values, named constants, explicit conditions, and observable outcomes over vague intent.
- "Retries up to 3 times with exponential backoff" is testable.
- "Retries reasonably" is not.

## Separate Quality Gates

`tested` and `documented` are separate checks.

- A change can be tested but not documented.
- A change can be documented but not tested.
- Both must be verified explicitly before merge.
- Neither gate substitutes for the other.

## Discoverability Over Prompt Memory

Important project knowledge should live in the repository in named files, not only in prompts, chat history, or oral tradition.

- Prefer many scoped documents over one monolithic manual.
- Keep names predictable so humans and agents can find the right document with simple search.
- Put durable project knowledge in repo files where it can be reviewed and updated.
