---
name: skill-synthesizer
description: Use after find-skills-safe has returned several candidates for the same capability, when none of them is individually the best choice but each is strong in a different way. Combines the strongest ideas from multiple already-vetted skills into one new, purpose-built skill — rather than forcing a pick-one-and-settle decision. Never installs, executes, or imports anything itself; produces a draft SKILL.md for the human to review, test, and run through the privacy-skill-converter before it's ever used.
provenance_note: Any skill this produces must carry forward the provenance (author, source URL, license) of every source skill it drew from, not just one — it's a synthesis of several, so it owes credit to all of them.
---

# Skill Synthesizer

## When to use this
Only after `find-skills-safe` has already surfaced multiple candidates for the same capability, with a strengths/weaknesses breakdown showing no single clear winner — e.g. "A has the best coverage but weak security review, B has excellent security review but limited coverage, C is fastest but least maintained."

## Hard rules
- Never copy large blocks of code or instructions verbatim from any source skill. Understand *why* each source is strong at what it's strong at, and write original instructions that achieve the same outcome — this avoids license conflicts between sources with incompatible terms, and avoids inheriting bugs or risks nobody's actually re-examined.
- Carry forward provenance for every source drawn from, not just the primary one — author, source URL, license, and a one-line note on what was taken from each.
- If any two sources have genuinely incompatible licenses for the way they'd need to be combined, say so plainly and let the user decide rather than quietly picking one.
- Never install, execute, or import the result — output stops at a draft SKILL.md, same as every other skill in this system.
- Treat the resulting skill as unproven. It has no track record, unlike something copied faithfully from one audited source — recommend it be tested (via Odysseus's own effectiveness audit) before relying on it for real work, and always run it through the privacy-skill-converter before import, even though it was built following the same safety principles.
- Never silently drop a capability one of the sources had just because it's harder to merge — if something can't reasonably be included, say so rather than quietly omitting it.

## Workflow

### Step 1 — Understand what's actually being combined
Take the candidates and their strengths/weaknesses (from find-skills-safe, or supplied directly by the user). For each, identify: what specific thing does it do better than the others, and why — a technique, a piece of coverage, a design choice, not just a vague "it's good."

### Step 2 — Design, don't collage
Decide what the ideal combined version should actually do. This is a design decision, not a cut-and-paste job — same spirit as the brainstorming skill: propose the shape of the combined skill, and if the user is available, check in before committing to a direction rather than assuming.

### Step 3 — Write the new skill
Produce a SKILL.md that achieves the combined behavior in original instructions, structured the same way as every other skill in this system (frontmatter, workflow, hard rules matching the safety requirements already established — no auto-install, no auto-execute, static-only where applicable).

### Step 4 — Present with full provenance and an honest gaps list
Hand back: the draft SKILL.md, a table of what was taken from each source and why, any capability that didn't make it in and why, and any license conflict found. Stop there — this skill's job ends at the draft, same as everything else.
