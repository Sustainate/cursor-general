# Commit, push to main, sync the running stack

**`/full-dev-pipeline` step 3:** Run only after step 2 succeeds. Invoking `/full-dev-pipeline` authorizes this step.

Commit the current work (follow the git commit protocol in user rules), merge into **main**, and push to **origin/main**.

Then sync whichever checkout actually runs the local dev stack:

1. **Find the deploy checkout** — not necessarily this workspace:
  - If this workspace is a git worktree (e.g. under `.worktrees/`), use `git worktree list` and pick the primary repo checkout (usually the path on branch `main`, not a feature worktree).
  - Otherwise use the repository root of the current workspace.
2. In that checkout: `git pull` on `main` so the running stack has the pushed commits.
3. If this session ran in a `.worktrees/` checkout and the feature is merged and pushed to `main`: from the primary `main` checkout, remove that worktree when `git status` is clean and the branch has no unpushed commits; then `git branch -d <feature-branch>` if fully merged into `main`. Skip and report if dirty, unpushed, not merged, or isolated `data/` may matter.
4. **Bring the running stack up and prove it** — do not skip, and do not leave restarts as instructions for the human.
  - Read **`AGENTS.md`** in the deploy checkout (then `README`, compose files, or package scripts if `AGENTS.md` is silent). Use **that repo's** start/rebuild/dev commands and health checks. Do not copy another project's stack (Docker service names, Next ports, `pnpm build`, PowerShell scripts, etc.) unless this checkout's docs name them.
  - Restart or rebuild **only** what this change needs (API image vs host frontend vs workers vs migrations — whatever the docs say).
  - **Gate (required):** run the health check the docs specify. If none exists, probe the URLs/ports the docs name for local dev (HTTP 200 or the documented equivalent) until they succeed. If a process is listening but requests time out or 5xx, stop that process and start it the documented way; if the docs mention a corrupted build cache, clear it as they say, then start again. Re-check until the gate passes.
  - Only after the gate passes, tell the human to hard-refresh the browser if this is a web app.

Do not assume a fixed path like `C:\Dev\…` — derive paths from the current repo and worktree layout.
