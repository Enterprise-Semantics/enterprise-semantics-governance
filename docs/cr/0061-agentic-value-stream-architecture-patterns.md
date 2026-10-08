# CR-VAS-008 ; Agentic Value Stream Architecture Patterns & Reference Architectures Model

Status: Accepted
Date: 2026-10-08
Author: Emmanuel A. Otchere
Implements: ES-ADR-058
Amends: ES-ADR-005 + ES-ADR-052 + ES-ADR-053 + ES-ADR-054 + ES-ADR-055 + ES-ADR-056 + ES-ADR-057 (extends AVS semantic baseline with architecture patterns and reference architectures model)
Supersedes: None
Depends: ES-ADR-005, ES-ADR-031, ES-ADR-049, ES-ADR-051, ES-ADR-052, ES-ADR-053, ES-ADR-054, ES-ADR-055, ES-ADR-056, ES-ADR-057

Target release: Enterprise-Semantics/agentic-value-stream v1.6.0
Scope restrictions: additive only ;;; no amendment to CR-VAS-002..007 acceptance boundaries
Implementation: ES-ADR-058 (this CR is the implementation record)

## 1. Purpose

This Change Request establishes the formal Architecture Patterns and Reference Architectures model for Agentic Value Streams. It translates the semantic qualification (CR-VAS-002), participation structure (CR-VAS-003), conformance validation (CR-VAS-004), measurement model (CR-VAS-005), maturity framework (CR-VAS-006), and governance model (CR-VAS-007) into a reusable architecture pattern language and reference architecture model without introducing implementation-specific concepts into the AVS ontology.

## 2. Problem Statement

The repository has established semantic qualification, participation, evidence, conformance, measurement, maturity, and governance layers, but cannot yet answer:

> How can Agentic Value Streams be architected in different realization patterns while preserving the same underlying semantics?

CR-VAS-008 establishes the architecture translation layer. The design intent is: architecture realizes AVS semantics; it does NOT define them. The implementation layer may change without necessarily changing AVS semantics.

## 3. Normative Architecture Principle

The primary architectural object remains the **Value Stream realization**. Agentic components are positioned according to where delegated decision/action capability is required.

The dependency is intentionally one-directional:

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

The latter reverses the semantic dependency.

## 4. Architecture Scope

CR-VAS-008 covers: reference architectures; realization patterns; agent placement; human-agent interaction; decision placement; orchestration; knowledge/context access; policy enforcement; authority enforcement; observability; measurement; fallback; multi-agent coordination; integration boundaries.

It does NOT prescribe: a particular AI model; agent framework; cloud provider; orchestration platform; programming language; workflow product; model architecture; vendor.

## 5. Six Architectural Planes

The canonical AVS reference architecture uses six architectural planes. This layering deliberately keeps technology at the bottom of the semantic dependency chain.

### P1 ; Value & Outcome Plane

Represents: stakeholder; outcome; value; Value Stream; value realization; outcome measures. This is the business anchor.

### P2 ; Value Stream Realization Plane

Represents: Value Stages; progression; decisions; actions; handoffs; dependencies; realization boundaries. Agentic participation is positioned here rather than creating a parallel "agentic process."

### P3 ; Agentic Participation Plane

Represents: actor; entrusted intent; contextual interpretation; action selection; progression; coordination; intervention. This plane implements the semantics established in CR-VAS-003.

### P4 ; Control & Governance Plane

Represents: authority; policy; constraints; risk; approval; escalation; intervention; revocation; audit; governance.

### P5 ; Knowledge & Context Plane

Represents the information required for contextual interpretation: enterprise data; knowledge; business state; customer context; external signals; policies; historical information. The architecture MUST distinguish access to context from interpretation of context.

### P6 ; Technology & Integration Plane

Represents implementation mechanisms: applications; APIs; services; agent runtimes; models; workflow systems; automation; event infrastructure; data platforms. Technology is realization infrastructure, not AVS semantics.

## 6. Canonical Architecture Pattern

The default pattern is:

```
Value Stream
   |
   v
Agentic Participation
   |
+---+----+
v   v    v
Intent Context Authority
   |
   v
Decision / Selection
   |
   v
Action
   |
   v
Value Outcome
```

Governance surrounds the entire realization.

## 7. Twelve Architecture Patterns (AP-01..AP-12)

### AP-01 ; Agentic Stage Participation

An Agentic Value Stream contains a localized agentic realization within one Value Stage. Use when: only one stage requires contextual decisions; other stages remain human or automated; localized delegation is preferable. This is NOT an "Agentic Value Stage" semantic type.

### AP-02 ; Agentic Decision

Agentic participation is concentrated around a consequential decision. Examples: case routing; eligibility determination; treatment of an exception; prioritization; resource allocation. The architecture must demonstrate that the decision affects Value Stream progression.

### AP-03 ; Agentic Execution

The agent determines or selects how an intended action is executed within bounded authority.

### AP-04 ; Human-Agent Hybrid

Agentic participation operates with explicit human interaction. First-class AVS architecture pattern.

### AP-05 ; Agent-to-Human Escalation

The agent operates within delegated authority until a boundary condition is encountered. The escalation threshold must be explicit.

### AP-06 ; Human-to-Agent Delegation

A human or organizational role delegates a defined outcome or decision scope to an agent. Delegation is not equivalent to issuing a task instruction.

### AP-07 ; Distributed Agentic Participation

Multiple agents participate in different portions of the Value Stream. Each participation point must retain: intent; authority; context; action selection; outcome contribution.

### AP-08 ; Coordinated Multi-Agent Realization

Multiple agents jointly contribute to a Value Stream outcome. Multi-agent architecture is optional; it is not a semantic requirement for AVS.

### AP-09 ; Agentic Orchestration

An orchestrating actor coordinates multiple realizations. The orchestrator itself does NOT automatically qualify as Agentic. Its participation must satisfy the AVS qualification rules.

### AP-10 ; Agentic Exception Resolution

The normal Value Stream is largely deterministic, but material exceptions require agentic interpretation and selection. Agenticity need not dominate the entire Value Stream.

### AP-11 ; Agentic Coordination Overlay

Agentic coordination may operate across multiple Value Stages without creating a new Value Stream hierarchy. The overlay is an architectural realization pattern; it is NOT a new semantic entity such as "Agentic Workflow."

### AP-12 ; Progressive Delegation

Delegated authority can increase or decrease according to defined governance criteria. Progression must be governed by evidence and authority policy. It must NOT be interpreted as mandatory maturity progression.

## 8. Architecture Boundary Model

Every AVS architecture SHOULD identify four boundaries: Value Boundary; Agentic Boundary; Authority Boundary; Technology Boundary.

```
+-----------------------------------+
|        VALUE BOUNDARY             |
|                                   |
|  +-----------------------------+  |
|  |     AGENTIC BOUNDARY        |  |
|  |                             |  |
|  |  Intent -> Context -> Sel.  |  |
|  |           v                 |  |
|  |   AUTHORITY BOUNDARY         |  |
|  |           v                 |  |
|  |         Action              |  |
|  +-----------------------------+  |
|                                   |
|     TECHNOLOGY BOUNDARY           |
+-----------------------------------+
```

## 9. Architecture Decision Model

```yaml
architecture_decision:
  id:
  value_stream:
  agentic_participation:
  pattern:
  rationale:
  authority:
  context:
  action_space:
  human_interaction:
  fallback:
  risks:
  measures:
  governance:
```

## 10. Architecture Quality Attributes

AVS architectures evaluated against: value effectiveness; semantic integrity; authority integrity; safety; explainability; observability; resilience; reversibility; intervention; scalability; interoperability; maintainability; auditability.

## 11. Reference Architecture Selection

Select according to: Value Stream structure; decision materiality; authority; risk; contextual complexity; intervention requirements; reversibility; outcome criticality; integration complexity.

NOT according to: novelty; agent count; model size; autonomy preference.

## 12. Architecture Anti-Patterns

### AP-A01 ; Agent-Centric Architecture

Starting with agents and attempting to discover the Value Stream afterward. Rejected.

### AP-A02 ; Agentic Workflow Ontology

Creating a parallel workflow hierarchy merely because agents participate. Rejected.

### AP-A03 ; Full-Agentification Assumption

Assuming every Value Stage must become agentic. Rejected.

### AP-A04 ; Autonomy Maximization

Treating maximum autonomy as the target architecture. Rejected.

### AP-A05 ; Technology-Led Semantics

Defining AVS based on the architecture of a particular agent platform. Rejected.

### AP-A06 ; Orchestration Equals Agenticity

Assuming an orchestrator is automatically an agentic participant. Rejected.

## 13. Invariants

CR-VAS-008 establishes 6 invariants:

- AVS-ARCH-INV-001: architecture realizes AVS semantics; it does NOT define them.
- AVS-ARCH-INV-002: technology MUST NOT define AVS qualification.
- AVS-ARCH-INV-003: agent framework choice MUST NOT define agenticity.
- AVS-ARCH-INV-004: orchestrator presence MUST NOT establish agentic qualification.
- AVS-ARCH-INV-005: multi-agent architecture is OPTIONAL, not a semantic requirement.
- AVS-ARCH-INV-006: heterogeneous Value Streams (human + automation + agent) are a first-class AVS architecture pattern.

## 14. Technology Substitution Principle

If two implementations preserve intent, authority, context, selection, action, outcome, and governance, then platform substitution SHALL NOT inherently change AVS identity.

## 15. Conformance Tests

### Positive (6 tests)

- VAS-AP-P01: Six Architectural Planes
- VAS-AP-P02: Twelve Architecture Patterns
- VAS-AP-P03: Four Architecture Boundaries
- VAS-AP-P04: Architecture Decision Record Template
- VAS-AP-P05: Architecture Quality Attributes
- VAS-AP-P06: Heterogeneous Value Streams

### Negative (6 tests)

- VAS-AP-N01: Agent-Centric Architecture
- VAS-AP-N02: Agentic Workflow Ontology
- VAS-AP-N03: Full-Agentification Assumption
- VAS-AP-N04: Autonomy Maximization
- VAS-AP-N05: Technology-Led Semantics
- VAS-AP-N06: Orchestration Equals Agenticity

### Boundary (6 tests)

- VAS-AP-BT-01: Architecture vs Semantic Qualification
- VAS-AP-BT-02: Multi-Agent vs Agentic
- VAS-AP-BT-03: Orchestrator vs Agentic Participant
- VAS-AP-BT-04: Technology Substitution vs AVS Identity
- VAS-AP-BT-05: Context Access vs Context Interpretation
- VAS-AP-BT-06: Progressive Delegation vs Maturity Progression

## 16. Acceptance Criteria

CR-VAS-008 is complete when:

- Canonical AVS reference architecture defined.
- Six architectural planes defined.
- Agentic participation remains subordinate to Value Stream realization.
- At least ten reusable architecture patterns defined.
- Human-agent patterns explicitly represented.
- Multi-agent realization represented as optional.
- Authority boundary represented.
- Value boundary represented.
- Technology boundary represented.
- Fallback represented.
- Architecture decision model defined.
- Architecture anti-patterns documented.
- Technology-neutral reference architecture established.
- Machine-readable architecture patterns created.
- PlantUML/reference visualizations aligned.
- CI validates architecture-pattern structure.

## 17. Definition of Done

CR-VAS-008 is complete when a practitioner can take a conformant AVS and answer: "What architectural pattern realizes its agentic participation, where does that participation occur, what authority does it have, how does it interact with humans and systems, and what happens when it cannot safely proceed?" without introducing new semantic types into the AVS ontology.

## 18. Architectural Position

CR-VAS-008 establishes the bridge:

```
SEMANTICS
   -> ARCHITECTURE
     -> IMPLEMENTATION
```

It prevents the repository from becoming either: (a) a purely conceptual ontology with no implementation guidance, or (b) a technology architecture whose implementation choices redefine the concept.

The next CR (CR-VAS-009) needs to establish the interoperability contract between these architecture patterns and actual technology implementations.

## 19. CR Sequence After CR-VAS-008

| CR | Layer | Question |
|---|---|---|
| VAS-002 | Semantic Qualification | What makes an AVS an AVS? |
| VAS-003 | Participation & Realization | How is agentic participation realized? |
| VAS-004 | Evidence & Conformance | How do we prove it? |
| VAS-005 | Measurement & Value | How well does it work? |
| VAS-006 | Maturity & Capability | How capable are we? |
| VAS-007 | Governance & Lifecycle | How is it controlled? |
| **VAS-008** | **Architecture Patterns** | **How is it architected?** |
| **VAS-009** | **Interoperability & Technology Boundaries** | **How is it implemented without corrupting the semantics?** |

<!-- Authored by: Emmanuel A. Otchere (cardinal author rule, 2026-10-08) -->
