# Session 10 — Using context go get AI to do your work

**Thursday, September 17 · 4:00–5:15 PM · CFI · lab machine**

**Bring these:**
- Your **GitHub username and password.** You are signing in on a machine that is not yours. If you use two-factor, bring the phone.
- The **link to your live site** — `https://yourusername.github.io`.

---

## Where today goes

Session 8 gave the agent **reach** — it could see your files and run commands on this machine. Today is about **instructions**: what you write down in a folder so you never have to explain it again.

Three kinds, in the order you meet them:

| | What it is | When it applies |
|---|---|---|
| **A skill someone else wrote** | A folder of instructions you install | When the request matches it |
| **`CLAUDE.md`** | Standing instructions for one folder | Every single time |
| **A skill you write** | Instructions for a job you do over and over | When the request matches it |

### Today’s pace

Lots to cover, here’s what we’ll target. Ask if you’re behind or have questions.

| By | You should be through |
|---|---|
| 4:10 | Part 1 — signed in to GitHub |
| 4:20 | Part 3 — skill installed |
| 4:35 | Part 4 — your site published by asking |
| 4:45 | Part 5 — `CLAUDE.md` |
| 5:10 | Part 6 — your own skill written and run |

---

## Part 1 — Sign in to GitHub

Your work lives in a GitHub repository. Claude cannot reach it until you hand this machine a credential.

`gh` is GitHub's command-line tool — the same GitHub you clicked through in Session 6, minus the web page. It is installed on this machine.

1. Open VS Code.
2. Open the **terminal**: **Terminal → New Terminal**
3. Type this and press Enter:

```
gh auth login
```

4. It asks four questions. Arrow keys to choose, Enter to confirm:

| It asks | You pick |
|---|---|
| Where do you use GitHub? | **GitHub.com** |
| Preferred protocol for Git operations? | **HTTPS** |
| Authenticate Git with your GitHub credentials? | **Yes** |
| How would you like to authenticate GitHub CLI? | **Login with a web browser** |

5. It prints a **one-time code** like `XXXX-XXXX`. Copy it, then press Enter — a browser opens.
6. Paste the code, sign in, click **Authorize**.
7. Back in VS Code, it confirms you are logged in.

**Check it worked.** Two commands. The first one only has to be run once, ever:

```
gh config set pager cat
```

```
gh api user --jq .login
```

**It should print your GitHub username back at you.** That is the checkpoint for Part 1. If it does, this machine can now act as you on GitHub.

Close your terminal, you don’t need it anymore.


<details><summary>Why did you have to do this yourself instead of asking Claude?</summary>

Because it is a login, and a login is the one place where "the AI does it for you" has to stop.

Claude can run `gh auth login` — it just cannot be you in the browser, cannot know your password, and should not. What you did instead was hand it a **credential**: from now on, when Claude runs a GitHub command in this folder, GitHub answers as though you ran it.

Notice what that actually means. You did not make the AI smarter. You extended what its harness can reach — from a folder on this machine to your account on the internet. Same move as Session 8, one level out.

</details>

---

## Part 2 — Bring your website down and open it

Your site exists on GitHub. It does not exist on this machine. Open the Claude Code panel and ask:

```
Clone my {username}.github.io repository onto my Desktop.
```

**Watch what it does.** It has to work out your username before it can know the repository name, then run the clone. Approve the commands as it asks. It can only do this because of Part 1.

When it finishes, a folder named `yourusername.github.io` appears on your Desktop with your `index.html` inside it.

### Now open that folder

1. **File → Open Folder**
2. Choose `yourusername.github.io` **on your Desktop**
3. Click **Open**

The window reloads. Claude Code starts over and asks whether you trust this folder. Say yes.

---

## Part 3 — Install a skill you did not write

Send this to Claude Code as one message:

```
Clone `gh repo clone jmathai/mgmt-342-dotclaude` into this repository so that its github-pages folder ends up at .claude/skills/github-pages — not wrapped inside the repository's own folder. Then add .claude/skills/github-pages/ to my .gitignore.
```

When it says it is done, open your way down through the Explorer. **You are checking for exactly this:**

```
.claude/
  skills/
    github-pages/
      SKILL.md
      reference/
```

### Check it took

Ask Claude Code:

```
What skills do you have available?
```

**If `github-pages` is not in the list, close the Claude Code session and start a new one, then ask again.** It will be there.

**Skills are read once, when a session starts.** Yours started back in Part 2, before `.claude/skills` existed, and nothing has told it to go look again.

> **Restarting the session is how you reload the folder.** When something you added is being ignored, this is the first thing to try, and it is right most of the time. You will need it twice more today.

---

## Part 4 — Publish your site by asking

Setup is over. Here is what it bought you.

Ask for a change. Replace the bracket with something true about you:

```
Add a page about [SOMETHING YOU CARE ABOUT — a sport, a job, a band, a place] and link to it from my homepage.
```

Look at the page it made. Ask for changes until you like it — you are the editor here, not the audience.

Then publish it:

```
Publish my site.
```

And once it says it is done:

```
Is my site live?
```

**Open your site in a new tab and refresh.** Your new page is on the internet.

### Compare it to Session 6

You did this exact job by hand two weeks ago.

| | Session 6, by hand | Just now |
|---|---|---|
| Save the file | Notepad, get the extension right | — |
| Get it to GitHub | Add file → Upload → drag → Commit | — |
| Publish it | Settings → Pages → wait | — |
| Confirm it worked | Actions tab, watch for the green check | — |
| What you did | ~14 clicks across 5 screens | typed one sentence |

<details><summary>So was the clicking in Session 6 a waste of time?</summary>

You just told a machine "publish my site" and it did four things you never named: saved the change, sent it to GitHub, waited for the build, and checked whether the live site actually reflected it.

**You only know those four things happened because you did them yourself two weeks ago.**

That is the difference between using a tool and being able to answer for it. When it fails — and this semester, it will — the person who clicked through it once can say "the build failed" or "it never pushed." The person who has only ever typed the sentence can only say "it didn't work."

</details>

---

## Part 5 — `CLAUDE.md`, the instructions that are always on

Start with the easy one. A file called `CLAUDE.md` at the top of your folder gets read **every time a session starts**, no matter what you ask. Standing orders for this folder.

Ask for one:

```
Create a CLAUDE.md for this folder. Interview me about my site and how I want it written before you write anything.
```

Answer its questions. Then **open `CLAUDE.md` in the editor and read what it wrote about you.** Some of it will be wrong. Fix it.

### Now add a rule it did not think of

Type a line yourself, in plain English — a rule you want followed every time. Real ones:

- *Never change my homepage headline without asking me first.*
- *Every page gets a link back to the homepage.*
- *Keep every page to one screen. No walls of text.*

Save the file. **Restart Claude Code, if needed.** Then ask for something that bumps into your rule and watch whether it holds.

> **You just wrote context.** No code, no install — a sentence in a file, in a folder, that changes how an agent behaves. That is the whole trick, and Part 6 is the same trick with one more moving part.

---

## Part 6 — Take a skill apart, then write your own

`CLAUDE.md` is always on. A skill is the other kind: instructions that sit quietly until the request matches them.

### First, read the one you have been using

Open `.claude/skills/github-pages/SKILL.md` in the editor. Actually open it. Scroll it.

**It is a markdown file. English sentences. No code, nothing installed, nothing compiled.** Rules like *"Act, don't instruct"* and *"Say saved and published, not committed and pushed."* Somewhere in there is the line that made it behave the way it did in Part 4.

Now look at the very top, between the `---` lines. Two fields: `name`, and a very long `description`.

<details><summary>Why is the description so much longer than the instructions it describes?</summary>

Because **the description is the only part that decides whether the skill runs at all.**

The agent does not read every skill's instructions before every message — that would be enormous. It reads the descriptions, matches them against what you said, and loads the body of the one that fits.

That is why the description is stuffed with phrasings — *"publish my site," "put it online," "make it live," "did it work?"* Whoever wrote it was guessing at every way a person might ask, because a phrasing that is missing is a skill that never fires.

**A perfect skill with a vague description does nothing.** Remember that in about five minutes.

</details>

### Get a tool for writing skills

There is an official plugin (or skill) whose whole job is helping you write these. Type this into Claude Code:

```
/plugin install skill-creator@claude-plugins-official
```

Then restart Claude Code, if needed.

**If that does not work, type `/plugin` on its own** and find `skill-creator` in the list. **If it is not there either, skip it entirely** — Claude can write a skill without it, and nothing below depends on having it.

### Pick your own routine

> **A skill is a routine you only have to explain once.**

You just wrote standing rules in `CLAUDE.md`. A skill is the other shape. Think about your own site and your own work, and look for something that is a **skill** and not another `CLAUDE.md` line:

1. **It is a job, not a preference.** *"Keep every page to one screen"* is a preference — one line in `CLAUDE.md`, done. A skill is a job with steps: do this, then this, then check that it worked.
2. **You only want it sometimes.** `CLAUDE.md` gets read on every message whether it matters or not. A skill stays out of the way until you ask for the job.
3. **One line will not cover it.** If explaining it properly takes a paragraph and an example of getting it wrong, it is too big to live in `CLAUDE.md` — it would be taxing every unrelated thing you ask.

And under all three: **you have to care how it comes out.** If you do not, the agent's default is already fine and neither a rule nor a skill earns its place.

<details><summary>Nothing came to mind — give me a starting point</summary>

Pick one and make it yours. Do not write it as-is; every one of these gets better the moment you have an opinion about it.

- **Add a page.** A new page on your site that matches the ones you already have — your headings, your nav, your footer, linked from the homepage, in your voice.
- **Check my site.** Every link works, every page has a way back to the homepage, nothing 404s, nothing is orphaned.
- **Proofread.** Read every page and flag typos, broken sentences, and places where the writing stops sounding like you.
- **Session notes.** Every build session you turn in a plain-text log — what you built, what broke, what's next. A skill that interviews you and writes it.

</details>

### Write it

**You write the instructions. Claude writes the file.** Adapt this, then answer its questions properly — your answers *are* the skill:

```
I want to write a skill for this folder.

Here is the job it should do: [DESCRIBE YOUR ROUTINE IN TWO OR THREE SENTENCES]

Interview me first. Ask me questions until you know how I want this done, what a bad result looks like, and every way I might ask for it. Then write the skill and show me what you wrote.
```

Things worth telling it when it asks:

- What does a **bad** result look like? Be specific — the bad example teaches more than the good one.
- How do you **ask for it**? Say it out loud three different ways and give it all three.
- What should it **never** do?

When it is done, **open the file it wrote and read it.** You are looking for two things: does the body say what you actually meant, and is the `description` full of the phrasings you would really type?

### Run it — and expect it to miss

Restart Claude Code, if needed. Then ask for the thing — using a phrase you **did not** dictate to it. Say it the way you would say it on a Tuesday when you are tired.

<details><summary>It didn't fire — it just did something generic, or asked what you meant</summary>

Good. This is the exercise.

Work the checklist, in this order:

1. **Did you restart?** The skill did not exist when the old session started. This is right most of the time — always check it first.
2. **Is the file in the right place?** Look in the Explorer with your own eyes. A skill one level too deep is invisible, with no error message.
3. **Is your phrasing in the description?** Open the file and read the `description` line. If what you typed is not in there in some form, the skill never had a chance.

Number 3 is usually it. Fix the description yourself — add the phrasing you actually used — restart, and try again.

**You just debugged a skill.** The loop is: it ignored me → restart → check the path → check the description. That is the loop for every skill you ever install or write.

</details>

Keep going until it fires on a phrase you did not plan for. **That is the finish line for today** — not a skill that exists, a skill that works when you forget exactly how you wrote it.

### Save it with everything else

Your skill is yours, so it belongs in your repository — unlike the borrowed one you ignored in Part 3.

```
Publish my site.
```

Your skill and your `CLAUDE.md` are now on GitHub. That matters more than it sounds: this is a lab machine, and next Thursday you may not be at this desk.

---

## Done early?

Some things to try.

- **Try three more phrasings** on your skill. Every one that fails is a line missing from your description.
- **Break something on purpose.** Rename `SKILL.md` to `skill.md`. Delete the `description` line. Move the skill folder one level deeper. **Knowing the failure shapes is worth more than a second working skill.**
- **Write a second skill.** You have the loop now.
- **Tighten your `CLAUDE.md`.** Cut it to five rules you would actually defend.

---

## Before you leave the room

### What you turn in

Three things. All three already exist — you are not writing anything new.

1. **Your live site URL** — `https://yourusername.github.io`. Paste it in the Canvas comment box.
2. **Your `CLAUDE.md`** — the one from Part 5, with the rule you wrote by hand still in it.
3. **Your `SKILL.md`** — the one from Part 6. Whichever routine you picked.

Both files are in your repository. Right-click each in the Explorer to find it on disk, or grab them from GitHub.

**You are turning in the instructions, not the output.** That is the point of today — what got built matters less than what you wrote down to make it get built the same way next time.

### And sign out

Shared lab computer. You handed it a credential in Part 1. Open a terminal and run:

```
gh auth logout
```

---

*MGMT 342 · Session 10 · Fall 2026 · Xavier University · Humphrey & Mathai*
