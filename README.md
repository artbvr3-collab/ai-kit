# ai-kit

My rules for working with AI agents — one set for every tool (Claude Code, Codex, Cursor, Hermes, GLM).

```
core/AGENTS.md         global rules: language, git, project memory, what needs asking
skills/                all skills in one place
templates/project/     new project skeleton: SOUL.md, AGENTS.md, notes/, pre-push hook
INVENTORY.md           an agent finds everything already installed (changes nothing)
SETUP.md               an agent connects its tool to ai-kit
inventory/             inventory reports
```

## Getting started
1. `git clone <this repo> ~/ai-kit`
2. In Claude Code: "Read `~/ai-kit/INVENTORY.md` and follow it." Review the report, move skills into `skills/`.
3. In each tool, one at a time: "Read `~/ai-kit/SETUP.md` and set yourself up."

## Changing rules
Edit the file in `~/ai-kit` and commit; push to GitHub when you want it on other machines. Tools are connected by links, so changes apply right away. On another machine: `git pull`.

## Workflow
Everything goes through commits:
- `start` — new project: template, local git, `SOUL.md`; private GitHub repo only if asked.
- work in small commits;
- `ship` — commit → checks → `SOUL.md` update → independent review in a separate chat or subagent → push only when asked. Runs at the end of every task.
- `review` — the reviewer's checklist and output format; also usable on its own.

## Project layout
- `SOUL.md` — project memory: what it is, how it works, decisions, status. Agents read it first and update it when finishing a task.
- `.githooks/pre-push` blocks pushing code changes without a `SOUL.md` update. For changes that don't affect the project's meaning: `SKIP_SOUL=1 git push`.
