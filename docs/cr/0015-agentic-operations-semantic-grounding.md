Below is CR-ES-007, scoped strictly to implement ADR-ES-007 without prematurely canonicalizing Operations, Operational Context, Policy, or Operational Outcome as separate foundational concepts.

CR-ES-007 ;;; Implement Agentic Operations Semantic Grounding

Status: Proposed
Date: 2026-09-23
Change Type: Foundational Semantic Specialization
Priority: P0
Target: Enterprise-Semantics
Authorizing ADR: ADR-ES-007 ;;; Agentic Operations Semantic Grounding
Target Semantic Version: v0.6.0
Depends On: CR-ES-001, CR-ES-003, CR-ES-004, CR-ES-005, CR-ES-006

;;;

1. Change Objective

Implement the semantic grounding established by ADR-ES-007 for Agentic Operations.

This change establishes Agentic Operations as a governed semantic specialization of Operations describing an operating mode in which operational sensing, interpretation, decision, coordination, adaptation, or execution is materially performed through agentic behavior within defined intent, authority, and policy boundaries.

The implementation shall preserve the distinction between:

* Operations
* Agentic Operations
* Process
* Workflow
* Agentic Workflow
* Value Stream
* Agentic Value Stream
* Agent
* Automation
* AI
* Autonomous Operations

The implementation shall not introduce an implicit dependency in which Agentic Operations becomes synonymous with AI, automation, autonomy, workflow execution, or value-stream realization.

;;;

2. Authoritative Semantic Definition

The canonical definition SHALL be:

Agentic Operations are operations in which operational sensing, interpretation, decision, coordination, adaptation, or execution is materially performed through agentic behavior within defined intent, authority, and policy boundaries.

The implementation SHALL preserve this wording unless a subsequent governed ADR supersedes it.

;;;

3. Architectural Decision Being Implemented

CR-ES-007 implements the following semantic assertion:

Agentic Operations
        |
        L-- specializes --► Operations

Agentic Operations therefore inherits the semantic context of Operations while adding a specific agentic operating mode.

It does not replace Operations.

It does not redefine Operations.

It does not establish Agentic Operations as a subtype of Process or Workflow.

;;;

4. Scope

4.1 In Scope

This CR shall implement:

1. Agentic Operations canonical concept.
2. Agentic Operations semantic properties.
3. Agentic Operations relationships.
4. Agentic Operations registry entry.
5. Agentic Operations profile.
6. WSF correspondence/mapping.
7. OpenDEA correspondence/mapping.
8. Agentic Operations documentation.
9. Agentic operational-loop documentation.
10. Agentic Workflow ↔ Agentic Operations boundary documentation.
11. PlantUML visualizations.
12. Representative enterprise examples.
13. Positive conformance tests.
14. Negative conformance tests.
15. Schema validation.
16. Relationship validation.
17. Semantic invariant validation.
18. v0.6.0 release preparation.

;;;

4.2 Explicitly Out of Scope

This CR shall not establish:

* Autonomous Operations.
* Autonomous Value Stream.
* Agentic Enterprise.
* Autonomous Enterprise.
* Agentic Network.
* Agentic Ecosystem.
* AI Operations as a synonym for Agentic Operations.
* AIOps as an Agentic Operations specialization.
* MLOps as an Agentic Operations specialization.
* Operational autonomy levels.
* A generalized autonomy ontology.
* A new Operations ontology where one does not already exist.
* A new Policy ontology.
* A new Operational Context ontology.
* A new Operational Outcome ontology.
* Changes to the WSF ontology.
* Changes to the OpenDEA metamodel.
* Changes to DEA catalogs.

Where a referenced concept is not yet canonically established, this CR shall document the dependency or correspondence rather than silently creating a new foundational concept.

;;;

5. Semantic Position

The implementation shall preserve the following architecture:

Stakeholder Value
       |
       v
Agentic Value Stream
       |
       v
Value Stage
       |
       v
Process
       |
       +--------------► Workflow
       |
       L--------------► Agentic Workflow
                              |
                              v
                       Agentic Operations
                              |
                 +------------+------------┐
                 v            v            v
               Agent        Human        System

This diagram is explanatory rather than a strict containment hierarchy.

In particular:

Agentic Operations is an operational mode and semantic context, not merely a parent container for Agentic Workflow.

Agentic Operations may coordinate multiple processes and workflows, while an Agentic Workflow represents a particular mechanism for coordinating or executing work.

;;;

6. Canonical Concept Artifact

Create:

enterprise-semantics/concepts/agentic-operations.yaml

The concept SHALL contain, at minimum:

id: ES:CONCEPT:AGENTIC_OPERATIONS
name: Agentic Operations
definition: >
  Agentic Operations are operations in which operational sensing,
  interpretation, decision, coordination, adaptation, or execution
  is materially performed through agentic behavior within defined
  intent, authority, and policy boundaries.
semantic_type: AgenticOperations
specializes:
  - Operations
status: Candidate
properties:
  - operational_intent
  - operational_scope
  - agentic_scope
  - authority_context
  - policy_context
  - decision_boundary
  - adaptation_scope
  - intervention_model
  - observation_scope
  - escalation_boundary
relationships:
  - specializes
  - engages
  - responds-to
  - operates-within
  - governed-by
  - coordinates
  - uses
  - produces
  - adapts-to
grounding:
  - WSF
provenance:
  - ADR-ES-007
  - CR-ES-007
version: 0.6.0

The exact repository schema SHALL prevail over this illustrative structure.

;;;

7. Semantic Properties

The following properties SHALL be supported.

Property	Semantic purpose
operational_intent	Establishes the intended operational direction or result.
operational_scope	Defines the operational domain or boundary being managed.
agentic_scope	Identifies where agentic behavior materially participates in operations.
authority_context	Defines the authority within which operational decisions/actions may occur.
policy_context	Identifies policies and constraints governing operational behavior.
decision_boundary	Defines decisions that may be interpreted, selected, or coordinated agentically.
adaptation_scope	Defines what operational behavior may adapt to changing conditions.
intervention_model	Defines human or other intervention points.
observation_scope	Defines operational conditions and outcomes being observed.
escalation_boundary	Defines conditions requiring escalation beyond delegated authority.

These properties SHALL describe semantic characteristics rather than prescribe a particular technology.

;;;

8. Canonical Relationships

The following relationships SHALL be implemented where their target concepts are already canonical.

8.1 Specialization

Agentic Operations -> specializes -> Operations

8.2 Agent engagement

Agentic Operations -> engages -> Agent

8.3 Operational context

Agentic Operations -> responds-to -> Operational Context
Agentic Operations -> adapts-to -> Operational Context

If Operational Context is not independently canonical, these references SHALL be represented as governed semantic references rather than used to create a new foundational concept.

8.4 Authority

Agentic Operations -> operates-within -> Authority

8.5 Policy

Agentic Operations -> governed-by -> Policy

The implementation SHALL reuse the established relationship vocabulary from CR-ES-004 wherever applicable.

8.6 Process coordination

Agentic Operations -> coordinates -> Process

8.7 Agentic Workflow usage

Agentic Operations -> uses -> Agentic Workflow

This relationship is valid because Agentic Workflow is established by ADR-ES-006.

It SHALL NOT imply:

Agentic Operations -> is-a -> Agentic Workflow

8.8 Operational outcome

Agentic Operations -> produces -> Operational Outcome

8.9 Relationship integrity

Every relationship SHALL specify:

* source concept;
* relationship predicate;
* target concept;
* relationship semantics;
* provenance;
* status.

No relationship SHALL be inferred merely from naming similarity.

;;;

9. Agentic Operational Loop

The implementation SHALL document the following semantic loop:

Operational Context
        |
        v
      Sense
        |
        v
   Interpret
        |
        v
     Decide
        |
        v
   Coordinate
        |
        v
       Act
        |
        v
 Observe Outcome
        |
        v
     Adapt
        |
        L--------------► Operational Context

The loop SHALL operate within:

Intent
   v
Authority
   v
Policies / Constraints
   v
Decision Boundary
   v
Operational Action
   v
Outcome

The loop is a semantic model of operational behavior, not a requirement for a particular control-loop implementation.

;;;

10. Agentic Operations vs Agentic Workflow

The implementation SHALL explicitly preserve the following boundary.

Dimension	Agentic Workflow	Agentic Operations
Primary concern	Work coordination/execution	Ongoing operational behavior
Semantic scope	Workflow	Operational environment
Time horizon	Workflow execution	Continuous/ongoing operation
Context	Workflow context	Operational context
Decision focus	Work path/action	Operational response
Adaptation	Workflow execution	Operational behavior
Process relationship	Realizes/executes work	Coordinates operational processes
Agent relationship	Engages Agents	May coordinate multiple Agents
Workflow relationship	Is a Workflow specialization	May use multiple Workflows
AI requirement	None	None
Autonomy implication	None	None

A workflow does not become Agentic Operations merely because it invokes an Agent.

Conversely, Agentic Operations may use conventional workflows, Agentic Workflows, human work, automated mechanisms, or combinations thereof.

;;;

11. Agentic Operations vs Agentic Value Stream

The implementation SHALL also preserve this boundary:

Dimension	Agentic Value Stream	Agentic Operations
Primary concern	Stakeholder value realization	Operational execution/management
Anchor	Stakeholder Value	Operational Outcome
Boundary	End-to-end value journey	Operating environment
Structure	Value Stages	Processes, workflows, operational activities
Purpose	Realize stakeholder value	Sustain and adapt operations
Scope	Value realization	Operational environment
Relationship	May depend on Agentic Operations	May support multiple Value Streams
AI requirement	None	None
Autonomy implication	None	None

A Value Stream may therefore depend on or use Agentic Operations without being reducible to them.

;;;

12. Agentic Operations and Human Participation

The implementation SHALL explicitly allow human participation.

Valid forms include:

Human-in-the-loop
Human-on-the-loop
Human-over-the-loop
Human escalation
Human approval
Human intervention

The following SHALL be invalid:

Agentic Operations requires removal of humans

Human participation does not invalidate the Agentic Operations semantic classification.

;;;

13. AI and Automation Boundary

Agentic Operations SHALL NOT require AI.

The following configurations shall remain semantically valid:

Agentic Operations + AI
Agentic Operations without AI
Agentic Operations + automation
Agentic Operations + human decision-making
Agentic Operations + systems
Agentic Operations + mixed execution mechanisms

The implementation SHALL prohibit the following semantic inference:

AI Operations = Agentic Operations
Automation = Agentic Operations
AI Agent = Agentic Operations

AI may implement or support agentic behavior, but AI is not the defining semantic characteristic.

;;;

14. Autonomy Boundary

Agentic Operations SHALL NOT imply Autonomous Operations.

The following implication SHALL be explicitly prohibited:

Agentic Operations -> Autonomous Operations

Autonomy requires separate semantic grounding and governance.

A future Autonomous Operations concept SHALL therefore require its own ADR and CR.

;;;

15. Registry

Update the Enterprise-Semantics concept registry with:

AGENTIC_OPERATIONS

The registry entry SHALL identify:

* Concept ID.
* Concept name.
* Semantic type.
* Status.
* Definition.
* Version.
* Authorizing ADR.
* Implementation CR.
* Related profile.

No autonomous or AI-specific registry entries shall be introduced through this CR.

;;;

16. Profile

Create:

ES:PROFILE:AGENTIC_OPERATIONS

The profile SHALL group:

Agentic Operations
Agent
Agentic
Intent
Authority
Agentic Workflow

Where existing profile structures permit reuse, the profile may reference or extend:

ES:PROFILE:AGENTIC
ES:PROFILE:AGENTIC_EXECUTION

The profile SHALL be treated as a semantic grouping mechanism.

It SHALL NOT imply inheritance among its members.

;;;

17. WSF Mapping

Create:

enterprise-semantics-mappings/wsf/agentic-operations.yaml

The mapping SHALL establish the intended correspondence to WSF.

If WSF already provides a canonical Operations concept:

Enterprise-Semantics Agentic Operations
        |
        L-- specialization/correspondence --► WSF Operations

If no canonical WSF Operations identifier exists, the mapping SHALL NOT invent one.

Instead, it SHALL record:

* intended semantic correspondence;
* unresolved target;
* mapping rationale;
* provenance;
* required future WSF governance.

This CR does not authorize WSF ontology modification.

;;;

18. OpenDEA Mapping

Create:

enterprise-semantics-mappings/opendea/agentic-operations.yaml

The mapping SHALL document correspondence to relevant OpenDEA operational semantics where such concepts exist.

The mapping SHALL distinguish:

* semantic correspondence;
* specialization;
* implementation realization;
* contextual use.

This CR does not modify the OpenDEA metamodel.

No OpenDEA metamodel change shall be implied by the mapping.

;;;

19. Documentation

Create:

enterprise-semantics-docs/concepts/agentic-operations.md
enterprise-semantics-docs/architecture/agentic-operations-boundary.md
enterprise-semantics-docs/architecture/agentic-operational-loop.md
enterprise-semantics-docs/architecture/agentic-workflow-operations-boundary.md

The concept document SHALL include:

1. Definition.
2. Semantic grounding.
3. Specialization.
4. Characteristics.
5. Properties.
6. Relationships.
7. Operational loop.
8. Human participation.
9. AI boundary.
10. Automation boundary.
11. Autonomy boundary.
12. Relationship to Agentic Workflow.
13. Relationship to Agentic Value Stream.
14. Examples.
15. Non-examples.
16. Conformance requirements.
17. Provenance.

;;;

20. Visualizations

Create:

enterprise-semantics-visuals/
  concepts/
    agentic-operations.puml
  relationships/
    agentic-operations-relationships.puml
  architecture/
    agentic-operational-loop.puml
    agentic-workflow-vs-agentic-operations.puml
    agentic-value-stream-operations-boundary.puml

The diagrams SHALL distinguish:

Value realization
        v
Operational realization
        v
Work execution
        v
Implementation

They SHALL not visually imply that Agentic Operations is a subtype of Agentic Workflow.

;;;

21. Enterprise Example

Create an example based on OTCHERE Inc.

Suggested example:

OTCHERE Inc.
    |
    v
Operational Context
    |
    +-- Order demand
    +-- Inventory conditions
    +-- Logistics status
    +-- Customer conditions
    L-- Operational constraints
            |
            v
     Agentic Operations
            |
            +-- Sense
            +-- Interpret
            +-- Assess
            +-- Decide
            +-- Coordinate
            +-- Act
            +-- Observe
            +-- Adapt
            L-- Escalate
                    |
          +---------+----------┐
          v         v          v
      Inventory   Logistics   Customer
      Workflow    Workflow    Escalation

The example SHALL demonstrate that multiple workflows can participate in the same Agentic Operations environment.

Possible workflows include:

* Order Fulfillment Workflow.
* Inventory Replenishment Workflow.
* Delivery Exception Workflow.
* Customer Escalation Workflow.

Not every workflow needs to be Agentic.

;;;

22. Example Semantic Assertion

The example SHALL support assertions such as:

OTCHERE Inc
    operates Agentic Operations
Agentic Operations
    engages Agent
Agentic Operations
    responds-to Operational Context
Agentic Operations
    operates-within Authority
Agentic Operations
    governed-by Policy
Agentic Operations
    coordinates Process
Agentic Operations
    uses Agentic Workflow
Agentic Operations
    produces Operational Outcome
Agentic Operations
    adapts-to Operational Context

The example SHALL NOT assert:

Agentic Operations is Autonomous Operations
Agentic Operations requires AI
Agentic Operations is Agentic Workflow
Agentic Operations is Agentic Value Stream

;;;

23. Conformance Tests

Implement conformance tests covering the following requirements.

AOP-CON-001 ;;; Specialization

Agentic Operations MUST specialize Operations.

AOP-CON-002 ;;; Material Agentic Participation

An implementation MUST demonstrate material agentic participation in operational sensing, interpretation, decision, coordination, adaptation, or execution.

AOP-CON-003 ;;; Authority

Agentic Operations MUST operate within a defined authority boundary.

AOP-CON-004 ;;; Policy

Operational behavior MUST be capable of being constrained by policies or equivalent operational constraints.

AOP-CON-005 ;;; Outcome Orientation

Agentic Operations MUST be oriented toward operational outcomes.

AOP-CON-006 ;;; Agent Engagement

Agentic Operations MUST support engagement of an Agent where agentic behavior is asserted.

AOP-CON-007 ;;; Agentic Workflow Compatibility

Agentic Operations MAY use Agentic Workflow.

AOP-CON-008 ;;; Process Coordination

Agentic Operations MAY coordinate one or more Processes.

AOP-CON-009 ;;; Human Participation

Human participation MUST remain semantically valid.

AOP-CON-010 ;;; Automation Compatibility

Automation MAY coexist with Agentic Operations.

AOP-CON-011 ;;; AI Independence

Agentic Operations MUST NOT require AI.

AOP-CON-012 ;;; Autonomy Independence

Agentic Operations MUST NOT imply Autonomous Operations.

AOP-CON-013 ;;; Workflow Distinction

Agentic Operations MUST NOT be classified as Agentic Workflow.

AOP-CON-014 ;;; Value Stream Distinction

Agentic Operations MUST NOT be classified as Agentic Value Stream.

AOP-CON-015 ;;; Provenance

Every canonical Agentic Operations assertion MUST identify its semantic provenance.

;;;

24. Negative Conformance Tests

The test suite SHALL explicitly reject:

Agentic Operations is-a Agentic Workflow
Agentic Operations is-a Agentic Value Stream
Agentic Operations is-a Process
Agentic Operations requires AI
Agentic Operations implies Autonomous Operations
Agentic Operations requires removal of human participation
Operations containing an Agent automatically become Agentic Operations
Agentic Operations = Agentic Workflow
Agentic Operations = AIOps
Agentic Operations = Automated Operations
Agentic Operations establishes Autonomous Operations

These negative tests are architectural invariants.

;;;

25. Schema Validation

CI SHALL validate:

* YAML syntax.
* Required fields.
* Concept identifiers.
* Registry references.
* Relationship predicates.
* Relationship targets.
* Profile references.
* Provenance references.
* Version consistency.
* Mapping structure.
* Conformance-test structure.

A malformed Agentic Operations artifact SHALL fail CI.

;;;

26. Semantic Validation

CI SHALL additionally verify:

Agentic Operations
    specializes Operations

and reject:

Agentic Operations
    specializes Agentic Workflow
Agentic Operations
    specializes Agentic Value Stream
Agentic Operations
    specializes Autonomous Operations

The validator SHALL also ensure that the following semantic properties are present:

authority_context
policy_context
decision_boundary
agentic_scope
intervention_model
escalation_boundary

;;;

27. Dependency Handling

Before implementation, inspect whether the following concepts already have canonical identifiers:

Operations
Operational Context
Policy
Operational Outcome
Process
Agent
Agentic Workflow
Authority
Intent

If canonical

Reference the existing identifiers.

If not canonical

Do not silently create full foundational concepts.

Instead:

1. Record the unresolved dependency.
2. Use the minimum governed reference structure permitted by the repository schema.
3. Mark the mapping as pending where necessary.
4. Create a Finding for future semantic grounding.
5. Do not expand CR-ES-007 beyond its authorization.

This prevents the Agentic Operations CR from becoming an uncontrolled expansion of the semantic foundation.

;;;

28. Repository Changes

Expected implementation footprint:

enterprise-semantics/
+-- concepts/
|   L-- agentic-operations.yaml
|
+-- mappings/
|   +-- wsf/
|   |   L-- agentic-operations.yaml
|   L-- opendea/
|       L-- agentic-operations.yaml
|
+-- profiles/
|   L-- agentic-operations.yaml
|
+-- registry/
|   L-- ...
|
+-- docs/
|   +-- concepts/
|   |   L-- agentic-operations.md
|   L-- architecture/
|       +-- agentic-operations-boundary.md
|       +-- agentic-operational-loop.md
|       L-- agentic-workflow-operations-boundary.md
|
+-- examples/
|   L-- operations/
|       L-- otchere-agentic-operations.yaml
|
L-- visuals/
    +-- concepts/
    |   L-- agentic-operations.puml
    L-- architecture/
        +-- agentic-operational-loop.puml
        +-- agentic-workflow-vs-agentic-operations.puml
        L-- agentic-value-stream-operations-boundary.puml

The exact repository structure SHALL follow the established implementation conventions from CR-ES-001 through CR-ES-006.

;;;

29. Governance

Implementation SHALL follow:

ADR-ES-007
     v
CR-ES-007
     v
Implementation
     v
Validation
     v
Conformance Tests
     v
PR
     v
CI
     v
Semantic Release v0.6.0

No implementation outside this CR’s scope is authorized.

Any newly discovered foundational semantic requirement SHALL become a Finding rather than being silently incorporated.

;;;

30. Acceptance Criteria

CR-ES-007 is accepted when:

* [ ]	Agentic Operations has a canonical concept artifact.
* [ ]	The ADR definition is implemented without semantic drift.
* [ ]	Agentic Operations specializes Operations.
* [ ]	Required properties are represented.
* [ ]	Required relationships are represented.
* [ ]	Agentic Workflow boundary is explicit.
* [ ]	Agentic Value Stream boundary is explicit.
* [ ]	Human participation remains valid.
* [ ]	AI is not a semantic requirement.
* [ ]	Automation is not equated with Agentic Operations.
* [ ]	Autonomy is not implied.
* [ ]	Registry is updated.
* [ ]	Profile is established.
* [ ]	WSF mapping is established without unauthorized WSF modification.
* [ ]	OpenDEA mapping is established without unauthorized OpenDEA modification.
* [ ]	Documentation is complete.
* [ ]	PlantUML diagrams compile.
* [ ]	OTCHERE Inc example validates.
* [ ]	Positive conformance tests pass.
* [ ]	Negative conformance tests pass.
* [ ]	Schema validation passes.
* [ ]	Relationship validation passes.
* [ ]	Provenance validation passes.
* [ ]	No unapproved foundational concepts are introduced.
* [ ]	CI passes.
* [ ]	Release metadata targets v0.6.0.

;;;

31. Definition of Done

CR-ES-007 is Done when the Enterprise-Semantics repository can demonstrate, through machine-readable semantics and automated conformance validation, that:

Agentic Operations is a governed specialization of Operations describing materially agentic operational behavior within defined intent, authority, and policy boundaries, while remaining distinct from Agentic Workflow, Agentic Value Stream, Process, AI, Automation, and Autonomous Operations.

The resulting semantic artifact SHALL be suitable for downstream mapping into WSF and OpenDEA without requiring either foundation to be modified by this CR.

;;;

32. Future Work Identified but Not Authorized

The following remain future semantic decisions:

ADR-ES-008+ ;;; Autonomous Operations
ADR-ES-009+ ;;; Agentic Enterprise
ADR-ES-010+ ;;; Autonomous Enterprise
ADR-ES-011+ ;;; Agentic Network
ADR-ES-012+ ;;; Agentic Ecosystem

Exact sequencing remains subject to subsequent architectural investigation.

No future concept listed above becomes canonical as a result of CR-ES-007.

;;;

33. Final Change Statement

CR-ES-007 establishes the operational semantic layer of the agentic architecture.

The resulting distinction is:

Agentic Value Stream
    = agentic value realization
Agentic Operations
    = agentic operational behavior
Agentic Workflow
    = agentic work coordination/execution
Agent
    = entity performing agentic behavior

Together, these concepts establish a coherent semantic progression without collapsing value realization, operations, execution, and agency into a single AI-centric abstraction.

Target Release: v0.6.0

This gives the agentic sequence a clean progression: Agent -> Agentic Value Stream -> Agentic Workflow -> Agentic Operations, while preserving the different semantic layers rather than turning them into increasingly broad “agentic” variants.
<!--
Authored by: Emmanuel A. Otchere (cardinal author rule, 2026-09-23)
-->
