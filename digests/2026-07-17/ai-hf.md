# Hugging Face 热门模型日报 2026-07-17

> 数据来源: [Hugging Face Hub](https://huggingface.co/) | 共 30 个模型 | 生成时间: 2026-07-17 01:50 UTC

---

好的，作为AI模型生态分析师，这是为您生成的《Hugging Face 热门模型日报》。

---

## Hugging Face 热门模型日报 | 2026-07-17

### 今日速览

本周 Hugging Face 生态呈现两大主线：一是以 **Qwen3.5/3.6** 系列为核心的多模态与量化模型生态持续繁荣，涌现出大量社区微调版本和GGUF量化版；二是**极致量化技术**成为焦点，`prism-ml`团队推出的1-bit和2-bit （Ternary）模型以极低的内存占用获得了大量关注。此外，腾讯的 `Hy3` 和智谱的 `GLM-5.2` 作为国内大厂的代表作，下载量与点赞数均名列前茅，显示了开源社区对高性能国产模型的强劲需求。特别值得注意的是，`empero-ai` 发布的 `Qwythos-9B` 系列模型下载量惊人，印证了社区对“小模型、高性能”的偏好。

### 热门模型

#### 🧠 语言模型（LLM、对话模型、指令微调）

- **[zai-org/GLM-5.2](https://huggingface.co/zai-org/GLM-5.2)** (作者: zai-org | 点赞: 4,029 | 下载: 513,061)  
  智谱AI的第五代GLM模型，采用了MoE-DSA架构，在对话生成任务上表现突出，是本周点赞数最高的纯文本模型。

- **[tencent/Hy3](https://huggingface.co/tencent/Hy3)** (作者: tencent | 点赞: 813 | 下载: 11,849)  
  腾讯混元大模型系列的最新版本Hy3，是国产大模型阵营的核心成员，在文本生成任务上具备强大竞争力。

- **[deepreinforce-ai/Ornith-1.0-35B-GGUF](https://huggingface.co/deepreinforce-ai/Ornith-1.0-35B-GGUF)** (作者: deepreinforce-ai | 点赞: 902 | 下载: 1,785,575)  
  一个35B参数的GGUF量化模型，下载量极高，表明社区对中等规模、可在本地部署的高性能模型需求旺盛。

- **[InternScience/Agents-A1](https://huggingface.co/InternScience/Agents-A1)** (作者: InternScience | 点赞: 568 | 下载: 33,400)  
  基于Qwen3.5-MoE的智能体专用模型，标志着社区正从单纯对话模型向更复杂的Agent应用演进。

- **[yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF](https://huggingface.co/yuxinlu1/gemma-4-12B-agentic-fable5-composer2.5-v2-3.5x-tau2-GGUF)** (作者: yuxinlu1 | 点赞: 1,208 | 下载: 506,068)  
  基于Gemma 4的精细调优模型，侧重编程与Agent能力， 展示了Google开源模型在社区中的活跃度。

#### 🎨 多模态与生成（图像、视频、音频、文本到X）

- **[HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive](https://huggingface.co/HauhauCS/Qwen3.6-35B-A3B-Uncensored-HauhauCS-Aggressive)** (作者: HauhauCS | 点赞: 2,787 | 下载: 2,328,315)  
  基于Qwen3.6的视觉MoE模型，主打“无审查”和高下载量，反映了社区对特定风格和自由度的追求。

- **[empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF](https://huggingface.co/empero-ai/Qwythos-9B-Claude-Mythos-5-1M-GGUF)** (作者: empero-ai | 点赞: 2,237 | 下载: 2,042,670)  
  一个结合了推理能力的9B多模态模型GGUF版，下载量超过200万，是本周最热门的多模态模型之一。

- **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)** (作者: baidu | 点赞: 2,010 | 下载: 1,852,722)  
  百度发布的通用OCR模型，在图像转文本任务上表现优异，是垂类AI应用的代表作。

- **[unsloth/Qwen3.6-27B-NVFP4](https://huggingface.co/unsloth/Qwen3.6-27B-NVFP4)** (作者: unsloth | 点赞: 216 | 下载: 1,712,974)  
  Unsloth团队采用NVFP4技术对Qwen3.6-27B进行量化，在保证精度的同时大幅提升了推理效率。

- **[Wan-AI/Wan-Dancer-14B](https://huggingface.co/Wan-AI/Wan-Dancer-14B)** (作者: Wan-AI | 点赞: 92 | 下载: 1,884)  
  一个专注于图像生成视频的模型，针对舞蹈动作生成进行了优化，是AIGC在视频内容创作领域的细分探索。

- **[Alissonerdx/LTX-Best-Face-ID](https://huggingface.co/Alissonerdx/LTX-Best-Face-ID)** (作者: Alissonerdx | 点赞: 167 | 下载: 0)  
  一个用于视频生成的身份保持LoRA，旨在改善视频中人物ID的一致性，是视频生成领域的热门微调方向。

#### 🔧 专用模型（代码、数学、医疗、嵌入）

- **（本周无明显突出的专用模型榜单）**

#### 📦 微调与量化（社区微调、GGUF、AWQ）

- **[prism-ml/Ternary-Bonsai-27B-gguf](https://huggingface.co/prism-ml/Ternary-Bonsai-27B-gguf)** (作者: prism-ml | 点赞: 605 | 下载: 74,007)  
  首创性的“三进制”2-bit量化模型，将27B模型压缩到极限，极大降低了本地部署门槛，是本周的技术亮点。

- **[prism-ml/Bonsai-27B-gguf](https://huggingface.co/prism-ml/Bonsai-27B-gguf)** (作者: prism-ml | 点赞: 341 | 下载: 559,267)  
  同样是prism-ml出品，将模型压缩到1-bit（二进制），下载量远超三元版，说明极致压缩是社区关注的焦点。

- **[jlnsrk/GLM-5.2-colibri-int4](https://huggingface.co/jlnsrk/GLM-5.2-colibri-int4)** (作者: jlnsrk | 点赞: 119 | 下载: 2,621)  
  为GLM-5.2提供的4-bit推理优化方案，旨在提升MoE模型在CPU上的运行效率。

- **[Cactus-Compute/needle](https://huggingface.co/Cactus-Compute/needle)** (作者: Cactus-Compute | 点赞: 248 | 下载: 733)  
  一个使用JAX框架训练的、专注于函数调用和工具使用的模型，代表了未来AI Agent模型的技术路线之一。

### 生态信号

1.  **“三极化”量化趋势明显**：除了传统4-bit量化，本周的`prism-ml`将模型量化推向了**1-bit和2-bit（Ternary）**的极致领域。这表明社区不仅在追求“能用”，更在探索在低端设备（如手机、Edge端）运行大模型的极限。虽然精度可能损失，但其引发的下载热潮证明，**“内存换性能”对大量用户极具吸引力**。

2.  **Qwen 3.5/3.6 生态主导权**：无论是多模态模型(`Qwythos`、`HauhauCS`、`unsloth`)还是Agent模型(`Agents-A1`)，Qwen系列都在其中扮演了“底座”角色。这标志着阿里Qwen系列已成功取代Llama系列，成为**2026年下半年开源社区的“地基”模型**。社区围绕其进行微调、量化和二次开发的生态已非常成熟。

3.  **小参数模型与大下载量**：从`Qwythos-9B`到`Ornith-1.0-35B`，**20B以下参数量的模型获得了最高的下载量**。这表明用户的实际部署偏好并非盲目追求最大参数，而是更青睐在消费级显卡上就能流畅运行、性能又足够强大的模型。

### 值得探索

1.  **研究趋势**: **[prism-ml/Ternary-Bonsai-27B-gguf](https://huggingface.co/prism-ml/Ternary-Bonsai-27B-gguf)**。这是当前量化技术的先锋，值得深入研究“三进制”或“1-bit”量化对模型能力的影响，以及其对边缘计算领域的潜在价值。这种将模型权重精确压缩至1-2比特的技术，可能是未来本地AI部署的关键。

2.  **应用尝试**: **[baidu/Unlimited-OCR](https://huggingface.co/baidu/Unlimited-OCR)**。百度在OCR领域的优势明显，这个模型下载量巨大。对于有文档数字化、截图提取、票据识别等需求的开发者和企业，这是一个开箱即用、性能极高的选择。它展示了垂类大模型在解决具体问题上的巨大能量。

3.  **未来方向**: **[InternScience/Agents-A1](https://huggingface.co/InternScience/Agents-A1)**。该模型旨在提升Agent能力，而不仅仅是聊天。如果你的项目需要构建一个能调用工具、执行多步任务的智能体，这个模型值得尝试。它代表了从“对话模型”向“行动模型”转变的重要趋势。

---
*本日报由 [agents-radar](https://github.com/leevaluder-maker/agents-radar) 自动生成。*