# claude-upgrades.md — Four operating rules

Run all four on every serious task, in sequence:

```
IDEA → ROAST → BUILD with Verification → CONTEXT check → SUB-AGENTS + /GOAL → SHIP
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

## 2 — VERIFICATION LOOP (done means verified, not asserted)

IMPORTANT: Define "done" before the task starts. Claude loops until all conditions are met.

**Definition of Done format:**
```
DONE = [specific condition 1]
     + [specific condition 2]
     + verification loop ran and passed
```

**Loop:**
1. Screenshot every section (desktop + mobile) → fix errors → repeat
2. Stress test: valid inputs, invalid inputs, edge cases, duplicates
3. Report: pass count, fail count, what needs fixing

**Add to any build prompt:**
```
After building, run verification loop. Screenshot all sections.
Submit with valid, invalid, and edge-case inputs.
Only stop when Definition of Done is confirmed true.
```

---

## 3 — CONTEXT MANAGEMENT (long conversation = worse output)

IMPORTANT: Context rot starts before 50% full. Keep context under 25% of window.

| Command | Use |
|---|---|
| `/context` | See what's eating tokens |
| `/clear` | Wipe and start fresh |
| `/compact` | Compress (slow — use sparingly) |

**Session Handoff (run before /clear):**
```
/session-handoff

Summary must include:
- Current goal (one sentence)
- Locked decisions (list only, no explanation)
- What shipped (filenames + what they contain)
- Open / deferred items
- "Pick up here:" — one sentence
```

Workflow: run handoff → copy output → `/clear` → paste summary → continue clean.

---

## 4 — SUB-AGENTS + /GOAL (stop being the bottleneck)

YOU ARE THE JUDGE. Claude is the worker. Keep them separate.

Anything that can run in parallel should run in parallel. Each sub-agent gets one task and a clean context window.

**Sub-agent pattern:**
```
Spin up [N] parallel sub-agents, one per deliverable:
- Sub-agent 1: [task] → saves to [filename]
- Sub-agent 2: [task] → saves to [filename]
Each works independently. After all complete, verify each file meets the bar.
```

**Goal template:**
```
/goal

[deliverable in plain language]

DONE WHEN:
- [objective condition 1]
- [objective condition 2]
After sub-agents finish, open each file, fix anything thin before declaring done.
```

---

## One-line reminders

1. Make it argue with you before it builds anything.
2. "Done" means verified, not asserted.
3. Long conversation = dumb Claude. Handoff and clear early.
4. You review. Claude executes. Never flip this.
