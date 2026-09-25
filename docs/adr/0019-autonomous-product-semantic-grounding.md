<!--
ADR-ES-017 , Autonomous Product Semantic Grounding Decision

Dash-normalized: colons (:) and semicolons (;) used consistently.
Verbatim original: 00_inbox/ADR-ES-017.md (em-dashes and ellipsis dividers preserved in source).

Status: Accepted (promoted from Proposed on 2026-09-25 per user directive message 1552885930522706062, "Audit and confirm inventory")
Decision Type: Foundational Semantic Specialization
Scope: Enterprise-Semantics
Supersedes: None
Depends on: ADR-ES-003 (Value Stream Semantic Grounding, Accepted 2026-09-23) , ADR-ES-004 (Agentic Semantic Grounding) , ADR-ES-007 (Agentic Operations Semantic Grounding, Accepted 2026-09-23) , ADR-ES-008 (Autonomous Operations Semantic Grounding, Accepted 2026-09-23) , ADR-ES-009 (Autonomous Value Stream Semantic Grounding, Accepted 2026-09-23) , ADR-ES-011 (Autonomous Enterprise Semantic Grounding, Accepted 2026-09-23) , ADR-ES-014 (Agentic Service Semantic Grounding, Accepted 2026-09-24) , ADR-ES-015 (Autonomous Service Semantic Grounding, Accepted 2026-09-25) , ADR-ES-016 (Agentic Product Semantic Grounding, Accepted 2026-09-25)
Related: CR-ES-017 (Autonomous Product Semantic Grounding, Proposed) , ADR-ES-016 (Agentic Product Semantic Grounding, Accepted 2026-09-25) , FND-ES-AG-008 (WSF Tier 1 / Tier 2 Grounding Boundary, Established 2026-09-22)

Decision: Establish Autonomous Product as a governed semantic specialization of Product describing a Product whose realization, interaction, configuration, fulfillment, or adaptation is capable of progressing through defined decisions, actions, coordination, and adaptation within specified product objectives, authority, policies, constraints, and governance boundaries without requiring human intervention for every product decision or action. Autonomous Product is a contextual specialization of the Product concept, not a new foundational type of offering, it does not redefine what a Product is, and it does not equate product with the Agent, Capability, Service, Workflow, Operations, Value Stream, AI, automation, or autonomy mechanisms through which the product may be realized. Deliberately preserves the architectural rule that Agentic and Autonomous remain orthogonal semantic dimensions per ADR-ES-001 + ADR-ES-012 + ADR-ES-014 + ADR-ES-015.

Slot note: this ADR is filed at governance repo docs/adr/0019-... Slot 0019 is the next free slot in the ES series. The ES series slot sequence is 0001 (Authority) , 0002 (Enterprise Semantic Model) , 0003 (Agentic Semantic Decision, ES-AG) , 0004 (Capability, ES) , 0005 (Value Stream, ES) , 0006 (Agentic, ES) , 0007 (Agentic Value Stream, ES) , 0008 (Agentic Workflow, ES) , 0009 (Agentic Operations, ES) , 0010 (Autonomous Operations, ES) , 0011 (Autonomous Value Stream, ES) , 0012 (Agentic Enterprise, ES) , 0013 (Autonomous Enterprise, ES) , 0014 (Agentic Capability, ES) , 0015 (Autonomous Capability, ES) , 0016 (Agentic Service, ES) , 0017 (Autonomous Service, ES) , 0018 (Agentic Product, ES) , 0019 (Autonomous Product, ES, this ADR).

Implementation: CR-ES-017 (Autonomous Product Semantic Grounding). CR-ES-017 is the implementation specification, this ADR ratifies it as a governed semantic decision.

Authored by: Emmanuel A. Otchere (cardinal author rule, 2026-09-24)
-->

ADR-ES-017 , Autonomous Product Semantic Grounding

ADR-ES-017: Autonomous Product Semantic Grounding

1. Decision

Establish Autonomous Product as a governed semantic specialization of Product.

Canonical Definition

An Autonomous Product is a Product whose realization, interaction, configuration, fulfillment, or adaptation is capable of progressing through defined decisions, actions, coordination, and adaptation within specified product objectives, authority, policies, constraints, and governance boundaries without requiring human intervention for every product decision or action.

The canonical specialization is:

Product
   |
   |-- specializes -> Autonomous Product

Autonomous Product describes the degree of independent progression of product realization.

It does not define the technology used to achieve that progression.
;;;
2. Semantic Principle

Autonomy is an independent semantic dimension from Agentic behavior.

Agentic     = how behavior is performed
Autonomous  = how independently behavior can progress
AI          = technology/capability
Automation  = execution mechanism

Therefore:

Agentic Product
      ≠
Autonomous Product

A Product may be:

* neither agentic nor autonomous;
* agentic but not autonomous;
* autonomous but not agentic;
* both agentic and autonomous.
;;;
3. Four-State Product Model

Agentic	Autonomous	Semantic characterization
No	No	Conventional Product
Yes	No	Agentic Product
No	Yes	Autonomous Product
Yes	Yes	Agentic and Autonomous Product

The fourth state is a combined semantic characterization, not a new foundational type.
;;;
4. Autonomous Product Realization

The conceptual realization pattern is:

Product Objective
        ->
Product Context
        ->
Sense / Assess
        ->
Decision
        ->
Action Selection
        ->
Product Execution
        ->
Observe Outcome
        ->
Adapt
        ↺

The progression is bounded by:

Objective
   ->
Authority
   ->
Policy
   ->
Constraints
   ->
Governance
   ->
Escalation

Autonomy therefore means bounded independent progression, not unrestricted operation.
;;;
5. Autonomy Materiality

An Autonomous Product must demonstrate material independent progression.

Evidence may include:

* independent product decisions;
* independent selection of permitted actions;
* autonomous configuration;
* autonomous coordination;
* autonomous fulfillment progression;
* contextual adaptation;
* autonomous exception handling;
* autonomous progression toward product objectives.

The mere presence of:

* software;
* APIs;
* automation;
* AI;
* an Agent;
* machine learning;
* event-driven execution;

does not establish Autonomous Product.
;;;
6. Human Participation

Human participation remains compatible with autonomy.

An Autonomous Product may operate using:

* human-in-the-loop;
* human-on-the-loop;
* human-over-the-loop;
* approval gates;
* exception intervention;
* escalation;
* supervisory governance.

Autonomous Product therefore does not mean:

* human-free;
* unattended;
* uncontrolled;
* governance-free;
* unlimited;
* irreversible.
;;;
7. Canonical Relationships

Where target concepts and predicates are canonical:

Autonomous Product
    +-- specializes -> Product
    +-- operates-within -> Authority
    +-- governed-by -> Policy
    +-- constrained-by -> Constraint
    +-- pursues -> Objective
    +-- responds-to -> Context
    +-- produces -> Outcome
    +-- adapts-to -> Context
    +-- uses -> Workflow
    +-- uses -> Agentic Workflow
    +-- supported-by -> Autonomous Operations
    +-- supports -> Capability
    +-- delivered-through -> Service
    |-- contributes-to -> Value

No relationship shall be implemented if its target concept has not been canonically established.
;;;
8. Agentic / Autonomous Boundary

The following distinctions are mandatory:

Agentic Product
    -> material agentic behavior
Autonomous Product
    -> independent progression
Agentic + Autonomous Product
    -> both characteristics

An Autonomous Product does not automatically become an Agentic Product.

An Agentic Product does not automatically become an Autonomous Product.
;;;
9. AI Boundary

AI is not required.

AI-enabled Product
      ≠
Autonomous Product

AI may support autonomous product behavior, but autonomy must be demonstrated through independent decision and action progression.
;;;
10. Automation Boundary

Automation is an execution mechanism.

Automation
      ≠
Autonomy

A fully automated deterministic product mechanism does not automatically constitute an Autonomous Product.

Autonomy requires independent progression within defined objectives, authority, policies, constraints, and governance.
;;;
11. Architectural Boundaries

Product / Capability

Capability
    -> enables
Product
    ->
Autonomous Product

Autonomous Capability does not automatically make every Product it enables autonomous.

Product / Service

Autonomous Product
       ->
may be delivered-through
       ->
Service

Autonomous Service and Autonomous Product remain distinct specializations.

Product / Workflow

Autonomous Product
       ->
may use
       ->
Workflow / Agentic Workflow

Workflow remains an execution/coordination construct.

Product / Operations

Autonomous Product
       ->
may use / depend upon
       ->
Autonomous Operations

Autonomous Operations does not automatically make every Product it supports autonomous.

Product / Value Stream

Autonomous Value Stream
       ->
may involve
       ->
Autonomous Product

Autonomous Product does not imply Autonomous Value Stream.
;;;
12. OTCHERE Inc Example

Consider an OTCHERE Inc customer-resolution product.

Customer Request
       ->
Autonomous Customer Resolution Product
       ->
Assess Customer Context
       ->
Determine Product Objective
       ->
Evaluate Authority / Policy / Constraints
       ->
Select Permitted Resolution
       ->
Execute Resolution
       ->
Observe Outcome
       ->
Adapt / Escalate

The product is autonomous because it can progress through material product decisions and actions without requiring human intervention for each decision.

A human may still intervene for exceptions, high-risk cases, or decisions outside delegated authority.
;;;
13. Rejected Interpretations

The following are rejected:

* Autonomous Product = AI Product
* Autonomous Product = Automated Product
* Autonomous Product = Agentic Product
* Autonomous Product = Product containing an Agent
* Autonomous Product = Product with no humans
* Autonomous Product = Product with unlimited authority
* Autonomous Product = Autonomous Service
* Autonomous Product = Autonomous Capability
* Autonomous Product = Autonomous Workflow
* Autonomous Product = Autonomous Operations
* Autonomous Product = Autonomous Value Stream
* Autonomous Product = Autonomous Enterprise
;;;
14. Deferred Concepts

This ADR does not establish:

* Autonomous Offering;
* Product autonomy maturity;
* autonomy levels;
* Autonomous Portfolio;
* Autonomous Agent;
* Autonomous Product Agent;
* Autonomous Ecosystem;
* Autonomous Enterprise beyond ADR-ES-011.
;;;
15. Governance

Implementation is authorized only through:

CR-ES-017: Autonomous Product Semantic Grounding

No WSF or OpenDEA implementation changes are authorized.
;;;
16. Release

Target:

Enterprise-Semantics v1.6.0
