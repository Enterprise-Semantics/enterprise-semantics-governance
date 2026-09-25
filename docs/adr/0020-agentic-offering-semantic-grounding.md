<!--
ADR-ES-018 , Agentic Offering Semantic Grounding Decision

Dash-normalized: colons (:) and semicolons (;) used consistently.
Verbatim original: 00_inbox/ADR-ES-018.md (em-dashes and ellipsis dividers preserved in source).

Status: Proposed
Decision Type: Semantic Specialization
Scope: Enterprise-Semantics
Supersedes: None
Depends on: ADR-ES-004 (Agentic Semantic Grounding) , ADR-ES-005 (Agentic Value Stream Semantic Grounding, Accepted 2026-09-23) , ADR-ES-006 (Agentic Workflow Semantic Grounding, Accepted 2026-09-23) , ADR-ES-007 (Agentic Operations Semantic Grounding, Accepted 2026-09-23) , ADR-ES-012 (Agentic Capability Semantic Grounding, Accepted 2026-09-24) , ADR-ES-014 (Agentic Service Semantic Grounding, Accepted 2026-09-24) , ADR-ES-016 (Agentic Product Semantic Grounding, Accepted 2026-09-25) , ADR-ES-017 (Autonomous Product Semantic Grounding, Accepted 2026-09-25)
Related: CR-ES-018 (Agentic Offering Semantic Grounding, Proposed) , ADR-ES-016 (Agentic Product Semantic Grounding, Accepted 2026-09-25) , ADR-ES-017 (Autonomous Product Semantic Grounding, Accepted 2026-09-25) , FND-ES-AG-008 (WSF Tier 1 / Tier 2 Grounding Boundary, Established 2026-09-22)

Decision: Establish Agentic Offering as a governed specialization of Offering describing an Offering whose composition, interaction, configuration, fulfillment, or value realization materially incorporates agentic behavior in interpreting intent, selecting or coordinating actions, or adapting the offering toward an intended stakeholder outcome within defined authority, policy, and contextual boundaries. This ADR does NOT redefine foundational Offering semantics. If Offering is not yet canonical at implementation time, CR-ES-018 shall record the dependency rather than silently creating an Offering ontology. The principal risk is treating Offering as a synonym for Product or Service. CR-ES-018 must validate the Offering dependency before canonical implementation.

Slot note: this ADR is filed at governance repo docs/adr/0020-... Slot 0020 is the next free slot in the ES series. The ES series slot sequence is 0001 (Authority) , 0002 (Enterprise Semantic Model) , 0003 (Agentic Semantic Decision, ES-AG) , 0004 (Capability, ES) , 0005 (Value Stream, ES) , 0006 (Agentic, ES) , 0007 (Agentic Value Stream, ES) , 0008 (Agentic Workflow, ES) , 0009 (Agentic Operations, ES) , 0010 (Autonomous Operations, ES) , 0011 (Autonomous Value Stream, ES) , 0012 (Agentic Enterprise, ES) , 0013 (Autonomous Enterprise, ES) , 0014 (Agentic Capability, ES) , 0015 (Autonomous Capability, ES) , 0016 (Agentic Service, ES) , 0017 (Autonomous Service, ES) , 0018 (Agentic Product, ES) , 0019 (Autonomous Product, ES) , 0020 (Agentic Offering, ES, this ADR).

Implementation: CR-ES-018 (Agentic Offering Semantic Grounding). CR-ES-018 is the implementation specification, this ADR ratifies it as a governed semantic decision. The implementation must verify the Offering dependency per ADR-ES-018 §16 + CR-ES-018 §2.

Authored by: Emmanuel A. Otchere (cardinal author rule, 2026-09-24)
-->

ADR-ES-018 , Agentic Offering Semantic Grounding

ADR-ES-018: Agentic Offering Semantic Grounding

1. Decision

Establish Agentic Offering as a governed specialization of Offering, provided that Offering is already canonically established in the Enterprise-Semantics semantic authority.

Canonical Definition

An Agentic Offering is an Offering whose composition, interaction, configuration, fulfillment, or value realization materially incorporates agentic behavior in interpreting intent, selecting or coordinating actions, or adapting the offering toward an intended stakeholder outcome within defined authority, policy, and contextual boundaries.

The specialization is:

Offering
   |
   |-- specializes -> Agentic Offering

This ADR does not redefine foundational Offering semantics.

If Offering is not yet canonical at implementation time, CR-ES-018 shall record the dependency rather than silently creating an Offering ontology.
;;;
2. Semantic Rationale

An Offering represents what an organization makes available to a stakeholder or market as a coherent proposition.

Agentic Offering introduces a distinct realization characteristic:

Offering
   +
Material Agentic Realization
   =
Agentic Offering

The agentic behavior may concern:

* interaction;
* configuration;
* composition;
* recommendation;
* fulfillment;
* orchestration;
* adaptation;
* exception handling;
* contextual value realization.

The Offering itself remains the semantic anchor.
;;;
3. Agentic Offering vs Agentic Product

These concepts must remain distinct.

Offering
   +-- may comprise / include -> Product
   |                              |-- Agentic Product
   |
   |-- Agentic Offering

An Offering may contain or compose multiple Products and Services.

Therefore:

Agentic Product ≠ Agentic Offering.

An Offering can be agentic because of the way the overall proposition is configured, composed, interacted with, fulfilled, or adapted even where its constituent Products are not individually agentic.

Conversely, an Agentic Product does not automatically make the entire Offering agentic.
;;;
4. Agentic Offering vs Agentic Service

Agentic Offering
      ->
may comprise / expose
      ->
Agentic Product / Agentic Service

Agentic Service concerns service realization.

Agentic Offering concerns the broader proposition presented to a stakeholder.

They therefore operate at different semantic boundaries.
;;;
5. Materiality

Agentic behavior must be material to the Offering.

Examples include:

* interpreting stakeholder intent;
* dynamically configuring an offering;
* dynamically composing product/service components;
* selecting fulfillment arrangements;
* coordinating multiple services;
* adapting an offering to context;
* interpreting exceptions;
* dynamically determining permitted response paths.

Insufficient evidence includes:

* an AI component somewhere in the implementation;
* automated billing;
* automated ordering;
* a chatbot used only as an interface;
* an Agent participating in an unrelated internal process.
;;;
6. Agentic / Autonomous Orthogonality

Agentic Offering does not establish Autonomous Offering.

The conceptual matrix is:

Agentic	Autonomous	Characterization
No	No	Conventional Offering
Yes	No	Agentic Offering
No	Yes	Autonomous Offering: future
Yes	Yes	Agentic + Autonomous Offering: future

Autonomous Offering requires separate governance.
;;;
7. AI Boundary

AI is not the definition of Agentic Offering.

AI-enabled Offering
       ≠
Agentic Offering

AI may support agentic offering behavior but is not required.
;;;
8. Automation Boundary

Automation is not sufficient.

Automated Offering
       ≠
Agentic Offering

Agentic realization requires contextual interpretation, action selection, coordination, adaptation, or equivalent agentic behavior.
;;;
9. Human Participation

Human participation remains valid.

An Agentic Offering may include:

* assisted interaction;
* approval;
* exception handling;
* human escalation;
* human oversight;
* human-controlled boundaries.

Agentic does not mean human-free.
;;;
10. Canonical Relationships

Where canonical targets and predicates exist:

Agentic Offering
    +-- specializes -> Offering
    +-- engages -> Agent
    +-- interprets -> Intent
    +-- operates-within -> Authority
    +-- governed-by -> Policy
    +-- constrained-by -> Constraint
    +-- uses -> Agentic Product
    +-- uses -> Agentic Service
    +-- uses -> Agentic Workflow
    +-- supports -> Capability
    +-- produces -> Outcome
    +-- adapts-to -> Context
    |-- contributes-to -> Value

These are conditional relationships, not mandatory composition rules.
;;;
11. Offering Realization Boundary

Stakeholder Intent
        ->
Agentic Offering
        ->
Interpret Context
        ->
Configure / Compose
        ->
Select / Coordinate
        ->
Fulfill
        ->
Observe Outcome
        ->
Adapt / Escalate

The Offering may employ Products, Services, Capabilities, Workflows, and Operations in realizing the proposition.
;;;
12. Value Stream Boundary

Agentic Offering and Agentic Value Stream are distinct:

Agentic Value Stream
        ->
value realization journey
        |
        |-- may involve -> Agentic Offering

Therefore:

Agentic Offering ≠ Agentic Value Stream

An Agentic Offering may participate in a conventional Value Stream, Agentic Value Stream, or Autonomous Value Stream.
;;;
13. Enterprise Boundary

An Agentic Offering does not establish:

Agentic Enterprise

An enterprise may provide an Agentic Offering without operating as an Agentic Enterprise.
;;;
14. Example: OTCHERE Inc

Consider an OTCHERE Inc integrated enterprise offering combining Products and Services.

A conventional offering:

Customer Need
      ->
OTCHERE Integrated Business Offering
      ->
Select Product
      ->
Select Service
      ->
Fulfill

An Agentic Offering:

Customer Intent
      ->
Agentic Integrated Business Offering
      ->
Interpret Customer Context
      ->
Determine Appropriate Proposition
      ->
Compose Product + Service Components
      ->
Coordinate Fulfillment
      ->
Observe Customer Outcome
      ->
Adapt / Escalate

The offering is agentic because agentic behavior materially affects the proposition’s realization, composition, interaction, or fulfillment.
;;;
15. Rejected Interpretations

The following are rejected:

* Agentic Offering = AI Offering
* Agentic Offering = Automated Offering
* Agentic Offering = Agentic Product
* Agentic Offering = Agentic Service
* Agentic Offering = Agentic Workflow
* Agentic Offering = Agentic Operations
* Agentic Offering = Agentic Value Stream
* Agentic Offering = Offering containing an Agent
* Agentic Offering = autonomous offering
* Agentic Offering = Offering with conversational UI
* Agentic Offering = Offering with an AI model
* Agentic Offering = human-free Offering
;;;
16. Foundational Dependency

This ADR intentionally does not establish the complete semantic definition of Offering.

Before CR-ES-018 is accepted as canonical, the repository must verify one of:

1. Offering already exists as a canonical Enterprise-Semantics concept; or
2. a separately authorized Offering semantic grounding ADR establishes it.

If neither condition is satisfied, implementation of the specialization shall remain blocked.
;;;
17. Consequences

Positive

* Extends agentic semantics from Product and Service to the broader Offering boundary.
* Prevents Product and Offering from becoming conflated.
* Allows composite propositions to exhibit agentic realization.
* Preserves Agentic/Autonomous orthogonality.
* Supports future autonomous offering semantics without premature canonicalization.

Risk

The principal architectural risk is treating Offering as merely a synonym for Product or Service.

CR-ES-018 must therefore validate the Offering dependency before canonical implementation.
;;;
18. Governance

Implementation is authorized through:

CR-ES-018: Agentic Offering Semantic Grounding

No WSF or OpenDEA implementation changes are authorized.
;;;
19. Release

Target:

Enterprise-Semantics v1.7.0
