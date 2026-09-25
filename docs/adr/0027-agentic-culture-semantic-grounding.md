ADR-ES-023 : Agentic Culture Semantic Grounding

ADR-ES-023 : Agentic Culture Semantic Grounding

Status: Accepted
Date Accepted: 2026-09-25
Decision Type: Semantic Definition
Semantic Version Target: v2.1.0
Scope: Enterprise-Semantics
Depends On: ADR-ES-004, ADR-ES-020, ADR-ES-022
Implementation: CR-ES-023

1. Decision

Establish Agentic Culture as a governed specialization of Culture, subject to the prerequisite that Culture itself is canonical within Enterprise-Semantics.

The canonical definition is:

An Agentic Culture is a Culture in which organizational norms, values, practices, and expectations materially support the interpretation of delegated intent, distribution of decision authority, human-agent collaboration, adaptive action, and accountable coordination involving agentic behavior.

The semantic relationship is:

Culture
   |
   +--- specializes -> Agentic Culture

Important: This ADR does not create the base Culture concept. If Culture is not yet canonical, CR-ES-023 SHALL remain blocked.



2. Rationale

Agentic transformation is not solely an operational or technological phenomenon.

An organization can possess:

* Agents;
* Agentic Workflows;
* Agentic Operations;
* Agentic Services;
* Agentic Capabilities;

without necessarily possessing an Agentic Culture.

Culture concerns the shared organizational patterns through which people interpret:

* authority;
* accountability;
* delegation;
* trust;
* collaboration;
* decision-making;
* adaptation;
* learning;
* acceptable behavior.

Agentic Culture therefore addresses a distinct semantic boundary from Agentic Organization.



3. Core Distinction

Agentic Organization
    = how the organization operates.
Agentic Culture
    = the norms and practices through which organizational
      participants understand and enact agentic behavior.

Agentic Culture is therefore neither a synonym for nor a required property of Agentic Organization.



4. Semantic Principle

Agentic Culture concerns cultural accommodation and institutionalization of agentic behavior.

It does not mean:

* AI culture;
* technology culture;
* automation culture;
* a culture controlled by Agents;
* replacement of human organizational culture;
* unrestricted delegation.



5. Materiality Requirement

A Culture SHALL NOT be classified as Agentic merely because the associated organization:

* uses AI;
* employs Agents;
* uses Agentic Workflows;
* operates Agentic Operations;
* automates processes;
* deploys autonomous systems.

Agentic Culture requires material cultural patterns related to agentic behavior.

Examples include:

* accepted delegation of defined decision rights;
* explicit human-agent collaboration norms;
* established agent accountability expectations;
* culturally accepted machine-mediated coordination;
* norms governing escalation;
* organizational learning from agentic outcomes;
* trust calibrated to delegated authority;
* expectations for adaptive organizational behavior.



6. Cultural Realization Pattern

A representative pattern is:

Organizational Values / Norms
            ->
Delegation Expectations
            ->
Authority & Accountability Norms
            ->
Human / Agent Interaction Norms
            ->
Decision & Coordination Practices
            ->
Adaptive Behavior
            ->
Learning / Reinforcement
            ->
Evolving Organizational Culture

This pattern is descriptive rather than a mandatory process model.



7. Core Relationships

Where canonical:

Agentic Culture
    +--- specializes -> Culture
    +--- supports -> Agentic Organization
    +--- shapes -> Delegation Practice
    +--- shapes -> Authority Practice
    +--- shapes -> Accountability Practice
    +--- shapes -> Collaboration Practice
    +--- shapes -> Decision Practice
    +--- supports -> Agentic Operations
    +--- supports -> Agentic Workflow
    +--- engages-with -> Agent
    +--- responds-to -> Organizational Context
    +--- contributes-to -> Organizational Outcome

Relationships SHALL only be activated when their target concepts are canonical.



8. Agentic Culture vs Agentic Organization

An Agentic Organization can exist with limited cultural institutionalization.

Conversely, an organization may develop cultural norms supportive of agentic behavior before its operational model becomes materially Agentic.

Therefore:

Agentic Culture ≠ Agentic Organization

The two concepts may be related without one being inferred from the other.



9. Agentic Culture vs Agentic Enterprise

Agentic Enterprise describes enterprise-level operation and value realization.

Agentic Culture describes cultural norms and practices.

Enterprise-level agentic behavior does not automatically establish Agentic Culture.



10. Agentic Culture vs Autonomous Culture

This ADR deliberately does not establish Autonomous Culture.

Autonomy and culture require separate analysis because cultural autonomy could mean several materially different things:

* acceptance of independent organizational decision-making;
* cultural support for reduced intervention;
* cultural delegation norms;
* cultural adaptation;
* cultural independence from human decision-makers.

These interpretations SHALL NOT be collapsed prematurely.

Autonomous Culture therefore remains an investigation candidate.



11. Human Participation

Human participation is fundamental to the semantic scope of Agentic Culture.

Agentic Culture may establish norms for:

* human-agent collaboration;
* human authority;
* agent delegation;
* escalation;
* accountability;
* review;
* intervention;
* learning.

Agentic Culture does not imply human displacement.



12. AI and Automation Independence

AI is not required.

Automation is not sufficient.

An Agentic Culture may support agentic behavior implemented through:

* human participants;
* software Agents;
* AI-enabled Agents;
* organizational rules;
* services;
* systems;
* workflows;
* combinations thereof.

The semantic property concerns cultural behavior, not technology.



13. Governance

Agentic Culture SHALL remain compatible with:

Authority
Policy
Constraint
Governance
Accountability
Escalation

Cultural acceptance of delegation does not establish unrestricted authority.



14. Enterprise Example

Within OTCHERE Inc, an Agentic Culture could include organizational norms that:

* explicitly distinguish delegated and retained decision rights;
* expect people and Agents to collaborate within defined authority;
* require accountability for agent-mediated decisions;
* normalize escalation when authority boundaries are exceeded;
* encourage adaptive responses to changing context;
* treat agentic outcomes as inputs to organizational learning;
* establish trust according to demonstrated scope and evidence rather than assuming unrestricted trust.

This is an illustrative pattern, not a canonical organizational prescription.



15. Deferred Concepts

This ADR does not establish:

* Autonomous Culture;
* Agentic Management;
* Autonomous Management;
* Agentic Leadership;
* Autonomous Leadership;
* Agentic Workforce;
* Autonomous Workforce;
* Agentic Organizational Maturity;
* Autonomous Cultural Maturity.

These require independent semantic decisions.



16. Consequences

Positive

* Extends agentic semantics into the cultural boundary.
* Separates cultural change from organizational operating change.
* Prevents “Agentic Culture” from becoming an AI-centric concept.
* Provides a semantic foundation for future organizational transformation analysis.
* Preserves human accountability and governance.

Constraints

* Culture must first be canonical.
* Cultural materiality must be demonstrated.
* Autonomous Culture remains unresolved.
* Agentic Culture cannot be inferred from Agentic Organization.



17. Decision Outcome

Agentic Culture is established as a candidate specialization of Culture, subject to the canonicalization dependency on Culture.

Target semantic release:

Enterprise-Semantics v2.1.0, conditional on the Culture dependency being satisfied.


Author: Emmanuel A. Otchere (cardinal author rule, 2026-09-24)


## Promotion Note

Promoted via 2-touchpoint ritual per ES series ADR-ES-001 section 10-11.

Per user directive message 1553040695345025105 + Culture-System_Resolution.md, this specialization tranche was implemented + promoted after foundational Culture (ES-026) was established.

Dependency gate RESOLVED: parent Culture concept is now canonical on origin/main per ADR-ES-026 + CR-ES-026 Accepted.

Status: Accepted. Date Accepted: 2026-09-25.

Emmanuel A. Otchere (cardinal author rule, 2026-09-24).
