# Hugging Face 热门模型日报 2026-07-14

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-07-14 01:29 UTC

---

好的，作为AI模型生态分析师，以下是根据您提供的2026-07-14数据生成的《Hugging Face 热门模型日报》。

---

### **Hugging Face 热门模型日报 | 2026-07-14**

#### **今日速览**

本周Hugging Face生态呈现三大趋势：**一是Qwen家族持续霸榜**，围绕Qwen3.5/3.6的微调、量化与多模态衍生模型占据半壁江山，显示出强大的社区生命力；**二是MoE（混合专家）架构全面开花**，从腾讯的Hy3到NVIDIA的巨型模型，稀疏激活模型正成为主流；**三是视觉与多模态模型（VLM）成为竞争焦点**，多数热门LLM均配备视觉理解能力。此外，**GGUF量化格式**依旧是个人部署的主流选择，多个模型下载量突破百万级别。

#### **热门模型**

##### 🧠 语言模型（LLM、对话模型、指令微调）

- **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)**
  作者: zai-org | 点赞: 3,900 | 下载: 464,914
  说明：智谱系最新稠密MoE模型，凭借强大的对话能力和高点赞数，成为本周社区关注度最高的模型之一。

- **[tencent/Hy3](https://huggingface.co/tencent/Hy3)**
  作者: tencent | 点赞: 754 | 下载: 9,157
  说明：腾讯出品的Hunyuan系列第三代文本生成模型，是国产大模型在开源社区的又一重要布局。

- **[nvidia/NVIDIA-Nemotron-Labs-3-Puzzle-75B-A9B-NVFP4](https://huggingface.co/nvidia/NVIDIA-Nemotron-Labs-3-Puzzle-75B-A9B-NVFP4)**
  作者: nvidia | 点赞: 114 | 下载: 38,775
  说明：NVIDIA的巨型MoE模型（75B参数量，9B激活），采用NVFP4精度，代表了企业级高算力模型的最新方向。

- **[SupraLabs/Supra-Router-51M](https://huggingface.co/SupraLabs/Supra-Router-51M)**
  作者: SupraLabs | 点赞: 114 | 下载: 1,573
  说明：一个专注于“路由”功能的轻量级模型，可能在模型集成或专家选择场景中扮演新角色。

##### 🎨 多模态与生成（图像、视频、音频、文本到X）

- **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)**
  作者: empero-ai | 点赞: 2,084 | 下载: 1,985,221
  说明：基于Qwen3.5的社区微调模型，结合Claude风格数据实现高下载量，是本周最受欢迎的量化多模态模型。

- **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)**
  作者: baidu | 点赞: 1,963 | 下载: 1,506,937
  说明：百度推出的通用OCR模型，下载量超百万，解决了无限制场景下的文字识别痛点，实用性极强。

- **[OpenMOSS-Team/MOSS-Transcribe-Diarize](https://huggingface.co/OpenMOSS-Team/MOSS-Transcribe-Diarize)**
  作者: OpenMOSS-Team | 点赞: 162 | 下载: 39,509
  说明：MOSS团队的开源语音转文本与说话人分离模型，推动了端到端语音处理的开源进程。

- **[robbyant/lingbot-video-moe-30b-a3b](https://huggingface.co/robbyant/lingbot-video-moe-30b-a3b)**
  作者: robbyant | 点赞: 100 | 下载: 513
  说明：创新的视频理解MoE模型，结合了视觉与稀疏激活架构，是视频AI领域的有趣尝试。

- **[Alissonerdx/LTX-Best-Face-ID](https://huggingface.co/Alissonerdx/LTX-Best-Face-ID)**
  作者: Alissonerdx | 点赞: 124 | 下载: 0
  说明：专门为视频生成任务设计的身份保持LoRA，旨在解决AI视频中角色面部一致性的难题。

##### 🔧 专用模型（代码、数学、医疗、嵌入）

- **[google/tabfm-1.0.0-pytorch](https://huggingface.co/google/tabfm-1.0.0-pytorch)**
  作者: google | 点赞: 362 | 下载: 21,590
  说明：谷歌正式发布的表格数据基础模型，支持零样本分类与回归，标志着AI在结构化数据领域的重大进步。

- **[CohereLabs/cohere-transcribe-arabic-07-2026](https://huggingface.co/CohereLabs/cohere-transcribe-arabic-07-2026)**
  作者: CohereLabs | 点赞: 102 | 下载: 11,647
  说明：Cohere专门针对阿拉伯语的语音识别模型，体现了大厂对低资源语言的策略性投入。

- **[nineninesix/gepard-1.0](https://huggingface.co/nineninesix/gepard-1.0)**
  作者: nineninesix | 点赞: 95 | 下载: 3,940
  说明：文本到语音（TTS）模型，继续丰富音频生成领域的开源生态。

##### 📦 微调与量化（社区微调、GGUF、AWQ）

- **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)**
  作者: HauhauCS | 点赞: 2,710 | 下载: 2,512,124
  说明：社区微调的极端风格化模型，主打“无审查”与“激进”特性，下载量极高，反映了对特定风格模型的强烈需求。

- **[unsloth/Qwen3.6-27B-MTP-GGUF](https://huggingface.co/unsloth/Qwen3.6-27B-MTP-GGUF)**
  作者: unsloth | 点赞: 1,074 | 下载: 2,901,906
  说明：Unsloth团队对Qwen3.6的量化版本，使用了MTP（Multi-Turn Prompting）优化，是个人部署高性能模型的首选。

- **[deepreinforce-ai/Ornith-1.0-35B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF)**
  作者: deepreinforce-ai | 点赞: 868 | 下载: 1,392,300
  说明：一款35B参数模型的GGUF版本，下载量巨大，说明社区对中等规模、高性价比模型的热爱。

- **[yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF)**
  作者: yuxinlu1 | 点赞: 1,178 | 下载: 452,627
  说明：基于Google Gemma-4的Agent微调版本，经过复杂命名修饰，代表了Agent/代码场景模型的社区化潮流。

- **[froggeric/Qwen-Fixed-Chat-Templates](https://huggingface.co/froggeric/Qwen-Fixed-Chat-Templates)**
  作者: froggeric | 点赞: 888 | 下载: 0
  说明：虽然下载量为0，但点赞数极高，这是一个专注于修复Qwen对话模板的项目，解决了开发者普遍遇到的痛点。

---

#### **生态信号**

本周生态的核心信号是 **“模型即服务”的民主化**。**Qwen系列**已从单一模型演变为一个庞大的开源生态，衍生出大量的微调（如Qwythos）和量化（如Unsloth）项目，这标志着开源社区对特定模型的深度依赖正在形成。 **MoE架构**（如GLM-5.2、Nemotron、Hy3）已全面超越稠密模型，成为顶级性能模型的标配。值得注意的是，**企业级模型（Google、NVIDIA、百度、腾讯）与社区微调模型形成了良性互动**：大厂贡献基座，社区则通过GGUF/Uncensored等方式将其大众化。此外，多模态（尤其是图像+文本）不再是附加功能，而是成为几乎所有热门LLM的标配。

---

#### **值得探索**

1.  **[google/tabfm-1.0.0-pytorch](https://huggingface.co/google/tabfm-1.0.0-pytorch)**
    **理由**：表格数据是商业和科学领域最常见的数据形式，TabFM作为此类基础模型的先驱，有望彻底改变“传统机器学习”的工作流，值得所有非NLP/CV方向的从业者深入研究。

2.  **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)**
    **理由**：OCR是一个极其成熟但尚未被单一开源模型完美解决的领域，百度这一模型下载量爆火，证明其通用性和鲁棒性可能达到了新的高度，对文档处理、自动化流程有巨大价值。

3.  **[tencent/Hy3](https://huggingface.co/tencent/Hy3)**
    **理由**：作为腾讯最新一代开源模型的代表，Hy3尚未像GLM或Qwen那样产生海量衍生模型。它可能是下一个社区微调的热点基座模型，值得早期关注和基准测试。

---
*本日报由 [agents-radar](https://github.com/leevaluder-maker/agents-radar) 自动生成。*