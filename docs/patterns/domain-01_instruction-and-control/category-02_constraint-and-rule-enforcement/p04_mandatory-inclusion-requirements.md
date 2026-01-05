---
id: "ppl-d01-c02-p04"
title: "Mandatory Inclusion Requirements"
type: pattern
status: active
version: 1.0.0
domain: "Instruction & Control"
category: "Constraint & Rule Enforcement"
subcategory: "Mandatory Inclusion Requirements"
tags:
  - "constraints"
  - "requirements"
  - "must-include"
  - "completeness"
  - "checklists"
created: 2026-01-05
updated: 2026-01-05
---
# Mandatory Inclusion Requirements

## Definition
Mandatory Inclusion Requirements is a prompt pattern that forces inclusion of specific elements (sections, items, warnings, fields, or steps) to ensure completeness and consistency.

## Intent
- Guarantee critical elements are present (warnings, steps, fields)
- Standardize outputs across multiple runs or authors
- Reduce omission errors in procedural or templated content

## Mechanism
The prompt enumerates required elements and specifies their placement or format. This is often paired with a checklist-style verification step.

## When to Use
- You need repeatable artifact generation (pattern docs, SOPs, tickets)
- There are non-negotiable safety/legal/compliance statements
- You are generating structured documentation with required sections

## When Not to Use
- When the required list is long and brittle (use a template instead)
- When the task benefits from flexible structure
- When requirements are unclear or contradictory

## Prompt Skeleton
```text
Mandatory Requirements:
- Include these sections/items: {required_items}
- Placement/format rules: {placement_rules}

Task:
{task}
```
### Example Prompt

```text
Mandatory Requirements:
- Include: Definition, Intent, Mechanism, When to Use, When Not to Use, Prompt Skeleton, Example Prompt, Example Output (Excerpt), Failure Modes, Evaluation Checklist, Variants, Notes, Tags.
- Placement/format: use the exact headings; include a checklist with [ ] boxes.

Task:
Write the pattern documentation for “Scope & Domain Limits”.
```

### Example Output (Excerpt)

```text
(Excerpt)
## Evaluation Checklist
* [ ] Answer stays within declared in-scope boundaries
* [ ] Out-of-scope topics are not introduced
* [ ] Missing info triggers the specified fallback behavior
```

## Failure Modes
* **Checklist drift:** Required items exist but headings/order diverge from the standard
* **Token compliance:** Mentions required items without providing meaningful content
* **Overconstraint:** Mandatory list forces irrelevant sections for some patterns
* **Inconsistency:** Different runs include different subsets of the mandatory items

## Evaluation Checklist
* [ ] All mandatory sections/items are present
* [ ] Headings match the standard exactly
* [ ] Required items are meaningful, not placeholder text
* [ ] Placement/format rules are respected
* [ ] No extra sections are added when prohibited

## Variants
* **Hard template:** provide a full template the model must fill
* **Minimal must-have list:** only include the top 3–5 critical items
* **Conditional requirements:** include items only when triggers apply

## Notes
When mandatory lists get long, switch to a template (skeleton) with explicit placeholders. Keep mandatory requirements testable—avoid subjective items like “make it good”.

## Tags
constraints, requirements, must-include, completeness, checklists
