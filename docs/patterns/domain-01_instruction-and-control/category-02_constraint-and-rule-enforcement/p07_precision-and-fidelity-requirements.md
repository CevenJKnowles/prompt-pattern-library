---
id: "ppl-d01-c02-p07"
title: "Precision & Fidelity Requirements"
type: pattern
status: active
version: 1.0.0
domain: "Instruction & Control"
category: "Constraint & Rule Enforcement"
subcategory: "Precision & Fidelity Requirements"
tags:
  - "precision"
  - "fidelity"
  - "constraints"
  - "verbatim"
  - "accuracy"
created: 2026-01-05
updated: 2026-01-05
---
# Precision & Fidelity Requirements

## Definition
Precision & Fidelity Requirements is a prompt pattern that forces strict adherence to provided source material, terminology, and formatting rules, minimizing invention, paraphrase drift, or interpretation errors.

## Intent
- Ensure outputs reflect provided inputs with minimal distortion
- Prevent the model from inventing details, fields, or relationships
- Support exacting documentation, extraction, or transformation tasks

## Mechanism
The prompt defines fidelity rules (use exact terms, preserve ordering, do not add fields) and mandates explicit uncertainty handling when data is missing.

## When to Use
- Transforming existing docs into a schema (YAML, JSON, templates)
- Extracting facts from provided material
- Generating diffs, changelogs, or structured summaries

## When Not to Use
- Creative ideation where invention is desired
- High-level synthesis where interpretation is the product
- When the provided source is incomplete and you want best-effort filling

## Prompt Skeleton
```text
Fidelity Rules:
- Use only the provided source content.
- Preserve key terminology exactly.
- Do not invent missing details or fields.
- If required information is missing: state what is missing and ask for it.

Task:
{task}

Source:
{source_text}
```
### Example Prompt

```text
Fidelity Rules:
- Use only the provided file list.
- Preserve filenames and headings exactly.
- Do not rename patterns or change IDs.
- If a file is missing, state it explicitly.

Task:
List the pattern files in Domain 1 / Category 2.

Source:
p01_style-and-tone-restrictions.md
p02_scope-and-domain-limits.md
p03_forbidden-content-rules.md
p04_mandatory-inclusion-requirements.md
p05_word-character-token-constraints.md
p06_safety-and-ethical-guardrails.md
p07_precision-and-fidelity-requirements.md
```

### Example Output (Excerpt)

```text
- p01_style-and-tone-restrictions.md
- p02_scope-and-domain-limits.md
- p03_forbidden-content-rules.md
- p04_mandatory-inclusion-requirements.md
- p05_word-character-token-constraints.md
- p06_safety-and-ethical-guardrails.md
- p07_precision-and-fidelity-requirements.md
```

## Failure Modes
* **Hallucinated additions:** Adds files/fields not present in the source
* **Terminology drift:** Paraphrases key labels that should stay exact
* **Silent repairs:** Fixes perceived errors in source without permission
* **Unsignaled uncertainty:** Guesses missing data instead of flagging it

## Evaluation Checklist
* [ ] Only source-supported content appears
* [ ] Key terms/labels are preserved exactly
* [ ] No renames or schema changes occur without instruction
* [ ] Missing info is flagged explicitly
* [ ] Formatting and ordering rules are respected

## Variants
* **Verbatim mode:** forbid paraphrase entirely; quote with limits
* **Schema lock:** enforce exact field set + ordering
* **Diff-first:** produce a change list before applying transformations

## Notes
Use this pattern when correctness depends on *not* being clever. Pair it with Scope & Domain Limits to prevent helpful-but-wrong additions.

## Tags
precision, fidelity, constraints, verbatim, accuracy
