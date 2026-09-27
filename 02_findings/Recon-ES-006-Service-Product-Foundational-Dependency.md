# Recon-ES-006 ; Service + Product Foundational Dependency Gap

Date: 2026-09-26
Author: Emmanuel A. Otchere (cardinal author rule, 2026-09-24)
Status: Filed

## Finding

During ES-030 backfill wave 5, an exhaustive branch audit (all vs-a branches + main) confirmed that no standalone base-concept YAML exists for:

- Service (agentic-service ES-014 + autonomous-service ES-015 both specialize a "parent Service concept" that has no ES record)
- Product (agentic-product ES-016 + autonomous-product ES-017 same pattern)

The specialization YAMLs state "Inherits WSF Service grounding via the parent Service concept" ; "Inherits WSF Product grounding via parent Product concept" ; but no WSF ADR for Service or Product has been filed on World-Semantic-Foundation/wsf-governance either (ADR register runs ADR-WSF-001 to ADR-WSF-34 ; none cover Service or Product).

## Pattern

This is the same foundational-dependency pattern as Culture/System (Recon-ES-003/004) and Ecosystem (Recon-ES-005). The established resolution path:

1. WSF-side foundation ADR (Service, Product) at subject-namespace or sequential IDs
2. WSF promotion to Baseline
3. ES-side integration ADR/CR pair adopting the WSF foundation
4. Specialization dependency gates then validate

## Current State

- The 4 specializations (agentic/autonomous service, agentic/autonomous product) are filed + implemented + Accepted, with dependency on a parent that exists only by assertion
- This predates the dependency-gate discipline (those tranches shipped before ES-022 Semantic Integrity made the gate explicit)
- No immediate breakage: the specializations are self-contained ; but the foundation-first rule is technically violated retroactively

## Resolution Options

- Option A: File WSF-ADR-SERVICE-001 + WSF-ADR-PRODUCT-001 (subject-namespace) ; promote to Baseline ; then ES integration ADRs
- Option B: File sequential ADR-WSF-35 (Service) + ADR-WSF-36 (Product) per the current github.com convention
- Option C: ES-local foundation (rejected by precedent ; WSF owns foundational meaning)

## Recommendation

Option B (sequential, matching the pattern established by ADR-WSF-33/34 filings), with subject-namespace aliases noted per LOCKED-PICKS convention.

## Author

Emmanuel A. Otchere (cardinal author rule, 2026-09-24)
