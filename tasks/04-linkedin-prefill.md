# Template: LinkedIn Prefill

Fill every `{{PLACEHOLDER}}`, then create a scheduled task whose prompt is
everything below the line.

**Schedule:** twice on weekdays, per the grid in `setup/05-schedule.md`.
**Name it:** `Job Search - LinkedIn Prefill ({{TIMES}} {{TZ}})`
**Requires:** a browser connector, with LinkedIn logged in.
**Runs on:** the person's own computer. Create this as a task that requires that
device, never as a cloud task. A cloud run finds no browser, logs an empty run,
and looks like a quiet day rather than a broken task.

**Read this before you create it.** LinkedIn's user agreement prohibits
automated interaction, and their detection restricts accounts that do it. An
account restriction in the middle of a job search is expensive. By default this
task fills each application, saves it, and leaves the final click to the
person. `{{LINKEDIN_SUBMIT_RULE}}` carries their choice from step 1. Use the
automatic text only if they asked for it by name after hearing that risk.

---

LinkedIn Easy Apply preparation for {{NAME}}. Requires the browser open with
LinkedIn logged in. If the browser is unreachable, stop immediately and say so.
Do not retry.

WHO THEY ARE: {{CURRENT_ROLE}}. {{YEARS}} years of experience. Based in {{CITY}}. {{DEADLINE_LINE}}
{{BACKGROUND}}

SUBMITTING: {{LINKEDIN_SUBMIT_RULE}}

DAILY CAP: at most {{LINKEDIN_DAY_CAP}} roles per calendar day across both
runs, saved and submitted together. LinkedIn limits how many Easy Apply
applications an account can send in a day. Before you start, count the
Pipeline rows with Source "LinkedIn Easy Apply" and today's Date found, and
stop filling when the count reaches the cap.

1. Read the Google Doc "{{ANSWER_SHEET_DOC}}". Open the Pipeline and Log tabs
   of Google Sheet "{{SHEET_NAME}}". Note when the previous LinkedIn Prefill
   run started, from its Log row.

   CATCH UP. Open LinkedIn's list of jobs they have applied to. For every
   Pipeline row at Status "Prefilled" with Source "LinkedIn Easy Apply" that
   appears there, set Status to "Applied" and Date applied to the date
   LinkedIn shows. The person pressed submit since the last run.

2. SEARCH. Run one LinkedIn Jobs search for each title below, one title at a
   time, filtered to Easy Apply and posted in the past week, located
   {{LOCATIONS}}:
   - {{FAMILY_A_TITLES}}
   - {{FAMILY_B_TITLES}}

   Keep only postings listed after the previous run started. An earlier run
   already scored the rest. With no previous run in the Log, keep the last 24
   hours.

3. FILTER OUT before opening anything:
{{AUTOFAILS}}
   - any role already in the Pipeline tab, matched by job URL or by company
     and title, whatever its Status. A role found on a company site gets a
     tailored CV through the apply run instead.
   - any company that received an application in the last 14 days, or that
     already has a role at "Prefilled", so a second saved role cannot break
     the 14-day company cooldown

4. SCORE. If today's count has already reached the daily cap, write the Log
   row and stop. Otherwise, for each title, open at most
   {{LINKEDIN_READ_CAP}} of the remaining postings, newest first, and read
   each job description. Score each out of 100 with the same rubric the
   morning sweep uses:
   - Years required falls inside {{YEARS_BAND}}: 25
   - Overlap with their skills and tools: 25
   - Location is one of {{LOCATIONS}}: 20
   - Industry or domain adjacency to their background: 15
   - Posted within 7 days: 10
   - Compensation disclosed: 5

   Drop anything scoring below 70, and do not record it. If nothing reaches
   70, write the Log row and stop. An empty run is correct. Never lower the
   bar to fill the run.

5. FILL every role scoring 70 or above, highest score first, until the daily
   cap is reached. Click Easy Apply and fill every field from the answer
   sheet: contact details, current and expected compensation, notice period
   and earliest joining date, location and relocation, work authorisation,
   years of experience, and the screening questions. Leave optional extras such as "Mark job as a top
   choice" unticked. Those picks are limited, so they are the person's call.

   CV: use the CV already saved on their LinkedIn account. Keep the one the
   form selects, or pick the most recent if it selects none. Never upload a
   file, and never build or tailor a CV here. LinkedIn does not keep uploaded
   files in a saved application, and tailored CVs are for applications on
   company sites, which the apply run handles.

   Leave a field blank and flag it when:
   - the answer sheet does not cover it
   - relocation outside {{LOCATIONS}} is asked
   - a figure below {{FLOOR}} would be needed
   Relocation questions about {{CITY}} are not blockers. Answer "I am based in
   {{CITY}}".

6. FINISH each one as SUBMITTING says. To save one for the person, go through
   to the final review screen and keep the filled answers with whichever save
   option LinkedIn offers:
   - a "Save Draft" button in the form: click it
   - otherwise close the Easy Apply window, and when LinkedIn asks "Save this
     application?", click Save
   Never click Discard. If neither option appears, leave the form open, write
   "not saved" in the row's Notes cell, and name it in the email.

   Then click Save on the job posting itself, so it appears in their Saved
   jobs. A saved role is never submitted by this task.

7. RECORD each in the Pipeline tab with today's date as Date found, its
   score, Source "LinkedIn Easy Apply", Source tier 3, CV file "LinkedIn profile CV", and the job URL.
   Status "Prefilled" for a saved role. Status "Applied" with today's date for
   a submitted one. Without these rows, the dedupe and the weekly review never
   see LinkedIn applications.

8. If a role also has a posting on the company's own board or an applicant
   tracking system, note it so they can apply there instead. Easy Apply has the
   lowest response rate of any channel, because it is frictionless for every
   applicant.

9. Append a row to the Log tab. Count the postings you read under Pages
   fetched, and submissions under Applications.

10. REPORT by email to {{EMAIL}} only if this run saved or submitted at least
    one role. Subject "LinkedIn - <N> saved for you, <M> sent". List each by
    company, role and score. For each saved role, name any field left blank
    and why. Tell them the saved roles are in Saved jobs under My jobs on
    LinkedIn: open each, check the answers, and click Submit. If nothing was
    saved or sent, send nothing.
