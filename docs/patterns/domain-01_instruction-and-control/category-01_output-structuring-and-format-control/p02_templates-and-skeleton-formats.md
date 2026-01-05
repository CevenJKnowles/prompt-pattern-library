---
id: ppl-d01-c01-p02
title: "Templates & Skeleton Formats"
type: pattern
status: active
version: 1.0.1
domain: "Instruction & Control"
category: "Output Structuring & Format Control"
subcategory: "Templates & Skeleton Formats"
tags:
  - "structure"
  - "templates"
  - "scaffolding"
  - "format-control"
created: 2026-01-05
updated: 2026-01-06
---

# Templates & Skeleton Formats

## Definition
Templates & Skeleton Formats are prompt structures that provide a predefined outline, layout, or placeholder-based format which the model is instructed to fill in, complete, or elaborate upon.

They differ from strict outlines in that the structure is typically *static and reusable*, designed to be applied across multiple tasks or inputs with minimal modification.

## Intent
- Reduce ambiguity in expected output structure
- Enforce consistent output shape across repeated generations
- Accelerate prompt authoring through reuse
- Improve completeness by making required fields explicit

## Mechanism
The prompt explicitly specifies:
- a fixed scaffold (sections, headings, placeholders, labels)
- instructions for how to populate each section
- constraints that prohibit adding/removing/renaming sections

This shifts the model from “invent the format” to **fill the given format**, reducing omission and format drift.

## When to Use
- Repeated tasks that must produce uniform output (reports, briefs, summaries)
- Data capture or structured extraction (fields, forms, checklists)
- Production workflows where downstream parsing or reuse depends on stable structure
- Team settings where a shared output standard is required

## When Not to Use
- Exploratory ideation where the structure should emerge organically
- Highly creative writing where rigid structure is counterproductive
- Tasks where the correct structure is unknown or likely to change mid-task
- Situations where over-constraint increases failure risk (e.g., complex, uncertain inputs)

## Prompt Skeleton
```text
Use the following template and complete all sections.

<SECTION 1 TITLE>
- <instruction or placeholder>

<SECTION 2 TITLE>
- <instruction or placeholder>

<SECTION 3 TITLE>
- <instruction or placeholder>

Rules:
- Complete every section.
- Do not add, remove, or rename sections.
- Keep responses within the template boundaries.
```

### Example Prompt

```
Use the following template and complete all sections.

Problem Statement:
- Summarize the core problem in 2–3 sentences.

Analysis:
- Identify key constraints and assumptions.

Proposed Solution:
- Describe a clear, actionable solution.

Rules:
- Complete every section.
- Do not add, remove, or rename sections.
- Do not include content outside these sections.
```

### Example Output (Excerpt)

```
Problem Statement:
- The team needs consistent weekly status updates that are easy to scan and compare.

Analysis:
- Multiple contributors write updates inconsistently; key items are often omitted; formatting varies across weeks.

Proposed Solution:
- Introduce a shared status template with fixed headings and required fields, and enforce “no extra sections.”
```

## Failure Modes

* **Template treated as optional:** the model adds extra sections or ignores placeholders
* **Overly complex scaffold:** too many fields reduce completion quality and increase omissions
* **Mismatch to task:** a rigid template forces unnatural structure and degrades usefulness
* **Ambiguous placeholders:** vague labels lead to inconsistent interpretation across runs

## Evaluation Checklist

* [ ] All sections are present and completed
* [ ] No extra sections were added and none were renamed
* [ ] Output stays inside the template boundaries
* [ ] Each section content matches its label/instruction
* [ ] Structure is reusable across similar tasks without modification

## Variants

* **Strict template:** fixed headings, fixed number of fields, strict completion rules
* **Light template:** fixed headings, minimal required fields, allows short entries
* **Two-pass:** fill template first, then (optionally) expand each section in order

## Notes

Prefer this pattern when output will be reused, compared, or parsed. If you need the model to *discover* structure first, use **Outline & Hierarchy Structures** and then convert the outline into a reusable template.

## Tags

structure, templates, skeletons, scaffolding, format-control, standardisation

---```