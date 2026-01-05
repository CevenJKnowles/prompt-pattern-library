---
id: "ppl-d01-c08-p03"
title: "Clarification-First Directives"
type: pattern
status: active
version: 1.0.0
domain: "Instruction & Control"
category: "Meta Instructions & Behavioral Anchors"
subcategory: "Clarification First"
tags:
  - "clarifying-questions"
  - "ambiguity-control"
  - "requirements-gathering"
  - "meta-instructions"
created: 2026-01-05
updated: 2026-01-05
---

## Definition

Forces the model to ask targeted clarifying questions before answering when the prompt is ambiguous or underspecified.

## Intent

Prevent wrong assumptions and reduce rework by gathering missing requirements up front.

## Mechanism

Adds a gate: if required parameters are missing, ask N questions; otherwise proceed to answer.

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
If critical details are missing:
1) Ask up to [N] clarifying questions (only questions).
2) Wait for answers.

If details are sufficient:
Proceed with the requested output immediately.
```

### Example Prompt

```text
You are helping me design a workout plan.

Rule: If critical details are missing, ask up to 4 clarifying questions before proposing any plan.

Request: "Make me a workout plan for strength and endurance."
```

### Example Output (Excerpt)

```text
1) What is your current training experience (beginner/intermediate/advanced)?  
2) How many days per week can you train, and how long per session?  
3) Do you have any injuries or constraints (e.g., knees, back, equipment limits)?  
4) What equipment do you have access to (gym, dumbbells, bodyweight only)?
```

## Failure Modes

- Asks too many questions or irrelevant questions.
- Proceeds with assumptions despite missing details.
- Questions are vague and don’t resolve ambiguity.

## Evaluation Checklist

* [ ] Are the questions necessary to produce a correct answer?
* [ ] Are questions specific and actionable?
* [ ] Is the number of questions bounded and respected?
* [ ] Does the model avoid making assumptions before clarification?

## Variants

- Add a 'best-effort default' clause when the user refuses to answer.
- Use a 'must-ask' set of required fields for recurring tasks.

## Notes

Best for planning, specs, and high-cost outputs. For low-stakes tasks, it can add unnecessary friction.

## Tags

- `clarifying-questions`
- `ambiguity-control`
- `requirements-gathering`
- `meta-instructions`
