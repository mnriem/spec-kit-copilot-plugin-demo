# Phase 1 Data Model: Spec-of-Specs Documentation

This feature is documentation, not code. The "data model" is the structure of the conventions the guidance defines. These are prose/Markdown conventions, not schemas or database entities.

## Entity: Roadmap

A durable, human-authored Markdown artifact that decomposes one large feature (an "epic") into independently-specifiable sub-features.

- **Location**: `specs/<epic-slug>/roadmap.md` (feature-scoped) or a top-level `ROADMAP.md` for a cross-cutting epic.
- **Fields**:
  - `title` — the large feature/epic name.
  - `overview` — 1–2 sentences of the epic's intent and why it is being decomposed.
  - `entries[]` — ordered list of Sub-feature entries (see below).
  - `status legend` — how entry status values are interpreted (e.g. planned / in-progress / done).
- **Validation / rules**:
  - Every entry has a unique id within the roadmap.
  - Entries are ordered so dependencies precede dependents (or dependencies are explicit).
  - The roadmap is updated before reconciling sub-specs when scope changes (evolution rule).
- **Relationships**: parent of many Sub-feature entries; referenced by many Sub-specs.

## Entity: Sub-feature entry

One row/item in the roadmap representing a single independently-specifiable slice of the epic.

- **Fields**:
  - `id` — stable short identifier (e.g. `R1`, `R2`) used as the linkage target.
  - `name` — short title of the sub-feature.
  - `intent` — one line: what this slice delivers.
  - `scope-boundary` — what is in/out for this slice, so it stays independently specifiable.
  - `dependencies` — ids of other entries this one depends on (or "none").
  - `status` — planned | in-progress | done.
  - `sub-spec-link` — path to the sub-feature's spec directory once created (empty until then).
- **Validation / rules**:
  - `id` is unique and immutable once referenced by a sub-spec.
  - `dependencies` reference existing entry ids only.
  - A slice too large to specify in one cycle SHOULD be split (may recurse into its own roadmap).
- **Relationships**: belongs to one Roadmap; fulfilled by at most one Sub-spec.

## Entity: Sub-spec

A standard Spec Kit feature (its own `spec.md` / `plan.md` / `tasks.md`) produced for one roadmap entry.

- **Fields** (additions to the normal spec, by convention only):
  - `parent-roadmap-ref` — in the spec's Input/summary line: parent roadmap path + entry id (e.g. "Parent roadmap: `specs/<epic>/roadmap.md` → R3").
- **Validation / rules**:
  - Exactly one `parent-roadmap-ref` naming a valid roadmap entry id (traceability — FR-004, SC-002).
  - The referenced roadmap entry's `sub-spec-link` points back to this sub-spec (bidirectional).
- **Relationships**: fulfills exactly one Sub-feature entry; sibling of other Sub-specs under the same Roadmap.

## Linkage summary (traceability)

```text
Roadmap (epic)
 ├─ entry R1 ──▶ specs/<epic>-part-1/ (Sub-spec, header: "→ R1")
 ├─ entry R2 ──▶ specs/<epic>-part-2/ (Sub-spec, header: "→ R2")
 └─ entry R3 ──▶ (not yet specified)
```

Bidirectional, greppable references — no tooling required. This structure is what the new page documents and what the worked example instantiates.
