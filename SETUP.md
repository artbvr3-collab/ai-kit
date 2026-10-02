# Connecting a tool to ai-kit

Instructions for an agent. Run them in each tool, one at a time:
"Read `~/ai-kit/SETUP.md` and set yourself up."

## Goal
After setup, this tool:
1. reads the global rules from `~/ai-kit/core/AGENTS.md` as its global instructions;
2. sees every skill in `~/ai-kit/skills/`;
3. is connected by **links** to ai-kit files, not copies, so an edit in ai-kit reaches every tool at once.

## Hard rules
- Touch **only your own tool's global settings**. Do not change projects (including the bot).
- Before any change, back up to `~/ai-kit-backup/<YYYY-MM-DD>/<tool>/`.
- Do not delete existing skills or instructions that are not in ai-kit. Leave them and list them in the report.
- Do not move secrets into ai-kit.

## Steps
1. **Update ai-kit:** `git -C ~/ai-kit pull`. If ai-kit lives elsewhere, use that path everywhere below.
2. **Identify yourself:** which tool you are and where your global instructions and skills live. Hints are in the table below. Not in the table, or paths don't match — check your tool's documentation.
3. **Describe the current state:** what is in those locations now.
4. **Show the plan:** exactly what you will create, replace or link. Diffs for files you change.
5. **Ask for confirmation** and wait.
6. **Back up**, then apply:
   - **Global instructions.** Best option: import the file, if the tool supports it (Claude Code: the line `@~/ai-kit/core/AGENTS.md` in `~/.claude/CLAUDE.md`). Otherwise symlink to `core/AGENTS.md`. If the old global instructions had something that is not in `core/AGENTS.md`, don't drop it — list it for me.
   - **Skills.** For each folder `~/ai-kit/skills/<name>/`, symlink it into the tool's skills folder under the same name. If a skill with that name already exists there, don't overwrite it — show the difference and ask.
   - **Retired skills.** `start`, `plan`, `build`, `change`, `vibe-coder`, `grok-plan`, `grok-worker` from the old workflow are replaced by ai-kit's `start`, `ship`, `review`. If old versions are in this tool's skill folders (e.g. `~/.claude/skills`, `~/.agents/skills`, `~/.codex/skills`), list them, ask once, back them up, remove them, then link the ai-kit ones. Copies inside projects and archives stay untouched.
   - **Can't write to a file** (rules are set only in the app UI) — give me the ready text and tell me where to paste it.
   - **Windows without symlinks** — copy, and note in the report that it is a copy and needs another SETUP run to update.
7. **Verify** the rules and skills are actually picked up (new session, skill list, ask "what are your global rules").
8. **Report** to me in Russian: what was done, where the backup is, what remains outside ai-kit.
9. **Update the hints:** if your tool wasn't in the table below or its paths were wrong, fix the table, then commit and push ai-kit (ask first).

## Tool hints
Paths change between versions — check the documentation if something isn't where expected.

| Tool | Global instructions | Skills |
|---|---|---|
| Claude Code | `~/.claude/CLAUDE.md` (supports `@import`) | `~/.claude/skills/<name>/SKILL.md` |
| Codex | `~/.codex/AGENTS.md` | `~/.codex/skills/` or `~/.agents/skills/` |
| Cursor | User Rules in app settings; reads `AGENTS.md` in projects | `~/.cursor/skills/` |
| Hermes Agent | **Paused — skip unless I ask.** `~/.hermes/` is the bot team's own git repo: its `AGENTS.md` and `SOUL.md` (Odin persona) belong to the bot, **don't replace them** — at most add a short reference to `core/AGENTS.md` and ask first | `~/.hermes/skills/` (bot skills; leave as is) |
| ZCode (GLM) | see ZCode docs | reads user skills from `~/.agents/skills/` |
| Gemini CLI | `~/.gemini/GEMINI.md` | see the docs for your version |
| Grok Build | `~/.grok/AGENTS.md` | `~/.grok/skills/` |
| GLM via Hermes (Z.AI API) | set up together with Hermes; nothing separate | — |
