# Feature Specification: Spec-of-Specs Documentation

**Feature Branch**: `001-spec-of-specs-docs`

**Created**: 2026-07-21

**Status**: Draft

**Input**: Assessment handoff (slug `specs-of-specs`, verdict GO) derived from issue #3423 and discussion #2914: document *how* to break a large feature into a roadmap plus independently-specifiable sub-specs (the "spec of specs" approach), closing the gap where `docs/concepts/complex-features.md` Option 4 states *what/when* but not *how*.

## User Scenarios & Testing *(mandatory)*

### User Story 1 - Learn how to decompose a large feature (Priority: P1)

A Spec Kit user is building a feature too large for a single specify/plan/tasks/implement cycle and keeps hitting context-window degradation during implementation. They open the documentation, find the "spec of specs" guidance, and follow a concrete, ordered procedure to break the feature into a roadmap and a set of smaller sub-features they can specify one at a time.

**Why this priority**: This is the core ask of the issue and the direct fix for the documented gap. Without it, the feature delivers no value.

**Independent Test**: A reader with a large hypothetical feature can follow the page end-to-end and produce a roadmap plus at least two sub-feature entries without needing any information not on the page.

**Acceptance Scenarios**:

1. **Given** a large feature and the documentation, **When** the user follows the roadmap-decomposition steps, **Then** they produce a roadmap listing distinct, independently-specifiable sub-features.
2. **Given** a completed roadmap, **When** the user follows the per-sub-feature steps, **Then** they know how to run each sub-feature through its own specify/plan/tasks/implement cycle.
3. **Given** the documentation, **When** the user reads the worked example, **Then** they can map the abstract procedure onto a realistic feature.

---

### User Story 2 - Trace sub-specs back to the roadmap (Priority: P2)

A user running several sub-specs for one large feature needs each sub-spec to reference its place in the parent roadmap, so scope and intent are not lost across separate runs and a reader can see how the pieces fit together.

**Why this priority**: Traceability is a stated goal and prevents the sub-specs from drifting into disconnected work, but the decomposition procedure (P1) delivers value even before this convention is adopted.

**Independent Test**: Following only the linkage guidance, a user can add a parent-roadmap reference to a sub-spec and a reader can trace that sub-spec back to its roadmap entry.

**Acceptance Scenarios**:

1. **Given** a roadmap and a sub-spec, **When** the user applies the documented linkage convention, **Then** the sub-spec names the roadmap entry it fulfills.
2. **Given** several sub-specs, **When** a reader inspects any one, **Then** they can identify the parent roadmap and the sibling sub-features.

---

### User Story 3 - Discover the approach from existing docs (Priority: P3)

A user reading the existing "Handling Complex Features" page encounters the four strategies and, when they reach the decomposition option, can navigate directly to the detailed spec-of-specs guidance without the overview page becoming bloated.

**Why this priority**: Discoverability improves adoption, but the guidance is usable once it exists (P1) even if a user arrives via search rather than the overview link.

**Independent Test**: From the "Handling Complex Features" overview, a user can reach the detailed spec-of-specs content in one navigation step, and the overview remains a scannable comparison of the strategies.

**Acceptance Scenarios**:

1. **Given** the "Handling Complex Features" page, **When** the user reads the decomposition strategy, **Then** a link leads to the detailed spec-of-specs documentation.
2. **Given** the documentation navigation, **When** the user browses the table of contents, **Then** the spec-of-specs page is listed and reachable.

---

### Edge Cases

- What happens when a sub-feature is itself still too large? The guidance should acknowledge that decomposition can recurse (a sub-spec may spawn its own roadmap) and note the added overhead.
- How does the guidance handle a roadmap that changes after some sub-specs are already written? It should state how users keep sub-specs aligned as the roadmap evolves (at minimum, a convention; tooling is out of scope).
- What happens when sub-features have dependencies on each other? The guidance should address ordering and cross-references between sub-specs.
- How does a user decide between this approach and the lighter Options 1-3 already documented? The overview must keep steering readers to the simplest sufficient option.

## Requirements *(mandatory)*

### Functional Requirements

- **FR-001**: The documentation MUST provide an ordered, repeatable procedure for decomposing a large feature into a roadmap of independently-specifiable sub-features.
- **FR-002**: The documentation MUST describe a roadmap artifact convention — what it contains, and where it lives — that a user can create without additional tooling.
- **FR-003**: The documentation MUST explain how to take each roadmap entry through its own specify/plan/tasks/implement cycle.
- **FR-004**: The documentation MUST define a linkage convention by which each sub-spec references its parent roadmap entry, enabling traceability.
- **FR-005**: The documentation MUST include a concrete worked example that walks a realistic large feature through decomposition into a roadmap and sub-features.
- **FR-006**: The documentation MUST address how sub-specs stay aligned with the roadmap as it evolves, and how inter-sub-feature dependencies/ordering are handled.
- **FR-007**: The existing "Handling Complex Features" page MUST remain a scannable overview of the four strategies and MUST link to the detailed spec-of-specs guidance rather than absorbing all of its detail.
- **FR-008**: The detailed spec-of-specs guidance MUST be wired into the documentation navigation/table of contents so it is discoverable.
- **FR-009**: The documentation MUST guide readers to choose decomposition only when lighter strategies are insufficient, consistent with existing complex-features guidance.
- **FR-010**: The documentation MUST NOT introduce or imply new tooling, commands, or extensions as prerequisites; the procedure MUST be achievable with the existing Spec Kit workflow.

### Key Entities *(include if feature involves data)*

- **Roadmap**: A durable, human-authored artifact that lists the sub-features a large feature decomposes into, in enough detail to drive separate specification. Serves as the parent that sub-specs reference.
- **Sub-feature entry**: A single item in the roadmap representing one independently-specifiable slice of the larger feature, including its intent and its relationship (dependencies/ordering) to sibling entries.
- **Sub-spec**: A standard Spec Kit feature (its own spec/plan/tasks) produced for one roadmap entry, carrying a reference back to that entry.

## Success Criteria *(mandatory)*

### Measurable Outcomes

- **SC-001**: A reader can follow the documentation end-to-end and produce a roadmap plus at least two sub-feature entries without consulting any source outside the page.
- **SC-002**: Each sub-spec produced by following the guidance contains an explicit, locatable reference to its parent roadmap entry (target: 100% of sub-specs in the worked example).
- **SC-003**: A reader can navigate from the "Handling Complex Features" overview to the detailed guidance in a single step, and the overview stays a one-screen comparison of the four strategies.
- **SC-004**: The worked example covers the full path from a single large feature to a roadmap and at least two independently-runnable sub-features.
- **SC-005**: Readers can correctly decide when to use decomposition versus the lighter strategies, as evidenced by the guidance explicitly stating the decision criteria.

## Assumptions

- The primary unmet need is *guidance* (how-to), not *automation*; a documentation change is sufficient and no new tooling is required (per the assessment decision).
- The detailed guidance lives as a dedicated documentation page (Option D from the concept), with the "Handling Complex Features" page reduced to a summary + link; if the detailed content proves too thin to justify its own page, it may instead expand Option 4 inline (Option A fallback) — final placement is confirmed during planning.
- A simple, human-authored textual roadmap with per-entry references is sufficient for traceability at the scale users operate; no machine-enforced consistency is expected.
- The documentation follows the existing docs conventions (Markdown under `docs/`, wired via the existing table of contents/navigation).
- A brief pointer to the community "Spec Roadmap" extension may be included for users wanting automation, but only if that extension is judged mature enough to reference; it is not a dependency of this feature.
- Audience is existing Spec Kit users who have already used the basic specify/plan/tasks/implement flow.
