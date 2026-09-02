# Changelog

All notable changes to this repository are documented in this file. Dates use
the committer's local time.

The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/) semantics.
This project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Planned

- ADR-ES-001 (organization scaffolding and initial content) ;; pending (D-008).
- CR-ES-001 ;; pending ADR-ES-001.
- Finding records for FND-ES-000 and FND-ES-001 ;; pending.
- FND-ES-AG-002+ sub-findings ;; pending (D-009). Author incrementally as the Agentic investigation progresses.
- CR-ES-AG-002+ ;;; implementation in progress. CR-ES-AG-002 lands agentic-execution profile_type + Profile record with WSF grounding. CR-ES-AG-003+ (Agentic Value Stream, Agentic Workflow, etc.) follow.

## [0.0.6] ; 2026-09-02 ; User-revised FND-ES-AG-001 + Grounding Result + CR-ES-AG-002

### Added

- `docs/finding/0001-agentic-semantic-grounding-canonical.md` ;;; user-revised canonical FND-ES-AG-001 (16,016 bytes with frontmatter, dash-normalized).
- `docs/finding/0001-agentic-semantic-grounding-grounding-result.md` ;;; FND-ES-AG-001-Grounding-Result (18,181 bytes with frontmatter, dash-normalized). Records the live WSF baseline grounding that informed the user revision.
- `docs/cr/0002-agentic-execution-profile-type.md` ;;; CR-ES-AG-002 (5,995 bytes, dash-normalized). Implements ADR-ES-AG-001 §6 CR-ES-AG-002 ;;; the agentic-execution profile_type + Profile record.

### Updated

- `docs/finding/0001-agentic-semantic-grounding.md` ;;; replaced with a stub pointing to canonical + grounding (preserves audit trail of the earlier authored version).

### Program board

- Finding card #4 ;;; commented + Status=Done (superseded by canonical).
- Finding card #9 ;;; new ;;; FND-ES-AG-001 canonical (user-revised). Status=In Progress.
- Finding card #10 ;;; new ;;; FND-ES-AG-001-Grounding-Result. Status=In Progress.

### Implementation

- CR-ES-AG-002 (commit 063ab5c on `Enterprise-Semantics/enterprise-semantics`): Profile record `agentic-execution` (Established, v1.0.0) with four governed characteristics. WSF grounding cited explicitly in provenance.

## [0.0.5] ; 2026-09-02 ; ADR-ES-AG-001 ingested (Agentic Semantic Decision)

### Added

- `docs/adr/0003-agentic-semantic-decision.md` ;;; ADR-ES-AG-001 ;;; Agentic Semantic Decision.
  Status: Proposed (awaiting human-owner acceptance). Three architectural commitments:
  (1) `Agentic` is a Profile modifier, not a new semantic kind. (2) `Agentic != Autonomous` at the Profile-characteristic level. (3) First implementation family: 11 concepts (Agentic Value Stream, Agentic Workflow, Agentic Flow, Agentic Operations, Agentic Enterprise, Agentic Capability, AI Agent, Agentic Agent, Agentic Service, Agentic Product, Agentic AI). `Agentic Culture` held back for separate investigation.
  Implementation sequence: CR-ES-AG-001+ (13 CRs).

### Updated

- FND-ES-AG-001 (card #4) and FND-ES-AG-002 (card #5) cards received comments noting they are cited by ADR-ES-AG-001, not closed.
- `docs/plan/PLAN.md` ;;; v0.7.0 (D-009 resolved, D-010 opened).
- `docs/plan/PLAN-CHANGELOG.md` ;;; v0.7.0 entry.

## [0.0.4] ; 2026-09-02 ; FND-ES-AG-002 ingested

### Added

- `docs/finding/0002-agentic-value-stream-semantic-grounding.md` ;;; FND-ES-AG-002 ;;; Agentic Value Stream Semantic Grounding.
  Status: Proposed Finding. Working conclusion: `Agentic Value Stream` is a **Profile** of `Value Stream`, not a Specialization, pure Characteristic, or Distinct kind.
  Justification: the four agentic characteristics (bounded autonomy, AI-augmented decision-making, adaptive value-realization, human governance) are characteristics of execution, not of value-realization semantics. A Profile preserves identity, governed relationships, lifecycle, and mappings while avoiding semantic duplication.
  Candidate relationships: `Agentic Value Stream profile-of Value Stream` ;; `realizes Value Outcome` ;; `enabled-by Capability` ;; `supported-by Process` ;; `executes-through Agentic Workflow`.
  Architectural preservation per ADR-ES-002 §22: `executes-through` preferred over `contains` to keep value-realization (semantics) and execution-choreography (mechanism) at the right level of abstraction.

## [0.0.3] ; 2026-09-02 ; FND-ES-AG-001 ingested (Path B for ADR-ES-002 dep)

### Added

- `docs/finding/0001-agentic-semantic-grounding.md` ;;; FND-ES-AG-001 ;;; Agentic Semantic Grounding.
  Status: Proposed Finding. Establishes the first substantive semantic investigation
  under ADR-ES-002. Addresses the 14 questions from ADR-ES-002 §21. Working
  hypothesis: Agentic != Autonomous; Agentic Value Stream is a specialization of
  Value Stream; Agentic Workflow specializes Workflow under agent participation;
  Agentic Flow specializes Activity/Process under AI-driven execution; AI Agent is
  an enterprise specialization of WSF Agent that uses AI Models.

### Updated

- `docs/adr/0002-enterprise-semantic-model.md` ;;; frontmatter updated with
  `dependency_status: pending` (Path B accepted; ADR-ES-001 outstanding).
- `docs/plan/PLAN.md` ;;; v0.5.0 (D-008 resolved via Path B; D-009 opened).
- `docs/plan/PLAN-CHANGELOG.md` ;;; v0.5.0 entry.

## [0.0.2] ; 2026-09-02 ; ADR-ES-002 ingested (dash-normalized)

### Added

- `docs/adr/0002-enterprise-semantic-model.md` ;;; ADR-ES-002 ;;; Enterprise Semantic Model.
  Status: Proposed (per the source). Establishes the semantic authority boundary
  between WSF, Enterprise-Semantics, OpenDEA, and DEA Catalogs. Defines the
  enterprise semantic scope, the concept model, relationships as first-class
  semantic objects, semantic identity, provenance, lifecycle, source-of-truth,
  specification authority, bi-directional integration, machine consumption,
  conformance, and the initial Agentic semantic implementation.

### Reference

- Verbatim source: local working folder `00_inbox/ADR-ES-002.md`.
- Dash-normalized draft: local working folder `seed/ADR-ES-norm-002.md`.

### Open question (surfaced to user)

- ADR-ES-002 explicitly depends on ADR-ES-001 (organization scaffolding and initial
  content), which has not been authored yet. Two paths:
  - **Path A:** Author ADR-ES-001 next, then return to implementing ADR-ES-002.
  - **Path B:** Accept ADR-ES-002 with a noted dependency on ADR-ES-001 and
    draft ADR-ES-001 alongside or after.

## [0.0.1] ; 2026-09-02 ; Skeleton

### Added

- README.md (purpose, ownership, status, relationship to other repos).
- CODEOWNERS (sole owner: @emmanuel-a-otchere).
- CHANGELOG.md (this file).
- .gitignore (credential, AI-model, and workspace-noise patterns).
- LICENSE (Apache-2.0).
- ADR template at `docs/adr/0000-template.md`.
- CR template at `docs/cr/0000-template.md`.
- Finding template at `docs/finding/0000-template.md`.
- `docs/plan/PLAN.md` migrated from the local working folder (Phase 0 commit).
- `docs/plan/PLAN-CHANGELOG.md` migrated alongside.