<!--
CR-ES-AG-005 ;;; dash-normalized
Verbatim original: 00_inbox/CR-ES-AG-005.md.
-->

# CR-ES-AG-005 ;;; Agentic Flow Concept Record

**Status:** Implemented
**Implements:** ADR-ES-AG-001 §6 CR-ES-AG-005
**Preceded by:** FND-ES-AG-001-Grounding-Result §7 ;;; FND-ES-AG-001 §7
**Authored by:** manny-es (the dedicated Enterprise-Semantics sub-agent)

---

## 1. Summary

Land the `Flow` base concept and the `Agentic Flow` profiled concept in `Enterprise-Semantics`. Flow represents the directional movement of value, work, information, or events through an enterprise. Agentic Flow is the Flow exhibited under agent-augmented execution conditions (Profile of Flow).

Flow is the **choreographic substrate** for Workflow (per `agentic-workflow.concept.yaml` cross-reference): Workflow sequences activities, but Flow defines the direction and rate of movement through the sequence.

---

## 2. Deliverables

- `concepts/flow.concept.yaml` ;; `Flow` concept record (Candidate, v0.1.0). Specializes WSF `Process` + references WSF `Event`.
- `concepts/agentic-flow.concept.yaml` ;; `Agentic Flow` concept record (Candidate, v0.1.0). Profile of Flow, binds `ES:PROFILE:agentic-execution`.
- `docs/cr/0005-agentic-flow-concept.md` ;; this CR document (landing in governance).
- CHANGELOG.md updated to v0.8.0.

---

## 3. Conformance evidence (real run output)

```text
$ python3 conformance/check.py
NO_DRIFT (1 Profile record(s) validated)
exit: 0

$ python3 conformance/check_concepts.py
NO_DRIFT (12 Concept record(s) validated)
exit: 0
```

---

## 4. Distinguishing Flow from Workflow

- **Flow** ;; directional movement through a sequence. *What* moves.
- **Workflow** ;; a sequence of activities that produces Flow. *How* the sequence is structured.
- **Value Stream** ;; a sequence of value-creating activities (which is realized as a Flow).

These three concepts compose: Value Stream is realized via Workflow, which generates Flow.

---

## 5. Acceptance

- Flow + Agentic Flow concept records pass concept schema validation.
- Agentic Flow binds `ES:PROFILE:agentic-execution` (per ADR-ES-AG-001 §3).
- Agentic Workflow cross-reference (`agentic-flow`) now resolves to a real Concept id.
- CHANGELOG v0.8.0 entry recorded.
