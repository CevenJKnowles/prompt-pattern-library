---
id: "ppl-d01-c06-p02"
title: "Imperative Instruction Style"
type: pattern
status: active
version: 1.0.0
domain: "Instruction & Control"
category: "Instruction Style & Tone Control"
subcategory: "Imperative Instruction Style"
tags:
  - "instruction-style"
  - "imperative"
  - "execution"
  - "procedures"
  - "runbooks"
created: 2026-01-05
updated: 2026-01-05
---

# Imperative Instruction Style

## Definition
Imperative Instruction Style is a prompt pattern that forces outputs to be framed as commands or direct instructions, often optimized for execution by a human or another agent.

## Intent
- Produce actionable guidance with minimal interpretation
- Reduce verbosity by focusing on steps and commands
- Support operational runbooks and checklists

## Mechanism
The prompt specifies imperative phrasing (e.g., “Create…”, “Run…”, “Verify…”), optionally enforcing step numbering and command blocks.

## When to Use
- You are writing procedures, runbooks, or SOPs
- You want the output to be immediately executable
- You need consistent action verbs for task automation

## When Not to Use
- The user wants conceptual explanation rather than actions
- The task has multiple valid approaches that require discussion
- Safety-critical actions require confirmation steps or warnings

## Prompt Skeleton
```text
Instruction Style:
- Use imperative verbs (commands).
- Keep each step atomic.
- Include verification steps.

Task:
{task}

Constraints:
{constraints_if_any}
```
### Example Prompt
```text
Instruction Style:
- Use imperative verbs.
- Keep each step atomic.
- Include verification steps.

Task:
Create a new Git branch and push it to origin.

Constraints:
Assume the user is already in the repo directory.
```

### Example Output (Excerpt)
```text
1. Check out main: `git checkout main`.
2. Pull latest: `git pull origin main`.
3. Create the branch: `git checkout -b phase2/content-fill`.
4. Push and set upstream: `git push -u origin phase2/content-fill`.
5. Verify: `git status` shows the upstream tracking branch.
```

## Failure Modes
* Missing verification: steps omit checks that confirm success
* Non-atomic steps: multiple actions merged into one instruction
* Ambiguous prerequisites: assumes tools/permissions without stating them

## Evaluation Checklist
* [ ] Each instruction begins with an action verb
* [ ] Steps are atomic and ordered
* [ ] Verification steps are included where appropriate
* [ ] Assumptions and prerequisites are stated
* [ ] Examples and command blocks match the constraints

## Variants
* Imperative + checklist: require checkboxes for each step
* Imperative + command-only: output only shell commands
* Imperative + safety gates: insert stop/confirm points

## Notes
Imperative outputs can feel abrupt. If user-facing tone matters, add a Tone Control constraint while keeping command structure.

## Tags
instruction-style, imperative, execution, procedures, runbooks
