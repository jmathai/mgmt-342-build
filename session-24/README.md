# Session 24 — Describe it before you build it

**Tuesday, November 10 · 4:00–5:15 PM · CFI · lab machine**

---

## Bring these

- **A problem from your career field.** Something that wastes your time, costs money or causes mistakes in a job you have or want.

---

## Where today goes

Module 4 is a small web app that solves a real problem in your field. It runs on your computer and works on a phone. The app should be small - don’t spend all your time on the app.

Today you do not build anything. You describe it. In class you write three documents:

1. **The problem.** Who has it and what it costs them.
2. **The evidence.** How you will show the problem is real and the app helps. Your survey goes out today.
3. **The solution.** What the app does, step by step.

After class you write two more:

4. **The web page.** The page that explains the app to someone in your field.
5. **The ad.** A 30 to 60 second commercial script.

Every one of these gets handed to an agent later. The agent builds the app from `solution.md` on Thursday. It builds the web page from `web-page.md`. On November 19 you produce the commercial from `ad-script.md`. Whatever you leave vague, the agent fills in with a guess.

---

## Part 1 — When to provide details?

How detailed do you think your .md files should be?

When’s a good time to be open ended and when is a good time to be detailed?



---

## Part 2 — Set up your folder

Make a folder for Module 4 in your own repository. What do you think goes in CLAUDE.md?

```
module4-app/
  CLAUDE.md
  problem.md
  evidence.md
  solution.md
  web-page.md
  ad-script.md
```

At minimum, `CLAUDE.md` is the map: which file holds what, and that `solution.md` is what the agent builds the app from.

Open `module4-app/` in VS Code. You write each file with the agent. You decide what goes in it.

### How to push for detail

**After** you draft each file, send this:

```
Read [FILE]. Interview me about it. Ask me five questions about what is
missing, vague or would leave you guessing if you had to build from it.
Ask them one at a time and wait for my answer.
```

---

## Part 3 — The problem

Write `problem.md`. Answer each of these in plain sentences:

```markdown
# The problem

## Who has it
[THE PERSON, THEIR JOB, AND THE SITUATION THEY ARE IN WHEN IT HAPPENS.]

## What it costs them
[TIME, MONEY, MISTAKES OR STRESS. USE A NUMBER IF YOU HAVE ONE, EVEN A ROUGH ONE.]

## How they handle it today
[THE SPREADSHEET, THE EMAIL, THE STICKY NOTE, THE THING THEY JUST LIVE WITH.]

## Why that falls short
[WHAT GOES WRONG WITH THE WAY THEY DO IT NOW.]

## How they would know it is solved
[WHAT IS DIFFERENT AFTERWARD. SOMETHING YOU COULD CHECK.]
```

Then run the interview.

<details><summary>My problem is too big</summary>

If the app needs a login, a database of every customer or a connection to a system you cannot reach, it is too big. Pick one moment inside the problem. "Managing inventory" is too big. "Knowing what to reorder on Friday afternoon" is the right size.

</details>

---

## Part 4 — The evidence

Your business case has to show two things: the problem is real, and the app helps. Do this part right after `problem.md`. The survey has to go out today.

Write `evidence.md`.

```markdown
# Evidence

## The problem is real
What I need to show: [TAKE IT FROM "WHAT IT COSTS THEM" IN problem.md.]

### What research says
[WHAT THE AGENT FOUND: HOW COMMON THE PROBLEM IS AND WHAT IT COSTS. EACH CLAIM WITH A SOURCE YOU OPENED.]

### What people who have it say
Survey link: [PASTE IT HERE.]
Who I sent it to: [1 OR 2 PEOPLE IN YOUR FIELD WHO HAVE THE PROBLEM.]
What would tell me I am wrong: [THE ANSWER THAT MEANS THE PROBLEM IS SMALLER THAN YOU THINK.]

## The app helps
Who tests it: [A CLASSMATE, ON NOVEMBER 17.]
What they do: [READ THE WEB PAGE, DO ONE TASK IN THE APP, GIVE FEEDBACK.]
What I write down: [WHERE THEY GOT STUCK AND HOW LONG IT TOOK.]
What would tell me I am wrong: [WHAT THE TESTER DOES THAT MEANS THE APP DID NOT HELP.]
```

**Send the survey first.** Three to five questions, taken from `problem.md`: Does this happen to you? How often? What does it cost you when it does? How do you handle it today? Build it in Microsoft Forms or Google Forms and send it now. Ask for answers by Thursday. On Thursday you give the answers to the agent along with `solution.md`, and change the plan where they disagree with it.

A classmate cannot answer the survey unless they have the problem too. Classmates test the app. People in your field answer the survey.

<details><summary>Who do I send it to?</summary>

Classmates in your major, people from an internship or job, a professor in your department, family members who do the work. Two honest answers from people who have the problem beat twenty from people who do not.

</details>

**Then do the agent research.** Send this:

```
Read problem.md. Research how common this problem is for people in
[YOUR FIELD] and what it costs them. Give me each finding with a link to
its source. Tell me where you could not find good evidence. Do not fill
a gap with a guess.
```

Open every link. Delete any claim whose source does not say what the agent says it does.

The research and the people answer different questions. Research tells you the problem exists in your field. People tell you it exists for the people you will build for. You need both.

Then run the interview.

---

## Part 5 — The solution

Write `solution.md`.

```markdown
# The solution

## In one sentence
[WHAT THE APP DOES.]

## What someone does with it
[STEP BY STEP, FROM OPENING IT ON THEIR PHONE TO FINISHING THE TASK.]

## The screens
[EACH SCREEN: WHAT IT SHOWS, WHAT YOU CAN TAP, WHAT HAPPENS WHEN YOU TAP IT.]

## What it does not do
[THE FEATURES YOU ARE LEAVING OUT ON PURPOSE.]

## Where the information comes from
[WHAT THE PERSON TYPES IN, AND WHAT THE APP ALREADY KNOWS.]
```

"What it does not do" matters. It is what keeps the app tiny. If you leave it out, the agent adds features.

Then run the interview.

---

## Discussion (if time)

- What did the interview ask that you had not thought about?
- Whose "What it does not do" list was the longest? Did it make the app clearer?
- Read your problem in one sentence to the person next to you. Can they tell you who has it?

---

## Done early?

- **Run the interview a third time** on `solution.md`. That is the file the agent builds from on Thursday.
- **Sketch the main screen.** On paper or with the agent. Save it in `module4-app/`.
- **Have the agent read all your files** and tell you where they disagree with each other.
- **Start the web page or the ad** below.

---

## Before you leave the room

1. Send the survey to 1 or 2 people who have the problem.
2. Commit `module4-app/` with `CLAUDE.md`, `problem.md`, `evidence.md` and `solution.md`.

On Thursday you hand `solution.md` and your survey answers to the agent and build the first version.

---

## After class — the web page and the ad

Write `web-page.md` before November 17. Your classmate reads the web page before testing the app. Write `ad-script.md` before November 19. Run the interview on each, the same as in class.

### The web page

Write `web-page.md`. This is the copy, not the page. The agent builds the page from it later.

```markdown
# Web page

## Headline
[ONE LINE.]

## Subhead
[ONE OR TWO SENTENCES.]

## The problem, in the user's words
[HOW SOMEONE IN YOUR FIELD WOULD DESCRIBE IT TO A COWORKER.]

## How the app helps
[THREE POINTS. ONE SENTENCE EACH.]

## What to do next
[THE ONE THING YOU WANT THE READER TO DO.]

## Look and feel
[COLORS, TONE, ANY IMAGE YOU WANT ON IT.]
```

You are not selling anything. The page explains to someone in your field why this problem is worth solving and how the app does it.

### The ad

Write `ad-script.md`. A 30 to 60 second commercial. On November 19 you make it with AI image, video and sound tools, so describe what is on screen and what is heard, not just what is said.

```markdown
# Ad script

## Length
[30, 45 OR 60 SECONDS.]

## The scenes
| Seconds | On screen | Voice or text | Sound |
|---|---|---|---|
| 0–5 | [THE HOOK] | | |
| | [THE PROBLEM MOMENT] | | |
| | [THE APP SOLVING IT] | | |
| | [THE CLOSING LINE] | | |

## Tone
[FUNNY, SERIOUS, CALM, FAST. PICK ONE.]
```

<details><summary>I do not know what a scene should look like</summary>

Ask the agent for three versions of the hook scene, each in a different tone. Pick one and say why. The choice has to be yours.

</details>

---

*MGMT 342 · Session 24 · Fall 2026 · Xavier University · Humphrey & Mathai*
