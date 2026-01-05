---
id: ppl-d01-c05-p04
title: Fallback Behavior Directives
type: pattern
status: active
version: 1.0.0
domain: Instruction & Control
category: Conditional Instruction Logic
subcategory: Fallback Behavior Directives
tags:
- conditional-logic
- fallback
- safe-defaults
- robustness
- recovery
created: 2026-01-05
updated: 2026-01-05
---

# Fallback Behavior Directives

## Definition
A prompt pattern that defines **fallback behaviors** when the model lacks information, confidence, or required inputs.

## Intent
- Avoid hallucinated specifics.
- Maintain progress when data is missing.
- Standardize recovery paths (ask, summarize, defer).

## Mechanism
- Define triggers for fallback (missing fields, low confidence, ambiguity).
- Specify a single fallback action per trigger.
- Constrain fallback outputs to safe formats (questions, checklists).

## When to Use
- User requests may be underspecified.
- Accuracy requirements are high.
- You want consistent “can’t do X, can do Y” behavior.

## When Not to Use
- You want the model to creatively fill gaps.
- You can reliably fetch missing data with tools.
- The task requires strict completion regardless of uncertainty.

## Prompt Skeleton
```text
Primary task: {primary_task}

If required input {input_X} is missing:
- Fallback: ask {question_X}

If confidence is low:
- Fallback: provide {safe_summary} and ask {one_question}

Otherwise:
- Execute primary task.

Output format:
{format_spec}
```

### Example Prompt
```text
Primary task: draft a project plan.

If the deadline is missing: ask for the deadline date.
If stakeholders are missing: ask who must approve.
Otherwise: produce a 6-step plan.

Output format: markdown bullets only.
```

### Example Output (Excerpt)
```text
- Step 1: …
- Step 2: …
- Step 3: …
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
conditional-logic, fallback, safe-defaults, robustness, recovery
