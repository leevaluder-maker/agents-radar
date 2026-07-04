# Hugging Face 热门模型日报 2026-07-04

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-07-04 01:59 UTC

---

好的，这是为您生成的《Hugging Face 热门模型日报》。

---

### 《Hugging Face 热门模型日报》- 2026-07-04

#### 📈 今日速览

本周 Hugging Face 社区呈现两大热点：**多模态能力普及化**与**模型追逐“极致”性能**。首先，以 `Qwen` 和 `Gemma 4` 为基础的大量微调版本涌现，特别是集成视觉能力的 MoE 模型成为主流。其次，社区对 GGUF 量化版本的需求依然旺盛，**用户对在本地部署高性能模型（如 35B 级别）有着强烈意愿**。值得关注的是，NVIDIA 和百度分别推出了面向特定场景的专用模型（如定位、OCR），显示出 **AI 模型正从通用对话向解决具体问题深入**。此外，一个拥有 397B 参数的巨型 MoE 模型 `Ornith-1.0` 也挤入榜单，标志着“更大即更强”的军备竞赛仍在继续。

#### 🏆 热门模型分类

##### 🧠 语言模型（LLM、对话模型、指令微调）

-   **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)**
    -   作者: zai-org | 点赞: 3,344 | 下载: 191,462
    -   一句话说明：智谱 AI 最新的 MoE 对话模型，以较高的社区关注度证明其在中英文场景的强大基线能力。

-   **[deepseek-ai/DeepSeek-V4-Pro-DSpark](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-DSpark)**
    -   作者: deepseek-ai | 点赞: 343 | 下载: 9,388
    -   一句话说明：DeepSeek 发布的 V4 版本 Pro 模型，专注于推理能力，是当前开源模型中的顶尖选手。

-   **[Qwen/Qwen-AgentWorld-35B-A3B](https://huggingface.co/Qwen/Qwen-AgentWorld-35B-A3B)**
    -   作者: Qwen | 点赞: 524 | 下载: 45,455
    -   一句话说明：通义千问团队推出的 Agent 专用模型，采用 35B 总参/3B 激活的 MoE 架构，专为智能体任务优化。

-   **[deepseek-ai/DeepSeek-V4-Flash-DSpark](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-DSpark)**
    -   作者: deepseek-ai | 点赞: 142 | 下载: 32,675
    -   一句话说明：V4 系列的高速版本，在保持性能的同时优化了推理效率，适合对延迟敏感的应用。

-   **[BugTraceAI/BugTraceAI-CORE-Ultra-27B-Q6](https://huggingface.co/BugTraceAI/BugTraceAI-CORE-Ultra-27B-Q6)**
    -   作者: BugTraceAI | 点赞: 125 | 下载: 11,444
    -   一句话说明：专注于网络安全（攻防）的专用模型，展示了 LLM 在垂直安全领域的应用潜力。

##### 🎨 多模态与生成（图像、视频、音频、文本到X）

-   **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)**
    -   作者: baidu | 点赞: 1,692 | 下载: 885,040
    -   一句话说明：百度推出的通用 OCR 模型，下载量极高，表明社区对高效、准确的光学字符识别需求巨大。

-   **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)**
    -   作者: nvidia | 点赞: 2,589 | 下载: 1,108,586
    -   一句话说明：NVIDIA 发布的零样本物体定位模型，结合了图文理解与空间定位能力，成为本周多模态领域的明星。

-   **[krea/Krea-2-Turbo](https://huggingface.co/krea/Krea-2-Turbo)**
    -   作者: krea | 点赞: 481 | 下载: 84,006
    -   一句话说明：Krea 推出的文生图模型 Turbo 版，专注于加速图像生成过程，满足社区对“快”和“好”的平衡需求。

-   **[fal/LTX-2.3-3DREAL-LoRA](https://huggingface.co/fal/LTX-2.3-3DREAL-LoRA)**
    -   作者: fal | 点赞: 150 | 下载: 0
    -   一句话说明：用于图片转视频任务的 LoRA 模型，专注于生成 3D 真实感内容，标志着视频生成正走向更精细化的控制。

##### 🔧 专用模型（代码、数学、医疗、嵌入）

-   **[google/tabfm-1.0.0-pytorch](https://huggingface.co/google/tabfm-1.0.0-pytorch)**
    -   作者: google | 点赞: 151 | 下载: 450
    -   一句话说明：Google 推出的表格数据基础模型，旨在零样本或少量样本下解决表格分类与回归问题，拓展了 LLM 在结构化数据上的应用。

-   **[nationaldesignstudio/rampart](https://huggingface.co/nationaldesignstudio/rampart)**
    -   作者: nationaldesignstudio | 点赞: 115 | 下载: 1,149
    -   一句话说明：基于 BERT 的词分类模型，专门用于 PII（个人身份信息）检测与脱敏，体现了企业对数据合规的迫切需求。

##### 📦 微调与量化（社区微调、GGUF、AWQ）

-   **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)**
    -   作者: empero-ai | 点赞: 1,372 | 下载: 1,366,360
    -   一句话说明：基于 Qwen 3.5 微调并量化为 GGUF 的模型，拥有极高的下载量，反映了社区对“角色扮演/创意写作 + 低门槛部署”模型的追捧。

-   **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)**
    -   作者: yuxinlu1 | 点赞: 2,585 | 下载: 628,225
    -   一句话说明：基于 Gemma 4 微调并量化的代码模型，凭借强大的推理与代码生成能力，成为本周最受欢迎的 GGUF 模型之一。

-   **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)**
    -   作者: HauhauCS | 点赞: 2,433 | 下载: 3,029,679
    -   一句话说明：基于 Qwen 3.6 的“无审查”版本且结合了 MoE 架构，下载量冲顶，表明社区对打破限制、具有高创造性的模型有强烈需求。

-   **[deepreinforce-ai/Ornith-1.0-35B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF)**
    -   作者: deepreinforce-ai | 点赞: 685 | 下载: 322,780
    -   一句话说明：Ornith 系列 35B 模型的量化版，提供多种尺寸选择（9B, 35B, 397B），覆盖了从个人部署到企业级应用的不同需求。

-   **[unsloth/Qwen3.6-27B-MTP-GGUF](https://huggingface.co/unsloth/Qwen3.6-27B-MTP-GGUF)**
    -   作者: unsloth | 点赞: 938 | 下载: 1,774,298
    -   一句话说明：知名量化团队 Unsloth 推出的 Qwen 3.6 量化版，以极高效率和兼容性著称，是本地部署 Qwen 3.6 的首选方案之一。

-   **[nvidia/GLM-5.2-NVFP4](https://huggingface.co/nvidia/GLM-5.2-NVFP4)**
    -   作者: nvidia | 点赞: 214 | 下载: 189,970
    -   一句话说明：NVIDIA 为 GLM-5.2 提供的 NVFP4 量化版本，利用其硬件优势进行优化，推动了高性能 MoE 模型的本地化部署。

#### 🌐 生态信号

1.  **Qwen 与 Gemma 生态正旺**：榜单中近半数模型基于 `Qwen` 系列（特别是 3.5/3.6 版本）或 `Gemma 4` 进行二次开发。这表明这两大系列已成为社区创新的“母体”，其开放的权重、强大的基座能力和完善的工具链吸引了大量微调和量化活动。

2.  **开源与闭源的竞合**：DeepSeek V4 和 GLM-5.2 等顶尖模型的开放权重，持续将开源模型的性能天花板推向新高度。与此同时，NVIDIA 通过推出 `LocateAnything` 和 `Model Optimizer` 量化工具，深度介入开源生态，构建软硬件结合的优势。**开源不再是闭源的平替，而是成为创新的主战场**。

3.  **微调与量化的“极端化”**：社区活动呈现两极分化：一端是追求极致性能的“大模型”微调（如 397B 的 Ornith），另一端是追求极致可用性的“小量化”版本（7B-35B 的 GGUF 模型）。**未来模型的价值不仅在于参数量，更在于其在特定场景（如 Agent、代码、角色扮演）下的微调效果和本地化部署的便利性**。

#### 🔭 值得探索

1.  **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)**：这是将“理解”与“定位”结合的优秀范例。对于从事机器人、自动驾驶或视觉问答的研究者而言，这个模型提供了一个强大的零样本基线，代表了下游视觉理解任务的新范式。

2.  **[google/tabfm-1.0.0-pytorch](https://huggingface.co/google/tabfm-1.0.0-pytorch)**：表格数据是工业界的核心。这个模型证明了 LLM 架构也能在表格任务上表现出强大的零样本能力。对于有数据分析、金融风控等需求的从业者，这是一个非常值得关注的“非传统”基础模型。

3.  **[Qwen/Qwen-AgentWorld-35B-A3B](https://huggingface.co/Qwen/Qwen-AgentWorld-35B-A3B)**：Agent 被认为是 LLM 最重要的应用方向之一。这个专为 Agent 优化的 MoE 模型，在保持高能力的同时，通过稀疏激活降低了推理成本。研究 Agent 框架或需要构建智能助手的研究者，建议重点关注。

---
*本日报由 [agents-radar](https://github.com/leevaluder-maker/agents-radar) 自动生成。*