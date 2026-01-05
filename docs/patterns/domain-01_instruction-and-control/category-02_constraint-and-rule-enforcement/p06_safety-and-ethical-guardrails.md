---
id: "ppl-d01-c02-p06"
title: "Safety & Ethical Guardrails"
type: pattern
status: active
version: 1.0.0
domain: "Instruction & Control"
category: "Constraint & Rule Enforcement"
subcategory: "Safety & Ethical Guardrails"
tags:
  - "safety"
  - "ethics"
  - "constraints"
  - "risk-control"
  - "policy"
created: 2026-01-05
updated: 2026-01-05
---
# Safety & Ethical Guardrails

## Definition
Safety & Ethical Guardrails is a prompt pattern that instructs the model to avoid unsafe, harmful, or high-risk outputs and to follow a defined safe-handling policy (refuse, redirect, or provide safer alternatives).

## Intent
- Reduce harm risk and policy violations
- Ensure cautious handling of high-stakes topics
- Make refusal/redirection behavior consistent and predictable

## Mechanism
The prompt defines prohibited outputs, allowed assistance boundaries, and a fallback procedure. It may require the model to ask clarifying questions or provide general information only.

## When to Use
- Requests may touch safety-critical domains (medical, legal, security, self-harm)
- You need consistent refusal/redirection behavior
- You are building a public-facing assistant or library

## When Not to Use
- When you need unrestricted creative generation (still within platform policy)
- When the task is purely internal and already constrained by other controls (still keep baseline safety rules)
- When guardrails are so broad they block benign content

## Prompt Skeleton
```text
Safety Guardrails:
- Do not provide: {disallowed_assistance}
- Do provide: {allowed_assistance}
- If the request is risky/unclear: {clarify_or_refuse_policy}

Task:
{task}
```
### Example Prompt

```text
Safety Guardrails:
- Do not provide: instructions enabling wrongdoing or harm.
- Do provide: high-level safety information, risk explanations, and safer alternatives.
- If the request is risky/unclear: ask clarifying questions or refuse with a brief explanation.

Task:
Explain how to secure a Git repository without giving step-by-step instructions for hacking accounts.
```

### Example Output (Excerpt)

```text
You can improve repository security by:

- Using strong authentication (e.g., hardware-backed keys where possible).
- Enabling least-privilege access and reviewing collaborator permissions.
- Keeping dependencies updated and scanning for known vulnerabilities.
- Auditing secrets to ensure tokens/keys are not committed.

I can’t help with account takeover instructions, but I can explain defensive best practices.
```

## Failure Modes
* **Over-refusal:** Blocks benign requests due to overly broad interpretation
* **Under-refusal:** Provides actionable harmful details despite guardrails
* **Inconsistent boundary:** Sometimes gives steps, sometimes refuses, without clear rules
* **Moralizing tone:** Adds judgment instead of clear, neutral safety handling

## Evaluation Checklist
* [ ] Disallowed assistance is not provided (including in examples)
* [ ] Allowed assistance is provided clearly and neutrally
* [ ] Fallback policy (clarify/refuse/redirect) triggers consistently
* [ ] Risk is explained at a useful level of abstraction
* [ ] Response avoids unnecessary detail that increases misuse potential

## Variants
* **High-stakes mode:** force extra caution + clarifying questions
* **Defensive-only:** allow only prevention/mitigation guidance
* **Escalation:** suggest professional help/resources for critical topics

## Notes
Guardrails work best when paired with explicit boundaries and a deterministic fallback behavior. Keep the tone neutral: explain why, then offer a safe alternative path.

## Tags
safety, ethics, constraints, risk-control, policy
