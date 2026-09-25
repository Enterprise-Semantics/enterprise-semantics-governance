<!--
ADR-ES-020 , Agentic Organization020 Semantic Grounding Decision

Dash-normalized: colons (:) and semicolons (;) used consistently.
Verbatim original: 00_inbox/ADR-ES-020.md (em-dashes and ellipsis dividers preserved in source).

Status: Proposed
Decision Type: Semantic Specialization
Scope: Enterprise-Semantics
Supersedes: None
Depends on: ADR-ES-018 (Agentic Offering Semantic Grounding, Accepted 2026-09-25)
Related: CR-ES-020 (Agentic Organization Semantic Grounding, Proposed) , ADR-ES-018 (Agentic Offering Semantic Grounding, Accepted 2026-09-25) , ADR-ES-017 (Autonomous Product Semantic Grounding, Accepted 2026-09-25)

Decision: Establish Agentic Organization as a governed specialization of Organization, subject to Organization being canonically established. This ADR does NOT redefine foundational Organization semantics. If Organization is not yet canonical at implementation time, CR-ES-020 shall record the dependency rather than silently creating an Organization ontology. The principal risk is conflating Agentic Organization with Agentic Enterprise or with an organization containing Agents. CR-ES-020 must validate the Organization dependency before canonical implementation.

Slot note: this ADR is filed at governance repo docs/adr/0022-... Slot 0022 is the next free slot in the ES series. The ES series slot sequence is 0001 (Authority) , 0002 (Enterprise Semantic Model) , 0003 (Agentic Semantic Decision, ES-AG) , 0004 (Capability, ES) , 0005 (Value Stream, ES) , 0006 (Agentic, ES) , 0007 (Agentic Value Stream, ES) , 0008 (Agentic Workflow, ES) , 0009 (Agentic Operations, ES) , 0010 (Autonomous Operations, ES) , 0011 (Autonomous Value Stream, ES) , 0012 (Agentic Enterprise, ES) , 0013 (Autonomous Enterprise, ES) , 0014 (Agentic Capability, ES) , 0015 (Autonomous Capability, ES) , 0016 (Agentic Service, ES) , 0017 (Autonomous Service, ES) , 0018 (Agentic Product, ES) , 0019 (Autonomous Product, ES) , 0020 (Agentic Offering, ES) , 0021 (Autonomous Offering, ES, this ADR).

Implementation: CR-ES-020 (Agentic Organization Semantic Grounding). The CR is the implementation specification, this ADR ratifies it as a governed semantic decision. The implementation must verify the Organization dependency per ADR-ES-020 §2 + CR-ES-020 §2.

Authored by: Emmanuel A. Otchere (cardinal author rule, 2026-09-24)
-->

ADR-ES-020 / CR-ES-020 , Agentic Organization

ADR-ES-020 , Agentic Organization Semantic Grounding

Status: Proposed
Date: 2026-09-25
Decision Type: Semantic Specialization
Priority: P0
Target: Enterprise-Semantics
Authorizing Decision: ADR-ES-020
Target Release: v1.9.0
---
1. Decision

Establish Agentic Organization as a governed specialization of Organization, subject to Organization being canonically established.

Canonical Definition

An Agentic Organization is an Organization in which material organizational activities, coordination, decision-making, or execution incorporate agentic behavior to interpret delegated intent, select or coordinate actions, adapt to context, or pursue organizational outcomes within defined authority, policy, and governance boundaries.

The specialization is:

Organization
      |
      -- specializes → Agentic Organization

Agentic Organization describes an organizational mode of operation, not an organization’s use of a particular technology.
---
2. Why Organization Is a Distinct Boundary

Organization is not equivalent to:

* Enterprise;
* Capability;
* Process;
* Operations;
* Product;
* Service;
* Value Stream.

An organization establishes a boundary for coordinated actors, roles, responsibilities, authority, resources, and activities.

Agentic Organization therefore concerns agentic behavior at the organizational coordination and operating boundary.
---
3. Semantic Principle

An Agentic Organization is not merely an organization that contains Agents.

The agentic behavior must materially affect organizational:

* decision-making;
* coordination;
* execution;
* adaptation;
* delegation;
* exception management;
* organizational response.

Therefore:

Organization
 +
Material Agentic Organizational Behavior
 =
Agentic Organization
---
4. Organizational Agentic Pattern

Organizational Intent
        
        
Agentic Organization
        
        
Interpret Context
        
        
Determine / Interpret Delegated Intent
        
        
Select / Coordinate Actions
        
        
Execute
        
        
Observe Organizational Outcome
        
        
Adapt / Escalate
        ↺

Bounded by:

Authority
Policy
Governance
Constraints
Accountability
Escalation
---
5. Agentic Organization vs Agentic Enterprise

These concepts are related but distinct.

Agentic Organization
        
        
organizational operating boundary
Agentic Enterprise
        
        
enterprise-wide value realization and operation

An Agentic Enterprise may comprise multiple Agentic Organizations.

An Agentic Organization does not automatically establish an Agentic Enterprise.
---
6. Agentic Organization vs Agent

Agent
   = acting entity
Agentic Organization
   = organization-level operating mode

An Agent may operate within an Agentic Organization.

An Organization does not become Agentic merely because it contains an Agent.
---
7. Agentic Organization vs Agentic Operations

Agentic Organization
        
        
organizational boundary
        
        
may operate through
        
        
Agentic Operations

Agentic Operations describes the operating mode of operational activity.

Agentic Organization describes the broader organizational coordination boundary.
---
8. Agentic / Autonomous Orthogonality

Agentic Organization does not imply Autonomous Organization.

The dimensions are independent:

Agentic Organization
       ≠
Autonomous Organization

A future Autonomous Organization requires separate semantic grounding.
---
9. AI Boundary

AI is not required.

AI-enabled Organization
       ≠
Agentic Organization

AI may be used to enable agentic organizational behavior but does not define it.
---
10. Automation Boundary

Automation does not establish Agentic Organization.

Automated Organization
       ≠
Agentic Organization

Material agentic interpretation, decision selection, coordination, adaptation, or equivalent behavior is required.
---
11. Human Participation

Agentic Organization remains compatible with human organizational participation.

Valid configurations include:

* human decision-makers;
* human supervisors;
* human escalation;
* human-in-the-loop;
* human-on-the-loop;
* human-over-the-loop;
* delegated agent participation;
* mixed human/agent coordination.

Agentic Organization does not require replacing human organizational actors.
---
12. Canonical Relationships

Where canonical targets exist:

Agentic Organization
    +-- specializes → Organization
    +-- engages → Agent
    +-- interprets → Intent
    +-- operates-within → Authority
    +-- governed-by → Policy
    +-- constrained-by → Constraint
    +-- coordinates → Process
    +-- uses → Agentic Workflow
    +-- uses → Agentic Operations
    +-- produces → Organizational Outcome
    +-- adapts-to → Organizational Context
    +-- exercises → Capability
    -- contributes-to → Value

Only relationships whose targets are canonical shall be activated.
---
13. Organizational Authority Boundary

The central boundary is:

Intent
   
        
Delegation
   
        
Authority
   
        
Policy / Governance
   
        
Decision
   
        
Action
   
        
Outcome
   
        
Adaptation / Escalation

Agentic organizational behavior must remain bounded by organizational authority and governance.
---
14. Agentic Organization and Organizational Culture

Agentic Organization does not imply Agentic Culture.

Agentic Organization
       ≠
Agentic Culture

Organizational culture may influence how agentic behavior is adopted and governed, but culture is a distinct semantic concern.
---
15. OTCHERE Inc Example

An OTCHERE Inc organization may delegate portions of customer operations to agents.

A conventional organizational pattern:

Customer Context
      
        
Organizational Team
      
        
Human Decision
      
        
Operational Action

An Agentic Organization pattern:

Organizational Intent
      
        
Delegated Authority
      
        
Agentic Organizational Coordination
      
        
Interpret Customer / Operational Context
      
        
Select Permitted Action
      
        
Coordinate Human + Agent + System
      
        
Observe Outcome
      
        
Adapt / Escalate

The organization is agentic because agentic behavior materially participates in organizational coordination and decision execution.
---
16. Rejected Interpretations

The following are rejected:

* Agentic Organization = AI Organization
* Agentic Organization = automated organization
* Agentic Organization = organization containing Agents
* Agentic Organization = Agentic Enterprise
* Agentic Organization = Agentic Operations
* Agentic Organization = Agentic Workflow
* Agentic Organization = Autonomous Organization
* Agentic Organization = human-free organization
* Agentic Organization = organization without managers
* Agentic Organization = organization controlled entirely by Agents
* Agentic Organization = AI-native organization
---
17. Deferred Concepts

This ADR does not establish:

* Autonomous Organization;
* Agentic Culture;
* Autonomous Culture;
* Agentic Ecosystem;
* Autonomous Ecosystem;
* Agentic Network;
* Autonomous Network;
* organizational autonomy maturity;
* organizational agent hierarchy;
* Agentic Management;
* Autonomous Management.

Each requires independent governance.
---
18. Consequences

Positive

* Establishes organization as a distinct agentic semantic boundary.
* Prevents Agentic Enterprise and Agentic Organization from collapsing into one concept.
* Preserves human participation.
* Connects organizational semantics with Agentic Operations and Agentic Workflow.
* Provides a foundation for future organizational agentic/cultural analysis.

Risk

The principal risk is conflating Agentic Organization with Agentic Enterprise or simply an organization containing Agents.

Material organizational behavior must therefore be demonstrated.
---
19. Governance

Implementation is authorized through:

CR-ES-020 , Agentic Organization Semantic Grounding

No WSF or OpenDEA implementation change is authorized.
---
20. Release

Target:

Enterprise-Semantics v1.9.0

