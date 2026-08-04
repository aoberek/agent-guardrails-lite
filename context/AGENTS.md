# AGENTS.md

This file is the first thing your AI coding agent reads. It tells the agent what this project is, how to work in it, what it may never touch without asking, and how to prove its work before calling something done.

Fill in every `<<REPLACE: ...>>` block below with details from your actual project. Delete this instruction line once you have.

## 1. What this project is

- **Name:** <<REPLACE: project name>>
- **One-line purpose:** <<REPLACE: what this project does, in one sentence>>
- **Stack:** <<REPLACE: language, framework, database, key libraries>>
- **Entry points:** <<REPLACE: where execution starts — main file, server entry, primary route table>>
- **Who runs this:** <<REPLACE: solo project, small team, production service with real users, etc.>>

## 2. How to work in this repo

- **Install:** <<REPLACE: exact install command>>
- **Run locally:** <<REPLACE: exact run command>>
- **Run tests:** <<REPLACE: exact test command>>
- **Lint / typecheck:** <<REPLACE: exact command>>
- **Before you say a task is done, run:** <<REPLACE: the specific commands that must pass — tests, typecheck, build>>

Run these yourself. Do not ask the human to run them and report back unless you have no way to run them yourself.

## 3. Scope contract

Read the current task's spec before touching anything. If there is no spec, ask for one or write one using `SCOPE-CONTRACT.md` before writing code.

Default rules, unless a specific task overrides them in writing:

- Touch only the files needed for the stated task. If you find an unrelated bug or improvement, name it in your output — do not fix it in the same diff.
- Do not rename, move, or delete a file unless the task explicitly asks for it.
- Do not add a new dependency unless the task explicitly allows it. Ask first.
- Do not change a public function's signature, a database schema, or an API contract without calling it out before you do it.
- If a task turns out to need more files than expected, stop and say so before continuing. Do not silently expand scope.

## 4. Danger zones — never touch unsupervised

See `review/DANGER-ZONES.md` for the full list and the reasoning. At minimum, the following require an explicit human go-ahead in the current conversation, every time, no exceptions:

- <<REPLACE: authentication or session code paths>>
- <<REPLACE: payment or billing code paths>>
- <<REPLACE: database migrations>>
- <<REPLACE: production config, secrets, or environment files>>
- <<REPLACE: CI/CD pipeline definitions>>
- Anything that deletes data, in any environment.

## 5. Verification — before you call it done

- State what you changed, in files-touched form, not prose.
- State how you verified it — which commands you ran and what they returned. "It should work" is not verification.
- If you touched code you did not write and do not fully understand, say so explicitly. Do not present unfamiliar code as verified when it isn't.
- Flag anything you are uncertain about instead of guessing silently.

## 6. Decisions and memory

- Log any non-trivial decision — a library choice, a rejected approach, a tradeoff — in `specs/DECISION-LOG-TEMPLATE.md` or the project's existing decision log. Future sessions, including yours, will not remember today's reasoning otherwise.
- Before ending a session with unfinished work, write a handoff note: what's done, what's left, what you tried that didn't work. Use `/handoff` if the tool supports slash commands.

## 7. Project-specific conventions

<<REPLACE: naming conventions, folder structure rules, patterns to follow, patterns to avoid — whatever is specific to this codebase and not obvious from reading it>>

## 8. Known sharp edges

<<REPLACE: parts of this codebase that are fragile, confusing, or commonly misread by anyone new to it — including an agent>>

---

Keep this file current. See `STALENESS.md` for when and how to refresh it. A stale context file is worse than no context file — it actively misleads the agent with information that used to be true.
