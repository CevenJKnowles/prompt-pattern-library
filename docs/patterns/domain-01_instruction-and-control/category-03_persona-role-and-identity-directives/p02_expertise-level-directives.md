---
id: ppl-d01-c03-p02
title: Expertise-Level Directives
type: pattern
status: stub
version: 0.1.0
domain: Instruction & Control
category: Persona, Role & Identity Directives
subcategory: Expertise-Level Directives
tags:
- expertise-level
- audience-control
- depth
- clarity
- constraint
created: 2026-01-05
updated: '2026-01-05'
---

# Expertise-Level Directives

## Definition
Specifies the level of expertise (beginner, intermediate, expert) to control depth, terminology, and assumptions.

## Intent
Match explanation depth and vocabulary to a defined competence level, preventing over-technical or over-simplified outputs.

## Mechanism
* Declare the target expertise level.
* State assumed prior knowledge (what is already known).
* State forbidden assumptions (what must be explained).
* Set examples/analogies requirement if needed.

## When to Use
* You write docs for a known audience level.
* You need stable depth across a series of answers.
* You want to avoid jargon or, conversely, avoid oversimplification.

## When Not to Use
* Audience is unknown and you cannot infer it.
* You want the model to choose the best depth dynamically.
* The task is purely generative (expertise constraint adds little).

## Prompt Skeleton
```text
EXPERTISE LEVEL: {beginner|intermediate|expert}
ASSUME KNOWN: {assumptions}
MUST EXPLAIN: {concepts}
TERMS:
- Allowed: {allowed_terms}
- Avoid: {avoid_terms}
OUTPUT: {format + depth rules}
```

### Example Prompt
```text
EXPERTISE LEVEL: beginner
ASSUME KNOWN: Basic computer use
MUST EXPLAIN: What a Git branch is, why it matters
TERMS:
- Allowed: commit, branch, main
- Avoid: rebase, detached HEAD
OUTPUT: 5–8 short bullets + 1 tiny command example
```

### Example Output (Excerpt)
```text
- A branch is a separate line of work in the same repo.
- It lets you change files without affecting main.
…
Example:
git checkout -b my-branch
```

## Failure Modes
* **Jargon leak:** advanced terms appear without explanation.
* **Over-simplification:** loses critical nuance for the task.
* **Inconsistent level:** switches between novice and expert mid-answer.

## Evaluation Checklist
* [ ] Target level is explicitly stated
* [ ] Assumptions are listed and realistic
* [ ] Required explanations are included
* [ ] Vocabulary matches the level
* [ ] Output depth stays consistent end-to-end

## Variants
* **Level ladder:** provide beginner + expert versions.
* **Adaptive:** ask 1–2 questions if level is unknown.
* **Constraint stack:** combine with length/granularity limits.

## Notes
If you publish to mixed audiences, consider a “two-layer” answer (simple first, advanced appendix).

## Tags
expertise-level, audience-control, depth, clarity, constraint
