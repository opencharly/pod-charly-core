# AGENTS.md — pod-charly-core

Standalone repo for the `charly-core` concept candy — it ships no install
content and owns the core family's `skill:` entities (the command documentation
for the core `charly` CLI surface). The entities live in `charly.yml` at the
repo root; `candy/plugin-marketplace` regenerates the standalone
opencharly/marketplace corpus from them.

Canonical files:

- `charly.yml` — the `charly-core:` concept candy entity plus the family's
  `skill:` entities (`charly-config-skill`, `charly-doctor-skill`,
  `charly-status-skill`, `charly-update-skill`, `charly-version-skill`,
  `clean-skill`, `cmd-skill`, `deploy-skill`, `logs-skill`, `remove-skill`,
  `service-skill`, `shell-skill`, `ssh-skill`, `start-skill`, `stop-skill`).
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `CHANGELOG/` — per-CalVer history.
- `README.md` — user overview only; never agent guidance.

## Load these skills first (R0)

- The owning skill for the command you are changing, e.g.
  `/charly-core:charly-config`, `/charly-core:deploy`, `/charly-core:service`,
  `/charly-core:start`, `/charly-core:stop`, `/charly-core:shell`,
  `/charly-core:logs`, `/charly-core:remove`, `/charly-core:ssh`,
  `/charly-core:cmd`, `/charly-core:clean`, `/charly-core:charly-status`,
  `/charly-core:charly-doctor`, `/charly-core:charly-update`,
  `/charly-core:charly-version`. Load the one whose `skill:` entity you are
  editing.
- `/charly-internals:skills` — the skill maintenance rules (author on the
  entity, regenerate the corpus, never hand-edit a projected `SKILL.md`).
- `/charly-pod:pod` — the `kind: pod` / deploy schema the `deploy` skill
  references.
- `/charly-internals:git-workflow` — before any git/PR action.

## Build / validate / test

- `charly box validate` at the repo root — the structural check: the manifest
  must parse and validate at the installed charly.
- The merge gate is the **org-wide** `charly/pr-validator` (required check
  `validate / validate`, defined in `opencharly/.github`); this repo has **no**
  per-repo candy gate. Its only workflow file is
  `.github/workflows/tag-on-merge.yml`.
- The candy is documentation-only: its `plan:` is a `true` no-op plus a `true`
  `check:` that the skill entities are present and generated into the
  marketplace. There is no live bed.

## Modify this repo

- The `skill:` entities are the projected usage sources. Edit them here, never
  the generated `SKILL.md` in the marketplace corpus; a corpus regeneration
  (`charly marketplace generate`) projects them.
- Keep each entity's `name` / `family` / `owner` fields and the projection path
  (`marketplace/core/skills/<name>/`) consistent; a rename must sweep every
  `/charly-core:<old>` cross-reference in the same change.
- Keep the concept candy's `plan:` no-op; it exists only to carry the entities.

## Landing

- PR-only. Every change lands through a pull request; the org-required
  `charly/pr-validator` validates the diff and body and arms native auto-merge
  on PASS. Direct pushes to `main` are blocked.
- History lives in `CHANGELOG/` (written by `tag-on-merge` at merge time); the
  PR body IS the changelog.
- The authoritative rulebook is the umbrella `AGENTS.md` in
  `opencharly/opencharly` and `charly/AGENTS.md` in the charly repo. Do not
  restate its rules here.
