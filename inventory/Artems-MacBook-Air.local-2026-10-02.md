# AI-kit inventory — Artems-MacBook-Air.local — 2026-10-02

Read-only scan. No files were changed except this report. No secrets were read or copied
(MCP/API entries are names only).

## 1. Installed AI tools

| Tool | Version | Binary / app | Config folder | Notes |
|---|---|---|---|---|
| Claude Code | 2.1.285 | `~/.local/bin/claude`, `/Applications/Claude.app` | `~/.claude` | Also used as the bot runtime inside Hermes (see below) |
| Codex CLI | 0.157.0 | `~/.local/bin/codex`, `/Applications/ChatGPT.app` | `~/.codex` | model `gpt-6-sol`, reasoning high, approval `never`; 13 OpenAI plugins |
| Hermes Agent | vgit.7b761da (2026-09-24), git install | `~/.local/bin/hermes`, `/Applications/Hermes.app` | `~/.hermes` | Live 5-bot Telegram team (Odin + huginn/muninn/andvari/heimdall); since 01.10 bots run on own Telegram gateway + Claude Code; update available |
| Gemini CLI | 0.54.4 | `~/.local/bin/gemini` | `~/.gemini` | OAuth personal; also holds Antigravity IDE builtin (`~/.gemini/antigravity-ide`) |
| ZCode (GLM) | — | `/Applications/ZCode.app` | `~/.zcode` | GLM-5.3 via `zai-individual-coding-plan`. **No standalone `glm` binary exists**; GLM is launched (a) as ZCode's own model, and (b) through the Z.AI API by Hermes (`provider: zai`, `base_url: api.z.ai/api/coding/paas/v4`, `model: glm-5.3-flash`) |
| Grok Build CLI | — | `/Applications/Grok Bot.app` | `~/.grok` | Own AGENTS.md, bundled skills, marketplace cache |
| Kimi (OpenClaw variant) | — | — | `~/.kimi_openclaw` | workspace with 8 skills (calendar, trello, budget…) |
| OpenClaw / AutoClaw | — | — | `~/.openclaw-autoclaw` | **Residue**: 605 SKILL.md under skills/ + agents/; Hermes config already shows `openclaw_residue_cleanup: seen` |
| Cursor | — | **not in /Applications** | `~/.cursor` | App appears uninstalled (~mid-July 2026, last IDE state 18.07); config/skills remain |
| Zed | — | `/Applications/Zed.app` | — | Editor only; no agent instructions/skills found |
| hub-global | — | — | `~/.hub-global` | Shared skill/runtime hub (node/python runtimes, `opencode-skills-last-known-good.json`); 20 media-generation skills |

## 2. Global instructions

| File | Size | Summary |
|---|---|---|
| `~/.hermes/AGENTS.md` | 38 KB | HERMES_HOME for the live 5-bot team; git repo of bot-team source; patch → review → push policy; map of profiles and tracked/untracked paths; "reply in Russian" |
| `~/.hermes/SOUL.md` | 12 KB | Odin persona: Russian chat, English artifacts, direct/cynical tone, orchestrator role, delegation rules |
| `~/.hermes/FEATURES.md` | 50 KB | Russian user-facing feature list of the bot team with ✅/🟡/⚪ statuses (updated 02.10) |
| `~/.grok/AGENTS.md` | 411 B | Language policy only: Russian chat, English artifacts |
| `~/.codex/AGENTS.md` | **0 B** | Empty |
| `~/.claude/CLAUDE.md` | — | Missing |
| `~/.cursorrules`, `~/.cursor/rules/` | — | Missing / empty |

Plus ~30 `.bak-*` copies of AGENTS/SOUL/FEATURES/config inside `~/.hermes` (dated backups, 25.09–02.10).

**Overlap:** the language policy (Russian chat / English artifacts) is stated three times — Hermes SOUL.md, Hermes AGENTS.md, Grok AGENTS.md — consistently, no contradictions found. **Gap:** Codex and Claude Code have no global instructions at all, so the shared policy does not reach them.

## 3. Skills

Total `SKILL.md` under `$HOME`: **2013** counted under the INVENTORY.md skip rules (excluding `~/Library`, `.cache`, `.npm`, `node_modules`; raw count including those: 2946). Counts on this machine drift by a few files between runs because tool caches are live. Of the 2013, all but the 150 user-managed ones are vendored/cache:

| Location | Count | Kind |
|---|---|---|
| `~/.codex/.tmp` | 616 | temp junk |
| `~/.openclaw-autoclaw/{skills,agents}` | 605 | OpenClaw residue |
| `~/.hermes/{profiles,hermes-agent,claude}` | 479 | Hermes-internal (profiles, engine source, bot runtimes) |
| `~/.zcode/cli`, `~/.claude/plugins`, `~/.codex/plugins`, `~/.grok/{marketplace-cache,bundled}` | 185 | plugin caches / bundled |
| `~/.hermes/tools/agent-browser-*` | 7 | vendored tool binaries (mtime 1985 = packed) |

The table sums to 1892 rather than 2013−150 = 1863 because the 19 skills under `~/.hermes/claude/bots/` are counted both here (as Hermes-internal) and in the user-managed 150 below, and boundary paths (`~/.hermes/cache`, `~/.hermes/installs`) sit on neither side cleanly.

**User-managed skills: 150** by location: `.hermes` 36 (bots + `skills/hermes`), `.cursor` 21 (mostly Cursor-bundled `skills-cursor`), `.hub-global` 20, `Documents` 16, `.claude` 14, `Projects` 12, `.codex` 9, `.kimi_openclaw` 8, `.agents` 7, `.grok` 4 (music), `.gemini` 3 (Antigravity builtin).

Full list (name, mtime, description, path) — see Appendix. Duplicates compared by whole-folder hash:

| Skill | Copies | Verdict |
|---|---|---|
| `change` | 5 | 4 identical (`~/.agents`, `~/.claude`, `Documents/Codex/.../Coding`, `Documents/kimi/.../migration`); `Projects/_archive/sdd-kit` older & different |
| `build` | 5 | `~/.agents` = Codex = kimi copies; **`~/.claude` is newer (01.10) and evolved** (whole-plan build vs one-step); sdd-kit oldest |
| `plan` | 5 | `~/.agents` = Codex = kimi; **`~/.claude` newer (01.10)**: auto-continues into `$build`; sdd-kit oldest |
| `start` | 5 | SKILL.md identical in `~/.agents` vs `~/.claude`, supporting files differ; `~/.agents` = kimi; sdd-kit oldest |
| `skill-creator` | 3 | all differ: `.claude/skills/synced` (plugin-synced), `.codex/skills/.system`, `.hub-global` — different tools' own copies |
| `scheduled-research-monitoring` | 3 | huginn = odin bots identical; `~/.hermes/skills/hermes` source differs (newer) |
| `track-personal-budget` | 3 | all differ; biggest/newest in `Documents/Codex/Projects/Life/.agents` (260K, 01.10) |
| `agenda`, `bot-team-delegation`, `external-agents`, `google-calendar`, `usage-hub` | 2 each | Hermes bot copies vs `~/.hermes/skills/hermes` sources — bot copies drift from sources |

Note: **ZCode loads the vibe-coder family from `~/.agents/skills`**, whose `build`/`plan` are one generation behind the `~/.claude` copies edited 01.10.

## 4. Commands, hooks, settings

- `~/.claude/settings.json`: permissions allowlist (git, ls, cat), opus-5-5 high effort, dark theme, push notifications. No `commands/`, no hooks.
- `~/.codex/config.toml`: `gpt-6-sol`, approval never, 13 OpenAI plugins (slack, documents, pdf, spreadsheets, presentations, browser, computer-use…), many per-project sections.
- `~/.hermes/config.yaml`: gateway multiplex; GLM via zai; auxiliary compression/approval via deepseek-chat; STT groq/ru; plugins idle-reset, board-context, about-me, notice-cleanup. `hooks/` exists but empty.
- `~/.cursor/mcp.json`: empty `mcpServers`. `skills-cursor/` are Cursor's bundled skills (create-rule, sdk, onboard…).
- `~/.gemini/settings.json`: OAuth personal only.
- `~/.zcode/v2/*`: bot/provider/credential configs; official plugins installed (browser-use, documents, pdf, presentations, spreadsheets, plugin-creator, zcode-guide) + user skills from `~/.agents`.

## 5. MCP servers (names only)

| Tool | Servers |
|---|---|
| Codex | `node_repl`, `computer-use`, `openaiDeveloperDocs` |
| Claude Code | none (global and per-project) |
| Cursor | none |
| Hermes | none in config.yaml |
| ZCode | MCP-like tools ship inside official plugins (node_repl, web_reader, image-search, 4_5v_mcp) — not user-configured |

## 6. Projects with agent instructions/skills

36 git repos under `~/Projects` and `~/Documents/Codex/Projects`. With AGENTS.md/CLAUDE.md/SOUL.md: music-taste, booklab (also `.agents/skills`), chat-anon, tg-agent-notify, dnd-ai, help-bot, proxyCheck, audizi, Argus, listen, clipbar, newvoice, jira-integration, mic-pipe, tg-research, daydashboard, voicetype, caroline, port-doctor, p-agent, LAB3.0, uk-ecommerce-leads (also `.agents/skills`), + 11 in `Projects/_archive`. Non-git folder with skills: `Documents/Codex/Projects/Life` (budget skill + ledger, used by bot Andvari).

## 7. Proposal

**Move to `~/ai-kit/skills/` (canonical single copy):**
1. vibe-coder family — `start`, `plan`, `build`, `change`, `vibe-coder`, `grok-plan`, `grok-worker`. For `build`/`plan` take the **newer `~/.claude` versions (01.10)**, for the rest `~/.agents`. Then point tools at ai-kit (symlink `~/.agents/skills` → ai-kit, or copy on release) and delete the four stale copies (`Documents/Codex/.../Coding/.agents`, `Documents/kimi/.../migration/agents-skills`, `Projects/_archive/sdd-kit`, duplicate in `~/.claude`).
2. `music-taste` — keep the repo `~/Projects/music-taste` as source of truth; the `~/.agents` copy becomes a symlink. Same pattern for `study-note` if it has a home repo.

**Move to `~/ai-kit/core/`:**
3. The shared language/voice policy (Russian chat, English artifacts, no flattery, direct tone) currently duplicated in Hermes SOUL.md + Grok AGENTS.md. One `core/policy.md`, referenced (or concatenated) by each tool — and finally give Codex and Claude Code the global instructions they now lack.

**Drop / leave as-is (not worth centralising):**
- Drop as outdated: `Projects/_archive/sdd-kit` skill copies (June generation), `Documents/kimi/workspace/migration` (migration leftovers), `~/.codex/.tmp` (616 temp files), `~/.openclaw-autoclaw` (OpenClaw residue, cleanup already flagged in Hermes), `Documents/Codex/2026-07-27/*` chat leftovers.
- Leave alone: Hermes internals (`~/.hermes/{skills,profiles,claude,bots}` — managed by its git repo; but worth re-syncing the drifted bot copies from `skills/hermes` sources), plugin/system skill copies (`skills/synced`, `.system`, `skills-cursor`, `.grok/bundled` — owned by their tools), `.hub-global` (active media-skill hub), job-specific skills in project repos (ecommerce-leads family, bridge-broker-geo).

**Biggest single win:** one canonical vibe-coder set in ai-kit + a symlink from `~/.agents/skills` fixes the stale-`build`/`plan`-in-ZCode problem and removes 8 duplicate copies at once.

## Appendix — user-managed skills (150)
| Name | Modified | Description | Path |
|---|---|---|---|
| 3d-animation-short-generator | 2026-09-27 | Create a coherent 3D animated short from an idea with character continuity, shot planning, video generation, music, and review. Use for c… | `/Users/pr1ce/.hub-global/skills/3d-animation-short-generator/SKILL.md` |
| agenda | 2026-10-01 | "Use for the user's tasks and to-dos (дела, задачи, не забыть, напомни, проконтролируй, зачекиниться), controlled tasks and answers to 🎯… | `/Users/pr1ce/.hermes/claude/bots/heimdall/.claude/skills/agenda/SKILL.md` |
| agenda | 2026-10-01 | "Use for the user's tasks and to-dos (дела, задачи, не забыть, напомни, проконтролируй, зачекиниться), controlled tasks and answers to 🎯… | `/Users/pr1ce/.hermes/claude/bots/odin/.claude/skills/agenda/SKILL.md` |
| agent-browser | 1985-10-26 | Browser automation CLI for AI agents. Use when the user needs to interact with websites, including navigating pages, filling forms, click… | `/Users/pr1ce/.hermes/tools/agent-browser-0.26.0-darwin-arm64/skills/agent-browser/SKILL.md` |
| agentcore | 1985-10-26 | Run agent-browser on AWS Bedrock AgentCore cloud browsers. Use when the user wants to use AgentCore, run browser automation on AWS, use a… | `/Users/pr1ce/.hermes/tools/agent-browser-0.26.0-darwin-arm64/skill-data/agentcore/SKILL.md` |
| agy-customizations | 2026-08-15 | >- | `/Users/pr1ce/.gemini/antigravity-ide/builtin/skills/agy-customizations/SKILL.md` |
| ai-release-deep-dive | 2026-10-01 | "Use when a user asks to dig into an AI model release." | `/Users/pr1ce/.hermes/claude/bots/huginn/.claude/skills/ai-release-deep-dive/SKILL.md` |
| anime-game-pv | 2026-09-27 | / | `/Users/pr1ce/.hub-global/skills/anime-game-pv/SKILL.md` |
| antigravity_guide | 2026-08-15 | Provides a comprehensive guide, quick reference, and sitemap for Google Antigravity (AGY), including the Antigravity CLI (agy), Antigravi… | `/Users/pr1ce/.gemini/antigravity-ide/builtin/skills/antigravity_guide/SKILL.md` |
| apple-availability-th | 2026-10-01 | "Use when asked when Apple products go on sale in Thailand." | `/Users/pr1ce/.hermes/claude/bots/huginn/.claude/skills/apple-availability-th/SKILL.md` |
| automate | 2026-08-13 | Use this skill to create Cursor Automations. | `/Users/pr1ce/.cursor/skills-cursor/automate/SKILL.md` |
| autopilot | 2026-08-13 | >- | `/Users/pr1ce/.cursor/skills-cursor/autopilot/SKILL.md` |
| booklab-run | 2026-08-31 | Run a new book through the booklab pipeline (inbox -> import -> probe TTS -> full TTS run -> site rebuild). Use when the user drops new E… | `/Users/pr1ce/Projects/booklab/.agents/skills/booklab-run/SKILL.md` |
| bot-team-delegation | 2026-09-30 | Use when routing a task to a team bot or one-shot pings. | `/Users/pr1ce/.hermes/skills/hermes/bot-team-delegation/SKILL.md` |
| bot-team-delegation | 2026-10-01 | Use when routing a task to a team bot or one-shot pings. | `/Users/pr1ce/.hermes/claude/bots/odin/.claude/skills/bot-team-delegation/SKILL.md` |
| brand-ad | 2026-09-27 | / | `/Users/pr1ce/.hub-global/skills/brand-ad/SKILL.md` |
| brand-promo-video-generator | 2026-09-27 | Create a promotional short from verified brand assets, product references, and campaign goals. Use for launches and social promotion; do… | `/Users/pr1ce/.hub-global/skills/brand-promo-video-generator/SKILL.md` |
| bridge-broker-geo | 2026-07-31 | "Анализировать эффективность CRM-брокеров внутри одного Bridge GEO: сравнивать CR, EPL и текущие Sale Status за сегодня, неделю с понедел… | `/Users/pr1ce/.codex/skills/bridge-broker-geo/SKILL.md` |
| build | 2026-06-10 | — | `/Users/pr1ce/Projects/_archive/sdd-kit/skills/build/SKILL.md` |
| build | 2026-08-01 | Implement the next verified step from notes/PLAN.md immediately after planning. Use when the user invokes $build or /build, says "собирае… | `/Users/pr1ce/.agents/skills/build/SKILL.md` |
| build | 2026-08-01 | Implement the next verified step from notes/PLAN.md immediately after planning. Use when the user invokes $build or /build, says "собирае… | `/Users/pr1ce/Documents/Codex/Projects/Coding/.agents/skills/build/SKILL.md` |
| build | 2026-08-04 | Implement the next verified step from notes/PLAN.md immediately after planning. Use when the user invokes $build or /build, says "собирае… | `/Users/pr1ce/Documents/kimi/workspace/migration/agents-skills/build/SKILL.md` |
| build | 2026-10-01 | Implement notes/PLAN.md after planning. Use when the user invokes $build or /build, says "собираем", "погнали кодить", "следующий шаг", "… | `/Users/pr1ce/.claude/skills/build/SKILL.md` |
| canvas | 2026-08-13 | >- | `/Users/pr1ce/.cursor/skills-cursor/canvas/SKILL.md` |
| ch-ecommerce-leads | 2026-09-29 | Add Swiss ecommerce companies to data/switzerland/ch-ecommerce-leads.xlsx — Zefix lookup, Google Maps phone, Zefix link instead of a PDF.… | `/Users/pr1ce/Documents/Codex/Projects/uk-ecommerce-leads/.agents/skills/ch-ecommerce-leads/SKILL.md` |
| change | 2026-06-10 | — | `/Users/pr1ce/Projects/_archive/sdd-kit/skills/change/SKILL.md` |
| change | 2026-08-01 | Modify an existing project according to the change's real code blast radius. Use when the user invokes $change or /change, or says "попра… | `/Users/pr1ce/.agents/skills/change/SKILL.md` |
| change | 2026-08-01 | Modify an existing project according to the change's real code blast radius. Use when the user invokes $change or /change, or says "попра… | `/Users/pr1ce/.claude/skills/change/SKILL.md` |
| change | 2026-08-01 | Modify an existing project according to the change's real code blast radius. Use when the user invokes $change or /change, or says "попра… | `/Users/pr1ce/Documents/Codex/Projects/Coding/.agents/skills/change/SKILL.md` |
| change | 2026-08-04 | Modify an existing project according to the change's real code blast radius. Use when the user invokes $change or /change, or says "попра… | `/Users/pr1ce/Documents/kimi/workspace/migration/agents-skills/change/SKILL.md` |
| cinematic-title-sequence | 2026-09-27 | / | `/Users/pr1ce/.hub-global/skills/cinematic-title-sequence/SKILL.md` |
| claude-chat-watcher | 2026-09-29 | Use when asked to check or recap a local Claude Code chat. | `/Users/pr1ce/.hermes/skills/claude-chat-watcher/SKILL.md` |
| cool-music-video | 2026-09-27 | / | `/Users/pr1ce/.hub-global/skills/cool-music-video/SKILL.md` |
| core | 1985-10-26 | Core agent-browser usage guide. Read this before running any agent-browser commands. Covers the snapshot-and-ref workflow, navigating pag… | `/Users/pr1ce/.hermes/tools/agent-browser-0.26.0-darwin-arm64/skill-data/core/SKILL.md` |
| create-hook | 2026-05-30 | >- | `/Users/pr1ce/.cursor/skills-cursor/create-hook/SKILL.md` |
| create-rule | 2026-05-30 | >- | `/Users/pr1ce/.cursor/skills-cursor/create-rule/SKILL.md` |
| create-skill | 2026-05-30 | >- | `/Users/pr1ce/.cursor/skills-cursor/create-skill/SKILL.md` |
| create-subagent | 2026-05-30 | >- | `/Users/pr1ce/.cursor/skills-cursor/create-subagent/SKILL.md` |
| docs | 2026-09-30 | 'docs (editable docs people share and comment on; the default for any document, named as a doc or not: a document, report, proposal, resu… | `/Users/pr1ce/.claude/skills/synced/cb27cbf1-5b75-49f6-8e4b-79f1da9dcfe8_d51e88b2-703c-429c-ad71-f0e2781bc331/docs/SKILL.md` |
| docx | 2026-09-30 | "Use this skill whenever the user wants to create, read, edit, or manipulate Word documents (.docx) or Word templates (.dotx). Triggers i… | `/Users/pr1ce/.claude/skills/synced/cb27cbf1-5b75-49f6-8e4b-79f1da9dcfe8_d51e88b2-703c-429c-ad71-f0e2781bc331/docx/SKILL.md` |
| dogfood | 1985-10-26 | Systematically explore and test a web application to find bugs, UX issues, and other problems. Use when asked to "dogfood", "QA", "explor… | `/Users/pr1ce/.hermes/tools/agent-browser-0.26.0-darwin-arm64/skill-data/dogfood/SKILL.md` |
| education-studio | 2026-09-27 | / | `/Users/pr1ce/.hub-global/skills/education-studio/SKILL.md` |
| ee-ecommerce-leads | 2026-09-29 | Add Estonian ecommerce companies to data/estonia/ee-ecommerce-leads.xlsx — e-Äriregister lookup, Google Maps phone, merged incorporation… | `/Users/pr1ce/Documents/Codex/Projects/uk-ecommerce-leads/.agents/skills/ee-ecommerce-leads/SKILL.md` |
| electron | 1985-10-26 | Automate Electron desktop apps (VS Code, Slack, Discord, Figma, Notion, Spotify, etc.) using agent-browser via Chrome DevTools Protocol.… | `/Users/pr1ce/.hermes/tools/agent-browser-0.26.0-darwin-arm64/skill-data/electron/SKILL.md` |
| external-agents | 2026-10-01 | "Use when the user wants another model to do or think about something: Claude Code, Codex, Grok (клод, кодекс, грок), 'лимиты сгорают', '… | `/Users/pr1ce/.hermes/claude/bots/odin/.claude/skills/external-agents/SKILL.md` |
| external-agents | 2026-10-01 | "Use when the user wants another model to do or think about something: Claude Code, Codex, Grok (клод, кодекс, грок), 'лимиты сгорают', '… | `/Users/pr1ce/.hermes/skills/hermes/external-agents/SKILL.md` |
| fastapi | 2026-09-25 | FastAPI best practices and conventions. Use when working with FastAPI APIs and Pydantic models for them. Keeps FastAPI code clean and up… | `/Users/pr1ce/.hermes/cache/uv/archive-v0/VXVDnOYQRcM8_Mry/fastapi/.agents/skills/fastapi/SKILL.md` |
| fleet-usage-cost | 2026-09-29 | Use for bot-team token-spend and PAYG cost estimates. | `/Users/pr1ce/.hermes/skills/hermes/fleet-usage-cost/SKILL.md` |
| google-calendar | 2026-08-10 | Google Calendar via local CLI — list upcoming events, create/update/delete, re-auth. Use when Owner asks about schedule, meetings, events… | `/Users/pr1ce/.kimi_openclaw/workspace/skills/google-calendar/SKILL.md` |
| google-calendar | 2026-10-01 | "Use for Google Calendar tasks: list, create, delete events." | `/Users/pr1ce/.hermes/claude/bots/heimdall/.claude/skills/google-calendar/SKILL.md` |
| google-workspace | 2026-09-29 | "Read this before the first Google Drive, Docs, Sheets or Slides connector call whenever the task creates or changes a Google file. Use t… | `/Users/pr1ce/.claude/skills/synced/cb27cbf1-5b75-49f6-8e4b-79f1da9dcfe8_d51e88b2-703c-429c-ad71-f0e2781bc331/google-workspace/SKILL.md` |
| google_meet | 2026-09-25 | Join a Google Meet call, transcribe live captions, optionally speak in realtime, and do the followup work afterwards. Use when the user a… | `/Users/pr1ce/.hermes/installs/422ab237c1451428/environments/89136ee4ddda4b83852d24ebe5cf8dab/workspace/plugins/google_meet/SKILL.md` |
| grok-plan | 2026-08-06 | Plan and build with Grok Build CLI as the heavy-code worker and Kimi as orchestrator. Use when the user invokes $grok-plan or /grok-plan,… | `/Users/pr1ce/.agents/skills/grok-plan/SKILL.md` |
| grok-worker | 2026-08-13 | Delegate well-specified bulk coding work to the Grok Build CLI as a headless worker while Kimi stays the orchestrator. Use when the user… | `/Users/pr1ce/.agents/skills/grok-worker/SKILL.md` |
| h3-prompt-expert | 2026-09-27 | / | `/Users/pr1ce/.hub-global/skills/h3-prompt-expert/SKILL.md` |
| h3-visual-design | 2026-09-27 | / | `/Users/pr1ce/.hub-global/skills/h3-visual-design/SKILL.md` |
| habit-watch | 2026-10-02 | "Use for the user's tracked daily habits (English speaking first): cron pings, check-ins, weekly reviews, short replies like +, done 15,… | `/Users/pr1ce/.hermes/claude/bots/heimdall/.claude/skills/habit-watch/SKILL.md` |
| handdrawn-live-video-generator | 2026-09-27 | / | `/Users/pr1ce/.hub-global/skills/handdrawn-live-video-generator/SKILL.md` |
| help | 2026-06-10 | — | `/Users/pr1ce/Projects/_archive/sdd-kit/skills/help/SKILL.md` |
| hermes-agent | 2026-09-25 | "Use, configure, theme, extend, and orchestrate Hermes Agent." | `/Users/pr1ce/.hermes/skills/autonomous-ai-agents/hermes-agent/SKILL.md` |
| hermes-bot-mode-setup | 2026-09-24 | Use when adding Hermes Bot Mode bots from the CLI. | `/Users/pr1ce/.hermes/skills/hermes/hermes-bot-mode-setup/SKILL.md` |
| imagegen | 2026-10-02 | "Generate or edit raster images when the task benefits from AI-created bitmap visuals such as photos, illustrations, textures, sprites, m… | `/Users/pr1ce/.codex/skills/.system/imagegen/SKILL.md` |
| import-memory | 2026-09-25 | Import a memory export from another AI assistant into Claude's memory — conversationally, additively, and with the content treated as data. | `/Users/pr1ce/.claude/skills/synced/cb27cbf1-5b75-49f6-8e4b-79f1da9dcfe8_d51e88b2-703c-429c-ad71-f0e2781bc331/import-memory/SKILL.md` |
| job-market-research | 2026-08-01 | Research, normalize, deduplicate, and compare European local and worldwide remote vacancies against a job seeker's experience, languages,… | `/Users/pr1ce/.codex/skills/job-market-research/SKILL.md` |
| kimi-desktop-gateway-policy | 2026-09-04 | / | `/Users/pr1ce/.kimi_openclaw/workspace/skills/kimi-desktop-gateway-policy/SKILL.md` |
| kimi-webbridge-desktop | 2026-08-14 | / | `/Users/pr1ce/.kimi_openclaw/workspace/skills/kimi-webbridge-desktop/SKILL.md` |
| kimiim | 2026-09-04 | Use this skill for any interaction with Kimi Group Chat or its Sessions, including reading Group Rules, checking members and recent messa… | `/Users/pr1ce/.kimi_openclaw/workspace/skills/kimiim/SKILL.md` |
| koc-video | 2026-09-27 | / | `/Users/pr1ce/.hub-global/skills/koc-video/SKILL.md` |
| launch-monitoring | 2026-10-01 | "Use when tracking rocket launches; quiet daily monitors." | `/Users/pr1ce/.hermes/claude/bots/huginn/.claude/skills/launch-monitoring/SKILL.md` |
| leads-table-analyzer | 2026-08-13 | Analyzes lead CSV exports, semantically groups arbitrary Sale Status values, sorts by Broker, Country, and status, converts UTC dates to… | `/Users/pr1ce/.cursor/skills/leads-table-analyzer/SKILL.md` |
| listen | 2026-08-18 | > | `/Users/pr1ce/.grok/skills/listen/SKILL.md` |
| loop | 2026-06-28 | >- | `/Users/pr1ce/.cursor/skills-cursor/loop/SKILL.md` |
| material-change-monitors | 2026-10-01 | "Use when a cron monitor must fire only on material change." | `/Users/pr1ce/.hermes/claude/bots/huginn/.claude/skills/material-change-monitors/SKILL.md` |
| micro-expression-video-generator | 2026-09-27 | / | `/Users/pr1ce/.hub-global/skills/micro-expression-video-generator/SKILL.md` |
| migrate-to-skills | 2026-05-30 | >- | `/Users/pr1ce/.cursor/skills-cursor/migrate-to-skills/SKILL.md` |
| minimalist-product-ad-generator | 2026-09-27 | Turn product images and selling points into a minimalist product ad with product anchors, concise copy, synced typography, and premium ca… | `/Users/pr1ce/.hub-global/skills/minimalist-product-ad-generator/SKILL.md` |
| moira | 2026-06-18 | Voice diary pipeline — every transcribed voice message becomes a diary entry via process_diary_voice, answered in Moira's voice. | `/Users/pr1ce/Projects/_archive/Dear Diary/deploy/moira/SKILL.md` |
| morning | 2026-09-25 | "Render the user's morning brief as a styled HTML artifact, or set it up as a recurring weekday task. Use only when the user explicitly a… | `/Users/pr1ce/.claude/skills/synced/cb27cbf1-5b75-49f6-8e4b-79f1da9dcfe8_d51e88b2-703c-429c-ad71-f0e2781bc331/morning/SKILL.md` |
| music-taste | 2026-09-01 | Personal music-taste chat with memory. Use when the user asks for music ("подбери музыку", "что послушать", "хочу похожее на..."), gives… | `/Users/pr1ce/Projects/music-taste/SKILL.md` |
| music-video-subtitle-generator | 2026-09-27 | / | `/Users/pr1ce/.hub-global/skills/music-video-subtitle-generator/SKILL.md` |
| notes-review | 2026-10-01 | "Use for the 🗂 notes review (Разбор заметок) and answers to it: numbers of notes that are no longer needed, «ок», archiving, deleting or… | `/Users/pr1ce/.hermes/claude/bots/muninn/.claude/skills/notes-review/SKILL.md` |
| onboard | 2026-07-03 | >- | `/Users/pr1ce/.cursor/skills-cursor/onboard/SKILL.md` |
| openai-docs | 2026-10-02 | "Use for Codex models/pricing, scheduled tasks, skills, settings, setup, troubleshooting, customization, automations, and self-knowledge—… | `/Users/pr1ce/.codex/skills/.system/openai-docs/SKILL.md` |
| paper-collage-explainer-generator | 2026-09-27 | Turn narration, story topics, or abstract ideas into a reviewed halftone paper-collage animation with tactile sound. Use for explainers a… | `/Users/pr1ce/.hub-global/skills/paper-collage-explainer-generator/SKILL.md` |
| pdf | 2026-09-25 | Use this skill whenever the user wants to do anything with PDF files. This includes reading or extracting text/tables from PDFs, combinin… | `/Users/pr1ce/.claude/skills/synced/cb27cbf1-5b75-49f6-8e4b-79f1da9dcfe8_d51e88b2-703c-429c-ad71-f0e2781bc331/pdf/SKILL.md` |
| permissioned-github | 2026-08-15 | Guidelines for interacting with GitHub and request permissions from the user when commands fail due to restrictions in the agent environm… | `/Users/pr1ce/.gemini/antigravity-ide/builtin/skills/permissioned-github/SKILL.md` |
| plan | 2026-06-10 | — | `/Users/pr1ce/Projects/_archive/sdd-kit/skills/plan/SKILL.md` |
| plan | 2026-08-01 | Turn a project idea into a compact executable implementation plan and hand it directly to coding. Use when the user invokes $plan or /pla… | `/Users/pr1ce/Documents/Codex/Projects/Coding/.agents/skills/plan/SKILL.md` |
| plan | 2026-08-04 | Turn a project idea into a compact executable implementation plan and hand it directly to coding. Use when the user invokes $plan or /pla… | `/Users/pr1ce/Documents/kimi/workspace/migration/agents-skills/plan/SKILL.md` |
| plan | 2026-08-06 | Turn a project idea into a compact executable implementation plan and hand it directly to coding. Use when the user invokes $plan or /pla… | `/Users/pr1ce/.agents/skills/plan/SKILL.md` |
| plan | 2026-10-01 | Turn a project idea into a compact executable implementation plan and hand it directly to coding. Use when the user invokes $plan or /pla… | `/Users/pr1ce/.claude/skills/plan/SKILL.md` |
| plugin-creator | 2026-10-02 | Create and scaffold plugin directories for Codex with a required '.codex-plugin/plugin.json', optional plugin folders/files, valid manife… | `/Users/pr1ce/.codex/skills/.system/plugin-creator/SKILL.md` |
| pptx | 2026-10-02 | "Use this skill any time a .pptx or .potx file is involved in any way — as input, output, or both. This includes: creating slide decks, p… | `/Users/pr1ce/.claude/skills/synced/cb27cbf1-5b75-49f6-8e4b-79f1da9dcfe8_d51e88b2-703c-429c-ad71-f0e2781bc331/pptx/SKILL.md` |
| reddit-reading | 2026-10-01 | "Read Reddit: subreddits, search, threads, users. No browser." | `/Users/pr1ce/.hermes/claude/bots/huginn/.claude/skills/reddit-reading/SKILL.md` |
| rename-chat | 2026-08-13 | >- | `/Users/pr1ce/.cursor/skills-cursor/rename-chat/SKILL.md` |
| research | 2026-08-18 | > | `/Users/pr1ce/.grok/skills/research/SKILL.md` |
| research-deck | 2026-08-16 | > | `/Users/pr1ce/.grok/skills/research-deck/SKILL.md` |
| retro | 2026-06-10 | — | `/Users/pr1ce/Projects/_archive/sdd-kit/skills/retro/SKILL.md` |
| review | 2026-06-09 | Review code changes with the Bugbot or Security Review subagent. | `/Users/pr1ce/.cursor/skills-cursor/review/SKILL.md` |
| review-agent | 2026-10-02 | Perform a read-only, defect-first review of a specified code change and return every actionable finding. Use when another agent delegates… | `/Users/pr1ce/.codex/skills/.system/review-agent/SKILL.md` |
| review-bugbot | 2026-07-16 | Review code changes with Bugbot subagent. | `/Users/pr1ce/.cursor/skills-cursor/review-bugbot/SKILL.md` |
| review-security | 2026-07-16 | Review code changes with Security Review subagent. | `/Users/pr1ce/.cursor/skills-cursor/review-security/SKILL.md` |
| rss-feeds | 2026-10-01 | "Read RSS, Atom, JSON feeds; discover feeds behind a page." | `/Users/pr1ce/.hermes/claude/bots/huginn/.claude/skills/rss-feeds/SKILL.md` |
| scan | 2026-06-10 | — | `/Users/pr1ce/Projects/_archive/sdd-kit/skills/scan/SKILL.md` |
| scheduled-research-monitoring | 2026-09-25 | Use for Hermes recurring research digests and feed monitors. | `/Users/pr1ce/.hermes/skills/hermes/scheduled-research-monitoring/SKILL.md` |
| scheduled-research-monitoring | 2026-10-01 | Use for recurring research digests and feed monitors (scheduled jobs of the bot team). | `/Users/pr1ce/.hermes/claude/bots/huginn/.claude/skills/scheduled-research-monitoring/SKILL.md` |
| scheduled-research-monitoring | 2026-10-01 | Use for recurring research digests and feed monitors (scheduled jobs of the bot team). | `/Users/pr1ce/.hermes/claude/bots/odin/.claude/skills/scheduled-research-monitoring/SKILL.md` |
| sdk | 2026-05-30 | >- | `/Users/pr1ce/.cursor/skills-cursor/sdk/SKILL.md` |
| shell | 2026-05-30 | >- | `/Users/pr1ce/.cursor/skills-cursor/shell/SKILL.md` |
| skill-creator | 2026-09-25 | Create new skills, modify and improve existing skills, and measure skill performance. Use when users want to create a skill from scratch,… | `/Users/pr1ce/.claude/skills/synced/cb27cbf1-5b75-49f6-8e4b-79f1da9dcfe8_d51e88b2-703c-429c-ad71-f0e2781bc331/skill-creator/SKILL.md` |
| skill-creator | 2026-09-27 | / | `/Users/pr1ce/.hub-global/skills/skill-creator/SKILL.md` |
| skill-creator | 2026-10-02 | Create or update a Codex skill with appropriately scoped instructions and any needed supporting resources. | `/Users/pr1ce/.codex/skills/.system/skill-creator/SKILL.md` |
| skill-installer | 2026-10-02 | Install Codex skills into $CODEX_HOME/skills from a curated list or a GitHub repo path. Use when a user asks to list installable skills,… | `/Users/pr1ce/.codex/skills/.system/skill-installer/SKILL.md` |
| skill-reviewer | 2026-09-27 | / | `/Users/pr1ce/.hub-global/skills/skill-reviewer/SKILL.md` |
| slack | 1985-10-26 | Interact with Slack workspaces using browser automation. Use when the user needs to check unread channels, navigate Slack, send messages,… | `/Users/pr1ce/.hermes/tools/agent-browser-0.26.0-darwin-arm64/skill-data/slack/SKILL.md` |
| song-read | 2026-08-18 | > | `/Users/pr1ce/.grok/skills/song-read/SKILL.md` |
| spec | 2026-06-10 | — | `/Users/pr1ce/Projects/_archive/sdd-kit/skills/spec/SKILL.md` |
| split-to-prs | 2026-05-30 | >- | `/Users/pr1ce/.cursor/skills-cursor/split-to-prs/SKILL.md` |
| start | 2026-06-10 | — | `/Users/pr1ce/Projects/_archive/sdd-kit/skills/start/SKILL.md` |
| start | 2026-08-01 | Create a named AI coding project under a Projects directory with bounded SOUL.md memory, an executable notes/PLAN.md, Obsidian-ready note… | `/Users/pr1ce/.agents/skills/start/SKILL.md` |
| start | 2026-08-01 | Create a named AI coding project under a Projects directory with bounded SOUL.md memory, an executable notes/PLAN.md, Obsidian-ready note… | `/Users/pr1ce/.claude/skills/start/SKILL.md` |
| start | 2026-08-01 | Create a named AI coding project under a Projects directory with bounded SOUL.md memory, an executable notes/PLAN.md, Obsidian-ready note… | `/Users/pr1ce/Documents/Codex/Projects/Coding/.agents/skills/start/SKILL.md` |
| start | 2026-08-04 | Create a named AI coding project under a Projects directory with bounded SOUL.md memory, an executable notes/PLAN.md, Obsidian-ready note… | `/Users/pr1ce/Documents/kimi/workspace/migration/agents-skills/start/SKILL.md` |
| status | 2026-06-10 | — | `/Users/pr1ce/Projects/_archive/sdd-kit/skills/status/SKILL.md` |
| statusline | 2026-05-30 | >- | `/Users/pr1ce/.cursor/skills-cursor/statusline/SKILL.md` |
| study-note | 2026-06-08 | >- | `/Users/pr1ce/.claude/skills/study-note/SKILL.md` |
| swiss-ecommerce-leads | 2026-07-31 | Find and qualify Swiss GmbH businesses that are plausible ecommerce prospects. Use for requests to research Swiss companies, exclude medi… | `/Users/pr1ce/.codex/skills/swiss-ecommerce-leads/SKILL.md` |
| time-awareness | 2026-09-04 | — | `/Users/pr1ce/.kimi_openclaw/workspace/skills/time-awareness/SKILL.md` |
| track-personal-budget | 2026-08-10 | Personal Thailand budget — cash THB, UAH card, Binance savings. Use when Owner reports balances, expenses, income, daily THB budget to mo… | `/Users/pr1ce/.kimi_openclaw/workspace/skills/track-personal-budget/SKILL.md` |
| track-personal-budget | 2026-10-01 | Вести личный бюджет в Таиланде — траты по гривневой карте monobank подтягиваются автоматически, наличные THB и Binance учитываются вручну… | `/Users/pr1ce/.hermes/claude/bots/andvari/.claude/skills/track-personal-budget/SKILL.md` |
| track-personal-budget | 2026-10-01 | Вести личный бюджет в Таиланде — траты по гривневой карте monobank подтягиваются автоматически, наличные THB и Binance учитываются вручну… | `/Users/pr1ce/Documents/Codex/Projects/Life/.agents/skills/track-personal-budget/SKILL.md` |
| trello | 2026-08-10 | Trello kanban via local CLI using macOS Keychain credentials (same as Codex trello-add-task). List boards/cards, add/move/archive. Defaul… | `/Users/pr1ce/.kimi_openclaw/workspace/skills/trello/SKILL.md` |
| trello-add-task | 2026-08-27 | Add a single task/card to the user's Trello boards through Trello REST API. Use when the user says to add, create, записать, поставить, o… | `/Users/pr1ce/Documents/Codex/Projects/Life/.agents/skills/trello-add-task/SKILL.md` |
| trip-day-planning | 2026-10-01 | "Trip planning: tours, pickups, sleep, packing, weather." | `/Users/pr1ce/.hermes/claude/bots/muninn/.claude/skills/trip-day-planning/SKILL.md` |
| ui-motion | 2026-09-27 | / | `/Users/pr1ce/.hub-global/skills/ui-motion/SKILL.md` |
| uk-ecommerce-leads | 2026-09-29 | Add UK ecommerce companies to data/uk-ecommerce-leads.xlsx — Companies House lookup, Google Maps phone, NEWINC incorporation PDF. Use whe… | `/Users/pr1ce/Documents/Codex/Projects/uk-ecommerce-leads/.agents/skills/uk-ecommerce-leads/SKILL.md` |
| update-cli-config | 2026-08-13 | >- | `/Users/pr1ce/.cursor/skills-cursor/update-cli-config/SKILL.md` |
| update-cursor-settings | 2026-05-30 | >- | `/Users/pr1ce/.cursor/skills-cursor/update-cursor-settings/SKILL.md` |
| usage-hub | 2026-10-01 | "Use for the user's paid AI services in one place: subscription limits (Claude, ChatGPT/Codex, Grok Build, GLM), API balances and spend (… | `/Users/pr1ce/.hermes/claude/bots/odin/.claude/skills/usage-hub/SKILL.md` |
| usage-hub | 2026-10-01 | "Use for the user's paid AI services in one place: subscription limits (Claude, ChatGPT/Codex, Grok Build, GLM), API balances and spend (… | `/Users/pr1ce/.hermes/skills/hermes/usage-hub/SKILL.md` |
| vercel-sandbox | 1985-10-26 | Run agent-browser + Chrome inside Vercel Sandbox microVMs for browser automation from any Vercel-deployed app. Use when the user needs br… | `/Users/pr1ce/.hermes/tools/agent-browser-0.26.0-darwin-arm64/skill-data/vercel-sandbox/SKILL.md` |
| vibe-coder | 2026-08-04 | The user's battle-tested start-plan-build-change coding workflow (migrated from Codex/Hermes ~/.agents/skills). Use when the user says "$… | `/Users/pr1ce/.agents/skills/vibe-coder/SKILL.md` |
| video-deconstruct | 2026-09-27 | / | `/Users/pr1ce/.hub-global/skills/video-deconstruct/SKILL.md` |
| voice-clone | 2026-09-27 | / | `/Users/pr1ce/.hub-global/skills/voice-clone/SKILL.md` |
| voice-persona | 2026-07-27 | Generate a compact English persona prompt for conversational English practice in a new ChatGPT Voice chat. Use when the user invokes $voi… | `/Users/pr1ce/Documents/Codex/Projects/Life/.agents/skills/voice-persona/SKILL.md` |
| voiceops | 2026-07-27 | Generate compact prompts for spoken-English lessons in ordinary ChatGPT Voice, analyze pasted Voice transcripts, maintain durable B1-to-B… | `/Users/pr1ce/Documents/Codex/Projects/Life/.agents/skills/voiceops/SKILL.md` |
| voiceops-analysis | 2026-07-27 | Generate compact prompts for spoken-English lessons in ordinary ChatGPT Voice, analyze pasted Voice transcripts, maintain durable B1-to-B… | `/Users/pr1ce/Documents/Codex/2026-07-27/new-chat-4/work/forward-test/voiceops-analysis/SKILL.md` |
| watchers | 2026-10-01 | Poll RSS, JSON APIs, and GitHub with watermark dedup. | `/Users/pr1ce/.hermes/claude/bots/huginn/.claude/skills/watchers/SKILL.md` |
| worker-safety | 2026-09-04 | — | `/Users/pr1ce/.kimi_openclaw/workspace/skills/worker-safety/SKILL.md` |
| xlsx | 2026-09-25 | "Use this skill any time a spreadsheet file is the primary input or output. This means any task where the user wants to: open, read, edit… | `/Users/pr1ce/.claude/skills/synced/cb27cbf1-5b75-49f6-8e4b-79f1da9dcfe8_d51e88b2-703c-429c-ad71-f0e2781bc331/xlsx/SKILL.md` |
