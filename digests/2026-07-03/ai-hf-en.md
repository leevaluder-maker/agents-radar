# Hugging Face Trending Models Digest 2026-07-03

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-07-03 02:01 UTC

---

Here is the structured Hugging Face Trending Models Digest for July 3, 2026.

---

## Hugging Face Trending Models Digest — 2026-07-03

### 1. Today's Highlights

This week’s trending roster is dominated by a massive wave of community-driven GGUF quantizations and fine-tunes, particularly around the Qwen 3.5/3.6 and GLM-5.2 MoE architectures. NVIDIA has made a strong push with both vision models (LocateAnything-3B) and optimized inference formats (NVFP4), while new entrants like Baidu’s **Unlimited-OCR** and the completely fresh **Ornith-1.0** model family from deepreinforce-ai signal a growing appetite for scalable, open-weight multimodal systems. The ecosystem is increasingly polarized between massive MoE base models and highly accessible quantized variants for local deployment.

### 2. Trending Models

#### 🧠 Language Models (LLMs, chat, instruction-tuned)

- **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** — *zai-org*, 3,256 likes, 176k downloads  
  The flagship MoE conversational model driving a new ecosystem of quantized and abliterated variants; trending due to strong community adoption and daily fine-tuning activity.

- **[deepseek-ai/DeepSeek-V4-Pro-DSpark](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-DSpark)** — *deepseek-ai*, 303 likes, 8k downloads  
  DeepSeek’s latest V4-generation dense model with advanced sparse activation (DSpark); trending as a high-performance open-weight alternative for reasoning-heavy tasks.

- **[deepreinforce-ai/Ornith-1.0-397B](https://huggingface.co/deepreinforce-ai/Ornith-1.0-397B)** — *deepreinforce-ai*, 196 likes, 7k downloads  
  A massive new MoE model from the Ornith family, offering competitive performance in a modular architecture; emerging as a challenger to established families.

- **[LiquidAI/LFM2.5-230M](https://huggingface.co/LiquidAI/LFM2.5-230M)** — *LiquidAI*, 192 likes, 26k downloads  
  A compact Liquid Foundation Model demonstrating strong performance for its size; popular for on-device and edge deployments.

- **[InternScience/Agents-A1](https://huggingface.co/InternScience/Agents-A1)** — *InternScience*, 182 likes, 1.5k downloads  
  A specialized MoE model designed for agentic tool-use and multi-step reasoning.

- **[google/tabfm-1.0.0-pytorch](https://huggingface.co/google/tabfm-1.0.0-pytorch)** — *google*, 119 likes, 89 downloads  
  Google’s tabular foundation model for zero-shot classification/regression; notable for bringing transformer architectures to structured data tasks.

#### 🎨 Multimodal & Generation (image, video, audio, text-to-X)

- **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)** — *baidu*, 1,652 likes, 758k downloads  
  A high-performance general OCR model from Baidu, gaining traction for its ability to handle complex document layouts and multilingual text.

- **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** — *nvidia*, 2,573 likes, 1M downloads  
  NVIDIA’s reference-level open-vocabulary object localization model, trending for its accuracy and generalization across domains.

- **[krea/Krea-2-Turbo](https://huggingface.co/krea/Krea-2-Turbo)** — *krea*, 462 likes, 69k downloads  
  A turbocharged text-to-image diffusion model optimized for speed, part of the broader Krea-2 ecosystem being widely adopted in ComfyUI workflows.

- **[fal/LTX-2.3-3DREAL-LoRA](https://huggingface.co/fal/LTX-2.3-3DREAL-LoRA)** — *fal*, 145 likes, 0 downloads (new)  
  A LoRA adapter for LTX-2.3 bringing photorealistic 3D-aware video generation; very new but already generating interest in the video synthesis community.

- **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)** — *empero-ai*, 1,256 likes, 1.25M downloads  
  A highly downloaded vision-language GGUF model fine-tuned on synthetic Claude data, showing strong demand for multimodal local inference.

#### 🔧 Specialized Models (code, math, medical, embeddings, PII)

- **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)** — *yuxinlu1*, 2,573 likes, 614k downloads  
  A specialized code-generation GGUF model built on Gemma-4, fine-tuned for long-context code composition and reasoning.

- **[yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF)** — *yuxinlu1*, 963 likes, 314k downloads  
  An agentic variant of the above, optimized for terminal and tool-use scenarios with extended reasoning capabilities.

- **[BugTraceAI/BugTraceAI-CORE-Ultra-27B-Q6](https://huggingface.co/BugTraceAI/BugTraceAI-CORE-Ultra-27B-Q6)** — *BugTraceAI*, 121 likes, 8k downloads  
  A cybersecurity-focused GGUF model for offensive and defensive security analysis.

- **[nationaldesignstudio/rampart](https://huggingface.co/nationaldesignstudio/rampart)** — *nationaldesignstudio*, 104 likes, 790 downloads  
  A BERT-based ONNX model for PII detection and token classification, trending alongside growing interest in privacy-preserving NLP pipelines.

#### 📦 Fine-tunes & Quantizations (GGUF, AWQ, community variants)

- **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** — *HauhauCS*, 2,397 likes, 3M downloads  
  The most downloaded model this week — an uncensored, aggressively fine-tuned Qwen3.6 MoE GGUF variant, reflecting massive demand for unrestricted local models.

- **[deepreinforce-ai/Ornith-1.0-35B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF)** — *deepreinforce-ai*, 658 likes, 284k downloads  
  GGUF quantizations of the new Ornith-1.0-35B base model, enabling local deployment of a competitive 35B MoE.

- **[nvidia/Qwen3.6-27B-NVFP4](https://huggingface.co/nvidia/Qwen3.6-27B-NVFP4)** — *nvidia*, 211 likes, 27k downloads  
  NVIDIA’s NVFP4 compressed format for Qwen3.6, demonstrating strong adoption of hardware-aware quantization for enterprise GPU clusters.

- **[nvidia/GLM-5.2-NVFP4](https://huggingface.co/nvidia/GLM-5.2-NVFP4)** — *nvidia*, 208 likes, 159k downloads  
  Similar NVFP4 quantization for GLM-5.2, offering memory-efficient MoE inference with minimal quality loss.

- **[huihui-ai/Huihui-GLM-5.2-abliterated-GGUF](https://huggingface.co/huihui-ai/Huihui-GLM-5.2-abliterated-GGUF)** — *huihui-ai*, 135 likes, 2.5k downloads  
  An “abliterated” (safety-removed) GGUF variant of GLM-5.2, continuing the community trend of releasing relaxed versions of popular models.

### 3. Ecosystem Signal

**Qwen 3.5/3.6** has solidified its position as the dominant open-weight MoE family, with dozens of community fine-tunes, uncensored variants, and GGUF quantizations generating millions of downloads. **GLM-5.2** is the primary alternative competing for attention, especially after NVIDIA released NVFP4-optimized versions. The **Ornith-1.0** family (9B, 35B, 397B) is a dark horse — a brand-new open architecture from deepreinforce-ai that already has high-quality GGUF quantizations available, signaling strong community investment. **NVIDIA** is aggressively building the toolchain layer: their NVFP4 quantizations and LocateAnything vision model show they are positioning as the infrastructure provider for open-weight models. The “uncensored” and “abliterated” sub-trend continues to accelerate, with HauhauCS’s Qwen3.6 variant alone surpassing 3M downloads — a clear signal of user demand for locally runnable models without safety guardrails. **ComfyUI ecosystem integration** is also notable, with Krea-2 derivations and LoRAs being surfaced directly on the Hub. On the open-weight vs proprietary axis, the week is overwhelmingly open, with no proprietary API-first models appearing in the top 30.

### 4. Worth Exploring

1. **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** — With 1M downloads and 2.5k likes in its first week, this is the standout multimodal model of the batch. It sets a new bar for open-vocabulary localization in a compact 3B parameter footprint, making it ideal for both research and production vision pipelines.

2. **[deepreinforce-ai/Ornith-1.0-35B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF)** — If you are evaluating next-generation MoE models beyond the Qwen/GLM duopoly, Ornith-1.0 deserves serious attention. Its GGUF variant makes it immediately deployable on consumer hardware, and its strong early metrics suggest it could be a competitive daily driver.

3. **[google/tabfm-1.0.0-pytorch](https://huggingface.co/google/tabfm-1.0.0-pytorch)** — This is an under-the-radar release that is worth studying for its architectural approach. Bringing zero-shot transformer capabilities to tabular data (regression, classification) could reshape how structured data ML is done, especially for enterprise teams heavily invested in tabular pipelines.

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*