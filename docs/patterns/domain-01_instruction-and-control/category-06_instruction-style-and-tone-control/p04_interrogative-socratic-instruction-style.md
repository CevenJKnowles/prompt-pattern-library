---
id: "ppl-d01-c06-p04"
title: "Interrogative / Socratic Instruction Style"
type: pattern
status: active
version: 1.0.0
domain: "Instruction & Control"
category: "Instruction Style & Tone Control"
subcategory: "Interrogative / Socratic Instruction Style"
tags:
  - "instruction-style"
  - "socratic"
  - "questions"
  - "requirements"
  - "teaching"
created: 2026-01-05
updated: 2026-01-05
---

# Interrogative / Socratic Instruction Style

## Definition
Interrogative / Socratic Instruction Style is a prompt pattern that forces the assistant to guide via questions, progressively eliciting constraints and assumptions before offering a solution.

## Intent
- Surface missing requirements and reduce incorrect assumptions
- Support teaching, coaching, and exploratory problem solving
- Increase user control over decisions and trade-offs

## Mechanism
The prompt requests a sequence of targeted questions (often grouped), optionally followed by a provisional plan once enough information is gathered.

## When to Use
- Requirements are ambiguous or under-specified
- You are tutoring or facilitating decision-making
- Wrong assumptions would cause rework or risk

## When Not to Use
- The user asked for immediate execution without questions
- The task is routine and well-specified
- The user is time-constrained and cannot answer follow-ups

## Prompt Skeleton
```text
Instruction Style:
- Ask clarifying questions first (Socratic).
- Group questions by theme.
- After answers, propose a concise plan.

Task:
{task}

Constraints:
{constraints_if_any}
```
### Example Prompt
```text
Instruction Style:
- Ask clarifying questions first.
- Group questions by theme.
- After answers, propose a concise plan.

Task:
Help me configure GitHub Pages deployment for MkDocs.

Constraints:
No links.
```

### Example Output (Excerpt)
```text
Questions (Environment): Which CI runner are you using? Are you deploying from a docs/ folder or repo root?
Questions (Branching): Is Pages set to deploy from a branch or GitHub Actions?
Provisional plan: Once confirmed, I will outline the exact mkdocs.yml and workflow steps.
```

## Failure Modes
* Question overload: too many questions without prioritization
* Never converges: keeps asking instead of proposing a plan
* Assumption creep: answers questions itself instead of waiting

## Evaluation Checklist
* [ ] Questions are necessary and prioritized
* [ ] Questions are grouped logically
* [ ] A convergence point is defined (when to start proposing solutions)
* [ ] No major assumptions are introduced without user input
* [ ] A provisional plan is concise and consistent with constraints

## Variants
* Socratic minimal: ask 2–5 highest-impact questions only
* Socratic + decision table: present options after questions
* Socratic + teaching: explain why each question matters

## Notes
Use this pattern sparingly in execution contexts. If the user has already decided, switch to a procedural or imperative style.

## Tags
instruction-style, socratic, questions, requirements, teaching
