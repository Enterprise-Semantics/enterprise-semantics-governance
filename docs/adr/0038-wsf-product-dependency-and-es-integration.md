# ADR-ES-032 ; WSF Product Dependency and Enterprise-Semantics Integration

Status: Accepted
Date: 2026-09-26
Deciders: eaojnr
Decision Type: Dependency integration (NOT foundational definition)
Scope: Enterprise-Semantics
Implements: ES-CR-032

## 1. Context

Enterprise-Semantics governs Product specializations (Agentic Product and Autonomous Product) but never established a local base Product concept record. Recon-ES-006 (2026-09-26) confirmed via exhaustive audit that the asserted parent existed nowhere ; ES or WSF. ADR-WSF-36 has now grounded WSF Product as the authoritative foundation at Baseline.

This ADR formalizes the integration: Enterprise-Semantics adopts WSF Product as the authoritative base concept and does NOT redefine the foundation locally. Per the Culture (ES-ADR-026) / System (ES-ADR-027) integration pattern.

## 2. Decision

1. Enterprise-Semantics adopts wsf:Product (per ADR-WSF-36, Baseline) as the authoritative foundation for Product
2. The ES-side base Product concept record is recorded as a WSF reference (authority: WSF ; source_decision: ADR-WSF-36), per the culture/system demotion pattern
3. ES specializations (ES-016 + ES-017) reference WSF:PRODUCT as base_concept with authority: WSF
4. Semantic Version target: v1.5.0/v1.6.0

## 3. Dependency Gate

Satisfied at filing: wsf:Product = Baseline per ADR-WSF-36 (promoted 2026-09-26, WSF PR #16).

## 4. Consequences

- The Recon-ES-006 Product gap is closed end-to-end (WSF foundation -> ES integration -> specialization dependency gates)
- ES-016 + ES-017 dependency gates are retroactively satisfied

## Promotion Metadata

- promotion_date: 2026-09-26
- promotion_trigger: implementation chain complete (base concept records validator NO_DRIFT 25 ; mappings filed ; kits + conformance landed) ; WSF dependencies at Baseline (PR #16)
- prior_status: Proposed
- promotion_authority: Emmanuel A. Otchere (cardinal author rule, 2026-09-24)

## Author

Emmanuel A. Otchere (cardinal author rule, 2026-09-24)
