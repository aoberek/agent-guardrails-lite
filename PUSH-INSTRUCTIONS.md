# Push instructions

This repo is built and ready locally at `product/agent-guardrails-lite/`. Nobody has created a GitHub account, created a remote, or pushed anything — that step requires your own GitHub identity and is deliberately left for you to run.

## 1. Fill in the remaining placeholders first

Before pushing, replace every `<<REPLACE: ...>>` in this folder:

- `README.md` — two Gumroad checkout URL placeholders and one email-capture form URL placeholder.

Everything else in this repo is already usable verbatim.

## 2. Create the GitHub repository (your account, your call)

Do this yourself, in your own GitHub account:

```
gh repo create agent-guardrails-lite --public --description "Stop your AI coding agent from breaking code that already worked. Free AGENTS.md starter + prompts."
```

(Or create it via github.com's "New repository" button — public, no README/license/gitignore auto-init since this folder already has all three.)

## 3. Initialize git and push

Run these from inside `product/agent-guardrails-lite/`:

```
cd product/agent-guardrails-lite
git init
git add .
git commit -m "Initial release: Agent Guardrails lite"
git branch -M main
git remote add origin https://github.com/<<REPLACE: your GitHub username>>/agent-guardrails-lite.git
git push -u origin main
```

If you used `gh repo create` in step 2 with the `--source` and `--push` flags instead, steps 2 and 3 collapse into one command:

```
cd product/agent-guardrails-lite
git init && git add . && git commit -m "Initial release: Agent Guardrails lite"
gh repo create agent-guardrails-lite --public --source=. --remote=origin --push
```

## 4. After it's live

- Add the repo URL to the Gumroad listing and the Notion Marketplace listing as the "try before you buy" link.
- Use it as the primary link in the r/SideProject and r/somethingimade posts — lead with this, not the paid link.
- Star and watch your own repo isn't necessary, but do turn on GitHub's repo topics (`ai-agents`, `claude-code`, `cursor`, `developer-tools`) so it's discoverable in GitHub search.

Nothing above has been run on your behalf. No account was created, no remote was added, and nothing was pushed.
