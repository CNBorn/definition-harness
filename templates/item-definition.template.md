# <Item Or Workflow Name> Definition

Use short, concrete rules. Remove unused sections without omitting required behavior or constraints.
For new docs, prefer `<domain>-<topic>-definition.md` in a flat directory. Keep existing adopted filenames.

## Scope

- Describe the specific workflow, command, policy, interface, or item this file defines.

## Inherits From

- `documentation/<system>-definition.md`

Link applicable system rules explicitly. A filename prefix does not establish inheritance. Remove this section if no system definition governs this scope.

## Governing Principles

- `documentation/<scope>-principles.md`

Link shared principles and cross-domain constraints when applicable. A separate principles file for this item is not required.

## Behavior Summary

- Short summary of the current behavior.

## Preconditions

- State required inputs, system state, permissions, or timing assumptions.

## Behavior

- Describe the observable sequence of behavior.
- Include branching, defaults, and failure conditions when relevant.
- Use a Mermaid flow or state diagram if it makes branches clearer. Label transitions and keep conditions and failure rules explicit in text.

## Edge Cases

- State important exceptional or limiting cases.

## Defaults And Constraints

- Document important values, retries, timeouts, thresholds, or policy caps.

## Verification Notes

- Describe the key assertions or outcomes that tests should verify.
