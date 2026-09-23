<!--
ADR-ES-006 ;;; Agentic Workflow Semantic Grounding Decision

Dash-normalized: colons (:) and semicolons (;) used consistently.
Verbatim original: 00_inbox/ADR-ES-006.md (em-dashes and ellipsis dividers preserved in source).

Status: Accepted (promoted from Proposed on 2026-09-23 per user directive message 1552318709853462599 ;;; "Attached is ADR-ES-006 and CR-ES-006 save them as separate files in their respective folders, read and understand then let's implement them")
Decision Type: Foundational Enterprise Semantic Specialization
Scope: Enterprise-Semantics
Supersedes: None
Depends on: ADR-ES-001 (Authority and Publication Architecture) ;;; ADR-ES-003 (Value Stream Semantic Grounding, Accepted 2026-09-23) ;;; ADR-ES-004 (Agentic Semantic Grounding, Accepted 2026-09-23) ;;; ADR-ES-005 (Agentic Value Stream Semantic Grounding, Accepted 2026-09-23) ;;; FND-ES-AG-008 (WSF Tier 1 / Tier 2 Grounding Boundary, Established 2026-09-22)
Related: CR-ES-006 (Agentic Workflow Semantic Grounding, Proposed) ;;; ADR-ES-007 (Agentic Operations, future) ;;; ADR-ES-008 (Autonomous, future) ;;; ADR-ES-009 (Autonomous Value Stream, future) ;;; ADR-ES-010 (Autonomous Workflow, future)

Decision: Establish Agentic Workflow as a specialization of Workflow. Agentic Workflow is a Workflow in which one or more work-coordination or execution decisions are materially performed through agentic behavior, enabling contextual interpretation, dynamic action selection, coordination, adaptation, or escalation within defined authority. Deliberately avoids premature canonicalization of Agentic Operations ;; Autonomous Workflow ;; Autonomous Value Stream ;; Autonomous Operations ;; AI-specific workflow semantics ;; LLM Workflow semantics.

Slot note: this ADR is filed at governance repo docs/adr/0008-... Slot 0008 is the next free slot in the ES series ;; distinct from the ES-AG series at slots 0003 (manny-es). The ES series slot sequence is 0001 (Authority), 0002 (Enterprise Semantic Model), 0003 (Agentic Semantic Decision, ES-AG), 0004 (Capability, ES), 0005 (Value Stream, ES), 0006 (Agentic, ES), 0007 (Agentic Value Stream, ES), 0008 (Agentic Workflow, ES).

Implementation: CR-ES-006 (Agentic Workflow Semantic Grounding). CR-ES-006 is the implementation specification ;; this ADR ratifies it as a governed semantic decision.

Authored by: Emmanuel A. Otchere (cardinal author rule, 2026-09-23)
-->
The next step should establish Agentic Workflow as the execution/coordination semantic that sits below Agentic Value Stream and Process, without allowing it to collapse into either.

The key architectural distinction is:

Agentic Value Stream
        v
Value Stage
        v
Process
        v
Agentic Workflow
        v
Activity / Task execution
        v
Agent / Human / System / Service

This makes Agentic Workflow a realization and coordination construct, whereas Agentic Value Stream remains the value-realization construct.

ADR-ES-006 ; Agentic Workflow Semantic Grounding

Status: Accepted (promoted from Proposed on 2026-09-23 per user directive message 1552318709853462599)
Date: 2026-09-23
Decision Type: Foundational Enterprise Semantic Specialization
Scope: Enterprise-Semantics
Depends On: ADR-ES-001, ADR-ES-003, ADR-ES-004, ADR-ES-005
Implementation: CR-ES-006
Target Semantic Version: 0.5.0

;;;

1. Context

Enterprise-Semantics has established:

* Value Stream as the semantic construct for end-to-end value realization;
* Value Stage as a meaningful transition in that value realization;
* Process as the organized body of work through which value-stage outcomes may be realized;
* Agent as an entity capable of interpreting delegated intent, selecting or coordinating actions, and acting within defined authority;
* Agentic as a mode of operation characterized by delegated intent, contextual interpretation, bounded authority, action selection or coordination, adaptation, and outcome orientation;
* Agentic Value Stream as a Value Stream in which one or more stages are materially realized through agentic behavior.

These decisions establish the value-realization and agentic semantics, but do not yet define the execution construct through which agentic behavior may coordinate work.

A conventional Workflow generally represents an organized sequence, flow, or coordination of work.

An agentic realization requires a related but distinct semantic: a workflow capable of incorporating delegated intent, contextual interpretation, dynamic action selection, agent participation, adaptive routing, or bounded decision-making.

This requires a formal Agentic Workflow concept.

The concept must not become synonymous with:

* Agentic Value Stream;
* Process;
* Activity;
* Task;
* Agentic Operations;
* Automation;
* AI workflow;
* or Autonomous Workflow.

;;;

2. Decision

Enterprise-Semantics establishes Agentic Workflow as a specialization of Workflow.

Canonical definition

An Agentic Workflow is a Workflow in which one or more work-coordination or execution decisions are materially performed through agentic behavior, enabling contextual interpretation, dynamic action selection, coordination, adaptation, or escalation within defined authority.

Formally:

Agentic Workflow
        L-- is a -> Workflow

Agentic Workflow therefore inherits the semantics of Workflow while adding agentic behavior to workflow coordination or execution.

;;;

3. Semantic Principle

The central principle is:

Workflow describes how work is coordinated or executed; Agentic Workflow describes a workflow in which agentic behavior materially participates in that coordination or execution.

Therefore:

VALUE REALIZATION
        |
        v
Value Stream
        |
        v
Value Stage
        |
        v
Process
        |
        v
Workflow
        |
        v
Activity / Task

with an agentic specialization at the workflow layer:

Workflow
    ▲
    | specializes
    |
Agentic Workflow

Agentic Workflow may therefore participate in the realization of a Process without becoming the Process itself.

;;;

4. Agentic Workflow Characteristics

An Agentic Workflow may exhibit:

4.1 Delegated Workflow Intent

The workflow may receive an objective or intent that influences execution.

4.2 Contextual Interpretation

The workflow may interpret runtime context to determine appropriate execution behavior.

4.3 Dynamic Routing

The next work step or execution path may be selected dynamically.

4.4 Agentic Coordination

Agents may coordinate activities, tasks, services, systems, or other agents.

4.5 Adaptive Execution

Workflow behavior may change in response to new information, events, outcomes, or conditions.

4.6 Bounded Decision Authority

Dynamic workflow decisions occur within defined authority, policies, constraints, and escalation boundaries.

4.7 Exception Interpretation

Exceptions may be interpreted and resolved through agentic decision-making rather than only through predefined exception paths.

4.8 Human Intervention

Human approval, intervention, escalation, or oversight may remain part of the workflow.

;;;

5. Workflow Inheritance

Agentic Workflow shall retain the semantic properties of Workflow.

The relationship is:

Agentic Workflow
       |
       L-- specializes -> Workflow

Agentic Workflow shall not redefine Workflow itself.

Where a canonical Workflow concept already exists in Enterprise-Semantics, Agentic Workflow shall reference it.

Where Workflow has not yet been independently grounded as a canonical Enterprise-Semantics concept, the implementation shall establish only the minimum semantic reference necessary to express the specialization and shall not use this ADR to silently create an unrelated Workflow ontology.

;;;

6. Relationship to Process

Process and Workflow remain distinct.

Process
  |
  L-- realized-through -> Workflow

An Agentic Workflow may therefore realize or support a Process:

Process
   |
   L-- realized-through
          v
   Agentic Workflow

This does not imply:

Agentic Workflow is-a Process

That relationship is explicitly invalid.

;;;

7. Relationship to Activity and Task

Agentic Workflow may coordinate the execution of Activities and Tasks.

Agentic Workflow
      |
      +-- coordinates -> Activity
      |
      L-- coordinates -> Task

An Activity or Task may be performed by:

* a human;
* an Agent;
* an automated system;
* a service;
* a combination of these.

Agentic Workflow therefore concerns dynamic coordination and execution behavior, not ownership of the underlying work semantics.

;;;

8. Relationship to Agent

Agentic Workflow may engage one or more Agents.

Agentic Workflow
        |
        L-- engages -> Agent

The Agent remains governed by ADR-ES-004.

An Agent may:

* interpret workflow intent;
* select an execution path;
* coordinate actions;
* invoke permitted services;
* respond to context;
* resolve exceptions;
* escalate when authority is exceeded.

The workflow does not become an Agent.

;;;

9. Agentic Workflow Execution Pattern

The conventional workflow pattern may be represented as:

Trigger
   v
Step
   v
Rule
   v
Action
   v
Next Step

An Agentic Workflow introduces a dynamic decision boundary:

Workflow Intent
      v
Context
      v
Agent
      v
Interpretation
      v
Authority / Constraints
      v
Action or Path Selection
      v
Execution
      v
Outcome
      v
Context Update
      ↺

The key distinction is not simply that the workflow contains an Agent.

The workflow becomes agentic when agentic behavior materially influences workflow coordination or execution.

;;;

10. Agentic Participation Threshold

Merely invoking an Agent does not make a Workflow an Agentic Workflow.

For example:

Workflow
   v
Agent used as fixed service
   v
Predetermined next step

does not necessarily establish agentic workflow semantics.

By contrast:

Workflow
   v
Agent interprets context
   v
Agent selects permitted next action
   v
Workflow adapts

does satisfy the semantic condition.

The distinction is therefore based on material agentic participation in workflow coordination or execution, not the mere presence of an Agent.

;;;

11. Authority Boundary

Agentic Workflow shall inherit the authority principles of Agentic semantics.

The canonical boundary is:

Workflow Intent
       v
Authority
       v
Constraints / Policies
       v
Agent Interpretation
       v
Action / Path Selection
       v
Execution
       v
Outcome

The workflow shall not imply unrestricted execution.

Where a selected action exceeds authority, the workflow may:

Escalate
   v
Request Approval
   v
Suspend
   v
Select Alternative

;;;

12. Adaptation Boundary

Agentic Workflow permits runtime adaptation.

However, adaptation shall remain bounded.

Context Change
      v
Interpretation
      v
Evaluate Authority / Constraints
      v
Select New Path
      v
Continue / Escalate

Agentic Workflow does not imply unrestricted self-modification of its underlying workflow definition.

Runtime adaptation and structural self-redefinition are distinct semantics.

;;;

13. Relationship to Automation

Automation may exist within Agentic Workflow.

The semantic distinction is:

Automation
    = execution according to predefined mechanisms

while:

Agentic Workflow
    = workflow execution or coordination
      materially influenced by agentic interpretation
      and action/path selection

An Agentic Workflow can therefore contain automated steps.

Automation is not itself evidence of agency.

;;;

14. Relationship to AI

Agentic Workflow is technology-neutral.

An Agentic Workflow may be implemented using:

* AI-based Agents;
* rule-based Agents;
* software Agents;
* socio-technical Agents;
* other implementations satisfying the Agent semantics.

Therefore:

AI ≠ Agentic Workflow

and:

AI-enabled Workflow ≠ necessarily Agentic Workflow

AI may be used to implement agentic interpretation or action selection, but it is not part of the definition.

;;;

15. Relationship to Agentic Value Stream

The concepts operate at different architectural levels.

Agentic Value Stream
        |
        +-- Value Stage
        |
        L-- Process
              |
              L-- Agentic Workflow

Agentic Value Stream answers:

How is stakeholder value realized end-to-end?

Agentic Workflow answers:

How is work dynamically coordinated or executed within a process?

Therefore:

Agentic Value Stream ≠ Agentic Workflow

An Agentic Value Stream may contain or use multiple Agentic Workflows.

An Agentic Workflow may also support a conventional Value Stream where appropriate.

;;;

16. Relationship to Agentic Operations

Agentic Operations is intentionally not established by this ADR.

The distinction is:

Agentic Workflow
    = work coordination / execution pattern
Agentic Operations
    = operational mode / organizational execution semantics

Agentic Operations shall require a separate ADR.

This ADR must not introduce a canonical Agentic Operations relationship merely to connect the concepts.

;;;

17. Relationship to Autonomous Workflow

Agentic Workflow does not imply autonomous workflow.

It may operate with:

* human approval;
* human escalation;
* constrained authority;
* predefined policies;
* supervised execution;
* externally established objectives.

A future autonomy decision may establish additional semantics.

;;;

18. Canonical Relationships

The following relationships are established:

Agentic Workflow
    +-- specializes -> Workflow
    +-- engages -> Agent
    +-- coordinates -> Activity
    +-- coordinates -> Task
    +-- operates-within -> Authority
    +-- interprets -> Intent
    L-- produces -> Outcome

Where supported by existing semantics:

Process
    L-- realized-through -> Agentic Workflow

The implementation shall not create redundant predicates where existing canonical predicates can be reused.

;;;

19. Property Model

Agentic Workflow may expose:

Property	Purpose
workflow_intent	Intent guiding dynamic execution
agentic_scope	Workflow decisions or execution areas subject to agentic behavior
authority_context	Authority governing agentic decisions
decision_boundary	Decisions that may be dynamically selected
adaptation_scope	Areas in which runtime adaptation is permitted
intervention_model	Human approval, oversight, escalation, or intervention
execution_context	Context used in workflow interpretation
escalation_boundary	Conditions requiring intervention

These properties supplement inherited Workflow semantics.

;;;

20. Architectural Boundary

The canonical semantic boundary becomes:

VALUE REALIZATION
-----------------------------
Agentic Value Stream
        v
Value Stage
-----------------------------
WORK ORGANIZATION
        v
Process
-----------------------------
WORK EXECUTION
        v
Agentic Workflow
        v
Activity / Task
-----------------------------
IMPLEMENTATION
        v
Agent / Human / Service / System / Resource

This boundary is normative for Enterprise-Semantics.

;;;

21. Example ;;; OTCHERE Inc Order Fulfillment

A Process may represent:

Fulfill Customer Order.

Its conventional workflow could be:

Receive Order
      v
Check Inventory
      v
Reserve Inventory
      v
Schedule Delivery
      v
Dispatch
      v
Confirm Delivery

An Agentic Workflow may instead operate:

Receive Order
      v
Interpret Order Context
      v
Assess Inventory / Customer / Delivery Context
      v
Select Fulfillment Strategy
      v
Coordinate Inventory
      v
Coordinate Logistics
      v
Monitor Outcome
      v
Adapt to Exception
      v
Escalate if Authority Exceeded
      v
Confirm Delivery

The Process remains:

Fulfill Customer Order.

The Workflow remains the mechanism through which that process is executed.

The Agentic Workflow introduces dynamic interpretation and bounded decision-making into that execution.

;;;

22. UML Relational Model

The conceptual model shall follow:

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
AgenticWorkflow --> Agent : engages
AgenticWorkflow --> Activity : coordinates
AgenticWorkflow --> Task : coordinates
AgenticWorkflow --> Intent : interprets
AgenticWorkflow --> Authority : operates-within
AgenticWorkflow --> Outcome : produces
@enduml

The actual repository diagram shall use the project’s established visual conventions.

;;;

23. Conformance Requirements

An implementation conforming to ADR-ES-006 shall satisfy:

AWF-CON-001
Agentic Workflow specializes Workflow.

AWF-CON-002
Agentic Workflow retains the semantics of Workflow.

AWF-CON-003
Agentic Workflow materially incorporates agentic behavior into coordination or execution.

AWF-CON-004
Agentic Workflow operates within defined authority.

AWF-CON-005
Agentic Workflow has an identifiable intent or execution objective where agentic decision-making occurs.

AWF-CON-006
Agentic Workflow may coordinate Activities and Tasks.

AWF-CON-007
Agentic Workflow may engage Agents.

AWF-CON-008
Human intervention is permitted.

AWF-CON-009
Agentic Workflow does not require AI.

AWF-CON-010
Agentic Workflow does not imply autonomy.

AWF-CON-011
Agentic Workflow is not a Process.

AWF-CON-012
Agentic Workflow is not a Value Stream.

AWF-CON-013
Agentic Workflow is not an Agent.

AWF-CON-014
Agentic Workflow preserves grounding and provenance.

;;;

24. Rejected Alternatives

24.1 Agentic Workflow = AI Workflow

Rejected because AI is implementation technology.

24.2 Agentic Workflow = Automated Workflow

Rejected because automation does not establish agentic interpretation or action selection.

24.3 Agentic Workflow = Autonomous Workflow

Rejected because agency does not imply autonomy.

24.4 Agentic Workflow = Process

Rejected because Process represents organized work while Workflow represents its coordination or execution.

24.5 Agentic Workflow = Workflow containing an Agent

Rejected because merely invoking an Agent does not establish material agentic workflow behavior.

24.6 Agentic Workflow = Agentic Value Stream

Rejected because value realization and work execution operate at different semantic levels.

;;;

25. Consequences

Positive

* Establishes a formal execution-level semantic for agentic behavior.
* Preserves the Process/Workflow boundary.
* Provides a controlled bridge between Agentic Value Stream and execution.
* Allows agentic behavior without requiring AI.
* Supports mixed human, automated, and agentic execution.
* Establishes authority and intervention boundaries.
* Provides a foundation for future Agentic Operations semantics.

Constraints

* Workflow semantics must remain independently identifiable.
* Agentic Workflow cannot be treated as a synonym for AI workflow.
* Autonomous behavior requires separate semantic grounding.
* Agentic Operations remains outside this ADR.

;;;

26. Decision Summary

The canonical relationship is:

Process
   |
   L-- realized-through
          v
      Workflow
          ▲
          | specializes
          |
  Agentic Workflow
          |
          +-- engages -> Agent
          +-- interprets -> Intent
          +-- operates-within -> Authority
          +-- coordinates -> Activity / Task
          L-- produces -> Outcome

Agentic Workflow therefore establishes agentic execution and coordination semantics without redefining the process being executed or the value stream being realized.

;;

27. Acceptance

This ADR was promoted from Proposed to Accepted on 2026-09-23 per user directive message 1552318709853462599. The promotion ritual per ADR-ES-001 §10-§11 (status header + body Status field + this §27 Acceptance section) was executed in concert with the CR-ES-006 promotion.

The promotion to Accepted has the following consequences:

* CR-ES-006 is binding on all subsequent Enterprise-Semantics concept records.
* Agentic Workflow (ES:CONCEPT:agentic-workflow) is canonical at Candidate lifecycle.
* The 2 Agentic Workflow governed predicates (operates-within ;; process-realized-through) are registered in relationships/vocabulary.yaml v0.6.0.
* The 2 inverse pairs are registered in relationships/inverse.yaml v0.6.0.
* Enterprise-Semantics v0.5.0 is the canonical version pointer (per §26 ;; versions/v0.5.0.yaml).
* ES:PROFILE:agentic-execution scope extension per CR-ES-006 §21.
* 2 mapping records (WSF + OpenDEA per CR-ES-006 §19 + §20) are PROPOSED.
* The 5 documentation files (per CR-ES-006 §15 + §16 + §23) are published in enterprise-semantics-docs.
* The 2 OTCHERE Inc examples (per CR-ES-006 §27) are published in enterprise-semantics-examples.
* The 9 test files (per CR-ES-006 §28 + §29) are published in enterprise-semantics-test-probe.
* The 3 PlantUML sources (per CR-ES-006 §24 + §25 + §26) are published in enterprise-semantics-visuals.
* No Agentic Operations ;; Agentic Flow ;; Autonomous Workflow ;; Autonomous Operations ;; Autonomous Value Stream ;; Autonomous Enterprise ;; Autonomous Agent ;; AI-specific workflow semantics ;; LLM Workflow ;; vendor-specific agent frameworks are canonicalised (per §3).
* No WSF metamodel change has been made (per §3 + §16).
* No OpenDEA metamodel change has been made (per §3 + §13 + §20).
* No DEA catalog implementation has been made (per §3).
* The follow-on sequence is unblocked: ADR-ES-007 (Agentic Operations) ;; ADR-ES-008 (Autonomous) ;; ADR-ES-009 (Autonomous Value Stream) ;; ADR-ES-010 (Autonomous Workflow).

The 7 PRs that satisfy the acceptance criteria:

- enterprise-semantics PR #12 ;; VS-A ;; 1 concept record rewritten (specialisation hypothesis) + 8 canonical relationships + 8 properties + 8 characteristics + 8 invariants + 2 mappings
- enterprise-semantics PR #13 ;; VS-B ;; 2 governed predicates + 2 inverse pairs + versions/v0.5.0.yaml
- enterprise-semantics-mappings PR #6 ;; VS-C ;; 2 mapping records (WSF + OpenDEA)
- enterprise-semantics-docs PR #5 ;; VS-D1a ;; 5 documentation files
- enterprise-semantics-examples PR #6 ;; VS-D1b ;; 2 OTCHERE Inc Order Fulfillment worked examples
- enterprise-semantics-test-probe PR #5 ;; VS-D2a ;; 9 test files + 14 AWF-CON rules + 10 negative tests
- enterprise-semantics-visuals PR #6 ;; VS-D2b ;; 3 PlantUML sources

Promoted by: Emmanuel A. Otchere (cardinal author rule, 2026-09-23) per ADR-ES-001 §10-§11 promotion ritual.

