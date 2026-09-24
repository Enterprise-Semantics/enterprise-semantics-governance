CR-ES-013 , Implement Autonomous Capability

Target release:

v1.2.0

This CR is the implementation specification for ADR-ES-013. The CR does not authorise creation of Autonomous Agent, Autonomous Workflow, Autonomous Process, Autonomous Service, Autonomous Organization, Autonomous Culture, Autonomous Ecosystem, Autonomous Network, AI Capability, capability autonomy maturity levels, autonomous capability scoring, Autonomous Value Stage, or modifications to WSF or OpenDEA per ADR-ES-013 §14 explicit deferral list.

CR-ES-013 , Implementation

CR-ES-013: Implement Autonomous Capability

## Promotion Metadata

- **Status:** Accepted
- **Promotion Date:** 2026-09-24
- **Authorizing ADR:** ADR-ES-013 (Accepted 2026-09-24)
- **Implementation Target:** v1.2.0
- **Depends On:** ADR-ES-002, ADR-ES-004, ADR-ES-008, ADR-ES-009, ADR-ES-011, ADR-ES-012
- **Promotion Rationale:** All 33 acceptance criteria from CR-ES-013 §18 satisfied via 8 implementation PRs across 6 repos ; validator NO_DRIFT (22 Concept records validated) ; v1.2.0 Autonomous Capability release pointer established ; 2x2 matrix at capability boundary structurally complete (Conventional, Agentic, Autonomous, Agentic+Autonomous-as-composition) ; orthogonal dimensions preserved per ACAP-AUTO-CON-015 ; bounded autonomy enforced per ACAP-AUTO-CON-007..009 ; forbidden inheritance blocked per ACAP-AUTO-NEG-001..006 ; AI/automation independence verified per ACAP-AUTO-CON-013..014 ; per user directive message 1552724263121981440, "followup with appropriate implementation"

1. Objective

Implement Autonomous Capability as a canonical Enterprise-Semantics specialization of Capability.

The implementation shall establish capability-level autonomy while preserving the semantic independence of:

* Agentic Capability
* Autonomous Capability
* Agentic Operations
* Autonomous Operations
* Agentic Value Stream
* Autonomous Value Stream
* Agentic Enterprise
* Autonomous Enterprise

No new foundational ontology shall be introduced beyond the scope authorized by ADR-ES-013.
;;;
2. Scope

In scope

1. Autonomous Capability canonical concept
2. Capability specialization
3. Autonomous realization semantics
4. autonomy properties
5. authority and governance boundaries
6. capability-level autonomy relationships
7. registry integration
8. profile integration
9. WSF correspondence mapping
10. OpenDEA correspondence mapping
11. documentation
12. architectural boundary documentation
13. PlantUML visualizations
14. OTCHERE Inc example
15. positive conformance tests
16. negative semantic tests
17. schema validation
18. relationship validation
19. autonomy-integrity validation
20. provenance
21. CI integration
22. v1.2.0 release preparation

Out of scope

* Autonomous Agent
* Autonomous Workflow
* Autonomous Process
* Autonomous Service
* Autonomous Organization
* Autonomous Culture
* Autonomous Ecosystem
* Autonomous Network
* AI Capability
* capability autonomy maturity levels
* autonomous capability scoring
* Autonomous Value Stage
* changes to WSF
* changes to OpenDEA metamodel
* new autonomy ontology
* new AI ontology
;;;
3. Canonical Concept

Create:

enterprise-semantics/concepts/autonomous-capability.yaml

Canonical definition:

An Autonomous Capability is a Capability whose realization is capable of progressing through decisions, actions, coordination, and adaptation within defined objectives, authority, policies, constraints, and governance boundaries without requiring human intervention for every capability decision or action.

Semantic type:

semantic_type: AutonomousCapability

Specialization:

specializes:
  - Capability
;;;
4. Required Properties

The schema shall support, at minimum:

properties:
  objective
  autonomy_scope
  realization_context
  decision_scope
  action_scope
  coordination_scope
  authority_context
  policy_context
  constraint_context
  governance_context
  adaptation_scope
  intervention_model
  escalation_boundary
  observation_scope
  realization_mode

Property intent

Property	Purpose
objective	Defines what autonomous realization is intended to achieve
autonomy_scope	Defines where autonomy applies
realization_context	Defines the context in which capability realization occurs
decision_scope	Defines decisions that may progress independently
action_scope	Defines actions that may progress independently
coordination_scope	Defines coordination that may occur independently
authority_context	Defines permitted authority
policy_context	Defines applicable policies
constraint_context	Defines limiting conditions
governance_context	Defines governance boundaries
adaptation_scope	Defines where adaptation is permitted
intervention_model	Defines human intervention semantics
escalation_boundary	Defines when control must transfer
observation_scope	Defines what realization observes
realization_mode	Defines conventional, automated, agentic, autonomous, or combined realization characteristics
;;;
5. Registry

Add:

AUTONOMOUS_CAPABILITY

to the canonical concept registry.

The registry entry shall identify:

id: AUTONOMOUS_CAPABILITY
name: Autonomous Capability
semantic_type: AutonomousCapability
specializes:
  - CAPABILITY
status: Candidate

The final status shall follow the Enterprise-Semantics publication lifecycle.
;;;
6. Profile

Create:

ES:PROFILE:AUTONOMOUS_CAPABILITY

The profile shall include the Autonomous Capability semantic characteristics without implying ontology inheritance beyond the canonical specialization.
;;;
7. Relationships

Implement only relationships supported by existing canonical concepts and predicates.

Required

Autonomous Capability
    +-- specializes -> Capability
    |-- enables -> Outcome

Capability inheritance

Autonomous Capability
    +-- exercised-by -> Role
    +-- supported-by -> Resource
    +-- delivered-through -> Service
    |-- implemented-by -> System

Autonomous realization

Where canonical targets exist:

Autonomous Capability
    +-- operates-within -> Authority
    +-- governed-by -> Policy
    +-- constrained-by -> Constraint
    +-- pursues -> Objective
    +-- responds-to -> Context
    +-- adapts-to -> Context
    +-- produces -> Outcome
    +-- realized-through -> Workflow
    +-- supported-by -> Autonomous Operations
    |-- enables -> Autonomous Value Stream

Do not create missing concepts merely to satisfy these relationships.
;;;
8. Agentic / Autonomous Integrity

The implementation must explicitly preserve:

Agentic ≠ Autonomous

and permit:

Agentic = false
Autonomous = true

and:

Agentic = true
Autonomous = false

and:

Agentic = true
Autonomous = true

The final state is a combined semantic characterization rather than a new concept.
;;;
9. Conformance Tests

Create:

enterprise-semantics-test-probe/conformance/autonomous-capability/

Positive tests

ACAP-AUTO-CON-001
Autonomous Capability specializes Capability
ACAP-AUTO-CON-002
Autonomous Capability retains enduring-ability semantics
ACAP-AUTO-CON-003
Autonomous Capability is outcome-oriented
ACAP-AUTO-CON-004
Autonomous Capability has defined autonomy scope
ACAP-AUTO-CON-005
Autonomous Capability has defined decision scope
ACAP-AUTO-CON-006
Autonomous Capability has defined action scope
ACAP-AUTO-CON-007
Autonomous Capability operates within authority
ACAP-AUTO-CON-008
Autonomous Capability is governed by policy
ACAP-AUTO-CON-009
Autonomous Capability is bounded by constraints
ACAP-AUTO-CON-010
Autonomous Capability may adapt within defined scope
ACAP-AUTO-CON-011
Autonomous Capability may retain human intervention
ACAP-AUTO-CON-012
Autonomous Capability supports escalation
ACAP-AUTO-CON-013
Autonomous Capability does not require AI
ACAP-AUTO-CON-014
Autonomous Capability does not require automation
ACAP-AUTO-CON-015
Autonomous Capability may coexist with Agentic behavior
ACAP-AUTO-CON-016
Autonomous Capability may support Autonomous Value Stream realization
ACAP-AUTO-CON-017
Autonomous Capability may be supported by Autonomous Operations
ACAP-AUTO-CON-018
Autonomous Capability retains provenance and grounding
;;;
10. Negative Tests

Create at minimum:

ACAP-AUTO-NEG-001
Autonomous Capability is-a Agentic Capability
ACAP-AUTO-NEG-002
Agentic Capability is-a Autonomous Capability
ACAP-AUTO-NEG-003
Autonomous Capability is-a Agent
ACAP-AUTO-NEG-004
Autonomous Capability is-a Autonomous Operations
ACAP-AUTO-NEG-005
Autonomous Capability is-a Autonomous Value Stream
ACAP-AUTO-NEG-006
Autonomous Capability is-a Autonomous Enterprise
ACAP-AUTO-NEG-007
Autonomous Capability requires AI
ACAP-AUTO-NEG-008
AI-enabled Capability automatically becomes Autonomous Capability
ACAP-AUTO-NEG-009
Automated Capability automatically becomes Autonomous Capability
ACAP-AUTO-NEG-010
Autonomous Capability requires elimination of humans
ACAP-AUTO-NEG-011
Autonomous Capability implies unlimited authority
ACAP-AUTO-NEG-012
Autonomous Operations automatically make every supported Capability autonomous
ACAP-AUTO-NEG-013
Autonomous Value Stream automatically makes every enabling Capability autonomous
ACAP-AUTO-NEG-014
Autonomous Capability implies Agentic Capability
;;;
11. Semantic Integrity Tests

The test probe shall verify:

Capability
  ->
Autonomous Capability

without allowing:

Autonomous Capability
  ->
Agentic Capability

or:

Autonomous Capability
  ->
Autonomous Operations

or:

Autonomous Capability
  ->
Autonomous Enterprise

as type inheritance.

It shall additionally verify:

Agentic = independent dimension
Autonomous = independent dimension
;;;
12. Documentation

Create:

enterprise-semantics-docs/concepts/autonomous-capability.md

Create architecture documents:

enterprise-semantics-docs/architecture/
  autonomous-capability-boundary.md
  capability-autonomous-realization-boundary.md
  autonomous-capability-execution-boundary.md
  autonomous-capability-value-stream-boundary.md
  autonomous-capability-enterprise-boundary.md
  agentic-vs-autonomous-capability.md
  capability-autonomy-authority-boundary.md

Documentation must explicitly explain:

* Capability versus Autonomous Capability
* Agentic versus Autonomous Capability
* autonomy versus automation
* autonomy versus AI
* capability versus operations
* capability versus value stream
* capability versus enterprise
* human intervention and escalation
* authority and governance boundaries
;;;
13. Visualizations

Create:

enterprise-semantics-visuals/
  concepts/
    autonomous-capability.puml
  relationships/
    autonomous-capability-relationships.puml
  architecture/
    capability-autonomous-realization-boundary.puml
    autonomous-capability-execution-boundary.puml
    autonomous-capability-value-stream-boundary.puml
    autonomous-capability-enterprise-boundary.puml
    agentic-vs-autonomous-capability.puml
    capability-autonomy-authority-boundary.puml

Primary conceptual visualization

Capability
     |
     +---------------+
     |               |
Agentic          Autonomous
Capability       Capability
     |               |
     |-------┬-------┘
             |
   Agentic + Autonomous
        realization

The diagram must not imply that Agentic Capability inherits Autonomous Capability or vice versa.
;;;
14. Example

Create:

enterprise-semantics-examples/capabilities/
  otchere-autonomous-capabilities.yaml

The example shall model at least:

Customer Resolution Capability

Customer Resolution Capability
        ->
Autonomous Customer Resolution Capability

with:

* objective
* autonomy scope
* decision scope
* action scope
* authority
* policy
* constraints
* intervention model
* escalation boundary
* outcome

Fulfillment Coordination Capability

Fulfillment Coordination Capability
        ->
Autonomous Fulfillment Coordination Capability

The example shall demonstrate that autonomous capability does not require removal of human intervention.
;;;
15. Mappings

Create:

enterprise-semantics-mappings/wsf/autonomous-capability.yaml
enterprise-semantics-mappings/opendea/autonomous-capability.yaml

Mappings shall document semantic correspondence only.

They shall not modify:

* WSF
* OpenDEA
* OpenDEA metamodel
* external catalogs

unless independently authorized.

Mapping types may include:

specialization
correspondence
implementation
realization

as justified by evidence.

No unsupported equivalence shall be asserted.
;;;
16. Provenance

The canonical concept shall include:

provenance:
  source:
    - ADR-ES-002
    - ADR-ES-004
    - ADR-ES-008
    - ADR-ES-009
    - ADR-ES-011
    - ADR-ES-012
  decision:
    - ADR-ES-013
  implementation:
    - CR-ES-013
;;;
17. CI Requirements

CI shall validate:

1. YAML/schema validity
2. concept registry integrity
3. relationship vocabulary integrity
4. specialization integrity
5. provenance completeness
6. profile integrity
7. mapping integrity
8. conformance tests
9. negative semantic tests
10. Agentic/Autonomous orthogonality
11. authority boundary integrity
12. autonomy scope integrity
13. forbidden inheritance
14. forbidden technology implications
15. unauthorized concept detection

The release gate must fail if:

Autonomous Capability -> Agentic Capability

is inferred as mandatory inheritance.

It must also fail if:

Autonomous Capability -> AI

or:

Autonomous Capability -> Automation

is encoded as a necessary condition.
;;;
18. Acceptance Criteria

CR-ES-013 is complete when:

* [ ]	Autonomous Capability is canonicalized.
* [ ]	It specializes Capability.
* [ ]	Capability semantics remain unchanged.
* [ ]	Autonomous realization is explicitly defined.
* [ ]	Objective scope is represented.
* [ ]	Decision scope is represented.
* [ ]	Action scope is represented.
* [ ]	Authority is represented.
* [ ]	Policy and constraints are represented.
* [ ]	Governance boundaries are represented.
* [ ]	Adaptation is represented.
* [ ]	Intervention is represented.
* [ ]	Escalation is represented.
* [ ]	Agentic and autonomous dimensions remain independent.
* [ ]	AI is not required.
* [ ]	Automation is not sufficient.
* [ ]	Human participation remains valid.
* [ ]	Autonomous Operations integration is represented where canonical.
* [ ]	Autonomous Value Stream integration is represented where canonical.
* [ ]	Autonomous Enterprise implication is explicitly prevented.
* [ ]	Agentic Capability implication is explicitly prevented.
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
* [ ]	Release target v1.2.0 is satisfied.
;;;
19. Release

Upon successful implementation and governance approval:

Enterprise-Semantics v1.2.0

shall publish Autonomous Capability as a canonical semantic specialization.

The release shall preserve all preceding semantic contracts from:

v0.2.0  Value Stream
v0.3.0  Agentic
v0.4.0  Agentic Value Stream
v0.5.0  Agentic Workflow
v0.6.0  Agentic Operations
v0.7.0  Autonomous Operations
v0.8.0  Autonomous Value Stream
v1.0.0  Autonomous Enterprise
v1.1.0  Agentic Capability
v1.2.0  Autonomous Capability
;;;
20. Governance

Implementation authority:

ADR-ES-013
      ->
CR-ES-013
      ->
PR
      ->
CI
      ->
Semantic Conformance
      ->
Enterprise-Semantics v1.2.0

No implementation outside the stated scope is authorized by this CR.


<!--
Authored by: Emmanuel A. Otchere (cardinal author rule, 2026-09-24)
-->
