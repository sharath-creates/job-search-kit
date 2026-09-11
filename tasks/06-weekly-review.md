# Template: Weekly Review

Fill every `{{PLACEHOLDER}}`, then create a scheduled task whose prompt is
everything below the line.

**Schedule:** Sunday morning.
**Name it:** `Job Search - Weekly Review ({{TIME}} {{TZ}})`

**Why it exists:** the other five tasks execute. This one decides whether the
strategy is working, and it is the only task permitted to recommend killing
part of the system.

---

Weekly job search review for {{NAME}} ({{EMAIL}}). {{DEADLINE_LINE}}

1. RECONCILE. Search Gmail for replies to applications from the last 21 days:
   confirmations, recruiter screens, rejections, interview invites, assessment
   links. Update the Status column in the Pipeline tab of Google Sheet
   "{{SHEET_NAME}}".

2. FOLLOW UP. List applications past their follow-up date with no reply. Draft
   a short follow-up to the recruiter or careers address where one exists. Save
   as Gmail drafts. Do not send.

3. DEEP DISCOVERY. {{SEARCH_TOOL}}, hard cap {{WEEKLY_SEARCH_CALLS}} calls at
   limit 10. Find companies hiring {{FAMILY_A_TITLES}} or {{FAMILY_B_TITLES}}
   in {{LOCATIONS}} that are not yet on the Watchlist tab. Propose additions
   with their board URL. Weight the first location highest.

4. QUERY PERFORMANCE. Update the Queries tab with applications sent and
   interviews per query. Retire any query with 3 or more runs and zero
   applications. Propose two replacements.

5. DUPLICATE AUDIT. Flag any company that received more than one application
   in the last 14 days. Name the task that sent them and the dates.

6. TAILORING AUDIT. Check that every row marked Applied has a tailored CV
   recorded and a keyword coverage percentage. Flag any that went out without
   one. Applying with a generic CV is the single largest cause of a low reply
   rate.

7. CONVERSION CHECK. Compare reply rate by family (A: {{FAMILY_A}},
   B: {{FAMILY_B}}) and by source (company boards, each applicant tracking
   system, each regional board, LinkedIn). Recommend shifting effort toward
   whichever is converting. If one family has produced nothing after 20 or more
   applications, say so plainly and recommend retiring it.

8. COST. Total the Log tab for the week: search calls, credits, pages fetched.
   Compare against the monthly allowance and project the month-end figure. If
   the projection exceeds the allowance, recommend a specific cut.

9. EMAIL a summary to {{EMAIL}}, under one screen:
   - {{DEADLINE_LINE}}
   - applications sent this week, replies, interviews scheduled
   - applied-to-reply rate, overall and by family
   - credits used this month against the allowance
   - the retire and add recommendations, at most three, each one line

   Lead with whichever number moved most. Do not open with a recap of what the
   system did.
