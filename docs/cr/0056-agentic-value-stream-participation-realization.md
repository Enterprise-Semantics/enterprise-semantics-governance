# CR-VAS-003 ; Agentic Value Stream Participation & Realization Model

Status: Accepted
Date: 2026-10-08
Deciders: eaojnr
Decision Type: Semantic baseline (participation & realization model for Agentic Value Stream)
Concept: Agentic Value Stream (ES:CONCEPT:agentic-value-stream)
Repository: Enterprise-Semantics/agentic-value-stream
Priority: Critical
Type: Semantic Model / Relationship Model / Metamodel Alignment / Conformance
Target: Agentic Value Stream semantic baseline v1.x
Implements: ES-ADR-053
Depends: CR-VAS-002 + ES-ADR-052

## 1. Change Objective

Establish the formal semantic model by which Agentic Value Stream (AVS) represents agentic participation within a canonical Value Stream.

CR-VAS-002 establishes the conditions under which a Value Stream qualifies as Agentic. CR-VAS-003 defines the semantic structure required to represent that qualification.

The change SHALL establish:

- What constitutes Agentic Participation.
- Who or what participates.
- Where participation occurs.
- What authority is delegated.
- What intent is entrusted.
- What contextual information is interpreted.
- What decisions/actions may be selected.
- How participation contributes to value realisation.
- How human and agentic participants interact.
- How localised agentic behavior is represented without creating parallel Value Stream constructs.
- How agentic realisation is distinguished from process, workflow, automation, AI, and autonomy.

### Core principle

Agentic Value Stream describes the manner in which value is realised; it does not replace the Value Stream, create a parallel value-stage hierarchy, or make the Agent the semantic center of the model.

## 2. Problem Statement

The repository currently establishes strong characteristics for agentic behavior but requires a more explicit representation model.

Without such a model, implementations are likely to introduce one or more of the following ambiguities:

- Treating an Agent as sufficient evidence of an Agentic Value Stream.
- Treating every AI-enabled Value Stream as agentic.
- Creating an Agentic Value Stage parallel to the canonical Value Stage.
- Confusing an agent with the authority delegated to it.
- Confusing an instruction with intent.
- Confusing recommendation with action selection.
- Confusing workflow orchestration with agentic coordination.
- Treating autonomy as a prerequisite.
- Representing an entire Value Stream as agentic when only one material decision is agentic.
- Failing to identify where agentic participation actually affects value realisation.

CR-VAS-003 therefore introduces an explicit Agentic Participation model while preserving the canonical Value Stream as the primary semantic structure.

## 3. Normative Semantic Principle

Agentic Participation SHALL be SUBORDINATE to the Value Stream. The semantic dependency is:

```
Value Stream
   |
   +-- Value Stage / Value-Realization Area
   |
   +-- Agentic Participation
            |
            +-- Actor / Agent
            +-- Entrusted Intent
            +-- Bounded Authority
            +-- Context
            +-- Decision / Selection
            +-- Action / Progression
            +-- Outcome Contribution
```

The Agentic Participation relationship does NOT become a replacement for Value Stream, Value Stage, Business Process, Business Capability, Workflow, Organization, Actor, or Agent.

## 4. Proposed Semantic Structure

### 4.1 Value Stream

The canonical Value Stream inherited from the underlying Enterprise Semantics / OpenDEA semantic foundation. AVS SHALL remain a specialisation of Value Stream.

```
Agentic Value Stream is a subset of Value Stream
```

### 4.2 Agentic Participation

Agentic Participation represents the fact that an actor participates in the realisation of a material portion of a Value Stream through agentic behavior. It is the semantic bridge between the Value Stream and the actor performing agentic realisation.

Conceptually:

```
Value Stream
   | has agentic participation
   v
Agentic Participation
   |
   +-- performed by -> Actor / Agent
   +-- advances -> Intent
   +-- governed by -> Authority
   +-- interprets -> Context
   +-- selects -> Action / Progression
   +-- contributes to -> Outcome
```

Critical rule: The Agent is NOT the definition of agenticity. Agentic Participation is. An Agent may exist without Agentic Participation. Conversely, agentic participation may be realised without a technical object explicitly classified as an Agent.

## 5. Agentic Participation as a Relationship, Not a New Value-Stage Type

The repository SHALL NOT introduce Agentic Value Stage, Agentic Process, Agentic Workflow, Agentic Operation, or Agentic Activity as parallel semantic constructs solely to represent agenticity.

Instead:

```
Value Stream
   +-- Value Stage
          +-- Agentic Participation
```

This permits a canonical Value Stage to contain human realisation, automated realisation, agentic realisation, hybrid realisation, or multiple forms of realisation.

## 6. Participation Scope

Agentic Participation SHALL support explicit scope.

```
agentic_scope:
  - decision
  - execution
  - coordination
  - stage
  - cross_stage
  - end_to_end
```

- `decision`: Agentic behavior materially affects a consequential decision.
- `execution`: Agentic behavior selects or performs a material action.
- `coordination`: Agentic behavior materially coordinates progression.
- `stage`: Agentic participation materially affects a Value Stage.
- `cross_stage`: Agentic participation materially affects progression across multiple Value Stages.
- `end_to_end`: Agentic participation materially governs or contributes across substantially the entire Value Stream.

`end_to_end` SHALL NOT be the default representation. A Value Stream can qualify as Agentic because of a single material agentic participation point.

## 7. Entrusted Intent

Agentic Participation SHALL reference an explicit intended outcome, objective, purpose, or progression objective.

The model SHALL distinguish Instruction from Intent. Instruction is a predetermined directive (e.g. "Execute step 4 after step 3"). Intent is a desired outcome or progression objective (e.g. "Resolve the customer's issue within policy and service-level constraints.").

Agentic Participation requires an entrusted or delegated purpose, not merely an executable instruction.

## 8. Authority Model

Agentic Participation SHALL explicitly represent the authority under which action selection occurs. At minimum, authority SHALL be representable through scope, permissions, constraints, policies, thresholds, escalation conditions, and revocation conditions.

Authority may be bounded by role, policy, financial threshold, operational threshold, risk threshold, regulatory constraint, security constraint, data-access constraint, escalation rule, human approval requirement, temporal constraint, or geographic constraint.

Semantic principle: Intent establishes what is being pursued; authority establishes what may legitimately be done in pursuit of it. Neither is sufficient independently.

## 9. Context Interpretation

Agentic Participation SHALL identify the relevant context upon which progression or action selection depends.

Context may include current state, customer state, transaction state, environmental conditions, policy state, resource availability, historical information, signals/events, external conditions, or other Value Stream state.

The model does not require a particular technology for context interpretation.

## 10. Decision and Action Semantics

The model SHALL distinguish:

```
Instruction
   |
   v
Evaluation
   |
   v
Recommendation
   |
   v
Selection
   |
   v
Commitment
   |
   v
Execution
```

These SHALL NOT be treated as interchangeable. The critical transition is Selection among permissible alternatives in pursuit of an entrusted outcome. A system that only evaluates a fixed rule set without meaningful selection does not become agentic merely because the evaluation is sophisticated.

## 11. Permissible Action Space

Agentic Participation SHALL be capable of representing the set or class of actions available to the participating actor.

Conceptually:

```
Intent + Context + Authority -> Permissible Action Space -> Action / Progression Selection
```

The model need not enumerate every possible action. It must, however, make it possible to establish that more than one permissible response/path exists AND that the realised response is selected contextually rather than completely predetermined.

## 12. Outcome Contribution

Agentic Participation SHALL connect to the Value Stream's realisation of value.

The model SHALL therefore distinguish:

```
Action selected -> Value Stream progression -> Stakeholder / value outcome
```

The existence of an agentic decision without material value-stream consequence SHALL NOT automatically qualify the Value Stream as Agentic. This reinforces the materiality requirement from CR-VAS-002.

## 13. Human Participation

Human participation SHALL be modelled as a valid realisation pattern rather than as an exception.

Supported patterns SHALL include:

- Pattern A: Human delegates an intended outcome to an Agent.
- Pattern B: Agent escalates an exception or threshold to a Human, who decides.
- Pattern C: Human decides, Agent executes.
- Pattern D: Agent decides, Human validates, then execution.
- Pattern E: Shared progression (Human and Agent alternate).

All five are valid provided the underlying AVS qualification conditions are satisfied.

## 14. Agent Semantics

The semantic model SHALL distinguish:

```
Agent != Agentic Participation != Agentic Value Stream
```

- Agent: A participating actor or implementation construct capable of performing delegated behavior.
- Agentic Participation: A semantic realisation relationship in which agentic behavior contributes materially to Value Stream realisation.
- Agentic Value Stream: A Value Stream that contains one or more qualifying instances of Agentic Participation.

## 15. AI Semantics

AI SHALL remain orthogonal. Valid configurations include AI + non-agentic, AI + agentic, non-AI + agentic, human + agentic, automation + agentic, and AI + automation + agentic. The presence of AI SHALL never itself satisfy AVS qualification.

## 16. Automation Semantics

The model SHALL preserve:

```
Automation != Agentic Participation
```

Automation can participate in an AVS. The automated component does not become agentic simply because it is downstream of an agent.

## 17. Autonomy Semantics

Autonomy SHALL remain an independent dimension. A Value Stream may be:

- Agentic + highly human-supervised.
- Agentic + partially autonomous.
- Agentic + highly autonomous.

Autonomy describes the degree of independent operation. Agenticity describes the presence of delegated, bounded, contextual, outcome-oriented action selection.

## 18. Realization Composition

Replace ambiguous single-axis realisation_mode semantics with explicit dimensions:

```
realization:
  composition: [human, automated, agentic, hybrid]
  agentic_scope: [decision, execution, coordination, stage, cross_stage, end_to_end]
  autonomy:
    level:
  human_involvement:
    mode:
```

This avoids conflating composition with scope, authority, autonomy, and human involvement.

## 19. Canonical Relationship Set

CR-VAS-003 SHALL establish the following conceptual relationships:

```
Agentic Value Stream
   |
   +-- specialises -> Value Stream
   |
   +-- contains / has -> Agentic Participation
                              |
                              +-- performed by -> Actor / Agent
                              +-- advances -> Entrusted Intent
                              +-- governed by -> Bounded Authority
                              +-- interprets -> Context
                              +-- selects -> Permissible Action
                              +-- affects -> Value Stream Progression
                              +-- contributes to -> Value Outcome
                              +-- may escalate to -> Human
```

Where applicable:

```
Agentic Participation
   |
   +-- occurs within -> Value Stage
   +-- affects -> Decision
   +-- realises -> Action
   +-- coordinates -> Participant
```

## 20. Cardinality Principles

The semantic model SHALL support:

- Value Stream: 1..* Agentic Participation.
- Agentic Participation: 1 Actor/Agent, 1 Intent, 1 Authority, 1..* Context, 1..* permissible actions, 1 material Value Stream contribution.
- Human escalation: 0..* Human escalation relationships.
- A single actor may participate in multiple Agentic Participation instances.
- A single Value Stage may contain zero or more Agentic Participation instances.

Not every Value Stage must be agentic.

## 21. Distributed and Hybrid Agentic Realization

The model SHALL explicitly support distributed agentic realisation. Example:

```
Value Stream
 +-- Stage A
 |    +-- Human
 +-- Stage B
 |    +-- Agentic Participation
 |         +-- Agent
 +-- Stage C
 |    +-- Automated Execution
 +-- Stage D
      +-- Human + Agent
```

This remains a single Value Stream. No parallel "Agentic Value Stream" needs to be constructed merely to represent the agentic portions.

## 22. Semantic Boundary Matrix

The repository SHALL add a normative boundary matrix:

| Concept | Has objective | Uses context | Selects action | Bounded authority | Material VS effect |
|---|---|---|---|---|---|
| Deterministic automation | +/- | No | No | No/implicit | Yes |
| AI recommendation | No | Yes | No | No | Potential |
| Human discretion | Yes | Yes | Yes | Yes | Yes |
| Agentic participation | Yes | Yes | Yes | Yes | Yes |
| Autonomous system | Potential | Yes | Yes | Variable | Not necessarily |
| Workflow | No | Limited | No | No | Potential |
| AI system | Variable | Variable | Variable | Variable | Variable |

This matrix becomes normative guidance rather than merely explanatory documentation.

## 23. Evidence Model

An AVS instance SHOULD be capable of supplying evidence for its qualification.

Recommended evidence structure: intent, authority, context, alternatives, selection, action, outcome_effect, intervention.

Evidence answers: How do we know that this participation is actually agentic? Full evidence semantics are landed under CR-VAS-004.

## 24. Conformance Implications

CR-VAS-003 SHALL extend the conformance kit introduced under CR-VAS-002.

Structural tests:

- VAS-ST-01 AVS specialises Value Stream.
- VAS-ST-02 Agentic Participation is represented explicitly.
- VAS-ST-03 Agent presence does not imply AVS.
- VAS-ST-04 Agentic Participation references an intent.
- VAS-ST-05 Agentic Participation references bounded authority.
- VAS-ST-06 Context is represented.
- VAS-ST-07 Action/progression selection is represented.
- VAS-ST-08 Material value contribution is represented.

Boundary tests:

- VAS-BT-01 AI without agentic participation.
- VAS-BT-02 Automation without agentic participation.
- VAS-BT-03 Workflow orchestration without agentic participation.
- VAS-BT-04 Agent present but deterministic behavior.
- VAS-BT-05 Autonomous system without Value Stream materiality.
- VAS-BT-06 Human discretion satisfying the conditions.
- VAS-BT-07 Agentic participation localised to one Value Stage.
- VAS-BT-08 Hybrid human-agent realisation.
- VAS-BT-09 Multi-agent coordination.
- VAS-BT-10 Agentic participation without AI.

## 25. Required Examples

The repository SHALL add canonical examples representing at least:

- Example 1: Agentic Decision (a customer-service agent selects an appropriate resolution path within policy).
- Example 2: Agentic Execution (an agent selects and executes an operational action within bounded authority).
- Example 3: Human-Agent Hybrid (agent resolves ordinary cases and escalates exceptions).
- Example 4: Distributed Agentic Value Stream (different Value Stages contain independent agentic participation).
- Example 5: Multi-Agent Coordination (multiple agents coordinate progression while remaining subordinate to the Value Stream).
- Example 6: False Positive (an AI recommendation system that never selects or commits to action).
- Example 7: False Positive (an autonomous technical system that has no material Value Stream relationship).
- Example 8: Non-AI Agentic Realization (a non-generative implementation that still satisfies delegated intent, contextual interpretation, bounded authority, action selection, and outcome contribution).

## 26. OpenDEA Alignment

CR-VAS-003 SHALL preserve the principle that AVS extends the semantics of Value Stream and does NOT create an alternative process/value architecture.

OpenDEA mappings SHALL therefore distinguish:

```
Value Stream -> Agentic Value Stream (specialisation) -> Agentic Participation (realisation) -> Business Process / Capability / Actor / Agent / Technology (may involve)
```

Agentic Participation MUST NOT be used as a substitute for Process, Capability, Organization, Application, Technology, or Workflow.

## 27. WSF Alignment

WSF alignment SHALL remain a semantic mapping rather than an assertion that Agentic Value Stream is necessarily a native WSF primitive.

Mapping types SHALL explicitly distinguish:

```
mapping_type:
  - specialisation
  - semantic_alignment
  - realisation_mapping
  - implementation_mapping
  - conceptual_correspondence
```

This prevents accidental metamodel mutation through mapping documentation.

## 28. Machine-Readable Model

The repository SHOULD evolve toward a structure conceptually similar to:

```yaml
agentic_participation:
  required:
    participant:
    intent:
    authority:
    context:
    action_selection:
    value_contribution:
  scope:
    allowed: [decision, execution, coordination, stage, cross_stage, end_to_end]
  relationships:
    performed_by: Actor
    may_be_realised_by: Agent
    occurs_within: ValueStage
    advances: Intent
    governed_by: Authority
    interprets: Context
    selects: Action
    contributes_to: ValueOutcome
    may_escalate_to: Human
  exclusions:
    - agent_presence_only
    - ai_presence_only
    - automation_only
    - recommendation_only
    - workflow_orchestration_only
```

This is illustrative rather than a final schema contract. The exact schema is reconciled with the existing repository structure.

## 29. Governance Rules

The repository SHALL establish the following governance rules:

- Rule 1: Value Stream remains primary. Agentic semantics cannot redefine the underlying Value Stream.
- Rule 2: Participation is explicit. Agentic behavior should be represented explicitly rather than inferred solely from the presence of an Agent.
- Rule 3: Authority is explicit. An agent cannot be considered agentic solely because it can execute actions.
- Rule 4: Materiality is mandatory. Agentic behavior must materially contribute to Value Stream realisation.
- Rule 5: AI is implementation-independent. No AI dependency shall be introduced into the semantic definition.
- Rule 6: Autonomy is orthogonal. Autonomy shall not be used as a proxy for agenticity.
- Rule 7: Human participation is first-class. Human involvement shall never invalidate AVS qualification.
- Rule 8: No parallel value-stage ontology. Agentic participation shall overlay canonical Value Stream semantics.

## 30. Required Repository Changes

CR-VAS-003 SHALL update, as applicable:

- `concept.yaml` (with the `participation:` block).
- `kit/kit.yaml` (with the expanded coverage and inventory).
- `kit/structural-01..08.yaml` (new structural tests).
- `kit/boundary-01..10.yaml` (new boundary tests).
- `docs/concept.md` (with the Participation and Realization section).
- `docs/conformance.md` (with the expanded test inventory).
- `mappings/wsf.yaml` (with the `participation_alignment` block).
- `mappings/opendea.yaml` (with the `participation_alignment` block).
- `visuals/agentic-value-stream/participation-model.puml` (new).
- `visuals/agentic-value-stream/semantic-boundary-matrix.puml` (new).

The exact directory names are reconciled with the existing repository convention.

## 31. Acceptance Criteria

CR-VAS-003 is accepted only when:

AC-01. Agentic Value Stream remains a specialisation of Value Stream.
AC-02. Agentic Participation is explicitly represented.
AC-03. Agentic Participation is not equivalent to Agent.
AC-04. Agent presence alone cannot qualify an AVS.
AC-05. Intent is explicitly representable.
AC-06. Authority is explicitly representable.
AC-07. Context is explicitly representable.
AC-08. Permissible action/progression selection is explicitly representable.
AC-09. Material Value Stream contribution is explicitly representable.
AC-10. Participation scope is machine-readable.
AC-11. Stage-level agentic participation is supported.
AC-12. Decision-level agentic participation is supported.
AC-13. Execution-level agentic participation is supported.
AC-14. Cross-stage agentic participation is supported.
AC-15. End-to-end realisation is supported without becoming mandatory.
AC-16. Human-agentic patterns are represented.
AC-17. AI remains optional.
AC-18. Automation remains distinct.
AC-19. Autonomy remains distinct.
AC-20. Workflow remains distinct.
AC-21. Autonomous technical systems without material Value Stream participation do not qualify.
AC-22. Non-AI agentic implementations can qualify.
AC-23. Distributed/hybrid AVS realisation is supported.
AC-24. Evidence supporting qualification can be represented.
AC-25. Structural and boundary conformance tests are implemented.
AC-26. OpenDEA mappings remain non-invasive.
AC-27. WSF mappings distinguish semantic alignment from metamodel equivalence.
AC-28. Documentation, schemas, examples, mappings and tests agree.
AC-29. No Agentic Value Stage, Agentic Workflow, or equivalent parallel ontology is introduced.
AC-30. CI validates the structural and semantic consistency of the model.

## 32. Definition of Done

CR-VAS-003 is complete when the repository contains a coherent and machine-testable Agentic Participation & Value Stream Realization Model in which:

```
Value Stream -> Agentic Participation -> Intent + Authority + Context -> Selection -> Action / Progression -> Material Value Contribution
```

can be represented without introducing a competing Value Stream ontology.

The repository must be able to answer, for any claimed AVS:

1. What Value Stream is being realised?
2. Where does agentic participation occur?
3. Who/what participates?
4. What intent has been entrusted?
5. What authority has been delegated?
6. What context is interpreted?
7. What permissible alternatives exist?
8. What was selected?
9. What action/progression resulted?
10. How did this materially affect Value Stream realisation?
11. What happens when authority is exceeded?
12. Where and how can humans intervene?

If those questions cannot be answered, the representation is incomplete.

## 33. Strategic Rationale

CR-VAS-002 establishes whether something is Agentic. CR-VAS-003 establishes how that agenticity is represented.

This distinction is critical. Without CR-VAS-003, the repository risks having a strong conceptual definition but weak instance semantics. Different implementers could satisfy CR-VAS-002 while representing the resulting AVS in incompatible ways.

CR-VAS-003 therefore creates the semantic bridge between:

```
Concept -> Qualification -> Participation -> Realisation -> Evidence -> Conformance
```

The intended result is that Agentic Value Stream becomes a semantic construct that can be instantiated, inspected, tested, mapped and governed rather than simply described.

## 34. Relationship to CR-VAS-002

The two CRs should be treated as complementary:

- CR-VAS-002: What makes a Value Stream Agentic? Output: Qualification semantics.
- CR-VAS-003: How is that agenticity represented? Output: Participation/realisation model.

This creates a clean progression:

```
CR-VAS-002 (Semantic Qualification)
   |
   v
CR-VAS-003 (Participation & Realization)
   |
   v
CR-VAS-004 (Evidence & Conformance)
```

CR-VAS-003 SHALL NOT repeat CR-VAS-002's qualification rules. It SHALL reference them and make them structurally representable.

The important architectural consequence is that CR-VAS-003 gives the repository a semantic spine: Value Stream -> Agentic Participation -> Intent / Authority / Context -> Selection -> Action -> Outcome. This spine determines the scope of CR-VAS-004.

## 35. Promotion Metadata

- Status: Accepted (semantic baseline extension, 2026-10-08).
- Cardinal author rule: Emmanuel A. Otchere (cardinal author rule, 2026-09-23).
- Vendor-specific material from embargoed sources: 0 references.
- D-004 dash rule: 0 en-dash (U+2013), 0 em-dash (U+2014), 0 triple-em-dash (U+2E3B).
- WSF metamodel not modified.
- OpenDEA metamodel not modified.

## 36. Related Artefacts

- ES-ADR-053 (Agentic Value Stream Participation & Realization Framework).
- ES-ADR-052 (Agentic Value Stream Semantic Qualification Framework).
- ES-ADR-005 (Agentic Value Stream decision).
- ES-ADR-031 (5-category boundary taxonomy).
- ES-ADR-049 (Per-Concept Repo Self-Containment).
- ES-ADR-051 (Editorial Restructure).
- CR-AVS-001 (Repository Conformance Reconciliation).
- CR-VAS-002 (Formal Semantic Qualification).
- FND-ES-AG-008 (Foundation Recon).
