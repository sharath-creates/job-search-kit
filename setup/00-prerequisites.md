# Step 0: Prerequisites

**Goal:** confirm what this kit needs, and get everything missing fixed in one
pass before any other step runs.

**Output:** `me/setup-state.md`

**Time:** 2 minutes.

---

## Say this first

> Before we build anything, I'm checking that I can reach everything I need.
> Give me a moment.

---

## Run all five checks, then report once

Run every check before you say anything else. A person fixing connectors makes
one trip to Claude's settings, so hand them the whole list in one message
rather than one failure at a time.

### 1. Google Drive, Sheets and Gmail

Try listing recent Drive files. Try listing the last few Gmail messages. Both
must work. There is no workaround: this kit stores its pipeline in a Google
Sheet, and every task reads from it.

### 2. A web search connector

Check whether a search tool is available. Firecrawl is the tuned default, and
its free tier gives 1,000 credits a month, of which this kit uses about 450 on
default settings. Any other search tool works: note its name, and step 5
adapts the query syntax. Read `reference/search-queries.md` when you reach
step 5, not now.

### 3. Scheduled tasks

Confirm you can create scheduled tasks. Do not create one yet. If you cannot,
setup still runs, and step 5 produces six prompt files instead of six tasks.

### 4. Their CV

Look in `me/` for a CV: any file other than `README.md` and
`EXAMPLE-profile.md`, in PDF, Word, plain text or Markdown format.

- **Exactly one:** use it. Do not ask.
- **Several:** ask which one is current.
- **None:** ask for it in the report below.

If the file's format defeats you, ask them to save it as a PDF and put that in
`me/` instead. If they paste or attach it in the chat, write its text to
`me/cv.md`, so a later step or a resumed session can read it without asking
again.

### 5. A browser connector

Check whether Claude in Chrome, or another connector that drives the
person's own Chrome, is available. A browser built into the Claude app does
not count: it is not logged in to their LinkedIn or their job site accounts.
Record yes or no. Do not ask about it now. Step 1 offers the two browser tasks
once the person knows what they do.

---

## Report

**Everything passed.** Say one line, then go straight into step 1 in the same
message:

> Everything's connected: Google, <search tool>, scheduled tasks. I found your
> CV (<file name>).

**Something is missing.** List every fix in one message and wait:

> Before we start, <N> things need fixing. The connectors are in Claude's
> settings under Connectors.
>
> 1. <Connect Google Drive and Gmail.>
> 2. <Connect Firecrawl. Its free tier covers this kit.>
> 3. <Put your CV in the `me` folder inside this kit, or attach it here. Any
>    format works.>
>
> Tell me when that's done and I'll re-check.

Once they say it's done, re-run only the checks that failed.

**Scheduled tasks unavailable.** Add this to the report and record the answer:

> Scheduled tasks aren't available on your plan or in this interface. We can
> still do the whole setup, and I'll give you six prompts you run by hand or
> schedule elsewhere. Want to continue?

---

## Write the state file

Create `me/setup-state.md`:

```markdown
# Setup state

Started: <today's date>

| Step | Status |
|------|--------|
| 0 Prerequisites | done |
| 1 Discovery | next |
| 2 Workspace | pending |
| 3 CV bank | pending |
| 4 Answer sheet | pending |
| 5 Scheduling | pending |

## Environment
- Google Drive/Sheets/Gmail: <yes/no>
- Search tool: <name>
- Scheduled tasks: <available/unavailable>
- CV: <path in me/, or "in Drive: <name>">
- Browser connector: <yes/no>
```

Then read `setup/01-discovery.md` and open with its first block.
