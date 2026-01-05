---
id: ppl-d01-c03-p01
title: Role Assignment Patterns
type: pattern
status: stub
version: 0.1.0
domain: Instruction & Control
category: Persona, Role & Identity Directives
subcategory: Role Assignment Patterns
tags:
- persona
- role
- behavior-control
- instruction
- constraint
created: 2026-01-05
updated: '2026-01-05'
---

# Role Assignment Patterns

## Definition
Assigns an explicit role (e.g., editor, analyst, tutor) to constrain behavior, vocabulary, and decision boundaries.

## Intent
Force predictable behavior by anchoring the model’s responses to a specific role with explicit duties, authority limits, and output expectations.

## Mechanism
* Declare the role and responsibilities in one sentence.
* Set authority boundaries (what it must not do).
* Specify audience and output format expectations.
* Optionally add a calibration line: depth, caution, tone.

## When to Use
* You need consistent framing across multiple prompts.
* You want outputs aligned to a profession or function.
* You are delegating multi-step work and want stable behavior.

## When Not to Use
* The task benefits from open exploration (role may over-constrain).
* You need neutral multi-perspective output without bias toward a role.
* You cannot define the role’s success criteria.

## Prompt Skeleton
```text
ROLE: {role}
TASK: {task}
AUDIENCE: {audience}
BOUNDARIES:
- Must: {must_rules}
- Must not: {must_not_rules}
OUTPUT:
- Format: {format}
- Length/Granularity: {constraints}
```

### Example Prompt
```text
ROLE: Technical editor
TASK: Rewrite the following paragraph for clarity while preserving meaning.
AUDIENCE: General audience
BOUNDARIES:
- Must: Keep all factual claims; keep terminology consistent
- Must not: Add new information; change the author’s intent
OUTPUT:
- Format: Revised paragraph + 3 bullet notes explaining changes
- Length/Granularity: Similar length; simple sentences
```

### Example Output (Excerpt)
```text
Revised paragraph: …
- Changed passive voice to active voice for clarity.
- Split one long sentence into two.
- Standardized terminology (… → …).
```

## Failure Modes
* **Role drift:** model slips into a different voice or task mode.
* **Overreach:** role implies authority (e.g., legal/medical) beyond constraints.
* **Under-specification:** vague role (“expert”) yields inconsistent outputs.

## Evaluation Checklist
* [ ] Role is explicitly named and unambiguous
* [ ] Boundaries include both must and must-not constraints
* [ ] Output expectations are stated (format + depth)
* [ ] Role is appropriate to the task (not over-claiming authority)
* [ ] Response stays in-role across the whole output

## Variants
* **Dual-role:** primary role + secondary reviewer role.
* **Role + rubric:** role plus scoring criteria.
* **Role with escalation:** role can request missing info before answering.

## Notes
Use specific roles (e.g., “grant reviewer”, “UX researcher”) rather than generic (“expert”). Pair with **Scope & Domain Limits** when role could imply risky advice.

## Tags
persona, role, behavior-control, instruction, constraint
