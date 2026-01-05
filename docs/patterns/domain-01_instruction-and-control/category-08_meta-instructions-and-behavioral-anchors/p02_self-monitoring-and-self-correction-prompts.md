---
id: "ppl-d01-c08-p02"
title: "Self-Monitoring & Self-Correction Prompts"
type: pattern
status: active
version: 1.0.0
domain: "Instruction & Control"
category: "Meta Instructions & Behavioral Anchors"
subcategory: "Self-Monitoring & Self-Correction"
tags:
  - "self-check"
  - "error-correction"
  - "quality-control"
  - "meta-instructions"
created: 2026-01-05
updated: 2026-01-05
---

## Definition

Adds an explicit self-review step to catch errors, omissions, or rule violations before finalizing output.

## Intent

Increase reliability by requiring the model to validate its own output against constraints and common failure modes.

## Mechanism

Inserts a check phase (e.g., verify facts, verify format, verify constraints) and then a correction phase if needed.

## When to Use

- When you need reliable, repeatable behavior control above task-level instructions.
- When prompts contain ambiguity, layered constraints, or multi-turn workflows.
- When you want consistent conflict-handling or self-regulation.

## When Not to Use

- When a one-off answer is sufficient and meta-control adds friction.
- When high flexibility is required and strict anchors could reduce usefulness.
- When the additional control layer is likely to confuse the user.

## Prompt Skeleton

```text
1) Draft the answer.
2) Run a self-check against the checklist:
   - constraints, format, completeness, obvious errors
3) If any check fails, revise and output only the corrected final answer.
```

### Example Prompt

```text
Task: Write a short troubleshooting guide for "Wi‑Fi connected but no internet".
Constraints:
- 6 steps max
- Each step starts with an imperative verb
- Avoid brand-specific advice

Process:
1) Draft.
2) Self-check for constraints and clarity.
3) Output only the corrected final guide.
```

### Example Output (Excerpt)

```text
1. Restart the router and modem to clear temporary network faults.
2. Reconnect to the Wi‑Fi network and confirm you are on the intended SSID.
3. Check another device to determine whether the issue is device-specific or network-wide.
4. Disable and re-enable the device’s network adapter to reset the connection stack.
5. Verify IP and DNS settings to ensure the device is receiving valid network configuration.
6. Test a different DNS server to rule out name-resolution problems.
```

## Failure Modes

- Self-check is requested but not enforced (model outputs the draft anyway).
- Checklist is incomplete, so failures still slip through.
- Self-check becomes verbose and replaces the answer.

## Evaluation Checklist

* [ ] Is the self-check step explicit and tied to the stated constraints?
* [ ] Does the final output comply with all constraints?
* [ ] Is the self-check lightweight (doesn't bloat the response)?
* [ ] Are corrections applied rather than merely noted?

## Variants

- Add a 'red flag' list (e.g., hallucination risk, missing citations) for high-stakes tasks.
- Use two-pass outputs: draft hidden, final shown (when allowed).

## Notes

Works best with short constraint lists and clear formatting rules. For long outputs, scope the self-check to critical requirements.

## Tags

- `self-check`
- `error-correction`
- `quality-control`
- `meta-instructions`
