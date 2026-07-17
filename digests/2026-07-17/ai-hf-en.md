# Hugging Face Trending Models Digest 2026-07-17

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-07-17 01:50 UTC

---

**Hugging Face Trending Models Digest — 2026-07-17**

### 1. Today’s Highlights

This week’s trending models reveal a clear shift toward extreme quantization and MoE architectures for efficient deployment. **Tencent’s Hy3** and **zai-org/GLM-5.2** represent strong releases from major labs, while the **prism-ml/Ternary-Bonsai** and **Bonsai** series push boundaries with 1-bit and 2-bit quantized 27B models. The **Qwythos-9B** family from empero-ai continues to dominate downloads, and **baidu/Unlimited-OCR** signals growing AI-driven OCR demand. The ecosystem is also seeing a burst of GGUF/MLX community ports, particularly around Qwen 3.5/3.6-based models.

---

### 2. Trending Models by Category

#### 🧠 Language Models (LLMs, chat models, instruction-tuned)

- **[thinkingmachines/Inkling](https://huggingface.co/thinkingmachines/Inkling)**  
  Author: thinkingmachines | Likes: 810 | Downloads: 4  
  A new image-text-to-text multimodal model, trending for its “inkling” reasoning approach and early community buzz despite low downloads.

- **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)**  
  Author: zai-org | Likes: 4,029 | Downloads: 513,061  
  A 5.2B MoE language model from Zhipu AI, trending for its strong performance in conversational and text generation tasks.

- **[tencent/Hy3](https://huggingface.co/tencent/Hy3)**  
  Author: tencent | Likes: 813 | Downloads: 11,849  
  A new Hunyuan-based text-generation model from Tencent, gaining attention as a capable open-weight alternative.

- **[deepreinforce-ai/Ornith-1.0-35B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF)**  
  Author: deepreinforce-ai | Likes: 902 | Downloads: 1,785,575  
  A 35B GGUF model from deepreinforce-ai, trending due to massive download volume and MIT licensing.

- **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)**  
  Author: HauhauCS | Likes: 2,787 | Downloads: 2,328,315  
  An uncensored MoE vision-language model based on Qwen 3.6, wildly popular for its aggressive finetune and high download count.

- **[InternScience/Agents-A1](https://huggingface.co/InternScience/Agents-A1)**  
  Author: InternScience | Likes: 568 | Downloads: 33,400  
  A MoE model optimized for agentic tasks, gaining traction for its Qwen 3.5-based design and image-text-to-text capabilities.

- **[yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF)**  
  Author: yuxinlu1 | Likes: 1,208 | Downloads: 506,068  
  A heavily fine-tuned Gemma 4 GGUF for coding and terminal use, trending for its “agentic” prompt style and composer v2 fusion.

- **[froggeric/Qwen-Fixed-Chat-Templates](https://huggingface.co/froggeric/Qwen-Fixed-Chat-Templates)**  
  Author: froggeric | Likes: 924 | Downloads: 0  
  A utility model fixing Qwen chat templates, trending among MLX users for its Jinja template corrections.

#### 🎨 Multimodal & Generation (image, video, audio, text-to-X)

- **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)**  
  Author: empero-ai | Likes: 2,237 | Downloads: 2,042,670  
  A GGUF-quantized 9B image-text-to-text model, extremely popular for its combination of Qwen 3.5 base and rich reasoning prompts.

- **[tencent/Hy3](https://huggingface.co/tencent/Hy3)** (also listed above)  
  Multimodal text generation via Hunyuan v3 architecture.

- **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)**  
  Author: baidu | Likes: 2,010 | Downloads: 1,852,722  
  Baidu’s flagship OCR model, trending for its powerful feature extraction and high adoption in document processing workflows.

- **[ATH-MaaS/OvisOCR2](https://huggingface.co/ATH-MaaS/OvisOCR2)**  
  Author: ATH-MaaS | Likes: 136 | Downloads: 3,678  
  A Qwen 3.5-based OCR model from ATH-MaaS, gaining traction as a specialized vision-to-text tool.

- **[Wan-AI/Wan-Dancer-14B](https://huggingface.co/Wan-AI/Wan-Dancer-14B)**  
  Author: Wan-AI | Likes: 92 | Downloads: 1,884  
  A 14B image-to-video model from Wan-AI, trending for dance/figure generation with Diffusers integration.

- **[Alissonerdx/LTX-Best-Face-ID](https://huggingface.co/Alissonerdx/LTX-Best-Face-ID)**  
  Author: Alissonerdx | Likes: 167 | Downloads: 0  
  A LoRA for LTX video models focused on identity-preserved face generation, trending among video creators.

- **[Cseti/LTX2.3-22B_IC-LoRA-CrossView-Prompt](https://huggingface.co/Cseti/LTX2.3-22B_IC-LoRA-CrossView-Prompt)**  
  Author: Cseti | Likes: 77 | Downloads: 0  
  A novel-view synthesis LoRA for LTX 2.3 video models, gaining interest for its cross-view prompt design.

- **[OpenMOSS-Team/MOSS-Transcribe-Diarize](https://huggingface.co/OpenMOSS-Team/MOSS-Transcribe-Diarize)**  
  Author: OpenMOSS-Team | Likes: 232 | Downloads: 75,105  
  An audio-to-text model for speech transcription and diarization, trending for its robust MOSS-based pipeline.

#### 🔧 Specialized Models (code, math, medical, embeddings)

- **[conradlocke/krea2-identity-edit](https://huggingface.co/conradlocke/krea2-identity-edit)**  
  Author: conradlocke | Likes: 322 | Downloads: 0  
  A LoRA for identity-preserving image editing on Krea-2-Raw, trending among ComfyUI users for consistent character edits.

- **[Cactus-Compute/needle](https://huggingface.co/Cactus-Compute/needle)**  
  Author: Cactus-Compute | Likes: 248 | Downloads: 733  
  A JAX-native function-calling and tool-use model, gaining attention for its needle-like precision in structured tasks.

#### 📦 Fine-tunes & Quantizations (community fine-tunes, GGUF, AWQ)

- **[prism-ml/Ternary-Bonsai-27B-gguf](https://huggingface.co/prism-ml/Ternary-Bonsai-27B-gguf)**  
  Author: prism-ml | Likes: 605 | Downloads: 74,007  
  A 27B model quantized to 2-bit ternary weights, trending for extreme compression while retaining conversational quality.

- **[prism-ml/Bonsai-27B-gguf](https://huggingface.co/prism-ml/Bonsai-27B-gguf)**  
  Author: prism-ml | Likes: 341 | Downloads: 559,267  
  A 1-bit GGUF quantization of a 27B model from the same family, extremely popular for its efficiency.

- **[unsloth/Qwen3.6-27B-NVFP4](https://huggingface.co/unsloth/Qwen3.6-27B-NVFP4)**  
  Author: unsloth | Likes: 216 | Downloads: 1,712,974  
  A 4-bit NVFP4 quantized version of Qwen 3.6-27B from Unsloth, trending for its high-quality quantization and massive download count.

- **[prism-ml/Ternary-Bonsai-27B-mlx-2bit](https://huggingface.co/prism-ml/Ternary-Bonsai-27B-mlx-2bit)**  
  Author: prism-ml | Likes: 84 | Downloads: 7,622  
  An MLX port of the Ternary Bonsai 27B at 2-bit, trending among Apple Silicon users.

- **[prism-ml/Bonsai-27B-mlx-1bit](https://huggingface.co/prism-ml/Bonsai-27B-mlx-1bit)**  
  Author: prism-ml | Likes: 82 | Downloads: 10,760  
  An MLX 1-bit port of Bonsai, gaining adoption for running 27B models on consumer hardware.

- **[jlnsrk/GLM-5.2-colibri-int4](https://huggingface.co/jlnsrk/GLM-5.2-colibri-int4)**  
  Author: jlnsrk | Likes: 119 | Downloads: 2,621  
  An int4 expert-streaming quantization of GLM-5.2, trending for CPU-friendly MoE inference.

- **[GnLOLot/MiniCPM5-1B-Claude-Opus-Fable5-Thinking-GGUF](https://huggingface.co/GnLOLot/MiniCPM5-1B-Claude-Opus-Fable5-Thinking-GGUF)**  
  Author: GnLOLot | Likes: 264 | Downloads: 121,296  
  A GGUF of a 1B MiniCPM5 thinking model, trending for its small size and “Claude Opus” prompt style.

- **[GnLOLot/MiniCPM5-1B-Claude-Opus-Fable5-V2-Thinking-GGUF](https://huggingface.co/GnLOLot/MiniCPM5-1B-Claude-Opus-Fable5-V2-Thinking-GGUF)**  
  Author: GnLOLot | Likes: 95 | Downloads: 3,691  
  A V2 version of the above, with improved thinking and quantization.

- **[GnLOLot/MiniCPM5-1B-Claude-Opus-Fable5-Thinking](https://huggingface.co/GnLOLot/MiniCPM5-1B-Claude-Opus-Fable5-Thinking)**  
  Author: GnLOLot | Likes: 131 | Downloads: 4,117  
  The original HuggingFace transformers version of the 1B thinking MiniCPM5 model.

- **[AngelSlim/Hy3-GGUF](https://huggingface.co/AngelSlim/Hy3-GGUF)**  
  Author: AngelSlim | Likes: 117 | Downloads: 80,796  
  A GGUF community port of Tencent’s Hy3, popular for its Apache-2.0 license.

- **[empero-ai/Qwythos-9B-v2-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-v2-GGUF)**  
  Author: empero-ai | Likes: 150 | Downloads: 89,107  
  A version 2 GGUF of the Qwythos 9B, benefiting from the original’s massive popularity.

- **[empero-ai/Qwythos-9B-v2](https://huggingface.co/empero-ai/Qwythos-9B-v2)**  
  Author: empero-ai | Likes: 129 | Downloads: 6,220  
  The non-quantized v2 of Qwythos 9B, available in transformers/safetensors format.

---

### 3. Ecosystem Signal

The **Qwen 3.5/3.6** family has become the dominant backbone for trending models this week. Of the 30 trending models, at least 12 are directly based on Qwen variants, including multiple quantizations, finetunes, and OCR extensions. This mirrors Qwen’s broader ecosystem momentum as a strong open-weight alternative to GPT-4 class models.

**Extreme quantization** continues to gain steam: 1-bit and 2-bit models (Bonsai, Ternary-Bonsai) are seeing significant community interest, reflecting a strong demand for running large models on consumer-grade hardware. The **GGUF format** remains the most popular quantization target, with 15+ models using it, while **MLX** ports are growing for Apple Silicon users.

**MoE architecture** is another clear trend. GLM-5.2, Agents-A1, and Qwen 3.6-35B-MoE all leverage Mixture-of-Experts, indicating the community is prioritizing efficiency without sacrificing parameter count.

On the fine-tuning side, **“Mythos” and “Fable” prompt styles** (inspired by Claude Opus stylizations) are highly popular, showing that prompt engineering and role-prompted models are driving adoption as much as raw performance.

**OCR** is having a moment: both **baidu/Unlimited-OCR** and **ATH-MaaS/OvisOCR2** are trending, signaling increased demand for document understanding and structured data extraction from images.

---

### 4. Worth Exploring

1. **[tencent/Hy3](https://huggingface.co/tencent/Hy3)** — A strong new open-weight model from Tencent’s Hunyuan team. With the GGUF port already trending, it’s worth exploring for high-quality text generation with competitive licensing.

2. **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)** — Baidu’s OCR model is a standout for document processing tasks. With 1.8M downloads and 2k+ likes, it’s a must-try for any vision-to-text pipeline.

3. **[prism-ml/Ternary-Bonsai-27B-gguf](https://huggingface.co/prism-ml/Ternary-Bonsai-27B-gguf)** — The most extreme quantization in this week’s trending list. Running a 27B model at 2-bit ternary weights is a technical achievement worth studying for efficient deployment.

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*