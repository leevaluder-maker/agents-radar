# Hugging Face 热门模型日报 2026-07-12

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-07-12 01:50 UTC

---

好的，作为AI模型生态分析师，以下是2026年7月12日的Hugging Face热门模型日报。

---

### **Hugging Face 热门模型日报 | 2026年7月12日**

#### **今日速览**

本周 Hugging Face 社区呈现出两大核心趋势：**Qwen 3.5/3.6 模型家族成为绝对主力**，衍生出大量微调、量化及以视觉能力为核心的多模态变体；与此同时，**NVIDIA和Mistral等大厂加大了对“性能-成本平衡”架构（如MoE）的开源投入**，并推出了针对特定任务（如定位、代码）的专用模型。此外，**视频和图像生成模型**开始引入身份保持等高级功能，标志着生成模型正从通用向细粒度应用进化。

#### **热门模型**

##### 🧠 **语言模型（LLM、对话模型、指令微调）**

*   **zai-org/GLM-5.2**
    *   [HF链接](https://huggingface.co/zai-org/GLM-5.2)
    *   作者: zai-org | 点赞: 3,832 | 下载: 421,270
    *   说明: 国产开源模型GLM的最新迭代版本，凭借强大且平衡的对话能力稳居社区热度榜首，是当前最受关注的通用LLM之一。

*   **InternScience/Agents-A1**
    *   [HF链接](https://huggingface.co/InternScience/Agents-A1)
    *   作者: InternScience | 点赞: 495 | 下载: 28,141
    *   说明: 基于Qwen 3.5-MoE架构的Agent专用模型，专为工具调用与复杂任务编排优化，代表了“模型即Agent”的趋势。

*   **meituan-longcat/LongCat-2.0**
    *   [HF链接](https://huggingface.co/meituan-longcat/LongCat-2.0)
    *   作者: meituan-longcat | 点赞: 177 | 下载: 1,572
    *   说明: 美团推出的超长上下文模型，专注于处理长文档和多轮对话任务，是企业级长文本应用的代表。

##### 🎨 **多模态与生成（图像、视频、音频、文本到X）**

*   **nvidia/LocateAnything-3B**
    *   [HF链接](https://huggingface.co/nvidia/LocateAnything-3B)
    *   作者: nvidia | 点赞: 2,707 | 下载: 1,472,194
    *   说明: NVIDIA推出的“万物定位”模型，具备强大的开放词汇目标检测与分割能力，在多模态感知任务上表现惊艳。

*   **baidu/Unlimited-OCR**
    *   [HF链接](https://huggingface.co/baidu/Unlimited-OCR)
    *   作者: baidu | 点赞: 1,929 | 下载: 1,380,690
    *   说明: 百度推出的通用OCR模型，号称能处理任意场景和文本类型的图像识别，展现出强大的产业化落地潜力。

*   **bottlecapai/ThinkingCap-Qwen3.6-27B**
    *   [HF链接](https://huggingface.co/bottlecapai/ThinkingCap-Qwen3.6-27B)
    *   作者: bottlecapai | 点赞: 236 | 下载: 4,128
    *   说明: 基于Qwen 3.6的多模态推理模型，强调在处理图文混合输入时的“思考”过程，性能不俗。

*   **Alissonerdx/LTX-Best-Face-ID**
    *   [HF链接](https://huggingface.co/Alissonerdx/LTX-Best-Face-ID)
    *   作者: Alissonerdx | 点赞: 99 | 下载: 0
    *   说明: 基于LTX视频模型的LoRA，专注于生成视频时保持人物身份（Face ID）的一致性，是社区对可控视频生成需求爆发的缩影。

*   **krea/Krea-2-Turbo**
    *   [HF链接](https://huggingface.co/krea/Krea-2-Turbo)
    *   作者: krea | 点赞: 588 | 下载: 168,154
    *   说明: Krea公司推出的第二代图像生成模型的高效版，在人像、艺术风格创作上表现出色，兼顾速度与质量。

##### 🔧 **专用模型（代码、数学、医疗、嵌入）**

*   **google/tabfm-1.0.0-pytorch**
    *   [HF链接](https://huggingface.co/google/tabfm-1.0.0-pytorch)
    *   作者: google | 点赞: 348 | 下载: 20,110
    *   说明: Google推出的表格数据基础模型，支持零样本分类与回归，代表了LLM从非结构化数据向结构化数据领域的延伸。

*   **CohereLabs/cohere-transcribe-arabic-07-2026**
    *   [HF链接](https://huggingface.co/CohereLabs/cohere-transcribe-arabic-07-2026)
    *   作者: CohereLabs | 点赞: 90 | 下载: 7,687
    *   说明: Cohere专为阿拉伯语优化的语音识别模型，体现了大厂对非英语语言多模态能力的战略布局。

##### 📦 **微调与量化（社区微调、GGUF）**

*   **empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF**
    *   [HF链接](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)
    *   作者: empero-ai | 点赞: 2,015 | 下载: 1,944,961
    *   说明: 基于Qwen 3.5的多模态推理模型，被社区量化并蒸馏了“Mythos”的长思考数据，是当前最受欢迎的GGUF模型之一。

*   **HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive**
    *   [HF链接](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)
    *   作者: HauhauCS | 点赞: 2,651 | 下载: 2,641,936
    *   说明: 社区基于Qwen 3.6 MoE大模型进行的“荤话”微调版，去除了安全限制并优化了模型激进风格，下载量极高，反映了社区对“无审查”模型的持续热情。

*   **deepreinforce-ai/Ornith-1.0-35B-GGUF**
    *   [HF链接](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF)
    *   作者: deepreinforce-ai | 点赞: 850 | 下载: 1,216,495
    *   说明: 一个35B级别的社区强基模型，经过量化后下载量巨大，证明中等规模且经过微调的强模型在本地部署市场拥有庞大需求。

*   **yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF**
    *   [HF链接](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF)
    *   作者: yuxinlu1 | 点赞: 1,150 | 下载: 436,530
    *   说明: Google Gemma 4的社区微调量化版，融合了“Agentic”和“Fable”等长思维链数据，专为编程与终端控制设计。

#### **生态信号**

*   **模型家族势头**：**Qwen 3.x系列（特别是3.5和3.6）** 已成为社区生态的标杆，其MoE变体和多模态能力衍生出最多的微调、量化项目。**NVIDIA的Nemotron-Labs和LocateAnything**，以及 **Google的Gemma 4** 家族也在快速崛起。
*   **开源权重 vs 闭源**：**开源权重模型持续主导社区讨论**。NVIDIA、Google和Mistral等公司不仅发布基础权重，还提供专用功能和更友好的许可证（如Apache-2.0），极大地推动了社区应用创新。
*   **量化与微调生态**：**GGUF格式的量化模型** 是社区流动性的核心，排行榜前五名中多个为此类模型，表明本地、高效部署是用户的核心诉求。社区微调（如从Claude蒸馏的“Mythos”数据）正在催生一批性能远超官方的“民间高手”变体。

#### **值得探索**

1.  **nvidia/LocateAnything-3B**：这是一个极具启发性的模型。它将LLM强大的语义理解能力与视觉定位任务结合，可以成为构建智能机器人、增强现实等应用的基石，值得深入阅读其论文和实验Demo。
2.  **zai-org/GLM-5.2**：如果你的项目需要强大的中文对话基础模型，GLM-5.2是目前社区验证过的最优选择之一。其极高的点赞和下载量证明了其稳定性和可靠性。
3.  **migtissera/Tess-4-27B**：这是一个社区基于Qwen 3.5从头微调的高质量多模态模型。相比于其他“套壳”模型，Tess系列在社区中享有盛誉，常被用作衡量多模态指令跟随水平的基线，值得关注其独特的训练策略。

---
*本日报由 [agents-radar](https://github.com/leevaluder-maker/agents-radar) 自动生成。*