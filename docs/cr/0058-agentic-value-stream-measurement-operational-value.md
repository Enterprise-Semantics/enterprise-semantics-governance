# CR-VAS-005 ; Agentic Value Stream Measurement & Operational Value Model

Status: Accepted
Date: 2026-10-08
Author: Emmanuel A. Otchere
Implements: ES-ADR-055
Amends: ES-ADR-005 + ES-ADR-052 + ES-ADR-053 + ES-ADR-054 (extends AVS semantic baseline with measurement model)
Supersedes: None
Depends: ES-ADR-005, ES-ADR-031, ES-ADR-049, ES-ADR-051, ES-ADR-052, ES-ADR-053, ES-ADR-054

## 1. Purpose

This Change Request establishes the formal Measurement & Operational Value Model for the Agentic Value Stream concept. It defines how a semantic qualification (CR-VAS-002), participation structure (CR-VAS-003), and conformance validation (CR-VAS-004) are evaluated for operational performance, agentic behavior, value realization, risk, intervention, and effectiveness.

## 2. Problem Statement

The repository can establish whether a Value Stream qualifies as Agentic without yet answering whether the agentic realization is:

- effective;
- efficient;
- valuable;
- appropriately delegated;
- appropriately constrained;
- intervention-heavy;
- stable;
- adaptive;
- producing better outcomes;
- introducing unacceptable risk;
- actually improving Value Stream realization.

A simplistic measurement model would likely produce metrics such as: number of agents, number of decisions, percentage automated, AI usage, number of interactions, model latency. These are implementation metrics, not necessarily measures of Agentic Value Stream value.

CR-VAS-005 therefore establishes a multi-dimensional measurement model centered on:

```
Agentic Behavior + Value Stream Performance + Outcome Realization +
       Authority / Risk + Human Intervention + Economic / Operational Value
```

## 3. Normative Measurement Principle

The primary measurement question SHALL be:

> Does agentic participation improve or materially contribute to the realization of Value Stream outcomes within acceptable authority, risk, cost, and intervention boundaries?

This creates a distinction between:

```
Agentic Activity != Agentic Effectiveness != Business Value
```

A highly active agent can be ineffective. A highly autonomous agent can destroy value. A low-volume agentic intervention can create substantial value. Therefore activity alone SHALL NEVER be treated as success.

## 4. Measurement Architecture

The measurement model SHALL use six primary dimensions:

1. Value Realization (PRIMARY).
2. Agentic Effectiveness.
3. Decision and Action Quality.
4. Human Intervention.
5. Authority, Risk and Boundary Performance.
6. Economic and Operational Efficiency.

These dimensions SHOULD be complemented by contextual implementation metrics where appropriate.

## 5. Measurement Hierarchy

The repository SHALL distinguish:

- Level 1 ; Activity. What happened?
- Level 2 ; Behavior. How did the agent behave?
- Level 3 ; Performance. How well did it perform?
- Level 4 ; Value. What value did it create or protect?
- Level 5 ; Strategic Effect. What changed because of agentic realization?

This prevents dashboards from becoming collections of low-level telemetry.

## 6. Value Realization

The primary dimension SHALL measure whether agentic participation improves the intended Value Stream outcome. Recommended metrics: Outcome Realization Rate, Outcome Quality, Value Leakage, Value Recovery, Exception Resolution Rate, Time-to-Outcome, Outcome Variance, Customer/Stakeholder Outcome.

The preferred measurement construct is:

```
Incremental AVS Value = AVS Result - Comparable Baseline Result
```

The baseline may be: historical, non-agentic, human-only, automated, controlled experiment, counterfactual simulation.

## 7. Agentic Effectiveness

Agentic effectiveness evaluates whether the agentic behavior is functioning as intended. Recommended metrics: Delegation Success Rate, Context Utilization Rate, Action Selection Effectiveness, Adaptive Progression Effectiveness, Agentic Resolution Rate.

Agentic Decision Density = Material Agentic Decisions / Value Stream Transactions. Higher agentic decision density SHALL NOT be interpreted as higher maturity. In some Value Streams, fewer agentic decisions may be preferable.

Action Selection Rate SHOULD be distinguished from Action Execution Rate, because execution may be automated after an agent makes the selection.

Authority Utilization is diagnostic, NOT inherently positive. Low utilization may indicate overly broad authority, insufficient delegation, low complexity, conservative behavior, or effective human intervention. High utilization may indicate appropriate delegation, excessive delegation, weak constraints, or unusually high case complexity.

## 8. Decision and Action Quality

The model SHALL distinguish between Decision Quality, Action Quality, and Outcome Quality. These are NOT equivalent. A good decision can produce a poor outcome because of execution. A poor decision can accidentally produce a good outcome.

Recommended measures: decision acceptance rate, action success rate, action reversal rate, decision override rate, rework rate, exception rate, downstream defect rate, policy-compliance rate.

## 9. Human Intervention

Human intervention SHALL be treated as an explicit dimension rather than automatically as failure. The model SHALL distinguish: required intervention, exception intervention, discretionary intervention, corrective intervention, approval intervention, validation intervention.

Lower intervention is NOT inherently better. An appropriate intervention rate may be desirable in high-risk Value Streams.

Intervention Effectiveness measures whether human intervention adds value: intervention success rate, intervention reversal rate, intervention-induced delay, prevented-loss value, avoided-risk value, unnecessary-intervention rate.

Escalation Precision and Escalation Miss Rate apply to agentic systems with escalation. The latter is particularly important in safety-, compliance-, financial-, or customer-impacting Value Streams.

## 10. Authority, Risk, and Boundary Performance

Recommended measures: Policy Compliance, Constraint Violation Rate, Escalation Failure Rate, Boundary Breach Rate, Risk-Adjusted Outcome, Risk-Adjusted Value.

```
Risk-Adjusted Value = Realized Value - Expected Risk Cost
```

This SHOULD remain conceptual rather than prescribing a universal financial formula. Different Value Streams may use: financial risk, operational risk, customer risk, regulatory risk, security risk, reputational risk.

## 11. Operational Efficiency

Potential metrics: cost per outcome, cost per successful resolution, time per outcome, throughput, capacity utilization, human effort avoided, human effort redirected, infrastructure cost, agent execution cost, exception handling cost.

A particularly important measure is what happened to human effort as a result of agentic realization. Categories: human effort eliminated, human effort reduced, human effort redirected, human effort increased. The objective SHALL NOT be defined as workforce reduction. In many Value Streams, the greater value may come from moving human effort toward complex decisions, relationship management, innovation, exception handling, and strategic work.

AVS Cycle Time SHOULD be compared against Baseline Cycle Time. Decomposition: Decision Time + Agent Execution Time + Human Intervention Time + Waiting Time + Exception Time.

## 12. Agentic Adaptation and Coordination

Where adaptive progression is present: maturity rate, maturity effectiveness, maturity reversal rate, maturity stability. Adaptation is measurable but is NOT itself proof of agenticity.

For multi-agent or distributed AVS implementations, additional measures MAY include: coordination success rate, coordination latency, coordination conflict rate, duplicate-action rate, inter-agent escalation rate, coordination failure rate, shared-state inconsistency, coordination-induced rework. These SHALL be conditional metrics. A single-agent AVS SHALL NOT be required to implement multi-agent metrics.

## 13. Measurement Context

Every measurement SHOULD identify its Value Stream context:

```
measurement:
  id:
  value_stream:
  agentic_participation:
  metric:
  definition:
  unit:
  population:
  period:
  baseline:
  observed_value:
  target:
  threshold:
  provenance:
```

This avoids orphan metrics that cannot be interpreted semantically.

## 14. Baseline Model

The measurement framework SHALL require a baseline wherever an improvement claim is made. Baseline types: historical, human_only, automated, pre_agentic, controlled, counterfactual, benchmark. The baseline SHALL be declared explicitly.

An assertion such as "Agentic implementation improved efficiency by 40%" SHALL NOT be considered complete without identifying the comparison baseline.

## 15. Measurement Dimensions vs Universal Metrics

The repository SHALL distinguish:

- Universal measurement dimensions (applicable conceptually to all AVS): value realization, agentic effectiveness, authority/risk, intervention, efficiency.
- Conditional metrics (applicable only where relevant): multi-agent coordination, adaptive progression, autonomy, AI-specific metrics, model performance.

This avoids creating a bloated mandatory measurement framework.

## 16. Recommended Core Metric Set

For a minimum AVS operational dashboard, the repository SHOULD recommend: Outcome Realization Rate, Incremental Value vs Baseline, Time-to-Outcome, Agentic Decision/Selection Rate, Action Success Rate, Authority Compliance Rate, Boundary Exception Rate, Human Intervention Rate, Intervention Effectiveness, Cost per Outcome, Rework / Reversal Rate, Value Stream Throughput. These are recommended core measures, not semantic qualification requirements.

## 17. Measurement Anti-Patterns

The repository SHALL explicitly identify the following anti-patterns. Each represents a way that measurement can become a backdoor definition of agenticity.

- Agent Count As Value. More agents = more value. False.
- Autonomy As Performance. More autonomy = better performance. False.
- Automation Rate As Agenticity. More automated = more agentic. False.
- Decision Volume As Effectiveness. More agent decisions = better AVS. False.
- Intervention Minimization. Less human intervention = better AVS. False.
- AI Model Quality As Value. Model quality = Value Stream value. False.
- Cost Reduction As Sole Value. Cost reduction is the only value. False.

Agentic Value Streams may create value through quality, speed, resilience, customer experience, risk reduction, innovation, capacity, revenue, and decision quality.

## 18. Value Attribution

The repository SHALL recognize that attributing Value Stream improvement solely to agentic participation can be difficult. Other factors may change simultaneously: process redesign, technology modernization, workforce changes, market conditions, policy changes, product changes, organizational restructuring. Therefore the measurement model SHOULD support an attribution confidence field: high, medium, low, unknown.

## 19. Measurement Provenance

Every reported metric SHOULD be traceable:

```
Value Stream -> Agentic Participation -> Observed Events -> Measurement -> Outcome
```

This allows measurements to remain semantically anchored.

## 20. Measurement Lifecycle

Measurements SHALL support: defined, instrumented, collected, validated, analyzed, acted_upon, reviewed. This distinguishes a metric definition from an operationally trusted measurement.

## 21. Measurement Quality

The repository SHOULD recognize at least: accuracy, completeness, timeliness, consistency, traceability, comparability. A metric without reliable measurement provenance SHALL NOT be treated as equivalent to a validated metric.

## 22. Measurement Maturity Separate

CR-VAS-005 SHALL NOT introduce maturity levels such as L1 = basic measurement, L2 = managed measurement, L3 = optimized measurement. Those belong to CR-VAS-006 or a later maturity specification. The purpose of this CR is to define what SHOULD be measurable, not how mature an organization is at measurement.

## 23. Machine-Readable Measurement Model

The repository SHOULD introduce a controlled measurement structure:

```
measurement_model:
  dimensions:
    value_realization:
      metrics: [outcome_realization_rate, incremental_value, time_to_outcome]
    agentic_effectiveness:
      metrics: [action_selection_rate, action_success_rate, agentic_resolution_rate]
    decision_quality:
      metrics: [decision_acceptance_rate, override_rate, reversal_rate]
    human_intervention:
      metrics: [intervention_rate, intervention_effectiveness, escalation_precision]
    authority_and_risk:
      metrics: [authority_compliance_rate, boundary_exception_rate, constraint_violation_rate]
    operational_efficiency:
      metrics: [cost_per_outcome, throughput, cycle_time, rework_rate]
```

This is a semantic template, not a requirement that every AVS implement every metric.

## 24. Measurement-to-Semantics Traceability

Every core metric SHOULD be traceable back to the semantic model:

- Delegated Intent -> Outcome Realization Rate.
- Bounded Authority -> Authority Compliance Rate.
- Contextual Interpretation -> Context Utilization / Adaptation Effectiveness.
- Action Selection -> Action Selection Effectiveness.
- Material Value Contribution -> Incremental Value / Outcome Improvement.
- Human Intervention -> Intervention Effectiveness.

This is important because it prevents the measurement framework from becoming disconnected from the semantics.

## 25. Relationship to Conformance

CR-VAS-004 establishes whether the semantic conditions are satisfied. CR-VAS-005 may use conformance evidence as a measurement input but SHALL NOT replace it.

```
Conformance -> "Is this actually AVS?"
Measurement -> "How well is the AVS performing?"
```

A poorly performing AVS can remain semantically conformant. A high-performing automated system can remain non-conformant.

## 26. Required Documentation

CR-VAS-005 SHALL add:

```
docs/
+-- measurement.md
+-- value-realization.md
+-- operational-metrics.md
+-- measurement-baselines.md
+-- measurement-provenance.md
+-- measurement-anti-patterns.md
```

The README SHOULD include a concise explanation that measurement is downstream of semantic qualification and conformance.

## 27. Required Examples

The repository SHOULD provide at least:

- Customer Service AVS. Measure: resolution rate, time-to-resolution, escalation, intervention, customer outcome.
- Procurement AVS. Measure: sourcing cycle time, negotiated value, policy compliance, exception rate, human intervention.
- Operations AVS. Measure: throughput, incident resolution, boundary violations, intervention, cost per outcome.
- Multi-Agent AVS. Measure: coordination success, coordination latency, conflict, outcome realization.

## 28. Acceptance Criteria

The implementation SHALL satisfy:

1. concept.yaml carries the new `measurement:` block covering: principle, normative question, 5-level hierarchy, 6 primary dimensions, 4 conditional metric categories, baseline model (7 types), counterfactual comparison principle, measurement context schema (12 fields), value attribution confidence (4 levels), measurement provenance chain, measurement lifecycle (7 stages), 6 measurement quality dimensions, 7 anti-patterns, 3 separation principles, measurement-to-semantics traceability map, core metric set (12 recommended measures), interpretation rules (6), machine-readable measurement model template, 4 reference examples, boundary assertion `per_cr_vas_005_measurement_value`.
2. The conformance kit is expanded to 91 tests (61 prior + 30 new).
3. 10 measurement positive tests are authored as `kit/me-positive-01..10.yaml` with test_ids `VAS-ME-P01..P10`.
4. 10 measurement negative tests are authored as `kit/me-negative-01..10.yaml` with test_ids `VAS-ME-N01..N10`.
5. 10 measurement boundary tests are authored as `kit/me-boundary-01..10.yaml` with test_ids `VAS-ME-BT-01..10`.
6. 6 new documentation files are added: `docs/measurement.md`, `docs/value-realization.md`, `docs/operational-metrics.md`, `docs/measurement-baselines.md`, `docs/measurement-provenance.md`, `docs/measurement-anti-patterns.md`.
7. `docs/concept.md` carries the new "Measurement and Operational Value (CR-VAS-005)" section.
8. `docs/conformance.md` is regenerated with the 91-test inventory and reflects the new boundary assertion `per_cr_vas_005_measurement_value`.
9. `kit/kit.yaml` coverage is updated from 61 to 91; new test_inventory blocks `me_positive`, `me_negative`, `me_boundary` are added; boundary assertion `per_cr_vas_005_measurement_value` is added.
10. 3 new visuals are added under `visuals/agentic-value-stream/`: `measurement-hierarchy.puml`, `measurement-dimensions.puml`, `measurement-anti-patterns.puml`.
11. `mappings/wsf.yaml` and `mappings/opendea.yaml` carry the new `measurement_alignment` block.
12. The repository carries the Cardinal author rule attribution for Emmanuel A. Otchere on all new files.
13. 0 references to TMForum (TMF, eTOM, Frameworx, SID, GB921, TAM, ODF, OSS/BSS) per user directive 2026-09-22.
14. 0 references to specific vendors in semantic content per the vendor embargo.
15. 0 en-dash (U+2013), 0 em-dash (U+2014), 0 triple-em-dash (U+2E3B) in any GitHub-shipped artefact per D-004 rule.
16. The repository does NOT introduce maturity levels (L1, L2, L3) per CR-VAS-005 §22.

## 29. Definition of Done

- All 91 conformance tests parse cleanly as YAML.
- `docs/conformance.md` lists 91 tests under their respective categories.
- `kit/kit.yaml` reports coverage=91.
- The new visuals render in PlantUML.
- The new documentation files reference the correct CR sections.
- The README is updated to reflect the 91-test inventory and the new visuals.
- The governance frame is filed in `Enterprise-Semantics/enterprise-semantics-governance` as ES-ADR-055 (slot 0055) + CR-VAS-005 (slot 0058).
- The PLAN entry is appended to `docs/plan/PLAN-CHANGELOG.md`.
- The state report is refreshed.

## 30. Promotion Metadata

- Status: Accepted.
- Date: 2026-10-08.
- Author: Emmanuel A. Otchere.
- Decision: ES-ADR-055.
- Cardinal author rule: card-carry on (author 2026-09-23).
- Vendor-specific material from embargoed sources: 0 references.
- D-004 dash rule: 0 en-dash (U+2013), 0 em-dash (U+2014), 0 triple-em-dash (U+2E3B).
- WSF metamodel not modified.
- OpenDEA metamodel not modified.

## 31. Related Artefacts

- CR-VAS-005 (Measurement & Operational Value Model).
- ES-ADR-055 (Measurement & Operational Value Framework).
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
