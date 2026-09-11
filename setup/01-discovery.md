# Step 1: Discovery

**Goal:** learn enough to score a job posting the way the person would score it
themselves, and to fill in an application form without asking them again.

**Output:** `me/profile.md`

**Time:** 15 minutes.

---

## How to run this

Ask in blocks. One block per message. Wait for the answer, acknowledge it in a
sentence, then move to the next block. Seven blocks total.

Never ask all seven at once. Someone who has never used an AI tool reads a
wall of questions and closes the tab.

When an answer is vague, ask one follow-up and accept whatever comes back the
second time. Precision here matters less than finishing.

---

## Block 1: Who you are

> Let's start with the basics.
>
> 1. Your full name, and the email you apply from.
> 2. Your current or most recent job title, company, and when you started.
> 3. Roughly how many years of full-time experience do you have?
> 4. Where do you live? City is enough.

## Block 2: The clock

> 5. Is there a date this needs to be done by? A last working day, a visa
>    deadline, a lease ending, anything. If there's no date, say "no deadline"
>    and I'll pace it differently.

A deadline changes the system's behaviour. With one, every report leads with
days remaining and the sourcing tasks weight recency harder. Without one, the
weekly review leads with conversion rate instead.

## Block 3: What you're going after

This is the block that matters. Get it right and everything downstream works.

> 6. What job titles are you going for? List every one you've been considering.

Take their list. Group it into families using `reference/role-families.md` if
you need help, then say:

> I've grouped those into <N> families: <list them>.
>
> I want you to drop this to two. Here's why. Each family needs its own CV
> angle and its own set of searches. Chasing four means you find out in three
> months that none of them worked, and you won't know which one to double on.
> Two means you get a readable answer in three weeks.
>
> Which two?

If they push back and insist on three, accept it once, record it, and add a
line to the profile saying the weekly review should retire the weakest family
after twenty applications with no reply.

Then:

> 7. For each family, name two or three companies you'd be pleased to work for.
>    I'll use them to calibrate what "good" looks like.

## Block 4: Where, and on what terms

> 8. Which locations work? Rank them if more than one.
> 9. Is remote acceptable? Fully remote, hybrid, or on-site only?
> 10. Would you relocate? If yes, where to, and where absolutely not?
> 11. Are there working hours you won't take? Some roles ask for US or European
>     hours from another timezone.

## Block 5: The floor

> 12. What's the lowest total compensation you'd accept? A number, not a range.
>     I'll never let a task apply to something below it, and I'll never put a
>     figure on a form that undercuts you.
> 13. What's your notice period?
> 14. When can you take interview calls? Give me actual windows, like
>     "weekdays before 10am and after 7pm".

## Block 6: The auto-fails

> 15. What makes you close a job posting immediately? Examples people give:
>     a degree requirement you don't meet, a specific company or industry,
>     seniority far above or below you, contract-only, or an unpaid trial.

Add two defaults yourself unless they object:

- Postings older than 30 days.
- Postings requiring more than <their years + 4> or capping below
  <their years - 1>.

## Block 7: How hard to push

> 16. How aggressive do you want this? Three levels:
>
>     **Light.** About 4 applications a day, one sourcing sweep, cheapest to
>     run. Good if you're employed and not in a hurry.
>
>     **Standard.** About 8 a day, two sourcing passes, apply runs every three
>     hours on weekdays. This is what most people want.
>
>     **Heavy.** About 12 a day. Only worth it if you have a deadline and time
>     to review what I prepare.

Record the level. Step 5 turns it into cron schedules and caps.

---

## Write the profile

Create `me/profile.md`. Keep it under 60 lines. Every scheduled task gets its
content pasted into it, so length here becomes token cost on every run.

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
their voice, drawn from what they told you. This is the single most reused
string in the system, so make it good.>

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

## Floor
- Minimum total compensation:
- Notice period:
- Interview availability:

## Auto-fail
- <one per line>

## Intensity
- Level: <light / standard / heavy>
- Applications per run:
- Applications per day:
```

---

## Then say

> That's the hard part done. Here's what I've got:
>
> <Read back, in four lines: the two families, the locations, the floor, the
> intensity level.>
>
> Anything wrong? If not, next I'll build your tracking sheet. That one's
> quick and you don't have to do anything.

Fix whatever they correct, rewrite the profile, update `me/setup-state.md` to
mark step 1 done and step 2 next, then read `setup/02-workspace.md`.
