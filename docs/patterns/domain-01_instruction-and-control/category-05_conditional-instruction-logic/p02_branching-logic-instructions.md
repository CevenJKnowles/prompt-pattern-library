---
id: ppl-d01-c05-p02
title: Branching Logic Instructions
type: pattern
status: active
version: 1.0.0
domain: Instruction & Control
category: Conditional Instruction Logic
subcategory: Branching Logic Instructions
tags:
- conditional-logic
- branching
- decision-tree
- control-flow
- output-routing
created: 2026-01-05
updated: 2026-01-05
---

# Branching Logic Instructions

## Definition
A prompt pattern that encodes **multi-branch decision logic** (tree-like) so the model routes to one of several defined response paths.

## Intent
- Support more than two branches cleanly.
- Keep complex routing readable.
- Ensure mutually exclusive paths are handled without overlap.

## Mechanism
- Define a decision order (top-down).
- Enforce **single-path selection** (“choose exactly one branch”).
- Require the model to report which branch was chosen (optionally hidden from final output).

## When to Use
- You have 3+ distinct response modes.
- You need consistent triage (support, safety, escalation).
- You want predictable routing across many inputs.

## When Not to Use
- Branches overlap heavily or require fuzzy matching.
- Routing requires external data not available in-context.
- You need the model to combine multiple branches.

## Prompt Skeleton
```text
Decision tree (choose exactly ONE branch):

1) If {predicate_1} -> Branch 1: {action_1}
2) Else if {predicate_2} -> Branch 2: {action_2}
3) Else if {predicate_3} -> Branch 3: {action_3}
4) Else -> Default: {default_action}

Output format:
{format_spec}
```

### Example Prompt
```text
Choose exactly one branch:

1) If the user message contains a concrete question -> Answer directly in 5 bullets.
2) Else if it contains a complaint -> Apologize once + propose 3 fixes.
3) Else if it is unclear -> Ask 2 clarifying questions.
4) Else -> Provide a 1-sentence summary.

Output format: plain text only.
```

### Example Output (Excerpt)
```text
- …
- …
- …
- …
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
conditional-logic, branching, decision-tree, control-flow, output-routing
