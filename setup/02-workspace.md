# Step 2: Workspace

**Goal:** create the Google Sheet every task reads and writes, and the Drive
folder tree that holds tailored CVs.

**Output:** a Google Sheet, a Drive folder, and the sheet URL recorded in
`me/setup-state.md`.

**Time:** 3 minutes, mostly you working.

---

## Say this first

> Building your tracker now. You don't need to do anything. I'll tell you when
> it's ready and give you the link.

---

## 1. Create the sheet

Search Drive for a sheet named `Job Search <current year>`. If one exists, ask
whether to use it or create a fresh one. Otherwise create it with four tabs.

Full column definitions are in `reference/sheet-schema.md`. Read that file now,
create the tabs exactly as specified, and do not improvise column names. Every
task template refers to these columns by name.

Summary of the four tabs:

| Tab | Holds |
|-----|-------|
| `Pipeline` | One row per job posting, from discovery through outcome |
| `Watchlist` | Company job boards polled for free on every sweep |
| `Queries` | Which searches are producing applications, and which to retire |
| `Log` | One row per task run: what fired, what it cost, what it found |

Freeze the header row on each tab.

## 2. Seed the watchlist

The watchlist is the cheapest source in the system. Polling a company's own job
board costs no search credits, and postings appear there before they appear
anywhere else.

Seed it with twenty to forty companies:

1. Start with the calibration companies from `me/profile.md`.
2. Add companies in the same industry and size band, in their target locations.
   Use your own knowledge first. Spend at most two searches here.
3. For each company, find its board URL. Most sit on one of these hosts:
   `job-boards.greenhouse.io/<company>`, `jobs.lever.co/<company>`,
   `jobs.ashbyhq.com/<company>`, `<company>.myworkdayjobs.com`,
   `jobs.smartrecruiters.com/<company>`, `apply.workable.com/<company>`.
4. Write each row with the board URL, today's date as `Last polled`, and a
   blank `Known roles`.

Drop any company whose board URL you cannot confirm. A broken URL costs a
failed fetch on every sweep for months.

## 3. Create the Drive folders

```
Job Search <year>/
  CV bank/              <- step 3 writes here
  Applications/         <- tasks write here, one folder per role
  Reference/            <- answer sheet copy, step 4
```

## 4. Record it

Append to `me/setup-state.md`:

```markdown
## Workspace
- Sheet: <name> <URL>
- Drive root: Job Search <year>
- Watchlist seeded: <N> companies
```

Mark step 2 done and step 3 next.

---

## Then say

> Your tracker is live: <URL>
>
> I seeded the watchlist with <N> company job boards. Those get checked every
> morning for free, before any paid searching happens.
>
> Next I need your CV. This is the step that decides whether your applications
> get read.

Read `setup/03-cv-bank.md`.
