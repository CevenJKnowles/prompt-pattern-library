---
id: "ppl-d01-c07-p01"
title: "Reusable Prompt Blocks"
type: pattern
status: active
version: 1.0.0
domain: "Instruction & Control"
category: "Modular & Reusable Instruction Components"
subcategory: "Reusable Prompt Blocks"
tags:
  - "modularity"
  - "reuse"
  - "instruction-design"
  - "prompt-blocks"
  - "composition"
  - "maintainability"
created: 2026-01-05
updated: 2026-01-05
---

# Reusable Prompt Blocks

## Definition
A reusable prompt “block” is a self-contained instruction fragment designed to be copied, versioned, and embedded inside larger prompts without rewriting.

## Intent
Increase consistency and speed by reusing tested instruction fragments across tasks and projects.

## Mechanism
Define a block with a clear name, purpose, inputs, and constraints. Insert it verbatim into prompts and bind variables via a small parameter section.

## When to Use
* You repeat the same instruction patterns across many prompts
* You want standardized behavior across a team or repo
* You need reliable “house style” constraints you can drop into any prompt

## When Not to Use
* The task is one-off and unlikely to be reused
* You cannot keep block boundaries stable (requirements churn daily)
* You need deep adaptation per instance rather than consistency

## Prompt Skeleton
```text
BLOCK: <BLOCK_NAME>
PURPOSE: <one sentence>
INPUTS:
- <input_1>: <type/shape>
- <input_2>: <type/shape>
CONSTRAINTS:
- <constraint_1>
- <constraint_2>
OUTPUT:
- <output format>
END BLOCK

TASK CONTEXT:
<task>

APPLY BLOCKS:
- <BLOCK_NAME> with {<input_1>=..., <input_2>=...}

RETURN:
<requested output>
```

### Example Prompt
```text
BLOCK: CITATION_STYLE
PURPOSE: Ensure claims include sources where applicable.
INPUTS:
- content: text
CONSTRAINTS:
- Cite only reliable sources
- No fabricated citations
OUTPUT:
- Revised content with citations markers
END BLOCK

TASK CONTEXT:
Rewrite the following paragraph for clarity.

APPLY BLOCKS:
- CITATION_STYLE with {content=<paragraph>}

RETURN:
Rewritten paragraph.
```

### Example Output (Excerpt)
```text
Rewritten paragraph with consistent citation markers and no added unverified claims.
```

## Failure Modes
* Block is too vague, leading to inconsistent use
* Inputs are undefined, causing misbinding
* Block grows into a “kitchen sink” and becomes brittle

## Evaluation Checklist
* [ ] Block has a single clear purpose
* [ ] Inputs are explicitly named and bounded
* [ ] Constraints are testable and non-contradictory
* [ ] Block can be pasted without editing its internals
* [ ] Example usage binds inputs explicitly

## Variants
* Add a `VERSION:` line inside the block
* Add a `TEST CASE:` mini-example below the block
* Create a “strict” and “lenient” variant of the same block

## Notes
* Keep blocks short (prefer composition over expansion)
* Treat blocks like API contracts: stable interface, evolving implementation
* Store blocks in the repo so they’re reviewable and diffable

## Tags
* `modularity`
* `reuse`
* `instruction-design`
* `prompt-blocks`
* `composition`
* `maintainability`
