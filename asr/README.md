# ASR — Automatic Speech Recognition

Speech → text. Curated tools, models, data, and research.

## Tools & Libraries
- **[SpeechBrain](https://github.com/speechbrain/speechbrain)** — all-in-one PyTorch speech toolkit (ASR, and more). `toolkit`
- **[NVIDIA NeMo](https://github.com/NVIDIA/NeMo)** — toolkit for ASR/TTS/LLM, strong pretrained models. `toolkit`
- **[ESPnet](https://github.com/espnet/espnet)** — end-to-end speech processing toolkit spanning ASR, TTS, translation, and enhancement recipes. `multilingual`
- **[WhisperX](https://github.com/m-bain/whisperX)** — Whisper pipeline adding word-level timestamps, forced alignment, and speaker diarization. `diarization`
- **[FunASR](https://github.com/modelscope/FunASR)** — industrial ASR toolkit with pretrained models for recognition, VAD, punctuation, and speaker diarization. `multilingual` `diarization`
- **[icefall](https://github.com/k2-fsa/icefall)** — next-gen Kaldi training recipes for ASR using k2 and lhotse. `streaming`
- **[resemble-enhance](https://github.com/resemble-ai/resemble-enhance)** — speech denoising and enhancement (denoiser + bandwidth extension), usable as ASR preprocessing. `enhancement`
- **[WeKWS](https://github.com/wenet-e2e/wekws)** — end-to-end keyword spotting (wake-word) toolkit aimed at production. `on-device`

## Models
- **[Whisper](https://github.com/openai/whisper)** — robust multilingual ASR; de-facto open baseline. `multilingual`
- **[Qwen3-ASR-1.7B](https://huggingface.co/Qwen/Qwen3-ASR-1.7B)** — Apache-2.0 ASR covering 30 languages and 22 Chinese dialects; unified streaming/offline inference. `multilingual` `streaming`
- **[Canary-Qwen-2.5B](https://huggingface.co/nvidia/canary-qwen-2.5b)** — NVIDIA speech-augmented LLM pairing a FastConformer encoder with a Qwen decoder; English-only. `llm`
- **[Granite 4.0 1B Speech](https://huggingface.co/ibm-granite/granite-4.0-1b-speech)** — IBM's compact Apache-2.0 speech recognition model covering six languages. `multilingual`
<!-- add: wav2vec2, Conformer, Parakeet, ... -->

## Datasets
<!-- add: LibriSpeech, Common Voice, GigaSpeech, People's Speech, ... -->

## Benchmarks & Leaderboards
- **[Open ASR Leaderboard](https://huggingface.co/spaces/hf-audio/open_asr_leaderboard)** — ranks open ASR models by WER and RTFx across English, multilingual, and long-form suites. `multilingual`
- **[Artificial Analysis — Speech-to-Text](https://artificialanalysis.ai/speech-to-text)** — independent leaderboard comparing WER, speed, and price across open and commercial models. `closed-source`
<!-- WER/CER on standard sets, ... -->

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
