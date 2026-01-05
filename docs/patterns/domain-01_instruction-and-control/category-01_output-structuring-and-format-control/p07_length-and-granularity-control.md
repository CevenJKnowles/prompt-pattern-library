---
id: ppl-d01-c01-p07
title: "Length & Granularity Control"
type: pattern
status: active
version: 1.0.0
domain: "Instruction & Control"
category: "Output Structuring & Format Control"
subcategory: "Length & Granularity Control"
tags:
  - "structure"
  - "length-control"
  - "granularity"
  - "verbosity"
  - "format-control"
created: 2026-01-05
updated: 2026-01-06
---

# Length & Granularity Control

## Definition
Length & Granularity Control is a prompt pattern that constrains the **amount of content produced** and the **level of detail within that content**, using explicit limits such as word counts, sentence counts, bullet counts, or depth-of-detail instructions.

The pattern focuses on regulating *how much* and *how detailed*, not *what structure* the content takes.

## Intent
- Prevent overlong or underdeveloped responses
- Align output detail with task requirements
- Improve consistency across repeated generations
- Reduce verbosity-related failure modes

## Mechanism
The prompt explicitly specifies:
- quantitative limits (words, sentences, bullets, paragraphs)
- qualitative granularity constraints (high-level vs detailed)
- scope boundaries for elaboration
- prohibitions against exceeding stated limits

This shifts the model from open-ended expansion into **budgeted generation**, where completeness is balanced against constraint.

## When to Use
- Summaries, briefs, or executive overviews
- Responses that must fit UI or documentation constraints
- Batch generation where consistency of length matters
- Any task sensitive to verbosity or detail level

## When Not to Use
- Exploratory analysis requiring open-ended reasoning
- Creative writing where length should emerge naturally
- Tasks with unknown or evolving scope
- Situations where strict limits risk omitting critical nuance

## Prompt Skeleton
```text
Respond in no more than {n} sentences.

Rules:
- Keep each sentence concise.
- Do not exceed the sentence limit.
- Do not include additional sections or prose.

Topic: {topic}
```
### Example Prompt

```
Respond in no more than 4 bullet points.

Rules:
- Each bullet must be one sentence.
- Do not exceed 12 words per bullet.
- Do not include any text outside the list.

Topic: Benefits of schema-normalised prompt patterns
```

### Example Output (Excerpt)

```
- Improves consistency across repeated generations.
- Reduces ambiguity in expected output.
- Simplifies maintenance and review.
- Supports scalable prompt authoring.
```

## Failure Modes
* **Limit violation:** exceeding stated word, sentence, or item counts
* **Artificial compression:** removing essential meaning to meet limits
* **Uneven granularity:** mixing high-level and low-level detail inconsistently
* **Implicit expansion:** adding caveats or qualifiers outside constraints

## Evaluation Checklist
* [ ] Quantitative limits are respected
* [ ] Granularity matches the stated level of detail
* [ ] No hidden overflow (extra clauses, run-ons)
* [ ] Output remains meaningful despite constraints
* [ ] Structure supports the specified length limits

## Variants
* **Hard limit:** strict maximum, no tolerance
* **Range-based:** minimum and maximum bounds
* **Per-item limit:** constraints applied to each list element
* **Two-pass:** constrain length first, expand selectively later

## Notes
This pattern is often combined with **Bullet, Number & List Control** or **Sectioned & Multi-Part Output** to regulate both structure and verbosity. Apply length constraints explicitly; implicit expectations are unreliable.

## Tags
structure, length-control, granularity, verbosity, constraint
```