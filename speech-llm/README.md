# Speech LLM — Audio-Language Models

Speech/audio LLMs and audio understanding: audio-language models, spoken QA/dialogue understanding, audio captioning.

## Tools & Libraries
- **[lmms-eval](https://github.com/EvolvingLMMs-Lab/lmms-eval)** — unified evaluation harness for multimodal LLMs spanning text, image, video, and audio. `evaluation`
- **[UltraEval-Audio](https://github.com/OpenBMB/UltraEval-Audio)** — evaluation framework for speech and audio LLMs across understanding and generation benchmarks. `evaluation`
- **[SLAM-LLM](https://github.com/X-LANCE/SLAM-LLM)** — recipe-based toolkit for training speech, audio, and music LLMs. `multimodal`
<!-- frameworks for building / serving audio-language models -->

## Models
- **[Qwen2-Audio](https://github.com/QwenLM/Qwen2-Audio)** — Alibaba's large audio-language model with voice-chat and audio-analysis interaction modes. `voice-chat` `multilingual`
- **[SALMONN](https://github.com/bytedance/SALMONN)** — multimodal LLM family from ByteDance/Tsinghua hearing speech, audio events, and music. `music`
- **[Ultravox](https://github.com/fixie-ai/ultravox)** — multimodal LLM for real-time voice; projects audio directly into the LLM embedding space. `realtime`
- **[Kimi-Audio](https://github.com/MoonshotAI/Kimi-Audio)** — open audio foundation model for understanding, generation, and speech conversation. `voice-chat`
- **[Audio Flamingo](https://github.com/NVIDIA/audio-flamingo)** — NVIDIA audio-understanding model series adding long-audio reasoning and multi-turn chat. `long-audio`

## Datasets
- **[AudioSet](https://research.google.com/audioset/)** — 2M human-labeled 10-second YouTube clips over a 632-class sound-event ontology. `audio-events`
- **[AudioCaps](https://audiocaps.github.io/)** — 46K in-the-wild audio clips with crowdsourced captions, built on AudioSet. `captioning`
- **[Clotho](https://zenodo.org/records/4783391)** — audio captioning dataset of 6,974 clips with five crowdsourced captions each (v2.1). `captioning`
- **[WavCaps](https://huggingface.co/datasets/cvssp/WavCaps)** — 400K weakly-labelled clips with ChatGPT-assisted captions for audio-language pretraining. `captioning`
- **[OpenAQA (LTU)](https://github.com/YuanGongND/ltu)** — 5.6M (audio, question, answer) tuples for audio instruction tuning; trained LTU. `instruction-tuning`
<!-- audio-instruction data, spoken QA, audio captioning corpora, ... -->

## Benchmarks & Leaderboards
- **[AIR-Bench](https://github.com/OFA-Sys/AIR-Bench)** — generative benchmark for large audio-language models with GPT-4-judged open-ended answers. `llm-judge`
- **[MMAU](https://github.com/Sakshi113/MMAU)** — 10K clips, 27 tasks testing expert-level reasoning over speech, sounds, and music. `reasoning`
- **[AudioBench](https://github.com/AudioLLMs/AudioBench)** — universal audio-LLM benchmark spanning speech, scene, and paralinguistic tasks; live leaderboard. `multilingual`
- **[VoiceBench](https://github.com/MatthewCYM/VoiceBench)** — evaluates LLM-based voice assistants on spoken instructions: knowledge, reasoning, robustness (TACL 2026). `spoken-qa`
- **[Dynamic-SUPERB](https://github.com/dynamic-superb/dynamic-superb)** — collaborative, community-expanded benchmark for instruction-based evaluation of speech models. `crowdsourced`
<!-- audio understanding benchmarks, spoken QA evals, ... -->

## Optimization & Inference
- **[vLLM](https://github.com/vllm-project/vllm)** — high-throughput LLM serving engine; runs audio-language models like Qwen2-Audio and Ultravox. `inference`
- **[llama.cpp](https://github.com/ggml-org/llama.cpp)** — C/C++ LLM runtime whose mtmd stack runs audio-input models on-device. `on-device` `gguf`
<!-- serving audio-LLMs, audio tokenization for inference, ... -->

## Finetuning & RL
- **[LLaMA-Factory](https://github.com/hiyouga/LlamaFactory)** — unified finetuning for 100+ LLMs, including Qwen2-Audio and Omni audio tasks. `lora`
- **[ms-swift](https://github.com/modelscope/ms-swift)** — ModelScope framework for SFT, DPO, and GRPO across 300+ multimodal LLMs. `lora` `rlhf`
- **[align-anything](https://github.com/PKU-Alignment/align-anything)** — all-modality alignment framework for training models with feedback, including audio-text. `rlhf`
<!-- audio-instruction tuning, preference optimization, ... -->

## Papers & Research
- **[Recent Advances in Speech Language Models: A Survey](https://arxiv.org/abs/2410.03751)** — systematic survey of end-to-end speech language models: architectures, training, evaluation (ACL 2025). `survey`
- **[AudioPaLM](https://arxiv.org/abs/2306.12925)** — Google model fusing PaLM-2 and AudioLM to speak and listen. `translation` `closed-source`
- **[Pengi](https://arxiv.org/abs/2305.11834)** — Microsoft audio language model framing every audio task as text generation. `captioning`
- **[SpeechGPT](https://arxiv.org/abs/2305.11000)** — early LLM with discrete speech units enabling cross-modal spoken dialogue. `voice-chat`
<!-- key papers -->

## Learning
- **[audio-ai-hub](https://github.com/BinWang28/audio-ai-hub)** — curated hub of audio-LLM papers, models, benchmarks, and datasets. `awesome-list`
<!-- tutorials, explainers -->

---
[← Speech Models hub](../README.md)
