# Sources — watchlist

Orgs, experts, and repos to monitor for new tools, models, and research. The **`source-monitor`** agent reads this file and reports what's new; the **`list-curator`** agent turns surfaced candidates into verified entries. Update `Last checked` after each monitoring run.

Keep descriptions factual — the curator verifies everything before anything lands in the lists.

## Orgs
| Source | Focus | Last checked |
| :-- | :-- | :-- |
| [kyutai-labs](https://github.com/kyutai-labs) | Speech-to-speech (Moshi), neural audio codec (Mimi), STT/TTS (delayed-streams-modeling), streaming translation (Hibiki), unmute | 2026-07-11 |
| [nvidia (Hugging Face)](https://huggingface.co/nvidia) | Nemotron speech line (3.5 ASR live; TTS/S2S announced, weights pending), Canary, Parakeet, Sortformer, Audio Flamingo → `asr`/`speech-llm`/`diarization` | 2026-07-11 |
| [ggml-org](https://github.com/ggml-org) | whisper.cpp (de-facto on-device ASR inference), ggml → `asr` · inference | 2026-07-11 |
| [k2-fsa](https://github.com/k2-fsa) | Next-gen Kaldi: sherpa-onnx, icefall — ASR + on-device inference → `asr` | 2026-07-11 |
| [speechbrain](https://github.com/speechbrain) | SpeechBrain all-in-one PyTorch toolkit → `asr`/`tts` | 2026-07-11 |
| [espnet](https://github.com/espnet) | ESPnet end-to-end speech toolkit → `asr`/`tts` | 2026-07-11 |
| [wenet-e2e](https://github.com/wenet-e2e) | WeNet production ASR, WeSpeaker → `asr`/`diarization` | 2026-07-11 |
| [pyannote](https://github.com/pyannote) | pyannote-audio — speaker diarization → `diarization` | 2026-07-11 |
| [snakers4](https://github.com/snakers4) | Silero VAD + models → `diarization`/`tts` | 2026-07-11 |
| [fishaudio](https://github.com/fishaudio) | fish-speech, Bert-VITS2 → `tts` | 2026-07-11 |
| [SWivid](https://github.com/SWivid) | F5-TTS → `tts` | 2026-07-11 |
| [resemble-ai](https://github.com/resemble-ai) | chatterbox, resemble-enhance → `tts` | 2026-07-11 |
| [myshell-ai](https://github.com/myshell-ai) | OpenVoice, MeloTTS — popular, lower recent activity ⚠️ → `tts` | 2026-07-11 |

## Experts / users to follow
| Source | Who / focus | Last checked |
| :-- | :-- | :-- |
| [LaurentMazare](https://github.com/LaurentMazare) | Co-founder, Kyutai. Rust ML (candle), Moshi internals | 2026-07-11 |
| [adefossez](https://github.com/adefossez) | Researcher, Kyutai. EnCodec, Demucs, MusicGen, Moshi | 2026-07-11 |
| [Vaibhavs10](https://github.com/Vaibhavs10) | Vaibhav Srivastav (HF). insanely-fast-whisper, open-tts-tracker — speech OSS | 2026-07-11 |
| [m-bain](https://github.com/m-bain) | Max Bain. WhisperX → `asr` | 2026-07-11 |

## Benchmarks / leaderboards (web)
| Source | Tracks → domain | Last checked |
| :-- | :-- | :-- |
| [Artificial Analysis — Speech-to-Text](https://artificialanalysis.ai/speech-to-text) | ASR leaderboard: AA-WER, speed, price across 50+ providers → `asr` | 2026-07-11 |
| [Artificial Analysis — Text-to-Speech](https://artificialanalysis.ai/text-to-speech) | TTS leaderboard: Arena Elo, price, speed across 80+ models → `tts` | 2026-07-11 |
| [HF Open ASR Leaderboard](https://huggingface.co/spaces/hf-audio/open_asr_leaderboard) | WER + RTF across ASR models → `asr` | 2026-07-11 |
| [TTS Arena V2](https://huggingface.co/spaces/TTS-AGI/TTS-Arena-V2) | Crowdsourced Elo ranking of TTS models → `tts` | 2026-07-11 |

## Repos (single)
| Source | Why | Last checked |
| :-- | :-- | :-- |
| [modelscope/FunASR](https://github.com/modelscope/FunASR) | Industrial-grade ASR toolkit (170× realtime, 50+ languages, diarization, streaming) → `asr` | 2026-07-11 |
