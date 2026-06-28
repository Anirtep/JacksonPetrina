# Jackson Petrina — AI Agent Workspace

This is Jackson's personal AI agent workspace. It holds the instructions, skills, and context files that make Claude useful across all of Jackson's projects.

## What this repo does

Every time Jackson opens a Claude session, Claude reads this workspace and immediately knows:
- Who Jackson is and what he works on
- How to help with each domain (art, CNC, guitar, trading, locksmith, sales)
- What skills are available (like `/roast`, `/hook-writer`, `/trade-review`)
- How to avoid past mistakes

Think of it like a brain that gets smarter over time — Jackson adds notes as he learns things, and Claude carries that knowledge into every future session.

## Key files

| File | What it does |
|---|---|
| `CLAUDE.md` | Loaded automatically. Core rules, memory rules, links to everything else. |
| `mendingform-agents.md` | The AI agent team for Jackson's art brand. 8 agents for content, sales, and analysis. |
| `claude-upgrades.md` | Advanced operating rules: stress-testing ideas, verification loops, parallel work. |
| `doc/JacksonPetrinares.pdf` | Jackson's resume. |

## Skills (`.claude/skills/`)

Skills are shortcuts — type `/skill-name` and Claude runs a structured workflow.

| Skill | What it does |
|---|---|
| `/simplify` | Explains any complex topic in plain language |
| `/roast` | Stress-tests an idea before you build it |
| `/hook-writer` | Writes 5 opening hooks for short-form video |
| `/content-analyst` | Analyzes social media data to find what's working |
| `/commission-outreach` | Writes DM scripts for reaching commission buyers |
| `/trade-review` | Structured options trade analysis |
| `/cnc-review` | Pre-flight check before running a CNC job |
| `/outreach-draft` | Writes outreach messages (3 versions, short to long) |
| `/session-handoff` | Saves session state before clearing context |

## Domain context files (`docs/`)

Reference files for each area of Jackson's work. Fill these in over time.

- `docs/cnc-context.md` — machine specs, materials, feed rates
- `docs/guitar-context.md` — scale lengths, current builds
- `docs/trading-context.md` — strategy, position sizing, risk rules
- `docs/business-context.md` — outreach systems, client types

## mendingform

Jackson's art brand. Layered MDF sculpture with a spiritual message — art about returning to oneness with oneself. Sold via Instagram DMs, in person, and commissions. $2,000–$3,000 per original piece. See `mendingform-agents.md` for the full agent team.
