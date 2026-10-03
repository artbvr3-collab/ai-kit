# Audit brief: <project>

Template for a project's `notes/audit.md`. The `audit` skill reads it before anything else and hands the rules below to every agent word for word. Keep it short; delete sections that do not apply.

## What this is
One or two sentences: what runs, where, since when, whether it is live.

## Threat model
- Who is untrusted (for an LLM bot: the model after it has read web pages, forwards, files).
- What must not happen: which secrets, whose private data, which actions.
- What is out of scope (for example: other local users, physical access).

## Never open or print
Paths and globs: `.env`, `secrets/`, chat history, databases, media, private data folders. Listing names and modes is fine unless said otherwise.

## Never run
Services, gateways, jobs, anything that sends a message or calls an API, service control (`launchctl`, restarts).

## Safe to run
Read-only commands that give live facts without opening private data: listening ports, firewall state, file modes, counts by type.

## Scratch testing
Env vars or flags that point the code at a scratch root or a fake API. Pure modules that are safe to copy and run on made-up inputs.

## Boundaries: in code or only in the prompt
For each isolation claim ("bot A cannot read B's data"): where it is enforced, or that it is only an instruction to the model. All components run as one OS user? Say so.

## Accepted risks and known false positives
What earlier audits reported and I decided to keep, or that turned out wrong, with the date and the reason.

## Reports
Where reports go (`notes/audits/<date>.md`), whether they are committed, whether the repo has a remote.
