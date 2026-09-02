# Enterprise Semantics — Program Plan

**Owner:** emmanuel-a-otchere
**GitHub Org:** https://github.com/Enterprise-Semantics
**Plan Source:** FND-ES-000 §3/§25 (canonical architecture) + FND-ES-001 §16 (governance sequence)
**Plan Version:** 0.1.0 (Phase 0; will increment per release)
**Plan Status:** Phase 0 in progress; Phases 1;6 awaiting Proceed
**Last Plan-Keeper Sync:** see `PLAN-CHANGELOG.md`

---

## 0. Architectural Outcome (from FND-ES-000 §25)

```text
                     WSF
                      : foundation grounding
                      :
                      v
             ENTERPRISE SEMANTICS
                      : enterprise semantic grounding
          +-----------+-----------+
          :           :           :
       Research    Concepts    Mappings
          :           :           :
          +-----------+-----------+
                      :
                 formalization
                      :
                      v
                   OpenDEA
                      :
                  instances
                      :
                      v
                DEA Catalogs
```

The semantic development loop:

```text
Existing Knowledge
       :↓
Semantic Seed
       :↓                       (candidate hypotheses)
Finding
       :↓                       (in scope, gated)
ADR
       :↓                       (governed decision)
CR
       :↓                       (implementable change)
Implementation
       :↓
CI
       :↓
Published Semantic Version
       :↓
Reference / Mapping
       :↓
Downstream Use
       :↓
New Finding
       :↑
       back to the top of the loop
```

---

## 1. Repo Inventory (target state)

9 public repos, all Apache-2.0, members-can-create-repos remains on the org (today's verified default).

| # | Repo | Mirrors | Purpose |
|---|------|---------|---------|
| 1 | `.github` | WSF `.github` | Org landing page (profile/README.md), shared community health files |
| 2 | `enterprise-semantics` | WSF `wsf` | Structured semantic source (YAML/JSON): concepts, relationships, identifier registry. Single source of truth |
| 3 | `enterprise-semantics-spec` | WSF `wsf-spec` | Normative specs: identifier scheme, relationship vocabulary, lifecycle model, conformance requirements, serialization formats |
| 4 | `enterprise-semantics-governance` | WSF `wsf-governance` | ADRs, CRs, Findings, workflow templates. **Home of this PLAN.md once Phase 2 lands.** |
| 5 | `enterprise-semantics-docs` | WSF `wsf-docs` | Human-readable documentation; generated where possible from `enterprise-semantics` |
| 6 | `enterprise-semantics-examples` | WSF `wsf-examples` | Worked enterprise models; provenance evidence for seed concepts |
| 7 | `enterprise-semantics-mappings` | (FND-ES-000 §9) | Bi-directional mappings: ES ;;; WSF, ES ;;; OpenDEA, ES ;;; DEA Catalogs |
| 8 | `enterprise-semantics-visuals` | WSF `wsf-visuals` | PlantUML/Mermaid/SVG sources; reproducible architectural diagrams |
| 9 | `enterprise-semantics-test-probe` | WSF `wsf-test-probe` | Conformance harness: schema validation, ID uniqueness, broken-reference check, mapping integrity |

---

## 2. Phases

### Phase 0 — Plan + Plan-Keeper (current)

**Objective:** Lock the program plan; stand up a durable plan-keeper.

**Deliverables:**

- [ ] **0.1** Local working folder `/home/hermes/Projects/Enterprise-Semantics/` with `00_inbox/` (verbatim FND-ES-000/001), `seed/` (dash-normalized drafts), `repos/` (clones), `plans/` (this file), `scripts/` (plan-keeper tooling)
- [ ] **0.2** Verbatim copies of FND-ES-000 and FND-ES-001 in `00_inbox/`
- [ ] **0.3** This `plans/PLAN.md` committed locally; `plans/PLAN-CHANGELOG.md` started
- [ ] **0.4** Plan-keeper cronjob scheduled (15-minute drift check + drift-only Discord ping)
- [ ] **0.5** Plan-keeper script at `scripts/plan_keeper.py` (idempotent, no destructive writes)
- [ ] **0.6** `seed/` directory seeded with the dash-normalized FND-ES-000/001 (orgs, scope, dash-rule-aware)
- [ ] **0.7** Git repo initialised in workspace; `.gitignore` blocks credential patterns

**Verification:**

- `tree -L 2 /home/hermes/Projects/Enterprise-Semantics/` shows the five subdirs
- `git -C /home/hermes/Projects/Enterprise-Semantics log --oneline` returns the initial commit
- `cronjob list` shows `es-plan-keeper` as `enabled`
- Plan-keeper dry-run on an empty board prints `NO_DRIFT`

**Definition of Done:** Plan committed; keeper live; user approves Proceed on Phase 1.

---

### Phase 1 — Workspace + Org Landing Page (no domain repos yet)

**Objective:** Make `Enterprise-Semantics` browsable; land the org charter; expose the WSF ;;; ES ;;; OpenDEA architecture publicly.

**Deliverables:**

- [ ] **1.1** Create `.github` public repo at `Enterprise-Semantics/.github` (Apache-2.0, profile README)
- [ ] **1.2** Author `profile/README.md` (dash-normalized, spec tone): org charter, the §0 architecture diagram, the §0 semantic-development loop, repo index, contribution flow, dash-rule notice
- [ ] **1.3** Add `CODE_OF_CONDUCT.md`, `CONTRIBUTING.md`, `SECURITY.md`, `PULL_REQUEST_TEMPLATE.md` to `.github`
- [ ] **1.4** Set org description: "Enterprise-level semantic definitions, relationships, and mappings: governed, public, machine-accessible."
- [ ] **1.5** Org-level program board created (single Project v2, owner `Enterprise-Semantics`), with custom fields: `Item Type` (Epic/Story/Task/Decision/Spike), `Priority` (Critical/High/Medium/Low), `Phase` (0/1/2/3/4/5/6), `Milestone` (linked at repo level)
- [ ] **1.6** Org board seeded with: one Epic issue per planned repo (8 future repos; no placeholder repos), one Roadmap Tracker Epic in governance (which will land in Phase 2)

**Verification:**

- `gh api /orgs/Enterprise-Semantics -q .description` returns the charter one-liner
- `gh repo list Enterprise-Semantics --json name` returns `[{"name":".github"}]`
- `curl -s https://raw.githubusercontent.com/Enterprise-Semantics/.github/main/profile/README.md | wc -c` returns > 1500 bytes
- `gh project list --owner Enterprise-Semantics` returns 1 open project with the right title
- Browser renders the org profile (manual check; URL listed in scorecard)

**Definition of Done:** Org browsable end-to-end; program board live with future-repo epics.

---

### Phase 2 — Domain Repo Skeleton (READMEs + charters, no content)

**Objective:** Create the 8 domain repos with READMEs, CODEOWNERS, CHANGELOGs; tighten branch protection on the spec/governance/docs trio.

**Deliverables:**

- [ ] **2.1** Create `enterprise-semantics` (the authority repo); commit `README.md`, `CODEOWNERS`, `CHANGELOG.md`, `.gitignore`
- [ ] **2.2** Create `enterprise-semantics-spec`; commit same skeleton plus an ADR template in `docs/adr/0000-template.md`
- [ ] **2.3** Create `enterprise-semantics-governance`; commit skeleton plus a CR template in `docs/cr/0000-template.md`, an ADR template, and a `Finding` template; migrate `plans/PLAN.md` here as `docs/plan/PLAN.md` once the repo exists
- [ ] **2.4** Create `enterprise-semantics-docs`; commit skeleton
- [ ] **2.5** Create `enterprise-semantics-examples`; commit skeleton
- [ ] **2.6** Create `enterprise-semantics-mappings`; commit skeleton with mapping-file schema stub
- [ ] **2.7** Create `enterprise-semantics-visuals`; commit skeleton with `docs/diagrams/` placeholder
- [ ] **2.8** Create `enterprise-semantics-test-probe`; commit skeleton with one example test that fails until `enterprise-semantics` has a concept file
- [ ] **2.9** Move the 7 architectural diagrams from FND-ES-000 §3, §4, §6, §9, §11, §23, §25 into `enterprise-semantics-visuals/docs/diagrams/` as PlantUML sources with PNG renders
- [ ] **2.10** Branch protection on the spec / governance / docs trio: require PR + 1 approving review on `main`; allow direct push on the others during skeleton phase

**Verification:**

- `gh repo list Enterprise-Semantics --json name -q 'length'` returns 9
- For each repo: `gh api repos/Enterprise-Semantics/<repo>/contents/README.md` returns 200
- For each repo: `gh api repos/Enterprise-Semantics/<repo>/license` confirms Apache-2.0
- Visuals repo has `docs/diagrams/` directory with the 7 PlantUML sources

**Definition of Done:** All 9 repos public, Apache-2.0, READMEs + CODEOWNERS + CHANGELOG present; diagrams committed.

---

### Phase 3 — Authority and Identifier Decisions (ADR-ES-001 + CR-ES-001)

**Objective:** Land the founding governance decisions in the governance repo, authored by the user (or me, gated by Proceed per ADR/CR template).

**Deliverables:**

- [ ] **3.1** `docs/adr/0001-establish-enterprise-semantics-authority-and-publication-architecture.md` (ADR-ES-001): 15 scope items from FND-ES-001 §24, identifier scheme proposal (`ES:<KIND>:<NAME>` per FND-ES-000 §7), workflow diagram for Findings ;;; ADRs ;;; CRs
- [ ] **3.2** `docs/cr/0001-establish-organization-and-semantic-authority-repository.md` (CR-ES-001): the implementing CR that flips Phase 2 repos from skeleton to seeded
- [ ] **3.3** `docs/finding/0001-establish-enterprise-semantics.md`: FND-ES-000/001 ingested as Finding records (verbatim body, dash-normalized metadata header)
- [ ] **3.4** Org board updated: ADR-ES-001 and CR-ES-001 as `Item Type: Decision` issues, status `In Progress`
- [ ] **3.5** Branch-protection tightening: all 9 repos require PR + 1 approving review

**Verification:**

- The three files render correctly at `github.com/Enterprise-Semantics/enterprise-semantics-governance/tree/main/docs`
- A test PR opens against the governance repo and resolves the ADR template correctly
- Org board shows ADR-ES-001 and CR-ES-001 with `Phase: 3`, `Status: In Progress`

**Definition of Done:** Founding governance committed; org board reflects it.

---

### Phase 4 — Semantic Seed Land (the actual enterprise-concepts-model content)

**Objective:** Materialize the seed concepts from FND-ES-000 §14/§15 as Candidate-status YAML records; land the initial profile stubs; stand up the first mapping skeletons.

**Deliverables:**

- [ ] **4.1** Seed concepts in `enterprise-semantics/concepts/<area>/<concept>.yaml` for each of the 14 families in FND-ES-000 §14: Enterprise, Intent and Governance, Capacity and Capability, Value, Work and Execution, Intelligence, Agentic, Autonomous, Operations, Closed Loop, Scenario, Information, State and Occurrence, Measurement and Value Realization. Each record: `id`, `canonical_name`, `definition`, `status: Candidate`, `provenance`, `aliases`, `relationships`, `classifications`
- [ ] **4.2** `enterprise-semantics/registry/ids.yaml`: identifier registry (prevents ID collisions)
- [ ] **4.3** Relationship records for the 8 hypotheses in FND-ES-000 §15 as `relationship.yaml` files with `status: provisional`
- [ ] **4.4** Profile stubs in `enterprise-semantics/profiles/`: `agentic-enterprise`, `agentic-operations`, `agentic-value-stream`, `autonomous-enterprise`, `autonomous-operations`, `autonomous-network`. Each stub enumerates the open questions it must investigate
- [ ] **4.5** Provenance links in every seed record pointing back to FND-ES-000/001 plus the existing agentic-work artifacts (e.g. `infographic/autonomous-flow-ai-closed-loop/`)
- [ ] **4.6** First mapping skeletons in `enterprise-semantics-mappings/`: `ES:Capability` ;;; `wsf:Capability`, `ES:Capability` ;;; `dea:Capability`
- [ ] **4.7** CI in `enterprise-semantics-test-probe`: schema validates every YAML, IDs unique, no broken references, lifecycle values in the controlled enum
- [ ] **4.8** Auto-generated Markdown views land in `enterprise-semantics-docs` per FND-ES-001 §4

**Verification:**

- All seed concepts pass CI; CI status check on `enterprise-semantics` main branch is green
- ID registry has zero collisions
- The 8 relationships land with `status: provisional`
- Mapping skeletons load with `status: proposed`

**Definition of Done:** CI green; seed browsable in human docs.

---

### Phase 5 — Conformance Gate and Program Board Maturity

**Objective:** Promote the test-probe to a hard CI gate; mature the program board; land the first real CR against the seed.

**Deliverables:**

- [ ] **5.1** `enterprise-semantics-test-probe` becomes the CI gate applied to `enterprise-semantics` and `enterprise-semantics-mappings` (the FND-ES-001 §14 list)
- [ ] **5.2** Branch protection requires the conformance check on every PR against the authority repo and the mappings repo
- [ ] **5.3** Org board matured: custom views (By Phase, By Repo, By Owner, Blocked), Milestones wired at repo level
- [ ] **5.4** First "real" CR landed: `CR-ES-002 — Promote Capability from Candidate to Proposed` (the first concept-specific CR that mutates the seed)
- [ ] **5.5** Semantic release tag: `enterprise-semantics@v0.1.0-seed`

**Verification:**

- A deliberately broken seed (e.g. duplicate ID) fails CI on `enterprise-semantics` PR
- Org board views are reachable; each view shows expected items
- `gh release view v0.1.0-seed` exists on `enterprise-semantics`

**Definition of Done:** CI gate enforced; first semantic release tagged.

---

### Phase 6 — First Concept ADRs (post-seed)

**Objective:** Author concept-specific ADRs that govern future seed promotions.

**Deliverables (one epic per ADR):**

- [ ] **6.1** FND-ES-002 → ADR-ES-002 — Capability Semantic Grounding
- [ ] **6.2** FND-ES-003 → ADR-ES-003 — Value Stream Semantic Grounding
- [ ] **6.3** FND-ES-004 → ADR-ES-004 — Agentic Semantic Grounding
- [ ] **6.4** FND-ES-005 → ADR-ES-005 — Agentic Value Stream Semantic Grounding
- [ ] **6.5** FND-ES-006 → ADR-ES-006 — Agentic Workflow Semantic Grounding
- [ ] **6.6** FND-ES-007 → ADR-ES-007 — Autonomous Operations Semantic Grounding
- [ ] **6.7** Findings chain: FND-ES-002 ... FND-ES-007 ingested as Finding records in `enterprise-semantics-governance/docs/finding/`

**Verification:**

- Each ADR has a corresponding CR that lands a code/spec change
- CI green on every PR
- Org board tracks each ADR's status through In Progress ;;; Done

**Definition of Done:** Seven concept ADRs merged; seven corresponding CRs merged; org board at Phase 6 Done for each.

---

## 3. WBS (Work Breakdown Structure)

This mirrors the org GitHub Project plan:

```text
Program: Enterprise Semantics (PVT_<org>)
├── Epic 0.0 — Plan + Plan-Keeper                              [Phase 0]
│     ├── Task 0.1: workspace + 00_inbox/seed
│     ├── Task 0.2: PLAN.md committed
│     ├── Task 0.3: PLAN-CHANGELOG.md started
│     ├── Task 0.4: plan-keeper cronjob scheduled
│     ├── Task 0.5: scripts/plan_keeper.py authored
│     ├── Task 0.6: seed/ dash-normalized drafts
│     └── Task 0.7: workspace git init
├── Epic 1.0 — Org Landing Page                                 [Phase 1]
│     ├── Task 1.1: .github repo created
│     ├── Task 1.2: profile/README.md authored
│     ├── Task 1.3: community health files
│     ├── Task 1.4: org description set
│     ├── Task 1.5: program board created + fields
│     └── Task 1.6: board seeded with future-repo epics
├── Epic 2.0 — Domain Repo Skeleton                             [Phase 2]
│     ├── Task 2.1: enterprise-semantics repo
│     ├── Task 2.2: enterprise-semantics-spec repo
│     ├── Task 2.3: enterprise-semantics-governance repo + PLAN.md migration
│     ├── Task 2.4: enterprise-semantics-docs repo
│     ├── Task 2.5: enterprise-semantics-examples repo
│     ├── Task 2.6: enterprise-semantics-mappings repo
│     ├── Task 2.7: enterprise-semantics-visuals repo
│     ├── Task 2.8: enterprise-semantics-test-probe repo
│     ├── Task 2.9: 7 architectural diagrams
│     └── Task 2.10: branch protection (spec/gov/docs trio)
├── Epic 3.0 — Authority and Identifier Decisions               [Phase 3]
│     ├── Task 3.1: ADR-ES-001
│     ├── Task 3.2: CR-ES-001
│     ├── Task 3.3: Finding records
│     ├── Task 3.4: board updated with Decisions
│     └── Task 3.5: branch protection tightened org-wide
├── Epic 4.0 — Semantic Seed Land                               [Phase 4]
│     ├── Task 4.1: 14 concept families as YAML
│     ├── Task 4.2: id registry
│     ├── Task 4.3: 8 hypotheses as relationship records
│     ├── Task 4.4: 6 profile stubs
│     ├── Task 4.5: provenance links
│     ├── Task 4.6: first mapping skeletons
│     ├── Task 4.7: CI in test-probe
│     └── Task 4.8: auto-generated docs views
├── Epic 5.0 — Conformance Gate + Program Board Maturity        [Phase 5]
│     ├── Task 5.1: CI gate enforced
│     ├── Task 5.2: branch protection requires conformance
│     ├── Task 5.3: board views
│     ├── Task 5.4: CR-ES-002 (first real CR)
│     └── Task 5.5: v0.1.0-seed release tag
└── Epic 6.0 — First Concept ADRs                               [Phase 6]
      ├── Task 6.1: ADR-ES-002 Capability
      ├── Task 6.2: ADR-ES-003 Value Stream
      ├── Task 6.3: ADR-ES-004 Agentic
      ├── Task 6.4: ADR-ES-005 Agentic Value Stream
      ├── Task 6.5: ADR-ES-006 Agentic Workflow
      ├── Task 6.6: ADR-ES-007 Autonomous Operations
      └── Task 6.7: Findings chain
```

---

## 4. Dependency Graph

```text
Phase 0 ──> Phase 1 ──> Phase 2 ──> Phase 3 ──> Phase 4 ──> Phase 5 ──> Phase 6
                       :                                                                                           
                       └── (PLAN.md migrates from local to enterprise-semantics-governance/docs/plan/PLAN.md)      
```

Phase 0 is independent and self-contained.
Phase 1 depends on Phase 0 (plan + keeper live).
Phase 2 depends on Phase 1 (org profile + board live so the 8 repos have a home).
Phase 3 depends on Phase 2 (governance repo exists to receive ADRs/CRs/Findings).
Phase 4 depends on Phase 3 (identifier scheme + lifecycle model decided by ADR-ES-001).
Phase 5 depends on Phase 4 (something to gate).
Phase 6 depends on Phase 5 (CI gate active; first release tagged).

---

## 5. Sub-agent ownership (added in v0.3.0)

Every change to the Enterprise-Semantics organization is the joint product of:

| Role | Identity | Cadence | Purpose |
|------|----------|---------|---------|
| Human owner | @emmanuel-a-otchere | on-demand | Sole sign-off authority. Approves and merges. |
| Dedicated sub-agent | `manny-es` (cronjob `c0b35d4938af`) | daily + on-demand | Proposes and prepares changes. Posts a Discord check-in every day at 09:00 local. Resolves drift surfaced by the keeper. |
| Drift keeper | `es-plan-keeper` (cronjob `434b5c9c3023`) | every 15 minutes | Read-only drift detection. Reports only when drift occurs. |

The two agents cooperate, never duplicate. The keeper detects; `manny-es` decides.

**Firing `manny-es` on demand:**

```bash
cronjob action=run job_id=c0b35d4938af
```

**Hard rules for `manny-es`** (full text in the cronjob prompt):

1. Commit author is always `@emmanuel-a-otchere`.
2. Dash normalization: colons / semicolons only, never en-dash or em-dash.
3. Spec tone in normative documents.
4. `enterprise-semantics` is the semantic authority; everything else derives from it.
5. Concept IDs use `ES:<KIND>:<NAME>` once ADR-ES-001 lands.
6. Concepts start at `Candidate`; promotion to Canonical requires an ADR + CR + CI green.
7. Branch protection on `enterprise-semantics-spec`, `enterprise-semantics-governance`, `enterprise-semantics-docs`: PR + 1 review required.
8. No auto-deploys; no auto-merges.
9. Cronjob cannot ask clarifying questions ;;; surface as pending-decision in Discord and exit.
10. Destructive operations forbidden ;;; propose, never execute.

**Identity surface:**

- Every repo's `CODEOWNERS` references `manny-es`.
- Org profile README has a "Program ownership" section naming `manny-es`.
- Plan-keeper YAML summary records `manny-es` cronjob id and live status.
- Program board has a `[manny-es]` Decision card (Item Type=Decision, Status=Done).

## 6. Plan-Keeper (durable sub-agent)

Per the user's directive ("always have a sub-agent responsible to keep the project plan updated"), the plan-keeper is implemented as a **cronjob** (durable across sessions), not as a session-scoped delegate_task.

| Attribute | Value |
|-----------|-------|
| Job ID | `es-plan-keeper` |
| Schedule | every 15 minutes |
| Script | `scripts/plan_keeper.py` (idempotent; reads board + repo state; diffs against PLAN.md) |
| Output behavior | silent on NO_DRIFT; opens/updates a `plan-drift` issue + pings the Enterprise-Semantics Discord channel on DRIFT |
| Cron prompt | self-contained: instructs the agent to fetch the board, diff against PLAN.md, and either emit a drift report or print `NO_DRIFT` |
| Skills loaded | `github`, `github-projects`, `github-org-bootstrap`, `writing-plans` |
| Deliver | `local` (silent) + `discord:<channel>` on drift |

**Why a cronjob, not delegate_task:** delegate_task dies on `/stop`, `/new`, or process exit. A cronjob survives across sessions, which is what "always have a sub-agent responsible" requires.

---

## 7. Decisions Log (open)

- **D-001 (open):** Plan-keeper cadence and notification channel — currently15min + Discord drift ping. Change here if user prefers daily digest only, or no automation.
- **D-002 (open):** Branch-protection bar — currently light during skeleton phase, tightened org-wide at Phase 3.5.
- **D-003 (open):** Orphan org `Enterprise-Concepts-Model` — currently untouched. User decision pending: delete / leave / archive.
- **D-004 (open):** Whether the local `seed/` directory is gitignored (so dash-normalized drafts don't leak into a future remote push) — currently YES, ignored.
- **D-005 (open):** Whether to publish the local working folder as a separate `es-workspace` repo (so the workspace is reproducible) — currently NO; revisit if user wants it.
- **D-006 (open):** PNG renders of PlantUML diagrams pending until Phase 5 CI wires the renderer. Recorded in `enterprise-semantics-visuals/CHANGELOG.md`.
- **D-007 (resolved 2026-09-02):** `manny-es` is the dedicated, named sub-agent for the Enterprise-Semantics organization. Implemented as cronjob `c0b35d4938af`. Identity surface updated across CODEOWNERS, profile README, program board (Decision card #2), and plan-keeper YAML.

---

## 8. Plan Status (machine-readable summary)

```yaml
program: Enterprise-Semantics
org: Enterprise-Semantics
plan_version: 0.1.0
phases:
  - id: 0
    title: "Plan + Plan-Keeper"
    status: completed
    started: 2026-09-02
    completed: 2026-09-02
  - id: 1
    title: "Workspace + Org Landing Page"
    status: completed
    started: 2026-09-02
    completed: 2026-09-02
  - id: 2
    title: "Domain Repo Skeleton"
    status: completed
    started: 2026-09-02
    completed: 2026-09-02
  - id: 3
    title: "Authority and Identifier Decisions"
    status: pending
  - id: 4
    title: "Semantic Seed Land"
    status: pending
  - id: 5
    title: "Conformance Gate + Program Board Maturity"
    status: pending
  - id: 6
    title: "First Concept ADRs"
    status: pending
repos:
  target: 9
  created: 9
  planned:
    - .github
    - enterprise-semantics
    - enterprise-semantics-spec
    - enterprise-semantics-governance
    - enterprise-semantics-docs
    - enterprise-semantics-examples
    - enterprise-semantics-mappings
    - enterprise-semantics-visuals
    - enterprise-semantics-test-probe
org_board:
  exists: true
  project_id: PVT_kwDOE02mGs4BiLsK
  url: https://github.com/orgs/Enterprise-Semantics/projects/1
keeper:
  cronjob_id: es-plan-keeper
  schedule: "*/15 * * * *"
  status: scheduled
agents:
  - name: es-plan-keeper
    role: drift detector
    cronjob_id: "434b5c9c3023"
    schedule: "*/15 * * * *"
    status: scheduled
  - name: manny-es
    role: dedicated sub-agent for Enterprise-Semantics
    cronjob_id: "c0b35d4938af"
    schedule: "0 9 * * *"
    status: scheduled
    purpose: "Daily check-in + on-demand; resolves keeper drift"
    decision_card: enterprise-semantics-governance#2
```

---

## 8. Cross-references

- `00_inbox/FND-ES-000.md` — canonical Finding (verbatim, em-dashes preserved)
- `00_inbox/FND-ES-001.md` — sharper Finding (verbatim, em-dashes preserved)
- `seed/` — dash-normalized drafts of the above
- `scripts/plan_keeper.py` — keeper script (Phase 0.5)
- `plans/PLAN-CHANGELOG.md` — change log for this plan