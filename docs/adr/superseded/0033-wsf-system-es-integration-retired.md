# ADR-ES-029 ; WSF System Dependency and Enterprise-Semantics Integration

Status: Proposed
Decision Type: Foundational Dependency Integration
Authority: Enterprise-Semantics
Semantic Version Target: v2.7.0
Scope: Enterprise-Semantics
Depends On: WSF-ADR-ES-027, ADR-ES-022, ADR-ES-025
Implementation: CR-ES-039
Supersedes: prior ADR-ES-027 short-cut implementation (the prior ADR-ES-027 is preserved in `docs/adr/0031-system-semantic-grounding.md` for historical reference but is no longer canonical; this alignment ADR is the canonical authority)

## 1. Decision

Enterprise-Semantics shall adopt WSF System as the authoritative foundational semantic for System.

Enterprise-Semantics shall not independently redefine System.

## 2. Semantic Authority

```
WSF
  |
  v
System
  |
  v
Enterprise-Semantics
  |
  v
Agentic System
```

WSF owns the foundational meaning. Enterprise-Semantics owns the enterprise-specific Agentic System specialization.

## 3. Dependency Gate

ES-025 implementation is blocked unless WSF System = Canonical + Validated. A local Enterprise-Semantics System definition cannot satisfy this dependency.

## 4. Agentic System Boundary

Agentic System specializes WSF System by adding material agentic behavior:

```
WSF System
     |
     +- specializes
            v
      Agentic System
```

The specialization must not alter the foundational meaning of System.

## 5. Agentic System Distinctions

Enterprise-Semantics must preserve:

- Agentic System is NOT Agent
- Agentic System is NOT Agentic Workflow
- Agentic System is NOT Agentic Operations
- Agentic System is NOT Agentic Service
- Agentic System is NOT Agentic Organization
- Agentic System is NOT Agentic Enterprise

## 6. Autonomous System

This ADR does not establish Autonomous System. Its potential future relationship to System remains subject to ES-022 specialization gate + mechanical symmetry prohibition.

## 7. Decision Outcome

WSF System becomes the authoritative dependency for ES-025 Agentic System.



## Author

Emmanuel A. Otchere (cardinal author rule, 2026-09-24)

## Cross-Program Traceability Note

Per user directive message 1553249359905165444 + WSF-ES-ALIGN-01, the WSF-side filings are WSF-ADR-ES-026 + WSF-CR-ES-026 (Culture) and WSF-ADR-ES-027 + WSF-CR-ES-027 (System). The ES-side chain adopts ES-ADR-028 + ES-CR-038 (Culture alignment) and ES-ADR-029 + ES-CR-039 (System alignment) to avoid slot collision with the prior ES-026/ES-027 foundational concept filings, which are now superseded by this alignment chain per CR-ES-026-section-2 + CR-ES-027-section-2 corrective guidance.
