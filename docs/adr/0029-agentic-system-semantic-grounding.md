ADR-ES-025 : Agentic System Semantic Grounding

The next specialization passes the ES-022 gate because System is materially affected by agentic behavior at the system operating boundary: interpretation, decision selection, coordination, adaptation, and execution. Importantly, this does not make every system containing AI, automation, or an Agent an Agentic System.

ADR-ES-025 : Agentic System Semantic Grounding

Status: Accepted
Date Accepted: 2026-09-25
Semantic Version: v2.3.0
Scope: Enterprise-Semantics
Depends on: ADR-ES-004, ADR-ES-007, ADR-ES-022
Implementation: CR-ES-025

1. Decision

Establish Agentic System as a canonical specialization of System, subject to the canonicalization of System.

Canonical Definition

An Agentic System is a System in which material system behavior incorporates the interpretation of delegated intent, contextual decision selection, action coordination, adaptation, or execution toward an intended outcome within defined authority, policy, and contextual boundaries.

The specialization is:

System
   |
   +--- specializes
          ->
   Agentic System

If System is not canonical, CR-ES-025 is blocked.

2. Semantic Rationale

A System describes an organized arrangement of interacting elements that produces or supports intended behavior or outcomes.

Agentic System adds a distinct behavioral characteristic: the system materially participates in interpreting intent and selecting, coordinating, adapting, or executing actions rather than merely executing predetermined behavior.

The distinction is therefore behavioral and semantic, not technological.

3. Agentic System Materiality

An Agentic System must materially exhibit one or more of:

* interpretation of delegated intent;
* contextual assessment influencing action selection;
* dynamic decision selection;
* action selection;
* coordination of actions or participants;
* adaptation to changing context;
* outcome-oriented execution;
* exception handling within authority;
* contextual escalation.

Merely incorporating an Agent does not establish an Agentic System.

Likewise, the following are insufficient by themselves:

* AI;
* machine learning;
* automation;
* rules engines;
* APIs;
* event-driven architecture;
* autonomous software;
* conversational interfaces;
* predictive analytics.

4. Agentic System Operating Pattern

The canonical pattern is:

System Intent
      ->
System Context
      ->
Interpret / Assess
      ->
Select Decision / Action
      ->
Coordinate / Execute
      ->
Observe Outcome
      ->
Adapt / Escalate
      ↺

The behavior remains bounded by:

Authority
Policy
Constraint
Context
Governance
Escalation

5. Agentic System and Agent

An Agent and an Agentic System are distinct.

Agent
  = Entity capable of interpreting delegated intent,
    selecting/coordinating actions, and acting within authority.
Agentic System
  = System whose material behavior incorporates
    agentic interpretation, decision, coordination,
    adaptation, or execution.

A System may:

* engage an Agent;
* contain an Agent;
* coordinate Agents;
* operate alongside Agents;

without automatically being an Agentic System.

Conversely, an Agentic System need not be defined as an Agent.

6. Agentic System and Agentic Workflow

The distinction is:

Agentic System
    ->
system-level behavior and interaction
Agentic Workflow
    ->
work coordination / execution behavior

An Agentic Workflow may be implemented by an Agentic System, but the concepts remain semantically distinct.

7. Agentic System and Agentic Operations

The distinction is:

Agentic System
    = behavior of a system
Agentic Operations
    = agentic mode of operating an operational environment

An Agentic System can support Agentic Operations without being synonymous with them.

Agentic Operations can coordinate multiple systems.

8. Agentic System and Autonomy

Agentic behavior does not imply autonomy.

The following remain valid:

Agentic-only
Autonomous-only
Agentic + Autonomous
Neither

Autonomy requires an independent-progression semantic determination and must not be inferred merely from Agentic System behavior.

No Autonomous System specialization is established by this ADR.

9. Human Participation

An Agentic System may require or support human participation through:

* human-in-the-loop;
* human-on-the-loop;
* human-over-the-loop;
* approval boundaries;
* exception handling;
* escalation;
* governance;
* policy definition.

Agentic System does not imply human exclusion.

10. Canonical Relationships

Where targets are canonical, Agentic System may:

* specialize -> System
* engage -> Agent
* interpret -> Intent
* operate-within -> Authority
* governed-by -> Policy
* constrained-by -> Constraint
* responds-to -> Context
* selects -> Action
* coordinates -> Action
* produces -> Outcome
* adapts-to -> Context
* uses -> Agentic Workflow
* supports -> Capability
* implements -> Service
* contributes-to -> Value

No relationship should introduce a non-canonical target merely to complete symmetry.

11. Boundary Conditions

Agentic System is explicitly not:

* Agent;
* Agentic Workflow;
* Agentic Operations;
* Agentic Organization;
* Agentic Enterprise;
* Agentic Service;
* Agentic Product;
* Agentic Offering;
* Autonomous System;
* AI System merely because it uses AI;
* Automated System merely because it automates execution.

12. Illustrative Example

For OTCHERE Inc, an order orchestration system could qualify as an Agentic System where it:

1. receives delegated fulfillment intent;
2. interprets customer, inventory, delivery and operational context;
3. evaluates available execution options;
4. selects or coordinates actions within defined authority;
5. dynamically responds to operational changes;
6. observes fulfillment outcomes;
7. adapts or escalates within policy boundaries.

A conventional rules-based order processing platform would not become Agentic System merely because it contains automation.

13. Deferred Concepts

This ADR does not establish:

* Autonomous System;
* Agentic Ecosystem;
* Autonomous Ecosystem;
* Agentic Network;
* Autonomous Network;
* AI Agent;
* Agentic AI;
* AI-Native System;
* autonomous system maturity;
* system autonomy levels.

Each requires an independent semantic specialization assessment.

14. Decision Outcome

Agentic System is established as a canonical specialization of System, subject to the System dependency gate and successful implementation through CR-ES-025.

Target release: v2.3.0.


Author: Emmanuel A. Otchere (cardinal author rule, 2026-09-24)


## Promotion Note

Promoted via 2-touchpoint ritual per ES series ADR-ES-001 section 10-11.

Per user directive message 1553040695345025105 + Culture-System_Resolution.md, this specialization tranche was implemented + promoted after foundational System (ES-027) was established.

Dependency gate RESOLVED: parent System concept is now canonical on origin/main per ADR-ES-027 + CR-ES-027 Accepted.

Autonomous System remains deferred per ADR-ES-022 section 13 (mechanical symmetry prohibition).

Status: Accepted. Date Accepted: 2026-09-25.

Emmanuel A. Otchere (cardinal author rule, 2026-09-24).
