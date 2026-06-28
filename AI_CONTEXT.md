# AI_CONTEXT.md — Minimum context for a new Claude session

Read this at the start of any session where you have no prior context.
Read CLAUDE.md too — this file adds what CLAUDE.md doesn't cover.

---

## What this workspace is

Personal AI workspace for Jackson Petrina. Not a code project.
All files are Markdown (.md). No build steps, no tests, no code, no dependencies.
The "application" is the Claude session itself.

## Who Jackson is

Maker, artist, entrepreneur. Primary focus right now: mendingform (art brand).
Also does CNC woodworking, guitar building, locksmith work, business/sales.
Non-technical — explain everything in plain English first, then technical if needed.

## How the file loading system works

Three layers, each loaded differently:

| Layer | File | When loaded |
|---|---|---|
| 1 | `CLAUDE.md` | Auto-loaded every session — do not ask Jackson to paste it |
| 2 | `mendingform-agents.md` | Load on demand — read it when Jackson asks about mendingform |
| 3 | `.claude/skills/*.md` | Invoked by slash command — `/hook-writer` loads `hook-writer.md` |

Skill filename = the command. `hook-writer.md` → `/hook-writer`. Exact match required.

## What "agents" means in this project

The agents in `mendingform-agents.md` are NOT automated tools.
They are copy-paste invoke templates — Jackson copies the template block, opens a new Claude session, pastes it.
There is no API, no code, no automation. It is a manual workflow.

## What is settled — do not re-open these

- Price range: $2,000–$3,000 per original piece
- Platforms: Instagram, TikTok, YouTube Shorts
- Sell through: Instagram DMs · In person · Commissions
- Tone: real, grounded, intentional — never salesy
- Festival/Burning Man niche: logged as future opportunity only — do not make it the focus
- All `docs/` context files: deleted (empty placeholders, not needed yet)
- `claude-upgrades.md`: deleted — merged into CLAUDE.md
- `LICENSE`: deleted — Bill Foote template remnant

## What is still open

- `BOTTLENECKS` field in Brand Brief (`mendingform-agents.md`) — not yet filled in
- Metricool account not yet set up
- No commission targets identified yet
- Eye/mandala piece not yet posted — waiting on black frame, Part 2 video planned

## What has shipped (content)

- Process videos for both pieces (blue circle grid and eye/mandala) posted to IG/TikTok/Shorts
- "Before the Rain" (blue circle grid): finished, photographed — not being posted, archived for now
- Eye/mandala piece: near-finished, getting black frame

## Current priority

Post the new piece (in progress) when finished. Run /post-workflow when it's done.

## Known inconsistency to be aware of

`commission-outreach.md` mentions the psychedelic/visionary art community as a place to find buyers.
This is accurate advice Jackson may use eventually — it is NOT the current focus.
Do not push this angle. It is available when Jackson asks for it.

## The most important skill right now

`/post-workflow` replaces four separate agent calls in one response:
hooks + video arc + caption + hashtags.
Use it when Jackson finishes a piece and needs content for it.

## Lab Notes

Located at the bottom of `mendingform-agents.md`.
Format: `DATE | WHAT I TRIED | WHAT HAPPENED | CHANGE NEXT TIME`
Read Lab Notes before doing mendingform work — they prevent repeated mistakes.

## What NOT to do

- Do not rebuild deleted files (docs/ context files, claude-upgrades.md, LICENSE, index.html, index.rmd, images/photo.JPG)
- Do not bloat CLAUDE.md — it is intentionally lean
- Do not invent brand details — ask Jackson if anything is unclear
- Do not re-open settled decisions listed above
- Do not paste CLAUDE.md or mendingform-agents.md into chat — reference by name, let Claude read them
- Do not paste skill file contents — invoke them with /skill-name
