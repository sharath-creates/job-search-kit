# Design notes

Why the kit is shaped the way it is. Read this before changing anything
structural.

---

## The system optimises for reply rate, not application count

Application count is easy to raise and easy to measure, which is why most
job search automation raises it. Reply rate is what determines whether the
search ends.

Every cap in the kit costs applications and buys reply rate:

| Constraint | Applications lost | Reply rate bought |
|---|---|---|
| Two families, not four | Large | Each family accumulates a readable sample |
| Score 70 threshold | Large | Applications go where the fit is real |
| 60% keyword coverage gate | Moderate | The applicant tracking system ranks the CV |
| 14-day company cooldown | Small | The company does not file the applicant as noise |
| Per-day cap | Moderate | Every application gets a tailored CV |

An empty run is a correct result. The task prompts say so in those words,
because an agent left to its own judgement will lower a threshold to produce
output, and the person reading the report will read zero as failure.

## Setup is an interview, not a configuration file

The audience is someone who has never written a prompt. A config file they fill
in themselves fails twice: they do not know what good values look like, and
nothing pushes back when they list four role families.

The interview pushes back exactly once, on the question that matters, and
accepts the answer if they insist. That is the right amount of friction for a
tool nobody is paid to use.

## Task prompts carry data, they do not fetch it

The alternative design has each scheduled run read `me/profile.md`. It is
cleaner, and it costs roughly twenty-five times more per run. `reference/token-budget.md`
has the arithmetic.

The cost of the chosen design is that changing the profile means updating six
task prompts. `setup/06-tuning.md` handles that, and the tuning command states
which tasks it touched.

## State lives outside the repo

The pipeline is in a Google Sheet rather than a file in the repo, for three
reasons: the person can open it on a phone and sort it, the browser-driven
tasks can reach it while they cannot reach the repo, and the repo stays
shareable with nothing personal in it.

`me/` is gitignored so the fork a person publishes carries no salary floor and
no email address.

## Six tasks, five of which never touch a submit button

Only the apply run submits, and it stops on six named conditions. The LinkedIn
task never submits at all, because LinkedIn's user agreement prohibits automated
interaction and their detection restricts accounts that do it. The boundary is
stated in the template itself rather than left to the agent's discretion, so a
person editing the prompt sees why it is there.

## What the kit deliberately does not do

- **Write cover letters from scratch per role.** It fills a slot in an answer
  the person approved. Generated prose that the person has not read is a
  liability in an interview.
- **Invent numbers for the CV.** The bank carries only what they confirmed.
- **Negotiate, or reply to a recruiter unprompted.** Inbox watch drafts and
  stops. The first human conversation should start with a human.
- **Score culture fit, or infer anything about the person beyond what they
  stated.** The rubric uses six observable properties of a posting.

## Known weaknesses

- **The watchlist needs maintenance.** Board URLs change and the broken-board
  rule only stops the bleeding.
- **Keyword coverage is a proxy.** It correlates with applicant tracking system
  ranking without being it, and a posting written in unusual language scores
  badly for the wrong reason.
- **The conversion check needs volume.** Below twenty applications per family
  its recommendations are noise, and the weekly review should say so rather
  than recommending a retirement on a sample of six.
- **Nothing here helps with referrals**, which out-convert every source in this
  system by a wide margin. The kit finds roles. A person still has to find the
  human inside the company.
