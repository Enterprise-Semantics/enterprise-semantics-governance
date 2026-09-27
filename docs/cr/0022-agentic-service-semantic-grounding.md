CR-ES-014 , Implement Agentic Service

Target release:

v1.3.0

This CR is the implementation specification for ADR-ES-014. The CR does not authorise creation of Autonomous Service, Agentic Product, Autonomous Product, AI Service, AI-native Service, service autonomy maturity, service autonomy levels, or modifications to WSF or OpenDEA per ADR-ES-014 §19 explicit deferral list.

CR-ES-014 , Implementation

CR-ES-014: Implement Agentic Service

## Promotion Metadata

- **Status:** Accepted
- **Promotion Date:** 2026-09-24
- **Authorizing ADR:** ADR-ES-014 (Accepted 2026-09-24)
- **Implementation Target:** v1.3.0
- **Depends On:** ADR-ES-002, ADR-ES-003, ADR-ES-004, ADR-ES-005, ADR-ES-006, ADR-ES-007, ADR-ES-012
- **Promotion Rationale:** All 34 acceptance criteria from CR-ES-014 §18 satisfied via 8 implementation PRs across 6 repos ; validator NO_DRIFT (22 Concept records validated) ; v1.3.0 Agentic Service release pointer established ; Agentic Materiality rule enforced per ASVC-CON-003 ; Agentic Capability -> Agentic Service -> Agentic Value Stream traceability chain established ; Agentic/Autonomous orthogonality at service boundary preserved per ASVC-NEG-006 ; AI/Automation independence verified per ASVC-CON-014..015 ; human participation preserved per ASVC-CON-013 ; per user directive message 1552724263121981440, "followup with appropriate implementation"

1. Decision

Establish Agentic Service as a governed semantic specialization of Service.

Canonical definition

An Agentic Service is a Service whose delivery or interaction materially incorporates agentic behavior in interpreting intent, selecting or coordinating actions, adapting service behavior, or executing service responses toward an intended outcome within defined authority, policy, and contextual boundaries.

The specialization is:

Service
   |
   |-- Agentic Service

Agentic Service does not redefine Service and does not make AI, automation, autonomy, or an Agent a prerequisite.
;;;
2. Semantic Rationale

The semantic architecture currently establishes agentic specializations across:

Capability
Value Stream
Workflow
Operations
Enterprise

Service is the next important boundary because a Service represents a means through which a capability or value is made available to a consumer or stakeholder.

The distinction is therefore:

Agentic Capability
        |
        +-- may be delivered-through ---> Agentic Service
        |
        |-- may enable ----------------> Agentic Value Stream

An Agentic Service is consequently concerned with agentic service delivery or interaction, rather than with the entire value stream or the underlying capability.
;;;
3. Service Semantics

The existing semantic meaning of Service shall remain authoritative.

Agentic Service retains the essential characteristics of Service, including its relationship to:

* provider
* consumer
* service interaction
* service outcome
* service delivery
* capability realization

Agentic behavior qualifies how the service is delivered or interacted with.

It does not change the fundamental identity of Service.
;;;
4. Agentic Materiality

A Service shall not become Agentic merely because it:

* invokes an Agent,
* uses AI,
* uses automation,
* exposes an API,
* contains an AI model,
* supports conversational interaction,
* is implemented by an autonomous system.

Agentic behavior must be material to service realization.

Examples of material agentic behavior include:

1. interpreting delegated service intent;
2. interpreting contextual service conditions;
3. dynamically selecting service actions;
4. dynamically coordinating service actions;
5. adapting service behavior;
6. interpreting service exceptions;
7. deciding within bounded service authority;
8. escalating when authority or policy boundaries are reached.
;;;
5. Canonical Agentic Service Pattern

Service Intent
      ->
Agentic Service
      ->
Service Context
      ->
Interpretation
      ->
Decision / Action Selection
      ->
Service Execution
      ->
Service Outcome
      ->
Contextual Adaptation
      ↺

Bounded by:

Authority
Policy
Constraints
Service Contract
Governance
Escalation

The pattern may include:

Human
Agent
System
Service
Workflow
Agentic Workflow

No particular implementation mechanism is required.
;;;
6. Core Semantic Distinctions

Agentic Service vs Agent

Agent
= Entity capable of interpreting delegated intent,
  selecting/coordinating actions, and acting within authority.
Agentic Service
= Service whose realization materially incorporates
  agentic behavior.

An Agent may participate in an Agentic Service without being the Service itself.

Therefore:

Agent ≠ Agentic Service
;;;
7. Agentic Service vs Agentic Capability

Agentic Capability
= enduring ability to achieve or enable an Outcome
  through material agentic realization.
Agentic Service
= means through which a capability or service outcome
  is made available through material agentic realization.

A capability may be delivered through an Agentic Service.

An Agentic Service may expose or enable capabilities that are not themselves Agentic Capabilities.

Therefore:

Agentic Capability ≠ Agentic Service
;;;
8. Agentic Service vs Agentic Workflow

Agentic Workflow
= agentic coordination/execution of work.
Agentic Service
= agentic realization of a service interaction or delivery.

An Agentic Service may use one or more Agentic Workflows.

The workflow is an execution mechanism; the service is the service-level offering/delivery construct.

Therefore:

Agentic Service ≠ Agentic Workflow
;;;
9. Agentic Service vs Agentic Operations

Agentic Operations
= agentic operating mode for ongoing operational activity.
Agentic Service
= service realization through agentic behavior.

An Agentic Service may operate within Agentic Operations.

Agentic Operations do not make every Service Agentic.

Therefore:

Agentic Service ≠ Agentic Operations
;;;
10. Agentic Service vs Agentic Value Stream

Agentic Value Stream
= end-to-end stakeholder value realization
  materially involving agentic behavior.
Agentic Service
= service-level delivery or interaction
  materially involving agentic behavior.

An Agentic Value Stream may use multiple Agentic Services.

An Agentic Service does not imply an Agentic Value Stream.

Therefore:

Agentic Service ≠ Agentic Value Stream
;;;
11. Agentic / Autonomous Orthogonality

Agentic Service establishes only the agentic dimension.

It does not establish Autonomous Service.

The following states remain semantically possible:

Agentic	Autonomous	Interpretation
No	No	Conventional Service
Yes	No	Agentic Service
No	Yes	Future Autonomous Service
Yes	Yes	Future combined characterization

Autonomous Service requires a separate ADR.

This ADR therefore does not establish:

Autonomous Service
;;;
12. AI Boundary

AI may be used to implement an Agentic Service.

However:

AI-enabled Service ≠ Agentic Service

and:

Agentic Service does not require AI

A deterministic or non-AI mechanism may exhibit agentic service behavior where the semantic conditions are satisfied.
;;;
13. Automation Boundary

Automation may participate in an Agentic Service.

However:

Automated Service ≠ Agentic Service

Automation provides an execution mechanism.

Agentic behavior concerns contextual interpretation, action selection, coordination, adaptation, and bounded decision behavior.
;;;
14. Human Participation

Human participation does not invalidate Agentic Service.

An Agentic Service may use:

* human-in-the-loop;
* human-on-the-loop;
* human-over-the-loop;
* human escalation;
* approval gates;
* exception handling.

The defining property is agentic service realization, not removal of humans.
;;;
15. Canonical Relationships

Subject to existing canonical vocabulary:

Agentic Service
    +-- specializes -> Service
    +-- engages -> Agent
    +-- interprets -> Intent
    +-- operates-within -> Authority
    +-- governed-by -> Policy
    +-- uses -> Agentic Workflow
    +-- produces -> Outcome
    +-- adapts-to -> Context
    +-- delivers -> Value
    |-- supports -> Capability

Only relationships whose predicates and target concepts are already canonical shall be implemented.

No relationship shall silently create a new foundational concept.
;;;
16. Service Interaction Boundary

The service-level semantic boundary is:

STAKEHOLDER / CONSUMER
        |
        | Service Interaction
        ->
AGENTIC SERVICE
        |
        +-- interprets intent
        +-- evaluates context
        +-- selects action
        +-- coordinates execution
        +-- adapts response
        |-- escalates exceptions
        |
        ->
SERVICE OUTCOME

This is distinct from the underlying execution boundary:

Agentic Service
       ->
Agentic Workflow
       ->
Activity / Task
       ->
Agent / Human / System
;;;
17. Conformance Invariants

The following are canonical invariants:

Agentic Service is-a Service
Agentic Service ≠ Agent
Agentic Service ≠ Capability
Agentic Service ≠ Agentic Capability
Agentic Service ≠ Agentic Workflow
Agentic Service ≠ Agentic Operations
Agentic Service ≠ Agentic Value Stream
Agentic Service does not require AI
Agentic Service does not require automation
Automation does not establish Agentic Service
AI does not establish Agentic Service
Agentic Service does not imply Autonomous Service
Agentic Service does not imply Autonomous Operations
Agentic Service does not imply Autonomous Value Stream
Agentic Service does not imply Autonomous Enterprise
Human participation does not invalidate Agentic Service
Agentic behavior must be material to service realization
;;;
18. Example: OTCHERE Inc Customer Resolution Service

OTCHERE Inc provides a Customer Resolution Service.

A conventional implementation may route every request according to predefined rules.

An Agentic Customer Resolution Service may:

Customer Intent
       ->
Interpret Customer Context
       ->
Determine Resolution Path
       ->
Check Service Authority
       ->
Select Permitted Action
       ->
Coordinate Fulfillment
       ->
Observe Customer Response
       ->
Adapt / Escalate
       ↺

The service remains a Service.

Its agentic nature derives from the material agentic behavior through which service realization occurs.

A human may intervene where:

* authority is exceeded;
* policy requires approval;
* an exception is ambiguous;
* the customer requests human escalation.
;;;
19. Deferred Concepts

This ADR does not establish:

* Autonomous Service
* Autonomous Service maturity
* AI Service
* AI-native Service
* Agentic Product
* Autonomous Product
* Agentic Contract
* Agentic Agreement
* Autonomous Organization
* Agentic Organization
* Service autonomy levels

Each requires separate semantic grounding.
;;;
20. Consequences

Positive

* extends agentic semantics into the service layer;
* preserves Service as the foundational concept;
* separates service realization from capability, workflow, operations, and value-stream semantics;
* provides a technology-neutral definition;
* enables Agentic Capability -> Agentic Service -> Agentic Value Stream traceability;
* supports future autonomous service semantics without conflating autonomy and agentic behavior.

Constraints

* agentic participation must be material;
* AI cannot be used as a semantic shortcut;
* automation cannot be used as a semantic shortcut;
* autonomous behavior cannot be inferred;
* service contracts, authority, policies, and escalation boundaries must remain explicit where applicable.
;;;
21. Provenance

provenance:
  source:
    - ADR-ES-002
    - ADR-ES-003
    - ADR-ES-004
    - ADR-ES-005
    - ADR-ES-006
    - ADR-ES-007
    - ADR-ES-012
  decision:
    - ADR-ES-014

Decision: Establish Agentic Service as a governed specialization of Service and authorize CR-ES-014 implementation.

The corresponding implementation CR is:

CR-ES-014: Implement Agentic Service

Status: Proposed
Date: 2026-09-25
Change Type: Foundational Semantic Implementation
Priority: P0
Target: Enterprise-Semantics
Authorizing ADR: ADR-ES-014
Target Release: v1.3.0
;;;
1. Objective

Implement Agentic Service as a canonical Enterprise-Semantics specialization of Service.

The implementation shall establish agentic service realization while maintaining strict semantic separation from:

* Agent
* Capability
* Agentic Capability
* Workflow
* Agentic Workflow
* Agentic Operations
* Agentic Value Stream
* Autonomous Service
* Autonomous Enterprise
;;;
2. Scope

In scope

* Agentic Service concept
* Service specialization
* agentic service-realization semantics
* service-context semantics
* delegated intent
* bounded authority
* contextual interpretation
* action selection
* service coordination
* adaptation
* escalation
* registry
* profile
* relationship integration
* WSF correspondence mapping
* OpenDEA correspondence mapping
* documentation
* architecture boundaries
* visualizations
* OTCHERE Inc example
* conformance tests
* negative semantic tests
* schema validation
* relationship validation
* provenance
* CI
* v1.3.0 release preparation

Out of scope

* Autonomous Service
* Agentic Product
* Autonomous Product
* AI Service
* AI-native Service
* service autonomy maturity
* service autonomy levels
* modifications to WSF
* modifications to OpenDEA metamodel
* new foundational Service ontology
* new Agent ontology
;;;
3. Canonical Concept

Create:

enterprise-semantics/concepts/agentic-service.yaml

Definition:

An Agentic Service is a Service whose delivery or interaction materially incorporates agentic behavior in interpreting intent, selecting or coordinating actions, adapting service behavior, or executing service responses toward an intended outcome within defined authority, policy, and contextual boundaries.

Semantic type:

semantic_type: AgenticService

Specialization:

specializes:
  - Service
;;;
4. Required Properties

The schema shall support:

properties:
  service_intent
  agentic_scope
  service_context
  delegated_intent
  authority_context
  decision_boundary
  action_selection_scope
  coordination_scope
  adaptation_scope
  intervention_model
  escalation_boundary
  policy_context
  constraint_context
  realization_mode

These properties describe the agentic realization of the Service, not a replacement for the underlying Service semantics.
;;;
5. Registry

Add:

AGENTIC_SERVICE

to the canonical concept registry.

Registry entry:

id: AGENTIC_SERVICE
name: Agentic Service
semantic_type: AgenticService
specializes:
  - SERVICE
status: Candidate
;;;
6. Profile

Create:

ES:PROFILE:AGENTIC_SERVICE

The profile shall group the Agentic Service characteristics without implying additional ontology or inheritance.
;;;
7. Relationships

Mandatory specialization

Agentic Service
    |-- specializes -> Service

Existing service relationships

Preserve applicable Service relationships, including relationships to:

Consumer
Provider
Capability
Outcome
Value

only where those concepts and predicates are canonical.

Agentic realization

Where canonical predicates exist:

Agentic Service
    +-- engages -> Agent
    +-- interprets -> Intent
    +-- operates-within -> Authority
    +-- governed-by -> Policy
    +-- constrained-by -> Constraint
    +-- uses -> Agentic Workflow
    +-- produces -> Outcome
    +-- adapts-to -> Context
    |-- supports -> Capability

Do not introduce missing foundational concepts solely to satisfy these relationships.
;;;
8. Materiality Rule

The implementation must encode a materiality requirement.

The following shall not, by themselves, qualify a Service as Agentic:

uses AI
uses an Agent
uses automation
uses an API
uses machine learning
uses a conversational interface
uses an autonomous system

The service must demonstrate material agentic behavior in its realization.

At least one meaningful agentic realization characteristic must be evidenced, such as:

* contextual interpretation;
* delegated-intent interpretation;
* dynamic action selection;
* agentic coordination;
* adaptive service behavior;
* contextual exception interpretation;
* bounded service decision-making.
;;;
9. Agentic / Autonomous Boundary

CR-ES-014 shall explicitly prevent:

Agentic Service -> Autonomous Service

from being interpreted as inheritance.

The following characterization remains valid:

Agentic = true
Autonomous = false

Future autonomous service semantics require a separate ADR.
;;;
10. Conformance Tests

Create:

enterprise-semantics-test-probe/conformance/agentic-service/

Positive tests

ASVC-CON-001
Agentic Service specializes Service
ASVC-CON-002
Agentic Service retains Service semantics
ASVC-CON-003
Agentic Service has material agentic realization
ASVC-CON-004
Agentic Service may interpret delegated intent
ASVC-CON-005
Agentic Service may interpret contextual conditions
ASVC-CON-006
Agentic Service may dynamically select actions
ASVC-CON-007
Agentic Service may coordinate actions
ASVC-CON-008
Agentic Service may adapt service behavior
ASVC-CON-009
Agentic Service operates within defined authority
ASVC-CON-010
Agentic Service may be governed by policy
ASVC-CON-011
Agentic Service may engage an Agent
ASVC-CON-012
Agentic Service may use Agentic Workflow
ASVC-CON-013
Human participation is permitted
ASVC-CON-014
AI is not required
ASVC-CON-015
Automation is not sufficient
ASVC-CON-016
Agentic Service remains distinct from Agentic Capability
ASVC-CON-017
Agentic Service remains distinct from Agentic Operations
ASVC-CON-018
Agentic Service remains distinct from Agentic Value Stream
ASVC-CON-019
Agentic Service retains provenance and grounding
;;;
11. Negative Tests

Create:

ASVC-NEG-001
Agentic Service is-a Agent
ASVC-NEG-002
Agentic Service is-a Agentic Capability
ASVC-NEG-003
Agentic Service is-a Agentic Workflow
ASVC-NEG-004
Agentic Service is-a Agentic Operations
ASVC-NEG-005
Agentic Service is-a Agentic Value Stream
ASVC-NEG-006
Agentic Service is-a Autonomous Service
ASVC-NEG-007
Agentic Service requires AI
ASVC-NEG-008
AI-enabled Service automatically becomes Agentic Service
ASVC-NEG-009
Automated Service automatically becomes Agentic Service
ASVC-NEG-010
A Service containing an Agent automatically becomes Agentic Service
ASVC-NEG-011
Agentic Service requires removal of humans
ASVC-NEG-012
Agentic Service implies autonomous behavior
ASVC-NEG-013
Agentic Service implies Autonomous Operations
ASVC-NEG-014
Agentic Service implies Autonomous Value Stream
ASVC-NEG-015
Agentic Service implies Autonomous Enterprise
;;;
12. Architecture Documentation

Create:

enterprise-semantics-docs/concepts/agentic-service.md

Create:

enterprise-semantics-docs/architecture/
  agentic-service-boundary.md
  service-agentic-realization-boundary.md
  agentic-service-execution-boundary.md
  agentic-service-capability-boundary.md
  agentic-service-value-stream-boundary.md
  agentic-service-operations-boundary.md
  agentic-vs-autonomous-service.md
  service-authority-escalation-boundary.md

The documentation shall explicitly distinguish:

Capability
     ->
Service
     ->
Agentic Service
     ->
Agentic Workflow
     ->
Execution

where applicable, while making clear that this is a semantic relationship architecture and not a mandatory containment hierarchy.
;;;
13. Visualizations

Create:

enterprise-semantics-visuals/concepts/
  agentic-service.puml

Create:

enterprise-semantics-visuals/architecture/
  service-agentic-realization-boundary.puml
  agentic-service-execution-boundary.puml
  agentic-service-capability-boundary.puml
  agentic-service-value-stream-boundary.puml
  agentic-service-operations-boundary.puml
  agentic-vs-autonomous-service.puml
  service-authority-escalation-boundary.puml

Required primary model

                    Service
                       |
                       | specializes
                       ->
                Agentic Service
                       |
          +------------┼------------+
          ->            ->            ->
       Intent       Authority     Context
          |            |            |
          |------------┼------------┘
                       ->
             Action Selection
                       ->
                 Execution
                       ->
                  Outcome
                       ↺
                   Adaptation
;;;
14. Example

Create:

enterprise-semantics-examples/services/
  otchere-agentic-services.yaml

The example shall contain at minimum:

Customer Resolution Service
        ->
Agentic Customer Resolution Service

and demonstrate:

* customer intent;
* contextual interpretation;
* service authority;
* action selection;
* permitted service action;
* service execution;
* outcome observation;
* adaptation;
* escalation.

The example shall explicitly show that human escalation remains possible.

A second example may demonstrate an Agentic Fulfillment Service.
;;;
15. Mappings

Create:

enterprise-semantics-mappings/wsf/agentic-service.yaml
enterprise-semantics-mappings/opendea/agentic-service.yaml

Mappings shall document semantic correspondence, specialization, realization, or implementation relationships only where justified.

No unsupported equivalence shall be asserted.

No WSF or OpenDEA implementation change is authorized by this CR.
;;;
16. Provenance

The canonical concept shall contain:

provenance:
  source:
    - ADR-ES-002
    - ADR-ES-003
    - ADR-ES-004
    - ADR-ES-005
    - ADR-ES-006
    - ADR-ES-007
    - ADR-ES-012
  decision:
    - ADR-ES-014
  implementation:
    - CR-ES-014
;;;
17. CI Requirements

CI shall validate:

1. schema validity;
2. registry integrity;
3. relationship integrity;
4. specialization integrity;
5. provenance completeness;
6. profile integrity;
7. mapping integrity;
8. conformance tests;
9. negative semantic tests;
10. agentic materiality;
11. authority-boundary integrity;
12. escalation-boundary integrity;
13. Service inheritance;
14. prohibited type inheritance;
15. AI independence;
16. automation independence;
17. autonomy independence.

The release gate must fail if an implementation encodes:

AI -> Agentic Service

or:

Automation -> Agentic Service

or:

Agent -> Agentic Service

as a necessary semantic implication.
;;;
18. Acceptance Criteria

CR-ES-014 is complete when:

* [ ]	Agentic Service is canonicalized.
* [ ]	Agentic Service specializes Service.
* [ ]	Service semantics remain intact.
* [ ]	Material agentic realization is explicitly modeled.
* [ ]	Service intent is represented.
* [ ]	Service context is represented.
* [ ]	Delegated intent is represented where applicable.
* [ ]	Authority boundary is represented.
* [ ]	Decision boundary is represented.
* [ ]	Action selection is represented.
* [ ]	Adaptation is represented.
* [ ]	Intervention model is represented.
* [ ]	Escalation boundary is represented.
* [ ]	Agent integration is represented.
* [ ]	Agentic Workflow integration is represented where canonical.
* [ ]	Agentic Capability distinction is documented.
* [ ]	Agentic Operations distinction is documented.
* [ ]	Agentic Value Stream distinction is documented.
* [ ]	Autonomous Service is not established.
* [ ]	AI is not required.
* [ ]	Automation is not sufficient.
* [ ]	Human participation remains valid.
* [ ]	OTCHERE Inc examples are provided.
* [ ]	WSF mapping is provided.
* [ ]	OpenDEA mapping is provided.
* [ ]	Documentation is complete.
* [ ]	Architecture boundaries are documented.
* [ ]	PlantUML diagrams are complete.
* [ ]	Positive conformance tests pass.
* [ ]	Negative tests pass.
* [ ]	Provenance is complete.
* [ ]	CI passes.
* [ ]	No unauthorized foundational concepts are introduced.
* [ ]	v1.3.0 release gate passes.
;;;
19. Governance

Implementation follows:

ADR-ES-014
      ->
CR-ES-014
      ->
PR
      ->
CI
      ->
Semantic Conformance
      ->
Enterprise-Semantics v1.3.0

CR-ES-014 authorizes only the changes explicitly defined above.

Any Autonomous Service semantics require a subsequent ADR/CR pair.

This establishes a useful next branch:

Capability ---------------- Service
    |                          |
    +-- Agentic Capability     |-- Agentic Service
    |
    |-- Autonomous Capability

The important architectural restraint is that Agentic Service is about agentic realization of a service, not about making the service autonomous. That keeps the same orthogonality established for Capability, Operations, Value Stream, and Enterprise.


<!--
Authored by: Emmanuel A. Otchere (cardinal author rule, 2026-09-24)
-->
