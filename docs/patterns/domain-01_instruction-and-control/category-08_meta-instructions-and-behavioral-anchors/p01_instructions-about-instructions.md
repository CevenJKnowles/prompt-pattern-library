---
id: "ppl-d01-c08-p01"
title: "Instructions About Instructions"
type: pattern
status: active
version: 1.0.0
domain: "Instruction & Control"
category: "Meta Instructions & Behavioral Anchors"
subcategory: "Instructions About Instructions"
tags:
  - "meta-instructions"
  - "instruction-parsing"
  - "policy-layer"
  - "control"
created: 2026-01-05
updated: 2026-01-05
---

## Definition

Defines how to interpret, prioritize, transform, or validate instructions themselves (not the task output).

## Intent

Prevent misinterpretation of complex prompts by explicitly instructing how to treat instruction blocks, constraints, and meta-rules.

## Mechanism

Adds a meta-layer that tells the model how to read the prompt (e.g., treat sections as constraints, ignore examples as non-binding, apply precedence rules).

## When to Use

- When you need reliable, repeatable behavior control above task-level instructions.
- When prompts contain ambiguity, layered constraints, or multi-turn workflows.
- When you want consistent conflict-handling or self-regulation.

## When Not to Use

- When a one-off answer is sufficient and meta-control adds friction.
- When high flexibility is required and strict anchors could reduce usefulness.
- When the additional control layer is likely to confuse the user.

## Prompt Skeleton

```text
Read the prompt as a specification with labeled sections.

1) Identify: Goals, Constraints, Inputs, Output Format.
2) Treat constraints as binding rules.
3) Treat examples as illustrative unless explicitly marked 'binding'.
4) If any instruction conflicts, follow the declared precedence order.

Then produce the requested output following this interpretation.
```

### Example Prompt

```text
Read the following prompt as a specification with labeled sections. Treat constraints as binding; treat examples as illustrative (non-binding). If any instruction conflicts, constraints win.

Goal: Summarize the article below.
Constraints: 
- Use bullet points only.
- Max 6 bullets.
- Include one bullet for uncertainty.

Example (illustrative): "This is a sample style."

Article: "A city introduced a new bike lane network. Early data suggests reduced car traffic, but long-term effects are unclear."
```

### Example Output (Excerpt)

```text
- The city introduced a new bike lane network.
- Early data indicates reduced car traffic after implementation.
- The change suggests a shift toward cycling-friendly infrastructure.
- Impacts may include different commuting patterns and street usage.
- Secondary effects (e.g., safety, business impact) are not yet established.
- Uncertainty: The long-term effects are unclear because only early data is available.
```

## Failure Modes

- Meta-rules are vague, causing the model to invent an interpretation.
- Examples are treated as binding when they should be illustrative (or vice versa).
- Precedence is unspecified, leading to inconsistent handling of conflicts.

## Evaluation Checklist

* [ ] Does the prompt clearly separate binding rules from illustrative examples?
* [ ] Is the interpretation procedure explicit and repeatable?
* [ ] Is precedence defined for conflicts between instructions?
* [ ] Does the output reflect the intended reading of the prompt?

## Variants

- Add an explicit precedence ladder (e.g., safety > constraints > format > style).
- Add a parsing step that restates extracted rules before answering.

## Notes

Use when prompts contain multiple layers (rules, examples, formatting). Keep the meta-protocol short to avoid over-constraining.

## Tags

- `meta-instructions`
- `instruction-parsing`
- `policy-layer`
- `control`
