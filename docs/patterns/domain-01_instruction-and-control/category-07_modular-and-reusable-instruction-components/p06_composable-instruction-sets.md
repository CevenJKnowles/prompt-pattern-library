---
id: "ppl-d01-c07-p06"
title: "Composable Instruction Sets"
type: pattern
status: active
version: 1.0.0
domain: "Instruction & Control"
category: "Modular & Reusable Instruction Components"
subcategory: "Composable Instruction Sets"
tags:
  - "modularity"
  - "reuse"
  - "instruction-design"
  - "composition"
  - "building-blocks"
  - "interfaces"
created: 2026-01-05
updated: 2026-01-05
---

# Composable Instruction Sets

## Definition
Composable instruction sets are small, orthogonal instruction fragments designed to be combined without conflict, like building blocks.

## Intent
Enable flexible prompt construction by combining stable micro-instructions instead of rewriting large monolithic prompts.

## Mechanism
Define each set with scope and constraints. Combine multiple sets explicitly and specify precedence when conflicts occur.

## When to Use
* You want mix-and-match behaviors (tone + format + constraints)
* You need reusable micro-instructions across domains
* You maintain a prompt library with shared components

## When Not to Use
* Instructions are deeply interdependent and can’t be isolated
* You cannot define precedence rules
* You expect frequent conflicts between instruction sets

## Prompt Skeleton
```text
INSTRUCTION SETS:
A) <SET_NAME>
- <directive_1>
- <directive_2>

B) <SET_NAME>
- <directive_1>

COMPOSITION RULES:
- If conflict, precedence: <A over B>
- Do not merge directives; apply in order

TASK:
<task>

APPLY SETS: <A>, <B>

OUTPUT: <format>
```

### Example Prompt
```text
INSTRUCTION SETS:
A) CONCISE_STYLE
- Use short sentences
- No filler

B) STRUCTURED_OUTPUT
- Use headings: Definition, Steps, Checklist

COMPOSITION RULES:
- If conflict, STRUCTURED_OUTPUT wins on format

TASK:
Explain slot-filling prompt frames.

APPLY SETS: CONCISE_STYLE, STRUCTURED_OUTPUT

OUTPUT: Markdown.
```

### Example Output (Excerpt)
```text
A Markdown explanation using the specified headings and concise phrasing.
```

## Failure Modes
* Sets overlap and create contradictions
* No precedence rule, causing unstable outputs
* Sets become too broad and stop being composable

## Evaluation Checklist
* [ ] Sets are orthogonal
* [ ] Precedence is defined
* [ ] Application order is explicit
* [ ] No directive requires hidden context
* [ ] Output format is clear

## Variants
* Add a ‘conflict detector’ checklist
* Provide strict/lenient variants of a set
* Create a compatibility note per set

## Notes
* Design sets to be single-purpose
* Avoid embedding task-specific content in sets
* Prefer 2–4 sets per prompt to reduce conflict

## Tags
* `modularity`
* `reuse`
* `instruction-design`
* `composition`
* `building-blocks`
* `interfaces`
