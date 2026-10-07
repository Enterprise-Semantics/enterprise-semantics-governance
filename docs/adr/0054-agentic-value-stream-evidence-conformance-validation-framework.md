# ADR-ES-054 ; Agentic Value Stream Evidence, Conformance & Qualification Validation Framework

Status: Accepted
Date: 2026-10-08
Deciders: eaojnr
Decision Type: Semantic baseline (evidence + conformance validation layer for Agentic Value Stream)
Scope: Enterprise-Semantics/agentic-value-stream (single concept baseline; evidence model reusable for future AVS extensions)
Implements: CR-VAS-004
Amends: ES-ADR-005 + ES-ADR-052 + ES-ADR-053 (extends Agentic Value Stream semantic baseline with formal evidence and conformance validation)
Supersedes: None
Depends: ES-ADR-005, ES-ADR-031, ES-ADR-049, ES-ADR-051, ES-ADR-052, ES-ADR-053

## 1. Context

ES-ADR-052 + CR-VAS-002 (2026-10-07) introduced the formal qualification test that establishes necessary and sufficient conditions for AVS qualification. ES-ADR-053 + CR-VAS-003 (2026-10-08) introduced the Agentic Participation & Value Stream Realization Model that bridges the Value Stream and the actor performing agentic realisation.

A semantic definition without an evidence model creates a significant governance problem. Two organisations may both claim "This is an Agentic Value Stream" while one has delegated intent, explicit authority, contextual interpretation, alternative actions, contextual action selection, and material outcome contribution, and the other merely has an LLM, an AI chatbot, an autonomous application, workflow automation, an AI recommendation engine, or an agentic product label.

Without formal evidence requirements, these implementations may be treated as semantically equivalent. That would undermine the purpose of the Agentic Value Stream concept.

CR-VAS-004 (2026-10-08) was authored by eaojnr as the design response. It establishes the evidence and validation layer that connects qualification and participation to a machine-testable conformance decision. This ADR accepts CR-VAS-004 as the formal evidence and conformance validation framework for Agentic Value Stream.

## 2. Decision

### 2.1 Normative Principle

The repository SHALL distinguish:

```
Claim -> Evidence -> Validation -> Qualification Decision -> Conformance Status
```

An AVS instance SHALL NOT be considered semantically conformant solely because it is named "agentic", contains an Agent, uses AI, uses an LLM, is autonomous, uses orchestration, adapts, or performs automated actions.

### 2.2 Three Levels of Evidence

The framework SHALL classify evidence into three semantic levels:

- Structural Evidence. Evidence that the required semantic relationships exist (Value Stream, Agentic Participation, Intent, Authority, Context, Action selection, Outcome contribution). Answers: Is the required semantic structure represented?
- Behavioural Evidence. Evidence that the represented participation actually behaves according to the semantics. Answers: Does the realisation actually behave agentically?
- Outcome Evidence. Evidence that agentic participation materially contributes to Value Stream realisation. Answers: Does the agentic behavior materially matter to the Value Stream?

### 2.3 Qualification Evidence Chain

The minimum evidence chain SHALL be:

```
Value Stream -> Agentic Participation -> Entrusted Intent -> Bounded Authority ->
  Contextual Interpretation -> Permissible Alternatives -> Action / Progression Selection ->
  Material Value Contribution
```

A missing mandatory link SHALL prevent full semantic qualification.

### 2.4 Evidence Sufficiency

Evidence SHALL be classified as sufficient, partial, insufficient, contradictory, or unverifiable. Sufficient evidence supports the qualification condition. Partial evidence does not fully establish the condition. Insufficient evidence asserts but does not demonstrate. Contradictory evidence conflicts with the claim. Unverifiable evidence cannot be independently inspected.

### 2.5 Mandatory vs Supporting Evidence

Mandatory evidence (required for AVS qualification): Value Stream identity, Agentic Participation, intent, authority, context, alternative selection, material value contribution.

Supporting evidence (useful but not mandatory): AI model information, agent architecture, automation architecture, autonomy level, performance metrics, intervention statistics, implementation technology, training data, model evaluation.

Supporting evidence SHALL NOT replace semantic evidence.

### 2.6 Evidence Independence

The same evidence SHALL NOT automatically satisfy multiple independent semantic conditions. The validation framework SHALL avoid circular evidence.

### 2.7 Evidence Provenance

Every material evidence item SHOULD have provenance including id, type, description, source, source_type (design_document, architecture_model, policy, configuration, execution_trace, decision_log, audit_record, test_result, simulation, human_review, system_observation, measurement), observed_at, provided_by, validated_by, validation_method, and confidence (high, medium, low, unknown).

### 2.8 Evidence Confidence

Confidence SHALL NOT override a missing mandatory semantic condition. High-confidence evidence of AI usage cannot compensate for absent evidence of delegated intent or bounded authority.

### 2.9 Qualification Decision Model

The qualification decision SHALL follow:

```
Value Stream? -> Agentic Participation? ->
  Intent + Authority + Context + Selection? -> Material Value Contribution? -> AVS QUALIFIED
```

Any mandatory condition failing SHALL prevent a qualified status.

### 2.10 Conformance Status

The repository SHALL distinguish conformance status: claimed, under_review, conditionally_conformant, conformant, non_conformant, expired.

### 2.11 Semantic Conformance vs Maturity

Conformance SHALL NOT be conflated with maturity. An organisation can have a highly mature implementation that is not semantically Agentic, or a semantically conformant AVS that is operationally immature.

The progression SHALL be:

```
Semantic Qualification -> Conformance -> Operational Capability -> Maturity
```

Maturity SHALL be addressed in a subsequent CR (CR-VAS-006), NOT here.

### 2.12 Counterfactual Validation

Materiality SHOULD preferably be tested through a counterfactual comparison of actual agentic realisation vs equivalent non-agentic realisation. The comparison evaluates differences in progression, decisions, action selection, outcome, intervention, and value realisation. The counterfactual need not always be executed in production. It MAY be demonstrated through simulation, historical replay, controlled testing, or analytical reasoning.

### 2.13 Behavioral Test Model

The conformance kit SHALL include behavioral scenarios. Each scenario SHOULD define id, purpose, preconditions, context, available_actions, authority, expected_selection, expected_progression, expected_outcome, evidence, and result.

### 2.14 Positive Conformance Tests

At minimum 8 positive conformance tests SHALL be implemented: VAS-CF-P01 Delegated Outcome, VAS-CF-P02 Contextual Selection, VAS-CF-P03 Bounded Authority, VAS-CF-P04 Material Progression, VAS-CF-P05 Human-Agent Hybrid, VAS-CF-P06 Non-AI Agentic, VAS-CF-P07 Localised Agenticity, VAS-CF-P08 Multi-Agent Coordination.

### 2.15 Negative Conformance Tests

At minimum 10 negative conformance tests SHALL be implemented: VAS-CF-N01 AI Only, VAS-CF-N02 Agent Label Only, VAS-CF-N03 Workflow Only, VAS-CF-N04 Recommendation Only, VAS-CF-N05 Fixed Automation, VAS-CF-N06 Autonomous System Without Value Materiality, VAS-CF-N07 Human Routine Execution, VAS-CF-N08 Missing Authority, VAS-CF-N09 Missing Selection, VAS-CF-N10 Non-Material Agentic Behavior.

### 2.16 Boundary Test Matrix

The repository SHALL include explicit boundary tests per CR-VAS-004 §21: LLM generates a response, AI recommends an action, Agent selects within policy, RPA executes fixed workflow, Autonomous vehicle performs transport, Human resolves exceptional case, Agent routes tickets using fixed rules, Agent selects customer remediation, Multi-agent negotiation affects fulfilment, AI forecasts demand.

### 2.17 Human Validation

Automated validation SHALL NOT be the sole mechanism for semantic qualification. The validation chain SHALL combine machine validation, evidence inspection, and semantic review.

### 2.18 Validation Roles

The repository SHOULD distinguish four roles: Instance Owner, Semantic Validator, Domain Reviewer, Governance Authority. These roles SHALL NOT be embedded as semantic requirements for being an AVS.

### 2.19 Evidence Lifecycle

Evidence SHALL have a lifecycle: Created, Submitted, Validated, Accepted, Monitored, Revalidated, Expired/Superseded. A conformance claim is therefore potentially time-bound.

### 2.20 Conformance Drift

The repository SHOULD support detection of semantic drift. Drift triggers include authority changed, agent behavior changed, workflow changed, Value Stream changed, Agentic Participation removed, action space changed, policy changed, human escalation removed, materiality changed. Drift is different from maturity deterioration.

### 2.21 Evidence Freshness

Evidence SHOULD optionally specify valid_from, valid_until, and review_interval. Freshness SHOULD be determined according to the volatility of the underlying semantic claim.

### 2.22 Conformance Levels

The repository SHALL NOT create multiple levels of "agenticity". The concept itself SHALL remain binary at the semantic boundary. Maturity is evaluated separately in a future specification.

### 2.23 Conformance Kit Architecture

The conformance kit SHALL evolve toward: kit/ with kit.yaml, schema/, positive/, negative/, boundary/, structural/, behavioral/, evidence/, expected-results/. Exact directory names follow the repository's established convention.

### 2.24 Conformance Result

Each test result SHALL be machine-readable: test_id, status (pass, fail, inconclusive, not_applicable), qualification_condition, evidence, observations, rationale. Inconclusive SHALL be distinguished from fail.

### 2.25 Qualification Decision Rules

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

### 2.26 Conformance Evidence vs Operational Telemetry

Runtime telemetry can provide evidence but SHALL NOT become the semantic definition. Telemetry is evidence, not semantics.

### 2.27 Conformance and Governance Separation

The semantic specification defines what MUST be true. The governance framework may define who is authorised to certify that it is true. These SHALL remain separate. This prevents organisational governance requirements from contaminating the universal semantic definition.

### 2.28 Conformance Kit Expansion

The conformance kit SHALL expand to 61 tests:

- 5 positive (AVS-VAL-01..07 required-value coverage), per CR-VAS-002.
- 5 negative (AVS-EXC-01..07 exclusion coverage), per CR-VAS-002.
- 5 edge case (AVS-EDGE-01..05 compositional arrangements), per CR-VAS-002.
- 8 structural (VAS-ST-01..08 participation structure), per CR-VAS-003.
- 10 boundary (VAS-BT-01..10 participation boundary distinction), per CR-VAS-003.
- 8 conformance positive (VAS-CF-P01..P08), per CR-VAS-004.
- 10 conformance negative (VAS-CF-N01..N10), per CR-VAS-004.
- 10 conformance boundary (VAS-CF-BT-01..10), per CR-VAS-004.

## 3. Implementation

### 3.1 concept.yaml evidence_conformance block

A new `evidence_conformance:` block is appended to the Agentic Value Stream concept record, carrying the three evidence levels, qualification evidence chain, evidence sufficiency vocabulary, mandatory vs supporting evidence, evidence independence, evidence provenance template, evidence confidence, qualification decision model, conformance status vocabulary, semantic conformance vs maturity separation, qualification evidence record template, materiality evidence + counterfactual validation, behavioural test model, positive + negative + boundary test inventory, validation roles, evidence lifecycle, conformance drift, evidence freshness, conformance levels, conformance kit architecture, conformance result template, qualification decision rules, telemetry vs evidence separation, and conformance vs governance separation.

### 3.2 Conformance kit

8 new conformance positive tests (cf-positive-01..08 / VAS-CF-P01..P08), 10 new conformance negative tests (cf-negative-01..10 / VAS-CF-N01..N10), and 10 new conformance boundary tests (cf-boundary-01..10 / VAS-CF-BT-01..10) are added under `kit/`. The kit manifest is updated to reflect the expanded coverage and inventory.

### 3.3 Documentation

5 new documentation files are added under `docs/`:

- `evidence.md` ; Evidence model, three levels, qualification evidence chain, sufficiency vocabulary, mandatory vs supporting evidence, provenance, confidence.
- `qualification.md` ; Qualification decision model, decision rules, materiality evidence, counterfactual validation.
- `validation.md` ; Validation chain (machine + evidence + review), roles, evidence lifecycle, freshness, conformance result template.
- `boundary-testing.md` ; Boundary test matrix per CR-VAS-004 §21 and reconciliation with CR-VAS-003 boundary tests.
- `conformance-drift.md` ; Drift triggers, drift vs maturity, drift handling, drift evidence.

`docs/concept.md` receives a new "Evidence and Conformance (CR-VAS-004)" section. `docs/conformance.md` is regenerated with the expanded 61-test inventory.

### 3.4 Visuals

Three new PlantUML diagrams are added under `visuals/agentic-value-stream/`:

- `qualification-decision-model.puml` ; CR-VAS-004 §12 + §30.
- `evidence-lifecycle.puml` ; CR-VAS-004 §24.
- `conformance-status-machine.puml` ; CR-VAS-004 §13 + §30.

## 4. Consequences

### 4.1 Positive

- The repository can now validate that an AVS instance is semantically conformant through explicit evidence rather than terminology.
- The qualification decision model is deterministic and machine-testable.
- Counterfactual validation establishes material contribution to Value Stream realisation.
- The conformance status vocabulary (claimed, under_review, conditionally_conformant, conformant, non_conformant, expired) supports time-bound conformance claims.
- Drift detection supports detection of semantic conformance changes over time.
- Conformance and maturity are explicitly separated.

### 4.2 Negative

- The conformance kit now carries 61 tests (vs 33). CI regeneration must handle the expanded inventory.
- Future CRs (CR-VAS-005 Measurement & Operational Value, CR-VAS-006 Maturity & Capability) will inherit the evidence + conformance model.
- Validators must distinguish pass, fail, inconclusive, and not_applicable. Inconclusive is not equivalent to fail.

### 4.3 Architectural alignment

This ADR continues the architectural separation established by ES-ADR-052 + ES-ADR-053:

- CR-VAS-002 = SEMANTIC QUALIFICATION (what makes a Value Stream Agentic).
- CR-VAS-003 = PARTICIPATION & REALIZATION (how is agentic participation represented).
- CR-VAS-004 = EVIDENCE & CONFORMANCE (how do we prove it).
- CR-VAS-005 = MEASUREMENT & OPERATIONAL VALUE (how well does it work).
- CR-VAS-006 = MATURITY & CAPABILITY (how well can the organisation scale and govern it).

CR-VAS-004 is the third of five CRs that form a coherent semantic-to-operational chain. The semantic control loop is now complete:

```
SEMANTIC DEFINITION -> REPRESENTATION -> EVIDENCE & VALIDATION -> CONFORMANCE
```

This is the point at which the Agentic Value Stream repository stops being merely a concept definition and becomes a governable semantic specification.

## 5. Promotion Metadata

- Status: Accepted (semantic baseline extension, 2026-10-08).
- Cardinal author rule: Emmanuel A. Otchere (cardinal author rule, 2026-09-23).
- Vendor-specific material from embargoed sources: 0 references.
- D-004 dash rule: 0 en-dash (U+2013), 0 em-dash (U+2014), 0 triple-em-dash (U+2E3B).
- WSF metamodel not modified.
- OpenDEA metamodel not modified.

## 6. Related Artefacts

- CR-VAS-004 (Evidence, Conformance & Qualification Validation Model).
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
