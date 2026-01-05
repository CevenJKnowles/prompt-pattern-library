---
id: "ppl-d01-c07-p04"
title: "Prompt Slot-Filling Structures"
type: pattern
status: active
version: 1.0.0
domain: "Instruction & Control"
category: "Modular & Reusable Instruction Components"
subcategory: "Prompt Slot-Filling Structures"
tags:
  - "modularity"
  - "reuse"
  - "instruction-design"
  - "slots"
  - "parameters"
  - "templates"
  - "fill-in"
created: 2026-01-05
updated: 2026-01-05
---

# Prompt Slot-Filling Structures

## Definition
Slot-filling structures define a fixed prompt frame with named slots to be filled at runtime, ensuring consistent structure across varied tasks.

## Intent
Reduce prompt drift and speed up authoring by using a stable frame with explicit insertion points.

## Mechanism
Create a template with slots (e.g., {TASK}, {CONSTRAINTS}) and provide a binding table. Require the model to respect boundaries and only use filled content.

## When to Use
* You need repeatable prompt frames with variable content
* Multiple people contribute to prompts and you want consistency
* You want safer prompts by isolating untrusted inputs

## When Not to Use
* Your task changes the structure every time
* You don’t control how slot values are filled
* The model must infer missing slot content

## Prompt Skeleton
```text
TEMPLATE:
[ROLE]
{ROLE}

[GOAL]
{GOAL}

[INPUT]
{INPUT}

[CONSTRAINTS]
{CONSTRAINTS}

[OUTPUT FORMAT]
{OUTPUT_FORMAT}

BINDINGS:
- ROLE = <...>
- GOAL = <...>
- INPUT = <...>
- CONSTRAINTS = <...>
- OUTPUT_FORMAT = <...>

INSTRUCTION:
Use only the filled slot values. Do not invent bindings.
```

### Example Prompt
```text
TEMPLATE:
[ROLE]
Documentation editor

[GOAL]
Rewrite text for clarity while preserving meaning.

[INPUT]
<paragraph>

[CONSTRAINTS]
- Keep length within ±10%
- No new claims

[OUTPUT FORMAT]
One revised paragraph.

INSTRUCTION:
Use only the filled slot values. Do not invent bindings.
```

### Example Output (Excerpt)
```text
A single revised paragraph with similar length and no added claims.
```

## Failure Modes
* Slots are ambiguous or overlapping
* Unfilled slots cause hallucinated content
* Constraints are not placed where they’re salient

## Evaluation Checklist
* [ ] Slots are clearly labeled
* [ ] All required slots are filled
* [ ] Bindings are explicit
* [ ] Instruction forbids invented bindings
* [ ] Output format is explicit

## Variants
* Add a ‘slot validation’ step
* Add optional slots with defaults
* Create strict vs flexible frames

## Notes
* Use consistent slot labels across the library
* Separate untrusted user text into a dedicated slot
* Keep frames short and scannable

## Tags
* `modularity`
* `reuse`
* `instruction-design`
* `slots`
* `parameters`
* `templates`
* `fill-in`
