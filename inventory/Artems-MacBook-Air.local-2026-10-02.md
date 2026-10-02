# AI-kit inventory — Artems-MacBook-Air.local — 2026-10-02

Regenerated after the INVENTORY.md update: skills split bundled/custom.
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

Total `SKILL.md` under `$HOME`: **2013** under the INVENTORY.md skip rules (excluding `~/Library`, `.cache`, `.npm`, `node_modules`; raw count including those: 2946); counts drift a few files between runs because tool caches are live. Split by origin below.

### 3a. Bundled skills — one line per source

| Source | Count |
|---|---|
| Hermes internal (`~/.hermes/{profiles,hermes-agent,claude}`; engine source + per-profile copies) | 479 |
| ZCode official plugin cache (`~/.zcode/cli`) | 79 |
| Grok bundled (`~/.grok/bundled`) | 22 |
| Grok marketplace cache (`~/.grok/marketplace-cache`) | 36 |
| Claude Code plugin cache (`~/.claude/plugins`) | 31 |
| Cursor bundled (`~/.cursor/skills-cursor`) | 20 |
| hub-global catalog (`~/.hub-global/skills`, media-generation pack; unsure — could be user-installed) | 20 |
| Codex plugin cache (`~/.codex/plugins`) | 17 |
| Claude Code plugin-synced (`~/.claude/skills/synced`) | 9 |
| agent-browser vendored binaries (`~/.hermes/tools`) | 7 |
| Codex system skills (`~/.codex/skills/.system`) | 6 |
| Antigravity built-in (`~/.gemini/antigravity-ide`) | 3 |

Junk not attributable to a source: `~/.codex/.tmp` (616 temp files), OpenClaw residue (605).

The three `skill-creator` copies (claude-synced / codex-system / hub) differ from each other, but each is stock for its tool; no locally modified bundled skill was detected (uniform unpack dates).

### 3b. Custom skills — 83

Written by the user or their agents. The 19 Hermes entries under `~/.hermes/claude/bots/` are deployed copies of custom skills (they drift from sources); Kimi workspace skills are marked unsure. Full list in the Appendix.

Duplicate groups (whole-folder hash across all user-area skills):

| Skill | Copies | Verdict |
|---|---|---|
| `agenda` | Hermes bot copy `.hermes/claude/bots/heimdall/.claude/skills/agenda`; Hermes bot copy `.hermes/claude/bots/odin/.claude/skills/agenda` | differ |
| `bot-team-delegation` | Hermes bot copy `.hermes/claude/bots/odin/.claude/skills/bot-team-delegation`; Hermes (source) `.hermes/skills/hermes/bot-team-delegation` | differ |
| `build` | shared ~/.agents (ZCode) `.agents/skills/build`; Claude Code `.claude/skills/build`; project Coding `Documents/Codex/Projects/Coding/.agents/skills/build`; Kimi migration leftover `Documents/kimi/workspace/migration/agents-skills/build`; project _archive `Projects/_archive/sdd-kit/skills/build` | differ — the `~/.claude` copy is newer (01.10) and semantically evolved |
| `change` | shared ~/.agents (ZCode) `.agents/skills/change`; Claude Code `.claude/skills/change`; project Coding `Documents/Codex/Projects/Coding/.agents/skills/change`; Kimi migration leftover `Documents/kimi/workspace/migration/agents-skills/change`; project _archive `Projects/_archive/sdd-kit/skills/change` | differ — 4 copies identical, sdd-kit copy older |
| `external-agents` | Hermes bot copy `.hermes/claude/bots/odin/.claude/skills/external-agents`; Hermes (source) `.hermes/skills/hermes/external-agents` | differ |
| `google-calendar` | Hermes bot copy `.hermes/claude/bots/heimdall/.claude/skills/google-calendar`; Kimi (unsure) `.kimi_openclaw/workspace/skills/google-calendar` | differ |
| `plan` | shared ~/.agents (ZCode) `.agents/skills/plan`; Claude Code `.claude/skills/plan`; project Coding `Documents/Codex/Projects/Coding/.agents/skills/plan`; Kimi migration leftover `Documents/kimi/workspace/migration/agents-skills/plan`; project _archive `Projects/_archive/sdd-kit/skills/plan` | differ — the `~/.claude` copy is newer (01.10) and semantically evolved |
| `scheduled-research-monitoring` | Hermes bot copy `.hermes/claude/bots/huginn/.claude/skills/scheduled-research-monitoring`; Hermes bot copy `.hermes/claude/bots/odin/.claude/skills/scheduled-research-monitoring`; Hermes (source) `.hermes/skills/hermes/scheduled-research-monitoring` | differ |
| `skill-creator` | Claude Code `.claude/skills/synced/cb27cbf1-5b75-49f6-8e4b-79f1da9dcfe8_d51e88b2-703c-429c-ad71-f0e2781bc331/skill-creator`; Codex `.codex/skills/.system/skill-creator`; — `.hub-global/skills/skill-creator` | differ |
| `start` | shared ~/.agents (ZCode) `.agents/skills/start`; Claude Code `.claude/skills/start`; project Coding `Documents/Codex/Projects/Coding/.agents/skills/start`; Kimi migration leftover `Documents/kimi/workspace/migration/agents-skills/start`; project _archive `Projects/_archive/sdd-kit/skills/start` | differ — SKILL.md identical in `~/.agents`/`~/.claude`, supporting files differ |
| `track-personal-budget` | Hermes bot copy `.hermes/claude/bots/andvari/.claude/skills/track-personal-budget`; Kimi (unsure) `.kimi_openclaw/workspace/skills/track-personal-budget`; project Life `Documents/Codex/Projects/Life/.agents/skills/track-personal-budget` | differ |
| `usage-hub` | Hermes bot copy `.hermes/claude/bots/odin/.claude/skills/usage-hub`; Hermes (source) `.hermes/skills/hermes/usage-hub` | differ |

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

## Appendix — custom skills (83)

| Name | Modified | Owner | Description | Path |
|---|---|---|---|---|
| agenda | 2026-10-01 | Hermes bot copy | "Use for the user's tasks and to-dos (дела, задачи, не забыть, напомни, проконтролируй, зачекиниться), controlled tasks and answers to 🎯… | `.hermes/claude/bots/heimdall/.claude/skills/agenda/SKILL.md` |
| agenda | 2026-10-01 | Hermes bot copy | "Use for the user's tasks and to-dos (дела, задачи, не забыть, напомни, проконтролируй, зачекиниться), controlled tasks and answers to 🎯… | `.hermes/claude/bots/odin/.claude/skills/agenda/SKILL.md` |
| ai-release-deep-dive | 2026-10-01 | Hermes bot copy | "Use when a user asks to dig into an AI model release." | `.hermes/claude/bots/huginn/.claude/skills/ai-release-deep-dive/SKILL.md` |
| apple-availability-th | 2026-10-01 | Hermes bot copy | "Use when asked when Apple products go on sale in Thailand." | `.hermes/claude/bots/huginn/.claude/skills/apple-availability-th/SKILL.md` |
| booklab-run | 2026-08-31 | project booklab | Run a new book through the booklab pipeline (inbox -> import -> probe TTS -> full TTS run -> site rebuild). Use when the user drops new E… | `Projects/booklab/.agents/skills/booklab-run/SKILL.md` |
| bot-team-delegation | 2026-10-01 | Hermes bot copy | Use when routing a task to a team bot or one-shot pings. | `.hermes/claude/bots/odin/.claude/skills/bot-team-delegation/SKILL.md` |
| bot-team-delegation | 2026-09-30 | Hermes (source) | Use when routing a task to a team bot or one-shot pings. | `.hermes/skills/hermes/bot-team-delegation/SKILL.md` |
| bridge-broker-geo | 2026-07-31 | Codex | "Анализировать эффективность CRM-брокеров внутри одного Bridge GEO: сравнивать CR, EPL и текущие Sale Status за сегодня, неделю с понедел… | `.codex/skills/bridge-broker-geo/SKILL.md` |
| build | 2026-08-01 | shared ~/.agents (ZCode) | Implement the next verified step from notes/PLAN.md immediately after planning. Use when the user invokes $build or /build, says "собирае… | `.agents/skills/build/SKILL.md` |
| build | 2026-10-01 | Claude Code | Implement notes/PLAN.md after planning. Use when the user invokes $build or /build, says "собираем", "погнали кодить", "следующий шаг", "… | `.claude/skills/build/SKILL.md` |
| build | 2026-08-01 | project Coding | Implement the next verified step from notes/PLAN.md immediately after planning. Use when the user invokes $build or /build, says "собирае… | `Documents/Codex/Projects/Coding/.agents/skills/build/SKILL.md` |
| build | 2026-08-04 | Kimi migration leftover | Implement the next verified step from notes/PLAN.md immediately after planning. Use when the user invokes $build or /build, says "собирае… | `Documents/kimi/workspace/migration/agents-skills/build/SKILL.md` |
| build | 2026-06-10 | project _archive | — | `Projects/_archive/sdd-kit/skills/build/SKILL.md` |
| ch-ecommerce-leads | 2026-09-29 | project uk-ecommerce-leads | Add Swiss ecommerce companies to data/switzerland/ch-ecommerce-leads.xlsx — Zefix lookup, Google Maps phone, Zefix link instead of a PDF.… | `Documents/Codex/Projects/uk-ecommerce-leads/.agents/skills/ch-ecommerce-leads/SKILL.md` |
| change | 2026-08-01 | shared ~/.agents (ZCode) | Modify an existing project according to the change's real code blast radius. Use when the user invokes $change or /change, or says "попра… | `.agents/skills/change/SKILL.md` |
| change | 2026-08-01 | Claude Code | Modify an existing project according to the change's real code blast radius. Use when the user invokes $change or /change, or says "попра… | `.claude/skills/change/SKILL.md` |
| change | 2026-08-01 | project Coding | Modify an existing project according to the change's real code blast radius. Use when the user invokes $change or /change, or says "попра… | `Documents/Codex/Projects/Coding/.agents/skills/change/SKILL.md` |
| change | 2026-08-04 | Kimi migration leftover | Modify an existing project according to the change's real code blast radius. Use when the user invokes $change or /change, or says "попра… | `Documents/kimi/workspace/migration/agents-skills/change/SKILL.md` |
| change | 2026-06-10 | project _archive | — | `Projects/_archive/sdd-kit/skills/change/SKILL.md` |
| claude-chat-watcher | 2026-09-29 | Hermes (source) | Use when asked to check or recap a local Claude Code chat. | `.hermes/skills/claude-chat-watcher/SKILL.md` |
| ee-ecommerce-leads | 2026-09-29 | project uk-ecommerce-leads | Add Estonian ecommerce companies to data/estonia/ee-ecommerce-leads.xlsx — e-Äriregister lookup, Google Maps phone, merged incorporation… | `Documents/Codex/Projects/uk-ecommerce-leads/.agents/skills/ee-ecommerce-leads/SKILL.md` |
| external-agents | 2026-10-01 | Hermes bot copy | "Use when the user wants another model to do or think about something: Claude Code, Codex, Grok (клод, кодекс, грок), 'лимиты сгорают', '… | `.hermes/claude/bots/odin/.claude/skills/external-agents/SKILL.md` |
| external-agents | 2026-10-01 | Hermes (source) | "Use when the user wants another model to do or think about something: Claude Code, Codex, Grok (клод, кодекс, грок), 'лимиты сгорают', '… | `.hermes/skills/hermes/external-agents/SKILL.md` |
| fleet-usage-cost | 2026-09-29 | Hermes (source) | Use for bot-team token-spend and PAYG cost estimates. | `.hermes/skills/hermes/fleet-usage-cost/SKILL.md` |
| google-calendar | 2026-10-01 | Hermes bot copy | "Use for Google Calendar tasks: list, create, delete events." | `.hermes/claude/bots/heimdall/.claude/skills/google-calendar/SKILL.md` |
| google-calendar | 2026-08-10 | Kimi (unsure) | Google Calendar via local CLI — list upcoming events, create/update/delete, re-auth. Use when Owner asks about schedule, meetings, events… | `.kimi_openclaw/workspace/skills/google-calendar/SKILL.md` |
| grok-plan | 2026-08-06 | shared ~/.agents (ZCode) | Plan and build with Grok Build CLI as the heavy-code worker and Kimi as orchestrator. Use when the user invokes $grok-plan or /grok-plan,… | `.agents/skills/grok-plan/SKILL.md` |
| grok-worker | 2026-08-13 | shared ~/.agents (ZCode) | Delegate well-specified bulk coding work to the Grok Build CLI as a headless worker while Kimi stays the orchestrator. Use when the user… | `.agents/skills/grok-worker/SKILL.md` |
| habit-watch | 2026-10-02 | Hermes bot copy | "Use for the user's tracked daily habits (English speaking first): cron pings, check-ins, weekly reviews, short replies like +, done 15,… | `.hermes/claude/bots/heimdall/.claude/skills/habit-watch/SKILL.md` |
| help | 2026-06-10 | project _archive | — | `Projects/_archive/sdd-kit/skills/help/SKILL.md` |
| hermes-agent | 2026-09-25 | Hermes (source) | "Use, configure, theme, extend, and orchestrate Hermes Agent." | `.hermes/skills/autonomous-ai-agents/hermes-agent/SKILL.md` |
| hermes-bot-mode-setup | 2026-09-24 | Hermes (source) | Use when adding Hermes Bot Mode bots from the CLI. | `.hermes/skills/hermes/hermes-bot-mode-setup/SKILL.md` |
| job-market-research | 2026-08-01 | Codex | Research, normalize, deduplicate, and compare European local and worldwide remote vacancies against a job seeker's experience, languages,… | `.codex/skills/job-market-research/SKILL.md` |
| kimi-desktop-gateway-policy | 2026-09-04 | Kimi (unsure) | / | `.kimi_openclaw/workspace/skills/kimi-desktop-gateway-policy/SKILL.md` |
| kimi-webbridge-desktop | 2026-08-14 | Kimi (unsure) | / | `.kimi_openclaw/workspace/skills/kimi-webbridge-desktop/SKILL.md` |
| kimiim | 2026-09-04 | Kimi (unsure) | Use this skill for any interaction with Kimi Group Chat or its Sessions, including reading Group Rules, checking members and recent messa… | `.kimi_openclaw/workspace/skills/kimiim/SKILL.md` |
| launch-monitoring | 2026-10-01 | Hermes bot copy | "Use when tracking rocket launches; quiet daily monitors." | `.hermes/claude/bots/huginn/.claude/skills/launch-monitoring/SKILL.md` |
| leads-table-analyzer | 2026-08-13 | Cursor | Analyzes lead CSV exports, semantically groups arbitrary Sale Status values, sorts by Broker, Country, and status, converts UTC dates to… | `.cursor/skills/leads-table-analyzer/SKILL.md` |
| listen | 2026-08-18 | Grok CLI | > | `.grok/skills/listen/SKILL.md` |
| material-change-monitors | 2026-10-01 | Hermes bot copy | "Use when a cron monitor must fire only on material change." | `.hermes/claude/bots/huginn/.claude/skills/material-change-monitors/SKILL.md` |
| moira | 2026-06-18 | project _archive | Voice diary pipeline — every transcribed voice message becomes a diary entry via process_diary_voice, answered in Moira's voice. | `Projects/_archive/Dear Diary/deploy/moira/SKILL.md` |
| music-taste | 2026-09-01 | project music-taste | Personal music-taste chat with memory. Use when the user asks for music ("подбери музыку", "что послушать", "хочу похожее на..."), gives… | `Projects/music-taste/SKILL.md` |
| notes-review | 2026-10-01 | Hermes bot copy | "Use for the 🗂 notes review (Разбор заметок) and answers to it: numbers of notes that are no longer needed, «ок», archiving, deleting or… | `.hermes/claude/bots/muninn/.claude/skills/notes-review/SKILL.md` |
| plan | 2026-08-06 | shared ~/.agents (ZCode) | Turn a project idea into a compact executable implementation plan and hand it directly to coding. Use when the user invokes $plan or /pla… | `.agents/skills/plan/SKILL.md` |
| plan | 2026-10-01 | Claude Code | Turn a project idea into a compact executable implementation plan and hand it directly to coding. Use when the user invokes $plan or /pla… | `.claude/skills/plan/SKILL.md` |
| plan | 2026-08-01 | project Coding | Turn a project idea into a compact executable implementation plan and hand it directly to coding. Use when the user invokes $plan or /pla… | `Documents/Codex/Projects/Coding/.agents/skills/plan/SKILL.md` |
| plan | 2026-08-04 | Kimi migration leftover | Turn a project idea into a compact executable implementation plan and hand it directly to coding. Use when the user invokes $plan or /pla… | `Documents/kimi/workspace/migration/agents-skills/plan/SKILL.md` |
| plan | 2026-06-10 | project _archive | — | `Projects/_archive/sdd-kit/skills/plan/SKILL.md` |
| reddit-reading | 2026-10-01 | Hermes bot copy | "Read Reddit: subreddits, search, threads, users. No browser." | `.hermes/claude/bots/huginn/.claude/skills/reddit-reading/SKILL.md` |
| research | 2026-08-18 | Grok CLI | > | `.grok/skills/research/SKILL.md` |
| research-deck | 2026-08-16 | Grok CLI | > | `.grok/skills/research-deck/SKILL.md` |
| retro | 2026-06-10 | project _archive | — | `Projects/_archive/sdd-kit/skills/retro/SKILL.md` |
| rss-feeds | 2026-10-01 | Hermes bot copy | "Read RSS, Atom, JSON feeds; discover feeds behind a page." | `.hermes/claude/bots/huginn/.claude/skills/rss-feeds/SKILL.md` |
| scan | 2026-06-10 | project _archive | — | `Projects/_archive/sdd-kit/skills/scan/SKILL.md` |
| scheduled-research-monitoring | 2026-10-01 | Hermes bot copy | Use for recurring research digests and feed monitors (scheduled jobs of the bot team). | `.hermes/claude/bots/huginn/.claude/skills/scheduled-research-monitoring/SKILL.md` |
| scheduled-research-monitoring | 2026-10-01 | Hermes bot copy | Use for recurring research digests and feed monitors (scheduled jobs of the bot team). | `.hermes/claude/bots/odin/.claude/skills/scheduled-research-monitoring/SKILL.md` |
| scheduled-research-monitoring | 2026-09-25 | Hermes (source) | Use for Hermes recurring research digests and feed monitors. | `.hermes/skills/hermes/scheduled-research-monitoring/SKILL.md` |
| song-read | 2026-08-18 | Grok CLI | > | `.grok/skills/song-read/SKILL.md` |
| spec | 2026-06-10 | project _archive | — | `Projects/_archive/sdd-kit/skills/spec/SKILL.md` |
| start | 2026-08-01 | shared ~/.agents (ZCode) | Create a named AI coding project under a Projects directory with bounded SOUL.md memory, an executable notes/PLAN.md, Obsidian-ready note… | `.agents/skills/start/SKILL.md` |
| start | 2026-08-01 | Claude Code | Create a named AI coding project under a Projects directory with bounded SOUL.md memory, an executable notes/PLAN.md, Obsidian-ready note… | `.claude/skills/start/SKILL.md` |
| start | 2026-08-01 | project Coding | Create a named AI coding project under a Projects directory with bounded SOUL.md memory, an executable notes/PLAN.md, Obsidian-ready note… | `Documents/Codex/Projects/Coding/.agents/skills/start/SKILL.md` |
| start | 2026-08-04 | Kimi migration leftover | Create a named AI coding project under a Projects directory with bounded SOUL.md memory, an executable notes/PLAN.md, Obsidian-ready note… | `Documents/kimi/workspace/migration/agents-skills/start/SKILL.md` |
| start | 2026-06-10 | project _archive | — | `Projects/_archive/sdd-kit/skills/start/SKILL.md` |
| status | 2026-06-10 | project _archive | — | `Projects/_archive/sdd-kit/skills/status/SKILL.md` |
| study-note | 2026-06-08 | Claude Code | >- | `.claude/skills/study-note/SKILL.md` |
| swiss-ecommerce-leads | 2026-07-31 | Codex | Find and qualify Swiss GmbH businesses that are plausible ecommerce prospects. Use for requests to research Swiss companies, exclude medi… | `.codex/skills/swiss-ecommerce-leads/SKILL.md` |
| time-awareness | 2026-09-04 | Kimi (unsure) | — | `.kimi_openclaw/workspace/skills/time-awareness/SKILL.md` |
| track-personal-budget | 2026-10-01 | Hermes bot copy | Вести личный бюджет в Таиланде — траты по гривневой карте monobank подтягиваются автоматически, наличные THB и Binance учитываются вручну… | `.hermes/claude/bots/andvari/.claude/skills/track-personal-budget/SKILL.md` |
| track-personal-budget | 2026-08-10 | Kimi (unsure) | Personal Thailand budget — cash THB, UAH card, Binance savings. Use when Owner reports balances, expenses, income, daily THB budget to mo… | `.kimi_openclaw/workspace/skills/track-personal-budget/SKILL.md` |
| track-personal-budget | 2026-10-01 | project Life | Вести личный бюджет в Таиланде — траты по гривневой карте monobank подтягиваются автоматически, наличные THB и Binance учитываются вручну… | `Documents/Codex/Projects/Life/.agents/skills/track-personal-budget/SKILL.md` |
| trello | 2026-08-10 | Kimi (unsure) | Trello kanban via local CLI using macOS Keychain credentials (same as Codex trello-add-task). List boards/cards, add/move/archive. Defaul… | `.kimi_openclaw/workspace/skills/trello/SKILL.md` |
| trello-add-task | 2026-08-27 | project Life | Add a single task/card to the user's Trello boards through Trello REST API. Use when the user says to add, create, записать, поставить, o… | `Documents/Codex/Projects/Life/.agents/skills/trello-add-task/SKILL.md` |
| trip-day-planning | 2026-10-01 | Hermes bot copy | "Trip planning: tours, pickups, sleep, packing, weather." | `.hermes/claude/bots/muninn/.claude/skills/trip-day-planning/SKILL.md` |
| uk-ecommerce-leads | 2026-09-29 | project uk-ecommerce-leads | Add UK ecommerce companies to data/uk-ecommerce-leads.xlsx — Companies House lookup, Google Maps phone, NEWINC incorporation PDF. Use whe… | `Documents/Codex/Projects/uk-ecommerce-leads/.agents/skills/uk-ecommerce-leads/SKILL.md` |
| usage-hub | 2026-10-01 | Hermes bot copy | "Use for the user's paid AI services in one place: subscription limits (Claude, ChatGPT/Codex, Grok Build, GLM), API balances and spend (… | `.hermes/claude/bots/odin/.claude/skills/usage-hub/SKILL.md` |
| usage-hub | 2026-10-01 | Hermes (source) | "Use for the user's paid AI services in one place: subscription limits (Claude, ChatGPT/Codex, Grok Build, GLM), API balances and spend (… | `.hermes/skills/hermes/usage-hub/SKILL.md` |
| vibe-coder | 2026-08-04 | shared ~/.agents (ZCode) | The user's battle-tested start-plan-build-change coding workflow (migrated from Codex/Hermes ~/.agents/skills). Use when the user says "$… | `.agents/skills/vibe-coder/SKILL.md` |
| voice-persona | 2026-07-27 | project Life | Generate a compact English persona prompt for conversational English practice in a new ChatGPT Voice chat. Use when the user invokes $voi… | `Documents/Codex/Projects/Life/.agents/skills/voice-persona/SKILL.md` |
| voiceops | 2026-07-27 | project Life | Generate compact prompts for spoken-English lessons in ordinary ChatGPT Voice, analyze pasted Voice transcripts, maintain durable B1-to-B… | `Documents/Codex/Projects/Life/.agents/skills/voiceops/SKILL.md` |
| voiceops-analysis | 2026-07-27 | Codex chat leftover | Generate compact prompts for spoken-English lessons in ordinary ChatGPT Voice, analyze pasted Voice transcripts, maintain durable B1-to-B… | `Documents/Codex/2026-07-27/new-chat-4/work/forward-test/voiceops-analysis/SKILL.md` |
| watchers | 2026-10-01 | Hermes bot copy | Poll RSS, JSON APIs, and GitHub with watermark dedup. | `.hermes/claude/bots/huginn/.claude/skills/watchers/SKILL.md` |
| worker-safety | 2026-09-04 | Kimi (unsure) | — | `.kimi_openclaw/workspace/skills/worker-safety/SKILL.md` |
