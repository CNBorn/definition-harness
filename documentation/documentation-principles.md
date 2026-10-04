# Documentation Principles

This document captures the guiding principles for documentation under `documentation/`.

## Three-Pillar Independence

Documentation, code, and tests are independent pillars that check each other.

- Documentation describes what the system should do and why.
- Code implements behavior.
- Tests verify behavior.
- Each pillar is authoritative in its own domain and does not duplicate another's responsibility.
- Code and tests may agree while both conflict with a definition. Passing tests do not resolve that disagreement.
- When documentation and runtime behavior disagree, report the evidence without assuming which pillar is wrong.
- Use approved intent and change history to decide whether to correct implementation, tests, or documentation.
- A failing test derived from a definition claim is a valuable signal that behavior may have drifted from intent.

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

## Clarity Before Brevity

Short, concrete text is easier to inspect for errors. Use STE-inspired writing principles: one main idea per sentence, active voice, and consistent terms.

- Cut repetition and filler. Keep conditions, exceptions, values, and stable rationale.
- Put a rule in one authoritative place. Link to it from other docs.
- Use a table for comparisons or a diagram for relationships when it reduces reading effort.
- Keep acceptance criteria explicit in text or tables. A diagram must not hide a requirement.
- Word count measures size, not correctness. Full ASD-STE100 compliance is not required.

## Final-State Capture By Default

The repository knowledge layer captures final behavior, stable rationale, and reusable evaluation criteria. Final validation evidence makes those claims reviewable.

- Implementation plans, attempt logs, progress, and handoff notes are transient execution state.
- External harnesses or sessions may manage that state without creating repository files.
- Create temporary working documents only when requested by the user or required by explicit repo-local policy.
- Existing repositories may retain their opted-in tracking conventions; adopting the harness does not require them to add or remove working artifacts.

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

## Shallow Organization

Flat documentation with domain and topic names gives readers a useful grouping without a deep directory tree.

- Use naming to aid discovery. Use explicit links to establish governing rules.
- Keep cross-domain relationships visible through links instead of adding naming levels.
- Prefer focused entry points over manually maintained exhaustive inventories. An inventory adds another place that can become stale.
- Preserve useful existing navigation and explicit local choices during compatible adoption.

## Evidence Before Alignment

A definition audit gives the documentation pillar an explicit path to check implementation and tests.

- Read governing claims before inspecting implementation, so current code does not silently become the expected behavior.
- Include relevant principles and architecture constraints. Distinguish observable requirements from rationale that needs judgment.
- Separate supported claims, conflicts, unclear rules, and missing evidence. Static inspection and passing tests have different limits.
- Report differences before changing any pillar. An audit must not silently erase disagreement by rewriting documentation.
