# PLAN-CHANGELOG.md — Enterprise Semantics Program Plan

This log tracks every committed change to `plans/PLAN.md`. The plan-keeper cronjob
references this file's most recent entry when reconciling the live org state against
the plan.

Format follows [Keep a Changelog](https://keepachangelog.com/) semantics. Dates are
local time of the committer.

---

## [0.6.0] ; 2026-09-02 ; FND-ES-AG-002 Agentic Value Stream Semantic Grounding

### Added

- `00_inbox/FND-ES-AG-002.md` ;;; authored (16,887 bytes, dash-normalized from the start).
- `seed/FND-ES-norm-AG-002.md` ;;; identical bytes (gitignored per D-004).
- `enterprise-semantics-governance/docs/finding/0002-agentic-value-stream-semantic-grounding.md` ;;; 17,513 bytes with frontmatter, pushed to remote governance repo.
- Program board: new Finding card `[FND-ES-AG-002] Agentic Value Stream Semantic Grounding (Proposed)` (Issue #5 in `enterprise-semantics-governance`, on the board with `Item Type=Spike`, `Phase=Phase 3`, `Priority=High`, `Status=In Progress`).

### FND-ES-AG-002 ;;; working conclusion (provisional, NOT normative)

- `Agentic Value Stream` is a **Profile** of `Value Stream`, not a Specialization, pure Characteristic, or Distinct kind.
- Justification: the four agentic characteristics (bounded autonomy, AI-augmented decision-making, adaptive value-realization, human governance) are characteristics of execution, not of value-realization semantics. A Profile preserves identity, governed relationships, lifecycle, and mappings while avoiding semantic duplication.
- Candidate definition (provisional):

  > An Agentic Value Stream is a Value Stream whose realization is characterized by goal-directed execution under bounded autonomy, AI-augmented decision-making, adaptive value-realization, and human governance rather than human execution.

- Candidate relationships (provisional):

  ```text
  Agentic Value Stream profile-of Value Stream
  Agentic Value Stream realizes Value Outcome
  Agentic Value Stream enabled-by Capability
  Agentic Value Stream supported-by Process
  Agentic Value Stream executes-through Agentic Workflow
  ```

- Architectural preservation per ADR-ES-002 §22: `executes-through` is preferred over `contains` to keep value-realization (semantics) and execution-choreography (mechanism) at the right level of abstraction.

### Open questions for the consolidated review

- Does Profile carry through to the entire Agentic family (Agentic Operations, Agentic Enterprise) or is it specific to Agentic Value Stream?
- How does Agentic Value Stream map to OpenDEA metamodel constructs? (Phase 4.6.)
- How does Agentic Value Stream map to WSF Value? (Phase 4.6.)

### Updated decisions

- **D-009** updated: FND-ES-AG-002 landed. Remaining sub-findings (FND-ES-AG-003+) ;;; per-concept and per-relationship investigations for the rest of the Agentic family.

---

## [0.5.0] ; 2026-09-02 ; Path B ; ADR-ES-002 dependency accepted ; FND-ES-AG-001 authored

### Path B decision (per user, 2026-09-02)

- ADR-ES-002 marked `dependency_status: pending` (ADR-ES-001 outstanding).
- ADR-ES-001 will land alongside or after. Surfaced on every `manny-es` check-in until resolved.

### Added

- `00_inbox/FND-ES-AG-001.md` ;;; authored (14,202 bytes, dash-normalized from the start ;;; 0 em-dashes, 0 en-dashes).
- `seed/FND-ES-norm-AG-001.md` ;;; identical bytes (gitignored per D-004).
- `enterprise-semantics-governance/docs/finding/0001-agentic-semantic-grounding.md` ;;; 14,668 bytes with frontmatter, pushed to remote governance repo.
- Program board: new Finding card `[FND-ES-AG-001] Agentic Semantic Grounding (Proposed)` (Issue #4 in `enterprise-semantics-governance`, on the board with `Item Type=Spike`, `Phase=Phase 3`, `Priority=High`, `Status=In Progress`).

### FND-ES-AG-001 ;;; summary

- Establishes the **Agentic Semantic Grounding** investigation as the first substantive semantic implementation under ADR-ES-002.
- Addresses the 14 questions from ADR-ES-002 §21.
- Working hypothesis (provisional, NOT normative):
  - `Agentic != Autonomous`.
  - `Agentic Value Stream` is a specialization of `Value Stream` (per ADR-ES-002 §22).
  - `Agentic Workflow` specializes `Workflow` under agent participation.
  - `Agentic Flow` specializes `Activity / Process` under AI-driven execution.
  - `AI Agent` is an enterprise specialization of WSF `Agent` that uses AI Models.
- Initial scope: 12 Agentic concepts from ADR-ES-002 §20, plus adjacent Autonomous concepts investigated only to establish the Agentic boundary.

### Updated decisions

- **D-008** updated: Path B accepted (ADR-ES-002 dependency noted, not blocking).
- New **D-009** (open): FND-ES-AG-002+ sub-findings ;;; not yet authored. Will land incrementally as the investigation progresses.

### Verification

- `python3 scripts/plan_keeper.py` ;;; `NO_DRIFT` after commit.
- `manny-es` daily check-in will surface D-008 (ADR-ES-001 outstanding) and the active Phase 3 status.

---

## [0.4.0] ; 2026-09-02 ; ADR-ES-002 ingested

### Added

- `00_inbox/ADR-ES-002.md` ;;; verbatim (17,751 bytes, em-dashes preserved).
- `seed/ADR-ES-norm-002.md` ;;; dash-normalized (17,742 bytes, em-dash ;;; colon, en-dash ;;; semicolon). Gitignored per D-004.
- `enterprise-semantics-governance/docs/adr/0002-enterprise-semantic-model.md` ;;; dash-normalized ADR with frontmatter (17,929 bytes), pushed to remote governance repo.
- `enterprise-semantics-governance/CHANGELOG.md` ;;; v0.0.2 entry recording the ADR-ES-002 ingest.
- Program board: new Decision card `[ADR-ES-002] Enterprise Semantic Model (Proposed)` (Issue #3 in `enterprise-semantics-governance`, on the board with `Item Type=Decision`, `Phase=Phase 3`, `Priority=High`, `Status=In Progress`).
- PLAN.md ;;; v0.4.0: D-008 logged (open), Phase 3 marked in_progress, plan-keeper YAML reflects the new state.

### Open question

- ADR-ES-002 explicitly depends on ADR-ES-001. ADR-ES-001 has not been authored. Two paths:
  - **Path A:** Author ADR-ES-001 next (commit to it first), then return to implementing ADR-ES-002.
  - **Path B:** Accept ADR-ES-002 with the dependency noted in the ADR header, then author ADR-ES-001 alongside or after.
  Awaiting user decision. Default: surface on each `manny-es` check-in.

---

## [0.3.0] ; 2026-09-02 ; Dedicated sub-agent manny-es established

### Added

- `manny-es` cronjob (id `c0b35d4938af`, daily 09:00 local + on-demand, attached to session). The dedicated, named sub-agent responsible for `Enterprise-Semantics` going forward.
- Cooperation contract with `es-plan-keeper`: keeper detects drift every 15 minutes; `manny-es` consumes the reports and decides whether to fix, flag, or escalate.
- Org profile README: new "Program ownership" section naming `manny-es` and explaining the manny-es / es-plan-keeper contract.
- CODEOWNERS updated across all 9 repos: human `@emmanuel-a-otchere` as owner + agent reference block pointing at `manny-es` cronjob with fire instructions.
- Program board: new Decision card `[manny-es] Dedicated sub-agent for Enterprise-Semantics` (Issue #2 in `enterprise-semantics-governance`, on the board with `Item Type=Decision`, `Phase=Phase 0`, `Status=Done`, `Priority=High`).
- PLAN.md v0.3.0: new §5 "Sub-agent ownership" documenting the role table, hard rules, and identity surface; renumbered subsequent sections. D-007 marked resolved.

### Verification

- `cronjob list` returns `manny-es` and `es-plan-keeper` as enabled, scheduled.
- `python3 scripts/plan_keeper.py` returns `NO_DRIFT`.
- All 9 repos have CODEOWNERS referencing `manny-es`.
- Org profile renders the new section.

### Pending (awaiting user)

- Phase 3 ;;; ADR-ES-001, CR-ES-001, Finding records.

---

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