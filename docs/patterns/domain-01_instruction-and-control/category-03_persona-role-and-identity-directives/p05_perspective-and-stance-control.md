---
id: ppl-d01-c03-p05
title: Perspective & Stance Control
type: pattern
status: stub
version: 0.1.0
domain: Instruction & Control
category: Persona, Role & Identity Directives
subcategory: Perspective & Stance Control
tags:
- perspective
- stance
- bias-control
- epistemic
- constraint
created: 2026-01-05
updated: '2026-01-05'
---

# Perspective & Stance Control

## Definition
Specifies viewpoint (first/third person), stance (neutral/pro/con), and epistemic posture (certain/uncertain) to control framing.

## Intent
Prevent accidental bias and enforce a consistent perspective and stance across outputs.

## Mechanism
* Declare perspective (I/we/they) and audience.
* Declare stance (neutral, advocate, critic).
* Declare uncertainty policy (label guesses, cite facts if used).
* Lock format to reduce accidental shifts.

## When to Use
* Policy or sensitive topics requiring neutrality.
* Arguments where you need explicit pro/con separation.
* Narrative writing needing stable POV.

## When Not to Use
* Exploratory ideation where stance should evolve.
* Tasks needing multi-stance synthesis unless explicitly structured.
* When stance would conflict with factual reporting.

## Prompt Skeleton
```text
PERSPECTIVE: {first-person|third-person|second-person}
STANCE: {neutral|pro|con|balanced}
UNCERTAINTY POLICY: {label guesses / cite sources / etc.}
OUTPUT: {format + constraints}
```

### Example Prompt
```text
PERSPECTIVE: third-person
STANCE: balanced
UNCERTAINTY POLICY: label guesses explicitly
OUTPUT: 2 sections (Pros / Cons) + 1 neutral conclusion
```

### Example Output (Excerpt)
```text
Pros:
- …
Cons:
- …
Conclusion:
- …
```

## Failure Modes
* **Stance bleed:** “balanced” output subtly advocates one side.
* **POV drift:** switches between first and third person.
* **Certainty inflation:** presents guesses as facts.

## Evaluation Checklist
* [ ] Perspective is explicitly set
* [ ] Stance is explicitly set
* [ ] Uncertainty policy is stated and followed
* [ ] Structure enforces stance separation (if needed)
* [ ] Conclusion matches declared stance

## Variants
* **Dual-stance:** write pro then con, each strongest form.
* **Triptych:** pro / con / synthesis with constraints.
* **Epistemic lock:** facts only; no speculation.

## Notes
For high-stakes topics, pair with **Forbidden Content Rules** and require citations where claims depend on external facts.

## Tags
perspective, stance, bias-control, epistemic, constraint
