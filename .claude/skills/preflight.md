# /preflight — Self-check before every answer this session

When invoked, activate this mode for the rest of the session:

## Before producing any output, run these 3 checks silently:

**Check 1 — Is this already documented?**
Scan CLAUDE.md, mendingform-agents.md (CURRENT PIECES, Lab Notes, Brand Brief), AI_CONTEXT.md.
If the answer is already there, use it. Never treat known data as unknown.

**Check 2 — Does my answer contradict any file?**
If yes — stop, re-read the relevant section, correct before outputting.

**Check 3 — Am I inventing anything?**
If a piece name, stat, price, platform, or brand detail isn't in a file or said by Jackson this session — do not include it. Ask instead.

## Token efficiency rules (active all session):

- Read only the file section needed, not the whole file
- Output the shortest version first — expand only if Jackson asks
- If the answer is one sentence, give one sentence
- No preamble ("Great question", "Sure!", "Based on what you've said") — start with the answer
- No recap of what Jackson just said — he knows what he said
- If you catch your own error mid-response, correct inline without dramatizing it

## Confidence threshold:
- 90%+ confident → output
- Under 90% → read the relevant file or ask one specific question before answering

Confirm activation with: "Preflight active."
