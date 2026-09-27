# Troubleshooting

Ordered by how often people hit them.

---

## A task fired and nothing happened

Check the Log tab first. A run that completed writes a row there.

| Log row | Meaning | Fix |
|---|---|---|
| No row at all | The task failed before reaching step 1, usually a connector | Re-run the task manually and read the error |
| Row with `Roles found: 0` | The searches returned nothing | Normal on a quiet day. Three days running means the queries are wrong. Read `reference/search-queries.md`. |
| Row with an error string | Named failure | Fix what it names |

A run reporting zero applications is often correct. The caps and thresholds are
designed to produce empty runs rather than bad applications.

## Roles are tailored but nothing gets sent

Check `Submission` in `me/setup-state.md`.

- **You approve:** the apply run sends only rows with the Approve box ticked.
  Rows at `Tailored` with no tick are waiting on the person, which is the
  system working as designed.
- **Automatic:** check the Log tab for apply run rows. No rows means the
  browser task is not firing: confirm it is bound to this computer, and that
  the computer was awake with Chrome open.

## A row says "Needs you"

A form asked something the answer sheet does not cover. The question sits in
the row's Question for you cell. Type the answer in Your answer, or `skip`, and
the next apply run finishes it. Answers that would apply to any company get
added to the answer sheet, so the same question stops a run only once.

A cell marked "needs you at the form" is a timed test, a video step, a payment
or a password. Apply from the URL yourself and type `done`.

## I'm getting too many emails

The kit sends one email each morning, plus inbox watch alerts when something
needs action, plus a LinkedIn prefill notice after a run that saved roles for
you.
More than that means a task prompt predates the one-email design. Say "update
my tasks" and Claude re-fills them from the current templates.

## LinkedIn saved jobs open with empty answers

LinkedIn Prefill saves each filled application before it closes the Easy Apply
window. If a saved job opens with the answers gone, LinkedIn discarded the
draft. The job is still in Saved jobs and its Pipeline row still has the
score, so apply from there with your answer sheet to hand.

## My LinkedIn account got restricted

Say "my LinkedIn got restricted". Claude switches LinkedIn back to "you click"
and turns the LinkedIn task off until you say the restriction is lifted. The
other five tasks carry on.

## Search credits are burning faster than expected

Check the Log tab's Search calls column against the cap in the task prompt. If
actual exceeds the cap, the prompt was created with the wrong number, since a
correctly written prompt states an exact count.

Common causes:
- Both sourcing tasks are running at light intensity. Task 2 should be off.
- A query contains a `site:` operator, which returns nothing and gets retried.
- The apply run is running searches. It must not. Its prompt says so explicitly,
  and if it is searching, the prompt was edited.

## The sheet is not updating

- Confirm the task prompt names the sheet exactly as it exists in Drive. A
  renamed sheet breaks every task at once.
- Confirm the Google connector is still authorised. Connectors expire.
- Check whether the sheet was moved into a shared drive the connector cannot
  reach.

## Browser tasks fail

Tasks 3 and 4 need the browser open with the sites logged in. They are written
to stop immediately rather than retry, so a failure report saying the browser
is unreachable is the task working correctly.

If the browser is open and they still fail, the site permissions in the browser
extension need granting for that domain.

## Too many low-quality roles

Raise the shortlist threshold from 55 to 65, then look at what the junk has in
common and convert it into an auto-fail. Read the tuning table in
`reference/scoring-rubric.md`.

## Good roles with low keyword coverage

The CV bank is thin for that family. Return to `setup/03-cv-bank.md` and add
bullets, particularly ones carrying the vocabulary those postings use.

## Duplicate applications

This is the failure the kit works hardest to prevent, so treat it as serious.

1. Read the weekly review's duplicate audit for the company and dates.
2. Check whether the apply run's 14-day cooldown guard is present in its prompt.
3. Check whether two apply runs fired inside the same hour, which happens when a
   cron expression was converted to UTC incorrectly.
4. Check whether the same company appears twice in Pipeline under slightly
   different names, which defeats the dedupe. Normalise the names.

## Nothing is converting

Give it three weeks and twenty applications per family before concluding
anything. Then read the weekly review's conversion check. It compares by family
and by source, and one of those two is usually carrying the problem.

If both families are flat after forty applications with tailored CVs, the
problem is upstream of this system. The CV bank's strongest bullets, the target
seniority, or the compensation floor are worth revisiting with a person rather
than a task.

## Starting over

Delete `profile.md`, `answer-sheet.md` and `setup-state.md` from `me/`, disable
the six tasks, and say "run setup". Your CV, the sheet and the CV bank survive,
and setup offers to reuse them.
