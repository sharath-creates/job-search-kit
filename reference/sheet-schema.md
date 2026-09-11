# Sheet schema

Four tabs in one Google Sheet named `Job Search <year>`. Create the columns
exactly as written. Every task template refers to them by name, so a renamed
column breaks a task silently.

Freeze the header row on every tab.

---

## Tab 1: Pipeline

One row per posting, from discovery through outcome.

| Column | Type | Written by | Notes |
|---|---|---|---|
| Date found | date | sourcing | |
| Company | text | sourcing | |
| Role | text | sourcing | |
| Family | A or B | sourcing | |
| Source tier | 1, 2 or 3 | sourcing | Which domain tier surfaced it |
| Source | text | sourcing | The specific board or host |
| Location | text | sourcing | |
| URL | link | sourcing | |
| Score | number | sourcing | Out of 100 |
| Coverage % | number | tailoring | Keyword match against the job description |
| Status | list | several | See the status list below |
| Date applied | date | apply run | |
| CV file | link | tailoring | The Drive doc used |
| Follow-up due | date | apply run | Date applied plus 10 days |
| Last contact | date | inbox watch | |
| Notes | text | any | One line. Reasons for stops and skips go here. |

Status values, in order: `Shortlisted`, `Tailored`, `Prefilled`, `Applied`,
`Replied`, `Screening`, `Interviewing`, `Offer`, `Rejected`, `Withdrawn`,
`Expired`.

Nothing writes a status that skips backwards. An apply run never sets a row
back to Shortlisted.

## Tab 2: Watchlist

Company boards polled for free on every sweep. This is the cheapest source in
the system and should be the largest.

| Column | Type | Notes |
|---|---|---|
| Company | text | |
| Board URL | link | The applicant tracking system board, not the marketing careers page |
| Tier | 1, 2 or 3 | Priority when the sweep runs short on time |
| Last polled | date | |
| Known roles | text | Titles seen last poll, comma separated. The diff source. |
| New this poll | number | |
| Status | list | `active` or `broken` |

A board that fails twice gets `broken` and is skipped until someone fixes the
URL. Without this rule, a dead board costs a failed fetch every morning
indefinitely.

## Tab 3: Queries

What each search is producing. This tab is the reason the system gets better
rather than merely persistent.

| Column | Type | Notes |
|---|---|---|
| Query | text | The exact string |
| Domain filter | text | Which tier and which domains |
| Freshness | text | `24h` or `7d` |
| Weekday | text | `all`, or the rotation days |
| Times run | number | |
| Roles surfaced | number | |
| Roles scoring 70+ | number | |
| Applications | number | |
| Interviews | number | |
| Status | list | `active` or `retired` |
| Retired on | date | |

The weekly review retires anything with 3 or more runs and zero applications.

## Tab 4: Log

One row per task run. This is how cost gets controlled and how a silent failure
becomes visible.

| Column | Type | Notes |
|---|---|---|
| Timestamp | datetime | |
| Task | text | Task name |
| Search calls | number | |
| Credits | number | |
| Pages fetched | number | |
| Roles found | number | |
| Roles 70+ | number | |
| Applications | number | |
| Outcome | text | One line |
| Errors | text | Blank when clean |

A task that fires and writes no Log row has failed. That is the first thing to
check when someone says nothing is happening.

---

## Why a sheet rather than a database

The person needs to open this on a phone, sort it, and see at a glance what is
waiting on them. A sheet does that with no tooling. The cost is that every task
reads and writes through a connector, which is slower than a local file and
occasionally rate-limited. `docs/codex.md` covers the local CSV alternative for
anyone without Google connectors.
