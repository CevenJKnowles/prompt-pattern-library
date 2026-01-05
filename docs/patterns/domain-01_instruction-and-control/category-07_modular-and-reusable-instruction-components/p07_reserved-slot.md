---
id: "ppl-d01-c07-p07"
title: "Reserved (slot)"
type: pattern
status: active
version: 1.0.0
domain: "Instruction & Control"
category: "Modular & Reusable Instruction Components"
subcategory: "Reserved (slot)"
tags:
  - "modularity"
  - "reuse"
  - "instruction-design"
  - "slots"
  - "parameters"
  - "templates"
  - "fill-in"
created: 2026-01-05
updated: 2026-01-05
---

# Reserved Slot

## Definition
A reserved slot is an intentionally empty placeholder for future patterns or sub-patterns, kept to preserve numbering and planned taxonomy space.

## Intent
Maintain stable pattern IDs and avoid renumbering when future patterns are added.

## Mechanism
Mark the file as reserved, keep the baseline structure, and clearly indicate that content is TBD.

## When to Use
* You want stable IDs for links and references
* You plan to add a future pattern but aren’t ready
* You need to reserve taxonomy space

## When Not to Use
* You have no intent to fill it and it creates noise
* Users will mistake it for a usable pattern
* The reserved slot blocks better organization

## Prompt Skeleton
```text
RESERVED PATTERN SLOT
ID: <existing ID>
TITLE: Reserved
STATUS: Reserved
NOTES:
- This slot is intentionally empty to preserve numbering.
- Do not reference as an active pattern.

FUTURE INTENT:
<one sentence, optional>
```

### Example Prompt
```text
RESERVED PATTERN SLOT
ID: ppl-d01-c07-p07
TITLE: Reserved
STATUS: Reserved
NOTES:
- Placeholder to preserve pattern numbering.

FUTURE INTENT:
TBD.
```

### Example Output (Excerpt)
```text
No output. This file is a placeholder.
```

## Failure Modes
* Accidentally treated as an active pattern
* No clear marker that it’s reserved
* Future pattern added without updating links

## Evaluation Checklist
* [ ] Reserved status is explicit
* [ ] Not referenced as active elsewhere
* [ ] Placeholder text is unambiguous
* [ ] File retains baseline structure
* [ ] Updated date reflects last touch

## Variants
* Reserve with a short future intent note
* Add a ‘do-not-use’ warning banner
* Track reserved slots in an index table

## Notes
* Keep reserved slots rare
* Document the rationale in the category index
* Update immediately when the real pattern is added

## Tags
* `modularity`
* `reuse`
* `instruction-design`
* `reserved`
* `placeholder`
* `tbd`
* `planning`
