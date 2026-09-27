# CR-ES-032 ; WSF Product Dependency Integration Implementation

Status: Proposed
Date: 2026-09-26
Implements: ES-ADR-032
Scope: Enterprise-Semantics

## 1. Intent

Implement ES-ADR-032: adopt wsf:Product (per ADR-WSF-36 + CR-WSF-36, Baseline) as the authoritative Product foundation.

## 2. Implementation Chain

1. ES-side base Product concept record as WSF reference (concepts/product.concept.yaml in enterprise-semantics + concept repo concept-product updated)
2. WSF mapping (enterprise-semantics-mappings/mappings/wsf/product.yaml, release_target: v1.6.0)
3. Specialization concept YAMLs updated to base_concept: WSF:PRODUCT with authority: WSF
4. Kit manifests + conformance regeneration

## 3. Acceptance Criteria

1. ES base Product concept record exists with authority: WSF and source_decision: ADR-WSF-36
2. Validator: NO_DRIFT
3. Mapping filed with release_target: v1.6.0
4. D-004 clean ; cardinal author stamp

## Author

Emmanuel A. Otchere (cardinal author rule, 2026-09-24)
