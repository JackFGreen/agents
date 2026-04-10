# Agent Skills

This repository stores multiple agent skills.

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
npx skills add https://github.com/<owner>/<repo> --skill <skill-name>
```
