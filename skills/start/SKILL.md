---
name: start
description: Create a new project with git, SOUL.md and the ai-kit template. Use when the user wants to start a new project — "новый проект", "создай проект", "давай начнём", $start.
---

# start: new project

## 1. Ask (one message, only what's missing)
- name;
- what it is, in one sentence;
- where (default `~/Projects/<name>`);
- GitHub repo? (default: yes, private).

## 2. Create
- Target folder exists and is not empty → stop and ask.
- Copy `~/ai-kit/templates/project/` into it, dotfiles included.
- `git init -b main`, `git config core.hooksPath .githooks`, `chmod +x .githooks/*`.

## 3. Fill in
- `SOUL.md`: name, "What it is" and whatever else is already known. Leave unknown sections empty, don't invent.
- `AGENTS.md`: run/test commands, once known.

## 4. First commit and push
- Commit: `Initial project skeleton`.
- GitHub wanted: `gh repo create <name> --private --source . --push`. `gh` missing or not logged in → give me the command and stop there.

## 5. Report (in Russian)
Path, repo URL, what to do next.
