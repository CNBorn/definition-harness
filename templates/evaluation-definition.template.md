# <Scope Name> Evaluation Definition

This document defines stable evaluation expectations for `<scope>`.

## Scope

- State the behavior, workflow, interface, or operator process this evaluation covers.
- State what this evaluation intentionally does not cover.

## Related Behavior Definitions

- `<docs path>/<scope>-definition.md`

## Evaluation Summary

- Summarize what evidence is required to trust changes in this scope.
- State whether this evaluation is command-based, scenario-based, rubric-based, or a mix.

## Required Checks

| Check | Command, tool, or scenario | Required result |
| --- | --- | --- |
| `<check name>` | `<command or scenario>` | `<pass condition>` |

## Scenario Coverage

- `<scenario>`: `<observable behavior or risk being checked>`

## Rubric Dimensions

Use this section only when correctness depends on judgment-heavy criteria such as design quality, writing quality, usability, support quality, or operator judgment.

| Dimension | Definition | Weight or priority | Passing evidence |
| --- | --- | --- | --- |
| `<dimension>` | `<what this dimension means>` | `<weight, priority, or n/a>` | `<what the evaluator must observe>` |

## Reference Cases

Use multiple reference cases when a single example could cause overfitting.

| Case | Expected evaluator judgment | Notes |
| --- | --- | --- |
| `<case or artifact>` | `<pass/fail/score>` | `<why>` |

## Anti-Patterns

- `<specific failure pattern the evaluator should catch>`
- `<specific failure pattern the evaluator should catch>`

## Evaluator Calibration

- State how evaluator judgments should be compared against human review.
- State when the rubric should be updated because evaluator results and human judgment disagree.

## Evidence Requirements

- `<test output, screenshot, video, logs, benchmark table, trace, or manual review note>`

## Failure Handling

- State what must happen when this evaluation fails.
- State whether failures block merge, require human review, or create follow-up work.
- State what the implementer should record before starting another iteration.

## Update Rule

- Update this file when evaluation criteria, commands, scenarios, evidence expectations, or risk boundaries change.
- Update this file when repeated review feedback shows that the rubric misses an important failure pattern.
