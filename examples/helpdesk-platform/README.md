# Helpdesk Platform

A helpdesk service that takes in support requests, routes tickets to queues, and escalates VIP tickets.

This directory is a full-repository adoption example for Definition Harness. It contains documentation only; the commands are illustrative.

This file is the only entry for humans and agents. `AGENTS.md` is a symlink to it.
It only routes. Behavior, operations, values, and limits live in `documentation/`; this file does not restate them.

## Run

```sh
make run
```

Operations for each feature are in the definition that owns it.

## Read Before Changing

1. [Documentation rules](documentation/documentation-definition.md): local documentation choices and the **adopted-scope table**. Find each scope's definition, principles, and validation there. This file does not list them.
2. [Support operations principles](documentation/support-operations-principles.md).
3. The definition for the affected scope, and the shared rules it links.

Routing must not mutate ticket state directly; see the ownership invariants in [Architecture](documentation/architecture.md).

## Development Commands

| Command | When to run |
| --- | --- |
| `make setup` | Once per checkout. |
| `make check` | Before finishing a change. All checks must pass. |
