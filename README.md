# enterprise-semantics-governance

> Enterprise-Semantics governance: Architectural Decision Records (ADRs), Change Requests (CRs), Findings, workflow templates, lifecycle documentation, status models.

This repository is where Enterprise-Semantics is governed, not just described. The three governance artifacts are:

| Artifact | Purpose |
|----------|---------|
| **Finding** (`docs/finding/`) | Captures a hypothesis or investigation result from existing work. Lives verbatim. |
| **ADR** (`docs/adr/`) | Governs an architectural decision. Once merged, ADRs are immutable; supersession requires a new ADR. |
| **CR** (`docs/cr/`) | Implements an ADR or an independent scope change. Carries a status field. |

The **program plan** (`docs/plan/PLAN.md`) lives here and is the canonical source of truth for the org-wide roadmap.

## Status

**Skeleton (v0.0.1).** ADR-ES-001 lands here in Phase 3 per the [program plan](https://github.com/Enterprise-Semantics/enterprise-semantics-governance/blob/main/docs/plan/PLAN.md).

## Workflow

```text
Finding   : candidate hypotheses from existing work
   :
   v
ADR       : governed architectural decision (in enterprise-semantics-governance)
   :
   v
CR        : change request against the implementation (in enterprise-semantics-governance)
   :
   v
PR        : pull request against the target repository
   :
   v
CI        : conformance + schema validation
   :
   v
Release   : semantic version tag on the authority repository
```

## Templates

- [`docs/finding/0000-template.md`](docs/finding/0000-template.md)
- [`docs/adr/0000-template.md`](docs/adr/0000-template.md)
- [`docs/cr/0000-template.md`](docs/cr/0000-template.md)

## Relationship to other repositories

This repository is the meta-repository. Every other Enterprise-Semantics repository points here for governance decisions that affect it.

## Contributing

See [CONTRIBUTING.md](https://github.com/Enterprise-Semantics/.github/blob/main/CONTRIBUTING.md). All governance documents follow the dash-normalization rule (colons / semicolons only, no en-dash or em-dash).

## License

Apache License 2.0. See [LICENSE](https://github.com/Enterprise-Semantics/enterprise-semantics-governance/blob/main/LICENSE).