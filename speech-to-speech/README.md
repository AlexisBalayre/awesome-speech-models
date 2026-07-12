# Speech-to-Speech

Direct speech↔speech: spoken dialogue models, voice conversion, real-time translation.

## Tools & Libraries
- **[Unmute](https://github.com/kyutai-labs/unmute)** — low-latency voice layer that gives text LLMs speech input and output (STT + LLM + TTS). `realtime`
- **[WEST](https://github.com/wenet-e2e/west)** — LLM-based speech toolkit for recognition, synthesis, and spoken dialogue. `toolkit`
- **[InvincibleVoice](https://github.com/kyutai-labs/invincible-voice)** — real-time assistive voice communication system (STT + LLM + TTS). `realtime`
<!-- frameworks for S2S pipelines / full-duplex dialogue -->

## Models
- **[Moshi-RAG](https://github.com/kyutai-labs/moshi-rag)** — full-duplex speech dialogue model augmented with retrieval. `realtime`
<!-- add: Moshi, full-duplex / spoken dialogue models, voice conversion models, ... -->

## Datasets
- **[Expresso](https://speechbot.github.io/expresso/)** — Meta's 48kHz expressive speech dataset: read styles plus 30 hours of improvised dialogues. `expressive`
<!-- paired speech, conversational speech, ... -->

## Benchmarks & Leaderboards
- **[Full-Duplex-Bench](https://github.com/DanielLin94144/Full-Duplex-Bench)** — evaluates turn-taking, backchannels, and interruption handling in full-duplex dialogue models. `full-duplex`
- **[URO-Bench](https://github.com/Ruiqi-Yan/URO-Bench)** — end-to-end benchmark testing understanding, reasoning, and oral conversation in spoken dialogue models. `conversational`
- **[Artificial Analysis — Speech-to-Speech](https://artificialanalysis.ai/speech-to-speech)** — independent leaderboard scoring speech reasoning, conversational dynamics, agentic performance, latency, and price. `closed-source`
<!-- latency, turn-taking, naturalness, translation quality, ... -->

## Optimization & Inference
- **[Voice Changer](https://github.com/w-okada/voice-changer)** — realtime voice conversion client supporting RVC, so-vits-svc, and MMVC models. `realtime` `voice-conversion`
- **[FastRTC](https://github.com/gradio-app/fastrtc)** — turns Python functions into real-time audio streams over WebRTC or WebSockets. `realtime` `streaming`
<!-- full-duplex streaming, latency budgets, ... -->

## Finetuning & RL
- **[moshi-finetune](https://github.com/kyutai-labs/moshi-finetune)** — LoRA finetuning for Moshi: turn stereo conversations into training data. `lora`
- **[RVC WebUI](https://github.com/RVC-Project/Retrieval-based-Voice-Conversion-WebUI)** — trains a retrieval-based voice conversion model from ten minutes of voice data. `voice-conversion`
- **[so-vits-svc-fork](https://github.com/voicepaw/so-vits-svc-fork)** — maintained so-vits-svc for singing voice conversion training with realtime inference support. `voice-conversion` `realtime`
<!-- adaptation, preference optimization, ... -->

## Papers & Research
- **[WavChat](https://arxiv.org/abs/2411.13577)** — 60-page survey of spoken dialogue models, from cascaded pipelines to end-to-end (2024). `survey`
- **[dGSLM](https://arxiv.org/abs/2203.16502)** — textless generative modeling of two-channel spoken dialogue with turn-taking and laughter (Meta, 2022). `full-duplex` `textless`
- **[GSLM](https://arxiv.org/abs/2102.01192)** — generative spoken language modeling from raw audio; founded the textless-NLP line (Meta, 2021). `textless`
- **[Translatotron](https://arxiv.org/abs/1904.06037)** — first direct speech-to-speech translation model, without intermediate text representation (Google, 2019). `translation`
<!-- key papers -->

## Learning
- **[Voice AI & Voice Agents: An Illustrated Primer](https://voiceaiandvoiceagents.com)** — engineering guide to realtime voice agents: latency, turn detection, interruptions, transport. `realtime` `low-latency`
- **[HF Audio Course — Speech-to-Speech Translation](https://huggingface.co/learn/audio-course/chapter7/speech-to-speech)** — hands-on unit building a cascaded speech-to-speech translation demo with open models. `translation`
<!-- tutorials, explainers -->

---
[← Speech Models hub](../README.md)
