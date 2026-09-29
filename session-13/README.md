# Session 13 — The folder is the agent

**Tuesday, September 29 · 4:00–5:15 PM · CFI · lab machine**
---

## Today's agenda

Session 10 you added instructions to a folder that already existed — your website. Today the folder is the whole job. There is no site, no code, no deliverable except the instructions you write.

You run customer service for the Xavier University bookstore. Every morning, customer emails land in an inbox. You are building the thing that reads each email, checks the order history, and drafts a reply you would be comfortable sending.

**You will not write a single reply.** You will write the instructions the agent follows, watch what it does with them, and then fix the instructions.

### Today's pace

Here is what we’ll do today.

| Steps | You should be through |
|---|---|
| 1 | folder open, `orders.csv` read |
| 2 | `CLAUDE.md` and agent instructions written |
| 3 | Part 3 — first run finished |
| 4 | Part 4 — replies scored |
| 5 | Part 5 — second run finished |

---

## Part 1 — Get the folder and read the data

**Download the folder.** Click this link and save the file to your **Desktop**:

[`session-13-data.zip`](https://github.com/jmathai/mgmt-342-build/raw/main/session-13/session-13-data.zip)

**Unzip it.** Double-click it. On Windows, right-click → **Extract All** → **Extract**.

You now have a folder called `bookstore-agent` on your Desktop.

**Open it in VS Code.** **File → Open Folder**, choose `Desktop → bookstore-agent`, click **Open**. Say yes when Claude Code asks whether you trust the folder.

### What the folder will look like

```
bookstore-agent/
  orders.csv     Five orders: who bought what, when, how they paid, how it arrived
  inbox/         Five customer emails, one per file, named by the sender's address
  outbox/        You create this. This is where the agent saves its draft replies.
  CLAUDE.md      You write this. It does not exist yet.
```

### The one rule

**Do not open the inbox.** You will only be looking at `CLAUDE.md` and `orders.csv` you can stare at as long as you like.

<details><summary>Why can't I just read the emails first?</summary>

Because then you would write five rules for five emails.

Real support teams write the return policy before they know who is going to return anything. The policy has to cover the customer who writes in tomorrow, and you have never met that person either. Writing rules against cases you can already see is the easiest mistake in this room to make and the hardest one to notice.

You get to open the inbox in Part 4. By then your policy is already written and it is too late to cheat.

</details>

### Study the CSV

Open `orders.csv`. Five rows. Actually read them — two minutes, with your eyes.

Look at the item types. Look at the dates and how old some of these orders are. Look at how people paid and how orders were delivered. **Read the notes column.**

Every one of those is a hint about what somebody is going to write in about.

---

## Part 2 — Write `CLAUDE.md`

Make a new file in this folder called `CLAUDE.md`. It covers four things.

Create the file starting with the following before adding your own content.

**1. Who you are.** Give the bookstore a name, a voice, and a sign-off. Decide how formal the replies sound. A reply signed *"Cheers, the Xavier crew"* is a different business than one signed *”Xavier University Bookstore, Customer Service."*

**2. The job.** Tell the agent what to do, in order. Something like: read each email in the inbox, find that customer's orders in `orders.csv` by their email address, work out which policy applies, write the reply to `outbox/` using the same file name as the email.
// TODO are 3 and 4 too descriptive or will students still have to try hard to think about what to include?
**3. Return and refund policy.** Be specific. Numbers, not adjectives.

- How many days does a customer have?
- Does it matter if the item was opened, used, or worn?
- Do textbooks, rentals, digital codes, apparel, and electronics get the same rules? They probably should not.
- Where does the money go — original payment method, store credit, cash?
- What happens when something arrives damaged?
- What happens when a customer damages something they rented?

**4. Escalation policy.** When should the agent *not* answer on its own and hand the email to a person instead?

- Over a certain dollar amount
- Anything your policy does not cover
- A customer who is angry, or threatening to complain to somebody
- A customer who says an employee already promised them something
- Anything touching financial aid or a student account

And say what escalating actually looks like. A holding reply to the customer? A note for staff? Both, in the same file?
//TODO I want to have them prompt Claude to generate the CLAUDE.md once they’ve done it themselves as an exercise.
<details><summary>I'm staring at a blank file</summary>

Write the four headings first — **Who we are**, **The job**, **Returns and refunds**, **When to escalate** — then fill them in. Plain sentences. This should be one page, not five.

If you want Claude to type it while you decide what goes in it, that is fine:

```
I'm writing a CLAUDE.md for this folder. Interview me about the bookstore's voice, our return policy, and when you should escalate to a human instead of replying. Ask me one question at a time. Do not suggest policy — I'll tell you what it is.
```

</details>

---

## Part 3 — Run it

Open Claude Code. Send exactly this:

```
Process the inbox.
```

That is the whole prompt. **Do not add anything in the chat.** Anything you want it to know belongs in `CLAUDE.md`, and if you say it in the chat you will never find out whether your file said it too.

Watch it work. It is reading your file, then reading emails you have not seen, then writing.

<details><summary>Predict before you open the outbox: how many of these would you actually send?</summary>

Write a number down. Five emails, how many clean replies?

Most people guess high. What usually comes back is a stack of replies that are perfectly polite, perfectly confident, and wrong in one specific way each — because the file was silent on that one thing and the agent filled the silence itself.

That gap between what you meant and what you wrote down is the whole session. Go find yours.

</details>

---

## Part 4 — Now open the inbox

Read each email next to its reply in `outbox/`. Five pairs. Score every one:

| Question | Yes / No |
|---|---|
| Did it find the right order? | |
| Did it apply the policy you actually wrote? | |
| Did it answer every question the customer asked? | |
| Did it escalate when it should have — and only then? | |
| Would you send this reply as written? | |

For every **No**, ask one question:

> **Was this the agent's mistake, or was my policy missing or unclear?**

It is the policy most of the time. Go look at your `CLAUDE.md` before you blame the machine.

<details><summary>Every reply came back fine</summary>

Two possibilities, and one is much more likely than the other.

Read your replies again against the actual policy in your file. Check the numbers. Check the item types. Check the one about renting. Somewhere in there the agent made a call your file never authorized, and it sounded so reasonable that you read straight past it.

A reply you would send is not the same as a reply your policy produced. Today you are grading the file, not the writing.

</details>

---

## Part 5 — Fix the file, not the reply

Do not edit anything in `outbox/`. Those are output. Output is disposable.

1. **Update `CLAUDE.md`** to close the gaps you found.
2. **Delete files from the outbox.**
3. Run it again:

```
Process the inbox.
```

4. Score it again.

### The rule for what you add

**No rule that only fixes one email.** *"If Marcus asks about his chemistry textbook, tell him yes"* is not a policy, it is a patch, and it does nothing for the next hundred customers.

Every line you add should be a line you would still want there if the inbox were completely different tomorrow. When you catch yourself writing a rule about a specific person, back up and ask what general thing that person ran into.

Keep going until every message gets a reply you would put your name on.

---

## Discussion

- What did your first version miss? Be specific about the gap.
- Where did the agent make a judgment call you did not expect? Was it a good one?
- Find a team who wrote a different reply to the same email. Why are they different? Which file is better, and what makes it better?
- What would you want a human to check before any of these actually went out?
- A completely new kind of email arrives tomorrow. Does your file handle it, or does it break?

---

## Done early?

- **Write an email that breaks it.** Make up a customer whose situation your policy does not cover, drop it in `inbox/`, and run it. What it does with a gap tells you more than what it does with a case you planned for.
- **Cut your file in half.** Most of these get long and repetitive. Find the rules that are saying the same thing twice.
- **Instruct the agent how to handle escalations** When an escalation happens, how can you automate the process to provide the agent sufficient information to continue?

---

## Before you leave the room

### What you turn in

Two things, in the Canvas comment box:

1. **Your `CLAUDE.md`** — the final version, pasted in as text.
2. **One reply from `outbox/`** — pick the one that came out well, and paste the email it was answering above it.

---

*MGMT 342 · Session 13 · Fall 2026 · Xavier University · Humphrey & Mathai*
