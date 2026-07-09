# Hugging Face Trending Models Digest 2026-07-09

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-07-09 02:01 UTC

---

# 🤗 Hugging Face Trending Models Digest — July 9, 2026

---

## 1. Today's Highlights

The open-weight AI ecosystem is surging with two dominant trends: **MoE (Mixture-of-Experts) efficiency** and **GGUF quantization** for local deployment. **Qwen 3.6** variants now dominate the top spots, with multiple fine-tunes and quantized versions racking up millions of downloads. **NVIDIA’s LocateAnything-3B** (2,667 likes) and **zai-org/GLM-5.2** (3,668 likes) lead the community buzz—one for vision grounding, the other for conversational MoE. Meanwhile, **DeepSeek-V4-Pro-DSpark** and its GGUF counterpart from Unsloth signal rising interest in deep reasoning MoE architectures. The agentic and coding model space is also heating up, led by **Gemma-4-12B** based fine-tunes for agentic terminal use.

---

## 2. Trending Models by Category

### 🧠 Language Models (LLMs, chat models, instruction-tuned)

- **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** — *zai-org* | 3,668 likes | 281k downloads  
  A conversational MoE model with DSA architecture, trending as a strong open-weight alternative for multi-turn dialogue.

- **[deepseek-ai/DeepSeek-V4-Pro-DSpark](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-DSpark)** — *deepseek-ai* | 439 likes | 15.5k downloads  
  The latest DeepSeek V4 production model with spark reasoning enhancements, backed by an arXiv paper and growing fast.

- **[mistralai/Leanstral-1.5-119B-A6B](https://huggingface.co/mistralai/Leanstral-1.5-119B-A6B)** — *mistralai* | 167 likes  
  A 119B-parameter MoE with only 6B active parameters—Mistral's efficient lean reasoning model.

- **[meituan-longcat/LongCat-2.0](https://huggingface.co/meituan-longcat/LongCat-2.0)** — *meituan-longcat* | 151 likes  
  A conversational model optimized for long-context generation, released by Meituan.

- **[AliesTaha/fable-traces](https://huggingface.co/AliesTaha/fable-traces)** — *AliesTaha* | 187 likes | 3.9k downloads  
  A Qwen3-based instruct model for narrative-style reasoning and story generation.

### 🎨 Multimodal & Generation (image, video, audio, text-to-X)

- **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** — *nvidia* | 2,667 likes | 1.4M downloads  
  A 3B vision-language model for open-vocabulary object localization—trending for its accuracy and small footprint.

- **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** — *HauhauCS* | 2,573 likes | 2.8M downloads  
  An uncensored MoE vision-language model with aggressive instruction tuning, massively popular for edge-of-boundary use.

- **[krea/Krea-2-Turbo](https://huggingface.co/krea/Krea-2-Turbo)** — *krea* | 555 likes | 123k downloads  
  A text-to-image diffusion model built on Krea-2-Raw, optimized for high-speed generation.

- **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)** — *baidu* | 1,873 likes | 1M downloads  
  A feature-extraction model for unlimited OCR tasks, excelling at document and scene text recognition.

- **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)** — *empero-ai* | 1,857 likes | 1.68M downloads  
  A Qwen3.5-based GGUF multimodal model with Claude-level mythos tuning, extremely popular in quantized form.

### 🔧 Specialized Models (code, math, medical, embeddings, tabular)

- **[google/tabfm-1.0.0-pytorch](https://huggingface.co/google/tabfm-1.0.0-pytorch)** — *google* | 313 likes | 9.5k downloads  
  Google's Tabular Foundation Model for zero-shot classification and regression on table data.

- **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)** — *yuxinlu1* | 2,652 likes | 674k downloads  
  A Gemma-4-12B variant fine-tuned for code and reasoning, heavily downloaded in GGUF format.

- **[yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF)** — *yuxinlu1* | 1,098 likes | 384k downloads  
  Agentic variant of Gemma-4-12B, optimized for autonomous tool-use and terminal operations.

- **[InternScience/Agents-A1](https://huggingface.co/InternScience/Agents-A1)** — *InternScience* | 400 likes | 14.7k downloads  
  A Qwen3.5-MoE model purpose-built for agentic tasks with vision input support.

### 📦 Fine-tunes & Quantizations (community fine-tunes, GGUF, AWQ)

- **[unsloth/Qwen3.6-27B-MTP-GGUF](https://huggingface.co/unsloth/Qwen3.6-27B-MTP-GGUF)** — *unsloth* | 1,011 likes | 2.84M downloads  
  Unsloth's highly optimized GGUF quantization of Qwen3.6-27B with multi-turn prompting support.

- **[deepreinforce-ai/Ornith-1.0-35B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF)** — *deepreinforce-ai* | 800 likes | 502k downloads  
  GGUF quantized version of the Ornith-1.0-35B MoE, popular for local deployment.

- **[deepreinforce-ai/Ornith-1.0-9B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-9B-GGUF)** — *deepreinforce-ai* | 461 likes | 454k downloads  
  The 9B sibling in GGUF form, offering a lighter quantized option for Ornith.

- **[nvidia/Qwen3.6-27B-NVFP4](https://huggingface.co/nvidia/Qwen3.6-27B-NVFP4)** — *nvidia* | 325 likes | 538k downloads  
  NVIDIA's FP4 quantized version of Qwen3.6-27B using Model Optimizer for extreme efficiency.

- **[froggeric/Qwen-Fixed-Chat-Templates](https://huggingface.co/froggeric/Qwen-Fixed-Chat-Templates)** — *froggeric* | 781 likes  
  A non-model resource fixing chat templates for Qwen3.5, highly useful for developers.

---

## 3. Ecosystem Signal

The **Qwen 3.6 lineage** has become the most active ecosystem on Hugging Face this week, spawning numerous fine-tunes, GGUF quantizations (Unsloth, NVIDIA, deepreinforce), and uncensored variants. **MoE architectures** are clearly winning—nearly every high-performing model (GLM-5.2, Ornith-1.0, DeepSeek-V4, Qwen3.6) uses mixture-of-experts, balancing capability with inference cost.

**GGUF quantization** remains the dominant access pattern for local deployment, with multiple models surpassing 1-2 million downloads. The community is increasingly favoring **quantized vision-language models** (Qwen3.6-27B-MTP-GGUF, Qwythos-9B), blending multimodal capability with edge-compatible format.

**Open-weight momentum** continues to eclipse proprietary API trends—models from Tencent, Baidu, Meituan, and NVIDIA all release openly, with permissive licenses (MIT, Apache-2.0). The **Gemma-4-12B agentic fine-tunes** signal a growing demand for models that can autonomously interact with terminals and tools, not just generate text.

Finally, **specialized models** for OCR (Baidu), tabular data (Google), and object localization (NVIDIA) show that foundation model leaders are now packaging domain-specific capabilities as standalone products, not just APIs.

---

## 4. Worth Exploring

1. **⭐ [nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** — 2,667 likes | 1.4M downloads — A compact yet powerful vision grounding model. At only 3B parameters, it delivers state-of-the-art open-vocabulary localization and is highly practical for robotics, retrieval, and visual QA applications.

2. **⭐ [unsloth/Qwen3.6-27B-MTP-GGUF](https://huggingface.co/unsloth/Qwen3.6-27B-MTP-GGUF)** — 1,011 likes | 2.84M downloads — The most downloaded quantized multimodal model this week. Perfect for local deployment of vision-language capabilities with Unsloth's optimized GGUF quality.

3. **⭐ [yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)** — 2,652 likes | 674k downloads — A top-tier coding and reasoning fine-tune of Gemma-4-12B, available in GGUF. Its high download volume and community approval signal a genuine practical breakthrough for developer tooling.

---

*Data sourced from Hugging Face Hub trending models page, July 9, 2026. Rankings based on weekly likes.*

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*