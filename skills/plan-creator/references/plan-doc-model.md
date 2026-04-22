# Plan Doc Model

Use this model to decide which planning documents a repository needs and what each one should control.

Prefer roles over fixed filenames. A file named `stage.md` may act as a roadmap doc; a file named `current.md` may act as a current-action doc.

## Recommended Roles

- Index doc: directory-level guide to the planning files
- Roadmap doc: milestone order, stages, capability sequence, current focus
- Current-action doc: one immediate executable step
- Schedule doc: dates, pacing, checkpoint timing
- Long-horizon plan doc: end state, workstreams, target capabilities
- Design doc: architecture, constraints, module shape, technical decisions

## Role Boundaries

### Index Doc

Use when the repo has multiple planning files and needs a stable entry point.

Own:

- file list
- short role descriptions
- cross-links
- source-of-truth notes

Do not own:

- detailed milestone content
- detailed task lists
- architecture decisions

### Roadmap Doc

Use for execution order.

Own:

- stages or milestones
- status checkpoints
- current focus summary
- exit criteria per stage when useful

Do not own:

- detailed current task execution steps
- detailed dates when a schedule doc already exists
- low-level implementation notes

### Current-Action Doc

Use for the single immediate step the repo should execute now.

Own:

- current judgment or assessment
- one immediate next step
- concrete task list
- completion criteria or validation markers
- short implementation notes when they reduce ambiguity

Do not own:

- broad backlog
- future milestone sequencing
- original timeline planning

### Schedule Doc

Use for original pacing, dates, periods, or milestone timing.

Own:

- dates
- weekly or milestone pacing
- checkpoint timing

Do not own:

- the latest execution decision when reality has drifted
- detailed implementation task lists

### Long-Horizon Plan Doc

Use for intended end state and major workstreams.

Own:

- project goal
- target capabilities
- workstream breakdown
- explicit non-goals

Do not own:

- current task detail
- date-level scheduling
- day-to-day status

### Design Doc

Use for technical shape and constraints.

Own:

- technical problem framing
- constraints
- proposed architecture
- open technical questions

Do not own:

- current execution status
- milestone pacing
- current-action task list

## Minimal Planning Sets

Choose the minimum set that fits the repo state.

### Tiny or Early-Stage Repo

- current-action doc

### Repo With Multiple Stages

- roadmap doc
- current-action doc

### Repo With External Deadlines

- roadmap doc
- current-action doc
- schedule doc

### Repo With Architecture Risk

- roadmap doc
- current-action doc
- design doc

### Larger Repo With Dedicated Planning Directory

- index doc
- roadmap doc
- current-action doc
- optional schedule doc
- optional long-horizon plan doc
- optional design doc

## Conflict Resolution

When inputs disagree, resolve in this order unless the user says otherwise:

1. Repository code and runnable evidence
2. Explicit user instruction
3. Current-action doc
4. Roadmap doc
5. Schedule doc
6. General planning notes or README text

## Naming Guidance

Common filenames by role:

- index doc: `plans/README.md`, `docs/planning/README.md`
- roadmap doc: `plans/roadmap.md`, `plans/stage.md`, `roadmap/implementation.md`
- current-action doc: `plans/next-step.md`, `docs/planning/current.md`, `roadmap/now.md`
- schedule doc: `plans/schedule.md`, `docs/planning/timeline.md`
- long-horizon plan doc: `plans/plan.md`, `roadmap/plan.md`
- design doc: `plans/design.md`, `docs/architecture.md`

Keep an existing filename when the content already serves the right role.
