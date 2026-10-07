# CR-VAS-006 ; Agentic Value Stream Maturity & Capability Model

Status: Accepted
Date: 2026-10-08
Author: Emmanuel A. Otchere
Implements: ES-ADR-056
Amends: ES-ADR-005 + ES-ADR-052 + ES-ADR-053 + ES-ADR-054 + ES-ADR-055 (extends AVS semantic baseline with maturity and capability model)
Supersedes: None
Depends: ES-ADR-005, ES-ADR-031, ES-ADR-049, ES-ADR-051, ES-ADR-052, ES-ADR-053, ES-ADR-054, ES-ADR-055

Target release: Enterprise-Semantics/agentic-value-stream v1.4.0
Scope restrictions: additive only ;;; no amendment to CR-VAS-002..005 acceptance boundaries
Implementation: ES-ADR-056 (this CR is the implementation record)

## 1. Purpose

This Change Request establishes the formal Maturity & Capability Model for the Agentic Value Stream concept. It defines how the semantic qualification (CR-VAS-002), participation structure (CR-VAS-003), conformance validation (CR-VAS-004), and measurement model (CR-VAS-005) are evaluated for organizational capability to design, govern, operate, measure, improve, and scale Agentic Value Streams.

## 2. Problem Statement

The repository can establish whether a Value Stream qualifies as Agentic, can prove the qualification through conformance evidence, can measure operational performance and value, but cannot yet answer how capable the organization is at systematically:

- identifying and modeling Agentic Value Streams;
- governing delegated authority;
- operating AVS reliably;
- measuring and attributing value;
- improving AVS performance based on evidence;
- scaling AVS capability across the enterprise.

A simplistic maturity model would likely produce metrics such as: AI adoption percentage, number of agents deployed, autonomy percentage, model sophistication, automation percentage, or production deployment age. These are implementation characteristics, NOT organizational capability assessments.

CR-VAS-006 therefore establishes a six-level maturity model with six capability dimensions, gated by mandatory level gates, evaluated through multidimensional assessment with a minimum-required-dimension aggregation rule.

The design intent is: maturity measures how systematically the organization can realize, govern, improve, and scale AVS. It does NOT determine whether a Value Stream is semantically an AVS.

## 3. Normative Maturity Principle

The primary maturity question SHALL be:

> How systematically and repeatedly can the organization design, govern, operate, measure, improve, and scale Agentic Value Streams at acceptable risk and sustainable cost?

This creates a distinction between:

```
Semantic Qualification != Conformance != Measurement != Maturity
```

The dependency is intentionally one-directional:

```
Semantic Qualification   (Is it AVS?)
   -> Conformance          (Is the claim valid?)
     -> Measurement        (How well does it perform?)
       -> Maturity          (How systematically can the organization
                              operate, govern, improve and scale it?)
```

## 4. Separation Principles

### 4.1 Maturity vs Semantic Qualification

Maturity does NOT determine whether a Value Stream is Agentic. AI adoption, agent count, autonomy percentage, model sophistication, and operational scale SHALL NOT be used as evidence that a Value Stream is Agentic.

### 4.2 Maturity vs Conformance

Maturity and conformance are independent. A non-conformant implementation cannot become conformant by achieving a higher maturity score. A high-maturity organization may operate non-conformant AVS instances.

### 4.3 Maturity vs Measurement

Maturity is not a measurement score. It is a multidimensional organizational capability assessment over measurement plus governance, design, operations, learning, and scaling.

### 4.4 Maturity vs Technology Maturity Model

AVS maturity is NOT Rules -> ML -> GenAI -> Agents -> Multi-Agent -> Autonomous AI. Technology progression SHALL NOT define agentic maturity.

### 4.5 Maturity Does Not Reward Autonomy

Higher autonomy is not inherently more mature. A mature AVS may deliberately retain human approval, escalation, conservative authority limits, mandatory validation, restricted action spaces, and regulatory controls.

## 5. Maturity Architecture

CR-VAS-006 establishes two related but distinct structures:

- Maturity levels describe the organization's overall progression (L0..L5).
- Capability dimensions describe what the organization is becoming capable of doing (C1..C6).

Each capability dimension is assessed independently. The overall maturity level is derived from a minimum-required-dimension gated aggregation, not a simple arithmetic average.

## 6. Maturity Levels

| Level | Name | Meaning |
|---|---|---|
| L0 | Unaware | No deliberate AVS capability. |
| L1 | Aware | AVS concepts understood and identified. |
| L2 | Defined | AVS practices, boundaries and governance are defined. |
| L3 | Implemented | Conformant AVS implementations operate in production. |
| L4 | Managed | AVS performance, risk, value and improvement are systematically managed. |
| L5 | Scaled & Adaptive | AVS capability is governed and continuously optimized across the enterprise. |

Critical distinction: a pilot or prototype is NOT automatically L3. The organization must demonstrate operational realization, not merely architectural intent.

Important limitation: L5 does NOT mean "everything is autonomous." It means the organization can deliberately and safely determine where agentic participation creates value, establish appropriate authority, operate it at scale, measure its effects, and continuously adapt the capability.

## 7. Capability Dimensions

| ID | Dimension |
|---|---|
| C1 | AVS Design & Semantic Modeling |
| C2 | Authority, Governance & Risk |
| C3 | Operational Realization |
| C4 | Value & Performance Management |
| C5 | Learning & Continuous Improvement |
| C6 | Portfolio Scaling & Enterprise Integration |

C2 is particularly important because delegated authority is central to meaningful agentic participation. C4 directly builds upon CR-VAS-005.

## 8. Multidimensional Assessment Rule

A single arithmetic average SHALL NOT be the default maturity mechanism. The profile SHALL remain visible with per-dimension levels and limiting dimensions called out.

Overall Maturity = minimum of required capability dimensions, subject to level-specific gates.

Example profile:

```yaml
maturity:
  overall:
    level: L3
  dimensions:
    design: L5
    governance: L4
    operations: L3
    value: L2
    improvement: L2
    scaling: L1
  limiting_dimensions:
    - value
    - improvement
    - scaling
```

## 9. Mandatory Gates

| Gate | Requires |
|---|---|
| L2 Gate | defined AVS semantics, defined qualification approach, authority model, evidence model, measurement model, governance ownership |
| L3 Gate | at least one conformant production AVS, operational authority enforcement, operational intervention/escalation, outcome measurement, traceable evidence |
| L4 Gate | repeatable performance management, baseline comparison, value measurement, risk monitoring, conformance drift management, systematic improvement |
| L5 Gate | multiple operational AVS implementations, portfolio governance, reusable capability patterns, enterprise measurement, demonstrated scaling, continuous capability evolution |

## 10. Evidence Requirements by Level

| Level | Evidence |
|---|---|
| L1 | strategy statements, awareness material, identified candidates, terminology, preliminary assessments |
| L2 | AVS models, qualification assessments, authority models, conformance tests, governance definitions, measurement specifications |
| L3 | production instances, conformance records, runtime evidence, operational metrics, intervention records, authority enforcement, outcome evidence |
| L4 | historical performance, baselines, trend analysis, value attribution, risk analysis, improvement records, conformance drift analysis |
| L5 | portfolio-level measurements, reusable patterns, enterprise governance, cross-AVS analysis, scaling evidence, continuous improvement, capability evolution records |

## 11. Maturity Anti-Patterns

The following SHALL explicitly be rejected:

- Maturity = autonomy
- Maturity = AI sophistication
- Maturity = agent count
- Maturity = automation percentage
- Maturity = intervention reduction
- Maturity = cost reduction
- Maturity = production deployment
- Maturity = semantic complexity

## 12. Human Participation in Mature AVS

Human participation SHALL remain a first-class design option at every maturity level. The objective is optimal delegation of value-realization decisions and actions within appropriate authority boundaries. Maximum delegation is NOT the target state.

Interaction patterns include: agent to human approval to action; agent to human exception handling to continue; human decision to agent execution; agent decision to human validation; human and agent shared progression.

A mature implementation chooses the appropriate interaction pattern based on: risk, authority, materiality, regulation, reversibility, consequence, confidence, and customer impact.

## 13. Capability Lifecycle

```
Discover -> Qualify -> Design -> Conform -> Deploy -> Measure ->
   Improve -> Scale -> Reassess
```

The lifecycle is iterative. A change to: authority, decision logic, agentic scope, Value Stream structure, operating context, risk boundary, or material behavior MAY trigger revalidation.

## 14. Maturity Transition Criteria

Progression between levels SHALL require demonstrated capability rather than elapsed time. There SHALL be no automatic progression based on age, deployment count, or technology adoption.

| Transition | Requires |
|---|---|
| L2 -> L3 | actual operational realization |
| L3 -> L4 | demonstrated management of performance, value and risk |
| L4 -> L5 | demonstrated organizational scaling and adaptive capability |

## 15. Maturity Drift

The model SHALL support regression. L4 Managed can become L3 Implemented after major platform migration, measurement gaps, or authority monitoring degradation. Maturity SHALL NOT be treated as an irreversible progression.

## 16. Governance Roles

Six governance roles are defined (organizational assignments, not ontology requirements):

| Role | Owns |
|---|---|
| AVS Capability Owner | organizational AVS capability |
| Value Stream Owner | value stream outcomes |
| Agentic Solution Owner | implementation of agentic participation |
| Risk / Governance Owner | authority, risk and policy controls |
| Semantic Steward | semantic consistency and conformance interpretation |
| Measurement / Value Owner | performance and value measurement |

In smaller organizations these MAY be combined, but they MUST remain conceptually distinguishable.

## 17. Assessment Frequency

Maturity SHALL be reassessed:

- periodically;
- after major architectural changes;
- after material authority changes;
- after significant changes in agentic scope;
- after major incidents;
- after significant regulatory changes;
- when expanding to new Value Streams;
- when material performance deterioration occurs.

Maturity status is therefore time-bound evidence, not a permanent organizational label.

## 18. Maturity Schema

The maturity model is machine-readable:

```yaml
maturity:
  model:
    id: AVS-MATURITY
    version: "1.0"
  declared_levels:
    - {id: L0, name: unaware}
    - {id: L1, name: aware}
    - {id: L2, name: defined}
    - {id: L3, name: implemented}
    - {id: L4, name: managed}
    - {id: L5, name: scaled-adaptive}
  declared_dimensions:
    - design_semantics
    - governance_authority_risk
    - operational_realization
    - value_performance
    - learning_improvement
    - portfolio_scaling
  assessment:
    method: gated_multidimensional
    aggregation: minimum_required_dimension
    evidence_required: true
    conformance_required_for: L3
  constraints:
    maturity_does_not_define_agenticity: true
    autonomy_not_required: true
    ai_not_required: true
    automation_not_required: true
    human_intervention_not_negative: true
```

## 19. Assessment Record Template

```yaml
maturity_assessment:
  id:
  subject:
    organization:
    portfolio:
    value_streams:
  model:
    version:
  assessment_period:
  dimensions:
    design_semantics:           {level, evidence, gaps}
    governance_authority_risk: {level, evidence, gaps}
    operational_realization:    {level, evidence, gaps}
    value_performance:          {level, evidence, gaps}
    learning_improvement:       {level, evidence, gaps}
    portfolio_scaling:          {level, evidence, gaps}
  overall:
    level:
    gating_result:
    limiting_dimensions:
  assessor:
  assessment_date:
  next_review:
```

## 20. Capability Gap Model

The maturity assessment SHALL produce capability gaps, not merely a maturity score. This makes the model actionable.

```yaml
gap:
  capability:
  current_level:
  target_level:
  gap_type: [...]
  priority:
  recommended_action: [...]
```

Common gap types: baseline_missing, attribution_missing, evidence_missing, process_undefined, measurement_undefined, policy_undefined, ownership_undefined, conformance_drift, regression.

## 21. Improvement Planning Chain

```
Current State -> Capability Gap -> Required Evidence ->
   Improvement Initiative -> Implementation -> Measurement -> Reassessment
```

This connects naturally to enterprise architecture and transformation planning.

## 22. Enterprise Architecture Relationship

AVS maturity informs:

- business architecture
- operating model transformation
- enterprise architecture
- AI strategy
- automation strategy
- workforce transformation
- governance
- risk management
- technology investment
- data and knowledge strategy

AVS maturity SHALL remain semantically scoped to Agentic Value Stream capability. It SHALL NOT become a generic enterprise digital maturity model.

## 23. Invariants

CR-VAS-006 introduces 12 normative invariants:

- AVS-MAT-INV-001: maturity does not define AVS semantic qualification.
- AVS-MAT-INV-002: conformance precedes L3 production maturity.
- AVS-MAT-INV-003: AI is not required for maturity.
- AVS-MAT-INV-004: autonomy is not required for maturity.
- AVS-MAT-INV-005: human intervention is not inherently a maturity defect.
- AVS-MAT-INV-006: agent count does not determine maturity.
- AVS-MAT-INV-007: technology sophistication does not determine maturity.
- AVS-MAT-INV-008: maturity shall be evidence-based.
- AVS-MAT-INV-009: maturity shall support regression.
- AVS-MAT-INV-010: overall maturity shall not conceal mandatory capability deficiencies.
- AVS-MAT-INV-011: maturity measures organizational capability, not merely individual AVS performance.
- AVS-MAT-INV-012: operational performance does not automatically establish organizational maturity.

## 24. Conformance Tests

### Positive (10 tests)

- VAS-MA-P01: L1 Aware Capability
- VAS-MA-P02: L2 Defined Capability
- VAS-MA-P03: L3 Implemented Capability
- VAS-MA-P04: L4 Managed Capability
- VAS-MA-P05: L5 Scaled & Adaptive Capability
- VAS-MA-P06: Six Capability Dimensions
- VAS-MA-P07: Multidimensional Assessment Profile
- VAS-MA-P08: Machine-Readable Maturity Schema
- VAS-MA-P09: Human Participation Guarantee
- VAS-MA-P10: Capability Lifecycle + Regression

### Negative (10 tests)

- VAS-MA-N01: Maturity != Autonomy
- VAS-MA-N02: Maturity != AI Sophistication
- VAS-MA-N03: Maturity != Agent Count
- VAS-MA-N04: Maturity != Automation Percentage
- VAS-MA-N05: Maturity != Intervention Reduction
- VAS-MA-N06: Maturity != Cost Reduction
- VAS-MA-N07: Maturity != Production Deployment
- VAS-MA-N08: Maturity != Semantic Complexity
- VAS-MA-N09: Maturity Shall Not Be Used As Semantic Qualification Evidence
- VAS-MA-N10: Overall Maturity Shall Not Conceal Mandatory Capability Deficiencies

### Boundary (10 tests)

- VAS-MA-BT-01: Maturity vs Semantic Qualification
- VAS-MA-BT-02: Maturity vs Conformance
- VAS-MA-BT-03: Maturity vs Measurement
- VAS-MA-BT-04: AI Is Not Required For Maturity
- VAS-MA-BT-05: Autonomy Is Not Required For Maturity
- VAS-MA-BT-06: Automation Is Not Required For Maturity
- VAS-MA-BT-07: Human Intervention Is Not A Maturity Defect
- VAS-MA-BT-08: Maturity vs Maturity Drift (Regression)
- VAS-MA-BT-09: Maturity vs Technology Maturity Model
- VAS-MA-BT-10: Maturity vs Operational Performance

## 25. Acceptance Criteria

CR-VAS-006 is complete when:

- A six-level AVS maturity model is defined.
- Each level has explicit capability criteria.
- Six capability dimensions are defined.
- Maturity is separated from semantic qualification.
- Maturity is separated from conformance.
- Maturity is separated from operational measurement.
- L3 requires conformant production AVS realization.
- L4 requires systematic value/performance/risk management.
- L5 requires enterprise scaling capability.
- Multidimensional assessment is supported.
- Maturity gates are defined.
- Evidence requirements are defined.
- Capability gaps are explicitly represented.
- Regression is supported.
- Human participation is not treated as inherently immature.
- Autonomy is not treated as inherently mature.
- AI sophistication is not used as a maturity proxy.
- Agent count is not used as a maturity proxy.
- Machine-readable maturity semantics exist.
- Machine-readable assessment structure exists.
- Positive and negative maturity tests exist.
- CI validation rules exist.
- Documentation is synchronized with the schema.

## 26. Definition of Done

CR-VAS-006 shall be considered complete when the repository can answer all four questions independently:

1. Is this an Agentic Value Stream? CR-VAS-002
2. Can we prove it? CR-VAS-004
3. How well does it perform and create value? CR-VAS-005
4. How capable are we at systematically realizing and scaling it? CR-VAS-006

The repository must not collapse these four questions into a single score.

<!-- Authored by: Emmanuel A. Otchere (cardinal author rule, 2026-10-08) -->
