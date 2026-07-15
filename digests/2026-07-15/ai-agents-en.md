# OpenClaw Ecosystem Digest 2026-07-15

> Issues: 500 | PRs: 500 | Projects covered: 13 | Generated: 2026-07-15 01:26 UTC

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

## OpenClaw Deep Dive

Here is the OpenClaw project digest for **2026-07-15**.

---

## OpenClaw Project Digest: 2026-07-15

### 1. Today's Overview

The OpenClaw project is experiencing extremely high activity levels, with **500 issues** and **500 pull requests** updated in the last 24 hours. This surge is largely driven by a critical **release blocker** (`v2026.7.1`) that introduced fatal startup migration errors, causing gateway crash-loops for many users. While the community is actively contributing fixes, the project maintains a backlog of over **341 open issues**, with several high-severity (`P0`) reports currently awaiting maintainer review or product decisions. The maintainer team led by `steipete` is heavily engaged, pushing multiple CI improvements and fixes for the ongoing v2026.7.1 stability crisis.

### 2. Releases

**No new releases** were published today. The latest version remains `2026.7.1`, which is the subject of several critical bug reports regarding startup failures.

### 3. Project Progress

Despite the current instability, the community shipped a large volume of fixes today:
- **Closed/Merged PRs:** The dataset shows 163 PRs were closed or merged (from a total of 500 updated).
- **Key Fixes in Flight:**
    - **Startup Migration Fixes:** Multiple PRs targeting the `v2026.7.1` gateway crash-loop are open.
    - **Cron Tool Compatibility:** PR [#107605](https://github.com/openclaw/openclaw/pull/107605) fixes a critical regression where the `cron` tool's JSON Schema was incompatible with `llama.cpp`'s strict parser.
    - **UI Stability:** A large PR [#107893](https://github.com/openclaw/openclaw/pull/107893) addresses flickering and scroll-jumping in the Control UI chat transcripts.
    - **CI/DevOps:** PR [#107894](https://github.com/openclaw/openclaw/pull/107894) shortens the plugin prerelease critical path in CI to speed up validation.

### 4. Community Hot Topics

Three issues are dominating community attention, reflecting deep-seated stability and security concerns:

1.  **[Issue #75: Linux/Windows Clawdbot Apps](https://github.com/openclaw/openclaw/issues/75) (113 comments, 81 👍)**
    - **Topic:** Expanding platform support.
    - **Analysis:** This is the single most 'upvoted' and discussed issue. It signals a strong, unmet desire for native desktop clients beyond macOS. This is likely a long-term roadmap item but indicates a significant market gap.

2.  **[Issue #94518: DeepSeek Cache Hit Rate <10%](https://github.com/openclaw/openclaw/issues/94518) (10 👍)**
    - **Topic:** Performance regression, cost impact.
    - **Analysis:** A serious concern for users relying on DeepSeek models. The reported drop in cache hit rate (a 90%+ drop) directly increases API costs and latency for users. The community is highly reactive to this, and a fix is likely a high priority.

3.  **[Issue #92451: System Prompt Bloat](https://github.com/openclaw/openclaw/issues/92451) (Closed)**
    - **Topic:** Context window management.
    - **Analysis:** Although closed, this issue highlighted a systemic problem: the addition of ~20 new default tools in v2026.6.x caused context bloat, degrading performance on smaller models. This has likely informed the 'red flags' and 'safety' concerns seen in other issues.

### 5. Bugs & Stability

Stability is the primary concern. The release of `v2026.7.1` introduced several fatal, blocker-level bugs.

- **🛑 CRITICAL - Gateway Crash-Loops on v2026.7.1 (P0)**
    - **Problem:** Multiple users report permanent gateway startup failure due to legacy memory sidecar migration conflicts (embedding cache, metadata). The `openclaw doctor --fix` tool does not resolve the issue.
    - **Reports:** [#107227](https://github.com/openclaw/openclaw/issues/107227), [#107133](https://github.com/openclaw/openclaw/issues/107133) (Closed), [#107220](https://github.com/openclaw/openclaw/issues/107220).
    - **Impact:** Blocks all usage after upgrade. Fix PRs are in active review.

- **🔴 HIGH - Session Initialization & Delivery Failures**
    - **Problem:** Multi-channel regression where a second message in a session fails with a "reply session initialization conflicted" error. This is a cross-channel issue (Signal, Discord, Telegram).
    - **Report:** [#102020](https://github.com/openclaw/openclaw/issues/102020).
    - **Impact:** Breaks core conversational flow.

- **🔴 HIGH - llama.cpp Compatibility Regression**
    - **Problem:** The `cron` tool's JSON schema (`pattern: "\S"`) is incompatible with the strict `llama.cpp` parser, breaking tool use for local models. This is considered a regression in `v2026.7.1`.
    - **Report:** [#107449](https://github.com/openclaw/openclaw/issues/107449).
    - **Fix:** PR [#107605](https://github.com/openclaw/openclaw/pull/107605) is open to address this.

- **🟡 MEDIUM - CLI Startup Preflight Corrupts Database**
    - **Problem:** On macOS, running `openclaw` commands while the gateway is active can corrupt `openclaw.sqlite` with "database disk image is malformed" errors.
    - **Report:** [#101290](https://github.com/openclaw/openclaw/issues/101290).
    - **Impact:** Data loss potential. Marked as `impact:data-loss` with `maturity:stable`.

### 6. Feature Requests & Roadmap Signals

The requests reveal a strong focus on **security**, **multi-session architecture**, and **developer workflow**.

- **Likely in Next Version:**
    - **Memory Trust Tagging ([#7707](https://github.com/openclaw/openclaw/issues/7707)):** A high-security request to tag memory entries by trust level to prevent poisoning. This is a structured, well-defined feature request with strong security implications.
    - **Model Fallback on Context Overflow ([#9986](https://github.com/openclaw/openclaw/issues/9986)):** A pragmatic fix. The fallback system exists for API errors, so extending it to context-length errors is a logical next step.

- **Longer-term Roadmap Signals:**
    - **Multi-Session Architecture ([#48874](https://github.com/openclaw/openclaw/issues/48874)):** An RFC for a shared LLM layer with isolated sessions. This signals a move towards enterprise-grade multi-tenancy and resource management.
    - **Cross-Platform Desktop Apps ([#75](https://github.com/openclaw/openclaw/issues/75)):** As noted above, this is a massive feature signal.

### 7. User Feedback Summary

The overall sentiment is a mix of **high satisfaction with the project's ambition** and **significant frustration with recent stability**.

- **Pain Points:**
    - **Release Quality:** The `v2026.7.1` release is causing significant pain. Comments on issues like [#107227](https://github.com/openclaw/openclaw/issues/107227) and [#107133](https://github.com/openclaw/openclaw/issues/107133) reflect frustration with a "release that doesn't start."
    - **Configuration Complexity:** Users report that configuration changes (e.g., `config.apply`) trigger complex restart logic that leads to race conditions and data corruption ([#22676](https://github.com/openclaw/openclaw/issues/22676)).
    - **Unreliable Multi-Step Execution:** Reports of duplicate tool execution and session yield issues ([#90944](https://github.com/openclaw/openclaw/issues/90944)) suggest that complex agentic workflows are fragile.

- **Satisfaction:**
    - Users are actively contributing fixes, indicating a strong and technically capable community.
    - There is continued enthusiasm for the project's unique features, such as the `memory` system and voice-call integration.

### 8. Backlog Watch

Several critical issues are open and have not yet been addressed by maintainers, potentially blocking progress.

- **Issue #6615: Denylist for exec-approvals** (Created Feb 1, 2026)
    - **Status:** Stale, needs maintainer review.
    - **Why it matters:** This is a high-demand security feature (7 👍) that would allow users to "allow all except X" policies. The lack of movement suggests a design debate on how to implement it safely.

- **Issue #8409: Webhook Hook Sessions Reuse** (Created Feb 8, 2026)
    - **Status:** Stale, needs maintainer review.
    - **Why it matters:** A documented feature (`sessionKey` for multi-turn webhooks) does not work as described. This represents a broken promise in the public API documentation, eroding trust.

- **Issue #102749: Startup Migration Never Converges (v2026.7.1)** (Created Jul 9, 2026)
    - **Status:** Closed, but the linked PRs are still open.
    - **Why it matters:** This is the root cause issue for the `v2026.7.1` crash-loops. While closed, the underlying fix is still in progress, meaning the problem is not yet resolved.

---

## Cross-Ecosystem Comparison

Here is the cross-project comparison report based on the community digest summaries for 2026-07-15.

---

## Cross-Project Comparison Report: Personal AI Agent Open-Source Ecosystem

**Date:** 2026-07-15
**Analyst:** Senior Analyst, AI Agent & Assistant Ecosystem

---

### 1. Ecosystem Overview

The personal AI agent open-source ecosystem is characterized by extreme dynamism and a clear bifurcation between rapid feature iteration and reactive stabilization. The ecosystem is currently dominated by the fallout from major releases (particularly OpenClaw `v2026.7.1` and CoPaw `v2.0.0`), which have caused significant user-facing regressions across multiple projects. While core agent capabilities like tool use, memory, and multi-channel support are now table stakes, the community’s primary pain points are shifting towards **operational reliability**, **security hardening**, and **deployment flexibility**. A clear architecture divergence is emerging between monolithic, all-in-one platforms (e.g., OpenClaw, ZeroClaw) and lightweight, modular frameworks (e.g., NanoBot, Moltis), each serving different segments of the developer and user base.

### 2. Activity Comparison

| Project | Issues Updated (24h) | PRs Updated (24h) | Release Status (24h) | Health Score | Notes |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **OpenClaw** | 500 | 500 | Stalled (v2026.7.1 has critical bugs) | **Critical** | High activity driven by release crisis. |
| **ZeroClaw** | 29 | 50 | Preparing v0.8.4 (July 31 target) | **Stable/High** | Feature-completion phase, strong SOP progress. |
| **IronClaw** | 48 | 50 | Stalled (Release PR #5598 open 12 days) | **Unstable** | High activity, but CI is broken & major bugs persist. |
| **CoPaw** | 50 | 50 | Patch v2.0.0.post2 released | **Critical** | Release crisis, but rapid patching. |
| **NanoBot** | 13 | 65 | Stalled (v0.1.4.post6) | **Healthy** | High throughput, good merge rate, no crisis. |
| **Hermes Agent** | 50 | 50 | Stalled (v0.17.0, stabilization phase) | **Healthy** | Strong closure rate, no P1 bugs reported. |
| **NanoClaw** | 0 | 26 | Stalled | **Healthy** | Focused on bug fixing & security. |
| **PicoClaw** | 3 | 9 | Stalled (v0.3.1) | **Healthy** | Steady maintenance tempo. |
| **Moltis** | 3 | 12 | New (20260714.11) | **Healthy** | Healthy, iterative maintenance. |
| **LobsterAI** | 4 | 3 | Stalled (v2026.6.1) | **Low** | Low activity, mainly closing stale issues. |
| **NullClaw** | 0 | 0 | N/A | **Dormant** | No activity in 24h. |
| **TinyClaw** | 0 | 0 | N/A | **Dormant** | No activity in 24h. |
| **ZeptoClaw** | 0 | 0 | N/A | **Dormant** | No activity in 24h. |

**Health Scale: Dormant < Low < Stable/Unstable < Healthy < Critical**

### 3. OpenClaw's Position

- **Advantages vs. Peers:**
    - **Largest Community & Mindshare:** OpenClaw dwarfs all other projects in raw activity (500 issues/PRs in 24h) and community engagement. It has the most comprehensive ecosystem of channels, tools, and integrations.
    - **Innovation Driver:** It is the source of key architectural concepts (Memory Trust Tagging, Multi-Session Architecture, SOP engines) that other projects like CoPaw and ZeroClaw are adopting or adapting.
    - **Feature Breadth:** The project leads in advanced features like deep memory management, voice-call integration, and cron-based heartbeats.

- **Technical Approach Differences:**
    - OpenClaw follows a **“big tent” monolithic architecture**, aiming to be the single platform for all agent needs. This contrasts with **NanoBot’s modular plugin system** and **NanoClaw’s lightweight, poll-loop driven approach**. OpenClaw’s complexity leads to higher integration cost and cascading failure modes, as evidenced by the `v2026.7.1` crisis.

- **Community Size Comparison:**
    - **OpenClaw** is the clear leader, with a massive, engaged, and technically capable community that is actively contributing fixes. Its size is a double-edged sword: it provides immense pressure for rapid resolution, but also amplifies the impact of any release regressions.
    - **ZeroClaw** and **IronClaw** represent the next tier, with large, active communities focused on specific verticals (enterprise-grade SOPs and multi-user isolation for ZeroClaw; high-quality Slack integration for IronClaw).
    - Projects like **NanoBot**, **CoPaw**, and **Hermes Agent** have strong, but smaller and more focused communities.

### 4. Shared Technical Focus Areas

The following requirements are emerging independently across multiple projects, indicating deep industry needs.

| Shared Need | Projects Reporting | Specific Feedback |
| :--- | :--- | :--- |
| **Security & Multi-Tenancy** | OpenClaw, ZeroClaw, NanoBot, CoPaw | Need for per-sender RBAC (ZeroClaw, NanoBot), confused-deputy fixes (ZeroClaw), memory trust tagging (OpenClaw). |
| **Stability & Release Quality** | OpenClaw, IronClaw, CoPaw, ZeroClaw | Frustration with release regressions causing crash loops (OpenClaw, ZeroClaw), CI “noise not signal” (IronClaw), and broken upgrade paths (CoPaw). |
| **Message Delivery Reliability** | NanoBot, NanoClaw, IronClaw | Failures in heartbeat routing, outbound DB journal recovery, and delivery after container/poll restarts. |
| **Memory & Context Management** | OpenClaw, CoPaw, ZeroClaw | Need for reliable context compression, separated conversation vs. memory, and protection against context overflow. |
| **Model Compatibility & Provider Parity** | OpenClaw, NanoBot, PicoClaw, Moltis | Fixes for JSON schema parsing (llama.cpp/OpenClaw), tool argument coercion (Moltis), provider-specific model compatibility (PicoClaw/Bedrock). |

### 5. Differentiation Analysis

| Project | Target User | Key Differentiator | Architecture |
| :--- | :--- | :--- | :--- |
| **OpenClaw** | Power users & integrators | **Broadest ecosystem & features** (SOP, memory, voice, multi-channel) | Monolithic, single gateway |
| **ZeroClaw** | Enterprise / Ops teams | **Best-in-class SOP engine & multi-tenant security** | Modular, SOP-centric |
| **IronClaw** | Enterprise knowledge workers | **Deep Slack integration & workspace collaboration** | Heavy backend, rich Slack UI |
| **NanoBot** | Developers / Tinkerers | **Lightweight, modular, high configurable heartbeat/cron** | Plugin-based, poll-driven |
| **CoPaw** | General users | **Accessible desktop app & sandboxed execution** | Sandbox-first, desktop-focused |
| **NanoClaw** | Container-native operators | **Lightweight, secure, launchd/systemd aware** | Minimal, poll-loop, high security |
| **Hermes Agent** | Research / Agent devs | **Self-evolving skills & advanced agent loop** | Research-oriented, sweeper-assisted |
| **Moltis** | Multi-channel developers | **Easy channel integration & small model compatibility** | Modular channel adapters |
| **PicoClaw** | Chinese market / DingTalk | **Asian channel focus (Feishu, DingTalk) & security** | Channel-optimized, Security-focused |
| **LobsterAI** | Coworking teams | **AI-powered coworking & conversation sharing** | Coworking UI, upstream tracker |

### 6. Community Momentum & Maturity

- **Tier 1: High Momentum / Feature Expansion (Stable)**
    - **ZeroClaw**: Moving from feature completion to hardening. Strong roadmap execution.
    - **NanoBot**: Rapid, high-quality bug fixing and feature addition. Good merge/close ratio.
    - **Moltis**: Healthy, iterative maintenance. New release published.

- **Tier 2: Crisis Management / Rapid Iteration (Unstable)**
    - **OpenClaw**: Massive momentum but currently fighting a release fire. Recovery pace will depend on next patch.
    - **IronClaw**: High momentum but held back by broken CI and unresolved Slack lifecycle bugs. Release is blocked.
    - **CoPaw**: Aggressively patching a major release. Users are frustrated, but team responsiveness is high.

- **Tier 3: Stabilization & Maintenance**
    - **Hermes Agent**: Actively closing issues and preparing for next release cycle. No P1 bugs.
    - **NanoClaw**: Consolidating fixes and security hardening. Zero new issues.
    - **PicoClaw**: Steady, low-volume maintenance.

- **Tier 4: Dormant / Low Activity**
    - **LobsterAI, NullClaw, TinyClaw, ZeptoClaw**: Minimal or no development activity, indicating potential project abandonment or a lack of community interest.

### 7. Trend Signals

The community feedback across all active projects reveals several strong industry trends relevant to AI agent developers.

1.  **From “Can it work?” to “Does it work reliably?”:** The dominant theme is **operational excellence**. Users are past the point of being impressed by basic agent functionality. They are deeply frustrated by regressions that break their workflows (crash loops, broken message delivery, lost context). **Value for developers:** Prioritize integration testing, CI/CD pipeline health, and graceful upgrade paths over shipping new features.

2.  **Security is a prerequisite, not a feature:** The demand for **RBAC, multi-tenancy, structured authorization, and hardened sandboxes** signals a market shift from personal toys to team and enterprise tools. Projects ignoring this (like the unpatched confused-deputy issue in ZeroClaw) face a existential risk to their adoption. **Value for developers:** Invest in core security architecture from day one. A trusted agent is a used agent.

3.  **The Multi-Model, Multi-Provider Reality:** The constant stream of fixes for **provider-specific quirks** (llama.cpp JSON schemas, Bedrock parameter deprecation, Qwen thinking token leakage) underscores that no single model is the standard. Agents must be **provider-agnostic and resilient** to breaking API changes. **Value for developers:** Build abstraction layers for providers and model behavior. Tool calling can’t be hardcoded to one model’s output format.

4.  **The Rise of the Production Admin:** Features like **OpenTelemetry correlation**, **better error diagnostics**, **resource governors**, and **configurable heartbeat/cron systems** point to a new user persona: the **AI Agent Operator**. This person is not just a developer but a sysadmin who needs to manage, monitor, and troubleshoot agents in production. **Value for developers:** Build observability, health checks, and operational controls as first-class features, not afterthoughts.

5.  **Data Sovereignty & Local-First:** The desire for **local STT engines** (Moltis), **no-cloud memory** (ZeroClaw’s Hindsight), and **container-native isolation** (NanoClaw) shows a strong undercurrent of demand for privacy-preserving, self-hostable agents that can run in air-gapped or regulated environments. **Value for developers:** Offer self-contained deployment modes and local model runtimes as a competitive advantage.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

# NanoBot Project Digest — 2026-07-15

## Today's Overview

The NanoBot project remains highly active, with 65 pull requests updated in the last 24 hours — 47 merged or closed, reflecting strong momentum in both bug fixing and feature development. Issues activity is moderate (13 updated), with 10 resolved and 3 remaining open. No new releases were published today, but the repository shows sustained attention to stability, with several high-priority (P1) fixes merged for heartbeat routing, channel reconnection, and streaming timeout protections. Community contributors continue to drive meaningful improvements across channels, WebUI, and provider integrations.

## Releases

No new releases were published today. The last known stable version remains v0.1.4.post6. The project appears to be accumulating changes for a future release, given the volume of merged PRs and pending feature work.

## Project Progress

Today saw 47 merged or closed PRs, reflecting rapid progress across multiple areas:

- **Heartbeat System Fixes**: PR #4928 (open) restructures unified session heartbeat routing, persisting the last concrete `channel:chat_id` route. PR #4915 (merged) makes heartbeat response evaluation more configurable, addressing regressions from the migration to cron-based heartbeats.

- **Channel Improvements**: PR #4931 (merged) fixes restart completion delivery — the notice now waits until the target channel has entered its lifecycle. PR #4933 (merged) adds slash command and app mention highlighting in WebUI. PR #4930 (merged) adds a copy action for user messages. PR #4446 (open) gates private chats and adds sender mention in DingTalk.

- **WebUI & Developer Experience**: PR #4935 (open) validates inferred file paths before preview. PR #4927 (merged) fixes a broken `package-lock.json` that prevented Docker builds. PR #4932 (merged) standardizes `--config` help text across CLI commands.

- **Testing & CI**: PR #4936 (merged) speeds up CI by replacing duplicated OS/version cross-product tests with representative jobs, and hardens the test suite for WebSocket, MCP, and channel retry tests.

- **Provider/Codex**: PR #4929 (merged) improves Codex debugging by identifying which request stage (OAuth vs. API) fails.

## Community Hot Topics

The most active discussions today focus on infrastructure reliability and feature parity across platforms:

- **Issue #4924** (3 comments, open) — Heartbeat target selection failure with `unifiedSession: true`. A fix PR (#4928) is already open. The underlying need is reliable bot responsiveness when sessions are consolidated.

- **Issue #4637** (closed) — Telegram long message splits cause earlier trunks to fail rendering. This is a long-standing UX issue for users sending markdown-formatted content through Telegram, where message fragmentation breaks formatting.

- **Issue #4787** (1 comment, open) — Resource leak in `Session.messages` list, which grows unbounded for long-running sessions. The `FILE_MAX_MESSAGES=2000` setting only caps display, not storage. This is a potential memory/time leak that could affect production deployments, especially with unified sessions.

- **Issue #1445** (2 comments, closed, 2 👍) — Users want cron jobs to not send channel messages when nothing meaningful happened. This reflects a desire for quieter, more intelligent automation that only notifies on actual state changes.

- **Issue #1086** (closed, 4 👍) — WhatsApp Bridge WebSocket binding to 127.0.0.1 preventing inter-container communication. This multi-instance deployment pain point received strong community support, though it was closed without an explicit fix noted.

## Bugs & Stability

Several bugs were reported and addressed today, ranked by severity:

- **P1 — Heartbeat routing with unified sessions** (Issue #4924, open): `_pick_heartbeat_target_from_sessions` fails when sessions are absent but a unified session exists. Raised by community member `wzrayyy`. **Fix available**: PR #4928.

- **P1 — Streaming LLM timeout bypass** (Issue #4795, closed): Streaming calls set `outer_timeout_s = None`, allowing indefinite resource consumption. Addressed in a now-closed PR.

- **P1 — Qwen thinking content leakage** (Issue #4934, open, 0 comments): Models like `qwen3.6-flash` expose thinking/reasoning content in chat responses via DashScope. No fix PR yet.

- **P2 — Resource leak in Session.messages** (Issue #4787, open): Unbounded list growth for long-running sessions, especially unified sessions. No fix PR yet.

- **P2 — Telegram markdown reliability** (Issue #2568, closed): Intermittent markdown rendering failures after v0.1.4.post6. Closed but the root cause may not be fully resolved.

- **Windows UTF-16 corruption** (Issue #4881, closed): `ExecTool` decodes PowerShell output as UTF-8, corrupting UTF-16LE output. Fix merged.

## Feature Requests & Roadmap Signals

The project's roadmap appears to be shaped by several recurring themes:

- **Heartbeat & Cron Evolution**: Multiple PRs and issues (heartbeat trigger command PR #4620, model override PR #4549, cron job management PR #4218) suggest NanoBot is maturing its automation layer. The heartbeat system is being made more configurable and user-controllable, with dedicated model overrides and CLI trigger commands. This is likely a priority for the next release.

- **Channel Parity & Multi-Instance**: The DingTalk channel improvements (PR #4446) and the WhatsApp Bridge containerization issue (#1086) signal growing demand for first-class multi-instance and container-native support. The refactoring PR #4908 moves channel setup and instance ownership to the channels themselves, suggesting architectural groundwork for unified multi-channel support.

- **WebUI as Primary Interface**: Multiple WebUI enhancements landed today: file path validation, slash command highlighting, copy actions, and guided setup flows (the latter mentioned in a package-lock fix). This aligns with the cron management feature request (#4218) — the WebUI may soon become the preferred management interface.

- **One-Click Deployments**: PR #4937 (open) adds one-click "Deploy to Render" support via a Render Blueprint. This suggests the team is prioritizing easy onboarding and cloud deployment, which could attract new users.

## User Feedback Summary

Real user pain points and use cases visible in today's data:

- **"My Telegram bot's markdown stopped working intermittently"** (Issue #2568) — Users are frustrated by unreliable rendering that breaks their bot's output format, especially after an update. The inconsistency (sometimes works, sometimes not) is harder to debug than a total failure.

- **"I don't want a message every time a cron job runs — only when something meaningful happens"** (Issue #1445, 2 👍) — Users want intelligent notification suppression. A cron job that runs every 10 minutes but only sends a message on a mention match is a concrete use case for social media monitoring bots.

- **"My Qwen model leaks its thinking process into the chat"** (Issue #4934) — Exposing reasoning tokens in chat responses is a serious UX issue for production bots, especially when using "thinking" models. This suggests users are deploying advanced models and expect clean, assistant-only output.

- **"My bot's heartbeat stopped working after I enabled unifiedSession"** (Issue #4924) — Configuration complexity around unified sessions is causing operational failures. Users need clearer documentation or smarter defaults.

- **"My Docker containers can't talk to each other because the WhatsApp bridge binds to localhost"** (Issue #1086, 4 👍) — This was the most-liked issue, indicating strong demand for proper container networking support, likely from users running multi-service architectures.

## Backlog Watch

Several items require maintainer attention:

- **Issue #4787 — Resource leak in Session.messages** (open since July 6, 1 comment, no fix PR): This is a potential memory/time leak that could affect all long-running deployments. With unified sessions becoming more common, this should be prioritized. No assignee or milestone.

- **Issue #4934 — Qwen thinking content leakage** (open, 0 comments, no fix PR): A P1 bug with no engagement yet. Users deploying Qwen models via DashScope will encounter this immediately. Needs triage and a fix.

- **PR #4549 — Heartbeat model_override config** (open since June 26, conflict label): A community contribution with merge conflicts. The feature is valuable for operators wanting to route heartbeats to cheaper models, but it remains stalled.

- **PR #4689 — OAuth status and expiry warnings** (open since July 3, conflict label): A significant UX improvement for OAuth providers. Blocked by merge conflicts. This has P1 priority and would benefit from maintainer help to resolve conflicts.

- **PR #4621 — Archive facts with provenance context** (open since July 1, conflict label): Improves memory consolidation accuracy by including source-discipline rules. Blocked by conflicts — this could be a key quality-of-life improvement for users relying on long-term memory.

The number of open PRs with the "conflict" label suggests the project may benefit from a maintainer-led conflict resolution session to unblock community contributions.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

# Hermes Agent Project Digest
**Date:** 2026-07-15

---

## 1. Today's Overview

Hermes Agent shows **high maintenance activity** with 50 issues and 50 PRs updated in the last 24 hours, though only 7 issues remain open and 6 PRs were merged/closed—indicating a **strong closure rate** by maintainers. The project appears to be in a **stabilization phase** following the v0.17.0 release, with focus on bug fixes across desktop, gateway, and cron subsystems. No new releases were published today, but the backlog of 44 open PRs suggests an upcoming release cycle is being prepared. Community engagement remains healthy, with users reporting real-world pain points around deployment, configuration, and session state.

---

## 2. Releases

**No new releases** were published on or around July 15, 2026. The latest public release remains v0.17.0.

---

## 3. Project Progress

Today's merged/closed activity (6 PRs) and 43 closed issues reflect significant progress across several subsystems:

- **Desktop & TUI fixes:** Multiple bugs closed including session source misidentification (`#50932`), model picker persistence (`#50944`), and Chinese-language UI feedback (`#51273`, `#51320`)
- **Gateway & Telegram:** Fixed orphaned typing indicator (`#50991`) and multiplexer token leakage (`#51029`)
- **Cron subsystem:** Resolved dual-firing race condition (`#51329`) and false-positive threat scanner for auto-issue skills (`#50754`)
- **Security hardening:** Addressed credential exfiltration via `read_file` (`#50734`) and aggressive secret redaction in `write_file` (`#51141`)
- **Provider compatibility:** Fixed NVIDIA NIM `chat_template_kwargs` translation (`#50703`) and Z.AI endpoint caching (`#51229`)

Most fixes were tagged `sweeper:implemented-on-main`, indicating automated or maintainer-driven resolution.

---

## 4. Community Hot Topics

| Issue/PR | Comments | Description |
|---|---|---|
| [#50703](https://github.com/NousResearch/hermes-agent/issues/50703) | 8 | **NVIDIA NIM translation bug** — `extra_body` strips `chat_template_kwargs`, breaking thinking mode on M3 models. Closed. |
| [#59113](https://github.com/NousResearch/hermes-agent/issues/59113) | 3 (open) | **Dashboard broken in Docker** — only works with built-in auth, fails behind reverse proxy. 2 👍. No fix merged. |
| [#51288](https://github.com/NousResearch/hermes-agent/issues/51288) | 3 | **Feature request:** Configurable WebSocket timeout via env var. Closed "not-planned." |
| [#51229](https://github.com/NousResearch/hermes-agent/issues/51229) | 3 | **Z.AI endpoint caching** — startup probing on sensitive accounts. Closed. |
| [#50944](https://github.com/NousResearch/hermes-agent/issues/50944) | 3 | **Desktop model picker** persists wrong provider after config change. Closed. |

**Underlying needs:** Users are demanding **better deployment flexibility** (Docker, reverse proxy auth) and **configuration persistence** in the TUI/Desktop layer. The NVIDIA NIM issue (most commented) highlights friction when integrating with enterprise AI infrastructure.

---

## 5. Bugs & Stability

**High Priority (P2) Bugs Reported Today:**

| Issue | Component | Description |
|---|---|---|
| [#64674](https://github.com/NousResearch/hermes-agent/issues/64674) (OPEN) | Gateway/Telegram | **Telegram adapter fails** on default-profile gateway when multiplex profiles and bot token lives in secondary `.env`. Risk: session state & message delivery. |
| [#64457](https://github.com/NousResearch/hermes-agent/issues/64457) (CLOSED) | Desktop/Windows | **Windows 11 25H2 update** fails during dependency install, leaves incomplete Python venv. |
| [#59113](https://github.com/NousResearch/hermes-agent/issues/59113) (OPEN) | Dashboard/Docker | **Dashboard broken in Docker** without built-in auth — regression. 2 community upvotes. |

**Fix PRs in Flight for Related Issues:**
- [#64686](https://github.com/NousResearch/hermes-agent/pull/64686) (OPEN) — Preserve rate-limit failure metadata in gateway
- [#64687](https://github.com/NousResearch/hermes-agent/pull/64687) (OPEN) — Identity-safe memory mutations (Journey)
- [#64688](https://github.com/NousResearch/hermes-agent/pull/64688) (OPEN) — Stale verification after terminal mutations
- [#64685](https://github.com/NousResearch/hermes-agent/pull/64685) (OPEN) — Windows fflate import + RDP GPU fallback

**Notable:** No P1 (critical) bugs were reported today. The open P2 issues focus on **deployment infrastructure** rather than core agent logic, suggesting base agent stability is solid.

---

## 6. Feature Requests & Roadmap Signals

| Issue/PR | Type | Description | Likelihood |
|---|---|---|---|
| [#64684](https://github.com/NousResearch/hermes-agent/pull/64684) (OPEN) | PR | **OpenTelemetry OTLP trace export plugin** — adds observability with correlated spans. | **High** — bundled plugin approach matches Hermes architecture |
| [#63672](https://github.com/NousResearch/hermes-agent/pull/63672) (OPEN) | PR | **Auto-title API sessions** — parity with CLI/gateway for `/v1/chat/completions`. | **High** — port of existing feature |
| [#49368](https://github.com/NousResearch/hermes-agent/pull/49368) (OPEN) | PR | **Kanban review lifecycle** — `request_review` transition for workers. | **Medium** — niche SDLC use case |
| [#51288](https://github.com/NousResearch/hermes-agent/issues/51288) | Issue | **Configurable TUI WebSocket timeout** — rejected as "not-planned." | **Low** — maintainer declined |
| [#51175](https://github.com/NousResearch/hermes-agent/issues/51175) | Issue | **Provider-agnostic credit display** in Desktop — rejected "not-planned." | **Low** — maintainer declined |

**Prediction:** Next minor release will likely include the **OTel plugin**, **API auto-titling**, and accumulated bug fixes. The desktop tray PR (#64683) may also land for Windows/Linux users.

---

## 7. User Feedback Summary

**Real Pain Points:**
- **Deployment friction:** Docker users report dashboard broken behind reverse proxy (#59113, 2 👍). Telegram multiplex setups fail to start after `hermes update` (#64674).
- **Windows instability:** Desktop updates leave broken Python venvs (#64457). Pip upgrade fails due to locked `hermes.exe` (#51015). PTY disposal on crash incomplete (#48732).
- **Configuration leaks:** Model picker writes wrong provider to config (#50944). Title generation sends wrong model to fallback endpoint (#51278).
- **Session state fragility:** Context compressor can produce orphan tool calls causing API 400 errors (#51218). Chat text disappears on session reopen (#50713, #51320).

**Positive Signals:**
- Chinese-language users actively reporting and receiving fixes (#51273, #51320)
- Community member (#wuyoujushi) highlighted "Hermes agent's self-evolving skill capabilities" as a pain point, showing real engagement with advanced features
- Multiple users confirm Hermes as "日常高频使用" (daily high-frequency use)

**Satisfaction:** Users are **active and invested** but experiencing **stability regressions** in deployment scenarios, particularly Docker and multi-profile Telegram setups.

---

## 8. Backlog Watch

| Issue/PR | Age | Component | Needs |
|---|---|---|---|
| [#29552](https://github.com/NousResearch/hermes-agent/pull/29552) | 55 days (OPEN) | Feishu gateway | **Markdown table rendering fix** — stale PR, gather maintainer attention |
| [#41239](https://github.com/NousResearch/hermes-agent/pull/41239) | 38 days (OPEN) | MCP | **Historical event replay on startup** — re-verified, needs merge |
| [#48230](https://github.com/NousResearch/hermes-agent/pull/48230) | 27 days (OPEN) | Dashboard | **Canonical profile setup command** — no activity since June 18 |
| [#48231](https://github.com/NousResearch/hermes-agent/pull/48231) | 27 days (OPEN) | Browser tool (macOS) | **User-installed browser detection** — stale fix |
| [#59113](https://github.com/NousResearch/hermes-agent/issues/59113) | 10 days (OPEN) | Dashboard/Docker | **Dashboard broken** — 2 community upvotes, no fix merged yet |

**Most Critical:** The **Docker dashboard regression** (#59113) has community support and no active fix PR. The **Feishu Markdown PR** (#29552) has been open 55 days—likely blocked on maintainer bandwidth for Asian platform integrations. The **MCP historical event PR** (#41239) is a re-verified fix that should be fast-tracked to avoid further user-impacting state corruption.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

# PicoClaw Project Digest — 2026-07-15

## Today's Overview
The PicoClaw project shows moderate activity with 3 issues and 9 pull requests updated in the last 24 hours. No new releases were published today. The team is maintaining steady momentum, with 5 PRs merged or closed and 4 remaining open. The current issue backlog remains manageable, though one high-priority feature request has been open for over a month. Development focus appears split between provider integration improvements (Bedrock, Anthropic), channel-specific fixes (Feishu, DingTalk), and infrastructure enhancements (token usage tracking, prompt caching).

## Releases
No new releases were published today. The latest available version remains **0.3.1**.

## Project Progress
Five pull requests were merged or closed today, reflecting solid progress across multiple areas:

- **AWS Bedrock Model Compatibility** ([PR #2982](https://github.com/sipeed/picoclaw/pull/2982) — closed): Fixed a critical error where Claude Opus 4.8 on Bedrock failed due to the deprecated `temperature` parameter. The fix now drops temperature for models that no longer support it, ensuring forward compatibility.

- **Streaming Tool Calls** ([PR #2957](https://github.com/sipeed/picoclaw/pull/2957) — closed): Fixed a regression where `tool_calls` messages were incorrectly filtered out as auxiliary messages during streaming responses. The fix adds a helper function to exclude tool calls from filtering.

- **SecureString Reflection Panic** ([PR #2270](https://github.com/sipeed/picoclaw/pull/2270) — closed): Resolved a panic in `collectSensitive` when iterating over map values containing `SecureString` types. Go reflection was returning non-addressable values, and the fix now creates addressable copies when needed.

- **Tool Schema Validation** ([PR #2128](https://github.com/sipeed/picoclaw/pull/2128) — closed): Fixed tool schema validation errors with strict OpenAI-compatible APIs (e.g., LM Studio) by ensuring all tool parameters include a valid `properties` field in their JSON Schema.

- **Per-Turn Token Usage** ([PR #3156](https://github.com/sipeed/picoclaw/pull/3156) — closed): Added emission of per-turn LLM token usage on finalized messages over the Pico channel, enabling downstream consumers to track input/output token consumption per conversation.

## Community Hot Topics
- **#3088** — *[Feature] Use vodozemac instead of libolm* ([Issue](https://github.com/sipeed/picoclaw/issues/3088)): **Most active issue** with 8 comments and 2 thumbs-up. The community strongly supports migrating from the unmaintained `libolm` to `vodozemac`, the official replacement. This is marked **priority: high** with `help wanted`. Users want a compile-time optional migration path. Underlying need: security and maintainability of the encryption layer.

- **#3255** — *[BUG] DingTalk chat list preview shows fixed "PicoClaw"* ([Issue](https://github.com/sipeed/picoclaw/issues/3255)): New issue filed today with 0 comments yet. User reports that DingTalk channel chat list previews show a static "PicoClaw" instead of actual reply content.

- **#3163** — *feat(bedrock): leverage Converse prompt caching via cache points* ([PR](https://github.com/sipeed/picoclaw/pull/3163)): Open PR since June 23 with continued discussion. This would bring significant cost savings (~0.1× input writes) for AWS Bedrock users through explicit cache points in system, tools, and messages.

## Bugs & Stability
Three issues were updated in the last 24 hours, all open:

| Issue | Title | Severity | Status |
|-------|-------|----------|--------|
| [#3232](https://github.com/sipeed/picoclaw/issues/3232) | Rate limiting doesn't work if no fallback models configured | **Medium** | Open, 1 comment, stale tag |
| [#3255](https://github.com/sipeed/picoclaw/issues/3255) | DingTalk chat list preview shows fixed "PicoClaw" | **Low** | New (today), no fix PR yet |
| [#3088](https://github.com/sipeed/picoclaw/issues/3088) | Use vodozemac instead of libolm (security) | **High** | Open, 8 comments, no fix PR |

**#3232** is notable: users configuring only `agents.defaults.model_name` without fallback models find that rate limiting (RPM) configuration simply doesn't apply. This is a UX/reliability bug. **No fix PR exists yet.**

## Feature Requests & Roadmap Signals
- **Vodozemac Migration** ([#3088](https://github.com/sipeed/picoclaw/issues/3088)): The highest-priority feature request. Given its `help wanted` and `priority: high` labels, and the security implications of using unmaintained `libolm`, this is a strong candidate for the next minor release (0.4.0).

- **Bedrock Prompt Caching** ([PR #3163](https://github.com/sipeed/picoclaw/pull/3163)): If merged, this would be a significant cost-optimization feature for AWS Bedrock users, likely appearing in the next release.

- **Per-Turn Token Usage** ([PR #3156](https://github.com/sipeed/picoclaw/pull/3156)): Already merged today. This is now available for downstream consumers.

- **Feishu Audio/Video Native Messages** ([PR #3256](https://github.com/sipeed/picoclaw/pull/3256)): Open PR filed today to map audio and video uploads to native Feishu message types instead of generic file delivery.

## User Feedback Summary
- **Positive:** The fix for Bedrock Opus 4.8 compatibility ([PR #2982](https://github.com/sipeed/picoclaw/pull/2982)) addresses a clear user pain point — model upgrades breaking LLM calls. The streaming tool_calls fix ([PR #2957](https://github.com/sipeed/picoclaw/pull/2957)) resolves a regression that likely affected users with tool-using workflows.

- **Pain Points:** 
  - Encryption library ([#3088](https://github.com/sipeed/picoclaw/issues/3088)): Users are concerned about using unmaintained `libolm` and want the security of `vodozemac`.
  - Rate limiting ([#3232](https://github.com/sipeed/picoclaw/issues/3232)): Configuration misfire frustrates users who don't set fallback models.
  - DingTalk preview ([#3255](https://github.com/sipeed/picoclaw/issues/3255)): Even simple reply formatting breaks chat list UX.
  - Anthropic prompt caching ([PR #3228](https://github.com/sipeed/picoclaw/pull/3228)): Users can't express prompt caching on the Anthropic provider, causing 0% cache hit rates.

- **Satisfaction:** The closure of several long-standing PRs (some dating back to March-April 2026) suggests the team is clearing technical debt and improving stability.

## Backlog Watch
- **[#3088](https://github.com/sipeed/picoclaw/issues/3088)** — *vodozemac migration* (Created: 2026-06-09, 35+ days open): **High priority**, labeled `help wanted`. No assignee. With its security implications and community interest (8 comments, 2 reactions), this needs maintainer attention. If not picked up soon, the security exposure increases.

- **[#3232](https://github.com/sipeed/picoclaw/issues/3232)** — *Rate limiting without fallback models* (Created: 2026-07-07, 8 days open): Stale-labeled but only 1 comment. No PR exists. A relatively simple configuration bug that could be a quick win.

- **[#3233](https://github.com/sipeed/picoclaw/pull/3233)** — *Fix pr 3222 backward compat* (Created: 2026-07-07, 8 days open): Stale-labeled PR. Description is minimal and type of change is unchecked. May need maintainer to nudge author for clarity or take over.

- **[#2128](https://github.com/sipeed/picoclaw/pull/2128)** — *Tool schema validation fix* (Created: 2026-03-28): Closed today after ~109 days. While resolved, the long turnaround for a straightforward fix suggests review bottlenecks.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

# NanoClaw Project Digest — 2026-07-15

**Project:** NanoClaw (github.com/qwibitai/nanoclaw)  
**Date:** 2026-07-15  
**Analysis Window:** Last 24 hours

---

## 1. Today's Overview

NanoClaw shows **high development velocity** with **26 pull requests updated** in the last 24 hours (19 open, 7 merged/closed) — a very active day for a personal AI assistant framework. The project has **zero new open issues**, suggesting no new bugs or feature requests are being surfaced by the community, while the core team focuses on consolidating fixes and adding integrations. No new releases were published today, but the high PR throughput indicates a **release candidate may be approaching**. The activity is concentrated on **Slack and Telegram integration fixes**, **poll-loop reliability**, a **new Dial channel integration**, and **security hardening** — reflecting a maturing project that is operationalizing multi-channel agent support.

---

## 2. Releases

**No new releases today.**

The last release remains the version prior to 2026-07-15. Given the volume of merged fixes, particularly security fixes (#2800) and supply-chain hardening (#2973), a patch release is likely imminent.

---

## 3. Project Progress — Merged/Closed PRs Today

**7 PRs were merged or closed** in the last 24 hours:

| PR | Title | Type | Author |
|----|-------|------|--------|
| [#3042](https://github.com/nanocoai/nanoclaw/pull/3042) | feat(setup): offer Dial in channel picker + wizard, installer, skills, docs | Feature Skill | OmriBenShoham |
| [#3043](https://github.com/nanocoai/nanoclaw/pull/3043) | fix(skills): switch Telegram deep-link from t.me to telegram.me | Fix | amit-shafnir |
| [#2753](https://github.com/nanocoai/nanoclaw/pull/2753) | fix(hooks): pre-commit fell open when pnpm was missing from PATH | Fix | sturdy4days |
| [#2730](https://github.com/nanocoai/nanoclaw/pull/2730) | fix: NANOCLAW_* flags set in .env never reach process.env under launchd/systemd | Fix | sturdy4days |
| [#2729](https://github.com/nanocoai/nanoclaw/pull/2729) | docs(add-telegram): match pairing status-block names to the setup step; fix adapter pin | Docs | sturdy4days |
| [#2728](https://github.com/nanocoai/nanoclaw/pull/2728) | fix(telegram): create the wiring row when pairing with a wire-to intent | Fix | sturdy4days |

**Key feature advances:**
- **Dial channel integration** (#3042) — a full channel integration (setup wizard, installer, skills, documentation) for the Dial messaging platform. This is a significant addition to the channel ecosystem.
- **Telegram deep-link correction** (#3043) — switches from `t.me` to `telegram.me` domain, likely addressing reliability or regional access issues.

**Important infrastructure fixes:**
- **Environment flag loading** (#2730) — critical fix for launchd/systemd users: `NANOCLAW_*` flags in `.env` were never reaching `process.env`, meaning egress lockdown and other operational guards were silently disabled in production deployments.
- **Telegram wiring bug** (#2728) — pairing with `--intent wire-to:<folder>` was succeeding in status reporting but never creating the database row for message routing.
- **Pre-commit hook robustness** (#2753) — when `pnpm` wasn't in PATH, pre-commit hooks would fail open instead of gracefully skipping.

---

## 4. Community Hot Topics

**No issues or PRs have accumulated significant comment threads or reactions** in this window. All 26 PRs show `Comments: undefined` in the metadata, indicating either zero comments or the data source not tracking them. The project appears to maintain a **tight, core-team-driven workflow** with little community discussion on individual PRs.

**Most notable PRs by activity age and author attention:**

- **[#3050](https://github.com/nanocoai/nanoclaw/pull/3050)** — "feat(setup): add Dial to channel picker + wizard/skills" (OmriBenShoham) — opened same day as merged #3042, suggesting an updated/refined Dial integration after the initial merge.
- **[#3049](https://github.com/nanocoai/nanoclaw/pull/3049)** and **[#3048](https://github.com/nanocoai/nanoclaw/pull/3048)** — Two poll-loop fixes from joevandyk addressing message delivery reliability.
- **[#2801](https://github.com/nanocoai/nanoclaw/pull/2801)** — "fix(router): harden untrusted router input" — has been open since June 17, suggesting a complex change under review.

**Underlying need:** The sparseness of community discussion combined with high PR volume suggests NanoClaw is in a **polish and harden** phase after an initial feature push. Users are not filing many issues — either because stability is good, or because the user base is still small/early-adopter.

---

## 5. Bugs & Stability

**Critical — Fixed Today:**

| PR | Title | Severity | Status |
|----|-------|----------|--------|
| [#2730](https://github.com/nanocoai/nanoclaw/pull/2730) | NANOCLAW_* flags never reach process.env under launchd/systemd | **High** — Security configuration silently ignored | Merged |
| [#2728](https://github.com/nanocoai/nanoclaw/pull/2728) | Telegram wire-to pairing creates no database wiring row | **High** — Feature failing silently | Merged |

**Critical — Open Fixes (not yet merged):**

| PR | Title | Severity | Author |
|----|-------|----------|--------|
| [#2800](https://github.com/nanocoai/nanoclaw/pull/2800) | Validate group folders and forbid implicit image pulls | **High** — Security: unvalidated group folders could allow path traversal; implicit image pulls could download malicious containers | sturdy4days |
| [#2750](https://github.com/nanocoai/nanoclaw/pull/2750) | Recover stale outbound.db journals after container kills; classify hot-journal poll races | **High** — Data loss: messages written to outbound.db just before container kill can be lost for up to 60s | sturdy4days |
| [#3045](https://github.com/nanocoai/nanoclaw/pull/3045) | Drain outbound messages on container exit | **Medium** — In-flight message loss when container exits | blueye25 |
| [#3044](https://github.com/nanocoai/nanoclaw/pull/3044) | Download inbound attachments that lost fetchData (#2888) | **Medium** — Telegram voice/audio notes silently dropped; agents see filename/placeholder with no bytes | mashkovtsevlx |
| [#2899](https://github.com/nanocoai/nanoclaw/pull/2899) | Discord: strip newline suffix from custom_id before parsing Gateway interactions | **Medium** — All Discord DM approval-card button taps route to "reject" due to parsing error | rudgalvis |

**Poll-loop reliability cluster** — Three PRs (#3049, #3048, #3045) address different message delivery failure modes in the poll-loop system, suggesting this subsystem has been a source of user-facing reliability issues.

**Regression Risk:** The "NANOCLAW_ flags never reach process.env" fix (#2730) is a significant behavioral change — users whose deployments depended on the broken behavior (i.e., expecting flags in `.env` to work) may need to verify their setups after upgrading.

---

## 6. Feature Requests & Roadmap Signals

**No new feature requests (issues) were created** in the last 24 hours. Roadmap signals come entirely from **merged and proposed PRs**:

**Strong signals for near-term inclusion:**
- **Dial channel integration** (#3050, #3042) — The Dial messaging platform is being actively integrated. The PR #3050 (still open) refines the implementation from #3042 (already merged). **Likely in next release.**
- **Unified approval lifecycle** (#3040, open, `core-team` tagged) — A core-team PR to "unify approval holds behind one lifecycle contract." This is a significant architectural change suggesting the current approval system may have multiple divergent paths. **Could be a v-next major change.**
- **Minimum release age gate for supply chain** (#2973, open) — Activating a 3-day (4320 min) wait for dependency updates. **Security-focused, likely in next patch.**

**Longer-term signals:**
- The multiple outbound.db/delivery fixes suggest **improved delivery reliability** is a priority.
- The "safeParseContent" hardening (#2801) indicates the router is seeing untrusted input; this may lead to broader input validation patterns.

**Missing signals:** No user requests for new channels (beyond Dial), no agent-level features, no API or extensibility requests. The project appears **focused on operational reliability** over feature expansion.

---

## 7. User Feedback Summary

**No direct user feedback (issues, comments, reactions) captured in this window.**

**Inferred pain points from fix PRs:**

1. **Deployment confusion:** The `NANOCLAW_*` flags not loading under launchd/systemd (#2730) means users deploying with system-level process managers would have silently disabled security features. This likely caused confusion or security gaps for production deployments.

2. **Message loss/delays:** Multiple fixes targeting outbound message delivery (poll-loop truncation #3048, tool-call turn delivery #3049, container exit draining #3045) suggest users experienced unpredictable message delivery — messages appearing to be sent but not arriving, or arriving after significant delays.

3. **Telegram pairing reliability:** Both the wiring row bug (#2728) and the status-block documentation mismatch (#2729) indicate the Telegram setup flow has been a source of user friction. Users following the skill documentation would get apparent success but no actual message routing.

4. **Attachment handling gaps:** Voice/audio notes on Telegram (#3044) being silently dropped is a noticeable UX gap — users send a voice message, the agent receives nothing usable.

5. **Discord interaction failures:** All DM approval buttons routing to rejection (#2899) is a complete failure of a core workflow for Discord users.

**Satisfaction indicators:** Zero new issues and low comment volume could indicate either a small user base that is generally satisfied, or a user base that is engaged primarily through other channels (Discord, Telegram) rather than GitHub.

---

## 8. Backlog Watch

**Long-open important PRs needing attention:**

| PR | Title | Age | Risk |
|----|-------|-----|------|
| [#2800](https://github.com/nanocoai/nanoclaw/pull/2800) | fix(security): validate group folders and forbid implicit image pulls | **28 days** (since June 17) | High — Security vulnerability. Unvalidated group folder paths could enable path traversal; implicit container image pulls could be exploited to download malicious images. **Should be prioritized for next release.** |
| [#2801](https://github.com/nanocoai/nanoclaw/pull/2801) | fix(router): harden untrusted router input (safeParseContent + engage_pattern) | **28 days** (since June 17) | Medium — Parsing primitive JSON payloads returns non-objects, causing callers to silently get `undefined`. Could cause unpredictable behavior in agent responses. |
| [#2750](https://github.com/nanocoai/nanoclaw/pull/2750) | fix: recover stale outbound.db journals after container kills | **33 days** (since June 12) | High — Data loss risk for outbound messages. Two related failure modes (stale journals, poll races) addressed in one PR. |
| [#2973](https://github.com/nanocoai/nanoclaw/pull/2973) | fix(supply-chain): activate minimumReleaseAge gate | **8 days** (since July 7) | Medium — Supply chain security. Currently ineffective due to config placement. |
| [#2899](https://github.com/nanocoai/nanoclaw/pull/2899) | fix(discord): strip newline suffix from custom_id | **14 days** (since July 1) | Medium — All Discord DM approvals broken. |

**Observation:** Four out of five of these waiting PRs are authored by **sturdy4days**, who also authored three of today's merged fixes. This suggests a single core contributor with a large backlog of valuable work awaiting review/merge. The project may benefit from additional reviewers to unblock this critical path.

**No long-unanswered issues from users** — the issue tracker appears well-maintained, with the last 24 hours showing zero open issues.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

# IronClaw Project Digest — 2026-07-15

## Today's Overview
IronClaw has sustained a high-activity cadence over the past 24 hours, with **48 issues** and **50 pull requests** updated, including a strong 54% close/merge rate across both categories. The project is deeply engaged in resolving a backlog of bug-bash findings from recent QA waves, with notable focus on **Slack extension lifecycle correctness**, **chat message ordering**, and **CI signal reliability**. The release pipeline remains stalled — no new releases this period — despite a pending release PR (#5598) that has been open for 12 days. The team is also executing a major architectural uplift: two "Train" roll-up PRs for a unified extension runtime (Trains A and B) are now under review, signaling a significant internal refactor.

## Releases
*No new releases in the past 24 hours.*

**Pending:** Release PR [#5598](https://github.com/nearai/ironclaw/pull/5598) remains open after 12 days, proposing `ironclaw_common` 0.4.2 → 0.5.0 (with API-breaking changes), `ironclaw_skills` 0.3.0 → 0.4.0 (breaking), and `ironclaw` 0.24.0 → 0.29.1. No migration notes or user-facing changelog have been published.

## Project Progress
**27 PRs merged or closed in the last 24 hours** (24 hours). Key advances:

- **Chat message ordering fix**: PR [#6096](https://github.com/nearai/ironclaw/pull/6096) (merged) serializes concurrent inbound-message writes per thread, fixing issue [#6047](https://github.com/nearai/ironclaw/issues/6047) (out-of-order messages in quick succession). Includes a failing-then-passing test.
- **Active-hold trigger visibility**: PR [#6066](https://github.com/nearai/ironclaw/pull/6066) (merged) derives an `active_hold` projection so gate-parked automations are visible in the WebUI and to the agent.
- **Error message quality**: PR [#6095](https://github.com/nearai/ironclaw/pull/6095) (merged) improves Slack auth-unavailable error messages to name the blocked provider, and stops misclassifying I/O faults as invalid input.
- **Extension runtime — P7b finalize**: PR [#6065](https://github.com/nearai/ironclaw/pull/6065) (merged) consolidates package inventory and retires vocabulary — the final PR of the extension-runtime Train B.
- **Extension runtime — P7a wiring**: PR [#6056](https://github.com/nearai/ironclaw/pull/6056) (merged) wires state enums and adds accounts list plus deferred legs.
- **Resource governor recovery from libSQL contention**: PR [#6089](https://github.com/nearai/ironclaw/pull/6089) (merged) classifies SQLite/LibSQL `BUSY`/`LOCKED` and PostgreSQL contention as typed retryable errors.
- **Self-verification pass for agent loop**: PR [#6093](https://github.com/nearai/ironclaw/pull/6093) (merged) adds a gated self-verification pass and a `benchmark_default` profile to enable it without changing default behavior.
- **WebUI memory browse isolation**: PR [#5896](https://github.com/nearai/ironclaw/pull/5896) (merged) scopes the WebUI v2 memory browse mount per authenticated caller, with an E2E regression test.
- **Light theme and chat status fixes**: Three closed issues — [#6039](https://github.com/nearai/ironclaw/issues/6039) (unreadable button/status colors in light theme), [#6037](https://github.com/nearai/ironclaw/issues/6037) (hidden chat connection status), [#6028](https://github.com/nearai/ironclaw/issues/6028) (stray `$` in MCP tab heading).

## Community Hot Topics
The most active discussions centered on **Slack lifecycle bugs** and **CI reliability**:

- **[#6105](https://github.com/nearai/ironclaw/issues/6105) (Open, 1 comment)** — A formal proposal for an extension/channel lifecycle state-machine test. The author notes that Slack lifecycle bugs have regressed across **all four** QA bug-bash waves despite fixes in between, making this the #1 user-facing bug family. PR [#6110](https://github.com/nearai/ironclaw/pull/6110) (open) is the first deliverable — an integration-tier state-machine test for Slack.
- **[#5948](https://github.com/nearai/ironclaw/issues/5948) (Closed, 5 comments)** — The assistant falsely reports the GitHub extension as activated when it's only installed. This highlights a trust-damaging UX pattern: the agent claims capabilities it doesn't actually have.
- **[#6103](https://github.com/nearai/ironclaw/issues/6103) (Open)** — Blunt assessment that main-branch CI is "noise, not signal": ~70% of July pushes to main failed (139/200) from ~5 flaky tests. The author also reveals that `nightly-deep-ci.yml` had **zero successful runs from May 6 to July 8**. This is a project-health red flag.
- **[#6037](https://github.com/nearai/ironclaw/issues/6037) (Closed)** — Chat connection status being hidden during disconnect/reconnect was quickly fixed, indicating the team values real-time user feedback.
- **[#6099](https://github.com/nearai/ironclaw/issues/6099) (Open)** — `POST /llm/test-connection` reports `ok: true` for an unreachable endpoint with an invalid key, directly misleading users.

## Bugs & Stability

### Critical/P2
- **[Slack hangs after reconnect (#6092)](https://github.com/nearai/ironclaw/issues/6092)** — Conversations never leave the "thinking" state after reconnection. **No fix PR yet.**
- **[Slack conflicting connection states (#6091)](https://github.com/nearai/ironclaw/issues/6091)** — After disconnect, UI shows conflicting states; agent believes Slack is still usable. **No fix PR yet.**
- **[LLM test-connection always reports ok (#6099)](https://github.com/nearai/ironclaw/issues/6099)** — Misconfigures users silently. **No fix PR yet.**
- **[Routine loses credentials after external token revocation (#5884)](https://github.com/nearai/ironclaw/issues/5884)** — Credential loss goes undetected mid-execution. PR [#6095](https://github.com/nearai/ironclaw/pull/6095) (merged) improves error surfacing but does not fix the detection gap.

### Serious/P3
- **[Run fails with generic model error after multi-tool execution (#5945)](https://github.com/nearai/ironclaw/issues/5945)** — Long workflows produce unhelpful "model provider was unavailable" errors. Closed without a root-cause fix visible.
- **[Thread deletion requires UI refresh (#5947)](https://github.com/nearai/ironclaw/issues/5947)** — UX inconsistency, closed.
- **[Memories visible cross-user in workspace (#5460)](https://github.com/nearai/ironclaw/issues/5460)** — Security/privacy gap affecting Railway staging. Closed after 14 days.

### Pre-existing bugs surfaced during reviews
- **[One-shot context-window cache races with slow writes (#6100)](https://github.com/nearai/ironclaw/issues/6100)** — Found during review of the chat-ordering fix. Affects `filesystem_service.rs`.
- **[FilesystemSessionThreadService reconstruction safety (#6102)](https://github.com/nearai/ironclaw/issues/6102)** — High severity follow-up to the chat-ordering fix, concerning per-thread locks and in-flight calls.
- **[Extension catalog failures shown as empty state (#6087)](https://github.com/nearai/ironclaw/issues/6087)** — Network errors are indistinguishable from genuinely empty catalogs. Open.

## Feature Requests & Roadmap Signals

### Likely in next release
- **WebChat v2 model selection + per-run cost**: PR [#6111](https://github.com/nearai/ironclaw/pull/6111) (open, XL) brings model selection and usage/cost—already in the OpenAI-compat API—to the regular WebChat v2 API, including default-model pricing.
- **Slack lifecycle state-machine test**: PR [#6110](https://github.com/nearai/ironclaw/pull/6110) (open) is the testing infrastructure that will likely gate future Slack fixes.
- **MCP registration framework skeleton**: PR [#5970](https://github.com/nearai/ironclaw/pull/5970) (open) is plumbing for a future MCP extension registration feature.
- **Unified extension model — Trains A & B**: PRs [#6061](https://github.com/nearai/ironclaw/pull/6061) and [#6090](https://github.com/nearai/ironclaw/pull/6090) (both open, XL) are roll-ups of a major internal refactor. Their merge will likely precede the release.

### Requested but not yet implemented
- **[Error fidelity enforcement (#6108)](https://github.com/nearai/ironclaw/issues/6108)** — Proposes a rule that no failure can be swallowed, genericized, or misreported as success. Cross-cutting and would address a recurring bug family.
- **[Model-input compatibility corpus in CI (#6107)](https://github.com/nearai/ironclaw/issues/6107)** — Automatically replay real tool-call argument shapes against schemas to catch over-strict validation — a bug class that has recurred on four separate days.
- **[Release/staging gate with boot smoke and upgrade-path canary (#6106)](https://github.com/nearai/ironclaw/issues/6106)** — A direct response to [#5966](https://github.com/nearai/ironclaw/issues/5966) where a correct security fix crash-looped every hosted deployment with pre-fix state.
- **[Process SLA: 24h fix-or-wontfix on failure taxonomy candidates (#6104)](https://github.com/nearai/ironclaw/issues/6104)** — Data shows the same harness bugs recur across consecutive daily reports, with lifetimes of 4–5 days.

## User Feedback Summary
The dominant user pain points cluster around **integration reliability** and **error transparency**:

- **Slack lifecycle is broken**: Users experience "thinking" hangs after reconnection, conflicting connection states across UI surfaces, and credentials silently lost after token revocation. This is the most frequently reported bug family, with four QA waves failing to fully resolve it.
- **Misleading success signals**: The `test-connection` endpoint reports `ok: true` for invalid endpoints, and the agent falsely claims extensions are "activated" when they are only installed — both erode user trust in system diagnostics.
- **Message ordering breaks conversational flow**: Messages appearing out of order (both user messages and tool activity) has been reported twice ([#6047](https://github.com/nearai/ironclaw/issues/6047), [#5418](https://github.com/nearai/ironclaw/issues/5418)) and was closed after a fix on July 14.
- **Workflow failures are opaque**: Long-running workflows fail with generic "model provider unavailable" errors, and routine failures after credential revocation produce misleading "credentials required" messages.
- **UI polish issues**: Deleted threads remain visible, light theme has unreadable elements, chat reconnections are invisible, and stray `$` characters appear in headings — small issues that accumulate to a perception of unfinished UX.
- **CI unreliability as a project-health signal**: While not directly user-facing, the 70% main-branch CI failure rate and two-month nightly-CI outage suggest the team has been under sustained pressure to ship features and fixes without adequate test infrastructure.

## Backlog Watch

### Issues needing maintainer attention
- **[#5640](https://github.com/nearai/ironclaw/issues/5640) — Harness gap: no RecordingSecurityAuditSink double** (Closed, 2 comments) — Despite having 2 comments and being closed, this represents a long-standing wiring-parity gap between production and integration harness. The fix was not identified in this digest period.
- **[#3483](https://github.com/nearai/ironclaw/issues/3483) — Package ironclaw-reborn in release artifacts** (Closed, 1 comment, created May 11) — The standalone binary exists but release packaging is intentionally disabled. This has been dormant for 2+ months.
- **[#5460](https://github.com/nearai/ironclaw/issues/5460) — Memories visible cross-user in workspace** (Closed after 14 days) — A security/isolation issue that took two weeks to close; no visible root-cause fix in associated PRs.

### PRs needing review/decision
- **[#5598](https://github.com/nearai/ironclaw/pull/5598) — Release PR** (Open, 12 days) — The release PR has been sitting for 12 days with breaking changes in `ironclaw_common` and `ironclaw_skills`. This is blocking all downstream users from getting fixes and features.
- **[#5977](https://github.com/nearai/ironclaw/pull/5977) — Advertise Reborn skills as one-line listing** (Open, 4 days) — A token-efficiency improvement that reduces system prompt size by ~7K tokens/call, authored by a core contributor. May be waiting on the `cache-first-loop` base branch.
- **[#6098](https://github.com/nearai/ironclaw/pull/6098) — Windows filesystem fix** (Open) — Filed by a new contributor, fixes a bug that makes `ironclaw-reborn` completely non-functional on Windows. This is a low-risk, high-impact fix.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

# LobsterAI Project Digest — 2026-07-15

## Today's Overview
The project shows a low-activity day with all 4 updated issues closed and 3 PRs merged, indicating the maintainers are focused on cleanup and stabilization rather than new feature work. No new releases were published today. The activity is concentrated on fixing agent runtime tool loops, conversation UI scroll behavior, and closing stale bug reports from early April. This suggests the team is in a maintenance phase, likely preparing for a minor patch release.

## Releases
No new releases were published in the last 24 hours. The latest available version remains the pinned `v2026.6.1` runtime referenced in the PRs.

## Project Progress
Three PRs were merged today, all addressing stability and correctness issues:

- **#2331** ([PR link](https://github.com/netease-youdao/LobsterAI/pull/2331)) — `fix(openclaw): terminate critical tool loops` — Backports a dual-layer fix for OpenClaw runtime `v2026.6.1` so that a critical `tool-loop` veto properly terminates the current Agent run. Preserves normal plugin veto and allows sibling tools in mixed parallel batches to finish before stopping. Includes patch validation and regression coverage.

- **#2330** ([PR link](https://github.com/netease-youdao/LobsterAI/pull/2330)) — `fix(openclaw): stop loop after aborted tool run` — Backports upstream commit `7fe287b0d3` to stop the agent loop at abort boundaries after tool execution and async turn hooks. Includes regression coverage and Lobster-specific patch validation.

- **#2329** ([PR link](https://github.com/netease-youdao/LobsterAI/pull/2329)) — `fix(cowork): prevent conversation scroll jumps` — Fixes the cowork renderer to respect manual scrolling during streaming and cancel pending auto-scroll actions, addressing a common UX pain point.

## Community Hot Topics
No issues or PRs received significant community engagement today. All 4 issues were closed stale bugs with 2-3 comments each, and the 3 PRs had zero comments. The most discussed items (all from April 3, 2026) were:

- **Issue #1389** ([link](https://github.com/netease-youdao/LobsterAI/issues/1389)) — Language selection: when set to English, Chinese options still display in English. 3 comments.
- **Issue #1386** ([link](https://github.com/netease-youdao/LobsterAI/issues/1386)) — Share feature truncates long conversation screenshots. 2 comments.
- **Issue #1388** ([link](https://github.com/netease-youdao/LobsterAI/issues/1388)) — Email configuration test connectivity hangs indefinitely with invalid credentials. 2 comments.
- **Issue #1390** ([link](https://github.com/netease-youdao/LobsterAI/issues/1390)) — Scheduled tasks fail to update intermittently (no reproducible steps). 2 comments.

These issues were closed as stale without maintainer responses, suggesting the team may have deprioritized these items or fixed them in earlier releases.

## Bugs & Stability
Four closed bugs were updated today, all classified as stale and likely addressed in previous hotfixes. None are currently open.

- **Medium severity**: [Issue #1386](https://github.com/netease-youdao/LobsterAI/issues/1386) — Share feature truncates long conversations. Missing content in generated images. No fix PR identified.
- **Medium severity**: [Issue #1388](https://github.com/netease-youdao/LobsterAI/issues/1388) — Email test connectivity hangs. UI freezes indefinitely on invalid credentials. No fix PR identified.
- **Low severity**: [Issue #1390](https://github.com/netease-youdao/LobsterAI/issues/1390) — Scheduled task update fails intermittently. No reproducible conditions.
- **Low severity**: [Issue #1389](https://github.com/netease-youdao/LobsterAI/issues/1389) — Language selector display inconsistency with English UI language.

The two runtime-related PRs (#2331, #2330) directly address agent stability issues in the OpenClaw component. The cowork PR (#2329) fixes a UI scrolling regression.

## Feature Requests & Roadmap Signals
No new feature requests were submitted today. The work visible today is entirely focused on bug fixes and runtime stability, indicating the team may be in a pre-release stabilization phase. The backports from upstream OpenClaw suggest the project is actively tracking upstream improvements.

## User Feedback Summary
User pain points visible from closed issues include:
- **Language localization**: English UI users experience inconsistent Chinese translation display.
- **Content sharing**: Long conversations generate incomplete screenshots, breaking an important sharing use case.
- **Email configuration**: Invalid credentials cause UI-freezing test connectivity, with no timeout or error feedback.
- **Scheduled tasks**: Intermittent update failure reduces reliability for automation use cases.
- **Conversation scrolling**: Streaming content causes unwanted auto-scroll (addressed by PR #2329).

No positive user feedback or satisfaction indicators were recorded today.

## Backlog Watch
No long-unanswered issues or PRs require maintainer attention today, as all recently updated items were either closed stale or merged. The oldest updated items are from April 3, 2026. No open PRs are pending.

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyagi">TinyAGI/tinyagi</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

# Moltis Project Digest — 2026-07-15

## 1. Today's Overview
Moltis shows **elevated maintenance activity** over the past 24 hours, with 12 PRs updated (8 merged/closed, 4 open) and 3 issues updated (2 open, 1 closed). A new release **20260714.11** was published. The project remains in a **healthy, iterative maintenance phase**—most activity focuses on bug fixing (browser tool compatibility, MCP OAuth, CalDAV parsing, gateway builds) and dependency updates rather than large new features. Two significant open feature PRs (chat context commands, browser auto-screenshots) continue to mature without merge, indicating careful review.

## 2. Releases
**Tag:** `20260714.11` (2026-07-14)

This is a point release; no changelog or breaking-change notes were included in the data. Given the high density of bug fixes merged on 2026-07-14, this release likely bundles:
- MCP OAuth fix for `resource_metadata` URLs (PR #1120, fixes #1119)
- Browser `null` optional parameter tolerance (PR #1098)
- Stringified scalar tool argument coercion (PR #1136)
- CalDAV non-ASCII datetime panic fix (PR #1145)
- Gateway `metrics` feature flag fix (PR #1139)
- Tool result cap on rehydration (PR #1089)

**Migration note:** No breaking changes expected.

## 3. Project Progress
**Merged/closed PRs (8 total):**
- **#1146** — GPT-5.6 model support (Sol, Terra, Luna) added to OpenAI/Codex catalogs; superseded models replaced in config examples
- **#1141** — npm/yarn dependency bump (esbuild, vite)
- **#1120** — Fix MCP OAuth `invalid_target` for servers using `resource_metadata` (Notion, Linear) — *direct fix for Issue #1119*
- **#1139** — Gateway `metrics` feature no longer force-enables matrix-sdk; weak dependency qualifier fix
- **#1145** — CalDAV `normalise_datetime` panic on non-ASCII datetimes from remote servers
- **#1136** — Coerce stringified scalar tool args (e.g., `"true"` → `true`) from small local models before validation
- **#1098** — Tolerate explicit `null` for optional browser tool params (Gemma 4 compatibility)
- **#1089** — Cap persisted tool/tool_result content on session rehydration

**Open PRs (4 total):**
- **#1148** — Dependabot npm/yarn update
- **#1124** — Chat context command support (per-turn runtime context injection)
- **#1135** — Browser auto-screenshots after state-changing actions
- **#1093** — Channel activity log visibility settings (per-account/channel/user)

## 4. Community Hot Topics
- **Issue #1102** (open, Feature: Add FunASR/SenseVoice as local STT engine) — 2 comments, 0 reactions. A maintainer added a license/capability clarification note on 2026-07-14, indicating ongoing evaluation. This feature addresses the need for **fully local, open-source speech-to-text** without cloud dependencies.
- **Issue #1132** (open, Bug: "main" session can't be deleted/archived) — 1 comment, 0 reactions. Core UX limitation; no fix PR yet.
- **Issue #1119** (closed, Bug: MCP OAuth `invalid_target`) — 1 comment, fix merged as PR #1120. High interest as it affects popular MCP servers (Notion, Linear).

## 5. Bugs & Stability
| Severity | Issue | Status | Fix |
|----------|-------|--------|-----|
| **Critical** | #1132 — "main" session cannot be deleted/archived (data management blocker) | Open | **No fix PR** |
| **High** | #1119 — MCP OAuth fails with `invalid_target` for Notion/Linear | Closed | **Fixed** in PR #1120 |
| **Medium** | #1145 — CalDAV panic on non-ASCII datetimes from remote servers | Closed | **Fixed** in PR #1145 (merged) |
| **Medium** | #1136 — Stringified scalar args from small models (Gemma 4, oMLX) cause validation failures | Closed | **Fixed** in PR #1136 (merged) |
| **Low** | #1098 — `null` optional params in browser tool calls from Gemma 4 | Closed | **Fixed** in PR #1098 (merged) |
| **Low** | #1139 — Gateway metrics feature force-enables matrix-sdk unnecessarily | Closed | **Fixed** in PR #1139 (merged) |

**Summary:** 5 out of 6 bugs reported recently have been fixed. One critical issue (#1132) remains without a fix PR.

## 6. Feature Requests & Roadmap Signals
**Likely in next release:**
- **Chat context command** (PR #1124) — Allows deployments to inject runtime context before each chat turn. Clean, well-specified; has been open since June 15 with no blockers.
- **Browser auto-screenshots** (PR #1135) — Per-step screenshot timeline for state-changing actions. Open since June 26; recent activity suggests active review.

**On the radar:**
- **FunASR/SenseVoice local STT** (Issue #1102) — Maintainer is researching licensing/capabilities. May land in a future minor release if licensing is acceptable.
- **Channel activity log visibility settings** (PR #1093) — Granular visibility controls for multi-user channels. Open since June 3; could ship in a subsequent release.
- **GPT-5.6 integration** — Already merged (PR #1146), so fully supported in current release.

## 7. User Feedback Summary
- **Session management pain point** (Issue #1132): User vvuk reports the "main" session is non-deletable/archivable, causing data hygiene issues. No workaround documented.
- **MCP server compatibility** (Issue #1119): User xzavrel found that popular MCP servers (Notion, Linear) fail during OAuth flow. Explicitly states "fixes my issue" in the PR—strong satisfaction signal from the fix.
- **Small model compatibility** (PR #1098, #1136): Community users report Gemma 4 and oMLX emit non-standard JSON tool arguments. The project has responded with two targeted fixes, showing responsiveness to local-model enthusiasts.
- **Feature request engagement** (Issue #1102): LauraGPT's request for FunASR/SenseVoice STT received a detailed license clarification from maintainers—demonstrating careful, transparent evaluation process.

## 8. Backlog Watch
- **Issue #1132** (open since 2026-06-18, 27 days) — **Critical UX bug** with no fix PR. "main" session undeletable. Needs maintainer attention and prioritization.
- **PR #1093** (open since 2026-06-03, 42 days) — Channel activity log visibility. No maintainer comments on the PR; may require review bandwidth.
- **PR #1124** (open since 2026-06-15, 30 days) — Chat context command. No recent activity from reviewer; feature is well-spec'd and could be merged.
- **PR #1135** (open since 2026-06-26, 19 days) — Browser auto-screenshots. Last update improved the branch; awaiting final review.

**Links:**
- [Issue #1132](https://github.com/moltis-org/moltis/issues/1132)
- [PR #1093](https://github.com/moltis-org/moltis/pull/1093)
- [PR #1124](https://github.com/moltis-org/moltis/pull/1124)
- [PR #1135](https://github.com/moltis-org/moltis/pull/1135)

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

Here is the project digest for CoPaw (GitHub repository: agentscope-ai/QwenPaw) for **2026-07-15**.

---

## CoPaw Project Digest — 2026-07-15

### 1. Today's Overview
The CoPaw project is experiencing a period of **intense, high-volume activity**, driven largely by the fallout from the recent v2.0.0 release. In the last 24 hours, there were 50 updated Issues and 50 updated PRs, with a 1:1 ratio of open to closed work. While 34 issues were resolved, 16 remain open, signaling a significant backlog of user-reported bugs and regressions. A single patch release (v2.0.0.post2) was published to address critical sandbox and packaging issues. The community is highly engaged but frustrated, with the vast majority of discussion centered on regressions in the new sandbox, memory system, and context compression.

### 2. Releases
- **New Version:** [v2.0.0.post2](https://github.com/agentscope-ai/QwenPaw/releases/tag/v2.0.0.post2)
- **Key Changes:**
    - `feat`: Added more sensitive files to the sandbox and allowed global read access.
    - `chore`: Version bump to 2.0.0.post2.
    - `test`: Added regression tests for runtime, security, and install processes.
- **Migration Notes:** This is a hotfix release. Users experiencing the sandbox and module import issues (e.g., `No module named 'agentscope.tool._builtin._scripts'`) should upgrade immediately via `pip install --upgrade qwenpaw` or the desktop app auto-updater.

### 3. Project Progress
In the last 24 hours, the team merged/closed 26 PRs and 34 Issues. Key advancements and fixes include:
- **New Channel:** Added a [Zalo Bot channel](https://github.com/agentscope-ai/QwenPaw/pull/6112) using the new plugin architecture.
- **Memory Fix:** [PR #6098](https://github.com/agentscope-ai/QwenPaw/pull/6098) improved reliability of the ReMe memory system and fixed a CJK embedding safety issue (related to Issue #5950).
- **Governance Fixes:** Multiple PRs ([#6109](https://github.com/agentscope-ai/QwenPaw/pull/6109), [#6122](https://github.com/agentscope-ai/QwenPaw/pull/6122)) addressed the sandbox not respecting the `OFF` mode or global switches.
- **Context Compression:** [PR #6108](https://github.com/agentscope-ai/QwenPaw/pull/6108) fixes a bug where tool results were orphaned during compression, causing permanent session breakage with DeepSeek.
- **Desktop CI:** Improved desktop build pipelines ([#6110](https://github.com/agentscope-ai/QwenPaw/pull/6110)).

### 4. Community Hot Topics
The most active issues highlight a user base that is **struggling with the stability of the v2.0.x line**.

- **[Issue #5951](https://github.com/agentscope-ai/QwenPaw/issues/5951) (CLOSED): Windows Sandbox Bug (pwsh recursion, memory exhaustion)** — *9 comments*. This was a critical "OS-level" bug. The Windows sandbox was spawning infinite `pwsh` windows, eating 20GB of RAM, and was unkillable. A root cause was identified in the sandbox init flow.
- **[Issue #6113](https://github.com/agentscope-ai/QwenPaw/issues/6113) (OPEN): Memory search loop** — *5 comments*. Users report that the agent gets stuck in an endless loop searching memory before every response, rendering the tool nearly unusable. This is a significant UX regression.
- **[Issue #6121](https://github.com/agentscope-ai/QwenPaw/issues/6121) (OPEN): Context compression breaks DeepSeek API** — *4 comments*. A specific failure mode where scrolling and compressing context leads to a permanent error when using the DeepSeek API, forcing users to start a new session.
- **[Issue #6023](https://github.com/agentscope-ai/QwenPaw/issues/6023) (CLOSED): Sandbox & Tool Guard Overhaul** — *2 👍*. A maintainer-opened meta-issue to gather feedback, acknowledging the sandbox is causing too much user friction.
- **Need:** Users are demanding **stability, predictability, and configurability** for core features like sandbox, memory, and context management. They want these systems to work silently without breaking their workflows.

### 5. Bugs & Stability
The project's stability is under pressure, with several high-severity regressions reported today. The team is responding with targeted patches.

| Severity | Bug Description | Issue | Fix PR? |
| :--- | :--- | :--- | :--- |
| **Critical** | Agent enters a "doom loop," calling the same tool repeatedly in a single turn, wasting tokens and time. | [#6116](https://github.com/agentscope-ai/QwenPaw/issues/6116) | None yet |
| **High** | Context compression for DeepSeek API orphans `tool` messages, leading to a 400 error and broken sessions. | [#6121](https://github.com/agentscope-ai/QwenPaw/issues/6121), [#6077](https://github.com/agentscope-ai/QwenPaw/issues/6077) | [PR #6108](https://github.com/agentscope-ai/QwenPaw/pull/6108) (merged) |
| **High** | Agent is stuck in an infinite "searching memory" loop before every user query. | [#6113](https://github.com/agentscope-ai/QwenPaw/issues/6113) | [PR #6120](https://github.com/agentscope-ai/QwenPaw/pull/6120) (open) |
| **Medium** | Approval system routes to wrong channel and `approval_level: OFF` is ignored for built-in tools. | [#6020](https://github.com/agentscope-ai/QwenPaw/issues/6020) | [PR #6122](https://github.com/agentscope-ai/QwenPaw/pull/6122) (open) |
| **Medium** | Upgrading from v1.x causes loss of agent config and workspace settings. | [#5964](https://github.com/agentscope-ai/QwenPaw/issues/5964), [#6100](https://github.com/agentscope-ai/QwenPaw/issues/6100) | None explicitly |

### 6. Feature Requests & Roadmap Signals
Despite the stability issues, the community is looking ahead. Key feature requests from today include:
- **Real-time message injection:** [Issue #6087](https://github.com/agentscope-ai/QwenPaw/issues/6087) requests the ability for a user to send a correction *during* an agent's tool-calling loop, rather than waiting for it to finish. This is a sophisticated UX request that indicates advanced users.
- **Controlled tool result output:** [Issue #5976](https://github.com/agentscope-ai/QwenPaw/issues/5976) asks for the ability to truncate or even suppress the verbose results of tool calls sent to channels (e.g., Feishu, DingTalk).
- **Benchmarking against Hermes:** [Issue #6064](https://github.com/agentscope-ai/QwenPaw/issues/6064) suggests the underlying agent architecture should be benchmarked against Hermes Agent for usability.
- **Prediction:** The **real-time message injection** feature is a strong signal for the next major feature. It's currently an open issue with a well-defined problem, and solving it would significantly improve the user experience for complex, multi-turn tasks.

### 7. User Feedback Summary
User sentiment is **mixed**. While there is excitement about the new architecture and features (like the pluggable channels), there is widespread frustration with the v2.0 upgrade.
- **Pain Points:**
    - "The sandbox is broken and unkillable."
    - "The memory system is too aggressive and gets stuck in loops."
    - "Context compression breaks my session permanently."
    - "Upgrading from v1.x lost all my settings."
- **Positive Signals:**
    - Users are still actively filing feature requests, indicating they see long-term value in the project.
    - The feedback on the "Sandbox & Tool Guard Overhaul" issue shows users are willing to help co-design solutions.
- **Satisfaction:** Low regarding stability. High regarding the project's potential and the maintainers' responsiveness (e.g., multiple patches released in a single day).

### 8. Backlog Watch
- **[PR #5187](https://github.com/agentscope-ai/QwenPaw/pull/5187) (OPEN, 30 days old):** "Windows desktop GUI automation with UIA + Tauri control mode." This is a major new feature (computer-use) that has been open for a month and is not yet merged. It requires attention to land before it becomes stale.
- **[Issue #578](https://github.com/agentscope-ai/QwenPaw/issues/578) (CLOSED, 130 days old):** "Meta: OpenClaw-Inspired Features." This was a strategic meta-issue but was recently closed. If the ideas are not being tracked elsewhere, they could be lost. A follow-up issue to track the adoption of these features would be beneficial.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

# ZeroClaw Project Digest — 2026-07-15

Generated from `github.com/zeroclaw-labs/zeroclaw` activity data

---

## 1. Today's Overview

ZeroClaw is in a high-activity maintenance and feature-completion phase, with 29 issues updated in the last 24 hours (23 open, 6 closed) and 50 pull requests updated (34 open, 16 merged/closed). The project is preparing for the **v0.8.4 maintenance train** (tracked in #8357) while simultaneously advancing the **SOP control plane** (tracker #8288, targeted for 5/5 completeness) and **multi-user isolation** milestones (#8290, #8289). Security and reliability remain dominant themes, with critical bugs around Landlock sandbox compatibility (#8973) and confused-deputy tool authorization (#7947) still open. Notably, no new releases were cut today, but **7 PRs from the Hindsight memory stack** (parts 2–7) landed together under `logical-and`, indicating a major memory subsystem overhaul is being finalized.

---

## 2. Releases

**No new releases today.**

The v0.8.3 milestone closeout tracker (#7320) is still open, suggesting release validation is ongoing. The v0.8.4 maintenance train (#8357) has a target date of **July 31, 2026**.

---

## 3. Project Progress

**16 PRs were merged or closed today (8 closed issues, 16 merged/closed PRs).** Notable completions:

| PR/Issue | Description | Significance |
|---|---|---|
| #9077 (merged) | Fix spurious positional arg in `channel start` docs example | Quick doc fix, improves ops usability |
| #8582 (merged) | Terminate ephemeral daemon on connection failure (ZeroCode) | Prevents zombie daemon processes |
| #8678 (closed) | `advance_step` had no run-status guard — approval gate bypass | **Security fix**: SOP engine integrity |
| #8631 (closed) | Headless deterministic SOP steps recorded "Completed" without executing | **Audit integrity fix** |
| #6689 (closed) | SOP audit silently no-op — documented memory keys never written | **Observability fix**: production audit was non-functional |
| #6686 (closed) | SOP cron triggers had no production caller | **Feature completion**: cron-triggered SOPs now operational |
| #8413 (closed) | Filesystem SOP event source | **New capability**: file-system-triggered SOPs |

**Memory subsystem overhaul**: The 7-stack Hindsight memory PRs (#9064–#9069, plus #9069 dashboard slice) are all open but together represent a comprehensive refactor adding shared/system memory tiers, recall/injection tuning, consolidation/dedup correctness, async retain, and dashboard integration. Part 2 (#9064) introduces authorization for shared memory; Part 3 (#9065) makes recall caps config-driven; Part 6 (#9068) adds async vectorization.

---

## 4. Community Hot Topics

Most active issues and discussions (by comment count):

| Item | Comments | Topic |
|---|---|---|
| [#5982 — Per-sender RBAC](https://github.com/zeroclaw-labs/zeroclaw/issues/5982) | 10 comments | Multi-tenant security; high-risk P2 enhancement, accepted for development |
| [#6055 — Slack thread hydration](https://github.com/zeroclaw-labs/zeroclaw/issues/6055) | 7 comments | User experience: backfill thread context on first mention |
| [#8973 — Landlock blocks shell on Fedora](https://github.com/zeroclaw-labs/zeroclaw/issues/8973) | 4 comments | **Critical P1 bug** blocking Linux users |
| [#9048 — Separate conversation from long-term memory](https://github.com/zeroclaw-labs/zeroclaw/issues/9048) | 3 comments | Architecture RFC — memory model improvement |
| [#8933 — Cross-turn OTel correlation](https://github.com/zeroclaw-labs/zeroclaw/issues/8933) | 3 comments | Observability RFC — conversation ID in telemetry |
| [#9070 — Anthropic SSE tool_use flush fix](https://github.com/zeroclaw-labs/zeroclaw/pull/9070) | PR, active | Provider streaming completeness |

**Analysis**: The community is heavily invested in **security architecture** (RBAC, multi-tenancy, isolation) and **SOP engine completeness**. The Slack thread hydration request (#6055) signals a real user pain point: agents lose context when re-mentioned in threads, forcing users to re-explain. The memory model RFC (#9048) is being actively debated — three comments in <24h suggests strong interest.

---

## 5. Bugs & Stability

### Critical (S0) — Security Risk
- **[#7947](https://github.com/zeroclaw-labs/zeroclaw/issues/7947): `execute_pipeline` bypasses per-agent tool gating** (confused deputy). Status: **in-progress**, assigned. Severity **S0 — data loss / security risk**. Pipeline steps use global allowed-tools instead of per-agent `ToolAccessPolicy`. **No fix PR exists yet.**

### High (P1) — S1/S2 severity
- **[#8973](https://github.com/zeroclaw-labs/zeroclaw/issues/8973): Landlock blocks shell access on Fedora** — `sh` cannot access `/dev/null`. Reported by `perillamint`. No fix PR. Affects all Linux users with Landlock enabled.
- **[#8563](https://github.com/zeroclaw-labs/zeroclaw/issues/8563): SOPs not available via web dashboard** — configured SOPs invisible to agent runtime. S1 — workflow blocked. No fix PR.
- **[#8675](https://github.com/zeroclaw-labs/zeroclaw/issues/8675): Malformed tool-call arguments sent to OpenAI providers** → 400 error → empty reply. S1 — workflow blocked. No fix PR.
- **[#8631](https://github.com/zeroclaw-labs/zeroclaw/issues/8631) (closed):** Headless deterministic SOPs recorded "Completed" without executing — **fix merged.**
- **[#8678](https://github.com/zeroclaw-labs/zeroclaw/issues/8678) (closed):** `advance_step` approval gate bypass — **fix merged.**

### Medium (P2) — S2 severity
- **[#8695](https://github.com/zeroclaw-labs/zeroclaw/issues/8695) (closed):** Cron jobs still recall memory when `uses_memory = false` — **fix merged.**
- **[#9001](https://github.com/zeroclaw-labs/zeroclaw/issues/9001):** Provider turn failures bury cause-specific diagnostics under generic retry envelope — open, needs maintainer review.
- **[#9052](https://github.com/zeroclaw-labs/zeroclaw/issues/9052):** `channel-line` omitted from CI/feature coverage — blocks CI for LINE channel users.

**Assessment**: Two high-severity security bugs (#7947, #8973) remain unpatched. The SOP engine bugs that were closed today (#8678, #8631) show the team is actively hardening the SOP runtime. The **confused-deputy** issue (#7947) is the most concerning — it's S0 severity with no visible fix PR.

---

## 6. Feature Requests & Roadmap Signals

### Active feature requests from community

| Issue | Feature | Likelihood for v0.8.4 |
|---|---|---|
| [#5982](https://github.com/zeroclaw-labs/zeroclaw/issues/5982) | Per-sender RBAC for multi-tenant | **High** — tracked by #8290, part of multi-user milestone |
| [#5607](https://github.com/zeroclaw-labs/zeroclaw/issues/5607) | Pre-hook skip gates for cron/SOP triggers | Medium — needs Maintainer review, P2 |
| [#8719](https://github.com/zeroclaw-labs/zeroclaw/issues/8719) | SOP `when` false should advance to next step | **High** — P2, accepted, enables multi-phase SOPs |
| [#9048](https://github.com/zeroclaw-labs/zeroclaw/issues/9048) | Separate conversation history from long-term memory | RFC — ties to Hindsight memory stack already in PR |

### What's actively shipping
- **SOP authoring surface** (#8736, task): Node-graph editor, live run overlays, channel fan-in — likely ships with v0.8.4
- **Multi-user isolation** (#8290): Per-principal sessions, per-sender authz — major milestone
- **OIDC first-shippable** (#8289): Pluggable AuthProvider — likely v0.8.5
- **ZeroRelay** (#8358): Blind forwarder for NAT traversal — tracked, active

**Prediction**: v0.8.4 will ship **SOP control plane completion** (13 capabilities, tracker #8288), **SOP authoring UI** (#8736), and **memory subsystem overhaul** (Hindsight stack parts 1–7). RBAC (#5982) and OIDC (#8289) likely slip to v0.8.5.

---

## 7. User Feedback Summary

**Pain points expressed:**

1. **Landlock incompatibility** (#8973): Linux users on Fedora cannot use shell tools with default security — forces either disabling Landlock or switching distributions.
2. **SOPs invisible in web dashboard** (#8563): Users following the StageHand example cannot see their SOPs in the agent's runtime. "The current documentation lacks detailed examples" (#8587) compounds this.
3. **Slack thread context loss** (#6055): Users must re-@mention the bot on every thread message, with no prior context — degraded UX compared to competing agents.
4. **Generic error messages** (#9001): When providers fail (LM Studio, Ollama), the system reports "All model_providers/models failed" with raw retry traces — users cannot distinguish connectivity issues from model errors.
5. **Memory model confusion** (#9048): The documented separation between conversation history and long-term memory isn't reflected in actual behavior — `uses_memory = false` still triggers memory recall (#8695, now fixed).

**Satisfaction signals:**
- Active engagement on SOP and OIDC trackers suggests power users are invested in the roadmap.
- The 7-PR Hindsight memory stack being co-authored by a single contributor (`logical-and`) indicates the codebase is approachable for external contributors.

---

## 8. Backlog Watch

### Issues needing maintainer attention (>14 days stale without maintainer response)

| Issue | Days since last update | Priority | Risk |
|---|---|---|---|
| [#5982](https://github.com/zeroclaw-labs/zeroclaw/issues/5982) — Per-sender RBAC | 84 days (created Apr 22) | P2 | High — accepted but no PR |
| [#5607](https://github.com/zeroclaw-labs/zeroclaw/issues/5607) — Pre-hook skip gates | 96 days (created Apr 10) | P2 | High — accepted, blocked |
| [#6685](https://github.com/zeroclaw-labs/zeroclaw/issues/6685) — SOP HTTP fan-in not wired | 61 days (created May 15) | P2 | High — documented but not implemented |
| [#8357](https://github.com/zeroclaw-labs/zeroclaw/issues/8357) — v0.8.4 tracker | 19 days | P2 | High — milestone slip risk |

### PRs needing author action (blocked by maintainer feedback)

| PR | Days since action requested |
|---|---|
| [#8890](https://github.com/zeroclaw-labs/zeroclaw/pull/8890) — Web search status classification | 6 days |
| [#9029](https://github.com/zeroclaw-labs/zeroclaw/pull/9029) — OpenAI vision capability | 2 days |
| [#8923](https://github.com/zeroclaw-labs/zeroclaw/pull/8923) — WASM plugin raw TCP/TLS | 6 days |
| [#8353](https://github.com/zeroclaw-labs/zeroclaw/pull/8353) — Error message context | 19 days |
| [#8901](https://github.com/zeroclaw-labs/zeroclaw/pull/8901) — Comment bureaucracy sweep | 6 days |

**Most concerning**: Issue #5982 (per-sender RBAC) has been accepted for 84 days with no PR attached, despite being part of the multi-user milestone. The `needs-maintainer-review` flag on RFC #9048 (memory separation) hasn't been triaged since creation yesterday, but that's acceptable for a new submission.

---

*Data snapshot: 2026-07-15 00:00 UTC. Generated from GitHub issue/PR metadata.*

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*