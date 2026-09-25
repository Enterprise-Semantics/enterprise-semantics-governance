CR-ES-015 , Implement Autonomous Service

Target release:

v1.4.0

This CR is the implementation specification for ADR-ES-015. The CR does not authorise creation of Agentic Service changes beyond compatibility, Autonomous Product, Agentic Product, Autonomous Service maturity levels, Service autonomy scoring, Autonomous Agent, Autonomous Workflow, Autonomous Process, Autonomous Organization, Autonomous Culture, Autonomous Ecosystem, AI Service, or modifications to WSF or OpenDEA per ADR-ES-015 §19 explicit deferral list.

CR-ES-015 , Implementation

CR-ES-015: Implement Autonomous Service

1. Objective

Implement Autonomous Service as a canonical Enterprise-Semantics specialization of Service.

The implementation shall establish service-level autonomy while preserving strict semantic separation from:

* Agentic Service;
* Autonomous Capability;
* Autonomous Operations;
* Autonomous Value Stream;
* Autonomous Enterprise;
* Agentic Workflow;
* Agent;
* AI;
* automation.
;;;
2. Scope

In scope

1. Autonomous Service concept
2. Service specialization
3. autonomous service-realization semantics
4. service objective
5. autonomy scope
6. decision scope
7. action scope
8. coordination scope
9. authority boundary
10. policy boundary
11. constraint boundary
12. governance boundary
13. adaptation
14. intervention
15. escalation
16. observation
17. registry
18. profile
19. relationship integration
20. WSF correspondence mapping
21. OpenDEA correspondence mapping
22. documentation
23. architecture boundaries
24. PlantUML visualizations
25. OTCHERE Inc examples
26. positive conformance tests
27. negative semantic tests
28. autonomy-integrity validation
29. provenance
30. CI integration
31. v1.4.0 release preparation

Out of scope

* Agentic Service changes beyond compatibility;
* Autonomous Product;
* Agentic Product;
* Autonomous Service maturity levels;
* Service autonomy scoring;
* Autonomous Agent;
* Autonomous Workflow;
* Autonomous Process;
* Autonomous Organization;
* Autonomous Culture;
* Autonomous Ecosystem;
* AI Service;
* changes to WSF;
* changes to OpenDEA metamodel;
* new foundational autonomy ontology.
;;;
3. Canonical Concept

Create:

enterprise-semantics/concepts/autonomous-service.yaml

Canonical definition:

An Autonomous Service is a Service whose delivery or interaction is capable of progressing through decisions, actions, coordination, and adaptation within defined service objectives, authority, policies, constraints, and governance boundaries without requiring human intervention for every service decision or action.

Semantic type:

semantic_type: AutonomousService

Specialization:

specializes:
  - Service
;;;
4. Required Properties

The schema shall support:

properties:
  service_objective
  autonomy_scope
  service_context
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
service_objective	Defines the service result toward which autonomous progression is directed
autonomy_scope	Defines where autonomy applies
service_context	Defines conditions relevant to service realization
decision_scope	Defines decisions permitted to progress independently
action_scope	Defines independently executable actions
coordination_scope	Defines independently coordinated service activity
authority_context	Defines permitted authority
policy_context	Defines applicable policy
constraint_context	Defines limiting conditions
governance_context	Defines governance boundaries
adaptation_scope	Defines where autonomous adaptation is permitted
intervention_model	Defines human intervention
escalation_boundary	Defines when control transfers
observation_scope	Defines what the service observes
realization_mode	Characterizes conventional, automated, agentic, autonomous, or combined realization
;;;
5. Registry

Add:

AUTONOMOUS_SERVICE

to the canonical concept registry.

Registry entry:

id: AUTONOMOUS_SERVICE
name: Autonomous Service
semantic_type: AutonomousService
specializes:
  - SERVICE
status: Candidate
;;;
6. Profile

Create:

ES:PROFILE:AUTONOMOUS_SERVICE

The profile shall group autonomous-service characteristics without implying additional ontology or inheritance.
;;;
7. Relationships

Mandatory

Autonomous Service
    |-- specializes -> Service

Service relationships

Preserve applicable Service relationships to:

Provider
Consumer
Capability
Outcome
Value

only where canonical predicates already exist.

Autonomous realization

Where canonical predicates and targets exist:

Autonomous Service
    +-- operates-within -> Authority
    +-- governed-by -> Policy
    +-- constrained-by -> Constraint
    +-- pursues -> Objective
    +-- responds-to -> Context
    +-- produces -> Outcome
    +-- adapts-to -> Context
    +-- uses -> Workflow
    +-- uses -> Agentic Workflow
    +-- supported-by -> Autonomous Operations
    |-- supports -> Capability

No missing foundational concept shall be created solely to satisfy a relationship.
;;;
8. Autonomy Materiality Rule

A Service qualifies as Autonomous Service only when autonomous progression is material to service realization.

The following do not independently establish autonomy:

uses AI
uses automation
uses an Agent
uses an autonomous system
runs without direct human supervision
uses machine learning
uses predefined decision rules

The implementation shall require evidence of meaningful independent progression in one or more of:

* decision execution;
* action execution;
* coordination;
* adaptation;
* exception handling;
* service progression toward objective.
;;;
9. Autonomy Integrity

The implementation shall explicitly distinguish:

Autonomous Service

from:

Agentic Service

The following must be valid:

Agentic = false
Autonomous = true

and:

Agentic = true
Autonomous = true

The second state is a combined characterization, not a new subtype.
;;;
10. Conformance Tests

Create:

enterprise-semantics-test-probe/conformance/autonomous-service/

Positive tests

ASVC-AUTO-CON-001
Autonomous Service specializes Service
ASVC-AUTO-CON-002
Autonomous Service retains Service semantics
ASVC-AUTO-CON-003
Autonomous Service has material autonomous realization
ASVC-AUTO-CON-004
Autonomous Service has defined service objective
ASVC-AUTO-CON-005
Autonomous Service has defined autonomy scope
ASVC-AUTO-CON-006
Autonomous Service has defined decision scope
ASVC-AUTO-CON-007
Autonomous Service has defined action scope
ASVC-AUTO-CON-008
Autonomous Service operates within authority
ASVC-AUTO-CON-009
Autonomous Service is bounded by policy
ASVC-AUTO-CON-010
Autonomous Service is bounded by constraints
ASVC-AUTO-CON-011
Autonomous Service is bounded by governance
ASVC-AUTO-CON-012
Autonomous Service may adapt within defined scope
ASVC-AUTO-CON-013
Autonomous Service supports escalation
ASVC-AUTO-CON-014
Human intervention remains permitted
ASVC-AUTO-CON-015
AI is not required
ASVC-AUTO-CON-016
Automation is not sufficient
ASVC-AUTO-CON-017
Autonomous Service may use Agentic Workflow
ASVC-AUTO-CON-018
Autonomous Service may be supported by Autonomous Operations
ASVC-AUTO-CON-019
Autonomous Service may participate in Autonomous Value Stream realization
ASVC-AUTO-CON-020
Autonomous Service retains provenance and grounding
;;;
11. Negative Tests

Create:

ASVC-AUTO-NEG-001
Autonomous Service is-a Agentic Service
ASVC-AUTO-NEG-002
Autonomous Service is-a Agent
ASVC-AUTO-NEG-003
Autonomous Service is-a Autonomous Capability
ASVC-AUTO-NEG-004
Autonomous Service is-a Autonomous Operations
ASVC-AUTO-NEG-005
Autonomous Service is-a Autonomous Value Stream
ASVC-AUTO-NEG-006
Autonomous Service is-a Autonomous Enterprise
ASVC-AUTO-NEG-007
Autonomous Service requires AI
ASVC-AUTO-NEG-008
AI-enabled Service automatically becomes Autonomous Service
ASVC-AUTO-NEG-009
Automated Service automatically becomes Autonomous Service
ASVC-AUTO-NEG-010
A Service containing an Agent automatically becomes Autonomous Service
ASVC-AUTO-NEG-011
Autonomous Service requires elimination of humans
ASVC-AUTO-NEG-012
Autonomous Service has unlimited authority
ASVC-AUTO-NEG-013
Autonomous Operations automatically make every Service autonomous
ASVC-AUTO-NEG-014
Autonomous Value Stream automatically makes every participating Service autonomous
ASVC-AUTO-NEG-015
Autonomous Capability automatically makes every delivered Service autonomous
ASVC-AUTO-NEG-016
Autonomous Service automatically becomes Agentic Service
;;;
12. Semantic Integrity Tests

The probe shall verify:

Service
   ->
Autonomous Service

without allowing autonomous specialization to imply:

Agentic Service
Agent
Autonomous Capability
Autonomous Operations
Autonomous Value Stream
Autonomous Enterprise

as type inheritance.

It shall also verify the orthogonal characterization:

Agentic = independent semantic dimension
Autonomous = independent semantic dimension
;;;
13. Documentation

Create:

enterprise-semantics-docs/concepts/autonomous-service.md

Create:

enterprise-semantics-docs/architecture/
  autonomous-service-boundary.md
  service-autonomous-realization-boundary.md
  autonomous-service-execution-boundary.md
  autonomous-service-capability-boundary.md
  autonomous-service-value-stream-boundary.md
  autonomous-service-operations-boundary.md
  agentic-vs-autonomous-service.md
  service-autonomy-authority-boundary.md

Documentation shall distinguish:

* Service vs Autonomous Service;
* Agentic Service vs Autonomous Service;
* Autonomous Service vs Autonomous Capability;
* Autonomous Service vs Autonomous Operations;
* Autonomous Service vs Autonomous Value Stream;
* Autonomous Service vs Autonomous Enterprise;
* autonomy vs automation;
* autonomy vs AI;
* human intervention vs autonomous progression;
* authority, policy, constraint, governance, and escalation.
;;;
14. Visualizations

Create:

enterprise-semantics-visuals/
  concepts/
    autonomous-service.puml
  relationships/
    autonomous-service-relationships.puml
  architecture/
    service-autonomous-realization-boundary.puml
    autonomous-service-execution-boundary.puml
    autonomous-service-capability-boundary.puml
    autonomous-service-value-stream-boundary.puml
    autonomous-service-operations-boundary.puml
    agentic-vs-autonomous-service.puml
    service-autonomy-authority-boundary.puml

Primary conceptual model

Service
   |
   | specializes
   ->
Autonomous Service
   |
   +---------------┬---------------┬---------------+
   ->               ->               ->               ->
Objective       Authority       Context       Service Outcome
   |               |               |               |
   |---------------┴---------------┴---------------┘
                   ->
              Decision
                   ->
           Action Selection
                   ->
              Execution
                   ->
             Observation
                   ->
              Adaptation
                   ↺

The visualization must not imply inheritance from Agentic Service or Autonomous Operations.
;;;
15. Example

Create:

enterprise-semantics-examples/services/
  otchere-autonomous-services.yaml

The primary example shall be:

Customer Resolution Service
        ->
Autonomous Customer Resolution Service

It shall contain:

* service objective;
* autonomy scope;
* service context;
* decision scope;
* action scope;
* authority;
* policy;
* constraints;
* governance;
* intervention model;
* escalation boundary;
* observation scope;
* service outcome.

The example shall demonstrate routine autonomous progression while preserving human escalation for exceptions.

A second example may represent an Autonomous Fulfillment Service.
;;;
16. Mappings

Create:

enterprise-semantics-mappings/wsf/autonomous-service.yaml
enterprise-semantics-mappings/opendea/autonomous-service.yaml

Mappings shall distinguish:

* specialization;
* correspondence;
* realization;
* implementation;

where justified.

No unsupported equivalence shall be asserted.

No WSF or OpenDEA implementation change is authorized by this CR.
;;;
17. Provenance

The canonical concept shall contain:

provenance:
  source:
    - ADR-ES-003
    - ADR-ES-004
    - ADR-ES-007
    - ADR-ES-008
    - ADR-ES-009
    - ADR-ES-011
    - ADR-ES-014
  decision:
    - ADR-ES-015
  implementation:
    - CR-ES-015
;;;
18. CI Requirements

CI shall validate:

1. YAML and schema validity;
2. concept registry integrity;
3. relationship vocabulary integrity;
4. specialization integrity;
5. provenance completeness;
6. profile integrity;
7. mapping integrity;
8. positive conformance tests;
9. negative semantic tests;
10. autonomy materiality;
11. autonomy-scope integrity;
12. authority-boundary integrity;
13. governance-boundary integrity;
14. escalation-boundary integrity;
15. Service inheritance;
16. Agentic/Autonomous orthogonality;
17. AI independence;
18. automation independence;
19. prohibited inheritance;
20. unauthorized concept detection.

The release gate shall fail if:

Autonomous Service -> Agentic Service

is encoded as mandatory inheritance.

It shall also fail if:

AI -> Autonomous Service

or:

Automation -> Autonomous Service

is encoded as a necessary semantic condition.
;;;
19. Acceptance Criteria

CR-ES-015 is complete when:

* [ ]	Autonomous Service is canonicalized.
* [ ]	It specializes Service.
* [ ]	Service semantics remain unchanged.
* [ ]	Autonomous realization is explicitly defined.
* [ ]	Service objective is represented.
* [ ]	Autonomy scope is represented.
* [ ]	Decision scope is represented.
* [ ]	Action scope is represented.
* [ ]	Coordination scope is represented.
* [ ]	Authority is represented.
* [ ]	Policy is represented.
* [ ]	Constraints are represented.
* [ ]	Governance boundaries are represented.
* [ ]	Adaptation is represented.
* [ ]	Observation is represented.
* [ ]	Intervention model is represented.
* [ ]	Escalation boundary is represented.
* [ ]	Agentic and autonomous dimensions remain independent.
* [ ]	AI is not required.
* [ ]	Automation is not sufficient.
* [ ]	Human participation remains valid.
* [ ]	Autonomous Operations integration is documented where canonical.
* [ ]	Autonomous Value Stream integration is documented where canonical.
* [ ]	Autonomous Capability distinction is documented.
* [ ]	Autonomous Enterprise implication is explicitly prevented.
* [ ]	Agentic Service implication is explicitly prevented.
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
* [ ]	v1.4.0 release gate passes.
;;;
20. Release

Upon successful implementation and governance approval:

Enterprise-Semantics v1.4.0

shall publish Autonomous Service as a canonical semantic specialization.

The release preserves the semantic progression:

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
v1.3.0  Agentic Service
v1.4.0  Autonomous Service
;;;
21. Governance

Implementation authority:

ADR-ES-015
      ->
CR-ES-015
      ->
PR
      ->
CI
      ->
Semantic Conformance
      ->
Enterprise-Semantics v1.4.0

No implementation outside the stated scope is authorized by this CR.

Any subsequent Autonomous Product, Agentic Product, or other semantic specialization requires its own ADR and CR.

This gives the Service branch the same deliberate two-dimensional structure already established for Capability:

                    Service
                       |
             +---------┴---------+
             |                   |
     Agentic Service      Autonomous Service
             |                   |
             |---------┬---------┘
                       |
          Agentic + Autonomous Service

The next architectural branch after this should therefore move to Product, rather than continuing to add more service variants.


<!--
Authored by: Emmanuel A. Otchere (cardinal author rule, 2026-09-24)
-->
