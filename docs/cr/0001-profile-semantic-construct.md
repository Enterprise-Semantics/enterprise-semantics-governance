<!--
CR-ES-AG-001 ;;; Profile semantic construct

Dash-normalized: colons (:) and semicolons (;) used consistently.
Verbatim original: 00_inbox/CR-ES-AG-001.md (identical bytes; authored
dash-normalized from the start).

Status: Proposed ;;; implemented (lands with this turn's CR body).
Authored by: manny-es (the dedicated sub-agent for Enterprise-Semantics).
Date: 2026-09-02.
Depends on: ADR-ES-AG-001 (Accepted) ;;; ADR-ES-002.
Implements: ADR-ES-AG-001 §3 (Profile modifier) ;;; §6 CR-ES-AG-001.

Lands in: enterprise-semantics repo (registry/profiles/ + schema/profile.schema.json
+ conformance/check.py + docs/profile.md + CHANGELOG.md).
-->

# CR-ES-AG-001 ;;; Profile semantic construct

**Status:** Proposed ;;; implemented
**Scope:** `enterprise-semantics` repo (semantic authority repository)
**Implements:** ADR-ES-AG-001 §3 (Agentic is a Profile modifier) ;; §6 CR-ES-AG-001 (Profile semantic construct)
**Depends on:** ADR-ES-AG-001 (Accepted 2026-09-02) ;; ADR-ES-002 (Enterprise Semantic Model)
**Enables:** CR-ES-AG-002 (agentic-execution profile_type registration) ;; CR-ES-AG-003+ (per-concept Agentic records)

---

## 1. Change

Establish the **Profile semantic construct** in `enterprise-semantics` as a first-class governed semantic artifact:

1. A **Profile registry** at `registry/profiles/` holding Profile YAML records.
2. A **Profile YAML schema** at `schema/profile.schema.json` defining the structure of Profile records.
3. A **Profile base record** at `registry/profiles/_base.profile.yaml` documenting the schema and conventions.
4. A **conformance check** that validates Profile YAML records against the schema and against the Profile registry invariants.

The Profile semantic construct is the foundation for all Agentic semantic records (CR-ES-AG-003+) and is reusable for any future Profile family (e.g. Autonomous, Open, Regulated).

---

## 2. Problem

Without a governed Profile semantic construct:

- Agentic concepts land as ad-hoc YAML records without a shared pattern.
- The Profile hypothesis from ADR-ES-AG-001 §3 cannot be implemented consistently.
- Downstream consumers cannot reason about which concepts are Profiles of which base concepts.
- Cross-concept relationships (e.g. `Agentic X profile-of X`) cannot be validated.

The Profile semantic construct provides the governance scaffolding that all subsequent Agentic CRs depend on.

---

## 3. Implementation

### 3.1 Repository

`enterprise-semantics` ;;; the semantic authority repository per ADR-ES-002 §14.

### 3.2 Directory structure

```text
enterprise-semantics/
  registry/
    profiles/
      _base.profile.yaml                 ;;; documents Profile conventions + example
      agentic-execution.profile.yaml     ;;; (lands in CR-ES-AG-002)
      ...
  schema/
    profile.schema.json                  ;;; JSON Schema for Profile YAML records
  concepts/
    value-stream.yaml                    ;;; (lands in CR-ES-AG-003 for Agentic Value Stream)
    ...
  mappings/
    (lands in Phase 4.6)
  conformance/
    check.py                             ;;; reads registry + schema + concepts, validates invariants
    tests/
      test_profile_registry.py
      test_profile_schema.py
```

### 3.3 Profile YAML schema

Each Profile is a YAML record conforming to `schema/profile.schema.json`:

```yaml
# Profile record structure (canonical example)
id: ES:PROFILE:<profile-id>           ;;; stable semantic identity
canonical_name: <profile-canonical-name>
definition: <governed semantic definition>
status: Candidate                       ;;; Candidate ;; Investigating ;; Proposed ;; Established ;; Canonical ;; Mapped ;; Deprecated ;; Retired
version: 1.0.0
profile_type: <profile-type-name>       ;;; e.g. agentic-execution
characteristics:                        ;;; governed set of properties that apply when the profile is active
  - id: ES:CHAR:<characteristic-id>
    canonical_name: <characteristic-name>
    description: <governed description>
governance: enterprise-semantics         ;;; authority that governs this Profile
provenance:
  - source: <evidence-source>
    note: <evidence note>
mappings: []                             ;;; bi-directional mappings to WSF ;; OpenDEA ;; catalogs
created: 2026-09-02
```

### 3.4 Profile registry invariants

The conformance harness enforces:

- `id` is unique across all Profile records.
- `id` matches the regex `^ES:PROFILE:[a-z][a-z0-9-]*$` (per ADR-ES-002 §11, identity independent of filename).
- `status` is one of the lifecycle states (per ADR-ES-002 §13).
- `version` follows semver.
- `profile_type` is registered in `registry/profile-types.yaml` (lands in CR-ES-AG-002).
- Each characteristic `id` is unique within the Profile.
- `characteristics[].id` matches the regex `^ES:CHAR:[a-z][a-z0-9-]*$`.
- `provenance` is non-empty.
- `mappings` is a list (possibly empty).

### 3.5 JSON Schema (`schema/profile.schema.json`)

A standard JSON Schema (Draft 2020-12) defining the Profile record structure. Generated from the Profile conventions above; reviewed and committed.

### 3.6 Conformance check (`conformance/check.py`)

A Python script that:

1. Reads every YAML file in `registry/profiles/`.
2. Validates each record against `schema/profile.schema.json`.
3. Validates registry invariants in §3.4.
4. Reports drift (uniqueness violations, missing fields, schema failures).
5. Exits 0 on success, non-zero on any violation.

A test harness at `conformance/tests/test_profile_schema.py` exercises:

- A valid Profile record passes.
- A Profile with duplicate `id` fails.
- A Profile with invalid `status` fails.
- A Profile with missing `provenance` fails.
- A Profile with invalid `id` regex fails.

### 3.7 Documentation

`docs/profile.md` documents the Profile semantic construct:

- Why Profile, per ADR-ES-AG-001 §3.1.
- How to author a Profile record (the YAML structure).
- How to validate a Profile record (the conformance harness).
- How Profile records relate to concept records (e.g. `Agentic Value Stream profile-of Value Stream`).
- Profile lifecycle governance.

---

## 4. Files added

| File | Purpose |
|------|---------|
| `registry/profiles/_base.profile.yaml` | Documents Profile conventions + example |
| `schema/profile.schema.json` | JSON Schema for Profile records |
| `conformance/check.py` | Conformance harness entry point |
| `conformance/tests/test_profile_schema.py` | Test harness for Profile invariants |
| `conformance/tests/fixtures/profile-valid.yaml` | Test fixture ;; valid Profile |
| `conformance/tests/fixtures/profile-invalid-id.yaml` | Test fixture ;; invalid Profile id |
| `conformance/tests/fixtures/profile-missing-provenance.yaml` | Test fixture ;; missing provenance |
| `docs/profile.md` | Profile semantic construct documentation |
| `CHANGELOG.md` | v0.1.0 ;;; CR-ES-AG-001 entry |

---

## 5. Conformance evidence

- `python3 conformance/check.py` exits 0.
- `pytest conformance/tests/` passes.
- No registry drift detected.

---

## 6. Acceptance criteria

This CR is accepted (closed, not just Proposed) when:

1. All files in §4 land in `enterprise-semantics` main branch.
2. `python3 conformance/check.py` exits 0.
3. `pytest conformance/tests/` passes.
4. CHANGELOG.md records v0.1.0.
5. `manny-es` posts a completion summary to Discord Home.

---

## 7. Cross-references

- ADR-ES-AG-001 (depends on): https://github.com/Enterprise-Semantics/enterprise-semantics-governance/blob/main/docs/adr/0003-agentic-semantic-decision.md
- ADR-ES-002 (depends on): https://github.com/Enterprise-Semantics/enterprise-semantics-governance/blob/main/docs/adr/0002-enterprise-semantic-model.md
- Local verbatim: `/home/hermes/Projects/Enterprise-Semantics/00_inbox/CR-ES-AG-001.md`
- Local dash-normalized: `/home/hermes/Projects/Enterprise-Semantics/seed/CR-ES-norm-AG-001.md`
- Implementation repo: https://github.com/Enterprise-Semantics/enterprise-semantics