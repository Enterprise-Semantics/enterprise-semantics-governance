CR-ES-004 : Agentic Semantic Grounding

Status: Accepted (promoted from Proposed on 2026-09-23 per user directive message 1552262422398767115 ;;; "Proceed with everything")
Change Type: Foundational Semantic Grounding
Priority: P0 ; Foundational Enterprise Concept
Related ADR: ADR-ES-004 ; Agentic Semantic Grounding
Depends On: CR-ES-001, CR-ES-002, CR-ES-003
Target Release: Enterprise-Semantics v0.3.0

;;;

1. Objective

Implement ADR-ES-004 and establish the foundational semantic infrastructure required to represent Agentic behavior within Enterprise-Semantics.

This CR shall establish:

* Agent;
* Agentic;
* delegated Intent;
* Authority;
* Action;
* agentic decision/action selection;
* agentic execution;
* contextual adaptation;
* Outcome orientation;
* semantic boundaries between Agentic, Automation, AI, and Autonomous;
* foundations for Agentic Workflow;
* foundations for Agentic Operations;
* foundations for Agentic Value Stream.

This CR does not establish Agentic Value Stream as a canonical specialization.

;;;

2. Scope

2.1 In Scope

* Agent semantic concept;
* Agentic semantic property;
* Intent;
* Authority;
* Action;
* Agent relationships;
* Agentic behavior characteristics;
* agentic decision boundary;
* AI Agent mapping;
* Agentic Workflow boundary;
* Agentic Operations boundary;
* Value Stream integration boundary;
* WSF grounding;
* OpenDEA correspondence;
* documentation;
* examples;
* conformance validation.

;;;

3. Out of Scope

Explicitly excluded:

* Agentic Value Stream;
* Autonomous Value Stream;
* Autonomous Agent;
* Autonomous Enterprise;
* Autonomous Operations;
* Agentic Workflow as a canonical specialization;
* Agentic Operations as a canonical specialization;
* AI model semantics;
* LLM semantics;
* vendor-specific agent frameworks;
* implementation technology standards;
* OpenDEA metamodel changes;
* WSF modifications.

;;;

4. Concept Representation

Add:

enterprise-semantics/
|---- concepts/
| |---- agent.yaml
| |---- agentic.yaml
| |---- intent.yaml
| |---- authority.yaml
| |---- action.yaml

;;;

5. Agent Schema

Implement:

id:
name: Agent
definition: >
 An Entity capable of interpreting delegated intent,
 selecting or coordinating actions, and acting within
 defined authority toward an intended outcome.
semantic_type: Agent
status:
relationships: []
grounding:
 wsf:
 enterprise_semantics:
 opendea:
provenance:
 adr:
 cr:
version:

;;;

6. Agentic Schema

Agentic shall be represented as a semantic property/mode rather than automatically as a universal Entity subclass.

id:
name: Agentic
definition: >
 A mode of operation in which an Agent interprets a delegated
 objective or intent, determines or selects actions within
 defined authority, and acts or coordinates actions toward
 an intended outcome.
semantic_type: SemanticProperty
status:
characteristics:
 - delegated-intent
 - contextual-interpretation
 - action-selection
 - bounded-authority
 - outcome-orientation
 - contextual-adaptation
provenance:
 adr:
 cr:
version:

;;;

7. Intent

Establish the semantic representation required for delegated objectives.

id:
name: Intent
definition: >
 A communicated or established desired direction, purpose,
 or intended result that guides action.
semantic_type: Intent

Intent shall remain distinct from:

* Goal;
* Requirement;
* Instruction;
* Policy;
* Action.

The exact semantic relationship among these concepts may be refined by subsequent governance.

;;;

8. Authority

Establish:

id:
name: Authority
definition: >
 A defined scope of permitted action or decision assigned
 to an Entity within a specified context.

Authority shall support:

* action permissions;
* decision boundaries;
* resource boundaries;
* escalation conditions;
* constraints.

;;;

9. Action

Establish:

id:
name: Action
definition: >
 An intentional act performed or initiated by an Entity
 toward an intended result.

Action shall remain distinct from:

* Process;
* Activity;
* Task;
* Workflow.

Action is the semantic unit required to describe agentic action selection.

;;;

10. Core Relationships

Add:

Subject	Predicate	Object
Agent	interprets	Intent
Agent	pursues	Goal
Agent	acts-within	Authority
Agent	selects	Action
Agent	coordinates	Action
Agent	produces	Outcome
Agent	adapts-to	Context
Agent	receives	Intent
Authority	constrains	Action
Intent	guides	Action
Action	produces	Outcome

All predicates shall be added to the canonical relationship vocabulary.

;;;

11. Agentic Execution Pattern

Implement the following semantic pattern:

Intent
 |
 v
Agent
 |
 |---- interprets Context
 |
 |---- operates within Authority
 |
 |---- selects Action
 |
 |---- coordinates Action
 |
 |---- adapts to Context
 |
 v
 Outcome

The model shall not require any specific AI technology.

;;;

12. Agentic Boundary

An execution instance shall be considered agentic only where the relevant semantic characteristics are present.

The test shall distinguish:

Conventional automation

Trigger
 v
Predefined Rule
 v
Predefined Action

from:

Agentic operation

Delegated Intent
 v
Context
 v
Interpretation
 v
Action Selection
 v
Execution
 v
Outcome
 ↺
Contextual Adaptation

The second pattern represents the foundational agentic semantic.

;;;

13. Agentic and AI Boundary

The implementation shall explicitly support:

AI System
 |
 |---- may be agentic
 |---- may not be agentic

and:

Agent
 |
 |---- may use AI

The test suite shall reject any schema rule that makes:

AI = Agent

or:

AI = Agentic

;;;

14. Agentic and Autonomous Boundary

The implementation shall explicitly support:

Agentic
 |
 |---- may operate with limited autonomy

but shall not infer:

Agentic → Autonomous

as a semantic identity.

Autonomy shall require a separate governed semantic definition.

;;;

15. Agentic Workflow Boundary

Create a documented boundary:

Workflow
 |
 |---- conventional execution
 |
 |---- may be realized agentically

Do not yet create:

AgenticWorkflow

as a canonical semantic concept.

The implementation shall reserve the semantic extension point for ADR-ES-006.

;;;

16. Agentic Operations Boundary

Document:

Operations
 |
 |---- may be performed agentically

without promoting Agentic Operations to canonical status.

The implementation shall establish the mapping boundary needed by ADR-ES-007.

;;;

17. Value Stream Boundary

The existing Value Stream semantic shall be referenced.

The implementation shall allow:

Value Stream
 |
 |---- uses / involves --> Agent

only as a preparatory semantic relationship.

The implementation shall not establish:

Agentic Value Stream

as a canonical concept.

That belongs to CR-ES-005.

;;;

18. AI Agent Correspondence

The mapping layer shall support:

Agent
 |
 |---- specialized implementation/context --> AI Agent

where appropriate.

AI Agent shall not be promoted to a foundational Enterprise-Semantics concept unless separately governed.

;;;

19. WSF Mapping

Create:

enterprise-semantics-mappings/wsf/agentic.yaml

The mapping shall identify:

* relevant WSF concepts;
* grounding status;
* semantic correspondence;
* confidence;
* provenance;
* governing ADR;
* governing CR.

No WSF modification is authorized.

;;;

20. OpenDEA Mapping

Create:

enterprise-semantics-mappings/opendea/agentic.yaml

The mapping shall establish correspondence without modifying the OpenDEA metamodel.

;;;

21. Registry

Register:

AGENT
AGENTIC
INTENT
AUTHORITY
ACTION

with appropriate semantic types and lifecycle states.

No downstream specialized concepts shall be promoted through this registry change.

;;;

22. Profiles

Update the Agentic profile:

enterprise-semantics/profiles/agentic/

with:

id: ES:PROFILE:AGENTIC
name: Agentic
scope:
 - Agent
 - Agentic
 - Intent
 - Authority
 - Action

The profile remains organizational metadata, not an ontology.

;;;

23. Documentation

Add:

enterprise-semantics-docs/
|---- concepts/
| |---- agent.md
| |---- agentic.md
| |---- intent.md
| |---- authority.md
| |---- action.md
|
|---- architecture/
| |---- agentic-boundary.md
| |---- agentic-autonomous-boundary.md
| |---- agentic-execution-boundary.md
|
|---- relationships/
 |---- agentic-relationships.md

Documentation shall explicitly explain:

* Agent;
* Agentic;
* AI Agent;
* Automation;
* Autonomous;
* Workflow;
* Agentic Workflow boundary;
* Operations;
* Agentic Operations boundary;
* Value Stream;
* Agentic Value Stream boundary.

;;;

24. Worked Example

Use OTCHERE Inc.

Illustrative:

OTCHERE Inc
 |
 |---- delegates Intent
 |
 v
 Customer Service Agent
 |
 |---- interprets customer context
 |
 |---- operates within authority
 |
 |---- selects response action
 |
 |---- invokes permitted service
 |
 |---- pursues resolution
 |
 v
 Customer Outcome

The example must demonstrate that:

* the Agent has delegated intent;
* authority is bounded;
* actions are selected;
* outcome is pursued;
* human escalation remains possible.

;;;

25. Relationship Validation

The test probe shall verify:

Agent → interprets → Intent
Agent → acts-within → Authority
Agent → selects → Action
Agent → produces → Outcome
Authority → constrains → Action
Intent → guides → Action

References must resolve.

;;;

26. Conformance Rules

AG-CON-001

Agent must have a definition.

AG-CON-002

Agentic must have a definition.

AG-CON-003

Agentic must identify its semantic characteristics.

AG-CON-004

Agentic must not be defined as AI.

AG-CON-005

Agentic must not be defined as Automation.

AG-CON-006

Agentic must not be defined as Autonomous.

AG-CON-007

Agent must have an authority relationship when modeled as acting agentically.

AG-CON-008

Agentic execution must have an intent or objective.

AG-CON-009

Agentic execution must support action selection.

AG-CON-010

Agentic execution must be outcome-oriented.

AG-CON-011

Agentic Value Stream must not be canonicalized by this CR.

AG-CON-012

Agentic Workflow must not be canonicalized by this CR.

AG-CON-013

Autonomous concepts must not be canonicalized by this CR.

;;;

27. Negative Tests

The following must fail semantic validation:

AI is-a Agent

when intended as a universal identity.

Agentic is-a Autonomous
Automation is-a Agentic
Agentic Value Stream is established by CR-ES-004
Agentic Workflow is established by CR-ES-004

These constructs require explicit semantic governance.

;;;

28. Visuals

Add:

enterprise-semantics-visuals/
|---- concepts/
| |---- agentic.puml
| |---- agentic-boundary.puml
| |---- agentic-autonomous-boundary.puml
|
|---- relationships/
 |---- agentic-relationships.puml

Primary conceptual visualization:

 Delegated Intent
 |
 v
 ┌-----------┐
 | Agent |
 |-------┬-----┘
 |
 ┌---------┼---------┐
 v v v
 Context Authority Goal
 | | |
 |-----------┼---------┘
 v
 Action Selection
 |
 v
 Action
 |
 v
 Outcome
 ▲
 |
 Adapt to Context

;;;

29. Versioning

This CR establishes:

Enterprise-Semantics v0.3.0

The release represents foundational Agentic semantic infrastructure.

It does not represent:

* an AI architecture;
* a mature agent model;
* an autonomous enterprise model;
* an Agentic Value Stream model.

;;;

30. CI Pipeline

Extend CI:

Schema
 v
Identifier
 v
Reference
 v
Relationship
 v
Lifecycle
 v
Provenance
 v
Agentic Boundary
 v
AI Boundary
 v
Autonomy Boundary
 v
Governance Traceability
 v
Conformance

;;;

31. Acceptance Criteria

CR-ES-004 is complete when:

* [ ]	Agent concept is implemented.
* [ ]	Agentic semantic property is implemented.
* [ ]	Intent is implemented.
* [ ]	Authority is implemented.
* [ ]	Action is implemented.
* [ ]	Agent relationships are implemented.
* [ ]	delegated intent is represented.
* [ ]	authority boundary is represented.
* [ ]	action selection is represented.
* [ ]	contextual adaptation is represented.
* [ ]	outcome orientation is represented.
* [ ]	AI/Agent distinction is validated.
* [ ]	Automation/Agentic distinction is validated.
* [ ]	Agentic/Autonomous distinction is validated.
* [ ]	Workflow boundary is documented.
* [ ]	Value Stream boundary is documented.
* [ ]	WSF mapping is recorded.
* [ ]	OpenDEA mapping is recorded.
* [ ]	Agentic profile is updated.
* [ ]	documentation is published.
* [ ]	OTCHERE Inc example is published.
* [ ]	visual source is published.
* [ ]	conformance tests pass.
* [ ]	no Agentic Value Stream semantics are canonicalized.
* [ ]	no Autonomous semantics are canonicalized.

;;;

32. Completion Condition

CR-ES-004 is complete when Enterprise-Semantics can formally represent:

Intent
 v
Agent
 v
Authority
 v
Action Selection
 v
Action
 v
Outcome

while distinguishing the resulting behavior from:

Automation
AI
Autonomy
Workflow

and while providing the semantic foundation required for:

Agentic Workflow
Agentic Operations
Agentic Value Stream

without prematurely defining those concepts.

;;;

33. Next Governed Change

The next governed pair shall be:

ADR-ES-005 ; Agentic Value Stream Semantic Grounding

followed by:

CR-ES-005 ; Agentic Value Stream Semantic Grounding

ADR-ES-005 will combine the two semantic foundations now established:

ADR-ES-003
Value Stream
 +
ADR-ES-004
Agentic
 v
ADR-ES-005
Agentic Value Stream

The resulting specialization must preserve the end-to-end value semantics of Value Stream while introducing agentic participation as a meaningful property of value-stream realization.

;;

34. Acceptance

This CR was promoted from Proposed to Accepted on 2026-09-23 per user directive message 1552262422398767115. The promotion ritual per ADR-ES-001 §10-§11 (body Status field + this §34 Acceptance section, with the cardinal author footer preserved) was executed in concert with the ADR-ES-004 promotion.

The promotion to Accepted has the following consequences:

* All 24 acceptance criteria of §31 are satisfied via 7 PRs across 6 repos (PR #7 + PR #8 + PR #9 enterprise-semantics ;;; PR #4 enterprise-semantics-mappings ;;; PR #3 enterprise-semantics-docs ;;; PR #3 enterprise-semantics-examples ;;; PR #3 enterprise-semantics-test-probe ;;; PR #3 enterprise-semantics-visuals).
* The 5 concept records (Agent + Agentic + Intent + Authority + Action) are canonical at Candidate lifecycle.
* The 11 governed predicates from §10 are registered in relationships/vocabulary.yaml v0.4.0.
* The 11 inverse pairs from §10 are registered in relationships/inverse.yaml v0.4.0.
* The 2 mapping records (WSF + OpenDEA per §19 + §20) are PROPOSED.
* The 9 documentation files (per §23) are published in enterprise-semantics-docs.
* The 1 OTCHERE Inc example (per §24) is published in enterprise-semantics-examples.
* The 9 test files + 13 AG-CON rules + 5 negative tests (per §26 + §27) are published in enterprise-semantics-test-probe.
* The 3 PlantUML sources (per §28) are published in enterprise-semantics-visuals.
* The Agentic Profile (ES:PROFILE:AGENTIC) per §22 is landed at v0.1.0 ;; Candidate in enterprise-semantics/profiles/agentic/.
* Enterprise-Semantics v0.3.0 is the canonical version pointer (per §29) ;; ratifies the Agentic semantic establishment.
* v0.4.0 of relationships/vocabulary.yaml is the canonical predicate vocabulary version (per §9 + §10).
* No Agentic Value Stream semantics are canonicalized (per §3 + §17 + AG-CON-011).
* No Autonomous semantics are established (per §3 + §14 + AG-INV-003 + AG-INV-010 + AG-CON-013).
* No AI model / LLM / vendor-specific agent framework semantics are introduced (per §3 + §19).
* No OpenDEA metamodel change has been made (per §3 + §20).
* No WSF modification has been made (per §3 + §19 + FND-ES-AG-008 §1.3).

The next governed change is ADR-ES-005 + CR-ES-005 (Agentic Value Stream Semantic Grounding), which will combine ADR-ES-003 (Value Stream) + ADR-ES-004 (Agentic) to establish the Agentic Value Stream specialization.

Promoted by: Emmanuel A. Otchere (cardinal author rule, 2026-09-23) per ADR-ES-001 §10-§11 promotion ritual.

<!--
Authored by: Emmanuel A. Otchere (cardinal author rule, 2026-09-23)
Promoted by: Emmanuel A. Otchere (cardinal author rule, 2026-09-23) per ADR-ES-001 §10-§11 promotion ritual
-->
