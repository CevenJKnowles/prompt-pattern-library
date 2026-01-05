---
id: ppl-d01-c03-p07
title: Personality Anchoring
type: pattern
status: stub
version: 0.1.0
domain: Instruction & Control
category: Persona, Role & Identity Directives
subcategory: Personality Anchoring
tags:
- persona
- anchoring
- drift-resistance
- tone
- constraint
created: 2026-01-05
updated: '2026-01-05'
---

# Personality Anchoring

## Definition
Anchors a stable personality profile (traits, tone, values, boundaries) to reduce drift across sessions or long tasks.

## Intent
Keep outputs consistent with a defined persona without turning every answer into roleplay.

## Mechanism
* Define a compact persona profile (traits + boundaries).
* State allowed behaviors and forbidden behaviors.
* Require consistency with the profile in all responses.
* Add a minimal self-check clause to prevent drift.

## When to Use
* You want consistent assistant behavior over time.
* You need a specific tone (e.g., clinical, playful, strict).
* You are building a reusable agent persona.

## When Not to Use
* Persona constraints could bias objective analysis.
* The task requires multiple voices/perspectives.
* You cannot specify traits clearly.

## Prompt Skeleton
```text
PERSONA ANCHOR:
- Traits: {traits}
- Values: {values}
- Tone: {tone}
- Boundaries: {boundaries}
RULE: Maintain this profile unless user explicitly overrides it.
```

### Example Prompt
```text
PERSONA ANCHOR:
- Traits: direct, precise, calm
- Values: honesty, fairness
- Tone: clinical, low-fluff
- Boundaries: label uncertainty; no invented citations
RULE: keep this across the session
```

### Example Output (Excerpt)
```text
- FACT: …
- GUESS: …
(uncertainty labeled; tone consistent)
```

## Failure Modes
* **Persona overreach:** becomes theatrical or roleplay-heavy.
* **Trait conflict:** traits or values contradict task requirements.
* **Rigidness:** refuses legitimate user overrides.

## Evaluation Checklist
* [ ] Persona profile is concise and concrete
* [ ] Boundaries include uncertainty/citation policy if needed
* [ ] Persona does not distort factual content
* [ ] User override rules are defined
* [ ] Outputs remain consistent across responses

## Variants
* **Light anchor:** 2–3 traits only.
* **Persona + modes:** define mode switching rules.
* **Contextual persona:** different anchors per domain.

## Notes
Keep anchors short. If you need strict formatting, combine with **Output Structuring & Format Control** patterns.

## Tags
persona, anchoring, drift-resistance, tone, constraint
