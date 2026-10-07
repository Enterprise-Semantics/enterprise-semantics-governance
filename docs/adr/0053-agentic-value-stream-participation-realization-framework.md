# ADR-ES-053 ; Agentic Value Stream Participation & Realization Framework

Status: Accepted
Date: 2026-10-08
Deciders: eaojnr
Decision Type: Semantic baseline (participation & realization model for Agentic Value Stream)
Scope: Enterprise-Semantics/agentic-value-stream (single concept baseline; participation model reusable for future AVS extensions)
Implements: CR-VAS-003
Amends: ES-ADR-005 + ES-ADR-052 (extends Agentic Value Stream semantic baseline with explicit participation & realization representation)
Supersedes: None
Depends: ES-ADR-005 (Agentic Value Stream decision), ES-ADR-031 (5-category boundary taxonomy), ES-ADR-049 (per-concept repo self-containment), ES-ADR-051 (editorial restructure), ES-ADR-052 (formal qualification framework)

## 1. Context

ES-ADR-005 established Agentic Value Stream as a specialisation of Value Stream. ES-ADR-052 + CR-VAS-002 (2026-10-07) introduced the formal qualification test that establishes the necessary and sufficient conditions under which a Value Stream qualifies as Agentic. The qualification test, however, remains abstract unless the repository can represent the entities, relationships, participation scopes, authority semantics, and realisation patterns of an actual Agentic Value Stream.

Without an explicit participation & realisation model, two implementations can both satisfy CR-VAS-002 while representing the resulting AVS in incompatible ways. The repository risks having a strong conceptual definition but weak instance semantics.

CR-VAS-003 (2026-10-08) was authored by eaojnr as the design response. It introduces the Agentic Participation relationship as the structural layer that bridges the Value Stream and the actor performing agentic realisation. This ADR accepts CR-VAS-003 as the formal participation & realisation framework for Agentic Value Stream.

## 2. Decision

### 2.1 Hierarchical subordination

Agentic Participation is SUBORDINATE to the Value Stream. The semantic dependency shall be:

```
Value Stream
   |
   +-- Value Stage / Value-Realization Area
   |
   +-- Agentic Participation
            |
            +-- Actor / Agent
            +-- Entrusted Intent
            +-- Bounded Authority
            +-- Context
            +-- Decision / Selection
            +-- Action / Progression
            +-- Outcome Contribution
```

Agentic Participation does NOT replace the Value Stream, does NOT create a parallel value-stage hierarchy, and does NOT make the Agent the semantic center of the model.

### 2.2 Participation scope vocabulary

The Agentic Value Stream SHALL support an explicit participation scope:

```
agentic_scope:
  - decision
  - execution
  - coordination
  - stage
  - cross_stage
  - end_to_end
```

`end_to_end` SHALL NOT be the default representation. A Value Stream can qualify as Agentic because of a single material agentic participation point.

### 2.3 Intent + Authority + Context + Selection

Agentic Participation SHALL explicitly reference:

- An entrusted intent. Instruction != Intent.
- A bounded authority with scope, permissions, constraints, policies, thresholds, escalation conditions, and revocation conditions.
- A relevant context (technology-agnostic).
- A permissible action space with more than one alternative.
- A selection mechanism among the alternatives.

### 2.4 Agent semantics distinction

The semantic model SHALL distinguish:

```
Agent != Agentic Participation != Agentic Value Stream
```

The Agent is NOT the definition of agenticity. Agentic Participation is.

### 2.5 AI, Automation, Autonomy remain orthogonal

The framework SHALL preserve:

- AI remains orthogonal. Valid configurations include AI + non-agentic, AI + agentic, non-AI + agentic, human + agentic, automation + agentic, AI + automation + agentic.
- Automation != Agentic Participation. Automation may participate in an AVS without itself becoming agentic.
- Autonomy is an independent dimension. Agenticity describes the presence of delegated, bounded, contextual, outcome-oriented action selection. Autonomy describes the degree of independent operation.

### 2.6 Human participation patterns

The framework SHALL support five human participation patterns as first-class:

- Pattern A: Human delegates an intended outcome to an Agent.
- Pattern B: Agent escalates an exception to a Human, who decides.
- Pattern C: Human decides, Agent executes.
- Pattern D: Agent decides, Human validates.
- Pattern E: Shared progression (alternating).

All five patterns are valid provided the underlying AVS qualification conditions (CR-VAS-002) are satisfied.

### 2.7 Prohibited parallel constructs

The framework SHALL NOT introduce any of the following as parallel semantic constructs solely to represent agenticity:

- Agentic Value Stage
- Agentic Process
- Agentic Workflow
- Agentic Operation
- Agentic Activity

A canonical Value Stage may contain any combination of human, automated, agentic, hybrid, or multiple forms of realisation.

### 2.8 Conformance kit expansion

The conformance kit SHALL be expanded to 33 tests:

- 5 positive (AVS-VAL-01..07 required-value coverage), per CR-VAS-002 §22.
- 5 negative (AVS-EXC-01..07 exclusion coverage), per CR-VAS-002 §22.
- 5 edge case (AVS-EDGE-01..05 compositional arrangements), per CR-VAS-002 §22.
- 8 structural (VAS-ST-01..08 participation structure), per CR-VAS-003 §24.
- 10 boundary (VAS-BT-01..10 participation boundary distinction), per CR-VAS-003 §24.

### 2.9 Governance rules

The framework establishes eight governance rules (AP-GOV-01..08):

1. AP-GOV-01 Value Stream remains primary.
2. AP-GOV-02 Participation is explicit.
3. AP-GOV-03 Authority is explicit.
4. AP-GOV-04 Materiality is mandatory.
5. AP-GOV-05 AI is implementation-independent.
6. AP-GOV-06 Autonomy is orthogonal.
7. AP-GOV-07 Human participation is first-class.
8. AP-GOV-08 No parallel value-stage ontology.

## 3. Implementation

### 3.1 concept.yaml participation block

A new `participation:` block is appended to the Agentic Value Stream concept record, carrying the hierarchy, scope vocabulary, intent/authority/context/action space/outcome, human participation patterns, agent/AI/automation/autonomy semantics, cardinality, distributed realisation, boundary matrix, evidence model template, machine-readable model template, and eight governance rules.

### 3.2 Conformance kit

8 new structural tests (VAS-ST-01..08) and 10 new boundary tests (VAS-BT-01..10) are added under `kit/`. The kit manifest (`kit/kit.yaml`) is updated to reflect the expanded coverage and inventory.

### 3.3 Documentation

`docs/concept.md` receives a new "Participation and Realization" section explaining the hierarchical subordination, scope vocabulary, agent/AI/automation/autonomy distinctions, prohibited parallel constructs, human participation patterns, and governance rules.

`docs/conformance.md` is regenerated with the expanded test inventory.

### 3.4 Visuals

Two new PlantUML diagrams are added under `visuals/agentic-value-stream/`:

- `participation-model.puml` ; canonical relationship set per CR-VAS-003 §19.
- `semantic-boundary-matrix.puml` ; normative boundary matrix per CR-VAS-003 §22.

### 3.5 Cross-program mappings

`mappings/wsf.yaml` and `mappings/opendea.yaml` each receive a `participation_alignment` block per CR-VAS-003 §26-§27 that distinguishes mapping types explicitly so that no metamodel mutation occurs through mapping documentation.

## 4. Consequences

### 4.1 Positive

- The repository can now represent Agentic Participation explicitly as a subordinate relationship to the Value Stream.
- The Agent is no longer the definition of agenticity; the participation relationship is.
- AI, automation, autonomy, and workflow distinctions are preserved as orthogonal dimensions.
- Human participation is established as a first-class realisation pattern.
- The conformance kit can validate both the qualification (CR-VAS-002) and the representation (CR-VAS-003) layers independently.

### 4.2 Negative

- The repository now carries more conformance tests (33 vs 15) and a richer visual vocabulary. CI regeneration must handle the expanded inventory.
- Cross-program mapping documents must distinguish mapping types explicitly, which adds authoring discipline.
- Future CRs (CR-VAS-004 Evidence & Conformance, CR-VAS-005 Measurement & Operational Value) will inherit this participation model.

### 4.3 Architectural alignment

This ADR continues the architectural separation established by ES-ADR-052:

- CR-VAS-002 = SEMANTIC QUALIFICATION (what makes a Value Stream Agentic).
- CR-VAS-003 = PARTICIPATION & REALIZATION (how is agentic participation represented).
- CR-VAS-004 = EVIDENCE & CONFORMANCE (how do we prove it).
- CR-VAS-005 = MEASUREMENT & OPERATIONAL VALUE (how well does it work).
- CR-VAS-006 = MATURITY & CAPABILITY (how well can the organisation scale and govern it).

CR-VAS-003 is therefore the second of five CRs that form a coherent semantic-to-operational chain.

## 5. Promotion Metadata

- Status: Accepted (semantic baseline extension, 2026-10-08).
- Cardinal author rule: Emmanuel A. Otchere (cardinal author rule, 2026-09-23).
- Vendor-specific material from embargoed sources: 0 references.
- D-004 dash rule: 0 en-dash (U+2013), 0 em-dash (U+2014), 0 triple-em-dash (U+2E3B).
- WSF metamodel not modified.
- OpenDEA metamodel not modified.

## 6. Related Artefacts

- CR-VAS-003 (Agentic Participation & Value Stream Realization Model).
- ES-ADR-052 (Agentic Value Stream Semantic Qualification Framework).
- ES-ADR-005 (Agentic Value Stream decision).
- ES-ADR-031 (5-category boundary taxonomy).
- ES-ADR-049 (Per-Concept Repo Self-Containment).
- ES-ADR-051 (Editorial Restructure).
- CR-AVS-001 (Repository Conformance Reconciliation).
- CR-VAS-002 (Formal Semantic Qualification).
- FND-ES-AG-008 (Foundation Recon).
