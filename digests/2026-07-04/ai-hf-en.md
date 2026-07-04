# Hugging Face Trending Models Digest 2026-07-04

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-07-04 01:59 UTC

---

# Hugging Face Trending Models Digest — 2026-07-04

## Today's Highlights

This week's trending models showcase a clear shift toward **mixture-of-experts (MoE) architectures** and **vision-language unification**, with multiple Qwen3.5/3.6-based MoE models dominating the top slots. NVIDIA is aggressively pushing its **NVFP4 quantization** pipeline for enterprise-scale models, while GGUF quantized variants continue to drive community adoption for local inference. The emergence of specialized agentic and coding models (gemma-4 family, Ornith series) signals growing demand for **task-optimized small-to-medium models**. Notably, Baidu's Unlimited-OCR and fal's LTX-2.3 video LoRA represent expanding multimodal frontiers beyond text generation.

---

## Trending Models

### 🧠 Language Models (LLMs, chat models, instruction-tuned)

- **[GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** — zai-org | 3,344 likes, 191k downloads  
  A 5.2B MoE conversational model gaining traction for its strong multilingual reasoning, with NVIDIA and huihui-ai providing quantized variants.

- **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** — HauhauCS | 2,433 likes, 3M downloads  
  The most downloaded model this week — an uncensored, aggressive-tuned 35B MoE vision-language model optimized via GGUF for rapid inference.

- **[nvidia/Qwen3.6-27B-NVFP4](https://huggingface.co/nvidia/Qwen3.6-27B-NVFP4)** — nvidia | 229 likes, 94k downloads  
  NVIDIA's FP4-quantized 27B model for production deployment, balancing quality and memory efficiency.

- **[Qwen/Qwen-AgentWorld-35B-A3B](https://huggingface.co/Qwen/Qwen-AgentWorld-35B-A3B)** — Qwen | 524 likes, 45k downloads  
  A 35B MoE model (3B active) optimized specifically for agentic tool-use and multi-turn reasoning tasks.

- **[LiquidAI/LFM2.5-230M](https://huggingface.co/LiquidAI/LFM2.5-230M)** — LiquidAI | 197 likes, 29k downloads  
  A tiny 230M Liquid Foundation Model demonstrating that liquid neural networks can produce competitive small LLMs.

- **[deepseek-ai/DeepSeek-V4-Pro-DSpark](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-DSpark)** — deepseek-ai | 343 likes, 9k downloads  
  DeepSeek's latest flagship with Mixture-of-Experts (MoE) and multi-token prediction, supported by an arXiv paper.

- **[deepseek-ai/DeepSeek-V4-Flash-DSpark](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-DSpark)** — deepseek-ai | 142 likes, 32k downloads  
  The faster, distilled variant of DeepSeek-V4 for low-latency chat applications.

### 🎨 Multimodal & Generation (image, video, audio, text-to-X)

- **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** — nvidia | 2,589 likes, 1.1M downloads  
  A 3B universal referring segmentation model that can locate and segment any object described in natural language — highly versatile for vision tasks.

- **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)** — baidu | 1,692 likes, 885k downloads  
  A unified OCR model handling scene text, document text, handwriting, and multilingual scripts with state-of-the-art accuracy.

- **[krea/Krea-2-Turbo](https://huggingface.co/krea/Krea-2-Turbo)** — krea | 481 likes, 84k downloads  
  A fast text-to-image diffusion model fine-tuned from Krea-2-Raw for high-quality generation at reduced compute.

- **[fal/LTX-2.3-3DREAL-LoRA](https://huggingface.co/fal/LTX-2.3-3DREAL-LoRA)** — fal | 150 likes, 0 downloads (just released)  
  A LoRA adapter for LTX-2.3 video model enabling photorealistic 3D-aware video generation from image inputs.

### 🔧 Specialized Models (code, math, medical, embeddings)

- **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)** — yuxinlu1 | 2,585 likes, 628k downloads  
  A GGUF-quantized gemma-4 12B coding model fine-tuned with Fable5 and Composer2.5 recipes, excelling at code generation and reasoning.

- **[yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF)** — yuxinlu1 | 992 likes, 329k downloads  
  Agentic variant of gemma-4 12B, optimized for terminal-based tool use and autonomous agent workflows.

- **[InternScience/Agents-A1](https://huggingface.co/InternScience/Agents-A1)** — InternScience | 209 likes, 3.5k downloads  
  A Qwen3.5-MoE-based agentic model designed for complex multi-step reasoning and API calling.

- **[BugTraceAI/BugTraceAI-CORE-Ultra-27B-Q6](https://huggingface.co/BugTraceAI/BugTraceAI-CORE-Ultra-27B-Q6)** — BugTraceAI | 125 likes, 11k downloads  
  A cybersecurity-focused Qwen3-based model for vulnerability analysis and offensive security testing.

- **[google/tabfm-1.0.0-pytorch](https://huggingface.co/google/tabfm-1.0.0-pytorch)** — google | 151 likes, 450 downloads  
  Google's TabFM foundation model for zero-shot tabular classification and regression, a rare specialized tabular release.

- **[nationaldesignstudio/rampart](https://huggingface.co/nationaldesignstudio/rampart)** — nationaldesignstudio | 115 likes, 1.1k downloads  
  An ONNX-optimized BERT model for PII token classification, deployable via Transformers.js for client-side privacy.

### 📦 Fine-tunes & Quantizations (community fine-tunes, GGUF, AWQ)

- **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)** — empero-ai | 1,372 likes, 1.36M downloads  
  The most downloaded GGUF model — a Qwen3.5-based 9B reasoning model quantized for llama.cpp with Mythos-style persona training.

- **[unsloth/Qwen3.6-27B-MTP-GGUF](https://huggingface.co/unsloth/Qwen3.6-27B-MTP-GGUF)** — unsloth | 938 likes, 1.77M downloads  
  Unsloth's fast-quantized 27B Qwen3.6 with multi-token prediction (MTP) support, enabling efficient speculative decoding.

- **[deepreinforce-ai/Ornith-1.0-35B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF)** — deepreinforce-ai | 685 likes, 322k downloads  
  GGUF quant of the Ornith 35B MoE model, combining Qwen3.5-MoE with image-text-to-text capabilities for local deployment.

- **[huihui-ai/Huihui-GLM-5.2-abliterated-GGUF](https://huggingface.co/huihui-ai/Huihui-GLM-5.2-abliterated-GGUF)** — huihui-ai | 144 likes, 3.6k downloads  
  An "abliterated" (safety-filter-removed) GGUF variant of GLM-5.2 for unrestricted use cases.

- **[nvidia/GLM-5.2-NVFP4](https://huggingface.co/nvidia/GLM-5.2-NVFP4)** — nvidia | 214 likes, 189k downloads  
  NVIDIA's FP4-quantized GLM-5.2, part of their Model Optimizer pipeline for enterprise GPU efficiency.

- **[Jackrong/Qwopus3.6-35B-A3B-Coder-MTP-GGUF](https://huggingface.co/Jackrong/Qwopus3.6-35B-A3B-Coder-MTP-GGUF)** — Jackrong | 122 likes, 44k downloads  
  A coding-focused GGUF of Qwen3.6 35B MoE with multi-token prediction for faster code generation.

- **[Comfy-Org/Krea-2](https://huggingface.co/Comfy-Org/Krea-2)** — Comfy-Org | 242 likes, 10 downloads  
  A ComfyUI-compatible variant of Krea-2, indicating growing integration between diffusion models and workflow tools.

---

## Ecosystem Signal

The **MoE paradigm** is now clearly dominant: 9 of the top 30 models use MoE architectures (GLM-5.2, Qwen3.5/3.6 MoE, Ornith series, Agents-A1), confirming that **scale is being traded for efficiency** — most MoE models hover around 35B total parameters with 3B active. The **Qwen ecosystem** has become a foundational platform, with Qwen3.5/3.6 spawning dozens of community fine-tunes, quantizations, and specialized variants.

**Open-weight momentum** continues to accelerate: all top-10 models by downloads are open-weight with quantized variants. The **GGUF format dominates community distribution** — 13 models in the list use GGUF, with llama.cpp compatibility now considered table-stakes. NVIDIA's **NVFP4 pipeline** (Qwen3.6-27B, GLM-5.2) represents an interesting counterpoint: proprietary quantization for enterprise, while community favors GGUF.

**Agentic and coding specialization** is the hottest fine-tuning direction. The gemma-4 12B coder+agentic variants from yuxinlu1, plus InternScience's Agents-A1 and Qwen's AgentWorld, show that **small, task-specific reasoning models** are becoming a distinct product category.

---

## Worth Exploring

1. **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** — With 2.6K likes and 1.1M downloads in its first week, this 3B universal segmentation model is a breakthrough in **compact vision grounding**. It's a must-study for anyone building interactive vision systems or robotic perception pipelines.

2. **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)** — The combination of a strong base (gemma-4), community fine-tuning recipes (Fable5/Composer2.5), and GGUF quantization creates a **highly accessible coding model** that rivals larger alternatives on many benchmarks. Perfect for local developer workflows.

3. **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)** — While OCR might seem mature, this model's ability to handle **scene text, documents, handwriting, and multiple languages** in a single unified architecture makes it a practical tool for document processing pipelines and a good reference for multimodal unification research.

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*