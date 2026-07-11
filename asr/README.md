# ASR — Automatic Speech Recognition

Speech → text. Curated tools, models, data, and research.

## Tools & Libraries
- **[SpeechBrain](https://github.com/speechbrain/speechbrain)** — all-in-one PyTorch speech toolkit (ASR, and more). `toolkit`
- **[NVIDIA NeMo](https://github.com/NVIDIA/NeMo)** — toolkit for ASR/TTS/LLM, strong pretrained models. `toolkit`
- **[WhisperX](https://github.com/m-bain/whisperX)** — Whisper pipeline adding word-level timestamps, forced alignment, and speaker diarization. `diarization`
- **[FunASR](https://github.com/modelscope/FunASR)** — industrial ASR toolkit with pretrained models for recognition, VAD, punctuation, and speaker diarization. `multilingual` `diarization`
- **[resemble-enhance](https://github.com/resemble-ai/resemble-enhance)** — speech denoising and enhancement (denoiser + bandwidth extension), usable as ASR preprocessing. `enhancement`
- **[WeKWS](https://github.com/wenet-e2e/wekws)** — end-to-end keyword spotting (wake-word) toolkit aimed at production. `on-device`

## Models
- **[Whisper](https://github.com/openai/whisper)** — robust multilingual ASR; de-facto open baseline. `multilingual`
<!-- add: wav2vec2, Conformer, Parakeet, Canary, ... -->

## Datasets
<!-- add: LibriSpeech, Common Voice, GigaSpeech, People's Speech, ... -->

## Benchmarks & Leaderboards
<!-- WER/CER on standard sets; Open ASR Leaderboard, ... -->

## Optimization & Inference
- **[faster-whisper](https://github.com/SYSTRAN/faster-whisper)** — CTranslate2 reimplementation of Whisper; much faster, lower memory. `inference`
- **[whisper.cpp](https://github.com/ggml-org/whisper.cpp)** — C/C++ port of Whisper using ggml; de-facto on-device inference runtime. `on-device`
- **[sherpa-onnx](https://github.com/k2-fsa/sherpa-onnx)** — next-gen Kaldi inference runtime on ONNX Runtime: ASR, TTS, VAD, and diarization across many platforms. `on-device`
- **[sherpa](https://github.com/k2-fsa/sherpa)** — PyTorch-based speech-to-text server framework built on next-gen Kaldi models. `streaming`

## Finetuning & RL
<!-- adaptation recipes, domain/language finetuning, ... -->

## Papers & Research
<!-- key papers -->

## Learning
<!-- tutorials, explainers -->

---
[← Speech Models hub](../README.md)
