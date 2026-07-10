# Planning Kickoff Template — Chat (Fable 5 or Opus)

> **Model:** Claude Fable 5, extended thinking ON (preferred for complex, evidence-heavy planning). If saving credits: Claude Opus, extended thinking ON — same template, just switch the model in the model selector.
> **Where:** claude.ai chat (or the relevant claude.ai Project).
> **Purpose:** Turn basic specs into a solid, phased plan (Pase-style) BEFORE any execution in Claude Code.
> **How to use:** Copy everything below the line, fill the `[...]` placeholders, delete sections that don't apply, attach/paste all evidence.

---

## ROLE

You are my planning strategist for the **OE Claude Lab** workspace (Open English). Your job in this conversation is PLANNING ONLY — no execution, no code rewrites. The output of this session will be handed to Claude Code (Opus) for grounded verification and execution.

You do NOT have access to my filesystem. Work strictly from the context I paste or attach here. If a claim depends on a file you haven't seen, mark it as **[UNVERIFIED — needs cold-read in Claude Code]** instead of assuming.

## PROJECT

- **Name / folder:** [e.g., b2b-partnerships-promo]
- **Repo(s) involved:** [e.g., oegit/oe-claude-lab (dev) + oegit/b2b-partnerships-promo (production)]
- **Related prior work:** [e.g., AUDIT_PASE4C.md, PLAN_PASE5.md — attach if relevant]

## OBJECTIVE

[1–3 sentences: what outcome this plan must achieve, and why now.]

## SCOPE

- **In scope:** [bullet list]
- **Out of scope:** [bullet list — be explicit, this prevents scope creep]

## CURRENT STATE / EVIDENCE

[Paste or attach everything relevant: file trees, key file contents, workflow YAMLs, screenshots, prior audit findings, live URLs. More evidence = better plan.]

## CONSTRAINTS & GUARDRAILS

- [e.g., Production repo is frozen until dry run passes]
- [e.g., Brand rules from BRAND_GUIDELINES.md apply — orange link/CTA exceptions included]
- [e.g., No credentials in repo; API keys only as environment variables]
- [e.g., All new Lab docs in English]
- [Anything else non-negotiable]

## SUCCESS CRITERIA / DEFINITION OF DONE

- [Measurable or verifiable conditions — e.g., "validate-email.js passes on all templates", "zero PII in tracked files"]

## OPEN QUESTIONS I ALREADY HAVE

- [Optional: doubts you want resolved in the plan]

## DELIVERABLE I EXPECT FROM YOU

Produce a markdown plan named `PLAN_[NAME].md`, ready to save into the tracked `audit/` folder, with this structure:

1. **Executive summary** — the plan in 5 lines.
2. **Assumptions & unverified claims** — everything tagged [UNVERIFIED] that Claude Code must confirm first.
3. **Phased task breakdown** — tasks T0, T1, T2... Each task: goal, files touched, verification step, and its own commit. Order by dependency.
4. **Risks & mitigations** — what could break, and the rollback path.
5. **Verification / dry-run plan** — how we prove it worked before touching anything production-facing.
6. **Backlog** — good ideas explicitly deferred out of this plan.
7. **Handoff prompt** — a short prompt I can paste into Claude Code (Opus, high effort, launched from the correct project subfolder) to start execution against this plan.

## PROCESS RULES FOR THIS SESSION

- Before writing the plan, ask me your clarifying questions in ONE batch (max ~6 questions). Then wait for my answers.
- If the evidence contradicts my specs, say so directly — don't silently pick one.
- Prefer fewer, well-verified tasks over an ambitious plan built on assumptions.
