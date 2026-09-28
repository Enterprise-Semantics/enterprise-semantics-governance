# ADR-ES-033 ; Loop Engineering Semantic Grounding

Status: Proposed
Date: 2026-09-28
Deciders: eaojnr
Target Semantic Version: 2.9.0
Semantic Kind: engineering_practice (NOT a specialization)

## 1. Decision

Enterprise-Semantics SHALL establish Loop Engineering as a governed semantic concept describing the deliberate design, implementation, instrumentation, operation, evaluation, and improvement of closed-loop behavior.

Loop Engineering SHALL NOT be modeled as a specialization of System, Process, Workflow, Operation, or Loop. It represents an engineering discipline/practice concerned with creating and governing feedback-driven behavior.

## 2. Canonical Definition

Loop Engineering is the disciplined design and continuous improvement of sensing, interpretation, decision, action, outcome observation, and adaptation loops that enable a system, operation, service, process, network, or other bounded context to respond to changing conditions and pursue intended outcomes.

## 3. Semantic Rationale

A loop is characterized by feedback between action and subsequent observation. Loop Engineering concerns the deliberate construction and management of that feedback mechanism.

Context
   ->
Sense / Observe
   ->
Interpret
   ->
Decide
   ->
Act
   ->
Observe Outcome
   ->
Evaluate
   ->
Adapt
   +----------------> Context

The loop may be human-operated, automated, agentic, autonomous, or hybrid.

## 4. Engineering Scope

Loop Engineering may address sensing, observation, contextual interpretation, decision logic, action selection, execution, outcome measurement, feedback, adaptation, control boundaries, intervention, escalation, learning, loop stability, performance, governance, observability, failure handling.

## 5. Semantic Boundary

Loop Engineering SHALL remain distinct from Closed Loop (behavioral pattern, semantic_kind), Autonomous Closed Loop (specialization, semantic_kind), Agentic Loop (agentic behavior may occur within a loop, but Loop Engineering does not require an Agent), Control System (a control system may implement a loop, but Loop Engineering is the discipline used to design and manage the loop).

## 6. Engineering Lifecycle

Define Objective -> Define Context -> Design Observation -> Design Interpretation -> Design Decision -> Design Action -> Design Outcome Measurement -> Design Feedback -> Design Adaptation -> Validate Boundary -> Operate -> Observe -> Improve.

## 7. Loop Properties

objective, context, observation_scope, decision_scope, action_scope, feedback_scope, adaptation_scope, intervention_model, escalation_boundary, measurement_model, governance_context, constraint_context.

## 8. Agentic and Autonomous Dimensions

- Agentic Loop Engineering: uses agentic behavior in loop design or execution
- Autonomous Loop Engineering: engineers independent loop progression
- Agentic + Autonomous Loop Engineering: combines both

These are characteristics of the engineered loop, not automatic properties of Loop Engineering itself.

## 9. Non-Goals

This ADR does not define Closed Loop, establish Autonomous Closed Loop, define AI Closed Loop, require AI, require automation, define a control-engineering standard, or prescribe implementation technology.

## 10. Acceptance Conditions

1. Loop Engineering is recognized as a discipline/practice concept.
2. Its semantic kind is distinct from object/entity specializations.
3. Its relationship to Closed Loop is explicit.
4. Its relationship to Agentic and Autonomous behavior is explicit.
5. Conformance tests prevent incorrect specialization.

## Author

Emmanuel A. Otchere (cardinal author rule, 2026-09-24)
