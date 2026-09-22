<!--
Authored by: Emmanuel A. Otchere (cardinal author rule, 2026-09-22)
Filing: CR-ES-001 §10 + §11-§13 (governance scaffolding ;;; no destructive replaces)
-->

# Governance Lifecycle

This document describes the operational lifecycle for governance artefacts in the Enterprise-Semantics program. It supplements ADR-ES-001 §9 with practical guidance.

## Lifecycle phases

### Finding

A Finding captures an investigation or candidate hypothesis. Findings:

- Live at `docs/finding/`.
- Author by `Emmanuel A. Otchere` (cardinal rule).
- Carry `Status: Proposed Finding` (or `Established`, `Deprecated`).
- Cite provenance explicitly.
- Do NOT establish normative semantic authority.

### ADR

An ADR establishes a governed architectural decision. ADRs:

- Live at `docs/adr/`.
- Author by `Emmanuel A. Otchere`.
- Carry `Status: Proposed` (or `Accepted`, `Superseded`, `Deprecated`).
- Are immutable once Accepted.
- Are superseded by a new ADR, not rewritten.

### CR

A CR implements an ADR or an independent scope change. CRs:

- Live at `docs/cr/`.
- Author by `Emmanuel A. Otchere`.
- Carry `Status: Proposed` (or `Accepted`, `Implemented`, `Rejected`).
- Reference their governing ADR.
- Specify out-of-scope items explicitly to prevent scope creep.

### Recon

A Recon reconciles current state and identifies next actions. Recon:

- Live at `docs/recon/`.
- Author by `Emmanuel A. Otchere`.
- Carry `Status: Proposed`.
- Do NOT promote concepts or modify semantic authority.
- Are filed before substantive governance change.

### Decision

A Decision captures a non-ADR governance decision. Decisions:

- Live at `decisions/`.
- Used for conventions, cardinal rules, operational rules.
- Author by `Emmanuel A. Otchere`.

## Promotion chain

Recon ;;; Finding ;;; ADR ;;; CR ;;; Implementation ;;; CI ;;; Release

Each phase is governed by the preceding phase's artefact. A CR cannot be filed before its ADR is Accepted. A CR cannot merge before CI passes. A Release cannot ship before CI has run.

## Out of scope

This document does not cover:

- Specific ADR content (each ADR is self-describing).
- Specific CR content (each CR is self-describing).
- Specific Finding content (each Finding is self-describing).

## Cardinal rules

- Author: Emmanuel A. Otchere (all governance artefacts).
- D-004 dash rule (colons + semicolons only in committed artefacts).
- Vendor-specific embargo (no material from embargoed sources in any artefact).
- SDO-neutral sourcing (ISO/IEC, ITU-T, ETSI, NIST).
