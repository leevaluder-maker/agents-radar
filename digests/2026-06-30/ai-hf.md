# Hugging Face 热门模型日报 2026-06-30

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-06-29 16:05 UTC

---

好的，作为AI模型生态分析师，以下是基于2026年6月30日数据生成的《Hugging Face 热门模型日报》。

---

### **Hugging Face 热门模型日报 | 2026年6月30日**

#### **今日速览**

本周 Hugging Face 生态呈现出两大显著趋势：一是以 **GLM-5.2** 和 **Qwen3.5/3.6** 为代表的 MoE（混合专家）架构大规模应用，促使社区涌现了大量针对性的量化版本和微调模型；二是 **DeepSeek-V4** 系列模型的发布引发了高度关注，其 DSpark 变体聚焦于快速推理，预示着新一代专为“推理”优化的模型竞争加剧。此外，视觉理解模型（如 Nvidia 的 LocateAnything）和多模态 Agent 模型也获得了社区热捧，标志着AI能力正从纯文本向更复杂的交互与感知方向进化。

---

### **热门模型**

#### 🧠 语言模型（LLM、对话模型、指令微调）

- **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** | 作者: zai-org | 点赞: 2,899 | 下载: 133,350
  - **说明**: 智谱AI的旗舰级MoE语言模型，凭借极高的点赞数成为本周焦点，代表了国产开源大模型的最新进展。
- **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** | 作者: HauhauCS | 点赞: 2,328 | 下载: 3,089,944
  - **说明**: 基于 Qwen3.6 的社区微调版，主打“无审查”和“激进风格”，下载量极高，反映了社区对模型个性化和开放性控制的需求。
- **[deepseek-ai/DeepSeek-V4-Pro-DSpark](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-DSpark)** | 作者: deepseek-ai | 点赞: 205 | 下载: 5,460
  - **说明**: DeepSeek 最新旗舰模型 V4 的 Pro 版本，配套“DSpark”推理加速技术，标志着从模型能力向高效部署的转变。
- **[deepreinforce-ai/Ornith-1.0-35B](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B)** | 作者: deepreinforce-ai | 点赞: 228 | 下载: 38,857
  - **说明**: 基于 Qwen3.5 的 MoE 变体，其全系列（9B/35B/397B）同时发布，生态完整，是社区微调热门选择。
- **[WeiboAI/VibeThinker-3B](https://huggingface.co/WeiboAI/VibeThinker-3B)** | 作者: WeiboAI | 点赞: 746 | 下载: 63,449
  - **说明**: 一个专注于数学推理的 3B 小模型，表明模型小型化和专业化趋势并行，小模型在特定任务上潜力巨大。
- **[nvidia/Qwen3.6-35B-A3B-NVFP4](https://huggingface.co/nvidia/Qwen3.6-35B-A3B-NVFP4)** | 作者: nvidia | 点赞: 376 | 下载: 5,392,518
  - **说明**: 英伟达官方对 Qwen3.6 的 4-bit FP4 量化版本，将MoE模型的部署门槛降到极低，下载量惊人。
- **[microsoft/FastContext-1.0-4B-SFT](https://huggingface.co/microsoft/FastContext-1.0-4B-SFT)** | 作者: microsoft | 点赞: 369 | 下载: 7,027
  - **说明**: 微软发布的小模型，侧重长上下文处理与 Agent 能力，预示着未来小模型在复杂工作流中的应用。
- **[deepseek-ai/DeepSeek-V4-Flash-DSpark](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-DSpark)** | 作者: deepseek-ai | 点赞: 89 | 下载: 2,239
  - **说明**: DeepSeek-V4 的“Flash”版本，旨在以更低成本实现快速推理，与 Pro 版形成高低搭配的组合策略。

#### 🎨 多模态与生成（图像、视频、音频、文本到X）

- **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)** | 作者: baidu | 点赞: 1,338 | 下载: 362,945
  - **说明**: 百度发布的全场景 OCR 模型，任务定义为“图像转文本”，高下载量印证了其在文档处理等场景的实用性。
- **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M)** | 作者: empero-ai | 点赞: 551 | 下载: 79,540
  - **说明**: 集成视觉能力的 9B 多模态模型，GGUF 量化版下载量接近百万，是社区进行多模态推理的主流选择。
- **[krea/Krea-2-Turbo](https://huggingface.co/krea/Krea-2-Turbo)** | 作者: krea | 点赞: 390 | 下载: 38,454
  - **说明**: Krea 发布的第二代图像生成模型 Turbo 版，相比 Raw 版更聚焦效率与速度，符合行业对即时生成的追求。
- **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** | 作者: nvidia | 点赞: 2,465 | 下载: 728,320
  - **说明**: 英伟达推出的“指哪打哪”视觉定位模型，在图像中精确识别目标的能力是计算机视觉领域的热门方向。
- **[nvidia/nemotron-3.5-asr-streaming-0.6b](https://huggingface.co/nvidia/nemotron-3.5-asr-streaming-0.6b)** | 作者: nvidia | 点赞: 739 | 下载: 76,154
  - **说明**: 专注于流式语音识别的小模型，为实时语音交互（如AI语音助手）提供了轻量级基础能力。
- **[fal/LTX-2.3-3DREAL-LoRA](https://huggingface.co/fal/LTX-2.3-3DREAL-LoRA)** | 作者: fal | 点赞: 110 | 下载: 0
  - **说明**: 用于图像生成视频的 LoRA，专注于生成逼真的 3D 效果，展现了社区在视频生成领域的精细化探索。

#### 🔧 专用模型（代码、数学、医疗、嵌入）

- **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)** | 作者: yuxinlu1 | 点赞: 2,496 | 下载: 561,577
  - **说明**: 基于Gemma 4的代码专用模型量化版，高点赞和高下载表明代码生成是当前最刚需的应用场景之一。
- **[yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF)** | 作者: yuxinlu1 | 点赞: 830 | 下载: 241,409
  - **说明**: 同样基于Gemma 4，但聚焦于“代理（Agent）”能力，表明Agent模型正在从概念走向具体实现。
- **[Chunjiang-Intelligence/DeepSeek-v4-Fable](https://huggingface.co/Chunjiang-Intelligence/DeepSeek-v4-Fable)** | 作者: Chunjiang-Intelligence | 点赞: 126 | 下载: 1,463
  - **说明**: 专注网络安全（Cybersecurity）的模型，展示了特定行业领域微调模型的细分市场。

#### 📦 微调与量化（社区微调、GGUF、AWQ）

- **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)** | 作者: empero-ai | 点赞: 893 | 下载: 907,682
  - **说明**: 该模型的无量化版本和 GGUF 版同时上榜，体现了社区对“模型+量化”组合发布模式的认可。
- **[deepreinforce-ai/Ornith-1.0-35B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF)** | 作者: deepreinforce-ai | 点赞: 450 | 下载: 123,598
  - **说明**: Ornith 系列的量化版，下载量远超其原始FP16版本，证明大模型消费级应用依赖于高效的量化技术。
- **[unsloth/GLM-5.2-GGUF](https://huggingface.co/unsloth/GLM-5.2-GGUF)** | 作者: unsloth | 点赞: 456 | 下载: 164,180
  - **说明**: 专业量化团队 unsloth 推出的 GLM-5.2 量化版，将官方模型转化为更易部署的 GGUF 格式，简化了推理流程。
- **[unsloth/Qwen-AgentWorld-35B-A3B-GGUF](https://huggingface.co/unsloth/Qwen-AgentWorld-35B-A3B-GGUF)** | 作者: unsloth | 点赞: 104 | 下载: 116,693
  - **说明**: 对 Qwen AgentWorld 模型进行量化，降低了运行世界模型的门槛，推动AI Agent研究普及。
- **[HauhauCS/Gemma4-12B-QAT-Uncensored-HauhauCS-Balanced](https://huggingface.co/HauhauCS/Gemma4-12B-QAT-Uncensored-HauhauCS-Balanced)** | 作者: HauhauCS | 点赞: 104 | 下载: 46,053
  - **说明**: 社区对 Gemma4 的“无审查”微调与量化，展示了开源社区在模型对齐和个性化上的强大创造力和多样性。

---

### **生态信号**

本周生态信号清晰：
1.  **MoE 与量化深度融合**：以 **GLM-5.2** 和 **Qwen3.5/3.6** 为代表的 MoE 架构已成为主流。社区的核心工作集中在将其量化为 **GGUF** 或 **NVFP4** 格式，以实现本地化、高效率的部署。unsolth 和 Nvidia 等专业化团队成为这一趋势的关键推动者。
2.  **开源生态的“分层”竞争**：技术生态已形成明显的分层：顶级基础模型（如 DeepSeek-V4、GLM-5.2）由头部机构发布，而中坚力量（Ornith、HauhauCS系列）则基于这些基础模型进行微调、对齐（“uncensored”或“agentic”），形成丰富的下游生态。
3.  **从“大而全”到“小而专”**：一方面，千亿级参数模型（Ornith-397B）仍在探索上限；另一方面，专注于特定领域（如**代码**、**数学推理**）的小模型（VibeThinker-3B、FastContext-4B）同样获得了极高的关注，证明模型专业化和场景化是未来重要的增长点。

---

### **值得探索**

1.  **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)**：如果你对计算机视觉的前沿感兴趣，这个模型是绝佳的入手点。它展示了如何用一个小型化模型（3B）实现复杂视觉定位任务，打破了“大模型才能做高级视觉”的传统观念。
2.  **[microsfot/FastContext-1.0-4B-SFT](https://huggingface.co/microsoft/FastContext-1.0-4B-SFT)**：该模型是探索AI **Agent** 基础能力的理想选择。作为微软出品的小型Agent模型，它更易于研究和部署，能帮助你快速上手构建基于智能体的应用，不必受限于海量计算资源。
3.  **[deepreinforce-ai/Ornith-1.0-397B](https://huggingface.co/deepreinforce-ai/Ornith-1.0-397B)**：如果你有足够的计算资源，这个模型值得深入研究。作为目前开源的、基于 MoE 的顶尖大模型之一，它是测试和理解当前MoE架构能力上限的绝佳样本，可以看作下一代模型能力的前瞻。

---
*本日报由 [agents-radar](https://github.com/leevaluder-maker/agents-radar) 自动生成。*