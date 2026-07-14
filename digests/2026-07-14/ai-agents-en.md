# OpenClaw Ecosystem Digest 2026-07-14

> Issues: 100 | PRs: 500 | Projects covered: 13 | Generated: 2026-07-14 01:29 UTC

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

Here is the OpenClaw project digest for **2026-07-14**.

---

## OpenClaw Project Digest – 2026-07-14

### 1. Today's Overview
The project is experiencing **very high activity**, with 100 issues and 500 pull requests updated in the last 24 hours. This signals a major push towards stabilizing the upcoming release. Two new versions (v2026.7.1-beta.6 and v2026.7.1) were cut, introducing several new model providers and making GPT-5.6 the default setup model. However, the high volume of open issues (91 out of 100) with "diamond lobster" and "platinum hermit" ratings indicates significant stability regressions and blocking bugs that the team is actively addressing. The community is highly engaged, with several long-running feature requests and critical bugs receiving sustained attention.

### 2. Releases
Two releases were published today:
- **v2026.7.1 (stable)** and **v2026.7.1-beta.6**: Both share the same changelog.
    - **New Models & Providers**: Added support for **Featherless**, **Claude Sonnet 5**, **Mythos 5**, **Meta Muse Spark 1.1**, and the internal **ClawRouter**.
    - **Default Model Change**: **GPT-5.6** is now the default model for new setups.
    - **Thinking Defaults**: The `/think ultra` directive is now the default for "Sol" and "Terra" models, while `max` is the default for "Luna". The `max` setting for Z.AI is now honored.
    - **UX Improvement**: Model availability is now automatically refreshed after an OAuth handshake, preventing stale provider lists.

### 3. Project Progress
Of the 500 updated PRs, **244 were closed or merged** today. Key areas of progress include:
- **Memory Architecture**: PR [#88504](https://github.com/openclaw/openclaw/pull/88504) *(feat(memory): add multi-slot memory role architecture)* is a massive feature addition that refactors the memory plugin system to support multiple roles (factual recall, auto-capture, etc.) rather than a single owner.
- **Stability & Bug Fixes**: Several critical fixes were merged, including PR [#103290](https://github.com/openclaw/openclaw/pull/103290) *(fix(wizard): make failed Hermes imports safely retryable)*, which addresses a blocking P0 onboarding issue.
- **Security & Data Integrity**: PR [#101037](https://github.com/openclaw/openclaw/pull/101037) *(fix(acp): preserve structured exec approval metadata)* strengthens the security boundary for structured exec approvals.
- **Codex Integration**: PR [#106927](https://github.com/openclaw/openclaw/pull/106927) *(feat(codex): continue paired-node Codex catalog sessions from the Control UI)* unblocks a key feature for multi-node setups.

### 4. Community Hot Topics
The following issues and PRs generated the most discussion:
- **Issue [#7707](https://github.com/openclaw/openclaw/issues/7707)** *(Feature: Memory Trust Tagging by Source)*: With 18 comments, this is the most active discussion. The community is deeply concerned about **memory poisoning attacks**. The request to tag memories by source (user commands vs. web scrapes) reflects a growing need for security-conscious agent design.
- **Issue [#38327](https://github.com/openclaw/openclaw/issues/38327)** *(Bug: "Cannot convert undefined or null to object" in 2026.3.2 with google-vertex/gemini-3.1-pro-preview)*: Still active with 11 comments, this long-standing regression (from March) continues to frustrate users, highlighting a need for better regression testing for enterprise providers like Google Vertex.
- **Issue [#90213](https://github.com/openclaw/openclaw/issues/90213)** *(Bug: Legacy state migration warnings persist after `doctor --fix`)*: This regression in the migration tool (10 comments) is a major usability pain point, preventing users from cleanly upgrading to the latest versions.
- **Issue [#103076](https://github.com/openclaw/openclaw/issues/103076)** *(Bug: Additional legacy-state migration sources block startup)*: A P0 blocker that continues to stall users upgrading to the latest "main" branch, indicating the migration process is more fragile than expected.
- **Issue [#77012](https://github.com/openclaw/openclaw/issues/77012)** *(Bug: WebChat session transcript overwritten on every turn)*: This 5.2 regression (7 comments) is a critical data-loss bug that undermines trust in the webchat interface.

### 5. Bugs & Stability
The project has a high volume of stability regressions. The most critical today are:
- **Critical (P0)**:
    - **Migration Blockers**: Issue [#103076](https://github.com/openclaw/openclaw/issues/103076) (additional legacy-state sources block gateway startup) and the now-closed [#103262](https://github.com/openclaw/openclaw/issues/103262) (onboarding migration commits config before applying) remain the most severe. Fix PR [#103290](https://github.com/openclaw/openclaw/pull/103290) aims to resolve the latter.
- **High (P1)**:
    - **Message Loss & Delivery**: Issues [#86012](https://github.com/openclaw/openclaw/issues/86012) (LINE channel message loss), [#90944](https://github.com/openclaw/openclaw/issues/90944) (sessions_yield wrong reply), and [#76665](https://github.com/openclaw/openclaw/issues/76665) (Z.AI context loss) represent a serious cluster of **message corruption and loss bugs**.
    - **Crash Loops**: Issue [#76275](https://github.com/openclaw/openclaw/issues/76275) (gateway restarting loop) is a long-standing high-severity regression that has been open since early May.
    - **Container/OS Issues**: Issue [#77178](https://github.com/openclaw/openclaw/issues/77178) (EPIPE on claude-cli in Docker) and [#77610](https://github.com/openclaw/openclaw/issues/77610) (spawn EBADF on macOS) highlight platform-specific runtime failures.
- **Medium (P2/P3)**:
    - **Doctor Tool Loop**: Issue [#77802](https://github.com/openclaw/openclaw/issues/77802) (doctor --fix fails atomically) is a high-impact UX bug preventing self-repair.
    - **Infinite Reasoning Loops**: Issue [#77625](https://github.com/openclaw/openclaw/issues/77625) (reasoningDefault=stream causes feedback loop) is a concerning AI behavior bug that can trap agents in infinite loops.

### 6. Feature Requests & Roadmap Signals
The most requested features indicate a clear user demand for **security, context management, and user safety**:
- **Memory Security ([#7707](https://github.com/openclaw/openclaw/issues/7707))**: The "Memory Trust Tagging by Source" feature is the most active request. This is a strong signal that the community is thinking about adversarial threats to agent memory.
- **Memory Hygiene ([#77447](https://github.com/openclaw/openclaw/issues/77447))**: A "memory hygiene doctor" to sanitize persisted artifacts (paths, tool outputs) is another clear security/privacy request.
- **Context Management ([#9986](https://github.com/openclaw/openclaw/issues/9986))**: Triggering model fallback on context length exceeded is a highly practical request to prevent session errors.
- **Non-Technical User Mode ([#77567](https://github.com/openclaw/openclaw/issues/77567))**: The "Uncle Jim mode" for isolated family agents suggests a desire to make OpenClaw safe and simple for non-technical users.
- **TUI Agent Selection ([#8892](https://github.com/openclaw/openclaw/issues/8892))**: A `--agent` flag for TUI is a simple but high-utility feature for multi-agent setups.

**Prediction for v2026.7.x**: The inclusion of PR [#88504](https://github.com/openclaw/openclaw/pull/88504) (multi-slot memory) suggests the foundation for advanced memory features is being laid. A "memory hygiene" feature is a likely follow-up in the next cycle.

### 7. User Feedback Summary
User sentiment is mixed. While the new models and features (like Featherless and Claude Sonnet 5) are welcome, the project is suffering from **a perceived decline in stability**.
- **Dissatisfaction**: There is significant frustration with **regressions**. Users report that "things that worked before" (like WebChat transcripts, WhatsApp, Google Chat) are breaking. The migration process (`doctor --fix`) is described as being in a "broken loop."
- **Pain Points**: The most painful issues are **silent message loss** (LINE, sessions_yield), **context corruption** (Z.AI, memory compaction), and **inability to cleanly upgrade** (legacy migration warnings).
- **Positive**: Despite bugs, users are actively working with the tool, reporting issues in detail, and contributing complex features (like the multi-slot memory architecture PR).

### 8. Backlog Watch
Several high-severity, long-stale issues (since May) remain open without a fix PR, which is concerning for project health.
- **Issue [#77443](https://github.com/openclaw/openclaw/issues/77443)** (WhatsApp event loop blocked – P1, stale since May 4): A blocking regression on Windows that has seen no fix PR.
- **Issue [#77675](https://github.com/openclaw/openclaw/issues/77675)** (SecretRef fails in embedded agents – P1, stale since May 5): A critical security/auth failure that is completely stalled.
- **Issue [#77720](https://github.com/openclaw/openclaw/issues/77720)** (Subagent children get no termination signal – P1, stale since May 5): A fundamental reliability issue for multi-agent workflows.
- **Issue [#77121](https://github.com/openclaw/openclaw/issues/77121)** (Exec tool can launch heavy validation commands – P1, stale since May 4): A security vulnerability where the `exec` tool can be used to harm the host system.
- **Issue [#77012](https://github.com/openclaw/openclaw/issues/77012)** (WebChat transcript overwritten – P1, stale since May 4): A critical data-loss bug with no fix in sight.

---

## Cross-Ecosystem Comparison

Here is the cross-project comparison report based on the daily digest data for **2026-07-14**.

---

### Cross-Project Ecosystem Report: Open-Source AI Agents & Assistants

**Date:** 2026-07-14

---

### 1. Ecosystem Overview

The personal AI agent open-source landscape is characterized by high-velocity development driven by the need for stability, security, and advanced memory management. Projects are currently in a dual state of rapid iteration and critical bug-bash stabilization following major version releases. Key themes dominating the space include a deep focus on **memory architecture** (trust, hygiene, and context management), **multi-channel reliability** (from Telegram to Matrix), and **governance hardening** (approval flows, tool allowlisting, and security auditing). The community is actively pushing projects toward more robust, production-ready deployments while demanding better UX for both technical and non-technical users, signaling a maturation of the ecosystem from experimental to enterprise-adjacent capabilities.

### 2. Activity Comparison

The table below compares the 24-hour activity for each project tracked on 2026-07-14. "Health Score" is a qualitative indicator based on bug-to-fix ratio, project velocity, and community sentiment.

| Project | Issues Updated | PRs Updated | Release Status | Health Score |
| :--- | :--- | :--- | :--- | :--- |
| **OpenClaw** | 100 | 500 | New v2026.7.1 (Stable) | **Stabilizing** |
| **NanoBot** | 13 | 45 | No new release | **High Velocity** |
| **Hermes Agent** | 50 | 50 | No new release | **Stabilizing** |
| **PicoClaw** | 4 | 5 | No new release | **Stable** |
| **NanoClaw** | 3 | 33 | No new release | **High Velocity** |
| **NullClaw** | 0 | 12 | No new release | **Steady** |
| **IronClaw** | 34 | 50 | No new release | **Bug Bash** |
| **LobsterAI** | 0 | 21 | No new release | **High Velocity** |
| **Moltis** | 0 | 1 | No new release | **Low Activity** |
| **CoPaw** | 50 | 50 | v2.0.0.post1 (Patch) | **Critical Bugs** |
| **ZeroClaw** | 50 | 50 | v0.8.3 Imminent | **High Velocity** |
| **TinyClaw** | 0 | 0 | N/A | **Inactive** |
| **ZeptoClaw** | 0 | 0 | N/A | **Inactive** |

**Key Observations:**
- **Extreme Velocity:** OpenClaw, CoPaw, and ZeroClaw are the most active, but with different drivers: OpenClaw is managing a post-release surge, CoPaw is in a crisis stabilization mode, and ZeroClaw is pushing toward a milestone.
- **Maintenance-Focused:** NanoBot, NanoClaw, and LobsterAI are in a high-velocity maintenance phase, merging many fixes for regressions and smaller features.
- **High Risk:** IronClaw is in an active "bug bash" with many new P2/P3 issues, while CoPaw has multiple critical P0 regressions from its v2.0.0 release.

### 3. OpenClaw's Position

**Advantages:** OpenClaw is the most active and mature "reference" project, acting as the central hub for the ecosystem. It has the largest community (500 PRs in 24 hours) and a clear release cadence with a new stable version. Its extensive model provider support and the recent **multi-slot memory architecture** (PR #88504) represent a significant technical lead in advanced agent memory design.

**Technical Approach:** OpenClaw is adopting a highly modular, plugin-driven architecture with a strong focus on security (structured exec approvals, trust tagging). It appears to be the most architecture-heavy, with large, foundational refactors (e.g., memory, migration tools).

**Community:** The community is both the largest and most vocal. While highly engaged and contributing complex features, user sentiment is mixed due to a perceived decline in stability post-release. This suggests a classic "early adopter" tension between rapid feature iteration and reliability.

**Peers:** Compared to smaller projects like NanoBot or NullClaw, OpenClaw moves faster but with more noticeable regressions. Its complexity is both its strength (capability) and weakness (fragility).

### 4. Shared Technical Focus Areas

The following requirements are emerging across multiple projects, indicating top-of-mind concerns for the ecosystem.

| Focus Area | Projects Involved | Specific Needs |
| :--- | :--- | :--- |
| **Memory Architecture & Security** | **OpenClaw**, **NanoBot**, **Hermes Agent**, **ZeroClaw** | Trust tagging by source (#7707), memory hygiene doctor (#77447), persistent memory parity (ZeroClaw #8891), Dream system reliability (NanoBot). |
| **Approval & Governance Hardening** | **Hermes Agent**, **IronClaw**, **OpenClaw**, **CoPaw**, **NullClaw** | Structured approval flows (#5885, #969), pre-tool enforcement hooks (#64084), MCP allowlisting (#3037, #5947), offload approval logic (#6054). |
| **Channel & Message Reliability** | **NanoBot**, **Hermes Agent**, **NanoClaw**, **IronClaw**, **NullClaw** | Silent message drops (#2995, #4897), LINE/WhatsApp/Telegram failure recovery, cron delivery issues (#954, #6050), message reordering (#6047). |
| **Context & Token Management** | **OpenClaw**, **NanoBot**, **Hermes Agent**, **IronClaw** | Context length exceeded fallback (#9986), rolling conversation cache (PicoClaw #3229), token leak prevention for small models (#5287). |
| **User-Facing Stability & UX** | **OpenClaw**, **Hermes Agent**, **IronClaw**, **CoPaw** | Migration tool failures (#90213), doctor loop (#77802), persistent error banners (#6050), CJK IME support (#39025). |

### 5. Differentiation Analysis

The ecosystem can be segmented by project focus, target user, and technical architecture.

**By Feature Focus:**
- **Enterprise/Observability:** **IronClaw** is deeply focused on audit systems (audit sink, per-user MCP) and a major architectural rework (NEA-25), suggesting an enterprise-first strategy.
- **GUI/Desktop UX:** **LobsterAI** and **ZeroClaw** are prioritizing desktop user experience (Windows/Mac installers, notifications, collaboration UIs). LobsterAI specifically focuses on the "cowork" use case.
- **Lightweight/Embedded:** **PicoClaw** and **NullClaw** focus on core agent logic with lower resource overhead, targeting embedded or plugin-style use cases.
- **Reference/R&D:** **OpenClaw** leads in foundational architecture for memory and model support, acting as the testbed for new ideas.

**By Target User:**
- **Developers/Integrators:** **ZeroClaw** (WASM plugins, SOP control plane), **Hermes Agent** (cross-platform approval delegation).
- **Power Users:** **OpenClaw** and **NanoBot** (multi-provider, custom memory systems).
- **Non-Technical/Family Users:** **OpenClaw** is beginning to address this with its "Uncle Jim mode" (#77567).

**By Architecture:**
- **Modular/Hub:** **OpenClaw** (large core with plugins).
- **Agent-First:** **NullClaw** (REPL-focused, approval flow).
- **Desktop-First:** **LobsterAI** (Electron-based, cowork streaming).

### 6. Community Momentum & Maturity

The projects can be grouped into three tiers based on activity, community engagement, and stability.

**Tier 1: High Velocity & Mature (Active Stabilization)**
- **OpenClaw**, **Hermes Agent**, **ZeroClaw**: These projects have very large communities (50+ issues/PRs daily), are actively releasing or near-release, and have clear roadmaps. They are in a phase of "stabilizing rapid growth," meaning they are strong but currently dealing with regressions from their own velocity. **ZeroClaw** stands out for having a formal RFC process and milestone planning.

**Tier 2: High Velocity & Maintenance Focus**
- **NanoBot**, **NanoClaw**, **LobsterAI**, **IronClaw**: These projects have a high merge rate and are actively fixing bugs and adding smaller features. They are stable but not in a major release window. **IronClaw** is the exception, showing "bug bash" activity which suggests a period of intense testing before a release.

**Tier 3: Steady & Low Activity**
- **PicoClaw**, **NullClaw**, **Moltis**: These projects show steady but lower volume contributions. They are stable and focused on specific niches. **Moltis** is the quietest, with only a single PR fixing a CaldAV bug.

**Tier 4: Inactive**
- **TinyClaw**, **ZeptoClaw**: No activity, indicating potential abandonment or a pause in public development.

### 7. Trend Signals

The following trends are derived from community feedback, bug reports, and feature requests across the ecosystem, offering strategic value for AI agent developers.

1.  **The "Memory Trust Crisis":** The most significant technical trend is the community's growing awareness of **memory poisoning and adversarial attacks on agent state** (OpenClaw's Memory Trust Tagging is the leading signal). This indicates that as agents persist more data, securing that memory is becoming a primary concern for production deployments.

2.  **The Demand for "Agnostic" Operations:** Users are frustrated by vendor lock-in and platform-specific failures. This manifests across projects as demands for **provider-agnostic memory** (NanoClaw), **provider-agnostic routing** (OpenClaw), and **cross-platform channel support** (Hermes Agent). The market is demanding "write once, run on any LLM."

3.  **From "Conversation" to "Workflow":** The community is moving past simple chat towards structured, automated workflows. Features like **scheduled tasks in templates** (NanoClaw), **SOP control planes** (ZeroClaw), and **cron job reliability** (NullClaw, LobsterAI) show a clear push for agents as reliable, autonomous process runners, not just chat bots.

4.  **Governance as a Feature, Not an Afterthought:** Across the board, projects are embedding **approval flows, tool allowlisting, and audit trails** as core architectural features. The ecosystem is maturing from "let the agent do anything" to "let the agent do what's allowed." This is a critical requirement for enterprise adoption and is a core differentiator.

5.  **Desktop as a First-Class Citizen:** While CLI and cloud deployments are dominant, there is a clear resurgence in **desktop application quality** (LobsterAI's Electron focus, ZeroClaw's macOS Tauri builds, Hermes Aegent's installer fixes). This signals a shift towards making these agent assistants a seamless part of the local desktop environment, not just a cloud service.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

Here is the NanoBot project digest for **2026-07-14**.

---

## NanoBot Project Digest for 2026-07-14

### 1. Today's Overview
The project is currently in a state of high velocity and intense development, with **45 Pull Requests** updated in the last 24 hours (including 18 merged/closed) and a strong focus on fixing regressions introduced by recent architectural changes. There are **13 Issues** updated, with a healthy closure rate (11 closed) suggesting good maintainer responsiveness. The activity is dominated by critical fixes for the Dream memory system, re-architecting channel ownership, and hardening the heartbeat/cron migration. While no new releases were cut today, the sheer volume of merged PRs indicates a major release candidate is likely being assembled.

### 2. Releases
**None** – No new releases were created today.

### 3. Project Progress (Merged/Closed PRs)
Today saw 18 PRs merged or closed, indicating significant forward momentum. Key advancements include:
- **Audit System (PR #4320):** Merged. A new `tools.audit` config module for agent action observability.
- **Dream Fixes:** Critical bugs in the Dream memory system were resolved.
    - **PR #4909:** Fixed Dream ignoring line-ending-only memory diffs (CRLF/LF).
    - **Issues #4894 & #4893:** Fixed bugs where Dream failed to prune base64-encoded session files and where `/dream-log` showed non-Dream commits.
- **Documentation (PRs #4913, #4912):** Updated the README with recent changes and removed a broken Star History embed.
- **WebUI (PR #4914):** Added a new Brazilian Portuguese (pt-BR) locale.
- **Bug Fixes (PR #4882):** Fixed `dream_content_diff()` reporting unchanged empty files as modified.

### 4. Community Hot Topics
The most engaged community discussions center on integration pain points and regression bugs.

- **Issue #4864: [Bug] Endless loop for `<tool_call> <function=complete_goal>`** (3 comments, OPEN): A high-severity bug where the gateway mis-parses a JSON parameter, causing the agent to loop. This is a suspected regression from a recent tool serialization update.
- **Issue #4897: [Bug] Issue with Discord bot integration** (3 comments, CLOSED): A user reported the bot connecting to Discord but failing to receive messages. The issue was closed, likely indicating a fix was identified or configuration issue resolved.
- **Issue #1500: Forced Information-Flow Output** (2 comments, 1 👍, CLOSED): A user requested a "message hierarchy" (like log levels) to suppress verbose tool calls and thinking steps. This highlights a strong user desire for configurable verbosity.
- **Issue #1011: Mattermost Bot** (2 comments, 4 👍, CLOSED): A stale but high-reaction feature request for Mattermost support was closed, signaling it is not currently a priority.

### 5. Bugs & Stability
The stability landscape today is a mix of **regressions (P1)** from recent migrations and **niche integration issues**.

| Severity | Issue # | Summary | Status | Fix PR? |
| :--- | :--- | :--- | :--- | :--- |
| **HIGH** | #4864 | Endless loop caused by gateway tool parameter serialization bug. | **Open** | None linked yet. |
| **HIGH** | #4915 | Heartbeat response evaluation causing regressions after migration to cron. | **Open (PR)** | PR #4915 |
| **MEDIUM** | #4897 | Discord bot online but unresponsive to messages. | Closed | Likely fixed. |
| **MEDIUM** | #4917 | Shell tool on Windows decodes UTF-16 process output incorrectly. | **Open (PR)** | PR #4917 |
| **LOW** | #4894 | `prune_dream_sessions()` fails on new base64-encoded filenames. | Closed | Fixed in mainline. |
| **LOW** | #4893 | `/dream-log` shows non-Dream commits (e.g., manual backups). | Closed | Fixed in mainline. |
| **LOW** | #4887 | Test setup fails because `dev` extras omit `lark-oapi` for Feishu tests. | Closed | Fixed in mainline. |
| **LOW** | #4882 | Dream diff reports unchanged empty files as modified. | Closed | Fixed in mainline. |

### 6. Feature Requests & Roadmap Signals
Recent PRs and issues clearly point to the project's direction for the next minor version.

- **Enhanced Observability (PR #4320 - Merged):** The new Audit Tool (MC-486) is a roadmap signal for enterprise-grade action logging.
- **Voice Channel Support (Issue #4911):** A proposal for a "guarded tool gateway seam" explicitly targets real-time voice channels, suggesting a major new channel type is on the roadmap.
- **Model Preset Binding (PR #4866 - Open):** Persisting model selection to sessions and capturing immutable LLM runtime configs is a significant UX improvement planned for the next release.
- **Channel Architecture Refactor (PR #4908 - Open):** Moving setup and instance ownership to channels is a sign of deep internal restructuring to support multi-instance (e.g., Feishu) and cleaner plugin architecture.
- **Auto-Discovery for Agent Hooks (PR #4878 - Open):** This mirrors the existing plugin pattern, suggesting the team is standardizing the extension system for easier third-party contributions.

### 7. User Feedback Summary
- **Pain Point: Verbose Output (Issue #1500):** A user explicitly requested a "message hierarchy" to filter out internal tool calls, calling it "forced" and annoying. This is a strong signal that the agent's transparency is hurting user experience.
- **Pain Point: Sink Integration (Issues #4897, #192, #1011, #2352):** Users are struggling with several channel integrations: Discord not receiving messages, Feishu not receiving files, and requests for WeChat and Mattermost support. The core software is robust, but channel reliability is a common friction point.
- **Pain Point: Dream System (Issues #4882, #4893, #4894):** The Dream memory system has seen a cluster of bugs this week (empty diffs, wrong logs, failed pruning), eroding user confidence in its reliability.
- **Use Case: Portuguese Localization (PR #4914):** A community-contributed translation shows active adoption from the Brazilian developer audience.

### 8. Backlog Watch
The following items are not new but remain unresolved and require attention.

- **Issue #1599: [CONFLICT] feat(telegram): stream LLM responses** (Open since 2026-03-06): This long-standing PR for Telegram streaming has merge conflicts. It is a highly desired feature and should be reviewed and rebased.
- **Issue #4313: [CONFLICT] Feat(webui): config.json/webui parity** (Open since 2026-06-12): A large PR aiming to close the gap between WebUI settings and the config file. It has conflicts and touches many files, likely stalling review.
- **Issue #4620: add heartbeat trigger command** (Open since 2026-07-01): This PR adds a manual heartbeat trigger. It is a feature request (Issue #3437) that appears stalled despite being community-contributed.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

# Hermes Agent Project Digest — 2026-07-14

## Today's Overview
The Hermes Agent project shows **moderate activity** today with 50 issues updated (25 open, 25 closed) and 50 open PRs (none merged/closed). No new releases are published. The closed issues represent a major cleanup of older bugs, many labeled `sweeper:implemented-on-main`, indicating fixes have landed on the main branch. However, the **50 open PRs with zero merges** suggests a review bottleneck or a focus on maintaining a large development queue. An unusually high number of **P0 and P1 severity bugs** (memory leak, stale session state) were reported today, which may require rapid attention. The 24-hour window also saw a spike in new issue creation (especially around streaming MCP, OOM, and payment failures), signaling emerging reliability concerns.

## Releases
No new releases were published on 2026-07-14. The last known version referenced in issues is **v0.15.1** and **v0.15.2** (PyPI). Users on PyPI reported missing remote-desktop features and locale files compared to git-main installs, suggesting the PyPI package may lag behind the main branch.

## Project Progress
**Closed/Merged Progress (from Issues, not PRs):**  
- **25 issues closed** today — all with the `sweeper:implemented-on-main` label, meaning fixes are already upstream. Key resolved items:
  - **Sidebar session list omission** (#38989) — desktop UX fix for intermittent session hiding
  - **Chinese IME / CJK composer bugs** (#39025, #39231) — send button and text submission fixed for CJK input methods
  - **Docker backend fails on Windows WSL2** (#39143) — working directory issue resolved
  - **`execute_code` permanent approval not persisting** (#39187) — authorization flow fixed
  - **`session_search` auxiliary model config 400 error** (#39078) — missing slot added
  - **Dashboard backup button argument mismatch** (#54801) — will be surfaced in open issues below
  - **`read_file` false "File not found" on interruption** (#63069) — mid-read kill race condition fixed
  - **Installation-path customization for desktop** (#38935) — question with implemented solution
  - **Windows CLI missing `hermes.exe` entry point** (#39185) — installer fix
  - **`locales/` missing from PyPI** (#39105) — i18n raw keys now resolved

**Open PRs (50 total, no merges):**  
While no PRs were merged today, several new PRs targeting today’s bugs were opened:
- **#64087** — Strip empty-content tool_calls assistant messages for DeepSeek compatibility
- **#64081** — Fix Windows console window flashes via CREATE_NO_WINDOW flag
- **#64086** — Interrupt TTS playback on new reply to prevent overlap
- **#64085** — Cron job retry on delivery failure (persistent network/DNS errors)
- **#64084** — PreToolUse enforcement hook for prompt-level rules
- **#64083** — Late-steer fallback ack with context-aware continuation
- **#64082** — Fix Telegram infinite 409 conflict loop
- **#64080** — Invalidate stale housekeeping fallback on substantive tool-only turn (fixes #63860)

## Community Hot Topics
Most active threads by comment count and reactions:

1. **#38989 — [CLOSED] Sidebar session list intermittently omits sessions**  
   6 comments, 3 👍  
   *Context:* Users lost access to recent sessions in the desktop sidebar. High user impact — likely a frequently encountered annoyance. Fix is now on main.  
   [Issue Link](https://github.com/NousResearch/hermes-agent/issues/38989)

2. **#39047 — [CLOSED] Auxiliary compression routes Gemini model to Codex backend**  
   5 comments  
   *Context:* Provider-qualified model slugs (`google/gemini-3-flash-preview`) with `provider: auto` are routed to the wrong backend (Codex) and rejected. Indicates a routing logic gap.  
   [Issue Link](https://github.com/NousResearch/hermes-agent/issues/39047)

3. **#39025 — [CLOSED] Windows desktop: Enter does not submit Chinese IME text**  
   5 comments  
   *Context:* Rich composer draft state remains stale after IME composition, requiring workarounds. Adds to a pattern of desktop input-method bugs (see also #39231).  
   [Issue Link](https://github.com/NousResearch/hermes-agent/issues/39025)

4. **#54801 — [OPEN] Dashboard backup button passes archive path as positional argument**  
   3 comments  
   *Context:* Backup fails silently with "unrecognized arguments" due to CLI flag mismatch. Still open — indicates a regression in the dashboard’s backup UX.  
   [Issue Link](https://github.com/NousResearch/hermes-agent/issues/54801)

5. **#64020 — [OPEN] Payment method failing on free plan**  
   2 comments  
   *Context:* User cannot connect at all because the CLI directs them to a subscription page and their card is declined — even for the **free plan**. Suggests a payment-gateway misconfiguration or unnecessary billing requirement.  
   [Issue Link](https://github.com/NousResearch/hermes-agent/issues/64020)

6. **#63911 — [OPEN] Telegram DM topic mode silently swallows kanban wake events**  
   3 comments  
   *Context:* Critical for Telegram power users — root-lobby gate returns early for events without thread_id, preventing completions.  
   [Issue Link](https://github.com/NousResearch/hermes-agent/issues/63911)

**Underlying Need:** The most active discussions revolve around **input-method support (CJK/IME)**, **provider/routing correctness** (Codex vs. Gemini), and **session/state reliability**. Users are frustrated by inconsistent behavior across platforms (desktop vs. CLI vs. Telegram) — especially around session persistence and event delivery.

## Bugs & Stability
**Today’s new open bugs (ranked by severity):**

| Severity | Issue | Summary | Fix PR Exists? |
|----------|-------|---------|----------------|
| **P0** | #63892 | Gateway OOM: MCP poll loop mistakes a completed future's TimeoutError for a poll timeout, spinning and leaking ~108MB/s of traceback | No |
| **P1** | #63860 | Stale housekeeping fallback survives a later substantive tool-only turn — model returns empty response, older narration is finalized | ✅ #64080 |
| **P2** | #64073 | Streamable HTTP MCP server stuck in keepalive/reconnect loop; `send_ping` times out on ~600s cadence | No |
| **P2** | #63695 | dan-blockers cron delivery/network failures — `APIConnectionError` from OpenAI codex | ✅ #64085 |
| **P2** | #64055 | Dashboard no longer respects auth methods (self-hosted OIDC ignored) | No |
| **P2** | #63069 | `read_file` falsely reports "File not found" when interrupted mid-read (wc -c subprocess killed) | Ported from #63069, likely fixed |
| **P2** | #63849 | Tool-result images never evicted on OpenAI-compatible path — accumulate until OOM | No |
| **P2** | #63940 | Weak local models (sub-8B) reproduce STEER_CHANNEL_NOTE marker template verbatim in tool-calling mode | No |
| **P2** | #63895 | Terminal autoscrolls to bottom even after agent output finishes — blocks history review | No |
| **P2** | #64020 | Payment method failing on free plan card decline | No |

**Notable regressions:**  
- **#64055** — Dashboard auth regression: self-hosted OIDC users forced to Nous Portal login  
- **#64073** — MCP server keepalive loop: likely introduced with recent Streamable HTTP changes  
- **#63892** — Memory OOM: traceback-leak pattern suggests a concurrency bug introduced in polling logic

## Feature Requests & Roadmap Signals
**Today’s new feature requests:**

1. **#63852 — [Feature]: Native fallback-chain readiness check without full agent sessions**  
   *User request:* A command to verify fallback models are actually usable without running an agent session. Current `hermes fallback list` only shows configuration, not runtime usability.  
   *Prediction:* Likely to be implemented in next minor release (0.16.x) as it addresses a common troubleshooting need.

2. **#39020 — [CLOSED] Desktop: Dedicated Providers settings section with per-provider API key management**  
   *User request:* Users want a UI panel for managing providers (enable/disable, key entry) instead of digging into low-level config files. Already implemented on main.  
   *Prediction:* Will appear in next desktop release.

3. **#64084 — PreToolUse enforcement hook for prompt-level rules**  
   *PR:* New hook added for enforcing rules before every tool call, making prompt-level rules resilient to recency bias.  
   *Prediction:* This will move into core agent architecture — a clear roadmap signal for safety/guardrails.

**Roadmap signals from recent contributions:**  
- **Cross-platform approval delegation** (#47863) — PR for native approval routing (WeChat/WeCom → Feishu) — indicates enterprise/team features are being prioritized  
- **Streamable HTTP MCP stability** (#64073, #64061) — multiple fixes in flight for MCP resource handling and keepalive reliability

## User Feedback Summary
**Pain Points (recurring themes):**
- **Desktop input-method support** (#39025, #39231) — Chinese/Japanese/Korean IME users cannot reliably submit text  
- **Session state inconsistency** (#38989, #39178) — sessions hidden from sidebar, `ended_at` not set after graceful disconnect  
- **Installation / packaging gaps** (#39185, #39105, #38919) — Windows missing `hermes.exe`, PyPI missing locales, older Macs blocked by CPU requirements  
- **Provider routing confusion** (#39047, #64055) — Gemini routed to Codex, custom OIDC ignored by dashboard  
- **Payment / onboarding friction** (#64020) — free-plan users blocked by card decline — suggests a UX failure in the subscription flow

**Satisfaction Signals:**
- 25 issues closed with `sweeper:implemented-on-main` suggests rapid bug-fix turnaround
- Multiple users engaged with feature requests (#39020) with positive reactions (👍: 3)
- No repeat reports of the same critical bugs — fixes appear to be effective

## Backlog Watch
**Long-unanswered / frozen Issues that may need maintainer attention:**

1. **#63911 — Telegram DM topic mode: root-lobby gate silently swallows kanban wake events**  
   Posted: 2026-07-13 | Updated: 2026-07-14 | Comments: 3 | No fix PR  
   *Impact:* Core Telegram automation broken for users relying on DM topic mode.  
   [Issue Link](https://github.com/NousResearch/hermes-agent/issues/63911)

2. **#54801 — Dashboard backup button passes archive path as positional argument**  
   Posted: 2026-06-29 | Updated: 2026-07-14 | Comments: 3 | No fix PR  
   *Impact:* Dashboard backup is completely non-functional — `hermes backup <path>` fails with "unrecognized arguments".  
   [Issue Link](https://github.com/NousResearch/hermes-agent/issues/54801)

3. **#64020 — Payment method failing on free plan**  
   Posted: 2026-07-13 | Updated: 2026-07-14 | Comments: 2 | No fix PR  
   *Impact:* New users cannot even access the free plan — likely a critical blocker for adoption.  
   [Issue Link](https://github.com/NousResearch/hermes-agent/issues/64020)

4. **#63184 (if exists, or any long-open P1/P0)**  
   *Note:* No very old P0/P1 issues are visible in the top 30 — suggests active triage. However, the **50 open PRs with zero merges today** indicates a potential review bottleneck that may need maintainer capacity.

5. **#47863 — Cross-platform approval delegation PR**  
   Posted: 2026-06-17 | Updated: 2026-07-14 | No merge activity  
   *Impact:* Enterprise feature stale in review — may need maintainer decision on direction.  
   [PR Link](https://github.com/NousResearch/hermes-agent/pull/47863)

---

**Project Health Summary:** Hermes Agent is actively maintained with rapid bug-fix turnaround (25 issues closed with fix-on-main today). However, the 50 open PRs and P0 memory leak (#63892) signal potential bottlenecks in review and testing. Desktop input-method support remains the top user experience gap.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

# PicoClaw Project Digest — 2026-07-14

## 1. Today's Overview

The PicoClaw project shows moderate activity today with 4 issues and 5 pull requests updated in the last 24 hours. All 4 tracked issues remain open and active, indicating ongoing community engagement around feature requests and bug reports. PR activity is healthy, with one merged/closed PR and 4 open PRs, including a significant fix for model resolution logic and a merged webhook feature. No new releases were published today, but the codebase is seeing steady incremental improvements across caching, provider compatibility, and build tooling.

## 2. Releases

**No new releases today.** The latest release remains unchanged. Two PRs updating Docker base images and removing duplicate `.gitignore` entries suggest maintenance work is ongoing but not yet packaged into a release.

## 3. Project Progress

- **PR #3253 [CLOSED] — `Feat/gateway webhook`** (by tisoga)  
  This PR was merged/closed today. It adds webhook support to the gateway component, enabling external integrations to receive event notifications. Likely impacts the project's extensibility and DevOps workflows.  
  [View PR](https://github.com/sipeed/picoclaw/pull/3253)

- **PR #3254 [OPEN] — `fix(agent): prefer verbatim model matches over provider-alias splits when resolving refs`** (by fabdelgado)  
  A critical fix for `lookupModelConfigByRef` that resolves a bug where provider-alias splits could incorrectly match model references over exact verbatim matches. This improves model resolution reliability, particularly important for users with complex multi-provider setups.  
  [View PR](https://github.com/sipeed/picoclaw/pull/3254)

- **PR #3228 [OPEN] — `fix(anthropic-messages): send SystemParts as system blocks with cache_control`** (by AayushGupta16)  
  Enables Anthropic prompt caching on the `anthropic_messages` provider by correctly serializing `SystemParts` as system blocks with per-block `cache_control` markers. This is a foundational step for #3229.  
  [View PR](https://github.com/sipeed/picoclaw/pull/3228)

## 4. Community Hot Topics

### 🔥 Most Active Discussion
**Issue #3088 — `[Feature] use vodozemac instead of libolm`**  
- 8 comments, 2 👍 reactions  
- Author: pbsds  
- The community is pushing to replace the unmaintained and insecure `libolm` library with `vodozemac` (the official Matrix replacement). The proposal suggests making `libolm` optional at compile time. This has been open since June 9 and is marked `stale` and `priority: high`, indicating strong user desire for cryptographic modernization.  
[View Issue](https://github.com/sipeed/picoclaw/issues/3088)

### 💬 Active Proposal Needing Attention
**Issue #3229 — `Proposal: rolling conversation cache breakpoints for anthropic-messages`**  
- 1 comment, author AayushGupta16  
- Builds on PR #3228 to extend caching beyond the system prompt into conversation history. This is a sophisticated proposal for reducing token costs in agentic workloads by marking cache breakpoints in conversation history. Links to issue #2191.  
[View Issue](https://github.com/sipeed/picoclaw/issues/3229)

## 5. Bugs & Stability

**Medium severity: Missing `thought_signature` error with Gemini via OpenAI compat format**  
- **Issue #3230 [OPEN, stale]** — When using Gemini in OpenAI-compatible format via Cloudflare AI Gateway with tool use, Gemini returns a missing `thought_signature` error. Affects versions 0.2.9 through 0.3.1. No fix PR linked yet.  
[View Issue](https://github.com/sipeed/picoclaw/issues/3230)

**Low severity: Model resolution ambiguity**  
- **PR #3254 [OPEN]** — Fixes a bug where model references could be incorrectly resolved via provider-alias splits instead of exact verbatim matches. A fix PR exists and is open.  
[View PR](https://github.com/sipeed/picoclaw/issues?q=is%3Aissue+is%3Aopen+label%3Abug)

## 6. Feature Requests & Roadmap Signals

| Feature Request | Issue # | Community Signal | Likelihood for Next Release |
|---|---|---|---|
| Replace libolm with vodozemac | #3088 | High (priority: high, 8 comments, 2 👍) | Moderate – blocking dependency, but stale since June |
| SearXNG with basic auth header | #3231 | Low (1 comment, 0 👍) | Low – niche feature |
| Anthropic conversation history caching | #3229 | Medium (links to fix PR, 1 comment) | Moderate – actionable with PR #3228 merged |
| Gateway webhook support | #3253 | Merged | ✅ Already shipped today |

**Prediction:** The vodozemac migration (#3088) may land in the next minor release given its high priority tag, particularly if maintainers un-stale the issue. Conversation caching for Anthropic (#3229) is the most technically mature proposal with an active PR foundation.

## 7. User Feedback Summary

- **Pain point: Token cost in agentic workloads** – Issue #3229 and PR #3228 reflect user frustration with high API costs from re-sending conversation history on every LLM call. The caching proposal directly addresses this.
- **Pain point: Insecure dependencies** – Issue #3088 highlights user demand for cryptographic hygiene; `libolm` being unmaintained is unacceptable for production deployments.
- **Integration friction** – Issue #3230 shows that Gemini + Cloudflare AI Gateway with tool use is broken, affecting users who want multi-provider workflows. No fix yet.
- **Positive signal:** The webhook feature (#3253) was merged, suggesting the project is responsive to community needs for extensibility.

## 8. Backlog Watch

⚠️ **High priority, 34 days open, stale**  
**Issue #3088 — `[Feature] use vodozemac instead of libolm`**  
- Status: Open, stale, `priority: high`  
- 8 comments, 2 👍 – significant community interest  
- No assigned maintainer or linked PR  
- This is the most important backlog item needing maintainer attention. The `stale` label combined with `priority: high` suggests it has been deprioritized despite strong user demand.  
[View Issue](https://github.com/sipeed/picoclaw/issues/3088)

⚠️ **7 days without maintainer response**  
**Issue #3229 — `Proposal: rolling conversation cache breakpoints for anthropic-messages`**  
- Author AayushGupta16 has contributed the enabling PR (#3228) but the proposal issue has no maintainer acknowledgment.  
[View Issue](https://github.com/sipeed/picoclaw/issues/3229)

⚠️ **8 days open, no maintainer activity**  
**Issue #3231 — `[Feature] SearXNG basic auth`**  
- Built-in search engine authentication request with no maintainer response.  
[View Issue](https://github.com/sipeed/picoclaw/issues/3231)

---

**Project Health Summary:** Steady development with a healthy PR/issue ratio. Community is actively contributing both feature proposals and fixes (5 PRs today). The main risk is the prolonged stalling of the high-priority `vodozemac` migration. The merged webhook feature and the pending Anthropic caching improvements indicate the project is evolving toward more production-ready, cost-efficient agent workloads.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

# NanoClaw Project Digest — 2026-07-14

## 1. Today's Overview
NanoClaw had a **highly productive day** with 33 PRs updated and 27 merged/closed, indicating a major push toward stability and feature completion. Three security-related issues were closed, suggesting active vulnerability remediation. No new releases were published, so these changes are still in the development branch. The project shows strong maintainer engagement and a steady stream of contributions across bug fixes, security hardening, and new feature development.

## 2. Releases
**No new releases** were published today. The latest available version remains the previous release (not specified in data).

## 3. Project Progress — Merged/Closed PRs
A total of **27 PRs were merged or closed** in the last 24 hours. Key advancements include:

- **Security & Approval Flow Fix** — PR #2998 (`fix(self-mod): render full MCP server payload on the approval card`) closes the approval-smuggling vulnerability by showing `args` and `env` on the approval card. This is the most critical fix today.
- **Channel Delivery Stability** — Multiple PRs addressed silent message drops: PR #2996 (`fix(delivery): route missing-adapter messages into the retry path`) and PR #2226 (`fix(host): throw on missing channel adapter`) ensure offline adapters don't silently mark messages as delivered. Issue #2995 is also resolved.
- **New Channel Support** — Two PRs add **Dial** (SMS + AI voice calls) as a first-class channel: PR #3032 (adapter) and PR #3033 (setup wizard integration). This expands NanoClaw's communication reach.
- **Scheduled Tasks in Templates** — PR #3022 (`feat: support scheduled tasks in templates`) enables templates to define recurring cron-triggered agent prompts, a significant feature for automation.
- **CLI Fixes** — PR #2743 fixes `ncl wirings create` dropping agent destinations; PR #2938 ensures proper ACL row creation for wiring.
- **Script & Diagnostics** — PRs #1889 and #1887 harden cleanup scripts (sqlite3 failure handling) and diagnostics (honoring `DO_NOT_TRACK`).
- **Provider Stability** — PR #2120 generalizes provider error substitutions; PR #2906 adds instance-wide default agent provider.

## 4. Community Hot Topics
**No issues or PRs had explicit comment counts** reported (all show `Comments: 0` or `Comments: undefined`). However, the **highest-priority topics** based on security criticality and author/core-team involvement are:

- **Security Issue #2827 / #2762** — The `add_mcp_server` approval-smuggling vulnerabilities (closed, fixed by PR #2998). These attracted attention from security researcher YLChen-007 and represent the most significant community concern today.
- **Bug #2995** — Offline channel adapters silently marking messages as delivered. Fixed by PR #2996 and PR #2226. The author (glifocat) is a core-team contributor.
- **Open feature PRs (3 active)** — PR #3036 (`fix(agent): inject current_time into context header`), PR #3037 (`feat(container): optional MCP tool allowlist`), and PR #3012/3013 (provider-agnostic persistent memory). These are still under review.

**Underlying need**: The community is demanding both security hardening (approval transparency) and reliability (no silent message drops). The large batch of PRs suggests active maintainer-driven development rather than broad community chatter.

## 5. Bugs & Stability
| Severity | Bug Description | Status | Fix PR |
|----------|----------------|--------|--------|
| **Critical** | MCP server approval flow hides `args` and `env`, enabling approval smuggling (CVE-like issue #2827) | Closed | PR #2998 merged |
| **High** | Outbound messages to offline channel adapters marked as delivered without sending (Issue #2995) | Closed | PR #2996 merged |
| **Medium** | Cleanup script silently treats sqlite3 failures as "no active sessions" (related to #1825) | Closed | PR #1889 merged |
| **Low** | Diagnostics skips `DO_NOT_TRACK` and `curl` missing check (PR #1887) | Closed | PR #1887 merged |
| **Open** | `ncl` socket transport has no timeout/frame cap (PR #2802) | **Open** | Needs merge |
| **Open** | Agent confuses day-of-week and hour on scheduled-task turns (PR #3036) | **Open** | Under review |

All time-critical bugs have fix PRs merged. The two open PRs (#2802 and #3036) are non-blocking features/stability improvements.

## 6. Feature Requests & Roadmap Signals
- **Provider-Agnostic Persistent Memory** — PR #3012 (open, by amit-shafnir) adds shared memory trees across providers. PR #3013 provides Codex integration. This is a major architectural addition likely for the next release.
- **MCP Tool Allowlist** — PR #3037 (open, by romanbsd) adds `NANOCLAW_MCP_TOOL_ALLOWLIST` for fine-grained tool access control. Expect this in next minor release.
- **Scheduled Tasks in Templates** — PR #3022 (merged) enables recurring cron-triggered agent prompts. This significantly enhances automation use cases and will ship in the next release.
- **Time Injection into Context** — PR #3036 (open) adds current time and weekday to agent context, addressing a common agent confusion. Likely included soon.
- **Dial Channel** — PRs #3032/#3033 (merged) add SMS/voice calls via Dial. Already merged, so will be in next release.
- **Structured Skill Format** — PR #3035 (merged) makes channel installs self-describing via SKILL.md. A foundational change for extensibility.

**Prediction**: The next release (likely 0.12.x or similar) will include: Dial channel, scheduled tasks in templates, structured skills, persistent memory (if PRs merge), and MCP allowlisting.

## 7. User Feedback Summary
**Direct user feedback is limited** in this data snapshot (comments=0 for all issues/PRs). However, inferred pain points from code changes:

- **Pain:** "Offline channel adapters silently swallow my outbound messages" — fixed in PRs #2996/#2226.
- **Pain:** "I can't control which MCP tools my agents can use" — addressed by open PR #3037.
- **Pain:** "My agent consistently gets the wrong day-of-week on scheduled tasks" — addressed by open PR #3036.
- **Pain:** "Setup scripts fail silently" — addressed by PR #1889 (sqlite3 handling) and PR #1887 (diagnostics).
- **Pain:** "Security risk: MCP server approval doesn't show all parameters" — fixed by PR #2998.

**Satisfaction signals**: The active PR stream (33 items) and 27 merges suggest maintainers are responsive to these pain points. The security issues were handled within weeks of reporting (June 14/21 → July 13 fix).

## 8. Backlog Watch
- **Open Socket Security PR #2802** — `fix(security): ncl socket hardening (client timeout/cap + server fail-closed/frame-cap)` by sturdy4days. Created June 17, still open after 27 days. **Needs review/merge** — this addresses a denial-of-service vector where the socket transport can hang indefinitely.
- **Open Memory Features** — PR #3012 and #3013 (amit-shafnir, created July 10). These are large architectural changes that may need more review time.
- **Open Agent Time Fix** — PR #3036 (mcaldas, created July 13). Recently opened; may require maintainer feedback.
- **No long-unanswered issues** — All 3 issues updated in the last 24h are closed. No stalled community issues identified.

**Risks**: The Open PRs are all from core-team/regular contributors, so the backlog is healthy — no abandoned community contributions. The main concern is PR #2802's 27-day wait time for a security fix.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

# NullClaw Project Digest — 2026-07-14

## 1. Today's Overview
No new issues were opened or closed in the last 24 hours, and no releases were published. However, **12 pull requests received updates**, all remaining open, signaling active development and review cycles. The project shows steady progress with a focus on agent CLI improvements, channel authentication hardening (Weixin, Teams, Matrix), and memory subsystem configurability. The absence of merged/closed PRs today suggests maintainers are conducting thorough reviews before merging.

## 2. Releases
**None.**  
No new releases were published. The latest available release remains unchanged.

## 3. Project Progress
No pull requests were merged or closed today. The following open PRs received updates and represent active work:

- **Agent CLI & REPL** — #970 (`fix(cli): handle arrow keys in agent REPL`) adds a raw-mode line editor for interactive terminal sessions, supporting cursor navigation, history, and key bindings.
- **Agent Approval Flow** — #969 (`feat(agent): structured approval_request / approval_response flow`) implements a two-turn tool approval mechanism via SSE for the shell tool.
- **Matrix Reliability** — #968 (`fix(matrix): persist next_batch across restart + test env isolation`) prevents full re-syncs on every restart by persisting the sync cursor.
- **Android HTTP** — #966 (`fix(http): secure buffered curl fallback on Android`) improves DNS resolution on Termux by routing all traffic through curl when `std.http` fails.
- **Streaming Tool Calls** — #964 (`Enable native API-level tool calls during streaming`) preserves structured tool-call deltas in `StreamChatResult` for execution during streaming.
- **Weixin Auth** — #963 (`fix(channels): document and harden Weixin iLink QR auth`) documents and hardens the QR authorization flow.
- **Anthropic Provider Docs** — #962 (`docs(providers): document native Anthropic provider with API key and OAuth support`) adds configuration docs for direct Anthropic API usage.
- **Memory Config** — #961 (`feat(memory): add configurable auto-recall, recall_limit, max_context_bytes`) adds three new config keys for finer control over memory recall.
- **Cron Persistence** — #959 (`fix(cron): persist paired token for scheduler tool access (#839)`) stores paired bearer tokens encrypted via `SecretStore` for cron job execution.
- **Teams Auth Fix** — #958 (`fix(teams): accept lowercase serviceurl JWT claim and raise JWKS fetch cap`) fixes a 403 error on MS Teams inbound messages.
- **One-shot Cron Fix** — #954 (`Fix: one-shot cron jobs silently fail to deliver messages`) addresses a use-after-free bug causing silent delivery failures.

## 4. Community Hot Topics
No issues or PRs have received new comments or reactions in the last 24 hours. Based on ongoing updates, the most active PRs are:

- **[#970](https://github.com/nullclaw/nullclaw/pull/970) — Arrow keys in REPL** — High interest in enhancing the interactive agent experience.
- **[#969](https://github.com/nullclaw/nullclaw/pull/969) — Structured approval flow** — Addresses a core safety/UX need for tool execution control.
- **[#961](https://github.com/nullclaw/nullclaw/pull/961) — Memory config options** — Users likely want tuning knobs for memory recall limits and context size.

Underlying need: users are seeking more robust interactive control (REPL), safer tool execution (approval), and better memory management.

## 5. Bugs & Stability
No new bugs were reported today. However, several existing fixes remain open:

| Severity | Bug | Status | Fix PR |
|----------|-----|--------|--------|
| **High** | One-shot cron jobs silently fail to deliver messages (use-after-free) | Open, fix proposed | [#954](https://github.com/nullclaw/nullclaw/pull/954) |
| **Medium** | Matrix full re-sync on restart (lost `next_batch`) | Open, fix proposed | [#968](https://github.com/nullclaw/nullclaw/pull/968) |
| **Medium** | MS Teams 403 due to lowercase `serviceurl` claim | Open, fix proposed | [#958](https://github.com/nullclaw/nullclaw/pull/958) |
| **Low** | Android DNS resolution failure with `std.http` | Open, workaround via curl | [#966](https://github.com/nullclaw/nullclaw/pull/966) |

No regressions or crashes were reported today.

## 6. Feature Requests & Roadmap Signals
While no new feature requests were filed today, the following PRs indicate roadmap direction:

- **Configurable Memory** (#961) — `auto_recall`, `recall_limit`, `max_context_bytes` — likely to land in next minor version, giving users more control over memory behavior.
- **Streaming Tool Calls** (#964) — Enables execution of API-level tools during streaming responses, which is critical for real-time agent interactions.
- **Native Anthropic Provider** (#962) — Official docs for direct Anthropic API usage, including OAuth/pro-plan detection, suggests expanding provider support beyond OpenRouter.
- **Approval Flow** (#969) — Structured two-turn approval is a significant UX and safety feature for production deployments.

**Prediction:** The next release will include memory configurability, the approval flow, and the cron persistence fix.

## 7. User Feedback Summary
No user feedback was submitted in the last 24 hours. Based on open PRs, recurring pain points include:

- **Unreliable cron execution** — One-shot jobs not delivering messages (#954) undermines trust in scheduling.
- **Matrix sync waste** — Full re-sync on every restart (#968) consumes bandwidth and time.
- **Teams integration broken** — 403 errors (#958) block MS Teams usage entirely for some users.
- **Lack of control over memory** — No way to limit context size or disable auto-recall (#961) leads to token waste in large conversations.

Satisfaction appears moderate, with active contributions from maintainers addressing these issues.

## 8. Backlog Watch
No issues or PRs have gone unanswered for extended periods. All 12 open PRs have been updated within the last ~30 days, with the oldest (#954) from June 13. Maintainers appear to be actively reviewing all submissions.

**Items that may need attention:**
- [#954](https://github.com/nullclaw/nullclaw/pull/954) (cron fix) — Open for over a month, critical for scheduling reliability.
- [#956](https://github.com/nullclaw/nullclaw/pull/956) (Alpine dependency bump) — Low risk, probably safe to merge.

No stale issues were identified in this snapshot.

---

*Generated from GitHub data retrieved 2026-07-14 00:00 UTC. Data reflects last 24 hours of activity.*

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

# IronClaw Project Digest
**Date: 2026-07-14**

## Today's Overview

IronClaw is experiencing a period of intense development activity and bug bash triage. With 34 issues updated in the last 24 hours (28 still open) and 50 PRs updated (34 open, 16 merged/closed), the project shows high contributor engagement. A major bug bash event appears to be underway, with 20+ new `P2` and `P3` severity issues filed in the last 24 hours, predominantly by user `joe-rlo`. The project also has three large PR stacks making significant architectural changes, including the NEA-25 unified extension model (8-PR roll-up), per-user MCP registration, and an offline v1-to-Reborn migration workflow. No new releases were published today.

## Releases

No new releases were published in the last 24 hours.

## Project Progress

The following PRs were merged or closed today, representing tangible progress:

**Closed/Merged (16 total):**
- **#6062** — `feat(matrix): add Reborn channel skeleton` ([nearai/ironclaw #6062](https://github.com/nearai/ironclaw/pull/6062)) - Adds a loadable WASM Matrix channel component shape, enabling a new communication channel
- **#6058** — `build(reborn): ship extension ownership migration` ([nearai/ironclaw #6058](https://github.com/nearai/ironclaw/pull/6058)) - Ships explicit extension-ownership migration binary in the Reborn Railway runtime image
- **#6021** — `build(deps): bump the everything-else group with 22 updates` ([nearai/ironclaw #6021](https://github.com/nearai/ironclaw/pull/6021)) - Automated dependency updates
- **#5971** — `fix: carry storage error cause when compaction summary persistence fails` ([nearai/ironclaw #5971](https://github.com/nearai/ironclaw/pull/5971)) - Fixes error cause propagation in compaction persistence
- **#5957** — `fix(reborn): harden OAuth and per-user extension lifecycles` ([nearai/ironclaw #5957](https://github.com/nearai/ironclaw/pull/5957)) - Combines Slack OAuth fixes with generic extension-removal cleanup
- **#5891** — `[bug_bash_P3] "Last completed" displays active run timestamp` — closed as issue
- **#5860** — `Tool activity details only appear after tool call completes` — closed as issue
- **#5953** — `Channel disconnect on extension removal is broken for generic ExternalChannel extensions` — closed as issue
- **#5883** — `[bug_bash_P2] Generic "model output could not be used" error after successful tool execution` — closed as issue

Key architectural advances in open PRs: The NEA-25 unified extension model ([#6061](https://github.com/nearai/ironclaw/pull/6061)), per-user MCP registration ([#5970](https://github.com/nearai/ironclaw/pull/5970)), and v1-to-Reborn migration workflow ([#5936](https://github.com/nearai/ironclaw/pull/5936)) remain active.

## Community Hot Topics

**Most active Issues:**

1. **#5948** — `[bug_bash_P3] Assistant incorrectly reports GitHub extension as activated when it is only installed` ([Issue #5948](https://github.com/nearai/ironclaw/issue/5948))  
   5 comments. The assistant misleadingly reports GitHub extension as fully operational when it's only installed but not activated. This represents a UX trust issue where users may attempt operations that will fail.

2. **#6050** — `[bug_bash_P3] Conversation history error banner displayed despite successful chat response` ([Issue #6050](https://github.com/nearai/ironclaw/issue/6050))  
   2 comments. A persistent error banner damages user confidence even when chat is working. A fix PR (#6064) was opened today to address this.

3. **#5640** — `Harness gap: no RecordingSecurityAuditSink double — hook_security_audit_sink always None in integration harness` ([Issue #5640](https://github.com/nearai/ironclaw/issue/5640))  
   2 comments. Critical testing infrastructure gap where production-security wiring is not replicated in integration tests.

4. **#5741** — `builtin.http.save can fail with OutputTooLarge instead of saving large responses` ([Issue #5741](https://github.com/nearai/ironclaw/issue/5741))  
   2 comments. A key tool fails silently for large web pages, impacting user ability to save content.

5. **#6000** — `How should security issues be reported?` ([Issue #6000](https://github.com/nearai/ironclaw/issue/6000))  
   1 comment from external reporter. No SECURITY.md exists and private vulnerability reporting is disabled — a process gap that could deter responsible disclosure.

**Most active PRs:**
- **#6064** — `fix: clear stale chat history load banner` ([PR #6064](https://github.com/nearai/ironclaw/pull/6064)) - Direct fix for #6050, opened today
- **#5970** — `feat(reborn): per-user MCP registration store` ([PR #5970](https://github.com/nearai/ironclaw/pull/5970)) - Major architectural feature with 14 files of changes
- **#6061** — `feat(reborn)!: unified extension model — NEA-25 Train A roll-up` ([PR #6061](https://github.com/nearai/ironclaw/pull/6061)) - 8-PR roll-up representing a significant rearchitecture

## Bugs & Stability

**P1 (Critical):**
- **#5943** — `[bug_bash_P1] Slack DM action posts to current channel instead of user's direct messages` ([Issue #5943](https://github.com/nearai/ironclaw/issue/5943)) — Privacy/functional bug; Slack messages leak to wrong recipients. No fix PR identified.

**P2 (High):**
- **#5836** — `[bug_bash_P2] Routine fails on every scheduled run with "No thread attached"` ([Issue #5836](https://github.com/nearai/ironclaw/issue/5836)) — 0% success rate for routine executions
- **#6060** — `[bug, created_by_ironclaw] Routine delivery target leaks across all routines` ([Issue #6060](https://github.com/nearai/ironclaw/issue/6060)) — Global default delivery target contaminates per-routine settings
- **#6048** — `[bug_bash_P2] Agent run fails because model attempts to call an unavailable tool` ([Issue #6048](https://github.com/nearai/ironclaw/issue/6048)) — Multi-step workspace tasks fail mid-execution
- **#6047** — `[bug_bash_P2] Task messages are processed and displayed out of chronological order` ([Issue #6047](https://github.com/nearai/ironclaw/issue/6047)) — Conversation flow broken by message reordering
- **#6046** — `[bug_bash_P2] Simple email-to-sheet workflow invokes excessive number of tools` ([Issue #6046](https://github.com/nearai/ironclaw/issue/6046)) — 124 tool invocations for a simple task, performance/stability concern
- **#6045** — `[bug_bash_P2] Agent diagnoses root cause instead of accomplishing the user's intent` ([Issue #6045](https://github.com/nearai/ironclaw/issue/6045)) — Agent fails to auto-retry trivial fix, degrading autonomy
- **#6044** — `[bug_bash_P2] Enter key sometimes does not submit message in WebUI` ([Issue #6044](https://github.com/nearai/ironclaw/issue/6044)) — Intermittent UI input failure
- **#6043** — `[bug_bash_P2] GitHub connection flow fails with generic capability error` ([Issue #6043](https://github.com/nearai/ironclaw/issue/6043)) — Authentication flow broken after token detection
- **#5885** — `[bug_bash_P2] Approval notification opens action without showing the approval message` ([Issue #5885](https://github.com/nearai/ironclaw/issue/5885)) — Approval workflow broken
- **#5879** — `[bug_bash_P2] Stale error banner remains visible after successful follow-up response` ([Issue #5879](https://github.com/nearai/ironclaw/issue/5879)) — UI state management regression
- **#5707** — `[bug_bash_P2] Routine creation response exposes internal implementation details` ([Issue #5707](https://github.com/nearai/ironclaw/issue/5707)) — Information disclosure via UI

**P3 (Medium):**
Issues #5948, #6050, #6051, #6049, #6052, #5889, #6028, #6037, #6039 — Various UI/UX bugs including display issues, slow loading, incorrect iconography, theme problems, and hidden connection status.

**Notable:** Multiple P2 bugs have direct fix PRs already open (#6064 for #6050) or were closed today (#5883, #5953), showing responsive bug bash triage. However, several P2 bugs (#5836, #5943, #6048) lack identified fixes.

## Feature Requests & Roadmap Signals

**Active architectural features in development:**
1. **NEA-25 Unified Extension Model** ([#6061](https://github.com/nearai/ironclaw/pull/6061)) — 8-PR roll-up reworking how extensions are registered, discovered, and managed. Includes retiring `slack_bot` and `slack_personal` in favor of a single `slack` extension. Expected to significantly impact the product taxonomy.
   
2. **Per-user MCP Registration Store** ([#5970](https://github.com/nearai/ironclaw/pull/5970)) — T1 of the MCP registration stack, enabling per-user MCP server management. Likely to ship in next major release.

3. **Offline v1-to-Reborn Migration Workflow** ([#5936](https://github.com/nearai/ironclaw/pull/5936)) — Complete workflow for migrating v1 installations to Reborn, including Docker support. Indicates production rollout is approaching.

4. **Matrix Channel Support** ([#6062](https://github.com/nearai/ironclaw/pull/6062), merged) — New communication channel skeleton added, indicating third-party channel expansion.

5. **Tools-Capable Completion Nudge** ([#6013](https://github.com/nearai/ironclaw/pull/6013)) — Interactive coding improvements with tool-aware steering.

**User-requested features from issues:**
- **#6000** — Security reporting mechanism (SECURITY.md, private vulnerability reporting)

## User Feedback Summary

**Real pain points from bug bash (user `joe-rlo`):**
- **Persistent error banners** that don't clear after success (#6050, #5879) — undermines user trust in system status
- **Authentication flow breakage** (#6043, #5882) — Slack and GitHub connections enter unrecoverable states without clear error messages
- **Incorrect status reporting** (#5948) — System claims capabilities that aren't actually available
- **Chronological ordering issues** (#6047) — Message display inversion breaks conversation flow
- **Excessive tool usage** (#6046) — Simple tasks require 124 tool invocations, indicating poor efficiency
- **Agent autonomy gaps** (#6045) — Agent explains problems instead of solving them, defeating purpose of AI assistant
- **Approval workflow broken** (#5885) — Cannot approve/deny actions when clicking notifications
- **Routine failures** (#5836, #6060) — Scheduled tasks fail consistently with delivery target leakage

**External security researcher (user `Anubhav-Koul`):**
- Blocked from responsible disclosure by missing security policy (#6000)

**UI/UX feedback (user `italic-jinxin`):**
- Stray `$` character rendering (#6028)
- Hidden connection status (#6037)
- Light theme color contrast issues (#6039)

## Backlog Watch

**Issues needing maintainer attention:**

1. **#6000** — `How should security issues be reported?` ([#6000](https://github.com/nearai/ironclaw/issue/6000))  
   *Created: 2026-07-11 | Last updated: 2026-07-13 | 0 maintainer responses*  
   External security researcher with a finding blocked by missing SECURITY.md and disabled private vulnerability reporting. **Risk: High** — could lead to uncoordinated disclosure or frustrated reporter.

2. **#5640** — `Harness gap: no RecordingSecurityAuditSink double` ([#5640](https://github.com/nearai/ironclaw/issue/5640))  
   *Created: 2026-07-04 | Last updated: 2026-07-13 | 2 comments from reporters only*  
   Testing infrastructure gap that means integration tests don't validate production security audit wiring. Surfaced by parity guard. No PR identified.

3. **#5741** — `builtin.http.save can fail with OutputTooLarge` ([#5741](https://github.com/nearai/ironclaw/issue/5741))  
   *Created: 2026-07-06 | Last updated: 2026-07-13 | 0 maintainer responses*  
   Core tooling regression that prevents saving common web content. Affects user confidence in agent's web capabilities.

**PRs needing review or attention:**
- **#5598** — `chore: release` ([#5598](https://github.com/nearai/ironclaw/pull/5598))  
  *Created: 2026-07-03 | Updated: 2026-07-13* — Release PR with API breaking changes in `ironclaw_common` and `ironclaw_skills`. Has been open for 11 days without merging, potentially blocking downstream consumers.

- **#5842, #5845, #5847** — NEA-25 stack PRs 3/7, 4/7, 5/7  
  *Created: 2026-07-08 | Updated: 2026-07-13* — Core of the unified extension model rearchitecture. Stack dependencies mean delays propagate; superseded by #6061 but these intermediate PRs remain open.

- **#5936** — `feat(migration): add offline v1-to-Reborn migration workflow` ([#5936](https://github.com/nearai/ironclaw/pull/5936))  
  *Created: 2026-07-10* — Large, high-risk PR with `risk: high` tag. Critical for production rollout but requires careful review.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

# LobsterAI Project Digest — 2026-07-14

## Today's Overview
The project saw exceptionally high activity with **21 PRs updated** in the last 24 hours, of which **19 were merged or closed** and **2 remain open**. No new issues were reported, and no new releases were published. The development velocity indicates a focused push toward stability and polish, with the majority of merges coming from core contributor **fisherdaddy**, who authored 12 of the closed PRs. The project appears to be in a heavy maintenance and hardening phase, particularly around Windows installer reliability, browser resource management, and cowork (multi-agent collaboration) UX refinements.

## Releases
No new releases were published today. The most recent release remains unknown from today's data.

## Project Progress — Merged/Closed PRs Today
The following features and fixes were merged or closed in the last 24 hours:

### Critical Build & Installer Improvements
- **#2327** — [CLOSED] Signed Windows app binaries via internal signing service to prevent security software from freezing the unsigned `LobsterAI.exe`. Fixes a field-deployed installation hang.
- **#2326** — [CLOSED] Implemented self-healing for interrupted `win-resources.tar` extraction on Windows, using a fallback to system `tar.exe` with a 10-minute watchdog.
- **#2323** — [CLOSED] Added an opt-in Windows web installer target (`nsis-web`) that downloads the app package from a CDN, gated by `LOBSTERAI_WEB_INSTALLER`.

### Browser & Resource Leak Fixes
- **#2328** — [CLOSED] Serialized concurrent browser launch/search operations to stop Chrome process leaks.

### macOS & Cross-Platform Fixes
- **#2321** — [CLOSED] Fixed macOS update failure related to `hdiutil`.

### Cowork (Multi-Agent) Enhancements
- **#2318** — [CLOSED] Upgraded desktop notifications: renamed `TaskCompletionNotifier` to `DesktopNotificationManager`, added waiting notifications for permission requests, foreground notification mode, and stale alert tracking.
- **#2324** — [CLOSED] Streamed ordered thinking blocks from OpenClaw per turn, preventing duplicate thinking messages during history reconciliation.
- **#2325** — [CLOSED] Fixed badge/title descender clipping and stabilized the cowork template UI.
- **#2319** — [CLOSED] Revamped homepage quick-action scenarios: replaced "教育学习" with "文档写作" (mapped to docx skill), refreshed PPTX/website prompts, kept chip bar visible after category selection.
- **#2315** — [CLOSED] Connected queued follow-up coordinator to process follow-ups across sessions and while the app is minimized.
- **#2292** — [CLOSED] Stabilized steer follow-up routing with Codex-style queuing, proper session scoping, and streaming state isolation.
- **#2300** — [CLOSED] Supported attachments (files, dragged/pasted files, images) in the steer queue with lightweight snapshots.

### Background Jobs & Scheduling
- **#2320** — [CLOSED] Fixed cron job fast-forwarding: instead of only skipping catch-up, advanced `nextRunAtMs` to the next valid occurrence to prevent replay of missed recurring jobs.

### UI/Build Fixes
- **#2322** — [CLOSED] Optimized file card rendering.
- **#2316** — [CLOSED] Fixed Windows title bar logo compression when sidebar is collapsed with an update badge.
- **#2289** — [CLOSED] Fixed stalled compaction retry maintenance in cowork, added regression tests.

### Stale PRs Merged (from April)
- **#1488** — [CLOSED] Overhauled scheduled task UI with card grid, search/filter, and history browsing.
- **#1494** — [CLOSED] Made skill selection state per-session instead of global.
- **#1323** — [CLOSED] Fixed misleading "input too long" error classification in cowork.

## Community Hot Topics
There were **no comments or reactions** on any PRs or issues in the last 24 hours, indicating a development-driven period without active community discussion. The most notable open PRs remain:

- **#1277** — [OPEN] `dependabot[bot]` PR to bump Electron from 40.2.1 to 43.1.0 and update electron-builder. This PR has been open since **April 2**, suggesting potential compatibility concerns or blocking issues.
  - Link: [PR #1277](https://github.com/netease-youdao/LobsterAI/pull/1277)

- **#1323** — [CLOSED today] `kayo5994`'s fix for cowork error classification, originally opened April 2, was stale for over 3 months before being merged.
  - Link: [PR #1323](https://github.com/netease-youdao/LobsterAI/pull/1323)

## Bugs & Stability

### High Severity
- **Windows Installer Freeze (RESOLVED)** — Security software froze on unsigned `LobsterAI.exe` during first execution, hanging installs in the field. Fixed via **#2327** (explicit binary signing) and **#2326** (self-healing tar extraction with watchdog).

### Medium Severity
- **Chrome Process Leak (RESOLVED)** — Concurrent browser launch/search operations caused Chrome process leaks. Fixed via **#2328** (serialization).
- **macOS Update Failure (RESOLVED)** — `hdiutil` failed during macOS updates. Fixed via **#2321**.
- **Cron Job Replay (RESOLVED)** — Skipping catch-up alone left stale `nextRunAtMs` timestamps, causing missed jobs to replay. Fixed via **#2320**.

### Low Severity
- **Cowork Badge Clipping (RESOLVED)** — Badge/title descender clipping in cowork templates. Fixed via **#2325**.
- **Windows Title Bar Compression (RESOLVED)** — Logo compression when sidebar collapsed with badge. Fixed via **#2316**.
- **Stalled Compaction Retry (RESOLVED)** — Cowork context maintenance not cleared when compaction retry didn't resume. Fixed via **#2289**.

No new bugs were reported today.

## Feature Requests & Roadmap Signals
No new feature requests were filed today. However, the following merged features signal likely roadmap priorities:

- **Web Installer Support** (#2323) — Opt-in Windows web installer suggests future distribution model flexibility.
- **Upgraded Desktop Notifications** (#2318) — Renamed and extended notification manager with foreground mode, indicating a push toward better user engagement.
- **Ordered Thinking Blocks** (#2324) — Streaming OpenClaw thinking per turn improves transparency for agent reasoning.
- **Attachment Support in Steer Queue** (#2300) — Users can now queue follow-ups with files/images during active turns, a quality-of-life improvement for power users.
- **Homepage Quick-Action Revamp** (#2319) — Replaced educational scenarios with document writing, reflecting pivot toward office productivity use cases.

**Prediction**: The next release will likely include the Electron 40→43 bump (#1277), the Windows web installer, and the notification overhaul.

## User Feedback Summary
No direct user feedback was recorded in today's issue/PR data. However, the following pain points were addressed:

- **Windows installation failures** — Users experienced frozen installs due to unsigned binaries and interrupted resource extraction. Both were resolved today.
- **Misleading error messages** — PR #1323 fixed cowork errors misclassifying unrelated `max_tokens` issues as "input too long," which previously confused users with short inputs.
- **Cross-session skill bleeding** — PR #1494 fixed skill selections persisting across sessions, a long-standing UX inconsistency.
- **Cron job reliability** — PR #2320 fixed missed recurring jobs replaying on startup, which would have caused unexpected agent behavior.

## Backlog Watch

### Critical Attention Needed
- **PR #1277** (dependabot, Electron 40→43 bump) — Open since **April 2, 2026** (104 days). This is a significant version jump and may require careful testing before merging. The Electron 43 release contains breaking API changes. Likely blocked by the maintainer resolving compatibility issues.
  - Link: [PR #1277](https://github.com/netease-youdao/LobsterAI/pull/1277)

### Stale Open PRs
- **PR #1323** — [CLOSED today] Had been open for ~103 days before merging. Its closure reduces backlog, but the long staleness suggests review bottlenecks.
- **PR #1488** and **#1494** — [CLOSED today] Both were April-era UI changes merged after months of inactivity.

No other open issues or PRs appear neglected. The project's maintainer team is actively clearing the backlog with today's 19 merges.

---

*Generated from GitHub data for netease-youdao/LobsterAI. All linked items are at `github.com/netease-youdao/LobsterAI`.*

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyagi">TinyAGI/tinyagi</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

Here is the Moltis project digest for July 14, 2026.

---

**Project Digest: Moltis (moltis-org/moltis)**
**Date:** 2026-07-14

### 1. Today's Overview

Project activity remains very low today, with zero new Issues or Releases logged in the last 24 hours. The sole point of movement is a single open Pull Request (#1147) which was last updated yesterday, indicating an ongoing effort to fix a significant functional bug in the CalDAV integration. The absence of new Issues or closed PRs suggests the community may be in a quiet phase, or activity is shifting toward review of the existing open fix. Overall, project health appears stable but idle.

### 2. Releases

No new releases were published in the last 24 hours. The project continues without a formal release tag for the current period.

### 3. Project Progress

No Pull Requests were merged or closed today. The only active PR remains open.

- **PR #1147 (Open):** fix(caldav): honor time range in list_events via server-side calendar-query. Authored by thoscut, this PR has not yet been merged.

### 4. Community Hot Topics

There is only one active community contribution today, which also represents the primary discussion point:

- **PR #1147 - fix(caldav): honor time range in list_events** ([Link](moltis-org/moltis PR #1147))
  - **Activity:** Opened 3 days ago, updated yesterday.
  - **Analysis:** This PR addresses a discrepancy where the `list_events` tool’s `start`/`end` parameters had no effect on any server, despite documentation claiming otherwise. The underlying need is for accurate, server-side filtering of calendar events, which is critical for users relying on Moltis for time management and scheduling automation.

### 5. Bugs & Stability

**Critical Bug (Active, Unmerged Fix):**

- **Bug:** The `list_events` tool in the CalDAV client ignores user-supplied time range parameters. The `_range` parameter was bound but never used, causing the client to always fetch all calendar resources.
  - **Severity:** **High** – This is a functional bug that negates a documented feature, potentially causing excessive data transfer and incorrect results in time-sensitive queries.
  - **Status:** A fix exists in **PR #1147** but has not yet been merged.

No crashes or regressions were reported in the last 24 hours.

### 6. Feature Requests & Roadmap Signals

No new feature requests were submitted today. The only actionable signal is the completion of the fix for CalDAV time-range filtering. Given the critical nature of this fix for users who depend on calendar integrations, it is a strong candidate for inclusion in the next patch release.

### 7. User Feedback Summary

No direct user feedback or pain points were captured today in Issues. However, the content of PR #1147 implies a real user pain point: inconsistency between documented behavior and actual tool performance. Users expecting precise date-range queries in their calendar tools would have experienced unexpected behavior or had to post-filter large datasets.

### 8. Backlog Watch

The project currently has no long-standing unanswered Issues. The primary item requiring maintainer attention is **PR #1147** ([Link](moltis-org/moltis PR #1147)). This open PR has been waiting for 3 days without merge or closure. For an AI agent tool, this represents a regression in documented functionality that should be prioritized for review and integration to maintain trust in the project’s reliability.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

# CoPaw Project Digest — 2026-07-14

## Today's Overview

CoPaw saw **high maintenance activity** on 2026-07-14, with **50 issues and 50 PRs updated** in the last 24 hours, 23 issues closed, and 28 PRs merged/closed. A **patch release v2.0.0.post1** was published. The project is in a **stabilization sprint** following the v2.0.0 launch, with multiple critical regressions being addressed. **Community engagement is intense** — users report significant dissatisfaction with v2.0.0 stability, particularly around tool-call message pairing, context compression, channel integration, and the permission/governance system. Maintainers are responding rapidly with hotfix PRs.

## Releases

- **v2.0.0.post1** (2026-07-14) — [View Release](https://github.com/agentscope-ai/QwenPaw/releases/tag/v2.0.0.post1)
  - **Fix:** Prevent browser autofill on provider search input (#5981)
  - **Fix:** Fix legacy session handling issues
  - **Chore:** Bump version to 2.0.0.post1
  - **⚠️ Migration Note:** No breaking changes; this is a hotfix patch. Users on v2.0.0 are encouraged to upgrade.

## Project Progress

**28 PRs merged/closed** today, with notable advances:

- **Core Stability Fixes:**
  - **#6058** — Flatten offload hint + temporarily disable broken offload mechanism (merged) — directly addresses the orphan `ToolResultBlock` API 400 errors reported by multiple users
  - **#6052** — Fix hint message flattening to prevent orphan `ToolResultBlock` (merged)
  - **#6050** — Flatten background tool hint and yield result events on SSE stream (merged)
  - **#5989** — Multi-layer orphan tool_result message defense (merged) — context compression eviction safety
  - **#6045** — Clear message queue when session is deleted (merged) — fixes a UI state bug where deleted sessions left stale queue data
  - **#6044** — Bridge register_tool to runtime ToolRegistry pipeline (merged) — fixes plugins registered via `api.register_tool()` being invisible to agents at runtime

- **Governance/Security:**
  - **#6054** — Relax no-finding fallback and add global sandbox switch (merged) — reduces low-value approval prompts, adds global sandbox toggle from Console

- **Testing & Quality:**
  - **#6061** — Add unit tests for Ponytail Quality plugin backend (merged)
  - **#5791** — Fix `formatCompact` unit rounding rollover in Console (merged) — fixes display of numbers like 999,999 showing as "1000.0K"

- **Active PRs (open, under review):**
  - **#5953** — Use standard truncation hint for scroll-capped tool results (fixes #5946, #5929, #6009)
  - **#6068** — Preserve session IDs during Scroll history migration
  - **#6067** — More sensitive files & allow read global
  - **#6063** — Bridge frontend tool-guard rules into policy deep scan
  - **#6065** — Remove dead imports/modules and wrong asyncio mark
  - **#6062** — Skip redundant manifest reconciliation to prevent FD exhaustion
  - **#6060** — Update reme-ai dependency to 0.4.1.0
  - **#5927** — Add `errors='replace'` to `_run_command` for GBK compatibility on Chinese Windows
  - **#5069** — Add visual model fallback for text-only primary models (long-running feature)
  - **#6053** — Use readiness endpoint in CLI doctor

## Community Hot Topics

| Issue/PR | Comments | Summary |
|---|---|---|
| [#5996 — Bug: 2.0.0 "MODEL_EXECUTION_ERROR"](https://github.com/agentscope-ai/QwenPaw/issues/5996) | 10 | Orphan `ToolResultBlock` in hint messages → OpenAI 400 error. **Root cause** identified and fixed in #6058, #6052, #6050. |
| [#5961 — Bug: v2.0.0 infinite loop](https://github.com/agentscope-ai/QwenPaw/issues/5961) | 7 | Agent repeatedly writes/deletes files endlessly with qwen3.7-plus. Likely related to tool result truncation or offload issues. |
| [#5947 — Bug: MCP tool allow/deny settings ineffective](https://github.com/agentscope-ai/QwenPaw/issues/5947) | 6 | Even after disabling sub-tools in MCP, agents can still call them. Governance bypass. |
| [#6006 — Bug: Message queue feature missing](https://github.com/agentscope-ai/QwenPaw/issues/6006) | 6 | Users urgently request restoration of message queue functionality lost in v2.0.0. |
| [#5980 — Missing features: SSH Offline, Profiles 404](https://github.com/agentscope-ai/QwenPaw/issues/5980) | 5 | Critical workflow features (SSH Offline, user profiles) return 404 after upgrade from v1.1.12 to v2.0.0. |
| [#6013 — Stability regression vs v1.x and Tencent WorkBuddy](https://github.com/agentscope-ai/QwenPaw/issues/6013) | 5 | User explicitly states v2.0.0 is less stable than v1.x and inferior to competing product. |

**Underlying needs:** Users are experiencing a **cluster of regressions** tied to message format changes, context compression logic, and the new governance system. The most critical pain point is the `role='tool'` 400 error, which breaks all tool-using workflows. There is also significant demand for **restoration of v1.x features** (message queue, SSH offline, profiles) that were dropped in the v2.0.0 redesign.

## Bugs & Stability

Ranked by severity:

| Severity | Issue | Description | Fix Status |
|---|---|---|---|
| **🔴 Critical** | [#5996](https://github.com/agentscope-ai/QwenPaw/issues/5996), [#5986](https://github.com/agentscope-ai/QwenPaw/issues/5986), [#5960](https://github.com/agentscope-ai/QwenPaw/issues/5960), [#5962](https://github.com/agentscope-ai/QwenPaw/issues/5962) | Orphan `tool_result` messages → API 400 errors. Affects all tool-calling agents on OpenAI-compatible APIs. | ✅ Fixed in #6058, #6052, #6050, #5989 |
| **🔴 Critical** | [#6006](https://github.com/agentscope-ai/QwenPaw/issues/6006) | Message queue feature removed in v2.0.0 — users "urgently" request restoration. | ❌ No fix PR |
| **🔴 Critical** | [#5980](https://github.com/agentscope-ai/QwenPaw/issues/5980) | SSH Offline, Profiles returning 404. Core workflow blockers. | ❌ No fix PR |
| **🟡 High** | [#6012](https://github.com/agentscope-ai/QwenPaw/issues/6012) | Desktop python-runtime missing `agentscope` dependency → `auto_memory` failure (Dream feature) | ❌ Unclear |
| **🟡 High** | [#6024](https://github.com/agentscope-ai/QwenPaw/issues/6024) | Dream feature `ModuleNotFoundError` — imports old AgentScope path instead of QwenPaw path | ❌ Unclear |
| **🟡 High** | [#5963](https://github.com/agentscope-ai/QwenPaw/issues/5963) | `execute_shell_command` hard-capped at 60s — longer commands silently offloaded as SUCCESS | ❌ No fix PR |
| **🟡 High** | [#6056](https://github.com/agentscope-ai/QwenPaw/issues/6056) | Background offload kills subprocess immediately, ignoring LLM-provided timeout | ❌ No fix PR |
| **🟡 High** | [#5954](https://github.com/agentscope-ai/QwenPaw/issues/5954) | Error on command: `"Is a directory: '/app/working/workspaces/default/.mcp'"` | ❌ No fix PR |
| **🟡 High** | [#6049](https://github.com/agentscope-ai/QwenPaw/issues/6049) | v2.0.0: Multi-turn conversation eventually fails with `Model 'unknown' execution failed` | ❌ No fix PR |
| **🟢 Medium** | [#5872](https://github.com/agentscope-ai/QwenPaw/issues/5872) | Docker container: Chromium fails due to dbus connection error | ❌ No fix PR |
| **🟢 Medium** | [#6020](https://github.com/agentscope-ai/QwenPaw/issues/6020) | Approval routing wrong: DingTalk approval appears on Desktop, not in DingTalk channel. `approval_level: OFF` ignored for built-in tools. | ❌ No fix PR |
| **🟢 Medium** | [#5788](https://github.com/agentscope-ai/QwenPaw/issues/5788) | Skills list only shows 20 items, scroll-to-load-more broken | ❌ No fix PR |
| **🟢 Medium** | [#5955](https://github.com/agentscope-ai/QwenPaw/issues/5955) | WebUI skills display: only 20 skills shown, disabled skills hidden | ❌ No fix PR |

## Feature Requests & Roadmap Signals

| Request | Issue | Signal Strength | Likelihood |
|---|---|---|---|
| **CIDR support for no-auth host whitelist** | [#6048](https://github.com/agentscope-ai/QwenPaw/issues/6048) | 👤 single user | Low — niche enterprise feature |
| **Visual model fallback for text-only models** | [#5069](https://github.com/agentscope-ai/QwenPaw/pull/5069) | 🔁 open PR, in review | Medium — useful for multi-modal workflows |
| **AgentScope permission control in QwenPaw** | [#5958](https://github.com/agentscope-ai/QwenPaw/issues/5958) | 👤 single user | Low — already partially covered by governance system |

**Prediction for next release:** The immediate priority for v2.0.0.post2/post3 will be **fixing the remaining regressions** — message queue restoration, profile/SSH offline 404s, Docker Chromium dbus error, and the skills list truncation. The governance system UI (approval routing, sandbox toggle) will see incremental improvements per #6054 and #6063.

## User Feedback Summary

**Pain Points (high frequency):**
1. **"v2.0.0 is less stable than v1.x"** — Multiple users (#6013, #5996, #5961, #6006) express frustration that the major version upgrade broke core workflows. One user explicitly compares unfavorably to Tencent's WorkBuddy (#6013).
2. **Tool-call 400 errors break everything** — The orphan `tool_result` bug (#5996, #5986, #5960, #5962) is the most reported issue. Users cannot rely on multi-turn conversations with tools.
3. **Missing features from v1.x** — SSH Offline, Profiles, Message Queue were removed or return 404 (#5980, #6006). Users feel v2.0.0 is a regression in functionality.
4. **Governance/permission system UX problems** — Approval prompts appear in wrong channel (#6020), "auto" mode is too noisy (#5954), MCP tool allow/deny settings are ignored (#5947).
5. **Context compression breaks conversations** — Long sessions with tools inevitably hit API 400 errors (#6049, #5986).

**Positive signals:**
- **Rapid maintainer response** — The close coupling of bug reports and fix PRs (e.g., #5996 fixed within hours by #6058, #6052, #6050) shows strong maintainer commitment.
- **Governance improvements** — PR #6054 relaxes low-value approval prompts and adds global sandbox toggle, addressing common friction.

## Backlog Watch

| Issue | Age | Why It Matters |
|---|---|---|
| [#2439 — Voice message transcription broken](https://github.com/agentscope-ai/QwenPaw/issues/2439) | 108 days (since Mar 28) | **Longest-standing bug** — voice transcription still not working. Updated 2026-07-14 with no maintainer response. |
| [#5872 — Docker Chromium/dbus failure](https://github.com/agentscope-ai/QwenPaw/issues/5872) | 5 days | Blocking `browser_use` in Docker. No PR yet. |
| [#5963 — Shell command hard-capped at 60s](https://github.com/agentscope-ai/QwenPaw/issues/5963) | 3 days | Silently offloads long commands, returning false SUCCESS. Critical for automation. |
| [#5979 — Electron CLI crash on Linux as root](https://github.com/agentscope-ai/QwenPaw/issues/5979) | 2 days | Blocks Linux users from running Electron-based tools. |
| [#5977 — Plugin HTTP routes lost after hot-reload](https://github.com/agentscope-ai/QwenPaw/issues/5977) | 2 days | Zero-downtime reload breaks plugin routing — affects operational reliability. |
| [#6008 — TUI crash on mouse click](https://github.com/agentscope-ai/QwenPaw/issues/6008) | 1 day | Terminal UI unusable with mouse. |

**Maintainer attention needed:** The **voice transcription bug (#2439)** has been open for over 3 months and was updated today — this is a significant gap for accessibility. The **Docker browser_use failure (#5872)** and **shell command timeout bug (#5963)** are blocking enterprise/automation use cases. The **TUI mouse crash (#6008)** is a new regression affecting terminal users.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

# ZeroClaw Project Digest — 2026-07-14

## Today's Overview

ZeroClaw shows high activity with 50 issues and 50 PRs updated in the past 24 hours, indicating a mature project in active development. The v0.8.3 milestone is closing out with all six child trackers closed, while v0.8.4 maintenance planning has begun (target July 31, 2026). Core architectural initiatives continue in parallel, including the SOP (Standard Operating Procedures) control plane, persistent memory subsystem parity, and a governance RFC on work lanes and board automation. One new RFC was opened today proposing to separate conversation history from agent-curated long-term memory. No new releases were published today.

## Releases

No new releases were published on 2026-07-14. The v0.8.3 release appears imminent as its milestone index (#7320) is the last open item, containing only final release validation and publication tasks.

## Project Progress

Only 1 PR was merged/closed today, but 49 remain open with active development. Key areas of progress visible in the PR queue:

- **Matrix progress drafts**: Large PR #8443 (by vrurg) adds single-message streaming for Matrix channel, with progress drafts and tool argument streaming
- **Memory content scanning**: PR #8984 (by Nillth) adds content-screening layer for security at memory write/read boundaries
- **SOP deterministic pipelines**: PR #8979 (by Nillth) adds channel gate prompts with checkpoint edit/revise
- **WASM channel plugins**: PR #8852 (by JordanTheJet) wires the first real caller for installed WASM channel plugins
- **Desktop/macOS release**: PRs #9032 and #9014 improve macOS release builds with dashboard embedding and notarization
- **Documentation**: PR #9050 compacts coding agent guidance; PR #9042 records memory backend ADR-005; PR #8741 adds SOP syntax examples

## Community Hot Topics

1. **[#6808 - RFC: Work Lanes, Board Automation, and Label Cleanup](https://github.com/zeroclaw-labs/zeroclaw/issues/6808)** (14 comments)
   - Governance RFC for routing work without manual maintainer overhead. Status: Accepted, rollout in progress. This is a foundational process change that affects all contributors.

2. **[#6165 - RFC: Prefer lighter ZeroClaw core through external integrations](https://github.com/zeroclaw-labs/zeroclaw/issues/6165)** (9 comments)
   - Proposal to move long-tail integrations toward skills, MCP servers, and plugin-hosted tools. Accepted, with high risk noted. This indicates the project is consciously avoiding bloat.

3. **[#5287 - Local-First Mode for Small Models](https://github.com/zeroclaw-labs/zeroclaw/issues/5287)** (5 comments, 2 👍)
   - Compact mode for local models: reduced prompt bloat, strict parsing, no prompt leakage. This has strong community interest and is accepted with high risk. Likely to land in v0.8.4.

**Underlying need**: The community is pushing for two complementary goals: (1) making the project more maintainable through better governance and leaner core, and (2) improving local/offline usage for small models. Both signal a maturing project that values both developer experience and user accessibility.

## Bugs & Stability

### Critical/Severe

- **[#9035 - Docker Compose gateway loopback-bound bug](https://github.com/zeroclaw-labs/zeroclaw/issues/9035)** (S1 - workflow blocked)
  - Docker Compose "Connection refused" after successful build. Reported today; no fix PR yet. High priority.

- **[#9028 - Ctrl+C on Windows force quits agent](https://github.com/zeroclaw-labs/zeroclaw/issues/9028)** (S2 - degraded behavior)
  - Windows users cannot gracefully stop the agent. No fix PR yet. Reported today.

### Moderate

- **[#9046 - models_cache.json never written](https://github.com/zeroclaw-labs/zeroclaw/issues/9046)** (S2 - degraded behavior)
  - `/model` command reads a file that nothing ever writes. Fix likely needed before v0.8.3 release.

- **[#6548 - Channel runtime replies bypass localization](https://github.com/zeroclaw-labs/zeroclaw/issues/6548)** (S3 - minor)
  - Hard-coded English strings persist despite non-English locale config. No fix PR linked.

### Fix PRs in Flight

- **[PR #9037](https://github.com/zeroclaw-labs/zeroclaw/pull/9037)** — Fixes literal `<eom>` markers leaking into ZeroCode transcript
- **[PR #9029](https://github.com/zeroclaw-labs/zeroclaw/pull/9029)** — Fixes OpenAiResponsesModelProvider incorrectly reporting no vision capability
- **[PR #9040](https://github.com/zeroclaw-labs/zeroclaw/pull/9040)** — Restores foreground startup feedback lost in earlier refactor
- **[PR #8913](https://github.com/zeroclaw-labs/zeroclaw/pull/8913)** — Annotates max-iteration turn stop with visible reason

## Feature Requests & Roadmap Signals

### Likely for v0.8.4 (target July 31)

- **Memory separation RFC** ([#9048](https://github.com/zeroclaw-labs/zeroclaw/issues/9048)): Separate conversation history from long-term memory — opened today, high risk. This is a significant architectural change that would affect runtime, gateway, and channel code.

- **Slack Events API HTTP mode** ([#9022](https://github.com/zeroclaw-labs/zeroclaw/issues/9022)): Optional HTTP Request URL mode for scale-to-zero deploys. Low implementation complexity; likely to land soon.

- **Pairing code GUI surface** ([#8998](https://github.com/zeroclaw-labs/zeroclaw/issues/8998)): Display one-time bind codes in dashboard instead of only logs. High value for onboarding/channel setup.

- **Config validation for peer group channels** ([#8997](https://github.com/zeroclaw-labs/zeroclaw/issues/8997)): Warn on non-existent channel alias references. Simple but impactful UX improvement.

### Longer-term Signals

- **Local-First Mode** ([#5287](https://github.com/zeroclaw-labs/zeroclaw/issues/5287)) continues to gain attention — accepted with high risk, likely blocks behind the memory architecture work.

- **SOP milestone** ([#8288](https://github.com/zeroclaw-labs/zeroclaw/issues/8288)) is nearing 5/5 completion, with PR #8979 adding key deterministic pipeline capabilities. This is a major feature for governance/automation.

## User Feedback Summary

**Positive signals**: The ZeroCode dashboard and web surfaces are getting attention, with Tauri desktop builds being hardened for macOS release (notarization, dashboard embedding). The WASM channel plugin system is now actually functional after PR #8852.

**Pain points reported today**:
- Windows users cannot Ctrl+C to gracefully stop the agent ([#9028](https://github.com/zeroclaw-labs/zeroclaw/issues/9028))
- Docker Compose users hit "Connection refused" due to gateway binding bug ([#9035](https://github.com/zeroclaw-labs/zeroclaw/issues/9035))
- Google Workspace tools reject necessary camelCase methods ([#9044](https://github.com/zeroclaw-labs/zeroclaw/issues/9044))
- Models cache file is never written, breaking model listing ([#9046](https://github.com/zeroclaw-labs/zeroclaw/issues/9046))
- OpenAI vision capability is incorrectly disabled ([#9019](https://github.com/zeroclaw-labs/zeroclaw/issues/9019), fix in PR #9029)

## Backlog Watch

**Issues needing maintainer response**:

- **[#8891 - Persistent memory parity tracker](https://github.com/zeroclaw-labs/zeroclaw/issues/8891)** — Open since July 9 with only 2 comments. This is a major roadmap epic; needs maintainer assignee or status update.

- **[#8288 - SOP milestone tracker](https://github.com/zeroclaw-labs/zeroclaw/issues/8288)** — Open since June 24, tagged `needs-maintainer-review` on several child PRs. Active PRs exist but the tracker itself could use a status comment.

- **[#8691 - ADR baseline restoration](https://github.com/zeroclaw-labs/zeroclaw/issues/8691)** — Open since July 4 with only 1 comment (the author's). Documentation tracker appears to have stalled.

**Older PRs needing attention**:

- **[#8353](https://github.com/zeroclaw-labs/zeroclaw/pull/8353)** — `needs-author-action` since June 26. Improve error message context and replace unwrap with expect. Small, valuable improvement that has stalled.

- **[#9027](https://github.com/zeroclaw-labs/zeroclaw/pull/9027)** — Large XL PR for SOP AMQP dispatch idempotency; risks accumulating merge conflicts if not reviewed soon.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*