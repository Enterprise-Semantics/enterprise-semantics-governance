Yes. Given where the model now stands, I would use ES-022 as the consolidation/integrity decision and ES-023 as the next substantive semantic concept: Agentic Culture. This avoids prematurely canonicalizing Autonomous Culture before its semantic basis has been established.

Below are the four formal artifacts.

ADR-ES-022 : Agentic/Autonomous Semantic Integrity and Coverage Model

ADR-ES-022 : Agentic/Autonomous Semantic Integrity and Coverage Model

Status: Accepted
Decision Type: Semantic Architecture / Integrity
Semantic Version Target: v2.0.0
Scope: Enterprise-Semantics
Depends On: ADR-ES-001 through ADR-ES-021
Implementation: CR-ES-022

1. Decision

Establish a governed Agentic/Autonomous Semantic Integrity and Coverage Model for Enterprise-Semantics.

The model defines how Agentic and Autonomous semantics SHALL be applied consistently across enterprise concepts without requiring every concept to receive an Agentic or Autonomous specialization.

The decision establishes four governing principles:

1. Agentic and Autonomous are independent semantic dimensions.
2. A specialization SHALL be established only where the dimension materially changes the semantics of the base concept.
3. Repeated cross-cutting behavior SHALL be represented consistently and SHALL NOT be redefined independently by every specialization.
4. Candidate concepts SHALL pass a semantic coverage and dependency assessment before canonicalization.



2. Problem

Enterprise-Semantics has now established Agentic and Autonomous specializations across:

Capability
Value Stream
Service
Product
Offering
Operations
Organization
Enterprise

and Agentic specialization for Workflow.

Continued expansion without an integrity model risks:

* semantic duplication;
* accidental inheritance;
* concept proliferation;
* inconsistent property vocabularies;
* inconsistent authority semantics;
* inconsistent autonomy boundaries;
* treating AI as the definition of Agentic;
* treating automation as the definition of Autonomous;
* creating unnecessary Agentic/Autonomous variants;
* introducing concepts whose base semantics are not yet canonical.



3. Normative Semantic Dimensions

The following distinction is normative:

Agentic
  = a mode of operation involving delegated intent,
    contextual interpretation, action selection,
    coordination, adaptation, or execution.
Autonomous
  = a characteristic of independent progression through
    decisions, actions, coordination, or adaptation within
    defined boundaries.
AI
  = technology or computational capability.
Automation
  = execution mechanism.

No dimension SHALL be defined through another dimension.

Therefore:

Agentic ≠ Autonomous
Agentic ≠ AI
Autonomous ≠ AI
Autonomous ≠ Automation
Agentic ≠ Automation



4. Applicability Model

A base concept SHALL be considered for Agentic or Autonomous specialization only when the characteristic materially changes the meaning of that concept.

The following test SHALL apply:

Does Agentic behavior materially alter how the concept
operates, realizes its purpose, coordinates activity,
makes decisions, adapts, or produces outcomes?
Does Autonomous behavior materially alter how the concept
progresses independently through decisions, actions,
coordination, or adaptation?

If the answer is no, a specialization SHALL NOT be created merely for symmetry.



5. Four-State Characterization

Where both dimensions are semantically applicable, the model permits:

Agentic	Autonomous	Characterization
No	No	Conventional
Yes	No	Agentic
No	Yes	Autonomous
Yes	Yes	Agentic + Autonomous

This is a semantic characterization, not a mandatory four-class inheritance hierarchy.



6. Established Coverage

The current canonical family is:

Capability
+--- Agentic Capability
+--- Autonomous Capability
Value Stream
+--- Agentic Value Stream
+--- Autonomous Value Stream
Service
+--- Agentic Service
+--- Autonomous Service
Product
+--- Agentic Product
+--- Autonomous Product
Offering
+--- Agentic Offering
+--- Autonomous Offering
Operations
+--- Agentic Operations
+--- Autonomous Operations
Organization
+--- Agentic Organization
+--- Autonomous Organization
Enterprise
+--- Agentic Enterprise
+--- Autonomous Enterprise
Workflow
+--- Agentic Workflow

This structure is considered the current semantic baseline.



7. Cross-Cutting Agentic Pattern

Agentic specializations SHOULD consistently evaluate:

Intent
Context
Delegation
Authority
Interpretation
Action Selection
Coordination
Adaptation
Intervention
Escalation
Outcome

Not every concept requires every property.

The relevant properties SHALL be selected according to the semantic boundary of the concept.



8. Cross-Cutting Autonomous Pattern

Autonomous specializations SHOULD consistently evaluate:

Objective
Context
Autonomy Scope
Decision Scope
Action Scope
Coordination Scope
Adaptation Scope
Authority
Policy
Constraint
Governance
Intervention
Escalation
Observation
Outcome

Again, the presence of a property in the pattern does not require its mechanical inclusion in every concept.



9. Semantic Dependency Rule

A specialization SHALL NOT establish an implicit foundational concept.

For example:

Agentic System

cannot be canonicalized merely because:

System

has not yet been grounded.

Likewise:

Agentic Ecosystem
Autonomous Ecosystem
Agentic Network
Autonomous Network

require semantic grounding of their respective base concepts before specialization.



10. Candidate Classification

Future concepts SHALL be classified into one of four states:

Canonical Candidate

A concept with:

* a stable semantic boundary;
* a canonical base concept;
* materially distinct semantics;
* sufficient relationship vocabulary;
* defensible use cases.

Investigate

A concept whose semantic usefulness is plausible but whose boundary requires research.

Profile / Implementation Concept

A useful term that describes a technology, implementation, operating pattern, or domain realization rather than a foundational semantic concept.

Deferred / Rejected

A concept that is premature, duplicative, ambiguous, or insufficiently differentiated.



11. Current Candidate Register

The following concepts SHALL remain subject to investigation rather than automatic canonicalization:

Agentic Culture
Autonomous Culture
Agentic System
Autonomous System
Agentic Ecosystem
Autonomous Ecosystem
Agentic Network
Autonomous Network
Loop Engineering
Closed Loop
Autonomous Closed Loop
AI Closed Loop
AI Agent
Agentic AI
AIOps
MLOps
AI-Native Operations

The existence of a candidate in this register does not establish it as canonical.



12. Governance Concept Dependency

The Agentic/Autonomous model repeatedly depends upon:

Intent
Objective
Authority
Policy
Constraint
Governance
Accountability
Escalation
Context
Outcome

These concepts SHALL therefore be subjected to semantic grounding before the model is expanded substantially beyond ES-021.



13. Prohibition on Mechanical Symmetry

Enterprise-Semantics SHALL NOT create a corresponding Autonomous concept solely because an Agentic concept exists.

Likewise, the existence of an Autonomous concept SHALL NOT require an Agentic counterpart.

Example:

Agentic Workflow

does not automatically require:

Autonomous Workflow

A separate semantic decision is required.



14. Consequences

Positive

* Prevents concept proliferation.
* Establishes a reusable semantic discipline.
* Protects Agentic/Autonomous orthogonality.
* Creates a controlled roadmap for remaining concepts.
* Makes future ADRs more consistent.
* Enables semantic coverage analysis across the model.

Negative

* Future concepts may require investigation before implementation.
* Some intuitively attractive concepts will remain deferred.
* Semantic symmetry cannot be used as a justification for canonicalization.



15. Decision Outcome

The Agentic/Autonomous semantic family SHALL be governed through the integrity and coverage model defined by this ADR.

Future concepts SHALL be admitted through semantic evidence and dependency validation rather than simple conceptual symmetry.

Target release:

Enterprise-Semantics v2.0.0


Author: Emmanuel A. Otchere (cardinal author rule, 2026-09-24)
