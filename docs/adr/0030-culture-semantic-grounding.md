# ADR-ES-026 ; Culture Semantic Grounding

Status: Accepted
Date Accepted: 2026-09-25
Decision Type: Foundational Definition
Semantic Version Target: v2.4.0
Scope: Enterprise-Semantics
Depends On: ADR-ES-022 ; Recon-ES-003
Implementation: CR-ES-026

1. Decision

Establish Culture as a canonical foundational semantic concept within Enterprise-Semantics.

Canonical Definition

Culture is the shared pattern of values, norms, beliefs, practices, expectations, and behavioral conventions through which an Organization shapes how its members and participants understand, coordinate, and conduct organizational activity.

The specialization is:

Entity
   |
   +-- specializes -> Organization
       |
       +-- specializes -> Culture

Per ADR-ES-022 section 9, this ADR does NOT create Culture as a specialization of any existing concept. Culture is a foundational concept in its own right.

2. Rationale

Per Recon-ES-003 (Culture Foundational Dependency Recon, 2026-09-25):

- Culture is NOT redundant with Organization, Governance, Policy, Capability, Role, or Process.
- Culture performs distinctive semantic work: normative coherence, behavioral conventions, interpretive lens, coordination of meaning, values + beliefs + practices.
- Culture SHALL NOT be defined around technology, AI, agents, autonomy, or organizational transformation.

3. Semantic Principle

Culture is normative + interpretive.

Culture concerns:
- shared meaning across members
- expected patterns of conduct
- collective interpretation of organizational situation
- shared understanding enabling coordinated action
- the broad pattern that shapes organizational behavior

Culture is NOT:
- structure (Organization)
- formal framework (Governance, Policy, Authority)
- activity sequence (Process)
- functional ability (Capability)
- IT system

4. Materiality Requirement

A Culture must exhibit material shared meaning across members.

Evidence may include:
- shared values
- shared norms
- shared beliefs
- shared practices
- shared expectations
- shared behavioral conventions

The following do not establish Culture by themselves:
- organizational structure
- governance framework
- policy codification
- individual behavior

5. Canonical Relationships

Where the target concepts are canonical, Culture may:

* specializes -> Entity (Culture is a foundational concept)
* supports -> Organization (Culture shapes Organization behavior)
* shapes -> Governance (Culture influences Governance interpretation)
* shapes -> Policy (Culture influences Policy interpretation)
* shapes -> Authority (Culture influences Authority exercise)
* shapes -> Accountability (Culture influences Accountability honored-ness)
* shapes -> Capability (Culture shapes how Capability is exercised)
* shapes -> Process (Culture shapes how Process is conducted)
* shapes -> Decision (Culture shapes how Decision is made)
* shapes -> Adaptation (Culture shapes how Adaptation occurs)

Relationships must not introduce non-canonical concepts merely to complete the model.

6. Boundary Conditions

Culture is explicitly not:
- Organization
- Governance
- Policy
- Authority
- Process
- Capability
- Agentic Culture
- Autonomous Culture
- AI Culture
- Technology Culture

7. Illustrative Example

For OTCHERE Inc, Culture could include organizational norms under which:
- shared values include accountability + adaptation + collaboration
- shared norms govern how decisions are interpreted
- shared practices shape how work is coordinated
- shared behavioral conventions establish how exceptions are handled

The example is illustrative and does not itself establish a canonical instance.

8. Deferred Concepts

This ADR does not establish:
- Agentic Culture (ES-023, separate specialization)
- Autonomous Culture (ES-024, separate specialization)
- Cultural Maturity
- Cultural Transformation
- Subculture

9. Decision Outcome

Culture is established as a foundational canonical concept.

The concept is released at v2.4.0, subject to successful implementation through CR-ES-026 and conformance validation.

Author: Emmanuel A. Otchere (cardinal author rule, 2026-09-24)


## Promotion Note

Promoted via 2-touchpoint ritual per ES series ADR-ES-001 section 10-11.

Per user directive message 1553040695345025105 + Culture-System_Resolution.md, this foundational tranche was filed + implemented + promoted after Foundation Recon (Recon-ES-003).

Key architectural consequences:

- Culture is now a foundational canonical concept in Enterprise-Semantics.
- Culture specializes Entity (not Organization, Governance, Policy, etc.).
- Per Recon-ES-003, Culture is NOT reducible to Organization/Governance/Policy/Process/Capability.
- Culture is the canonical base for ES-023 (Agentic Culture) + ES-024 (Autonomous Culture).
- Dependency gate RESOLVED for ES-023 + ES-024.

Status: Accepted. Date Accepted: 2026-09-25.

Emmanuel A. Otchere (cardinal author rule, 2026-09-24).
