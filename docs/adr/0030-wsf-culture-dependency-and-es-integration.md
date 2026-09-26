# ES-ADR-026 ; WSF Culture Dependency and Enterprise-Semantics Integration

Status: Proposed
Authority: Enterprise-Semantics
Depends On: WSF-ADR-ES-026 ; Culture Semantic Grounding
Related: ES-ADR-023, ES-ADR-024, ES-FOUND-001
Target Semantic Version: 2.1.0
Decision Type: Foundational Dependency Integration
Scope: Enterprise-Semantics
Implements: ES-CR-026

## Cross-Program Traceability Note

This is the canonical Enterprise-Semantics integration ADR for the WSF Culture foundation. It supersedes the prior short-cut ES-026 foundational filing at slot 0030, which created a competing local foundational Culture definition. Per WSF-ES-ALIGN-01, Enterprise-Semantics SHALL NOT independently redefine Culture ; WSF owns foundational meaning.

## 1. Decision

Enterprise-Semantics SHALL adopt WSF Culture as the authoritative foundational semantic for Culture.

Enterprise-Semantics SHALL NOT define an independent or competing foundational Culture concept.

The Enterprise-Semantics concepts:

- Agentic Culture
- Autonomous Culture

SHALL specialize the authoritative WSF Culture concept rather than a locally defined Enterprise-Semantics Culture concept.

The semantic authority chain SHALL therefore be:

```
WSF
+- Culture
   |
   +- Agentic Culture
   |
   +- Autonomous Culture
```

Enterprise-Semantics remains responsible for the enterprise-specific specialization semantics, while WSF remains authoritative for the foundational meaning of Culture.

## 2. Context

ES-ADR-023 established Agentic Culture as an Enterprise-Semantics specialization of Culture.

ES-ADR-024 established Autonomous Culture as an Enterprise-Semantics specialization of Culture.

Subsequent foundation reconnaissance identified that Culture is sufficiently general to belong at the WSF semantic layer and that independently defining Culture within Enterprise-Semantics would create competing semantic authorities.

WSF therefore provides the foundational semantic, while Enterprise-Semantics provides enterprise-specific specializations.

## 3. Authoritative Foundation

The authoritative WSF definition is:

Culture is a socially situated pattern of shared meanings, values, norms, practices, and expectations that influences how a collective interprets, evaluates, and conducts behavior within a context.

Enterprise-Semantics SHALL consume this definition and SHALL NOT alter its foundational meaning.

## 4. Dependency Rule

The following dependency gate SHALL apply:

```
WSF Culture
    |
    v
Enterprise-Semantics Culture Dependency
    |
    v
Agentic Culture
Autonomous Culture
```

Agentic Culture and Autonomous Culture SHALL NOT become Canonical until WSF Culture = Canonical.

The dependency is semantic, not merely documentary.

## 5. Enterprise-Semantics Interpretation

Within Enterprise-Semantics, Culture provides the foundational semantic basis for organizational patterns involving:

- shared meaning
- values
- norms
- practices
- expectations
- interpretation
- behavior
- contextual adaptation

Enterprise-Semantics may constrain and specialize these characteristics when defining enterprise-specific cultural concepts.

It SHALL NOT redefine Culture to mean organizational culture exclusively.

## 6. Specialization Relationships

The following semantic relationships are established:

```
Culture
 +- specializes -> Agentic Culture
 +- specializes -> Autonomous Culture
```

More precisely:

```
Agentic Culture
    specializes -> WSF Culture
Autonomous Culture
    specializes -> WSF Culture
```

The specializations remain independent dimensions.

Therefore:

```
Culture
+- conventional
+- Agentic Culture
+- Autonomous Culture
+- Agentic + Autonomous Culture
```

Agentic Culture SHALL NOT imply Autonomous Culture. Autonomous Culture SHALL NOT imply Agentic Culture.

## 7. Enterprise-Semantics Boundaries

Enterprise-Semantics Culture specialization SHALL NOT collapse Culture into:

- Organization
- Organizational Identity
- Collective
- Context
- Value
- Norm
- Rule
- Policy
- Governance
- Behavior

These concepts may participate in cultural relationships without becoming synonymous with Culture.

## 8. Authority and Provenance

The authority chain SHALL be recorded as:

```
WSF
  |
  v
WSF Culture
  |
  v
Enterprise-Semantics dependency
  |
  v
Agentic Culture / Autonomous Culture
```

The provenance chain SHALL preserve:

```
provenance:
  source:
    - ES-FOUND-001
    - WSF-ADR-ES-026
  decision:
    - ES-ADR-026
```

Implementation provenance is recorded by ES-CR-026.

## 9. Consequences

Positive:

- Establishes a single semantic authority for Culture.
- Prevents semantic duplication between WSF and Enterprise-Semantics.
- Allows Agentic Culture and Autonomous Culture to remain enterprise-specific.
- Preserves the WSF -> Enterprise-Semantics specialization boundary.
- Enables future non-enterprise cultural specializations without semantic conflict.

Negative:

- Enterprise-Semantics becomes dependent on WSF Culture lifecycle and governance.
- Changes to foundational WSF Culture semantics may require downstream impact assessment.
- Enterprise-Semantics cannot independently redefine foundational Culture semantics.

## 10. Non-Goals

This ADR does not:

- redefine WSF Culture
- create a second Culture concept
- establish Agentic Culture as a WSF concept
- establish Autonomous Culture as a WSF concept
- define organizational culture as equivalent to Culture
- modify WSF governance
- introduce new autonomous or agentic dimensions

## 11. Acceptance Conditions

This ADR is ready for implementation when:

1. WSF-ADR-ES-026 is accepted.
2. WSF Culture is Canonical.
3. Enterprise-Semantics registry supports authoritative external concepts.
4. ES-023 and ES-024 are updated to reference WSF Culture.
5. No competing local foundational Culture concept remains.
6. Mapping and provenance are established.
7. Conformance tests validate the dependency.

## WSF Cross-Reference

Filed on github.com/World-Semantic-Foundation/wsf-governance:

- ADR-WSF-33 ; Culture Semantic Grounding (ES Integration) ; Status: Proposed
  - Subject-namespace alias: WSF-ADR-CULTURE-001 (per LOCKED-PICKS v9 section 313-318)
  - PR #12 merged 2026-09-26
- CR-WSF-33 ; Culture Implementation in WSF (ES Integration)
  - Subject-namespace alias: WSF-CR-CULTURE-001

## Author

Emmanuel A. Otchere (cardinal author rule, 2026-09-24)
