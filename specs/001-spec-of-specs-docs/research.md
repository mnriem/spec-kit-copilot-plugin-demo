# Phase 0 Research: Spec-of-Specs Documentation

All spec Assumptions and open questions are resolved below. No blocking `NEEDS CLARIFICATION` remain.

## Decision 1 — Page placement: dedicated page vs. inline expansion

- **Decision**: Create a dedicated `docs/concepts/spec-of-specs.md` page (concept-D), and reduce `complex-features.md` Option 4 to a short summary that links to it.
- **Rationale**: `complex-features.md` is a four-strategy *comparison* page (it ends with a "Which Approach to Choose" table). Inlining the full how-to would bloat that comparison and bury the other three options. A dedicated page gives the procedure a stable, linkable home with room for a worked example, and matches the assessment's recommended Option D.
- **Alternatives considered**: (A) Expand Option 4 inline — rejected as primary because it bloats the overview; retained as a documented fallback if the new page proves too thin. (B) New extension/tooling — out of scope (FR-010). (C) Point solely at the community "Spec Roadmap" extension — rejected as the primary deliverable; may be referenced as an optional pointer only.

## Decision 2 — Section under Concepts vs. Guides

- **Decision**: Place under **Concepts** (`docs/concepts/`), adjacent to `complex-features.md` and `spec-persistence.md`.
- **Rationale**: The content is a conceptual approach/methodology (how to think about decomposition), consistent with its sibling `complex-features.md`. Keeping them co-located makes the summary→detail link natural and keeps the TOC grouping coherent.
- **Alternatives considered**: `docs/guides/` (used for `evolving-specs.md`, `monorepo.md`) — rejected because those are task/workflow guides listed under "Development"; the spec-of-specs page is a concept that pairs with complex-features.

## Decision 3 — Roadmap artifact convention

- **Decision**: A human-authored Markdown roadmap file kept alongside the feature's specs, e.g. `specs/<feature>/roadmap.md` (or a top-level `ROADMAP.md` for the epic), listing numbered sub-features each with: id/slug, one-line intent, scope boundary, dependencies/order, and status.
- **Rationale**: Uses only plain Markdown and the existing `specs/` layout — no tooling (FR-002, FR-010). Numbered entries give each sub-spec a stable reference target (supports FR-004 linkage). Status column lets users track progress across separate runs.
- **Alternatives considered**: A machine-parsed schema or a dedicated command to generate/maintain it — rejected as out of scope (automation deferred). A tracker (Jira) — out of scope.

## Decision 4 — Parent↔sub-spec linkage convention

- **Decision**: Each sub-feature's `spec.md` names its parent roadmap and entry in the **Input/summary line** (e.g. "Parent roadmap: `specs/<epic>/roadmap.md` → entry R3"), and the roadmap entry links back to the sub-feature directory once created.
- **Rationale**: Bidirectional, greppable references satisfy traceability (FR-004, SC-002) with zero tooling. Placing the reference in the existing spec header means no new spec-template section is required.
- **Alternatives considered**: Front-matter metadata keys — rejected to avoid implying a parsed schema/tooling. A separate index file — redundant with the roadmap itself.

## Decision 5 — Roadmap evolution & inter-sub-feature dependencies

- **Decision**: Document that the roadmap is a living artifact: when scope shifts, update the roadmap first, then reconcile affected sub-specs; record dependencies/ordering in each roadmap entry and cross-reference dependent sub-specs. Note that a sub-feature that is still too large can recurse into its own roadmap (with an overhead caveat).
- **Rationale**: Directly answers spec Edge Cases and FR-006 using convention/discipline rather than enforcement, consistent with the no-tooling constraint.
- **Alternatives considered**: A consistency-checking command — out of scope; may be mentioned as future work only.

## Decision 6 — Community "Spec Roadmap" extension pointer

- **Decision**: Include at most a brief, clearly-optional "For automation" pointer to the community "Spec Roadmap" extension, framed as third-party and not required.
- **Rationale**: Serves users wanting automation without committing the project to build or endorse tooling. Kept optional because the extension is early-stage (v0.1.0, discovery-only) per the assessment research.
- **Alternatives considered**: Omit entirely — acceptable; the pointer is non-essential and can be dropped if maturity is in doubt.

## Decision 7 — Validation approach

- **Decision**: Validate by manual review against the spec's Success Criteria and a DocFX link/toc sanity check (page renders, TOC entry present, summary→detail link resolves).
- **Rationale**: Docs-only change; no automated test harness exists for prose. Matches Constitution Principle II (no behavior change → review-based validation).
- **Alternatives considered**: Adding a docs linter/test — rejected as new tooling outside scope.
