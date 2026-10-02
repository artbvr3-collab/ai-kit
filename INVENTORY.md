# Inventory: what is installed

Instructions for an agent. Run them in any local tool (Claude Code preferred):
"Read `~/ai-kit/INVENTORY.md` and follow it."

## Main rule
**Do not change, delete or move anything.** Only read and write a report.
**Do not copy secrets:** keys, tokens, passwords, `.env` contents. For MCP and APIs, names only.

## What to find

1. **Installed AI tools.** Check Claude Code, Codex, Cursor, Hermes, GLM (how it is launched: as its own program or through another tool with a different API), and anything similar you find. For each: version and config folder.

2. **Global instructions.** Files like `CLAUDE.md`, `AGENTS.md`, `SOUL.md`, `GEMINI.md`, `.cursorrules` in tool config folders (`~/.claude`, `~/.codex`, `~/.cursor`, `~/.hermes`, `~/.config/*`, etc.). For each: path, size, 2–3 line summary.

3. **Skills.** Every `SKILL.md` under the home folder (skip `node_modules`, `.git`, caches, trash). First split them by origin:
   - **Bundled:** shipped with a tool or installed from a plugin/marketplace (e.g. Hermes default skills, Claude Code plugins). These update with the tool and are not mine. Only count them per source (`Hermes built-in: 120`), don't list each one. If a bundled skill was modified locally, treat it as custom.
   - **Custom:** written by me or my agents (in global skill folders or inside projects). If unsure about a skill, put it here and mark it "unsure".

   For each custom skill:
   - name and description (from the file header),
   - path, which tool or project it belongs to,
   - modification date,
   - copies elsewhere and whether they are identical (compare folder hashes).

4. **Slash commands, hooks, settings.** `commands/`, `hooks`, `settings.json`, `config.toml`, `config.yaml` — what is configured, no secrets.

5. **MCP servers.** Names only, and which tool they are connected to.

6. **Projects.** Git repos under the home folder that have `AGENTS.md`, `CLAUDE.md`, `SOUL.md` or their own skills. Path and which of these they have.

## Report

Save to `~/ai-kit/inventory/<hostname>-<YYYY-MM-DD>.md`:

- table of tools;
- bundled skills: one line per source with a count;
- table of custom skills: name, location, duplicates, whether copies differ;
- global instructions and where they overlap or contradict each other;
- **proposal**: which skills and rules to move to `~/ai-kit/skills/` and `~/ai-kit/core/`, what to drop as outdated, where to pick one version out of several.

Show me the summary and ask whether to commit the report to ai-kit.
