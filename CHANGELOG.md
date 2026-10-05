# Changelog

## Unreleased

## 1.4.1

- Add entry-file rules. The entry file only routes: how to run, development commands, the reading route, validation commands, and one-sentence links for always-visible constraints.
- Ownership comes first. When a definition owns a user or operator workflow, the entry file links to it and does not restate it. "README covers workflows" now applies only to workflows without an owner, such as installation and commands.
- Behavior and operation changes update only the owning definition. A new adopted scope updates only the adopted-scope table. The entry file changes only when its routing content changes.
- Make the local documentation definition and its adopted-scope table the only document index. Keep the entry file in the documentation language, without translated copies. Move content without an owner to its owner or leave it to code and tests.
- Define entry duties as roles, not files. One `README.md` with `AGENTS.md` as a relative symlink is recommended, not required. Pointer files and separate files remain valid. Document symlink limits and a `readlink` check.
- Add "Shrink An Existing Entry File" with an orphan check. Shrink `README.md` before converting `AGENTS.md` to a symlink, and record the agent entry size before and after in the PR. Add the "Small Routing Entry" principle, and `templates/entry-file.template.md`. Align development flow, audit scope, adoption guidance, and templates.
- Apply the rules to this repository. `README.md` is routing-only and `AGENTS.md` links to it. Adoption prompts, starter files, and scoped-adoption examples moved to `ADOPTION.md`.
- Existing adopters need no action. Paths, separate entry files, and existing navigation remain valid. Shrinking an existing entry file is optional.

## 1.4.0

- Add an on-demand Definition Audit contract and task template. Include applicable principles, evaluation definitions, architecture constraints, and workflow rules.
- Require claim-level evidence, separate test coverage, explicit conflicts and uncertainty, and coverage limits. Report findings before repairs without assuming which pillar is correct.
- Add flat domain/topic naming guidance with at most two semantic levels and explicit governing links.
- Prevent agents from adding or expanding manual inventories of every Markdown file unless requested or required by explicit local policy. Keep focused entry points, adopted-scope tables, and generated discovery available.
- Align agent routing, adoption guidance, development flow, and authoring templates with the new defaults.
- Preserve existing paths, filenames, directory structures, navigation, and explicit local policies. Audits are opt-in; no migration, default CI gate, or repository report is required.

## 1.3.0

- Add STE-inspired writing rules and guidance for tables, charts, and editable diagrams.
- Simplify document types, work roles, adoption guidance, and development flow. Add a Mermaid evaluation loop and align authoring templates.
- Default repository capture to final behavior, stable rationale, reusable evaluation criteria, and final validation evidence.
- Make implementation guides, context, progress, handoff, and acceptance-contract files opt-in through user requests or explicit repo-local policy.
- Remove automatic repository tracking requirements for delegated, multi-session, and unattended work, while preserving existing opted-in conventions and templates.
- Remove the delegated-work artifact reporting section from the default PR template.
- Preserve existing docs paths, definitions, and explicit working-artifact policies. No migration is required.

## 1.2.0

- Add a vendor-neutral repository contract for delegated agent work.
- Define initializer, implementer, evaluator, and closer as work roles rather than runtime components.
- Add progress, acceptance-contract, and evaluation-definition guidance for external agent harnesses.
- Add templates for delegated-work progress, acceptance contracts, and evaluation definitions.
- Expand evaluation guidance for rubric-based review, baseline examples, anti-patterns, and evaluator calibration.
- Update the PR template to capture evaluation evidence and delegated-work artifact closure.

## 1.1.0

- Add scoped adoption guidance for existing and partially adopted repositories.
- Add backward-compatibility guidance for repositories already using the original `documentation/` model.
- Add `ADOPTION.md`.
- Add templates for existing-repo documentation rules and adopting one scope at a time.
- Shorten `README.md` into an agent-oriented landing page.
- Make prompt-based adoption the primary README quick start path.
- Add `VERSION`.
- Add harness evolution principles for future compatibility-aware changes.
