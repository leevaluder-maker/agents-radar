# Hugging Face 热门模型日报 2026-06-30

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-06-30 02:30 UTC

---

好的，作为AI模型生态分析师，以下是为您准备的《Hugging Face 热门模型日报》。

---

### **Hugging Face 热门模型日报 | 2026年6月30日**

#### **今日速览**

今日榜单揭示了几个显著趋势：**多模态Mixture-of-Experts (MoE) 模型**成为绝对主流，如GLM-5.2和Qwen3.6系列占据了下载和点赞高位。**社区量化微调活动极为活跃**，特别是针对GLM-5.2、Qwen3.5/3.6及Gemma 4等大模型的GGUF版本，展示了开发者对本地化部署和高效推理的强烈需求。此外，**NVIDIA**以其专属优化和ASR模型，**DeepSeek**以V4系列新模型，在专业领域和前沿研究方面持续贡献。最后，**“无审查”**（Uncensored）和**“智能体”**（Agentic）等特定功能取向的模型也获得了社区高度关注。

---

#### **热门模型**

##### 🧠 **语言模型（LLM、对话模型、指令微调）**

- **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** | 作者: zai-org | 👍 2,945 | 📥 133k
  *一句话说明*：新一代GLM MoE大模型，凭借卓越的对话和生成能力，成为本周最受关注的通用模型。

- **[Qwen/Qwen-AgentWorld-35B-A3B](https://huggingface.co/Qwen/Qwen-AgentWorld-35B-A3B)** | 作者: Qwen | 👍 438 | 📥 26k
  *一句话说明*：Qwen团队专为“智能体”场景设计的MoE模型，总参数35B但激活仅3B，兼顾性能与效率。

- **[deepseek-ai/DeepSeek-V4-Pro-DSpark](https://huggingface.co/deepseek-ai/DeepSeek-V4-Pro-DSpark)** | 作者: deepseek-ai | 👍 216 | 📥 5k
  *一句话说明*：DeepSeek V4的Pro版本，集成了“DSpark”动态稀疏激活技术，代表了前沿的大模型架构探索。

- **[deepseek-ai/DeepSeek-V4-Flash-DSpark](https://huggingface.co/deepseek-ai/DeepSeek-V4-Flash-DSpark)** | 作者: deepseek-ai | 👍 95 | 📥 2k
  *一句话说明*：DeepSeek V4的Flash版，同样使用DSpark技术，侧重于推理速度的优化。

- **[LiquidAI/LFM2.5-230M](https://huggingface.co/LiquidAI/LFM2.5-230M)** | 作者: LiquidAI | 👍 152 | 📥 15k
  *一句话说明*：Liquid AI推出的新型“液态基础模型”，以极小参数量展现了不俗的性能，极具研究价值。

- **[WeiboAI/VibeThinker-3B](https://huggingface.co/WeiboAI/VibeThinker-3B)** | 作者: WeiboAI | 👍 749 | 📥 63k
  *一句话说明*：一款专注于数学推理的3B参数模型，在推理能力垂直领域表现出色，获得了社区的高度认可。

- **[Chunjiang-Intelligence/DeepSeek-v4-Fable](https://huggingface.co/Chunjiang-Intelligence/DeepSeek-v4-Fable)** | 作者: Chunjiang-Intelligence | 👍 130 | 📥 1k
  *一句话说明*：基于DeepSeek V4的微调版本，专注于网络安全领域，是专业化应用的一个典范。

##### 🎨 **多模态与生成（图像、视频、音频、文本到X）**

- **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)** | 作者: baidu | 👍 1,374 | 📥 362k
  *一句话说明*：百度开源的高性能OCR模型，几乎无所不识别，以强大的实用性和下载量稳居榜首。

- **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** | 作者: HauhauCS | 👍 2,333 | 📥 3.09M
  *一句话说明*：基于Qwen3.6的“无审查”微调MoE模型，下载量惊人，反映了社区对高自由度多模态模型的强烈需求。

- **[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)** | 作者: nvidia | 👍 2,482 | 📥 728k
  *一句话说明*：NVIDIA推出的通用目标定位模型，能根据文字描述在图像中精准定位任意物体，极具实用性。

- **[krea/Krea-2-Turbo](https://huggingface.co/krea/Krea-2-Turbo)** | 作者: krea | 👍 394 | 📥 38k
  *一句话说明*：文生图模型Krea-2的快速版，在保持画质的同时大幅提升了生成速度。

- **[krea/Krea-2-Raw](https://huggingface.co/krea/Krea-2-Raw)** | 作者: krea | 👍 245 | 📥 27k
  *一句话说明*：Krea-2的基础模型，为Turbo版和社区微调提供了优质的底座。

- **[fal/LTX-2.3-3DREAL-LoRA](https://huggingface.co/fal/LTX-2.3-3DREAL-LoRA)** | 作者: fal | 👍 115 | 📥 0
  *一句话说明*：专为LTX视频模型打造的图像转视频LoRA，专注于生成逼真的3D风格视频。

- **[nvidia/nemotron-3.5-asr-streaming-0.6b](https://huggingface.co/nvidia/nemotron-3.5-asr-streaming-0.6b)** | 作者: nvidia | 👍 743 | 📥 76k
  *一句话说明*：NVIDIA的流式语音识别模型，支持边听边识别，延迟极低，适用于实时对话场景。

- **[HauhauCS/Gemma4-12B-QAT-Uncensored-HauhauCS-Balanced](https://huggingface.co/HauhauCS/Gemma4-12B-QAT-Uncensored-HauhauCS-Balanced)** | 作者: HauhauCS | 👍 107 | 📥 46k
  *一句话说明*：基于Gemma 4的“无审查”多模态模型，采用QAT量化，在性能与功能自由度之间取得了平衡。

##### 🔧 **专用模型（代码、数学、医疗、嵌入）**

- **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M)** | 作者: empero-ai | 👍 561 | 📥 79k
  *一句话说明*：融合了多种神话与角色扮演数据的对话模型，主打独特叙事风格和创意交互体验。

- **[deepreinforce-ai/Ornith-1.0-35B](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B)** | 作者: deepreinforce-ai | 👍 241 | 📥 38k
  *一句话说明*：聚焦于多模态推理（image-text-to-text）的MoE模型，是Ornith系列中性能与规模均衡的选择。

- **[deepreinforce-ai/Ornith-1.0-397B](https://huggingface.co/deepreinforce-ai/Ornith-1.0-397B)** | 作者: deepreinforce-ai | 👍 169 | 📥 1k
  *一句话说明*：Ornith系列的超大杯版本，参数量达到惊人的397B，代表了该系列模型的最高能力上限。

##### 📦 **微调与量化（社区微调、GGUF、AWQ）**

- **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)** | 作者: empero-ai | 👍 953 | 📥 907k
  *一句话说明*：Qwythos对话模型的GGUF量化版，作为热门模型的本地部署版本，下载量极高。

- **[yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-coder-fable5-composer2.5-v1-GGUF)** | 作者: yuxinlu1 | 👍 2,503 | 📥 561k
  *一句话说明*：专为代码和推理优化的Gemma 4模型GGUF版，凭借其出色的代码能力，成为本周最受欢迎的量化模型之一。

- **[yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF)** | 作者: yuxinlu1 | 👍 848 | 📥 241k
  *一句话说明*：同样是Gemma 4的微调版，但侧重于“智能体”和终端操作场景，展示了社区对多功能Agent模型的探索。

- **[unsloth/GLM-5.2-GGUF](https://huggingface.co/unsloth/GLM-5.2-GGUF)** | 作者: unsloth | 👍 465 | 📥 164k
  *一句话说明*：知名量化团队Unsloth出品的GLM-5.2 GGUF版，为这个当红模型提供了高效本地部署的官方优化方案。

- **[nvidia/GLM-5.2-NVFP4](https://huggingface.co/nvidia/GLM-5.2-NVFP4)** | 作者: nvidia | 👍 171 | 📥 81k
  *一句话说明*：NVIDIA使用其专属的NVFP4量化技术优化GLM-5.2，代表了在特定硬件上的极致性能表现。

- **[deepreinforce-ai/Ornith-1.0-35B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF)** | 作者: deepreinforce-ai | 👍 483 | 📥 123k
  *一句话说明*：Ornith-1.0-35B模型的GGUF量化版，让这个大模型更容易在消费级硬件上运行。

- **[deepreinforce-ai/Ornith-1.0-9B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-9B-GGUF)** | 作者: deepreinforce-ai | 👍 308 | 📥 68k
  *一句话说明*：Ornith系列9B版本的GGUF量化版，为资源有限的用户提供了入门级多模态模型选择。

- **[nvidia/Qwen3.6-35B-A3B-NVFP4](https://huggingface.co/nvidia/Qwen3.6-35B-A3B-NVFP4)** | 作者: nvidia | 👍 378 | 📥 5,392k
  *一句话说明*：NVIDIA对Qwen3.6 MoE模型进行NVFP4量化的结果，巨大的下载量表明社区对官方优化版的热烈欢迎。

- **[unsloth/Qwen-AgentWorld-35B-A3B-GGUF](https://huggingface.co/unsloth/Qwen-AgentWorld-35B-A3B-GGUF)** | 作者: unsloth | 👍 114 | 📥 116k
  *一句话说明*：Qwen专业Agent模型的GGUF版，让智能体模型也能便捷地本地运行。

---

#### **生态信号**

本周生态展现出几个清晰信号：**MoE架构全面开花**。从GLM-5.2、Qwen3.6到DeepSeek V4，几乎所有顶级模型家族都采用了或正在转向MoE，证明了其在性能与成本间的出色平衡。在**开源权重**方面，NVIDIA的角色日益重要，不仅是硬件和量化工具提供者，更是LocateAnything和Nemotron等原创模型的开发者。**社区微调活动空前繁荣**，HauhauCS的“Uncensored”系列和yuxinlu1的“Agentic/Coder”系列获得海量下载，说明社区不仅关注基础能力，更追求特定“风格”（如无审查）和“功能”（如智能体、代码）。**GGUF量化已成为生态的刚性需求**，几乎所有热门模型都在第一时间被社区或官方（如Unsloth）量化，以降低本地部署门槛。

---

#### **值得探索**

1.  **探索“无审查”的上限：[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)**
    *理由*：以惊人的下载量位居前列，展示了社区对释放模型潜能的渴望。对于研究模型对齐、安全边界或需要极高内容自由度的开发者而言，这是一个极具研究价值的模型。

2.  **体验前沿的多模态定位：[nvidia/LocateAnything-3B](https://huggingface.co/nvidia/LocateAnything-3B)**
    *理由*：NVIDIA的力作，将“根据文字找物体”这一经典CV任务做到了极高水准。对于想要构建高级图像编辑、智能标注或机器人视觉系统的开发者，这个模型提供了强大的基础能力。

3.  **感受小型模型的革命：[LiquidAI/LFM2.5-230M](https://huggingface.co/LiquidAI/LiquidAI/LFM2.5-230M)**
    *理由*：当大家都在追求大、更大时，LiquidAI用230M参数证明了“小”模型的巨大潜力。这种全新架构（液态网络）可能在边缘计算、隐私保护等场景开辟新路径，值得所有AI从业者关注。

---
*本日报由 [agents-radar](https://github.com/leevaluder-maker/agents-radar) 自动生成。*