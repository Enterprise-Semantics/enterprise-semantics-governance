<!--
FND-ES-AG-003 ;;; Agentic Workflow Semantic Grounding

Dash-normalized: colons (:) and semicolons (;) used consistently.
Verbatim original: 00_inbox/FND-ES-AG-003.md (identical bytes; authored
dash-normalized from the start).

Status: Proposed Finding.
Authored by: manny-es (the dedicated sub-agent for Enterprise-Semantics).
Date: 2026-09-02.
Preceded by: FND-ES-AG-001 ;;; FND-ES-AG-002.
Depends on: ADR-ES-AG-001 (Accepted) ;;; ADR-ES-002.
Transitively: ADR-ES-001 pending.

Working conclusion: Agentic Workflow is a Profile of Workflow under agent-augmented
execution conditions, applying the same Profile characteristics as the rest of the
Agentic family per ADR-ES-AG-001.
-->

# FND-ES-AG-003 ;;; Agentic Workflow Semantic Grounding

**Status:** Proposed Finding
**Scope:** `Agentic Workflow` (and its relationship to `Workflow`)
**Precedes:** ADR-ES-AG-001 (cited as supporting evidence) ;; CR-ES-AG-004 (Agentic Workflow)
**Depends on:** ADR-ES-AG-001 (Accepted) ;; FND-ES-AG-001 (Agentic Semantic Grounding) ;; FND-ES-AG-002 (Agentic Value Stream Semantic Grounding) ;; ADR-ES-002 ;; ADR-ES-001 pending
**Related:** FND-ES-000 ;; FND-ES-001 ;; ADR-ES-002 §21 Q6

---

## 1. Finding

The existing body of agentic work uses `Agentic Workflow` as a distinct concept from `Workflow`. It appears in the FND-ES-000 §15 seed relationships:

```text
Agentic Workflow
    orchestrates
        Agentic Flow
```

and in the FND-ES-AG-002 candidate relationships:

```text
Agentic Value Stream
    executes-through
        Agentic Workflow
```

This Finding investigates the relationship between `Agentic Workflow` and `Workflow` and proposes a candidate answer.

**Working conclusion (provisional, NOT normative):**

`Agentic Workflow` is a **Profile** of `Workflow` under agent-augmented execution conditions, applying the same Profile characteristics as the rest of the Agentic family per ADR-ES-AG-001.

The rationale follows.

---

## 2. Problem being addressed

Without semantic grounding of `Agentic Workflow`:

- The diagram-level convention `Agentic Workflow orchestrates Agentic Flow` is not a governed semantic assertion.
- The relationship `Agentic Value Stream executes-through Agentic Workflow` (per FND-ES-AG-002) is not implementable without knowing whether `Agentic Workflow` is a Profile, Specialization, or Distinct kind.
- Downstream consumers cannot stably reference `Agentic Workflow`.
- Cross-investigation comparisons between agentic and non-agentic workflows remain fragile.

---

## 3. Investigation methodology

### 3.1 What is `Workflow`?

A `Workflow` is a specific execution choreography ;;; a sequence of steps, decision points, and execution paths that produce a defined outcome. It is distinct from:

| Concept | Unit of analysis |
|---------|------------------|
| Value Stream | End-to-end value realization |
| Process | Recurring organizational capability |
| Workflow | Specific execution choreography |
| Task Flow | Individual task execution |

`Workflow` is choreographic (about how steps are arranged) ;;; not value-realizational (about what value is realized) and not structural (about recurring capabilities).

### 3.2 What is `Agentic`?

Per FND-ES-AG-001 §5 and ADR-ES-AG-001 §3, the working hypothesis is:

> `Agentic` is a Profile modifier under agent-augmented execution conditions.

It is not a semantic kind in its own right. It is a configuration overlay on a base concept.

### 3.3 What makes a Workflow Agentic?

A Workflow is Agentic when, across its steps, it exhibits the four Profile characteristics from ADR-ES-AG-001 §3.3:

1. **Goal-directed execution under bounded autonomy.** The Workflow progresses toward a stated outcome without requiring continuous human-driven routing.
2. **AI-augmented decision-making.** Decision points are resolved by AI agents under governed policy.
3. **Adaptive behavior.** The Workflow can reconfigure its steps in response to changing conditions and feedback.
4. **Human governance, not human execution.** Humans set intent, policy, and outcome criteria. AI agents execute within those bounds.

Each property is a **characteristic** of the Workflow's execution, not of its choreographic structure.

### 3.4 The four candidate answers

| Hypothesis | Description | Implications |
|------------|-------------|--------------|
| **A. Specialization** | `Agentic Workflow` is a strict subclass of `Workflow`. | Inherits all properties; agentic-specific properties are differentiating constraints. |
| **B. Profile** | `Agentic Workflow` is a Workflow with the agentic profile applied. | Same identity as Workflow, but with a configuration overlay. |
| **C. Characteristic** | `Agentic Workflow` is a Workflow that happens to have agentic characteristics. | No new concept; just an observation about a Workflow. |
| **D. Distinct kind** | `Agentic Workflow` is its own ontological class. | Requires its own definition, relationships, lifecycle. |

**Chosen hypothesis: B ;;; Profile.**

Rationale:

- Same reasoning as FND-ES-AG-002 §3.4: the agentic characteristics are characteristics of execution, not of choreographic structure.
- ADR-ES-AG-001 §3 commits the Agentic family to the Profile pattern. Applying it consistently here preserves architectural consistency.
- A Profile preserves governed relationships (especially `orchestrates Agentic Flow`), lifecycle, and mappings.

### 3.5 Why not Specialization?

A Specialization would imply that `Agentic Workflow` has additional properties that `Workflow` does not. The four agentic characteristics are not additional properties ;;; a Workflow without those characteristics is still a Workflow. They are execution constraints, not choreographic extensions.

### 3.6 Why not Distinct kind?

A Distinct kind would duplicate the Workflow definition for the agentic case. That violates ADR-ES-002 §5 and would prevent a Workflow from becoming agentic without changing its semantic identity.

### 3.7 Why not Characteristic alone?

A pure Characteristic would lose stable identity for `Agentic Workflow` ;// it would just be `Workflow` with a flag. Governed relationships (e.g. `Agentic Workflow orchestrates Agentic Flow`) would not be expressible as governed semantic assertions.

---

## 4. Candidate semantic grounding

Per ADR-ES-AG-001 §3.3 and the WSF grounding work:

```text
WSF Activity
   ;
   (via enterprise specialization)
   ;
Workflow
   ;
   (via Profile)
   ;
Agentic Workflow

; profile characteristics:
   ;  goal-directed execution under bounded autonomy
   ;  AI-augmented decision-making
   ;  adaptive behavior
   ;  human governance, not human execution
```

`Agentic Workflow` inherits the Workflow grounding plus the Profile characteristics.

---

## 5. Candidate definition

Per ADR-ES-002 §7:

> An Agentic Workflow is a Workflow whose execution is characterized by goal-directed progression under bounded autonomy, AI-augmented decision-making at decision points, adaptive step reconfiguration, and human governance rather than human execution.

This definition is:

- **Provisional ;;; not yet canonical.**
- **Subject to change** as the consolidated Agentic semantic review (per FND-ES-AG-001 §6) produces additional evidence.
- **Traceable** to ADR-ES-AG-001 §3.3 and the existing Agentic Workflow investigation artifact.

---

## 6. Candidate relationships

| Subject | Predicate | Object | Status | Provenance | Inverse |
|---------|-----------|--------|--------|------------|---------|
| Agentic Workflow | profile-of | Workflow | provisional | FND-ES-AG-003 §3.4 | has-profile |
| Agentic Workflow | orchestrates | Agentic Flow | provisional | FND-ES-000 §15 | orchestrated-by |
| Agentic Workflow | executes | Value Outcome (indirect) | provisional | FND-ES-AG-003 §6.1 | executed-by |

### 6.1 Why `orchestrates Agentic Flow`?

Per FND-ES-000 §15 and the existing Agentic diagrams, `Agentic Workflow` orchestrates `Agentic Flow`. The relationship preserves the architectural distinction:

- `Workflow` is choreographic (sequence of steps).
- `Flow` is the unit-of-execution that the Workflow sequences.
- `Workflow orchestrates Flow` keeps them at the right level of abstraction.

### 6.2 The indirect Value Outcome relationship

`Agentic Workflow` does not directly realize `Value Outcome` ;;; that is `Agentic Value Stream`'s relationship per FND-ES-AG-002 §6.2. `Agentic Workflow` contributes to value-realization indirectly:

```text
Agentic Value Stream
    executes-through Agentic Workflow
        which orchestrates Agentic Flow
            which uses AI Agent
```

The indirect relationship is acceptable because the architectural chain is explicit.

---

## 7. Architectural preservation

Per ADR-ES-002 §22 and FND-ES-AG-002 §6.1:

- `Value Stream != Process != Workflow != Task Flow` is preserved.
- `Agentic Workflow orchestrates Agentic Flow` is preferred over `contains` to keep choreographic structure (Workflow) and unit-of-execution (Flow) at the right level of abstraction.

---

## 8. Candidate lifecycle status

Per ADR-ES-002 §13:

```text
Candidate (current) → Investigating → Proposed → Established → Canonical
```

- Promotion to **Investigating** lands with this Finding.
- Promotion to **Proposed** requires the consolidated Agentic semantic review (FND-ES-AG-001 §6) to accept the Profile hypothesis for Agentic Workflow (consistent with FND-ES-AG-002 for Agentic Value Stream).
- Promotion to **Established** requires ADR-ES-AG-001 (already Accepted 2026-09-02) + CR-ES-AG-004 landing the YAML record with conformance evidence.

---

## 9. Provenance

The candidate relationships and the Profile hypothesis are derived from:

- **FND-ES-000** §15 ;;; candidate seed relationships.
- **FND-ES-001** §9 ;;; Agentic vs Autonomous distinction.
- **ADR-ES-002** §6, §20, §21 Q6, §22 ;;; governance of specialization, Agentic family, Q6 (Agentic Workflow vs Workflow).
- **ADR-ES-AG-001** §3 ;;; Profile architectural commitment.
- **FND-ES-AG-001** §5 ;;; working hypothesis on Agentic as a modifier.
- **FND-ES-AG-002** §3.4 ;;; Profile hypothesis pattern (applied here to Workflow).
- The existing Agentic Workflow investigation (in the broader enterprise semantic workspace).

These are **evidence** for the Profile hypothesis. They do not, by themselves, establish it as canonical.

---

## 10. Decision summary

> **`Agentic Workflow` is, on the evidence available to this Finding, a Profile of `Workflow` under agent-augmented execution conditions.**
>
> The Profile relationship follows the same reasoning as FND-ES-AG-002 for `Agentic Value Stream`:
>
> - The agentic characteristics are characteristics of execution, not of choreographic structure.
> - The Profile pattern preserves governed relationships (especially `orchestrates Agentic Flow`), lifecycle, and mappings.
> - A Profile avoids the semantic duplication that a Distinct kind would create.
>
> The Finding does not, by itself, establish `Agentic Workflow` as canonical. Promotion to `Proposed` requires the consolidated Agentic semantic review. Promotion to `Established` requires CR-ES-AG-004 landing the YAML record with conformance evidence.

---

## 11. Cross-references

- FND-ES-AG-001 (parent): https://github.com/Enterprise-Semantics/enterprise-semantics-governance/blob/main/docs/finding/0001-agentic-semantic-grounding.md
- FND-ES-AG-002 (sibling ;;; Agentic Value Stream): https://github.com/Enterprise-Semantics/enterprise-semantics-governance/blob/main/docs/finding/0002-agentic-value-stream-semantic-grounding.md
- ADR-ES-AG-001 (Accepted 2026-09-02): https://github.com/Enterprise-Semantics/enterprise-semantics-governance/blob/main/docs/adr/0003-agentic-semantic-decision.md
- ADR-ES-002 (depends on): https://github.com/Enterprise-Semantics/enterprise-semantics-governance/blob/main/docs/adr/0002-enterprise-semantic-model.md
- Local verbatim: `/home/hermes/Projects/Enterprise-Semantics/00_inbox/FND-ES-AG-003.md`
- Local dash-normalized: `/home/hermes/Projects/Enterprise-Semantics/seed/FND-ES-norm-AG-003.md`