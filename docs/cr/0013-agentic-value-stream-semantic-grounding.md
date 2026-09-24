<!--
CR-ES-005 ;; Agentic Value Stream Semantic Grounding

Dash-normalized: colons (:) and semicolons (;) used consistently.
Verbatim original: 00_inbox/CR-ES-005.md (em-dashes and ellipsis dividers preserved in source).

Status: Proposed
Change Type: Foundational Semantic Specialization
Priority: P0
Target: Enterprise-Semantics
Depends On: CR-ES-001, CR-ES-002, CR-ES-003, CR-ES-004
Authorizing ADR: ADR-ES-005
Target Semantic Version: 0.4.0

Cardinal author rule applied per skill: footer-only signature preserves body numbering AND satisfies the cardinal author rule.

Authored by: Emmanuel A. Otchere (cardinal author rule, 2026-09-23)
-->

CR-ES-005: Implement Agentic Value Stream Semantic Grounding

Status: Accepted (promoted from Proposed on 2026-09-23 per user directive message 1552289869429088307, "Save it, read and understand, then proceed with all tasks needed to make way to implement it appropriately. Then implement it.")
Date: 2026-09-23
Change Type: Foundational Semantic Specialization
Priority: P0
Target: Enterprise-Semantics
Depends On: CR-ES-001, CR-ES-002, CR-ES-003, CR-ES-004
Authorizing ADR: ADR-ES-005
Target Semantic Version: 0.4.0

;;;

1. Purpose

Implement the canonical Agentic Value Stream semantic established by ADR-ES-005.

The implementation shall extend the existing Value Stream semantic without replacing it, while establishing the semantic representation of agentic participation in end-to-end value realization.

The implementation must remain:

* technology-neutral;
* agentic rather than AI-centric;
* compatible with human participation;
* distinct from automation;
* distinct from autonomy;
* distinct from Process and Workflow;
* compatible with mixed conventional, automated, human, and agentic realization.

;;;

2. Scope

2.1 In Scope

This CR establishes:

* Agentic Value Stream;
* Agentic Value Stream specialization of Value Stream;
* agentic value-stream properties;
* Agentic Value Stream relationships;
* Agentic Value Stream profile;
* Enterprise-Semantics registry entry;
* WSF semantic mapping;
* OpenDEA semantic mapping;
* conformance requirements;
* negative conformance tests;
* documentation;
* relational diagrams;
* classic-versus-agentic illustrative models;
* canonical examples;
* CI validation.

;;;

3. Out of Scope

The following shall not be canonicalized by CR-ES-005:

* Agentic Workflow;
* Agentic Operations;
* Agentic Flow;
* Autonomous Value Stream;
* Autonomous Agent;
* Autonomous Enterprise;
* Autonomous Operations;
* AI Agent as the definition of Agent;
* AI/LLM semantic models;
* vendor-specific agent frameworks;
* new WSF foundational concepts;
* OpenDEA metamodel modification;
* DEA catalog implementation.

Where these concepts are referenced, they shall be explicitly marked as future/deferred concepts.

;;;

4. Canonical Definition

Add:

An Agentic Value Stream is a Value Stream in which one or more stages are materially realized through agentic behavior, enabling delegated interpretation, action selection, coordination, adaptation, or execution toward stakeholder value realization.

Semantic type:

AgenticValueStream

Parent:

ValueStream

Relationship:

AgenticValueStream
    `---- specializes > ValueStream

;;;

5. Canonical Schema

Create:

enterprise-semantics/concepts/agentic-value-stream.yaml

Proposed structure:

id: ES:CONCEPT:AGENTIC_VALUE_STREAM
name: Agentic Value Stream
definition: >
  A Value Stream in which one or more stages are materially realized
  through agentic behavior, enabling delegated interpretation, action
  selection, coordination, adaptation, or execution toward stakeholder
  value realization.
semantic_type: AgenticValueStream
specializes:
  - ES:CONCEPT:VALUE_STREAM
properties:
  - name: agentic_scope
    type: reference_set
    required: true
    description: >
      Identifies the stages, decisions, or execution areas in which
      agentic behavior materially participates.
  - name: delegated_intent
    type: reference
    required: true
    description: >
      Identifies the intent that guides agentic participation.
  - name: authority_context
    type: reference
    required: true
    description: >
      Identifies the authority within which agentic participation occurs.
  - name: decision_boundary
    type: reference_set
    required: false
    description: >
      Identifies decisions that may be interpreted or selected
      through agentic behavior.
  - name: intervention_model
    type: enumeration
    required: false
    values:
      - human-in-loop
      - human-on-loop
      - human-over-loop
      - mixed
      - none-specified
  - name: adaptation_scope
    type: reference_set
    required: false
    description: >
      Identifies where contextual adaptation is permitted.
  - name: realization_mode
    type: enumeration
    required: false
    values:
      - mixed
      - predominantly-agentic
      - agentic-partial
      - agentic-coordinated
relationships:
  - predicate: specializes
    target: ES:CONCEPT:VALUE_STREAM
  - predicate: realizes
    target: ES:CONCEPT:STAKEHOLDER_VALUE
  - predicate: contains
    target: ES:CONCEPT:VALUE_STAGE
  - predicate: engages
    target: ES:CONCEPT:AGENT
grounding:
  foundation: WSF
  semantic_authority: Enterprise-Semantics
provenance:
  decision: ADR-ES-005
  implementation: CR-ES-005
version: 0.4.0

The exact schema syntax shall conform to the schema conventions established by CR-ES-001 rather than introducing a parallel format.

;;;

6. Registry

Extend the canonical concept registry with:

id: AGENTIC_VALUE_STREAM
name: Agentic Value Stream
type: concept
status: Candidate
definition: >
  A Value Stream in which one or more stages are materially realized
  through agentic behavior, enabling delegated interpretation,
  action selection, coordination, adaptation, or execution toward
  stakeholder value realization.

The concept shall reference:

ADR-ES-005
CR-ES-005
ES:CONCEPT:VALUE_STREAM
ES:CONCEPT:AGENT
ES:CONCEPT:INTENT
ES:CONCEPT:AUTHORITY

;;;

7. Relationship Model

Add the following canonical relationships.

Agentic Value Stream
        |
        |---- specializes > Value Stream
        |
        |---- realizes > Stakeholder Value
        |
        |---- contains > Value Stage
        |
        `---- engages > Agent

Agent semantics remain inherited from CR-ES-004:

Agent
 |---- interprets > Intent
 |---- acts-within > Authority
 |---- selects > Action
 |---- coordinates > Action
 |---- produces > Outcome
 `---- adapts-to > Context

No new agentic execution relationship shall be introduced merely to represent Agentic Workflow or Agentic Operations.

;;;

8. Value Stream Inheritance

The Agentic Value Stream schema shall preserve the mandatory Value Stream semantics established by CR-ES-003.

At minimum, the implementation shall preserve:

stakeholder
initiating_condition
realization_boundary
stages
outcomes
relationships
grounding
provenance
version

The implementation shall not duplicate or redefine these properties where inheritance/reference is supported by the repository schema architecture.

;;;

9. Agentic Scope

agentic_scope is required because an Agentic Value Stream does not necessarily operate agentically at every stage.

Examples:

agentic_scope:
  - order-validation
  - fulfillment-selection
  - exception-management

or:

agentic_scope:
  - decision: fulfillment-routing
  - decision: exception-resolution

The schema should allow the scope to reference existing Value Stages, decisions, or other governed semantic elements without creating a new Agentic Value Stage concept.

;;;

10. Authority and Intent

Every Agentic Value Stream shall provide semantic linkage between agentic participation and:

Intent
Authority

The implementation shall prevent a model in which:

Agentic Value Stream
      |
Agent
      |
Unbounded Action

The canonical semantic pattern shall instead be:

Agentic Value Stream
        |
Delegated Intent
        |
Agent
        |
Authority
        |
Action Selection
        |
Execution
        |
Outcome

;;;

11. Mixed Realization

The implementation shall explicitly permit:

Value Stage 1 > Conventional
Value Stage 2 > Automated
Value Stage 3 > Agentic
Value Stage 4 > Human
Value Stage 5 > Agentic + Human

This is an important architectural invariant.

Agentic Value Stream must not be interpreted as:

“A value stream where everything is performed by agents.”

;;;

12. Mapping, WSF

Create:

enterprise-semantics-mappings/wsf/agentic-value-stream.yaml

The mapping shall establish:

Enterprise-Semantics Agentic Value Stream
        |
specialization of
        |
WSF Value Stream

The mapping shall identify Agentic Value Stream as an Enterprise-Semantics specialization, not as a newly asserted foundational WSF concept.

Proposed mapping classification:

mapping_type: specialization
source: ES:CONCEPT:AGENTIC_VALUE_STREAM
target: WSF:CONCEPT:VALUE_STREAM

Any WSF Agent/Agency mapping shall reuse the semantic grounding established by CR-ES-004 rather than duplicating it.

;;;

13. Mapping, OpenDEA

Create:

enterprise-semantics-mappings/opendea/agentic-value-stream.yaml

The mapping shall establish:

Enterprise-Semantics
        |
        `---- Agentic Value Stream
                |
          OpenDEA specialization
                |
           Value Stream

The mapping shall not modify the OpenDEA metamodel.

If OpenDEA currently has no canonical Agentic Value Stream element, the mapping shall represent it as:

semantic specialization / target concept

rather than claiming implementation availability.

;;;

14. Profile

Create or extend:

enterprise-semantics/concepts/profiles/agentic.yaml

with:

id: ES:PROFILE:AGENTIC_VALUE_REALIZATION
name: Agentic Value Realization
scope:
  - Agent
  - Agentic
  - Intent
  - Authority
  - Action
  - Value Stream
  - Value Stage
  - Agentic Value Stream

This profile shall provide discoverability and grouping only.

It shall not imply that all listed concepts belong to one inheritance hierarchy.

;;;

15. Documentation

Create:

enterprise-semantics-docs/concepts/agentic-value-stream.md

The document shall include:

1. Definition
2. Semantic purpose
3. Value Stream inheritance
4. Agentic characteristics
5. Agentic scope
6. Authority and intent
7. Mixed realization
8. Human intervention
9. AI boundary
10. Automation boundary
11. Autonomy boundary
12. Process boundary
13. Workflow boundary
14. Examples
15. Conformance requirements
16. Provenance

;;;

16. Architecture Documentation

Add:

enterprise-semantics-docs/architecture/
  agentic-value-stream-boundary.md
  value-stream-agentic-boundary.md
  agentic-value-realization.md

These shall explain:

VALUE
Value Stream
      |
Value Stage
      |
Process
      |
Activity
      |
Task
      |
Workflow
AGENCY
Agent
      |
Intent
      |
Authority
      |
Action Selection
      |
Outcome

The two structures intersect without becoming the same model.

;;;

17. Canonical Relational Diagram

Create:

enterprise-semantics-visuals/relationships/
  agentic-value-stream.puml

The conceptual PlantUML should represent:

@startuml
class ValueStream
class AgenticValueStream
class ValueStage
class StakeholderValue
class Agent
class Intent
class Authority
class Action
class Outcome
AgenticValueStream --|> ValueStream
ValueStream "1" *-- "1..*" ValueStage
AgenticValueStream --> "1" --> StakeholderValue : realizes
AgenticValueStream --> "1..*" Agent : engages
Agent --> Intent : interprets
Agent --> Authority : acts-within
Agent --> Action : selects
Agent --> Action : coordinates
Agent --> Outcome : produces
@enduml

The actual diagram shall conform to repository styling conventions.

;;;

18. Classic vs Agentic Visualization

Create:

enterprise-semantics-visuals/concepts/
  value-stream-vs-agentic-value-stream.puml

The visual shall depict two parallel representations.

Classic Value Stream

Trigger
  |
Value Stage
  |
Process
  |
Decision / Execution
  |
Next Stage
  |
Stakeholder Value

Agentic Value Stream

Trigger
  |
Value Stage
  |
Context
  |
Intent
  |
Agent
  |
Authority / Constraints
  |
Action Selection
  |
Execution
  |
Outcome
  ↺
Contextual Adaptation
  |
Next Value Stage

The illustration must make clear that the value journey remains the same semantic construct, while the realization mechanism becomes capable of agency.

;;;

19. Example, OTCHERE Inc Order-to-Cash

Add:

enterprise-semantics-examples/value-streams/
  order-to-cash.yaml
  order-to-cash-agentic.yaml

The classic example shall demonstrate the Value Stream established by CR-ES-003.

The Agentic example shall demonstrate agentic participation such as:

Customer Demand
      |
Order Capture
      |
Customer Context Interpretation
      |
Order Validation
      |
Fulfillment Path Selection
      |
Inventory / Logistics Coordination
      |
Exception Adaptation
      |
Human Escalation if Authority Exceeded
      |
Delivery
      |
Settlement
      |
Customer / Enterprise Outcome

The example shall explicitly identify:

* Agent;
* delegated Intent;
* Authority;
* agentic Scope;
* decision Boundary;
* intervention Model;
* resulting Outcome.

;;;

20. Example, Pay-to-Fulfillment

Add an additional example illustrating a value stream where agentic participation is distributed across financial and operational stages.

The example should demonstrate:

Payment Initiation
      |
Payment Interpretation
      |
Risk / Constraint Assessment
      |
Transaction Routing
      |
Fulfillment Coordination
      |
Exception Handling
      |
Settlement
      |
Stakeholder Value

The example must remain technology-neutral.

;;;

21. Conformance Tests

Create:

enterprise-semantics-test-probe/conformance/
  agentic-value-stream/

Tests shall include:

Positive

AVS-CON-001
Agentic Value Stream specializes Value Stream.

AVS-CON-002
Agentic Value Stream contains one or more Value Stages.

AVS-CON-003
Agentic Value Stream realizes Stakeholder Value.

AVS-CON-004
Agentic Value Stream engages an Agent.

AVS-CON-005
Agentic participation references Intent.

AVS-CON-006
Agentic participation references Authority.

AVS-CON-007
Agentic scope may cover selected stages rather than the entire stream.

AVS-CON-008
Human intervention may coexist with agentic participation.

AVS-CON-009
Mixed realization modes are valid.

AVS-CON-010
Grounding and provenance are present.

;;;

22. Negative Conformance Tests

The following must fail validation:

AI is-a Agentic Value Stream
Agentic Value Stream is-a AI System
Agentic Value Stream is-a Autonomous Value Stream
Agentic Value Stream requires AI
Agentic Value Stream requires full autonomy
Agentic Value Stream replaces Value Stream
Agentic Value Stream is-a Process
Agentic Value Stream is-a Workflow
Agentic Value Stream establishes Agentic Workflow
Agentic Value Stream establishes Agentic Operations

These tests are architectural safeguards against semantic drift.

;;;

23. Schema Validation

CI shall validate:

* YAML/JSON syntax;
* schema conformity;
* concept registry integrity;
* relationship integrity;
* inheritance integrity;
* mandatory Value Stream properties;
* Agentic Value Stream properties;
* provenance;
* version;
* mapping references;
* profile references;
* example validity.

The implementation shall fail CI if Agentic Value Stream can be instantiated without satisfying the mandatory Value Stream inheritance requirements.

;;;

24. Relationship Integrity

CI shall validate:

Agentic Value Stream
        |
Value Stream

and:

Agentic Value Stream
        |
Agent
        |
Intent
Authority
Action
Outcome

The validator shall reject dangling semantic references.

;;;

25. Documentation Conformance

Documentation shall be checked for explicit distinctions:

Agentic ≠ AI
Agentic ≠ Automation
Agentic ≠ Autonomous
Agentic Value Stream ≠ Agentic Workflow
Agentic Value Stream ≠ Agentic Operations
Agentic Value Stream ≠ Process
Agentic Value Stream ≠ Workflow

This is a semantic conformance requirement, not merely editorial guidance.

;;;

26. Versioning

Increment Enterprise-Semantics to:

v0.4.0

Rationale:

* CR-ES-004 introduced foundational agentic semantics;
* CR-ES-005 introduces a major semantic specialization consuming that foundation;
* the release adds a new canonical concept and associated mappings, profiles, examples, and conformance artifacts.

No WSF or OpenDEA version increment is implied by this CR.

;;;

27. Implementation Sequence

Implementation shall proceed in this order:

1. Confirm Value Stream schema compatibility
             |
2. Add Agentic Value Stream schema
             |
3. Register concept
             |
4. Add relationships
             |
5. Add profiles
             |
6. Add WSF mapping
             |
7. Add OpenDEA mapping
             |
8. Add documentation
             |
9. Add UML / visual artifacts
             |
10. Add canonical examples
             |
11. Add positive conformance tests
             |
12. Add negative conformance tests
             |
13. Run CI validation
             |
14. Semantic review
             |
15. Publish v0.4.0

;;;

28. Acceptance Criteria

CR-ES-005 is complete when:

* [ ]	Agentic Value Stream has a canonical definition.
* [ ]	Agentic Value Stream specializes Value Stream.
* [ ]	Value Stream inheritance is validated.
* [ ]	Agentic scope is represented.
* [ ]	Intent and Authority linkage is represented.
* [ ]	Agent participation is represented.
* [ ]	Mixed realization is supported.
* [ ]	Human intervention is supported.
* [ ]	AI is not a semantic requirement.
* [ ]	Automation is not conflated with agency.
* [ ]	Autonomy is not implied.
* [ ]	Process and Workflow boundaries remain intact.
* [ ]	WSF mapping is established without modifying WSF.
* [ ]	OpenDEA mapping is established without modifying OpenDEA.
* [ ]	Profile is established.
* [ ]	Documentation is complete.
* [ ]	UML relational model exists.
* [ ]	Classic vs Agentic Value Stream visualization exists.
* [ ]	OTCHERE Inc examples exist.
* [ ]	Positive conformance tests pass.
* [ ]	Negative conformance tests pass.
* [ ]	CI validates the complete semantic package.
* [ ]	v0.4.0 is publishable.

;;;

29. Governance

Implementation shall follow:

ADR-ES-005
      |
CR-ES-005
      |
PR
      |
Schema Validation
      |
Semantic Conformance
      |
Architecture Review
      |
CI
      |
Enterprise-Semantics v0.4.0

No implementation outside this scope shall be merged under CR-ES-005.

In particular, introducing Agentic Workflow, Agentic Operations, Autonomous Value Stream, or AI-specific ontology under this CR constitutes scope expansion and requires a separate governed change.

;;;

30. Definition of Done

CR-ES-005 is considered implemented when the Enterprise-Semantics repository can answer, machine-readably and unambiguously:

What is an Agentic Value Stream?

How does it specialize Value Stream?

Where does agency enter the value-realization model?

How is agentic participation bounded by intent and authority?

How does it coexist with human and conventional execution?

How is it different from AI, automation, and autonomy?

How does it remain distinct from Process and Workflow?

and when those answers are enforced through schemas, mappings, examples, diagrams, provenance, and automated conformance tests.

This gives the sequence a clean semantic progression:

CR-ES-003
Value Stream
      |
CR-ES-004
Agentic
      |
CR-ES-005
Agentic Value Stream
      |
future
Agentic Workflow
      |
future
Agentic Operations
      |
future
Autonomous
      |
future
Autonomous Value Stream

The important architectural move in ES-005 is that we now have a formal place for the user’s broader Agentic Value Stream work without making the concept synonymous with AI. It establishes the value-stream transformation first; the specialized execution mechanisms can then be grounded independently.

;;

31. Acceptance

This CR was promoted from Proposed to Accepted on 2026-09-23 per user directive message 1552289869429088307 (*Save it, read and understand, then proceed with all tasks needed to make way to implement it appropriately. Then implement it.*). The promotion ritual per ADR-ES-001 §10-§11 (body Status field + this §31 Acceptance section, with the cardinal author footer preserved) was executed in concert with the ADR-ES-005 promotion.

The promotion to Accepted has the following consequences:

* All 23 acceptance criteria of §28 are satisfied via 7 PRs across 6 repos.
* Agentic Value Stream (ES:CONCEPT:agentic-value-stream) is canonical at Candidate lifecycle.
* The 3 Agentic Value Stream governed predicates from §10 are registered in relationships/vocabulary.yaml v0.5.0 (PR #11 enterprise-semantics).
* The 3 inverse pairs from §10 are registered in relationships/inverse.yaml v0.5.0.
* Enterprise-Semantics v0.4.0 is the canonical version pointer per §26 (versions/v0.4.0.yaml).
* ES:PROFILE:agentic-value-realization (per §14) is registered at registry/profiles/.
* 2 mapping records (WSF + OpenDEA per §12 + §13) are PROPOSED (PR #5 enterprise-semantics-mappings).
* 9 documentation files (per §15 + §16 + §23) are published (PR #4 enterprise-semantics-docs).
* 1 OTCHERE Inc example (per §19) is published (PR #4 enterprise-semantics-examples).
* 9 test files (per §21 + §22) are published (PR #4 enterprise-semantics-test-probe).
* 3 PlantUML sources (per §17 + §18) are published (PR #5 enterprise-semantics-visuals).
* No Agentic Workflow ;; Agentic Operations ;; Agentic Flow ;; Autonomous Value Stream ;; Autonomous Agent ;; Autonomous Enterprise ;; Autonomous Operations ;; AI-specific semantics ;; vendor-specific agent frameworks are canonicalised (per §3).
* No WSF metamodel change has been made (per §3 + §12 + ADR-ES-005 §16).
* No OpenDEA metamodel change has been made (per §3 + §13).
* No DEA catalog implementation has been made (per §3).
* The implementation sequence per §27 has been completed: schema compatibility + Agentic Value Stream schema + concept registry + relationships + profiles + WSF mapping + OpenDEA mapping + documentation + UML / visual artefacts + canonical examples + positive conformance tests + negative conformance tests + CI validation.
* The FND-ES-AG-002 Profile hypothesis has been formally superseded by the specialisation hypothesis (per ADR-ES-005 §2).
* The follow-on sequence is unblocked: ADR-ES-006 (Agentic Workflow) ;; ADR-ES-007 (Agentic Operations) ;; ADR-ES-008 (Autonomous) ;; ADR-ES-009 (Autonomous Value Stream).

Promoted by: Emmanuel A. Otchere (cardinal author rule, 2026-09-23) per ADR-ES-001 §10-§11 promotion ritual.

<!--
Authored by: Emmanuel A. Otchere (cardinal author rule, 2026-09-23)
Promoted by: Emmanuel A. Otchere (cardinal author rule, 2026-09-23) per ADR-ES-001 §10-§11 promotion ritual
-->
