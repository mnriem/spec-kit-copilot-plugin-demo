# Docs Structure Contract: Spec-of-Specs Documentation

The "interface" this feature exposes is the documentation surface: the new page, the edited overview, and the navigation entry. This contract defines what must be true of each so the change is complete and consistent.

## New page: `docs/concepts/spec-of-specs.md`

Required sections (in order):

1. **Title + intro** — names the "spec of specs" approach and when to reach for it (only when lighter strategies in complex-features are insufficient — FR-009).
2. **The roadmap pass** — ordered procedure to decompose a large feature into a roadmap of independently-specifiable sub-features (FR-001).
3. **The roadmap artifact** — what the roadmap file contains and where it lives; a copy-pasteable Markdown template (FR-002).
4. **Specifying each sub-feature** — how to run each roadmap entry through its own specify/plan/tasks/implement cycle (FR-003).
5. **Linking sub-specs to the roadmap** — the bidirectional reference convention (FR-004).
6. **Keeping the roadmap and sub-specs in sync** — evolution rule + inter-sub-feature dependencies/ordering + recursion caveat (FR-006, Edge Cases).
7. **Worked example** — a realistic large feature decomposed into a roadmap + ≥2 sub-feature entries, showing the linkage (FR-005, SC-004).
8. **(Optional) For automation** — brief, clearly-optional pointer to the community "Spec Roadmap" extension (non-essential).

Constraints:
- Markdown only; relative links; no new tooling implied (FR-010).
- Uses DocFX-compatible Markdown consistent with sibling concept pages.

## Edited page: `docs/concepts/complex-features.md`

- Option 4 ("Decompose the Feature Into Smaller Specs") is trimmed to a short summary (what it is + when to use it) and **links to** `spec-of-specs.md` for the detailed procedure (FR-007).
- The four-option "Which Approach to Choose" table remains intact and scannable (SC-003).
- No other option's content is altered.

## Edited nav: `docs/toc.yml`

- Add an entry under the **Concepts** group, adjacent to "Handling Complex Features":
  ```yaml
    - name: Spec of Specs
      href: concepts/spec-of-specs.md
  ```
- Entry resolves to the new file so the page is reachable from site navigation (FR-008, SC-003 acceptance scenario 2).

## Acceptance (contract-level)

- Navigating from complex-features Option 4 to the detailed page is a single link hop (SC-003).
- The new page appears in the TOC under Concepts.
- All internal links resolve (DocFX build has no broken-link errors for the added/edited files).
- Every FR (FR-001…FR-010) maps to at least one section above.
