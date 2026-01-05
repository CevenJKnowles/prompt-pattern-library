# Prompt Pattern YAML Schema & Policy (v1.0)

This document defines the **canonical YAML schema** for all prompt pattern files in the Prompt Pattern Library.

It serves as the **single source of truth** for:
- required and optional metadata fields
- field meanings and constraints
- authoring policy and consistency rules

All pattern files **must conform** to this schema.

---

## 1. Design Principles

The schema follows a **Hybrid Model (70% systems rigor / 30% pedagogy)**:

- YAML is **machine-readable, stable, and automation-ready**
- Markdown body is **human-readable and instructional**
- YAML must never become prose-heavy
- Pedagogical depth belongs in the Markdown body, not metadata

---

## 2. Required YAML Fields (Mandatory)

Every pattern file **must include all required fields**.

```yaml
id: "DXX-CXX-PXX"
slug: "kebab-case-identifier"
title: "Human-readable Pattern Title"

domain:
  id: "domain-xx"
  name: "Domain Name"

category:
  id: "category-xx"
  name: "Category Name"

pattern:
  id: "pxx"
  name: "Pattern Name"

status: "draft | stable | deprecated"
maturity: "alpha | beta | stable"

tags:
  - "controlled"
  - "keywords"

created: "YYYY-MM-DD"
updated: "YYYY-MM-DD"
version: "X.Y.Z"
```

### Required Field Rules
- `id` must be globally unique
- `slug` must be filesystem-safe (lowercase, hyphenated)
- `domain`, `category`, and `pattern` must match the taxonomy
- `status` reflects lifecycle
- `maturity` reflects confidence
- `version` follows semantic versioning

---

## 3. Optional YAML Fields

Optional fields **may be used when meaningful**.

They are divided into **baseline optionals** and **extended optionals**.

---

## 4. Baseline Optional Fields (Strongly Recommended)

These fields should be included for **most patterns** unless there is a clear reason not to.

```yaml
summary: "One-sentence description of the pattern’s intent."

audience:
  - "beginner"
  - "intermediate"
  - "expert"

risk:
  - "low | medium | high"

constraints:
  - "Any explicit limitation or condition."

relationships:
  related:
    - "DXX-CXX-PYY"

notes:
  - "Short author note or usage warning."
```

### Baseline Policy
- These fields improve searchability, navigation, and comprehension
- Authors are encouraged to include them by default
- Do **not** force content—clarity over completeness

---

## 5. Extended Optional Fields (Use Selectively)

These fields are **advanced** and should only be added when they provide real value.

```yaml
aliases:
  - "Alternative name"

inputs:
  - "Expected input type or structure"

outputs:
  - "Expected output type or structure"

relationships:
  parents:
    - "DXX-CYY-PZZ"
  contrasts:
    - "DXX-CYY-PZZ"

sources:
  - "Paper, documentation, dataset, or observation reference"
```

### Extended Policy
- Do not add fields speculatively
- Prefer consistency across related patterns
- Avoid partial population across a category unless intentional

---

## 6. Explicit Non-Goals (What YAML Must NOT Contain)

YAML must **not** include:
- long explanations
- prompt examples
- step-by-step instructions
- evaluation rubrics
- narrative teaching content

These belong in the **Markdown body**.

---

## 7. Markdown Body Expectations (Non-YAML)

Every pattern file should include, at minimum:

```md
## Definition
## When to Use
## When Not to Use
## Prompt Template
## Example
## Failure Modes
## Evaluation Checklist
```

(Exact section titles may evolve, but intent must remain.)

---

## 8. Extension & Change Policy

- New YAML fields require a **schema version bump**
- Schema changes must be documented in this file
- Ad-hoc metadata additions are not permitted
- If a need emerges repeatedly, propose a schema extension

---

## 9. Canonical Status

This document is:
- **Authoritative**
- **Versioned**
- **Binding for all contributors**

All pattern files in `docs/patterns/` are expected to comply.

---

**Schema Version:** 1.0  
**Status:** Locked  
**Effective:** Immediately
