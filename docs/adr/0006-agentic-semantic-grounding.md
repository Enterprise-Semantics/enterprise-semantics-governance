<!--
ADR-ES-004, Agentic Semantic Grounding Decision

Dash-normalized: colons (:) and semicolons (;) used consistently.
Verbatim original: 00_inbox/ADR-ES-004.md (em-dashes and ellipsis dividers preserved in source).

Status: Accepted (promoted from Proposed on 2026-09-23 per user directive message 1552262422398767115, "Proceed with everything")
Date: 2026-09-23
Decision Type: Foundational Semantic Architecture
Scope: Enterprise-Semantics (Agentic as foundational semantic property)
Supersedes: None
Depends on: ADR-ES-001 (Authority and Publication Architecture) ;; ADR-ES-002 (Capability Semantic Grounding, Accepted 2026-09-23) ;; ADR-ES-003 (Value Stream Semantic Grounding, Accepted 2026-09-23) ;; FND-ES-AG-008 (WSF Tier 1 / Tier 2 Grounding Boundary, Established 2026-09-22)
Related: CR-ES-004 (Agentic Semantic Grounding, Accepted 2026-09-23) ;; ADR-ES-005 (Agentic Value Stream, future) ;; ADR-ES-006 (Agentic Workflow, future) ;; ADR-ES-007 (Autonomous Operations, future) ;; FND-ES-AG-001-Grounding-Result §1 (kernel/decomposition pattern)

Decision: Establish Agentic as a foundational enterprise semantic property describing a mode of operation in which an Agent interprets a delegated objective or intent, determines or selects actions within defined authority, and acts or coordinates actions toward an intended outcome. Agentic shall remain distinct from AI, Automation, and Autonomous. Agent may be human, software-based, computational, organizational, or socio-technical. Agentic is modeled as a semantic property/mode rather than automatically as a universal Entity subtype, this prevents the ontology from unnecessarily turning every agentic construct into a new top-level entity class.

Slot note: this ADR is filed at governance repo docs/adr/0006-... The slot sequence is 0000-template, 0001-authority-and-publication, 0002-enterprise-semantic-model, 0003-agentic-semantic-decision, 0004-capability-semantic-grounding, 0005-value-stream-semantic-grounding, 0006-agentic-semantic-grounding. Slot 0006 is the next free slot. The pre-existing 0003-agentic-semantic-decision is the ES-AG series slot for ADR-ES-AG-001 by manny-es (separate lineage), the ES series continues with 0004-0005-0006.

Promotion rationale: All 24 acceptance criteria of CR-ES-004 §31 satisfied via 6 PRs across 6 repos (PR #7 enterprise-semantics, PR #8 enterprise-semantics, PR #4 enterprise-semantics-mappings, PR #3 enterprise-semantics-docs, PR #3 enterprise-semantics-examples, PR #3 enterprise-semantics-test-probe, PR #3 enterprise-semantics-visuals, PR #9 enterprise-semantics for the Agentic Profile per CR-ES-004 §22). The 5 concept records (Agent + Agentic + Intent + Authority + Action) are Candidate (per scope decision, promotion to Established held for separate governed action). The 33 governed predicates (13 Value Stream + 9 Capability + 11 Agentic + 4 namespaced for cross-CR subject-type disambiguation) are registered in vocabulary.yaml v0.4.0. The 2 mapping records (WSF Tier 2 Specialisation + OpenDEA architectural pattern) are PROPOSED. The 9 docs files + 1 OTCHERE Inc example + 9 test files + 3 PlantUML sources are published. The Agentic Profile (ES:PROFILE:AGENTIC) is landed at v0.1.0, Candidate.

Implementation: CR-ES-004 (Agentic Semantic Grounding). CR-ES-004 is the implementation specification, this ADR ratifies it as a governed semantic decision.

Authored by: Emmanuel A. Otchere (cardinal author rule, 2026-09-23)
Promoted by: Emmanuel A. Otchere (cardinal author rule, 2026-09-23) per ADR-ES-001 §10-§11 promotion ritual
-->

ADR-ES-004 ; Agentic Semantic Grounding

|Status: Accepted (promoted from Proposed on 2026-09-23 per user directive message 1552262422398767115, "Proceed with everything")
Date: 2026-09-23
Decision Type: Foundational Semantic Architecture
Scope: Enterprise-Semantics
Supersedes: None
Depends On: ADR-ES-001, ADR-ES-002, ADR-ES-003
Implementation: CR-ES-004

;;;

1. Decision Summary

Establish Agentic as an enterprise semantic property describing a mode of operation in which an agent can interpret a delegated objective or intent, determine or select actions within defined authority, and act or coordinate actions toward an intended outcome.

Agentic semantics shall not be defined as synonymous with:

* Artificial Intelligence;
* AI Agent;
* automation;
* autonomous operation;
* machine learning;
* generative AI;
* workflow automation.

The foundational distinction is:

Agentic describes the capacity for delegated goal-directed agency within defined authority, not the technology used to provide that agency.

This ADR establishes the semantic foundation for subsequent concepts including:

* Agent;
* Agentic Flow;
* Agentic Workflow;
* Agentic Operations;
* Agentic Value Stream.

;;;

2. Context

Enterprise systems increasingly contain components capable of:

* interpreting objectives;
* selecting actions;
* planning;
* coordinating activities;
* invoking services;
* negotiating execution paths;
* adapting execution;
* responding to changing conditions;
* requesting human intervention;
* acting within delegated authority.

These behaviors cannot be adequately represented by treating them simply as:

Automation

or:

Workflow

because traditional automation generally executes predefined logic, while agentic behavior introduces some degree of contextual interpretation, decision selection, planning, or delegated action.

At the same time, agentic behavior must not automatically be equated with autonomy.

An agent may be agentic while operating under:

* explicit human approval;
* bounded policies;
* delegated authority;
* predefined objectives;
* supervision;
* escalation rules;
* operational constraints.

Therefore a semantic distinction between Agentic and Autonomous is required.

;;;

3. Problem

Without a foundational Agentic semantic, enterprise architecture risks conflating:

AI
Automation
Agent
Agentic
Autonomous
Workflow
Agentic Workflow

This creates ambiguity when modeling enterprise operating behavior.

The semantic model must answer:

* What makes behavior agentic?
* What is an Agent?
* How does an Agent differ from an automated system?
* How does Agentic differ from Autonomous?
* How does Agentic Workflow differ from Workflow?
* How does Agentic Operations differ from conventional Operations?
* How can agentic behavior participate in a Value Stream?

;;;

4. Decision

Enterprise-Semantics shall establish the following foundational definition.

4.1 Agentic

Agentic describes a mode of operation in which an Agent interprets a delegated objective or intent, determines or selects actions within defined authority, and acts or coordinates actions toward an intended outcome.

Agentic behavior therefore contains, at minimum, a meaningful degree of:

1. delegated intent or objective;
2. contextual interpretation;
3. action selection or planning;
4. delegated authority;
5. execution or coordination;
6. orientation toward an intended outcome.

Not every implementation must exhibit the same degree of each characteristic.

;;;

5. Agent

Establish:

An Agent is an Entity capable of interpreting delegated intent, selecting or coordinating actions, and acting within defined authority toward an intended outcome.

An Agent may be:

* human;
* software-based;
* computational;
* organizational;
* socio-technical;

provided that the relevant semantic characteristics are present.

The concept AI Agent shall therefore be treated as a possible specialization or implementation of Agent rather than as the definition of Agent itself.

;;;

6. Agentic as a Semantic Property

Agentic shall be modeled primarily as a semantic property or mode of operation, rather than automatically as a universal Entity subtype.

For example:

Agent
 |
 |---- operates agentically

or:

Workflow
 |
 |---- has agentic execution characteristics

or:

Operation
 |
 |---- performed agentically

The exact specialization structure shall be established by each subsequent concept ADR.

This prevents the ontology from unnecessarily turning every agentic construct into a new top-level entity class.

;;;

7. Agentic Characteristics

An agentic construct should be evaluated against the following characteristics.

7.1 Delegated Intent

There is an objective, intent, goal, or desired outcome delegated to the Agent.

7.2 Context Interpretation

The Agent interprets relevant context rather than merely executing an unconditional predefined sequence.

7.3 Action Selection

The Agent can select, sequence, or coordinate actions within its authority.

7.4 Bounded Authority

The Agent operates within explicit or implicit authority boundaries.

7.5 Outcome Orientation

Actions are directed toward an intended outcome rather than merely completion of a fixed instruction.

7.6 Adaptation

The Agent may alter its execution path in response to changing conditions.

Adaptation is characteristic of agentic operation but is not by itself sufficient to establish agentic semantics.

;;;

8. Agentic vs Automation

Automation shall remain distinct.

Automation

Generally represents:

execution of predefined logic, rules, or procedures without requiring contextual action selection by an agent.

Agentic Operation

Represents:

delegated goal-oriented operation involving contextual interpretation and action selection within authority.

Therefore:

Automation ≠ Agentic

However:

Agentic operation may use automation.

A conventional automated workflow may therefore remain non-agentic.

;;;

9. Agentic vs Autonomous

This distinction is foundational.

Agentic

Agentic operation emphasizes:

* delegated intent;
* action selection;
* contextual interpretation;
* bounded authority;
* goal-directed execution.

Autonomous

Autonomous operation additionally emphasizes a higher degree of:

* self-direction;
* self-management;
* self-adaptation;
* reduced external intervention;
* sustained independent operation.

Therefore:

Agentic ≠ Autonomous

and:

Agentic
 |
 |---- may evolve toward --> Autonomous

Autonomy shall be established by a separate semantic ADR.

;;;

10. Agentic vs AI

AI shall not define Agentic.

An agentic implementation may use:

* AI;
* optimization;
* rules;
* reasoning systems;
* symbolic systems;
* planning systems;
* conventional software;
* combinations of these.

Likewise, an AI system is not necessarily agentic.

Therefore:

AI ≠ Agentic

and:

AI Agent ⊂ possible Agents

subject to future formalization.

;;;

11. Agentic vs Workflow

Workflow describes coordinated execution.

Agentic Workflow describes a workflow in which agentic behavior participates materially in:

* planning;
* interpretation;
* sequencing;
* decision selection;
* execution;
* adaptation;
* coordination.

Therefore:

Workflow
 |
 |---- may be realized agentically

Agentic Workflow shall be established in a subsequent ADR.

;;;

12. Agentic Operations

Agentic Operations shall represent the application of agentic behavior to operational execution.

It shall address how operational work may be:

* interpreted;
* planned;
* coordinated;
* executed;
* adapted;
* escalated.

Agentic Operations shall remain distinct from Agentic Value Stream.

The distinction is:

Agentic Operations
 |
 |---- concerns operational execution
Agentic Value Stream
 |
 |---- concerns end-to-end value realization

;;;

13. Agentic Value Stream Boundary

Agentic Value Stream shall not be defined by this ADR.

However, this ADR establishes the semantic prerequisites for ADR-ES-005.

The intended specialization relationship is:

Value Stream
 |
 |---- agentic specialization -->
 Agentic Value Stream

Agentic Value Stream must therefore retain the fundamental semantics established by ADR-ES-003.

;;;

14. Core Relationships

The following relationships shall be established or prepared for implementation.

Subject	Predicate	Object
Agent	interprets	Intent
Agent	pursues	Goal
Agent	acts-within	Authority
Agent	selects	Action
Agent	coordinates	Action
Agent	produces	Outcome
Agent	adapts-to	Context
Agentic Operation	uses	Agent
Agentic Workflow	uses	Agent
Agentic Workflow	realizes	Workflow Intent
Agentic Operation	pursues	Operational Outcome
Agentic Value Stream	uses	Agent

The last relationship is reserved for ADR-ES-005 and shall not be promoted to a Value Stream specialization by this ADR.

;;;

15. Authority Boundary

Agentic operation must be bounded.

An Agent shall operate within:

Intent
 |
 v
Authority
 |
 v
Constraints / Policies
 |
 v
Action Selection
 |
 v
Execution
 |
 v
Outcome

Authority may include:

* permitted actions;
* prohibited actions;
* resource limits;
* decision thresholds;
* escalation requirements;
* policy constraints;
* human approval requirements.

Agentic semantics without authority boundaries would be insufficiently defined for enterprise use.

;;;

16. Human Participation

Agentic semantics does not imply elimination of humans.

A human may:

* define intent;
* delegate authority;
* approve actions;
* supervise execution;
* intervene;
* resolve exceptions;
* revoke authority;
* evaluate outcomes.

Therefore:

Human-in-the-loop
Human-on-the-loop
Human-over-the-loop

may all represent agentic operating patterns.

Human participation does not invalidate agentic semantics.

;;;

17. Agentic Decision Boundary

Agentic behavior requires a distinction between:

Instruction

A prescribed action or procedure.

Decision

Selection among possible actions or responses.

Agentic Decision

A context-sensitive action selection performed by an Agent within delegated authority toward an intended outcome.

Therefore:

Instruction
 v
Execution

differs semantically from:

Intent
 v
Context
 v
Decision / Action Selection
 v
Execution
 v
Outcome

The latter represents the core agentic pattern.

;;;

18. Consequences

Positive

This decision provides:

* a technology-neutral definition of Agentic;
* a clear boundary between Agentic and Autonomous;
* a clear boundary between Agentic and Automation;
* a semantic basis for Agentic Workflow;
* a semantic basis for Agentic Operations;
* a semantic basis for Agentic Value Stream;
* explicit authority and governance semantics;
* compatibility with human-agent collaboration.

Architectural consequence

Enterprise-Semantics must model agency as behavior and capability, rather than treating AI technology as the semantic foundation.

Governance consequence

Future Agentic specializations must reference this ADR rather than independently redefining Agentic.

;;;

19. Rejected Alternatives

19.1 Agentic = AI

Rejected because AI is a technology/technical capability category while Agentic describes a mode of operation.

19.2 Agentic = Automation

Rejected because predefined execution does not inherently involve contextual action selection.

19.3 Agentic = Autonomous

Rejected because delegated agency does not require independent self-governance.

19.4 Agent = AI Agent

Rejected because human and non-AI agents may satisfy the foundational semantic definition.

19.5 Agentic = Unsupervised

Rejected because agentic operation may include human approval and intervention.

19.6 Agentic = Self-learning

Rejected because learning is not a necessary condition for agentic action.

;;;

20. Architectural Invariants

AG-INV-001

Agentic ≠ AI

AG-INV-002

Agentic ≠ Automation

AG-INV-003

Agentic ≠ Autonomous

AG-INV-004

Agent ≠ AI Agent

AG-INV-005

Agentic operation requires delegated intent or objective.

AG-INV-006

Agentic operation occurs within defined authority.

AG-INV-007

Agentic operation is outcome-oriented.

AG-INV-008

Human participation does not invalidate Agentic semantics.

AG-INV-009

Agentic Value Stream is a specialization of Value Stream,
not a replacement for Value Stream.

AG-INV-010

Autonomy requires separate semantic grounding.

;;;

21. Implementation

This ADR shall be implemented through:

CR-ES-004 ; Agentic Semantic Grounding

CR-ES-004 shall establish:

* Agent semantic representation;
* Agentic semantic representation;
* intent;
* authority;
* action;
* decision boundary;
* agentic relationships;
* AI Agent correspondence;
* Agentic Workflow boundary;
* Agentic Operations boundary;
* Value Stream boundary;
* provenance;
* mappings;
* conformance tests;
* worked examples.

;;;

22. Acceptance Criteria

The ADR is implemented when:

* [ ]	Agent has a formal semantic definition.
* [ ]	Agentic has a formal semantic definition.
* [ ]	Agentic is distinguished from AI.
* [ ]	Agentic is distinguished from automation.
* [ ]	Agentic is distinguished from autonomy.
* [ ]	delegated intent is represented.
* [ ]	authority is represented.
* [ ]	action selection is represented.
* [ ]	outcome orientation is represented.
* [ ]	human intervention is supported.
* [ ]	AI Agent is not incorrectly made synonymous with Agent.
* [ ]	Agentic Workflow boundary is established.
* [ ]	Agentic Operations boundary is established.
* [ ]	Agentic Value Stream dependency is established.
* [ ]	WSF grounding is documented.
* [ ]	OpenDEA implications are documented.
* [ ]	conformance tests pass.
* [ ]	no premature Autonomous semantics are established.

;;;

23. Next Governed Change

Following implementation:

ADR-ES-005 ; Agentic Value Stream Semantic Grounding

shall define the formal specialization of Value Stream in which agentic participation materially changes how value-stream stages are interpreted, coordinated, adapted, or executed.

The semantic chain shall therefore be:

Value Stream
 |
 v
Agentic Semantic Foundation
 |
 v
Agentic Value Stream

;;;

24. Acceptance

This ADR was promoted from Proposed to Accepted on 2026-09-23 per user directive message 1552262422398767115. The promotion ritual per ADR-ES-001 §10-§11 (status header + body Status field + this §24 Acceptance section) was executed in concert with the CR-ES-004 promotion.

The promotion to Accepted has the following consequences:

* CR-ES-004 is binding on all subsequent Enterprise-Semantics concept records.
* The 5 Agentic concepts (Agent + Agentic + Intent + Authority + Action) are foundational ;; further specialisations must reference this ADR rather than independently redefining Agentic.
* The 11 Agentic governed predicates (per CR-ES-004 §10) are authoritative, any new Agentic relationship must be added via the governed vocabulary process (relationships/vocabulary.yaml).
* The 4 critical boundary distinctions are now load-bearing, AI Agent = Agent or AI = Agentic or Agentic = Autonomous are rejected by AG-CON-004 + AG-CON-005 + AG-CON-006 conformance rules.
* v0.4.0 is the canonical version pointer for the Agentic semantic establishment, the v0.3.0 version pointer established by VS-B ratifies this decision.
* FND-ES-AG-008 §1.3 classification (ES-canonical novelty, Tier 2 Specialisation) is operationally enforced for the Agentic construct.
* The follow-on sequence is unblocked: ADR-ES-005 (Agentic Value Stream), ADR-ES-006 (Agentic Workflow), ADR-ES-007 (Autonomous Operations), ADR-ES-008 (Agentic Capability, if needed).
* Human participation patterns (human-in/on/over-the-loop) are first-class, not exclusions, per ADR-ES-004 §16.

The 6 PRs across 6 repos that satisfy the acceptance criteria:

- enterprise-semantics PR #7 ;; VS-A ;; 5 concept records
- enterprise-semantics PR #8 ;; VS-B ;; 11 Agentic predicates + 11 inverse pairs + v0.3.0 version pointer
- enterprise-semantics-mappings PR #4 ;; VS-C ;; 2 mapping records (WSF + OpenDEA)
- enterprise-semantics-docs PR #3 ;; VS-D1a ;; 9 documentation files
- enterprise-semantics-examples PR #3 ;; VS-D1b ;; 1 OTCHERE Inc Customer Service Agent example
- enterprise-semantics-test-probe PR #3 ;; VS-D2a ;; 9 test files + 13 AG-CON rules + 5 negative tests
- enterprise-semantics-visuals PR #3 ;; VS-D2b ;; 3 PlantUML sources
- enterprise-semantics PR #9 ;; Profile ;; Agentic Profile (ES:PROFILE:AGENTIC) per CR-ES-004 §22

Promoted by: Emmanuel A. Otchere (cardinal author rule, 2026-09-23) per ADR-ES-001 §10-§11 promotion ritual.