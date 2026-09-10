# Session 8 — VS Code, Claude Code, and your first Skill

**Thursday, September 10 · 4:00–5:15 PM · CFI · lab machine**

**Bring these:**
- Your **GitHub username and password.** You are signing in on a machine that is not yours. If you use two-factor, bring the phone.
- The **link to your live site** — `https://yourusername.github.io`.

**Tuesday you opened Claude in VS Code and poked at it.** Today it does real work. By 5:15 you will have changed your live website by asking for the change in a sentence, and published it without opening github.com once.

---

## Three new things today

| | What it is | What it replaces |
|---|---|---|
| **VS Code** | A window with a file browser on one side and an AI on the other | Copilot in a browser tab |
| **Claude Code** | An AI that can actually reach the files and run commands | Copy/paste from Copilot into TextEdit |
| **A Skill** | A folder of instructions that changes how the AI behaves | Using the GitHub website |

They stack in that order. Work down the page.

---

## Part 1 — VS Code, and why you are not using most of it

VS Code is built for people who write code for a living. You are not doing that. **Treat it as a glorified Windows Explorer with an AI bolted onto the side.**

Three areas matter today:

- **The Explorer**, down the left. A file browser — the folders and files you are working on. **This is the part you actually use.**
- **The editor**, the big area in the middle. Shows the contents of whatever file you click. You barely touch it today.
- **The panel**, bottom or right. This holds the **terminal** and **Claude Code**. This is where you spend the session.

### The one thing you have to get right: the open folder

**File → Open Folder** is how you tell VS Code what you are working on. Everything else follows from it — what the Explorer lists, where the terminal starts, and, most importantly today, **what the AI can see.**

### Open a folder — deliberately the wrong one

1. **File → Open Folder**
2. Choose your **Desktop**
3. Click **Open**

The Explorer on the left now shows whatever is sitting on your Desktop.

**This is the wrong folder, on purpose.** Hold that thought for two minutes.

---

## Part 2 — Claude Code is a different harness, not a smarter model

Think back to Session 4. Copilot wrote you a perfectly good HTML file and then handed it to you as text in a chat box, and you copied it into Notepad yourself. On my screen, the file just appeared.

> **That gap was never about which model was smarter. It is about what the tool is allowed to reach.**

The thing wrapped around the model — the part that decides whether it gets to open a file, write a file, or run a command — is the **harness**. Copilot's harness reaches a browser. **Claude Code's harness reaches this computer.**

Same family of model. Radically different job, because of what it is permitted to do.

### Open Claude Code

Open the Claude Code panel.

**The first time it starts in a folder it has never seen, it asks whether you trust the files in it.** Say yes — this is your Desktop on a lab machine. But read what it is asking, because it is asking the question this whole session is about: *am I allowed to work in here?* You are granting it access to a folder, and it will not touch anything until you do.

Now send:

```
What files are in this folder?
```

<details><summary>Predict before you send it: how does it answer?</summary>

It lists what is on your Desktop.

Two things worth catching, and the second is the one that matters.

**It went and looked.** No paperclip, no upload, no pasting. In Session 4 you spent an entire round of class handing a chat box a document; here, reading the folder is just something the tool does. That is the harness.

**And it can see all of it.** Everything on that Desktop is inside its reach right now, because that is the folder you opened. Nothing went wrong — but notice that you decided it, in three clicks, without thinking about it.

**The open folder is the boundary.** That is why Part 1 said this one was wrong on purpose.

</details>

---

## Part 3 — Sign in to GitHub (Claude can’t do this for you)

Install the GitHub command line by following these instructions in VSCode.
1. Go to Terminal > New Terminal
2. Copy and paste the following and type `Y` when prompted and then `Enter`.

```
winget install --id GitHub.cli
```

Your work lives in a GitHub repository. You need to give Claude access to your GitHub account.

`gh` is GitHub's command-line tool — the same GitHub you clicked through in Session 6, minus the web page. It is already installed on this machine.

1. Open the **terminal** in VS Code: **Terminal → New Terminal**
2. Type this and press Enter:

```
gh auth login
```

3. It asks four questions. Arrow keys to choose, Enter to confirm:

| It asks | You pick |
|---|---|
| Where do you use GitHub? | **GitHub.com** |
| Preferred protocol for Git operations? | **HTTPS** |
| Authenticate Git with your GitHub credentials? | **Yes** |
| How would you like to authenticate GitHub CLI? | **Login with a web browser** |

4. It prints a **one-time code** like `7C8C-E763`. Copy it, then press Enter — a browser opens.
5. Paste the code, sign in, click **Authorize**.
6. Back in VS Code, it confirms you are logged in.

**Check it worked.** Two commands in the terminal — the first one only has to be run once, ever:

```
gh config set pager cat
```

```
gh api user --jq .login
```

It should print your GitHub username back at you. If it does, this machine can now act as you on GitHub.

<details><summary>What was that first command for?</summary>

Out of the box, `gh` hands its output to a **pager** — a scrolling viewer that takes over the terminal and does not give it back until you press `q`. That is genuinely useful for a hundred lines of output. For one word it just looks like the terminal has frozen.

`gh config set pager cat` tells it to print straight to the screen instead. You run it once and every `gh` command behaves normally from then on.

**If you ever do end up stuck in a screen you cannot type into: press `q`.** That is worth remembering on its own — plenty of terminal programs do this.

</details>

<details><summary>Why did you have to do this yourself instead of asking Claude?</summary>

Because it is a login, and a login is the one place where "the AI does it for you" has to stop.

Claude can run `gh auth login` — it just cannot be you in the browser, cannot know your password, and should not. What you did instead was hand it a **credential**: from now on, when Claude runs a GitHub command in this folder, GitHub answers as though you ran it.

Notice what that actually means. You did not make the AI smarter. You extended what its harness can reach — from a folder on this machine, to your account on the internet. That is the same move as Part 2, one level out.

</details>

---

## Part 4 — Bring your website down and open it

Your site exists on GitHub. It does not exist here. Ask Claude Code:

```
Clone my {username}.github.io repository onto my Desktop.
```

**Watch what it does.** It has to work out your username before it can know the repository name, then run the clone. Approve the commands as it asks.

When it finishes, a new folder — `yourusername.github.io` — appears in the Explorer with your `index.html` inside it.

### Now open a different folder

The Desktop is still the open folder. Move to the website itself.

1. **File → Open Folder**
2. Choose `yourusername.github.io` on your Desktop
3. Click **Open**

The window reloads. The Explorer now shows `index.html` at the top level, with nothing above it. Claude Code starts over and asks whether you trust this folder — same question as Part 2, new folder. Say yes.

### Ask it the same question again

```
What files are in this folder?
```

<details><summary>Predict first: how is the answer different?</summary>

**Your Desktop is gone.** It lists your website — `index.html`, and whatever else you published — and nothing else. Your other files did not move and nothing was deleted. They are simply outside now.

Same computer, same model, same question, two answers ten seconds apart. **The only thing that changed is which folder you opened.**

That is the whole idea, demonstrated twice. In Part 2 the boundary was wide and you set it without thinking. Here you set it on purpose, and it is exactly the project you are working on.

</details>

**Your website is the open folder now.** That is where you work for the rest of the session.

<details><summary>Why bother? It was already visible in the Explorer.</summary>

Being visible is not the same as being the folder. From the Desktop you could *see* the website in the file tree — but "this folder" meant the Desktop, so that is what Claude read.

That matters immediately. In Part 5 you install a set of instructions that applies to *this website specifically*, and it has to sit inside the website's folder for the agent to find it. From the Desktop, "inside the folder" would have put it in the wrong place.

**Open Folder is the most important menu item in this program.** It is not a convenience — it is the decision about what the agent is working on. Get it wrong and nothing else in the session works.

</details>

**One thing to notice:** opening a different folder restarted your Claude Code conversation. It came back empty. Remember that it did — it matters in Part 6.

---

## Part 5 — Install a Skill

Everything so far has been about **reach**. This part is about **instructions**.

Send this to Claude Code as one message:

```
Create a .claude/skills folder and add .claude to my .gitignore. Then clone this repository into .claude/skills: `gh repo clone jmathai/mgmt-342-dotclaude`
```

When it is done, look in the Explorer. You should be able to open your way down to:

```
.claude/
  skills/
    github-pages/
      SKILL.md
      reference/
```

<details><summary>What is a Skill?</summary>

**It is a folder with a markdown file in it — instructions written in English. No code, nothing installed.**

It is context. The same context engineering you did in Session 4, except written down once in the folder instead of retyped into every message.

That is as far as we go today. **We take skills apart properly next session**, when you write one.

</details>

<details><summary>Why add .claude to .gitignore?</summary>

Two reasons, and the second is the real one.

The small reason: this repository is a live website. Files in it get published. The skill is not part of your website.

The bigger reason: **`.gitignore` is you deciding what belongs to the project and what is just how you happen to work.** The skill is tooling — it shapes how *you* build the site, and it does not belong to the site any more than VS Code does. That distinction is going to come up in every repository you touch from here on.

</details>

---

## Part 6 — Nothing has changed yet. Find out why.

Before you restart anything, ask Claude Code — in the **same** conversation you have been using:

```
What skills do you have available?
```

<details><summary>Predict first: does it know about the skill you just installed?</summary>

**No.** It will tell you it has none, or list something that is not the one you just cloned.

The folder is on disk. You can see it in the Explorer. Claude cannot.

**Skills are read once, when a session starts.** This session started back in Part 4, the moment you opened your website folder — and `.claude/skills` did not exist yet. It has been running ever since, and nothing has told it to go look again.

This is the Session 4 idea — *a model does not remember, it re-reads* — moved up one level. Everything the agent knows about this folder was assembled at the instant the session began. Change the folder mid-conversation and the conversation never finds out.

</details>

### Restart the session

Close the Claude Code session and start a new one. Then ask the same question again:

```
What skills do you have available?
```

**Now it knows.** Same folder, same computer, same model, same question — a different answer, because a new session read the folder fresh.

> **Restarting the session is how you reload the folder.** Remember this. When something you added is being ignored, this is the first thing to try, and it is right most of the time.

---

## Part 7 — Change your site and publish it

The whole session has been setup. Here is the payoff.

Ask for a change. Replace the bracket with something true about you:

```
Add a page about [SOMETHING YOU CARE ABOUT — a sport, a job, a band, a place] and link to it from my homepage.
```

> **Keep this prompt.** The prompt you actually send is what you turn in today, so if you reword it, write down the version you sent.

Look at the page it made. Ask for changes until you like it — you are the editor here, not the audience. Every follow-up you send is part of the prompt you turn in, so keep those too.

Then publish it:

```
Publish my site.
```

Then, once it says it is done:

```
Is my site live?
```

**Open your site and refresh.** Your new page is on the internet.

### Compare it to Session 6

You did this same job by hand a week ago.

| | Session 6, by hand | Session 8, with the skill |
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

## Part 8 — Optional: leave the agent a note

**Only if you have time.** If class is nearly over, skip to the checklist below — this is not required today.

A skill is one way to put context in a folder. Here is the other, and it is simpler: a file called `CLAUDE.md` at the top of your folder, which Claude reads every time it starts.

Ask for one:

```
Create a CLAUDE.md for this folder. Ask me questions about my site and how I want it written before you write it.
```

Answer its questions. Then open `CLAUDE.md` in the Explorer and read what it wrote about you.

Add a line yourself — a rule you want followed every time, in plain English. Something like *"Never change my homepage headline without asking"* or *"Keep every page to one screen."*

Then restart Claude Code — you know why by now — and ask for a change that bumps into your rule.

<details><summary>What is this actually for?</summary>

A skill is context that shows up **when it is relevant**. `CLAUDE.md` is context that is **always there** — the standing instructions for this folder, loaded at the start of every session.

Between them, that is most of what the rest of this course is: deciding what an agent should always know, what it should know only sometimes, and writing both down where it will find them.

</details>

---

## Before you leave the room

### What you turn in

Two things, in a plain-text file named `session-08.txt`, uploaded to Canvas:

1. **The prompt you used** to add your second page — the exact wording you sent, plus any follow-ups you sent to fix it up.
2. **Your live site URL** — `https://yourusername.github.io`, on its own line.

### Check it before you submit

Professor Humphrey opens that URL and expects a working website with a second page on it. Make sure that is what loads.

1. Open your site URL in a **private / incognito window**. This matters — it shows you the published site rather than a cached copy or a local file that only exists on this machine.
2. The homepage loads.
3. **The link to your second page is on the homepage, and clicking it works.** This is the one that breaks. A page that exists but is not linked is a page nobody finds.
4. The second page renders — text, not raw HTML, not a 404.

If any of those fail, fix it now. Ask Claude:

```
My second page isn't showing up on my live site. Find out why and fix it.
```

There are two of us in the room right now. There will not be on Sunday night.

### And before you walk away from this machine

**Sign out of GitHub.** This is a shared lab computer and you handed it a credential in Part 3. In the terminal:

```
gh auth logout
```

---

*MGMT 342 · Session 8 · Fall 2026 · Xavier University · Humphrey & Mathai*
