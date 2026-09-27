# ADR-ES-030 ; Per-Concept Repository + Test-Kit + Conformance Section Structure

Status: Proposed
Date: 2026-09-26
Deciders: eaojnr
Decision Type: Structural repository architecture
Scope: Enterprise-Semantics (org-wide)
Implements: ES-CR-030

## 1. Context

The Enterprise-Semantics org has grown to 25 concept records distributed across 6 repos with concepts, vocabulary, profiles, tests, docs, examples, and visuals centrally organized. As the concept count grows, three structural needs emerged:

1. Concept-level isolation and independent lifecycle management
2. Portable, per-concept conformance test kits with machine-readable manifests
3. A unified, generated conformance section giving org-wide auditability

Per user directive batch confirmation (2026-09-26): DP1 = B (repo per concept), DP2 = B (per-concept test kits), DP3 = C (CI-generated conformance section).

## 2. Decision

### 2.1 Per-Concept Repositories (DP1 = B)

Each governed concept receives its own repository under the Enterprise-Semantics org:

- Naming: `concept-<slug>` (e.g. `concept-agentic-culture`, `concept-agentic-ecosystem`)
- Contents: the concept YAML at repository root (`concept.yaml`) plus a README
- The concept repo is the authoritative home for that concept's definition record
- The shared vocabulary (`relationships/vocabulary.yaml`) remains in `enterprise-semantics` and is consumed by reference (shared predicates are org-wide, not per-concept)
- Profiles and version pointers remain in `enterprise-semantics` (they are release-coordination artefacts, not concept definitions)

### 2.2 Per-Concept Test Kits (DP2 = B)

Each concept's conformance tests are bundled into a test kit in `enterprise-semantics-test-probe`:

- Path: `tests/kits/<slug>/`
- Each kit contains: `kit.yaml` manifest + the concept's positive/negative/integrity tests
- The `kit.yaml` manifest declares: concept ID, base concept, boundary assertions covered, test counts by category, status
- Kits are the unit of conformance coverage audit

### 2.3 CI-Generated Conformance Section (DP3 = C)

A conformance section is generated into `enterprise-semantics-docs` at `conformance/`:

- Generated, never hand-maintained (derived data)
- Source: kit manifests + concept validator output
- Generation: CI job in `enterprise-semantics-test-probe` reads all kit manifests and validator results, renders the conformance section, and commits to the docs repo
- Contents: per-concept coverage matrix (concept x kit x status), validator results, org-wide summary

## 3. Consequences

### Positive

- Concept definitions gain independent lifecycle (versioning, branching, releases) per repo
- Test coverage is auditable per concept via kit manifests
- Conformance status is always current (CI-generated, not hand-written)
- The structure scales to the 17-candidate register backlog and beyond

### Negative / Trade-offs

- Repo count grows by 25 (eventually): more repos to govern
- Cross-concept changes (shared vocabulary) still require the central repo
- One-time migration of concept files from `enterprise-semantics/concepts/` to per-concept repos

### Mitigations

- Migration is staged: pilot wave of 5 most recent concepts, backfill in subsequent waves
- `enterprise-semantics` retains the shared vocabulary, profiles, versions, and validator; it does NOT become obsolete
- The validator reads concept records from per-concept repos (org-wide scan) once migration completes; until then it continues to validate the central copies

## 4. Pilot Wave

First 5 concept repos (most recent tranches, all with satisfied dependency gates):

- concept-agentic-culture (ES-023)
- concept-autonomous-culture (ES-024)
- concept-agentic-system (ES-025)
- concept-autonomous-system (ES-028)
- concept-agentic-ecosystem (ES-029)

Backfill waves follow for the remaining 20 concepts.

## 5. Compliance

- D-004: zero forbidden glyphs
- No inline triple-semicolon dividers in body content
- Cardinal author stamp: Emmanuel A. Otchere (cardinal author rule, 2026-09-24)

## Author

Emmanuel A. Otchere (cardinal author rule, 2026-09-24)
