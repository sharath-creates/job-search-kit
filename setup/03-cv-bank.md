# Step 3: CV bank

**Goal:** turn one CV into a bank of reusable, evidence-carrying bullets that a
scheduled task can select from to build a one-page CV tailored to any single
job description.

**Output:** a Google Doc named `CV BANK (do not send)` in `Job Search <year>/CV bank/`.

**Time:** 10 minutes, and it needs the person's attention.

---

## Say this first

> Applicant tracking systems rank you on how closely your CV matches the job
> description. One CV sent to fifty jobs matches none of them well.
>
> So we're not making one CV. We're making a bank: every achievement you have,
> written once, tagged. When a task finds a good role, it picks the twelve
> bullets that match that job description and assembles a one-page CV from
> them. Same facts every time, different selection.
>
> Send me your CV and I'll start.

---

## 1. Extract

Read their CV. Pull out every distinct achievement, responsibility and skill.
Aim for thirty to fifty raw items. Include things they undersold.

Then find the gaps. For any role lasting more than six months with fewer than
four extracted bullets, ask:

> Your time at <company> is thin in the bank. Tell me one thing you did there
> that you'd mention in an interview, and what changed because of it.

Ask this at most three times. Do not interrogate.

## 2. Rewrite each bullet

Every bullet follows the same shape: **action, object, mechanism, result.**

> Rebuilt the quote approval flow in the internal pricing tool, cutting sales
> turnaround from 24 hours to under 5 minutes.

Rules:

- Lead with a verb. Never lead with "Responsible for" or "Worked on".
- One sentence. Under 30 words.
- Carry a number wherever one exists. Time saved, volume handled, revenue,
  headcount, error rate, adoption.
- Where no number exists, carry a consequence instead. "Which unblocked the
  Q3 launch" beats a vague claim.
- Never invent a number. If they cannot recall one, ask once, then leave the
  bullet without one.

## 3. Tag each bullet

Tag every bullet with:

- **Family:** A, B, or both. Which target family it supports.
- **Keywords:** three to six terms a job description would use. These drive
  selection, so use the market's vocabulary, not the company's internal names.
- **Strength:** 1 to 3. A 3 is an achievement with a number and clear
  ownership. A 1 is a responsibility with no outcome.

## 4. Write the bank

Structure the Google Doc exactly like this. The tasks parse it.

```
# CV BANK (do not send)

## Header block
<Name> | <email> | <phone> | <city> | <LinkedIn URL>

## Summary variants
### Family A
<Three lines, tuned to family A>
### Family B
<Three lines, tuned to family B>

## Experience
### <Company> | <Title> | <dates> | <location>
- [A,B] [k: keyword, keyword, keyword] [s:3] <bullet>
- [A]   [k: keyword, keyword]          [s:2] <bullet>

## Education
<verbatim from their CV>

## Certifications
<verbatim>

## Skills pool
<Flat comma-separated list. The tailoring step selects from this, so include
every tool, language and framework they have touched.>

## Tailoring rules
1. One page. Never two.
2. Extract the job description's keyword set before selecting anything.
3. Select the summary variant matching the role's family.
4. Select at most 14 bullets total, at most 5 per role.
5. Within a role, order by keyword overlap, then by strength.
6. Never include a bullet with zero keyword overlap, even a strong one.
7. Reuse the job description's exact terms where the bullet already means the
   same thing. Do not change what the bullet claims.
8. Trim the skills line to the 12 skills the job description names or implies.
9. Keep the header block, education and certifications verbatim.
10. Compute keyword coverage as matched keywords divided by job description
    keywords. Below 60%, do not send. Report it instead.
```

## 5. Check it back

Show them three of the rewritten bullets and ask:

> Do these sound like you, and is every number here true? I'd rather fix it now
> than have you find it in an interview.

Correct whatever they flag.

---

## Record it

Append to `me/setup-state.md`:

```markdown
## CV bank
- Doc: <URL>
- Bullets: <N> (<N> family A, <N> family B, <N> both)
- Strength 3 bullets: <N>
```

Mark step 3 done and step 4 next.

## Then say

> Bank's built: <N> bullets, <N> of them carrying hard numbers.
>
> Last question block, then I schedule everything. This one's about the
> questions application forms ask, so I never have to interrupt you mid-run.

Read `setup/04-answer-sheet.md`.
