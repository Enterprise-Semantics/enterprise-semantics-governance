# ES-ADR-059: Agentic Value Stream Semantic Versioning, Evolution & Migration Framework

**Status:** Proposed
**Type:** Architecture / Semantic Governance / Versioning / Compatibility / Migration
**Date:** 2026-10-08
**Author:** Emmanuel A. Otchere (cardinal author rule, 2026-09-23)
**Decision body:** Enterprise-Semantics Architecture Review Board
**Implements:** CR-VAS-010
**Depends on:** ES-ADR-005, ES-ADR-031, ES-ADR-049, ES-ADR-051, ES-ADR-052, ES-ADR-053, ES-ADR-054, ES-ADR-055, ES-ADR-056, ES-ADR-057, ES-ADR-058

## 1. Context

The Agentic Value Stream (AVS) semantic contract now spans 8 published Change Requests (CR-VAS-002 through CR-VAS-008) plus the 1.6.0 baseline established by CR-AVS-001. Each CR has added sub-blocks to `concept.yaml`, test inventory entries to `kit/kit.yaml`, and documentation sets under `docs/`. Mappings to the World Semantic Foundation and OpenDEA carry corresponding alignment blocks per layer.

A repository of this depth, with a published semantic contract consumed by downstream implementations, requires a controlled mechanism for semantic evolution. Without one, the following risks emerge:

- **Contradictory definitions.** Two CRs in succession may add blocks whose assumptions drift away from each other.
- **Silent qualification drift.** Patch-version releases may quietly change qualification criteria without an explicit major-version signal.
- **Instance invalidation without notice.** Downstream AVS records conformant to v1.x may become non-conformant under v1.y without a manifest of which conditions changed.
- **Mapping fragmentation.** WSF and OpenDEA mappings may diverge from the AVS canonical definitions because no canonical authority schema is published.
- **Untraceable deprecations.** A field or property may be removed without a record of when it was deprecated, what replaced it, or which instances depend on it.

These risks are not hypothetical. The empirical evidence in Wave 6 showed that semantic blocks can grow with strong local coherence while losing global traceability. The fix is a versioning framework with explicit classification, compatibility dimensions, and migration classes.

## 2. Decision

Adopt CR-VAS-010 as the controlled semantic evolution mechanism for the Agentic Value Stream. CR-VAS-010 introduces the `versioning:` block in `concept.yaml` and the corresponding governance documentation set in `docs/` and `diagrams/`.

The block is additive: it does not amend the qualification, participation, evidence, measurement, maturity, governance, or architecture blocks already landed. It governs how those blocks themselves evolve over time.

The block is normative: it binds future change requests to a classification, a five-dimension compatibility assessment, a migration class, and a release manifest.

The block is testable: 18 new tests (6 positive + 6 negative + 6 boundary) using the `sv-` prefix bind the nine-class taxonomy, the SemVer policy, the spec-vs-artifact distinction, the five compatibility dimensions, the invariant evolution template, the five migration classes, and the ten anti-patterns.

## 3. Core principle

The AVS semantic contract MUST evolve deliberately, transparently, and traceably. A repository version change is not merely a software release event. It MAY change the meaning of the concept, the qualification of instances, or the interpretation of downstream architecture. Consequently, AVS MUST distinguish semantic change from implementation change and documentation change.

This principle is the foundation for all sub-decisions below.

## 4. Scope

CR-VAS-010 governs changes to:

- canonical definitions
- semantic qualification rules (CR-VAS-002)
- Agentic Participation relationships (CR-VAS-003)
- characteristics and invariants
- schemas and controlled vocabularies
- evidence and conformance requirements (CR-VAS-004)
- measurement definitions (CR-VAS-005)
- maturity and governance models (CR-VAS-006, CR-VAS-007)
- architecture patterns (CR-VAS-008)
- interoperability contracts (CR-VAS-009)
- WSF and OpenDEA mappings
- examples, documentation, and conformance fixtures

CR-VAS-010 does NOT govern:

- downstream implementation technology choices
- vendor selection
- licensing or commercial decisions
- deployment topology (those are downstream concerns, not semantic contract concerns)

## 5. Sub-decisions

### 5.1 Nine-class change taxonomy

Every proposed change MUST be assigned one or more classifications from: Editorial, Clarification, Additive, Structural, Semantic, Breaking, Deprecation, Corrective, Multi-classification. A change may have multiple classifications. Classification MUST reflect actual impact, not the size of the code or documentation diff.

Rationale: an invariant change may be a one-line patch that is semantically breaking. Diff size is a misleading signal for compatibility.

### 5.2 SemVer with semantic impact as determinant

MAJOR.MINOR.PATCH per SemVer, but with explicit per-tier rules anchored in semantic impact rather than in diff size:

- MAJOR: incompatible with the previous semantic contract (changing qualification conditions, redefining an invariant, removing a mandatory property, changing controlled vocabulary such that interpretation shifts, changing a conformance rule such that previously conformant instances become non-conformant).
- MINOR: compatible functionality or clarification added without changing existing conformant representations.
- PATCH: corrections that do not intentionally alter the semantic contract.

A qualification change MUST NOT be released as a patch (SV-INV-003).

### 5.3 Spec vs artifact version split

The repository distinguishes the version of the overall AVS specification from the version of individual artifacts. An artifact MUST NOT declare compatibility with a specification version if it changes or contradicts that specification's normative semantics.

Rationale: optional schema improvements should not imply specification changes. Conversely, a schema that contradicts a spec MUST NOT be deemed compatible with that spec.

### 5.4 Five-dimension compatibility

Compatibility MUST be evaluated across Definition, Instance, Schema, Conformance, and Mapping. A change may be schema-compatible but semantically breaking (SV-INV-008). The compatibility report MUST make that distinction explicit.

### 5.5 Five migration classes

Migration class is selected by semantic impact:

- M0: No migration (existing artifacts valid).
- M1: Mechanical (deterministic structural transformation).
- M2: Reviewed (transformation requires validation or human review).
- M3: Semantic reassessment (instances reassessed against changed qualification or invariant requirements).
- M4: Requalification required (formal reevaluation before conformance claim to the new release).

### 5.6 Eight normative invariants (SV-INV-001..008)

1. SV-INV-001: classification by impact, not diff size.
2. SV-INV-002: SemVer is a release convention, not compatibility.
3. SV-INV-003: qualification change MUST NOT be a patch.
4. SV-INV-004: invariant IDs SHOULD remain stable when meaning is stable.
5. SV-INV-005: migration transformations MUST be explicit; the repository MUST NOT silently infer missing semantic evidence.
6. SV-INV-006: no cross-repo canonical conflict without reconciliation.
7. SV-INV-007: conformant-to-one does not imply conformant-to-another.
8. SV-INV-008: schema-compat does not equal semantic-compat.

### 5.7 14-item change request checklist

Every change request MUST include: problem statement; current normative position; proposed change; semantic rationale; classification; compatibility impact; affected invariants; affected schemas; affected conformance tests; affected mappings; migration requirements; documentation changes; acceptance criteria; rollback or remediation approach.

### 5.8 Impact analysis chain

The change impact traverses: Changed Definition -> Invariants -> Qualification Rules -> Schemas -> Conformance Tests -> Architecture Patterns -> Mappings -> Examples and Documentation. The dependency graph MUST be derived from repository metadata, not maintained as a hand-drawn diagram.

## 6. Implementation

- `concept.yaml`: new `versioning:` block with 20 sub-keys, 8 normative invariants (SV-INV-001..008), and per-CR-VAS-010 boundary_assertion.
- `kit/kit.yaml`: bumped to v1.7.0; `sv_positive`, `sv_negative`, `sv_boundary` test inventory blocks; provenance now includes ES-ADR-059 and CR-VAS-010; boundary_assertions now includes `per_cr_vas_010_versioning_evolution`.
- 18 new tests (6+6+6) under `kit/sv-positive-01..06.yaml`, `kit/sv-negative-01..06.yaml`, `kit/sv-boundary-01..06.yaml`.
- 8 new documentation files under `docs/`.
- 3 new PUML diagrams under `diagrams/`.
- WSF mapping gains `versioning_alignment` block (8 WSF correspondences; 5-dimension compatibility evidence).
- OpenDEA mapping gains `versioning_alignment` block (8 OpenDEA correspondences; 5-dimension compatibility evidence).

## 7. Compatibility evidence

Per CR-VAS-010 §8, compatibility is reported across the five dimensions:

- Definition: compatible (additive block; no existing definitions change).
- Instance: compatible (no instance-shape changes).
- Schema: compatible (no schema changes; new block is additive to concept.yaml).
- Conformance: compatible (no existing test changes; 18 new sv-* tests added).
- Mapping: compatible (wsf_mapping and opendea_mapping receive new versioning_alignment blocks; existing alignment blocks unchanged).

## 8. Consequences

Positive:

- The AVS semantic contract gains an explicit, testable evolution mechanism.
- Future CRs land with a classification, a five-dimension compatibility assessment, a migration class, and a release manifest.
- WSF and OpenDEA mappings carry explicit versioning alignment anchored to SV-INV-001..008.
- The 18 new tests detect every anti-pattern catalogued in `docs/versioning-anti-patterns.md`.

Negative:

- Future CRs MUST complete the 14-item change request checklist. This is additional work per CR; the cost is offset by the long-term reduction in semantic drift and release-time rollback risk.
- Cross-repo canonical conflict reconciliation is now a binding requirement (SV-INV-006). This requires a coordination protocol across the Enterprise-Semantics repository family. The protocol is defined in `docs/versioning.md` and operationalised in `enterprise-semantics-governance`.

## 9. Alternatives considered

### 9.1 No versioning framework (status quo)

The repository continues to evolve via ad-hoc SemVer and ad-hoc release notes. Rejected: this is the failure mode the CR is designed to prevent. Cross-version re-labelling, silent qualification drift, and uncontrolled mapping divergence are observed risks.

### 9.2 SemVer-only (without explicit compatibility assessment)

Adopt MAJOR.MINOR.PATCH and treat each increment as a compatibility claim. Rejected: SV-INV-002 explicitly forbids treating SemVer as a compatibility guarantee. Compatibility MUST be assessed and evidenced.

### 9.3 Per-block independent versioning

Allow each `concept.yaml` sub-block to evolve under its own version. Rejected: this fragments the semantic contract and makes the specification vs artifact distinction impossible to maintain. The specification is the contract; the blocks are its parts.

### 9.4 Impact analysis as hand-drawn diagram only

Maintain the dependency graph as a manually-updated diagram. Rejected: CR-VAS-010 §18 explicitly requires the graph to be derived from repository metadata, not maintained as a hand-drawn diagram. The diagram in `docs/release-process.md` is illustrative only.

## 10. References

- CR-VAS-010 §1-§21: core requirements.
- SV-INV-001..008: normative invariants introduced by this ADR.
- WSF SemVer §2-§4: reference SemVer model.
- WSF Release Manifest §1-§2: machine-readable manifest.
- WSF Migration Records §3: migration record model.
- OpenDEA Change Management §3: change taxonomy.
- OpenDEA Reference Architecture §4-§10: canonical authority, invariant lifecycle, vocabulary governance, deprecation, dual-version support, dependency analysis, normative invariants.
- CR-VAS-002 through CR-VAS-009: prior CRs whose evolution this framework governs.

## 11. Adoption

This ADR is binding for the AVS specification from version 1.7.0 onwards. CR-VAS-011 (validation harness) will operationalise the anti-pattern checks against this framework.

## 12. Cardinal author

Emmanuel A. Otchere (cardinal author rule, 2026-09-23)
