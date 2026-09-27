# Step 1: Discovery

**Goal:** learn enough to score a job posting the way the person would score it
themselves, and to fill in an application form without asking them again.

**Output:** `me/profile.md`

**Time:** 10 minutes.

---

## How to run this

Read the CV named in `me/setup-state.md` first. It answers about a third of
this step: name, email, current role and start date, years of experience,
city, the industries they have worked in, and the titles they have held. Never
ask for something the CV already says. State it and let them correct it.

Then run six blocks, one per message. Each block opens with what you already
know or propose, and asks only for what is missing. Wait for the answer,
acknowledge it in a sentence, then move to the next block.

Never ask all six at once. Someone who has never used an AI tool reads a
wall of questions and closes the tab.

When an answer is vague, ask one follow-up and accept whatever comes back the
second time. Finishing matters more than precision here.

Write each block's answers into `me/profile.md` as you go, using the template
at the end of this file. If the person stops halfway, a resumed session reads
the partial profile and picks up at the first block with no answers.

---

## Block 1: What the CV says

> I've read your CV. Here's what I took from it:
>
> - <Name>, <email>
> - <Title> at <company>, since <month year>
> - About <N> years of full-time experience
> - Based in <city>
>
> Anything wrong there? One more thing: is there a date this has to be done
> by? A last working day, a visa deadline, a lease ending. If not, say "no
> deadline".

If the CV lacks any of those four lines, ask for the missing ones in this same
message.

A deadline changes the system's behaviour. With one, every report leads with
days remaining and the sourcing tasks weight recency harder. Without one, the
weekly review leads with conversion rate instead.

## Block 2: What you're going after

This is the block that matters. Get it right and everything downstream works.

Before you ask, group the titles in their CV into families using
`reference/role-families.md`, and pick the two that fit best. That is usually
the family they have the most recent evidence for, plus the one they are
growing into.

> From your CV, I'd aim at two kinds of role:
>
> - **<Family A>:** <titles>
> - **<Family B>:** <titles>
>
> Is that what you're going for? Add or swap any titles you've been
> considering.

If their answer spans more than two families, say:

> Those fall into <N> families: <list them>.
>
> I want you to drop this to two. Each family needs its own CV angle and its
> own set of searches. Chasing four means you find out in three months that
> none of them worked, and you won't know which one to push on. Two means you
> get a readable answer in three weeks.
>
> Which two?

If they push back and insist on three, accept it once, record it, and add a
line to the profile saying the weekly review should retire the weakest family
after twenty applications with no reply.

Then propose calibration companies in the same message as your
acknowledgement:

> I'll calibrate what "good" looks like against a few companies you'd be
> pleased to join. Based on where you've worked, I'd use <two or three for A>
> and <two or three for B>. Swap any you like, or say "fine".

## Block 3: Where, and on what terms

Propose from the CV's city and country:

> Here's what I'll assume about location. Correct anything that's wrong:
>
> - Locations: <city> first, then remote within <country>
> - Hybrid and fully remote are both fine
> - No relocation
> - No roles that need <US or European> working hours from <city>
> - You're allowed to work in <country> and don't need visa sponsorship

Each correction replaces a default. If they add a location in another country,
ask whether they can work there and whether they would need sponsorship.

## Block 4: The floor

Never propose these numbers. Ask for them.

> Now money and timing. Application forms ask for these, so I need your
> figures:
>
> 1. The lowest total compensation (CTC) you'd accept. One number. I'll never
>    let a task apply below it, and I'll never put a figure on a form that
>    undercuts you.
> 2. Your expected CTC, for forms that want a single number.
> 3. Your current CTC. Most forms ask for it, LinkedIn's included. If you'd
>    rather not state it, say "skip" and I'll leave that field for you.
> 4. Your notice period. I'll give your earliest joining date as that long
>    after an offer.
>
> For interview calls I'll offer weekdays before 10:00 and after 18:30. Tell me
> if other windows suit you better.

## Block 5: The auto-fails

Propose the defaults, built from what they have told you:

> I'll skip any posting that:
>
> - was posted more than 30 days ago
> - asks for more than <their years + 4> years, or caps below <their years - 1>
> - <needs the working hours they excluded, if any>
> - <needs relocation somewhere they refused, if any>
>
> What else makes you close a job posting immediately? People mention a degree
> they don't have, contract-only roles, or an industry they won't work in. Or
> say "that's it".

## Block 6: How hard to push

> Last question. How hard should this push? I'd suggest **standard**: about 8
> applications a day on weekdays. **Light** is about 4 a day and the cheapest
> to run. **Heavy** is about 12 a day, and only worth it with a deadline and
> time to review what I prepare.

If step 0 found a browser connector, add this to the same message:

> Two of the six tasks fill in application forms in Chrome on this computer,
> so it needs to stay on during the day. Want them? If yes, pick how
> applications on company sites go out:
>
> - **You approve (recommended).** Each morning's email lists the roles I've
>   prepared, with a tailored CV for each. Tick the ones you want in the
>   sheet, from your phone if you like, and the next run sends them.
> - **Automatic.** Runs send anything that clears the bar, up to your daily
>   cap. You can still stop any role by setting its Status to Withdrawn.
>
> Either way, a form question your answer sheet doesn't cover stops that
> application and asks you in the sheet.
>
> On LinkedIn, I fill in every Easy Apply form that scores 70 or above, twice
> a day, and save the job. You open Saved jobs on LinkedIn, check the answers,
> and click Submit. I can click Submit for you instead, but LinkedIn's user
> agreement bans automated applying, and accounts get restricted for it. Say
> "LinkedIn automatic" only if you accept that risk.

If step 0 found no browser connector, say instead:

> Two optional tasks fill in application forms in Chrome. I can't reach a
> browser from here, so I'll leave them off. You can add them later by saying
> "turn on apply runs".

Record the level, whether they want the browser tasks, the submission mode,
and the LinkedIn mode. LinkedIn stays "you click" unless they said "LinkedIn
automatic" in those words or close to them. Step 5 turns all of this into
schedules and caps.

---

## Write the profile

Create `me/profile.md`. Keep it under 60 lines. Step 5 copies its fields into
every scheduled task, so length here becomes token cost on every run.

```markdown
# Profile

## Identity
- Name:
- Email:
- Current role: <title> at <company>, since <date>
- Experience: <N> years
- Location: <city>
- Deadline: <date, or "none">

## Background one-liner
<Two sentences a scheduled task can paste into a cover note. Written in
their voice, drawn from their CV and what they told you. This is the single
most reused string in the system, so make it good.>

## Target families
### Family A: <name>
Titles: <comma separated>
Calibration companies: <list>

### Family B: <name>
Titles: <comma separated>
Calibration companies: <list>

## Location and terms
- Locations, ranked:
- Remote: <fully / hybrid / on-site>
- Relocation: <yes to X, never to Y>
- Working hours excluded:
- Work authorisation: <per location: allowed yes/no, sponsorship yes/no>

## Floor
- Minimum total compensation:
- Expected compensation:
- Current compensation: <figure, or "not stated">
- Notice period:
- Interview availability:

## Auto-fail
- <one per line>

## Intensity
- Level: <light / standard / heavy>
- Applications per run:
- Applications per day:
- Browser tasks: <yes / no>
- Submission: <you approve / automatic / not applicable>
- LinkedIn: <you click / automatic / not applicable>
```

---

## Then say

> That's the hard part done. Here's what I've got:
>
> <Read back, in four lines: the two families, the locations, the floor, the
> intensity level with the submission mode.>
>
> Anything wrong? If not, I'll build your tracking sheet and your CV bank
> next. You don't need to do anything for that part.

Fix whatever they correct, rewrite the profile, update `me/setup-state.md` to
mark step 1 done and step 2 next, then read `setup/02-workspace.md`.
