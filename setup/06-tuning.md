# Tuning

Read this when someone asks to change a running system. Handle the request,
update the affected task prompts and `me/` files, and report what changed.

Changing a task's prompt means updating the scheduled task itself, since the
prompt carries the person's details rather than reading them at run time.

---

## "Nothing good is showing up"

Diagnose in this order. Stop at the first cause you find.

1. **Read the Queries tab.** Any query with three or more runs and zero
   applications is dead. Retire it and propose two replacements from
   `reference/search-queries.md`.
2. **Read the score distribution in Pipeline.** If most rows sit between 40 and
   60, the rubric's location or years weighting is fighting the market. If
   almost nothing is being written at all, the auto-fails are too broad.
3. **Check the watchlist.** If `Last polled` has not moved in days, the board
   URLs are broken. Re-verify them.
4. **Ask about the families.** If one family has produced nothing in twenty
   applications, say so plainly and recommend retiring it.

## "It's finding too much junk"

Raise the shortlist threshold from 55 to 65. Add auto-fails for whatever the
junk has in common. Narrow the domain filters toward company boards and away
from aggregators.

## "It costs too much"

In order of savings:

1. Drop task 2 entirely. It is the redundant one.
2. Cut `{{FETCH_CAP}}` from 15 to 8. Scoring fetches are the largest single
   cost in a sweep.
3. Cut `{{SEARCH_CALLS}}` from 10 to 6.
4. Move task 1 from daily to Monday, Wednesday, Friday.
5. Move apply runs from every three hours to twice a day.

Never save tokens by having a task read the repo, by removing the dedupe step,
or by dropping the tailoring step. Each of those costs more than it saves.

## "I want to change what I'm going for"

Re-run the family block of `setup/01-discovery.md`. Then:

- Rewrite the family sections of `me/profile.md`.
- Re-tag the CV bank for the new family and add a summary variant.
- Rebuild the query set.
- Update every task prompt that carries `{{FAMILY_*}}`.
- Add a note in the sheet's Log tab, so the weekly review knows the comparison
  window restarted.

## "I got an interview"

Update the Pipeline row. Then offer, without being asked twice:

> Want me to pull together what I know about them, and the questions this role
> is likely to open with?

## "I accepted an offer"

Disable all six tasks. Do not delete them. Write a closing summary into the Log
tab: applications sent, replies, interviews, and which family and which source
produced the offer. That last line is the most useful thing the system will
ever tell them.

## "Start over"

Delete the four files in `me/`, disable the tasks, and read
`setup/00-prerequisites.md`.
