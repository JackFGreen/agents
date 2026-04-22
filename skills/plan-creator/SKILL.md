---
name: plan-creator
description: Create or normalize repository planning documents using a role-based planning model. Use when Codex needs to add missing planning docs, split a mixed planning file into roadmap/current-action/schedule/design roles, rewrite planning docs around a consistent plan doc model, or scaffold repo planning files such as plans/README.md, roadmap.md, next-step.md, schedule.md, plan.md, or design.md.
---

# Plan Creator

Create or normalize a repository's planning surface from a plan doc model instead of ad hoc filenames or mixed-purpose notes.

Read [./references/plan-doc-model.md](./references/plan-doc-model.md) before writing. Read [./references/doc-templates.md](./references/doc-templates.md) when you need starter shapes or need to create a missing file from scratch.

## Workflow

1. Inspect the repository's existing planning surface.
   - Look for planning docs in `plans/`, `docs/planning/`, `docs/roadmap/`, `roadmap/`, or the repo root
   - Prefer an index doc when present, such as `plans/README.md`
   - Identify whether docs are missing, duplicated, or mixing multiple roles
2. Infer the minimum useful planning set.
   - Start with the user's request
   - Create only the roles the repo actually needs now
   - Default to a current-action doc first when the planning surface is sparse
3. Map each document to one role.
   - Index doc: planning directory guide
   - Roadmap doc: execution order and milestones
   - Current-action doc: single immediate task
   - Schedule doc: original pacing or dates
   - Long-horizon plan doc: end state and workstreams
   - Design doc: architecture and constraints
4. Write or revise docs by role, not by filename habit.
   - Keep one source of truth per responsibility
   - Move duplicated task detail out of roadmap and schedule docs into the current-action doc
   - Keep design docs stable and avoid rewriting them as status reports
5. Keep the planning set connected.
   - Add relative cross-links when multiple planning docs exist
   - Update index docs when new planning files are added
   - Point roadmap docs to the current-action doc for the immediate task

## Authoring Rules

- Optimize for execution clarity, not completeness.
- Prefer repository terminology over generic template wording.
- Keep each doc short enough to scan quickly.
- Preserve still-correct content when normalizing an existing doc set.
- Prefer targeted edits over wholesale rewrites unless the structure is broken.
- Do not create a broad planning suite when one focused current-action doc is enough.
- Do not duplicate the same detailed task list across roadmap, schedule, and current-action docs.
- Do not invent dates, status, or milestones that are not supported by repository evidence or the user's request.

## Output Rules

When the user asks to create planning docs:

- State which docs you will create or revise
- State the role each doc will serve
- Keep the resulting docs consistent with the plan doc model

When the user asks for only one artifact:

- Create only that artifact unless another file is required to make it coherent
- If another file is required, keep the expansion minimal and explain why

When planning docs already exist:

- Reuse the repository's existing names when they already match a clear role
- Normalize by content responsibility, not by forcing a rename
- Preserve repository-local headings and language when they still express the right role clearly

## Common Requests

- "Create planning docs for this repo"
- "Split this mixed plan into roadmap and current work"
- "Add a `plans/README.md` and normalize the rest"
- "Create a current-action file from this roadmap"
- "Turn these loose notes into a plan/roadmap/schedule/design set"

## Things To Avoid

- Do not turn schedule docs into task sheets
- Do not turn roadmap docs into implementation diaries
- Do not use the current-action doc as a backlog dump
- Do not create redundant parallel docs that compete for the same responsibility
- Do not add documentation files outside the requested planning surface just to explain the process
