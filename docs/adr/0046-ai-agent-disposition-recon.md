# ADR-ES-037 ; AI Agent Semantic Disposition Recon

Status: Proposed
Date: 2026-09-28
Deciders: eaojnr
Semantic Area: Agent, Artificial Intelligence
Candidate: AI Agent
Predecessors: ES-ADR-004, ES-ADR-022
Target: Disposition decision, not automatic canonicalization

## 1. Decision

The recon SHALL determine whether the candidate represents a semantic concept, a characteristic/profile, an implementation pattern, a technology-dependent realization, or terminology that should remain non-canonical.

Expected disposition: Technology-qualified Agent / implementation specialization. SHALL NOT replace or redefine Agent.

## 2. Required Recon Questions

The recon SHALL establish: Is AI Agent a canonical specialization of Agent or a technology characterization ?

It SHALL examine whether the candidate provides semantic information not already captured through the existing canonical taxonomy (Agent, Agentic, Autonomous, Closed Loop, Operations, etc.).

## 3. Negative Boundary Tests

The recon SHALL reject equivalences:

- Agentic != AI
- Agent != AI Agent
- AI Agent ⊂ Agents implemented using AI

## 4. Critical Tests

| Combination | Expected disposition |
|-------------|----------------------|
| Agent without AI | Valid |
| AI without Agent behavior | Valid |
| AI Agent without autonomy | Valid |
| AI Agent with autonomy | Valid |
| Agentic Agent without AI | Valid |
| Autonomous Agent without AI | Valid |
| AI Agent + Agentic | Valid |
| AI Agent + Autonomous | Valid |
| AI Agent + Agentic + Autonomous | Valid |

This preserves the ES-022 orthogonality model.

## 5. Disposition

Candidate disposition: Technology-qualified Agent / implementation specialization. SHALL NOT replace or redefine Agent.

Canonicalization requires evidence that the term provides semantic information not already captured through the existing taxonomy.

## 6. Author

Emmanuel A. Otchere (cardinal author rule, 2026-09-24)
