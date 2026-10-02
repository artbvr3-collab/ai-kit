---
name: ship
description: Commit, get an independent review in a fresh context, and push. Use when work is ready to save or push — the user says "пушь", "запушь", "сохрани", "закоммить", "ship", $ship — and at the end of any task that changed files.
---

# ship: commit → review → push

Every finished piece of work ends here. Nothing finished stays uncommitted or unpushed.

## 1. Look
- `git status`, `git diff`, unpushed commits: `git log @{u}..HEAD` (no upstream yet — all local commits).

## 2. Commit
- Split uncommitted changes into small commits, one idea each, clear English messages.
- Check the diff for secrets (`.env`, keys, tokens). Never commit them.

## 3. Checks
- Run the project's test/lint commands from `AGENTS.md` / `SOUL.md`, if any.
- Red → fix it, or stop and report. Never push red.

## 4. Project memory
- If features, behavior, architecture or decisions changed, update `SOUL.md` and commit it.

## 5. Review in a fresh context
The reviewer must not see this conversation — only the repo and the review checklist. Same model is fine; fresh eyes are the point.

- Range: `@{u}..HEAD` (no upstream — all local commits).
- Prompt: `Review commits <range> in this repository following ~/ai-kit/skills/review/SKILL.md. Do not modify any files.`
- Reviewer, first that works:
  1. **Separate chat:** run `claude -p "<prompt>" --disallowedTools "Edit,Write,NotebookEdit"` in the repo root (check `claude --help` if flags error).
  2. **Subagent:** if `claude` CLI is unavailable, spawn a subagent with the same prompt (Claude Code: Agent tool; other tools: their equivalent).
  3. **Self-review** with the same checklist — last resort; say in the report: "independent review not done: <reason>".
- I ask for a second opinion from another vendor → also run `codex exec -s read-only "<prompt>"` or `gemini -p "<prompt>"`, whichever works.
- Act on the result:
  - `BLOCKING` → fix, commit, review again (once). Still blocking → stop and report to me.
  - `SHOULD` → fix if small, otherwise list it in the report.
  - `NIT` → fix only if trivial.

## 6. Push
- `git push` (`git push -u origin <branch>` if no upstream). No remote → tell me.
- The pre-push hook may block on `SOUL.md`: update it, or use `SKIP_SOUL=1 git push` only if the change really doesn't affect what the project is.
- Never force-push `main`.

## 7. Report (in Russian, short)
- commits pushed (one line each);
- reviewer and verdict, what was fixed;
- where it was pushed.
