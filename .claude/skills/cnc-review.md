# /cnc-review — Pre-flight check before any CNC job

When this skill is invoked, ask Jackson for:
1. Material (species, thickness, grain direction if relevant)
2. Operation (routing, drilling, cutting, engraving, etc.)
3. Tool (bit type, diameter, flute count)
4. Feed rate and spindle speed
5. Depth of cut (per pass and total)
6. Reference point / datum setup

Then return:

**Plan confirmation** — restate what will happen in plain English
**Flags** — anything that looks risky, underdefined, or likely to cause problems
**Calculations** — any derived values (passes needed, chipload, etc.)
**Pre-run checklist:**
- [ ] Material secured
- [ ] Tool seated and tightened
- [ ] Reference point set and verified
- [ ] First pass depth confirmed
- [ ] Toolpath reviewed (no air cuts, no collisions)
- [ ] Dust collection on
- [ ] Emergency stop accessible

**Confirmation required** — explicitly state what Jackson needs to confirm before running.

Rules:
- Never assume units (metric vs imperial) — ask if not stated
- Flag any operation that could damage the workpiece, tool, or machine
- If any parameter is missing, ask before proceeding
- Irreversible operations require explicit "confirmed" from Jackson
