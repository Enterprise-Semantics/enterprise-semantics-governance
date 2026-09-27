<!--
ADR-ES-016 , Agentic Product Semantic Grounding Decision

Dash-normalized: colons (:) and semicolons (;) used consistently.
Verbatim original: 00_inbox/ADR-ES-016.md (em-dashes and ellipsis dividers preserved in source).

Status: Accepted (promoted from Proposed on 2026-09-25 per user directive message 1552856516682317857, "Save, understand and implement accordingly")
Decision Type: Foundational Semantic Specialization
Scope: Enterprise-Semantics
Supersedes: None
Depends on: ADR-ES-003 (Value Stream Semantic Grounding, Accepted 2026-09-23) , ADR-ES-004 (Agentic Semantic Grounding) , ADR-ES-005 (Agentic Value Stream Semantic Grounding, Accepted 2026-09-23) , ADR-ES-006 (Agentic Workflow Semantic Grounding, Accepted 2026-09-23) , ADR-ES-007 (Agentic Operations Semantic Grounding, Accepted 2026-09-23) , ADR-ES-012 (Agentic Capability Semantic Grounding, Accepted 2026-09-24) , ADR-ES-014 (Agentic Service Semantic Grounding, Accepted 2026-09-24) , ADR-ES-015 (Autonomous Service Semantic Grounding, Accepted 2026-09-25)
Related: CR-ES-016 (Agentic Product Semantic Grounding, Proposed) , ADR-ES-017 (Autonomous Product Semantic Grounding, Deferred per ADR-ES-016 §19) , FND-ES-AG-008 (WSF Tier 1 / Tier 2 Grounding Boundary, Established 2026-09-22)

Decision: Establish Agentic Product as a governed semantic specialization of Product describing a Product whose material realization, interaction, configuration, adaptation, or fulfillment incorporates agentic behavior in interpreting intent, selecting or coordinating actions, or adapting product behavior toward an intended outcome within defined authority, policy, and contextual boundaries. Agentic Product is a contextual specialization of the Product concept, not a new foundational type of offering, it does not redefine what a Product is, and it does not equate product with the Agent, Capability, Service, Workflow, Operations, Value Stream, AI, automation, or autonomy mechanisms through which the product may be realized. Deliberately avoids premature canonicalization of Autonomous Product, AI Product, Product maturity, Product autonomy levels, Autonomous Offering, Agentic Offering, Agentic Portfolio, Autonomous Portfolio, Product Agent, Autonomous Agent, Agentic Ecosystem, Autonomous Ecosystem.

Slot note: this ADR is filed at governance repo docs/adr/0018-... Slot 0018 is the next free slot in the ES series. The ES series slot sequence is 0001 (Authority) , 0002 (Enterprise Semantic Model) , 0003 (Agentic Semantic Decision, ES-AG) , 0004 (Capability, ES) , 0005 (Value Stream, ES) , 0006 (Agentic, ES) , 0007 (Agentic Value Stream, ES) , 0008 (Agentic Workflow, ES) , 0009 (Agentic Operations, ES) , 0010 (Autonomous Operations, ES) , 0011 (Autonomous Value Stream, ES) , 0012 (Agentic Enterprise, ES) , 0013 (Autonomous Enterprise, ES) , 0014 (Agentic Capability, ES) , 0015 (Autonomous Capability, ES) , 0016 (Agentic Service, ES) , 0017 (Autonomous Service, ES) , 0018 (Agentic Product, ES, this ADR).

Implementation: CR-ES-016 (Agentic Product Semantic Grounding). CR-ES-016 is the implementation specification, this ADR ratifies it as a governed semantic decision.

Authored by: Emmanuel A. Otchere (cardinal author rule, 2026-09-24)
-->

ADR-ES-016 , Agentic Product Semantic Grounding

ADR-ES-016: Agentic Product Semantic Grounding

1. Decision

Establish Agentic Product as a governed semantic specialization of Product, where the product’s material realization, interaction, configuration, adaptation, or fulfillment incorporates agentic behavior within defined intent, authority, policy, and contextual boundaries.

Canonical Definition

An Agentic Product is a Product whose material realization, interaction, configuration, adaptation, or fulfillment incorporates agentic behavior in interpreting intent, selecting or coordinating actions, or adapting product behavior toward an intended outcome within defined authority, policy, and contextual boundaries.

The semantic relationship is:

Product
   |
   |-- specializes -> Agentic Product

Agentic Product does not redefine Product.

It establishes a specialization based on the mode through which product value is realized or product behavior is delivered, rather than on the technology used to implement the product.
;;;
2. Semantic Rationale

Products represent something intentionally offered to a stakeholder or consumer for the realization of intended value.

An Agentic Product introduces an additional semantic characteristic:

Product
   +
Material Agentic Realization
   =
Agentic Product

The presence of AI, automation, an Agent, software, APIs, machine learning, or adaptive technology does not by itself establish an Agentic Product.

The agentic characteristic must materially affect how the product:

* interprets delegated or communicated intent;
* evaluates contextual conditions;
* selects or coordinates actions;
* adapts product behavior;
* determines or adjusts fulfillment;
* responds to exceptions;
* progresses toward an intended outcome.
;;;
3. Architectural Position

Agentic Product belongs at the Product realization boundary, distinct from the Capability, Service, Workflow, Operations, Value Stream, and Enterprise boundaries.

Enterprise
    |
    +-- Capability
    |      |-- Agentic Capability
    |
    +-- Product
    |      |-- Agentic Product
    |
    +-- Service
    |      +-- Agentic Service
    |      |-- Autonomous Service
    |
    |-- Value Stream
           +-- Agentic Value Stream
           |-- Autonomous Value Stream

This establishes parallel specialization without collapsing the concepts into one another.
;;;
4. Product vs Agentic Product

Dimension	Product	Agentic Product
Semantic identity	Product	Product specialization
Value orientation	Provides intended product value	Provides product value through material agentic realization
Intent	Product purpose/intent	May interpret delegated or contextual intent
Behavior	Defined product behavior	Behavior can involve agentic interpretation and action selection
Decision behavior	May be predetermined or externally controlled	Material decisions may be selected within defined authority
Adaptation	May be configured or externally adapted	Product realization may adapt contextually
Authority	May not be an explicit property	Required where agentic action occurs
AI	Not required	Not required
Automation	Not required	Not sufficient
Agent	Not required	May engage an Agent
Human participation	Valid	Valid
Autonomy	Not implied	Not implied
;;;
5. Agentic Product Is Not

Agentic Product shall not be semantically equated with:

* AI Product
* AI-enabled Product
* Automated Product
* Autonomous Product
* Agent
* AI Agent
* Agentic Capability
* Agentic Service
* Agentic Workflow
* Agentic Operations
* Agentic Value Stream
* Agentic Enterprise

In particular:

AI Product ≠ Agentic Product
Automated Product ≠ Agentic Product
Agentic Product ≠ Autonomous Product

An AI system can be incorporated into a Product without making the Product agentic.

A Product can be agentic without using AI.

A Product can be agentic without being autonomous.
;;;
6. Agentic Materiality

An Agentic Product must demonstrate material agentic realization.

The agentic behavior must affect a substantive aspect of the product’s realization or interaction.

Examples include:

* interpreting consumer intent;
* selecting among permitted product behaviors;
* dynamically configuring a product response;
* coordinating product components;
* adapting product behavior to context;
* selecting fulfillment actions;
* interpreting exceptions;
* determining when escalation is required.

The following are insufficient by themselves:

* inclusion of an AI model;
* use of machine learning;
* use of an API;
* automated execution;
* conversational interaction;
* recommendation functionality;
* presence of an Agent somewhere in the implementation;
* dynamic software behavior without delegated intent and bounded action selection.
;;;
7. Canonical Relationships

Where the target concepts and predicates are already canonical, Agentic Product may participate in the following relationships:

Agentic Product
    +-- specializes -> Product
    +-- engages -> Agent
    +-- interprets -> Intent
    +-- operates-within -> Authority
    +-- governed-by -> Policy
    +-- constrained-by -> Constraint
    +-- uses -> Agentic Workflow
    +-- produces -> Outcome
    +-- adapts-to -> Context
    +-- supports -> Capability
    +-- delivered-through -> Service
    |-- contributes-to -> Value

These relationships do not imply that every Agentic Product must contain or use every listed concept.

CR-ES-016 shall implement only relationships whose target concepts and predicates are already canonically available.

No foundational concept shall be silently introduced to satisfy a relationship.
;;;
8. Agentic Product Realization Boundary

The conceptual realization pattern is:

Product Intent
      ->
Agentic Product
      ->
Product Context
      ->
Interpret Intent
      ->
Assess Context
      ->
Select / Coordinate Action
      ->
Product Execution
      ->
Product Outcome
      ->
Adapt / Escalate
      ↺

The entire product does not need to operate agentically.

An Agentic Product may contain conventional, automated, human-mediated, and agentic realization mechanisms simultaneously.
;;;
9. Product / Service Boundary

Product and Service must remain distinct.

PRODUCT
What is offered for stakeholder/consumer value realization
        |
        +-- Agentic Product
        |
        |-- may be delivered-through ->
                         SERVICE
                           |
                           +-- Agentic Service
                           |-- Autonomous Service

An Agentic Service does not automatically make the Product Agentic.

Conversely, an Agentic Product may employ conventional or agentic services.

The classification depends on where the material agentic behavior resides.
;;;
10. Product / Capability Boundary

Capability represents an enduring ability.

Product represents an offered realization of value.

Therefore:

Capability
   |
   |-- may enable -> Product
                         |
                         |-- Agentic Product
Agentic Capability
   |
   |-- may enable -> Agentic Product

An Agentic Capability does not automatically make every Product it enables agentic.

Agentic materiality must be demonstrated at the Product boundary.
;;;
11. Product / Value Stream Boundary

An Agentic Value Stream describes agentic behavior at the end-to-end value-realization boundary.

An Agentic Product describes agentic behavior at the product boundary.

Agentic Value Stream
        |
        +-- realizes -> Stakeholder Value
        |
        |-- may involve -> Agentic Product

Therefore:

Agentic Product ≠ Agentic Value Stream

A conventional Product may participate in an Agentic Value Stream.

An Agentic Product may participate in a conventional, Agentic, or Autonomous Value Stream.
;;;
12. Agentic / Autonomous Orthogonality

Agentic and Autonomous remain independent semantic dimensions.

                    AUTONOMOUS
                       |
             No        |        Yes
        +--------------┼--------------+
Agentic |              |              |
   No   | Conventional  | Autonomous   |
        | Product       | Product      |
        +--------------┼--------------┤
   Yes  | Agentic       | Agentic +    |
        | Product       | Autonomous   |
        |--------------┴--------------┘

Therefore:

* Agentic Product does not imply Autonomous Product.
* Autonomous Product does not imply Agentic Product.
* A Product may be both.
* A Product may be neither.

Autonomous Product is not established by this ADR.

If required, it shall be established through a separate ADR and CR.
;;;
13. AI Boundary

AI is an implementation or technological capability dimension.

It is not the semantic basis of Agentic Product.

AI
 |-- may enable -> Agentic behavior
Agentic behavior
 |-- may exist without -> AI

Therefore:

AI-enabled Product ≠ Agentic Product.

An AI component may support an Agentic Product, but the product’s agentic character must be established from its behavior and realization semantics.
;;;
14. Automation Boundary

Automation describes execution through predetermined mechanisms.

Agentic behavior involves interpretation, action selection, coordination, adaptation, or equivalent behavior within delegated authority.

Therefore:

Automation -> executes predetermined behavior
Agentic behavior -> interprets context and selects permitted behavior

Automation may be part of an Agentic Product, but automation alone does not establish one.
;;;
15. Human Participation

Human participation remains semantically valid.

An Agentic Product may employ:

* human-in-the-loop interaction;
* human-on-the-loop oversight;
* human-over-the-loop governance;
* approval gates;
* exception-based intervention;
* escalation;
* human-controlled boundaries.

Agentic does not mean human-free.
;;;
16. Example: OTCHERE Inc

Consider an OTCHERE Inc customer resolution product.

Conventional Product

Customer Request
      ->
Customer Resolution Product
      ->
Predefined Resolution Options
      ->
Resolution

Agentic Product

Customer Intent
      ->
Agentic Customer Resolution Product
      ->
Interpret Customer Context
      ->
Determine Permitted Resolution Path
      ->
Select / Coordinate Actions
      ->
Execute Resolution
      ->
Observe Customer Outcome
      ->
Adapt or Escalate

The product is agentic because agentic behavior materially participates in the realization of the product’s intended outcome.

The use of an AI model alone would not establish this classification.
;;;
17. Architectural Invariants

The following invariants are established:

1. Agentic Product is a specialization of Product.
2. Agentic Product retains the semantic identity of Product.
3. Agentic behavior must be material to Product realization or interaction.
4. Agentic Product is outcome-oriented.
5. Agentic Product operates within defined authority.
6. Policy and constraint boundaries remain applicable.
7. Human participation is permitted.
8. AI is not required.
9. Automation is not sufficient.
10. Agentic Product does not imply Autonomous Product.
11. Agentic Product does not imply Agentic Service.
12. Agentic Product does not imply Agentic Capability.
13. Agentic Product does not imply Agentic Workflow.
14. Agentic Product does not imply Agentic Operations.
15. Agentic Product does not imply Agentic Value Stream.
16. Agentic Product does not imply Agentic Enterprise.
17. Agent is not a Product.
18. Agentic Workflow is not a Product.
19. Agentic Operations is not a Product.
20. Provenance and semantic grounding are mandatory.
;;;
18. Rejected Interpretations

The following interpretations are rejected:

* Agentic Product = AI Product
* Agentic Product = automated Product
* Agentic Product = Product containing an Agent
* Agentic Product = Product using an AI model
* Agentic Product = autonomous Product
* Agentic Product = Agentic Service
* Agentic Product = Agentic Capability
* Agentic Product = Agentic Workflow
* Agentic Product = Agentic Operations
* Agentic Product = Agentic Value Stream
* Agentic Product = Product with conversational interaction
* Agentic Product = Product with adaptive software
* Agentic Product = Product requiring no human participation
* Agentic Product = Product with unlimited authority
;;;
19. Deferred Concepts

This ADR does not establish:

* Autonomous Product
* AI Product
* Autonomous Product levels
* Product autonomy maturity
* Agentic Product maturity
* Autonomous Offering
* Agentic Offering
* Agentic Portfolio
* Autonomous Portfolio
* Product Agent
* Autonomous Agent
* Agentic Ecosystem
* Autonomous Ecosystem

Each requires independent semantic grounding if subsequently needed.
;;;
20. Consequences

Positive

* Extends the established Agentic specialization pattern to Product.
* Preserves separation between product, capability, service, workflow, operations, and value-stream semantics.
* Prevents AI-centric definitions.
* Establishes a reusable boundary for agentically realized products.
* Preserves orthogonality between Agentic and Autonomous dimensions.
* Enables future Autonomous Product grounding without semantic collision.

Negative

* Requires explicit materiality tests to distinguish genuinely agentic products from products merely containing AI or automation.
* Product semantics must be sufficiently grounded before the specialization can be treated as fully canonical.
* Additional product/offer semantics may eventually be required.

Architectural Risk

The primary risk is prematurely treating Product as equivalent to Service, Capability, or Offering.

CR-ES-016 therefore shall not silently redefine foundational Product semantics.
;;;
21. Governance

This ADR authorizes implementation through:
