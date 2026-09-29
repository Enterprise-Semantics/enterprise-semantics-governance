# CR-ES-050 ; Per-Concept Repo Self-Containment Gap Closure (Implementation)

Status: Accepted
Date: 2026-09-30
Implements: ADR-ES-050
Amends: ES-CR-049 implementation wave (adds 4 slices)

## Promotion Metadata

- Adr: ES-ADR-050 (Accepted 2026-09-30)
- Cardinal author rule: Emmanuel A. Otchere <emmanuel@otchere.com>
- Wave structure: 4 slices (A, B, C, D)
- Slice A: Test File Mirror (up to 480 test files across 48 repos)
- Slice B: Mapping Authoring (22 repos need mappings)
- Slice C: Visual Authoring (28 repos need visuals)
- Slice D: Example Authoring (47 repos need examples)
- Goal: Achieve 48/48 self-contained repositories before release cut

## 1. Implementation Plan

### Slice A ; Test File Mirror

For each of 48 concept repositories:

1. Clone `concept-<slug>` to a working dir.
2. Copy `positive-01.yaml` through `positive-05.yaml` and `negative-01.yaml` through `negative-05.yaml` from canonical source at `enterprise-semantics-test-probe/tests/<slug>/`.
3. If canonical source has zero tests, generate the 10 tests using the 5-category taxonomy from ES-ADR-031 §4.
4. Commit with the cardinal author message and push.

### Slice B ; Mapping Authoring

For each of 22 concepts lacking mappings:

1. Author `mappings/wsf.yaml` declaring `mapping_type` and source authority.
2. Author `mappings/opendea.yaml` and `mappings/dea-catalogs.yaml` where material.
3. Commit and push per repo.

### Slice C ; Visual Authoring

For each of 28 concepts lacking visuals:

1. Author `visuals/<slug>-boundary.puml`.
2. Compile to PNG to verify syntax.
3. Commit and push per repo.

### Slice D ; Example Authoring

For each of 47 concepts lacking examples:

1. Author `examples/<slug>-reference.yaml` demonstrating boundary assertions.
2. Declare conformance level.
3. Commit and push per repo.

## 2. PR Sequence

- CR-ES-050-a: enterprise-semantics-test-probe (canonical tests update) + 48 per-concept repo pushes
- CR-ES-050-b: enterprise-semantics-mappings (canonical mappings update) + 22 per-concept repo pushes
- CR-ES-050-c: enterprise-semantics-visuals (canonical visuals update) + 28 per-concept repo pushes
- CR-ES-050-d: enterprise-semantics-examples (canonical examples update) + 47 per-concept repo pushes

## 3. Acceptance Criteria

- All 48 repos contain 11 core artefact types (or material absence acknowledged).
- Zero forbidden glyphs (D-004 sweep clean).
- Cardinal author rule preserved on all commits.

## 4. Author

Emmanuel A. Otchere <emmanuel@otchere.com> (cardinal author rule, 2026-09-24).
