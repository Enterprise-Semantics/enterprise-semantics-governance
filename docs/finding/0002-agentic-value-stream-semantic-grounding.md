<!--
FND-ES-AG-002 ;;; Agentic Value Stream Semantic Grounding

Dash-normalized: colons (:) and semicolons (;) used consistently.
Verbatim original: 00_inbox/FND-ES-AG-002.md (identical bytes; authored
dash-normalized from the start).

Status: Proposed Finding
Authored by: manny-es (the dedicated sub-agent for Enterprise-Semantics)
Date: 2026-09-02
Preceded by: FND-ES-AG-001 (Agentic Semantic Grounding).
Depends on: ADR-ES-002 ;;; ADR-ES-001 pending.

Working conclusion (provisional, NOT normative):
Agentic Value Stream is a Profile of Value Stream, not a Specialization,
a pure Characteristic, or a Distinct kind.
-->

# FND-ES-AG-002 ;;; Agentic Value Stream Semantic Grounding

**Status:** Proposed Finding
**Scope:** `Agentic Value Stream` (and its relationship to `Value Stream`)
**Precedes:** FND-ES-AG-001+ (consolidated Agentic semantic review) ;; ADR-ES-AG-001 ;; CR-ES-AG-001+ ;; enterprise-semantics seed
**Depends on:** FND-ES-AG-001 (Agentic Semantic Grounding) ;; ADR-ES-002 (Enterprise Semantic Model) §22 ;; ADR-ES-001 (organization scaffolding) pending
**Related:** FND-ES-000 §15 ;; FND-ES-001 §9

---

## 1. Finding

The existing body of agentic enterprise work uses the term `Agentic Value Stream` as if it has a settled meaning. It appears in diagrams, in the Agentic Value Stream investigation, and in the FND-ES-000 seed concept list under the candidate relationships:

```text
Agentic Value Stream
    realizes
        Value Outcome
    enabled-by
        Capability
    supported-by
        Process
    executes-through
        Agentic Workflow
```

The semantic relationship between `Agentic Value Stream` and `Value Stream` has not been formally established.

Per ADR-ES-002 §22:

> "Whether it is a specialization/profile or a distinct concept must be determined through the Finding/ADR process."

This Finding investigates that question and proposes a candidate answer.

**Working conclusion (provisional, NOT normative):**

`Agentic Value Stream` is a **profile** of `Value Stream` under bounded-autonomy, AI-augmented execution conditions. It is not a distinct semantic kind and not a free-standing ontological class.

The rationale follows.

---

## 2. Problem being addressed

Without semantic grounding of `Agentic Value Stream`:

- Diagrams that show `Agentic Value Stream` as a node carry no semantic authority.
- Downstream systems cannot stably reference it.
- The architectural distinction between Value Stream, Process, Workflow, and Task Flow (per ADR-ES-002 §22) cannot be enforced when `Agentic Value Stream` is used loosely.
- Whether `Agentic Value Stream` is a generic specialization (which could apply to any value stream augmented with AI) or a specific kind (which would require a separate definition) remains undecided.
- Whether `Agentic Value Stream` should contain `Process`, `Workflow`, or `Agentic Workflow` is not constrained by anything but diagram convention.

---

## 3. Investigation methodology

The investigation follows the questions in ADR-ES-002 §21, narrowed to one concept:

### 3.1 What is `Value Stream`?

A `Value Stream` is the end-to-end progression of value-realization steps that delivers an outcome of value to a stakeholder. It is a semantic concept distinct from `Process`, `Workflow`, and `Task Flow`:

| Concept | Unit of analysis | Decomposition |
|---------|------------------|---------------|
| Value Stream | End-to-end value realization | Stages, Segments |
| Process | Recurring organizational capability | Activities |
| Workflow | Specific execution choreography | Steps |
| Task Flow | Individual task execution | Actions |

The distinctions matter because a `Value Stream` is **about value**, not about work decomposition. A `Value Stream` may be supported by multiple `Processes`, executed through `Workflows`, and operationalized through `Task Flows`. Each of these is a different semantic kind.

### 3.2 What is `Agentic`?

Per FND-ES-AG-001 §5, the working hypothesis is:

> `Agentic` is a characteristic of an entity, indicating capacity for goal-directed action with bounded autonomy under AI-augmented execution.

It is not, on this hypothesis, a semantic kind in its own right. It is a **modifier** that qualifies an existing semantic kind (Capability, Workflow, Operations, Enterprise, Value Stream).

### 3.3 What makes a Value Stream Agentic?

A Value Stream is Agentic when it exhibits, across its stages:

1. **Goal-directed execution under bounded autonomy.** The Value Stream progresses toward a stated value outcome without requiring continuous human-driven routing.
2. **AI-augmented decision-making.** Decisions about progression, exception handling, and routing are made by AI agents under governed policy.
3. **Adaptive value-realization.** The Value Stream can reconfigure its stages in response to changing conditions, feedback, and outcome signals.
4. **Human governance, not human execution.** Humans set intent, policy, and outcome criteria. AI agents execute within those bounds.

Each property is a **characteristic** of the Value Stream, not a separate class of Value Stream.

### 3.4 The four candidate answers to "what kind of concept is Agentic Value Stream?"

| Hypothesis | Description | Implications |
|------------|-------------|--------------|
| **A. Specialization** | `Agentic Value Stream` is a strict subclass of `Value Stream`. | Inherits all properties; agentic-specific properties are differentiating constraints. |
| **B. Profile** | `Agentic Value Stream` is a Value Stream with the agentic profile characteristics applied. | Same identity as Value Stream, but with a configuration overlay. |
| **C. Characteristic** | `Agentic Value Stream` is a Value Stream that happens to have agentic characteristics. | No new concept; just an observation about a Value Stream. |
| **D. Distinct kind** | `Agentic Value Stream` is its own ontological class, separate from Value Stream. | Requires its own definition, relationships, lifecycle. |

**Chosen hypothesis: B ;;; Profile.**

Rationale:

- A `Profile` is the right semantic tool when a concept has the same identity as its base, but applies a configuration overlay that constrains how it relates to other concepts.
- A `Specialization` (A) would imply a strict subclass with non-shared properties. The four agentic characteristics in §3.3 are not non-shared ;;; a Value Stream without those characteristics is still a Value Stream.
- A `Characteristic` (C) would reduce `Agentic Value Stream` to an observation ;;; useful for description but not for governance. Governance requires `Agentic Value Stream` to be referenceable as an entity.
- A `Distinct kind` (D) would create semantic duplication and would violate the WSF grounding principle in ADR-ES-002 §5.

### 3.5 Why not Specialization?

A `Specialization` is appropriate when:

- The subclass has additional properties that the superclass does not have.
- The subclass is a different semantic kind that requires its own definition.

For `Agentic Value Stream`, neither is true:

- It does not have **additional properties** beyond a Value Stream ;;; the agentic characteristics are characteristics of execution, not of the value-realization semantics.
- It is not a **different semantic kind** ;;; it still realizes Value Outcomes; it still has Stages; it is still a Value Stream.

A Profile is the lighter-weight tool that captures the constraint without forcing a new ontological class.

### 3.6 Why not Distinct kind?

Creating a distinct kind would:

- require a separate definition, separate lifecycle, separate identity, separate mappings.
- duplicate the Value Stream definition for the agentic case.
- prevent a Value Stream from becoming agentic without changing its semantic identity.

This violates the architectural principle in ADR-ES-002 §5: "Enterprise context is not sufficient reason to duplicate foundational semantics." Adding a duplicate for the agentic case would duplicate for the wrong reason.

### 3.7 Why not Characteristic alone?

A characteristic is an **observation about an entity**. Treating `Agentic Value Stream` as a pure characteristic would mean:

- No stable identity for `Agentic Value Stream` ;;; it is just `Value Stream` with a flag.
- No governable relationships ;;; "Agentic Value Stream enables Capability" would not be expressible as a governed semantic assertion.
- No lifecycle ;;; the agentic-ness cannot be promoted from candidate to canonical.

The Profile hypothesis preserves the identity (because the Value Stream still has an identity) and the governability (because the Profile can carry governed characteristics and relationships).

---

## 4. Candidate semantic grounding

Per ADR-ES-002 §21 Q12, the candidate WSF grounding for `Value Stream` itself is `Value` (the WSF kernel concept) plus `Process` (as the supporting execution substrate) plus `Activity` (as the unit of execution).

`Agentic Value Stream` inherits this grounding, plus the agentic profile characteristics.

```text
WSF Value
   ;
   (via enterprise specialization)
   ;
Value Stream
   ;
   (via profile)
   ;
Agentic Value Stream

; profile characteristics:
   ;  goal-directed execution under bounded autonomy
   ;  AI-augmented decision-making
   ;  adaptive value-realization
   ;  human governance, not human execution
```

The Profile relationship to `Value Stream` is therefore established as:

```text
Profile of: Value Stream
Profile type: agentic-execution
Governed by: enterprise-semantics (Profile registry)
```

---

## 5. Candidate definition

Per ADR-ES-002 §7, the candidate definition for `Agentic Value Stream` is:

> An Agentic Value Stream is a Value Stream whose realization is characterized by goal-directed execution under bounded autonomy, AI-augmented decision-making, adaptive value-realization, and human governance rather than human execution.

This definition is:

- **Provisional ;;; not yet canonical.**
- **Subject to change** as the consolidated Agentic semantic review (per FND-ES-AG-001 §6) produces additional evidence.
- **Traceable** to ADR-ES-002 §21 Q7 and to the existing Agentic Value Stream investigation artifact.

---

## 6. Candidate relationships

Per FND-ES-000 §15 and FND-ES-AG-001 §4 Q14, the candidate relationships for `Agentic Value Stream`:

| Subject | Predicate | Object | Status | Provenance | Inverse |
|---------|-----------|--------|--------|------------|---------|
| Agentic Value Stream | realizes | Value Outcome | provisional | FND-ES-000 §15 | realized-by |
| Agentic Value Stream | enabled-by | Capability | provisional | FND-ES-000 §15 | enables |
| Agentic Value Stream | supported-by | Process | provisional | FND-ES-000 §15 | supports |
| Agentic Value Stream | executes-through | Agentic Workflow | provisional | ADR-ES-002 §22 ;; FND-ES-AG-001 §5 | executed-by |
| Agentic Value Stream | profile-of | Value Stream | provisional | FND-ES-AG-002 §3.4 | has-profile |

Each relationship is:

- **provisional** until FND-ES-AG-002+ produces evidence supporting `proposed` or `established`.
- **subject to qualification.** For example, `executes-through Agentic Workflow` holds only when the Value Stream has reached a state of AI-augmented execution ;;; a partially-executed Value Stream that is mid-transition to agentic execution may not satisfy this relationship.
- **subject to ADR-ES-AG-001** for promotion to governed status.

### 6.1 Why `executes-through` (not `contains`)?

ADR-ES-002 §22 explicitly rules out:

```text
Agentic Value Stream
    contains
Agentic Workflow
```

`contains` would imply that `Agentic Workflow` is a sub-component of `Agentic Value Stream`. That conflates value-realization with execution-choreography.

`executes-through` preserves the architectural distinction:

- `Value Stream` is about value-realization (semantics).
- `Workflow` is about execution-choreography (mechanism).
- `Value Stream executes-through Workflow` keeps them at the right level of abstraction.

### 6.2 Why `realizes Value Outcome`?

`Value Outcome` is what the Value Stream produces. The relationship is the semantic grounding of what a Value Stream is for. Without this relationship, `Value Stream` would be an empty concept.

### 6.3 Why `enabled-by Capability`?

`Agentic Value Stream` does not run on its own. It is enabled by Capabilities (per FND-ES-000 §15 and the existing capability-grounded work). The relationship is candidate evidence for the WSF `Capability` grounding in §4.

### 6.4 Why `supported-by Process`?

`Process` is the recurring organizational substrate that supports the Value Stream's execution. This is a different relationship from `executes-through Workflow`. A `Process` is structural (recurring capability), a `Workflow` is choreographic (specific execution path).

### 6.5 Why `profile-of Value Stream`?

This is the central relationship of this Finding. It establishes `Agentic Value Stream` as a Profile of `Value Stream` rather than a distinct semantic kind. This relationship is what the ADR-ES-AG-001 decision hinges on.

---

## 7. Candidate lifecycle status

Per ADR-ES-002 §13, the candidate lifecycle status for `Agentic Value Stream`:

| Status | Promotable to | Evidence required |
|--------|---------------|-------------------|
| Candidate (current) | Investigating | This Finding (FND-ES-AG-002) lands. |
| Investigating | Proposed | Consolidated Agentic semantic review (FND-ES-AG-001 §6) accepts the Profile hypothesis. |
| Proposed | Established | ADR-ES-AG-001 is approved with the Profile hypothesis as the governed decision. |
| Established | Canonical | `enterprise-semantics` releases a Candidate-status YAML record for `Agentic Value Stream` and a Profile record linking it to `Value Stream`. |

`Agentic Value Stream` does **not** skip Candidate ;;; per ADR-ES-002 §25, "Canonical != implemented elsewhere" and "implementation is the consequence of an approved semantic decision."

---

## 8. Provenance

The candidate relationships and the Profile hypothesis are derived from:

- **FND-ES-000** §3, §15 ;; semantic seed candidate list and candidate relationships.
- **FND-ES-001** §9 ;; Agentic vs Autonomous distinction and architectural constraint on Value Stream / Process / Workflow / Task Flow.
- **ADR-ES-002** §6, §20, §21, §22 ;; governance of specialization, Agentic family, the 14 questions, the architectural constraint.
- **The existing Agentic Value Stream investigation** (in the broader enterprise semantic workspace) ;; empirical evidence of agent participation, intent-driven execution, autonomous decisioning, and continuous optimization in agentic value streams.
- **FND-ES-AG-001** §5 ;; the working hypothesis on Agentic as a modifier.

These are **evidence** for the Profile hypothesis. They do not, by themselves, establish it as canonical.

---

## 9. Open questions for the consolidated review

The following questions are not answered by this Finding and must be addressed in FND-ES-AG-001+ sub-findings or the consolidated Agentic semantic review:

1. Does the `Profile` semantic construct (as opposed to specialization or characteristic) carry through to the entire Agentic family? Or is `Profile` specific to `Agentic Value Stream`?
2. Is `Agentic Operations` also a Profile of `Operations`, or is it a Specialization?
3. Is `Agentic Enterprise` also a Profile of `Enterprise`, or is it a Specialization?
4. What is the relationship between `Agentic Value Stream`, `Agentic Operations`, and `Agentic Enterprise`? Are they co-profiled?
5. How does `Agentic Value Stream` map to OpenDEA metamodel constructs? (Phase 4.6 deliverable.)
6. How does `Agentic Value Stream` map to WSF `Value`? (The Profile relationship is internal to Enterprise-Semantics ;;; the WSF grounding is via `Value Stream`'s existing WSF grounding.)

---

## 10. Decision summary

> **`Agentic Value Stream` is, on the evidence available to this Finding, a Profile of `Value Stream` rather than a specialization, characteristic alone, or distinct semantic kind.**
>
> The Profile relationship is the right semantic tool because:
>
> - The four agentic characteristics (bounded autonomy, AI-augmented decision-making, adaptive value-realization, human governance) are characteristics of execution, not of value-realization semantics.
> - The Agentic Value Stream shares its identity with Value Stream ;;; promoting/demoting its agentic profile does not change its identity.
> - A Profile preserves governed relationships, lifecycle, and mappings ;;; a pure characteristic would not.
> - A Profile avoids the semantic duplication that a distinct kind would create.
>
> The Finding does not, by itself, establish `Agentic Value Stream` as canonical. Promotion to `Proposed` requires the consolidated Agentic semantic review (FND-ES-AG-001 §6) to accept this hypothesis. Promotion to `Established` requires ADR-ES-AG-001.

---

## 11. Cross-references

- FND-ES-AG-001 (parent Finding): https://github.com/Enterprise-Semantics/enterprise-semantics-governance/blob/main/docs/finding/0001-agentic-semantic-grounding.md
- ADR-ES-002 (depends-on): https://github.com/Enterprise-Semantics/enterprise-semantics-governance/blob/main/docs/adr/0002-enterprise-semantic-model.md
- ADR-ES-002 §22 (architectural constraint on Agentic Value Stream): local working folder `00_inbox/ADR-ES-002.md`
- Local verbatim: `/home/hermes/Projects/Enterprise-Semantics/00_inbox/FND-ES-AG-002.md`
- Local dash-normalized: `/home/hermes/Projects/Enterprise-Semantics/seed/FND-ES-norm-AG-002.md`