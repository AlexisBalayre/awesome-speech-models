# Skills & Commands for `awesome-speech-models` — Design

**Status:** Approved — ready for implementation plan
**Date:** 2026-05-31

## Goal

Add project-local skill and slash commands that make the existing curation workflow (source-monitor → list-curator) faster to invoke and closes the loop by applying curated entries to the list files. Capture editorial craft (one-liner writing, tag choice, placement, ordering) in one source of truth that both the main session and the `list-curator` agent reference.

## Non-goals

- No `auditing-the-list` skill — deferred until lists have content to audit.
- No `list-applier` agent — `/apply` runs in main session.
- No `/check-links`, `/new-domain`, `/stats` commands — premature with near-empty lists.
- No controlled tag vocabulary lockdown — seed + grow.
- No changes to `source-monitor`, `SOURCES.md`, `README.md`, or domain READMEs.
- No new permissions in `.claude/settings.json`.

## What gets created or changed

```
.claude/
├── agents/
│   ├── source-monitor.md      (unchanged)
│   └── list-curator.md        (one-line edit: defer craft to skill)
├── skills/
│   └── curating-an-entry/
│       └── SKILL.md           (NEW)
└── commands/
    ├── refresh.md             (NEW)
    ├── add.md                 (NEW)
    └── apply.md               (NEW)

CONTRIBUTING.md                (one-line edit: drop redundant `model` tag in example)
```

## The skill — `curating-an-entry`

### Trigger

`description:` frontmatter activates the skill when adding, updating, or removing an entry. Trigger phrases: *"add this repo"*, *"format this entry"*, *"update the X entry"*, or when processing `list-curator` output in the main session.

### Style

Flexible — judgment-driven, not a rigid checklist. The skill defers to `CONTRIBUTING.md` for the format contract and only adds the editorial layer.

### Contents

`SKILL.md` contains the following sections, in order:

1. **Defer-to-CONTRIBUTING note.** Format rules (`- **[Name](url)** — line. \`tag\`` shape, one-line constraint, no-duplicates rule) live in `CONTRIBUTING.md`. This skill is the *how to make good calls* layer.
2. **One-liner craft.**
   - Lead with what the project IS, not what it does in marketing terms.
   - Past the `—`: 8–14 words on what makes it notable.
   - Avoid marketing words: *amazing*, *powerful*, *state-of-the-art*, *easy*, *blazing fast*.
   - Draw from the repo description / README, not hype.
3. **Tag vocabulary.**
   - 1–3 tags per entry, lowercase, hyphenated.
   - **Capability** (open vocab, reuse existing first): `multilingual`, `streaming`, `on-device`, `realtime`, `voice-cloning`, `diarization`, `vad`, etc.
   - **Runtime** (only when notable): `rust`, `cpp`, `onnx`, `gguf`.
   - **Openness flag** (only when not OSS): `closed-source`.
   - Seed-then-grow: prefer reusing tags already in the lists; new tags added sparingly.
   - **No `kind` tag** (section placement already conveys whether it's a model/tool/dataset/etc.).
4. **Section placement disambiguation.** Worked examples for recurring edge cases:
   - Inference engine for an existing model → `Optimization & Inference`, not `Tools & Libraries`.
   - Pipeline/wrapper around a model → `Tools & Libraries`.
   - Paper that also released weights → entry under `Models` with paper link in description, **not** duplicated under `Papers`.
   - Cross-domain projects → primary domain only.
5. **Ordering tie-breakers.** Within a section: foundational/de-facto first → recent activity → GitHub stars as last resort. Papers section: chronological newest-notable first.
6. **Quality bar.**
   - Default: `pushedAt` within 12 months → include.
   - 12–24 months: include only if foundational/de-facto; otherwise skip.
   - >24 months: exclude unless foundational (Kaldi-class exceptions).
   - "Foundational" = referenced by other entries in the list, or de-facto standard in the field.
7. **Update / removal heuristics.**
   - Project archives: demote in ordering first; remove only if clearly superseded.
   - Name change: update entry in place.
   - 404: find replacement or remove.
8. **Workflow.** Step-by-step for the agent or main session: read CONTRIBUTING.md → pick section → write one-liner → pick tags → place in order.

## The commands

All commands are stored prompts at `.claude/commands/<name>.md`. All are project-local.

### `/refresh`

**Args:** none, or optional source name (e.g. `/refresh kyutai-labs`) to scope.

**Behavior:**
1. Dispatch `source-monitor` agent, surface candidates grouped by source.
2. **Pause** — show the digest to the user (source-monitor often returns 20+ items; user trims before curation).
3. On user confirmation, dispatch `list-curator` agent on the surfaced candidates.
4. Return formatted entries grouped by `file → section`, ready for `/apply`.

### `/add <url>`

**Args:** one URL — GitHub repo, HF model, arXiv paper, or leaderboard URL.

**Behavior:**
1. Dispatch `list-curator` agent on the single URL — skip source-monitor.
2. Curator verifies (link is live), classifies (domain + section), writes one-liner + tags per the skill.
3. Return the proposed entry + placement + any "skipped" or "borderline" notes.

Optimizes the "I just saw a cool repo" moment.

### `/apply`

**Args:** none. Reads the last `list-curator` output from main-session conversation context.

**Behavior:**
1. Find the most recent `list-curator` output in the conversation. If none, tell the user to run `/add` or `/refresh` first.
2. For each proposed entry: locate target file and section heading via `Read` + `Grep`.
3. Determine insertion point using the skill's ordering rules. If the section is empty (current state of all domain READMEs), the entry becomes the first item under the heading.
4. Use `Edit` to insert. **Per-edit permission prompts give the review checkpoint** — no diff-preview reinvention needed.
5. After all edits applied, summarize what landed where.

If the user wants to reject a specific proposed entry, they deny that specific `Edit` call.

## Existing-file edits

### `.claude/agents/list-curator.md`

Add **one line** to step 2 ("For each candidate"):

> *Before classifying or writing the one-liner, Read `.claude/skills/curating-an-entry/SKILL.md` for editorial guidance. CONTRIBUTING.md remains canonical for format.*

The agent's existing structure (load rules → verify → de-dupe → classify → write → quality gate → report) is preserved; only the source of editorial judgment moves to the skill.

### `CONTRIBUTING.md`

Drop the redundant `model` tag in the example so it does not contradict the skill's vocab rule.

**Before:**
```
- **[Whisper](...)** — robust multilingual ASR; the de-facto open baseline. `model` `multilingual`
```

**After:**
```
- **[Whisper](...)** — robust multilingual ASR; the de-facto open baseline. `multilingual`
```

## Build order

1. Write `curating-an-entry` skill (foundational — everything else references it).
2. One-line edit to `list-curator.md`.
3. One-line edit to `CONTRIBUTING.md` example.
4. Write `/add` command (simplest; lets us test the skill end-to-end against one real entry).
5. Write `/refresh` command.
6. Write `/apply` command (last; depends on the others producing valid curator output).
7. Smoke test: `/add https://github.com/openai/whisper` → `/apply` → confirm entry lands in `asr/README.md` under Models with the right format and ordering.

## Decisions log

Key decisions resolved during the grill, with reasoning preserved for future-you:

- **Skill vs CONTRIBUTING.md boundary** → skill *complements*. CONTRIBUTING.md owns format (the *what*); skill owns editorial judgment (the *how to make good calls*). Different readers, different layers.
- **Skill count** → one now (`curating-an-entry`), audit skill deferred until lists have content to audit.
- **Skill location** → project-local at `.claude/skills/curating-an-entry/`, versioned with the repo.
- **Integration with list-curator** → list-curator defers to the skill via `Read` (no Skill tool in its allowlist). Single source of truth, minimal change to a working agent.
- **Command set** → all three (`/refresh`, `/add`, `/apply`); the two thin ones are nearly free.
- **`/apply` mechanism** → main session does the edits via `Edit`. Per-edit permission flow gives review checkpoint. No new agent.
- **Skill content scope** → full, with tag vocabulary explicitly marked as seed-then-grow.
- **Tag vocabulary** → capability tags (open vocab) + optional runtime + `closed-source` flag. No `kind` tag — section already conveys it.
- **Quality bar** → 12-month default + foundational override. Hard enough to let `list-curator` reject cleanly; flexible enough to keep Kaldi-class exceptions.
