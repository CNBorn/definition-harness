# VIP Escalation Definition

## Scope

- Defines the workflow for escalating unresolved VIP tickets.

## Inherits From

- `documentation/ticket-routing-definition.md`

## Behavior Summary

- VIP tickets that remain unassigned or unresolved beyond defined thresholds are escalated to a dedicated response path.

## Preconditions

- Ticket belongs to a VIP or enterprise account.
- Ticket has not reached a terminal state.

## Behavior

- If a VIP ticket is unassigned for more than 10 minutes, the system pages the on-duty support lead.
- If a VIP ticket remains unresolved for more than 60 minutes, the system raises an escalation event for leadership review.
- Escalation notifications must not change ticket priority by themselves; they trigger review, not silent mutation.

## Edge Cases

- Duplicate escalation notifications for the same threshold crossing are suppressed.
- Manually paused tickets do not escalate while the pause is active.

## Defaults And Constraints

- Thresholds are measured from the most recent reopen or creation time, whichever is later.

## Verification Notes

- Tests should cover threshold crossing, pause suppression, duplicate suppression, and reopen timing reset behavior.
