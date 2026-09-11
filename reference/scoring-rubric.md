# Scoring rubric

Every sourcing task scores a posting out of 100 before deciding what to do with
it. The rubric is what stops the system applying to everything it finds.

---

## The bands

| Score | What happens |
|---|---|
| 0 | Auto-failed. Not recorded. |
| 1-54 | Discarded. Not recorded. |
| 55-69 | Written to Pipeline as Shortlisted. No CV tailored. Available if the queue runs dry. |
| 70-100 | Written to Pipeline, CV tailored, eligible for an apply run. |

Keyword coverage gates separately. A role scoring 85 with 45% coverage does not
get applied to, because the CV bank cannot produce a CV that matches its job
description. That combination means the role sounds right and reads wrong, and
it is worth telling the person about.

---

## The six components

### Years required, 25 points
Full marks when the stated requirement falls inside the person's band, which is
their years minus 1 to their years plus 4. Half marks when it sits one year
outside. Zero when it sits further out, and an auto-fail when it demands more
than their years plus 4 or caps below their years minus 1.

This is weighted highest because it is the single most common rejection reason
and the easiest to read from a posting.

### Skill overlap, 25 points
Proportion of the posting's named tools, languages and methods that appear in
the CV bank's skills pool. Score it as the proportion, rounded to the nearest 5.

### Location, 20 points
Full marks for the first location in their ranked list, 15 for the second, 10
for the third, 20 for fully remote inside their country. Zero otherwise, unless
relocation there is on their accepted list, in which case 10.

### Domain adjacency, 15 points
Full marks when the company's industry matches one they have worked in. Ten
when it is adjacent, meaning the same buyer or the same problem in a different
sector. Zero when it is unrelated. Industry knowledge shortens ramp time and
interviewers weight it heavily.

### Recency, 10 points
Full marks inside 7 days, 5 inside 14, zero beyond. Auto-fail beyond 30. Reply
rate on a 30-day-old posting is close to zero, because the shortlist is already
drawn.

### Compensation disclosed, 5 points
Full marks when a figure or range appears. This is a small weight doing a
specific job: it biases the system toward employers who are transparent, and it
makes the floor check possible before applying rather than after.

---

## Auto-fails

These produce a score of 0 regardless of everything else. Four are universal
and the rest come from step 1 of setup.

Universal:
- Posted more than 30 days ago.
- Requires more than the person's years plus 4.
- Caps below the person's years minus 1.
- Requires relocation to a location on their never list.

Common additions, offered during setup:
- Specifies working hours in a timezone they excluded.
- Gates on a specific institution or degree they do not hold.
- Unpaid trial period, or a fee to apply.
- Contract-only when they want permanent, or the reverse.
- A named company or industry they refuse.

---

## Tuning the rubric

Read the score distribution in Pipeline before changing anything.

| Symptom | Cause | Fix |
|---|---|---|
| Almost nothing recorded | Auto-fails too broad | Remove the newest addition first |
| Most rows between 40 and 60 | Location or years weighting fights the market | Widen the years band by 1, or add remote to locations |
| Many rows above 70, few above 60% coverage | The CV bank is thin for that family | Return to step 3 and add bullets |
| Rows above 70 that look wrong to the person | Domain adjacency is being scored too generously | Ask what made it wrong, and convert the answer into an auto-fail |

Change one weight at a time and wait a week. The rubric is the system's
judgement, and judgement retuned daily is noise.
