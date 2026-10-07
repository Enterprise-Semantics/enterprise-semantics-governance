# ADR-ES-052 ; Agentic Value Stream Semantic Qualification Framework

Status: Accepted
Date: 2026-10-07
Deciders: eaojnr
Decision Type: Semantic baseline (formal qualification rules for Agentic Value Stream)
Scope: Enterprise-Semantics/agentic-value-stream (single concept baseline; framework reusable for future qualifications)
Implements: CR-VAS-002
Amends: ES-ADR-005 (extends Agentic Value Stream semantic baseline with formal qualification)
Supersedes: None
Depends: ES-ADR-005 (Agentic Value Stream decision), ES-ADR-031 (5-category boundary taxonomy), ES-ADR-049 (per-concept repo self-containment), ES-ADR-051 (editorial restructure)

## 1. Context

ES-ADR-005 established Agentic Value Stream as a specialisation of Value Stream. The original decision defined the concept narratively but did not specify necessary and sufficient conditions for qualification. As a result, superficially adjacent constructs (deterministic automation, adaptive automation, decision-support AI, human discretion, autonomous systems, dynamic workflows) could appear to satisfy the Agentic Value Stream semantic, when in fact they do not.

Review-ES-000 (2026-10-07) identified this as the most important semantic gap in the repository: the definition is stronger than its executable and conformance machinery. The semantic baseline describes consequences of agentic behavior better than the irreducible condition that makes behavior agentic.

CR-VAS-002 (2026-10-07) was authored by eaojnr as the design response. This ADR accepts CR-VAS-002 as the formal qualification framework for Agentic Value Stream.

## 2. Decision

### 2.1 Formal qualification test

A candidate qualifies as an Agentic Value Stream if and only if:

(a) All seven required values hold (AVS-VAL-01 through AVS-VAL-07).
(b) None of the seven exclusion conditions hold (AVS-EXC-01 through AVS-EXC-07).
(c) Materiality is satisfied (AVS-MAT-01 through AVS-MAT-03).

The seven required values are:

1. AVS-VAL-01 Value-Stream Foundation. The candidate is a Value Stream.
2. AVS-VAL-02 Material Agentic Participation. One or more stages are materially realised through agentic behavior.
3. AVS-VAL-03 Delegated or Entrusted Intent. The agentic participants are entrusted with an intended outcome.
4. AVS-VAL-04 Bounded Authority. The agentic participants operate within explicit bounded authority.
5. AVS-VAL-05 Contextual Interpretation. The agentic participants interpret relevant context in service of the entrusted intent.
6. AVS-VAL-06 Permissible Action or Progression Selection. The agentic participants select from a set of permissible actions or progression paths.
7. AVS-VAL-07 Value-Realization Effect. The agentic participation contributes to stakeholder value realisation.

The seven not-required values are:

1. AVS-NRQ-01 AI. AI is not a prerequisite.
2. AVS-NRQ-02 Autonomy. Autonomy is not a prerequisite.
3. AVS-NRQ-03 Automation. Automation is not a prerequisite.
4. AVS-NRQ-04 Decision-making as isolated quality. Decision-making alone is not sufficient.
5. AVS-NRQ-05 Agency as isolated quality. Agency alone is not sufficient.
6. AVS-NRQ-06 Learning. Learning is not a prerequisite.
7. AVS-NRQ-07 Human intervention is illegitimate. Human intervention remains legitimate.

The seven exclusion conditions are:

1. AVS-EXC-01 Deterministic automation only. Predetermined sequence with no contextual interpretation.
2. AVS-EXC-02 Adaptive automation only. Stimulus-response adaptation without delegated intent.
3. AVS-EXC-03 Decision-support AI only. AI recommendations executed by a separate actor without progression authority.
4. AVS-EXC-04 Human discretion only. The entire stream is executed by humans with full discretion at every stage.
5. AVS-EXC-05 Autonomous system participation only. Self-directed progression without external authority binding.
6. AVS-EXC-06 Dynamic workflow participation only. Workflow without value-stream anchoring.
7. AVS-EXC-07 Insufficient material proportion. Agentic participation below the materiality threshold.

### 2.2 Materiality

Materiality is quantified by three criteria:

1. AVS-MAT-01 Stage-count materiality. At least one Value Stage is materially agentic.
2. AVS-MAT-02 Value-effect materiality. The agentic participation produces a stakeholder-observable value effect.
3. AVS-MAT-03 Continuity materiality. The agentic participation persists across the stage realisation, not as a single decision in an otherwise fixed sequence.

### 2.3 Architectural invariants

Thirteen architectural invariants are enforced by the conformance kit:

AVS-INV-001 through AVS-INV-013. They include the value-stream anchor invariant, the stage composition invariant, the material agentic participation invariant, the delegated intent invariant, the bounded authority invariant, the contextual interpretation invariant, the action selection invariant, the value-realisation invariant, the AI-not-required invariant, the autonomy-not-required invariant, the automation-not-required invariant, the determinism-exclusion invariant, and the boundary-assertion invariant.

### 2.4 Edge cases

Five edge cases are recognised as compositional arrangements under which the candidate still qualifies:

1. AVS-EDGE-01 Single-stage material agentic participation.
2. AVS-EDGE-02 Cross-stage material agentic participation.
3. AVS-EDGE-03 Multiple agentic participants with separate authorities.
4. AVS-EDGE-04 Agentic participation with co-existing automation.
5. AVS-EDGE-05 Agentic participation with co-existing human discretion.

### 2.5 Boundary preservation

This framework does NOT introduce Agentic Value Stage, Agentic Workflow, Agentic Operations, or Autonomous Value Stream as new constructs. Existing Value Stage remains the stage construct. The qualification framework is bounded to Agentic Value Stream.

## 3. Rationale

The qualification framework formalises what was implicit in ES-ADR-005. The narrative definition identified the irreducible condition (agentic participation with delegated intent, bounded authority, interpretation, action selection) but did not specify how to test it or how to distinguish it from adjacent constructs. Without formal qualification, conformance testing reduces to per-implementation review, which does not scale and is not auditable.

The required values + exclusion conditions + materiality structure mirrors the Open Group Architectural Framework (TOGAF) conformance pattern: necessary conditions, sufficient conditions, and exclusion criteria. The structure is reusable for future qualification frameworks applied to other concepts.

The seven not-required values establish the AI boundary explicitly. AI is implementation technology, not semantic identity. The same pattern (decision-making, agency, autonomy) is preserved for future qualifications.

The seven exclusion conditions establish the boundary against adjacent constructs. Each exclusion is a positive disqualifier, not merely an absence of qualification. This makes the boundary auditable.

The thirteen invariants are the operational hooks for conformance testing. Each invariant maps to one or more required values or exclusion conditions. The conformance kit enforces the invariants through fifteen tests (five positive, five negative, five edge case).

## 4. Consequences

### 4.1 Positive

1. The Agentic Value Stream semantic is now formally testable. A candidate can be evaluated against the qualification test with an unambiguous pass/fail.
2. The semantic boundary against adjacent constructs (deterministic automation, adaptive automation, decision-support AI, human discretion, autonomous systems, dynamic workflows) is established as positive disqualifiers.
3. The conformance kit (5 positive + 5 negative + 5 edge case tests) implements the qualification test mechanically.
4. Future qualification frameworks can reuse the structure (required + not-required + exclusion + materiality + invariants + edge cases).

### 4.2 Negative

1. The qualification framework introduces seven not-required values, which may be interpreted as restrictive if read in isolation. The intent is to clarify that absence does not disqualify and presence alone does not qualify.
2. The qualification framework does not address the question of which Value Stages count as "materially agentic" beyond the three materiality criteria. This is reserved for future operational guidance.

### 4.3 Neutral

1. The framework is bounded to Agentic Value Stream. Other agentic concepts (Agentic Workflow, Agentic Operations, Agentic Value Stage) are not covered and require their own qualification frameworks if and when introduced.

## 5. Implementation

The qualification framework is implemented in the agentic-value-stream repository at `Enterprise-Semantics/agentic-value-stream`. The implementation includes:

- `concept.yaml` ; qualification block with required values, not-required values, exclusion conditions, materiality, invariants, and edge cases.
- `kit/positive-01.yaml` through `kit/positive-05.yaml` ; positive tests asserting each required value group.
- `kit/negative-01.yaml` through `kit/negative-05.yaml` ; negative tests asserting each primary exclusion condition.
- `kit/edge-case-01.yaml` through `kit/edge-case-05.yaml` ; edge case tests asserting compositional arrangements.
- `kit/kit.yaml` ; coverage manifest, auto-derived from the kit/ inventory.
- `docs/concept.md` ; narrative concept description with formal qualification section.
- `docs/conformance.md` ; CI-derived conformance status.
- `visuals/agentic-value-stream/semantic-anatomy.puml` ; PlantUML diagram of the qualification structure.
- `mappings/wsf.yaml` ; WSF mapping with qualification overlay.
- `mappings/opendea.yaml` ; OpenDEA mapping with qualification overlay.

## 6. Validation

The qualification framework is validated by:

1. The conformance kit (5 positive + 5 negative + 5 edge case tests) implements the qualification test mechanically.
2. The semantic anatomy diagram visualises the structure.
3. The WSF and OpenDEA mappings record how the qualification overlays the existing semantic landscape without modifying either metamodel.
4. The framework is reusable: future qualification frameworks applied to other concepts can adopt the same structure.

## 7. Cardinal rules

- Author: Emmanuel A. Otchere (cardinal author rule, 2026-09-23)
- D-004 dash rule: 0 en-dash (U+2013) ; 0 em-dash (U+2014) ; 0 horizontal-ellipsis divider (U+2E3B)
- D-005 prose rule: 0 tripled-semicolon (;;;); preserved only inside backtick code spans (rule documentation)
- D-006 writing rule: coherent prose, no ad-libs or telegraphic phrasing, paragraphs lead into each other, crisp titles, good formatting
- SDO-neutral sourcing: ISO/IEC, ITU-T, ETSI, NIST (no TMForum, no vendor-specific)
- Vendor embargo: 0 references to specific vendors in semantic content
