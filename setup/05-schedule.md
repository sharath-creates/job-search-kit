# Step 5: Scheduling

**Goal:** turn the six templates in `tasks/` into six live scheduled tasks with
the person's details baked in.

**Output:** six scheduled tasks, their IDs recorded in `me/setup-state.md`.

**Time:** 3 minutes.

---

## The rule that governs this step

**A scheduled run must never read this repository.** Each run starts in a fresh
session. If its prompt says "read the repo", every run pays to load files it
could have carried in its own text. So you substitute every placeholder now,
once, and the resulting prompt is self-contained.

The cost of getting this wrong is roughly 30,000 tokens per run, across about
40 runs a week. Read `reference/token-budget.md` if you want the arithmetic.

---

## 1. Confirm the schedule

Work out their timezone from the city in `me/profile.md`. Do not ask for it;
the grid below shows it, and they can correct it there.

Times below are local. If the scheduler accepts a timezone, give it theirs and
the local times as written. Convert to UTC only when it does not, and then
shift the day-of-week field if the conversion crosses midnight. A wrong
conversion is the usual cause of two apply runs firing in the same hour.

| Task | Light | Standard | Heavy |
|------|-------|----------|-------|
| 1 Shortlist Sweep | 07:00 Mon, Wed, Fri | 07:00 Mon-Sat | 07:00 daily |
| 2 Sourcing Top-up | off | 13:00 Mon-Sat | 13:00 and 17:00 daily |
| 3 Apply Run | 10:00 and 16:00 Mon-Fri | every 3h, 09:00-21:00 Mon-Fri | every 2h, 09:00-21:00 Mon-Fri |
| 4 LinkedIn Prefill | 12:00 and 19:00 Mon-Fri | 10:30 and 19:30 Mon-Fri | 10:00 and 20:00 Mon-Fri |
| 5 Inbox Watch | 08:00 daily | 08:00 and 20:00 daily | 08:00, 14:00, 20:00 daily |
| 6 Weekly Review | 10:00 Sunday | 10:00 Sunday | 10:00 Sunday |

LinkedIn Prefill saves each filled application to the person's LinkedIn
Saved jobs, so they can review it whenever they are free. Its two runs sit
between apply runs at every level, because both tasks drive the same browser.
Keep them apart if you move either one.

Caps by level:

| | Light | Standard | Heavy |
|---|---|---|---|
| Applications per apply run | 1 | 2 | 3 |
| Applications per day, all runs | 4 | 8 | 12 |
| Search calls per sweep | 6 | 10 | 14 |
| Pages fetched for scoring per sweep | 8 | 15 | 20 |
| LinkedIn postings read per title, per run | 3 | 5 | 8 |
| LinkedIn roles filled per day, both runs | 75 | 75 | 75 |

The LinkedIn daily cap is 75 at every level because LinkedIn limits how many
Easy Apply applications an account can send in a day. The read cap usually
keeps a day well under it.

Show the person their grid and ask:

> Here's the schedule, in <timezone> time. Anything you want moved?

If `me/profile.md` says no to browser tasks, drop tasks 3 and 4 and say so.

## 2. Fill the templates

For each template in `tasks/`, read it, substitute every placeholder, and
create the scheduled task with the filled text as its prompt.

| Placeholder | Source |
|---|---|
| `{{NAME}}` `{{EMAIL}}` `{{CITY}}` | `me/profile.md` identity |
| `{{CURRENT_ROLE}}` | Title at company, since date |
| `{{YEARS}}` | Years of experience |
| `{{DEADLINE_LINE}}` | A sentence about days remaining, or an empty string |
| `{{BACKGROUND}}` | The background one-liner, verbatim |
| `{{FAMILY_A}}` `{{FAMILY_A_TITLES}}` | Family A name and title list |
| `{{FAMILY_B}}` `{{FAMILY_B_TITLES}}` | Family B name and title list |
| `{{LOCATIONS}}` | Ranked locations, comma separated |
| `{{AUTOFAILS}}` | One per line, from profile |
| `{{FLOOR}}` | Minimum compensation, with currency |
| `{{AVAILABILITY}}` | Interview windows |
| `{{YEARS_BAND}}` | Years minus 1 to years plus 4, written as a range |
| `{{SHEET_NAME}}` | Sheet name, from setup-state |
| `{{DRIVE_ROOT}}` | `Job Search <year>` |
| `{{CV_BANK_DOC}}` | CV bank doc name |
| `{{ANSWER_SHEET_DOC}}` | Drive copy of the answer sheet |
| `{{PER_RUN_CAP}}` `{{PER_DAY_CAP}}` | From the caps table |
| `{{SEARCH_CALLS}}` `{{FETCH_CAP}}` | From the caps table |
| `{{LINKEDIN_READ_CAP}}` `{{LINKEDIN_DAY_CAP}}` | From the caps table |
| `{{WEEKLY_SEARCH_CALLS}}` | Twice `{{SEARCH_CALLS}}`, capped at 20 |
| `{{SEARCH_TOOL}}` | Search connector name |
| `{{TZ}}` `{{TIME}}` `{{TIMES}}` `{{INTERVAL}}` `{{WINDOW}}` | Their timezone and the local times from the schedule grid. These appear in task names, not in prompt bodies. |
| `{{APPROVAL_RULE}}` | The submission mode from the profile. See the table below. |
| `{{APPROVAL_NOTE}}` | The submission mode from the profile. See the table below. |
| `{{LINKEDIN_SUBMIT_RULE}}` | The LinkedIn mode from the profile. See the table below. |
| `{{QUERIES_A}}` `{{QUERIES_B}}` | Built in the next section |
| `{{TOPUP_QUERY_1}}` to `{{TOPUP_QUERY_4}}` | The four highest-yield queries from the set, one per domain tier |
| `{{BOARD_DOMAINS}}` `{{BOARD_DOMAINS_PRIMARY}}` `{{BOARD_DOMAINS_SECONDARY}}` `{{REGIONAL_DOMAINS}}` `{{NOISE_DOMAINS}}` | The domain tier lists in `reference/search-queries.md`, narrowed to their locations |

The two approval placeholders take one of these fixed texts:

| Mode | `{{APPROVAL_RULE}}` (task 3) | `{{APPROVAL_NOTE}}` (task 1) |
|---|---|---|
| You approve | `Only rows whose Approve cell is ticked, or reads yes, y or x. An unticked row waits, however well it scores.` | `Tick Approve in the sheet on the ones you want sent. The next apply run sends them.` |
| Automatic | `Every row that passes the guards below. The person chose automatic submission within these caps.` | `The apply runs send these within your daily cap. Set Status to Withdrawn on any you want to skip.` |
| No browser tasks | Task 3 is not created. | `Apply from the links above. The tailored CV and cover note for each sit in its Drive folder. Set Status to Applied when you send one, or the weekly review will pick up the confirmation email.` |

`{{LINKEDIN_SUBMIT_RULE}}` (task 4) takes one of these:

| LinkedIn mode | `{{LINKEDIN_SUBMIT_RULE}}` |
|---|---|
| You click | `Never click Submit or Send application. Fill each form, then save it for the person to review and submit.` |
| Automatic | `The person chose automatic submission on LinkedIn and accepted the risk to their account. Click Submit only when every field came from the answer sheet and nothing was left blank or flagged. Save the rest for the person.` |

Verify before creating each task: no `{{` remains anywhere in the prompt.

## 3. Build the query set

Read `reference/search-queries.md` once. Using their two families and their
locations, write six to ten queries and assign domain filters. Write the
resulting list into the `Queries` tab of the sheet and into `{{QUERIES_A}}` and
`{{QUERIES_B}}`.

If the search tool is not Firecrawl, that file's last section covers the syntax
differences. Adapt the queries before substituting them.

## 4. Decide where each task runs

Two of the six drive a browser that is already logged in to the job sites, so
they have to run on the person's own machine. The other four touch nothing but
Google Workspace and the search API, so they belong in the cloud, where they
fire whether or not that machine is awake.

| Task | Runs | Why |
|---|---|---|
| 1 Shortlist Sweep | Cloud | Search API and Sheets only |
| 2 Sourcing Top-up | Cloud | Search API and Sheets only |
| 3 Apply Run | Their own computer | Drives a logged-in browser |
| 4 LinkedIn Prefill | Their own computer | Drives a logged-in browser |
| 5 Inbox Watch | Cloud | Gmail only |
| 6 Weekly Review | Cloud | Sheets only |

Create tasks 3 and 4 so that they require that computer. Set the local-device
requirement as you create the task. If your scheduler cannot express it at
creation time, create the task anyway and tell the person to switch on
"Require this computer" for it in the desktop app before the first run.

Get this wrong and nothing shouts. A browser-driving task created in the cloud
wakes up, finds no browser, and logs an empty run, which reads like "nothing
matched today" rather than "this was never going to work".

Tasks 1, 2, 5 and 6 stay in the cloud on purpose. Bind them to a laptop and
they stop the moment it sleeps, and a sweep that skips a day loses the roles
posted that day.

## 5. Create the tasks

Create them live and record every ID. Do not ask whether to start them
disabled: the person can stop everything by saying "pause my search", so a
disabled start only adds a step they have to remember.

Set each task's approval mode to automatic ("Auto" in Claude Cowork). Nobody
is there to click Allow when a scheduled run fires, so a task left on manual
approval stalls at its first connector call. If the scheduler will not take
the mode at creation, tell the person to open each task on the Scheduled page
and set it themselves.

## 6. Record it

Append to `me/setup-state.md`:

```markdown
## Tasks
| # | Name | ID | Schedule (local) | Enabled |
|---|------|-----|------------------|---------|

## Settings
- Intensity: <level>
- Submission: <you approve / automatic / not applicable>
- LinkedIn: <you click / automatic / not applicable>
- Per-run cap: <N>, per-day cap: <N>
- Search calls per sweep: <N>, credits per month estimated: <N>
- Timezone: <tz>
```

Mark all steps done.

---

## Then say

> Everything's live. Here's what happens next:
>
> - Tomorrow at <time>, the first sweep runs. From then on you get one email
>   each morning: new roles worth your time, what went out yesterday, and
>   anything waiting on you. No email means nothing needed you.
> - Inbox watch checks for interview invites and test links at <times>, and
>   emails you only when one needs action.
> - <You approve: Tick Approve in the sheet on the roles you want sent, from
>   your phone if you like. Nothing goes out without that tick.>
>   <Automatic: Apply runs send up to <N> a day. Set a row's Status to
>   Withdrawn to stop one.>
>   <No browser tasks: Apply from the links in the morning email. Each one
>   has a tailored CV waiting in Drive.>
> - <LinkedIn, you click: Twice each weekday I fill in LinkedIn Easy Apply
>   forms for roles scoring 70 or above and save them. Open Saved jobs on
>   LinkedIn, check each one, and click Submit.>
>   <LinkedIn, automatic: Twice each weekday I submit LinkedIn Easy Apply
>   forms for roles scoring 70 or above, up to 75 a day, and save any I
>   couldn't fill in completely for you to finish.>
>
> Give it three days before you judge it. The first sweep usually finds more
> than the rest because it has no history to dedupe against.
>
> Things you can say to me any time:
>
> - "job search status" for a summary
> - "pause my search", and "resume my search" when you're back
> - "the roles look wrong", and I'll retune the queries
> - "make my search cheaper"
>
> Your sheet: <sheet URL>

If the person wants to change anything later, read `setup/06-tuning.md`.
