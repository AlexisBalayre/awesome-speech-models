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
- **[wav2vec 2.0](https://huggingface.co/facebook/wav2vec2-base-960h)** — self-supervised speech representation model introduced in arXiv:2006.11477; CTC-finetuned on LibriSpeech. `ctc`
- **[Qwen3-ASR-1.7B](https://huggingface.co/Qwen/Qwen3-ASR-1.7B)** — Apache-2.0 ASR covering 30 languages and 22 Chinese dialects; unified streaming/offline inference. `multilingual` `streaming`
- **[Canary-Qwen-2.5B](https://huggingface.co/nvidia/canary-qwen-2.5b)** — NVIDIA speech-augmented LLM pairing a FastConformer encoder with a Qwen decoder; English-only. `llm`
- **[Granite 4.0 1B Speech](https://huggingface.co/ibm-granite/granite-4.0-1b-speech)** — IBM's compact Apache-2.0 speech recognition model covering six languages. `multilingual`
<!-- add: Parakeet, ... -->

## Datasets
- **[LibriSpeech](https://www.openslr.org/12)** — 1,000 hours of read English audiobook speech; the standard ASR benchmark corpus. `read-speech`
- **[Common Voice](https://commonvoice.mozilla.org/)** — Mozilla's crowdsourced multilingual speech corpus spanning 100+ languages, continuously growing. `multilingual` `crowdsourced`
- **[GigaSpeech](https://github.com/SpeechColab/GigaSpeech)** — 10,000 hours of transcribed English audio from audiobooks, podcasts, and YouTube. `multi-domain`
- **[Multilingual LibriSpeech](https://www.openslr.org/94/)** — 50,000-hour audiobook corpus extending LibriSpeech to eight European languages. `multilingual` `read-speech`
- **[People's Speech](https://huggingface.co/datasets/MLCommons/peoples_speech)** — 30,000+ hours of transcribed English speech under CC-BY/CC-BY-SA licensing. `multi-domain`
<!-- add: ... -->

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
- **[Fine-Tune Whisper (HF blog)](https://huggingface.co/blog/fine-tune-whisper)** — step-by-step recipe for finetuning Whisper on new languages with Transformers. `multilingual`
- **[Fine-Tune Wav2Vec2 (HF blog)](https://huggingface.co/blog/fine-tune-wav2vec2-english)** — walkthrough finetuning wav2vec 2.0 with CTC for English ASR. `ctc`
- **[Whisper-Finetune](https://github.com/yeyupiaoling/Whisper-Finetune)** — Whisper finetuning with LoRA and timestamp data, plus accelerated deployment paths. `lora`
<!-- adaptation recipes, domain/language finetuning, ... -->

## Papers & Research
- **[Conformer](https://arxiv.org/abs/2005.08100)** — convolution-augmented Transformer encoder; the dominant architecture in modern ASR systems. `architecture`
- **[SpecAugment](https://arxiv.org/abs/1904.08779)** — spectrogram masking augmentation that became standard in ASR training pipelines. `augmentation`
- **[Listen, Attend and Spell](https://arxiv.org/abs/1508.01211)** — attention-based encoder-decoder model that established end-to-end sequence-to-sequence speech recognition. `seq2seq`
- **[Sequence Transduction with RNNs](https://arxiv.org/abs/1211.3711)** — Graves' RNN-Transducer paper; the basis of most streaming ASR today. `streaming`
- **[Connectionist Temporal Classification](https://www.cs.toronto.edu/~graves/icml_2006.pdf)** — the ICML 2006 loss enabling alignment-free sequence labeling for speech. `ctc`
<!-- key papers -->

## Learning
- **[Hugging Face Audio Course](https://huggingface.co/learn/audio-course/chapter0/introduction)** — free course on audio transformers with a hands-on ASR unit. `course`
- **[Speech and Language Processing](https://web.stanford.edu/~jurafsky/slp3/)** — Jurafsky & Martin's free textbook; chapter 15 covers ASR fundamentals. `textbook`
- **[Stanford CS224S](https://web.stanford.edu/class/cs224s/)** — Stanford's spoken language processing course covering deep-learning ASR and dialogue. `course`
- **[Sequence Modeling with CTC](https://distill.pub/2017/ctc/)** — Distill's visual explainer of the CTC algorithm by Awni Hannun. `ctc`
<!-- tutorials, explainers -->

---
[← Speech Models hub](../README.md)
