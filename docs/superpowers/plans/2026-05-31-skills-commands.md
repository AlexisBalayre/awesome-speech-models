# Skills & Commands Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Add one project-local skill (`curating-an-entry`) and three slash commands (`/refresh`, `/add`, `/apply`) that capture editorial craft in one source of truth and close the curation loop by writing curated entries to the right files.

**Architecture:** All artifacts are project-local under `.claude/`. The skill is the single source of editorial judgment (one-liner craft, tag vocab, section placement, ordering, quality bar). Commands are stored prompts that dispatch the existing `source-monitor` and `list-curator` agents and (for `/apply`) make `Edit` calls from the main session — per-edit permission prompts give the review checkpoint.

**Tech Stack:** Markdown only. No code. Claude Code conventions for skills (`.claude/skills/<name>/SKILL.md`), agents (`.claude/agents/<name>.md`), and slash commands (`.claude/commands/<name>.md`).

---

## File Structure

| Path | Action | Responsibility |
|---|---|---|
| `.claude/skills/curating-an-entry/SKILL.md` | Create | Editorial methodology (one-liner craft, tag vocab, placement, ordering, quality bar, update/removal heuristics) |
| `.claude/agents/list-curator.md` | Modify (1 line at start of §2) | Defer editorial judgment to the skill |
| `CONTRIBUTING.md` | Modify (line 16 example) | Drop redundant `model` tag so example matches new vocab rule |
| `.claude/commands/add.md` | Create | `/add <url>` — single-URL quick add via list-curator |
| `.claude/commands/refresh.md` | Create | `/refresh [source]` — chain source-monitor → list-curator |
| `.claude/commands/apply.md` | Create | `/apply` — write last curator output to files |

**Notes on validation:** This work is content authoring (Markdown prompts/methodology), not code. There is no unit test scaffold. The integration test for the whole stack is **Task 7's smoke run**: `/add https://github.com/openai/whisper` → `/apply` → confirm the entry lands in `asr/README.md` under Models with correct format and ordering. Each per-file task validates by `head`-ing the file and confirming structure.

---

## Task 1: Create the `curating-an-entry` skill

**Files:**
- Create: `.claude/skills/curating-an-entry/SKILL.md`

- [ ] **Step 1: Create the directory**

```bash
mkdir -p .claude/skills/curating-an-entry
```

- [ ] **Step 2: Write `SKILL.md`** with this exact content:

````markdown
---
name: curating-an-entry
description: Use when adding, updating, or removing an entry in this curated speech-AI list — e.g. "add this repo", "format this entry", "update the X entry", or when processing list-curator output. Editorial methodology layered on top of CONTRIBUTING.md's format rules.
---

# Curating an Entry

`CONTRIBUTING.md` is canonical for the **format** (`- **[Name](url)** — line. \`tag\`` shape, one-line constraint, no-duplicates rule). This skill is the *editorial judgment* layer: how to write a good one-liner, which tags to use, where to place an entry, when to include or skip it.

## When this applies

- Adding a single entry (often via `/add` or `list-curator` output).
- Updating an existing entry (project renamed, scope changed, new release worth noting).
- Removing or demoting an entry (project archived, link dead, superseded).
- Reviewing borderline candidates before they land in the lists.

## 1. One-liner craft

Past the `—`, write **8–14 words** describing what the project IS and why it's notable.

**Do:**
- Lead with what it is (a model, a toolkit, a runtime, a dataset).
- State the distinguishing feature in concrete terms ("multilingual ASR", "non-autoregressive vocoder", "on-device inference via ggml").
- Draw the description from the project's own README/abstract.

**Don't:**
- Marketing words: *amazing*, *powerful*, *state-of-the-art*, *blazing fast*, *easy*, *production-ready*.
- Generic phrases: *high-quality results*, *for everyone*, *next generation*.
- Long-form. If you need more than one line, the entry is wrong or belongs elsewhere.

**Examples**

Good:
- `robust multilingual ASR; the de-facto open baseline`
- `streaming neural codec (1.1 kbps) used in Moshi`
- `non-autoregressive flow-matching TTS with voice cloning`

Bad:
- `state-of-the-art speech recognition with amazing accuracy` (marketing words, no specifics)
- `a great tool for working with speech models` (generic, doesn't say what it IS)

## 2. Tag vocabulary

**1–3 tags per entry.** Lowercase, hyphenated. Reuse existing tags from the lists first; add new ones sparingly.

**Capability tags (open vocab)** — what the project does or a notable property. Seed examples:

- `multilingual`, `streaming`, `on-device`, `realtime`, `low-latency`
- `voice-cloning`, `voice-conversion`, `diarization`, `vad`
- `non-autoregressive`, `zero-shot`

**Runtime tags (only when notable)** — the implementation lang/runtime when it's a distinguishing factor.

- `rust`, `cpp`, `onnx`, `gguf`
- Skip these for ordinary Python projects — the default is implicit.

**Openness flag (only when not OSS):**

- `closed-source` — for commercial-only or weights-restricted entries that we choose to include.

**No `kind` tag.** Don't use `model`, `tool`, `dataset`, `paper`, `benchmark`, etc. — the section heading already conveys this. Adding it duplicates information.

## 3. Section placement

The eight sections per domain (Tools & Libraries · Models · Datasets · Benchmarks & Leaderboards · Optimization & Inference · Finetuning & RL · Papers & Research · Learning) cover most cases cleanly. The edge cases:

- **Inference engine for an existing model** (e.g. whisper.cpp, sherpa-onnx) → **Optimization & Inference**, not Tools & Libraries. The primary value is the inference layer.
- **Pipeline / wrapper around a model** (e.g. WhisperX) → **Tools & Libraries**. Primary value is the orchestration / UX.
- **Paper that also released weights** → one entry under **Models** with the paper link in the description ("introduced in arXiv:XXXX"). Do **not** duplicate under Papers.
- **Cross-domain project** (e.g. a speech-to-speech model that also does ASR) → place under its **primary domain only**. Cross-reference in the description if needed.
- **Hugging Face Spaces / demos** → only if they expose a leaderboard or canonical benchmark; otherwise skip.

When unsure, grep the section first to see what's already there. Match the precedent.

## 4. Ordering within a section

"Roughly by relevance/popularity" decomposes as:

1. **Foundational / de-facto first.** Whisper, Tacotron, Kaldi — entries everyone references go at the top, even if commits are quiet.
2. **Recent + active second.** Pushed in the last 6 months, growing usage.
3. **GitHub stars as last-resort tie-breaker.** Don't lead with stars; they're a noisy signal.

For **Papers & Research**: chronological, newest-notable first.

## 5. Quality bar

**Default rule** (use `gh repo view` for `pushedAt`):

- Within **12 months** → include if it meets the other criteria.
- **12–24 months** → include only if foundational / de-facto.
- **>24 months** → exclude unless foundational (Kaldi-class).

**Foundational override.** A project is "foundational" if (a) other entries in our lists already reference it, or (b) it's the de-facto standard in the field. These exceptions are rare; flag them in the proposal rather than auto-including.

**Open source default.** If the project is not OSS but we're including it (e.g. closed leaderboard, important commercial baseline), tag it `closed-source`.

**Skip:**

- Forks of existing entries that don't add a clear orthogonal capability.
- Single-experiment repos with no README, no releases, no usage signal.
- Tutorials with <100 stars unless widely cited.

## 6. Updating and removing

- **Project archives officially** → demote in section ordering first. Remove only if a clear successor exists or no one cites it anymore.
- **Name or URL changes** → update in place; verify the new link is canonical (not a vanity redirect).
- **Link 404s** → try the Wayback Machine to identify what was there, then find the current home or remove.
- **Superseded by a newer project from the same authors** → keep the original if still in use; otherwise remove and replace.

## 7. Workflow

When adding or processing entries:

1. **Read `CONTRIBUTING.md`** for the format contract.
2. **Verify the link is live** (`gh repo view` or WebFetch).
3. **Pick the domain** (`asr` / `tts` / `speech-to-speech`) by primary capability.
4. **Pick the section** using the placement rules in §3.
5. **Grep for duplicates** in that section.
6. **Apply the quality bar** (§5). If borderline, flag rather than silently drop.
7. **Write the one-liner** per §1.
8. **Pick tags** per §2.
9. **Determine position** in the section per §4.
````

- [ ] **Step 3: Verify the file structure**

Run: `head -10 .claude/skills/curating-an-entry/SKILL.md`
Expected: YAML frontmatter visible with `name: curating-an-entry` and `description: Use when adding...`

Run: `wc -l .claude/skills/curating-an-entry/SKILL.md`
Expected: ~110 lines.

- [ ] **Step 4: Commit**

```bash
git add .claude/skills/curating-an-entry/SKILL.md
git commit -m "feat: add curating-an-entry skill with editorial methodology"
```

---

## Task 2: Wire `list-curator` agent to defer to the skill

**Files:**
- Modify: `.claude/agents/list-curator.md:16` (insert a line right after `## 2. For each candidate`)

- [ ] **Step 1: Read the current file to confirm structure**

Run: `sed -n '14,22p' .claude/agents/list-curator.md`
Expected: lines 14–22 show `## 1. Load the rules` end, blank line, `## 2. For each candidate`, then the existing numbered substeps.

- [ ] **Step 2: Insert the deferral line**

Edit `.claude/agents/list-curator.md` to add one line immediately after `## 2. For each candidate` (line 16) and before substep `1. **Verify it's real & live**` (currently line 17). The inserted block is:

```
Before classifying or writing one-liners, Read `.claude/skills/curating-an-entry/SKILL.md` for editorial guidance. `CONTRIBUTING.md` remains canonical for format.

```

(Blank line after the sentence to separate it from the numbered list.)

After the edit, lines 16–18 should read:

```
## 2. For each candidate
Before classifying or writing one-liners, Read `.claude/skills/curating-an-entry/SKILL.md` for editorial guidance. `CONTRIBUTING.md` remains canonical for format.

1. **Verify it's real & live** — `gh repo view <owner>/<repo> --json name,description,stargazerCount,pushedAt,url` or WebFetch the URL. Anything that 404s or can't be confirmed is dropped.
```

- [ ] **Step 3: Verify the edit landed correctly**

Run: `sed -n '14,22p' .claude/agents/list-curator.md`
Expected: the deferral sentence appears between `## 2. For each candidate` and the numbered substeps; the rest of the file is unchanged.

Run: `git diff .claude/agents/list-curator.md`
Expected: a single one-line addition (plus a blank line) under the `## 2. For each candidate` heading.

- [ ] **Step 4: Commit**

```bash
git add .claude/agents/list-curator.md
git commit -m "refactor(list-curator): defer editorial judgment to curating-an-entry skill"
```

---

## Task 3: Fix `CONTRIBUTING.md` example to match new tag vocab

**Files:**
- Modify: `CONTRIBUTING.md:16` (drop redundant `model` tag)

- [ ] **Step 1: Confirm current example**

Run: `grep -n "Whisper" CONTRIBUTING.md`
Expected: line 16 reads exactly:

```
- **[Whisper](https://github.com/openai/whisper)** — robust multilingual ASR; the de-facto open baseline. `model` `multilingual`
```

- [ ] **Step 2: Replace the line**

Edit `CONTRIBUTING.md` line 16 from the above to:

```
- **[Whisper](https://github.com/openai/whisper)** — robust multilingual ASR; the de-facto open baseline. `multilingual`
```

- [ ] **Step 3: Verify**

Run: `grep -n "Whisper" CONTRIBUTING.md`
Expected: line 16 shows only `` `multilingual` `` after the description (no `` `model` ``).

- [ ] **Step 4: Commit**

```bash
git add CONTRIBUTING.md
git commit -m "docs(contributing): drop redundant kind tag in example"
```

---

## Task 4: Create `/add` command

**Files:**
- Create: `.claude/commands/add.md`

- [ ] **Step 1: Create the directory**

```bash
mkdir -p .claude/commands
```

- [ ] **Step 2: Write `add.md`** with this exact content:

```markdown
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
```

- [ ] **Step 3: Verify**

Run: `head -5 .claude/commands/add.md`
Expected: frontmatter with `description:` and `argument-hint: <url>` visible.

- [ ] **Step 4: Commit**

```bash
git add .claude/commands/add.md
git commit -m "feat(commands): add /add for single-URL quick add"
```

---

## Task 5: Create `/refresh` command

**Files:**
- Create: `.claude/commands/refresh.md`

- [ ] **Step 1: Write `refresh.md`** with this exact content:

```markdown
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
```

- [ ] **Step 2: Verify**

Run: `head -5 .claude/commands/refresh.md`
Expected: frontmatter with `description:` and `argument-hint: [source-name]`.

- [ ] **Step 3: Commit**

```bash
git add .claude/commands/refresh.md
git commit -m "feat(commands): add /refresh to chain source-monitor and list-curator"
```

---

## Task 6: Create `/apply` command

**Files:**
- Create: `.claude/commands/apply.md`

- [ ] **Step 1: Write `apply.md`** with this exact content:

```markdown
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
```

- [ ] **Step 2: Verify**

Run: `head -5 .claude/commands/apply.md`
Expected: frontmatter with `description:` (no `argument-hint:` since `/apply` takes no args).

- [ ] **Step 3: Commit**

```bash
git add .claude/commands/apply.md
git commit -m "feat(commands): add /apply to write curator output to files"
```

---

## Task 7: End-to-end smoke test

**Files:** none modified. This is a manual integration test of the whole stack.

**Why this exists:** This is the equivalent of the "make sure the test passes" step in code-TDD. Without it, the plan is "wrote 6 files" with no validation that the pieces work together.

- [ ] **Step 1: Run `/add` against a known-good URL**

In the Claude Code session, type:

```
/add https://github.com/openai/whisper
```

Expected: `list-curator` agent dispatches, Reads `CONTRIBUTING.md` and `.claude/skills/curating-an-entry/SKILL.md`, verifies the URL via `gh repo view openai/whisper`, returns a proposed entry similar to:

```
- **[Whisper](https://github.com/openai/whisper)** — robust multilingual ASR; the de-facto open baseline. `multilingual`
```

with placement `asr/README.md → Models`.

If the curator returns a `model` tag, the skill defer is not working — go back to Task 2 and check that the line landed.

- [ ] **Step 2: Run `/apply` to write the entry**

In the same session, type:

```
/apply
```

Expected: the command finds the curator output in conversation context, identifies `asr/README.md → Models`, reads the file, locates the `## Models` heading, and proposes an `Edit` to insert the bullet under it. Approve the edit.

- [ ] **Step 3: Verify the entry landed**

Run: `grep -A 1 "^## Models" asr/README.md`
Expected: the `## Models` heading immediately followed by the Whisper bullet entry. No other sections touched.

Run: `git diff asr/README.md`
Expected: a single bullet added under the `## Models` heading.

- [ ] **Step 4: Commit the smoke-test result**

```bash
git add asr/README.md
git commit -m "test: add Whisper entry as end-to-end smoke test of /add and /apply"
```

- [ ] **Step 5: Sanity-check `/refresh` exists and parses** (no full run)

Run: `head -5 .claude/commands/refresh.md`
Expected: frontmatter visible.

We do not do a full `/refresh` run as part of this plan because it depends on network state and watchlist contents that vary; running `source-monitor` is documented in `.claude/agents/README.md` and can be exercised separately.

---

## Done criteria

- All six artifacts exist at their expected paths.
- `list-curator.md` contains the deferral sentence.
- `CONTRIBUTING.md` example tag set is `` `multilingual` `` only.
- Whisper entry has been added to `asr/README.md → Models` via `/add` + `/apply`.
- Six commits on the branch (one per task) plus the smoke-test commit.
