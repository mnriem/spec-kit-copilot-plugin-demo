# Implementation Plan: Spec-of-Specs Documentation

**Branch**: `001-spec-of-specs-docs` | **Date**: 2026-07-21 | **Spec**: [spec.md](./spec.md)

**Input**: Feature specification from `/specs/001-spec-of-specs-docs/spec.md`

## Summary

Close the documented gap where `docs/concepts/complex-features.md` Option 4 names the "spec of specs" decomposition approach but never explains *how* to do it. Deliver a new dedicated concepts page, `docs/concepts/spec-of-specs.md`, that gives an ordered procedure for decomposing a large feature into a durable roadmap plus independently-specifiable sub-features, a roadmap artifact convention, a parent↔sub-spec linkage convention, guidance on roadmap evolution and inter-sub-feature dependencies, and a worked example. Trim Option 4 in `complex-features.md` to a short summary that links to the new page, and wire the new page into `docs/toc.yml`. Documentation-only; no CLI, tooling, or extension changes.

## Technical Context

**Language/Version**: Markdown (DocFX-rendered docs site); no code changes

**Primary Dependencies**: Existing `docs/` site — DocFX (`docs/docfx.json`), navigation via `docs/toc.yml`

**Storage**: Static files under `docs/`

**Testing**: Manual doc review against the spec quality checklist and success criteria; DocFX build sanity (links resolve, toc entry renders). No automated unit tests apply.

**Target Platform**: Rendered documentation site (github.github.io/spec-kit) + in-repo Markdown

**Project Type**: Documentation change to an existing single-repo CLI project

**Performance Goals**: N/A (static docs)

**Constraints**: Follow existing docs conventions (Markdown, relative links, `toc.yml` wiring); no new tooling introduced; overview page must stay scannable

**Scale/Scope**: One new page (~1 screen-plus with a worked example), one edited page (Option 4 trimmed + linked), one `toc.yml` entry

## Constitution Check

*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

The constitution is oriented at the `specify-cli` Python codebase; most principles (I code architecture, II test-backed change, III CLI UX, IV offline performance, V dependencies) govern code and are **not triggered** by a docs-only change. Relevant, satisfied gates:

- **Principle II (docs discipline)**: This change adds no behavior and touches no code paths, so no automated tests are mandated; validation is doc review + DocFX build. PASS.
- **Principle III (docs under the site) / V (safe, idempotent file ops)**: The change only adds one Markdown file and edits two existing files (`complex-features.md`, `toc.yml`); it creates no code, no dependencies, and is reversible. PASS.
- **Principle IV (offline-first)**: No network dependency introduced; the guidance relies solely on the existing offline Spec Kit workflow (FR-010). PASS.

No violations. Complexity Tracking not required.

## Project Structure

### Documentation (this feature)

```text
specs/001-spec-of-specs-docs/
├── plan.md              # This file
├── spec.md              # Feature spec
├── research.md          # Phase 0 output
├── data-model.md        # Phase 1 output (roadmap artifact structure)
├── quickstart.md        # Phase 1 output (validation guide)
├── contracts/
│   └── docs-structure.md # Phase 1 output (page/nav/linkage contract)
└── checklists/
    └── requirements.md  # Spec quality checklist
```

### Source Code (repository root)

This feature changes documentation only. Affected paths:

```text
docs/
├── concepts/
│   ├── complex-features.md   # EDIT: trim Option 4 to summary + link to new page
│   └── spec-of-specs.md      # NEW: detailed spec-of-specs guidance
└── toc.yml                   # EDIT: add "Spec of Specs" entry under Concepts
```

**Structure Decision**: No `src/` or `tests/` changes. All work lands under `docs/` following the existing DocFX conventions: a new concepts page, a trimmed overview page, and a `toc.yml` navigation entry.

## Complexity Tracking

No constitution violations; section intentionally empty.
