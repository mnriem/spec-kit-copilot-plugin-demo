# Idea Research: Specs-of-specs feature breakdown

- **Slug**: specs-of-specs
- **Created**: 2026-07-21
- **Evidence confidence (overall)**: medium

## Users & Demand

- The idea originates from a real user question in discussion #2914 ("Dealing with fairly complex features"), where the author reports LLMs hallucinating and losing track of plan/tasks mid-implementation on large features, and explicitly asks whether a "spec of specs" breakdown is the right strategy. — [source: https://github.com/github/spec-kit/discussions/2914] (confidence: high, cited)
- Issue #3423 (enhancement, by @PeterDaumQS) converts that discussion into a concrete documentation/extension request, indicating demand beyond a single one-off question. — [source: https://github.com/github/spec-kit/issues/3423] (confidence: high, cited)
- Breadth of demand (how many users hit this) is not quantified. — [ASSUMPTION] (confidence: low)

## Prior Art

- **In-repo docs already cover this partially.** `docs/concepts/complex-features.md` presents four approaches to large features; **Option 4 "Decompose the Feature Into Smaller Specs"** already names and describes the "spec of specs" approach: each sub-feature gets its own `spec.md`/`plan.md`/`tasks.md` and runs its own cycle. — [source: docs/concepts/complex-features.md] (confidence: high, cited)
- **Gap in that prior art:** the doc describes *that* you decompose and *when* to reach for it, but not the *how* — no roadmap artifact, no step-by-step procedure for generating sub-specs from a parent, and no linkage/consistency mechanism. This matches exactly what #3423 asks for. — [source: docs/concepts/complex-features.md + issue #3423] (confidence: high, cited)
- **Community extension "Spec Roadmap" (v0.1.0, srobroek)** already tackles adjacent ground: "capture a durable spec roadmap after the constitution, then review specs against it before and after implementation." It is discovery-only (not installable from the community catalog) and early-stage (v0.1.0, 0 downloads/stars). — [source: https://github.com/srobroek/speckit-roadmap, via `specify extension search roadmap`] (confidence: high, cited)
- **Community "Jira Integration" (mbachorik)** creates Epics/Stories from spec-kit specs and task breakdowns — adjacent (hierarchy from specs) but external-tracker-focused, not a native roadmap→sub-spec flow. — [source: https://github.com/mbachorik/spec-kit-jira] (confidence: medium, cited)

## Market & Context

- Feature decomposition / hierarchical planning is a common practice in SDD-style and PRD-driven tools; the "cost of doing nothing" is that users continue to hit context-window degradation on large features and either give up on Spec Kit for big work or invent ad-hoc breakdowns. — [ASSUMPTION] (confidence: medium)
- Spec Kit already ships an assessment pipeline (this `assess` extension) and a workflow system, showing the project favors staged, artifact-driven flows — a "roadmap → sub-specs" flow would fit that pattern. — [source: repo `.specify/` + installed `assess` extension] (confidence: medium, cited)

## Data & Constraints

- Root cause per both the discussion and docs is **context window exhaustion** during `/speckit.implement`; any solution should reduce per-run context, not just add process. — [source: docs/concepts/complex-features.md, discussion #2914] (confidence: high, cited)
- The component tagged on the issue is **Documentation**, suggesting the minimum viable deliverable is docs, with an extension as an optional escalation. — [source: issue #3423] (confidence: high, cited)
- No compliance/legal/platform constraints identified. — [ASSUMPTION] (confidence: low)

## Evidence Against the Idea

- **A partial solution already exists** in `complex-features.md` (Option 4). The delta may be small enough that a documentation expansion — not a new extension — fully satisfies the request, making a heavier "extension" build hard to justify. — [source: docs/concepts/complex-features.md] (confidence: high, cited)
- **Overlap with an existing community extension** ("Spec Roadmap") risks duplicating effort; the better path might be to endorse/adopt/improve that rather than build parallel tooling. — [source: https://github.com/srobroek/speckit-roadmap] (confidence: medium, cited)
- The docs themselves warn decomposition "adds the most overhead, so reserve it for features that are too large to handle any other way" — over-investing in tooling for the least-recommended option may be low ROI. — [source: docs/concepts/complex-features.md] (confidence: medium, cited)
- Demand is currently evidenced by one discussion + one issue; not yet shown to be widespread. — [ASSUMPTION] (confidence: low)

## Gaps & Open Questions

- [NEEDS CLARIFICATION: Is the desired deliverable documentation-only (expand Option 4 with a concrete roadmap→sub-spec procedure) or a new extension/command that automates it?]
- [NEEDS CLARIFICATION: What roadmap artifact format and location should be used, and how should each sub-spec reference the parent roadmap?]
- [NEEDS CLARIFICATION: How should sub-specs stay consistent with the roadmap as it evolves (the exact gap the "Spec Roadmap" community extension targets)?]
- [NEEDS CLARIFICATION: Should this coordinate with / build on the existing community "Spec Roadmap" extension rather than duplicate it?]

## Sources

- https://github.com/github/spec-kit/issues/3423 (host: github.com, policy: allowlisted)
- https://github.com/github/spec-kit/discussions/2914 (host: github.com, policy: allowlisted)
- docs/concepts/complex-features.md (host: local repo, policy: read-only)
- https://github.com/srobroek/speckit-roadmap (host: github.com, policy: allowlisted — via extension catalog metadata)
- https://github.com/mbachorik/spec-kit-jira (host: github.com, policy: allowlisted — via extension catalog metadata)
