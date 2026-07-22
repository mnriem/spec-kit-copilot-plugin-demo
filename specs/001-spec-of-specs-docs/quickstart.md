# Quickstart / Validation Guide: Spec-of-Specs Documentation

This feature is documentation. "Validation" means confirming the pages exist, render, link correctly, and satisfy the spec's success criteria. No code build or tests are involved.

## Prerequisites

- Repo checked out on branch `001-spec-of-specs-docs`.
- (Optional) DocFX installed locally to build the site, or rely on the docs CI build.

## Files expected after implementation

- NEW: `docs/concepts/spec-of-specs.md`
- EDIT: `docs/concepts/complex-features.md` (Option 4 trimmed + linked)
- EDIT: `docs/toc.yml` (Concepts group gains a "Spec of Specs" entry)

## Validation scenarios

### 1. Page exists with required structure (FR-001…FR-006, FR-010)
- Open `docs/concepts/spec-of-specs.md`.
- Confirm the sections listed in `contracts/docs-structure.md` are present and ordered.
- Confirm no new CLI/tooling/extension is presented as a prerequisite.
- **Expected**: all required sections present; procedure achievable with the existing specify/plan/tasks/implement flow.

### 2. Worked example is end-to-end (FR-005, SC-001, SC-004)
- Read the worked example.
- **Expected**: one large feature is decomposed into a roadmap plus at least two independently-runnable sub-feature entries, each with intent, scope, dependency info, and a roadmap id.

### 3. Traceability convention is demonstrated (FR-004, SC-002)
- Inspect the worked example's roadmap entries and sample sub-spec header.
- **Expected**: each sub-spec references its parent roadmap entry, and each roadmap entry links back to its sub-spec — bidirectional.

### 4. Overview stays scannable and links out (FR-007, FR-009, SC-003, SC-005)
- Open `docs/concepts/complex-features.md`.
- **Expected**: Option 4 is a short summary that links to `spec-of-specs.md`; the four-option comparison table is intact; the guidance still steers readers to the simplest sufficient option.

### 5. Navigation wiring (FR-008, SC-003 scenario 2)
- Open `docs/toc.yml`.
- **Expected**: a "Spec of Specs" entry under the Concepts group with `href: concepts/spec-of-specs.md`.

### 6. Links resolve (contract acceptance)
- Grep for the new page reference: `grep -rn "spec-of-specs" docs/`.
- (Optional) Build docs with DocFX and confirm no broken-link warnings for the added/edited files.
- **Expected**: the summary→detail link and the TOC href both resolve to the new file.

## Sign-off

Validation passes when scenarios 1–6 all meet their expected outcomes and the `checklists/requirements.md` items remain satisfied.
