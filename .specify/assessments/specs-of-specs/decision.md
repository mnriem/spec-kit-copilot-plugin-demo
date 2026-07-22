# Decision: Specs-of-specs feature breakdown

- **Slug**: specs-of-specs
- **Decided**: 2026-07-21
- **Verdict**: go
- **Artifacts reviewed**: intake.md? yes | research.md? yes | problem.md yes | concept.md? yes

## Scorecard

| Criterion | Rating | Justification |
|-----------|--------|---------------|
| Problem validity | strong | Real, cited gap: `complex-features.md` Option 4 names the "spec of specs" approach but omits the *how*; raised in discussion #2914 and issue #3423. |
| Evidence strength | adequate | Demand and the doc gap are cited (discussion + issue + in-repo doc); breadth of demand is the main assumption, but the core problem is well-supported. |
| Value vs. inaction | adequate | Without it, users keep hitting context degradation on large features and invent inconsistent ad-hoc breakdowns; documented advice stays unactionable. Value is real though bounded (least-recommended, highest-overhead path). |
| Feasibility / appetite | strong | Recommended Option D (dedicated docs page) is `small` appetite, no tooling to maintain, fully within a docs-scoped change. |
| Strategic fit | adequate | Fills a gap in existing official docs and complements Options 1–3; aligns with Spec Kit's artifact-driven, staged philosophy. |
| Risk posture | strong | Main risks (content drift, over-scoping the page, format bikeshedding) are identified with clear mitigations; docs-only change is low-blast-radius and easily revised. |

## Verdict & Rationale

**Go.** The problem is valid and cited, and there is a credible `small`-appetite concept (Option D — a dedicated "spec of specs" page, with Option A inline-expansion as fallback) that directly satisfies the Documentation-tagged request. Evidence strength is `adequate` (not weak/unknown) — the doc gap and its origin are concretely sourced, with only demand-breadth as an assumption that does not block a low-cost docs fix. No criterion is `weak`. This clears the go bar: problem validity `strong`, evidence `adequate`, and a shaped, recommended option. Hand off to `/speckit-specify` to produce the actual documentation change; heavier options (B: new extension; C: endorse community extension) remain deferred pending evidence of automation demand.

## If needs-clarification

- N/A (verdict is go).

## If go — Handoff to `/speckit-specify`

- **Problem**: Spec Kit docs recommend decomposing large features into "smaller specs" (the "spec of specs" approach) but never document *how*, leaving users to invent ad-hoc, inconsistent breakdowns.
- **Chosen approach**: Option D — add a dedicated `spec of specs` documentation page (e.g. `docs/concepts/spec-of-specs.md`) that keeps `complex-features.md` as the scannable overview (Option 4 → short summary + link) and holds the full procedure: the roadmap decomposition pass, a roadmap artifact convention and location, per-sub-feature specify/plan/tasks/implement cycles, a parent↔sub-spec linkage convention, and a worked example. Fallback to Option A (inline expansion of Option 4) if the content is too thin for its own page. Wire the new page into `toc.yml`/nav.
- **In scope / out of scope**:
  - *In*: documentation only — the how-to procedure, roadmap artifact convention, linkage convention, worked example, and nav wiring; optional brief pointer to the community "Spec Roadmap" extension for users wanting automation.
  - *Out*: building automation/tooling or a new extension; external tracker (Jira) integration; a programmatic roadmap↔sub-spec consistency engine; prescribing feature architecture; single-cycle context fixes (already covered by Options 1–3).
- **Success metrics**: a user can follow the page end-to-end to produce a roadmap + ≥2 sub-specs unaided; each sub-spec references its parent roadmap entry; reduction in large-feature context-degradation questions post-publication.
- **Carried-forward open questions**:
  - Final page placement: `docs/concepts/spec-of-specs.md` vs a `docs/guides/` page (resolve by drafting and judging length — informs D-vs-A).
  - Exact roadmap artifact format/location and the per-entry reference convention sub-specs use.
  - How sub-specs stay consistent with the roadmap as it evolves (convention vs. future tooling).
  - Whether to include the pointer to the community "Spec Roadmap" extension (contingent on vetting its maturity).
  - Target audience framing (new users vs. experienced multi-spec teams).
