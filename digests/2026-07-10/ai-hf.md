# Hugging Face 热门模型日报 2026-07-10

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-07-10 01:59 UTC

---

好的，这是为您生成的《Hugging Face 热门模型日报》。

---

## Hugging Face 热门模型日报 | 2026-07-10

### 📰 今日速览

本周 Hugging Face 生态呈现出三大趋势：**Qwen3.6 系列及其变体继续霸榜**，成为社区微调与量化的首选基座模型；**Krea-2 图像生成系列**异军突起，围绕其衍生的 LoRA、ControlNet 与 Turbo 版本形成完整生态链；**NVIDIA 在多个赛道（量化推理、视觉定位、语言模型）密集发布新作**，显示出其从硬件到模型生态的全方位渗透。此外，**GGUF 量化格式**依旧是社区最活跃的领域，大量高下载量的推理优化模型证明了端侧部署需求的强劲。

---

### 🔥 热门模型

#### 🧠 语言模型（LLM、对话模型、指令微调）

| 模型 | 作者 | 点赞/下载 | 一句话说明 |
| :--- | :--- | :--- | :--- |
| **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** | zai-org | 3,729 / 362,300 | 智谱新一代 MoE 对话模型，凭借 MoE 架构与强大的对话能力成为本周点赞数最高的纯语言模型。 |
| **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)** | empero-ai | 1,931 / 1.87M | 基于 Qwen3.5 的社区微调版，融合了长达 1M 的 Claude 对话数据，量化版下载量极高，社区热度惊人。 |
| **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** | HauhauCS | 2,596 / 2.71M | Qwen3.6 的 35B MoE 去限制版，兼具视觉与文本能力，高下载量反映了社区对“个性定制”模型的旺盛需求。 |
| **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)** | yuxinlu1 | 2,670 / 703K | 基于 Gemma-4 的代码专用量化版，结合了 Fable 与 Composer 技巧，在代码生成与推理任务上表现突出。 |
| **[yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF)** | yuxinlu1 | 1,117 / 418K | 上一模型的 Agentic 变体，针对终端交互与智能体任务进行了强化。 |

#### 🎨 多模态与生成（图像、视频、音频、文本到X）

| 模型 | 作者 | 点赞/下载 | 一句话说明 |
| :--- | :--- | :--- | :--- |
| **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** | nvidia | 2,687 / 1.44M | NVIDIA 推出的通用视觉定位模型，以“指哪打哪”的识别能力成为本周最受关注的多模态模型。 |
| **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)** | baidu | 1,903 / 1.24M | 百度发布的全能 OCR 模型，在复杂场景文字识别上表现优异，下载量说明其任务场景非常广泛。 |
| **[krea/Krea-2-Turbo](https://huggingface.co/krea/Krea-2-Turbo)** | krea | 569 / 157K | Krea-2 的高效 Turbo 版，在保持画质的同时大幅提升了推理速度，是社区图像生成的首选之一。 |
| **[conradlocke/krea2-identity-edit](https://huggingface.co/conradlocke/krea2-identity-edit)** | conradlocke | 133 / 0 | Krea-2 的人物身份保持 LoRA，用于保持角色一致性的图像编辑，标志着 Krea-2 生态的成熟。 |

#### 🔧 专用模型（代码、数学、医疗、嵌入）

| 模型 | 作者 | 点赞/下载 | 一句话说明 |
| :--- | :--- | :--- | :--- |
| **[google/tabfm-1.0.0-pytorch](https://huggingface.co/google/tabfm-1.0.0-pytorch)** | google | 330 / 16K | Google 发布的表格数据基础模型（TabFM），支持零样本分类与回归，为结构化数据领域带来新范式。 |
| **[mistralai/Leanstral-1.5-119B-A6B](https://huggingface.co/mistralai/Leanstral-1.5-119B-A6B)** | mistralai | 179 / 258 | Mistral 继续探索高效 MoE 架构，119B 参数仅激活 6B，是极致效率的代表。 |

#### 📦 微调与量化（社区微调、GGUF、AWQ）

| 模型 | 作者 | 点赞/下载 | 一句话说明 |
| :--- | :--- | :--- | :--- |
| **[unsloth/Qwen3.6-27B-MTP-GGUF](https://huggingface.co/unsloth/Qwen3.6-27B-MTP-GGUF)** | unsloth | 1,025 / 2.89M | unsloth 为 Qwen3.6 打造的官方量化版，采用 MTP 技术，极致优化后下载量接近 300 万，是量化界的“爆款”。 |
| **[deepreinforce-ai/Ornith-1.0-35B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF)** | deepreinforce-ai | 820 / 957K | Ornith 系列的 35B GGUF 版，社区自研微调模型，下载量接近百万，说明社区创新力依然强劲。 |
| **[nvidia/Qwen3.6-27B-NVFP4](https://huggingface.co/nvidia/Qwen3.6-27B-NVFP4)** | nvidia | 332 / 748K | NVIDIA 为 Qwen3.6 提供的 NVFP4 极致量化方案，专为其 GPU 优化，下载量证明了硬件与模型协同的重要性。 |

---

### 📈 生态信号

本周生态最明显的信号是 **“模型即生态”** 的加速形成。Qwen3.6 和 Krea-2 已不仅仅是单个模型，而是围绕其产生了大量的社区微调、量化工具链（GGUF、NVFP4）和下游应用（LoRA、ControlNet）。这表明**开源模型在进入成熟期后，其平台属性会带来指数级的社区贡献**。

在开源 vs 闭源方面，本周前十名中**除 NVIDIA 的 NVFP4 方案外，几乎全部为开源模型**，且以 **Apache-2.0 和社区自制许可证**为主。闭源模型的表现在榜单上已不占优势。

值得注意的量化活动是 **GGUF 和 NVFP4 的“双轨并行”**：社区普遍采用 GGUF 以实现跨平台（CPU/GPU）部署，而 NVIDIA 则通过 NVFP4 等技术定义了其GPU上的最佳实践，试图在推理环节形成“护城河”。

---

### 🔭 值得探索

1.  **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)**：这个模型代表了“多模态感知”的新方向，它不满足于“识别是什么”，而是追求“定位在哪里”。对于机器人、自动驾驶和工业检测等领域，这类模型的实际落地价值极高，值得深入研究其 zero-shot 定位能力。

2.  **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)**：作为本周点赞数最高的模型，GLM-5.2 代表了国产大模型在 MoE 架构上的最新探索。其对话能力与训练细节值得对照其技术报告进行深入分析，以理解其与 Llama/Qwen 系列的异同。

3.  **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)**：这个模型集合了“Gemma-4 基座 + Fable/Composer 微调技巧 + GGUF 量化”这一完整链路。对于希望复现“高质量代码模型”的开发者来说，这是一个绝佳的研究案例，可以学习社区如何高效地打磨一个专用模型。

---
*本日报由 [agents-radar](https://github.com/leevaluder-maker/agents-radar) 自动生成。*