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

Convert from `me/profile.md`. Times below are local; convert each to UTC using
their timezone before creating anything, and shift the day-of-week field if the
conversion crosses midnight.

| Task | Light | Standard | Heavy |
|------|-------|----------|-------|
| 1 Shortlist Sweep | 07:00 Mon, Wed, Fri | 07:00 Mon-Sat | 07:00 daily |
| 2 Sourcing Top-up | off | 13:00 Mon-Sat | 13:00 and 17:00 daily |
| 3 Apply Run | 10:00 and 16:00 Mon-Fri | every 3h, 09:00-21:00 Mon-Fri | every 2h, 09:00-21:00 Mon-Fri |
| 4 LinkedIn Prefill | off | 11:00 and 14:00 Mon-Fri | 11:00, 14:00, 17:00 Mon-Fri |
| 5 Inbox Watch | 08:00 daily | 08:00 and 20:00 daily | 08:00, 14:00, 20:00 daily |
| 6 Weekly Review | 10:00 Sunday | 10:00 Sunday | 10:00 Sunday |

Caps by level:

| | Light | Standard | Heavy |
|---|---|---|---|
| Applications per apply run | 1 | 2 | 3 |
| Applications per day, all runs | 4 | 8 | 12 |
| Search calls per sweep | 6 | 10 | 14 |
| Pages fetched for scoring per sweep | 8 | 15 | 20 |

Show the person their grid and ask:

> Here's the schedule. Times are yours, local. Anything you want moved?

If they said no to browser tasks in step 0, drop tasks 3 and 4 and say so.

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
| `{{WEEKLY_SEARCH_CALLS}}` | Twice `{{SEARCH_CALLS}}`, capped at 20 |
| `{{SEARCH_TOOL}}` | Search connector name |
| `{{TZ}}` `{{TIME}}` `{{TIMES}}` `{{INTERVAL}}` `{{WINDOW}}` | Their timezone and the local times from the schedule grid. These appear in task names, not in prompt bodies. |
| `{{QUERIES_A}}` `{{QUERIES_B}}` | Built in the next section |
| `{{TOPUP_QUERY_1}}` to `{{TOPUP_QUERY_4}}` | The four highest-yield queries from the set, one per domain tier |
| `{{BOARD_DOMAINS}}` `{{BOARD_DOMAINS_PRIMARY}}` `{{BOARD_DOMAINS_SECONDARY}}` `{{REGIONAL_DOMAINS}}` `{{NOISE_DOMAINS}}` | The domain tier lists in `reference/search-queries.md`, narrowed to their locations |

Verify before creating each task: no `{{` remains anywhere in the prompt.

## 3. Build the query set

Read `reference/search-queries.md` once. Using their two families and their
locations, write six to ten queries and assign domain filters. Write the
resulting list into the `Queries` tab of the sheet and into `{{QUERIES_A}}` and
`{{QUERIES_B}}`.

If the search tool is not Firecrawl, that file's last section covers the syntax
differences. Adapt the queries before substituting them.

## 4. Create the tasks

Create each one disabled if the person wants to review first. Otherwise create
them live.

Then create them. Record every ID.

## 5. Record it

Append to `me/setup-state.md`:

```markdown
## Tasks
| # | Name | ID | Schedule (local) | Enabled |
|---|------|-----|------------------|---------|

## Settings
- Intensity: <level>
- Per-run cap: <N>, per-day cap: <N>
- Search calls per sweep: <N>, credits per month estimated: <N>
- Timezone: <tz>
```

Mark all steps done.

---

## Then say

> Everything's live. Here's what happens next:
>
> - Tomorrow at <time>, the first sweep runs and fills your sheet.
> - At <time>, inbox watch starts checking for replies.
> - Nothing gets submitted without you.
>
> Give it three days before you judge it. The first sweep usually finds more
> than the rest because it has no history to dedupe against.
>
> Two things to do yourself:
>
> 1. Open <sheet URL> tomorrow and look at what scored above 70. If the roles
>    look wrong, tell me and I'll retune the queries.
> 2. Say "job search status" any time for a summary.

If the person wants to change anything later, read `setup/06-tuning.md`.
