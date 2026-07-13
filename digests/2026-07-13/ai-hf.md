# Hugging Face 热门模型日报 2026-07-13

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-07-13 01:52 UTC

---

好的，这是为您生成的《Hugging Face 热门模型日报》。

---

### 📰 Hugging Face 热门模型日报 | 2026-07-13

#### **今日速览**

本周 Hugging Face 生态呈现三大热点：首先，**以 Qwen 3.6 和 DeepSeek V4 为代表的国产模型家族势头强劲**，大量社区微调版本和量化版本涌入榜单，形成了庞大的衍生生态。其次，**MoE（混合专家）架构成为主流**，多款高人气模型（如 GLM-5.2、Qwen3.6-35B-A3B）均采用此架构，以更小的激活参数实现强大性能。最后，**多模态与专业化模型百花齐放**，从百度的 OCR 到 NVIDIA 的定位模型，再到专门的语音识别与视频生成模型，应用场景正快速细分。

#### **热门模型分类速览**

##### 🧠 语言模型（LLM、对话模型、指令微调）

- **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** | 作者: zai-org | 👍 3,857 | ⬇️ 441,413
  - **一句话**：采用了 MoE-DSA 架构的旗舰级对话模型，周增赞近4000，是本周社区关注的绝对焦点。
- **[tencent/Hy3](https://huggingface.co/tencent/Hy3)** | 作者: tencent | 👍 724 | ⬇️ 8,655
  - **一句话**：腾讯发布的 Hy3 文本生成模型，作为大型企业的重量级发布，具备较强的潜力。
- **[meituan-longcat/LongCat-2.0](https://huggingface.co/meituan-longcat/LongCat-2.0)** | 作者: meituan-longcat | 👍 182 | ⬇️ 1,767
  - **一句话**：美团发布的长上下文对话模型，反映了业界对超长文本处理能力的需求日益增长。
- **[SupraLabs/Supra-Router-51M](https://huggingface.co/SupraLabs/Supra-Router-51M)** | 作者: SupraLabs | 👍 107 | ⬇️ 1,434
  - **一句话**：参数仅为 51M 的模型路由器，为大规模模型混合使用提供了轻量级调度方案。

##### 🎨 多模态与生成（图像、视频、音频、文本到X）

- **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** | 作者: nvidia | 👍 2,717 | ⬇️ 1,501,653
  - **一句话**：NVIDIA 推出的通用物体定位模型，凭借超强的零样本定位能力获得社区热捧。
- **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)** | 作者: baidu | 👍 1,943 | ⬇️ 1,430,656
  - **一句话**：百度发布的无需预设字符集的 OCR 模型，可识别任意文字，实用性极强。
- **[OpenMOSS-Team/MOSS-Transcribe-Diarize](https://huggingface.co/OpenMOSS-Team/MOSS-Transcribe-Diarize)** | 作者: OpenMOSS-Team | 👍 130 | ⬇️ 14,491
  - **一句话**：集语音转文字与说话人分离于一体的模型，是会议记录等场景的利器。
- **[CohereLabs/cohere-transcribe-arabic-07-2026](https://huggingface.co/CohereLabs/cohere-transcribe-arabic-07-2026)** | 作者: CohereLabs | 👍 95 | ⬇️ 9,860
  - **一句话**：Cohere 发布的高精度阿拉伯语语音识别模型，填补了小语种市场的空白。
- **[Alissonerdx/LTX-Best-Face-ID](https://huggingface.co/Alissonerdx/LTX-Best-Face-ID)** | 作者: Alissonerdx | 👍 111 | ⬇️ 0
  - **一句话**：基于 LTX-Video 的身份保持 LoRA，可生成特定人物的视频，是视频生成领域的流行微调方向。
- **[nineninesix/gepard-1.0](https://huggingface.co/nineninesix/gepard-1.0)** | 作者: nineninesix | 👍 85 | ⬇️ 2,263
  - **一句话**：文本到语音（TTS）模型，为文本生成声音，开辟了多模态交互新路径。

##### 🔧 专用模型（代码、数学、医疗、嵌入、表格）

- **[google/tabfm-1.0.0-pytorch](https://huggingface.co/google/tabfm-1.0.0-pytorch)** | 作者: google | 👍 357 | ⬇️ 20,973
  - **一句话**：Google 的开源表格基础模型，支持零样本表格分类与回归，对结构化数据领域影响深远。
- **[InternScience/Agents-A1](https://huggingface.co/InternScience/Agents-A1)** | 作者: InternScience | 👍 510 | ⬇️ 29,038
  - **一句话**：基于 Qwen3.5 MoE 架构的 Agent 专用模型，旨在提升AI自主完成任务的能力。

##### 📦 微调与量化（社区微调、GGUF、AWQ）

- **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** | 作者: HauhauCS | 👍 2,676 | ⬇️ 2,596,384
  - **一句话**：基于 Qwen3.6 的未审查 MoE 模型，因激进的交互风格和高下载量，体现了社区对特定风格模型的需求。
- **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)** | 作者: empero-ai | 👍 2,047 | ⬇️ 1,967,677
  - **一句话**：将 Claude 风格的推理能力蒸馏到 Qwen 3.5 基座的 GGUF 量化版，是社区微调与量化结合的典范。
- **[yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF)** | 作者: yuxinlu1 | 👍 1,159 | ⬇️ 445,368
  - **一句话**：针对代码和 Agent 任务优化的 Gemma-4 量化版，证明了 Gemini 开源模型在特定领域的微调价值。
- **[unsloth/Qwen3.6-27B-MTP-GGUF](https://huggingface.co/unsloth/Qwen3.6-27B-MTP-GGUF)** | 作者: unsloth | 👍 1,058 | ⬇️ 2,905,019
  - **一句话**：Unsloth 团队版的 Qwen3.6 量化模型，下载量高达290万，显示了社区对高效推理版本的巨大需求。
- **[deepreinforce-ai/Ornith-1.0-35B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF)** | 作者: deepreinforce-ai | 👍 855 | ⬇️ 1,347,036
  - **一句话**：一款 35B 参数的 MIT 协议开源模型，其 GGUF 版本下载量极高，体现了开放协议和量化版的双重吸引力。
- **[froggeric/Qwen-Fixed-Chat-Templates](https://huggingface.co/froggeric/Qwen-Fixed-Chat-Templates)** | 作者: froggeric | 👍 865 | ⬇️ 0
  - **一句话**：专门修复 Qwen 模型对话模板的工具型模型，虽然无下载量，但高点赞说明其解决了社区的普遍痛点。

#### **生态信号**

1.  **模型家族效应凸显**：**Qwen 3.6** 和 **Gemma 4** 形成了强大的社区衍生生态。围绕它们出现了数十个微调、量化、聊天模板修复版本，头部基础模型正成为生态底座。
2.  **MoE 架构已成主流**：从 GLM-5.2、Qwen3.6-35B-A3B 到 NVIDIA 的 Nemotron 系列，MoE 架构在本期榜单中占据绝对C位，“以小博大”是当前大模型竞赛的核心策略。
3.  **量化与微调活动空前活跃**：GGUF 量化模型占据了下载量榜单的半壁江山。社区不再满足于使用原始权重，而是通过 GGUF 实现本地化部署，并通过 LoRA 或全量微调进行“风格化”（如 Uncensored、Claude 风格），模型消费与再创作的门槛显著降低。Unsloth 等工具的出现极大加速了这一过程。

#### **值得探索**

1.  **🥇 [zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)**：本周点赞数最高的模型，其 MoE-DSA 架构在性能和效率上的表现值得深入研究，可能是下一代国产模型的重要参考。
2.  **🥈 [google/tabfm-1.0.0-pytorch](https://huggingface.co/google/tabfm-1.0.0-pytorch)**：Google 的表格基础模型是业界重磅，它有望改变机器学习中结构化数据的处理方式，对于数据科学家和 Kaggle 玩家来说价值巨大。
3.  **🥉 [HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)**：该模型极高的下载量和独特的“未审查+激进”定位，揭示了社区在安全边界之外对个性化和多元化AI交互方式的强烈渴求。

---
*本日报由 [agents-radar](https://github.com/leevaluder-maker/agents-radar) 自动生成。*