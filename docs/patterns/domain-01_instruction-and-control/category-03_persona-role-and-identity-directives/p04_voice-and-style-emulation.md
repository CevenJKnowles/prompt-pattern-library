---
id: ppl-d01-c03-p04
title: Voice & Style Emulation
type: pattern
status: stub
version: 0.1.0
domain: Instruction & Control
category: Persona, Role & Identity Directives
subcategory: Voice & Style Emulation
tags:
- voice
- style-control
- rewrite
- consistency
- constraint
created: 2026-01-05
updated: '2026-01-05'
---

# Voice & Style Emulation

## Definition
Simulates a specified voice or writing style while preserving the user’s content and constraints.

## Intent
Achieve consistent tone and stylistic features without changing meaning or introducing new facts.

## Mechanism
* Describe the target style using attributes (not a named living author).
* Define what must be preserved (facts, structure, intent).
* Define what must change (tone, diction, rhythm).
* Add “no new facts” and “no invented citations” constraints.

## When to Use
* Brand voice consistency in docs and UI text.
* Editorial rewrites with preserved meaning.
* Generating multiple sections in one coherent style.

## When Not to Use
* You need neutral or purely factual output.
* The style request could bias content (e.g., persuasive when you need balanced).
* You cannot define style features.

## Prompt Skeleton
```text
STYLE TARGET:
- Tone: {tone}
- Diction: {simple|technical|poetic}
- Rhythm: {short|mixed|long}
PRESERVE:
- Facts, intent, key terms
DO NOT:
- Add new facts, mimic a specific living author
OUTPUT: {format}
```

### Example Prompt
```text
STYLE TARGET:
- Tone: calm, clinical
- Diction: plain language
- Rhythm: short sentences
PRESERVE:
- Meaning and key terminology
DO NOT:
- Add new claims
OUTPUT: Rewrite the paragraph + 5 style notes
```

### Example Output (Excerpt)
```text
Rewritten paragraph: …
Style notes:
- Shortened sentences.
- Reduced hedging.
…
```

## Failure Modes
* **Meaning drift:** style rewrite changes claims.
* **Over-stylization:** adds flair that harms clarity.
* **Implicit imitation:** style too closely resembles a specific author.

## Evaluation Checklist
* [ ] Style attributes are explicit (tone/diction/rhythm)
* [ ] Preservation constraints are stated
* [ ] No-new-facts constraint is present
* [ ] Output retains key terminology
* [ ] Style is consistent across the entire output

## Variants
* **Style palette:** 2–3 selectable styles.
* **Controlled intensity:** light vs heavy rewrite.
* **Style + length control:** pair with Length & Granularity.

## Notes
Prefer describing style as attributes. Avoid naming living writers; keep it “brand voice”-oriented.

## Tags
voice, style-control, rewrite, consistency, constraint
