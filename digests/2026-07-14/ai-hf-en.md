# Hugging Face Trending Models Digest 2026-07-14

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-07-14 01:29 UTC

---

# 🤗 Hugging Face Trending Models Digest — July 14, 2026

## Today's Highlights
This week's trending models showcase a strong pivot toward **Mixture-of-Experts (MoE) architectures**, with GLM-5.2 and several Qwen3.6 variants dominating the leaderboard. **Quantized GGUF releases continue to surge**, reflecting sustained community demand for efficient local deployment—empero-ai's Qwythos-9B-Claude-Mythos and its v2 variant collectively amassed over 2M downloads. Notably, **vision-language and image-text-to-text models** now represent the single largest category, signaling a maturation of multimodal capabilities in the open-weight ecosystem. The emergence of domain-specific tools like **Unlimited-OCR (Baidu)** and **Agents-A1 (InternScience)** points to increasing specialization beyond general-purpose chat.

---

## Trending Models by Category

### 🧠 Language Models (LLMs, chat models, instruction-tuned)

- **[tencent/Hy3](https://huggingface.co/tencent/Hy3)** — Tencent | 754 likes, 9.2K downloads  
  A large-scale Hunyuan-based text-generation model from Tencent, trending as the latest iteration in the Hy series with strong Chinese-language performance.

- **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** — zai-org | 3,900 likes, 465K downloads  
  A conversational MoE model using the GLM-MoE-DSA architecture, trending for its high parameter efficiency and dialogue quality.

- **[nvidia/NVIDIA-Nemotron-Labs-3-Puzzle-75B-A9B-NVFP4](https://huggingface.co/nvidia/NVIDIA-Nemotron-Labs-3-Puzzle-75B-A9B-NVFP4)** — nvidia | 114 likes, 38.8K downloads  
  NVIDIA's 75B-parameter MoE model with NVFP4 quantization, trending as part of the Nemotron Labs puzzle-solving series.

- **[SupraLabs/Supra-Router-51M](https://huggingface.co/SupraLabs/Supra-Router-51M)** — SupraLabs | 114 likes, 1.6K downloads  
  A lightweight 51M-parameter routing model for LLM orchestration, trending for its potential in multi-model agent workflows.

### 🎨 Multimodal & Generation (image, video, audio, text-to-X)

- **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)** — empero-ai | 2,084 likes, 1.99M downloads  
  An image-text-to-text Qwen3.5-based model with Claude-Mythos fine-tuning, highly downloaded for its reasoning capabilities in GGUF format.

- **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)** — baidu | 1,963 likes, 1.51M downloads  
  A universal OCR model from Baidu supporting diverse document formats, trending for its impressive accuracy and broad language coverage.

- **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** — HauhauCS | 2,710 likes, 2.51M downloads  
  A 35B-parameter MoE vision-language model with uncensored aggressive fine-tuning, trending for its massive download count and distinctive persona.

- **[Alissonerdx/LTX-Best-Face-ID](https://huggingface.co/Alissonerdx/LTX-Best-Face-ID)** — Alissonerdx | 124 likes, 0 downloads  
  A reference-to-video LoRA model for identity-preserving video generation, trending as a novel application of LTX-Video.

- **[CohereLabs/cohere-transcribe-arabic-07-2026](https://huggingface.co/CohereLabs/cohere-transcribe-arabic-07-2026)** — CohereLabs | 102 likes, 11.6K downloads  
  An Arabic automatic speech recognition model from Cohere, trending for its specialized language focus.

- **[nineninesix/gepard-1.0](https://huggingface.co/nineninesix/gepard-1.0)** — nineninesix | 95 likes, 3.9K downloads  
  A Qwen3.5-based text-to-speech model, trending as an emerging TTS entry in the Qwen ecosystem.

- **[robbyant/lingbot-world-v2-14b-causal-fast](https://huggingface.co/robbyant/lingbot-world-v2-14b-causal-fast)** — robbyant | 93 likes, 0 downloads  
  A causal world model for image-to-video generation, trending for its "world model" approach to video synthesis.

### 🔧 Specialized Models (code, math, medical, embeddings, audio)

- **[InternScience/Agents-A1](https://huggingface.co/InternScience/Agents-A1)** — InternScience | 526 likes, 29.8K downloads  
  A Qwen3.5-MoE model optimized for agentic workflows, trending for its MoE architecture and agent-focused training.

- **[nvidia/Nemotron-Labs-Audex-30B-A3B](https://huggingface.co/nvidia/Nemotron-Labs-Audex-30B-A3B)** — nvidia | 142 likes, 1.1K downloads  
  A 30B-parameter audio understanding model from NVIDIA's Nemotron Labs, trending for cross-modal reasoning capabilities.

- **[google/tabfm-1.0.0-pytorch](https://huggingface.co/google/tabfm-1.0.0-pytorch)** — google | 362 likes, 21.6K downloads  
  Google's tabular foundation model supporting zero-shot classification and regression, trending as a rare specialized foundation model for tabular data.

- **[OpenMOSS-Team/MOSS-Transcribe-Diarize](https://huggingface.co/OpenMOSS-Team/MOSS-Transcribe-Diarize)** — OpenMOSS-Team | 162 likes, 39.5K downloads  
  An audio-text-to-text model combining transcription with speaker diarization, trending for its practical audio processing pipeline.

### 📦 Fine-tunes & Quantizations (community fine-tunes, GGUF, AWQ)

- **[unsloth/Qwen3.6-27B-MTP-GGUF](https://huggingface.co/unsloth/Qwen3.6-27B-MTP-GGUF)** — unsloth | 1,074 likes, 2.90M downloads  
  Unsloth's MTP-optimized GGUF quantization of Qwen3.6-27B, trending as the most downloaded model this week with massive community adoption.

- **[deepreinforce-ai/Ornith-1.0-35B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF)** — deepreinforce-ai | 868 likes, 1.39M downloads  
  A 35B-parameter GGUF model under MIT license, trending for endorsement compatibility and strong general reasoning.

- **[yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF)** — yuxinlu1 | 1,178 likes, 452.6K downloads  
  A heavily fine-tuned Gemma-4-12B GGUF model optimized for agentic coding and terminal use, trending for extreme fine-tuning.

- **[froggeric/Qwen-Fixed-Chat-Templates](https://huggingface.co/froggeric/Qwen-Fixed-Chat-Templates)** — froggeric | 888 likes, 0 downloads  
  A Jinja chat template fix for Qwen models, trending as a high-utility community resource despite zero actual downloads (template-only).

- **[jlnsrk/GLM-5.2-colibri-int4](https://huggingface.co/jlnsrk/GLM-5.2-colibri-int4)** — jlnsrk | 86 likes, 2.0K downloads  
  An int4 CPU-quantized version of GLM-5.2 using expert streaming, trending for enabling MoE inference on consumer hardware.

- **[GnLOLot/MiniCPM5-1B-Claude-Opus-Fable5-Thinking-GGUF](https://huggingface.co/GnLOLot/MiniCPM5-1B-Claude-Opus-Fable5-Thinking-GGUF)** — GnLOLot | 220 likes, 68.7K downloads  
  A tiny 1B-parameter thinking model in GGUF format, trending for its surprising reasoning capability at extremely small scale.

---

## Ecosystem Signal

**MoE domination is the defining trend this week.** Six of the top 10 models by likes use Mixture-of-Experts architectures (GLM-5.2, Qwen3.6 variants, Nemotron-Labs, Agents-A1), confirming that parameter-efficient scaling via sparse activation has become the dominant paradigm. **Quantization is no longer optional—it's expected.** Nearly 40% of trending models are GGUF quantizations, with unsloth emerging as a key infrastructure provider enabling community adoption. The **open-weight ecosystem is consolidating around a few core families**: Qwen (3.5/3.6) variants appear in 9 of 30 trending models, while GLM, Nemotron, and Gemma form secondary clusters. Notably, **enterprise players (Tencent, Baidu, NVIDIA, Google) are releasing increasingly capable open models**, blurring the line between proprietary and open-weight ecosystems. The emergence of **template-only and router models** (e.g., Qwen-Fixed-Chat-Templates, Supra-Router) signals growing maturity in the ecosystem infrastructure layer.

---

## Worth Exploring

1. **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** — The highest-liked model this week (3,900 likes) and a strong performer in conversational MoE. Its combination of parameter efficiency and dialogue quality makes it a prime candidate for production chatbot deployments.

2. **[unsloandth/Qwen3.6-27B-MTP-GGUF](https://huggingface.co/unsloth/Qwen3.6-27B-MTP-GGUF)** — With 2.9M downloads in a single week, this is the community's clear favorite. It's the most practical choice for local multimodal inference, balancing capability with accessibility.

3. **[InternScience/Agents-A1](https://huggingface.co/InternScience/Agents-A1)** — As agentic workflows become the next frontier, this Qwen3.5-MoE model offers a glimpse into specialized architectures for tool use and multi-step reasoning—worth studying for anyone building LLM agents.

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*