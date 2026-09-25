CR-ES-025 : Agentic System Implementation

CR-ES-025 : Agentic System Implementation

Status: Approved for Implementation
Target Release: v2.3.0
Implements: ADR-ES-025
Dependency: SYSTEM must be canonical

1. Objective

Implement Agentic System as a governed specialization of System while maintaining the semantic distinctions among:

System
Agent
Agentic Workflow
Agentic Operations
Agentic Service
Agentic Organization
Agentic Enterprise
Autonomous System

If System is not canonical, this CR is blocked.

2. Canonical Concept

Create:

enterprise-semantics/concepts/agentic-system.yaml

Required identity:

id: AGENTIC_SYSTEM
name: Agentic System
specializes: SYSTEM
definition: >
  A System in which material system behavior incorporates
  the interpretation of delegated intent, contextual decision
  selection, action coordination, adaptation, or execution
  toward an intended outcome within defined authority, policy,
  and contextual boundaries.

3. Required Properties

Implement:

system_intent
agentic_scope
system_context
delegated_intent
authority_context
policy_context
constraint_context
interpretation_scope
decision_scope
action_selection_scope
coordination_scope
adaptation_scope
intervention_model
escalation_boundary
observation_scope
realization_mode

4. Materiality Gate

The validator must require material agentic behavior.

Valid evidence includes:

* delegated-intent interpretation;
* contextual decision selection;
* dynamic action selection;
* action coordination;
* adaptive response;
* outcome-oriented execution;
* exception handling;
* contextual escalation.

The following must not independently establish Agentic System:

AI
Automation
Agent presence
Machine Learning
API
Rules Engine
Event-driven architecture
Predictive analytics
Conversational interface
Autonomous software

5. Registry and Profile

Register:

AGENTIC_SYSTEM

Create:

ES:PROFILE:AGENTIC_SYSTEM

The profile must not infer:

AGENTIC_SYSTEM -> AUTONOMOUS_SYSTEM
AGENTIC_SYSTEM -> AGENT
AGENTIC_SYSTEM -> AGENTIC_WORKFLOW

6. Relationships

Implement canonical relationships where targets exist:

AGENTIC_SYSTEM
  -> specializes -> SYSTEM
  -> engages -> AGENT
  -> interprets -> INTENT
  -> operates-within -> AUTHORITY
  -> governed-by -> POLICY
  -> constrained-by -> CONSTRAINT
  -> responds-to -> CONTEXT
  -> selects -> ACTION
  -> coordinates -> ACTION
  -> produces -> OUTCOME
  -> adapts-to -> CONTEXT
  -> uses -> AGENTIC_WORKFLOW
  -> supports -> CAPABILITY
  -> implements -> SERVICE
  -> contributes-to -> VALUE

7. Boundary Validation

The conformance suite must explicitly distinguish:

System
    ≠ Agent
    ≠ Agentic Workflow
    ≠ Agentic Operations
    ≠ Agentic Service
    ≠ Agentic Organization
    ≠ Agentic Enterprise

and must not establish:

Agentic System -> Autonomous System

as an inheritance relationship.

8. Four-State Characterization

The model should support:

Agentic	Autonomous	System characterization
No	No	Conventional System
Yes	No	Agentic System
No	Yes	Autonomous System candidate
Yes	Yes	Agentic + Autonomous System candidate

The final two states are characterization states only. Autonomous System remains deferred until separately canonicalized.

9. Repository Artifacts

Documentation

enterprise-semantics-docs/concepts/agentic-system.md

Architecture

agentic-system-boundary.md
agentic-system-agent-boundary.md
agentic-system-workflow-boundary.md
agentic-system-operations-boundary.md
agentic-system-service-boundary.md
agentic-system-capability-boundary.md
agentic-system-authority-boundary.md
agentic-vs-autonomous-system.md

Visuals

agentic-system-boundary.puml
agentic-system-realization.puml
agentic-system-agent-boundary.puml
agentic-system-execution-boundary.puml
agentic-vs-autonomous-system.puml

Example

enterprise-semantics-examples/systems/otchere-agentic-system.yaml

The OTCHERE Inc example must demonstrate material agentic behavior and explicit authority/policy boundaries.

10. Mappings

Create:

enterprise-semantics-mappings/wsf/agentic-system.yaml
enterprise-semantics-mappings/opendea/agentic-system.yaml

Mappings must document correspondence or intended specialization only and must not alter WSF or OpenDEA.

11. Conformance Tests

Create:

ASYS-CON-001 ... ASYS-CON-021
ASYS-NEG-001 ... ASYS-NEG-018

Positive tests must cover:

* System specialization;
* delegated intent;
* contextual interpretation;
* decision selection;
* action selection;
* coordination;
* adaptation;
* outcome orientation;
* authority;
* policy;
* constraint;
* intervention;
* escalation;
* human participation;
* Agent engagement;
* Agentic Workflow integration;
* system-level realization.

Negative tests must include:

* AI = Agentic System;
* automation = Agentic System;
* Agent presence = Agentic System;
* API = Agentic System;
* autonomous software = Agentic System;
* Agentic System = Agent;
* Agentic System = Agentic Workflow;
* Agentic System = Agentic Operations;
* Agentic System = Agentic Service;
* Agentic System = Agentic Organization;
* Agentic System = Agentic Enterprise;
* Agentic System = Autonomous System;
* agentic behavior requires AI;
* agentic behavior requires autonomy;
* human participation prohibited;
* unlimited authority;
* governance unnecessary;
* policy unnecessary.

12. Provenance

provenance:
  source:
    - ADR-ES-004
    - ADR-ES-007
    - ADR-ES-022
  decision:
    - ADR-ES-025
  implementation:
    - CR-ES-025

13. Acceptance Criteria

CR-ES-025 is complete when:

* SYSTEM dependency is satisfied;
* Agentic System is canonical;
* specialization is validated;
* material agentic behavior is demonstrable;
* delegated intent is represented;
* contextual interpretation is represented;
* decision/action selection is represented;
* coordination is represented;
* adaptation is represented;
* authority/policy/constraint boundaries are explicit;
* intervention and escalation are represented;
* human participation remains valid;
* AI independence is validated;
* automation independence is validated;
* Agent boundary is validated;
* Workflow boundary is validated;
* Operations boundary is validated;
* Service boundary is validated;
* Autonomous System remains deferred;
* OTCHERE Inc example exists;
* WSF/OpenDEA mappings exist;
* documentation and visuals exist;
* positive and negative conformance tests pass;
* CI passes;
* no unauthorized concepts are introduced.

14. Release

Successful completion publishes:

Enterprise-Semantics v2.3.0

This advances the semantic sequence from cultural conditions for autonomy (ES-024) into the system behavioral layer (ES-025) without prematurely canonicalizing Autonomous System. That preserves the ES-022 specialization gate rather than creating a mechanical Agentic/Autonomous pair.

Author: Emmanuel A. Otchere (cardinal author rule, 2026-09-24)
