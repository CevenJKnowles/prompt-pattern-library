---
id: "ppl-d01-c06-p03"
title: "Procedural Instruction Style"
type: pattern
status: active
version: 1.0.0
domain: "Instruction & Control"
category: "Instruction Style & Tone Control"
subcategory: "Procedural Instruction Style"
tags:
  - "instruction-style"
  - "procedural"
  - "sequencing"
  - "prerequisites"
  - "verification"
created: 2026-01-05
updated: 2026-01-05
---

# Procedural Instruction Style

## Definition
Procedural Instruction Style is a prompt pattern that structures the output as a sequence of steps with explicit ordering, prerequisites, and completion criteria.

## Intent
- Ensure predictable step-by-step guidance
- Make dependencies and prerequisites explicit
- Support repeatable processes with clear endpoints

## Mechanism
The prompt requests a numbered procedure and defines required components such as prerequisites, steps, and a final verification step.

## When to Use
- The user needs to follow a repeatable process
- Tasks have prerequisites or order-dependent steps
- You need an audit-friendly procedural record

## When Not to Use
- The task is primarily conceptual or exploratory
- There are many equally good approaches and you need comparison first
- The user wants a quick answer rather than a process

## Prompt Skeleton
```text
Instruction Style:
- Provide a numbered procedure.
- Include prerequisites.
- End with verification criteria.

Task:
{task}

Constraints:
{constraints_if_any}
```
### Example Prompt
```text
Instruction Style:
- Provide a numbered procedure.
- Include prerequisites.
- End with verification criteria.

Task:
Update a feature branch with the latest changes from main.

Constraints:
Use standard Git commands. No links.
```

### Example Output (Excerpt)
```text
Prerequisites: clean working tree.
1. Switch to main and pull.
2. Switch back to your feature branch.
3. Merge or rebase main into the feature branch.
4. Resolve conflicts if any.
5. Verify with `git log` and run tests.
```

## Failure Modes
* Skipped prerequisites: user hits preventable errors mid-process
* Vague verification: no clear success criteria
* Hidden branching: introduces optional paths without labeling them

## Evaluation Checklist
* [ ] Prerequisites are listed before steps
* [ ] Steps are ordered and unambiguous
* [ ] Optional branches are labeled as optional
* [ ] A verification step exists with concrete checks
* [ ] Constraints are respected in examples and outputs

## Variants
* Procedure + decision points: add explicit IF/THEN branches
* Procedure + timeboxing: include time estimates per step
* Procedure + rollback: include recovery steps

## Notes
If the user might choose between merge vs rebase, pair with a Comparison pattern before the procedure, then commit to one approach.

## Tags
instruction-style, procedural, sequencing, prerequisites, verification
