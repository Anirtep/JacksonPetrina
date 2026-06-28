# Jackson Petrina — AI Agent Workspace

This is the brain behind Jackson's Claude sessions. Every time you open Claude, it reads this folder and knows exactly who Jackson is, what he's working on, and how to help.

---

## What's in here

```
JacksonPetrina/
│
├── CLAUDE.md               ← Claude's rules. Auto-loaded every session. Start here.
├── mendingform-agents.md   ← AI team for Jackson's art brand (mendingform)
├── JacksonPetrinares.pdf   ← Jackson's resume
│
└── .claude/
    └── skills/             ← Shortcuts. Type /skill-name and Claude runs a workflow.
        ├── post-workflow.md        /post-workflow — hooks + caption + hashtags in one shot
        ├── hook-writer.md          /hook-writer — 5 video hooks, weakest to strongest
        ├── content-analyst.md      /content-analyst — analyze social media performance
        ├── commission-outreach.md  /commission-outreach — DM scripts for art buyers
        ├── outreach-draft.md       /outreach-draft — write any outreach message
        ├── roast.md                /roast — stress-test any idea before building it
        ├── simplify.md             /simplify — explain any complex topic in plain English
        └── session-handoff.md      /session-handoff — save your place before clearing
```

---

## How to use this

**When you finish a piece:** Type `/post-workflow` and describe the piece in one sentence. Claude handles hooks, video arc, caption, and hashtags in one response.

**For any skill:** Just type the slash command. Example: `/roast` then describe your idea.

**To make Claude smarter over time:** When you learn something — a sales line that landed, a hook that flopped — tell Claude and ask it to add it to Lab Notes in `mendingform-agents.md`.

---

## Setting up analytics (do this when you start posting)

1. Create creator accounts on Instagram, TikTok, and YouTube
2. Sign up at **Metricool.com** (free) → connect all three platforms in one place
3. Every week: export the analytics report → paste it into Claude and type `/content-analyst`
4. Claude tells you what's working, what to stop doing, and what to test next

---

## What mendingform is

Layered MDF sculpture with a spiritual message — art about returning to oneness with oneself. Made in a real shop. Sold via Instagram DMs, in person, and commissions. $2,000–$3,000 per original piece.
