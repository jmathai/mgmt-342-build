# Session 25 — Motion graphics with Claude Opus 5.5

**Thursday, November 12 · 4:00–5:15 PM · CFI · lab machine**

---

Your Module 4 business case needs AI media. A short motion graphic is one of the fastest ways to get it: a 30 to 60 second animated video for your app, made entirely using Claude.

---

## Set your model to Opus 5.5

In the Claude Code panel, type:

```
/model
```

Pick **Opus 5.5** from the list and press Enter. Then check it took:

```
Which model are you?
```

It should say Opus 5.5. If it says anything else, run `/model` again.

**Start a new session for each video.** Motion work uses a lot of context. A fresh session per video keeps the agent focused and keeps it from mixing up two projects.

---

## How Claude makes a video

Claude does not have a video editor. It writes a web page that animates, then turns that page into a video file.

1. **It writes one HTML file.** Shapes, text, images and timing, all in code. You open it in a browser and watch it play.
2. **Every frame is computed from the time.** The page has a function that answers "what does the screen look like at 3.2 seconds?" This is what lets it be turned into a video exactly, frame by frame.
3. **It renders the frames to an MP4.** A tool called Playwright opens the page, steps through time, and saves each frame. A tool called ffmpeg stitches the frames together and adds the sound.

If Playwright or ffmpeg will not install on the lab machine, you still have the HTML file. Play it full screen and record it with the Snipping Tool (**Windows + Shift + R**). The quality is lower, but it works.

You do not need to understand the code. You do need to describe what you want precisely, and look at what comes back.

---

## Where the examples come from

[prompt-motion.com](https://prompt-motion.com) collects motion videos made with Opus 5.5, with the prompt used for each one. Open it and watch five or six before you write anything. Each video and prompt belongs to its creator, who is linked on the entry.

The prompts there fall into two groups.

### Short prompts

A sentence or two. Claude makes nearly every decision.

An example prompt on the site.

```
make a dynamic 15-second motion graphics video that shows what an incredible
motion designer you are, like it's your showreel for a résumé. go all out.
```

— [@stephanlivera](https://prompt-motion.com/stephanlivera-df17a2). Compare it with [@shneural](https://prompt-motion.com/shneural-2abdfa), [@ajith_io](https://prompt-motion.com/ajith-io-b5626e) and [@himanshutwtxs](https://prompt-motion.com/himanshutwtxs-5f4b43). Same words, very different videos.

An explainer, written conversationally:

```
We're going to try a little test. Do you think you could render a recipe
motion graphic animation using javascript or html (w/e you think will produce
the best) to show the full recipe from start to finish (empty glass to
completed cocktail) - Explainer video style - Showing the recipe ingredients +
measurements as they're going into the cup. Should be a 30s video.
```

— [@Ror_Fly](https://prompt-motion.com/ror-fly-9950f1), a Negroni recipe. This is the closest example on the site to a "how the app works" video.

A short prompt with a reference video attached:

```
Make a fast-paced ad for Claude, about 10–15 s (closer to 15). Reference video
attached.
1. research: - Study Claude's earlier brand designs first. - Find every photo
and asset that fits: artistic, editorial, whatever the idea needs.
2. design/direction - An art reimagine: bold, light mode. - Clean and perfect:
no beige "artsy" look, no eyebrow labels. - Paint elements on top of the
images. - Above all: fast-paced and very creative.
3. rules - No slop. Study the reference closely: smoothness, timing, shot
durations, fonts, elements. - Take some inspiration and borrow techniques,
but change the design overall, it should look like something you did
completely on yourself with your own taste - Every morph has to be perfect.
ideas: (since everything moves fast) - Clean, varied Claude SVG animations -
Images small, bigger, several at once - Morphing text - Clean 3D animation -
Zooms
extra notes: - Feel free to work 10+ hours - Give me the final video, ending on the Claude logo.
```

— [@LexnLin](https://prompt-motion.com/lexnlin-038035). The reference video does a lot of the work. Five seconds of an ad you like tells Claude more about pacing than a paragraph does.

**Short prompts are good for seeing what is possible.** They are bad for getting a video about your app, because Claude fills every gap with its own idea.

### Long prompts

Several hundred to several thousand words. These are the ones whose videos look professional. Open them on the site and read them in full:

- [Shape morphing through UI states](https://prompt-motion.com/twoclipping-5cba86) by @twoclipping. One shape becomes a button, a loader, a music player, a slider, a chart, on a 120 BPM beat.
- [Photo print app launch film](https://prompt-motion.com/twoclipping-221cab) by @twoclipping. An Apple-keynote-style app launch in one continuous shot.
- [Landing page 3D fly-over](https://prompt-motion.com/twoclipping-d89be5) by @twoclipping. A camera glides down a real landing page laid flat on a studio floor.
- [Launch video remake](https://prompt-motion.com/notdwd-c2037d) by @notdwd. A 12-second product sting, specified frame by frame.

They all use the same sections, in tags:

| Section | What goes in it |
|---|---|
| `<inputs>` | What Claude should ask you for before it starts: your logo, colors, photos, a song. |
| `<direction>` | The look. Canvas color, fonts, how things move, and a **Banned** list. |
| `<structure>` | The timeline. What happens at each second or each beat. |
| `<build>` | How to make it: one HTML file, size, frame rate, how to render. |
| `<gotchas>` | Mistakes to avoid that the author learned the hard way. |
| `<start>` | What Claude does first. Almost always: ask for inputs, then show stills before rendering. |

---

## What the good prompts have in common

These show up again and again in the videos that look best. Use them in your own prompts.

- **A length and a size.** "15 seconds, square 1440x1440, 60fps." Square works on a phone and on a slide.
- **A timeline.** What happens from 0 to 2 seconds, 2 to 5, and so on. Without one, Claude spreads things out evenly and the video drags.
- **One continuous take.** "Every scene is made out of the previous one: nothing fades or cuts." Shapes turning into other shapes looks far better than slides fading in and out.
- **A short visual vocabulary.** One background color, one or two fonts by name, one accent color.
- **A Banned list.** "Banned: crossfades, glows, particle bursts, bouncy easing, anything that looks like a template." This is the single biggest improvement you can make to a prompt. Claude's defaults are what make AI video look like AI video.
- **A cursor that does the work.** For an app, a cursor clicking and dragging through the screens shows what the app does without any narration.
- **Stills before the full render.** "Show me stills at 0, 3, 7 and 12 seconds before you render." You catch the bad idea in one minute instead of ten.
- **Real sound, not synthesized.** Free music and sound effects from [Mixkit](https://mixkit.co) or [Pixabay](https://pixabay.com/music/). Ask Claude to line up the cuts with the beat.
- **A loop, if it repeats.** "The last frame is the first frame." Good for a web page hero or a social post.

---

## Prompts for your app

Every prompt here reads one file: `ad-script.md`, the commercial you wrote for Session 24. The scene table is already a timeline, which is the part most prompts are missing. If your scene table is thin, fix it before you send anything. Replace every `[SQUARE BRACKET]` before you send.

Put each video in its own folder inside `module4-app/`, for example `module4-app/media/ad/`.

### 1. The quick version

Send this first. It is the short-prompt approach: Claude makes most of the decisions.

```
Read ad-script.md. Make it as a motion graphic. Show me a still from each
scene before you render the video.
```

Watch what Claude decides for you: the colors, the fonts, how things move. Keep what you like and put it in prompt 2. Ban what you do not like.

### 2. The full commercial (30–60 seconds)

The long-prompt approach, built from the same sections as the prompt-motion.com examples.

```
<inputs>
Read ad-script.md. Then ask me for: my app name, a logo (or offer to draw a
simple mark), two brand colors, and a royalty-free song from Mixkit that
matches the tone in the script. If I skip any, pick defaults and tell me
what you picked.
</inputs>

<direction>
A motion graphic of my commercial, square 1080x1080 at 60fps. Match the tone
in ad-script.md. Off-white canvas, my two brand colors, one font (Inter).
One continuous take: every scene grows out of the previous one. Where a
scene shows the app, a cursor drives it with real clicks.
Banned: crossfades, glows, particle bursts, bouncy easing, stock UI kits,
text longer than six words on screen, anything that looks like a template.
</direction>

<structure>
Follow the scene table in ad-script.md exactly. Use the Seconds column for
timing. The On screen column is what must be shown. The Voice or text column
becomes on-screen text (no voiceover). The Sound column tells you where the
music and sound effects hit. Line up every scene change with a beat.
</structure>

<build>
One HTML file. Every style is computed from time inside seek(t): no CSS
transitions, no timers. Render with Playwright and ffmpeg to an H.264 MP4
with the music. Put everything in media/ad/.
</build>

<gotchas>
Measure text only after the fonts load. If my app name is long, scale it to
fit rather than letting it run off the frame. If Playwright or ffmpeg will
not install, tell me straight away and give me the HTML file to play full
screen.
</gotchas>

<start>
Ask me for the inputs. Tell me which scenes you cannot show well with shapes
and text alone, and what you would do instead. Then show me one still per
scene before you render the full video.
</start>
```

Compare it with what prompt 1 gave you. The difference is what the extra detail bought.

### 3. The 12-second cut

A short version of the same ad, for the top of your web page or a social post.

```
Read ad-script.md and the video in media/ad/. Make a 12 second cut of it:
the hook, the moment the app solves the problem, and the closing line.
Same look, same colors, same fonts. Keep the music on the beat.
The last frame is the first frame, so it loops.
Show me stills at 1, 5, 9 and 12 seconds, then render to media/ad-short/.
```

### 4. The showreel, for fun

Send the original showreel prompt from the top of this page, unchanged. Then compare yours with the person next to you. Same prompt, same model. Why are they different?

---

## Fixing what comes back

The first render is a draft. These follow-ups fix the most common problems:

| What you see | Send this |
|---|---|
| It drags | `Cut the total length by a third. Nothing holds still longer than one second.` |
| It looks like a template | `Add these to the Banned list: [WHAT LOOKS CHEAP]. Rebuild the scenes that used them.` |
| Text is hard to read | `Every piece of text stays on screen at least 1.2 seconds and is at least 48px. Fix any that are not.` |
| Things overlap or pop | `Render one still every half second and check each for overlapping text or a shape that jumps between frames. Fix them.` |
| Cuts miss the music | `Analyze the song for its beat grid and move every cut onto a beat.` |
| One scene is wrong | `Change only [SECONDS] to [WHAT YOU WANT]. Do not touch anything else.` |

Ask for one change at a time. If you ask for six, you will get four of them and two new problems.

**Look at the stills.** Claude cannot watch the video the way you do. It can only check what you tell it to check.

---

## Done early?

- **Write your own long prompt.** Pick a video on [prompt-motion.com](https://prompt-motion.com) you like, read its prompt, and write one for your app using the same sections.
- **Make a loop** of your logo for the top of your web page. Add "The last frame is the first frame" to the prompt.
- **Ask Claude how many tokens the video took.** Motion work is expensive. Is a 30 second video worth it, or does a 10 second one do the job?

---

*MGMT 342 · Session 25 · Fall 2026 · Xavier University · Humphrey & Mathai*
