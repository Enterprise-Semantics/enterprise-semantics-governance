# Recon-ES-004 ; System Foundational Dependency Recon ; 2026-09-25

## Author

Emmanuel A. Otchere (cardinal author rule, 2026-09-24)

## Purpose

Per user directive (Culture-System_Resolution.md) and ADR-ES-022
section 9 + section 10 dependency gate, perform foundational
dependency recon for the proposed System concept before drafting
ADR-ES-027.

## Central Question (per user directive)

What distinguishes a System from an Entity, Organization, Service,
Resource, or Workflow?

The definition must accommodate: business systems, information
systems, technical systems, socio-technical systems, operational
systems, distributed systems without collapsing System into IT
system.

## Cross-Checked Concepts (per user directive)

| Concept | Semantic scope | Overlap risk | Disambiguation |
|---|---|---|---|
| Entity | Foundational semantic kind | Low ; Entity is the broadest semantic category | System is a specialization of Entity (organized-whole semantics) |
| Organization | Entity organized to coordinate people + roles + capabilities | Medium ; Organization can be a type of System | Organization has people ; System does not require people. System has organized elements ; Organization has organized members + roles |
| Enterprise | Organizational or organizational-like entity for cumulative priority realization | Low ; Enterprise is cumulative + priority-realization | Enterprise concerns cumulative value realization ; System concerns organized-element behavior |
| Capability | Ability to realize an outcome | Low ; Capability is functional, System is structural-behavioral | Capability is what a System can do ; System is what realizes the capability |
| Service | Unit of value delivery to a consumer | Medium ; Service is delivery-oriented, System is structural | Service concerns value delivery ; System concerns element organization + behavior |
| Resource | Asset or input to activity | Low ; Resource is consumed, System is organized | Resource is what is used ; System is what uses them |
| Process | Sequence of activities producing an outcome | Medium ; Process is sequential activity, System is structural | Process is what happens inside a System ; System is the containing structure |
| Workflow | Coordinated execution of work | Medium ; Workflow is execution-oriented, System is structural | Workflow is how work flows ; System is the arranged whole |
| Agent | Entity capable of interpreting delegated intent | Medium ; Agent is one type of element that may participate in a System | Agent is an element with intent ; System is the organized whole in which Agents participate |
| Outcome | Result of an action or process | Low ; Outcome is effect, System is the producer | Outcome is what is produced ; System is what produces it |
| Context | Setting or environment | Low ; Context is environmental, System is structural | Context is the environment ; System operates within Context |

## Semantic Decision per Recon

System is NOT redundant with any established concept. System
performs distinctive semantic work:

1. **Element organization** : multiple interacting parts
2. **Behavioral coherence** : elements produce coherent system-level behavior
3. **Boundary** : the system has a defined boundary (what is inside vs outside)
4. **Purpose orientation** : elements are organized toward intended functions + outcomes
5. **Contextual operation** : operates within a defined context

These dimensions are NOT fully covered by:
- Entity (which is too broad)
- Organization (which requires people + roles)
- Service (which is delivery-oriented)
- Resource (which is consumable)
- Process / Workflow (which concern activity sequences)

## Recommended Canonical Definition (per user directive)

A System is an organized whole of interacting elements whose
relationships and behavior enable the realization of one or more
intended functions, purposes, or outcomes within a defined context
and boundary.

## Constraints (per user directive)

- System SHALL remain sufficiently general to accommodate business, information, technical, socio-technical, operational, and distributed systems.
- System SHALL NOT collapse into IT system.
- System precedes Agentic System (ES-025) as the canonical base.
- Autonomous System is NOT established by ADR-ES-027 (per ES-022 specialization gate, mechanical symmetry prohibition).

## Disposition

PROCEED with ADR-ES-027 (System Semantic Grounding, v2.5.0).

## Reconciliation with prior tranches

- ES-025 (Agentic System, BLOCKED on System canonical): dependency resolution now possible
- Autonomous System remains deferred per ADR-ES-025 section 13 (no mechanical symmetry)

## Author

Emmanuel A. Otchere (cardinal author rule, 2026-09-24)
