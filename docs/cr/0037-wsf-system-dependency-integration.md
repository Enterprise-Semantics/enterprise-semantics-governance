# ES-CR-027 ; WSF System Dependency Integration

Status: Proposed
Implements: ES-ADR-027
Depends On: WSF-ADR-ES-027
Related: ES-ADR-025, ES-FOUND-001
Target Semantic Version: 2.3.0
Authority: Enterprise-Semantics

## Cross-Program Traceability Note

This is the canonical Enterprise-Semantics integration CR for the WSF System foundation. It supersedes the prior short-cut ES-CR-027 at slot 0037. Per WSF-ES-ALIGN-01, the implementation SHALL NOT create a competing local foundational System concept.

## 13. Change Objective

Integrate the authoritative WSF System semantic into Enterprise-Semantics and update Agentic System to specialize WSF System.

No competing foundational System definition shall be introduced.

## 14. Registry

Add:

```yaml
- id: SYSTEM
  authority: WSF
  authority_status: canonical
  dependency_type: foundational
  source_decision: WSF-ADR-ES-027
```

The registry SHALL identify WSF as the semantic owner.

## 15. Agentic System Update

Update Agentic System:

```
source: AGENTIC_SYSTEM
relationship: specializes
target: WSF:SYSTEM
```

The Agentic System artifact SHALL not contain an alternative foundational definition of System.

## 16. Repository Changes

Implement:

- WSF System registry dependency
- Agentic System base-concept update (base_concept: WSF:SYSTEM)
- WSF System mapping at `enterprise-semantics-mappings/wsf/system.yaml`
- Agentic System mapping (already exists at `enterprise-semantics-mappings/wsf/agentic-system.yaml` + `opendea/agentic-system.yaml`)
- provenance
- documentation
- architecture diagrams
- conformance tests

Do not create `enterprise-semantics/concepts/system.yaml` as a competing foundational concept.

If a local reference artifact is technically required, it SHALL explicitly identify WSF as the semantic authority (status: Deprecated, foundation_authority: WSF, source_decision: WSF-ADR-ES-027).

## 17. Mapping

Create:

```
enterprise-semantics-mappings/
+- wsf/
   +- system.yaml
```

with the authoritative correspondence:

```yaml
source:
  authority: Enterprise-Semantics
  concept: SYSTEM
target:
  authority: WSF
  concept: SYSTEM
mapping_type: equivalent
```

The mapping represents semantic identity/reference, not ownership transfer.

## 18. Agentic System Mapping

Ensure the Enterprise-Semantics mapping expresses:

```
source: ES:AGENTIC_SYSTEM
relationship: specializes
target: WSF:SYSTEM
```

## 19. Provenance

Record:

```
provenance:
  source:
    - ES-FOUND-001
    - WSF-ADR-ES-027
  decision:
    - ES-ADR-027
  implementation:
    - ES-CR-027
```

## 20. Documentation

The architecture documentation SHALL show:

```
WSF
 |
 +- System
       |
       +- Agentic System
             |
             +- Enterprise-Semantics
```

The documentation SHALL state explicitly that System is WSF-owned.

## 21. Conformance Tests

Positive:

Validate that:

- WSF System is authoritative
- Agentic System specializes WSF System
- System remains technology-neutral
- Agentic System retains the Agentic semantic boundary
- Agentic System does not imply Autonomous System

Negative:

Validate that:

- Enterprise-Semantics cannot become owner of foundational System
- Agentic System cannot redefine System
- an Agent is not automatically a System
- an AI implementation is not automatically an Agentic System
- automation alone does not establish Agentic System
- Agentic Workflow is not equivalent to Agentic System
- Agentic Operations is not equivalent to Agentic System

## 22. Acceptance Criteria

- [ ] WSF System is registered as canonical external authority.
- [ ] No competing local foundational System exists.
- [ ] Agentic System references WSF:SYSTEM.
- [ ] WSF System mapping exists.
- [ ] Agentic System mapping exists.
- [ ] Provenance is complete.
- [ ] Documentation is updated.
- [ ] Architecture visuals are updated.
- [ ] Positive conformance tests pass.
- [ ] Negative conformance tests pass.
- [ ] CI validates the dependency gate.

## 23. Release Effect

Upon successful implementation:

Enterprise-Semantics v2.3.0

contains the WSF System dependency integration and the governed Agentic System specialization.

## Author

Emmanuel A. Otchere (cardinal author rule, 2026-09-24)
