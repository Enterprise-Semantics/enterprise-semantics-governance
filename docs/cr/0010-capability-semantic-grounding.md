CR-ES-002: Capability Semantic Grounding

Status: Proposed
Change Type: Semantic Grounding
Priority: P0 Foundational Enterprise Concept
Related ADR: ADR-ES-002 Capability Semantic Grounding
Depends On: CR-ES-001 Enterprise-Semantics Authority and Publication Architecture
Target Release: Enterprise-Semantics v0.1.0


;;


1. Objective

Establish Capability as a formally grounded enterprise semantic concept within Enterprise-Semantics.

This change shall define:

* the canonical meaning of Capability;
* its semantic boundaries;
* its distinction from adjacent enterprise concepts;
* its core relationships;
* its grounding in WSF;
* its correspondence to OpenDEA;
* its reusable representation within the Enterprise-Semantics semantic source of truth;
* its initial validation and conformance requirements.

This CR establishes the semantic foundation for subsequent specializations and applications of Capability, including business, operational, technical, agentic, and autonomous capability contexts.

This CR does not establish Agentic Capability, Autonomous Capability, Business Capability, Technical Capability, or other specialized capability concepts as foundational concepts.


;;


2. Semantic Decision

2.1 Canonical Definition

Capability

An enduring ability of an Entity to achieve or enable an Outcome.

Capability describes what an Entity is able to achieve or enable, rather than the activity through which the achievement occurs.

Capability therefore represents an enduring potential or competence of an Entity that may be exercised through processes, roles, services, systems, resources, or other realization mechanisms.


;;


2.2 Semantic Characteristics

A Capability:

1. is associated with an Entity;
2. represents an ability rather than an activity;
3. is oriented toward an achievable or enabled Outcome;
4. may exist independently of any single Process;
5. may be exercised repeatedly across multiple Processes or scenarios;
6. may be supported or implemented by multiple architectural elements;
7. may contribute to Value realization;
8. may be assessed independently of the specific process used to exercise it;
9. may exist at different levels of abstraction;
10. may be specialized by context without changing the foundational meaning of Capability.


;;


3. Semantic Boundary

Capability shall be distinguished from adjacent concepts.

Concept	Semantic concern	Distinction from Capability
Entity	Who or what exists or acts	Capability is an ability possessed by an Entity
Role	Contextual responsibility or position	Role identifies responsibility; Capability identifies ability
Process	Organized transformation or execution	Process describes how work is performed; Capability describes what can be achieved
Function	Purpose or area of activity	Function describes an area of responsibility/activity; Capability describes ability
Outcome	Result achieved or enabled	Capability enables or contributes to an Outcome; it is not the Outcome
Resource	Something available for use	Resource supports a Capability; it is not the ability itself
Service	Offered means of providing value or capability	Service exposes or delivers capabilities through an interaction/offer
System	Organized technical or socio-technical construct	System may implement or support a Capability
Value	Worth or benefit realized by a stakeholder	Capability contributes to Value but is not itself Value
Goal	Intended state or result	Capability may enable achievement of a Goal
Skill	Learned proficiency of an actor	Skill may contribute to a Capability but does not necessarily represent the enterprise-level ability
Process Activity	Unit of process execution	Activity exercises a Capability but does not define the Capability

The principal semantic distinction is:

Capability answers “what can be achieved?” while Process answers “how is it performed?”


;;


4. Core Relationships

The following relationships shall be established as canonical Capability relationships.

Subject	Predicate	Object	Meaning
Entity	possesses	Capability	An Entity has the ability represented by a Capability
Capability	enables	Outcome	A Capability makes an Outcome achievable or possible
Capability	realized-through	Process	A Capability is exercised or manifested through a Process
Capability	exercised-by	Role	A Role exercises a Capability within a defined context
Capability	supported-by	Resource	A Resource provides support required for Capability exercise
Capability	delivered-through	Service	A Service exposes or delivers a Capability to a consumer
Capability	implemented-by	System	A System provides an implementation of a Capability
Capability	contributes-to	Value	A Capability contributes to the realization of Value
Capability	supports	Goal	A Capability supports achievement of a Goal

These relationships shall be represented as explicit semantic relationships rather than implicit documentation statements.


;;


5. Relationship Semantics

5.1 Entity: possesses → Capability

Definition:

An Entity possesses a Capability when the Entity has the enduring ability represented by that Capability.

This is the primary anchoring relationship for Capability.

Example:

OTCHERE Inc possesses Customer Relationship Management Capability.


;;


5.2 Capability: enables → Outcome

Definition:

A Capability enables an Outcome when possession or exercise of the Capability makes the Outcome achievable.

The relationship does not assert that the Capability alone produces the Outcome.


;;


5.3 Capability: realized-through → Process

Definition:

A Capability is realized-through a Process when execution of the Process exercises or manifests the Capability.

This relationship establishes the critical Capability:Process boundary.

A Capability therefore must not be defined as a collection of Processes.


;;


5.4 Capability: exercised-by → Role

Definition:

A Role exercises a Capability when the Role is responsible for applying or performing the ability represented by the Capability within a defined context.


;;


5.5 Capability: supported-by → Resource

Definition:

A Resource supports a Capability when the Resource provides something required for the Capability to be exercised or sustained.


;;


5.6 Capability: delivered-through → Service

Definition:

A Capability is delivered-through a Service when the Service provides access to, or realizes the utility of, that Capability for a consumer.

The relationship shall not imply that Capability and Service are synonymous.


;;


5.7 Capability: implemented-by → System

Definition:

A System implements a Capability when the System provides the mechanisms required for the Capability to exist or operate within a defined context.

This relationship is intentionally broader than software implementation.


;;


5.8 Capability: contributes-to → Value

Definition:

A Capability contributes-to Value when the Capability provides a causal or enabling contribution to value realization.

contributes-to does not imply direct, exclusive, or quantifiable causation.


;;


6. Capability Identity

Capability identity shall be independent of:

* organizational ownership;
* process implementation;
* technology implementation;
* service implementation;
* role assignment;
* organizational hierarchy;
* individual performers;
* specific operating scenarios.

A Capability identifier shall remain stable when its implementation changes.

For example:

ES:CAPABILITY:CUSTOMER-RELATIONSHIP-MANAGEMENT

shall not change merely because OTCHERE Inc changes the processes, systems, organizational units, or services through which the capability is realized.


;;


7. Capability Representation

The canonical semantic representation shall extend the common Enterprise-Semantics concept schema established by CR-ES-001.

Illustrative representation:

id: ES:CAPABILITY:CUSTOMER-RELATIONSHIP-MANAGEMENT
name: Customer Relationship Management
definition: >
  An enduring ability of an Entity to establish, maintain,
  develop, and manage relationships with customers to enable
  intended outcomes.
semantic_type: Capability
status: PROPOSED
domain:
  - Enterprise
relationships:
  - predicate: possesses
    object_type: Entity
  - predicate: enables
    object_type: Outcome
  - predicate: realized-through
    object_type: Process
  - predicate: exercised-by
    object_type: Role
  - predicate: supported-by
    object_type: Resource
  - predicate: delivered-through
    object_type: Service
  - predicate: implemented-by
    object_type: System
  - predicate: contributes-to
    object_type: Value
grounding:
  wsf:
    status: mapped
  enterprise_semantics:
    status: canonical
  opendea:
    status: mapped
provenance:
  adr:
    - ADR-ES-002
  cr:
    - CR-ES-002
version: 0.1.0

The example is illustrative and shall not itself establish Customer Relationship Management as a canonical catalog capability.


;;


8. Capability and Process Boundary

This CR establishes an explicit semantic boundary between Capability and Process.

Capability

Represents:

the ability to achieve or enable something.

Process

Represents:

the organized execution or transformation through which something is performed or achieved.

Therefore:

Entity
  |
    |-- possesses ──> Capability
  |                    |
  |                      |-- enables ──> Outcome
  |
    |-- participates/exercises through ──> Process
                                      |
                                        |-- realizes Capability

A Process may change while the Capability remains stable.

Conversely, a Capability may evolve while existing Processes continue to operate temporarily against an earlier capability state.

This distinction is foundational for enterprise architecture because it permits capability-based analysis independent of current implementation.


;;


9. Capability and Function Boundary

Capability shall not be treated as a synonym for Function.

Function identifies an area or purpose of activity.

Capability identifies an enduring ability.

For example:

Function:
Customer Management
Capabilities:
- Customer Relationship Management
- Customer Insight
- Customer Engagement
- Customer Retention

A Function may therefore encompass multiple Capabilities, while a Capability may be exercised across multiple Functions or organizational contexts.

The exact Function semantic shall be governed independently.


;;


10. Capability and Service Boundary

A Service shall not be treated as a Capability.

A Service provides an interaction or means through which value or capability is made available to a consumer.

The semantic pattern is therefore:

Capability
     |
       |-- delivered-through ──> Service
                                  |
                                    |-- consumed by ──> Entity

A Service may expose one or more capabilities, and a Capability may be delivered through multiple Services.


;;


11. Capability and System Boundary

System shall not be treated as a subtype of Capability.

A System may implement, support, enable, or participate in the realization of a Capability.

The architecture must therefore preserve:

Capability ≠ System

and:

Capability ──implemented-by──> System

This prevents technical implementation from becoming embedded within the semantic definition of the enterprise ability.


;;


12. Capability and Outcome Boundary

Capability and Outcome represent different semantic layers.

Capability ──enables──> Outcome

Capability represents potential or ability.

Outcome represents an achieved or enabled result.

For example:

Customer Service Capability
        |
          |-- enables ──>
              Customer Issue Resolved Outcome

The outcome is therefore evidence of a realized result, not the definition of the capability itself.


;;


13. Capability Specialization

Capability shall support contextual specialization.

Potential specializations include:

Capability
  |-- Business Capability
  |-- Operational Capability
  |-- Technical Capability
  |-- Organizational Capability
  |-- Agentic Capability
  |-- Autonomous Capability

These are not established as canonical concepts by this CR.

This CR establishes only the foundational semantic structure necessary for subsequent specialization.

Future specialization ADRs must demonstrate:

1. the distinguishing semantic property;
2. why the specialization cannot be represented through contextual classification;
3. its relationship to foundational Capability;
4. its boundary with adjacent concepts;
5. its WSF grounding;
6. its OpenDEA implications.


;;


14. Capability Assessment Boundary

Capability shall be assessable independently from its implementation.

Assessment may consider dimensions such as:

* existence;
* breadth;
* depth;
* consistency;
* effectiveness;
* maturity;
* performance;
* adaptability;
* resilience.

However, assessment models and maturity constructs remain outside this CR.

Enterprise-Semantics shall provide the semantic identity and meaning of Capability.

Assessment-Models shall remain authoritative for maturity-model and assessment constructs.

This preserves the boundary between:

Semantic Definition
        ->
Capability
        ->
Assessment Application


;;


15. WSF Grounding

Capability shall be grounded against the World Semantic Foundation.

The Enterprise-Semantics implementation shall:

* reference the relevant WSF concept;
* record the grounding relationship;
* identify whether the Enterprise-Semantics concept is an extension, specialization, contextualization, or other mapped construct;
* avoid copying WSF definitions into Enterprise-Semantics as an independent competing authority;
* preserve WSF provenance.

Where WSF does not yet provide sufficient foundational semantics, the gap shall be recorded rather than silently resolved by duplication.

No WSF repository modification is authorized by this CR.


;;


16. OpenDEA Implications

OpenDEA may represent Capability as an enterprise architecture construct and may provide specialized architectural views of Capability.

CR-ES-002 does not modify the OpenDEA metamodel.

The mapping shall establish correspondence between:

Enterprise-Semantics Capability
            |
              |-- maps-to ──> OpenDEA Capability Construct

The mapping shall distinguish:

* semantic identity;
* architectural representation;
* catalog instantiation;
* implementation realization.

This prevents OpenDEA implementation constraints from becoming part of the foundational semantic definition.


;;


17. DEA Catalog Implications

DEA Catalogs may instantiate or classify Capability after the semantic foundation is established.

The expected separation is:

Enterprise-Semantics
        |
          |-- defines ──> Capability
                         |
                         ->
                    OpenDEA
                         |
                         ->
                  DEA Capability
                      Catalog
                         |
                         ->
                    Capability
                    Instances

A catalog entry shall not redefine the foundational meaning of Capability.

Catalog-specific classification, sectorization, architecture coordinates, or organizational applicability shall remain downstream concerns.


;;


18. Semantic Validation Rules

The conformance probe shall validate at minimum:

CAP-001: Identity

Every Capability must have a unique identifier.

CAP-002: Definition

Every canonical Capability must have a definition.

CAP-003: Entity Association

A Capability must be capable of being associated with an Entity through possesses.

CAP-004: Outcome Association

A Capability must support an enables relationship to Outcome where an Outcome is asserted.

CAP-005: Process Boundary

Capability definitions must not contain Process definitions as their semantic identity.

CAP-006: System Boundary

Capability definitions must not identify a System as the Capability itself.

CAP-007: Service Boundary

Capability definitions must not equate Capability with Service.

CAP-008: Relationship Integrity

All referenced relationship predicates must exist in the Enterprise-Semantics relationship vocabulary.

CAP-009: Provenance

Every canonical Capability must identify its governing ADR and CR.

CAP-010: Lifecycle

Capability lifecycle status must conform to the Enterprise-Semantics lifecycle model.

CAP-011: Grounding

A canonical Capability must identify its WSF grounding status.

CAP-012: Specialization

A Capability specialization must explicitly reference its parent Capability semantic.


;;


19. Documentation Changes

Update enterprise-semantics-docs with:

concepts/
  |-- capability.md
architecture/
  |-- capability-boundary.md
relationships/
  |-- capability-relationships.md

Documentation shall include:

* canonical definition;
* semantic characteristics;
* boundary analysis;
* relationship semantics;
* examples;
* WSF grounding;
* OpenDEA correspondence;
* lifecycle;
* specialization rules.


;;


20. Example Model

The initial worked example shall use OTCHERE Inc.

Illustrative model:

OTCHERE Inc
     |
       |-- possesses ──>
          Customer Relationship Management Capability
                    |
                      |-- enables ──> Customer Retention Outcome
                    |
                      |-- realized-through ──>
                    |       Customer Relationship Process
                    |
                      |-- exercised-by ──>
                    |       Customer Relationship Manager Role
                    |
                      |-- supported-by ──>
                    |       Customer Information Resource
                    |
                      |-- delivered-through ──>
                    |       Customer Engagement Service
                    |
                      |-- implemented-by ──>
                    |       Customer Management System
                    |
                      |-- contributes-to ──>
                            Customer Value

The example demonstrates the semantic separation without establishing the example capability as a canonical catalog entry.


;;


21. Relationship Vocabulary Changes

Add or confirm the following predicates in the Enterprise-Semantics relationship vocabulary:

possesses
enables
realized-through
exercised-by
supported-by
delivered-through
implemented-by
contributes-to
supports

Each predicate must include:

* identifier;
* canonical predicate;
* inverse where applicable;
* subject type;
* object type;
* definition;
* lifecycle status;
* provenance.

No relationship shall be inferred merely from natural-language documentation.


;;


22. Mapping Changes

Create Capability mapping structures in:

enterprise-semantics-mappings/
  |-- wsf/
|     |-- capability.yaml
  |-- opendea/
|     |-- capability.yaml
  |-- dea-catalogs/
      |-- capability.yaml

Mapping types shall explicitly distinguish:

* equivalent;
* specialization;
* generalization;
* contextualization;
* extension;
* implementation;
* realization;
* correspondence.

Where the semantic relationship cannot yet be established with sufficient confidence, the mapping shall remain PROPOSED rather than being promoted to canonical.


;;


23. Conformance Tests

Add Capability-specific tests to the semantic test probe.

Minimum test groups:

tests/
  |-- capability/
|     |-- identity
|     |-- schema
|     |-- relationships
|     |-- boundaries
|     |-- provenance
|     |-- grounding
|     |-- specialization

The tests shall verify both positive and negative cases.

For example:

VALID:
Capability → realized-through → Process
INVALID:
Process → is-a → Capability

unless an explicit future semantic decision establishes such a relationship.


;;


24. Versioning

This change establishes the Capability semantic foundation for:

Enterprise-Semantics v0.1.0

The version shall indicate semantic establishment rather than maturity of the wider Enterprise-Semantics program.

Future breaking semantic changes shall require a new ADR and corresponding CR.


;;


25. Out of Scope

The following are explicitly excluded:

* modification of WSF;
* modification of OpenDEA metamodel;
* creation of a complete Business Capability Catalog;
* creation of sector-specific capabilities;
* Agentic Capability;
* Autonomous Capability;
* Capability maturity models;
* capability scoring;
* capability heatmaps;
* capability prioritization;
* capability investment methodology;
* capability decomposition methodology;
* Process metamodel changes;
* Service metamodel changes;
* System metamodel changes;
* Function semantic grounding;
* Role semantic grounding;
* Resource semantic grounding.

These may become subjects of subsequent governed changes.


;;


26. Acceptance Criteria

CR-ES-002 is complete when:

* [ ]	Capability has a canonical Enterprise-Semantics definition.
* [ ]	Capability semantic boundaries are documented.
* [ ]	Capability is explicitly distinguished from Process, Function, Role, Resource, Service, System, Outcome, and Value.
* [ ]	Core Capability relationships are formally represented.
* [ ]	Relationship vocabulary is validated.
* [ ]	Capability schema representation is implemented.
* [ ]	Capability identity rules are implemented.
* [ ]	Capability lifecycle is implemented.
* [ ]	Capability provenance is implemented.
* [ ]	WSF grounding is recorded.
* [ ]	OpenDEA correspondence is recorded without modifying OpenDEA.
* [ ]	DEA Catalog correspondence boundary is established.
* [ ]	Capability documentation is published.
* [ ]	Capability example model is published using OTCHERE Inc.
* [ ]	Capability conformance tests pass.
* [ ]	No unapproved specialization is promoted to canonical status.
* [ ]	All implementation artifacts trace to ADR-ES-002.
* [ ]	CI validates the resulting semantic structure.


;;


27. Completion Condition

CR-ES-002 shall be considered complete when Enterprise-Semantics can answer, in machine-readable and human-readable form:

What is a Capability?

What is it not?

What can it relate to?

How is it grounded in WSF?

How does it correspond to OpenDEA?

How may it subsequently be specialized?

How can its semantic integrity be validated?

At completion, Capability becomes an established enterprise semantic foundation upon which subsequent architectural and domain-specific concepts may safely build.


;;


28. Next Governed Change

The next semantic grounding sequence should proceed to:

ADR-ES-003: Value Stream Semantic Grounding

followed by:

CR-ES-003: Value Stream Semantic Grounding

This establishes the foundational Value Stream semantics before introducing:

* Agentic Value Stream;
* Autonomous Value Stream;
* Agentic Workflow;
* Agentic Operations;
* Value Realization relationships.

This sequencing preserves the semantic principle:

Foundational Concept
        ->
Enterprise Semantic Grounding
        ->
Architectural Correspondence
        ->
Specialization
        ->
Agentic / Autonomous Extension
        ->
Operational Application

<!--
Authored by: Emmanuel A. Otchere (cardinal author rule, 2026-09-22)
-->
