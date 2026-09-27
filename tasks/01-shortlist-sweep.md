# Template: Shortlist Sweep

Fill every `{{PLACEHOLDER}}`, then create a scheduled task whose prompt is
everything below the line. Nothing below the line may refer to this repository.

**Schedule:** see the grid in `setup/05-schedule.md`.
**Name it:** `Job Search - Shortlist Sweep ({{TIME}} {{TZ}})`

---

Build today's job shortlist for {{NAME}}.

WHO THEY ARE: {{CURRENT_ROLE}}. {{YEARS}} years of experience. Based in {{CITY}}. {{DEADLINE_LINE}}
{{BACKGROUND}}

TARGET FAMILIES:
A) {{FAMILY_A}}: {{FAMILY_A_TITLES}}
B) {{FAMILY_B}}: {{FAMILY_B_TITLES}}

LOCATION PRIORITY: {{LOCATIONS}}

DO NOT APPLY TO ANYTHING. This task finds, scores, tailors and records only.

1. WATCHLIST, zero search credits. Open the Watchlist tab of Google Sheet
   "{{SHEET_NAME}}". Fetch each board URL and diff the roles listed against the
   Known roles cell. Anything new goes into step 3. Update Last polled and
   Known roles. A board that fails to load twice in a row gets its Status set
   to "broken" and is skipped from then on. Report broken boards.

2. DISCOVERY. Use {{SEARCH_TOOL}}. HARD CAP: exactly {{SEARCH_CALLS}} search
   calls, limit 10 each, freshness filter set to the last 24 hours.

   Family A queries, domain filter {{BOARD_DOMAINS}}:
{{QUERIES_A}}

   Family B queries, domain filter {{BOARD_DOMAINS}}:
{{QUERIES_B}}

   The last two calls rotate by weekday across {{REGIONAL_DOMAINS}}, freshness
   set to the last 7 days.

   RULES: never put a site: operator inside a query string, use the domain
   filter parameter. Do not set an include list and an exclude list on the same
   call. Zero results means log it and move on, with no retry.

3. DEDUPE. Read only the Pipeline columns this run uses: Date found, Company,
   Role, Location, URL, Score, Coverage %, Status, Date applied, Question for
   you. Drop anything already in the Pipeline tab, and anything from a company
   that received an application in the last 14 days.

4. SCORE. Fetch at most {{FETCH_CAP}} of the new postings, newest first. Score
   each out of 100:
   - Years required falls inside {{YEARS_BAND}}: 25
   - Overlap with their skills and tools: 25
   - Location is one of {{LOCATIONS}}: 20
   - Industry or domain adjacency to their background: 15
   - Posted within 7 days: 10
   - Compensation disclosed: 5

   AUTO-FAIL, score 0 and do not record:
{{AUTOFAILS}}

5. WRITE everything scoring 55 or above to the Pipeline tab with Status
   "Shortlisted", its family, and its source tier.

6. TAILOR. For every role scoring 70 or above:
   a. Read the Google Doc "{{CV_BANK_DOC}}".
   b. Extract the job description's keyword set.
   c. Select bullets under the bank's 10 tailoring rules and assemble a
      one-page CV.
   d. Write a 150-word cover note using the stock "why this role" answer with
      the company-specific slot filled from the posting.
   e. Save both to Drive at "{{DRIVE_ROOT}}/Applications/<date>/<company>-<role>/".
   f. In the Pipeline row, record the keyword coverage percentage and the CV
      file link, and set Status to "Tailored".
   Below 60% coverage, do not tailor. Leave the row as "Shortlisted" and note
   the reason.

7. LOG. Append one row to the Log tab: date, task name, search calls used,
   credits used, pages fetched, roles found, roles scoring 70+, roles tailored.

8. REPORT by email to {{EMAIL}}. This is their one daily email from the job
   search, so gather everything into it:
   - READY: every row at Status "Tailored" found since the previous Shortlist
     Sweep row in the Log tab, with score, keyword coverage, company, role,
     location and URL. {{APPROVAL_NOTE}}
   - SENT: company and role for every Pipeline row applied to since the
     previous Shortlist Sweep row in the Log tab.
   - WAITING ON YOU: every row with Status "Needs you", with its Question for
     you cell, and a reminder that typing an answer in Your answer lets the
     next apply run finish it. Then one line counting older rows still at
     "Tailored", and one counting rows at "Prefilled" that sit in their
     LinkedIn Saved jobs waiting for their click.
   Subject "Job search <date> - N ready, M sent, K need you". Add one line
   with credits used this month and the sheet link. If READY, SENT and
   WAITING ON YOU are all empty, send nothing. Silence is a valid outcome.

If a tool is unreachable, stop and say which one. Do not retry more than once.
