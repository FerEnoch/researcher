---
name: researcher
description: "Trigger: investigar rubro, benchmark, research pre-dev, brief de producto, discovery técnico. Corre el kit researcher (Lite, Fase 1, Fase 2) en cualquier proyecto."
license: Apache-2.0
metadata:
  author: "ferenoch"
  version: "1.0"
---

## Activation Contract

Activate when the user wants pre-dev research: explore a domain, benchmark
competitors, find inspiration, write a product brief, or prepare technical
discovery before building. Ask which mode if unclear; default to Lite.

## Hard Rules

- Never write production code, backlog, or estimates. End at brief/discovery.
- Never version run outputs. Write them to `<project>/output/<slug>/` only.
- Models are parameters: use the ones the user declares per run.
- Gaps become `UNRESOLVED`, never confident prose.
- Lite never runs adversarial review. Say so in the brief.

## Decision Gates

| User need | Mode | Protocol |
|---|---|---|
| Explore idea, inspiration, go/no-go | Lite | `protocols/00-lite/LITE_PROTOCOL.md` |
| Committed idea, brief for architecture | Phase 1 | `protocols/01-benchmarking/MASTER_PROTOCOL.md` |
| Validated brief, pre-ADR groundwork | Phase 2 | `protocols/02-tech-discovery/MASTER_PROTOCOL.md` |
| Lite done, blockers need adjudication | Escalate | Phase 1 reusing `lite/` artifacts |

## Execution Steps

1. Locate the kit: `$RESEARCHER_KIT`, else ask once and remember it.
   Fallback: clone the published repo URL.
2. Read the mode protocol file and follow it verbatim (topes, ledger
   rules, stop conditions, fixed brief sections).
3. Create `<project>/output/<slug>/run.yaml` from the kit template.
4. Write artifacts under `<project>/output/<slug>/{lite,brief,discovery}/`.
5. Fill `lite_measured` (or phase status) and report `UNRESOLVED` plus
   the escalate/do-not-build recommendation.

## Output Contract

Return: mode used, artifacts written (paths), ledger highlights
(regulatory + MVP claims only in Lite), UNRESOLVED list, and whether
Phase 1 is recommended.

## References

- Kit protocols: `<kit>/protocols/00-lite/`, `<kit>/protocols/01-benchmarking/`, `<kit>/protocols/02-tech-discovery/`
- End-to-end flow: `<kit>/docs/PIPELINE.md`
- Run templates: `<kit>/templates/run-lite.md`, `run-research.md`, `run-discovery.md`, `run.yaml`
