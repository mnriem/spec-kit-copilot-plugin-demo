# Spec Kit Walkthrough

With the Spec Kit Copilot plugin installed, this session went from a raw GitHub
issue to shipped documentation. Each step below shows the exact command entered and
what it did.

## Assessment (using the `assess` extension)

1. **`Initialize the project as a Spec Kit project using Copilot and skills mode`**
   Scaffolds `.specify/` and installs the spec-kit commands as Copilot Agent Skills
   (`.github/skills/speckit-*/SKILL.md`).

2. **`/skills reload`**
   Loads the newly scaffolded skills into the running session.

3. **`Add the assess extension`**
   Installs the Idea Assessment Pipeline — 5 assess skills (intake, research, define,
   shape, decide).

4. **`/skills reload`**
   Picks up the newly added assess skills.

5. **`Now do an intake using https://github.com/github/spec-kit/issues/3423`**
   Captures the raw idea from the issue into `.specify/assessments/specs-of-specs/intake.md`.

6. **`Continue`** → research
   Gathers evidence for and against the idea into `research.md`.

7. **`Continue`** → define
   Frames the problem — affected users, goals, non-goals, success metrics — in `problem.md`.

8. **`Continue`** → shape
   Sketches 2–3 solution options with appetite and trade-offs in `concept.md`.

9. **`What about D a separate page describing option 4 in more detail?`**
   Adds Option D (a dedicated docs page) and makes it the recommended option.

10. **`Continue`** → decide
    Scores the idea and records the verdict in `decision.md`: **go**, handing off to SDD.

## Delivery (using Spec-Driven Development)

11. **`Continue`** → specify
    Converts the go verdict into `specs/001-spec-of-specs-docs/spec.md` plus a spec
    quality checklist.

12. **`Yes`** → plan
    Produces `plan.md` and design artifacts (`research.md`, `data-model.md`,
    `contracts/`, `quickstart.md`).

13. **`Yes`** → tasks
    Generates the dependency-ordered `tasks.md` (14 tasks, grouped by user story).

14. **`Do the implementation`** → implement
    Executes the tasks: adds `docs/concepts/spec-of-specs.md`, trims Option 4 in
    `complex-features.md` to a summary + link, and wires the new page into `docs/toc.yml`.
