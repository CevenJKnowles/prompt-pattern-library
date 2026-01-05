---
id: "ppl-d01-c02-p01"
title: "Style & Tone Restrictions"
type: pattern
status: active
version: 1.0.0
domain: "Instruction & Control"
category: "Constraint & Rule Enforcement"
subcategory: "Style & Tone Restrictions"
tags:
  - "constraints"
  - "tone"
  - "style"
  - "register"
  - "format-control"
created: 2026-01-05
updated: 2026-01-05
---
# Style & Tone Restrictions

## Definition
Style & Tone Restrictions is a prompt pattern that specifies an allowed voice, register, and stylistic profile (and optionally forbids others) while preserving the task’s substantive requirements.

## Intent
- Stabilize output voice across runs, authors, or agents
- Prevent unwanted stylistic drift (hype, sarcasm, legalese, excessive hedging)
- Match channel constraints (docs, UI copy, support, academic writing)

## Mechanism
The prompt sets a target tone/register and lists crisp rules (allowed and forbidden features). Rules are treated as hard constraints, separate from task content, to reduce accidental coupling.

## When to Use
- You need consistent voice across many outputs (docs, patterns, templates)
- Your org/product requires a defined communication style
- You need to prevent specific stylistic failure modes (e.g., no emojis, no marketing)

## When Not to Use
- Creative writing or voice exploration (unless the exploration itself is bounded)
- Early-stage problem solving where correctness is the only priority
- When you actually want adaptive tone by audience (then specify audience constraints instead)

## Prompt Skeleton
```text
You are writing for {audience}.

Style & Tone Rules:
- Tone: {tone}
- Register: {register}
- Forbidden: {forbidden_features}
- Required: {required_features}
- If uncertain: state uncertainty and what would resolve it.

Task:
{task}
```
### Example Prompt

```text
You are writing for a technical documentation audience.

Style & Tone Rules:
- Tone: calm, direct, non-fluffy.
- Register: professional, plain language.
- Forbidden: emojis, rhetorical questions, marketing language.
- Required: short paragraphs and bullet lists.
- If uncertain: state what is uncertain and how to confirm it.

Task:
Explain how to create and switch Git branches locally, then push a new branch to origin.
```

### Example Output (Excerpt)

```text
To create and push a new branch:

- Update main:
  - git checkout main
  - git pull origin main

- Create and switch:
  - git checkout -b phase2/content-fill

- Push and set upstream:
  - git push -u origin phase2/content-fill
```

## Failure Modes
* **Rule conflict:** Combining mutually exclusive constraints (e.g., “be exhaustive” + “no more than 3 bullets”)
* **Over-constraint:** Style rules suppress necessary warnings, nuance, or completeness
* **Leakage:** Forbidden features reappear (emojis, slang, hype) under pressure
* **Coupling:** Style rules accidentally change the substantive content requirements

## Evaluation Checklist
* [ ] Output matches the stated tone and register
* [ ] Forbidden features are absent
* [ ] Task content remains complete despite style constraints
* [ ] Uncertainty is disclosed clearly and actionably when relevant
* [ ] Style rules are separated from content rules (or intentionally coupled)

## Variants
* **Preset styles:** RFC tone, academic abstract, support ticket, release notes
* **Channel-specific:** Slack message, README section, PR comment
* **Negative-only constraints:** list only what to avoid when you want flexibility

## Notes
Keep style rules short (5–10 bullets). If you need both consistency and adaptability, specify audience and context first, then constrain tone within bounds.

## Tags
constraints, tone, style, register, format-control
