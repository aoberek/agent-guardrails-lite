# Prompt library — lite (5 of 40)

These 5 are copied verbatim from the full 40-prompt library in [Agent Guardrails](<<REPLACE: Gumroad checkout URL>>), picked as the 5 most useful standalone — the ones that don't depend on any other file in the full kit to be worth using today. Each follows the same four-part shape: **State** (what to assume is true) → **Action** (the one thing to do) → **Constraint** (what not to do) → **Output format** (exactly what to return).

The full kit has 40 of these, organized into 7 categories (onboarding, spec writing, implementation guardrails, debugging, review, refactor/migration, session handoff), plus a CSV you can import straight into Notion or any database tool.

---

### Ask before assuming intent in ambiguous code

**Tool:** All
**When to use:** Any time reading unfamiliar code produces genuine uncertainty about intent, not just about implementation detail.

- **State:** You've found code whose purpose or correctness you cannot determine from reading it alone.
- **Action:** State exactly what's ambiguous, list the interpretations you're considering, and ask which is correct rather than picking the most likely one and proceeding.
- **Constraint:** Do not proceed with an assumption dressed up as a fact. Do not ask a vague open-ended question when you can narrow it to a short list of concrete options.
- **Output format:** The ambiguous code (file and line), 2-3 concrete interpretations, and a direct question asking which one is right.

---

### Turn a vague request into a checkable spec

**Tool:** All
**When to use:** Any time you're handed a task as a sentence or two instead of a written spec.

- **State:** You have a one- or two-sentence request with no formal spec.
- **Action:** Write a full spec covering: Problem, Definition of done (as a checklist of checkable conditions, not prose), Scope contract, Out of scope.
- **Constraint:** Do not invent a Definition of done condition that isn't checkable — if you can't state how you'd verify a line, ask instead of guessing. Flag every place the original request was ambiguous.
- **Output format:** A filled spec in the shape above, plus a short list of open questions that need a human answer before work starts.

---

### Reproduce before fixing

**Tool:** All
**When to use:** The very first step of any debugging task, before any code is changed.

- **State:** You've been given a bug report or failure description.
- **Action:** Reproduce the failure yourself first — run the exact steps or write a test that fails the same way — before proposing or writing any fix.
- **Constraint:** Do not propose a fix based on reading the code and guessing at the cause. If you cannot reproduce it, say so explicitly instead of fixing what you assume is wrong.
- **Output format:** Confirmation of the reproduction (command run, output showing the failure), then and only then a proposed fix.

---

### Confidence audit — ask what the agent is unsure about

**Tool:** All
**When to use:** Before doing a detailed line-by-line review, to direct your attention to the highest-risk parts first.

- **State:** A diff is presented as complete and ready for review.
- **Action:** Ask directly: which specific parts of this change are you fully confident in, and which are you not — and why, not just a confidence label.
- **Constraint:** Do not accept a blanket "I'm confident in all of it" without pushing for specifics — treat that answer itself as a signal to look harder, not as reassurance.
- **Output format:** A list of components/lines with a confidence level and the specific reason for any uncertainty, feeding directly into where a human reviewer should focus.

---

### Write a handoff note

**Tool:** Claude Code
**When to use:** End of any session that leaves work unfinished, or that involved a non-obvious struggle worth recording even if the task finished.

- **State:** A session is ending with a task partially done, or fully done but worth recording context on.
- **Action:** Write a handoff note: status, what's done, what's left, what was tried that didn't work and why it didn't work.
- **Constraint:** Do not write a vague summary like "made progress" — be specific enough that a session with zero memory of this one could resume correctly from the note alone.
- **Output format:** A short handoff block: status / what's done / what's left / what was tried that didn't work.
