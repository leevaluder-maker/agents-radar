# OpenClaw Ecosystem Digest 2026-07-17

> Issues: 500 | PRs: 500 | Projects covered: 13 | Generated: 2026-07-17 01:50 UTC

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

Here is the project digest for **OpenClaw** for **2026-07-17**.

---

## OpenClaw Project Digest: 2026-07-17

### 1. Today's Overview
The OpenClaw project remains in a state of **high activity** with 500 issues and 500 PRs updated in the last 24 hours. The community is heavily engaged in triaging a wave of regressions introduced in the **2026.7.1** release, alongside a long tail of pending architectural enhancements. While no new releases occurred today, the maintainers and community are focusing on critical stability fixes, particularly around gateway startup failures and session state corruption. The project shows a strong throughput of resolved items (197 merged/closed PRs, 172 closed issues), but the volume of open items suggests a significant maintenance burden.

### 2. Releases
**None.**

No new versions were released in the last 24 hours. The project is currently stabilizing the **2026.7.x** line, with many critical bugs filed against `2026.7.1`.

### 3. Project Progress
Today saw **197** PRs merged or closed, indicating a productive day of code integration. Key areas of advancement include:
- **Cross-Platform UI Parity**: A significant feature PR ([#109212](https://github.com/openclaw/openclaw/pull/109212)) adds native inline widget support across iOS, Android, and macOS apps, closing a gap where rich widgets only worked in the Control UI.
- **Session Integrity & Memory**: A major refactor ([#109427](https://github.com/openclaw/openclaw/pull/109427)) moves non-session runtime journals to SQLite, moving away from fragile JSONL files. Another fix ([#103984](https://github.com/openclaw/openclaw/pull/103984)) improves context compaction accuracy for CJK (Chinese, Japanese, Korean) text, preventing excessive context retention.
- **Agent & CLI Tooling**: Experimental CLI commands for "Claw" package management ([#102296](https://github.com/openclaw/openclaw/pull/102296), [#102306](https://github.com/openclaw/openclaw/pull/102306)) are being reviewed, aiming to simplify agent distribution and state management.
- **Security Hardening**: A critical fix ([#109233](https://github.com/openclaw/openclaw/pull/109233)) addresses a bypass in the file-transfer plugin where a `denyPaths` rule could be circumvented by listing the denied directory itself.

### 4. Community Hot Topics
The most active discussions revolve around a few core themes:

- **Linux/Windows Client Demand**: Issue [#75](https://github.com/openclaw/openclaw/issues/75) ("Linux/Windows Clawdbot Apps") remains the most commented issue (113 comments) and a strong signal of unmet user demand for desktop parity.
- **Reliability Regressions**: Two high-severity regressions have intense community engagement:
    - **Codex Turn Completion Stalls**: Issue [#88312](https://github.com/openclaw/openclaw/issues/88312) (20 comments, 5 👍) describes a critical regression where the Codex app-server fails to confirm turn completion, hanging the agent.
    - **Telegram Timeouts**: Issue [#87744](https://github.com/openclaw/openclaw/issues/87744) (15 comments) reports a parallel crash-loop/timeout issue for Codex-backed Telegram sessions.
- **Performance & Cost**: Issue [#94518](https://github.com/openclaw/openclaw/issues/94518) ("DeepSeek cache hit rate <10%") is a highly voted issue (10 👍, 11 comments) indicating significant cost and latency impact from a regression in caching logic.

### 5. Bugs & Stability
The project is facing a **high-severity stability crisis** following the `2026.7.1` release. Several **P0 (release-blocker)** bugs have been reported today:

- **Gateway Crash-Loops**: Two critical issues describe the gateway failing to start entirely:
    - [#107220](https://github.com/openclaw/openclaw/issues/107220): Fatal crash due to legacy memory sidecar conflicts.
    - [#107694](https://github.com/openclaw/openclaw/issues/107694): Gateway fails due to a strict guard on benign migration warnings.
- **Session State Corruption**:
    - [#108238](https://github.com/openclaw/openclaw/issues/108238): Context usage is miscalculated, leading to false "context overflow" errors.
    - [#108233](https://github.com/openclaw/openclaw/issues/108233): The iOS app creates orphan sessions on reconnect.
- **Memory Exhaustion**: PR [#109446](https://github.com/openclaw/openclaw/pull/109446) is being fast-tracked to fix a Codex memory leak where timed-out hooks consume gigs of RAM.
- **Tool Payload Rejection**:
    - [#107449](https://github.com/openclaw/openclaw/issues/107449) (closed): A `cron` tool JSON Schema was incompatible with `llama.cpp`, breaking local LLM users.
    - [#108075](https://github.com/openclaw/openclaw/issues/108075): A similar generic schema rejection error is being reported.

*Note: Many of these bugs have fix PRs already open (e.g., [#109446](https://github.com/openclaw/openclaw/pull/109446) for the memory leak), suggesting a rapid response from the maintainer team.*

### 6. Feature Requests & Roadmap Signals
High-impact feature requests continue to be debated:

- **Security & Sandboxing**: Two related enhancements are gaining traction:
    - **Memory Trust Tagging** ([#7707](https://github.com/openclaw/openclaw/issues/7707)): To prevent prompt injection poisoning of memory.
    - **Filesystem Sandboxing** ([#7722](https://github.com/openclaw/openclaw/issues/7722)): To restrict agent file access. Both are P2 but have high potential for inclusion in a future security-focused release.
- **Agent Observability**: A request for a `/models test-fallback` command ([#6599](https://github.com/openclaw/openclaw/issues/6599)) highlights a desire for better debugging tools.
- **UX Polish**: A feature for configurable `parseMode` for Telegram channels ([#10944](https://github.com/openclaw/openclaw/issues/10944)) and a streaming TTS pipeline for voice calls ([#8355](https://github.com/openclaw/openclaw/issues/8355)) point to ongoing efforts to polish mature integrations.

### 7. User Feedback Summary
- **Frustration**: Users are frustrated by the instability of the `2026.7.1` release. Bug reports like "Control UI is worse" ([#108182](https://github.com/openclaw/openclaw/issues/108182)) and "can't restart the gateway" ([#106920](https://github.com/openclaw/openclaw/issues/106920)) reflect a negative experience with the latest stable upgrade.
- **Dissatisfaction with Documentation Gaps**: The broken `sessionKey` documentation for webhooks (Issue [#11665](https://github.com/openclaw/openclaw/issues/11665)) shows user frustration when promised features don't work as documented.
- **Desire for Autonomy**: Feature requests for agent-triggered compaction ([#6757](https://github.com/openclaw/openclaw/issues/6757)) and masked secrets ([#10659](https://github.com/openclaw/openclaw/issues/10659)) indicate a user base pushing for more autonomous and secure agent capabilities.

### 8. Backlog Watch
Several important issues are languishing without maintainer review, risking becoming blockers for the community:

- **Security Feature Gap**: **Filesystem Sandboxing** ([#7722](https://github.com/openclaw/openclaw/issues/7722)) and **Masked Secrets** ([#10659](https://github.com/openclaw/openclaw/issues/10659)) both carry the `clawsweeper:needs-product-decision` tag, indicating they are stalled at a product strategy level despite clear user demand. The resulting lack of security hardening is a potential bottleneck.
- **Stalled Refactor**: The **Slack agent visibility** bug ([#7359](https://github.com/openclaw/openclaw/issues/7359)) is a long-standing P2 enhancement with no maintainer movement. This creates a "blind spot" for agents on Slack, a major enterprise channel.
- **WebSocket Reconnect Bug**: A critical P1 bug affecting Chinese users where WebSocket reconnects terminate sessions ([#38091](https://github.com/openclaw/openclaw/issues/38091)) is tagged `clawsweeper:needs-live-repro` and has not been resolved since March. This likely causes significant UX friction for a large user segment.

---

## Cross-Ecosystem Comparison

Here is the cross-project comparison report based on the provided community digest summaries.

---

## Cross-Project Comparison Report: Personal AI Agent Ecosystem

**Date:** 2026-07-17
**Analyst:** Senior Analyst, AI Agent Open-Source Ecosystem

### 1. Ecosystem Overview

The personal AI assistant open-source landscape is undergoing a period of intense, bifurcated activity. A tier of large, mature projects (led by **OpenClaw** and **ZeroClaw**) are grappling with post-release stability crises and major architectural refactoring, while a second tier of newer or more focused projects (**NanoBot**, **NanoClaw**, **IronClaw**) are rapidly iterating on feature completeness and channel expansion. A consistent theme across the ecosystem is a **push toward production-grade reliability**, with critical bugs around session state corruption, memory leaks, and channel startup failures dominating discussions. Simultaneously, the community is demanding greater **autonomy and security**, with strong signals for agent-triggered memory management, sandboxing, and multi-provider failover. While the core reference implementation (OpenClaw) remains the most active, several peers are carving out distinct technical niches, particularly in lightweight deployment and enterprise channel integration.

### 2. Activity Comparison

| Project | Issues (Updated 24h) | PRs (Updated 24h) | Release (24h) | Health Signal |
| :--- | :--- | :--- | :--- | :--- |
| **OpenClaw** | 500 | 500 | None | **High Activity / Critical Stress.** Massive throughput, but a high-severity stability crisis post-release. |
| **NanoBot** | 1 | 13 | None | **Focused Sprint.** Low issue count, high PR velocity targeting specific p1 bugs. Healthy. |
| **Hermes Agent** | 50 | 50 | None | **High Activity / Steady State.** Stable throughput with a mix of feature work and bug fixing. |
| **PicoClaw** | 2 | 9 | None | **Maintenance Lull.** Low activity, dependent on dependency bumps. A growing backlog of stale PRs. |
| **NanoClaw** | 4 | 19 | None | **Elevated & Productive.** High PR-to-issue ratio and strong merge rate indicate efficient development. |
| **NullClaw** | 1 | 0 | None | **Dormant / Fragile.** No PR activity. A single critical bug represents a production blocker with no fix. |
| **IronClaw** | 18 | 39 | None | **High Tempo / Refactoring.** Strong engineering investment in late-stage stabilization and new channels. |
| **LobsterAI** | 3 (stale) | 17 | **Yes (v2026.7.16)** | **Release Focused.** High merge rate centered on stabilizing a core feature ("Cowork"). |
| **TinyClaw** | 0 | 0 | None | **Inactive.** No activity in the reporting period. |
| **Moltis** | 0 | 3 | **Yes (20260716.01)** | **Quiet & Stable.** Low public engagement but consistent, focused feature delivery. |
| **CoPaw** | 44 | 46 | None | **High Velocity / Post-Release Firefighting.** Very active, with a strong focus on v2.0 regression fixes. |
| **ZeptoClaw** | 5 (closed) | 0 | None | **Documentation Phase.** No code changes; focused on security audit documentation. |
| **ZeroClaw** | 26 | 50 | None | **Sustained High Velocity / Architectural Shift.** Deep into major refactoring with large RFCs. |

### 3. OpenClaw's Position

- **Advantages vs. Peers:**
    - **Unmatched Community Size & Throughput:** With 500 issues and 500 PRs updated in 24 hours, OpenClaw’s community engagement is an order of magnitude larger than any peer. This provides immense pressure-testing and a vast pool of contributors.
    - **Comprehensive Feature Set:** It is the only project with dedicated discussions on memory trust tagging, filesystem sandboxing, and a "Claw" package manager, signaling a mature roadmap for security and extensibility that others are only beginning to address.
    - **Cross-Platform UI Parity:** A major merged PR has closed the gap on native widgets for iOS, Android, and macOS, a feature few others are actively pursuing.

- **Technical Approach Differences:**
    - OpenClaw is pursuing a **heavy, monolithic-core approach** with a plugin/package ecosystem managed by a dedicated CLI tool ("Claw"). This contrasts with projects like **NanoBot** and **NanoClaw**, which are leveraging a more modular, channel-centric architecture with lighter cores.
    - Its current crisis underscores the risk of this approach: high complexity from a feature-rich core leads to significant regressions after each release.

- **Community Size Comparison:**
    - OpenClaw is the undisputed **ecosystem giant** in terms of raw activity. The closest competitors by volume are **ZeroClaw** (50/50) and **CoPaw** (44/46), which represent 10% and 9% of OpenClaw's issue/PR volume, respectively. This quantifies OpenClaw's dominant, though volatile, market position.

### 4. Shared Technical Focus Areas

A clear set of requirements is emerging across multiple projects, independent of their size or focus:

- **Multi-LLM Provider Fallback & Resilience:**
    - **Projects:** OpenClaw, NanoBot, NanoClaw, Hermes Agent, ZeroClaw.
    - **Specific Need:** Automatic failover when a primary LLM provider hits a quota limit, rate limit, or billing failure. This is a top priority for production deployments. (**NanoClaw** has two competing PRs for this, **ZeroClaw** has an RFC for provider unification).

- **Session State Integrity & Memory Management:**
    - **Projects:** OpenClaw, NanoBot, Hermes Agent, CoPaw, ZeroClaw.
    - **Specific Need:** Fixing issues with context overflow miscalculation, orphaned sessions, memory leaks, and session history corruption. The community is demanding clear separation between conversation history and curated long-term memory.

- **Channel Expansion & Identity:**
    - **Projects:** OpenClaw, NanoClaw, IronClaw, ZeroClaw.
    - **Specific Need:** Integrating new channels (Telegram, WhatsApp, Signal, Dial) and fixing multi-channel identity management. A critical pain point is the confusion caused when running two WhatsApp paths (Cloud vs. Baileys) under the same key.

- **Desktop & Deployment Reliability:**
    - **Projects:** OpenClaw, Hermes Agent, CoPaw.
    - **Specific Need:** Fixing broken desktop apps on Windows, silent WebSocket failures, session state corruption on profile switches, and deployment issues (Docker timezone, ARM64 missing binaries).

- **Security Hardening:**
    - **Projects:** OpenClaw, NanoBot, Hermes Agent, ZeroClaw.
    - **Specific Need:** Filesystem sandboxing, masked secrets, plugin permission models, and fixing bypasses in security rules. The failure of silent startup errors (deceptive "healthy" status) is a common security and reliability concern.

### 5. Differentiation Analysis

| Project | Key Differentiator | Target User | Technical Architecture |
| :--- | :--- | :--- | :--- |
| **OpenClaw** | **The Feature-Rich Reference.** Dominates in feature scope and community size. | Power users and developers wanting all-in-one functionality. | Monolithic core with a tool/package CLI for extensibility. |
| **NanoBot** | **The Lean Bug-Squasher.** Focused, rapid response to bugs and user feedback. | Developers needing a stable, lightweight, and responsive agent. | Modular, with high PR velocity on targeted fixes. |
| **NanoClaw** | **The Channel & Fallback Specialist.** Deep focus on channel adapter reliability and LLM fallback. | Organizations needing robust multi-channel deployment with resilient LLM handling. | Channel-centric with clear PRs for fallback and provider resilience. |
| **IronClaw** | **The Refactored & Scalable Platform.** Undergoing a late-stage shift from monolithic to modular ("Reborn"). | Developers looking for a modern, scalable, and maintainable platform. | Heavy refactoring of a composition crate; focus on WebUI v2 and background services. |
| **CoPaw** | **The Post-Release Stability Champion.** Most active in fixing regressions after a major v2.0 release. | Users migrating from v1.x and needing a stable, reliable experience. | High velocity bug-fixing cycle post-major-version release. |
| **ZeroClaw** | **The Future-Architecture Pioneer.** Deep into major RFCs for memory, providers, and plugins. | Developers and contributors interested in next-gen agent architecture. | Architecturally ambitious, with large, slow-moving RFCs and a plugin runtime stack. |

### 6. Community Momentum & Maturity

- **Tier 1: Rapidly Iterating & High Risk/Reward**
    - **OpenClaw, ZeroClaw, CoPaw:** These projects are experiencing the highest velocity but also the most significant growing pains. OpenClaw and CoPaw are in "firefighting" mode post-release, while ZeroClaw is in a high-risk architectural pivot. This is where the most innovation and the most volatility are concentrated.

- **Tier 2: Focused & Productive**
    - **NanoBot, NanoClaw, IronClaw:** These projects demonstrate healthy, sustainable momentum. They are not as large as Tier 1 but are more efficient, with better signal-to-noise ratios (fewer open issues relative to PRs). **NanoClaw**, with its high merge rate and clear feature focus, is a standout performer.

- **Tier 3: Stabilizing & Mature**
    - **Hermes Agent, LobsterAI, Moltis:** These projects are in a steady state, balancing new features with a stable release cycle. **LobsterAI** successfully shipped a release today, and **Moltis** is a model of a stable, low-drama project.

- **Tier 4: Inactive / Low Engagement**
    - **PicoClaw, NullClaw, TinyClaw, ZeptoClaw:** These projects show signs of low engagement or maintenance. **NullClaw** is fragile with a critical bug and no development activity. **PicoClaw** has a growing stale backlog. **TinyClaw** is inactive. **ZeptoClaw** is in a non-development phase.

### 7. Trend Signals

- **Reliability Trumps Features:** The most urgent user feedback across all major projects is not about new features, but about **broken sessions, silent failures, and memory leaks**. The market is signaling that an agent that works consistently is more valuable than one with many features that break.
- **The Battle for Production-Grade Deployment:** A clear industry trend is the push toward "set it and forget it" automation. Community demands for background services (`launchd`/`systemd`), non-Tauri desktop builds, and robust Docker deployments indicate that users want these agents running as critical, long-lived infrastructure.
- **Multi-Provider & Multi-Modal is the Baseline:** Users no longer expect to be tied to a single LLM. The demand for automatic fallback (quota, rate limits) is a top-tier requirement. Furthermore, the community expects rich input/output: voice calls (TTS), audio tool markers (`[AUDIO:]`), and folder context attachments are now being requested as standard features.
- **Security as a Feature, Not an Afterthought:** The prevalence of issues around sandboxing, masked secrets, and injection prevention—across projects of all sizes—shows that security is becoming a core differentiator. A project's ability to handle permissions granularly and prevent silent data leaks will be key for enterprise adoption.
- **Architectural Divergence:** The ecosystem is fragmenting on approach. OpenClaw and ZeroClaw are betting on complex, monolithic cores with rich plugin systems. In contrast, projects like NanoClaw and IronClaw are succeeding with lighter, more modular architectures that focus on specific, high-value features (channel reliability, background services). The next winning architecture is still undefined.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

# NanoBot Project Digest — 2026-07-17

## Today's Overview
The project saw moderate activity with one open issue and a significant 13 pull requests updated in the last 24 hours, indicating active development despite a release pause. The lone open issue (#4948) highlights a WebUI/subagent lifecycle bug that could affect user experience in complex multi-agent sessions. PR activity is heavily weighted toward p1-priority fixes (8 of 13), suggesting a focused bug-squashing sprint with contributions from 8 different authors. The project maintains strong community engagement with PRs addressing session caching, security hardening, MCP cancellation handling, and provider-level input sanitization.

## Releases
No new releases were published in the reporting period.

## Project Progress
One PR was merged/closed today:
- **#4950** (closed) — `docs(readme): reflect community maintenance` by Re-bin. A documentation-only change updating the README contact section to acknowledge collaborative maintenance with open-source contributors.

## Community Hot Topics
- **Issue #4948** — `WebUI loses visibility when a late subagent completion starts a system turn` (0 comments, 0 reactions). This is the only open issue updated today and addresses a critical UX gap where late-running subagents become invisible in the WebUI after the main turn cycle expires. While currently low engagement, this bug directly impacts multi-agent workflows and is likely to draw attention from power users.
- **PR #4959** — `fix: add one second to retry after delays` by wzrayyy (0 comments, 0 reactions). Addresses recurring rate-limit warnings where provider retries were executing at the exact boundary of the rate window, causing repeated failures. This pragmatic fix has high practical value for users of rate-limited LLM providers.

## Bugs & Stability
All reported bugs are actively addressed with corresponding fix PRs:

**P1 (Critical):**
- **Session memory leak / unbounded cache** — PR #4957 (`fix(session): bound the in-memory session cache`) introduces a 128-entry LRU with weak-reference overflow to prevent memory exhaustion in long-running sessions. Companion PR #4956 caps message history at 2,000 messages at persistence time.
- **WebUI subagent invisibility** — Issue #4948 / PR #4954 (`fix(webui): keep late subagent turns visible`). Preserves WebUI delivery metadata for late-arriving subagent results, assigning fresh turn IDs when a new system dispatch starts.
- **UTF-16 surrogate crashes** — PR #4952 (`fix(providers): sanitize UTF-16 surrogates at provider request boundary`). Blocks UnicodeEncodeError crashes on emoji-heavy content during JSON round-trips to LLM providers.
- **False cancellation signals** — PR #4960 (`fix: preserve real cancellation in MCP paths`). Distinguishes real task cancellation from CancelledError signals leaked by MCP/AnyIO integrations, preventing silent swallow of legitimate cancellations.
- **Rate-limit retry timing** — PR #4959 (`fix: add one second to retry after delays`). Prevents repeated rate-limit failures by adding a 1-second buffer to retry backoff.
- **Docker security** — PR #4955 (`Harden default Docker Compose security`). Removes SYS_ADMIN capability and unconfined AppArmor/seccomp from defaults; adds opt-in bwrap sandbox path.
- **Jina Reader URL leak** — PR #4947 (`fix(web): keep sensitive URLs out of Jina Reader`). Makes third-party readability conversion opt-in to prevent credential/token leakage through URL parameters.

## Feature Requests & Roadmap Signals
- **Nimble search provider** — PR #4951 (`feat(web): add Nimble search provider`) by wildcard adds a new REST-based web search option, following the existing provider pattern. Likely to land in next release given its clean integration.
- **Native folder picker bridges** — PR #4953 (`feat(webui): support native folder picker bridges`) by Re-bin enables external native hosts to advertise folder-picker capabilities through the WebUI bootstrap with tab-scoped token authentication. Targets desktop/WASM deployment use cases.
- **One-click Render deployment** — PR #4937 (`feat: add one-click Deploy to Render support`) by Ho1yShif provides a Render Blueprint for instant cloud deployment with persisted session history and memory. Currently open 3 days; could be merged pending review.
- **zh-TW locale improvements** — PR #4958 (`Improve zh-TW Traditional Chinese locale`) by PeterDaveHello enhances translation quality for Traditional Chinese users.

## User Feedback Summary
Based on issue/PR content, key user pain points include:
- **Rate-limit frustrations**: Users consistently seeing repeated rate-limit warnings where retries execute at exact boundary of rate windows (PR #4959).
- **Session memory bloat**: Long-running sessions cause memory pressure from unbounded history caching, affecting users with extended conversations (PR #4956, PR #4957).
- **Multi-agent visibility gaps**: Complex agent workflows break WebUI rendering when subagents complete after the parent turn expires, causing confusion (Issue #4948, PR #4954).
- **Emoji/Unicode crashes**: Production failures on emoji-heavy content block LLM requests, particularly impacting chat-heavy use cases (PR #4952).

## Backlog Watch
No long-unanswered issues or PRs requiring immediate maintainer attention were identified in the reporting period. The project shows healthy maintainer responsiveness with all open items having recent activity (updated within hours of filing). The older PR #4937 (Render deployment, created July 14) has pending review tag CC @Re-bin and would benefit from review — it represents a significant usability improvement for cloud deployment workflows.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

# Hermes Agent Project Digest — 2026-07-17

## Today's Overview
Today marks a high-activity period for Hermes Agent, with 50 issues and 50 PRs updated in the last 24 hours. The project maintains strong community engagement, with 43 open issues and 44 open PRs reflecting active development and user feedback. Seven issues and six PRs were closed/merged today, indicating steady progress on the codebase. Notably, security and stability concerns are driving significant discussion, particularly around session state isolation, provider compatibility, and desktop app regressions.

## Releases
No new releases today.

## Project Progress
Six PRs were merged or closed today, reflecting focused improvements:

- **#65634 (merged)** — `feat(slack): render structured worker progress` — Adds bounded worker-progress contract for Slack gateway runs, including editable thread-scoped progress cards and sanitized HTTPS preview links.
- **#65925 (merged)** — `fix(cli): only mark speech-to-text messages as voice input` — Fixes a bug where voice mode labeling persisted to all messages while voice mode was active, causing model confusion.
- **#53222 (closed)** — `fix(memory): gate auto recall + scrub inline-echoed recall block` — Addresses the critical memory recall leak where customer‑facing channels could receive internal `<memory-context>` blocks (#40170).
- **#61284 (closed)** — Dashboard "Silent WebSocket" regression fix — Resolves the issue where session switching in the dashboard failed to render PTY output.
- **#41904 (closed)** — Codex app-server runtime thread context loss fix — Addresses multi-turn context loss in the `codex_app_server` gateway runtime.
- **#52470 (closed)** — Dashboard auto-restart silently fails — Fixes subprocess environment inheritance that caused silent restart failures.
- **#54489 (closed)** — `hermes setup` disables basic plugin → dashboard auth fails — Fixes non-loopback bind authentication failures.
- **#66022 (closed)** — Duplicate feature request for `/branch` threading on Discord/Telegram/Slack — Closed as duplicate.

## Community Hot Topics
### Most Discussed Issues
1. **[#25267 — Claude Agent SDK model provider with subscription OAuth](https://github.com/NousResearch/hermes-agent/issues/25267)** — 11 comments, 41 👍. Users with Claude subscriptions want to avoid paying twice (subscription + per-token API). Strong support signals a high-priority integration need.

2. **[#61265 — Hermes sends extremely large prompts to local OpenAI-compatible models](https://github.com/NousResearch/hermes-agent/issues/61265)** — 6 comments. Multi-minute stalls across model sizes. This P2 performance bug affects all local model users.

3. **[#4335 — Cross-platform session context sharing (CLI ↔ Telegram)](https://github.com/NousResearch/hermes-agent/issues/4335)** — 6 comments. Users desire unified conversation history across platforms, highlighting gateway architecture limitations.

4. **[#15985 — Gemma 4 forgets it has skills](https://github.com/NousResearch/hermes-agent/issues/15985)** — 5 comments. Obsidian skill integration broken with Ollama-hosted Gemma 4, impacting power users.

### Most Active PRs
- **#66033 (open)** — `perf(desktop): kill the layout-thrash cascade on session switch` — Follow-up to two merged performance fixes for the desktop app session switch path.
- **#61183 (open)** — `fix(cron): avoid Windows Python launcher popups` — Windows-specific cron stability fix.
- **#66029 (open)** — `fix(gateway): reply to first-contact /start with a welcome instead of silence` — Telegram onboarding UX fix.

## Bugs & Stability
### Critical / High Severity (P2)
- **[#61265 (P2, open)](https://github.com/NousResearch/hermes-agent/issues/61265) — Extremely large prompts to local models** — Multi-minute stalls across model sizes. Affects all local OpenAI-compatible model users. No fix PR yet.
- **[#65384 (P2, open)](https://github.com/NousResearch/hermes-agent/issues/65384) — Desktop App creates new session on every message with non-default profile** — Remote backend session state corruption for profile-based workflows.
- **[#65787 (P2, open)](https://github.com/NousResearch/hermes-agent/issues/65787) — MCP keepalive O(tool-count) timeout/reconnect loop** — `list_tools()` under 30s timeout causes guaranteed reconnection failures on large MCP servers.
- **[#65746 (P2, open)](https://github.com/NousResearch/hermes-agent/issues/65746) — MoA/local calls crash after 30s: float infinity to integer** — Non-finite stale timeout breaks Mixture of Agents provider calls.
- **[#58745 (P2, open)](https://github.com/NousResearch/hermes-agent/issues/58745) — Context compression semantics conflict** — `context_length` parameter used for both capability declaration and budget enforcement, causing every-turn compression loops.
- **[#53491 (P2, open)](https://github.com/NousResearch/hermes-agent/issues/53491) — Skills security: guard_agent_created off by default** — No security scan for autonomously created persistence skills. PR #43370 partially addresses related session isolation.

### Medium / Low Severity (P3)
- **[#65949 (P3, open)](https://github.com/NousResearch/hermes-agent/issues/65949) — Google Cloud Vertex not recognized as provider** — Documentation mismatch with CLI.
- **[#65854 (P2, open)](https://github.com/NousResearch/hermes-agent/issues/65854) — Uninstall can delete other packages** — Shared Python folder ownership bug.
- **[#57539 (P3, open)](https://github.com/NousResearch/hermes-agent/issues/57539) — Vertex provider missing from HERMES_OVERLAYS** — `/model --provider vertex` fails at CLI.
- **[#54115 (P3, open)](https://github.com/NousResearch/hermes-agent/issues/54115) — BG Review OOM with local llama.cpp** — Background review mechanism causes severe memory issues.

### Fixed Today
- **[#61284 (closed)](https://github.com/NousResearch/hermes-agent/issues/61284) — Dashboard silent WebSocket regression** — Fixed in recent merge.
- **[#66019 (closed P3)](https://github.com/NousResearch/hermes-agent/issues/66019) — `hermes -z` silently ignores `terminal.backend`** — Sandbox bypass via oneshot mode. Closed, needs verification.

## Feature Requests & Roadmap Signals
### High Community Demand
- **[#25267](https://github.com/NousResearch/hermes-agent/issues/25267) — Claude subscription OAuth provider** — 41 👍, suggesting many users want to avoid double billing. Likely candidate for next release or plugin ecosystem.
- **[#45779](https://github.com/NousResearch/hermes-agent/issues/45779) — Multi-gateway connections with per-gateway tabs** — 4 👍, reflects multi-machine users' need for unified desktop management.

### Likely for Next Version
- **Cross-platform session sharing (#4335)** — Structural change to gateway architecture, but community demand is growing.
- **Skip parameters config for auxiliary tasks (#26881)** — Addresses real pain with incompatible providers; relatively contained config change.
- **Structured session tracing (#6741)** — Profiling capability requested by power users, small implementation scope.
- **Context-aware orchestrator model routing (#66020)** — Newly filed but addresses a common user need for multi-model workflows without manual switching.

### Newly Filed Features (Today)
- **[#66020](https://github.com/NousResearch/hermes-agent/issues/66020) — Context-Aware Orchestrator Model Routing** — Agent self-routes tasks to optimal models based on task type.
- **[#65481](https://github.com/NousResearch/hermes-agent/issues/65481) — Support `models_url` in custom providers** — Decouple model discovery from inference base URL.
- **[#65897 (fix PR)](https://github.com/NousResearch/hermes-agent/pull/65897) — Windows toast notification click handler** — Desktop UX fix for notification-driven session navigation.

## User Feedback Summary
### Pain Points
1. **Provider billing friction** — Users with Claude subscriptions (#25267) feel penalized by needing separate API key billing.
2. **Local model performance regression** — Large prompts (#61265) make local deployment severely degraded, affecting self-hosted users.
3. **Desktop app reliability** — Session state corruption (#65384), silent WebSocket failures (#61284), and long TTS timeout (#66008) erode confidence in desktop experience.
4. **Security concerns** — Skills auto-creation without scanning (#53491) worries security-conscious users.

### Satisfaction Signals
- Active community filing detailed bugs with reproduction steps.
- Multiple contributors providing fix PRs (7 PRs today).
- Users requesting advanced features (multi-gateway, model routing) indicating adoption beyond basic use.

### Common Use Cases
- **Local deployment** — Ollama/llama.cpp users facing memory and prompt size issues.
- **Multi-platform** — CLI ↔ Telegram ↔ Discord users wanting unified sessions.
- **Professional workflows** — Obsidian integration, cron task automation, code execution.

## Backlog Watch
### Issues Needing Maintainer Attention
- **[#65985 (P3, no comments)](https://github.com/NousResearch/hermes-agent/issues/15985) — Gemma 4 forgets skills** — Unanswered for several weeks despite 5 comments. Affects Ollama + skills integration.
- **[#4335 (P3, 6 comments)](https://github.com/NousResearch/hermes-agent/issues/4335) — Cross-platform session sharing** — Long-standing (since March) feature request with no maintainer response.
- **[#6741 (P3, 3 comments)](https://github.com/NousResearch/hermes-agent/issues/6741) — Structured session tracing** — Filed April, no apparent progress despite profiling benefits.
- **[#8642 (P3, 2 comments)](https://github.com/NousResearch/hermes-agent/issues/8642) — Plugin status bar hook** — Plugin ecosystem enhancement awaiting implementation.

### Stale PRs
- **[#11640](https://github.com/NousResearch/hermes-agent/pull/11640) — gateway: handle /start as welcome** — Open since April, conflicts with #66029 which addresses same issue with a newer approach.
- **[#33342](https://github.com/NousResearch/hermes-agent/pull/33342) — fix(delegation): use configured provider** — Open since May, P3 severity but ongoing compatibility risk.
- **[#43370](https://github.com/NousResearch/hermes-agent/pull/43370) — Fix cron session context isolation** — Open since June, P2 severity with security implications.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

# PicoClaw Project Digest — 2026-07-17

## 1. Today's Overview
PicoClaw shows **moderate activity** over the past 24 hours, with 9 open pull requests and 2 issues updated. The project is in a **steady dependency maintenance phase**, with six dependency bump PRs from Dependabot (Go packages and GitHub Actions) all still open. A notable **user-facing bug** persists on NanoKVM regarding OpenAI GPT connectivity, and the first-ever **Traditional Chinese (zh-TW) locale PR** has arrived—signaling growing international community adoption. No new releases were published today, and zero PRs were merged or closed.

## 2. Releases
**No new releases today.** The latest release remains v0.3.1 (build 2026-07-03).

## 3. Project Progress
**No PRs were merged or closed in the last 24 hours.**

Notable open PRs that have been updated:
- **#3261** — New zh-TW locale and Traditional Chinese translations for WebUI and documentation (PeterDaveHello)
- **#3262/#3263** — Dependabot bumps for GitHub Actions (`setup-go` v6→v7, `setup-node` v6→v7)
- **#3236** — Major bump of `github/copilot-sdk/go` from 0.2.0 to 1.0.6 (potentially breaking)
- **#3118** — Long-standing feature: remote Pico WebSocket mode for the agent (jp39, stale since June 12)
- **#3115** — Critical session-history corruption fix for inline data URL media extraction (jp39, stale since June 12)

## 4. Community Hot Topics
- **#3195** [OPEN] — *"OpenAI GPT does not work on NanoKVM with default config"* — 3 comments, remains the most discussed issue. User rtadams89 attempted to configure `gpt-5.4` but received errors. This is a **configuration compatibility gap** between PicoClaw and the NanoKVM 2.4.0 integration. https://github.com/sipeed/picoclaw/issues/3195
- **#3261** [OPEN] — New zh-TW locale PR with no comments yet, but represents a **community-driven internationalization effort**. https://github.com/sipeed/picoclaw/pull/3261
- **#3118** [OPEN, stale] — Remote WebSocket mode for agent. Last updated June 12, but activity suggests maintainers may be revisiting. https://github.com/sipeed/picoclaw/pull/3118

**Underlying need:** Users on edge hardware (NanoKVM) want plug-and-play AI assistant functionality; international users are proactively localizing the project.

## 5. Bugs & Stability
**Bugs reported (ranked by severity):**

1. **[HIGH] #3195** — *OpenAI GPT fails on NanoKVM* — User cannot use gpt-5.4 despite following official docs. No fix PR exists. Impacts a key use case (KVM-integrated AI).  
   https://github.com/sipeed/picoclaw/issues/3195

2. **[MEDIUM] #3260 [CLOSED]** — *ARM64 launcher missing* — User on Raspberry Pi 3B (aarch64) could not find launcher binary after downloading ARM64 release. Marked closed but no resolution visible in the data.  
   https://github.com/sipeed/picoclaw/issues/3260

**Regression Watch:** PR #3115 (fix for session-history corruption when data URLs appear in tool output) remains unmerged after 35 days. This is a **potential data loss bug** in session history if any tool returns base64 image strings in plain text.

## 6. Feature Requests & Roadmap Signals
- **zh-TW locale (PR #3261)** — Likely to be merged in next patch release, as it's non-breaking and low risk.
- **Remote WebSocket mode (PR #3118)** — If merged, enables out-of-process agent execution, a significant architecture advance. May land in v0.4.0.
- **NanoKVM support improvements** — Given the #3195 bug report, expect better default config handling for NanoKVM in the next version.

**Prediction:** Next release (v0.3.2) will likely include the zh-TW locale, M1-related Apple Silicon fixes (implied from build system updates), and dependency bumps. The remote WebSocket agent may wait for a minor version bump.

## 7. User Feedback Summary
- **Pain Point:** ARM64 Linux users (Raspberry Pi) encounter missing launcher binaries after download, causing setup friction (#3260).
- **Pain Point:** NanoKVM users cannot easily configure OpenAI GPT models despite following official documentation—suggests the default config path is fragile (#3195).
- **Positive Signal:** Community member contributed a full zh-TW locale without being asked, indicating strong satisfaction and engagement from international users (#3261).
- **Use Case Gap:** Remote agent mode (#3118) has been requested since June, suggesting power users want headless/WebSocket-driven operation, not just CLI.

## 8. Backlog Watch
| Item | Last Updated | Days Stale | Risk |
|------|-------------|------------|------|
| **#3118** — Remote Pico WebSocket mode | 2026-06-12 | 35 | High — if unmerged, feature development stalls |
| **#3115** — Data URL corruption fix | 2026-06-12 | 35 | High — potential data loss bug remains unfixed |
| **#3238** — AWS SDK Go bump | 2026-07-09 | 8 | Medium — dependency rot |
| **#3236** — Copilot SDK major bump (0.2.0 → 1.0.6) | 2026-07-09 | 8 | **Critical** — version jump suggests breaking API changes; needs maintainer review before merge |

**Maintainer attention needed:** Two high-impact PRs (#3118, #3115) have been untouched for over a month. The Copilot SDK bump (#3236) from 0.2.0 to 1.0.6 is a major version change and could silently break downstream integrations if merged without review.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

# NanoClaw Project Digest — 2026-07-17

## Today's Overview
Project activity is **elevated**, with 19 PRs updated in the last 24 hours and 4 issues active. The community is deeply engaged in core infrastructure work, particularly around LLM fallback mechanisms and channel adapter reliability. Three PRs were merged/closed, signaling steady progress. The project shows healthy contributor velocity, though the backlog of 16 open PRs suggests maintainer review capacity may be strained.

## Releases
**No new releases** today. The latest release remains prior versions; notable unreleased features (LLM fallback, Dial channel, security fixes) are accumulating in open PRs.

## Project Progress
**3 PRs merged/closed today:**

- **#2913** ([fix(whatsapp-cloud): register bridge under distinct 'whatsapp-cloud' instance key](https://github.com/nanocoai/nanoclaw/pull/2913)) — **Merged.** Fixes the WhatsApp Cloud/native Baileys collision where both registered under `whatsapp`, causing silent misrouting. This is a high-impact infrastructure fix.
- **#2914** ([docs(add-whatsapp-cloud): document webhook route + state-namespace migration](https://github.com/nanocoai/nanoclaw/pull/2914)) — **Merged.** Documentation follow-up to the WhatsApp fix.
- **#3061** ([Custom PR — closed](https://github.com/nanocoai/nanoclaw/pull/3061)) — **Closed** without merge; unclear scope.

**Notable unmerged but advancing PRs:**
- **#3057** ([feat: automatic Claude↔Codex quota fallback](https://github.com/nanocoai/nanoclaw/pull/3057)) — Major feature enabling per-agent-group automatic failover when Claude hits quota, with Telegram/WhatsApp channels and pilot activation module.
- **#3069** ([feat: host-orchestrated fallback to backup LLM provider](https://github.com/nanocoai/nanoclaw/pull/3069)) — Complements #3057 with install-wide failover on quota exhaustion, billing failure, or API overload.
- **#3070** ([Fix WhatsApp sender identity divergence](https://github.com/nanocoai/nanoclaw/pull/3070)) — Resolves a user identity mismatch between Baileys and Cloud WhatsApp paths.

## Community Hot Topics

**Most commented issues:**
1. **#2916** ["hi"](https://github.com/nanocoai/nanoclaw/issues/2916) — 2 comments. Low-signal test/placeholder issue.
2. **#3016** [Every rate_limit_event logged as quota error](https://github.com/nanocoai/nanoclaw/issues/3016) — 2 comments. Users experiencing noisy false-positive quota errors on successful turns (82 occurrences in one week reported). **Underlying need:** Better telemetry hygiene — distinguishing true quota exhaustion from non-blocking rate limits.

**Most active PRs by context:**
- Two competing LLM fallback PRs (#3057, #3069) suggest community disagreement or parallel work on failover strategy. Both are heavily referenced and will need reconciliation.
- **#3065** (loopback webhook authentication) addresses a security advisory (GHSA-h9g4-589h-68xv), indicating coordinated security response.

**User need analysis:** The cluster of WhatsApp/sender-identity fixes (#3070, #2913, #2914, #2911) reveals that **multi-channel identity management** is a critical pain point. Users running both WhatsApp Cloud and Baileys paths experience message misrouting and broken user state — this is a real deployment blocker for organizations needing WhatsApp redundancy.

## Bugs & Stability

**High severity:**
1. **#3064** ([Channel adapter startup failure swallowed](https://github.com/nanocoai/nanoclaw/issues/3064)) — **Critical.** A channel that fails `setup()` is silently swallowed, leaving the host running "healthy" but actually deaf on that channel. KeepAlive cannot recover it. **Fix PR exists:** #3067 (propagates failure, exits non-zero).
2. **#2911** ([WhatsApp Cloud collides with native WhatsApp](https://github.com/nanocoai/nanoclaw/issues/2911)) — **High.** Already fixed by #2913 (merged). Two WhatsApp channels with same key `whatsapp` caused silent disablement of one.

**Medium severity:**
3. **#3016** ([Rate limit false positives](https://github.com/nanocoai/nanoclaw/issues/3016)) — **Medium.** Noisy but non-destructive; pollutes logs with up to 82 false quota errors/week. No dedicated fix PR yet, though fallback PRs (#3057, #3069) touch related code.
4. **#2851** ([Abandoned poll loops steal tests' messages](https://github.com/nanocoai/nanoclaw/issues/2851) — via PR) — **Medium.** Test infrastructure bug causing cross-test contamination. Open since June 24, now gaining updates.

**Low severity:**
5. **#3068** ([Scheduled task cross-session visibility](https://github.com/nanocoai/nanoclaw/issues/2992) — via PR) — **Low.** Scheduled tasks work, but feedback is confusing across same-group sessions. Fix in PR #3068.

## Feature Requests & Roadmap Signals

**Strong roadmap signals (likely v2.2+):**
1. **Multi-LLM fallback architecture** — Two competing PRs (#3057, #3069) propose automatic failover from Claude to Codex/quota-based fallback. This is clearly a priority for the maintainers and suggests next release will include LLM resilience.
2. **Dial channel integration** — PRs #3041 and #3050 add a new "Dial" channel (SMS + AI voice calls), including setup wizard changes. This indicates expansion beyond messaging into voice telephony.
3. **Signal adapter improvements** — PRs #2695 (image attachment staging), #3062 (read receipts) show ongoing investment in Signal channel usability. The image attachment fix has been open since June 6 — may finally merge.

**User-requested features (from issue analysis):**
- **Better telemetry/error classification** (#3016) — Users want clear distinction between real quota errors and transient rate limits. The fallback PRs partially address this.
- **Channel startup reliability** (#3064) — Silent failures undermine trust in "healthy" status. PR #3067 directly addresses this.
- **WhatsApp dual-channel support** (#2911) — Already fixed; but users needing both WhatsApp paths is a confirmed use case.

**Prediction:** Next release (v2.2.x) will likely include: LLM fallback (one of #3057/#3069, possibly merged), Dial channel, Signal read receipts, and the channel startup fix.

## User Feedback Summary

**Pain points:**
- **Deceptive health status** (#3064): "host reports healthy but runs deaf" — undermines trust in monitoring.
- **Log pollution** (#3016): 82 false quota warnings/week erodes signal-to-noise ratio for production deployments.
- **WhatsApp identity confusion** (#3070): Users running mixed WhatsApp infrastructure get broken user identity across paths.
- **Signal missing features** (PR #2695, #3062): Cannot receive images in containers (since June 6); messages not marked read on sender's side.

**Satisfaction signals:**
- Active PR contributions from diverse authors (QuantumBreakz, bissamiftikhar, salvodmt, elia-ben-cnaan, tenequm) suggest engaged developer community.
- PR #3065 (security advisory) indicates proactive vulnerability response — positive governance signal.
- The Dial channel addition shows community-driven expansion into new capabilities.

**Unaddressed concerns:**
- PR #2851 (test pollution) has been open since June 24 with no resolution — indicates possible test infrastructure fragility that may slow development velocity.
- No response yet to #3016 from maintainers regarding the noisy quota logging.

## Backlog Watch

**Issues needing maintainer attention:**
1. **#3064** ([Channel adapter startup swallowed](https://github.com/nanocoai/nanoclaw/issues/3064)) — **Critical, filed today.** Fix PR #3067 exists; needs review and merge.
2. **#3016** ([Rate limit false positives](https://github.com/nanocoai/nanoclaw/issues/3016)) — **Open since July 11.** No maintainer response. 82 occurrences/week per user.
3. **#2916** ([Issue "hi"](https://github.com/nanocoai/nanoclaw/issues/2916)) — **Low priority.** Test/spam issue; may need closure.

**Stale PRs needing attention:**
1. **#2695** ([Signal image attachments](https://github.com/nanocoai/nanoclaw/pull/2695)) — **Open since June 6 (41 days).** Core usability fix; Signal channel cannot receive images in container. Needs review.
2. **#2851** ([Test poll loops](https://github.com/nanocoai/nanoclaw/pull/2851)) — **Open since June 24 (23 days).** Test infrastructure bug causing cross-test contamination; may be blocking other work.
3. **#2798** ([CHANGELOG expansion](https://github.com/nanocoai/nanoclaw/pull/2798)) — **Open since June 17 (30 days).** Documentation housekeeping.

**Conflict watch:** PRs #3057 and #3069 propose overlapping LLM fallback mechanisms. Maintainers should clarify which approach (per-agent-group vs install-wide) takes priority, or merge both with clear layering. This divergence risks developer confusion and wasted effort if both proceed independently.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

Here is the NullClaw project digest for **2026-07-17**.

---

### 1. Today’s Overview

The NullClaw project is in a **low-activity maintenance mode** over the past 24 hours, with no new releases or merged pull requests. The single most significant event is a critical crash bug (Issue #976) reported in the latest stable release (`v2026.5.29`), which has received one comment but no immediate fix PR. The lack of any PR activity suggests that development focus is either on internal branches or paused. The project's health is currently **stable but fragile**, with one high-severity open issue threatening production reliability for Telegram gateway users on `aarch64` Linux.

### 2. Releases

**No new releases today.** The latest available version remains **v2026.5.29**.

### 3. Project Progress

**No pull requests were merged or closed in the last 24 hours.** No features or fixes were advanced.

### 4. Community Hot Topics

The community’s attention is entirely focused on one critical issue:

- **[#976 [OPEN] SIGSEGV on every inbound Telegram message — inbound worker thread spawned with a ~512 KB stack overflows](https://github.com/nullclaw/nullclaw/issues/976)** (1 comment, 0 reactions)
    - **Context:** The reporter is running NullClaw as a systemd service on aarch64 Linux. Every inbound Telegram message triggers a segmentation fault due to an undersized worker thread stack (approximately 512 KB).
    - **Impact:** This causes the gateway to crash-loop, dropping all incoming messages, making the bot effectively non-functional for the user.
    - **Analysis:** This is likely a shebang or platform-specific stack size limit on ARM64. The community need here is **urgent reliability**—users expect the Telegram gateway to handle message concurrency without crashing. The single comment likely discusses the stack size, but no patch or workaround has been officially proposed.

### 5. Bugs & Stability

| Severity | Issue | Description | PR Fix Exists? |
| :--- | :--- | :--- | :--- |
| **Critical** | [#976](https://github.com/nullclaw/nullclaw/issues/976) | SIGSEGV (crash) on every inbound Telegram message on aarch64 Linux. Inbound worker thread stack overflow (512 KB). | No |
| Low | None | No other bugs or regressions reported today. | N/A |

**Analysis:** This is a regression in `v2026.5.29` specifically on the ARM64 platform. It is a **high-severity production blocker** for any user running the Telegram gateway on aarch64 hardware (e.g., Raspberry Pi, AWS Graviton). Since there is no linked fix PR or a new release candidate, affected users must either downgrade to a previous stable build or patch the thread stack size manually.

### 6. Feature Requests & Roadmap Signals

**No explicit feature requests were filed today.** However, the nature of Issue #976 sends a strong signal to the maintainers:

- **Predicted next version focus:** **Platform stability for ARM64**. The crash indicates that thread stack size configuration is not universal across architectures. A likely fix in the next release will either:
    - Dynamically set a larger thread stack (e.g., 2 MB) for `aarch64` Linux.
    - Make the stack size configurable via a runtime flag or environment variable (e.g., `NULLCLAW_TG_WORKER_STACK_KB`).

### 7. User Feedback Summary

- **Reported Pain Points (1 user):**
    - **Crash-to-oblivion:** The user explicitly reports that “the message is dropped” and they “never get a reply.” This indicates a complete breakdown of the primary use case (Telegram bot).
    - **Systemd loop frustration:** The `Restart=always` systemd configuration is exacerbating the problem by creating a crash-loop with no backoff strategy visible.
- **Satisfaction:** **Low.** The user `wonhotoss` filed a detailed bug report indicating a negative experience with the latest release. The lack of a quick-fix response within 24 hours may further reduce user confidence.
- **Use Case Impact:** This bug directly affects **production Telegram bots** running on ARM servers, which are common for self-hosted AI agents. It is a blocking issue for that segment.

### 8. Backlog Watch

- **#976 [OPEN] – Critical Bug (1 day old):** While not "long-unanswered" yet, this issue requires **immediate maintainer attention**. Given its severity (crash on every message) and its platform-specific nature (aarch64), a first triage comment from a maintainer is essential. If no response comes within 48 hours, this should be escalated as a project health risk.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

# IronClaw Project Digest — 2026-07-17

## Today's Overview

IronClaw activity remains at a high tempo, with **18 issues** and **39 pull requests** updated in the last 24 hours, indicating sustained engineering investment across both the Reborn runtime and WebUI v2. The project is in a **late-stage refactoring and stabilization phase**, with core contributors executing planned carve-outs of the monolithic `ironclaw_reborn_composition` crate, building out background-service deployment stories, and shipping new channel integrations (Telegram). No new releases were published today, but the release pipeline PR (#5598) continues to accumulate breaking-change approvals. The team is responsive: 11 PRs were merged or closed, and 3 issues were resolved. A notable **OAuth flow reversion** (#6166) was merged and then immediately reconsidered, reflecting careful lifecycle hygiene work. The bug tracker shows **8 actively triaged issues** from the recent `bug_bash` campaign, with P2 and P3 priorities indicating user-facing reliability concerns.

## Releases

**No new releases today.** The most recent release preparation is tracked in PR #5598, which proposes breaking changes to `ironclaw_common` and `ironclaw_skills` for v0.5.0 and v0.4.0 respectively, but remains open.

## Project Progress

**Merged/closed PRs today (11 total):**

- **OAuth lifecycle hygiene** — PR #6130 (`fix(auth): OAuth flow-lifecycle hygiene`) was merged, then **reverted** via PR #6166 while its behavior is reconsidered. This indicates careful caution around authentication flow changes.
- **Auth conformance testing** — PR #6114 (`test(auth): shared OAuth-flow conformance suite`) was merged, closing the gap between fake and durable `AuthFlowManager` test suites and hardening the foundation.
- **WebUI onboarding exploration** — PR #5565 (`feat(gateway): onboarding/NUX demo`) was closed/merged after accumulating 13 self-contained commits, delivering an intent-URL → sign-in → onboarding → agentic-chat experience.
- **Dependency updates** — Two `dependabot` PRs (#6115, #6165) were merged, keeping the Rust dependency tree current across 25–26 updates each.
- **User secrets management** — Issue #6118 (Add per-user secrets management to Admin UI) was closed, with the frontend layer now fully wired.

**Major features advancing in open PRs:**

- **Telegram channel extension** (PR #6159) — First-class Telegram entrypoint on Reborn, with admin bot setup, WebGeneratedCode pairing, and DM entrypoint. Ships behind the `webui-v2-beta` feature flag.
- **Background service install** (PR #6172) — Adds `launchd` (macOS) and `systemd --user` support for `ironclaw-reborn`, enabling headless background operation with `install/uninstall/start/stop/status/restart`.
- **Terminal UI** (PR #6157) — Ratatui-based terminal client for Reborn, acting as a thin HTTP+SSE consumer of WebChat v2 API.
- **Workspace redesign** (PR #6162) — Redesigns legacy gateway agent workspace with WebUI v2 design-system tokens, split 1/2 of the prior mega-PR #5565.
- **Chat-first onboarding** (PR #6163) — Stacked on #6162, adds auth-deferred onboarding with marketing-site handoff, setup wizard, and in-thread scripted journey.
- **Unified extension runtime** (PR #6116) — Large reconciliation PR merging 92 commits from `main` into the generic extension runtime architecture, covering agent, channel/web, workspace, sandbox, CI, docs, and dependencies.
- **GitHub CI triage** (PR #6140) — Ships `github.get_job_logs` capability with SSRF-safe redirect egress, enabling the agent to triage CI failures autonomously.
- **Composition mass ratchet** (PR #6167) — Introduces `scripts/dev_metrics.py` and a CI gate to prevent the `ironclaw_reborn_composition` crate from growing beyond its charter.

## Community Hot Topics

### Most Active Issues

1. **#6168 — Shrink the `ironclaw_reborn_composition` god-crate** (2 comments)
   - *Author: ilblackdragon (core)* — This issue outlines the charter-bound carve-out of the largest crate (~24% of production code) into a lean ~10% assembly-only wiring crate. It generated 2 comments in its first day and signals a major architectural refactoring push.
   - URL: https://github.com/nearai/ironclaw/issues/6168

2. **#6155 — Follow-up messages receive no response after a failed run** (2 comments, P2 bug_bash)
   - *Author: joe-rlo* — A critical user-facing bug where a conversation becomes completely unresponsive after any run failure. The lack of error feedback leaves users stuck.
   - URL: https://github.com/nearai/ironclaw/issues/6155

3. **#6126 — First message in new chat has no loading or streaming state** (2 comments, P3 bug_bash)
   - *Author: joe-rlo* — UI remains blank while assistant processes the first message, appearing frozen.
   - URL: https://github.com/nearai/ironclaw/issues/6126

4. **#6127 — "Previous run still in progress" displayed incorrectly** (2 comments, P3 bug_bash)
   - *Author: joe-rlo* — False status warning on a routine's first (and only) execution.
   - URL: https://github.com/nearai/ironclaw/issues/6127

### Most Active PRs

- **#6159 — Telegram channel extension** — New contributor-friendly channel integration by BenKurrek, already attracting attention for its DM entrypoint and WebGeneratedCode pairing.
- **#6167 — Dev metrics + composition mass ratchet gate** — ilblackdragon's CI tooling PR introduces automated codebase health metrics.
- **#6172 — Background service install** — henrypark133's launchd/systemd support, enabling production deployments.
- **#6162/#6163 — Workspace redesign + chat-first onboarding** — achalvs's pair of stacked PRs, split from the original mega-PR #5565.

**Underlying needs:** The community is signaling strong demand for **reliability** (no stuck chats, proper loading states), **multi-platform deployment** (background services, multi-arch builds), and **channel expansion** (Telegram). The architectural refactoring of the composition crate shows the team proactively addressing technical debt before it impacts velocity.

## Bugs & Stability

### Severity: High

- **#6155 — Follow-up messages receive no response after a failed run** (P2)
  - *Impact:* Total conversation lockup after any run failure. No workaround.
  - *Status:* No fix PR yet, opened 1 day ago.
  - URL: https://github.com/nearai/ironclaw/issues/6155

- **#6170 — Users can access filesystem via shell on multi-tenant instances** (unranked)
  - *Impact:* Security vulnerability on multi-tenant deployments — users can run `ls -all` unbounded to their workspace.
  - *Status:* Opened today by sergeiest, no resolution.
  - URL: https://github.com/nearai/ironclaw/issues/6170

### Severity: Medium

- **#6126 — No loading/streaming state on first message** (P3)
  - *Impact:* User perceives app as frozen for several seconds.
  - URL: https://github.com/nearai/ironclaw/issues/6126

- **#6127 — "Previous run still in progress" error on first execution** (P3)
  - *Impact:* Confusing user-facing status message.
  - URL: https://github.com/nearai/ironclaw/issues/6127

- **#6149 — Workspace download failures silently ignored** (unranked)
  - *Impact:* User cannot determine if download succeeded or failed.
  - URL: https://github.com/nearai/ironclaw/issues/6149

- **#6145 — Toast lifecycle and accessibility issues** (unranked)
  - *Impact:* Toasts auto-dismiss in 2.6 seconds, cannot be manually dismissed, no pause-on-hover.
  - URL: https://github.com/nearai/ironclaw/issues/6145

### Severity: Low

- **#5602 — Can't connect Slack from chat**
  - *Impact:* Reported 14 days ago, remains open with no fix PR. Agent claims connection but returns pairing code instead.
  - URL: https://github.com/nearai/ironclaw/issues/5602

**Crash/hang analysis:** The daily failure taxonomy (#6144) from clawbench shows the largest failure band (~78 tasks, `response/empty`) is persistent and likely infrastructure-related rather than code bugs. No new crash reports were filed today.

## Feature Requests & Roadmap Signals

### User-requested features added today

- **#6158 — zh-TW Traditional Chinese localization** — PeterDaveHello proposes adding Traditional Chinese to WebUI v2, which currently only offers Simplified Chinese. This is a low-effort localization request that improves accessibility for Taiwanese/Hong Kong users.
  - URL: https://github.com/nearai/ironclaw/issues/6158

- **#6146 — Add theme selection controls to Appearance settings** — italic-jinxin requests that the dedicated Appearance settings page (currently empty) include light/dark theme controls, which already exist in the sidebar.
  - URL: https://github.com/nearai/ironclaw/issues/6146

- **#6142 — Serve WebUI at root path instead of `/v2`** — italic-jinxin proposes cleaning up URL paths from `/v2/chat` to `/chat`.
  - URL: https://github.com/nearai/ironclaw/issues/6142

- **#6143 — Promote CLI from `ironclaw-reborn` to `ironclaw`** — italic-jinxin proposes renaming the Reborn CLI to the canonical `ironclaw` command after v1 retirement.
  - URL: https://github.com/nearai/ironclaw/issues/6143

### Prediction for next version

Based on active PRs and roadmap signals, the **next release** (tracked in PR #5598) will likely include:

1. **Breaking changes to `ironclaw_common` (v0.5.0) and `ironclaw_skills` (v0.4.0)** — Already prepared in the release PR.
2. **Telegram channel integration** — PR #6159 is code-complete and likely to land before release.
3. **Background service install** — PR #6172 provides critical deployment infrastructure.
4. **OAuth flow improvements** — Despite the reversion, the auth conformance suite (#6114) is merged, and the lifecycle fixes are being reconsidered.
5. **WebChat v2 model selection + cost display** — PR #6111 is merged.

## User Feedback Summary

### Pain points (active issues)

1. **Conversation lockup after errors** (#6155) — Users report that any run failure makes the chat completely unresponsive. With no error message or retry mechanism, trust is eroded.
2. **First-message blank screen** (#6126) — New users experience an apparent freeze, which is a poor first impression.
3. **False status warnings** (#6127) — "Previous run still in progress" on first execution confuses users and undermines confidence in the system's reliability.
4. **Slack connection broken** (#5602) — Reported 14 days ago, the `connect to Slack` flow claims success but fails to actually connect DMs.
5. **Workspace download failures** (#6149) — Silent failures with no user feedback for file downloads.
6. **Localization gaps** (#6158) — Traditional Chinese users cannot select their locale.

### Positive signals

- The **Telegram extension** (PR #6159) adds a highly-requested channel with proper admin bot setup and DM entrypoint.
- **Background service support** (PR #6172) enables production deployments on macOS and Linux.
- The **workspace redesign** (PR #6162) and **chat-first onboarding** (PR #6163) show investment in user experience for new users.
- **Multi-arch build support** (#6160) indicates planning for broader deployment targets.

## Backlog Watch

### Issues needing maintainer attention

- **#5602 — Can't connect Slack from chat** — 14 days old, 1 comment, no fix PR. This is a live user-facing integration bug that may be related to the Slack connection-epoch refactoring tracked in #6164/#6169.
  - URL: https://github.com/nearai/ironclaw/issues/5602

- **#4471 — Track Reborn runtime decomposition** — 43 days old, 1 comment. The runtime.rs file is above the 3,000-line budget. No further updates since the initial mention.
  - URL: https://github.com/nearai/ironclaw/issues/4471

- **#6170 — Remove user access to file system via shell** — Opened today but is a **security vulnerability** on multi-tenant instances. Requires immediate triage.
  - URL: https://github.com/nearai/ironclaw/issues/6170

### PRs needing review

- **#5598 — chore: release** — Open for 14 days, accumulating breaking changes. The release PR needs final approval to ship v0.5.0 of `ironclaw_common` and v0.4.0 of `ironclaw_skills`.
  - URL: https://github.com/nearai/ironclaw/pull/5598

- **#5978 — Require read-before-edit in reborn coding tools** — Open for 6 days, important for code quality but appears to be waiting on a review cycle for the full stacked PR series.
  - URL: https://github.com/nearai/ironclaw/pull/5978

---

*Generated 2026-07-17 from GitHub activity data. All links reference `github.com/nearai/ironclaw`.*

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

Based on the provided GitHub data for the LobsterAI project (netease-youdao/LobsterAI), here is the structured project digest for 2026-07-16.

---

### LobsterAI Project Digest – 2026-07-16

### 1. Today's Overview
The project exhibited high activity today, driven by a major release push. A total of 17 pull requests (PRs) were updated, with 14 being merged or closed, indicating strong forward momentum. Three issues were updated, though all are marked as stale. The focus was squarely on stabilizing and enhancing the "Cowork" feature, with significant refactoring of clipboard handling, attachment support, and conversation UI behavior. The release v2026.7.16 was successfully cut, consolidating these improvements.

### 2. Releases
**No new releases today.**
- The latest activity includes the creation of the release PR `#2344` (Release/2026.7.16), which was merged today. This suggests a version **v2026.7.16** was rolled out to users.

### 3. Project Progress
Merged/closed PRs today advanced several key areas, primarily the **Cowork** feature and UI polish:
- **Refactoring & Code Quality:** PR [#2343](https://github.com/netease-youdao/LobsterAI/pull/2343) refactored clipboard attachment extraction for better testability.
- **User Interface Fixes:**
    - PR [#2339](https://github.com/netease-youdao/LobsterAI/pull/2339) fixed alignment and text truncation in update cards for narrow sidebars.
    - PR [#2302](https://github.com/netease-youdao/LobsterAI/pull/2302) introduced a Windows-specific branded title bar and moved sidebar actions into it.
- **Cowork Feature Stability:**
    - PR [#2329](https://github.com/netease-youdao/LobsterAI/pull/2329) prevented conversation scroll jumps during streaming.
    - PR [#2289](https://github.com/netease-youdao/LobsterAI/pull/2289) fixed a bug where stalled compaction retries were not properly cleaned up, adding regression tests.
    - PR [#2292](https://github.com/netease-youdao/LobsterAI/pull/2292) stabilized the steer follow-up routing, including queuing and session management.
    - PR [#2300](https://github.com/netease-youdao/LobsterAI/pull/2300) allowed file attachments in the steer follow-up queue.
    - PR [#2313](https://github.com/netease-youdao/LobsterAI/pull/2313) fixed the steer queue to only submit the selected item, preserving FIFO order.
    - PR [#2307](https://github.com/netease-youdao/LobsterAI/pull/2307) refined prompt modes, moving status bars and fixing follow-up handling.
    - PR [#2310](https://github.com/netease-youdao/LobsterAI/pull/2310) added support for folder context attachments.

### 4. Community Hot Topics
The most active issues and PRs by comment count (2 comments max) are all marked as `stale`, showing limited recent community engagement on open discussion threads.
- **Issue [#1361](https://github.com/netease-youdao/LobsterAI/issues/1361):** [CLOSED] Localization bug: The "delete" button on the custom agent detail page is in English instead of Chinese. This was a straightforward bug that was closed.
- **Issue [#1317](https://github.com/netease-youdao/LobsterAI/issues/1317):** [OPEN] Feature request to show keyboard shortcut hints (`kbd` tags) for sidebar buttons (e.g., Ctrl+N, Ctrl+F). A corresponding PR [#1318](https://github.com/netease-youdao/LobsterAI/pull/1318) exists but is also stale. The underlying need is for improved discoverability and user onboarding for power-user features.
- **Issue [#1319](https://github.com/netease-youdao/LobsterAI/issues/1319):** [OPEN] Feature request to add a skeleton loading state to the session list to eliminate the "empty state flash" on startup. A corresponding PR [#1320](https://github.com/netease-youdao/LobsterAI/pull/1320) exists but is stale. The need is for a smoother, more professional initial user experience.

### 5. Bugs & Stability
No new bugs were reported in the last 24 hours. The main stability work was on existing issues:
- **Fix: Conversation Scroll Jumping:** [PR #2329](https://github.com/netease-youdao/LobsterAI/pull/2329) addresses an issue where auto-scrolling during streaming conflicts with manual scrolling. (Severity: Medium)
- **Fix: Stalled Compaction Maintenance:** [PR #2289](https://github.com/netease-youdao/LobsterAI/pull/2289) fixes a bug related to context maintenance not cleaning up properly after a compaction retry. (Severity: High, as it could affect long-running sessions).
- **Fix: Steer Queue Submission:** [PR #2313](https://github.com/netease-youdao/LobsterAI/pull/2313) fixed a bug where the steer queue would process incorrectly, ensuring only the selected item is submitted. (Severity: Medium)

### 6. Feature Requests & Roadmap Signals
Three feature requests are currently pending via stale PRs:
- **Keyboard Shortcut Hints:** [PR #1318](https://github.com/netease-youdao/LobsterAI/pull/1318) (platform-aware `kbd` tags) is a strong candidate for a future release, as it aligns with UX best practices. This is likely to be integrated soon.
- **Skeleton Loading for Sessions:** [PR #1320](https://github.com/netease-youdao/LobsterAI/pull/1320) addresses a clear user perception issue. It is a small, isolated change that improves perceived performance and could be picked up quickly.
- **Model Selector in Input Toolbar:** [PR #1364](https://github.com/netease-youdao/LobsterAI/pull/1364) (already closed) added a model selector to the home page input toolbar. This feature is now live, indicating the team followed through on this user-proposed workflow enhancement.

### 7. User Feedback Summary
User feedback today is inferred primarily from the closed issues and the rationale behind the merged PRs.
- **Pain Point:** Localization consistency was a pain point, with a user reporting that the "delete" button on a custom agent page was showing in English instead of Chinese. This was quickly addressed in [Issue #1361](https://github.com/netease-youdao/LobsterAI/pull/1361).
- **Pain Point:** A user requested an easier way to discover keyboard shortcuts ([Issue #1317](https://github.com/netease-youdao/LobsterAI/issues/1317)), indicating the current discoverability of these power features is low.
- **Pain Point:** The "empty state flicker" in the session list ([Issue #1319](https://github.com/netease-youdao/LobsterAI/issues/1319)) points to user dissatisfaction with the initial loading experience.
- **Positive Outcome:** The merging of [PR #1364](https://github.com/netease-youdao/LobsterAI/pull/1364) (model selector in input toolbar) shows the project is responsive to user workflow efficiency requests.

### 8. Backlog Watch
The following items are marked as `stale` and have been open since **April 2, 2026** (over 3 months). They require maintainer attention to either be merged, closed, or updated with a revised plan.
- **PR [#1318](https://github.com/netease-youdao/LobsterAI/pull/1318):** Keyboard shortcut hints. Requires a review and merge decision.
- **PR [#1320](https://github.com/netease-youdao/LobsterAI/pull/1320):** Skeleton loading for session list. Requires a review and merge decision.
- **PR [#1321](https://github.com/netease-youdao/LobsterAI/pull/1321):** Fix for overlays not dismissing when switching settings tabs. Requires review and merge decision.

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyagi">TinyAGI/tinyagi</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

# Moltis Project Digest — 2026-07-17

## Today's Overview
The Moltis project saw a quiet yet productive day, with zero new or updated issues but three pull requests merged, all from the same author (penso). One new release (20260716.01) was published. No new bugs, regressions, or community discussions surfaced. The activity level is moderate, with maintainer focus clearly on closing recent feature work and stabilizing the web UI. The project appears to be in a steady state of incremental improvement rather than undergoing large architectural changes.

## Releases
**Release 20260716.01** was published on 2026-07-16.  
No release notes, changelog, or migration guides were provided. Based on the PRs merged in the same period, the release likely includes:
- Improved agent and sandbox status feedback
- Kimi K3 / K2.7 Code provider support
- Fix for sandbox toggle UI when no sandbox backend is available

No breaking changes or migration notes have been identified.

## Project Progress
Three pull requests were merged/closed today, all by **penso**:

- **PR #1155** [CLOSED] — *Improve agent and sandbox status feedback*  
  Adds broadcasting of external-agent session metadata once session IDs become available, returns persisted external-agent history from full context requests while keeping web session stores merge-safe, and treats installed external agents as available chat backends (including Apple Container support).  
  [GitHub PR #1155](https://github.com/moltis-org/moltis/pull/1155)

- **PR #1156** [CLOSED] — *Add Kimi K3 provider support*  
  Adds Kimi K3 and Kimi K2.7 Code Highspeed to Moonshot and Kimi Code model catalogs, updates model capabilities, reasoning-effort handling, provider defaults, config templates, documentation, and key-help links. Includes onboarding E2E coverage for Moonshot setup.  
  [GitHub PR #1156](https://github.com/moltis-org/moltis/pull/1156)

- **PR #1154** [CLOSED] — *fix(web): show direct mode when sandbox is unavailable*  
  Fixes the chat header to show a "direct" (non-sandboxed) toggle when no real sandbox backend is available. Disables the sandbox toggle and image selector when only non-isolated fallback execution is present. Adds E2E coverage for this corner case.  
  [GitHub PR #1154](https://github.com/moltis-org/moltis/pull/1154)

## Community Hot Topics
No community activity was recorded today. There are no open issues or pull requests with comments, reactions, or discussion threads in the last 24 hours. The project currently has zero open issues and zero open pull requests, indicating either a well-maintained tracker or low external engagement.

## Bugs & Stability
No new bugs, crashes, or regressions were reported today. The only stability-related work was the proactive fix in **PR #1154**, which addresses a UI edge case where the sandbox toggle incorrectly showed "sandboxed" when no sandbox backend existed — a user-facing display bug now resolved.

**Severity**: Low (visual/UX inconsistency, no data loss or crash)

## Feature Requests & Roadmap Signals
No new feature requests were submitted today. The merged PRs suggest the project is prioritizing:
- **Provider expansion** — Kimi K3/K2.7 Code support was added, indicating ongoing investment in new model provider integrations.
- **UX robustness** — Sandbox status handling and direct-mode fallback were improved, suggesting a focus on graceful degradation when components are missing.
- **External agent interoperability** — Better metadata sharing and session handling for external agents.

Likely next-version features include additional provider integrations and further polish of sandbox/agent status feedback.

## User Feedback Summary
No user feedback was recorded in the last 24 hours. The absence of issue reports or comments may indicate either satisfied users or low usage volume. The lack of complaints about recent changes (provider additions, sandbox fixes) is a neutral signal.

## Backlog Watch
There are no unanswered or long-standing issues or pull requests. The project's issue tracker is currently empty, which is unusual for an active open-source project. Maintainers may want to monitor for:
- Silent regressions that have not yet been reported
- Feature requests that may have been raised previously on other channels
- General community engagement, which appears minimal today

**Overall project health**: Stable, with incremental improvements and no reported incidents.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

Based on the GitHub data for CoPaw (from the `agentscope-ai/QwenPaw` repository, presumably the core project), here is the project digest for **2026-07-17**.

---

# CoPaw Project Digest: 2026-07-17

## 1. Today's Overview
CoPaw is in a **high-velocity** state, with 44 issues and 46 PRs updated in the last 24 hours, indicating a very active development and community cycle. The project shows a healthy **commitment to stability** following the recent v2.0.0 release, with a strong focus on fixing regressions (memory leaks, session handling, upgrade woes) and improving cross-platform robustness (Windows UAC, Docker timezones). While user frustration is evident around the v2.0 migration and new "memory" features, the development team is responding rapidly with targeted fix PRs. Activity this week signals the team is trying to harden v2.0.0.post2 before a potential stable release.

## 2. Releases
**No new releases were published today.**

Observations: The project is currently in a "post-release" patch cycle (v2.0.0.post2). The velocity of bug reports suggests a release candidates (v2.0.0.post3 or similar) is likely imminent to address the accumulation of critical bugs.

## 3. Project Progress
Of the **46 PRs updated**, **25 were merged/closed** today. The focus was heavily on stability and fixing regressions introduced in v2.0:
- **Windows & CLI Fixes:** A significant fix for the Windows Desktop app's "Run as Admin" issue was merged in PR #6127 (conditional UAC elevation).
- **Chat & Memory Integrity:** Backend/frontend fixes were merged to fix session ordering (PR #6180) and preserve streaming whitespace (PR #6166).
- **Infrastructure:** A fix for Docker container timezone sync was merged (PR #6192), and cron task updates were fixed to preserve runtime fields (PR #6200).
- **Channels:** A major refactor (PR #6168) was merged to fix memory leaks in Mattermost and other channels by bounding unbounded state collections.
- **CI/QA:** A dedicated PR (PR #6185) adapted the end-to-end test suite to the v2.0.0 UI redesigns, ensuring test stability.

## 4. Community Hot Topics
The community is deeply engaged, primarily discussing **pain points related to the v2.0 upgrade**.

- **[Issue #6158] Token Usage Anomaly:** A user reported 28 million DeepSeek tokens consumed without any direct usage. This points to potential background processes (cron, Dify-style workflows?) eating up quotas silently. **Underlying need:** Desperate need for a usage dashboard and audit log.
    - URL: [Issue #6158](https://github.com/agentscope-ai/QwenPaw/Issues/6158)
- **[Issue #5995] Silent Message Drops:** A critical UX bug where messages are silently dropped when a session is busy. The user (feng183043996) is a power user reporting core interaction failures. **Underlying need:** Robust session queuing and user feedback for "busy" states.
    - URL: [Issue #5995](https://github.com/agentscope-ai/QwenPaw/Issues/5995)
- **[Issue #6196 / PR #6192] Docker Timezone:** UTC-only logs in Docker containers caused confusion for cron scheduling. The fix was merged within 24 hours of the report, showing excellent responsiveness. **Underlying need:** Enterprise/production deployment reliability.
    - URL: [Issue #6196](https://github.com/agentscope-ai/QwenPaw/Issues/6196)
- **[Issue #6155] Upgrade from 1.x to 2.0:** A detailed bug report listing 4 distinct issues found after migration, including embedding mapping and auto-memory bugs. **Underlying need:** A smoother, documented migration path from v1 to v2.
    - URL: [Issue #6155](https://github.com/agentscope-ai/QwenPaw/Issues/6155)

## 5. Bugs & Stability
The bug volume is **high**, primarily concentrated on the v2.0 release.

- **Critical / High Severity:**
    - **Session/Context Loss:** Issues #6074 and #6047 describe agents forgetting context after switching agents or starting a new chat. This is a fundamental UX killer. *No fix PR yet.*
    - **Silent Message Drops (#5995):** Messages are lost without warning. *No fix PR yet.*
    - **Windows Admin Privileges (#6161, #6169):** Two separate reports confirm the v2 app is broken for standard users on Windows. *Fix PR #6127 is in review.*
    - **2.0 "Amnesia" (#6148):** Users report severe memory loss and a broken `/compact` command. *Fix likely in the works related to auto-memory (PR #6142).*
- **Medium Severity:**
    - **Chat UI Glitches (#6129):** Missing spaces/line feeds in streaming thinking blocks. *Fix PR #6166 merged.*
    - **Docker Timezone (#6188):** Fixed by PR #6192 (merged).
    - **LLaMA MCP Crash (#6201):** A specific PubMed MCP tool crashes local LLM inference. *No fix yet.*
- **Low Severity:**
    - **QQ Bot Image Path Error (#6152):** Pydantic validation fails on local file paths. *Fix likely related to channel rework.*

## 6. Feature Requests & Roadmap Signals
User requests are shifting from "add more features" to **"fix the core experience."**

- **Reusable Workflows (#6163):** A sophisticated feature request for a visual workflow orchestrator with audit trails. This is a long-term vision item, unlikely for the next patch but indicative of the platform's trajectory.
- **Whitelist CIDR Support (#6048):** A request for network-level access control, suggesting enterprise/SaaS deployment interests.
- **Standalone Python Environment (#6160):** A common request for Desktop users whose system Python is unreliable. This suggests a desire for a more "batteries-included" desktop experience.
- **Independent Runtime (#6160) & Non-Tauri Variant (#6076):** These two requests combined strongly signal that the **Desktop (Tauri)** packaging is creating friction for specific user segments (Win7, Conda users).
- **Policy Management UI (#5880):** Users want to delete/edit approval rules, indicating a need for self-service governance.

**Prediction for next release (v2.0.0.post3 or v2.1):**
Fix heavy release. Likely includes: Windows UAC fix, core session/memory fixes, Docker timezone, and perhaps the new "context usage indicator" (PR #6195).

## 7. User Feedback Summary
- **Positive:** The user asking about a non-Tauri variant (#6076) explicitly calls it a "great open-source project." The speed of PR merges for reported bugs (e.g., #6196 to #6192) shows a responsive team, which users will appreciate.
- **Negative / Frustration:**
    - **"Memory is broken"** - The most consistent complaint. Users feel the agent "forgets" too much, and new features (auto-memory) are causing regressions.
    - **"Windows is broken"** - The forced admin requirement is blocking standard users and headless launches.
    - **"v2.0 broke what worked in 1.x"** - Issues like #6155 and #6148 highlight that the core AgentScope upgrade introduced many regressions.

## 8. Backlog Watch
The following items are lingering without maintainer resolution and represent risk:

- **[Issue #5821] Granular `rejects_media`:** A technical feature request from 2026-07-06. It has 2 comments, suggesting it's a niche but well-defined enhancement that has stalled.
    - URL: [Issue #5821](https://github.com/agentscope-ai/QwenPaw/Issues/5821)
- **[Issue #5880] Policy Deletion UI:** Simple UX request for deleting "Always Allow" rules. Open for a week with 2 comments. No PR or assignee. This slows down power users.
    - URL: [Issue #5880](https://github.com/agentscope-ai/QwenPaw/Issues/5880)
- **[Issue #5995] Silent Message Drops:** Despite being a critical bug, this high-profile issue from 2026-07-12 has seen no maintainer assignment or PR. It is a ticking time bomb for user trust.
    - URL: [Issue #5995](https://github.com/agentscope-ai/QwenPaw/Issues/5995)

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

# ZeptoClaw Project Digest — 2026-07-17

## Today's Overview
ZeptoClaw saw a burst of **documentation-focused closure activity** in the last 24 hours, with **5 issues all closed** and **zero open issues or pull requests**. The project remains in a **low-maintenance, high-completion cadence** — no new code merges or releases, but steady progress on security documentation tasks. All closed items were authored by YLChen-007 and focused on classifying "D2 trigger way" evidence for individual CVEs. The lack of open PRs or new releases suggests the team is currently in a **validation and documentation phase** rather than active feature development. Project health appears stable, with no regressions, crashes, or unresolved bugs reported.

## Releases
No new releases today. The latest available release remains unchanged from prior dates.

## Project Progress
- **Merged/Closed PRs today: 0** — no pull requests were merged or closed.
- **Issues closed today: 5** — all are documentation issues (#631, #632, #633, #634, #635) under `docs(security)` that completed source-verified trigger path analysis for specific CVEs (Issue 264, 268, 271, 329, 466). Each involved updating `d2_xclaw_trigger_way` in issue-security JSON files and writing workflow receipts. No code-level features or fixes were advanced.

## Community Hot Topics
The only community activity came from **one contributor (YLChen-007)** across five issues. Each issue received exactly **1 comment** and **0 reactions**, indicating low public engagement:
- [#631: docs(security): classify D2 trigger way for Issue 264](https://github.com/qhkm/zeptoclaw/issues/631)
- [#632: docs(security): classify D2 trigger way for Issue 268](https://github.com/qhkm/zeptoclaw/issues/632)
- [#633: docs(security): classify D2 trigger way for Issue 271](https://github.com/qhkm/zeptoclaw/issues/633)
- [#634: docs(security): classify D2 trigger way for Issue 329](https://github.com/qhkm/zeptoclaw/issues/634)
- [#635: docs(security): classify D2 trigger way for Issue 466](https://github.com/qhkm/zeptoclaw/issues/635)

**Underlying need:** These issues are part of a systematic effort to **document and classify attacker trigger methods** for prompt-injection or LLM-mediated vulnerabilities, likely for a security audit or CVE submission pipeline. The "D2" classification and "prompt-mediated trigger" terminology suggests a taxonomy being built for attack surface analysis. No broader user discussion is visible.

## Bugs & Stability
No bugs, crashes, or regressions were reported today. The project maintains a clean stability record in this snapshot.

## Feature Requests & Roadmap Signals
No new feature requests were filed today. The ongoing work on security trigger classification may indicate a **planned CVE disclosure or security hardening release** in the near future. Based on the pattern of CSV row analysis (rows 121–125 across issues), a **documentation or audit completion milestone** could be imminent. No signals point to new user-facing features being requested.

## User Feedback Summary
No user feedback was present in today's issues or PRs. The only participant (YLChen-007) appears to be an internal contributor or security researcher, not an end user. No satisfaction or dissatisfaction signals are available.

## Backlog Watch
**No long-unanswered issues or PRs identified.** All 5 issues from the last 24 hours were closed within hours of creation. The project has zero open issues and zero open PRs in this window. The maintainer queue is clear, with no items requiring attention. This could indicate either a **very responsive team** or a **low-traffic project** between major feature cycles.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

# ZeroClaw Project Digest — 2026-07-17

## Today's Overview

ZeroClaw shows **sustained high development velocity** with 50 PRs and 26 issues updated in the last 24 hours, though the vast majority (46 PRs open, 24 issues open) remain in progress. The project is deep in a **major architectural refactoring cycle**, with multiple large RFCs and tracker issues converging on provider unification (#5937), memory subsystem redesign (#9048, #9103), and a comprehensive plugin channel runtime stack (#8862, #8863, #8852). No new releases shipped today; the team appears heads-down on the v0.8.4 maintenance train (#8357) targeting July 31. A notable personnel change occurred — `singlerider` has left the project, triggering a CODEOWNERS cleanup (#9107).

---

## Releases

**No new releases** were published today. The team is working toward v0.8.4 (target: July 31, 2026) tracked in #8357, which follows the v0.8.3 release that shipped with three parallel provenance/signing mechanisms now being consolidated (#9101).

---

## Project Progress

### Merged/Closed Today (6 items)
| Item | Type | Description |
|------|------|-------------|
| [#8798](https://github.com/zeroclaw-labs/zeroclaw/issues/8798) | Closed (wontfix) | RFC to consolidate `/ws/chat` and `/acp` onto single wire protocol — declined |
| [#7320](https://github.com/zeroclaw-labs/zeroclaw/issues/7320) | Closed | v0.8.3 milestone tracker — all child trackers closed, final release validation remaining |
| [#9107](https://github.com/zeroclaw-labs/zeroclaw/pull/9107) | Merged/Open | Removed departing maintainer @singlerider from 44 CODEOWNERS entries |
| [#9104](https://github.com/zeroclaw-labs/zeroclaw/pull/9104) | Open (new) | Added `grok_cli` subprocess model provider for Grok via local CLI |
| [#9105](https://github.com/zeroclaw-labs/zeroclaw/pull/9105) | Open (new) | Fixed Lucid ARM cold starts — raised timeouts from 500ms→3s |
| [#9106](https://github.com/zeroclaw-labs/zeroclaw/issues/9106) | Open (new) | New RFC: A2A outbound client (A2ATool) for inter-agent calls |

### Active Feature Work
- **Channel plugin runtime stack** (JordanTheJet): Six stacked PRs (#8852, #8855, #8857, #8862, #8863, #8923) advancing WASM channel plugins — webhook ingress, WebSocket support, raw TCP+TLS, mirror channel parity. This is the largest single workstream.
- **Gateway OpenAI-compatible endpoint** (REL-mame): PR #8486 adds a REST `/v1/chat/completions` endpoint for LangChain/Continue.dev compatibility.
- **Inkbox native channel** (dimavrem22): PR #8384 adds email+SMS+voice+iMessage channel with Quickstart onboarding.
- **Herdr observability** (eugeneb50): PR #8337 integrates Herdr agent status reporting for CLI interactive mode.

---

## Community Hot Topics

### Most Active Discussions

1. **[#5937](https://github.com/zeroclaw-labs/zeroclaw/issues/5937) — Unify providers architecture** (11 comments)
   - *Underlying need*: Fragmented provider configuration with inconsistent reqwest usage. This is foundational — every provider integration touches this code. The `risk:high` flag and long duration (since April) suggest a complex refactor touching many subsystems.

2. **[#7952](https://github.com/zeroclaw-labs/zeroclaw/issues/7952) — Optional broad-channel prebuilts** (7 comments)
   - *Underlying need*: Users configuring channels not in the default bundle face confusion. Community wants optional binary variants without compromising the lean default install experience.

3. **[#9101](https://github.com/zeroclaw-labs/zeroclaw/issues/9101) — Consolidate release attestation mechanisms** (5 comments)
   - *Underlying need*: v0.8.3 shipped with three parallel signing mechanisms (cosign, GitHub attestations, SLSA) from uncoordinated PRs. Community wants one signing story and ~20 assets instead of 53 — a CI efficiency and security audit concern.

4. **[#8832](https://github.com/zeroclaw-labs/zeroclaw/issues/8832) — Gateway-local Kanban board** (5 comments)
   - *Underlying need*: Operators want visibility into "what is my agent working on?" — inspired by OpenClaw Workboard plugin. Signals demand for agent task visualization in the web dashboard.

5. **[#9048](https://github.com/zeroclaw-labs/zeroclaw/issues/9048) — Separate conversation history from long-term memory** (5 comments)
   - *Underlying need*: Users experience memory mixing — session history and curated long-term memory are stored through same backend. This RFC proposes clean separation, critical for memory reliability.

---

## Bugs & Stability

### Critical Severity (S1 — workflow blocked)

| Issue | Description | Fix PR/Status |
|-------|-------------|---------------|
| [#8560](https://github.com/zeroclaw-labs/zeroclaw/issues/8560) | `browser_open` hangs agent turn when launcher fails — unbounded subprocess wait also affects TTS and ffmpeg | No fix PR yet; status:in-progress |
| [#9085](https://github.com/zeroclaw-labs/zeroclaw/issues/9085) | Nested runtime panic in `try_enable_pgvector` when pgvector is enabled — gateway/agent startup blocked | No fix PR yet; status:accepted |

### High Severity (S2 — degraded behavior)

| Issue | Description | Fix PR/Status |
|-------|-------------|---------------|
| [#9078](https://github.com/zeroclaw-labs/zeroclaw/issues/9078) | Serial transport desynchronized after non-matching response ID — `send_request` doesn't drain buffer | No fix PR yet; status:accepted |
| [#9089](https://github.com/zeroclaw-labs/zeroclaw/issues/9089) | Tool output supports `[IMAGE:]` but not `[AUDIO:]` markers — audio results reach model as literal text | No fix PR yet; status:accepted |
| [#9046](https://github.com/zeroclaw-labs/zeroclaw/issues/9046) | `models_cache.json` is read but never written — the "run zeroclaw models refresh" hint cannot resolve it | status:in-progress |

### Stability Notes
- **PR #9105** (yanchenko): Fixes Lucid ARM cold starts by raising timeouts — a pragmatic fix addressing a real deployment pain point for ARM users.
- **PR #8536** (mazhuima): Preserves inner `Elapsed` error in hardware timeout handlers — improves debuggability for serial transport issues.

---

## Feature Requests & Roadmap Signals

### Likely for v0.8.4 (target: July 31)
- **Provider unification** (#5937) — refactoring providers architecture is foundational and has been in progress since April
- **`session_ttl_hours`** implementation (#8134) — stale channel session cleanup, accepted and in-progress
- **Memory separation** (#9048) — conversation history vs. long-term memory, accepted RFC
- **Kanban board** (#8832) — gateway dashboard visualization, accepted RFC

### Emerging Signals
- **A2A outbound** (#9106) — filed today, proposes A2ATool for inter-agent collaboration; likely targets v0.9
- **Separate authoritative memory from enrichment** (#9103) — filed today, addresses Lucid-as-backend conflation
- **Grok CLI provider** (PR #9104) — community demand for Grok integration via local CLI
- **Realtime speech-to-speech** (#8780) — Gemini Live channel; accepted but likely a larger effort

### Prediction
The plugin channel runtime stack (PRs #8852–#8923) appears to be the **primary v0.8.4 feature**, along with the memory separation RFC. Provider unification (#5937) may slip to v0.9 given its complexity and long duration.

---

## User Feedback Summary

### Pain Points (from Issues)
1. **Memory confusion**: Users report session history and long-term memory mixing in critical paths (#9048) — "implementation still mixes them in important paths"
2. **Installation confusion**: Default prebuilt bundles lack channels users configure, creating confusion (#7952)
3. **Hang/crash on startup**: pgvector panic blocks gateway/agent startup (#9085) — "S1 - workflow blocked"
4. **Missing audio support**: Tool output markers only support images, not audio (#9089) — "S2 - degraded behavior"
5. **Cached model never written**: `models_cache.json` read-but-never-written creates perpetual hint messages (#9046)
6. **Pipeline tool bypasses permissions**: `execute_pipeline` sub-tool execution ignores `ToolAccessPolicy` (PR #7960) — a security and UX concern
7. **Lucid ARM cold starts fail**: Default timeouts too low for ARM64 (PR #9105) — "healthy local-embedding cold start measured about 1.4-1.6 seconds"

### Satisfaction Signals
- Active community contribution: 14 distinct authors in today's data (including first-time names like `kingstar001`, `yanchenko`, `legokichi`)
- v0.8.3 shipped successfully with three attestation mechanisms — while redundant, all three work (per #9101)
- Herdr integration (#8337) and Inkbox channel (#8384) show expanding ecosystem appeal

---

## Backlog Watch

### Long-unanswered Items Needing Maintainer Attention

| Issue | Age | Reason for Concern |
|-------|-----|--------------------|
| [#8367](https://github.com/zeroclaw-labs/zeroclaw/issues/8367) — Capability-aware documentation RFC | 21 days (created June 26) | `status:blocked, needs-maintainer-review` — agents cannot answer about capabilities they lack; critical for UX |
| [#8541](https://github.com/zeroclaw-labs/zeroclaw/issues/8541) — Matrix thread-scoped history | 17 days (created June 30) | `status:blocked, needs-maintainer-review` — affects Matrix channel deployments |
| [#8398](https://github.com/zeroclaw-labs/zeroclaw/issues/8398) — Plugin permission model open questions | 20 days (created June 27) | `needs-author-action` — two permission models tried, none settled; foundational for plugin security |
| [#8891](https://github.com/zeroclaw-labs/zeroclaw/issues/8891) — Persistent memory parity tracker | 8 days (created July 9) | `needs-maintainer-review` — coordinates multi-PR rollout; without review, memory subsystem stalls |

### PRs Needing Author Action (stalled)
- [#8486](https://github.com/zeroclaw-labs/zeroclaw/pull/8486) — OpenAI endpoint (XL size, 18 days stalled)
- [#8571](https://github.com/zeroclaw-labs/zeroclaw/pull/8571) — OAuth credential fix (17 days stalled)
- [#7960](https://github.com/zeroclaw-labs/zeroclaw/pull/7960) — Pipeline tool permissions (28 days stalled)
- [#8966](https://github.com/zeroclaw-labs/zeroclaw/pull/8966) — Max context fallback fix (6 days stalled)
- [#8384](https://github.com/zeroclaw-labs/zeroclaw/pull/8384) — Inkbox channel (20 days stalled)

**Alert**: The blockage of #8367 and #8541 for 17–21 days, combined with the departure of `singlerider` (who was sole owner of `zeroclaw-api` and `zeroclaw-infra` paths), creates risk that important RFCs and Matrix-specific features remain unaddressed. The new CODEOWNERS routing (#9107) may help but the project should monitor these items closely.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*