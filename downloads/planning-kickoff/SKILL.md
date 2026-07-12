---
name: planning-kickoff
description: Plan or spec any OE project before executing. Use for phrases like vamos a planear, hagamos el plan, nuevo proyecto, hagamos el spec de X, spec doc, or when the user shares specs expecting a plan.
---

# Planning Kickoff

Standard pipeline for Open English (OE Claude Lab) projects: turn basic specs into a verified, executable plan before touching anything.

## When this skill applies

ALWAYS use this skill when the user wants to start, plan, spec, or kick off a new project, task, campaign, Pase, or claude.ai Project — including phrases like "vamos a planear", "nuevo proyecto", "arranquemos con", "hagamos el plan", "planeación", "hagamos el spec de X", "armemos el spec", "spec doc", "spec document", "let's build the spec" — or when the user shares specs/requirements and expects a structured plan or spec document. Also use it when deciding whether a task needs formal planning at all.

## The pipeline (5 stops)

1. **Define** — capture objective, in/out scope, constraints (user provides, ~5 min). For LARGE projects, run the **Spec Doc process** instead: load `references/SPEC_DOC_PROCESS.md` and iterate a versioned spec doc (dump → expansion → decision rounds → close at open questions = 0 → ship to the Project's Context). The spec then feeds the Plan stop via a Scenario B kickoff (the message points to the spec, never retypes it).
2. **Plan** — in chat. Load `references/PLANNING_TEMPLATE_CHAT.md`, fill it with the user's specs, run it. Model: Fable 5 effort High (preferred) or Opus effort High (budget). Output: `PLAN_[NAME].md`.
3. **Verify** — in Claude Code. Load `references/PLANNING_TEMPLATE_CLAUDE_CODE.md`. Model: Opus effort High, Plan Mode ON, launched from the project subfolder. Confirms every `[UNVERIFIED]` claim against real files (✅/❌/⚠️) before finalizing the plan.
4. **Execute** — task by task, one commit per task (`paseN(TN):` prefix), approval gate at critical points.
5. **QA / dry run** — prove it works before touching anything production-facing.

## Which template, when

| Situation | Template | Where |
|---|---|---|
| Large project that needs a full Define first (spec doc) | `SPEC_DOC_PROCESS.md` | Chat — ideally inside the target claude.ai Project |
| Strategic planning, no repo yet, or claude.ai Project setup | `PLANNING_TEMPLATE_CHAT.md` | Chat (claude.ai) |
| Plan must be grounded in real repo files, or execution follows | `PLANNING_TEMPLATE_CLAUDE_CODE.md` | Claude Code (Desktop app) |
| Repo-only task with no strategic component | Skip chat, go straight to `PLANNING_TEMPLATE_CLAUDE_CODE.md` | Claude Code |

## Hard rules

- Chat cannot see the filesystem: anything unconfirmed gets tagged `[UNVERIFIED]` in the plan, never assumed.
- Claude Code verifies before planning: read real files first, plan second, execute only after explicit approval.
- Plans and audits are saved in the tracked `audit/` folder: `PLAN_PASEX`, `AUDIT_PASEX`, `NOTES_PASEX`.
- Skip stops 2–3 entirely for small tasks (<~30 min, obvious scope). Formal planning for tiny tasks is bureaucracy.
- Use a claude.ai Project only if the topic will span 3+ chats; otherwise a normal chat with the template is enough.
- Spec docs: one versioned doc rewritten in FULL each decision round (v0.1 → v0.N); FINAL only at open questions = 0 — zero loose TBDs; the chat is disposable, the doc is the deliverable.
- All plan documents in English.

## Adapting the templates

The templates are starting points, not scripts. Adapt the DELIVERABLE section to the task — e.g., for a claude.ai Project setup replace the "Handoff prompt" with UI setup steps, since no Claude Code phase exists. Delete sections that don't apply. Always keep: [UNVERIFIED] tagging, one-batch clarifying questions, phased tasks with per-task verification, and the approval gate.
