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

3. DEDUPE. Drop anything already in the Pipeline tab, and anything from a
   company that received an application in the last 14 days.

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
   f. Record the keyword coverage percentage in the Pipeline row.
   Below 60% coverage, do not tailor. Move the row to the 55-69 band and note
   the reason.

7. LOG. Append one row to the Log tab: date, task name, search calls used,
   credits used, pages fetched, roles found, roles scoring 70+, roles tailored.

8. REPORT by email to {{EMAIL}}, only if something scored 70 or above. Subject
   "Shortlist <date> - N roles ready". List each with score, keyword coverage,
   company, role, location and URL. Add one line with credits used this month.
   If nothing scored 70+, send nothing. Silence is a valid outcome.

If a tool is unreachable, stop and say which one. Do not retry more than once.
