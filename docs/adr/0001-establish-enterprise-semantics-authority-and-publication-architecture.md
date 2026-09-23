ADR-ES-001 — Establish Enterprise-Semantics Authority and Publication Architecture

Status: Proposed
Date: 2026-09-22
Decision Type: Foundational Architecture
Scope: Enterprise-Semantics Organization
Supersedes: None
Related: FND-ES-000, FND-ES-001
Implementation: CR-ES-001

⸻

1. Context

Enterprise-Semantics establishes the enterprise-level semantic layer between the World Semantic Foundation (WSF) and OpenDEA.

The intended semantic architecture is:

World Semantic Foundation
          │
          │ foundational semantics
          ▼
Enterprise-Semantics
          │
          │ enterprise semantic grounding
          ▼
OpenDEA
          │
          │ architectural specialization
          ▼
DEA Catalogs

Enterprise-Semantics is therefore neither a replacement for WSF nor an alternative OpenDEA metamodel.

Its purpose is to establish, govern, publish, and maintain enterprise-level semantic definitions, relationships, classifications, profiles, and mappings that can subsequently be specialized by OpenDEA.

The organization has been established as a multi-repository architecture. A durable authority model and publication mechanism are therefore required before substantive semantic content is promoted.

The Enterprise-Semantics governance repository defines the governed lifecycle as:

Finding
   ↓
ADR
   ↓
CR
   ↓
PR
   ↓
CI
   ↓
Published Semantic Version

This ADR establishes the architectural authority and publication model required for that lifecycle. (GitHub)

⸻

2. Problem

Without an explicit semantic authority architecture, Enterprise-Semantics risks becoming:

* a collection of terminology;
* a documentation repository;
* an ungoverned ontology;
* a duplicate of WSF;
* an alternative OpenDEA metamodel;
* or a collection of disconnected conceptual research.

The program therefore requires a clearly defined authority boundary, source of truth, repository responsibility, identifier scheme, semantic lifecycle, governance mechanism, publication mechanism, and downstream mapping model.

⸻

3. Decision

Enterprise-Semantics shall operate as a governed enterprise semantic authority with a structured semantic source of truth, normative specifications, formal governance, human-readable documentation, worked examples, mappings, reproducible visualizations, and conformance validation.

The semantic authority shall be implemented through the Enterprise-Semantics repository architecture defined by the program plan.

The canonical architecture is:

                         WSF
                          │
                 foundational grounding
                          │
                          ▼
                 ENTERPRISE-SEMANTICS
                          │
          ┌───────────────┼───────────────┐
          │               │               │
       Research        Concepts        Mappings
          │               │               │
          └───────────────┼───────────────┘
                          │
                     formalization
                          │
                          ▼
                       OpenDEA
                          │
                       instances
                          │
                          ▼
                    DEA Catalogs

Enterprise-Semantics shall maintain semantic authority independently from downstream architectural implementation.

⸻

4. Authority Boundary

4.1 WSF

WSF remains authoritative for foundational world semantics.

Enterprise-Semantics shall not redefine or duplicate foundational WSF concepts where an applicable WSF semantic already exists.

Where an enterprise concept specializes or contextualizes a WSF concept, Enterprise-Semantics shall explicitly identify that grounding.

⸻

4.2 Enterprise-Semantics

Enterprise-Semantics is authoritative for:

* enterprise semantic concepts;
* enterprise semantic definitions;
* enterprise relationship semantics;
* enterprise semantic classifications;
* semantic profiles;
* enterprise semantic identifiers;
* enterprise semantic provenance;
* enterprise-level semantic constraints;
* WSF mappings;
* OpenDEA mappings;
* semantic lifecycle status.

Enterprise-Semantics is not authoritative for the OpenDEA metamodel itself.

⸻

4.3 OpenDEA

OpenDEA remains authoritative for enterprise architecture metamodel constructs.

OpenDEA may specialize or formalize Enterprise-Semantics concepts within the architecture metamodel.

Promotion of an Enterprise-Semantics concept into OpenDEA shall therefore require the appropriate OpenDEA governance process.

⸻

4.4 DEA Catalogs

DEA Catalogs instantiate, classify, organize, and apply architectural concepts within defined catalog domains.

A catalog entry shall not redefine the semantic authority of the underlying Enterprise-Semantics concept.

⸻

5. Repository Architecture

Enterprise-Semantics shall use a multi-repository architecture.

Repository	Authority
enterprise-semantics	Structured semantic source of truth
enterprise-semantics-spec	Normative semantic specifications
enterprise-semantics-governance	ADRs, CRs, Findings, lifecycle and program governance
enterprise-semantics-docs	Human-readable semantic documentation
enterprise-semantics-examples	Worked enterprise semantic models
enterprise-semantics-mappings	WSF, OpenDEA and DEA Catalog mappings
enterprise-semantics-visuals	Reproducible semantic and architectural diagrams
enterprise-semantics-test-probe	Semantic conformance and integrity validation
.github	Organization-level governance and community assets

This corresponds to the repository architecture established in the current program plan. (GitHub)

⸻

6. Semantic Source of Truth

The enterprise-semantics repository shall be the canonical structured source for semantic content.

The authoritative semantic representation shall be machine-readable.

Initial serialization shall use YAML and/or JSON as defined by the normative specification.

Human-readable Markdown documentation, diagrams, and other published representations shall not become competing semantic authorities.

The authority relationship is:

Structured Semantic Source
          │
          ├── generates / informs → Documentation
          ├── generates / informs → Visuals
          ├── validates → Examples
          ├── supports → Mappings
          └── validates through → Conformance Probe

Where generated artifacts conflict with the structured semantic source, the structured semantic source takes precedence.

⸻

7. Identifier Architecture

Enterprise-Semantics shall use a globally distinguishable identifier scheme.

The initial identifier pattern shall be:

ES:<KIND>:<NAME>

The exact permitted values of KIND, normalization rules, uniqueness constraints, and serialization requirements shall be governed by the Enterprise-Semantics specification.

Identifiers shall be:

* stable;
* unique;
* machine-readable;
* independent of repository location;
* independent of display labels;
* persistent across documentation changes;
* traceable to provenance.

Changing a display name shall not automatically create a new semantic identity.

A semantic identity change requires governed treatment.

⸻

8. Semantic Lifecycle

Enterprise-Semantics shall distinguish semantic maturity from implementation state.

The initial semantic lifecycle is:

Proposed
   ↓
Candidate
   ↓
Established
   ↓
Canonical

A concept may also be:

Rejected
Superseded
Deprecated

where applicable.

Lifecycle transitions shall be governed rather than inferred from repository presence.

A concept appearing in the repository does not, by itself, make that concept canonical.

⸻

9. Governance Lifecycle

Enterprise semantic change shall follow:

Existing Knowledge
       ↓
Finding
       ↓
ADR
       ↓
CR
       ↓
Implementation
       ↓
CI
       ↓
Published Semantic Version
       ↓
Reference / Mapping
       ↓
Downstream Use
       ↓
New Finding

This creates a continuous semantic development loop.

A Finding captures investigation or a candidate hypothesis.

An ADR establishes a governed semantic decision.

A CR defines the implementable change required by that decision.

A PR implements the CR.

CI establishes conformance.

A release establishes the published semantic state.

This lifecycle is consistent with the current governance repository definition. (GitHub)

⸻

10. Finding Authority

Findings shall preserve the distinction between:

what has been researched

and:

what has been decided.

Research findings may contain:

* alternative interpretations;
* competing definitions;
* unresolved questions;
* semantic hypotheses;
* external references;
* candidate relationships;
* architectural implications.

A Finding shall not itself establish canonical semantic authority.

This prevents research from silently becoming normative architecture.

⸻

11. ADR Authority

An ADR establishes a semantic or architectural decision.

Once merged, an ADR is immutable.

A later change shall not rewrite the historical decision.

Where a decision changes, a new ADR shall:

1. identify the previous ADR;
2. explain the changed understanding;
3. establish the new decision;
4. identify affected concepts and implementations;
5. define migration or compatibility requirements where necessary.

This preserves semantic decision history.

⸻

12. Change Request Authority

A CR translates an approved ADR into an implementable change.

A CR shall identify:

* target repository;
* files or structures affected;
* semantic changes;
* identifiers;
* relationships;
* schemas;
* mappings;
* documentation;
* examples;
* validation;
* conformance requirements;
* completion criteria.

A CR shall not introduce an architectural decision that has not been established by its governing ADR unless the CR is explicitly authorized as an independent scope change.

⸻

13. Relationship Semantics

Relationships are first-class semantic content.

Enterprise-Semantics shall maintain a governed relationship vocabulary.

A relationship shall have:

* canonical predicate;
* subject semantics;
* object semantics;
* direction;
* inverse where applicable;
* cardinality where applicable;
* provenance;
* lifecycle state.

Examples include:

Entity → possesses → Capability
Capability → enables → Outcome
Enterprise → operates-through → Value Stream
Value Stream → realizes → Value

Relationship wording shall be semantically deliberate.

Generic association semantics shall not be used where a more precise relationship is available.

⸻

14. Provenance

Every canonical semantic concept shall maintain provenance sufficient to establish:

* origin;
* research basis;
* governing decision;
* implementation history;
* external grounding where applicable;
* downstream mappings.

Provenance shall distinguish:

Source
Research
Decision
Implementation
Mapping

This ensures that an externally sourced concept, an internally derived concept, and a downstream architectural specialization are not represented as equivalent origins.

⸻

15. Mapping Architecture

Enterprise-Semantics shall maintain explicit mappings between:

Enterprise-Semantics ↔ WSF
Enterprise-Semantics ↔ OpenDEA
Enterprise-Semantics ↔ DEA Catalogs

Mappings shall distinguish semantic relationships such as:

* equivalent;
* specialization;
* generalization;
* extension;
* composition;
* contextualization;
* implementation;
* realization;
* correspondence.

A mapping shall not imply semantic equivalence merely because two constructs share a similar name.

⸻

16. Semantic Profiles

Enterprise-Semantics may define semantic profiles that group related concepts for a particular enterprise domain or semantic theme.

A profile shall not create an implicit new ontology.

Profiles are organizational and semantic views over governed concepts.

Examples of future profiles include:

* Agentic Enterprise;
* Agentic Operations;
* Agentic Value Stream;
* Autonomous Enterprise;
* Autonomous Operations;
* Autonomous Network;
* Value Realization.

The existence of a profile does not automatically establish each contained concept as canonical.

⸻

17. Conformance

Enterprise-Semantics shall maintain automated validation covering, at minimum:

* identifier uniqueness;
* identifier syntax;
* schema validity;
* relationship validity;
* broken references;
* lifecycle validity;
* provenance completeness;
* mapping integrity;
* profile integrity.

Conformance shall occur before semantic publication.

The enterprise-semantics-test-probe repository shall provide the corresponding validation mechanism.

⸻

18. Publication Architecture

Semantic publication shall be versioned.

A published semantic version represents a validated state of the Enterprise-Semantics authority.

Publication shall occur only after:

Governed Decision
        ↓
Implementation
        ↓
Validation
        ↓
Conformance
        ↓
Approval
        ↓
Semantic Release

The published version shall provide a reproducible reference point for downstream consumers.

OpenDEA and DEA Catalogs shall be able to identify the Enterprise-Semantics semantic version against which a mapping or specialization was developed.

⸻

19. Compatibility

Semantic changes shall distinguish:

Additive

New concepts or relationships that do not invalidate existing semantic interpretation.

Clarifying

Changes that improve explanatory precision without changing semantic identity.

Restrictive

Changes that constrain previously permitted interpretation.

Breaking

Changes that alter semantic identity, relationship meaning, required structure, or interpretation sufficiently to invalidate downstream consumers.

Breaking semantic changes shall require explicit governance and versioning.

⸻

20. Separation of Semantic and Implementation Authority

Enterprise-Semantics shall distinguish:

Semantic Authority
        ≠
Architecture Implementation
        ≠
Catalog Instance
        ≠
Documentation

The same concept may therefore appear across multiple repositories while retaining one semantic authority.

For example:

Enterprise-Semantics
        │
        │ defines
        ▼
Capability
        │
        ├── documented by → ES Docs
        ├── illustrated by → ES Visuals
        ├── demonstrated by → ES Examples
        ├── mapped by → ES Mappings
        ├── validated by → ES Test Probe
        └── specialized by → OpenDEA

⸻

21. Scope of Enterprise-Semantics

Enterprise-Semantics shall cover enterprise-level semantics including, but not limited to:

* Enterprise;
* Intent and Governance;
* Capacity and Capability;
* Value;
* Work and Execution;
* Intelligence;
* Agentic;
* Autonomous;
* Operations;
* Closed Loop;
* Scenario;
* Information;
* State and Occurrence;
* Measurement and Value Realization.

These are semantic domains rather than an assertion that every term within them is already canonical.

The current program plan identifies these as the semantic seed families. (GitHub)

⸻

22. Explicit Non-Goals

This ADR does not establish:

* a replacement for WSF;
* an OpenDEA metamodel;
* a DEA Catalog;
* an enterprise architecture framework;
* an AI framework;
* an ontology language implementation;
* a technology architecture;
* a specific vendor model;
* canonical status for every seed concept.

Enterprise-Semantics is concerned with semantic authority, not with owning every downstream implementation.

⸻

23. Architectural Principles

The following principles are established:

23.1 Foundation before specialization

Enterprise concepts shall be grounded in foundational semantics where applicable.

23.2 Semantics before implementation

A concept shall be semantically understood before being structurally implemented.

23.3 Evidence before decision

Research shall precede normative semantic decisions where ambiguity exists.

23.4 Decision before change

Implementation shall follow an approved ADR unless explicitly authorized as an independent change.

23.5 One semantic authority

The same semantic concept shall not acquire competing authoritative definitions across repositories.

23.6 Explicit mapping

Cross-model correspondence shall be represented explicitly rather than inferred from naming similarity.

23.7 Machine-readable authority

Canonical semantics shall be represented in machine-readable form.

23.8 Reproducible publication

Published semantic versions shall be reproducible and testable.

23.9 Historical integrity

Merged ADRs shall remain immutable.

23.10 Downstream independence

OpenDEA and DEA Catalogs may specialize Enterprise-Semantics without becoming the authority for Enterprise-Semantics itself.

⸻

24. Consequences

Positive

This decision:

* establishes a durable semantic authority;
* separates WSF, Enterprise-Semantics and OpenDEA responsibilities;
* prevents terminology from becoming uncontrolled architecture;
* provides a governed path from research to canonical semantics;
* enables machine-readable enterprise semantics;
* supports explicit semantic mappings;
* enables downstream OpenDEA specialization;
* provides reproducible semantic releases;
* creates a foundation for agentic, autonomous, value, capability and operational semantic work.

Negative

The architecture introduces governance overhead.

Semantic changes require:

* findings where research is required;
* ADRs for decisions;
* CRs for implementation;
* conformance;
* publication discipline.

This is intentional.

The cost is accepted to prevent semantic drift and competing authorities.

⸻

25. Decision

Enterprise-Semantics is established as the governed enterprise semantic authority between WSF and OpenDEA.

Its canonical semantic source shall be the structured content of the enterprise-semantics repository.

Its semantic specifications shall be governed through enterprise-semantics-spec.

Its decisions and changes shall be governed through enterprise-semantics-governance.

Its published semantics shall be validated through the Enterprise-Semantics conformance mechanism and released as versioned semantic states.

Its relationship to WSF, OpenDEA and DEA Catalogs shall be explicit and mapping-based.

The semantic development lifecycle shall be:

Finding
   ↓
ADR
   ↓
CR
   ↓
Implementation
   ↓
CI
   ↓
Semantic Release
   ↓
Reference / Mapping

⸻

26. Implementation

Implementation of this decision is governed by:

CR-ES-001 — Establish Enterprise-Semantics Authority and Publication Architecture

CR-ES-001 shall establish the repository structures, governance records, identifier registry, semantic seed structure, mapping foundations, validation foundations, and publication mechanisms required by this ADR.

⸻

27. Future Decisions Enabled

This ADR establishes the authority required for subsequent semantic grounding decisions, including:

* ADR-ES-002 — Capability Semantic Grounding
* ADR-ES-003 — Value Stream Semantic Grounding
* ADR-ES-004 — Agentic Semantic Grounding
* ADR-ES-005 — Agentic Value Stream Semantic Grounding
* ADR-ES-006 — Agentic Workflow Semantic Grounding
* subsequent Autonomous semantic decisions
* subsequent Value Realization semantic decisions

These decisions remain independently governed.

⸻

28. Acceptance Criteria

ADR-ES-001 is considered implemented when:

1. the Enterprise-Semantics authority repository is established;
2. the normative specification repository is established;
3. the governance repository contains the required ADR, CR and Finding structures;
4. the identifier scheme is specified;
5. the semantic lifecycle is specified;
6. the governance lifecycle is operational;
7. provenance requirements are defined;
8. mapping architecture is established;
9. conformance mechanisms are established;
10. semantic publication is versionable;
11. WSF, Enterprise-Semantics, OpenDEA and DEA Catalog boundaries are documented;
12. the initial semantic seed can be introduced without creating a competing authority.

Decision State: Proposed
Implementation State: Pending CR-ES-001