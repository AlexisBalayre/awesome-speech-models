---
description: Format a single URL (repo, model, paper) as a list entry via list-curator.
argument-hint: <url>
---

Use the `list-curator` agent to format the URL `$ARGUMENTS` as a paste-ready entry for this curated list.

Process:

1. Dispatch the `list-curator` agent. In the brief, include:
   - The single URL: `$ARGUMENTS`. Skip source-monitor entirely.
   - Instruction to Read `.claude/skills/curating-an-entry/SKILL.md` for editorial guidance and `CONTRIBUTING.md` for format.
   - Steps to follow: verify the link is live, classify the correct domain + section, grep for duplicates, write the one-liner and tags per the skill.
   - Required return shape: proposed entry (in the exact `CONTRIBUTING.md` format), target placement as `file → section`, and any "skipped" or "borderline" notes with reasons.

2. Show the agent's output to the user. **Do not write to any file** — that's `/apply`'s job.

3. If the curator flags the entry as borderline or skipped, surface the reason clearly so the user can decide whether to override.

If `$ARGUMENTS` is empty, tell the user to call `/add <url>` and stop.
