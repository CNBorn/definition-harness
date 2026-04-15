# Code Structure Principles

This document defines stable principles for organizing source code.

## Domain Ownership First

- Place code where the behavior is owned.
- Prefer feature or domain placement over generic catch-all placement.
- Constants, types, and rules should usually live close to the behavior they describe.

## No Catch-All Modules

- Avoid grab-bag files such as broad `helpers`, `utils`, or root-level shared types without clear ownership.
- If a module starts mixing unrelated concepts, split it by boundary.

## Shared Only After Real Reuse

- Do not create shared modules preemptively.
- Promote logic to shared only when multiple independent domains truly depend on the same contract or behavior.

## Keep Contracts Near Behavior

- Keep data contracts and domain constants near the code that owns them.
- Narrow ownership makes refactors safer and reduces accidental coupling.

## Dependency Direction Must Stay Clear

- Higher-level orchestration may depend on domains.
- Domains should not depend on top-level orchestration.
- If dependency direction becomes unclear, move the contract to the narrowest stable owner.

## Refactor By Clarifying Ownership

- Prefer focused moves and dependency cleanup over broad renaming campaigns.
- Separate behavior changes from ownership changes whenever practical.

## Documentation Should Capture Rules, Not Folder Inventories

- Document organizing rules and decision criteria.
- Avoid exhaustive folder maps that go stale quickly.
- Keep implementation-coupled structure notes in `architecture.md` only when they materially affect system understanding.
