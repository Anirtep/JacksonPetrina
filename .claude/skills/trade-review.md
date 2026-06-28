# /trade-review — Structured options position analysis

When this skill is invoked, ask Jackson for:
1. Underlying (ticker)
2. Position type (long call / short put / spread / etc.)
3. Strike(s) and expiry
4. Current thesis ("why am I in this?")
5. Current P&L or entry price (optional)

Then return:

**Bull case** — what has to happen for this to work? Be specific.
**Bear case** — what kills this trade? Be specific. Don't soften it.
**Biggest risk** — the single thing that could cause maximum loss.
**Cheapest test** — the smallest way to validate the thesis before adding size.
**One question to answer** — what does Jackson most need to know before deciding anything?

Rules:
- Present bull and bear case with equal weight. Do NOT validate the trade just because Jackson asked.
- If the thesis is weak, say so directly.
- No financial advice — help Jackson think clearly, not tell Jackson what to do.
- Never assume position size or risk tolerance. Ask if relevant.
