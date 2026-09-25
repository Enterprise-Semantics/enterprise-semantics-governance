CR-ES-016 , Implement Agentic Product

Target release:

v1.5.0

This CR is the implementation specification for ADR-ES-016. The CR does not authorise creation of Autonomous Product, AI Product, Product maturity, Product autonomy levels, Offering ontology, Portfolio ontology, Product Agent, Autonomous Agent, Product changes in WSF, Product changes in OpenDEA, or new foundational Product ontology per ADR-ES-016 §19 explicit deferral list and CR-ES-016 §2 out-of-scope list.

CR-ES-016 , Implementation

CR-ES-016: Implement Agentic Product

1. Purpose

Implement the canonical Agentic Product semantic specialization established by ADR-ES-016.

The implementation shall establish Agentic Product as a governed specialization of Product while preserving strict semantic separation from:

* Agent;
* Agentic Capability;
* Agentic Service;
* Agentic Workflow;
* Agentic Operations;
* Agentic Value Stream;
* Autonomous Product;
* AI;
* Automation.

No new foundational Product ontology shall be silently introduced through this CR.
;;;
2. Scope

In Scope

1. Agentic Product concept.
2. Agentic Product schema.
3. Concept registry entry.
4. Agentic Product profile.
5. Canonical relationships.
6. Agentic materiality constraints.
7. Product realization boundary.
8. Product/service boundary.
9. Product/capability boundary.
10. Product/value-stream boundary.
11. Agentic/autonomous orthogonality.
12. Authority and policy boundaries.
13. OTCHERE Inc example.
14. WSF semantic mapping.
15. OpenDEA semantic mapping.
16. Documentation.
17. PlantUML visualizations.
18. Positive conformance tests.
19. Negative conformance tests.
20. CI validation.
21. Provenance.
22. v1.5.0 release gate.

Out of Scope

* Autonomous Product.
* AI Product.
* Product maturity.
* Product autonomy levels.
* Offering ontology.
* Portfolio ontology.
* Product Agent.
* Autonomous Agent.
* Product changes in WSF.
* Product changes in OpenDEA.
* New foundational Product ontology unless separately authorized.
;;;
3. Canonical Concept

Create:

enterprise-semantics/concepts/agentic-product.yaml

Canonical definition:

An Agentic Product is a Product whose material realization, interaction, configuration, adaptation, or fulfillment incorporates agentic behavior in interpreting intent, selecting or coordinating actions, or adapting product behavior toward an intended outcome within defined authority, policy, and contextual boundaries.

Semantic type:

semantic_type: AgenticProduct

Specialization:

specializes:
  - Product
;;;
4. Required Properties

The schema shall support:

properties:
  product_intent:
  agentic_scope:
  product_context:
  delegated_intent:
  authority_context:
  decision_boundary:
  action_selection_scope:
  coordination_scope:
  adaptation_scope:
  intervention_model:
  escalation_boundary:
  policy_context:
  constraint_context:
  realization_mode:

Properties must describe the agentic realization of the Product, not duplicate unrelated Product semantics.
;;;
5. Material Agentic Realization

The implementation shall enforce the distinction between:

Agentic Product

and:

Product containing AI
Product containing automation
Product invoking an Agent
Product with adaptive software

A valid Agentic Product must demonstrate material agentic behavior affecting product realization or interaction.

The validator should recognize characteristics such as:

* intent interpretation;
* contextual interpretation;
* dynamic action selection;
* agentic coordination;
* contextual adaptation;
* exception interpretation;
* bounded decision-making;
* escalation.

Presence of an AI component alone shall fail the agentic-materiality requirement.
;;;
6. Registry

Add:

AGENTIC_PRODUCT

to the canonical concept registry.

The registry entry shall reference:

enterprise-semantics/concepts/agentic-product.yaml

Registry validation shall confirm:

* unique identifier;
* canonical name;
* semantic type;
* specialization;
* lifecycle status;
* version;
* provenance;
* schema location.
;;;
7. Profile

Create:

ES:PROFILE:AGENTIC_PRODUCT

The profile shall identify the semantic scope of Agentic Product.

Indicative structure:

id: ES:PROFILE:AGENTIC_PRODUCT
name: Agentic Product
scope:
  - Product
  - Agentic Product
  - Agent
  - Intent
  - Authority
  - Action

The profile shall not imply that every scoped concept is a subtype of Product.
;;;
8. Relationships

Where canonical predicates and target concepts exist, implement:

Agentic Product
    -> specializes -> Product
    -> engages -> Agent
    -> interprets -> Intent
    -> operates-within -> Authority
    -> governed-by -> Policy
    -> constrained-by -> Constraint
    -> uses -> Agentic Workflow
    -> produces -> Outcome
    -> adapts-to -> Context
    -> supports -> Capability
    -> delivered-through -> Service
    -> contributes-to -> Value

The implementation must not create a new predicate merely to satisfy this CR if an equivalent canonical predicate already exists.

If a target concept is not yet canonical:

1. do not silently create it;
2. record the relationship as deferred;
3. document the dependency;
4. preserve the semantic intent in the mapping/documentation layer.
;;;
9. Agentic / Autonomous Orthogonality

The implementation must enforce:

Agentic Product ≠ Autonomous Product

No inheritance relationship shall be created between them.

The conformance model shall support:

Agentic	Autonomous	Result
No	No	Product
Yes	No	Agentic Product
No	Yes	Autonomous Product: future
Yes	Yes	Agentic + Autonomous Product: future combination

The CR does not authorize implementation of Autonomous Product.
;;;
10. AI Independence

The test suite shall verify:

AI-enabled Product -> not necessarily Agentic Product

Negative test:

A Product containing an AI model alone
must not satisfy Agentic Product conformance.

Positive test:

A Product materially interpreting delegated intent,
selecting permitted actions, and adapting its behavior
within authority boundaries may satisfy Agentic Product
conformance without requiring AI.
;;;
11. Automation Independence

The test suite shall verify:

Automated Product ≠ Agentic Product

A deterministic rules engine, workflow engine, script, or automation mechanism shall not satisfy Agentic Product conformance merely because it executes automatically.
;;;
12. Human Participation

The conformance suite shall explicitly permit:

human-in-loop
human-on-loop
human-over-loop
exception intervention
approval
escalation

The following shall fail:

Agentic Product requires removal of humans
;;;
13. Product / Service Boundary

Add architectural documentation showing:

Product
   |
   |-- Agentic Product
           |
           |-- may be delivered-through ->
                         Service
                            |
                            +-- Agentic Service
                            |-- Autonomous Service

Conformance must prevent:

Agentic Service is-a Agentic Product

and:

Agentic Product is-a Agentic Service

unless an explicitly modeled separate specialization exists.
;;;
14. Product / Capability Boundary

Document:

Capability
    -> enables
Product
Agentic Capability
    -> may enable
Agentic Product

The validator must prevent:

Agentic Capability is-a Agentic Product

and:

Agentic Product is-a Agentic Capability
;;;
15. Product / Value Stream Boundary

Document:

Agentic Value Stream
        ->
may involve
        ->
Agentic Product

The validator must prevent:

Agentic Product is-a Agentic Value Stream

and:

Agentic Value Stream is-a Agentic Product
;;;
16. Product / Workflow Boundary

Document:

Agentic Product
       ->
may use
       ->
Agentic Workflow
       ->
Activity / Task
       ->
Agent / Human / System

The Product remains the product-level semantic entity.

The Workflow remains the execution/coordination construct.

The validator must prevent:

Agentic Workflow is-a Agentic Product
;;;
17. Product / Operations Boundary

Document:

Agentic Product
       ->
may depend on / use
       ->
Agentic Operations

Agentic Operations represents the operating environment or mode of operational realization.

It is not a Product subtype.
;;;
18. Architecture Documentation

Create:

enterprise-semantics-docs/concepts/agentic-product.md

Create architecture documents:

enterprise-semantics-docs/architecture/
  agentic-product-boundary.md
  product-agentic-realization-boundary.md
  agentic-product-execution-boundary.md
  agentic-product-capability-boundary.md
  agentic-product-service-boundary.md
  agentic-product-value-stream-boundary.md
  agentic-product-operations-boundary.md
  agentic-vs-autonomous-product.md
  product-authority-escalation-boundary.md

Documentation shall explicitly distinguish:

Product
Agentic Product
Agentic Service
Agentic Capability
Agentic Workflow
Agentic Operations
Agentic Value Stream
;;;
19. Visualizations

Create:

enterprise-semantics-visuals/
  concepts/
    agentic-product.puml
  relationships/
    agentic-product-relationships.puml
  architecture/
    product-agentic-realization-boundary.puml
    agentic-product-execution-boundary.puml
    agentic-product-capability-boundary.puml
    agentic-product-service-boundary.puml
    agentic-product-value-stream-boundary.puml
    agentic-product-operations-boundary.puml
    agentic-vs-autonomous-product.puml
    product-authority-escalation-boundary.puml

The primary conceptual diagram shall show:

                 Product
                    |
             specializes
                    ->
             Agentic Product
                    |
       +------------┼-------------+
       ->            ->             ->
     Intent      Authority      Context
       |            |             |
       |------------┼-------------┘
                    ->
            Action Selection
                    ->
             Product Outcome
                    ->
                Adaptation
;;;
20. Example

Create:

enterprise-semantics-examples/products/
  otchere-agentic-products.yaml

The example shall use OTCHERE Inc.

Example:

Customer Resolution Product
        ->
Agentic Customer Resolution Product
        ->
Customer Intent
        ->
Context Interpretation
        ->
Permitted Resolution Selection
        ->
Action Coordination
        ->
Resolution Execution
        ->
Customer Outcome
        ->
Adapt / Escalate

The example shall demonstrate:

* delegated intent;
* contextual interpretation;
* authority;
* action selection;
* policy/constraint boundaries;
* outcome orientation;
* adaptation;
* human escalation.

It shall not require AI.
;;;
21. WSF Mapping

Create:

enterprise-semantics-mappings/wsf/agentic-product.yaml

The mapping shall document:

* source concept;
* Enterprise-Semantics concept;
* semantic correspondence;
* specialization intent;
* provenance;
* unresolved semantic dependencies.

No WSF repository modification is authorized.
;;;
22. OpenDEA Mapping

Create:

enterprise-semantics-mappings/opendea/agentic-product.yaml

The mapping shall document:

* OpenDEA Product correspondence;
* Enterprise-Semantics Agentic Product specialization;
* relevant OpenDEA architectural context;
* semantic constraints;
* unresolved mappings.

No OpenDEA repository modification is authorized.
;;;
23. Conformance Tests

Create:

enterprise-semantics-test-probe/conformance/agentic-product/

Positive Tests

Implement at minimum:

APROD-CON-001  Agentic Product specializes Product
APROD-CON-002  Product semantics are retained
APROD-CON-003  Material agentic realization exists
APROD-CON-004  Product realization is outcome-oriented
APROD-CON-005  Intent interpretation is supported
APROD-CON-006  Contextual interpretation is supported
APROD-CON-007  Action selection may occur
APROD-CON-008  Coordination may occur
APROD-CON-009  Adaptation may occur
APROD-CON-010  Authority boundary exists
APROD-CON-011  Policy/constraint boundary exists
APROD-CON-012  Human intervention is permitted
APROD-CON-013  Agentic Workflow may support realization
APROD-CON-014  Agent may participate
APROD-CON-015  Agentic Product may support Capability
APROD-CON-016  Agentic Product may participate in Value Stream
APROD-CON-017  AI is not required
APROD-CON-018  Automation is not sufficient
APROD-CON-019  Agentic does not imply Autonomous
APROD-CON-020  Provenance and grounding are present
;;;
24. Negative Tests

Implement at minimum:

APROD-NEG-001  Agentic Product is-a Agent
APROD-NEG-002  Agentic Product is-a Agentic Capability
APROD-NEG-003  Agentic Product is-a Agentic Service
APROD-NEG-004  Agentic Product is-a Agentic Workflow
APROD-NEG-005  Agentic Product is-a Agentic Operations
APROD-NEG-006  Agentic Product is-a Agentic Value Stream
APROD-NEG-007  Agentic Product requires AI
APROD-NEG-008  AI-enabled Product automatically becomes Agentic Product
APROD-NEG-009  Automated Product automatically becomes Agentic Product
APROD-NEG-010  Product containing an Agent automatically becomes Agentic Product
APROD-NEG-011  Agentic Product automatically becomes Autonomous Product
APROD-NEG-012  Agentic Product requires elimination of humans
APROD-NEG-013  Agentic Product has unlimited authority
APROD-NEG-014  Agentic Product requires every product action to be agentic
APROD-NEG-015  Agentic Product automatically establishes Agentic Value Stream
APROD-NEG-016  Agentic Product automatically establishes Agentic Enterprise
;;;
25. Schema Validation

CI shall validate:

* schema syntax;
* required properties;
* property types;
* specialization;
* relationship integrity;
* registry integrity;
* provenance;
* version;
* profile membership;
* mapping references.
;;;
26. Semantic Integrity Validation

CI shall explicitly validate:

Agentic Product -> Product

and reject unauthorized inheritance:

Agentic Product -> Agent
Agentic Product -> Agentic Capability
Agentic Product -> Agentic Service
Agentic Product -> Agentic Workflow
Agentic Product -> Agentic Operations
Agentic Product -> Agentic Value Stream
Agentic Product -> Autonomous Product

The test suite must also ensure that these are not introduced indirectly through profiles or mappings.
;;;
27. Materiality Validation

A conformance implementation shall distinguish between:

Insufficient

Product
  + AI component
Product
  + automated workflow
Product
  + Agent invocation

Potentially Agentic

Product
  + delegated intent
  + contextual interpretation
  + bounded authority
  + dynamic action selection
  + outcome-oriented adaptation

The validator must assess semantic evidence rather than technology labels.
;;;
28. Provenance

The concept shall contain:

provenance:
  source:
    - ADR-ES-003
    - ADR-ES-004
    - ADR-ES-005
    - ADR-ES-006
    - ADR-ES-007
    - ADR-ES-012
    - ADR-ES-014
    - ADR-ES-015
  decision:
    - ADR-ES-016
  implementation:
    - CR-ES-016

Additional provenance may be added where actual external grounding is subsequently documented.
;;;
29. Acceptance Criteria

CR-ES-016 is complete only when:

* [ ]	Agentic Product is canonically defined.
* [ ]	Product specialization is represented.
* [ ]	Material agentic realization is enforced.
* [ ]	Intent semantics are represented.
* [ ]	Authority boundaries are represented.
* [ ]	Policy/constraint boundaries are represented.
* [ ]	Outcome orientation is represented.
* [ ]	Adaptation is represented.
* [ ]	Human intervention remains valid.
* [ ]	AI independence is validated.
* [ ]	Automation independence is validated.
* [ ]	Agentic/Autonomous orthogonality is validated.
* [ ]	Product/Capability boundary is documented.
* [ ]	Product/Service boundary is documented.
* [ ]	Product/Workflow boundary is documented.
* [ ]	Product/Operations boundary is documented.
* [ ]	Product/Value Stream boundary is documented.
* [ ]	Agentic Product does not inherit from Agent.
* [ ]	Agentic Product does not inherit from Agentic Capability.
* [ ]	Agentic Product does not inherit from Agentic Service.
* [ ]	Agentic Product does not inherit from Agentic Workflow.
* [ ]	Agentic Product does not inherit from Agentic Operations.
* [ ]	Agentic Product does not inherit from Agentic Value Stream.
* [ ]	Autonomous Product is not introduced.
* [ ]	OTCHERE Inc example exists.
* [ ]	WSF mapping exists.
* [ ]	OpenDEA mapping exists.
* [ ]	Documentation exists.
* [ ]	PlantUML diagrams exist.
* [ ]	Positive conformance tests pass.
* [ ]	Negative conformance tests pass.
* [ ]	Provenance is complete.
* [ ]	CI passes.
* [ ]	No unauthorized foundational concepts are introduced.
;;;
30. Release Gate

Successful completion authorizes:

Enterprise-Semantics v1.5.0

The release shall contain the Agentic Product semantic specialization and its supporting schemas, mappings, profiles, documentation, examples, diagrams, and conformance suite.

No WSF or OpenDEA implementation release is implied.
;;;
31. Architectural Continuity

The resulting semantic architecture becomes:

Capability
   +-- Agentic Capability
   |-- Autonomous Capability
Product
   |-- Agentic Product
       |-- [Autonomous Product: future]
Service
   +-- Agentic Service
   |-- Autonomous Service
Value Stream
   +-- Agentic Value Stream
   |-- Autonomous Value Stream
Enterprise
   +-- Agentic Enterprise
   |-- Autonomous Enterprise

Agentic and Autonomous remain orthogonal semantic dimensions, not a single maturity ladder.

The next autonomous specialization of Product, if required, shall be governed separately rather than inferred from this CR.

This gives the sequence a coherent progression: Capability -> Product -> Service, while keeping Agentic and Autonomous as independent semantic dimensions rather than turning the model into an AI/autonomy maturity hierarchy.


<!--
Authored by: Emmanuel A. Otchere (cardinal author rule, 2026-09-24)
-->
