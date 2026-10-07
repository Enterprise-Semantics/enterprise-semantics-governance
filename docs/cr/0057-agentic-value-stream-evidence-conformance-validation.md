# CR-VAS-004 ; Agentic Value Stream Evidence, Conformance & Qualification Validation Model

Status: Accepted
Date: 2026-10-08
Author: Emmanuel A. Otchere
Implements: ES-ADR-054
Amends: ES-ADR-005 + ES-ADR-052 + ES-ADR-053 (extends AVS semantic baseline with evidence + conformance validation)
Supersedes: None
Depends: ES-ADR-005, ES-ADR-031, ES-ADR-049, ES-ADR-051, ES-ADR-052, ES-ADR-053

## 1. Purpose

This Change Request establishes the formal Evidence, Conformance & Qualification Validation Model for the Agentic Value Stream concept. It defines how a semantic qualification (CR-VAS-002) and a participation structure (CR-VAS-003) are converted into evidence, how evidence is validated, how qualification is determined, and how conformance status is recorded and maintained.

## 2. Problem Statement

A semantic definition without an evidence model creates a significant governance problem. Two organisations may both claim "This is an Agentic Value Stream" while one has delegated intent, explicit authority, contextual interpretation, alternative actions, contextual action selection, and material outcome contribution, and the other merely has an LLM, an AI chatbot, an autonomous application, workflow automation, an AI recommendation engine, or an agentic product label.

Without formal evidence requirements, these implementations may be treated as semantically equivalent. That would undermine the purpose of the Agentic Value Stream concept.

The repository needs a model that:

- Distinguishes claim, evidence, validation, qualification decision, and conformance status.
- Classifies evidence by semantic level (structural, behavioural, outcome).
- Identifies mandatory vs supporting evidence.
- Provides a deterministic qualification decision model.
- Establishes conformance status semantics and lifecycle transitions.
- Supports detection of semantic drift.
- Separates conformance from maturity.

## 3. Normative Design Principle

The Agentic Value Stream repository SHALL distinguish:

```
Claim -> Evidence -> Validation -> Qualification Decision -> Conformance Status
```

An AVS instance SHALL NOT be considered semantically conformant solely because it is named "agentic", contains an Agent, uses AI, uses an LLM, is autonomous, uses orchestration, adapts, or performs automated actions.

The qualification decision SHALL be evidence-based and machine-testable. The conformance status SHALL be time-bound and reflect drift detection. Conformance SHALL be separated from maturity.

## 4. Three Levels of Evidence

Evidence is classified into three semantic levels.

### 4.1 Structural Evidence

Evidence that the required semantic relationships exist (Value Stream, Agentic Participation, Intent, Authority, Context, Action selection, Outcome contribution). Answers the question: Is the required semantic structure represented?

Structural evidence SHALL include:

- Value Stream identity.
- Agentic Participation representation.
- Entrusted Intent.
- Bounded Authority.
- Contextual Interpretation.
- Permissible Alternatives.
- Action / Progression Selection.
- Material Value Contribution.

A missing mandatory structural element SHALL prevent full qualification.

### 4.2 Behavioural Evidence

Evidence that the represented participation actually behaves according to the semantics (interprets context, alternatives exist, selects among alternatives, authority boundaries enforced, escalation occurs, progression changes). Answers: Does the realisation actually behave agentically?

Behavioural evidence SHALL be demonstrated through:

- Decision logs.
- Execution traces.
- Audit records.
- Test results.
- Simulations.
- Human review records.
- System observations.

### 4.3 Outcome Evidence

Evidence that agentic participation materially contributes to Value Stream realisation (altered progression, consequential decision, materially different action, improved or changed value realisation, successful resolution of contextual variation). Answers: Does the agentic behavior materially matter to the Value Stream?

Outcome evidence MAY be demonstrated through:

- Counterfactual comparison.
- Historical replay.
- Controlled testing.
- Analytical reasoning.
- Consequential decision attribution.

## 5. Qualification Evidence Chain

The minimum evidence chain is:

```
Value Stream -> Agentic Participation -> Entrusted Intent -> Bounded Authority ->
  Contextual Interpretation -> Permissible Alternatives -> Action / Progression Selection ->
  Material Value Contribution
```

A missing mandatory link SHALL prevent full semantic qualification.

## 6. Evidence Sufficiency

Evidence SHALL be classified as sufficient, partial, insufficient, contradictory, or unverifiable.

- Sufficient. Evidence supports the relevant qualification condition.
- Partial. Some evidence exists but does not fully establish the condition.
- Insufficient. The condition is asserted but not demonstrated.
- Contradictory. Available evidence conflicts with the qualification claim.
- Unverifiable. Evidence is referenced but cannot be independently inspected or validated.

## 7. Mandatory vs Supporting Evidence

Mandatory evidence (required for AVS qualification):

- Value Stream identity.
- Agentic Participation.
- Intent.
- Authority.
- Context.
- Alternative selection.
- Material value contribution.

Supporting evidence (useful but not mandatory):

- AI model information.
- Agent architecture.
- Automation architecture.
- Autonomy level.
- Performance metrics.
- Intervention statistics.
- Implementation technology.
- Training data.
- Model evaluation.

Supporting evidence SHALL NOT replace semantic evidence. The boundary between mandatory and supporting evidence prevents implementation details (e.g. AI model, autonomy level, performance metrics, automation architecture, agent architecture, training data, model evaluation, implementation technology) from being used as a substitute for semantic conditions.

## 8. Evidence Independence

The same evidence SHALL NOT automatically satisfy multiple independent semantic conditions. The validation framework SHALL avoid circular evidence.

Example: "The agent has access to customer data" may support contextual access but does NOT establish delegated intent, authority, action selection, or outcome contribution.

## 9. Evidence Provenance

Every material evidence item SHOULD have provenance. The recommended structure is:

```
evidence:
  id:
  type:
  description:
  source:
  source_type: design_document | architecture_model | policy |
    configuration | execution_trace | decision_log | audit_record |
    test_result | simulation | human_review | system_observation |
    measurement
  observed_at:
  provided_by:
  validated_by:
  validation_method:
  confidence: high | medium | low | unknown
```

The provenance SHALL distinguish the origin of the evidence. Provenance matters because a single statement of fact does not establish semantic conformance without verifiable source.

## 10. Evidence Confidence

Evidence MAY carry a confidence classification (high, medium, low, unknown). However, confidence SHALL NOT override a missing mandatory semantic condition. High-confidence evidence of AI usage cannot compensate for absent evidence of delegated intent or bounded authority.

## 11. Qualification Decision Model

The qualification decision SHALL follow:

```
Value Stream? -> Agentic Participation? -> Intent + Authority + Context + Selection? ->
  Material Value Contribution? -> AVS QUALIFIED
```

Any mandatory condition failing SHALL prevent a qualified status.

## 12. Qualification Decision Rules

```
IF
  Value Stream semantics = PASS
AND
  all mandatory AVS conditions = PASS
AND
  materiality = PASS
AND
  no exclusion = triggered
THEN
  CONFORMANT
ELSE IF
  mandatory evidence incomplete
THEN
  UNDER_REVIEW / CONDITIONALLY_CONFORMANT
ELSE
  NON_CONFORMANT
```

A triggered exclusion SHALL override superficial positive evidence.

## 13. Conformance Status

The repository SHALL distinguish conformance status: claimed, under_review, conditionally_conformant, conformant, non_conformant, expired.

- Claimed. The Instance Owner asserts that the instance is an AVS.
- Under Review. Evidence is being assessed.
- Conditionally Conformant. Most conditions are satisfied but defined exceptions or evidence gaps remain.
- Conformant. All mandatory semantic requirements are satisfied.
- Non-Conformant. One or more mandatory requirements fail.
- Expired. Previously conformant evidence is no longer current or valid.

## 14. Semantic Conformance vs Maturity

Conformance SHALL NOT be conflated with maturity. An organisation can have a highly mature implementation that is not semantically Agentic, or a semantically conformant AVS that is operationally immature.

The progression SHALL be:

```
Semantic Qualification -> Conformance -> Operational Capability -> Maturity
```

Maturity SHALL be addressed in a subsequent CR (CR-VAS-006), NOT here.

This separation matters because conflating maturity with semantics would let marketing-driven maturity labels (e.g. "agentic-ready") substitute for semantic conformance evidence.

## 15. Materiality Evidence

The evaluator SHALL answer:

> If the agentic participation were removed and replaced by a non-agentic realisation, would the Value Stream's progression, consequential decisions, or realisation of stakeholder value materially change?

The result SHALL be recorded as:

```
materiality:
  test:
  result: true
  rationale:
  evidence:
```

A simple assertion of true without rationale SHALL be insufficient.

## 16. Counterfactual Validation

Materiality SHOULD preferably be tested through a counterfactual. The baseline is the actual agentic realisation. The counterfactual is an equivalent non-agentic realisation. The comparison evaluates differences in:

- Progression.
- Decisions.
- Action selection.
- Outcome.
- Intervention.
- Value realisation.

The counterfactual need not always be executed in production. It MAY be demonstrated through simulation, historical replay, controlled testing, or analytical reasoning.

## 17. Behavioural Test Model

The conformance kit SHALL include behavioural scenarios. Each scenario SHOULD define:

- id. Unique identifier.
- purpose. Why the scenario matters.
- preconditions. Required setup.
- context. Relevant contextual facts.
- available_actions. Set of permissible actions.
- authority. Bounded authority.
- expected_selection. Expected action selection under the scenario.
- expected_progression. Expected progression impact.
- expected_outcome. Expected outcome contribution.
- evidence. Evidence trail.
- result. Pass, fail, inconclusive, not_applicable.

The scenario differs from a structural test in that it focuses on behaviour at runtime rather than structure in design.

## 18. Positive Conformance Tests

8 positive conformance tests are implemented:

- VAS-CF-P01 Delegated Outcome.
- VAS-CF-P02 Contextual Selection.
- VAS-CF-P03 Bounded Authority.
- VAS-CF-P04 Material Progression.
- VAS-CF-P05 Human-Agent Hybrid.
- VAS-CF-P06 Non-AI Agentic.
- VAS-CF-P07 Localised Agenticity.
- VAS-CF-P08 Multi-Agent Coordination.

## 19. Negative Conformance Tests

10 negative conformance tests are implemented:

- VAS-CF-N01 AI Only.
- VAS-CF-N02 Agent Label Only.
- VAS-CF-N03 Workflow Only.
- VAS-CF-N04 Recommendation Only.
- VAS-CF-N05 Fixed Automation.
- VAS-CF-N06 Autonomous System Without Value Materiality.
- VAS-CF-N07 Human Routine Execution.
- VAS-CF-N08 Missing Authority.
- VAS-CF-N09 Missing Selection.
- VAS-CF-N10 Non-Material Agentic Behavior.

## 20. Boundary Test Matrix

The repository SHALL include explicit boundary tests per CR-VAS-004 §21:

| Scenario | Agentic? | Reason |
|---|---|---|
| LLM generates a response | Not necessarily | No delegated action authority. |
| AI recommends an action | Not necessarily | Recommendation != selection. |
| Agent selects within policy | Yes, if material | Delegated bounded selection. |
| RPA executes fixed workflow | No | Deterministic execution. |
| Autonomous vehicle performs transport | Not automatically | Autonomous != AVS. |
| Human resolves exceptional case | Potentially | Conditions must be satisfied. |
| Agent routes tickets using fixed rules | No | Routing alone insufficient. |
| Agent selects customer remediation | Potentially yes | Depends on authority/materiality. |
| Multi-agent negotiation affects fulfilment | Potentially yes | Requires qualification evidence. |
| AI forecasts demand | No | Prediction != agentic realisation. |

10 conformance boundary tests are implemented (VAS-CF-BT-01..10) covering this matrix.

## 21. Human Validation

Automated validation SHALL NOT be the sole mechanism for semantic qualification. The validation chain SHALL combine:

- Machine validation.
- Evidence inspection.
- Semantic review.

Certain questions require semantic judgement, particularly:

- Whether authority is genuinely delegated.
- Whether action alternatives are meaningful.
- Whether participation is material.
- Whether the claimed outcome is genuinely a Value Stream outcome.

The repository MUST NOT embed validation requirements (e.g. "must be reviewed by a certification body") as semantic requirements for being an AVS. The semantic boundary must remain universal.

## 22. Validation Roles

The repository SHOULD distinguish four roles:

- Instance Owner. Responsible for making the AVS claim and supplying evidence.
- Semantic Validator. Evaluates conformance against the Agentic Value Stream specification.
- Domain Reviewer. Validates domain-specific interpretation where required.
- Governance Authority. May approve formal certification where organisational governance requires it.

These roles SHALL NOT be embedded as semantic requirements for being an AVS.

## 23. Evidence Lifecycle

Evidence SHALL have a lifecycle:

```
Created -> Submitted -> Validated -> Accepted -> Monitored -> Revalidated -> Expired / Superseded
```

A conformance claim is therefore potentially time-bound. An instance that is conformant today may become non-conformant tomorrow if its evidence expires, is superseded, or is invalidated by drift detection.

## 24. Conformance Drift

The repository SHOULD support detection of semantic drift. A previously conformant instance MAY become non-conformant when its semantic structure changes.

Drift triggers include:

- Authority has changed.
- Agent behavior has changed.
- Workflow has changed.
- Value Stream has changed.
- Agentic Participation has been removed.
- Action space has changed.
- Policy has changed.
- Human escalation has been removed.
- Materiality has changed.

Drift is different from maturity deterioration. Drift means the semantic qualification conditions are no longer met. Maturity deterioration means the operational quality has degraded while the semantic qualification is preserved.

When drift is detected:

1. Re-validate conformance using the current state.
2. Update the qualification evidence record.
3. Move the conformance status to one of Under Review, Conditionally Conformant, Non-Conformant, or Expired.
4. Notify the Instance Owner + Semantic Validator.
5. Begin the Revalidated stage of the evidence lifecycle.

## 25. Evidence Freshness

Evidence MAY optionally specify freshness:

```
freshness:
  valid_from:
  valid_until:
  review_interval:
```

Freshness SHOULD be determined according to the volatility of the underlying semantic claim:

- Static Value Stream definition. Relatively stable.
- Agent authority configuration. Potentially volatile.
- Runtime decision behavior. Highly dynamic.

If an evidence item does not explicitly carry freshness, freshness SHALL be inferred from the source_type:

- design_document. Relatively stable.
- policy. Potentially volatile.
- configuration. Potentially volatile.
- execution_trace. Highly dynamic.
- decision_log. Highly dynamic.

## 26. Conformance Levels

The repository SHALL NOT create multiple levels of "agenticity". The concept itself SHALL remain binary at the semantic boundary. A candidate is either semantically an Agentic Value Stream or it is not. Maturity is evaluated separately in a future specification (CR-VAS-006).

## 27. Conformance Kit Architecture

The conformance kit SHALL evolve toward the structure:

```
kit/
+-- kit.yaml
+-- schema/
+-- positive/
+-- negative/
+-- boundary/
+-- structural/
+-- behavioral/
+-- evidence/
+-- expected-results/
```

Exact directory names follow the repository's established convention.

## 28. Conformance Result

Each test result SHOULD be machine-readable:

```
result:
  test_id:
  status: pass | fail | inconclusive | not_applicable
  qualification_condition:
  evidence:
  observations:
  rationale:
```

Inconclusive SHALL be distinguished from fail. Absence of evidence is NOT necessarily evidence of semantic failure; it MAY indicate insufficient evidence. However, an instance cannot become fully conformant while mandatory evidence remains inconclusive.

## 29. Qualification Evidence Record

The repository SHOULD carry a machine-readable qualification record per concept instance, capturing:

- The qualification evidence record.
- Per-condition status.
- Evidence references (id + source_type + confidence).
- Conformance status.
- Validation chain attribution.
- Drift events.

This record is consumed by validation tooling and by humans auditing conformance.

## 30. Qualification Decision Rules (formal)

```
IF
  Value Stream semantics = PASS
AND
  all mandatory AVS conditions = PASS
AND
  materiality = PASS
AND
  no exclusion = triggered
THEN
  CONFORMANT
ELSE IF
  mandatory evidence incomplete
THEN
  UNDER_REVIEW / CONDITIONALLY_CONFORMANT
ELSE
  NON_CONFORMANT
```

A triggered exclusion SHALL override superficial positive evidence.

## 31. Conformance Evidence vs Operational Telemetry

Runtime telemetry can provide evidence but SHALL NOT become the semantic definition. Telemetry is evidence, not semantics.

This distinction matters because telemetry systems are designed to measure runtime behavior, not semantic qualification. Mixing the two would let runtime performance substitute for semantic conformance.

## 32. Conformance and Governance Separation

The semantic specification defines what MUST be true. The governance framework may define who is authorised to certify that it is true. These SHALL remain separate.

This separation prevents organisational governance requirements (e.g. certification authority, external audit, internal governance board) from contaminating the universal semantic definition.

## 33. Strategic Rationale

CR-VAS-004 is the third of five CRs in the Agentic Value Stream semantic-to-operational chain:

- CR-VAS-002 = SEMANTIC QUALIFICATION.
- CR-VAS-003 = PARTICIPATION & REALIZATION.
- CR-VAS-004 = EVIDENCE & CONFORMANCE.
- CR-VAS-005 = MEASUREMENT & OPERATIONAL VALUE.
- CR-VAS-006 = MATURITY & CAPABILITY.

With CR-VAS-004, the semantic control loop is now complete:

```
SEMANTIC DEFINITION -> REPRESENTATION -> EVIDENCE & VALIDATION -> CONFORMANCE
```

CR-VAS-005 (Measurement & Operational Value) and CR-VAS-006 (Maturity & Capability) will operate on top of this foundation.

The Agentic Value Stream repository is no longer merely a concept definition. It is a governable semantic specification.

## 34. Acceptance Criteria

The implementation SHALL satisfy:

1. concept.yaml carries the new `evidence_conformance:` block covering: principle, three evidence levels, qualification evidence chain, sufficiency vocabulary, mandatory vs supporting evidence, evidence independence, provenance template, confidence, qualification decision model, decision rules, conformance status vocabulary, semantic conformance vs maturity separation, qualification evidence record, materiality evidence + counterfactual validation, behavioural test model, positive test inventory (8), negative test inventory (10), boundary test inventory (10), validation roles, evidence lifecycle, drift detection, evidence freshness, conformance kit architecture, conformance result template, telemetry vs evidence separation, governance separation, qualification decision rules.
2. The conformance kit is expanded to 61 tests (33 prior + 28 new).
3. 8 conformance positive tests are authored as `kit/cf-positive-01..08.yaml` with test_ids `VAS-CF-P01..P08`.
4. 10 conformance negative tests are authored as `kit/cf-negative-01..10.yaml` with test_ids `VAS-CF-N01..N10`.
5. 10 conformance boundary tests are authored as `kit/cf-boundary-01..10.yaml` with test_ids `VAS-CF-BT-01..10`.
6. 5 new documentation files are added: `docs/evidence.md`, `docs/qualification.md`, `docs/validation.md`, `docs/boundary-testing.md`, `docs/conformance-drift.md`.
7. `docs/concept.md` carries the new "Evidence and Conformance (CR-VAS-004)" section.
8. `docs/conformance.md` is regenerated with the 61-test inventory and reflects the new boundary assertion `per_cr_vas_004_evidence_validation`.
9. `kit/kit.yaml` coverage is updated from 33 to 61; new test_inventory blocks `cf_positive`, `cf_negative`, `cf_boundary` are added; boundary assertion `per_cr_vas_004_evidence_validation` is added.
10. 3 new visuals are added under `visuals/agentic-value-stream/`: `qualification-decision-model.puml`, `evidence-lifecycle.puml`, `conformance-status-machine.puml`.
11. The repository carries the Cardinal author rule attribution for Emmanuel A. Otchere on all new files.
12. 0 references to TMForum (TMF, eTOM, Frameworx, SID, GB921, TAM, ODF, OSS/BSS) per user directive 2026-09-22.
13. 0 references to specific vendors in semantic content per the vendor embargo.
14. 0 en-dash (U+2013), 0 em-dash (U+2014), 0 triple-em-dash (U+2E3B) in any GitHub-shipped artefact per D-004 rule.
15. The repository does NOT introduce the Agentic Value Stage, Agentic Workflow, Agentic Operations, or Autonomous Value Stream concepts per CR-VAS-002.

## 35. Definition of Done

- All 61 conformance tests parse cleanly as YAML.
- `docs/conformance.md` lists 61 tests under their respective categories.
- `kit/kit.yaml` reports coverage=61.
- The new visuals render in PlantUML.
- The new documentation files reference the correct CR sections.
- The README is updated to reflect the 61-test inventory and the new visuals.
- The governance frame is filed in `Enterprise-Semantics/enterprise-semantics-governance` as ES-ADR-054 (slot 0054) + CR-VAS-004 (slot 0057).
- The PLAN entry is appended to `docs/plan/PLAN-CHANGELOG.md`.
- The state report is refreshed.

## 36. Promotion Metadata

- Status: Accepted.
- Date: 2026-10-08.
- Author: Emmanuel A. Otchere.
- Decision: ES-ADR-054.
- Cardinal author rule: card-carry on (author 2026-09-23).
- Vendor-specific material from embargoed sources: 0 references.
- D-004 dash rule: 0 en-dash (U+2013), 0 em-dash (U+2014), 0 triple-em-dash (U+2E3B).
- WSF metamodel not modified.
- OpenDEA metamodel not modified.

## 37. Related Artefacts

- CR-VAS-004 (Evidence, Conformance & Qualification Validation Model).
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
- FND-ES-AG-008 (Foundation Recon).
