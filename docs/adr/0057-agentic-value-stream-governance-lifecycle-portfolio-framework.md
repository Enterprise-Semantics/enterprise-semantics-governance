# ADR-ES-057 ; Agentic Value Stream Governance, Lifecycle & Portfolio Framework

Status: Accepted
Date: 2026-10-08
Deciders: eaojnr
Decision Type: Semantic baseline extension (governance, lifecycle, and portfolio management layer for Agentic Value Stream)
Scope: Enterprise-Semantics/agentic-value-stream (single concept baseline; governance model reusable for future AVS extensions)
Implements: CR-VAS-007
Amends: ES-ADR-005 + ES-ADR-052 + ES-ADR-053 + ES-ADR-054 + ES-ADR-055 + ES-ADR-056 (extends AVS semantic baseline with formal governance, lifecycle, and portfolio management model)
Supersedes: None
Depends: ES-ADR-005, ES-ADR-031, ES-ADR-049, ES-ADR-051, ES-ADR-052, ES-ADR-053, ES-ADR-054, ES-ADR-055, ES-ADR-056

## 1. Context

ES-ADR-052 + CR-VAS-002 (2026-10-07) introduced the formal qualification test for AVS. ES-ADR-053 + CR-VAS-003 (2026-10-08) introduced Agentic Participation & Value Stream Realization. ES-ADR-054 + CR-VAS-004 (2026-10-08) introduced evidence and conformance validation. ES-ADR-055 + CR-VAS-005 (2026-10-08) introduced measurement and operational value. ES-ADR-056 + CR-VAS-006 (2026-10-08) introduced organizational maturity and capability progression.

A semantic definition, participation structure, evidence + conformance layer, measurement layer, and maturity framework together answer five questions:

1. Is this an AVS? (CR-VAS-002 qualification)
2. How is agentic participation realized? (CR-VAS-003 participation)
3. Can we prove conformance? (CR-VAS-004 evidence)
4. How well does it perform and create value? (CR-VAS-005 measurement)
5. How capable are we at systematically operating it? (CR-VAS-006 maturity)
6. How do we control it throughout its life? (CR-VAS-007 governance)

CR-VAS-007 (2026-10-08) was authored by eaojnr as the design response. It establishes the management control plane around the already-defined semantic object. Governance does NOT redefine AVS semantics; it governs how conformant AVS are created, changed, monitored, suspended, retired, and managed across an enterprise portfolio.

The single most important design decision in CR-VAS-007 is: governance sits across the lifecycle rather than above the ontology. It controls qualification, authority, operation, change, and retirement without becoming another semantic layer.

This ADR accepts CR-VAS-007 as the formal Governance, Lifecycle & Portfolio Framework for Agentic Value Stream.

## 2. Decision

### 2.1 Normative Principle

The repository SHALL establish a governance and lifecycle model that operates as a **management control plane** around an already-defined AVS semantic object. Governance begins with:

```
Value Stream -> Agentic Participation -> Authority -> Risk ->
   Outcome -> Governance
```

rather than:

```
AI Model -> Agent -> Agentic System -> Governance
```

The latter incorrectly makes technology the primary governance object.

### 2.2 Ten Lifecycle States

An AVS SHALL have an explicit lifecycle:

| State | Meaning |
|---|---|
| Proposed | Candidate identified for agentic realization. |
| Assessed | Initial evaluation covering relevance, authority, risk, materiality. |
| Designed | Formal design (scope, intent, authority, action space). |
| Qualified | Semantic qualification + evidence satisfied. |
| Approved | Governance authority authorizes implementation or operation. |
| Implemented | Realization exists technically/operationally. |
| Operational | Actively realizing value. Required controls active. |
| Managed | Systematic measurement, monitoring, risk, value, conformance, improvement. |
| Suspended | Temporary cessation of agentic realization. |
| Retired | No longer authorized for operational use. |

The lifecycle is NOT necessarily linear. An AVS may move backwards (Operational -> Suspended -> Revalidated -> Operational, or Operational -> Material Change -> Reassessment -> Non-Conformant -> Remediation).

### 2.3 Seven Governance Domains

Governance covers seven domains:

| ID | Domain |
|---|---|
| G1 | Semantic Governance |
| G2 | Authority Governance |
| G3 | Operational Governance |
| G4 | Risk & Policy Governance |
| G5 | Value Governance |
| G6 | Change Governance |
| G7 | Portfolio Governance |

### 2.4 Material Change + Change Classification

A change is material when it could alter semantic qualification, authority, action space, risk exposure, stakeholder outcome, Value Stream progression, intervention requirements, regulatory obligations, or operational boundary.

Changes are classified as Class A (Non-Material), Class B (Controlled), Class C (Material; requires formal revalidation), or Class D (Critical; requires governance approval before implementation).

### 2.5 Authority Governance

Authority is governed throughout the lifecycle as a governed enterprise resource. Authority records include scope, permissions, constraints, policies, thresholds, escalation conditions, revocation conditions, and effective dates. Authority escalation is explicit and observable. Authority revocation SHALL be supported. Revocation MUST NOT require semantic deletion of the AVS.

### 2.6 Fallback Governance

Every production AVS SHOULD define an appropriate fallback strategy. Patterns include: Agentic -> Human; Agentic -> Deterministic Automation; Agentic -> Manual Process; Agentic -> Safe Stop.

### 2.7 Intervention Governance

Human intervention SHALL be governed as an explicit control mechanism. Intervention types include approval, validation, exception handling, correction, escalation, override, investigation, and recovery. Intervention SHALL NOT automatically be classified as failure.

### 2.8 Portfolio Governance

Portfolio governance identifies AVS inventory, business domains, authority concentration, criticality, risk, value, maturity, technology dependencies, shared capabilities, duplication, and lifecycle state. Prioritization considers expected value, strategic alignment, feasibility, risk, capability readiness, reuse potential, and operational criticality.

The repository identifies reusable capabilities (identity, authorization, policy enforcement, knowledge retrieval, decision services, monitoring, evaluation, intervention, audit, measurement, orchestration). Portfolio governance explicitly monitors for agent sprawl and concentration risk.

### 2.9 Runtime vs Governance Policy Distinction

The following distinction is mandatory: Instruction != Policy != Authority != Governance Decision. An agent instruction cannot legitimately override a higher-order authority constraint.

The policy hierarchy is Enterprise -> Domain -> Value Stream -> AVS -> Authority Boundary -> Runtime Enforcement.

### 2.10 Governance Invariants

CR-VAS-007 introduces 15 normative invariants (AVS-GOV-INV-001..015). The most foundational:

- AVS-GOV-INV-001: governance does not redefine AVS semantics.
- AVS-GOV-INV-002: semantic qualification and governance approval are distinct decisions.
- AVS-GOV-INV-003: operational status does not imply continuing conformance.
- AVS-GOV-INV-004: material changes require appropriate revalidation.
- AVS-GOV-INV-006: authority must be revocable.
- AVS-GOV-INV-009: lifecycle states must support suspension and resumption.
- AVS-GOV-INV-010: lifecycle states must support retirement.
- AVS-GOV-INV-013: runtime instructions cannot supersede governing authority or policy.
- AVS-GOV-INV-014: conformance is subject to lifecycle revalidation.
- AVS-GOV-INV-015: governance responsibilities are organizational assignments, not ontology requirements.

### 2.11 Governance Maturity vs AVS Maturity

CR-VAS-006 measures organizational capability (maturity to govern). CR-VAS-007 governs the actual lifecycle (actual exercise of governance). These are distinct: a highly mature organization can still make a poor governance decision; a smaller organization may operate a very disciplined governance process for a critical AVS.

## 3. Implementation

### 3.1 Concept Record (concept.yaml)

A new top-level `governance:` block is added to `Enterprise-Semantics/agentic-value-stream/concept.yaml`. The block has 32 sub-keys formalizing principle, governance objective, six dimensions, governance object model, lifecycle with 10 states, state separation, seven governance domains, material change + change classification, change decision model, authority governance (record schema, escalation, revocation), fallback governance, intervention governance, conformance drift, governance triggers, governance evidence, governance decision types, portfolio governance (inventory, prioritization, capability reuse, agent sprawl, concentration risk), lifecycle ownership, RACI principle, policy hierarchy, runtime vs governance policy distinction, emergency controls, governance dashboard, governance metrics, governance vs AVS maturity distinction, machine-readable lifecycle schema, change record schema, portfolio record schema, 15 invariants, and boundary assertions.

Version bumped 1.4.0 -> 1.5.0. Promotion history extended.

### 3.2 Conformance Kit

`kit/kit.yaml` is updated to coverage 151 (was 121). New `gv_positive`, `gv_negative`, `gv_boundary` blocks added at top level. Provenance and boundary assertions extended.

### 3.3 Tests

30 new governance tests:

- 10 positive (VAS-GV-P01..P10): lifecycle management, seven governance domains, material change revalidation, authority revocation, safe suspension and fallback, portfolio governance, capability reuse and avoidance of agent sprawl, governance evidence and decision types, runtime instruction shall not override authority, governance metrics and dashboard.
- 10 negative (VAS-GV-N01..N10): the six anti-patterns and four additional negative tests (governance redefines semantics, operational status implies continuing conformance, lifecycle without retirement support, governance decisions without evidence).
- 10 boundary (VAS-GV-BT-01..10): governance vs semantic qualification, qualification vs approval, lifecycle state vs governance status, material vs non-material change, authority escalation vs normal authority use, conformance drift vs version change, governance maturity vs AVS maturity, governance metrics vs measurement metrics, intervention as control vs intervention as failure, governance RACI vs ontology responsibility.

### 3.4 Documentation

Eight new docs:

- `governance.md`: purpose, core principle, governance objective, dimensions, scope.
- `lifecycle.md`: 10-state lifecycle, non-linearity, state separation.
- `change-management.md`: material change concept, change classification (4 classes), change decision model.
- `authority-governance.md`: authority record schema, escalation, revocation, governance evidence.
- `suspension-and-recovery.md`: suspension triggers, fallback patterns, emergency controls, recovery.
- `portfolio-governance.md`: portfolio inventory, prioritization, capability reuse, agent sprawl avoidance, concentration risk.
- `governance-metrics.md`: six governance metrics, dashboard views.
- `governance-anti-patterns.md`: six anti-patterns with rejection rationale.

### 3.5 Visuals

Three new PUML diagrams:

- `avs-lifecycle.puml`: 10-state lifecycle state diagram with regression arrows.
- `governance-domains.puml`: seven governance domains + governance container.
- `governance-policy-hierarchy.puml`: Enterprise -> Domain -> Value Stream -> AVS -> Authority Boundary -> Runtime Enforcement.

### 3.6 Mappings

The repository's `mappings/wsf.yaml` and `mappings/opendea.yaml` receive new `governance_alignment` blocks, treating governance as a repository-specific framework overlay over WSF and OpenDEA without modifying either metamodel.

## 4. Consequences

### 4.1 Positive

- The repository now answers the sixth question: how is the AVS controlled throughout its life?
- Governance is explicitly separated from semantic qualification, conformance, measurement, and maturity. A clean six-question architecture is established.
- The 10-state lifecycle is semantically anchored.
- The seven governance domains cover semantic, authority, operational, risk/policy, value, change, and portfolio views.
- Material change classification prevents ungoverned evolution.
- Authority revocation is supported. Runtime instructions cannot supersede governing policy.
- Portfolio governance addresses agent sprawl and concentration risk.
- The 15 invariants bind governance decisions, dashboards, and reporting.

### 4.2 Negative

- The conformance kit now carries 151 tests (vs 121 Wave 4). CI regeneration must handle the expanded inventory.
- Validators must distinguish lifecycle state from governance status.
- Organizations may resist the policy hierarchy (which prevents runtime instructions from becoming the highest authority).

### 4.3 Architectural alignment

This ADR closes the 5-part semantic-to-operational chain AND extends it with the governance control plane:

- CR-VAS-002 = SEMANTIC QUALIFICATION.
- CR-VAS-003 = PARTICIPATION & REALIZATION.
- CR-VAS-004 = EVIDENCE & CONFORMANCE.
- CR-VAS-005 = MEASUREMENT & OPERATIONAL VALUE.
- CR-VAS-006 = MATURITY & CAPABILITY.
- CR-VAS-007 = GOVERNANCE, LIFECYCLE & PORTFOLIO.

The conceptual stack:

```
                    VALUE STREAM
                         |
              AGENTIC PARTICIPATION
                         |
          +--------------+--------------+
          |              |              |
        Intent        Authority       Context
          |              |              |
          +--------------+--------------+
                         |
                  Action / Outcome
                         |
                 ---------------
                         |
                    CONFORMANCE
                         |
                    MEASUREMENT
                         |
                     MATURITY
                         |
                    GOVERNANCE
                         |
              +-----------+-----------+
              |                       |
          Lifecycle              Portfolio
```

The critical insight is that governance sits across the lifecycle rather than above the ontology. It controls qualification, authority, operation, change, and retirement without becoming another semantic layer.

## 5. Promotion Metadata

- Status: Accepted (semantic baseline extension, 2026-10-08).
- Cardinal author rule: Emmanuel A. Otchere (cardinal author rule, 2026-09-23).
- Vendor-specific material from embargoed sources: 0 references.
- D-004 dash rule: 0 en-dash (U+2013), 0 em-dash (U+2014), 0 triple-em-dash (U+2E3B).
- WSF metamodel not modified.
- OpenDEA metamodel not modified.

## 6. Related Artefacts

- CR-VAS-007 (Governance, Lifecycle & Portfolio Management Model).
- ES-ADR-056 (Maturity & Capability Framework).
- ES-ADR-055 (Measurement & Operational Value Framework).
- ES-ADR-054 (Evidence, Conformance & Qualification Validation Framework).
- ES-ADR-053 (Agentic Value Stream Participation & Realization Framework).
- ES-ADR-052 (Agentic Value Stream Semantic Qualification Framework).
- ES-ADR-005 (Agentic Value Stream decision).
- ES-ADR-031 (5-category boundary taxonomy).
- ES-ADR-049 (Per-Concept Repo Self-Containment).
- ES-ADR-051 (Editorial Restructure).
- CR-AVS-001 (Repository Conformance Reconciliation).
- CR-VAS-002 (Formal Semantic Qualification).
- CR-VAS-003 (Participation & Realization Model).
- CR-VAS-004 (Evidence, Conformance & Qualification Validation).
- CR-VAS-005 (Measurement & Operational Value Model).
- CR-VAS-006 (Maturity & Capability Model).

<!-- Authored by: Emmanuel A. Otchere (cardinal author rule, 2026-10-08) -->
