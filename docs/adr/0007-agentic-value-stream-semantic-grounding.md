<!--
ADR-ES-005 ;; Agentic Value Stream Semantic Grounding Decision

Dash-normalized: colons (:) and semicolons (;) used consistently.
Verbatim original: 00_inbox/ADR-ES-005.md (em-dashes and ellipsis dividers preserved in source).

Status: Accepted (promoted from Proposed on 2026-09-23 per user directive message 1552289869429088307 ;;; "Save it, read and understand, then proceed with all tasks needed to make way to implement it appropriately. Then implement it.")
Decision Type: Foundational Enterprise Semantic Specialization
Scope: Enterprise-Semantics
Supersedes: None
Depends on: ADR-ES-001 (Authority and Publication Architecture) ;; ADR-ES-003 (Value Stream Semantic Grounding, Accepted 2026-09-23) ;; ADR-ES-004 (Agentic Semantic Grounding, Accepted 2026-09-23) ;; FND-ES-AG-008 (WSF Tier 1 / Tier 2 Grounding Boundary, Established 2026-09-22)
Related: CR-ES-005 (Agentic Value Stream Semantic Grounding, Accepted 2026-09-23) ;; ADR-ES-006 (Agentic Workflow, future) ;; ADR-ES-007 (Agentic Operations, future) ;; ADR-ES-008 (Autonomous, future) ;; ADR-ES-009 (Autonomous Value Stream, future)

Decision: Establish Agentic Value Stream as a specialization of Value Stream. Agentic Value Stream is a Value Stream in which one or more stages are materially realized through agentic behavior. The Agentic Value Stream concept retains the fundamental semantics of Value Stream while adding an explicit representation of agentic participation in value realization. Deliberately avoids premature canonicalization of Agentic Workflow ;; Agentic Operations ;; Agentic Flow ;; Autonomous Value Stream ;; Autonomous Agent ;; Autonomous Enterprise ;; Autonomous Operations ;; AI-specific semantics.

Slot note: this ADR is filed at governance repo docs/adr/0007-... Slot 0007 is the next free slot in the ES series ;; distinct from the ES-AG series at slot 0003 (manny-es). The ES series slot sequence is 0001 (Authority), 0002 (Enterprise Semantic Model), 0003 (Agentic Semantic Decision, ES-AG), 0004 (Capability, ES), 0005 (Value Stream, ES), 0006 (Agentic, ES), 0007 (Agentic Value Stream, ES).

Promotion rationale: All 23 acceptance criteria of CR-ES-005 §28 satisfied via 7 PRs across 6 repos. The 1 concept record (ES:CONCEPT:agentic-value-stream) rewritten to align with the specialisation hypothesis (replacing the prior FND-ES-AG-002 Profile hypothesis) ;; 3 governed predicates (specializes ;; engages ;; agent-realizes) ;; 3 inverse pairs ;; v0.4.0 version pointer ;; Agentic Value Realization Profile (ES:PROFILE:agentic-value-realization) ;; 2 mapping records (WSF + OpenDEA) ;; 9 docs files + 1 OTCHERE Inc example + 9 test files + 3 PlantUML sources.

Implementation: CR-ES-005 (Agentic Value Stream Semantic Grounding). CR-ES-005 is the implementation specification ;; this ADR ratifies it as a governed semantic decision.

Authored by: Emmanuel A. Otchere (cardinal author rule, 2026-09-23)
Promoted by: Emmanuel A. Otchere (cardinal author rule, 2026-09-23) per ADR-ES-001 §10-§11 promotion ritual
-->

The next governed pair should establish Agentic Value Stream as a specialization of Value Stream, while deliberately avoiding premature canonicalization of Agentic Workflow, Agentic Operations, Autonomous Value Stream, or AI-specific semantics.

ADR-ES-005 ; Agentic Value Stream Semantic Grounding

Status: Accepted (promoted from Proposed on 2026-09-23 per user directive message 1552289869429088307)
Date: 2026-09-23
Decision Type: Foundational Enterprise Semantic Specialization
Scope: Enterprise-Semantics
Depends On: ADR-ES-001, ADR-ES-003, ADR-ES-004
Implementation: CR-ES-005
Target Semantic Version: 0.4.0

;;;

1. Context

ADR-ES-003 established Value Stream as the semantic construct for representing the end-to-end progression through which stakeholder value is realized.

ADR-ES-004 established Agentic as a mode of operation characterized by delegated intent, contextual interpretation, bounded authority, action selection or coordination, outcome orientation, and adaptation.

These two semantic foundations create the need to represent a value stream in which such agentic behavior materially participates in the realization of value.

The resulting concept must not collapse:

* Value Stream into Process;
* Agentic Value Stream into Agentic Workflow;
* Agentic into AI;
* Agentic into Automation;
* Agentic into Autonomous;
* value realization into execution;
* or agentic participation into complete autonomy.

The semantic requirement is therefore to represent agency within the value-realization structure, rather than to redefine the value stream around a particular technology.

;;;

2. Decision

Enterprise-Semantics establishes Agentic Value Stream as a specialization of Value Stream.

Canonical definition

An Agentic Value Stream is a Value Stream in which one or more stages are materially realized through agentic behavior, enabling delegated interpretation, action selection, coordination, adaptation, or execution toward stakeholder value realization.

Agentic Value Stream therefore inherits the fundamental semantics of Value Stream while adding an explicit representation of agentic participation in value realization.

Formally:

Agentic Value Stream
        `---- is a > Value Stream

Agentic Value Stream does not replace the Value Stream concept.

;;;

3. Semantic Principle

The central semantic distinction is:

Value Stream describes the progression of value realization; Agentic describes a mode through which portions of that progression are realized.

Therefore:

VALUE REALIZATION
        |
        v
Value Stream
        |
        |---- Value Stage
        |      |
        |      `---- Process
        |             `---- Activity
        |                    `---- Task
        |                           `---- Workflow / Task Flow
        |
        v
Agentic Value Stream
        |
        |---- retains the Value Stream structure
        |
        |---- introduces agentic participation
        |
        |---- enables contextual interpretation
        |
        |---- enables delegated decision/action selection
        |
        |---- enables dynamic coordination
        |
        `---- enables contextual adaptation

The distinction is therefore primarily semantic and operational, rather than technological.

;;;

4. Agentic Value Stream Characteristics

An Agentic Value Stream may exhibit one or more of the following characteristics:

4.1 Delegated Intent

The value realization is influenced by an established or delegated intent that guides agentic behavior.

4.2 Contextual Interpretation

Relevant context can be interpreted during value realization rather than being entirely predetermined.

4.3 Dynamic Action Selection

Actions or execution paths may be selected according to the interpreted context, intent, authority, constraints, and expected outcome.

4.4 Agentic Coordination

An Agent may coordinate actions, participants, services, processes, or other agents within its authority.

4.5 Adaptive Progression

The progression through stages may change in response to new information, events, outcomes, or context.

4.6 Bounded Authority

Agentic behavior operates within explicitly defined authority and policy boundaries.

4.7 Intervention

Human intervention, escalation, approval, or oversight may remain part of the value stream.

4.8 Outcome Orientation

Agentic behavior remains directed toward intended stakeholder and value outcomes rather than merely executing predetermined tasks.

;;;

5. Agentic Does Not Mean Entirely Agentic

An Agentic Value Stream does not require every stage, process, activity, or task to be agentic.

A valid Agentic Value Stream may contain:

Conventional execution
        +
Automated execution
        +
Human decision
        +
Agentic decision
        +
Agentic coordination
        +
Human intervention

Consequently, agentic coverage is contextual, not binary at the entire-stream level.

For example:

Order-to-Cash
Order Capture          Conventional
Order Validation       Agentic
Credit Decision        Human / Agentic
Fulfillment Selection  Agentic
Delivery               Automated / Conventional
Exception Management   Agentic
Settlement             Automated

The value stream remains one end-to-end value realization construct despite having heterogeneous realization modes.

;;;

6. Relationship to Value Stage

Agentic behavior may occur within one or more existing Value Stages.

A new Agentic Value Stage concept is not established by this ADR.

Instead:

Value Stream
    |
    `---- contains > Value Stage
                       |
                       `---- may be realized agentically

This preserves the distinction between:

* what transition in value occurs ;;; Value Stage;
* how that transition is realized ;;; Process and its execution mechanisms;
* whether agentic behavior participates ;;; Agentic realization.

;;;

7. Canonical Relationships

The following relationships are established or specialized by this decision.

Value Stream inheritance

Agentic Value Stream
    `---- specializes > Value Stream

Value realization

Agentic Value Stream
    `---- realizes > Stakeholder Value

Stage structure

Agentic Value Stream
    `---- contains > Value Stage

Agent participation

Agentic Value Stream
    `---- engages > Agent

Agent authority

The Agentic Value Stream does not redefine the authority semantics established by ADR-ES-004.

Agent
    |---- interprets > Intent
    |---- acts-within > Authority
    |---- selects > Action
    |---- coordinates > Action
    `---- produces > Outcome

Contextual adaptation

Agent
    `---- adapts-to > Context

The value stream therefore provides the value-realization context within which agentic behavior operates.

;;;

8. Agentic Value Stream Property Model

An Agentic Value Stream inherits the properties of Value Stream established by ADR-ES-003.

Additional semantic properties may include:

Property	Purpose
agentic_scope	Identifies where agentic behavior materially participates
delegated_intent	Identifies the intent guiding agentic participation
authority_context	Defines the authority under which agentic behavior operates
decision_boundary	Identifies decisions that may be interpreted or selected agentically
intervention_model	Defines human or external intervention points
adaptation_scope	Identifies where contextual adaptation is permitted
realization_mode	Describes the mixture of conventional, automated, human, and agentic realization

These properties describe the agentic characteristics of realization and do not replace the underlying Value Stream properties.

;;;

9. Classic and Agentic Value Stream

The semantic distinction can be represented as follows:

Dimension	Value Stream	Agentic Value Stream
Primary concern	Value realization	Value realization with agentic participation
Value stages	Required	Inherited
Stakeholder	Required	Inherited
Initiating condition	Required	Inherited
Realization boundary	Required	Inherited
Process realization	Supported	Supported
Delegated intent	Not intrinsically required	Material where agentic behavior operates
Authority	Not intrinsically required as an agentic construct	Explicitly relevant
Action selection	May be predetermined or externally managed	May be performed agentically
Context interpretation	Not intrinsic	Explicit characteristic
Dynamic coordination	Not intrinsic	Explicit characteristic
Adaptation	Not intrinsic as an agentic construct	Explicit characteristic
Human intervention	Permitted	Permitted and representable
AI dependency	None	None
Automation dependency	None	None
Autonomy implication	None	None

The distinction does not imply that conventional Value Streams cannot be dynamic or adaptive. Rather, Agentic Value Stream explicitly represents agency as part of value realization.

;;;

10. Execution Boundary

Agentic Value Stream does not alter the established execution boundary.

VALUE REALIZATION
--------------------------------
Agentic Value Stream
        |
        v
Value Stage
--------------------------------
WORK ORGANIZATION
        |
        v
Process
        |
        v
Activity
        |
        v
Task
--------------------------------
EXECUTION / COORDINATION
        |
        v
Workflow / Task Flow
--------------------------------
IMPLEMENTATION
        |
        v
Service / System / Resource / Technology

Agentic behavior may influence any appropriate execution layer, but this does not make those layers semantically equivalent.

;;;

11. Relationship to AI

Agentic Value Stream is deliberately technology-neutral.

AI may implement an Agent.

An Agent may use AI.

An Agent may alternatively be implemented through software, a socio-technical mechanism, or another entity capable of satisfying the Agent semantics.

Therefore:

AI ≠ Agent
AI ≠ Agentic
Agentic Value Stream ≠ AI Value Stream

AI-based agents are an implementation possibility rather than a semantic requirement.

;;;

12. Relationship to Automation

Automation and agency remain distinct.

Automation
Trigger
   |
Predefined Rule
   |
Predefined Action

versus:

Agentic behavior
Delegated Intent
      |
Context
      |
Interpretation
      |
Action Selection
      |
Execution
      |
Outcome
      ↺
Contextual Adaptation

Automation may participate in an Agentic Value Stream without itself being agentic.

;;;

13. Relationship to Autonomy

Agentic Value Stream does not imply Autonomous Value Stream.

An Agentic Value Stream may operate with:

* human approval;
* human escalation;
* constrained agent authority;
* policy-controlled decisions;
* fixed organizational boundaries;
* externally established objectives.

Autonomy is therefore a separate semantic dimension.

A future Autonomous Value Stream ADR may establish additional criteria for self-governance, self-directed adaptation, or reduced external intervention.

Such semantics are explicitly outside this decision.

;;;

14. Relationship to Agentic Workflow and Agentic Operations

This ADR does not establish:

* Agentic Workflow;
* Agentic Operations;
* Agentic Flow;
* Autonomous Value Stream;
* Autonomous Enterprise;
* Autonomous Operations.

Those concepts may subsequently be grounded through separate ADRs.

For this decision:

Agentic Value Stream
        |
        `---- engages > Agent

is sufficient.

More specialized execution relationships should be introduced only when their corresponding concepts become canonical.

;;;

15. Illustrative Example ;;; Order-to-Cash

Conventional representation

Customer Demand
      |
Order Capture
      |
Order Validation
      |
Credit Check
      |
Fulfillment
      |
Delivery
      |
Invoice
      |
Collection
      |
Customer / Enterprise Value

The Value Stream defines the progression of value realization.

Agentic representation

Customer Demand
      |
Interpret Customer Context
      |
Determine Order Handling
      |
Validate Order
      |
Select Fulfillment Path
      |
Coordinate Inventory / Logistics
      |
Adapt to Exceptions
      |
Escalate Where Authority Is Exceeded
      |
Complete Delivery / Settlement
      |
Customer / Enterprise Value

The difference is not that the second representation contains “more AI.”

The difference is that agentic interpretation, decision selection, coordination and adaptation have become material mechanisms of value realization.

;;;

16. Architectural Position

The semantic hierarchy is:

WSF
 |
 `---- Value Stream
        |
        v
Enterprise-Semantics
        |
        `---- Agentic Value Stream
               |
               |---- Value Stage
               |---- Agent
               |---- Intent
               |---- Authority
               |---- Process
               `---- Outcome
        |
        v
OpenDEA
        |
        `---- Agentic Value Stream specialization

Enterprise-Semantics therefore provides the semantic grounding while OpenDEA may subsequently specialize and operationalize the concept within its enterprise architecture metamodel.

No WSF metamodel change is required by this ADR.

;;;

17. Conformance Requirements

An implementation conforming to this decision shall satisfy:

AVS-CON-001
Agentic Value Stream shall specialize Value Stream.

AVS-CON-002
Agentic Value Stream shall retain the stakeholder-value realization semantics of Value Stream.

AVS-CON-003
Agentic Value Stream shall retain initiating-condition semantics.

AVS-CON-004
Agentic Value Stream shall retain realization-boundary semantics.

AVS-CON-005
An Agentic Value Stream shall identify at least one material agentic characteristic.

AVS-CON-006
Agentic participation shall be associated with delegated intent and bounded authority.

AVS-CON-007
Agentic participation may apply to one or more stages; complete-stream agency is not required.

AVS-CON-008
Agentic Value Stream shall not imply Autonomous Value Stream.

AVS-CON-009
Agentic Value Stream shall not require AI.

AVS-CON-010
Agentic Value Stream shall not redefine Process, Activity, Task, or Workflow.

AVS-CON-011
Agentic Value Stream shall preserve stakeholder value realization as its primary semantic purpose.

AVS-CON-012
Agentic Value Stream instances shall carry appropriate grounding and provenance.

;;;

18. Rejected Alternatives

18.1 Agentic Value Stream = AI-enabled Value Stream

Rejected because AI is an implementation technology rather than the semantic basis of agency.

18.2 Agentic Value Stream = Fully Autonomous Value Stream

Rejected because agentic behavior does not inherently imply autonomy.

18.3 Agentic Value Stream = Automated Value Stream

Rejected because automation does not inherently involve interpretation or delegated action selection.

18.4 Agentic Value Stream = Value Stream composed entirely of Agents

Rejected because agentic participation may be localized to particular stages, decisions, activities, or execution boundaries.

18.5 Agentic Value Stream replaces Value Stream

Rejected because Agentic Value Stream is a specialization and must inherit the fundamental semantics of Value Stream.

18.6 Agentic Value Stage

Rejected for this release because the existing Value Stage construct can represent the value transition independently of its realization mode.

;;;

19. Consequences

Positive

* Establishes a technology-neutral semantic foundation for agentic value realization.
* Preserves the existing Value Stream ontology.
* Provides a formal bridge between Value Stream and Agent semantics.
* Allows mixed human, automated, conventional, and agentic realization.
* Prevents premature conflation of agentic, autonomous, AI, and automation concepts.
* Creates a stable semantic foundation for later Agentic Workflow and Agentic Operations concepts.
* Enables OpenDEA to specialize the concept without redefining its meaning.

Constraints

* Agentic Value Stream cannot be fully specified through workflow semantics alone.
* Agentic participation requires explicit authority and intent semantics.
* Autonomous behavior requires a subsequent semantic decision.
* Specialized execution concepts remain intentionally deferred.

;;;

20. Decision Summary

The canonical relationship is:

Value Stream
     ^
     | specializes
     |
Agentic Value Stream
     |
     |---- realizes > Stakeholder Value
     |---- contains > Value Stage
     `---- engages > Agent
                       |---- interprets > Intent
                       |---- acts-within > Authority
                       |---- selects > Action
                       |---- coordinates > Action
                       `---- produces > Outcome

Agentic Value Stream therefore represents the transformation of value realization from a predominantly predefined progression into a value stream capable of delegated interpretation, dynamic action selection, coordination, and contextual adaptation;;;without making AI or autonomy part of its definition.

;;;

21. Next Decision Candidates

Potential subsequent semantic decisions include:

1. ADR-ES-006 ;;; Agentic Workflow Semantic Grounding
2. ADR-ES-007 ;;; Agentic Operations Semantic Grounding
3. ADR-ES-008 ;;; Autonomous Semantic Grounding
4. ADR-ES-009 ;;; Autonomous Value Stream Semantic Grounding

The sequencing should remain governed rather than establishing all downstream concepts within this ADR.

The implementation CR should now translate that decision into the canonical semantic artifacts, schemas, mappings, examples, visuals, and conformance tests;;;without pulling the deferred concepts into the release.

;;

22. Acceptance

This ADR was promoted from Proposed to Accepted on 2026-09-23 per user directive message 1552289869429088307. The promotion ritual per ADR-ES-001 §10-§11 (status header + body Status field + this §22 Acceptance section) was executed in concert with the CR-ES-005 promotion.

The promotion to Accepted has the following consequences:

* CR-ES-005 is binding on all subsequent Enterprise-Semantics concept records.
* Agentic Value Stream (ES:CONCEPT:agentic-value-stream) is canonical at Candidate lifecycle.
* The 3 Agentic Value Stream governed predicates (specializes ;; engages ;; agent-realizes) are registered in relationships/vocabulary.yaml v0.5.0.
* The 3 inverse pairs are registered in relationships/inverse.yaml v0.5.0.
* Enterprise-Semantics v0.4.0 is the canonical version pointer (per §26 ;; versions/v0.4.0.yaml).
* ES:PROFILE:agentic-value-realization (per CR-ES-005 §14) is registered at registry/profiles/.
* profile_type: agentic-value-realization is registered at registry/profile-types.yaml.
* 2 mapping records (WSF + OpenDEA per CR-ES-005 §12 + §13) are PROPOSED.
* The 9 documentation files (per CR-ES-005 §15 + §16 + §23) are published in enterprise-semantics-docs.
* The 1 OTCHERE Inc example (per CR-ES-005 §19) is published in enterprise-semantics-examples.
* The 9 test files (per CR-ES-005 §21 + §22) are published in enterprise-semantics-test-probe.
* The 3 PlantUML sources (per CR-ES-005 §17 + §18) are published in enterprise-semantics-visuals.
* No Agentic Workflow ;; Agentic Operations ;; Agentic Flow ;; Autonomous Value Stream ;; Autonomous Agent ;; Autonomous Enterprise ;; Autonomous Operations ;; AI-specific semantics ;; vendor-specific agent frameworks are canonicalised (per §3).
* No WSF metamodel change has been made (per §3 + §16).
* No OpenDEA metamodel change has been made (per §3 + §13).
* No DEA catalog implementation has been made (per §3).
* The follow-on sequence is unblocked: ADR-ES-006 (Agentic Workflow) ;; ADR-ES-007 (Agentic Operations) ;; ADR-ES-008 (Autonomous) ;; ADR-ES-009 (Autonomous Value Stream).

The 7 PRs that satisfy the acceptance criteria:

- enterprise-semantics PR #10 ;; VS-A ;; 1 concept record rewritten (specialisation hypothesis) + ES:PROFILE:agentic-value-realization
- enterprise-semantics PR #11 ;; VS-B ;; 3 governed predicates + 3 inverse pairs + versions/v0.4.0.yaml
- enterprise-semantics-mappings PR #5 ;; VS-C ;; 2 mapping records (WSF + OpenDEA)
- enterprise-semantics-docs PR #4 ;; VS-D1a ;; 5 documentation files
- enterprise-semantics-examples PR #4 ;; VS-D1b ;; 1 OTCHERE Inc Order-to-Cash (Agentic) example
- enterprise-semantics-test-probe PR #4 ;; VS-D2a ;; 9 test files + 12 AVS-CON rules + 10 negative tests
- enterprise-semantics-visuals PR #5 ;; VS-D2b ;; 3 PlantUML sources

Promoted by: Emmanuel A. Otchere (cardinal author rule, 2026-09-23) per ADR-ES-001 §10-§11 promotion ritual.
