# OpenClaw Ecosystem Digest 2026-07-12

> Issues: 464 | PRs: 500 | Projects covered: 13 | Generated: 2026-07-12 01:50 UTC

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

Here is the project digest for **OpenClaw** on **2026-07-12**.

---

## OpenClaw Project Digest: 2026-07-12

### 1. Today's Overview
OpenClaw is in a period of **intense, high-velocity development**, with 464 issues and 500 PRs updated in the last 24 hours, reflecting a large and active contributor base. The project is currently processing a new beta release (v2026.7.1-beta.5) while simultaneously addressing a **high-severity P0 regression** where nearly all tool outputs are broken, rendering the core agent loop effectively non-functional for many users. The data suggests a strong focus on stability and session state management, with multiple critical PRs (e.g., #104877, #104681) being pushed to fix memory pressure and heap issues. Despite the high volume of activity, the presence of a critical blocker indicates the project is currently in a **firefighting/stabilization sprint** ahead of a potential stable release.

### 2. Releases
- **New Release:** `v2026.7.1-beta.5` (OpenClaw 2026.7.1-beta.5)
- **Key Feature:** **Conversational Onboarding (Crestodian):** The project has shipped an AI-guided setup wizard that runs across CLI, web, and macOS. It features model-judged approvals bound to exact operations, masked credential prompts, and deterministic fallback when no model is available.
- **Implications:** This significantly lowers the barrier to entry for new users, automating the traditionally complex provider and model configuration process.

### 3. Project Progress
In the last 24 hours, 255 PRs were merged or closed, indicating significant forward momentum.
- **Core Stability (SQLite Migration):** A major effort tracked in Issue #88838, "Track core session/transcript SQLite migration via accessor seam," is now consolidating. The active implementation PR (#96625) flips sessions and transcripts to SQLite storage, a fundamental architecture improvement.
- **MCP Apps (Phase 0):** PR #104742 introduces the first phase of support for Model Context Protocol (MCP) apps, allowing any MCP server to bind a tool to a `ui://` resource via a `_meta.ui.resourceUri`. This is a major extensibility feature for the Control UI.
- **Plugin Hub UI:** PR #104834 merges the Skills, Plugins, and Skill Workshop sections into a single "Plugins" hub in the Control UI, streamlining the user interface.
- **Memory & Performance:**
    - PR #95757 (`fix(memory): respect QMD timeout for memory_search`) fixes a critical bug where memory searches were being aborted prematurely.
    - PR #104877 (`fix: derive heap pressure thresholds from V8 heap limit`) fixes false-positive memory warnings for users with custom V8 heap settings.
    - PR #104864 (`fix(tui): preserve terminal errors across history reloads`) closes a frustrating TUI bug where error messages were lost during a session rebuild.

### 4. Community Hot Topics
The community is most engaged with **session state stability and architectural resilience**.

- **#75** `[Linux/Windows Clawdbot Apps]` **(110 comments, 81 👍):** The most commented-on issue. Users are demanding full parity with the macOS app on Linux and Windows. This is a clear signal for platform expansion, but its status as a long-running enhancement suggests it is a major, ongoing undertaking.
    - [View Issue](https://github.com/openclaw/openclaw/issues/75)
- **#99241** `[Tool outputs sometimes render as image attachments]` **(21 comments):** A high-impact bug where agents cannot read their own tool outputs. The community is feeling the pain of a broken core workflow, as the agent loses context on critical stdout/stderr text.
    - [View Issue](https://github.com/openclaw/openclaw/issues/99241)
- **#10687** `[Fully dynamic model discovery (OpenRouter + beyond)]` **(10 comments, 3 👍):** Users want seamless, up-to-date model lists from fast-moving providers like OpenRouter, highlighting friction with the current static model catalog.
    - [View Issue](https://github.com/openclaw/openclaw/issues/10687)
- **#7707** `[Feature Request: Memory Trust Tagging by Source]` **(17 comments):** The community is increasingly security-conscious, wanting to prevent memory poisoning from untrusted web content or third-party skills.
    - [View Issue](https://github.com/openclaw/openclaw/issues/7707)

### 5. Bugs & Stability
A critical **P0 regression** is currently active, alongside several P1 issues.

- **P0 (Critical):**
    - **Issue #104721** `[> All tool results return "(see attached image)" literal string]` **(11 comments):** This is the highest-severity active issue. It is a regression where the actual data of tool results is being replaced with a placeholder string, making the agent unable to function. This is a **release blocker** for the new beta. **No dedicated fix PR is open yet.**
        - [View Issue](https://github.com/openclaw/openclaw/issues/104721)

- **P1 (High Severity):**
    - **Issue #99241** (see above): "Tool outputs render as image attachments." This appears to be a related or precursor issue to the P0 regression. **No dedicated fix PR is open.**
    - **Issue #102175** `[Embedded prompt cache breaks across room-event boundaries]` **(16 comments):** A regression causing prompt cache misses in long-lived sessions, leading to higher costs and slower responses. **No fix PR is open.**
    - **Issue #91009** `[Codex PreToolUse relay spawns CPU-bound processes]` **(9 comments):** A bug causing high CPU usage and gateway stalls when using Anthropic's Codex. PR #102241 may be related but is still in "needs proof" status.
    - **Issue #103917** `[Gateway crashes on unhandled FsSafeError]` **(6 comments):** A crash loop that can occur when a subagent's workspace is deleted. **No dedicated fix PR is open.**
    - **Issue #103332** (Closed): `[Bug: openclaw can not run with codex/gpt5.6 in pi]` A regression was filed and closed, suggesting a quick fix was merged.

**Summary:** The most critical bug is the tool output regression (#104721), which completely breaks the agent's ability to perceive its own actions.

### 6. Feature Requests & Roadmap Signals
Based on activity and labeling, the following features appear to be high priority:

- **Likely Next Version (v2026.7.x stable):**
    - **MCP Apps (#104742):** The Phase 0 PR is open and being refined. This is a major integration point and strongly positioned for the next release.
    - **Plugins Hub UI (#104834):** A UI consolidation effort that is likely ready for release.
    - **Conversational Onboarding:** Already in the latest beta, this will be the standard for new installs.
    - **SQLite Session Storage:** The massive push to migrate to SQLite for sessions (#88838) is nearing consolidation and will be a core architectural feature of the next update.
- **Longer Term (P2, Awaiting Decision):**
    - **Dynamic Model Discovery (#10687):** A highly requested feature but still awaiting a product decision.
    - **Memory Trust Tagging (#7707):** A key security feature that requires significant design work.
    - **Distributed Agent Runtime (#42026):** Separating control plane and compute is a major architectural goal but still in RFC stage.

### 7. User Feedback Summary
- **Pain Point: Session & Gateway Stability:** Users are experiencing significant pain from session bloat (#55334, #45718), gateway OOMs (#54155, #87109), and memory leaks (#54155). The issue #55334 describes a "death spiral" where a session grows until the gateway is killed.
- **Pain Point: Broken Agent Loop:** The most immediate pain is the "see attached image" regression (#104721, #99241), which makes the agent unresponsive to its own tool outputs. This is damaging user trust in the core functionality.
- **Pain Point: Configuration Friction:** The static model catalog (#10687) and the inability to use batch APIs (#9865) create friction for power users trying to optimize cost and performance.
- **Use Case: Enterprise / Production:** Comments regarding cron reliability, session isolation, and data loss (#84903, #11665) show a user base that is trying to use OpenClaw for production-like scenarios and is hitting systemic limits.
- **Satisfaction:** The high volume of feature requests and engagement (even on critical bugs) suggests a deeply invested user base that sees the project's potential despite current instabilities.

### 8. Backlog Watch
The following are important, older items that appear to be stalled or require maintainer decisions:

- **#75** `[Linux/Windows Clawdbot Apps]`: The most-thumbed-up (81 👍) and commented-on (110) issue. It is a clear demand signal, but progress is slow due to its scope. It is still in "needs-product-decision" and "needs-maintainer-review" status.
    - [View Issue](https://github.com/openclaw/openclaw/issues/75)
- **#42026** `[RFC: Distributed Agent Runtime]`: An architectural RFC that has been open since March 2026 (P2). It requires a product decision to move forward.
    - [View Issue](https://github.com/openclaw/openclaw/issues/42026)
- **#6615** `[Feature: Add denylist support for exec-approvals]`: A security feature with 7 👍 that has been waiting for a maintainer review and product decision since February 2026.
    - [View Issue](https://github.com/openclaw/openclaw/issues/6615)
- **#7722** `[Feature: Filesystem Sandboxing Config]`: Another security feature (4 👍) waiting for a decision. Security-themed features appear to be a consistent backlog theme.
    - [View Issue](https://github.com/openclaw/openclaw/issues/7722)

---

## Cross-Ecosystem Comparison

Here is the cross-project comparison report based on the community digest summaries for 2026-07-12.

---

### Ecosystem Overview

The open-source personal AI assistant ecosystem is marked by a bifurcation between intense, high-velocity stabilization efforts and quiet maintenance periods. While flagship projects like OpenClaw and Hermes Agent are deeply engaged in firefighting critical regressions stemming from architectural migrations (e.g., SQLite session storage, Reborn runtime), the ecosystem shows strong community demand for platform expansion, enhanced security governance, and provider flexibility. Projects in quieter phases (e.g., Moltis, LobsterAI) reveal a potential depth of feature backlog that could accelerate upon maintainer attention. A common thread across the most active projects is a struggle to balance innovation with stability, resulting in significant user pain from regressions and configuration friction.

### Activity Comparison

| Project | Issues Updated (24h) | PRs Updated (24h) | Release Status (24h) | Health Signal |
| :--- | :--- | :--- | :--- | :--- |
| **OpenClaw** | 464 | 500 | Beta (v2026.7.1-beta.5) | **Firefighting** — High velocity, but critical P0 regression blocks core function. |
| **NanoBot** | 22 | 26 | None | **Active Hardening** — Addressing a major security audit (42 findings). |
| **Hermes Agent** | 50 | 50 | None | **Regression Squashing** — High churn on stability bugs and platform regressions. |
| **IronClaw** | 7 | 50 | None (Release PR open for 9 days) | **Architecture Transition** — Dominated by Reborn runtime rework. |
| **CoPaw** | 23 | 5 | v2.0.0 (source of crisis) | **Crisis Mode** — v2.0.0 introduced critical regressions, no hotfix in sight. |
| **ZeroClaw** | 50 | 50 | None | **Balanced Growth** — High activity with major feature (goal-mode) and P1 bugs. |
| **PicoClaw** | 0 | 3 | None | **Stable Maintenance** — Low activity, single functional improvement merged. |
| **NullClaw** | 2 | 0 | None | **Calm** — Low activity, two items in discussion. |
| **NanoClaw** | 2 | 8 | None | **Active Refinement** — Focused on guard seam and scheduled tasks. |
| **TinyClaw** | 0 | 0 | None | **Inactive** |
| **ZeptoClaw** | 0 | 0 | None | **Inactive** |
| **LobsterAI** | 3 (stale) | 1 (stale) | None | **Stalled** — All items stale for 100+ days. |
| **Moltis** | 0 | 1 | None | **Dormant** — Single PR open for a fix, no community engagement. |

### OpenClaw's Position

OpenClaw maintains its position as the ecosystem's most dominant and ambitious core reference implementation by a significant margin, evidenced by 464 issues and 500 PRs updated in 24 hours—an order of magnitude more than its nearest peers (ZeroClaw, Hermes Agent). Its advantages include a **massive contributor base**, a **rapid release cadence** (beta on day 0 of a new release cycle), and ambitious features like **SQLite session migration**, **MCP Apps support**, and **Conversational Onboarding** that set a high bar for user experience. Technically, OpenClaw is tackling the most complex architectural challenges (e.g., distributed agent runtime, session state management) while simultaneously shipping consumer-facing features like the Plugin Hub UI. Its primary weakness, mirroring the ecosystem trend, is a struggle to maintain stability at its velocity, as highlighted by the P0 regression (#104721) where the agent cannot read its own tool outputs—a complete breakdown of the core agent loop. No other project demonstrates a comparable combination of scale, feature breadth, and community size.

### Shared Technical Focus Areas

Several requirements are emerging simultaneously across multiple projects, indicating ecosystem-wide pain points.

- **Memory & Session State Management:** **OpenClaw** (SQLite migration, heap pressure thresholds), **NanoBot** (prompt cache stability, unbounded queues), **Hermes Agent** (context compaction fabricating data, MCP process leaks), **ZeroClaw** (MCP/tool-schema cloning causing unbounded RSS growth), and **NullClaw** (Telegram channel timeout) are all wrestling with how to manage agent memory and long-lived sessions. The community's need for stable, efficient, and non-corrupting session management is the single most prominent technical theme.
- **Provider & Model Flexibility:** **OpenClaw** (dynamic model discovery), **Hermes Agent** (custom provider UI), **NullClaw** (Grok CLI provider), and **CoPaw** (OAuth support) all signal that users want to easily add, configure, and switch between a wide variety of AI providers and models. The "static model catalog" is a friction point across the ecosystem.
- **Security Governance & Sandboxing:** The **NanoBot** audit (42 findings) and **ZeroClaw** P1 bug (skill-review fork SIGSEGV) are the most extreme examples, but **OpenClaw** (exec-approval denylist, filesystem sandboxing config), **Hermes Agent** (Tirith security bypass), and **IronClaw** (no private security reporting channel) also show a growing user demand for robust, configurable security controls.
- **Cross-Platform Parity:** **OpenClaw** (Linux/Windows Clawdbot Apps), **Hermes Agent** (Windows memory leaks), and **IronClaw** (Windows `local-dev-yolo` broken) indicate that users are demanding and being blocked on full-featured support for non-macOS/Linux platforms, particularly Windows.
- **CI/CD & Build Reliability:** Both **IronClaw** (flaky test poller, staging-release promotion) and **NanoClaw** (Windows build failure with VS 2026) highlight that development infrastructure itself is a source of friction for contributors.

### Differentiation Analysis

While many projects share an overarching goal of creating autonomous agents, their strategic focus and target users diverge significantly.

| Dimension | **OpenClaw** | **NanoBot / NanoClaw** | **Hermes Agent** | **IronClaw** | **CoPaw / ZeroClaw** |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Target User** | Power users, integrators, large-scale deployments | Self-hosters, local LLM enthusiasts, security-conscious | Enterprise, multi-platform teams (Telegram, Feishu, Slack) | Cloud-first, attestation-secure, Reborn-runtime adopters | Chinese-speaking ecosystem, multi-agent channels, lightweight |
| **Architecture** | Monolithic but modular; micro-Window manager | Lightweight plugin/extension model | Multi-platform gateway services (Telegram, Slack, Feishu) | Reborn runtime (cloud-native, secret-scoped) | Agent-loop over external models; channel-first |
| **Feature Focus** | Agent runtime correctness, session state, UI/UX | Prompt caching, security hardening, MCP reliability | Platform integration, data migrations, agent guidance | Extension runtime, queued messages, E2E testing | Agent loops, tool permissions, memory management |

For example, **IronClaw** is uniquely differentiated by its cloud-native, attestation-verified compute model, a stark contrast to **NanoBot**’s focus on local LLM and Ollama caching. **Hermes Agent** distinguishes itself via its breadth of messaging platform support (Telegram, Feishu, Slack), which is unmatched by the single-platform focus of a project like **NullClaw** (Telegram-centric).

### Community Momentum & Maturity

The projects fall into distinct tiers based on activity and stage of development.

- **Tier 1: Rapidly Iterating / Feature-Incubating**
    - **OpenClaw** (Extreme velocity, firefighting regressions)
    - **ZeroClaw** (High velocity, balanced between feature work and bug fixes)
    - **IronClaw** (High velocity, focused on a major architectural transition)
    - **NanoBot** (Active hardening from a security audit)
- **Tier 2: Stabilizing / Refining**
    - **Hermes Agent** (High churn but focused on squashing regressions)
    - **NanoClaw** (Measured progress on guard seam and scheduled tasks)
    - **CoPaw** (In crisis, forced to stabilize a broken v2.0.0)
- **Tier 3: Low Activity / Dormant**
    - **PicoClaw**, **NullClaw** (Stable maintenance with low volume)
    - **Moltis**, **LobsterAI**, **TinyClaw**, **ZeptoClaw** (Negligible or zero recent activity)

A clear pattern emerges: the most ambitious projects (OpenClaw, ZeroClaw, IronClaw) are paying a "complexity tax" in the form of critical bugs and regressions, while less active projects may be stable but are not innovating. **CoPaw** is the most dramatic example of this, where a major version release has backfired into a crisis.

### Trend Signals

Extracting high-level industry trends from the aggregate community feedback:

1.  **"Agent Loop Stability" is the New Frontier:** The most critical user pain points are no longer about model quality but about the agent's *own infrastructure*—its ability to not crash (SIGSEGV in ZeroClaw), not corrupt its own memory (Hermes Agent), not get stuck in loops (CoPaw), and not misinterpret its own tool outputs (OpenClaw). The community is pushing the frontier from "can the AI think" to "can the agent runtime survive thinking."
2.  **The "Secure-by-Default" Threshold Approaches:** The NanoBot security audit is a watershed moment. It signals that the ecosystem is reaching an inflection point where foundational architectural choices (e.g., `os.environ` for API keys, no rate limiting, no private vulnerability reporting) are no longer acceptable. Projects that lag on this will lose trust.
3.  **Local LLM Viability Hinges on Prompt Cache Engineering:** The intense discussion in NanoBot (#2463) about prompt prefix preservation for Ollama caching reveals a critical bottleneck for self-hosted agents. The entire cost and speed argument for local models depends on efficiently reusing KV caches. This is not an AI problem; it is a **data serialization and architecture problem**.
4.  **Configuration Friction is a Barrier to Adoption:** Across OpenClaw, IronClaw, and ZeroClaw, users are reporting friction with static model catalogs, broken config templates, and complicated setup for local MCP servers. The successful next generation of agent platforms will prioritize "zero-touch" setup and seamless provider discovery as a core feature, not an afterthought.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

# NanoBot Project Digest — July 12, 2026

## 1. Today's Overview

NanoBot is in an **active development and security hardening phase**, with 22 issues and 26 pull requests updated in the last 24 hours. The project is experiencing sustained high community engagement, driven primarily by a major security audit (42 findings documented in #4815) and ongoing performance/architectural debates around prompt caching and provider compatibility. Three existing issues were closed, but 19 remain open/active. No new releases were published. The maintainer team appears responsive, with several fix PRs already in flight for recently reported vulnerabilities.

## 2. Releases

**No new releases.** The last published release predates the data window. Users are advised to track the `main` branch for the latest fixes, as several critical security patches are awaiting merge.

## 3. Project Progress

**Six PRs were merged/closed in the last 24 hours:**
- **#4891** (closed) — *refactor(agent): make runtime context opt-in and prefix-stable* — A significant architectural improvement that stops injecting volatile metadata into every prompt, enabling cache stability. Depends on #4844.
- **#4844** (closed) — *refactor(agent): gate sustained goals behind explicit /goal* — Replaced the old `long_task`/`complete_goal` contract with explicit `create_goal`/`update_goal` tools. Removes the controversial automatic turn-continuation feature.
- **#4764** (closed) — *fix(mcp): isolate reconnect cancel scopes to prevent gateway crash* — Fixes a crash (related to #4302) when MCP streamable-http servers timeout.
- **#4860** (closed) — Bug fix for missing `onboard`/`webui` commands for uv-installed users.
- **#4302** (closed) — Bug fix for gateway crash after MCP reconnect.
- **#4872** (closed) — Enhancement: Dream now only commits if changes are productive.

**Key feature advances in open PRs:** Model-preset-to-session binding (#4866), guided WebUI setup flows (#4855), and MCP tool provider lifecycle extraction (#4875).

## 4. Community Hot Topics

| Issue | Title | Comments | Link |
|-------|-------|----------|------|
| #2463 | Architectural: prompt prefix preservation | 14 comments | [View](https://github.com/HKUDS/nanobot/issues/2463) |
| #4867 | Preserve exact prompt prefix for Ollama caching | 4 comments | [View](https://github.com/HKUDS/nanobot/issues/4867) |
| #4860 | Missing `onboard`/`webui` commands | 3 comments | [View](https://github.com/HKUDS/nanobot/issues/4860) |

**Analysis:** The #2463 ↔ #4867 conversation is the most significant community thread. Users are reporting that NanoBot's conversation history reconstruction is not byte-identical to what was sent to the model, **adding 60+ seconds per turn** with Ollama due to cache misses. This is a fundamental architectural tension between NanoBot's current history serialization and efficient local LLM inference. The depth of discussion (14 comments over 4 months on #2463) indicates this is a **top-tier performance blocker** for self-hosted users. PR #4891 (prefix-stable context) is a direct response to this pain point.

## 5. Bugs & Stability

| Severity | Issue | Description | Fix PR? |
|----------|-------|-------------|---------|
| **🔴 Critical** | #4785 | `read_file` loads entire file before truncation — multi-GB files cause OOM crash | No |
| **🔴 Critical** | #4784 | Provider API keys leaked between providers via global `os.environ` mutation | No |
| **🔴 Critical** | #4783 | CLI subprocesses inherit full `os.environ` — API keys leaked to installed apps | No |
| **🔴 Critical** | #4782 | `/v1/chat/completions` has zero rate limiting — credit exhaustion vector | No |
| **🔴 Critical** | #4781 | No WebSocket connection limit — trivial FD exhaustion DoS | No |
| **🔴 Critical** | #4780 | Unbounded `asyncio.Queue` in MessageBus — memory exhaustion | No |
| **🔴 Critical** | #4779 | `process_direct()` bypasses all channel authorization (6+ callers) | No |
| **🔴 Critical** | #4777 | `/stop` command cancels other users' tasks in group chats | #4889 (open) |
| **🔴 Critical** | #4778 | `system` channel messages bypass all authorization checks | No |
| **🟠 High** | #4886 | Docker Compose disables AppArmor and seccomp | No |
| **🟠 High** | #4885 | CLI app registry is an unsigned code-install supply chain | No |
| **🟠 High** | #4884 | WebFetch sends complete user URLs to Jina | No |
| **🟠 High** | #4883 | API session lock map grows without bounds | **#4890 (open)** |
| **🟠 High** | #4882 | Dream content diff reports empty files as modified | No |
| **🟠 High** | #4881 | Windows ExecTool corrupts PowerShell UTF-16 output | No |
| **🟠 High** | #4887 | Test setup fails: missing `lark-oapi` dependency | No |

**Note:** The "42 Findings" audit (#4815) represents a **comprehensive security review** by a single contributor (hamb1y). The maintainer team has already merged/closed some related items and has open fix PRs (#4889, #4890, #4880, #4888) addressing a subset. The remaining findings are 6+ days old with no maintainer response — this backlog warrants urgent attention.

## 6. Feature Requests & Roadmap Signals

**Likely in next release:**
- **Prefix-stable system prompt** (PR #4891, PR #4371) — Directly addresses the critical Ollama caching issue (#4867). Expected to land soon given its priority and merged dependencies.
- **Model preset binding to sessions** (PR #4866) — Lets users `/model` switch without leaking state between conversations. High user value for multi-model workflows.
- **Sustained goal gating** (PR #4844, PR #4879) — Replaces the controversial auto-continuation with explicit user opt-in. Multiple PRs compete here; the maintainer's merged PR #4844 suggests this direction.

**Longer-term signals:**
- **MCP tool provider lifecycle** (PR #4875) — Architectural cleanup for better MCP reliability.
- **Guided WebUI setup** (PR #4855) — Improves onboarding for less technical users.
- **API rate limiting / connection limits** — No PRs exist yet, but the audit (#4782, #4781) will likely drive these.

## 7. User Feedback Summary

**Pain points expressed:**
1. **Ollama unusability** (#4867): "totally unusable with Ollama and 32 GB of VRAM" — 60-second overhead per turn for cache misses is the #1 user complaint.
2. **Onboarding friction** (#4860): New uv-installed users cannot find `onboard` or `webui` commands. This indicates either documentation mismatch or packaging regression.
3. **Empty Dream commits** (#4872): Users frustrated by git log pollution from unproductive Dream runs. Now fixed (closed).
4. **MCP reliability** (#4302, #4764): Gateway crashes after MCP reconnect are disruptive for users running custom MCP servers.

**Satisfaction signals:** The community is actively contributing fixes — 6 PRs were merged/closed today alone, suggesting healthy contributor trust and maintainer responsiveness.

## 8. Backlog Watch

| Issue | Age | Description | Needs Attention? |
|-------|-----|-------------|------------------|
| #2463 | 109 days | Prompt prefix preservation (architectural) | **Yes** — This is the root cause of the Ollama caching crisis. PR #4891 addresses symptoms but not the core serialization issue. |
| #4021 | 46 days | Codex duplicate reasoning items fix (AI-assisted) | **Yes** — Long-open, conflict-labeled. Affects OpenAI Responses API users. |
| #4145 | 41 days | Weather Skill contribution | **Yes** — Conflict-labeled, no recent activity. Blocks community contribution. |
| #4371 | 26 days | Add breakpoint before Recent History for cache stability | **Yes** — Directly addresses the Ollama caching problem but is conflict-labeled and not yet merged. |
| #4650 | 10 days | Extract turn history recovery | **Moderate** — Refactor with conflicts. No negative impact if delayed. |

**Most critical backlog item:** **#2463** is the oldest open issue and the root cause of the most painful user complaint (Ollama performance). The maintainer should prioritize a resolution that ensures NanoBot's stored conversation history is byte-identical to the prompt prefix that was sent, enabling server-side KV cache hits.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

Here is the project digest for **Hermes Agent** on **2026-07-12**.

**Date:** 2026-07-12
**Project:** Hermes Agent (github.com/nousresearch/hermes-agent)

---

### 1. Today's Overview

Hermes Agent is in a period of extremely high activity, with 50 open issues and 50 open pull requests updated in the last 24 hours. The project is heavily focused on squashing regressions and stabilizing the platform across multiple messaging platforms and desktop environments. A significant volume of work is dedicated to fixing bugs introduced in recent releases, particularly concerning session management, message delivery, and configuration migrations. Despite the high churn, no new releases were cut today, indicating the maintainers are likely consolidating changes before a stable point release.

### 2. Releases

**None.** No new releases were published in the last 24 hours.

### 3. Project Progress (Closed PRs)

There were **0 merged/closed PRs** in the last 24 hours. However, the 50 open PRs indicate active work is pending review. Key areas of progress visible in open PRs include:
- **Gateway & Session Stability:** PR #61092 aims to fix auto-resets ignoring the `session_reset.mode` policy.
- **Desktop & Windows Support:** PR #61291 includes `pywin32` paths for Windows backend reliability.
- **Dashboard Fixes:** PR #61045 fixes a PTY reattach bug that linked different chat sessions to the same terminal process.
- **Platform-Specific Fixes:** PRs are open for Telegram (large file uploads, PR #62941), Feishu (WebSocket reconnection, PR #61271), and Slack (thread context reading, PR #61261).

### 4. Community Hot Topics

The following issues and PRs generated the most discussion and reactions, revealing core community concerns:

- **🔥 Skills Index Degradation (#38240):** The most discussed issue (21 comments). An automated probe found the Skills Hub index is stale. This is a critical infrastructure concern for users relying on the agent's skill library.
    - *Link:* [NousResearch/hermes-agent Issue #38240](https://github.com/NousResearch/hermes-agent/issues/38240)
- **Security Bypass in Tirith (#35357):** A high-impact discussion (6 comments) about the human-in-the-loop approval system only covering shell commands, leaving tools like `write_file` and `send_message` unguarded.
    - *Link:* [NousResearch/hermes-agent Issue #35357](https://github.com/NousResearch/hermes-agent/issues/35357)
- **Agent Has No Internal Clock (#62904):** Users report the agent repeatedly fails to check the system date, leading to incorrect time-relative statements despite multiple attempted fixes.
    - *Link:* [NousResearch/hermes-agent Issue #62904](https://github.com/NousResearch/hermes-agent/issues/62904)
- **Microsoft SkillOpt Integration (#32925):** A feature request that received 11 upvotes, indicating strong community interest in self-evolving agent skills.
    - *Link:* [NousResearch/hermes-agent Issue #32925](https://github.com/NousResearch/hermes-agent/issues/32925)

### 5. Bugs & Stability

Today's report shows a high volume of stability issues, with many centered on regressions from recent updates.

**P1 (Critical):**
- **Context Compaction Fabricates Data (#62365):** The agent's context compression is inventing user requests that never happened, corrupting conversation history. **(Open)**
    - *Link:* [NousResearch/hermes-agent Issue #62365](https://github.com/NousResearch/hermes-agent/issues/62365)
- **Desktop Bracketed-Paste Corruption (#62557):** Electron desktop app leaks terminal control sequences into persisted user messages, duplicating content. **(Open)**
    - *Link:* [NousResearch/hermes-agent Issue #62557](https://github.com/NousResearch/hermes-agent/issues/62557)
- **Config Migration Data Loss (#62723):** Upgrading silently wipes `platforms.feishu` config from 9 out of 10 profiles. **(Open)**
    - *Link:* [NousResearch/hermes-agent Issue #62723](https://github.com/NousResearch/hermes-agent/issues/62723)

**P2 (High):**
- **MCP Process Leaks (#60385):** MCP server processes are not killed on reconnect, leading to resource exhaustion. **(Closed/Fixed)**
    - *Link:* [NousResearch/hermes-agent Issue #60385](https://github.com/NousResearch/hermes-agent/issues/60385)
- **Telegram Uploads Fail (#62936):** Files >~15MB always time out due to an unset `media_write_timeout` parameter. **(Open)** *A fix PR exists: #62941.*
- **Windows Memory Leak (#53995):** Gateway pymalloc memory leak causes hard crashes and session stalls on Windows. **(Open)**
- **API Call Crash (#62914):** `_emit_pending_fallback_notice()` raises `AttributeError` on fallback success path, crashing the entire API call. **(Open)**

### 6. Feature Requests & Roadmap Signals

User-requested features point toward a desire for more customization and provider flexibility.

- **Priority Signal:** The **Tirith security gate bypass (#35357)** and **Config data loss (#62723)** are likely to be fast-tracked for a hotfix release.
- **Likely for Next Version:**
    - **Custom OpenAI-compatible Provider UI (#38975):** Desktop UI for adding custom providers easily.
    - **Pricing Overrides & Contract Pricing (#9403):** Ability to maintain custom pricing catalogs for enterprise use.
    - **Native OpenCode Go Provider (#62916):** Adding support for a popular code-focused model directly into the GUI.
    - **Always-preload Skills (#62927):** A config option to inject skill bodies into every session without needing the agent to call `skill_view()`.

### 7. User Feedback Summary

- **Pain Points:** The dominant theme is **regression fatigue**. Users are frustrated by data loss during upgrades (#62723), session corruption (#62557), and the core agent making up false user requests (#62365). The recurring "no internal clock" bug (#62904) suggests a critical AI reasoning flaw that is not yet resolved.
- **Security Concerns:** The Tirith approval gate bypass (#35357) is a major trust and security concern for users deploying the agent in sensitive environments.
- **Usability:** Users are asking for more intuitive configuration, particularly around custom providers (#38975) and the desktop UI (#38975, #62916).
- **Platform Stability:** Windows users are suffering disproportionately from memory leaks (#53995) and desktop freezes (#62884).

### 8. Backlog Watch

The following issues and PRs require attention from maintainers:

- **Skills Index Degradation (#38240):** Open for over a month with 21 comments. A core feature (the Skills Hub) is confirmed degraded, and the fix requires maintainer action on CI/CD workflows.
- **Feishu Data Loss (#62723):** A P1 bug that causes permanent config loss for Feishu users. Despite being opened yesterday, it is a critical regression that will block many users from updating.
- **Matrix Gateway Blocked (#62401):** Open for two days. Matrix users on macOS are blocked because of an unnecessary dependency build failure. No maintainer response is visible.
- **Vision MCP Documentation Gap (#62675):** A user is requesting the `Context7` MCP server be added to the official catalog. This is a low-effort documentation/configuration fix that would significantly improve the user experience for vision-based workflows.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

# PicoClaw Project Digest — 2026-07-12

## Today's Overview
The PicoClaw project shows moderate activity driven primarily by pull request work, with three PRs updated in the last 24 hours (one merged/closed, two open). No new releases or new issues were recorded in this period, indicating a stable maintenance phase rather than a burst of new feature development. The merged PR (#3249) represents a meaningful enhancement to the skill management system, while the two open PRs address agent runtime configurability and DeltaChat cleanup. Project health appears solid, with active community contributions progressing through the review pipeline.

## Releases
**No new releases.** The latest release remains unchanged; no version bumps or tag updates were detected in the last 24 hours.

## Project Progress
The following pull request was merged/closed in the last 24 hours:

- **#3249 — Skill enable/disable state + cron RunNow** *(merged)*  
  *Author: m4n3z40* | [View PR](https://github.com/sipeed/picoclaw/pull/3249)  
  Implements a per-skill disabled state stored in `workspace/skills/.skills-state.json` within each skill root, enabling UI toggle for skills and cron pause/resume. Designed to leverage recursive mtime-tracking so disabled skills disappear from `<skills>` on the next turn without requiring a restart. This feature advances the project toward more dynamic skill management directly from the interface.

## Community Hot Topics
While no issues or PRs generated heavy comment/reaction activity in this period, the following items represent the most notable community-drive discussions:

- **#3225 — Support agent-specific runtime overrides** (open, 7 days stale)  
  *Author: xdatafactor* | [View PR](https://github.com/sipeed/picoclaw/pull/3225)  
  Proposes allowing `agents.list` entries to define per-agent overrides for `max_tokens`, summarization thresholds, and `split_on_marker`. The underlying need is clear: users want fine-grained control over agent behavior without global configuration changes. Staleness tag suggests the maintainers may need to provide review feedback to keep this moving.

- **#3222 — refactor(deltachat): cleanup implementation, documentation -200LOC** (open)  
  *Author: trufae* | [View PR](https://github.com/sipeed/picoclaw/pull/3222)  
  Large-scale cleanup of DeltaChat integration, removing legacy features, hardcoded relay lists, and password-based email config in favor of jsonrpc secrets. The -200LOC footprint signals a positive maintenance direction — reducing complexity and surface area for bugs.

## Bugs & Stability
**No new bugs, crashes, or regressions were reported in the last 24 hours.**  
The project remains stable with no incoming bug reports. The DeltaChat refactor PR (#3222) proactively eliminates legacy fallback code that could have been a source of future instability.

## Feature Requests & Roadmap Signals
The following user-requested features are visible from active PRs:

- **Agent-specific runtime overrides** (#3225) — Per-agent `max_tokens`, summarization thresholds, and split markers. This is likely to land in the next minor release if maintainers provide timely review feedback.
- **Skill enable/disable UI toggles** (#3249, already merged) — This feature is now part of the codebase and can be expected in the next release.

**Prediction:** The next version will ship the skill toggle UI functionality (#3249), and if #3225 receives maintainer attention soon, agent-specific overrides may also be included.

## User Feedback Summary
No direct user feedback (comments, reactions) was captured in this 24-hour window. However, the nature of the active PRs suggests:

- **Pain point:** Users want to disable skills without restarting the agent — now addressed by #3249.
- **Use case:** Advanced users managing multiple agents require per-agent configuration rather than global defaults — driving #3225.
- **Satisfaction indicator:** The quick merge of #3249 (created and merged within the same day) suggests responsive maintainers and healthy contributor-maintainer alignment.

## Backlog Watch
The following item requires maintainer attention to avoid stalling:

- **#3225 — Support agent-specific runtime overrides** ([View PR](https://github.com/sipeed/picoclaw/pull/3225))  
  Open for 8 days as of this digest, now marked `[stale]`. This is a well-structured feature PR with clear tests and a focused scope. If left unaddressed, it risks bit-rotting against the main branch. Tagging for review should be a priority to preserve contributor momentum.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

# NanoClaw Project Digest — 2026-07-12

## 1. Today's Overview
Project activity remains **elevated** with 8 PRs updated in the last 24 hours, including 2 closed and 6 still open. The core team is actively working on two major architectural initiatives: the **guard seam** (centralized decision function for privileged actions, PR #2986) and the **scheduled-tasks train** (one-door delivery via PR #2988). Two new open issues were filed yesterday, one a Windows build regression (VS 2026 + better-sqlite3) and one a false-positive rate-limit logging spam. No new releases were cut. Overall project health is **good**, with steady forward progress on structural improvements and prompt attention to regressions.

## 2. Releases
No new releases were created in the last 24 hours.

## 3. Project Progress
Two PRs were merged or closed today:

- **#3018 — RFC: temporal (incognito) sessions** *(closed, not merged)* — A design RFC for throwaway, memory-free DM sessions. Closed per `CONTRIBUTING.md` as source-code features on `main` are not accepted; the design direction is noted for future skill-based implementation.
- **#3015 — fix: preserve phase context in live progress** *(merged)* — Fixes a real E2E issue where Claude’s first tool event could arrive before the phase description, causing an orphaned "completed reading" card. Also handles tool_result summaries being consumed by long warnings. Includes new regression tests for realistic timing and long warnings. **67 files / 1,267 tests PASS.**

## 4. Community Hot Topics
- **#3018 — RFC: temporal (incognito) sessions** — A vision proposal for throwaway DM sessions with no memory persistence. The author explicitly opened this as an RFC, not a mergeable feature. The discussion (0 comments so far) may shape a future skill. *[Link](https://github.com/nanocoai/nanoclaw/pull/3018)*
- **#3019 — fix(agent-runner): stall watchdog to recover from hung in-flight tools** — Addresses a production incident where a busy agent group experienced 30-minute SDK-activity gaps (heartbeat age ~1,800,000 ms) causing container kills. The fix introduces a watchdog that detects genuinely hung tool calls and recovers the container. This is the most operationally urgent PR open. *[Link](https://github.com/nanocoai/nanoclaw/pull/3019)*

## 5. Bugs & Stability

| Severity | Issue | Summary | Fix PR? |
|----------|-------|---------|---------|
| **High** | #3017 — Windows: VS 2026 + better-sqlite3 v11.10.0 compilation fails | Node.js native addon compilation fails under Visual Studio 2026 June Feature Update 18.7.3. Unknown if caused by VS 2026 toolchain changes or better-sqlite3 incompatibility. 0 comments. | None yet |
| **Medium** | #3016 — Every rate_limit_event logged as quota error even when "allowed" | Since PR #2965, agent-runner logs false "Rate limit (retryable: false, quota)" errors on every turn that completes normally. User logged 82 instances in one week. 0 comments. | None yet |
| **Medium** | #3020 — fix: rescue undelivered unwrapped replies after re-wrap nudge | When the model omits the `<message to>` wrapper (common after long tool chains), replies are silently dropped. This PR rescues them and suppresses recaps. Fixes #2369, #2393, #2404. | Open PR #3020 |
| **High** | #3019 — Stall watchdog for hung in-flight tools | Production incident: 30-minute zero SDK activity gaps kill containers. PR adds watchdog to detect truly hung tools. | Open PR #3019 |

## 6. Feature Requests & Roadmap Signals

### Likely for Next Minor Release:
- **Provider-agnostic persistent memory** (PR #3012) — A new `memory/` tree shared across agent providers, loaded on new contexts, cleared after compaction. This is a core-team feature and appears close to merging.
- **Scheduled tasks — one-door delivery** (PR #2988, part 3/5) — Forces all delivery through a named `to` destination; task sessions have exactly one delivery path. Follows two already-merged PRs in the train.

### Longer-Term Signals:
- **Temporal (incognito) sessions** (PR #3018, RFC) — Throwaway, memory-free DM sessions. Not mergeable as-is, but may become a skill. Community sentiment is not yet visible (0 comments).
- **Guard seam (phase 2)** (PR #2986) — Centralizes all privileged action decisions into a single `guard()` function with allow/hold/deny outcomes. This is a major architecture change likely spanning multiple releases.

## 7. User Feedback Summary
- **False positive rate-limit logging** (Issue #3016): A real user reports that the agent-runner floods logs with error messages that are not actually errors. 82 false alarms in one week causes log noise and undermines trust in monitoring.
- **Silent reply drops** (PR #3020): When the model omits the standard message wrapper (common after long tool chains), replies are silently lost. The fix is in open PR #3020.
- **Windows build pain** (Issue #3017): Windows developers face a hard block — VS 2026 + better-sqlite3 v11.10.0 fails to compile. No workaround known yet. This affects a platform that already requires extra setup.

## 8. Backlog Watch
No long-unanswered issues or PRs were identified in the last 24 hours. All open items are recent (created within 1–3 days) and receiving attention. The two open bugs (#3016, #3017) have zero comments from maintainers — they would benefit from an initial triage response to set user expectations.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

# NullClaw Project Digest — 2026-07-12

## Today's Overview
NullClaw showed low activity in the past 24 hours, with **2 open issues updated** and **0 pull requests or releases**. No new code was merged. The project appears to be in a calm maintenance phase, with no critical regressions or incoming feature work from contributors. The two active discussions focus on a Telegram channel timeout bug and a new provider request for Grok CLI, indicating ongoing community interest in expanding provider support and improving production reliability.

## Releases
*No new releases were published today. The last known release remains unchanged.*

## Project Progress
- **Pull Requests merged/closed today:** 0  
  No PR activity was recorded. No features, fixes, or documentation changes advanced through the review pipeline.

## Community Hot Topics
1. **Issue #972 — [bug] Telegram channel stops responding after idle time**  
   - Author: `i11010520` | Created: 2026-06-30 | Updated: 2026-07-11 | Comments: 3  
   - Summary: After a night of idle time, the Telegram channel stops responding to messages, while the `nullclaw` backend continues to function normally (e.g., `nullclaw agent -m "ping"` works). The user provided backend logs showing the agent is alive, suggesting the disconnect is specific to the Telegram integration layer.  
   - Link: [Issue #972](https://github.com/nullclaw/nullclaw/issues/972)  
   - *Underlying need:* Users expect the Telegram connector to maintain persistent, long-lived sessions without manual reconnection. The issue points to a potential heartbeat, timeout, or reconnection logic gap in the Telegram provider.

2. **Issue #975 — Add grok-cli provider (run Grok via the grok CLI's login session, unmetered)**  
   - Author: `yanggf8` | Created: 2026-07-11 | Updated: 2026-07-11 | Comments: 1  
   - Summary: Feature request to add a `grok-cli` provider that reuses the existing subprocess pattern (`claude-cli`, `codex-cli`, `gemini-cli`) to run Grok through its local CLI, leveraging a paid grok.com subscription. The author notes the code location `src/provider_probe.zig:43`.  
   - Link: [Issue #975](https://github.com/nullclaw/nullclaw/issues/975)  
   - *Underlying need:* Users want to extend NullClaw's model provider ecosystem with Grok, following the established pattern, to enable unmetered usage from existing subscriptions.

## Bugs & Stability
| Severity | Issue | Description | Status | Fix PR Exists? |
|----------|-------|-------------|--------|----------------|
| **High** | #972 | Telegram channel silent after idle period, backend healthy. Likely a connectivity/liveness issue in the Telegram adapter. | Open (updated yesterday) | No |
| **Low** | None | No other bugs reported in the last 24h. | — | — |

**Analysis:** The Telegram issue is the most notable bug. It impacts real-world usability for users relying on 24/7 Telegram-based agents. Without a fix PR or maintainer response, this may become a growing frustration for users deploying NullClaw in production-like settings.

## Feature Requests & Roadmap Signals
- **#975 — grok-cli provider:** A clear, implementable feature request. Since NullClaw already supports multiple CLI-based providers, adding Grok via the same subprocess pattern is low-hanging fruit. **Prediction:** Could land in the next minor release if a maintainer or contributor steps up to implement it.
- No other feature requests were active today.

## User Feedback Summary
- **Pain point:** Telegram connector reliability during idle periods is a concrete operational frustration (Issue #972). Users expect chat integrations to remain active unattended.
- **Use case demand:** Extending model provider support to Grok (Issue #975) shows ongoing user interest in adding more subscription-based CLI tools, reflecting a desire for variety and cost control.
- **Satisfaction:** No positive user feedback or confirmations of resolutions were recorded in the last day. The lack of maintainer comments on either issue may indicate bandwidth constraints.

## Backlog Watch
- **Issue #972** — Created June 30, last updated July 11, 3 comments. Maintainer has not yet triaged or commented. This is the highest-importance item needing attention, as it affects a core integration (Telegram) and has been open for nearly two weeks with no official response.
- **No other long-unanswered items** were detected in the current data set.

*End of digest for 2026-07-12. Data sourced from nullclaw/nullclaw GitHub project.*

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

# IronClaw Project Digest — 2026-07-12

## Today's Overview

Project activity is **elevated**, with 50 PRs updated in the last 24 hours (14 merged/closed) and 7 open issues. The Reborn runtime continues to dominate development effort, with four major PR trains in progress covering extension-runtime support, queued-message steering, recoverable error hardening, and Responses API coverage. A notable cluster of three Windows-compatibility and local-development issues (#5999, #5998, #6000) suggests growing user adoption on non-Linux platforms is exposing portability gaps. CI infrastructure saw significant investment, including a new staging-release promotion workflow (#5639) and flaky-test remediation (#6005). No new releases were published.

## Releases

No new releases were published in the last 24 hours. The last release train (#5598) remains open, proposing bumps for `ironclaw_common` (0.4.2 → 0.5.0, breaking), `ironclaw_skills` (0.3.0 → 0.4.0, breaking), and `ironclaw` (0.24.0 → 0.29.1). No migration notes are available yet.

## Project Progress

**14 PRs were merged or closed** in the last 24 hours. Notable merges include:

- **[#6003] ci: route workflows to canceled runner** — [PR](https://github.com/nearai/ironclaw/pull/6003) (closed, accidental PR, maintainers asked to delete)
- **[#5997] test(e2e): address Emulate fixture review** — [PR](https://github.com/nearai/ironclaw/pull/5997) (merged, addresses Gemini/CodeRabbit review feedback on fixture handling)
- **[#5951] fix(llm): recover near.ai streaming tool-call args with trailing content** — [PR](https://github.com/nearai/ironclaw/pull/5951) (merged, fixes reasoning models like DeepSeek-V4-Flash getting empty tool-call arguments)

**Key feature advances in open PRs:**
- **Extension runtime train (PRs 2–3 of 8):** [#5995](https://github.com/nearai/ironclaw/pull/5995) (P1: manifest v3, recipes, resolved record) and [#5996](https://github.com/nearai/ironclaw/pull/5996) (P2: adapters, ExtensionHost, tool-dispatch cutover) — this is the largest structural change in flight, reworking how extensions are loaded and dispatched.
- **Queued-message steering:** [#5981](https://github.com/nearai/ironclaw/pull/5981) (split 1/2) allows user messages to busy threads to be queued as steering input rather than rejected, with WebUI visibility.
- **Recoverable error hardening:** [#5965](https://github.com/nearai/ironclaw/pull/5965) (XL-sized) ensures recoverable dispatch errors carry their real cause into model-visible detail channels instead of dropping them.
- **Agent guidance rewrite:** [#6001](https://github.com/nearai/ironclaw/pull/6001) rewrites `AGENTS.md` around Reborn-native architecture, removing v1 source-path scopes.
- **Admin-provisioned secrets scoping:** [#5934](https://github.com/nearai/ironclaw/pull/5934) threads WebUI caller default agent scope through admin secret operations.
- **CI improvements:** [#5639](https://github.com/nearai/ironclaw/pull/5639) (staging-release promotion), [#6005](https://github.com/nearai/ironclaw/pull/6005) (flaky Slack trigger poller fix), [#5991](https://github.com/nearai/ironclaw/pull/5991) (require Responses API coverage in PR checks), [#6004](https://github.com/nearai/ironclaw/pull/6004) (Google OAuth token refresh per canary run).

## Community Hot Topics

### Most Active Issues

1. **[#5969] GLM-5.2 not available in opencode default model list** — [Issue](https://github.com/nearai/ironclaw/issue/5969) — 1 comment, closed. User had to manually configure a model that should be included by default.

2. **[#6000] No security reporting channel** — [Issue](https://github.com/nearai/ironclaw/issue/6000) — 0 comments but critical topic. Reporter has a potential security finding but cannot find private reporting mechanism; no `SECURITY.md` and GitHub private vulnerability reporting is disabled.

3. **[#5998] Local MCP server rejected by Reborn** — [Issue](https://github.com/nearai/ironclaw/issue/5998) — Detailed analysis of how `stdio` transport and loopback HTTP are both blocked, leaving no path for local MCP servers.

4. **[#5992] Daily failure taxonomy** — [Issue](https://github.com/nearai/ironclaw/issue/5992) — Systematic analysis showing clawbench failures are dominated by a benchmark defect (~77+ tasks failed due to test infrastructure, not model quality).

### Underlying Needs
The community is signaling **three clear needs**:
- **Better default model lists** (#5969) — users expect popular models to work out of the box
- **Security transparency** (#6000) — the lack of a reporting channel is a governance gap that could deter responsible disclosure
- **Local/offline development support** (#5998, #5999) — users want to develop and test with local resources, which is currently blocked by POSIX-only path handling and MCP transport restrictions

## Bugs & Stability

### High Severity
- **[#5999] local-dev-yolo cannot start on Windows** — [Issue](https://github.com/nearai/ironclaw/issue/5999) — `MountAlias` expects POSIX paths; Windows paths with backslashes are incompatible. **No fix PR yet.** This blocks all Windows development.

- **[#5998] No transport for local MCP server** — [Issue](https://github.com/nearai/ironclaw/issue/5998) — Both `stdio` and loopback HTTP are denied. **No fix PR yet.** Blocks local MCP development entirely.

- **[#6000] No private security reporting channel** — [Issue](https://github.com/nearai/ironclaw/issue/6000) — Governance gap. **No fix PR yet.** Exposes the project to risk of unreported vulnerabilities.

### Medium Severity
- **[#5969] GLM-5.2 missing from default model list (closed)** — Already fixed or manually configurable, but indicates a process gap in model-list maintenance.
- **[#5968] HTTP tool fails with third-party APIs without MCP support** — [Issue](https://github.com/nearai/ironclaw/issue/5968) — Generic HTTP tool returns non-descriptive errors and lacks auth/egress support. **No fix PR yet.**

### Low Severity / Test Infrastructure
- **[#5992] clawbench dominated by benchmark defect** — 77+ tasks fail due to test infrastructure, not model quality. Tracked but not prioritized as user-facing.

### Fix PRs in Flight
- **[#5951] Streaming tool-call trailing content fix** — merged, fixes reasoning models getting empty arguments.
- **[#5965] Recoverable error hardening** — open, ensures errors carry real cause to model.
- **[#6005] Flaky Slack trigger poller** — open, deterministic tick eliminates timing-dependent failures.

## Feature Requests & Roadmap Signals

### High-Confidence Roadmap Items (active PRs)
- **Extension runtime** (PRs #5995, #5996) — manifest v3, adapters, dispatch cutover. Likely in next release (0.30+).
- **Queued-message steering** (#5981) — active-run steering from queued user messages. Likely next release.
- **Responses API completion** (#5990, #5991) — closing semantic fidelity gaps, with CI coverage requirement. High priority.
- **Admin-provisioned secrets scoping** (#5934) — WebUI integration for secret management. Likely next release.

### User-Requested Features
- **Easy local proxy service for private inference** (#5987) — users want a simple proxy that handles attestation and connects to CVM, so they don't need to implement attestation themselves. **No PR yet.**
- **Better default model lists** (#5969) — implicit request for automated model-list synchronization. **No PR yet.**

### Prediction for Next Release (v0.29→v0.30)
The next release will likely include: extension-runtime P0–P2, queued-message steering, recoverable error hardening, Responses API coverage, admin secrets scoping, and the agent guidance rewrite. The Windows/local-dev issues will likely not be fixed in time unless prioritized for hotfix.

## User Feedback Summary

### Pain Points
- **Offline/local development blocked on Windows** (#5999) — `local-dev-yolo` is completely broken on Windows
- **Local MCP server development impossible** (#5998) — no supported transport for on-device MCP
- **Security disclosure barrier** (#6000) — reporter found a vulnerability but cannot report privately
- **Complex attestation setup** (#5987) — users find attestation documentation too complex and want a proxy service
- **HTTP tool limited for third-party APIs** (#5968) — generic tool lacks auth and egress for non-MCP services

### Satisfaction Signals
- Active community engagement: 50 PRs updated in 24 hours, with multiple regular contributors (ironloopai[bot], Anubhav-Koul, serrrfirat)
- Detailed issue descriptions from users (#5998, #5999, #6000 show thorough investigation)
- Systematic failure tracking (#5992) shows project transparency and commitment to quality

### Use Cases
- **AI agent development** — opencode integration, model configuration
- **Third-party API integration** — Attio and similar services without MCP support
- **Cross-platform development** — Windows users attempting to set up local dev environments
- **Security research** — vulnerability disclosure attempts

## Backlog Watch

### Critical Items Needing Maintainer Attention
1. **[#6000] Security reporting channel** — [Issue](https://github.com/nearai/ironclaw/issue/6000) — 0 comments, no maintainer response. **Reporter has a finding they want to disclose privately.** This is a governance gap that could lead to a public disclosure if unaddressed.

2. **[#5999] Windows local-dev-yolo broken** — [Issue](https://github.com/nearai/ironclaw/issue/5999) — 0 comments, no maintainer response. Windows compatibility is a growing concern.

3. **[#5998] Local MCP server transport blocked** — [Issue](https://github.com/nearai/ironclaw/issue/5998) — 0 comments, no maintainer response. Blocks a common development workflow.

4. **[#5987] Request for local proxy service** — [Issue](https://github.com/nearai/ironclaw/issue/5987) — 0 comments, no maintainer response. User experience friction with attestation.

### Long-Open Items
- **[#5598] Release PR** — [PR](https://github.com/nearai/ironclaw/pull/5598) — Open since 2026-07-03 (9 days), blocking version bumps for three crates. Two have breaking changes. Awaiting maintainer merge or further work.
- **[#5639] Main CI checks staging-release promotion** — [PR](https://github.com/nearai/ironclaw/pull/5639) — Open since 2026-07-04 (8 days), large CI infrastructure change.

### Trend Observation
This is the first digest where three issues from the same reporter (Anubhav-Koul) cover platform portability (#5999), network architecture (#5998), and security governance (#6000) — suggesting a systematic reviewer or early adopter testing the project's edge cases. These issues collectively represent a **quality-of-life threshold** for users outside the Linux-first development path.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

Here is the structured digest for **LobsterAI** based on the provided GitHub data for **2026-07-12**.

---

## LobsterAI Project Digest – 2026-07-12

### 1. Today's Overview
The LobsterAI project is currently in a **low-activity maintenance phase**. Over the past 24 hours, there were no new releases or merged pull requests, and no issues were resolved. The project saw updates to 4 open items (3 issues, 1 PR), all of which have been marked as "stale" (last updated over 3 months ago and untouched for the last 24 hours). This stagnation suggests a potential pause in core development, though community members are still submitting quality-of-life feature requests that remain pending triage and prioritization.

### 2. Releases
**None.** No new versions were published today, and no releases are listed in the data.

### 3. Project Progress
**No merged or closed PRs today.** The only PR activity was an update to an existing open request.

### 4. Community Hot Topics
The entire active issue/PR set revolves around UI/UX enhancements for the "Cowork" feature. All three items have exactly 1 comment each and zero reactions, indicating **low community engagement** but clear, specific user needs.

- **#1326 (Issue) & #1327 (PR): ToolUse 工具调用块批量展开/折叠**  
  *Author: MaoQianTu* | [Issue Link](https://github.com/netease-youdao/LobsterAI/issues/1326) | [PR Link](https://github.com/netease-youdao/LobsterAI/pull/1327)  
  *Analysis:* The most actionable item. The user proposes a "Expand All / Collapse All" toggle when an AI turn contains 2+ tool calls. The author has already submitted a matching PR (#1327), meaning this feature is ready for review and likely to be merged if maintainers engage. This reflects a deep user need for **reducing repetitive clicks in multi-tool workflows**.

- **#1330: Error Status Red Dot Indicator in Session List**  
  *Author: MaoQianTu* | [Issue Link](https://github.com/netease-youdao/LobsterAI/issues/1330)  
  *Analysis:* Another UI polish request. Users want a red dot (with glow effect) on error-state sessions in the sidebar. Currently only `running` and `unread` states are visualized. This indicates a **visibility gap in operational monitoring**—users cannot quickly spot broken workflows.

- **#1329: Scheduled Task Notification Channels Empty**  
  *Author: gongfen0121* | [Issue Link](https://github.com/netease-youdao/LobsterAI/issues/1329)  
  *Analysis:* A **functional bug** rather than a feature request. The user reports that new scheduled tasks only offer "Don't notify" as an option in the notification channel dropdown. This directly blocks use of a core automation feature.

### 5. Bugs & Stability
**No new bugs reported today** (only pre-existing stale items). The most critical pending bug is:

- **#1329 (High Severity): Scheduled Task Notification Channels Broken**  
  *Age:* 101 days, *Comments:* 1, *Fix PR:* None  
  *Impact:* Users cannot configure notification channels for scheduled tasks. This is a regression or missing feature that effectively disables monitoring automation. No maintainer response or PR exists yet.

**No crashes, regressions, or security issues are reported in today's data.**

### 6. Feature Requests & Roadmap Signals
All three open items are feature requests (with #1329 being a bug-masquerading-as-feature). Likely candidates for the next version:

| Prediction | Issue | Rationale |
|---|---|---|
| **High confidence** | #1326 / #1327 (Batch tool toggle) | Already has a complete, ready-to-merge PR with testable code. |
| **Medium confidence** | #1330 (Error badge) | Simple UI change; could be bundled with a minor UI polish release. |
| **Low confidence** | #1329 (Notification channels) | Blocking but requires backend/dropdown data fetching logic—likely deeper fix. |

**Roadmap Signal:** The community is consistently asking for **better session feedback** (visual status) and **batch interaction controls**. Future versions may focus on Cowork UI ergonomics.

### 7. User Feedback Summary
- **Pain Points:** Users are frustrated by micro-level inefficiencies (clicking each tool call individually) and lack of visual cues (cannot see broken sessions at a glance). Scheduled automation setup is partially broken.
- **Satisfaction:** No positive feedback is visible in the data. The silence from maintainers (no comments in 100+ days on any item) may be a source of user dissatisfaction.
- **Use Cases:** Power users running complex multi-tool AI sessions; administrators setting up cron-style notifications via scheduled tasks.

### 8. Backlog Watch
All three open issues and the PR are **stale** (last updated over 3 months ago). They require urgent maintainer attention:

| Item | Age (days) | Risk | Why it matters |
|---|---|---|---|
| **#1326 / #1327** (Feature + PR) | 101 | **High** | User contributed code is pending review. Risk of community frustration if continues to rot. |
| **#1329** (Bug) | 101 | **High** | Blocks a core automation feature. |
| **#1330** (Feature) | 101 | **Medium** | Low effort, high visibility improvement. |

**Recommendation:** Maintainers should triage these four items as a batch. Merging #1327 would immediately signal responsiveness. Acknowledging the remaining issues with a "planned" label would reduce community uncertainty.

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyagi">TinyAGI/tinyagi</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

# Moltis Project Digest — July 12, 2026

## Today's Overview
Development activity on Moltis is very low today, with zero issues updated in the last 24 hours and no new releases published. One pull request (#1147) was updated yesterday and remains open, representing the only visible contributor activity. The project appears to be in a quiet maintenance phase, with no bug reports, feature requests, or community discussion emerging during this period. While the single open PR indicates some backend progress, the overall project pulse is subdued.

## Releases
No new releases were published in the last 24 hours. The most recent Moltis release remains unavailable for tracking; no version history or changelog was detected in today's data.

## Project Progress
No pull requests were merged or closed today. The one open PR that saw an update is:

- **#1147 [OPEN]** `fix(caldav): honor time range in list_events via server-side calendar-query`  
  Author: thoscut | Updated: 2026-07-11 | [Link](https://github.com/moltis-org/moltis/pull/1147)  
  **Summary:** This PR fixes a critical bug where the `list_events` tool ignored the `start` and `end` time range parameters. The `_range` parameter was bound but never passed to the CalDAV server, causing the client to fetch all calendar resources regardless of requested time windows, contradicting documented behavior. The fix now issues a proper CalDAV calendar-query with time-range filtering, which should improve performance and correctness for calendar-related interactions.

Despite being a fix, this PR remains unmerged, meaning the bug is still present in the current codebase.

## Community Hot Topics
There are no active discussions or high-activity threads in the project today. The only open PR (#1147) has zero comments and zero reactions. This indicates a complete absence of community engagement in the past 24 hours, which may reflect either a very stable project or low community visibility.

## Bugs & Stability
No new bugs, crashes, or regressions were reported today. However, the open PR #1147 highlights a known bug in `list_events` that remains unresolved: the time range parameters `start` and `end` have no effect, causing the tool to fetch all events from the calendar server. This is a **medium-severity** functional bug that makes calendar queries inefficient and potentially unusable for large calendars. No other stability issues were recorded.

## Feature Requests & Roadmap Signals
No new feature requests were filed or discussed today. The quietness around feature proposals suggests either current feature completeness or a lull in community feedback. The ongoing fix in PR #1147 indicates that improving CalDAV functionality is the nearest priority, but no roadmap items were signaled.

## User Feedback Summary
No user feedback, pain points, or satisfaction/dissatisfaction signals were captured in the last 24 hours. The absence of any comments on the open PR or issues suggests that either users are not encountering problems, or they are not actively reporting them through GitHub. The lack of reactions on PR #1147 may imply low user awareness of the CalDAV time-range bug.

## Backlog Watch
No long-unanswered issues or PRs requiring maintainer attention were identified in today's data. The only open PR (#1147) is relatively recent (submitted July 11) and has not yet received a response. It does not yet qualify as backlog, but it represents the sole pending work item and would benefit from maintainer review to clear the CalDAV bug from the codebase.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

Here is the CoPaw project digest for **2026-07-12**.

---

## CoPaw Project Digest
**Date:** 2026-07-12
**Source Data:** github.com/agentscope-ai/CoPaw

### 1. Today's Overview
The CoPaw project is experiencing a **high-severity stability crisis** following the recent v2.0.0 release. In the last 24 hours, 23 issues were updated—all remaining open—with a surge of bug reports indicating severe regressions in core functionality. The most critical problems include a Windows sandbox causing system crashes (pwsh recursion), context compression breaking AI model API calls, and data migration errors for users upgrading from v1.x. While the community is active in reporting and triaging, the maintainers have yet to issue a hotfix or patch release. The project is currently in a **reactive, high-pressure** state as the user base struggles with a release that appears to have been pushed with significant defects.

### 2. Releases
**No new releases** were published in the last 24 hours. The project remains on v2.0.0, which is the source of the majority of today’s reported issues. Given the volume of critical bugs, a patch release (v2.0.1) is urgently needed.

### 3. Project Progress
5 Pull Requests were merged or closed today, all focusing on a single UI fix:
- **Dark Mode Readability Fix:** Four separate PRs ([#5970](agentscope-ai/QwenPaw PR #5970), [#5971](agentscope-ai/QwenPaw PR #5971), [#5973](agentscope-ai/QwenPaw PR #5973), [#5974](agentscope-ai/QwenPaw PR #5974)) were opened and closed by the same author to fix low-contrast text in dark mode (Closes #5969). The final version merged was [#5974](agentscope-ai/QwenPaw PR #5974).
- **No backend or core logic PRs were merged today.**

**Observations:** The development effort today is entirely cosmetic. No merged PRs address the critical regressions reported in the issue tracker, which is a concerning signal for project health.

### 4. Community Hot Topics
The three most active threads highlight a major regression in the context management system:

- **[#5951] [Bug]: Windows 沙箱问题 (7 comments)** - The highest priority technical issue. Users report that the sandbox (used for executing shell commands) causes an infinite recursive spawn of `pwsh.exe` windows, consuming 20GB of RAM and rendering the tool unusable on Windows. This is a **blocker for all Windows users**.
    - Link: [Issue #5951](agentscope-ai/QwenPaw Issue #5951)

- **[#5961] [Bug]: v2.0.0 循环执行 (3 comments)** - Users report that agents using the Qwen 3.7+ model get stuck in infinite loops of "write, delete, write, delete," failing to complete simple tasks. This suggests a fatal flaw in the agent loop’s decision logic in v2.0.0.
    - Link: [Issue #5961](agentscope-ai/QwenPaw Issue #5961)

- **[#5960] [Bug]: 上下文压缩跨消息边界拆散 tool_call/tool_result 配对导致 400 (2 comments)** - This bug causes AI API calls (e.g., DeepSeek) to return HTTP 400 errors. The context compression system is incorrectly splitting paired function call requests and responses across separate messages, breaking the model’s required input format. This is likely the root cause of many "Internal error" reports.
    - Link: [Issue #5960](agentscope-ai/QwenPaw Issue #5960)

### 5. Bugs & Stability
The v2.0.0 release has introduced multiple **critical regressions**. Bugs are ranked by severity below:

| Severity | Issue | Description | Fix PR? |
| :--- | :--- | :--- | :--- |
| **CRITICAL** | [#5951](agentscope-ai/QwenPaw Issue #5951) | Windows sandbox causes infinite pwsh spawn & memory exhaustion. | None |
| **CRITICAL** | [#5960](agentscope-ai/QwenPaw Issue #5960) | Context compression breaks tool_call/tool_result pairs, causing API 400 errors. | None |
| **CRITICAL** | [#5962](agentscope-ai/QwenPaw Issue #5962) | WeChat channel fails with 400 due to same context compression bug as #5960. | None |
| **CRITICAL** | [#5967](agentscope-ai/QwenPaw Issue #5967) | Pydantic data migration error blocks all agents after upgrade. | None |
| **HIGH** | [#5961](agentscope-ai/QwenPaw Issue #5961) | Agent loops infinitely on Qwen 3.7+ models. | None |
| **HIGH** | [#5963](agentscope-ai/QwenPaw Issue #5963) | Shell command execution hard-capped at 60s; timeouts ignored. | None |
| **MEDIUM** | [#5950](agentscope-ai/QwenPaw Issue #5950) | Embedding errors for Chinese text due to character vs. token counting. | None |
| **MEDIUM** | [#5952](agentscope-ai/QwenPaw Issue #5952) | Auto-memory fails due to missing submodule in desktop build. | None |
| **MEDIUM** | [#5966](agentscope-ai/QwenPaw Issue #5966) | Confusion over internal kernel version (2.0 vs 1.12). | None |
| **LOW** | [#5969](agentscope-ai/QwenPaw Issue #5969) | Dark mode text contrast is poor. | PR [#5974](agentscope-ai/QwenPaw PR #5974) |

**Data Migration Failures:** A cluster of bugs ([#5964](agentscope-ai/QwenPaw Issue #5964), [#5956](agentscope-ai/QwenPaw Issue #5956), [#5967](agentscope-ai/QwenPaw Issue #5967)) confirm that the upgrade path from v1.x to v2.0.0 is broken, causing loss of chat history and session data.

### 6. Feature Requests & Roadmap Signals
- **Improved Permission System ([#5954](agentscope-ai/QwenPaw Issue #5954)):** A user explicitly criticized the new v2.0.0 permission modes (Auto, Smart) as too noisy, requesting a "Whitelist" mode where users can "run once" or "always allow." This strongly suggests the current UX for tool permissions is a regression.
- **Channel Output Control ([#5976](agentscope-ai/QwenPaw Issue #5976)):** A request to separate the sending of "tool call parameters" from "tool call results" to channels, and to truncate large results. This indicates power users are hitting token limits or noise issues in multi-agent channels.
- **OAuth Support ([#4124](agentscope-ai/QwenPaw Issue #4124)):** A long-standing request for OAuth login for OpenAI/Codex providers, which is still open.

**Prediction:** The next release must prioritize a **complete rework of the context compression system** and a **fix for the data migration layer**. The permission system will likely be tweaked based on the strong negative feedback.

### 7. User Feedback Summary
User sentiment is **strongly negative** due to the v2.0.0 upgrade.

- **High Pain:** "升级到最新版后沙箱实现存在严重且无法关闭的问题，整个工具几乎不可用" (After upgrade, the sandbox has a serious bug that cannot be turned off, making the entire tool almost unusable). [Source: #5951]
- **High Pain:** "发现智能体总会反反复复的写入、删除、写入、删除，很长时间也不能完成一个简单任务" (Agent keeps writing and deleting, unable to complete a simple task). [Source: #5961]
- **Frustration (Permission):** "新设计的权限模式感觉不好用，用起来很麻烦" (The new permission model feels bad and is troublesome to use). [Source: #5954]
- **Confusion:** "目前可以通过脚本安装的方式升级到 v2.0.0 吗？我升级后还是 v1.1.12" (Can I upgrade to v2.0.0 via script? After upgrade, I still see v1.1.12). [Source: #5959]
- **Positive (Design):** A user contributed a fix for dark mode visibility (#5969), showing community willingness to help polish the UI, but this is overshadowed by core logic failures.

### 8. Backlog Watch
The following issues have been open for extended periods without resolution and represent unmet community needs:

- **[#4124] Support OAuth login for OpenAI / Codex** - Open since **2026-05-08**. This is a significant feature request with no recent activity from maintainers.
    - Link: [Issue #4124](agentscope-ai/QwenPaw Issue #4124)

- **[#2664] Support for Intel Macs** - Open since **2026-03-31**. While this may be a lower priority, the lack of any response or update is a gap for users still on Intel hardware.
    - Link: [Issue #2664](agentscope-ai/QwenPaw Issue #2664)

**Maintainer Attention Required:** The lack of any official communication (e.g., "we are aware" or "hotfix is coming") on the critical regressions listed in Section 5 is the project's biggest risk today. Users are filing duplicates because the core bugs are not being acknowledged.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

# ZeroClaw Project Digest — 2026-07-12

## Today's Overview
High activity across the ZeroClaw repository with 50 issues and 50 PRs updated in the last 24 hours. All 50 issues remain open (none closed), signaling a heavy backlog of active work. The project saw 4 PRs merged/closed today, indicating steady but measured throughput. No new releases were published. The most significant development trend is the coordinated **goal-mode implementation split stack** (tracker #8681) with 9 comments and multiple stacked PRs, representing a major architectural initiative that is currently the project's largest active feature effort. Overall project health is mixed: strong contributor engagement and ambitious feature development, but also several high-severity bugs and a growing tracker burden for the v0.8.3 milestone.

## Releases
No new releases today. The last release notes remain the most recent published version.

## Project Progress
**4 PRs merged/closed in the last 24 hours:**

- **#9004** `docs(rustdoc): stop linking private helpers` (closed) — Maintained strict intra-doc link lint hygiene; small docs-only fix.
- **#8924** `docs(maintainers): clarify review validation evidence` (closed) — Relaxed validation requirements for CI-covered changes; improves maintainer workflow.
- **#8989** `docs(maintainers): shorten issue stale window` (closed) — Reduced stale-entry window from 45 to 15 days; increases responsiveness pressure.
- **#8987** `feat(quickstart): recommend capability-safe runtime defaults` (merged) — Core quickstart improvement: daemon now authors default provider-safe runtime recommendations rather than maintaining separate policy.

**Key feature advances visible in open PRs:**
The **goal-mode implementation stack** (tracker #8681) now has 5 stacked PRs in active development:
- **#8687** — Goal controller and verifier (Rust-side admission path, restart recovery, cost attribution)
- **#8688** — Trusted goal tools and delegation boundaries (model-callable `goal_start`, `goal_objective`, `goal_resume`)
- **#8689** — Channel goal command admission (`/goal start`, `status`, `budget`, etc.)
- **#8746** — Fix active goal self-resume loops
- **#8996** — Preserve running goals across daemon reload

## Community Hot Topics
**Most active issues (by comment count):**

1. **#8681** [Tracker: Goal mode implementation split stack](https://github.com/zeroclaw-labs/zeroclaw/issues/8681) — **9 comments**. The highest-activity item. Coordinates splitting the accepted goal-mode feature into reviewable PRs. Author vrurg is driving this architectural effort. Represents the project's most ambitious current feature work.

2. **#8054** [System prompt tool-availability mismatch across entry points](https://github.com/zeroclaw-labs/zeroclaw/issues/8054) — **9 comments**. A critical bug where different entry points (WebSocket, multimodal, /think) show inconsistent tool availability to the model. Perlowja filed this as a follow-up to fix #7756.

3. **#5808** [Default 32k context budget exceeded on iteration 1](https://github.com/zeroclaw-labs/zeroclaw/issues/5808) — **8 comments**. A persistent S1 issue where the first LLM call already exceeds context budget ~3.3x due to system prompt + tool definitions. Blocked workflow for users with default settings.

4. **#7952** [Publish full-channel prebuilt assets](https://github.com/zeroclaw-labs/zeroclaw/issues/7952) — **6 comments**. Community demand for channel-specific prebuilt binaries to avoid confusion when users configure channels not included in the default bundle.

**Underlying needs analysis:**
- **Goal-mode tracker** reflects demand for structured, long-running agent objectives with budget controls and recovery—a sophisticated feature that distinguishes ZeroClaw from simpler agent frameworks.
- **Context budget issues** (common among top threads) show users hitting practical scalability limits with default configurations.

## Bugs & Stability
**High-severity bugs (P1) active today:**

| Issue | Severity | Bug Description | Fix PR Status |
|-------|----------|----------------|---------------|
| **#8654** | P1 | skill-review fork panics (out-of-range slice) → SIGSEGV after tool-heavy turns | Status: in-progress, no fix PR yet |
| **#8675** | P1 | Malformed native tool-call arguments sent unvalidated to OpenAI-format providers → provider 400 → empty reply | Status: accepted, no fix PR yet |
| **#8642** | P1 | MCP/tool-schema cloning drives unbounded RSS growth in agent loop (split from OOM root cause #5542) | Status: accepted, no fix PR yet |
| **#8718** | P2 (S2) | `zeroclaw config init` ships config template that daemon rejects, silently disabling local_whisper transcription | Fix PR #8751 open (needs-author-action) |
| **#6350** | P1 | WhatsApp Web allowed-numbers bypassed for LID-based contacts (silent message drops) | Status: in-progress |

**New or escalated bugs in last 24 hours:**
- **#8720** (P2) — Bedrock Nova 2 Lite cachePoint errors; user asks for config-level caching disable
- **#8578** (P2) — On daemon start failure, zerocode doesn't terminate the failed process (leaks zombie)

**CRITICAL WARNING:** The skill-review fork panic (#8654) takes down the entire agent process with SIGSEGV under `panic=abort`. This means a single tool-heavy turn can crash the whole daemon. No fix PR exists yet.

## Feature Requests & Roadmap Signals
**Active user-requested features:**

1. **#8134** — `session_ttl_hours` auto-truncation of stale session history. In-progress. High community value for teams running multiple channels (Slack, Telegram) to reduce token waste. Likely for v0.8.3.

2. **#7759** — Decouple gateway WebSocket lifetime from agent turn lifecycle. Accepted (P1). Enables background turns that survive client disconnects. Likely for v0.8.3.

3. **#8832** — RFC: Gateway-local Kanban board for agent work. New (2 comments). Inspired by OpenClaw Workboard plugin. Unlikely for immediate shipping—still in RFC phase.

4. **#8695** — Skills management UI in gateway dashboard. Accepted. Complements existing gateway management for a first-class runtime concept.

5. **#7952** — Full-channel prebuilt binaries. Blocked, needs maintainer review. Strong user demand.

**Prediction for next release:** The **goal-mode stack** (5 PRs) is the most likely major feature to land. The **session TTL** (#8134) and **background WebSocket turns** (#7759) are strong candidates due to P1 acceptance status.

## User Feedback Summary
**Real pain points heard today:**
- **Configuration friction:** "I can use Bedrock Nova 2 Lite, but I am randomly getting a caching error. I want to disable caching" (#8720) — users want per-model config knobs without code changes.
- **Silent failures:** "zeroclaw config init writes values that the daemon rejects, silently disabling transcription" (#8718) — new users get zero feedback about broken features.
- **Memory growth:** "MCP/tool-schema cloning drives unbounded RSS growth" (#8642) — users report OOM on long-running agent sessions.
- **Process management:** "On failure to start daemon, it doesn't terminate the process" (#8578) — operator experience issue.

**Satisfaction signals:**
- Active participation in goal-mode feature discussions (vrurg's tracker has 9 comments from multiple contributors)
- Community members filing detailed bug reports with reproduction steps (tw-360vier's SIGSEGV report, metalmon's malformed arguments report)

## Backlog Watch
**Issues/PRs needing maintainer attention (long-open, unanswered, or stuck):**

| Item | Days Open | Status | Notes |
|------|-----------|--------|-------|
| **#7952** — Publish full-channel prebuilt assets | 23 days | `blocked, needs-maintainer-review` | Community wants this; maintainer action required |
| **#7960** — `execute_pipeline` tool access policy bypass | 23 days | `needs-author-action` | Security bug fix stalled on author response |
| **#6350** — WhatsApp Web LID-based contact bypass | 70 days | `status:in-progress` | Critical P1; silent message drops; no fix in sight |
| **#5808** — Default 32k context budget overflow | 87 days | `status:in-progress` | S1 workflow blocker; still unresolved |
| **#8135** — Wasm-first plugin runtime RFC | 20 days | `status:accepted` | Major architecture decision; no implementation PR yet |
| **#8751** — Fix LocalWhisperConfig defaults (fix for #8718) | 6 days | `needs-author-action` | Fix exists but author needs to respond |
| **#8838** — Idle-bound SSE streaming fix | 4 days | `needs-author-action` | High-risk XL PR; stuck on author |

**Most concerning:** #5808 (87 days, S1) and #6350 (70 days, P1) represent long-standing critical defects with no resolution in sight. The v0.8.3 milestone tracker (#7320) shows 15 open items with a frozen scope—this milestone appears to be growing rather than closing.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*