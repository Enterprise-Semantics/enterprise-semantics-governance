# ADR-ES-056 ; Agentic Value Stream Maturity & Capability Framework

Status: Accepted
Date: 2026-10-08
Deciders: eaojnr
Decision Type: Semantic baseline extension (maturity & capability layer for Agentic Value Stream)
Scope: Enterprise-Semantics/agentic-value-stream (single concept baseline; maturity model reusable for future AVS extensions)
Implements: CR-VAS-006
Amends: ES-ADR-005 + ES-ADR-052 + ES-ADR-053 + ES-ADR-054 + ES-ADR-055 (extends AVS semantic baseline with formal maturity and capability model)
Supersedes: None
Depends: ES-ADR-005, ES-ADR-031, ES-ADR-049, ES-ADR-051, ES-ADR-052, ES-ADR-053, ES-ADR-054, ES-ADR-055

## 1. Context

ES-ADR-052 + CR-VAS-002 (2026-10-07) introduced the formal qualification test that establishes necessary and sufficient conditions for AVS qualification. ES-ADR-053 + CR-VAS-003 (2026-10-08) introduced the Agentic Participation & Value Stream Realization Model. ES-ADR-054 + CR-VAS-004 (2026-10-08) introduced the evidence and conformance validation model. ES-ADR-055 + CR-VAS-005 (2026-10-08) introduced the Measurement & Operational Value Model.

The semantic definition, participation structure, evidence + conformance layer, and measurement layer together answer four questions:

1. Is this an Agentic Value Stream? (CR-VAS-002 qualification)
2. Can we prove it? (CR-VAS-004 conformance)
3. How well does it perform and create value? (CR-VAS-005 measurement)
4. How capable are we at systematically realizing and scaling it? (CR-VAS-006 maturity)

CR-VAS-006 (2026-10-08) was authored by eaojnr as the design response. It establishes the organizational maturity and capability progression model that evaluates how systematically the organization can design, govern, operate, measure, improve, and scale Agentic Value Streams.

The single most important design decision in CR-VAS-006 is: maturity is a property of the organization, not of the AVS itself. Maturity does NOT determine whether a Value Stream is semantically an AVS. A high-maturity organization may have non-agentic Value Streams. A low-maturity organization may operate a semantically conformant AVS. A highly performant AVS does not automatically imply organizational maturity.

This ADR accepts CR-VAS-006 as the formal Maturity & Capability Framework for Agentic Value Stream.

## 2. Decision

### 2.1 Normative Principle

The repository SHALL distinguish four layers, in this order:

- Semantic qualification (CR-VAS-002): is this an AVS?
- Conformance & evidence (CR-VAS-004): is the claim valid?
- Operational measurement (CR-VAS-005): how well does it perform?
- Maturity & capability (CR-VAS-006): how systematically can the organization operate, govern, improve, and scale it?

The dependency is intentionally one-directional. Maturity SHALL NOT be used as evidence of agenticity. AI adoption, agent count, autonomy percentage, model sophistication, and operational scale SHALL NOT establish maturity on their own.

### 2.2 Six Maturity Levels

The maturity model defines six levels of organizational AVS capability:

| Level | Name | Meaning |
|---|---|---|
| L0 | Unaware | No deliberate AVS capability. |
| L1 | Aware | AVS concepts understood and identified. |
| L2 | Defined | AVS practices, boundaries and governance are defined. |
| L3 | Implemented | Conformant AVS implementations operate in production. |
| L4 | Managed | AVS performance, risk, value and improvement are systematically managed. |
| L5 | Scaled & Adaptive | AVS capability is governed and continuously optimized across the enterprise. |

Levels represent increasing organizational capability, not increasing agenticity.

### 2.3 Six Capability Dimensions

Maturity SHALL be assessed across six capability dimensions:

| ID | Dimension |
|---|---|
| C1 | AVS Design & Semantic Modeling |
| C2 | Authority, Governance & Risk |
| C3 | Operational Realization |
| C4 | Value & Performance Management |
| C5 | Learning & Continuous Improvement |
| C6 | Portfolio Scaling & Enterprise Integration |

### 2.4 Multidimensional Assessment Rule

A single arithmetic average SHALL NOT be the default maturity mechanism. The profile SHALL remain visible with per-dimension levels and limiting dimensions called out.

Overall Maturity = minimum of required capability dimensions, subject to level-specific gates. This prevents exceptional strength in one area from masking fundamental weakness elsewhere.

### 2.5 Mandatory Gates

| Gate | Requires |
|---|---|
| L2 Gate | defined AVS semantics, defined qualification approach, authority model, evidence model, measurement model, governance ownership |
| L3 Gate | at least one conformant production AVS, operational authority enforcement, operational intervention/escalation, outcome measurement, traceable evidence |
| L4 Gate | repeatable performance management, baseline comparison, value measurement, risk monitoring, conformance drift management, systematic improvement |
| L5 Gate | multiple operational AVS implementations, portfolio governance, reusable capability patterns, enterprise measurement, demonstrated scaling, continuous capability evolution |

### 2.6 Maturity Anti-Patterns (Rejected)

Per CR-VAS-006 §21, the following SHALL be explicitly rejected as maturity evidence:

- Maturity = autonomy
- Maturity = AI sophistication
- Maturity = agent count
- Maturity = automation percentage
- Maturity = intervention reduction
- Maturity = cost reduction
- Maturity = production deployment
- Maturity = semantic complexity

### 2.7 Maturity Invariants

CR-VAS-006 introduces 12 normative invariants (AVS-MAT-INV-001..012). The most foundational:

- AVS-MAT-INV-001: maturity does not define AVS semantic qualification.
- AVS-MAT-INV-002: conformance precedes L3 production maturity.
- AVS-MAT-INV-003: AI is not required for maturity.
- AVS-MAT-INV-004: autonomy is not required for maturity.
- AVS-MAT-INV-005: human intervention is not inherently a maturity defect.
- AVS-MAT-INV-006: agent count does not determine maturity.
- AVS-MAT-INV-009: maturity shall support regression.
- AVS-MAT-INV-010: overall maturity shall not conceal mandatory capability deficiencies.

### 2.8 Human Participation Guarantee

Human participation SHALL remain a first-class design option at every maturity level. A mature implementation chooses the appropriate interaction pattern based on risk, authority, materiality, regulation, reversibility, consequence, confidence, and customer impact.

The target state is optimal delegation of value-realization decisions and actions within appropriate authority boundaries. Maximum delegation is NOT the target state.

### 2.9 Maturity Drift

The model SHALL support regression. L4 Managed can become L3 Implemented after major platform migration, measurement gaps, or authority monitoring degradation. Maturity SHALL NOT be treated as an irreversible progression.

### 2.10 Enterprise Architecture Relationship

AVS maturity informs business architecture, operating model transformation, enterprise architecture, AI strategy, automation strategy, workforce transformation, governance, risk management, technology investment, and data and knowledge strategy.

AVS maturity SHALL remain semantically scoped to Agentic Value Stream capability. It SHALL NOT become a generic enterprise digital maturity model.

## 3. Implementation

### 3.1 Concept Record (concept.yaml)

A new top-level `maturity:` block is added to `Enterprise-Semantics/agentic-value-stream/concept.yaml`. The block has 28 sub-keys formalizing principle, normative question, separation principles, six-level model, six-dimension capability model, capability progression matrix, multidimensional assessment rule, mandatory gates, evidence requirements by level, eight anti-patterns, human participation guarantee, full-automation caveat, capability lifecycle, transition criteria, machine-readable schema, assessment record template, capability gap model, improvement planning chain, enterprise architecture relationship, governance roles, assessment frequency, drift principle, 12 invariants, and boundary assertions.

Version bumped 1.3.0 -> 1.4.0. Promotion history extended.

### 3.2 Conformance Kit

`kit/kit.yaml` is updated to coverage 121 (was 91). New `ma_positive`, `ma_negative`, `ma_boundary` blocks added at top level. Provenance and boundary assertions extended.

### 3.3 Tests

30 new maturity tests:

- 10 positive (VAS-MA-P01..P10): L1..L5 capability, six capability dimensions, multidimensional assessment profile, machine-readable maturity schema, human participation guarantee, capability lifecycle + regression.
- 10 negative (VAS-MA-N01..N10): the eight anti-patterns and two anti-pattern category tests (maturity-as-qualification and arithmetic-average-concealment).
- 10 boundary (VAS-MA-BT-01..10): maturity vs qualification, conformance, measurement, AI, autonomy, automation, human intervention, drift/regression, technology maturity model, operational performance.

### 3.4 Documentation

Seven new docs:

- `maturity.md`: purpose, core principle, separation principles, scope.
- `capability-model.md`: six capability dimensions with detailed scope, capability progression matrix.
- `maturity-levels.md`: L0..L5 with definitions, minimum capabilities, critical distinctions, gates.
- `maturity-assessment.md`: assessment principle, multidimensional assessment rule, overall maturity rule, mandatory gates, evidence requirements by level, assessment record template, assessment frequency.
- `capability-gaps.md`: gap model, gap types, improvement planning chain.
- `maturity-governance.md`: governance roles, capability lifecycle, transition criteria, drift, regression, enterprise architecture relationship.
- `maturity-anti-patterns.md`: eight anti-patterns with rejection rationale and detection heuristics.

### 3.5 Visuals

Three new PUML diagrams:

- `maturity-levels.puml`: L0..L5 state diagram with regression arrows.
- `maturity-capability-dimensions.puml`: six capability dimensions + profile container.
- `maturity-anti-patterns.puml`: the eight anti-patterns grouped under "Maturity is NOT...".

### 3.6 Mappings

The repository's `mappings/wsf.yaml` and `mappings/opendea.yaml` receive new `maturity_alignment` blocks, treating maturity as a repository-specific framework overlay over WSF and OpenDEA without modifying either metamodel.

## 4. Consequences

### 4.1 Positive

- The repository now answers the fourth question: how capable is the organization at systematically realizing and scaling AVS?
- Maturity is explicitly separated from semantic qualification, conformance, and measurement. A clean four-question architecture is established.
- The six-level model + six-dimension capability model is semantically anchored.
- The multidimensional assessment rule (gated minimum, not arithmetic mean) prevents exceptional strength in one area from masking fundamental weakness elsewhere.
- The 8 anti-patterns prevent maturity from becoming a backdoor definition of agenticity.
- The 12 invariants bind maturity assessments, dashboards, and reporting.
- Maturity regression is supported: L4 -> L3 is valid.
- Human participation is explicitly guaranteed as a first-class design option.

### 4.2 Negative

- The conformance kit now carries 121 tests (vs 91 Wave 3). CI regeneration must handle the expanded inventory.
- Future CR-VAS-007+ (Governance & Lifecycle) will inherit the maturity model.
- Organizations may resist the "minimum-required-dimension" rule (which prevents gaming the score by concentrating on a single dimension).

### 4.3 Architectural alignment

This ADR completes the 5-part semantic-to-operational chain:

- CR-VAS-002 = SEMANTIC QUALIFICATION.
- CR-VAS-003 = PARTICIPATION & REALIZATION.
- CR-VAS-004 = EVIDENCE & CONFORMANCE.
- CR-VAS-005 = MEASUREMENT & OPERATIONAL VALUE.
- CR-VAS-006 = MATURITY & CAPABILITY.

With CR-VAS-006, the Agentic Value Stream repository now establishes a coherent semantic-to-operational specification that supports qualification, participation, evidence, conformance, measurement, and maturity.

## 5. Promotion Metadata

- Status: Accepted (semantic baseline extension, 2026-10-08).
- Cardinal author rule: Emmanuel A. Otchere (cardinal author rule, 2026-09-23).
- Vendor-specific material from embargoed sources: 0 references.
- D-004 dash rule: 0 en-dash (U+2013), 0 em-dash (U+2014), 0 triple-em-dash (U+2E3B).
- WSF metamodel not modified.
- OpenDEA metamodel not modified.

## 6. Related Artefacts

- CR-VAS-006 (Maturity & Capability Model).
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
- CR-VAS-005 (Measurement & Operational Value Model).

<!-- Authored by: Emmanuel A. Otchere (cardinal author rule, 2026-10-08) -->
