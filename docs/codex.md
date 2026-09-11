# Running this with Codex or another agent

The kit assumes three things Claude provides: a scheduler, Google connectors,
and a search connector. Each has a substitute. Nothing else changes.

Read this once before running setup with a non-Claude agent, then follow
`AGENTS.md`.

---

## Change 1: scheduling

Claude creates scheduled tasks through its own scheduler. Codex has no
equivalent, so step 5 changes shape: instead of creating six tasks, write six
filled prompt files to `me/tasks/` and hand over the scheduling lines.

Write each filled template to `me/tasks/NN-name.md`, then run it with a
non-interactive invocation. For Codex:

```bash
codex exec --full-auto "$(cat me/tasks/01-shortlist-sweep.md)"
```

Schedule it with cron on macOS or Linux:

```cron
# Shortlist sweep, 07:00 Mon-Sat
0 7 * * 1-6 cd /path/to/job-search-kit && codex exec --full-auto "$(cat me/tasks/01-shortlist-sweep.md)" >> me/runs.log 2>&1

# Sourcing top-up, 13:00 Mon-Sat
0 13 * * 1-6 cd /path/to/job-search-kit && codex exec --full-auto "$(cat me/tasks/02-sourcing-topup.md)" >> me/runs.log 2>&1

# Inbox watch, 08:00 and 20:00 daily
0 8,20 * * * cd /path/to/job-search-kit && codex exec --full-auto "$(cat me/tasks/05-inbox-watch.md)" >> me/runs.log 2>&1

# Weekly review, 10:00 Sunday
0 10 * * 0 cd /path/to/job-search-kit && codex exec --full-auto "$(cat me/tasks/06-weekly-review.md)" >> me/runs.log 2>&1
```

Cron runs in local time, which removes the UTC conversion step that Claude's
scheduler needs.

On Windows, use Task Scheduler with an action running `cmd /c` and the same
command, or use WSL and the cron lines above.

The self-contained rule still applies, and it matters more here. `cat` of the
filled prompt is the entire context the run gets, so a prompt that says "read
the repo" makes every cron run pay for it.

## Change 2: the pipeline store

Without Google connectors, the sheet becomes four CSV files in `me/data/`:

```
me/data/pipeline.csv
me/data/watchlist.csv
me/data/queries.csv
me/data/log.csv
```

Same columns as `reference/sheet-schema.md`, same order. Substitute into the
templates as follows:

| Template phrase | Local replacement |
|---|---|
| `the Pipeline tab of Google Sheet "{{SHEET_NAME}}"` | `me/data/pipeline.csv` |
| `the Watchlist tab` | `me/data/watchlist.csv` |
| `the Queries tab` | `me/data/queries.csv` |
| `the Log tab` | `me/data/log.csv` |
| `Drive at "{{DRIVE_ROOT}}/Applications/..."` | `me/applications/<date>/<company>-<role>/` |
| `the Google Doc "{{CV_BANK_DOC}}"` | `me/cv-bank.md` |
| `the Google Doc "{{ANSWER_SHEET_DOC}}"` | `me/answer-sheet.md` |

CSV is cheaper to read than a sheet connector and it diffs in git, which makes
the pipeline's history inspectable. The cost is that it does not open on a
phone. Someone who wants both can commit `me/data/` to a private repo and read
it on GitHub's mobile view.

Add `me/data/` to `.gitignore` unless the repo is private.

## Change 3: email

Tasks 5 and 6 read Gmail. Without a mail connector:

- **Inbox watch** has no substitute worth building. IMAP through a script is
  possible and is more maintenance than most people want. The honest advice is
  to keep this one task on Claude with a Gmail connector, or to accept that
  inbox monitoring stays manual.
- **Reports** change from email to a written file. Replace "Email a summary to
  {{EMAIL}}" with "Write the summary to `me/reports/<date>-<task>.md`". Losing
  the push notification is the real cost, so pair it with a desktop notification
  in the cron line if that matters.

## Change 4: search

Codex reaches search through whatever MCP server is configured. The last
section of `reference/search-queries.md` covers the parameter differences. The
queries themselves are portable.

## Change 5: the browser tasks

Tasks 3 and 4 need a browser the agent can drive with the person's sessions
logged in. Where that is unavailable, drop both. The remaining four still
source, score, tailor and monitor, and applying becomes a manual step from a
queue that is already prepared. Many people prefer that anyway.

---

## What stays identical

The interview, the rubric, the CV bank format, the tailoring rules, the caps,
the guardrails and the tuning logic. Those are the parts worth having, and none
of them depend on which agent runs them.
