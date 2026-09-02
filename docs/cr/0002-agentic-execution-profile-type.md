# CR-ES-AG-002 ;;; agentic-execution profile_type + Profile record

**Status:** Proposed ;;; implemented
**Scope:** `enterprise-semantics` repo
**Implements:** ADR-ES-AG-001 §6 CR-ES-AG-002 ;;; the agentic-execution profile_type + Profile record.
**Depends on:** CR-ES-AG-001 (Profile semantic construct, landed) ;;; ADR-ES-AG-001 (Accepted) ;;; ADR-ES-002 ;;; FND-ES-AG-001 (canonical, user-revised) ;;; FND-ES-AG-001-Grounding-Result (WSF live baseline).
**Enables:** CR-ES-AG-003 (Agentic Value Stream) ;;; CR-ES-AG-004 (Agentic Workflow).

---

## 1. Change

Register the `agentic-execution` profile_type and land a governed Profile record
that captures the architectural commitment from ADR-ES-AG-001 §3:

1. Register `agentic-execution` in `registry/profile-types.yaml` (already done in
   CR-ES-AG-001 ;;; status remains `Established`).
2. Land the `Profile record` at `registry/profiles/agentic-execution.profile.yaml`
   with the four governed characteristics from ADR-ES-AG-001 §3.3.
3. Cite WSF grounding in the Profile record's provenance per the
   FND-ES-AG-001-Grounding-Result requirement.

---

## 2. Why this CR exists

The Profile semantic construct from CR-ES-AG-001 provides the governance scaffolding,
but it is empty until at least one governed Profile record exists. CR-ES-AG-002 lands
the first one.

The `agentic-execution` profile_type is the foundation of the entire Agentic family
per ADR-ES-AG-001 §3.3. Without this CR, downstream CRs (CR-ES-AG-003 Agentic Value
Stream ;;; CR-ES-AG-004 Agentic Workflow ;;; etc.) cannot reference a registered
profile_type, and the conformance harness will reject them.

---

## 3. Implementation

### 3.1 Profile type registration

Already done in CR-ES-AG-001 ;;; `registry/profile-types.yaml` lists
`agentic-execution` as `Established`. No change needed here.

### 3.2 Profile record

Land at `registry/profiles/agentic-execution.profile.yaml`:

```yaml
id: ES:PROFILE:agentic-execution
canonical_name: Agentic Execution Profile
definition: |
  A Profile that applies the four governed Agentic characteristics to a base concept
  (e.g. Value Stream, Workflow, Operations, Enterprise). The base concept retains its
  identity ;;; the Profile adds a governed configuration overlay. Per ADR-ES-AG-001 §3.
status: Established
version: 1.0.0
profile_type: agentic-execution
characteristics:
  - id: ES:CHAR:goal-directed-execution-under-bounded-autonomy
    canonical_name: Goal-directed execution under bounded autonomy
    description: |
      The entity progresses toward stated outcomes without requiring continuous human
      routing, within bounds set by governance.
  - id: ES:CHAR:ai-augmented-decision-making
    canonical_name: AI-augmented decision-making
    description: |
      Decisions about progression, exception handling, and routing are made by AI
      agents under governed policy.
  - id: ES:CHAR:adaptive-behavior
    canonical_name: Adaptive behavior
    description: |
      The entity reconfigures its structure or execution in response to feedback
      and outcome signals.
  - id: ES:CHAR:human-governance-not-human-execution
    canonical_name: Human governance, not human execution
    description: |
      Humans set intent, policy, and outcome criteria. AI agents execute within
      those bounds.
governance: enterprise-semantics
provenance:
  - source: docs/adr/0003-agentic-semantic-decision.md
    note: ADR-ES-AG-001 §3.3 defines the four characteristics.
  - source: https://github.com/World-Semantic-Foundation
    note: WSF live baseline provides the foundational grounding. Agentic concepts
    specialize WSF concepts (e.g. Value Stream, Workflow) rather than redefining
    them. Per FND-ES-AG-001-Grounding-Result.
  - source: docs/finding/0001-agentic-semantic-grounding-canonical.md
    note: FND-ES-AG-001 (user-revised canonical) establishes the grounding matrix.
  - source: docs/finding/0001-agentic-semantic-grounding-grounding-result.md
    note: Grounding Result establishes WSF live baseline alignment and the strong-
    candidates list.
mappings: []
created: 2026-09-02
updated: 2026-09-02
```

### 3.3 Conformance

- `python3 conformance/check.py` ;;; `NO_DRIFT (1 Profile record(s) validated)`, exit 0.
- The four characteristics are non-empty, regex-compliant, and unique within the Profile.
- The provenance cites the WSF live baseline per the Grounding Result.

---

## 4. Files added

| File | Purpose |
|------|---------|
| `registry/profiles/agentic-execution.profile.yaml` | First governed Profile record. |
| `CHANGELOG.md` | v0.2.0 entry. |

---

## 5. Acceptance criteria

This CR is accepted when:

1. The Profile record lands in `enterprise-semantics` main branch.
2. `python3 conformance/check.py` exits 0 with 1 record validated.
3. CHANGELOG.md records v0.2.0.
4. `manny-es` posts a completion summary to Discord Home.

---

## 6. Cross-references

- ADR-ES-AG-001: https://github.com/Enterprise-Semantics/enterprise-semantics-governance/blob/main/docs/adr/0003-agentic-semantic-decision.md
- FND-ES-AG-001 (canonical): https://github.com/Enterprise-Semantics/enterprise-semantics-governance/blob/main/docs/finding/0001-agentic-semantic-grounding-canonical.md
- FND-ES-AG-001-Grounding-Result: https://github.com/Enterprise-Semantics/enterprise-semantics-governance/blob/main/docs/finding/0001-agentic-semantic-grounding-grounding-result.md
- Local verbatim: `/home/hermes/Projects/Enterprise-Semantics/00_inbox/CR-ES-AG-002.md`
- Local dash-normalized: `/home/hermes/Projects/Enterprise-Semantics/seed/CR-ES-norm-AG-002.md`
- Implementation repo: https://github.com/Enterprise-Semantics/enterprise-semantics

## 7. Provenance rationale

The Grounding Result document emphasizes that the Agentic family must specialize
WSF, not duplicate it. The Profile record's provenance explicitly cites WSF as
the foundational source ;;; this is the auditable trail that any future reviewer
can follow to confirm the Agentic profile is grounded rather than invented.
