---
name: review
description: Review code changes (commit range, branch or uncommitted diff) for bugs, security and project-memory accuracy. Use when asked to review — "отревьюй", "проверь коммиты", $review — or when another agent asks for a review.
---

# review

**Read-only.** Never edit files, commit or push.

## Steps
1. Read `SOUL.md` and `AGENTS.md` for context.
2. Read the changes: `git log -p <range>` (default `@{u}..HEAD`; nothing there — `git diff HEAD`). Open the surrounding code when the diff alone isn't enough.
3. Check:
   - correctness: bugs, broken edge cases, things that will fail at runtime;
   - existing behavior broken by the change;
   - security: secrets in the diff, unsafe input handling, injections;
   - tests: changed logic without tests, tests that can't pass;
   - `SOUL.md` still matches what the code does;
   - commits: unrelated changes mixed together, misleading messages.

   Don't nitpick style unless it hurts readability.

## Output (exactly this format, in English)
```
VERDICT: PASS | FIX
BLOCKING:
- file:line — problem — why it matters — suggested fix
SHOULD:
- ...
NIT:
- ...
```
Empty section — `- none`. `PASS` only if `BLOCKING` is empty.

If the user asked for the review directly (not another agent), add a short summary in Russian after the block.
