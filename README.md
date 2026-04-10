# Agent Skills

This repository stores multiple agent skills.

## Skills

### `plan-next`

`plan-next` compares a repository's actual code state with its planning documents and decides the single most important next implementation step.

Use it when you want an agent to:

- inspect roadmap, current-action, schedule, or design docs
- compare planning intent with what is actually built
- recommend one concrete next step instead of a broad backlog
- update the repo's current-action planning doc when asked
- normalize missing or poorly structured planning docs

It is designed for plan-aware execution guidance rather than general project management prose.

## Layout

```text
skills/<skill-name>/
  SKILL.md
  agents/openai.yaml
  references/
  scripts/
  assets/
```

## Conventions

- Keep each skill self-contained under `skills/`.
- Put human-facing repository docs at the repo root.
- Avoid extra docs inside individual skill folders unless they are required by the skill workflow.

## Install

```bash
npx skills add https://github.com/JackFGreen/agents --skill <skill-name>
```

For Claude Code:

```bash
npx skills add https://github.com/JackFGreen/agents --skill plan-next --agent claude-code
```

## Example

Prompt the agent with:

```text
Use $plan-next to compare this repo with its planning docs, tell me the next concrete task, and update the current-action doc.
```
