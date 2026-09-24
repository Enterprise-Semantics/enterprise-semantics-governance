<!--
ADR-ES-014 , Agentic Service Semantic Grounding Decision

Dash-normalized: colons (:) and semicolons (;) used consistently.
Verbatim original: 00_inbox/ADR-ES-014.md (em-dashes and ellipsis dividers preserved in source).

Status: Proposed
Decision Type: Foundational Semantic Specialization
Scope: Enterprise-Semantics
Supersedes: None
Depends on: ADR-ES-002 (Enterprise Semantic Model) , ADR-ES-003 (Value Stream Semantic Grounding, Accepted 2026-09-23) , ADR-ES-004 (Agentic Semantic Grounding) , ADR-ES-005 (Agentic Value Stream Semantic Grounding, Accepted 2026-09-23) , ADR-ES-006 (Agentic Workflow Semantic Grounding, Accepted 2026-09-23) , ADR-ES-007 (Agentic Operations Semantic Grounding, Accepted 2026-09-23) , ADR-ES-012 (Agentic Capability Semantic Grounding, Accepted 2026-09-24)
Related: CR-ES-014 (Agentic Service Semantic Grounding, Proposed) , ADR-ES-015 (Autonomous Service Semantic Grounding, Deferred per ADR-ES-014 §19) , FND-ES-AG-008 (WSF Tier 1 / Tier 2 Grounding Boundary, Established 2026-09-22)

Decision: Establish Agentic Service as a governed semantic specialization of Service describing a Service whose delivery or interaction materially incorporates agentic behavior in interpreting intent, selecting or coordinating actions, adapting service behavior, or executing service responses toward an intended outcome within defined authority, policy, and contextual boundaries. Agentic Service is a contextual specialization of the Service concept, not a new foundational type of service, and does not make AI, automation, autonomy, or an Agent a prerequisite. Deliberately avoids premature canonicalization of Autonomous Service, Autonomous Service maturity, AI Service, AI-native Service, Agentic Product, Autonomous Product, Agentic Contract, Agentic Agreement, Autonomous Organization, Agentic Organization, Service autonomy levels.

Slot note: this ADR is filed at governance repo docs/adr/0016-... Slot 0016 is the next free slot in the ES series. The ES series slot sequence continues from 0015 (Autonomous Capability) ; 0016 (Agentic Service, ES, this ADR).

Implementation: CR-ES-014 (Agentic Service Semantic Grounding). CR-ES-014 is the implementation specification, this ADR ratifies it as a governed semantic decision.

Authored by: Emmanuel A. Otchere (cardinal author rule, 2026-09-24)
-->

ADR-ES-014 , Agentic Service Semantic Grounding

ADR-ES-014: Agentic Service Semantic Grounding

1. Decision

Establish Agentic Service as a governed semantic specialization of Service.

Canonical definition

An Agentic Service is a Service whose delivery or interaction materially incorporates agentic behavior in interpreting intent, selecting or coordinating actions, adapting service behavior, or executing service responses toward an intended outcome within defined authority, policy, and contextual boundaries.

The specialization is:

Service
   |
   |-- Agentic Service

Agentic Service does not redefine Service and does not make AI, automation, autonomy, or an Agent a prerequisite.
;;;
2. Semantic Rationale

The semantic architecture currently establishes agentic specializations across:

Capability
Value Stream
Workflow
Operations
Enterprise

Service is the next important boundary because a Service represents a means through which a capability or value is made available to a consumer or stakeholder.

The distinction is therefore:

Agentic Capability
        |
        +-- may be delivered-through ---> Agentic Service
        |
        |-- may enable ----------------> Agentic Value Stream

An Agentic Service is consequently concerned with agentic service delivery or interaction, rather than with the entire value stream or the underlying capability.
;;;
3. Service Semantics

The existing semantic meaning of Service shall remain authoritative.

Agentic Service retains the essential characteristics of Service, including its relationship to:

* provider
* consumer
* service interaction
* service outcome
* service delivery
* capability realization

Agentic behavior qualifies how the service is delivered or interacted with.

It does not change the fundamental identity of Service.
;;;
4. Agentic Materiality

A Service shall not become Agentic merely because it:

* invokes an Agent,
* uses AI,
* uses automation,
* exposes an API,
* contains an AI model,
* supports conversational interaction,
* is implemented by an autonomous system.

Agentic behavior must be material to service realization.

Examples of material agentic behavior include:

1. interpreting delegated service intent;
2. interpreting contextual service conditions;
3. dynamically selecting service actions;
4. dynamically coordinating service actions;
5. adapting service behavior;
6. interpreting service exceptions;
7. deciding within bounded service authority;
8. escalating when authority or policy boundaries are reached.
;;;
5. Canonical Agentic Service Pattern

Service Intent
      ->
Agentic Service
      ->
Service Context
      ->
Interpretation
      ->
Decision / Action Selection
      ->
Service Execution
      ->
Service Outcome
      ->
Contextual Adaptation
      ↺

Bounded by:

Authority
Policy
Constraints
Service Contract
Governance
Escalation

The pattern may include:

Human
Agent
System
Service
Workflow
Agentic Workflow

No particular implementation mechanism is required.
;;;
6. Core Semantic Distinctions

Agentic Service vs Agent

Agent
= Entity capable of interpreting delegated intent,
  selecting/coordinating actions, and acting within authority.
Agentic Service
= Service whose realization materially incorporates
  agentic behavior.

An Agent may participate in an Agentic Service without being the Service itself.

Therefore:

Agent ≠ Agentic Service
;;;
7. Agentic Service vs Agentic Capability

Agentic Capability
= enduring ability to achieve or enable an Outcome
  through material agentic realization.
Agentic Service
= means through which a capability or service outcome
  is made available through material agentic realization.

A capability may be delivered through an Agentic Service.

An Agentic Service may expose or enable capabilities that are not themselves Agentic Capabilities.

Therefore:

Agentic Capability ≠ Agentic Service
;;;
8. Agentic Service vs Agentic Workflow

Agentic Workflow
= agentic coordination/execution of work.
Agentic Service
= agentic realization of a service interaction or delivery.

An Agentic Service may use one or more Agentic Workflows.

The workflow is an execution mechanism; the service is the service-level offering/delivery construct.

Therefore:

Agentic Service ≠ Agentic Workflow
;;;
9. Agentic Service vs Agentic Operations

Agentic Operations
= agentic operating mode for ongoing operational activity.
Agentic Service
= service realization through agentic behavior.

An Agentic Service may operate within Agentic Operations.

Agentic Operations do not make every Service Agentic.

Therefore:

Agentic Service ≠ Agentic Operations
;;;
10. Agentic Service vs Agentic Value Stream

Agentic Value Stream
= end-to-end stakeholder value realization
  materially involving agentic behavior.
Agentic Service
= service-level delivery or interaction
  materially involving agentic behavior.

An Agentic Value Stream may use multiple Agentic Services.

An Agentic Service does not imply an Agentic Value Stream.

Therefore:

Agentic Service ≠ Agentic Value Stream
;;;
11. Agentic / Autonomous Orthogonality

Agentic Service establishes only the agentic dimension.

It does not establish Autonomous Service.

The following states remain semantically possible:

Agentic	Autonomous	Interpretation
No	No	Conventional Service
Yes	No	Agentic Service
No	Yes	Future Autonomous Service
Yes	Yes	Future combined characterization

Autonomous Service requires a separate ADR.

This ADR therefore does not establish:

Autonomous Service
;;;
12. AI Boundary

AI may be used to implement an Agentic Service.

However:

AI-enabled Service ≠ Agentic Service

and:

Agentic Service does not require AI

A deterministic or non-AI mechanism may exhibit agentic service behavior where the semantic conditions are satisfied.
;;;
13. Automation Boundary

Automation may participate in an Agentic Service.

However:

Automated Service ≠ Agentic Service

Automation provides an execution mechanism.

Agentic behavior concerns contextual interpretation, action selection, coordination, adaptation, and bounded decision behavior.
;;;
14. Human Participation

Human participation does not invalidate Agentic Service.

An Agentic Service may use:

* human-in-the-loop;
* human-on-the-loop;
* human-over-the-loop;
* human escalation;
* approval gates;
* exception handling.

The defining property is agentic service realization, not removal of humans.
;;;
15. Canonical Relationships

Subject to existing canonical vocabulary:

Agentic Service
    +-- specializes -> Service
    +-- engages -> Agent
    +-- interprets -> Intent
    +-- operates-within -> Authority
    +-- governed-by -> Policy
    +-- uses -> Agentic Workflow
    +-- produces -> Outcome
    +-- adapts-to -> Context
    +-- delivers -> Value
    |-- supports -> Capability

Only relationships whose predicates and target concepts are already canonical shall be implemented.

No relationship shall silently create a new foundational concept.
;;;
16. Service Interaction Boundary

The service-level semantic boundary is:

STAKEHOLDER / CONSUMER
        |
        | Service Interaction
        ->
AGENTIC SERVICE
        |
        +-- interprets intent
        +-- evaluates context
        +-- selects action
        +-- coordinates execution
        +-- adapts response
        |-- escalates exceptions
        |
        ->
SERVICE OUTCOME

This is distinct from the underlying execution boundary:

Agentic Service
       ->
Agentic Workflow
       ->
Activity / Task
       ->
Agent / Human / System
;;;
17. Conformance Invariants

The following are canonical invariants:

Agentic Service is-a Service
Agentic Service ≠ Agent
Agentic Service ≠ Capability
Agentic Service ≠ Agentic Capability
Agentic Service ≠ Agentic Workflow
Agentic Service ≠ Agentic Operations
Agentic Service ≠ Agentic Value Stream
Agentic Service does not require AI
Agentic Service does not require automation
Automation does not establish Agentic Service
AI does not establish Agentic Service
Agentic Service does not imply Autonomous Service
Agentic Service does not imply Autonomous Operations
Agentic Service does not imply Autonomous Value Stream
Agentic Service does not imply Autonomous Enterprise
Human participation does not invalidate Agentic Service
Agentic behavior must be material to service realization
;;;
18. Example: OTCHERE Inc Customer Resolution Service

OTCHERE Inc provides a Customer Resolution Service.

A conventional implementation may route every request according to predefined rules.

An Agentic Customer Resolution Service may:

Customer Intent
       ->
Interpret Customer Context
       ->
Determine Resolution Path
       ->
Check Service Authority
       ->
Select Permitted Action
       ->
Coordinate Fulfillment
       ->
Observe Customer Response
       ->
Adapt / Escalate
       ↺

The service remains a Service.

Its agentic nature derives from the material agentic behavior through which service realization occurs.

A human may intervene where:

* authority is exceeded;
* policy requires approval;
* an exception is ambiguous;
* the customer requests human escalation.
;;;
19. Deferred Concepts

This ADR does not establish:

* Autonomous Service
* Autonomous Service maturity
* AI Service
* AI-native Service
* Agentic Product
* Autonomous Product
* Agentic Contract
* Agentic Agreement
* Autonomous Organization
* Agentic Organization
* Service autonomy levels

Each requires separate semantic grounding.
;;;
20. Consequences

Positive

* extends agentic semantics into the service layer;
* preserves Service as the foundational concept;
* separates service realization from capability, workflow, operations, and value-stream semantics;
* provides a technology-neutral definition;
* enables Agentic Capability -> Agentic Service -> Agentic Value Stream traceability;
* supports future autonomous service semantics without conflating autonomy and agentic behavior.

Constraints

* agentic participation must be material;
* AI cannot be used as a semantic shortcut;
* automation cannot be used as a semantic shortcut;
* autonomous behavior cannot be inferred;
* service contracts, authority, policies, and escalation boundaries must remain explicit where applicable.
;;;
21. Provenance

provenance:
  source:
    - ADR-ES-002
    - ADR-ES-003
    - ADR-ES-004
    - ADR-ES-005
    - ADR-ES-006
    - ADR-ES-007
    - ADR-ES-012
  decision:
    - ADR-ES-014

Decision: Establish Agentic Service as a governed specialization of Service and authorize CR-ES-014 implementation.
