# CR-VAS-007 ; Agentic Value Stream Governance, Lifecycle & Portfolio Management Model

Status: Accepted
Date: 2026-10-08
Author: Emmanuel A. Otchere
Implements: ES-ADR-057
Amends: ES-ADR-005 + ES-ADR-052 + ES-ADR-053 + ES-ADR-054 + ES-ADR-055 + ES-ADR-056 (extends AVS semantic baseline with governance, lifecycle, and portfolio management model)
Supersedes: None
Depends: ES-ADR-005, ES-ADR-031, ES-ADR-049, ES-ADR-051, ES-ADR-052, ES-ADR-053, ES-ADR-054, ES-ADR-055, ES-ADR-056

Target release: Enterprise-Semantics/agentic-value-stream v1.5.0
Scope restrictions: additive only ;;; no amendment to CR-VAS-002..006 acceptance boundaries
Implementation: ES-ADR-057 (this CR is the implementation record)

## 1. Purpose

This Change Request establishes the formal Governance, Lifecycle & Portfolio Management Model for the Agentic Value Stream concept. It defines how the semantic qualification (CR-VAS-002), participation structure (CR-VAS-003), conformance validation (CR-VAS-004), measurement model (CR-VAS-005), and maturity framework (CR-VAS-006) are governed as a Value Stream with agentic participation throughout its lifecycle and across an enterprise portfolio.

## 2. Problem Statement

The repository can establish whether a Value Stream qualifies as Agentic, can prove the qualification, can measure operational performance, can assess organizational maturity, but cannot yet answer how the AVS is:

- proposed;
- assessed;
- designed;
- qualified;
- approved;
- deployed;
- operated;
- monitored;
- changed;
- revalidated;
- suspended;
- retired;
- and governed as part of an enterprise portfolio.

CR-VAS-007 establishes the management control plane around the already-defined semantic object. The design intent is: governance describes how the organization controls the AVS existence and evolution, NOT what the AVS is.

## 3. Normative Governance Principle

The primary governance question SHALL be:

> How is the Agentic Value Stream controlled throughout its lifecycle?

The governance object remains anchored to the Value Stream and its delegated agentic participation:

```
Value Stream
   -> Agentic Participation
     -> Authority
       -> Risk
         -> Outcome
           -> Governance
```

rather than:

```
AI Model
   -> Agent
     -> Agentic System
       -> Governance
```

The latter incorrectly makes technology the primary governance object.

## 4. Separation Principles

### 4.1 Governance vs Semantic Qualification

Governance does NOT redefine AVS semantics. Semantic qualification (CR-VAS-002) and governance approval are distinct decisions.

### 4.2 Governance vs Conformance

Governance does NOT redefine conformance. A conformant implementation may still be denied governance approval. A non-conformant implementation may still have governance approval withdrawn.

### 4.3 Governance vs Measurement

Governance metrics complement (do NOT replace) CR-VAS-005 measurement metrics. Governance metrics evaluate the control plane; measurement metrics evaluate AVS performance.

### 4.4 Governance vs Maturity

CR-VAS-006 measures organizational capability (maturity to govern). CR-VAS-007 governs the actual lifecycle (actual exercise of governance). These are distinct.

### 4.5 Portfolio Governance vs Individual AVS Governance

Portfolio governance must NOT redefine individual AVS semantics.

### 4.6 Runtime Instruction vs Governance Policy

An agent instruction cannot legitimately override a higher-order authority constraint (Instruction != Policy != Authority != Governance Decision).

## 5. Governance Objective

Ensure that delegated agentic participation remains semantically valid, appropriately authorized, operationally controlled, outcome-oriented, measurable, and aligned with enterprise intent throughout its lifecycle.

Governance covers six dimensions:

1. Semantic integrity
2. Authority integrity
3. Operational integrity
4. Risk and policy integrity
5. Value integrity
6. Lifecycle integrity

## 6. Governance Object Model

Governance is subordinate to the semantic model. It operates on three semantic boundaries (semantic, authority, outcome) and produces three outputs (lifecycle, controls, portfolio).

```
                    Agentic Value Stream
                            |
             +--------------+--------------+
             |              |              |
          Semantic       Authority       Outcome
          Boundary        Boundary        Boundary
             |              |              |
             +--------------+--------------+
                            |
                       Governance
                            |
       +--------------------+--------------------+
       |                    |                    |
   Lifecycle             Controls            Portfolio
       |                    |                    |
   Change/Release      Risk/Policy        Prioritization
   Validation          Intervention       Dependencies
   Retirement          Monitoring         Investment
```

## 7. Lifecycle Model

An AVS SHALL have an explicit lifecycle with 10 states.

| State | Meaning |
|---|---|
| Proposed | Candidate identified for agentic realization. No conformance claim yet. |
| Assessed | Initial evaluation covering relevance, agentic participation, expected outcomes, potential authority, risk, materiality, feasibility. |
| Designed | Formal design including participation scope, intent, authority, contextual inputs, action space, intervention, escalation, expected outcomes, measurement, governance. |
| Qualified | Semantic qualification and evidence requirements satisfied (CR-VAS-002 + CR-VAS-004). |
| Approved | Governance authority authorizes implementation or operation. Approval SHALL NOT be interpreted as semantic qualification. |
| Implemented | Realization exists technically/operationally but may not yet operate as a production service. |
| Operational | Actively realizing value in intended operational environment. Required controls active. |
| Managed | Operational + systematic measurement, monitoring, risk management, value management, conformance management, improvement. Aligns with CR-VAS-006. |
| Suspended | Temporarily ceased agentic realization. Triggers: material policy violation, authority breach, unacceptable risk, conformance failure, severe operational incident, unexplained outcome degradation, loss of required evidence, regulatory requirement. |
| Retired | No longer authorized for operational use. Historical evidence, measurement history, governance decisions, lessons learned, relevant provenance preserved. |

The lifecycle is NOT necessarily linear. An AVS may move backwards: Operational -> Suspended -> Revalidated -> Operational, or Operational -> Material Change -> Reassessment -> Non-Conformant -> Remediation.

## 8. Governance State vs Lifecycle State

Lifecycle state and governance status SHALL remain distinct. An AVS may be operational while subject to remediation, heightened monitoring, conditional approval, or restricted authority. This prevents state explosion.

## 9. Governance Domains (G1..G7)

| ID | Domain | Controls |
|---|---|---|
| G1 | Semantic Governance | Value Stream identity, agentic participation, qualification, semantic boundary, conformance, ontology alignment |
| G2 | Authority Governance | Authority scope, permissions, thresholds, policies, escalation, revocation, temporal/transaction/risk limits |
| G3 | Operational Governance | Reliability, observability, incident management, intervention, escalation, service ownership, fallback |
| G4 | Risk & Policy Governance | Regulatory requirements, organizational policy, safety, security, privacy, financial limits, reputational risk |
| G5 | Value Governance | Value baseline, outcome realization, benefit realization, cost, risk-adjusted value, customer/stakeholder outcomes |
| G6 | Change Governance | Semantic changes, authority changes, agentic scope changes, policy changes, operating-context changes, major technology changes |
| G7 | Portfolio Governance | Prioritization, duplication, reuse, dependencies, investment, risk concentration, capability reuse, retirement |

## 10. Material Change

A change is material when it could alter: whether the implementation remains semantically Agentic; delegated authority; action space; risk exposure; stakeholder outcome; Value Stream progression; intervention requirements; regulatory obligations; operational boundary.

Examples: change agent model; change authority threshold; change decision policy; expand action space; move from advisory to delegated execution; add a new Value Stream stage; remove human approval; expand geography; change customer population; change regulatory context. These SHOULD trigger revalidation.

## 11. Change Classification

| Class | Meaning | Action |
|---|---|---|
| Class A | Non-Material | No full requalification required. |
| Class B | Controlled | Targeted review required. |
| Class C | Material | Formal revalidation required. |
| Class D | Critical | Governance approval required before implementation. |

## 12. Change Decision Model

```
Change Proposed
   -> Materiality Assessment
     -> No: Controlled Change
     -> Yes: Revalidation
       -> Approval
         -> Implementation
           -> Evidence
             -> Monitoring
```

## 13. Authority Governance

Authority is governed throughout the lifecycle as a governed enterprise resource. Records include scope, actor, permissions, constraints, policies, thresholds, temporal boundary, transaction boundary, escalation conditions, revocation conditions, approval, effective_from, effective_until.

Escalation is explicit and observable. Revocation is supported and MUST NOT require semantic deletion.

## 14. Fallback Governance

Every production AVS SHOULD define an appropriate fallback strategy. Patterns: Agentic -> Human; Agentic -> Deterministic Automation; Agentic -> Manual Process; Agentic -> Safe Stop. Fallback is determined by Value Stream criticality and risk.

## 15. Intervention Governance

Human intervention SHALL be governed as an explicit control mechanism. Intervention types: approval; validation; exception handling; correction; escalation; override; investigation; recovery. Intervention SHALL NOT automatically be classified as failure.

## 16. Conformance Drift

An AVS may gradually cease to conform. Causes: context changes; authority expansion; policy changes; new action options; Value Stream changes; agent behavior changes; customer population changes; regulatory changes. Conformance is a lifecycle property, NOT a one-time certification event. Periodic and event-triggered revalidation SHALL be supported.

## 17. Governance Triggers

Revalidation SHOULD be triggered by: Semantic Change; Authority Change; Risk Change; Policy Change; Material Outcome Change; Agentic Scope Change; Value Stream Change; Regulatory Change; Major Incident; Conformance Drift; Architecture Change.

## 18. Governance Evidence

Each governance decision has traceable evidence. Records include id, subject, decision, rationale, authority, evidence, risks, conditions, effective dates, decided_by, reviewed_by, review_date.

## 19. Governance Decision Types

Controlled vocabulary (15 verbs): qualify; approve; approve_with_conditions; reject; deploy; continue; restrict; escalate; suspend; resume; revalidate; expand; reduce_scope; revoke_authority; retire.

## 20. Portfolio Governance

### Inventory

AVS inventory, business domains, Value Streams, agentic scope, authority concentration, criticality, risk, value, maturity, technology dependencies, shared capabilities, duplication, lifecycle state.

### Prioritization

Expected Value + Strategic Alignment + Feasibility + Risk + Capability Readiness + Reuse Potential + Operational Criticality. A simple "highest automation opportunity first" strategy is explicitly rejected.

### Capability Reuse

Reusable capabilities: identity; authorization; policy enforcement; knowledge retrieval; decision services; monitoring; evaluation; intervention; audit; measurement; orchestration.

### Avoiding Agent Sprawl

Monitor for: duplicate agents; duplicate capabilities; inconsistent authority models; fragmented policies; overlapping Value Streams; redundant AI services; unnecessary multi-agent architectures.

The goal is NOT to minimize the number of agents; the goal is to minimize unnecessary complexity while maximizing reusable value-realization capability.

### Portfolio Risk Concentration

An enterprise SHOULD identify concentration risks such as many AVS sharing the same authority service, policy engine, agent platform -> single failure or control point.

## 21. Lifecycle Ownership

| Responsibility | Owner |
|---|---|
| Value outcome | Value Stream Owner |
| Semantic integrity | Semantic Steward |
| Agentic realization | AVS/Solution Owner |
| Authority | Authority Owner |
| Risk | Risk/Governance Owner |
| Operations | Operational Owner |
| Measurement | Value/Measurement Owner |
| Lifecycle | AVS Lifecycle Owner |

## 22. Governance RACI Principle

The repository SHOULD avoid embedding a universal RACI matrix into the semantic concept. RACI belongs to organizational governance configuration.

## 23. Governance Policy Hierarchy

```
Enterprise Policy
   -> Domain Policy
     -> Value Stream Policy
       -> AVS Policy
         -> Authority Boundary
           -> Runtime Enforcement
```

This prevents runtime agent instructions from becoming the highest authority.

## 24. Runtime Instruction vs Governance Policy

```
Instruction != Policy != Authority != Governance Decision
```

An agent instruction cannot legitimately override a higher-order authority constraint.

## 25. Emergency Controls

Critical AVS implementations SHOULD provide: emergency suspension; authority revocation; safe fallback; escalation; incident capture; evidence preservation; controlled restart. These controls SHOULD operate independently enough to remain effective when the AVS itself is malfunctioning.

## 26. Governance Dashboard

A portfolio governance dashboard should expose: Lifecycle (Proposed, Assessed, Designed, Qualified, Approved, Operational, Suspended, Retired); Semantic (conformance status, drift, qualification age); Authority (utilization, exceptions, revocations, escalation); Risk (incidents, boundary violations, policy exceptions); Value (outcome realization, incremental value, cost, risk-adjusted value); Maturity (capability profile, gaps, improvement trajectory).

## 27. Governance Metrics

| Metric | Formula / Description |
|---|---|
| Governance Review Timeliness | reviews_completed_within_required_period / reviews_due |
| Revalidation Compliance | material_changes_revalidated / material_changes |
| Authority Control Coverage | agentic_authority_boundaries_with_active_controls / total_delegated_authority_boundaries |
| Governance Exception Rate | governance_exceptions / governed_avs_events |
| Suspension Response Time | Time from critical governance trigger to effective suspension |
| Remediation Closure Rate | closed_governance_findings / open_governance_findings |

## 28. Lifecycle Schema

Machine-readable lifecycle record:

```yaml
lifecycle:
  state: operational
  state_since:
  owner:
  previous_state:
  transition_reason:
  governance:
    status:
    approval:
    conditions:
  qualification:
    status:
    last_validated:
    next_review:
  conformance:
    status:
    last_assessed:
  material_change:
    pending: false
  suspension:
    active: false
```

## 29. Change Record Schema

```yaml
change:
  id:
  avs:
  classification:
  description:
  affected_scope:
  affected_authority:
  affected_risk:
  affected_outcomes:
  materiality:
    determination:
    rationale:
  revalidation:
    required:
    status:
  approval:
    required:
    status:
  implementation:
    status:
  post_change_validation:
    status:
    evidence:
```

## 30. Portfolio Record

```yaml
portfolio:
  id:
  name:
  members:
    - avs_id:
  governance:
    owner:
    review_cycle:
  dependencies:
    - type:
      subject:
  shared_capabilities:
    - capability:
  risk_profile:
    criticality:
    concentration:
  value:
    aggregate:
    confidence:
```

## 31. Invariants

CR-VAS-007 establishes 15 invariants:

- AVS-GOV-INV-001: governance does not redefine AVS semantics.
- AVS-GOV-INV-002: semantic qualification and governance approval are distinct decisions.
- AVS-GOV-INV-003: operational status does not imply continuing conformance.
- AVS-GOV-INV-004: material changes require appropriate revalidation.
- AVS-GOV-INV-005: delegated authority must remain bounded and governable.
- AVS-GOV-INV-006: authority must be revocable.
- AVS-GOV-INV-007: production AVS should have an appropriate fallback strategy.
- AVS-GOV-INV-008: human intervention may be a deliberate governance control.
- AVS-GOV-INV-009: lifecycle states must support suspension and resumption.
- AVS-GOV-INV-010: lifecycle states must support retirement.
- AVS-GOV-INV-011: governance decisions require traceable evidence.
- AVS-GOV-INV-012: portfolio governance must not redefine individual AVS semantics.
- AVS-GOV-INV-013: runtime instructions cannot supersede governing authority or policy.
- AVS-GOV-INV-014: conformance is subject to lifecycle revalidation.
- AVS-GOV-INV-015: governance responsibilities are organizational assignments, not ontology requirements.

## 32. Conformance Tests

### Positive (10 tests)

- VAS-GV-P01: Lifecycle Management
- VAS-GV-P02: Seven Governance Domains
- VAS-GV-P03: Material Change Revalidation
- VAS-GV-P04: Authority Revocation
- VAS-GV-P05: Safe Suspension and Fallback
- VAS-GV-P06: Portfolio Governance
- VAS-GV-P07: Capability Reuse And Avoidance Of Agent Sprawl
- VAS-GV-P08: Governance Evidence And Decision Types
- VAS-GV-P09: Runtime Instruction Shall Not Override Authority
- VAS-GV-P10: Governance Metrics And Dashboard

### Negative (10 tests)

- VAS-GV-N01: Approval Equals Qualification
- VAS-GV-N02: No Revalidation
- VAS-GV-N03: Irrevocable Authority
- VAS-GV-N04: Agent Controls Policy
- VAS-GV-N05: No Fallback
- VAS-GV-N06: Portfolio By Agent Count
- VAS-GV-N07: Governance Redefines Semantics
- VAS-GV-N08: Operational Status Implies Continuing Conformance
- VAS-GV-N09: Lifecycle Without Retirement Support
- VAS-GV-N10: Governance Decisions Without Evidence

### Boundary (10 tests)

- VAS-GV-BT-01: Governance vs Semantic Qualification
- VAS-GV-BT-02: Qualification vs Approval
- VAS-GV-BT-03: Lifecycle State vs Governance Status
- VAS-GV-BT-04: Material vs Non-Material Change
- VAS-GV-BT-05: Authority Escalation vs Normal Authority Use
- VAS-GV-BT-06: Conformance Drift vs Version Change
- VAS-GV-BT-07: Governance Maturity vs AVS Maturity
- VAS-GV-BT-08: Governance Metrics vs Measurement Metrics
- VAS-GV-BT-09: Intervention As Control vs Intervention As Failure
- VAS-GV-BT-10: Governance RACI vs Ontology Responsibility

## 33. Acceptance Criteria

CR-VAS-007 is complete when:

- AVS lifecycle states are defined.
- Lifecycle transitions are defined.
- Governance domains are defined.
- Governance status is separated from lifecycle status.
- Material change is formally defined.
- Change classification exists.
- Revalidation triggers are defined.
- Authority governance is established.
- Authority revocation is supported.
- Suspension and resumption are supported.
- Appropriate fallback is addressed.
- Intervention governance is defined.
- Conformance drift is addressed.
- Governance evidence is represented.
- Governance decision types are defined.
- Portfolio governance is established.
- Capability reuse is addressed.
- Agent sprawl and duplication are addressed.
- Governance concentration risk is addressed.
- Governance responsibilities are defined without embedding organizational RACI into the ontology.
- Governance metrics are defined.
- Lifecycle and governance schemas are machine-readable.
- Positive and negative governance tests exist.
- CI validation rules exist.
- Governance documentation is synchronized with schemas.

## 34. Definition of Done

CR-VAS-007 shall be considered complete when an organization can trace an AVS through: Proposal -> Assessment -> Design -> Qualification -> Approval -> Implementation -> Operation -> Measurement -> Governance -> Change / Revalidation -> Suspension / Recovery -> Retirement, with explicit evidence, authority, ownership, and decision records at each material governance point.

## 35. Architectural Position

CR-VAS-007 introduces an important architectural distinction: the AVS semantic model describes what the thing is. Governance describes how the organization controls its existence and evolution. This prevents the repository from drifting into a generic "agent governance framework." The governance object remains anchored to the Value Stream and its delegated agentic participation.

## 36. CR Sequence After CR-VAS-007

The AVS architecture now progresses coherently:

| CR | Layer | Question |
|---|---|---|
| VAS-002 | Semantic Qualification | What makes an AVS an AVS? |
| VAS-003 | Participation & Realization | How is agentic participation realized? |
| VAS-004 | Evidence & Conformance | How do we prove it? |
| VAS-005 | Measurement & Value | How well does it work? |
| VAS-006 | Maturity & Capability | How capable are we? |
| VAS-007 | Governance & Lifecycle | How is it controlled throughout its life? |

The next logical area after CR-VAS-007 is CR-VAS-008: Architecture Patterns, Reference Architectures & Implementation Boundaries, where the semantic and governance model can be translated into reusable architectural patterns without allowing implementation technology to leak back into the core AVS semantics.

<!-- Authored by: Emmanuel A. Otchere (cardinal author rule, 2026-10-08) -->
