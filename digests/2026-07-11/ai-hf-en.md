# Hugging Face Trending Models Digest 2026-07-11

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-07-11 01:47 UTC

---

# Hugging Face Trending Models Digest – 2026-07-11

## 1. Today's Highlights

This week’s trending leaderboard is defined by a surge in **vision-language MoE models** and aggressive **GGUF quantization** for deployment-scale adoption. **zai-org/GLM-5.2** (3,785 likes) leads the pack as a massive conversational MoE, while **nvidia/LocateAnything-3B** (2,701 likes) signals enterprise demand for grounded vision-language tools. The **Qwen3.6 ecosystem** dominates the fine-tune and quantization wave, with **HauhauCS/Qwen3.6-35B-A3B-Uncensored** (2,623 likes, 2.66M downloads) and **unsloth/Qwen3.6-27B-MTP-GGUF** (1,036 likes, 2.9M downloads) showing peak community engagement. Meanwhile, **empero-ai/Qwythos-9B-Claude-Mythos-5-1M** and its GGUF sibling represent a new trend: story-driven reasoning models fused with proprietary system signals. The presence of **baidu/Unlimited-OCR** (1.9K likes, 1.3M downloads) and **nvidia/NVIDIA-Nemotron-Labs-3-Puzzle** reminds us that OCR and puzzle-solving specialty models remain strong vertical bets.

---

## 2. Trending Models

### 🧠 Language Models (LLMs, chat models, instruction-tuned)

- **[tencent/Hy3](https://huggingface.co/tencent/Hy3)** – tencent | 664 likes, 6.9K downloads  
  A next-gen Hunyuan-generation text model (Hy v3) optimized for scalable conversational AI, trending due to Tencent's ecosystem push.

- **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** – zai-org | 3,785 likes, 392.7K downloads  
  A massive MoE conversational model (GLM architecture with DSA routing) gaining traction for its instruction quality and open-weight availability.

- **[InternScience/Agents-A1](https://huggingface.co/InternScience/Agents-A1)** – InternScience | 471 likes, 25.8K downloads  
  A Qwen3.5-based MoE agent model, notable for blending image-text understanding with text generation.

- **[deepreinforce-ai/Ornith-1.0-35B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF)** – deepreinforce-ai | 835 likes, 1.09M downloads  
  A 35B MIT-licensed text model with GGUF format, heavily downloaded for its efficient reasoning and permissive license.

- **[mistralai/Leanstral-1.5-119B-A6B](https://huggingface.co/mistralai/Leanstral-1.5-119B-A6B)** – mistralai | 184 likes, 315 downloads  
  Mistral's latest 119B-parameter sparse MoE (6B active) with vLLM support, trending as a cutting-edge open-weight alternative.

- **[deepseek-ai/DeepSeek-V4-Pro-DSpark](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-DSpark)** – deepseek-ai | 463 likes, 33.1K downloads  
  DeepSeek's V4 Pro variant with DSpark acceleration, driving interest in distributed inference.

- **[SupraLabs/Supra-Router-51M](https://huggingface.co/SupraLabs/Supra-Router-51M)** – SupraLabs | 86 likes, 1.2K downloads  
  A tiny 51M parameter router model for intelligent model selection, interesting for agent orchestration.

---

### 🎨 Multimodal & Generation (image, video, audio, text-to-X)

- **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)** – baidu | 1,921 likes, 1.32M downloads  
  A feature-extraction OCR model from Baidu, trending for its zero-shot document understanding at scale.

- **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** – nvidia | 2,701 likes, 1.46M downloads  
  A 3B vision-language grounding model (object localization + description), highly popular for enterprise visual AI.

- **[krea/Krea-2-Turbo](https://huggingface.co/krea/Krea-2-Turbo)** – krea | 575 likes, 164.5K downloads  
  A turbo-charged text-to-image diffusion model built on Krea-2-Raw, trending for fast generation quality.

- **[OpenMOSS-Team/MOSS-Transcribe-Diarize](https://huggingface.co/OpenMOSS-Team/MOSS-Transcribe-Diarize)** – OpenMOSS-Team | 98 likes, 5.9K downloads  
  An audio-text-to-text model combining transcription with speaker diarization, useful for meeting analysis.

- **[open-gigaai/Giga-World-1](https://huggingface.co/open-gigaai/Giga-World-1)** – open-gigaai | 118 likes, 0 downloads  
  An early-release Apache-2.0 world generation model using diffusers, capturing video generation interest.

- **[robbyant/lingbot-video-moe-30b-a3b](https://huggingface.co/robbyant/lingbot-video-moe-30b-a3b)** – robbyant | 76 likes, 317 downloads  
  A 30B MoE video model (3B active) with LingBotVideoPipeline, trending for efficient video generation.

- **[Alissonerdx/LTX-Best-Face-ID](https://huggingface.co/Alissonerdx/LTX-Best-Face-ID)** – Alissonerdx | 84 likes, 0 downloads  
  An identity-preserving text-to-video model (LTX-2), driving interest in consistent character generation.

---

### 🔧 Specialized Models (code, math, medical, embeddings)

- **[google/tabfm-1.0.0-pytorch](https://huggingface.co/google/tabfm-1.0.0-pytorch)** – google | 345 likes, 18.6K downloads  
  Google's tabular foundation model for zero-shot classification and regression, a rare high-quality tabular AI release.

- **[nvidia/NVIDIA-Nemotron-Labs-3-Puzzle-75B-A9B-NVFP4](https://huggingface.co/nvidia/NVIDIA-Nemotron-Labs-3-Puzzle-75B-A9B-NVFP4)** – nvidia | 99 likes, 23.4K downloads  
  A 75B puzzle-solving MoE model with NVFP4 quantization, pushing reasoning into specialized domains.

- **[nvidia/Nemotron-Labs-Audex-30B-A3B](https://huggingface.co/nvidia/Nemotron-Labs-Audex-30B-A3B)** – nvidia | 94 likes, 576 downloads  
  An audex (audio+text) reasoning MoE, representing Nvidia's broader multimodal push.

---

### 📦 Fine-tunes & Quantizations (community fine-tunes, GGUF, AWQ)

- **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)** – empero-ai | 1,976 likes, 1.91M downloads  
  A GGUF-quantized 9B mythos-level reasoning model fusing Qwen3.5 with Claude-style outputs, massively popular for role-play and reasoning.

- **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** – HauhauCS | 2,623 likes, 2.66M downloads  
  An uncensored MoE vision-language GGUF variant of Qwen3.6, the most downloaded model this week, appealing to unrestricted use cases.

- **[yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF)** – yuxinlu1 | 1,134 likes, 427.7K downloads  
  A highly tuned Gemma-4-based GGUF for agentic coding and terminal use, popular with developer tooling communities.

- **[unsloth/DeepSeek-V4-Flash-GGUF](https://huggingface.co/unsloth/DeepSeek-V4-Flash-GGUF)** – unsloth | 124 likes, 31.9K downloads  
  Unsloth's flash-quantized DeepSeek-V4, highlighting the continued appetite for efficient large-model deployment.

- **[unsloth/Qwen3.6-27B-MTP-GGUF](https://huggingface.co/unsloth/Qwen3.6-27B-MTP-GGUF)** – unsloth | 1,036 likes, 2.9M downloads  
  A Qwen3.6 vision-language GGUF with multi-token prediction (MTP), top-2 in downloads due to unsloth's optimization reputation.

- **[nvidia/Qwen3.6-27B-NVFP4](https://huggingface.co/nvidia/Qwen3.6-27B-NVFP4)** – nvidia | 336 likes, 787.7K downloads  
  Nvidia's NVFP4-quantized version of Qwen3.6-27B, bridging enterprise deployment with community model popularity.

- **[AliesTaha/fable-traces](https://huggingface.co/AliesTaha/fable-traces)** – AliesTaha | 198 likes, 4.9K downloads  
  A Qwen3-based instruct fine-tune for narrative trace generation (fable-style), reflecting niche story-generation demand.

- **[conradlocke/krea2-identity-edit](https://huggingface.co/conradlocke/krea2-identity-edit)** – conradlocke | 161 likes, 0 downloads  
  A ComfyUI LoRA for identity-based image editing on Krea-2-Raw, trending for creative workflows.

- **[GnLOLot/MiniCPM5-1B-Claude-Opus-Fable5-Thinking-GGUF](https://huggingface.co/GnLOLot/MiniCPM5-1B-Claude-Opus-Fable5-Thinking-GGUF)** – GnLOLot | 157 likes, 9K downloads  
  A tiny 1B GGUF reasoning model combining MiniCPM5 with Claude-style thinking, popular for resource-constrained reasoning.

- **[froggeric/Qwen-Fixed-Chat-Templates](https://huggingface.co/froggeric/Qwen-Fixed-Chat-Templates)** – froggeric | 836 likes, 0 downloads  
  A utility dataset fixing Qwen3.5 chat templates (MLX/Jinja), vital metadata for the Qwen ecosystem.

- **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M)** – empero-ai | 761 likes, 184.3K downloads  
  The base (non-quantized) version of the Qwythos mythos model, equally popular for creative prompting.

---

## 3. Ecosystem Signal

The Hugging Face ecosystem is experiencing a clear **Qwen3.6+MoE consolidation**: models from multiple authors (HauhauCS, unsloth, nvidia, empero-ai) are all building on the Qwen3.5/3.6 backbone, suggesting it has become the preferred base for fine-tuning and quantization. **Mixture-of-Experts (MoE)** architectures dominate the top 10, with GLM-5.2, Agents-A1, Qwen3.6-35B-A3B, and Nemotron all adopting sparse activation—confirming the industry shift to efficiency at scale.

**GGUF quantization is now the default deployment format**, with 8 of the top 15 downloaded models using it. Unsloth, in particular, has cemented its role as the go-to quantization provider (two entries in top downloads). The **"uncensored" and "mythos" trend** (Qwythos, HauhauCS) indicates strong demand for unaligned creative and role-play models, sitting alongside enterprise giants like nvidia's LocateAnything and Baidu's Unlimited-OCR. Open-weight models (DeepSeek-V4, Mistral Leanstral, Google TabFM) compete with proprietary-style fine-tunes, but the market clearly rewards **accessibility (GGUF) and specificity (uncensored, agentic)** over raw parameter count.

---

## 4. Worth Exploring

1. **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** – With 2.7K likes and 1.46M downloads in a week, this 3B model sets a new bar for efficient vision-language grounding. It’s a prime candidate for real-world applications like visual search, document parsing, or robotic picking—small enough to fine-tune, powerful enough to use zero-shot.

2. **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** – The highest-downloaded model (2.66M) signals where the community is voting with their GPUs. Whether for research on unconstrained generation, creative writing, or testing alignment boundaries, this is the week's most impactful community release.

3. **[unsloth/Qwen3.6-27B-MTP-GGUF](https://huggingface.co/unsloth/Qwen3.6-27B-MTP-GGUF)** – Multi-token prediction (MTP) is an emerging technique to improve inference throughput, and unsloth's GGUF packaging makes it immediately usable. At 2.9M downloads, it’s the second most downloaded model and arguably the most practical for production deployment this week.

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*