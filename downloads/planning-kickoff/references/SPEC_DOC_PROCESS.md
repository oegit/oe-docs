# Spec Doc Process — Define stage for large projects

> **Model:** the most capable model available, maximum effort. Spec mistakes multiply into every downstream task.
> **Where:** claude.ai chat — preferably INSIDE the target claude.ai Project, so the Project's Memory absorbs the decisions as they close.
> **Purpose:** turn a raw idea into a complete, closed Define (a versioned spec doc) BEFORE any planning. The finished spec feeds the Scenario B planning kickoff: it gets uploaded to the Project's Context, and the kickoff message only points to it.
> **Language:** the spec doc is ALWAYS written in English, regardless of the conversation language.

## The 5 steps

### Step 1 — Initial dump
The user describes the idea in natural language, plus the deliverables they have in mind. No structure required — capture everything as-is.

### Step 2 — Expansion
The model proposes everything the dump is missing: undecided points, edge cases, dependencies, hidden assumptions. The user decides what makes it into the spec — nothing enters without their call.

### Step 3 — Decision rounds
Iterate in rounds. Each round:

- Closes a batch of decisions.
- Rewrites the FULL document as a new version (v0.1 → v0.2 → … → v0.N). Never patch fragments — always regenerate the whole doc.
- Corrects misunderstandings on the spot, as soon as they surface.
- Technical decisions can be explicitly delegated by the user ("I'll go with your recommendation") — record them as closed, noting the delegation.

### Step 4 — Close
The spec is FINAL only when **open questions = 0**. Any remaining open question means another round, not a final spec.

### Step 5 — Ship
Upload the final spec to the claude.ai Project's **Context** panel (current version only — replace the old file, never accumulate versions there) and launch the planning kickoff using **Scenario B**: the message points to the spec, never retypes its fields.

## Hard rules

- **Most capable model, maximum effort** — for every round, not just the first.
- **One versioned doc.** The chat is disposable; the doc is the deliverable. Everything that matters lives in the current version.
- **Only closed decisions + explicit open questions.** Zero loose TBDs — anything undecided is listed as an open question, never left vague inside the text.
- **English only**, like every Lab document.
- **Prefer running it inside the Project** so the Project's Memory absorbs the decisions.

## How to run it (for the model)

1. On the initial dump, read it fully, then run Step 2: propose the missing pieces in ONE organized batch, grouped by theme. Wait for the user's calls.
2. After each user reply, close what they decided, regenerate the FULL spec as the next version, and end the doc with the explicit list of remaining open questions.
3. Keep a visible header in every version: project name, version number, date, open-question count.
4. Declare the spec FINAL only at open questions = 0, then hand the user Step 5: upload to Context + the Scenario B kickoff message.
