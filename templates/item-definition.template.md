# <Item Or Workflow Name> Definition

Use short, concrete rules. Remove unused sections without omitting required behavior or constraints.

## Scope

- Describe the specific workflow, command, policy, interface, or item this file defines.

## Inherits From

- `documentation/<system>-definition.md`

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
