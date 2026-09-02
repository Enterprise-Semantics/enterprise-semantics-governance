<!--
FND-ES-AG-001-Grounding-Result ;;; Agentic Semantic Grounding Result

Dash-normalized: colons (:) and semicolons (;) used consistently.
Verbatim original (em-dashes preserved): 00_inbox/FND-ES-AG-001-Grounding-Result.md.

Status: Proposed Finding (companion to FND-ES-AG-001).
Author: eaojnr (user revision).
Date authored: 2026-09-02.
Date ingested: 2026-09-02.
Depends on: FND-ES-AG-001 (canonical) ;;; WSF live baseline (Capability,
  Entity, Disposition).
Supplements: ADR-ES-002 ;;; ADR-ES-AG-001 (Accepted).

Key correction: do not create a parallel Agentic ontology ;;; specialize
WSF where possible. Reject several "Agentic X" concepts that may be
properties, profiles, or specializations rather than independent concepts.

-->

Yes. I have now grounded the Agentic family against the **live WSF baseline and the live Enterprise-Semantics structure**, rather than treating the previously proposed Agentic vocabulary as authoritative.

The most important result is that **we should not create a parallel Agentic ontology**. We should establish an enterprise semantic specialization that reuses WSF foundations and adds only the enterprise meaning that is actually new.

WSF explicitly defines its Tier 1 foundation as `Entity`, `Concept`, `Relationship`, `Event`, `State`, `Disposition`, `Proposition`, `Assertion`, `Identity`, `Context`, `Time`, and `Space`; it also explicitly states that downstream semantic systems specialize and extend WSF without redefining foundational meaning. ([GitHub][1])

## FND-ES-AG-001: Grounding Result

I recommend we now regard the following as the **Draft Agentic Semantic Grounding Matrix**.

| Candidate                | WSF grounding                                                                                  | Enterprise treatment                                                          | Initial disposition             |
| ------------------------ | ---------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ------------------------------- |
| **Agentic AI**           | AI is not currently established as a WSF Tier 1 concept                                        | Enterprise concept/profile concerning AI exhibiting agency characteristics    | **Investigate**                 |
| **AI Agent**             | Ground in WSF `Entity`, `Disposition`, `Capability`, `Action/Activity` semantics as applicable | Specialized enterprise agent concept                                          | **Investigate**                 |
| **Agentic Agent**        | Ground in `Entity` + agent-related disposition/capability                                      | Potentially redundant with AI Agent                                           | **Challenge**                   |
| **Agentic Capability**   | Directly grounded in WSF `Capability`                                                          | Enterprise specialization/profile only if agency changes capability semantics | **Investigate**                 |
| **Agentic Flow**         | Ground in WSF `Process`/`Event`/`State`/`Relationship` semantics as applicable                 | Enterprise execution construct                                                | **Investigate**                 |
| **Agentic Workflow**     | Workflow is not a WSF Tier 1 concept                                                           | Enterprise workflow specialization                                            | **Investigate**                 |
| **Agentic Service**      | Ground in WSF `Entity`/`Capability`/`Relationship` semantics                                   | Enterprise service specialization/profile                                     | **Investigate**                 |
| **Agentic Product**      | Ground in WSF `Entity`/`Capability`/`Value`-related semantics                                  | Enterprise product specialization/profile                                     | **Investigate**                 |
| **Agentic Value Stream** | Must preserve WSF grounding and enterprise Value Stream semantics                              | Enterprise specialization/profile                                             | **High-priority investigation** |
| **Agentic Operations**   | Ground in WSF entities, dispositions, events, states, relationships                            | Genuine enterprise operating concept candidate                                | **High-priority investigation** |
| **Agentic Enterprise**   | Ground in WSF `Entity` + enterprise specialization                                             | Enterprise-level specialization/profile                                       | **High-priority investigation** |
| **Agentic Culture**      | Ground in WSF entity/disposition/context semantics                                             | Enterprise organizational/cultural concept                                    | **Investigate**                 |

This immediately reveals an important correction to our earlier thinking:

> **Several names in the Agentic vocabulary are not necessarily concepts. Some may turn out to be properties, profiles, specializations, or contextual compositions.**

That is precisely what the grounding exercise should expose.

---

# 1. WSF grounding is stronger than we previously assumed

The WSF Capability definition is particularly important.

WSF defines Capability as a specialized form of `Disposition`, grounded in Capacity + Ability and attributable to an Entity in a context. It explicitly distinguishes Capability from Process, Function, Service, Outcome and Resource. ([GitHub][2])

It also already establishes a specialization pattern:

```text
WSF Capability
      │
      ├── Business Capability
      ├── Operational Capability
      ├── Technical Capability
      ├── Organizational Capability
      └── Digital Capability
```

and explicitly requires specializations to preserve Capability semantics. ([GitHub][2])

Therefore I would **not** create an independent Enterprise-Semantics `Capability`.

Likewise, I would not initially create:

```text
Enterprise-Semantics/Capability
```

Instead:

```text
wsf:Capability
       │
       │ specialization/profile
       ▼
es:AgenticCapability
```

and even that should only survive if agency introduces a meaningful semantic distinction.

---

# 2. This changes the Agentic Capability hypothesis

Our earlier hypothesis was:

```text
Capability
   │
   └── specialized-by
          ▼
Agentic Capability
```

The grounding now says:

**Possible, but not yet demonstrated.**

We need to ask:

> What makes a Capability specifically Agentic?

If the answer is merely:

> "The capability is performed by an AI agent."

then `Agentic Capability` may **not** be a new kind of Capability.

It may instead be:

```text
Capability
     │
     ├── bearer → AI Agent
     │
     └── execution characteristic → Agentic
```

Conversely, if Agentic Capability has distinct semantic properties involving agency, goal-directed choice, delegation, reasoning, adaptation or autonomous action, then a specialization may be justified.

That is a much stronger investigation.

---

# 3. AI Agent needs the same treatment

We should avoid the chain:

```text
AI
 ↓
AI Agent
 ↓
Agentic Agent
```

until we know that each represents a genuine semantic distinction.

I currently see three plausible models:

### Model A: specialization

```text
Agent
  │
  ▼
AI Agent
  │
  ▼
Agentic Agent
```

### Model B: intersection/profile

```text
             Agent
               ▲
               │
AI ─────────────┼────────────
               │
          AI Agent
               │
        Agentic characteristic
```

### Model C: agent as enterprise role/capability bearer

```text
Entity
  │
  ├── Role
  ├── Capability
  └── Agentic disposition
```

We should not choose among these yet.

**Agentic Agent should therefore remain a challenged candidate**, rather than automatically entering the canonical seed.

---

# 4. Agentic Workflow is much more promising

Here the distinction appears stronger.

We already have:

```text
Process
Workflow
Task Flow
```

and the enterprise semantic work needs to preserve these distinctions.

The candidate:

```text
Agentic Workflow
```

can therefore be investigated as:

```text
Workflow
   │
   └── specializes / profiles
             ▼
      Agentic Workflow
```

where the distinguishing semantic characteristic might concern:

* agent participation;
* agent selection;
* dynamic planning;
* goal-directed execution;
* delegation;
* contextual decision-making;
* adaptation.

The key is that **Agentic Workflow remains a Workflow first**.

It should not become a generic "agentic thing that executes work."

---

# 5. Agentic Flow must not collapse into Workflow

This is another important grounding result.

I would retain:

```text
Agentic Flow
```

as a candidate, but explicitly investigate whether it is actually needed.

We could end up with:

```text
Agentic Workflow
       │
       └── orchestrates
              ▼
         Agentic Flow
```

or we could discover that "Agentic Flow" is simply the runtime realization of an Agentic Workflow and does not warrant an independent semantic concept.

That is exactly the kind of question the Finding should resolve.

---

# 6. Agentic Value Stream is the most important investigation

This remains the most structurally significant candidate.

We should start from:

```text
Value Stream
```

and ask whether:

```text
Agentic Value Stream
```

is genuinely:

```text
Value Stream
      │
      └── specialization/profile
```

rather than creating a separate value-stream ontology.

The current Enterprise-Semantics repository already anticipates an **Agentic Value Stream worked example** and an **Agentic vs Autonomous comparative scenario**, which confirms that these are intended as explicit semantic investigation areas rather than generic vocabulary. ([GitHub][3])

The key semantic test should be:

> Does agency change the meaning of Value Stream, or does it describe a characteristic of how the Value Stream is realized?

My current hypothesis is:

```text
Value Stream
      │
      ▼
Agentic Value Stream
```

as a **specialization/profile**, not a new foundational kind.

But this remains a Finding outcome, not a decision.

---

# 7. Agentic Operations is likely a genuine enterprise concept

This one is different.

`Agentic Operations` describes an enterprise operating phenomenon, not merely an implementation technology.

A useful initial model is:

```text
Enterprise
    │
    └── operates-through
              ▼
       Operating Model
              │
              ▼
       Agentic Operations
```

with Agentic Operations potentially involving:

```text
Goals
  ↓
Agentic Decision
  ↓
Agentic Action
  ↓
Operational Event
  ↓
Operational State
  ↓
Observation
  ↓
Adaptation
```

The semantic distinction from `Autonomous Operations` must then be established.

This is probably one of the strongest candidates for a genuine Enterprise-Semantics concept.

---

# 8. Agentic Enterprise

Likewise, `Agentic Enterprise` appears to be a legitimate enterprise specialization candidate.

But we should **not define it simply as "enterprise using AI agents."**

The investigation should determine whether an Agentic Enterprise requires agentic characteristics across:

```text
Enterprise
├── Strategy
├── Governance
├── Capability
├── Value Creation
├── Operations
├── Decision
├── Work
└── Culture
```

This is potentially a semantic profile of an Enterprise rather than a completely separate Entity type.

That distinction will matter greatly to OpenDEA later.

---

# 9. Agentic Culture

This is probably the least mature candidate.

It should remain in the investigation because it appears in the existing conceptual work, but we should resist defining it too early.

The first question is:

> Is Agentic Culture a semantic concept in its own right, or a characterization of organizational dispositions, behaviors, norms and practices?

It may ultimately be better modeled as a **contextual/profile construct** rather than a standalone enterprise object.

---

# 10. The Agentic Semantic Graph

After grounding, I would reduce the initial graph to this **investigation graph**:

```text
                         Enterprise
                              │
                       operates-through
                              ▼
                    Agentic Operations
                              │
                         enables / supports
                              ▼
                    Agentic Value Stream
                              │
                       executes-through
                              ▼
                    Agentic Workflow
                              │
                         orchestrates
                              ▼
                       Agentic Flow
                              │
                              │ uses
                              ▼
                          AI Agent
                              │
                              │ uses
                              ▼
                          AI Model
```

And alongside it:

```text
WSF Capability
       │
       └── ? specialization/profile
                    ▼
           Agentic Capability
```

and:

```text
WSF / Agent
       │
       └── ? specialization/profile
                    ▼
                 AI Agent
```

This is much cleaner than the earlier broad graph.

---

# 11. Agentic vs Autonomous

The comparative work should be retained as a **boundary investigation**, not a classification decision.

The initial semantic hypothesis is:

```text
                 Agency
                   │
                   ▼
               AGENTIC
                   │
                   │ may exhibit
                   ▼
              AUTONOMOUS
```

and separately:

```text
Autonomous
   │
   ├── self-governance
   ├── self-adaptation
   └── independent execution
```

while:

```text
Agentic
   │
   ├── goal-directed agency
   ├── contextual decision
   ├── delegation
   ├── orchestration
   └── adaptive action
```

The overlap needs investigation.

We should **not** establish:

```text
Agentic ⊂ Autonomous
```

or:

```text
Autonomous ⊂ Agentic
```

at this stage.

---

# 12. What I would now classify

### Strong candidates for Enterprise-Semantics

```text
Agentic Operations
Agentic Enterprise
Agentic Value Stream
Agentic Workflow
```

### Conditional candidates

```text
Agentic Capability
AI Agent
Agentic AI
Agentic Service
Agentic Product
Agentic Culture
Agentic Flow
```

### Candidate requiring particular scrutiny

```text
Agentic Agent
```

because it may be terminologically redundant with AI Agent or represent a different semantic distinction.

---

# 13. Most important conclusion

The grounding exercise has produced a useful architectural rule:

> **The Agentic semantic family should not be modeled as a flat taxonomy of "Agentic X" concepts.**

Instead it should be modeled as a set of **enterprise specializations, profiles and relationships grounded in WSF concepts**, with only genuinely new enterprise semantics receiving independent concept status.

That gives us:

```text
                 WSF
                  │
       foundational semantics
                  │
        ┌─────────┴──────────┐
        ▼                    ▼
     Capability            Entity
        │                    │
        │                    │
        ▼                    ▼
Agentic Capability       AI Agent
                              │
                              ▼
                       Agentic behavior
                              │
          ┌───────────────────┼─────────────────┐
          ▼                   ▼                 ▼
 Agentic Workflow     Agentic Operations   Agentic Enterprise
          │                   │                 │
          └───────────────────┼─────────────────┘
                              ▼
                    Agentic Value Stream
```

The exact arrows remain hypotheses.

---

# Recommended next move

I think we have enough to **freeze FND-ES-AG-001 as the grounding Finding**, but **not enough to write the Agentic ADR yet**.

The next analytical artifact should be:

## **FND-ES-AG-002 : Agentic Concept Definition**

This should take the four strongest candidates first:

1. **Agentic Workflow**
2. **Agentic Value Stream**
3. **Agentic Operations**
4. **Agentic Enterprise**

and derive for each:

```text
WSF Parent / Grounding
        ↓
Enterprise Semantic Need
        ↓
Necessary Distinguishing Characteristics
        ↓
Definition
        ↓
Concept Type
        ↓
Relationships
        ↓
Boundary Conditions
        ↓
Examples
        ↓
Counterexamples
        ↓
Provenance
        ↓
Canonicality Recommendation
```

Then we can return to `AI Agent`, `Agentic Capability`, `Agentic Flow`, `Agentic Service`, `Agentic Product`, and `Agentic Culture`.

This two-step grounding is important because the live WSF baseline already gives us a strong semantic foundation: for example, Capability is explicitly grounded in `Disposition`, `Capacity`, `Ability`, Entity, Role and Context, and WSF explicitly requires specializations to preserve that meaning. ([GitHub][2])

So **we are now ready to move from "what should belong to Agentic semantics?" to "what precisely does each Agentic enterprise concept mean?"** That is the point at which the first implementation CRs can eventually become genuinely semantic rather than merely repository population.

[1]: https://github.com/World-Semantic-Foundation "World Semantic Foundation · GitHub"
[2]: https://github.com/World-Semantic-Foundation/wsf/blob/main/concepts/capability.md "wsf/concepts/capability.md at main · World-Semantic-Foundation/wsf · GitHub"
[3]: https://github.com/Enterprise-Semantics/enterprise-semantics-examples "GitHub - Enterprise-Semantics/enterprise-semantics-examples: Enterprise-Semantics reference applications: canonical enterprise model, Agentic Value Stream worked example, Agentic vs Autonomous comparative scenario. Worked examples showing enterprise-semantics in action. · GitHub"
