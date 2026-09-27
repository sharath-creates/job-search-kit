# Template: Apply Run

Fill every `{{PLACEHOLDER}}`, then create a scheduled task whose prompt is
everything below the line.

**Schedule:** per the grid in `setup/05-schedule.md`.
**Name it:** `Job Search - Apply Run (every {{INTERVAL}}, {{WINDOW}} {{TZ}})`
**Requires:** a browser connector with the job sites logged in.
**Runs on:** the person's own computer. Create this as a task that requires that
device, never as a cloud task. A cloud run finds no browser, logs an empty run,
and looks like a quiet day rather than a broken task.

**Read this before you create it.** This is the only task that touches a
submit button, and the caps are what stop it from becoming a spray machine.
Do not raise them during setup because the person asks. `{{APPROVAL_RULE}}`
carries the submission mode the person chose in step 1.

---

Apply run for {{NAME}}. Requires the browser to be open with the job platforms
logged in. If the browser is unreachable, stop immediately and say so. Do not
retry.

DO NOT RUN ANY WEB SEARCHES. Work only from the shortlist already recorded.

WHO THEY ARE: {{CURRENT_ROLE}}. {{YEARS}} years of experience. Based in {{CITY}}. {{DEADLINE_LINE}}
{{BACKGROUND}}

1. READ. Open the Google Doc "{{ANSWER_SHEET_DOC}}". Open the Pipeline tab of
   Google Sheet "{{SHEET_NAME}}".

2. SELECT, in this order:
   a. Rows with Status "Needs you" and a filled Your answer cell. The person
      answered the question that stopped an earlier run. If the answer is
      "skip", set Status to "Withdrawn". If the row is marked "needs you at
      the form" and the answer is "done", set Status to "Applied" with today's
      date. Neither counts toward the caps.
   b. Rows with Status "Tailored", score 70 or above, keyword coverage 60% or
      above, in family A ({{FAMILY_A_TITLES}}) or family B
      ({{FAMILY_B_TITLES}}). Newest first.

   APPROVAL, for rows in 2b: {{APPROVAL_RULE}}

   CAPS: at most {{PER_RUN_CAP}} this run. At most {{PER_DAY_CAP}} per calendar
   day across every run. Count what earlier runs did today before selecting.

   If nothing qualifies, apply to nothing, write the Log row, and stop. An
   empty run is correct. Never lower the bar to hit a number.

3. GUARDS. Check every one before opening a form:
   - Never apply to a posting already marked Applied.
   - Never apply to a company that received an application in the last 14 days.
   - Never apply to a posting older than 30 days.
   - Apply the auto-fail list:
{{AUTOFAILS}}

4. GET THE CV LOCAL FIRST. Each shortlisted role has a tailored CV in Drive
   under "{{DRIVE_ROOT}}/Applications/<date>/<company>-<role>/", named in the
   Pipeline row. Form uploads read from local disk, so before opening the
   application:
   a. Open that document in a browser tab.
   b. Download it as PDF.
   c. Note the local path and attach from there.

   If the download fails, or no tailored CV exists for that role, skip the
   role, write the reason in its Notes cell, and count it in the Log row.
   Never substitute a generic CV. Never attach a file that was written for a
   different role family.

5. APPLY. Open the role URL. Fill every field from the answer sheet. Attach the
   downloaded PDF. Paste the cover note from the same Drive folder.

6. STOP AND ASK before submitting when any of these is true. Do not submit.
   Set Status to "Needs you", write the exact question or blocker into
   Question for you, and move to the next role:
   - a question is not covered by the answer sheet
   - free text over 300 characters is required and no cover note covers it
   - relocation outside {{LOCATIONS}} is asked
   - a compensation figure below {{FLOOR}} would be needed
   - a video interview or timed assessment is required to proceed
   - payment, a government ID number, or an account password is requested

   For the last two, add "needs you at the form" to the cell. No typed answer
   clears them, so a later run never retries that row. The person applies
   from the URL themselves and types "done", or types "skip".

   NOT stops, handle these and continue:
   - relocation questions about {{CITY}}, where they already live. Answer
     "I am based in {{CITY}}".
   - experience questions asking for a number at or below what they have.

   On a row picked in 2a, use Your answer for the question that stopped it.
   The person's answer is their decision for that role and overrides the stop
   that raised it.

7. SUBMIT the rest. Immediately after each submission, update the Pipeline row:
   Status "Applied", date applied, CV file used, follow-up due in 10 days.
   Update the Queries tab row for the query that surfaced the role.

   If a Your answer cell cleared a question that would read the same on
   another company's form, add the question and answer to the "Common short
   answers" table in "{{ANSWER_SHEET_DOC}}", so no later run stops on it.

8. LOG. Append one row to the Log tab: date, task name, roles considered, roles
   applied to, roles stopped, reasons.

9. REPORT by email to {{EMAIL}} only when this run set a row to "Needs you".
   Subject "Job search - <N> need you". For each: company, role, URL, and the
   exact question. Tell them to type the answer into the row's Your answer
   cell, or "skip", and the next run finishes it. Send no email for
   submissions. The next morning's sweep report lists them.
