# Step 4: Answer sheet

**Goal:** pre-answer every question an application form asks, so an apply run
fills a form without stopping, and stops only on a real judgement call.

**Output:** `me/answer-sheet.md`, plus a copy in Drive at
`Job Search <year>/Reference/`.

**Time:** 7 minutes.

---

## Say this first

> Application forms ask the same forty questions. If I have your answers up
> front, a run fills a form in one pass and only interrupts you when something
> genuinely needs your judgement. Some of these you've already answered, so
> this is shorter than it looks.

---

## Ask in four blocks

Pull anything already in `me/profile.md` and confirm it rather than re-asking.

### Block 1: Identity and logistics

> - Phone number with country code
> - LinkedIn URL, and portfolio or GitHub if you have one
> - Current address, or at least city and postcode
> - Are you legally authorised to work in <each target location>?
> - Do you need visa sponsorship now or in future?
> - Notice period (confirm)
> - Earliest start date

### Block 2: Money

> - Current total compensation, if you're willing to state it
> - Expected total compensation, as a single number
> - Your floor (confirm from profile)
>
> When a form asks for a number and won't take a range, I'll use your expected
> figure. When it asks for a range, I'll use expected to expected plus 15%.
> Say so if you'd rather I did something else.

### Block 3: The stock free-text answers

These four appear constantly. Draft each one yourself from `me/profile.md` and
the CV bank, show it, and let them edit. Do not ask them to write from scratch.

> **Why do you want this role?**
> A 60-word template with a `<company specific>` slot the task fills per role.
>
> **Why are you leaving your current role?**
> 30 words. Forward-looking. Nothing negative about the current employer.
>
> **What's your greatest strength, with an example?**
> 50 words, built on a strength-3 bullet from the bank.
>
> **Tell us about yourself.**
> 80 words. Their background one-liner, expanded.

### Block 4: Voluntary disclosure

> Forms often ask about gender, ethnicity, disability, and veteran status.
> These are voluntary and I won't guess. Tell me what you want me to select,
> or say "prefer not to say" and I'll use that everywhere.

Record whatever they say and use it verbatim. Never infer any of these.

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
A run must leave the field blank, stop, and report when:
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

Copy it to Drive under `Job Search <year>/Reference/`. The browser-based tasks
read the Drive copy, since they cannot see this repo.

---

## Then say

> Done. Everything's in place. Last step is scheduling, which takes two
> minutes, and then this runs on its own.

Update `me/setup-state.md`, mark step 4 done and step 5 next, then read
`setup/05-schedule.md`.
