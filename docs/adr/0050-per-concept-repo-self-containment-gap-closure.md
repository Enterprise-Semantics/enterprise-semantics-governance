# ADR-ES-050 ; Per-Concept Repo Self-Containment Gap Closure

Status: Accepted
Date: 2026-09-30
Deciders: eaojnr
Decision Type: Structural repository content amendment (amendment to ES-ADR-049 §2.1)
Scope: Enterprise-Semantics (org-wide, all 48 concept repositories)
Implements: CR-ES-050
Amends: ES-ADR-049 §2.1 (Self-Contained Concept Repository Layout)
Supersedes: None

## 1. Context

ES-ADR-049 established that each `concept-<slug>` repository must be self-contained with all canonical resources mirrored from the central repositories (concepts, mappings, visuals, examples, tests, documentation).

The initial landing on 2026-09-30 was incomplete. A re-audit on 2026-09-30 confirmed:

- 11 of 48 repositories are fully self-contained (all 11 core artefact types present).
- 37 of 48 repositories are missing `kit/positive-NN.yaml` and `kit/negative-NN.yaml` test files. The previous mirror copied only the `kit.yaml` manifest, not the test files themselves.
- 22 of 48 repositories lack any `mappings/` content.
- 28 of 48 repositories lack any `visuals/` content.
- 47 of 48 repositories lack any `examples/` content.

This gap is structural: ES-ADR-049 promised self-containment, but the landing did not deliver it for the majority of repositories. The release cut cannot proceed until the gap is closed.

## 2. Decision

ES-ADR-049 §2.1 is amended to require that the per-concept-repo self-containment wave be completed in 4 additional slices before release cut.

### 2.1 Slice A ; Test File Mirror (CR-ES-050-a)

Author `kit/positive-NN.yaml` and `kit/negative-NN.yaml` (NN in 01..05) for all 48 concept repositories. Source: canonical `enterprise-semantics-test-probe/tests/<slug>/`.

### 2.2 Slice B ; Mapping Authoring (CR-ES-050-b)

For each of the 22 concepts lacking `mappings/` content, author canonical mappings:

- `mappings/wsf.yaml` (mandatory, if material)
- `mappings/opendea.yaml` (where applicable)
- `mappings/dea-catalogs.yaml` (where applicable)

Each mapping MUST declare `mapping_type` from the canonical vocabulary (`specialization`, `correspondence`, `instantiation`, `profile`) and cite the source authority.

### 2.3 Slice C ; Visual Authoring (CR-ES-050-c)

For each of the 28 concepts lacking `visuals/` content, author at minimum `visuals/<slug>-boundary.puml`. PlantUML diagram showing the concept's boundary, relationships, and cardinality.

### 2.4 Slice D ; Example Authoring (CR-ES-050-d)

For each of the 47 concepts lacking `examples/` content, author `examples/<slug>-reference.yaml`. Example demonstrates the concept's boundary assertions and declares conformance level.

## 3. Wave Order

1. Slice A lands first (test files are foundational to conformance).
2. Slices B, C, D land in parallel after Slice A.

## 4. Acceptance Criteria

This decision is implemented when:

- All 48 repositories contain the 11 core artefact types (or have material absence acknowledged).
- All new YAML files parse cleanly.
- All new PlantUML files compile without error.
- Zero forbidden glyphs (D-004 sweep clean).
- Cardinal author rule preserved on all commits.

## 5. Consequences

### Positive

- Self-containment promise of ES-ADR-049 is fulfilled.
- Release cut can proceed with structural integrity.
- Each per-concept repo can be reviewed and adopted independently.

### Negative

- 4 additional PRs across central repos.
- ~250 file additions across 48 per-concept repos.
- ~2-3 hours of agent execution time.

### Neutral

- The "examples" slice (D) is non-critical for self-containment. If time is constrained, examples can be deferred without violating the core promise.

## 6. Author

Emmanuel A. Otchere <emmanuel@otchere.com> (cardinal author rule, 2026-09-24).
