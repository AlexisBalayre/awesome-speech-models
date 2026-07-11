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
<!-- add: LJSpeech, VCTK, LibriTTS, ... -->

## Benchmarks & Leaderboards
- **[TTS Arena V2](https://huggingface.co/spaces/TTS-AGI/TTS-Arena-V2)** — crowdsourced blind A/B arena producing Elo rankings of open and proprietary TTS. `crowdsourced`
- **[Artificial Analysis — Text-to-Speech](https://artificialanalysis.ai/text-to-speech)** — independent leaderboard comparing quality Elo, price, and speed across TTS providers. `closed-source`
<!-- MOS / naturalness / intelligibility, ... -->

## Optimization & Inference
<!-- streaming synthesis, quantization, on-device, ... -->

## Finetuning & RL
<!-- voice cloning, speaker adaptation, RL for naturalness, ... -->

## Papers & Research
<!-- key papers -->

## Learning
<!-- tutorials, explainers -->

---
[← Speech Models hub](../README.md)
