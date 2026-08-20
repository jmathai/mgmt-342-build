# Session 2 — Prompt engineering

**Thursday, August 20 · 4:00–5:15 PM · CFI · your own laptop**

This page is the session. Work down it with us. Every prompt sits in a grey box with a **copy icon** in its top-right corner — click the icon, then paste. Do not retype anything.

**Two tools today.** Copilot, and GitHub, which you are reading this on right now.

**One rule before we start:** some prompts contain `[SQUARE BRACKETS]`. Replace those with things that are actually true about you before you send. Leave them in and the model will write about `[YOUR MAJOR]`.

**Where you end up:** by 5:15 you will have written the real text for your website's About page — the first piece of your Module 1 Build.

---

## Where this page lives

**You are reading this on GitHub.** It is sort of like Canvas or a course website, and a little different. This page is a file, sitting in a folder, and you are looking at it in a browser like any other web page. No account, no install, no login.

**A repository is a collection of files.** That is the entire idea. People say "repo." It keeps files together, backs them up, and lets you share them — think OneDrive for now.

**Look up.** Above this page is a path: repository name, then folder, then this file. Click the repository name at the far left.

**Look at what is there. How much of it is code?**

<details><summary>Answer</summary>

None of it.

Folders — `session-2` — and a couple of files at the top. `README.md` is the one that displays on its own when you open a folder, which is why this page appeared without you clicking a file name.

GitHub is where the world keeps its code, so everyone assumes a repository *is* code. **A repository holds files. What kind is your business.**

What you are reading is **markdown**: plain text with a few marks in it. `#` makes a heading, `**` makes bold, `-` makes a bullet. That is most of the language.

**Markdown is what models read and write well**, for three reasons:

- **It is plain text.** A Word file or PDF has to be pulled apart before a model can read it, and the structure gets mangled. Markdown arrives intact.
- **The marks carry the structure.** The model sees the same headings and lists you see, so it can tell a rule from an example.
- **They were trained on mountains of it.** Most documentation and most of GitHub is markdown. That is why answers come back with headings and bullets you never asked for.

Which is why instructions written *for* AI are markdown files. `CLAUDE.md` at the top of this repo is one — it tells an assistant how to use this folder. You build your own in Module 2.

</details>

---

## Getting into Copilot

On your own laptop.

1. Open a browser tab to **[copilot.microsoft.com](https://copilot.microsoft.com)**.
2. Sign in to your account — the same address you use for email.
3. You should land on a page with a box to type in. That is the whole setup.

**If you cannot get in, raise your hand.**

---

## Part 1 — What you are looking at

Every frontier lab ships its own product — Copilot, ChatGPT, Gemini, Claude — and they compete hard on how those look. Underneath, all of them have the same four controls.

- **The box.** You type here. It is where most people stop.
- **The microphone.** Talk instead of typing. Jarrod had you doing this last class.
- **The paperclip, or a `+`.** Takes a file off your computer and puts it in front of the model.
- **The dropdown near the box.** Open it. You will see something like **Smart**, **Study and learn**, and **Search**.

**Open that dropdown now.** Menus differ between accounts and Microsoft changes them often.

**When would you attach a file instead of typing out what is in it?**

<details><summary>Answer</summary>

Not mainly to save typing. **Typing it out means summarizing, and summarizing throws things away.** You decide in four seconds which details survive, and what dies is the exact title, date, number, wording. Hand over the file and you lose nothing.

Some material you cannot retype at all — a spreadsheet, a transcript, a twelve-page posting. Attach when the real thing exists and the specifics matter. You do one at the end of this part.

</details>

**And what is that dropdown choosing?**

<details><summary>Answer</summary>

It differs between products. **It may change the model or the prompt.**

</details>

**There is no such thing as "the AI."** A handful of labs build frontier models, and each ships several at once. Open Copilot, ChatGPT or Gemini and you are not talking to a company — you are talking to whichever model that product routed you to today.

**One product hides many models.** Those labels you just opened are not model names. They are Microsoft's labels sitting on top of models (or prompts) it does not show you, and which one you get can change without anyone telling you.

**The two things a menu like that controls** are how much work the model does before answering, and whether it goes and looks things up first. Both matter more than wording. You test the second one in Part 2.

**Free tiers give you smaller models and fewer messages.** Paid accounts get priority when Microsoft is busy, so at 4pm with twenty of us at once, expect it slower for some of you. That is the actual thing you would be paying for.

Now the uncomfortable part, at the start of a session about prompt engineering:

> **Choosing the right model is a bigger quality lever than anything you do to your wording.** Get the model right first. Then everything below makes it better.

**The labs and what they ship.**

| Lab | Its models, cheapest first |
|---|---|
| Anthropic | Haiku · Sonnet · Opus |
| OpenAI | Luna · Terra · Sol |
| Google | Gemini Flash · Gemini Pro |

Every lab ships a small one, a middle one and a big one.

**The small ones are not the bad ones.** Haiku, Luna and Flash are not failed attempts at Opus, Sol and Pro. They are built cheap and fast. For summarizing, sorting, extracting, reformatting, the small model finishes while the big one is still thinking, at a tenth of the price. Reaching for the largest model every time is how people run out of free messages by Wednesday.

I use a small low cost model for an app I created so that I can offer it for free.

**Match the model to the job.** Big model when being wrong is expensive. Small model when it is not.

### The paperclip, in thirty seconds

**Download this file:** [womens_clothing_sales.csv](files/womens_clothing_sales.csv). Click it — GitHub shows the contents as a table — then download it to your laptop. A year of sales for a clothing retailer, one row per order. You just pulled a file out of a repository, and it was not code.

First ask without it. Send this with nothing attached:

```
What are the most popular women's clothing items?
```

Now click the paperclip, attach the CSV, and send **the exact same question again.**

```
What are the most popular women's clothing items?
```

**Identical wording both times. Compare the answers.**

<details><summary>Answer</summary>

**The first answer was confident and about nothing.** Jeans, a little black dress, a white t-shirt, leggings — the standard list. It never says where that came from, because it came from the middle of everything ever written about women's clothing. Not from a business, a year, or a single real customer.

It did not feel like a failure. It answered fast and sounded right. **That is the failure mode to fear** — not a model that refuses, but one that answers. A refusal is obvious. A confident generic answer reads exactly like knowledge.

**The second answer had to count.** With 1,000 real orders in front of it, it cannot reach for the standard list. You should see the Maxi Dress at the top, Dresses leading by a wide margin, and names like Culottes and Pleated Skirt that no generic answer would produce.

> **You changed not one word. The paperclip did all of it.**

**Now look at how it decided what "popular" means.** The file supports two answers:

| "Popular" means | Top item |
|---|---|
| Most units sold | Button-Up Shirt and Maxi Dress, tied at 71 |
| Most money brought in | Maxi Dress, at $7,280 — Button-Up Shirt nowhere near the top |

Both correct. A buyer deciding what to reorder would care enormously which one you handed them. The model picked for you and probably never mentioned it had a choice.

**It picked because you left it room to pick.** A vague word gets a vague reading, and something has to fill the gap. The rest of today is deciding when to leave that room open and when to close it.

</details>

---

## Part 2 — One prompt, two modes

Last class you all sent identical text and got different answers back. **The same input does not guarantee the same output.**

Now one variable further. Send **one prompt twice**, changing nothing but the dropdown.

Set the mode to **Smart** and send this.

```
I have three hours on Saturday and no money to spend. Tell me exactly how to use
that time to make my personal website more likely to get me an internship
interview. Give me a plan I could actually follow, and tell me what to skip.
```

Now switch the mode to **Search** and send the identical prompt again. Do not change a word.

Selecting "Search" tells the underlying AI model to prioritize finding facts from an outside source rather than changing the actual AI engine itself.

**Put the two side by side. How much of that difference could you have gotten by rewording?**

<details><summary>Answer</summary>

None of it. **You changed zero words.**

The two modes answer from different places. **Smart** answers out of what the model already absorbed in training — fluent, fast, and it cannot tell you anything it did not already know. **Search** goes and fetches pages first, then writes from them. That usually reads more concrete and more current, and it can point at where something came from.

> **Where the answer comes from is a bigger lever than how you word it.**

Which is the same lesson the paperclip just taught. There are two ways to get material in front of a model: **you hand it over**, or **it goes and gets it.** Search is the second one, running automatically.

**Search is not automatically better.** If it retrieves junk, you get junk delivered fluently. And for anything about *you* there is nothing out there to retrieve — no amount of searching finds what you did last summer. That is what the rest of today is for.

</details>

---

## Part 3 — What the models already absorbed

**Open a Temporary chat.** Look near the top of the Copilot window, beside the New chat button. It does not read your saved personalization and never gets written to your history. You use it for the rest of today.

*No Temporary chat in your version? Use **google.com** instead. A search box carries nothing from your previous conversations either, and the answer at the top of a results page is a model too — most people never think of it that way. Everything below works the same.*

Why it has to be clean: **a model's answer depends on everything in the conversation, not only on what you typed.** Saved personalization, earlier turns, a file you attached ten minutes ago — all of it steers the output. Compare two prompts with any of that in the way and you cannot tell which change caused which result. Why it works that way is Aug 27.

Send this.

```
You are a world-class copywriter with 20 years of experience. Take a deep breath and think step by step. Write an About Me page for a personal website.
```

**Now open a second Temporary chat** — a fresh one, not a reply in the first — and send this.

```
Write an About Me page for a personal website.
```

**Read both. How different are they, really?**

<details><summary>Answer</summary>

Barely different, and both generic.

In 2023 the first prompt genuinely beat the second. Telling a model to act as an expert, take a deep breath, or think step by step measurably improved its output, and people built businesses selling libraries of these phrasings.

Then the labs trained those behaviors in. A current model does not need to be told to reason through a problem. The expert persona mostly just spends tokens.

Be skeptical accordingly: most prompt engineering advice online was written for models that no longer exist.

This is a clean comparison, not a rigorous one — especially if you fell back to Google, where the model is small and fast and flattens most inputs toward the same answer anyway. The claim it supports is narrow: the tricks are not the lever people think they are.

**Now notice what both prompts have in common:** neither told the model anything about *you*. That is the actual problem, and persona theater does not fix it. That is Part 4.

</details>

---

## Part 4 — Build the brief

This is the core of today. **Open a Temporary chat.**

If you have used Copilot before it may already know things about you, and Pass 1 will come back better than it has any right to — hiding exactly what we are trying to show you. A temporary chat cannot reach any of that. **Use a fresh Temporary chat for each part from here on.**

> **A temporary chat is not saved.** Close it and the text is gone. Copy anything you like out before you move on.

Three prompts, in order, in one conversation. Keep all three answers where you can see them.

### Pass 1 — what you would have written anyway

```
Write an About Me page for my website.
```

### Pass 2 — add the specification

Same request. Now say who it is for, how long, what voice, and what to avoid. It is what you would tell a person.

```
Write the About Me section for my personal website.

It is read by employers deciding whether to interview me for an internship.
Two short paragraphs, first person, plain language. No buzzwords - do not use
"passionate," "driven," or "results-oriented." I would rather sound specific
than impressive.
```

### Pass 3 — add what only you know

Same again, plus the facts. Replace the bracketed parts with things that are true about you.

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

For most people, 2 to 3.

**Pass 1** could have been typed by anyone, so you got what anyone gets: the middle of every About Me page ever written. A vague prompt leaves an enormous range of likely next tokens, and averaging them is the safest thing it can do. Generic input, generic output — mechanism, not laziness.

**Pass 2** narrowed the range. Audience, length, voice and banned words are real constraints. This is the part people skip.

**Pass 3** did something the others could not. Every model was trained on millions of About Me pages, so it has seen every *form* yours could take. It has never seen `[THING ONE]`. That fact exists nowhere in its training data.

**The part of the work that does not get automated is the part that depends on knowing something.** No future model will know what you did last summer.

> **Say what you want. Then say what only you know.**

</details>

---

## Part 5 — Where to leave the model room

Everything in Part 4 pushed one direction: be more specific. Now the counterweight, because "always be more specific" is wrong.

**Over-specifying is its own failure mode.** When you know exactly what you want, pin it down. When you *don't* — and at the start of a project you usually don't — a highly specific prompt locks the model into your first idea and hands back a polished version of something you had not finished thinking about. You lose the thing it is genuinely good at: showing you options you would not have generated.

**Pin the constraints and leave the direction open.**

```
I am building a personal website to show employers when I apply for internships.
I am a [YEAR] [MAJOR] major at Xavier University.

Do not write the site yet. Give me five genuinely different directions I could
take it - different in what the site is trying to prove about me, not just
different colors. One sentence each. Include at least one you think I probably
would not have considered.
```

**Look at the five. Was any better than the idea you walked in with?**

<details><summary>Answer</summary>

Notice what was still tightly specified: who you are, who is reading, that you want five, that they differ on substance rather than styling, that you want one outside your instincts, and — critically — **do not write it yet.**

That last clause does real work. Without it the model picks a direction and starts drafting, and once a draft is on screen you anchor to it.

The skill is not "be specific" or "be vague." It is knowing **which dial to pin and which to leave loose**:

- Pin the constraints — audience, format, length, tone, what to avoid.
- Leave loose the thing you are trying to discover.

Getting this backwards is the most common way people waste time with these tools. Vague constraints make the output unusable; an over-specified direction means never seeing an idea that was not already yours.

</details>

---

## Part 6 — Make it interview you

Instead of writing a better brief, make the model find out what your brief should have said.

**A fresh Temporary chat — this one especially.** Run it where you already told it everything in Part 4 and it has nothing left to ask.

```
I need an About Me page for a personal website. Before you write anything, ask
me five questions that would help you write it well. Ask them one at a time and
wait for my answer before asking the next one.
```

Answer honestly. Then, when it has all five:

```
Now write it, using everything I just told you.
```

**Compare this to your best result from Part 4.**

<details><summary>Answer</summary>

Two clauses make it work, and both are easy to drop:

- **"Before you write anything"** — otherwise it writes first and asks afterward.
- **"One at a time and wait"** — otherwise you get five questions in a wall and answer them all badly.

It beats writing a careful brief because it does not require you to already know what matters. Parts 4 and 5 asked you to specify the right things up front. This flips it: the model has seen enough About Me pages to know which facts distinguish a good one, so let it ask.

Use this whenever you start something you have not done before.

</details>

---

## Before you leave the room

**Save the output — today that is not automatic.** Temporary chats are not written to your history, so closing the tab loses everything. Copy your best About Me text out now. You build on it Aug 27 and it becomes part of your website, due Thursday Sep 10.

**Your participation file.** Every class ends with one file, worth 4 points.

1. Write a plain-text file named `session-02.txt`. Build session, so it is a build log: **what you built, what broke, what's next.** Your own words, no formatting.
2. **Upload it to Canvas**.
3. **Also save a copy** into `my-work/class-notes/` in your course folder.

**Bring a document with you on Aug 27.** You attached one file today and saw what it did. Next session that becomes the whole method — you hand the model things that already exist instead of typing them out. Find one document that is about you or was written by you:

- A resume
- A paper or long assignment you wrote
- Your class schedule, degree audit, or transcript
- A scholarship, application, or cover-letter essay
- A job description for a job you have held
- Your LinkedIn profile, exported as a PDF — open your profile, click **More**, choose **Save to PDF**
- A club, team, or organization bio, or a description of a role you hold
- A group project report or deck you contributed to

One is enough, more is better. PDF, Word, or plain text all work — from Google Docs, use File → Download and pick PDF. Look at what is in it before class, since anything you upload leaves your laptop. Pick something else if it holds a home address, an ID number, or your grades.

**Not today:** the actual `.html` file. That is Aug 27. Today you wrote what goes in it.

---

*MGMT 342 · Session 2 · Fall 2026 · Xavier University · Humphrey & Mathai*
