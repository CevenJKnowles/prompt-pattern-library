---
id: ppl-d01-c01-p02
title: "Templates & Skeleton Formats"
type: pattern
status: active
version: 1.0.0
domain: "Instruction & Control"
category: "Output Structuring & Format Control"
subcategory: "Templates & Skeleton Formats"
tags:
  - structure
  - templates
  - scaffolding
  - format-control
created: 2026-01-05
updated: 2026-01-06
---

# Templates & Skeleton Formats

## Definition

Templates & Skeleton Formats are prompt structures that provide a predefined outline, layout, or placeholder-based format which the model is instructed to fill in, complete, or elaborate upon.

They differ from strict outlines in that the structure is typically *static and reusable*, designed to be applied across multiple tasks or inputs with minimal modification.

---

## Intent

This pattern is used to:

- Reduce ambiguity in expected output structure
- Enforce consistency across repeated generations
- Accelerate prompt authoring by reusing known-good formats
- Guide the model toward completeness without over-constraining content

Templates & Skeleton Formats are especially useful in production workflows where predictable output shape matters more than stylistic variation.

---

## Mechanism

The prompt explicitly presents:

- A fixed structural scaffold (sections, headings, placeholders, or labels)
- Clear instructions to populate each part
- Optional guidance on content depth or constraints per section

The model treats the provided structure as authoritative and focuses its reasoning on *filling*, not *inventing*, the format. This reduces format drift and omission errors.

---

## Prompt Skeleton
```text
Use the following template and complete all sections.

<SECTION 1 TITLE>
- <instruction or placeholder>

<SECTION 2 TITLE>
- <instruction or placeholder>

<SECTION 3 TITLE>
- <instruction or placeholder>

Do not add, remove, or rename sections.
```
### Example
```
Complete the template below.

Problem Statement:
- Summarize the core problem in 2–3 sentences.

Analysis:
- Identify key constraints and assumptions.

Proposed Solution:
- Describe a clear, actionable solution.

Do not include content outside these sections.
```

***

## Failure Modes

* Treating the template as optional rather than mandatory

* Combining this pattern with open-ended creative prompts, causing structure drift

* Overloading templates with excessive instructions, reducing clarity

* Using highly specific templates for tasks that require flexibility

***

## Tags

structure, templates, scaffolding, format-control

```
```
