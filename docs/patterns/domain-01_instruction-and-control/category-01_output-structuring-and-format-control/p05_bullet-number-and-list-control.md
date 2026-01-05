---
id: ppl-d01-c01-p05
title: "Bullet, Number & List Control"
type: pattern
status: active
version: 1.0.0
domain: "Instruction & Control"
category: "Output Structuring & Format Control"
subcategory: "Bullet, Number & List Control"
tags:
  - "structure"
  - "lists"
  - "bullets"
  - "numbering"
  - "format-control"
created: 2026-01-05
updated: 2026-01-06
---

# Bullet, Number & List Control

## Definition
Bullet, Number & List Control is a prompt pattern that constrains the model’s output into **explicit list structures**, such as bullet points, numbered lists, or ordered/unordered sequences, with clear rules governing item count, ordering, and formatting.

The focus is on **enumeration discipline** rather than prose flow.

## Intent
- Enforce clear itemisation of ideas, steps, or attributes
- Improve scanability and readability
- Prevent narrative drift in multi-point responses
- Enable predictable, comparable list-based outputs

## Mechanism
The prompt explicitly specifies:
- the list type (bulleted, numbered, ordered, unordered)
- formatting rules (markers, indentation, numbering style)
- constraints on list length or item count
- prohibitions against prose outside list items

This shifts the model from paragraph generation into **item-by-item completion**, reducing verbosity and structural inconsistency.

## When to Use
- Enumerating steps, requirements, features, or criteria
- Producing checklists, task lists, or summaries
- Structuring responses that must be easily scannable
- Situations where order or count of items matters

## When Not to Use
- Long-form explanation or narrative reasoning
- Highly interconnected ideas that do not decompose cleanly
- Creative writing where rigid enumeration is restrictive
- Tasks where nuance would be lost by forced listing

## Prompt Skeleton
```text
Respond using a numbered list with exactly {n} items.

Rules:
- Use numbers only.
- Do not include sub-bullets.
- Keep each item to one sentence.
- Do not include prose outside the list.

Topic: {topic}
```
### Example Prompt
```
Respond using a numbered list with exactly 5 items.

Rules:
- Use numbers only.
- Do not include sub-bullets.
- Keep each item to one sentence.
- Do not include prose outside the list.

Topic: Key risks in prompt pattern over-constraining
```

### Example Output (Excerpt)
```
1. Reduced flexibility when task requirements change.
2. Increased failure rates on ambiguous inputs.
3. Overly rigid outputs that obscure nuance.
4. Higher prompt maintenance overhead.
5. User frustration due to constrained responses.
```

## Failure Modes

* **List drift:** switching between bullets and numbers mid-output
* **Item count violations:** more or fewer items than specified
* **Prose leakage:** introductory or concluding paragraphs outside the list
* **Overloaded items:** multiple ideas crammed into a single bullet

## Evaluation Checklist

* [ ] List type matches the prompt specification
* [ ] Item count adheres to stated constraints
* [ ] Formatting markers are consistent
* [ ] No prose appears outside list items
* [ ] Each item is semantically self-contained

## Variants

* **Fixed-count list:** exact number of items enforced
* **Priority list:** ordered list ranked by importance
* **Checklist:** binary or action-oriented items
* **Two-pass:** generate list first, then expand items separately

## Notes

This pattern pairs well with **Length & Granularity Control** when both item count and detail level must be managed. Avoid combining with free-form explanation unless listing is performed first.

## Tags

structure, lists, bullets, numbering, enumeration, format-control
