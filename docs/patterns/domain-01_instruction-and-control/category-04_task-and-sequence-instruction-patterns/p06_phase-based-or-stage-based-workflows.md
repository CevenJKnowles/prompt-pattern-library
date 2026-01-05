---
id: ppl-d01-c04-p06
title: Phase-Based or Stage-Based Workflows
type: pattern
status: active
version: 1.0.0
domain: Instruction & Control
category: Task & Sequence Instruction Patterns
subcategory: Phase-Based or Stage-Based Workflows
tags:
- phases
- stages
- workflow
- gating
- planning
created: 2026-01-05
updated: '2026-01-05'
---

# Phase-Based or Stage-Based Workflows

## Definition
Phase-Based or Stage-Based Workflows is a prompt pattern that structures work into named **phases** (e.g., plan → draft → review → finalize) with explicit goals and boundaries for each stage.

## Intent
- Enforce process discipline
- Make multi-step work reviewable and auditable
- Reduce premature finalization
- Support iterative refinement with gates

## Mechanism
The prompt specifies:
- phase names and order
- per-phase objectives and outputs
- constraints on what is allowed in each phase
- optional approval gates between phases

This creates a **staged pipeline** where each phase has a defined role.

## When to Use
- Writing, editing, refactoring workflows
- Projects requiring review steps
- High-stakes outputs needing validation
- Any iterative work where premature final answers are risky

## When Not to Use
- Simple one-shot answers
- Time-critical responses where staging adds friction
- Highly interactive tasks where phases change constantly
- When the user explicitly wants the final output immediately

## Prompt Skeleton
```text
Phases (in order):
1) Plan — outline approach and assumptions.
2) Draft — produce initial output.
3) Review — identify issues and fix them.
4) Finalize — deliver the final version.

Rules:
- Output each phase under "## Phase {n}: {name}".
- Do not perform later-phase work early.
- Stop after each phase if {gate}=true.

```
### Example Prompt

```
Phases (in order):
1) Plan — list required sections and constraints.
2) Draft — write the pattern content.
3) Review — check headings and checkboxes.
4) Finalize — output the final markdown.

Rules:
- Output each phase under "## Phase {n}: {name}".
- Do not perform later-phase work early.
- Stop after each phase if gate=true.
```

### Example Output (Excerpt)

```
## Phase 1: Plan
- Use baseline sections...

## Phase 2: Draft
# Pattern Name...

## Phase 3: Review
- Headings match...

## Phase 4: Finalize
# Pattern Name...
```

## Failure Modes
* **Phase collapse:** skipping phases or merging them
* **Premature finalization:** producing final output during planning
* **Gate ignoring:** continuing despite required stop/review
* **Phase bloat:** adding unnecessary phases without value

## Evaluation Checklist
* [ ] Phases are explicit and ordered
* [ ] Each phase has a clear objective and output
* [ ] No phase work appears outside its boundary
* [ ] Gates are respected when specified
* [ ] Final output reflects review corrections

## Variants
* **Two-phase:** draft → review
* **Multi-review:** add a validation/security phase
* **User-gated:** require explicit user confirmation to proceed
* **Tool-gated:** require tests/metrics before advancing

## Notes
This pattern is a good fit for complex content work in the PPL because it prevents “draft-as-final.” Combine with **Evaluation Checklists** for systematic review.

## Tags
phases, stages, workflow, gating, planning, structure, instruction
