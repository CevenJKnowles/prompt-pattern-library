---
id: "ppl-d01-c08-p07"
title: "Instruction Hierarchy & Priority Rules"
type: pattern
status: active
version: 1.0.0
domain: "Instruction & Control"
category: "Meta Instructions & Behavioral Anchors"
subcategory: "Instruction Hierarchy & Priority Rules"
tags:
  - "instruction-hierarchy"
  - "priority-rules"
  - "conflict-resolution"
  - "meta-instructions"
created: 2026-01-05
updated: 2026-01-05
---

## Definition

Defines a precedence system for resolving conflicting instructions within a prompt or across turns.

## Intent

Prevent contradiction and drift when prompts include multiple instruction sources (rules, user goals, format constraints).

## Mechanism

Specifies an ordered list of instruction classes and a conflict-resolution procedure.

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
Instruction precedence (highest to lowest):
1) [Safety / policy rules]
2) [Hard constraints]
3) [Output format requirements]
4) [Style preferences]
5) [Optional suggestions]

If a conflict occurs, follow the higher-ranked instruction and note the adjustment briefly (if allowed).
```

### Example Prompt

```text
Instruction precedence (highest to lowest):
1) Safety rules
2) Hard constraints
3) Output format requirements
4) Style preferences
5) Optional suggestions

Task: "Write a short answer."
Hard constraints: Max 3 sentences.
Output format: Bullet points.
Style: Friendly tone.

Now answer: "What is photosynthesis?"
```

### Example Output (Excerpt)

```text
- Photosynthesis is the process by which plants, algae, and some bacteria convert light energy into chemical energy.  
- They use carbon dioxide and water to produce sugars, releasing oxygen as a byproduct.  
- It’s a foundational pathway that supports most life by supplying both biomass and atmospheric oxygen.
```

## Failure Modes

- No precedence is provided, so conflicts are resolved inconsistently.
- Precedence is provided but not applied in the output.
- Precedence is overly complex, increasing confusion.

## Evaluation Checklist

* [ ] Is the precedence ladder explicit and ordered?
* [ ] Does the output follow the highest-ranked applicable rules?
* [ ] Are conflicts resolved consistently and predictably?
* [ ] Is the ladder minimal and understandable?

## Variants

- Add a step that restates resolved conflicts before answering.
- Use domain-specific ladders (e.g., legal compliance > safety > formatting).

## Notes

Hierarchy rules are especially useful for prompt libraries and agent systems where multiple instruction sources collide.

## Tags

- `instruction-hierarchy`
- `priority-rules`
- `conflict-resolution`
- `meta-instructions`
