# Hugging Face 热门模型日报 2026-07-05

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-07-05 02:07 UTC

---

好的，这是为您生成的《Hugging Face 热门模型日报》。

---

### **Hugging Face 热门模型日报 | 2026年7月5日**

#### **今日速览**

本周 Hugging Face 生态呈现出“三足鼎立”的态势：**GLM**、**DeepSeek-V4** 和 **Qwen3.5/3.6** 三大顶级模型家族齐头并进，均推出了重量级新版本，并迅速获得了社区热捧。**GGUF 量化版本**依然是社区驱动的最强引擎，催生了大量专注于推理效率的衍生模型，如 Ornith 系列表现抢眼。同时，NVIDIA 的 **LocateAnything** 在视觉定位任务上异军突起，成为非语言模型中的黑马。值得注意的是，基于 **Gemma-4** 的 Agentic 和 Coder 模型社区需求旺盛，而 **Krea-2** 等图像生成模型的迭代也预示着创意工具的边界正在拓宽。

#### **热门模型**

##### 🧠 语言模型（LLM、对话模型、指令微调）

- **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)**
  - 作者: zai-org | 点赞: 3,399 | 下载: 208,920
  - 说明: 智谱 AI 推出的最新一代对话模型，采用 MoE 架构，凭借强大的推理和对话能力登顶本周点赞榜。

- **[deepseek-ai/DeepSeek-V4-Pro-DSpark](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-DSpark)**
  - 作者: deepseek-ai | 点赞: 370 | 下载: 10,306
  - 说明: DeepSeek V4 系列的高性能版本，专注于复杂推理与编程任务，代表了国产开源模型的顶尖水平。

- **[deepseek-ai/DeepSeek-V4-Flash-DSpark](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-DSpark)**
  - 作者: deepseek-ai | 点赞: 157 | 下载: 40,271
  - 说明: V4 系列中的轻量快速版，平衡了性能与推理速度，适合在线部署场景。

- **[Qwen/Qwen-AgentWorld-35B-A3B](https://huggingface.co/Qwen/Qwen-AgentWorld-35B-A3B)**
  - 作者: Qwen | 点赞: 534 | 下载: 50,188
  - 说明: 通义千问专为 Agent 场景优化的 MoE 模型，主打低推理成本下的强大工具调用与自主决策能力。

- **[deepreinforce-ai/Ornith-1.0-397B](https://huggingface.co/deepreinforce-ai/Ornith-1.0-397B)**
  - 作者: deepreinforce-ai | 点赞: 209 | 下载: 33,268
  - 说明: 基于 Qwen3.5 MoE 架构的超大规模模型，提供了接近闭源 API 级别的性能，是社区微调中的巨无霸。

- **[nvidia/GLM-5.2-NVFP4](https://huggingface.co/nvidia/GLM-5.2-NVFP4)**
  - 作者: nvidia | 点赞: 228 | 下载: 236,501
  - 说明: NVIDIA 与智谱合作，采用 NVFP4 量化推理优化技术，大幅降低了 GLM-5.2 的部署显存需求。

- **[AliesTaha/fable-traces](https://huggingface.co/AliesTaha/fable-traces)**
  - 作者: AliesTaha | 点赞: 121 | 下载: 0
  - 说明: 一个专注于指令微调的 Qwen3 变体模型，探索在特定叙事或写作场景下的表现。

##### 🎨 多模态与生成（图像、视频、音频、文本到X）

- **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)**
  - 作者: nvidia | 点赞: 2,604 | 下载: 1,194,542
  - 说明: NVIDIA 推出的通用视觉定位模型，能够识别并框出图像中任何物体的位置，社区反响极佳，是本周多模态领域的明星。

- **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)**
  - 作者: baidu | 点赞: 1,714 | 下载: 988,379
  - 说明: 百度开源的全能 OCR 模型，支持复杂场景下的文字识别，下载量巨大，显示了“文字识别”这一经典任务的持续需求。

- **[krea/Krea-2-Turbo](https://huggingface.co/krea/Krea-2-Turbo)**
  - 作者: krea | 点赞: 496 | 下载: 89,384
  - 说明: 文生图工具 Krea 的第二代 Turbo 版本，在图像生成质量和速度上进行了显著提升。

- **[fal/LTX-2.3-3DREAL-LoRA](https://huggingface.co/fal/LTX-2.3-3DREAL-LoRA)**
  - 作者: fal | 点赞: 157 | 下载: 0
  - 说明: 基于 LTX-2.3 的视频生成 LoRA，专门针对 3D 写实风格进行微调，体现文生视频领域的社区创新。

##### 🔧 专用模型（代码、数学、医疗、嵌入）

- **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)**
  - 作者: yuxinlu1 | 点赞: 2,595 | 下载: 641,260
  - 说明: 基于 Gemma-4 并专注于代码生成的模型，在编程与推理任务上表现优异，是本周代码领域的冠军。

- **[yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF)**
  - 作者: yuxinlu1 | 点赞: 1,010 | 下载: 342,752
  - 说明: 同样是 Gemma-4 的变体，专为 Agent 工作流（如终端命令执行）设计，是自动化脚本领域的热门选择。

- **[google/tabfm-1.0.0-pytorch](https://huggingface.co/google/tabfm-1.0.0-pytorch)**
  - 作者: google | 点赞: 197 | 下载: 1,177
  - 说明: Google 发布的基础表格模型，支持零样本的表格分类与回归，为表格数据处理带来了新的范式。

- **[nvidia/Nemotron-Labs-TwoTower-30B-A3B-Base-BF16](https://huggingface.co/nvidia/Nemotron-Labs-TwoTower-30B-A3B-Base-BF16)**
  - 作者: nvidia | 点赞: 121 | 下载: 10,479
  - 说明: NVIDIA 发布的“双塔”架构模型，旨在高效处理文本核心任务，是探索新架构的代表。

##### 📦 微调与量化（社区微调、GGUF、AWQ）

- **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)**
  - 作者: HauhauCS | 点赞: 2,454 | 下载: 2,993,053
  - 说明: 本周下载量最高的模型！基于 Qwen3.6 的 MoE 视觉模型，去除了审查限制（Uncensored）并针对特定风格进行了激进调优，极受欢迎。

- **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)**
  - 作者: empero-ai | 点赞: 1,462 | 下载: 1,464,047
  - 说明: 基于 Qwen3.5 的 GGUF 量化版，融合了 Claude 风格的数据，是追求兼顾创意与可部署性的用户的首选。

- **[deepreinforce-ai/Ornith-1.0-35B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF)**
  - 作者: deepreinforce-ai | 点赞: 712 | 下载: 359,659
  - 说明: Ornith 系列 35B 模型的 GGUF 量化版，使得在消费级硬件上运行大规模模型成为可能。

- **[deepreinforce-ai/Ornith-1.0-9B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-9B-GGUF)**
  - 作者: deepreinforce-ai | 点赞: 424 | 下载: 320,660
  - 说明: 与 35B 版本对应的小型化 GGUF 模型，提供了效率与性能的更优平衡点。

- **[huihui-ai/Huihui-GLM-5.2-abliterated-GGUF](https://huggingface.co/huihui-ai/Huihui-GLM-5.2-abliterated-GGUF)**
  - 作者: huihui-ai | 点赞: 162 | 下载: 4,701
  - 说明: GLM-5.2 的“去审查”（abliterated）GGUF 版本，满足了特定用户群体对模型输出自由的追求。

- **[Jackrong/Qwopus3.6-35B-A3B-Coder-MTP-GGUF](https://huggingface.co/Jackrong/Qwopus3.6-35B-A3B-Coder-MTP-GGUF)**
  - 作者: Jackrong | 点赞: 131 | 下载: 59,971
  - 说明: 一个结合了视觉与编码能力的GGUF模型，体现了多模态模型被量化为特定用途的趋势。

- **[BugTraceAI/BugTraceAI-CORE-Ultra-27B-Q6](https://huggingface.co/BugTraceAI/BugTraceAI-CORE-Ultra-27B-Q6)**
  - 作者: BugTraceAI | 点赞: 132 | 下载: 12,001
  - 说明: 专注于网络安全领域的 Qwen3 量化模型，用于漏洞分析和渗透测试，是垂直领域微调的典型代表。

#### **生态信号**

1.  **三大巨头瓜分话语权**：本周榜单清晰地反映了**GLM、DeepSeek 和 Qwen（/Qwen3.5/3.6）** 三足鼎立的格局。它们不仅是原版模型的热门，更是社区微调（如 Ornith、HauhauCS）和量化（如 GGUF）的核心基座。这三大家族几乎占据了所有高性能、高关注度的模型。

2.  **“开源权重”是发动机，“量化微调”是燃料**：DeepSeek V4 和 GLM-5.2 等模型选择开放全权重，这直接催生了海量的社区创新。用户通过 GGUF 量化（占比极高）和“消融审查”（Abliteration）等微调手段，将基础模型改造为自己的“专属工具”。闭源模型（即使性能更强）在社区动态和热度上已无法与这些开放生态抗衡。

3.  **硬件友好是核心诉求**：从 397B 参数量的 Ornith 到其 GGUF 版本，再到 NVIDIA 的 NVFP4 量化，所有趋势都指向一点：**降低推理门槛**。社区不再仅仅追求模型质量，更关注如何让大模型在个人电脑、游戏显卡上流畅运行。这预示着未来模型竞争将不仅是参数的竞赛，更是部署效率的竞赛。

#### **值得探索**

1.  **[nvidia/GLM-5.2-NVFP4](https://huggingface.co/nvidia/GLM-5.2-NVFP4)**
    - **理由**：GLM-5.2 的性能加上 NVIDIA 的原生 NVFP4 量化优化，使其成为在 NVIDIA GPU 上部署顶级对话模型的最优解之一。如果你有 NVIDIA 硬件，这个模型能让你以极低的资源消耗获得旗舰体验。

2.  **[google/tabfm-1.0.0-pytorch](https://huggingface.co/google/tabfm-1.0.0-pytorch)**
    - **理由**：在 LLM 霸榜的时代，基于表格数据的专用基础模型非常罕见且有价值。Google TabFM 提供了一个“零样本”处理表格任务的极简方案，对于数据科学家和工业界用户来说，这可能是取代传统 GBDT 模型的新尝试。

3.  **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)**
    - **理由**：以 3B 的小尺寸实现了强大的“指哪打哪”视觉定位能力。它不是一个简单的分类或检测模型，而是理解“任何物体”语义的通用模型。对于构建视觉 Agent、自动化流程或理解复杂图像内容，这绝对值得上手一试。

---
*本日报由 [agents-radar](https://github.com/leevaluder-maker/agents-radar) 自动生成。*