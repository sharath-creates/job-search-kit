# Template: Sourcing Top-up

Fill every `{{PLACEHOLDER}}`, then create a scheduled task whose prompt is
everything below the line.

**Schedule:** midday, per the grid in `setup/05-schedule.md`. Off at light
intensity.
**Name it:** `Job Search - Sourcing Top-up ({{TIME}} {{TZ}})`

**Why it exists:** the morning sweep runs before most postings go live. This
keeps the apply queue full through the afternoon at a quarter of the cost.

---

Midday sourcing top-up for {{NAME}}. {{DEADLINE_LINE}}

WHO THEY ARE: {{CURRENT_ROLE}}. {{YEARS}} years of experience. Based in {{CITY}}.

DO NOT APPLY TO ANYTHING.

HARD CAP: exactly 4 search calls on {{SEARCH_TOOL}}, limit 10 each, freshness
set to the last 24 hours.

Call 1, domain filter {{BOARD_DOMAINS_PRIMARY}}:
  {{TOPUP_QUERY_1}}
Call 2, domain filter {{BOARD_DOMAINS_SECONDARY}}:
  {{TOPUP_QUERY_2}}
Call 3, domain filter {{REGIONAL_DOMAINS}}:
  {{TOPUP_QUERY_3}}
Call 4, no include filter, exclude {{NOISE_DOMAINS}}:
  {{TOPUP_QUERY_4}}

Never put a site: operator inside a query string. Do not set an include list and
an exclude list on the same call.

DEDUPE against the Pipeline tab of Google Sheet "{{SHEET_NAME}}", and against
any company that received an application in the last 14 days.

Fetch at most 8 new URLs and score them with the same rubric the morning sweep
uses:
- Years required falls inside {{YEARS_BAND}}: 25
- Overlap with their skills and tools: 25
- Location is one of {{LOCATIONS}}: 20
- Industry or domain adjacency: 15
- Posted within 7 days: 10
- Compensation disclosed: 5

Same auto-fails:
{{AUTOFAILS}}

Append everything scoring 55 or above to Pipeline as "Shortlisted".

For every role scoring 70 or above, read "{{CV_BANK_DOC}}", extract the job
description's keyword set, assemble a one-page CV under the bank's 10 tailoring
rules, write a 150-word cover note, and save both to
"{{DRIVE_ROOT}}/Applications/<date>/<company>-<role>/". Record keyword coverage
in the Pipeline row. Below 60% coverage, do not tailor.

Append a row to the Log tab.

Email {{EMAIL}} only if something scored 70 or above. Keep it to one screen:
each role with score, coverage and URL, plus credits used this month.
