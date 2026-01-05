# Gold‑Standard Prompt Pattern — Example (v1.0)

This file demonstrates a **fully populated, canonical prompt pattern** using the locked YAML schema.
Use this as the reference implementation for Phase 2 authoring.

---

```yaml
id: PPL-D01-C01-S01
slug: outline-and-hierarchy-structures
domain: Domain 01 — Instruction & Control
category: Category 01 — Output Structuring & Format Control
subcategory: Outline & Hierarchy Structures
version: 1.0
status: canonical
phase: phase-2
author: Ceven J. Knowles
created: 2026-01-05
updated: 2026-01-05

summary: >
  Forces the model to produce a clearly structured, hierarchical outline
  with explicit levels, ordering, and section boundaries.

intent:
  - Impose structural clarity
  - Prevent free‑form or narrative drift
  - Improve scanability and downstream reuse

use_when:
  - Planning documents
  - Reports, guides, or curricula
  - Any task requiring ordered structure

avoid_when:
  - Free‑form creative writing
  - Exploratory brainstorming
  - Conversational ideation

inputs:
  - topic
  - optional scope constraints
  - optional depth or length limits

outputs:
  - ordered outline
  - numbered or nested hierarchy

constraints:
  - Preserve hierarchy depth
  - Do not merge levels
  - No explanatory prose outside the outline

compatibility:
  works_well_with:
    - Step‑by‑Step Reasoning
    - Persona Assignment
    - Length Constraints
  conflicts_with:
    - Open‑Ended Creative Generation
    - Stream‑of‑Consciousness Output

anti_patterns:
  - Vague task framing
  - Mixed structural metaphors
  - Narrative explanations embedded in outline

examples:
  canonical_prompt: |
    Create a structured outline for the topic below.
    Use numbered headings and nested subpoints.
    Do not include prose explanations.

    Topic: {{topic}}

  expected_output_excerpt: |
    1. Introduction
       1.1 Purpose
       1.2 Scope
    2. Core Concepts
       2.1 Definition
       2.2 Key Components

notes:
  - This pattern is structural, not semantic
  - Combine with reasoning patterns only if explicitly required

governance:
  drift_risk: low
  review_cycle: stable
```

---

## Explanation

This pattern demonstrates:
- Full YAML compliance
- Clear intent separation
- Explicit compatibility rules
- Anti‑pattern documentation
- Minimal but sufficient examples

Use this file as:
- a **template reference**
- a **review benchmark**
- a **lint target** for future automation
