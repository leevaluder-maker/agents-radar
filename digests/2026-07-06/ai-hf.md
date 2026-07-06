# Hugging Face 热门模型日报 2026-07-06

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-07-06 02:12 UTC

---

好的，作为AI模型生态分析师，以下是基于2026年7月6日Hugging Face热门模型数据整理的报告。

---

### **Hugging Face 热门模型日报 (2026-07-06)**

#### **1. 今日速览**

本周Hugging Face生态呈现出高度活跃的“稠密与稀疏混合”及“开源与量化齐飞”的态势。**MoE（混合专家）架构**成为绝对主流，以Qwen 3.5/3.6系列和GLM 5.2为代表，多家机构都在此基础上进行微调与量化。**GGUF量化模型**持续霸榜，下载量惊人，表明社区对本地部署和高效推理的需求旺盛。值得关注的是，**NVIDIA**和**Google**分别推出了前沿的NF4量化模型和通用表格模型，标志着头部企业正将战场从纯大语言模型延伸至特定领域与基础设施优化。此外，**DeepSeek V4**系列的发布也验证了高性能开源模型的持续进化。

#### **2. 热门模型**

##### 🧠 语言模型（LLM、对话模型、指令微调）

- **zai-org/GLM-5.2** ([链接](https://huggingface.co/zai-org/GLM-5.2))
  - 作者: `zai-org` | 点赞: 3,470 | 下载: 220,379
  - 是智谱AI开源的新一代MoE大模型，凭借其强大的对话能力和原生多语言支持，获得了社区极高的关注度，成为本周当之无愧的明星模型。
- **deepseek-ai/DeepSeek-V4-Pro-DSpark** ([链接](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-DSpark))
  - 作者: `deepseek-ai` | 点赞: 390 | 下载: 12,580
  - DeepSeek V4系列的专业版，在推理和代码能力上更进一步，代表了开源模型在高端性能上的持续追赶。
- **deepseek-ai/DeepSeek-V4-Flash-DSpark** ([链接](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-DSpark))
  - 作者: `deepseek-ai` | 点赞: 161 | 下载: 48,696
  - DeepSeek V4的快速蒸馏版本，旨在提供接近Pro版的性能但更快的推理速度，适合对延迟敏感的应用。
- **InternScience/Agents-A1** ([链接](https://huggingface.co/InternScience/Agents-A1))
  - 作者: `InternScience` | 点赞: 290 | 下载: 7,010
  - 基于Qwen 3.5 MoE架构构建的智能体模型，专为任务规划和工具调用优化，体现了大模型向Agent化发展的趋势。
- **nvidia/GLM-5.2-NVFP4** ([链接](https://huggingface.co/nvidia/GLM-5.2-NVFP4))
  - 作者: `nvidia` | 点赞: 240 | 下载: 280,087
  - NVIDIA对GLM-5.2进行NF4精度的极致量化版本，在几乎不损失性能的情况下大幅降低模型体积和推理成本，推动大模型在NVIDIA硬件上的高效部署。
- **mistralai/Leanstral-1.5-119B-A6B** ([链接](https://huggingface.co/mistralai/Leanstral-1.5-119B-A6B))
  - 作者: `mistralai` | 点赞: 117 | 下载: 26
  - Mistral的最新巨大MoE模型，激活参数仅6B但总参数量达119B，是追求极致性能与效率平衡的探索。目前刚发布，下载量不高但潜力巨大。
- **Qwen/Qwen-AgentWorld-35B-A3B** ([链接](https://huggingface.co/Qwen/Qwen-AgentWorld-35B-A3B))
  - 作者: `Qwen` | 点赞: 549 | 下载: 55,113
  - 通义千问官方发布的Agent专用模型，进一步强化了其在多模态和智能体领域的布局，是构建复杂AI工作流的理想基座。

##### 🎨 多模态与生成（图像、视频、音频、文本到X）

- **nvidia/LocateAnything-3B** ([链接](https://huggingface.co/nvidia/LocateAnything-3B))
  - 作者: `nvidia` | 点赞: 2,618 | 下载: 1,247,265
  - NVIDIA推出的高效视觉定位模型，只需自然语言指令即可精准定位图像中的任意目标，在开放世界视觉理解任务上表现惊艳，下载量巨大。
- **baidu/Unlimited-OCR** ([链接](https://huggingface.co/baidu/Unlimited-OCR))
  - 作者: `baidu` | 点赞: 1,750 | 下载: 1,044,217
  - 百度的全能OCR模型，以其强大的多语言、多场景（包括复杂版面）文字识别能力，成为实际应用中的热门选择。

##### 🔧 专用模型（代码、数学、医疗、嵌入）

- **google/tabfm-1.0.0-pytorch** ([链接](https://huggingface.co/google/tabfm-1.0.0-pytorch))
  - 作者: `google` | 点赞: 226 | 下载: 2,670
  - Google推出的零样本表格基础模型，可在未见过的表格数据上直接进行分类和回归，无需微调，为数据分析领域带来了革命性工具。
- **BugTraceAI/BugTraceAI-CORE-Ultra-27B-Q6** ([链接](https://huggingface.co/BugTraceAI/BugTraceAI-CORE-Ultra-27B-Q6))
  - 作者: `BugTraceAI` | 点赞: 135 | 下载: 12,196
  - 专注于网络安全领域的量化模型，用于漏洞分析与自动修复，体现了大模型在特定垂直行业深度应用的潜力。
- **nationaldesignstudio/rampart** ([链接](https://huggingface.co/nationaldesignstudio/rampart))
  - 作者: `nationaldesignstudio` | 点赞: 129 | 下载: 2,783
  - 一个轻量级的BERT模型，专门用于个人身份信息（PII）的识别与脱敏，适合部署在隐私敏感的环境中。

##### 📦 微调与量化（社区微调、GGUF、AWQ）

- **empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF** ([链接](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF))
  - 作者: `empero-ai` | 点赞: 1,557 | 下载: 1,533,844
  - 基于Qwen 3.5，融合了Claude风格回复的微调模型，其GGUF版本下载量超过150万，是社区“风格模仿”和“本地化部署”热潮的缩影。
- **yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF** ([链接](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF))
  - 作者: `yuxinlu1` | 点赞: 2,610 | 下载: 651,758
  - 基于Google Gemma-4的代码专用微调模型，经过混合数据集优化，编码能力出色，其GGUF量化版本是本周开发者的热门下载项目。
- **HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive** ([链接](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive))
  - 作者: `HauhauCS` | 点赞: 2,487 | 下载: 3,018,257
  - 对最新Qwen 3.6 MoE模型进行的“无审查”微调版本，下载量突破300万，反映了社区对模型输出自由度的强烈需求。
- **unsloth/Qwen3.6-27B-MTP-GGUF** ([链接](https://huggingface.co/unsloth/Qwen3.6-27B-MTP-GGUF))
  - 作者: `unsloth` | 点赞: 964 | 下载: 2,776,389
  - 由著名量化社区Unsloth提供的Qwen 3.6高效GGUF版本，结合了MTP（多令牌预测）技术，在高质量量化社区中极受欢迎。

#### **3. 生态信号**

- **MoE的“黄金时代”：** Qwen3.5/3.6和GLM 5.2系列全面采纳MoE架构，不仅追求极致性能，更在“高效稀疏”上内卷。社区在此基础上进行的微调与量化活动异常繁荣，表明MoE已从技术前沿走向普惠应用。
- **开源权重的新标杆：** 本周头部模型几乎全部开源权重。DeepSeek V4和Mistral Leanstral的发布，证明在高端模型上，开源社区已能与闭源模型（如Claude 4/OpenAI GPT-5）展开有力竞争，开源正成为新常态。
- **量化是应用的关键：** GGUF和NVIDIA的NF4格式成为两大核心量化流派。前者以高通用性和社区支持取胜（如Unsloth），后者则基于NVIDIA的硬件生态实现极致优化。社区微调模型的下载量远高于基座模型，说明“即拿即用”的量化模型是生态繁荣的基石。

#### **4. 值得探索**

1.  **nvidia/LocateAnything-3B**：一个非常有趣且实用的多模态模型。它打破了传统目标检测的边界，能够理解复杂场景描述，是当前最“聪明”的视觉定位工具之一，强烈推荐开发者体验。
2.  **google/tabfm-1.0.0-pytorch**：对于数据科学家而言，这是一个潜在的Game Changer。零样本表格处理能力可以省去大量特征工程和模型训练时间，值得深入研究其在业务场景中的应用潜力。
3.  **unsloth/Qwen3.6-27B-MTP-GGUF**：Qwen 3.6是当前最强的开源模型系列之一，而Unsloth的量化版本代表了社区最佳实践。这不仅是“尝鲜”最新模型的首选，也是研究如何高效部署30B级MoE模型的绝佳案例。

---
*本日报由 [agents-radar](https://github.com/leevaluder-maker/agents-radar) 自动生成。*