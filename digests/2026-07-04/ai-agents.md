# OpenClaw 生态日报 2026-07-04

> Issues: 314 | PRs: 500 | 覆盖项目: 13 个 | 生成时间: 2026-07-04 01:59 UTC

- [OpenClaw](https://github.com/openclaw/openclaw)
- [NanoBot](https://github.com/HKUDS/nanobot)
- [Hermes Agent](https://github.com/nousresearch/hermes-agent)
- [PicoClaw](https://github.com/sipeed/picoclaw)
- [NanoClaw](https://github.com/qwibitai/nanoclaw)
- [NullClaw](https://github.com/nullclaw/nullclaw)
- [IronClaw](https://github.com/nearai/ironclaw)
- [LobsterAI](https://github.com/netease-youdao/LobsterAI)
- [TinyClaw](https://github.com/TinyAGI/tinyagi)
- [Moltis](https://github.com/moltis-org/moltis)
- [CoPaw](https://github.com/agentscope-ai/CoPaw)
- [ZeptoClaw](https://github.com/qhkm/zeptoclaw)
- [ZeroClaw](https://github.com/zeroclaw-labs/zeroclaw)

---

## OpenClaw 项目深度报告

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，根据您提供的 OpenClaw 项目 GitHub 数据，我为您生成了 2026-07-04 的项目动态日报。

---

## OpenClaw 项目动态日报 | 2026-07-04

### 1. 今日速览

今日 OpenClaw 项目社区活跃度极高，尤其是 **PR 提交与 Code Review** 活动异常频繁。过去24小时内，共有 **500 条 PR 更新**，其中高达 89%（445条）处于待合并状态，显示了核心团队正在集中进行大规模的代码重构和功能整合。Issue 方面，围绕 **安全性** 和 **消息丢失** 的“钻石龙虾”级问题讨论依然激烈，特别是 `doomclaw` 提到的“工具调用间文本泄漏”问题持续发酵。尽管当天没有新版本发布，但项目在基础设施重构、平台兼容性修复和用户体验优化方面取得了显著进展。

### 2. 版本发布

**无**。今日无新版本发布。

### 3. 项目进展

今日项目进展主要体现在 **大规模代码重构** 和 **关键Bug修复** 上。虽然合并的PR数量不多（55条），但这些 PR 的讨论和准备活动非常密集，预示着一次重大的内部一致性提升。

*   **核心基础设施重构**: 核心维护者 `RomneyDa` 提交了多个重构 PR，旨在消除代码库中的重复逻辑，提升可维护性和安全性。
    *   **PR #99757**: [重构TTS配置合并](https://github.com/openclaw/openclaw/pull/99757)，统一语音合成配置路径。
    *   **PR #99746**: [重构安全秘密原语](https://github.com/openclaw/openclaw/pull/99746)，统一密钥显示与比较逻辑。
    *   **PR #99744**: [重构基础HTTP请求读取](https://github.com/openclaw/openclaw/pull/99744)，将边界检查从媒体模块移至基础设施层。

*   **关键Bug修复**:
    *   **PR #99748**: [修复嵌入式Agent在 `replay_invalid` 重试时保留过期思考签名](https://github.com/openclaw/openclaw/pull/99748)的问题，提升了Agent进程重启后的稳定性。
    *   **PR #99756**: [修复文本工具输出被替换为媒体占位符](https://github.com/openclaw/openclaw/pull/99756)的问题，直接回应用户在Issue #96857和 #99241中的反馈。

*   **平台与渠道适配**:
    *   **PR #99745**: [修复Telegram富文本发送和打字指示器超时问题](https://github.com/openclaw/openclaw/pull/99745)，优化了Telegram渠道的通信体验。
    *   **PR #98868**: [刷新iOS on-boarding流程](https://github.com/openclaw/openclaw/pull/98868)，改进新用户的第一印象。

### 4. 社区热点

今日社区讨论的核心围绕着 **AI代理行为的可控性与安全性** 展开。

*   **Issue #25592**: “工具调用间文本泄漏” 问题成为最热议题，获得 **33条评论**。用户 `doomclaw` 报告称，Agent在处理过程中产生的内部文本（如错误处理、确认信息）会意外地被发送到用户通道，造成严重的UX问题。这直接触及了AI Agent行为的边界，用户希望 Agent 能更“清晰”地区分内部思考与外部沟通。
*   **Issue #10659**: “隐藏Secrets”功能请求持续获得高关注（13条评论，4个👍）。用户强烈要求增加一个系统，允许Agent使用API密钥，但禁止Agent看到其原始值，以防止提示注入攻击下的凭证泄露。
*   **Issue #12602**: “Slack Block Kit 支持” 功能请求也保持活跃（13条评论）。用户希望Agent能创建更丰富的交互式消息（如按钮、选择列表），而不仅仅是纯文本，以更好地集成到Slack工作流中。

这些热点表明，社区正从“Agent能做什么”转向“如何安全、可控、优雅地让Agent做事”。

### 5. Bug 与稳定性

今日报告的 Bug 主要集中在消息传递、会话状态和数据一致性方面，部分已有关联的修复 PR。

*   **严重 (P1, Diamond Lobster)**:
    *   **Issue #98416**: `v2026.6.11` 发布版缺少重入保护，导致回复会话初始化冲突。 **严重性: 高**，直接影响用户交互。**已有社区PR讨论，但无直接修复PR。**
    *   **Issue #92043**: 180秒压缩超时是整个管道上的单次墙钟，且无部分进度重用，导致长时间压缩每次都会失败。 **严重性: 高**，影响长对话/大型文档处理。**待维护者决策**。
    *   **Issue #90361**: `memory_search` 工具偶发返回“索引元数据丢失”错误，疑似搜索/重建竞争条件。有用户自提本地修复。**已有本地修复方案**。

*   **中等 (P2)**:
    *   **Issue #73148**: 在未安装 `sharp` 包的环境下，`image` 工具返回模糊的“Failed to optimize image”错误。**影响可用性**，缺少清晰诊断。**状态为陈旧**。
    *   **Issue #92241**: 更新/回滚后，Gateway持有陈旧模块导入路径，导致消息被静默丢弃。 **影响可靠性**。**需要实况复现**。

### 6. 功能请求与路线图信号

今日提交的功能请求显示了用户对 **安全性、权限管理和跨平台体验** 的持续追求。

*   **安全与权限**:
    *   **Issue #15032**: 为子代理（sub-agents）添加按生成（per-spawn）的工具限制，此功能已被多次提及，未来极有可能被纳入路线图。
    *   **Issue #13616**: 请求一个标准的备份/恢复工具，用于配置、定时任务和会话历史。这反映了用户在生产环境中对灾难恢复的需求。

*   **开发者体验**:
    *   **Issue #14785**: 建议减少工具schema的token开销 (~3500 tok/session)。这是一个性能优化请求，直指高额API成本问题，如果实现，将惠及所有用户。

*   **平台兼容性**:
    *   **PR #99751**: 确保 `@openclaw/llama-cpp-provider` 在系统不兼容时不会安装失败。这表明项目正在降低本地AI模型的部署门槛。

### 7. 用户反馈摘要

从Issue评论和描述中，可以提炼出以下真实的用户声音：

*   **痛点：Agent行为不透明**。用户对“工具调用间文本泄漏” (Issue #25592) 和“工具输出降级为图片占位符” (Issue #96857) 感到困扰。他们希望Agent的“大脑”和“嘴巴”之间有清晰的界限。
*   **痛点：配置不够灵活**。用户希望有**针对特定场景的细粒度控制**，例如：
    *   为不同Agent使用不同的插件配置 (Issue #55401)。
    *   为子Agent限制特定工具 (Issue #15032)。
*   **需求：更丰富的渠道交互**。用户不满足于纯文本，他们希望Agent能：
    *   在Slack中发送Block Kit消息 (Issue #12602)。
    *   在WhatsApp中发送和接收贴纸 (Issue #7476)。
    *   在Telegram中发送图文混排消息 (PR #99745)。
*   **满意点：项目维护者对重构和代码质量的投入**。多个来自核心维护者的重构PR（如PR #99753, #99755）表明项目团队在主动优化内部架构，这对于项目的长期健康是积极信号。

### 8. 待处理积压

以下是一些长期未得到响应或进展缓慢的重要Issue，建议维护者关注：

*   **【高优先级】Issue #6615**: [为 `exec-approvals` 添加拒绝名单](https://github.com/openclaw/openclaw/issues/6615) (7个👍)。自2月初提出，已有用户强烈希望实现“除X外允许一切”的策略。当前状态为“等待安全评审”，进展缓慢。
*   **【中等优先级】Issue #73148**: [`image` 工具未安装 `sharp` 时返回模糊错误](https://github.com/openclaw/openclaw/issues/73148)。创建于4月底，已被标记为“陈旧 (stale)”，但该问题会严重影响新用户的使用体验，是一个易用性硬伤。
*   **【中等优先级】Issue #75593**: [子代理列表在生成后为空](https://github.com/openclaw/openclaw/issues/75593)。尽管已被关闭，但用户描述其是Issue #71495的延续，即使是修复后的版本仍有此问题。建议维护者再次审视其修复方案的完整性。

---

## 横向生态对比

好的，作为资深技术分析师，基于您提供的各项目 2026-07-04 动态数据，我为您呈现一份详尽的横向对比分析报告。

---

### 1. 生态全景

当前，AI 智能体/个人 AI 助手开源生态正处于 **“从功能探索向生产就绪”加速迈进** 的关键阶段。社区反馈的焦点已从“Agent 能做什么”转向“如何安全、稳定、可控地让 Agent 做事”，**安全性（密钥脱敏、访问控制、凭证隔离）、运行时稳定性（内存泄漏、连接保活、崩溃恢复）以及多 Agent 协作（A2A、目标模式）** 成为最核心的议题。另一方面，以 OpenClaw 为代表的核心项目正在引领一场深度的 **架构重构（Refactoring）**，通过梳理内部代码、统一安全原语和分离关注点，为下一阶段的规模化扩张和生态繁荣奠定基础。尽管各个项目步调不一，但追求企业级可靠性和开发者友好体验是整个生态的一致方向。

### 2. 各项目活跃度对比

下表汇总了各项目在 2026-07-04 的活跃度数据（注：无活动的项目已排除）。

| 项目名称 | Issues 更新数 | PRs 更新数 | 版本发布 | 健康度评估 | 核心动态关键词 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **OpenClaw** | 500 (高) | 500 (极高) | 无 | ⭐⭐⭐⭐ (高) | 大规模重构、安全原语、代码清理、合规性 |
| **NanoBot** | 29 (中) | 38 (高) | 无 | ⭐⭐⭐⭐ (高) | 记忆系统、插件架构、模型兼容性、OAuth |
| **Hermes Agent** | 50 (高) | 50 (高) | 无 | ⭐⭐⭐⭐ (高) | 安全审计、平台兼容性、异步性能、成就系统 |
| **PicoClaw** | 2 (低) | 17 (中) | **v0.3.1** | ⭐⭐⭐⭐ (高) | 渠道重连、Agent协作、配置迁移修复 |
| **NanoClaw** | 1 (低) | 17 (中) | 无 | ⭐⭐⭐ (良好) | 多通道支持、MCP协议兼容、容器运行时 |
| **IronClaw** | 33 (中) | 50 (高) | 无 | ⭐⭐⭐ (良好) | Reborn架构打磨、安全身份层、CI稳定性 |
| **LobsterAI** | - | 14 (中) | **2026.7.3** | ⭐⭐⭐⭐ (高) | CoWork 目标模式、服务部署、性能优化 |
| **CoPaw** | 39 (高) | 33 (高) | 无 | ⭐⭐⭐⭐ (高) | 记忆Reranker、QwenPaw 2.0 Bug修复、安全 |
| **ZeroClaw** | 36 (高) | 50 (高) | 无 | ⭐⭐⭐⭐ (高) | OIDC支持、OOM根因定位、SOP可视化、插件系统 |
| **NullClaw** | 1 (低) | 0 | 无 | ⭐⭐ (中等) | 社区动态极少，核心开发停滞 |
| **TinyClaw** | 0 | 0 | 无 | ⭐⭐ (低) | 无活动 |
| **Moltis** | 0 | 0 | 无 | ⭐ (新项目) | 无活动 |
| **ZeptoClaw** | 0 | 0 | 无 | ⭐⭐ (低) | 无活动 |

**注**：`nullclaw` 虽然有新Issue，但核心PR活动为零，健康度较低。`IronClaw` 因CI红色和多个严重Bug待解决，健康度评为良好。

### 3. OpenClaw 在生态中的定位

OpenClaw 是当前生态中 **绝对的“基础平台”和“核心参照系”**，其地位尤为突出：

*   **社区规模与活跃度碾压**：从数据看，OpenClaw 的 Issue/PR 数量（各500条）是其他活跃项目的5-10倍。这种量级表明其拥有最庞大的贡献者群体和最复杂的社区生态。
*   **技术路线：稳定压倒一切**：与 NanoBot 和 NanoClaw 积极引入新功能（插件、MCP）不同，OpenClaw 本周期的重点是 **“清理债务”**。其核心维护者 `RomneyDa` 主导的大规模重构（Refactoring），指向了 **代码可维护性、安全性和合规性**。这与 ZeroClaw 社区热议的 OIDC 和企业级安全需求高度一致，表明 OpenClaw 正在为成为生产级基础设施铺路。
*   **关键差异**：
    *   **与 Hermes Agent 相比**：Hermes 侧重于修复平台兼容性和安全漏洞（如密钥泄露），而 OpenClaw 是主动进行预防性的架构重构以从根本上消除此类问题。
    *   **与 NanoBot 相比**：NanoBot 通过插件系统快速响应新需求（如 OAuth），迭代速度快；OpenClaw 则更偏向于核心引擎的稳定性，通过 PR #99757 等重构来统一配置和逻辑路径。
    *   **总结**：OpenClaw 像一个 **“操作系统内核”**，其他项目则像是基于此内核或受其启发的 **“特色发行版”**。其社区动态是所有下游项目开发者需要密切关注的风向标。

### 4. 共同关注的技术方向

多个项目不约而同地涌现出相似的需求和问题，揭示了行业共性痛点：

*   **安全与凭证管理**（**涉及**：OpenClaw, Hermes Agent, CoPaw, ZeroClaw）
    *   **具体诉求**：隐藏/脱敏 API 密钥（#10659）、社区热议的密钥安全方案（`CoPaw #5705`）、OIDC 认证支持（`ZeroClaw #7141`）、凭证跨平台隔离（`Hermes #12058`）、凭证泄露至磁盘（`Hermes #48441`）。这说明 **“零信任”和“最小权限”原则** 正从概念走向社区刚需。
*   **运行时稳定性与内存管理**（**涉及**：OpenClaw, Hermes Agent, ZeroClaw, PicoClaw）
    *   **具体诉求**：OOM 问题（`ZeroClaw #8642`）、连接保活/重连（`PicoClaw #3178`）、异步函数缺少 `await` 导致崩溃（`Hermes #58010`）、180秒超时无进度重用（`OpenClaw #92043`）。稳定性是 Agent 从玩具走向工具的核心瓶颈。
*   **多 Agent 协作与工作流**（**涉及**：OpenClaw, NanoBot, PicoClaw, LobsterAI）
    *   **具体诉求**：子 Agent 工具限制（`OpenClaw #15032`）、A2A 编排（`NanoBot #4179`）、Agent 协作总线（`PicoClaw #2937`）、CoWork 目标模式（`LobsterAI`）。用户不再满足于单个 Agent 聊天，而是需要 **复杂的、有组织的工作流**。
*   **Agent 行为可控性与可解释性**（**涉及**：OpenClaw, NanoBot, CoPaw, ZeroClaw）
    *   **具体诉求**：工具调用间文本泄漏（`OpenClaw #25592`）、短期记忆丢失（`NanoBot #4044`）、上下文压缩导致“失忆”（`CoPaw #5746`）、SOP 步骤被假完成（`ZeroClaw #8631`）。用户对 Agent 的“黑箱”行为感到不满，要求 **更高的透明度和可干预性**。

### 5. 差异化定位分析

| 特性/项目 | OpenClaw | NanoBot | Hermes Agent | PicoClaw | ZeroClaw | LobsterAI |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **核心定位** | **基础平台/框架** | **个人通用助手** | **AI 编码代理** | **嵌入式/边缘 Agent** | **企业级工作流平台** | **AI 协作与部署平台** |
| **功能侧重** | 核心架构、安全原语、合规性 | 记忆管理、插件生态、PWA | 编码辅助、MCP集成、OAuth | 多通讯渠道（WhatsApp等） | SOP管理、WASM插件、认证 | CoWork协作、子Agent面板、服务部署 |
| **目标用户** | 高级开发者/企业架构师 | 个人用户/轻度开发者 | AI 编码发烧友 | 个人/小团队 | 企业/团队 | 企业/开发者团队 |
| **技术架构** | 模块化重构，追求内部一致性和合规 | 轻量级、插件化、快速迭代 | 针对异步和平台兼容性优化 | 强渠道适配，关注连接鲁棒性 | 基于 RFC 的严肃演进，强安全模型 | 基于 OpenClaw，强调协作交互 |
| **差异化优势** | 社区最大、最成熟的“稳定核心” | 最活跃的“功能快速响应” | 最强的“编码场景”优化 | 最广的“通讯渠道”覆盖 | 最系统的“企业级工作流”管理 | 最直观的“多Agent协作”界面 |

### 6. 社区热度与成熟度

*   **第一梯队：快速迭代与功能扩展期（活跃度极高）**
    *   **OpenClaw**：虽然进行重构，但呈现实时、大规模、高密度的开发协作，社区响应迅速。
    *   **NanoBot**：PR 提交和合并频繁，快速落地插件、OAuth 等新功能，开发者参与度高。
    *   **ZeroClaw**：围绕 RFC 展开体系化开发，同时处理大量并行任务，社区讨论专业且深入。

*   **第二梯队：功能巩固与质量提升期（活跃度高）**
    *   **Hermes Agent**：在快速修复 Bug 和填补安全漏洞的同时，合并小的功能增强，处于边修复边前进的阶段。
    *   **PicoClaw**：围绕渠道稳定性和版本补丁进行小步快跑，维护节奏健康。
    *   **LobsterAI**：在自家核心功能（CoWork）上深度打磨并发布新版本，是专注的产品化路线。
    *   **CoPaw**：在跟随 QwenPaw 2.0 社区反馈进行高强度修复，是典型的“测试-反馈-修复”循环。

*   **第三梯队：停滞或起步期（活跃度低）**
    *   **NullClaw, TinyClaw, Moltis, ZeptoClaw**：核心开发活动基本停滞，社区仅有零星的 Bug 反馈或完全静默。

### 7. 值得关注的趋势信号

1.  **“安全左移”成为共识**：从 `OpenClaw` 的重构安全原语，到 `CoPaw` 的用户提交系统性安全方案，再到 `ZeroClaw` 的企业级 OIDC 提案。**开发者应立刻将密钥管理、访问控制 (RBAC) 和审计日志作为 Agent 应用的必要组成部分**，而非事后补丁。

2.  **记忆系统是“圣杯”也是“阿喀琉斯之踵”**：`NanoBot` 的短期记忆丢失、`CoPaw` 的上下文压缩错误、`OpenClaw` 的搜索竞争条件，均指向 **记忆检索的准确性、一致性和资源消耗** 是当前最大的技术挑战。**任何构建复杂 Agent 的开发者，都必须投入精力研究和选用正确的记忆模型（如分层记忆、RAG + 重排序器），并建立监控机制**。

3.  **从单体 Agent 到 Agent 网格**：`ZeroClaw` 的 SOP、`LobsterAI` 的 CoWork、`NanoBot` 的 A2A 编排需求，标志着 **将多个专业 Agent 编排成一个工作流** 的模式正成为主流。**开发者应开始使用 MCP 或 A2A 等开放协议来解耦 Agent 能力，并将工作流定义（如 SOP）与 Agent 本体分离**。

4.  **“连接”优于“能力”**：`PicoClaw` 投入大量精力修复 WhatsApp 连接问题，`Hermes Agent` 处理 Telegram 与 CLI 的差异。这提示 **Agent 成功的门槛不在于其核心模型有多强，而在于它是否能无缝、可靠地融入用户已有的工作流和通讯习惯中**。渠道稳定性和跨平台一致性是关键。

---

**总结**：AI 智能体开源生态正从一个充满激情的“淘金潮”阶段，进入一个需要扎实“基建”和精细化运营的“建城”阶段。对于技术决策者而言，**选择 OpenClaw 作为基础平台以获取长期稳定性，同时关注 NanoBot/ZeroClaw 等以其新特性作为功能参考，是一个值得考虑的策略**。对于开发者而言，**深入理解记忆系统、安全模型和 Agent 工作流编排**，将是未来 1-2 年内最重要的技术投资。

---

## 同赛道项目详细报告

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

好的，作为 NanoBot 项目的 AI 智能体与开源项目分析师，以下是为您生成的 2026-07-04 项目动态日报。

---

# NanoBot 项目动态日报 | 2026-07-04

## 1. 今日速览

项目今日**极其活跃**，社区贡献热情高涨。过去24小时内，共有 **29 个 Issues** 和 **38 个 PRs** 被更新，显示项目正处于高速迭代期。问题主要集中在**内存管理机制**（长期记忆与短期记忆的冲突）、**MCP 工具稳定性**和 **WebUI 体验优化**上。值得注意的是一批针对 `temperature` 参数和 Claude Sonnet 5 模型兼容性的 Bug 已被迅速修复并合并，体现了开发团队对重要反馈的快速响应能力。目前仍有较多待合并的 PR（32个），预示着下一个版本将包含丰富的功能更新。

- **活跃度评估**: ⭐⭐⭐⭐⭐ (极高) - 社区反馈和代码贡献均非常活跃。

## 3. 项目进展

今日合并/关闭了 **6 个 PRs**，主要聚焦于 Bug 修复和关键功能增强：

- **[Merged] PR #4687: 更新 Anthropic 默认模型** - 将过时的默认模型从 `claude-sonnet-4-20250514` 更新为 `claude-sonnet-4-6`，确保了新用户开箱即用的兼容性。 (https://github.com/HKUDS/nanobot/pull/4687)
- **[Merged] PR #4685: 修复 Sonnet 5 的 `temperature` 参数问题** - 修复了向 Claude Sonnet 5 发送 `temperature` 参数导致 `400` 错误的问题，保证了 Anthropic 最新模型的支持。 (https://github.com/HKUDS/nanobot/pull/4685)
- **[Merged] PR #4632: 新增 Anthropic OAuth 提供者** - 支持 Claude Code 的 OAuth Token，为没有 Anthropic API 密钥的订阅用户提供了便捷的接入方式，降低了使用门槛。 (https://github.com/HKUDS/nanobot/pull/4632)
- **[Merged] PR #4396 & #4691: 插件控制系统** - 引入了全新的插件管理架构，允许用户通过 `nanobot plugins` 命令或在 WebUI 中启用/禁用可选功能（如聊天、文档支持），让核心安装更精简，同时提升了功能的可发现性和故障恢复能力。 (https://github.com/HKUDS/nanobot/pull/4396) (https://github.com/HKUDS/nanobot/pull/4691)
- **[Merged] PR #4688: 安全的 WebUI 首次启动器** - 新增 `nanobot webui` 命令，提供了一键式安全启动流程，自动检查配置和依赖，改善了新用户的入门体验。 (https://github.com/HKUDS/nanobot/pull/4688)

**项目向前迈进**: 今天的主要进步在于生态扩展（OAuth、插件系统）和基础健壮性（模型兼容性、模型默认值）的提升，这为项目吸引更多非技术用户和开发者奠定了良好基础。

## 4. 社区热点

今日讨论最活跃的议题集中在**记忆系统的认知一致性**上。

- **#4044: 短期记忆丢失** - 这是一个长期存在的问题，引发了社区的广泛共鸣（6条评论）。用户痛点在于，Agent 在对话中会“失忆”，无法记住自己刚刚提出的问题。背后的诉求是希望 Nanobot 能拥有更强大、更智能的上下文窗口管理和记忆机制，而非简单的 token 截断。相关 PR #4280 已提交，尝试解决该问题。 (https://github.com/HKUDS/nanobot/issues/4044)
- **#4061: OpenAI 兼容供应商的 Tool Call 解析失败** - 揭示了生态兼容性的一个难点：部分第三方供应商以文本形式返回工具调用，而非标准结构体。用户希望 Nanobot 的解析器能更鲁棒，兼容非标准实现，避免将原始文本返回给用户。 (https://github.com/HKUDS/nanobot/issues/4061)
- **#3744: 团队合作中 Session 级别的 Memory** - 该需求直指多用户场景下的痛点。当多个用户共享一个 Agent 时，`USER.md` 和 `MEMORY.md` 的混用会产生隐私和逻辑冲突。用户强烈需要一个以“会话（Session）”为粒度的隔离记忆机制，这是一个关键的路线图信号。 (https://github.com/HKUDS/nanobot/issues/3744)

## 5. Bug 与稳定性

今日报告的 Bug 按严重程度排列如下：

- **P0 - 崩溃/Crash**:
    - **#4652: MCP 工具调用异常导致进程崩溃** - 当 MCP 工具返回错误或空数据时，程序直接闪退，没有任何容错处理。**已有 Fix PR #4666**: 通过包装渲染结果并对超时、取消等异常进行结构化处理来提升稳定性。 (https://github.com/HKUDS/nanobot/issues/4652)
    - **#4302: MCP 重连后 Gateway 崩溃** - 会话终止后，MCP 重连机制导致 Gateway 级别崩溃，严重影响长时间运行的服务。 (https://github.com/HKUDS/nanobot/issues/4302)

- **P1 - 主要功能异常**:
    - **#4061: 文本格式 Tool Call 无法解析** - 导致无法与部分非标准 API 对接。 (https://github.com/HKUDS/nanobot/issues/4061)
    - **#4044: 短期记忆丢失** - 严重影响对话连贯性，是用户感知最强的 Bug。 (https://github.com/HKUDS/nanobot/issues/4044)
    - **#4307: 后置上下文整理会清除 Agent 的交付消息** - 导致用户无法引用 Agent 上一轮次的输出，这是一个设计缺陷。 (https://github.com/HKUDS/nanobot/issues/4307)

- **P2 - 平台/配置兼容性**:
    - **#4511: Windows 后台进程信息不一致** - 重启后进程信息文件未更新，影响后台任务管理。**已有 Fix PR #4690**。 (https://github.com/HKUDS/nanobot/issues/4511)
    - **#4683: Sonnet 5 的 `temperature` 参数问题** - 已通过 PR #4685 修复。 (https://github.com/HKUDS/nanobot/issues/4683)

- **P3 - 非核心功能**:
    - **#3626: Telegram 长轮询静默挂起** - 网络波动会导致机器人看似存活但停止接收消息，是渠道层面的稳定性问题。 (https://github.com/HKUDS/nanobot/issues/3626)

## 6. 功能请求与路线图信号

今日收到的新功能请求和已有 PR 展示了以下几个关键路线图方向：

- **1. 记忆与上下文增强**:
    - **#4440: `search_history` 只读工具** - 允许 Agent 主动从历史记录（`memory/history.jsonl`）中检索信息。该需求已有对应 **PR #4439**，大概率会进入下一版本。
    - **#4212: 防止“记忆污染”** - 用户担心未被确认的推断会作为事实被固化到长期记忆中，并很难被更正。这是一个关于记忆系统准确性和可信度的深刻需求。
    - **#4508: `ask_clarification` 工具** - 希望 Agent 在面对模糊需求时能主动提问澄清，而不是盲目猜测。这代表了提升 Agent 交互质量的方向。

- **2. 多 Agent 与系统集成**:
    - **#4179: 原生 Agent-to-Agent (A2A) 编排** - 用户希望创建“主管-研究员-写手”这样的多 Agent 团队，这是一个迈向复杂工作流的关键架构请求。
    - **#4166: 允许子 Agent 访问 MCP 服务** - 目前子 Agent 无法使用宿主配置的 MCP 工具，限制了其能力。
    - **#4218: WebUI 定时任务管理** - 将强大的 CLI `cron` 功能带到 WebUI，降低管理复杂度。

- **3. 用户界面与体验**:
    - **#4479: PWA 支持与移动端手势** - 社区已提交了功能实现，表明对移动端体验的迫切需求。
    - **#4693: 进一步改善 WebUI 移动端响应式布局** - 与 PWA 功能相辅相成。

**版本信号**: 结合大量已合并和待合并的 PR（如 OAuth 支持、插件系统、cron 增强、记忆修复），NanoBot 的 **0.3.0** 或下一个重要版本将是一次重大的功能迭代，预计会包含全新的**插件架构**、**更丰富的记忆管理和检索能力**、以及**对更多后端模型和渠道的深度支持**。

## 7. 用户反馈摘要

从今日的 Issues 评论中，我们提炼出以下真实用户反馈：

- **正面反馈**: 用户对项目的发展方向（如插件化、“less is more”的哲学）和快速修复能力表示认可。Issue #3846 中的用户对 `nanobot` 的多轮对话技能处理方案给予了高度评价（+1）。
- **痛点 - 记忆与上下文**: 这是目前最普遍的痛点。用户明确感受到“它不记得自己说过什么”（Issuse #4044），并且这种失忆不是简单的配置问题，而是核心机制需要改进。用户描述“会话在它的回合和你的回合之间断裂”非常形象。
- **痛点 - 稳定性**: MCP 工具相关的崩溃问题（Issuse #4652, #4302）让重度用户感到非常沮丧，直接导致服务不可用。
- **使用场景**: 用户群体多样化，包括个人助理、通过 Telegram/飞书等渠道的团队协作（Issuse #3744）、以及集成进自动化工作流（Issuse #4431心率监测、#4290 cron 任务）。
- **不满意的地方**: WebUI 的移动端体验是明显的短板，用户在 Issue #4693 中详细描述了“内容被裁剪”、“输入框被键盘遮挡”等具体困境。

## 8. 待处理积压

以下为久未更新或响应，但重要性较高的议题，建议维护者关注：

- **Issues**:
    1.  **#3626: Telegram 长轮询问题** - 自5月5日报告，至今已有2个月，仍无进展。对于依赖 Telegram 的用户而言，这是一个长期存在的基础稳定性问题。 (https://github.com/HKUDS/nanobot/issues/3626)
    2.  **#3744: 团队合作中 Session 级别的 Memory** - 这是一个被广泛讨论且需要架构性设计的特性，作为社区强需求的代表，应被纳入路线图规划。 (https://github.com/HKUDS/nanobot/issues/3744)
    3.  **#3769: `nanobot doctor` 诊断命令** - 一个能极大提升用户自排查能力的实用工具，增强项目专业度，值得优先考虑。 (https://github.com/HKUDS/nanobot/issues/3769)

- **Pull Requests**:
    1.  **#4280: 修复上下文压力下的记忆连续性** - 这个 PR 直接关联到社区最热的 Issue #4044（短期记忆丢失），但尚未合并。如果此 PR 能解决问题，将极大缓解用户的核心痛点。 (https://github.com/HKUDS/nanobot/pull/4280)
    2.  **#4459: Mattermost 渠道支持** - 作为一个新的企业级渠道集成，该 PR 已搁置超过10天，需要维护者审阅以确定是否纳入。 (https://github.com/HKUDS/nanobot/pull/4459)

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，以下是根据 Hermes Agent 项目 2026-07-04 的 GitHub 数据生成的每日项目动态日报。

---

# Hermes Agent 项目动态日报 (2026-07-04)

## 1. 今日速览

Hermes Agent 项目今日呈现 **高度活跃** 状态。过去 24 小时内，社区共提交了 50 条 Issues 和 50 条 PRs，显示出极高的贡献热情。当前项目健康状况良好，但 Bug 修复和新功能请求的比例相当，开发者正面维持稳定性和推进功能的双重挑战。值得注意的是，安全相关（OAuth、密钥泄露、文件权限）和平台兼容性（Windows、Docker、Telegram）问题是社区关注的焦点，维护团队已针对多个高危问题提交了高优先级的修复 PR。

## 2. 版本发布

本轮报告周期内 **无新版本发布**。

## 3. 项目进展

今日共有 **7 个 PR 被合并或关闭**，推动了以下方面的改进：

- **成就系统 (Achievements)：** 两个关于同一功能（添加导出端点和代理摘要）的 PR 被合并/关闭 (PRs [#58015](https://github.com/NousResearch/hermes-agent/pull/58015), [#58012](https://github.com/NousResearch/hermes-agent/pull/58012))，表明此功能已进入稳定阶段。
- **性能与兼容性：** PR [#51592](https://github.com/NousResearch/hermes-agent/pull/51592) 修复了 Docker 构建中的 overlayfs 性能问题，通过合并文件操作优化了镜像构建速度。
- **平台功能适配：** 为 Telegram 网关增加了外部回调处理程序 (PR [#57999](https://github.com/NousResearch/hermes-agent/pull/57999))，增强了其可扩展性。

这些合并标志着项目在解决近期痛点方面迈出了坚实的步伐。

## 4. 社区热点

今日社区讨论呈现出 **问题解决导向** 的特点，高评论 Issues 主要围绕严重的 Bug 和实用的功能请求。

- 最活跃 Bug 讨论：
  - **[#12058](https://github.com/NousResearch/hermes-agent/issues/12058) [Bug]: OpenAI Codex OAuth works in CLI, but Telegram gateway replies No Codex credentials stored** (5 条评论)。用户报告了 CLI 和 Telegram 网关之间严重的认证凭证不一致问题。这反映了多平台网关下凭证隔离和复用机制的潜在缺陷。
  - **[#48441](https://github.com/NousResearch/hermes-agent/issues/48441) [Security]: Terminal session snapshots leak .env secrets to disk in plaintext** (5 条评论, 1 👍)。此问题涉及严重的终端会话快照功能导致的明文密钥泄露，已被关闭，表明项目维护者对此类安全问题响应迅速。
- 高需求功能请求：
  - **[#40173](https://github.com/NousResearch/hermes-agent/issues/40173) feat(telegram): channel_profiles — route Telegram chats to Hermes profiles in one gateway** (3 👍)。社区强烈期望单一 Telegram 机器人能服务于多个代理配置环境，这个请求解决了运行多个机器人实例的痛点。

这些热点揭示了用户对 **身份认证的跨平台一致性** 和 **多代理管理的灵活性** 有强烈需求。

## 5. Bug 与稳定性

今日报告的 Bug 集中在几个关键领域，部分已有修复 PR。

| 严重程度 | Issue | 描述 | 状态 |
| :--- | :--- | :--- | :--- |
| **严重** | [#48441](https://github.com/NousResearch/hermes-agent/issues/48441) | 终端会话快照导致 .env 密钥明文泄露到磁盘 | 已关闭 |
| **高** | [#48534](https://github.com/NousResearch/hermes-agent/issues/48534) | Anthropic Max OAuth 由于 User-Agent 被屏蔽导致 token 交换失败 | 开放中，待修复 |
| **高** | [#54675](https://github.com/NousResearch/hermes-agent/issues/54675) | 多路复用网关中，Bot Token 绕过 per-profile 密钥作用域 | 开放中，有重复标记 |
| **高** | [#58010](https://github.com/NousResearch/hermes-agent/issues/58010) | `AsyncSessionDB` 缺少 `await`，导致 `/resume` 命令崩溃 (P1) | 开放中，有重复标记 |
| **中** | [#57903](https://github.com/NousResearch/hermes-agent/issues/57903) | 异步 LLM 调用在 Desktop WebSocket 中使用忙轮询阻塞循环 | 开放中，已有草案 PR [#57933](https://github.com/NousResearch/hermes-agent/pull/57933) |
| **中** | [#57928](https://github.com/NousResearch/hermes-agent/issues/57928) | Telegram 中的文件附件在配合 `/steer` 等命令时被静默丢弃 | 开放中 |
| **中** | [#57967](https://github.com/NousResearch/hermes-agent/issues/57967) | `hermes kanban create` 成功返回 ID 但数据库提交失败导致数据丢失 | 开放中，需复现 |

**注：** 严重级别 Bug 的修复速度很快（如 #48441 和 #58010），但部分 Bug 的重复标记（如 #54675）可能意味着需要更系统的方案来解决根本问题。

## 6. 功能请求与路线图信号

今日的功能请求呈现出 **平台深度集成**、**用户自定义** 和 **可观测性** 三个趋势。

- **平台深度集成：**
  - **[#46337](https://github.com/NousResearch/hermes-agent/issues/46337) Add UI for Custom Local STT/TTS...**: 用户希望 Hermes Desktop 能支持自定义的本地语音、图像生成提供商。
  - **[#31776](https://github.com/NousResearch/hermes-agent/issues/31776) Expose multi-bank routing for Hindsight memory**: 扩展记忆功能，支持按复杂条件路由到不同的记忆库。
  - **[#50668](https://github.com/NousResearch/hermes-agent/issues/50668) Telegram cron delivery should create fresh DM topic**：改进 Telegram 定时任务的消息投递逻辑。
- **用户自定义与迁移：**
  - **[#524](https://github.com/NousResearch/hermes-agent/issues/524) Agent Migration System**: 用户希望从其他 AI 编码代理（如 Claude Code, Cursor）迁移时能自动导入配置，表明项目在争取新用户导入方面有潜力。
- **可观测性：**
  - **[#57973](https://github.com/NousResearch/hermes-agent/issues/57973) Expose per-model MoA usage accounting**: 用户希望更细粒度的模型使用统计，用于本地成本核算。

已经有 PR 尝试解决部分问题（如 [#57984](https://github.com/NousResearch/hermes-agent/pull/57984) 添加了 OpenAI Agents SDK 桥），这些趋势很可能在下一个版本中得到体现。

## 7. 用户反馈摘要

- **痛点：**
  - **平台间行为不一致：(** 用户在 Telegram 网关使用 Codex 时遭遇认证问题 (#12058)，而 CLI 正常，这严重影响了多平台工作流。
  - **配置复杂性：** 用户抱怨 Docker 配置文档不完善，且无法通过环境变量轻松设置模型配置 (#12188)。
  - **不透明的失败：** Bug 报告显示，工具输出被内容引用标签替换 (#58009)、文件附件被静默丢弃 (#57928)、配置文件无变化时仍被标记 (#57931)，这些都降低了用户对 Agent 行为的信任。
  - **Windows 体验不佳：** 多个 Windows 相关 Bug 被提出，如空白的控制台窗口闪烁 (#56747) 和 git 克隆的 MCP 目录无法删除 (#58008)，表明 Windows 平台的用户体验和稳定性有待提升。
- **满意点：**
  - 用户对希望增加的功能，如 **Telegram 频道路由** (#40173)、**可配置的 Discord 语音超时** (#17790) 表达了明确的赞同（👍），表明项目方向与社区需求吻合。
- **使用场景：**
  - 用户主要在 **自托管/生产环境**（Docker, Coolify, Railway）和 **桌面应用**（Windows, Ubuntu）中使用 Hermes Agent，用于 **AI 编码辅助**、**任务自动化**（cron, kanban）和 **多平台机器人**（Telegram, Discord, WhatsApp）。

## 8. 待处理积压

以下 Issue 或 PR 可能因其重要性和等待响应时间值得维护者特别关注：

- **长期未响应的核心功能请求：**
  - **[#524](https://github.com/NousResearch/hermes-agent/issues/524) Feature: Agent Migration System** (创建于 2026-03-06)。这是一个能大幅降低新用户进入门槛的功能，已获得一定支持，但未见到最近的维护者评论或开发活动。如果被采纳，可能成为项目重要的增长点。
- **开放的、高影响力的安全问题：**
  - **[#48534](https://github.com/NousResearch/hermes-agent/issues/48534) Anthropic Max OAuth fails** (P1, 2026-06-18)。此问题阻塞了使用 Anthropic 模型的用户认证流程，虽已被定位，但仍未修复。这对于依赖 Anthropic 的用户是关键阻塞项。
- **潜在的回归风险：**
  - **[#3651](https://github.com/NousResearch/hermes-agent/pull/3651) feat(secrets): add phase 1 secrets tool** (P2, 2026-03-29)。这是一个涉及安全边界的重要 PR，合并至今已有数月。需要确认它是否已在最近的版本中完全生效，以及是否有新的边缘情况（如 [#57955](https://github.com/NousResearch/hermes-agent/issues/57955) 中提到的 `terminal` 工具绕过文件保护）未被覆盖。

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，以下是为您生成的 PicoClaw 项目动态日报。

---

# PicoClaw 项目动态日报 | 2026-07-04

## 1. 今日速览
今日 PicoClaw 项目活跃度较高，共计处理了 2 个新 Issue 和 17 个 Pull Request，并发布了 `v0.3.1` 补丁版本。社区核心贡献者（如 `AME0BIUS`）提交了多项针对 WhatsApp、Matrix 等渠道的稳定性修复，表明项目正集中力量解决连接鲁棒性问题。尽管 Issue 数量不多，但近期爆发的 PR 活动（特别是针对渠道重连和 Agent 协作功能的合并）预示着项目内部架构正在快速迭代。**总体健康度良好，处于稳定发展的活跃期。**

## 2. 版本发布
- **版本号**: `v0.3.1`
- **链接**: [Release v0.3.1](https://github.com/sipeed/picoclaw/releases/tag/v0.3.1)
- **更新内容**:
  - 本次发布为小版本补丁，主要包含了来自依赖库 `nearai-provider` 和 `go-sdk` 的合并更新。
  - 修复了 `codex/store` 中的类型断言问题。
- **破坏性变更**: 无。
- **迁移注意事项**: 普通更新，建议所有 `v0.3.x` 用户升级。

## 3. 项目进展
今日，项目在 **稳定性** 和 **新功能** 两个维度上均有实质进展：

- **核心架构推进**:
    - **[Agent 协作]** 持续优化 Agent 间的 `clear` 命令。PR #3224 (`fix(agent): clear routed agent session`) 已修复了在多 Agent 场景下，`/clear` 命令会错误清除默认 Agent 会话而非当前路由 Agent 会话的Bug。[#3224](https://github.com/sipeed/picoclaw/pull/3224)
    - **[渠道稳定性]** 针对 WhatsApp 和 Matrix 渠道的连接断开问题，贡献者 `AME0BIUS` 提交了三个关键修复：
        - PR #3220: 为 WhatsApp 添加了带指数退避的 Websocket 重连机制。[#3220](https://github.com/sipeed/picoclaw/pull/3220)
        - PR #3219: 为 Matrix 同步循环添加了带退避的重连机制，防止网络中断后永久卡死。[#3219](https://github.com/sipeed/picoclaw/pull/3219)
        - PR #3218: 修复了配置文件从 v2 迁移到 v3 时，因缺少 `build_info` 字段导致的“未知字段”阻塞错误。[#3218](https://github.com/sipeed/picoclaw/pull/3218)
    - **[新渠道 & 功能]**：
        - PR #3217: 为 **Discord** 渠道引入了基于角色的访问控制 (`allow_roles`)，授权更精细。[#3217](https://github.com/sipeed/picoclaw/pull/3217)
        - PR #3193: 新增 **Simplex** 渠道支持，进一步扩展了通信方式。[#3193](https://github.com/sipeed/picoclaw/pull/3193)
    - **[代码清理]** PR #3222 (`refactor(deltachat)`) 对 DeltaChat 渠道进行了大规模清理，删除了约 320 行过时代码和依赖，提升了代码可维护性。[#3222](https://github.com/sipeed/picoclaw/pull/3222)
- **已合并/关闭的 PR**
    - PR #3128: 修复了四个搜索引擎函数中忽略 `resp.Body.Close()` 错误的问题。[#3128](https://github.com/sipeed/picoclaw/pull/3128)
    - PR #3142: 修复了 spawn 子任务中 `ForUser` 字段导致重复消息推送的问题。[#3142](https://github.com/sipeed/picoclaw/pull/3142)
    - PR #3156: 实现了通过 Pico 通道在每轮对话结束时发送 LLM token 用量信息。[#3156](https://github.com/sipeed/picoclaw/pull/3156)

## 4. 社区热点
- **WhatsApp 连接稳定性（#3178 & #3179 & #3220）**:
    - Issue #3178 报告了 WhatsApp 的 Websocket 超时问题，指出服务在运行 2-3 天后会静默断开且无法恢复。[#3178](https://github.com/sipeed/picoclaw/issues/3178)
    - **分析**: 这表明 WhatsApp 渠道的稳定性是当前社区最关心的痛点之一。已有 PR #3179 和今日的 #3220 提出了具体方案，开发团队积极响应，显示出对核心功能可靠性的重视。

## 5. Bug 与稳定性
按严重程度排列：

| 严重程度 | Bug 描述 | Issue/PR 链接 | 是否已有 Fix PR |
| :--- | :--- | :--- | :--- |
| **高** | **WhatsApp 服务静默断开且无法恢复**：Websocket 读循环在检测到错误后不停重试，但连接已死亡。 | [#3178](https://github.com/sipeed/picoclaw/issues/3178) <br> [#3220](https://github.com/sipeed/picoclaw/pull/3220) | 是 (PR #3220) |
| **高** | **Matrix 同步循环永久死亡**：网络中断或服务器重启后，同步循环直接退出，导致机器人永久离线。 | [#3219](https://github.com/sipeed/picoclaw/pull/3219) | 是 (PR #3219) |
| **中** | **Android 版本无法启动**：用户在 Android 上遇到启动服务问题，无法修改路径。 | [#3182](https://github.com/sipeed/picoclaw/issues/3182) | 无 (已标记为 `stale`) |
| **中** | **配置迁移失败**：从 v2 迁移到 v3 时，因 `build_info` 字段缺失导致迁移被阻塞。 | [#3218](https://github.com/sipeed/picoclaw/pull/3218) | 是 (PR #3218) |
| **中** | **多 Agent 场景下 `/clear` 命令行为错误**：/clear 会清除默认 Agent 的会话，而非当前 Agent。 | [#3224](https://github.com/sipeed/picoclaw/pull/3224) | 是 (PR #3224) |

## 6. 功能请求与路线图信号
- **Agent 协作（#2937）**：PR #2937 (`Feat/agent collaboration`) 引入了“Agent 协作总线”的设计，为 Agent 间通信、邮件、隔离会话等提供了基础框架。这是一个重要的路线图信号，表明项目正朝着更复杂的多 Agent 工作流演进。[#2937](https://github.com/sipeed/picoclaw/pull/2937)
- **可配置的默认模型回退链（#3200）**：PR #3200 新增了在 WebUI 中配置模型回退链路的功能，当首选模型不可用时自动切换。这提升了用户体验，特别是对于依赖第三方 API 的场景。[#3200](https://github.com/sipeed/picoclaw/pull/3200)
- **Discord 角色基访问控制（RBAC）（#3217）**：PR #3217 引入了 `allow_roles`，允许更精细地控制谁可以在 Discord 上使用机器人，满足了社区协作场景的安全需求。[#3217](https://github.com/sipeed/picoclaw/pull/3217)
- **新渠道扩展**：`Simplex` (#3193) 和 `DeltaChat` 的持续重构 (#3222) 表明项目意图覆盖更多去中心化和隐私优先的通信协议。

## 7. 用户反馈摘要
- **痛点明确**：用户 `Jh123x` 报告 WhatsApp 连接超时问题，并提供了详细的复现步骤、环境信息和截图，反馈质量极高。这反映出项目核心通讯渠道的稳定性测试需要加强。
- **使用场景多元**：用户 `Monessem` 遇到 Android 版本启动问题，表明项目存在跨平台适配的挑战，尤其是在移动端。

## 8. 待处理积压
- **[PR #2937] Agent 协作**：该 PR 自 2026-05-24 起已开放 40 天，涉及重大功能变更。尽管已标记 `feat`，但长时间未合并，可能需要更多 review 或存在未解决的架构争议。建议维护者关注。[#2937](https://github.com/sipeed/picoclaw/pull/2937)
- **[Issue #3182] Android 版本无法启动**：此问题已标记为 `stale`，且无回复。考虑到移动端用户群体，建议维护者跟进或标记为已知限制。[#3182](https://github.com/sipeed/picoclaw/issues/3182)

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

# NanoClaw 项目动态日报 | 2026-07-04

## 1. 今日速览

过去24小时内，NanoClaw 项目保持**中等活跃度**，共产生1条新 Issue 和17条 PR 更新。值得注意的是，待合并 PR 积压已达到15条，较昨日略有增加，但已有2条 PR 被关闭或合并，显示出维护团队的持续工作。社区关注点集中在**本地模型 MCP 工具 Schema 的开销问题**，以及**WhatsApp/Signal 等通讯渠道的稳定性修复**。目前项目尚未发布新版本，但大量修复和功能 PR 正在排队等待合并，预示着一轮集中发布可能即将到来。

## 2. 版本发布

- **无新版本发布。**

## 3. 项目进展

**已合并/关闭（2条）：**
- **PR #2765**：已关闭的 `feat(providers): add .format-lint-off`（作者：@amit-shafnir），新增了 Provider 侧的格式化lint开关，有助于CI流程中的代码风格控制。
- **PR #2330**：已关闭的 `fix(container): make axios MCP servers work through OneCLI's proxy`（作者：@Tij8i），修复了 axios v1.x 在 OneCLI 代理下因 `HTTPS_PROXY` 支持问题导致认证注入失败的bug。

**待合并重要进展：**
- **PR #2921**（@michaelzetune）：修复了 compose 过程中所有 skill 的 `instructions.md` 被错误地注入到所有 group 的 `CLAUDE.md` 中，遵循了 group 的 skill 选择逻辑。此修复将直接影响终端用户的 agent 指令精确性。
- **PR #2918**（@joshm1230212）：新增 **LINE Official Account 渠道**（原生适配器 + `/add-line` skill），标志着 NanoClaw 向东亚即时通讯市场的进一步拓展。这是一个较大型的功能PR。

**总体判断：** 项目在**容器运行时稳定性**（Podman keep-id映射、session 过期处理）、**多通道支持**（WhatsApp、Signal、LINE）以及**MCP 协议兼容性**（HTTP/SSE 传输、代理适配）方面持续取得实质性进展，但大量 PR 仍处于开放待合并状态，合并效率有待提升。

## 4. 社区热点

**🌟 Issue #2917（新开，0评论）：本地模型作为主Agent时MCP工具Schema Token开销**
> 链接：[Issue #2917](https://github.com/nanocoai/nanoclaw/issues/2917)

用户 `cappuccinowholemilk-stack` 报告，当 Agent 的“主模型”从 Claude 切换为本地模型（通过 oMLX）时，即使模型不需要调用 MCP 工具，每次请求仍会发送完整的 MCP 工具 Schema 集——在 Gemma4:31B agent 上测试发现有约 **27k tokens** 的额外开销。这是社区对**本地模型部署成本优化**的核心诉求：用户期望系统能根据后端类型动态决定是否/如何附加 MCP Schema，避免对本地模型造成无谓的 token 浪费。该问题目前无评论和标记，但 Token 开销直接影响用户体验和推理成本，具备较高响应优先级。

## 5. Bug 与稳定性

| 严重程度 | 描述 | 链接 | 修复状态 |
|---------|------|------|---------|
| **高** | **容器重启导致 DB 连接泄漏/文档过期/脚本重复** — PR #2920 修复了 `openInboundDb()` 在 restart-check 后未关闭导致文件描述符泄漏的问题；同时还发现了 `formatter.ts` 仍然引用已废弃的 `NANOCLAW_ADMIN_USER_IDS` 环境变量。 | [PR #2920](https://github.com/nanocoai/nanoclaw/pull/2920) | 已有修复 PR |
| **中** | **WhatsApp 通道单定时器重连与清理不彻底** — PR #2348 通过确保单定时器和完全清理解决 reconnection 不一致问题。 | [PR #2348](https://github.com/nanocoai/nanoclaw/pull/2348) | 已有修复 PR |
| **中** | **Signal 通道 DM 被静默丢弃** — PR #2694 修复了 Signal 适配器未设置 `isMention`/`isGroup` 导致路由无法自动创建 `messaging_group`，DM 消息被静默丢弃。 | [PR #2694](https://github.com/nanocoai/nanoclaw/pull/2694) | 已有修复 PR |
| **中** | **Signal 通道图片附件无法在容器内读取** — PR #2695 修复了 Signal 图片附件路径指向宿主机路径，容器内 agent 无法读取的问题。 | [PR #2695](https://github.com/nanocoai/nanoclaw/pull/2695) | 已有修复 PR |
| **低** | **Poll-loop 中 session 过期后原始错误仍显示给用户** — PR #2184 修复了 `isSessionInvalid()` 检测成功后仍将原始错误作为聊天消息显示的问题。 | [PR #2184](https://github.com/nanocoai/nanoclaw/pull/2184) | 已有修复 PR |
| **低** | **poll-loop 中 send_message 在回合中触发时产生重复文本** — PR #2531 抑制了 mid-turn 重复文本输出。 | [PR #2531](https://github.com/nanocoai/nanoclaw/pull/2531) | 已有修复 PR |

**总体判断：** 今日报告的 Bug 主要集中在**通讯通道**（Signal/WhatsApp）和**容器运行时**两方面，且全部已有修复 PR，说明维护团队对于稳定性问题响应及时，但从 Issue 创建到 PR 合并的时间跨度较长（部分如 #2184 已开放2个月），效率仍有提升空间。

## 6. 功能请求与路线图信号

| 功能请求 | 来源 | 链接 | 可能纳入版本 |
|---------|------|------|-------------|
| **LINE Official Account 渠道** | PR #2918（@joshm1230212） | [PR #2918](https://github.com/nanocoai/nanoclaw/pull/2918) | ✅ 高可能性，已提交完整实现 |
| **Google Contacts MCP 工具** | PR #2693（@cfis） | [PR #2693](https://github.com/nanocoai/nanoclaw/pull/2693) | ✅ 高可能性，OneCLI 生态延伸 |
| **系统摘要（System Digest）技能** | PR #2863（@grantland） | [PR #2863](https://github.com/nanocoai/nanoclaw/pull/2863) | ✅ 高可能性，增强 agent 状态感知 |
| **CalDAV 工具** | PR #2530（@cfis） | [PR #2530](https://github.com/nanocoai/nanoclaw/pull/2530) | ✅ 高可能性，日历集成需求明确 |
| **HTTP/SSE MCP 服务器传输** | PR #2208（@cfis） | [PR #2208](https://github.com/nanocoai/nanoclaw/pull/2208) | ✅ 高可能性，MCP 协议兼容性至关重要 |
| **本地模型 MCP Schema 开销优化** | Issue #2917（@cappuccinowholemilk-stack） | [Issue #2917](https://github.com/nanocoai/nanoclaw/issues/2917) | ❓ 尚无对应 PR，需社区/维护者评估 |

**路线图信号：** 项目明显在朝着 **“多通道 + 生态工具集成”** 方向演进（LINE、Gmail、GCal、CalDAV、Google Contacts），同时也在**容器运行时**和**MCP 协议完备性**上持续投入。本地模型 token 使用优化成为突出痛点，可能成为下一阶段的重点议题。

## 7. 用户反馈摘要

- **🔴 用户痛点（Issue #2917）：** 本地模型作为主Agent时被意外收取 27k tokens 的 MCP Schema 开销。用户明确期望系统能够“聪明地”根据后端模型类型判断是否需要传输工具描述，这反映了社区对**成本意识**和**本地模型优化**的强烈需求。
- **🟡 持续性修复（多个 PR）：** 大量 PR 聚焦于 Signal/WhatsApp 通道的消息被丢弃、附件不可读、连接不稳定等问题，说明通讯渠道的用户体验仍是社区关注的重点。cfis 在 Signal 相关 PR 中表现出较高的活跃度。
- **🟢 积极贡献：** @michaelzetune 修复了 compose 指令注入的群组逻辑问题，对多 skill 配置用户友好；@grantland 贡献了系统摘要技能，有助于提升 agent 的上下文感知能力。

## 8. 待处理积压

以下为长期开放、近期无人评论或更新缓慢的重要 Issue/PR，建议维护者关注：

| 类型 | 编号 | 标题 | 开放天数 | 链接 | 建议操作 |
|------|------|------|---------|------|---------|
| 🔴 Bug PR | #2184 | poll-loop 中 session 过期时原始错误仍显示给用户 | 63天 | [PR #2184](https://github.com/nanocoai/nanoclaw/pull/2184) | 建议尽快 review 合并，影响终端用户体验 |
| 🔴 Bug PR | #2348 | WhatsApp 单定时器重连 + 清理 | 57天 | [PR #2348](https://github.com/nanocoai/nanoclaw/pull/2348) | 如无冲突，可考虑合并 |
| 🔴 Bug PR | #2230 | 容器运行时 Podman 用户映射 | 62天 | [PR #2230](https://github.com/nanocoai/nanoclaw/pull/2230) | 容器化部署的关键依赖 |
| 🟡 Feature PR | #2208 | HTTP/SSE MCP 服务器传输 | 62天 | [PR #2208](https://github.com/nanocoai/nanoclaw/pull/2208) | 若与现有功能不冲突应优先合并 |
| 🟡 Feature PR | #2493 | 跨组持续 `continue` 指令支持 | 约48天 | [PR #2493](https://github.com/nanocoai/nanoclaw/pull/2493) | 长期开放未更新，需确认 maintainer 意愿 |
| 🟡 新 Issue | #2917 | 本地模型 MCP 工具 Schema Token 开销 | 1天 | [Issue #2917](https://github.com/nanocoai/nanoclaw/issues/2917) | 建议标记 `cost-optimization` 或 `good-first-issue` 引导社区参与 |

**积压趋势分析：** 项目当前有 **10条开放 PR 等待合并**（标记“待合并”），其中近半开放超过30天。待合并 PR 数量（15条）显著高于已合并/关闭数量（2条），说明合并瓶颈较为突出。建议维护团队评估是否可安排集中的代码 review 日，或者引入代码审查轮值机制，以避免功能修复积压影响迭代效率。

---

*报告生成时间：2026-07-04 | 数据来源：[nano coai/nanoclaw](https://github.com/nano coai/nanoclaw)*

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

好的，作为AI智能体与个人AI助手领域开源项目分析师，以下是根据您提供的NullClaw项目数据生成的日报。

---

# NullClaw 项目动态日报 | 2026年7月4日

## 1. 今日速览

- 项目在过去24小时内活跃度较低，核心开发工作（PR、版本发布）处于停滞状态。
- 社区侧有轻微动态，新增并活跃了1个关于Telegram频道空闲后无响应的Bug反馈。
- 当前项目的主要关注点集中在用户报告的稳定性问题上，而非新功能开发。
- 综合来看，项目维护节奏放缓，可能需要关注后台进程的健康度及社区反馈的响应效率。

## 2. 版本发布

今日无新版本发布。

## 3. 项目进展

过去24小时内，没有合并或关闭的Pull Requests。项目在功能开发或现有Bug修复方面没有可量化的推进。

## 4. 社区热点

- **Issue #972: [bug] telegram channel stop respond after some idle time** ([链接](nullclaw/nullclaw Issue #972))
  - **动态**：这是过去24小时内唯一活跃的Issue，由用户`i11010520`创建，于7月3日被更新，目前有1条评论。
  - **分析**：该问题报告了Telegram频道在空闲一段时间（例如过夜）后“死亡”且无响应的现象。关键信息在于，用户指出后端`nullclaw`本身的运行似乎正常（执行`nullclaw agent -m "ping"`有效）。这强烈暗示问题出在**telegram bot的长连接或代理会话保持机制**上，而非核心agent或记忆系统。这是个人AI助手类项目常见的运维痛点，涉及心跳保活、连接池管理等底层网络逻辑。

## 5. Bug 与稳定性

- **[严重] Issue #972: Telegram频道空闲后无响应**
  - **描述**：Telegram bot在长时间空闲后彻底无响应，但后端服务状态正常。
  - **影响**：直接影响用户通过Telegram渠道与AI助手交互的连续性，属于体验下降的严重问题。
  - **严重性**：高。该问题影响了主要交互入口的可靠性。
  - **状态**：`OPEN`，目前尚未关联相关的fix PR。

## 6. 功能请求与路线图信号

今日无新增功能请求。当前所有信号均指向**连接稳定性的修复**，这可能成为下一版本优先解决的稳定性补丁方向，而非新增功能。

## 7. 用户反馈摘要

- **用户痛点**：`i11010520`在Issue #972中的反馈清晰揭示了用户面临的一个核心痛点：**“不可预测的空闲超时导致服务不可用”**。用户期望AI助手能够全天候稳定值守，而非需要用户定期“唤醒”。
- **使用场景**：用户显然将NullClaw部署在类似EC2的云端实例上，作为常驻后台服务运行。其对`nullclaw agent -m "ping"`命令的熟悉使用也表明用户具备一定的技术背景。
- **满意点**：用户明确指出“It seems `nullclaw` work well at backend”，表达了对项目核心引擎（包括记忆体、混合检索等）的肯定。这为维护者提供了宝贵信息：核心功能可靠，问题很可能出在特定的网络外设模块（Telegram adapter）上。

## 8. 待处理积压

- **Issue #972: Telegram频道空闲后无响应** ([链接](nullclaw/nullclaw Issue #972))
  - **状态**：`OPEN`，已有1条评论，过去24小时内被更新，是当前最活跃且唯一的问题。
  - **建议**：这是目前最值得项目维护者优先响应的Issue。建议维护者：
    1. 在Issue中复现并确认问题，或询问更多日志细节（如Telegram库的日志、网络连接状态）。
    2. 检查Telegram客户端的重连逻辑、心跳间隔配置以及底层TCP长超时设置。
    3. 若能快速定位，应优先安排一个hotfix点版本。

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

好的，这是根据您提供的 IronClaw 项目 GitHub 数据生成的 2026-07-04 项目动态日报。

---

## IronClaw 项目动态日报 — 2026-07-04

### 1. 今日速览

今日 IronClaw 项目社区活跃度极高。过去24小时内，有 **33 个 Issue 更新**，**50 个 PR 更新**，表明开发与协作非常密集。项目重心集中在 **Reborn 架构的深度打磨**上：一方面大量合并关于身份验证、入口路由、代码清理的 PR（如 #5619、#5625、#5626），另一方面也暴露出多个由审计和QA发现的严重 Bug（如 #5614、#5615、#5605）。此外，CI 状态不健康（#5603、#5590）以及 Slack 集成功能存在缺陷（#5522、#5602）是当前影响用户体验和开发效率的主要问题。

### 2. 版本发布

*   **无**

### 3. 项目进展

今日项目在 **Reborn 核心功能的完善与清理** 上取得了显著进展，多个关键 PR 被合并：

*   **Reborn 身份层重写与安全修复 (PR #5619)**: 由 `ilblackdragon` 合并的 PR，针对 `ironclaw_reborn_identity` 进行了全面重构。该 PR 拆除了过时的类型、强制执行边界规则、完善了合约，并加入了错误路径测试，大幅提升了身份模块的健壮性。此 PR 还包含数据库迁移。
*   **Reborn 组合架构内部重构 (PR #5585)**: 由 `serrrfirat` 合并的 PR，将 Reborn 组合层的内部代码按模块（如 `observability/`, `budget/`）进行了更清晰的划分，提高了代码的可维护性。
*   **采用清单驱动的 Slack 入口路由 (PR #5625 & #5626)**: 由 `ilblackdragon` 先后合并的 PR。PR #5625 建立了清单（manifest）驱动的宿主入口路由和凭证一致性检查的基础。PR #5626 则在此基础上，将 Slack 的入口路由完全从 Rust 代码中解耦，改为从扩展清单（manifest）中声明式定义，是向更灵活、数据驱动的平台架构迈进的重要一步。
*   **WASM egress 凭证修复 (PR #5623)**: 由 `serrrfirat` 合并的 PR，修复了 WASM 环境中凭证注入的逻辑，使其不再直接从清单中重新推导，而是尊重授权器的 `Decision.obligations`，解决了潜伏已久的安全隐患（对应 Issue #5512）。
*   **类型/特征清理 (PR #5567)**: 由 `serrrfirat` 合并的 PR，执行了代码复杂度审计的清理积压任务，移除了6个冗余特征，统一了6个DTO集群，净减少176行代码。
*   **其他重要合并**:
    *   **Reborn #3231 后续 (PR #5624)**: 提取了主机运行时测试工具。
    *   **Bedrock 支持 (PR #5059)**: 令 `ironclaw-reborn` 二进制文件支持 AWS Bedrock。
    *   **Sidebar UI 修复 (PR #5130)**: 修复了 WebUI v2 侧边栏高亮不在聊天页面时依然存在的问题。

总的来说，项目在本日显著地提升了 **Reborn 核心架构的纯度**、**安全性** 和 **可扩展性**。

### 4. 社区热点

今日最受关注的话题集中于对 Reborn 身份层（Identity Layer）的审计结果上。`ilblackdragon` 在6小时内提交了多个高度相关的 Issue（#5614, #5615, #5616, #5617, #5618），并在随后的 PR #5619 中进行了修复。这些议题引发了大量讨论：

1.  **身份层安全缺陷**:
    *   **Issue #5614**: [关键] `resolve_or_create` 中的电子邮件索引写入和 CAS 操作之间存在进程本地锁边界，可能导致跨进程的邮件冲突，分裂用户身份。
    *   **Issue #5615**: [高] `bind()` 函数缺少对 OAuth 表面的防护，在 `SurfaceKind::ChannelActor` 上会失败。
    *   **Issue #5616**: [中] `adopt_migrated_identity` 函数存在两个严重缺陷：从未写入用户记录和操作顺序错误。

2.  **工具调用/恢复逻辑缺陷**:
    *   **Issue #5583**: 当模型调用一个被禁用的能力（如 `spawn_subagent`）时，网关以 `model_error` 终止运行，而不是给出模型可见的拒绝回复，破坏了用户体验。
    *   **Issue #5608**: 本地开发用的合成能力的重试路径是死代码，因为 `input_ref` 校验失败，导致重试合约无效。

3.  **CI 持续红色**:
    *   **Issue #5603**: `main` 分支的 Docker 构建和 Clippy 检查因 “engine-v2” 移除后的遗留问题而失败。
    *   **Issue #5590**: 存在多个确定性代码/测试失败，导致 `main` 分支的多项 CI 检查不通过。

### 5. Bug 与稳定性

今日报告的 Bug 集中在 Reborn 的 **身份系统**、**工具调用失败恢复** 和 **用户界面** 上。

*   **严重**:
    *   **Issue #5614**: [高] 用户身份因邮件冲突可能分裂。
    *   **Issue #5615**: [高] 身份绑定缺少 OAuth 防护。
    *   **Issue #5583**: [高] 禁用能力调用失败的错误处理不当。
    *   **Issue #5603**: [高] CI 红色，阻碍所有后续合并。
    *   **Issue #5605**: [高] Reborn 内存上下文注入机制在正式环境中是死代码。

*   **中等**:
    *   **Issue #5608**: [中] 本地开发工具的重试路径不可达。
    *   **Issue #5604**: [中] Slack OAuth 设置流程变更，去除旧的配对流程。
    *   **Issue #5512**: [中] WASM 凭证注入忽视授权器决策。
    *   **Issue #5616 / #5617 / #5618**: 均被标记为中等风险的 identity 相关缺陷。

*   **已修复或已有修复 PR**:
    *   **Issue #5510 / #5507**: 用户反馈的无法删除旧 Routine 和日志不可见问题，暂无对应 PR。
    *   **PR #5623**: 修复了 Issue #5512 中报告的凭证问题。
    *   **PR #5625 / #5626**: 修复了入口路由设计，部分解决了旧 Slack 集成的遗留问题。
    *   **PR #5619**: 修复了 #5614、#5615 等身份层问题。
    *   **PR #5604**: 正在处理 Slack 配对流程的移除。

### 6. 功能请求与路线图信号

*   **Reborn 架构深化**: Issue #5588 追踪了从 QA 工作中移除的正式功能修改，这些修改是生产就绪的必选项，可能在未来几个 PR 中出现。
*   **Slack 集成优化**: PR #5604 正在将 Slack 从旧的“配对码”模式迁移到基于 OAuth 的标准化设置，这表明团队正在重构扩展安装流程以提高其健壮性和用户体验。
*   **并行代码审查技能**: PR #5622 新增了一个“并行代码审查”技能，表明项目范围内正在开发更复杂的 AI 辅助开发工具。

### 7. 用户反馈摘要

*   **Slack 连接依然困惑**: 用户 `matiasbenary` 在 Issue #5602 中报告，尝试连接 Slack 时，AI 回复已连接，但实际并未完成。这表明 Slack 连接的用户体验仍然存在脱节，亟需修复。
*   **无法删除旧 Routine**: 用户 `joe-rlo` 在 Issue #5510 中报告，找不到任何方法来删除创建的旧例程（Routine），导致旧配置持续运行，影响新例程。这暴露了用户管理和清理功能上的缺失。
*   **Routine 失败调试困难**: 用户 `joe-rlo` 在 Issue #5507 中反映，当 Routine 运行失败时，UI 显示“未附加线程”，且无法查看具体会话日志，导致调试极其困难。这严重影响了开发和生产排查效率。
*   **QA 自动化测试发现生产问题**: Issue #5522 和 #5588 通过 QA 流程暴露了 Routine 在读取 Slack DM 时因缺少能力凭证而陷入重试循环，以及更广泛的生产行为缺陷，表明 QA 覆盖率正在逐步提升。

### 8. 待处理积压

*   **CI 不稳定**: Issue #5590 (主分支 CI 绿色) 和 #5603 (engine-v2 遗留问题) 是需要立即处理的最高优先级积压，它们阻塞了所有后续代码合并。
*   **Slack 配对流程移除**: Issue #5604 的 PR 虽然已开，但仍在审查中，其完成是解决 Slack 集成众多 Bug（#5602, #5522）的关键前提。
*   **Routine 管理**: Issue #5510 (无法删除例程) 和 #5507 (例程失败无法调试) 是直接影响用户的关键可用性问题，目前没有对应的 PR，需尽快分配资源。
*   **Reborn 功能补全**: Issue #5588 追踪的从 QA 工作中摘出的生产行为修复清单，需要团队在完成当前架构清理后，尽快回到这些功能的实现上。

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

好的，作为 LobsterAI 开源项目分析师，以下是基于 2026-07-03 至 2026-07-04 项目数据生成的日报。

---

# LobsterAI 项目动态日报 | 2026-07-04

## 1. 今日速览

LobsterAI 项目今日迎来了一次重要的版本发布 `2026.7.3`，并随之合并了大量高密度的 Pull Request (14 条)，显示出积极的开发节奏。核心开发方向集中在 **CoWork 协作模式的增强**（如新增 Goal 模式、优化 Prompt 工具栏、修复会话状态同步）以及 **用户体验的打磨**（修复 Mac 全屏黑屏、优化大会话渲染性能）。此外，项目清理了一个老旧 Issue，但仍有 2 个长期未合并的 PR 处于积压状态，需要维护者关注。总体而言，项目处于 **高活跃度、快速迭代** 的健康状态。

## 2. 版本发布

**LobsterAI 2026.7.3**
- **发布链接**: [LobsterAI 2026.7.3 Release](https://github.com/netease-youdao/LobsterAI/releases/tag/2026.7.3)
- **主要内容**:
    - **服务部署能力增强**: 新增了服务部署功能 (`feat: service deployment`)。
    - **CoWork 协作模式**: 引入了全新的 **智能体协作目标模式 (goal mode)**，允许用户为协作任务设定更明确的目标 (`feat(cowork): add goal mode`)。
    - **子智能体面板**: 为 CoWork 模式新增了子智能体 (subagent) 的视图制品面板，方便用户查看和管理各子任务产出 (`feat(cowork): add subagent artifact panel`)。
- **破坏性变更**: 无明确说明。
- **迁移注意事项**: 主要涉及新功能的引入，用户无需额外操作即可体验新特性。

## 3. 项目进展

今日合并了大量重要 PR，项目在多条技术线上取得了实质性进展。

- **CoWork 协作模式重大更新**: 这是今日的核心亮点，多个 PR 围绕此功能展开。
    - #2268: 修复了 CoWork 模式下添加菜单的宽度问题，使其恢复紧凑美观的布局。
    - #2267: **关键修复**: 同步了来自 OpenClaw 网关的频道会话模型覆盖，解决了模型切换后 IM/频道会话与实际生效模型不一致的问题，这是一个重要的状态同步 Bug 修复。
    - #2266: 修复了 CoWork 聊天错误时的上下文维护状态问题，防止了 UI 在异常后卡死在“上下文整理/压缩”状态。
    - #2242: 优化了 CoWork 详情的 Prompt 工具栏，使其在窄屏或侧边栏展开时能够自动紧凑排列。
    - #2262: 删除了 Goal 菜单中多余的占位符提示文字，使 UI 更简洁。
- **客户端稳定性与体验优化**:
    - #2246: **修复了 macOS 全屏下关闭应用导致黑屏的问题**，这是一个重要的平台兼容性问题修复。
    - #2247: 优化了 CoWork 中 `plan` 模式的恢复流程，通过延迟执行避免了与已中止任务的锁文件冲突。
    - #2264: 优化了大会话（如工具调用密集的聊天）的渲染性能，并将工具结果折叠后的截断阈值从 64K 优化到 16K，同时新增了会话诊断导出功能，方便用户排查问题。
- **UI/UX 打磨**:
    - #2269: 优化了“创建智能体”按钮和模型服务商禁用时的交互，增加了 Tooltip 和授权引导。
    - #2263: 对字体大小和设置界面进行了优化。
- **其它修复**:
    - #2261: 修复了子智能体面板的时间戳显示错误。
    - #2260: 修复了 OpenClaw 系统提示中任务工作目录与智能体工作空间的分离问题，提升了提示词的精确性。
    - #2265: 修复了部署弹窗的布局滚动问题，并优化了头部提示信息的展示时机。

**项目状态**: 经过此次密集合并，CoWork 功能的成熟度与稳定性得到显著提升，同时解决了多个平台和性能问题，项目整体向前迈进了坚实的一步。

## 4. 社区热点

今日没有特别高评论量或多反应的 Issue 或 PR，讨论主要集中在代码审查和合并流程中。这说明当前社区动态主要由开发团队主导，用户侧反馈相对平静。

## 5. Bug 与稳定性

今日修复了几个关键的 Bug，按重要程度排列如下：

| 严重程度 | Bug 描述 | 相关 Issue/PR | 是否有 Fix PR |
| :--- | :--- | :--- | :--- |
| **高** | macOS 全屏模式下关闭应用导致黑屏。 | #2246 | 已合并 |
| **高** | CoWork 聊天错误时，UI 可能卡死在“上下文整理”状态，无法响应。 | #2266 | 已合并 |
| **中** | IM/频道会话中的模型切换无法被应用内同步，导致显示和实际使用不一致。 | #2267 | 已合并 |
| **中** | 大型会话（Tool-heavy）渲染性能差，导致 UI 卡顿。 | #2264 | 已合并 |
| **低** | CoWork 子智能体面板的时间戳显示错误。 | #2261 | 已合并 |

## 6. 功能请求与路线图信号

- **新增功能明确**: 本次发布的 `2026.7.3` 版本及合并的 PR 已经清晰展现了路线图上的两个重要功能落地：
    - **CoWork 目标模式**: 该功能从 PR #2241 (未在本日报显示完整但已合并) 引入，表明 AI 智能体协作正从自由对话向任务导向型进化，这可能是项目长期“智能体工作流”规划的一部分。
    - **服务部署功能**: 标志着项目正在加强对智能体服务化、部署上线场景的支持。

- **潜在需求信号**:
    - 积压的 **PR #1353** (`Agent 技能选择器新增全选和清除功能`) 虽然已过时，但其背后是用户对大量技能进行批量管理的需求。考虑到项目在不断扩展 Agent 能力，该功能在未来版本被采纳的可能性 **高**。
    - 积压的 **PR #1464** (`IM 平台实例名称和凭证 ID 的重复校验`) 反映了多实例管理中的痛点，这是一个必要的易用性改进，未来被合并的可能性 **高**。

## 7. 用户反馈摘要

今日用户活跃度较低，主要反馈来源于已关闭的 Issue。

- **Issue #1422**: 用户反馈了 MCP 自定义页面中，服务名称过长时，删除弹框的显示问题。虽然该问题已被标记为已关闭，但其场景描述 (`服务名称较长时，删除弹框展示不友好`) 指向了 UI 对**长文本/特殊内容**的适配不足问题。这是一个常见的 UI 缺陷，开发团队在后续 UI 审查中应持续关注。

## 8. 待处理积压

项目当前有 2 个处于 `[stale]` 状态的 PR，长期未获得代码审查和合并，请维护者关注。

- **PR #1353**: `feat(agent): Agent 技能选择器新增全选和清除功能`
    - **作者**: fhraiwxr
    - **摘要**: 为 Agent 技能选择器提供全选和清除功能，并显示已选计数，提升大量技能选择场景下的用户体验。
    - **链接**: [PR #1353](https://github.com/netease-youdao/LobsterAI/pull/1353)
    - **建议**: 该 PR 虽已过时，可能存在代码冲突，但其功能价值明确。建议项目组评估是否值得在最新代码基础上以此思路进行重构合并，以提升 Agent 配置的易用性。

- **PR #1464**: `fix(im): add duplicate validation for instance name and credential ID`
    - **作者**: gongzhi-netease
    - **摘要**: 为钉钉、飞书、QQ 的 IM 多实例配置增加名称和凭证 ID 的重复校验，防止用户创建混乱或冲突的配置。
    - **链接**: [PR #1464](https://github.com/netease-youdao/LobsterAI/pull/1464)
    - **建议**: 这是一个基础的防错 (foolproof) 功能，对提升产品健壮性和用户体验有直接帮助。建议尽快审查并合并。

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyagi">TinyAGI/tinyagi</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

好的，这是为您生成的 CoPaw 项目动态日报。

---

# CoPaw 项目动态日报 — 2026-07-04

## 1. 今日速览

过去24小时内，CoPaw 社区保持了高活跃度。项目共处理了 **39 条 Issue** 和 **33 条 PR**，关闭/合并数量占比较高，体现了维护团队对社区反馈的积极响应。最值得关注的是，多个针对 **QwenPaw Runtime 2.0 版本**的 Bug 报告（如上下文管理、工具调用错误）和修复 PR 被提交，表明社区已开始对 Beta 版进行深度测试并反馈关键性问题。同时，一个关于“密钥安全”的功能提案获得了社区广泛讨论，反映出企业级安全需求正成为用户关注的重点。总体来看，项目正处于 **健康、活跃的迭代阶段**。

## 2. 版本发布

无

## 3. 项目进展

过去一天内，项目在记忆系统、平台兼容性和功能修复方面取得了显著进展：

- **记忆系统增强**: PR [#5648](https://github.com/agentscope-ai/QwenPaw/pull/5648) (已合并) 为记忆搜索引入了可配置的 Reranker (重排序器)，能够通过外部 API 对混合搜索结果进行重排序，提升记忆检索的精准度。配套的 PR [#5647](https://github.com/agentscope-ai/QwenPaw/pull/5647) (已合并) 则在控制台 UI 中添加了对应的配置面板，使用户可以方便地开启/关闭并配置该功能。这是对记忆系统可用性的重要提升。
- **平台兼容性修复**:
    - **Windows 原生沙盒**: PR [#5525](https://github.com/agentscope-ai/QwenPaw/pull/5525) (已合并) 来自首次贡献者，实现了 Windows 环境下的原生沙盒支持，解决了 Windows 用户在代码执行隔离方面的痛点。
    - **GitHub Models 提供商更新**: PR [#5735](https://github.com/agentscope-ai/QwenPaw/pull/5735) (已合并) 将 GitHub Models 的集成更新至新的官方端点，并支持了细粒度的个人访问令牌（PAT），保证了该服务提供商的持续可用性。
- **核心功能修复**:
    - **策略持久化修复**: PR [#5506](https://github.com/agentscope-ai/QwenPaw/pull/5506) (已合并) 修复了 2.0 版本中前端策略修改后未同步到 `policy.yaml` 文件的问题，以及当 `execution_level` 配置为 `off` 时审批逻辑的 Bug。
    - **容错能力提升**: PR [#5755](https://github.com/agentscope-ai/QwenPaw/pull/5755) (已合并) 增强了系统对无效 MCP 客户端配置的容错能力，单个客户端的配置错误不再会导致整个 Agent 配置加载失败。PR [#5764](https://github.com/agentscope-ai/QwenPaw/pull/5764) (已合并) 则为请求增加了超时、重试和 AbortSignal 的支持，提升了网络请求的健壮性。
- **开发者体验**: PR [#5754](https://github.com/agentscope-ai/QwenPaw/pull/5754) (已合并) 对前端 Session 项组件进行了统一重构，提升了代码质量和可维护性。

## 4. 社区热点

-   **【安全】** **[Feature] 密钥脱敏与安全存储** (`#5705`)
    - **链接**: [Issue #5705](https://github.com/agentscope-ai/QwenPaw/issues/5705)
    - **热点诉求**: 社区成员 `wjt0321` 提交了一份非常详尽的功能请求，系统性地分析了当前版本在密钥安全方面的不足，包括环境变量回退覆盖不全、日志中存在密钥泄漏风险等，并提出了一套完整的改进方案。
    - **社区信号**: 该 Issue 获得6条评论，显示出社区对于安全性和企业级应用的强烈诉求。此类全面的分析报告对项目安全性的提升具有极高价值。

-   **【质量】** **[Bug] 2.0 beta：scroll 上下文压缩可能错误折叠当前任务** (`#5746`)
    - **链接**: [Issue #5746](https://github.com/agentscope-ai/QwenPaw/issues/5746)
    - **热点诉求**: 用户 `biaobiaobiao108` 详细报告了在 2.0 Beta 版中，使用 `scroll` 策略进行上下文压缩时，可能导致当前正在执行的任务（如 `/heartbeat` 的复杂链式调用）上下文被错误截断，模型最终“失忆”并回复旧消息。
    - **社区信号**: 该问题指向了 2.0 核心架构中一个严重的稳定性隐患。巧合的是，PR [#5765](https://github.com/agentscope-ai/QwenPaw/pull/5765) 恰好被提交以修复此问题，体现了敏锐的社区反馈与快速的开发者响应。

## 5. Bug 与稳定性

| 严重程度 | 问题 | Issue/PR 链接 | 状态 |
| :--- | :--- | :--- | :--- |
| **严重** | **Runtime 2.0 上下文压缩可能错误折叠当前任务** | [#5746](https://github.com/agentscope-ai/QwenPaw/issues/5746) | 已提交修复 PR [#5765](https://github.com/agentscope-ai/QwenPaw/pull/5765) |
| **严重** | **Runtime 2.0 畸形 tool-call 历史导致工具被重复调度** | [#5717](https://github.com/agentscope-ai/QwenPaw/issues/5717) | 已提交修复 PR [#5761](https://github.com/agentscope-ai/QwenPaw/pull/5761) |
| **严重** | **Console 前端因 /api 前缀重复导致 404** | [#5769](https://github.com/agentscope-ai/QwenPaw/issues/5769) | 待处理 |
| **中等** | **计划模式下反复读取同一文件，造成性能浪费** | [#5759](https://github.com/agentscope-ai/QwenPaw/issues/5759) | 待处理 |
| **中等** | **自动化任务无故中断** | [#5616](https://github.com/agentscope-ai/QwenPaw/issues/5616), [#5763](https://github.com/agentscope-ai/QwenPaw/issues/5763) | 待处理（报告者未提供详细复现步骤） |

## 6. 功能请求与路线图信号

-   **安全与密钥管理**: Issue [#5705](https://github.com/agentscope-ai/QwenPaw/issues/5705) 中提出的密钥脱敏与安全存储方案，由于其系统性和紧迫性，极有可能会被纳入下一版本的开发计划。
-   **自定义模型协议**: Issue [#5609](https://github.com/agentscope-ai/QwenPaw/issues/5609) 提出希望支持非标准 OpenAI-compatible 的 API 端点（如图片生成API），这表明用户有连接更广泛模型生态的需求。这可能需要对现有模型接入层进行扩展。
-   **插件机制增强**: Issue [#4613](https://github.com/agentscope-ai/QwenPaw/issues/4613) 和 [#4642](https://github.com/agentscope-ai/QwenPaw/issues/4642) 均指向了插件系统的扩展性不足，特别是缺乏`Agent Hook`等事件回调机制。这被视为项目未来的重要演进方向。

## 7. 用户反馈摘要

-   **痛点**:
    - **稳定性问题**: 用户反复抱怨自动化任务在执行过程中出现**无故中断、卡死**的现象 (`#5616`, `#5763`)。这是一个严重影响用户信任的稳定问题。
    - **上下文丢失**: 多位用户（`#5746`, `#5710`）报告了因上下文管理策略（如压缩）导致模型“失忆”，这损害了复杂任务的连续性和可靠性。
    - **Windows GBK 编码**: 尽管有零散修复，但 Windows 用户在中文环境下仍频繁遭遇 GBK 编码错误 (`#4481`)，影响基础使用。
-   **期望**:
    - **企业级特性**: 用户强烈要求更多安全和企业级特性，如**密钥脱敏**、**工作目录**、**多会话管理**等 (`#5705`, `#4642`)。
    - **更好的桌面体验**: macOS 用户期望窗口关闭后能后台运行并**恢复对话上下文** (`#4672`)。Wayland 用户则反馈宠物功能不兼容 (`#5183`)。
    - **更大的模型兼容性**: 用户希望插件能获取到当前会话信息 (`#5547`)，并支持更多非标准 API 的模型 (`#5609`)。

## 8. 待处理积压

-   **Windows GBK 编码问题** (`#4481`): 这是一个长期未彻底解决的系统性问题。虽然已合并了一些零散修复，但评论区有用户提出了从系统级解决的方案（如替换打印函数），但该 Issue 已于昨日关闭。建议维护者评估是否需要重新开启或另建 Issue 来跟踪一个根本性的解决方案。
-   **Console 前端 404 问题** (`#5769`): 这是 2.0.0b2 的一个明显且影响体验的 Bug，导致控制台部分功能不可用。目前尚无关联 PR。
-   **自动化任务无故中断** (`#5616`, `#5763`): 这两个问题缺乏详细日志和复现步骤，维护者需要引导用户提供更多信息以便排查。

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

过去24小时无活动。

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

好的，作为 AI 智能体与个人 AI 助手领域开源项目分析师，这是根据您提供的 GitHub 数据，为 ZeroClaw 项目生成的 2026-07-04 项目动态日报。

---

# ZeroClaw 项目动态日报 | 2026-07-04

## 1. 今日速览

ZeroClaw 项目在 2026-07-04 表现出极高的社区活跃度。过去 24 小时内，项目共处理了 36 条 Issue 和 50 条 PR，这表明开发者和用户都在积极参与。尽管没有新版本发布（无新 Release），但大量待合并的 PR（44 条）预示着下一轮功能发布可能即将到来。社区关注点主要集中在 **安全问题加固 (OIDC、Zip-bomb)、运行时稳定性 (Windows 兼容性、OOM、SOP 引擎 Bug) 以及新功能引入 (插件系统、Goal 模式、SOP 可视化)** 上，项目整体处于快速迭代和功能扩展期。

## 2. 版本发布

无新版本发布。

## 3. 项目进展

以下是今日（自上次报告以来）被**合并或关闭**的关键 PR，它们推动了项目的具体进展：

- **修复 Windows 测试兼容性**：PR [#8524](https://github.com/zeroclaw-labs/zeroclaw/pull/8524) 被合并，修复了在 OpenAI 兼容的 Provider 请求中，当 `tool_calls` 存在时发送空字符串 `content` 导致部分端点拒绝的问题，这是解决 Issue #7462 中提到的 Windows 测试失败的重要一步。
- **安全加固**：长期存在的 Issue [#8554](https://github.com/zeroclaw-labs/zeroclaw/issues/8554) 被关闭，该 Issue 报告了针对 Zip 炸弹的未防护风险。这表明团队已着手加强对技能包（Skill Zip）安装过程的安全性审查。
- **SOP 功能推进**：PR [#8679](https://github.com/zeroclaw-labs/zeroclaw/pull/8679) 被提交，补充了 SOP 的 TOML 配置参考和条件语法说明，完善了文档体系，使开发者能更容易地利用 SOP 功能。

**项目进展总结**：项目正稳步从“功能补全”向“生产环境稳定”和“安全性”迈进。虽然今日关闭/合并的 PR 数量不多（6 条），但 `[domain:security]` 标签的活跃度显示安全是当前阶段的核心焦点之一。同时，大量处于 `in-progress` 状态的 Issue 表明，多个并行的功能开发线（如插件系统、运行时执行、目标模式）正在高效推进。

## 4. 社区热点

- **Issue #6808**: [RFC: Work Lanes, Board Automation, and Label Cleanup](https://github.com/zeroclaw-labs/zeroclaw/issues/6808)
  - **评论数**: 13 (最高)
  - **热点分析**: 作为一项关于工作流、面板自动化和标签清理的治理型 RFC，该 Issue 已更新至第 9 版并处于“接受/滚动推出”状态。13 条评论表明社区对如何管理和优化项目内部工作流程，尤其是自动化和标签使用规范，有深入讨论。这通常反映了项目在达到一定规模后，对提升开发和维护效率的内在需求。

- **Issue #7462**: [[Bug]: 74 test failures on Windows](https://github.com/zeroclaw-labs/zeroclaw/issues/7462)
  - **评论数**: 8
  - **热点分析**: 该 Bug 报告了在 Windows 11 上 74 个测试失败的问题，CI 只覆盖了 Linux。8 条评论表明跨平台兼容性是社区用户的直接痛点。开发者正深入探讨路径语义、控制台编码等问题，PR #8524 的合并即是解决该问题的子集，表明这仍是社区高度关注的待办事项。

- **Issue #7141**: [RFC: OIDC authentication provider support](https://github.com/zeroclaw-labs/zeroclaw/issues/7141)
  - **评论数**: 7
  - **热点分析**: OIDC 认证支持的 RFC 获得了 7 条评论和 0 个👍，这表明社区对多用户、企业级的安全性有强烈诉求。用户希望原生支持 OIDC 提供者（如 Keycloak, Okta），以实现在多代理环境下的统一认证和权限管理。讨论聚焦于插件化认证架构，这将是走向企业级应用的基石。

## 5. Bug 与稳定性

按严重程度排列今日报告的 Bug：

- **S0 - 数据丢失/安全风险**: 无新增。
- **S1 - 工作流阻塞**:
  - **[Bug] MCP/tool-schema cloning drives unbounded RSS growth** ([#8642](https://github.com/zeroclaw-labs/zeroclaw/issues/8642)): 从 OOM 问题中拆解出的根因之一，MCP 工具 Schema 的克隆导致内存无限增长。严重程度高，**已有团队成员在跟踪**。
  - **[Bug] SOPs are not available to the agent through the web dashboard** ([#8563](https://github.com/zeroclaw-labs/zeroclaw/issues/8563)): 通过 Web 仪表盘配置的 SOP 无法被代理运行时检测。阻碍了 Web 用户使用 SOP 功能。
  - **[Bug] WhatsApp Web device linking broken** ([#8627](https://github.com/zeroclaw-labs/zeroclaw/issues/8627)): WhatsApp 频道因新的 Passkey/Companion linking 机制而无法连接。阻塞了该频道功能。
  - **[Bug] Source install with embedded-web fails** ([#8632](https://github.com/zeroclaw-labs/zeroclaw/issues/8632)): 源代码安装 `embedded-web` 功能时，因构建流程顺序问题导致编译失败。**已有 `in-progress` 标签**。
- **S2 - 行为降级**:
  - **[Bug] headless deterministic SOP steps recorded Completed without executing** ([#8631](https://github.com/zeroclaw-labs/zeroclaw/issues/8631)): 无头触发下的确定性 SOP 步骤未实际执行却被记录为已完成，导致审计跟踪失真。
  - **[Bug] skill-review fork panics** ([#8654](https://github.com/zeroclaw-labs/zeroclaw/issues/8654)): 技能审查分支在工具使用密集回合后因切片越界导致 `SIGSEGV` 崩溃。**已有对应 Fix PR [#8680](https://github.com/zeroclaw-labs/zeroclaw/pull/8680) 被提交**。
  - **[Bug] ZeroCode can complete a Code turn with no visible assistant output** ([#8644](https://github.com/zeroclaw-labs/zeroclaw/issues/8644)): ZeroCode 会话中，代码执行成功但无可见输出。
  - **[Bug]: advance_step has no run-status guard** ([#8678](https://github.com/zeroclaw-labs/zeroclaw/issues/8678)): SOP 引擎的步骤推进功能可以绕过审批门，存在审批完整性风险。
- **S3 - 小问题**:
  - **[Bug] ZeroCode transcript highlight does not dismiss on blank side clicks** ([#8652](https://github.com/zeroclaw-labs/zeroclaw/issues/8652)): ZeroCode 选中文本高亮后，无法通过点击空白区域取消。
  - **[Bug] ZeroCode code-block Copy includes Markdown fences** ([#8664](https://github.com/zeroclaw-labs/zeroclaw/issues/8664)): 复制代码块时会连带 Markdown 标记。

## 6. 功能请求与路线图信号

- **Goal Mode**：RFC [#8303](https://github.com/zeroclaw-labs/zeroclaw/issues/8303) 提出的“目标模式”收到了第一个 👍。对应的实现 PR [#8393](https://github.com/zeroclaw-labs/zeroclaw/pull/8393) 仍处于 `needs-author-action` 状态，但 `risk:high` 和 `size:XL` 标签表明此功能复杂且重要，是 v0.8.3 发行计划中的重点。
- **Cron Job `uses_memory` 标志**：用户多次提出在 CLI、工具和 Web UI 中暴露 cron job 的 `uses_memory` 标志 ([#8397](https://github.com/zeroclaw-labs/zeroclaw/issues/8397), [#8677](https://github.com/zeroclaw-labs/zeroclaw/issues/8677))。相应的实现 PR [#8676](https://github.com/zeroclaw-labs/zeroclaw/pull/8676) 已被打开，将纳入下个版本。
- **ZeroCode 增强**：用户提出了 ZeroCode TUI 的多个小功能请求，包括：**自动恢复最近的 Code 会话** ([#8653](https://github.com/zeroclaw-labs/zeroclaw/issues/8653)) 和 **接收并验证来自守护进程的完整 RPC 规范** ([#8626](https://github.com/zeroclaw-labs/zeroclaw/issues/8626))。这些表明 ZeroCode 的用户体验是迭代的重点。

## 7. 用户反馈摘要

从问题评论中提炼的真实用户痛点和使用场景：

- **跨平台体验痛点**：用户 `NiuBlibing` 报告了 Windows 上大量的测试失败，并详细指明了 Unix-only 命令、路径语义和终端编码是主要原因。这反映了项目在提供稳定 Windows 体验方面存在短板。
- **生产环境安全性需求**：用户 `singlerider` 和 `JordanTheJet` 分别提出了 OIDC 支持和增强权限模型 (Issue #8044) 的需求。这表明用户已开始将 ZeroClaw 用于或计划用于多用户、安全敏感的生产环境。
- **SOP 功能可用性**：用户 `susyabashti` 报告 SOP 在 Web 面板上不可用，而用户 `Stalesamy` 报告了 SOP 步骤的假完成问题。这反馈了 SOP 功能虽已推出，但在 **Web 集成**和**执行可靠性**上仍有待打磨。
- **性能与资源管理**：用户 `Themoonshinesontheriver` 的 OOM 问题 (Issue #5542) 被深入拆解，`JordanTheJet` 确认了 MCP Schema 克隆导致内存泄漏的新根因。这反馈了复杂插件和工具系统下的资源管理是当前运行时的关键挑战。

## 8. 待处理积压

- **Issue #7314**: [v0.8.3 WASM plugin program 追踪](https://github.com/zeroclaw-labs/zeroclaw/issues/7314): 这是一个长期存在的追踪 Issue，记录了 WASM 插件系统的整体进展。大量的相关 PR（如 [#8661](https://github.com/zeroclaw-labs/zeroclaw/pull/8661)）已经打开，但这个追踪 Issue 本身需要维护者定期更新状态，以向社区透明化进度。
- **Issue #8519**: [Reconcile cargo-audit ignores and remediate wasmtime-wasi CVEs](https://github.com/zeroclaw-labs/zeroclaw/issues/8519): 该 Issue 指出 CI 中存在 `cargo audit` 与 `cargo deny` 告警不一致的问题，并且需要修复 wasmtime-wasi 的 CVE。这属于长期未解决的安全技术债务，虽然已有 `in-progress` 标签，但未有关联的 Fix PR，建议维护者优先处理。

</details>

---
*本日报由 [agents-radar](https://github.com/leevaluder-maker/agents-radar) 自动生成。*