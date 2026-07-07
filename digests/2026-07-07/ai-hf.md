# Hugging Face 热门模型日报 2026-07-07

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-07-07 02:08 UTC

---

好的，作为AI模型生态分析师，以下是为您生成的《Hugging Face 热门模型日报》（2026-07-07）。

---

### Hugging Face 热门模型日报 | 2026-07-07

#### 1. 今日速览

本周 Hugging Face 社区热度由 **Qwen 3.6 系列** 的衍生模型和社区微调版本主导，特别是 **GGUF** 量化版模型下载量惊人，反映了终端部署的巨大需求。**NVIDIA** 和 **Mistral AI** 等头部厂商持续发力，分别推出了针对特定任务优化的模型。此外，**Agent** 和 **Coding** 领域的模型（如 DeepSeek-V4-Pro、gemma-4 微调版）关注度持续走高。值得注意的是，**“自训练”** 和 **“风格迁移”**（如 Claude “Mythos” 风格）的社区微调模型异常活跃，成为一股新兴力量。

#### 2. 热门模型

##### 🧠 语言模型（LLM、对话模型、指令微调）

- **zai-org/GLM-5.2**
  - 作者: zai-org | 点赞: 3,532 | 下载: 231,218
  - 以MoE架构著称的GLM系列最新版本，凭借优异的对话性能获得社区极高关注。

- **deepseek-ai/DeepSeek-V4-Pro-DSpark**
  - 作者: deepseek-ai | 点赞: 409 | 下载: 14,276
  - DeepSeek V4系列的专业加速版，专为推理和代码任务优化，代表了顶级开源模型的最新方向。

- **nvidia/Nemotron-Labs-TwoTower-30B-A3B-Base-BF16**
  - 作者: nvidia | 点赞: 126 | 下载: 10,766
  - NVIDIA推出的30B参数层级MoE模型，采用双塔结构，专为高效推理和实验室场景设计。

##### 🎨 多模态与生成（图像、视频、音频、文本到X）

- **HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive**
  - 作者: HauhauCS | 点赞: 2,529 | 下载: 2,910,241
  - **现象级模型**。基于Qwen3.6的无审查GGUF版本，以极高的下载量和点赞数证明了社区对“无限制”多模态模型的需求。

- **nvidia/LocateAnything-3B**
  - 作者: nvidia | 点赞: 2,635 | 下载: 1,340,559
  - NVIDIA推出的视觉定位模型，能够在图像中进行高精度通用目标检测，点出和下载双高。

- **krea/Krea-2-Turbo**
  - 作者: krea | 点赞: 529 | 下载: 109,470
  - Krea系列的最新Turbo版本，专注于快速、高质量的文本到图像生成，是基于Stable Diffusion生态的增强版。

##### 🔧 专用模型（代码、数学、医疗、嵌入）

- **baidu/Unlimited-OCR**
  - 作者: baidu | 点赞: 1,795 | 下载: 1,070,230
  - 百度发布的通用OCR模型，号称可在任何场景下进行文本识别，下载量巨大，证明其实用价值高。

- **google/tabfm-1.0.0-pytorch**
  - 作者: google | 点赞: 257 | 下载: 7,036
  - Google发布的表格数据基础模型，支持零样本表格分类与回归，有望简化大量结构化数据分析任务。

- **nationaldesignstudio/rampart**
  - 作者: nationaldesignstudio | 点赞: 136 | 下载: 3,821
  - 一个专为PII（个人身份信息）脱敏设计的Token分类模型，关注点精准，适合数据处理流程。

##### 📦 微调与量化（社区微调、GGUF、AWQ）

- **empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF**
  - 作者: empero-ai | 点赞: 1,642 | 下载: 1,617,508
  - **本周最亮眼的微调模型**。将 “Claude-Mythos” 这一特定风格/数据微调进 Qwen3.5，并打包成GGUF，大量下载表明社区对“风格化”模型需求旺盛。

- **yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF**
  - 作者: yuxinlu1 | 点赞: 2,623 | 下载: 664,319
  - 基于Google Gemma-4的编码专家模型，社区微调后性能优异，GGUF版本下载量极高，是代码工作者和本地部署者的最爱。

- **unsloth/Qwen3.6-27B-MTP-GGUF**
  - 作者: unsloth | 点赞: 974 | 下载: 2,818,499
  - 本周下载量冠军。由著名量化库Unsloth推出的Qwen3.6 MoE模型GGUF版，证明了专业量化工具对模型普及的极大推动。

#### 3. 生态信号

- **Qwen 家族统治力惊人**：无论是 Qwen3.5 还是最新的 Qwen3.6，其衍生模型占据了榜单的半壁江山，几乎成为了社区二次开发的“母板”。开源模型的话语权正从西方逐渐转移到以阿里（Qwen）为代表的亚洲团队。
- **开源权重成为主流，闭源模型被“蒸馏”**：本周榜单未见任何新的闭源API模型，相反，社区正大量通过微调（Fine-tune）和风格模仿（如Mythos系列），将闭源模型（如Claude）的“精髓”注入开源权重。
- **量化是模型落地的唯一桥梁**：**GGUF** 格式的模型下载量遥遥领先，**Unsloth**等专业量化工具成为生态核心。社区越来越倾向于下载可直接运行的“即插即用”版本，而非原始权重。

#### 4. 值得探索

- **empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF**：如果你好奇社区是如何逆向工程并模仿顶级闭源模型风格的，这个模型是绝佳案例。其在9B参数上实现的风格迁移能力值得所有模型开发者研究。
- **nvidia/LocateAnything-3B**：对于计算机视觉和机器人领域的从业者，这是一个开箱即用的强大工具。3B的小体量实现通用目标定位，结合其极高的人气，代表了视觉模型从“理解”到“定位”的趋势。
- **google/tabfm-1.0.0-pytorch**：在LLM热潮之外，这是一个被低估的“潜力股”。谷歌出手的表格基础模型，可能将深度学习的应用场景大规模拓展到金融、工业、医疗等结构化数据领域，值得所有数据科学家关注。

---
*本日报由 [agents-radar](https://github.com/leevaluder-maker/agents-radar) 自动生成。*