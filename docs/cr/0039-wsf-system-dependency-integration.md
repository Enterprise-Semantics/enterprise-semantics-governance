# CR-ES-039 ; WSF System Dependency Integration

Status: Proposed
Target Release: v2.7.0
Implements: ADR-ES-029
Authority: Enterprise-Semantics
Dependency: WSF-ADR-ES-027 accepted and implemented

## 1. Objective

Integrate the WSF System foundation into Enterprise-Semantics and remove any possibility of competing local foundational System semantics.

## 2. Repository Changes

Do not maintain `enterprise-semantics/concepts/system.yaml` as a competing canonical concept.

If a reference artifact is required (per CR-ES-027 section 2 + WSF-ES-ALIGN-01 CR-ES-027 section 2), it must explicitly identify:

```yaml
id: ES:CONCEPT:system
canonical_name: System (WSF Reference)
authority: WSF
dependency_type: foundational
source_decision: WSF-ADR-ES-027
definition: |
  Reference record for the WSF System concept.
  Per WSF-ADR-ES-027 section 2, a System is an organized
  whole of interacting elements whose relationships and
  behavior enable one or more intended functions,
  purposes, or outcomes within a defined boundary
  and context.

  This record is a dependency reference, NOT an
  independent semantic definition. The semantic
  authority is WSF (WSF-ADR-ES-027).
```

The prior `concepts/system.concept.yaml` created in the ES-027 tranche (slot 0031) is demoted from foundational status per this CR. The historical file is preserved for reference but is no longer canonical.

## 3. Dependency Registry

Register per the existing Enterprise-Semantics canonical registry:

```yaml
- id: SYSTEM
  authority: WSF
  authority_status: canonical
  dependency_type: foundational
  source_decision: WSF-ADR-ES-027
```

## 4. Agentic System Dependency

Update AGENTIC_SYSTEM to identify base_concept: WSF:SYSTEM.

## 5. Mapping

Create or update:

- `enterprise-semantics-mappings/wsf/system.yaml` (System)
- `enterprise-semantics-mappings/wsf/agentic-system.yaml` (Agentic System grounded to WSF System)
- `enterprise-semantics-mappings/opendea/agentic-system.yaml` (Agentic System grounded to OpenDEA)

Mappings must clearly distinguish:

```
WSF System
      |
      v
Enterprise-Semantics Agentic System specialization
```

## 6. Validation

Implement dependency tests confirming:

- WSF System is canonical
- Local System is not independently defined
- Agentic System specializes WSF System
- Agentic System retains System semantics
- Agentic System requires material agentic behavior
- AI is not required
- Automation is not sufficient
- Agent presence alone is insufficient
- Agentic System does not imply Autonomous System

## 7. Provenance

```
provenance:
  source:
    - ES-FOUND-001
    - WSF-ADR-ES-027
  decision:
    - ES-ADR-029
  implementation:
    - ES-CR-039
```

## 8. Acceptance Criteria

Complete when:

- WSF System is validated
- WSF System remains the sole foundational authority
- Enterprise-Semantics contains no competing System definition
- ES-025 references WSF System
- Agentic System boundaries pass
- Mappings are complete
- Conformance tests pass
- CI passes

## 9. Release

The dependency integration becomes part of the next Enterprise-Semantics release (v2.7.0) following successful validation.



## Author

Emmanuel A. Otchere (cardinal author rule, 2026-09-24)

## Cross-Program Traceability Note

Per user directive message 1553249359905165444 + WSF-ES-ALIGN-01, the WSF-side filings are WSF-ADR-ES-026 + WSF-CR-ES-026 (Culture) and WSF-ADR-ES-027 + WSF-CR-ES-027 (System). The ES-side chain adopts ES-ADR-028 + ES-CR-038 (Culture alignment) and ES-ADR-029 + ES-CR-039 (System alignment) to avoid slot collision with the prior ES-026/ES-027 foundational concept filings, which are now superseded by this alignment chain per CR-ES-026-section-2 + CR-ES-027-section-2 corrective guidance.
