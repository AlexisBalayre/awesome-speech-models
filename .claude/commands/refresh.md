---
description: Check tracked sources for new candidates and format them as list entries.
argument-hint: [source-name]
---

Refresh the lists by checking tracked sources in `SOURCES.md` and formatting any new candidates.

Process:

1. Dispatch the `source-monitor` agent. If `$ARGUMENTS` is non-empty, ask it to focus only on the named source; otherwise let it sweep the full `SOURCES.md` watchlist.

2. Present the source-monitor digest to the user grouped by source. **Pause** — wait for the user to confirm which candidates to take forward. (source-monitor often surfaces 20+ items; many won't be worth curating.)

3. Dispatch the `list-curator` agent on the confirmed subset. In the brief, include:
   - The subset of URLs/candidates the user picked.
   - Instruction to Read `.claude/skills/curating-an-entry/SKILL.md` for editorial guidance and `CONTRIBUTING.md` for format.
   - Required return shape: entries grouped by `file → section`, ready for `/apply`; plus any "skipped" or "borderline" notes.

4. Show the curator output to the user. **Do not write to any file** — that's `/apply`'s job.
