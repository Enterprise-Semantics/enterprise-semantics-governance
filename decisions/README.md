<!--
Authored by: Emmanuel A. Otchere (cardinal author rule, 2026-09-22)
Filing: CR-ES-001 §10 + §11-§13 (governance scaffolding ;;; no destructive replaces)
-->

# Decisions

This directory holds non-ADR governance decisions. Per CR-ES-001 §10 and ADR-ES-001 §11.

## When to use

Use this directory for governance decisions that:

- Do not establish new architectural direction (use ADR-ES-* for that).
- Do not implement a code or content change (use CR-ES-* for that).
- Do establish a policy, convention, or operational rule.

Examples (held for future CRs):

- Lifecycle state convention (Title-Case vs ALL-CAPS).
- Author field rule (Emmanuel A. Otchere cardinal rule).
- WSF↔ES boundary classification decision (per FND-ES-AG-008).
- Per-concept Established label re-evaluation (per user directive 2026-09-22).

## Naming convention

`NNNN-short-title.md` where NNNN is the next available slot.

## Out of scope

This directory does not hold:

- ADRs (use `../docs/adr/`).
- CRs (use `../docs/cr/`).
- Findings (use `../docs/finding/`).
- Reconnaissance (use `../docs/recon/`).
