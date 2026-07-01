# /session-handoff — Save session state before clearing context

When this skill is invoked, output exactly this structure:

**Current goal:** [one sentence — what are we trying to accomplish?]

**Locked decisions:** [bullet list — what has been decided and should not be re-litigated]

**What shipped:** [bullet list — files created/modified, what each contains]

**Open / deferred:** [bullet list — questions not yet answered, decisions pending]

**Pick up here:** [one sentence — the exact next action to take in the new session]

**Key files to load:** [list any files that the new session needs to read immediately]

Rules:
- Be specific. "We decided to use imperial units for the CNC job" not "we made some decisions."
- Do not summarize the whole conversation — only what matters for continuing the work.
- Keep it under 20 lines total.
- After outputting, remind Jackson: copy this → /clear → paste it back in.
