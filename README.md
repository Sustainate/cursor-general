# cursor-general

Shared Cursor slash commands and agent workflow for Sustainate projects.

## Commands

Slash commands live in [`.cursor/commands/`](.cursor/commands/). Open this folder as your Cursor workspace, or copy/sync commands to `%USERPROFILE%\.cursor\commands\` for global use.

| Command | Purpose |
|---------|---------|
| `full-dev-pipeline` | Review → implement → audit → ship (three steps) |
| `self-review-of-plan-spec` | Step 1: review plan/spec and implement |
| `check-fix-implementation` | Step 2: audit and fix |
| `commit-push-to-main` | Step 3: commit, merge to main, push, sync stack |

## Typical session

1. Brainstorm and write plan/spec (`docs/superpowers/` in your app repo).
2. Run `/full-dev-pipeline` in that app repo (with these commands available).

This repo versions the commands themselves; app code lives in other repositories.
