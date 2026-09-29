# CR-ES-049 ; Per-Concept Repo Self-Containment (Implementation)

Status: Accepted
Date: 2026-09-30
Implements: ADR-ES-049
Amends: ES-CR-030 §2.1 distribution list

## Promotion Metadata

- Adr: ES-ADR-049 (Accepted 2026-09-30)
- Cardinal author rule: Emmanuel A. Otchere <emmanuel@otchere.com>
- Wave structure: 6 slices, parallel landing
- Slice 1: Test Kit Completion (110 missing tests for 11 zero-test concepts)
- Slice 2: Per-concept docs enrichment (29 to 48 with target-architectures + CMM + assessment + measurement)
- Slice 3: Mirror everything into 48 per-concept repos (48 PRs)
- Slice 4: CI sync workflow + GITHUB_TOKEN-only sync to per-concept repos
- Slice 5: authority-chain.md + PLAN [3.1.99] + skill write
- Slice 6: validation sweep (zero forbidden glyphs, all YAML parses, CI green)

## 1. Implementation

### 1.1 Slice 1: Test Kit Completion

For each of the 11 zero-test concepts (agentic-offering, agentic-organization, agentic-product, agentic-service, autonomous-capability, autonomous-offering, autonomous-organization, autonomous-product, autonomous-service, product, service), author 5 positive and 5 negative conformance tests in `enterprise-semantics-test-probe/tests/<slug>/`. Total: 110 new test files.

Test categories follow the 5-category taxonomy from ES-ADR-031 §4:

1. Foundational reference or specialization (positive and negative)
2. Agentic or autonomous independence (positive and negative)
3. Four-state matrix independence (positive and negative)
4. AI not required (positive and negative)
5. Cross-context or network-level materiality (positive and negative)

### 1.2 Slice 2: Per-Concept Docs Enrichment

For each concept, the docs gain 4 new sections (or 4 new files if no docs exist):

- `target-architectures.md`: 3 reference architectures that instantiate the concept at different scales.
- `capability-maturity-model.yaml`: 5-level model (Level 0 Ad-hoc to Level 4 Adaptive) with measurement criteria per level.
- `assessment.md`: assessment methodology (evidence required per level, conformance gating, assessor qualifications).
- `measurement.md`: quantitative metrics, measurement frequency, instrumentation requirements, reporting format.

### 1.3 Slice 3: Mirror to Per-Concept Repos

For each of the 48 concept repos, a single PR lands the full exhaustive layout per ADR-ES-049 §2.1. PR titles follow the established pattern: `feat: self-contain concept-<slug> ; ES-ADR-049 + CR-ES-049`. Cardinal author rule preserved on all 48 commits.

### 1.4 Slice 4: CI Sync Workflow

A new workflow in `.github` org repo: `.github/workflows/sync-concept-repos.yml`. On push to main in any of the 6 central repos, it triggers the per-concept-repo mirror. Uses only `GITHUB_TOKEN`.

### 1.5 Slice 5: Governance Documentation

`authority-chain.md` updated with structural-change section referencing ES-ADR-049 and CR-ES-049. PLAN entry [3.1.99] committed.

### 1.6 Slice 6: Validation Sweep

Run D-004 sweep, validator, all YAML parses, CI sync dry-run.

## 2. Backward Compatibility

ES-ADR-030 §2.1 is amended, not replaced. The single source of truth remains the central repos. The per-concept repo becomes a derived snapshot. Existing tooling that consumes the central repos is unaffected.

## 3. Acceptance Criteria

Per ADR-ES-049 §3.