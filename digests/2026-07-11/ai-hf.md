# Hugging Face 热门模型日报 2026-07-11

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-07-11 01:47 UTC

---

好的，作为AI模型生态分析师，我将基于您提供的2026年7月11日数据，为您生成一份结构清晰的《Hugging Face 热门模型日报》。

---

### **Hugging Face 热门模型日报 | 2026年7月11日**

#### **今日速览**

本周社区热点集中在大厂与社区的“双核驱动”上：一方面，**腾讯、百度、NVIDIA、DeepSeek** 等巨头发布了重量级基座模型及工具；另一方面，社区围绕 **Qwen3.6** 和 **Gemma 4** 掀起了疯狂的量化和微调热潮，尤其以“无审查”和“GGUF”格式最为显著。值得关注的是，**NVIDIA** 凭借多款视觉与语言模型霸榜，而**百度**的OCR模型下载量惊人，显示出实用型多模态模型的强大需求。

#### **热门模型**

##### 🧠 语言模型（LLM、对话模型、指令微调）

*   **zai-org/GLM-5.2**
    *   作者: zai-org | 点赞: 3,785 | 下载: 392,655
    *   **一句话说明**：智谱开源的最新旗舰对话模型，从点赞数上看，无疑是本周社区最受关注的“当红炸子鸡”，标志着国产大模型在开源社区的又一里程碑。
*   **deepseek-ai/DeepSeek-V4-Pro-DSpark**
    *   作者: deepseek-ai | 点赞: 463 | 下载: 33,088
    *   **一句话说明**：DeepSeek V4的“DSpark”变体，旨在提升推理效率，展现了DeepSeek在性能优化上的持续投入，是研究MoE架构的绝佳样本。
*   **mistralai/Leanstral-1.5-119B-A6B**
    *   作者: mistralai | 点赞: 184 | 下载: 315
    *   **一句话说明**：Mistral AI推出的Leanstral模型更新，119B参数但仅激活6B，是探索高效Transformer架构的旗舰，下载量虽低但战略意义重大。
*   **InternScience/Agents-A1**
    *   作者: InternScience | 点赞: 471 | 下载: 25,772
    *   **一句话说明**：基于Qwen3.5 MoE架构的智能体模型，瞄准了AI Agent应用场景，反映了业内对Agent化模型的探索趋势。
*   **meituan-longcat/LongCat-2.0**
    *   作者: meituan-longcat | 点赞: 170 | 下载: 1,308
    *   **一句话说明**：美团开源的超长上下文模型，旨在解决长文本理解与生成难题，是行业应用导向的代表作。

##### 🎨 多模态与生成（图像、视频、音频、文本到X）

*   **nvidia/LocateAnything-3B**
    *   作者: nvidia | 点赞: 2,701 | 下载: 1,456,269
    *   **一句话说明**：NVIDIA的通用视觉定位模型，因其在“图像-文本-到-文本”任务中的强大潜力而备受推崇，下载量极高，是本周的“明星模型”之一。
*   **baidu/Unlimited-OCR**
    *   作者: baidu | 点赞: 1,921 | 下载: 1,319,683
    *   **一句话说明**：百度开源的“无限”OCR模型，凭借其超高的实用性和通用性，获得了巨大的下载量，证明了传统技术在多模态时代仍有巨大价值。
*   **krea/Krea-2-Turbo**
    *   作者: krea | 点赞: 575 | 下载: 164,525
    *   **一句话说明**：Krea 2的加速版扩散模型，主打快速图像生成，是AI绘画社区的热门工具。
*   **OpenMOSS-Team/MOSS-Transcribe-Diarize**
    *   作者: OpenMOSS-Team | 点赞: 98 | 下载: 5,919
    *   **一句话说明**：一款集成了语音转录和说话人分离的音频处理模型，填补了音频场景下的需求空白，代表了MOSS生态的扩展。
*   **Alissonerdx/LTX-Best-Face-ID**
    *   作者: Alissonerdx | 点赞: 84 | 下载: 0
    *   **一句话说明**：专注于身份保持的视频生成模型，实现可定制化的“参考到视频”生成，虽然下载量为0但创意十足。

##### 🔧 专用模型（代码、数学、医疗、嵌入）

*   **google/tabfm-1.0.0-pytorch**
    *   作者: google | 点赞: 345 | 下载: 18,626
    *   **一句话说明**：Google推出的表格数据基础模型，具备零样本表格分类与回归能力，是基础模型在结构化数据领域的重要探索。
*   **nvidia/NVIDIA-Nemotron-Labs-3-Puzzle-75B-A9B-NVFP4**
    *   作者: nvidia | 点赞: 99 | 下载: 23,404
    *   **一句话说明**：NVIDIA的Puzzle模型，结合了75B参数和创新的NVFP4精度量化，代表了在超大规模模型推理效率上的前沿尝试。
*   **SupraLabs/Supra-Router-51M**
    *   作者: SupraLabs | 点赞: 86 | 下载: 1,160
    *   **一句话说明**：一种超轻量的模型路由器，用于将请求动态路由到最适合的LLM，揭示了模型路由与编排领域的微型化趋势。
*   **meituan-longcat/LongCat-2.0** (已在LLM分类列出，但也可归为专用长上下文模型)

##### 📦 微调与量化（社区微调、GGUF、AWQ）

*   **HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive**
    *   作者: HauhauCS | 点赞: 2,623 | 下载: 2,660,170
    *   **一句话说明**：Qwen3.6的“无审查+激进”魔改版，下载量高达266万，是社区微调狂热、追求个性化和底线的典型代表。
*   **unsloth/Qwen3.6-27B-MTP-GGUF**
    *   作者: unsloth | 点赞: 1,036 | 下载: 2,895,457
    *   **一句话说明**：凭借Unsloth的量化魔力，将最火的Qwen3.6-27B模型高效转化为GGUF格式，下载量全网最高，是开源用户本地部署的首选。
*   **empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF**
    *   作者: empero-ai | 点赞: 1,976 | 下载: 1,909,705
    *   **一句话说明**：融合Claude和Mythos风格的Qwythos模型的GGUF量化版，下载量同样惊人，体现了社区对创意融合模型和高效部署的追捧。
*   **yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF**
    *   作者: yuxinlu1 | 点赞: 1,134 | 下载: 427,668
    *   **一句话说明**：基于Google Gemma 4的Agentic微调版GGUF模型，专注于编码和终端操作，显示了社区对Agent功能的极高兴趣。

#### **生态信号**

1.  **Qwen3.6 + MoE 家族统治力显现**：Qwen3.6系列（及其变体Qwen3.5）不仅自身冲榜，围绕它进行的微调、量化（如Unsloth、HauhauCS）也占据了大量下载量。同时，MoE（混合专家）架构几乎成为标配（如GLM-5.2、DeepSeek V4 Pro、InternScience Agents-A1, Nvidia Nemotron系列）。
2.  **GGUF格式的绝对主导**：Top 10下载量中有5个是GGUF格式模型。这印证了开源社区对本地部署、高效推理的强烈需求。“量化和分享”已成为一种主流的文化活动。
3.  **GPU供给充裕，但模型极度“贪吃”**：NVIDIA不仅在商业上成功，在开源模型生态（视觉、语言、量化格式）中通过基础研究和社区支持获得了极高人气。这背后反映出，生态正围绕如何更高效地利用稀缺的GPU资源进行激烈竞赛。

#### **值得探索**

1.  **Google / tabfm-1.0.0-pytorch**: 对于数据科学家和Kaggle竞赛玩家，这是本周最值得探索的模型。它挑战了深度学习只擅长非结构化数据的固有印象，有望颠覆表格数据分析的范式。
2.  **zai-org / GLM-5.2**: 作为国内最受关注的开源模型之一，GLM-5.2在性能、汉语能力等方面值得与Llama、Qwen进行深入对比，是研究中文大模型前沿进展的绝佳对象。
3.  **unsloth / Qwen3.6-27B-MTP-GGUF**: 如果你是个人开发者或希望在自己的笔记本上体验顶级开源模型的威力，这个模型是本周的不二之选。它完美诠释了社区如何通过技术（量化）与热情（魔改），将旗舰级模型“平民化”。

---
*本日报由 [agents-radar](https://github.com/leevaluder-maker/agents-radar) 自动生成。*