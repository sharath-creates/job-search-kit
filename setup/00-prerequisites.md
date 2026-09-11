# Step 0: Prerequisites

**Goal:** confirm the five things this kit needs, and fix whatever is missing
before any other step runs.

**Output:** `me/setup-state.md`

**Time:** 5 minutes.

---

## Say this first

> Before we build anything, I need to check five things. This takes a couple of
> minutes and saves an hour of confusing failures later. I'll check what I can
> myself and ask you about the rest.

---

## The five checks

Run them in order. Stop at the first failure, give the fix, and wait.

### 1. Google Drive, Sheets and Gmail

Try listing recent Drive files. Try listing the last few Gmail messages.

- **Both work:** say "Drive and Gmail are connected."
- **Either fails:** stop. Say:
  > I can't reach your Google account yet. Open Claude's settings, find
  > Connectors, and connect Google Drive and Gmail. Tell me when that's done
  > and I'll re-check.

Do not offer a workaround. This kit stores its pipeline in a Google Sheet, and
every task reads from it.

### 2. A web search connector

Check whether a search tool is available. Firecrawl is the tuned default.

- **Firecrawl available:** say so, and note that the free tier gives 1,000
  credits a month, of which this kit uses about 450 on default settings.
- **A different search tool available:** say which one you found, and note that
  step 5 will adapt the query syntax. Read `reference/search-queries.md` when
  you reach step 5, not now.
- **Nothing available:** stop. Say:
  > I have no web search tool, so I can't find job postings. Firecrawl has a
  > free tier that covers this. Connect it in Claude's settings under
  > Connectors, then tell me.

### 3. Scheduled tasks

Confirm you can create scheduled tasks. Do not create one yet.

- **Unavailable:** say:
  > Scheduled tasks aren't available on your plan or in this interface. We can
  > still do the whole setup, and I'll give you six prompts you run by hand or
  > schedule elsewhere. Want to continue?

Record the answer. If they continue, step 5 produces files instead of tasks.

### 4. Their CV

Ask:
> Do you have your current CV handy? Any format works. Attach it, or tell me
> it's already in your Drive and I'll find it.

You need it in step 3, not now. Record whether it exists.

### 5. Chrome (optional)

Ask:
> Two of the six tasks fill in application forms in your browser. They need
> Chrome open with the Claude extension installed, and they never submit
> anything without you. The other four work without it. Do you want those two?

If they say no, step 5 schedules four tasks instead of six. Record the answer.

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
- CV supplied: <yes/no/in Drive>
- Browser tasks wanted: <yes/no>
```

---

## Then say

> All clear. Next is the part that decides everything else: what you're
> actually going after. It's the longest step, about fifteen minutes, and it's
> mostly me asking and you answering. Ready?

Wait for yes, then read `setup/01-discovery.md`.
