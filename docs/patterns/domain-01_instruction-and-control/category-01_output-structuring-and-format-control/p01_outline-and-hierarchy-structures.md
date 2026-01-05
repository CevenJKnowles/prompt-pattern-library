---
id: "D01-C01-P01"
slug: "outline-and-hierarchy-structures"
title: "Outline & Hierarchy Structures"

domain:
  id: "domain-01"
  name: "Instruction & Control"

category:
  id: "category-01"
  name: "Output Structuring & Format Control"

pattern:
  id: "p01"
  name: "Outline & Hierarchy Structures"

status: "active"
maturity: "beta"

tags:
  - "structure"
  - "formatting"
  - "hierarchy"
  - "outline-control"

summary: "Forces the model to produce a clearly structured, hierarchical outline with explicit levels and ordering."

audience:
  - "beginner"
  - "intermediate"

risk:
  - "low"

constraints:
  - "Preserve hierarchy depth"
  - "Do not merge structural levels"
  - "No explanatory prose outside the outline"

relationships:
  related:
    - "D01-C01-P07"
  contrasts:
    - "D09-C01-P01"

notes:
  - "This pattern is structural, not semantic."
  - "Apply before drafting long-form content to reduce drift."

created: "2026-01-05"
updated: "2026-01-05"
version: "1.0.0"
---

# Outline & Hierarchy Structures

## Definition
A prompt pattern that constrains the model’s output into a **hierarchical outline**, using explicit levels (numbering, nesting, or headings) to enforce clarity, order, and navigability.

## Intent
- Impose structural clarity
- Prevent free-form or narrative drift
- Improve scanability and downstream reuse

## Mechanism
The prompt explicitly specifies:
- required hierarchy depth
- ordering rules
- permitted structural markers (numbers, bullets, headings)
- prohibitions against prose outside structural nodes

This shifts the model from generative narration into **layout-first planning**.

## When to Use
- Planning documents or reports
- Documentation, curricula, or specifications
- Any task requiring ordered structure before prose

## When Not to Use
- Free-form creative writing
- Exploratory brainstorming
- Conversational ideation or dialogue

## Prompt Template
```text
Create a structured outline for the topic below.

Rules:
- Use numbered headings and nested subpoints.
- Maximum depth: {max_depth}.
- Do not include explanatory prose outside outline items.

Topic: {topic}
```

### Example Prompt
```
Create a structured outline for the topic below.

Rules:
- Use numbered headings and nested subpoints.
- Maximum depth: 3.
- Do not include explanatory prose outside outline items.

Topic: A GitHub-ready documentation workflow for a prompt pattern library
```
### Example Output (Excerpt)
```
1. Overview
   1.1 Purpose
   1.2 Scope
2. Core Concepts
   2.1 Taxonomy as source of truth
   2.2 YAML vs Markdown separation
```
## Failure Modes

* **Over-decomposition:** too many levels reduce usability
* **Fake structure:** headings exist but content is incoherent
* **Hierarchy drift:** inconsistent numbering or nesting rules

## Evaluation Checklist

* [ ] Hierarchy depth matches constraints
* [ ] Structural markers are consistent
* [ ] No prose appears outside outline nodes
* [ ] Each node is semantically coherent

## Variants

* **Strict skeleton:** fixed headings and fixed number of nodes
* **Adaptive skeleton:** fixed headings, variable subpoints
* **Two-pass:** outline first, expand sections sequentially

## Notes
Combine with **Length & Granularity Control** only *after* the outline is generated.

---