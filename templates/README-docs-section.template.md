## Documentation

Project documentation lives in `documentation/`. Recommended entry points:

- `documentation/documentation-definition.md`: documentation model and authoring conventions
- `documentation/architecture.md`: runtime or system structure and ownership boundaries
- `documentation/development-flow.md`: feature work process
- `documentation/agent-workflow-definition.md`: delegated agent work conventions
- `documentation/<core-system>-definition.md`: authoritative behavior for a core subsystem
- `documentation/<core-scope>-principles.md`: stable rationale for key system decisions
- `documentation/<core-scope>-evaluation-definition.md`: stable evaluation expectations when ordinary tests are not enough

Definition files (`*-definition.md`) describe behavioral requirements. Principles files (`*-principles.md`) describe design rationale. Evaluation definition files (`*-evaluation-definition.md`) describe stable validation expectations.

For new docs, prefer a flat directory with domain and optional topic prefixes, such as `<domain>-<topic>-definition.md`.
Keep governing relationships explicit in document links. Preserve existing names and paths.
These are focused entry points. Do not expand them into a manual inventory of every Markdown file unless requested or required by explicit local policy.

When requested, a Definition Audit compares selected governing documents with implementation and test evidence.
It includes relevant principles and architecture constraints, reports conflicts and uncertainty before repairs, and records coverage limits.
Use Definition Harness's `definition-audit-definition.md` or the adapted local contract. Reports stay in the session or PR by default.
