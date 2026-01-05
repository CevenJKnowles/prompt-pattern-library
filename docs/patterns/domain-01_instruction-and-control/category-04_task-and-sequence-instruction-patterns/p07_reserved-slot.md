---
id: ppl-d01-c04-p07
title: Reserved (slot)
type: pattern
status: reserved
version: 0.1.0
domain: Instruction & Control
category: Task & Sequence Instruction Patterns
subcategory: Reserved (slot)
tags: []
created: 2026-01-05
updated: '2026-01-05'
---

# Reserved (slot)

## Definition
This slot is reserved for a future pattern in this category. No content has been assigned yet.

## Intent
- Preserve numbering for future expansion
- Avoid renaming downstream references
- Keep category capacity open

## Mechanism
A reserved entry is maintained as a placeholder file with a stable ID and filename.

When activated, the placeholder is replaced with a fully specified pattern while preserving the ID.

## When to Use
- You expect the category to grow but want stable numbering
- You want to avoid breaking links during early design
- You need to hold space for a known upcoming concept

## When Not to Use
- The library is already stable and numbering will not change
- You do not intend to fill the slot
- You need a complete set for a public release without placeholders

## Prompt Skeleton
```text
(Reserved)

No prompt skeleton is defined until this slot is assigned a pattern.

```
### Example Prompt

```
(Reserved)

No example prompt is defined until this slot is assigned a pattern.
```

### Example Output (Excerpt)

```
(Reserved)

No example output is defined until this slot is assigned a pattern.
```

## Failure Modes
* **Forgotten placeholder:** the slot remains reserved indefinitely
* **Silent drift:** slot is repurposed without documenting the change
* **Broken expectations:** users assume completeness where a placeholder exists

## Evaluation Checklist
* [ ] Placeholder status is clearly marked as reserved
* [ ] ID and filename remain stable
* [ ] The slot is documented in the category index
* [ ] Activation plan exists (or is explicitly deferred)

## Variants
* **Reserved with note:** include a brief description of the intended future pattern
* **Reserved with criteria:** specify what would justify activating the slot
* **Reserved with links:** point to related patterns that cover similar ground

## Notes
Reserved slots should be rare. If multiple reserved slots exist, consider revising the taxonomy to reflect actual inventory.

## Tags
reserved, placeholder, governance
