# ADR-ES-028 ; WSF Culture Dependency and Enterprise-Semantics Integration

Status: Proposed
Decision Type: Foundational Dependency Integration
Authority: Enterprise-Semantics
Semantic Version Target: v2.6.0
Scope: Enterprise-Semantics
Depends On: WSF-ADR-ES-026, ADR-ES-022, ADR-ES-023, ADR-ES-024
Implementation: CR-ES-038
Supersedes: prior ADR-ES-026 short-cut implementation (the prior ADR-ES-026 is preserved in `docs/adr/0030-culture-semantic-grounding.md` for historical reference but is no longer canonical; this alignment ADR is the canonical authority)

## 1. Decision

Enterprise-Semantics shall adopt WSF Culture as the authoritative semantic foundation for Culture.

Enterprise-Semantics shall not independently redefine or canonicalize a competing foundational Culture concept.

## 2. Semantic Authority

```
WSF
  |
  v
Culture
  |
  v
Enterprise-Semantics
  |
  v
Agentic Culture
Autonomous Culture
```

WSF owns the foundational meaning. Enterprise-Semantics owns the enterprise-specific specialization semantics.

## 3. Enterprise-Semantics Consequence

Existing concepts:

- Agentic Culture
- Autonomous Culture

must identify WSF Culture as their foundational dependency. Their definitions may specialize Culture but must not redefine it.

## 4. Dependency Gate

ES-023 and ES-024 implementation is blocked unless WSF Culture = Canonical.

The Enterprise-Semantics repository must not satisfy this dependency through a local placeholder definition.

## 5. Boundary

Enterprise-Semantics may define:

- Agentic Culture
- Autonomous Culture
- enterprise cultural specialization
- enterprise-specific relationships
- enterprise examples
- enterprise conformance

It must not redefine:

- the meaning of Culture
- the world-semantic scope of Culture
- foundational Culture relationships

## 6. Decision Outcome

WSF Culture becomes the authoritative dependency for Enterprise-Semantics Culture-related specializations.



## Author

Emmanuel A. Otchere (cardinal author rule, 2026-09-24)

## Cross-Program Traceability Note

Per user directive message 1553249359905165444 + WSF-ES-ALIGN-01, the WSF-side filings are WSF-ADR-ES-026 + WSF-CR-ES-026 (Culture) and WSF-ADR-ES-027 + WSF-CR-ES-027 (System). The ES-side chain adopts ES-ADR-028 + ES-CR-038 (Culture alignment) and ES-ADR-029 + ES-CR-039 (System alignment) to avoid slot collision with the prior ES-026/ES-027 foundational concept filings, which are now superseded by this alignment chain per CR-ES-026-section-2 + CR-ES-027-section-2 corrective guidance.
