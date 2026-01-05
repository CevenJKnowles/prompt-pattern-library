---
id: ppl-d01-c01-p03
title: "Tabular & Matrix Output"
type: pattern
status: active
version: 1.0.0
domain: "Instruction & Control"
category: "Output Structuring & Format Control"
subcategory: "Tabular & Matrix Output"
tags:
  - "structure"
  - "tables"
  - "matrices"
  - "format-control"
created: 2026-01-05
updated: 2026-01-06
---

# Tabular & Matrix Output

## Definition
Tabular & Matrix Output is a prompt pattern that constrains the model’s response into a **table or matrix form**, using rows and columns to organise information into explicit, comparable fields.

The structure may be presented as a markdown table, CSV-like grid, or clearly delimited matrix, depending on the constraints specified in the prompt.

## Intent
- Enforce consistent field alignment across multiple items
- Enable easy comparison between entities or attributes
- Reduce ambiguity by binding values to explicit columns
- Support downstream reuse, parsing, or inspection

## Mechanism
The prompt specifies:
- the required table or matrix structure
- column (and optionally row) labels
- formatting rules (e.g. markdown table, delimiter style)
- constraints on content placement (no prose outside cells)

This shifts the model from narrative generation into **field-bound completion**, where each datum must occupy a defined position.

## When to Use
- Comparing multiple options, entities, or scenarios
- Summarising structured information across consistent attributes
- Preparing outputs for spreadsheets, reports, or further processing
- Any task where relational clarity matters more than prose flow

## When Not to Use
- Free-form explanation or storytelling
- Tasks where relationships are non-rectangular or emergent
- Highly qualitative analysis that does not decompose cleanly into fields
- Situations where rigid structure obscures nuance

## Prompt Skeleton
```text
Present the output in a table with the following columns:

| Column A | Column B | Column C |
|----------|----------|----------|

Rules:
- Populate every cell.
- Do not add or remove columns.
- Do not include prose outside the table.

Input: {input_data}
```
### Example Prompt

```
Present the output in a table with the following columns:

| Feature | Advantage | Limitation |
|---------|-----------|------------|

Rules:
- Populate every cell.
- Do not add or remove columns.
- Do not include prose outside the table.

Input: Three common prompt-structuring patterns
```

### Example Output (Excerpt)

```
| Feature                 | Advantage                         | Limitation                         |
|-------------------------|-----------------------------------|------------------------------------|
| Outline structures      | Clear hierarchical planning        | Can over-constrain creativity       |
| Templates               | Consistent reusable outputs        | May reduce flexibility              |
| Tabular output          | Easy comparison across attributes  | Poor fit for narrative explanation  |
```

## Failure Modes

* **Column drift:** values appear under the wrong headings
* **Missing cells:** some rows or columns are left incomplete
* **Prose leakage:** explanatory text appears outside the table
* **Over-tabularisation:** forcing complex ideas into an unnatural grid

## Evaluation Checklist

* [ ] All specified rows and columns are present
* [ ] Every cell is populated appropriately
* [ ] No prose appears outside the table or matrix
* [ ] Column labels clearly match cell content
* [ ] Structure supports comparison or reuse

## Variants

* **Fixed matrix:** predefined rows and columns, fully constrained
* **Expandable rows:** fixed columns with variable row count
* **CSV-style:** delimiter-based output for machine ingestion
* **Two-pass:** generate table first, then explain selected cells separately

## Notes

This pattern pairs well with **Templates & Skeleton Formats** when repeated tabular outputs are required. Avoid combining with open-ended narrative prompts unless the table is generated first and prose is explicitly deferred.

## Tags

structure, tables, matrices, comparison, format-control
