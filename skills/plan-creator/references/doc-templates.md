# Planning Doc Templates

Use these templates when the repo lacks a planning doc, when an existing file is structurally broken, or when the user asks you to scaffold planning docs from scratch.

Keep templates terse. Replace placeholders with repository-specific facts.

## Index Doc

Example paths:

- `plans/README.md`
- `docs/planning/README.md`

```md
# Planning Docs

This directory stores the repository's planning documents.

## Documents

- [./roadmap.md](./roadmap.md): Execution order and milestone status
- [./current.md](./current.md): Immediate actionable step
- [./schedule.md](./schedule.md): Original pacing and dates
- [./design.md](./design.md): Architecture notes and constraints

## Source Of Truth

- Use [./roadmap.md](./roadmap.md) for execution order
- Use [./current.md](./current.md) for current execution
- Keep [./schedule.md](./schedule.md) as timing reference unless replanning
```

## Roadmap Doc

Example paths:

- `plans/roadmap.md`
- `plans/stage.md`

```md
# Roadmap

This document defines execution order for the repository.

Current actionable work lives in [./current.md](./current.md).

## Current Overview

| Milestone | Name | Status |
|------|------|------|
| 1 | Foundation | Done |
| 2 | Current Focus | In Progress |
| 3 | Next Expansion | Not Started |

## Milestone 1 Foundation

Goal: State the first completed milestone.

### Done

- Completed capability

### Exit Criteria

- Validation or observable condition

## Milestone 2 Current Focus

Goal: State the current execution goal.

### Done

- Existing capability

### Remaining

- Concrete missing work
- Concrete missing validation

### Exit Criteria

- Observable completion condition
```

## Current-Action Doc

Example paths:

- `plans/next-step.md`
- `docs/planning/current.md`

```md
# Current Next Step

## Current Assessment

- State the current stage or focus
- State the key implementation evidence
- State the most important remaining gap

## Task

Describe one concrete step to execute now.

## Tasks

1. File or module change
2. Validation command
3. Any final subtask needed to complete the step

## Done When

- Observable condition that marks the step complete
- Validation result that should pass

## Implementation Notes

- Keep only short constraints that reduce ambiguity
- Omit this section when not needed
```

Equivalent headings are fine when the repo already uses them, including local-language forms such as `当前判断`, `任务清单`, `完成标志`, and `代码建议`.

## Schedule Doc

Example paths:

- `plans/schedule.md`
- `docs/planning/timeline.md`

```md
# Project Schedule

> Start date: YYYY-MM-DD
> Goal: One-sentence pacing goal

This document records the original pacing plan.

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

Example paths:

- `plans/plan.md`
- `roadmap/plan.md`

```md
# Project Plan

## Goal

Describe the intended end state in one or two paragraphs.

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

Example paths:

- `plans/design.md`
- `docs/architecture.md`

```md
# Design Notes

## Problem

Describe the technical problem or design target.

## Constraints

- Constraint from scope
- Constraint from runtime or tooling
- Constraint from validation or operations

## Proposed Shape

- Main module boundary
- Main data flow
- Important interface or type

## Open Questions

- Unresolved technical question
- Deferred design choice
```
