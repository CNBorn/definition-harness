# <Scope Name> Evaluation Definition

This document defines stable evaluation expectations for `<scope>`.

## Scope

- State the behavior, workflow, interface, or operator process this evaluation covers.
- State what this evaluation intentionally does not cover.

## Related Behavior Definitions

- `<docs path>/<scope>-definition.md`

## Evaluation Summary

- Summarize what evidence is required to trust changes in this scope.

## Required Checks

| Check | Command, tool, or scenario | Required result |
| --- | --- | --- |
| `<check name>` | `<command or scenario>` | `<pass condition>` |

## Scenario Coverage

- `<scenario>`: `<observable behavior or risk being checked>`

## Evidence Requirements

- `<test output, screenshot, video, logs, benchmark table, trace, or manual review note>`

## Failure Handling

- State what must happen when this evaluation fails.
- State whether failures block merge, require human review, or create follow-up work.

## Update Rule

- Update this file when evaluation criteria, commands, scenarios, evidence expectations, or risk boundaries change.
