---
id: ppl-d01-c05-p01
title: If–Then Instruction Patterns
type: pattern
status: active
version: 1.0.0
domain: Instruction & Control
category: Conditional Instruction Logic
subcategory: If–Then Instruction Patterns
tags:
- conditional-logic
- if-then
- rule-enforcement
- branching
- control-flow
created: 2026-01-05
updated: 2026-01-05
---

# If–Then Instruction Patterns

## Definition
A prompt pattern that expresses instructions as explicit **IF / THEN** rules so the model selects actions based on stated conditions.

## Intent
- Reduce ambiguity in conditional requirements.
- Make decision rules explicit and auditable.
- Prevent the model from “averaging” across conflicting cases.

## Mechanism
- State conditions as testable predicates.
- Bind each predicate to a single required action/output.
- Add an explicit **default** clause when no condition matches.

## When to Use
- You have clear business rules or policy logic.
- Different outputs are required for different user states/inputs.
- You want deterministic branching without extra discussion.

## When Not to Use
- Conditions are vague or subjective (e.g., “good”, “appropriate”).
- You need probabilistic exploration rather than a single path.
- The rule set is large enough to require a table or external logic engine.

## Prompt Skeleton
```text
If {condition_A}:
- Do: {action_A}

Else if {condition_B}:
- Do: {action_B}

Else:
- Do: {default_action}

Output format:
{format_spec}
```

### Example Prompt
```text
You are an assistant generating a short reply.

If the user asks for a refund:
- Provide the refund steps in 3 bullets.

Else if the user asks to change an address:
- Provide the address-change steps in 3 bullets.

Else:
- Ask one clarifying question.

Output format: bullet list only.
```

### Example Output (Excerpt)
```text
- To request a refund: (1) … (2) … (3) …
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
conditional-logic, if-then, rule-enforcement, branching, control-flow
