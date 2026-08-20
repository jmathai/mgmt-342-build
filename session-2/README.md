# Session 2 — Prompt engineering

**Thursday, August 20 · 4:00–5:15 PM · CFI · your own laptop**

This page is the session. Work down it with us. Every prompt below sits in a grey box with a **copy icon** in its top-right corner — click the icon, then paste into Copilot. Do not retype anything.

**Two tools today.** Copilot, where you spend most of the session, and GitHub, which you are reading this on right now.

**One rule before we start:** some prompts contain `[SQUARE BRACKETS]`. Replace those with things that are actually true about you before you send. If you send it with the brackets still in, the model will do exactly what you asked and write about `[YOUR MAJOR]`.

**Where you end up:** by 5:15 you will have written the real text for your own website's About page — the first piece of your Module 1 Build.

---

## Where this page lives

Start with the tool you are already using without having been told you were.

**You are reading this on GitHub.** Not Canvas, not a course website, not a PDF someone emailed you. This page is a file, sitting in a folder, on GitHub — and you are looking at it in a browser like any other web page. No account, no install, no login.
**A repository is a collection of files.** That is the entire idea. People say "repo." It keeps a set of files together, backs them up, and lets you share them — think OneDrive for now. A repo can sit on your laptop and never go anywhere; this one is on GitHub because we wanted you to be able to read it. The comparison is imperfect and we will break it in September, but it will hold today.

**Look up.** Above this page is a path — the repository name, then the folder, then the file you are reading. Click the repository name at the far left. That takes you to everything in it.

**Look at what is there. How much of it is code?**

<details><summary>Answer</summary>

None of it. Not one line.

You are looking at folders — `session-2`, `session-4` — and a couple of files at the top. `README.md` is the one that displays on its own when you open a folder, which is why this page appeared without you clicking a file name. GitHub is where the world keeps its code, so nearly everyone assumes a repository *is* code. It is not. **A repository holds files. What kind is your business.**

What you are actually reading is **markdown**: plain text with a few marks in it. `#` makes a heading, `**` makes bold, `-` makes a bullet. That is close to the whole language, and you can learn it in about five minutes.

**Markdown is worth knowing because it is what models read and write best**, and there are three reasons for that:

- **It is plain text, so nothing has to be converted.** A Word file or a PDF has to be pulled apart before a model can read it, and the structure usually gets mangled on the way through. Markdown arrives intact.
- **The marks carry the structure.** The model sees the same headings and lists you see, so it can tell a heading from a sentence — which means it can tell what is a rule and what is an example.
- **Models were trained on mountains of it.** Most documentation and most of GitHub is markdown. That is why answers come back with headings and bullets you never asked for. It is the format they are most fluent in.

Which is why the instructions people write *for* AI are markdown files. Open `CLAUDE.md` at the top of this repository — that is a plain markdown file that tells an assistant how to use this folder, and it is the pattern you build yourself in Module 2. You use it on Aug 27.

</details>

**What you are not doing today:** making an account, installing anything, or typing a single Git command. Sep 3 is the account. Today you only need to know what you are looking at.

---

## Getting into Copilot

On your own laptop.

1. Open a browser tab to **[copilot.microsoft.com](https://copilot.microsoft.com)**.
2. Sign in to your account — the same address you use for email.
3. You should land on a page with a box to type in. That is the whole setup.

**If you cannot get in, raise your hand.**

---

## Part 1 — What you are looking at

Before we touch a prompt, look at the thing you just signed into.

Every lab ships its own product — Copilot, ChatGPT, Gemini, Claude — and they compete hard on how those products look. Underneath, they have all landed on the same four controls. Learn them here and you can sit down in front of any of them.

- **The box.** You type here. Obvious, and it is where most people stop.
- **The microphone.** Talk instead of typing. Jarrod had you doing this last class.
- **The paperclip, or a `+`.** Takes a file off your computer and puts it in front of the model.
- **The dropdown just under the box.** It probably says **Quick response**. Open it and you get **Quick response**, **Think Deeper**, **Study and learn**, **Smart**, **Search**.

**Open that dropdown now.** It is free, it takes ten seconds, and almost nobody has ever done it.

Two questions before we go further.

**When would you attach a file instead of just typing out what is in it?**

<details><summary>Answer</summary>

The cheap answer is "when it would take too long to type." True, and it is the smaller reason.

The real one: **typing it out means summarizing it, and summarizing throws things away.** You decide in about four seconds which details survive, from memory, and what does not survive is the exact title, the exact date, the exact number, the exact wording. Hand over the document and you have thrown away nothing.

And some material you cannot retype at all — a twelve-page posting, a spreadsheet, a transcript. Attach when the real thing already exists and the specifics matter. You do one of these at the end of this part, and Aug 27 is nothing but this.

</details>

**And what is that dropdown actually choosing?**

<details><summary>Answer</summary>

Not a personality. Not a tone. **It is choosing a different model**, or at least a different amount of work the model is allowed to do before it answers.

That is a bigger deal than it looks, and the rest of this part is about why.

</details>


**There is no such thing as "the AI."** There are a handful of labs building frontier models, and each ships several models at once. When you open Copilot, ChatGPT, or Gemini, you are not talking to a company — you are talking to whichever specific model that product decided to route you to today.

**One product hides many models — and does not always tell you which one you got.** Go back to those five labels you just opened. They are not five models with five names. They are Microsoft's labels sitting on top of underlying models it does not show you, and which one you get can change without anyone telling you.

**Thinking models versus fast models.** That menu is this distinction made concrete. Quick response answers immediately. Think Deeper works through the problem before it starts writing — slower, and noticeably better at anything with more than one step: analysis, planning, math, code, anything where being wrong halfway through ruins the end. Quick response is fine for "rewrite this sentence." **If a task has steps, pick the thinking one.**

**Free tiers give you smaller models and fewer messages.** Study and learn, Smart, and Search are open to everyone. Think Deeper is too — but paid accounts get priority whenever Microsoft is busy, so at 4pm with twenty of us hitting it at once, expect it to be slower for some of you than others. That is the actual thing you would be paying for.

Now the uncomfortable part, at the start of a session about prompt engineering:

> **Choosing the right model is a bigger quality lever than anything you will do to your wording.** A mediocre prompt on a thinking model beats a beautifully crafted prompt on a fast one, most days. Get the model right first. Then everything below makes it better.

**So here are the labs and what they ship.** Written down on Aug 20, 2026, and going stale immediately — which is itself the lesson.

| Lab | Its models, cheapest first |
|---|---|
| Anthropic | Haiku · Sonnet · Opus |
| OpenAI | Luna · Terra · Sol |
| Google | Gemini Flash · Gemini Pro |

Notice the shape. Every one of them ships a small one, a middle one and a big one, and the names are the only part that differs. That shape will still be true in October when at least one of those names is wrong.

**The small ones are not the bad ones.** This is the part people get wrong. Haiku, Luna and Flash are not failed attempts at Opus, Sol and Pro — they are built to be cheap and fast, and they cost a fraction as much to run. For summarizing, sorting, extracting, reformatting, answering something simple: the small model finishes while the big one is still thinking, at a tenth of the price. Reaching for the largest model every time is how people run out of free messages by Wednesday.

The judgment you want is **match the model to the job**, not "always use the best one." Big model when being wrong is expensive. Small model when it is not.

### The paperclip, in thirty seconds

You met the attach button in the list above. Use it once now, so the rest of the semester has something to point back at.

**Download this file:** [womens_clothing_sales.csv](files/womens_clothing_sales.csv). Click it — GitHub shows you the contents as a table — then use the download button to save it to your laptop. Notice what just happened: you pulled a file out of a repository, and it was not code. A year of sales for a women's clothing retailer, one row per order.

First ask without it. Send this on its own, with nothing attached:

```
What are the most popular women's clothing items?
```

Read what comes back. Now click the paperclip, attach the CSV you just downloaded, and send **the exact same question again.**

```
What are the most popular women's clothing items?
```

**Identical wording both times. Compare the two answers.**

<details><summary>Answer</summary>

**The first answer was confident, reasonable, and about nothing.** You most likely got jeans, a little black dress, a white t-shirt, leggings — the standard list. Read it again and notice it never says where it came from. It is the statistical middle of everything ever written about women's clothing, and it is not about a business, a year, or a single real customer.

The uncomfortable part is that it did not feel like a failure. It answered immediately and it sounded right. **That is the failure mode to fear** — not a model that refuses, but a model that answers. A refusal is obvious. A confident generic answer reads exactly like knowledge.

**The second answer had to count.** With the file attached there are 1,000 real orders in front of it, and it can no longer reach for the standard list. If it read the file properly you should see the Maxi Dress at the top, Dresses as the leading category by a wide margin, and names like Culottes and Pleated Skirt that no generic answer would ever produce.

> **You changed not one word. The paperclip did all of it.**

**Now the second thing, and it is the one to carry into Part 4.** Look at *how* it decided what "popular" means. That word is doing a lot of unexamined work — this file supports at least two answers:

| "Popular" means | Top item |
|---|---|
| Most units sold | Button-Up Shirt and Maxi Dress, tied at 71 |
| Most money brought in | Maxi Dress, at $7,280 — and the Button-Up Shirt is nowhere near the top |

Both are correct. They are not the same answer, and a buyer deciding what to reorder would care enormously about which one you handed them. The model picked one for you and probably did not mention that it had a choice.

**It picked because you left it room to pick.** That is not a bug and it is not the model being careless — a vague word gets a vague reading, and something has to fill the gap. The rest of today is about deciding when to leave that room open and when to close it.

</details>

---
## Part 2 — Warm-up: one prompt, two models

Last class you all sent identical text and got back different answers. That is worth restating in one line, because it is the floor everything else sits on: **the same input does not guarantee the same output.** This is not a search engine looking up a stored result. It is generating text token by token, choosing from a range of likely next tokens, and it does not always choose the same one. Which is why you cannot memorize a magic prompt, and why "it worked when I tried it" proves nothing.

Today, one variable further. Send **one prompt twice**, changing nothing but the dropdown.

Set the mode to **Quick response** and send this.

```
I have three hours on Saturday and no money to spend. Tell me exactly how to use
that time to make my personal website more likely to get me an internship
interview. Give me a plan I could actually follow, and tell me what to skip.
```

Now set the mode to **Think Deeper** and send the identical prompt again. Do not change a word. It will be slower. Wait for it — the waiting is the thing you are looking at.

**Put the two answers side by side. How much of that difference could you have gotten by rewording?**

<details><summary>Answer</summary>

Almost none of it. **You changed zero words.** Every bit of the difference came out of a dropdown that almost nobody opens.

Look at what specifically changed. Quick response usually hands you a tidy list of generic website advice — true, fast, and it would read the same for anyone who asked. Think Deeper tends to notice that you said *three hours* and *no money*, and to ration against those constraints: sequence, tradeoffs, what to cut. It engaged with your actual situation because it worked through the problem before it started writing.

That is the claim from Part 1, now sitting on your screen instead of in a blockquote:

> **Choosing the model is a bigger lever than choosing the words.**

Two things to keep straight, because they get run together:

- **Same model, twice** — you get different wording, roughly equal quality. That is last class.
- **Different models, same prompt** — you get different *quality*, and the gap is much wider. Both answers to that dropdown are plausible English. Only one of them thought about your three hours.

None of which means Think Deeper is always the answer. It is slower, it burns your free messages faster, and for "rewrite this sentence" it buys you nothing. Match the model to the job — same lesson as the small models above. **But when a task has steps, pick the thinking one.**

</details>

---

## Part 3 — What the models already absorbed

**Leave Copilot open and start a new tab at google.com.** Nothing else to change.

Two reasons we run this one in Google. The small one: the answer at the top of a results page is a model too, and most people have never thought of it that way. The one that matters today: unlike Copilot, it is not carrying anything from your previous conversations. So the only thing that differs between the two answers below is the words you typed.

Paste this into the search box.

```
You are a world-class copywriter with 20 years of experience. Take a deep breath and think step by step. Write an About Me page for a personal website.
```

Now clear the box and paste this.

```
Write an About Me page for a personal website.
```

**Read both. How different are they, really?**

<details><summary>Answer</summary>

Probably barely different, and both probably generic.

Here is the honest history. In 2023, the first prompt genuinely beat the second. Telling a model to act as an expert, or to take a deep breath, or to think step by step, measurably improved its output. People built entire businesses selling libraries of phrasings like these.

Then the labs trained those behaviors in. A current model does not need to be told to be careful or to reason through a problem — that is now default behavior. The expert persona mostly just spends tokens.

Be skeptical accordingly. Most "prompt engineering" advice you will find online was written for models that no longer exist, and a lot of what still circulates is theater.

One caveat, so you do not over-read this: the model behind a Google result is small and fast, so it flattens most inputs toward the same answer anyway. This is a clean comparison, not a rigorous one. The claim it supports is narrow — the tricks are not the lever people think they are.

**Now notice what both prompts have in common:** neither one told the model a single thing about *you*. That is the actual problem, and no amount of persona theater fixes it. That is Part 4.

</details>

**One thing to carry forward.** We sent you to Google to get a guaranteed clean slate, because it is the version you can see. Copilot has its own: the **Temporary chat** — look for it near the top of the window, usually a small icon or an item in the menu beside the New chat button. A temporary chat does not read your saved personalization and never gets written to your history. It is the same idea in the tool you are actually going to use, and you will use it for the rest of today.

Why any of this matters: **a model's answer depends on everything sitting in the conversation, not only on what you typed.** Saved memory, earlier turns, a file you attached ten minutes ago — all of it is steering the output. When you are comparing two prompts, every one of those is a second variable, and you can no longer tell which change caused which result. A clean slate is how you isolate the one thing you meant to test.

Why it happens that way is Aug 27.

---

## Part 4 — Build the brief

This is the core of today.
**Open a Temporary chat** — the one you just read about in Part 3.

That is not housekeeping, it is the whole reason the next twenty minutes work. If you have used Copilot before, it may already know things about you, and Pass 1 will come back better than it has any right to, hiding exactly what we are trying to show you. A temporary chat cannot reach any of that. **Use a fresh Temporary chat for each numbered part from here on** — Parts 4, 5 and 6 alike.

> **A temporary chat is not saved.** Close it and the text is gone. When you get something you like today, copy it out and paste it somewhere that persists before you move on. That includes the version you leave with.

Three prompts. Send them in order, in one conversation. Keep all three answers where you can see them.

### Pass 1 — what you would have written anyway

```
Write an About Me page for my website.
```

### Pass 2 — add the specification

Same request. Now say who it is for, how long, what voice, and what to avoid. None of this is a trick. It is what you would tell a person.

```
Write the About Me section for my personal website.

It is read by employers deciding whether to interview me for an internship.
Two short paragraphs, first person, plain language. No buzzwords - do not use
"passionate," "driven," or "results-oriented." I would rather sound specific
than impressive.
```

### Pass 3 — add what only you know

Same again, plus the facts. Replace the bracketed parts with things that are actually true about you.

```
Write the About Me section for my personal website.

It is read by employers deciding whether to interview me for an internship.
Two short paragraphs, first person, plain language. No buzzwords - do not use
"passionate," "driven," or "results-oriented." I would rather sound specific
than impressive.

About me: I am a [YEAR] [MAJOR] major at Xavier University. Two things I have
actually done that I would want an employer to know: [THING ONE], [THING TWO].
```

**Which jump was bigger — 1 to 2, or 2 to 3?**

<details><summary>Answer</summary>

For most people, 2 to 3, and it is not close.

**Pass 1** could have been typed by anyone on earth, so you got what anyone on earth gets: the statistical middle of every About Me page ever written. Remember Tuesday — the model is predicting likely next tokens. A vague prompt leaves an enormous range of likely next tokens, and averaging them is the safest thing it can do. Generic input, generic output. That is mechanism, not laziness.

**Pass 2** narrowed the range. Audience, length, voice, and a list of banned words are real constraints, and the output got measurably less generic. This is the part people skip.

**Pass 3** did something the other two could not do at all. Every model was trained on millions of About Me pages, so it has seen every *form* your page could take. It has never seen `[THING ONE]`. That fact exists nowhere in its training data and can only come from you.

That is worth sitting with, because it is the durable version of this lesson: **the part of the work that does not get automated is the part that depends on knowing something.** No future model, however good, will know what you did last summer.

The pattern to carry out of this room:

> **Say what you want. Then say what only you know.**

</details>

---

## Part 5 — Where to leave the model room

Everything in Part 4 pushed one direction: be more specific. Now the counterweight, because "always be more specific" is wrong and will cost you.

**Over-specifying is its own failure mode.** When you already know exactly what you want, pin it down. But when you *don't* — and at the start of a project you usually don't — a highly specific prompt locks the model into your first idea and hands you back a polished version of something you had not finished thinking about. You lose the one thing the model is genuinely good at: showing you options you would not have generated yourself.

The move is to **pin the constraints and leave the direction open.**

```
I am building a personal website to show employers when I apply for internships.
I am a [YEAR] [MAJOR] major at Xavier University.

Do not write the site yet. Give me five genuinely different directions I could
take it - different in what the site is trying to prove about me, not just
different colors. One sentence each. Include at least one you think I probably
would not have considered.
```

**Look at the five. Was any of them better than the idea you walked in with?**

<details><summary>Answer</summary>

Notice what was still tightly specified: who you are, who is reading, that you want five, that they must differ on substance rather than styling, that you want one outside your own instincts, and — critically — **do not write it yet.**

That last clause is doing real work. Without it the model picks a direction and starts drafting, and once there is a draft on screen you will anchor to it.

The skill is not "be specific" or "be vague." It is knowing **which dial to pin and which to leave loose**:

- Pin the constraints — audience, format, length, tone, what to avoid, what done looks like.
- Leave loose the thing you are actually trying to discover.

Getting this backwards is the single most common way people waste time with these tools. They leave the constraints vague, so the output is unusable, and they over-specify the direction, so they never see an idea that was not already theirs.

</details>

---

## Part 6 — Make it interview you

One more move, and it is the one most people have never seen. Instead of writing a better brief, make the model find out what your brief should have said.

**A fresh Temporary chat — this one especially.** If you run it in the thread where you already told it everything in Part 4, it has nothing left to ask you and the whole exercise falls flat.

```
I need an About Me page for a personal website. Before you write anything, ask
me five questions that would help you write it well. Ask them one at a time and
wait for my answer before asking the next one.
```

Answer its questions honestly. Then, when it has all five:

```
Now write it, using everything I just told you.
```

**Compare this to your best result from Part 4.**

<details><summary>Answer</summary>

Two clauses make this work, and both are easy to drop:

- **"Before you write anything"** — otherwise it writes first and asks afterward, which is useless.
- **"One at a time and wait"** — otherwise you get five questions in a wall and answer them all badly.

Why it beats writing a careful brief from scratch: it does not require you to already know what matters. Parts 4 and 5 asked you to specify the right things up front. This flips it — the model has seen enough About Me pages to know which facts distinguish a good one, so let it ask.

Use this whenever you are starting something you have not done before. It is the fastest way from "I need a thing" to "I know what the thing should be."

</details>

---

## Before you leave the room

**Save the output — and today that is not automatic.** You worked in temporary chats, which are not written to your history, so closing the tab loses everything in it. Copy your best About Me text out now and keep it somewhere you can find it — you build on it on Aug 27 and it becomes part of your website, which is due Thursday Sep 10.

**Your participation file.** Every class ends with one file, and it is worth 4 points.

1. Write a plain-text file named `session-02.txt`. Since this was a build session, it is a build log: **what you built, what broke, what's next.** Typed in your own words, no formatting, no polish.
2. **Upload it to Canvas**.
3. **Also save a copy** into `my-work/class-notes/` in your course folder.

**Bring a document with you on Aug 27.** You attached one file today — the sales spreadsheet — and saw what it did to the answer. Next session that stops being a demo and becomes the whole method — you hand the model things that already exist instead of typing them out. It only works if you show up with something. Find one document that is about you or was written by you, and have it on your laptop:

- A resume
- A paper or long assignment you wrote
- Your class schedule, degree audit, or transcript
- A scholarship, application, or cover-letter essay
- A job description for a job you have held
- Your LinkedIn profile, exported as a PDF — open your profile, click **More**, choose **Save to PDF**
- A club, team, or organization bio, or a description of a role you hold
- A group project report or deck you contributed to

One is enough, more is better. PDF, Word, or plain text all work — if it lives in Google Docs, use File → Download and pick PDF. Have a look at what is in it before class, since anything you upload leaves your laptop, and pick something else if it holds a home address, an ID number, or your grades.

**Not today:** the actual `.html` file. That is Aug 27. Today you wrote what goes in it.

---

*MGMT 342 · Session 2 · Fall 2026 · Xavier University · Humphrey & Mathai*
