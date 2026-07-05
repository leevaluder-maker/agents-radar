# OpenClaw Ecosystem Digest 2026-07-05

> Issues: 500 | PRs: 500 | Projects covered: 13 | Generated: 2026-07-05 02:07 UTC

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

# OpenClaw Project Digest — 2026-07-05

## 1. Today's Overview

The OpenClaw project shows intense activity with the daily data cap reached on both issues (500) and pull requests (500), indicating a highly engaged developer and user community. There are 456 open/active issues and 343 open PRs, with 44 issues and 157 PRs closed or merged in the last 24 hours. No new releases were published today, suggesting the team is in a heavy development and stabilization cycle. The project is processing significant community feedback with dozens of critical bugs (P0/P1) actively being discussed, though some long-standing issues remain open and require maintainer triage attention.

## 2. Releases

**No new releases in the last 24 hours.** The last known version referenced in issue reports is OpenClaw 2026.3.13 (stable), released March 13, 2026. The project appears to be in a mid-cycle development phase with no immediate release imminent.

## 3. Project Progress

**Merged/Closed PRs Today (157):** A substantial number of fixes and improvements were merged, including:

- **Critical reliability fixes:**
  - [#100136](https://github.com/openclaw/openclaw/pull/100136) — Hides duplicate channel delivery mirrors in Slack conversations, preventing message noise
  - [#100138](https://github.com/openclaw/openclaw/pull/100138) — Fixes Codex to fail closed on unknown projector events instead of silently succeeding
  - [#100050](https://github.com/openclaw/openclaw/pull/100050) — Fixes session-maintenance warning deduplication when zero-valued fields change
  - [#100013](https://github.com/openclaw/openclaw/pull/100013) — Prevents subagent truncation from exceeding max display length
  - [#100096](https://github.com/openclaw/openclaw/pull/100096) — Fixes session warning duration display (rolling units correctly across boundaries)

- **Infrastructure & quality of life:**
  - [#100083](https://github.com/openclaw/openclaw/pull/100083) — Updates oxlint/tsgolint linting rules for safer code quality enforcement
  - [#100122](https://github.com/openclaw/openclaw/pull/100122) — Enables array fill lint rule across 20+ channel modules to prevent shared mutable object bugs
  - [#88962](https://github.com/openclaw/openclaw/pull/88962) — Completes `preserveKeys` implementation for session maintenance (previously incomplete)
  - [#98831](https://github.com/openclaw/openclaw/pull/98831) — Removes stale Anthropic replay thinking plumbing after earlier architecture change

- **Channel fixes:**
  - [#77912](https://github.com/openclaw/openclaw/pull/77912) — Proper binary file delivery for xlsx/csv/zip via chat (Sandpaw Bug #9b)
  - [#77619](https://github.com/openclaw/openclaw/pull/77619) — Mattermost now includes thread files in inbound media processing
  - [#85571](https://github.com/openclaw/openclaw/pull/85571) — Recovers orphaned terminal-progress embedded runs at 60-second timeout

**Notable open PRs advancing key features:**
- [#100140](https://github.com/openclaw/openclaw/pull/100140) (XL feature) — Enables assistants to remember across private conversations (closes #99611)
- [#99059](https://github.com/openclaw/openclaw/pull/99059) (XL refactor) — Extracts reusable AI runtime package for model protocol adapters
- [#100125](https://github.com/openclaw/openclaw/pull/100125) (XL fix) — Fixes DashScope/Moonshot endpoint misclassification when provider plugin is not installed
- [#99686](https://github.com/openclaw/openclaw/pull/99686) — Classifies doctor fix recommendations with policy metadata

## 4. Community Hot Topics

**Most Active Issues (by comment activity):**

1. **[#44925](https://github.com/openclaw/openclaw/issues/44925) — "Subagent completion silently lost"** (20 comments, Diamond Lobster severity)
   - **Analysis:** Users report a critical orchestration failure where subagent task results vanish without notification, retries, or auto-restart. This is the most discussed active issue and represents a fundamental trust-breaker for multi-agent workflows. The discussion reveals three distinct failure patterns with error codes. **Underlying need:** Operators require guaranteed delivery of subagent results in production pipelines; silent data loss makes multi-agent orchestration unreliable for any serious use.

2. **[#48788](https://github.com/openclaw/openclaw/issues/48788) — "Centralized filename encoding utility"** (18 comments)
   - **Analysis:** Users pushing for a proper architectural solution to filename encoding in Content-Disposition headers, moving beyond the Chinese UTF-8 fix (PR #48578) to cover Shift-JIS, EUC-KR, GB18030, and others. **Underlying need:** Global teams need reliable file exchange across channels — this is an internationalization/inclusion issue that blocks non-English-speaking users.

3. **[#22676](https://github.com/openclaw/openclaw/issues/22676) — "Signal daemon stop() race condition"** (17 comments, ages since Feb 2026)
   - **Analysis:** A long-standing P1 bug where gateway restarts create orphaned processes and port conflicts. The age of this issue (5 months) is concerning. **Underlying need:** Production operators need safe hot-reload of configuration without service disruption. This remains one of the oldest P1 bugs.

4. **[#22438](https://github.com/openclaw/openclaw/issues/22438) — "Tiered bootstrap file loading"** (17 comments)
   - **Analysis:** Users want progressive context management where bootstrap files don't waste LLM tokens in irrelevant sessions (sub-agents, cron jobs). **Underlying need:** Cost optimization and context window efficiency — users paying per-token want granular control over what gets loaded into each session type.

5. **[#32473](https://github.com/openclaw/openclaw/issues/32473) — "Control UI requires device identity"** (17 comments, 5 👍, CLOSED)
   - **Analysis:** This regression-blocking issue was closed, which is positive news. Users deploying on VPS with Docker were unable to access the control UI without HTTPS/localhost. The resolution suggests improved auth flow for headless deployments.

**Most Reacted Issue:**
- **[#32473](https://github.com/openclaw/openclaw/issues/32473)** — 5 reactions, indicating high user impact for VPS/Docker deployments
- **[#33413](https://github.com/openclaw/openclaw/issues/33413)** — "Slack: Show tool-level progress" — 3 reactions, users want better Slack UX
- **[#48920](https://github.com/openclaw/openclaw/issues/48920)** — "Live Docs are ahead of release" — 3 reactions, docs-reference confusion

## 5. Bugs & Stability

**Critical (P0):**
- **[#99594](https://github.com/openclaw/openclaw/issues/99594) — "Cloud instance shows 'out of credits' with $109 balance"** — Active Pro plan users unable to use their paid accounts. This is likely a cloud infrastructure billing/cache issue. No fix PR visible. **Status:** Needs immediate cloud-team escalation.
- **[#48920](https://github.com/openclaw/openclaw/issues/48920) — "Live Docs are ahead of release"** — Documentation references `IsolatedSessions` that doesn't exist in stable release 2026.3.13. **Status:** Documentation/versioning mismatch causing user confusion and feature-availability frustration.

**Critical (P1):**
- **[#44925](https://github.com/openclaw/openclaw/issues/44925) — Subagent completion silently lost** — No fix PR linked; has fix-shape-clear and linked-pr-open labels but no concrete resolution path visible
- **[#22676](https://github.com/openclaw/openclaw/issues/22676) — Signal daemon race condition** — No updated fix PR; 5 months old. **Fix PR exists:** None linked.
- **[#43367](https://github.com/openclaw/openclaw/issues/43367) — Multi-agent orchestration unstable** — Concurrent config overwrites, session-lock failures. **Fix PR:** [#100120](https://github.com/openclaw/openclaw/pull/100120) addresses the model-not-found hint for bundled providers but not the core orchestration issue.
- **[#48003](https://github.com/openclaw/openclaw/issues/48003) — Steer mode does not inject mid-turn** — Regressed in commit 9889c6da5. **Fix PR:** None visible; linked PR is open.
- **[#52249](https://github.com/openclaw/openclaw/issues/52249) — ACP parent session stuck until refresh** — UI deadlock after child completion. **Fix PR:** None.
- **[#54488](https://github.com/openclaw/openclaw/issues/54488) — Session lane starvation** — Followup drain blocks inbound dispatch for 20-30 minutes. **Fix PR:** None.
- **[#49876](https://github.com/openclaw/openclaw/issues/49876) — Cron sessions hallucinate output** after tool failures. **Fix PR:** None.
- **[#51396](https://github.com/openclaw/openclaw/issues/51396) — clearUnboundScopes strips operator scopes** for non-local token-auth clients — regression in 2026.3.13. **Fix PR:** None.

**High Severity (P2 with security/data-loss impact):**
- **[#43996](https://github.com/openclaw/openclaw/issues/43996) — Sandbox container exits immediately** with `no-new-privileges` (operation not permitted) — critical security sandbox regression. **Fix PR:** None.
- **[#45740](https://github.com/openclaw/openclaw/issues/45740) — gh-issues skill prompt injection** — Untrusted issue body injected directly into sub-agent prompts, a security vulnerability. **Fix PR:** None.
- **[#50090](https://github.com/openclaw/openclaw/issues/50090) — Community Skill Development & ClawHub** — The gap between promise and practice for the skills ecosystem. Not a bug but a structural issue. **Fix PR:** None.

**Today's Notable Bug Reports:**
- **[#100117](https://github.com/openclaw/openclaw/pull/100117)** — Open PR fixing TUI embedded event listener failures (async boundary causing silent crashes)
- **[#100135](https://github.com/openclaw/openclaw/pull/100135)** — Open PR fixing spill-file pointer loss during history elision and truncated web_fetch output

## 6. Feature Requests & Roadmap Signals

**Most-requested features by community engagement:**

1. **Memory Management Overhaul ([#43747](https://github.com/openclaw/openclaw/issues/43747))** — 9 comments, high confusion: "Memory management is in chaos." Users report inconsistent behavior (different chunking/embedding strategies, different storage locations between team members). **Prediction:** Likely to be addressed in next minor release as a UX/stability priority.

2. **Community Skill Ecosystem ([#50090](https://github.com/openclaw/openclaw/issues/50090))** — 15 comments, 2 👍. The ClawHub vision exists but the execution gap is wide. Users want publishable, installable community skills. **Prediction:** Partially addressed in 2026.4.x if the roadmap prioritizes ecosystem growth.

3. **Pre-response Enforcement Hooks ([#13583](https://github.com/openclaw/openclaw/issues/13583))** — 12 comments, 2 👍. Users want mechanical hard gates for tool-call policies in high-stakes workflows (finance, security, ops). **Prediction:** Unlikely in near term; requires significant architectural changes to agent loop.

4. **Post-subagent Completion Hook ([#22358](https://github.com/openclaw/openclaw/issues/22358))** — 12 comments. Enable automatic trajectory generation and retrospective analysis after significant subagent work. **Prediction:** Could appear as a plugin hook in 2026.4.x.

5. **Skill Priority Configuration ([#50199](https://github.com/openclaw/openclaw/issues/50199))** — 8 comments. Users need intelligent skill selection when multiple skills overlap. **Prediction:** Likely candidate for community contribution given clear problem statement.

6. **YAML Config Support ([#45758](https://github.com/openclaw/openclaw/issues/45758))** — 7 comments, 2 👍. Users want YAML as an alternative to JSON5 for configuration. **Prediction:** Low-hanging fruit; could be contributed quickly.

7. **Filesystem Sandboxing Config ([#7722](https://github.com/openclaw/openclaw/issues/7722))** — 9 comments, 4 👍. Users want `tools.fileAccess` with allow/deny path lists. This is the most-reacted feature request. **Prediction:** Security-sensitive feature requiring careful design review — mid-term roadmap item.

**Roadmap Signal — The big ongoing refactors:**
- [#99059](https://github.com/openclaw/openclaw/pull/99059) — Extracting reusable AI runtime package suggests OpenClaw is moving toward a plugin/package architecture for model adapters
- [#100140](https://github.com/openclaw/openclaw/pull/100140) — "Assistants remember across private conversations" suggests unified memory/cross-session context

## 7. User Feedback Summary

**Real Pain Points Expressed:**

1. **"My subagent work just disappeared"** — Multiple users (IIIyban, waliddafif, pidgeon777) report that multi-agent orchestration is unreliable in production. Subagents complete silently without results, sessions get stuck, lock files persist.

2. **"I can't use the control UI on my VPS"** — RafaelLee (Issue #32473, resolved) — Deployment friction for non-localhost setups was a significant adoption barrier that appears to be closed now.

3. **"Memory is chaotic"** — AM-young-fun (Issue #43747) — Teams using OpenClaw report completely inconsistent memory management behavior between users, making collaborative use frustrating.

4. **"The LLM lied to me and I paid for it"** — bo-blue (Issue #49876) — When cron session tool calls fail, the LLM fabricates plausible output instead of failing cleanly. This is both a trust and a cost issue.

5. **"My gateway is eating 14GB of RAM"** — the-lobsternaut (Issue #54155) — Memory leak grows from 389MB to 14.7GB over 4 days. This makes long-running gateway deployments unsustainable.

6. **"Someone's work path is hardcoded into my install"** — buggiant-coder (Issue #51429) — `/Users/wangtao` hardcoded into production code shipped to users, creating unauthorized directories. This reflects poorly on QA/CI practices.

7. **"Docs tell me to use features that don't exist"** — Stoff81 (Issue #48920) — Documentation drift between `IsolatedSessions` in live docs and the actual release makes onboarding confusing.

**Satisfaction Signals:**
- The project has a healthy stream of incoming PRs (157 closed/merged today)
- PR #100125 has `dependencies-changed` label and touches 20+ channels, indicating active multi-platform support
- Several long-standing issues (Slack UX, Mattermost file handling, binary file delivery) are being addressed through merged PRs
- The community is actively suggesting architectural improvements (multi-session architecture, tiered loading, YAML config) — a sign of engaged, sophisticated power users

**Dissatisfaction Signals:**
- The backlog of P1 bugs (10+ issues tagged P1) with no fix PRs is concerning
- Issue #99594 (Cloud credits bug) is a P0 that blocks paying customers
- Several Chinese-language issues (Shi [#51429](https://github.com/openclaw/openclaw/issues/51429), [#45765](https://github.com/openclaw/openclaw/issues/45765)) suggest international users are affected by English-centric development practices

## 8. Backlog Watch

**Critical Items Needing Maintainer Attention (age > 2 weeks, no progress):**

1. **[#22676](https://github.com/openclaw/openclaw/issues/22676) — Signal daemon race condition** (P1, opened Feb 21, 2026 — **134 days**)
   - Oldest P1 bug. Critical for production reliability. No fix PR visible. Users report orphaned processes and send failures on every config change.

2. **[#7722](https://github.com/openclaw/openclaw/issues/7722) — Filesystem Sandboxing Config** (P2, opened Feb 3, 2026 — **152 days**)
   - Most-upvoted feature request (4 👍). Security-focused sandboxing. No active PRs.

3. **[#13583](https://github.com/openclaw/openclaw/issues/13583) — Pre-response Enforcement Hooks** (P2, opened Feb 10, 2026 — **145 days**)
   - High-stakes workflow hard gates. No maintainer review assigned.

4. **[#45740](https://github.com/openclaw/openclaw/issues/45740) — gh-issues skill prompt injection** (P2, security, opened Mar 14, 2026 — **113 days**)
   - Security vulnerability — raw issue bodies injected into sub-agent prompts. Needs security review label applied but no visible action.

5. **[#43996](https://github.com/openclaw/openclaw/issues/43996) — Sandbox container exits immediately** (P1, security, opened Mar 12, 2026 — **115 days**)
   - Docker sandbox broken with `no-new-privileges`. Users cannot run any commands. Needs product decision and maintainer review.

6. **[#43747](https://github.com/openclaw/openclaw/issues/43747) — Memory management chaos** (P2, regression, opened Mar 12, 2026 — **115 days**)
   - Inconsistent behavior between users/instances. No product decision.

**PRs Stuck in Review:**
- **[#51762](https://github.com/openclaw/openclaw/pull/51762)** — "Honor configured default agent across main paths" (opened Mar 21, 2026 — **106 days**)
  - Fixes hardcoded `DEFAULT_AGENT_ID = "main"` — important for multi-agent deployments. Status: proof supplied but no maintainer movement.

- **[#78184](https://github.com/openclaw/openclaw/pull/78184)** — "Clean approval-pending chat prompts" (opened May 6, 2026 — **60 days**)
  - Fixes Telegram/Zollie approval loop. Status: waiting on author.

**Warning Signals:**
- Of the 50 top issues analyzed, **24 (48%) have the `clawsweeper:no-new-fix-pr` label** — meaning ClawSweeper (likely an automated triage tool) cannot find any active fix PR for these issues. This suggests a growing gap between bug reports and developer capacity.
- Several P1 issues also carry `clawsweeper:needs-product-decision` and `clawsweeper:needs-maintainer-review` — indicating decisions are blocked, not just fixes.

---

**Overall Assessment:** OpenClaw is in a period of high community engagement but is struggling to keep up with bug-fix velocity relative to issue creation. The 456 active open issues mean the issue tracker is growing faster than the team can resolve them. The good news: the PR pipeline is robust (157 merged/closed today), and several long-standing channel-specific bugs are being fixed. The concerning trend: P1 reliability bugs (subagent data loss, race conditions, session starvation) remain open for months without visible fix PRs. The project would benefit from a focused stabilization sprint.

---

## Cross-Ecosystem Comparison

Here is the cross-project comparison report based on the provided digest data.

---

## Cross-Project Comparison Report: AI Agent Open-Source Ecosystem
**Date:** 2026-07-05

### 1. Ecosystem Overview
The personal AI assistant & agent open-source landscape on July 5, 2026, is characterized by a bifurcation between "reference platform" projects (OpenClaw) experiencing high community engagement but struggling with bug-fix velocity, and smaller projects (NanoBot, NanoClaw, Hermes Agent) operating intense, focused stabilization sprints. A clear industry-wide pressure is emerging around **production reliability**—specifically silent data loss, multi-agent orchestration stability, and memory management consistency—indicating the ecosystem is moving from "magic demo" to "mission-critical tool." A secondary but tangible trend is the **democratization of infrastructure**, with projects like ZeroClaw and NanoClaw investing in container sandboxing, SSRF prevention, and formal security policies, signaling growing enterprise interest. Finally, there is a clear divergence in architectural philosophy, with OpenClaw and Hermes Agent pushing large-scale architectural refactors (extracted runtimes, context governance), while PicoClaw and LobsterAI focus on targeted, incremental improvements to existing configurations.

### 2. Activity Comparison

| Project | Active Issues | Open PRs | PRs Merged/Closed (24h) | Release Today? | Health Score (Qualitative) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **OpenClaw** | 456 | 343 | 157 | No | **Constrained** – High demand, velocity capped by capacity. Significant (P0/P1) bugs open >100 days. |
| **NanoBot** | Very Low | ~10 (est.) | 7 | No | **Excellent** – Rapid triage; 6 of 7 identified bugs closed in cycle. |
| **Hermes Agent** | 44 | 43 | 7 | No | **Healthy** – Active, with major features (Context Health) in review. Moderate backlog. |
| **PicoClaw** | 3 | 5 | 2 | No | **Stable** – Low activity, but responsive to regressions (reverted broken PR in <2 days). |
| **NanoClaw** | ~1 (new) | ~18 (est.) | 22 | No | **Very High** – Major cleanup & feature sweep. Exceptional merge velocity. |
| **IronClaw** | 9 | ~43 (est.) | 17 | No | **Strong** – High velocity on coordinated OAuth migration. Release PR stalled. |
| **LobsterAI** | 2 | 3 | 2 | No | **Moderate** – Focused on bug fixes. Low community engagement. Stale issues. |
| **CoPaw (QwenPaw)**| 8 | 3 | 0 | No | **Under Pressure** – High bug-fix load on v2.0 beta; no merges today. |
| **ZeroClaw** | 39 | 49 | 1 | No | **High, but Loaded** – Very large WIP; well-organized via trackers. Critical S1 bugs open. |
| **NullClaw, TinyClaw, Moltis, ZeptoClaw** | - | - | 0 | No | **Dormant** – No public activity observed. |

### 3. OpenClaw's Position

- **Advantages vs. Peers:** OpenClaw is the undisputed community hub, with an order of magnitude more engagement (456 open issues, 343 open PRs) than any other project. Its ecosystem of channels (Slack, Mattermost, etc.) is the most mature. The project is leading the architecture conversation with large-scale refactors (extracted runtime, cross-session memory).
- **Technical Approach:** OpenClaw’s "mono-repo, community-driven" model is a core strength and weakness. It allows rapid integration of community fixes (157 merged today), but the review pipeline is backlogged, and the `clawsweeper` bot identifies **48% of top issues lack any fix PR**.
- **Community Size & Velocity:** OpenClaw dwarfs all peers in raw numbers, but its **bug-fix throughput per issue** is lower. Meanwhile, NanoBot and NanoClaw show equivalent (or higher) responsiveness with a much smaller community. OpenClaw’s challenge is not interest, but **sustainable scaling** of maintainer capacity.

### 4. Shared Technical Focus Areas

Across projects, several dominant themes emerge, indicating industry-wide requirements:

- **Memory & Context Management (Critical):**
    - **OpenClaw** (#43747: "Memory is in chaos"), **CoPaw** (#5775, #5778: Auto-memory broken, compression destroys context), **ZeroClaw** (#8695: Cron memory flag mismatch).
    - *Need:* Consistent, user-configurable memory that is reliable across sessions. The ecosystem is failing at "agentic persistence."
- **Multi-Agent/Sub-Agent Reliability:**
    - **OpenClaw** (#44925: "Subagent completion silently lost", #52249: Parent session stuck), **NanoBot** (#4652: MCP tool crash), **Hermes Agent** (#56004: Reasoning stripped on replay).
    - *Need:* Guaranteed delivery and clear error handling when orchestrating sub-tasks. Silent failure is unacceptable for production.
- **Security Hardening (SSRF, Prompt Injection, Sandboxing):**
    - **NanoBot** (#4671: SSRF pinning), **OpenClaw** (#43996: Sandbox broken, #45740: Prompt injection in gh-issues), **NanoClaw** (#2923: UI card defacement, #2954: Security policy PR), **ZeroClaw** (#8654: panic on skill review).
    - *Need:* Proactive security measures, especially around untrusted data (issue bodies, tool outputs) and network egress.
- **Provider Flexibility & Reliability:**
    - **Hermes Agent** (#58498: Desktop ignores OpenAI Codex), **ZeroClaw** (#8615: `<think>` tag deletion, #8675: Malformed tool calls), **CoPaw** (#5773: Memory breaks OCG provider).
    - *Need:* Feature parity and consistent behavior across model providers, not just OpenAI/Anthropic.

### 5. Differentiation Analysis

- **Target User:**
    - **OpenClaw:** The "Generalist Power User" – needs deep configurability, multi-channel support, and a massive plugin ecosystem.
    - **NanoBot / PicoClaw:** The "Pragmatic Hobbyist" – values low setup friction, reliability, and core features over overwhelming choice.
    - **IronClaw / ZeroClaw:** The "Enterprise Developer" – focused on correctness, architectural rigor, and security audits. Integration testing (ratchets) and formal policies are priorities.
    - **Hermes Agent:** The "Model-Hedging User" – targets those who switch between different LLM providers frequently.
    - **LobsterAI:** The "Workflow & Task User" – feature set focused on proxy handling and document management during tasks.

- **Technical Architecture:**
    - **OpenClaw / Hermes Agent:** Monolithic/complex agents with deep lifecycle hooks. Path towards "agent operating systems" with runtime extraction and policy engines.
    - **NanoBot / NanoClaw:** Modular, container-first design. Focus on sandboxing and egress control. The "Kubernetes for agents" model.
    - **IronClaw:** Very high engineering standards with harness tests and compile-time enforcement. Most "boring" codebase that is least likely to have a production regression.
    - **ZeroClaw:** High velocity, feature-packed (Goal Mode, SOP engine, new channels). The "breadth-first" competitor.

### 6. Community Momentum & Maturity

- **Tier 1: Rapidly Iterating (High Merge Velocity, Feature-Rich)**
    - **OpenClaw:** Rapid iteration, but on a "fire hose" model. Introduces many features, but stability lags.
    - **NanoBot:** *Best-in-class turnaround.* From bug report (July 2) to fix (July 4). A model for efficient development.
    - **NanoClaw:** Significant feature sweep today. Appears to be building release momentum.
    - **ZeroClaw:** High development output (Goal Mode, SOP). Well-organized, but carrying a large technical debt (many open PRs/issues).

- **Tier 2: Stabilizing / Consolidating (Focus on Bug Fixes, Performance)**
    - **Hermes Agent:** Merging 7 PRs/day is solid. Focus on provider support and context governance implies maturing codebase.
    - **IronClaw:** High engineering quality and architectural discussions. The community is small (Near AI), but the code is production-ready.
    - **PicoClaw:** Low activity, but responsive. Likely in a maintenance window.

- **Tier 3: Stalled / Dormant (No Activity)**
    - **NullClaw, TinyClaw, Moltis, ZeptoClaw:** No public activity in 24 hours. May represent dead-ends or projects waiting for maintainer bandwidth.

### 7. Trend Signals

1.  **From "Chatbot" to "Agent Operator":** Users no longer want a single chat interface. Across projects, the demand is for **SOP engines** (ZeroClaw), **cron jobs** (ZeroClaw, OpenClawClaw), **sub-agents** (OpenClaw, NanoBot), and **goal-mode** (ZeroClaw). The value is shifting from conversation to orchestration.
2.  **The Container is King:** The most sophisticated projects (NanoClaw, ZeroClaw, NanoBot) are all investing in **container sandboxing** and **egress control**. This signals that AI agents are moving towards executing arbitrary code/tools, requiring robust containment.
3.  **Opaque AI is Unacceptable:** "Silent failures" and "fabricated output" (OpenClaw #49876, ZeroClaw #8615) are the top dissatisfaction signals. The industry demand is for **deterministic error surfacing** and **auditable log trails**. IronClaw's "errors must surface" PR is a leading indicator.
4.  **The Multi-Model Reality:** The community is no longer satisfied with "ChatGPT clone." They want consistent behavior across OpenRouter, vLLM, Groq, and Cerebras. The projects that abstract this complexity well (Hermes Agent, ZeroClaw) gain an edge.
5.  **Documentation as a Feature:** OpenClaw (#48920: "Live docs are ahead of release") and NanoClaw (multiple doc-fix PRs) show that **documentation drift** is a major pain point. For developers, "truth is in the code" is not acceptable; projects that maintain accurate, versioned docs will win trust.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

Here is the NanoBot project digest for **2026-07-05**.

---

## NanoBot Project Digest — 2026-07-05

### 1. Today's Overview
The project shows a **high-activity cycle**, with **13 PRs updated** in the last 24 hours, including **7 merged/closed**. The two issues that were updated are both closed, indicating a strong push toward resolution of recent bugs. While there were **zero new releases**, the high merge velocity suggests a significant "fixes and features" patch is being assembled. The maintainers are clearly focused on **stability (race conditions, crash prevention) and security (SSRF prevention)**.

### 2. Releases
**No new releases today.** The project appears to be in a stabilization sprint, consolidating multiple bugfix branches before a tag.

### 3. Project Progress
The following significant work advanced today (merged/closed items):

- **Security – SSRF Hardening** (PR #4671 – still open, high activity): Implementing DNS pinning for `web_fetch` and MCP HTTP probes to prevent Server-Side Request Forgery attacks. This is the most critically reviewed PR of the batch.
- **Copilot Token Refresh Race Condition** (PR #4684 – **CLOSED**): Guarded the GitHub Copilot token refresh with an `asyncio.Lock`, fixing a bug where concurrent requests would cause duplicate token fetches and potential authorization crashes.
- **Windows Gateway Stop Crash** (PR #4690 – **CLOSED**): Fixed a crash on `nanobot gateway stop` when `CTRL_BREAK_EVENT` fails, adding a `taskkill` fallback for Windows users.
- **Crash-Durable Pairing Writes** (PR #4653 – **CLOSED**): Restored `fsync` calls in atomic writes to prevent data loss during a crash in the pairing module.
- **MCP Malformed Tool Result Handling** (PR #4666 – **CLOSED**): Fixed Issue #4652 by wrapping MCP result rendering exceptions, preventing a full process crash when tools return bad data.
- **Config Serialization Fix** (PR #4692 – **CLOSED**): Aligned `model_presets` field naming to `modelPresets` (camelCase) to match documentation.
- **DingTalk Shutdown Task** (PR #4646 – **CLOSED**): Fixed a resource leak where the DingTalk stream task was not properly cancelled on shutdown.
- **WebUI Viewport Fix** (PR #4694 – **OPEN**): Fixes horizontal overflow/clipping on mobile-width browsers (Fixes #4693).

### 4. Community Hot Topics
- **#4696 – Smooth WebUI Streaming Markdown Reveal** (Author: chengyongru, Updated: 2026-07-04)  
  *Open PR, no comments yet.*  
  **Analysis**: This is a UX quality-of-life feature introducing buffered rendering and natural-speed reveal. It indicates the community cares about the perceived responsiveness of streaming output, not just raw speed.

- **#4677 – Copilot Token Refresh Race** (Author: hamb1y-bot, Updated: 2026-07-04, 1 comment)  
  *Closed Issue.*  
  **Analysis**: This was the root cause of intermittent "empty responses" or "auth failures" under load. The fix (PR #4684) was shipped rapidly—this shows good maintainer responsiveness to race-condition bugs.

- **#4652 – MCP Tool Call Process Crash** (Author: Lucky314159, Updated: 2026-07-04, 3 comments)  
  *Closed Issue.*  
  **Analysis**: A high-severity bug (process crash) with a rapid turnaround: filed Jul 2, fix merged Jul 4. The fix ensures that bad data from MCP tools doesn't propagate as an unhandled exception. This is critical for production reliability.

### 5. Bugs & Stability
| Severity | Bug | Status | Fix PR? | Notes |
|----------|-----|--------|---------|-------|
| **P0 – Critical** | SSRF via URL validation bypass (#4611) | PR #4671 **OPEN** | ✅ Yes | Most security-critical item; DNS pinning being reviewed. |
| **P1 – High** | MCP tool crash (#4652) | **CLOSED** | ✅ Yes (PR #4666) | Fixed – process no longer crashes on bad MCP results. |
| **P1 – High** | Copilot token refresh race (#4677) | **CLOSED** | ✅ Yes (PR #4684) | Fixed – concurrent requests no longer trigger duplicate token fetches. |
| **P1 – High** | Pairing data loss on crash (#4653) | **CLOSED** | ✅ Yes (PR #4653) | Fixed – `fsync` restored for atomic writes. |
| **P2 – Medium** | DingTalk shutdown leak (#4646) | **CLOSED** | ✅ Yes (PR #4646) | Fixed – resources now cleaned up during stop. |
| **P2 – Medium** | Windows gateway stop crash (#4690) | **CLOSED** | ✅ Yes (PR #4690) | Fixed – graceful fallback implemented. |
| **P2 – Medium** | WebUI mobile viewport clipping (#4693) | PR #4694 **OPEN** | ✅ Yes | Ongoing – likely merges next week. |

**Summary**: The stability sprint has resolved **6 of 7 identified bugs** this cycle, with only the SSRF fix still under review.

### 6. Feature Requests & Roadmap Signals
- **MCP Tool Inheritance for Subagents** (PR #4697 – OPEN, Author: franciscomaestre)  
  *Config-driven inheritance allows specialist subagents to access database/search MCP tools without re-implementation.*  
  **Prediction**: High-value for developers building complex multi-agent workflows. Likely to merge within the next two releases.

- **Mattermost Channel Support** (PR #4459 – OPEN, Author: goodtiding5, since Jun 22)  
  *A full integration with WebSocket + REST, streaming responses, and auto-reconnect.*  
  **Prediction**: This has been open for ~2 weeks without maintainer review. It may be waiting for bandwidth, but it is a major community contribution.

- **WebUI Markdown Streaming** (PR #4696 – OPEN)  
  *Analyst note: This is purely UX polish, but signals user demand for a "reading experience" that matches ChatGPT/Copilot parity.*

### 7. User Feedback Summary
- **Pain Point: MCP tool failures crash the bot** (Issue #4652) – Fixed. User reported immediate crashes during normal agent operation. Fix was delivered in 2 days.
- **Pain Point: Copilot auth fails under concurrent requests** (Issue #4677) – Fixed. User reported intermittent failures under load.
- **Pain Point: WebUI unusable on mobile** (Issue #4693) – Addressed by PR #4694. User-reported "clipped viewport and horizontal scroll" on narrow screens.
- **Pain Point: Windows gateway fails to stop** (PR #4690) – User encountered tracebacks. Fix uses `taskkill` fallback.
- **Satisfaction Signal**: The rapid triage of 7 merged/closed PRs in 24h suggests the community is actively engaged and maintainers are responsive.

### 8. Backlog Watch
- **PR #4459 – Mattermost Channel Support** (Last updated: 2026-07-04)  
  *Status: Open since Jun 22. **0 maintainer comments**.*  
  **Action needed**: This is a substantial, well-documented PR. If the maintainers intend to accept it, they should provide feedback soon to avoid contributor frustration. If they are deferring, a clear "not now" note is needed.

- **PR #4697 – MCP Inheritance for Subagents** (Last updated: 2026-07-04, **0 comments**)  
  *Status: Open for 1 day, but no reviewer engagement yet.*  
  **Action needed**: Low urgency but could block other agent-structure work if left unattended.

- **No orphaned Issues older than 3 days found.** The project is current.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

# Hermes Agent Project Digest — 2026-07-05

## Today's Overview

Hermes Agent shows **very high activity** on July 5, 2026, with 50 issues and 50 PRs updated in the last 24 hours. The project maintains a robust **44 open issues** (active) and **6 closed**, while PRs show **43 open** and **7 merged/closed** — indicating a healthy but slightly backlogged review pipeline. No new releases were published today. The community is highly engaged, with several critical bug fixes under active review, particularly around Python 3.14 compatibility, credential handling, and Qwen model reasoning preservation. Multiple PRs address long-standing issues about skills adherence and context governance, suggesting a maturing codebase with growing community contributions.

## Releases

No new releases today. The latest available version appears to be Hermes Agent v0.18.0 (referenced in bug reports) and v0.14.0 (mentioned in older issues). No migration notes or changelogs were published in the last 24 hours.

## Project Progress

**Merged/Closed PRs Today (7 total):**
- [#58605](https://github.com/NousResearch/hermes-agent/pull/58605) — **docs**: Shrank `AGENTS.md` to a compact bootloader, routing contributors to canonical docs. Clean, focused change.
- [#58606](https://github.com/NousResearch/hermes-agent/pull/58606) — **Feat**: Added Groq and Cerebras as recognized providers in `hermes auth`. Addresses user pain point.
- [#58370](https://github.com/NousResearch/hermes-agent/issues/58370) — **Closed**: Feature request for "Fable copilot" planning/review path; closed without merge notes visible.
- [#58518](https://github.com/NousResearch/hermes-agent/issues/58518) — **Closed**: Bug fix for WebUI session list hiding active CLI sessions before final output.

**Key Feature PRs Open (not merged yet but active):**
- [#58597](https://github.com/NousResearch/hermes-agent/pull/58597) — **Context Health**: Adds Phases 1–9 auto context governance, including policy model, pre-turn intake guard, task registry, and boundary enforcement. This is a **major architectural addition**.
- [#58601](https://github.com/NousResearch/hermes-agent/pull/58601) — **Docker sandbox egress control**: New "allowlist" mode for container networking, plus a shared filtered proxy. Important for security-conscious deployments.
- [#58610](https://github.com/NousResearch/hermes-agent/pull/58610) — **Compact large tool results**: Stores oversized tool outputs on disk with compact handles in conversation history. Reduces context bloat.

## Community Hot Topics

**Most Active Issue:**
- [#844](https://github.com/NousResearch/hermes-agent/issues/844) — **Feature: Knowledgebase RAG System** (7 comments, 4 👍). Open since March 2026, still actively discussed. Users want a document directory → embed → retrieve pipeline. This is the most-upvoted feature request in the dataset and signals strong demand for local-first RAG capabilities.

**Other Heated Discussions:**
- [#42864](https://github.com/NousResearch/hermes-agent/issues/42864) — **scope-recall standalone memory provider** (6 comments, RFC/show-and-tell). A community-maintained plugin for scoped durable memory with auditable local storage. The author seeks official documentation/support.
- [#40297](https://github.com/NousResearch/hermes-agent/issues/40297) — **Desktop: per-session workspace selection** (5 comments, 9 👍). Users want to switch projects without restarting the desktop app. High upvote count indicates strong demand for multi-project workflows.
- [#56004](https://github.com/NousResearch/hermes-agent/issues/56004) — **Qwen3.6 / vLLM: reasoning stripped on replay** (3 comments, 2 👍). Multi-turn thinking context is lost — a critical bug for reasoning-heavy use cases.

**Underlying Needs:** The community is pushing for three major themes: (1) better memory/RAG integration, (2) multi-session project management in the desktop app, and (3) model-provider parity (especially for free-tier or cutting-edge providers like Groq, Cerebras, Eden AI).

## Bugs & Stability

**Critical/High Severity (P1–P2):**
- [#48534](https://github.com/NousResearch/hermes-agent/issues/48534) — **[CLOSED/P1]** Anthropic Max OAuth fails (404) because Anthropic now blocks the `claude-cli/` User-Agent. **Fixed/closed today** — good resolution speed.
- [#40960](https://github.com/NousResearch/hermes-agent/issues/40960) — **[P2]** Credential pool exhaustion returns misleading 401 instead of 429/402. Users see auth errors when they're really hitting quota limits. **Fix PR exists** (not yet merged).
- [#56004](https://github.com/NousResearch/hermes-agent/issues/56004) — **[P2]** Qwen3.6/vLLM: prior-turn reasoning stripped on replay. Multi-turn thinking context lost. **No fix PR visible**, still open.
- [#58581](https://github.com/NousResearch/hermes-agent/issues/58581) — **[P2]** `vision_analyze` fails to route through `auxiliary.vision` when main model is text-only (DeepSeek V4 Pro). All vision requests fail. **Fix PR [#58600](https://github.com/NousResearch/hermes-agent/pull/58600) opened today.**
- [#57948](https://github.com/NousResearch/hermes-agent/issues/57948) — **[P2]** `vision_analyze` first call returns 400 when main model lacks vision; second call works. Intermittent failure pattern. **Fix PR #58600 also addresses this.**
- [#58498](https://github.com/NousResearch/hermes-agent/issues/58498) — **[P2]** Desktop ignores OpenAI Codex provider, routes through Nous Portal instead (CLI works correctly). **No fix PR visible.**

**Medium Severity (P3):**
- [#58596](https://github.com/NousResearch/hermes-agent/issues/58596) — **Python 3.14 crash**: `DaemonThreadPoolExecutor` references removed attributes. Breaks all concurrent features. **Two fix PRs exist**: [#57459](https://github.com/NousResearch/hermes-agent/pull/57459) and [#58598](https://github.com/NousResearch/hermes-agent/pull/58598).
- [#35530](https://github.com/NousResearch/hermes-agent/issues/35530) — TUI not resizing properly in some terminals. **No fix PR.** 
- [#58404](https://github.com/NousResearch/hermes-agent/issues/58404) — Desktop chat sessions tagged as TUI, receive terminal guidance. Session misclassification. **No fix PR.**
- [#58569](https://github.com/NousResearch/hermes-agent/issues/58569) — Skills loaded but not followed (treated as advisory). Related to #54256. **No fix PR.**
- [#58555](https://github.com/NousResearch/hermes-agent/issues/58555) — Skills Hub: ClawHub "View source" links broken. **No fix PR.**

**Security-Related:**
- [#58594](https://github.com/NousResearch/hermes-agent/pull/58594) — **PR**: Redacts Telegram bot tokens from error logs. Important leak prevention. Open, not merged.
- [#58601](https://github.com/NousResearch/hermes-agent/pull/58601) — **PR**: Docker sandbox egress allowlist. Proactive security hardening.

## Feature Requests & Roadmap Signals

**High Community Demand (likely for next release):**
- **Knowledgebase RAG System** ([#844](https://github.com/NousResearch/hermes-agent/issues/844)) — Most-upvoted open feature. Predict inclusion in v0.19.0 or v0.20.0 given sustained interest.
- **Per-session workspace selection** ([#40297](https://github.com/NousResearch/hermes-agent/issues/40297)) — 9 upvotes. Desktop UX improvement likely to land soon.
- **Voice wake word** ([#49383](https://github.com/NousResearch/hermes-agent/issues/49383)) — "Hey Hermes" for desktop app. Growing interest in voice interfaces.

**Provider Expansion (multiple requests today):**
- **Groq & Cerebras** ([#58603](https://github.com/NousResearch/hermes-agent/issues/58603)) — Already implemented in PR [#58606](https://github.com/NousResearch/hermes-agent/pull/58606). Likely in next patch.
- **Eden AI** ([#58571](https://github.com/NousResearch/hermes-agent/issues/58571)) — Multi-provider aggregator. Early stage, no PR yet.
- **WhatsApp setup wizard** ([#58041](https://github.com/NousResearch/hermes-agent/issues/58041)) — One-command configuration. Clear UX improvement.
- **Signal adapter enhancements** ([#39043](https://github.com/NousResearch/hermes-agent/issues/39043)) — Native quote/reply, edit, remote-delete. Niche but valuable.
- **Aurora dashboard theme** ([#57051](https://github.com/NousResearch/hermes-agent/pull/57051)) — Frosted-glass aesthetic. Open PR, not merged.

**Prediction:** Next release (likely v0.19.0) will include Groq/Cerebras provider support, the compact tool-results handle feature, and the context health governance framework. The RAG knowledgebase system is a strong candidate for v0.20.0.

## User Feedback Summary

**Pain Points:**
- **Configuration complexity**: WhatsApp setup requires 4+ manual steps vs Telegram's single wizard (#58041). Users want parity.
- **Desktop vs CLI inconsistency**: Multiple reports that Desktop behaves differently from CLI — provider routing (#58498), workspace switching (#40297), session tagging (#58404).
- **Skills non-compliance**: Users report the agent loads but ignores skill instructions (#58569). "Use X, NOT Y" instructions are treated as advisory — a significant trust issue.
- **Model switching instability**: Behavior changes dramatically when switching models, even for the same task (#27103).
- **Fictional character identity bug**: Novel content stored in memory causes the agent to assume fictional roles in later sessions (#21709). Creative writers affected.
- **MacOS Keychain test isolation**: Tests fail due to real credentials being picked up (#58609). Developer friction for contributors on macOS.

**Satisfaction Signals:**
- Community members are actively contributing plugins (scope-recall memory provider, #42864) and submitting fix PRs — indicating a healthy, engaged developer ecosystem.
- The "Fable copilot" feature (#58370) suggests advanced users are pushing for more sophisticated model orchestration patterns.

## Backlog Watch

**Long-Unanswered Important Issues Needing Maintainer Attention:**

| Issue | Age | Comments | Last Update | Risk |
|-------|-----|----------|-------------|------|
| [#844](https://github.com/NousResearch/hermes-agent/issues/844) — RAG Knowledgebase | 117 days | 7 | 2026-07-04 | **High** — most-upvoted feature, no PR or roadmap commitment visible |
| [#21709](https://github.com/NousResearch/hermes-agent/issues/21709) — Novel content → fictional identity | 58 days | 1 | 2026-07-04 | **Medium** — unusual bug but affects creative users |
| [#27103](https://github.com/NousResearch/hermes-agent/issues/27103) — Redundant skills, model switching instability | 50 days | 3 | 2026-07-05 | **High** — affects core agent reliability |
| [#34143](https://github.com/NousResearch/hermes-agent/issues/34143) — Profile Codex auth ignores global pool | 38 days | 2 | 2026-07-05 | **Medium** — authentication edge case |
| [#31513](https://github.com/NousResearch/hermes-agent/issues/31513) — WSL2 gateway idle → 100% CPU | 42 days | 1 | 2026-07-05 | **Low** — WSL2-specific, but could affect many Windows users |
| [#35530](https://github.com/NousResearch/hermes-agent/issues/35530) — TUI resize issues | 36 days | 2 | 2026-07-05 | **Medium** — terminal UX quality |

**Most Concerning:** Issue #844 (RAG system) has been open since March with 4 upvotes, no maintainer response, and no PR. For a project marketing agent capabilities, the absence of a built-in RAG pipeline is a growing gap. Issue #27103 (skills redundancy + model switching instability) affects core agent reliability and has received only moderate attention despite being open since mid-May.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

# PicoClaw Project Digest
**Date:** 2026-07-05

## Today's Overview
PicoClaw shows moderate activity over the past 24 hours with 4 issues updated (3 active, 1 closed) and 7 pull requests updated (5 open, 2 merged/closed). The project has seen no new releases. Community contributions are focused on dependency bumps, configuration cleanup, and i18n fixes from repeat contributor `chengzhichao-xydt`, while two critical fixes for agent session handling and Windows path regression were merged. Several stale issues remain open, and a new feature PR for agent-specific runtime overrides was opened today. Overall project health is stable with ongoing maintenance but some aging issues requiring attention.

## Releases
**No new releases.** The latest available version remains the Git state noted in recent bug reports (v0.2.4-9-ged618e1 from March 2026).

## Project Progress
**Merged/Closed PRs today (2):**
- **[PR #3224 – `fix(agent): clear routed agent session`](https://github.com/sipeed/picoclaw/pull/3224)** (Merged) — Critically fixes `/clear` command for multi-agent setups. Previously routed-agent sessions were not cleared; only the default agent was cleared. This resolves a functional regression for users with multiple agents configured.
- **[PR #3221 – Revert "test: cover sandbox fs Windows path handling"](https://github.com/sipeed/picoclaw/pull/3221)** (Closed) — Reverted PR #3158 due to an import error in `pkg/providers/openai_compat/provider.go`. This indicates a regression was caught quickly after merging Windows path testing.

**Open but active PRs (5):**
- [PR #3225 – Support agent-specific runtime overrides](https://github.com/sipeed/picoclaw/pull/3225) — New feature allowing per-agent configurations for `max_tokens`, summarization thresholds, and `split_on_marker` (opened today).
- [PR #3192 – Docker goreleaser base image bump](https://github.com/sipeed/picoclaw/pull/3192)
- [PR #3191 – Remove duplicate `.gitignore` entry](https://github.com/sipeed/picoclaw/pull/3191)
- [PR #3190 – Sync i18n missing locale keys](https://github.com/sipeed/picoclaw/pull/3190)
- [PR #3189 – Fix LINE channel `resp.Body.Close()` errors](https://github.com/sipeed/picoclaw/pull/3189)

## Community Hot Topics
**Most active issues (by comments):**
1. **[Issue #3150](https://github.com/sipeed/picoclaw/issues/3150) – "[BUG]它给自己整失忆了"** (4 comments, closed as stale) — Chinese-language bug report literally meaning "it gave itself amnesia." User likely experienced session memory loss. Was closed due to staleness with no resolution.
2. **[Issue #3088](https://github.com/sipeed/picoclaw/issues/3088) – "[Feature] use vodozemac instead of libolm"** (4 comments, 2 👍, help wanted, priority high) — Strong community demand to replace deprecated/insecure `libolm` with `vodozemac`. This has been open for nearly a month and marked as high priority, but no PR has materialized.
3. **[Issue #3182](https://github.com/sipeed/picoclaw/issues/3182) – "[BUG] Android version"** (2 comments) — Android user cannot launch service or change paths despite granting permissions.

**Underlying needs:** The vodozemac migration (#3088) reflects growing security consciousness among users, particularly Matrix channel users. The Android issue (#3182) signals mobile deployment pain points. The "amnesia" issue (#3150) points to session persistence reliability concerns.

## Bugs & Stability
**Reported bugs today (active):**
- **Issue #3182 – Android service launch failure** (Medium severity) — User cannot launch PicoClaw service on Android; path settings unchangeable. No fix PR yet. Impacts mobile adoption.
- **Issue #3194 – "Received encrypted message but crypto is not enabled"** (Medium severity, stale) — Matrix encrypted messages received but crypto not available. User on v0.2.4-9. No resolution in comments.
- **Issue #3150 – Session memory loss** (Low severity, closed as stale) — Unresolved but closed due to inactivity. May still affect users.

**Regression fix merged:**
- [PR #3221](https://github.com/sipeed/picoclaw/pull/3221) reverted a Windows path handling test PR (#3158) that broke imports — caught and resolved within 2 days.

## Feature Requests & Roadmap Signals
**Active feature signals:**
1. **[PR #3225 – Agent-specific runtime overrides](https://github.com/sipeed/picoclaw/pull/3225)** (opened today) — Most likely candidate for next release. Enables per-agent `max_tokens`, summarization thresholds, and split markers. Strong signal that configuration flexibility is a priority.
2. **[Issue #3088 – vodozemac migration](https://github.com/sipeed/picoclaw/issues/3088)** (high priority, help wanted) — Security-critical feature. Likely targeted for an upcoming major/minor release given the upstream deprecation of libolm.
3. **i18n completeness** — PR #3190 adds missing translation keys for Bengali and Czech, showing ongoing localization effort.

**Prediction for next version:** Agent-specific overrides (PR #3225) will likely land, possibly alongside the vodozemac migration if a contributor steps forward.

## User Feedback Summary
**Pain points:**
- **Android reliability** – Service fails to launch, path setting inaccessible (#3182)
- **Matrix encryption gaps** – Users receiving encrypted messages but crypto not enabled, leaving them unable to decrypt (#3194)
- **Session memory issues** – User reported "amnesia" in Chinese-language issue (#3150), suggesting session loss under unclear conditions
- **Multi-agent confusion** – `/clear` command previously only cleared default agent (fixed today in PR #3224)

**Satisfaction signals:**
- Positive community engagement on dependency upgrades (2 👍 on vodozemac request)
- Active maintainer responsiveness – regression reverted within 2 days (PR #3221)
- Continued i18n contributions suggest active non-English user base

## Backlog Watch
**High-priority stale items needing attention:**
1. **[Issue #3088 – vodozemac migration](https://github.com/sipeed/picoclaw/issues/3088)** (high priority, stale since 2026-06-09) — No assignee. Security concern. Last updated 2026-07-04 but no PR linked. Risk grows as libolm ages.
2. **[Issue #3150 – Session memory loss](https://github.com/sipeed/picoclaw/issues/3150)** (closed as stale) — Although closed, the underlying problem may persist. Needs maintainer to reproduce or request user update with current version.
3. **[Issue #3194 – Matrix crypto not enabled](https://github.com/sipeed/picoclaw/issues/3194)** (stale since 2026-06-27) — Single comment, no maintainer response visible. Likely configuration or build-time issue.
4. **[PR #3192, #3191, #3190, #3189](https://github.com/sipeed/picoclaw/pulls?q=is%3Apr+is%3Aopen+updated%3A2026-06-27)** — Four PRs from same contributor all stale for 8 days. These are low-risk chores (Docker bumps, gitignore cleanup, i18n sync, lint fixes) that should be mergeable with minimal review.

**Maintainer attention needed:** The backlog of high-priority, unassigned issues combined with a cluster of unreviewed chore PRs suggests maintainers may be bandwidth-constrained. The vodozemac issue (#3088) is the most critical unaddressed item.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

Here is the project digest for **NanoClaw**, based on GitHub data from **2026-07-05**.

---

## NanoClaw Project Digest — 2026-07-05

### 1. Today’s Overview
NanoClaw saw a major spike in activity today, driven almost entirely by a large batch of merged pull requests (22 closed/merged) and a smaller wave of new opens (18). This indicates that maintainers performed a significant cleanup and feature sweep, likely ahead of a planned release or milestone. The single new open issue is a moderate-severity security report regarding UI integrity. No new releases were cut today, but the sheer volume of high-quality merged PRs (covering security docs, CLI improvements, container management, and bug fixes) suggests a release candidate may be forming.

### 2. Releases
None. No new versions of NanoClaw were tagged today.

### 3. Project Progress
The development velocity was extremely high, with 22 PRs merged or closed. Key advances include:

- **Security & Hardening:**
    - *PR #2945* (merged): Rewrote `docs/SECURITY.md` to describe the actual v2 container perimeter and marked outdated v1 guides as historical.
    - *PR #2943* (merged): Fixed the mount allowlist loader to honor the `readOnly` key and stop caching parse errors, improving container configuration reliability.
    - *PR #2934* (merged): Made security-perimeter environment variables (egress lockdown, resource caps) reachable from the shipped service configuration.
- **CLI & Group Management:**
    - *PR #2939* (merged): Added `ncl groups config add-mount` / `remove-mount` verbs, allowing host-only management of additional container mounts.
    - *PR #2036* (open): A large rework to add per-group container environment variables, now managed via the database instead of the file system. This is a major feature that appears ready for review.
- **Agent Runner & Stability:**
    - *PR #2956* (open): Fixes a bug where agents could deliver duplicate messages when the final output repeats tool-sent content.
    - *PR #2931* (merged): Changed container image builds from blocking (`execSync`) to asynchronous, preventing the host from freezing during long builds.
    - *PR #2942* (merged): Fixed a cross-process `in_reply_to` stamp bug that affected the MCP server integration.
- **Codebase Hygiene:**
    - Several PRs deleted dead code, deprecated shims, scaffold-era CLI vocabulary, and a broken auth script (*#2935, #2936, #2940, #2946*).
    - *PR #2937* (merged): Ensured that resetting a stuck session via `rm -rf` now works reliably by re-provisioning missing session folders.
- **UI/UX:**
    - *PR #2933* (merged): Added colored buttons to approval cards (Slack primary/danger styles), improving visual clarity for approvals/rejections.

### 4. Community Hot Topics
The most active discussions centered on large-scope changes and security policy:

- **PR #2036 ([OPEN] feat: per-group container env vars, DB-managed via `ncl groups config set-env`)**
    - A major feature that moved configuration from a stale file-based system to the database. It was refreshed recently (2026-07-04) and represents a significant quality-of-life improvement for container orchestration. Community interest is implied by its long life (since April) and the maintainer’s effort to resync it.
    - **Link:** [PR #2036](https://github.com/nanocoai/nanoclaw/pull/2036)

- **PR #2954 ([OPEN] Add Phase-1 security reporting & triage policy)**
    - A new policy document adding a formal reporting process, likely a response to the ongoing security issue discussion (see Issue #2923). The PR is a draft waiting for maintainer sign-offs, indicating the team is being deliberate about establishing security governance.
    - **Link:** [PR #2954](https://github.com/nanocoai/nanoclaw/pull/2954)

- **PR #2955 ([OPEN] fix(router): mention-sticky must not subscribe the channel root or accumulate-only sessions)**
    - A fix for the routing logic regarding mention-sticky sessions. It prevents incorrect subscription behaviors when sessions exist without thread engagement.
    - **Link:** [PR #2955](https://github.com/nanocoai/nanoclaw/pull/2955)

### 5. Bugs & Stability
One new security bug was reported, and several bugs were fixed today.

- **High Severity:** **Issue #2923** *([OPEN] `ask_user_question` card can be defaced by a forged click before origin authz)*
    - A security spoofing bug where an attacker can overwrite the text displayed on an approval card (e.g., changing the agent name) before the backend checks authorization. While the malicious action is blocked, the visual integrity of the card is compromised. No fix PR exists yet, but the *security policy PR (#2954)* indicates the maintainers are prioritizing a security response framework.
    - **Link:** [Issue #2923](https://github.com/nanocoai/nanoclaw/issues/2923)

- **Fixed Bugs (in today’s merges):**
    - **Fixed:** Duplicate message delivery by agents when tool output repeats final text (PR #2956).
    - **Fixed:** Host freezing during Docker image builds (PR #2931).
    - **Fixed:** Cross-process `in_reply_to` stamp being a no-op for MCP servers (PR #2942).
    - **Fixed:** Session reset procedure failing because the folder wasn't re-created (PR #2937).

### 6. Feature Requests & Roadmap Signals
Several merges and open PRs point to the upcoming roadmap:

- **Per-group environment variables (PR #2036):** This is a long-standing request for fine-grained container configuration. It’s likely to land in the next release (v2.2.x or v2.3.x).
- **Asynchronous image builds (PR #2931):** Now merged, this unblocks operators who need to build images without downtime.
- **Skill contributions:** The addition of an "OpenCode Stack" skill (PR #2952) and related configuration fixes (PR #2951) show community effort to extend NanoClaw’s integrations. The maintainers are accepting these as part of the "operational/container" skill category.
- **Security policy formalization (PR #2954):** The establishment of a formal triage and reporting policy is a strong signal that the project is maturing and seeking community security contributions.

### 7. User Feedback Summary
- **Pain Points:**
    - **Security/UI spoofing:** The new issue (#2923) highlights a real-world user fear about the trustworthiness of approval UIs.
    - **Documentation lag:** The large number of doc-fix PRs (e.g., #2948, #2945, #2953) indicates users have been encountering instructions that no longer match the v2 codebase, leading to confusion about setup and configuration.
    - **Host blocking:** The fix for synchronous image builds (PR #2931) directly addresses a user-reported pain point where operators had to wait for long image builds, blocking other host operations.
- **Satisfaction:**
    - The community is actively contributing high-quality pull requests (e.g., per-group env vars, skill additions), suggesting a healthy and engaged user base.
    - The maintainer's responsiveness is very high, with a large batch of PRs being reviewed and merged in a single day, which is a strong positive indicator.

### 8. Backlog Watch
No long-unanswered critical issues or PRs were identified in the 24-hour window. The oldest open PRs (like #2036) have been actively maintained and refreshed by the author, not abandoned. The overall backlog health appears good, with one caveat:

- **Watch Item:** The new **security vulnerability (Issue #2923)** has no fix in progress. While a policy is being written, the bug itself is unassigned and has no linked PR. Given its security nature, this needs maintainer attention soon.
    - **Link:** [Issue #2923](https://github.com/nanocoai/nanoclaw/issues/2923)

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

# IronClaw Project Digest — 2026-07-05

## Today's Overview

IronClaw continues at high velocity with **43 PRs updated in the last 24 hours**, 17 of which were merged or closed, alongside **9 active issues** (8 open, 1 closed). The project is deep in a coordinated multi-stack effort to replace Slack's legacy pairing-code authentication with personal OAuth, spanning 4 stacked PRs (#5643, #5644, #5645, #5646). CI and testing infrastructure improvements also dominate today's activity, with a new wiring-parity tripwire (#5637/#5642) to catch harness drift, and a planned flip from informational to ratcheted integration coverage (#5638). The lone closed issue (#5590) confirms that `main` branch CI checks have been restored to green. There were **no new releases** today.

## Releases

None in the last 24 hours. The most recent release process appears to be stalled at PR #5598 (`chore: release`), which proposes breaking changes for `ironclaw_common` (0.4.2→0.5.0), `ironclaw_skills` (0.3.0→0.4.0), and `ironclaw` itself (0.24.0→0.29.1). This release PR remains open and has not been merged.

## Project Progress

**17 PRs merged or closed today** — a productive day. Key advances:

- **Slack OAuth migration (stacked PRs progressing):** The 4-PR stack is moving forward: #5643 (CI for WebUI V2 JS tests) is open, #5644 (OAuth foundations, 77 files, dormant additive layer) is open and under review, #5645 (swap pairing codes for OAuth, 121 files, deletion-dominated) is open, and #5646 (reject legacy config fields at serve startup) is open. The initial design PR #5604 also saw continued discussion.

- **Migration tooling delivered:** PR #5627 (`feat(migration): v1/engine-v2 → Reborn state migration tool`) was **merged**. This new `ironclaw_reborn_migration` crate converts legacy IronClaw v1 and engine-v2 persisted state to Reborn's substrate without silent data loss.

- **CI benchmarking & optimization:** PR #5635 (bucketed Reborn crate tests, 12 named buckets replacing one-per-crate) was merged. PR #5638 (flip integration coverage to ratchet) and #5648 (benchmark narrower crate test targets) remain open. The OVH sccache addition to Reborn gateway smoke (#5606) was merged, cutting that job from ~48 minutes.

- **Static safety enforcement:** PR #5652 (deny `unused_must_use` workspace-wide) and PR #5651 (static enforcement that failures surface, not swallow) are both open – both zero-cost changes that will strengthen correctness guarantees.

- **Bug fix for agent-loop:** PR #5042 (single-line answers naming `__`-tools were misclassified and rejected) was **merged** after being open since June 17.

- **Documentation delivered:** PR #5383 (error recoverability audit + remediation plan) was merged, providing the blueprint for the two-bucket error strategy: security errors stop the run, all others must surface.

## Community Hot Topics

**Most commented/discussed items today:**

- **PR #5644 (77 files, Slack OAuth foundations)** — Near AI's BenKurrek's 2nd stack PR. Review thread includes detailed discussion on `SLACK_PERSONAL_OAUTH_SETUP_SCOPES` scope splitting (read vs chat:write opt-in), which spawned Issue #5650. The discussion centers on whether all 5 `slack_user` capabilities need the full 11-scope set including `chat:write` – a security-conscious design question about principle of least privilege.

- **PR #5626 (manifest-driven Slack ingress routes)** — Near AI's ilblackdragon's proposal to replace hand-written Rust policy literals with manifest-declared data. This is architecturally significant: it moves routing configuration from code to data, reducing the surface for policy drift.

- **PR #5649 (coverage-enabler batch)** — henrypark133's 3-commit PR adding bridged tool disclosure, WebUI V2/identity unlock, and trace-capture coverage for previously uncovered 0% crates. This is part of the ongoing push to make integration coverage ratcheted rather than informational (#5638).

**Underlying needs:** The team is actively managing scope/risk trade-offs in the Slack OAuth migration (scope granularity, backtracking compatibility), while simultaneously building the testing infrastructure to catch regressions (wiring parity, coverage ratchets). The high comment counts reflect that these are careful, security-conscious architectural decisions being made collectively.

## Bugs & Stability

**Ranked by severity:**

1. **[Medium] #5647 — Bridged tool disclosure strips bridge meta-tools (latent):** When >32-tool catalogs are deferred to bridge meta-tools, the synthetic `ironclaw.*` capability IDs are absent from granted capability sets. **No fix PR yet**, but it blocks the bridged disclosure coverage enabler in #5649.

2. **[Medium] #5640 — Harness gap: no RecordingSecurityAuditSink in integration harness:** The production local-dev build always wires `TracingSecurityAuditSink`, but the integration harness always gets `None`. **No fix PR yet** – surfaced by the wiring-parity tripwire (#5637/#5642).

3. **[Low] #5641 — `EXPECTED_PRODUCTION_SHAPE` is hand-derived, fragile:** The production shape constant must be manually re-derived when `build_reborn_runtime`'s literal changes. **No fix PR yet**, but acknowledged as technical debt.

4. **[Resolved] #5590 — Main branch CI checks green again:** Closed today. A sampling of failures (code style, live/browser QA) were addressed. The remaining concern is the persistent nightly E2E failure (#4108, open since May 27).

5. **[Persistent, Low Visibility] #4108 — Nightly E2E failed (open 39 days):** Still failing silently. Last updated July 4 with no comments. This may be a known flaky test or genuinely broken – the lack of discussion is concerning.

6. **[CI Infra] #5636 — CI job-level skips block Railway deploys:** Railway's "Wait for CI" treats skipped checks as failures. The team has identified the fix – use `cancelled()` instead of `skipped` – but the PR is not yet merged. This blocks `main` deployments when any job is intentionally skipped.

**Bug-fix PRs merged:** #5042 (single-line answer misclassification) – a minor but real user-facing bug.

## Feature Requests & Roadmap Signals

**Active feature work in progress (likely for next release):**

- **Slack Personal OAuth (4-PR stack, #5643–#5646):** The highest-priority feature. The stack removes pairing codes, adds OAuth flows, and breaks backward compatibility for legacy `[slack]` config fields. Likely to land as a coordinated merge in the next days.

- **Error recoverability (PR #5651, #5383):** Following the audit blueprint, the team is moving toward compile-time error-surface enforcement. This is a correctness/UX feature, not user-facing, but will reduce silent failures.

- **Integration coverage ratchet (#5638):** A quality insurance feature – once flipped, coverage drops will cause CI failure, preventing test regression.

- **Manifest-driven ingress (#5626):** If merged, Slack route configuration moves from Rust code to manifest data, which enables third-party extensions to declare their own ingress routes without modifying core.

**User-facing requests (implicit from issues):** The Slack OAuth work directly addresses user pain points around the outdated pairing-code flow. The coverage ratchet and wiring-parity guards are developer-facing quality measures that protect against regressions reaching users.

## User Feedback Summary

Based on the data, there is **little direct user feedback captured in this snapshot**. The project appears to be in a heavy development/infrastructure phase:

- **User pain point (observed):** Slack pairing-code flow is being replaced with OAuth, suggesting users found the old flow cumbersome. The breaking change to reject legacy `[slack]` config fields (#5646) will require operator action on upgrade.

- **User pain point (observed):** Nightly E2E tests keep failing (#4108) without clear communication to users – if these test failures correspond to real regressions, users may experience degraded functionality.

- **Satisfaction signal:** The team prioritizes the "no silent failure" principle (#5651, #5383, #5652), which indicates a commitment to reliable behavior that end users can depend on.

- **Developer pain point (inferred):** The wiring-parity tripwire (#5637) exists because harness drift has happened before, suggesting the integration test infrastructure has been fragile.

**Gap:** There are no feature requests, bug reports, or satisfaction signals from external (non-team) users in this snapshot. All activity appears to be from Near AI core contributors and the CI bot. The project may benefit from broader community engagement channels or a more accessible way to report user experiences.

## Backlog Watch

**Items needing maintainer attention:**

- **#4108 — Nightly E2E failed (open 39 days, zero comments):** This is the longest-running open issue with zero maintainer response. While it's auto-generated by `github-actions[bot]`, its persistence (last updated July 4, still failing) suggests either (a) known flakiness being tolerated, or (b) a real failure nobody has had bandwidth to investigate. **Recommendation:** Label as `known-flaky` or assign an owner to investigate.

- **#5598 — `chore: release` (open 2 days, 0 comments):** The release PR with breaking changes (0.24.0→0.29.1 for `ironclaw`) has no discussion and no merge. If this release is blocked, the Slack OAuth stack (which depends on these changes) cannot ship. **Recommendation:** Determine blocker – lack of review, conflicts, or intentional hold – and communicate.

- **#5170 — Fix subagent spawn run failure (open 12 days, 0 comments):** A core contributor PR from June 23 with no recent discussion. Subagent spawning is foundational to the agent loop; a bug here could block multi-agent workflows. **Recommendation:** Request reviewer or merge if ready.

- **#5304 — Enable final-answer nudge for interactive runs (open 9 days, 0 comments):** A small but user-visible improvement (prevents empty turns). Stalled with no discussion. **Recommendation:** Review and merge – it's low risk and user-facing.

- **#5641 — `EXPECTED_PRODUCTION_SHAPE` fragility (new today):** While not urgent, the team should consider fixing this before the next wiring-parity update catches someone off guard.

**Overall project health:** Strong. The team is delivering at high velocity with careful architecture reviews. The primary risk is release cadence – the unresolved release PR (#5598) and the magnitude of breaking changes in the Slack OAuth stack could create deployment friction. The persistent nightly E2E failure (#4108) and the deployment-blocking CI skip issue (#5636) are the two most urgent operational concerns.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

Here is the LobsterAI project digest for **2026-07-05**.

---

## LobsterAI Project Digest — 2026-07-05

### 1. Today's Overview
Project activity remains moderate but focused, with two merged pull requests (PRs) and one new open PR appearing in the last 24 hours. No new releases were published today, indicating the team is in a stabilization or patch phase. There is one open, stale issue regarding a file upload bug during task execution. Overall, the project appears healthy, with maintainers actively addressing technical debt (legacy config migration) and critical runtime bugs (proxy propagation), though community-facing features remain quiet.

### 2. Releases
*No new releases were published today.*

### 3. Project Progress
Two PRs were merged today, indicating focused bug fixing and housekeeping:

- **[PR #2272 (Closed)]** `fix(agent): migrate legacy AGENTS.md identity blocks to IDENTITY.md`
  - **Author:** fisherdaddy
  - **Summary:** This PR automatically detects and removes legacy identity content embedded in `AGENTS.md` files, ensuring each agent’s identity is managed solely via the new `IDENTITY.md` file. It includes backup and safe-failure mechanisms per agent.
  - **Impact:** Reduces configuration conflicts; improves maintainability of agent identity management.
  - **Link:** [PR #2272](https://github.com/netease-youdao/LobsterAI/pull/2272)

- **[PR #2271 (Closed)]** `fix: propagate system proxy to managed browser.`
  - **Author:** fisherdaddy
  - **Summary:** Ensures that the system-level HTTP/HTTPS proxy settings are correctly forwarded to the managed browser instance.
  - **Impact:** Fixes a critical connectivity issue for users behind corporate or privacy proxies.
  - **Link:** [PR #2271](https://github.com/netease-youdao/LobsterAI/pull/2271)

### 4. Community Hot Topics
The community’s attention is concentrated on two long-standing, stale issues that have seen recent updates:

- **[Issue #1352] (Open, stale)** "任务对话框，任务运行中，附件无法上传（点击上传附件无反应）"
  - **Author:** devilszy | **Comments:** 1 | **Updated:** 2026-07-04
  - **Summary:** During an active task, users report that clicking the attachment upload button yields no response.
  - **Analysis:** This bug blocks a core workflow (file handling during tasks). Despite its severity, it has been open since April without a fix PR.
  - **Link:** [Issue #1352](https://github.com/netease-youdao/LobsterAI/issues/1352)

- **[Issue #1350] (Open, stale)** "skills文件长时间生成阻塞无法感知，中间态过程无展示，用户无法进行下一步"
  - **Author:** jimmy-xz | **Comments:** 0 | **Updated:** 2026-07-04
  - **Summary:** Two related pain points: (1) generation of skill files blocks without progress indication, and (2) the same model prompt works correctly in `Openclaw` but fails in `LobsterAI`.
  - **Analysis:** This exposes a deeper inconsistency in model behavior and a UX gap (lack of intermediate state feedback). The community is frustrated by the "black box" feeling of the system.
  - **Link:** [Issue #1350](https://github.com/netease-youdao/LobsterAI/pull/1350) *(Note: This issue is filed as a PR)*

### 5. Bugs & Stability
- **(Severity: High)** #1352 — Attachment upload fails during active tasks. No fix PR exists yet.
- **(Severity: Medium)** #1350 — Skill generation blocks silently with no progress feedback; model interpretation diverges from `Openclaw`. This is both a reliability and UX regression.
- **Fixed today:** PR #2271 fixes a high-impact proxy propagation issue that could break all network-bound operations (browser, model API calls) for users behind a proxy.

### 6. Feature Requests & Roadmap Signals
- **UX / Transparency (from #1350):** Users are demanding visible progress indicators or intermediate thinking states during skill generation. This is a recurring theme—the system currently feels opaque when processing.
- **Model Consistency (from #1350):** The community expects the prompt interpretation to match the performance of `Openclaw` (the same underlying model). This suggests a potential divergence in prompt-preprocessing or context setup between the two products.
- **No new feature requests were filed today.** Current activity skews toward bug fixes and internal cleanup.

### 7. User Feedback Summary
- **Satisfaction:** No positive feedback recorded. The two closed PRs (proxy fix, identity migration) are internal improvements not directly praised by users.
- **Dissatisfaction / Pain Points:**
  - *Blocking workflows:* Users cannot upload attachments during tasks (#1352).
  - *Lack of feedback:* The system provides no progress or error messages during long operations, leaving users unsure whether a process is running or stuck (#1350).
  - *Model inconsistency:* The same prompt in `LobsterAI` vs `Openclaw` yields different results, eroding trust in the core reasoning engine (#1350).

### 8. Backlog Watch
- **Issue #1352 — High attention needed:** Open since April 2026, affecting a core task feature (attachment upload). Has been "stale" but recently updated. A fix or workaround is overdue.
- **Issue #1350 — Medium attention needed:** Also open since April, covering two actionable items (progress feedback, model parity). No maintainer response visible.
- **PR #1350 (Open):** This PR is actually an issue filed as a PR (see #1350 above). It has been updated twice but no discussion from the team. Needs a maintainer to convert it to an issue or clarify the submission format.

---

*End of digest.*

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

Based on the GitHub data from `agentscope-ai/CoPaw` (noted as `QwenPaw` in issues), here is the project digest for **2026-07-05**.

---

### CoPaw Project Digest – 2026-07-05

### 1. Today's Overview
The CoPaw project shows a **high level of bug-fix activity** with 11 issues updated in the last 24 hours, but a **slowing PR pipeline** with 3 open PRs and no merges. While the community is excited about the upcoming v2.0 release, the stability of the current 2.0.0b3 beta is under stress, with several significant regressions reported regarding memory management, context compression, and API compatibility. A major focus is currently on fixing the **auto-memory system** (PR #5777), which has been identified as fundamentally broken across sessions.

### 2. Releases
**No new releases** were published today. The latest versions remain `1.1.12` (stable) and `2.0.0b3` (beta).

### 3. Project Progress
- **No PRs merged or closed today.** The development focus appears to be on review and testing rather than landing new features.
- **Active PRs awaiting review:**
    - **PR #5777** (feat/memory): A critical fix for the auto-memory turn state management, directly addressing the core bug in Issue #5775. This is the most actionable PR currently open.
    - **PR #5597 & #5598** (feat/fallback): Backend and console UI for LLM fallback. These have been open for a week without movement, suggesting they may be waiting on the resolution of the more urgent memory bugs.

### 4. Community Hot Topics
- **Issue #5775 ([Bug] Auto-memory interval never triggers)**: This is the **most critical discussion** of the day. It reports that the core memory persistence feature in v2.0.0b3 is completely broken due to state loss. The presence of PR #5777 shows the maintainers are actively working on this. [Link](agentscope-ai/QwenPaw Issue #5775)
- **Issue #5778 ([Bug] scroll compression loses context)**: A high-impact regression in v2.0. Users report that the new "scroll" compression strategy destroys conversation context, causing the agent to lose track of tasks. This is a fundamental UX issue for the new version. [Link](agentscope-ai/QwenPaw Issue #5778)
- **Issue #2865 ([Feature] Custom agent names/avatars)**: This is the **longest-standing open feature request** (since April 3rd). With 4 comments and 1 reaction, it represents a persistent desire for UI personalization. [Link](agentscope-ai/QwenPaw Issue #2865)

### 5. Bugs & Stability
The project is currently under significant bug-fix pressure, especially around the v2.0 beta. Bugs ranked by severity:

1.  **Critical – Memory System Failure (Issue #5775)**: Auto-memory fails entirely due to state loss across requests. **Fix in progress via PR #5777.**
2.  **Critical – Context Compression Regression (Issue #5778)**: The new "scroll" compressor in v2.0 destroys context and breaks `reasoning_content` for thinking models.
3.  **High – IM Context Staleness (Issue #5776)**: In long-lived sessions (e.g., QQ), the agent treats old, pinned messages as the current active task, leading to erratic behavior.
4.  **Medium – Provider Specific Failures**:
    - **Issue #5773**: Memory search breaks the OpenCode Go (OCG) provider entirely.
    - **Issue #5774**: Google/Gemini channel is experiencing errors.
5.  **Low – Logging and API Issues**:
    - **Issue #5779**: Cron state API returns UTC time ignoring timezone config.
    - **Issue #5771**: Debug logs incorrectly use `WARNING` level, causing log spam.

### 6. Feature Requests & Roadmap Signals
- **High Demand (Likely v2.0):** The community strongly desires **custom agent names and avatars** (Issue #2865). Given the UI changes in v2.0, this is a strong candidate for the final release.
- **In Progress (Targeting v2.0 stable):** The **LLM model fallback** feature (PRs #5597, #5598) is under active development. This suggests redundancy and reliability are a focus for the next stable release.
- **Community Sentiment (Issue #5770):** A user expressed high anticipation for the "amazing" v2.0 official release. This positive sentiment contrasts with the current bug reports, indicating high hopes for a polished final product.

### 7. User Feedback Summary
- **Pain Points (v2.0 Beta Stability):** Users are experiencing severe regressions. The new compression strategy is destroying conversation history, and the auto-memory feature is non-functional. The community is bearing the brunt of the beta instability.
- **Use Case Conflicts:** The memory issues are causing real workflow disruptions. One user reports an AI that cannot remember a task from five days ago (Issue #5776), while another reports an AI that compresses all context into "a few fuzzy titles," making it useless for ongoing tasks (Issue #5778).
- **Satisfaction:** There is a high level of goodwill and excitement for the v2.0 feature set, but current satisfaction with the `2.0.0b3` stability is low due to these core memory/context regressions. Users largely appreciate the active bug reporting and quick PR responses (e.g., PR #5777).

### 8. Backlog Watch
- **Issue #2865 ([Feature] Custom agent names/avatars)**: This is the **most critical backlog item**. Updated yesterday but created in April. It is a highly requested feature with no update from maintainers regarding its inclusion in v2.0. [Link](agentscope-ai/QwenPaw Issue #2865)
- **PRs #5597 & #5598 (LLM Fallback):** These two PRs have been open for 6 days with no merge activity. They represent a significant new feature (model fallback) that is likely desired for the v2.0 stable release. The delay may be due to the team prioritizing the critical memory bugs.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

# ZeroClaw Project Digest — 2026-07-05

## Today's Overview

ZeroClaw shows **high development velocity** heading into the v0.8.3 release cycle, with 50 issues and 50 PRs updated in the last 24 hours. The project is actively integrating the **goal-mode feature** across channels, runtime, and tools via a coordinated tracker (#8681) split across multiple large PRs (#8687, #8688, #8689). A critical **S1 bug** (#8193) blocking MCP tool discovery in TUI sessions was closed, alongside ongoing work to stabilize provider compatibility and SOP engine integrity. With 49 open PRs and 39 active issues, the maintainers are managing a substantial work-in-progress load, but tracker-driven organization and label automation (RFC #6808) are helping keep scope bounded.

## Releases
**No new releases today.** The project remains in the v0.8.x series, with v0.8.3 being the active development target tracked across multiple coordination issues (#8360, #8071, #7314, #8073).

## Project Progress

**PRs merged/closed today: 1**
- **#8723** — `fix(security): preserve generated file references in leak scans` (vrurg): Addresses high-entropy token redaction false positives for legitimate file references (related to #8722, #4832). Merged into `master`.

**Feature work advancing:**
- **Goal-mode implementation** (vrurg, PRs #8687, #8688, #8689): Three XL-sized PRs delivering the goal controller/verifier, trusted goal tools with delegation boundaries, and channel `/goal` command admission. These are split from the `feat/goal-mode` branch per tracker #8681.
- **Telegram multi-message streaming** (#8561, metalmon): Adds `multi_message_delay_ms` config and `StreamMode::MultiMessage` with agent turn boundaries.
- **OpenAI Bridge channel** (#8710, titilambert): New channel exposing OpenAI-compatible HTTP endpoints for third-party tool integration (Home Assistant, etc.).
- **SOP visual authoring surfaces** (#8590, singlerider): XL PR adding SOP authoring UI with channel fan-in, tests, and docs — tagged for beta testers.
- **Cron `uses_memory` flag exposure** (#8676, databillm): CLI, tool, and gateway API now expose the per-job stateless-run flag.
- **Model context window UI** (#7946, eugeneb50): Context usage bar added to TUI, gateway chat, and CLI interactive mode.
- **Typed slash-command editor** (#8620, Nillth): WebUI editor for skill bundle slash-command options.

## Community Hot Topics

1. **#8193** [CLOSED] — *MCP tools/tool_search missing from TUI sessions* (15 comments)
   - S1 bug where MCP servers expose tools but ZeroCode TUI sessions don't receive them. Gateway sees the tools but sessions show empty tool list. **Now closed** — fix likely included in runtime/gateway sync improvements.
   - [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8193)

2. **#6808** [OPEN] — *RFC: Work Lanes, Board Automation, and Label Cleanup* (13 comments)
   - Governance RFC for routing work without manual board maintenance. Status: accepted, rollout in progress. Proposes label-based automation and tracker markers (codified today by PR #8715).
   - [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/6808)

3. **#8681** [OPEN] — *Tracker: Goal mode implementation split stack* (7 comments)
   - New tracker from vrurg coordinating the split of goal-mode work into reviewable PRs from `feat/goal-mode`. The three PRs (#8687, #8688, #8689) posted concurrently show a coordinated landing.
   - [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8681)

## Bugs & Stability

**Critical (S1 — workflow blocked):**
- **#8675** [OPEN] — *Malformed native tool-call arguments sent unvalidated to OpenAI-format providers* (metalmon): Provider 400 errors when models emit non-JSON tool arguments. No fix PR yet but tracker #8360 covers provider serialization.
  - [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8675)
- **#8654** [OPEN] — *skill-review fork panics with out-of-range slice → SIGSEGV* (tw-360vier): Background skill review crashes the entire agent process with `panic = abort`. No fix PR posted yet.
  - [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8654)

**High severity (S2 — degraded behavior):**
- **#8695** [OPEN] — *Cron jobs recall memory when `uses_memory = false`* (databillm): The flag only suppresses scheduler prefix, not memory context. A companion PR #8676 exposes the flag to CLI but doesn't fix the runtime behavior.
  - [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8695)
- **#8678** [OPEN] — *SOP approval gate bypass via advance_step* (Stalesamy): Driver can call `sop_advance` without run-status guard. Security concern for SOP integrity.
  - [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8678)
- **#8615** [OPEN] — *Compatible provider silently deletes content via unconditional `<think>` tag stripping* (NiuBlibing): Unclosed think tags produce empty replies; users lose content invisibly.
  - [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8615)
- **#8722** [OPEN] — *High-entropy detector redacts legitimate generated filenames* (vrurg): False positives on random filenames. Fix PR #8723 was **merged** today addressing this.
  - [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8722)
- **#8664** [OPEN] — *ZeroCode code-block Copy includes Markdown fences* (Audacity88): Copy function includes backtick lines.
  - [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8664)
- **#8646** [OPEN] — *ZeroCode Logs detail hides event attributes* (Audacity88).
  - [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8646)

**Recently closed bugs:**
- **#8193** (MCP tools missing from TUI) — CLOSED
- **#6891** (Scheduled Jobs edit API 422) — CLOSED
- **#7862** (OpenAI-compat sends empty tools list to vLLM) — CLOSED
- **#8359** (Memory embeddings don't refresh provider profile) — CLOSED
- **#8636** (Plugin system follow-ups) — CLOSED

## Feature Requests & Roadmap Signals

**Goal-mode ecosystem** is the dominant theme — with #8681 as the tracker and three XL PRs in review, this is the highest-priority feature for v0.8.3. It adds:
- Goal controller/verifier with restart recovery
- Channel `/goal` commands (start, pause, resume, cancel)
- Trusted goal tools with delegation boundaries

**SOP improvements** continue to generate user demand:
- **#8719** [NEW] — *False `when` should advance to next SOP step, not end run* (metalmon): Enables multi-phase SOPs with loop → finalize flow.
  - [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8719)
- **#8587** [OPEN] — *Missing detailed SOP syntax examples in docs* (susyabashti).
  - [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8587)

**Provider / reliability:**
- **#8721** [OPEN] — *Fail over on Anthropic refusal so downgrade is surfaced* (IftekharUddin): PR to handle Claude 4+ safety refusals that return HTTP 200 with empty content.
  - [Link](https://github.com/zeroclaw-labs/zeroclaw/pull/8721)

**New channel:**
- **#8710** — OpenAI Bridge channel for third-party OpenAI client compatibility (titilambert). Signals breadth expansion beyond native channels.
  - [Link](https://github.com/zeroclaw-labs/zeroclaw/pull/8710)

## User Feedback Summary

**Pain points:**
- **MCP tool visibility** (#8193): Two users reported MCP tools connecting but not appearing in TUI — this was a major workflow blocker now resolved.
- **Provider silent failures** (#8615, #8675): Users on compatible providers (vLLM, OpenRouter) face invisible content loss and 400 errors from malformed tool calls — trust in non-OpenAI providers is eroding.
- **Cron job memory behavior** (#8695, databillm): User expected `uses_memory = false` to fully disable memory recall; the partial implementation is confusing and breaks stateless workflows.
- **High-entropy detector false positives** (#8722, vrurg): User's generated filenames are redacted as secrets — legitimate output is corrupted.
- **SOP routing** (#8719, metalmon): User needs multi-phase SOPs where false conditions advance rather than terminate — current behavior blocks complex approval workflows.

**Satisfaction signals:**
- The **SOP visual authoring PR** (#8590) explicitly calls for beta testers, suggesting confidence in the feature's maturity.
- The **goal-mode** work is being carefully split (#8681) into reviewable chunks, indicating disciplined engineering despite high velocity.
- Third-party plugin validation (#8636) was completed and follow-ups resolved — the plugin authoring guides are producing working external plugins.

## Backlog Watch

**Issues needing maintainer attention:**
- **#4832** [OPEN since March 27] — *Add config option to disable LeakDetector high-entropy token redaction* (whtiehack, 4 comments): User has been waiting over 3 months for a config toggle. While #8723 was merged today with a programmatic fix, the user explicitly requested user-facing configuration — this gap may persist.
  - [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/4832)

- **#7497** [OPEN since June 11] — *RFC: OCI-Compliant Container Registries as Plugin Storage* (bheatwole, 3 comments): Blocked RFC for WASM plugin distribution via OCI registries. No maintainer response visible in last 3 weeks. With WASM plugin program progressing (#7314 tracker), this RFC needs resolution.
  - [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/7497)

- **#8720** [OPEN, today] — *Disable cachePoint for Bedrock Nova 2 Lite model* (ngamradt): New support request for config-based cache disabling. No response yet.
  - [Link](https://github.com/zeroclaw-labs/zeroclaw/issues/8720)

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*