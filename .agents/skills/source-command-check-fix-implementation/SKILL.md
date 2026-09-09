---
name: "source-command-check-fix-implementation"
description: "Migrated source command `check-fix-implementation`"
---

# source-command-check-fix-implementation

Use this skill when the user asks to run the migrated source command `check-fix-implementation`.

## Command Template

# check-fix-implementation

**`/full-dev-pipeline` step 2:** Track corrections as `Correction N: complete` in `.superpowers/sdd/progress.md` — not plan checkboxes.

You as Orchestrator, please do a 2 x self review the curent implemenention and make list of all needed corrections. The use sub-agents to implement prodcition grade real fixes for those corrections.

**Subagent fix of currnet implemenation::** Never write plain text progress updates for subagents. Always invoke the native `Task` tool so Codex renders the built-in UI widget.

- Use subagent-driven-development **per correction** (each correction is one task).
- Important! Always us Composer 2.5 model  for sub-agents - no other model!
- Fresh Task subagent per role per task.
- Per correction N: task-brief → implementer → review-package BASE HEAD → task reviewer (must state "Spec compliance: ✅/❌" and "Task quality: ✅/❌") → fix loops until both ✅ → verify npm test → append `Correction N: complete` to `.superpowers/sdd/progress.md`.
- Orchestrator: monitor subagent terminals.
- If code already exists without artifacts: REVIEW-ONLY loops per correction before marking complete.

After all corrections done (or correction list empty after both reviews), orchestrator final review in chat; npm test exit 0 (where applicable).

If not OK after 3 full rounds: chat + write `.superpowers/sdd/blocker.md` for next session.

Session NOT fulfilled without reviewer ✅✅ per correction and progress log evidence.
