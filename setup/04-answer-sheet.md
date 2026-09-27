# Step 4: Answer sheet

**Goal:** pre-answer every question an application form asks, so an apply run
fills a form without stopping, and stops only on a real judgement call.

**Output:** `me/answer-sheet.md`, plus a copy in Drive at
`Job Search <year>/Reference/`.

**Time:** 3 minutes.

---

## Draft first, then show it once

Application forms ask the same forty questions. Most of the answers already sit
in `me/profile.md` and the CV. Draft the whole sheet yourself, then show it in
one message and let the person correct it. Do not ask field by field.

Fill from the profile and the CV:

- **Contact:** phone, LinkedIn, portfolio or GitHub, from the CV. Use the
  city as the address unless the CV carries a full one.
- **Work authorisation and sponsorship:** from the profile.
- **Notice period** from the profile, and **earliest start** as "<notice
  period> after an offer". A run that meets a date field adds the notice
  period to that day's date.
- **Compensation:** floor, expected and current, from the profile. When a
  form wants a range, use expected to expected plus 15%.
- **Common short answers:** years of experience in their core skills, highest
  qualification, certifications, from the CV.

Draft the four stock free-text answers from the profile and the CV bank:

- **Why this role:** 60 words, with a `<company specific>` slot the task
  fills per role.
- **Why leaving:** 30 words. Forward-looking. Nothing negative about the
  current employer.
- **Greatest strength:** 50 words, built on a strength-3 bullet from the bank.
- **About yourself:** 80 words. Their background one-liner, expanded.

Voluntary disclosure (gender, ethnicity, disability, veteran status) defaults
to "prefer not to say". Never infer any of these.

## Show it

> Application forms ask the same forty questions, so I've drafted your answers
> from what you've told me. Read them once and fix anything that's wrong.
>
> **Contact:** <phone>, <LinkedIn>, <portfolio>. <Name any that are missing.>
> **Work:** notice <period>, so you can start <period> after an offer.
> <Authorisation summary.>
> **Money:** expected <figure>. If a form wants a range, <figure> to
> <figure + 15%>. Never below <floor>.
>
> **Why this role** (I fill in the company part for each job):
> <draft>
>
> **Why you're leaving:** <draft>
>
> **Greatest strength:** <draft>
>
> **About you:** <draft>
>
> **Voluntary questions** (gender, ethnicity, disability, veteran status): I'll
> answer "prefer not to say" on all of them unless you tell me otherwise.

Apply their corrections. For voluntary disclosure, use their words verbatim.
If they supplied a missing contact detail, add it.

---

## Write the sheet

Create `me/answer-sheet.md`:

```markdown
# Answer sheet
Version 1. Updated <date>.

## Identity
| Field | Answer |
|---|---|
| Full name | |
| Email | |
| Phone | |
| Address | |
| LinkedIn | |
| Portfolio | |

## Work authorisation
| Location | Authorised | Sponsorship needed |
|---|---|---|

## Logistics
| Field | Answer |
|---|---|
| Notice period | |
| Earliest start | |
| Willing to relocate | |
| Interview availability | |

## Compensation
| Field | Answer |
|---|---|
| Current | |
| Expected | |
| Floor (never go below) | |
| If a range is required | expected to expected +15% |

## Stock answers
### Why this role (60w, <company specific> slot)
### Why leaving (30w)
### Greatest strength (50w)
### About yourself (80w)

## Common short answers
| Question pattern | Answer |
|---|---|
| Years of experience in <their core skill> | |
| Years of experience in <family A core skill> | |
| Years of experience in <family B core skill> | |
| Highest qualification | |
| Do you have a <certification they hold> | Yes |
| Are you currently employed | |
| How did you hear about us | Company website |

## Voluntary disclosure
| Field | Answer |
|---|---|
| Gender | |
| Ethnicity | |
| Disability | |
| Veteran status | |

## Stop and ask
A run must not submit, and must write the question into the sheet for the
person to answer, when:
- the question is not covered above
- free text over 300 characters is required and no tailored cover note covers it
- relocation outside <their accepted locations> is asked
- a compensation figure below the floor would be needed
- a video interview or timed assessment is required to proceed
- payment, a government ID number, or an account password is requested

## Never a stop
- Relocation questions about a city they already live in. Answer "I am based
  in <city>".
- Experience questions asking for a number at or below what they have. Answer
  with their actual figure.
```

Copy it to Drive under `Job Search <year>/Reference/`. The scheduled tasks
read the Drive copy, since they cannot see this repo. From now on the Drive
copy is the live one: when the person answers a new form question in the
sheet, the apply run adds it to the Drive copy's "Common short answers" table,
so no later run stops on the same question.

---

## Then say

> Done. Everything's in place. Last step is the schedule, and then this runs
> on its own.

Update `me/setup-state.md`, mark step 4 done and step 5 next, then read
`setup/05-schedule.md` and show its schedule grid in the same message.
