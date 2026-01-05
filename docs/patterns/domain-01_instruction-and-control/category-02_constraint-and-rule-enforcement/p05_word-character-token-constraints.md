---
id: "ppl-d01-c02-p05"
title: "Word/Character/Token Constraints"
type: pattern
status: active
version: 1.0.0
domain: "Instruction & Control"
category: "Constraint & Rule Enforcement"
subcategory: "Word/Character/Token Constraints"
tags:
  - "constraints"
  - "length-control"
  - "tokens"
  - "limits"
  - "format-control"
created: 2026-01-05
updated: 2026-01-05
---
# Word/Character/Token Constraints

## Definition
Word/Character/Token Constraints is a prompt pattern that enforces explicit size limits using counts (words, characters, tokens, bullets, paragraphs), often paired with structural rules to prevent overflow.

## Intent
- Fit outputs into strict UI or platform limits
- Control cost/latency by limiting generation size
- Standardize response size across batch generations

## Mechanism
The prompt declares hard maxima (and optionally minima) and defines how to handle overflow (truncate, prioritize, or refuse). It may also constrain per-item size to prevent a single bullet from bloating.

## When to Use
- UI copy, meta descriptions, SMS, tool fields with strict caps
- Batch outputs where consistent size matters
- Cost/latency sensitive pipelines

## When Not to Use
- When the task requires nuance and cannot be safely compressed
- When the user expects detailed reasoning
- When you cannot meaningfully count tokens/characters in context

## Prompt Skeleton
```text
Length Constraints:
- Max words: {max_words}
- Max characters: {max_chars}
- Max bullets: {max_bullets}
- Per-bullet limit: {per_bullet_limit}

Overflow Policy:
- {overflow_policy}

Task:
{task}
```
### Example Prompt

```text
Length Constraints:
- Max bullets: 4
- Per-bullet limit: 12 words
- No text outside the bullet list

Overflow Policy:
- If you cannot fit, drop the least important point.

Task:
List benefits of schema-normalized prompt patterns.
```

### Example Output (Excerpt)

```text
- Improves consistency across repeated generations.
- Reduces ambiguity in expected output.
- Simplifies maintenance and review.
- Supports scalable prompt authoring.
```

## Failure Modes
* **Limit violation:** Exceeds declared counts or sneaks overflow via long clauses
* **Meaning loss:** Compression removes essential conditions or safety caveats
* **Inconsistent counting:** Word/character counting interpreted loosely across runs
* **Structure mismatch:** Adds headers/extra prose despite rules

## Evaluation Checklist
* [ ] Declared limits are respected
* [ ] No hidden overflow (extra prose outside the allowed area)
* [ ] Per-item constraints are followed consistently
* [ ] Output remains meaningful despite compression
* [ ] Overflow policy is applied deterministically

## Variants
* **Hard max only:** simplest enforcement; easiest to audit
* **Range constraints:** specify min and max for completeness
* **Two-pass:** short answer first; optional expansion only if requested

## Notes
Prefer countable units that match your channel (bullets for lists, characters for UI fields). For token caps, treat them as approximations unless you have programmatic counting.

## Tags
constraints, length-control, tokens, limits, format-control
