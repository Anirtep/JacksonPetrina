# claude-upgrades.md
# Four operating upgrades — load this in any session to run sharper

> These four rules fix Claude's default failure modes. Apply all four, in order, on every serious task.

---

## The core problem (one paragraph)

Claude is tuned to make you feel productive, not to make you money. It agrees with you ~88% of the time (documented: "elephant" study). Output quality degrades as conversation length grows — this is called "context rot" and it starts well before the window is full. And Claude declares itself done before actually verifying the work. These four upgrades fix each of those directly.

---

## Upgrade 1 — ROAST (Anti-Sycophancy)

**Problem**: Claude approves whatever you say. Even if you change your mind, it approves that too.

**Rule**: Before building anything or approving any plan, run a stress-test council. Never skip this on decisions that cost time or money.

### The Council (5 roles + 1 judge)

| Role | Job |
|---|---|
| Contrarian | Find the single fatal flaw. Assume it will fail. |
| Expansionist | Find the biggest possible upside. Assume it succeeds wildly. |
| First Principles | Use only pure logic. No outside context, no trends. |
| Deep Researcher | Pull real market data, competitor pricing, analogous products. |
| Buyer | Role-play as the actual customer. Would they pay? Why / why not? |
| Judge | Reads all five reports. Issues the verdict. |

### Verdict format
- **Green Light** — ship as-is
- **Reshape** — keep the core, change the approach (most common)
- **Kill** — fatal structural flaw, don't build this

**Always includes**: the single cheapest test you can run in 48 hours to validate before writing any code or spending any money.

### How to invoke
```
/roast

[describe your idea in 2–3 sentences]

Answer 3 questions when asked:
1. Who is the actual buyer?
2. What is your edge / what do you already have?
3. What are your constraints and how fast do you need revenue?
```

### Key insight
A council with different personas gives you perspectives that a single model — even Opus — cannot generate alone. Generic "do you think this will work?" questions get generic answers. The council forces disagreement by design.

---

## Upgrade 2 — VERIFICATION LOOP (Check Its Own Work)

**Problem**: Claude hands you something that looks finished. "Finished" and "working" are not the same thing. NYU study: ~40% of AI-generated code has security vulnerabilities.

**Rule**: Claude does not get to declare itself done. It must verify first. You define what "done" looks like before it starts.

### Two-part loop

**Part 1 — Build verification** (before it hands anything to you):
- Take screenshots of every section (desktop + mobile)
- Click every button
- Submit forms with valid AND invalid inputs
- Repeat until zero visible errors

**Part 2 — Stress testing** (after it says it's done):
- Run edge cases humans might actually hit (spaces in emails, wrong formats, double submissions)
- Try to break it
- Report what broke and what passed with counts

### Definition of Done format
Write this before the task starts. Example:
```
DONE = all 6 files exist and none are empty
     + market research has 6+ competitors
     + outreach drafts = 25 pieces minimum
     + verification loop ran and passed
     + no visible layout errors on mobile
```

The more objective, the better. Claude loops until these conditions are met.

### How to invoke
Add this block to any build prompt:
```
After building, do NOT trust that it looks right.
Run a verification loop:
1. Screenshot every section (desktop + mobile)
2. Review each screenshot — fix anything broken
3. Submit forms with valid inputs, invalid inputs, edge cases (spaces, wrong format, duplicates)
4. Report: how many passed, how many failed, what needs fixing
Only stop when every item in the Definition of Done is confirmed true.
```

### Key insight
Claude gets you ~65% there on the first pass. Verification gets you to ~90%. You only have to review, not rebuild.

---

## Upgrade 3 — CONTEXT MANAGEMENT (Keep Claude Sharp)

**Problem**: Context rot. Every AI model degrades as conversation length grows. The drop-off starts before the window is even 50% full. More tokens = worse outputs.

**Rule**: Keep context lean. Never let it fill past ~25% of the window. When it approaches that, run Session Handoff before clearing.

### Commands to know

| Command | What it does |
|---|---|
| `/context` | Shows what's eating your context window with token counts |
| `/clear` | Wipes the context and starts fresh |
| `/compact` | Compresses the conversation (slower, use sparingly) |

### Session Handoff skill (run this before /clear)

Session Handoff writes a tight summary containing:
- What we're working on
- Decisions that are locked (don't re-litigate)
- What shipped (key files, their locations)
- Open questions / deferred decisions
- Exactly where to pick back up

**Workflow**: Run `/session-handoff` → copy the output → run `/clear` → paste the summary back in → continue from clean context with no lost progress.

### How to invoke
```
/session-handoff

Give me a handoff summary with:
- Current goal in one sentence
- Decisions locked (list, no explanation needed)
- What shipped: file names and what they contain
- Open questions or deferred items
- "Pick up here:" — one sentence on the next action
```

### Key insight
Short context = higher quality. A clean window with a good handoff summary outperforms a bloated window with "full history." Paste summaries into sub-agents, never raw conversation history.

---

## Upgrade 4 — SUB-AGENTS + /GOAL (Stop Being the Bottleneck)

**Problem**: You can only point Claude one direction at a time. You are the bottleneck. Anthropic's own test: multi-agent team outperformed single agent by 90%+ on research tasks.

**Rule**: Anything that can happen in parallel should run in parallel. Set an explicit finish line and a separate evaluator — Claude doesn't get to grade its own work.

### Sub-agents
A sub-agent is a separate Claude instance with:
- Its own clean context window (no context rot from the main session)
- One specific task
- Its own output file (outputs never overwrite each other)

**When to use**: Any task with 3+ independent pieces. Research, writing, and analysis can all run simultaneously. Synthesizer reads all outputs last.

**Pattern**:
```
Spin up [N] parallel sub-agents, one per deliverable:
- Sub-agent 1: [task] → saves to [filename]
- Sub-agent 2: [task] → saves to [filename]
- Sub-agent 3: [task] → saves to [filename]
Each works independently. Do not wait for others.
After all complete, run a verification pass on each file.
```

### /goal
Sets a finish line that Claude works toward turn after turn until a separate evaluator confirms it's done. The builder and the judge are different models — Claude cannot declare itself done.

```
/goal

[describe the deliverable]

DONE WHEN:
- [specific, objective condition 1]
- [specific, objective condition 2]
- [specific, objective condition 3]

After sub-agents finish, open each file, verify it meets the bar,
fix anything thin or generic before declaring done.
```

### Key insight
You shift from builder → decision maker and reviewer. Claude runs the parallel work. You approve, redirect, and judge. This is the correct division of labor.

---

## All four, in sequence

```
IDEA
  ↓
ROAST → Reshape / Green Light / Kill + 48hr test
  ↓
BUILD with Verification Loop baked in
  ↓
CONTEXT check — session handoff if approaching 25%
  ↓
SCALE with sub-agents + /goal for parallel execution
  ↓
SHIP (verified, tested, edge cases found)
```

---

## One-line reminders

- **Upgrade 1**: Make it argue with you before it builds anything.
- **Upgrade 2**: "Done" means verified, not asserted.
- **Upgrade 3**: Long conversation = dumb Claude. Clear early, handoff first.
- **Upgrade 4**: You are the judge. Claude is the worker. Keep them separate.
