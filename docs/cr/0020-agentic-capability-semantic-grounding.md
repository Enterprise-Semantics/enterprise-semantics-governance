CR-ES-012 , Implement Agentic Capability Semantic Grounding

Target release:

v1.1.0

This CR is the implementation specification for ADR-ES-012. The CR does not authorise creation of Autonomous Capability, AI Capability, Agentic Capability maturity levels, Agentic Capability scoring, Agentic Organization, Autonomous Organization, Agentic Culture, Autonomous Culture, Agentic Ecosystem, Autonomous Ecosystem, or modifications to WSF or OpenDEA per ADR-ES-012 §25 explicit deferral list.

CR-ES-012 , Implementation

CR-ES-012: Implement Agentic Capability Semantic Grounding

1. Change Objective

Implement the governed semantic grounding of Agentic Capability established by ADR-ES-012.

The implementation shall extend the canonical Capability semantic model with an agentic realization specialization while preserving Capability as the universal foundational concept.
;;;
2. Canonical Concept

Create:

enterprise-semantics/concepts/agentic-capability.yaml

Canonical definition:

An Agentic Capability is a Capability whose realization materially incorporates agentic behavior in achieving or enabling an intended Outcome within defined authority, policy, and contextual boundaries.

Semantic type:

semantic_type: AgenticCapability
specializes: Capability
;;;
3. Schema Requirements

The schema shall inherit the semantic properties of Capability and additionally support:

agentic_scope:
realization_context:
delegated_intent:
authority_context:
decision_boundary:
action_selection_scope:
adaptation_scope:
intervention_model:
escalation_boundary:
realization_mode:

The implementation must not duplicate the foundational Capability definition where inheritance/reference is supported by the repository schema architecture.
;;;
4. Required Relationships

Support:

Agentic Capability
    -> specializes -> Capability
Agentic Capability
    -> enables -> Outcome
Agentic Capability
    -> realized-through -> Agentic Workflow
Agentic Capability
    -> supported-by -> Agentic Operations
Agentic Capability
    -> engages -> Agent
Agentic Capability
    -> exercised-by -> Role
Agentic Capability
    -> supported-by -> Resource
Agentic Capability
    -> delivered-through -> Service
Agentic Capability
    -> implemented-by -> System
Agentic Capability
    -> enables -> Agentic Value Stream

Existing Capability relationships shall be reused rather than duplicated.

Only relationships whose predicates and target concepts are canonical shall be activated in the canonical model.
;;;
5. Registry

Add:

AGENTIC_CAPABILITY

to the canonical registry.

Registry metadata shall include:

id:
name: Agentic Capability
semantic_type: AgenticCapability
status:
definition:
specializes: Capability
relationships:
grounding:
provenance:
version:
;;;
6. Profile

Create:

enterprise-semantics/concepts/profiles/agentic-capability.yaml

Profile identifier:

ES:PROFILE:AGENTIC_CAPABILITY

Scope:

scope:
  - Capability
  - Agentic Capability
  - Agent
  - Agentic Workflow
  - Agentic Operations
  - Agentic Value Stream
  - Outcome
  - Intent
  - Authority

Profile membership must not create inheritance.
;;;
7. Capability Inheritance Integrity

CI shall verify:

Agentic Capability
        ->
specializes
        ->
Capability

and reject:

Capability
        ->
requires
        ->
Agentic

as a universal condition.

Not every Capability is Agentic.
;;;
8. Material Agentic Realization Test

The implementation shall include a qualification rule:

Capability
+
Material Agentic Realization
=
Agentic Capability

The following alone must not qualify:

Capability + AI
Capability + Automation
Capability + Agent
Capability + System

unless the implementation demonstrates material agentic realization.
;;;
9. Agentic Realization Evidence

A conforming Agentic Capability instance shall be able to identify applicable evidence from:

Delegated Intent
Contextual Interpretation
Action Selection
Agentic Coordination
Adaptation
Bounded Authority
Outcome Orientation

Not every property needs to be independently present where the established Agentic semantics permit a different realization pattern, but the instance must demonstrate material agentic behavior.
;;;
10. Agent Relationship

Validate:

Agentic Capability
        ->
engages
        ->
Agent

The following inference must fail:

Agent
        ->
is-a
        ->
Capability

and:

Agent
        ->
is-a
        ->
Agentic Capability
;;;
11. Workflow Relationship

Validate:

Agentic Capability
        ->
realized-through
        ->
Agentic Workflow

The model must preserve:

Capability ≠ Workflow
Agentic Capability ≠ Agentic Workflow
;;;
12. Operations Relationship

Validate:

Agentic Capability
        ->
supported-by / realized-through
        ->
Agentic Operations

where the relationship vocabulary permits.

Reject:

Agentic Operations
        ->
is-a
        ->
Agentic Capability
;;;
13. Value Stream Relationship

Validate:

Agentic Capability
        ->
enables
        ->
Agentic Value Stream

Reject:

Agentic Value Stream
        ->
is-a
        ->
Agentic Capability

The implementation must preserve the semantic distinction:

Capability -> ability
Value Stream -> value realization
;;;
14. Enterprise Relationship

Validate:

Agentic Enterprise
        ->
possesses
        ->
Agentic Capability

where the canonical Entity/Enterprise capability relationship permits.

Reject:

Agentic Capability
        ->
is-a
        ->
Agentic Enterprise

A single Agentic Capability does not establish Agentic Enterprise.
;;;
15. AI Integrity

CI shall reject:

Agentic Capability requires AI
AI Capability automatically becomes Agentic Capability
AI-enabled Capability automatically becomes Agentic Capability

The implementation shall not introduce AI as a dependency.
;;;
16. Automation Integrity

CI shall reject:

Automation establishes Agentic Capability
Automated Capability automatically becomes Agentic Capability

Automation may support an Agentic Capability but is not its semantic definition.
;;;
17. Autonomy Integrity

Do not create:

Autonomous Capability

in this CR.

The implementation must explicitly validate:

Agentic Capability
        ≠
Autonomous Capability

and:

Agentic Capability
        ⇏
Autonomous Capability

Future Autonomous Capability semantics require a separate ADR.
;;;
18. Human Participation

Agentic Capability may include:

Human
Agent
Human + Agent
Human + System
Agent + System
Human + Agent + System

Human intervention does not invalidate Agentic Capability.

The implementation must reject:

Agentic Capability requires human elimination
;;;
19. Capability Transformation Example

Create:

enterprise-semantics-examples/capabilities/
    otchere-agentic-capabilities.yaml

The example shall use OTCHERE Inc and demonstrate at least:

Customer Resolution Capability
        ->
Agentic Customer Resolution Capability

and:

Fulfillment Coordination Capability
        ->
Agentic Fulfillment Coordination Capability

Each example shall identify:

* capability definition
* intended outcome
* agentic scope
* realization context
* delegated intent
* authority
* decision boundary
* action scope
* intervention model
* escalation boundary
* realization mechanism

The example must demonstrate that not all capabilities are agentic.
;;;
20. Documentation

Create:

enterprise-semantics-docs/concepts/agentic-capability.md

Required sections:

1. Definition
2. Capability grounding
3. Agentic specialization
4. Materiality requirement
5. Capability boundary
6. Agent boundary
7. Workflow boundary
8. Operations boundary
9. Value Stream boundary
10. Enterprise boundary
11. AI boundary
12. Automation boundary
13. Autonomy boundary
14. Human participation
15. Example
16. Conformance
17. Deferred concepts
;;;
21. Architecture Documentation

Create:

enterprise-semantics-docs/architecture/
    capability-agentic-realization-boundary.md
    agentic-capability-execution-boundary.md
    agentic-capability-value-stream-boundary.md
    agentic-capability-enterprise-boundary.md

The primary architecture model shall be:

CAPABILITY
"What enduring ability exists?"
        |
        v
AGENTIC CAPABILITY
"Is realization materially agentic?"
        |
        +--------------+
        v              v
Agentic Workflow   Agentic Operations
        |              |
        |------┬-------┘
               v
             Agent
               |
               v
            Outcome
;;;
22. Visual Assets

Create:

enterprise-semantics-visuals/
    concepts/
        agentic-capability.puml
    architecture/
        capability-agentic-realization-boundary.puml
        agentic-capability-execution-boundary.puml
        agentic-capability-value-stream-boundary.puml
        agentic-capability-enterprise-boundary.puml
        capability-vs-agentic-capability.puml
;;;
23. Conformance Tests

Create:

enterprise-semantics-test-probe/
    conformance/
        agentic-capability/

Implement:

ACAP-CON-001
ACAP-CON-002
ACAP-CON-003
ACAP-CON-004
ACAP-CON-005
ACAP-CON-006
ACAP-CON-007
ACAP-CON-008
ACAP-CON-009
ACAP-CON-010
ACAP-CON-011
ACAP-CON-012
ACAP-CON-013
ACAP-CON-014
ACAP-CON-015
ACAP-CON-016
ACAP-CON-017
ACAP-CON-018
;;;
24. Negative Tests

The following must fail:

ACAP-NEG-001

Agentic Capability is-a Agent

ACAP-NEG-002

Agent is-a Agentic Capability

ACAP-NEG-003

Agentic Capability is-a Agentic Workflow

ACAP-NEG-004

Agentic Workflow is-a Agentic Capability

ACAP-NEG-005

Agentic Capability is-a Agentic Operations

ACAP-NEG-006

Agentic Operations is-a Agentic Capability

ACAP-NEG-007

Agentic Capability is-a Agentic Value Stream

ACAP-NEG-008

Agentic Value Stream is-a Agentic Capability

ACAP-NEG-009

Agentic Capability requires AI

ACAP-NEG-010

AI automatically establishes Agentic Capability

ACAP-NEG-011

Automation automatically establishes Agentic Capability

ACAP-NEG-012

Agentic Capability automatically implies Autonomous Capability

ACAP-NEG-013

Agentic Capability automatically establishes Agentic Enterprise

ACAP-NEG-014

Agentic Capability requires removal of humans
;;;
25. WSF Mapping

Create:

enterprise-semantics-mappings/wsf/agentic-capability.yaml

The mapping shall identify:

* Capability correspondence
* Agentic specialization
* capability realization semantics
* relationship correspondence
* provenance
* unresolved foundational dependencies

No WSF modification is authorized.
;;;
26. OpenDEA Mapping

Create:

enterprise-semantics-mappings/opendea/agentic-capability.yaml

The mapping shall document intended correspondence with OpenDEA Capability semantics.

No OpenDEA metamodel modification is authorized.

The mapping shall explicitly distinguish:

Capability
Agentic Capability
Business Capability
Technical/Operational realization

without prematurely creating OpenDEA specializations.
;;;
27. Relationship Integrity

CI shall verify the semantic distinction:

Capability
        ->
enables
        ->
Outcome

while Agentic Capability additionally supports:

Agentic Capability
        ->
realization through
        ->
Agentic mechanisms

The implementation must not replace the foundational Capability -> Outcome semantics.
;;;
28. Provenance

The concept shall include:

provenance:
  source:
    - ADR-ES-002
    - ADR-ES-004
    - ADR-ES-012
  decision:
    - ADR-ES-012
  implementation:
    - CR-ES-012

Any external source introduced during implementation must use the established provenance classification.
;;;
29. Versioning

Target:

v1.1.0

The release shall include:

ADR-ES-012
CR-ES-012
Agentic Capability canonical concept
Capability relationship integration
Agentic realization semantics
WSF mapping
OpenDEA mapping
Documentation
Architecture models
Visuals
Examples
Conformance tests
Negative tests
CI validation
;;;
30. Scope Restrictions

CR-ES-012 does not authorize:

* Autonomous Capability
* AI Capability
* Agentic Capability maturity levels
* Agentic Capability scoring
* Agentic Organization
* Autonomous Organization
* Agentic Culture
* Autonomous Culture
* Agentic Ecosystem
* Autonomous Ecosystem
* modifications to WSF
* modifications to OpenDEA

Each requires separate governance.
;;;
31. Acceptance Criteria

CR-ES-012 is complete when:

1. Agentic Capability exists as a canonical concept.
2. It explicitly specializes Capability.
3. The foundational Capability definition remains intact.
4. Material agentic realization is required.
5. Outcome orientation is retained.
6. Agent relationships are valid.
7. Agentic Workflow relationships are valid.
8. Agentic Operations relationships are valid.
9. Agentic Value Stream relationships are valid.
10. Agentic Enterprise integration is valid.
11. AI is not required.
12. Automation is not sufficient.
13. Autonomy is not implied.
14. Human participation remains valid.
15. OTCHERE Inc examples pass.
16. Positive conformance tests pass.
17. Negative conformance tests pass.
18. WSF mapping exists without WSF modification.
19. OpenDEA mapping exists without OpenDEA modification.
20. Documentation is complete.
21. Architecture diagrams are complete.
22. Visual assets are complete.
23. Provenance is complete.
24. CI validates Capability/Agentic boundaries.
25. No unauthorized foundational concepts are introduced.
26. Release metadata identifies v1.1.0.
;;;
32. Architectural Outcome

CR-ES-012 establishes the missing capability-level bridge:

                         ENTERPRISE
                             |
                  Agentic Enterprise
                             |
                             v
                      Agentic Capability
                             |
                +------------┼------------+
                |            |            |
                v            v            v
        Agentic Value   Agentic Ops   Agentic Workflow
           Stream            |            |
                |            |-----┬------┘
                |                  v
                |--------------- Agent
                                  |
                                  v
                               Outcome

The semantic architecture now spans:

Capability
    ->
Agentic Capability
    ->
Agentic realization
    ->
Agentic Workflow / Operations
    ->
Agentic Value Realization
    ->
Agentic Enterprise

while maintaining the independent dimensions of:

Agentic
Autonomous
AI
Automation

The governing implementation principle is:

Agentic Capability is a specialization of Capability based on the material mode of capability realization; it does not redefine what a Capability is, and it does not collapse Capability, Agent, Workflow, Operations, Value Stream, Enterprise, AI, automation, or autonomy into a single semantic construct.

This gives the semantic stack a much stronger architectural shape: Capability -> Agentic Capability -> Agentic realization -> Value/Operations/Enterprise boundaries. The next ADR can then address the corresponding Autonomous Capability question, but it should be treated as a separate semantic decision rather than automatically inferred from this one.

<!--
Authored by: Emmanuel A. Otchere (cardinal author rule, 2026-09-24)
-->
