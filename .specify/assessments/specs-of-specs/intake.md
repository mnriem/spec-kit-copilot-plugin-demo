# Idea Intake: Specs-of-specs feature breakdown

- **Slug**: specs-of-specs
- **Created**: 2026-07-21
- **Source**: https://github.com/github/spec-kit/issues/3423
- **Type**: improvement

## Idea (as captured)

Fetched from GitHub issue #3423 — "[Feature]: Explain the process to use spec kit for feature break down (specs of specs approach)" by @PeterDaumQS (Peter Daum), created 2026-07-09. URL Trust Policy branch: **allowlisted** (host: github.com). Labels: enhancement.

> ### Problem Statement
>
> following the discussion #2914 .
>
> Currently the documentation (https://github.github.com/spec-kit/concepts/complex-features.html) states only that for very large features it's advised to break it into smaller specs.
>
> The way to break down into smaller specs is not described but can be achieved with spec kit.
>
> ### Proposed Solution
>
> Add a documentation section or extension describing how to use spec kit to generate a specs of specs approach (eg. building a roadmap).
>
> ### Component
>
> Documentation
>
> ### Use Cases
>
> 1. Documentation describes how to use spec kit to build the road map
> 2. Documentation describes how to use sub spec kit runs to build from that road map the dedicated part of the features

## Restated

The current docs advise breaking very large features into smaller specs but do not explain how to actually do that with Spec Kit. The proposal is to add documentation (or an extension) describing a "specs of specs" approach — using Spec Kit to build a roadmap and then driving sub-runs to spec out each part of the feature from that roadmap.

## Origin & Context

- **Raised by**: @PeterDaumQS (Peter Daum), via GitHub issue #3423
- **Trigger**: Follow-up to discussion #2914; existing `concepts/complex-features` documentation advises splitting large features into smaller specs but does not describe the method for doing so.

## First-Glance Unknowns

- [NEEDS CLARIFICATION: Should this be delivered as documentation only, or as a new Spec Kit extension/command that automates the roadmap → sub-spec breakdown?]
- [NEEDS CLARIFICATION: What is the intended structure of a "roadmap" artifact and how do sub-spec runs reference/link back to it?]
- [NEEDS CLARIFICATION: What did discussion #2914 conclude or recommend that should shape this approach?]
- [NEEDS CLARIFICATION: Who is the target audience — new Spec Kit users or teams already running multi-spec projects?]
- [NEEDS CLARIFICATION: How do the resulting sub-specs stay consistent with the parent roadmap as it evolves?]
