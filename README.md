# Job Search Kit

A job search that runs itself, built for people like me who do not have the time to apply to jobs because of their work.

You download this kit, connect a few free accounts, and chat with Claude for about twenty-five minutes. Claude reads your CV, builds a tracking sheet and a bank of CV bullets, and schedules six tasks. From then on, those tasks find roles that fit you, tailor a CV for each one, fill in applications, and watch your inbox for interview invites you would otherwise miss. You get one email a morning, and you decide what gets sent.

P.S. This needs a Claude Pro subscription or higher, and the Claude desktop app on a Mac or Windows computer. Budget roughly ₹2,000 a month. Everything else it uses has a free tier.

## Set it up, step by step

There are two parts. Part 1 connects your accounts once and takes about fifteen minutes. Part 2 is a conversation with Claude and takes about twenty-five. You can stop at any point and pick up where you left off.

### Part 1: One-time preparation

#### Step 1. Get Claude and the desktop app

1. Go to [claude.ai](https://claude.ai), sign in, and subscribe to **Pro** or a higher plan.
2. Download the desktop app from [claude.com/download](https://claude.com/download).
3. Install it, open it, and sign in with the same account.

**Done when** the Claude app is open and your initials show in its lower-left corner.

#### Step 2. Connect your Google account

The kit keeps your tracker in a Google Sheet, saves tailored CVs to Google Drive, and reads Gmail for replies from employers.

1. In the Claude app, click **Customize** in the left sidebar, then **Connectors**. Some versions keep this under **Settings → Connectors**.
2. Find **Google Drive**, click **Connect**, and sign in with the Google account you use for job applications. Allow the permissions it asks for.
3. Do the same for **Gmail**.

**Done when** Google Drive and Gmail both show as connected.

#### Step 3. Connect Firecrawl, the job search engine

Firecrawl is the web search the kit uses to find postings. Its free plan gives 1,000 credits a month with no card needed, and the kit uses about 450.

1. Create a free account at [firecrawl.dev](https://www.firecrawl.dev).
2. Back in the Claude app, go to **Customize → Connectors**, click **+**, then **Add custom connector**.
3. Fill in the two fields:
   - Name: `Firecrawl`
   - URL: `https://mcp.firecrawl.dev/v2/mcp-oauth`
4. Click **Add**, then **Connect**. A browser window opens. Sign in to Firecrawl there and approve the connection.

**Done when** Firecrawl appears in your list of connectors.

#### Step 4 (optional). Let Claude fill in application forms

Skip this step and the kit still finds roles, tailors a CV for each one, and watches your inbox. You apply yourself, from the links in the morning email. Do this step, and Claude also fills in application forms on company sites and on LinkedIn.

1. In Google Chrome, open [Claude in Chrome](https://chromewebstore.google.com/detail/claude/fcoeoabgfenejglbffodgkkbkcdhcgfn) and click **Add to Chrome**. Sign in with your Claude account and grant the permissions it asks for. Click the puzzle-piece icon in the toolbar, then the pin next to Claude, so it stays visible.
2. In the Claude app, open **Settings → Connectors**, find **Claude in Chrome**, click **Configure**, and switch it on.
3. In the Claude app, open **Settings → Cowork** and set **Preferred browser** to **Chrome (Claude in Chrome)**. Claude's built-in browser is not logged in to your LinkedIn, so this setting matters.
4. In Chrome, log in to LinkedIn and to any job sites where you keep an account.

These two tasks run on this computer. On weekdays, keep it switched on, with the Claude app and Chrome open.

**Done when** the Claude icon sits in your Chrome toolbar and Chrome is logged in to LinkedIn.

#### Step 5. Download the kit

1. Click [this link](https://github.com/sharath-creates/job-search-kit/archive/refs/heads/main.zip) to download the kit as a ZIP file. You do not need a GitHub account.
2. Unzip it. On Windows, right-click the file and choose **Extract All**. On a Mac, double-click it.
3. Move the unzipped `job-search-kit-main` folder into your **Documents** folder. Claude's folder picker works with folders inside your user folder.

#### Step 6. Put your CV in the kit

Open `job-search-kit-main`, then the `me` folder inside it, and copy your CV there. PDF or Word both work, under any file name.

Git ignores the `me` folder, so nothing you put there ends up on GitHub, even if you later publish your own copy of the kit.

### Part 2: Let Claude set you up

#### Step 7. Open the kit in Claude

1. Open the Claude app. If the message box offers **Chat** and **Cowork**, choose **Cowork**. Newer versions have no switch, and any conversation works.
2. Click **Work in a project or folder** in the message box, and choose `job-search-kit-main`.
3. Type this and press Enter:

```
Read CLAUDE.md and set me up
```

4. Claude asks before it uses Google Drive, Gmail or Firecrawl. Click **Allow** each time. If the clicking gets tiresome, switch the mode in the message box to **Auto**.

#### Step 8. Answer Claude's questions

Claude reads your CV first, shows you what it found, and asks you to correct it. Most answers are "yes, that's right" or a one-line fix. Keep these to hand, because Claude never guesses them:

| Have ready | Why Claude asks |
|---|---|
| The lowest CTC you would accept | No task ever applies below it |
| Your expected CTC | Forms often want a single number |
| Your current CTC (optional) | Most forms ask for it, LinkedIn's included. Skip it and Claude leaves that field for you. |
| Your notice period | It sets your earliest joining date |
| Phone number with country code, and your LinkedIn profile link | Only needed if your CV leaves them out |

Claude also suggests, and you confirm or correct:

- **The two kinds of role to chase.** This matters most. Two is the limit, because each kind needs its own CV angle and its own searches. Claude suggests two from your CV.
- **Your locations.** Cities, remote or hybrid, relocation, and whether you need visa sponsorship.
- **Companies you admire**, which Claude uses to calibrate what a good role looks like.
- **Your pace.** Light is about 4 applications a day, standard about 8, heavy about 12. Standard suits most people.
- **Sending applications**, if you did step 4. By default you tick each one before it is sent, and LinkedIn forms wait for your click.

#### Step 9. Say yes to the schedule

Claude shows the six tasks and when each one runs, in your time zone. Say "looks good", or ask to move any of them. Claude creates them and gives you the link to your tracker sheet.

**Done when** the **Scheduled** page, in the left sidebar of the Claude app, lists six tasks whose names start with "Job Search". Skipped step 4? Then you see four.

### Stuck?

| If you see this | Do this |
|---|---|
| Claude says it can't reach Google, Gmail or Firecrawl | Redo step 2 or 3, then tell Claude "check again" |
| Claude can't find your CV | Check that the file sits inside the `me` folder, or drag it into the chat |
| The folder picker won't accept the kit's folder | Move `job-search-kit-main` into Documents and try again |
| You ran out of time | Close the app. Next time, pick the same folder and say "continue setup" |
| A scheduled task sits waiting for approval | On the Scheduled page, open the task and set its approval mode to Auto |
| The form-filling tasks do nothing | Recheck step 4: the Claude app and Chrome both open, and the preferred browser set to Chrome |

For anything else, see `reference/troubleshooting.md`.

## Your first week

- **The first morning sweep** runs at 07:00 on its next scheduled day. If it found anything, you get an email listing new roles, each with a score, a keyword match and a tailored CV, plus anything waiting on you. No email means nothing needed you.
- **Tick what you want sent.** Open your tracker sheet on your phone and tick **Approve** on the roles you like. The next apply run sends them, with the CV tailored to each.
- **Check LinkedIn when you have a few minutes.** Twice each weekday, Claude fills in Easy Apply forms for roles scoring 70 or above, up to 75 a day, and saves them. Open **My jobs → Saved jobs** on LinkedIn, check each one, and click **Submit**.
- **Answer new questions in the sheet.** If a form asked something your answers don't cover, that row says **Needs you**, with the question beside it. Type your answer in the next column, and the next run finishes the application. Claude remembers answers that apply to any company, so the same question never stops a run twice.
- **Give it three days** before you judge it. The first sweep finds the most, because it has nothing to compare against yet.

## Things you can say to Claude

Open the Claude app, pick the kit's folder with **Work in a project or folder**, and say any of these:

| Say | What happens |
|---|---|
| "job search status" | A summary of the week, and anything waiting on you |
| "pause my search" | Every task stops until you say "resume my search" |
| "the roles look wrong" | Claude retunes the searches and the scoring |
| "make my search cheaper" | Fewer searches and page reads, in order of savings |
| "switch to automatic" | Apply runs on company sites stop waiting for your tick |
| "LinkedIn automatic" | LinkedIn Prefill submits complete forms itself, after you confirm the risk |
| "my LinkedIn got restricted" | The LinkedIn task stops, and the other five carry on |
| "I got an interview at <company>" | The sheet updates, and Claude offers to prepare you |
| "update my tasks" | Your scheduled tasks pick up changes from a newer version of the kit |

## Updating to a newer version

1. Download the kit again, as in step 5, and unzip it.
2. Copy everything inside your old `me` folder into the new `me` folder.
3. Open the new folder in Claude, as in step 7, and say "update my tasks".

If you use Git, `git clone https://github.com/sharath-creates/job-search-kit.git` gets you the kit, and `git pull` gets updates. Say "update my tasks" after each pull.

## Why this exists

High-volume applying produces low returns. A typical pattern looks like this: two hundred applications over three weeks, the same generic CV attached to all of them, four unrelated job titles chased at once, six applications to the same company inside a single week, and two interview calls at the end of it.

Four things cause that outcome:

- **Spray.** Chasing several unrelated role families at once means no single family accumulates enough signal to tell you whether it is working.
- **Generic CVs.** Applicant tracking systems rank on keyword overlap with the job description. One CV sent everywhere ranks badly everywhere.
- **Duplicates.** Nobody tracks what they already sent, so the same company receives the same profile repeatedly and files it under noise.
- **Missed replies.** Assessment links often expire within a week. Scheduling links can expire in a day or two. An unread inbox loses the opportunities that high-volume applying earned.

Every rule in this kit stops one of those four.

## What you get

Setup schedules six tasks. Each runs on its own, records what it did in your sheet, and stops. By default, none of them sends an application you have not approved.

| # | Task | When | What it does |
|---|---|---|---|
| 1 | Shortlist Sweep | Daily, early morning | Polls company job boards, runs a capped set of searches, scores every new role out of 100, tailors a CV for the best ones, and sends your one morning email |
| 2 | Sourcing Top-up | Daily, midday | A cheaper second pass that keeps the queue full between the sweep and the apply runs |
| 3 | Apply Run | Every few hours on weekdays | Takes the tailored roles you ticked in the sheet, attaches the CV built for each, fills in the form on the company's site, and submits. Any question it cannot answer goes back to you in the sheet. |
| 4 | LinkedIn Prefill | Twice on weekdays | Searches Easy Apply roles for each title you target, scores them out of 100, fills in every one scoring 70+ (up to 75 a day) with your details and the CV on your LinkedIn account, and saves it for you to submit |
| 5 | Inbox Watch | Twice daily | Reads your email for interview invites, assessment links, and recruiter questions, works out what expires when, drafts replies, and emails you only when something needs action |
| 6 | Weekly Review | Sunday morning | Reconciles the pipeline, audits for duplicates and untailored applications, compares reply rates by role family and by source, and tells you what to retire |

Tasks 1, 2, 5 and 6 run in the cloud, so they fire whether or not your computer is on. Tasks 3 and 4 run on your own computer, because they drive a Chrome browser already logged in to the job sites. Tailored CVs go to applications on company sites. LinkedIn Easy Apply uses the CV already on your LinkedIn account.

## What it costs

Roughly, per month, on the defaults:

- **Search credits:** about 450 of Firecrawl's 1,000 free monthly credits.
- **Claude usage:** the scheduled tasks are written to be self-contained, so a run loads no files from this kit and re-reads no large documents. `reference/token-budget.md` explains the design and lists the levers if you want to spend less.

Four settings control almost all of it: how many searches run per sweep, how many pages get read for scoring, how many LinkedIn postings get read per title, and how often the apply runs fire. Setup asks you to pick a level, and you can change it later by saying "make my search cheaper".

## The safety rules

These are built into every task and are worth knowing before you turn anything on.

- **Nothing submits without your say-so.** By default the apply run sends only roles you ticked. If you chose automatic, the caps and stops below are the limit, and you can withdraw any row.
- **Daily and per-run caps.** A maximum number of applications per run and per day, set during setup, and at most 75 LinkedIn roles a day. An empty run is a correct result.
- **A fourteen-day company cooldown.** One company receives at most one application per fortnight.
- **No generic CVs on company sites.** A company-site role without a tailored CV gets skipped and reported, never sent a default file.
- **LinkedIn stops before the final click unless you opt in.** LinkedIn's user agreement prohibits automated interaction and their detection restricts accounts that do it. By default task 4 fills in and saves, and you submit.
- **Hard search caps.** Every task states its exact call count and credit ceiling. A task that finds nothing logs that and exits.

### On LinkedIn automation

LinkedIn's User Agreement prohibits automated applying, and that applies to locally-run browser tools as much as to anything in the cloud. By default this kit fills in every Easy Apply form that scores 70 or above, up to 75 a day, saves the job, and leaves the submit button to you. Open Saved jobs on LinkedIn whenever you have a few minutes, check each one, and click Submit.

The task on your computer can click Submit for you. Say "LinkedIn automatic" during setup or later, and it submits the forms it could fill in completely and saves the rest for you. Claude states the risk once and asks you to confirm before turning it on. Accounts get restricted for automated activity, and losing your LinkedIn mid-search costs you far more than the minutes you save. If it happens, say "my LinkedIn got restricted" and Claude stops the LinkedIn task.

## What this kit does not do

It does not submit anything you have not approved, unless you turn on automatic submission. It does not scrape profiles or contact data. It does not message recruiters on your behalf. It does not promise interviews, and no tool can.

It removes the hours between deciding to apply and having applied. That is the whole product.

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

`reference/troubleshooting.md` covers the failures people hit most: a task that fires and does nothing, tailored roles that never get sent, search credits burning faster than expected, the sheet not updating, LinkedIn drafts that lose their answers, and Chrome-dependent tasks failing when the browser is closed.

## License

GNU AGPL-3.0. Fork it, change the rubric, retune the queries for your market. If you hand out a modified version, or run one as a service other people use, your changes have to ship under the same licence. Help keep the internet free. Full text in `LICENSE`.
