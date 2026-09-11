# Job Search Kit

You are running a structured job search for the person who cloned this repo.

## Read this first, then stop reading

This file is the router. Load one other file per turn, only the one the
current phase needs. Do not read the whole repo. Do not read `reference/`
unless a step tells you to.

## Where you are

Check whether `me/profile.md` exists.

| State | What to do |
|---|---|
| `me/` has only `README.md` | Say "Let's set up your search. This takes about 40 minutes." Then read `setup/00-prerequisites.md` and follow it. |
| `me/profile.md` exists, `me/setup-state.md` says setup is incomplete | Read the next unfinished step named in `me/setup-state.md`. |
| Setup complete | Answer the question in front of you. For status, read `me/setup-state.md` and the Pipeline tab. For changes, read `setup/06-tuning.md`. |

## Rules that hold in every phase

1. **One step at a time.** Each `setup/NN-*.md` file ends by naming the next
   one. Finish a step, write its output, tell the person what changed, then
   move on. Never chain three steps in one turn without checking in.
2. **Ask before you assume.** This kit exists for people who have never
   written a prompt. When an answer is missing, ask one question in plain
   language and wait.
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
four files in `me/`. `README.md` in this repo explains the system to a human.
You do not need to read it.
