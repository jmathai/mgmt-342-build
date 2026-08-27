# Session 4 — Context engineering

**Thursday, August 27 · 4:00–5:15 PM · CFI · your own laptop**

**By the end of class you will have:** an `index.html` file on your laptop that opens in a browser and is your About Me website. The actual file, not a draft of one.

**Bring:** your About Me text from Aug 20, and one document about you — a resume, a paper you wrote, a transcript, an application essay, a club bio, a LinkedIn PDF. One is enough.

**Two screens today.** You work in Copilot. I run the same session beside you in **Claude Code** — a tool you do not have yet and get on Sep 8. Watch what it does differently at each round. That difference is the lesson.

---

## Intro

**A model does not remember you. It re-reads.** Nothing persists inside it between messages. On your fifth message the entire conversation — all four earlier turns, both halves, plus anything attached — is sent again from the top, in one block. It answers. It forgets. Every turn is a cold read.

**Four things fill that window. Only one of them is you typing.**

| Row | What goes in | Where it comes from | Round |
|---|---|---|---|
| 1 | The system prompt | What you don’t see or control | n/a |
| 2 | Your conversation and memories | Earlier turns, saved memory | n/a |
| 3 | Your prompt | You, typing | Round 1 |
| 4 | Material you hand over documents | Files you attach | Round 2 |
| 5 | Material it goes and gets | RAG, links, fetched by the tool | Round 3 |

Jarrod will talk about RAG in an upcoming session.

> **Prompt engineering is row 2. Context engineering is deciding what occupies the rest.**

Today you fill them one at a time and watch the page get better. Pay attention to how different your experience is than mine.

---

## Round 1 — A basic prompt

Open Copilot. **New conversation.**


Copy and paste this prompt.
```
Create an about me page that is a single HTML file.
```

### Round 1 — Watch my screen

<details><summary>What do you notice that was different?</summary>
* No code block appeared.
  I did not have to copy/paste.

Why?

Copilot cannot do that. It can hand you text; it cannot touch your computer. **That gap is not about which model is smarter. It is about what the tool is allowed to reach.**
</details>

Leave that file open in a browser tab. You will reload it later.

---

## Round 2 — Hand it a document

Same conversation.

Attach your file with the paperclip or **+**, and send:

<details><summary>Lost your Aug 20 text?</summary>
Send the following prompt, answer them, copy the whole block, save it to a file.

```
Ask me five questions, one at a time, that would help you write an ‘about me’ file.
```

**Windows** — Start → type `Notepad` → Enter. Paste. File → Save As. Change **Save as type** to **All Files (\*.\*)**. Name it `index.html`, save to Desktop.

**Mac** — Command+Space → type `TextEdit` → Enter. Format → **Make Plain Text**, *before* you paste. Paste. File → Save, name it `index.html`, save to Desktop.

**Double-click it. It should open in your browser as a web page.**
</details>

<details><summary>Have a LinkedIn profile?</summary>
You can download a PDF resume.

1. Click the profile icon.
2. Click View Profile.
3. Click the More (3 dots).
4. Click Save to PDF.
</details>

```
Update the about me HTML to include information about me.
```

<details><summary>It opened as code, or in the wrong program</summary>

Wrong name — almost always `index.html.txt`.

Windows: File Explorer → View → tick **File name extensions**, then rename.
Mac: click the file once, press Enter, fix the name.

**A file's extension is just the end of its name, and it tells your computer which program opens it.** `index.html` and `index.html.txt` hold identical text. One is a web page, one is a note.

</details>

**Compare it to Round 1.**

### Round 2 — Watch my screen


<details><summary>What do you notice that was different?</summary>

  * I did not have to attach a file.

Why?
</details>

---

## Round 3 — Provide context as a reference

Let’s make this visual. Find a website’s aesthetic you like and tell Copilot to make it look like that.

```
Make it look like redbull.com
```

If time permits, continue customizing the file. We’ll use it as a starting point in the next session.

Save this file and turn it in.

### Round 3 — Watch my screen

<details><summary>What do you notice that was different?</summary>

  * Not too much different.

Why?
</details>

Let’s do a verification.

```
How did you find out what redbull.com looks like?
```

**Do the verification** open up https://redbull.com and compare.

---

## A real world example

Download the [sales.csv](sales.csv) file.

**New conversation.** Attach the csv file.

Ask about the product which generated the most total sales by value.

```
Which product generated the most total sales?
```

```
I would like to see a pie chart by revenue and product name.
```

### Round 3 — Watch my screen

<details><summary>What do you notice that was different?</summary>

  * It knew my name.
  * It knew my store’s name.
  * It responded to specific questions concisely.

Why?
</details>

---

## Let’s create a game

We will try and create a Pacman game by giving Copilot a reference.

What reference? A code repository in GitHub.

```
I want you to create a single html file with a pacman game using https://github.com/bward2/pacman-js
```

### Watch my screen

<details><summary>What could be different?</summary>

  * What if I didn’t limit it to one file?
</details>

## Before you leave the room

**Keep `index.html` where you can find it.** Desktop is fine. Sep 8 you bring it to a lab machine and put it on the internet.

---

*MGMT 342 · Session 4 · Fall 2026 · Xavier University · Humphrey & Mathai*
