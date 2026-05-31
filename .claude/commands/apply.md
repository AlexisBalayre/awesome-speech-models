---
description: Apply the most recent list-curator output to the right files.
---

Apply the most recent `list-curator` output from this conversation to the target files.

Process:

1. **Find the source.** Look at the recent conversation for the most recent `list-curator` agent output (formatted entries grouped by `file → section`). If you cannot find one, tell the user to run `/add <url>` or `/refresh` first and stop.

2. **For each proposed entry:**
   a. Read the target file (e.g., `asr/README.md`).
   b. Locate the target section heading via Grep.
   c. Determine the insertion point:
      - If the section is empty (likely — all three domain READMEs currently have only headers), the entry becomes the first bullet under the heading.
      - If the section has existing entries, place per the ordering rules in `.claude/skills/curating-an-entry/SKILL.md` §4 (foundational first → recent activity → stars as tie-breaker; Papers & Research section is chronological, newest-notable first).
   d. Use the `Edit` tool to insert the entry. The per-edit permission prompt gives the user a review checkpoint — if they deny an Edit, skip that entry and continue with the rest.

3. **After all edits applied,** summarize what landed where (e.g., `asr/README.md → Models: 1 entry added`) and note anything that was rejected or skipped.

Constraints:
- Do not reformat unrelated entries.
- Do not touch sections other than those named in the curator output.
- If the curator output also includes a "Skipped" section, do not act on those — they were explicitly rejected during curation.
