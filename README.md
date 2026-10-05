# Definition Harness

A spec-anchored repository harness that keeps software behavior, intent, tests, and operator instructions aligned. The current version is in `VERSION`.

This file is the only entry for humans and agents. `AGENTS.md` is a symlink to it.
It only routes. Rules live in `ADOPTION.md` and `documentation/`; this file does not restate them.

## Quick Start

Point your coding agent at this repository URL. A local checkout is not required.

```text
Use Definition Harness from <repo URL>. Read its README and ADOPTION.md, choose the adoption mode for this repository, and follow it.
```

Prompts for a new repository, an existing repository, one scope, and an earlier-version adopter are in [Adoption Prompts](ADOPTION.md#adoption-prompts).
For an audit, use `templates/definition-audit.template.md`.

## Read Before Adopting

1. [ADOPTION.md](ADOPTION.md): adoption modes, compatibility, starter files, and the entry-file layout. Adoption is gradual by scope, not by discipline.
2. [Documentation definition](documentation/documentation-definition.md): document types, naming, writing, entry-file, and update rules.
3. [Development flow](documentation/development-flow.md): planning, validation, and PR closure.
4. [Agent workflow definition](documentation/agent-workflow-definition.md): when work is delegated to an agent.
5. [Definition audit definition](documentation/definition-audit-definition.md): when a user requests an audit.

Adapt `templates/` paths and validation commands to the target repository before use.
[POSITIONING.md](POSITIONING.md) explains why this exists. [CHANGELOG.md](CHANGELOG.md) lists version changes.

## Working In This Repository

Follow the documents above for changes to this repository, and [harness evolution principles](documentation/harness-evolution-principles.md) for changes to rules, templates, versions, or compatibility.
Preserve compatibility for adopted repositories unless a breaking version is planned; see [Framework Versions](ADOPTION.md#framework-versions).

Validation:

```sh
test "$(readlink AGENTS.md)" = README.md
```

Also check changed Markdown links and Mermaid diagrams. Record results in the PR.
