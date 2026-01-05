---
id: ppl-d01-c04-p05
title: Parallel Task Instructions
type: pattern
status: active
version: 1.0.0
domain: Instruction & Control
category: Task & Sequence Instruction Patterns
subcategory: Parallel Task Instructions
tags:
- parallelism
- multi-task
- workflow
- segmentation
- structure
created: 2026-01-05
updated: '2026-01-05'
---

# Parallel Task Instructions

## Definition
Parallel Task Instructions is a prompt pattern that asks the model to perform multiple tasks **independently in parallel**, producing separate outputs per task without intermixing.

## Intent
- Speed up response usefulness when tasks are independent
- Prevent one task from hijacking the whole response
- Improve comparability of outputs
- Support multi-track thinking (options, perspectives)

## Mechanism
The prompt defines:
- multiple independent tasks
- strict output segregation (sections per task)
- rules forbidding cross-references unless requested
- optional resource budgets per task (length/time)

This yields a **multi-lane** response rather than a single serial chain.

## When to Use
- Comparing alternatives side-by-side
- Producing multiple drafts/angles
- Independent subtasks (summary + checklist + risks)
- When the user wants breadth quickly

## When Not to Use
- Tasks with strong dependencies
- When one task’s output is required for another
- When output length is tightly constrained
- When the user needs a single integrated answer

## Prompt Skeleton
```text
Complete the tasks below in parallel (independently).

Tasks:
A) {task_a}
B) {task_b}
C) {task_c}

Rules:
- Output under headings: "## A", "## B", "## C".
- Do not reference other sections.
- Keep each section <= {limit} words.

```
### Example Prompt

```
Complete the tasks below in parallel (independently).

Tasks:
A) Give a 5-bullet definition.
B) Give 5 failure modes.
C) Give a checklist.

Rules:
- Output under headings: "## A", "## B", "## C".
- Do not reference other sections.
- Keep each section <= 80 words.
```

### Example Output (Excerpt)

```
## A
- Defines a pattern...

## B
- Overgeneralization...

## C
- [ ] Matches baseline...
```

## Failure Modes
* **Cross-talk:** leaking information between sections
* **Uneven effort:** one section is detailed, others are shallow
* **Hidden dependencies:** tasks aren’t actually independent
* **Format drift:** headings or limits ignored per section

## Evaluation Checklist
* [ ] Tasks are independent and listed explicitly
* [ ] Each task output is clearly separated
* [ ] No cross-references occur unless allowed
* [ ] Per-task limits are respected
* [ ] Outputs are comparable in depth and quality

## Variants
* **Budgeted lanes:** different word budgets per task
* **Role lanes:** different personas per section
* **Option lanes:** produce multiple solution options in parallel
* **Validation lane:** add a final section that checks all lanes

## Notes
Use with **Sectioned Output** and **Length Control** to prevent runaway parallel sections. If tasks have dependencies, switch to **Sequential Multi-Task Patterns**.

## Tags
parallelism, multi-task, workflow, segmentation, structure, structure, instruction
