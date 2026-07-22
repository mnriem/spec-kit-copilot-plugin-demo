# Concept: Specs-of-specs feature breakdown

- **Slug**: specs-of-specs
- **Created**: 2026-07-21
- **Recommended option**: Option D — Dedicated "spec of specs" page (fallback: Option A — inline expansion)

## Options

### Option A — Documentation expansion ("how", not just "what")
- **Sketch**: Expand `docs/concepts/complex-features.md` Option 4 (and/or add a dedicated concept/guide page) with a concrete, repeatable procedure: how to run a first "roadmap" pass that decomposes a large feature into a numbered list of independently-specifiable sub-features; a simple convention for a roadmap artifact and where it lives; and how to run each sub-feature through its own specify/plan/tasks/implement cycle while referencing the parent roadmap. Includes a worked example and a lightweight linkage convention (each sub-spec names its parent roadmap entry).
- **Appetite**: small (days).
- **Trade-offs**: Wins — directly satisfies the issue (tagged Documentation), lowest overhead, no new tooling to maintain, ships fast, immediately actionable. Sacrifices — no automation; consistency between roadmap and sub-specs is enforced by convention/discipline, not tooling.
- **Rabbit holes**: Over-engineering the roadmap format; drifting into prescribing feature architecture; trying to document every agent's sub-agent behavior instead of a general procedure.

### Option B — New "roadmap/breakdown" extension
- **Sketch**: Build a Spec Kit extension adding commands to generate a durable roadmap from a large feature and scaffold sub-spec directories from it, with a maintained parent↔child link and a review step that checks sub-specs against the roadmap before/after implementation.
- **Appetite**: medium–large (weeks+).
- **Trade-offs**: Wins — automates decomposition and consistency, the strongest answer to the roadmap-evolution problem. Sacrifices — significant build + ongoing maintenance; **substantial overlap with the existing community "Spec Roadmap" extension**; heavy investment in what the docs call the least-recommended, highest-overhead option.
- **Rabbit holes**: Roadmap-to-sub-spec consistency engine; cross-run state management; duplicating/competing with community work; scope creep into project-tracker territory.

### Option C — Endorse/adopt the community "Spec Roadmap" extension + thin docs
- **Sketch**: Point users to the existing community "Spec Roadmap" extension for the automated roadmap-governance path, and add a short docs section that frames when to use decomposition and links out to it, plus the manual fallback from Option A.
- **Appetite**: small (days), contingent on the community extension's quality/maturity.
- **Trade-offs**: Wins — avoids duplication, leverages existing work, low effort. Sacrifices — depends on a v0.1.0, 0-download, discovery-only (not default-installable) third-party extension; ties official guidance to an external maintainer; may not be production-ready.
- **Rabbit holes**: Vetting/QA of the third-party extension; catalog/installability constraints; support expectations if it's presented as endorsed.

### Option D — Dedicated page for the "spec of specs" approach
- **Sketch**: Keep `complex-features.md` as the concise overview (its four-option table stays as-is, with Option 4 as a short summary), and move the detailed *how* into a new standalone page — e.g. `docs/concepts/spec-of-specs.md` (or a guide under `docs/guides/`) — linked from Option 4. That page carries the full procedure: the roadmap pass, the roadmap artifact convention and location, per-sub-feature specify/plan/tasks/implement cycles, the parent↔sub-spec linkage convention, and a worked example. Same content as Option A, but as its own first-class document rather than an expanded section.
- **Appetite**: small (days).
- **Trade-offs**: Wins — keeps `complex-features.md` scannable (it's a comparison of four strategies, not a deep-dive on one); gives the approach a stable, linkable home and room to grow (diagrams, examples) without bloating the overview; better discoverability via `toc.yml`/nav. Sacrifices — one more page to keep in sync with the overview; a reader must follow a link to get the detail; slightly more docs plumbing (toc/nav/index entries).
- **Rabbit holes**: Duplicating content between the overview and the new page (drift risk); deciding concepts/ vs guides/ placement; over-scoping the new page into a general "large features" tutorial.

## Recommendation

**Option D (dedicated page), falling back to Option A if a full page proves thin.** Option D is the same low-overhead, `small`-appetite documentation fix as A, but it respects the shape of `complex-features.md` — a four-way *comparison* page that should stay scannable rather than swell around one option. A standalone `spec-of-specs` page gives the procedure a stable, linkable home with room for a worked example and (later) diagrams, and improves discoverability through the docs nav. If the detailed content turns out too short to justify its own page, collapse it back into an expanded Option 4 section (Option A). Either way, an optional pointer to the community "Spec Roadmap" extension (Option C) covers users wanting automation. Reserve Option B only if broad demand for automation emerges later.

<details>
<summary>Prior recommendation (superseded)</summary>

**Option A (documentation expansion), optionally referencing Option C.** The issue is explicitly tagged *Documentation*, and the core gap is that Option 4 already names the "spec of specs" approach but omits the *how*. A concrete procedure + worked example + a lightweight roadmap/linkage convention fully satisfies the stated goals (repeatable breakdown, traceability, closing the how-gap) at `small` appetite with no maintenance burden. A brief pointer to the community "Spec Roadmap" extension can cover users who want automation, without committing the project to build or maintain competing tooling. Reserve Option B only if evidence of broad demand for automation emerges later.

</details>

## Out of Scope (for the recommended option)

- Automated roadmap generation or sub-spec scaffolding tooling.
- External project-tracker (e.g. Jira) integration.
- Prescribing implementation/architecture for any resulting feature.
- Single-cycle context-window fixes (already covered by Options 1–3 in `complex-features.md`).
- A programmatic roadmap↔sub-spec consistency engine.

## Assumptions to Validate

- A documented procedure + convention is sufficient for users to break down large features without tooling.
- The primary unmet need is *guidance* (how-to), not *automation*.
- The community "Spec Roadmap" extension is mature/trustworthy enough to reference (needed before adding Option C's pointer).
- Whether `complex-features.md` should retain the detailed content (Option A) or hand it to a dedicated page (Option D) — resolve by drafting the procedure and judging its length.
- A simple textual roadmap artifact with per-entry references is enough for traceability at the scale users operate.
