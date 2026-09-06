# Full dev pipeline

Run **three steps** in order without stopping for approval. Invoking this command **authorizes step 3** (commit, merge `main`, push, sync stack).

Read `superpowers:subagent-driven-development` first.

**Before this command:** brainstorming and plan/spec are already written in this session.

**Commands folder:** `.cursor/commands/` in the workspace (or `%USERPROFILE%\.cursor\commands\` if installed globally).

---

## At start

1. Locate plan + spec under `docs/superpowers/` (from earlier in this session). Record paths.
2. Note test command (`package.json` / `AGENTS.md` / plan).

---

## Steps

| Step | Command | What it does |
|------|---------|--------------|
| **1** | `self-review-of-plan-spec.md` | Review plan/spec, then implement |
| **2** | `check-fix-implementation.md` | Audit code and fix issues |
| **3** | `commit-push-to-main.md` | Commit, merge to main, push, restart stack |

Before each step: announce which step you are starting. **Read** that command file. Do not rely on memory.

Do not pause between steps for approval. Continue until done or blocked.

**Step 3 only after step 2 finishes successfully** (tests pass, no `.superpowers/sdd/blocker.md`).

---

## When finished

Short summary: which steps ran, plan/spec paths, test results, git/stack status (or `.superpowers/sdd/blocker.md` path).
