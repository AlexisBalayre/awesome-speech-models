# Diarization — Speaker Analysis

Speaker analysis: diarization (who spoke when), speaker embedding/verification, and voice activity detection.

## Tools & Libraries
- **[pyannote-audio](https://github.com/pyannote/pyannote-audio)** — neural building blocks for speaker diarization: VAD, speaker change, overlap, embeddings; pretrained pipelines. `diarization` `vad`
- **[Silero VAD](https://github.com/snakers4/silero-vad)** — lightweight pre-trained voice activity detector with ONNX and streaming support. `vad` `on-device`
- **[WeSpeaker](https://github.com/wenet-e2e/wespeaker)** — research and production speaker embedding toolkit with verification, recognition, and diarization recipes. `diarization` `onnx`
- **[3D-Speaker](https://github.com/modelscope/3D-Speaker)** — Alibaba toolkit for single- and multi-modal speaker verification, recognition, and diarization. `diarization`

## Models
- **[pyannote speaker-diarization-community-1](https://huggingface.co/pyannote/speaker-diarization-community-1)** — open pyannote pipeline succeeding 3.1; lower DER plus exclusive speaker timestamps for transcription alignment. `diarization`
- **[ECAPA-TDNN (SpeechBrain)](https://huggingface.co/speechbrain/spkrec-ecapa-voxceleb)** — speaker embedding trained on VoxCeleb (arXiv:2005.07143); de-facto open speaker verification baseline. `speaker-verification`
- **[Sortformer](https://huggingface.co/nvidia/diar_sortformer_4spk-v1)** — NVIDIA end-to-end diarizer resolving speaker permutation via sort loss (arXiv:2409.06656); four speakers max. `license-restricted`
- **[Streaming Sortformer](https://huggingface.co/nvidia/diar_streaming_sortformer_4spk-v2)** — streaming Sortformer variant tracking up to four speakers in real time; CC-BY-4.0. `streaming` `low-latency`
<!-- speaker embedding models, end-to-end diarization models, ... -->

## Datasets
- **[VoxCeleb](https://www.robots.ox.ac.uk/~vgg/data/voxceleb/)** — audio-visual corpus of 1M+ utterances from 7,000+ speakers; standard embedding training data. `in-the-wild`
- **[AMI Meeting Corpus](https://groups.inf.ed.ac.uk/ami/corpus/)** — 100 hours of multi-modal meeting recordings (CC-BY-4.0); the classic meeting diarization corpus. `meetings`
- **[VoxConverse](https://www.robots.ox.ac.uk/~vgg/data/voxconverse/)** — 50+ hours of in-the-wild YouTube conversation; the VoxSRC diarization track evaluation set. `in-the-wild`
- **[CALLHOME (NIST SRE 2000)](https://catalog.ldc.upenn.edu/LDC2001S97)** — LDC telephone conversation corpus; the classic CALLHOME diarization evaluation set. `telephone` `closed-source`

## Benchmarks & Leaderboards
- **[DIHARD III](https://dihardchallenge.github.io/dihard3/)** — hard-domain diarization challenge spanning clinical, restaurant, and web audio; DER/JER metrics. `in-the-wild`
- **[VoxSRC](https://mm.kaist.ac.kr/datasets/voxceleb/voxsrc/)** — VoxCeleb speaker recognition challenge series (2019–23) with a VoxConverse diarization track. `speaker-verification`
- **[dscore](https://github.com/nryant/dscore)** — reference DER and JER scoring tool used by the DIHARD challenges. `evaluation`
- **[pyannote.metrics](https://github.com/pyannote/pyannote-metrics)** — reproducible evaluation, diagnostic, and error-analysis toolkit for speaker diarization systems. `evaluation`
<!-- DER on standard sets, ... -->

## Optimization & Inference
- **[diart](https://github.com/juanmc2005/diart)** — streaming speaker diarization framework; overlap-aware, low-latency pipelines built on pyannote. `streaming` `realtime`
- **[TEN VAD](https://github.com/TEN-framework/ten-vad)** — low-latency, lightweight voice activity detector for realtime agents; desktop, mobile, and web. `vad` `low-latency`
- **[FluidAudio](https://github.com/FluidInference/FluidAudio)** — Swift CoreML runtime for on-device diarization, VAD, ASR, and TTS on Apple platforms. `on-device` `swift`
<!-- streaming diarization, on-device VAD, ... -->

## Finetuning & RL
- **[Adapting pyannote to your own data](https://github.com/pyannote/pyannote-audio/blob/develop/tutorials/adapting_pretrained_pipeline.ipynb)** — official pyannote notebook for adapting the pretrained diarization pipeline to new domains. `domain-adaptation`
<!-- domain adaptation, speaker enrollment, ... -->

## Papers & Research
- **[Powerset multi-class cross entropy loss for neural speaker diarization](https://arxiv.org/abs/2310.13025)** — Interspeech 2023 loss reformulation behind pyannote 3.x segmentation models. `diarization`
- **[A Review of Speaker Diarization: Recent Advances with Deep Learning](https://arxiv.org/abs/2101.09624)** — 2021 survey covering modular pipelines through end-to-end neural diarization systems. `survey`
- **[End-to-End Neural Speaker Diarization with Self-attention](https://arxiv.org/abs/1909.06247)** — Fujita et al. 2019; EEND framing diarization as multi-label classification. `diarization`
- **[X-Vectors: Robust DNN Embeddings for Speaker Recognition](https://www.danielpovey.com/files/2018_icassp_xvectors.pdf)** — Snyder et al. 2018; the DNN speaker embeddings that replaced i-vectors. `speaker-verification`
<!-- key papers -->

## Learning
- **[awesome-diarization](https://github.com/wq2012/awesome-diarization)** — curated papers, libraries, datasets, and learning materials for speaker diarization. `diarization`
- **[HF Audio Course — Transcribe a Meeting](https://huggingface.co/learn/audio-course/chapter7/transcribe-meeting)** — hands-on chapter combining pyannote diarization with Whisper for speaker-attributed transcripts. `diarization`
<!-- tutorials, explainers -->

---
[← Speech Models hub](../README.md)
