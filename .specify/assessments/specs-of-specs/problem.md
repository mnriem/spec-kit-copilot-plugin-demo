# Problem Definition: Specs-of-specs feature breakdown

- **Slug**: specs-of-specs
- **Created**: 2026-07-21
- **Inputs used**: intake.md? yes | research.md? yes | user input only? no

## Problem Statement

When a feature is too large to run through a single specify/plan/tasks/implement cycle, Spec Kit users hit context-window degradation during `/speckit.implement` (hallucination, plan/task drift). The docs recommend decomposing into "smaller specs" but never explain *how* to do it, so users are left to invent ad-hoc breakdown procedures with no guidance on structuring a roadmap or generating consistent sub-specs from it.

## Affected Users & Stakeholders

- **Users**: Spec Kit practitioners building large/complex features — they experience mid-implementation model degradation and lack a documented method to break the work into independently-specifiable sub-features. — [source: discussion #2914, issue #3423]
- **Users**: Teams coordinating multi-spec efforts — they need each sub-spec to trace back to a parent roadmap and stay consistent as it evolves. — [source: issue #3423 use cases; partially [NEEDS CLARIFICATION: how many teams operate at this scale]]
- **Stakeholders**: Spec Kit maintainers / docs owners — decide whether the fix is a documentation expansion or a new extension, and own consistency with existing `complex-features.md` guidance. — [source: issue #3423 tagged "Documentation"]
- **Stakeholders**: Community extension authors (e.g. "Spec Roadmap" by srobroek) — an overlapping roadmap-governance extension already exists and could be endorsed or duplicated. — [source: research.md]

## Goals

- Give users a clear, repeatable procedure to break a large feature into a roadmap plus independently-implementable sub-specs, each runnable without exhausting the context window.
- Make each sub-spec traceable to the parent roadmap so scope and intent are not lost across runs.
- Close the documented gap: existing `complex-features.md` Option 4 states *what/when* to decompose but not *how*.

## Non-Goals

- Solving general context-window degradation for features that fit in a single cycle (already covered by Options 1–3 in `complex-features.md`).
- Building deep external project-tracker integration (e.g. Jira epic/story sync) — out of scope for this problem.
- Prescribing a specific implementation/architecture for any resulting feature — this is about the breakdown method, not the features themselves.
- [NEEDS CLARIFICATION: whether replacing/adopting the community "Spec Roadmap" extension is in or out of scope.]

## Success Metrics

- A user can follow the guidance end-to-end to produce a roadmap and ≥2 sub-specs without additional external instruction. (baseline: not currently possible — no documented procedure)
- Reduction in "context degradation on large features" reports/questions after publication. (baseline: unknown; ≥1 discussion + 1 issue to date)
- Each generated sub-spec contains an explicit reference back to the parent roadmap. (baseline: 0 — no linkage convention exists)
- [NEEDS CLARIFICATION: is adoption/download volume a target if delivered as an extension, or is doc-page engagement the metric?]

## Cost of Inaction

Users continue hitting model degradation on large features and either abandon Spec Kit for big work or invent inconsistent ad-hoc breakdowns. The documented "spec of specs" advice remains unactionable, the discussion/issue stay open, and the roadmap-consistency problem is left to a single early-stage (v0.1.0) community extension that is not installable from the default catalog.

## Open Questions

- [NEEDS CLARIFICATION: Deliverable form — documentation-only expansion of Option 4, or a new extension/command that automates roadmap → sub-spec generation?]
- [NEEDS CLARIFICATION: Roadmap artifact — what format and location, and how does each sub-spec reference it?]
- [NEEDS CLARIFICATION: Consistency — how do sub-specs stay aligned with the roadmap as it changes over time?]
- [NEEDS CLARIFICATION: Relationship to the existing community "Spec Roadmap" extension — build on it, endorse it, or independent?]
- [NEEDS CLARIFICATION: Target audience — new users learning decomposition, or experienced teams already running multi-spec projects?]
