<!--
ADR-ES-012 , Agentic Capability Semantic Grounding Decision

Dash-normalized: colons (:) and semicolons (;) used consistently.
Verbatim original: 00_inbox/ADR-ES-012.md (em-dashes and ellipsis dividers preserved in source).

Status: Accepted (promoted from Proposed on 2026-09-24 per user directive message 1552696611153649796, "Proceed promotion")
Decision Type: Foundational Semantic Specialization
Scope: Enterprise-Semantics
Supersedes: None
Depends on: ADR-ES-001 (Authority and Publication Architecture) , ADR-ES-002 (Enterprise Semantic Model) , ADR-ES-004 (Agentic Semantic Grounding) , ADR-ES-006 (Agentic Workflow Semantic Grounding, Accepted 2026-09-23) , ADR-ES-007 (Agentic Operations Semantic Grounding, Accepted 2026-09-23) , ADR-ES-010 (Agentic Enterprise Semantic Grounding, Accepted 2026-09-24) , ADR-ES-011 (Autonomous Enterprise Semantic Grounding, Accepted 2026-09-24)
Related: CR-ES-012 (Agentic Capability Semantic Grounding, Accepted 2026-09-24) , ADR-ES-013 (Autonomous Capability Semantic Grounding, Deferred per ADR-ES-012 §25) , FND-ES-AG-008 (WSF Tier 1 / Tier 2 Grounding Boundary, Established 2026-09-22)

Decision: Establish Agentic Capability as a governed semantic specialization of Capability describing a Capability whose realization materially incorporates agentic behavior in achieving or enabling an intended Outcome within defined authority, policy, and contextual boundaries. Agentic Capability is a contextual specialization of the universal Capability concept established by ADR-ES-002, not a new foundational type of ability, it does not redefine what a Capability is, and it does not equate ability with the Agent, Workflow, Operations, Value Stream, AI, automation, or autonomy mechanisms through which that ability may be realized. Deliberately avoids premature canonicalization of Autonomous Capability, AI Capability, Agentic Capability maturity levels, Agentic Organization, Agentic Culture, Agentic Ecosystem.

Slot note: this ADR is filed at governance repo docs/adr/0014-... Slot 0014 is the next free slot in the ES series. The ES series slot sequence is 0001 (Authority) , 0002 (Enterprise Semantic Model) , 0003 (Agentic Semantic Decision, ES-AG) , 0004 (Capability, ES) , 0005 (Value Stream, ES) , 0006 (Agentic, ES) , 0007 (Agentic Value Stream, ES) , 0008 (Agentic Workflow, ES) , 0009 (Agentic Operations, ES) , 0010 (Autonomous Operations, ES) , 0011 (Autonomous Value Stream, ES) , 0012 (Agentic Enterprise, ES) , 0013 (Autonomous Enterprise, ES) , 0014 (Agentic Capability, ES, this ADR).

Implementation: CR-ES-012 (Agentic Capability Semantic Grounding). CR-ES-012 is the implementation specification, this ADR ratifies it as a governed semantic decision.

Authored by: Emmanuel A. Otchere (cardinal author rule, 2026-09-24)
-->

ADR-ES-012 , Agentic Capability Semantic Grounding

ADR-ES-012 : Agentic Capability Semantic Grounding

1. Decision

Establish Agentic Capability as a governed semantic specialization of Capability.

The canonical definition is:

An Agentic Capability is a Capability whose realization materially incorporates agentic behavior in achieving or enabling an intended Outcome within defined authority, policy, and contextual boundaries.

The core semantic relationship is:

Capability
    |
    |-- Agentic Capability
             |
             +-- realizes through -> Agentic Workflow
             +-- supports -> Agentic Operations
             +-- enables -> Outcome
             |-- may enable -> Agentic Value Stream

Agentic Capability is therefore not a new foundational type of ability.

It is a contextual specialization describing how a Capability is materially realized.
;;;
2. Existing Capability Grounding

ADR-ES-002 established:

A Capability is an enduring ability of an Entity to achieve or enable an Outcome.

This definition remains authoritative.

Agentic Capability does not replace, redefine, or narrow Capability.

Therefore:

Capability
   +-- Conventional Capability
   +-- Agentic Capability
   |-- Other future contextual specializations

The model must preserve the universal nature of Capability.
;;;
3. Problem

The preceding agentic semantic model establishes agentic behavior across:

Agent
Agentic Workflow
Agentic Operations
Agentic Value Stream
Agentic Enterprise

However, Capability currently has no formal semantic mechanism for expressing that a particular enterprise ability is materially realized through agentic behavior.

Without this concept, the model creates a gap between:

Enterprise Strategy
       ->
Capability
       ->
Value Stream / Process / Operations

and the agentic realization model:

Agent
       ->
Agentic Workflow
       ->
Agentic Operations
       ->
Agentic Value Stream

Agentic Capability provides the missing semantic bridge.
;;;
4. Core Semantic Principle

Agentic Capability describes what an Entity is able to achieve or enable, while Agentic describes how that capability is materially realized.

Therefore:

Capability
        = enduring ability
Agentic Capability
        = enduring ability
          + material agentic realization

The distinction must remain explicit.
;;;
5. Agentic Capability Boundary

The primary question is:

Does the capability’s realization materially incorporate agentic behavior?

It is not:

Does the enterprise possess an Agent?

Nor:

Does the capability use AI?

Nor:

Is the capability automated?

Nor:

Is the capability autonomous?

Therefore:

Agentic Capability
        ≠
Capability containing an Agent

and:

Agentic Capability
        ≠
AI Capability

and:

Agentic Capability
        ≠
Automated Capability
;;;
6. Capability and Agentic Realization

The conceptual model is:

Capability
     |
     v
Agentic Capability
     |
     +-- enables -> Outcome
     |
     +-- realized-through -> Agentic Workflow
     |
     +-- supported-by -> Agent
     |
     +-- exercised-by -> Role
     |
     +-- supported-by -> Resource
     |
     +-- delivered-through -> Service
     |
     |-- implemented-by -> System

These relationships inherit the Capability semantics established by ADR-ES-002 where applicable.

Agentic realization adds the behavioral dimension.
;;;
7. Materiality Requirement

A Capability must not be classified as Agentic merely because an Agent participates somewhere in its implementation.

Agentic behavior must be material to capability realization.

Examples of material agentic participation include:

* contextual decision-making
* dynamic action selection
* adaptive coordination
* delegated execution
* contextual exception handling
* agentic interaction with stakeholders
* agentic resource coordination
* adaptive fulfillment of the capability’s intended outcome

The mere use of an Agent as a tool does not automatically qualify.
;;;
8. Capability Realization Boundary

The architecture distinguishes:

CAPABILITY
"What enduring ability exists?"
        ->
AGENTIC CAPABILITY
"Is the ability materially realized agentically?"
        ->
REALIZATION
Agentic Workflow / Agentic Operations / Service / System / Human
        ->
OUTCOME

Capability therefore remains upstream of specific execution mechanisms.
;;;
9. Relationship to Agent

An Agent may participate in the realization of an Agentic Capability.

Agentic Capability
        ->
realized-through
        ->
Agent

However, the Agent is not the Capability.

Therefore:

Agent ≠ Capability
Agent ≠ Agentic Capability

An Agent is an acting Entity.

A Capability is an enduring ability.
;;;
10. Relationship to Agentic Workflow

Agentic Workflow may realize an Agentic Capability.

Agentic Capability
        ->
realized-through
        ->
Agentic Workflow

However:

Agentic Capability
        ≠
Agentic Workflow

The distinction remains:

* Capability = ability
* Workflow = coordinated execution
;;;
11. Relationship to Agentic Operations

Agentic Operations may support or realize an Agentic Capability.

Agentic Capability
        ->
supported-by / realized-through
        ->
Agentic Operations

The exact relationship shall use only predicates already established in the relationship vocabulary.

Agentic Operations remain an operational boundary.

Agentic Capability remains a capability boundary.
;;;
12. Relationship to Value Stream

An Agentic Capability may enable an Agentic Value Stream.

Agentic Capability
        ->
enables
        ->
Agentic Value Stream

This does not imply:

Agentic Capability
        = 
Agentic Value Stream

The semantic distinction remains:

Capability -> ability
Value Stream -> value realization
;;;
13. Relationship to Autonomous Capability

This ADR does not establish Autonomous Capability.

Autonomous Capability may be a future specialization describing the independent realization of a Capability.

For example:

Capability
   +-- Agentic Capability
   |-- Autonomous Capability      <- future

The concepts must not be conflated.

An Agentic Capability may be:

* non-autonomous
* partially autonomous
* fully autonomous within its defined boundary

but autonomy must not be inferred from Agentic Capability.
;;;
14. Agentic / Autonomous Orthogonality

The semantic architecture therefore permits:

Capability
    |
    +-- Agentic
    |
    +-- Autonomous
    |
    |-- Agentic + Autonomous

However, only Agentic Capability is established by this ADR.

Autonomous Capability remains deferred.
;;;
15. AI Boundary

AI is not required.

An Agentic Capability may use AI, but:

AI
   ≠
Agentic Capability

Similarly:

AI-enabled Capability
   ≠
Agentic Capability

An AI system may support a Capability without the Capability being materially agentic.
;;;
16. Automation Boundary

Automation does not establish Agentic Capability.

Automated Capability
   ≠
Agentic Capability

A predefined automated mechanism can support a Capability without interpreting delegated intent, selecting actions contextually, or adapting behavior.
;;;
17. Agentic Enterprise Relationship

An Agentic Enterprise may possess Agentic Capabilities.

Agentic Enterprise
        ->
possesses
        ->
Agentic Capability

However:

Agentic Capability
        ≠
Agentic Enterprise

A single Agentic Capability does not establish Agentic Enterprise.

Enterprise-level materiality remains a separate qualification boundary.
;;;
18. Capability Portfolio Relationship

Agentic Capability may be used to characterize selected portions of an enterprise capability portfolio.

Example:

OTCHERE Inc Capability Portfolio
Customer Service
     |
     |-- Agentic Customer Service Capability
Fulfillment Management
     |
     |-- Agentic Fulfillment Coordination Capability
Supply Management
     |
     |-- Conventional / mixed realization
Financial Management
     |
     |-- Conventional / mixed realization

This allows capability transformation to be modeled incrementally rather than declaring an entire enterprise agentic.
;;;
19. Capability Transformation

The model supports transformation from conventional realization toward agentic realization:

Capability
    ->
Capability Assessment
    ->
Agentic Realization Design
    ->
Agentic Capability
    ->
Agentic Workflow / Operations
    ->
Outcome

The Capability itself remains semantically stable while its realization mode may change.

This distinction is important for enterprise architecture and transformation management.
;;;
20. Agentic Capability Characteristics

An Agentic Capability may exhibit:

1. delegated intent interpretation
2. contextual interpretation
3. dynamic action selection
4. agentic coordination
5. adaptive realization
6. bounded authority
7. outcome orientation
8. contextual decision-making
9. exception interpretation
10. escalation

Not every characteristic must occur independently; the qualification requirement is material agentic realization.
;;;
21. Capability Realization Pattern

The canonical pattern is:

Capability Intent
        ->
Agentic Capability
        ->
Context
        ->
Interpretation
        ->
Decision
        ->
Action Selection
        ->
Execution
        ->
Outcome
        ->
Adaptation

Bounded by:

Authority
Policy
Constraints

This connects the capability model to the established agentic execution semantics without making Workflow or Agent a subtype of Capability.
;;;
22. Example: OTCHERE Inc

Consider Customer Resolution as an enterprise Capability.

A conventional realization might be:

Customer Issue
      ->
Human Assessment
      ->
Predefined Process
      ->
Resolution

An Agentic Capability realization may be:

Customer Issue
      ->
Context Interpretation
      ->
Determine Resolution Intent
      ->
Select Authorized Action
      ->
Coordinate Service
      ->
Observe Outcome
      ->
Adapt / Escalate

The enduring ability remains:

The ability to resolve customer issues toward a satisfactory outcome.

What changes is the realization mode.

Therefore:

Customer Resolution Capability
             ->
Agentic Customer Resolution Capability

is a semantic specialization rather than the creation of an entirely new business ability.
;;;
23. Conformance Invariants

ACAP-CON-001
Agentic Capability specializes Capability.

ACAP-CON-002
Agentic Capability retains the Capability definition of enduring ability.

ACAP-CON-003
Agentic behavior must be material to realization.

ACAP-CON-004
Agentic Capability remains outcome-oriented.

ACAP-CON-005
Agentic Capability may engage an Agent.

ACAP-CON-006
Agentic Capability may be realized through Agentic Workflow.

ACAP-CON-007
Agentic Capability may be supported by Agentic Operations.

ACAP-CON-008
Agentic Capability may enable Agentic Value Stream realization.

ACAP-CON-009
Agentic Capability does not require AI.

ACAP-CON-010
Automation does not establish Agentic Capability.

ACAP-CON-011
Agentic Capability does not imply autonomy.

ACAP-CON-012
Agentic Capability does not imply Agentic Enterprise.

ACAP-CON-013
Agent is not a subtype of Capability.

ACAP-CON-014
Agentic Workflow is not a subtype of Capability.

ACAP-CON-015
Agentic Operations is not a subtype of Capability.

ACAP-CON-016
Agentic Value Stream is not a subtype of Capability.

ACAP-CON-017
Agentic Capability operates within appropriate authority boundaries.

ACAP-CON-018
Agentic Capability requires provenance and semantic grounding.
;;;
24. Explicitly Rejected Interpretations

The following are rejected:

* Agentic Capability = AI Capability
* Agentic Capability = Automated Capability
* Agentic Capability = Agent
* Agentic Capability = Agentic Workflow
* Agentic Capability = Agentic Operations
* Agentic Capability = Agentic Value Stream
* Agentic Capability = Capability containing an Agent
* Agentic Capability = Autonomous Capability
* Agentic Capability = Enterprise Capability that uses AI
* Agentic Capability = Capability requiring full autonomy
* Agentic Capability = Capability with no human participation
;;;
25. Future Concepts Deferred

This ADR does not establish:

* Autonomous Capability
* AI Capability
* Agentic Capability Maturity
* Agentic Capability Levels
* Agentic Organization
* Autonomous Organization
* Agentic Culture
* Autonomous Culture
* Agentic Ecosystem
* Autonomous Ecosystem

Each requires independent semantic grounding.
;;;
26. Consequences

Positive

* Extends the universal Capability semantic model into agentic realization.
* Provides an architectural bridge between Capability and the agentic execution model.
* Allows selective capability transformation.
* Prevents AI from becoming the definition of agentic capability.
* Preserves the distinction between ability and execution.
* Supports enterprise capability portfolios containing mixed realization modes.
* Enables future autonomous capability semantics without conflating them with agentic capability.

Negative

* Qualification requires evidence that agentic behavior is material to capability realization.
* Capability transformation semantics may eventually require explicit realization-state modeling.
* Autonomous Capability remains a future semantic decision.
;;;
27. Decision Summary

The semantic architecture now establishes:

Capability
    |
    |-- Agentic Capability
            |
            +-- enables -> Outcome
            +-- realized-through -> Agentic Workflow
            +-- supported-by -> Agentic Operations
            +-- engages -> Agent
            |-- enables -> Agentic Value Stream

The governing principle is:

Agentic Capability describes an enduring ability whose realization materially incorporates agentic behavior; it does not redefine Capability, and it does not equate ability with the Agent, Workflow, Operations, Value Stream, AI, automation, or autonomy mechanisms through which that ability may be realized.

