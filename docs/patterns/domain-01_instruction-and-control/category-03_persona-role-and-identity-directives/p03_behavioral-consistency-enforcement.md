---
id: ppl-d01-c03-p03
title: Behavioral Consistency Enforcement
type: pattern
status: stub
version: 0.1.0
domain: Instruction & Control
category: Persona, Role & Identity Directives
subcategory: Behavioral Consistency Enforcement
tags:
- consistency
- behavior-control
- self-check
- drift-resistance
- constraint
created: 2026-01-05
updated: '2026-01-05'
---

# Behavioral Consistency Enforcement

## Definition
Enforces stable behaviors (tone, risk posture, formatting, reasoning style) across a session or document.

## Intent
Prevent drift by explicitly naming the behavior rules and requiring the model to self-check before finalizing output.

## Mechanism
* State the behavioral rules (tone, caution level, style).
* Add a self-check instruction against the rules.
* Require correction if any rule is violated.
* Optionally lock response format to reduce variance.

## When to Use
* Long sessions where drift is likely.
* Multi-part documents needing consistent style.
* High-stakes contexts requiring careful boundaries.

## When Not to Use
* You want creative variability and surprise.
* The task is tiny and drift risk is minimal.
* Rules are too many or contradictory.

## Prompt Skeleton
```text
BEHAVIOR RULES:
- Tone: {tone}
- Risk posture: {caution level}
- Style: {style constraints}
SELF-CHECK: Before final answer, verify compliance with all rules; if not compliant, revise.
OUTPUT: {format}
```

### Example Prompt
```text
BEHAVIOR RULES:
- Tone: concise, technical
- Risk posture: no speculation without labeling it
- Style: bullets; no marketing language
SELF-CHECK: verify each bullet is factual or clearly marked guess
OUTPUT: Answer + checklist confirmation
```

### Example Output (Excerpt)
```text
- FACT: …
- GUESS: …
Checklist:
- [x] No marketing language
- [x] Speculation labeled
```

## Failure Modes
* **Rule omission:** some rules not followed.
* **Hidden drift:** starts compliant, ends informal or speculative.
* **Overhead:** self-check bloats output if not constrained.

## Evaluation Checklist
* [ ] Behavior rules are concrete and testable
* [ ] Rules do not conflict
* [ ] Self-check instruction is included
* [ ] Output format supports compliance
* [ ] Final output visibly adheres to rules

## Variants
* **Hard lock:** reject answering until rules can be met.
* **Scored compliance:** rate adherence 1–5 per rule.
* **Session anchor:** restate rules at the start of each response.

## Notes
Keep rule count low (3–7). If needed, group rules into categories (tone, safety, format).

## Tags
consistency, behavior-control, self-check, drift-resistance, constraint
