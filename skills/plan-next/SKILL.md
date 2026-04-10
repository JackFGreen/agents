---
name: plan-next
description: Decide the next concrete implementation step for the current repository by comparing the real code state with planning documents. Use when the user asks what to do next, asks to update next-step guidance, wants the result written back into planning documentation, or needs planning docs normalized by role such as roadmap, current-action, schedule, plan, or design docs.
---

# Plan Next

Assess the repository state against its planning documents, decide the highest-priority next step, and persist the recommendation when the user asks for documentation updates.

If the user asks for examples, asks to add missing planning docs, or the existing docs need a structural reset, read [./references/doc-templates.md](./references/doc-templates.md) and reuse the closest template shape instead of inventing a new format.

## Workflow

1. Read the planning documents that exist.
   - Prefer a planning index doc when present, such as `plans/README.md` or `docs/planning/README.md`
   - Then read roadmap, current-action, schedule, design, and long-horizon plan docs if present
   - Look in common planning locations such as `plans/`, `docs/planning/`, `docs/roadmap/`, `roadmap/`, or the repo root
   - When both roadmap and current-action docs exist, read both before deciding the current action
   - Use the repository's actual planning structure instead of assuming fixed filenames
2. Inspect the actual repository state before giving advice.
   - Check the root `package.json` when relevant
   - Inspect the main implementation area first
   - Use repository docs and layout to infer the active scope
3. Compare plan intent with implementation reality.
   - Identify what the plan expects now
   - Identify what is actually built
   - Prefer the earliest missing foundational work over later feature ideas
4. Produce one primary next step, not a broad backlog.
   - State why this step is next
   - State the concrete deliverables for that step
   - Keep the recommendation short enough to act on immediately
5. If the user asks to save or update the plan, write the result into the repository's current-action document if one exists, and update adjacent planning docs when needed.
6. Keep document roles separated when persisting.
   - Schedule or timeline docs: original pacing, milestone reference
   - Roadmap docs: sequence, status, checkpoints, brief current focus
   - Next-step docs: current assessment, one next step, concrete deliverables
   - If the active stage changes, update both files to stay consistent
7. When a planning doc is missing or badly structured, normalize it with the closest template example from `references/doc-templates.md`.
   - Preserve repository-specific terminology
   - Keep cross-links relative to the directory that actually contains the planning docs
   - Do not duplicate the same detailed task list across roadmap, current-action, and schedule docs
8. Before writing back to an existing current-action doc, compare the existing content with the new recommendation.
   - Preserve still-valid sections, terminology, and links when possible
   - Update only the parts that are now stale or incorrect
   - Do not blindly overwrite the whole file if the current structure is still usable
   - Only rewrite the document wholesale when the file is structurally broken, badly out of date, or the user explicitly asks for a rewrite
9. If no planning docs exist, create the minimum planning surface that satisfies the user's request.
   - Default to a single current-action doc
   - Add a roadmap doc only when the work clearly spans multiple milestones or dependencies
   - Add a schedule doc only when the user asks for dates, pacing, or milestone timing
   - Add a design doc only when architecture decisions need to be captured, not as a default companion file
10. When editing an existing planning doc, classify each section before changing it.
   - Keep sections whose claims still match repository evidence
   - Revise sections whose structure is useful but whose claims are stale
   - Remove sections only when they are misleading, duplicated elsewhere, or no longer serve the doc's role
   - Add sections only when the current document cannot express the needed decision clearly

## Decision Rules

- Optimize for execution, not completeness.
- Prioritize foundational runnable work before later features when the repo is still early-stage.
- Treat empty entry files, missing scripts, and missing type or build setup as evidence that the project is still in initialization.
- Do not assume secondary apps or packages are in scope unless the repo docs or the user indicate that they are.
- If schedule dates and implementation status conflict, use the implementation gap to choose the next step.
- Prefer repository evidence over stale planning text when they disagree.
- If schedule docs conflict with roadmap docs, treat roadmap docs as the current execution order unless the repo says otherwise.
- If no planning docs exist, infer the minimum useful planning set from repository evidence and create only the docs needed for the user's request.
- If sources conflict, resolve them in this order unless the user says otherwise: repository code and runnable evidence, explicit user instruction, current-action doc, roadmap doc, schedule doc, general repo docs.

## Output Shape

When answering "what should I do next", provide:

1. Current assessment
2. The single most important next step
3. The concrete tasks to complete that step

Keep the answer concise and action-oriented.

When updating docs:

- Keep the current-action doc terse and executable, more like a task sheet than a narrative
- Keep schedule or timeline docs as reference material unless the user explicitly asks to replan them
- Keep roadmap docs concise and roadmap-oriented; compress already-completed milestones
- Keep design docs aspirational; do not rewrite them to mirror transient implementation state unless the user asks
- Avoid duplicating the same detailed action list in multiple planning files
- Do not generate a full planning suite by default when a smaller update or a single new doc is enough

## Persistence Rules

When writing the recommendation back into the repo:

- Prefer the repository's existing current-action document, often something like `plans/next-step.md`, `docs/planning/current.md`, or `roadmap/now.md`
- Read the existing document first and diff its claims against repository evidence before editing
- Keep the content short and executable
- Reference the relevant plan files directly
- Treat the current-action doc as the source of truth for the current actionable step
- Use roadmap docs to summarize status and point readers to the current-action doc
- If a new planning document is added, update plan indexes when they exist
- If a new planning document needs to be created, start from the corresponding template in `references/doc-templates.md` and then fill in repository evidence
- Prefer targeted edits over wholesale replacement when the existing doc already has useful structure
- If no current-action doc exists, create one before creating broader planning docs unless the user asked for a different artifact first

## Scope Inference

Infer the active scope from repository evidence:

- planning docs
- workspace layout
- package names
- README or repo guidelines
- explicit user instructions

If the repo has a documented primary workspace, prioritize it. If not, use the area with the clearest active implementation and planning alignment.

## Doc Role Inference

Infer document role by content and responsibility, not filename alone:

- A roadmap doc usually tracks phases, milestones, status, or execution order
- A current-action doc usually contains one immediate task with deliverables
- A schedule doc usually contains dates, weeks, checkpoints, or pacing
- A long-horizon plan doc usually describes target capabilities and end state
- A design doc usually explains architecture, constraints, and module shape

## Things To Avoid

- Do not create a broad planning package when one focused current-action doc would solve the task
- Do not rewrite a roadmap doc into a task sheet
- Do not rewrite a design doc into a status report
- Do not preserve outdated claims just because they already exist in a planning file
- Do not invent stage status, progress, or dates that are not supported by repository evidence

## Example Prompt

Use `$plan-next` to compare the repo with its planning docs, tell me the next concrete task, and save it to the repo's current-action planning file.
