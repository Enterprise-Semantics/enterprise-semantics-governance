# CR-ES-051 ; Per-Concept Repository Editorial Restructure (Implementation)

Status: Accepted
Date: 2026-09-30
Implements: ADR-ES-051
Amends: ES-CR-049 implementation wave (extends with Wave B/C/D)

## Promotion Metadata

- Adr: ES-ADR-051 (Accepted 2026-09-30)
- Cardinal author rule: Emmanuel A. Otchere <emmanuel@otchere.com>
- Wave structure: 4 waves (A: source rule, B: rename, C: prose sweep, D: writing-quality audit)
- Goal: Editorial restructure per user directive 1554671408913715303.

## 1. Implementation Plan

### Wave A ; Source-Side Generation Rule Update

Update generation rules in:

- MEMORY.md ; add D-005 standard (`;;;` forbidden in prose; natural punctuation required).
- Skill `github-language-rule-d004` ; rename to `github-language-rule-d004-d005` and add `;;;`-prose repair rules.

This wave is the source fix: no GitHub change.

### Wave B ; Rename 48 Repos

For each of 48 per-concept repos:

1. `gh repo rename Enterprise-Semantics/<old> Enterprise-Semantics/<new> --confirm` (where old = `concept-<slug>`, new = `<slug>`).
2. Add GitHub topic `concept` to the renamed repo.
3. Update local clone's `README.md` to add the `Topic: concept` landing-page badge.

Then update 176 files across 8 central repos with `concept-<slug>` references. Also update 48 per-concept repo READMEs with internal cross-references.

### Wave C ; Prose `;;;` Sweep

Sweep `;;;` from all prose artefacts:

- 8 central repo READMEs and core markdown files.
- 48 per-concept repo READMEs.
- Generated docs in 48 per-concept repos: `docs/concept.md`, `docs/target-architectures.md`, `docs/assessment.md`, `docs/measurement.md`.
- Kit test description fields in 480 test files (48 repos x 10 tests).
- Mapping file prose fields (22 mappings).
- Example scenario fields (47 examples).
- Visual note blocks (28 PlantUML files).
- PLAN entries with prose `;;;` (preserved only in YAML literal-block structural separators).
- ADR/CR prose with `;;;` dividers.
- Commit messages across history (only forward-going).

### Wave D ; Writing-Quality Audit

Audit representative READMEs and generated docs:

- 8 central repo READMEs.
- 5 representative concept READMEs (one per category: foundation, specialization, network, behavioral pattern, profile-realized).
- 4 representative generated docs (one per enrichment type).
- Apply paragraph-flow, title-crispness, formatting consistency revisions.
- Present before/after on one file for user sign-off.

## 2. PR Sequence

- Wave A: Direct edits to MEMORY.md and skill (no PR needed).
- Wave B: 48 per-concept repo PRs (each rename + topic + README update) + 8 central repo PRs (176 file reference updates).
- Wave C: 8 central repo PRs + 48 per-concept repo PRs (prose sweep).
- Wave D: 8 central repo PRs + 5 per-concept repo PRs (writing-quality revisions).

## 3. Acceptance Criteria

- All 48 repos renamed with redirects preserved.
- All 176 + 48 internal references updated.
- All `;;;` removed from prose.
- All writing-quality revisions landed.
- Zero forbidden glyphs (—, –, ⸻, `;;;` in prose).
- Cardinal author rule preserved on all commits.

## 4. Author

Emmanuel A. Otchere <emmanuel@otchere.com> (cardinal author rule, 2026-09-24).
