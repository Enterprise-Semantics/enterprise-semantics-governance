<!--
FND-ES-AG-008 ;;; WSF Tier 1 / Tier 2 Grounding Boundary

Status: Proposed Finding
Authored by: Emmanuel A. Otchere
Date: 2026-09-22
Preceded by: Recon-ES-001a ;; ADR-ES-001 ;; FND-ES-AG-001 ;; FND-ES-AG-001-Grounding-Result
Depends on: FND-ES-AG-001 ;; FND-ES-AG-001-Grounding-Result ;; ADR-ES-001 ;; ADR-ES-002 ;; Recon-ES-001a §7 ;; WSF Tier 1/2 synthesis ;; F-035
Precedes: ADR-ES-002 ;; ADR-ES-003 ;; subsequent Phase 6 concept-specific ADRs ;; per-concept classification table

Working conclusion (provisional, NOT normative):
The current ES concept catalogue requires a per-concept WSF-grounding resolution into one of three legitimate categories (Tier 1 Kernel Reference, Tier 2 Specialisation, ES-canonical). Mixed claims (one concept specialising multiple WSF concepts, or specialising + referencing) are themselves a defect under ADR-ES-001 §4.1 and must be resolved before any concept-specific ADR can land.
-->

# FND-ES-AG-008 ;;; WSF Tier 1 / Tier 2 Grounding Boundary

**Status:** Proposed Finding
**Scope:** The WSF ;;; Enterprise-Semantics grounding relationship for every concept currently in `concepts/` plus the structural pattern future concepts must satisfy.
**Authored by:** Emmanuel A. Otchere
**Date:** 2026-09-22
**Preceded by:** Recon-ES-001a ;; ADR-ES-001 ;; FND-ES-AG-001 ;; FND-ES-AG-001-Grounding-Result
**Depends on:** FND-ES-AG-001 ;; FND-ES-AG-001-Grounding-Result ;; ADR-ES-001 ;; ADR-ES-002 ;; Recon-ES-001a §7 ;; WSF Tier 1/2 synthesis ;; F-035
**Precedes:** ADR-ES-002 ;; ADR-ES-003 ;; subsequent Phase 6 concept-specific ADRs ;; per-concept classification table for `enterprise-semantics-mappings`

---

## 1. Finding

### 1.1 The structural problem

Repository inspection of all 14 current concept YAMLs reveals that `wsf_grounding` claims are inconsistent in three ways:

1. **Uniform verb.** All claims use `specializes` or `references` against `external:wsf:*` identifiers, with no distinction between cases where WSF defines the concept at the kernel vs where WSF has a Tier 2 specialisation pattern vs where WSF has no equivalent.
2. **Multi-WSF claims.** Several concepts claim relationships to *more than one* WSF concept (e.g. `workflow` claims `wsf:Activity specializes` AND `wsf:Event references`; `agent` and `ai-agent` claim `wsf:Entity specializes` AND `wsf:Capability references`). Such multi-WSF claims effectively redefine the relationship between the WSF concepts inside ES, which ADR-ES-001 §4.1 forbids.
3. **Implicit ontological commits.** Profile records inherit the base concept's grounding via `references` (not `specializes`), but the YAMLs do not always make this inheritance explicit.

The combination obscures the WSF ;;; ES boundary and produces concrete defects: semantic duplication of WSF's Capability specialisation pattern in ES; underspecification of how ES Value Stream builds on the WSF kernel `Value`; and implicit ontological commits that downstream consumers cannot audit.

### 1.2 The three legitimate grounding categories

Per ADR-ES-001 §4.1, §4.2, §6, §15 and FND-ES-AG-001-Grounding-Result §1, the only legitimate ES ;;; WSF relationships are:

| Category | WSF status | ES treatment |
|----------|------------|--------------|
| **Tier 1 Kernel Reference** | WSF defines at Tier 1 kernel | ES does NOT redefine the kernel primitive; ES records reference the WSF concept; ES may add Profile bindings but does not introduce new semantics for the primitive itself |
| **Tier 2 Specialisation** | WSF defines a generic specialisation pattern at Tier 2 | ES records are ONE of the WSF-anticipated sub-kinds, OR are an additional parallel-class sub-kind requiring explicit justification |
| **ES-canonical** | WSF has no equivalent | ES is the authoritative home; `wsf_grounding` declares explicit absence of foundational grounding |

**Mixed claims are defects.** A concept that claims `specializes A` AND `specializes B` (or `specializes A` AND `references B`) is effectively redefining the relationship between A and B inside ES. Per ADR-ES-001 §4.1, such claims must be resolved into a single dominant category before the concept's ADR can land.

### 1.3 Per-concept classification (all 14, verified against YAMLs 2026-09-22)

Status legend: Resolved = single dominant category; Resolution Required = mixed claim needs ADR to pick one; Inherited = Profile record inherits base's classification.

| ES Concept ID | YAML claim | Working classification | Resolution call |
|---------------|------------|------------------------|-----------------|
| `ES:CONCEPT:capability` | `wsf:Capability specializes` | **Tier 2 Specialisation** | Resolved (provisional: Business-Capability equivalent per WSF pattern); ADR-ES-002 confirms |
| `ES:CONCEPT:value-stream` | `wsf:Value specializes` | **Tier 1 Kernel Reference + ES-canonical novelty** | Resolved (two relationships: references wsf:Value + introduces ES Stream construct); ADR-ES-003 implements |
| `ES:CONCEPT:enterprise` | `wsf:Entity specializes` | **Tier 1 Kernel Reference** | Resolved |
| `ES:CONCEPT:workflow` | `wsf:Activity specializes` + `wsf:Event references` | **Resolution Required** | ADR must pick primary specialisation target (Activity or Event) and demote the other to `references` or remove |
| `ES:CONCEPT:flow` | `wsf:Process specializes` + `wsf:Event references` | **Resolution Required** | Same; ADR must pick |
| `ES:CONCEPT:operations` | `wsf:Activity specializes` + `wsf:Event references` | **Resolution Required** | Same; ADR must pick |
| `ES:CONCEPT:agent` | `wsf:Entity specializes` + `wsf:Capability references` | **Resolution Required** | ADR-ES-AG-### decides whether `Capability references` is supplementary or vestigial |
| `ES:CONCEPT:ai-agent` | `wsf:Entity specializes` + `wsf:Capability references` | **Resolution Required** | Same; FND-ES-AG-007 already established Distinct-kind status but the mixed grounding claim was not addressed |
| `ES:CONCEPT:agentic-capability` | `wsf:Capability references` + Profile of capability | **Tier 2 Specialisation inherited + Profile** | Resolved (Profile-inheritance is correct pattern per ADR-ES-AG-001 §3) |
| `ES:CONCEPT:agentic-value-stream` | `wsf:Value references` + Profile of value-stream | **Tier 1 Kernel Reference inherited + Profile** | Resolved |
| `ES:CONCEPT:agentic-workflow` | `wsf:Activity references` + `wsf:Event references` + Profile | **Resolution Required inherited + Profile** | Base workflow must be resolved first; Profile-inheritance follows |
| `ES:CONCEPT:agentic-flow` | `wsf:Process references` + Profile | **Resolution Required inherited + Profile** | Base flow must be resolved first |
| `ES:CONCEPT:agentic-operations` | `wsf:Activity references` + Profile | **Resolution Required inherited + Profile** | Base operations must be resolved first |
| `ES:CONCEPT:agentic-enterprise` | `wsf:Entity references` + Profile | **Tier 1 Kernel Reference inherited + Profile** | Resolved |

**Summary by category:**
- Resolved: 6 concepts (capability, value-stream, enterprise, agentic-capability, agentic-value-stream, agentic-enterprise)
- Resolution Required: 8 concepts (workflow, flow, operations, agent, ai-agent, agentic-workflow, agentic-flow, agentic-operations)

### 1.4 Working hypothesis (provisional, NOT normative)

For each ES concept:
1. The `wsf_grounding` block must declare exactly ONE primary grounding relationship (either `specializes` for Tier 2 Specialisations and Tier 1 Kernel specialisations, or `references` for Tier 1 Kernel references and Profile inheritances).
2. Any supplementary grounding claims are defects and must be either justified as `references` (Tier 1 Kernel supplementary) or removed.
3. ES-canonical concepts must declare explicit absence of foundational grounding, not claim `specializes` against an `external:wsf:*` ID that does not exist.

The 8 Resolution Required concepts each require a per-concept ADR decision before the concept can be promoted out of Candidate.
### 1.5 Why Profile records use `references` not `specializes`

Per ADR-ES-AG-001 §3, a Profile is a governed configuration overlay applied to a base concept. The base concept retains its semantic identity; the Profile adds characteristics (in this org's current pattern: the four `agentic-execution` characteristics).

The semantic consequence is that a Profile record's relationship to WSF is *inherited from its base*, not independently established. A Profile that claims `wsf:Capability specializes` directly would be redefining the base's WSF relationship inside the Profile overlay ;;; which ADR-ES-001 §4.1 forbids and which is structurally unnecessary because the base already carries the grounding claim.

The correct Profile pattern is therefore:
- Base concept carries the primary WSF grounding claim (`specializes` for Tier 2; `references` for Tier 1 Kernel Reference or ES-canonical inheritance).
- Profile record carries `references` (not `specializes`) for the base's WSF grounding ;;; declaring inheritance without re-asserting the specialisation.
- Profile record additionally carries `profile_bindings` pointing to the Profile definition (`ES:PROFILE:agentic-execution` in this org's current pattern).

All 6 current Profile records (`agentic-capability`, `agentic-value-stream`, `agentic-workflow`, `agentic-flow`, `agentic-operations`, `agentic-enterprise`) follow this pattern correctly. The Profile convention itself is therefore not in scope for the mixed-claim defect interpretation in §1.2 ;;; the defect applies only to base concepts.

### 1.6 Foundational grounds

The three-category taxonomy and the mixed-claim defect interpretation rest on ADR-ES-001 §4.1 (no redefining WSF), §4.2 (ES scope), §6 (source of truth precedence), §15 (mapping relationships); FND-ES-AG-001-Grounding-Result §1 (WSF grounding is stronger than assumed; downstream systems specialise without redefining); WSF_Foundational_Semantic_Synthesis §3 (Tier 1 foundational domains + Tier 2 specialisations); F-035 (semantic kernel); ADR-ES-AG-001 §3 (Profile does not redefine base).

---

## 2. Problem being addressed

Without this classification:
- ADR-ES-002..006 cannot be drafted, because every concept YAML would either need to be amended first or carry mixed claims forward into the ADR.
- The recon §10 maturity gate cannot be evaluated for any concept, because the gate's `WSF grounding` criterion (criterion #7) presupposes a single, defensible grounding relationship.
- The `enterprise-semantics-mappings` repo cannot author mapping records, because mappings require each side to have a settled classification.
- The recon §14 governance pipeline stalls at ADR-ES-002 indefinitely.

---

## 3. Investigation methodology

This Finding applies the same approach as FND-ES-AG-001-Grounding-Result §1 to the broader WSF ;;; ES boundary rather than to the Agentic family specifically.

### 3.1 What WSF defines at Tier 1 vs Tier 2

Per WSF_Foundational_Semantic_Synthesis §3: Tier 1 includes the kernel (Entity, Relationship, Value, etc.) plus the Foundational Semantic Domains (Identity, Concept, Event, State, Disposition, Proposition, Assertion, Context, Time, Space, etc.). Tier 2 includes dispositions derived from Tier 1 (Capability = specialisation of Disposition derived from Capacity + Ability).

### 3.2 What WSF does not define

WSF explicitly states (§2) it is not an enterprise architecture model, business architecture model, assessment model, catalog of industry terminology, or repository of every possible domain concept. Constructs that are enterprise-specific (Value Stream as a Stream construct, Operations, Enterprise as an operating unit, Workflow, Flow, Agent in the AI sense, etc.) are not in WSF scope.

### 3.3 What is the legitimate WSF ;;; ES relationship

Per ADR-ES-001 §4.1 + §15: ES shall not redefine WSF concepts. The legitimate relationships are the three categories in §1.2. The mixed claims in §1.3 are defects to be resolved, not legitimate complexity.

### 3.4 Verification

All 14 concept YAMLs in `repos/enterprise-semantics/concepts/` were parsed and the `wsf_grounding` block extracted. The §1.3 table is the verified state as of 2026-09-22.

---

## 4. Proposed next step

### 4.1 Primary deliverable

Produce a machine-readable and human-readable per-concept WSF ;;; ES classification table covering all 14 concepts. The table is a separate artefact:

- `repos/enterprise-semantics-mappings/mappings/wsf-es-classification.v0.1.csv` (CSV)
- `repos/enterprise-semantics-mappings/mappings/wsf-es-classification.v0.1.md` (Markdown render)

Each row carries: ES concept ID, ES canonical name, current YAML `wsf_grounding` claim, working classification (one of the three categories), resolution call (Resolved / Resolution Required), owning ADR, decision state.

### 4.2 ADR-ES-002 is the first concept-specific ADR

ADR-ES-002 (Capability Semantic Grounding) implements the §1.3 Capability classification. It decides Business-Capability-equivalence vs parallel-class and amends the YAML accordingly.

### 4.3 ADR-ES-003 is the second

ADR-ES-003 (Value Stream Semantic Grounding) implements the §1.3 Value Stream classification. It amends the YAML to declare the two-relationship structure (Tier 1 Kernel Reference + ES-canonical novelty).

### 4.4 ADR-ES-004 through ADR-ES-006 follow the recon pipeline (Agentic family); ADR-ES-007 through ADR-ES-014 cover the 8 Resolution Required concepts (Option Q)

Recon §14 pipeline reserved ADR-ES-002 for Capability and ADR-ES-003 for Value Stream, then ADR-ES-004 through ADR-ES-006 for the Agentic concept-specific family (Agentic, Agentic Value Stream, Agentic Workflow). Per Option Q, those recon reservations are preserved:

- ADR-ES-002: Capability Semantic Grounding (Tier 2 Specialisation resolved; Business-Capability equivalent provisional)
- ADR-ES-003: Value Stream Semantic Grounding (Tier 1 Kernel Reference + ES-canonical novelty)
- ADR-ES-004: Agentic Semantic Grounding (already ratified as ADR-ES-AG-001; reconcile the ADR-ES-AG vs ADR-ES numbering)
- ADR-ES-005: Agentic Value Stream Semantic Grounding (per ADR-ES-001 §27 numbering)
- ADR-ES-006: Agentic Workflow Semantic Grounding (per ADR-ES-001 §27 numbering)

The 8 Resolution Required concepts extend the sequence:

- ADR-ES-007: Workflow Semantic Grounding (Resolution Required: pick primary WSF target)
- ADR-ES-008: Flow Semantic Grounding (Resolution Required)
- ADR-ES-009: Operations Semantic Grounding (Resolution Required)
- ADR-ES-010: Agent Semantic Grounding (Resolution Required)
- ADR-ES-011: AI Agent Semantic Grounding (Resolution Required + FND-ES-AG-007 Distinct-kind)
- ADR-ES-012: Agentic Workflow Semantic Grounding (Resolution Required inherited + Profile)
- ADR-ES-013: Agentic Flow Semantic Grounding (Resolution Required inherited + Profile)
- ADR-ES-014: Agentic Operations Semantic Grounding (Resolution Required inherited + Profile)

Each ADR resolves the concept's mixed grounding claim (declares single dominant category + any supplementary `references` it can justify) before the concept can be considered for §10 maturity gate evaluation. The recon's Capability-first order is preserved at the front of the sequence; the Resolution Required concepts follow the recon pipeline, not displace it.

### 4.5 The 4 Established labels require both §10 gate AND this Finding

Per the user's 2026-09-22 directive (re-evaluate, no grandfathering), each Established label is reviewed at its concept-specific ADR. That review cannot proceed until this Finding is Accepted and the Resolution Required concepts have their mixed claims resolved. The §10 maturity gate and the WSF grounding classification are joint prerequisites.

### 4.6 No concept YAML is modified by this Finding

The Finding produces the classification framework and the per-concept table. The ADRs implement the changes. Per ADR-ES-001 §10, Findings establish hypotheses, not decisions.

---

## 5. Out of scope (explicit)

- No concept YAML modification.
- No ADR promotion to Accepted.
- No Established label change.
- No Phase 6 concept-specific ADR drafting (gated on this Finding being Accepted and the Resolution Required concepts being decided).
- No `enterprise-semantics-mappings` mapping record authored (those implement the classification, not produce it).
- No remote push to `github.com/Enterprise-Semantics`.
- No CR-ES-001 authoring (held per user directive 2026-09-22).
- No amendment to the recon §14 governance pipeline (Capability first preserved; the first concrete ADR is preceded by this Finding).

---

## 6. Working conclusion (provisional, NOT normative)

The current ES concept catalogue requires per-concept resolution of WSF grounding into one of three legitimate categories (Tier 1 Kernel Reference, Tier 2 Specialisation, ES-canonical). Mixed claims are defects under ADR-ES-001 §4.1 and must be resolved before any concept-specific ADR can land. The per-concept classification in §1.3 is provisional and explicitly subject to ADR-ES-002 through ADR-ES-### review.

This Finding establishes the classification framework and the per-concept table. It does not amend any YAML, does not promote any ADR, and does not author any CR.
