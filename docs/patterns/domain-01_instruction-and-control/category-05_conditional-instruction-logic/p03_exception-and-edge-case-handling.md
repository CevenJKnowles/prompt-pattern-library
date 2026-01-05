---
id: ppl-d01-c05-p03
title: Exception & Edge-Case Handling
type: pattern
status: active
version: 1.0.0
domain: Instruction & Control
category: Conditional Instruction Logic
subcategory: Exception & Edge-Case Handling
tags:
- conditional-logic
- edge-cases
- exceptions
- robustness
- error-handling
created: 2026-01-05
updated: 2026-01-05
---

# Exception & Edge-Case Handling

## Definition
A prompt pattern that enumerates **exceptions and edge cases** and binds them to explicit handling rules to avoid brittle outputs.

## Intent
- Prevent failure on rare inputs.
- Make exception handling visible.
- Improve safety and correctness at boundaries.

## Mechanism
- List known edge cases as explicit conditions.
- Assign a safe, minimal handling action to each.
- Add a “fallback-to-clarify” rule for unknown edge cases.

## When to Use
- Inputs may be malformed, incomplete, or adversarial.
- You’ve observed recurring failure cases.
- You need safe behavior at system boundaries.

## When Not to Use
- Edge cases are unknown and too numerous.
- You can validate inputs upstream programmatically.
- Over-handling would harm usability (too many caveats).

## Prompt Skeleton
```text
Handle edge cases first:

If {edge_case_1}:
- Do: {edge_action_1}

If {edge_case_2}:
- Do: {edge_action_2}

Otherwise:
- Follow the primary instructions: {primary_action}

If none of the above are confidently applicable:
- Ask: {clarifying_question}

Output format:
{format_spec}
```

### Example Prompt
```text
If the user provides no budget, ask for a budget range.
If the user provides a negative number, ask them to correct it.
Otherwise, recommend 3 options.

Output format: numbered list.
```

### Example Output (Excerpt)
```text
1) Option A …
2) Option B …
3) Option C …
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
conditional-logic, edge-cases, exceptions, robustness, error-handling
