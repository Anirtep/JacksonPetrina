# TROUBLESHOOTING.md — Common problems and how to fix them

---

## Claude doesn't know about mendingform / gives generic output

**What's happening:** The mendingform context wasn't loaded.
**Fix:** Say: "Read mendingform-agents.md and tell me the brand mission."
If that doesn't work, the context window may be full — see "Session feels slow or off" below.

---

## A slash command isn't working

**What's happening:** The skill file may not exist or the name doesn't match.
**Fix:**
1. Check that the file exists: `.claude/skills/skill-name.md`
2. The filename must match the command exactly — hyphens, lowercase, no spaces
3. `hook-writer.md` works for `/hook-writer` — `hookwriter.md` does not
4. Make sure the file is saved

---

## Claude is re-opening a decision that was already made

**What's happening:** The decision wasn't saved anywhere permanent.
**Fix:** Add it to `AI_CONTEXT.md` under "What is settled."
If it's a brand decision (price, audience, tone), add it to the Brand Brief in `mendingform-agents.md`.

---

## The QA review is approving everything and not catching problems

**What's happening:** You're running QAReviewer in the same session that created the content.
The same Claude session is biased toward output it helped create.
**Fix:** Always use a completely fresh session for QA:
1. Open a brand new Claude session (not the one you've been working in)
2. Do NOT paste any background or context first
3. Paste exactly this, then paste the content underneath:
   ```
   You are QAReviewer for mendingform — a layered sculpture art brand.
   Tone: real, grounded, intentional — never salesy.
   Score: SHIP IT / MINOR EDITS / REWORK. Return 3 bullets: what's strong, what to fix, specific suggestion.
   ```

---

## Session feels slow, output quality dropped, or Claude seems confused

**What's happening:** Context rot — the session window is too full.
**Fix:**
1. Type `/context` to see how full the window is
2. If over 60%, run `/session-handoff` to save your place
3. Then run `/compact` to compress, or `/clear` to start fresh
4. Paste the session-handoff output at the top of the new session

---

## A skill is producing the right format but wrong brand tone

**What's happening:** The skill isn't referencing the brand voice rules correctly.
**Fix:**
1. Open the skill file in `.claude/skills/`
2. Check whether it says anything about tone
3. If not, add this line to the Rules section:
   `- Tone: real, grounded, intentional — never salesy. No hollow adjectives.`
4. Log the fix in Lab Notes

---

## Claude invented something that isn't in the Brand Brief

**What's happening:** A [FILL:] placeholder was interpreted as an instruction to guess.
**Fix:**
1. Correct Claude immediately: "That's not accurate — don't invent brand details"
2. Fill in the [FILL:] field with the real answer so it doesn't happen again
3. The only current unfilled field is BOTTLENECKS in `mendingform-agents.md`

---

## You added a skill but it's not being recognized

**Fix checklist:**
- [ ] File is in `.claude/skills/` (not in root or another folder)
- [ ] Filename is all lowercase with hyphens, no spaces
- [ ] Filename matches the command exactly (minus the slash)
- [ ] File is saved
- [ ] You typed `/skill-name` (with the slash)

---

## Lab Notes keep getting ignored / forgotten

**Fix:** Add Lab Notes to the end of your standard session close-out:
1. Run `/session-handoff` to save your place
2. Before you /clear, add one line to Lab Notes in mendingform-agents.md
3. Then /clear

---

## You can't find the .claude/ folder

**What's happening:** Hidden folders are invisible by default.
- **Mac:** Press `Cmd + Shift + .` in Finder to toggle hidden files
- **Windows:** File Explorer → View → check "Hidden items"
- **Claude Code:** The file tree shows all files including hidden ones
