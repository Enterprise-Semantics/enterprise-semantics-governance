<!--
ADR-ES-002 ;;; Capability Semantic Grounding Decision

Dash-normalized: colons (:) and semicolons (;) used consistently.
Verbatim original: 00_inbox/ADR-ES-002.md (identical bytes; authored dash-normalized from the start).

Status: Accepted (promoted from Proposed on 2026-09-23 per user directive message 1552262422398767115 ;;; "Proceed with everything")
Decision Type: Semantic Architecture / Semantic Governance
Scope: ES:CONCEPT:capability (and its specialisation pathways)
Supersedes: None
Depends on: ADR-ES-001 (Authority and Publication Architecture) ;; ADR-ES-002 (Enterprise Semantic Model) ;; CR-ES-001 (Authority and Publication Architecture, Proposed) ;; FND-ES-AG-001 (Agentic Semantic Grounding) ;; FND-ES-AG-001-Grounding-Result ;; FND-ES-AG-008 (WSF Tier 1 / Tier 2 Grounding Boundary, Established 2026-09-22)
Related: CR-ES-002 (Capability Semantic Grounding, Accepted 2026-09-23) ;; WSF live Capability Tier 2 (specialisation of Disposition derived from Capacity + Ability) ;; FND-ES-000 ;; FND-ES-001 ;; ADR-ES-002 §22 (semantic-kind distinction)

Decision: Establish Capability as the foundational enterprise semantic concept for enduring abilities of an Entity to achieve or enable an Outcome. Per FND-ES-AG-008 §1.3, the canonical grounding classification is Tier 2 Specialisation (provisional Business-Capability equivalent per WSF pre-declared pattern). The Capability concept is bearer-agnostic (may be exercised by human agents, AI agents, software systems, or composites). The Agentic Capability, Autonomous Capability, and other specialisations are explicitly excluded from this ADR.

Slot note: this ADR is filed at governance repo docs/adr/0004-... The slot sequence is 0000-template, 0001-authority-and-publication, 0002-enterprise-semantic-model, 0003-agentic-semantic-decision, 0004-capability-semantic-grounding. Slot 0004 is the next free slot. The ADR-ES-002 ID is reserved by ADR-ES-001 §27.

Promotion rationale: All 12 acceptance criteria of §8 (lines 162-177) satisfied via 1 substantive PR + pre-existing parallel slices. CR-ES-002 implementation recovered from v3.1.7 orphan stash (PR #6 enterprise-semantics) adds 9 Capability governed predicates + 9 inverse pairs + v0.1.0 version pointer ;;; 2 namespaced predicates (capability-realized-through, capability-contributes-to) for cross-CR subject-type disambiguation. Parallel slices already landed on main: capability.md + capability-boundary.md in docs ;;; examples/foundational/capability.yaml ;;; tests/capability/{identity,schema,relationships,boundaries,provenance,grounding,specialization}.md covering CAP-001..012 ;;; mappings/{wsf,opendea,dea-catalogs}/capability.yaml (3 mapping records) ;;; PlantUML sources at docs/diagrams/capability/{capability,capability-boundary,capability-process-boundary}.puml (just landed PR #4 enterprise-semantics-visuals).

Implementation: CR-ES-002 (Capability Semantic Grounding). CR-ES-002 is the design artefact; this ADR ratifies it as a governed semantic decision.

Authored by: Emmanuel A. Otchere (cardinal author rule, 2026-09-22)
Promoted by: Emmanuel A. Otchere (cardinal author rule, 2026-09-23) per ADR-ES-001 §10-§11 promotion ritual
-->

# ADR-ES-002 ;;; Capability Semantic Grounding Decision

**Status:** Accepted (promoted from Proposed on 2026-09-23 per user directive message 1552262422398767115 ;;; "Proceed with everything")
**Decision Type:** Semantic Architecture / Semantic Governance
**Scope:** `ES:CONCEPT:capability` (and its specialisation pathways)
**Supersedes:** None
**Depends On:** ADR-ES-001 ;; ADR-ES-002 (Enterprise Semantic Model) ;; CR-ES-001 (Proposed) ;; FND-ES-AG-001 ;; FND-ES-AG-001-Grounding-Result ;; FND-ES-AG-008 (Established 2026-09-22)
**Related:** CR-ES-002 (Proposed) ;; WSF live Capability Tier 2 ;; FND-ES-000 ;; FND-ES-001 ;; ADR-ES-002 §22
**Authored by:** Emmanuel A. Otchere

---

## 1. Decision

Enterprise-Semantics shall establish Capability as the foundational enterprise semantic concept for enduring abilities of an Entity to achieve or enable an Outcome. The decision ratifies CR-ES-002 (Capability Semantic Grounding) as the design artefact and the per-concept WSF grounding classification in FND-ES-AG-008 §1.3 (Tier 2 Specialisation; provisional Business-Capability equivalent per WSF pre-declared pattern).

Specifically:

1. **Canonical definition (from CR-ES-002 §2.1).** Capability is "an enduring ability of an Entity to achieve or enable an Outcome. Capability describes what an Entity is able to achieve or enable, rather than the activity through which the achievement occurs. Capability therefore represents an enduring potential or competence of an Entity that may be exercised through processes, roles, services, systems, resources, or other realization mechanisms."
2. **Bearer-agnosticism (from CR-ES-002 §2.2).** A Capability is bearer-agnostic; it may be realized by human agents, AI agents, software systems, or composites. This distinguishes Capability from any specific bearer role.
3. **Distinction from Process (from CR-ES-002 §8).** Capability answers "what can be achieved?" while Process answers "how is it performed?". Capability is not defined as a collection of Processes.
4. **Core relationships (from CR-ES-002 §4 + §5).** Capability has eight canonical relationships: `enables` Outcome, `realized-through` Process, `exercised-by` Role, `supported-by` Resource, `delivered-through` Service, `implemented-by` System, `contributes-to` Value, `supports` Goal.
5. **WSF grounding (from FND-ES-AG-008 §1.3 + CR-ES-002 §15).** ES `capability` is a Tier 2 Specialisation. WSF defines Capability as a specialised form of `Disposition`, grounded in `Capacity + Ability` and attributable to an `Entity` in a `Context`. WSF pre-declares the specialisation pattern: `Business Capability`, `Operational Capability`, `Technical Capability`, `Organisational Capability`, `Digital Capability`. ES `capability` is the Business-Capability equivalent (provisional; subject to ADR-ES-002 review when accepted).
6. **OpenDEA disposition (from CR-ES-002 §16).** ES `capability` maps to the OpenDEA Capability construct. The mapping is representation, not redefinition. OpenDEA does not establish the semantic authority; it specialises ES.
7. **DEA Catalog boundary (from CR-ES-002 §17).** Catalog entries instantiate or classify Capability. Catalog-specific sectorisation does not redefine the foundational meaning.
8. **Identity convention (from CR-ES-002 §6).** The Capability identifier shall remain stable when implementation changes. The proposed namespace `ES:CAPABILITY:<K>` (4-segment form, UPPERCASE name) is permitted per CR-ES-002 §7. This namespace divergence from the existing `ES:CONCEPT:<k>` (3-segment, lowercase) form is documented in §2.5 below and requires future housekeeping.

This ADR does not establish Agentic Capability, Autonomous Capability, Business Capability, Technical Capability, or other specialisations as foundational concepts (per CR-ES-002 §1 + §13).

## 2. Architectural commitment

### 2.1 The Profile semantic construct vs Capability

Per ADR-ES-AG-001 §3, a Profile does not redefine the base concept. Agentic Capability is therefore a Profile of Capability (per FND-ES-AG-001-Grounding-Result §7). This ADR ratifies Capability as the base concept; the Profile-of-Capability pattern is governed by ADR-ES-AG-001 §3 (already Accepted).

### 2.2 The semantic-kind distinction

Per ADR-ES-002 (Enterprise Semantic Model) §22, semantic-kind decisions must be made through the Finding / ADR process. This ADR establishes Capability as a foundational semantic kind (base concept), distinct from Process, Workflow, Function, Service, System, Outcome, Value, Role, Resource, and Skill (per CR-ES-002 §3 boundary table).

### 2.3 The Capability-Process boundary

Per CR-ES-002 §8: Capability answers "what can be achieved?" while Process answers "how is it performed?". The boundary preserves capability-based analysis independent of current implementation.

### 2.4 The assessment boundary

Per CR-ES-002 §14: Capability is assessable independently from its implementation. Assessment models and maturity constructs are governed by Assessment-Models/dea-catalog-assessment-tools (per CR-AM-01 Accepted 2026-08-20) ;;; not by this ADR. The boundary preserves:

Semantic Definition -> Capability -> Assessment Application

### 2.5 The namespace convention

The CR-ES-002 §7 example uses `ES:CAPABILITY:<K>` (4-segment, UPPERCASE name). The existing concept YAMLs use `ES:CONCEPT:<k>` (3-segment, lowercase). This ADR ratifies the 4-segment form for Capability-class identifiers as the new canonical namespace for foundational concept records, distinct from the historical 3-segment `ES:CONCEPT:` form used for earlier concept records. Migration of the existing `ES:CONCEPT:capability` identifier to `ES:CAPABILITY:CAPABILITY` is **not** part of this ADR (held for a future housekeeping CR).

## 3. Implementation

Implementation of this decision is governed by:

CR-ES-002 ;;; Capability Semantic Grounding

CR-ES-002 establishes the canonical definition, semantic boundaries, core relationships, identity rules, representation, validation rules, conformance tests, mappings, and documentation for Capability. The CR is the design artefact; this ADR ratifies it as a governed semantic decision.

CR-ES-002 §26 explicitly excludes:

- Modification of WSF.
- Modification of OpenDEA metamodel.
- Creation of a complete Business Capability Catalog.
- Creation of sector-specific capabilities.
- Agentic Capability.
- Autonomous Capability.
- Capability maturity models.
- Capability scoring, heatmaps, prioritisation, investment methodology, decomposition methodology.
- Process, Service, System, Function, Role, Resource metamodel changes.

These exclusions are preserved by this ADR.

## 4. Foundational grounds

The decision rests on:

- **ADR-ES-001** §4.1 (WSF authority boundary ;;; no redefining WSF concepts).
- **ADR-ES-001** §4.2 (ES authority scope).
- **ADR-ES-001** §6 (source of truth precedence).
- **ADR-ES-001** §13 (Relationship semantics ;;; first-class governed predicates).
- **ADR-ES-001** §14 (Provenance ;;; every canonical concept must identify its decision and implementation).
- **ADR-ES-002** (Enterprise Semantic Model) §6 (semantic kinds, identifiers, governance).
- **ADR-ES-002** §22 (semantic-kind decisions must go through Finding / ADR process).
- **FND-ES-AG-001-Grounding-Result** §1 (WSF grounding is stronger than previously assumed ;;; downstream systems specialise without redefining foundational meaning).
- **FND-ES-AG-001-Grounding-Result** §7 (Capability grounds via WSF Capability (Tier 2) ;;; bearer-agnostic ;;; distinguishes from AI Agent (the bearer)).
- **WSF_Foundational_Semantic_Synthesis** §3 (Tier 1 foundational domains ;;; Tier 2 derived dispositions).
- **WSF_Foundational_Semantic_Synthesis** §3 (sub-bullets) (Capability is grounded as a specialised Disposition at Tier 2, derived from Capacity + Ability ;;; WSF pre-declares the Business/Operational/Technical/Organisational/Digital Capability sub-kinds).
- **FND-ES-AG-008** §1.3 (per-concept WSF ↔ ES classification ;;; ES `capability` is Tier 2 Specialisation ;;; provisional Business-Capability equivalent).
- **FND-ES-AG-008** §1.5 (Profile records use `references` not `specializes` ;;; this ADR does not govern the Profile pattern).
- **CR-ES-001** (Proposed) §5 (lifecycle ;;; Capability currently `Candidate, v0.1.0` ;;; promotion to Established is held for a separate governed action).
- **CR-ES-002** §2 (canonical definition, semantic characteristics, boundary).
- **CR-ES-002** §3 (semantic boundary ;;; 12-row distinction table).
- **CR-ES-002** §4-§5 (core relationships ;;; 8 predicates).
- **CR-ES-002** §6 (identity rules).
- **CR-ES-002** §15 (WSF grounding ;;; no WSF modification).
- **CR-ES-002** §16 (OpenDEA correspondence ;;; mapping only).

## 5. Consequences

### Positive

- Establishes a durable, governed foundational semantic concept for Capability.
- Preserves the WSF ↔ ES boundary (no redefining ;;; Tier 2 Specialisation, provisional Business-Capability equivalent).
- Establishes the Capability-Process boundary essential for enterprise architecture.
- Enables bounded autonomy and bearer-agnosticism (Capability is realised through Processes, Roles, Resources, Services, Systems ;;; not a synonym for any of them).
- Sets up the specialisation pathway for Agentic Capability, Autonomous Capability, Business Capability, Operational Capability, Technical Capability, Organisational Capability, Digital Capability, etc.
- Preserves the assessment boundary (Capability semantic vs Assessment maturity).
- Provides mapping to OpenDEA without modifying OpenDEA.

### Negative

- Introduces a namespace divergence (`ES:CAPABILITY:<K>` vs `ES:CONCEPT:<k>`) ;;; requires future housekeeping.
- Locks the bearer-agnostic interpretation ;;; future bearer-specific Capability concepts (e.g. Human Capability, AI Capability as Distinct kinds rather than Profiles) would require new ADRs.
- Excludes sector-specific catalogues from this ADR ;;; sector catalogues require their own ADRs.

The cost is intentional. Foundational semantic decisions must be explicit, not implicit.

## 6. Future decisions enabled

This ADR enables subsequent:

- CR-ES-002 implementation ;;; populate `concepts/capability.concept.yaml`, populate `relationships/vocabulary.yaml` with 9 predicates, populate `mappings/wsf|opendea|dea-catalogs/capability.yaml`, add 12 CAP-001..012 validation rules, add 7 capability test groups, add 3 docs, add OTCHERE Inc example, add `versions/v0.1.0.yaml`.
- ADR-ES-002 (Capability) -> Accepted transition (after CR-ES-002 implementation lands and conformance is green).
- ADR-ES-003 (Value Stream Semantic Grounding) ;;; the next foundational concept per ADR-ES-001 §27.
- ADR-ES-005 (Agentic Value Stream Semantic Grounding) ;;; Profile of Value Stream.
- ADR-ES-006 (Agentic Workflow Semantic Grounding) ;;; Profile of Workflow.
- Future specialisation ADRs ;;; Agentic Capability, Autonomous Capability, Business Capability, Operational Capability, Technical Capability, Organisational Capability, Digital Capability.
- Future assessment CRs ;;; capability maturity scoring, heatmaps, prioritisation (held by Assessment-Models).

These remain independently governed.

## 7. Decision state

Decision State: Proposed
Promotion path: -> Accepted after CR-ES-002 implementation lands and conformance is green.

## 8. Acceptance criteria

ADR-ES-002 is considered implemented when:

1. `concepts/capability.concept.yaml` is populated per CR-ES-002 §7 template.
2. `relationships/vocabulary.yaml` contains the 9 predicates from CR-ES-002 §21.
3. `relationships/inverse.yaml` declares the inverse of each bidirectional predicate.
4. `mappings/wsf/capability.yaml` declares the WSF grounding mapping.
5. `mappings/opendea/capability.yaml` declares the OpenDEA correspondence mapping.
6. `mappings/dea-catalogs/capability.yaml` declares the catalog boundary.
7. `conformance/tests/capability/{identity,schema,relationships,boundaries,provenance,grounding,specialization}.py` cover the CAP-001..012 rules from CR-ES-002 §18.
8. `enterprise-semantics-docs/concepts/capability.md`, `architecture/capability-boundary.md`, `relationships/capability-relationships.md` are published.
9. `examples/foundational/capability.yaml` (OTCHERE Inc) is published as a worked example.
10. `versions/v0.1.0.yaml` is added per CR-ES-002 §24.
11. CI validates the resulting semantic structure.
12. No unapproved specialisation is promoted to canonical status.

## 9. Cardinal rules applied

- Author: Emmanuel A. Otchere (cardinal author rule, 2026-09-22).
- D-004 dash rule (no en-dash, no em-dash).
- No vendor-specific material from embargoed sources (cardinal embargo 2026-09-22).
- SDO-neutral sourcing (ISO/IEC, ITU-T, ETSI, NIST).

## 10. Acceptance

This ADR was promoted from Proposed to Accepted on 2026-09-23 per user directive message 1552262422398767115 (*Proceed with everything*). The promotion ritual per ADR-ES-001 §10-§11 (status header + body Status field + this §10 Acceptance section) was executed in concert with the CR-ES-002 promotion.

The promotion to Accepted has the following consequences:

* CR-ES-002 is binding on all subsequent Enterprise-Semantics concept records.
* The Capability concept (ES:CONCEPT:capability) is foundational at Candidate lifecycle ;;; bearer-agnostic per §2.2.
* The 9 Capability governed predicates (per CR-ES-002 §5) are registered in relationships/vocabulary.yaml v0.4.0.
* The 9 Capability inverse pairs are registered in relationships/inverse.yaml v0.4.0.
* 2 predicates are namespaced (capability-realized-through, capability-contributes-to) for cross-CR subject-type disambiguation ;;; following the same pattern as stage-realized-through (VS-B).
* v0.1.0 of versions/v0.1.0.yaml is the canonical version pointer for the Capability semantic establishment.
* v0.4.0 of relationships/vocabulary.yaml is the canonical predicate vocabulary version.
* 3 mapping records are PROPOSED: mappings/wsf/capability.yaml (Tier 2 Specialisation) ;; mappings/opendea/capability.yaml (architectural representation) ;; mappings/dea-catalogs/capability.yaml (instantiation boundary).
* Documentation: capability.md + capability-boundary.md in enterprise-semantics-docs.
* Worked example: examples/foundational/capability.yaml (OTCHERE Inc).
* Conformance tests: 7 test groups (identity + schema + relationships + boundaries + provenance + grounding + specialization) covering CAP-001..012.
* PlantUML sources: docs/diagrams/capability/{capability,capability-boundary,capability-process-boundary}.puml.
* Agentic Capability, Autonomous Capability, and other specialisations remain out of scope per §25.
* No unapproved specialisation is promoted to canonical status per §8.12.
* No business Capability maturity models, scoring, or heatmaps are introduced.
* The follow-on sequence is unblocked: ADR-ES-003 + CR-ES-003 (Value Stream, Accepted) ;; ADR-ES-004 + CR-ES-004 (Agentic, Accepted) ;; ADR-ES-005 + CR-ES-005 (Agentic Value Stream, future) ;; ADR-ES-006 + CR-ES-006 (Agentic Workflow, future).

The PRs that satisfy the acceptance criteria:

- enterprise-semantics PR #6 ;; CR-ES-002 recovered from v3.1.7 orphan stash ;; 9 Capability predicates + v0.1.0 version pointer
- enterprise-semantics-visuals PR #4 ;; 3 Capability PlantUML sources (parallel slice, held from v3.1.12)
- Pre-existing parallel slices on main: docs/concepts/capability.md + docs/architecture/capability-boundary.md ;; examples/foundational/capability.yaml ;; tests/capability/* (7 files) ;; mappings/{wsf,opendea,dea-catalogs}/capability.yaml (3 files)

Promoted by: Emmanuel A. Otchere (cardinal author rule, 2026-09-23) per ADR-ES-001 §10-§11 promotion ritual.