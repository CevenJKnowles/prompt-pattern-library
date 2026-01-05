---
id: "ppl-d01-c02-p03"
title: "Forbidden Content Rules"
type: pattern
status: active
version: 1.0.0
domain: "Instruction & Control"
category: "Constraint & Rule Enforcement"
subcategory: "Forbidden Content Rules"
tags:
  - "constraints"
  - "forbidden"
  - "redlines"
  - "compliance"
  - "safety"
created: 2026-01-05
updated: 2026-01-05
---
# Forbidden Content Rules

## Definition
Forbidden Content Rules is a prompt pattern that lists content that must not appear in the output (topics, claims, formats, or behaviors), often paired with an explicit refusal or substitution policy.

## Intent
- Prevent inclusion of disallowed material (policy, legal, brand, or project rules)
- Reduce risk of accidental sensitive disclosure
- Enforce clean-room writing constraints (no quotes, no links, no proprietary names)

## Mechanism
The prompt defines a set of forbidden items and specifies how to respond if the task would require them (omit, generalize, refuse, or ask for an alternative).

## When to Use
- You must enforce redlines (no personal data, no internal code names, no competitor mention)
- You want to avoid certain rhetorical styles (no hype, no fear appeals)
- You are publishing under constraints (no URLs, no quotations, no citations)

## When Not to Use
- When the user expects a comprehensive survey including restricted items
- When forbidden rules are vague or subjective and likely to conflict
- When a safer approach is to redefine the task objective instead

## Prompt Skeleton
```text
Forbidden Content Rules:
- Do not include: {forbidden_items}
- Do not do: {forbidden_behaviors}

If the task requires forbidden content:
- {fallback_behavior}

Task:
{task}
```
### Example Prompt

```text
Forbidden Content Rules:
- Do not include: URLs, personal data, internal repository secrets.
- Do not do: speculate about private configuration.

If the task requires forbidden content:
- Say you cannot provide that, and offer a safe alternative.

Task:
Explain Git branching and pushing without using any links.
```

### Example Output (Excerpt)

```text
Steps:

- Update main:
  - git checkout main
  - git pull origin main

- Create branch:
  - git checkout -b phase2/content-fill

- Push:
  - git push -u origin phase2/content-fill
```

## Failure Modes
* **Rule leakage:** Forbidden elements appear indirectly (e.g., “search for …” implies links)
* **Overblocking:** Model refuses safe content because the forbidden list is ambiguous
* **Inconsistent fallback:** Sometimes omits, sometimes refuses, without a consistent rule
* **Masked violations:** Forbidden content appears in code blocks or examples

## Evaluation Checklist
* [ ] No forbidden topics, elements, or behaviors appear
* [ ] Fallback behavior triggers consistently when needed
* [ ] Output remains useful while respecting redlines
* [ ] Examples and code blocks comply with the same rules
* [ ] Forbidden list is specific and testable

## Variants
* **Hard redlines:** refusal if any forbidden material is necessary
* **Substitution policy:** replace with placeholders (e.g., {REDACTED})
* **Format bans:** forbid specific output formats (tables, JSON, code blocks)

## Notes
Keep forbidden lists concrete. If you need complex compliance, pair this with an evaluation checklist and a final self-audit instruction (e.g., “scan for URLs before final answer”).

## Tags
constraints, forbidden, redlines, compliance, safety
