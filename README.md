# Job Search Kit

A job search that runs itself, built for people like me who do not have the time to apply to jobs because of their work. Download this repo, drop your CV into it, open it in Claude, and say "set me up". Claude reads your CV, checks a few things with you for about twenty-five minutes, builds your tracking sheet, writes your CV bank, and schedules six recurring tasks that source roles, tailor your CV, prepare applications, and watch your inbox for replies you would otherwise miss. After that you get one email a morning.

P.S. This needs a Claude Pro subscription with scheduled tasks, or an equivalent ChatGPT plan if you port it. Budget roughly ₹2,000 a month.

## Why this exists

High-volume applying produces low returns. A typical pattern looks like this: two hundred applications over three weeks, the same generic CV attached to all of them, four unrelated job titles chased at once, six applications to the same company inside a single week, and two interview calls at the end of it.

Four things cause that outcome:

- **Spray.** Chasing several unrelated role families at once means no single family accumulates enough signal to tell you whether it is working.
- **Generic CVs.** Applicant tracking systems rank on keyword overlap with the job description. One CV sent everywhere ranks badly everywhere.
- **Duplicates.** Nobody tracks what they already sent, so the same company receives the same profile repeatedly and files it under noise.
- **Missed replies.** Assessment links often expire within a week. Scheduling links can expire in a day or two. An unread inbox loses the opportunities that high-volume applying earned.

Every rule in this kit stops one of those four.

## What you get

Setup schedules six tasks. Each runs on its own, records what it did in your sheet, and stops. By default, none of them submit an application you have not ticked.

| # | Task | When | What it does |
|---|---|---|---|
| 1 | Shortlist Sweep | Daily, early morning | Polls company job boards, runs a capped set of searches, scores every new role out of 100, tailors a CV for the best ones, and sends your one morning email |
| 2 | Sourcing Top-up | Daily, midday | A cheaper second pass that keeps the queue full between the sweep and the apply runs |
| 3 | Apply Run | Every few hours on weekdays | Takes the tailored roles you ticked in the sheet, attaches the CV built for each, fills the form, and submits. Any question it cannot answer goes back to you in the sheet. |
| 4 | LinkedIn Prefill | Twice on weekdays | Searches Easy Apply roles for each title you target, scores them out of 100, fills in every one scoring 70+ (up to 75 a day) with your answer-sheet details and the CV on your LinkedIn account, and saves it. You open Saved jobs on LinkedIn, check it, and click Submit. |
| 5 | Inbox Watch | Twice daily | Reads your email for interview invites, assessment links, and recruiter questions, computes what expires when, drafts replies, and emails you only when something needs action |
| 6 | Weekly Review | Sunday morning | Reconciles the pipeline, audits for duplicates and untailored applications, compares reply rates by role family and by source, and tells you what to retire |

Tasks 1, 2, 5 and 6 run in the cloud, so they fire whether or not your laptop is on. Tasks 3 and 4 are created as tasks that require your own computer, because they drive a browser already logged in to the job sites. They hand every real decision back to you.

### How you stay in control from your phone

Your Google Sheet is where you and the system talk. Each morning's email lists the roles it prepared, each with a score, a keyword match and a tailored CV. You open the sheet on your phone and tick Approve on the ones you want. The next apply run sends them.

If a form asks something your answer sheet does not cover, the run stops on that role and writes the question into the sheet. You type your answer next to it, and the next run finishes the application. Answers that would apply to any company get saved, so the same question never stops a run twice.

Thirty roles take a few minutes to tick, rather than ninety minutes to fill. If you would rather not tick at all, pick automatic submission during setup, and the apply runs send everything that clears the bar, within your daily cap.

## Before you start

You need five things. Setup checks all of them in one go and gives you a single list of anything to fix.

1. A Claude subscription with scheduled tasks available.
2. A Google account connected to Claude, with Drive, Sheets and Gmail enabled. Your pipeline lives in a Google Sheet and your tailored CVs live in Drive.
3. A web search connector. Firecrawl is what this kit is tuned for, and its free tier covers a month of searching. Any search tool works with a small edit, documented in `reference/search-queries.md`.
4. Your current CV, in any format.
5. About twenty-five minutes, once. After that the system runs on its own.

Optional: tasks 3 and 4 fill in forms in your browser, so they need the Claude in Chrome extension and a computer that stays on at home. Skip them and the other four still find roles, tailor a CV for each, and watch your inbox. You apply from the morning email.

## Install

1. **Download the kit.** On this page, click the green **Code** button, then **Download ZIP**, and unzip it somewhere you will find again. No Git needed.
2. **Add your CV.** Put your CV file into the `me` folder inside the kit. Git ignores that folder, so your CV never ends up on GitHub.
3. **Start.** Open Claude, add the unzipped folder as a project directory, and type:

```
set me up
```

Claude checks your connectors, finds your CV, and starts. Stop whenever you want and say "continue setup" later, since progress is saved after every step.

If you already use Git, `git clone https://github.com/sharath-creates/job-search-kit.git` works too, and `git pull` gets you updates. After updating, say "update my tasks" so your scheduled tasks pick up the changes.

## What setup asks you

Claude reads your CV first, then shows you what it found and what it suggests. Most answers are "yes, that's right" or a one-line correction.

| Step | You provide | Claude produces |
|---|---|---|
| 0 | Nothing, unless a connector is missing | A green light, or one list of everything to fix |
| 1 | Corrections to what your CV says, the roles you want, your salary floor | `me/profile.md` |
| 2 | Nothing | A Google Sheet with four tabs, seeded with company boards worth watching |
| 3 | A quick check of three bullets, plus any stories your CV left out | A master CV bank in Drive, split into reusable bullets |
| 4 | A read-through of drafted form answers | `me/answer-sheet.md`, the source of every form answer |
| 5 | A yes to the schedule | Six scheduled tasks, live |

Step 1 is the one that matters. It asks you to name at most two role families and holds you to them. The scoring rubric, the search queries and the CV tailoring all follow from that choice. It also asks for your salary numbers, which Claude never guesses.

## After setup

You get one email each morning when there is something to report: new roles ready, what went out yesterday, and anything waiting on you. No email means nothing needed you. Inbox Watch emails separately, and only when a reply or a test link needs action. LinkedIn Prefill emails after a run that saved roles for you.

Things you can say to Claude in this folder any time:

| Say | What happens |
|---|---|
| "job search status" | A summary of the week, and anything waiting on you |
| "pause my search" | Every task stops until you say "resume my search" |
| "the roles look wrong" | Claude retunes the searches and the scoring |
| "make my search cheaper" | Fewer searches and fetches, in order of savings |
| "switch to automatic" | Apply runs stop waiting for your tick |
| "LinkedIn automatic" | LinkedIn Prefill submits complete forms itself, after you confirm the risk |
| "I got an interview at <company>" | The sheet updates, and Claude offers to prepare you |

## What it costs

Roughly, per month, on the defaults:

- **Search credits:** about 450 of Firecrawl's 1,000 free monthly credits.
- **Claude usage:** the scheduled tasks are written to be self-contained, so a run loads no repository files and re-reads no large documents. `reference/token-budget.md` explains the design and lists the levers if you want to spend less.

Three settings control almost all of it: how many searches run per sweep, how many pages get fetched for scoring, and how often the apply runs fire. Setup asks you to pick a level, and you can change it later by saying "make my search cheaper".

## The safety rules

These are built into every task and are worth knowing before you turn anything on.

- **Nothing submits without your say-so.** By default the apply run sends only roles you ticked. If you chose automatic, the caps and stops below are the limit, and you can withdraw any row.
- **Daily and per-run caps.** A maximum number of applications per run and per day, set during setup. An empty run is a correct result.
- **A fourteen-day company cooldown.** One company receives at most one application per fortnight.
- **No generic CVs on company sites.** A company-site role without a tailored CV gets skipped and reported, never sent a default file. LinkedIn Easy Apply uses the CV on your LinkedIn account.
- **LinkedIn stops before the final click unless you opt in.** LinkedIn's user agreement prohibits automated interaction and their detection restricts accounts that do it. By default task 4 fills and saves, and you submit.
- **Hard search caps.** Every task states its exact call count and credit ceiling. A task that finds nothing logs that and exits.

### On LinkedIn automation

LinkedIn's User Agreement prohibits automated applying, and that applies to locally-run browser tools as much as to anything in the cloud. By default this kit fills in every Easy Apply form that scores 70 or above, up to 75 a day, saves the job, and leaves the submit button to you. Open Saved jobs on LinkedIn whenever you have a few minutes, check each one, and click Submit.

The task on your computer can click Submit for you. Say "LinkedIn automatic" during setup or later, and it submits the forms it could fill in completely and saves the rest for you. Claude states the risk once and asks you to confirm before turning it on. Accounts get restricted for automated activity, and losing your LinkedIn mid-search costs you far more than the minutes you save. If it happens, say "my LinkedIn got restricted" and Claude stops the LinkedIn task.

If you modify this to auto-submit, that is your account and your call, and it is not what this kit does.

## What this kit does not do

It does not submit anything you have not approved, unless you turn on automatic submission. It does not scrape profiles or contact data. It does not message recruiters on your behalf. It does not promise interviews, and no tool can.

It removes the hours between deciding to apply and having applied. That is the whole product.

If you would rather not tick each application, choose automatic submission during setup, or say "switch to automatic" later. The apply run then does the final click for you on company job boards, within your caps. LinkedIn has its own opt-in, described above.

## Using this with Codex or another agent

`AGENTS.md` mirrors `CLAUDE.md` for agents that read that convention. `docs/codex.md` covers the changes you need: scheduling through cron or Task Scheduler instead of Claude's scheduled tasks, local CSV files instead of Google Sheets if you have no connector, and the search tool swap, plus what happens to email and the browser tasks.

## Repository map

```
CLAUDE.md              Router. Claude reads this first, every session.
AGENTS.md              The same router for Codex and other agents.
setup/                 Six guided steps. Claude reads one at a time.
tasks/                 The six task templates, with placeholders.
reference/             Rubrics, query libraries, schemas, troubleshooting.
docs/                  Porting guides and design notes.
me/                    Your CV and your answers. Gitignored.
```

## Troubleshooting

`reference/troubleshooting.md` covers the failures people hit most: a task that fires and does nothing, tailored roles that never get sent, search credits burning faster than expected, the sheet not updating, and Chrome-dependent tasks failing when the browser is closed.

## License

GNU AGPL-3.0. Fork it, change the rubric, retune the queries for your market. If you hand out a modified version, or run one as a service other people use, your changes have to ship under the same licence. Help keep the internet free. Full text in `LICENSE`.
