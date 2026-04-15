# Architecture Overview

This document defines the high-level architecture for a helpdesk platform: request intake, routing, agent work, and escalation boundaries.

## Architectural Intent

- Keep ticket ownership explicit.
- Keep routing policy testable and reviewable.
- Separate product rules from transport and vendor adapters.

## Runtime Boundaries

1. Intake Layer
- Accepts API, email, and web form submissions.
- Normalizes inbound requests into internal ticket contracts.

2. Routing Layer
- Applies priority, queue, and assignment policy.
- Decides whether escalation rules should trigger.

3. Work Management Layer
- Owns ticket state transitions, SLA timers, comments, and assignments.

4. Adapter Layer
- Integrates with email delivery, CRM sync, chat notifications, and analytics.

## Ownership Invariants

- Ticket status and assignment are owned by the work management layer.
- Routing recommendations do not directly mutate persistent ticket state without an explicit transition step.
- Adapter payloads are derived outputs, not source-of-truth state.

## Dependency Direction Rules

- Intake may depend on normalization contracts.
- Routing may depend on ticket contracts and policy definitions.
- Adapters consume internal contracts and external schemas, but should not own routing policy.

## Non-goals

- Vendor-specific API details
- UI component structure
- Database table inventories
