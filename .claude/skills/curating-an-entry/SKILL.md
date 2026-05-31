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
