---
id: ppl-d01-c04-p01
title: Step-by-Step Procedural Tasks
type: pattern
status: active
version: 1.0.0
domain: Instruction & Control
category: Task & Sequence Instruction Patterns
subcategory: Step-by-Step Procedural Tasks
tags:
- procedure
- sequencing
- step-by-step
- task-control
- compliance
created: 2026-01-05
updated: '2026-01-05'
---

# Step-by-Step Procedural Tasks

## Definition
Step-by-Step Procedural Tasks is a prompt pattern that forces the model to execute or describe work as an explicit **ordered sequence of steps**, with each step scoped to a single action or decision.

## Intent
- Reduce skipped steps and implicit leaps
- Improve reproducibility of instructions
- Make multi-step reasoning auditable
- Enable checkpointing and hand-off between steps

## Mechanism
The prompt specifies:
- an explicit step format (numbered steps, one action per step)
- constraints on step size and wording
- rules for when to stop, ask questions, or verify
- optional “pause” checkpoints before continuing

This converts an open-ended response into a **procedural trace** with clear boundaries between actions.

## When to Use
- Tutorials, SOPs, runbooks, checklists
- Tasks where order matters (setup, installation, configuration)
- Safety-critical or compliance-sensitive procedures
- Any workflow where users need to follow along stepwise

## When Not to Use
- Pure brainstorming where order is irrelevant
- Creative writing with emergent structure
- Very small tasks where steps add unnecessary overhead
- Situations where the user explicitly wants a concise direct answer

## Prompt Skeleton
```text
Task: {task}

Output format:
- Provide a numbered list of steps.
- One action per step.
- Keep each step <= {max_words} words.

Rules:
- Do not skip steps.
- If a required input is missing, stop and ask for it.
- End with: "Stop."
```
### Example Prompt

```
Task: Configure a Git branch workflow for content edits.

Output format:
- Provide a numbered list of steps.
- One action per step.
- Keep each step <= 18 words.

Rules:
- Do not skip steps.
- If a required input is missing, stop and ask for it.
- End with: "Stop."
```

### Example Output (Excerpt)

```
1. Ensure your working tree is clean with `git status`.
2. Switch to `main` and pull latest with `git checkout main` + `git pull`.
3. Create and switch to a branch with `git checkout -b phase2/content-fill`.
4. Push the branch upstream using `git push -u origin phase2/content-fill`.
5. Make edits, then commit in small batches.
Stop.
```

## Failure Modes
* **Step skipping:** jumping from setup to outcome without intermediate actions
* **Step bundling:** combining multiple actions into one step
* **Unclear prerequisites:** assuming tools/inputs exist without stating them
* **Non-terminating flow:** continuing after missing inputs instead of stopping

## Evaluation Checklist
* [ ] Steps are strictly ordered and numbered
* [ ] Each step contains a single action or decision
* [ ] Preconditions and required inputs are explicit
* [ ] The procedure stops to ask questions when needed
* [ ] The final output is executable by the target user

## Variants
* **Checkpointed:** pause after each step and wait for user confirmation
* **Two-level:** steps with substeps for fine-grained execution
* **Guardrailed:** include safety/validation checks per step
* **Time-boxed:** limit the number of steps or total length

## Notes
This pattern pairs well with **Termination & Stop Conditions** and **Precision & Fidelity Requirements** to prevent the model from “running ahead.”

## Tags
procedure, sequencing, step-by-step, task-control, compliance, structure, instruction
