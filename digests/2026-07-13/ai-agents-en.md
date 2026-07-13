# OpenClaw Ecosystem Digest 2026-07-13

> Issues: 500 | PRs: 500 | Projects covered: 13 | Generated: 2026-07-13 01:52 UTC

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

Here is the OpenClaw project digest for July 13, 2026.

---

## OpenClaw Project Digest: 2026-07-13

### 1. Today's Overview

Activity on the OpenClaw repository is at a critical inflection point. In the last 24 hours, 500 issues and 500 PRs were updated, indicating a massive surge in both community involvement and development output. While the merge/close rate (231 of 500 PRs) is healthy, a concerning volume of high-severity "platinum hermit" rated bugs remain open, including a critical memory leak and a systemic tool-output visualization failure. The release of `v2026.7.1-beta.6` shows the team is actively shipping, but the prevalence of `needs-product-decision` and `needs-maintainer-review` labels suggests a significant backlog in maintainer bandwidth.

### 2. Releases

**New Release: `v2026.7.1-beta.6`**

This release introduces several new model providers and model updates, along with default configuration changes.

- **New Models & Providers:**
    - Added support for **Featherless**, **Claude Sonnet 5**, and **Mythos 5**.
    - Introduced **Meta Muse Spark 1.1**.
    - Added **ClawRouter**, a new routing/switching service for agents.
- **Default Model Change:** The new-setup default model has been switched to **GPT-5.6**.
- **`/think` Command Update:** The `/think` command was extended to support more granular control, including `ultra` for Sol and Terra plans, and `max` for Luna.
- **Model Availability Refresh:** The system now honors model availability lists after OAuth re-authentication, fixing a bug where newly authorized models were not immediately selectable.

### 3. Project Progress

Over 230 PRs were merged or closed today, demonstrating substantial development velocity. Key areas of progress include:

- **Channel & Session Reliability:**
    - **PR #103562 (Open):** Fixes silent message loss in Discord by implementing retry logic for reply session initialization conflicts (closes #102381).
    - **PR #105775 (Open):** Fixes ClickClack outbound media delivery and configurable model replies.
    - **PR #105802 (Open):** Refactors channel pairing state from JSON to SQLite, resolving a long-standing state consistency issue for Telegram.
- **Gateway & Security:**
    - **PR #103534 (Open):** Enforces cross-plugin ownership checks in `sessions.patch`, closing a security boundary vulnerability.
    - **PR #105643 (Open):** Fixes a crash-loop by sweeping orphaned MCP temp directories at startup.
- **Configuration & Usability:**
    - **PR #105727 (Open):** Adds a warning when user-authored JSON5 comments in config are stripped by the system, preventing silent data loss.
    - **PR #105835 (Open):** Fixes provider-level context window settings not being inherited by child models.
    - **PR #105832 (Closed):** Scopes the Web UI sidebar session list to the currently selected agent, improving navigation for users with multiple agents.
- **Documentation & Tools:**
    - **PR #105826 (Open):** Restores the CI enforcement for unused exports (dead code), improving codebase hygiene.
    - **PR #105838 (Open):** Begins a large-scale refactor to share plugin contract scaffolds across 15+ channel plugins, reducing drift and maintenance burden.

### 4. Community Hot Topics

The community is most engaged around stability, cross-platform support, and security.

- **#1: [#75 - Linux/Windows Clawdbot Apps](https://github.com/openclaw/openclaw/issues/75)**
    - *Comments: 110 | 👍: 81*
    - **Analysis:** This is the oldest and most active issue by a significant margin. The overwhelming demand for native desktop apps on Linux and Windows is a clear signal that the user base is not just macOS/iOS. The volume of engagement on an eight-month-old issue suggests growing frustration, making it a strong candidate for being a high-level roadmap priority.

- **#2: [#6615 - Add denylist support for exec-approvals](https://github.com/openclaw/openclaw/issues/6615)**
    - *Comments: 7 | 👍: 7*
    - **Analysis:** This feature request for "allow everything except X" policies continues to gather traction. It started months ago and is marked `needs-product-decision`. Users want granular control over security without breaking their workflow with constant prompts, especially for known-safe operations.

- **#3: [#10118 - TUI: Support Shift+Enter for newline](https://github.com/openclaw/openclaw/issues/10118)**
    - *Comments: 5 | 👍: 4*
    - **Analysis:** A small but highly-requested UX feature for heavy terminal users. The demand for multi-line prompts in the TUI is a sign of professional/developer use cases driving feedback, where complex instructions are common.

### 5. Bugs & Stability

This is the area of highest concern. A cluster of P0 and P1 bugs indicates significant reliability issues introduced in recent releases.

- **P0 / Critical:**
    - **[Issue #91588 - Gateway Memory Leak](https://github.com/openclaw/openclaw/issues/91588):** RSS grows from 350MB to 15.5GB, causing repeated OOM crashes. This is the most severe infrastructure bug currently open.
    - **[Issue #104721 - All tool results return "(see attached image)"](https://github.com/openclaw/openclaw/issues/104721):** A complete failure of the tool output system. Agents cannot read stdout/stderr. This is a regression and a potential release blocker.
    - **[Issue #101290 - CLI startup corrupts live state DB](https://github.com/openclaw/openclaw/issues/101290):** A CLI health check can corrupt the SQLite database of a running gateway. This is a high-impact regression for production deployments.
    - **[Issue #99241 - Tool outputs render as unreadable image attachments](https://github.com/openclaw/openclaw/issues/99241):** A related issue to #104721, describing the symptom of ANSI-heavy or long-running tool output becoming unreadable.
- **P1 / High:**
    - **[Issue #102020 - Second message fails with "session initialization conflicted"](https://github.com/openclaw/openclaw/issues/102020):** A critical workflow-breaking bug where a session can only handle one message. Impact is cross-channel (Signal, Telegram).
    - **[Issue #87744 - Codex-backed Telegram reliably times out](https://github.com/openclaw/openclaw/issues/87744):** A reliability regression where Codex integration with Telegram fails to complete turns.
    - **[Issue #91009 - Codex hook processes cause CPU burnout](https://github.com/openclaw/openclaw/issues/91009):** A performance regression causing Gateway RPC stalls.
    - **[Issue #94939 - 6.x migration leaves empty conversation store](https://github.com/openclaw/openclaw/issues/94939):** A data loss bug specific to the v6 upgrade path, breaking proactive messages on MS Teams.

- **Fix PRs in Flight:**
    - **PR #105836** aims to fix the core of the "tool output as image" bug (#104721, #99241) by stripping braille glyphs that trigger the attachment rendering in WebChat.
    - **PR #101714 (Closed)** attempted to bound the model pricing cache, but was closed.
    - **PR #102082 (Open)** aims to fix Slack by suppressing progress-related "chrome" messages that were confusing the agent.

### 6. Feature Requests & Roadmap Signals

The release adds new model support and fixes, but the most telling signals for the next version come from the backlog.

- **Likely in Next Version (v2026.7.x):**
    - **Provider-Level Config Overrides:** Fixes for inherited `contextWindow` (PR #105835) and dynamic model discovery (Issue #10687) suggest a refactoring of the provider/model configuration layer is underway.
    - **Improved Exec Security:** The ongoing work on `denylist` support (Issue #6615) and "masked secrets" (Issue #10659) signals a major security hardening push, likely in response to the prompt injection risks noted in Issue #10659.

- **Roadmap Candidates (High Community Demand):**
    - **Official Linux/Windows Clients:** The demand is impossible to ignore. If a v7.0 roadmap exists, this should be a headline feature.
    - **Streaming TTS for Voice Calls (Issue #8355):** The request for sentence-level streaming (LLM -> TTS -> Audio) points to a desire for more natural and responsive voice interactions, a key differentiator for a personal AI assistant.
    - **Memory Trust Tagging (Issue #7707):** This feature addresses a fundamental attack vector (memory poisoning) and was filed with a high "diamond lobster" severity rating.

### 7. User Feedback Summary

The feedback paints a picture of a powerful but fragile system.

- **Frustration & Pain Points:**
    - **Core Reliability is the #1 complaint.** Users are reporting that conversation sessions break after the first or second message (#102020), tool results vanish or become unreadable (#104721, #99241), and the gateway crashes daily due to memory leaks (#91588).
    - **"Beta" Feeling is still strong.** The number of regressions in v2026.6.x and v2026.7.x suggests that stability testing is not keeping up with feature velocity. The high number of "needs live repro" labels suggests the team is struggling to replicate these issues, which is frustrating for users filing detailed bug reports.
- **Satisfaction & Use Cases:**
    - **Power Users are Pushing Boundaries.** The demand for advanced features like exec denylists, fine-grained context overflow handling, and Shift+Enter in the TUI indicates that users are integrating OpenClaw deeply into their development and system administration workflows.
    - **Multi-Platform is Key.** The near-universal desire for Linux/Windows clients shows that users see OpenClaw as a potential central hub for their digital life, regardless of OS.

### 8. Backlog Watch

Several important items have been languishing without clear maintainer direction, despite being flagged for evaluation.

- **[#7707 - Feature Request: Memory Trust Tagging by Source](https://github.com/openclaw/openclaw/issues/7707)**
    - *Updated: 2026-07-12 | Labels: needs-product-decision, needs-security-review*
    - **Status:** Stalled. This is a crucial security feature that has been open for over 5 months. The lack of a product decision is a risk, as memory poisoning is a known attack vector for autonomous agents.

- **[#10687 - Models: fully dynamic model discovery](https://github.com/openclaw/openclaw/issues/10687)**
    - *Updated: 2026-07-13 | Labels: maintainer, needs-product-decision, needs-live-repro*
    - **Status:** Stalled. While the issue itself is a feature request, it is tagged as `maintainer` and has been updated today. This suggests a maintainer is aware of it but hasn't made a decision on the implementation approach. The static model catalog is a frequent source of friction for users of fast-moving providers.

- **[#71301 - Ship version-matched bundled docs for agent onboarding](https://github.com/openclaw/openclaw/issues/71301)**
    - *Updated: 2026-07-12 | Labels: needs-product-decision*
    - **Status:** Stalled. This is a quality-of-life improvement that would allow the AI itself to better explain its own features. The lack of progress suggests it's not a priority, despite the potential to significantly reduce support load and user confusion.

---

## Cross-Ecosystem Comparison

Here is the cross-project comparison report based on the July 13, 2026 community digests.

---

## Cross-Project Comparison Report: Personal AI Agent Ecosystem
**Date:** 2026-07-13

### 1. Ecosystem Overview

The open-source personal AI assistant ecosystem is in a period of intense maturation, characterized by a clear divide between "reference" projects supporting broad experimentation and "appliance" projects focused on production stability. While innovation in model support and agentic workflows (routing, memory, tool use) continues at a high pace, a pervasive theme across nearly all projects is **stability regression** following major releases or rapid feature velocity. Community feedback consistently highlights that reliability, configuration consistency, and multi-platform support are now more critical differentiators than raw feature count. The ecosystem is shifting from proving what is possible to proving what is dependable.

### 2. Activity Comparison

The following table summarizes the 24-hour activity for each project as of July 13, 2026.

| Project | Issues Updated (Open) | PRs Updated (Active) | Release Today | Health Signal |
| :--- | :--- | :--- | :--- | :--- |
| **OpenClaw** | 500 (High Severity) | 500 (231 Merged) | ✅ v2026.7.1-beta.6 | **Fragile** – High velocity, but critical P0 bugs (memory leak, tool output failure) |
| **NanoBot** | 4 (Moderate) | 7 (3 Merged) | ❌ None | **Stable** – Focused on bug fixes, but critical Ollama caching issue unresolved |
| **Hermes Agent** | 50 (9 Open) | 50 (7 Merged) | ❌ None | **Strong** – High closure rate (41/50 issues), good maintenance velocity |
| **PicoClaw** | 5 (Moderate) | 2 (1 Merged) | ❌ None | **Stable** – Healthy mix of community bug reports and infrastructure fixes |
| **NanoClaw** | 3 (Moderate) | 13 (2 Merged) | ❌ None | **Resilient** – Critical token cap bug fixed within 24 hours; focused on ops hardening |
| **NullClaw** | 0 | 6 (4 Merged) | ❌ None | **Stable** – Stability-focused; all recent activity is production-oriented fixes |
| **IronClaw** | 10 (High) | 50 (22 Merged) | ❌ None | **At Risk** – Extremely high velocity but ~70% main-branch CI failure rate |
| **LobsterAI** | 1 | 2 (1 Merged) | ❌ None | **Cautious** – Single critical multi-agent config bug; low community activity |
| **CoPaw** | 21 (18 Open) | 11 (3 Merged) | ❌ None | **Under Pressure** – Post-2.0.0 release stabilization crunch; critical `MODEL_EXECUTION_ERROR` affecting all users |
| **ZeroClaw** | 30 (High) | 50 (3 Merged) | ❌ None | **At Risk** – High velocity, but critical S1 bugs (context overflow, SIGSEGV) remain open |

*Note: TinyClaw, Moltis, and ZeptoClaw reported no activity.*

### 3. OpenClaw's Position

- **Advantages:** OpenClaw remains the most feature-rich reference implementation, demonstrating the widest model provider support (Featherless, Claude Sonnet 5, Meta Muse) and the most advanced plugin/router architecture (ClawRouter). It is the clearest benchmark for frontier capabilities in the ecosystem.
- **Technical Differences:** Its architecture is the most ambitious, with a complex gateway system and a focus on enabling advanced agent composition (multi-agent, complex routing). This contrasts with more minimalist projects like NanoBot or NullClaw, which prioritize simplicity.
- **Community Size:** OpenClaw has the largest and most vocal community by orders of magnitude (110 comments on a single Linux/Windows client issue). However, this comes with a downside: the "wisdom of the crowd" is producing a vast bug backlog (500 issues) that overwhelms maintainer bandwidth, as evidenced by 231 out of 500 PRs being closed/merged – a rate that struggles to keep pace.

### 4. Shared Technical Focus Areas

Multiple projects are independently converging on the same architectural challenges:

1.  **Message Reliability & Delivery Guarantees (OpenClaw, NullClaw, NanoClaw):** Silent message drops, duplicate replies, and session initialization failures are being tackled by all three. **OpenClaw** has PRs for retry logic and state consistency (#103562). **NullClaw** has a critical fix for use-after-free in cron job delivery (#954). **NanoClaw** addresses reply duplication from re-wrap nudges (#3026).

2.  **Context Window & Prompt Caching (OpenClaw, ZeroClaw, NanoBot):** The battle for efficient context handling is universal. **OpenClaw** is fixing provider-level config inheritance for context windows (#105835). **ZeroClaw** is dealing with default context budget overflow (#5808). **NanoBot** has a critical, unresolved issue where Ollama integration adds 60 seconds per turn due to missing prompt caching (#4867).

3.  **Security Hardening & Granular Access Control (OpenClaw, NanoClaw, ZeroClaw):** All three are investing in more nuanced security models. **OpenClaw** is working on exec-approval denylists (#6615) and masked secrets (#10659). **NanoClaw** is building a `guard()` seam for all privileged actions (PR #2986). **ZeroClaw** has SOP capability not being fully integrated into the web UI (#8563).

### 5. Differentiation Analysis

| Dimension | OpenClaw | Hermes Agent | ZeroClaw | CoPaw |
| :--- | :--- | :--- | :--- | :--- |
| **Feature Focus** | Broad experimentation, model support | Platform adapter reliability | ZeroCode DSL & memory systems | Post-major-release stability & multi-channel |
| **Target User** | Expert developer/researcher | Production ops / systems integrator | Developer-user; operator of many agents | Power user on Windows/macOS |
| **Architectural Theme** | Complex, modular, plugin-rich | Mature, reliable, maintenance-first | Ambitious, DSLs, scheduled operations | UI-centric, desktop-first, Alibaba ecosystem |
| **Community Feedback** | "Powerful but fragile" | "Stable and responsive" | "Breaks out-of-the-box" | "Regressions from upgrade" |

### 6. Community Momentum & Maturity

**Tier 1: High Velocity, High Friction (Rapidly Iterating)**
- **OpenClaw, IronClaw, ZeroClaw:** These projects have the most PRs and issues, indicating massive community investment but significant stability debt. They are pushing the envelope but at the cost of reliability for the average user.

**Tier 2: Active Stabilization (Stabilizing)**
- **CoPaw, NanoClaw, NullClaw:** These are in a post-feature crunch stabilization phase. Activity is focused entirely on fixing regression bugs and shoring up production-critical infrastructure. This is a healthy sign of maturity.

**Tier 3: Steady State (Mature / Niche)**
- **Hermes Agent, PicoClaw, NanoBot:** These projects show moderate, consistent activity with a high issue-closure rate, indicating a more stable, predictable pace. They are likely serving a well-defined, satisfied user base without the chaos of rapid expansion.

**Tier 4: Low / Inactive:**
- **LobsterAI, TinyClaw, Moltis, ZeptoClaw:** Minimal to no community engagement suggests these are either very nascent, abandoned, or serving a highly specific niche with little external contribution.

### 7. Trend Signals for AI Agent Developers

1.  **Reliability is the New Feature:** The single loudest signal across the ecosystem is that users value a stable foundation over new model support. The "silent failure" (e.g., agents dying mid-response, logs lying about rate limits, sessions breaking after one message) is the most destructive UX pattern. Developer investment in observability, test infrastructure, and idempotency is now more critical than new tool integrations.

2.  **The "Default Config" is a Security and Usability Minefield:** Multiple projects (ZeroClaw, OpenClaw, NanoClaw) are being forced to rethink their default security posture (e.g., ZeroClaw's 32k context overflow, OpenClaw's lack of exec denylist). The era of "permissive by default" for personal agents is ending. Developers should invest in granular, configurable guardrails from day one.

3.  **Desktop & Mobile Clients are Non-Negotiable:** The top community request across the largest project (OpenClaw #75) is for native Linux/Windows apps. Users see their AI agent as a system-level tool, not a web application. Projects that ignore this (like PicoClaw's stale Android request) risk limiting their growth.

4.  **The "Prompt Caching Tax" is the #1 Performance Bottleneck:** The feedback from NanoBot's Ollama issue and IronClaw's work on prompt-cache break detection reveals a universal truth: for any agent using large context windows, the cost (both latency and money) of not caching is the single biggest performance problem. The most successful next-generation agents will be those that master prompt optimization and caching strategies.

5.  **Multi-Modal and Multi-Channel are Converging:** The ecosystem is moving beyond just text. Bugs related to image attachments (OpenClaw, IronClaw), local GIF delivery (Hermes), and voice call TTS streaming (OpenClaw) show that users expect their agent to handle media fluidly across all interfaces. The distinction between "chat," "coding," and "media" is disappearing.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

Here is the project digest for **NanoBot** on **2026-07-13**.

---

## NanoBot Project Digest – 2026-07-13

### 1. Today's Overview
Activity is moderate, with a clear focus on bug fixes and infrastructure stability. Four Issues and seven PRs were updated in the last 24 hours. The most critical signals involve regressions in the heartbeat system (affecting agent responsiveness) and a foundation-breaking caching bug with Ollama. A security-oriented PR restricting remote WebUI access was merged, indicating ongoing hardening of the deployment surface. While no new releases were cut today, the maintainer team is actively reviewing and merging priority-1 fixes.

### 2. Releases
**None.** No new versions or tags were published in the last 24 hours.

### 3. Project Progress (Merged/Closed PRs)
Three PRs were closed or merged:
- **[PR #4879 – feat(long_task): gate sustained-goal behind opt-in flag (default off)](https://github.com/HKUDS/nanobot/pull/4879)** — Closed as a duplicate. The sustained-goal feature (automatic turn continuation during long tasks) blocked user interaction. This decision signals maintainers are not pursuing that feature in its current form.
- **[PR #4892 – fix(webui): allow remote workspace access reduction](https://github.com/HKUDS/nanobot/pull/4892)** — Merged (Security/WebUI). Allows remote WebUI sessions to reduce Full Access to Default Permission without altering the workspace, and limits access escalation to localhost. This is a practical security improvement for multi-user deployments.
- **[PR #4898 – merge](https://github.com/HKUDS/nanobot/pull/4898)** — Closed. Likely a trivial merge commit or branch clean-up.

### 4. Community Hot Topics
The most active discussion centers on foundational performance and integration reliability:

- **[Issue #4867 – [CLOSED] Preserve exact prompt prefix to enable caching in Ollama](https://github.com/HKUDS/nanobot/issues/4867)** — 4 comments. The user reports that Ollama requests incur an **extra 60 seconds per turn** because NanoBot does not preserve the prompt prefix for cache hits. This makes local inference with 32 GB VRAM “totally unusable.” The underlying need is clear: without prompt prefix caching, NanoBot cannot be used effectively with local models at scale.
- **[Issue #4897 – [OPEN] Discord bot integration](https://github.com/HKUDS/nanobot/issues/4897)** — 0 comments, but represents a new user hitting a first-run integration wall (bot shows online but receives no messages). This suggests the Discord channel documentation or default configuration may be incomplete.
- **[PR #4896 – [OPEN] fix(heartbeat): rewrite prompt to execute tasks instead of reporting](https://github.com/HKUDS/nanobot/pull/4896)** — A regression fix with high community impact: the heartbeat cron job refactor broke the two-stage review/execute system. Agents now only report status without executing tasks.

### 5. Bugs & Stability
Four bugs were reported or actively addressed. Ranked by severity:

| Severity | Issue / PR | Description | Fix PR Exists? |
|----------|------------|-------------|----------------|
| **P1 (Critical)** | [PR #4896](https://github.com/HKUDS/nanobot/pull/4896) | Heartbeat cron regression: agents only list tasks instead of executing them. Introduced in `v0.2.1`. | ✅ Yes (open) |
| **P1 (Critical)** | [Issue #4867](https://github.com/HKUDS/nanobot/issues/4867) | Ollama unusable (60s extra per turn) due to missing prompt prefix caching. CLOSED but unresolved. | ❌ No |
| **P2 (Medium)** | [Issue #4894](https://github.com/HKUDS/nanobot/issues/4894) | `prune_dream_sessions()` fails on base64-encoded Dream session filenames; legacy glob pattern broken. | ❌ No |
| **P2 (Medium)** | [Issue #4893](https://github.com/HKUDS/nanobot/issues/4893) | `/dream-log` and `/dream-restore` show non-Dream commits (shared git history with backup commits). | ❌ No |

### 6. Feature Requests & Roadmap Signals
- **Prompt prefix caching (Issue #4867):** This is a mandatory feature for Ollama/LM Studio users. Although the issue is closed, the underlying problem remains unsolved and is likely to be re-implemented as a core performance feature in the next release.
- **Guided setup flows (PR #4855 – open):** Adds productized onboarding for Channels (Discord, Feishu) with validation, QR handoff, and safer secret handling. This signals a push toward lowering the barrier for non-developer users.
- **Opt-in sustained-goal (PR #4879 – closed as duplicate):** The community is actively debating how to handle long-running background tasks without blocking user interaction. Expect an alternative design to appear in the next milestone.

### 7. User Feedback Summary
- **Pain Point – Local model performance:** The 60-second Ollama latency (Issue #4867) is the loudest complaint. The user describes it as “totally unusable” even on high-end hardware. This is a retention risk for users running local models.
- **Pain Point – Discord integration friction:** A user successfully enabled the plugin and saw the bot online but received no messages. This suggests documentation gaps or default configuration errors in the gateway.
- **Pain Point – Dream subsystem confusion:** Two issues (#4893, #4894) show that recent filename encoding changes broke the pruning and log-display features, leading to confusing outputs for users of the Dream memory system.

### 8. Backlog Watch
- **[PR #4145 – fix: resolve #3958 — Weather Skill](https://github.com/HKUDS/nanobot/pull/4145)** — *Open for 42 days.* This skill-pack contribution has been idle for over a month. While non-critical, it suggests delays in reviewing skill ecosystem contributions.
- **[Issue #4897 – Discord bot integration](https://github.com/HKUDS/nanobot/issues/4897)** — *Open, 0 comments, no response from maintainers.* New user issue with zero engagement risks creating a negative first impression. Ideal for a quick triage or acknowledgement.
- **[Issue #4867 – Ollama caching](https://github.com/HKUDS/nanobot/issues/4867)** — *Closed but unresolved.* No linked PR or commit exists. The feature request is effectively abandoned unless a maintainer picks it up. This is a high-value target for the next release.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

# Hermes Agent Project Digest — 2026-07-13

## Today's Overview
The Hermes Agent project shows **high community engagement** with 50 issues updated and 50 PRs active in the last 24 hours. The vast majority of issues (41 of 50) are closed, indicating strong maintenance velocity—many of these are tagged `sweeper:implemented-on-main`, suggesting automated or systematic closures. The open issues (9) include longstanding refactoring work, a Windows-specific crash, and a high-impact `cua-driver` bug. The PR landscape is more active on the open side (43 open vs. 7 closed/merged), dominated by a large documentation generalization effort from `LeonSGP43` that spans 8+ PRs. No new releases were published today; the last release appears to be `v0.13.0` (v2026.5.7). **Overall health is good**, but the backlog of open PRs (especially older ones like #17392 from April) may be a concern for velocity.

## Releases
**No new releases today.** The latest known release remains `v0.13.0` (tagged v2026.5.7). No release notes, breaking changes, or migration guides are available for today.

## Project Progress
**7 PRs were merged or closed today**, all in the `sweeper:implemented-on-main` category:
- **[#23148](https://github.com/nousresearch/hermes-agent/pull/23148)** — docs(open-webui): generalized checkout path in Open WebUI bootstrap guide (part of #6237)
- **[#63505](https://github.com/nousresearch/hermes-agent/pull/63505)** — fix(telegram): send local GIFs as animations via `send_animation` with cross-platform file handling

Additionally, 41 issues were closed today. The **dominant theme** was platform adapter fixes:
- **Telegram:** Photo/reply-to-message forwarding fixed ([#22250](https://github.com/nousresearch/hermes-agent/issues/22250)), GIF delivery improved via #63505
- **NVIDIA/Kimi:** Base URL detection fixed ([#23158](https://github.com/nousresearch/hermes-agent/issues/23158)), Kimi K2-6 thinking mode content delivery fixed ([#22949](https://github.com/nousresearch/hermes-agent/issues/22949))
- **Matrix:** `send_message` now encrypts into E2EE rooms instead of posting plaintext ([#23055](https://github.com/nousresearch/hermes-agent/issues/23055))
- **Systemd:** Infinite restart loop via port conflict fixed ([#21915](https://github.com/nousresearch/hermes-agent/issues/21915))
- **Dashboard:** Stale WebSocket timeout fixes for `/api/pty` ([#22864](https://github.com/nousresearch/hermes-agent/issues/22864), [#21948](https://github.com/nousresearch/hermes-agent/issues/21948))

## Community Hot Topics
The most active discussions by comment count are:

1. **[#22791](https://github.com/nousresearch/hermes-agent/issues/22791)** (closed) — *Add Infisical as an External Vault backend* — 7 comments, 13 👍. Sub-issue of Phase 4 External Vaults (#3630). Community strongly wants a plugin ecosystem for secret managers, echoing earlier requests.

2. **[#21827](https://github.com/nousresearch/hermes-agent/issues/21827)** (closed) — *Topic-Aware Subagent Routing* — 6 comments. Proposes routing different tasks (research, coding, finance) to the most cost-effective model; users want to avoid paying top-tier costs for simple queries.

3. **[#22926](https://github.com/nousresearch/hermes-agent/issues/22926)** (closed) — *Kanban stale claim locks from dead workers* — 5 comments. A production-grade bug with automatic cleanup gaps; the sweeper marked it `implemented-on-main`.

4. **[#23158](https://github.com/nousresearch/hermes-agent/issues/23158)** (closed) — *NVIDIA base URL not recognized* — 4 comments. Chinese-language bug report indicating a i18n/provider detection gap.

5. **[#22949](https://github.com/nousresearch/hermes-agent/issues/22949)** (closed) — *Kimi K2-6 thinking mode content not displayed in Telegram* — 4 comments. Multi-provider (Kimi + NVIDIA) + multi-platform (Telegram) interaction bug.

**Underlying needs:** The community is pushing for (1) broader provider/LLM ecosystem support (Infisical, Cloudflare AI in #21164, Claude Team auth in #32392), (2) cost optimization via smarter model routing, and (3) improved production reliability (kanban locks, systemd restarts).

## Bugs & Stability
**High-severity bugs reported today:**

| Issue | Severity | Description | Fix Status |
|-------|----------|-------------|------------|
| [#63223](https://github.com/nousresearch/hermes-agent/issues/63223) | **Open/P2** | Windows GBK encoding error in `heartbeat.py` + SQLite lock crash on Chinese Windows | No fix PR yet |
| [#52951](https://github.com/nousresearch/hermes-agent/issues/52951) | **Open/High** | `cua-driver` UIAccess helper dies after Alt+Tab — blocks all computer_use for session | No fix PR |
| [#22986](https://github.com/nousresearch/hermes-agent/issues/22986) | **Closed/P2** | Codex retry rate ~8x higher post-v0.13.0 due to strict stream-timeout enforcement | Fixed on main |
| [#22926](https://github.com/nousresearch/hermes-agent/issues/22926) | **Closed/P3** | Kanban dead worker claim locks with no auto-cleanup | Fixed on main |
| [#22864](https://github.com/nousresearch/hermes-agent/issues/22864) | **Closed/P2** | Dashboard PTY WebSocket timeout before HTTP 101 flushes | Fixed on main |
| [#21915](https://github.com/nousresearch/hermes-agent/issues/21915) | **Closed/P2** | systemd infinite restart loop due to incomplete process cleanup | Fixed on main |

The **most critical open bug** is [#52951](https://github.com/nousresearch/hermes-agent/issues/52951) (cua-driver crash on window focus change), tagged `risk-platform-windows` and `platform/windows`, which completely breaks computer_use for Windows users until session restart. No fix PR exists yet.

The **second most critical** is [#63223](https://github.com/nousresearch/hermes-agent/issues/63223) — a new Windows encoding crash that appears in the latest desktop build.

## Feature Requests & Roadmap Signals
**Top requested features from today's activity:**

1. **[#22791](https://github.com/nousresearch/hermes-agent/issues/22791)** — Add **Infisical** as external vault backend (13 👍). Part of Phase 4 infrastructure work. Likely in next release.

2. **[#21827](https://github.com/nousresearch/hermes-agent/issues/21827)** — **Topic-Aware Subagent Routing** — match tasks to optimal models. High user interest for cost savings. Could appear if routed as a plugin/agent system.

3. **[#32392](https://github.com/nousresearch/hermes-agent/issues/32392)** (open) — **Claude Code / Claude Team authentication** as Hermes provider. Users want to leverage existing subscriptions without API billing. Open since May, 2 comments, 1 👍 — moderate traction.

4. **[#38164](https://github.com/nousresearch/hermes-agent/issues/38164)** / **[#38173](https://github.com/nousresearch/hermes-agent/issues/38173)** — **Tirith approval dialog for Desktop client**. Command confirmation popup needed for non-CLI mode. Duplicate issue filed.

5. **[#21164](https://github.com/nousresearch/hermes-agent/issues/21164)** — **Cloudflare Workers AI** as provider (3 comments, closed). Already marked `not-planned` by sweeper.

**Prediction for next version:** Infisical vault support (#22791) is the strongest candidate given it's a sub-issue of an ongoing Phase 4 effort and has high 👍 count. Topic-Aware Routing (#21827) may be deferred or become an optional plugin.

## User Feedback Summary
**Pain points expressed today:**
- **Chinese Windows users** face encoding crashes (#63223, #23158) — locale-specific regressions
- **Production reliability:** Kanban workers leave stale locks (#22926), systemd deployments may infinite loop (#21915) — trust issues for production users
- **Cost optimization:** Users unhappy paying for "top-tier models" on simple tasks (#21827)
- **Desktop app limitations:** No Tirith approval popup in Desktop client forces CLI use (#38164)
- **Feature gaps:** No Infisical, Cloudflare AI, or Claude Team auth — perceived as missing key ecosystem integrations
- **Local GIF delivery** on Telegram was broken (#63505) — now fixed

**Positive signals:**
- High closure rate (41/50 issues) suggests responsive maintainers
- Multi-platform (Telegram, Discord, Matrix, QQ, Teams) fixes indicate broad ecosystem care
- Community member `LeonSGP43` is systematically improving docs across the entire project

## Backlog Watch
**Issues/PRs needing maintainer attention:**

1. **[#52951](https://github.com/nousresearch/hermes-agent/issues/52951)** (open since June 26) — **cua-driver UIAccess crash on Alt+Tab**. High severity, Windows-only, no fix PR. Blocks computer_use for all Windows users. **Priority: Critical.**

2. **[#63223](https://github.com/nousresearch/hermes-agent/issues/63223)** (opened 2026-07-12, today) — Windows GBK encoding + SQLite lock crash. Fresh but no triage response yet.

3. **[#17476](https://github.com/nousresearch/hermes-agent/issues/17476)** (open since April 29) — Consolidate live-time PRs. 3 comments, P3, refactoring — has not been touched by maintainers.

4. **[#17392](https://github.com/nousresearch/hermes-agent/pull/17392)** (open since April 29) — Stale stream timeout fix during tool-call generation. P2, has `sweeper:risk-message-delivery` and `sweeper:blast-broad` labels — risky but important for reliability. No comments from maintainers in ~2.5 months.

5. **[#32392](https://github.com/nousresearch/hermes-agent/issues/32392)** (open since May 26) — Claude Team/pro auth provider. No maintainer response. If accepted, would be a major value-add for Anthropic ecosystem users.

**Call to action:** The `cua-driver` Windows crash (#52951) and the stale PR #17392 are the most actionable items that would significantly improve user trust and reliability.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

Here is the PicoClaw project digest for July 13, 2026.

---

## PicoClaw Project Digest – 2026-07-13

### 1. Today's Overview
Activity remains moderate, with 5 issues and 2 pull requests updated in the last 24 hours. The project shows a healthy mix of community bug reporting, infrastructure fixes, and ongoing maintenance. A critical bug regarding a “silent death” in the Matrix sync loop has gained traction, while a new feature request for ARMv7 Docker support was quickly closed as completed. One new bug was opened today involving provider prefix parsing, suggesting the provider abstraction layer is still maturing.

### 2. Releases
**No new releases today.** The latest available version remains unknown from this data.

### 3. Project Progress
One pull request was merged/closed today:

- **[#3190 [CLOSED] fix(i18n): sync missing locale keys from en.json to bn-in and cs translations](https://github.com/sipeed/picoclaw/pull/3190)** – This PR fills missing translation keys for Bengali (India) and Czech locales, improving internationalization completeness. No functional changes.

One PR remains open:

- **[#3251 [OPEN] fix(providers): capture the prompt cache token usage in Anthropic providers](https://github.com/sipeed/picoclaw/pull/3251)** – Aims to expose cache hit/miss token metrics from Claude, giving operators visibility into prompt caching effectiveness and cost savings.

### 4. Community Hot Topics
- **[Issue #3203 [OPEN] Matrix sync loop has no reconnection logic — silent death after network/server disruption](https://github.com/sipeed/picoclaw/issues/3203)** – This is the most active issue, with 2 comments and 1 👍 reaction. The community highlights a reliability hole: when the Matrix `/sync` loop dies, the process stays alive, so systemd’s `Restart=on-failure` does not trigger. Users are effectively left with a dead bot until manual restart. No fix PR is attached yet, but this is likely to be prioritized.

- **[Issue #3252 [OPEN] splitKnownProviderModel strips provider prefix when model ID contains known provider alias](https://github.com/sipeed/picoclaw/issues/3252)** – Filed today with no comments yet, but it points to a logic error in provider factory parsing that could break multi-provider setups.

### 5. Bugs & Stability
**High Severity:**
- **[Issue #3203 [OPEN] Matrix sync loop has no reconnection logic — silent death](https://github.com/sipeed/picoclaw/issues/3203)** – No reconnection logic after network or server disruption. Potential workaround: external watchdog scripts. No fix PR exists.

**Medium Severity:**
- **[Issue #3252 [OPEN] splitKnownProviderModel incorrectly strips provider prefix](https://github.com/sipeed/picoclaw/issues/3252)** – Affects model ID routing. Reproducible with certain provider aliases. No fix PR yet.

**Low Severity (closed today):**
- **[Issue #3194 [CLOSED] Received encrypted message but crypto is not enabled](https://github.com/sipeed/picoclaw/issues/3194)** – Closed, likely as a user environment misconfiguration or already fixed.

### 6. Feature Requests & Roadmap Signals
- **[Issue #3250 [CLOSED] Add Docker Compose support for armhf (ARMv7) devices](https://github.com/sipeed/picoclaw/issues/3250)** – Quickly closed, indicating that maintainers either already added this support or decided it is out of scope. If implemented, it signals a push toward low-power home server deployment (e.g., OneCloud, Raspberry Pi Zero).

- **[Issue #3182 [OPEN] Android version](https://github.com/sipeed/picoclaw/issues/3182)** – An older request (stale) to support running PicoClaw on Android. With 3 comments but no maintainer response, this appears low on the roadmap.

> **Prediction:** The Matrix reconnection fix and the Anthropic cache metrics PR are likely candidates for the next minor release (v0.2.10). ARMv7 support, if landed, may appear in a subsequent release.

### 7. User Feedback Summary
- **Pain Points:**
  - **Reliability:** The Matrix sync loop silent death is a clear frustration for users who expect always-on operation.
  - **Provider Configuration:** The parsing bug in `splitKnownProviderModel` shows that model ID formats remain confusing for users.
  - **Mobile Gap:** The stale Android issue suggests a gap in mobile/edge deployment support.
- **Use Cases:**
  - Users are deploying PicoClaw on low-power ARM devices (OneCloud) for home automation and lightweight AI assistants.
  - Anthropic API users want to monitor cache performance to manage costs effectively.

### 8. Backlog Watch
- **[Issue #3182 [OPEN] Android version](https://github.com/sipeed/picoclaw/issues/3182)** – Created 2026-06-26, last updated 2026-07-12, with 3 comments and no maintainer response. This request has been open over two weeks without official acknowledgement. If cross-platform mobile deployment is a strategic goal, this deserves a triage label or a roadmap milestone.

- **[Issue #3194 [CLOSED] Received encrypted message but crypto is not enabled](https://github.com/sipeed/picoclaw/issues/3194)** – Though closed, it was marked “stale” before closure, suggesting maintainers may be slow to handle edge-case Matrix crypto issues.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

# NanoClaw Project Digest — 2026-07-13

## 1. Today's Overview

The project shows **moderate activity** over the last 24 hours, with 3 open issues and 13 pull requests (11 open, 2 merged/closed). No new releases were published. The activity is concentrated on **critical operational stability** — fixing silent agent failures (token caps, container poisoning) and addressing core issues with reply delivery and rate-limit logging. Seven of the open PRs carry `[core-team]` or `[PR: Fix]` labels, indicating focused maintainer effort on infrastructure hardening. A new feature stream for operator CLI commands (`ncl approvals`) and scheduled-task templates also advanced.

## 2. Releases

**No new releases** in the last 24 hours. The latest available version remains unchanged from prior digests.

## 3. Project Progress

**Two PRs were merged/closed today:**

- **PR #3024 (closed/merged): `fix(container): raise the agent SDK's 32000 output-token cap to the model's real ceiling`** — Authored by javexed, this directly fixes issue #3023 (see Bugs & Stability below). The agent-runner's `CLAUDE_CODE_MAX_OUTPUT_TOKENS` environment variable was unset, silently capping all Claude agents at 32k output tokens. This fix configures the cap to match the model's actual maximum.

- **PR #2952 (closed): `Skill/add opencode stack`** — An operational/container skill PR by javexed, providing a full stack for the "opencode" integration. Closed after review.

**Notable open PRs that advanced (updated today):**
- **PR #2986** ([link](https://github.com/nanocoai/nanoclaw/pull/2986)) — Core-team guard seam: every privileged action now passes through a single `guard()` decision function (allow/hold/deny). This is phase 2 of guarded actions, centralizing access control.
- **PR #2987** ([link](https://github.com/nanocoai/nanoclaw/pull/2987)) — Opt-in local audit log skill for `ncl` surface, rebased and hardened.
- **PR #2982** ([link](https://github.com/nanocoai/nanoclaw/pull/2982)) — Fixes tool allowlist drift between the agent runner's `TOOL_ALLOWLIST` and the actual pinned `claude-code` CLI (2.1.197).
- **PR #3022** ([link](https://github.com/nanocoai/nanoclaw/pull/3022)) — Scheduled tasks in templates: recurring tasks defined in `tasks/*.md` with cron schedules, created paused on agent group stamp.

## 4. Community Hot Topics

The most active issues and PRs based on engagement (comments, reactions) are:

- **Issue #3016: "Every rate_limit_event is logged as a quota error"** ([link](https://github.com/nanocoai/nanoclaw/issues/3016)) — 1 comment, opened by glifocat. This is the most impactful user-facing bug (see Bugs section). The user reports 82 false positive "quota" errors over a week, all turns completed normally. **Underlying need:** Trust in monitoring/logging — users cannot distinguish real quota exhaustion from benign events.

- **Issue #3023: "Every Claude agent is silently capped at 32000 output tokens"** ([link](https://github.com/nanocoai/nanoclaw/issues/3023)) — Filed by javexed, who also submitted the fix (PR #3024, already merged). **Underlying need:** Long-running agents (CAD, code generation) failing silently halfway through a response, with no user-visible configuration.

- **Issue #3026: "Re-wrap nudge re-runs the model and duplicates replies"** ([link](https://github.com/nanocoai/nanoclaw/issues/3026)) — Filed by fjnoyp, with a companion fix PR #3028. **Underlying need:** Reply reliability and deduplication — agents that send replies via `send_message` get duplicate responses when the re-wrap nudge triggers.

## 5. Bugs & Stability

Three bugs reported today, ranked by severity:

| Severity | Issue | Summary | Fix Status |
|----------|-------|---------|------------|
| **Critical** | #3023 ([link](https://github.com/nanocoai/nanoclaw/issues/3023)) | All Claude agents silently capped at 32k output tokens; long turns die mid-response with an opaque API error. User hit this on a CAD project emitting long OpenSCAD files. | **Fixed** — PR #3024 merged today |
| **High** | #3016 ([link](https://github.com/nanocoai/nanoclaw/issues/3016)) | Every `rate_limit_event` logged as a quota error since #2965, even when status is "allowed". 82 false positives in one week for one install. Disrupts monitoring dashboards and operator trust. | **No fix PR yet** — issue open since Jul 11 |
| **High** | #3026 ([link](https://github.com/nanocoai/nanoclaw/issues/3026)) | Re-wrap nudge re-runs the model and sends duplicate replies when the agent already replied via `send_message`. | **PR #3028** ([link](https://github.com/nanocoai/nanoclaw/pull/3028)) — fix authored by ogarciarevett, captures message sequence to suppress duplicate nudge |

**Also notable:**
- PR #3020 ([link](https://github.com/nanocoai/nanoclaw/pull/3020)) — Rescues undelivered unwrapped replies (fixes #2369, #2393), with recap suppression for silent drops.
- PR #3027 ([link](https://github.com/nanocoai/nanoclaw/pull/3027)) — Container intermittently goes silent because `wakeContainer` fails with `EISDIR`: `/tmp` gets poisoned when `/tmp/onecli-proxy-ca.pem` is a directory. Fix relocates `TMPDIR`.

## 6. Feature Requests & Roadmap Signals

- **Operator CLI for approvals: PR #3029** ([link](https://github.com/nanocoai/nanoclaw/pull/3029)) — Adds `ncl approvals approve/reject/reject-with-reason` verbs. Currently operators can observe approvals but cannot resolve them. Likely for next minor release given it's a core-team PR with no blockers.

- **Scheduled tasks in templates: PR #3022** ([link](https://github.com/nanocoai/nanoclaw/pull/3022)) — Supports defining cron tasks in template directories. Created paused on stamp. Addresses a clear user pain point: "recreating scheduled tasks manually." Strong candidate for next version.

- **Audit log skill: PR #2987** ([link](https://github.com/nanocoai/nanoclaw/pull/2987)) — Opt-in local audit logging for the `ncl` surface. Still open after rebasing. Signals the project is building compliance/observability features, likely aimed at enterprise deployment scenarios.

- **Per-group harness capability toggles: PR #2983** ([link](https://github.com/nanocoai/nanoclaw/pull/2983)) — Extends the pattern of disabling duplicate Claude Code builtins (cron/scheduling) to more capabilities, with per-group configuration. This is an architectural improvement, likely targeted at the next major or minor release.

## 7. User Feedback Summary

- **Pain point: Monitoring reliability.** Users (glifocat, #3016) report that the agent-runner's logging is untrustworthy — it screams "rate limit error" when everything works fine. This erodes confidence in alerts and operational dashboards. The user specifically measured 82 false alarms in one week.

- **Pain point: Silent agent failures.** User javexed (#3023) hit a scenario where a long CAD generation died mid-stream with a vague API error. The real cause (unset token cap) was invisible to operators. The fix was merged within 24 hours — responsive, but the silent failure mode suggests a need for better default configuration validation.

- **Pain point: Reply duplication.** User fjnoyp (#3026) reports that agents using `send_message` get duplicated replies because the re-wrap nudge cannot see replies already delivered. This creates confusing user experiences — recipients see the same message twice.

- **Satisfaction signal:** The PR for WhatsApp sharing warnings (#3021) suggests the community is proactively thinking about compliance and brand safety, indicating a maturing user base concerned with production deployments.

## 8. Backlog Watch

- **Issue #3016: False quota errors** ([link](https://github.com/nanocoai/nanoclaw/issues/3016)) — Opened July 11, no fix PR yet. With 82 false positives per week for a single user, this is accumulating technical debt in operator trust. Needs maintainer attention, especially given that the root cause is in a recent change (#2965).

- **PR #2982: Tool allowlist drift** ([link](https://github.com/nanocoai/nanoclaw/pull/2982)) — Open since July 8, updated today. Fixes misnamed tools (e.g., `Task` → `Agent`) in the allowlist. The code comment above the allowlist is also misleading. This is a correctness issue that could silently prevent agents from using valid tools.

- **PR #2983: Per-group harness toggles** ([link](https://github.com/nanocoai/nanoclaw/pull/2983)) — Open since July 8, still in review. No maintainer comments visible. While not an emergency, it blocks the architectural unification of capability gating.

- **PR #2986: Guard seam phase 2** ([link](https://github.com/nanocoai/nanoclaw/pull/2986)) — The largest architectural change in the open PR list (multi-file, core security). No evidence of blockers, but the review surface is significant. This is the foundation for all future access control — delays here cascade to other features.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

# NullClaw Project Digest — 2026-07-13

## Today's Overview

The NullClaw project saw moderate activity today, with no new issues or releases but a substantial batch of pull request updates—six PRs were touched, four of which were closed/merged and two remain open. The maintainer team focused heavily on fixing critical cron job delivery failures, Discord gateway reliability, and agent output handling bugs. The active PRs (#954 and #953) are both from contributor `vernonstinebaker`, signaling sustained community interest in reliability improvements. Overall, the project is in a **stability-focused phase**, with all recent activity addressing production-grade issues rather than new features.

## Releases

No new releases were published today. The latest release remains the previous version.

## Project Progress

Four pull requests were closed or merged today, advancing several reliability and correctness fixes:

- **[#948 – fix cron agent delivery attribution](https://github.com/nullclaw/nullclaw/pull/948)** (closed, Author: `DonPrus`): Fixes cron job metadata propagation so that `agent_start` events are correctly attributed to the delivery channel/account. Also preserves delivery routing flags in both local storage and gateway payloads.

- **[#949 – fix: make queue_mode configurable from config.json](https://github.com/nullclaw/nullclaw/pull/949)** (closed, Author: `vernonstinebaker`): Adds `agent.default_queue_mode` configuration field, moves `QueueMode` enum to `config_types.zig` for single-source-of-truth, and parses from `config.json` with sensible fallback.

- **[#950 – fix(gateway): move port probe before allocations to prevent test leak](https://github.com/nullclaw/nullclaw/pull/950)** (closed, Author: `addadi`): Fixes a resource leak in test environments where `AddressInUse` errors caused premature exit without cleaning up allocated `Config`, `RuntimeProviderBundle`, and `SessionManager` objects.

- **[#951 – fix(agent_runner): suppress stderr initialization logs on agent failure](https://github.com/nullclaw/nullclaw/pull/951)** (closed, Author: `vernonstinebaker`): Prevents initialization logs (memory plan, MCP server registration, channel startup) from being posted to channels as false agent responses when the agent process exits non-zero.

## Community Hot Topics

The two open pull requests are the most active items today, both from `vernonstinebaker`:

- **[[OPEN] #954 – Fix: one-shot cron jobs silently fail to deliver messages (use-after-free in OutboundMessage.channel)](https://github.com/nullclaw/nullclaw/pull/954)**: This PR addresses a **critical bug** where scheduled "once" cron jobs execute and are removed from `cron.json` but produce no output. Root cause is identified as a use-after-free on `OutboundMessage.channel`. This is the most technically significant open issue, reflecting a need for safer memory management in message delivery pipelines.

- **[[OPEN] #953 – fix(discord): recover closed gateway sockets](https://github.com/nullclaw/nullclaw/pull/953)**: Addresses Discord gateway reconnect reliability by closing the active socket before joining heartbeat threads during cleanup, and treating stalled pre-HELLO reconnects as unhealthy after a bounded grace window. Includes regression test coverage.

Both PRs reflect community demand for **reliable message delivery** across all channels and **robust connection recovery** for Discord integrations—core infrastructure concerns for agent operations.

## Bugs & Stability

| Severity | Bug Description | Status |
|----------|----------------|--------|
| **Critical** | One-shot cron jobs silently fail to deliver messages due to use-after-free in `OutboundMessage.channel` (issue #941) | Open fix PR: [#954](https://github.com/nullclaw/nullclaw/pull/954) |
| **High** | Discord gateway sockets may not recover properly after disconnect, causing stalled reconnects | Open fix PR: [#953](https://github.com/nullclaw/nullclaw/pull/953) |
| **Medium** | Agent failures post initialization logs (memory plan, MCP server) to channels as false responses | Fixed in [#951](https://github.com/nullclaw/nullclaw/pull/951) |
| **Medium** | Gateway `AddressInUse` errors cause resource leaks in test environments | Fixed in [#950](https://github.com/nullclaw/nullclaw/pull/950) |
| **Low** | Queue mode not configurable from `config.json`, forcing default behavior | Fixed in [#949](https://github.com/nullclaw/nullclaw/pull/949) |
| **Low** | Cron agent delivery attribution missing, breaking channel/account tracking | Fixed in [#948](https://github.com/nullclaw/nullclaw/pull/948) |

No new bugs were reported in the last 24 hours; all fixes target previously known issues.

## Feature Requests & Roadmap Signals

Today's activity does not include new feature requests. However, the following developments signal likely near-term product direction:

- **Configurable queue modes per agent** (from [#949](https://github.com/nullclaw/nullclaw/pull/949)): The addition of `agent.default_queue_mode` suggests greater session configuration flexibility is being prioritized.
- **Discord gateway resilience** (from [#953](https://github.com/nullclaw/nullclaw/pull/953)): Indicates Discord remains a first-class channel, warranting dedicated socket recovery logic.
- **Cron delivery tracking** (from [#948](https://github.com/nullclaw/nullclaw/pull/948)): Improved attribution for cron agents suggests a push toward better auditability and accountability for scheduled tasks.

These fixes are likely to be included in the next minor release, as they address core functionality gaps.

## User Feedback Summary

No explicit user comments or reactions are recorded in today's data. However, the pattern of fixes (silent failures, wrong output attribution, missing configurations) strongly suggests user pain points around:

- **Unreliable scheduled message delivery** – cron jobs that appear to run but produce no visible output are highly confusing for users managing automation workflows.
- **Discord bot disconnection** – users relying on Discord as a primary channel likely experience missed messages and broken automation when gateway sockets fail to recover.
- **Misleading agent output** – seeing initialization logs appear in chat as agent responses undermines trust in agent behavior.

These fixes directly address real operational frustrations reported by users.

## Backlog Watch

No long-unanswered issues or PRs are noted today. All six items updated in the last 24 hours are recent (June 10–13, 2026) and actively being addressed by the maintainer team or regular contributors. The project's issue and PR hygiene appears healthy, with no backlogged items requiring maintainer attention.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

# IronClaw Project Digest — 2026-07-13

## 1. Today's Overview

IronClaw remains in a period of **extremely high development velocity**, with 50 pull requests updated in the last 24 hours (22 merged/closed, 28 open) and 10 active issues. The project is deep into a major architectural transformation — the "Reborn" loop resilience and extension-runtime workstreams — with multiple large (XL-sized) PRs in flight across 8 separate workstreams. However, **CI stability is the dominant source of friction**: a single systematic analysis (Issue #6014) reveals that ~70% of main branch pushes in July failed, with the `Code Coverage` matrix being the largest source of red. The core team is actively addressing this with static pre-push checks (PR #6022) and hermetic test isolation fixes (PR #6023). No new releases were published today.

## 2. Releases

_No new releases in the last 24 hours._ The most recent tagged release remains prior to this reporting period.

## 3. Project Progress

**22 pull requests were merged or closed today.** Key advancements include:

- **Agent Loop Resilience** (PR #5959, stack lead): The large "Reborn loop resilience" PR continues to advance through its stacked PRs, with prompt-cache break detection (PR #5975), skill listing optimization (PR #5977), and edit guardrails (PRs #5978, #5979) all progressing through review.
- **Extension Runtime Workstream**: PR #6012 (P5 — delivery coordinator + Slack/Telegram outbound) and PR #6025 (P6 — extraction completion with config/connect UI, frontend, CLI, migrations) are the 6th and 7th of 8 PRs in this train, signaling near-completion of a major infrastructure overhaul.
- **OpenAI-Compatible Cost Tracking**: PR #5976 adds per-run token usage and USD cost to the Reborn OpenAI-compatible Responses API — Phase 1 of a broader cost-transparency initiative.
- **MCP Registration Store**: PR #5970 rebuilt the per-user MCP registration store on top of the new `InstallationOwner` machinery, unblocking the MCP registration stack.
- **Dependency Updates**: Two large dependabot PRs (PRs #5926 closed, #6021 open) update 20-22 dependencies including `agent-client-protocol` from 0.10.4 → 1.2.0.

## 4. Community Hot Topics

- **Issue #2601 — CLI/TUI for Managing Secrets** (2 comments, open since 2026-04-18): This long-standing feature request highlights a significant onboarding friction. The author reports struggling with authentication and poor documentation around secret management. The underlying need is for a proper secrets management interface rather than manually editing configuration files or environment variables — a common pain point for new users configuring integrations with services.

- **Issue #6011 — Daily failure taxonomy** (0 comments but high impact): This systematic analysis of CI failures on 2026-07-12 provides critical transparency into the project's testing health, cataloging 136 non-pass benchmark runs and multiple CI failure classes.

- **Issue #6010 — NEAR AI inference (GLM-5.2) hangs** (closed, but notable): User reports that GLM-5.2 becomes unusable for interactive development due to frequent multi-minute hangs. This was auto-filed by IronClaw's bug reporting system, then closed — possibly fixed or superseded.

- **Issue #6009 — GLM-5.2 not in default model list** (closed): User must manually add GLM-5.2 to opencode's default model list. This reflects a configuration/deployment gap where the latest model isn't automatically discoverable.

## 5. Bugs & Stability

**High Severity:**
- **[BUG, #6014] CI fragility: ~70% main-push failure rate** — The single most impactful stability issue. Root cause is structural, not a bad commit. Fix in progress: PR #6022 and #6023 target static pre-push checks and test isolation fixes.
- **[BUG, #6015] Flaky: build_runtime_input_production_* races on std::env** — A real test-isolation defect causing ~14 tests to fail together intermittently. Fix: PR #6023 (direct fix) is open and linked.

**Medium Severity:**
- **[BUG, #6017] DB concurrency contract tests flaky** — Postgres delete/recreate race and libSQL concurrent writer issues under parallel load. No fix PR yet.
- **[BUG, #6016] Slack trigger-delivery e2e tests timeout** — Live offenders causing main branch failures as of 07-11. Fix: PR #6020 addresses Slack/outbound determinism.
- **[BUG, #5704] Image preview becomes transparent during chat** — Closed bug with visual regression during agent processing. Fixed.

**Lower Severity:**
- **[BUG, #6010] GLM-5.2 inference hangs** — Closed, likely resolved or mitigated.
- **[BUG, #6009] GLM-5.2 missing from default model list** — Closed, configuration fix.

## 6. Feature Requests & Roadmap Signals

**Near-term (likely next release):**
- **Secrets management CLI/TUI (#2601)** — Open since April, the project acknowledges the need (#2601 has a "Feature Proposal" tag). Given the extension-runtime workstream nearing completion, a secrets management interface is a plausible next QoL feature.
- **Per-run cost tracking (#5976)** — Already in PR; token usage and USD cost tracking is imminent for the OpenAI-compatible API.
- **Dependency readiness checks for `doctor` command (#6019)** — Extending the CLI diagnostic tool with LLM/provider credential readiness checks.

**Medium-term signals:**
- **MCP registration store (#5970)** — Being rebuilt post-#5499; this is foundational for third-party tool integration.
- **Prompt-cache break detection (#5975)** — Sophisticated optimization to prevent KV-cache collapse (demonstrated 3.5× cost multiplier on long agentic turns).
- **Edit guardrails (#5978, #5979)** — Claude Code-inspired safety checks (require read-before-edit, post-edit diagnostics) indicate the project is systematically closing the feature gap with Claude Code.

**Long-term:**
- **Extension runtime completion** — P6 (PR #6025) is the 7th of 8 PRs; the extension-runtime architectural overhaul appears to be wrapping up, which will enable richer third-party integrations.

## 7. User Feedback Summary

**Pain Points:**
- **Authentication friction** (#2601): Users struggle with service authentication and lack clear documentation for secrets management. The CLI/TUI request reflects frustration with manual configuration.
- **Inference instability** (#6010): NEAR AI inference (GLM-5.2) hangs for minutes during interactive coding, making it "unusable for real-time interactive development tasks."
- **Model availability gaps** (#6009): Latest models require manual fork and addition to opencode — a significant barrier for non-expert users.
- **CI unreliability**: While this is a developer pain point rather than end-user, the 70% main-push failure rate (#6014) slows down feature delivery for all users.

**Satisfaction Signals:**
- No overtly negative feedback about the direction of the Reborn architecture.
- The systematic failure taxonomy (#6011) and rapid issue filing (auto-bugs for inference hangs) suggest robust observability instrumentation.

## 8. Backlog Watch

| Issue | Created | Last Updated | Age | Status | Concern |
|-------|---------|--------------|-----|--------|---------|
| [#2601 — CLI/TUI for Managing Secrets](https://github.com/nearai/ironclaw/issues/2601) | 2026-04-18 | 2026-07-12 | ~86 days | OPEN, 2 comments | Long-unaddressed user pain point for onboarding. No maintainer response visible. Feature proposal with no linked PR. |
| [#5704 — Image preview transparency](https://github.com/nearai/ironclaw/issues/5704) | 2026-07-06 | 2026-07-12 | 6 days | CLOSED | Closed, but was a P3 bug bash item; worth verifying fix is deployed. |
| [#5934 — Admin secrets scope fix](https://github.com/nearai/ironclaw/pull/5934) | 2026-07-10 | 2026-07-12 | 2 days | OPEN | Core contributor PR that "validate and ship" is requested — appears blocked or awaiting final review. |

**Key observation**: The project's backlog is remarkably fresh — most issues are <2 weeks old. The one outlier (#2601, 86 days old) is the most significant backlog item and represents a genuine user onboarding issue that may be deprioritized in favor of the architectural workstreams.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

# LobsterAI Project Digest — 2026-07-13

Generated from GitHub data (github.com/netease-youdao/LobsterAI)

---

## 1. Today's Overview

Project activity remains moderate, with two pull requests updated and one open issue in the last 24 hours, though no new releases arrived. The open issue (#2293) has drawn attention with multiple comments and describes a multi-agent configuration persistence bug that appears regression-related. A stale PR (#1325) and a merged PR (#2065) were both updated, indicating maintainers are cleaning up older contributions. The overall project health is stable but shows signs of community friction around configuration isolation and data lifecycle management.

---

## 2. Releases

No new releases today. The last documented release remains prior to this digest period.

---

## 3. Project Progress

### Merged/Closed PRs Today
- **[Merged]** PR #2065 — `fix(agent): 使用短 UUID 替代名称生成 Agent ID` (Author: gongzhi-netease)  
  ✅ Addresses a critical design flaw where Agent IDs were derived from names (e.g., "My Assistant" → "my-assistant"), causing deleted agents' local data (workspace, sessions) to reappear when a new agent was created with the same name. The fix switches to short UUIDs for ID generation.  
  ⚠️ The PR notes a known *remaining* issue: deletion of an agent still does NOT clean up `cowork_sessions` (orphan data). This is flagged as a follow-up.  
  [Link to PR](https://github.com/netease-youdao/LobsterAI/pull/2065)

### No Other Merged/Closed PRs Today
Only one PR was closed/merged in the observed window.

---

## 4. Community Hot Topics

### Most Active Issue
- **Issue #2293** — "重启后，多个agent下的USER.md被覆盖替换的BUG？" (Author: yepcn)  
  - **Comments**: 4 | **Reactions**: 0  
  - **Created**: 2026-07-07 | **Updated**: 2026-07-12  
  - **Summary**: User reports that after modifying the "About You" page or `USER.md` for one agent, all agents' `USER.md` files are overwritten with the main agent's content upon restart. They tested by manually editing `workspace-*` folders while the software was closed, only to find all agents' `USER.md` replaced on next app launch. User suspects this is a regression from a recent update.  
  - **Analysis**: Describes a serious multi-agent configuration isolation failure. The behavior suggests a shared state or incorrect file-path resolution when reading/writing USER.md during startup.  
  [Link to Issue](https://github.com/netease-youdao/LobsterAI/issues/2293)

### Most Active PR
- **PR #1325** — `feat(ui): 为新建对话图标按钮添加悬停提示` (Author: 0xFLX)  
  - **Comments**: 0 | **Updated**: 2026-07-12 (stale since April 2)  
  - **Summary**: Adds `title` attributes to the new-chat icon button across collapsed sidebar, session detail, agent management, and MCP views.  
  - **State**: Open, stale (3+ months old).  
  - **Signal**: Low-urgency UX polish, but lack of maintainer response may indicate lower prioritization.  
  [Link to PR](https://github.com/netease-youdao/LobsterAI/pull/1325)

---

## 5. Bugs & Stability

### Active Bugs (Ranked by Severity)

| Severity | Issue | Description | Status |
|----------|-------|-------------|--------|
| 🔴 High | [#2293](./issues/2293) | Multi-agent USER.md overwritten by main agent on restart — data isolation broken. Suspected regression. | Open, 4 comments, user actively testing |
| 🟡 Medium | (related, PR #2065 context) | Deleting an agent does not clean up `cowork_sessions` — orphaned session data persists. | Known, deferred follow-up |

### Observations
- Bug #2293 is the single most critical stability concern today, as it directly destroys intentional per-agent configuration without warning.
- The fix from PR #2065 (UUID-based agent IDs) partially addresses data resurrection but explicitly acknowledges the deletion cleanup gap — a related stability risk.

No crash-level or regression-level bugs reported beyond these two.

---

## 6. Feature Requests & Roadmap Signals

### User-Requested Feature (via Bug #2293)
- **Implicit request**: Proper multi-agent configuration isolation — each agent should maintain its own `USER.md` and "About You" content independently, surviving restarts and modifications to other agents.  
- **Predicted priority**: High. This is a core UX requirement for power users who run multiple specialized agents. Fix likely in next patch.

### Stale PR #1325 — UX Polish
- **Request**: Tooltip hover text for new-chat icon when sidebar is collapsed.  
- **Prediction**: Likely merged in a minor release once a maintainer reviews; not blocking but improves usability for new users.

### Roadmap Signal (from PR #2065)
- **Direction**: Moving from name-based to UUID-based agent identity — signals a push toward more robust data lifecycle management and eventual support for proper agent deletion workflows (including session cleanup).

---

## 7. User Feedback Summary

### Pain Points
- **Data isolation failure** (Issue #2293): User explicitly reports frustration that customizing one agent's `USER.md` corrupts all others — *"I can't set different requirements for different agents."*  
- **Reappearing data** (PR #2065 context): Named-based agent IDs caused deleted agents to "resurrect" when a new agent shared the same name — *unsettling user experience*.  
- **Deletion incompleteness**: Orphan `cowork_sessions` remain after agent deletion — risk of unintended behavior or wasted storage.

### Satisfaction Signals
- No positive user feedback was recorded in the 24h window. The community contributions (PRs #1325, #2065) suggest engaged developers who care about polish and correctness.

### Overall Sentiment
Cautiously negative among power users encountering configuration bugs. The agent configuration overwrite bug is a regression that undermines trust in multi-agent workflows.

---

## 8. Backlog Watch

### Issues Requiring Maintainer Attention

| Item | Age | Type | Why It Matters |
|------|-----|------|----------------|
| **#1325** — New chat icon tooltip | 102 days (stale) | Open PR | Low-effort UX improvement; lack of review may discourage future contributors |
| **#2293** — Multi-agent USER.md overwrite | 6 days | Open bug | High severity, actively discussed by user; no maintainer response yet visible in public thread |

### Recommendation
- **Immediate**: Assign a maintainer to reproduce and triage Issue #2293 — this is an active blocker for multi-agent users.
- **Short-term**: Review and merge or close stale PR #1325 to clear backlog and encourage community contributions.
- **Future**: Complete the deletion cleanup tracked in PR #2065 to close the data orphan gap.

---

*Digest generated on 2026-07-13 from public GitHub data for LobsterAI (netease-youdao/LobsterAI).*

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyagi">TinyAGI/tinyagi</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

# CoPaw Project Digest — 2026-07-13

## Today's Overview

CoPaw is experiencing a significant post-2.0.0 release stability crunch, with **21 issues updated in the last 24 hours** (18 open, 3 closed) and **11 pull requests active** (8 open, 3 merged/closed). The activity level is high, suggesting a community actively testing and reporting regressions from the v2.0.0 major release. No new releases were published today. The project is in a **stabilization phase**, with several critical `MODEL_EXECUTION_ERROR` bugs, context compression pairing failures, and backward-compatibility gaps dominating the tracker. The maintainer response appears mixed — some issues remain uncommented for days while others receive rapid PRs, indicating possible bottleneck in triage capacity.

## Releases

**No new releases today.** The last published version remains **v2.0.0** (Windows Tauri desktop app, qwenpaw-desktop.exe). Users continue reporting regressions from this release.

## Project Progress

Three PRs were merged/closed today:

- **[PR #5990](https://github.com/agentscope-ai/QwenPaw/pull/5990)** (closed) — `fix(compat): handle legacy 'file' block type in _coerce_block` — Addresses 1.x to 2.0 message deserialization gap where `file`-type blocks were not converted to `DataBlock`, causing `ToolResultBlock` failures.
- **[PR #5988](https://github.com/agentscope-ai/QwenPaw/pull/5988)** (closed) — Same fix, likely duplicate/iterative PR.
- **[PR #5987](https://github.com/agentscope-ai/QwenPaw/pull/5987)** (closed) — `fix(scroll): sanitize unpaired tool messages after context compression` — First-time contributor PR addressing orphan `tool_result` messages after compression eviction.

**Active PRs with significant traction:**
- **[PR #5726](https://github.com/agentscope-ai/QwenPaw/pull/5726)** (ready-for-human-review) — Implements vision fallback for text-only models; allows `qwen3-max` to handle images via fallback to `qwen-vl-max`. This is a significant feature enhancement ready for maintainer review.
- **[PR #5992](https://github.com/agentscope-ai/QwenPaw/pull/5992)** (first-time-contributor) — Adds per-session model overrides, a highly requested feature for multi-use-case agents.

## Community Hot Topics

### Most Active Issues

1. **[Issue #5996](https://github.com/agentscope-ai/QwenPaw/pull/5996)** — `[Bug]: 2.0.0对话时会产生MODEL_EXECUTION_ERROR` — **5 comments, most active issue.** Root cause identified: `_hint.py` constructs messages with `ToolResultBlock` but without matching `tool_calls`, violating OpenAI API requirements. This is a core serialization bug in QwenPaw's hint system affecting all users.

2. **[Issue #5952](https://github.com/agentscope-ai/QwenPaw/pull/5952)** — `[Bug]: auto-memory fails with "No module named 'agentscope.tool._builtin._scripts'"` — **4 comments.** Affects Windows Tauri desktop app; memory summarization completely broken due to missing module packaging. Has been open since July 10 with no closed status.

3. **[Issue #5986](https://github.com/agentscope-ai/QwenPaw/pull/5986)** — `Bug: Context compression breaks tool_call/tool_result pairing -> 400 BadRequestError` — **4 comments.** Eviction logic doesn't guarantee `tool_calls/tool_result` pairing, causing OpenAI API 400 errors. Related PRs [#5987](https://github.com/agentscope-ai/QwenPaw/pull/5987) and [#5989](https://github.com/agentscope-ai/QwenPaw/pull/5989) exist as fixes.

**Underlying needs:** Users are hitting fundamental API compatibility issues post-v2.0.0, particularly around OpenAI's strict `tool_calls` → `tool` message ordering requirement. The hint system and context compression are both producing malformed message sequences.

## Bugs & Stability

### Critical Severity

1. **`MODEL_EXECUTION_ERROR` — Hint system causes orphan `tool` messages** — [Issue #5996](https://github.com/agentscope-ai/QwenPaw/pull/5996), [Issue #6002](https://github.com/agentscope-ai/QwenPaw/pull/6002), [Issue #5985](https://github.com/agentscope-ai/QwenPaw/pull/5985) — Multiple reports of identical root cause: assistant messages containing `ToolResultBlock` without `tool_calls` field. Fix PR [#5989](https://github.com/agentscope-ai/QwenPaw/pull/5989) provides multi-layer defense but is still open.

2. **Context compression orphans tool results** — [Issue #5986](https://github.com/agentscope-ai/QwenPaw/pull/5986) — Evicts tool_call messages but retains tool_result messages, causing 400 errors. PRs [#5987](https://github.com/agentscope-ai/QwenPaw/pull/5987) and [#5989](https://github.com/agentscope-ai/QwenPaw/pull/5989) address this.

### High Severity

3. **Auto-memory completely broken on Windows desktop** — [Issue #5952](https://github.com/agentscope-ai/QwenPaw/pull/5952) — `No module named 'agentscope.tool._builtin._scripts'` due to missing PyInstaller bundle inclusion. PR [#5997](https://github.com/agentscope-ai/QwenPaw/pull/5997) provides the fix (desktop bundle inclusion).

4. **Session mapping loss on upgrade to 2.0.0** — [Issue #5964](https://github.com/agentscope-ai/QwenPaw/pull/5964) — Chat history exists in DB but session mapping is lost; web UI returns 500 errors when opening old conversations.

5. **Skill pool completely broken for new skills** — [Issue #6001](https://github.com/agentscope-ai/QwenPaw/pull/6001), [Issue #6000](https://github.com/agentscope-ai/QwenPaw/pull/6000) — No newly installed skill appears in skill pool regardless of placement or configuration.

6. **Governance/Auto mode overly aggressive** — [Issue #5994](https://github.com/agentscope-ai/QwenPaw/pull/5994) — Every operation triggers security review; no allow rules hit in AUTO mode.

7. **Feishu channel message display inconsistency** — [Issue #6003](https://github.com/agentscope-ai/QwenPaw/pull/6003) — Messages received by webhook but not displayed in web UI, though still executed.

### Medium Severity

- **Plugin HTTP routes lost after workspace hot-reload** — [Issue #5977](https://github.com/agentscope-ai/QwenPaw/pull/5977)
- **`qwenpaw doctor` health check endpoint wrong** — [Issue #5983](https://github.com/agentscope-ai/QwenPaw/pull/5983)
- **Shell execution requires approval every time** — [Issue #5982](https://github.com/agentscope-ai/QwenPaw/pull/5982)
- **Electron CLI tool crashes under sandbox** — [Issue #5979](https://github.com/agentscope-ai/QwenPaw/pull/5979)
- **Memory compact fails with invalid session characters** — [Issue #5978](https://github.com/agentscope-ai/QwenPaw/pull/5978)

## Feature Requests & Roadmap Signals

1. **Cross-channel session handoff** — [Issue #5999](https://github.com/agentscope-ai/QwenPaw/pull/5999) — Request to continue same agent session across Console, Feishu, DingTalk seamlessly. This is a sophisticated multi-channel orchestration feature likely requiring architectural changes.

2. **Per-session model overrides** — [PR #5992](https://github.com/agentscope-ai/QwenPaw/pull/5992) — Being actively implemented by a first-time contributor. Would allow different LLMs per conversation within same agent.

3. **Vision fallback for text-only models** — [PR #5726](https://github.com/agentscope-ai/QwenPaw/pull/5726) — Ready for review; would significantly improve multimodal UX.

4. **Slash command autocomplete in all UIs** — [PR #5869](https://github.com/agentscope-ai/QwenPaw/pull/5869) — Under review; exposed system commands in TUI and web console.

**Prediction:** Cross-channel session handoff and per-session model overrides are likely candidates for next minor release (2.1.0), given community demand and existing PRs. The vision fallback feature may be merged first as it's ready for review.

## User Feedback Summary

**Pain points (recurring themes):**
- **v2.0.0 stability regression** is the dominant theme — users report features working in v1.x (SSH offline, profiles, skill discovery) are now broken or missing entirely.
- **Tool execution flow is broken** — three separate issues ([#5996](https://github.com/agentscope-ai/QwenPaw/pull/5996), [#5986](https://github.com/agentscope-ai/QwenPaw/pull/5986), [#5985](https://github.com/agentscope-ai/QwenPaw/pull/5985)) describe models returning 400 errors due to malformed message ordering. This affects all users interacting with OpenAI-compatible APIs.
- **Memory system failures** — auto-memory (#5952) and/compact (#5978) both broken, affecting agent long-term memory.
- **V1 → v2 migration breaks** — session mapping loss (#5964), legacy file block handling (PRs #5990, #5991, #5993), skill pool not detecting new skills (#6001) — users unable to upgrade smoothly.
- **Sandbox and governance friction** — shell execution prompts every time (#5982), AUTO mode blocks everything (#5994), Electron CLI crashes in sandbox (#5979) — power users struggling with new security model.
- **UI inconsistencies** — model search field auto-filled with username (#5981), Feishu messages not displayed (#6003), format compact rounding error (PR #5791).

**Satisfaction signals:** None observed today. The issue tracker reflects frustration rather than positive feedback, consistent with a post-major-release stabilization period.

**Case study from Issue #5998:** User lost trust after agent used old plan instead of confirmed new plan for itinerary generation. This memory inconsistency bug undermines user confidence in agent reliability for multi-step tasks.

## Backlog Watch

| Item | Created | Last Updated | Days Unresolved | Notes |
|------|---------|--------------|-----------------|-------|
| [#5952](https://github.com/agentscope-ai/QwenPaw/pull/5952) Auto-memory broken (Windows) | Jul 10 | Jul 12 | **3 days** | No maintainer response; PR [#5997](https://github.com/agentscope-ai/QwenPaw/pull/5997) provides fix |
| [#5964](https://github.com/agentscope-ai/QwenPaw/pull/5964) Session mapping loss on upgrade | Jul 11 | Jul 12 | **2 days** | No fix PR yet |
| [#5996](https://github.com/agentscope-ai/QwenPaw/pull/5996) MODEL_EXECUTION_ERROR | Jul 12 | Jul 13 | **1 day** | High activity, PR [#5989](https://github.com/agentscope-ai/QwenPaw/pull/5989) in review |
| [#5726](https://github.com/agentscope-ai/QwenPaw/pull/5726) Vision fallback (ready-for-review) | Jul 2 | Jul 13 | **11 days** | Waiting maintainer review; significant feature enhancement |
| [#5869](https://github.com/agentscope-ai/QwenPaw/pull/5869) Slash autocomplete (Under Review) | Jul 8 | Jul 12 | **5 days** | Under review, no merge |

**Priority items needing maintainer attention:**
1. [#5952](https://github.com/agentscope-ai/QwenPaw/pull/5952) — Windows desktop auto-memory blocker — should be prioritized given PR fix exists
2. [#5964](https://github.com/agentscope-ai/QwenPaw/pull/5964) — Session mapping loss blocks all users who upgraded with existing conversations
3. [#5726](https://github.com/agentscope-ai/QwenPaw/pull/5726) — Vision fallback ready-for-review for 11 days; community may lose interest
4. [#6001](https://github.com/agentscope-ai/QwenPaw/pull/6001) / [#6000](https://github.com/agentscope-ai/QwenPaw/pull/6000) — Skill pool completely broken; core extensibility mechanism non-functional

**Project health assessment:** **Yellow/Amber** — Community activity is high and contributors are actively submitting fixes, but the volume of critical regressions from v2.0.0 exceeds current triage throughput. The project needs a stabilization sprint focused on the hint system, context compression pairing, backward compatibility layer, and skill/memory systems before new features can safely land.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

# ZeroClaw Project Digest — 2026-07-13

## Today's Overview

The ZeroClaw project remains in a high-activity phase with 30 issues and 50 PRs updated in the last 24 hours, indicating sustained development velocity. The overwhelming majority of activity centers on the upcoming v0.8.3 and v0.8.4 maintenance trains, with significant work across the memory subsystem, runtime stability, provider compatibility, and ZeroCode consolidation. Critical severity bugs (S1) remain open in the runtime, MCP tool-schema cloning, and OpenAI provider paths, though multiple fix PRs are in review. Community engagement is moderate, with several long-running trackers coordinating multi-PR rollouts for observability, SOP capabilities, and operator UX onboarding.

## Releases

**No new releases today.** The project has been tracking toward v0.8.3 and v0.8.4 (targeting July 31, 2026) with multiple coordinated milestone trackers (Issues #8070, #8071, #8073, #8360, #8362, #8363, #8357). No release artifacts were published in the reporting period.

## Project Progress

**3 PRs were merged or closed today:**
- **#8653 [CLOSED]:** Feature request for auto-resuming the most recent ZeroCode Code session on pane entry was accepted and closed without a merged PR, suggesting the feature may have been deemed less critical for the current milestone.
- **#8940 [CLOSED]:** A fix for ZeroCode UI fill_style() rendering in queue sidebar and session picker overlays was closed as a duplicate, likely superseded by larger UI consolidation work.
- **#9027 [OPEN]:** A fix for AMQP dispatch idempotency for SOP triggers was opened today as part of the SOP milestone tracker (#8288), ensuring duplicate SOP runs are prevented when one AMQP delivery matches multiple SOPs.

Key PRs under active review include the memory subsystem overhaul (PRs #8893, #8895, #8897, #8898, #8900, #8984), which collectively introduce audit trails, retrieval caching, reranked recall, typed memory classification, and content screening. The ZeroCode Code pane consolidation (#8655) and WASM plugin execution prototype (#8661) also remain active.

## Community Hot Topics

**Most active issues (by comment count):**

1. **#5808 — Default 32k context budget exceeded by system prompt + tool definitions (8 comments)**  
   *[Bug, priority:p1, status:in-progress]*  
   URL: https://github.com/zeroclaw-labs/zeroclaw/issues/5808  
   *Community need:* First-iteration context overflow causes perpetual preemptive trimming, effectively breaking default configuration for any non-trivial agent. This is a foundational usability blocker that prevents new users from running the project out-of-the-box without deep configuration changes.

2. **#6055 — Slack: hydrate thread context from conversations.replies (6 comments)**  
   *[Feature, channel:slack, priority:p2]*  
   URL: https://github.com/zeroclaw-labs/zeroclaw/issues/6055  
   *Community need:* Users working with Slack threads find the bot's lack of conversational memory frustrating—every mention is treated as a fresh interaction. The feature request for backfilling thread history reflects a desire for natural, contextual conversation rather than stateless command execution.

3. **#6641 — Turn-level OTel trace correlation (5 comments)**  
   *[Feature, observability:otel, priority:p2]*  
   URL: https://github.com/zeroclaw-labs/zeroclaw/issues/6641  
   *Community need:* Operators managing multiple agents need end-to-end observability per agent turn to debug latency, tool failures, and memory behavior. This is infrastructure for production deployments.

**Most active PR (by scope/size):**  
- **#8655** — ZeroCode Code pane consolidation (XL size, 13 labels)  
  URL: https://github.com/zeroclaw-labs/zeroclaw/pull/8655  
- **#8984** — Memory content screening at write/recall boundaries (XL size, security-focused)  
  URL: https://github.com/zeroclaw-labs/zeroclaw/pull/8984

## Bugs & Stability

**Critical (S1 - workflow blocked):**

1. **#5808 — Default context budget overflow (priority:p1)**  
   *First iteration of fresh conversation already exceeds 32k budget by ~3.3x due to system prompt + tool definitions.*  
   URL: https://github.com/zeroclaw-labs/zeroclaw/issues/5808  
   *No fix PR open.*

2. **#8654 — skill-review fork panic → daemon SIGSEGV (priority:p1)**  
   *Out-of-range slice in skills/review.rs crashes the entire agent process (SIGSEGV under panic=abort) after tool-heavy turns.*  
   URL: https://github.com/zeroclaw-labs/zeroclaw/issues/8654  
   *No fix PR open.*

3. **#8563 — SOPs not available through web dashboard (priority:p1)**  
   *Configured SOPs at shared/sops path are not detected by agent runtime in web chat sessions.*  
   URL: https://github.com/zeroclaw-labs/zeroclaw/issues/8563  
   *No fix PR open.*

**High (S2 - degraded behavior):**

4. **#8642 — MCP/tool-schema cloning drives unbounded RSS growth**  
   *Memory growth path separate from the WSL2 restart-storm issue.*  
   URL: https://github.com/zeroclaw-labs/zeroclaw/issues/8642  
   *No fix PR open.*

5. **#9019 — OpenAI Responses provider rejects vision-capable models**  
   *Hardcoded ProviderCapabilities.vision = false blocks image input despite model support.*  
   URL: https://github.com/zeroclaw-labs/zeroclaw/issues/9019  
   *No fix PR open.*

6. **#9016 — OpenAI tool turns fail when reasoning effort sent with function tools**  
   *Provider returns errors when non-none reasoning effort is sent alongside function tools.*  
   URL: https://github.com/zeroclaw-labs/zeroclaw/issues/9016  
   *No fix PR open.*

**Fix PRs in review for related bugs:**
- **#8947** — Fix Anthropic provider to honor timeout_secs config instead of hardcoded 120s  
  URL: https://github.com/zeroclaw-labs/zeroclaw/pull/8947
- **#8935** — Fix Gemini thought signature preservation in tool-call history  
  URL: https://github.com/zeroclaw-labs/zeroclaw/pull/8935
- **#8943** — Fix Bedrock prompt caching to exclude Nova 2 models  
  URL: https://github.com/zeroclaw-labs/zeroclaw/pull/8943

## Feature Requests & Roadmap Signals

**High community demand:**
- **#9022 — Optional Slack Events API (HTTP Request URL) mode for scale-to-zero deploys**  
  URL: https://github.com/zeroclaw-labs/zeroclaw/issues/9022  
  *New today.* Users deploying ZeroClaw at scale want to avoid persistent polling connections. This signals enterprise/cloud deployment interest.

- **#8445 — Telegram multi-message mode (one message per agent turn)**  
  URL: https://github.com/zeroclaw-labs/zeroclaw/issues/8445  
  *Current concatenation of all turns into single message reduces readability for multi-step agent responses.*

- **#7762 — Cron documentation missing; need per-cron model selection**  
  URL: https://github.com/zeroclaw-labs/zeroclaw/issues/7762  
  *Users want cheap models for scheduled tasks. Documentation gaps frustrate setup.*

**Likely next-version candidates:** The memory subsystem features from the five active PRs (#8893, #8895, #8897, #8898, #8900) are strong candidates for v0.8.3 or v0.8.4, as they represent a coordinated push to productionize the memory framework. The SOP milestone (#8288) is also likely to land soon given the active PR pipeline and dedicated tracker.

## User Feedback Summary

**Pain points:**
- Default configuration is broken out-of-the-box (#5808) — new users hit context overflow immediately.
- Slack thread conversations lack memory (#6055) — stateless experience frustrates natural interaction.
- Cron jobs lack documentation and model selection (#7762) — simple scheduled tasks require deep configuration exploration.
- Telegram channel output is unwieldy for multi-step agent turns (#8445).
- SOPs don't work through web dashboard (#8563) — a core feature is unavailable through the primary UI.
- ZeroCode Chat streamed turns look like log/API payloads to small local models (#8999) — degrades experience for local-only users.

**Satisfaction signals:**
- Multiple users (JordanTheJet, Audacity88, Nillth) are actively contributing substantial feature PRs, indicating developer satisfaction and investment.
- The detailed tracker system (#8070–8073, #8360–8363) shows organized project management that users/contributors are engaging with.

## Backlog Watch

**High-priority open issues needing maintainer attention:**

1. **#5808 — Default context budget overflow (priority:p1, 3 months old)**  
   *No fix PR or assignment. This is the single biggest onboarding blocker.*  
   URL: https://github.com/zeroclaw-labs/zeroclaw/issues/5808

2. **#6074 — Audit: track 153 commits lost in bulk revert (priority:p2, ~3 months old)**  
   *Important recovery tracking but no progress since April.*  
   URL: https://github.com/zeroclaw-labs/zeroclaw/issues/6074

3. **#8654 — skill-review fork panic → daemon SIGSEGV (priority:p1, 10 days old)**  
   *Critical stability bug with no fix PR.*  
   URL: https://github.com/zeroclaw-labs/zeroclaw/issues/8654

4. **#8353 — PR: improve error message context (stale-candidate, 17 days old)**  
   *Small fix PR labeled `needs-author-action` and `stale-candidate` — at risk of becoming stale.*  
   URL: https://github.com/zeroclaw-labs/zeroclaw/pull/8353

5. **#8880 — [Not listed but PR #8888 referenced earlier, rechecking]**  
   *No PRs require maintainer attention beyond the normal review queue.*

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*