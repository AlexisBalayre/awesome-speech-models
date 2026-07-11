# Speech Models — Knowledge Hub

A curated knowledge base of **open-source tools, models, datasets, and research** for speech AI, kept as a single monorepo.

## Domains

| Domain | What |
|---|---|
| [ASR](./asr) | Automatic Speech Recognition — speech → text |
| [TTS](./tts) | Text-to-Speech — text → speech |
| [Speech-to-Speech](./speech-to-speech) | Direct speech↔speech, voice conversion, spoken dialogue |

## How this is organized

Each domain has its own `README.md` with the same sections, so the structure folds in the
related sub-topics (benchmarks, inference, finetuning) instead of scattering them:

- **Tools & Libraries** — open-source frameworks and toolkits
- **Models** — notable open models / checkpoints
- **Datasets** — training & evaluation data
- **Benchmarks & Leaderboards** — how models are compared
- **Optimization & Inference** — quantization, serving, streaming, latency
- **Finetuning & RL** — adaptation, SFT, preference/RL recipes
- **Papers & Research** — key reading
- **Learning** — tutorials, courses, explainers

See [CONTRIBUTING.md](./CONTRIBUTING.md) for the entry format and curation rules.

## Companion repos

- `awesome-agents/` — agents knowledge hub (separate monorepo)

---
_Started 2026-05-25. Curated, opinionated, work in progress._
