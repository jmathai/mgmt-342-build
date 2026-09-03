# Session 6 — Intro to GitHub and GitHub Pages

**Thursday, September 3 · 4:00–5:15 PM · Online · your own laptop**

**Bring:** your `index.html` file from Aug 27 (Session 4). Know where it is on your laptop before we start.

**Today is all browser, no installs.** No git, no command line, nothing to download. By 5:15 you will have a GitHub account and a real website, live at an address that is yours — `yourusername.github.io` — built entirely by clicking around a web page.

**This session is online.** If something isn't working, say so in the chat rather than waiting.

---

## What GitHub actually is

You have already used GitHub without an account — you read Session 2 and Session 4 sitting in a browser, no login. Today you get the other side of it: a place of your own to put files.

**A repository is a collection of files that GitHub keeps for you** — think a slightly more technical OneDrive. It keeps a history of every change, and because the files live on GitHub's servers instead of only your laptop, they can be turned into a website.

**A commit is a saved snapshot** — every time you change a file and save that change, GitHub keeps the version before and the version after. You are not editing in place; you are stacking snapshots, which is why nothing you do today is easy to lose.

**GitHub Pages takes a repository and serves it as a static website.** Point it at a folder of files, and whatever is in there becomes a live page on the internet, no separate hosting to pay for or configure.

**What is a static website?** It’s a website that does not change. Go to Amazon.com one signed out and signed in. It will be different. The content comes from a database and changes based user. A static website doesn’t change.

<details><summary>Why does this matter more than "free web hosting"?</summary>

Every build you do for the rest of the semester ends up here. Not just this website — starting Module 2, your entire course folder, every file, every note, every project, lives in a GitHub repository, and an AI agent works inside it the same way you're about to work inside this one by hand.

Today you learn the interface by doing the simplest possible version of it yourself: one repository, one file, one click to publish. Session 8 onward, an agent does it for you. Knowing what it's actually doing is why you're doing it manually first.

</details>

---

## Part 1 — Create your GitHub account

1. Go to **[github.com](https://github.com)**.
2. Click **Sign up**.
3. Use an email you actually check — verification goes there, and this account follows you for the rest of the course.
4. Pick a username carefully. **You cannot cleanly change it later**, and in a few minutes it becomes part of your website's address - `<yourusername>.github.io` will be your URL.
5. Verify your email.

**You should now be looking at your GitHub homepage, logged in.**

---

## Part 2 — Create your Pages repository

GitHub Pages has one naming rule that makes the setup close to automatic: name your repository exactly `<yourusername>.github.io`, and GitHub turns on Pages for it by itself.

1. Click the **+** in the top-right corner, then **New repository**.
2. Under **Repository name**, type your GitHub username followed by `.github.io` — all lowercase, exactly matching your username. If your username is `jsmith42`, the repository is named `jsmith42.github.io`.
3. Leave it set to **Public**. Pages needs a public repository on a free account.
4. Keep **Add a README file** off.
5. Click **Create repository**.

<details><summary>Why does the name have to match exactly?</summary>

GitHub reserves that exact pattern — `<username>.github.io` — as the one repository per account that becomes your personal site at the root of that address. Any other repository name still works with Pages, but it publishes to `yourusername.github.io/repository-name` instead, with the repository name tacked onto the end. Matching your username gets you the clean address with no extra setup.

</details>

**Look at what you're looking at.** A repository with no files in it.

---

## Part 3 — Upload your index.html

This is the file you built in Session 4.

1. In your new repository, click **Add file**, then **Upload files**.
2. Drag `index.html` into the box, or click **choose your files** and select it from your laptop.
3. Scroll down to **Commit changes**. Leave the default message, or write one — a sentence describing what you changed. Leave "Commit directly to the `main` branch" selected.
4. Click **Commit changes**.

**Refresh the repository page.** You should now see one file: `index.html`.

<details><summary>Lost your index.html, or it's not on this laptop?</summary>

Download [index.html](index.html) or create a new one with Copilot:

```
Ask me five questions, one at a time, that would help you write an about me page. Then write it as a single HTML file.
```

Answer its questions, then copy the HTML it gives you into a plain-text editor and save the file as `index.html`. Come back here and continue from step 1 above.

</details>

<details><summary>Why does index.html matter, specifically?</summary>

When Pages looks at your repository for something to publish, it checks for a file named exactly `index.html` at the top level and serves that as your homepage. That's the same convention behind almost every website you've ever visited — the address bar shows a domain with nothing after it, and the server is quietly filling in `index.html` for you.

`README.md` is for people reading the repository on GitHub. `index.html` is for people visiting the website. You now have both, doing two different jobs.

</details>

---

## Part 4 — Visit your live site

1. In your repository, click **Settings**, then **Pages** in the left sidebar.
2. You should see **Your site is live at** followed by an address — `https://yourusername.github.io`. If it instead says building or hasn't finished, give it a few minutes.
3. Open that address in a new tab.

**That is your website. On the internet. With your name on it.**

<details><summary>It says 404, or shows nothing</summary>

Almost always one of two things:

- **Wrong filename.** Back in your repository, confirm the file is named exactly `index.html`, not `index.html.txt` or `Index.html`. Click the filename to check — GitHub shows the exact name at the top of the file view.
- **Still building.** The first publish can take up to ten minutes. Refresh the Settings → Pages screen and check again before troubleshooting further.

</details>

---

## Part 5 — Edit it, and watch it publish

A live website isn't a one-time upload — it rebuilds every time you commit. Prove it to yourself.

1. In your repository, click on `index.html` to open it.
2. Click the **pencil icon** in the top-right of the file view — this is GitHub's built-in editor, no download required.
3. Find a sentence and change it. Anything small and easy to spot.
4. Scroll down to **Commit changes**, leave "Commit directly to the `main` branch" selected, and click **Commit changes**.
5. Click the **Actions** tab at the top of the repository.
6. You'll see a workflow run — a yellow dot while it's running, a green check when it's done. That's Pages rebuilding your site from the file you just committed.
7. Once it's green, go back to your live site and **refresh the page** to see your change.

<details><summary>What is Actions, actually?</summary>

Every commit to `main` doesn't just save a snapshot — on a repository named `<username>.github.io`, it also kicks off a small automated job that rebuilds the site and republishes it. **Actions** is where GitHub shows you those jobs running: what triggered it, whether it's still going, and whether it succeeded or failed.

You didn't set any of this up — it came free with the naming convention from Part 2. But it's worth seeing once, because this is the same idea behind almost everything an agent does starting Session 7: change a file, commit, and something automated reacts. Today the "something" is GitHub's own publishing job. Soon it's Claude, watching for the same trigger.

</details>

**Send the link to yourself** — text it, email it, whatever you'll actually open again. You'll want it on Sep 8.

---

## Before you leave the room

**Your participation file.** Every class ends with one file, worth 4 points.

1. Write a plain-text file named `session-06.txt`. Build session, so it is a build log: **what you built, what broke, what's next.** Your own words, no formatting. **Include the URL of your live site** — `https://yourusername.github.io` — as its own line.
2. **Upload it to Canvas.**
3. **Keep a copy on your laptop** — your course folder repository doesn't exist yet, so today is still a Canvas day. Session 8 onward, your notes join the repository instead.

**What's next.** Sep 8 you use this account and a computer in the lab for the first time. You'll set up VS Code and an AI agent, hand it access to the account you made today, and it will take over the parts you just did by hand — committing, and pushing — for the rest of the semester.

---

*MGMT 342 · Session 6 · Fall 2026 · Xavier University · Humphrey & Mathai*
