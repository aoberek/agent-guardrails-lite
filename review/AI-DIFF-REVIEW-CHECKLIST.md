# AI diff review checklist

Printable. One page. Run through this before merging any AI-generated diff, no matter how small it looks.

## 1. Scope

- [ ] Every changed file is in the task's "may touch" list, or was explicitly called out and approved mid-task.
- [ ] No file was renamed, moved, or deleted unless the task explicitly asked for it.
- [ ] No new dependency was added unless pre-approved.
- [ ] Nothing in `DANGER-ZONES.md` was touched without the explicit sign-off that section requires.

## 2. Match to spec

- [ ] The diff does what the spec's Definition of done says — re-read that section and check each line against the actual change, don't rely on memory of what was asked.
- [ ] Nothing extra was bundled in — no drive-by refactor, no unrelated fix, no "while I was in there" change. If something extra is genuinely valuable, it should be a separate, reviewable diff.

## 3. What to read first in a large diff

Read in this order, not file-list order:

1. Any schema, migration, or type definition change — everything downstream depends on these being right.
2. Any change to a function's public signature or return shape — the highest blast radius per line changed.
3. The actual logic of the core change — the reason this diff exists.
4. Test changes — did tests get adjusted to match new (possibly wrong) behavior, or genuinely extended?
5. Everything else last — imports, formatting, incidental cleanup.

## 4. Where AI-generated code characteristically fails

- [ ] **Silently changed behavior in code adjacent to the actual task** — an edit to a shared helper "to make it cleaner" that changes behavior for every other caller.
- [ ] **Error handling that swallows instead of surfaces** — a try/catch added around new code that quietly returns a default value on failure instead of propagating or logging the error.
- [ ] **Tests that assert the new behavior is what it is, rather than what it should be** — a test written to match whatever the implementation happened to do, not the spec's actual requirement. This makes a broken implementation look verified.
- [ ] **Edge cases dropped from an existing function during a "refactor"** — a null check, an empty-array case, or a boundary condition present in the old code but missing from the new version.
- [ ] **Confident narration of unverified behavior** — read the agent's own summary of what it did skeptically; check that every claim ("this handles X") was actually tested, not asserted.

## 5. Verification

- [ ] The commands in `AGENTS.md` Section 2 ("before you say a task is done, run: ...") were actually run, and their output is shown, not just claimed.
- [ ] Any part of the diff the agent flagged as uncertain has been specifically checked by a human, not waved through because the rest of the diff looked fine.

## 6. Before merge

- [ ] A decision was logged if this diff involved a non-trivial choice (see `DECISION-LOG-TEMPLATE.md`).
- [ ] A rollback plan exists if this diff touches anything in `DANGER-ZONES.md` (see `ROLLBACK-PROTOCOL.md`).
