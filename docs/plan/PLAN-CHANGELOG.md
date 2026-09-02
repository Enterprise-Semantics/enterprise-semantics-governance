# PLAN-CHANGELOG.md — Enterprise Semantics Program Plan

This log tracks every committed change to `plans/PLAN.md`. The plan-keeper cronjob
references this file's most recent entry when reconciling the live org state against
the plan.

Format follows [Keep a Changelog](https://keepachangelog.com/) semantics. Dates are
local time of the committer.

---

## [0.1.0] ; 2026-09-02 ; Phase 0 in progress

### Added

- Initial `plans/PLAN.md` authored (Phases 0;;6, repo inventory, WBS, dependency graph, plan-keeper spec, decisions log, machine-readable summary).
- `00_inbox/FND-ES-000.md` and `00_inbox/FND-ES-001.md` stored verbatim (em-dashes preserved per user directive).
- `seed/FND-ES-norm-000.md` and `seed/FND-ES-norm-001.md` dash-normalized drafts (em-dash ;;; colon, en-dash ;;; semicolon); gitignored per D-004.
- `scripts/plan_keeper.py` cronjob-driven drift detector (idempotent, read-only against GitHub).
- `.gitignore` covering credential, AI-model, and workspace-noise patterns.

### Decisions recorded (open)

- **D-001** Plan-keeper cadence: every 15 minutes + Discord drift ping (subject to user override).
- **D-002** Branch-protection bar: light during skeleton phase, tightened org-wide at Phase 3.5.
- **D-003** Orphan org `Enterprise-Concepts-Model`: untouched (user decision pending).
- **D-004** `seed/` directory: gitignored.
- **D-005** Local workspace: not published as a separate `es-workspace` repo (subject to revisit).

### Pending (awaiting user Proceed)

- Phase 1 ;;; create `.github` profile repo, author org charter, create program board.

## [0.2.0] ; 2026-09-02 ; Phase 1 + Phase 2 complete

### Phase 1 ;;; Org landing page

- `.github` profile repo created (public, Apache-2.0, charter at `profile/README.md`).
- Org description set: "Enterprise-level semantic definitions, relationships, and mappings: governed, public, machine-accessible."
- Org-level GitHub Project #1 "Enterprise Semantics Program" created with custom fields `Item Type`, `Priority`, `Phase`.
- 8 future-repo epics created in `.github` (Issues #1-#8) + 1 roadmap tracker (#9); board seeded.

### Phase 2 ;;; Domain repo skeleton

- 8 domain repos created (public, Apache-2.0, descriptive descriptions):
  - `enterprise-semantics`, `enterprise-semantics-spec`, `enterprise-semantics-governance`,
    `enterprise-semantics-docs`, `enterprise-semantics-examples`,
    `enterprise-semantics-mappings`, `enterprise-semantics-visuals`,
    `enterprise-semantics-test-probe`.
- Each seeded with: README, CODEOWNERS, CHANGELOG, .gitignore, LICENSE.
- Repo-specific extras:
  - spec: ADR template.
  - governance: ADR + CR + Finding templates + `docs/plan/PLAN.md` migrated from local.
  - mappings: schema stub.
  - visuals: 7 PlantUML architectural diagrams + render.sh.
  - test-probe: skeleton harness + tests.
- Roadmap epics #1-#8 in `.github` closed (superseded); 8 new epics created in their target repos (#1 in each) and added to the project board with `Phase=Phase 2`. Roadmap tracker (#9) closed.
- Branch protection applied to spec / governance / docs trio: 1 approving review, linear history, no force push.

### Plan-keeper

- `es-plan-keeper` cronjob (job id `434b5c9c3023`) ran successfully after Phase 1 ;;; first drift report posted to Discord Home (the report reads "REPOS_MISSING: [all 8]"). Once the keeper ticks again, it should report either NO_DRIFT or remaining drift on missing branch-protection-only repos.