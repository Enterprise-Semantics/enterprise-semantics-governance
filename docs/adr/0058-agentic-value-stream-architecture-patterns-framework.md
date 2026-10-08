# ADR-ES-058 ; Agentic Value Stream Architecture Patterns & Reference Architectures Framework

Status: Accepted
Date: 2026-10-08
Deciders: eaojnr
Decision Type: Semantic baseline extension (architecture patterns + reference architectures layer for Agentic Value Stream)
Scope: Enterprise-Semantics/agentic-value-stream (single concept baseline; architecture model reusable for future AVS extensions)
Implements: CR-VAS-008
Amends: ES-ADR-005 + ES-ADR-052 + ES-ADR-053 + ES-ADR-054 + ES-ADR-055 + ES-ADR-056 + ES-ADR-057 (extends AVS semantic baseline with formal architecture patterns and reference architectures model)
Supersedes: None
Depends: ES-ADR-005, ES-ADR-031, ES-ADR-049, ES-ADR-051, ES-ADR-052, ES-ADR-053, ES-ADR-054, ES-ADR-055, ES-ADR-056, ES-ADR-057

## 1. Context

ES-ADR-052 + CR-VAS-002 through ES-ADR-057 + CR-VAS-007 (2026-10-07/2026-10-08) established the qualification, participation, conformance, measurement, maturity, and governance layers for AVS. The 6-layer semantic-to-operational chain is complete, with governance sitting across the lifecycle.

A semantic definition, participation structure, evidence + conformance layer, measurement layer, maturity framework, and governance control plane together answer six questions:

1. Is this an AVS? (CR-VAS-002)
2. How is agentic participation realized? (CR-VAS-003)
3. Can we prove it? (CR-VAS-004)
4. How well does it perform? (CR-VAS-005)
5. How capable are we? (CR-VAS-006)
6. How is it controlled? (CR-VAS-007)
7. **How is it architected?** (CR-VAS-008)

CR-VAS-008 (2026-10-08) was authored by eaojnr as the design response. It establishes the architecture patterns and reference architectures layer that translates the established semantic model into architecture without introducing implementation-specific concepts into the AVS ontology.

The single most important design decision in CR-VAS-008 is: architecture realizes AVS semantics; it does NOT define them. Technology MUST NOT define AVS qualification. The implementation layer may change without necessarily changing AVS semantics.

This ADR accepts CR-VAS-008 as the formal Architecture Patterns & Reference Architectures Framework for Agentic Value Stream.

## 2. Decision

### 2.1 Normative Principle

The repository SHALL establish an architecture patterns model that translates AVS semantics into architecture. The dependency is one-directional:

```
AVS Semantics
   -> Participation Model
     -> Governance & Authority
       -> Architecture Pattern
         -> Technology Realization
```

NOT:

```
Technology Platform
   -> Agent Architecture
     -> "Agentic Value Stream"
```

### 2.2 Six Architectural Planes

The canonical AVS reference architecture uses six architectural planes:

| ID | Plane | Purpose |
|---|---|---|
| P1 | Value & Outcome Plane | Business anchor. Stakeholder, outcome, value, Value Stream, value realization, outcome measures. |
| P2 | Value Stream Realization Plane | Value Stages, progression, decisions, actions, handoffs, dependencies, realization boundaries. |
| P3 | Agentic Participation Plane | Actor, entrusted intent, contextual interpretation, action selection, progression, coordination, intervention. Implements CR-VAS-003. |
| P4 | Control & Governance Plane | Authority, policy, constraints, risk, approval, escalation, intervention, revocation, audit, governance. |
| P5 | Knowledge & Context Plane | Enterprise data, knowledge, business state, customer context, external signals, policies, historical information. |
| P6 | Technology & Integration Plane | Applications, APIs, services, agent runtimes, models, workflow systems, automation, event infrastructure, data platforms. Technology is realization infrastructure, not AVS semantics. |

### 2.3 Twelve Reusable Architecture Patterns (AP-01..AP-12)

| Pattern | Summary |
|---|---|
| AP-01 | Agentic Stage Participation ; localized agentic realization in one stage. |
| AP-02 | Agentic Decision ; concentrated around a consequential decision. |
| AP-03 | Agentic Execution ; selects among permissible execution alternatives. |
| AP-04 | Human-Agent Hybrid ; explicit human interaction. |
| AP-05 | Agent-to-Human Escalation ; boundary-condition escalation with explicit threshold. |
| AP-06 | Human-to-Agent Delegation ; entrusted intent + bounded authority. |
| AP-07 | Distributed Agentic Participation ; multiple agents across the Value Stream. |
| AP-08 | Coordinated Multi-Agent Realization ; optional multi-agent architecture. |
| AP-09 | Agentic Orchestration ; orchestrator is not automatically agentic. |
| AP-10 | Agentic Exception Resolution ; agenticity for material exceptions only. |
| AP-11 | Agentic Coordination Overlay ; overlay, NOT a new semantic entity like "Agentic Workflow." |
| AP-12 | Progressive Delegation ; governed progression, NOT maturity progression. |

### 2.4 Four Architectural Boundaries

Every AVS architecture SHALL identify four boundaries:

- Value Boundary (where realization begins/ends)
- Agentic Boundary (where agentic participation occurs)
- Authority Boundary (what may/may not decide or execute)
- Technology Boundary (which systems implement realization)

### 2.5 Architecture Anti-Patterns (rejected)

Per CR-VAS-008 §22:

- AP-A01: Agent-Centric Architecture
- AP-A02: Agentic Workflow Ontology
- AP-A03: Full-Agentification Assumption
- AP-A04: Autonomy Maximization
- AP-A05: Technology-Led Semantics
- AP-A06: Orchestration Equals Agenticity

### 2.6 Architecture Quality Attributes

AVS architectures are evaluated against 12 quality attributes: value effectiveness; semantic integrity; authority integrity; safety; explainability; observability; resilience; reversibility; intervention; scalability; interoperability; maintainability; auditability.

### 2.7 Architecture Selection Criteria

Selection criteria: Value Stream structure; decision materiality; authority; risk; contextual complexity; intervention requirements; reversibility; outcome criticality; integration complexity.

NOT selected according to: novelty; agent count; model size; autonomy preference.

### 2.8 Architecture Invariants

CR-VAS-008 introduces 6 normative invariants (AVS-ARCH-INV-001..006). The most foundational:

- AVS-ARCH-INV-001: architecture realizes AVS semantics; it does NOT define them.
- AVS-ARCH-INV-002: technology MUST NOT define AVS qualification.
- AVS-ARCH-INV-003: agent framework choice MUST NOT define agenticity.
- AVS-ARCH-INV-004: orchestrator presence MUST NOT establish agentic qualification.
- AVS-ARCH-INV-005: multi-agent architecture is OPTIONAL, not a semantic requirement.
- AVS-ARCH-INV-006: heterogeneous Value Streams (human + automation + agent) are a first-class AVS architecture pattern.

### 2.9 Technology Substitution Principle

If two implementations preserve intent, authority, context, selection, action, outcome, and governance, then platform substitution SHALL NOT inherently change AVS identity.

## 3. Implementation

### 3.1 Concept Record (concept.yaml)

A new top-level `architecture:` block is added to `Enterprise-Semantics/agentic-value-stream/concept.yaml`. The block has 16 sub-keys formalizing principle, normative question, scope, primary object, six architectural planes, canonical pattern, twelve patterns, boundary model, decision record, quality attributes, selection, six anti-patterns, technology neutrality, six invariants, and boundary assertions.

Version bumped 1.5.0 -> 1.6.0. Promotion history extended.

### 3.2 Conformance Kit

`kit/kit.yaml` is updated to coverage 169 (was 151). New `ap_positive`, `ap_negative`, `ap_boundary` blocks added at top level. Provenance and boundary assertions extended.

### 3.3 Tests

18 new architecture tests:

- 6 positive (VAS-AP-P01..P06): six architectural planes, twelve architecture patterns, four architecture boundaries, architecture decision record template, architecture quality attributes, heterogeneous Value Streams.
- 6 negative (VAS-AP-N01..N06): the six anti-patterns.
- 6 boundary (VAS-AP-BT-01..BT-06): architecture vs semantic qualification, multi-agent vs agentic, orchestrator vs agentic participant, technology substitution vs AVS identity, context access vs context interpretation, progressive delegation vs maturity progression.

### 3.4 Documentation

Six new docs:

- `architecture.md`: purpose, core principle, normative question, scope.
- `reference-architecture.md`: six architectural planes with detailed scope; canonical architecture pattern.
- `architecture-patterns.md`: twelve reusable patterns AP-01..AP-12.
- `architecture-boundaries.md`: four architectural boundaries.
- `architecture-decisions.md`: architecture decision record template, quality attributes, selection criteria.
- `architecture-anti-patterns.md`: six anti-patterns with rejection rationale.

### 3.5 Visuals

Three new PUML diagrams:

- `avs-reference-architecture.puml`: six architectural planes (P1..P6) layered diagram.
- `avs-architecture-patterns.puml`: twelve reusable patterns AP-01..AP-12 with notes on optionality (AP-08), orchestrator non-qualification (AP-09), overlay-not-entity (AP-11), and delegation-vs-maturity (AP-12).
- `avs-architecture-boundaries.puml`: four architectural boundaries.

### 3.6 Mappings

The repository's `mappings/wsf.yaml` and `mappings/opendea.yaml` receive new `architecture_alignment` blocks, treating architecture as a repository-specific translation layer over WSF and OpenDEA without modifying either metamodel.

## 4. Consequences

### 4.1 Positive

- The repository now answers the seventh question: how is the AVS architected?
- Architecture is explicitly separated from semantics. A clean seven-question architecture is established.
- Six architectural planes provide a stable reference architecture.
- Twelve reusable architecture patterns cover the common realization shapes.
- Four architectural boundaries make the semantic-to-implementation layering explicit.
- The six anti-patterns prevent the repository from becoming a vendor or platform catalogue.
- The 6 invariants bind architecture decisions and pattern selection.
- Technology substitution is supported as long as intent, authority, context, selection, action, outcome, and governance are preserved.

### 4.2 Negative

- The conformance kit now carries 169 tests (vs 151 Wave 5). CI regeneration must handle the expanded inventory.
- Validators must distinguish architecture from semantic qualification.
- Implementers may resist the "architecture realizes semantics" principle (which prevents agent-platform-led design).

### 4.3 Architectural alignment

This ADR extends the 6-part semantic-to-operational chain with the architecture translation layer:

- CR-VAS-002 = SEMANTIC QUALIFICATION.
- CR-VAS-003 = PARTICIPATION & REALIZATION.
- CR-VAS-004 = EVIDENCE & CONFORMANCE.
- CR-VAS-005 = MEASUREMENT & OPERATIONAL VALUE.
- CR-VAS-006 = MATURITY & CAPABILITY.
- CR-VAS-007 = GOVERNANCE, LIFECYCLE & PORTFOLIO.
- **CR-VAS-008 = ARCHITECTURE PATTERNS & REFERENCE ARCHITECTURES** (Wave 6).

The semantic-to-implementation chain is:

```
                   AGENTIC VALUE STREAM
                            |
                     SEMANTICS
                            |
                       QUALIFICATION
                            |
                      PARTICIPATION
                            |
                         EVIDENCE
                            |
                       CONFORMANCE
                            |
                        MEASUREMENT
                            |
                         MATURITY
                            |
                       GOVERNANCE
                            |
                       ARCHITECTURE
                            |
                    INTEROPERABILITY  <- CR-VAS-009 (next)
                            |
                       TECHNOLOGY
```

## 5. Promotion Metadata

- Status: Accepted (semantic baseline extension, 2026-10-08).
- Cardinal author rule: Emmanuel A. Otchere (cardinal author rule, 2026-09-23).
- Vendor-specific material from embargoed sources: 0 references.
- D-004 dash rule: 0 en-dash (U+2013), 0 em-dash (U+2014), 0 triple-em-dash (U+2E3B).
- WSF metamodel not modified.
- OpenDEA metamodel not modified.

## 6. Related Artefacts

- CR-VAS-008 (Architecture Patterns & Reference Architectures Model).
- ES-ADR-057 (Governance, Lifecycle & Portfolio Framework).
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
- CR-VAS-002 through CR-VAS-007 (the prior 6 CRs in the chain).

<!-- Authored by: Emmanuel A. Otchere (cardinal author rule, 2026-10-08) -->
