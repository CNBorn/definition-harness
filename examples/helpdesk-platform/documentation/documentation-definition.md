# Documentation Definition

This document defines the local documentation choices for the helpdesk platform.
It applies [Definition Harness 1.4.2](https://github.com/CNBorn/definition-harness/blob/43c094ccdffa0af516a895fc18d4527786ad373e/ADOPTION.md) in full-repository mode. The full rules are in the pinned [documentation definition](https://github.com/CNBorn/definition-harness/blob/43c094ccdffa0af516a895fc18d4527786ad373e/documentation/documentation-definition.md); this document records local choices.

## Documentation Path And Entry

- Stable documentation lives in `documentation/`. Working docs, such as progress, context, acceptance, and handoff files, are not enabled.
- `README.md` is the only entry for humans and agents. `AGENTS.md` is a relative symlink to it.
- The entry file only routes. It links to owning documents and does not restate them.
- The documentation language is English.

## Adopted Scopes

This table is the only document index. Full-repository adoption lists every scope that has a definition.

| Scope | Definition | Principles | Validation |
| --- | --- | --- | --- |
| Ticket routing | [ticket-routing-definition.md](ticket-routing-definition.md) | [support-operations-principles.md](support-operations-principles.md) | `make check`; tests for the definition's verification notes |
| VIP escalation | [vip-escalation-definition.md](vip-escalation-definition.md) | [support-operations-principles.md](support-operations-principles.md) | `make check`; tests for the definition's verification notes |

[Architecture](architecture.md) defines boundaries and ownership for all scopes.

## Update Rules

- A behavior or operation change updates only the definition that owns it, with tests for its observable claims.
- A new scope adds a row to this table. It does not change `README.md`.
- Update `README.md` only when how to run, development commands, the reading route, or validation commands change.
- Update `architecture.md` only when boundaries, ownership, dependency direction, or lifecycle invariants change.
- Planning, validation, and PR closure follow the pinned [development flow](https://github.com/CNBorn/definition-harness/blob/43c094ccdffa0af516a895fc18d4527786ad373e/documentation/development-flow.md).
