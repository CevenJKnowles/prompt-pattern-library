---
id: "ppl-d01-c06-p07"
title: "Reserved (slot)"
type: pattern
status: active
version: 1.0.0
domain: "Instruction & Control"
category: "Instruction Style & Tone Control"
subcategory: "Reserved (slot)"
tags:
  - "reserved"
  - "placeholder"
  - "indexing"
created: 2026-01-05
updated: 2026-01-05
---

# Reserved (slot)

## Definition
Reserved (slot) is a placeholder pattern file reserved for future expansion of the category without renumbering existing pattern IDs.

## Intent
- Preserve stable IDs for future additions
- Avoid reindexing or renaming patterns later
- Keep category structure extensible

## Mechanism
The file remains reserved, with minimal content to preserve schema and prevent broken navigation.

## When to Use
- You expect future patterns but want stable numbering now
- You need to keep parity with planned category size

## When Not to Use
- When the category is final and no expansion is planned
- When reserved slots create confusion for readers

## Prompt Skeleton
```text
Reserved Slot:
- This pattern ID is intentionally reserved.

Task:
{task}
```
### Example Prompt
```text
Reserved Slot:
- This pattern ID is intentionally reserved.

Task:
N/A
```

### Example Output (Excerpt)
```text
N/A
```

## Failure Modes
* Reader confusion: users expect a real pattern
* Accidental reuse: content is added without updating index/relationships

## Evaluation Checklist
* [ ] File clearly states it is reserved
* [ ] Navigation and index do not imply active usage
* [ ] Schema remains consistent with other patterns

## Variants
* Reserved + rationale: add a short note explaining planned scope

## Notes
If you decide to activate this slot, update the category index and ensure tags and examples are meaningful and accurate.

## Tags
reserved, placeholder, indexing
