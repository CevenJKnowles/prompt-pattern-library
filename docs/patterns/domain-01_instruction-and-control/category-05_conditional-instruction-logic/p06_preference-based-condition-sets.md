---
id: ppl-d01-c05-p06
title: Preference-Based Condition Sets
type: pattern
status: active
version: 1.0.0
domain: Instruction & Control
category: Conditional Instruction Logic
subcategory: Preference-Based Condition Sets
tags:
- conditional-logic
- preferences
- personalization
- rules
- selection
created: 2026-01-05
updated: 2026-01-05
---

# Preference-Based Condition Sets

## Definition
A prompt pattern that applies conditional rules based on **user preferences** (explicitly stated) to tailor outputs without guesswork.

## Intent
- Personalize without stereotyping or assumptions.
- Make preference rules transparent.
- Ensure consistent application of user constraints.

## Mechanism
- Collect preferences as explicit parameters.
- Map each preference to a rule/constraint.
- Specify precedence when preferences conflict.

## When to Use
- Users specify constraints (tone, length, format, budget).
- You want predictable personalization.
- You need reusable preference presets.

## When Not to Use
- Preferences are unknown and you can’t ask.
- Personalization requires sensitive inference.
- The task demands a neutral, standard output.

## Prompt Skeleton
```text
Preferences (do not infer):
- {pref_1}
- {pref_2}
- {pref_3}

If {pref_1}:
- Apply: {rule_1}

If {pref_2}:
- Apply: {rule_2}

If preferences conflict:
- Resolve by precedence: {precedence_rule}

Output format:
{format_spec}
```

### Example Prompt
```text
Preferences:
- User wants concise answers
- User wants markdown headings
- User wants no tables

Apply these preferences strictly.

Output format: markdown only.
```

### Example Output (Excerpt)
```text
## Summary
- …
## Next steps
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
conditional-logic, preferences, personalization, rules, selection
