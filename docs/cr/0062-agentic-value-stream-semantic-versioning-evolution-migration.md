# CR-VAS-010: Agentic Value Stream Semantic Versioning, Evolution & Migration

**Status:** Proposed
**Type:** Semantic Governance / Versioning / Compatibility / Migration
**Scope:** Canonical AVS concept, semantic assets, schemas, mappings, conformance tests, architecture patterns, and implementation profiles
**Dependencies:** CR-VAS-002 through CR-VAS-009
**Implements:** ES-ADR-059
**Date:** 2026-10-08
**Author:** Emmanuel A. Otchere (cardinal author rule, 2026-09-23)

## 1. Purpose

Establish a controlled semantic evolution mechanism for Agentic Value Stream (AVS). The CR defines how the repository evolves without creating contradictory definitions, silently changing qualification criteria, invalidating existing instances without notice, or fragmenting downstream implementations.

It governs changes to:

- canonical definitions
- semantic qualification rules
- Agentic Participation relationships
- characteristics and invariants
- schemas and controlled vocabularies
- evidence and conformance requirements
- measurement definitions
- maturity and governance models
- architecture patterns
- interoperability contracts
- WSF and OpenDEA mappings
- examples, documentation, and conformance fixtures

## 2. Core principle

The AVS semantic contract MUST evolve deliberately, transparently, and traceably.

A repository version change is not merely a software release event. It MAY change the meaning of the concept, the qualification of instances, or the interpretation of downstream architecture.

Consequently, AVS MUST distinguish semantic change from implementation change and documentation change.

## 3. Change classification

Every proposed change MUST be assigned one or more classifications.

| Classification | Description | Example |
|---|---|---|
| Editorial | Improves wording without changing meaning. | Clarifying ambiguous prose. |
| Clarification | Makes an existing rule more precise without intentionally changing its meaning. | Explaining an existing invariant. |
| Additive | Introduces an optional compatible capability. | Adding an optional evidence field. |
| Structural | Changes schema structure or relationships. | Reorganizing a schema while preserving semantics. |
| Semantic | Changes definitions, qualification, invariants, or relationship meaning. | Altering what constitutes meaningful action selection. |
| Breaking | Makes a previously valid conformant representation invalid or changes its interpretation. | Making a previously optional qualification condition mandatory. |
| Deprecation | Announces planned withdrawal of a construct or field. | Deprecating a legacy property. |
| Corrective | Fixes an inconsistency between declared semantics and actual repository artifacts. | Correcting a test manifest that misreports test coverage. |
| Multi-classification | A change may have multiple classifications. | A change to qualification may be both semantic AND breaking. |

A change may have multiple classifications. For example, a semantic change may also be breaking.

Classification MUST reflect actual impact, not the size of the code or documentation diff.

## 4. Versioning policy

Adopt semantic versioning for the published AVS specification, using MAJOR.MINOR.PATCH.

### MAJOR

Increment when a change is incompatible with the previous semantic contract.

Examples:

- changing the necessary conditions for AVS qualification
- changing the meaning of a canonical relationship
- removing a mandatory property
- redefining an invariant
- changing controlled vocabulary in a way that alters interpretation
- changing a conformance rule such that previously conformant instances become non-conformant

A major release MUST include migration guidance and an explicit impact assessment.

### MINOR

Increment when compatible functionality or clarification is added without changing the meaning of existing conformant representations.

Examples:

- adding an optional property
- introducing a new optional architecture pattern
- adding a compatible mapping type
- adding a non-breaking evidence field
- adding supplementary examples

A minor release MUST document new capabilities and any implementation actions recommended.

### PATCH

Increment for corrections that do not intentionally alter the semantic contract.

Examples:

- correcting typographical errors
- fixing broken documentation links
- correcting a schema description
- repairing a test fixture that incorrectly represents an already-defined rule

A patch release MUST NOT be used to disguise a semantic or compatibility-breaking change.

Important: SemVer is the release convention; it does not itself establish semantic compatibility. Compatibility MUST be assessed and evidenced.

## 5. Separate specification version from artifact version

The repository SHOULD distinguish the version of the overall AVS specification from the version of individual artifacts.

```yaml
specification:
  id: AVS
  version: "1.0.0"
artifact:
  id: avs-qualification-schema
  version: "1.1.0"
  specification_version: "1.0.0"
```

This allows an optional schema improvement without implying that the entire semantic specification has changed.

However, an artifact MUST NOT declare compatibility with a specification version if it changes or contradicts that specification's normative semantics.

## 6. Canonical semantic authority

The repository MUST identify the authoritative source for each semantic asset.

For each artifact, record:

- canonical identifier
- authoritative repository or location
- artifact version
- specification version
- status
- owner or steward
- dependencies
- compatibility declaration
- supersession history

If the Enterprise-Semantics repository family is the canonical source of truth, a concept-specific repository MUST clearly identify whether its content is authoritative, a maintained distribution, or a derived artifact.

Multiple repositories MUST NOT independently evolve conflicting canonical definitions without an explicit reconciliation mechanism.

## 7. Normative versus informative changes

Every change MUST identify whether it affects normative semantics or informative material.

Normative material includes:

- definitions
- required conditions
- invariants
- controlled vocabularies
- qualification rules
- mandatory schema constraints
- conformance requirements

Informative material includes:

- explanatory examples
- optional guidance
- illustrative diagrams
- non-binding implementation suggestions

Changing informative material can still expose a semantic contradiction. Informative status MUST NOT be used to evade review when an example implicitly changes the meaning of a normative rule.

## 8. Semantic compatibility

Compatibility MUST be evaluated against at least five dimensions:

1. Definition compatibility: does the meaning remain stable?
2. Instance compatibility: can existing AVS records still be interpreted?
3. Schema compatibility: can existing representations still be parsed and validated?
4. Conformance compatibility: do previously conformant instances retain their status under the new rules?
5. Mapping compatibility: do mappings to WSF, OpenDEA, and other external models retain their intended meaning?

A change may be schema-compatible but semantically breaking. The compatibility report MUST make that distinction explicit.

## 9. Qualification rule changes

Changes to CR-VAS-002 qualification conditions require heightened review.

The change proposal MUST state:

- which qualification conditions are affected
- whether previously conformant instances remain conformant
- whether previously non-conformant instances may now qualify
- whether evidence requirements change
- whether negative and boundary tests change
- whether downstream mappings or architecture patterns change

A change that alters qualification criteria MUST NOT be released as a patch.

Where the change is breaking, the release MUST include a major-version increment or an explicitly approved equivalent versioning policy.

## 10. Invariant evolution

Each invariant MUST have:

- a stable identifier
- a normative statement
- a rationale
- an effective specification version
- a status
- a test or verification method where applicable

```yaml
invariant:
  id: AVS-INV-018
  statement: Agent existence alone is insufficient to establish AVS qualification.
  status: active
  introduced_in: "1.0.0"
  verification:
    - AVS-QT-N03
```

Invariant identifiers SHOULD remain stable across releases when their meaning remains stable.

If an invariant's meaning changes materially, the repository MUST document the change explicitly rather than silently reusing its identifier.

## 11. Controlled vocabulary evolution

Controlled vocabularies MUST define how values are added, deprecated, renamed, or removed.

```yaml
vocabulary:
  id: avs-agentic-scope
  version: "1.0.0"
  values:
    - id: decision
      status: active
    - id: execution
      status: active
    - id: cross_stage
      status: active
```

Rules:

- New compatible values may be introduced additively.
- Renaming a value MUST preserve its identity through an explicit alias or migration mapping where appropriate.
- Removing a value requires a deprecation and migration policy.
- A value MUST NOT be redefined to mean something materially different.
- Unknown values MUST be handled according to the consuming schema's declared extensibility policy.

## 12. Deprecation policy

Deprecation SHOULD follow a documented lifecycle:

Active -> Deprecated -> Retired

Each deprecated artifact or property MUST document:

- reason for deprecation
- version in which deprecation was introduced
- replacement, if one exists
- compatibility implications
- migration instructions
- earliest intended removal version

Deprecation MUST NOT imply immediate invalidity unless the release explicitly states that the item is no longer accepted.

## 13. Migration model

Migration MUST preserve traceability between the old and new representations.

```yaml
migration:
  id: AVS-MIG-001
  from_specification: "1.x"
  to_specification: "2.0.0"
  affected_artifacts:
    - qualification-schema
    - evidence-schema
  transformations:
    - source_field: legacy_field
      target_field: replacement_field
      transformation: explicit_mapping
  semantic_review_required: true
  automated: false
```

Migration transformations MUST be explicit.

The repository MUST NOT silently infer missing semantic evidence merely to make legacy instances pass a newer conformance suite.

## 14. Migration classes

Support the following migration classes:

- M0: No migration. Existing artifacts remain valid.
- M1: Mechanical. Deterministic structural transformation with no semantic reinterpretation.
- M2: Reviewed. Transformation requires validation or human review.
- M3: Semantic reassessment. Affected instances must be reassessed against changed qualification or invariant requirements.
- M4: Requalification required. The change requires formal reevaluation before the instance can claim conformance to the new release.

The class MUST be selected based on semantic impact, not implementation convenience.

## 15. Dual-version support

During a major-version transition, the repository MAY support two specification versions concurrently.

If so, it MUST declare:

- supported versions
- conformance rules for each version
- migration expectations
- end-of-support dates or criteria
- treatment of cross-version mappings

An instance conformant to one version MUST NOT automatically be labelled conformant to another.

## 16. Release manifest

Each release SHOULD include a machine-readable manifest.

```yaml
release:
  specification: AVS
  version: "1.1.0"
  status: released
  previous_version: "1.0.0"
  compatibility:
    semantic: compatible
    schema: compatible
    conformance: compatible
  changes:
    - id: AVS-CHG-001
      classification: additive
      affected_artifacts:
        - measurement-schema
  migration:
    required: false
    guide: null
```

Compatibility values MUST be justified by the release review, not automatically inferred from the version number.

## 17. Change request requirements

Every semantic change request MUST include:

1. Problem statement.
2. Current normative position.
3. Proposed change.
4. Semantic rationale.
5. Classification.
6. Compatibility impact.
7. Affected invariants.
8. Affected schemas.
9. Affected conformance tests.
10. Affected mappings.
11. Migration requirements.
12. Documentation changes.
13. Acceptance criteria.
14. Rollback or remediation approach where appropriate.

## 18. Repository and downstream impact analysis

A change-impact assessment SHOULD traverse dependencies from the changed artifact to affected assets.

```text
Changed Definition
  -> Invariants
    -> Qualification Rules
      -> Schemas
        -> Conformance Tests
          -> Architecture Patterns
            -> Mappings
              -> Examples & Documentation
```

The actual dependency graph MUST be derived from repository metadata and references rather than maintained only as a manually written diagram.

## 19-21. Acceptance criteria, Definition of Done, Strategic rationale

The acceptance criteria, definition of done, and strategic rationale are reproduced verbatim from the CR-VAS-010 brief:

### 19. Acceptance criteria

- Semantic versioning policy is documented.
- Specification and artifact versions are distinguished.
- Canonical semantic authority is explicit.
- Change classifications are defined.
- Normative and informative assets are distinguished.
- Compatibility dimensions are defined.
- Qualification changes receive heightened review.
- Invariant identifiers and histories are managed.
- Controlled vocabulary evolution is governed.
- Deprecation lifecycle is documented.
- Migration classes are defined.
- Migration records are machine-readable.
- Release manifests are machine-readable.
- Cross-version conformance is explicitly controlled.
- Change requests include downstream impact analysis.
- CI checks version and reference consistency.
- Documentation matches the release manifest.

### 20. Definition of Done

CR-VAS-010 is complete when a maintainer can determine:

- what changed
- why it changed
- which semantic contract applies
- whether existing instances remain valid
- which artifacts require migration
- whether conformance must be reassessed
- which downstream assets are affected

The repository MUST be able to evolve without silently changing the meaning of AVS.

### 21. Strategic rationale

CR-VAS-010 establishes semantic continuity across time.

Without it, a repository may have rigorous qualification and conformance rules today yet gradually lose reliability as definitions, schemas, and examples change independently.

The objective is not to prevent semantic evolution. It is to ensure that evolution is deliberate, explainable, testable, and traceable.

## 22. Boundary assertion (Wave 7 landing)

Per CR-VAS-010, the AVS semantic contract MUST evolve deliberately, transparently, and traceably. Semantic compatibility MUST be assessed across five dimensions. Migration transformations MUST be explicit. The compatibility report MUST distinguish schema-compatible changes from semantically breaking changes.

## 23. Cardinal author

Emmanuel A. Otchere (cardinal author rule, 2026-09-23)
