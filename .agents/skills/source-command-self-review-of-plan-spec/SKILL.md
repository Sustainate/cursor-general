---
name: "source-command-self-review-of-plan-spec"
description: "Migrated source command `self-review-of-plan-spec`"
---

# source-command-self-review-of-plan-spec

Use this skill when the user asks to run the migrated source command `self-review-of-plan-spec`.

## Command Template

# **self-review-of-plan-spec-and-execution**

**`/full-dev-pipeline` step 1:** Run PHASE A → PHASE B.

BINDING: Stage 3 + superpowers:subagent-driven-development (read skill first).

Orchestrator edits ONLY: docs/superpowers/**, plan checkboxes, .superpowers/sdd/**, blocker *.md.

Orchestrator MUST NOT edit lib/**, server.js, public/**, test/** until each task has reviewer Spec ✅ AND Quality ✅. Parent code edits = SESSION FAILED.

When orchestrating tasks and spawning subagents, you are acting as the project lead. You MUST delegate all code execution to subagents. When calling the Task tool to spawn a subagent. You must invoke Composer 2.5 model for all sub-agents/background workers, no other model.

PHASE A — DOCS ONLY

- 3× review plan + spec A→Z (coherent, logical, matches codebase). After EACH round patch BOTH spec and plan before the next.
- No implementers, no task-brief, no code/test edits.
- End with: "PHASE A COMPLETE" + summary bullets.
- THEN CONTINUE DIRECTLY AND AUTOMATICALLY TO PHASE B BELOW FOR IMPLEMENTATION  - DO NOT STOP AT END OF PHASE A!

PHASE B — SDD (after PHASE A IS COMPLETE) 

**Subagent Delegation Rule:** Never write plain text progress updates for subagents. Always invoke the native `Task` tool so Codex renders the built-in UI widget.

- Use subagent-driven-development task-by-task; plan checkboxes (- [ ]).
- Important! Always us Composer 2.5 model  for sub-agents - no other model!
- Fresh Task subagent per role per task.
- Per task N: task-brief → implementer → review-package BASE HEAD → task reviewer (must state "Spec compliance: ✅/❌" and "Task quality: ✅/❌") → fix loops until both ✅ → verify npm test → [x] → append task line to `.superpowers/sdd/progress.md`.
- Orchestrator: monitor subagent terminals.
- If code already exists without artifacts: REVIEW-ONLY loops per task before any [x].

After all tasks done, you as orchestrator MUST DO A final review in chat; npm test exit 0.

If not OK after 3 full Phase B rounds: chat + write `.superpowers/sdd/blocker.md` for next session.

Session NOT fulfilled without reviewer ✅✅ per task and `.superpowers/sdd/progress.md` evidence.
