# ADR-ES-051 ; Per-Concept Repository Editorial Restructure (Drop `concept-` prefix + `;;;` prose repair)

Status: Accepted
Date: 2026-09-30
Deciders: eaojnr
Decision Type: Structural repository naming + editorial standard (amendment to ES-ADR-049 §2.1 + supersedes parts of ES-ADR-049 §2.4)
Scope: Enterprise-Semantics (org-wide, all 48 per-concept repositories + 8 central repositories)
Implements: CR-ES-051
Amends: ES-ADR-049 §2.1, §2.4

## 1. Context

Per-Concept Repo Self-Containment (ES-ADR-049) established that each concept lives in its own repository. The implementation chose a path-naming convention of `concept-<slug>`, e.g. `Enterprise-Semantics/agentic-value-stream`.

Two editorial issues have been identified:

1. **Discovery friction**: The `concept-` prefix in the URL makes each repo harder to find by name. Search, autocomplete, and direct linking all hit the prefix noise first. The convention should not require the prefix to identify the repo as a concept.
2. **Prose `;;;` damage**: Tripled-semicolon dividers were emitted in many prose artefacts (READMEs, generated docs, PLAN entries, ADRs/CRs, kit test descriptions, mapping notes, example scenarios, visual note blocks). The D-004 sweep scope covered only en/em-dashes; `;;;` was treated as a YAML literal-block separator and preserved. In prose, `;;;` is non-standard punctuation that disrupts readability.

## 2. Decision

### 2.1 Drop the `concept-` prefix from repo paths

Per-concept repositories are renamed from `Enterprise-Semantics/concept-<slug>` to `Enterprise-Semantics/<slug>`.

Discoverability is preserved through repository metadata:

- Each repo receives the GitHub topic `concept` (visible on the repo's main page).
- Each repo's `README.md` carries a landing-page badge: `Topic: concept`.
- The canonical landing page on `technehub-labs.github.io/portal/` lists all 48 repos under the `Concepts` section.

GitHub's `gh repo rename` mechanism preserves the old name as a redirect, so external links continue to resolve during transition.

### 2.2 Prose `;;;` repair

The D-004 standard is amended to also prohibit `;;;` in prose across GitHub-shipped artefacts:

- Forbidden: `;;;` in any prose context (commit messages, README body, ADR/CR body, generated docs, PLAN entries, kit test descriptions, mapping notes, example scenarios, PlantUML note blocks, PR titles).
- Preserved: `;;;` in YAML literal block values where it functions as a structural-data separator (per the established ES-AG-series YAML divider convention). These instances are non-prose structural metadata.
- Natural punctuation replaces `;;;` in prose: commas in lists, semicolons (single) for related clauses, periods between thoughts, colons before enumerated items, line breaks between paragraphs.

### 2.3 Writing-quality standard

All GitHub-shipped prose must satisfy:

- **No short ad-libs or puns.** No telegraphic phrasing.
- **Coherent paragraph flow.** Paragraphs lead into each other; transitions are explicit.
- **Crisp titles.** Titles state the document's claim or scope in concrete terms.
- **Good formatting.** Hierarchical headings, lists where appropriate, code blocks for technical content, tables for structured data, no inconsistent indentation.

## 3. Cascade (repos affected)

### 3.1 Repository renames

48 per-concept repositories:

- `concept-<slug>` -> `<slug>` for all 48 slugs.
- GitHub auto-redirects the old name.
- New repos receive `topic: concept`.

### 3.2 Reference updates (176 files in 8 central repos)

| Repo | Files with `concept-<slug>` refs |
|---|---|
| enterprise-semantics | 15 |
| enterprise-semantics-docs | 48 |
| enterprise-semantics-test-probe | 95 |
| enterprise-semantics-visuals | 1 |
| enterprise-semantics-governance | 16 |
| .github (sync workflow) | 1 |
| enterprise-semantics-mappings | 0 |
| enterprise-semantics-examples | 0 |

Plus 48 per-concept repos have internal cross-references (one README.md per repo linking to siblings).

### 3.3 Writing-quality audit

Selected artefacts receive a paragraph-flow + title-crispness + formatting pass:

- 8 central repo READMEs (one per central repo).
- 1 representative concept README per category (foundation, specialization, network, behavioral pattern, profile-realized).
- 1 representative sample of each enrichment doc type (target-architectures, assessment, measurement, capability-maturity-model).

## 4. Wave Order

1. Wave A: Source-side generation rule update (no GitHub change).
2. Wave B: Rename 48 repos via `gh repo rename`. Update all 176 + 48 internal references.
3. Wave C: Prose `;;;` sweep across all 11 repos (8 central + 48 per-concept) + WSF repos.
4. Wave D: Writing-quality audit on representative READMEs and generated docs.

## 5. Acceptance Criteria

- All 48 repos renamed (old name preserved as redirect).
- All 176 central-repo file references updated.
- All 48 per-concept repo cross-references updated.
- All `;;;` instances removed from prose.
- All `;;;` instances preserved in YAML literal-block structural separators.
- All targeted writing-quality revisions landed.
- D-004 sweep clean (no em-dash, en-dash, U+2E3B).
- Zero forbidden glyphs (now extended: `;;;` in prose).
- Cardinal author rule preserved on all commits.

## 6. Consequences

### Positive

- Repos discoverable by direct name (no prefix noise).
- Coherent, readable prose across the org.
- Discoverability via `topic: concept` is explicit.
- Establishes a durable editorial standard going forward.

### Negative

- External links may break if not honoring redirects (mitigated by GitHub's redirect mechanism).
- ~250 file edits across the org.
- ~2-4 hours of agent execution time.

### Neutral

- The old `concept-<slug>` URLs remain valid as redirects indefinitely.

## 7. Author

Emmanuel A. Otchere <emmanuel@otchere.com> (cardinal author rule, 2026-09-24).
