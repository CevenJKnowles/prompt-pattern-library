---
id: ppl-d01-c04-p02
title: Sequential Multi-Task Patterns
type: pattern
status: active
version: 1.0.0
domain: Instruction & Control
category: Task & Sequence Instruction Patterns
subcategory: Sequential Multi-Task Patterns
tags:
- sequencing
- multi-task
- ordering
- workflow
- execution-control
created: 2026-01-05
updated: '2026-01-05'
---

# Sequential Multi-Task Patterns

## Definition
Sequential Multi-Task Patterns is a prompt pattern that decomposes a request into multiple tasks and enforces a **fixed execution order**, producing outputs per task in sequence.

## Intent
- Prevent the model from mixing tasks
- Improve traceability and review of multi-part work
- Support staged workflows (draft → revise → finalize)
- Reduce omission of later tasks

## Mechanism
The prompt defines:
- a list of tasks (Task A, Task B, Task C)
- a strict order and completion criteria per task
- an output boundary for each task (headers/blocks)
- rules forbidding cross-contamination (no working on B during A)

This enforces a **pipeline** rather than a blended response.

## When to Use
- Multi-part deliverables (plan + draft + checklist)
- Content production with review gates
- Analysis followed by recommendations
- Any request where outputs must be separable

## When Not to Use
- Problems requiring integrated synthesis across tasks
- Highly interactive dialog where tasks evolve mid-stream
- Tiny requests where task partitioning adds noise
- When the user wants a single unified output

## Prompt Skeleton
```text
You will complete the following tasks in order:
1) {task_1}
2) {task_2}
3) {task_3}

Rules:
- Do not start Task 2 until Task 1 is complete.
- Output each task under a heading "## Task {n}".
- Do not reference future tasks while working on the current one.

```
### Example Prompt

```
You will complete the following tasks in order:
1) Summarize the category goal in 3 bullets.
2) Produce a prompt skeleton for the pattern.
3) Provide an example prompt and output excerpt.

Rules:
- Do not start Task 2 until Task 1 is complete.
- Output each task under a heading "## Task {n}".
- Do not reference future tasks while working on the current one.
```

### Example Output (Excerpt)

```
## Task 1
- Enforce strict ordering across multiple tasks.
- Keep outputs separated for review.
- Reduce mixing and omissions.

## Task 2
Prompt Skeleton:
"Complete Task 1, then Task 2..."

## Task 3
Example Prompt:
"1) Summarize..."
```

## Failure Modes
* **Task blending:** mixing outputs across tasks
* **Premature execution:** starting later tasks early
* **Missing completion criteria:** unclear when a task is “done”
* **Uneven depth:** over-investing in early tasks and starving later tasks

## Evaluation Checklist
* [ ] Tasks are listed explicitly and ordered
* [ ] Output is clearly segmented per task
* [ ] No task content leaks into other task sections
* [ ] All tasks are completed with comparable thoroughness
* [ ] The order matches the user’s priorities

## Variants
* **Gate-based:** require a review/approval line before advancing
* **Iterative pass:** repeat the sequence (draft → refine → finalize)
* **Scoped outputs:** enforce length limits per task
* **Dependency-aware:** allow later tasks to consume earlier outputs only

## Notes
Use with **Sectioned & Multi-Part Output** to make task boundaries unambiguous. Add **Stop Conditions** if the user must confirm between tasks.

## Tags
sequencing, multi-task, ordering, workflow, execution-control, structure, instruction
