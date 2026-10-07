# CR-VAS-002 ; Agentic Value Stream Formal Semantic Qualification

Status: Accepted
Date: 2026-10-07
Deciders: eaojnr
Decision Type: Semantic baseline (formal qualification rules for Agentic Value Stream)
Concept: Agentic Value Stream (ES:CONCEPT:agentic-value-stream)
Repository: Enterprise-Semantics/agentic-value-stream
Priority: Critical
Type: Semantic/Metamodel/Conformance
Target: Agentic Value Stream semantic baseline v1.0.0
Implements: ES-ADR-052

## 1. Change Objective

Establish a formal, testable semantic qualification rule for Agentic Value Stream. The rule must establish:

1. Necessary conditions for qualification (what must be true).
2. Sufficient conditions for qualification (what guarantees qualification).
3. Exclusion conditions for qualification (what disqualifies a candidate).
4. Materiality requirements (how much is enough).
5. The relationship between agentic participation and Value Stream realisation.
6. A normative qualification test implementable by the conformance kit.

The framework MUST NOT introduce Agentic Value Stage, Agentic Workflow, Agentic Operations, or Autonomous Value Stream as new constructs. Existing Value Stage remains the stage construct. AI is implementation technology, not semantic identity.

## 2. Problem Statement

The current semantic definition permits adjacent concepts to appear superficially equivalent. Deterministic automation, adaptive automation, decision-support AI, human discretion, autonomous systems, and dynamic workflows may each appear to satisfy the Agentic Value Stream narrative definition, when in fact they do not.

AI, automation, adaptation, decision-making, agency, and human discretion alone MUST NOT establish AVS qualification. The semantic boundary must identify the combination of properties constituting material agentic realisation of value-stream progression.

The qualification must be:

1. Testable. A candidate can be evaluated with an unambiguous pass/fail.
2. Auditable. The qualification can be verified by a third party.
3. Distinguishing. The qualification separates AVS from adjacent constructs.
4. Implementation-agnostic. The qualification does not require AI, autonomy, automation, or any specific technology.

## 3. Normative Semantic Principle

An Agentic Value Stream is a Value Stream in which one or more material portions of value realisation are performed through agentic participation, where an authorised actor is entrusted with an intended outcome or progression objective and is able to interpret relevant context and select permissible actions or progression paths within a bounded authority rather than merely executing a completely predetermined sequence.

## 4. Required Values

A candidate MUST satisfy all seven required values:

1. AVS-VAL-01 Value-Stream Foundation. The candidate is a Value Stream.
2. AVS-VAL-02 Material Agentic Participation. One or more stages are materially realised through agentic behavior.
3. AVS-VAL-03 Delegated or Entrusted Intent. The agentic participants are entrusted with an intended outcome.
4. AVS-VAL-04 Bounded Authority. The agentic participants operate within explicit bounded authority.
5. AVS-VAL-05 Contextual Interpretation. The agentic participants interpret relevant context in service of the entrusted intent.
6. AVS-VAL-06 Permissible Action or Progression Selection. The agentic participants select from a set of permissible actions or progression paths.
7. AVS-VAL-07 Value-Realization Effect. The agentic participation contributes to stakeholder value realisation.

## 5. Not Required Values

The following are explicitly NOT required. Their absence does not disqualify; their presence alone does not qualify.

1. AVS-NRQ-01 AI. AI is not a prerequisite.
2. AVS-NRQ-02 Autonomy. Autonomy is not a prerequisite.
3. AVS-NRQ-03 Automation. Automation is not a prerequisite.
4. AVS-NRQ-04 Decision-making as isolated quality. Decision-making alone is not sufficient.
5. AVS-NRQ-05 Agency as isolated quality. Agency alone is not sufficient.
6. AVS-NRQ-06 Learning. Learning is not a prerequisite.
7. AVS-NRQ-07 Human intervention is illegitimate. Human intervention remains legitimate.

## 6. Exclusion Conditions

A candidate fails qualification if any of the seven exclusion conditions hold:

1. AVS-EXC-01 Deterministic automation only. Predetermined sequence with no contextual interpretation.
2. AVS-EXC-02 Adaptive automation only. Stimulus-response adaptation without delegated intent.
3. AVS-EXC-03 Decision-support AI only. AI recommendations executed by a separate actor without progression authority.
4. AVS-EXC-04 Human discretion only. The entire stream is executed by humans with full discretion at every stage.
5. AVS-EXC-05 Autonomous system participation only. Self-directed progression without external authority binding.
6. AVS-EXC-06 Dynamic workflow participation only. Workflow without value-stream anchoring.
7. AVS-EXC-07 Insufficient material proportion. Agentic participation below the materiality threshold.

## 7. Materiality

Materiality is quantified by three criteria:

1. AVS-MAT-01 Stage-count materiality. At least one Value Stage is materially agentic.
2. AVS-MAT-02 Value-effect materiality. The agentic participation produces a stakeholder-observable value effect.
3. AVS-MAT-03 Continuity materiality. The agentic participation persists across the stage realisation, not as a single decision in an otherwise fixed sequence.

## 8. Normative Qualification Test

A candidate PASSES iff:

(a) All seven required values hold (AVS-VAL-01 through AVS-VAL-07).
(b) None of the seven exclusion conditions hold (AVS-EXC-01 through AVS-EXC-07).
(c) Materiality is satisfied (AVS-MAT-01 through AVS-MAT-03).

A candidate FAILS iff any required value does not hold, any exclusion condition holds, or materiality is not satisfied.

## 9. Architectural Invariants

The following thirteen architectural invariants are enforced by the conformance kit:

- AVS-INV-001 Value-Stream Anchor Invariant.
- AVS-INV-002 Stage Composition Invariant.
- AVS-INV-003 Material Agentic Participation Invariant.
- AVS-INV-004 Delegated Intent Invariant.
- AVS-INV-005 Bounded Authority Invariant.
- AVS-INV-006 Contextual Interpretation Invariant.
- AVS-INV-007 Action Selection Invariant.
- AVS-INV-008 Value-Realisation Invariant.
- AVS-INV-009 AI-Not-Required Invariant.
- AVS-INV-010 Autonomy-Not-Required Invariant.
- AVS-INV-011 Automation-Not-Required Invariant.
- AVS-INV-012 Determinism-Exclusion Invariant.
- AVS-INV-013 Boundary-Assertion Invariant.

## 10. Edge Cases

The following five edge cases are recognised compositional arrangements:

1. AVS-EDGE-01 Single-stage material agentic participation.
2. AVS-EDGE-02 Cross-stage material agentic participation.
3. AVS-EDGE-03 Multiple agentic participants with separate authorities.
4. AVS-EDGE-04 Agentic participation with co-existing automation.
5. AVS-EDGE-05 Agentic participation with co-existing human discretion.

## 11. Boundary Preservation

This framework does NOT introduce Agentic Value Stage, Agentic Workflow, Agentic Operations, or Autonomous Value Stream as new constructs. Existing Value Stage remains the stage construct. The qualification framework is bounded to Agentic Value Stream.

## 12. Conformance Kit

The conformance kit implements the qualification test with fifteen tests:

- 5 positive tests asserting each required value group (AVS-VAL-01..07).
- 5 negative tests asserting each primary exclusion condition (AVS-EXC-01..04, AVS-EXC-07).
- 5 edge case tests asserting compositional arrangements (AVS-EDGE-01..05).

## 13. Architectural Outcome

The Agentic Value Stream semantic is now formally distinguishable from:

1. Deterministic automation (AVS-EXC-01).
2. Adaptive automation (AVS-EXC-02).
3. Decision-support AI (AVS-EXC-03).
4. Human discretion alone (AVS-EXC-04).
5. Autonomous systems (AVS-EXC-05).
6. Dynamic workflows (AVS-EXC-06).
7. Immaterial participation (AVS-EXC-07).

The Agentic Value Stream semantic preserves the necessary and sufficient conditions for qualification without conflating them with adjacent constructs.

## 14. Definition of Done

The qualification framework is considered complete when:

1. `concept.yaml` carries the `qualification:` block with all seven required values, seven not-required values, seven exclusion conditions, materiality, thirteen invariants, and five edge cases.
2. `kit/positive-01.yaml` through `kit/positive-05.yaml` assert each required value group.
3. `kit/negative-01.yaml` through `kit/negative-05.yaml` assert each primary exclusion condition.
4. `kit/edge-case-01.yaml` through `kit/edge-case-05.yaml` assert compositional arrangements.
5. `kit/kit.yaml` auto-derives coverage from the kit/ inventory.
6. `docs/concept.md` includes the formal qualification section.
7. `docs/conformance.md` records the conformance status.
8. `visuals/agentic-value-stream/semantic-anatomy.puml` visualises the qualification structure.
9. `mappings/wsf.yaml` includes the qualification overlay section.
10. `mappings/opendea.yaml` includes the qualification overlay section.
11. The canonical mirror in `Enterprise-Semantics/enterprise-semantics` is updated.
12. The conformance kit mirror in `Enterprise-Semantics/enterprise-semantics-test-probe` is updated.
13. The governance ADR ES-ADR-052 is filed and Accepted.

## 15. Cardinal Rules

- Author: Emmanuel A. Otchere (cardinal author rule, 2026-09-23)
- D-004 dash rule: 0 en-dash (U+2013) ; 0 em-dash (U+2014) ; 0 horizontal-ellipsis divider (U+2E3B)
- D-005 prose rule: 0 tripled-semicolon (;;;); preserved only inside backtick code spans (rule documentation)
- D-006 writing rule: coherent prose, no ad-libs or telegraphic phrasing, paragraphs lead into each other, crisp titles, good formatting
- SDO-neutral sourcing: ISO/IEC, ITU-T, ETSI, NIST (no TMForum, no vendor-specific)
- Vendor embargo: 0 references to specific vendors in semantic content

## 16. Promotion Metadata

- Promotion: Accepted on filing (per ES-ADR-052 acceptance).
- Status: Accepted.
- Lifecycle status: candidate (per CR-AVS-001 §14; promotion to Established reserved for acceptance review).
- Conformance status: semantically_conformant.
- Date: 2026-10-07.
