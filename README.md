# Agent Skills

Reusable planning skills for coding agents.

This repository currently provides two skills:

- `plan-creator`: create or normalize planning docs using a role-based planning model
- `plan-next`: decide the next concrete implementation step from repo state, reusing planning docs when available

## Which Skill To Use

Use `plan-creator` when:

- a repo has no planning docs yet
- planning notes are mixed together and need to be split by role
- you want to scaffold or normalize `roadmap`, `current-action`, `schedule`, `plan`, or `design` docs
- you want to add a planning index such as `plans/README.md`

Use `plan-next` when:

- you want the single most important next implementation step
- you want that next step derived from repository evidence, whether planning docs already exist or not
- you want the current-action doc updated from real code state
- roadmap and implementation have drifted and need to be reconciled

## Skills

### `plan-creator`

`plan-creator` builds a planning surface from a plan doc model. It focuses on document structure and role separation.

Typical capabilities:

- infer the minimum useful planning set from the repo and the user's request
- create missing planning docs
- split one mixed planning file into separate role-based docs
- normalize an inconsistent `plans/` directory
- preserve existing repo terminology and headings when they already fit

Typical outputs:

- `plans/README.md`
- `plans/roadmap.md` or `plans/stage.md`
- `plans/next-step.md`
- `plans/schedule.md`
- `plans/plan.md`
- `plans/design.md`

Example prompts:

```text
Use $plan-creator to create a minimal planning set for this repo.
```

```text
Use $plan-creator to create planning docs for this repo from these product and engineering requirements.
```

```text
Use $plan-creator to normalize the planning docs under plans/ and split mixed content into roadmap, current-action, and schedule roles.
```

```text
Use $plan-creator to add a plans/README.md index and connect the existing planning files by role.
```

### `plan-next`

`plan-next` reads the planning surface, inspects the actual repository state, and chooses one immediate next step. It focuses on execution guidance.

Typical capabilities:

- inspect roadmap, current-action, schedule, plan, and design docs when they exist
- compare plan intent with implementation reality
- choose one next step instead of generating a backlog
- infer a minimum planning surface from repository evidence when no planning docs exist
- update the current-action doc with a compact executable action sheet
- keep roadmap and current-action docs aligned when saving updates

Current-action docs written by `plan-next` usually include:

- current assessment
- one immediate next step
- concrete task list
- completion markers or exit criteria
- short implementation notes when needed

Example prompts:

```text
Use $plan-next to inspect this repo and tell me the next concrete implementation step, even if no planning docs exist yet.
```

```text
Use $plan-next to inspect this repo's plans and tell me the single most important next step.
```

```text
Use $plan-next to compare this repo with its planning docs, tell me the next concrete task, and update the current-action doc.
```

```text
Use $plan-next to compare this repo with its roadmap and current-action docs, then update the current-action file with the next executable task.
```

```text
Use $plan-next to review the repo against plans/ and tell me what to build next without creating a broad backlog.
```

## Install

```bash
npx skills add https://github.com/JackFGreen/agents --skill plan-creator
```

```bash
npx skills add https://github.com/JackFGreen/agents --skill plan-next
```

For Claude Code:

```bash
npx skills add https://github.com/JackFGreen/agents --skill plan-next --agent claude-code
```

## Repository Layout

```text
skills/<skill-name>/
  SKILL.md
  agents/openai.yaml
  references/
  scripts/
  assets/
```

`SKILL.md` is the agent-facing instruction file. The root `README.md` is the human-facing entry point for this repository.
