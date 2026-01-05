---
id: ppl-d01-c01-p04
title: "JSON, XML & Code-Like Formats"
type: pattern
status: active
version: 1.0.0
domain: "Instruction & Control"
category: "Output Structuring & Format Control"
subcategory: "JSON, XML & Code-Like Formats"
tags:
  - "structure"
  - "json"
  - "xml"
  - "code-like"
  - "format-control"
created: 2026-01-05
updated: 2026-01-06
---

# JSON, XML & Code-Like Formats

## Definition
JSON, XML & Code-Like Formats is a prompt pattern that constrains the model’s output to a **formal, machine-readable structure**, such as JSON objects, XML trees, or code-like syntax with explicit keys, fields, and nesting rules.

The emphasis is on **syntactic correctness and structural determinism**, rather than natural language fluency.

## Intent
- Produce outputs suitable for parsing, validation, or programmatic reuse
- Eliminate ambiguity in field names, nesting, and data boundaries
- Enforce strict structural discipline over free-form explanation
- Integrate LLM output into software, pipelines, or automated workflows

## Mechanism
The prompt explicitly specifies:
- the required format (e.g. JSON, XML, YAML, pseudo-code)
- allowed keys, fields, or tags
- nesting rules and ordering constraints
- prohibitions against prose outside the structured output

This shifts the model from narrative generation into **syntax-bound completion**, where correctness is defined by adherence to the specified format.

## When to Use
- Generating configuration files, schemas, or structured data
- Producing outputs intended for automated ingestion or validation
- Interfacing LLMs with software systems or APIs
- Any task where structural precision outweighs readability

## When Not to Use
- Human-facing explanations or instructional prose
- Exploratory reasoning or ideation
- Situations where format requirements are unstable or unknown
- Tasks where minor syntax errors would invalidate the output

## Prompt Skeleton
```text
Return the output strictly in the following JSON format.

Rules:
- Use exactly the specified keys.
- Preserve nesting and data types.
- Do not include comments or explanatory text.
- Do not include content outside the JSON object.

{
  "field_a": "<value>",
  "field_b": {
    "subfield_1": "<value>",
    "subfield_2": "<value>"
  }
}
```

### Example Prompt
```
Return the output strictly in the following JSON format.

Rules:
- Use exactly the specified keys.
- Preserve nesting and data types.
- Do not include comments or explanatory text.
- Do not include content outside the JSON object.

{
  "pattern_name": "<string>",
  "primary_use": "<string>",
  "risk_level": "<low | medium | high>"
}
```

### Example Output (Excerpt)
```
{
  "pattern_name": "Tabular & Matrix Output",
  "primary_use": "Structured comparison across attributes",
  "risk_level": "low"
}
```

## Failure Modes
* **Syntax errors:** missing braces, invalid nesting, or malformed structure
* **Key drift:** additional, missing, or renamed fields
* **Prose leakage:** explanatory text outside the structured block
* **Format mixing:** combining multiple formats (e.g. JSON plus markdown)

## Evaluation Checklist
* [ ] Output conforms exactly to the specified format
* [ ] All required keys or fields are present
* [ ] No extra keys or attributes appear
* [ ] No prose exists outside the structured block
* [ ] Structure is parseable without post-processing

## Variants
* **Strict JSON:** machine-validated, no tolerance for deviation
* **XML tree:** tag-based hierarchical representation
* **Code stub:** language-like syntax with placeholders
* **Two-pass:** generate structured data first, explain separately if needed

## Notes
Use this pattern only when downstream systems depend on format correctness. If structure discovery is required first, apply **Outline & Hierarchy Structures** before locking into a code-like format.

## Tags
structure, json, xml, code-like, machine-readable, format-control
```