Proceeding from the established ES-022 semantic-integrity gate, ADR/CR-ES-024 remains Autonomous Culture, and the next candidate should be evaluated rather than mechanically paired. The next concept selected here is Agentic System, because System is a foundational enterprise/semantic concept and the agentic distinction can be materially expressed at the system operating boundary.

ADR-ES-024 : Autonomous Culture

ADR-ES-024 : Autonomous Culture Semantic Grounding

Status: Accepted
Date Accepted: 2026-09-25
Semantic Version: v2.2.0
Scope: Enterprise-Semantics
Depends on: ADR-ES-008, ADR-ES-020, ADR-ES-021, ADR-ES-022, ADR-ES-023
Implementation: CR-ES-024

1. Decision

Establish Autonomous Culture as a canonical specialization of Culture.

Canonical Definition

An Autonomous Culture is a Culture in which organizational norms, values, practices, and expectations materially support independent decision-making, delegated action, adaptive behavior, and reduced reliance on human intervention within defined objectives, authority, policies, constraints, accountability, and governance boundaries.

The specialization is expressed as:

Culture
   |
   +--- specializes
          ->
   Autonomous Culture

Culture must already be canonical. This ADR does not establish, infer, or create the Culture concept.

2. Semantic Rationale

Autonomy is not equivalent to technology, AI, automation, or the absence of humans.

Within Enterprise-Semantics:

Agentic    = mode of operation
Autonomous = characteristic of independent progression
AI         = technology / computational capability
Automation = execution mechanism

Autonomous Culture therefore describes the cultural conditions that normalize, support, govern, and reinforce bounded independent progression.

The semantic change is cultural rather than technological.

It concerns expectations and norms surrounding:

* delegated decision authority;
* authorized independent action;
* exception-based human intervention;
* adaptive behavior;
* outcome accountability;
* trust in delegated execution;
* escalation;
* governance;
* organizational learning.

3. Materiality Requirement

A Culture qualifies as Autonomous Culture only where autonomy materially affects cultural norms, practices, expectations, or decision conventions.

Evidence may include:

* defined autonomous decision rights;
* expectations that authorized decisions proceed without per-decision approval;
* exception-based intervention norms;
* accountability for outcomes rather than every individual action;
* accepted autonomous adaptation;
* explicit authority and escalation boundaries;
* institutionalized trust and verification practices;
* organizational learning from autonomous outcomes.

The following do not establish Autonomous Culture by themselves:

* AI adoption;
* automation;
* deployment of autonomous software;
* use of Agents;
* autonomous systems;
* Autonomous Operations;
* Autonomous Organization;
* Autonomous Enterprise;
* reduced headcount;
* digital transformation.

4. Autonomous Cultural Realization

The canonical conceptual pattern is:

Organizational Objective
        ->
Delegated Authority
        ->
Autonomy Expectations
        ->
Independent Decision / Action
        ->
Outcome Observation
        ->
Adaptive Behavior
        ->
Exception / Escalation
        ->
Organizational Learning
        ↺

The pattern is bounded by:

Authority
Policy
Constraint
Governance
Accountability
Escalation

Autonomous Culture therefore establishes the cultural context for bounded autonomy, rather than defining the autonomous behavior of an Organization, Operation, Service, Product, Offering, or Enterprise.

5. Agentic and Autonomous Orthogonality

Agentic and Autonomous remain independent dimensions.

Agentic	Autonomous	Cultural characterization
No	No	Conventional Culture
Yes	No	Agentic Culture
No	Yes	Autonomous Culture
Yes	Yes	Agentic + Autonomous Culture

No inheritance is implied between Agentic Culture and Autonomous Culture.

Specifically:

Autonomous Culture ≠ Agentic Culture
Agentic Culture    ≠ Autonomous Culture

A culture can support autonomous decision-making without requiring agentic behavior, and it can support agentic behavior without establishing autonomous progression.

6. Human Participation

Autonomous Culture does not imply a human-free organization.

Humans may retain responsibility for:

* objectives;
* strategy;
* governance;
* authority delegation;
* policy;
* constraints;
* accountability;
* exception handling;
* escalation;
* organizational learning.

The defining distinction is that human intervention is not required for every decision or action within an explicitly authorized autonomous boundary.

7. Canonical Relationships

Where the target concepts are canonical, Autonomous Culture may:

* specialize -> Culture
* support -> Autonomous Organization
* support -> Agentic Organization
* shape -> Delegation Practice
* shape -> Authority Practice
* shape -> Accountability Practice
* shape -> Intervention Practice
* shape -> Escalation Practice
* shape -> Decision Practice
* shape -> Adaptation Practice
* support -> Autonomous Operations
* support -> Agentic Operations
* engage-with -> Agent
* respond-to -> Organizational Context
* contribute-to -> Organizational Outcome

Relationships must not introduce non-canonical concepts merely to complete the model.

8. Boundary Conditions

Autonomous Culture is explicitly not:

* Autonomous Organization;
* Autonomous Enterprise;
* Autonomous Operations;
* Autonomous Workflow;
* Autonomous Service;
* Autonomous Product;
* Autonomous Offering;
* Agentic Culture;
* AI Culture;
* Automated Culture;
* human-free culture;
* absence of governance;
* absence of accountability;
* unlimited autonomy.

9. Illustrative Example

For OTCHERE Inc, an Autonomous Culture could include organizational norms under which authorized operational decisions proceed without individual human approval, while:

* authority boundaries are explicit;
* policies constrain action;
* outcomes remain accountable;
* exceptions trigger escalation;
* humans retain governance responsibility;
* autonomous outcomes feed organizational learning.

The example is illustrative and does not itself establish a canonical instance.

10. Deferred Concepts

This ADR does not establish:

* Agentic Management;
* Autonomous Management;
* Agentic Leadership;
* Autonomous Leadership;
* Agentic Workforce;
* Autonomous Workforce;
* Cultural Autonomy Maturity;
* Organizational Autonomy Maturity;
* Autonomous Ecosystem;
* Autonomous Network.

11. Decision Outcome

Autonomous Culture is established as a canonical specialization of Culture.

The concept is released at v2.2.0, subject to successful implementation through CR-ES-024 and conformance validation.


Author: Emmanuel A. Otchere (cardinal author rule, 2026-09-24)


## Promotion Note

Promoted via 2-touchpoint ritual per ES series ADR-ES-001 section 10-11.

Per user directive message 1553040695345025105 + Culture-System_Resolution.md, this specialization tranche was implemented + promoted after foundational Culture (ES-026) was established.

Dependency gate RESOLVED: parent Culture concept is now canonical on origin/main per ADR-ES-026 + CR-ES-026 Accepted.

Status: Accepted. Date Accepted: 2026-09-25.

Emmanuel A. Otchere (cardinal author rule, 2026-09-24).
