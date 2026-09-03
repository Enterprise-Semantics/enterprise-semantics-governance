<!--
FND-ES-AG-007 ;;; AI Agent Semantic Grounding ;;; dash-normalized
Verbatim original: 00_inbox/FND-ES-AG-007.md.
Status: Proposed Finding. Precedes: CR-ES-AG-009.
Working conclusion: AI Agent is a Distinct semantic kind ;; not a Profile.
Grounds via WSF Entity + WSF Capability. Gating prerequisite for
FND-ES-AG-006 (Agentic Agent scrutiny).
-->

# FND-ES-AG-007 ;;; AI Agent Semantic Grounding

**Status:** Proposed Finding
**Scope:** `AI Agent` (and its relationship to `Agent`, `Agentic Agent`, `Capability bearer`)
**Precedes:** CR-ES-AG-009 (AI Agent concept record) ;; ADR-ES-AG-001 §6.
**Depends on:** FND-ES-AG-001 canonical ;;; FND-ES-AG-001-Grounding-Result ;;; ADR-ES-AG-001 ;;; ADR-ES-002.
**Related:** FND-ES-AG-002 ;; FND-ES-AG-003 ;; FND-ES-AG-004 ;; FND-ES-AG-005 ;; FND-ES-AG-006 (scrutiny of `Agentic Agent`).

---

## 1. Finding

The existing Agentic body of work uses `AI Agent` as if it is a distinct concept. It appears in the FND-ES-000 §14 seed concept list, FND-ES-AG-001 §2 initial Agentic family, and the FND-ES-AG-001-Grounding-Result §3 (one of three plausible models for the `Agent / AI Agent / Agentic Agent` relationship).

The FND-ES-AG-001-Grounding-Result §3 + §12 explicitly identifies `AI Agent` as a **strong candidate** for grounded enterprise semantics ;; distinct from `Agentic Agent`, which is the **scrutinized candidate** per FND-ES-AG-006.

This Finding applies the 10-step grounding template from the Grounding Result §13 to `AI Agent`, **before** any decision on whether `Agentic Agent` should be canonicalized.

**Working conclusion (provisional, NOT normative):**

`AI Agent` is **recommended for canonicalization as a Distinct semantic kind** ;; not a Profile, not a specialization, but a foundational enterprise concept that specializes WSF `Agent` (in the AI-bearing sense). The `AI Agent` kind provides the **grounding target** that any future decision on `Agentic Agent` (Profile vs redundant vs Distinct, per FND-ES-AG-006) must reference.

The rationale follows in the 10-step structure.

---

## 2. Problem being addressed

Without semantic grounding of `AI Agent`:

- The `Agent` / `AI Agent` / `Agentic Agent` relationship (per FND-ES-AG-006 §3) cannot be settled ;; we cannot decide whether `Agentic Agent` is redundant or distinct without first grounding `AI Agent`.
- Downstream systems cannot stably reference `AI Agent` as a semantic object.
- The Profile of Profile pattern (e.g. `Agentic Capability` -> `Capability` -> `AI Agent` bearer) cannot be expressed.
- Mapping to OpenDEA's agent metamodel loses meaning.

---

## 3. 10-step grounding

### 3.1 WSF Parent / Grounding

Per FND-ES-AG-001-Grounding-Result §3, the strongest grounding for `AI Agent` is via WSF `Agent` (which carries AI-bearing capability) ;; or, if WSF does not yet have an `Agent` concept, via WSF `Entity` with a Capability bearer specialization.

The Grounding Result §3 notes that WSF may need to add `Agent` as a foundational concept if not present. This Finding assumes the worst case (WSF lacks `Agent`) and grounds `AI Agent` directly in WSF `Entity` + WSF `Capability`.

```text
WSF Entity (Tier 1)
  ; (via AI-bearing capability specialization)
  ;
WSF Capability (Tier 2)
  ; (via bearer specialization)
  ;
AI Agent
```

If WSF adds `Agent` later (per the Grounding Result §3 recommendation), the grounding can be tightened ;; but the foundational grounding via `Entity` + `Capability` is sound in the meantime.

### 3.2 Enterprise Semantic Need

The enterprise-specific semantic need for `AI Agent` is to capture **AI-bearing agents** ;; software entities that exhibit intelligence, decision-making capacity, and goal-directed behavior, while operating under governance.

This need is not adequately captured by:

- WSF `Entity` alone ;; too generic (covers any entity, not AI-bearing agents).
- WSF `Capability` alone ;; covers capability, not the bearer.
- WSF `Role` alone ;; relational, not the AI-bearing aspect.

Therefore `AI Agent` is justified as a foundational ES concept that combines:

- An Entity (the AI system itself).
- A Capability bearer (the AI system bears capabilities).
- An implicit Decision capacity (decisions are made under governed policy).

### 3.3 Necessary Distinguishing Characteristics

A canonical `AI Agent` exhibits these characteristics:

1. **AI-bearing** ;; the agent's decision-making is grounded in AI (machine learning, foundation models, or other AI techniques). Non-AI agents (e.g. human agents, deterministic automation) are NOT `AI Agent`.
2. **Goal-directed** ;; the agent pursues stated outcomes (not just reactive).
3. **Capability bearer** ;; the agent bears capabilities that can be invoked, observed, and governed.
4. **Decision-making capacity** ;; the agent makes decisions (with varying degrees of autonomy) under governed policy.
5. **Observable** ;; the agent's behavior produces evidence (events, observations, decisions) that can be recorded and audited.

These characteristics distinguish `AI Agent` from:

- `Agent` (the generic Agent concept, not necessarily AI-bearing).
- `Human Agent` (a human in an agent role, no AI grounding).
- `Autonomous System` (broader autonomy, may not be AI-bearing).
- `Workflow` (a sequence of activities, not a single AI-bearing entity).

### 3.4 Definition

Per ADR-ES-002 §7, the candidate definition for `AI Agent`:

> An AI Agent is an Entity that bears AI-grounded capabilities, exhibits goal-directed behavior under governed policy, makes decisions under varying degrees of autonomy, and produces observable evidence of its operation ;; all within an enterprise semantic context.

This definition is provisional and subject to revision.

### 3.5 Concept Type

`ai-agent` ;; a Distinct semantic kind. Not a Profile. Not a specialization of `Agent` (which we treat as distinct). Grounded via WSF `Entity` + WSF `Capability`.

### 3.6 Relationships

| Subject | Predicate | Object | Status | Provenance | Inverse |
|---------|-----------|--------|--------|------------|---------|
| AI Agent | specializes | WSF Entity | provisional | FND-ES-AG-007 §3.1 | specialized-by |
| AI Agent | bears | WSF Capability | provisional | FND-ES-AG-007 §3.2 | borne-by |
| AI Agent | produces | WSF Event | provisional | FND-ES-AG-007 §3.3 #5 | produced-by |
| AI Agent | makes | Decision (under governed policy) | provisional | FND-ES-AG-007 §3.3 #4 | made-by |
| AI Agent | distinct-from | Human Agent | proposed | FND-ES-AG-007 §3.3 | (symmetric) |
| AI Agent | grounding-target-for | Agentic Agent (if canonicalized) | provisional | FND-ES-AG-006 §3 | (depends on FND-ES-AG-006 outcome) |
| AI Agent | used-by | Agentic Workflow | provisional | FND-ES-AG-001 §3 | uses |
| AI Agent | used-by | Agentic Value Stream | provisional | FND-ES-AG-001 §3 | uses |

### 3.7 Boundary Conditions

`AI Agent` applies when:

- The agent's decision-making is AI-grounded (machine learning, foundation models, or other AI techniques).
- The agent is an Entity that bears Capabilities.
- The agent's behavior produces observable evidence.

`AI Agent` does NOT apply when:

- The agent is a human in an agent role (`Human Agent`).
- The agent's decision-making is deterministic with no AI grounding (`Automation`, `Script`).
- The agent is a software entity that bears no AI-grounded capabilities (`Software Component`).
- The agent is a sequence of activities (`Workflow`, `Process`).

### 3.8 Examples

- An LLM-powered assistant that takes user requests, plans actions, invokes tools, and returns results ;; the assistant is an `AI Agent`.
- A reinforcement learning system that plays a game, learns from outcomes, and improves its policy ;; the RL system is an `AI Agent`.
- A foundation model that is invoked per-request but does not bear persistent capabilities ;; this is `Model`, not `AI Agent` (the model is a Capability bearer of `AI Agent`, not itself an `AI Agent`).

### 3.9 Counterexamples

- A human customer service representative ;; this is `Human Agent`, not `AI Agent`.
- A cron job that runs on a schedule and calls a fixed API ;; this is `Automation`, not `AI Agent`.
- A database stored procedure ;; this is `Software Component`, not `AI Agent`.
- An ML model artifact (e.g. weights, config) sitting in a model registry ;; this is `Model`, not `AI Agent` (the model becomes an `AI Agent` only when wrapped in a bearer that exhibits the §3.3 characteristics).

### 3.10 Provenance

Evidence supporting `AI Agent` as a Distinct kind:

- FND-ES-AG-001-Grounding-Result §3 ;; one of three plausible models treats `AI Agent` as a specialization of `Agent`. Even in the other two models, `AI Agent` has its own semantic role.
- FND-ES-AG-001-Grounding-Result §12 ;; `AI Agent` is identified as a strong candidate, distinct from `Agentic Agent` which is scrutinized.
- FND-ES-000 §14 ;; included in the seed concept list.
- FND-ES-AG-001 canonical §2 ;; included in the initial Agentic family.
- ADR-ES-AG-001 §6 ;; CR-ES-AG-009 (AI Agent concept record) is in the implementation sequence.

Evidence does NOT support:

- Treating `AI Agent` as redundant with `Agent` (per the Grounding Result §3 warning against premature redundancy).
- Treating `AI Agent` as a Profile (it is foundational, not a configuration overlay).
- Treating `AI Agent` as identical to `Agentic Agent` (per FND-ES-AG-006, `Agentic Agent` is the scrutinized candidate, not `AI Agent`).

### 3.11 Canonicality Recommendation

```text
Candidate (current)
    ↓ Investigating ;;; landing with this Finding
Proposed ;;; consolidated Agentic semantic review accepts the Distinct kind hypothesis
    ↓
Established ;;; CR-ES-AG-009 lands the concept record with conformance evidence
Canonical ;;; post-release
```

Per ADR-ES-AG-001 §9, promotion to `Established` requires CR-ES-AG-009.

---

## 4. Decision summary

> **`AI Agent` is, on the evidence available to this Finding, recommended for canonicalization as a Distinct semantic kind in `Enterprise-Semantics`.**
>
> `AI Agent` grounds via WSF `Entity` + WSF `Capability` (with a recommended WSF `Agent` addition if WSF chooses). It is foundational, not a Profile. It is distinct from `Human Agent`, `Agentic Agent`, and other adjacent concepts.
>
> This Finding is the **gating prerequisite** for any future decision on `Agentic Agent` (per FND-ES-AG-006). The three plausible models in FND-ES-AG-006 §3 cannot be evaluated until `AI Agent` is grounded.
>
> Promotion to `Proposed` requires the consolidated Agentic semantic review. Promotion to `Established` requires CR-ES-AG-009.

---

## 5. Cross-references

- FND-ES-AG-001 canonical: `docs/finding/0001-agentic-semantic-grounding-canonical.md`
- FND-ES-AG-001-Grounding-Result: `docs/finding/0001-agentic-semantic-grounding-grounding-result.md`
- FND-ES-AG-006 (sibling scrutiny): `docs/finding/0006-agentic-agent-scrutiny.md`
- ADR-ES-AG-001 §6: `docs/adr/0003-agentic-semantic-decision.md`
- ADR-ES-002 §7: `docs/adr/0002-enterprise-semantic-model.md`
- Local verbatim: `/home/hermes/Projects/Enterprise-Semantics/00_inbox/FND-ES-AG-007.md`
