# TTS — Text-to-Speech

Text → speech. Curated tools, models, data, and research.

## Tools & Libraries
- **[Coqui TTS](https://github.com/coqui-ai/TTS)** — deep-learning TTS toolkit with many models and voice cloning. `toolkit`
- **[Piper](https://github.com/rhasspy/piper)** — fast, local neural TTS optimized for edge devices. `local` `fast`
- **[WeTextProcessing](https://github.com/wenet-e2e/WeTextProcessing)** — text normalization and inverse normalization for TTS frontends and ASR output. `cpp`

## Models
- **[Kokoro](https://github.com/hexgrad/kokoro)** — 82M-parameter lightweight TTS; top-ranked open model on TTS Arena V2. `multilingual` `on-device`
- **[StyleTTS 2](https://github.com/yl4579/StyleTTS2)** — TTS via style diffusion and adversarial training with speech language models; basis of Kokoro. `zero-shot`
- **[OpenVoice](https://github.com/myshell-ai/OpenVoice)** — instant voice cloning with cross-lingual tone-color transfer, by MIT and MyShell. `voice-cloning` `zero-shot`
- **[fish-speech](https://github.com/fishaudio/fish-speech)** — multilingual zero-shot TTS with voice cloning. `multilingual` `zero-shot` `voice-cloning`
- **[Chatterbox](https://github.com/resemble-ai/chatterbox)** — open TTS with zero-shot voice cloning and emotion/intensity control. `zero-shot` `voice-cloning`
- **[VoxCPM](https://github.com/OpenBMB/VoxCPM)** — tokenizer-free multilingual TTS with voice design from text descriptions and voice cloning. `multilingual` `voice-cloning` `zero-shot`
- **[F5-TTS](https://github.com/SWivid/F5-TTS)** — non-autoregressive flow-matching TTS with zero-shot voice cloning. `zero-shot` `voice-cloning`
- **[Bert-VITS2](https://github.com/fishaudio/Bert-VITS2)** — VITS2 backbone with multilingual BERT for expressive synthesis. `multilingual` `license-restricted`
- **[OmniVoice](https://github.com/k2-fsa/OmniVoice)** — zero-shot voice-cloning TTS covering 600+ languages. `multilingual` `zero-shot` `voice-cloning`
- **[Silero Models](https://github.com/snakers4/silero-models)** — pre-trained TTS (and STT) models with a simple API. `multilingual` `on-device` `license-restricted`
- **[pocket-tts](https://github.com/kyutai-labs/pocket-tts)** — compact CPU-only TTS with low latency and voice cloning. `on-device` `voice-cloning`
- **[ZipVoice](https://github.com/k2-fsa/ZipVoice)** — compact zero-shot flow-matching TTS. `zero-shot`
- **[Habibi-TTS](https://github.com/SWivid/Habibi-TTS)** — unified dialectal Arabic speech synthesis. `multilingual`
- **[DramaBox](https://github.com/resemble-ai/DramaBox)** — prompt-driven expressive TTS with voice cloning, fine-tuned from the LTX-2.3 audio model. `voice-cloning` `license-restricted`
<!-- add: XTTS, Bark, MeloTTS, ... -->

## Datasets
- **[LJ Speech](https://keithito.com/LJ-Speech-Dataset/)** — 24 hours of single-speaker English audiobook clips; the classic TTS training corpus. `single-speaker`
- **[VCTK](https://datashare.ed.ac.uk/handle/10283/3443)** — 110 English speakers with varied accents; standard corpus for multi-speaker TTS. `multi-speaker`
- **[LibriTTS](https://www.openslr.org/60/)** — 585 hours of multi-speaker English at 24 kHz, derived from LibriSpeech. `multi-speaker`
- **[LibriTTS-R](https://www.openslr.org/141/)** — sound-quality-restored LibriTTS via speech restoration; cleaner target audio for TTS training. `multi-speaker`
- **[Emilia](https://huggingface.co/datasets/amphion/Emilia-Dataset)** — 215k hours of in-the-wild speech across six languages for generation training. `multilingual` `license-restricted`

## Benchmarks & Leaderboards
- **[TTS Arena V2](https://huggingface.co/spaces/TTS-AGI/TTS-Arena-V2)** — crowdsourced blind A/B arena producing Elo rankings of open and proprietary TTS. `crowdsourced`
- **[Artificial Analysis — Text-to-Speech](https://artificialanalysis.ai/text-to-speech)** — independent leaderboard comparing quality Elo, price, and speed across TTS providers. `closed-source`
<!-- MOS / naturalness / intelligibility, ... -->

## Optimization & Inference
- **[RealtimeTTS](https://github.com/KoljaB/RealtimeTTS)** — streaming text-to-audio library with low latency across many TTS engine backends. `streaming` `low-latency`
- **[MLX-Audio](https://github.com/Blaizzy/mlx-audio)** — speech generation and transcription on Apple Silicon via the MLX framework. `on-device`
- **[kokoro-onnx](https://github.com/thewh1teagle/kokoro-onnx)** — ONNX Runtime inference for Kokoro; near-realtime synthesis on CPU across platforms. `onnx` `on-device`
- **[Kokoro-FastAPI](https://github.com/remsky/Kokoro-FastAPI)** — Dockerized Kokoro-82M inference server with OpenAI-compatible endpoints and streaming output. `streaming`
<!-- streaming synthesis, quantization, on-device, ... -->

## Finetuning & RL
- **[GPT-SoVITS](https://github.com/RVC-Boss/GPT-SoVITS)** — few-shot voice cloning and TTS WebUI; train a voice from one minute of audio. `voice-cloning` `few-shot`
- **[Unsloth TTS Fine-tuning](https://unsloth.ai/docs/basics/text-to-speech-tts-fine-tuning)** — guides and notebooks for LoRA fine-tuning Orpheus, Sesame-CSM, and other TTS models. `lora`
<!-- voice cloning, speaker adaptation, RL for naturalness, ... -->

## Papers & Research
- **[Seed-TTS](https://arxiv.org/abs/2406.02430)** — ByteDance's 2024 family of versatile speech generation models with zero-shot in-context cloning. `zero-shot`
- **[VALL-E](https://arxiv.org/abs/2301.02111)** — 2023 paper casting TTS as neural-codec language modeling; sparked zero-shot cloning wave. `zero-shot`
- **[VITS](https://arxiv.org/abs/2106.06103)** — 2021 conditional VAE with adversarial learning; backbone of many open TTS models. `end-to-end`
- **[FastSpeech 2](https://arxiv.org/abs/2006.04558)** — 2020 non-autoregressive TTS trained with pitch, energy, and duration conditioning. `non-autoregressive`
- **[Tacotron 2](https://arxiv.org/abs/1712.05884)** — 2017 seq2seq mel-spectrogram synthesis with WaveNet vocoder; long-time neural TTS reference. `autoregressive`
- **[WaveNet](https://arxiv.org/abs/1609.03499)** — 2016 autoregressive raw-audio generative model that started neural speech synthesis. `autoregressive`
<!-- key papers -->

## Learning
- **[Hugging Face Audio Course — Unit 6](https://huggingface.co/learn/audio-course/chapter6/introduction)** — hands-on unit on TTS datasets, pretrained models, fine-tuning, and evaluation. `hands-on`
- **[Speech Zone — Speech Synthesis](https://speech.zone/courses/speech-synthesis/)** — University of Edinburgh course covering the TTS pipeline from text processing to waveform. `foundations`
- **[A Survey on Neural Speech Synthesis](https://arxiv.org/abs/2106.15561)** — comprehensive 2021 survey of neural TTS: architectures, vocoders, expressiveness, efficiency. `overview`
<!-- tutorials, explainers -->

---
[← Speech Models hub](../README.md)
