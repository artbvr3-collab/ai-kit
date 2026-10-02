---
name: ship
description: Commit, get an independent review from another agent, and push. Use when work is ready to save or push — the user says "пушь", "запушь", "сохрани", "закоммить", "ship", $ship — and at the end of any task that changed files.
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

## 5. Review by another agent
- Range: `@{u}..HEAD` (no upstream — all local commits).
- Pick a reviewer that is **not you**. Try in this order, skipping ones not installed (`command -v`):
  - `codex exec -s read-only "<prompt>"`
  - `claude -p "<prompt>"`
  - `gemini -p "<prompt>"`
  - any other installed agent CLI with a non-interactive mode (e.g. Grok Build) — check its `--help`.

  A reviewer fails (not logged in, no subscription, limits, timeout) → move on to the next one. Flags change between versions — check `--help` if a call errors on arguments.
- Run it in the repo root with this prompt:
  `Review commits <range> in this repository following ~/ai-kit/skills/review/SKILL.md. Do not modify any files.`
- Act on the result:
  - `BLOCKING` → fix, commit, review again (once). Still blocking → stop and report to me.
  - `SHOULD` → fix if small, otherwise list it in the report.
  - `NIT` → fix only if trivial.
- All reviewers unavailable or failed → review yourself using the same checklist and say clearly in the report: "external review not done: <reason>".

## 6. Push
- `git push` (`git push -u origin <branch>` if no upstream). No remote → tell me.
- The pre-push hook may block on `SOUL.md`: update it, or use `SKIP_SOUL=1 git push` only if the change really doesn't affect what the project is.
- Never force-push `main`.

## 7. Report (in Russian, short)
- commits pushed (one line each);
- reviewer and verdict, what was fixed;
- where it was pushed.
