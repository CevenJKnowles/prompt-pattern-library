---
id: "ppl-d01-c06-p01"
title: "Declarative Instruction Style"
type: pattern
status: active
version: 1.0.0
domain: "Instruction & Control"
category: "Instruction Style & Tone Control"
subcategory: "Declarative Instruction Style"
tags:
  - "instruction-style"
  - "declarative"
  - "tone-control"
  - "clarity"
  - "formatting"
created: 2026-01-05
updated: 2026-01-05
---

# Declarative Instruction Style

## Definition
Declarative Instruction Style is a prompt pattern that specifies the desired response style as declarative statements (clear assertions) rather than commands, questions, or procedural steps.

## Intent
- Produce confident, assertive explanations without imperative phrasing
- Reduce ambiguity by framing outputs as statements of fact or policy
- Improve readability in documentation, specs, and summaries

## Mechanism
The prompt explicitly requests declarative sentences, optionally constraining tense, hedging, and modality (e.g., avoid “should/could” unless uncertainty is required).

## When to Use
- You are writing documentation, definitions, or policy-style summaries
- You want an authoritative tone without sounding directive
- You need consistent sentence forms for downstream parsing

## When Not to Use
- The task is a step-by-step procedure (procedural format is more suitable)
- The user expects interactive questioning or Socratic exploration
- High uncertainty requires careful hedging and sourcing

## Prompt Skeleton
```text
Instruction Style:
- Use declarative statements.
- Prefer present tense.
- Avoid imperatives ("Do X") and questions.

Task:
{task}

Constraints:
{constraints_if_any}
```
### Example Prompt
```text
Instruction Style:
- Use declarative statements.
- Prefer present tense.
- Avoid imperatives and questions.

Task:
Describe what Git branches are and how they relate to working directories.

Constraints:
No links. Keep it concise.
```

### Example Output (Excerpt)
```text
A Git branch is a named pointer to a commit. The working directory reflects the files from the currently checked-out branch. Switching branches changes the files on disk to match the selected branch.
```

## Failure Modes
* Imperative leakage: output slips into “Do this / run that” language
* Question drift: output turns into Q&A or prompts the user unnecessarily
* Overconfidence: strong assertions where uncertainty should be stated

## Evaluation Checklist
* [ ] Output is primarily declarative sentences rather than commands
* [ ] Questions are avoided unless explicitly allowed
* [ ] Tone remains clear and non-hyperbolic
* [ ] Any uncertainty is stated explicitly when needed
* [ ] Examples follow the same declarative constraints

## Variants
* Declarative + hedged: allow “may/might” for uncertain statements
* Declarative + definitions: require term-definition pairs
* Declarative + bullet assertions: enforce one assertion per bullet

## Notes
If you need enforceable structure, pair this with Output Structuring patterns (e.g., fixed headings) while keeping sentence forms declarative.

## Tags
instruction-style, declarative, tone-control, clarity, formatting
