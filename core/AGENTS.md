# Global rules

Apply to every project and every tool. Project rules live in the project's `AGENTS.md` and take precedence over these.

## Language
- Reply to me in Russian, short and to the point. Quoting English (code, logs, docs, terms) is fine.
- Write everything else in English: code, comments, commit messages, `SOUL.md`, `notes/`, instructions, skills, any files for agents.
- Not sure what I want — ask, don't guess.

## Without asking / ask first / never
- Without asking: read code, run tests and linters, commit to the current branch.
- Ask first: delete data, add dependencies, change global tool settings.
- Never: force-push to `main`, rewrite pushed history, commit secrets.

## Git
- Every project lives in git. No repo — run `git init`.
- Small commits: one idea per commit, clear message.
- `.env` and keys go into `.gitignore`.
- Finished work doesn't stay uncommitted or unpushed: at the end of every task that changed files, run the `ship` skill (commit → review by another agent → push).

## Project memory (`SOUL.md`)
- Every project has `SOUL.md` at its root: what the project is, how it works, decisions made and why, what is in progress. Read it first.
- Before every push, update `SOUL.md` if features, behavior, architecture or decisions changed. The update goes in the same push as the change.
- Keep `SOUL.md` short (~150 lines max). Details go to `notes/`.
- No `SOUL.md` — create one from `~/ai-kit/templates/project/SOUL.md`.

## New project
- Use the `start` skill.

## Skills
- If a skill fits the task, use it instead of working from memory.
