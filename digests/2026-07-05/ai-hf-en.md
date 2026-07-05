# Hugging Face Trending Models Digest 2026-07-05

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-07-05 02:07 UTC

---

Here is the structured **Hugging Face Trending Models Digest** for July 5, 2026.

---

### 1. Today’s Highlights

The Hugging Face ecosystem this week is dominated by a massive push toward **MoE (Mixture-of-Experts) architectures**, led by the **GLM-5.2** and **Qwen3.5/3.6** families. NVIDIA continues its aggressive play in the model optimization space with NVFP4 quantizations of both Qwen and GLM, while the community is heavily engaged in **GGUF quantization and "abliterated" fine-tunes** for local inference. A notable new trend is the rise of **agentic and terminal-optimized coding models**, exemplified by the *gemma-4-12B-agentic-fable5* series, which has seen explosive adoption. Finally, vision-language models (VLMs) like **nvidia/LocateAnything-3B** and **Baidu/Unlimited-OCR** are setting new standards for specialized image-to-text tasks.

---

### 2. Trending Models by Category

#### 🧠 Language Models (LLMs, chat models, instruction-tuned)

- **[GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** — *zai-org* | 3,399 likes, 208k downloads  
  A flagship MoE model with strong conversational abilities; trending as the highest-liked release on the leaderboard.

- **[Qwen3.6-27B-NVFP4](https://huggingface.co/nvidia/Qwen3.6-27B-NVFP4)** — *nvidia* | 250 likes, 184k downloads  
  NVIDIA’s 4-bit floating-point quantization of Qwen3.5, enabling high-performance inference on enterprise GPUs.

- **[Ornith-1.0-397B](https://huggingface.co/deepreinforce-ai/Ornith-1.0-397B)** — *deepreinforce-ai* | 209 likes, 33k downloads  
  A massive 397B MoE model (based on Qwen3.5-MoE) pushing the frontier of dense+sparse scaling.

- **[mistralai/Leanstral-1.5-119B-A6B](https://huggingface.co/mistralai/Leanstral-1.5-119B-A6B)** — *mistralai* | 100 likes, 4 downloads  
  A 119B parameter MoE with only 6B active parameters, optimized for efficient serving with vLLM.

- **[Qwen/Qwen-AgentWorld-35B-A3B](https://huggingface.co/Qwen/Qwen-AgentWorld-35B-A3B)** — *Qwen* | 534 likes, 50k downloads  
  Qwen’s dedicated agent-optimized model; trending for its balance of size (35B total, 3B active) and agentic performance.

- **[AliesTaha/fable-traces](https://huggingface.co/AliesTaha/fable-traces)** — *AliesTaha* | 121 likes, 0 downloads  
  A fine-tune of Qwen3 focused on instruction-following; early traction despite no downloads yet.

#### 🎨 Multimodal & Generation (image, video, audio, text-to-X)

- **[Krea-2-Turbo](https://huggingface.co/krea/Krea-2-Turbo)** — *krea* | 496 likes, 89k downloads  
  A turbo-charged version of the Krea-2 text-to-image model, offering faster inference with maintained quality.

- **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** — *nvidia* | 2,604 likes, 1.19M downloads  
  A specialized vision model for object localization and feature extraction; one of the most downloaded models this week.

- **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)** — *baidu* | 1,714 likes, 988k downloads  
  A state-of-the-art OCR model from Baidu; trending for its generalizability across complex document layouts.

- **[Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** — *HauhauCS* | 2,454 likes, 2.99M downloads  
  An uncensored, aggressive fine-tune of Qwen3.6 MoE with vision capabilities; extremely high download count.

- **[fal/LTX-2.3-3DREAL-LoRA](https://huggingface.co/fal/LTX-2.3-3DREAL-LoRA)** — *fal* | 157 likes, 0 downloads  
  A LoRA for real-to-3D video generation; newly released and gaining attention for its creative potential.

#### 🔧 Specialized Models (code, math, medical, embeddings, security)

- **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)** — *yuxinlu1* | 2,595 likes, 641k downloads  
  A Gemma-4 based coding model with advanced code reasoning; one of the top trending models overall.

- **[yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF)** — *yuxinlu1* | 1,010 likes, 342k downloads  
  An agentic version of the Gemma-4 coder, optimized for terminal and tool-use workflows.

- **[BugTraceAI/BugTraceAI-CORE-Ultra-27B-Q6](https://huggingface.co/BugTraceAI/BugTraceAI-CORE-Ultra-27B-Q6)** — *BugTraceAI* | 132 likes, 12k downloads  
  A cybersecurity-focused Qwen3 model with 6-bit quantization for offensive and defensive security tasks.

- **[google/tabfm-1.0.0-pytorch](https://huggingface.co/google/tabfm-1.0.0-pytorch)** — *google* | 197 likes, 1.1k downloads  
  Google’s TabFM foundation model for zero-shot tabular classification and regression.

- **[nationaldesignstudio/rampart](https://huggingface.co/nationaldesignstudio/rampart)** — *nationaldesignstudio* | 123 likes, 1.8k downloads  
  A lightweight ONNX/BERT model for PII token classification; trending for privacy-preserving pipelines.

#### 📦 Fine-tunes & Quantizations (community fine-tunes, GGUF, AWQ)

- **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)** — *empero-ai* | 1,462 likes, 1.46M downloads  
  A GGUF quant of a mythos-instruct fine-tune on Qwen3.5; massive download numbers indicate strong community adoption.

- **[huihui-ai/Huihui-GLM-5.2-abliterated-GGUF](https://huggingface.co/huihui-ai/Huihui-GLM-5.2-abliterated-GGUF)** — *huihui-ai* | 162 likes, 4.7k downloads  
  An "abliterated" (safety-removed) GGUF version of GLM-5.2, popular among local inference users.

- **[deepreinforce-ai/Ornith-1.0-35B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF)** — *deepreinforce-ai* | 712 likes, 359k downloads  
  GGUF quant of the 35B Ornith MoE model; trending due to its permissive MIT license and endpoint compatibility.

- **[Jackrong/Qwopus3.6-35B-A3B-Coder-MTP-GGUP](https://huggingface.co/Jackrong/Qwopus3.6-35B-A3B-Coder-MTP-GGUF)** — *Jackrong* | 131 likes, 59k downloads  
  A GGUF quant of a coder fine-tune on Qwen3.6 MoE; notable for its MTP (Multi-Token Prediction) optimization.

---

### 3. Ecosystem Signal

The ecosystem is decisively shifting toward **Mixture-of-Experts (MoE) architectures** as the dominant paradigm for both dense and sparse scaling. The **Qwen3.5/3.6** and **GLM-5.2** model families are pulling away from the pack, with the former spawning dozens of community fine-tunes and the latter becoming a preferred base for optimization. NVIDIA is cementing its role as an enterprise infrastructure provider by releasing **NVFP4 quantizations** of both families, signaling a move beyond pure hardware into model optimization as a service. The **open-weight vs proprietary** front is increasingly blurred: models like **Ornith-1.0** (MIT license) and **Leanstral** (Apache-2.0) are challenging closed alternatives, while Qwen and GLM maintain strong guardrails. Quantization activity remains extremely high, with GGUF variants dominating local deployment, but new formats like **Pytorch-native FP4** are emerging. Notably, **agentic and coding-focused fine-tunes** (e.g., Gemma-4-coder, Qwen-AgentWorld) are the hottest sub-niche, reflecting the industry’s pivot toward agentic AI and developer tooling.

---

### 4. Worth Exploring

1. **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** — One of the most downloaded models this week for a reason: it sets a new bar for 3B-scale object localization in images. Worth studying for any vision pipeline requiring high-accuracy feature extraction without a huge model footprint.

2. **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)** — This model represents the cutting edge of open-weight code reasoning in a GGUF package. Its 2.5k likes in a single week and 641k downloads make it a must-try for any developer looking to run a top-tier coding assistant locally.

3. **[fal/LTX-2.3-3DREAL-LoRA](https://huggingface.co/fal/LTX-2.3-3DREAL-LoRA)** — For those interested in generative AI beyond text and image, this LoRA for video-to-3D generation is an early glimpse into the next wave of creative AI tools. Even with zero downloads, its novelty and connection to the LTX ecosystem make it a model worth monitoring.

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*