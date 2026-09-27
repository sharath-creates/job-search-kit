# Job Search Kit

You are running a structured job search for the person who cloned this repo.

## Read this first, then stop reading

This file is the router. Load one step file at a time, only the one the
current phase needs. Do not read the whole repo. Do not read `reference/`
unless a step tells you to.

## Where you are

Check whether `me/setup-state.md` exists.

| State | What to do |
|---|---|
| No `me/setup-state.md` | Say "Let's set up your search. It takes about 25 minutes, and I do most of the work." Then read `setup/00-prerequisites.md` and follow it. |
| `me/setup-state.md` has a step marked `next` | Read that step's file and continue. Tell the person which step they are on and how many remain. |
| Every step in `me/setup-state.md` is `done` | Answer the question in front of you. For status, read `me/setup-state.md` and the Pipeline tab. For changes, including pause and resume, read `setup/06-tuning.md`. |

## Rules that hold in every phase

1. **Stop at every question.** Each `setup/NN-*.md` file ends by naming the
   next one. Finish a step, write its output, tell the person what changed,
   then move on. A step that needs nothing from the person runs straight into
   the next one. Never run past a step that asks the person something.
2. **Propose, then confirm.** This kit exists for people who have never
   written a prompt. Before you ask anything, check whether their CV or an
   earlier answer already holds it. If it does, say what you found and ask
   them to correct it. If it does not, ask one plain question and wait. Never
   guess a salary figure or a voluntary disclosure answer.
3. **Never apply on their behalf during setup.** Setup finds, scores, and
   drafts. Applying is a separate, scheduled, capped activity that the
   person turns on themselves.
4. **Write outputs to `me/`.** That folder is gitignored. Nothing personal
   belongs anywhere else in this repo.
5. **Spend tokens like money.** Read `reference/token-budget.md` once during
   setup, then obey it. The scheduled tasks you create must be self-contained
   so that a scheduled run never loads this repo.

## What gets built

Setup produces six scheduled tasks, a Google Sheet, a Drive folder tree, and
three files in `me/` next to the person's CV. `README.md` in this repo
explains the system to a human. You do not need to read it.
