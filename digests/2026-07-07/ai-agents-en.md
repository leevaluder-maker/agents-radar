# OpenClaw Ecosystem Digest 2026-07-07

> Issues: 500 | PRs: 500 | Projects covered: 13 | Generated: 2026-07-07 02:08 UTC

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

# OpenClaw Project Digest — 2026-07-07

## Today's Overview

OpenClaw shows **extreme activity levels** with **500 issues and 500 PRs updated in the last 24 hours**, indicating a highly engaged community and active development cycle. Of the updated issues, **402 remain open** (highly active backlog), while **98 were closed**; of the PRs, **199 were merged or closed**, and **301 remain open**. No new official releases were published today, though the project continues to process a large volume of community contributions. The project appears to be in a **sustained high-velocity development phase**, with maintainers and community contributors actively processing a substantial queue of fixes, features, and stability improvements.

---

## Releases

**No new releases** were published on 2026-07-07. The most recent available version in the issue tracker references `v2026.6.11`, which was noted to have a published-dist regression (Issue #98416). Users should monitor for the next patch release.

---

## Project Progress

**199 PRs merged/closed today**, indicating strong forward momentum. Significant closures include:

- **fix(chat.abort): pass stored sessionId to match active embedded runs** ([PR #101222](https://github.com/openclaw/openclaw/pull/101222)) — A **XL-sized P1 fix** ensuring the `chat.abort` RPC reliably stops active tool subprocesses, closing a gap where external UI integrations (e.g., Open WebUI) could not abort running operations. Status: 👀 ready for maintainer look.

- **fix(agents): normalize surrogate cache fingerprints** ([PR #101009](https://github.com/openclaw/openclaw/pull/101009)) — Closes Issue #100957, addressing malformed UTF-16 surrogate halves causing prompt-cache normalization mismatches.

- **fix(auto-reply): stop treating wait as abort trigger** ([PR #98639](https://github.com/openclaw/openclaw/pull/98639)) — Fixes a Telegram-specific bug where the word "wait" in group chats was misinterpreted as an abort command.

- **refactor(codex): store app-server thread bindings in SQLite plugin state** ([PR #101210](https://github.com/openclaw/openclaw/pull/101210)) — A **XL-sized** refactor moving Codex bindings from file-locked JSON sidecars to SQLite, ending cross-process locking violations.

Notable open PRs with active progress include a **large continuation feature** ([PR #85651](https://github.com/openclaw/openclaw/pull/85651)) for context-pressure-aware agent self-continuation (`continue_work`/`continue_delegate`/`request_compaction`), and a **heartbeat fix** ([PR #100377](https://github.com/openclaw/openclaw/pull/100377)) addressing a ~60s per-tick latency regression.

---

## Community Hot Topics

### Most Active Issues (by comments)

1. **[#75 — Linux/Windows Clawdbot Apps](https://github.com/openclaw/openclaw/issues/75)** (110 comments, 81 👍)
   *P2, enhancement, security-impact, UX-friction* — The highest-engagement item. Users are requesting native desktop apps for Linux and Windows, matching existing macOS/iOS/Android offerings. This signals **strong cross-platform demand** from the community.

2. **[#25592 — Text between tool calls leaks to messaging channels](https://github.com/openclaw/openclaw/issues/25592)** (33 comments)
   *P1, diamond lobster severity, security & message-loss impacts* — A critical UX/security bug where internal agent processing output (error handling, narration) is exposed to users via Slack, iMessage, etc. High priority for maintainers.

3. **[#9443 — Prebuilt Android APK releases](https://github.com/openclaw/openclaw/issues/9443)** (27 comments, 4 👍, **closed**)
   *P0, security/ux-release-blocker* — **Now closed**, suggesting the team has resolved the prebuilt Android APK distribution gap.

4. **[#98416 — v2026.6.11 published dist missing reentrancy guard](https://github.com/openclaw/openclaw/issues/98416)** (20 comments, 5 👍, **closed**)
   *P1, diamond lobster* — A released-version regression where the published distribution lacked a critical reentrancy guard, causing reply session initialization conflicts. Now closed.

5. **[#22438 — Tiered bootstrap file loading](https://github.com/openclaw/openclaw/issues/22438)** (17 comments)
   *P2, session-state impact* — A feature request for progressive context control, reducing token waste on large workspaces.

### Most Upvoted Open Issues

| Issue | 👍 | Summary |
|-------|---|---------|
| [#39604](https://github.com/openclaw/openclaw/issues/39604) | 11 | Allow private network access in `web_fetch` |
| [#63829](https://github.com/openclaw/openclaw/issues/63829) | 9 | Per-agent memory-wiki vault configuration |
| [#42840](https://github.com/openclaw/openclaw/issues/42840) | 9 | MathJax/LaTeX support in Control UI |
| [#37634](https://github.com/openclaw/openclaw/issues/37634) | 7 | Sandbox workspace writable when access=none |
| [#20786](https://github.com/openclaw/openclaw/issues/20786) | 6 | Telegram Business Bot support |

### Underlying Community Needs

- **Desktop Parity**: Strong demand for Linux/Windows native apps (#75, 110 comments)
- **Context Efficiency**: Users want tiered bootstrap loading (#22438), reduced tool schema overhead (#14785)
- **Multi-Agent Stability**: Multiple issues (#43367, #35203, #39476) expose friction in concurrent agent orchestration
- **Channel Parity**: Requests for Telegram Business (#20786), Feishu fixes (#41744, #34528), and cross-channel TUI visibility (#40678)

---

## Bugs & Stability

### Critical / P0 Issues

- **[#43661 — Session hangs indefinitely on compaction timeout](https://github.com/openclaw/openclaw/issues/43661)** (7 comments)
  *P0, platinum hermit, ux-release-blocker* — Compaction timeout causes silent failure loops with duplicate message resends every ~10 minutes. **No recovery mechanism**. This is the most severe open bug.

- **[#9443 — Prebuilt Android APK (CLOSED)](https://github.com/openclaw/openclaw/issues/9443)** — Had P0 release-blocker status, now resolved.

### P1 / Diamond Lobster Severity — Open

| Issue | Summary | Impact | Fix PR? |
|-------|---------|--------|---------|
| [#25592](https://github.com/openclaw/openclaw/issues/25592) | Text between tool calls leaks to channels | Security, message-loss | 🔗 Linked PR open |
| [#22676](https://github.com/openclaw/openclaw/issues/22676) | Signal daemon stop() race condition | Orphaned processes, send failures | 🔗 Linked PR open |
| [#29387](https://github.com/openclaw/openclaw/issues/29387) | Bootstrap files in agentDir silently ignored | Session-state, security | 🔗 Linked PR open |
| [#43367](https://github.com/openclaw/openclaw/issues/43367) | Multi-agent orchestration unstable | Session-state, message-loss, auth | 🔗 Linked PR open |
| [#31583](https://github.com/openclaw/openclaw/issues/31583) | `exec` tool doesn't inherit skill env vars | Security, auth (regression) | No linked fix PR |
| [#38327](https://github.com/openclaw/openclaw/issues/38327) | "Cannot convert undefined or null to object" with Gemini | Auth, crash-loop (regression) | Needs live repro |
| [#40611](https://github.com/openclaw/openclaw/issues/40611) | Heartbeat drift fix causes aggressive retry | Session-state, message-loss | 🔗 Linked PR open |
| [#39847](https://github.com/openclaw/openclaw/issues/39847) | Echo contamination — metadata not stripped | Security (stale issue) | 🔗 Linked PR open |

### Regressions

Three regressions are flagged as **"worked before, now fails"**:
- **[#31583](https://github.com/openclaw/openclaw/issues/31583)** — `exec` tool env inheritance broken
- **[#38327](https://github.com/openclaw/openclaw/issues/38327)** — Gemini 3.1 crash on any message (version 2026.3.2)
- **[#43747](https://github.com/openclaw/openclaw/issues/43747)** — Memory management "in chaos" across users — this is particularly concerning as it suggests a systemic regression in memory persistence/embedding behavior

### Recently Fixed (Closed Today/Recently)

| Issue | Summary | Fix |
|-------|---------|-----|
| [#98416](https://github.com/openclaw/openclaw/issues/98416) | v2026.6.11 dist missing reentrancy guard | Closed — fix source published |
| [#101204](https://github.com/openclaw/openclaw/issues/101204) | Gateway fails to start when optional TTS keys missing | Closed by [#101265](https://github.com/openclaw/openclaw/pull/101265) |

---

## Feature Requests & Roadmap Signals

### High-Impact Open Feature Requests (likely next-version candidates)

1. **Tiered Bootstrap File Loading** ([#22438](https://github.com/openclaw/openclaw/issues/22438)) — 17 comments, linked PR open. This is a clear efficiency win that may land soon given the linked PR.

2. **Per-Agent Memory-Wiki Vault Configuration** ([#63829](https://github.com/openclaw/openclaw/issues/63829)) — 12 comments, 9 👍. Strong multi-agent isolation use case, aligns with observed multi-agent stability work.

3. **`tools.web.fetch.allowPrivateNetwork`** ([#39604](https://github.com/openclaw/openclaw/issues/39604)) — 13 comments, 11 👍 (highest upvoted). A relatively small config change that would unblock many internal/intranet use cases.

4. **Pre-response Enforcement Hooks (Hard Gates)** ([#13583](https://github.com/openclaw/openclaw/issues/13583)) — 12 comments, for high-stakes workflow safety. Taps into the existing hooks system.

5. **Write Tool Append Mode** ([#40001](https://github.com/openclaw/openclaw/issues/40001)) — 11 comments. Directly addresses data loss in cron/shared-file scenarios.

### Roadmap Signals

- **Distributed Agent Runtime** ([#42026](https://github.com/openclaw/openclaw/issues/42026)) — An RFC proposing separating control plane from agent compute. This would be a **major architectural shift** and suggests maintainers are thinking about horizontal scaling.
- **Multi-Agent Collaboration Enhancement** ([#35203](https://github.com/openclaw/openclaw/issues/35203)) — An RFC covering capability profiling, shared blackboard, layered memory, and cost governance. This aligns with the multi-agent instability issues being reported.
- **Per-Agent Cost Budget Enforcement** ([#42475](https://github.com/openclaw/openclaw/issues/42475)) — Practical operations feature for cost control at the gateway level.

### Predicted for Next Release

Given the high activity on PR #101222 (chat.abort fix, just closed) and the number of linked-PR open issues at P1, the next patch release will likely focus on **session stability fixes, compaction timeout recovery, and multi-agent reliability improvements**.

---

## User Feedback Summary

### Pain Points

- **Memory instability** — Users report inconsistent memory management across installations (#43747, 9 comments): "Mine keeps doing chunking & embedding... my colleague A, her claw is storing... in a completely different way." This is a regression causing confusion.

- **Multi-agent orchestration fragility** (#43367, 13 comments): "Concurrent agents add/config overwrites, session-lock failures, and detached child work" — users trying parallel workflows hitting systematic failures.

- **CJK/Telegram rendering** — Multiple users report **bold/italic markdown broken for CJK text** (#101229, PR in progress), impacting Chinese/Japanese/Korean users across all channels.

- **Webchat avatar broken** — Duplicate reports ([#38439](https://github.com/openclaw/openclaw/issues/38439), [#41201](https://github.com/openclaw/openclaw/issues/41201)) of 404 errors for agent avatars in the Control UI, flagged as regressions.

- **Tool error warnings in user channels** ([#39406](https://github.com/openclaw/openclaw/issues/39406), 6 comments) — Users find it confusing when transient tool errors are visible in chat even after successful retry.

### Use Cases Driving Activity

- **Multi-user/team deployments** — Issues from groups of 3+ people using OpenClaw simultaneously (#43747)
- **Business/customer-facing bots** — Telegram Business Bot support (#20786), Feishu integration fixes (#41744)
- **Automation/scripiting** — Cron sessions destroying shared files (#40001), backup exclude patterns (#40786)
- **Security-conscious deployments** — Env variable injection (#31583), internal network access (#39604), audit logging (#20935)

### Satisfaction Signals

- 81 👍 on the desktop app request (#75) indicates high satisfaction with existing mobile apps but desire for parity
- Quick closure of P0 Android APK issue (#9443) demonstrates **responsive maintainers on release-blockers**
- The sheer volume of feature requests (not complaints) suggests a **highly engaged, satisfied core user base** that sees OpenClaw as worth investing in

---

## Backlog Watch

### High-Impact Issues Needing Maintainer Attention

| Issue | Age | Priority | Notes |
|-------|-----|----------|-------|
| [#43661](https://github.com/openclaw/openclaw/issues/43661) | 4 months | **P0** | Compaction timeout → duplicate message loop. Needs live repro. |
| [#38327](https://github.com/openclaw/openclaw/issues/38327) | 4 months | P1 | "Cannot convert undefined or null to object" — regression with Gemini. Needs live repro. |
| [#25592](https://github.com/openclaw/openclaw/issues/25592) | 4.5 months | P1 | Text leakage between tool calls. Needs product decision + security review. |
| [#31583](https://github.com/openclaw/openclaw/issues/31583) | 4 months | P1 | `exec` env var regression. **No linked fix PR.** |
| [#22676](https://github.com/openclaw/openclaw/issues/22676) | 4.5 months | P1 | Signal daemon race condition. Has linked PR but still open. |
| [#14785](https://github.com/openclaw/openclaw/issues/14785) | 5 months | P2 | 3,500 token/session tool schema overhead. Long-standing efficiency issue. |
| [#75](https://github.com/openclaw/openclaw/issues/75) | 6 months | P2 | Linux/Windows apps — highest engagement. Needs product decision. |

### PRs Stuck in Review

- **[#85651](https://github.com/openclaw/openclaw/pull/85651)** — Context-pressure continuation (XL, P2, since May 23) — Status: 📣 needs proof after ~6 weeks
- **[#81306](https://github.com/openclaw/openclaw/pull/81306)** — Loopback bind fix (since May 13) — Status: 📣 needs proof after ~8 weeks
- **[#89040](https://github.com/openclaw/openclaw/pull/89040)** — Event-loop stall fix (XL, P1, since June 1) — 👀 ready for maintainer look but awaiting maintainer action

### Metadata Concerns

Many issues carry the following tags, suggesting maintainer bottlenecks:
- `clawsweeper:needs-maintainer-review` — Present on ~40% of the top 50 issues
- `clawsweeper:needs-product-decision` — Present on ~30% of the top 50 issues
- `clawsweeper:needs-security-review` — Present on ~35% of the top 50 issues

This pattern suggests the maintainer team may be **stretched thin on review bandwidth**, even as automated bots (clawsweeper) handle triage. The community is contributing actively, but approval velocity may be a bottleneck.

---

*Generated from GitHub data for openclaw/openclaw, snapshot 2026-07-07. Data reflects 500 issues and 500 PRs updated in the last 24 hours.*

---

## Cross-Ecosystem Comparison

Here is the cross-project comparison report, compiled from the July 7, 2026 community digest summaries.

---

### Cross-Project Ecosystem Comparison Report: AI Agent Open-Source Landscape

**Date:** 2026-07-08 (Analysis of 2026-07-07 Data)

#### 1. Ecosystem Overview

The open-source personal AI assistant and agent ecosystem is experiencing a period of intense, feature-driven development with a clear shift from proof-of-concept to production-ready reliability. Projects like OpenClaw and ZeroClaw are processing massive community contributions, focusing on session stability, multi-agent orchestration, and cost controls. A significant cross-cutting theme is the push for **enterprise-readiness**, evidenced by features like opt-in audit logging (NanoClaw), OAuth maturity (IronClaw, LobsterAI), and multi-account management (LobsterAI). However, this velocity comes with growing pains, as several projects show maintainer bottlenecks in review bandwidth and struggle with silent failures and regressions that undermine user trust in automation.

#### 2. Activity Comparison

| Project | Issues Updated (24h) | PRs Updated (24h) | New Release (24h) | Health Signal |
| :--- | :--- | :--- | :--- | :--- |
| **OpenClaw** | 500 (402 open) | 500 (301 open) | No | **High Velocity** - Extreme community engagement, active backlog churn, but review bandwidth is a bottleneck. |
| **ZeroClaw** | 50 (44 open) | 50 (41 open) | No | **High Intensity** - Strong architectural focus (Goal Mode), critical bugs being addressed, high community engagement on key features. |
| **IronClaw** | 41 (36 open) | 50 (37 open) | No | **High Momentum** - Focused on runtime hardening ("Reborn" architecture), subagent threading, and WebUI modernization. |
| **CoPaw** | 34 (25 open) | 50 (25 open) | Yes (v1.1.12.post3) | **High Activity / Strained** - Shipped a patch fix, but has a large test infrastructure push and open high-severity bugs (memory, mobile). |
| **NanoBot** | 39 (31 open) | 491 (482 open) | No | **Audit & Stabilization** - A 35-finding security audit dominates activity, driving a wave of critical fix PRs across the codebase. |
| **LobsterAI** | 0 | 12 (1 open) | No | **High-Velocity Dev** - Shipped multiple major features (xAI/Grok OAuth, multi-account email, heartbeat controls) in a single day. |
| **Moltis** | 0 | 5 (2 open) | No | **Stable Maintenance** - Incremental fixes (Docker, Telegram, WhatsApp) with no new community distress signals. |
| **PicoClaw** | 4 | 5 (4 open) | No | **Moderate Activity** - Focused on core provider layer (Anthropic caching fix) and Gemini compatibility issues. |
| **NanoClaw** | 3 | 10 (8 open) | No | **Modernization Phase** - Invested in documentation overhaul and merged a significant audit log feature. |
| **NullClaw** | 0 | 1 (1 open) | No | **Maintenance Lull** - No feature development or bug triage visible; a single dependency PR has been stale for 22 days. |
| **TinyClaw** | - | - | No | **No Activity** |
| **ZeptoClaw** | - | - | No | **No Activity** |
| **Hermes Agent** | - | - | - | **Data Unavailable** |

#### 3. OpenClaw's Position

OpenClaw is the clear **ecosystem leader in community size and activity volume**, processing an order of magnitude more issues and PRs than any other project. Its key advantages and differentiators include:

- **Community Scale & Demand:** With 81 upvotes for desktop app parity and hundreds of active issues, OpenClaw has the largest and most vocal user base, driving features like tiered bootstrap loading and cross-platform native apps.
- **Mature Architecture:** It is moving beyond basic tool use into advanced territory with features like context-pressure-aware agent self-continuation and a proposed distributed agent runtime (RFC #42026).
- **Ecosystem Bottleneck:** The sheer volume of contributions (500 PRs/day) creates a significant maintainer review bottleneck, with many high-priority items tagged `needs-maintainer-review`. This is a challenge other projects, managing smaller scales, may not yet face.

In contrast, **ZeroClaw** and **IronClaw** show similar architectural ambition but with a more controlled development pace. **NanoBot** focuses intensely on security hardening, while **CoPaw** and **LobsterAI** prioritize shipping practical features for their user bases.

#### 4. Shared Technical Focus Areas

The following requirements emerged across multiple projects, signaling key areas of industry demand:

- **Session & Context Reliability (OpenClaw, CoPaw, ZeroClaw):** All three projects face bugs related to context compression destroying critical data, session hangs on timeout, and tool state loss. Users demand that long-running agent sessions are robust and recoverable.
- **Silent Failure & Observability (IronClaw, NanoClaw, LobsterAI, OpenClaw):** A systemic user pain point is agents that appear to succeed but silently fail. This is being addressed with "no borking" runtimes (IronClaw), SIEM-ready audit logs (NanoClaw), heartbeat cost controls (LobsterAI), and better error propagation (OpenClaw).
- **MCP & Provider Interoperability (PicoClaw, ZeroClaw, Moltis, CoPaw):** The Model Context Protocol (MCP) is becoming a critical integration point, but projects struggle with OAuth handshakes (Moltis), tool visibility (ZeroClaw), and silent connection failures (NanoClaw).
- **Enterprise & Compliance Features (NanoClaw, LobsterAI, IronClaw):** There is a clear push for production-grade deployments, including opt-in audit trails (NanoClaw), multi-account email management (LobsterAI), OAuth wire-format fixes (IronClaw), and cost governance (ZeroClaw).
- **Cross-Platform & Channel Parity (OpenClaw, NanoBot, ZeroClaw, Moltis):** Users demand consistent experiences on Telegram, Feishu/Lark, Mattermost, WhatsApp, and native desktop apps. Bugs in channel rendering (CJK text) and setup are recurring pain points.

#### 5. Differentiation Analysis

| Project | Primary Differentiator | Target User / Use Case |
| :--- | :--- | :--- |
| **OpenClaw** | **Ecosystem Scale & Breadth** | Power users and developers needing a highly customizable, extensible, and well-integrated multi-agent platform. |
| **ZeroClaw** | **Architectural Rigor (Goal Mode)** | Users and developers prioritizing structured, goal-driven automation and real-time (voice) interaction. |
| **IronClaw** | **Production Runtime (Reborn)** | Developers building high-stakes, automated workflows that demand reliability and subagent persistence. |
| **CoPaw** | **Channel & Market Specificity** | Developers targeting East Asian markets with strong integration for QQ, WeChat, and Chinese LLMs (Qwen). |
| **NanoBot** | **Security & Correctness Focus** | Security-conscious developers and teams who need a verifiably safe agent runtime. |
| **LobsterAI** | **User Experience & Feature Velocity** | End-users and teams wanting an opinionated, polished, and feature-rich desktop-first assistant experience. |

#### 6. Community Momentum & Maturity

- **Tier 1: Rapidly Iterating (High Risk/High Reward)**
    - **OpenClaw** and **ZeroClaw** are pushing architectural boundaries (distributed agents, goal mode) while managing a massive community. IronClaw is foundational re-architecting its core runtime ("Reborn"). These projects offer the most advanced features but come with a higher risk of regressions and instability.
- **Tier 2: Actively Maturing (Stable & Feature-Rich)**
    - **CoPaw**, **LobsterAI**, and **NanoBot** are shipping production-ready features quickly. CoPaw is managing a large community with a patch release cadence. LobsterAI is showing disciplined, high-velocity feature development. NanoBot is consolidating after a major security audit.
- **Tier 3: Stabilizing & Maintaining (Incremental Improvements)**
    - **Moltis** and **PicoClaw** are in a stable maintenance phase, fixing bugs and adding minor features. **NanoClaw** is focused on documenting and hardening existing functionality.
- **Tier 4: Inactive / Dormant**
    - **NullClaw**, **TinyClaw**, and **ZeptoClaw** show no meaningful community activity, suggesting they may be deprecated or in a long-term hiatus.

#### 7. Trend Signals

From the community feedback and technical focus across these projects, several key industry trends are clear:

- **From "Does it work?" to "Can I trust it?":** The dominant theme is the demand for **reliability and observability**. Users are less concerned with new LLM providers and more focused on whether their agent can be trusted to execute a task without silent failure or data loss.
- **The Agent is the Integration Point:** The push for native support of enterprise tools (Slack, Feishu, Mattermost, Teams, Zoom, Notion, Linear) signals that the "AI agent" is becoming a new middleware layer, not just a chatbot. Projects that solve channel reliability and MCP OAuth will win enterprise adoption.
- **Cost Governance is a Core Feature:** Heartbeat cost controls in LobsterAI and cost budget enforcement proposals in OpenClaw show that as agents become more autonomous, managing API token burn is a top-of-mind concern for both individual users and organizations.
- **Architecture Splits to Scale:** The introduction of subagent threads (IronClaw), distributed agent runtimes (OpenClaw), and goal-mode architecture (ZeroClaw) indicates a move away from monolithic agent loops toward more modular, persistent, and scalable agent architectures.
- **Security is Becoming Non-Negotiable:** The explicit security audits in NanoBot, the opt-in audit logs in NanoClaw, and the plugin permission model discussions in ZeroClaw all point towards a maturing ecosystem where security is a prerequisite for production deployment, not an afterthought.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

# NanoBot Project Digest — 2026-07-07

## Today's Overview

NanoBot is in a **high-activity audit and stabilization phase** today, with 39 open issues and 491 open pull requests reflecting intense community and maintainer activity. A comprehensive 35-finding security and correctness audit (Issue #4815) has been filed, driving a wave of targeted fix PRs addressing critical bugs in memory management, tool execution, and runtime safety. The project shows **zero new releases**, indicating the team is consolidating fixes ahead of a potential version bump. With 9 merged/closed PRs in the last 24 hours and hundreds of open PRs in flight, the codebase is undergoing significant but measured improvement.

## Releases

*No new releases were published in the last 24 hours.* The last known release remains the 0.2.2 documentation baseline referenced in bug reports. Given the volume of active fixes (especially security-related), a maintenance release may be imminent.

## Project Progress

**9 pull requests were merged or closed** in the last 24 hours, alongside 8 closed issues. Notable advancements include:

| PR # | Description | Status |
|------|-------------|--------|
| #4673 | fix(dream): ground memory audit records in the real git diff | **Merged** |
| #4654 | fix(cli): print response text when streaming fails in interactive mode | **Merged** |
| #4459 | feat: add Mattermost channel support | **Merged** |
| #1290 | fix(heartbeat): restore HEARTBEAT_OK_TOKEN and legacy callback support | **Merged** |
| #2060 | feat: shell tool: allow configurable specific paths when restrict_to_workspace=True | **Closed** |
| #4818 | fix(runtime): guard web_fetch signature against None URL | **Merged** |

The **Mattermost channel integration** (#4459) is a significant new feature, adding WebSocket + REST API support for real-time messaging and streaming responses. The Dream consolidation fix (#4673) addresses a correctness issue where audit logs could mismatch actual file changes.

## Community Hot Topics

The community is heavily engaged with the **security and correctness audit** dominating discussions:

1. **[#4815 — Audit summary: 35 security / bug / refactor findings](https://github.com/HKUDS/nanobot/issues/4815)** (0 comments, newly filed) — This comprehensive audit by contributor `hamb1y` covers command injection, path escape, auth bypass, deserialization, secrets handling, concurrency bugs, and dead code. Although zero comments yet, the 35 findings have already spawned 11+ targeted fix PRs, indicating high maintainer engagement.

2. **[#4061 — Bug: OpenAI-compatible text-format tool calls not parsed](https://github.com/HKUDS/nanobot/issues/4061)** (6 comments, **CLOSED**) — A significant interoperability issue with OpenAI-compatible providers that emit tool calls as plaintext markup instead of structured `tool_calls`. The root cause was identified in the runner's tool call execution path.

3. **[#4511 — Bug: Windows `--background` gateway option inconsistencies](https://github.com/HKUDS/nanobot/issues/4511)** (4 comments, **CLOSED**) — Windows users experienced process tracking corruption when restarting the gateway with `--background`, where PID file data became inconsistent with actual process state.

4. **[#4544 — Bug: Windows exec shell semantics inconsistency](https://github.com/HKUDS/nanobot/issues/4544)** (3 comments, **CLOSED**) — Cross-platform agent authors faced inconsistent behavior as single-line commands routed to `cmd.exe` while multi-line commands used PowerShell, breaking common patterns like cross-line `cd`.

The underlying need across these threads is **cross-platform reliability and API compatibility** — users consistently report Windows-specific issues and non-standard provider behavior that breaks core workflows.

## Bugs & Stability

The audit (#4815) has identified several critical issues, with fix PRs already submitted for many:

### Critical / P0-P1

| Issue | Description | Severity | Fix PR? |
|-------|-------------|----------|---------|
| #4815 (findings) | Command injection via unsanitized arguments | **Critical** | #4671 |
| #4803 | API keys stored as plaintext in `~/.nanobot/config.json` | **Security** | None yet |
| #4796 | `restrict_to_workspace` defaults to `False` — full filesystem exposed | **Security** | None yet |
| #4795 | Streaming LLM calls bypass wall-clock timeout (no resource protection) | **P1** | None yet |
| #4797 | No resource limits on shell subprocesses — fork bomb risk | **P1** | None yet |
| #4792 | `/stop` silently discards pending queue messages (permanent loss) | **P1** | None yet |
| #4793 | Global ExecSessionManager singleton shared across all agent loops (cross-session visibility) | **P1** | None yet |
| #4794 | Exec sessions have no shutdown cleanup — orphaned child processes | **P1** | None yet |

### Medium / P2

| Issue | Description | Fix PR? |
|-------|-------------|---------|
| #4804 | Leaked `CancelledError` silently swallowed in main agent loop (MCP anyio) | #4814 |
| #4805 | `suppress(Exception)` on `prepare_call` silently swallows validation errors | #4811 |
| #4802 | Token budget returns spurious 128 when context window is disabled (0) | #4817 |
| #4801 | Unprotected `message['role']` dict access — KeyError on malformed entries | #4812 |
| #4800 | `.strip()` on list-form `msg.content` crashes on multimodal messages | #4813 |
| #4799 | External lookup signature creates false cache entry for `None` URLs | #4820 |
| #4798 | Concurrent file writes from different sessions — workspace file corruption | None yet |
| #4791 | No channel-level message rate limiting — DoS risk | None yet |

### Refactoring / Inefficiency

| Issue | Description |
|-------|-------------|
| #4806 | 11 orphaned functions, 8 test-only functions, 3 unused `__all__` exports |
| #4807 | Duplicated channel `__init__` pattern across 16 files — extract to `BaseChannel` |
| #4808 | `json.loads(json.dumps(...))` instead of `copy.deepcopy` — 3 sites |
| #4809 | `setdefault({}).update()` wastes allocation in LLM request hot path |
| #4810 | Duplicated markdown-to-rich-text converters across 3 channels |

## Feature Requests & Roadmap Signals

1. **[#3436 — Call external agent](https://github.com/HKUDS/nanobot/issues/3436)** (3 comments, open since April) — User requests Nanobot rely on external agent frameworks (opencode, codex) instead of its internal agent. This signals demand for **plugin-based agent backends** and could shape a v0.3 architecture.

2. **[#4614 — CLI: support multiline input via Shift+Enter / Alt+Enter](https://github.com/HKUDS/nanobot/pull/4614)** (OPEN) — A UX improvement for the interactive CLI, switching from single-line to multiline-capable `PromptSession`. Likely to merge soon.

3. **[#4771 — Support document attachments in WebUI](https://github.com/HKUDS/nanobot/pull/4771)** (OPEN) — Extends WebUI to accept PDFs and other documents with MIME/size validation. This is a **strong candidate for next release** as it expands the WebUI from image-only to full document support.

4. **[#4689 — Surface OAuth status and expiry warnings](https://github.com/HKUDS/nanobot/pull/4689)** (OPEN) — Improves OAuth provider UX across CLI, WebUI, and runtime. Likely to merge as it addresses a filed issue (#4679).

5. **[#4619 — Feishu channel: system-level new session messages](https://github.com/HKUDS/nanobot/issues/4619)** (CLOSED) — Enhancement for Feishu (Lark) channel to use `msg_type system` for session divider visual effects in group chats.

**Prediction:** The next release will likely include Mattermost channel support (#4459), document attachments in WebUI (#4771), OAuth status improvements (#4689), and multiple security/stability fixes from the audit wave.

## User Feedback Summary

**Pain Points:**
- **Windows inconsistencies** (#4511, #4544): Background process tracking breaks after restart; shell command semantics differ between single-line and multi-line — severely impacts cross-platform agent development
- **Provider interoperability** (#4061, #4637): OpenAI-compatible providers with non-standard tool call formatting break agent execution; Telegram long message chunking renders previous trunks invisible
- **Configuration security** (#4803, #4796): API keys persist in plaintext and filesystem access defaults to unrestricted — users may not realize their agents have full filesystem access
- **Reliability gaps** (#4798, #4792): Concurrent file writes cause corruption; `/stop` command causes permanent message loss mid-turn

**Satisfaction Signals:**
- **Mattermost support** (#4459) merged — community demand for enterprise messaging platforms is being addressed
- **CLI UX improvements** (#4614) actively being tested — multiline input resolves a long-standing ergonomic issue
- **Rapid fix turnaround**: The 35 audit findings filed today (#4815) already have 11+ fix PRs, showing maintainers prioritize user-reported issues

## Backlog Watch

| Issue/PR | Created | Last Updated | Days Stale | Priority |
|----------|---------|--------------|------------|----------|
| [#3436 — Call external agent](https://github.com/HKUDS/nanobot/issues/3436) | 2026-04-25 | 2026-07-06 | **73 days** | Enhancement — No maintainer response |
| [#4637 — Telegram long message trunking](https://github.com/HKUDS/nanobot/issues/4637) | 2026-07-01 | 2026-07-06 | **6 days** | Bug — No fix PR yet, UI remains broken |
| [#4511 — Windows `--background` inconsistencies](https://github.com/HKUDS/nanobot/issues/4511) | 2026-06-25 | 2026-07-06 | **12 days** | Recently closed — verify fix released |
| [#4791 — No channel-level rate limiting](https://github.com/HKUDS/nanobot/issues/4791) | 2026-07-06 | 2026-07-06 | **1 day** | DoS vulnerability — No fix PR yet |
| [#4798 — Concurrent file writes corruption](https://github.com/HKUDS/nanobot/issues/4798) | 2026-07-06 | 2026-07-06 | **1 day** | Data loss risk — No fix PR yet |

**Notable:** The `restrict_to_workspace` default (`False`) (#4796) and plaintext API key storage (#4803) are **critical security issues** with no fix PRs yet submitted. These should be prioritized before any release, as they expose users to filesystem-wide access and credential theft respectively.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

⚠️ Summary generation failed.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

# PicoClaw Project Digest — 2026-07-07

## Today's Overview

PicoClaw shows **moderate activity** today with 4 issues updated and 5 pull requests in motion, though no new releases are cutting. The project’s **core provider layer** is the clear focal point: a critical Anthropic prompt caching bug (#2191) has finally received a fix PR (#3228), and a related proposal (#3229) for rolling conversation cache breakpoints signals deeper architectural thinking. The **remote agent WebSocket mode** PR (#3118) remains open after nearly a month, suggesting continued work on agent infrastructure. Overall health appears stable, with one bug fix merged (#3227) and several open discussions around provider compatibility and memory tool safety.

## Releases

**No new releases** for 2026-07-07. The latest tag remains unspecified from the preceding period.

## Project Progress

One **pull request was merged/closed** today:

- **#3227** [CLOSED] — `fix(providers): resolve tool_use name/args from Function on reloaded history`  
  Closed by **AayushGupta16**. Fixes round-trip corruption where `tool_use` blocks lost their `name` and `arguments` after chat history was serialized and reloaded, because those fields were tagged as `json:"-"`. Both Anthropic providers (`anthropic_messages` and `anthropic`) now restore tool use blocks correctly from session history.  
  [GitHub](https://github.com/sipeed/picoclaw/pull/3227)

No other PRs were closed or merged today.

## Community Hot Topics

- **#2191 (CLOSED) — [BUG] anthropic_messages provider ignores SystemParts, breaks Anthropic prompt caching**  
  *Comments: 4 | 👍: 0 | Author: whtiehack*  
  A long-standing bug (originally reported March 30) where the `anthropic_messages` provider flattens system messages to a plain string, discarding `SystemParts` content blocks. This made Anthropic’s per-block `cache_control` markers impossible to express, defeating prompt caching entirely. **Today’s fix PR #3228 directly addresses this.**  
  [GitHub](https://github.com/sipeed/picoclaw/issues/2191)

- **#3229 (OPEN) — Proposal: rolling conversation cache breakpoints for anthropic-messages**  
  *Comments: 0 | 👍: 0 | Author: AayushGupta16*  
  Extends #3228 with a design for dynamic cache breakpoints in conversation history—not just the system prompt. The author argues that in agentic workloads, conversation history dominates input tokens and should also be cacheable. This suggests a feature request for **intelligent cache invalidation** boundaries rather than static caching.  
  [GitHub](https://github.com/sipeed/picoclaw/issues/3229)

- **#3230 (OPEN) — [BUG] Function call is missing thought_signature when calling Gemini API via OpenAI compat format**  
  *Comments: 0 | 👍: 0 | Author: VictorSu000*  
  A compatibility issue specific to users routing Gemini through Cloudflare AI Gateway in OpenAI format. The error “missing thought_signature” indicates a **schema mismatch** between Gemini’s expectations and the OpenAI-compatible tool call format. Affects versions 0.2.9 through 0.3.1.  
  [GitHub](https://github.com/sipeed/picoclaw/issues/3230)

## Bugs & Stability

| Issue | Severity | Summary | Fix PR Exists? |
|-------|----------|---------|----------------|
| #3230 | **High** – blocks Gemini usage via Cloudflare AI Gateway in OpenAI format | Function calls trigger “missing thought_signature” error on Gemini | ❌ No fix PR yet |
| #3231 | **Medium** – feature gap for authenticated SearXNG | SearXNG search requires `basicauth` header; URL-embedded auth unsupported | ❌ No fix PR yet |
| #3227 | **Medium** – session history corruption for tool calls | `tool_use` blocks lost name/args after reload (fixed ✅) | ✅ Merged today |

The most impactful regression is **#3230 (Gemini+OpenAI compat)**, as it affects a multi-version range (0.2.9–0.3.1) and blocks a common deployment pattern. No fix PR has emerged yet.

## Feature Requests & Roadmap Signals

- **Rolling conversation cache breakpoints (#3229)** — A structural proposal to extend prompt caching beyond static system prompts into conversation history. If implemented, this would significantly reduce API costs and latency for long-running agent sessions. Likely candidate for the next minor version (0.4.x) given the related #3228 fix.

- **SearXNG BasicAuth support (#3231)** — A pragmatic feature request to pass authentication headers rather than URL-embedded credentials. Low complexity, high value for self-hosted search use cases. Could appear soon if a contributor picks it up.

- **Remote Pico WebSocket mode (#3118)** — Still open after 25 days. This adds `picoclaw agent --remote ws://...` functionality, enabling remote agent control. No maintainer response yet; may be awaiting review bandwidth.

## User Feedback Summary

- **Pain point: prompt cache ineffectiveness** — Issue #2191 (and the cascade of #3228→#3229) shows users are actively trying to use Anthropic’s prompt caching feature and hitting hardcoded limitations. The fix is incoming but the proposal for dynamic breakpoints indicates users want more than a basic fix.

- **Pain point: provider compatibility for Gemini** — Issue #3230 demonstrates real-world friction: users attempting to route Gemini through Cloudflare AI Gateway with OpenAI-format tools experience an opaque error. The user tested across three versions, showing frustration with regressions that persisted across releases.

- **Pain point: memory file safety** — PR #3226 (still open) addresses a subtle behavioral issue: the generic `write_file` tool used to update `MEMORY.md` framed overwrite as “replace,” coaching the model toward destructive behavior. The fix softens the guard to “append or replace.” This reflects a community desire for **safer agent memory management** without dedicated memory tools.

## Backlog Watch

- **#3118 (OPEN) — Add remote Pico WebSocket mode**  
  *Created: 2026-06-12 | Updated: 2026-07-06 | Author: jp39*  
  No maintainer comments in 25 days. This is a significant feature (remote agent control) with no visible feedback path. Risk of becoming stale.  
  [GitHub](https://github.com/sipeed/picoclaw/pull/3118)

- **#3226 (OPEN) — Stop write_file from coaching destructive overwrite**  
  *Created: 2026-07-05 | Updated: 2026-07-06 | Author: ACMYuechen*  
  A small but important safety fix for memory file management. No maintainer response yet, despite being open for two days.  
  [GitHub](https://github.com/sipeed/picoclaw/pull/3226)

- **#3230 (OPEN) — Gemini thought_signature bug**  
  *Created: 2026-07-06 | Updated: 2026-07-06 | Author: VictorSu000*  
  Zero maintainer comments so far. Affects a broad version range and a popular provider. Needs triage.  
  [GitHub](https://github.com/sipeed/picoclaw/issues/3230)

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

# NanoClaw Project Digest — 2026-07-07

## 1. Today's Overview

NanoClaw is currently in a **high-velocity documentation modernization phase**, with 10 PRs updated in the last 24 hours and 3 issues raised. The project shows strong maintainer engagement, particularly around closing a significant security policy PR (#2967) and advancing a broad docs staleness sweep across architecture, SDK, and database documentation. Activity is concentrated on **safety, correctness, and developer experience** rather than new features. The three open issues highlight both enterprise integration ambitions and a critical operational reliability gap in MCP server handling. No new releases were published today, but the accumulation of merged docs and audit-log infrastructure suggests a v2.2.0 release may be approaching.

---

## 2. Releases

**No new releases** were published in the last 24 hours. The last known commit references are `08a1ac9/v2.1.38` and `b6cb53e`, indicating the project is on v2.1.x series. The audit log feature (#2967) and significant docs rewrites may feed into a future v2.2.0.

---

## 3. Project Progress

**Two PRs were closed today:**

- **#2967 [CLOSED] feat: opt-in local audit log (AUDIT_ENABLED)** — *moshe-nanoco* — A significant feature addition: an opt-in SIEM-shaped JSON audit trail under `data/audit/` with `ncl audit list` read-back and a post-write hook registry. This addresses compliance/governance use cases. *Merged/closed 2026-07-06.*

- **#16 [CLOSED] Escape special regex characters in assistant name trigger pattern** — *gavrielc* — A bugfix ensuring special regex characters in `ASSISTANT_NAME` don't break trigger pattern matching. *Closed 2026-07-06 (originally Feb 2026).*

**Eight PRs remain open and under review**, including five documentation rewrites by glifocat, two agent-runner fixes, and the Teams-CLI credential flow PR.

---

## 4. Community Hot Topics

| Issue/PR | Comments | 👍 | Topic |
|----------|----------|----|-------|
| [#2960 Live Zoom voice agent + K-ai KB integration](https://github.com/nanocoai/nanoclaw/issues/2960) | 1 | 0 | **Enterprise voice integration proposal** |
| [#2968 MCP server failures are silent](https://github.com/nanocoai/nanoclaw/issues/2968) | 0 | 0 | **Critical operational reliability** |
| [#2967 Audit log feature](https://github.com/nanocoai/nanoclaw/pull/2967) | — | 0 | **Governance & compliance** (merged) |

**Analysis:** The Zoom voice agent proposal (#2960) signals a clear enterprise push toward real-time meeting intelligence, combining voice, KB retrieval, and action-item extraction. The MCP silent failure issue (#2968) received zero comments but represents a **dangerous trust illusion** — agents claiming success while missing tools. This needs urgent maintainer response.

---

## 5. Bugs & Stability

**High severity:**
- **#2968 [OPEN] MCP server spawn/connect failures are silent** — *explorerleslie* — When an MCP server fails to connect (bad path, missing deps, crash), the SDK silently proceeds with remaining tools and agents claim success. **No fix PR exists yet.** This is a **silent data-loss and trust bug** — users believe their agent is fully equipped when it isn't. *Zero comments; needs maintainer triage.*

**Medium severity:**
- **#2965 [OPEN] fix(agent-runner): match rate_limit_event as a top-level SDK message type** — *glifocat* — SDK 0.3.x changed rate-limit events from `system.subtype` to top-level `SDKRateLimitEvent`. Current code misses these, potentially causing mis-counting of rate limits. *Fix PR exists.*

- **#2966 [OPEN] fix(agent-runner): record provider errors as failed, and mirror failed acks** — *glifocat* — Provider errors inside consumed batches are recorded as `completed` instead of `failed`, masking failures. *Fix PR exists (draft).*

---

## 6. Feature Requests & Roadmap Signals

**Strong roadmap signals from today:**
1. **Live voice agent with Zoom RTMS integration** (#2960) — Proposes a wake-phrase triggered KB Q&A agent inside Zoom meetings, with full transcript capture and action-item extraction. This would require audio streaming, Azure OpenAI Realtime API integration, and meeting bot authorization support.
2. **Opt-in audit logging** (#2967, merged) — The compliance and SIEM-ready audit trail suggests enterprise/government deployment readiness is a priority.
3. **Teams-CLI-first credentials flow** (#2958) — Moving from 7-step Azure portal walk to `teams login` + `teams app create` signals investment in Microsoft Teams integration ease-of-use.

**Prediction for next release:** The audit log feature (#2967) and the entire docs staleness sweep (#2961–2964) may be bundled into v2.2.0. The MCP silent failure fix (#2968) should be prioritized before release.

---

## 7. User Feedback Summary

**Pain points expressed:**
- **"Agent runs apparently healthy" while missing tools** (#2968) — A user reports the trust-breaking experience of discovering their MCP-configured agent silently lacked tools. This undermines confidence in the entire agent orchestration model.
- **"I want to generate a logo"** (#2959) — The image generation request is minimal, but highlights that users expect NanoClaw-as-platform to support image creation use cases (likely via DALL-E or similar provider integration).
- **Docs staleness** — The extensive docs sweep (5 PRs) implicitly acknowledges that users were encountering out-of-date architecture, SDK, and DB documentation. The community's patience is being repaid with code-grounded rewrites.

---

## 8. Backlog Watch

| Item | Age | Status | Risk |
|------|-----|--------|------|
| [#2968 MCP server failures silent](https://github.com/nanocoai/nanoclaw/issues/2968) | 1 day | **No response from maintainers** | **Critical** — zero maintainer engagement on a reliability bug that causes silent tool loss. |
| [#1959 Image generation](https://github.com/nanocoai/nanoclaw/issues/2959) | 1 day | Open, no comments | Low — user request, not a bug. |
| [PR #2954 Security policy](https://github.com/nanocoai/nanoclaw/pull/2954) | 3 days | Open, no maintainer sign-offs yet | Medium — Phase-1 security reporting policy awaits two maintainer approvals. |

**Most concerning:** #2968 has zero comments and zero maintainer response in its first day. Given it describes a **silent failure that can mislead users about agent capabilities**, it should have been triaged within hours. This is a gap in the project's incident responsiveness for operational reliability issues.

---

**Overall Health Assessment:** Green-Yellow — Strong development velocity and documentation investment, but one critical reliability bug (#2968) lacks any maintainer acknowledgment. The documentation modernization and audit log addition are healthy signs of project maturity.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

# NullClaw Project Digest — 2026-07-07

Generated from [github.com/nullclaw/nullclaw](https://github.com/nullclaw/nullclaw)

---

## 1. Today's Overview

The NullClaw project is in a **maintenance lull** today, with no new issues, no releases, and no merged or closed pull requests in the last 24 hours. A single open dependency-bump pull request (#956) updating Alpine from 3.23 to 3.24 remains open and received its last update yesterday (2026-07-06). With zero open issues and zero closed items, the project shows no signs of active feature development or bug triage at this moment. The overall activity level is **very low**, suggesting a possible quiet period or a maintainer-focused interval. Project health appears stable but stagnant — no regressions are surfacing, but no progress is visible either.

---

## 2. Releases

**No new releases** in the reporting period. The latest release remains unknown from the data provided.

---

## 3. Project Progress

**Merged/closed PRs today: 0** — No features, fixes, or documentation changes were completed in the last 24 hours.

**Notable open PR:**  
- [#956 [OPEN] ci(deps): bump alpine from 3.23 to 3.24 in the docker-images group](https://github.com/nullclaw/nullclaw/pull/956) — Submitted 2026-06-15 by `dependabot[bot]`, last updated 2026-07-06. This dependency update would bring the Docker base image to Alpine 3.24, a routine maintenance upgrade. No comments or reviews recorded.

---

## 4. Community Hot Topics

- **Most active PR (only one):** [#956 — Bump alpine 3.23→3.24](https://github.com/nullclaw/nullclaw/pull/956) — This is the sole update in the last 24 hours. With zero comments and zero reactions, it has generated no community discussion.  
  **Underlying need:** The PR reflects a standard dependency hygiene practice — keeping Docker images current with latest stable Alpine releases for security patches and compatibility. The lack of engagement suggests either the community is small, or this update is seen as unremarkable.

**No issues** were created or updated in the reporting period.

---

## 5. Bugs & Stability

- **New bugs reported today: 0**  
- **Open bugs: 0** (from the data provided)

**Ranked severity: None.** No crashes, regressions, or stability issues have been surfaced in the past 24 hours. The project’s issue tracker shows zero open/active issues, implying either a very stable state or unreported problems.

---

## 6. Feature Requests & Roadmap Signals

**No new feature requests** were submitted in the last 24 hours. The project’s issue list is empty, providing no signals for upcoming features or roadmap direction.

**Prediction for next version:** Given the only active activity is a Docker base image bump, the next minor release will likely include this Alpine 3.24 upgrade alongside any other accumulated dependency updates. No breaking changes are anticipated from this PR.

---

## 7. User Feedback Summary

**No user feedback** was expressed in the reporting period — no comments, reactions, or user-reported pain points on issues or PRs. The absence of complaints may indicate satisfaction, but equally could reflect low engagement or limited user base. No use cases or dissatisfaction signals are available.

---

## 8. Backlog Watch

- **Long-unanswered PR:** [#956 (open since 2026-06-15)](https://github.com/nullclaw/nullclaw/pull/956) — This dependency bump has been open for **22 days** without any maintainer review, approval, or comment. While Dependabot PRs are often lower priority, a three-week wait suggests possible maintainer bandwidth constraints or a deliberate pause. **Needs maintainer attention:** merging or closing this PR would clear the only open item and demonstrate governance activity.

**No long-unanswered issues** exist, as the issue tracker is currently empty.

---

**Overall Project Health Assessment:** The project is in a **quiet but healthy** state — zero open issues suggests no known bugs, but zero merging activity over 24 hours and an unanswered dependency PR for three weeks indicate **low community and maintainer momentum**. If this pattern continues, the project risks becoming dormant.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

# IronClaw Project Digest — 2026-07-07

## Today's Overview

High activity across the IronClaw project with 41 issues updated (36 open/active, 5 closed) and 50 pull requests updated (37 open, 13 merged/closed) in the last 24 hours. Development momentum is strong, with a significant focus on the "Reborn" runtime architecture, WebUI v2 frontend migration to TypeScript, and production-hardening of the OAuth and filesystem stacks. The project is in a sustained integration push, with multiple stacked PR trains converging on gate-dispatch coverage, subagent thread-harness design, and performance auditing. No new releases were published today.

## Releases

*No new releases in the last 24 hours.* The pending release PR #5598 (`chore: release`) remains open, which would bump `ironclaw_common` from 0.4.2 to 0.5.0 (breaking changes), `ironclaw_skills` from 0.3.0 to 0.4.0 (breaking changes), `ironclaw` from 0.24.0 to 0.29.1, and several other crates. This release appears to be blocked by ongoing integration work.

## Project Progress

**13 PRs merged or closed today**, representing substantial infrastructure and feature advancement:

- **PR #5176** (merged, closed) — `docs(reborn): subagent thread harness — foundational design + PR0/PR1 plan`. Docs-only PR establishing the design for subagents as first-class, addressable, resumable threads.
- **PR #5750** (open, test-only) — `smoke micro-pinchbench-13` — benchmarking infrastructure.
- **PR #5748** (open) — `docs(reborn): canonical subagent thread-harness design` — adds the accepted design document for subagent completion-delivery and durability layer.
- **PR #5749** (open) — `feat(filesystem): CAS-guarded delete_if_version on RootFilesystem` — new CAS-delete primitive required by the subagent await-edge delivery design.
- **PR #5751** (open) — `fix(filesystem): pool libSQL connections to stop concurrent-CAS SQLITE_MISUSE (#5466)` — fixes a critical concurrency bug where parallel CAS operations caused `SQLITE_MISUSE`.
- **PR #5692** (open) — `reborn: no run-borking failures — collapsed recoverability stack` — large PR integrating the no-borking-failures release train (5 stacked PRs combined), implementing recoverable error batching, failure lane classification, model-visible failure detail, and LoopFailureKind fault matrix.
- **PR #5733** (open) — `fix(reborn): [PRODUCTION CHANGE] #5572 — forward checkpoint stage/load through HookedLoopCheckpointPort` — fixes hooks middleware where `stage_checkpoint_payload` and `load_checkpoint_payload` were unimplemented.
- **PR #5735** (open) — `Real gate-dispatch harness convergence + triggered-delivery outcome proof` — production crate change enabling harness convergence for gate-dispatch testing.
- **Four codex/WebUI PRs** (#5728, #5729, #5730, #5731, #5732) — migrating the WebUI v2 frontend from JavaScript to TypeScript, switching to pnpm, adding Vite scaffold, and embedding prebuilt assets.

## Community Hot Topics

**Most Active Issues:**

1. **[#5713 — Slack notification silent failures (CLOSED)](https://github.com/nearai/ironclaw/issues/5713)** (3 comments) — `triggered_notification_for_state` only builds Slack payloads for `Completed`/`BlockedApproval`/`BlockedAuth`, silently dropping `Failed` notifications. Root cause identified in `slack_delivery.rs`; closed likely with a fix.

2. **[#5702 — GitHub issue integration HTTP 403 (OPEN)](https://github.com/nearai/ironclaw/issues/5702)** (2 comments, bug_bash_P2) — Agent's GitHub issue search/create capabilities fail with HTTP 403 errors. Blocks all GitHub issue interaction despite configured integration.

3. **[#5553 — Approval notifications disappear (OPEN)](https://github.com/nearai/ironclaw/issues/5553)** (2 comments, bug_bash_P2) — Approval notifications flash and disappear rather than persisting in the notification history. Long-standing UX issue affecting user trust in automation workflows.

4. **[#5712 — tool_search discloses full capability catalog (OPEN)](https://github.com/nearai/ironclaw/issues/5712)** (1 comment) — Security/architecture issue where `ToolDisclosureCapabilityPort` sits inside `CapabilitySurfaceProfileFilter` and never sees the caller's `allow_set`, leaking the full catalog.

**Most Active PRs (undefined comments are likely `0` but not explicitly returned):**

- **PR #5731 ([OPEN] Move WebUI frontend source to TypeScript)** — Large (XL), experienced contributor, moving browser JS to TypeScript.
- **PR #5751 ([OPEN] fix(filesystem): pool libSQL connections)** — Core contributor, critical concurrency fix.
- **PR #5692 ([OPEN] reborn: no run-borking failures)** — Core contributor, large integrated release train.

**Underlying Need Analysis:** The community's most active issues cluster around **silent failures and poor error visibility** — Slack notifications dropping failures (#5713), approval notifications disappearing (#5553), GitHub integration returning opaque 403s (#5702), and routines showing generic errors (#5703). This pattern suggests a systemic pain point: users cannot trust automations because failures are invisible or inscrutable. The "no run-borking failures" PR #5692 directly addresses this at the runtime level.

## Bugs & Stability

**Severity: Critical**

- **#5466 (tracked) — Concurrent CAS SQLITE_MISUSE** — Parallel CAS operations causing database corruption. Fix PR **#5751** (open) pools libSQL connections to resolve.

**Severity: High**

- **#5713 [CLOSED] — Slack notifications silently drop Failed state** — Automation failures produce no Slack notification. Fix appears merged.
- **#5702 — GitHub integration HTTP 403** — Blocks all GitHub issue interaction. No fix PR identified yet.
- **#5741 — builtin.http.save fails with OutputTooLarge** — Cannot save large web pages. Configuration-level issue.
- **#5739 — Hardcoded 128K context budget** — Ignores model's actual `context_length`, caps usable context at ~50% on larger-window models.
- **#5734 — Official installers 404** — Download URLs use wrong tag format (`v{version}` vs `ironclaw-v{version}`), all downloads fail.

**Severity: Medium**

- **#5553 — Approval notifications disappear** (bug_bash_P2) — Long-standing UX/notification delivery bug.
- **#5703 — Generic routine failure errors** (bug_bash_P2) — "invalid internal instruction" instead of root cause.
- **#5708 — Error banners outside chat stream** (bug_bash_P2) — Floating error UI detaches from conversation.
- **#5707 — Routine creation exposes internal details** (bug_bash_P2) — Confirmation responses leak implementation internals.
- **#5701 — Activity panel hides tool details** (bug_bash_P2) — No real-time tool call visibility.

**Severity: Low**

- **#5694 — clientActionId() throws on insecure origins** — Breaks all mutating requests on plain HTTP.
- **#5706 — Raw thread IDs in sidebar under load** (bug_bash_P3) — Cosmetic/lag-related display issue.
- **#5705 — Terminal icon with no disable option** (bug_bash_P3) — UI customization gap.
- **#5704 — Image preview transparency during processing** (bug_bash_P3) — Minor visual glitch.

## Feature Requests & Roadmap Signals

**Active Feature Work (in-queue or in-progress):**

1. **Subagent Thread Harness** (PR #5748, PR #5176, PR #5749) — First-class, addressable, resumable subagent threads. This is a **major architectural initiative** that reframes subagents from one-shot computations to persistent threads with crash/restart survival. Expected in the next 1-2 releases.

2. **WebUI v2 TypeScript Migration** (PRs #5728-5732) — Complete frontend rewrite from JavaScript to TypeScript with Vite build tooling. Predict this lands in the next release (likely `ironclaw 0.30.x`).

3. **OAuth Wire-Format Matrix Fixes** (PR #5579, still open) — Parse robustness for spec-legal provider responses. Needed for multi-provider OAuth interoperability.

4. **Context Budget Configuration** (#5739) — Request to make the 128K token budget configurable and model-aware. Likely to be prioritized given the impact on larger models.

5. **Filesystem CAS-Guarded Delete** (PR #5749) — New primitive for subagent delivery. Will unlock the subagent PR0/PR1 merge gate.

**Predictions for Next Release:**
- The TypeScript WebUI migration (5 stacked PRs) is likely the highest-priority ship target.
- The "no run-borking failures" release train (#5692) will likely merge, dramatically improving error visibility.
- The pending release PR #5598 will unblock once the integration train stabilizes.
- Subagent thread harness (PR0) may merge as experimental.

## User Feedback Summary

**Core Pain Points (from bug_bash items this week):**

- **Silent automation failures** — Users cannot know when triggered/scheduled runs fail (#5713). The project is investing heavily in the "no-borking" runtime to address this.
- **Invisible debugging paths** — Failed routines show "no thread attached" (#5507, closed), blocking post-mortem analysis.
- **Unhelpful error messages** — Generic "invalid internal instruction" provides no diagnostic value (#5703).
- **Disappearing approval notifications** — Approval workflows are unreliable, undermining trust in human-in-the-loop automations (#5553).
- **UI/UX friction** — Error banners floating outside chat (#5708), activity panel hiding tool details (#5701), raw thread IDs under load (#5706), terminal icon that cannot be disabled (#5705), transparent images during processing (#5704).
- **Integration breakage** — GitHub issues HTTP 403 (#5702) blocks a core use case.
- **Routine creation leaks** — Responses expose internal triggers, cron, and command references to end users (#5707).

**Satisfaction Signals:**

- The active PR train on "no-run borking" (#5692) signals architectural commitment to error transparency.
- The subagent thread harness design (#5748) addresses long-standing requests for agent persistence and resumability.
- The TypeScript migration (#5731) suggests investment in frontend quality.
- Multiple coverage-gap PRs (#5738, #5740, #5743, #5723, #5661) demonstrate rigorous testing culture.

## Backlog Watch

**Critical Backlog Items Needing Maintainer Attention:**

1. **PR #5579** ([OPEN] fix(oauth): wire-format matrix fixes) — Open since July 3, 4 days. Blocks OAuth interoperability with providers that return spec-legal string-typed `expires_in`. Core contributor, experienced — needs review and merge.

2. **#5712** ([OPEN] tool_search discloses full capability catalog) — Security architecture issue. No fix PR yet. Could expose sensitive capability information through the search catalog.

3. **#5715** ([OPEN] Wiring-parity guard: extend EXPECTED_PRODUCTION_SHAPE) — Test-support wiring can silently drift from production. No fix PR yet. Integration risk.

4. **#5721** ([OPEN] Reborn: production turn-state filesystem uses with_fixed_view) — Per-user `/turns` collapse on multi-user boxes, potential CAS contention. Defense-in-depth concern for multi-tenant deployments.

5. **#5744** ([OPEN] Reborn harness: auth-resolution real dispatch arm unreachable) — Auth resolution path has no OAuth-gated-capability profile enabler. Blocks end-to-end auth flow testing.

6. **#5722** ([OPEN] Reborn: real gate-dispatch unreachable at int tier) — Interaction services read a disjoint turn-run store. Blocks integration-level testing of approval/auth dispatch arms.

**Longest-Open Items:**

- **Issue #5553** (Approval notifications disappear) — Open since July 2, 5 days with only 2 comments. Bug_bash P2 priority but no fix PR assigned.
- **Issue #5555** ([CLOSED]) and **#5556** ([CLOSED]) — Both bug_bash items closed in the last 24 hours, good closure velocity.
- **Issue #5507** ([CLOSED]) — Failed routine "no thread attached" — closed today. Good sign that bug_bash items are being addressed.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

# LobsterAI Project Digest — 2026-07-07

## Today's Overview

LobsterAI saw a surge of activity on July 6th, with **12 pull requests merged/closed** and **1 open PR** still under review. No new issues were filed, and no new releases were published. The day was dominated by **cross-area cleanup and feature work**, spanning settings UI redesign, MCP transport fixes, xAI (Grok) OAuth integration, heartbeat cost controls, email multi-account support, and cowork home screen enhancements. The project appears in a **high-velocity development phase** with multiple contributors shipping production-quality changes in parallel.

## Releases

**No new releases today.** The latest release remains unknown from this snapshot. Several merged PRs (notably #2284, #2283, #2276, #2275) contain substantial feature work that could form the basis of a future release.

## Project Progress

**12 PRs were merged or closed today**, with significant feature advancement across the stack:

**Major Features Landed:**
- **xAI (Grok) OAuth Login** (#2276) — Adds browser PKCE login against `auth.x.ai` with device-code fallback; wires credentials into OpenClaw auth-profiles; registers xAI as a selectable Grok provider. [View PR](https://github.com/netease-youdao/LobsterAI/pull/2276)
- **Heartbeat Cost-Control Policy** (#2280) — Adds a managed heartbeat policy prompt; removes proactive-heartbeat guidance from bundled templates; repairs legacy `HEARTBEAT.md` files in existing workspaces. [View PR](https://github.com/netease-youdao/LobsterAI/pull/2280)
- **Heartbeat Toggle Setting** (#2278) — Adds Settings > Agent Engine toggle for OpenClaw heartbeat (enabled by default); persists through Cowork config; writes `1h` when enabled, `0m` when disabled. [View PR](https://github.com/netease-youdao/LobsterAI/pull/2278)
- **Multi-Account Email Skill** (#2275) — Adds multi-account support for the built-in `imap-smtp-email` skill; email account management in settings with enable/disable, default account, provider presets, connectivity testing; preserves legacy `.env` compatibility. [View PR](https://github.com/netease-youdao/LobsterAI/pull/2275)
- **Time-Aware Cowork Home** (#2274) — Greets users based on time of day; surfaces recent tasks for one-click resume; polish on hover/focus feedback for quick actions and input. [View PR](https://github.com/netease-youdao/LobsterAI/pull/2274)

**UI/UX Polish:**
- Settings and cowork cleanup (#2284) — Redesigns model provider settings UI; removes home recent tasks card; archives legacy cron files; hides console window when spawning Python on Windows; allows dev server port override via `PORT` env. [View PR](https://github.com/netease-youdao/LobsterAI/pull/2284)
- Optimize skill, MCP, memory, and mail UI (#2283) — UI refinements across multiple areas. [View PR](https://github.com/netease-youdao/LobsterAI/pull/2283)

**Bug Fixes:**
- Scheduled task "no notification" channel fix & settings model-delete fix (#2256, merged today) — Fixes two bugs: scheduled task notification channel `不通知` not persisting; white screen when deleting active chat model in settings. [View PR](https://github.com/netease-youdao/LobsterAI/pull/2256)
- Prevent stale cowork sync from restarting context maintenance (#2281) — Guards against late empty-final history syncs returning errored sessions to maintenance state; adds regression coverage. [View PR](https://github.com/netease-youdao/LobsterAI/pull/2281)
- Hide bundled xAI plugin from sync (#2279) — Prevents OpenClaw built-in xAI provider plugin from appearing in user plugin sync. [View PR](https://github.com/netease-youdao/LobsterAI/pull/2279)
- Clear stale MCP transport config (#2277) — Normalizes MCP server config by transport type so stale headers/env/args are cleared when editing or switching transport. [View PR](https://github.com/netease-youdao/LobsterAI/pull/2277)

**Dependencies:**
- Pending bump: electron 40.2.1 → 43.0.0 and electron-builder update (#1277, open since Apr 2). [View PR](https://github.com/netease-youdao/LobsterAI/pull/1277)

## Community Hot Topics

No issues or PRs had recorded comments or reactions in this snapshot. The **highest-activity PR is #1277** (dependabot electron bump, open since April 2), which has been updated recently but lacks community engagement metrics. The **xAI/Grok integration** (#2276) and **multi-account email** (#2275) are likely the most anticipated features by users, but no direct community signal is visible in today's data.

## Bugs & Stability

**Bugs Fixed Today (ranked by severity):**

| Severity | Bug | Fix PR | Status |
|----------|-----|--------|--------|
| **High** | White screen when deleting active chat model in settings | #2256 | Merged |
| **High** | Stale cowork sync could restart context maintenance after chat errors | #2281 | Merged |
| **Medium** | Scheduled task "no notification" channel not persisting after save | #2256 | Merged |
| **Medium** | Empty/missing `HEARTBEAT.md` triggers periodic model calls unnecessarily | #2280 | Merged |
| **Low** | Stale MCP transport headers/env/args not cleared on transport switch | #2277 | Merged |
| **Low** | Bundled xAI plugin appearing in user plugin sync | #2279 | Merged |

No new bugs were reported today via Issues. All fixes came from self-identified code improvements by contributors.

**Stability Concern:** The white screen fix (#2256) and the cowork context maintenance race condition (#2281) both addressed potentially user-disruptive bugs that could cause data loss or application crashes.

## Feature Requests & Roadmap Signals

Based on merged PRs today, the following features indicate roadmap priorities:

1. **xAI/Grok Provider Support (#2276)** — Likely to be in next release; brings a major third-party model provider into the platform.
2. **Multi-Account Email Skill (#2275)** — Major UX improvement for email-heavy workflows; preserves backward compatibility.
3. **Heartbeat Cost Controls (#2278, #2280)** — Addresses API cost management for agent heartbeat calls; likely driven by user feedback on unexpected API usage.
4. **Cowork Home Enhancements (#2274)** — Time-aware greetings and recent task cards improve daily usability.
5. **MCP Transport Cleanup (#2277)** — Indicates MCP is becoming more critical, requiring better config management.

**Prediction:** The next release will likely include xAI provider support, multi-account email, heartbeat policy controls, and the MCP fixes. The electron bump (#1277) may also be fast-tracked if security fixes are required.

## User Feedback Summary

No direct user feedback was captured in today's Issues or PR comments. However, several PRs implicitly address user pain points:

- **Unwanted API costs** → #2278 and #2280 give users control over heartbeat frequency
- **Model deletion risking crash** → #2256 prevents white screen on model delete
- **Email configuration complexity** → #2275 adds multi-account UI with provider presets and connectivity testing
- **Scheduled notifications unreliable** → #2256 fixes notification channel persistence
- **Windows users** → #2284 hides the Python console window on Windows

These fixes suggest users are actively deploying LobsterAI in production environments where reliability, cost control, and multi-account management are critical.

## Backlog Watch

**Long-unanswered PR requiring attention:**

- **#1277 — `chore(deps-dev): bump the electron group`** — Open since April 2, 2026 (3+ months). Bumps electron from 40.2.1 to 43.0.0 (major version jump). Dependabot has kept it updated, but it remains unmerged. This may require manual intervention if breaking changes are introduced. [View PR](https://github.com/netease-youdao/LobsterAI/pull/1277)

**No long-unanswered Issues** are present in this snapshot.

**Observation:** The project lacks open Issues entirely, which is unusual for an active project. This may indicate that issues are being resolved before this snapshot was taken, or that the project uses a different tracking mechanism for bug reports and feature requests beyond GitHub Issues.

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyagi">TinyAGI/tinyagi</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

Here is the Moltis project digest for **2026-07-07**.

---

## Moltis Project Digest – 2026-07-07

### 1. Today's Overview
The project is in a **stable maintenance phase** with no new issues or releases in the last 24 hours. Activity was concentrated on pull requests: five PRs were updated, with **three merged/closed** and **two still open**. The merged work focused on fixing Docker volume conflicts, resolving Telegram streaming edge-cases, and upgrading the WhatsApp integration to support modern LID-native addressing. The open PRs address an MCP OAuth authentication bug and a routine dependency bump. Overall, the project shows healthy, incremental progress with no signs of regression or community distress.

### 2. Releases
**None.** No new releases were published since the last digest.

### 3. Project Progress
Three pull requests were **merged/closed** in the last 24 hours:

- **#1122 – fix: drop VOLUME declarations that shadow the home bind mount** (closed)  
  Removed problematic `VOLUME` directives from the Dockerfile that prevented bind mounts of the entire `/home/moltis` directory. This fixes a common deployment pain point for users running custom home configurations.

- **#1113 – hotfix(telegram): stream final replies without completion notify** (closed)  
  Fixes a Telegram streaming regression where, when completion notifications were disabled, the final message was not streamed correctly. Restores expected edit-in-place behavior.

- **#1144 – feat(whatsapp): bump whatsapp-rust 0.5 -> 0.6 with LID-native addressing** (closed)  
  Upgrades the WhatsApp bridge to use LID-based addressing (WhatsApp’s new identity model). This fixes both inbound message delivery after device re-registration and outbound message failures to migrated peers.

### 4. Community Hot Topics
- **#1120 [OPEN] fix(mcp): use direct fetch for resource_metadata URL from WWW-Authenticate**  
  *Author: xzavrel*  
  This PR aims to fix a critical bug where MCP OAuth integration fails with `invalid_target` for servers like Notion and Linear. The root cause is that `discover_and_register()` incorrectly passes the `resource_metadata` URL, causing authentication handshake failures. This has been open since June 13 and is actively pending review.

- **#1087 [OPEN] chore(deps): bump tar from 0.4.45 to 0.4.46**  
  *Author: dependabot[bot]*  
  A routine dependency update that has been open since May 29. The long wait suggests maintainers are either cautious about the tar crate or this is a low-priority bot PR.

### 5. Bugs & Stability
No new bugs, crashes, or regressions were reported in the last 24 hours.

**Existing open bug of note** (carried over):
- **PR #1120 – MCP OAuth `invalid_target` failure** (severity: **high**)  
  Affects users of Notion and Linear MCP servers. The fix PR exists but has not been merged yet.

### 6. Feature Requests & Roadmap Signals
The **WhatsApp LID-native addressing upgrade** (PR #1144) is a strong roadmap signal. It indicates Moltis is keeping pace with WhatsApp’s infrastructure changes, which is important for any user relying on the WhatsApp integration. There are no explicit user-submitted feature requests in the current data, but the Telegram hotfix (#1113) hints at increasing use of streaming completion workflows.

**Prediction:** The next minor release will likely include both the Telegram streaming fix (#1113) and the WhatsApp LID upgrade (#1144). The MCP OAuth fix (#1120) is also a strong candidate for inclusion, pending review.

### 7. User Feedback Summary
There is no direct user feedback (e.g., comments, reactions) recorded in the last 24 hours. However, the **Docker volume fix (#1122)** and the **Telegram streaming hotfix (#1113)** both address real, previously reported pain points:
- Users deploying with custom home directories were blocked by Docker volume shadowing.
- Telegram users relying on streaming without completion notifications lost final replies.

The **WhatsApp LID fix (#1144)** likely resolves user complaints about message failures after device re-registration, a common friction point in WhatsApp integrations.

### 8. Backlog Watch
- **PR #1087 – `tar` crate dependency bump**  
  *Opened: 2026-05-29 | Age: 38 days*  
  A simple bot PR that is pending for over a month. No security vulnerability is flagged, but long-standing unmerged dependency bumps can become a maintenance drag. A maintainer should review and merge.

- **PR #1120 – MCP OAuth resource_metadata fix**  
  *Opened: 2026-06-13 | Age: 24 days*  
  This is the most important open PR. It addresses a functionality-blocking bug for a prominent use case (Notion/Linear MCP servers). The PR has no comments from maintainers, which is a concern. This needs a review decision to avoid leaving users blocked.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

# CoPaw Project Digest — 2026-07-07

## 1. Today's Overview

CoPaw shows **very high activity** today with 34 issues updated and 50 PRs updated in the last 24 hours, signaling a project in active development. The team shipped a patch release (v1.1.12.post3) to fix an ACP compatibility regression affecting 1.x users, while the backend is processing a large wave of regression tests — 5 open PRs from hanson-hex add over 350 unit tests across inbox, channels, approvals, runtime/security, and console modules. The open-to-closed ratio (25 open vs 9 closed issues, 25 open vs 25 merged/closed PRs) indicates a healthy but strained triage pipeline, with several high-severity bugs (auto-memory, context compression, mobile UI truncation) still awaiting resolution.

## 2. Releases

### v1.1.12.post3 — Patch Release
- **Changes:** Pinned `agent-client-protocol` to `>=0.9.0,<0.11.0` to resolve a breaking import error (`SetSessionModelResponse` missing) that caused QwenPaw 1.x to malfunction with newer ACP releases.
- **Breaking Changes:** None.
- **Migration Notes:** No migration required; users on the 1.x line will get the fix automatically via pip. The ACP pin is forward-compatible within the specified range.

## 3. Project Progress

**Merged/Closed PRs today (25 total):** Key advances include:
- **#5818** (rayrayraykk): Shipped the v1.1.12.post3 patch with ACP pin.
- **#5768** (manjieqi): Fixed naive datetime in `AgentMdManager.list_working_mds()`/`list_memory_mds()` by adding `timezone.utc`, preventing frontend misparsing.
- **#5769** (elain0205): Fixed double `/api` prefix bug in console routes causing 404 for workspace commands.
- **#4820** (jc200808): Long-standing PR fixing inline source URL normalization in media blocks during context compaction.

**Feature advances in open PRs:** The memory/reranker ecosystem is converging with two competing approaches — #5669 (qwen3-rerank via DashScope) and #5692 (standard reranker on reme0.4) — both under review. A comprehensive scroll context protection strategy (#5765) addresses three issues simultaneously, including stale pinned messages in long-lived IM sessions.

## 4. Community Hot Topics

### Most Active Issues

1. **[#5757] Feishu message no reply** (11 comments) — User reports Feishu (Lark) bot receives messages but produces zero responses after the first reply in both Docker and AgentScope Platform instances. This is a **recurring channel reliability complaint** with high user frustration.

2. **[#5401] Console crashes on large tool-use sessions** (9 comments) — Frontend white-screens when opening sessions with extensive tool-call history due to `DataContent` type mismatch between backend API and frontend renderer. Root cause identified; no fix PR yet.

3. **[#5273] v2.0.0 Pre-release Bug Tracker** (5 comments, 👍1) — Central tracking issue for v2.0.0-alpha.1 regressions. The maintainer (@rayrayraykk) is using this to consolidate pre-release bug reports.

4. **[#5253] Custom channel listener dies on save** (5 comments) — Every save to a custom channel kills its listener, requiring manual restart. Despite being open since June 17, no fix PR exists.

5. **[#5725] Browser stuttering during streaming** (4 comments) — User reports severe browser lag during streaming output that resolves after completion, with DeepSeek web cited as a smooth benchmark.

### Community Pulse
The **QwenPaw GitHub Issue Feedback Assistant Skill** (#5567, 👍2) by tecgic highlights grassroots attempts to improve issue quality — it auto-generates standard-format issues from natural language complaints. This signals both community engagement and frustration with the existing issue submission friction.

## 5. Bugs & Stability

### High Severity

| Issue | Description | Fix PR? |
|-------|-------------|---------|
| **#5775** — Auto-memory never triggers | `MemoryMiddleware` state lost across per-request agent rebuilds; `auto_memory_interval > 1` silently does nothing | #5815 (open) attempts to fix by moving state to memory manager |
| **#5787** — Mobile web UI bottom truncated | Content cut off on all pages (phones/tablets); hat box buttons invisible and unclickable | None yet |
| **#5789** — Context compression crashes on JSON Schema violation | Model output exceeds `maxLength: 200` in structured compression output, raising `jsonschema.validate()` exception | None |
| **#5782** — Google Gemini embedding `index=None` (CLOSED) | OpenAI-compatible endpoint returns `Embedding.index=None` → `TypeError`; vector search silently falls back to keyword search | Closed — likely fixed in pending commit |

### Medium Severity

| Issue | Description | Fix PR? |
|-------|-------------|---------|
| **#5771** — `model_factory.py` WARNING log spam | Debug logs incorrectly use WARNING level for assistant message blocks, flooding logs | None |
| **#5784** — Context threshold shows wrong value | Same model ID across multiple providers shows incorrect `max_input_length` in UI | #5822 (open) |
| **#5790** — Loading spinner persists after response | Console input-box spinner never disappears after Agent completes | None |
| **#5776** — Stale pinned message as active task | Long-lived QQ/IM sessions treat week-old pinned messages as current task | #5765 (open) addresses |
| **#5781** — Offline code mode can't preview files | Requires online resource download even when offline | None |

### Low Severity / Minor

- **#5788** — Skills list shows only 20 items, scroll-to-load broken (CSS overflow limitation)
- **#5767** — Architecture limitation: single-session pull model blocks multi-agent evolution

## 6. Feature Requests & Roadmap Signals

### Likely for Next Release
- **Granular `rejects_media` capability** (#5821) — Change from all-or-nothing to per-media-type stripping. Small, well-defined change ideal for a point release.
- **Multi-user account management** (#5780) — Request for team member management beyond single Bot-account authentication. Cited as blocker for enterprise adoption.
- **Timed task result popup toggle** (#5797) — User backlash against the all-or-nothing approach to cron notifications; wants per-task popup control.
- **WeChat channel auto-refresh in Console** (#5795) — Real-time new message display when received via WeChat channel.

### Longer-Term Roadmap Signals
- **Zalo Bot channel support** (#5168) — Vietnamese community request; Telegram-like integration for local users.
- **Recording-aware memory ranking** (#5316) — Already has a feature PR and community interest, but implementation is still in design.
- **Skills list infinite scroll fix** (#5788) — Underlying UX issue with progressive rendering.

## 7. User Feedback Summary

### Positive / Constructive Signals
- **Passionate users:** Issue #5797 explicitly demands *more* control instead of the maintainer removing features that some users find annoying (cron popups). Phrases like "不要因噎废食" (don't throw out the baby with the bathwater) indicate deep engagement.
- **Community tooling:** #5567 (Issue Feedback Assistant) was created by a user to help others submit better bugs — a strong sign of community investment.
- **Third-party integration desire:** Vietnamese users requesting Zalo (#5168), and general enthusiasm for multi-workspace support (#5767).

### Pain Points & Dissatisfaction
- **Channel reliability is the top complaint:** Feishu (#5757), custom channel (#5253), OCG provider (#5773) all suffer from silent failures, timeouts, or listener death.
- **Streaming performance disappoints:** #5725 explicitly compares unfavorably to DeepSeek's web interface.
- **Memory/context system is confusing and fragile:** Four open issues (#5775, #5710, #5776, #5789) all touch different failure modes of the same system.
- **Mobile experience is broken:** #5787 describes an unusable truncated UI on phones/tablets.
- **v2.0.0 pre-release quality concerns:** #5273 tracker accumulating reports, combined with #5769 (double /api prefix 404), suggests beta QA gaps.

### Unmet User Needs
- Users want **toggle-based choices** not developer-decided defaults (#5797).
- Users want **offline-first tools** (#5781) — code mode shouldn't require internet for file preview.
- Users want **real-time UI updates** without manual page switching (#5795).

## 8. Backlog Watch

### Stale Important Issues Needing Attention

| Issue | Days Open | Summary | Risk |
|-------|-----------|---------|------|
| **#5168** — Zalo Bot channel | 24 days | Request for Vietnamese platform integration. No maintainer response. | Community alienation; missing entire market |
| **#5253** — Custom channel listener dies on save | 20 days | Critical reliability bug; user must re-save config after every edit | Channel reliability hit |
| **#5401** — Console crash on large tool-use sessions | 14 days | Frontend white-screen; root cause identified but no fix PR | User data loss risk |
| **#5710** — Context compression destroys critical anchor messages | 6 days | Loss of channel awareness, task context after compression — high severity | Production safety issue |
| **#5787** — Mobile web UI bottom truncated | 2 days (new) | Completely broken mobile experience | Bad first impression |

### PRs Requiring Maintainer Decision

- **#5669** vs **#5692** — Two competing reranker implementations for memory search. Both are "Under Review" and need a decision on which (or both) to merge.
- **#5765** — Comprehensive scroll context fix covering 3 bugs; supersedes #5747. Needs final review as it addresses the critical #5776 (stale pinned messages).
- **#5654** — DingTalk delivery surface errors; open since June 30, awaiting merge to fix #5566.

### Note
The **hanson-hex** regression test PR series (#5807–#5813) represents a significant test infrastructure investment — 5 PRs adding 350+ test cases. These should be prioritized to reduce the risk of regressions in the active development cycle.

---

*Generated from CoPaw GitHub data (agentscope-ai/QwenPaw) for 2026-07-07*

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

Here is the ZeroClaw project digest for July 7, 2026.

---

### ZeroClaw Project Digest | 2026-07-07

**Report generated from 50 updated issues and 50 updated pull requests across the zeroclaw-labs/zeroclaw repository.**

### 1. Today's Overview

ZeroClaw is in a period of high-intensity development and stabilization, with 50 issues and 50 PRs updated in the last 24 hours. The project is actively addressing critical stability and security bugs while simultaneously landing major new features, particularly around a "goal-mode" architecture and real-time voice channels. The community is highly engaged, driving discussions on tool discovery, provider compatibility, and channel configuration. Two significant long-standing bugs (MCP tool visibility and Telegram channel setup) remain the top workflow blockers, with fix PRs or dedicated trackers now in progress.

### 2. Releases

No new releases were published in the last 24 hours.

### 3. Project Progress

Nine PRs were either merged or closed today, reflecting a steady stream of improvements:

- **CI & Security Hardening:**
    - **PR #8776**: `fix(ci): make local gates workspace-aware`. Makes the local Rust quality gate run clippy against the full workspace, preventing broken member-crate code from landing.
    - **PR #8781**: `fix(security): remove stale advisory ignores`. Clears 18 stale `cargo-deny` advisory entries to unblock the Security CI gate.
- **User Experience (ZeroCode TUI):**
    - **PR #8779**: `fix(zerocode): use daemon final text when no streaming text was accumulated`. Fixes a silent text loss issue in streaming sessions.
    - **PR #8777**: `fix(zerocode): strip markdown fences from code block copy text`. Improves the copy-paste experience for code blocks.
    - **PR #8778**: `chore: Optimize images`. Reduces repository asset sizes.
- **Runtime & Tools:**
    - **PR #8676** (Open): `feat(cron): expose per-cron-job uses_memory flag`. Exposes the `uses_memory` flag in CLI, tools, and the Gateway API, allowing cron jobs to be memory-aware. This feature is live but the PR remains open for review.
    - **PR #8630**: `docs(sop): correct cron trigger dispatch status`. Fixes documentation regarding how cron triggers are dispatched.

### 4. Community Hot Topics

The community is most actively discussing two major subject areas:

- **Bug: MCP Tools Missing from TUI** ([Issue #8193](https://github.com/zeroclaw-labs/zeroclaw/issues/8193)) - **16 comments**. A critical S1 (workflow blocked) bug where MCP tools are visible to the Gateway but not received by ZeroCode TUI sessions. This is the single most discussed issue, indicating a significant user-facing reliability problem in the tool discovery pipeline. A regression guard PR ([#8775](https://github.com/zeroclaw-labs/zeroclaw/pull/8775)) has been submitted to prevent this from recurring.

- **RFC: Work Lanes & Board Automation** ([Issue #6808](https://github.com/zeroclaw-labs/zeroclaw/issues/6808)) - **13 comments**. A governance RFC focused on streamlining project management for maintainers. Its high engagement suggests the community values better visibility into the project's workflow and priorities.

Other notable discussions:
- **RFC: OpenAI Chat Completions Adapter** ([Issue #8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603)) - A new RFC proposing an API adapter to allow OpenAI-compatible clients to connect, signaling community demand for broader integration.
- **Goal Mode Implementation** ([Issue #8681](https://github.com/zeroclaw-labs/zeroclaw/issues/8681)) - A tracker with 8 comments coordinating the split of the goal-mode feature into reviewable PRs, showing active architectural progress.
- **Napcat/OneBot Channel Request** ([Issue #2503](https://github.com/zeroclaw-labs/zeroclaw/issues/2503)) - A long-standing feature request with 9 comments requesting bot platform support, indicating a specific user base need.

### 5. Bugs & Stability

The project resolved or is actively addressing several high-severity bugs:

- **S1 - Workflow Blocked:**
    - **MCP Tool Discovery** ([Issue #8193](https://github.com/zeroclaw-labs/zeroclaw/issues/8193)): MCP tools missing in TUI. **Status:** PR [#8775](https://github.com/zeroclaw-labs/zeroclaw/pull/8775) provides a regression test.
    - **Telegram Channel Config** ([Issue #8505](https://github.com/zeroclaw-labs/zeroclaw/issues/8505)): Channel setup fails, bot unresponsive. **Status:** Open, active P1.
    - **Malformed Tool-Call Arguments** ([Issue #8675](https://github.com/zeroclaw-labs/zeroclaw/issues/8675)): Malformed tool arguments sent to OpenAI-format providers cause 400 errors and empty replies. **Status:** Open, P1.
- **S2 - Degraded Behavior:**
    - **Headless SOP Engine** ([Issue #8631](https://github.com/zeroclaw-labs/zeroclaw/issues/8631)): SOP steps falsely recorded as "Completed." **Status:** Closed, fixed.
    - **UTF-8 String Truncation** ([Tracker #7828](https://github.com/zeroclaw-labs/zeroclaw/issues/7828)): Ongoing audit for byte-boundary safety.
- **Recently Fixed:**
    - **Dashboard** ([Issue #7523](https://github.com/zeroclaw-labs/zeroclaw/issues/7523)): Dashboard not available. **Status:** Closed.
    - **SOP Gate Bypass** ([PR #8747](https://github.com/zeroclaw-labs/zeroclaw/pull/8747)): Fix submitted to prevent advancing SOP runs past approval gates.
    - **CI Gate Failures** ([Issue #8753](https://github.com/zeroclaw-labs/zeroclaw/issues/8753)): Broken code can land on master. **Status:** Active, with PR [#8776](https://github.com/zeroclaw-labs/zeroclaw/pull/8776) fixing the root cause.

### 6. Feature Requests & Roadmap Signals

The roadmap is clearly focused on two major areas for the v0.8.3 and v0.9.0 milestones:

- **Goal Mode (Trackers #8681, #7320)**: The implementation of a "goal-mode" architecture is being split into small, reviewable PRs (e.g., [#8688](https://github.com/zeroclaw-labs/zeroclaw/pull/8688), [#8689](https://github.com/zeroclaw-labs/zeroclaw/pull/8689), [#8746](https://github.com/zeroclaw-labs/zeroclaw/pull/8746)). This is a major architectural shift likely to land in the next release.
- **Real-time Voice Channels (Issues #7943, #7944, #8780)**: A significant push toward multimodal interaction, including a backend-agnostic voice host and a physical voice satellite device. This suggests ZeroClaw is targeting hardware/home-assistant use cases.
- **OpenAI API Adapter (Issue #8603)**: An RFC for a compatibility layer is generating interest. This feature, if accepted, would greatly lower the barrier for new integrations.

**Prediction:** "Goal Mode" and the related "Goal Command Admission" are the most likely candidates for the v0.8.3 release. The OpenAI adapter RFC has the potential to be a fast-track feature for v0.9.0.

### 7. User Feedback Summary

- **Positive Signals:**
    - Community is actively contributing to the project's governance (RFC #6808).
    - Users are requesting first-class integration with other tools (Agent Skills logo, OpenAI API adapter).
- **Pain Points & Dissatisfaction:**
    - **Tool Reliability:** The MCP tool visibility bug (#8193) is frustrating for users who rely on MCP servers, as tools that are configured appear to be "missing" in the primary user interface.
    - **Setup Friction:** The Telegram channel bug (#8505) and the long-standing request for a Napcat channel (#2503) indicate that initial setup and non-standard channel configuration are a source of user frustration.
    - **File Handling:** Users are reporting issues with `file_read` for non-UTF-8 encodings (#7521), which is a common pain point for developers and operators working with legacy systems.

### 8. Backlog Watch

Several high-importance items remain open and would benefit from maintainer attention:

- **High Risk / Needs Review:**
    - **RFC: Plugin Permission Model** ([Issue #8398](https://github.com/zeroclaw-labs/zeroclaw/issues/8398)): Open questions about the plugin security model. A decision here is critical for the WASM/plugin platform roadmap.
    - **RFC: OpenAI Chat Completions Adapter** ([Issue #8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603)): A large feature RFC with no maintainer decision yet.
    - **Feature: Per-Chat Model Switching** ([Issue #8600](https://github.com/zeroclaw-labs/zeroclaw/issues/8600)): A popular request (1 👍) with no maintainer review.
- **Aging but Active:**
    - **Feature: Add ZeroClaw Logo to Agent Skills** ([Issue #5262](https://github.com/zeroclaw-labs/zeroclaw/issues/5262)): A low-effort, high-visibility feature request from April that is still open and accepted.
    - **Feature: Inject Agent Alias into Prompt** ([Issue #6311](https://github.com/zeroclaw-labs/zeroclaw/issues/6311)): A key multi-agent UX improvement from May, accepted but still open.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*