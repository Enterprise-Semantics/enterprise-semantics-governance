<!--
CR-ES-AG-009 ;;; dash-normalized
Verbatim original: 00_inbox/CR-ES-AG-009.md.
-->

# CR-ES-AG-009 ;;; AI Agent Concept Record

**Status:** Implemented
**Implements:** ADR-ES-AG-001 §6 CR-ES-AG-009
**Preceded by:** FND-ES-AG-007 (AI Agent Semantic Grounding)
**Authored by:** manny-es (the dedicated Enterprise-Semantics sub-agent)

---

## 1. Summary

Land the `AI Agent` concept record in `Enterprise-Semantics`, grounding it as a Distinct semantic kind per FND-ES-AG-007.

This is the **gating prerequisite** for FND-ES-AG-006 (`Agentic Agent` scrutiny). Without `AI Agent` grounded, the three plausible models for `Agent / AI Agent / Agentic Agent` cannot be evaluated.

---

## 2. Deliverables

- `concepts/ai-agent.concept.yaml` ;; `AI Agent` concept record (Candidate, v0.1.0). Distinct kind, not a Profile. Grounded via WSF `Entity` + WSF `Capability`.
- `concepts/agent.concept.yaml` ;; `Agent` concept record (Candidate, v0.1.0). The generic Agent concept ;; not AI-bearing per se. Distinct from `AI Agent`.
- `docs/cr/0009-ai-agent-concept.md` ;; this CR document (landing in governance).
- `docs/finding/0007-ai-agent-semantic-grounding.md` ;; FND-ES-AG-007 (landing in governance).
- CHANGELOG.md updated to v0.7.0.

---

## 3. Conformance evidence (real run output)

```text
$ python3 conformance/check.py
NO_DRIFT (1 Profile record(s) validated)
exit: 0

$ python3 conformance/check_concepts.py
NO_DRIFT (10 Concept record(s) validated)
exit: 0
```

---

## 4. Acceptance

- AI Agent concept record passes concept schema validation.
- AI Agent concept record explicitly cites WSF grounding (Entity + Capability).
- AI Agent is Distinct, not a Profile.
- FND-ES-AG-007 surfaced to user via Finding card.
- CHANGELOG v0.7.0 entry recorded.
- Program board updated: Finding card #21 (FND-ES-AG-007) ;; Decision card #22 (this CR, Implemented).
