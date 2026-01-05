---
id: ppl-d01-c03-p06
title: Cross-Role Switching Prompts
type: pattern
status: stub
version: 0.1.0
domain: Instruction & Control
category: Persona, Role & Identity Directives
subcategory: Cross-Role Switching Prompts
tags:
- multi-pass
- role-switching
- workflow
- quality-control
- constraint
created: 2026-01-05
updated: '2026-01-05'
---

# Cross-Role Switching Prompts

## Definition
Coordinates deliberate switching between roles (e.g., drafter → critic → editor) using explicit phase boundaries.

## Intent
Get multi-pass quality improvements without role confusion by separating phases and outputs.

## Mechanism
* Define phases with role per phase.
* Lock deliverables per phase.
* Prohibit mixing phases in one response unless requested.
* Optionally add a stop/confirm gate between phases.

## When to Use
* You want draft + critique + revision flows.
* You need systematic quality control.
* You want to emulate team handoffs.

## When Not to Use
* You need a single fast answer.
* Roles are unclear or overlapping.
* User can’t manage multi-step outputs.

## Prompt Skeleton
```text
PHASE 1 (ROLE: {role1}): {deliverable1}
PHASE 2 (ROLE: {role2}): {deliverable2}
PHASE 3 (ROLE: {role3}): {deliverable3}
RULE: Do not start next phase until prior phase output is complete (or until user confirms).
```

### Example Prompt
```text
PHASE 1 (ROLE: drafter): produce an outline
PHASE 2 (ROLE: critic): list 5 weaknesses
PHASE 3 (ROLE: editor): revise outline to address weaknesses
RULE: do not blend phases; clearly label outputs
```

### Example Output (Excerpt)
```text
PHASE 1: Outline …
PHASE 2: Weaknesses …
PHASE 3: Revised outline …
```

## Failure Modes
* **Phase mixing:** critique appears inside the draft.
* **Role confusion:** voice changes unpredictably.
* **Runaway scope:** too many phases without limits.

## Evaluation Checklist
* [ ] Phases are explicitly labeled
* [ ] Each phase has one role and one deliverable
* [ ] Rules prevent phase mixing
* [ ] Outputs are clearly separated
* [ ] Total scope and length are bounded

## Variants
* **Gated phases:** require user “OK” before phase 2/3.
* **Two-pass:** draft → revise only.
* **Parallel critics:** 2 critics with different rubrics.

## Notes
This is a structural coordinator pattern; pair with **Bullet/List Control** and **Length & Granularity** to keep phases compact.

## Tags
multi-pass, role-switching, workflow, quality-control, constraint
