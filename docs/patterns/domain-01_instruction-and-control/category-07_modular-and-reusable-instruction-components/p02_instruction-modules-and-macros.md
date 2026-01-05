---
id: "ppl-d01-c07-p02"
title: "Instruction Modules & Macros"
type: pattern
status: active
version: 1.0.0
domain: "Instruction & Control"
category: "Modular & Reusable Instruction Components"
subcategory: "Instruction Modules & Macros"
tags:
  - "modularity"
  - "reuse"
  - "instruction-design"
  - "macros"
  - "templates"
  - "scaffolding"
created: 2026-01-05
updated: 2026-01-05
---

# Instruction Modules & Macros

## Definition
Instruction modules/macros are named bundles of directives that can be invoked as a unit (like a macro), reducing repetition and enabling consistent behavior.

## Intent
Enable faster prompt authoring by invoking pre-packaged instruction sets with predictable effects.

## Mechanism
Define modules with a name and activation syntax. At runtime, expand the module into its directives or treat it as a referenced specification.

## When to Use
* You have recurring task families (summaries, QA, extraction)
* You need consistent compliance constraints across outputs
* You maintain a shared prompt library

## When Not to Use
* The model cannot access the module content and you cannot paste it
* You need transparency (no “hidden” macro expansion)
* You expect high customization per run

## Prompt Skeleton
```text
MODULE: <MODULE_NAME>
SCOPE: <what it controls>
DIRECTIVES:
- <directive_1>
- <directive_2>
PARAMETERS:
- <param_1>
END MODULE

TASK:
<task>

ACTIVATE MODULES:
- <MODULE_NAME> with {<param_1>=...}

OUTPUT:
<format>
```

### Example Prompt
```text
MODULE: STRUCTURED_SUMMARY
SCOPE: Produce consistent summaries.
DIRECTIVES:
- Use headings: Context, Key Points, Risks, Next Steps
- Keep bullet points concise
PARAMETERS:
- max_bullets
END MODULE

TASK:
Summarize the meeting notes below.

ACTIVATE MODULES:
- STRUCTURED_SUMMARY with {max_bullets=8}

OUTPUT:
Markdown.
```

### Example Output (Excerpt)
```text
A Markdown summary with the specified headings and up to 8 bullets per section.
```

## Failure Modes
* Module name collision or ambiguous activation
* Parameters ignored because they’re not clearly bound
* Module directives conflict with task-specific constraints

## Evaluation Checklist
* [ ] Module scope is explicit
* [ ] Activation syntax is unambiguous
* [ ] Parameters are listed and used in the example
* [ ] Directives don’t contradict other constraints
* [ ] Output format is specified

## Variants
* Provide a ‘lite’ module with fewer directives
* Split a module into smaller modules and compose them
* Add a `DEACTIVATE:` mechanism to override sub-directives

## Notes
* Avoid “magic” modules; include the directives in-repo
* Keep modules testable with small sample inputs
* Prefer composition of small modules over one big module

## Tags
* `modularity`
* `reuse`
* `instruction-design`
* `macros`
* `templates`
* `scaffolding`
