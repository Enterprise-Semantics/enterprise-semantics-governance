CR-ES-003 : Value Stream Semantic Grounding

Status: Proposed
Change Type: Foundational Semantic Grounding
Priority: P0 : Foundational Enterprise Concept
Related ADR: ADR-ES-003 : Value Stream Semantic Grounding
Depends On: CR-ES-001, CR-ES-002
Target Release: Enterprise-Semantics v0.2.0

;;

1. Objective

Implement ADR-ES-003 : Value Stream Semantic Grounding and establish Value Stream as a formally represented enterprise semantic concept within Enterprise-Semantics.

This change shall introduce:

* Value Stream;
* Value Stage;
* their semantic schemas;
* their canonical relationships;
* identity and lifecycle rules;
* provenance;
* WSF grounding;
* OpenDEA correspondence;
* DEA Catalog correspondence boundaries;
* worked semantic examples;
* conformance validation;
* reproducible visualizations.

The implementation shall establish the semantic foundation required for later:

* Agentic Value Stream;
* Autonomous Value Stream;
* Value Realization;
* Agentic Workflow;
* Agentic Operations.

No Agentic Value Stream semantics shall be established by this CR.

;;

2. Scope

2.1 In Scope

Semantic model

* Value Stream;
* Value Stage;
* Value Stream relationships;
* Value Stage relationships;
* initiating condition;
* value realization boundary;
* stakeholder value relationship;
* outcome relationship.

Infrastructure

* concept definitions;
* schemas;
* registry entries;
* relationship vocabulary;
* provenance;
* lifecycle;
* mappings;
* profiles;
* documentation;
* examples;
* visuals;
* conformance tests.

Architectural boundaries

* Value Stream ↔ Process;
* Value Stream ↔ Capability;
* Value Stream ↔ Outcome;
* Value Stream ↔ Service;
* Value Stream ↔ Workflow;
* Value Stream ↔ Organization;
* Value Stream ↔ Product.

;;

3. Out of Scope

The following are explicitly excluded:

* Agentic Value Stream;
* Autonomous Value Stream;
* Agentic Workflow;
* Autonomous Operations;
* AI Agent;
* Agentic Operations;
* Value Realization Framework;
* High-Value Scenario;
* Value of Function;
* KCI;
* KEI;
* KBI;
* modification of WSF;
* modification of OpenDEA;
* Process metamodel changes;
* Workflow metamodel changes;
* creation of an industry Value Stream catalog;
* creation of an enterprise-specific Value Stream catalog.

These require subsequent governed changes.

;;

4. Canonical Value Stream Definition

Implement the ADR-ES-003 definition:

A Value Stream is an end-to-end sequence of value-creating stages through which a stakeholder value proposition is realized, from an initiating need, demand, or trigger to a resulting stakeholder outcome or value realization.

This definition shall be stored in the machine-readable semantic source of truth.

The definition shall not be replaced by implementation-oriented language such as:

“A sequence of business processes.”

That would collapse Value Stream into Process.

;;

5. Canonical Value Stage Definition

Establish:

A Value Stage is a meaningful transition in the progression of stakeholder value within a Value Stream.

A Value Stage shall represent a value-relevant state transition rather than merely an executable unit of work.

A stage may be realized through:

* one Process;
* multiple Processes;
* Activities;
* Tasks;
* Services;
* Systems;
* human participation;
* automated execution.

Therefore:

Value Stage ≠ Process
Value Stage ≠ Activity
Value Stage ≠ Task

;;

6. Semantic Representation

Add the following concepts to:

enterprise-semantics/concepts/
value-stream.yaml
value-stage.yaml

;;

7. Value Stream Schema

The canonical representation shall contain, at minimum:

id:
name:
definition:
description:
status:
semantic_type: ValueStream
stakeholder:
initiating_condition:
realization_boundary:
stages: []
relationships: []
grounding:
  wsf:
  enterprise_semantics:
  opendea:
provenance:
  source:
  finding:
  adr:
  cr:
  implementation:
version:

Required semantics

stakeholder

Identifies the stakeholder or stakeholder context for which value is being realized.

initiating_condition

Identifies the need, demand, event, opportunity, or other condition that initiates the Value Stream.

realization_boundary

Identifies the intended endpoint at which the relevant stakeholder outcome or value realization has occurred.

stages

References the Value Stages composing the Value Stream.

;;

8. Value Stage Schema

Add:

id:
name:
definition:
description:
status:
semantic_type: ValueStage
value_stream:
preceding_stage:
following_stage:
purpose:
input_state:
resulting_state:
stakeholder:
outcomes: []
capabilities: []
processes: []
services: []
resources: []
relationships: []
grounding:
  wsf:
  enterprise_semantics:
  opendea:
provenance:
  source:
  finding:
  adr:
  cr:
  implementation:
version:

The schema shall distinguish value state from execution input/output.

A stage’s input_state and resulting_state describe the value progression.

Process input/output belongs to the Process semantic.

;;

9. Core Value Stream Relationships

Add or formalize the following predicates.

Subject	Predicate	Object
Value Stream	realizes	Stakeholder Value
Value Stream	contains	Value Stage
Value Stream	enabled-by	Capability
Value Stream	realized-through	Process
Value Stream	produces	Outcome
Value Stream	uses	Service
Value Stream	involves	Organization
Value Stream	uses	Resource
Value Stage	precedes	Value Stage
Value Stage	realized-through	Process
Value Stage	requires	Capability
Value Stage	produces	Outcome
Value Stage	contributes-to	Stakeholder Value

All predicates shall be represented in the relationship vocabulary.

;;

10. Relationship Semantics

10.1 Value Stream → realizes → Stakeholder Value

Definition:

A Value Stream realizes Stakeholder Value when progression through the Value Stream results in the intended stakeholder value being achieved or made available.

This is the primary Value Stream relationship.

;;

10.2 Value Stream → contains → Value Stage

Definition:

A Value Stream contains a Value Stage when that stage forms part of the defined progression of value realization.

;;

10.3 Value Stream → enabled-by → Capability

Definition:

A Value Stream is enabled by a Capability when that Capability provides an ability required for one or more stages of the Value Stream to be realized.

;;

10.4 Value Stream → realized-through → Process

Definition:

A Value Stream is realized through a Process when Process execution contributes to the realization of one or more stages of the Value Stream.

This relationship must not imply:

Value Stream = Process

;;

10.5 Value Stream → produces → Outcome

Definition:

A Value Stream produces an Outcome when progression through the Value Stream results in the specified outcome.

;;

10.6 Value Stream → uses → Service

Definition:

A Value Stream uses a Service when the Service provides functionality, interaction, or value-enabling means required by the Value Stream.

;;

10.7 Value Stream → involves → Organization

Definition:

A Value Stream involves an Organization when the Organization participates in, enables, or contributes to one or more stages of the Value Stream.

;;

10.8 Value Stage → precedes → Value Stage

Definition:

A Value Stage precedes another Value Stage when it occurs earlier in the defined progression of value realization.

The relationship shall support explicit ordering without requiring an implementation-specific workflow.

;;

10.9 Value Stage → realized-through → Process

Definition:

A Value Stage is realized through a Process when execution of the Process contributes to the transition represented by the Value Stage.

;;

10.10 Value Stage → requires → Capability

Definition:

A Value Stage requires a Capability when the Capability provides an ability necessary for the stage to be realized.

;;

10.11 Value Stage → produces → Outcome

Definition:

A Value Stage produces an Outcome when completion of the stage results in the specified outcome.

;;

11. Value Stream Identity Rules

Implement the following invariants.

VS-ID-001

Value Stream identifiers must be globally unique within Enterprise-Semantics.

VS-ID-002

A Value Stream identifier must not encode:

* organizational ownership;
* implementation technology;
* process identifier;
* system identifier;
* workflow identifier.

VS-ID-003

Changing the implementation of a Value Stream must not require changing its semantic identity.

VS-ID-004

A Value Stream name may change without changing its identifier when semantic identity remains unchanged.

VS-ID-005

A fundamentally different value journey requires a distinct Value Stream identity.

;;

12. Value Stage Identity Rules

VST-ID-001

Every Value Stage shall have a unique identifier.

VST-ID-002

A Value Stage identifier shall be unique independently of its Process implementation.

VST-ID-003

Changing the Process implementing a stage shall not inherently change the stage identity.

VST-ID-004

A Value Stage must belong to at least one Value Stream when published as a Value Stream instance.

VST-ID-005

A stage shall not be identified solely by an organizational unit.

;;

13. Value Progression Model

The semantic source shall support:

Initiating Condition
        |
        v
Value Stage 1
        |
        v
Value Stage 2
        |
        v
Value Stage 3
        |
        v
Value Stage N
        |
        v
Realization Boundary

The model must not require a strictly linear execution sequence.

A Value Stream may contain:

* branching;
* convergence;
* optional stages;
* repeated stages;
* conditional progression.

However, the semantics of these patterns shall not be confused with workflow execution semantics.

;;

14. Execution Boundary

CR-ES-003 shall explicitly preserve the following architectural boundary:

VALUE REALIZATION
──────────────────────────────────
Value Stream
     |
     v
Value Stage
──────────────────────────────────
EXECUTION
     |
     v
Process
     |
     v
Activity
     |
     v
Task
     |
     v
Workflow / Task Flow
──────────────────────────────────
IMPLEMENTATION
     |
     ├── Service
     ├── System
     ├── Resource
     |--── Technology

The implementation shall ensure that schemas do not accidentally collapse these layers.

;;

15. Capability Integration

CR-ES-003 shall reference the Capability semantics established by CR-ES-002.

The canonical relationship shall be:

Value Stream
      |
      |--── enabled-by ──> Capability

A Value Stream may require multiple capabilities.

A Capability may enable multiple Value Streams.

No Capability duplication shall be created within the Value Stream schema.

;;

16. Process Integration

The Value Stream implementation shall reference the existing Process semantic.

The relationship:

Value Stream
      |
      |--── realized-through ──> Process

shall be explicitly represented.

The implementation shall not create a parallel ValueStreamProcess concept.

;;

17. Workflow Boundary

Workflow shall not be a direct semantic decomposition of Value Stream.

The architecture shall remain:

Value Stream
      ->
Value Stage
      ->
Process
      ->
Activity
      ->
Task
      ->
Workflow / Task Flow

A Workflow may execute activities belonging to processes that realize a Value Stream.

This distinction becomes particularly important for subsequent Agentic Workflow and Agentic Value Stream semantics.

;;

18. Example : Order-to-Cash

Create an initial worked example using OTCHERE Inc.

id: ES:VALUE-STREAM:ORDER-TO-CASH
name: Order-to-Cash
definition: >
  An end-to-end sequence of value-creating stages through which
  a customer order is transformed into delivered value and
  corresponding financial realization.
semantic_type: ValueStream
stakeholder:
  - Customer
  - OTCHERE Inc
initiating_condition:
  type: Demand
  description: Customer requires an offering.
realization_boundary:
  description: Customer receives the intended offering and OTCHERE Inc realizes the corresponding commercial value.
stages:
  - ES:VALUE-STAGE:ORDER-TO-CASH:CAPTURE-DEMAND
  - ES:VALUE-STAGE:ORDER-TO-CASH:CONFIRM-ORDER
  - ES:VALUE-STAGE:ORDER-TO-CASH:FULFILL-ORDER
  - ES:VALUE-STAGE:ORDER-TO-CASH:DELIVER-OFFERING
  - ES:VALUE-STAGE:ORDER-TO-CASH:REALIZE-PAYMENT

This example is illustrative and shall not automatically establish Order-to-Cash as a canonical catalog Value Stream.

;;

19. Example : Value Stage

Illustrative:

id: ES:VALUE-STAGE:ORDER-TO-CASH:FULFILL-ORDER
name: Fulfill Order
definition: >
  A value stage through which the ordered offering is prepared
  to satisfy the confirmed customer demand.
semantic_type: ValueStage
value_stream:
  - ES:VALUE-STREAM:ORDER-TO-CASH
preceding_stage:
  - ES:VALUE-STAGE:ORDER-TO-CASH:CONFIRM-ORDER
following_stage:
  - ES:VALUE-STAGE:ORDER-TO-CASH:DELIVER-OFFERING
capabilities:
  - ES:CAPABILITY:ORDER-FULFILLMENT
processes:
  - ES:PROCESS:ORDER-FULFILLMENT

Identifiers shown for Process and Capability are illustrative references and shall only be used where corresponding governed concepts exist.

;;

20. Example : Pay-to-Fulfillment

The model shall also support Value Streams whose progression begins with a commercial or transactional trigger.

Illustrative:

Payment Demand
      |
      v
Pay-to-Fulfillment
      |
      ├── Establish Payment
      ├── Confirm Transaction
      ├── Authorize Fulfillment
      ├── Prepare Fulfillment
      ├── Fulfill Demand
      |--── Confirm Realization

The example demonstrates that Value Stream semantics are independent of a fixed process taxonomy.

;;

21. WSF Mapping

Create:

enterprise-semantics-mappings/wsf/value-stream.yaml

The mapping shall record:

source:
target:
mapping_type:
relationship:
confidence:
status:
provenance:
governing_adr: ADR-ES-003
governing_cr: CR-ES-003

The mapping must explicitly state whether the Enterprise-Semantics Value Stream is:

* equivalent;
* specialized;
* contextualized;
* extended;
* corresponding

to the relevant WSF semantic.

No WSF concept shall be copied into Enterprise-Semantics merely to avoid a mapping.

;;

22. OpenDEA Mapping

Create:

enterprise-semantics-mappings/opendea/value-stream.yaml

The mapping shall distinguish:

Enterprise-Semantics semantic
          ->
OpenDEA architectural construct

from:

OpenDEA construct
          ->
DEA Catalog instance

No OpenDEA metamodel modification is included in this CR.

;;

23. DEA Catalog Boundary

Create:

enterprise-semantics-mappings/dea-catalogs/value-stream.yaml

This mapping shall establish the downstream relationship without creating catalog content.

The eventual catalog architecture may contain:

Value Stream
    |
    ├── Value Stage
    ├── Capability
    ├── Process
    ├── Outcome
    |--── Stakeholder Value

but the actual catalog population requires a separate governed catalog change.

;;

24. Registry Changes

Add the following semantic types to the Enterprise-Semantics registry:

VALUE_STREAM
VALUE_STAGE

The registry shall track:

* identifier;
* name;
* semantic type;
* lifecycle;
* version;
* governing ADR;
* governing CR.

No example Value Stream shall become canonical merely by appearing in the registry.

;;

25. Lifecycle

Value Stream and Value Stage shall follow:

PROPOSED
    ->
CANDIDATE
    ->
ESTABLISHED
    ->
CANONICAL

The lifecycle shall support:

REJECTED
SUPERSEDED
DEPRECATED

as exceptional states.

;;

26. Provenance

Every canonical Value Stream and Value Stage shall record:

ADR-ES-003
CR-ES-003
implementation reference
semantic source
mapping provenance

Where external sources are used, they shall be recorded as sources rather than treated as semantic authority.

;;

27. Documentation

Add:

enterprise-semantics-docs/
├── concepts/
|   ├── value-stream.md
|   |--── value-stage.md
|
├── architecture/
|   ├── value-stream-boundary.md
|   ├── value-stream-process-boundary.md
|   |--── value-realization-boundary.md
|
|--── relationships/
    |--── value-stream-relationships.md

Documentation shall explain:

1. what Value Stream is;
2. what Value Stream is not;
3. Value Stream vs Process;
4. Value Stream vs Capability;
5. Value Stream vs Service;
6. Value Stream vs Workflow;
7. Value Stream vs Outcome;
8. Value Stream vs Value;
9. Value Stage semantics;
10. execution boundary;
11. WSF grounding;
12. OpenDEA mapping.

;;

28. Visual Model

Add reproducible source to:

enterprise-semantics-visuals/
|--── concepts/
    ├── value-stream.puml
    ├── value-stream-boundary.puml
    |--── value-stream-process-boundary.puml

The primary UML model shall represent:

ValueStream "1" *-- "1..*" ValueStage
ValueStream --> Capability : enabled-by
ValueStream --> Process : realized-through
ValueStream --> Outcome : produces
ValueStream --> StakeholderValue : realizes
ValueStage --> ValueStage : precedes
ValueStage --> Capability : requires
ValueStage --> Process : realized-through
ValueStage --> Outcome : produces

The diagram shall not imply that Process is structurally contained by Value Stream as an ontological child.

realized-through is a semantic relationship, not composition.

;;

29. Conformance Rules

Add Value Stream validation rules.

VS-CON-001 : Definition

Every Value Stream must have a definition.

VS-CON-002 : Identity

Every Value Stream must have a unique identifier.

VS-CON-003 : Stakeholder

Every published Value Stream must identify a stakeholder context.

VS-CON-004 : Initiation

Every published Value Stream must identify an initiating condition.

VS-CON-005 : Realization Boundary

Every published Value Stream must define its realization boundary.

VS-CON-006 : Stages

Every established Value Stream must contain at least one Value Stage.

VS-CON-007 : Value Relationship

Every established Value Stream must support a realizes relationship to Stakeholder Value.

VS-CON-008 : Process Boundary

A Value Stream must not be modeled as a specialization of Process.

VS-CON-009 : Capability Boundary

A Value Stream must not be modeled as a specialization of Capability.

VS-CON-010 : Workflow Boundary

A Value Stream must not be modeled as a Workflow.

VS-CON-011 : Stage Integrity

Every published Value Stage must reference a Value Stream.

VS-CON-012 : Stage Ordering

If stage ordering is asserted, preceding/following references must resolve.

VS-CON-013 : Relationship Integrity

Every Value Stream predicate must exist in the relationship vocabulary.

VS-CON-014 : Provenance

Every established Value Stream must reference its governing ADR and CR.

VS-CON-015 : Grounding

Every established Value Stream must declare its WSF grounding status.

VS-CON-016 : Lifecycle

All lifecycle values must conform to the Enterprise-Semantics lifecycle specification.

VS-CON-017 : Agentic Isolation

No Agentic Value Stream concept may be promoted to canonical status by this CR.

;;

30. Negative Conformance Tests

The test probe shall include explicit failure cases.

Invalid example 1

Value Stream is-a Process

Expected:

FAIL

Invalid example 2

Value Stream is-a Capability

Expected:

FAIL

Invalid example 3

Value Stream contains Task

as a direct semantic decomposition.

Expected:

FAIL

unless the model explicitly represents Task through the Process execution boundary.

Invalid example 4

Value Stage = Activity

Expected:

FAIL

unless a governed semantic relationship explicitly establishes the correspondence.

;;

31. Test Probe Structure

Add:

enterprise-semantics-test-probe/
|--── tests/
    |--── value-stream/
        ├── schema/
        ├── identity/
        ├── lifecycle/
        ├── relationships/
        ├── boundaries/
        ├── provenance/
        ├── grounding/
        |--── examples/

Tests shall include:

* valid Value Stream;
* invalid Value Stream;
* valid Value Stage;
* invalid Value Stage;
* broken stage reference;
* broken Process reference;
* broken Capability reference;
* invalid lifecycle;
* missing provenance;
* missing stakeholder;
* missing initiation;
* missing realization boundary;
* invalid Process specialization;
* invalid Capability specialization;
* unauthorized Agentic Value Stream status.

;;

32. Example Documentation

Create:

enterprise-semantics-examples/
|--── value/
    ├── order-to-cash.yaml
    ├── pay-to-fulfillment.yaml
    |--── value-stream-process-boundary.yaml

Examples shall use OTCHERE Inc where an enterprise example is required.

No ACME example shall be introduced.

;;

33. Semantic Profile

Update:

enterprise-semantics/profiles/value/

with Value Stream profile metadata.

The profile shall identify:

id: ES:PROFILE:VALUE
name: Value
scope:
  - Value
  - Value Stream
  - Value Stage

The profile shall group related concepts but shall not create an implicit ontology or semantic superclass.

;;

34. Versioning

CR-ES-003 shall establish:

Enterprise-Semantics v0.2.0

The release represents establishment of the foundational Value Stream semantic layer.

It does not imply:

* mature Value Stream catalogs;
* Agentic Value Stream support;
* autonomous value realization;
* complete value-management semantics.

;;

35. CI Pipeline

Extend CI with:

Schema Validation
       ->
Identifier Validation
       ->
Reference Validation
       ->
Relationship Validation
       ->
Lifecycle Validation
       ->
Provenance Validation
       ->
Value Stream Boundary Tests
       ->
Mapping Validation
       ->
Example Validation
       ->
Governance Traceability
       ->
Enterprise-Semantics Conformance

A release shall fail if a Value Stream violates any mandatory boundary rule.

;;

36. Acceptance Criteria

CR-ES-003 is complete when:

* [ ]	Value Stream schema exists.
* [ ]	Value Stage schema exists.
* [ ]	Value Stream definition is machine-readable.
* [ ]	Value Stage definition is machine-readable.
* [ ]	Value Stream identity rules are implemented.
* [ ]	Value Stage identity rules are implemented.
* [ ]	Value Stream lifecycle is implemented.
* [ ]	Value Stage lifecycle is implemented.
* [ ]	realizes relationship is established.
* [ ]	contains relationship is established.
* [ ]	enabled-by relationship is established.
* [ ]	realized-through relationship is established.
* [ ]	produces relationship is established.
* [ ]	Value Stage ordering is represented.
* [ ]	stakeholder context is represented.
* [ ]	initiating condition is represented.
* [ ]	realization boundary is represented.
* [ ]	Process boundary is validated.
* [ ]	Capability boundary is validated.
* [ ]	Workflow boundary is validated.
* [ ]	WSF mapping exists.
* [ ]	OpenDEA mapping exists.
* [ ]	DEA Catalog mapping boundary exists.
* [ ]	documentation is published.
* [ ]	PlantUML source is published.
* [ ]	OTCHERE Inc example is published.
* [ ]	Order-to-Cash example is published.
* [ ]	Pay-to-Fulfillment example is published.
* [ ]	conformance tests pass.
* [ ]	CI validates all Value Stream constraints.
* [ ]	no Agentic Value Stream semantics are canonicalized.

;;

37. Completion Condition

CR-ES-003 is complete when Enterprise-Semantics can represent a Value Stream independently of its implementation and can formally distinguish:

Value Stream
       |
       ├── Value Stage
       |
       ├── Capability
       |
       ├── Process
       |
       ├── Activity
       |
       ├── Task
       |
       ├── Workflow
       |
       ├── Service
       |
       ├── System
       |
       ├── Outcome
       |
       |--── Stakeholder Value

The semantic authority must be able to answer:

What is the value journey?

Who is the stakeholder?

What initiates it?

What stages constitute it?

What value is being realized?

What outcomes are produced?

What capabilities enable it?

What processes realize it?

What execution mechanisms implement those processes?

without collapsing these concepts into one another.

;;

38. Architectural Result

The resulting semantic architecture shall be:

                    ENTERPRISE VALUE REALIZATION
                              |
                              v
                       ┌──────────────┐
                       | Value Stream |
                       |--──────┬───────┘
                              |
                 contains     |
                              v
                       ┌──────────────┐
                       | Value Stage  |
                       |--──────┬───────┘
                              |
                ┌─────────────┼──────────────┐
                |             |              |
                v             v              v
           Capability      Process        Service
                |             |
                |             v
                |          Activity
                |             |
                |             v
                |            Task
                |             |
                |             v
                |          Workflow
                |
                |--─────────────┐
                              v
                           Outcome
                              |
                              v
                     Stakeholder Value

The model establishes value progression above execution.

That distinction is the principal architectural purpose of CR-ES-003.

;;

39. Next Governed Change

Following successful completion of CR-ES-003, the next governed artifact is:

ADR-ES-004 : Agentic Semantic Grounding

ADR-ES-004 shall first establish the foundational semantics of:

* Agent;
* Agentic;
* Agentic Flow;
* Agentic Workflow;
* Agentic Operations;

before introducing Agentic Value Stream itself.

The subsequent sequence shall therefore remain:

ADR-ES-003
Value Stream
     |
     v
CR-ES-003
Value Stream implementation
     |
     v
ADR-ES-004
Agentic Semantic Grounding
     |
     v
CR-ES-004
Agentic implementation
     |
     v
ADR-ES-005
Agentic Value Stream Semantic Grounding
     |
     v
CR-ES-005
Agentic Value Stream implementation

This sequencing ensures that Agentic Value Stream is a semantically grounded specialization of Value Stream rather than an independently invented parallel concept.

<!--
Authored by: Emmanuel A. Otchere (cardinal author rule, 2026-09-23)
-->
