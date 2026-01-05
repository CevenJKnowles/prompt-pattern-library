# Prompt Pattern Library

Canonical prompt-pattern taxonomy and atomic pattern library.

---

## What this repository is

- **Taxonomy v1.0 (locked)**  
  A stable, canonical classification of prompt patterns structured as:  
  **Domains → Categories → Subcategories**

  > **Structural note:**  
  > The Prompt Pattern Library defines **18 primary domains**.  
  > **Domain 19 — Meta-Prompting, Logic & System Control** is included as a
  > *structural and system-level domain* to materialize the meta-layer required
  > for documentation, navigation, orchestration, and tooling.  
  > It does not alter the conceptual 18-domain model.

- **Phase 2 — Atomic Pattern Library**  
  One Markdown file per pattern (subcategory), each using a consistent
  **YAML + Markdown schema**, designed for:
  - clear documentation
  - cross-referencing
  - long-term versioning
  - static publishing

---

## Canonical source of truth

- **Taxonomy reference:**  
  `docs/governance/taxonomy-v1.0.md`

This file is the authoritative definition of the taxonomy.
Folder structure and navigation files mirror it, but do not supersede it.

---

## Authoring workflow

- Open `docs/` as a **Zettlr project root**
- Each domain and category has an `_index.md`
- Each atomic pattern lives in its own Markdown file

This structure supports:
- focused authoring
- predictable navigation
- Git-based review
- MkDocs publishing

---

## Publishing (optional)

This repository includes `mkdocs.yml` for building a clean static wiki.
Publishing is optional and does not affect the authoring workflow.

---

## Start here

- `docs/index.md`
- `docs/patterns/_index.md`
- `docs/governance/taxonomy-v1.0.md`
