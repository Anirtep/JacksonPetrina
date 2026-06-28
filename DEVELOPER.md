# DEVELOPER.md — How to maintain and extend this workspace

This guide is for Jackson, a collaborator, or any future maintainer.
There is no code in this project. Every file is plain text in Markdown format (.md).

---

## First: how to see all files

The `.claude/` folder is hidden by default (the dot at the start hides it on Mac and Windows).

- **Mac:** Press `Cmd + Shift + .` (period) in Finder to show/hide hidden files
- **Windows:** File Explorer → View → check "Hidden items"
- **Terminal:** `ls -la` shows all files including hidden ones
- **Claude Code:** All files are visible in the file tree regardless of hidden status

---

## Complete file map

```
JacksonPetrina/
│
├── CLAUDE.md               Auto-loaded every Claude session. Keep under 70 lines.
├── mendingform-agents.md   Brand context + agent invoke templates. Read on demand.
├── AI_CONTEXT.md           Onboarding file for new AI sessions with no prior context.
├── DEVELOPER.md            This file. Maintenance guide for humans.
├── TOKEN_SAVING_NOTES.md   How to keep Claude sessions fast and efficient.
├── TROUBLESHOOTING.md      Common problems and how to fix them.
├── README.md               Human overview. Not auto-read by Claude.
├── JacksonPetrinares.pdf   Jackson's resume. Not used by Claude.
│
└── .claude/
    └── skills/
        ├── post-workflow.md        /post-workflow  — hooks + arc + caption + hashtags in one shot
        ├── hook-writer.md          /hook-writer    — 5 video hooks, weakest to strongest
        ├── content-analyst.md      /content-analyst — analyze social media performance data
        ├── commission-outreach.md  /commission-outreach — 3-message DM sequence for buyers
        ├── outreach-draft.md       /outreach-draft — any outreach message, 3 versions
        ├── roast.md                /roast          — stress-test any idea before committing
        ├── simplify.md             /simplify       — explain any topic in plain English
        └── session-handoff.md      /session-handoff — save session state before /clear
```

---

## How to add a new skill

1. Create a `.md` file inside `.claude/skills/`
2. Name it exactly what you want to type, using hyphens instead of spaces, all lowercase
   - Want `/price-check`? → file must be named `price-check.md`
3. Use this structure (copy from an existing skill as a template):
   ```
   # /skill-name — One sentence describing what this does

   When this skill is invoked, ask:
   1. [question needed to run the skill]
   2. [question needed to run the skill]

   Then return: [describe the output format]

   Rules:
   - [what to always do]
   - [what to never do]
   ```
4. Add `/skill-name` to the `## Skills` line in `CLAUDE.md`
5. Add a row to the skills table in `README.md`

---

## How to update the Brand Brief

The Brand Brief lives inside `mendingform-agents.md` near the top.
Edit fields directly. Replace `[FILL:]` placeholder text with real information.
Never delete a field — only update the value.

**The one field still needing a real value:**
`BOTTLENECKS` — add what's actually slowing Jackson down right now.

---

## How Lab Notes work

Lab Notes are at the bottom of `mendingform-agents.md`.
Add one line after any session where something meaningful happened.

**Format:**
```
DATE | WHAT I TRIED | WHAT HAPPENED | CHANGE NEXT TIME
```

**When to add an entry:**
- After a skill produces unexpectedly bad output
- After a post performs much better or worse than expected
- After a DM conversation reveals what buyers respond to
- After any decision that should not be re-opened in a future session

---

## Rules for editing CLAUDE.md

Only add a line to CLAUDE.md if it meets ALL three criteria:
1. Relevant in almost every session (not just mendingform)
2. Not already handled by a skill file or reference file
3. Under 2 lines of text

Everything else belongs in a skill file or Lab Notes.
Each line in CLAUDE.md costs tokens on every session. Keep it tight.

---

## How to fix a skill that's giving bad output

1. Run the skill and note exactly what went wrong
2. Open the skill's file in `.claude/skills/`
3. Add a rule at the bottom: `- Do NOT [the specific thing that went wrong]`
4. Add an entry to Lab Notes
5. Run the skill again to confirm the fix worked

---

## Files that were removed and why

| File removed | Reason |
|---|---|
| `docs/cnc-context.md` | Empty placeholder — no real data yet |
| `docs/guitar-context.md` | Empty placeholder — no real data yet |
| `docs/trading-context.md` | Empty placeholder — no real data yet |
| `docs/business-context.md` | Empty placeholder — no real data yet |
| `claude-upgrades.md` | Merged into CLAUDE.md — one rules file is better than two |
| `LICENSE` | Leftover from Bill Foote portfolio template |
| `.claude/skills/trade-review.md` | Not using Claude for options trading currently |
| `.claude/skills/cnc-review.md` | Not using Claude for CNC pre-flight currently |
| `doc/JacksonPetrinares.pdf` | Duplicate — moved to repo root; `doc/` folder removed |
| `index.html`, `index.rmd` | Bill Foote PhD portfolio template files — unrelated to Jackson |
| `images/photo.JPG` | Bill Foote's photo — unrelated to Jackson |

---

## Git workflow

**Branch:** `claude/user-profile-summary-84oetr`

```bash
# Stage a specific file
git add filename.md

# Commit with a plain-English message
git commit -m "Short description of what changed and why"

# Push to remote
git push -u origin claude/user-profile-summary-84oetr
```

Write commit messages like you're leaving a note for yourself in six months.
Good: `Add /price-check skill for commission pricing conversations`
Bad: `update files`
