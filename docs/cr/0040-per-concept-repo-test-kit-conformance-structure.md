# CR-ES-030 ; Per-Concept Repository + Test-Kit + Conformance Section Implementation

Status: Accepted
Date: 2026-09-26
Implements: ES-ADR-030
Scope: Enterprise-Semantics (org-wide)

## 1. Intent

Execute the structural change per ES-ADR-030: create per-concept repositories, bundle per-concept test kits with manifests, and establish the CI-generated conformance section.

## 2. Per-Concept Repository Creation (DP1 = B)

For each pilot concept:

1. Create repo `concept-<slug>` in the Enterprise-Semantics org (public, main branch)
2. Seed with the concept YAML at repo root as `concept.yaml` (from the concept's implementation branch or main)
3. Add README.md: concept name, ES tranche reference, base concept, status, governance pointers
4. Commit with cardinal author stamp

Naming: `concept-<slug>` ; slug = concept kebab-case name (agentic-culture, autonomous-culture, agentic-system, autonomous-system, agentic-ecosystem).

## 3. Per-Concept Test Kits (DP2 = B)

In `enterprise-semantics-test-probe`:

1. Create `tests/kits/<slug>/` per pilot concept
2. Author `kit.yaml` manifest per concept:

```yaml
id: ES:KIT:<slug>
concept: ES:CONCEPT:<slug>
base_concept: <WSF or ES parent>
status: established
version: <semantic version>
coverage:
  positive: <count>
  negative: <count>
  integrity: <count>
boundary_assertions_covered: [<list>]
provenance:
  decision: [ES-ADR-NNN]
  implementation: [ES-CR-NNN]
```

3. Tests already authored for the concept are referenced or co-located in the kit directory

## 4. CI-Generated Conformance Section (DP3 = C)

In `enterprise-semantics-test-probe`:

1. Author `conformance/generate_conformance.py`: reads all `tests/kits/*/kit.yaml` manifests + validator output, renders the conformance section markdown
2. Author `.github/workflows/conformance.yml`: nightly (and on kit change) job that runs the generator and commits the output to `enterprise-semantics-docs/conformance/`
3. Initial run commits the first generated conformance section: `conformance/README.md` (org summary) + `conformance/<slug>.md` (per-concept pages)

## 5. Migration Safety

- Central concept copies in `enterprise-semantics/concepts/` are NOT deleted in the pilot wave; they remain until backfill completes and the validator is updated to org-wide scanning
- Validator behavior is unchanged in the pilot wave
- Rollback: concept repos are additive; deletion of a pilot repo + no-op on central copies restores prior state

## 6. Acceptance Criteria

1. 5 concept repos exist with concept.yaml + README
2. 5 kit manifests exist in test-probe
3. `generate_conformance.py` runs clean and produces the conformance section
4. Conformance section committed to docs repo
5. D-004 clean ; cardinal author stamp on all commits

## Promotion Metadata

- promotion_date: 2026-09-26
- promotion_trigger: all 6 acceptance criteria met at full scale (39 concepts, 5 waves)
- prior_status: Approved for Implementation
- promotion_authority: Emmanuel A. Otchere (cardinal author rule, 2026-09-24)

## Author

Emmanuel A. Otchere (cardinal author rule, 2026-09-24)
