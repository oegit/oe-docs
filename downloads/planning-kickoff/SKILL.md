---
name: planning-kickoff
description: Standard OE Claude Lab process to plan any project before executing it. ALWAYS use this skill when the user wants to start, plan, or kick off a new project, task, campaign, Pase, or claude.ai Project — including phrases like "vamos a planear", "nuevo proyecto", "arranquemos con", "hagamos el plan", "planeación", or when the user shares specs/requirements and expects a structured plan. Also use it when deciding whether a task needs formal planning at all.
---

# Planning Kickoff

Standard pipeline for Open English (OE Claude Lab) projects: turn basic specs into a verified, executable plan before touching anything.

## The pipeline (5 stops)

1. **Define** — capture objective, in/out scope, constraints (user provides, ~5 min).
2. **Plan** — in chat. Load `references/PLANNING_TEMPLATE_CHAT.md`, fill it with the user's specs, run it. Model: Fable 5 extended thinking (preferred) or Opus extended thinking (budget). Output: `PLAN_[NAME].md`.
3. **Verify** — in Claude Code. Load `references/PLANNING_TEMPLATE_CLAUDE_CODE.md`. Model: Opus effort High, Plan Mode ON, launched from the project subfolder. Confirms every `[UNVERIFIED]` claim against real files (✅/❌/⚠️) before finalizing the plan.
4. **Execute** — task by task, one commit per task (`paseN(TN):` prefix), approval gate at critical points.
5. **QA / dry run** — prove it works before touching anything production-facing.

## Which template, when

| Situation | Template | Where |
|---|---|---|
| Strategic planning, no repo yet, or claude.ai Project setup | `PLANNING_TEMPLATE_CHAT.md` | Chat (claude.ai) |
| Plan must be grounded in real repo files, or execution follows | `PLANNING_TEMPLATE_CLAUDE_CODE.md` | Claude Code (Desktop app) |
| Repo-only task with no strategic component | Skip chat, go straight to `PLANNING_TEMPLATE_CLAUDE_CODE.md` | Claude Code |

## Hard rules

- Chat cannot see the filesystem: anything unconfirmed gets tagged `[UNVERIFIED]` in the plan, never assumed.
- Claude Code verifies before planning: read real files first, plan second, execute only after explicit approval.
- Plans and audits are saved in the tracked `audit/` folder: `PLAN_PASEX`, `AUDIT_PASEX`, `NOTES_PASEX`.
- Skip stops 2–3 entirely for small tasks (<~30 min, obvious scope). Formal planning for tiny tasks is bureaucracy.
- Use a claude.ai Project only if the topic will span 3+ chats; otherwise a normal chat with the template is enough.
- All plan documents in English.

## Adapting the templates

The templates are starting points, not scripts. Adapt the DELIVERABLE section to the task — e.g., for a claude.ai Project setup replace the "Handoff prompt" with UI setup steps, since no Claude Code phase exists. Delete sections that don't apply. Always keep: [UNVERIFIED] tagging, one-batch clarifying questions, phased tasks with per-task verification, and the approval gate.
