# Hugging Face 热门模型日报 2026-07-08

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-07-08 01:48 UTC

---

好的，作为AI模型生态分析师，以下是根据您提供的数据生成的《Hugging Face 热门模型日报》。

---

### **Hugging Face 热门模型日报 | 2026年7月8日**

#### **今日速览**

本周 Hugging Face 热点呈现“三足鼎立”态势：**Qwen 3.5/3.6 家族生态全面爆发**，大量基于其的微调、量化和变体模型霸榜；**Gemma 4 与 GLM-5.2** 作为新兴劲旅，凭借优秀的基座性能和社区创作（如代码、角色扮演）迅速崛起；**多模态与专用模型**百花齐放，从百度的 OCR 到英伟达的视觉定位模型均获得极高关注。量化（GGUF）社区异常活跃，成为推动模型普及的核心力量。

#### **热门模型**

##### 🧠 **语言模型（LLM、对话模型、指令微调）**

- **zai-org/GLM-5.2** | 作者: zai-org | 👍: 3,591 | 📥: 281,584
    - **说明**: 本周绝对的黑马，由 zai-org 推出的 MoE 架构对话模型，以惊人的点赞数登顶，证明了市场对新型高效对话模型的需求。
- **mistralai/Leanstral-1.5-119B-A6B** | 作者: mistralai | 👍: 157 | 📥: 157
    - **说明**: Mistral 最新力作，119B 总参/6B 激活参数的极致 MoE 模型，代表了前沿的稀疏化技术方向。
- **deepseek-ai/DeepSeek-V4-Pro-DSpark** | 作者: deepseek-ai | 👍: 424 | 📥: 15,538
    - **说明**: DeepSeek V4 的专业加速版，专注于推理性能优化，是追求高性价比推理的重要选择。
- **meituan-longcat/LongCat-2.0** | 作者: meituan-longcat | 👍: 139 | 📥: 385
    - **说明**: 美团发布的长上下文对话模型，表明工业界在长文本处理上的持续投入。
- **deepreinforce-ai/Ornith-1.0-35B** | 作者: deepreinforce-ai | 👍: 357 | 📥: 280,236
    - **说明**: 基于 Qwen3.5 MoE 的 35B 模型，兼顾多模态与文本生成，是社区进行多模态推理的热门基座。
- **deepreinforce-ai/Ornith-1.0-9B** | 作者: deepreinforce-ai | 👍: 402 | 📥: 136,037
    - **说明**: Ornith 系列的 9B 版本，更轻量，吸引了对效率有要求的用户群体。

##### 🎨 **多模态与生成（图像、视频、音频、文本到X）**

- **baidu/Unlimited-OCR** | 作者: baidu | 👍: 1,833 | 📥: 1,084,945
    - **说明**: 百度的全能光学字符识别模型，超百万下载量，其强大的实用性和高下载量体现了OCR任务的巨大刚需。
- **nvidia/LocateAnything-3B** | 作者: nvidia | 👍: 2,657 | 📥: 1,424,958
    - **说明**: 英伟达推出的通用视觉定位模型，点赞和下载双高，代表了视觉感知模型向通用化迈进的趋势。
- **krea/Krea-2-Turbo** | 作者: krea | 👍: 540 | 📥: 123,729
    - **说明**: 社区热门的文本到图像生成模型，追求更快的Turbo版本，是AIGC创作领域的重要工具。
- **empero-ai/Qwythos-9B-Claude-Mythos-5-1M** | 作者: empero-ai | 👍: 723 | 📥: 152,516
    - **说明**: 基于Qwen3.5的“神话”主题微调模型，融合多模态能力，代表了社区在角色扮演和创意生成上的探索。
- **Qwen/Qwen-AgentWorld-35B-A3B** | 作者: Qwen | 👍: 560 | 📥: 60,736
    - **说明**: 阿里 Qwen 官方推出的智能体世界模型，面向 Agent 场景，标志着大模型从对话走向自主操作的重要一步。

##### 🔧 **专用模型（代码、数学、医疗、嵌入）**

- **google/tabfm-1.0.0-pytorch** | 作者: google | 👍: 288 | 📥: 9,458
    - **说明**: Google 的表格基础模型，主打零样本分类与回归，是表格数据领域的SOTA基座，价值极高。
- **yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF** | 作者: yuxinlu1 | 👍: 2,638 | 📥: 674,977
    - **说明**: 基于 Gemma 4 的代码专用模型，融合了故事与创作能力，证明了在特定任务上微调的价值。
- **yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF** | 作者: yuxinlu1 | 👍: 1,076 | 📥: 384,383
    - **说明**: 同样基于 Gemma 4 的智能体代码模型，强调终端交互能力，是Agent+代码的典范。

##### 📦 **微调与量化（社区微调、GGUF、AWQ）**

- **empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF** | 作者: empero-ai | 👍: 1,759 | 📥: 1,683,711
    - **说明**: 与前文 Qwythos 对应的 GGUF 量化版，超160万下载，再次印证了量化模型是生态传播的“最后一公里”。
- **HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive** | 作者: HauhauCS | 👍: 2,551 | 📥: 2,823,988
    - **说明**: 最受欢迎的“无审查”社区微调模型之一，基于Qwen3.6 MoE，下载量近300万，反映了用户对“开放”模型的强烈偏好。
- **nvidia/Qwen3.6-27B-NVFP4** | 作者: nvidia | 👍: 315 | 📥: 538,687
    - **说明**: 英伟达推出的 ModelOpt 量化版 Qwen3.6，展示了硬件厂商与模型厂商在推理优化上的深度合作。
- **unsloth/Qwen3.6-27B-MTP-GGUF** | 作者: unsloth | 👍: 991 | 📥: 2,842,118
    - **说明**: Unsloth 出品的 Qwen3.6 MTP 量化版，高达 284 万下载，标准的GGUF格式使其成为本地部署的“标配”。
- **deepreinforce-ai/Ornith-1.0-35B-GGUF** | 作者: deepreinforce-ai | 👍: 780 | 📥: 502,663
    - **说明**: Ornith 35B 的 GGUF 版本，下载量超 50 万，是资源受限场景下运行大型 MoE 模型的首选。
- **InternScience/Agents-A1-Q4_K_M-GGUF** | 作者: InternScience | 👍: 74 | 📥: 11,226
    - **说明**: Agents-A1 模型的量化版，为 Agent 模型的本地化和低成本部署提供了可能。

#### **生态信号**

1.  **Qwen 家族势头最旺**，特别是 Qwen3.5/3.6 系列，几乎成为了社区微调和量化的“标准原料”，无论是官方还是第三方模型都表现抢眼。
2.  **MoE（混合专家）模型成为主流**，从 GLM-5.2 到 Qwen 和 Ornith 系列，MoE 架构因在同等算力下提供更强能力而备受青睐。
3.  **量化（GGUF）生态极度繁荣**，热门模型几乎都有对应的GGUF版本。社区已经形成了“先发模型，后发量化”的固定传播链路，GGUF是连接学术与普通用户的关键桥梁。
4.  **开源权重模型持续压制闭源**，榜单上几乎全部为开源模型，社区通过持续“炼丹”（微调、量化）不断挖掘开源模型的价值，形成强大飞轮。

#### **值得探索**

1.  **nvidia/LocateAnything-3B**: 强烈推荐。它在通用视觉定位任务上表现出色，且仅有 3B 参数，非常适合作为机器人、自动驾驶等领域的视觉基础模型。其“Anything”的特性预示着广阔的应用前景。
2.  **zai-org/GLM-5.2**: 值得深究。作为本周点赞王，其性能表现令人期待。建议尝试其对话能力，评估其在长上下文和复杂指令遵循上的真实水平，这可能会是下一个社区微调的热门基座。
3.  **Qwen/Qwen-AgentWorld-35B-A3B**: 值得关注。这是由顶级团队（Qwen）官方出品的智能体模型。建议在 Agent 框架（如 LangChain, AutoGPT）中替换传统 LLM 进行测试，评估其在规划、工具调用和记忆管理上的原生能力。

---
*本日报由 [agents-radar](https://github.com/leevaluder-maker/agents-radar) 自动生成。*