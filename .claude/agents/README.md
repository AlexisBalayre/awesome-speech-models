# Agent catalog

Subagents run in their own context window and return only a summary, so research never bloats the main conversation. Both are **read-only** — they propose, they never edit the lists. Claude dispatches them when the trigger matches; you can also force one (e.g. "run source-monitor").

| Agent | When to use | Model · tools |
| :---- | :---------- | :------------ |
| `source-monitor` | "What's new from my sources?" — reads `SOURCES.md` and reports new/updated candidates from tracked GitHub orgs/users/repos (`gh`) and web leaderboards (`WebFetch`). | Haiku · Read/Glob/Grep/Bash/WebFetch |
| `list-curator` | Adding entries — verifies links are live, de-dupes, and returns entries formatted per `CONTRIBUTING.md`, filed to the right section. Often run right after `source-monitor`. | Sonnet · Read/Glob/Grep/WebFetch/WebSearch/Bash |

**Typical flow:** `source-monitor` surfaces candidates from `SOURCES.md` → `list-curator` verifies + formats them → you paste the approved entries into the lists.
