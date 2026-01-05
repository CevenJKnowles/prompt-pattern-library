---
id: "ppl-d01-c07-p05"
title: "Modular Instruction Pipelines"
type: pattern
status: active
version: 1.0.0
domain: "Instruction & Control"
category: "Modular & Reusable Instruction Components"
subcategory: "Modular Instruction Pipelines"
tags:
  - "modularity"
  - "reuse"
  - "instruction-design"
  - "pipelines"
  - "stages"
  - "workflow"
  - "composition"
created: 2026-01-05
updated: 2026-01-05
---

# Modular Instruction Pipelines

## Definition
Modular instruction pipelines split a task into staged modules (e.g., plan → draft → verify → format), each with clear outputs feeding the next.

## Intent
Increase quality and reliability by decomposing complex work into auditable stages.

## Mechanism
Define stages with objectives and outputs. Enforce that each stage completes before the next begins, and that intermediate artifacts are preserved.

## When to Use
* Tasks require multiple reasoning steps
* You need traceable intermediate outputs
* You want to separate creativity from verification/formatting

## When Not to Use
* The task is trivial and a pipeline adds overhead
* You cannot afford latency or verbosity
* Intermediate artifacts would leak sensitive info

## Prompt Skeleton
```text
PIPELINE:
1) STAGE: <Name>
   GOAL: <...>
   OUTPUT: <artifact>
2) STAGE: <Name>
   GOAL: <...>
   INPUT: <artifact from prior>
   OUTPUT: <artifact>
...

RULES:
- Complete stages in order
- Do not skip stages
- Preserve stage outputs verbatim

TASK INPUT:
<...>

RUN PIPELINE AND RETURN FINAL OUTPUT.
```

### Example Prompt
```text
PIPELINE:
1) STAGE: Outline
   GOAL: Build a numbered outline
   OUTPUT: Outline
2) STAGE: Draft
   GOAL: Write the draft following the outline
   INPUT: Outline
   OUTPUT: Draft
3) STAGE: Checklist
   GOAL: Validate against constraints
   INPUT: Draft
   OUTPUT: Final Draft

RULES:
- Complete stages in order
- Preserve stage outputs

TASK INPUT:
Write a short guide on keeping prompts reusable.

RUN PIPELINE AND RETURN FINAL OUTPUT.
```

### Example Output (Excerpt)
```text
A final guide produced after outline → draft → checklist stages, with consistent structure.
```

## Failure Modes
* Stages are too large and don’t isolate failure
* Outputs aren’t clearly defined, breaking handoff
* Model collapses stages into one response without labels

## Evaluation Checklist
* [ ] Stages have explicit outputs
* [ ] Order is enforced
* [ ] Intermediate artifacts are labeled
* [ ] Constraints are checked explicitly
* [ ] Final output matches requested format

## Variants
* Add a ‘verification’ stage using a checklist
* Add a ‘compression’ stage to shorten output
* Add a ‘risk flags’ stage for safety concerns

## Notes
* Keep 3–5 stages for most tasks
* Name artifacts consistently
* Avoid mixing evaluation with drafting in the same stage

## Tags
* `modularity`
* `reuse`
* `instruction-design`
* `pipelines`
* `stages`
* `workflow`
* `composition`
