# Hugging Face Trending Models Digest 2026-06-30

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-06-29 16:05 UTC

---

# Hugging Face Trending Models Digest — 2026-06-30

## Today's Highlights

This week's HuggingFace trending list is dominated by **MoE (Mixture-of-Experts) architectures** and **vision-language models**, with Qwen-based variants and DeepSeek V4-family models leading the charge. NVIDIA's new quantization format **NVFP4** appears on two major models (GLM-5.2 and Qwen3.6-35B), signaling a push toward efficient inference on enterprise hardware. The **GLM-5.2** series from zai-org and its GGUF quantizations by unsloth are attracting significant community attention, while the uncensored **Qwen3.6-35B** variant from HauhauCS has gone viral with over 3M downloads. On the specialized model front, NVIDIA's **LocateAnything-3B** for visual grounding tasks and Microsoft's **FastContext-1.0-4B** for long-context applications represent notable enterprise contributions.

---

## Trending Models by Category

### 🧠 Language Models (LLMs, chat models, instruction-tuned)

- **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** — zai-org | 2,899 likes, 133k downloads — A powerful MoE-based conversational LLM with DSA attention, trending as the flagship open-weight model in the GLM family.

- **[deepseek-ai/DeepSeek-V4-Pro-DSpark](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-DSpark)** — deepseek-ai | 205 likes, 5.5k downloads — DeepSeek's latest V4 generation with DSPark acceleration, representing the cutting edge of open-weight LLMs with published research (arxiv:2606.19348).

- **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** — HauhauCS | 2,328 likes, 3.09M downloads — An uncensored, aggressive-tuned variant of Qwen3.6-35B MoE with vision capabilities, trending massively for its unrestricted behavior and community fine-tuning.

- **[LiquidAI/LFM2.5-230M](https://huggingface.co/LiquidAI/LFM2.5-230M)** — LiquidAI | 147 likes, 15.5k downloads — A 230M-parameter liquid foundation model optimized for efficient text generation, gaining traction as a lightweight alternative.

- **[WeiboAI/VibeThinker-3B](https://huggingface.co/WeiboAI/VibeThinker-3B)** — WeiboAI | 746 likes, 63k downloads — A 3B math-specialized reasoning model built on Qwen2, trending for strong chain-of-thought performance at a compact size.

- **[microsoft/FastContext-1.0-4B-SFT](https://huggingface.co/microsoft/FastContext-1.0-4B-SFT)** — microsoft | 369 likes, 7k downloads — A 4B SFT-tuned model for long-context tasks with a built-in "Explorer SubAgent" capability, marking Microsoft's entry into efficient long-context LLMs.

### 🎨 Multimodal & Generation (image, video, audio, text-to-X)

- **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)** — baidu | 1,338 likes, 363k downloads — A universal OCR model for image-to-text extraction, trending for Baidu's enterprise-grade accuracy and massive download volume.

- **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)** — empero-ai | 893 likes, 908k downloads — A 9B Qwen3.5-based image-text-to-text model with 1M context, GGUF-quantized for local deployment and highly downloaded for its Claude-inspired mythos training.

- **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** — nvidia | 2,465 likes, 728k downloads — A 3B vision-language model for object localization and image feature extraction, trending for NVIDIA's production-quality zero-shot grounding capability.

- **[krea/Krea-2-Turbo](https://huggingface.co/krea/Krea-2-Turbo)** — krea | 390 likes, 38k downloads — A diffusion-based text-to-image model with turbo optimization, building on Krea-2-Raw for faster generation.

- **[fal/LTX-2.3-3DREAL-LoRA](https://huggingface.co/fal/LTX-2.3-3DREAL-LoRA)** — fal | 110 likes, 0 downloads — A LoRA adapter for LTX-2.3 enabling 3D-realistic image-to-video generation, a niche but novel contribution.

- **[nvidia/nemotron-3.5-asr-streaming-0.6b](https://huggingface.co/nvidia/nemotron-3.5-asr-streaming-0.6b)** — nvidia | 739 likes, 76k downloads — A 0.6B streaming ASR model with NeMo integration, trending for real-time speech recognition at a compact size.

### 🔧 Specialized Models (code, math, medical, embeddings)

- **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)** — yuxinlu1 | 2,496 likes, 562k downloads — A Gemma-4-based coding model with Fable5 fine-tuning and composer architecture, GGUF-quantized and extremely popular for developer use.

- **[Chunjiang-Intelligence/DeepSeek-v4-Fable](https://huggingface.co/Chunjiang-Intelligence/DeepSeek-v4-Fable)** — Chunjiang-Intelligence | 126 likes, 1.5k downloads — A DeepSeek V4 fine-tune specialized for cybersecurity applications, representing a vertical domain adaptation of a flagship model.

- **[yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF)** — yuxinlu1 | 830 likes, 241k downloads — An agentic variant of Gemma-4-12B with terminal-use optimization, trending for autonomous coding workflows.

### 📦 Fine-tunes & Quantizations (community fine-tunes, GGUF, AWQ)

- **[deepreinforce-ai/Ornith-1.0-35B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF)** — deepreinforce-ai | 450 likes, 124k downloads — A 35B Qwen3.5 MoE model GGUF-quantized with MIT license and endpoints support, heavy download volume.

- **[unsloth/GLM-5.2-GGUF](https://huggingface.co/unsloth/GLM-5.2-GGUF)** — unsloth | 456 likes, 164k downloads — Unsloth's GGUF quantization of GLM-5.2, critical for enabling local deployment of this popular MoE model.

- **[nvidia/Qwen3.6-35B-A3B-NVFP4](https://huggingface.co/nvidia/Qwen3.6-35B-A3B-NVFP4)** — nvidia | 376 likes, 5.39M downloads — NVIDIA's NVFP4-quantized version of Qwen3.6-35B MoE, the highest-download model this week, optimized for NVIDIA hardware with ModelOptimizer.

- **[nvidia/GLM-5.2-NVFP4](https://huggingface.co/nvidia/GLM-5.2-NVFP4)** — nvidia | 163 likes, 82k downloads — NVIDIA's NVFP4 quantization of GLM-5.2, enabling efficient inference of this MoE model on enterprise GPUs.

- **[HauhauCS/Gemma4-12B-QAT-Uncensored-HauhauCS-Balanced](https://huggingface.co/HauhauCS/Gemma4-12B-QAT-Uncensored-HauhauCS-Balanced)** — HauhauCS | 104 likes, 46k downloads — A QAT-quantized, uncensored Gemma4-12B vision-language model balancing performance and safety guardrails.

- **[unsloth/Qwen-AgentWorld-35B-A3B-GGUF](https://huggingface.co/unsloth/Qwen-AgentWorld-35B-A3B-GGUF)** — unsloth | 104 likes, 117k downloads — Unsloth's GGUF of Qwen's AgentWorld world-model MoE, enabling local agent simulation.

---

## Ecosystem Signal

The **MoE trend is undeniable**: nearly half of this week's top-30 models use Mixture-of-Experts architectures (GLM-5.2, Qwen3.5/3.6 MoE, Ornith, DeepSeek V4 MoE variants). The community is gravitating toward models that offer dense-model quality at inference costs proportional to active parameters. **GGUF quantization continues as the dominant local deployment format**, though NVIDIA's **NVFP4** emerges as a serious hardware-native alternative, already generating 5.4M downloads for the Qwen3.6 target alone. The **uncensored model sub-trend** is strong, with HauhauCS pushing multiple uncensored variants to viral download numbers, suggesting demand for unrestricted chatbots. **Vision-language convergence** is accelerating: 8 of the 30 models process images alongside text, a sharp increase from prior months. Enterprise players (NVIDIA, Microsoft, Baidu) are releasing production-quality specialized models rather than general-purpose LLMs, while community creators (HauhauCS, yuxinlu1, deepreinforce-ai) dominate the fine-tune and quantization space. The **LiquidAI LFM2.5** and **WeiboAI VibeThinker** show that sub-3B models remain a vital part of the ecosystem, competing with larger peers on specific benchmarks.

---

## Worth Exploring

1. **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** — A rare open-weight object localization model at only 3B parameters with NVIDIA's quality guarantee. Essential for any computer vision pipeline needing zero-shot grounding without heavy compute.

2. **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)** — The most liked coding-specific model this week with 2.5k likes, combining Gemma-4's strong base with Fable5 fine-tuning. GGUF format means it's immediately usable with llama.cpp for local coding assistance.

3. **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** — With 3M downloads, this is the week's viral model. Studying its aggressive fine-tuning recipe reveals what the community finds lacking in safety-filtered models, and its Qwen3.6 MoE backbone represents the latest generation of efficient vision-language LLMs.

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*