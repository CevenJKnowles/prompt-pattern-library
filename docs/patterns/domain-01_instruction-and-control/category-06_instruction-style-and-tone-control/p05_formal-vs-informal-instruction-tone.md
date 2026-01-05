---
id: "ppl-d01-c06-p05"
title: "Formal vs Informal Instruction Tone"
type: pattern
status: active
version: 1.0.0
domain: "Instruction & Control"
category: "Instruction Style & Tone Control"
subcategory: "Formal vs Informal Instruction Tone"
tags:
  - "tone-control"
  - "register"
  - "formal"
  - "informal"
  - "consistency"
created: 2026-01-05
updated: 2026-01-05
---

# Formal vs Informal Instruction Tone

## Definition
Formal vs Informal Instruction Tone is a prompt pattern that explicitly sets the register of instructions (formal/professional vs casual/conversational) while keeping content constraints intact.

## Intent
- Align tone with audience expectations (workplace vs personal)
- Improve clarity by controlling slang, contractions, and politeness markers
- Maintain consistent voice across a documentation set

## Mechanism
The prompt specifies register rules (e.g., contractions allowed/disallowed, politeness level, emoji policy) and may provide a short tone sample.

## When to Use
- You need consistent tone across many files
- You are adapting instructions for different audiences
- You want to reduce perceived harshness of imperative outputs

## When Not to Use
- The tone is already dictated by a corporate style guide
- The user wants content-first and does not care about register
- The requested tone conflicts with safety or compliance constraints

## Prompt Skeleton
```text
Tone Control:
- Register: {formal|informal}
- Contractions: {allow|disallow}
- Politeness: {low|medium|high}
- Emoji: {none|limited|allowed}

Task:
{task}

Constraints:
{constraints_if_any}
```
### Example Prompt
```text
Tone Control:
- Register: formal
- Contractions: disallow
- Politeness: medium
- Emoji: none

Task:
Explain how to create a Git branch and set upstream.

Constraints:
No links. Keep it concise.
```

### Example Output (Excerpt)
```text
First, switch to the repository directory. Next, create the branch with `git checkout -b <branch-name>`. Then push the branch and set upstream with `git push -u origin <branch-name>`.
```

## Failure Modes
* Register drift: mixes formal and casual phrasing
* Overpoliteness: adds filler that reduces clarity
* Tone overrides content: focuses on voice instead of correctness

## Evaluation Checklist
* [ ] Register matches the requested tone throughout
* [ ] Contractions and emoji rules are followed
* [ ] Tone constraints do not reduce technical accuracy
* [ ] Output remains concise and actionable when required
* [ ] Examples reflect the same register constraints

## Variants
* Tone + style sample: include a 2–3 sentence voice sample
* Tone + taboo list: forbid slang words or phrases
* Tone + localization: specify regional spelling conventions

## Notes
Tone constraints should be lightweight. If you need strict formatting, combine with Output Structuring patterns and keep tone secondary.

## Tags
tone-control, register, formal, informal, consistency
