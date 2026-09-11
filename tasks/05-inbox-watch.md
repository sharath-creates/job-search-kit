# Template: Inbox Watch

Fill every `{{PLACEHOLDER}}`, then create a scheduled task whose prompt is
everything below the line.

**Schedule:** per the grid in `setup/05-schedule.md`.
**Name it:** `Job Search - Inbox Watch ({{TIMES}} {{TZ}})`

**Why it exists:** this is the highest-value task in the kit and the cheapest
to run. Applying earns replies. Replies expire. Assessment links commonly run
for 7 days and interview scheduling links for 36 hours, and a missed one wastes
the application that produced it.

---

Inbox watch for {{NAME}}'s job search ({{EMAIL}}). {{DEADLINE_LINE}}
They are {{CURRENT_ROLE}}, targeting {{FAMILY_A}} and {{FAMILY_B}} roles.

DO NOT APPLY TO ANYTHING. Do not run web searches. Read email, classify,
report.

1. Search Gmail over the last 14 days for anything requiring ACTION:
   - interview invitations, calendar invites from unknown senders, scheduling
     links
   - assessment or test links
   - "profile incomplete", "complete your application", "we tried reaching you"
   - recruiter replies asking a direct question
   - offers, or requests for documents, references, or salary expectations

   Queries: newer_than:14d combined with each of interview, assessment,
   schedule, availability, time slot, shortlisted, "complete your application",
   next round, "tried reaching".

   Exclude noise: job board alerts, application confirmations that ask for
   nothing, newsletters, and course marketing.

2. For each item, extract the EXPIRY and compute whether it is still valid as
   of now. Links are commonly time-boxed at 24 hours, 36 hours, or 7 days. This
   is the most important field in the report.

3. Classify each one:
   - ACT NOW: expires within 48 hours, or has already been chased once
   - ACT THIS WEEK
   - EXPIRED: report with a recovery draft
   - FYI: rejections and acknowledgements

4. For every ACT NOW and EXPIRED item, create a Gmail DRAFT reply. Never send.
   Short, professional, no grovelling. Include continued interest, availability
   ({{AVAILABILITY}}), and one or two lines of fit drawn from:
   {{BACKGROUND}}

5. Update the Status column of the Pipeline tab in Google Sheet
   "{{SHEET_NAME}}" for every application that has moved.

6. Append a row to the Log tab.

7. Email a summary to {{EMAIL}}. Subject
   "Inbox watch <date> <AM or PM> - N need action". ACT NOW at the very top,
   with hours remaining and a direct link for each. Then ACT THIS WEEK, then
   EXPIRED with the draft prepared, then a one-line FYI count. If nothing needs
   action, send one line saying so. Do not pad.

8. Flag any company that sent more than one application acknowledgement for the
   same role in the last 14 days. That means the apply run is submitting
   duplicates, and it needs fixing before the next run.
