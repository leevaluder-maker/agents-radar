# Hugging Face Trending Models Digest 2026-07-15

> Source: [Hugging Face Hub](https://huggingface.co/) | 30 models | Generated: 2026-07-15 01:26 UTC

---

# 🤗 Hugging Face Trending Models Digest — 2026-07-15

## 1. Today's Highlights

This week's trending ecosystem is dominated by **Qwen3.5/3.6 derivatives** and **GGUF quantizations**, with several 9B–35B MoE models attracting massive download volumes. Qwen-based fine-tunes like `Qwythos-9B` and `HauhauCS/Qwen3.6-35B-A3B-Uncensored` are seeing millions of downloads, signaling strong community appetite for accessible, locally-runnable reasoning models. NVIDIA's Nemotron Labs continues expanding its specialized MoE lineup, while new entrants in video (LingBot) and speech (Gepard) show multimodal diversification. The GLM-5.2 family also resurges with strong engagement, and we see emerging interest in **extreme quantization** (1-bit and ternary Bonsai models) for ultra-low-resource deployment.

## 2. Trending Models by Category

### 🧠 Language Models (LLMs, chat models, instruction-tuned)

- **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** — *zai-org* — Likes: 3,948 | Downloads: 489,611  
  A conversational MoE model with DSA attention; trending as the highest-liked model this week, likely from strong chat performance and efficient inference.

- **[bottlecapai/ThinkingCap-Qwen3.6-27B](https://huggingface.co/bottlecapai/ThinkingCap-Qwen3.6-27B)** — *bottlecapai* — Likes: 341 | Downloads: 6,208  
  A reasoning-focused Qwen 3.6 fine-tune; gaining traction for enhanced step-by-step thinking capabilities in a 27B package.

- **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** — *HauhauCS* — Likes: 2,730 | Downloads: 2,443,871  
  An uncensored, vision-capable 35B MoE GGUF with aggressive tuning; extremely popular for unrestricted use cases and high throughput.

- **[nvidia/NVIDIA-Nemotron-Labs-3-Puzzle-75B-A9B-NVFP4](https://huggingface.co/nvidia/NVIDIA-Nemotron-Labs-3-Puzzle-75B-A9B-NVFP4)** — *nvidia* — Likes: 117 | Downloads: 41,755  
  NVIDIA's 75B MoE with NVFP4 quantization; trending for pushing state-of-the-art in efficient large-scale inference.

- **[nvidia/Nemotron-Labs-Audex-30B-A3B](https://huggingface.co/nvidia/Nemotron-Labs-Audex-30B-A3B)** — *nvidia* — Likes: 149 | Downloads: 1,332  
  A 30B active-parameter MoE for specialized reasoning; part of NVIDIA's growing open-weight Nemotron Labs suite.

- **[InternScience/Agents-A1](https://huggingface.co/InternScience/Agents-A1)** — *InternScience* — Likes: 538 | Downloads: 30,539  
  A Qwen 3.5 MoE derivative optimized for agentic tool use; rising due to autonomous agent community interest.

- **[deepreinforce-ai/Ornith-1.0-35B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF)** — *deepreinforce-ai* — Likes: 880 | Downloads: 1,533,354  
  A 35B GGUF with MIT license and endpoint compatibility; widely downloaded for production-ready local deployment.

- **[migtissera/Tess-4-27B](https://huggingface.co/migtissera/Tess-4-27B)** — *migtissera* — Likes: 112 | Downloads: 1,262  
  A Qwen 3.5-based vision-language model; noted for solid multimodal reasoning in a compact 27B form.

- **[yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF)** — *yuxinlu1* — Likes: 1,189 | Downloads: 468,629  
  A highly-tuned Gemma 4 derivative for agentic and terminal coding tasks; trending for combining code reasoning with lightweight GGUF format.

### 🎨 Multimodal & Generation (image, video, audio, text-to-X)

- **[tencent/Hy3](https://huggingface.co/tencent/Hy3)** — *tencent* — Likes: 781 | Downloads: 10,406  
  Tencent's Hunyuan V3 text-generation model; drawing attention for its unified architecture and enterprise backing.

- **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)** — *baidu* — Likes: 1,983 | Downloads: 1,715,301  
  Baidu's image-text-to-text OCR model; massively downloaded for its unlimited-scene OCR capability and broad language support.

- **[conradlocke/krea2-identity-edit](https://huggingface.co/conradlocke/krea2-identity-edit)** — *conradlocke* — Likes: 288 | Downloads: 0  
  A LoRA for identity-preserving image editing built on Krea-2; trending for enabling consistent character edits in ComfyUI workflows.

- **[robbyant/lingbot-world-v2-14b-causal-fast](https://huggingface.co/robbyant/lingbot-world-v2-14b-causal-fast)** — *robbyant* — Likes: 96 | Downloads: 0  
  A 14B world model for image-to-video generation; noted for fast causal video synthesis and open-world modeling.

- **[robbyant/lingbot-video-moe-30b-a3b](https://huggingface.co/robbyant/lingbot-video-moe-30b-a3b)** — *robbyant* — Likes: 104 | Downloads: 700  
  An MoE video diffusion model; trending in the video generation community for efficient scaling.

- **[Alissonerdx/LTX-Best-Face-ID](https://huggingface.co/Alissonerdx/LTX-Best-Face-ID)** — *Alissonerdx* — Likes: 141 | Downloads: 0  
  A LoRA for identity-preserving text-to-video with LTX; new entry for consistent face generation in video.

- **[mgwr/M87](https://huggingface.co/mgwr/M87)** — *mgwr* — Likes: 106 | Downloads: 2,408  
  A text-to-image LoRA based on Krea-2-Turbo; popular for fine-grained style control in diffusion pipelines.

- **[nineninesix/gepard-1.0](https://huggingface.co/nineninesix/gepard-1.0)** — *nineninesix* — Likes: 101 | Downloads: 5,872  
  A Qwen 3.5-based text-to-speech model; notable for TTS capability integrated into a text-generation pipeline.

- **[OpenMOSS-Team/MOSS-Transcribe-Diarize](https://huggingface.co/OpenMOSS-Team/MOSS-Transcribe-Diarize)** — *OpenMOSS-Team* — Likes: 189 | Downloads: 65,109  
  An audio-text-to-text model combining transcription with speaker diarization; widely used for meeting and call processing.

### 🔧 Specialized Models (code, math, medical, embeddings, OCR)

- **(No strictly specialized models beyond those already categorized; OCR is listed under Multimodal)**

### 📦 Fine-tunes & Quantizations (community fine-tunes, GGUF, AWQ)

- **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)** — *empero-ai* — Likes: 2,156 | Downloads: 2,006,265  
  A Qwen 3.5 GGUF fine-tune with Claude-style reasoning; trending due to strong reasoning benchmarks and efficient 9B quantization for local use.

- **[empero-ai/Qwythos-9B-v2-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-v2-GGUF)** — *empero-ai* — Likes: 129 | Downloads: 70,260  
  v2 of the popular Qwythos GGUF series; refined chat and reasoning performance.

- **[empero-ai/Qwythos-9B-v2](https://huggingface.co/empero-ai/Qwythos-9B-v2)** — *empero-ai* — Likes: 115 | Downloads: 3,959  
  The non-quantized safetensors version of Qwythos-9B-v2; serves as base for the GGUF quantizations above.

- **[GnLOLot/MiniCPM5-1B-Claude-Opus-Fable5-Thinking-GGUF](https://huggingface.co/GnLOLot/MiniCPM5-1B-Claude-Opus-Fable5-Thinking-GGUF)** — *GnLOLot* — Likes: 233 | Downloads: 89,892  
  A 1B MiniCPM5 GGUF with Claude-inspired thinking; surprisingly high engagement for a ultra-small model, reflecting demand for tiny reasoning models.

- **[unsloth/DeepSeek-V4-Flash-GGUF](https://huggingface.co/unsloth/DeepSeek-V4-Flash-GGUF)** — *unsloth* — Likes: 172 | Downloads: 55,222  
  Unsloth's high-speed GGUF quantization of DeepSeek-V4; popular for extremely fast inference on consumer hardware.

- **[unsloth/Qwen3.6-27B-MTP-GGUF](https://huggingface.co/unsloth/Qwen3.6-27B-MTP-GGUF)** — *unsloth* — Likes: 1,091 | Downloads: 2,904,515  
  Unsloth's Multi-Token Prediction GGUF for Qwen 3.6 27B; the most downloaded model this week, driven by MTP speed gains and unsloth's optimization.

- **[unsloth/Qwen3.6-27B-NVFP4](https://huggingface.co/unsloth/Qwen3.6-27B-NVFP4)** — *unsloth* — Likes: 204 | Downloads: 1,599,150  
  NVFP4 quantization of Qwen 3.6 27B; trending for NVIDIA 4-bit floating-point format enabling low-latency inference on Ada/Blackwell GPUs.

- **[froggeric/Qwen-Fixed-Chat-Templates](https://huggingface.co/froggeric/Qwen-Fixed-Chat-Templates)** — *froggeric* — Likes: 902 | Downloads: 0  
  A template-fixing utility for Qwen models in MLX and llama.cpp; valuable for developers struggling with inconsistent chat formatting.

- **[prism-ml/Ternary-Bonsai-27B-gguf](https://huggingface.co/prism-ml/Ternary-Bonsai-27B-gguf)** — *prism-ml* — Likes: 146 | Downloads: 23  
  A 2-bit ternary quantization of a 27B model; pushing extreme compression boundaries for ELI5-level inference.

- **[prism-ml/Bonsai-27B-gguf](https://huggingface.co/prism-ml/Bonsai-27B-gguf)** — *prism-ml* — Likes: 89 | Downloads: 513  
  A 1-bit binary quantization of a 27B model; experimental but gaining attention for near-lossless extreme compression.

- **[jlnsrk/GLM-5.2-colibri-int4](https://huggingface.co/jlnsrk/GLM-5.2-colibri-int4)** — *jlnsrk* — Likes: 102 | Downloads: 2,188  
  INT4 quantization of GLM-5.2 with expert streaming for CPU-friendly MoE inference; trending for affordable large-model deployment on CPU.

- **[open-gigaai/Giga-World-1](https://huggingface.co/open-gigaai/Giga-World-1)** — *open-gigaai* — Likes: 132 | Downloads: 0  
  A new world model diffusion pipeline; tagged for US region and Apache-2.0 license, signaling open video generation effort.

## 3. Ecosystem Signal

The **Qwen ecosystem** (3.5/3.6) has become the dominant foundation for community fine-tuning, with nearly half of top models derived from it. Qwen's permissive license, strong MoE variants (35B-A3B, 27B), and aggressive quantization compatibility make it the go-to base for both uncensored and reasoning-tuned variants. **GLM-5.2** shows surprising longevity, ranking 1st in likes — its DSA MoE attention and strong conversational performance keep it relevant months after release.

**Open-weight momentum** continues accelerating: NVIDIA's Nemotron Labs is consistently releasing competitive MoE models (75B, 30B) with NVFP4 quantization, while Baidu's Unlimited-OCR shows that even traditional AI labs are releasing fully open models with multi-million downloads. The **MoE paradigm** is now mainstream — every major family (Qwen, GLM, Nemotron, LingBot) uses Mixture-of-Experts for efficiency.

**Quantization innovation** is a clear trend: we see competition between GGUF (Unsloth, Empero), NVFP4 (NVIDIA/Unsloth), INT4 (GLM-colibri), and even 1-bit/ternary formats (Prism-ML). This reflects growing demand for running 27B–75B models on consumer hardware and CPUs. The massive download numbers for GGUF variants (2M+ for Qwythos-9B and 2.9M for Unsloth's Qwen 3.6 MTP) confirm that **local inference is the dominant use case** driving Hugging Face traffic today.

## 4. Worth Exploring

1. **[unsloth/Qwen3.6-27B-MTP-GGUF](https://huggingface.co/unsloth/Qwen3.6-27B-MTP-GGUF)** — The most-downloaded model this week (2.9M) using Multi-Token Prediction for 2-3x speedup. Anyone building local inference pipelines should study how MTP acceleration works in practice and whether it preserves quality.

2. **[prism-ml/Ternary-Bonsai-27B-gguf](https://huggingface.co/prism-ml/Ternary-Bonsai-27B-gguf)** — At 2-bit ternary quantization, this model tests the limits of lossy compression. Worth exploring for edge deployment research, ultra-low-resource settings, or studying the quality-compression frontier.

3. **[yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF)** — Combines one of the best fine-tuning recipes (Fable, Composer2.5) with Gemma 4's strong code reasoning in a small 12B GGUF. Excellent study subject for agentic tool-use fine-tuning methodology.

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*