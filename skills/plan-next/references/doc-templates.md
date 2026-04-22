# Planning Doc Templates

Use these templates when the repository lacks a planning doc, when an existing doc needs a structural reset, or when the user asks for an example shape before you write updates.

Keep templates terse. Replace placeholder bullets with repository-specific facts instead of preserving the example wording.

Prefer document roles over fixed filenames. Reuse the closest role and adapt links to the repository's actual layout.

## Recommended Document Roles

- Index doc: directory-level guide that explains which planning docs exist and what each one controls
- Roadmap doc: long-horizon goals, stages, milestones, or capability sequence
- Current-action doc: the single immediate next step
- Schedule doc: original timeline or milestone pacing
- Design doc: architecture notes, technical constraints, and major decisions

Common locations include:

- `plans/`
- `docs/planning/`
- `docs/roadmap/`
- `roadmap/`
- repository root for smaller projects

## Index Doc

Use when the repo has multiple planning docs and needs role separation.

### Example Path

- `plans/README.md`
- `docs/planning/README.md`

```md
# Planning Docs

This directory stores planning documents for the repository.

## Documents

- [./roadmap.md](./roadmap.md): Long-horizon product and execution direction
- [./design.md](./design.md): Design notes and technical decisions
- [./schedule.md](./schedule.md): Original timeline or milestone pacing
- [./current.md](./current.md): Single current actionable step

## Source Of Truth

- Use [./roadmap.md](./roadmap.md) for execution order and progress
- Use [./current.md](./current.md) for the immediate task
- Keep [./schedule.md](./schedule.md) as reference unless explicitly replanning
```

## Roadmap Doc

Use for stage order, milestone order, capability sequence, or status checkpoints.

### Example Path

- `plans/stage.md`
- `docs/planning/roadmap.md`
- `roadmap/implementation.md`

```md
# Roadmap

This document turns the project plan into an execution sequence.

If this conflicts with the schedule, use this file as the execution order.

## Current Overview

| Milestone | Name | Status |
|------|------|------|
| 1 | Foundation | Done |
| 2 | Current Focus | In Progress |
| 3 | Next Expansion | Not Started |

Current actionable work lives in [./current.md](./current.md).

Current focus: Milestone 2.

## Milestone 1 Foundation

Goal: Establish the minimum runnable baseline.

### Done

- Example completed milestone

### Exit Criteria

- Example validation command

## Milestone 2 Current Focus

Goal: Describe the current execution objective in one sentence.

### Done

- Existing capability that already supports this milestone

### Remaining

- Concrete missing capability
- Concrete missing validation

### Exit Criteria

- Observable condition that marks the milestone complete

## Milestone 3 Next Expansion

Goal: Describe the next milestone briefly.

### Remaining

- Future work item

### Exit Criteria

- Outcome that makes this milestone complete
```

## Current-Action Doc

Use for the single current recommendation. Keep it executable and short. Favor a compact action sheet that explains why this is the current priority, what to do now, and how to know the step is done.

### Example Path

- `plans/next-step.md`
- `docs/planning/current.md`
- `roadmap/now.md`

```md
# Current Next Step

## Current Assessment

- State the current milestone, stage, or focus
- State the key implementation evidence that supports this judgment
- State the most important remaining gap

## Task

Describe one concrete step to execute now.

## Tasks

1. File or module change
2. Validation command
3. Any other concrete subtask required to finish the step

## Done When

- Observable condition that marks the step complete
- Validation result that should pass

## Implementation Notes

- Keep only short constraints, boundaries, or code-shape guidance that reduce ambiguity
- Omit this section when it does not help execution
```

The document may use equivalent headings such as `Current Judgment`, `Next Step`, `Task List`, `Completion Criteria`, or repository-local language such as `当前判断`, `任务清单`, `完成标志`, and `代码建议`.

## Schedule Doc

Use for the original timeline or milestone pacing. Do not turn it into a duplicate of the current-action doc.

### Example Path

- `plans/schedule.md`
- `docs/planning/timeline.md`
- `roadmap/schedule.md`

```md
# Project Schedule

> Start date: YYYY-MM-DD
> Goal: One-sentence timeline goal

This document records the original pacing plan. Actual execution order is maintained in [./roadmap.md](./roadmap.md).

## Milestones

| Period | Focus | Notes |
|-------|------|------|
| Week 1 | Foundation | Baseline setup |
| Week 2 | Current buildout | Main focus area |
| Week 3 | Expansion | Follow-up scope |

## Checkpoints

| Time | Checkpoint |
|------|-----------|
| Week 1 | First runnable milestone |
| Week 2 | Current core milestone |
| Week 3 | Next milestone |
```

## Long-Horizon Plan Doc

Use for long-horizon goals, major modules, and intended end state. Keep it aspirational rather than task-sheet oriented.

### Example Path

- `plans/plan.md`
- `docs/planning/vision.md`
- `roadmap/plan.md`

```md
# Project Plan

## Goal

Describe the end-state in one or two paragraphs.

## Core Workstreams

- Workstream 1 and why it exists
- Workstream 2 and why it exists
- Workstream 3 and why it exists

## Target Capabilities

- User-facing capability
- Technical platform capability
- Operational or quality capability

## Non-Goals For Now

- Explicitly deferred idea
- Explicitly deferred system area
```

## Design Doc

Use for architecture notes, technical choices, and constraints. Keep it stable; do not rewrite it on every implementation delta.

### Example Path

- `plans/design.md`
- `docs/planning/design.md`
- `docs/architecture.md`

```md
# Design Notes

## Problem

Describe the technical problem or design target.

## Constraints

- Constraint from product scope
- Constraint from runtime or tooling
- Constraint from validation or operations

## Proposed Shape

- Main module boundary
- Main data flow
- Important interface or type

## Open Questions

- Unresolved technical question
- Deferred design decision
```

## Mapping Guidance

When the repository uses different filenames, map by role:

- `stage.md`, `roadmap.md`, `milestones.md`, `implementation-plan.md`: roadmap doc
- `next-step.md`, `current.md`, `now.md`, `focus.md`: current-action doc
- `schedule.md`, `timeline.md`, `milestones-calendar.md`: schedule doc
- `plan.md`, `vision.md`, `strategy.md`: long-horizon plan doc
- `design.md`, `architecture.md`, `tech-design.md`: design doc

If multiple documents overlap, prefer the one with the clearest current ownership and update cross-links instead of duplicating content.
