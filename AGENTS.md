# Job Search Kit (agent router)

This file mirrors `CLAUDE.md` for agents that read the `AGENTS.md` convention,
including Codex. The routing logic is identical. The differences in execution
are listed in `docs/codex.md`, and you should read that file once before
running setup.

## Read this first, then stop reading

This file is the router. Load one other file per turn, only the one the current
phase needs. Do not read the whole repo.

## Where you are

Check whether `me/profile.md` exists.

| State | What to do |
|---|---|
| `me/` has only `README.md` | Read `docs/codex.md`, then `setup/00-prerequisites.md`, and follow it. |
| `me/profile.md` exists, `me/setup-state.md` says setup is incomplete | Read the next unfinished step named in `me/setup-state.md`. |
| Setup complete | Answer the question in front of you. For changes, read `setup/06-tuning.md`. |

## Rules that hold in every phase

1. One step at a time. Finish a step, write its output, report, then stop.
2. Ask before you assume. Ask one question in plain language and wait.
3. Never submit an application. Setup finds, scores and drafts.
4. Write outputs to `me/`. That folder is gitignored.
5. Obey `reference/token-budget.md`. Generated task files must be
   self-contained so a scheduled run loads nothing from this repo.

## The one structural difference

Claude creates scheduled tasks through its own scheduler. Codex has no
equivalent, so step 5 writes each task prompt to `me/tasks/NN-name.md` and
prints the cron or Task Scheduler line that runs it. `docs/codex.md` has the
exact commands.
