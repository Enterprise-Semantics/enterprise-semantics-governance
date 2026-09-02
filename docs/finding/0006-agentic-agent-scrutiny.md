<!--
FND-ES-AG-006 ;;; Agentic Agent Scrutiny ;;; dash-normalized
Verbatim original: 00_inbox/FND-ES-AG-006.md.
Status: Proposed Finding (scrutiny).
Working conclusion: Agentic Agent is held back from the canonical seed pending
further investigation, per FND-ES-AG-001-Grounding-Result §3 + §12. Three
plausible models exist ;;; none is chosen. The recommendation is to ground
AI Agent (FND-ES-AG-009) first, then decide whether Agentic Agent is redundant,
a Profile, or a Distinct concept.
-->

# FND-ES-AG-006 ;;; Agentic Agent Semantic Grounding (Scrutiny)

**Status:** Proposed Finding
**Scope:** `Agentic Agent` ;;; scrutiny per FND-ES-AG-001-Grounding-Result §3 + §12.
**Precedes:** Conditional CR-ES-AG-010 (Agentic Agent concept record) ;; ADR-ES-AG-001 §6.
**Depends on:** FND-ES-AG-001 canonical ;;; FND-ES-AG-001-Grounding-Result §3 + §12 ;;; ADR-ES-AG-001 ;;; ADR-ES-002.
**Related:** FND-ES-AG-002 ;; FND-ES-AG-003 ;; FND-ES-AG-004 ;; FND-ES-AG-005 ;; FND-ES-AG-009 (AI Agent).

---

## 1. Finding

The existing Agentic body of work uses `Agentic Agent` as if it is a distinct
concept. It appears in the FND-ES-000 §14 seed concept list and the FND-ES-AG-001
canonical §2 initial Agentic family.

The FND-ES-AG-001-Grounding-Result §3 explicitly warns:

> **Agentic Agent should therefore remain a challenged candidate**, rather
> than automatically entering the canonical seed.

The Grounding Result §3 presents three plausible models for the
Agent/AI Agent/Agentic Agent relationship:

### Model A ;;; Specialization

```text
Agent
  ;
  ▼
AI Agent
  ;
  ▼
Agentic Agent
```

### Model B ;;; Intersection/Profile

```text
         Agent
           ▲
           │
AI ────────┼───────────
           │
       AI Agent
           │
   Agentic characteristic
```

### Model C ;;; Agent as enterprise role/capability bearer

```text
Entity
  ├── Role
  ├── Capability
  └── Agentic disposition
```

The Grounding Result §3 concludes: "We should not choose among these yet."

This Finding applies the 10-step grounding template from the Grounding Result
§13, **treating `Agentic Agent` as a SCRUTINIZED candidate** ;;; not as an
auto-accepted one.

**Working conclusion (provisional, NOT normative):**

`Agentic Agent` is **NOT recommended for canonicalization at this stage**.
The term may turn out to be:

- Redundant with `AI Agent` (per Model A/B).
- A property of `AI Agent` (agentic disposition), not a separate concept.
- A different semantic distinction that we have not yet grounded.

The investigation should continue, but the term should NOT land in the
canonical seed until one of the three models is justified.

The rationale follows.

---

## 2. Problem being addressed

Without scrutiny of `Agentic Agent`:

- The term may silently enter the canonical seed as a redundant concept.
- Downstream systems cannot distinguish `Agentic Agent` from `AI Agent`.
- Mapping to OpenDEA's agent metamodel would require disambiguating which
  agent concept is referenced.
- The semantic graph would carry an ungrounded edge.

---

## 3. 10-step grounding

### 3.1 WSF Parent / Grounding

Per FND-ES-AG-001-Grounding-Result §3, three candidate grounding models exist.
None of them is settled:

- **Model A ;;; Specialization:** Agent -> AI Agent -> Agentic Agent. This
  implies that each level adds properties. But the Grounding Result §3
  warns that `AI Agent` and `Agentic Agent` may be terminologically
  redundant.
- **Model B ;;; Intersection/Profile:** AI and Agent intersect to form
  AI Agent ;;; then Agentic is a characteristic. This implies that
  `Agentic Agent` is not a separate concept but a Profile of `AI Agent`.
- **Model C ;;; Agent as enterprise role/capability bearer:** Agent is
  an enterprise role or capability bearer ;;; not a separate kind. This
  implies `Agentic Agent` is a Profile of Agent as Role/Capability bearer.

No model is canonical. WSF grounding does not yet disambiguate.

### 3.2 Enterprise Semantic Need

The enterprise-specific need depends on which model is chosen:

- If Model A is correct, the need is for a three-level specialization
  (Agent -> AI Agent -> Agentic Agent). This is heavy.
- If Model B is correct, the need is for `Agentic` as a Profile of `AI
  Agent`. This is lighter.
- If Model C is correct, the need is for `Agentic` as a Profile of Agent
  as Role/Capability bearer. This is even lighter.

The Grounding Result §3 explicitly says: "We should not choose among these
yet."

### 3.3 Necessary Distinguishing Characteristics

If `Agentic Agent` were canonical, the necessary distinguishing characteristics
might be:

- Agency (goal-directed behavior).
- Adaptability.
- Decision-making capacity.

But these are precisely the characteristics that the agentic-execution
Profile applies. So the question becomes: is `Agentic Agent` a Concept or a
Profile?

### 3.4 Definition

**No definition recommended at this stage.** The Grounding Result §12 explicitly
flags `Agentic Agent` as the candidate "requiring particular scrutiny" because
it "may be terminologically redundant with AI Agent or represent a different
semantic distinction."

### 3.5 Concept Type

**Undetermined.** Either `ai-agent-profile` (if Model B is correct) or
`role-profile` (if Model C is correct).

### 3.6 Relationships

**Undetermined.** The candidate relationships from FND-ES-000 §14 are:

```text
Agentic Flow
    uses
AI Agent

AI Agent
    uses
AI Model
```

But the `Agentic Agent` slot in these relationships is not grounded.

### 3.7 Boundary Conditions

`Agentic Agent` (if it were canonical) would apply when:

- An Agent (in some model) exhibits agentic characteristics AND is grounded
  in AI.

But without choosing the grounding model, the boundary cannot be defined.

### 3.8 Examples

**Not provided at this stage.** Per the Grounding Result §3, we should not
choose among the three models yet.

### 3.9 Counterexamples

**Not provided at this stage.** Same reason.

### 3.10 Provenance

Evidence for `Agentic Agent` as a separate concept:

- FND-ES-000 §14 includes `Agentic Agent` in the seed concept list.
- FND-ES-AG-001 canonical §2 includes `Agentic Agent` in the initial Agentic
  family.
- Existing Agentic body of work uses the term.

Evidence AGAINST `Agentic Agent` as a separate concept:

- FND-ES-AG-001-Grounding-Result §3 ;;; three plausible models, none chosen.
- FND-ES-AG-001-Grounding-Result §12 ;;; flagged as requiring particular
  scrutiny.
- ADR-ES-002 §5 ;;; enterprise context is not sufficient reason to
  duplicate foundational semantics.

### 3.11 Canonicality Recommendation

```text
CHALLENGED ;;; do NOT proceed to Investigating/Proposed at this stage.
```

Per the Grounding Result §12, the recommendation is:

> **Candidate requiring particular scrutiny:** Agentic Agent ;;; because it
> may be terminologically redundant with AI Agent or represent a different
> semantic distinction.

Therefore the recommendation is:

1. Hold `Agentic Agent` back from CR-ES-AG-010.
2. Author FND-ES-AG-009 (AI Agent semantic grounding) ;;; ground AI Agent
   first.
3. Investigate whether `Agentic Agent` is:
   - Redundant with `AI Agent` (drop the concept).
   - A Profile of `AI Agent` (different from the Profile pattern ;;; agentic
     is a characteristic of an AI agent, not a Profile of the AI agent).
   - A Distinct concept (rare ;;; would need strong justification).

Until that investigation completes, `Agentic Agent` stays **out of the
canonical seed**.

---

## 4. Decision summary

> **`Agentic Agent` is held back from the canonical seed pending further investigation.**
>
> The Grounding Result §3 + §12 flag this concept as requiring particular
> scrutiny. Three plausible models exist ;;; none is chosen.
>
> The recommendation is to:
>
> - Author FND-ES-AG-009 (AI Agent semantic grounding) first.
> - Use that grounding to decide whether `Agentic Agent` is redundant, a
>   Profile, or a Distinct concept.
> - Not land `Agentic Agent` in the canonical seed until that decision
>   is made.
>
> This preserves the ADR-ES-002 §5 principle: "Enterprise context is not
> sufficient reason to duplicate foundational semantics."

---

## 5. Cross-references

- FND-ES-AG-001-Grounding-Result §3 + §12: https://github.com/Enterprise-Semantics/enterprise-semantics-governance/blob/main/docs/finding/0001-agentic-semantic-grounding-grounding-result.md
- FND-ES-AG-001 canonical §2: https://github.com/Enterprise-Semantics/enterprise-semantics-governance/blob/main/docs/finding/0001-agentic-semantic-grounding-canonical.md
- ADR-ES-AG-001 §6: https://github.com/Enterprise-Semantics/enterprise-semantics-governance/blob/main/docs/adr/0003-agentic-semantic-decision.md
- ADR-ES-002 §5: https://github.com/Enterprise-Semantics/enterprise-semantics-governance/blob/main/docs/adr/0002-enterprise-semantic-model.md
- Local verbatim: `/home/hermes/Projects/Enterprise-Semantics/00_inbox/FND-ES-AG-006.md`
