# /post-workflow — Full content pipeline for a new piece

One command that runs through every content step for a finished or in-progress piece.
Replaces the need to call hook-writer, content-crafter, and audience-scout separately.

When this skill is invoked, ask:
1. What is this piece or video about? (one sentence — the process, the moment, the material)
2. Platform: TikTok / Instagram Reels / YouTube Shorts (or all three)?
3. Finished piece reveal, mid-process footage, or early stages?

Then run all four steps in sequence and return everything in one response:

---

**Step 1 — Hooks**
5 options, weakest → strongest.
- Never start with a greeting, your name, or "Hey guys"
- Every hook must create a reason to keep watching: question, tension, surprise, or promise
- Shorter is almost always better for the opening line

**Step 2 — Video arc**
What to show, in what order. 3–5 beats maximum.
Format: Beat 1 [what viewer sees] → Beat 2 → Beat 3 → payoff/reveal

**Step 3 — Caption**
3 variations, shortest first.
- No hollow adjectives (stunning, amazing, incredible, unique)
- End with a CTA (comment, DM, share) — flag if missing
- Tone: real, grounded, never salesy

**Step 4 — Hashtags**
15 max. Mix of:
- Broad reach: #art #sculpture #handmade
- Niche community: #consciousart #visionaryart #processart
- Long-tail specific: #mdfart #layeredwood #cncsculpture
Label each HIGH / MEDIUM / LOW confidence.

---

After all four sections, end with:
> Ready for QA? Open a fresh Claude session and paste: "You are QAReviewer for mendingform. Score: SHIP IT / MINOR EDITS / REWORK. 3 bullets only." Then paste everything above.

Rules:
- Run all four steps even if Jackson only asked for one
- Shortest versions first in every section
- If unsure about tone or audience, check the Brand Brief in mendingform-agents.md
- Never invent hashtag performance data — label confidence honestly
