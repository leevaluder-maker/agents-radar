# Hugging Face Trending Models Digest 2026-07-12

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-07-12 01:50 UTC

---

Here is the structured **Hugging Face Trending Models Digest** for **2026-07-12**.

---

## 1. Today’s Highlights

This week’s trending models show a clear shift toward **massive MoE architectures** with highly accessible GGUF quantizations, led by the **Qwen3.6** and **GLM-5.2** ecosystems. **Nvidia** continues its aggressive open-weight push with three new entries—including a 3B vision model for object localization and a 75B ternary-precision reasoning MoE. The community is also mobilizing around **agentic and coding workflows**, with models like `gemma-4-12B-agentic-fable5` and `Ornith-1.0-35B` gaining rapid adoption. Notably, **vision-language MoEs** are dominating the top of the likes and downloads charts, indicating that multimodal reasoning is now the default expectation for new base models.

---

## 2. Trending Models by Category

### 🧠 Language Models (LLMs, chat models, instruction-tuned)

- **[GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)**  
  *zai-org* | 3,832 likes | 421k downloads  
  A massive MoE conversational model from the GLM family, trending as one of the most liked models of the week due to strong Chinese-English bilingual performance and an open-weight release.

- **[Tess-4-27B](https://huggingface.co/migtissera/Tess-4-27B)**  
  *migtissera* | 84 likes | 806 downloads  
  A Qwen3.5-based vision-language chat model, gaining traction for its strong reasoning and clean instruction-following in multimodal settings.

- **[AliesTaha/fable-traces](https://huggingface.co/AliesTaha/fable-traces)**  
  *AliesTaha* | 199 likes | 5k downloads  
  A Qwen3 instruct model fine-tuned on "fable" synthetic traces, trending as a compact, high-quality reasoning model for research.

- **[SupraLabs/Supra-Router-51M](https://huggingface.co/SupraLabs/Supra-Router-51M)**  
  *SupraLabs* | 98 likes | 1.3k downloads  
  A tiny 51M parameter routing model for LLM orchestration, drawing interest in the agentic and Mixture-of-Experts research community.

### 🎨 Multimodal & Generation (image, video, audio, text-to-X)

- **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)**  
  *nvidia* | 2,707 likes | 1.47M downloads  
  A lightweight 3B vision model for object localization and referring expression comprehension, trending for its simplicity and high accuracy.

- **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)**  
  *baidu* | 1,929 likes | 1.38M downloads  
  A general-purpose OCR foundation model supporting unlimited-length text recognition, widely adopted for document processing pipelines.

- **[krea/Krea-2-Turbo](https://huggingface.co/krea/Krea-2-Turbo)**  
  *krea* | 588 likes | 168k downloads  
  A fast text-to-image diffusion model based on Krea-2-Raw, trending for its speed-to-quality ratio in creative workflows.

- **[Alissonerdx/LTX-Best-Face-ID](https://huggingface.co/Alissonerdx/LTX-Best-Face-ID)**  
  *Alissonerdx* | 99 likes | 0 downloads  
  A identity-preservation LoRA for LTX-video, enabling reference-to-video face generation, niche but highly anticipated in the video generation community.

- **[OpenMOSS-Team/MOSS-Transcribe-Diarize](https://huggingface.co/OpenMOSS-Team/MOSS-Transcribe-Diarize)**  
  *OpenMOSS-Team* | 109 likes | 12.8k downloads  
  An audio-text model for simultaneous transcription and speaker diarization, trending for its practical utility in meeting and call analysis.

- **[CohereLabs/cohere-transcribe-arabic-07-2026](https://huggingface.co/CohereLabs/cohere-transcribe-arabic-07-2026)**  
  *CohereLabs* | 90 likes | 7.7k downloads  
  Cohere’s latest ASR model for Arabic, showing strong industry investment in non-English speech recognition.

### 🔧 Specialized Models (code, math, medical, embeddings)

- **[google/tabfm-1.0.0-pytorch](https://huggingface.co/google/tabfm-1.0.0-pytorch)**  
  *google* | 348 likes | 20k downloads  
  Google’s zero-shot tabular foundation model in PyTorch, trending as a strong alternative to deep learning on structured data.

- **[nvidia/NVIDIA-Nemotron-Labs-3-Puzzle-75B-A9B-NVFP4](https://huggingface.co/nvidia/NVIDIA-Nemotron-Labs-3-Puzzle-75B-A9B-NVFP4)**  
  *nvidia* | 106 likes | 30.4k downloads  
  A 75B reasoning MoE with **NVFP4** ternary precision, pushing the frontier of ultra-low-bit deployment for high-performance reasoning.

- **[nvidia/Nemotron-Labs-Audex-30B-A3B](https://huggingface.co/nvidia/Nemotron-Labs-Audex-30B-A3B)**  
  *nvidia* | 120 likes | 743 downloads  
  Nvidia’s audio understanding MoE, specialized for auditing and speech analytics, expanding the Nemotron Labs ecosystem.

- **[mistralai/Leanstral-1.5-119B-A6B](https://huggingface.co/mistralai/Leanstral-1.5-119B-A6B)**  
  *mistralai* | 189 likes | 350 downloads  
  Mistral’s lean 119B MoE (6B active), fine-tuned from their 2603 base, trending for its efficiency and Apache-2.0 license.

### 📦 Fine-tunes & Quantizations (community fine-tunes, GGUF, AWQ)

- **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)**  
  *HauhauCS* | 2,651 likes | 2.64M downloads  
  A 35B MoE uncensored Qwen3.6 variant in GGUF, trending due to high download volume and strong demand for unrestricted reasoning models.

- **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)**  
  *empero-ai* | 2,015 likes | 1.94M downloads  
  A GGUF quantized 9B vision-language model fine-tuned on synthetic Claude data, popular for local deployment of multimodal reasoning.

- **[unsloth/Qwen3.6-27B-MTP-GGUF](https://huggingface.co/unsloth/Qwen3.6-27B-MTP-GGUF)**  
  *unsloth* | 1,048 likes | 2.9M downloads  
  The most downloaded model of the week; a Qwen3.6 27B GGUF with Multi-Token Prediction, optimized for speed and human-like text generation.

- **[yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF)**  
  *yuxinlu1* | 1,150 likes | 436k downloads  
  A fine-tuned Gemma-4 GGUF for coding and agentic terminal use, trending at the intersection of agentic AI and quantized deployment.

- **[deepreinforce-ai/Ornith-1.0-35B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF)**  
  *deepreinforce-ai* | 850 likes | 1.22M downloads  
  A widely downloaded MIT-licensed 35B GGUF, trending as a general-purpose, uncensored chat model for local inference.

- **[GnLOLot/MiniCPM5-1B-Claude-Opus-Fable5-Thinking-GGUF](https://huggingface.co/GnLOLot/MiniCPM5-1B-Claude-Opus-Fable5-Thinking-GGUF)**  
  *GnLOLot* | 191 likes | 29.9k downloads  
  A 1B thinking GGUF model, showing community interest in small, fast reasoning models for edge deployment.

- **[froggeric/Qwen-Fixed-Chat-Templates](https://huggingface.co/froggeric/Qwen-Fixed-Chat-Templates)**  
  *froggeric* | 852 likes | 0 downloads  
  A template-only repository fixing Qwen chat templates for MLX and Jinja, anomalously high-liked for a non-model asset, reflecting developer frustration with template fragmentation.

---

## 3. Ecosystem Signal

The **Qwen3.5/3.6 family** is clearly the dominant model lineage this week, underpinning 7 of the top 30 entries across base models, fine-tunes, and quantizations—including the #1 downloaded model (Unsloth’s Qwen3.6-27B GGUF). **MoE** (Mixture-of-Experts) has become the default architecture for new large releases, with models like GLM-5.2, Nemotron-Puzzle-75B, and Leanstral-1.5 all deploying sparse activation ratios between 5-10% of total parameters. On the **open-weight** front, Nvidia and Mistral are leading with Apache-2.0 licenses, signaling a continued industry shift toward permissive open release for large-scale research and commercial use. **GGUF quantization** remains the backbone of community adoption: 10 of the 30 trending models are GGUF files, and the top 3 models by download count are all GGUF variants. This confirms that ease of local inference on consumer hardware (llama.cpp, vLLM, MLX) is the primary driver of mass adoption. Finally, the rise of **identity-preservation video LoRAs** (LTX-Best-Face-ID) and **reference-to-video** models suggests the next wave of generative AI is moving beyond images into controlled video synthesis.

---

## 4. Worth Exploring

1. **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** – A standout 3B vision model that achieves state-of-the-art object localization with minimal compute. Ideal for robotics, RAG-on-images, and visual agent pipelines.

2. **[unsloth/Qwen3.6-27B-MTP-GGUF](https://huggingface.co/unsloth/Qwen3.6-27B-MTP-GGUF)** – The week’s most downloaded model, combining Qwen3.6’s strong multimodal reasoning with Multi-Token Prediction and high-quality GGUF quantization. A must-test for anyone deploying capable MoE models locally.

3. **[nvidia/NVIDIA-Nemotron-Labs-3-Puzzle-75B-A9B-NVFP4](https://huggingface.co/nvidia/NVIDIA-Nemotron-Labs-3-Puzzle-75B-A9B-NVFP4)** – A research-forward 75B MoE with ternary NVFP4 precision. Worth studying for its ultra-low-bit reasoning capabilities and potential to reshape efficient deployment of large MoEs on edge hardware.

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*