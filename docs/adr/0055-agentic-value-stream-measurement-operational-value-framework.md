# ADR-ES-055 ; Agentic Value Stream Measurement & Operational Value Framework

Status: Accepted
Date: 2026-10-08
Deciders: eaojnr
Decision Type: Semantic baseline extension (measurement layer for Agentic Value Stream)
Scope: Enterprise-Semantics/agentic-value-stream (single concept baseline; measurement model reusable for future AVS extensions)
Implements: CR-VAS-005
Amends: ES-ADR-005 + ES-ADR-052 + ES-ADR-053 + ES-ADR-054 (extends AVS semantic baseline with formal measurement model)
Supersedes: None
Depends: ES-ADR-005, ES-ADR-031, ES-ADR-049, ES-ADR-051, ES-ADR-052, ES-ADR-053, ES-ADR-054

## 1. Context

ES-ADR-052 + CR-VAS-002 (2026-10-07) introduced the formal qualification test that establishes necessary and sufficient conditions for AVS qualification. ES-ADR-053 + CR-VAS-003 (2026-10-08) introduced the Agentic Participation & Value Stream Realization Model. ES-ADR-054 + CR-VAS-004 (2026-10-08) introduced the evidence and conformance validation model.

A semantic definition, a participation structure, and an evidence + conformance layer together do NOT answer whether the agentic realization is producing meaningful Value Stream improvement, at acceptable risk and cost, within its delegated authority and intended operating model.

Without a formal measurement model, two AVS implementations with identical semantic qualification and identical conformance status may be operationally very different. One may produce substantial value; the other may produce risk, waste, or harm.

CR-VAS-005 (2026-10-08) was authored by eaojnr as the design response. It establishes the measurement model that evaluates an already-qualified and conformant AVS implementation. The single most important design decision is: do not allow measurement to become a backdoor definition of agenticity.

This ADR accepts CR-VAS-005 as the formal Measurement & Operational Value Framework for Agentic Value Stream.

## 2. Decision

### 2.1 Normative Principle

The repository SHALL distinguish:

```
Activity != Effectiveness != Business Value
```

Measurement evaluates an already-qualified and conformant AVS implementation. Measurement does NOT determine whether the underlying concept is semantically an AVS.

### 2.2 Normative Measurement Question

The primary measurement question SHALL be:

> Does agentic participation improve or materially contribute to the realization of Value Stream outcomes within acceptable authority, risk, cost, and intervention boundaries?

### 2.3 Five-Level Measurement Hierarchy

The framework SHALL distinguish:

- Level 1 ; Activity. What happened?
- Level 2 ; Behavior. How did the agent behave?
- Level 3 ; Performance. How well did it perform?
- Level 4 ; Value. What value did it create or protect?
- Level 5 ; Strategic Effect. What changed because of agentic realization?

This prevents dashboards from becoming collections of low-level telemetry.

### 2.4 Six Primary Measurement Dimensions

The framework SHALL distinguish:

1. Value Realization (PRIMARY).
2. Agentic Effectiveness.
3. Decision and Action Quality.
4. Human Intervention.
5. Authority and Risk.
6. Operational Efficiency.

### 2.5 Conditional Metrics

The framework SHALL distinguish universal measurement dimensions from conditional metrics. Conditional categories: multi-agent coordination, adaptive progression, AI-specific, autonomy-specific. A single-agent AVS SHALL NOT be required to implement multi-agent metrics.

### 2.6 Baseline Model

A baseline SHALL be required wherever an improvement claim is made. The baseline SHALL be declared explicitly. Baseline types: historical, human_only, automated, pre_agentic, controlled, counterfactual, benchmark.

### 2.7 Counterfactual Comparison

The framework SHALL support:

```
Incremental AVS Value = AVS Result - Comparable Baseline Result
```

This is substantially more meaningful than measuring agentic activity alone.

### 2.8 Measurement Context

Every measurement SHALL identify its Value Stream context: id, value_stream, agentic_participation, metric, definition, unit, population, period, baseline, observed_value, target, threshold, provenance.

### 2.9 Value Attribution

The framework SHALL represent attribution confidence: high, medium, low, unknown.

### 2.10 Measurement Provenance

Every reported metric SHOULD be traceable:

```
Value Stream -> Agentic Participation -> Observed Events -> Measurement -> Outcome
```

This allows measurements to remain semantically anchored.

### 2.11 Measurement Lifecycle

The framework SHALL support a lifecycle: defined, instrumented, collected, validated, analyzed, acted_upon, reviewed.

### 2.12 Measurement Quality

A metric without reliable measurement provenance SHALL NOT be treated as equivalent to a validated metric. Quality dimensions: accuracy, completeness, timeliness, consistency, traceability, comparability.

### 2.13 Measurement Anti-Patterns

The framework SHALL explicitly identify:

- Agent Count As Value. False.
- Autonomy As Performance. False.
- Automation Rate As Agenticity. False.
- Decision Volume As Effectiveness. False.
- Intervention Minimization. False.
- AI Model Quality As Value. False.
- Cost Reduction As Sole Value. False.

### 2.14 Separation Principles

The framework SHALL separate measurement from:

- Semantic Qualification (CR-VAS-002). Measurement may use qualification evidence as a measurement input but SHALL NOT replace it.
- Conformance (CR-VAS-004). Measurement may use conformance evidence as a measurement input but SHALL NOT replace it. A poorly performing AVS can remain semantically conformant. A high-performing automated system can remain non-conformant.
- Maturity (CR-VAS-006 territory). The framework SHALL NOT introduce maturity levels.

### 2.15 Measurement-to-Semantics Traceability

The framework SHALL map:

- Delegated Intent -> Outcome Realization Rate.
- Bounded Authority -> Authority Compliance Rate.
- Contextual Interpretation -> Context Utilization / Adaptation Effectiveness.
- Action Selection -> Action Selection Effectiveness.
- Material Value Contribution -> Incremental Value / Outcome Improvement.
- Human Intervention -> Intervention Effectiveness.

### 2.16 Core Metric Set (Recommended, Not Required)

The framework SHALL recommend a 12-metric core set: outcome_realization_rate, incremental_value_vs_baseline, time_to_outcome, agentic_decision_selection_rate, action_success_rate, authority_compliance_rate, boundary_exception_rate, human_intervention_rate, intervention_effectiveness, cost_per_outcome, rework_reversal_rate, value_stream_throughput.

### 2.17 Interpretation Rules

The framework SHALL assert:

- Authority utilization is diagnostic, NOT inherently positive.
- Lower intervention is NOT inherently better.
- Higher decision density SHALL NOT be interpreted as higher maturity.
- Adaptation is measurable but is NOT itself proof of agenticity.
- Action Selection Rate is distinct from Action Execution Rate.
- Multi-agent metrics are optional for single-agent AVS.

### 2.18 Human Effort Reallocation

The objective SHALL NOT be defined as workforce reduction. The framework SHALL recognize 4 categories: human_effort_eliminated, human_effort_reduced, human_effort_redirected, human_effort_increased.

### 2.19 Cycle Time Decomposition

The framework SHALL decompose AVS Cycle Time: decision_time, agent_execution_time, human_intervention_time, waiting_time, exception_time.

### 2.20 Machine-Readable Measurement Model

The framework SHALL provide a semantic template (NOT a requirement that every AVS implement every metric):

```
measurement_model:
  dimensions:
    value_realization: [outcome_realization_rate, incremental_value, time_to_outcome]
    agentic_effectiveness: [action_selection_rate, action_success_rate, agentic_resolution_rate]
    decision_quality: [decision_acceptance_rate, override_rate, reversal_rate]
    human_intervention: [intervention_rate, intervention_effectiveness, escalation_precision]
    authority_and_risk: [authority_compliance_rate, boundary_exception_rate, constraint_violation_rate]
    operational_efficiency: [cost_per_outcome, throughput, cycle_time, rework_rate]
```

### 2.21 Reference Examples

The framework SHALL provide at least 4 reference examples: customer service AVS, procurement AVS, operations AVS, multi-agent AVS.

### 2.22 Conformance Kit Expansion

The conformance kit SHALL expand to 91 tests:

- 33 prior (CR-VAS-002 + CR-VAS-003 + CR-VAS-004).
- 10 measurement positive (VAS-ME-P01..P10).
- 10 measurement negative (VAS-ME-N01..N10).
- 10 measurement boundary (VAS-ME-BT-01..10).

The framework SHALL cover 10 measurement positive tests, 10 measurement negative tests covering the 7 anti-patterns and 3 separation principles, and 10 measurement boundary tests distinguishing measurement from qualification, conformance, and maturity.

### 2.23 Boundary Assertion

The repository SHALL add the boundary assertion `per_cr_vas_005_measurement_value`.

## 3. Implementation

### 3.1 concept.yaml measurement block

A new `measurement:` block is appended to the Agentic Value Stream concept record, carrying: principle, normative question, 5-level hierarchy, 6 primary dimensions, 4 conditional metric categories, baseline model (7 types), counterfactual comparison principle, measurement context schema (12 fields), value attribution confidence, measurement provenance chain, measurement lifecycle, 6 measurement quality dimensions, 7 anti-patterns, 3 separation principles, measurement-to-semantics traceability map, core metric set (12 recommended measures), interpretation rules, machine-readable measurement model template, relationship-to-conformance narrative, human effort reallocation categories, cycle time decomposition, and reference examples.

### 3.2 Conformance kit

30 new measurement test files are added under `kit/`:

- `kit/me-positive-01..10.yaml` ; VAS-ME-P01..P10.
- `kit/me-negative-01..10.yaml` ; VAS-ME-N01..N10.
- `kit/me-boundary-01..10.yaml` ; VAS-ME-BT-01..10.

The kit manifest is updated to reflect the expanded coverage (33 -> 91 tests) and the new `me_positive`, `me_negative`, `me_boundary` test_inventory blocks. The boundary assertion `per_cr_vas_005_measurement_value` is added.

### 3.3 Documentation

6 new documentation files are added under `docs/`:

- `measurement.md` ; Normative question, 5-level hierarchy, 6 primary dimensions, conditional metrics, baseline model, counterfactual comparison, measurement context, value attribution, provenance chain, lifecycle, quality dimensions.
- `value-realization.md` ; Primary dimension detail, risk-adjusted value, counterfactual value.
- `operational-metrics.md` ; Economic and operational efficiency metrics, cycle time decomposition, human effort reallocation.
- `measurement-baselines.md` ; Baseline types, improvement claim rule, counterfactual value construct.
- `measurement-provenance.md` ; Provenance chain, lifecycle, quality dimensions, measurement context.
- `measurement-anti-patterns.md` ; 7 anti-patterns with explicit verdict (False).

`docs/concept.md` receives a new "Measurement and Operational Value (CR-VAS-005)" section. `docs/conformance.md` is regenerated with the 91-test inventory.

### 3.4 Visuals

3 new PlantUML diagrams are added under `visuals/agentic-value-stream/`:

- `measurement-hierarchy.puml` ; CR-VAS-005 §5.
- `measurement-dimensions.puml` ; CR-VAS-005 §4 + §35.
- `measurement-anti-patterns.puml` ; CR-VAS-005 §30.

### 3.5 Mappings

The repository's `mappings/wsf.yaml` and `mappings/opendea.yaml` receive a new `measurement_alignment` block, treating measurement as a semantic overlay over WSF and OpenDEA without modifying either metamodel.

## 4. Consequences

### 4.1 Positive

- The repository can now evaluate an already-qualified and conformant AVS implementation across 6 primary dimensions.
- The measurement model is semantically anchored via measurement-to-semantics traceability.
- The framework explicitly separates measurement from qualification, conformance, and maturity.
- The 7 anti-patterns prevent measurement from becoming a backdoor definition of agenticity.
- Conditional metrics distinguish universal from optional measures, preventing bloat.

### 4.2 Negative

- The conformance kit now carries 91 tests (vs 33 Wave 1, vs 61 Wave 2). CI regeneration must handle the expanded inventory.
- Future CR-VAS-006 (Maturity & Capability) will inherit the measurement model.
- Validators must distinguish core (universal) metrics from conditional metrics.

### 4.3 Architectural alignment

This ADR completes the 5-part semantic-to-operational chain:

- CR-VAS-002 = SEMANTIC QUALIFICATION.
- CR-VAS-003 = PARTICIPATION & REALIZATION.
- CR-VAS-004 = EVIDENCE & CONFORMANCE.
- CR-VAS-005 = MEASUREMENT & OPERATIONAL VALUE.
- CR-VAS-006 = MATURITY & CAPABILITY (next).

With CR-VAS-005, the Agentic Value Stream repository now establishes a coherent semantic-to-operational specification that supports qualification, participation, evidence, conformance, and measurement. Maturity remains a separate future CR.

## 5. Promotion Metadata

- Status: Accepted (semantic baseline extension, 2026-10-08).
- Cardinal author rule: Emmanuel A. Otchere (cardinal author rule, 2026-09-23).
- Vendor-specific material from embargoed sources: 0 references.
- D-004 dash rule: 0 en-dash (U+2013), 0 em-dash (U+2014), 0 triple-em-dash (U+2E3B).
- WSF metamodel not modified.
- OpenDEA metamodel not modified.

## 6. Related Artefacts

- CR-VAS-005 (Measurement & Operational Value Model).
- ES-ADR-054 (Evidence, Conformance & Qualification Validation Framework).
- ES-ADR-053 (Agentic Value Stream Participation & Realization Framework).
- ES-ADR-052 (Agentic Value Stream Semantic Qualification Framework).
- ES-ADR-005 (Agentic Value Stream decision).
- ES-ADR-031 (5-category boundary taxonomy).
- ES-ADR-049 (Per-Concept Repo Self-Containment).
- ES-ADR-051 (Editorial Restructure).
- CR-AVS-001 (Repository Conformance Reconciliation).
- CR-VAS-002 (Formal Semantic Qualification).
- CR-VAS-003 (Participation & Realization Model).
- CR-VAS-004 (Evidence, Conformance & Qualification Validation).
- FND-ES-AG-008 (Foundation Recon).
