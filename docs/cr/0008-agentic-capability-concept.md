<!--
CR-ES-AG-008 ;;; dash-normalized
Verbatim original: 00_inbox/CR-ES-AG-008.md.
-->

# CR-ES-AG-008 ;;; Agentic Capability Concept Record

**Status:** Implemented
**Implements:** ADR-ES-AG-001 §6 CR-ES-AG-008
**Authored by:** manny-es (the dedicated Enterprise-Semantics sub-agent)

---

## 1. Summary

Land the `Capability` base concept and the `Agentic Capability` profiled concept in `Enterprise-Semantics`. Capability represents an enterprise's ability to realize outcomes through coordinated resources, processes, and competencies. Agentic Capability is the Capability exhibited under agent-augmented execution conditions (Profile of Capability).

This is the **Profile-of-Profile reasoning** item flagged in the queue: the Profile characteristics (bounded autonomy, AI-augmented decision-making, adaptive behavior, human governance) apply to **Capability's outcome-realization aspect**, not to a specific bearer. This distinguishes `Agentic Capability` from `AI Agent` (which IS the bearer).

---

## 2. Profile-of-Profile reasoning (why this is not a special case)

Per FND-ES-AG-001-Grounding-Result §7, Capability grounds via WSF Capability (Tier 2). The Profile-of-Capability pattern works because:

- A **Capability** is the *what* ;; the ability to realize outcomes.
- An **Agentic Capability** is the *what, under agent-augmented execution* ;; the same ability, now realized by AI agents under human governance.
- An **AI Agent** is the *who* ;; the bearer of the Capability.
- An **Agentic Enterprise** is the *how-wide* ;; the enterprise characterized by Agentic Capabilities across its eight enterprise areas.

The Profile characteristics apply to the *outcome-realization aspect* ;; not to a specific bearer. This is what distinguishes Capability profiles from Agent profiles.

---

## 3. Deliverables

- `concepts/capability.concept.yaml` ;; `Capability` concept record (Candidate, v0.1.0). Specializes WSF Capability.
- `concepts/agentic-capability.concept.yaml` ;; `Agentic Capability` concept record (Candidate, v0.1.0). Profile of Capability, binds `ES:PROFILE:agentic-execution`.
- `docs/cr/0008-agentic-capability-concept.md` ;; this CR document (landing in governance).
- CHANGELOG.md updated to v0.9.0.

---

## 4. Conformance evidence (real run output)

```text
$ python3 conformance/check.py
NO_DRIFT (1 Profile record(s) validated)
exit: 0

$ python3 conformance/check_concepts.py
NO_DRIFT (14 Concept record(s) validated)
exit: 0
```

---

## 5. Acceptance

- Capability + Agentic Capability concept records pass concept schema validation.
- Agentic Capability binds `ES:PROFILE:agentic-execution` (per ADR-ES-AG-001 §3).
- Agentic Value Stream's `external:concept:capability` cross-reference now resolves to a real Concept id.
- CHANGELOG v0.9.0 entry recorded.
