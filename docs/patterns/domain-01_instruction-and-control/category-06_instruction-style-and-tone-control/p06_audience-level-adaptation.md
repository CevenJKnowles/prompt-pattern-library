---
id: "ppl-d01-c06-p06"
title: "Audience-Level Adaptation"
type: pattern
status: active
version: 1.0.0
domain: "Instruction & Control"
category: "Instruction Style & Tone Control"
subcategory: "Audience-Level Adaptation"
tags:
  - "audience"
  - "adaptation"
  - "difficulty"
  - "clarity"
  - "teaching"
created: 2026-01-05
updated: 2026-01-05
---

# Audience-Level Adaptation

## Definition
Audience-Level Adaptation is a prompt pattern that fixes the target reader’s expertise level and adjusts terminology, pacing, and assumptions accordingly.

## Intent
- Prevent over-technical or under-technical explanations
- Reduce cognitive load by matching the reader’s baseline knowledge
- Improve instructional usefulness for specific audiences

## Mechanism
The prompt specifies audience level (beginner/intermediate/advanced) and sets rules for jargon, examples, and verification steps.

## When to Use
- You are writing for mixed audiences and must choose one level
- The user explicitly states their experience level
- The output will be reused in documentation or teaching materials

## When Not to Use
- The user wants the shortest possible answer regardless of level
- Audience level is unknown and you cannot ask clarifying questions
- The content is inherently advanced and cannot be simplified safely

## Prompt Skeleton
```text
Audience:
- Level: {beginner|intermediate|advanced}
- Jargon: {avoid|allow|prefer}
- Examples: {required|optional}

Task:
{task}

Constraints:
{constraints_if_any}
```
### Example Prompt
```text
Audience:
- Level: beginner
- Jargon: avoid
- Examples: required

Task:
Explain what a Git branch is.

Constraints:
No links. Use one simple analogy.
```

### Example Output (Excerpt)
```text
A branch is like a separate line of work in the same project. It lets you make changes without affecting the main version until you choose to merge those changes back.
```

## Failure Modes
* Level mismatch: uses jargon without defining it
* Over-simplification: removes essential constraints or caveats
* Inconsistent level: starts simple then jumps to advanced details

## Evaluation Checklist
* [ ] Terminology matches the stated audience level
* [ ] Jargon rules are followed consistently
* [ ] Examples are included when required and remain accurate
* [ ] Assumptions are explicit and appropriate for the audience
* [ ] The output remains technically correct despite simplification

## Variants
* Multi-audience: generate three versions for different levels
* Audience + glossary: define key terms inline
* Audience + pacing: limit sentence length and paragraph size

## Notes
If you cannot determine the audience level, pair with a brief Socratic clarification step, then commit to one level for the final output.

## Tags
audience, adaptation, difficulty, clarity, teaching
