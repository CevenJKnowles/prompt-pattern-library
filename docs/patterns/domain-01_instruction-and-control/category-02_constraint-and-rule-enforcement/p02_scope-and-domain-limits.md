---
id: "ppl-d01-c02-p02"
title: "Scope & Domain Limits"
type: pattern
status: active
version: 1.0.0
domain: "Instruction & Control"
category: "Constraint & Rule Enforcement"
subcategory: "Scope & Domain Limits"
tags:
  - "constraints"
  - "scope"
  - "domain"
  - "boundaries"
  - "risk-control"
created: 2026-01-05
updated: 2026-01-05
---
# Scope & Domain Limits

## Definition
Scope & Domain Limits is a prompt pattern that constrains *what* the model may cover by defining in-scope topics, out-of-scope topics, and boundaries for assumptions or external speculation.

## Intent
- Prevent tangents and unbounded expansions
- Reduce hallucination risk by limiting conjecture
- Keep responses aligned to a specific domain, audience, or artifact

## Mechanism
The prompt declares scope boundaries (in/out), allowable sources of information, and what to do when the user request exceeds scope (refuse, ask, or provide a minimal safe redirect).

## When to Use
- You need domain-accurate output (legal/medical/finance-adjacent, or other high-stakes areas)
- You are generating content for a bounded artifact (a repo section, a specific doc page)
- You want to prevent speculative filler

## When Not to Use
- Open exploration/brainstorming where scope discovery is the goal
- Early research where you want broad coverage and mapping
- When the task requires cross-domain synthesis

## Prompt Skeleton
```text
Scope:
- In-scope: {in_scope}
- Out-of-scope: {out_of_scope}
- Allowed assumptions: {assumptions_policy}
- Sources: {sources_policy}

If the request is out-of-scope:
- {fallback_behavior}

Task:
{task}
```
### Example Prompt

```text
Scope:
- In-scope: Git branching workflow in this repository (local + remote).
- Out-of-scope: Git rebase strategies, advanced CI/CD, GitHub Actions configuration.
- Allowed assumptions: none; ask if missing details.
- Sources: repository state and standard Git behavior only.

If the request is out-of-scope:
- Provide a one-sentence redirect and stop.

Task:
Explain how to create a new branch and push it to origin.
```

### Example Output (Excerpt)

```text
To create and push a branch:

- Ensure main is current:
  - git checkout main
  - git pull origin main

- Create and switch:
  - git checkout -b phase2/content-fill

- Push and set upstream:
  - git push -u origin phase2/content-fill
```

## Failure Modes
* **Scope creep:** Answer expands into adjacent topics (e.g., rebase, CI) despite being out-of-scope
* **Silent assumptions:** Model fills missing details without flagging uncertainty
* **Over-restriction:** Scope is so tight the answer becomes unhelpful
* **Mismatch:** Declared scope contradicts the actual task requirements

## Evaluation Checklist
* [ ] Answer stays within declared in-scope boundaries
* [ ] Out-of-scope topics are not introduced
* [ ] Missing info triggers the specified fallback behavior
* [ ] Assumptions are handled according to policy
* [ ] The scoped answer still solves the stated task

## Variants
* **Whitelist scope:** enumerate only allowed topics and refuse everything else
* **Budgeted scope:** allow one adjacent clarification but no expansion
* **Source-bounded:** only use provided docs/files; otherwise ask

## Notes
Scope boundaries are easiest to follow when expressed as explicit in/out lists plus a deterministic fallback rule. Avoid vague phrases like “keep it short” when scope is the real constraint.

## Tags
constraints, scope, domain, boundaries, risk-control
