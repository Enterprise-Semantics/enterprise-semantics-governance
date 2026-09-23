The first CR should implement ADR-ES-001 only. It should establish the governance and semantic-authority scaffolding, without prematurely introducing the substantive Capability, Value Stream, or Agentic models.

CR-ES-001: Establish Enterprise-Semantics Authority and Publication Architecture

Status: Proposed
Change Type: Foundational Infrastructure
Priority: P0 Foundation
Related ADR: ADR-ES-001
Repository Scope: Enterprise-Semantics organization
Target Release: v0.0.1 / initial governed foundation

<!--
Authored by: Emmanuel A. Otchere (cardinal author rule, 2026-09-22)
-->


;;


1. Objective

Implement ADR-ES-001 Establish Enterprise-Semantics Authority and Publication Architecture.

This CR establishes the minimum executable architecture required for Enterprise-Semantics to operate as a governed semantic authority between the World Semantic Foundation (WSF) and OpenDEA.

The change establishes:

* semantic authority structure;
* repository responsibilities;
* identifier infrastructure;
* semantic lifecycle;
* governance artifact structure;
* provenance structure;
* relationship-vocabulary foundation;
* mapping foundation;
* semantic profiles;
* validation foundation;
* publication structure.

This CR does not promote substantive enterprise concepts to canonical status.


;;


2. Architectural Scope

The resulting architecture shall be:

                         WSF
                          |
                   foundational
                    semantics
                          |
                          v
                Enterprise-Semantics
                          |
          |--───────────────  |--───────────────┐
        |                 |                 |
     Authority         Governance        Specification
        |                 |                 |
          |--───────────────  |--───────────────┘
                          |
               |--──────────  |--──────────┐
             v            v            v
          Docs         Examples      Mappings
             |            |            |
               |--──────────  |--──────────┘
                          |
                       Visuals
                          |
                     Test Probe
                          |
                          v
                        OpenDEA
                          |
                          v
                    DEA Catalogs


;;


3. Repository Changes

3.1 enterprise-semantics

Establish the canonical structured semantic authority.

Required initial structure:

enterprise-semantics/
  |-- README.md
  |-- LICENSE
  |-- concepts/
  |-- relationships/
  |-- profiles/
  |-- registry/
  |-- provenance/
  |-- schemas/
  |-- versions/

The repository shall contain no duplicate semantic authority in Markdown.

Markdown documentation may describe semantic content but shall not supersede structured semantic source.


;;


4. Semantic Concept Structure

Establish a standard concept representation.

Initial conceptual schema:

id:
name:
definition:
description:
status:
semantic_type:
domain:
aliases: []
exclusions: []
relationships: []
grounding:
  wsf: []
  enterprise_semantics: []
  opendea: []
provenance:
  source: []
  finding: []
  adr: []
  cr: []
  implementation: []
version:

The exact field names shall be finalized against the normative specification.

The schema shall support future concepts without requiring structural redesign.


;;


5. Concept Lifecycle

Establish the following lifecycle:

PROPOSED
    ->
CANDIDATE
    ->
ESTABLISHED
    ->
CANONICAL

Additional terminal or exceptional states:

REJECTED
SUPERSEDED
DEPRECATED

Lifecycle state shall be explicit.

Repository presence shall not imply semantic maturity.


;;


6. Initial Semantic Registry

Create a registry capable of tracking:

* semantic identifier;
* preferred name;
* semantic type;
* domain;
* lifecycle state;
* version introduced;
* governing ADR;
* governing CR.

Example:

concepts:
  - id: ES:CONCEPT:<identifier>
    name: <name>
    status: PROPOSED
    adr: ADR-ES-XXX
    cr: CR-ES-XXX

No final identifier shall be invented outside the identifier specification.


;;


7. Identifier Specification

Update:

enterprise-semantics-spec

with the normative identifier specification.

The specification shall establish:

Identity requirements

Identifiers must be:

* unique;
* stable;
* machine-readable;
* repository-independent;
* display-label-independent.

Naming requirements

Identifier normalization shall be defined centrally.

Persistence

A display-name change shall not automatically create a new semantic identity.

Change

A semantic identity change shall require governed treatment.


;;


8. Relationship Vocabulary Foundation

Create:

relationships/
  |-- vocabulary.yaml
  |-- inverse.yaml
  |-- README.md

The vocabulary shall support:

relationship:
  id:
  predicate:
  inverse:
  subject:
  object:
  definition:
  status:
  provenance:

The implementation shall support relationship governance but shall not populate an uncontrolled list of predicates.

Only relationships established through an approved ADR/CR or explicitly authorized seed activity shall become governed relationships.


;;


9. Provenance Model

Establish:

provenance/
  |-- sources.yaml
  |-- findings.yaml
  |-- decisions.yaml
  |-- README.md

Provenance shall distinguish:

SOURCE
RESEARCH
FINDING
DECISION
IMPLEMENTATION
MAPPING

A semantic concept must be traceable to the decision and implementation that established it.


;;


10. Governance Repository

Update:

enterprise-semantics-governance

with the canonical governance structure:

enterprise-semantics-governance/
  |-- README.md
  |-- adr/
  |-- cr/
  |-- findings/
  |-- decisions/
  |-- templates/
  |-- policies/
  |-- docs/

The governance repository shall establish the lifecycle:

Finding
   ->
ADR
   ->
CR
   ->
PR
   ->
CI
   ->
Semantic Release


;;


11. ADR Template

Create the canonical ADR template.

Required sections:

Title
Status
Date
Decision Type
Scope
Context
Problem
Decision
Semantic Definition
Semantic Boundaries
Relationships
WSF Grounding
OpenDEA Implications
Consequences
Rejected Alternatives
Implementation
Acceptance Criteria

The template shall encourage semantic precision without forcing every ADR to contain fields irrelevant to its decision.


;;


12. CR Template

Create the canonical CR template.

Required sections:

Title
Status
Related ADR
Objective
Scope
Repository Changes
Semantic Changes
Schema Changes
Relationship Changes
Mapping Changes
Documentation
Examples
Validation
Conformance
Completion Criteria
Out of Scope

A CR must be implementable without requiring the implementer to infer the intended architectural decision.


;;


13. Finding Template

Create the canonical Finding template.

Required sections:

Title
Status
Research Question
Context
Evidence
Observed Semantics
Competing Interpretations
Candidate Definitions
Candidate Relationships
Architectural Implications
WSF Considerations
Open Questions
Recommendation for Further Governance

A Finding shall not establish normative semantic authority.


;;


14. Semantic Specification

Update:

enterprise-semantics-spec

to define the initial semantic authority model.

The specification shall cover:

1. concept structure;
2. relationship structure;
3. identifiers;
4. lifecycle states;
5. provenance;
6. semantic profiles;
7. mappings;
8. versioning;
9. validation requirements.

The specification shall remain technology-neutral except where serialization requirements require otherwise.


;;


15. Mapping Foundation

Establish:

enterprise-semantics-mappings/
  |-- wsf/
  |-- opendea/
  |-- dea-catalogs/
  |-- README.md

Each mapping shall identify:

source:
target:
mapping_type:
relationship:
confidence:
status:
provenance:
governing_adr:

Supported mapping types shall initially include:

* equivalent;
* specialization;
* generalization;
* extension;
* contextualization;
* realization;
* implementation;
* correspondence.

The list may be expanded through governance.


;;


16. WSF Mapping Boundary

Create the initial WSF mapping structure.

It shall explicitly document:

Enterprise-Semantics
        |
        | grounded-by / specializes
        v
World Semantic Foundation

No WSF concept shall be copied into the Enterprise-Semantics authority merely for convenience.

Where Enterprise-Semantics uses a WSF concept, the relationship shall be represented through mapping.


;;


17. OpenDEA Mapping Boundary

Create:

mappings/opendea/

with an initial README establishing:

Enterprise-Semantics concepts may be specialized or formalized by OpenDEA. An OpenDEA implementation does not redefine the semantic authority of the Enterprise-Semantics concept.

No OpenDEA metamodel changes are included in this CR.


;;


18. Semantic Profiles

Establish the profile structure:

profiles/
  |-- enterprise/
  |-- capability/
  |-- value/
  |-- agentic/
  |-- autonomous/
  |-- operations/
  |-- workflow/
  |-- value-realization/

Profiles shall provide semantic organization rather than independent authorities.

Initial profile files may contain metadata and scope definitions only.

Substantive concept promotion will occur through subsequent ADR/CR pairs.


;;


19. Documentation Repository

Update:

enterprise-semantics-docs

with the foundational architecture documentation.

Minimum documentation:

docs/
  |-- architecture/
|     |-- semantic-authority.md
|     |-- authority-boundaries.md
|     |-- lifecycle.md
  |-- concepts/
  |-- relationships/
  |-- mappings/
  |-- governance/

The documentation shall explain:

WSF
 ->
Enterprise-Semantics
 ->
OpenDEA
 ->
DEA Catalogs

and the distinction between semantic authority and downstream implementation.


;;


20. Examples Repository

Establish:

enterprise-semantics-examples

with an example structure:

examples/
  |-- foundational/
  |-- enterprise/
  |-- capability/
  |-- value/
  |-- agentic/
  |-- autonomous/
  |-- value-realization/

At this stage, examples shall demonstrate the modeling mechanism rather than establish canonical concepts.

Where an enterprise example is required, use OTCHERE Inc.


;;


21. Visual Repository

Establish:

enterprise-semantics-visuals

with:

visuals/
  |-- architecture/
  |-- concepts/
  |-- relationships/
  |-- mappings/
  |-- profiles/

The initial architecture diagram shall represent:

WSF
 |
 v
Enterprise-Semantics
 |
 v
OpenDEA
 |
 v
DEA Catalogs

Visual source shall be maintained in a reproducible diagram format.

Rendered images shall be treated as derived artifacts.


;;


22. Test Probe

Establish the initial conformance probe in:

enterprise-semantics-test-probe

The first validation layer shall check:

Structural

* valid YAML/JSON;
* schema conformity;
* identifier syntax;
* identifier uniqueness.

Referential

* valid concept references;
* valid relationship references;
* valid profile references;
* valid mapping references.

Governance

* valid lifecycle state;
* valid ADR reference;
* valid CR reference;
* provenance presence.

Architectural

* no unresolved authority references;
* no duplicate canonical identifiers;
* valid WSF/OpenDEA mapping structures.

The probe does not yet need to validate domain-specific semantic rules.


;;


23. Versioning

Establish the initial repository/program state as:

Enterprise-Semantics v0.0.1

This version represents the architectural skeleton and governance foundation, not a mature semantic release.

The version shall not imply that all planned semantic concepts are canonical.


;;


24. CI

Establish CI checks for:

Schema validation
      ->
Identifier validation
      ->
Reference validation
      ->
Relationship validation
      ->
Provenance validation
      ->
Governance-reference validation
      ->
Conformance probe

A pull request modifying semantic authority content shall fail CI when any mandatory validation fails.


;;


25. README Updates

Update organization and repository READMEs to clearly state:

Enterprise-Semantics

Enterprise-Semantics is the governed enterprise semantic authority between WSF and OpenDEA.

WSF

WSF provides foundational world semantics.

OpenDEA

OpenDEA specializes enterprise semantics into enterprise architecture.

DEA Catalogs

DEA Catalogs instantiate and organize architectural knowledge.

The README shall explicitly state that Enterprise-Semantics is not a replacement for WSF or OpenDEA.


;;


26. Initial Semantic Seed Boundary

This CR establishes the infrastructure required for the semantic seed but does not itself finalize the substantive seed.

The following concepts may therefore remain in:

PROPOSED

until their individual ADRs establish their semantics:

* Capability
* Value Stream
* Agentic
* Agentic Enterprise
* Agentic Operations
* Agentic Value Stream
* Agentic Workflow
* Autonomous Operations
* Autonomous Enterprise
* Autonomous Value Stream
* Value Realization concepts

The first substantive concept ADR shall follow this CR.


;;


27. Out of Scope

CR-ES-001 shall not:

* redefine WSF concepts;
* modify the WSF repository;
* modify the OpenDEA metamodel;
* create canonical Agentic concepts;
* create canonical Autonomous concepts;
* establish Capability semantics;
* establish Value Stream semantics;
* establish Value Realization semantics;
* establish HVS semantics;
* establish KCI/KEI/KBI semantics;
* introduce vendor-specific semantic dependencies;
* introduce TM Forum material into WSF grounding.

Those matters require their own research and governed changes.


;;


28. Acceptance Criteria

CR-ES-001 is complete when all of the following are true:

Authority

* enterprise-semantics contains the canonical structured semantic-source structure.

Specification

* identifier, concept, relationship, lifecycle and provenance structures are specified.

Governance

* ADR, CR and Finding templates exist;
* governance lifecycle is documented.

Mapping

* WSF mapping structure exists;
* OpenDEA mapping structure exists;
* DEA Catalog mapping structure exists.

Documentation

* authority boundaries are documented.

Examples

* example structure exists and validates.

Visuals

* architecture diagram source exists and renders.

Validation

* conformance probe executes;
* CI validates authority content;
* broken references are detected.

Publication

* initial version is reproducible;
* semantic authority can be consumed independently from documentation.

Governance

* CR implementation is traceable to ADR-ES-001;
* no out-of-scope semantic decision has been introduced.


;;


29. Deliverables

The implementation shall produce:

1. Enterprise-Semantics authority skeleton;
2. normative specification foundation;
3. governance templates;
4. identifier registry foundation;
5. relationship vocabulary foundation;
6. provenance foundation;
7. mapping foundation;
8. semantic profile foundation;
9. documentation foundation;
10. examples foundation;
11. visual foundation;
12. conformance-probe foundation;
13. CI validation;
14. initial reproducible semantic version.


;;


30. Completion Statement

Upon successful completion:

Enterprise-Semantics shall possess a governed, machine-readable, versionable semantic-authority architecture capable of receiving substantive enterprise semantic concepts through subsequent ADR/CR cycles.

The next governed change shall be:

ADR-ES-002 Capability Semantic Grounding

followed by:

CR-ES-002 Implement Capability Semantic Grounding.

This gives us the proper first implementation boundary: CR-ES-001 builds the semantic machinery; CR-ES-002 and onward populate it. It also prevents the first CR from accidentally becoming a giant catch-all semantic model.