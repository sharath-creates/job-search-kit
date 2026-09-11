# Token budget

Read this once during setup. The figures below are order-of-magnitude estimates
rather than measurements, and they will drift with model and tool changes. The
design principles behind them hold regardless.

---

## The one decision that dominates everything

A scheduled run starts in a fresh session with no memory of setup. It has two
possible shapes:

**Shape A, repo-reading.** The prompt says "read `CLAUDE.md`, then
`me/profile.md`, then `tasks/01-shortlist-sweep.md`, then run it." Every run
pays to load those files. Call it 25,000 to 35,000 tokens of pure overhead
before the task does anything.

**Shape B, self-contained.** Setup substitutes the person's details into the
template once, and the resulting text becomes the scheduled task's prompt. The
run loads nothing. Overhead is the prompt itself, around 1,200 tokens.

At standard intensity the six tasks fire roughly 40 times a week. Shape A costs
something like 1.2 million tokens a week in overhead alone. Shape B costs about
50,000.

This is why `setup/05-schedule.md` insists that no generated prompt may refer to
this repository, and why tuning means editing the scheduled task rather than
editing a file the task reads.

---

## Where the rest of the cost sits

Ranked by size within a single sourcing run:

1. **Fetching postings to score them.** Each fetched page runs 3,000 to 8,000
   tokens. Fifteen of them is the largest line item in the run by a wide
   margin.
2. **Reading the CV bank to tailor.** One read, 2,000 to 4,000 tokens,
   multiplied by the number of roles tailored in that run.
3. **Reading the sheet.** Pipeline grows all search. By week six it is the
   second largest read in the run.
4. **Search results themselves.** Ten calls at limit 10 returns titles and
   snippets, which is cheap.
5. **The prompt.** Fixed and small.

---

## The levers, in order of savings

### 1. Cap fetches, not searches
Searching is cheap and fetching is expensive. A sweep that runs 10 searches and
fetches 8 pages costs less than one that runs 6 searches and fetches 15. Set
`{{FETCH_CAP}}` deliberately and let the search budget run wider.

### 2. Dedupe before fetching, never after
The order in every sourcing task is search, dedupe against Pipeline, then fetch.
Reversing those two means paying to read postings already recorded. By week
four this is most of what a search returns.

### 3. Keep the sheet read narrow
A task needs Company, Role, Status and Date applied to dedupe. It does not need
the Notes column or the whole Log tab. Read the columns the task uses.

### 4. Let the watchlist carry the load
Polling a company board costs one fetch and no search credits, and the diff
against `Known roles` means only new titles get scored. Forty watchlist
companies outproduce four extra search calls at lower cost. Grow the watchlist
before raising the search budget.

### 5. Tailor at 70, not at 55
Tailoring reads the CV bank and writes two documents. Doing it for every
shortlisted role roughly triples the cost of a sweep for roles that will not be
applied to this week.

### 6. Report by exception
Every task in this kit sends nothing when it finds nothing. Composing and
sending a "no results today" email costs tokens and trains the person to ignore
the inbox.

---

## What not to cut

- **The dedupe step.** Removing it saves one sheet read and causes duplicate
  applications, which is the failure that damages an actual job search.
- **The tailoring step.** Removing it saves the CV bank read and drops the
  reply rate toward zero, which wastes every token the system spends finding
  roles.
- **The Log tab.** Removing it saves almost nothing and removes the only way to
  see what a run cost.

---

## Rough monthly figures at standard intensity

| Item | Estimate |
|---|---|
| Search credits | 400 to 500 of Firecrawl's 1,000 free monthly credits |
| Scheduled runs | about 170 |
| Pages fetched | about 600 |
| Documents written | about 120, two per tailored role |

At light intensity, roughly 40% of those. At heavy, roughly 180%.

If the weekly review projects a month-end overrun, it recommends a specific
cut. Take the cuts in the order listed in `setup/06-tuning.md`.
