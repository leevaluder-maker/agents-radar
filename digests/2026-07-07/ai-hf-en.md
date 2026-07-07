# Hugging Face Trending Models Digest 2026-07-07

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-07-07 02:08 UTC

---

# 🤗 Hugging Face Trending Models Digest — 2026-07-07

## 1. Today's Highlights

This week's trending models reveal a clear **shift toward mixture-of-experts (MoE) architectures** and aggressive community fine-tuning of Qwen 3.5/3.6 and GLM-5.2 variants. NVIDIA continues its push into **NVFP4 quantized models** and specialized vision-grounding tools, while the **Ornith 1.0 family** from deepreinforce-ai and the **Gemma-4-based coding agents** from yuxinlu1 are driving massive download volumes. The presence of Google's **TabFM** and Baidu's **Unlimited-OCR** signals growing interest in vertical-domain foundation models. Notably, GGUF quantizations dominate the download charts, reflecting strong demand for local deployment.

## 2. Trending Models by Category

### 🧠 Language Models (LLMs, chat models, instruction-tuned)

- **[GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** — zai-org | 3,532 likes, 231k downloads  
  A MoE-based conversational model with DSA routing; trending due to its strong performance and active abliteration community (Huihui-GLM variant).

- **[DeepSeek-V4-Pro-DSpark](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-DSpark)** — deepseek-ai | 409 likes, 14k downloads  
  The latest DeepSeek V4 variant with enhanced reasoning; drawing attention for its arxiv-published architecture and DSpark inference optimizations.

- **[Leanstral-1.5-119B-A6B](https://huggingface.co/mistralai/Leanstral-1.5-119B-A6B)** — mistralai | 143 likes, 106 downloads  
  A massive 119B MoE model with 6B active parameters; early-stage but setting records for parameter efficiency in the Mistral lineage.

- **[Agents-A1](https://huggingface.co/InternScience/Agents-A1)** — InternScience | 345 likes, 8.8k downloads  
  An agent-oriented MoE model built on Qwen 3.5; gaining traction for its image-text-to-text capabilities and multi-modal agent workflows.

### 🎨 Multimodal & Generation (image, video, audio, text-to-X)

- **[Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)** — baidu | 1,795 likes, 1.07M downloads  
  A feature-extraction model for universal OCR; trending due to Baidu's reputation and massive download numbers for document AI use cases.

- **[LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** — nvidia | 2,635 likes, 1.34M downloads  
  NVIDIA's vision-language grounding model for spatial localization; extremely popular for its zero-shot object detection capabilities.

- **[Krea-2-Turbo](https://huggingface.co/krea/Krea-2-Turbo)** — krea | 529 likes, 109k downloads  
  A distilled text-to-image model fine-tuned from Krea-2-Raw; trending for its speed-quality tradeoff in creative generation.

- **[Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** — HauhauCS | 2,529 likes, 2.91M downloads  
  An uncensored, vision-capable MoE GGUF model; the highest-downloaded model this week, combining Qwen 3.6 MoE with aggressive fine-tuning.

### 🔧 Specialized Models (code, math, medical, embeddings)

- **[gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)** — yuxinlu1 | 2,623 likes, 664k downloads  
  A GGUF quantized Gemma-4 fine-tune for code generation with agentic tool use; extremely popular for local coding assistants.

- **[gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF)** — yuxinlu1 | 1,051 likes, 371k downloads  
  Enhanced agentic variant of the above, optimized for terminal and multi-turn coding tasks.

- **[tabfm-1.0.0-pytorch](https://huggingface.co/google/tabfm-1.0.0-pytorch)** — google | 257 likes, 7k downloads  
  Google's foundational model for tabular data supporting zero-shot classification and regression; signals the rise of non-text modalities.

- **[rampart](https://huggingface.co/nationaldesignstudio/rampart)** — nationaldesignstudio | 136 likes, 3.8k downloads  
  A BERT-based ONNX model for PII token classification; trending for privacy-preserving text processing with transformers.js.

### 📦 Fine-tunes & Quantizations (community fine-tunes, GGUF, AWQ)

- **[Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)** — empero-ai | 1,642 likes, 1.62M downloads  
  A GGUF quantized Qwen 3.5 variant fine-tuned on Claude-Mythos data; one of the most downloaded models, popular for role-play and creative writing.

- **[Ornith-1.0-35B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF)** — deepreinforce-ai | 759 likes, 437k downloads  
  A 35B MoE GGUF model with MIT license; the Ornith family is trending for its accessible, endpoint-compatible architecture.

- **[Qwen3.6-27B-MTP-GGUF](https://huggingface.co/unsloth/Qwen3.6-27B-MTP-GGUF)** — unsloth | 974 likes, 2.82M downloads  
  The unsloth team's GGUF quant of Qwen 3.6 with Multi-Token Prediction; massive downloads reflect Qwen 3.6's rapid adoption.

- **[Huihui-GLM-5.2-abliterated-GGUF](https://huggingface.co/huihui-ai/Huihui-GLM-5.2-abliterated-GGUF)** — huihui-ai | 178 likes, 6.7k downloads  
  An "abliterated" (safety-removed) GGUF version of GLM-5.2; niche but high-engagement for uncensored LLM enthusiasts.

## 3. Ecosystem Signal

The trending list reveals **three major ecosystem shifts**:

1. **MoE models now dominant**: Over half of the text-generation models on this list are mixture-of-experts, led by Qwen 3.5/3.6 MoE (deepreinforce's Ornith, InternScience's Agents-A1, Qwen's AgentWorld) and GLM-5.2. The 35B-A3B form factor (35B total, 3B active) is becoming a sweet spot for performance vs. efficiency.

2. **GGUF quantization is the default deployment path**: 9 of 30 models are GGUF-quantized, and they account for the top download counts (unsloth's Qwen 3.6 MTP, HauhauCS's uncensored variant, Qwythos). The community is prioritizing local inference with llama.cpp compatibility over raw performance.

3. **Open-weight leadership is fragmented**: DeepSeek V4 Pro, GLM-5.2, and Qwen 3.6 compete for the "best open model" crown, while Mistral's Leanstral 119B-A6B represents a frontier-scale MoE. NVIDIA is uniquely active across both vision (LocateAnything) and quantized LLMs (Qwen3.6-27B-NVFP4), pushing hardware-aligned optimizations.

## 4. Worth Exploring

1. **[Leanstral-1.5-119B-A6B](https://huggingface.co/mistralai/Leanstral-1.5-119B-A6B)** — Though only 143 likes, this 119B-parameter MoE with only 6B active is a breakthrough in inference efficiency. It's a must-study for anyone interested in sub-10B-inference models with frontier knowledge.

2. **[tabfm-1.0.0-pytorch](https://huggingface.co/google/tabfm-1.0.0-pytorch)** — Tabular data is the last unconquered frontier for foundation models. TabFM's zero-shot capabilities and Google's backing make it a potential game-changer for enterprise ML workflows.

3. **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** — With 2.9M downloads in one week, this model is the community's consensus pick. Its aggressive fine-tuning on top of Qwen 3.6 MoE demonstrates the ceiling of what community-driven optimization can achieve for multimodal reasoning.

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*