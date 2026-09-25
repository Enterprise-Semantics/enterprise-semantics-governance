# ADR-ES-021 , Offering Canonical Grounding

Status: Accepted
Date Accepted: 2026-09-25
Date: 2026-09-25
Decision Type: Foundational Concept Grounding
Priority: P0
Target: Enterprise-Semantics
Authorizing Decision: ADR-ES-021
Target Release: v1.8.1
Author: Emmanuel A. Otchere (cardinal author rule, 2026-09-24)

## 1. Decision

Establish Offering as a canonical foundational concept in Enterprise-Semantics, prior to or concurrent with the Agentic Offering and Autonomous Offering specializations.

Canonical Definition

An Offering is a coordinated bundle of Products, Services, and Capabilities that an enterprise or organizational unit commits to make available to a Customer (internal or external) in order to satisfy a defined Customer Need, within defined Authority, Policy, Constraints, and Governance, and that progresses through Offering Context Assessment, Configuration, Composition, Fulfillment, and Value Realization to produce Customer Outcome.

The foundational concept is:

Offering
   is a
Coordinated Bundle of Products + Services + Capabilities
   with
Objective ;; Context ;; Authority ;; Policy ;; Constraints ;; Governance
   progressing through
Context Assessment -> Configuration -> Composition -> Fulfillment -> Value Realization
   producing
Customer Outcome

This ADR establishes the foundational concept. Specializations are governed separately.

## 2. Why Offering Is a Distinct Boundary

Offering is not equivalent to:

- Product
- Service
- Capability
- Portfolio
- Value Stream
- Enterprise

An Offering establishes a coordinated bundle boundary that addresses a Customer Need through configuration, composition, fulfillment, and value realization, distinct from any single constituent.

## 3. Foundational Principle

An Offering is identified by:

- the Customer Need it addresses
- the Customer Outcome it produces
- the coordinated bundle of Products + Services + Capabilities it composes
- the Authority, Policy, Constraints, and Governance under which it operates
- the Offering Context within which it is configured and fulfilled
- the progression from context assessment through value realization

The progression operates within:

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

## 4. Canonical Relationships

Where canonical predicates and target concepts exist:

Offering
    , addresses -> Customer Need
    , composes -> Product
    , composes -> Service
    , exercises -> Capability
    , pursues -> Objective
    , responds-to -> Context
    , operates-within -> Authority
    , governed-by -> Policy
    , constrained-by -> Constraint
    , fulfilled-through -> Fulfillment Process
    , produces -> Customer Outcome
    , realizes -> Value
    , escalates-through -> Escalation Boundary

These are foundational relationships. No missing foundational concept shall be silently created.

## 5. Product / Service / Capability Boundaries

Offering composes Products + Services + Capabilities:

Offering
    -> composes -> Product
    -> composes -> Service
    -> exercises -> Capability

However:

Offering is-a Product
Offering is-a Service
Offering is-a Capability

These four statements must fail conformance unless separately authorized.

Product is-a Offering
Service is-a Offering
Capability is-a Offering

These four statements must fail conformance unless separately authorized.

## 6. Value Stream Boundary

Offering participates in Value Stream:

Value Stream
    -> involves -> Offering

However:

Offering is-a Value Stream

must fail conformance.

Offering
        !=
Value Stream

## 7. Enterprise Boundary

Enterprise offers Offerings:

Enterprise
    -> offers -> Offering

However:

Offering is-a Enterprise

must fail conformance.

Offering
        !=
Enterprise

## 8. Customer Need Boundary

Offering addresses Customer Need:

Customer Need
    -> is-addressed-by -> Offering

However:

Offering is-a Customer Need

must fail conformance.

## 9. Fulfillment Boundary

Offering is fulfilled through Fulfillment Process:

Fulfillment Process
    -> fulfills -> Offering

However:

Offering is-a Fulfillment Process

must fail conformance.

## 10. OTCHERE Inc Example

An OTCHERE Inc integrated business offering operates as follows:

Customer Need
      |
      v
Integrated Offering
      |
      v
Assess Customer Context
      |
      v
Determine Offering Objective
      |
      v
Evaluate Authority / Policy / Constraints
      |
      v
Select Product + Service + Capability Configuration
      |
      v
Coordinate Fulfillment
      |
      v
Observe Customer Outcome
      |
      v
Adapt / Escalate

The Offering is foundational: it is the coordinated bundle that addresses the Customer Need, composes Products + Services + Capabilities, and progresses through fulfillment to produce Customer Outcome.

## 11. Rejected Interpretations

The following are rejected:

- Offering = Product
- Offering = Service
- Offering = Capability
- Offering = Portfolio
- Offering = Value Stream
- Offering = Enterprise
- Offering = Customer Need
- Offering = Fulfillment Process
- Offering = Solution
- Offering = Sale

## 12. Deferred Concepts

This ADR does not establish:

- Agentic Offering (governed by ADR-ES-018)
- Autonomous Offering (governed by ADR-ES-019)
- Offering autonomy maturity
- Offering lifecycle stages
- Offering Portfolio
- Solution
- Customer (as a foundational concept; deferred)
- Fulfillment Process (as a foundational concept; deferred)

Each requires independent semantic governance.

## 13. Consequences

Positive

- Establishes Offering as a canonical foundational concept.
- Resolves the Foundational Dependency Gate documented in ADR-ES-018 + ADR-ES-019 + CR-ES-018 + CR-ES-019.
- Enables autonomous and agentic Offering specializations to land on solid foundational ground.
- Preserves Product + Service + Capability as distinct semantic boundaries.

Risk

The principal risk is premature creation of dependent concepts (Customer, Fulfillment Process, Portfolio) within this ADR. The deferral discipline in section 12 mitigates this risk.

## 14. Governance

Implementation is authorized through:

CR-ES-021 , Offering Canonical Grounding Implementation

No WSF or OpenDEA implementation change is authorized.

## 15. Release

Target:

Enterprise-Semantics v1.8.1

Author: Emmanuel A. Otchere (cardinal author rule, 2026-09-24)


## Promotion Note

Promoted via 2-touchpoint ritual per ES series ADR-ES-001 section 10-11.

Per user directive messages 1552941597417807973 ("Proceed") + 1552920574223843429 ("What is unresolved about ADR/CR #19") + 1552900782440058902 ("Proceed with 18") + 1552912455527571546 ("save, read, understand, implement"), this foundational tranche was filed + implemented + promoted to resolve the Foundational Dependency Gates documented in ADR-ES-018 section 16 + ADR-ES-019 section 2.

Upon landing:
- ADR-ES-018 (Agentic Offering, v1.7.0) specialization becomes solidly grounded.
- ADR-ES-019 (Autonomous Offering, v1.8.0) specialization becomes solidly grounded.
- AOFF-NEG-BLOCKED-001 conformance test flips from BLOCKED to PASS.
- mappings/wsf/autonomous-offering.yaml status: candidate -> established.
- mappings/opendea/autonomous-offering.yaml status: candidate -> established.
- v1.8.0 release pointer foundational_dependency_gate flips from documented to resolved.

Status: Proposed -> Accepted 2026-09-25.

Emmanuel A. Otchere (cardinal author rule, 2026-09-24).
