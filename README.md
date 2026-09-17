# Job Search Kit

A job search that runs itself, built for people like me who do not have the time to apply to jobs because of their work. Clone this repo, open it in Claude, and say "set me up". Claude
interviews you for about forty minutes, builds your tracking sheet, writes your
CV bank, and schedules six recurring tasks that source roles, tailor your CV,
prepare applications, and watch your inbox for replies you would otherwise miss.

P.S. This requires Claude Pro or ChatGPT plus to work which costs about 2000 per month.

---

## Why this exists

High-volume applying produces low returns. A typical pattern looks like this:
two hundred applications over three weeks, the same generic CV attached to all
of them, four unrelated job titles chased at once, six applications to the same
company inside a single week, and two interview calls at the end of it.

Four things cause that outcome:

- **Spray.** Chasing several unrelated role families at once means no single
  family accumulates enough signal to tell you whether it is working.
- **Generic CVs.** Applicant tracking systems rank on keyword overlap with the
  job description. One CV sent everywhere ranks badly everywhere.
- **Duplicates.** Nobody tracks what they already sent, so the same company
  receives the same profile repeatedly and files it under noise.
- **Missed replies.** Assessment links expire in seven days. Interview
  scheduling links expire in thirty-six hours. An unread inbox loses the
  opportunities that high-volume applying earned.

Every rule in this kit stops one of those four.

---

## What you get

Setup schedules six tasks. Each runs on its own, reports what it did, and
stops. None of them submit an application without your review.

| # | Task | When | What it does |
|---|---|---|---|
| 1 | Shortlist Sweep | Daily, early morning | Polls company job boards, runs a capped set of searches, scores every new role out of 100, writes anything scoring 55+ to your sheet |
| 2 | Sourcing Top-up | Daily, midday | A cheaper second pass that keeps the queue full between the sweep and the apply runs |
| 3 | Apply Run | Every few hours on weekdays | Takes the highest-scoring shortlisted roles, downloads the CV already tailored to each one, fills the form, and stops for your review where a judgement call is needed |
| 4 | LinkedIn Prefill | Twice on weekdays | Fills Easy Apply forms and leaves the final click to you |
| 5 | Inbox Watch | Twice daily | Reads your email for interview invites, assessment links, and recruiter questions, computes what expires when, and drafts replies |
| 6 | Weekly Review | Sunday morning | Reconciles the pipeline, audits for duplicates and untailored applications, compares reply rates by role family and by source, and tells you what to retire |

Tasks 1, 2, 5 and 6 run without you present. Tasks 3 and 4 need your browser
open, and they hand every real decision back to you.

---

## Before you start

You need five things. The setup walks you through each one and will not move on
until it works.

1. **A Claude subscription** with scheduled tasks available.
2. **A Google account** connected to Claude, with Drive, Sheets and Gmail
   enabled. Your pipeline lives in a Google Sheet and your tailored CVs live in
   Drive.
3. **A web search connector.** Firecrawl is what this kit is tuned for, and
   its free tier covers a month of searching. Any search tool works with a
   small edit, documented in `reference/search-queries.md`.
4. **Your current CV**, in any format.
5. **Forty minutes**, once. After that the system runs on its own.
6. **Personal laptop/PC**, one that's always on and at your home applying for you.

Optional: the Claude in Chrome extension, if you want tasks 3 and 4. Skip them
and the other four still work.

---
You can install git for windows here : //CLaude you need to fill this
## Install

```bash
git clone https://github.com/sharath-creates/job-search-kit.git
cd job-search-kit
```

Open Claude, add this folder as a project directory, and type:

```
set me up
```

Claude reads `CLAUDE.md`, sees that `me/profile.md` is missing, and starts the
interview. Answer the questions. Stop whenever you want and say "continue
setup" later, since progress is saved after every step.

---

## What setup asks you

Six steps, each one short.

| Step | You provide | Claude produces |
|------|-------------|-----------------|
| 0 | Confirmation that your connectors work | A green light, or a specific fix |
| 1 | Your history, your targets, your limits | `me/profile.md` |
| 2 | Nothing | A Google Sheet with four tabs, seeded with company boards worth watching |
| 3 | Your CV | A master CV bank in Drive, split into reusable bullets |
| 4 | Salary floor, notice period, availability | `me/answer-sheet.md`, the source of every form answer |
| 5 | Your timezone and how aggressive you want to be | Six scheduled tasks, live |

Step 1 is the one that matters. It forces you to name at most two role families
and holds you to them. The scoring rubric, the search queries and the CV
tailoring all follow from that choice.

---

## What it costs

Roughly, per month, on the defaults:

- **Search credits:** about 450 of Firecrawl's 1,000 free monthly credits.
- **Claude usage:** the scheduled tasks are written to be self-contained, so a
  run loads no repository files and re-reads no large documents. `reference/token-budget.md`
  explains the design and lists the levers if you want to spend less.

Three settings control almost all of it: how many searches run per sweep, how
many pages get fetched for scoring, and how often the apply runs fire. Setup
asks you to pick a level, and you can change it later by saying "make my search
cheaper".

---

## The safety rules

These are built into every task and are worth knowing before you turn anything
on.

- **Nothing submits without you.** Tasks 3 and 4 fill forms and stop.
- **Daily and per-run caps.** A maximum number of applications per run and per
  day, set during setup. An empty run is a correct result.
- **A fourteen-day company cooldown.** One company receives at most one
  application per fortnight.
- **No generic CVs.** A role without a tailored CV gets skipped and reported,
  never sent a default file.
- **No LinkedIn automation past the final click.** LinkedIn's user agreement
  prohibits automated interaction and their detection restricts accounts that
  do it. Task 4 prepares, then stops.
- **Hard search caps.** Every task states its exact call count and credit
  ceiling. A task that finds nothing logs that and exits.

---

## Using this with Codex or another agent

`AGENTS.md` mirrors `CLAUDE.md` for agents that read that convention.
`docs/codex.md` covers the three changes you need: scheduling through cron or
Task Scheduler instead of Claude's scheduled tasks, local CSV files instead of
Google Sheets if you have no connector, and the search tool swap.

---

## Repository map

```
CLAUDE.md              Router. Claude reads this first, every session.
AGENTS.md              The same router for Codex and other agents.
setup/                 Six guided steps. Claude reads one at a time.
tasks/                 The six task templates, with placeholders.
reference/             Rubrics, query libraries, schemas, troubleshooting.
docs/                  Porting guides and design notes.
me/                    Your answers. Gitignored.
```

---

## Troubleshooting

`reference/troubleshooting.md` covers the failures people hit most: a task that
fires and does nothing, search credits burning faster than expected, the sheet
not updating, and Chrome-dependent tasks failing when the browser is closed.

## License

MIT. Fork it, change the rubric, retune the queries for your market.
