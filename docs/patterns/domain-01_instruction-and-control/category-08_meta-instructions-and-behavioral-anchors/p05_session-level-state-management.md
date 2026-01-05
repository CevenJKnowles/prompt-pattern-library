---
id: "ppl-d01-c08-p05"
title: "Session-Level State Management"
type: pattern
status: active
version: 1.0.0
domain: "Instruction & Control"
category: "Meta Instructions & Behavioral Anchors"
subcategory: "Session-Level State Management"
tags:
  - "state-management"
  - "session-memory"
  - "variables"
  - "meta-instructions"
created: 2026-01-05
updated: 2026-01-05
---

## Definition

Makes the model maintain explicit state variables across turns and update them deterministically.

## Intent

Reduce drift and confusion in multi-step processes by keeping an explicit, user-visible state representation.

## Mechanism

Defines named state fields and update rules; each response includes the current state plus requested output.

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
Maintain a session state object with fields:
- [field]: [meaning]
Rules:
- Update state only when new info is provided.
- Do not infer state values without evidence.
In each response:
1) Print STATE:
2) Then provide the requested output.
```

### Example Prompt

```text
Maintain a session state object with fields:
- goal: the user’s goal
- constraints: hard rules
- next_step: what we will do next

Rules:
- Update state only when the user provides new info.
- Do not infer missing values.

Now: The user says, "I want a 3-day meal plan. Vegetarian. 30 minutes max cooking per meal."
```

### Example Output (Excerpt)

```text
STATE:
- goal: 3-day meal plan
- constraints: vegetarian; ≤30 minutes cooking per meal
- next_step: ask for dietary preferences (calories, allergies) OR propose a default plan

Output:
To tailor the plan, do you have any allergies or foods you want to avoid? If not, I can propose a balanced default 3‑day vegetarian plan with quick recipes under 30 minutes.
```

## Failure Modes

- State is updated based on assumptions rather than user-provided info.
- State becomes too verbose and crowds out useful output.
- State fields are inconsistent or renamed mid-session.

## Evaluation Checklist

* [ ] Are state fields clearly defined and stable?
* [ ] Are updates deterministic and evidence-based?
* [ ] Does the response clearly separate state from output?
* [ ] Is state concise enough to be usable?

## Variants

- Add a CHANGELOG section that lists updates since last state.
- Use JSON state for tool-friendly workflows.

## Notes

Explicit state is especially useful for planning, specs, and long constraints. Keep the state minimal and user-relevant.

## Tags

- `state-management`
- `session-memory`
- `variables`
- `meta-instructions`
