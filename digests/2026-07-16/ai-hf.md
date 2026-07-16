# Hugging Face 热门模型日报 2026-07-16

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-07-16 01:46 UTC

---

好的，以下是 2026-07-16 的《Hugging Face 热门模型日报》。

---

## Hugging Face 热门模型日报 | 2026-07-16

### 今日速览

今日榜单呈现“寡头效应”，**Qwen 家族及其社区衍生模型**（尤其是量化版）几乎统治了下载量榜单，显示了其作为基座模型的绝对热度。同时，**腾讯 Hunyuan（Hy3）** 和 **GLM-5.2** 两大国产模型势头强劲，分别以原生权重和社区适配版本上榜。值得注意的是，GitHub 级开源模型 **Ornith-1.0-35B** 的 GGUF 版本下载量惊人，反映了社区对高质量、可本地部署模型的强烈需求。此外，**极低比特量化**（如 1-bit、Ternary）和 **MoE 结构** 成为社区量化工作的主要发力点。

### 热门模型

#### 🧠 语言模型（LLM、对话模型、指令微调）

- [**zai-org/GLM-5.2**](https://huggingface.co/zai-org/GLM-5.2) | 作者: zai-org | 点赞: 3,998 | 下载: 489,611
  - **一句话说明**：智谱AI自研的MoE+专家共享架构（DSA）大模型，以近4000点赞位列本周热度榜首，代表了国产高端通用模型的持续进化。
- [**tencent/Hy3**](https://huggingface.co/tencent/Hy3) | 作者: tencent | 点赞: 800 | 下载: 10,406
  - **一句话说明**：腾讯混元系列的第三代模型，作为官方发布的原生权重迅速获得社区关注，是商业公司开源大模型的重要代表。
- [**deepreinforce-ai/Ornith-1.0-35B-GGUF**](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF) | 作者: deepreinforce-ai | 点赞: 894 | 下载: 1,533,354
  - **一句话说明**：一个35B参数的强大开源模型，其GGUF量化版在下载量上遥遥领先，证明了社区对“大参数+高可用性”模型的偏爱。
- [**InternScience/Agents-A1**](https://huggingface.co/InternScience/Agents-A1) | 作者: InternScience | 点赞: 556 | 下载: 30,539
  - **一句话说明**：基于 Qwen3.5 MoE 的 Agent 专用模型，表明“模型即代理”的融合趋势，专门针对工具调用和自主任务进行了优化。
- [**yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF**](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF) | 作者: yuxinlu1 | 点赞: 1,198 | 下载: 468,629
  - **一句话说明**：一个极其复杂的社区命名模型，基于Gemma-4，专注于编码和终端Agent能力，下载量巨大，反映了对“小而强”Agent模型的高需求。
- [**nvidia/Nemotron-Labs-Audex-30B-A3B**](https://huggingface.co/nvidia/Nemotron-Labs-Audex-30B-A3B) | 作者: nvidia | 点赞: 156 | 下载: 1,332
  - **一句话说明**：NVIDIA发布的旗舰级MoE模型，总参数量30B，激活仅3B，是高效推理的典范，代表了顶级硬件厂商对MoE结构的押注。

#### 🎨 多模态与生成（图像、视频、音频、文本到X）

- [**baidu/Unlimited-OCR**](https://huggingface.co/baidu/Unlimited-OCR) | 作者: baidu | 点赞: 2,002 | 下载: 1,715,301
  - **一句话说明**：百度开源的通用OCR模型，下载量超过170万，证明其在文档处理、图像识别等实际应用中的巨大价值。
- [**bottlecapai/ThinkingCap-Qwen3.6-27B**](https://huggingface.co/bottlecapai/ThinkingCap-Qwen3.6-27B) | 作者: bottlecapai | 点赞: 366 | 下载: 6,208
  - **一句话说明**：结合了 Qwen3.6 视觉能力的“思考”模型，能够在复杂的图文任务中展示逐步推理过程。
- [**conradlocke/krea2-identity-edit**](https://huggingface.co/conradlocke/krea2-identity-edit) | 作者: conradlocke | 点赞: 307 | 下载: 0
  - **一句话说明**：基于 Krea-2 基座模型的LoRA插件，专为人像“换脸”或身份编辑设计，是AIGC在创意工具领域的最新应用。
- [**open-gigaai/Giga-World-1**](https://huggingface.co/open-gigaai/Giga-World-1) | 作者: open-gigaai | 点赞: 135 | 下载: 0
  - **一句话说明**：一个高质量的世界模型，可能应用于AI仿真或生成，虽然下载量为0，但点赞数显示了社区对其潜力的认可。
- [**Alissonerdx/LTX-Best-Face-ID**](https://huggingface.co/Alissonerdx/LTX-Best-Face-ID) | 作者: Alissonerdx | 点赞: 154 | 下载: 0
  - **一句话说明**：用于 LTX-Video 模型的LoRA，专注于保留角色身份（脸部特征）的文生视频任务。

#### 🔧 专用模型（代码、数学、医疗、嵌入）

- [**Cactus-Compute/needle**](https://huggingface.co/Cactus-Compute/needle) | 作者: Cactus-Compute | 点赞: 236 | 下载: 571
  - **一句话说明**：一个基于JAX框架、专为函数调用和工具使用而生的JAX模型，瞄准了AI Agent生态中的关键环节。

#### 📦 微调与量化（社区微调、GGUF、AWQ）

- [**empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF**](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF) | 作者: empero-ai | 点赞: 2,216 | 下载: **2,006,265**
  - **一句话说明**：本周下载量之王！基于 Qwen3.5 微调并高度量化的模型，是社区对“榨干”开源模型性能的极致追求。
- [**HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive**](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive) | 作者: HauhauCS | 点赞: 2,760 | 下载: **2,443,871**
  - **一句话说明**：Qwen 系MoE模型（35B总参/3B活跃）的“无审查”GGUF版，下载量巨高，体现了社区对“最大自由度”和“高效本地部署”的双重渴望。
- [**prism-ml/Ternary-Bonsai-27B-gguf**](https://huggingface.co/prism-ml/Ternary-Bonsai-27B-gguf) | 作者: prism-ml | 点赞: 474 | 下载: 23
  - **一句话说明**：开创性的 **三值量化（Ternary）** 大模型，将模型大小压缩到极致（2-bit），代表了模型小型化的最前沿探索。
- [**prism-ml/Bonsai-27B-gguf**](https://huggingface.co/prism-ml/Bonsai-27B-gguf) | 作者: prism-ml | 点赞: 269 | 下载: 513
  - **一句话说明**：接续上一篇，这更是一款激进到 **1-bit** 的 27B 大模型，虽然下载量不大，但其技术方向极具研究价值。
- [**unsloth/Qwen3.6-27B-NVFP4**](https://huggingface.co/unsloth/Qwen3.6-27B-NVFP4) | 作者: unsloth | 点赞: 208 | 下载: 1,599,150
  - **一句话说明**：Unsloth推出的NVidia FP4量化版Qwen3.6，为最新显卡的高效推理提供原生支持，工具与模型互为犄角。
- [**jlnsrk/GLM-5.2-colibri-int4**](https://huggingface.co/jlnsrk/GLM-5.2-colibri-int4) | 作者: jlnsrk | 点赞: 111 | 下载: 2,188
  - **一句话说明**：针对 GLM-5.2 的 CPU 友好型 INT4 量化版，结合“专家流式”技术，让大模型能在更多低算力设备上运行。

### 生态信号

当前 Hugging Face 生态呈现出 **“Qwen/GLM/Hunyuan三分天下，社区二创空前活跃”** 的格局。Qwen 系（特别是3.5/3.6版本）凭借其强大的能力和开放的许可，成为社区微调与量化的绝对主力，衍生了大量专注于“无审查”、“思考”或“特定任务”的变体。腾讯的 Hy3 和智谱的 GLM-5.2 则是国产自研力量的标杆，官方权重发布即引发关注，但社区量化（如 GLM-5.2的colibri-int4）活动仍在追赶 Qwen 的规模。**模型量化是本周最核心的趋势**，方向呈现两极分化：一边是极致压缩的1-bit/Ternary/FP4等高频玩法，旨在挑战边缘设备（如手机）部署；另一边是大量MoE模型（如35B-A3B）的量化释放，旨在让拥有中等消费级显卡的用户流畅运行“大”模型。总体来看，开源权重发布正从“可选”变为“必选”，而社区生态的繁荣程度已成为衡量一个模型成功与否的关键指标。

### 值得探索

1.  **📊 [prism-ml/Ternary-Bonsai-27B-gguf](https://huggingface.co/prism-ml/Ternary-Bonsai-27B-gguf)**：想亲手体验一下模型量化能达到的极限吗？这是一个绝佳的研究对象。它展示了将27B大模型压缩到2-bit后，其推理表现究竟能保留多少，对于低资源设备部署和模型结构研究有重要意义。
2.  **🦾 [Cactus-Compute/needle](https://huggingface.co/Cactus-Compute/needle)**：当前 AI Agent 是绝对热点，而其核心就是优秀的函数调用能力。这个模型专为此而生，且基于JAX框架（业内用于快速研究）。它是研究 Agent 能力基座、而非简单套用通用对话模型的绝佳样本。
3.  **🎬 [Alissonerdx/LTX-Best-Face-ID](https://huggingface.co/Alissonerdx/LTX-Best-Face-ID)**：如果你想探索最新的“身份保留”视频生成技术，这个模型值得入手。它展示了社区如何通过LoRA这类轻量化手段，在文生视频模型中实现“角色一致性”，是AIGC应用的重要方向。

---
*本日报由 [agents-radar](https://github.com/leevaluder-maker/agents-radar) 自动生成。*