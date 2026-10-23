# charly-core — retired

> **RETIRED — this repo publishes nothing.** All 15 `core`-family skills live in the
> repo that holds the code, plugin or config each one documents (the table below).
> Nothing is authored, built, deployed or consumed here: a change to a `core`-family
> skill is a change at its destination repo, in the same pull request as the entity it
> documents.

**This repo no longer authors a skill.** It was the `charly-core` concept candy: a `true`-no-op `plan:` and 15 `skill:` entities, with the prose in `.agents/skills/`.
Under `AGENTS.md` Part II #5 a skill lives in the repo whose code,
plugin or config it describes — and this repo holds none of them (measured before the
change: **0 `.go`, 0 `.cue`, no `candy/` directory**) — so 15 of them moved, byte-identically,
to the repo that does:

| Skill | Now authored in | The entity that owns it |
|---|---|---|
| `charly-version` | [`opencharly/charly`](https://github.com/opencharly/charly) | the CLI itself — the only core skill with no `command:` provider in the org |
| `clean` | [`opencharly/plugin-clean`](https://github.com/opencharly/plugin-clean) | the `command:clean` provider |
| `cmd` | [`opencharly/plugin-cmd`](https://github.com/opencharly/plugin-cmd) | the `command:cmd` provider |
| `charly-doctor` | [`opencharly/plugin-doctor`](https://github.com/opencharly/plugin-doctor) | the `command:doctor` provider |
| `deploy` | [`opencharly/plugin-fleet`](https://github.com/opencharly/plugin-fleet) | the `command:deploy` provider |
| `charly-config`, `charly-update`, `logs`, `remove`, `service`, `shell`, `start`, `stop` | [`opencharly/plugin-pod`](https://github.com/opencharly/plugin-pod) | the `command:` providers that serve these verbs |
| `ssh` | [`opencharly/plugin-ssh`](https://github.com/opencharly/plugin-ssh) | the `command:ssh` provider |
| `charly-status` | [`opencharly/plugin-status`](https://github.com/opencharly/plugin-status) | the `command:status` provider |

**The addresses did not change.** Every skill keeps its `core` family at its
destination node, so `/charly-core:<skill>` still resolve — they are simply authored
where the entity is implemented. The move is the rule `AGENTS.md` Part II #5 states, tracked
in [opencharly/opencharly#600](https://github.com/opencharly/opencharly/issues/600).

## What remains here

| Property | Value |
|---|---|
| Layer / candy | `charly-core` (drained concept candy) |
| Install content | none — a `true` no-op `plan:` |
| Owns | nothing — 0 `skill:` entities |
| Service / port | none |

Do not compose, reference or edit this repo: the skills, their routing nodes and their
prose all live at the destinations above, and this repo's retirement is tracked in
[opencharly/opencharly#600](https://github.com/opencharly/opencharly/issues/600).
