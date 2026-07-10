# Hugging Face Trending Models Digest 2026-07-10

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-07-10 01:59 UTC

---

# 🤗 Hugging Face Trending Models Digest — July 10, 2026

## 1. Today's Highlights

This week's trending models reveal a clear shift toward **multi-modal MoE architectures**, with Qwen3.5/3.6 variants dominating the leaderboard alongside NVIDIA's specialized vision models. The standout is **nvidia/LocateAnything-3B** (2,687 likes), a compact but powerful object localization model, reflecting growing demand for precise vision AI. In the language space, **zai-org/GLM-5.2** (3,729 likes) leads by sheer community enthusiasm, while **HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive** (2,596 likes) showcases the ongoing appetite for uncensored, high-performance MoE models. Quantization activity remains intense, with GGUF variants of Qwen3.6 and DeepSeek-V4 seeing massive download numbers.

## 2. Trending Models by Category

### 🧠 Language Models (LLMs, chat models, instruction-tuned)

- **[tencent/Hy3](https://huggingface.co/tencent/Hy3)** — tencent | 615 likes, 5,572 downloads  
  Hunyuan's next-gen text-generation model, trending as Tencent's flagship open-weight release.

- **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** — zai-org | 3,729 likes, 362,300 downloads  
  A conversational GLM MoE model with DSA architecture, the week's most-liked pure LLM release.

- **[mistralai/Leanstral-1.5-119B-A6B](https://huggingface.co/mistralai/Leanstral-1.5-119B-A6B)** — mistralai | 179 likes, 258 downloads  
  Mistral's efficient 119B MoE with 6B active parameters, built on their Leanstral-2603 foundation.

- **[deepseek-ai/DeepSeek-V4-Pro-DSpark](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-DSpark)** — deepseek-ai | 458 likes, 29,230 downloads  
  DeepSeek's V4 Pro with DSpark optimization, backed by research paper arxiv:2606.19348.

- **[nvidia/NVIDIA-Nemotron-Labs-3-Puzzle-75B-A9B-NVFP4](https://huggingface.co/nvidia/NVIDIA-Nemotron-Labs-3-Puzzle-75B-A9B-NVFP4)** — nvidia | 85 likes, 16,959 downloads  
  NVIDIA's Puzzle-pretrained 75B MoE (9B active) with NVFP4 quantization for efficient inference.

- **[nvidia/Nemotron-Labs-Audex-30B-A3B](https://huggingface.co/nvidia/Nemotron-Labs-Audex-30B-A3B)** — nvidia | 82 likes, 436 downloads  
  A 30B MoE (3B active) from NVIDIA's Nemotron Labs series for audex tasks.

- **[meituan-longcat/LongCat-2.0](https://huggingface.co/meituan-longcat/LongCat-2.0)** — meituan-longcat | 165 likes, 1,107 downloads  
  Meituan's long-context conversational model, optimized for extended reasoning chains.

- **[SupraLabs/Supra-Router-51M](https://huggingface.co/SupraLabs/Supra-Router-51M)** — SupraLabs | 73 likes, 722 downloads  
  A tiny 51M routing model for dynamic expert selection in MoE systems.

### 🎨 Multimodal & Generation (image, video, audio, text-to-X)

- **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** — nvidia | 2,687 likes, 1,447,244 downloads  
  NVIDIA's 3B vision model for precise object localization and feature extraction, trending for its accuracy-to-size ratio.

- **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)** — baidu | 1,903 likes, 1,246,042 downloads  
  Baidu's unlimited-domain OCR model for image-text-to-text pipelines, seeing massive adoption.

- **[krea/Krea-2-Turbo](https://huggingface.co/krea/Krea-2-Turbo)** — krea | 569 likes, 157,302 downloads  
  Faster variant of Krea-2-Raw for text-to-image generation with diffusers.

- **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)** — empero-ai | 1,931 likes, 1,875,602 downloads  
  GGUF-quantized multi-modal Qwen3.5 finetune with 1M context for reasoning tasks.

- **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** — HauhauCS | 2,596 likes, 2,716,428 downloads  
  Uncensored Qwen3.6 35B MoE (3B active) with vision, extremely popular for aggressive reasoning.

- **[bottlecapai/ThinkingCap-Qwen3.6-27B](https://huggingface.co/bottlecapai/ThinkingCap-Qwen3.6-27B)** — bottlecapai | 187 likes, 2,189 downloads  
  Qwen3.6-based multi-modal model with enhanced chain-of-thought capabilities.

- **[nvidia/Qwen3.6-27B-NVFP4](https://huggingface.co/nvidia/Qwen3.6-27B-NVFP4)** — nvidia | 332 likes, 748,054 downloads  
  NVIDIA-optimized Qwen3.6 27B with NVFP4 quantization for efficient deployment.

- **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M)** — empero-ai | 748 likes, 179,378 downloads  
  Unquantized version of Qwythos 9B for image-text-to-text and Qwen3.5 reasoning.

- **[open-gigaai/Giga-World-1](https://huggingface.co/open-gigaai/Giga-World-1)** — open-gigaai | 91 likes, 0 downloads  
  Apache-2.0 licensed diffuser model for world-scale image generation.

- **[eric-venti-seeds/Sun-Direction-Lora-Flux2Klein9B](https://huggingface.co/eric-venti-seeds/Sun-Direction-Lora-Flux2Klein9B)** — eric-venti-seeds | 123 likes, 0 downloads  
  Sun-direction lighting LoRA for Flux2Klein image-to-image editing.

- **[conradlocke/krea2-identity-edit](https://huggingface.co/conradlocke/krea2-identity-edit)** — conradlocke | 133 likes, 0 downloads  
  LoRA for identity-preserving image editing using Krea-2-Raw base.

- **[Patil/Krea-2-depth-controlnet](https://github.com/Patil/Krea-2-depth-controlnet)** — Patil | 83 likes, 0 downloads  
  Depth-aware ControlNet LoRA for Krea-2 flow-matching pipelines.

### 🔧 Specialized Models (code, math, medical, embeddings, tabular)

- **[google/tabfm-1.0.0-pytorch](https://huggingface.co/google/tabfm-1.0.0-pytorch)** — google | 330 likes, 16,374 downloads  
  Google's tabular foundation model for zero-shot classification and regression on structured data.

- **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)** — yuxinlu1 | 2,670 likes, 703,735 downloads  
  Gemma-4 12B GGUF finetuned for coding, code reasoning, and terminal tasks, very popular among developers.

- **[yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF)** — yuxinlu1 | 1,117 likes, 418,171 downloads  
  Agentic variant of Gemma-4 12B for autonomous coding and terminal operations.

- **[InternScience/Agents-A1](https://huggingface.co/InternScience/Agents-A1)** — InternScience | 436 likes, 23,112 downloads  
  Qwen3.5 MoE 4B-scale model optimized for multi-modal agentic workflows.

### 📦 Fine-tunes & Quantizations (community fine-tunes, GGUF, AWQ)

- **[unsloth/DeepSeek-V4-Flash-GGUF](https://huggingface.co/unsloth/DeepSeek-V4-Flash-GGUF)** — unsloth | 111 likes, 22,953 downloads  
  Unsloth's GGUF quantization of DeepSeek-V4-Flash for efficient local inference.

- **[unsloth/Qwen3.6-27B-MTP-GGUF](https://huggingface.co/unsloth/Qwen3.6-27B-MTP-GGUF)** — unsloth | 1,025 likes, 2,894,918 downloads  
  Multi-turn-prompt GGUF of Qwen3.6 27B, the week's most downloaded model at 2.9M downloads.

- **[deepreinforce-ai/Ornith-1.0-35B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF)** — deepreinforce-ai | 820 likes, 957,721 downloads  
  35B GGUF model with MIT license, endpoints-compatible for easy deployment.

- **[froggeric/Qwen-Fixed-Chat-Templates](https://huggingface.co/froggeric/Qwen-Fixed-Chat-Templates)** — froggeric | 822 likes, 0 downloads  
  MLX-compatible fixed chat templates for Qwen models, a niche but essential utility.

- **[AliesTaha/fable-traces](https://huggingface.co/AliesTaha/fable-traces)** — AliesTaha | 197 likes, 4,647 downloads  
  Qwen3-based instruct model with Fable trace data for improved chain-of-thought.

- **[GnLOLot/MiniCPM5-1B-Claude-Opus-Fable5-Thinking-GGUF](https://huggingface.co/GnLOLot/MiniCPM5-1B-Claude-Opus-Fable5-Thinking-GGUF)** — GnLOLot | 142 likes, 2,239 downloads  
  Ultra-small 1B GGUF using MiniCPM5 with Claude Opus thinking traces.

## 3. Ecosystem Signal

The current ecosystem reveals **three major trends**:

1. **MoE Dominance**: Nearly every trending LLM this week uses Mixture-of-Experts architecture. The Qwen3.5/3.6 family leads with multiple active parameter scales (3B, 6B, 9B), while NVIDIA's Nemotron-Labs series and Mistral's Leanstral push MoE efficiency further. The 35B-A3B form factor (35B total, 3B active) has become a sweet spot for performance-per-token.

2. **Quantization as Standard Practice**: GGUF variants now represent the majority of download counts. The top 3 most-downloaded models are all GGUF quantizations, with unsloth/Qwen3.6-27B-MTP-GGUF exceeding 2.8M downloads. Community fine-tunes on Qwen and Gemma-4 base models are increasingly released first in GGUF format, indicating a shift toward consumer-hardware deployment as the default use case.

3. **Vision-MoE Convergence**: Models like Qwythos-9B and Qwen3.6-35B-A3B combine MoE language backbones with vision encoders, blurring the line between pure LLMs and multimodal systems. NVIDIA's LocateAnything-3B demonstrates that task-specific vision models can achieve high popularity even at smaller scales, suggesting demand for production-ready, specialized vision AI over general-purpose behemoths.

Open-weight models continue to outpace proprietary releases in community engagement, with DeepSeek-V4, Gemma-4, and Qwen3.6 forming the dominant base model families for fine-tuning activity.

## 4. Worth Exploring

1. **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** — At only 3B parameters with 2,687 likes and 1.4M downloads, this is the standout model of the week. It proves that compact, precisely-targeted vision models can outperform larger alternatives in specific domains. Worth studying for its architecture efficiency and as a blueprint for deploying vision AI at the edge.

2. **[unsloth/Qwen3.6-27B-MTP-GGUF](https://huggingface.co/unsloth/Qwen3.6-27B-MTP-GGUF)** — The week's most-downloaded model (2.9M) signals that 27B MoE models with multi-turn prompting are the new standard for local reasoning. If you're building for consumer hardware, this represents the current state-of-the-art in quantized conversational AI.

3. **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)** — Gemma-4's coding variant has 2,670 likes and 703K downloads, indicating strong developer satisfaction. Its "composer" architecture for code generation is a novel approach worth examining for anyone building AI-assisted development tools.

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*