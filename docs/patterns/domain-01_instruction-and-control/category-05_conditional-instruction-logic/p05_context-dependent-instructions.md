---
id: ppl-d01-c05-p05
title: Context-Dependent Instructions
type: pattern
status: active
version: 1.0.0
domain: Instruction & Control
category: Conditional Instruction Logic
subcategory: Context-Dependent Instructions
tags:
- conditional-logic
- context
- state
- routing
- constraints
created: 2026-01-05
updated: 2026-01-05
---

# Context-Dependent Instructions

## Definition
A prompt pattern that gates instructions based on **conversation state or provided context**, ensuring outputs match the current scenario.

## Intent
- Prevent applying rules from the wrong context.
- Support stateful workflows (setup → execute → review).
- Make context prerequisites explicit.

## Mechanism
- Declare the context variables/state keys.
- Bind instruction sets to each state.
- Require the model to confirm the detected state (optionally internal).

## When to Use
- Multi-step workflows (intake, plan, execute).
- Different constraints apply at different phases.
- You need stable behavior across long threads.

## When Not to Use
- State is not reliably available in the prompt.
- The task is single-shot and stateless.
- Context rules are too complex without tooling.

## Prompt Skeleton
```text
Context keys:
- State: {state}
- Inputs: {inputs}

If state == "{state_A}":
- Do: {action_A}

If state == "{state_B}":
- Do: {action_B}

Else:
- Ask: {clarifying_question}

Output format:
{format_spec}
```

### Example Prompt
```text
Context:
State: REVIEW

If state == DRAFT: write the draft.
If state == REVIEW: critique in 5 bullets.
Else: ask what stage we are in.

Output format: bullets only.
```

### Example Output (Excerpt)
```text
- Clarity: …
- Completeness: …
- Risk: …
- …
```

## Failure Modes
* **Condition drift:** conditions reinterpreted or broadened beyond the prompt
* **Multi-branch mixing:** output blends two branches instead of selecting one
* **Missing default:** no defined behavior when no condition matches
* **Over-triggering:** fallback triggers too easily and blocks progress

## Evaluation Checklist
* [ ] Conditions are explicit and testable
* [ ] Branches are mutually exclusive or precedence is defined
* [ ] A default / else behavior is specified
* [ ] Output format is fixed and followed
* [ ] No branch mixing occurs in the final output

## Variants
* **Binary:** simple IF/ELSE rule
* **Multi-branch:** decision tree with ordered predicates
* **Table-driven:** condition-action table (read top-down)
* **Two-pass:** detect branch, then generate output under that branch

## Notes
Prefer **explicit predicates** over vague language. If the model must choose a single path, state: **choose exactly one branch**.

## Tags
conditional-logic, context, state, routing, constraints
