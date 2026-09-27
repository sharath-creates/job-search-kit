# Template: LinkedIn Prefill

Fill every `{{PLACEHOLDER}}`, then create a scheduled task whose prompt is
everything below the line.

**Schedule:** per the grid in `setup/05-schedule.md`. Off at light intensity.
Evening by default, so the prefilled forms are waiting when the person gets to
the computer.
**Name it:** `Job Search - LinkedIn Prefill ({{TIMES}} {{TZ}})`
**Requires:** a browser connector, with LinkedIn logged in.
**Runs on:** the person's own computer. Create this as a task that requires that
device, never as a cloud task. A cloud run finds no browser, logs an empty run,
and looks like a quiet day rather than a broken task.

**Read this before you create it.** LinkedIn's user agreement prohibits
automated interaction, and their detection restricts accounts that do it. An
account restriction in the middle of a job search is expensive. This task
prepares applications and leaves the final click to the person. Every version
of this prompt must keep that boundary. Say so to the person before creating
it, and let them decline.

---

LinkedIn Easy Apply preparation for {{NAME}}. Requires the browser open with
LinkedIn logged in. If the browser is unreachable, stop immediately and say so.
Do not retry.

HOW THIS TASK WORKS: it fills every field and then stops. Never click Submit,
never click Send application, and never advance past the final review screen.

WHO THEY ARE: {{CURRENT_ROLE}}. {{YEARS}} years of experience. Based in {{CITY}}. {{DEADLINE_LINE}}

1. Read the Google Doc "{{ANSWER_SHEET_DOC}}". Open the Pipeline tab of
   Google Sheet "{{SHEET_NAME}}".

   CATCH UP. Open LinkedIn's list of jobs they have applied to. For every
   Pipeline row at Status "Prefilled" with Source "LinkedIn Easy Apply" that
   appears there, set Status to "Applied" and Date applied to the date
   LinkedIn shows. The person pressed submit since the last run.

2. Search LinkedIn Jobs, filtered to Easy Apply, posted in the last 24 hours,
   located {{LOCATIONS}} in that order:
   - {{FAMILY_A_TITLES}}
   - {{FAMILY_B_TITLES}}

3. FILTER OUT before opening anything:
{{AUTOFAILS}}
   - any role already in the Pipeline tab at a Status other than "Shortlisted"
     or "Tailored"
   - any company that received an application in the last 14 days

4. Take at most 5 roles per run. For each, open the Easy Apply flow and fill
   every field from the answer sheet.
   CV: if the Pipeline row holds a CV tailored to that role, attach it.
   Otherwise attach nothing and flag that the role needs tailoring first. Never
   attach a generic CV.

5. Leave each one on the final review screen, unsubmitted. Do not close the
   tabs. Record each in the Pipeline tab with Status "Prefilled", Source
   "LinkedIn Easy Apply", Source tier 3, and the job URL. Update the row if
   the role is already there. Without this, the dedupe and the weekly review
   never see LinkedIn applications.

6. Leave a field blank and flag it when:
   - the answer sheet does not cover it
   - relocation outside {{LOCATIONS}} is asked
   - a figure below {{FLOOR}} would be needed
   Relocation questions about {{CITY}} are not blockers. Answer "I am based in
   {{CITY}}".

7. If a role also has a posting on the company's own board or an applicant
   tracking system, note it so they can apply there instead. Easy Apply has the
   lowest response rate of any channel, because it is frictionless for every
   applicant.

8. Append a row to the Log tab.

9. REPORT by email to {{EMAIL}} only if this run prefilled at least one role.
   Subject "LinkedIn - <N> ready for your click". List them by company and
   role, with the tab each is in, plus any fields left blank and why. Remind
   them these expire with the browser session. If nothing was prefilled, send
   nothing.
