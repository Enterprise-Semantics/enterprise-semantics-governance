<!--
FND-ES-AG-005 ;;; Agentic Enterprise Semantic Grounding ;;; dash-normalized
Verbatim original: 00_inbox/FND-ES-AG-005.md.
Status: Proposed Finding. Precedes: CR-ES-AG-007.
Working conclusion: Agentic Enterprise is a Profile of Enterprise under agent-
augmented operating-model conditions.
-->

# FND-ES-AG-005 ;;; Agentic Enterprise Semantic Grounding

**Status:** Proposed Finding
**Scope:** `Agentic Enterprise` (and its relationship to `Enterprise`)
**Precedes:** CR-ES-AG-007 (Agentic Enterprise concept record) ;; ADR-ES-AG-001 §6.
**Depends on:** FND-ES-AG-001 canonical ;;; FND-ES-AG-001-Grounding-Result ;;; ADR-ES-AG-001 ;;; ADR-ES-002.
**Related:** FND-ES-AG-002 ;; FND-ES-AG-003 ;; FND-ES-AG-004.

---

## 1. Finding

The existing Agentic body of work uses `Agentic Enterprise` as an enterprise-
level specialization. It appears in the FND-ES-000 §15 candidate relationships:

```text
Agentic Enterprise
    operates-through
        Agentic Operations
```

The Grounding Result §8 identifies `Agentic Enterprise` as one of the four
strongest candidates. The Grounding Result also warns that `Agentic Enterprise`
must NOT be defined merely as "an enterprise using AI agents" ;;; that would
collapse important semantic distinctions.

This Finding applies the 10-step grounding template from the Grounding Result
§13 to `Agentic Enterprise`.

**Working conclusion (provisional, NOT normative):**

`Agentic Enterprise` is a Profile of `Enterprise` under agent-augmented
operating-model conditions. Per ADR-ES-AG-001 §3, the agentic-execution Profile
applies the four governed characteristics. The Profile binding is to
`Enterprise` (not to `Operating Model` directly ;;; the binding reaches the
operating-model via the Enterprise binding).

The rationale follows in the 10-step structure.

---

## 2. Problem being addressed

Without semantic grounding of `Agentic Enterprise`:

- The term collapses to a vague "uses AI" ;;; this prevents precise
  specification of what makes an Enterprise Agentic.
- Downstream systems cannot stably reference `Agentic Enterprise`.
- The boundary between `Agentic Enterprise`, `Digital Enterprise`, `AI-Native
  Enterprise`, and `Autonomous Enterprise` cannot be enforced.
- Mapping to OpenDEA's enterprise metamodel loses meaning.

---

## 3. 10-step grounding

### 3.1 WSF Parent / Grounding

Per FND-ES-AG-001-Grounding-Result §8, `Agentic Enterprise` is grounded in:

```text
WSF Entity
   ;
   (via enterprise specialization)
   ;
Enterprise
   ;
   (via Profile binding)
   ;
Agentic Enterprise
```

Specifically:

- `Enterprise` ;;; WSF grounding via WSF `Entity` (Disposition + Capability).
  An Enterprise is a complex Entity that operates to realize value.
- `Agentic Enterprise` ;;; inherits via Profile.

### 3.2 Enterprise Semantic Need

The enterprise-specific semantic need is to capture enterprises that exhibit
agentic characteristics across their operating model. The Grounding Result §8
identifies these as enterprise-level phenomena spanning:

```text
Enterprise
├── Strategy
├── Governance
├── Capability
├── Value Creation
├── Operations
├── Decision
├── Work
└── Culture
```

An Agentic Enterprise exhibits agentic characteristics across **all** of these
areas, not just one. That is the distinguishing feature.

### 3.3 Necessary Distinguishing Characteristics

A Profile of `Enterprise` under agent-augmented operating-model conditions
exhibits the four governed characteristics from ADR-ES-AG-001 §3.3, applied
across the eight enterprise areas from §3.2:

1. **Goal-directed execution under bounded autonomy** ;;; at the enterprise
   level, this means the enterprise pursues stated outcomes without requiring
   continuous human-driven routing across its strategy, governance, capability,
   value creation, operations, decision, work, and culture dimensions.
2. **AI-augmented decision-making** ;;; at the enterprise level, decisions
   across all eight dimensions are made by AI agents under governed policy.
3. **Adaptive behavior** ;;; at the enterprise level, the enterprise
   reconfigures its operating model in response to feedback and outcome signals.
4. **Human governance, not human execution** ;;; at the enterprise level,
   humans set intent, policy, and outcome criteria. AI agents execute within
   those bounds across all eight dimensions.

### 3.4 Definition

Per ADR-ES-002 §7, the candidate definition for `Agentic Enterprise`:

> An Agentic Enterprise is an Enterprise whose operating model systematically
> incorporates agent-augmented decision-making, adaptive operating configuration,
> goal-directed execution under bounded autonomy, and human governance rather
> than human execution ;;; across its strategy, governance, capability, value
> creation, operations, decision, work, and culture.

This definition is provisional and subject to revision.

### 3.5 Concept Type

`enterprise-profile` ;;; a Profile of `Enterprise` that operates at the
enterprise level rather than the operating-model or activity level.

### 3.6 Relationships

| Subject | Predicate | Object | Status | Provenance | Inverse |
|---------|-----------|--------|--------|------------|---------|
| Agentic Enterprise | profile-of | Enterprise | provisional | FND-ES-AG-005 §3.4 | has-profile |
| Agentic Enterprise | operates-through | Agentic Operations | provisional | FND-ES-000 §15 ;; FND-ES-AG-004 §3.6 | operated-by |
| Agentic Enterprise | exhibits | Agentic Culture | provisional | FND-ES-AG-001 §12 ;; FND-ES-001 §9 | exhibited-by |
| Agentic Enterprise | realizes | Agentic Value Stream(s) | provisional | FND-ES-000 §15 | realized-by |

### 3.7 Boundary Conditions

`Agentic Enterprise` applies when:

- The Enterprise exhibits the four Profile characteristics across the eight
  enterprise areas (or substantially all of them).
- The Enterprise's Operating Model is anchored in agent-augmented execution.
- The Enterprise demonstrates human governance (not self-governance).

`Agentic Enterprise` does NOT apply when:

- The Enterprise merely deploys AI agents ;;; ad-hoc AI usage is not Agentic
  Enterprise.
- The Enterprise exhibits self-governance across all areas ;;; this is
  `Autonomous Enterprise`.
- The Enterprise uses AI in only one or two areas ;;; partial adoption is
  not the full Profile.

### 3.8 Examples

- An Enterprise whose Strategy, Governance, Capability, Value Creation,
  Operations, Decision, Work, and Culture all systematically incorporate
  AI agents under human-set policy ;;; the Enterprise exhibits Agentic
  Enterprise characteristics across all eight areas.

### 3.9 Counterexamples

- An Enterprise that deploys AI agents in Customer Service only ;;; this is
  partial adoption, not the full Profile.
- An Enterprise where AI agents make all strategic decisions without human
  oversight ;;; this is Autonomous Enterprise.
- An Enterprise that has fully automated a single process ;;; this is
  Digital Operations, not Agentic Enterprise.

### 3.10 Provenance

Evidence supporting the Profile hypothesis:

- FND-ES-AG-001-Grounding-Result §8 ;;; identifies Agentic Enterprise as a
  legitimate enterprise specialization candidate.
- FND-ES-000 §15 ;;; candidate relationship chain.
- FND-ES-001 §14 ;;; existing Agentic body of work uses the term consistently.

Evidence does NOT support:

- Defining Agentic Enterprise as "Enterprise using AI agents" (too vague ;;;
  per Grounding Result §8).
- Creating Agentic Enterprise as a Distinct kind (per ADR-ES-002 §5).

### 3.11 Canonicality Recommendation

```text
Candidate (current)
    ↓ Investigating ;;; landing with this Finding
Proposed ;;; consolidated Agentic semantic review accepts the Profile hypothesis
    ↓
Established ;;; CR-ES-AG-007 lands the concept record
Canonical ;;; post-release
```

Per ADR-ES-AG-001 §9, promotion to `Established` requires CR-ES-AG-007.

---

## 4. Decision summary

> **`Agentic Enterprise` is, on the evidence available to this Finding, a Profile of `Enterprise` under agent-augmented operating-model conditions.**
>
> The Profile pattern follows ADR-ES-AG-001 §3. The Profile binding is to
> `Enterprise` (not directly to `Operating Model`). The Profile characteristics
> are applied across the eight enterprise areas (Strategy, Governance,
> Capability, Value Creation, Operations, Decision, Work, Culture).
>
> The boundary conditions distinguish `Agentic Enterprise` from `Digital
> Enterprise`, `AI-Native Enterprise`, and `Autonomous Enterprise`.
>
> The Finding does not, by itself, establish `Agentic Enterprise` as canonical.
> Promotion to `Proposed` requires the consolidated Agentic semantic review.
> Promotion to `Established` requires CR-ES-AG-007.

---

## 5. Cross-references

- FND-ES-AG-001 canonical: https://github.com/Enterprise-Semantics/enterprise-semantics-governance/blob/main/docs/finding/0001-agentic-semantic-grounding-canonical.md
- FND-ES-AG-001-Grounding-Result: https://github.com/Enterprise-Semantics/enterprise-semantics-governance/blob/main/docs/finding/0001-agentic-semantic-grounding-grounding-result.md
- ADR-ES-AG-001: https://github.com/Enterprise-Semantics/enterprise-semantics-governance/blob/main/docs/adr/0003-agentic-semantic-decision.md
- ADR-ES-002: https://github.com/Enterprise-Semantics/enterprise-semantics-governance/blob/main/docs/adr/0002-enterprise-semantic-model.md
- FND-ES-AG-004 (sibling): https://github.com/Enterprise-Semantics/enterprise-semantics-governance/blob/main/docs/finding/0004-agentic-operations-semantic-grounding.md
- Local verbatim: `/home/hermes/Projects/Enterprise-Semantics/00_inbox/FND-ES-AG-005.md`
