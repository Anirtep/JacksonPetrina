# Jackson Petrina — AI Agent Workspace

This is the brain behind Jackson's Claude sessions. Every time you open Claude and point it at this folder, Claude reads the files and immediately knows who Jackson is, what he's building, and how to behave.

---

## Important: hidden files

The `.claude/` folder is hidden by default and won't show up in normal file browsing.
- **Mac:** Press `Cmd + Shift + .` (period) in Finder to show hidden files
- **Windows:** File Explorer → View → check "Hidden items"
- **Claude Code:** The file tree shows everything automatically

---

## What's in here

```
JacksonPetrina/
│
├── CLAUDE.md               ← Claude's rules. Auto-loaded every session.
├── mendingform-agents.md   ← Brand brief + AI team for mendingform
├── AI_CONTEXT.md           ← Quick onboarding for new AI sessions
├── DEVELOPER.md            ← How to add/update skills and files
├── TOKEN_SAVING_NOTES.md   ← How to keep Claude fast and efficient
├── TROUBLESHOOTING.md      ← Common problems and fixes
├── JacksonPetrinares.pdf   ← Jackson's resume
│
└── .claude/
    └── skills/             ← Shortcuts. Type /skill-name and Claude runs a workflow.
        ├── post-workflow.md        /post-workflow — hooks + arc + caption + hashtags in one shot
        ├── hook-writer.md          /hook-writer — 5 video hooks, weakest to strongest
        ├── content-analyst.md      /content-analyst — analyze social media performance
        ├── commission-outreach.md  /commission-outreach — 3-message DM sequence for buyers
        ├── outreach-draft.md       /outreach-draft — write any outreach message, 3 versions
        ├── roast.md                /roast — stress-test any idea before committing
        ├── simplify.md             /simplify — explain any topic in plain English
        └── session-handoff.md      /session-handoff — save your place before clearing
```

---

## How to use skills

Type `/skill-name` in Claude and it runs that workflow automatically.
Example: type `/post-workflow` → Claude asks what the piece is about → returns hooks, caption, and hashtags.

The filename in `.claude/skills/` must match the command exactly.
`hook-writer.md` is invoked by `/hook-writer`. Rename it and it breaks.

---

## How to use this day-to-day

**When you finish a piece:** Type `/post-workflow` and describe it in one sentence. Claude returns hooks, video arc, caption, and hashtags all at once.

**For any other task:** Type the matching slash command. `/roast` an idea, `/simplify` something confusing, `/commission-outreach` when you have a buyer to reach.

**Before clearing context:** Always type `/session-handoff` first. It saves your place so you can pick up exactly where you left off in a new session.

**To make Claude smarter over time:** When something works (or doesn't), ask Claude to add it to Lab Notes in `mendingform-agents.md`. One line per session compounds over time.

---

## What "agents" actually means

The agents listed in `mendingform-agents.md` are NOT automated tools — there is no code running.
They are copy-paste templates. To use one: copy the invoke block → open a fresh Claude session → paste it.
The `/post-workflow` skill runs through four of them automatically, so you rarely need to do this manually.

---

## The QA process (do this before posting anything)

1. Finish your content using `/post-workflow` or any other skill
2. Open a **brand new Claude session** — not the one you've been working in
3. Paste this exactly, then paste your content underneath:
   ```
   You are QAReviewer for mendingform — a layered sculpture art brand.
   Tone: real, grounded, intentional — never salesy.
   Score: SHIP IT / MINOR EDITS / REWORK. Return 3 bullets: what's strong, what to fix, specific suggestion.
   ```
4. Act on the verdict before posting

The reason for a fresh session: Claude in the same session that created the content is biased toward it.

---

## Setting up analytics (when you start posting)

1. Create creator accounts on Instagram, TikTok, and YouTube
2. Sign up at **Metricool.com** (free) → connect all three platforms
3. Every week: export the analytics report → paste it into Claude → type `/content-analyst`
4. Claude tells you what's working, what to stop, and what to test next

---

## What mendingform is

Layered MDF sculpture with a spiritual message — art about returning to oneness with oneself. Made in a real shop. Sold via Instagram DMs, in person, and commissions. $2,000–$3,000 per original piece.
