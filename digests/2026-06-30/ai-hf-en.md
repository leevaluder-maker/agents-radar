# Hugging Face Trending Models Digest 2026-06-30

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-06-30 02:30 UTC

---

# 🤗 Hugging Face Trending Models Digest — 2026-06-30

## Today's Highlights

This week's trending models reveal a strong surge in **Mixture-of-Experts (MoE) architectures** dominating the top ranks, with **GLM-5.2** and **Qwen3.6-35B-A3B** variants leading in both likes and downloads. The **Ornith 1.0** series from deepreinforce-ai (spanning 9B to 397B parameters) demonstrates growing community appetite for multi-scale MoE models. NVIDIA's **Model Optimizer** quantizations (NVFP4) are gaining traction for production deployment, while **uncensored fine-tunes** like HauhauCS's Qwen3.6 variant have exploded in downloads (3M+). The **Krea-2** image generation ecosystem is also emerging strongly, supported by both official and community LoRAs. Notably, **Gemma-4-12B** coding variants continue to attract massive engagement, signaling sustained interest in agentic coding capabilities.

---

## Trending Models

### 🧠 Language Models

- **GLM-5.2** by zai-org | 2,945 likes | 133,350 downloads  
  The highest-liked model this week; a MoE-based conversational model from Zhipu AI featuring a novel dynamic sparse attention architecture.
- **Ornith-1.0-35B-GGUF** by deepreinforce-ai | 483 likes | 123,598 downloads  
  A quantized 35B MoE model (Qwen3.5-based) offering strong performance with MIT licensing, driving broad community adoption.
- **Ornith-1.0-9B-GGUF** by deepreinforce-ai | 308 likes | 68,667 downloads  
  The smaller sibling of the Ornith series, popular for its accessibility and endpoints compatibility.
- **DeepSeek-V4-Pro-DSpark** by deepseek-ai | 216 likes | 5,460 downloads  
  DeepSeek's latest flagship with advanced reasoning; accompanied by a research paper (arxiv:2606.19348).
- **VibeThinker-3B** by WeiboAI | 749 likes | 63,449 downloads  
  A compact 3B math-focused model based on Qwen2, offering strong reasoning capabilities in a small footprint.
- **Qwen-AgentWorld-35B-A3B** by Qwen | 438 likes | 26,223 downloads  
  A world-model MoE from Qwen designed for agentic planning and environment understanding.
- **LFM2.5-230M** by LiquidAI | 152 likes | 15,463 downloads  
  A tiny 230M Liquid Foundation Model, demonstrating that small LMs remain relevant for edge deployment.

### 🎨 Multimodal & Generation

- **Unlimited-OCR** by baidu | 1,374 likes | 362,945 downloads  
  A versatile image-text-to-text OCR model supporting unlimited input sizes; the most downloaded model this week.
- **Krea-2-Turbo** by krea | 394 likes | 38,454 downloads  
  A text-to-image diffusion model fine-tuned from Krea-2-Raw for faster, more stylized generation.
- **Krea-2-Raw** by krea | 245 likes | 27,464 downloads  
  The base text-to-image model powering the Krea-2 ecosystem; open-weight with permissive licensing.
- **LocateAnything-3B** by nvidia | 2,482 likes | 728,320 downloads  
  A 3B vision-language model for zero-shot object localization; NVIDIA's highest-liked model this week.
- **LTX-2.3-3DREAL-LoRA** by fal | 115 likes | 0 downloads  
  A 3D-aware video generation LoRA for the LTX-2.3 pipeline, pushing image-to-video boundaries.
- **nemotron-3.5-asr-streaming-0.6b** by nvidia | 743 likes | 76,154 downloads  
  NVIDIA's compact streaming ASR model (0.6B params) optimized for real-time speech recognition.

### 🔧 Specialized Models

- **Qwythos-9B-Claude-Mythos-5-1M-GGUF** by empero-ai | 953 likes | 907,682 downloads  
  A reasoning-enhanced Qwen3.5 variant with 1M context; massive downloads highlight demand for long-context models.
- **Chunjiang-Intelligence/DeepSeek-v4-Fable** | 130 likes | 1,463 downloads  
  A cybersecurity-focused fine-tune of DeepSeek-V4, indicating specialization trends.
- **gemma-4-12B-coder-fable5-composer2.5-v1-GGUF** by yuxinlu1 | 2,503 likes | 561,577 downloads  
  The most popular coding model this week; a Gemma-4-12B fine-tune optimized for code generation and reasoning.

### 📦 Fine-tunes & Quantizations

- **HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive** | 2,333 likes | 3,089,944 downloads  
  An uncensored, aggressively fine-tuned MoE variant; the highest download count this week by a large margin.
- **unsloth/GLM-5.2-GGUF** | 465 likes | 164,180 downloads  
  Community quantization of GLM-5.2 by Unsloth, democratizing access to this powerful MoE.
- **nvidia/GLM-5.2-NVFP4** | 171 likes | 81,944 downloads  
  NVIDIA's optimized 4-bit floating-point quantization for GLM-5.2, targeting production efficiency.
- **nvidia/Qwen3.6-35B-A3B-NVFP4** | 378 likes | 5,392,518 downloads  
  NVIDIA's NVFP4 quantization of Qwen3.6-35B-A3B; explosive downloads show strong demand for efficient MoE deployment.
- **Gemma4-12B-QAT-Uncensored-HauhauCS-Balanced** | 107 likes | 46,053 downloads  
  A balanced uncensored variant of Gemma-4-12B, continuing the uncensored fine-tuning trend.

---

## Ecosystem Signal

The model ecosystem in late June 2026 is defined by **MoE dominance** and **quantization maturity**. The GLM-5.2 and Qwen3.5/3.6 model families are the clear winners this week, attracting both official releases and multiple community quantizations. **NVIDIA's Model Optimizer** (NVFP4) is emerging as a standard for efficient deployment, with over 5M downloads for a single quantized checkpoint — signaling that developers are prioritizing production-ready, low-bit models over raw FP16 weights.

The **"uncensored" fine-tuning movement** continues to accelerate, with HauhauCS variants accumulating millions of downloads. This reflects a growing community preference for models with minimal alignment constraints, particularly for creative writing and roleplay applications.

**Ornith 1.0** represents a new trend: coherent model families spanning 9B to 397B parameters, all built on Qwen3.5 MoE architecture with MIT licensing. This "unified family" approach may reshape how the community benchmarks and deploys models at different scales.

On the multimodal front, **Krea-2** is building a full ecosystem (base model, turbo variant, ComfyUI integration, style LoRAs), while NVIDIA's **LocateAnything-3B** shows that specialized vision models at smaller scales can still achieve high engagement.

---

## Worth Exploring

1. **nvidia/LocateAnything-3B** — With 2,482 likes and 728K downloads, this is the standout vision model this week. Its zero-shot object localization capability at just 3B parameters makes it highly practical for developers needing efficient visual grounding without large compute.

2. **yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF** — The 2,503 likes and 561K downloads speak to the quality of this coding fine-tune. It combines Google's Gemma-4 base with advanced composition techniques, making it a prime candidate for code gen workflows.

3. **HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive** — Despite ethical considerations, this model's 3M+ downloads demand attention. It represents the extreme end of community-driven model customization and offers insights into how aggressive fine-tuning affects MoE architectures.

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*