# OpenClaw Ecosystem Digest 2026-07-04

> Issues: 314 | PRs: 500 | Projects covered: 13 | Generated: 2026-07-04 01:59 UTC

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

# OpenClaw Project Digest — 2026-07-04

## Today's Overview

Project activity remains very high, with **314 updated issues** (222 open) and **500 updated pull requests** (445 open) in the last 24 hours. A significant portion of activity centers on **consolidation/refactoring efforts** led by maintainer `RomneyDa`, who submitted ~10 PRs today unifying security, abort, HTTP, and TTS primitives across the codebase. The bug queue shows concentrated attention on **session-state integrity**, **message delivery reliability**, and **compaction/stability** regressions, with multiple diamond-lobster-rated issues remaining open and awaiting maintainer or product decisions. No new releases were published today.

---

## Releases

**No new releases** recorded for 2026-07-04. The most recent published version remains `v2026.6.11`, which itself carries a known regression (Issue #98416) where a published dist was missing a reentrancy guard, causing reply session initialization conflicts.

---

## Project Progress

**Merged/closed PRs:** 55 of 500 updated PRs were merged or closed. Notable merged contributions include:
- **#99748 — `fix(embedded-agent): strip stale thinking signatures on replay_invalid retry`** — Fixes permanent `replay_invalid` rejection after provider changes.
- **#99749 — `fix #99712: surface empty interactive replies`** — Addresses silent empty return from interactive direct replies.
- **#99750 — `refactor: consolidate exact boolean coercion`** — Unifies trimming/case-folding contracts across core and plugin paths.
- **#99751 — `fix: make @openclaw/llama-cpp-provider install never fail`** — Prevents installation failures on incompatible systems by making `node-llama-cpp` postinstall configurable.
- **#99754 — `fix: make Codex event projector fail closed on protocol drift`** — Treats unknown Codex item statuses as failed, with one-time warnings per drift type.

The broader refactoring wave (#99740, #99744, #99746, #99753, #99755) consolidates tool-result helpers, bounded HTTP reads, secret masking/comparison, abort primitives, and deferred promises into shared infrastructure — reducing audit surface and drift risk across plugins.

---

## Community Hot Topics

**Most active issues (by comment count):**

1. **#25592 — Text between tool calls leaks to messaging channels** (33 comments, 1 👍)  
   *Status: OPEN, diamond lobster, stable*  
   Users report that internal processing output (error handling, narration) leaks to Slack/iMessage channels as visible messages. This is a significant UX and security concern — the community is pressing for a routing isolation mechanism.  
   [Issue link](https://github.com/openclaw/openclaw/issues/25592)

2. **#99551 — Codex worker runaway hardening sprint tracker** (14 comments, 1 👍)  
   *Status: OPEN, diamond lobster*  
   A high-urgency tracker for hardening failure modes exposed by incident worker `019f18dc-...`. Child issues include Codex tool advertisement conflicts and prompt-injection safeguarding.  
   [Issue link](https://github.com/openclaw/openclaw/issues/99551)

3. **#73148 — Image tool: opaque "Failed to optimize image" when sharp is not installed** (14 comments, 3 👍)  
   *Status: OPEN, stale, P2*  
   The vision pipeline fails with a non-descriptive error on every image when `sharp` is absent. Users want a clear dependency hint.  
   [Issue link](https://github.com/openclaw/openclaw/issues/73148)

4. **#12602 — Slack Block Kit support for agent messages** (13 comments)  
   *Status: OPEN, P2, enhancement*  
   Agents can only send plain text/markdown to Slack. CRM summaries, database results, and action confirmations need richer formatting.  
   [Issue link](https://github.com/openclaw/openclaw/issues/12602)

5. **#10659 — Masked Secrets: prevent agent from accessing raw API keys** (13 comments, 4 👍)  
   *Status: OPEN, P1, diamond lobster*  
   Users want a system where agents can *use* API keys without *seeing* them — protecting against accidental leaks and prompt injection.  
   [Issue link](https://github.com/openclaw/openclaw/issues/10659)

**Underlying needs:** The community is demanding stronger **security boundaries** (leak prevention, permission manifests, denylists), **reliable message delivery** (text-leak prevention, fallback delivery), and **richer channel integrations** (Slack Block Kit, WhatsApp stickers, Telegram parse modes).

---

## Bugs & Stability

**High-severity open bugs (P1, diamond lobster):**

1. **#98416 — v2026.6.11 published dist missing reentrancy guard** (11 comments, 5 👍)  
   Reply session initialization is conflicted on the latest release. No fix PR yet.  
   [Issue link](https://github.com/openclaw/openclaw/issues/98416)

2. **#92043 — 180s compaction timeout fails identically every turn** (11 comments, 3 👍)  
   A single wall-clock timeout over the entire chunk pipeline with no partial-progress reuse means slow-but-legitimate compactions fail perpetually.  
   [Issue link](https://github.com/openclaw/openclaw/issues/92043)

3. **#38327 — "Cannot convert undefined or null to object" with google-vertex/gemini-3.1** (10 comments, 3 👍)  
   Regression in v2026.3.2 affecting Vertex AI users. No fix PR linked.  
   [Issue link](https://github.com/openclaw/openclaw/issues/38327)

4. **#85714 — Agent's final message stranded when LLM forgets delivery tool** (8 comments)  
   No fallback delivery from `task_complete` — responses silently lost.  
   [Issue link](https://github.com/openclaw/openclaw/issues/85714)

5. **#78562 — Repeated tool-loop context overflows cause successive auto-compactions** (5 comments, 2 👍)  
   Each compaction succeeds, but next tool-loop immediately overflows — user sees repeated "compacting..." messages.  
   [Issue link](https://github.com/openclaw/openclaw/issues/78562)

6. **#98437 — MCP loopback bundle emits thousands of `conflicting schema definitions` warnings per day** (5 comments)  
   Every init emits one warning per shared field name — severe log pollution.  
   [Issue link](https://github.com/openclaw/openclaw/issues/98437)

**Recently closed bugs:** #98528 (Tool output returns empty after first call per turn — v2026.6.11 regression, closed), #97871 (Agent `--local` hangs with Ollama/LM Studio — closed), #75593 (Subagents list empty after spawn — closed).

**Fix PRs in flight:** #99756 (text tool results ahead of stale media placeholders, closes #99241), #99747 (protect uncovered cleanup window in Codex app-server), #99745 (harden Telegram rich send fallback and typing breaker).

---

## Feature Requests & Roadmap Signals

**High-demand features (P1/P2, diamond lobster/platinum hermit rating):**

| Feature | Issue | Priority | Likely Timeline |
|---|---|---|---|
| **Masked Secrets** (agents cannot see API keys) | #10659 | P1 | High — aligns with security sprint #99551 |
| **Capability-based permissions** (default-deny for tools/skills) | #12678 | P2 | Medium — complements manifest standard |
| **Per-agent plugin config overrides** | #55401 | P2 | Medium — multi-agent setups growing |
| **Dynamic model discovery** (OpenRouter) | #10687 | P2 | Medium-high — fast-moving catalogs |
| **Slack Block Kit support** | #12602 | P2 | Medium — long-standing request |
| **Self-update with backup + health check + auto-rollback** | #14526 | P2 | Medium — production ops need |
| **Cron job hooks system** (pre/post triggers) | #9465 | P2 | Lower — nice-to-have vs. stability bugs |
| **Per-spawn tool restrictions for sub-agents** | #15032 | P2 | Medium — prompt injection defense |

**Prediction for next release:** The **Masked Secrets** (#10659) and **capability-based permissions** (#12678) features are strong candidates — they directly address the security hardening goals of the Codex worker runaway sprint (Issue #99551) and have maintainer attention. The **dynamic model discovery** (#10687) is also likely given fast-moving provider catalogs.

---

## User Feedback Summary

**Common pain points:**
- **Message leak / delivery confusion**: Internal processing text routes to Slack/iMessage (Issue #25592), final agent messages get stranded when delivery tool is forgotten (#85714), tool outputs degrade to `(see attached image)` placeholders (#96857, #99241).
- **Compaction / context reliability**: Repeated compaction loops (#78562), 180s timeout too aggressive (#92043), memory_search "index metadata is missing" despite valid index (#90361).
- **Security friction**: No way to restrict tool access for sub-agents (#15032), no denylist for exec-approvals (#6615), skills run with full trust (#12219).
- **Multi-agent complexity**: Cannot configure plugins per-agent (#55401), spawned agents inherit full tool access (#15032), sub-agent announce cannot be suppressed cleanly (#8299).
- **UI/UX gaps**: TUI lacks multi-line input (#10118), iOS chat doesn't trigger assistant replies reliably (#97983), no plain-text copy option (#7909), accessibility issues with emojis/unicode (#9637).

**Positive signal:** Multiple users are actively deploying multi-agent gateways, voice calls, and Telegram/WhatsApp bots — indicating strong production adoption despite stability gaps.

---

## Backlog Watch

**Long-unanswered important items needing maintainer attention:**

1. **#73148 — Image tool: opaque error when sharp is not installed** (14 comments, 3 👍, P2, *stale*)  
   Last updated 2026-04-28, no fix PR. A clear error message would be trivial to implement.  
   [Issue link](https://github.com/openclaw/openclaw/issues/73148)

2. **#83600 — `feat(whatsapp): support list reply actions`** (PR, P2, *stale*)  
   Labeled `⏳ waiting on author` since 2026-05-18. Large PR with video proof — likely needs a maintainer to unblock.  
   [PR link](https://github.com/openclaw/openclaw/pull/83600)

3. **#58373 — `fix(agents): bootstrap non-main models.json on skip`** (PR, P1, *waiting on author*)  
   Critical bug fix for `Unknown model` errors on `agents.create`. Awaiting author since 2026-03-31.  
   [PR link](https://github.com/openclaw/openclaw/pull/58373)

4. **#10687 — Dynamic model discovery for OpenRouter** (P2, 9 comments, 3 👍, *needs product decision*)  
   Last maintainer touch: none since issue creation. Current static catalog approach is a growing pain point.  
   [Issue link](https://github.com/openclaw/openclaw/issues/10687)

5. **#12678 — Skill Permission Manifest Standard (skill.yaml)** (P2, 6 comments, *needs security review*)  
   Foundational for skill ecosystem trust. Security review label applied but no movement reported.  
   [Issue link](https://github.com/openclaw/openclaw/issues/12678)

**Assessment:** The backlog of stale but high-value PRs (#83600, #58373) suggests a maintainer bottleneck in reviewing large, complex contributions. The consolidation wave today (RomneyDa's PRs) may be a deliberate effort to reduce future review friction by sharing infrastructure.

---

## Cross-Ecosystem Comparison

Here is the cross-project comparison report.

---

### 1. Ecosystem Overview

The personal AI agent open-source landscape on this date is characterized by intense, concurrent development across a spectrum of projects, driven by a shared ambition to build reliable, secure, and multi-modal assistant infrastructure. Activity is bifurcated: larger, more established projects like **OpenClaw** and **IronClaw** are deep into major architectural refactoring (unification/consolidation and the "Reborn" migration, respectively), while others like **ZeroClaw** and **NanoBot** are rapidly iterating to stabilize core features, fix critical regressions, and expand channel integrations (WhatsApp, Telegram, Mattermost). A strong community focus on security boundaries, message delivery reliability, and context management is evident across all projects, indicating the ecosystem is maturing from a prototype phase into a focus on production-grade operation.

### 2. Activity Comparison

| Project | Updated Issues (24h) | Updated PRs (24h) | New Release Status | Overall Health Score |
|---|---|---|---|---|
| OpenClaw | 314 | 500 | No new release | ★★★☆☆ (High activity but high bug count) |
| IronClaw | 33 | 50 | No new release | ★★☆☆☆ (High velocity, but CI is red, bugs mounting) |
| ZeroClaw | 36 | 50 | No new release | ★★★★☆ (High activity, fix velocity high, stable core) |
| LobsterAI | 1* | 16 | **Yes (v2026.7.3)** | ★★★★★ (Rapid bug-fix sprint, stable release) |
| CoPaw | 39 | 33 | No new release | ★★★☆☆ (Very active, two-track development, v2.0 beta bugs) |
| NanoBot | 29 | 38 | No new release | ★★★★☆ (Healthy cadence, strong on core improvements) |
| Hermes Agent | 50 | 50 | No new release | ★★☆☆☆ (High activity, but high bug count, security concerns) |
| PicoClaw | 2* | 17 | **Yes (v0.3.1)** | ★★★★☆ (Burst of stability fixes, low new issues) |
| NanoClaw | 1 | 17 | No new release | ★★☆☆☆ (Low new issues, but high PR backlog) |
| NullClaw | 1 | 0 | No new release | ★★☆☆☆ (Minimal activity, single bug reported) |

*Note: For LobsterAI and PicoClaw, the issue count may be undercounted due to the source data focusing on the most recent day's updates.

### 3. OpenClaw's Position

**OpenClaw** maintains its position as the ecosystem’s core reference implementation, evidenced by an order-of-magnitude higher volume of issues and PRs. Its primary advantage is **architectural consolidation**, seen today in maintainer `RomneyDa`'s wave of PRs unifying security, abort, HTTP, and TTS primitives across the codebase. This reduces audit surface and drift risk for downstream projects.

- **Advantages vs. Peers:** Superior refactoring discipline; largest plugin ecosystem; most extensive channel integration support (WhatsApp, Telegram, Matrix).
- **Technical Approach Differences:** More conservative, focusing on codebase quality and bug fixes rather than the experimental feature velocity seen in ZeroClaw or the Reborn architecture migration of IronClaw.
- **Community Size:** The 500 updated PRs in 24 hours dwarf all other projects, indicating the largest contributor base.

**Key Weakness:** The sheer volume of open, high-severity bugs (session-state integrity, message delivery, compaction) is a significant stability risk. The project is a victim of its own success—the complexity of the codebase and broad contributor base are outpacing the maintainers' ability to merge fixes.

### 4. Shared Technical Focus Areas

The following requirements are emerging across multiple projects, representing the ecosystem's consensus on critical next steps:

- **Security Boundaries & Secret Management:** Several projects are explicitly building mechanisms to protect API keys and sensitive data.
    - **OpenClaw** (#10659): "Masked Secrets" feature to prevent agents from seeing raw keys.
    - **Hermes Agent** (#48441, #58006, #58007): Fixing terminal session snapshot leaks and credential isolation.
    - **ZeroClaw** (#7141/#8672): Multi-user auth (OIDC, SSH, peercred) with permission profiles.
    - **CoPaw** (#5705): Request for env-var key fallbacks and log sanitization.

- **Message Delivery Reliability & Channel Awareness:** A systemic problem where agents forget context or deliver messages to the wrong location.
    - **OpenClaw** (#25592): Text leaks from internal processing to public channels.
    - **NanoBot** (#4044): "Short term memory loss" after context window pressure.
    - **CoPaw** (#5746, #5710): Context compression causing agents to forget the channel they are in.
    - **NullClaw** (#972): Telegram channel stops responding after idle time.

- **MCP (Model Context Protocol) Reliability & Resilience:** Handling MCP server failures, schema bloat, and connection drops.
    - **OpenClaw** (#98437): MCP loopback warnings causing log pollution.
    - **NanoBot** (#4652, #4302): Process crashes on MCP tool errors and reconnection issues.
    - **NanoClaw** (#2917): MCP tool schema overhead (~27k tokens) crippling local model performance.
    - **CoPaw** (#5755): Making agent config resilient to invalid MCP client configs.

- **Cross-Platform Stability (Windows):** Windows users are frequently reporting regressions and reliability issues.
    - **IronClaw** (#5603): CI failing due to Windows unused import.
    - **ZeroClaw** (#7462): 74 undetected test failures on Windows.
    - **Hermes Agent** (#56747): Blank console windows flashing on desktop GUI.
    - **CoPaw** (#5525, #4481): Native sandbox fix merged, but GBK encoding remains unresolved.

### 5. Differentiation Analysis

| Project | Primary Focus | Target User | Key Differentiator |
|---|---|---|---|
| OpenClaw | Core Reference, Consolidation | Plugin developers, integrators | Largest ecosystem, codebase stability focus |
| ZeroClaw | Team/Enterprise, Governance | Teams, SRE, power users | SOP engine, multi-user auth (OIDC), WASM plugins, Goal Mode |
| IronClaw | Re-architecture, Production | Enterprise/Power users | "Reborn" architecture migration, WASM credentials, manifest-driven ingress |
| Hermes Agent | Gateway, Multi-Profile | Intermediate/Advanced | Multi-platform gateways, desktop app, MCP customization |
| NanoClaw | Productivity, Channel Expansion (LINE) | Asian market, consumers | Channel-specific integration (LINE, Signal, CalDAV) |
| PicoClaw | Lightweight, Mobile | Mobile-first, hobbyists | Low resource footprint, v0.3.1 release fixing WhatsApp/Config |
| NanoBot | Simplicity, Core Stability | General users, beginners | Low bug count, focused on fixing core (MCP crashes, context window) |
| LobsterAI | Collaborative Workspace | Development teams | "Cowork"/Goal Mode for multi-agent workspaces |
| CoPaw | Multi-Instance, Enterprise (China) | Enterprise (China), Windows users | Two-track dev (1.1.x stable, 2.0 beta), strong UI focus |
| NullClaw | Minimalist, Telegram-focused | Hobbyists, single-channel | Extremely small scope, low activity |

### 6. Community Momentum & Maturity

- **Tier 1: High-Momentum, High-Maturity (Rapid iteration, stable for power users)**
    - **ZeroClaw**: Highest velocity on core features (SOP, WASM, OIDC). Multiple bug-fix PRs in flight. Stable core.
    - **LobsterAI**: Released a new version (2026.7.3) with a 87.5% close/merge rate. Aggressive on UI/UX.
    - **PicoClaw**: Released a patch (v0.3.1) focused on WhatsApp and config migration stability.

- **Tier 2: Heavy Development, "Breaking Things to Fix Them" Phase**
    - **IronClaw**: "Reborn" migration is past substrate but hardening uncovered critical bugs. Red CI is a blocker.
    - **OpenClaw**: Huge contributor base, but high bug count and maintainer bottleneck on merging large fixes.
    - **CoPaw**: High activity split between stable (1.1.x) and beta (v2.0) tracks, with significant beta community reporting context and API bugs.

- **Tier 3: Stabilizing/Moderate Activity**
    - **NanoBot**: Healthy cadence, focused on core fixes (MCP crashes, memory loss). Predictable v0.3.0 target.
    - **Hermes Agent**: High activity but with a significant number of open P1/P2 bugs and security concerns.

- **Tier 4: Low Activity / Hobbyist**
    - **NanoClaw**: Low issue generation but a high PR backlog.
    - **NullClaw, TinyClaw, Moltis, ZeptoClaw**: Minimal to zero activity; these projects are either stable, stalled, or maintainer-limited.

### 7. Trend Signals

1.  **The "WASM-in-a-Sidecar" Security Model is Gaining Traction.** ZeroClaw’s prototype (#8661) to execute plugins out-of-process via a sidecar, combined with IronClaw’s WASM credential work and OpenClaw’s "Masked Secrets" requests, signals a shift towards **memory-safe, sandboxed plugin execution** as the baseline expectation for production agents. This is a direct response to prompt injection and secret leakage threats.
2.  **Deterministic Workflows (SOPs) are the Next Frontier.** ZeroClaw’s "Standard Operating Procedure" engine is the most mature example, but the community's frustration with context loss and "random" agent behavior (NanoBot's #4044, CoPaw's #5746) implies a strong demand for **more predictable, auditable agent execution**. This is moving beyond simple task automation into structured, defensible agent behavior.
3.  **Multi-User/Session Isolation is an Unmet Enterprise Need.** Multiple projects have open issues (OpenClaw #12678, NanoBot #3744, ZeroClaw #7141, Hermes #58006) demanding proper principal isolation, authentication, and permission profiles. This indicates the market is shifting from single-user toys to multi-tenant operations, a critical prerequisite for enterprise adoption.
4.  **MCP Adoption has Exposed a Scalability and Trust Crisis.** The initial enthusiasm for MCP is being tempered by real-world problems: **schema bloat** (NanoClaw's 27k tokens overhead), **process crashes** from tool errors (NanoBot), and **unresolved security certification** (CVE drift on wasmtime). The ecosystem is learning that MCP is a powerful protocol, but its naive integration introduces significant operational and security risks that require new infrastructure (sidecars, validation layers, cost governors) to manage.
5.  **The "Always-On" Gateway is a Double-Edged Sword.** Projects with real-time gateways (NullClaw, PicoClaw, Hermes, OpenClaw) are all reporting a common failure pattern: the **gateway dies silently after idle periods** (NullClaw #972, PicoClaw #3179, Hermes #57903). This is a classic "solved" problem (keep-alive pings, reconnection loops) that is apparently being re-solved independently by each project, suggesting a lack of a shared base library for gateway connectivity. This is a prime area for ecosystem-level standardization.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

Here is the NanoBot project digest for **2026-07-04**.

---

## NanoBot Project Digest – 2026-07-04

### 1. Today's Overview
NanoBot shows **high activity** today with 29 updated issues and 38 updated PRs in the last 24 hours, indicating a healthy development cadence. The project is focused on **stability and core improvements**, with significant attention to fixing crashes caused by MCP tool exceptions and resolving context window management bugs. A strong community presence is evident, with several community-contributed PRs targeting memory consolidation, plugin controls, and new channel integrations (Mattermost). The project released no new versions today, but the intense PR activity signals an upcoming patch release.

### 2. Releases
**No new releases** were published on this date.

### 3. Project Progress
Six PRs were closed or merged today, reflecting several key fixes and features advancing to the main branch.

- **#4687** `fix(providers): update Anthropic default model to claude-sonnet-4-6` – Updated the stale default model (from May 2025) to the current version across the codebase and documentation.
- **#4685** `fix: omit temperature for sonnet 5` – Resolves a regression where the Anthropic provider sent a `temperature` parameter to `claude-sonnet-5`, which now rejects it (fixes #4683).
- **#4632** `feat(providers): add Anthropic OAuth` – New provider supporting Claude Code tokens from `claude setup-token`, allowing use without an API key.
- **#4396** `Add optional Nanobot plugin controls` – Lighter plugin-style flow for managing optional features (chat, providers, documents) across CLI and WebUI.
- **#4691** `fix(plugins): polish optional feature controls` – Safety polish for the new plugin system, adding warnings for missing dependencies and improving recovery paths.
- **#4688** `feat(cli): add safe WebUI first-run launcher` – New `nanobot webui` command that safely creates/loads config and checks provider setup before starting the gateway.

### 4. Community Hot Topics
The most active discussions reveal deep concerns about **memory management and context continuity**, which directly affect user trust in the assistant.

- **#4044** `[bug] short term memory loss` (6 comments) – The top concern: the agent asks a question, receives an answer, but has no memory of having asked. Users pinpoint root causes as context window pressure or memory consolidation problems. **Link: [Issue #4044](https://github.com/HKUDS/nanobot/issues/4044)**
- **#3744** `[enhancement] session级别MEMORY功能请求` (5 comments) – Multi-user session memory isolation, specifically asking how `USER.md` and `MEMORY.md` mechanisms work when multiple IM users share a single agent. **Link: [Issue #3744](https://github.com/HKUDS/nanobot/issues/3744)**
- **#3846** `[enhancement] enhance: keep skill content in multi-turn conversations` (5 comments, 1 👍) – Users report that skill definitions are not persisted across turns, forcing the agent to reload them via `read_file` each time. **Link: [Issue #3846](https://github.com/HKUDS/nanobot/issues/3846)**
- **#4061** `Bug: OpenAI-compatible text-format tool calls are not parsed` (6 comments) – Some providers emit tool calls as plain text in assistant content instead of structured `tool_calls`, causing raw markup to be shown to users. **Link: [Issue #4061](https://github.com/HKUDS/nanobot/issues/4061)**

### 5. Bugs & Stability
Several bugs were reported, with the **most critical being process crashes** in production environments. Fix PRs already exist for the top two issues.

| Severity | Issue # | Description | Fix PR Status |
|----------|---------|-------------|---------------|
| **Critical** | #4652 | **Nanobot process crashes** when MCP tool call returns an error or empty data. | ✅ **PR #4666** (open) – Contains malformed tool results |
| **Critical** | #4302 | **Gateway crashes** after MCP reconnection when a session is terminated. | Similar to #4211; no dedicated fix yet |
| **High** | #4307 | **Post-turn consolidation wipes assistant's own delivery message**, losing user follow-up references under modest `context_window_tokens` (e.g., 40k). | ⏳ No fix PR yet |
| **Medium** | #4683 | `temperature` parameter sent to `claude-sonnet-5` causes `400 invalid_request_error`. | ✅ **Merged** (#4685) |
| **Medium** | #4511 | Windows `--background` flag: after `/restart`, the process info JSON becomes inconsistent with actual runtime. | ⏳ No fix PR yet |
| **Low** | #3626 | Telegram long polling silently hangs (bot alive, can send, but stops receiving). | ⏳ No fix PR yet |

### 6. Feature Requests & Roadmap Signals
Several feature requests are gaining traction and align with existing codebase patterns, making them strong candidates for the next minor release.

- **Native Agent-to-Agent Orchestration** (#4179, 1 👍) – Users want a Supervisor → Researcher → Writer multi-agent team pattern within a shared workspace. Given the existing `SubagentManager`, this is a logical extension.
- **`ask_clarification` tool** (#4508) – A tool to end the turn with a focused question when the user request is ambiguous or risky. Expected to reduce hallucination.
- **`search_history` tool** (#4440, 1 👍) – A read-only tool to query `memory/history.jsonl` without loading it into the active context. PR #4439 is already open, likely for the next release.
- **Persistent skill context** (#3846, 1 👍) – Users want skill definitions to be kept in the context window across multiple turns. Related to the overall memory pressure theme.
- **Heartbeat-specific model override** (#4431) – Let the `HeartbeatService` run on a cheaper model instead of the main agent model.
- **Dangerous command authorization** (#3887, 1 👍) – An authorization mechanism to override the hardcoded `deny_patterns` in the `exec` tool (e.g., approve `rm -rf` for a specific vendor command).

**Prediction for v0.3.0**: The `search_history` tool (#4439), `ask_clarification` tool, and the MCP crash fix (#4666) are likely to land next.

### 7. User Feedback Summary
Real user pain points center on **stability, memory reliability, and configuration ergonomics**.

- **Dissatisfied**: Users running production MCP servers report **process crashes** on tool errors (#4652) and **gateway crashes** on MCP reconnection (#4302). Both are "dealbreakers" for unattended operation.
- **Dissatisfied**: The **short-term memory loss** (#4044) undermines trust—users report that the agent cannot maintain a coherent conversation thread.
- **Dissatisfied**: Windows users face **broken background command behavior** (#4511) and **gateway stop crashes** (PR #4690 addresses this).
- **Satisfied**: The **Anthropic OAuth** support (#4632) was well-received by Claude subscription users who previously needed an API key.
- **Frustrated**: Users managing multiple IM users on a single agent want **session-level memory isolation** (#3744), fearing that personal notes from one user might leak to another.

### 8. Backlog Watch
The following items have been open for **over a month** without direct maintainer engagement, representing risk to community trust.

- **#3744** `session级别MEMORY功能请求` (Created: 2026-05-11) – Multi-user memory isolation. Requires architectural decision on per-user `MEMORY.md` vs. workspace-level memory. **Needs maintainer response.**
- **#3626** `Telegram long polling silently hangs` (Created: 2026-05-05) – A persistent networking bug affecting a major channel. **No PR or assignee.**
- **#3973** `Dream System: Hunger Problem & Lack of Real-time Learning` (Created: 2026-05-23) – The self-improvement Dream system only has `history.jsonl` as input, limiting its effectiveness. Users request **real-time learning hooks**. **No maintainer reply.**
- **#4107** `Allow configuring additional bind mounts for bwrap sandbox` (Created: 2026-05-30) – Security sandbox configuration request for users with custom directory structures. **Stale—no assignee.**

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

# Hermes Agent Project Digest — 2026-07-04

## Today's Overview

Hermes Agent shows **very high activity** today with 50 issues and 50 PRs updated in the last 24 hours, indicating a highly engaged contributor community and a project under active development. The issue tracker is dominated by **open security and stability reports** (47 open issues), while the PR queue contains **43 open pull requests** with several critical fixes targeting auth, state management, and platform compatibility. No new releases were published today, but the volume of merged/closed work (7 PRs) suggests progress toward an upcoming release. The project continues to mature rapidly, though the concentration of P1/P2 bugs—particularly around authentication and multiplexed gateway operations—signals ongoing growing pains from recent feature expansion.

## Releases

**None** — No new releases were published today.

## Project Progress

Seven PRs were merged or closed today, spanning several components:

- **#57999** `feat(telegram): add external callback handlers` — Merged feature adding prefix-based callback data dispatch from Telegram to local scripts, with configurable response templates. This extends Telegram gateway extensibility for community operators.
- **#56074** `fix: reset in-memory _openrouter_catalog_cache on /model --refresh` — Merged fix ensuring `hermes model --refresh` clears both disk and in-memory caches, resolving stale model catalog issues.
- **#51592** `fix(docker): avoid overlayfs copy-up storm in chmod/chown` — Merged Docker optimization replacing three recursive permission walks with a single pass, reducing image build time on overlay filesystems.
- **#58012** `feat(achievements): add export endpoint and agent summary (#18472)` — Closed (duplicated by #58015), but the workstream continues with an improved implementation.

The achievements export feature (#58015, #58012) appears to be a notable advancement: it breaks achievements out of `state.json` into a proper REST endpoint and agent-communication surface, enabling external tools to read agent accomplishments.

## Community Hot Topics

1. **Issue #40173** `feat(telegram): channel_profiles — route Telegram chats to Hermes profiles in one gateway` — 3 reactions, 3 comments. This feature request to route different Telegram chats to different agent profiles via a single gateway process has strong community interest. The underlying need is clear: operators running multiple agent personalities currently must spin up separate gateway processes for each profile, which is resource-intensive and operationally complex.

2. **Issue #12188** `[Feature]: Setting hermes model config/settings inside Docker compose as env variables` — 2 reactions, 5 comments. Users are frustrated by the lack of Docker environment variable support for model configuration. The current workflow requires `docker exec` to run `hermes model` commands inside containers, which breaks automated deployments.

3. **Issue #524** `Feature: Agent Migration System — Auto-Detect & Import Settings from Claude Code, Codex, Gemini CLI, Cursor, Aider, Roo Code & Others on First Install` — 1 reaction, 4 comments. This long-running feature request (since March) reflects a critical onboarding pain point: users switching from other AI coding agents must manually re-enter API keys, MCP server configs, and custom instructions.

4. **Issue #48441** `[Security] Terminal session snapshots leak .env secrets to disk in plaintext` — 1 reaction, 5 comments (CLOSED). This high-severity security issue was resolved but generated significant discussion about secret management in terminal snapshot mechanisms.

5. **Issue #56747** `[Windows] Blank terminal console windows flash when running agent or tools on desktop GUI` — 1 reaction, 1 comment. A Windows-specific UX annoyance with popup console windows is getting attention as desktop usage grows.

## Bugs & Stability

### Critical / P1 Bugs (reported today or updated)

1. **#58010** `AsyncSessionDB breaks /resume — missing await in slash_commands.py` — **P1**. Agent `resume` command crashes with `TypeError: 'coroutine' object is not subscriptable` because `slash_commands.py` was never updated to await `AsyncSessionDB` methods. Severity: **high** — breaks session resumption entirely. Merged PR #57933 contains pending fix.

2. **#57928** `BUG - file attachment broken` — **P2**. Files attached to Telegram messages with `/steer`, `/goal`, or `/subgoal` slash commands are silently dropped. Severity: **high** for Telegram users relying on document attachments in structured commands.

3. **#58009** `Tool output replaced with <<ccr:...>> content reference tags when exceeding ~1KB threshold` — **P2**. Tool outputs >1KB are silently replaced with content reference tags, breaking any tool call that produces substantial output. Severity: **very high** — effectively breaks terminal, read_file, kubectl, and similar tools for all realistic use cases.

4. **#57903** `async LLM calls block the desktop WebSocket loop via busy-poll` — **P2**. Desktop app WebSocket connection stalls during LLM calls due to busy-polling patterns. A draft PR #57933 exists.

5. **#54675** `Multiplexed gateway: platform bot tokens resolved via os.getenv bypass the per-profile secret scope` — **P2**. In multiplexed gateway mode, secondary profiles use the default profile's bot token instead of their own, breaking multi-profile deployments. No fix PR yet.

6. **#57905** `computer_use ignores cua-driver 0.7.0 data.windows output, causing empty window discovery` — **P2** on Windows. Computer Use agent cannot discover windows after driver update. No fix PR yet.

### P3 Bugs (reported today)

- **#57986** `[Bug]: /journey crashes when a skill’s frontmatter metadata is not a dict` — Crashes learning graph builder on malformed skill metadata.
- **#57931** `hermes doctor: Mem0 OSS mode falsely reports "API key not set"` — False positive in diagnostics for self-hosted Mem0 users.
- **#57949** `Langfuse SDK plugin: placeholder API key silent failure` — No error surfaced when using dummy API keys.
- **#57955** `terminal tool lacks protected-file path validation (bypasses SOUL.md write-protection)` — Security boundary bypass via shell commands.
- **#57968** `bug(desktop): flat "Sessions" list missing from sidebar after update` — Visual regression in desktop app sidebar.

### Notable Stability PRs in Flight

- **#58003** `fix(state): increase SQLite busy timeout from 1s to 30s (#57921)` — Addressing gateway `database is locked` errors when dashboard stalls under GIL pressure.
- **#58008** `fix(mcp): delete git-cloned MCP dirs on Windows despite read-only .git files` — Fixing PermissionError on Windows MCP directory cleanup.
- **#58004** `fix(update): self-heal venv after failed lazy backend refresh` — Improving update reliability with auto-reinstall of corrupted packages.
- **#57563** `Fix(gateway/cron): resolve BWS multiplexing credential isolation, OAuth path hijack, and cron scheduler thread safety` — **P1 security fix** in open review addressing multiple credential isolation vulnerabilities.

## Feature Requests & Roadmap Signals

### Strong Signal Features

1. **Channel-based profile routing** (#40173) — Route different Telegram chats/groups to different agent profiles via a config map. This is likely for the next minor release given community traction (3 👍) and clear implementation scope.

2. **Configurable Discord voice timeout** (#17790) — Making the hardcoded 5-minute voice inactivity timeout configurable. Simple config change with high utility for persistent voice workflows.

3. **Telegram cron delivery per-topic** (#50668) — Fresh DM topic per cron execution to avoid output landing in stale conversation contexts. Addresses a common multi-topic workflow pain point.

4. **Multi-bank routing for Hindsight memory** (#31776) — Exposing multiple memory bank support beyond the current single `bank_id` per session. This aligns with enterprise/professional use cases needing separate memory contexts per workspace or project.

### Prediction for Next Release

The next minor release (v0.19.0, targeting ~2026.8.1 based on cadence) will likely include:
- The **merged achievements export feature** (#58015)
- **Telegram callback handlers** (#57999)
- **Multi-profile channel routing** (#40173) — strong community demand, clean implementation
- **Core auth/security fixes** from #57563, #58006, #58014
- SQLite timeout improvements (#58003)

## User Feedback Summary

### Pain Points

1. **Authentication friction**: Multiple users report broken OAuth flows with Anthropic (Cloudflare 403s, User-Agent blocks, 404 on token exchange), suggesting Anthropic has changed their auth backend without backward compatibility.

2. **Docker deployment confusion**: Users struggle with model configuration in Docker Compose (#12188) — the documentation gap forces `docker exec` workflows that are fragile and non-deterministic.

3. **Silent failures across features**: Several bugs today (#58009 content references, #57928 file attachment drops, #57949 Langfuse silent failure, #57967 kanban silent commit failures) share a pattern: **operations report success but actually fail silently**. This erodes user trust in the tool's output.

4. **Windows UX degradation**: Blank console window flashes (#56747), missing desktop sidebar (#57968), CUA window discovery failure (#57905) — Windows users face an accumulating set of desktop app issues.

5. **Cron vs interactive inconsistency**: Composio MCP tools work in Telegram/TUI but not in cron-triggered sessions (#57861). This pattern of feature gaps between cron and interactive modes is a recurring theme (also seen in session search FTS capability issues).

### Satisfaction Signals

- The **achievements export** feature (#58015) was developed and merged rapidly after community specification (#18472), demonstrating responsive feature development.
- Multiple **security-focused PRs** (#58006, #58007, #58014, #57563) show the team is actively addressing credential handling and isolation concerns.
- The **OpenAI Agents SDK bridge** (#57984) represents sophisticated governance and quality infrastructure, appealing to enterprise users.

## Backlog Watch

### High-Severity Unresolved Issues Needing Maintainer Attention

1. **#58010** `AsyncSessionDB breaks /resume — missing await` — **P1, opened today**. Core session resume is completely broken. PR #57933 has a draft fix but is not yet merged. **Urgent.**

2. **#58009** `Tool output replaced with <<ccr:...>> tags` — **P2, opened today**. Breaks all tools producing >1KB output. No fix PR yet. **Very high impact on usability.**

3. **#54675** `Multiplexed gateway: platform bot tokens bypass per-profile secret scope` — **P2, opened 5 days ago**. Security vulnerability in multi-profile deployments. No fix PR identified.

4. **#48534** `Anthropic Max OAuth fails: token exchange 404s` — **P1, opened 16 days ago**. Complete auth flow failure for Anthropic Max tier. PR #58014 addresses retry logic but the 404 root cause (User-Agent blocking) may require Anthropic coordination.

5. **#6347** `Anthropic OAuth refresh path gets Cloudflare 403` — **P2, opened 86 days ago**. Long-standing Anthropic OAuth refresh failure. Unresolved for nearly 3 months. Credentials become permanently stale.

### Stale Feature Requests

6. **#524** `Agent Migration System` — **P3, opened 120 days ago**. High-value onboarding feature with 4 comments and 1 👍. No signs of implementation. This represents a significant new-user acquisition bottleneck.

7. **#31776** `Multi-bank routing for Hindsight memory` — **P3, opened 40 days ago**. Feature request with moderate community interest. No PRs or roadmap signals.

### Long-Standing PRs

8. **#3651** `feat(secrets): add phase 1 secrets tool and redaction hardening` — **P2, opened 97 days ago**. This PR has been open for over 3 months and touches critical security infrastructure. It implements a first-class secrets tool with redaction hardening. The prolonged review cycle may indicate security concerns or scope creep.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

Here is the project digest for PicoClaw.

---

**Project Digest: PicoClaw**
**Date:** 2026-07-04
**Data Period:** 2026-07-03 00:00:00 UTC - 2026-07-04 00:00:00 UTC

### 1. Today's Overview
PicoClaw shows a **high burst of development activity** today, with 17 Pull Requests (PRs) updated and a new patch release (v0.3.1). The focus is heavily on stability, specifically implementing robust reconnection logic for WebSocket-based channels (WhatsApp, Matrix) and fixing a configuration migration bug that blocks upgrades. While the sheer number of PRs indicates a productive day, several of these contributions are minor fixes or reverts, suggesting a period of debugging following the recent v0.3.x release. The open issue count remains low (2), indicating the community is seeing relatively few new critical failures.

### 2. Releases
**New Release: v0.3.1**
The project published [v0.3.1](https://github.com/sipeed/picoclaw/releases) today. While the provided changelog contains internal merge commits, the context from the PRs updated today suggests this release likely contains several critical bug fixes:
- **WhatsApp Stability:** Improves WebSocket reconnection logic to prevent silent disconnects after 2-3 days.
- **Agent Routing Fix:** Resolves an issue where the `/clear` command would clear the wrong agent session (default instead of the active one).
- **Config Migration:** Fixes a `v2` to `v3` config migration bug that caused a "unknown field(s): build_info" error, blocking the upgrade path for users on certain builds (v0.2.5+).
- **Upgrade Note:** Users running v0.2.x who have customized their configuration files may encounter a one-time migration prompt. This release should resolve that error.

### 3. Project Progress
Today saw **5 PRs merged or closed** (mostly closed in favor of others), with 2 significant fixes merged:
- **Fixed Agent Session Clearing ([#3224](https://github.com/sipeed/picoclaw/pull/3224)):** Ethan1918 contributed a fix preventing the `/clear` command from targeting the wrong agent when messages are routed to a non-default agent. This resolves a major UX friction for users running multi-agent setups.
- **Fixed Duplicate Messages from Spawn Agents ([#3142](https://github.com/sipeed/picoclaw/pull/3142)):** A fix from jincheng-xydt was merged to prevent duplicate message delivery when a sub-agent (spawn) completes a task. This was a source of spam and confusion in conversations.

### 4. Community Hot Topics
There is low direct community discussion (few comments on issues), but the **PRs tell the story of the most pressing concerns**:
- **[WhatsApp Reliability (PR #3179 & #3220)](https://github.com/sipeed/picoclaw/pull/3220):** Two separate authors (Alix-007 and AMEOBIUS) created PRs on the exact same day to fix WhatsApp WebSocket disconnection. This indicates a widespread, predictable failure pattern that is a top pain point for users.
- **[Delta Chat Integration (PR #3222)](https://github.com/sipeed/picoclaw/pull/3222):** The refactor by trufae details a desire to clean up the newly added Delta Chat gateway. The removal of 320 lines of code (including hardcoded servers and outdated tests) suggests users were running into configuration and maintenance issues with the initial implementation.

### 5. Bugs & Stability
One **high-severity bug** was actively being fixed today:
- **WhatsApp Silent Disconnect (High Severity):** The core issue is that the WhatsApp WebSocket listener would break on any read error and never reconnect. A simple "retry loop" was insufficient as it tried to use the dead connection. Fix PRs exist from two developers ([#3179](https://github.com/sipeed/picoclaw/pull/3179), [#3220](https://github.com/sipeed/picoclaw/pull/3220)).
- **V2 Config Migration Block (Critical Severity):** A blocking bug (`build_info` unknown field) prevented users from upgrading their configuration to v3. This was fixed via a config schema update in PR [#3218](https://github.com/sipeed/picoclaw/pull/3218).

### 6. Feature Requests & Roadmap Signals
Two notable feature PRs indicate the direction of the project:
- **Configurable Model Fallback Chain ([#3200](https://github.com/sipeed/picoclaw/pull/3200)):** lc6464 has added a feature to the Web UI allowing users to set a default model fallback chain. This is a highly requested feature for reliability, allowing PicoClaw to switch to a backup model (e.g., from Deepseek to GPT) if the primary is unavailable or rate-limited. Expect this in v0.4.0.
- **Agent Collaboration Bus ([#2937](https://github.com/sipeed/picoclaw/pull/2937)):** This large, long-standing PR is still open. It proposes a first-class internal messaging bus for agents (mailboxes, threads). While not merged, it is the strongest signal of a future major feature for complex, multi-agent workflows.

### 7. User Feedback Summary
User feedback from the last 24 hours (via Issues #3178 and #3182) reveals specific pain points:
- **"It just stops working" (Reliability):** The WhatsApp issue (#3178) shows frustration with the service "randomly" failing after a few days. The core demand is for a persistent, self-healing connection.
- **"Can't change path from settings" (Android Usability):** The Android bug report (#3182) highlights a critical failure on mobile. Users cannot configure the app, indicating a UI regression or a permission-handling error that blocks all functionality.
- **"My upgrade broke" (Configuration Migration):** The fix in PR #3218 implies users on v0.2.5+ were hitting a hard error when trying to upgrade. This causes immediate distrust in the update process and is a source of significant user frustration.

### 8. Backlog Watch
The following low-activity items require maintainer attention to prevent them from stalling the community:
- **[Feat/agent collaboration (PR #2937)](https://github.com/sipeed/picoclaw/pull/2937):** This is the most significant feature in the backlog. It has been open since May 24 and has no maintainer comments. Inactivity here discourages contributors from working on large, risky features.
- **[fix(whatsapp): reconnect after websocket drops (PR #3179)](https://github.com/sipeed/picoclaw/pull/3179):** From Alix-007. While a newer PR (#3220) solves the same issue, this one is older and adds more conservative diagnostic handlers (ping/pong). A decision is needed on which implementation is preferred to avoid duplicate effort.
- **[Added simplex channel type (PR #3193)](https://github.com/sipeed/picoclaw/pull/3193):** This is a new feature request for a new channel protocol (Simplex). It has received no maintainer feedback. A "yes/no" or "needs work" tag would help the contributor understand their next steps.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

# NanoClaw Project Digest — 2026-07-04

## Today's Overview
NanoClaw shows moderate activity today with 1 new issue and a surge of 17 pull requests updated over the past 24 hours, 2 of which were merged/closed. No new releases were published. The project continues to mature across multiple fronts: channel reliability (Signal and WhatsApp), container compatibility (Podman, mount security), and MCP transport expansion are all seeing active fix and feature work. However, 15 PRs remain open, some dating back weeks, suggesting a growing review backlog. The spike in PR updates may indicate maintainer cycles have returned, but throughput on closure remains lower than ideal for project health.

## Releases
*No new releases were published today. There are no version change notes to report.*

## Project Progress
Two PRs were merged/closed today, indicating forward movement on stability and tooling:

- **PR #2765** — `feat(providers): add .format-lint-off` (closed, by amit-shafnir): Adds a formatting lint-off capability for providers, likely targeting code quality workflows.
- **PR #2330** — `fix(container): make axios MCP servers work through OneCLI's proxy` (closed, by Tij8i): Resolves a compatibility issue where axios-based MCP servers failed when routed through OneCLI’s CONNECT-only proxy, previously returning HTTP 400 errors silently.

## Community Hot Topics
- **Issue #2917** — [OPEN] Token overhead concern when using local models as primary agents. Author cappuccinowholemilk-stack highlights a real performance problem: ~27k tokens of MCP tool schema overhead are sent every request, even when the orchestrating model is a local Gemma4:31B. This is the *only* active issue today but touches a core cost/performance pain point for users experimenting with local model backends. *No comments yet, so community discussion has not engaged.*
  [Link](https://github.com/nanocoai/nanoclaw/issues/2917)
- **PR #2184** — [OPEN] `fix(poll-loop): retry immediately on stale session instead of delivering error` — 2 months old, still active. The author (cfis) continues to update this foundational fix for Claude Code session expiration handling. Prolonged review cycle may be frustrating for users experiencing session-dropping bugs.
  [Link](https://github.com/nanocoai/nanoclaw/pull/2184)
- **PR #2208** — [OPEN] `feat(mcp): support http and sse MCP server transports` — open since early May, still being updated. This is a significant architectural addition for MCP connectivity, but its long tenure suggests it may be large or contentious.
  [Link](https://github.com/nanocoai/nanoclaw/pull/2208)

## Bugs & Stability
*High severity:*
- **Issue #2917** — Token overhead for local-model orchestration. Not yet a confirmed bug, but flagged as a significant performance regression. Local model users will face degraded latency and higher cost due to unnecessary MCP schema bloat. No fix PR exists yet.

*Moderate severity (fix PRs exist/open):*
- **PR #2184** — Stale session handling in poll-loop delivers raw errors to users before retrying. Fix exists but remains unmerged for ~2 months.
- **PR #2920** — Newly filed: DB connection leak in `container-restart.ts` (`openInboundDb()` never closed), stale docs referencing removed `NANOCLAW_ADMIN_USER_IDS`, and a duplicate script file. Fix provided in the same PR, awaiting review.
- **PR #2694/2695** — Signal adapter drops DMs silently (`isMention`/`isGroup` not set) and cannot read inbound image attachments from container. Both fixes authored by cfis, still open.
- **PR #2348** — WhatsApp channel has single-timer reconnect and teardown issues. Fix exists.
- **PR #2230** — Container runner fails to map host user on rootless Podman. Fix exists.

*Low severity:*
- **PR #2349** — Mount security allowlist can crash if entries lack a `path` field. Fix exists.

## Feature Requests & Roadmap Signals
Several skill/utility PRs indicate steady ecosystem expansion:

| PR # | Feature | Status |
|------|---------|--------|
| #2530 | `/add-caldav-tool` — CalDAV calendar integration | Open, updated today |
| #2693 | `/add-google-contacts-tool` — Google Contacts via MCP | Open, updated today |
| #2863 | `/setup-system-digest` and `/system-digest` skills — system monitoring via OneCLI | Open, updated today |
| #2918 | **LINE Official Account channel** — native adapter + `/add-line` skill — major new channel integration from external contributor joshm1230212 | Opened today |

These suggest the project is actively targeting productivity tooling (CalDAV, Google Contacts) and new messaging channels (LINE). The LINE channel PR (#2918) is the most significant roadmap signal from this week, potentially expanding NanoClaw’s reach into Asian markets.

## User Feedback Summary
- **Local model token cost pain** (Issue #2917): Users running local models like Gemma4:31B as primary orchestrators are paying full MCP tool-schema token overhead (~27k tokens) every request. This undermines the cost and latency benefits of local inference. The user's framing as “before any real conversation” suggests frustration with architectural inefficiency.
- **Container compatibility friction**: Multiple fix PRs (#2230, #2349, #2695) indicate that containerized deployments (especially rootless Podman and Signal in containers) remain a persistent pain point for users.
- **Session stability frustration**: PR #2184 has been open since May 2 — two full months with no merge — while users continue to receive raw error messages from expired Claude Code sessions. This is likely eroding trust in the poll-loop reliability.

## Backlog Watch
- **PR #2184** — `fix(poll-loop): retry immediately on stale session` — 2 months open, last updated today. Core reliability fix. Needs maintainer decision.
  [Link](https://github.com/nanocoai/nanoclaw/pull/2184)
- **PR #2208** — `feat(mcp): support http and sse MCP server transports` — 2 months open. Architectural feature, possibly blocked by scope or disagreements.
  [Link](https://github.com/nanocoai/nanoclaw/pull/2208)
- **PR #2348** — Single-timer reconnect for WhatsApp — 2 months open.
  [Link](https://github.com/nanocoai/nanoclaw/pull/2348)
- **Issue #2917** — Local model token overhead — filed yesterday, no engagement yet from maintainers. If confirmed, this affects a growing segment of the user base.
  [Link](https://github.com/nanocoai/nanoclaw/issues/2917)

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

# NullClaw Project Digest — 2026-07-04

## Today's Overview
Project activity is minimal today, with only one open issue updated in the past 24 hours and no new pull requests, merges, or releases. The single tracked issue (#972) is a reported bug in the Telegram adapter that has been open for several days, suggesting the maintainer may be investigating a reliability problem rather than pushing new features. Overall, the project appears to be in a low-velocity, maintenance-focused phase, with no signs of active development or community contribution this period.

## Releases
**No new releases.** The latest release remains prior to this date; no version bumps, changelogs, or migration notes are available for 2026-07-04.

## Project Progress
**No pull requests were merged or closed today.** No feature branches advanced, and no fixes were committed. The project's development pipeline is idle.

## Community Hot Topics
**Single active Issue:** [#972 — [bug] telegram channel stop respond after some idle time](https://github.com/nullclaw/nullclaw/issues/972)  
- Author: i11010520 | Comments: 1 | Reactions: 0  
- **Analysis:** This is the only community-visible discussion. The reporter describes that the Telegram integration stops responding after overnight idle periods, even though the backend (nullclaw agent) still answers `ping` commands. The one existing comment likely comes from the maintainer or a helper. The underlying need is a **reliability fix** for long-lived Telegram sessions — users expect persistent, always-on connectivity without manual re-triggering. This is a classic "stale connection" or "token expiration" bug, and it may require a keep-alive mechanism or reconnection logic. Given the single speaker, community engagement is very low.

## Bugs & Stability
| Issue | Severity | Description | Fix PR Exists? |
|-------|----------|-------------|----------------|
| [#972](https://github.com/nullclaw/nullclaw/issues/972) | **Medium-High** | Telegram channel stops responding after idle hours; backend remains healthy. User must manually intervene. Affects real-world usage for anyone running Telegram bots continuously. | No PR open |

**Ranking rationale:** Medium-High because it’s functional (not crashing the process) but breaks a core channel integration for users relying on overnight/always-on bots. No crash, but a UX regression.

## Feature Requests & Roadmap Signals
No explicit feature requests were filed today. However, the **Telegram idle bug (#972)** implies a strong unspoken request for **connection resilience / automatic reconnection** features. If the fix involves adding a keep-alive or periodic re-auth mechanism, that same infrastructure could be extended to other channel adapters (e.g., Slack, Discord). This is likely to land in the next minor release as a quick patch rather than a roadmap feature.

## User Feedback Summary
**Main pain point:** The Telegram adapter fails silently after idle periods, forcing users to restart or re-check the bot. The reporter’s tone suggests mild frustration — they note the backend itself works fine, so the issue is specific to channel integration. There is no explicit satisfaction expressed today; the community sentiment appears neutral to slightly dissatisfied, driven by a missing reliability guarantee.

## Backlog Watch
- **Longest-unanswered issue:** [#972](https://github.com/nullclaw/nullclaw/issues/972) has been open for **4 days** (created 2026-06-30, updated 2026-07-03) with only one comment. This is the only tracked issue. It is receiving some attention (updated yesterday) but has not been resolved or assigned. It warrants priority attention because it is a **user-facing regression** in a popular channel (Telegram) and is the sole item in the project’s active queue. No older issues were updated in the monitored window.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

# IronClaw Project Digest — 2026-07-04

## Today's Overview

IronClaw remains in an intense development phase, with the **Reborn architecture migration** continuing to dominate activity. Over the past 24 hours, **33 issues** and **50 pull requests** were updated, with PR velocity showing strong momentum (28 merged/closed vs 22 open). The project closed **28 PRs**, including significant refactors to identity management, type deduplication, and Slack integration infrastructure. However, **CI remains red on `main`** due to engine-v2 removal fallout (#5603, #5590), and a wave of QA-discovered bugs in Reborn identity, credential injection, and memory systems surfaced. No new releases were published. A major **Slack OAuth migration** PR (#5604, XL size) was opened, signaling a user-facing UX improvement in flight.

---

## Releases

**None** — no new releases were published today. The last release appears to be the `0.29.1` version under development in the `chore: release` PR (#5598), which includes breaking API changes in `ironclaw_common` (0.4.2→0.5.0) and `ironclaw_skills` (0.3.0→0.4.0), but this PR remains open and unmerged.

---

## Project Progress

### Merged/Closed PRs Today (28 total — top highlights)

| PR | Description | Impact |
|---|---|---|
| [#5619](https://github.com/nearai/ironclaw/pull/5619) | `refactor(reborn_identity): de-slop` — dead types, boundary rules, CONTRACT, error-path tests | Major cleanup of identity layer, closes multiple risk bugs |
| [#5625](https://github.com/nearai/ironclaw/pull/5625) | `feat(reborn): manifest-projected host-ingress route + fail-closed credential coherence` | Declarative ingress contract for Slack manifest |
| [#5567](https://github.com/nearai/ironclaw/pull/5567) | `refactor(types,traits): execute judged dedup backlog` — 6 traits removed, 6 DTO clusters unified, net -176 lines | Reduces type complexity |
| [#5624](https://github.com/nearai/ironclaw/pull/5624) | Reborn #3231 follow-ups: test harness extraction + landing-policy doc | Completes two long-standing architecture items |
| [#5585](https://github.com/nearai/ironclaw/pull/5585) | `refactor Reborn composition internals` — modules for observability, telemetry, artifact resolver | Improves code organization |
| [#5622](https://github.com/nearai/ironclaw/pull/5622) | `feat(skills): add parallel-pr-review skill` | New developer productivity tool |
| [#5080](https://github.com/nearai/ironclaw/pull/5080) | Docs/file upload (new contributor: `dat-Devvv`) | Documentation addition |

### Merged Bug Fixes
- [#5130](https://github.com/nearai/ironclaw/pull/5130) — Fixed sidebar thread highlight off chat routes (WebUI v2)
- Multiple identity-layer fixes via #5619

### Infrastructure Advancement
- [#5101](https://github.com/nearai/ironclaw/pull/5101) — CI: reuse cargo-component installer in live canary (open, but active)

### Notable Merged Ingress Stack (superseding older PRs)
Multiple PRs in the ingress stack were closed as superseded in favor of the cleaner #5625 approach:
- [#5107](https://github.com/nearai/ironclaw/pull/5107), [#5093](https://github.com/nearai/ironclaw/pull/5093), [#5072](https://github.com/nearai/ironclaw/pull/5072), [#5100](https://github.com/nearai/ironclaw/pull/5100) — All closed as superseded by #5625

---

## Community Hot Topics

### Most Active Issues (by comment count)

1. **[#3067](https://github.com/nearai/ironclaw/issues/3067) — [TEST] Reborn: Add vertical-slice integration test suite** (33 comments)
   - *Status:* Open, updated 2026-07-03
   - *Analysis:* The top-voted issue by far, tracking the "Reborn" integration test strategy. The high comment count shows deep technical debate on integration test architecture. Critical for ensuring Reborn cutover quality.

2. **[#3087](https://github.com/nearai/ironclaw/issues/3087) — [Reborn] Compose ironclaw_host_runtime services** (7 comments)
   - *Status:* Closed
   - *Analysis:* Core service composition for the host runtime — now resolved.

3. **Multiple issues with 3 comments each:** [#3231](https://github.com/nearai/ironclaw/issues/3231), [#3278](https://github.com/nearai/ironclaw/issues/3278), [#3236](https://github.com/nearai/ironclaw/issues/3236), [#5522](https://github.com/nearai/ironclaw/issues/5522)
   - Reborn architecture deep-dives (thread policy, cancellation, service integration)
   - QA bug: Reborn routine fails when Slack DMs require missing capability (#5522)

### Most Active PRs

Open PRs with highest activity (undefined comment counts, but size/risk tags indicate scope):

- [#5604](https://github.com/nearai/ironclaw/pull/5604) — [size: XL] **Remove Slack pairing flow in favor of OAuth setup** — Major UX improvement, broad scope
- [#5049](https://github.com/nearai/ironclaw/pull/5049) — Wire identity + profile context sources in production composition — Core Reborn feature
- [#5626](https://github.com/nearai/ironclaw/pull/5626) — Project Slack ingress routes from manifest, delete Rust policy literals — Continuation of ingress stack
- [#5132](https://github.com/nearai/ironclaw/pull/5132) — Redirect invalid chat thread routes (new contributor `rafly-habibi`)
- [#5101](https://github.com/nearai/ironclaw/pull/5101) — CI: reuse cargo-component installer (new contributor `theredspoon`)

---

## Bugs & Stability

### High-Severity Bugs

| Issue | Severity | Description | Fix Status |
|---|---|---|---|
| [#5512](https://github.com/nearai/ironclaw/issues/5512) | **High** | WASM credential provider re-derives injection eligibility from manifest instead of authorizer's Decision.obligations | Open; [#5623](https://github.com/nearai/ironclaw/pull/5623) fixes this |
| [#5615](https://github.com/nearai/ironclaw/issues/5615) | **High** | `bind()` has no OAuth-surface guard — defense-in-depth gap | Open; findings from de-slop audit |
| [#5614](https://github.com/nearai/ironclaw/issues/5614) | **High** | Cross-process divergent-email logins can split a principal | Open; race condition in filesystem store |
| [#5616](https://github.com/nearai/ironclaw/issues/5616) | **Medium** | `adopt_migrated_identity` never writes StoredUser — phantom user | Open |
| [#5617](https://github.com/nearai/ironclaw/issues/5617) | **Medium** | Login seam (OAuth → WebuiUserDirectory → resolver) tested only with fakes | Open |
| [#5605](https://github.com/nearai/ironclaw/issues/5605) | **Medium** | Memory prompt-context injection unwired — `memory_snippets` always empty in production | Open |
| [#5583](https://github.com/nearai/ironclaw/issues/5583) | **Medium** | Hallucinated call to disabled capability fails run as `model_error` instead of denial | Open |
| [#5608](https://github.com/nearai/ironclaw/issues/5608) | **Medium** | Retry path unreachable for local-dev synthetic capabilities — collapses into terminal failure | Open |
| [#5603](https://github.com/nearai/ironclaw/issues/5603) | **High** | CI red on main: Docker build missing prompts COPY + Clippy Windows unused import | Open |
| [#5590](https://github.com/nearai/ironclaw/issues/5590) | **High** | Make main branch CI checks green again | Open |
| [#5507](https://github.com/nearai/ironclaw/issues/5507) | **Medium** | Failed routine run shows "No thread attached" — blocks debugging | Open |
| [#5510](https://github.com/nearai/ironclaw/issues/5510) | **Medium** | Cannot delete old routines — stale routines accumulate | Open |
| [#5522](https://github.com/nearai/ironclaw/issues/5522) | **Medium** | Reborn routine fails when Slack DMs require missing capability + retry loop | Open |
| [#5602](https://github.com/nearai/ironclaw/issues/5602) | **Low** | Can't connect Slack from chat (despite agent claiming success) | Open |

### Fix PRs in Flight
- [#5623](https://github.com/nearai/ironclaw/pull/5623) — **Honor staged credential obligations for WASM egress** (direct fix for #5512)
- [#5619](https://github.com/nearai/ironclaw/pull/5619) — Identity de-slop (fixes #5615, #5616, #5614, #5617)

### Integration Test / Quality Assurance
- [#5527](https://github.com/nearai/ironclaw/issues/5527) — FilesystemSessionThreadService idempotency write/read scope mismatch — closed as design flaw
- [#5500](https://github.com/nearai/ironclaw/issues/5500) — Stabilize Reborn Playwright channel-connect tests — closed
- [#5595](https://github.com/nearai/ironclaw/issues/5595) — Daily failure taxonomy (2026-07-03) — pinchbench suite analysis

---

## Feature Requests & Roadmap Signals

### User-Requested / QA-Reported Features

1. **Slack OAuth Migration** — [#5604](https://github.com/nearai/ironclaw/pull/5604) (XL PR, opened today): The most significant user-facing change in flight. Removes the old pairing-code flow in favor of per-user OAuth-backed tool identity. Addresses #5602 (Slack connection UX failure).

2. **Routine Management** — [#5510](https://github.com/nearai/ironclaw/issues/5510): Users cannot delete old routines, forcing "complete restart" to clear them. Compounded by stale routines running on old configurations.

3. **WASM Credential Obligations** — [#5623](https://github.com/nearai/ironclaw/pull/5623) (fixes #5512): Making credential injection honor the authorization Decision rather than manifest — critical for security and correctness.

### Roadmap Predictions (Next Release Candidates)
- **Slack OAuth UX** (#5604) — likely to land next, given its size and scope
- **Manifest-driven ingress** (#5625, #5626) — already merged or in final review
- **Identity de-slop fixes** (#5619) — already merged, so fixes will ship
- **Type dedup cleanup** (#5567) — already merged, reduces complexity
- **CI stabilization** (#5603, #5590) — blocking release

---

## User Feedback Summary

### Real User Pain Points (from QA + bug reports)

| Pain Point | Source | Frequency |
|---|---|---|
| Cannot delete old routines — stale routines accumulate | [#5510](https://github.com/nearai/ironclaw/issues/5510) | 1 report + compounding effect |
| Slack connection flow broken (pairing code vs OAuth confusion) | [#5602](https://github.com/nearai/ironclaw/issues/5602) | 1 report |
| Failed routines show "No thread attached" — no debugging path | [#5507](https://github.com/nearai/ironclaw/issues/5507) | 1 report |
| Routine runs fail when Slack DM reading needs missing capability | [#5522](https://github.com/nearai/ironclaw/issues/5522) | 1 report |

### User Satisfaction Signals
- **Positive:** Active community contributions from new contributors (`dat-Devvv`, `rafly-habibi`, `theredspoon`)
- **Negative:** CI being red on `main` discourages community confidence in trunk stability
- **Neutral/Working:** The Reborn migration is clearly in a "land now, polish later" phase — many production features (memory injection, credential coherence, identity) are being fixed post-landing

### Use Cases Observed
- Slack DM reading agent routines (broken by missing capability authorizer)
- Routine-based github-api-health-check monitoring (fails with opaque errors)
- Multi-agent coordination (TurnCoordinator, MissionService design)
- Slack OAuth-based authentication (incoming UX improvement)

---

## Backlog Watch

### Issues Needing Maintainer Attention

1. **[#3067](https://github.com/nearai/ironclaw/issues/3067) — Reborn vertical-slice integration tests** (33 comments, open since 2026-04-29, last updated 2026-07-03)
   - *Why watch:* The highest-commented issue overall, critical for Reborn quality assurance. Still open; progress appears to be in PRs but no issue closure in sight.

2. **[#3127](https://github.com/nearai/ironclaw/issues/3127) — Scalable capability permission UX** (2 comments, open since 2026-04-30)
   - *Why watch:* Fundamental UX for Reborn's capability system; no PR activity visible.

3. **[#3141](https://github.com/nearai/ironclaw/issues/3141) — Cost-based budgets in ResourceGovernor** (2 comments, open since 2026-05-01)
   - *Why watch:* Port of existing V1 behavior; important for feature parity but no recent movement.

4. **[#5221](https://github.com/nearai/ironclaw/issues/5221) — Ironclaw harness backlog (deepseek-v4-flash)** (0 comments, open since 2026-06-25)
   - *Why watch:* New model integration backlog — 8 hillclimb steps, 12 candidates. Active but no PRs linked. Risk of model support lagging.

5. **[#5618](https://github.com/nearai/ironclaw/issues/5618) — ExternalIdentityKey: decide surface** (0 comments, open 2026-07-03)
   - *Why watch:* Freshly filed — production caller analysis finds dead code, needs architectural decision.

### Abandoned/Stalled PRs (merged/closed too recent to judge stall; all open PRs are active)

No PRs appear stalled — all open PRs have been updated within 24 hours.

---

## Project Health Summary

| Metric | Value | Trend |
|---|---|---|
| Open issue count | 28 active | ↑ (fresh bugs from de-slop audits) |
| PR throughput (24h) | 28 merged/closed, 22 open | ↑ (high velocity) |
| New contributors | 3 (`dat-Devvv`, `rafly-habibi`, `theredspoon`) | ↑ (healthy pipeline) |
| CI status | Red on `main` | ↓ (critical blocker) |
| Release cadence | 0 new releases this period | ↓ (last release pending) |
| Reborn migration progress | Core substrate landed; identity, memory, credentials being hardened | → (steady progress) |
| Security/correctness bugs found | 7+ (from identity de-slop + WASM credential audit) | ↑ (but being fixed rapidly) |

**Bottom line:** The project is moving fast with strong PR throughput and community involvement, but is currently in a "breaking things to fix them" phase. The Reborn architecture migration is past the initial substrate landing and into hardening — with a burst of QA-discovered bugs being actively patched. CI being red on `main` is the most immediate risk; until #5603 and #5590 are resolved, the project lacks a stable trunk for community contributions or release cutting.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

Here is the **LobsterAI Project Digest** for **2026-07-04**, generated from the provided GitHub data.

---

## LobsterAI Project Digest — 2026-07-04

### 1. Today's Overview
LobsterAI is in a **high-velocity release stabilization phase**, processing **16 PRs** in the last 24 hours with a **87.5% close/merge rate** (14 of 16). A new patch release (2026.7.3) was cut, primarily focused on **cowork (collaborative workspace) reliability**, **session rendering performance**, and **OpenClaw integration fixes**. Issue activity was minimal (1 closed issue), suggesting the team is aggressively clearing the backlog ahead of a larger milestone. Overall project health is **strong**, with rapid iteration on user-facing UI/UX and backend stability.

### 2. Releases
**New Release: [LobsterAI 2026.7.3](https://github.com/netease-youdao/LobsterAI/releases/tag/2026.7.3)**
- **Notable Changes:**
    - **feat: service deployment** – Enables deployment of user agents as services.
    - **feat(cowork): add goal mode** – Introduces a new "Goal" mode for collaborative agent workflows.
    - **feat(cowork): add subagent artifact panel** – A new dedicated panel for displaying subagent outputs.
- **Breaking Changes:** None explicitly documented, but the introduction of `cowork: Goal Mode` may require users to adjust their agent configurations.
- **Migration Notes:** No specific migration steps mentioned. Users are advised to review the new "Goal Mode" configuration options.

### 3. Project Progress
The last 24 hours show a **concentrated sprint** on the `cowork` module and session stability. Key advances:
- **Cowork / Goal Mode Foundation:** Multiple PRs ([#2242](https://github.com/netease-youdao/LobsterAI/pull/2242), [#2262](https://github.com/netease-youdao/LobsterAI/pull/2262), [#2268](https://github.com/netease-youdao/LobsterAI/pull/2268)) refined the UI for the new Goal Mode, fixing prompt toolbar compactness and removing unnecessary helper text.
- **Session Model Sync Fix:** PR [#2267](https://github.com/netease-youdao/LobsterAI/pull/2267) solved a critical data divergence issue where model switches made outside the app (via the OpenClaw gateway) were not reflected in the IM/channel sessions.
- **Large Session Performance:** PR [#2264](https://github.com/netease-youdao/LobsterAI/pull/2264) reduced rendering work for tool-heavy sessions by shrinking collapsed tool-result formatting from 64K to 16K and memoizing displays.
- **Stability & Diagnostic Tools:** Added a raw session diagnostics export feature ([#2264](https://github.com/netease-youdao/LobsterAI/pull/2264)) and improved error handling for context maintenance ([#2266](https://github.com/netease-youdao/LobsterAI/pull/2266)).

### 4. Community Hot Topics
Community discussion was minimal today, with most attention focused on internal release processes. The only notable item is a **long-stale open PR**:

- **[PR #1353](https://github.com/netease-youdao/LobsterAI/pull/1353) (OPEN, Stale)** – "feat(agent): Agent 技能选择器新增全选和清除功能"
    - **Status:** Open since April 2026, updated yesterday.
    - **User Need:** Users want "select all" and "clear all" buttons in the Agent skill selector. This indicates a need for better mass-editing capabilities to manage large skill sets. The underlying need is **UX efficiency** when configuring complex agents.

### 5. Bugs & Stability
One significant stability fix was merged today, alongside several minor UI fixes. **Severity ratings (High/Medium/Low) are assigned based on impact on user workflow.**

- **Severity: High** — **Context Maintenance Stuck in UI ([PR #2266](https://github.com/netease-youdao/LobsterAI/pull/2266)):** A bug caused the UI to remain stuck in a "context maintenance" loading state after a chat error (e.g., LLM timeout). **Fix: Merged**.
- **Severity: Medium** — **macOS Fullscreen Black Screen ([PR #2246](https://github.com/netease-youdao/LobsterAI/pull/2246)):** Closing a macOS fullscreen app could result in a black screen. **Fix: Merged** (Exit fullscreen before hiding the main window).
- **Severity: Medium** — **Session File Lock Collision ([PR #2247](https://github.com/netease-youdao/LobsterAI/pull/2247)):** Plan-mode recovery could run before a previous abort cycle finished, causing file lock collisions. **Fix: Merged** (Added a delay until the abort settles).
- **Severity: Low** — **Subagent Panel Timestamps ([PR #2261](https://github.com/netease-youdao/LobsterAI/pull/2261)):** Incorrect timestamps displayed on subagent turn chips in the panel. **Fix: Merged**.

### 6. Feature Requests & Roadmap Signals
The data reveals two major directions for the near-term roadmap:

1.  **Agent Skill Management UX (Low Priority, High Impact):** The stale PR [#1353](https://github.com/netease-youdao/LobsterAI/pull/1353) requesting "select all/clear all" for skills has been open for 3 months. This is a clear signal that the current skill selector is a pain point. **Prediction:** Likely to be merged in the next minor version (2026.7.x or 2026.8.x) as a quality-of-life feature.
2.  **Advanced Cowork Modes:** The introduction of "Goal Mode" (Release 2026.7.3) and the "Subagent Artifact Panel" (PR #2241) signals a roadmap shift toward **structured, multi-agent collaboration**. Future versions will likely expand on this (e.g., dependency graphs between subagencies, goal chaining).

### 7. User Feedback Summary
- **Pain Point (Skill Selection):** The stale PR #1353 demonstrates a user desire for more efficient bulk operations, suggesting frustration with the current point-and-click skill selection interface.
- **Satisfaction (UI Polish):** Several closed PRs ([#2269](https://github.com/netease-youdao/LobsterAI/pull/2269), [#2263](https://github.com/netease-youdao/LobsterAI/pull/2263)) focused on tooltips, font size optimization, and guidance for authentication. This indicates active development to smooth out minor friction points, likely driven by user complaints.
- **Trust & Reliability:** The rapid fixes for session model divergence ([#2267](https://github.com/netease-youdao/LobsterAI/pull/2267)) and UI hangs ([#2266](https://github.com/netease-youdao/LobsterAI/pull/2266)) are responses to significant user trust issues. The development of a diagnostics export tool ([#2264](https://github.com/netease-youdao/LobsterAI/pull/2264)) is a strong signal that the team is investing in debugging tools for advanced users.

### 8. Backlog Watch
The following items have been open for an extended period and require maintainer attention.

- **[PR #1353](https://github.com/netease-youdao/LobsterAI/pull/1353) (OPEN, Stale)** – **Author:** fhraiwxr. *feat(agent): Agent 技能选择器新增全选和清除功能.*
    - **Age:** ~93 days (Since 2026-04-02).
    - **Risk:** The PR itself is complete and has no conflicts mentioned, but it has been ignored. This risks contributor churn and sends a signal that community contributions are deprioritized.
- **[PR #1464](https://github.com/netease-youdao/LobsterAI/pull/1464) (OPEN, Stale)** – **Author:** gongzhi-netease. *fix(im): add duplicate validation for instance name and credential ID.*
    - **Age:** ~91 days (Since 2026-04-04).
    - **Risk:** This is a data integrity bug for multi-instance IM (DingTalk, Feishu, QQ). Without this fix, users can create duplicate instances and re-add the same bot, leading to message conflicts. This is a **data safety issue** that should be prioritized.

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

Here is the CoPaw project digest for July 4, 2026.

---

### CoPaw Project Digest: 2026-07-04

**Generated from:** GitHub Data (github.com/agentscope-ai/CoPaw)

---

### 1. Today's Overview

CoPaw shows **very high activity** for July 4th, with 39 issues and 33 pull requests updated in the last 24 hours. The project appears to be in a heavy development and stabilization phase, particularly with the `v2.0.0-beta` series. Activity is split between fixing regressions in the new 2.0 runtime (e.g., context management, API routing) and plugging security/feature gaps in the stable `v1.1.x` line (e.g., key sanitization, MCP resilience). The influx of first-time contributors and numerous focused bug-fix PRs suggest a healthy, responsive open-source ecosystem.

### 2. Releases

**No new releases were published today.** The latest release remains the previous version(s). The project is currently active on two tracks: the stable `v1.1.12` series and the beta `v2.0.0b2` series.

### 3. Project Progress

A significant number of PRs were merged or closed today, indicating solid forward momentum. Key areas of progress include:

- **Core Stability & Platform Support:**
    - **Windows Support:** PR [#5525](https://github.com/agentscope-ai/QwenPaw/pull/5525) (merged) implements a native sandbox for Windows, a significant enhancement for that user base.
    - **Provider Updates:** PR [#5735](https://github.com/agentscope-ai/QwenPaw/pull/5735) (merged) updated the GitHub Models provider to use new endpoints and support fine-grained Personal Access Tokens (PATs).
    - **Memory & Reranking:** Two PRs by `lecheng2018` ([#5648](https://github.com/agentscope-ai/QwenPaw/pull/5648), [#5647](https://github.com/agentscope-ai/QwenPaw/pull/5647)) were merged, adding a configurable reranker for memory search, including a new UI configuration panel.

- **Bug Fixes & Configuration:**
    - **Policy Persistence:** PR [#5506](https://github.com/agentscope-ai/QwenPaw/pull/5506) (merged) fixes a critical bug where tool execution policy changes from the frontend were not being saved to the `policy.yaml` file.
    - **MCP Validation:** PR [#5755](https://github.com/agentscope-ai/QwenPaw/pull/5755) (merged) makes the agent configuration resilient to invalid MCP (Model Context Protocol) client configs, preventing a single typo from crashing the entire agent setup.
    - **UI & Session Logic:** PR [#5754](https://github.com/agentscope-ai/QwenPaw/pull/5754) (merged) introduces a unified session item component, and PR [#5764](https://github.com/agentscope-ai/QwenPaw/pull/5764) (merged) adds critical request timeout, retry, and `AbortSignal` support.

### 4. Community Hot Topics

The most active discussions highlight deep technical and architectural challenges:

- **[Issue #5705: Key Sanitization & Security](https://github.com/agentscope-ai/QwenPaw/issues/5705)** (6 comments): A detailed feature request analyzing gaps in the current key security, including env var fallback coverage and missing log sanitization. This shows a community concern for enterprise-grade security.
- **[Issue #5746: 2.0 Beta Context Mismanagement](https://github.com/agentscope-ai/QwenPaw/issues/5746)** (4 comments): A severe bug report describing how the `scroll` context compression in `v2.0.0b2` can lead to the model "losing its memory" mid-task and reverting to old conversation topics. This is a critical stability issue for the new runtime.
- **[Issue #5711: Competitive Analysis & Improvement Roadmap](https://github.com/agentscope-ai/QwenPaw/issues/5711)** (3 comments): A comprehensive, community-driven analysis of CoPaw's weaknesses versus competitors, covering tool efficiency, memory flaws, and missing features. This signals a highly engaged user base invested in the project's direction.
- **[Issue #5769: 2.0 Beta API Routing Bug](https://github.com/agentscope-ai/QwenPaw/pull/5769)** (1 comment, just opened): Reports a `404` error on the new Console due to a double `/api` prefix in the URL path, suggesting a recent regression in the 2.0 frontend-backend integration.

### 5. Bugs & Stability

Several bugs were reported or actively discussed, with many having fix PRs already in progress.

- **Critical:**
    - **v2.0 Context Compression Loss ([#5746](https://github.com/agentscope-ai/QwenPaw/issues/5746)):** The model forgets its current task due to aggressive context compression. **Fix PR:** [#5765](https://github.com/agentscope-ai/QwenPaw/pull/5765) (open) aims to protect the active turn and improve recall.
    - **v2.0 Double API Prefix 404 ([#5769](https://github.com/agentscope-ai/QwenPaw/issues/5769)):** A frontend routing issue causing a 404 for all users of the new Console.
    - **v2.0 Malformed Tool-Call Loop ([#5717](https://github.com/agentscope-ai/QwenPaw/issues/5717)):** Truncated tool-call arguments from a history entry can cause the model to repeat the same task forever. **Fix PR:** [#5761](https://github.com/agentscope-ai/QwenPaw/pull/5761) (open).

- **Medium:**
    - **Context Compression Breaks Channel Awareness ([#5710](https://github.com/agentscope-ai/QwenPaw/issues/5710)):** Agent forgets which chat channel (e.g., Feishu) it is in after context compression.
    - **Plugin Ghost Dependencies ([#5689](https://github.com/agentscope-ai/QwenPaw/issues/5689)):** Deleting a plugin leaves behind a broken import, causing all dialogues to error.
    - **Task Crashes/Freezes ([#5616](https://github.com/agentscope-ai/QwenPaw/issues/5616), [#5763](https://github.com/agentscope-ai/QwenPaw/issues/5763)):** Users report automated tasks crashing or hanging for unknown reasons.

- **Minor:**
    - **Console Chat SDK Limitation ([#5767](https://github.com/agentscope-ai/QwenPaw/issues/5767)):** The single-session model of the SDK blocks multi-agent/workspace features.

### 6. Feature Requests & Roadmap Signals

Several feature requests point toward the project's near-term evolution:

- **High Priority:**
    - **Security & Key Management ([#5705](https://github.com/agentscope-ai/QwenPaw/issues/5705)):** Request for env-var-based key fallbacks and comprehensive log sanitization. Likely for next minor release.
    - **Custom Model Protocols ([#5609](https://github.com/agentscope-ai/QwenPaw/issues/5609)):** Users want to use non-standard API endpoints (e.g., for image generation), which is a blocker for many third-party model providers.

- **Medium Priority:**
    - **Session ID Access in Plugins ([#5547](https://github.com/agentscope-ai/QwenPaw/issues/5547)):** A practical enterprise requirement for passing user context from business systems through to MCP tools.
    - **Plugin Extensibility Hooks ([#4642](https://github.com/agentscope-ai/QwenPaw/issues/4642)):** A request to make Context, Hooks, and Agents extensible via non-invasive plugins. This signals a desire for CoPaw to be a more modular platform.
    - **Windows GBK System Fix ([#4481](https://github.com/agentscope-ai/QwenPaw/issues/4481)):** A request for a system-level solution to Windows encoding issues, replacing the current workaround-based fixes.

### 7. User Feedback Summary

User sentiment is mixed. On one hand, there is **high satisfaction** from a technically sophisticated community that is actively building plugins (see [#4613](https://github.com/agentscope-ai/QwenPaw/issues/4613) on creating a full LightRAG plugin) and providing deep architectural feedback (see [#5711](https://github.com/agentscope-ai/QwenPaw/issues/5711) and [#5705](https://github.com/agentscope-ai/QwenPaw/issues/5705)).

On the other hand, there is **significant frustration** with stability, particularly on the v2.0 beta track:
- **Context loss** is a repeated and deeply disruptive pain point.
- **Configuration fragility** (e.g., MCP config typos crashing the whole agent) erodes trust.
- **Automation tasks** are reported to be unreliable, crashing without explanation.
- **Windows users** continue to struggle with encoding issues, despite previous fixes.

### 8. Backlog Watch

The following items require urgent attention from maintainers:

- **[Issue #4481: System-wide Windows GBK fix](https://github.com/agentscope-ai/QwenPaw/issues/4481):** Despite multiple patches, this issue has been open since May 18. The root cause (system-level encoding) remains unaddressed, affecting all Windows users.
- **[Issue #5547: Session ID in Plugins](https://github.com/agentscope-ai/QwenPaw/issues/5547):** Unanswered for over a week. This is a blocking feature for enterprise deployments connecting CoPaw to internal business logic.
- **[Issue #5710: Context Compression Lacks Protected Anchor Points](https://github.com/agentscope-ai/QwenPaw/issues/5710):** This is a companion to the critical bug #5746. Even if the eviction logic is fixed, the lack of a fundamental "pinning" mechanism for key messages is a design flaw.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

# ZeroClaw Project Digest — 2026-07-04

## 1. Today's Overview

The ZeroClaw project remains highly active with **36 issues updated** (32 open, 4 closed) and **50 pull requests updated** (44 open, 6 merged/closed) in the last 24 hours. No new releases were published today. The project is deep into the **v0.8.3 milestone cycle**, with major feature work advancing across six tracked areas: WASM plugin architecture, Standard Operating Procedures (SOP), security/auth providers, observability, goal-mode runtime, and ZeroCode TUI improvements. **Three critical-severity bugs** were opened today, including approval-gate integrity bypass and process-killing panics, though multiple fix PRs are already in flight. Community engagement is healthy with 13+ comment threads and distributed contributions from maintainers and external integrators.

---

## 2. Releases

**No new releases today.** The last published version remains part of the v0.8.3 development cycle. The upcoming release will incorporate the WASM-out-of-process execution prototype, OIDC multi-user auth, and the SOP authoring suite.

---

## 3. Project Progress

**6 Pull Requests merged/closed today:**

### Closed/Bugs Fixed
- **PR #8524** (`fix(providers): omit empty assistant tool-call content in OpenAI-compatible requests`) — Fixes provider 400 errors when OpenAI-compatible endpoints reject messages carrying `tool_calls` with empty string content. **Rebased and merged**, resolves one root cause behind multi-provider workflow blocks.

### Active Feature/Integration Progress
- **PR #8680** (`fix(skills): bound skill-review history slice against in-fork compaction`) — Fixes the `SIGSEGV` panic from issue #8654 where the skill-review fork panicked with out-of-range slice access. **Now open**, with maintainer review requested.
- **PR #8676** (`feat(cron): expose per-cron-job uses_memory flag in CLI, tools, and gateway API`) — Addresses issue #8397 by making the memory-usage flag for cron jobs configurable through all imperative interfaces. **Open for review.**
- **PR #8672** (`feat(security): multi-user auth providers, permission profiles, and principal isolation`) — Implements the OIDC, SSH-key, peercred, and native pairing auth providers from RFC #7141. **Large surface area change**, open.
- **PR #8661** (`feat(plugins): execute WASM plugins out-of-process via zeroclaw-plugin-host sidecar`) — **Prototype proof-of-concept PR** demonstrating sandboxed plugin execution in a separate process. **Not yet a delivery decision**, but shows technical feasibility.
- **PR #8524** (closed, as above) — Provider fix merged.

---

## 4. Community Hot Topics

### Most Active Issues

| Issue | Comments | Topic |
|-------|----------|-------|
| [#6808](https://github.com/zeroclaw-labs/zeroclaw/issues/6808) | 13 | RFC: Work Lanes, Board Automation, and Label Cleanup |
| [#7462](https://github.com/zeroclaw-labs/zeroclaw/issues/7462) | 8 | 74 test failures on Windows — Unix-only path/console issues |
| [#5542](https://github.com/zeroclaw-labs/zeroclaw/issues/5542) | 7 (closed) | Consecutive OOM in WSL2 — multi-root-cause deep investigation |
| [#7141](https://github.com/zeroclaw-labs/zeroclaw/issues/7141) | 7 | RFC: OIDC authentication provider support |

**Analysis:**
- **#6808 (RFC: Work Lanes)** — Still the most-commented issue after 6 weeks. This governance RFC proposes automated issue routing through label-based board management. The longevity suggests maintainers are iterating on workflow policy, possibly delaying v0.8.3 governance tooling decisions.
- **#7462 (Windows Testing)** — Windows CI coverage is a persistent pain point. The community's reluctance to add Windows CI jobs (only Linux runs) is costing real user confidence: 74 test failures on Windows are undetected in CI. Expect this to become a P0 blocker before v0.9.0.
- **#5542 (WSL2 OOM)** — Now partially resolved by #8633 (component-supervisor backoff) but the memory-growth root cause was split into separate issue #8642. The project is handling this responsibly with root-cause decomposition.

### Most Active Pull Requests

| PR | Context | Impact |
|----|---------|--------|
| [#8661](https://github.com/zeroclaw-labs/zeroclaw/pull/8661) | WASM plugin sidecar prototype | **Architecture-critical** — if adopted, changes plugin security model entirely |
| [#8590](https://github.com/zeroclaw-labs/zeroclaw/pull/8590) | Visual SOP authoring (XL-size) | Largest PR open; affects 20+ components; calling for beta testers |
| [#8567](https://github.com/zeroclaw-labs/zeroclaw/pull/8567) | OTel content policy | RFC #8462 implementation; enables production observability opt-in |

---

## 5. Bugs & Stability

### New Bugs Today (Highest to Lowest Severity)

| ID | Severity | Title | Fix PR? |
|----|----------|-------|---------|
| [#8678](https://github.com/zeroclaw-labs/zeroclaw/issues/8678) | **S2** (approval-gate integrity bypass) | `advance_step` has no run-status guard — a driver can bypass an approval gate via `sop_advance` | **No** — opened today |
| [#8654](https://github.com/zeroclaw-labs/zeroclaw/issues/8654) | **S2** (daemon SIGSEGV) | `skill-review fork panics (out-of-range slice)` → daemon crashes with SIGSEGV after tool-heavy turn | **PR #8680** — fix open |
| [#8642](https://github.com/zeroclaw-labs/zeroclaw/issues/8642) | **S2** (RSS growth) | MCP/tool-schema cloning drives unbounded RSS growth in agent loop (split from OOM #5542) | **No** — investigation |
| [#8675](https://github.com/zeroclaw-labs/zeroclaw/issues/8675) | **S1** (workflow blocked) | Malformed native tool-call arguments sent unvalidated to OpenRouter/OpenAI providers → provider 400 → empty reply | **No** — opened today |
| [#8627](https://github.com/zeroclaw-labs/zeroclaw/issues/8627) | **S1** (workflow blocked) | WhatsApp Web device linking broken by new passkey/SHORTCAKE companion-linking gate | **No** — status:blocked |
| [#8644](https://github.com/zeroclaw-labs/zeroclaw/issues/8644) | **S2** (degraded) | ZeroCode can complete a Code turn with no visible assistant output | **No** |
| [#8645](https://github.com/zeroclaw-labs/zeroclaw/issues/8645) | **S2** (degraded) | Reload banner shows persistent drift for ZEROCLAW_* env-overridden secrets | **No** |
| [#8664](https://github.com/zeroclaw-labs/zeroclaw/issues/8664) | **S2** (minor) | ZeroCode code-block Copy includes Markdown fences and highlights message | **No** |
| [#8652](https://github.com/zeroclaw-labs/zeroclaw/issues/8652) | **S3** (minor) | ZeroCode transcript highlight does not dismiss on blank side clicks | **No** |

### Critical Risk Bugs Open
- **#8675 (provider validation)** — Unvalidated JSON arguments cause silent provider errors; affects all OpenAI-compatible providers (OpenRouter, Azure, Copilot). Likely to be promoted to P0.
- **#8654 (skill-review panic)** — SIGSEGV means the daemon exits, taking down all agents in a multi-agent pod. PR #8680 is an urgent fix.
- **#8678 (SOP approval bypass)** — An approval-gate integrity violation, albeit requiring driver access. Security impact is moderate but trust impact is high.

---

## 6. Feature Requests & Roadmap Signals

### Likely for v0.8.3 or v0.9.0

| Feature | Tracking Issue/PR | Status | Likely Ship |
|---------|------------------|--------|-------------|
| WASM plugin out-of-process execution | [#8661](https://github.com/zeroclaw-labs/zeroclaw/pull/8661) (PR) | Prototype, not yet decision | v0.9.0+ |
| OIDC multi-user auth + permission profiles | [#7141](https://github.com/zeroclaw-labs/zeroclaw/issues/7141), [#8672](https://github.com/zeroclaw-labs/zeroclaw/pull/8672) (PR) | Implementation open | v0.8.3 |
| Goal mode (durable bounded sessions) | [#8303](https://github.com/zeroclaw-labs/zeroclaw/issues/8303), [#8393](https://github.com/zeroclaw-labs/zeroclaw/pull/8393) (PR) | ADR + feature work | v0.8.3 |
| SOP visual authoring (fan-in, tests, docs) | [#8590](https://github.com/zeroclaw-labs/zeroclaw/pull/8590) (PR) | XL PR, calling beta testers | v0.8.3 |
| OTel content policy (opt-in LLM/tool I/O capture) | [#8567](https://github.com/zeroclaw-labs/zeroclaw/pull/8567) (PR) | Open, RFC #8462 impl | v0.8.3 |
| Per-cron-job `uses_memory` exposure | [#8676](https://github.com/zeroclaw-labs/zeroclaw/pull/8676) (PR) | Open | v0.8.3 |
| Context window usage bar in all chat surfaces | [#7946](https://github.com/zeroclaw-labs/zeroclaw/pull/7946) (PR) | Open, spanning TUI+Gateway+CLI | v0.8.3 |
| Remove hardcoded ClawHub → git-catalog skill installer | [#8638](https://github.com/zeroclaw-labs/zeroclaw/pull/8638) (PR) | Breaking change, open | v0.9.0 |
| Plugin authoring guide series (WASM component-model) | [#8621](https://github.com/zeroclaw-labs/zeroclaw/pull/8621) (PR) | Docs open | v0.8.3 |
| Agent-policy parity harness | [#8659](https://github.com/zeroclaw-labs/zeroclaw/pull/8659) (PR) | Tests-only, open | v0.8.3 |
| Auto-resume most recent Code session | [#8653](https://github.com/zeroclaw-labs/zeroclaw/issues/8653) | Enhancement request | v0.8.4+ |
| uses_memory checkbox in Gateway UI | [#8677](https://github.com/zeroclaw-labs/zeroclaw/issues/8677) | Enhancement request | v0.8.3 if fast |

### Community Requests
- **#8677** (uses_memory checkbox in web UI) — Tracks the same gap as #8397: the Gateway web UI lacks a checkbox for cron memory-usage flag. Low complexity, likely picked up soon.
- **#8653** (auto-resume Code sessions) — Repeated community friction point: "session resume feels manual." Likely fast follow after ZeroCode stability.

---

## 7. User Feedback Summary

### Real Pain Points
- **Windows testing gap** (#7462): 74 test failures on Windows remain undetected because CI runs only on Linux. The community reporter's production setup is Windows 11 with Chinese locale — a significant population of users are getting degraded experiences.
- **WSL2 OOM continuing** (#8642, split from #5542): Memory growth from MCP tool-schema cloning is still being investigated. Users in containerized/WSL2 environments report instability.
- **WhatsApp channel broken** (#8627): A new WhatsApp security gate (passkey/SHORTCAKE) broke device linking entirely. Status:blocked means no ETA.
- **SOP workflow friction**: Multiple SOP-related bugs today (#8678 approval bypass, #8631 false-green audit trails) suggest the SOP engine is mature but has integration holes.
- **Provider validation gap** (#8675): Silent provider failures when tool-call arguments are malformed — users get empty replies without diagnostic error messages.

### Satisfactions
- **SOP visual authoring beta** (#8590) was called out with "Calling Beta Testers" — the community is engaging with deterministic workflow tooling.
- **Plugin authoring guides** (#8621) received external validation (third-party integrator built a real plugin against them), suggesting the developer experience is improving.
- **Multi-user auth** (#8672) addresses a long-standing enterprise requirement for principal isolation.

---

## 8. Backlog Watch

### Issues Needing Maintainer Attention

| Issue | Age | Priority | Reason to Watch |
|-------|-----|----------|-----------------|
| [#6716](https://github.com/zeroclaw-labs/zeroclaw/issues/6716) — PR architecture review skill | 49 days | P2, risk:medium | PR has been open since May 16 with no maintainer updates. Valuable for PR quality but stuck. |
| [#6717](https://github.com/zeroclaw-labs/zeroclaw/issues/6717) — Integrate arch-review into PR session | 49 days | P2, risk:low | Twin to #6716; same author, same inactivity. |
| [#6718](https://github.com/zeroclaw-labs/zeroclaw/issues/6718) — Document work queue query in issue triage | 49 days | P2, risk:low | Trivial doc change but languishing for 7 weeks. |
| [#8627](https://github.com/zeroclaw-labs/zeroclaw/issues/8627) — WhatsApp Web broken | 2 days | **P1, blocked** | New external dependency change (WhatsApp serving security gate) — may need upstream investigation rather than code fix. |
| [#8393](https://github.com/zeroclaw-labs/zeroclaw/issues/8393) — Goal mode implementation | 7 days | **P2, risk:high, size:XL** | Huge PR with `needs-author-action` label — author needs to respond to maintainer feedback or the feature may miss v0.8.3. |
| [#8519](https://github.com/zeroclaw-labs/zeroclaw/issues/8519) — Reconcile cargo-audit ignores and remediate wasmtime-wasi CVEs | 4 days | P1, risk:high | 22 RustSec advisories on master; CI is failing. Must be resolved before v0.8.3 release to avoid shipping with known CVEs. |
| [#8632](https://github.com/zeroclaw-labs/zeroclaw/issues/8632) — Source install with embedded-web fails before API client exists | 2 days | **P1, in-progress** | Blocks clean source builds for developers; maintainers are actively working. |

### Most Pressing Backlog Item
**Issue #8519** (cargo-audit CVE drift) — 22 advisories are not tracked by `.cargo/audit.toml`, CI is failing master. This is both a release blocker and a security risk if ignored. The `in-progress` status suggests maintainers are aware, but the issue has 0 comments, so community visibility is low.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*