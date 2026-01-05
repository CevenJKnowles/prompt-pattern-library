---
id: ppl-d01-c04-p04
title: Task Decomposition & Subtasking
type: pattern
status: active
version: 1.0.0
domain: Instruction & Control
category: Task & Sequence Instruction Patterns
subcategory: Task Decomposition & Subtasking
tags:
- decomposition
- planning
- subtasks
- workflow
- structure
created: 2026-01-05
updated: '2026-01-05'
---

# Task Decomposition & Subtasking

## Definition
Task Decomposition & Subtasking is a prompt pattern that forces the model to break a complex task into **explicit subtasks**, often with dependencies and deliverables for each subtask.

## Intent
- Make complex work manageable
- Expose hidden dependencies and prerequisites
- Improve planning quality and completeness
- Create a checklist the user can execute

## Mechanism
The prompt requires:
- a subtask list with clear boundaries
- optional dependency mapping (A before B)
- per-subtask outputs (goal, input, output)
- rules preventing premature deep work before decomposition

This converts “do X” into a **structured plan**.

## When to Use
- Projects, implementations, migrations
- Anything with multiple moving parts
- When you need a plan before execution
- When delegating work across people/tools

## When Not to Use
- Simple tasks with a single action
- When the user wants immediate output, not planning
- When the task is exploratory and should remain flexible
- When decomposition creates artificial bureaucracy

## Prompt Skeleton
```text
Task: {task}

First, decompose into {n}–{m} subtasks.
For each subtask, include:
- Goal
- Inputs needed
- Output/deliverable
- Dependencies (if any)

Rules:
- Do not execute subtasks; only decompose.
- If information is missing, list it under "Open Questions".

```
### Example Prompt

```
Task: Fill a category of prompt-pattern markdown files.

First, decompose into 5–8 subtasks.
For each subtask, include:
- Goal
- Inputs needed
- Output/deliverable
- Dependencies (if any)

Rules:
- Do not execute subtasks; only decompose.
- If information is missing, list it under "Open Questions".
```

### Example Output (Excerpt)

```
1) Inventory files
- Goal: Identify all pattern stubs in the category
- Inputs: Category folder
- Output: File list
- Dependencies: None

2) Normalize frontmatter
- Goal: Align YAML fields to baseline
- Inputs: Baseline pattern
- Output: Updated YAML
- Dependencies: 1

3) Fill sections
- Goal: Write Definition/Intent/... for each pattern
- Inputs: Pattern titles
- Output: Completed markdown
- Dependencies: 2
```

## Failure Modes
* **Over-decomposition:** too many subtasks with trivial differences
* **Under-decomposition:** vague subtasks that hide real work
* **Missing dependencies:** tasks listed without ordering constraints
* **Execution leakage:** starting to execute instead of planning

## Evaluation Checklist
* [ ] Subtasks are explicit and non-overlapping
* [ ] Each subtask has a clear deliverable
* [ ] Dependencies are stated where relevant
* [ ] No subtask execution occurs prematurely
* [ ] Open questions are captured explicitly

## Variants
* **Dependency graph:** include a DAG-style ordering
* **Time-boxed:** estimate effort per subtask
* **Role-based:** assign an owner/tool to each subtask
* **Two-layer:** phases → subtasks per phase

## Notes
Often paired with **Sequential Multi-Task Patterns** to execute the subtasks after planning. Add **Stop Conditions** between phases if review is required.

## Tags
decomposition, planning, subtasks, workflow, structure, structure, instruction
