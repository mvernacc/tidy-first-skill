# *Tidy First?* Skill

A [skill](https://agentskills.io/home) for coding agents to apply the *Tidy First?* code cleanup techniques before starting a plan.

References: [*Tidy First?* by Ken Beck](https://www.oreilly.com/library/view/tidy-first/9781098151232/)

## Install

Codex:

```
$skill-installer install https://github.com/mvernacc/tidy-first-skill/tree/main/tidy-first
```

## Usage

Codex:

1. Create a plan, e.g. with the [`create-plan` skill](https://github.com/openai/skills/tree/main/skills/.experimental/create-plan).
2. Ask Codex to apply `tidy-first` in the code areas the plan will touch.
3. Proceed with behavior changes after tidy-only edits are done.

Example:

```
Use tidy-first. Plan: plan.md
```
