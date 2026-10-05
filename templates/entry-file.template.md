# <Project Name>

<One sentence: what this repository is.>

This file is the only entry for humans and agents. `AGENTS.md` is a symlink to it.
It only routes. Behavior, operations, values, and limits live in `<docs path>/`; this file does not restate them.

## Run

<Requirements, one line each, linked to the definition that owns the platform contract.>

```sh
<run command>
```

Operations for each feature are in the definition that owns it.

## Read Before Changing

1. [Documentation rules](<docs path>/documentation-definition.md): document types, naming, workflow, and the **adopted-scope table**. Find each scope's definition, principles, and validation there. This file does not list them.
2. <Shared principles that every change must follow, if any.>
3. The definition for the affected scope, and the shared rules it links.

<Always-visible constraint: one sentence and a link to its owner.>

## Development Commands

| Command | When to run |
| --- | --- |
| `<setup command>` | <once per checkout> |
| `<check command>` | <before finishing a change; all checks must pass> |
