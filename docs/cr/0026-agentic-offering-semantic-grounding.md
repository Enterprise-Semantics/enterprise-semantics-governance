CR-ES-018 , Implement Agentic Offering

Target release:

v1.7.0

This CR is the implementation specification for ADR-ES-018. The CR does not authorise creation of Autonomous Offering, Product autonomy maturity, Autonomous Portfolio, Autonomous Agent, Autonomous Product Agent, Autonomous Ecosystem, or new foundational Offering ontology per ADR-ES-018 §14 explicit deferral list and CR-ES-018 §2 foundational dependency gate. If Offering is not yet canonical, CR-ES-018 remains Blocked by Dependency and shall not create a substitute Offering definition.

CR-ES-018 , Implementation

CR-ES-018: Implement Agentic Offering

1. Purpose

Implement Agentic Offering as a specialization of Offering while preserving the distinction between:

* Offering;
* Product;
* Service;
* Agentic Product;
* Agentic Service;
* Agentic Workflow;
* Agentic Operations;
* Agentic Value Stream;
* Agentic Enterprise.
;;;
2. Foundational Dependency Gate

Before implementation:

CHECK:
Is Offering canonical in Enterprise-Semantics?

If YES:

Proceed with Agentic Offering specialization.

If NO:

Block canonical implementation and raise a dependency for a separately governed Offering semantic grounding ADR.

CR-ES-018 shall not create Offering implicitly.
;;;
3. Concept

If the dependency gate passes, create:

enterprise-semantics/concepts/agentic-offering.yaml

Canonical definition:

An Agentic Offering is an Offering whose composition, interaction, configuration, fulfillment, or value realization materially incorporates agentic behavior in interpreting intent, selecting or coordinating actions, or adapting the offering toward an intended stakeholder outcome within defined authority, policy, and contextual boundaries.
;;;
4. Properties

Implement:

properties:
  offering_intent:
  agentic_scope:
  offering_context:
  delegated_intent:
  authority_context:
  decision_boundary:
  configuration_scope:
  composition_scope:
  coordination_scope:
  adaptation_scope:
  intervention_model:
  escalation_boundary:
  policy_context:
  constraint_context:
  realization_mode:

Properties must describe agentic Offering realization and must not duplicate foundational Offering properties unnecessarily.
;;;
5. Registry

Add:

AGENTIC_OFFERING

to the canonical registry.
;;;
6. Profile

Create:

ES:PROFILE:AGENTIC_OFFERING

The profile shall group the semantic concepts relevant to Agentic Offering without implying that all are subtypes.
;;;
7. Relationships

Where canonical dependencies exist:

Agentic Offering
    -> specializes -> Offering
    -> engages -> Agent
    -> interprets -> Intent
    -> operates-within -> Authority
    -> governed-by -> Policy
    -> constrained-by -> Constraint
    -> uses -> Agentic Product
    -> uses -> Agentic Service
    -> uses -> Agentic Workflow
    -> supports -> Capability
    -> produces -> Outcome
    -> adapts-to -> Context
    -> contributes-to -> Value

Unresolved relationships shall be documented rather than implemented through unauthorized concept creation.
;;;
8. Product Boundary

Document:

Offering
   +-- Product
   |    |-- Agentic Product
   |
   |-- Agentic Offering

The validator shall reject:

Agentic Offering is-a Agentic Product

and:

Agentic Product is-a Agentic Offering

unless a separate, explicitly governed relationship establishes such correspondence.
;;;
9. Service Boundary

Document:

Agentic Offering
      ->
may use
      ->
Agentic Service

The validator shall reject:

Agentic Offering is-a Agentic Service
;;;
10. Value Stream Boundary

Document:

Agentic Value Stream
      ->
may involve
      ->
Agentic Offering

The validator shall reject:

Agentic Offering is-a Agentic Value Stream
;;;
11. Workflow Boundary

Document:

Agentic Offering
      ->
may use
      ->
Agentic Workflow

Workflow remains the execution/coordination construct.
;;;
12. Operations Boundary

Document:

Agentic Offering
      ->
may depend upon
      ->
Agentic Operations

Agentic Operations is not a subtype of Offering.
;;;
13. Agentic Materiality

The implementation shall distinguish:

Insufficient

Offering
  + AI
Offering
  + automation
Offering
  + chatbot
Offering
  + Agent somewhere in implementation

Potentially Agentic

Offering
  + stakeholder intent interpretation
  + contextual evaluation
  + bounded authority
  + dynamic composition/configuration
  + action selection
  + coordination
  + adaptation
;;;
14. Conformance Tests

Create:

enterprise-semantics-test-probe/conformance/agentic-offering/

Positive tests:

AOFF-CON-001  specializes Offering
AOFF-CON-002  retains Offering semantics
AOFF-CON-003  material agentic behavior exists
AOFF-CON-004  stakeholder intent may be interpreted
AOFF-CON-005  context may influence realization
AOFF-CON-006  configuration may be dynamically selected
AOFF-CON-007  composition may be dynamically selected
AOFF-CON-008  coordination may occur
AOFF-CON-009  adaptation may occur
AOFF-CON-010  authority boundary exists
AOFF-CON-011  policy/constraint boundary exists
AOFF-CON-012  outcome orientation exists
AOFF-CON-013  human intervention is permitted
AOFF-CON-014  Agentic Product may participate
AOFF-CON-015  Agentic Service may participate
AOFF-CON-016  Agentic Workflow may participate
AOFF-CON-017  AI is not required
AOFF-CON-018  automation is not sufficient
AOFF-CON-019  Agentic does not imply Autonomous
AOFF-CON-020  provenance is complete

Negative tests:

AOFF-NEG-001  Agentic Offering is-a Agent
AOFF-NEG-002  Agentic Offering is-a Agentic Product
AOFF-NEG-003  Agentic Offering is-a Agentic Service
AOFF-NEG-004  Agentic Offering is-a Agentic Workflow
AOFF-NEG-005  Agentic Offering is-a Agentic Operations
AOFF-NEG-006  Agentic Offering is-a Agentic Value Stream
AOFF-NEG-007  Agentic Offering requires AI
AOFF-NEG-008  AI automatically establishes Agentic Offering
AOFF-NEG-009  Automation automatically establishes Agentic Offering
AOFF-NEG-010  Offering containing an Agent automatically becomes Agentic Offering
AOFF-NEG-011  Agentic Offering automatically becomes Autonomous Offering
AOFF-NEG-012  Agentic Offering requires removal of humans
AOFF-NEG-013  Agentic Offering has unlimited authority
AOFF-NEG-014  Agentic Product automatically makes the whole Offering agentic
AOFF-NEG-015  Agentic Service automatically makes the whole Offering agentic
;;;
15. Documentation

Create:

enterprise-semantics-docs/concepts/agentic-offering.md

Architecture:

enterprise-semantics-docs/architecture/
  agentic-offering-boundary.md
  offering-agentic-realization-boundary.md
  agentic-offering-product-boundary.md
  agentic-offering-service-boundary.md
  agentic-offering-execution-boundary.md
  agentic-offering-value-stream-boundary.md
  agentic-offering-operations-boundary.md
  agentic-vs-autonomous-offering.md
  offering-authority-escalation-boundary.md
;;;
16. Visualizations

Create:

enterprise-semantics-visuals/concepts/agentic-offering.puml
enterprise-semantics-visuals/relationships/agentic-offering-relationships.puml
enterprise-semantics-visuals/architecture/offering-agentic-realization-boundary.puml
enterprise-semantics-visuals/architecture/agentic-offering-product-boundary.puml
enterprise-semantics-visuals/architecture/agentic-offering-service-boundary.puml
enterprise-semantics-visuals/architecture/agentic-offering-execution-boundary.puml
enterprise-semantics-visuals/architecture/agentic-offering-value-stream-boundary.puml
enterprise-semantics-visuals/architecture/agentic-offering-operations-boundary.puml
enterprise-semantics-visuals/architecture/agentic-vs-autonomous-offering.puml
enterprise-semantics-visuals/architecture/offering-authority-escalation-boundary.puml
;;;
17. Example

Create:

enterprise-semantics-examples/offerings/
  otchere-agentic-offerings.yaml

Example:

Customer Intent
       ->
Agentic Integrated Business Offering
       ->
Interpret Customer Context
       ->
Determine Appropriate Proposition
       ->
Compose Product + Service
       ->
Coordinate Fulfillment
       ->
Observe Customer Outcome
       ->
Adapt / Escalate

The example must demonstrate agentic materiality at the Offering boundary, not merely inherit the classification from an Agentic Product or Agentic Service.
;;;
18. Mappings

Create:

enterprise-semantics-mappings/wsf/agentic-offering.yaml
enterprise-semantics-mappings/opendea/agentic-offering.yaml

Mappings shall document correspondence and specialization intent.

No WSF/OpenDEA implementation change is authorized.
;;;
19. Provenance

provenance:
  source:
    - ADR-ES-004
    - ADR-ES-005
    - ADR-ES-006
    - ADR-ES-007
    - ADR-ES-012
    - ADR-ES-014
    - ADR-ES-016
    - ADR-ES-017
  decision:
    - ADR-ES-018
  implementation:
    - CR-ES-018
;;;
20. Acceptance Criteria

* [ ]	Offering dependency verified.
* [ ]	Agentic Offering canonically defined.
* [ ]	Agentic specialization implemented only if Offering is canonical.
* [ ]	Material agentic realization validated.
* [ ]	Intent interpretation represented.
* [ ]	Contextual realization represented.
* [ ]	Configuration/composition scope represented.
* [ ]	Authority represented.
* [ ]	Policy/constraint boundaries represented.
* [ ]	Outcome orientation represented.
* [ ]	Adaptation represented.
* [ ]	Human participation preserved.
* [ ]	AI independence validated.
* [ ]	Automation independence validated.
* [ ]	Product boundary validated.
* [ ]	Service boundary validated.
* [ ]	Workflow boundary validated.
* [ ]	Operations boundary validated.
* [ ]	Value Stream boundary validated.
* [ ]	Agentic/Autonomous orthogonality validated.
* [ ]	OTCHERE Inc example implemented.
* [ ]	WSF mapping implemented or dependency documented.
* [ ]	OpenDEA mapping implemented or dependency documented.
* [ ]	Documentation implemented.
* [ ]	Visuals implemented.
* [ ]	Positive tests pass.
* [ ]	Negative tests pass.
* [ ]	Provenance passes.
* [ ]	CI passes.
* [ ]	No unauthorized Offering ontology is introduced.
;;;
21. Release Gate

If the Offering dependency is satisfied:

Enterprise-Semantics v1.7.0

If Offering is not yet canonical, CR-ES-018 remains Blocked by Dependency and shall not create a substitute Offering definition.
;;;
22. Architectural Continuity

The resulting structure is:

Capability
 +-- Agentic Capability
 |-- Autonomous Capability
Product
 +-- Agentic Product
 |-- Autonomous Product
Service
 +-- Agentic Service
 |-- Autonomous Service
Offering
 |-- Agentic Offering
     |-- [Autonomous Offering: future]
Value Stream
 +-- Agentic Value Stream
 |-- Autonomous Value Stream
Enterprise
 +-- Agentic Enterprise
 |-- Autonomous Enterprise

This preserves the central semantic architecture:

                 AGENTIC              AUTONOMOUS
                    |                     |
                    |                     |
Capability ---------┼---------------------┼--
Product ------------┼---------------------┼--
Service ------------┼---------------------┼--
Offering -----------┼---------------------┼--
Value Stream -------┼---------------------┼--
Enterprise ---------┼---------------------┼--

Agentic and Autonomous are cross-cutting semantic dimensions, while each domain concept retains its own semantic identity and realization boundary.

Architectural note: 017 completes the Product pair cleanly. 018 deliberately introduces a dependency gate because Offering should not be invented implicitly merely to support its Agentic specialization. That gate is important for maintaining the Enterprise-Semantics authority rather than allowing the agentic-concepts sequence to accidentally become the mechanism by which foundational enterprise concepts are created.


<!--
Authored by: Emmanuel A. Otchere (cardinal author rule, 2026-09-24)
-->


## Promotion Metadata

- Status: Proposed -> Accepted
- Date Accepted: 2026-09-25
- Authorising Directive: USER-DIRECTIVE-1552900782440058902 ("Proceed with 18")
- Foundational Dependency Gate: documented, not blocked, per user override of Path X (ADR-ES-018 §16 + CR-ES-018 §2)
- Implementation Chain: 8 PRs across 6 repos (VS-A through VS-D2c)
- Dependency Resolution: ADR-ES-019 (Offering canonical grounding) remains unresolved at acceptance
- Promotion Author: Emmanuel A. Otchere (cardinal author rule, 2026-09-24)
- Promotion Ritual: 2-touchpoint per ES series ADR-ES-001 §10-§11
