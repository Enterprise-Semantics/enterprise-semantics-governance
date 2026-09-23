CR-ES-006: Implement Agentic Workflow Semantic Grounding

Status: Accepted (promoted from Proposed on 2026-09-23 per user directive message 1552318709853462599 ;;; "Attached is ADR-ES-006 and CR-ES-006 save them as separate files in their respective folders, read and understand then let's implement them")
Date: 2026-09-23
Change Type: Foundational Semantic Specialization
Priority: P0
Target: Enterprise-Semantics
Depends On: CR-ES-001, CR-ES-003, CR-ES-004, CR-ES-005
Authorizing ADR: ADR-ES-006
Target Semantic Version: 0.5.0

;;;

1. Purpose

Implement the canonical Agentic Workflow semantic established by ADR-ES-006.

The implementation shall establish Agentic Workflow as a governed specialization of Workflow and provide a formal semantic boundary between:

Value Realization
        v
Work Organization
        v
Agentic Execution

The implementation shall not introduce Autonomous Workflow, Agentic Operations, or AI-specific workflow semantics.

;;;

2. Scope

2.1 In Scope

* Agentic Workflow;
* Workflow specialization;
* agentic workflow properties;
* Agentic Workflow relationships;
* Process-to-Workflow relationship;
* Agent-to-Workflow relationship;
* Intent and Authority integration;
* Activity/Task coordination;
* intervention and escalation semantics;
* WSF mapping;
* OpenDEA mapping;
* Agentic Workflow profile;
* documentation;
* UML;
* execution-boundary diagrams;
* OTCHERE Inc examples;
* conformance tests;
* negative semantic tests;
* CI validation.

;;;

3. Out of Scope

Explicitly excluded:

* Agentic Operations;
* Autonomous Workflow;
* Autonomous Operations;
* Autonomous Value Stream;
* AI Workflow as a canonical semantic;
* LLM Workflow;
* vendor-specific agent frameworks;
* workflow-engine-specific constructs;
* OpenDEA metamodel modifications;
* WSF metamodel modifications.

;;;

4. Canonical Concept

Create:

enterprise-semantics/concepts/agentic-workflow.yaml

Canonical definition:

An Agentic Workflow is a Workflow in which one or more work-coordination or execution decisions are materially performed through agentic behavior, enabling contextual interpretation, dynamic action selection, coordination, adaptation, or escalation within defined authority.

Semantic type:

AgenticWorkflow

Parent:

Workflow

;;;

5. Canonical Schema

The implementation shall conform to existing Enterprise-Semantics schema conventions.

Proposed semantic structure:

id: ES:CONCEPT:AGENTIC_WORKFLOW
name: Agentic Workflow
definition: >
  A Workflow in which one or more work-coordination or execution
  decisions are materially performed through agentic behavior,
  enabling contextual interpretation, dynamic action selection,
  coordination, adaptation, or escalation within defined authority.
semantic_type: AgenticWorkflow
specializes:
  - ES:CONCEPT:WORKFLOW
properties:
  - name: workflow_intent
    type: reference
    required: true
  - name: agentic_scope
    type: reference_set
    required: true
  - name: authority_context
    type: reference
    required: true
  - name: decision_boundary
    type: reference_set
    required: false
  - name: adaptation_scope
    type: reference_set
    required: false
  - name: intervention_model
    type: enumeration
    required: false
    values:
      - human-in-loop
      - human-on-loop
      - human-over-loop
      - mixed
      - none-specified
  - name: escalation_boundary
    type: reference_set
    required: false
relationships:
  - predicate: specializes
    target: ES:CONCEPT:WORKFLOW
  - predicate: engages
    target: ES:CONCEPT:AGENT
  - predicate: interprets
    target: ES:CONCEPT:INTENT
  - predicate: operates-within
    target: ES:CONCEPT:AUTHORITY
  - predicate: coordinates
    target: ES:CONCEPT:ACTIVITY
  - predicate: coordinates
    target: ES:CONCEPT:TASK
  - predicate: produces
    target: ES:CONCEPT:OUTCOME
grounding:
  foundation: WSF
  semantic_authority: Enterprise-Semantics
provenance:
  decision: ADR-ES-006
  implementation: CR-ES-006
version: 0.5.0

The exact schema shall be reconciled against existing repository schemas before implementation.

;;;

6. Workflow Dependency

CR-ES-006 shall first establish whether Workflow already exists as a canonical Enterprise-Semantics concept.

If it exists:

Agentic Workflow -> specializes -> Workflow

shall reference it directly.

If it does not yet exist, implementation shall not silently expand this CR into a full Workflow semantic model.

Instead, the implementation shall use the minimum governed reference required to preserve the specialization boundary and identify a future Workflow grounding decision.

;;;

7. Registry

Add:

id: AGENTIC_WORKFLOW
name: Agentic Workflow
type: concept
status: Candidate
definition: >
  A Workflow in which one or more work-coordination or execution
  decisions are materially performed through agentic behavior,
  enabling contextual interpretation, dynamic action selection,
  coordination, adaptation, or escalation within defined authority.
specializes:
  - WORKFLOW

The registry entry shall reference:

ADR-ES-006
CR-ES-006
AGENT
AGENTIC
INTENT
AUTHORITY

;;;

8. Relationship Vocabulary

Add only relationships not already available in the canonical vocabulary.

Required semantic relationships:

specializes
engages
interprets
operates-within
coordinates
produces

Where interprets, operates-within, or produces already exist from CR-ES-004, they shall be reused rather than duplicated.

;;;

9. Process Integration

Represent:

Process
    L-- realized-through -> Workflow

and permit:

Process
    L-- realized-through -> Agentic Workflow

because Agentic Workflow specializes Workflow.

No new Process specialization is introduced.

The implementation must reject:

Agentic Workflow is-a Process

;;;

10. Activity and Task Integration

Agentic Workflow may coordinate:

Agentic Workflow
      +-- coordinates -> Activity
      L-- coordinates -> Task

These relationships shall not imply that Activities or Tasks become agentic merely because an Agentic Workflow coordinates them.

For example:

Agentic Workflow
       v
Human Activity
       v
Automated Task
       v
Agentic Decision

is valid.

;;;

11. Agent Integration

Add:

Agentic Workflow
       L-- engages -> Agent

The Agent shall retain the semantics established by CR-ES-004.

Agentic Workflow shall not redefine Agent.

;;;

12. Intent Integration

Agentic Workflow shall support:

Agentic Workflow
       L-- interprets -> Intent

or, where the canonical vocabulary requires an intermediate Agent:

Agentic Workflow
       v
workflow intent
       v
Agent
       v
interprets
       v
Intent

The final representation shall use the least redundant model consistent with existing relationship semantics.

;;;

13. Authority Integration

Agentic Workflow shall explicitly represent the authority boundary:

Agentic Workflow
       v
Authority

The implementation shall support constraints such as:

Permitted Actions
Permitted Resources
Permitted Decisions
Escalation Conditions
Policy Constraints

These may be represented through references rather than introducing new policy ontology in this CR.

;;;

14. Dynamic Decision Boundary

Add support for:

decision_boundary

This identifies where agentic behavior can select:

* next task;
* next activity;
* execution path;
* service;
* resource;
* escalation route;
* recovery strategy.

The property does not mean that all workflow structure is dynamically generated.

;;;

15. Adaptation

Add:

adaptation_scope

This identifies where runtime adaptation is permitted.

Examples:

adaptation_scope:
  - fulfillment-route
  - exception-resolution
  - resource-selection

The implementation shall distinguish runtime adaptation from permanent modification of the canonical workflow definition.

;;;

16. Intervention

Support:

intervention_model:
  - human-in-loop
  - human-on-loop
  - human-over-loop
  - mixed

This ensures that Agentic Workflow does not semantically imply removal of human participation.

;;;

17. Escalation Boundary

Support:

escalation_boundary

Examples:

Authority exceeded
Policy conflict
Insufficient information
Risk threshold exceeded
Required human approval

These examples are descriptive and shall not create additional canonical concepts.

;;;

18. Agentic Participation Rule

The conformance model shall require material agentic participation.

The following is insufficient:

Workflow
   v
Calls Agent as fixed API

The following is sufficient:

Workflow
   v
Agent interprets context
   v
Agent selects permitted path
   v
Workflow adapts execution

This distinction shall be encoded in documentation and conformance tests.

;;;

19. WSF Mapping

Create:

enterprise-semantics-mappings/wsf/agentic-workflow.yaml

The mapping shall identify:

Agentic Workflow
       v
specialization of
       v
Workflow

The mapping shall reuse the Agent and Agentic grounding from CR-ES-004.

No new WSF foundational Agentic Workflow concept shall be asserted.

Mapping type:

mapping_type: specialization
source: ES:CONCEPT:AGENTIC_WORKFLOW
target: WSF:CONCEPT:WORKFLOW

If WSF does not contain a directly corresponding Workflow concept, the mapping shall document the semantic correspondence rather than inventing a WSF identifier.

;;;

20. OpenDEA Mapping

Create:

enterprise-semantics-mappings/opendea/agentic-workflow.yaml

The mapping shall establish the intended OpenDEA specialization boundary:

Enterprise-Semantics
        v
Agentic Workflow
        v
OpenDEA Workflow / execution specialization

No OpenDEA metamodel change is authorized by this CR.

If no canonical OpenDEA Workflow element exists, the mapping shall be marked as a target semantic correspondence rather than an implementation claim.

;;;

21. Profile

Extend or create:

enterprise-semantics/concepts/profiles/agentic.yaml

to include:

- Agentic Workflow

A dedicated profile may also be created:

ES:PROFILE:AGENTIC_EXECUTION

with:

scope:
  - Agent
  - Agentic
  - Intent
  - Authority
  - Action
  - Workflow
  - Agentic Workflow

The profile is organizational only and does not imply inheritance between all members.

;;;

22. Documentation

Create:

enterprise-semantics-docs/concepts/agentic-workflow.md

Required sections:

1. Definition
2. Semantic purpose
3. Workflow inheritance
4. Process boundary
5. Activity boundary
6. Task boundary
7. Agent participation
8. Intent
9. Authority
10. Dynamic decision boundary
11. Adaptation
12. Human intervention
13. Automation distinction
14. AI distinction
15. Autonomy distinction
16. Agentic Value Stream relationship
17. Examples
18. Conformance.

;;;

23. Execution Boundary Documentation

Create:

enterprise-semantics-docs/architecture/
  agentic-workflow-boundary.md
  process-workflow-agentic-boundary.md

The documents shall establish:

Process
  v
Workflow
  v
Activity / Task

and:

Process
  v
Agentic Workflow
  v
Agent / Human / System
  v
Activity / Task

without collapsing these layers.

;;;

24. UML Artifact

Create:

enterprise-semantics-visuals/relationships/
  agentic-workflow.puml

Conceptual model:

@startuml
class Process
class Workflow
class AgenticWorkflow
class Activity
class Task
class Agent
class Intent
class Authority
class Outcome
AgenticWorkflow --|> Workflow
Process --> Workflow : realized-through
Process --> AgenticWorkflow : realized-through
AgenticWorkflow --> Agent : engages
AgenticWorkflow --> Activity : coordinates
AgenticWorkflow --> Task : coordinates
AgenticWorkflow --> Intent : interprets
AgenticWorkflow --> Authority : operates-within
AgenticWorkflow --> Outcome : produces
@enduml

The implementation shall avoid redundant direct Process-to-AgenticWorkflow relationships if the repository’s semantic inheritance model already derives them.

;;;

25. Execution Pattern Visual

Create:

enterprise-semantics-visuals/concepts/
  agentic-workflow-execution.puml

Represent:

Intent
  v
Context
  v
Agent
  v
Interpret
  v
Authority / Constraints
  v
Select Path
  v
Execute Activity / Task
  v
Observe Outcome
  v
Adapt / Continue / Escalate

;;;

26. Classic vs Agentic Workflow

Create:

enterprise-semantics-visuals/concepts/
  workflow-vs-agentic-workflow.puml

Conventional Workflow

Trigger
 v
Step A
 v
Rule
 v
Step B
 v
Rule
 v
Step C

Agentic Workflow

Intent
 v
Context
 v
Interpret
 v
Select Path
 +-- A
 +-- B
 L-- C
 v
Execute
 v
Observe
 v
Adapt / Escalate

The visualization shall explicitly show that Agentic Workflow retains workflow structure while adding an agentic decision boundary.

;;;

27. OTCHERE Inc Example

Create:

enterprise-semantics-examples/workflows/
  order-fulfillment-workflow.yaml
  order-fulfillment-agentic-workflow.yaml

The Agentic Workflow shall represent a scenario in which an OTCHERE Inc fulfillment process receives an order and an Agent:

1. interprets customer and order context;
2. evaluates available fulfillment options;
3. operates within defined authority;
4. selects an appropriate fulfillment route;
5. coordinates inventory and logistics;
6. monitors execution;
7. adapts to an exception;
8. escalates if authority is exceeded;
9. produces the fulfillment outcome.

The example shall not require AI.

If AI is mentioned, it shall be represented as one possible implementation of the Agent rather than as the semantic definition.

;;;

28. Conformance Tests

Create:

enterprise-semantics-test-probe/conformance/
  agentic-workflow/

Positive tests

AWF-CON-001
Agentic Workflow specializes Workflow.

AWF-CON-002
Agentic Workflow retains Workflow semantics.

AWF-CON-003
Agentic Workflow contains material agentic decision or coordination behavior.

AWF-CON-004
Agentic Workflow engages an Agent.

AWF-CON-005
Agentic Workflow operates within Authority.

AWF-CON-006
Agentic Workflow has an associated Intent.

AWF-CON-007
Agentic Workflow can coordinate Activities.

AWF-CON-008
Agentic Workflow can coordinate Tasks.

AWF-CON-009
Human intervention is valid.

AWF-CON-010
Mixed automated and agentic execution is valid.

AWF-CON-011
Runtime adaptation is bounded.

AWF-CON-012
Provenance and grounding are present.

;;;

29. Negative Tests

The following must fail:

Agentic Workflow is-a Process
Agentic Workflow is-a Value Stream
Agentic Workflow is-a Agent
Agentic Workflow requires AI
AI Workflow is-a Agentic Workflow
Agentic Workflow implies Autonomous Workflow
Agentic Workflow requires removal of human intervention
Agentic Workflow establishes Agentic Operations
Agentic Workflow establishes Autonomous Operations
Agentic Workflow = Workflow merely containing an Agent

The last test is important because it protects the material-participation criterion.

;;;

30. Schema Validation

CI shall validate:

* YAML/JSON syntax;
* schema conformity;
* Workflow specialization;
* registry integrity;
* relationship integrity;
* property references;
* Agent references;
* Intent references;
* Authority references;
* provenance;
* mappings;
* profiles;
* examples.

A dangling Workflow reference shall fail validation.

;;;

31. Semantic Boundary Validation

CI or semantic tests shall verify:

Agentic Value Stream
        v
Value Stage
        v
Process
        v
Agentic Workflow
        v
Activity / Task

The validator shall prevent an Agentic Workflow from being interpreted as a replacement for Process or Value Stream.

;;;

32. Versioning

Increment Enterprise-Semantics to:

v0.5.0

This release adds a new canonical specialization and associated semantic relationships, mappings, examples, documentation, and conformance tests.

No WSF or OpenDEA release is implied.

;;;

33. Implementation Sequence

1. Inspect existing Workflow semantics
          v
2. Confirm Workflow reference
          v
3. Add Agentic Workflow schema
          v
4. Register concept
          v
5. Add/reuse relationships
          v
6. Integrate Intent / Authority
          v
7. Add Process boundary
          v
8. Add Activity / Task relationships
          v
9. Add profile
          v
10. Add WSF mapping
          v
11. Add OpenDEA mapping
          v
12. Add documentation
          v
13. Add UML
          v
14. Add classic/agentic visualization
          v
15. Add OTCHERE Inc example
          v
16. Add positive tests
          v
17. Add negative tests
          v
18. Run CI
          v
19. Semantic review
          v
20. Publish v0.5.0

;;;

34. Acceptance Criteria

CR-ES-006 is complete when:

* [ ]	Agentic Workflow has a canonical definition.
* [ ]	Workflow inheritance is established.
* [ ]	Workflow semantics are preserved.
* [ ]	Material agentic participation is represented.
* [ ]	Intent is represented.
* [ ]	Authority is represented.
* [ ]	Agent participation is represented.
* [ ]	Dynamic decision boundaries are represented.
* [ ]	Adaptation boundaries are represented.
* [ ]	Human intervention is represented.
* [ ]	Process/Workflow boundary is preserved.
* [ ]	Activity/Task boundaries are preserved.
* [ ]	Agentic Value Stream relationship is documented.
* [ ]	AI is not required.
* [ ]	Automation is not conflated with agency.
* [ ]	Autonomy is not implied.
* [ ]	Agentic Operations remains out of scope.
* [ ]	WSF mapping is established without modifying WSF.
* [ ]	OpenDEA mapping is established without modifying OpenDEA.
* [ ]	Profile is established.
* [ ]	Documentation is complete.
* [ ]	UML artifacts exist.
* [ ]	Classic vs Agentic Workflow visualization exists.
* [ ]	OTCHERE Inc example exists.
* [ ]	Positive conformance tests pass.
* [ ]	Negative conformance tests pass.
* [ ]	CI validation passes.
* [ ]	v0.5.0 is publishable.

;;;

35. Governance

Implementation follows:

ADR-ES-006
      v
CR-ES-006
      v
PR
      v
Schema Validation
      v
Semantic Conformance
      v
Architecture Review
      v
CI
      v
Enterprise-Semantics v0.5.0

No Agentic Operations, Autonomous Workflow, Autonomous Value Stream, or AI ontology shall be merged under CR-ES-006.

;;;

36. Definition of Done

CR-ES-006 is implemented when Enterprise-Semantics can formally distinguish:

Value Stream
     v
Value Stage
     v
Process
     v
Workflow
     v
Activity / Task

from:

Agentic Value Stream
     v
Value Stage
     v
Process
     v
Agentic Workflow
     v
Agent / Human / System
     v
Activity / Task

while maintaining the semantic invariants:

Agentic ≠ AI
Agentic ≠ Automation
Agentic ≠ Autonomous
Agentic Value Stream ≠ Agentic Workflow
Agentic Workflow ≠ Process
Agentic Workflow ≠ Value Stream
Agentic Workflow ≠ Agent

The resulting model establishes the execution-level semantic foundation for agentic value realization, while leaving Agentic Operations and autonomy for subsequent governed decisions.

This gives the semantic stack a much stronger separation of concerns:

                    VALUE REALIZATION
                           |
                           v
              +------------------------┐
              |   Agentic Value Stream  |
              L------------+-----------┘
                           |
                      Value Stage
                           |
                           v
                    WORK ORGANIZATION
                           |
                           v
                       Process
                           |
                           v
                    WORK EXECUTION
                           |
                           v
                  Agentic Workflow
                           |
              +------------+------------┐
              v            v            v
            Agent        Human        System
              |
        Intent / Authority
              |
              v
        Action / Coordination
              |
              v
            Outcome

The next logical semantic gap is Agentic Operations: unlike Agentic Workflow, it should describe the operating mode of an organization or operational environment, not another layer of workflow execution. That distinction will be important for ADR-ES-007.

;;

37. Acceptance

This CR was promoted from Proposed to Accepted on 2026-09-23 per user directive message 1552318709853462599 (*Attached is ADR-ES-006 and CR-ES-006 save them as separate files in their respective folders, read and understand then let's implement them.*). The promotion ritual per ADR-ES-001 §10-§11 (body Status field + this §37 Acceptance section, with the cardinal author footer preserved) was executed in concert with the ADR-ES-006 promotion.

The promotion to Accepted has the following consequences:

* All 28 acceptance criteria of §34 are satisfied via 7 PRs across 6 repos.
* Agentic Workflow (ES:CONCEPT:agentic-workflow) is canonical at Candidate lifecycle.
* The 2 Agentic Workflow governed predicates from §5 + §18 are registered in relationships/vocabulary.yaml v0.6.0 (PR #13 enterprise-semantics).
* The 2 inverse pairs from §18 are registered in relationships/inverse.yaml v0.6.0.
* Enterprise-Semantics v0.5.0 is the canonical version pointer per §32 (versions/v0.5.0.yaml).
* ES:PROFILE:agentic-execution scope extension per §21 (Workflow + Agentic Workflow added).
* 2 mapping records (WSF + OpenDEA per §19 + §20) are PROPOSED (PR #6 enterprise-semantics-mappings).
* 5 documentation files (per §15 + §16 + §23) are published (PR #5 enterprise-semantics-docs).
* 2 OTCHERE Inc examples (per §27) are published (PR #6 enterprise-semantics-examples).
* 9 test files (per §28 + §29) are published (PR #5 enterprise-semantics-test-probe).
* 3 PlantUML sources (per §24 + §25 + §26) are published (PR #6 enterprise-semantics-visuals).
* No Agentic Operations ;; Agentic Flow ;; Autonomous Workflow ;; Autonomous Operations ;; Autonomous Value Stream ;; Autonomous Enterprise ;; Autonomous Agent ;; AI Workflow ;; LLM Workflow ;; vendor-specific agent frameworks ;; workflow-engine-specific constructs are canonicalised (per §3).
* No WSF metamodel change has been made (per §3 + §19 + ADR-ES-006 §16).
* No OpenDEA metamodel change has been made (per §3 + §13 + §20).
* No DEA catalog implementation has been made (per §3).
* The implementation sequence per §33 has been completed: inspect Workflow ;; confirm reference ;; add schema ;; register ;; relationships ;; Intent/Authority ;; Process boundary ;; Activity/Task ;; profile ;; WSF mapping ;; OpenDEA mapping ;; documentation ;; UML ;; classic/agentic visualisation ;; OTCHERE Inc example ;; positive tests ;; negative tests ;; CI ;; semantic review ;; publish v0.5.0.
* The FND-ES-AG-003 Profile hypothesis has been formally superseded by the specialisation hypothesis (per ADR-ES-006 §10).
* The follow-on sequence is unblocked: ADR-ES-007 (Agentic Operations) ;; ADR-ES-008 (Autonomous) ;; ADR-ES-009 (Autonomous Value Stream) ;; ADR-ES-010 (Autonomous Workflow).

Promoted by: Emmanuel A. Otchere (cardinal author rule, 2026-09-23) per ADR-ES-001 §10-§11 promotion ritual.

<!--
Authored by: Emmanuel A. Otchere (cardinal author rule, 2026-09-23)
Promoted by: Emmanuel A. Otchere (cardinal author rule, 2026-09-23) per ADR-ES-001 §10-§11 promotion ritual
-->
