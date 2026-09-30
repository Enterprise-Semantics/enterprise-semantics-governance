# CR-ES-032-PRD ; WSF Product Dependency Integration Implementation

Status: Accepted
Date: 2026-09-26
Implements: ES-ADR-032-PRD
Scope: Enterprise-Semantics

## 1. Intent

Implement ES-ADR-032-PRD: adopt wsf:Product (per ADR-WSF-36 + CR-WSF-36, Baseline) as the authoritative Product foundation.

## 2. Implementation Chain

1. ES-side base Product concept record as WSF reference (concepts/product.concept.yaml in enterprise-semantics + concept repo product updated)
2. WSF mapping (enterprise-semantics-mappings/mappings/wsf/product.yaml, release_target: v1.6.0)
3. Specialization concept YAMLs updated to base_concept: WSF:PRODUCT with authority: WSF
4. Kit manifests + conformance regeneration

## 3. Acceptance Criteria

1. ES base Product concept record exists with authority: WSF and source_decision: ADR-WSF-36
2. Validator: NO_DRIFT
3. Mapping filed with release_target: v1.6.0
4. D-004 clean ; cardinal author stamp

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
