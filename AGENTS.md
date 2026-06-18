# AGENTS.md

## Cursor Cloud specific instructions

This repository is a **collection of agent skills** (Markdown `SKILL.md` files) packaged as a private npm package. It is documentation/content, not a runnable web/server application.

- **There is no app server, lint, test, or build step.** `package.json` only exposes `changeset` and `version` scripts (release tooling via `@changesets/cli`). Do not invent lint/test/build commands.
- **Dependencies**: a single `npm install` installs the changesets release tooling. This is handled by the startup update script.
- **Inspect skills**: `bash scripts/list-skills.sh` prints every `SKILL.md` path in the repo.
- **Use/install skills locally**: `bash scripts/link-skills.sh` symlinks each skill into `~/.claude/skills` (skips `deprecated/`). This is how the skills are consumed by the Claude CLI.
- **Release flow**: changes are versioned with Changesets. Add a changeset with `npx changeset`; CI (`.github/workflows/release.yml`) runs `npm ci` then opens a version PR on push to `main`.
- **Repo conventions** (see `CLAUDE.md`): every skill in `engineering/`, `productivity/`, or `misc/` must be referenced in the top-level `README.md` and `.claude-plugin/plugin.json`; skills in `personal/`, `in-progress/`, and `deprecated/` must not appear in either. Keep these in sync when adding/moving skills.
