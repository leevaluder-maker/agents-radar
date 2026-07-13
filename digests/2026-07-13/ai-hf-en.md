# Hugging Face Trending Models Digest 2026-07-13

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-07-13 01:52 UTC

---

Here is the structured Hugging Face Trending Models Digest for July 13, 2026.

---

## Hugging Face Trending Models Digest — 2026-07-13

### 1. Today’s Highlights

This week’s trending models are dominated by the **Qwen 3.6 ecosystem**, which has sparked an explosion of fine-tunes, quantizations, and vision-enabled variants. The **uncensored** and **"thinking"** model trend continues to accelerate, as seen with aggressive community fine-tunes and token-efficient reasoning versions. **NVIDIA** and **Cohere** are also making strategic plays in specialized domains, with NVIDIA releasing a trio of models spanning vision localization (LocateAnything-3B), language (Nemotron-Labs-Audex-30B), and puzzle-solving (Nemotron-Labs-3-Puzzle-75B). Meanwhile, **multi-modal MoE** architectures are solidifying as a major paradigm, with several Mixture-of-Experts models appearing across both language and video generation pipelines.

### 2. Trending Models by Category

#### 🧠 Language Models (LLMs, chat models, instruction-tuned)

- **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** — *zai-org* | Likes: 3,857 | Downloads: 441,413  
  A major conversational MoE model from Zhipu AI using the GLM architecture, trending due to its strong MoE design and community adoption for dialogue applications.

- **[bottlecapai/ThinkingCap-Qwen3.6-27B](https://huggingface.co/bottlecapai/ThinkingCap-Qwen3.6-27B)** — *bottlecapai* | Likes: 266 | Downloads: 4,463  
  Image-text-to-text model built on Qwen 3.6 with "thinking" capabilities, gaining attention for multimodal reasoning.

- **[InternScience/Agents-A1](https://huggingface.co/InternScience/Agents-A1)** — *InternScience* | Likes: 510 | Downloads: 29,038  
  A Qwen 3.5 MoE-based agent model with image-text-to-text support, trending for its agentic architecture.

- **[nvidia/Nemotron-Labs-Audex-30B-A3B](https://huggingface.co/nvidia/Nemotron-Labs-Audex-30B-A3B)** — *nvidia* | Likes: 131 | Downloads: 901  
  NVIDIA's 30B MoE language model (3B active), part of the Nemotron Labs suite, attracting interest for enterprise-grade performance.

- **[nvidia/NVIDIA-Nemotron-Labs-3-Puzzle-75B-A9B-NVFP4](https://huggingface.co/nvidia/NVIDIA-Nemotron-Labs-3-Puzzle-75B-A9B-NVFP4)** — *nvidia* | Likes: 113 | Downloads: 34,796  
  A 75B MoE puzzle-solving model with 9B active parameters, using NVIDIA's NVFP4 quantization for efficient deployment.

- **[migtissera/Tess-4-27B](https://huggingface.co/migtissera/Tess-4-27B)** — *migtissera* | Likes: 94 | Downloads: 971  
  Image-text-to-text model built on Qwen 3.5, notable for its "Tess" lineage of reasoning-focused fine-tunes.

- **[meituan-longcat/LongCat-2.0](https://huggingface.co/meituan-longcat/LongCat-2.0)** — *meituan-longcat* | Likes: 182 | Downloads: 1,767  
  A long-context conversational model from Meituan, trending for its extended context window capabilities.

#### 🎨 Multimodal & Generation (image, video, audio, text-to-X)

- **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** — *nvidia* | Likes: 2,717 | Downloads: 1,501,653  
  NVIDIA's compact 3B vision-language model for object localization, highly popular due to its utility in vision tasks and strong feature extraction performance.

- **[Alissonerdx/LTX-Best-Face-ID](https://huggingface.co/Alissonerdx/LTX-Best-Face-ID)** — *Alissonerdx* | Likes: 111 | Downloads: 0  
  A LoRA for identity-preserving text-to-video using the LTX-Video pipeline, trending for face-consistent video generation.

- **[robbyant/lingbot-world-v2-14b-causal-fast](https://huggingface.co/robbyant/lingbot-world-v2-14b-causal-fast)** — *robbyant* | Likes: 85 | Downloads: 0  
  A world model for image-to-video generation with causal attention, part of the LingBot series focusing on video world modeling.

- **[open-gigaai/Giga-World-1](https://huggingface.co/open-gigaai/Giga-World-1)** — *open-gigaai* | Likes: 123 | Downloads: 0  
  A diffusion-based world model, newly released with Apache-2.0 license, signaling open-weight competition in world model research.

- **[CohereLabs/cohere-transcribe-arabic-07-2026](https://huggingface.co/CohereLabs/cohere-transcribe-arabic-07-2026)** — *CohereLabs* | Likes: 95 | Downloads: 9,860  
  A dedicated Arabic ASR model from Cohere, trending as a specialized high-quality speech recognition release.

- **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)** — *baidu* | Likes: 1,943 | Downloads: 1,430,656  
  Baidu's general-purpose OCR model with massive adoption, trending for its unlimited text extraction from images.

- **[nineninesix/gepard-1.0](https://huggingface.co/nineninesix/gepard-1.0)** — *nineninesix* | Likes: 85 | Downloads: 2,263  
  A text-to-speech model built on Qwen 3.5 text backbone, gaining traction for voice generation from language models.

#### 🔧 Specialized Models (code, math, medical, embeddings)

- **[google/tabfm-1.0.0-pytorch](https://huggingface.co/google/tabfm-1.0.0-pytorch)** — *google* | Likes: 357 | Downloads: 20,973  
  Google's tabular foundation model for classification and regression, trending for zero-shot tabular learning.

- **[OpenMOSS-Team/MOSS-Transcribe-Diarize](https://huggingface.co/OpenMOSS-Team/MOSS-Transcribe-Diarize)** — *OpenMOSS-Team* | Likes: 130 | Downloads: 14,491  
  An audio-text-to-text model combining transcription and speaker diarization, gaining attention for meeting and conversation analysis.

- **[yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF)** — *yuxinlu1* | Likes: 1,159 | Downloads: 445,368  
  A Gemma 4-based agentic coding model optimized for terminal use, trending among developers for agentic code generation workflows.

#### 📦 Fine-tunes & Quantizations (community fine-tunes, GGUF, AWQ)

- **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)** — *empero-ai* | Likes: 2,047 | Downloads: 1,967,677  
  A highly popular GGUF quantization of a Qwen 3.5-based reasoning model, trending for efficient local deployment with llama.cpp.

- **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** — *HauhauCS* | Likes: 2,676 | Downloads: 2,596,384  
  An uncensored MoE fine-tune of Qwen 3.6 with aggressive prompting, one of the most downloaded models this week.

- **[unsloth/DeepSeek-V4-Flash-GGUF](https://huggingface.co/unsloth/DeepSeek-V4-Flash-GGUF)** — *unsloth* | Likes: 152 | Downloads: 44,614  
  Unsloth's optimized GGUF quantization of DeepSeek V4, popular for fast inference on consumer hardware.

- **[unsloth/Qwen3.6-27B-MTP-GGUF](https://huggingface.co/unsloth/Qwen3.6-27B-MTP-GGUF)** — *unsloth* | Likes: 1,058 | Downloads: 2,905,019  
  A massively downloaded GGUF version of Qwen 3.6-27B with Multi-Token Prediction, sought after for efficient local LLM use.

- **[unsloth/Qwen3.6-27B-NVFP4](https://huggingface.co/unsloth/Qwen3.6-27B-NVFP4)** — *unsloth* | Likes: 179 | Downloads: 1,378,663  
  An NVFP4 quantized variant of Qwen 3.6-27B optimized for NVIDIA hardware, highly downloaded for GPU-constrained setups.

- **[bottlecapai/ThinkingCap-Qwen3.6-27B-GGUF](https://huggingface.co/bottlecapai/ThinkingCap-Qwen3.6-27B-GGUF)** — *bottlecapai* | Likes: 83 | Downloads: 312,299  
  A token-efficient thinking model GGUF, trending for reducing inference costs while maintaining reasoning quality.

- **[deepreinforce-ai/Ornith-1.0-35B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF)** — *deepreinforce-ai* | Likes: 855 | Downloads: 1,347,036  
  A MIT-licensed 35B GGUF model compatible with Hugging Face endpoints, widely downloaded for flexible deployment.

- **[GnLOLot/MiniCPM5-1B-Claude-Opus-Fable5-Thinking-GGUF](https://huggingface.co/GnLOLot/MiniCPM5-1B-Claude-Opus-Fable5-Thinking-GGUF)** — *GnLOLot* | Likes: 202 | Downloads: 49,268  
  A tiny 1B thinking model GGUF, appealing for edge deployment and low-resource environments.

- **[SupraLabs/Supra-Router-51M](https://huggingface.co/SupraLabs/Supra-Router-51M)** — *SupraLabs* | Likes: 107 | Downloads: 1,434  
  A 51M parameter router model for directing inputs to specialized models, gaining traction in modular AI pipelines.

- **[froggeric/Qwen-Fixed-Chat-Templates](https://huggingface.co/froggeric/Qwen-Fixed-Chat-Templates)** — *froggeric* | Likes: 865 | Downloads: 0  
  A chat template correction for Qwen models (including Qwen 3.5), trending due to widespread need for proper Jinja formatting.

### 3. Ecosystem Signal

The **Qwen 3.6 family** is the dominant narrative this cycle, spawning an entire sub-ecosystem of MoE variants (e.g., 35B-A3B uncensored, 27B MTP), vision-enabled versions, and quantized GGUF releases. The **"uncensored"** and **"thinking"** fine-tuning categories continue to see heavy engagement, suggesting strong community demand for models with fewer guardrails and chain-of-thought reasoning — even at large scales. **Mixture-of-Experts** is no longer experimental; it has become the de facto architecture for efficient scaling, as evidenced by the number of MoE models (GLM-5.2, Nemotron-Labs-Audex, Qwen 3.6 variants). **NVIDIA** is aggressively building an open-weight suite with NVFP4 quantization that bridges their hardware ecosystem, positioning themselves as a full-stack AI provider. On the open-source side, **Cohere** and **Google** are releasing specialized models (Arabic ASR, tabular FM), indicating a trend toward vertical-specific foundation models rather than general-purpose giants. Quantization activity is at an all-time high — Unsloth alone accounts for three of the top downloaded models — as inference efficiency remains the primary bottleneck for community adoption.

### 4. Worth Exploring

1. **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** — With nearly 2.6M downloads, this uncensored MoE fine-tune represents the frontier of aggressive prompt-following in large MoE models at a very active parameter count (3B active). Essential study for understanding the limits and risks of uncensored model behavior.

2. **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** — At only 3B parameters with over 1.5M downloads and 2.7K likes, this vision model demonstrates that compact, task-specific models can achieve outsized community impact. It is a strong candidate for edge deployment and multimodal retrieval pipelines.

3. **[unsloth/Qwen3.6-27B-MTP-GGUF](https://huggingface.co/unsloth/Qwen3.6-27B-MTP-GGUF)** — As the most downloaded model in this digest (2.9M), this GGUF with Multi-Token Prediction is a benchmark for understanding how quantization and architectural innovations (MTP) combine to make open-source LLMs viable on consumer hardware. A must-study for anyone building local inference infrastructure.

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*