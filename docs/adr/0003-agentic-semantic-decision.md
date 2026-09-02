<!--
ADR-ES-AG-001 ;;; Agentic Semantic Decision

Dash-normalized: colons (:) and semicolons (;) used consistently.
Verbatim original: 00_inbox/ADR-ES-AG-001.md (identical bytes; authored
dash-normalized from the start).

Status: Proposed (awaiting human-owner acceptance).
Authored by: manny-es (the dedicated sub-agent for Enterprise-Semantics).
Date: 2026-09-02.
Depends on: ADR-ES-002 (Enterprise Semantic Model) ;;; FND-ES-AG-001 ;;; FND-ES-AG-002.
Transitive: ADR-ES-001 (organization scaffolding) ;; pending.

Decision: Agentic concepts are Profiles of their base concepts under agent-augmented
execution conditions (profile_type: agentic-execution). Agentic != Autonomous is
established at the Profile-characteristic level, not at the semantic-kind level.

Implementation: CR-ES-AG-001+ (13 CRs).
-->

# ADR-ES-AG-001 ;;; Agentic Semantic Decision

**Status:** Proposed
**Decision Type:** Semantic Architecture / Semantic Governance
**Scope:** Agentic concept family in `Enterprise-Semantics`
**Supersedes:** None
**Depends on:** ADR-ES-002 (Enterprise Semantic Model) ;; FND-ES-AG-001 (Agentic Semantic Grounding) ;; FND-ES-AG-002 (Agentic Value Stream Semantic Grounding) ;; ADR-ES-001 (organization scaffolding) ;; pending
**Related:** FND-ES-000 ;; FND-ES-001 ;; ADR-ES-002 §6, §20, §21, §22

---

## 1. Decision

The Agentic concept family in `Enterprise-Semantics` shall be governed by three architectural commitments:

1. **`Agentic` is a Profile modifier, not a new semantic kind.** Concepts qualified as `Agentic` are Profiles of their base concept under agent-augmented execution conditions.
2. **`Agentic != Autonomous`** is established as a semantic distinction at the Profile-characteristic level, not at the semantic-kind level.
3. **The first implementation family shall be Agentic Value Stream, Agentic Workflow, Agentic Flow, Agentic Operations, Agentic Enterprise, Agentic Capability, AI Agent, Agentic Agent, Agentic Service, Agentic Product, and Agentic Culture**, with their governed relationships defined through CR-ES-AG-001+.

This ADR accepts the Profile hypothesis from FND-ES-AG-002 and extends it to the Agentic concept family. It does not yet promote any specific concept to `Established` ;;; that requires CR-ES-AG-001+ landing the YAML records with appropriate conformance evidence.

The ADR is **`Proposed`** until human-owner acceptance. Implementation CRs (CR-ES-AG-001+) cannot land until this ADR is `Accepted`.

---

## 2. Problem

The Agentic concept family (12 concepts per ADR-ES-002 §20) has been investigated in two Findings:

- **FND-ES-AG-001** established the investigation as the first substantive semantic implementation under ADR-ES-002.
- **FND-ES-AG-002** proposed that `Agentic Value Stream` is a Profile of `Value Stream`, not a Specialization, pure Characteristic, or Distinct kind.

Without an architectural decision:

- Per-concept decisions are made in isolation, with no shared pattern.
- Downstream consumers cannot predict the semantic shape of Agentic concepts.
- Mappings to WSF and OpenDEA cannot be designed coherently.
- The Agentic family risks semantic drift as more concepts are added.

The Agentic family needs an **architectural commitment** that all per-concept decisions can rely on.

---

## 3. Architectural commitment ;;; `Agentic` is a Profile modifier

### 3.1 The Profile semantic construct

A `Profile` in `Enterprise-Semantics` is:

```text
Profile
  subject: a base concept (e.g. Value Stream, Workflow, Operations, Enterprise)
  profile_type: a named profile family (e.g. agentic-execution)
  characteristics: a governed set of properties that apply when the profile is active
  governance: which authority governs the profile (Enterprise-Semantics)
  status: Candidate ;; Investigating ;; Proposed ;; Established ;; Canonical
```

A Profile:

- Does not introduce a new semantic kind. The base concept retains its identity.
- Applies a governed configuration overlay. The characteristics are not free-floating; they are specified in a Profile registry.
- Preserves governed relationships of the base concept. The Profile can add Profile-specific relationships but does not erase base relationships.
- Carries its own lifecycle. The Profile can be promoted through Candidate ;; Established ;; Canonical independently of the base concept.

### 3.2 Why Profile for the Agentic family

Per FND-ES-AG-002 §3.4, the four candidate hypotheses for how `Agentic X` relates to `X` were:

- **A. Specialization** ;; rejected because the Agentic characteristics are characteristics of execution, not of the base concept's semantics.
- **B. Profile** ;; chosen because it preserves identity, applies a configuration overlay, and supports governed relationships and lifecycle.
- **C. Pure Characteristic** ;; rejected because it loses stable identity and governable relationships.
- **D. Distinct kind** ;; rejected because it duplicates the base concept's definition and violates ADR-ES-002 §5.

This ADR applies the Profile hypothesis to the **entire** Agentic family. The reasoning is:

- All four Agentic characteristics in FND-ES-AG-002 §3.3 (bounded autonomy, AI-augmented decision-making, adaptive value-realization, human governance) are **characteristics of execution**, not of the semantics of Value Stream, Workflow, Operations, or Enterprise.
- The same profile characteristics apply across the family ;; the Profile pattern generalizes.
- A Profile pattern is cheaper to govern than per-concept Specialization decisions ;; one decision establishes the pattern.

### 3.3 The profile characteristics

The Agentic profile applies the following characteristics when active:

| Characteristic | Description |
|----------------|-------------|
| Goal-directed execution under bounded autonomy | The entity progresses toward stated outcomes without requiring continuous human routing, within bounds set by governance. |
| AI-augmented decision-making | Decisions about progression, exception handling, and routing are made by AI agents under governed policy. |
| Adaptive behavior | The entity reconfigures its structure or execution in response to feedback and outcome signals. |
| Human governance, not human execution | Humans set intent, policy, and outcome criteria. AI agents execute within those bounds. |

These characteristics apply to:

- `Agentic Value Stream` ;; characteristics apply to the Value Stream's execution.
- `Agentic Workflow` ;; characteristics apply to the Workflow's execution.
- `Agentic Operations` ;; characteristics apply to the Operations' execution.
- `Agentic Enterprise` ;; characteristics apply to the Enterprise's operating model.
- (others as the per-concept findings establish)

### 3.4 Profile relationships

Each `Agentic X` shall carry:

```text
Agentic X
    profile-of X
    profile_type: agentic-execution
    governed-by: Enterprise-Semantics
    status: Candidate ;; Investigating ;; Proposed ;; Established ;; Canonical
```

The base concept (`X`) is unchanged. The Agentic concept is a Profile overlay.

---

## 4. Architectural commitment ;;; `Agentic != Autonomous`

### 4.1 The semantic distinction

Per FND-ES-000 §15, FND-ES-001 §9, and ADR-ES-002 §20, the Agentic and Autonomous families are distinct:

| Property | Agentic | Autonomous |
|----------|---------|------------|
| Bounded autonomy | Yes | Yes (stronger) |
| AI-augmented decision-making | Yes | Yes |
| Adaptive behavior | Yes | Yes (stronger) |
| Human governance | Required | Optional |
| Self-governance | No | Yes |
| Self-adaptation | Limited | Yes |
| Self-execution under policy | Within bounds | Within bounds, broader |
| Human-in-the-loop for novel conditions | Yes | No (system decides) |

The two families occupy **different regions** of the autonomy spectrum:

```text
Human-governed               Self-governed
   ;                              ;
   ;; Agentic Enterprise ;;; Autonomous Enterprise
   ;;                              ;;
   ;                              ;
Manual execution       Fully autonomous execution
```

### 4.2 The Profile-level distinction

The distinction is at the Profile-characteristic level, not at the semantic-kind level. An Autonomous X is a different Profile of X (profile_type: autonomous-operation) with stronger characteristics.

Specifically:

- `Agentic X` has the four Profile characteristics in §3.3 with human governance REQUIRED.
- `Autonomous X` has the same four characteristics with human governance OPTIONAL and self-governance REQUIRED.

The two are Profiles of the same base concept with different profile_type values.

### 4.3 Why not Distinct kinds

Creating `Agentic X` and `Autonomous X` as Distinct semantic kinds would:

- duplicate the base concept definition for each Profile.
- prevent a `Value Stream` from becoming more autonomous over time without changing its semantic identity.
- violate ADR-ES-002 §5.

The Profile pattern handles this naturally ;; the same base concept can carry different Profiles over its lifecycle.

---

## 5. Implementation family

The first implementation family under this ADR consists of 11 concepts, derived from ADR-ES-002 §20 with `Agentic Culture` flagged for separate investigation (per ADR-ES-002 §21 Q10, the most speculative concept in the cluster):

| Concept | Profile of | Status (after CR-ES-AG-001+) |
|---------|------------|------------------------------|
| Agentic Value Stream | Value Stream | Candidate ;; Investigating |
| Agentic Workflow | Workflow | Candidate ;; Investigating |
| Agentic Flow | Activity / Process | Candidate ;; Investigating |
| Agentic Operations | Operations | Candidate ;; Investigating |
| Agentic Enterprise | Enterprise | Candidate ;; Investigating |
| Agentic Capability | Capability | Candidate ;; Investigating |
| AI Agent | WSF Agent | Candidate ;; Investigating |
| Agentic Agent | AI Agent (or WSF Agent) | Candidate ;; Investigating ;; per FND-ES-AG-001+ |
| Agentic Service | Service | Candidate ;; Investigating |
| Agentic Product | Product | Candidate ;; Investigating |
| Agentic AI | AI | Candidate ;; Investigating |

`Agentic Culture` is held back from this implementation family pending a dedicated Finding (FND-ES-AG-NN).

### 5.1 Per-concept findings still required

Each concept in §5 requires its own per-concept Finding (FND-ES-AG-003+) that establishes:

- candidate WSF grounding (per ADR-ES-002 §21 Q12);
- candidate definition;
- candidate relationships (especially the Profile relationship and other governed relationships);
- candidate lifecycle status;
- candidate provenance;
- whether the Profile hypothesis applies cleanly, or whether per-concept adjustments are required.

FND-ES-AG-002 (Agentic Value Stream) has already established the Profile hypothesis for one concept. The remaining concepts follow the same pattern unless a Finding-supported deviation is justified.

### 5.2 Relationship governance

The candidate relationships from FND-ES-AG-001 §4 Q14 and FND-ES-AG-002 §6 form the initial relationship vocabulary:

```text
profile-of        ;; an Agentic concept is a Profile of its base
realizes          ;; an Agentic concept realizes a value-bearing outcome
enabled-by        ;; an Agentic concept is enabled by a Capability
supported-by      ;; an Agentic concept is supported by a Process
executes-through  ;; an Agentic Value Stream executes through an Agentic Workflow
orchestrates      ;; an Agentic Workflow orchestrates an Agentic Flow
uses              ;; an Agentic Flow uses an AI Agent
```

Each relationship is `provisional` until CR-ES-AG-001+ lands the YAML record and the conformance harness validates it.

---

## 6. Implementation sequence ;;; CR-ES-AG-001+

The implementation is sequenced as CRs, not as a single CR:

### CR-ES-AG-001 ;;; Profile semantic construct

Establishes the Profile registry and Profile YAML schema in `enterprise-semantics`. Profile characteristics are first-class semantic objects with their own identity, governance, and lifecycle.

### CR-ES-AG-002 ;;; Agentic profile_type

Registers the `agentic-execution` profile_type in the Profile registry. Establishes the four Profile characteristics from §3.3 as governed semantic objects.

### CR-ES-AG-003 ;;; Agentic Value Stream

Lands the `Agentic Value Stream` Candidate-status YAML record in `enterprise-semantics`, with:

- profile-of Value Stream
- realizes Value Outcome
- enabled-by Capability
- supported-by Process
- executes-through Agentic Workflow

Per FND-ES-AG-002.

### CR-ES-AG-004 ;;; Agentic Workflow

Lands the `Agentic Workflow` Candidate-status YAML record. Per FND-ES-AG-003 (pending).

### CR-ES-AG-005 ;; through ;; CR-ES-AG-011

One CR per remaining concept in §5. Each lands a Candidate-status YAML record.

### CR-ES-AG-012 ;;; Conformance gate ;;; Profile validation

Adds Profile-specific conformance checks to the harness:

- Profile relationship has valid profile_type.
- Profile characteristics are all governed.
- Profile lifecycle status is valid.
- Profile relationships do not duplicate base relationships.

### CR-ES-AG-013 ;;; First semantic release

Tags the first Agentic semantic release (`v0.1.0-agentic-seed`) after CRs 1-12 land and conformance is green.

Each CR lands in sequence and must pass conformance before the next. Skipping ahead is not allowed.

---

## 7. Architectural constraint ;; Value Stream != Process != Workflow != Task Flow

Per ADR-ES-002 §22 and FND-ES-AG-002 §6.1, this ADR reaffirms:

- `Value Stream`, `Process`, `Workflow`, and `Task Flow` are distinct semantic kinds.
- An `Agentic Value Stream` does not `contain` an `Agentic Workflow` ;;; it `executes-through` it.
- An `Agentic Workflow` does not `contain` an `Agentic Flow` ;;; it `orchestrates` it.
- An `Agentic Flow` does not `contain` an `AI Agent` ;;; it `uses` it.

These architectural constraints carry into the CR-ES-AG-001+ implementation. The conformance gate validates them.

---

## 8. Architectural constraint ;; Agentic vs Autonomous ;§

Per §4:

- `Agentic X` and `Autonomous X` are Profiles of the same base concept `X` with different profile_type values.
- They are not Distinct kinds.
- They can co-exist on the same base concept (a Value Stream can carry both Agentic and Autonomous Profiles at different lifecycle stages).

---

## 9. Acceptance criteria

This ADR is `Accepted` (promoted from `Proposed`) when:

1. Human owner (or delegated authority) explicitly approves.
2. At least the Profile hypothesis (FND-ES-AG-002) is reviewed and accepted.
3. The CR-ES-AG-001+ sequence is approved.

Until `Accepted`, CR-ES-AG-001+ cannot land.

---

## 10. Consequences

### Positive

- Architectural consistency: all Agentic concepts follow the Profile pattern.
- Reduces per-concept decision overhead: the Profile hypothesis generalizes.
- Enables governed relationship evolution: relationships are governed semantic objects.
- Supports bi-directional integration: Profile relationships can map cleanly to WSF and OpenDEA.
- Preserves the Agentic != Autonomous distinction without semantic duplication.
- Agentic Value Stream, Agentic Workflow, Agentic Operations, Agentic Enterprise, etc. can carry the same Profile pattern ;; consistent semantic shape across the family.

### Negative

- Profile semantic construct adds governance complexity (Profile registry, profile_type registry, characteristic registry).
- Per-concept findings (FND-ES-AG-003+) still required for WSF grounding, definition, relationships.
- Conformance gate must validate Profile-specific semantics.
- Cultural change ;;; diagrams showing `Agentic X` as a box now need to be re-expressed as a Profile of `X`.

These costs are intentional. Per ADR-ES-002 §24: "semantic authority without governance would rapidly become another uncontrolled vocabulary."

---

## 11. Decision summary

> **The Agentic concept family in `Enterprise-Semantics` is governed by the Profile semantic construct.**
>
> `Agentic` is a Profile modifier, not a new semantic kind. `Agentic X` is a Profile of `X` under agent-augmented execution conditions.
>
> `Agentic != Autonomous` is established at the Profile-characteristic level, not at the semantic-kind level. Both are Profiles of the same base concept with different profile_type values.
>
> The first implementation family consists of 11 concepts (Agentic Value Stream, Agentic Workflow, Agentic Flow, Agentic Operations, Agentic Enterprise, Agentic Capability, AI Agent, Agentic Agent, Agentic Service, Agentic Product, Agentic AI), with Agentic Culture held back for separate investigation.
>
> Implementation is sequenced as CR-ES-AG-001+ (13 CRs) with conformance validation between each.
>
> The ADR is `Proposed` until human-owner acceptance. CR-ES-AG-001+ cannot land until `Accepted`.

---

## 12. Cross-references

- FND-ES-AG-001 (Agentic Semantic Grounding): https://github.com/Enterprise-Semantics/enterprise-semantics-governance/blob/main/docs/finding/0001-agentic-semantic-grounding.md
- FND-ES-AG-002 (Agentic Value Stream Semantic Grounding): https://github.com/Enterprise-Semantics/enterprise-semantics-governance/blob/main/docs/finding/0002-agentic-value-stream-semantic-grounding.md
- ADR-ES-002 (depends on): https://github.com/Enterprise-Semantics/enterprise-semantics-governance/blob/main/docs/adr/0002-enterprise-semantic-model.md
- ADR-ES-001 (organization scaffolding, pending): surfaces on every `manny-es` check-in until resolved.
- Local verbatim: `/home/hermes/Projects/Enterprise-Semantics/00_inbox/ADR-ES-AG-001.md`
- Local dash-normalized: `/home/hermes/Projects/Enterprise-Semantics/seed/ADR-ES-norm-AG-001.md`