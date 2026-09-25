Below are the formal ADR/CR pairs for ES-020 and ES-021, keeping the semantic discipline established through ES-019. ES-021 therefore establishes the autonomous counterpart to Agentic Organization, while explicitly preserving the orthogonality between agentic behavior and autonomous progression.

ADR-ES-020 : Agentic Organization Semantic Grounding

ADR-ES-020 : Agentic Organization Semantic Grounding

Status: Accepted
Decision Type: Semantic Definition
Semantic Version Target: v1.9.0
Scope: Enterprise-Semantics
Depends On: ADR-ES-004, ADR-ES-007, ADR-ES-010, ADR-ES-011
Implementation: CR-ES-020

1. Decision

Establish Agentic Organization as a governed specialization of Organization within Enterprise-Semantics.

The canonical definition is:

An Agentic Organization is an Organization in which material organizational activities, coordination, decision-making, or execution incorporate agentic behavior to interpret delegated intent, select or coordinate actions, adapt to context, or pursue organizational outcomes within defined authority, policy, and governance boundaries.

The semantic relationship is:

Organization
      |
      +--- specializes -> Agentic Organization

Agentic Organization describes an organizational mode of operation. It does not define a technology architecture, AI architecture, organizational structure, or degree of autonomy.



2. Rationale

An organization may increasingly incorporate agentic behavior into how it:

* interprets organizational intent;
* delegates objectives;
* coordinates work;
* makes operational or managerial decisions;
* selects actions;
* responds to changing circumstances;
* manages exceptions;
* coordinates people, systems, services, and agents;
* adapts organizational activity toward intended outcomes.

These characteristics warrant a semantic distinction from an organization that merely uses Agents.

The presence of an Agent, AI system, automation, or agentic workflow inside an organization does not by itself make the organization Agentic.

Agentic characterization requires material organizational behavior.



3. Semantic Principle

The following distinctions remain normative:

Concept	Semantic meaning
Agentic	Mode of operation involving interpretation, action selection, coordination, adaptation, or delegated action
Autonomous	Independent progression within defined objectives, authority, policies, constraints, and governance
AI	Technology or computational capability
Automation	Mechanism for executing predefined or configured behavior
Organization	Entity organized to coordinate people, roles, capabilities, resources, processes, and activities toward intended outcomes

Therefore:

Agentic ≠ Autonomous
Agentic ≠ AI
Agentic ≠ Automation
Organization ≠ Enterprise

An Agentic Organization may contain autonomous components without being an Autonomous Organization.



4. Materiality Requirement

An Organization SHALL NOT be classified as Agentic merely because it:

* employs an Agent;
* uses AI;
* uses automation;
* invokes an AI service;
* operates an Agentic Workflow;
* has automated business processes;
* uses autonomous software;
* exposes an API to an Agent.

Agentic characterization requires material incorporation of agentic behavior into organizational activity.

Relevant material behavior may include:

1. organizational decision-making;
2. organizational coordination;
3. organizational execution;
4. interpretation of delegated intent;
5. dynamic action selection;
6. organizational adaptation;
7. delegated operational response;
8. exception management;
9. contextual organizational response.



5. Semantic Realization Pattern

The normative organizational pattern is:

Organizational Intent
        ->
Agentic Organization
        ->
Interpret Context
        ->
Interpret Delegated Intent
        ->
Select / Coordinate Actions
        ->
Execute
        ->
Observe Organizational Outcome
        ->
Adapt / Escalate

The behavior is bounded by:

Authority
Policy
Constraint
Governance
Accountability
Escalation

Agentic behavior therefore does not imply unrestricted organizational discretion.



6. Core Relationships

Where the referenced concepts are canonical, Agentic Organization may participate in the following relationships:

Agentic Organization
    +--- specializes -> Organization
    +--- engages -> Agent
    +--- interprets -> Intent
    +--- operates-within -> Authority
    +--- governed-by -> Policy
    +--- constrained-by -> Constraint
    +--- coordinates -> Process
    +--- uses -> Agentic Workflow
    +--- uses -> Agentic Operations
    +--- produces -> Organizational Outcome
    +--- adapts-to -> Organizational Context
    +--- exercises -> Capability
    +--- contributes-to -> Value

Only relationships whose target concepts are already canonical SHALL be activated in the implementation.



7. Boundaries

Agentic Organization vs Agentic Enterprise

Agentic Organization concerns organizational behavior.

Agentic Enterprise concerns enterprise-level value realization and enterprise operation.

An enterprise may contain Agentic Organizations without the entire enterprise being characterized as Agentic.

Agentic Organization vs Agentic Operations

Agentic Operations describe the agentic operation of an operational environment.

Agentic Organization describes the organizational entity and its organizational behavior.

Agentic Organization vs Agentic Workflow

Agentic Workflow describes agentic coordination or execution of work.

Agentic Organization describes organizational behavior that may use such workflows.

Agentic Organization vs Agent

An Agent performs or coordinates actions.

An Agentic Organization is an Organization whose material behavior incorporates agentic operation.

Agentic Organization vs Agentic Culture

Agentic Culture concerns organizational norms, values, behaviors, and cultural patterns.

Agentic Organization concerns organizational operation and coordination.

Agentic Organization vs Autonomous Organization

Agentic behavior does not establish organizational autonomy.

Autonomous Organization requires a separate semantic decision.



8. Human Participation

Human participation remains compatible with Agentic Organization.

Agentic organizational behavior may include:

* human-in-the-loop;
* human-on-the-loop;
* human-over-the-loop;
* delegated human authority;
* escalation to human authority;
* collaborative human-agent decision-making.

Agentic Organization therefore does not imply removal of managers, employees, governance bodies, or human accountability.



9. Explicit Non-Equivalences

The following SHALL NOT be inferred:

Agentic Organization -> AI Organization
Agentic Organization -> Automated Organization
Agentic Organization -> Agentic Enterprise
Agentic Organization -> Agentic Operations
Agentic Organization -> Agentic Workflow
Agentic Organization -> Autonomous Organization
Agentic Organization -> Human-free Organization
Agentic Organization -> Agent-controlled Organization



10. Enterprise Example

For OTCHERE Inc, an Agentic Organization may have organizational intent delegated through defined authority boundaries.

The organization may:

1. interpret organizational context;
2. interpret delegated organizational intent;
3. coordinate people, agents, systems, and services;
4. dynamically select organizational actions;
5. execute coordinated responses;
6. observe organizational outcomes;
7. adapt organizational activity;
8. escalate decisions exceeding delegated authority.

The organization remains governed by policies, accountability structures, constraints, and human authority.



11. Deferred Concepts

This ADR does not establish:

* Autonomous Organization;
* Agentic Culture;
* Autonomous Culture;
* Agentic Ecosystem;
* Autonomous Ecosystem;
* Agentic Network;
* Autonomous Network;
* Agentic Management;
* Autonomous Management;
* Agent hierarchy;
* Organizational autonomy maturity;
* Agentic organizational maturity.

These require independent semantic decisions.



12. Consequences

Positive

* Establishes an organizational semantic boundary for agentic behavior.
* Prevents Agentic Enterprise from absorbing organizational semantics.
* Preserves Agentic/Autonomous orthogonality.
* Separates organizational behavior from AI technology.
* Supports future autonomous organization semantics without prematurely defining them.
* Provides a reusable semantic foundation for enterprise architecture and organizational modeling.

Constraints

* Materiality must be demonstrated.
* Agent presence alone is insufficient.
* Implementations must respect canonical dependency gates.
* Autonomous Organization must not be inferred from this ADR.



13. Decision Outcome

Agentic Organization is established as a specialization of Organization.

Target semantic release:

Enterprise-Semantics v1.9.0


Author: Emmanuel A. Otchere (cardinal author rule, 2026-09-24)


