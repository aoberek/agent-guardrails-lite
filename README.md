# Agent Guardrails — lite

**Stop your AI coding agent from breaking code that already worked.**

This is the free, public subset of [Agent Guardrails](https://arielton.gumroad.com/l/agent-guardrails) — a drop-in context, spec, and review system for Claude Code, Cursor, and Codex. Copy `context/AGENTS.md` below into your project, fill in the blanks, and your agent stops forgetting, stops sprawling, and stops shipping diffs you can't review. No signup, no install, no cloning required to get value — the whole flagship file is inlined below.

## Use it right now

1. Copy the `AGENTS.md` content below into a new file at the root of your project.
2. Replace every `<<REPLACE: ...>>` block with your project's actual details.
3. Read `context/HOW-TO-FILL-THIS-IN.md` in this repo if you want a line-by-line guide to filling it in well instead of quickly.
4. Start your next AI coding session by asking your agent to read this file first.

## `AGENTS.md`, in full

````markdown
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

Read the current task's spec before touching anything. If there is no spec, ask for one before writing code.

Default rules, unless a specific task overrides them in writing:

- Touch only the files needed for the stated task. If you find an unrelated bug or improvement, name it in your output — do not fix it in the same diff.
- Do not rename, move, or delete a file unless the task explicitly asks for it.
- Do not add a new dependency unless the task explicitly allows it. Ask first.
- Do not change a public function's signature, a database schema, or an API contract without calling it out before you do it.
- If a task turns out to need more files than expected, stop and say so before continuing. Do not silently expand scope.

## 4. Danger zones — never touch unsupervised

At minimum, the following require an explicit human go-ahead in the current conversation, every time, no exceptions:

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

- Log any non-trivial decision — a library choice, a rejected approach, a tradeoff — somewhere future sessions will read it. Future sessions, including yours, will not remember today's reasoning otherwise.
- Before ending a session with unfinished work, write a handoff note: what's done, what's left, what you tried that didn't work.

## 7. Project-specific conventions

<<REPLACE: naming conventions, folder structure rules, patterns to follow, patterns to avoid — whatever is specific to this codebase and not obvious from reading it>>

## 8. Known sharp edges

<<REPLACE: parts of this codebase that are fragile, confusing, or commonly misread by anyone new to it — including an agent>>

---

Keep this file current. A stale context file is worse than no context file — it actively misleads the agent with information that used to be true.
````

## What else is in this repo

- `context/HOW-TO-FILL-THIS-IN.md` — a line-by-line guide to filling in every section above properly instead of quickly.
- `prompts/prompt-library-lite.md` — 5 prompts, picked as the most useful on their own, from the full 40-prompt library.
- `review/AI-DIFF-REVIEW-CHECKLIST.md` — the one-page checklist to run before merging any AI-generated diff.

## What the paid kit adds

This repo is genuinely useful on its own — it's not a teaser with the substance held back. The $29 kit ([Agent Guardrails](https://arielton.gumroad.com/l/agent-guardrails)) adds what a single file can't cover:

- Tool-specific variants (`CLAUDE.md`, Cursor's `.cursorrules` and `rules/*.mdc`) and 6 stack-specific addenda (Next.js + TypeScript, Python + FastAPI, Go, Turborepo monorepo, legacy JavaScript, generic).
- Spec, task, decision-log, and scope-contract templates, plus 3 fully filled worked examples.
- 12 slash commands (`/spec`, `/plan`, `/scope-check`, `/implement`, `/test-first`, `/review-diff`, `/explain-change`, `/danger-check`, `/rollback-plan`, `/context-refresh`, `/decision`, `/handoff`) for Claude Code, Cursor, and Codex.
- The full review system: `DANGER-ZONES.md`, `ROLLBACK-PROTOCOL.md`, `VERIFY-WHAT-YOU-DIDNT-WRITE.md`, `TEST-FIRST-PROMPTS.md`.
- All 40 prompts, categorized, plus a CSV you can import straight into a Notion database.
- A companion Notion "Agent Run Log" template, pre-loaded with all 40 prompts.
- A ~10,000-word playbook covering the five ways agent runs go sideways, how to write a spec an agent can't misread, scope control, verifying code you didn't write, and two full worked examples.
- Two install scripts (`check-context.sh`, `session-start.sh`).

## Get notified about the full kit

Want the worked examples, the 40-prompt library, and the Notion template? <<REPLACE: email capture form URL>> to get notified — or skip the wait and get it now: [Agent Guardrails on Gumroad](https://arielton.gumroad.com/l/agent-guardrails).

## License

MIT — see `LICENSE`. This license covers only the files in this repository; the full paid kit has its own commercial license.
