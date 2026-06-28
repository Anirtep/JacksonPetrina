# claude-upgrades.md — Operating rules for quality, verification, and parallel work

Run these in sequence on every serious task:
```
IDEA → ROAST → PLAN → BUILD with Verification → CONTEXT check → SUB-AGENTS + /GOAL → SHIP
```

---

## 1 — ROAST (stress-test before building)

YOU MUST run the council before building anything that costs time or money.

| Role | Job |
|---|---|
| Contrarian | Find the fatal flaw. Assume failure. |
| Expansionist | Find the biggest upside. Assume wild success. |
| First Principles | Pure logic only. No trends or outside context. |
| Deep Researcher | Real market data, competitor pricing, analogues. |
| Buyer | Role-plays the actual customer. Would they pay? |
| Judge | Reads all five. Issues the verdict. |

**Verdict**: Green Light / Reshape / Kill + cheapest 48-hour validation test

**Invoke:** `/roast` → answer 3 questions: target buyer, your edge, budget + timeline

---

## 2 — PLAN MODE (before any consequential execution)

IMPORTANT: For any task where a mistake costs >5 minutes to undo, enter plan mode first.

- Plan mode = Claude reads and researches but changes nothing
- Claude outlines steps, asks clarifying questions, maps the approach
- Switch out of plan mode only after you approve the plan
- Ask "how should we handle X?" not "do X" — let Claude reason through the problem first
- Tell Claude: "Ask me questions until you're 95% confident you understand exactly what I need"

---

## 3 — VERIFICATION LOOP (done means verified, not asserted)

IMPORTANT: Define "done" before the task starts. Claude loops until all conditions are met.

**Definition of Done format:**
```
DONE = [specific condition 1]
     + [specific condition 2]
     + verification loop ran and passed
```

**Build verification into the to-do list itself:**
- After each major step: screenshot / check / test
- Don't move to next step until 95% confident current step is correct
- Stress test: valid inputs, invalid inputs, edge cases, duplicates
- Report: pass count, fail count, what needs fixing

**Add to any build prompt:**
```
After building, run verification loop. Check each section.
Test with valid and invalid inputs. Only stop when Definition of Done is confirmed true.
```

---

## 4 — CONTEXT MANAGEMENT (long conversation = worse output)

IMPORTANT: Context rot starts before 50% full. Keep context under 60% of window.

| Command | Use |
|---|---|
| `/context` | See what's eating tokens |
| `/compact [keep X]` | Compress but preserve specific things |
| `/clear` | Wipe and start fresh (run session-handoff first) |
| `/re` | Quick undo — roll back without starting over |

**Session Handoff (run before /clear or switching domains):**
```
/session-handoff

Output:
- Current goal (one sentence)
- Locked decisions (list only)
- What shipped (filenames + what they contain)
- Open / deferred items
- "Pick up here:" — one sentence
```

**Domain switching rule:** Clear context between unrelated domains (CNC → trading, art → business). Accumulated context from one domain pollutes another.

---

## 5 — SUB-AGENTS + /GOAL (stop being the bottleneck)

YOU ARE THE JUDGE. Claude is the worker. Keep them separate.

**When to use sub-agents:** Any task with 3+ independent pieces (research, writing, analysis can all run simultaneously).

**Model rule:** Sub-agents doing bulk reading/research → Haiku (cheap). Main agent synthesizing → Opus.

**Sub-agent pattern:**
```
Spin up [N] parallel sub-agents, one per deliverable:
- Sub-agent 1 (Haiku): [research task] → saves to [filename]
- Sub-agent 2 (Haiku): [research task] → saves to [filename]
Main agent (Opus): synthesize all outputs into final answer.
```

**Goal template:**
```
/goal

[deliverable in plain language]

DONE WHEN:
- [objective condition 1]
- [objective condition 2]
After sub-agents finish, verify each file meets the bar before declaring done.
```

---

## 6 — OUTPUT QUALITY (challenge before accepting)

Never accept mediocre output.

- 65–80% there → "Not good enough, try a completely different approach"
- 80–90% there → "Almost — here's exactly what's off, revise"
- 90%+ → accept, then update the skill or CLAUDE.md with what not to do next time

**When Claude improves:** explicitly tell it to update the skill file or CLAUDE.md so it doesn't make the same mistake again.

**Challenge output that is:** vague, hollow-worded, unsupported by reasoning, assumes instead of asks, or declares done without verifying.

---

## 7 — ULTRATHINK (maximum reasoning budget)

Type `ultrathink` to allocate ~32K tokens of thinking before Claude responds.

**Use for:**
- Architecture or system decisions
- Complex debugging that hasn't resolved after 2 tries
- High-stakes decisions ($50+ to undo, irreversible)
- Trade setups involving significant capital
- Material selection or specs that will be expensive to change

**Do NOT use for:** simple fixes, one-off questions, anything that resolved fine on the first try.

---

## 8 — PERMISSIONS (safe autonomy)

Never use `--dangerously-skip-permissions`.

**Correct setup:**
- Explicitly ALLOW: known-safe commands for your workflow
- Explicitly DENY: destructive commands (rm, delete, DROP, truncate, remove)
- Deny list takes priority over allow list

One-time configuration that gives full speed without full danger.

---

## One-line reminders

1. Make it argue with you before it builds anything.
2. "Done" means verified, not asserted.
3. Long conversation = worse output. Handoff and clear between domains.
4. You review. Claude executes. Never flip this.
5. If it's just okay, reject it. Second try is usually dramatically better.
6. Type `ultrathink` when the decision matters.
