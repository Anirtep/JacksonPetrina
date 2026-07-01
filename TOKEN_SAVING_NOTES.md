# TOKEN_SAVING_NOTES.md — How to keep Claude fast and efficient

Tokens are the "words" Claude reads and writes. More tokens = slower, more expensive.
This file explains how this workspace is structured to waste as few tokens as possible.

---

## The three-layer loading strategy

This workspace is designed so Claude only reads what it needs for the current task.

| Layer | File(s) | Loaded | Token cost |
|---|---|---|---|
| 1 | `CLAUDE.md` | Every session automatically | Small, paid every time — keep it lean |
| 2 | `mendingform-agents.md` | On demand, when mendingform work starts | Medium, paid per task |
| 3 | `.claude/skills/*.md` | Only when a /skill is invoked | Small, paid per invocation |

**The key principle:** Big files only load when needed. CLAUDE.md is lean by design.

---

## What is already optimized

- `CLAUDE.md` is kept under 70 lines — see DEVELOPER.md for the rule on why
- `mendingform-agents.md` is intentionally lean — verbose sections were removed
- Skills are independent — Claude reads only the one skill you invoke
- One rules file (CLAUDE.md) — previously there were two overlapping files
- No empty placeholder files — four docs/ files were deleted because they had no real content

---

## The biggest token traps to avoid

**1. Pasting long documents into the chat**
Instead of pasting mendingform-agents.md, say: "Read mendingform-agents.md for brand context."
Claude can read the file directly — no pasting needed.

**2. Long sessions that drift across topics**
CNC session → art session → trading session in the same window pollutes context.
Run `/session-handoff` then `/clear` when switching to a different domain.
Rule: compact at 60% context window, not 80% — quality degrades before the window is technically full.

**3. Re-explaining things that are already in files**
If Claude asks about something that's in CLAUDE.md or mendingform-agents.md, it may have
lost context. Don't re-explain — instead compact or start a fresh session.

**4. Rebuilding knowledge that should be saved**
Every time Jackson learns something and it's NOT saved to Lab Notes, that knowledge
must be re-derived from scratch next session. Lab Notes is the compound interest of this system.

---

## How to tell Claude what to load without wasting tokens

| Instead of... | Say this |
|---|---|
| Pasting the full brand brief | "Read mendingform-agents.md for brand context" |
| Pasting CLAUDE.md | Nothing — it's auto-loaded |
| Pasting a skill file | Type `/skill-name` — it loads automatically |
| Re-explaining past decisions | "Check AI_CONTEXT.md for what's settled" |

---

## Context commands (quick reference)

| Command | What it does |
|---|---|
| `/context` | Shows how much of the context window is used |
| `/compact [keep X]` | Compresses the session but keeps specific things |
| `/clear` | Wipes everything — run /session-handoff first |
| `/re` | Quick undo — rolls back the last action |

---

## The Lab Notes compound effect

Each Lab Notes entry prevents a repeated mistake in all future sessions.
One entry today = potentially hundreds of tokens saved across dozens of future sessions.
Write one entry per meaningful session. It pays dividends over time.

---

## Red flags that tokens are being wasted

- Claude asks a question that is already answered in an existing file
- Claude produces output that contradicts the Brand Brief
- A session runs long before producing any real deliverable
- The same mistake appears in Lab Notes more than once

---

## Files that should never be pasted into chat

- `CLAUDE.md` — auto-loaded
- `mendingform-agents.md` — reference by name
- Any skill file — invoked with /skill-name
- `AI_CONTEXT.md` — reference by name if needed

Pasting these files manually doubles the token cost for no benefit.
