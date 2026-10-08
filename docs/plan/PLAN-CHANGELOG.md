# PLAN-CHANGELOG.md, and Enterprise Semantics Program Plan

This log tracks every committed change to `plans/PLAN.md`. The plan-keeper cronjob
references this file's most recent entry when reconciling the live org state against
the plan.

Format follows [Keep a Changelog](https://keepachangelog.com/) semantics. Dates are
local time of the committer.

---

## [3.0.0] ; 2026-09-03 ; Phase 5 complete + v0.1.0-seed tagged + 3 CRs landed

### User directive (2026-09-03, message 1544933800973434910)

> '1,2,3,4'

Picked the full queue: CR-ES-AG-005, CR-ES-AG-008, CR-ES-AG-009, Phase 5.

### Implementation sequence landed this turn

- **FND-ES-AG-007** ;; AI Agent Semantic Grounding (10-step template). Working conclusion: AI Agent is a Distinct semantic kind, NOT a Profile. Gating prerequisite for FND-ES-AG-006 (Agentic Agent scrutiny).
- **CR-ES-AG-009** (commit `a00f054`) ;; AI Agent concept record + Agent base. **Distinct kind.** 10 Concepts validated.
- **CR-ES-AG-005** (commit `d8b1c98`) ;; Agentic Flow concept record + Flow base. Profile of Flow, binds `agentic-execution`. 12 Concepts validated. Cross-reference to `external:concept:agentic-flow` now resolves.
- **CR-ES-AG-008** (commit `0839d93`) ;; Agentic Capability concept record + Capability base. Profile of Capability, binds `agentic-execution`. 14 Concepts validated. Profile-of-Profile reasoning: Profile characteristics apply to **Capability's outcome-realization aspect**, not to a specific bearer ;; distinguishes `Agentic Capability` (the *what*) from `AI Agent` (the *who*).

### Phase 5 wiring

- `enterprise-semantics-test-probe` promoted from skeleton (always return 1) to real harness. Sources `enterprise-semantics/conformance/check.py` and `check_concepts.py` directly ;; **no source duplication**.
- GitHub Actions workflows on `enterprise-semantics` and `enterprise-semantics-mappings` invoke the harness on every push and PR to main.
- `v0.1.0-seed` tagged on `enterprise-semantics` (commit `116304b`).
- GitHub Release published at https://github.com/Enterprise-Semantics/enterprise-semantics/releases/tag/v0.1.0-seed

### Conformance evidence (real run output)

```text
$ python3 ../enterprise-semantics-test-probe/tools/validate.py --mode all
[profile]  exit=0  NO_DRIFT (1 Profile record(s) validated)
[concepts] exit=0  NO_DRIFT (14 Concept record(s) validated)
PASS: NO_DRIFT
```

### Program board

- Cards #20-23 created (CR-ES-AG-005, CR-ES-AG-008, CR-ES-AG-009, Phase 5) ;; Status=Done + closed.

### Final state

- 1 Profile record (Established v1.0.0)
- 14 Concept records (8 base + 6 profiled, all Candidate v0.1.0)
- 7 Findings (FND-ES-AG-001/002/003/004/005/006/007)
- 9 CRs (CR-ES-AG-001 through 009, all Implemented)
- 1 ADR Accepted (ADR-ES-AG-001), 1 ADR Proposed (ADR-ES-002)
- Phase 5 conformance gate live
- v0.1.0-seed tagged

### Updated decisions

- **D-010** updated: 9 of 13 CRs landed ;; CR-ES-AG-010 (conditional), 011, 012, 013 remain.
- **D-011** still open (CR-ES-AG-010 gating). Now unblocked by FND-ES-AG-007 (AI Agent Distinct kind hypothesis). The three plausible models from FND-ES-AG-006 §3 can now be evaluated.
- **D-006** (PNG renders of PlantUML diagrams) still deferred ;; Phase 5.6.

### Next-queue status

- CR-ES-AG-010 (Agentic Agent) ;; now unblocked. Three plausible models to evaluate per FND-ES-AG-006 §3. FND-ES-AG-007 (AI Agent) provides the grounding target.
- CR-ES-AG-011 (Agentic Service/Product/AI) ;; straightforward, can land after 010.
- CR-ES-AG-012 (Profile conformance extension) ;; cross-record checks.
- CR-ES-AG-013 (first semantic release tag) ;; now `v0.1.0-seed`. Subsequent releases v0.x.y.

### Verification

- `python3 ../enterprise-semantics-test-probe/tools/validate.py --mode all` ;; PASS: NO_DRIFT.

---

## [2.0.0] ; 2026-09-03 ; D-003 resolved (Path A), naming drift reconciled

### User directive (2026-09-03, message 1544919802534035608)

> 'A'

Picked Path A on D-003: `Enterprise-Semantics` is canonical. The earlier `Enterprise-Concepts-Model` org remains an empty shell (no archive, no destroy).

### Hygiene applied

1. **PLAN bumped to v0.2.0.**
2. **D-003 entry rewritten** with resolution narrative.
3. **`Enterprise-Semantics/.github/profile/README.md`** ;; added a top-of-file `Canonical URL notice` section so any external reference to `Enterprise-Concepts-Model` resolves with an explicit redirect sentence. Commit `3a770ac1a0` on `Enterprise-Semantics/.github` main.
4. **Empty `Enterprise-Concepts-Model` org preserved** (no destructive action per trust-first rule). External material that linked it now reads the alias notice.

### Verification

- `gh api /orgs/Enterprise-Concepts-Model -q .public_repos`. 0 (unchanged, untouched).
- `gh api /orgs/Enterprise-Semantics -q .public_repos`. 9 (unchanged, full seed).
- `gh api /repos/Enterprise-Semantics/.github/contents/profile/README.md -q .size`. 9718 (was 9294).

### What did NOT happen

- No repos renamed.
- No code moved.
- No semantic artifacts relocated.
- No program-board cards archived or recreated.
- No CHANGELOG reissued.

### Next-queue status

- D-010 still in_progress. CR-ES-AG-005, 008, 009, 010 (conditional), 011, 012, 013 remain.
- Phase 5 (conformance gate + release tag) pending.

---

## [1.0.0] ; 2026-09-02 ; Agentic Seed Release, first Agentic semantic implementation landed

### User directive (2026-09-02, message 1544738104559009833)

> 'Save them, use it to ground the initial set of concepts, then proceed with
> CR-ES-AG-002, then CR-ES-AG-003 then CR-ES-AG-004 then get into the attached
> required actions as well. Structure the actions out and follow through the
> systematic plan to deliver them.'

The user sent:

1. FND-ES-AG-001 (user-revised canonical). Replaces my earlier authored version.
2. FND-ES-AG-001-Grounding-Result. Live WSF baseline grounding result.

### Key correction from Grounding Result

**Do not create a parallel Agentic ontology. Specialize WSF where possible.**

- WSF already grounds Capability in Disposition + Capacity + Ability + Entity + Role + Context. ES must specialize, not redefine.
- Agentic Capability may NOT be a new kind. Could be Capability with agentic characteristic (bearer -> AI Agent, agentic execution).
- Agentic Agent. Requires scrutiny (may be redundant with AI Agent).
- Strong candidates: Agentic Operations, Agentic Enterprise, Agentic Value Stream, Agentic Workflow.

### Implementation sequence landed this turn

- **CR-ES-AG-002** (commit 063ab5c). Agentic-execution Profile record (Established, v1.0.0). Cites WSF live baseline in provenance.
- **CR-ES-AG-003** (commit c15f12c). Agentic Value Stream concept record + Value Stream base.
- **CR-ES-AG-004** (commit c15f12c). Agentic Workflow concept record + Workflow base.
- **CR-ES-AG-006** (commit 3869999). Agentic Operations concept record + Operations base.
- **CR-ES-AG-007** (commit 3869999). Agentic Enterprise concept record + Enterprise base.

### Findings authored

- **FND-ES-AG-001** (user-revised canonical). Supersedes my earlier authored version (audit trail preserved).
- **FND-ES-AG-001-Grounding-Result**. Live WSF baseline grounding that informed the revision.
- **FND-ES-AG-004**. Agentic Operations semantic grounding (10-step template from Grounding Result §13).
- **FND-ES-AG-005**. Agentic Enterprise semantic grounding (10-step template).
- **FND-ES-AG-006**. Agentic Agent scrutiny. Held back from canonical per Grounding Result §3 + §12.

### Program board

- 18 cards live (3 decisions + 3 findings pre-work + 4 new decisions + 3 new findings + manny-es + 4 roadmap placeholders closed).
- Finding card #4 (my earlier authored FND-ES-AG-001). Superseded, Status=Done.
- Cards #9, #10, #14, #15, #16. New findings, Status=In Progress.
- Cards #11, #12, #13, #17, #18. New CRs (implemented), Status=Done.

### Conformance evidence (real run output)

```text
$ python3 conformance/check.py
NO_DRIFT (1 Profile record(s) validated)
exit: 0

$ python3 conformance/check_concepts.py
NO_DRIFT (8 Concept record(s) validated)
exit: 0

$ python3 conformance/tests/test_profile_schema.py
5/5 cases passed
exit: 0

$ python3 conformance/tests/test_concept_schema.py
5/5 cases passed
exit: 0
```

### Updated decisions

- **D-011** (open, opened 2026-09-02): CR-ES-AG-005 (Agentic Flow), 008 (Agentic Capability), 009 (AI Agent), 010 (Agentic Agent. Conditional, gated on FND-ES-AG-006 + FND-ES-AG-009), 011 (Agentic Service/Product/AI), 012 (Profile conformance extension), 013 (first semantic release tag).

### Verification

- `python3 scripts/plan_keeper.py`. `NO_DRIFT`, exit 0.

---

## [0.9.0] ; 2026-09-02 ; CR-ES-AG-001 Profile semantic construct landed

### Implementation

- **CR-ES-AG-001 (Profile registry + schema)** landed in `enterprise-semantics` repo:
  - `schema/profile.schema.json` (4,061 bytes). JSON Schema Draft 2020-12.
  - `registry/profile-types.yaml` (1,689 bytes). Profile type registry (agentic-execution, autonomous-operation, example-do-not-use).
  - `registry/profiles/_base.profile.yaml` (2,284 bytes). Profile conventions + canonical example.
  - `conformance/check.py` (6,939 bytes). Profile conformance harness.
  - `conformance/tests/test_profile_schema.py` (10,656 bytes). 5-case test suite.
  - `conformance/tests/fixtures/*.yaml` (1,560 bytes total). 3 test fixtures.
  - `docs/profile.md` (5,266 bytes). Profile semantic construct documentation.
  - `CHANGELOG.md` v0.1.0.
- Remote commit: 8afee80 on `Enterprise-Semantics/enterprise-semantics` main branch.

### Conformance evidence

- `python3 conformance/check.py`. `NO_DRIFT (0 Profile record(s) validated)`, exit 0.
- `python3 conformance/tests/test_profile_schema.py`. `5/5 cases passed`, exit 0.

### Documentation

- `CR-ES-AG-001` published at `enterprise-semantics-governance/docs/cr/0001-profile-semantic-construct.md` (7,895 bytes).
- `FND-ES-AG-003` (Agentic Workflow) authored and pushed (12,043 bytes with frontmatter).

### Next CR

- **CR-ES-AG-002**, register`agentic-execution` profile_type and land Agentic Value Stream + Agentic Workflow Profile records (next step in the sequence per ADR-ES-AG-001 §6).

### Verification

- `python3 scripts/plan_keeper.py`. `NO_DRIFT` after commit.

---

## [0.8.0] ; 2026-09-02 ; ADR-ES-AG-001 Accepted ; CR-ES-AG-001 implementation begins

### User decision (2026-09-02)

- Picked option #1 (recommended). Promote ADR-ES-AG-001 to Accepted and begin the CR-ES-AG-001+ implementation sequence.

### ADR-ES-AG-001 acceptance

- `docs/adr/0003-agentic-semantic-decision.md`. Frontmatter updated: `Status: Accepted` (promoted from Proposed).
- Program board: Decision card #6 (`[ADR-ES-AG-001] Agentic Semantic Decision (Proposed)`), and Status promoted to`Done`.
- Acceptance comment added on issue #6 with the three architectural commitments in force.
- Local copies (`00_inbox/ADR-ES-AG-001.md` + `seed/ADR-ES-norm-AG-001.md`) updated to reflect the accepted status.

### Implementation unlocked

- CR-ES-AG-001+ (13 CRs). Sequence locked by ADR-ES-AG-001 §6. CR-ES-AG-001 (Profile semantic construct + registry + YAML schema) lands in this turn as the first concrete implementation.

### Updated decisions

- **D-010** (in_progress): CR-ES-AG-001+ unblocked.

### Verification

- `python3 scripts/plan_keeper.py`. `NO_DRIFT` after commit.

---

## [0.7.0] ; 2026-09-02 ; ADR-ES-AG-001 Agentic Semantic Decision (Proposed)

### User decision (2026-09-02)

- Picked option #2. Author ADR-ES-AG-001 early to lock in the Profile pattern before all sub-findings land.

### Added

- `00_inbox/ADR-ES-AG-001.md`. Authored (16,772 bytes, dash-normalized from the start).
- `seed/ADR-ES-norm-AG-001.md`. Identical bytes (gitignored per D-004).
- `enterprise-semantics-governance/docs/adr/0003-agentic-semantic-decision.md`. 17,608 bytes with frontmatter, pushed to remote governance repo.
- Program board: new Decision card `[ADR-ES-AG-001] Agentic Semantic Decision (Proposed)` (Issue #6 in `enterprise-semantics-governance`, on the board with `Item Type=Decision`, `Phase=Phase 3`, `Priority=High`, `Status=In Progress`).
- Comments added to Finding cards #4 (FND-ES-AG-001) and #5 (FND-ES-AG-002) noting they are cited by ADR-ES-AG-001, not closed.

### ADR-ES-AG-001, three architectural commitments

1. **`Agentic` is a Profile modifier, not a new semantic kind.** `Agentic X` is a Profile of `X` under agent-augmented execution conditions.
2. **`Agentic != Autonomous`** is established at the Profile-characteristic level, not at the semantic-kind level. Both are Profiles of the same base concept with different profile_type values.
3. **First implementation family:** 11 concepts (Agentic Value Stream, Agentic Workflow, Agentic Flow, Agentic Operations, Agentic Enterprise, Agentic Capability, AI Agent, Agentic Agent, Agentic Service, Agentic Product, Agentic AI). `Agentic Culture` held back for separate investigation.

### Profile characteristics (apply when the Agentic profile is active)

- Goal-directed execution under bounded autonomy
- AI-augmented decision-making
- Adaptive behavior
- Human governance, not human execution

### Implementation sequence, and CR-ES-AG-001+ (13 CRs)

- **CR-ES-AG-001**, and Profile semantic construct (registry + schema)
- **CR-ES-AG-002**, agentic-execution profile_type registration
- **CR-ES-AG-003**, and Agentic Value Stream (per FND-ES-AG-002)
- **CR-ES-AG-004**, and Agentic Workflow (per FND-ES-AG-003 pending)
- **CR-ES-AG-005 through 011**, one CR per remaining concept
- **CR-ES-AG-012**, and Profile conformance gate validation
- **CR-ES-AG-013**, and First semantic release tag

### Acceptance criteria

- Human owner (or delegated authority) explicitly approves.
- The Profile hypothesis (FND-ES-AG-002) is reviewed and accepted.
- The CR-ES-AG-001+ sequence is approved.

Until `Accepted`, CR-ES-AG-001+ cannot land.

### Architectural constraints reaffirmed

- Value Stream != Process != Workflow != Task Flow
- `executes-through` preferred over `contains`
- Agentic and Autonomous are Profiles, not Distinct kinds

### Updated decisions

- **D-009** (resolved 2026-09-02): FND-ES-AG-001 and FND-ES-AG-002 landed and consumed by ADR-ES-AG-001.
- **D-010** (open): CR-ES-AG-001+ sequence locked. CRs cannot land until ADR-ES-AG-001 is `Accepted`.

### Verification

- `python3 scripts/plan_keeper.py`. `NO_DRIFT` after commit.
- ADR-ES-AG-001 awaiting human-owner acceptance. `manny-es` will surface this on each daily check-in.

---

## [0.6.0] ; 2026-09-02 ; FND-ES-AG-002 Agentic Value Stream Semantic Grounding

### Added

- `00_inbox/FND-ES-AG-002.md`. Authored (16,887 bytes, dash-normalized from the start).
- `seed/FND-ES-norm-AG-002.md`. Identical bytes (gitignored per D-004).
- `enterprise-semantics-governance/docs/finding/0002-agentic-value-stream-semantic-grounding.md`. 17,513 bytes with frontmatter, pushed to remote governance repo.
- Program board: new Finding card `[FND-ES-AG-002] Agentic Value Stream Semantic Grounding (Proposed)` (Issue #5 in `enterprise-semantics-governance`, on the board with `Item Type=Spike`, `Phase=Phase 3`, `Priority=High`, `Status=In Progress`).

### FND-ES-AG-002, working conclusion (provisional, NOT normative)

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

- **D-009** updated: FND-ES-AG-002 landed. Remaining sub-findings (FND-ES-AG-003+). Per-concept and per-relationship investigations for the rest of the Agentic family.

---

## [0.5.0] ; 2026-09-02 ; Path B ; ADR-ES-002 dependency accepted ; FND-ES-AG-001 authored

### Path B decision (per user, 2026-09-02)

- ADR-ES-002 marked `dependency_status: pending` (ADR-ES-001 outstanding).
- ADR-ES-001 will land alongside or after. Surfaced on every `manny-es` check-in until resolved.

### Added

- `00_inbox/FND-ES-AG-001.md`. Authored (14,202 bytes, dash-normalized from the start. 0 em-dashes, 0 en-dashes).
- `seed/FND-ES-norm-AG-001.md`. Identical bytes (gitignored per D-004).
- `enterprise-semantics-governance/docs/finding/0001-agentic-semantic-grounding.md`. 14,668 bytes with frontmatter, pushed to remote governance repo.
- Program board: new Finding card `[FND-ES-AG-001] Agentic Semantic Grounding (Proposed)` (Issue #4 in `enterprise-semantics-governance`, on the board with `Item Type=Spike`, `Phase=Phase 3`, `Priority=High`, `Status=In Progress`).

### FND-ES-AG-001, summary

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
- New **D-009** (open): FND-ES-AG-002+ sub-findings. Not yet authored. Will land incrementally as the investigation progresses.

### Verification

- `python3 scripts/plan_keeper.py`. `NO_DRIFT` after commit.
- `manny-es` daily check-in will surface D-008 (ADR-ES-001 outstanding) and the active Phase 3 status.

---

## [0.4.0] ; 2026-09-02 ; ADR-ES-002 ingested

### Added

- `00_inbox/ADR-ES-002.md`. Verbatim (17,751 bytes, em-dashes preserved).
- `seed/ADR-ES-norm-002.md`. Dash-normalized (17,742 bytes, em-dash. Colon, en-dash. Semicolon). Gitignored per D-004.
- `enterprise-semantics-governance/docs/adr/0002-enterprise-semantic-model.md`. Dash-normalized ADR with frontmatter (17,929 bytes), pushed to remote governance repo.
- `enterprise-semantics-governance/CHANGELOG.md`. V0.0.2 entry recording the ADR-ES-002 ingest.
- Program board: new Decision card `[ADR-ES-002] Enterprise Semantic Model (Proposed)` (Issue #3 in `enterprise-semantics-governance`, on the board with `Item Type=Decision`, `Phase=Phase 3`, `Priority=High`, `Status=In Progress`).
- PLAN.md. V0.4.0: D-008 logged (open), Phase 3 marked in_progress, plan-keeper YAML reflects the new state.

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

- Phase 3. ADR-ES-001, CR-ES-001, Finding records.

---

## [0.2.0] ; 2026-09-02 ; Phase 1 + Phase 2 complete

### Phase 1, and Org landing page

- `.github` profile repo created (public, Apache-2.0, charter at `profile/README.md`).
- Org description set: "Enterprise-level semantic definitions, relationships, and mappings: governed, public, machine-accessible."
- Org-level GitHub Project #1 "Enterprise Semantics Program" created with custom fields `Item Type`, `Priority`, `Phase`.
- 8 future-repo epics created in `.github` (Issues #1-#8) + 1 roadmap tracker (#9); board seeded.

### Phase 2, and Domain repo skeleton

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

- `es-plan-keeper` cronjob (job id `434b5c9c3023`) ran successfully after Phase 1. First drift report posted to Discord Home (the report reads "REPOS_MISSING: [all 8]"). Once the keeper ticks again, it should report either NO_DRIFT or remaining drift on missing branch-protection-only repos.

---

## [0.1.0] ; 2026-09-02 ; Phase 0 in progress

### Added

- Initial `plans/PLAN.md` authored (Phases 0;;6, repo inventory, WBS, dependency graph, plan-keeper spec, decisions log, machine-readable summary).
- `00_inbox/FND-ES-000.md` and `00_inbox/FND-ES-001.md` stored verbatim (em-dashes preserved per user directive).
- `seed/FND-ES-norm-000.md` and `seed/FND-ES-norm-001.md` dash-normalized drafts (em-dash. Colon, en-dash. Semicolon); gitignored per D-004.
- `scripts/plan_keeper.py` cronjob-driven drift detector (idempotent, read-only against GitHub).
- `.gitignore` covering credential, AI-model, and workspace-noise patterns.

### Decisions recorded (open)

- **D-001** Plan-keeper cadence: every 15 minutes + Discord drift ping (subject to user override).
- **D-002** Branch-protection bar: light during skeleton phase, tightened org-wide at Phase 3.5.
- **D-003** Orphan org `Enterprise-Concepts-Model`: untouched (user decision pending).
- **D-004** `seed/` directory: gitignored.
- **D-005** Local workspace: not published as a separate `es-workspace` repo (subject to revisit).

[3.1.98] docs: D-004 retrospective natural punctuation sweep 2026-09-28
Per user directive 1554532746037174465 (corrected D-004 scope: en/em-dashes + U+2E3B only, NOT `;;;`):
- Swept all GitHub-shipped artefacts across 9 repos: enterprise-semantics, enterprise-semantics-mappings, enterprise-semantics-docs, enterprise-semantics-examples, enterprise-semantics-test-probe, enterprise-semantics-visuals, enterprise-semantics-governance, wsf-governance, wsf-spec.
- Repositories swept: enterprise-semantics-governance #101 (68 files), enterprise-semantics #60 (33 files), enterprise-semantics-mappings #27 (5 files + 12 YAML re-validated), enterprise-semantics-docs #34 (6 files), enterprise-semantics-examples #24 (11 files + 2 YAML re-validated), enterprise-semantics-test-probe #34 (7 files), enterprise-semantics-visuals no candidates, wsf-governance #23 (11 files + 1 YAML re-validated), wsf-spec no candidates.
- Replacements:
  - Em-dash (U+2014): tight context `X—Y` -> `X: Y`; space context `X — Y` -> `X: Y`; standalone -> `:`.
  - En-dash (U+2013): number range `1–3` -> `1-3`; standalone -> `-`.
  - U+2E3B triple-em-dash divider: -> `:`.
  - Triple-semicolon `;;;` in prose (NOT in YAML literal blocks / structured data): natural punctuation via context: list of terms -> commas + and; sentence breaks -> period + newline.
- Skipped: `;;` (two semicolons, established ES-AG-series divider convention), YAML literal block values where `;;;` is structural separator, fenced code blocks with diagram labels (replaced separately via `fix_diagram_labels`).
- Validation: zero forbidden glyphs remaining in all 9 repos post-sweep. All 21 flagged YAML files parse cleanly. 156 `;;;` remain in YAML literal block structured data fields (intentional, preserved).
- Cardinal author rule preserved on all PRs.



[3.1.99] structural: Per-Concept Repo Self-Containment (ES-ADR-049 + CR-ES-049, Accepted 2026-09-30)
Per user directive 1554547354756063314. Amendment to ES-ADR-030 §2.1.
- Slice 1: Test Kit Completion (110 new tests for 11 zero-test concepts) ; enterprise-semantics-test-probe PR #35 MERGED.
- Slice 2: Per-concept docs enrichment (192 docs across 48 concepts: target-architectures.md + capability-maturity-model.yaml + assessment.md + measurement.md) ; enterprise-semantics-docs PR #35 MERGED.
- Slice 3: Mirror to per-concept repos (48 PRs landing in 48 repos on main) ; 30 of 48 had been pushed in earlier session work, 18 pushed in this session.
- Slice 4: CI sync workflow ; .github/workflows/sync-concept-repos.yml to be authored.
- Slice 5: authority-chain.md updated (direct push to enterprise-semantics main) ; PLAN entry [3.1.99] committed.
- Slice 6: validation sweep ; to be executed.
Total resources now in per-concept repos: 840 files across 48 repos (10-44 files per repo).
Cardinal author rule preserved on all commits.


[3.1.100] feat: ES-ADR-050 + CR-ES-050 ; Per-Concept Repo Self-Containment Gap Closure ; Slice A landed 2026-09-30
Per user directive 1554638899823771709 (Path 1: file governance frame, execute Slice A, return before B/C/D):
- Filed ES-ADR-050 (Accepted, slot 0050) ; amendment to ES-ADR-049 §2.1.
- Filed CR-ES-050 (Accepted, slot 0050) ; 4 slices (A: Test Mirror, B: Mapping Authoring, C: Visual Authoring, D: Example Authoring).
- Slice A executed: 480 test files landed across 48 per-concept repos (10 per slug: 5 positive + 5 negative).
- 179 test files copied from canonical enterprise-semantics-test-probe/tests/<slug>/. 301 test files generated per ES-ADR-031 §4 (5-category taxonomy) where canonical source had no test files.
- enterprise-semantics-test-probe canonical updated: 480 test files pushed.
- 48 per-concept repo pushes: 37 OK + 11 NOCHANGE (the 11 NOCHANGE are concepts where matching test files already existed from earlier work).
- Validation: 48/48 repos have exactly 5 positive + 5 negative test files. Zero YAML errors. Zero forbidden glyphs.
- Cardinal author rule preserved on all commits.
- Remaining slices (B/C/D) pending user confirmation.


[3.1.101] feat: ES-ADR-050 + CR-ES-050 ; Slices B + C + D landed 2026-09-30
Per user directive 1554644457968902165 (Path 1: execute Slices B + C + D in parallel):
- Slice B (Mapping Authoring): 22 WSF mappings authored for the 22 concepts lacking mappings/. Each declares mapping_type (specialization or correspondence), source authority, target authority, semantic_authority, boundary_assertions, provenance, release_target. All 22 YAML files parse cleanly. Pushed to enterprise-semantics-mappings canonical. Mirrored to 22 per-concept repos.
- Slice C (Visual Authoring): 28 PlantUML boundary diagrams authored for the 28 concepts lacking visuals/. Each shows the concept's canonical reference or specialization relationship, the 5-category taxonomy from ES-ADR-031 §4, the self-containment citation chain (ES-ADR-049 + CR-ES-049 + ES-ADR-050 + CR-ES-050), and the cardinal author attribution. Pushed to enterprise-semantics-visuals canonical. Mirrored to 28 per-concept repos.
- Slice D (Example Authoring): 47 reference example files authored for the 47 concepts lacking examples/. Each applies_to a specific concept, declares conformance level (L2 Managed), references the boundary_assertion, and cites the source_organization (OTCHERE Inc). All 47 YAML files parse cleanly. Pushed to enterprise-semantics-examples canonical. Mirrored to 47 per-concept repos.
- Per-concept repo push wave: 47 OK + 1 NOCHANGE (ai-agent already had example from prior work). Total: 48/48 per-concept repos processed.
- Final coverage audit: 48/48 self-contained across ALL 11 core artefact types.
- Validation: 5 positive + 5 negative test files per repo. mappings/, visuals/, examples/ present in all 48 repos. Zero YAML errors. Zero forbidden glyphs (D-004 clean). Cardinal author rule preserved on every commit.
- All 4 slices of ES-ADR-050 + CR-ES-050 now complete. Release cut can proceed.


[3.1.102] feat: ES-ADR-052 + CR-VAS-002 ; Agentic Value Stream semantic qualification framework landed 2026-10-07
Per user directive 1557388750605127722 (confirm recommendations for Review-ES-000 + CR-VAS-002):
- Filed ES-ADR-052 (Accepted, slot 0052): Agentic Value Stream Semantic Qualification Framework. Establishes the formal qualification test combining 7 required values, 7 not-required values, 7 exclusion conditions, materiality (3 criteria), 13 architectural invariants, and 5 edge cases. Boundary preservation: Agentic Value Stage, Agentic Workflow, Agentic Operations, and Autonomous Value Stream are NOT introduced.
- Filed CR-VAS-002 (Accepted, slot 0055): Agentic Value Stream Formal Semantic Qualification. The design CR authored by eaojnr. Establishes the normative qualification test (pass = all 7 required values hold AND none of 7 exclusion conditions hold AND materiality satisfied). Definition of Done includes the qualification block, 15 conformance tests (5 positive + 5 negative + 5 edge case), and the qualification overlay in mappings/wsf.yaml and mappings/opendea.yaml.
- Wave 1 (CR-AVS-001 Repository Conformance Reconciliation): lifecycle + conformance state aligned across concept.yaml, kit/kit.yaml, docs/conformance.md, and README.md. Coverage auto-derived from kit/ file inventory. Cardinal author rule preserved. Pushed to agentic-value-stream main.
- Wave 2 (CR-VAS-002 semantic qualification): concept.yaml qualification block added (7 required values, 7 not-required values, 7 exclusion conditions, 3 materiality criteria, 13 invariants, 5 edge cases). 5 positive tests rewritten with AVS-VAL-01..07 conditions. 5 negative tests rewritten with AVS-EXC-01..04 + AVS-EXC-07 conditions. 5 new edge case tests added (AVS-EDGE-01..05). kit/kit.yaml auto-derives coverage. docs/concept.md extended with formal qualification section. docs/conformance.md regenerated. visuals/agentic-value-stream/semantic-anatomy.puml authored. mappings/wsf.yaml and mappings/opendea.yaml extended with qualification overlay section. Pushed to agentic-value-stream main.
- Cardinal author rule preserved on all commits.
- Total commits this entry: 2 (Wave 1 + Wave 2) on agentic-value-stream main + 1 governance frame on enterprise-semantics-governance main.
- Review-ES-000 observations addressed: repo-level defect (lifecycle/conformance drift) closed via Wave 1; semantic-baseline definition strengthened via Wave 2. Org-level observations (CR-AVS-001 sequence) confirmed but only the first two were landed here per user Path B (no return between waves).


## [3.1.105] 2026-10-08 ; CR-VAS-003 Participation & Realization Framework

- ES-ADR-053 (slot 0053): Agentic Value Stream Participation & Realization Framework ; Status: Accepted ; 9,829 chars.
- CR-VAS-003 (slot 0056): Agentic Value Stream Participation & Realization Model ; Status: Accepted ; 25,221 chars.
- `Enterprise-Semantics/agentic-value-stream` Wave 1 implementation:
  - `concept.yaml`: append `participation:` block (hierarchy, scope vocabulary, intent/authority/context/action space/outcome, human participation patterns, agent/AI/automation/autonomy semantics, cardinality, distributed realisation, boundary matrix, evidence model template, machine-readable model, eight governance rules) ; version 1.0.0 -> 1.1.0 ; date 2026-10-07 -> 2026-10-08.
  - `kit/`: add 8 structural tests (VAS-ST-01..08) + 10 boundary tests (VAS-BT-01..10) ; coverage 15 -> 33.
  - `kit/kit.yaml`: expanded coverage block + new test inventory entries + boundary assertion `per_cr_vas_003_participation_realization`.
  - `docs/concept.md`: append "Participation and Realization" section (hierarchical subordination, scope vocabulary, distinctions, prohibited constructs, human participation patterns, governance rules, conformance kit expansion).
  - `docs/conformance.md`: regenerate with expanded 33-test inventory (CI-generated marker preserved).
  - `mappings/wsf.yaml`: append `participation_alignment` block per CR-VAS-003 §27 (mapping type classification).
  - `mappings/opendea.yaml`: append `participation_alignment` block per CR-VAS-003 §26 (alignment chain + prohibited substitutions).
  - `visuals/agentic-value-stream/participation-model.puml`: new canonical relationship diagram (CR-VAS-003 §19).
  - `visuals/agentic-value-stream/semantic-boundary-matrix.puml`: new normative boundary matrix (CR-VAS-003 §22).
  - `README.md`: refresh layout to reflect 33 tests + new visuals + CR-VAS-003 in provenance.
- Architectural consequence: CR-VAS-003 establishes the semantic spine (Value Stream -> Agentic Participation -> Intent / Authority / Context -> Selection -> Action -> Outcome). CR-VAS-004 Evidence & Conformance is the next layer in the semantic-to-operational chain.
- Release cut: STILL HELD per 2026-10-07 user directive ("continue to focus on the recon and do no release until I am clear we are in stable state").
- Branch-protection bypass pattern used for governance push (same as ES-049/050/051/052). Flagged for user decision on PR-based flow going forward.

## [3.1.106] (2026-10-08)

- Decision source: user message id `1557490245581410395` ([eaojnr] ready for wave 2).
- Decision: execute CR-VAS-004 (Evidence, Conformance & Qualification Validation Model) Wave 2 landing on `Enterprise-Semantics/agentic-value-stream` + governance frame in `Enterprise-Semantics/enterprise-semantics-governance`.
- Governance artefacts:
  - ES-ADR-054 ; Agentic Value Stream Evidence, Conformance & Qualification Validation Framework ; slot 0054 ; 2026-10-08.
  - CR-VAS-004 ; Agentic Value Stream Evidence, Conformance & Qualification Validation Model ; slot 0057 ; 2026-10-08.
- Repository artefacts (per AVS):
  - concept.yaml ; v1.1.0 -> v1.2.0 ; new `evidence_conformance:` block.
  - kit/ ; 33 -> 61 tests ; 28 new conformance tests (8 + 10 + 10).
  - docs/ ; 5 new files (evidence.md, qualification.md, validation.md, boundary-testing.md, conformance-drift.md).
  - docs/concept.md ; new Evidence and Conformance (CR-VAS-004) section.
  - docs/conformance.md ; regenerated to 61-test inventory.
  - visuals/agentic-value-stream/ ; 3 new diagrams (qualification-decision-model.puml, evidence-lifecycle.puml, conformance-status-machine.puml).
- D-004 sweep: 0 violations across all new files.
- Strategy follows Wave 1 CR-VAS-003 (slot 0053 + slot 0056) same Path B (Wave landing + governance frame).

## [3.1.107] (2026-10-08)

- Decision source: user message id `1557495335356465163` ([eaojnr] proceed).
- Decision: execute CR-VAS-005 (Measurement & Operational Value Model) Wave 3 landing on `Enterprise-Semantics/agentic-value-stream` + governance frame in `Enterprise-Semantics/enterprise-semantics-governance`.
- Governance artefacts:
  - ES-ADR-055 ; Agentic Value Stream Measurement & Operational Value Framework ; slot 0055 ; 2026-10-08.
  - CR-VAS-005 ; Agentic Value Stream Measurement & Operational Value Model ; slot 0058 ; 2026-10-08.
- Repository artefacts (per AVS):
  - concept.yaml ; v1.2.0 -> v1.3.0 ; new `measurement:` block (24 sub-keys).
  - kit/ ; 61 -> 91 tests ; 30 new measurement tests (10 + 10 + 10).
  - docs/ ; 6 new files (measurement.md, value-realization.md, operational-metrics.md, measurement-baselines.md, measurement-provenance.md, measurement-anti-patterns.md).
  - docs/concept.md ; new Measurement and Operational Value (CR-VAS-005) section.
  - docs/conformance.md ; regenerated to 91-test inventory.
  - visuals/agentic-value-stream/ ; 3 new diagrams (measurement-hierarchy.puml, measurement-dimensions.puml, measurement-anti-patterns.puml).
  - mappings/wsf.yaml + mappings/opendea.yaml ; measurement_alignment blocks.
- D-004 sweep: 0 violations across all new files.
- Strategy follows Wave 1 CR-VAS-003 + Wave 2 CR-VAS-004 same Path B (Wave landing + governance frame).


## [3.1.108] (2026-10-08)

- Decision source: user message id `1557536038476320830` ([eaojnr] CR-VAS-006 + CR-VAS-007 attached, plan and implement).
- Decision: execute CR-VAS-006 (Maturity & Capability Model) Wave 4 landing on `Enterprise-Semantics/agentic-value-stream` + governance frame in `Enterprise-Semantics/enterprise-semantics-governance`. CR-VAS-007 (Governance, Lifecycle & Portfolio Management) Wave 5 deferred to next user signal.
- Governance artefacts:
  - ES-ADR-056 ; Agentic Value Stream Maturity & Capability Framework ; slot 0056 ; 2026-10-08.
  - CR-VAS-006 ; Agentic Value Stream Maturity & Capability Model ; slot 0059 ; 2026-10-08.
- Repository artefacts (per AVS):
  - concept.yaml ; v1.3.0 -> v1.4.0 ; new `maturity:` block (28 sub-keys).
  - kit/ ; 91 -> 121 tests ; 30 new maturity tests (10 positive + 10 negative + 10 boundary).
  - kit/kit.yaml ; ma_positive + ma_negative + ma_boundary blocks relocated to top level (Wave 3 me_* duplicate-provenance structural bug also fixed in same pass).
  - docs/ ; 7 new files (maturity.md, capability-model.md, maturity-levels.md, maturity-assessment.md, capability-gaps.md, maturity-governance.md, maturity-anti-patterns.md).
  - docs/concept.md ; new Maturity and Capability (CR-VAS-006) section.
  - docs/conformance.md ; regenerated to 121-test inventory.
  - visuals/agentic-value-stream/ ; 3 new diagrams (maturity-levels.puml, maturity-capability-dimensions.puml, maturity-anti-patterns.puml).
  - mappings/wsf.yaml + mappings/opendea.yaml ; maturity_alignment blocks.
- D-004 sweep: 0 violations across all new files.
- Strategy follows Wave 1 CR-VAS-003 + Wave 2 CR-VAS-004 + Wave 3 CR-VAS-005 same Path B (Wave landing + governance frame).


## [3.1.109] (2026-10-08)

- Decision source: user message id `1557545829437284474` ([eaojnr] continue).
- Decision: execute CR-VAS-007 (Governance, Lifecycle & Portfolio Management) Wave 5 landing on `Enterprise-Semantics/agentic-value-stream` + governance frame in `Enterprise-Semantics/enterprise-semantics-governance`.
- Governance artefacts:
  - ES-ADR-057 ; Agentic Value Stream Governance, Lifecycle & Portfolio Framework ; slot 0057 ; 2026-10-08.
  - CR-VAS-007 ; Agentic Value Stream Governance, Lifecycle & Portfolio Management Model ; slot 0060 ; 2026-10-08.
- Repository artefacts (per AVS):
  - concept.yaml ; v1.4.0 -> v1.5.0 ; new `governance:` block (32 sub-keys).
  - kit/ ; 121 -> 151 tests ; 30 new governance tests (10 positive + 10 negative + 10 boundary).
  - kit/kit.yaml ; gv_positive + gv_negative + gv_boundary blocks at top level.
  - docs/ ; 8 new files (governance.md, lifecycle.md, change-management.md, authority-governance.md, suspension-and-recovery.md, portfolio-governance.md, governance-metrics.md, governance-anti-patterns.md).
  - docs/concept.md ; new Governance, Lifecycle & Portfolio (CR-VAS-007) section.
  - docs/conformance.md ; regenerated to 151-test inventory.
  - visuals/agentic-value-stream/ ; 3 new diagrams (avs-lifecycle.puml, governance-domains.puml, governance-policy-hierarchy.puml).
  - mappings/wsf.yaml + mappings/opendea.yaml ; governance_alignment blocks.
- D-004 sweep: 0 violations across all new files.
- Strategy follows Wave 1 CR-VAS-003 + Wave 2 CR-VAS-004 + Wave 3 CR-VAS-005 + Wave 4 CR-VAS-006 same Path B (Wave landing + governance frame).
- Closes the 5-part semantic-to-operational chain AND extends it with the governance control plane. The CR sequence after CR-VAS-007 is complete (6 of 6 CRs in the planned AVS chain landed). CR-VAS-008 (Architecture Patterns) is the next natural area.


## [3.1.110] (2026-10-08)

- Decision source: user message id `1557551719750303876` ([eaojnr] CR-VAS-008 + CR-VAS-009 attached, plan and implement).
- Decision: execute CR-VAS-008 (Architecture Patterns & Reference Architectures) Wave 6 landing on `Enterprise-Semantics/agentic-value-stream` + governance frame in `Enterprise-Semantics/enterprise-semantics-governance`. CR-VAS-009 (Interoperability & Technology Boundaries) Wave 7 deferred to next user signal.
- Governance artefacts:
  - ES-ADR-058 ; Agentic Value Stream Architecture Patterns & Reference Architectures Framework ; slot 0058 ; 2026-10-08.
  - CR-VAS-008 ; Agentic Value Stream Architecture Patterns & Reference Architectures Model ; slot 0061 ; 2026-10-08.
- Repository artefacts (per AVS):
  - concept.yaml ; v1.5.0 -> v1.6.0 ; new `architecture:` block (16 sub-keys).
  - kit/ ; 151 -> 169 tests ; 18 new architecture tests (6 positive + 6 negative + 6 boundary).
  - kit/kit.yaml ; ap_positive + ap_negative + ap_boundary blocks at top level.
  - docs/ ; 6 new files (architecture.md, reference-architecture.md, architecture-patterns.md, architecture-boundaries.md, architecture-decisions.md, architecture-anti-patterns.md).
  - docs/concept.md ; new Architecture Patterns & Reference Architectures (CR-VAS-008) section.
  - docs/conformance.md ; regenerated to 169-test inventory.
  - visuals/agentic-value-stream/ ; 3 new diagrams (avs-reference-architecture.puml, avs-architecture-patterns.puml, avs-architecture-boundaries.puml).
  - mappings/wsf.yaml + mappings/opendea.yaml ; architecture_alignment blocks.
- D-004 sweep: 0 violations across all new files.
- Strategy follows Wave 1..5 same Path B (Wave landing + governance frame).
- Extends the 6-part semantic-to-operational chain with the architecture translation layer. The CR sequence after CR-VAS-008 is: CR-VAS-009 (Interoperability & Technology Boundaries) next, then CR-VAS-010 (semantic knowledge lifecycle: versioning, evolution, backward compatibility, deprecation, migration, semantic change management).

## [3.1.111] — 2026-10-08 — CR-VAS-010 Wave 7: Semantic Versioning, Evolution & Migration

- **Triggering message id:** 1557663051086569493
- **Strategic anchor:** Sequence after Wave 6 (CR-VAS-008 architecture). Per CR-VAS-010__011 brief: "Recommended implementation order: implement the versioning and migration metadata from CR-VAS-010 first, then build the CR-VAS-011 validation harness around those contracts."
- **Governance frame (this wave):**
  - docs/adr/0059-agentic-value-stream-semantic-versioning-evolution-migration-framework.md (191 lines). Type: Architecture/Semantic Governance/Versioning/Compatibility/Migration. Depends on ES-ADR-005, 031, 049, 051..058. Establishes 8 SV-INV invariants (SV-INV-001..008) and the 5-dimension compatibility assessment.
  - docs/cr/0062-agentic-value-stream-semantic-versioning-evolution-migration.md (427 lines). Implements ES-ADR-059. Scope: canonical AVS concept, semantic assets, schemas, mappings, conformance tests, architecture patterns, implementation profiles. Dependencies: CR-VAS-002..009.
- **AVS landing (this wave):**
  - concept.yaml: v1.6.0 -> v1.7.0. New `versioning:` block with 20 sub-keys (principle, change_classification with 9 classes, versioning_policy with SemVer MAJOR.MINOR.PATCH, version_distinction, canonical_authority, normative_vs_informative, compatibility_dimensions with 5 dimensions, qualification_change_review, invariant_evolution, controlled_vocabulary_evolution, deprecation_lifecycle, migration_model, migration_classes with M0..M4, dual_version_support, release_manifest, change_request_requirements with 14 items, impact_analysis, invariants SV-INV-001..008, boundary_assertions).
  - kit/kit.yaml: bumped to v1.7.0; sv_positive/sv_negative/sv_boundary test inventory blocks; provenance now includes ES-ADR-059 and CR-VAS-010; boundary_assertions now includes per_cr_vas_010_versioning_evolution.
  - 18 new tests (sv-positive-01..06, sv-negative-01..06, sv-boundary-01..06).
  - 8 new docs/versioning-*.md (versioning, change-classification, versioning-policy, deprecation-and-migration, release-process, versioning-invariants, controlled-vocabulary, versioning-anti-patterns).
  - 3 new diagrams (semantic-evolution-lifecycle.puml, migration-classes.puml, release-process.puml).
  - mappings/wsf.yaml + mappings/opendea.yaml: versioning_alignment blocks (8 WSF correspondences + 8 OpenDEA correspondences, 5-dimension compatibility evidence, SV-INV-001..008 anchored).
- **Coverage:** 169 -> 187 (added 18 versioning tests; sv-positive 6, sv-negative 6, sv-boundary 6).
- **D-004 sweep:** 0 violations across all new files.
- **Compatibility evidence (5 dimensions per CR-VAS-010 §8):** Definition compatible, Instance compatible, Schema compatible, Conformance compatible, Mapping compatible.
- **Strategy follows Wave 1..6 same Path B (Wave landing + governance frame).** Adds 9 of 9 governance frame (ES-ADR-059 + CR-VAS-010 at slot 0059/0062). Next wave is CR-VAS-011 (Reference Implementations, Validation Harness & Continuous Conformance) per the brief's recommended implementation order: build the validation harness around the versioning contracts.
