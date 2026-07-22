# spec-kit Copilot Plugin Demo

This project demonstrates an end-to-end AI-assisted development workflow using [spec-kit](https://github.com/github/spec-kit) with the Spec Kit plugin for GitHub Copilot CLI. Starting from a raw GitHub issue, an idea was assessed, specified, planned, and shipped entirely through structured agents — first the Idea Assessment Pipeline (the `assess` extension), then Spec-Driven Development. The steps below document exactly what was entered — you can follow the same process to take your own ideas from issue to implementation.

> **Note on the workflow:** The feature was not driven by an elaborate formal specification. It began as a raw GitHub issue, was assessed through the intake → research → define → shape → decide pipeline, and only then handed off to Spec-Driven Development. Each command below is the exact prompt entered into Copilot Chat, as you will see.

## Acknowledgements

This project is built on top of **[spec-kit](https://github.com/github/spec-kit)**, an open-source toolkit for Spec-Driven Development created and maintained by **[GitHub](https://github.com/github)**. All credit for the toolkit, its agents, and its extensions belongs to the spec-kit contributors. Please visit the original repository to learn more, contribute, or show your appreciation.

---

## Prerequisites

- [GitHub Copilot CLI](https://docs.github.com/en/copilot/concepts/agents/copilot-cli/about-copilot-cli)
- The Spec Kit `specify` CLI on your `PATH`:

  ```bash
  uv tool install specify-cli      # or: pipx install specify-cli
  specify --version
  ```

- A GitHub repository to work in

### Install the Spec Kit Copilot plugin

This demo is driven by the [Spec Kit Copilot plugin](https://github.com/github/spec-kit-copilot), which exposes the `specify` CLI to the Copilot agent as skills. Register the marketplace, then install the plugin:

```bash
copilot plugin marketplace add github/spec-kit-copilot
copilot plugin install spec-kit-copilot@spec-kit-marketplace
```

Verify it loaded:

```bash
copilot plugin list
# or, inside an interactive session:
/skills list
```

See the [plugin README](https://github.com/github/spec-kit-copilot#installation) for local development installs and troubleshooting.

---

## Assessment — from issue to a go/no-go decision

The `assess` extension adds the Idea Assessment Pipeline: five skills (intake, research, define, shape, decide) that turn a raw idea into a scored decision before any code is written.

### Step 1 — Initialize the project

```
Initialize the project as a Spec Kit project using Copilot and skills mode
```

This scaffolds `.specify/` and installs the spec-kit commands as Copilot Agent Skills (`.github/skills/speckit-*/SKILL.md`).

### Step 2 — Load the new skills

```
/skills reload
```

Loads the newly scaffolded skills into the running session.

### Step 3 — Add the assess extension

```
Add the assess extension
```

Installs the Idea Assessment Pipeline — the five assess skills (intake, research, define, shape, decide).

### Step 4 — Reload again

```
/skills reload
```

Picks up the newly added assess skills.

### Step 5 — Intake the idea

```
Now do an intake using https://github.com/github/spec-kit/issues/3423
```

Captures the raw idea from the issue into `.specify/assessments/specs-of-specs/intake.md`.

### Step 6 — Research

```
Continue
```

Gathers evidence for and against the idea into `research.md`.

### Step 7 — Define the problem

```
Continue
```

Frames the problem — affected users, goals, non-goals, success metrics — in `problem.md`.

### Step 8 — Shape the solution

```
Continue
```

Sketches 2–3 solution options with appetite and trade-offs in `concept.md`.

### Step 9 — Refine an option

```
What about D a separate page describing option 4 in more detail?
```

Adds Option D (a dedicated docs page) and makes it the recommended option.

### Step 10 — Decide

```
Continue
```

Scores the idea and records the verdict in `decision.md`: **go**, handing off to Spec-Driven Development.

---

## Delivery — Spec-Driven Development

With a **go** decision in hand, the standard spec-kit agents took the idea from specification to a shipped change.

### Step 11 — Specify

```
Continue
```

Converts the go verdict into `specs/001-spec-of-specs-docs/spec.md` plus a spec quality checklist.

### Step 12 — Plan

```
Yes
```

Produces `plan.md` and design artifacts (`research.md`, `data-model.md`, `contracts/`, `quickstart.md`).

### Step 13 — Generate the task list

```
Yes
```

Generates the dependency-ordered `tasks.md` (14 tasks, grouped by user story).

### Step 14 — Implement

```
Do the implementation
```

Executes the tasks: adds `docs/concepts/spec-of-specs.md`, trims Option 4 in `complex-features.md` to a summary plus link, and wires the new page into `docs/toc.yml`.

---

## Result

A raw GitHub issue turned into a shipped change — assessed, specified, planned, and implemented through structured agent workflows without manual scaffolding. In this run the idea happened to resolve to a documentation change (a new concept page wired into the docs table of contents), but the point of the demo is the workflow itself: the Spec Kit plugin for GitHub Copilot CLI carrying any idea from issue to implementation.
