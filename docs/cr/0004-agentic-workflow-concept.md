# CR-ES-AG-004 ;;; Agentic Workflow (concept record)

**Status:** Proposed ;;; implemented
**Scope:** `enterprise-semantics` repo
**Implements:** ADR-ES-AG-001 §6 CR-ES-AG-004 ;;; the Agentic Workflow concept record.
**Depends on:** CR-ES-AG-001 ;;; CR-ES-AG-002 ;;; CR-ES-AG-003 ;;; FND-ES-AG-003 ;;; ADR-ES-AG-001 ;;; ADR-ES-002 ;;; FND-ES-AG-001-Grounding-Result.
**Enables:** Downstream CRs that reference Agentic Workflow.

---

## 1. Change

Land the `Agentic Workflow` Concept record at
`concepts/agentic-workflow.concept.yaml`, plus the supporting `Workflow` Concept
record at `concepts/workflow.concept.yaml`. Per FND-ES-AG-003 and ADR-ES-AG-001 §3
;;; Agentic Workflow is a Profile of Workflow under agent-augmented execution
conditions.

---

## 2. Implementation

### 2.1 Records landed

- `concepts/workflow.concept.yaml` ;;; base Concept record, status=Established.
- `concepts/agentic-workflow.concept.yaml` ;;; profiled Concept record,
  status=Candidate, profile_bindings to `ES:PROFILE:agentic-execution`.

### 2.2 WSF grounding (mandatory per FND-ES-AG-001-Grounding-Result)

- Workflow ;;; specializes `external:wsf:Activity` ;;; references `external:wsf:Event`.
- Agentic Workflow ;;; references `external:wsf:Activity` (inherited via Workflow).

### 2.3 Profile binding

- Agentic Workflow ;;; binds `ES:PROFILE:agentic-execution` (profile_type=agentic-execution, active=true).

### 2.4 Governed relationships

- Agentic Workflow profile-of Workflow (status=proposed).
- Agentic Workflow orchestrates Agentic Flow (status=provisional). Per
  ADR-ES-002 §22 ;;; not contains.

### 2.5 Conformance

Inherited from CR-ES-AG-003. All harnesses and tests green.

---

## 3. Files added

| File | Purpose |
|------|---------|
| `concepts/workflow.concept.yaml` | Base Concept record. |
| `concepts/agentic-workflow.concept.yaml` | Profiled Concept record. |

---

## 4. Acceptance criteria

1. Records land in `enterprise-semantics` main branch.
2. `python3 conformance/check_concepts.py` ;;; `NO_DRIFT (4 Concept record(s) validated)`, exit 0.
3. `python3 conformance/tests/test_concept_schema.py` ;;; `5/5 cases passed`, exit 0.
4. CHANGELOG.md records v0.4.0.

---

## 5. Cross-references

- FND-ES-AG-003: https://github.com/Enterprise-Semantics/enterprise-semantics-governance/blob/main/docs/finding/0003-agentic-workflow-semantic-grounding.md
- ADR-ES-AG-001: https://github.com/Enterprise-Semantics/enterprise-semantics-governance/blob/main/docs/adr/0003-agentic-semantic-decision.md
- Local verbatim: `/home/hermes/Projects/Enterprise-Semantics/00_inbox/CR-ES-AG-004.md`
