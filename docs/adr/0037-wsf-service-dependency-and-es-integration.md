# ADR-ES-031-SVC ; WSF Service Dependency and Enterprise-Semantics Integration

Status: Accepted
Date: 2026-09-26
Deciders: eaojnr
Decision Type: Dependency integration (NOT foundational definition)
Scope: Enterprise-Semantics
Implements: ES-CR-031-SVC

## 1. Context

Enterprise-Semantics governs Service specializations (Agentic Service and Autonomous Service) but never established a local base Service concept record. Recon-ES-006 (2026-09-26) confirmed via exhaustive audit that the asserted parent existed nowhere ; ES or WSF. ADR-WSF-35 has now grounded WSF Service as the authoritative foundation at Baseline.

This ADR formalizes the integration: Enterprise-Semantics adopts WSF Service as the authoritative base concept and does NOT redefine the foundation locally. Per the Culture (ES-ADR-026) / System (ES-ADR-027) integration pattern.

## 2. Decision

1. Enterprise-Semantics adopts wsf:Service (per ADR-WSF-35, Baseline) as the authoritative foundation for Service
2. The ES-side base Service concept record is recorded as a WSF reference (authority: WSF ; source_decision: ADR-WSF-35), per the culture/system demotion pattern
3. ES specializations (ES-014 + ES-015) reference WSF:SERVICE as base_concept with authority: WSF
4. Semantic Version target: v1.3.0/v1.4.0

## 3. Dependency Gate

Satisfied at filing: wsf:Service = Baseline per ADR-WSF-35 (promoted 2026-09-26, WSF PR #16).

## 4. Consequences

- The Recon-ES-006 Service gap is closed end-to-end (WSF foundation -> ES integration -> specialization dependency gates)
- ES-014 + ES-015 dependency gates are retroactively satisfied

## Promotion Metadata

- promotion_date: 2026-09-26
- promotion_trigger: implementation chain complete (base concept records validator NO_DRIFT 25 ; mappings filed ; kits + conformance landed) ; WSF dependencies at Baseline (PR #16)
- prior_status: Proposed
- promotion_authority: Emmanuel A. Otchere (cardinal author rule, 2026-09-24)

## Compound ID Note (2026-09-28)

- Logical ID was ES-031 (Service integration). Per the user-authoritative model, ES-031 is reassigned to Agentic Network (slot 0040). This Service integration tranche is renamed ES-031-SVC (compound ID convention) to preserve history + signal that logical ES-031 now belongs to a different concept.
- Same convention applies to ES-032-PRD (Product integration ; was ES-032).

## Author

Emmanuel A. Otchere (cardinal author rule, 2026-09-24)
