# Session 16 — Three analysts and a decision

**Tuesday, October 13 · 4:00–5:15 PM · CFI · lab machine**

---

## Where today goes

You have written two kinds of instruction so far. `CLAUDE.md` is always on. A skill sits quiet until the request matches its description. Today is the third kind: a **subagent**. It has its own instructions, its own context window, and it does not run until something hands it work.

That last part is the whole session. You are not writing instructions for an agent anymore. You are writing instructions for four of them, and deciding who gets told what.

Session 13 you ran the bookstore's support desk. Today you are the manager. The Xavier bookstore has to decide what to stock for spring, and the order goes to the publishers in December. You have one semester of sales, the spring course roster, the publishers' terms, and the returns log.

You will not do the analysis. You will hire three analysts, read what they send back, and then build the thing that turns three memos into one decision.

### Who is actually in the room

Session 13 was one agent in one window. Everything went in the same place — your `CLAUDE.md`, all five emails, the orders file, every reply it drafted. By the fifth email it was still carrying the first four.

Today there are five, and `CLAUDE.md`.

The **main agent** is the Claude Code session you type into. It has no file of its own — `CLAUDE.md` is just its always-on instructions, the same as in Session 13. It is the only one that can hand work to anybody.

A **subagent** *is* a file. `.claude/agents/demand.md` is the demand analyst. It only runs when the main agent sends it something.

So when you send a prompt, you are talking to the main agent, and it is the one deciding who gets the work. Your four briefs describe the staff. `CLAUDE.md` describes the manager.

### Context, and why there is more than one of it

Everything an agent knows at any moment sits in one place, called its **context**. Your instructions, the files it has opened, what it has said back to you — all of it, in one window.

Two things are true about that window and both of them matter today.

**It has a limit.** It is large, but it is finite, and quality falls off before you reach the edge of it. An agent holding four spreadsheets, three sets of instructions and half an hour of its own output is worse at the next question than it was at the first one. That is what Session 13 felt like by the fifth email.

**It is a boundary.** Each of your four agents gets its own, and they cannot see into each other's. The margin analyst cannot read what the demand analyst is thinking, and neither can read your chat. Nobody is overhearing anybody.

That boundary is the useful part. Four narrow windows beat one crowded one — each agent sees the files for its own question and nothing else, so it is working at the top of its ability rather than the bottom. It is also the only way four agents can cover a problem that would not fit in one window at all.

They are not completely sealed off, though. **They exchange memos.** An analyst writes what it found to `findings/`, and the planner reads those files later. That is a deliberately narrow channel: a file somebody chose to write, not a window somebody can see into. You decide what crosses it, which means you also decide what does not.

### What is actually in each window

A subagent starts empty. It gets its own brief and the shared `CLAUDE.md`, and nothing else — not a data file until it opens one itself.

| | What is in the window |
|---|---|
| main agent | `CLAUDE.md`, your prompt, and what comes back |
| `demand` | its brief, the shared file, and the two data files it opens |
| `margin` | its brief, the shared file, and the one data file it opens |
| `planner` | its brief, the shared file, and three memos |

That is the point, and it is not just tidiness. It is why you can tell an analyst which files it owns and have that mean something. It is why four agents can work a problem that does not fit in one window: the demand analyst reads all 403 rows, and those rows never enter *your* window, or the planner's. What comes back is the memo.

It cuts the other way too. **Your planner cannot check an analyst's work, because it never sees the data.** All it ever gets is the memo. If something is not in the memo, the planner does not know it — no matter how obvious it was to the analyst that found it.

---

## Part 1 — Get the folder and read what you are allowed to read

**Download the folder.** Click this link and save the file to your **Desktop**:

[`session-16-data.zip`](https://github.com/jmathai/mgmt-342-build/raw/main/session-16/session-16-data.zip)

**Unzip it.** Double-click it. On Windows, right-click → **Extract All** → **Extract**.

**Open it in VS Code.** **File → Open Folder**, choose `Desktop → bookstore-plan`, click **Open**. Trust the folder when Claude Code asks.

### What the folder will look like

```
bookstore-plan/
  data/
    orders-fall.csv         403 line items. Fall 2026, every sale.
    enrollment-spring.csv   Spring sections and projected seats, with fall seats next to them.
    supplier-prices.csv     What we pay, what we can charge, and the publishers' terms.
    returns-log.csv         What came back, why, and what it cost us.
    budget.md               What you have to spend. Read this one first.
  CLAUDE.md                 Mostly written for you. Two sections are yours.
  .claude/agents/
    demand.md               Four briefs, scaffolded. Frontmatter is there.
    margin.md               Everything in square brackets is yours to write.
    risk.md
    planner.md
  findings/                 Empty. Your analysts write their memos here.
```

**The four agent briefs are scaffolded and empty.** The headings and the frontmatter are there so you are not inventing a format at four o'clock. The content is the assignment. Anything in `[SQUARE BRACKETS]` is a blank — leave one in and you will get a memo about `[THE ONE QUESTION]`.

### The one rule

**Read `budget.md`, `orders-fall.csv` and `enrollment-spring.csv` as long as you like.

### Read what you can

Start with `data/budget.md`. It is six lines and it sets the whole problem.

`orders-fall.csv` is 403 rows. You are not going to read 403 rows. Read twenty and then look at the columns instead.

Notice there is a `format` column, and that it is not just new and used. Notice which courses show up over and over. Open `enrollment-spring.csv` next to it — ten courses, and it gives you both spring projected seats and fall seats.

**Those two numbers side by side are the whole demand question.** You sold some number of copies into some number of fall seats. Spring has a different number of seats. One of the ten courses changes a lot more than the others.

---

## Part 2 — Read `CLAUDE.md`, then staff it

Open `CLAUDE.md`. Most of it is written for you — what the store is, what is
being decided, the dates the money is committed, the budget, and the shape every
memo has to take. Read it. All five agents read it before they do anything.

Two sections are blank, and they are the ones about *your team*: **The agents**
and **The job**. Those belong here rather than in an agent's own file, because
only the main agent can delegate, and `CLAUDE.md` is the main agent's
instructions.

Paste this in over those two sections, then change what needs changing.

```markdown
## The agents

There are five of us and only one of us can delegate.

| | What it is | Can delegate? |
|---|---|---|
| **main agent** | the Claude Code session | **yes** |
| `demand` | `.claude/agents/demand.md` | no |
| `margin` | `.claude/agents/margin.md` | no |
| `risk` | `.claude/agents/risk.md` | no |
| `planner` | `.claude/agents/planner.md` | no |

The three analysts do not depend on each other and can run at the same time.
`planner` must not run until all three memos exist in `findings/`, because the
memos are the only thing it is allowed to read.

## The job

You are the main agent. You do not analyse anything and you do not decide
anything. You dispatch, you wait, and you report what landed.

- **"Run the analysts."** Dispatch `demand`, `margin` and `risk`. Wait for all
  three. Then tell me which memos were written and nothing else — do not
  summarise them, the memos are the output.
- **"Build the plan."** Dispatch `planner`. If any of the three memos is missing
  from `findings/`, stop and say which one rather than running it short.
```

**Read what you just pasted.** Two lines in it are doing real work and you should
know which.

The first is *"`planner` must not run until all three memos exist."* Nothing
enforces that. A planner dispatched early does not crash — it reads the two
memos that happen to be there and writes a confident plan missing a third of the
picture, and nothing in `PLAN.md` will say so.

The second is *"do not summarise them."* Left out, the main agent reads all three
memos to summarise them for you, and now everything the three analysts worked
separately is sitting in one window anyway.

**Notice what is still not in this file.** It does not say which data files each
agent reads. It does not say what any agent's question is. It does not say what
to do when two of them disagree. That is Part 3 and Part 5, and it is the whole
assignment.

<details><summary>Why is cost of goods not in here?</summary>

Because only one agent needs it.

Everything in this file, all five agents see. The minute a rule about cost lands
in the shared context, all of them start reasoning about margin whether you
wanted that or not — and then you have five agents doing one agent's job.

The test for anything you are tempted to add here: how many agents need it? If
the answer is one, it belongs in that one's brief.

</details>

## Part 3 — Write the three analyst briefs

Open `.claude/agents/`. Four files, already scaffolded. Three of them are analysts and you fill them in now. The planner waits until Part 5.

Each brief has the same five sections, and each one does a different job:

| Section | What it decides |
|---|---|
| the opening line | what this analyst is |
| **The data you own** | what it can see, and what it cannot |
| **The question you must answer** | the one thing it is for |
| **What your memo must contain** | whether the planner can use the result |
| **What you must not do** | where this analyst's authority stops |

### Who gets what

- **`demand`** — owns `orders-fall.csv` and `enrollment-spring.csv`. How many units will we sell in spring, in what format mix? The attach rate is the way in: units sold in fall over fall seats, applied to spring seats.
- **`margin`** — owns `supplier-prices.csv`, and `orders-fall.csv` for the format mix only. What does one copy earn us, in each format that title sells in? New, used and rental do not have the same economics and the file has the numbers for all three.
- **`risk`** — owns `supplier-prices.csv` and `returns-log.csv`. What could cost us money between the December order and the end of spring that nobody has priced in?

### Where briefs die

`CLAUDE.md` already tells every agent to read only the files its own brief names, so you do not have to write the prohibition three times. What you do have to write is the part that says what comes back.

Here is a `risk` brief that will run and will be useless:

```markdown
## The question you must answer

What could cost us money that nobody has priced in?

## What your memo must contain

Write findings/risk.md describing the risks you found.
```

Nothing there is wrong. It will come back with a page of considerations, no numbers, no dates, and nothing your planner can act on. **Do not copy it.** Use it to see what a brief looks like when it describes the job and forgets to describe the output.

The fix is not more words. It is deciding what a finding *is* before you ask for any. "Risk of overstock" is not a finding. A title, a dollar amount, a date it becomes irreversible, and what to do instead — that is a finding, and a brief that says so gets it.

<details><summary>How do I write a brief for a file I haven't read?</summary>

You describe the job, not the findings.

You know what a risk analyst does. It looks for money that could disappear and that nobody has counted. You do not know what it will find, and if you did you would not need it.

This is the honest version of the position every manager is in. It is why the brief has to say what to look for, how to report it, and what counts as important enough to flag. A brief that says "analyse the risk" gets you a page of considerations. A brief that says "flag anything that commits money we cannot get back, name the dollar amount, and name the date it becomes irreversible" gets you something you can act on.

Write the second kind.

</details>

<details><summary>Do not skip the description line</summary>

The `description:` in the frontmatter is the only part that decides whether a subagent gets picked at all. Session 10, Part 6 — same rule as a skill.

Leave it in brackets and you will sit through Part 4 wondering why nothing ran.

</details>

## Part 4 — Run the analysts

Open Claude Code. Send exactly this:

```
Run the analysts.
```

That is the whole prompt. **Nothing else in the chat.** If you say it in the chat you will never know whether your files said it too.

Watch what it does. Three subagents start, each reads only what you let it read, each writes one memo.

Then read all three memos in `findings/`. **Now** open `supplier-prices.csv` and `returns-log.csv` and check their work.

<details><summary>Predict before you read: will the three memos agree?</summary>

Write down what you think each one will say about ECON 201 — it is the store's biggest title.

They will not agree, and it is not because any of them is broken. Each one answered its own question correctly using the only data it had. The disagreement is real, it is in the business, and three competent analysts is exactly how you surface it.

That is the good news. The bad news is nobody has decided anything yet, and three correct memos pointing three directions is not a plan. That is Part 5.

</details>

<details><summary>Check what each analyst actually knew</summary>

Open `findings/demand.md` and look for any mention of cost, margin, or the publishers.

There is none, and not because it was obedient. It never had the file. Its window held its brief, the shared file, and two CSVs.

Now look at what that cost you. The demand analyst read 403 rows. Somewhere in there is the fact that ECON 201 sold in three different formats in wildly different proportions — and unless its memo says so in a form the planner can use, that fact has now been read by one agent and is known to nobody.

**The memo is the entire handoff.** Everything the analyst saw and did not write down is gone.

</details>

<details><summary>Only one memo showed up, or none did</summary>

Two likely causes.

**The delegation is not in `CLAUDE.md`.** If your file never says "use the demand, margin and risk subagents," the main agent has no reason to think there is anybody to hand work to, and it will do the job itself. Check Part 2, section 4.

**The description does not match.** The `description:` line is how a subagent gets picked, same as a skill — Session 10, Part 6. A vague one does not get chosen.

Fix the file, delete anything in `findings/`, and run it again.

</details>

---

## Part 5 — Write the planner

Three memos, one decision. Open `.claude/agents/planner.md`.

It owns `findings/` and nothing else. If it reads `data/`, it will redo the analysis and you will have four analysts and nobody deciding.

Its job is `PLAN.md`: for every title, what to order, in what format, how many, and why. Against a budget of **$26,000**.

**You will not fit.** Read `data/budget.md`, then look at what demand is projecting and what `supplier-prices.csv` says a copy costs. The money does not stretch to cover every seat in every course. That is not a mistake in the data — it is the job.

So the hard section is the one named **When your analysts disagree**. The budget guarantees they will: demand wants coverage, margin wants the format that earns, risk wants nothing you cannot undo, and there is not enough money for all three.

You can tell it risk wins on anything irreversible. You can tell it margin decides format and demand decides quantity. You can tell it to protect required courses first and let apparel go. You can tell it to escalate to you. All of those are real management choices and none of them is in the data.

What you cannot do is leave the section empty. **The planner resolves the disagreement either way** — the only question is whether it does it where you can see it.

Then run it:

```
Build the plan.
```

---

## Part 6 — Fix the brief, not the plan

Open `PLAN.md`. Score it.

| Question | Yes / No |
|---|---|
| Does every title have a quantity and a format? | |
| Can you trace every number back to a memo? | |
| Where two analysts disagreed, did it choose — and say why? | |
| Did it stay out of the one decision it does not have the information to make? | |
| Would you sign this and send it to the publishers? | |

For every **No**, ask one question:

> **Was this the planner's mistake, or was my brief missing or unclear?**

Do not edit `PLAN.md`. It is output. Fix the brief, delete `PLAN.md`, run it again.

<details><summary>The plan looks fine to me</summary>

Check ECON 201 specifically, and check it against all three memos rather than against the plan's own reasoning.

It is the biggest title in the store. Demand wants a lot of it. Margin has a clear view about which format earns. Risk found something in the publisher's terms with a date on it. If `PLAN.md` recommends a quantity without mentioning what risk found, your planner resolved a conflict silently — and a conflict resolved silently is a conflict nobody reviewed.

Then check CHEM 115. There is no good answer there. Find out whether your planner noticed that or just picked a number.

</details>

### The rule for what you add

**No rule that only fixes one title.** *"For ECON 201, order used copies"* is not a policy, it is you doing the analysis and having the agent type it.

Write the general version. What was true about ECON 201 that made used the right call? Write *that*, and it will still be right in the spring when the title has changed.

---

## Discussion

- Which analyst found the thing that changed the decision? Would your brief have found it if you had written it two sentences shorter?
- Where did two of your analysts do the same work twice? What did that cost you?
- The reading says context hoarding is the new job security. You built the hoarding on purpose today by telling each analyst which files it owns. Was that right? What broke because of it?
- One agent reading all four files would have had the whole picture and no handoff problem at all. Make the argument for doing it that way. Then say what you would lose.
- Find a team whose plan recommends a different quantity for ECON 201. Both of you read the same data. Why are the numbers different — the data, the briefs, or the planner?
- Your planner made a judgment call you did not authorize. Find it. Would you have made the same one?

---

## Done early?

- **Let the analysts talk.** Give margin read access to `findings/demand.md`. Run it again. The memo gets better and something else gets worse — find out what.
- **Break the planner on purpose.** Write a fourth analyst whose memo flatly contradicts one of the three, drop it in, and see whether your conflict rule holds.
- **Cost it.** Ask Claude Code how many tokens that run took, then ask what the cheapest version of the same plan would look like. You have three analysts because you hired three. Were all three worth it?

---

## Before you leave the room

### What you turn in — due Thursday Oct 15 at the start of class

Commit these to your repository under `module3-artifacts/rep1-stocking-plan/` and paste the link in Canvas:

1. **`PLAN.md`** — the final version.
2. **The three memos** from `findings/`.
3. **Your four agent files** and your `CLAUDE.md`.

The plan is the artifact. The briefs are the work. You are graded on both, and on being able to say why your planner decided what it decided.

---

*MGMT 342 · Session 16 · Fall 2026 · Xavier University · Humphrey & Mathai*
