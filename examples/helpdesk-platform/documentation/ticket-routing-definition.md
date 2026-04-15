# Ticket Routing Definition

## Scope

- Defines how newly created tickets are classified, prioritized, and assigned to a queue.
- Does not define the full lifecycle after a ticket is assigned.

## Governing Principles

- `documentation/support-operations-principles.md`

## Behavior Summary

- Every new ticket is assigned a priority and queue before it becomes available for agent work.
- Routing decisions are deterministic from ticket facts and configured policy inputs.

## Core Rules

- Routing must use explicit ticket attributes and configured policy, not freeform agent judgment at intake time.
- Tickets from customers with an active enterprise plan enter the `enterprise-support` queue by default.
- Tickets marked as security-sensitive enter the `security-review` queue regardless of general product area.
- If a ticket matches multiple queues, the highest-severity queue wins.

## Inputs And Triggers

- New ticket creation from API, email, or form intake.
- Policy configuration updates applied by operators.

## State And Contracts

- Normalized ticket category
- Customer plan tier
- Severity classification
- Queue assignment

## Defaults And Constraints

- Tickets with insufficient classification data default to `general-support`.
- Routing must complete before the ticket is visible in the agent work queue.

## Verification Notes

- Tests should cover queue precedence, plan-tier routing, security overrides, and default fallback behavior.
