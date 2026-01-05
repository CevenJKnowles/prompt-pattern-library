---
id: ppl-d01-c01-p06
title: "Sectioned & Multi-Part Output"
type: pattern
status: active
version: 1.0.0
domain: "Instruction & Control"
category: "Output Structuring & Format Control"
subcategory: "Sectioned & Multi-Part Output"
tags:
  - "structure"
  - "sections"
  - "multi-part"
  - "format-control"
created: 2026-01-05
updated: 2026-01-06
---

# Sectioned & Multi-Part Output

## Definition
Sectioned & Multi-Part Output is a prompt pattern that constrains the model’s response into **explicit, named sections or parts**, each serving a distinct role within a single response.

Unlike outlines (which emphasise hierarchy) or templates (which emphasise reusability), this pattern focuses on **clear segmentation of content by function**.

## Intent
- Separate different types of content within one response
- Improve readability by isolating concerns
- Ensure all required components are addressed
- Reduce blending of analysis, explanation, and conclusions

## Mechanism
The prompt explicitly specifies:
- the required sections or parts
- section titles and ordering
- expectations for content type per section
- prohibitions against content appearing outside sections

This shifts the model from continuous prose into **segmented delivery**, where each section is completed independently.

## When to Use
- Responses that must include multiple distinct components
- Analyses that separate reasoning from conclusions
- Reports, reviews, or assessments with defined parts
- Situations where clarity depends on functional separation

## When Not to Use
- Simple or single-focus answers
- Tasks where content flows naturally as a narrative
- Exploratory brainstorming without predefined structure
- Creative writing where segmentation breaks coherence

## Prompt Skeleton
```text
Respond using the following sections, in order.

Section 1: <title>
- <instructions>

Section 2: <title>
- <instructions>

Section 3: <title>
- <instructions>

Rules:
- Use all sections exactly as titled.
- Do not merge or reorder sections.
- Do not include content outside the sections.
```
### Example Prompt
```
Respond using the following sections, in order.

Context:
- Briefly describe the background.

Analysis:
- Identify key factors and constraints.

Recommendation:
- Provide a clear proposed action.

Rules:
- Use all sections exactly as titled.
- Do not merge or reorder sections.
- Do not include content outside the sections.
```

### Example Output (Excerpt)
```
Context:
- The team is standardising prompt patterns across multiple projects.

Analysis:
- Inconsistent structure leads to uneven outputs and maintenance overhead.

Recommendation:
- Adopt a fixed sectioned format for all recurring prompt tasks.
```

## Failure Modes
* **Section omission:** one or more required parts are missing
* **Content bleed:** material intended for one section appears in another
* **Order drift:** sections are reordered or merged
* **Uneven depth:** some sections are overdeveloped while others are shallow

## Evaluation Checklist
* [ ] All specified sections are present
* [ ] Section titles match the prompt exactly
* [ ] Content aligns with the purpose of each section
* [ ] No content appears outside defined sections
* [ ] Ordering is preserved

## Variants
* **Fixed sections:** all sections mandatory and stable
* **Analytic split:** separate analysis, synthesis, and recommendation
* **Multi-response:** same sections repeated across multiple inputs
* **Two-pass:** fill sections first, refine content later

## Notes
This pattern is often combined with **Templates & Skeleton Formats** when the same multi-part structure is reused across tasks. If hierarchical planning is required first, apply **Outline & Hierarchy Structures** before sectioning.

## Tags
structure, sections, multi-part, segmentation, format-control
