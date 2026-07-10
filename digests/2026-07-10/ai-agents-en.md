# OpenClaw Ecosystem Digest 2026-07-10

> Issues: 500 | PRs: 500 | Projects covered: 13 | Generated: 2026-07-10 01:59 UTC

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

Based on the provided GitHub data for **OpenClaw** on **2026-07-10**, here is the project digest.

---

## OpenClaw Project Digest: 2026-07-10

### 1. Today's Overview

OpenClaw is experiencing a significant surge in community activity, with **500 issues** and **500 pull requests** updated in the last 24 hours. This high volume indicates a very active user base and a substantial maintenance load, but also a healthy pipeline of incoming contributions. Despite the high activity, project health is mixed: while there is a strong focus on fixes, the backlog of critical, long-standing issues remains a concern. A small flurry of maintainer-driven Pull Requests suggests core maintainers are actively addressing infrastructure and CI pipeline stability.

### 2. Releases

**No new releases were recorded for this date.**

The project has not published a new version since the data cut-off. Given the high number of open PRs and fixes in progress, users are running on a commit-by-commit basis (`main` branch) to receive the latest patches.

### 3. Project Progress

**Today's closed/merged PRs** (total: ~200) included several notable improvements:

- **Plugin & Channel Reliability:**
    - **PR #101023** (open): Fixed an issue where a failed persistence write could cause plugin channels to route messages to the wrong session.
    - **PR #102445** (open): Fixed cron channel failure alerts dropping when a global webhook destination was configured.
- **Performance & Stability:**
    - **PR #102971** (open): Replaced an O(n^2) character loop in `stripDisallowedChatControlChars` with a regex, preventing event-loop blocking on large messages (up to 1MB+).
    - **PR #102409** (open): Fixed a cropping bug in the proxy-capture preview that could corrupt UTF-8 characters.
- **Configuration & Security:**
    - **PR #102619** (open): Added validation to reject `cron.sessionRetention: "0h"` to prevent silent data loss.
    - **PR #102953** (open): Redacted OAuth error response bodies in fetch error messages to prevent credential leakage.
- **Continuous Integration:**
    - **PR #103237** (closed): Fixed a CI pipeline failure where a GitHub push timeout could falsely fail a release-performance check.
    - **PR #103244** (open): Updated CI infrastructure tooling to comply with security patches.

### 4. Community Hot Topics

The community is most engaged with issues concerning **reliability and data integrity**.

- **Issue #44925** [Bug]: Subagent completion silently lost (21 comments). Users are deeply concerned about a "silent failure" mode where sub-agent results are lost without notification, degrading trust in task orchestration.
- **Issue #63918** [Closed] Cron agentTurn sends thinking=none (18 comments). High engagement on resolved issue, indicating this model compatibility problem was a widespread pain point for automation users.
- **Issue #99241** [Bug]: Tool outputs render as unreadable image attachments (15 comments). A critical "platinum hermit" issue highlighting a major UX failure in long-running tasks where agent visibility of tool results is lost.
- **Issue #45740** [Bug]: gh-issues skill vulnerability (14 comments). A security issue drawing concern, as it demonstrates a path for prompt injection from external data sources.

### 5. Bugs & Stability

Several high-severity bugs were flagged or are under active discussion.

| Issue ID | Severity | Title | Fix PR Exists? |
| :--- | :--- | :--- | :--- |
| **#44925** | P1, Diamond | Subagent completion silently lost | No (Needs Maintainer Review) |
| **#99241** | P1, Platinum | Tool outputs render as unreadable images | No |
| **#89278** | P1, Diamond | Codex OAuth refresh causes auth timeout | No |
| **#52249** | P1, Diamond | ACP parent session stuck until refresh | No |
| **#84569** | P1, Diamond | WhatsApp session stalls on long model_call | No |
| **#45494** | P1, Platinum | Cron jobs silently time out on LLM API errors | No |
| **#43996** | P1, Diamond | Sandbox container exit with `operation not permitted` | No |

**Top Regressions:** Issues **#102175** (message_tool_only destabilizing prompt cache) and **#100782** (all tool results rendered as images in Discord) are marked as regressions from recent releases, indicating areas where new code has introduced instability.

### 6. Feature Requests & Roadmap Signals

- **Persistent Task Status (Issue #52640):** Users want a "first-class persistent task-status surface" for long-running channel turns (e.g., in Discord). This strongly suggests the next release will include a UI element to display running task progress, likely leveraging the work on `sessions_yield` and pause states.
- **Pre-Reset Memory Flush (Issue #45608):** A request for `/new` and `/reset` commands to trigger a "silent agentic memory flush" before destroying the session. This is a highly requested (4 👍) feature that likely aligns with an upcoming roadmap item for improved agentic memory management.
- **Configurable Session Startup Prompt (Issue #45501):** Users want to customize the message injected into a new session after `/reset`. This is a low-risk, high-impact quality-of-life improvement that could easily be added in the next minor release.

### 7. User Feedback Summary

- **Pain Points:**
    - **Silent Failures:** Users are frustrated by the lack of error feedback in subagent orchestration, cron jobs, and tool routing (Issues #44925, #45494, #53408).
    - **Data Loss:** The risk of losing tool outputs or context leads to a lack of trust in long-running automation tasks (Issues #99241, #53628).
    - **Configuration Friction:** Users of Docker containers and non-standard environments face significant friction (Issue #92516, #45765).
- **Use Cases:**
    - **Automation & DevOps:** Cron jobs and webhooks are clearly critical workflows that are facing instability.
    - **Multi-Platform Chat:** Users are heavily reliant on Discord, Telegram, and WhatsApp channels.
    - **Agentic Workflows:** The demand for reliable sub-agent spawning and parent-child session management is high.
- **Satisfaction:**
    - The high volume of issue creation indicates active, dedicated users.
    - Pull requests like #101023 (fixing binding maps) show that the community is actively contributing to solving these pain points, a sign of a healthy open-source ecosystem.

### 8. Backlog Watch

These are important items that appear to be stuck or are awaiting crucial maintainer input:

- **Issue #45740** (P2, Security, 2026-03-14): The `gh-issues` prompt injection vulnerability. Despite being a security risk with a clear fix path, it remains open and unassigned.
- **Issue #43996** (P1, 2026-03-12): The `No-new-privileges` sandbox crash. This is a high-severity issue affecting sandbox reliability in common Docker configurations and has been outstanding for months.
- **Issue #45718** (P2, 2026-03-14): Session bloat from accumulating `skillsSnapshot`. This is a known performance sink that continues to grow, leading to context overflow errors with no action taken.
- **PR #75662** (P2, 2026-05-01): A fix for pausing yielded main-session runs. This PR is mature but marked as **"waiting on author"** despite being open for over two months, suggesting it may be complex to finalize or has been deprioritized.

---

## Cross-Ecosystem Comparison

Here is the cross-project comparison report, generated from the provided community digest summaries.

---

## Cross-Project Ecosystem Report: 2026-07-10

### 1. Ecosystem Overview

The open-source personal AI assistant ecosystem is in a phase of high-velocity stabilization. While feature development continues, the community’s primary focus has shifted to hardening reliability, plugging security vulnerabilities, and addressing regressions introduced by recent rapid releases. There is a strong, cross-cutting user demand for agentic trustworthiness—specifically, silent failures, data loss, and unreliable tool orchestration are the most cited pain points. Simultaneously, a clear architectural divergence is appearing between projects aiming for lightweight, modular, single-purpose agents and those building towards full-featured, multi-platform, production-ready platforms. The landscape is becoming increasingly polarized around developer experience versus end-user deployment readiness.

### 2. Activity Comparison

| Project | Issues Updated (24h) | PRs Updated (24h) | Merged/Closed PRs | Release Status | Health Score | Notes |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **OpenClaw** | 500 | 500 | ~200 | No Release | 8/10 | Highest raw volume; heavy maintenance & community contribution |
| **NanoBot** | 22 | 22 | 4 | No Release | 7/10 | High-velocity; focused on regressions & security |
| **Hermes Agent** | 50 | 50 | 15 | No Release (v0.18.1) | 7/10 | Moderate triage bottleneck; P1 credential & gateway bugs |
| **PicoClaw** | 3 | 16 | 4 | No Release (v0.2.9) | 6/10 | Moderate activity; critical config & Matrix bugs blocking new users |
| **NanoClaw** | 9 | 17 | 3 | No Release | 7/10 | Heavy development; security fix & scheduled-tasks train advancing |
| **NullClaw** | 0 | 0 | 0 | N/A | N/A | No activity recorded |
| **IronClaw** | 32 | 28 (merged) | 28 | No Release (pending) | 7/10 | Major bug-bash day; Slack integration in critical state |
| **LobsterAI** | 0 | 14 | 11 | No Release | 8/10 | High throughput, stable polish cycle |
| **Moltis** | 0 | 1 | 0 | No Release | 6/10 | Very quiet; only GPT-5.6 model support PR |
| **CoPaw** | 35 | 50 | 32 | **v2.0.0-beta.5** | 8/10 | High activity, shipped a patch; critical v2.0 regressions emerging |
| **TinyClaw** | 0 | 0 | 0 | N/A | N/A | No activity recorded |
| **ZeptoClaw** | 0 | 0 | 0 | N/A | N/A | No activity recorded |
| **ZeroClaw** | 36 | 50 | 11 | No Release (v0.8.x) | 8/10 | Intense dev cycle; SSRF & MCP leak fixes advancing |

### 3. OpenClaw’s Position

- **Advantages vs. Peers:** OpenClaw commands the largest community and the highest raw activity (500+ issues/PRs updated). It serves as the foundational core, with downstream projects (LobsterAI, PicoClaw, NanoClaw) explicitly building on its gateway and API. Its community is the most self-sustaining and contributor-driven.
- **Technical Approach Differences:** OpenClaw operates as a robust, low-level reference implementation focused on core protocols (HTTP, WebSocket), channel plugins, and persistence. It is less opinionated about user interface or advanced agentic patterns (e.g., subagent orchestration), leaving that to higher-level projects.
- **Community Size:** The community is large, vocal, and deeply technical. The main pain point is the sheer volume of long-standing, high-severity bugs (subagent completion loss, tool result rendering) that are being outpaced by new feature contributions. While the ecosystem is healthy, the core maintainers appear stretched.

### 4. Shared Technical Focus Areas

The following requirements are emerging across multiple projects, indicating systemic needs:

1.  **Subagent & Task Orchestration Reliability:** A critical trust gap in multi-step workflows.
    - **OpenClaw:** Subagent completion silently lost (#44925)
    - **Hermes Agent:** Agent violates own saved rules (#60429)
    - **NanoClaw:** Recurring reminders stop after first fire (#2997)
    - **ZeroClaw:** reasoning_content lost in tool-call loops (#6672)
2.  **Channel UX Consistency & Reliability:** Silent failures in message delivery.
    - **OpenClaw:** Tool outputs render as unreadable image attachments (#99241)
    - **NanoBot:** WhatsApp replies sent to wrong groups (#4823); Matrix reconnection failure (#3203)
    - **Hermes Agent:** Discord heartbeat stall (#60794); Gateway session data loss (#61145)
    - **CoPaw:** Feishu channel unreliably drops messages (#5757)
3.  **Security Hardening:** Preventing credential leakage and command injection.
    - **OpenClaw:** gh-issues skill prompt injection (#45740)
    - **NanoBot:** Symlink workspace escape (#4629)
    - **Hermes Agent:** OAuth error body credential leakage (part of PR #102953)
    - **NanoClaw:** MCP server args/env hidden during approval (#2827/#2762)
    - **CoPaw:** `${HOME}` bypass in rm detection (#5866)
    - **ZeroClaw:** SSRF fixes across image_gen, file_download (#8826, #8827, #8713)
4.  **Observability & Debugging:** Users need better visibility into agent actions and failures.
    - **Hermes Agent:** "Unknown" App on OpenRouter logs (#61099)
    - **ZeroClaw:** Tool self-awareness gap (agent doesn't know it can add cron) (#5862)
    - **LobsterAI:** No message timestamps (#1339)

### 5. Differentiation Analysis

| Dimension | OpenClaw / ZeroClaw | Hermes Agent / CoPaw | NanoBot / NanoClaw | PicoClaw / TinyClaw |
| :--- | :--- | :--- | :--- | :--- |
| **Primary User** | Developer / System Integrator | Power User / Enterprise | Enthusiast / Tinkerer | Embedded / Edge Hobbyist |
| **Core Architecture** | Modular, protocol-driven, multi-channel plugin system | Full-featured, opinionated agent (Gateway + rich TUI) | Lightweight, single-purpose, tool-focused | Minimal footprint, low-resource (ARM, Raspberry Pi) |
| **Feature Focus** | Reliability, protocol compliance, security | Advanced agentic patterns (subagents, credentials, cron) | Ease of use, quick setup, specific channel support (WhatsApp, Telegram) | Resource efficiency, offline-capable, DeltaChat |
| **Deployment Model** | Docker/Container, CLI daemon | Desktop .exe/DMG, headless server | Simple binary, minimal dependencies | Cross-compiled, single binary |
| **Community Maturity** | Mature, large, self-sustaining | Maturing, actively triaged | Growing, beginner-friendly | Niche, focused |

### 6. Community Momentum & Maturity

- **Tier 1: Rapidly Iterating (Production Readiness Focus)**
    - **OpenClaw, ZeroClaw, CoPaw:** High-velocity, multi-track development. These projects are actively shipping patches and new features while dealing with scaling pains. They are closest to or in public beta/stable.
- **Tier 2: Active Stabilization (High-Volume Bug Fixing)**
    - **NanoBot, Hermes Agent, NanoClaw, IronClaw:** High throughput with a clear emphasis on squashing regressions and closing security gaps. These projects are establishing their stable baseline.
- **Tier 3: Steady Polish**
    - **LobsterAI, PicoClaw:** Lower volume but consistent activity. Focused on UX improvements, localization, and small feature requests.
- **Tier 4: Incubating / Dormant**
    - **Moltis, NullClaw, TinyClaw, ZeptoClaw:** Minimal to no activity. Moltis is the only one with a signal (GPT-5.6 support PR), suggesting it is in a maintenance-only phase.

### 7. Trend Signals

The following industry trends are extracted from community feedback and issue patterns, and are valuable for AI agent developers:

- **Agentic Trust is the #1 Barrier to Adoption:** Users are not worried about AI capability; they are worried about **silent failures** (subagent lost, message not sent, task not scheduled). The ecosystem is currently failing on "promise keeping." This is a massive opportunity for developers who can implement robust observability, deterministic retries, and user-visible confirmations.
- **Multi-Model & Provider Resilience is a Must-Have:** The demand for credential pooling (Hermes Agent, ZeroClaw), automatic failover, and provider-agnostic code paths is driven by operational frustration. A single provider outage should not take down a user’s entire automation.
- **The "Headless" Agent is the Default Power-User Pattern:** The clear signal from Hermes Agent (remote agent, local tool execution #18715), IronClaw (CLI/TUI for secrets), and NanoClaw (MCP server approval transparency) is that serious users run agents on servers, not desktops. This demands remote-CLI-first UX, API-based access, and robust session management.
- **Security is Shifting Left to the Approval Flow:** Instead of post-hoc audits, the community is demanding real-time, transparent approval for privileged actions (MCP server add, `rm -rf`, file overwrites). The design of these approval cards is becoming a critical UX battleground.
- **Context Management is the New LLM Benchmark:** As context windows grow (1M+), the ability to **intelligently compress, prune, and search** conversation history without breaking tool call structures (CoPaw #5856) is becoming a key differentiator. This is shifting from a performance optimization to a core reliability feature.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

Here is the project digest for NanoBot, based on data from 2026-07-10.

---

## NanoBot Project Digest: 2026-07-10

### 1. Today's Overview
NanoBot is experiencing a period of high maintenance velocity and community engagement. In the last 24 hours, 22 issues and 22 pull requests were updated, indicating a very active development cycle. A significant cluster of this activity is focused on recent regressions and stability fixes, particularly concerning the WhatsApp channel, MCP reconnection, and subprocess management. While new feature development continues, the project's immediate priority is hardening the platform against bugs introduced in recent releases.

### 2. Releases
No new releases were published today.

### 3. Project Progress
Four pull requests were closed/merged today, reflecting a focus on bug fixes and build improvements:
- **[#4859] fix(matrix): preserve mxc markdown image sources** - Fixes a regression where Matrix image URLs were incorrectly sanitized.
- **[#4857] Add Dockerfile arg to override optional Python dependencies** - Enhances build configurability, allowing users to specify which extras (e.g., WhatsApp bridge) to install at build time.
- **[#4629] fix(exec): block relative symlink workspace escapes** - Closes a security vulnerability where restricted commands could use symlinks to escape the workspace sandbox.
- **[#4862] fix(exec): isolate exec session managers** - Refactors exec session management to prevent cross-agent interference, ensuring each agent loop has its own isolated session manager.

### 4. Community Hot Topics
- **WhatsApp Group Regression (Issue #4823)** - The most active open issue, this reports a severe bug in the WhatsApp channel where replies are now being sent to all groups instead of the intended one. This is a high-priority regression that breaks a core feature for many users.
- **Endless Loop Bug (Issue #4864)** - A user reports a critical blocking bug where the `complete_goal` tool call causes an infinite loop because the gateway is parsing the parameters incorrectly. This directly prevents users from using the goal-seeking feature.
- **Missing CLI Commands (Issue #4860)** - A new user reports that the commands `nanobot onboard` and `nanobot webui` listed in documentation do not exist in the installed tool. This points to a documentation gap or a packaging issue that can severely degrade the onboarding experience.
- **Task-Specific Model Configuration (Issue #912)** - With 3 reactions, this long-standing feature request for using different models for conversation, tool use, and browsing remains a popular community desire.

### 5. Bugs & Stability
Several critical and high-priority bugs were reported today:
- **Critical: Endless loop on `complete_goal` (Issue #4864)** - A complete blocker for a core feature. This is a tool parameter serialization bug in the gateway layer. No fix PR is currently open.
- **High: Missing CLI commands (Issue #4860)** - A severe onboarding issue that indicates either a broken installation path or incorrect documentation.
- **High: MCP Reconnect Crash (PR #4843)** - A fix is already in review for a gateway crash that occurs when an MCP connection expires and tries to reconnect, specifically related to stale stack cleanup.
- **High: Zombie Subprocesses (PR #4840)** - A fix is in review for a process management bug where zombie child processes are left behind, potentially exhausting system resources.
- **Medium: Docker Build Failure (PR #4863)** - A fix is in review for a regression where a fresh Docker build fails due to an out-of-sync `package-lock.json` file.

### 6. Feature Requests & Roadmap Signals
- **Pre-handler Hooks (Issue #990)** - A user requests a configurable hook to bypass LLM processing for specific message patterns (e.g., `#diary`). This is a low-cost, high-efficiency feature that is a strong candidate for the next patch release.
- **Multi-Tenant Gateway (Issue #936)** - The request for a single gateway instance to manage multiple agents to reduce resource usage. This is a significant architectural change and is likely a longer-term roadmap item.
- **SimpleX Chat Integration (Issue #240)** - An old request for a new, decentralized channel with continued community interest (3 reactions). It remains on the backlog.

### 7. User Feedback Summary
- **Frustration with Stability**: A user stopped evaluation of the framework due to "too many hallucinations" with the `exec` tool (Issue #937), expressing a lack of confidence. The recent spate of regressions is likely to amplify this sentiment.
- **Onboarding Pain**: The missing CLI commands (Issue #4860) highlight a critical user experience failure for new adopters, directly contradicting the "get started" documentation.
- **Desire for Customization**: Users are actively requesting more granular control over model selection (Issue #912) and message routing (Issue #990) to manage costs and behavior, indicating a maturing user base with specific operational needs.
- **Operational Gaps**: The request for a subagent control plane (Issue #1006) and unbounded media disk growth (Issue #896) show that users are running into operational scaling issues in production-like environments.

### 8. Backlog Watch
- **Issue #912: Task-Specific Model Configuration** - Open since Feb 2026 with high community interest (3 👍). This is a frequently requested power-user feature that the maintainers should consider prioritizing for the next minor release.
- **Issue #1006: Control plane MVP for subagents** - Open since Feb 2026. This is an important operational feature for advanced users that has received no maintainer response. It represents a significant gap in the subagent feature set.
- **Issue #240: SimpleX Chat as a channel** - Open since Feb 2026 with 3 👍. While a niche request, it has been pending for months without any comment from the team.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

# Hermes Agent Project Digest — 2026-07-10

## Today's Overview

Hermes Agent shows high activity today with 50 issues and 50 PRs updated in the last 24 hours, though only 15 issues and 15 PRs were closed or merged — a closure rate of 30%, indicating a moderate triage bottleneck. No new releases were published during this period. The project's open-to-closed ratio (35 open vs 15 closed for both issues and PRs) suggests the maintainer team is processing inbound reports but may be falling slightly behind new submissions. The most significant activity centers around gateway reliability, authentication flows, and provider credential pool bugs, with several high-priority (P1/P2) items being addressed through concurrent PRs.

## Releases

**None.** There were no new releases published in the last 24 hours. The last reported version is v0.18.1 (2026-07-07), referenced in bug report #60794.

## Project Progress

Today's 15 merged/closed PRs addressed several infrastructure and reliability concerns:

- **Gateway connectivity hardening** — PR [#61767](https://github.com/NousResearch/hermes-agent/pull/61767) enforces reconnect contracts across QQ Bot and WeCom Callback adapters, restoring recovery after outages. PR [#61770](https://github.com/NousResearch/hermes-agent/pull/61770) restores Feishu/Lark group @mention events over WebSocket.
- **Export security** — PR [#61769](https://github.com/NousResearch/hermes-agent/pull/61769) completes HTML session-export hardening with nonce-based CSP and escaped role sinks.
- **Reasoning effort fixes** — PR [#61772](https://github.com/NousResearch/hermes-agent/pull/61772) fixes provider-only projection defects introduced when `max` became a valid reasoning effort value.
- **Credential rotation fixes** — PR [#61754] fixes Copilot token/base_url rotation bug; PR [#61712] fixes MoA fallback recovery path.
- **Memory provider** — PR [#55503] resolved a permanent write lock in the Holographic memory provider's `memory_store.db`.
- **Gateway session hygiene** — Issue [#61145] identified destructive DELETE behavior in auto-compression; relevant fixes are in progress.

## Community Hot Topics

The most active discussions reveal deep operational pain points:

### [Issue #18715](https://github.com/NousResearch/hermes-agent/issues/18715) — Remote agent with local tool execution (8 comments, 20 👍)
**Underlying need:** Users want a split architecture where a remote Hermes Agent instance handles skills/memory/sessions while tool execution (especially `terminal`) runs on their local machine. This is one of the highest-signal feature requests, suggesting many enterprise/power users run headless servers they cannot install arbitrary tools on. The 20-reaction count places it among the most desired features this month.

### [Issue #61487](https://github.com/NousResearch/hermes-agent/issues/61487) — Z.AI credential pool cascade-marks all keys (5 comments)
**Underlying need:** Multi-key credential pools are failing catastrophically — one key hitting quota exhausts all keys in the pool. This is a critical reliability concern for users depending on Z.AI as their primary provider with fallback keys.

### [Issue #60429](https://github.com/NousResearch/hermes-agent/issues/60429) — Agent violates own saved rules (4 comments)
**Underlying need:** A trust-damaging bug where agent-created rules/memory are not honored during subsequent interactions. Users report asking the agent to save rules to memory or skills, then watching it violate those exact rules. This strikes at the reliability of the agent's self-modification capabilities.

### [Issue #61099](https://github.com/NousResearch/hermes-agent/issues/61099) — OpenRouter logs show "Unknown" App (4 comments)
**Underlying need:** Operational visibility — users relying on OpenRouter can't identify their Hermes Agent traffic, breaking cost attribution and usage monitoring.

## Bugs & Stability

### Critical (P1)
- **Gateway session-hygiene data loss (Issue #61145)** — Auto-compression permanently DELETEs conversation transcripts instead of soft-archiving. Fix PR exists.
- **Discord heartbeat stall (Issue #60794,** [PR #61767](https://github.com/NousResearch/hermes-agent/pull/61767)) — `build_channel_directory` blocks the event loop with synchronous SQLite queries. A fix is in progress.

### High (P2)
- **Nous inference API unreachable (Issue #60715)** — All models time out; connection to `inference-api.nousresearch.com` fails even via curl. Needs repro.
- **Credential pool exhaustion bugs (Issues #61487, #61451)** — Z.AI and Anthropic providers both suffer from cascade exhaustion where a single model-specific 429 marks the entire credential as exhausted in the pool.
- **Model switch cross-wiring (Issues #47828, #61296)** — Switching models via `/mode` retains the old provider's `base_url`, causing 400 errors against mismatched endpoints. Two separate reports with fix PR [#61296](https://github.com/NousResearch/hermes-agent/pull/61296) now closed.
- **Skills disappearing after bootstrap sync (Issue #48877)** — Agent-created skills become unavailable after `hermes update` despite existing on disk.
- **Portal token expiry unrecoverable headlessly (Issue #58572)** — Gateway crashes with no remote recovery path; users on headless servers hit a hard wall.

### Moderate (P3)
- **Windows desktop installer failures (Issues #38963, #61657)** — Multiple reports of installer failing at app/desktop build step on Windows 11.
- **Honcho API key empty (Issue #61661)** — `honcho_conclude` tool sends empty API key, causing AuthenticationError.
- **Feishu Markdown tables unrendered (Issue #61643)** — Raw pipe syntax shown instead of rendered tables.
- **Token speed inaccurate (Issue #60583)** — Status bar tokens/sec reads below real speed for local OpenAI-compatible providers.

## Feature Requests & Roadmap Signals

### High Signal / Likely Next Version
1. **Remote agent with local tool execution** (Issue #18715, 20 👍) — Strongest community signal; would enable split-mode deployments for headless/power users.
2. **Self-hosted OIDC RP-Initiated Logout** (Issue #35410, 3 comments, 1 👍 + duplicate Issue #61243) — Critical for identity-management-conscious users, especially enterprises.
3. **Desktop-only thin client installer** (Issue #61329, 2 comments) — Complements the remote agent feature; users want a lightweight client that connects to an existing remote backend.

### Medium Signal / Likely Considered
1. **Auto reasoning mode** (Issue #40306, 1 comment) — ChatGPT-style automatic detection of when to think vs respond directly.
2. **Per-cron reasoning effort overrides** (Issue #23524, 3 comments) — Fine-grained control over thinking effort per scheduled job.
3. **Configurable startup/session panels** (Issue #17977, 1 comment) — Deeper TUI skin customization parity.

### Prediction
The **remote agent with local tool execution** (#18715) is the strongest roadmap signal and could appear in v0.19.0. The **credential pool cascade exhaustion bugs** (#61487, #61451) are likely to receive hotfixes in the next patch release given their severity for paying users.

## User Feedback Summary

### Pain Points
- **Installer reliability on Windows** – Multiple users report failures with the .exe installer (#38963, #61657), often at the app/desktop build step.
- **Credential pool unpredictability** – Users relying on multi-key pools (Z.AI, Anthropic) experience entire pool exhaustion from a single rate limit, undermining the redundancy benefit.
- **Agent self-modification trust issues** – Users report agent violating its own saved rules (#60429), eroding confidence in the agent's self-improvement capabilities.
- **Headless operation fragility** – When token expiry or crashes occur on remote servers, there is no recovery path without physical access (#58572).
- **Provider identification inconsistency** – OpenRouter users can't reliably identify Hermes Agent traffic in their logs (#61099).

### Use Cases Driving Activity
- **Multi-machine deployments** – Users want a server-agent + local-tools split architecture.
- **Enterprise identity management** – Strong interest in proper IdP session termination (RP-Initiated Logout).
- **Multi-provider redundancy** – Heavy use of credential pooling with Anthropic, Z.AI, and OpenAI across multiple keys.
- **Headless/remote operation** – Users running Hermes on home servers accessed via Telegram/Discord with no physical access.

### Sentiment
The tone across today's issues is **constructive but frustrated** — users are reporting precise, reproducible bugs with detailed evidence (curl outputs, error codes, screenshots), but several tickets express concern about the pace of resolution on credential pool exhaustion and data loss bugs. The 20-reaction issue for remote/local split suggests a vocal power-user base that sees Hermes as a production tool, not a toy.

## Backlog Watch

### Critical Unanswered Items
- **[Issue #17977](https://github.com/NousResearch/hermes-agent/issues/17977)** — Configurable TUI startup panels (created 2026-04-30, 73 days open, 1 comment, no maintainer response). One of the oldest open feature requests with demonstrated interest.

### Important Unresolved Bug Reports
- **[Issue #48877](https://github.com/NousResearch/hermes-agent/issues/48877)** — Skills disappearing after bootstrap sync (created 2026-06-19, 21 days open, P2). No fix PR linked despite reproducible evidence.
- **[Issue #58572](https://github.com/NousResearch/hermes-agent/issues/58572)** — Gateway crashes on token expiry with no recovery (created 2026-07-05, 5 days open, P2). Critical for headless deployments.
- **[Issue #60429](https://github.com/NousResearch/hermes-agent/issues/60429)** — Agent violates own rules (created 2026-07-07, 3 days open, P3, needs-repro). High trust impact if confirmed.
- **[Issue #60715](https://github.com/NousResearch/hermes-agent/issues/60715)** — Nous inference API unreachable (created 2026-07-08, 2 days open, P2, needs-repro). Could be an environmental issue, but impacts users relying on Nous portal.

### Test Infrastructure Concerns
- **[Issue #61673](https://github.com/NousResearch/hermes-agent/issues/61673)** — Cron tests write to user's live `~/.hermes/cron/jobs.json` (created 2026-07-09, 1 day open, P2). This is a production-data safety bug that could create real recurring agent turns on developer machines.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

# PicoClaw Project Digest — 2026-07-10

## Today's Overview
Activity has **moderately increased** in the last 24 hours, with **16 PRs updated** (4 merged/closed) and **3 open issues** gaining traction. The project shows healthy maintenance momentum with five dependency bumps in flight, a significant DeltaChat refactor (-320 LOC), and a concretely motivated ARMv7 build target PR from a real Raspberry Pi user. No new releases have been cut, and several long-running PRs remain open, indicating the core team may be consolidating changes for a future v0.3.0.

## Releases
**No new releases** in the last 24 hours. The latest available version remains **v0.2.9** (git 2992…). Users installing fresh will still encounter the v2→v3 config migration bug (#3206, see Bugs section).

## Project Progress
Four PRs were **merged or closed** today:

- **#3226** (CLOSED) — `fix(tools): stop write_file from coaching destructive overwrite (#3150)` by ACMYuechen. An important safety fix: the tool no longer nudges the agent to overwrite existing files, reducing risk of accidental data loss.
- **#3171** (CLOSED) — `fix(line): add ok checks for sync.Map type assertions in Send` by chengzhichao-xydt. Prevents potential panics in the LINE channel by properly checking type-assertion success.
- **#3213** (CLOSED) — `build(deps): bump github.com/aws/aws-sdk-go-v2/config` (dependabot). Routine AWS SDK update.
- **#3207** (CLOSED) — `build(deps): bump github.com/github/copilot-sdk/go from 0.2.0 to 1.0.5` (dependabot). A notable jump from pre-release to stable v1.0.5.

Open PRs that advanced today include the **DeltaChat refactor** (#3222, -320 LOC), the **remote Pico WebSocket agent mode** (#3118), and continued work on **Bedrock prompt caching** (#3163).

## Community Hot Topics
No single issue or PR has drawn significant reactions or lengthy discussion. Comments remain sparse (1–2 per item). The most notable conversations cluster around:

- **#3201** — `[Feature] Support streaming output for QQ channel` (2 comments). User YsLtr highlights that Telegram and Pico WebSocket already implement `StreamingCapable` but QQ is missing this. The underlying need is **consistent real-time UX across all chat platforms**.
- **#3203** — `[BUG] Matrix sync loop has no reconnection logic` (1 comment). User weissfl reports that Matrix `/sync` silently dies after network/server disruption, with no automatic reconnection.
- **#3206** — `v2→v3 config migration fails with false 'unknown field(s)'` (1 comment). A fresh-install blocker.

**Analysis:** The low comment volume on recently filed issues suggests either (a) users are resolving problems via Discord or direct channels, or (b) the project’s review bandwidth is constrained. The QQ streaming request (#3201) and Matrix reconnection bug (#3203) are the most likely to attract additional community input given they affect daily usability.

## Bugs & Stability
Three active bugs of **moderate to high severity**:

| Severity | Issue | Description | Fix PR Exists? |
|----------|-------|-------------|----------------|
| **High** | #3206 | v2→v3 config migration fails with `unknown field(s): build_info, session.dm_scope`. Blocks fresh installs from running `picoclaw status`. | **No** — no fix PR linked. |
| **High** | #3203 | Matrix `/sync` long-poll dies after network disruption with no reconnection. Process stays alive, so systemd `Restart=on-failure` does **not** trigger. Users must manually restart. | **No** — no fix PR linked. |
| **Medium** | #3180 (PR) | CLI tool calls with invalid JSON in `function.arguments` crash the agent. A fix PR is open but not yet merged. | **Yes** — PR #3180 by Alix-007 is open. |

Additionally, the `write_file` overwrite coaching bug (#3226) was **fixed and merged** today, removing a behavioral safety issue.

## Feature Requests & Roadmap Signals
Three notable feature signals appeared in updated PRs:

1. **QQ Channel Streaming (#3201)** — User request to add `StreamingCapable` to QQ. *Likelihood for next release: High.* The pattern is well-established in Telegram and WebSocket channels; implementing this is incremental.
2. **AWS Bedrock Prompt Caching (#3163)** — PR by loafoe adds explicit cache points for the Converse API, promising cost savings (~0.1× input read). *Likelihood for next release: Medium-High.* The PR has been open since June 23 and is technically mature.
3. **Remote Pico WebSocket Agent Mode (#3118)** — PR by jp39 adds `picoclaw agent --remote ws://...` mode. *Likelihood for next release: Medium.* The PR has been open for nearly a month, suggesting either complexity or prioritization lag.

**Prediction:** The next release (v0.3.0?) will likely bundle at least the **streaming QQ support**, the **Bedrock caching feature**, and the **ARMv7 build target** (#3205), plus the backlog of dependency bumps.

## User Feedback Summary
Real user pain points visible from the data:

- **Matrix reliability is a blocker** for users on unstable networks (#3203). The silent-death pattern is particularly frustrating because auto-restart mechanisms don’t trigger.
- **Fresh-install friction** persists with the v2→v3 migration bug (#3206), even on the latest release. This is a first-impression issue for newcomers.
- **Raspberry Pi users feel second-class** — one user (#3205) had to build a custom ARM target and fix 9router parsing. The ARMv7 PR directly addresses this.
- **Safety improvements are welcome** — the merged `write_file` fix (#3226) removes a footgun where the tool encouraged file overwrites, showing the community values defensive defaults.
- **Dependency hygiene is active** — five dependabot PRs in one day (AWS, Copilot SDK, golang.org/x/sync, pion/rtp) indicate the project prioritizes staying current, though the Azure baseline freeze PR (#3204) suggests supply-chain constraints.

Overall sentiment appears **neutral to slightly positive** — users are encountering real bugs but see fixes in progress. No PRs or issues express frustration with maintainer responsiveness.

## Backlog Watch
Several important items need maintainer attention:

| Item | Type | Age | Why It Matters |
|------|------|-----|----------------|
| **#3206** — v2→v3 config migration failure | Bug | 8 days | Blocks all fresh installs; no fix PR exists. **Highest priority.** |
| **#3203** — Matrix reconnection failure | Bug | 8 days | Silent death pattern degrades a core channel; no fix PR exists. |
| **#3180** — CLI tool-call invalid JSON crash | Bug (PR) | 14 days | Fix PR authored but unmerged; crashes affect CLI users. |
| **#3163** — Bedrock prompt caching | Feature (PR) | 17 days | Technically mature but idle; cost-saving feature users want. |
| **#3118** — Remote Pico WebSocket mode | Feature (PR) | 28 days | Longest-open feature PR; may need maintainer review/revision. |

**⚠️ Critical:** Issue #3206 and #3203 have **no linked fix PRs** despite being filed over a week ago. For a project at v0.2.9, a config migration bug on fresh install is a **hard blocker** for new adoption. Community trust may erode if these remain unaddressed.

---
*Generated from sip
eed/picoclaw GitHub data. All links: https://github.com/sipeed/picoclaw/issues/{id} / https://github.com/sipeed/picoclaw/pull/{id}.*

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

# NanoClaw Project Digest — 2026-07-10

## 1. Today's Overview

NanoClaw shows **high activity** today with 9 open issues and 17 pull requests updated in the last 24 hours, with 3 PRs merged/closed. No new releases were published. The project is in a **heavy development phase**, with multiple core-team PRs advancing the scheduled-tasks train (parts 3/5 and 2/5), a new guard/authorization seam, and a security fix for MCP server approval smuggling. Several Telegram adapter bugs were reported, revealing edge cases around channel wiring, bot membership, and `allowed_updates` persistence. The community is actively contributing fixes and security improvements, including an audit logging skill and ncl socket hardening PRs that remain open.

---

## 2. Releases

**No new releases** were published today. The project continues to accumulate changes toward an upcoming release—particularly the scheduled-tasks feature train, guard seam, and several bug fixes.

---

## 3. Project Progress

**Merged/Closed PRs today (3 total):**

- **[#2993]** — *Make NanoClaw resilient to a down container runtime* (shiranLupo) — **Closed**. Prevents `process.exit(1)` on failed `docker info` at boot; `main()` now degrades gracefully and recovers when Docker Desktop starts.
- **[#2621]** — *chore: add .gitattributes to enforce LF line endings for shell scripts* (GarethWright) — **Closed**. Ensures consistent line endings across platforms.
- **[#2981]** — *Scheduled tasks: ncl tasks control plane, isolated sessions, script gate* (omri-maya) — **Closed** (part 2/5 of the scheduled-tasks train). Ships the full `ncl tasks` resource with create/update/run/append-log, per-series isolated sessions, run history, and pre-task scripting gate.

**Key feature advancement:**
The **scheduled-tasks train** is moving fast: [#2988] (part 3/5, one-door delivery) is open, following two already-merged predecessors (#2980, #2981). This signals a major new subsystem nearing completion.

**Security & architecture:**
- **Guard seam** ([#2986]) — Every privileged action now passes one `guard()` decision function (allow/hold/deny). Architectural milestone for authorization.
- **Per-group harness capability toggles** ([#2983]) — Lean defaults for new groups, grandfathering existing configs.
- **Agent-runner tool allowlist fix** ([#2982]) — Removes five nonexistent tools from allowlist, adds drift guard.

---

## 4. Community Hot Topics

### Most Active Discussion Issues

- **#2989** — *Telegram: channels silently blackholed when bot token previously polled with narrower allowed_updates* (1 comment, allixsenos) — Identifies a Telegram API design pitfall: the server persists `allowed_updates` per token. The fix likely must always pass an explicit `allowed_updates` parameter.  
  [Link](nanocoai/nanoclaw Issue #2989)

- **#2985** — *opencode provider: silent no-reply when final text snapshot misses session.idle* (1 comment, fjnoyp) — Long agentic turns silently produce no reply. The agent completes its answer, but the `session.idle` event never fires, so the response is never delivered. This suggests a provider-specific timing/event delivery bug.  
  [Link](nanocoai/nanoclaw Issue #2985)

### Most Active Pull Requests

- **#2998** — *fix(self-mod): render full MCP server payload on the approval card* (glifocat) — Direct response to security advisory #2827/#2762: ensures `args` and `env` are visible on the approval card before an MCP server is added.  
  [Link](nanocoai/nanoclaw PR #2998)

- **#2987** — *feat: /add-audit skill — opt-in local audit log for the ncl surface* (moshe-nanoco) — SIEM-shaped, append-only NDJSON audit logs for every ncl dispatch outcome. Community demand for observability/security.  
  [Link](nanocoai/nanoclaw PR #2987)

**Underlying needs:** The community is demanding **visibility and control**: (1) audit logging for privileged operations, (2) full disclosure of MCP server configurations during approval, (3) reliable delivery guarantees, and (4) better Telegram integration for real-world use (channels, bot membership, rich rendering).

---

## 5. Bugs & Stability

### High Severity

- **[#2997]** — *hasIdenticalSend matches sends from previous fires, so recurring reminders with fixed text stop arriving* — **Severity: High**. A critical scheduling bug: recurring tasks with static reminder text deliver once, then silently stop. The dedup logic (`hasIdenticalSend`) incorrectly matches across different fires. No fix PR open yet.  
  [Link](nanocoai/nanoclaw Issue #2997)

- **[#2989]** — *Telegram: channels silently blackholed when bot token previously polled with narrower allowed_updates* — **Severity: High**. Messages to Telegram channels are silently dropped when the bot token has a stale `allowed_updates` persisted server-side. Unpredictable, hard to diagnose.  
  [Link](nanocoai/nanoclaw Issue #2989)

### Medium Severity

- **[#2995]** — *Outbound messages to an offline channel adapter are marked delivered without any send* — **Severity: Medium**. Messages "disappear" when the channel adapter isn't registered. A fix PR exists: [#2996] routes missing-adapter messages into the retry path.  
  [Link](nanocoai/nanoclaw Issue #2995) | [Fix PR](nanocoai/nanoclaw PR #2996)

- **[#2985]** — *opencode provider: silent no-reply when final text snapshot misses session.idle* — **Severity: Medium**. Agent completes work but user sees no reply. Blocks long agentic turn workflows.  
  [Link](nanocoai/nanoclaw Issue #2985)

- **[#2992]** — *Scheduled tasks are invisible and unmanageable across sessions of the same agent group* — **Severity: Medium**. Tasks are scoped per-session DB, making cross-group management impossible. Part of the scheduled-tasks feature area.  
  [Link](nanocoai/nanoclaw Issue #2992)

- **[#2991]** — *Telegram: channel wirings with sender_scope='known' never engage (channel posts are anonymous)* — **Severity: Medium**. `sender_scope='known'` is useless for broadcast channels because Telegram doesn't expose individual senders.  
  [Link](nanocoai/nanoclaw Issue #2991)

- **[#2990]** — *Telegram: bot does not react to being added to a chat (my_chat_member updates are discarded)* — **Severity: Medium**. Bots can't detect or react to being added to groups/channels.  
  [Link](nanocoai/nanoclaw Issue #2990)

### Security Vulnerabilities (High Severity)

- **[#2827]** / **[#2762]** — *add_mcp_server approval flow hides runtime args and env* — **Severity: Critical (Security)**. Approval cards show only the server name, allowing attackers to smuggle malicious `args` or `env`. Fix PR [#2998] renders the full payload on the approval card. These remain open—presumably pending review or merge.  
  [Issue #2827](nanocoai/nanoclaw Issue #2827) | [Issue #2762](nanocoai/nanoclaw Issue #2762) | [Fix PR #2998](nanocoai/nanoclaw PR #2998)

---

## 6. Feature Requests & Roadmap Signals

### Likely in Next Version

- **Scheduled tasks subsystem** — The 5-part train (parts 2/5 and 3/5 open/merged today) is a strong signal that proper cron/task management (create, update, cancel, pause, resume, per-series sessions, one-door delivery) will land in the next release.
- **Guard seam / authorization framework** — PR #2986 introduces a unified `guard()` decision function for all privileged actions. This is foundational for future access control features.
- **MCP server approval transparency** — PR #2998 fixes the security blind spot where `args` and `env` were hidden during approval.
- **Per-group capability toggles** — PR #2983 allows fine-grained control over which harness features are enabled per messaging group.

### Community Requested (Near-Term)

- **Audit logging** — PR #2987 (add-audit skill) responds to demand for SIEM-compatible audit trails. Likely to merge.
- **Telegram rich rendering** — PR #2877 (Bot API 10.1 `sendRichMessage`) adds native rich message support for Telegram. Still open, but aligns with community needs.
- **Multimodal (v1 feature restoration)** — PR #2618 restores image/voice/PDF attachments and reaction support. Long-running PR (since May) but active.

### Future Considerations

- **Cross-session task management** — Issue #2992 will require architectural changes to make `list_tasks`/`update_task` etc. work across all sessions in an agent group.
- **Telegram my_chat_member handling** — Issue #2990 hints at a need for bot lifecycle event handling beyond basic message dispatch.

---

## 7. User Feedback Summary

### Pain Points (Expressed)

| Pain Point | Source | Likelihood of Fix in Next Release |
|---|---|---|
| **Silent delivery failures** — Messages that appear sent but never arrive (Telegram blackhole, offline adapters, opencode provider) | #2989, #2995, #2985 | High (fix PRs exist for #2995/2996; #2989 and #2985 still need investigation) |
| **Recurring reminders stop after first fire** — Static-text reminders are deduped incorrectly, causing silent cancellation | #2997 | Medium (bug not yet assigned or fixed) |
| **Scheduled tasks invisible across sessions** — Can't manage tasks created by one session from another | #2992 | Medium (scheduled-tasks train may address this in later parts) |
| **Security: MCP server args/env hidden during approval** — Critical security blind spot | #2827, #2762 | High (fix PR #2998 submitted, pending merge) |
| **Telegram: bot can't detect being added to groups** — No `my_chat_member` handling | #2990 | Low (not yet addressed) |
| **Telegram: sender_scope='known' never works for channels** — Channel posts are anonymous | #2991 | Medium (likely needs doc fix or scope remapping) |

### Use Cases Supported
- Multi-platform messaging bots (Telegram, Discord, opencode)
- Scheduled/recurring task automation
- Self-modifying agent workflows (MCP tools)
- Secure approval workflows
- Agent delegation with reporting (PR #2994 — Feishu/飞书 notification)

### Satisfaction Signals
- High core-team participation in scheduled tasks, guard seam, and audit features suggests the project is maturing its architecture.
- Rapid PR merging (3 closed today) shows active maintenance response.
- Community contributions from multiple authors (glifocat, allixsenos, fjnoyp, shiranLupo) indicate healthy open-source engagement.

---

## 8. Backlog Watch

### Issues Needing Maintainer Attention

| Issue | Age | Status | Why It Matters |
|---|---|---|---|
| **#2827 / #2762** — MCP server approval smuggling (security) | 19–26 days | Open, no assignee despite fix PR #2998 | Security vulnerability in critical approval flow. Fix PR exists but hasn't been merged. High urgency. |
| **#2618** — Restore multimodal (image/voice/PDF) & reactions | 46 days | Open, no recent activity | Restores v1 capabilities; stalled since May. Community blocker for users migrating from v1. |
| **#1598** — Add-remote-storage skill (WebDAV/S3 via rclone) | 99 days | Open, old | Large feature PR (skill + ncl configuration commands). Stalled for over 3 months. |
| **#2544** — Telegram enable message_reaction + callback_query | 53 days | Open, no activity | Small enhancement that would improve Telegram user experience. |

### PRs That Need Review/Merge

| PR | Age | Status | Notes |
|---|---|---|---|
| **#2998** — Fix MCP server approval card transparency | 1 day | Open | Urgent security fix. Should be prioritized. |
| **#2987** — Add-audit skill | 1 day | Open | New skill for observability. Needs testing + merge. |
| **#2802** — ncl socket hardening (timeout, buffer caps) | 23 days | Open | Important for preventing resource exhaustion. |
| **#2226** — Throw on missing channel adapter (older approach) | 69 days | Open | May be superseded by #2996 (newer, authored by core-team member). Should be closed if obsolete. |

### Watch Item
The **scheduled-tasks feature train** (parts 4/5 and 5/5) has not yet appeared as PRs. If they stall, the partial implementation (parts 1–3 merged/open) could leave the system in an incomplete state. Watch for the remaining parts in the coming days.

---

*Generated on 2026-07-10 from NanoClaw GitHub data. All links are relative to nanocoai/nanoclaw.*

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

Here is the IronClaw project digest for 2026-07-10, generated from the provided GitHub data.

---

## IronClaw Project Digest — 2026-07-10

### 1. Today's Overview
The project is experiencing a high-volume day, dominated by a major bug-bash push. 32 issues were updated, with 11 new critical "bug_bash_P2" and 1 bug_bash_P1 issue filed today alone, signaling a targeted effort to surface and document stability problems. While 28 PRs were merged or closed, the bulk of contributions are focused on refactoring (e.g., builder patterns, error handling) and fixing Slack integration and automation bugs. The project is healthy in terms of development velocity, but is clearly in a "stabilization and polish" cycle, with a strong emphasis on rooting out regressions and UX failures.

### 2. Releases
No new releases were published in the last 24 hours. A pending release PR (#5598) is open and has been for several days, which would introduce breaking API changes to `ironclaw_common` (v0.4.2 -> v0.5.0) and `ironclaw_skills` (v0.3.0 -> v0.4.0). This release is likely being held to allow for the current bug-fix wave to land first.

### 3. Project Progress
In the last 24 hours, 28 pull requests were merged or closed, reflecting significant internal cleanup and foundational improvements. Key advances include:
- **Error Handling**: The project hardened its error surface by merging a workspace-wide deny on `unused_must_use` (#5652, #5662), ensuring that dropped `Result` values no longer compile. This prevents silent failure swallowing across 90+ sites.
- **Code Health (Default Builders)**: A large stack of PRs (#5791, #5793, #5794, #5798, #5799, #5800, #5811, #5812) was merged to establish a consistent `::default().set_*()` pattern for configuration structs across the Reborn stack, reducing boilerplate and making test setup clearer.
- **Legacy Code Removal**: Legacy v1 coverage test binaries and their orphaned trace fixtures were removed (#5826, #5827), reducing maintenance burden and CI cost.
- **Tool Overhaul**: A significant open PR (#5904) for a Slack tool overhaul is under active review, including identity fixes, structured errors, and pagination.

### 4. Community Hot Topics
The most active discussions are centered on critical Slack integration and notification failures, indicating high user impact.

- **[Near-Miss Bug] Approval Notifications Disappear (#5553)**: With 4 comments, this issue describes a critical UX failure where approval requests flash and then vanish from the notification history. This is a top-priority concern as it can cause automation workflows to deadlock.
- **[Design Gap] No Way to Unpair Slack on Host-Beta Mount (#5747)**: With 3 comments, this issue highlights a fundamental usability gap in the Slack integration. Once paired, a user cannot disconnect, leaving them locked into a service.
- **[UX/Hang] Activity Panel Hides Details / Fails to Update During Run (#5701)**: With 3 comments, this reports that the activity panel collapses tool details and is not real-time, making it impossible to monitor an active run. This is a significant blow to user confidence in the system's feedback loop.

### 5. Bugs & Stability
A large wave of bug-bash issues was filed today (2026-07-09), mostly at "P2" severity. The root cause analysis suggests a systemic Slack integration problem.

- **P1 - Critical**:
    - **Wrong Recipient**: A Slack notification was delivered to an unrelated user (#5877). This is a data privacy and security-critical bug. *No explicit fix PR exists yet, but PR #5898 directly addresses "per-trigger delivery targets" to fix wrong-channel delivery.*
- **P2 - High**:
    - **Approval Flow Broken**: The approval notification opens an action but hides the actual approve/deny card (#5885). This makes the system completely unresponsive to user input.
    - **Slack Auth State Corruption**: Repeated Slack reconnects leave the auth flow in a permanent "Waiting for Slack..." state (#5882). The Web UI fails to recognize auth completed via Slack (#5880).
    - **Routine State Corruption**:
        - Pending approval blocks *all* subsequent scheduled runs (#5886).
        - Routines lose credentials after an external token is revoked, requiring re-setup (#5884).
        - A systemic "No thread attached" error causes a routine to fail every 5 minutes (#5836).
    - **Data Loss / Model Errors**: Runs that hit the action limit discard all progress (#5887). Successful tool execution is followed by a generic "model output could not be used" error (#5883).
- **P3 - Low**:
    - Several UI bugs were filed, including a non-functional "Load older messages" button (#5889) and an inability to delete old threads (#5888).

### 6. Feature Requests & Roadmap Signals
- **CLI/TUI for Managing Secrets (#2601)**: Despite being opened in April, this issue was updated yesterday, suggesting renewed interest or progress. As the project adds more integrations (Slack, GitHub), managing authentication tokens becomes a core pain point. This is a strong candidate for a future release.
- **Agent Tool Ecosystem**: A new contributor submitted a PR (#5903) to add 25 paid endpoints from the "JMT x402 Agent Tools" service. This signals the platform is attracting third-party tool developers, which is a key health indicator for its ecosystem growth.
- **Tech Debt Cleanup**: A new issue (#5897) proposes decomposing the first-party skill activation module, indicating a move toward better modularity and testability.

### 7. User Feedback Summary
The user feedback implicitly captured in today's issues reveals deep dissatisfaction with the system's reliability and predictability concerning external integrations and automations. Key pain points include:

- **"I don't trust the system"**: Users are experiencing a "two-state" problem where a run appears successful (tool execution finishes) but then fails with a cryptic model error, or where error banners persist after success. This erodes trust in the results.
- **"Slack is a mess"**: The feedback coalesces around one core problem: IronClaw's Slack integration is unreliable. Messages go to the wrong user or channel, authentication is unstable, and disconnection is impossible. This is a critical integration to fix.
- **"I can't monitor or control my work"**: The non-functional activity panel, disappearing approval notifications, and inability to delete threads all point to a UI that feels static and unresponsive, making users feel they have no control over the agent's actions.

### 8. Backlog Watch
- **#2601 - Feature: CLI/TUI for Managing Secrets**: Opened April 18, this issue requests a critical piece of infrastructure for managing authentication tokens, which is directly related to many of today's credential-related bugs. It remains open with minimal engagement despite being a high-value usability win.
- **#5499 - WASM Tool Install from Zip**: This large, low-risk PR for the Reborn stack has been open since July 1. It is a foundational piece (Part 1) for enabling configurable tools and appears to be blocked on review or further dependencies. Its progress should be watched as it enables third-party tool installation.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

Here is the project digest for **LobsterAI** (github.com/netease-youdao/LobsterAI) for **2026-07-10**.

---

## LobsterAI Project Digest – 2026-07-10

### 1. Today's Overview
LobsterAI saw high-velocity development activity today, with **14 PRs updated** in the last 24 hours—11 of which were merged or closed. The team focused heavily on the **Cowork** and **OpenClaw** subsystems, addressing attachment handling, prompt sanitization, agent display names, and sub-tool history syncing. Community-submitted feature PRs remained open but stale, with no new releases cut. The project appears to be in a **stable, iterative polish phase** with a strong emphasis on fixing regressions and improving UX consistency across the renderer and main process boundaries.

### 2. Releases
**None.** No new releases were published in the last 24 hours. The latest stable release remains unchanged.

### 3. Project Progress
11 PRs were merged or closed today, indicating significant engineering throughput. Key advancements include:

- **Cowork & Prompt UX:** PR #2307 refines prompt modes (removed Plan Mode switch, moved Goal/Steer status bars, fixed queued Steer follow-up handling). PR #2300 enables file attachments (dragged, pasted, text selections) in the Steer queue.
- **Subagent & Tool Fixes:** PR #2299 fixes syncing of subagent child tool call/results history, and PR #2305 ensures agent display names propagate correctly to OpenClaw agent entries and artifact panels.
- **Sidebar & Task Management:** PR #2304 improves sidebar task pagination with incremental loading, expand/collapse controls, and drag-sort ordering for agents.
- **Windows-Specific UX:** PR #2302 adds a branded Windows title bar with native window controls, moving collapsed-sidebar actions into the bar.
- **Memory & Cron:** PR #2301 explicitly disables memory dreaming (cron management) when LobsterAI dreaming is off.
- **Data Cleanup:** PR #2308 sanitizes null bytes (U+0000) from prompts before sending to the OpenClaw gateway, preventing hard rejects.
- **Uninstaller Enhancement:** PR #1396 improves the Windows NSIS uninstaller to fully clean AppData and handle running applications gracefully.
- **Localization:** PR #1397 localizes compact time suffixes (e.g., "now", "26m") in the session list to support Chinese and other languages.

### 4. Community Hot Topics
The community’s most active issues remain **stale feature requests from April 2026**, each with consistent discussion but no recent maintainer engagement:

- **#1339 – Missing message timestamps** – 1 comment, asking for HH:MM display on user messages.
- **#1341 – No up/down arrow history in input** – 1 comment, wanting terminal-like history navigation.
- **#1343 – Search only searches titles, not message content** – 1 comment, requesting full-text search.
- **#1345 – No export to Markdown** – 1 comment, requesting text-based export of Cowork sessions.

These issues reveal a **strong user demand for better session navigation and data portability**. Notably, PR #1340 (timestamp) and PR #1342 (history navigation) were submitted by the same author and remain open, awaiting merge.

- **#1339** – [Link](https://github.com/netease-youdao/LobsterAI/issues/1339)
- **#1341** – [Link](https://github.com/netease-youdao/LobsterAI/issues/1341)
- **#1343** – [Link](https://github.com/netease-youdao/LobsterAI/issues/1343)
- **#1345** – [Link](https://github.com/netease-youdao/LobsterAI/issues/1345)

### 5. Bugs & Stability
Today’s bug fixes were **medium-to-low severity**, with no crashes or regressions reported:

| Severity | Issue/PR | Description | Status |
|----------|----------|-------------|--------|
| **Medium** | PR #2308 | Null bytes (U+0000) in prompts cause hard reject from OpenClaw gateway; fix sanitizes at ingestion and outbound boundaries. | Merged |
| **Medium** | PR #2299 | Subagent child sessions missing tool call/results history; fix extracts and syncs gateway history. | Merged |
| **Low** | PR #2301 | Dreaming cron jobs not cleaned up when memory dreaming disabled; fix explicitly disables in OpenClaw config. | Merged |
| **Low** | Issue #1394 | Non-repeating scheduled tasks auto-deleted after execution; user expects editable task to persist. | Closed (stale) |

### 6. Feature Requests & Roadmap Signals
Several community requests show a **clear roadmap signal** for the Cowork UI:

- **Message timestamps** (PR #1340) – Likely to be merged soon, as it is a small, well-contained change.
- **Input history navigation** (PR #1342) – A mature PR matching the terminal-like UX request; likely candidate for next minor release.
- **Full-text search** (Issue #1343) – No PR exists; this is a larger feature requiring async message loading and caching, possibly targeted for v2.x.
- **Export to Markdown** (Issue #1345) – No PR exists but reuse of existing IPC interfaces makes it feasible for a near-term patch.

These features align with the project’s visible trajectory toward **power-user workflows, data portability, and session management**.

### 7. User Feedback Summary
User feedback is **highly constructive and focused on usability gaps**:

- **Pain point:** Users cannot see message send times in chat, making it hard to understand conversation pacing (Issue #1339).
- **Pain point:** No way to quickly reuse or edit previously sent messages via keyboard input history (Issue #1341).
- **Pain point:** Search is limited to session titles, making it impossible to find sessions by remembered keywords (Issue #1343).
- **Pain point:** Exporting sessions only supports image-based export; users need text/Markdown for editing and note-taking (Issue #1345).
- **Bug frustration:** Non-repeating scheduled tasks are deleted after execution, preventing reuse/editing (Issue #1394, now closed as stale).

Overall, users are **satisfied with the core Cowork and agent features** but find **session and message management underdeveloped**.

### 8. Backlog Watch
The following important, user-submitted PRs have been **stale for over 3 months** and need maintainer attention:

- **PR #1340 – Message timestamps** – [Link](https://github.com/netease-youdao/LobsterAI/pull/1340) – Open, no recent activity. Closes highly demanded Issue #1339.
- **PR #1342 – Input history navigation** – [Link](https://github.com/netease-youdao/LobsterAI/pull/1342) – Open, no recent activity. Closes highly demanded Issue #1341.
- **PR #1396 – Uninstaller enhancement** – [Link](https://github.com/netease-youdao/LobsterAI/pull/1396) – Marked closed/stale, but contains valuable Windows cleanup logic that is still relevant.
- **PR #1397 – Localized time suffixes** – [Link](https://github.com/netease-youdao/LobsterAI/pull/1397) – Marked closed/stale, but represents an i18n improvement that may need rebasing.

Additionally, **Issue #1343 (full-text search)** and **Issue #1345 (export to Markdown)** remain open with no associated PRs. These are high-value features that, if implemented, would significantly improve user experience.

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyagi">TinyAGI/tinyagi</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

# Moltis Project Digest — 2026-07-10

## Today's Overview
Moltis had a quiet day with no new issues or releases. The only activity was the opening of one pull request, **#1146**, which proposes adding support for GPT-5.6 model variants. No issues were updated, closed, or created in the last 24 hours. Overall project activity is low, but the single PR signals forward-looking work on model support expansion.

## Releases
No new releases were published today. The latest available release remains unchanged.

## Project Progress
No pull requests were merged or closed today. The only new PR, **#1146**, is still open and under review. No features advanced to a completed state in this period.

## Community Hot Topics
The sole active PR is the most notable community item:

- **[#1146 — Add GPT-5.6 model support](https://github.com/moltis-org/moltis/pull/1146)** (open, created 2026-07-09, updated 2026-07-09, 0 comments, 0 reactions)  
  *Author: PeterDaveHello*  
  This PR adds support for GPT-5.6 Sol, Terra, and Luna models to OpenAI and OpenAI Codex fallback catalogs. It also documents the 1.05M context window and 372K limit for ChatGPT/Codex backend, including the `gpt-5.6` Sol alias, and updates configuration templates. The lack of comments or reactions suggests initial review is still pending. The underlying need is clear: users want access to the latest frontier models with their extended context capabilities.

## Bugs & Stability
No bugs, crashes, or regressions were reported today. Code stability appears stable with no new issue filings.

## Feature Requests & Roadmap Signals
**PR #1146** is the only feature signal today, directly requesting GPT-5.6 model support. This is a natural progression given the model's recent release. It is reasonable to predict that GPT-5.6 support (Sol, Terra, Luna) will be included in the next Moltis release, as it is a straightforward catalog extension without architectural changes.

## User Feedback Summary
No user feedback, pain points, or use-case discussions were recorded in issues or PRs today. The project received no new comments or reactions, making it difficult to gauge user satisfaction from this data window.

## Backlog Watch
No long-unanswered issues or PRs were identified. The project backlog appears clean with no unresolved items requiring maintainer attention.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

# CoPaw Project Digest — 2026-07-10

## Today's Overview

CoPaw shows high activity with 35 issues updated and 50 pull requests touched in the last 24 hours, reflecting sustained community and maintainer engagement. The project shipped **v2.0.0-beta.5**, a minor beta release with scroll-related fixes for the eviction index and seam banner logic. 15 issues were closed alongside 32 merged/closed PRs, indicating a strong pace of bug fixing and feature integration. The community remains highly vocal, with the top discussion thread (#2291) accumulating 64 comments and serving as a structured onboarding hub for new contributors. Overall project health appears robust, though several user-facing regressions in the new 2.0 beta series require attention.

## Releases

**v2.0.0-beta.5** (released 2026-07-09)
- **Changes:**
  - Fix(scroll): label un-headlined evicted spans in the eviction index (@niceIrene, PR #5848)
  - Fix(scroll): anchor the live turn with a seam banner in the eviction index (@niceIrene, PR #58)

This is a small patch release addressing visual/documentation issues in the scroll (context compaction) component. No breaking changes or migration notes are documented.

## Project Progress

**32 merged/closed PRs today** cover a wide range of fixes and improvements:

- **Memory & Reasoning:**
  - `fix(agents): reduce reasoning alignment log spam` (PR #5908) — addresses log-level misuse in `model_factory.py` that caused WARNING-level spam on every assistant block (fixes #5771)
  - `fix(model): default preserve_thinking to false` (PR #5870) — flips the default to prevent reasoning reflux loops where prior-turn chain-of-thought content caused repetitive outputs
  - `feat(memory): add reranker for search results on reme0.4` (PR #5692, under review) — adds post-retrieval reranking stage to improve memory search quality

- **Tool Calls & MCP:**
  - `fix(agents): surface malformed tool-call input to model` (PR #5761) — ensures malformed `tool_call.input` is visible to the model instead of silently dropped
  - `fix(mcp): apply runtime approval level to driver policy` (PR #5864) — sends effective Console approval level in chat requests so MCP driver policy aligns with UI
  - `fix(driver): honor off approval level for driver policy` (PR #5853, first-time contributor) — stops approval popups when approval level is OFF
  - `chore: fix mcp version` (PR #5904)

- **Channels & Notifications:**
  - `fix(channels): surface DingTalk delivery failures` (PR #5654) — fixes #5566 by skipping empty outgoing text and surfacing failures only for explicit senders
  - `fix(channels): Matrix Channel token login` (PR #5868) — resolves `M_MISSING_TOKEN` error from mixed auth methods
  - Business WeChat QR code fix (Issue #5893, self-reported by user with solution)

- **Security:**
  - `fix(security): split rm detection/extraction to prevent ${HOME} bypass` (PR #5866) — critical fix for #5090 where `rm -rf ${HOME}` was not flagged as dangerous due to variable substitution order

- **Frontend & TUI:**
  - `fix(tui): improve approvals and warmup sessions` (PR #5892)
  - `fix(runtime): use structured Error object in error envelope` (PR #5905) — fixes frontend SDK compatibility after runtime v2 refactor

- **Testing:**
  - `test(integration): Sprint 4.1 — cover /api/tool-calls/* + /api/console/chat/task` (PR #5895) — 21 integration test cases
  - `test(unit): channels module unit tests` (PR #5812) — 176 unit test cases
  - `test(unit): runtime/security/install regression tests` (PR #5813) — 43 targeted unit tests

- **Documentation:**
  - `update(docs): update docs for qwenpaw 2.0` (PR #5899)

## Community Hot Topics

| Issue/PR | Comments | Topic |
|----------|----------|-------|
| [#2291 [OPEN]](https://github.com/agentscope-ai/QwenPaw/issues/2291) — Help Wanted: Open Tasks | **64** | Contributor onboarding hub with structured P0–P2 task list |
| [#5757 [OPEN]](https://github.com/agentscope-ai/QwenPaw/issues/5757) — Feishu not responding | **13** | Critical channel bug: first message replies, subsequent messages silently dropped on both Docker and Platform instances |
| [#5379 [CLOSED]](https://github.com/agentscope-ai/QwenPaw/issues/5379) — Python install → Internal Server Error | **10** | Startup crash related to `get_remote_addr(transport)` |
| [#5879 [OPEN]](https://github.com/agentscope-ai/QwenPaw/issues/5879) — Request: disable sandbox toggle | **6** | User wants ability to disable sandbox in trusted environments to allow `pip install` and agent capabilities |
| [#5479 [CLOSED]](https://github.com/agentscope-ai/QwenPaw/issues/5479) — Large session file crash (>500KB) | **6** | Frontend crashes when opening sessions >500KB — expects progressive loading |
| [#5797 [OPEN]](https://github.com/agentscope-ai/QwenPaw/issues/5797) — Cron notification toggle | **6** | Users want per-task control over popup notifications instead of blanket on/off |
| [#5328 [CLOSED]](https://github.com/agentscope-ai/QwenPaw/issues/5328) — DeepSeek agent hangs during thinking | **5** | Agent gets stuck mid-thinking across all platforms |

**Analysis:** The Help Wanted thread (#2291) serves as the project's primary community onboarding mechanism, with maintainer @cuiyuebing actively triaging. The highest-signal user issues center on **channel reliability** (Feishu, DingTalk) and **sandbox limitations** in v2.0 — both critical for production deployment. The sandbox disable request (#5879) is gaining rapid traction with 6 comments in its first day.

## Bugs & Stability

**High Severity (active, with fix PRs noted):**

1. **[#5906 [OPEN]](https://github.com/agentscope-ai/QwenPaw/issues/5906)** — Duplicate prevention false alarm: triggers "Doom loop" error on non-duplicate conversations. **Severity: High.** Affects v2.0.0b4. No fix PR yet.
2. **[#5896 [OPEN]](https://github.com/agentscope-ai/QwenPaw/issues/5896)** — Iteration limit miscount: counts from last trigger, not new message, reaching 100 prematurely. **Severity: High.** Affects v2.0.0b4. No fix PR yet.
3. **[#5856 [OPEN]](https://github.com/agentscope-ai/QwenPaw/issues/5856)** — Context compaction drops `tool_call` structure entirely, causing 400 errors and message count mismatch. **Severity: High.** Related PR #5841 (whitespace fix) merged, but structural loss not addressed.
4. **[#5872 [OPEN]](https://github.com/agentscope-ai/QwenPaw/issues/5872)** — Docker: `browser_use` fails due to dbus connection error causing Chromium exit. **Severity: High.** No fix PR yet.
5. **[#5910 [OPEN]](https://github.com/agentscope-ai/QwenPaw/issues/5910)** — Auto Memory Search generates malformed `function_call` history for OpenAI Responses API, causing 502 errors. **Severity: High.** New, no fix PR yet.

**Medium Severity:**

6. **[#5911 [OPEN]](https://github.com/agentscope-ai/QwenPaw/issues/5911)** — Windows AppContainer sandbox ignores configured shell (always uses cmd.exe). **Severity: Medium.**
7. **[#5900 [OPEN]](https://github.com/agentscope-ai/QwenPaw/issues/5900)** — MCP `streamable_http` session terminated: no auto-reconnect, client permanently skipped. **Severity: Medium.**
8. **[#5887 [OPEN]](https://github.com/agentscope-ai/QwenPaw/issues/5887)** — Command-triggered ReMe auto-memory runs without `session_id` after `/new` in QQ. **Severity: Medium.**
9. **[#5771 [OPEN]](https://github.com/agentscope-ai/QwenPaw/issues/5771)** — `model_factory.py` debug logs at WARNING level causing log spam. **Severity: Low.** Fix PR #5908 submitted.
10. **[#5859 [OPEN]](https://github.com/agentscope-ai/QwenPaw/issues/5859)** — DeepSeek model call fails during auto_memory_search due to missing `reasoning_content` field. **Severity: Medium.**

**Recently Fixed (today):**
- [#5379](https://github.com/agentscope-ai/QwenPaw/issues/5379) — `Internal Server Error` on startup (CLOSED)
- [#5328](https://github.com/agentscope-ai/QwenPaw/issues/5328) — DeepSeek thinking hang (CLOSED)
- [#5863](https://github.com/agentscope-ai/QwenPaw/issues/5863) — Image not displaying in Coding Session (CLOSED)
- [#5841](https://github.com/agentscope-ai/QwenPaw/issues/5841) — Whitespace-prefixed tool-call JSON (MERGED)
- [#5866](https://github.com/agentscope-ai/QwenPaw/issues/5866) — `${HOME}` bypass in rm detection (MERGED)
- [#5898](https://github.com/agentscope-ai/QwenPaw/issues/5898) — OneBot channel watchdog restart loop (CLOSED)

## Feature Requests & Roadmap Signals

**Top user-requested features this period:**

1. **[#5879](https://github.com/agentscope-ai/QwenPaw/issues/5879)** — **Disable sandbox toggle** (6 comments, first day): Users running v2.0 in trusted environments want to bypass sandbox restrictions that prevent `pip install` and full agent capability. **Likelihood for next release: High** — strong user demand, relatively simple UI toggle.

2. **[#5797](https://github.com/agentscope-ai/QwenPaw/issues/5797)** — **Per-task cron notification toggle** (6 comments): Users want per-scheduled-task control over popup notifications (not blanket on/off). **Likelihood for next release: Medium** — discussed as response to PR #4803 which disabled all popups.

3. **[#5903](https://github.com/agentscope-ai/QwenPaw/issues/5903)** — **Session grouping + import/export** (1 comment): Organizational feature for managing multiple sessions per agent. **Likelihood: Low-Medium** — nice-to-have UX improvement.

4. **[#5909](https://github.com/agentscope-ai/QwenPaw/issues/5909)** — **Configurable theme/skin module** (1 comment, linked to #2291): Design proposal from a new contributor claiming Task 1 of the Help Wanted list. **Likelihood: Medium** — explicitly scheduled as P0 in #2291.

5. **[#5711 CLOSED](https://github.com/agentscope-ai/QwenPaw/issues/5711)** — **QwenPaw capability gap analysis**: Comprehensive feature request post outlining weaknesses in tool call efficiency, memory mechanism, rule enforcement, and context preservation, with competitor benchmarking. Closed but likely informs ongoing development.

**Prediction for v2.0.0-rc1:** Sandbox toggle, theme/skin module (first Task #1 deliverable), and continued MCP/channel stability improvements.

## User Feedback Summary

**Satisfaction indicators:**
- Multiple first-time contributors submitting fixes (PRs #5853, #5739), indicating good onboarding experience
- Active use of Help Wanted board (#2291) with 64 comments — community is engaged and self-organizing
- Users like @MCQSJ filing multiple detailed bugs on v2.0.0b4 shows active beta testing community

**Key pain points (direct quotes/summaries):**
1. **Sandbox too restrictive:** *"2.0版本在可信任，自使用的设备上面，沙盒严重限制了agent的能力，且无法关闭，连让agent安装python的库都无法正常完成了"* — User in trusted environments feels sandbox is crippling (#5879)
2. **Context compaction breaks tool calls:** *"The structured tool_call data is permanently lost. The model never sees its own tool calls, so it cannot continue the conversation correctly."* — Critical regression that breaks agent autonomy (#5856)
3. **Docker browser_use unusable:** User reports Chromium exits immediately due to dbus error in container (#5872)
4. **Feishu channel unreliable:** *"机器人显示了收到，但是没有任何回复"* — Bot shows "received" but produces no response after first message (#5757)
5. **Cron notifications too binary:** *"千问不要因噎废食，有人反对，就都关掉了"* — User criticizes the all-or-nothing approach to notification popups (#5797)

**Feedback themes:** Users want **configurability over protectiveness** — both in sandbox and notifications — and are frustrated by the 2.0 beta's hard-coded defaults that trade capability for safety.

## Backlog Watch

**Issues requiring maintainer attention:**

| Issue | Age | Reason for Watch |
|-------|-----|------------------|
| [#2291 [OPEN]](https://github.com/agentscope-ai/QwenPaw/issues/2291) — Help Wanted | ~107 days | High-traffic meta-issue; new task claims (#5909) need prompt review |
| [#5856 [OPEN]](https://github.com/agentscope-ai/QwenPaw/issues/5856) — Context compaction drops tool_calls | 2 days | **Critical:** core agent functionality broken by compaction. No maintainer response yet despite detailed reproduction |
| [#5906 [OPEN]](https://github.com/agentscope-ai/QwenPaw/issues/5906) — Duplicate prevention false alarm | 1 day | **Critical:** blocks normal conversation in v2.0.0b4. Filed by experienced beta tester @MCQSJ |
| [#5896 [OPEN]](https://github.com/agentscope-ai/QwenPaw/issues/5896) — Iteration limit miscount | 1 day | **Critical:** also filed by @MCQSJ. Premature stop at 100 iterations |
| [#5910 [OPEN]](https://github.com/agentscope-ai/QwenPaw/issues/5910) — Auto Memory Search 502 error | <1 day | **Critical:** breaks OpenAI Responses API users entirely. Filed by @BLUE0818 |
| [#5911 [OPEN]](https://github.com/agentscope-ai/QwenPaw/issues/5911) — Windows sandbox ignores configured shell | <1 day | Filed by @BLUE0818 alongside #5910, same user hitting multiple 2.0 regressions |
| [#5900 [OPEN]](https://github.com/agentscope-ai/QwenPaw/issues/5900) — MCP no auto-reconnect | <1 day | Filed by @feng183043996; another Docker user with production-impacting MCP instability |
| [#287 unresolved?] | — | OneBot default-on (#5898, CLOSED today) and DingTalk user isolation (#5835, CLOSED) were addressed promptly — good responsiveness overall |

**PRs needing review:**
- [#5637 [OPEN]](https://github.com/agentscope-ai/QwenPaw/pull/5637) — Event-driven subagent lifecycle (10 days old, significant architectural change)
- [#5187 [OPEN]](https://github.com/agentscope-ai/QwenPaw/pull/5187) — Windows desktop GUI automation (26 days old, large feature)
- [#5692 [OPEN]](https://github.com/agentscope-ai/QwenPaw/pull/5692) — Memory search reranker (9 days old, under review)
- [#5739 [OPEN]](https://github.com/agentscope-ai/QwenPaw/pull/5739) — Text selection in chat cards (8 days old, first-time contributor, under review)

**Maintainer attention needed:** The cluster of critical v2.0.0 beta regressions (#5856, #5906, #5896, #5910, #5911) filed by experienced community members should be prioritized — these represent core functionality breakage that erodes trust in the beta series.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

# ZeroClaw Project Digest
**Date: 2026-07-10**

---

## Today's Overview

ZeroClaw is in an **intense development cycle** with 36 issues and 50 PRs updated in the last 24 hours, indicating a highly active maintainer team pushing toward multiple milestones. The project has 25 open/active issues and 39 open PRs, with significant work underway on v0.8.3 (observability, config-driven policy, CI) and v0.9.0 (auth, security, gateway hardening). No new releases were cut today, but the volume of merged PRs (11) suggests release candidates may be imminent. Critical security fixes for SSRF vulnerabilities across multiple tool surfaces and a long-standing MCP process leak are moving through review.

---

## Releases

**No new releases today.** The latest release remains at version 0.8.x (last release date unknown). Several tracker issues suggest v0.8.3 and v0.9.0 are in active development:

- [v0.8.3 observability, CI, docs, deps tracker](https://github.com/zeroclaw-labs/zeroclaw/issues/8073)
- [v0.8.3 config-driven runtime policy tracker](https://github.com/zeroclaw-labs/zeroclaw/issues/8363)
- [v0.9.0 auth/security/gateway tracker](https://github.com/zeroclaw-labs/zeroclaw/issues/7432)

---

## Project Progress

**11 PRs merged/closed today**, demonstrating steady forward momentum:

| PR | Title | Status |
|----|-------|--------|
| [#8881](https://github.com/zeroclaw-labs/zeroclaw/pull/8881) | fix(cron): expose wechat, signal, email in cron delivery schema | Merged |
| [#8875](https://github.com/zeroclaw-labs/zeroclaw/issues/8875) | bug(config): degraded-section warning can point to config migrate without showing parse error | Closed |
| [#8873](https://github.com/zeroclaw-labs/zeroclaw/pull/8873) | fix(cli): UTF-8-safe stdin cap in exit prompt + audit trail | Merged |
| [#8872](https://github.com/zeroclaw-labs/zeroclaw/pull/8872) | fix(zerocode): use runtime profile max_context_tokens for context meter | Merged |
| [#8884](https://github.com/zeroclaw-labs/zeroclaw/pull/8884) | test(log): cover llm request UTF-8 truncation | Merged |
| [#8833](https://github.com/zeroclaw-labs/zeroclaw/pull/8833) | fix(config): widen config-set alias auto-materialization past providers.* | Closed |
| [#8760](https://github.com/zeroclaw-labs/zeroclaw/issues/8760) | bug(runtime): keep daemon-owned agent output out of daemon stdout | Closed |
| [#8652](https://github.com/zeroclaw-labs/zeroclaw/issues/8652) | bug: ZeroCode transcript highlight does not dismiss on blank side clicks | Closed |
| [#8044](https://github.com/zeroclaw-labs/zeroclaw/issues/8044) | bug: Harden /model --agent scope with per-sender authorization | Closed |
| [#8094](https://github.com/zeroclaw-labs/zeroclaw/issues/8094) | bug: Anthropic provider added in Quickstart is unavailable in chat until reset | Closed |
| [#7836](https://github.com/zeroclaw-labs/zeroclaw/pull/7836) | fix(channels/orchestrator): use resolved agent config for strict_tool_parsing and parallel_tools | Merged |

**Key features and fixes that advanced today:**

- **SSRF security fixes progressing** — Three PRs ([#8826](https://github.com/zeroclaw-labs/zeroclaw/pull/8826), [#8827](https://github.com/zeroclaw-labs/zeroclaw/pull/8827), [#8713](https://github.com/zeroclaw-labs/zeroclaw/pull/8713)) targeting DNS rebinding checks, image_gen URL validation, and file_download host classification
- **MCP process leak fix** — PR [#8866](https://github.com/zeroclaw-labs/zeroclaw/pull/8866) addresses the long-standing stdio MCP orphan process accumulation bug
- **OpenAI-compatible endpoint** — Large PR [#8486](https://github.com/zeroclaw-labs/zeroclaw/pull/8486) adding chat completions API continues to be refined
- **Plugin capability catalog** — PRs [#8909](https://github.com/zeroclaw-labs/zeroclaw/pull/8909), [#8923](https://github.com/zeroclaw-labs/zeroclaw/pull/8923) advancing the plugin unification track

---

## Community Hot Topics

### Most Active Issues & PRs

1. **[Issue #5862](https://github.com/zeroclaw-labs/zeroclaw/issues/5862) — [Bug]: zeroclaw does not know it can add cron** (13 comments)
   - User reports asking ZeroClaw to schedule recurring tasks fails because the agent doesn't recognize its own cron capability
   - Underlying need: Better tool self-discovery or tool-use awareness so the agent can inform users of available system tools

2. **[Issue #6808](https://github.com/zeroclaw-labs/zeroclaw/issues/6808) — RFC: Work Lanes, Board Automation, and Label Cleanup** (13 comments)
   - Governance RFC proposing process improvements for issue triage and PR routing
   - Accepted, rollout in progress — signals project maturity and maintainer team scaling

3. **[Issue #6699](https://github.com/zeroclaw-labs/zeroclaw/issues/6699) — tool_filter_groups is a no-op for real MCP tools** (9 comments, **CLOSED**)
   - Critical bug where documented tool filtering had zero effect on MCP tools
   - Fix deployed, demonstrating responsive bug resolution for high-risk issues

4. **[Issue #6034](https://github.com/zeroclaw-labs/zeroclaw/issues/6034) — [Bug]: 单轮对话以及多轮对话会出现丢失 user message的现象** (8 comments, **CLOSED**)
   - Chinese-language bug report about losing user messages in single/multi-turn conversations
   - Severity S1 (workflow blocked), now resolved

5. **[Issue #6672](https://github.com/zeroclaw-labs/zeroclaw/issues/6672) — reasoning_content not passed back in agentic tool-call loops** (5 comments)
   - Xiaomi thinking mode models lose reasoning content across tool call turns
   - Severity S0 (data loss), still open — impacts Chinese-language model ecosystem

**Analysis:** The community is actively using ZeroClaw in production-ish scenarios with real LLM providers (Xiaomi, Qwen, custom endpoints) and encountering edge cases in agentic loops. The cron self-awareness bug (#5862) suggests a UX gap where agents need meta-cognition about available system tools.

---

## Bugs & Stability

### Critical/High Severity (S0-S1)

| Issue | Severity | Description | Fix Status |
|-------|----------|-------------|------------|
| [#6672](https://github.com/zeroclaw-labs/zeroclaw/issues/6672) | S0 - Data loss | reasoning_content lost in tool-call loops with Xiaomi models | Open, blocked |
| [#6558](https://github.com/zeroclaw-labs/zeroclaw/issues/6558) | S0 - Data loss | Provider error with Qwen 3.5 Plus (405 Method Not Allowed) | Open, blocked |
| [#8094](https://github.com/zeroclaw-labs/zeroclaw/issues/8094) | S0 - Data loss | Anthropic provider unavailable in chat after Quickstart add | **CLOSED** |
| [#8044](https://github.com/zeroclaw-labs/zeroclaw/issues/8044) | S1 - Security | /model --agent scope lacks per-sender authorization | **CLOSED** |

### Medium Severity (S2-S3)

| Issue | Severity | Description | Fix Status |
|-------|----------|-------------|------------|
| [#6517](https://github.com/zeroclaw-labs/zeroclaw/issues/6517) | S2 - Degraded | Context overflow causes hallucination/drift | Open, needs repro |
| [#8762](https://github.com/zeroclaw-labs/zeroclaw/issues/8762) | S2 - Degraded | Anthropic provider fixed 120s timeout for long turns | Open, accepted |
| [#7809](https://github.com/zeroclaw-labs/zeroclaw/issues/7809) | S2 - Degraded | Channel turns ignore strict/parallel tool flags | **CLOSED** |
| [#8760](https://github.com/zeroclaw-labs/zeroclaw/issues/8760) | S2 - Degraded | Daemon-owned agent output leaking to daemon stdout | **CLOSED** |
| [#8915](https://github.com/zeroclaw-labs/zeroclaw/issues/8915) | S2 - Degraded | agent_start/agent_end events missing for channel turns | Open, in-progress |
| [#8871](https://github.com/zeroclaw-labs/zeroclaw/issues/8871) | S3 - Minor | Third-party API 429 rate-limit responses not handled | Open, blocked |
| [#8810](https://github.com/zeroclaw-labs/zeroclaw/issues/8810) | S2 - Degraded | Telegram documentation is incorrect | Open, in-progress |

### Ongoing Security Fixes
- Three SSRF-related PRs in flight: [#8826](https://github.com/zeroclaw-labs/zeroclaw/pull/8826) (image_gen gate), [#8827](https://github.com/zeroclaw-labs/zeroclaw/pull/8827) (DNS rebinding check), [#8713](https://github.com/zeroclaw-labs/zeroclaw/pull/8713) (file_download host classifier)

---

## Feature Requests & Roadmap Signals

### In-Development Features Likely for Next Release

1. **OpenAI-compatible Chat Completions endpoint** ([#8550](https://github.com/zeroclaw-labs/zeroclaw/issues/8550), PR [#8486](https://github.com/zeroclaw-labs/zeroclaw/pull/8486))
   - Enables integration with Open WebUI, LobeChat, LangChain, Continue.dev
   - Major architectural change — likely for v0.9.0

2. **Plugin Unification** (Track A, [#8850](https://github.com/zeroclaw-labs/zeroclaw/issues/8850)+)
   - Capability catalog across all UIs ([#8907](https://github.com/zeroclaw-labs/zeroclaw/issues/8907))
   - Gateway and dashboard integration ([#8909](https://github.com/zeroclaw-labs/zeroclaw/pull/8909))
   - Host-mediated raw TCP/TLS for channel plugins ([#8923](https://github.com/zeroclaw-labs/zeroclaw/pull/8923))

3. **Local-First Mode** ([#5287](https://github.com/zeroclaw-labs/zeroclaw/issues/5287))
   - Compact prompting for small models, strict parser, no prompt leakage
   - High community interest (2 👍), accepted but not yet in-progress
   - Likely for v0.9.0 or v0.10.0

4. **Multi-User Milestone** ([#8290](https://github.com/zeroclaw-labs/zeroclaw/issues/8290))
   - Per-principal isolation, per-sender authorization
   - Building on uniform Principal identity model

5. **Discord Channel Parity** ([#7831](https://github.com/zeroclaw-labs/zeroclaw/issues/7831))
   - Embeds, typed slash options, components, voice support

### Emerging Feature Signals
- Right-click context menu for ZeroCode chat ([#8919](https://github.com/zeroclaw-labs/zeroclaw/issues/8919))
- Amazon Bedrock native integration support request ([#8925](https://github.com/zeroclaw-labs/zeroclaw/issues/8925))
- Channel goal command admission ([#8689](https://github.com/zeroclaw-labs/zeroclaw/pull/8689))

---

## User Feedback Summary

### Common Pain Points
1. **Tool self-awareness gap** — Users expect the agent to know about and proactively offer system tools (cron, image generation) rather than failing silently ([#5862](https://github.com/zeroclaw-labs/zeroclaw/issues/5862))
2. **Provider integration friction** — Custom/Chinese providers (Qwen, Xiaomi, custom endpoints) produce inconsistent errors, especially in tool-call loops ([#6672](https://github.com/zeroclaw-labs/zeroclaw/issues/6672), [#6558](https://github.com/zeroclaw-labs/zeroclaw/issues/6558))
3. **Context management issues** — Long conversations degrade into hallucination/drift without clear resolution path ([#6517](https://github.com/zeroclaw-labs/zeroclaw/issues/6517))
4. **Documentation inaccuracies** — Telegram channel docs contain incorrect examples, frustrating user onboarding ([#8810](https://github.com/zeroclaw-labs/zeroclaw/issues/8810))
5. **AWS/Bedrock configuration difficulty** — Users struggle with environment variable setup for cloud integrations ([#8925](https://github.com/zeroclaw-labs/zeroclaw/issues/8925))

### User Satisfaction Signals
- Multiple bug reports are being actively resolved (11 issues closed today)
- Chinese-language community is active and reporting issues (multiple WeChat/Chinese provider references)
- The cron bug user (#5862) demonstrates sophisticated usage — scheduling recurring tasks via natural language

---

## Backlog Watch

### Long-Unanswered Issues Needing Maintainer Attention

| Issue | Created | Last Updated | Status | Reason for Concern |
|-------|---------|--------------|--------|-------------------|
| [#5862](https://github.com/zeroclaw-labs/zeroclaw/issues/5862) | 2026-04-18 | 2026-07-10 | Open, blocked, stale-candidate | 13 comments, **120+ days open**, cron self-awareness is a core UX issue |
| [#6672](https://github.com/zeroclaw-labs/zeroclaw/issues/6672) | 2026-05-15 | 2026-07-10 | Open, blocked, needs-author-action | S0 severity, data loss with Xiaomi models, open 56 days |
| [#5287](https://github.com/zeroclaw-labs/zeroclaw/issues/5287) | 2026-04-04 | 2026-07-09 | Open, accepted | High-value feature (2 👍), open 97 days, no PR yet |
| [#6517](https://github.com/zeroclaw-labs/zeroclaw/issues/6517) | 2026-05-07 | 2026-07-10 | Open, blocked, stale-candidate | Context overflow causing hallucination, open 64 days |
| [#6558](https://github.com/zeroclaw-labs/zeroclaw/issues/6558) | 2026-05-10 | 2026-07-10 | Open, blocked, stale-candidate | S0 severity with Qwen provider, open 61 days |

### PRs Awaiting Review
- [#8272](https://github.com/zeroclaw-labs/zeroclaw/pull/8272) — Auth outcome test coverage (created 2026-06-24, open 16 days)
- [#8443](https://github.com/zeroclaw-labs/zeroclaw/pull/8443) — Matrix single-message progress drafts (created 2026-06-28, open 12 days, needs-author-action)

---

**Project Health Assessment:** 🟢 **Active & Healthy** — High developer throughput, rapid bug fixing (11 closed today), major architectural work in progress, and responsive security patching. Risks include stale high-severity bugs (especially around Chinese-language provider compatibility) and potential scope creep from multiple parallel trackers (v0.8.3, v0.9.0, plugin unification).

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*