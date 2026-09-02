<!--
ADR-ES-002 ;;; Enterprise Semantic Model

Dash-normalized: colons (:) and semicolons (;) used consistently.
Verbatim original (with em-dashes preserved): 00_inbox/ADR-ES-002.md

Dependency status (2026-09-02):
- Depends on ADR-ES-001 ;;; Organization Scaffolding and Initial Content.
- ADR-ES-001 has not been authored yet.
- Per user decision (2026-09-02, message 1544720255153082421), Path B:
  Accept ADR-ES-002 with the dependency noted, author ADR-ES-001
  alongside or after. See PLAN-CHANGELOG.md v0.4.0 and v0.5.0.
-->

# ADR-ES-002: Enterprise Semantic Model

**Status:** Proposed
**Decision Type:** Architecture / Semantic Governance
**Scope:** `Enterprise-Semantics`
**Supersedes:** None
**Depends On:** ADR-ES-001: Organization Scaffolding and Initial Content
**Enables:** Agentic Semantic Grounding and subsequent Enterprise Semantic CRs

---

## 1. Decision

Establish the **Enterprise Semantic Model** as the governed semantic layer for concepts that require **enterprise-specific meaning**, while preserving the **World Semantic Foundation (WSF)** as the authoritative source for world/foundational semantics.

`Enterprise-Semantics` shall therefore:

1. **Reference WSF rather than reproduce it.**
2. Define concepts whose semantics are specifically required to describe enterprises and enterprise phenomena.
3. Permit enterprise-specific specialization, profiling, contextualization, composition and relationship semantics.
4. Maintain stable semantic identities, definitions, relationships, provenance and lifecycle.
5. Publish machine-readable semantic artifacts as the authoritative semantic content.
6. Provide human-readable documentation as generated/presentational material.
7. Provide explicit mappings to independently governed semantic authorities and models.
8. Support downstream consumption without requiring downstream systems to copy semantic definitions.
9. Establish conformance mechanisms so semantic integrity is machine-verifiable.
10. Use the established **Finding → ADR → CR → Implementation → CI → Release** lifecycle for semantic evolution.

The initial substantive semantic implementation shall be the **Agentic Semantic Concept Set**.

---

# 2. Problem

Enterprise semantic work is increasingly producing concepts that cannot be adequately represented merely by generic world semantics.

Examples include:

* Agentic Enterprise
* Agentic Operations
* Agentic Value Stream
* Agentic Workflow
* Agentic Capability
* Agentic Service
* Agentic Product
* Autonomous Operations
* Autonomous Enterprise

These concepts describe enterprise-specific structures, behaviors, operating models and value realization patterns.

At the same time, many concepts required to describe them are already foundational concepts governed elsewhere.

Recreating those concepts inside Enterprise-Semantics would create:

* semantic duplication;
* competing definitions;
* unnecessary ontology divergence;
* mapping complexity;
* authority ambiguity.

The architecture therefore requires a clear boundary between **foundational semantics** and **enterprise specialization**.

---

# 3. Semantic Authority Boundary

The following authority boundary is established:

```text
                    World Semantic Foundation
                              │
                              │ foundational semantics
                              ▼
                    Enterprise Semantics
                              │
                              │ enterprise specialization
                              ▼
                    Enterprise Models
                              │
                              ▼
                         OpenDEA
                              │
                              ▼
                       DEA Catalogs
```

The layers are **federated**, not hierarchical ownership structures.

### WSF

WSF remains authoritative for foundational/world semantics.

### Enterprise-Semantics

Enterprise-Semantics becomes authoritative for the enterprise-specific semantic concepts within its declared scope.

### OpenDEA

OpenDEA remains authoritative for its enterprise architecture metamodel and implementation representation.

### DEA Catalogs

DEA catalogs remain authoritative for their cataloged instances.

No authority is transferred by mapping.

---

# 4. Enterprise Semantic Scope

Enterprise-Semantics shall cover semantic concepts concerned with:

* enterprise existence and organization;
* enterprise actors and roles;
* enterprise intent and governance;
* enterprise capacity and capability;
* enterprise value creation and realization;
* enterprise work and operation;
* enterprise intelligence;
* enterprise agency;
* enterprise autonomy;
* enterprise operating models;
* enterprise transformation;
* enterprise scenarios and contexts;
* enterprise measurement and value realization.

The scope is deliberately **semantic**, rather than tied to a particular architecture framework, implementation technology, vendor, industry or application.

---

# 5. Non-Scope

Enterprise-Semantics shall not become a replacement for WSF.

It shall not independently redefine generic concepts merely because they are used by enterprises.

For example, if WSF adequately establishes the semantics of:

* Entity
* Relationship
* Event
* State
* Process
* Information
* Data
* Resource
* System

Enterprise-Semantics shall reference or specialize those concepts as necessary rather than create competing definitions.

The governing principle is:

> **Enterprise context is not sufficient reason to duplicate foundational semantics.**

A new enterprise concept is justified when the enterprise context introduces semantic characteristics that are not adequately expressed by the applicable WSF concept.

---

# 6. Enterprise Specialization

Enterprise-Semantics shall support a specialization pattern:

```text
WSF Concept
     │
     │ specialization / profile / contextualization
     ▼
Enterprise Concept
```

However, inheritance shall **never be inferred merely from naming**.

For example:

```text
AI Agent
     │
     ▼
Agentic Agent
```

may ultimately be appropriate, but this must be established through semantic investigation.

Likewise:

```text
System
  │
  ▼
Autonomous System
```

is a candidate semantic relationship requiring evidence and analysis.

The subsequent Finding/ADR process determines the actual semantic relationship.

---

# 7. Semantic Concept Model

An Enterprise Semantic Concept shall be governed through, at minimum:

```text
Concept
├── Stable Identity
├── Canonical Name
├── Definition
├── Semantic Scope
├── Concept Type
├── Lifecycle Status
├── Version
├── Provenance
├── Relationships
├── Mappings
└── Evidence
```

The exact serialization schema is an implementation matter derived from this ADR.

---

# 8. Concept, Assertion and Representation

The model shall maintain a strict separation between:

### Concept

```text
Agentic Value Stream
```

### Assertion

```text
Agentic Value Stream
      realizes
Value Outcome
```

### Representation

```text
YAML
JSON
Markdown
PlantUML
Graph
Database
API
```

Therefore:

> A representation does not establish semantic authority merely because it expresses a concept or relationship.

The semantic source must remain authoritative independently of its representations.

---

# 9. Relationships Are Governed Semantic Objects

Relationships shall be first-class semantic artifacts.

A relationship shall identify, at minimum:

```text
Relationship
├── Identity
├── Subject
├── Relationship Type
├── Object
├── Qualification
├── Status
├── Provenance
├── Evidence
└── Rationale
```

This allows the organization to distinguish:

```text
"these concepts are shown together"
```

from:

```text
"this relationship has been semantically established."
```

This distinction is essential for the Agentic semantic work.

---

# 10. Enterprise Relationship Vocabulary

Enterprise-Semantics may establish relationships not already adequately provided by WSF.

Candidate examples include:

```text
specializes
realizes
enables
supports
operates-through
executes-through
orchestrates
uses
contributes-to
evolves-toward
interfaces-with
depends-on
```

These are **not automatically canonical through this ADR**.

The relationship vocabulary itself is governed semantic content and must subsequently be established through the semantic governance lifecycle.

---

# 11. Semantic Identity

Enterprise concepts shall have stable identifiers independent of:

* repository location;
* filename;
* Git branch;
* Git commit;
* documentation URL;
* implementation class;
* database key.

A concept's identity must survive representation and implementation changes.

The exact identifier syntax is to be established by the implementation CR derived from this ADR.

---

# 12. Provenance

Enterprise-Semantics shall distinguish semantic origin.

At minimum:

```text
Externally Defined
Adapted
Synthesized
Proposed
```

Existing research, models, diagrams and repositories may provide **evidence** for semantic investigation.

They do not automatically become normative semantic authority.

This permits the current Agentic body of work to be brought into Enterprise-Semantics without prematurely declaring every existing term canonical.

---

# 13. Semantic Lifecycle

Enterprise concepts shall progress through an explicit lifecycle.

The working lifecycle is:

```text
Candidate
    ↓
Investigating
    ↓
Proposed
    ↓
Established
    ↓
Canonical
    ↓
Mapped
    ↓
Deprecated / Retired
```

A concept can be **Canonical within Enterprise-Semantics** without being implemented by OpenDEA or another downstream system.

Likewise, mapping does not transfer ownership.

---

# 14. Semantic Source of Truth

The structured semantic representation in:

**`Enterprise-Semantics/enterprise-semantics`**

shall be the authoritative source for Enterprise Semantic definitions and governed semantic assertions.

Derived artifacts may include:

```text
Structured Semantic Source
        │
        ├── JSON
        ├── YAML
        ├── Markdown
        ├── PlantUML
        ├── CSV
        ├── relational representation
        └── graph representation
```

Documentation and visualizations shall therefore be treated as **derived semantic views**, unless explicitly designated otherwise.

---

# 15. Specification Authority

The organization shall maintain a distinction between:

```text
enterprise-semantics
        │
        └── semantic content

enterprise-semantics-spec
        │
        └── semantic rules/schema

enterprise-semantics-governance
        │
        └── semantic governance decisions
```

Supporting repositories may provide:

* specifications;
* governance;
* mappings;
* examples;
* documentation;
* visualizations;
* conformance testing.

None of them may independently establish a competing semantic authority.

---

# 16. Bi-Directional Integration

Enterprise-Semantics shall support bi-directional semantic integration.

### With WSF

Enterprise-Semantics may:

```text
reference
specialize
profile
align-with
map-to
```

WSF may reference enterprise-specific semantic profiles where appropriate.

### With OpenDEA

Enterprise-Semantics may establish:

```text
maps-to
represented-by
specializes
profile-of
```

OpenDEA may identify the Enterprise Semantic concept underlying an architecture construct.

### With Catalogs

Catalogs may reference Enterprise Semantic identifiers rather than copying semantic definitions.

---

# 17. Meaning of Bi-Directional Integration

Bi-directional integration **does not mean**:

* shared repositories;
* shared ownership;
* duplicated definitions;
* runtime coupling;
* synchronized source code;
* automatic inheritance.

It means:

```text
Authority A
   │
   │ stable semantic reference / mapping
   ▼
Authority B
   │
   │ independent reference / mapping
   ▼
Authority A
```

Each authority retains its own governance and lifecycle.

---

# 18. Machine Consumption

Enterprise-Semantics shall be designed as a **machine-consumable semantic authority**.

A downstream system must be able to obtain:

```text
Concept ID
Definition
Status
Version
Relationships
Provenance
Mappings
```

without parsing human-oriented prose.

Initial machine access may use repository-based artifacts and APIs.

A dedicated semantic runtime/service is not required by this ADR.

---

# 19. Conformance

Enterprise-Semantics shall establish automated conformance validation covering at least:

* unique semantic identifiers;
* valid identifiers;
* required definitions;
* valid concept references;
* valid relationship references;
* valid relationship types;
* valid inverses;
* provenance completeness;
* lifecycle validity;
* mapping validity;
* schema validity;
* version consistency;
* generated-artifact consistency.

The conformance system shall prevent invalid semantic releases.

---

# 20. Initial Semantic Implementation

The first semantic implementation under this ADR shall **not attempt to populate a complete enterprise ontology**.

The first semantic family shall be:

# Agentic Concepts

Initial candidates:

```text
Agentic AI
AI Agent
Agentic Agent
Agentic Capability
Agentic Flow
Agentic Workflow
Agentic Service
Agentic Product
Agentic Value Stream
Agentic Operations
Agentic Enterprise
Agentic Culture
```

Adjacent autonomous concepts may be investigated where necessary to establish the Agentic boundary:

```text
Autonomous System
Autonomous Flow
Autonomous Closed Loop
Autonomous Value Stream
Autonomous Operations
Autonomous Enterprise
Autonomous Ecosystem
```

They should not automatically be admitted to the initial canonical set.

---

# 21. Agentic Semantic Grounding

The next Finding shall investigate the semantic grounding of the Agentic family.

It should answer questions including:

1. What does **Agentic** mean?
2. What is an **AI Agent**?
3. Is **Agentic Agent** distinct from AI Agent?
4. What is an **Agentic Capability**?
5. What differentiates **Agentic Flow** from Workflow?
6. What differentiates **Agentic Workflow** from Workflow?
7. What makes a Value Stream **Agentic**?
8. What makes Operations **Agentic**?
9. What makes an Enterprise **Agentic**?
10. What constitutes **Agentic Culture**?
11. How does Agentic relate to Autonomous?
12. Which concepts are specializations of WSF concepts?
13. Which concepts require genuinely new enterprise semantics?
14. Which relationships among them are semantically justified?

This becomes the first major semantic investigation enabled by ADR-ES-002.

---

# 22. Architectural Constraint on Agentic Value Stream

The Agentic investigation shall preserve the distinction:

```text
Value Stream
≠
Process
≠
Workflow
≠
Task Flow
```

and shall not assume:

```text
Agentic Value Stream
    contains
Agentic Workflow
```

The relationship should initially be treated as a candidate such as:

```text
Agentic Value Stream
       executes-through
Agentic Workflow
```

until semantic investigation establishes the appropriate relationship.

Similarly, `Agentic Value Stream` shall not automatically be treated as a fundamentally new kind of Value Stream. Whether it is a specialization/profile or a distinct concept must be determined through the Finding/ADR process.

---

# 23. Governance Lifecycle

Enterprise Semantic evolution shall follow:

```text
Investigation
      ↓
Finding
      ↓
ADR
      ↓
CR
      ↓
Implementation
      ↓
CI Evidence
      ↓
Semantic Release
```

This means semantic implementation does not itself establish semantic truth.

Implementation is the consequence of an approved semantic decision.

---

# 24. Consequences

### Positive

This decision:

* prevents duplication of WSF;
* establishes a clear enterprise semantic boundary;
* gives Agentic concepts an appropriate semantic home;
* supports independent governance;
* permits downstream machine consumption;
* enables bidirectional mappings;
* preserves semantic provenance;
* makes relationships governable;
* allows semantic evolution without forcing downstream repositories to change simultaneously;
* creates a path from research concepts to governed semantics.

### Negative

It introduces additional governance discipline.

Concepts cannot simply be declared canonical because they appear useful.

There will also be additional work maintaining:

* mappings;
* provenance;
* semantic identifiers;
* lifecycle;
* conformance;
* releases.

These costs are intentional because semantic authority without governance would rapidly become another uncontrolled vocabulary.

---

# 25. Decision Summary

The essential decision can be reduced to:

> **WSF defines foundational world semantics. Enterprise-Semantics defines enterprise-specialized semantics. OpenDEA defines architectural representation and implementation. DEA Catalogs define catalog instances.**

And:

> **Enterprise-Semantics will not recreate the World Semantic Model. It will specialize and extend it only where enterprise meaning requires it.**

Finally:

> **ADR-ES-002 establishes sufficient architecture and governance to begin the first substantive semantic domain: Agentic Concepts.**

---

# Next implementation sequence

With ADR-ES-002 established, I recommend we now move directly to:

### **FND-ES-AG-001: Agentic Semantic Grounding**

This should be a **Finding, not yet a CR**.

Its output should be a semantic analysis of the existing Agentic concepts, determining their WSF grounding, enterprise specialization, definitions, boundaries and candidate relationships.

Then:

```text
FND-ES-AG-001
        ↓
Agentic Semantic Findings
        ↓
ADR-ES-AG-001
        ↓
Agentic Semantic Contract
        ↓
CR-ES-AG-001+
        ↓
enterprise-semantics implementation
        ↓
Conformance
        ↓
Agentic Semantic Release
```

That gives us exactly the progression you proposed: **ADR-ES-002 establishes the Enterprise Semantic Model once, and the Agentic concepts become the first actual semantic implementation rather than creating another round of foundational architecture work.**
