---
id: ppl-d01-c04-p03
title: Task Looping & Repetition Instructions
type: pattern
status: active
version: 1.0.0
domain: Instruction & Control
category: Task & Sequence Instruction Patterns
subcategory: Task Looping & Repetition Instructions
tags:
- iteration
- looping
- repetition
- workflow
- control
created: 2026-01-05
updated: '2026-01-05'
---

# Task Looping & Repetition Instructions

## Definition
Task Looping & Repetition Instructions is a prompt pattern that makes the model repeat a defined operation across a set of items, steps, or cycles using an explicit loop structure.

## Intent
- Improve consistency across batches
- Reduce forgotten items in lists/sets
- Standardize repeated transformations
- Enable scalable processing (N items, same rules)

## Mechanism
The prompt specifies:
- an item set (list of inputs, rows, files)
- a repeated procedure applied to each item
- a per-item output format
- rules for handling missing/invalid items

This turns the model into a **batch processor** with uniform output per iteration.

## When to Use
- Applying the same template to multiple patterns/files
- Generating consistent summaries per item
- Review passes (check each file for compliance)
- Any repetitive operation that benefits from uniformity

## When Not to Use
- When items require distinct bespoke reasoning
- When repetition encourages shallow boilerplate
- When the item set is unknown or can’t be enumerated
- When the task should be interactive rather than batch

## Prompt Skeleton
```text
Items:
{items}

For each item, perform the same procedure:
1) {operation_1}
2) {operation_2}

Output format (repeat per item):
- Item: {item_name}
- Result: {result}

Rules:
- Do not skip any item.
- Do not change the output format.

```
### Example Prompt

```
Items:
- p01
- p02
- p03

For each item, perform the same procedure:
1) State the intent in one sentence.
2) Provide one failure mode.

Output format (repeat per item):
- Item: {item}
- Intent: ...
- Failure mode: ...

Rules:
- Do not skip any item.
- Do not change the output format.
```

### Example Output (Excerpt)

```
- Item: p01
- Intent: Enforce ordered, stepwise procedures.
- Failure mode: Skips steps.

- Item: p02
- Intent: Separate and sequence multiple tasks.
- Failure mode: Blends tasks.

- Item: p03
- Intent: Apply the same procedure repeatedly.
- Failure mode: Inconsistent formatting.
```

## Failure Modes
* **Item skipping:** omitting entries from the loop
* **Format drift:** changing structure mid-loop
* **Inconsistent application:** applying different rules to different items
* **Over-compression:** overly brief outputs to “get through” the loop

## Evaluation Checklist
* [ ] The item set is explicit and complete
* [ ] The same procedure is applied to every item
* [ ] Output format is identical per item
* [ ] No item is skipped or merged
* [ ] Exceptions are handled per stated rules

## Variants
* **Two-pass loop:** generate first pass, then validate/repair each item
* **Chunked loop:** process items in batches to manage length
* **Priority loop:** process high-priority items first, then the rest
* **Conditional loop:** apply different branches based on item properties

## Notes
Combine with **Length & Granularity Control** to prevent the loop from blowing past output limits. For strictness, add **Precision Requirements**.

## Tags
iteration, looping, repetition, workflow, control, structure, instruction
