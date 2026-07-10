# Planning Kickoff Template — Opus (Claude Code)

> **Model:** Claude Opus, effort **High**, **Plan Mode ON** (Shift+Tab until "plan mode" shows in the input bar — Opus reads and proposes, but cannot edit files until you approve).
> **Where:** Claude Code inside the Claude Desktop app, launched from the **specific project subfolder** (never the parent `OE Claude Lab` folder). Foundation files (`CLAUDE.md`, `BRAND_GUIDELINES.md`, `COMPANY_CONTEXT.md`) live one level up.
> **Purpose:** Ground the plan in the REAL state of the repo — verify, then plan. Use this either (a) to turn a Fable chat plan into an executable, verified plan, or (b) to plan directly when the task is repo-centric.
> **How to use:** Copy everything below the line, fill the `[...]` placeholders, delete what doesn't apply.

---

## MISSION

This session is PLANNING ONLY. Do not modify, create, or delete any file yet. Your deliverable is a verified plan document. Execution happens in a later session (or after my explicit approval in this one).

## PROJECT

- **Working folder:** [e.g., b2b-partnerships-promo/]
- **Repo(s):** [e.g., oegit/oe-claude-lab, branch main; production: oegit/b2b-partnerships-promo]
- **Input plan (if any):** [e.g., audit/PLAN_PASE5.md — the strategic plan produced by Fable in chat]

## OBJECTIVE

[1–3 sentences: the outcome this plan must achieve.]

## PHASE 1 — COLD-READ & VERIFY (do this first)

1. Read the relevant foundation files one level up, plus the three custom skills (`open-english-brand.md`, `open-english-copy.md`, `open-english-banners.md`) if the task touches brand/copy output.
2. Explore the actual repo state: file tree, key configs, workflows, `git log` for recent history.
3. If an input plan exists, verify EVERY assumption tagged [UNVERIFIED] against the real files. Report each one as ✅ confirmed, ❌ wrong (with what you actually found), or ⚠️ partially true.
4. Flag anything risky you discover that the input plan missed (secrets, PII, schema drift, CI side effects, etc.).

Stop and show me the verification report before moving to Phase 2 if anything came back ❌ or ⚠️.

## PHASE 2 — WRITE THE PLAN

Produce `audit/PLAN_[NAME].md` (in English) with:

1. **Verified current state** — short summary of what the repo actually looks like.
2. **Task breakdown** — T0, T1, T2... Each task must include:
   - Goal (one line)
   - Exact files to touch
   - Verification step (how we prove the task worked)
   - Its own commit, with a proposed commit message
3. **Order & dependencies** — which tasks block which.
4. **Guardrails** — restated for this plan: [e.g., production frozen until dry run passes; no credentials/PII in tracked files; API keys as env vars only].
5. **Dry-run / rollback plan** — how to test safely and how to revert each risky task.
6. **Backlog** — deferred items, explicitly out of this plan.

## CONSTRAINTS

- [Project-specific constraints — e.g., legacy HTML still live in CI, don't break promote.yml]
- All new Lab documents in English.
- One commit per task; no batch commits mixing unrelated changes.

## APPROVAL GATE

After writing the plan file, STOP. Summarize the plan in ≤10 lines and wait for my explicit "go" before executing anything. If I say go, execute task by task, showing me each verification result before moving to the next task.
