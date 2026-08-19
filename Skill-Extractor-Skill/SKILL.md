---
name: skill-extractor
description: Use when a useful capability exists inside a large repository, agent framework, or codebase that is too big or too tangled to convert as a whole — pull out just the one specific capability the user wants and distill it into a proper, scoped SKILL.md. Never runs, builds, or executes anything from the source repo — reads only. Output still needs to go through odysseus-privacy-skill-converter afterward, same as anything else before import.
---

# Skill Extractor

## When to use this
Not for a normal skill (single SKILL.md, a few small files) — that's the Converter's job. This is for when the useful thing is buried inside something much bigger: a full agent framework, an app repo, a large tool project — and only one piece of it is actually wanted.

## Hard rules
- Static read only. Never run, build, install dependencies for, or execute any part of the source repo to understand it — reasoning from reading code and docs, not from running them.
- Never pull in more than what's needed for the requested capability. Don't drag along unrelated modules just because they're nearby in the file tree.
- Never copy large blocks of source code verbatim into the output — understand what the logic does and re-express it as clear instructions/original code, same reasoning as the Synthesizer: avoids license conflicts and avoids silently inheriting bugs nobody re-examined.
- If credentials, API keys, or `.env`-style secrets are visible anywhere in the repo, never read their values or carry them into the output — note generically that the original expects a credential of some kind, nothing more.
- If the requested capability is too entangled with the rest of the codebase to cleanly separate — genuinely can't be pulled out without dragging in half the framework — say so plainly rather than forcing a broken or fake extraction.
- Preserve provenance: original repo, author, license, and specific file paths the extraction was drawn from.
- If the repo is too large to read in full, search it targeted — filenames, function names, and docs related to the requested capability — rather than attempting to ingest everything.
- The output is a draft. It still goes through odysseus-privacy-skill-converter before import, same as everything else — extraction doesn't imply it's already safe.

## Workflow

### Step 1 — Confirm scope before reading anything
Get a specific description of the one capability wanted. "Pull out the PDF-parsing logic" is scoped. "Convert this repo" is not — redirect that back to a normal Converter task or say the repo is too broad for extraction.

### Step 2 — Locate, don't ingest everything
Search the repo structure and docs for the specific files/functions relevant to the requested capability. Read only what's actually related, not the whole tree.

### Step 3 — Understand and distill
Once the relevant code/logic is found, understand what it does and why. Write a new, minimal SKILL.md that captures just that capability in clear original instructions — not a copy of the source files.

### Step 4 — Report what didn't make it
If parts of the capability depend on something too tangled to extract cleanly (a shared internal library, a required service, project-specific config), say so explicitly rather than silently dropping functionality or faking a self-contained version that won't actually work.

### Step 5 — Hand off with full provenance
Present: the draft SKILL.md, the source repo/author/license/file paths it was drawn from, and an honest note on anything left out and why. Stop there — same as every other skill in this system, this one's job ends at the draft.
