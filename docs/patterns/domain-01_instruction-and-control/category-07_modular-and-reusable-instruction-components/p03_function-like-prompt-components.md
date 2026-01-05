---
id: "ppl-d01-c07-p03"
title: "Function-Like Prompt Components"
type: pattern
status: active
version: 1.0.0
domain: "Instruction & Control"
category: "Modular & Reusable Instruction Components"
subcategory: "Function-Like Prompt Components"
tags:
  - "modularity"
  - "reuse"
  - "instruction-design"
  - "functions"
  - "inputs-outputs"
  - "interfaces"
  - "composition"
created: 2026-01-05
updated: 2026-01-05
---

# Function-Like Prompt Components

## Definition
Function-like prompt components define a clear interface (inputs → outputs) and behavior contract, enabling prompts that behave like callable functions.

## Intent
Improve reliability by turning fuzzy instructions into interface-driven components with explicit inputs, outputs, and constraints.

## Mechanism
Specify inputs, validation rules, transformation logic, and expected output schema. Invoke with bound parameters and require deterministic formatting.

## When to Use
* You need consistent transformations (e.g., extract, normalize, classify)
* You want prompts to be composable in pipelines
* You need predictable outputs for downstream tooling

## When Not to Use
* The task is creative/ambiguous and resists strict I/O contracts
* You cannot constrain the model output format reliably
* You don’t control the calling context

## Prompt Skeleton
```text
FUNCTION: <NAME>
INPUTS:
- <name>: <type> (constraints)
PROCESS:
- <step_1>
- <step_2>
OUTPUT:
- <schema/format>
ERRORS:
- If <condition>, return <error format>
END FUNCTION

CALL:
<NAME>({<name>=...})

RETURN ONLY OUTPUT.
```

### Example Prompt
```text
FUNCTION: NORMALIZE_TAGS
INPUTS:
- tags: list[string] (kebab-case)
PROCESS:
- Lowercase
- Replace spaces with '-'
- Deduplicate
OUTPUT:
- list[string]
ERRORS:
- If any item is empty, return ERROR:EMPTY_TAG
END FUNCTION

CALL:
NORMALIZE_TAGS({tags=["UI Design", "ui-design", " "]})

RETURN ONLY OUTPUT.
```

### Example Output (Excerpt)
```text
ERROR:EMPTY_TAG
```

## Failure Modes
* Interface is underspecified (types/constraints missing)
* Return format leaks extra commentary
* Error handling not defined, causing silent failure

## Evaluation Checklist
* [ ] Inputs include constraints
* [ ] Output schema is explicit
* [ ] Error path is defined
* [ ] Call syntax binds parameters clearly
* [ ] Instruction includes ‘return only output’

## Variants
* Add ‘unit tests’ inside the prompt
* Add a strict JSON output schema
* Provide a fallback ‘best-effort’ error mode

## Notes
* Treat this as a contract: don’t change outputs casually
* Keep function components small and single-purpose
* Use consistent error formats across functions

## Tags
* `modularity`
* `reuse`
* `instruction-design`
* `functions`
* `inputs-outputs`
* `interfaces`
* `composition`
