# Hugging Face Trending Models Digest 2026-07-16

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-07-16 01:46 UTC

---

# 🤗 Hugging Face Trending Models Digest — 2026-07-16

## Today's Highlights

A massive wave of Qwen 3.x derivatives dominates today's trending board, with **Qwythos-9B** variants from empero-ai accumulating over 2 million downloads and a new **Qwen3.6-35B-A3B** MoE uncensored model pulling in 2.4 million. The **GLM-5.2** from zai-org (3,998 likes) and **Hy3** from Tencent reflect growing MoE and proprietary-derivative momentum. Ternary and sub-2-bit quantization pushes continue via prism-ml's **Ternary-Bonsai-27B**, while infrastructure models like **Needle** (function-calling) and **MOSS-Transcribe-Diarize** (audio pipeline) signal a maturing ecosystem beyond pure chat. Unsloth's **Qwen3.6-27B-NVFP4** with 1.6M downloads shows hardware-aware quantization is now mainstream.

---

## Trending Models

### 🧠 Language Models (LLMs, Chat, Instruction-Tuned)

- **[GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** — zai-org · 3,998 likes · 489K downloads  
  A large-scale MoE conversational model with DSA routing, trending due to its strong open-weight alternative to proprietary systems.

- **[Hy3](https://huggingface.co/tencent/Hy3)** — tencent · 800 likes · 10K downloads  
  Hunyuan's next-generation dense LLM, gaining traction as Tencent's premier open-weight text-generation offering.

- **[InternScience/Agents-A1](https://huggingface.co/InternScience/Agents-A1)** — InternScience · 556 likes · 30K downloads  
  Qwen3.5-MoE based model optimized for agentic workflows, trending for its sparse activation (35B total, ~3.5B active).

- **[yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF)** — yuxinlu1 · 1,198 likes · 468K downloads  
  Gemma 4 fine-tune for coding and terminal agentic tasks, trending for its extreme parameter overhead (3.5x tau²) and agentic focus.

- **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** — HauhauCS · 2,760 likes · 2.4M downloads  
  An uncensored Qwen3.6 MoE variant (35B total, 3B active) with aggressive alignment removal, extremely popular for roleplay and creative writing.

- **[deepreinforce-ai/Ornith-1.0-35B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF)** — deepreinforce-ai · 894 likes · 1.5M downloads  
  MIT-licensed 35B GGUF, trending for its permissive license and strong general reasoning performance.

- **[nvidia/Nemotron-Labs-Audex-30B-A3B](https://huggingface.co/nvidia/Nemotron-Labs-Audex-30B-A3B)** — nvidia · 156 likes · 1.3K downloads  
  Nvidia's new MoE architecture with 30B total / 3B active parameters, notable for Nvidia's direct open-weight release.

- **[GnLOLot/MiniCPM5-1B-Claude-Opus-Fable5-Thinking-GGUF](https://huggingface.co/GnLOLot/MiniCPM5-1B-Claude-Opus-Fable5-Thinking-GGUF)** — GnLOLot · 250 likes · 89K downloads  
  A 1B parameter GGUF distilled from Claude Opus with chain-of-thought capabilities, trending as an ultra-efficient thinking model.

### 🎨 Multimodal & Generation (Image, Video, Audio, Text-to-X)

- **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)** — empero-ai · 2,216 likes · 2M downloads  
  A Qwen3.5-based multimodal model fine-tuned on Claude Mythos data, trending massively due to its strong vision-language reasoning and extreme quantization variety.

- **[bottlecapai/ThinkingCap-Qwen3.6-27B](https://huggingface.co/bottlecapai/ThinkingCap-Qwen3.6-27B)** — bottlecapai · 366 likes · 6.2K downloads  
  Qwen3.6 image-text-to-text model optimized for chain-of-thought reasoning in vision tasks.

- **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)** — baidu · 2,002 likes · 1.7M downloads  
  Baidu's large-scale OCR model supporting unlimited-length document recognition, trending for its practical enterprise utility.

- **[ATH-MaaS/OvisOCR2](https://huggingface.co/ATH-MaaS/OvisOCR2)** — ATH-MaaS · 118 likes · 745 downloads  
  Qwen3.5-based OCR model, complementary to Unlimited-OCR with a focus on structured document understanding.

- **[thinkingmachines/Inkling](https://huggingface.co/thinkingmachines/Inkling)** — thinkingmachines · 361 likes · 0 downloads  
  A novel image-text-to-text and audio-text-to-text multimodal model, trending for its cross-modal architecture.

- **[open-gigaai/Giga-World-1](https://huggingface.co/open-gigaai/Giga-World-1)** — open-gigaai · 135 likes · 0 downloads  
  Apache-2.0 licensed world model using Diffusers, trending as an open alternative to video generation models.

- **[robbyant/lingbot-world-v2-14b-causal-fast](https://huggingface.co/robbyant/lingbot-world-v2-14b-causal-fast)** — robbyant · 99 likes · 0 downloads  
  A 14B causal world model for image-to-video generation, trending for its fast inference architecture.

- **[robbyant/lingbot-video-moe-30b-a3b](https://huggingface.co/robbyant/lingbot-video-moe-30b-a3b)** — robbyant · 111 likes · 700 downloads  
  MoE video generation model (30B total, 3B active) with custom Diffusers pipeline.

- **[mgwr/M87](https://huggingface.co/mgwr/M87)** — mgwr · 127 likes · 2.4K downloads  
  A Krea-2-Turbo LoRA for text-to-image, trending in the community for quality image generation on top of Krea's base.

- **[Alissonerdx/LTX-Best-Face-ID](https://huggingface.co/Alissonerdx/LTX-Best-Face-ID)** — Alissonerdx · 154 likes · 0 downloads  
  Identity-preserving LoRA for LTX Video, enabling reference-to-video with consistent face generation.

- **[OpenMOSS-Team/MOSS-Transcribe-Diarize](https://huggingface.co/OpenMOSS-Team/MOSS-Transcribe-Diarize)** — OpenMOSS-Team · 215 likes · 65K downloads  
  Audio-text-to-text transcription and speaker diarization model, trending as a practical speech processing pipeline.

### 🔧 Specialized Models (Code, Function-Calling, Embeddings)

- **[Cactus-Compute/needle](https://huggingface.co/Cactus-Compute/needle)** — Cactus-Compute · 236 likes · 571 downloads  
  A JAX-based model for agentic function calling and tool use, trending for its lightweight yet powerful tool-use capabilities.

### 📦 Fine-tunes & Quantizations (Community Derivatives, GGUF, AWQ)

- **[prism-ml/Ternary-Bonsai-27B-gguf](https://huggingface.co/prism-ml/Ternary-Bonsai-27B-gguf)** — prism-ml · 474 likes · 23 downloads  
  The first ternary (2-bit) quantized 27B model, trending for pushing quantization boundaries to extreme compression.

- **[prism-ml/Bonsai-27B-gguf](https://huggingface.co/prism-ml/Bonsai-27B-gguf)** — prism-ml · 269 likes · 513 downloads  
  1-bit quantized 27B model, complementary to the ternary variant and attracting extreme-efficiency enthusiasts.

- **[empero-ai/Qwythos-9B-v2-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-v2-GGUF)** — empero-ai · 144 likes · 70K downloads  
  Second generation Qwythos GGUF quantization, iterating on the massively popular v1.

- **[froggeric/Qwen-Fixed-Chat-Templates](https://huggingface.co/froggeric/Qwen-Fixed-Chat-Templates)** — froggeric · 917 likes · 0 downloads  
  Corrected Jinja2 chat templates for Qwen 3.5 models, trending as essential infrastructure for proper Qwen deployments.

- **[AngelSlim/Hy3-GGUF](https://huggingface.co/AngelSlim/Hy3-GGUF)** — AngelSlim · 109 likes · 0 downloads  
  Community GGUF quantization of Tencent's Hy3, Apache-2.0 licensed.

- **[unsloth/Qwen3.6-27B-NVFP4](https://huggingface.co/unsloth/Qwen3.6-27B-NVFP4)** — unsloth · 208 likes · 1.5M downloads  
  Nvidia FP4 quantization of Qwen3.6 by Unsloth, trending for enabling high-quality inference on consumer GPUs.

- **[jlnsrk/GLM-5.2-colibri-int4](https://huggingface.co/jlnsrk/GLM-5.2-colibri-int4)** — jlnsrk · 111 likes · 2.1K downloads  
  INT4 quantization of GLM-5.2 using expert-streaming for CPU inference, trending for MoE-on-CPU practicality.

---

## Ecosystem Signal

Several clear trends emerge from today's leaderboard.

**Qwen 3.x Family Dominance** — Nearly half the top 30 models derive from Qwen 3.5 or 3.6, confirming it as the most active fine-tuning base in the open ecosystem. The explosion of Qwythos variants (2M+ downloads) and the uncensored Qwen3.6-35B (2.4M) indicate strong community demand for lightweight, multimodal MoE architectures.

**MoE Becomes Default** — Models like **GLM-5.2**, **Agents-A1**, and **HauhauCS/Qwen3.6** all use mixture-of-experts with typical 10:1 sparsity ratios. The 30B-A3B pattern (30B total, 3B active) is becoming the sweet spot for local deployment, balancing capability with memory efficiency.

**Extreme Quantization Frontier** — prism-ml's binary (1-bit) and ternary (2-bit) **Bonsai** models at 27B represent a new frontier in aggressive compression. While adoption remains niche (23-513 downloads), the buzz (474 likes) suggests growing interest in sub-4-bit techniques for edge deployment.

**Infrastructure Maturation** — The presence of **Qwen-Fixed-Chat-Templates** (917 likes, 0 downloads), **Needle** for function-calling, and **MOSS-Transcribe-Diarize** for audio pipelines signals a shift from raw model releases toward deployment tooling. The ecosystem is maturing beyond "just the model" to include templates, pipelines, and quantization formats.

**Open-Weight Leadership** — Nvidia, Baidu, and Tencent all contributed top-tier open-weight releases, suggesting that even major proprietary labs are investing in open-weight release strategies as competitive differentiators.

---

## Worth Exploring

1. **[Ternary-Bonsai-27B-gguf](https://huggingface.co/prism-ml/Ternary-Bonsai-27B-gguf)** — The first ternary quantized 27B model is worth studying for anyone interested in extreme model compression. If 2-bit can preserve reasonable quality at 27B, it opens doors for running capable models on phones or low-end hardware. The 23 downloads are low, but the 474 likes indicate the community is watching closely — this is a research frontier worth hands-on evaluation.

2. **[yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF)** — Despite the unwieldy name, this is a serious attempt at Gemma 4 fine-tuning for agentic and terminal use cases. The 3.5x tau² parameter overhead is an unusual architectural choice, and its 1,198 likes suggest it performs well. Worth benchmarking against Qwen-based agents for code generation and tool-use tasks.

3. **[Cactus-Compute/needle](https://huggingface.co/Cactus-Compute/needle)** — As function-calling and tool-use become the primary interface for LLM-enabled applications, Needle's JAX-based approach offers a lightweight, specialized alternative to general-purpose Moe models. Its 236 likes and 0 downloads (likely pre-release) make it an under-explored candidate for agentic workflows.

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*