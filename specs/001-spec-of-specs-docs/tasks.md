---
description: "Task list for Spec-of-Specs Documentation"
---

# Tasks: Spec-of-Specs Documentation

**Input**: Design documents from `/specs/001-spec-of-specs-docs/`

**Prerequisites**: plan.md, spec.md, research.md, data-model.md, contracts/docs-structure.md, quickstart.md

**Tests**: Not applicable — documentation-only feature. "Validation" is manual review per `quickstart.md` (no automated test tasks).

**Organization**: Tasks are grouped by user story (P1→P3) from spec.md so each story is an independently reviewable increment.

## Format: `[ID] [P?] [Story] Description`

- **[P]**: Can run in parallel (different files, no dependencies)
- **[Story]**: Which user story this task belongs to (US1, US2, US3)
- Exact file paths are included in each task.

## Path Conventions

Documentation-only change under `docs/`. Affected files:
- NEW `docs/concepts/spec-of-specs.md`
- EDIT `docs/concepts/complex-features.md`
- EDIT `docs/toc.yml`

---

## Phase 1: Setup (Shared Infrastructure)

**Purpose**: Establish the new page skeleton so all user stories write into a consistent structure.

- [X] T001 Create `docs/concepts/spec-of-specs.md` with the DocFX-compatible section skeleton (headings only, in the order defined in `specs/001-spec-of-specs-docs/contracts/docs-structure.md`: Intro/when-to-use, The roadmap pass, The roadmap artifact, Specifying each sub-feature, Linking sub-specs to the roadmap, Keeping in sync, Worked example, optional For automation).

---

## Phase 2: Foundational (Blocking Prerequisites)

**Purpose**: Author the intro that frames when to use the approach — every later section builds on this framing. MUST complete before the story phases.

- [X] T002 In `docs/concepts/spec-of-specs.md`, write the Title + intro section: define the "spec of specs" approach and state it is the highest-overhead option, to be used only when the lighter strategies in `complex-features.md` (Options 1–3) are insufficient (satisfies FR-009; sets up US1).

**Checkpoint**: Page exists with skeleton + framing intro. User story phases can now proceed.

---

## Phase 3: User Story 1 — Learn how to decompose a large feature (Priority: P1) 🎯 MVP

**Goal**: A reader can follow an ordered procedure to break a large feature into a roadmap and independently-specifiable sub-features, run each through its own cycle, and see a worked example.

**Independent Test**: A reader with a large hypothetical feature follows the page and produces a roadmap plus ≥2 sub-feature entries using only page content (SC-001, SC-004).

- [X] T003 [US1] In `docs/concepts/spec-of-specs.md` "The roadmap pass" section, write the ordered, repeatable decomposition procedure (identify slices → define boundaries → order by dependency → record as roadmap entries), per `research.md` Decision 3 and FR-001.
- [X] T004 [US1] In `docs/concepts/spec-of-specs.md` "The roadmap artifact" section, document the roadmap file convention and location (`specs/<epic>/roadmap.md` or top-level `ROADMAP.md`) and include a copy-pasteable Markdown roadmap template with the fields from `data-model.md` (id, name, intent, scope-boundary, dependencies, status, sub-spec-link) — FR-002.
- [X] T005 [US1] In `docs/concepts/spec-of-specs.md` "Specifying each sub-feature" section, explain running each roadmap entry through its own `/speckit-specify` → `/speckit-plan` → `/speckit-tasks` → `/speckit-implement` cycle without new tooling (FR-003, FR-010).
- [X] T006 [US1] In `docs/concepts/spec-of-specs.md` "Worked example" section, decompose one realistic large feature into a roadmap with ≥2 sub-feature entries, each showing intent, scope, dependency info, and a roadmap id (FR-005, SC-004).

**Checkpoint**: US1 delivers the core how-to and a worked example — this is the MVP and independently shippable.

---

## Phase 4: User Story 2 — Trace sub-specs back to the roadmap (Priority: P2)

**Goal**: Each sub-spec references its parent roadmap entry (and vice-versa) so scope/intent survive across separate runs.

**Independent Test**: Using only the linkage guidance, a user adds a parent-roadmap reference to a sub-spec and a reader can trace it back (SC-002).

- [X] T007 [US2] In `docs/concepts/spec-of-specs.md` "Linking sub-specs to the roadmap" section, document the bidirectional linkage convention from `research.md` Decision 4 / `data-model.md`: sub-spec header names `parent roadmap → entry id`; roadmap entry's `sub-spec-link` points back (FR-004).
- [X] T008 [US2] In `docs/concepts/spec-of-specs.md` "Keeping the roadmap and sub-specs in sync" section, document the evolution rule (update roadmap first, then reconcile sub-specs), inter-sub-feature dependencies/ordering, and the recursion caveat for still-too-large slices (FR-006, spec Edge Cases).
- [X] T009 [US2] In the "Worked example" section of `docs/concepts/spec-of-specs.md`, extend the example to show the concrete bidirectional reference (a sample sub-spec header line + the roadmap entry linking back), demonstrating SC-002.

**Checkpoint**: US1 + US2 give a complete, traceable methodology.

---

## Phase 5: User Story 3 — Discover the approach from existing docs (Priority: P3)

**Goal**: Readers reach the new page from the complex-features overview and site navigation, while the overview stays scannable.

**Independent Test**: From `complex-features.md`, a reader reaches the detailed page in one hop, and the overview remains a scannable four-strategy comparison (SC-003).

- [X] T010 [P] [US3] In `docs/concepts/complex-features.md`, trim "Option 4: Decompose the Feature Into Smaller Specs" to a short summary (what it is + when to use) and add a link to `spec-of-specs.md` for the detailed procedure; keep the "Which Approach to Choose" table intact (FR-007, SC-003, SC-005).
- [X] T011 [P] [US3] In `docs/toc.yml`, add a "Spec of Specs" entry (`href: concepts/spec-of-specs.md`) under the Concepts group, adjacent to "Handling Complex Features" (FR-008).

**Checkpoint**: The page is discoverable via both the overview link and site nav.

---

## Phase 6: Polish & Cross-Cutting Concerns

**Purpose**: Verify the whole change against the spec and docs conventions.

- [X] T012 [P] Run the "For automation" decision: optionally add a brief, clearly-optional pointer to the community "Spec Roadmap" extension in `docs/concepts/spec-of-specs.md`, or omit it (per `research.md` Decision 6) — non-blocking.
- [X] T013 Validate all internal links resolve: `grep -rn "spec-of-specs" docs/` and confirm the complex-features link and toc href point to the new file (contract acceptance, quickstart scenario 6).
- [X] T014 Review `docs/concepts/spec-of-specs.md` against `specs/001-spec-of-specs-docs/quickstart.md` scenarios 1–5 and the spec Success Criteria (SC-001…SC-005); confirm no new tooling is implied (FR-010) and prose matches sibling concept pages' style.

---

## Dependencies & Execution Order

- **Setup (Phase 1)** → **Foundational (Phase 2)** must complete first (they create the file and its framing).
- **US1 (Phase 3)** depends on Phase 2. It is the MVP.
- **US2 (Phase 4)** builds on US1 content (extends the same page and worked example) — do after US1.
- **US3 (Phase 5)** only edits `complex-features.md` and `toc.yml`; T010 and T011 are independent of each other and of US1/US2 content, so they may run in parallel and even before US1 finishes (the link target file already exists after T001). Listed last by priority.
- **Polish (Phase 6)**: T013/T014 run after all content exists; T012 is optional.

## Parallel Opportunities

- T010 and T011 are marked **[P]** — different files (`complex-features.md`, `toc.yml`), no shared edits.
- T012 is **[P]** (independent optional edit).
- Within US1/US2, tasks edit the same file (`spec-of-specs.md`) in different sections; they are safe to do sequentially to avoid edit conflicts (not marked [P]).

## Implementation Strategy

- **MVP = Phase 1 + 2 + US1 (T001–T006)**: a complete, usable spec-of-specs how-to with a worked example. Shippable on its own.
- **Increment 2 = US2 (T007–T009)**: adds traceability + evolution guidance.
- **Increment 3 = US3 (T010–T011)**: wires discoverability.
- **Finish = Polish (T012–T014)**: link check + quality review.

## Task Summary

- **Total tasks**: 14
- **US1 (P1)**: 4 tasks (T003–T006) — MVP
- **US2 (P2)**: 3 tasks (T007–T009)
- **US3 (P3)**: 2 tasks (T010–T011)
- **Setup/Foundational**: 2 tasks (T001–T002)
- **Polish**: 3 tasks (T012–T014)
