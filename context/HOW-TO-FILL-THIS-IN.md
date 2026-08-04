# How to fill in AGENTS.md

This is a line-by-line guide to filling in `AGENTS.md`. Budget 15–20 minutes the first time. It gets faster after that, and `STALENESS.md` tells you when to redo it.

## Section 1 — What this project is

- **Name:** The name you actually call it internally. Not the marketing name if those differ.
- **One-line purpose:** Write this so a new hire would understand what the project does from this sentence alone. If you can't do that in one sentence, the project has more than one purpose — split it, or pick the primary one and note the rest under "Known sharp edges."
- **Stack:** List what actually runs in production, not what's in an unused config file. If you have a legacy piece and a new piece, say both and say which is which.
- **Entry points:** The file or route table an agent should open first to understand control flow. If there are several (a web server and a worker, for instance), list both.
- **Who runs this:** This changes how cautious the agent should be. "Production service with paying users" should produce more caution than "personal side project." Say which one this is — don't leave the agent to guess.

## Section 2 — How to work in this repo

Every command here must be one you can paste into a terminal and have it work, right now, in this repo. Not the command from the README that's six months stale. Run each one yourself before you write it down.

- **Install:** The one command that gets a fresh clone running. If it's more than one command, list all of them in order.
- **Run locally:** Include flags you actually use, not just the bare minimum.
- **Run tests:** If you have more than one test suite (unit vs. integration, for example), list both and say when to use which.
- **Lint / typecheck:** If this project doesn't have one, write "None configured" — do not leave the field blank, since a blank field looks like an oversight rather than a fact.
- **Before you say a task is done, run:** This is usually a combination of the above. Be exact about the combination, since this is the line the agent checks before every "done."

## Section 3 — Scope contract

The defaults in the template are reasonable for most projects. Change them only if your project genuinely has different rules — for example, a project where dependency additions are expected and pre-approved, or a solo project where asking before every rename is unnecessary friction. Write the actual rule you want followed, not the template default, if they diverge.

## Section 4 — Danger zones

List the specific paths, not just categories. "Authentication" is vague. `src/auth/`, `middleware/session.ts`, and `infra/iam-policies.tf` are specific enough that an agent can recognize them without guessing. If a category in the template doesn't apply to this project (no payment code, say), delete that line rather than leaving a placeholder.

## Section 5 — Verification

Leave this section as written unless your project has an unusual verification step (a manual QA checklist, a required staging deploy, a specific person who must review certain changes). If so, add it here.

## Section 6 — Decisions and memory

Point this at wherever your team actually keeps decisions today, if that's not the template's `DECISION-LOG-TEMPLATE.md`. A decision log nobody uses is worse than none — it gives false confidence that history is being recorded.

## Section 7 — Project-specific conventions

This is the section worth the most time. Generic advice ("follow existing patterns") is useless to an agent that hasn't seen the codebase yet. Write the conventions a new senior engineer would need explained on day one: where business logic lives versus where it shouldn't, what naming pattern controllers/handlers/services follow, what the test file layout is, what's intentionally inconsistent for a historical reason versus what's a bug waiting to be normalized.

## Section 8 — Known sharp edges

The parts of the codebase every existing team member already knows to be careful around, that nobody has written down because it's "obvious" to insiders. It is not obvious to an agent with no history in this repo. Write down the thing you'd say out loud to a new hire in their first week: "don't touch that module without reading the comment at the top," "that function is called from three places you wouldn't expect," "the staging config secretly points at prod for one service."

## When you're done

Delete the instruction line at the top of `AGENTS.md`. Commit the file. If you use Claude Code, either copy this content into `CLAUDE.md` or make `CLAUDE.md` a one-line pointer to `AGENTS.md` — see `CLAUDE.md` in this kit for both options.
