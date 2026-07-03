# OpenClaw Ecosystem Digest 2026-07-03

> Issues: 196 | PRs: 500 | Projects covered: 13 | Generated: 2026-07-03 02:01 UTC

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

# OpenClaw Project Digest — 2026-07-03

## Today's Overview

OpenClaw shows **very high activity** with 196 issues and 500 PRs updated in the last 24 hours, alongside a **new beta release (v2026.7.1-beta.1)** introducing GPT-5.6 support and external harness attachment. Despite strong development momentum, the project is grappling with a **concentrated bug burden**: multiple P1 regressions in session state, message loss, and auth provider stability persist from earlier releases (2026.5.27, 2026.6.11), indicating quality control gaps in the release pipeline. Roughly **72 issues were closed** and **66 PRs merged/closed** — a healthy throughput — but the open/active issue count (124) and open PR count (434) signal a **widening backlog** that may strain maintainers.

---

## Releases

### v2026.7.1-beta.1 (published 2026-07-03)

- **OpenAI GPT-5.6 support:** Model family now recognized across catalog, capability, and runtime selection paths ([#98333](https://github.com/openclaw/openclaw/issues/98333))
- **External harness attachment:** `openclaw attach` launches an external harness against an existing Gateway session

**No breaking changes or migration notes reported.**

---

## Project Progress

**66 PRs merged/closed yesterday.** Notable merges include:

- **Memory stability:** `fix(memory-wiki): avoid implicit error coercion` ([#99307](https://github.com/openclaw/openclaw/pull/99307)) — unblocks CI lint on main
- **MCP safety:** `fix(mcp): bound HTTP response body reads at 1 MiB` ([#99293](https://github.com/openclaw/openclaw/pull/99293)) — prevents OOM from large MCP server responses
- **Telegram ambient persistence:** `feat(auto-reply): persist ambient room events as transcript rows` ([#99306](https://github.com/openclaw/openclaw/pull/99306)) — fixes [#99257](https://github.com/openclaw/openclaw/issues/99257)
- **Testing expansion:** `test(qa): cover Crabline Zalo transport` ([#99303](https://github.com/openclaw/openclaw/pull/99303)) — new QA coverage for Zalo gateway
- **Consolidation:** `refactor(shared): consolidate remaining channel lazy loaders` ([#99302](https://github.com/openclaw/openclaw/pull/99302)) — reduces duplicated dynamic-import patterns across channels
- **Agent failure surface:** `fix: surface terminal agent run failures` ([#99304](https://github.com/openclaw/openclaw/pull/99304)) — improves error visibility for agent runs that fail silently

---

## Community Hot Topics

### Most commented issues (last 24h)

1. **#25592** — *"Text between tool calls leaks to messaging channels"* (33 comments, 🔥 urgent) — [Link](https://github.com/openclaw/openclaw/issues/25592)  
   Persistent UX issue: agent-internal processing text routed to Slack/iMessage as visible messages. Labeled `diamond lobster`, `security`, `message-loss`. Open since Feb 2026 — community frustration is palpable.

2. **#88312** — *"[Regression] Codex app-server turn-completion stall"* (19 comments, 👍5) — [Link](https://github.com/openclaw/openclaw/issues/88312)  
   Repeated regression of a previously-fixed bug. Affects Codex-backed multi-tool agent turns. A `platinum hermit` severity issue.

3. **#92201** — *"Embedded runner: freshly streamed thinking signatures intermittently invalid on replay (Anthropic)"* (18 comments) — [Link](https://github.com/openclaw/openclaw/issues/92201)  
   Anthropic thinking-block replay failure with recovery wrapper that never fires. `diamond lobster` — high community engagement.

4. **#73148** — *"Image tool: opaque 'Failed to optimize image' when sharp is not installed"* (14 comments) — [Link](https://github.com/openclaw/openclaw/issues/73148)  
   Poor error messaging for missing native dependency. Users frustrated by silent failures.

5. **#98416** — *"v2026.6.11 published dist missing reentrancy guard"* (8 comments, 👍5) — [Link](https://github.com/openclaw/openclaw/issues/98416)  
   **Distribution integrity failure** — published build missing a critical fix from source; reply session initialization conflicted. High trust concern.

### Most reacted

- **#88312** (👍5) — Codex stall regression
- **#98416** (👍5) — Reentrancy guard missing in published dist

**Underlying needs:** Users are demanding **reliable agent-turn completion**, **correct replay of streaming signatures**, and **transparent error reporting** (no more opaque "failed to optimize image" without actionable diagnostics). The reentrancy distribution gap (#98416) has eroded trust in release quality.

---

## Bugs & Stability

### Critical (P1, active, high severity)

| Issue | Summary | Impact | Fix PR exists? |
|-------|---------|--------|----------------|
| [#25592](https://github.com/openclaw/openclaw/issues/25592) | Inter-tool text leaks to messaging channels | Message loss, security | No |
| [#88312](https://github.com/openclaw/openclaw/issues/88312) | Codex turn-completion stall (regression) | Session state, message loss | No |
| [#92201](https://github.com/openclaw/openclaw/issues/92201) | Anthropic thinking signatures invalid on replay | Session state, message loss | No |
| [#98416](https://github.com/openclaw/openclaw/issues/98416) | Published dist missing reentrancy guard | Session state, message loss | No |
| [#72015](https://github.com/openclaw/openclaw/issues/72015) | Active-memory blocks replies; QMD boot overload | Crash-loop | No |
| [#70024](https://github.com/openclaw/openclaw/issues/70024) | Channel stop timeout leaves channel permanently dead | Session state, message loss | No |
| [#98790](https://github.com/openclaw/openclaw/issues/98790) | Concurrent agent-to-agent turn forks; post-compaction Anthropic replay failure | Data loss, session state | No |
| [#99164](https://github.com/openclaw/openclaw/pull/99164) | PR: Classify Anthropic refusal as failover-eligible | Auth provider | **Yes** (open) |

### New today (2026-07-03)

- **#99253** — *"Assistant self-inserted a fabricated user turn and answered it as real input"* (P2, `security`) — [Link](https://github.com/openclaw/openclaw/issues/99253)  
  Serious safety hallucination: assistant generated fake timestamped user messages and responded to them. Supersedes #99252.

- **#99241** — *"Tool outputs sometimes render as image attachments and become unreadable to the agent"* (P1-ish, behavior bug) — [Link](https://github.com/openclaw/openclaw/issues/99241)  
  Long-running/ANSI-heavy tool results collapse into `(see attached image)` placeholder; agent cannot read original stdout.

- **#99183** — *"Local embedding worker fork fails with ENOENT after Node upgrade"* (P2) — [Link](https://github.com/openclaw/openclaw/issues/99183)  
  `fork()` inherits execPath of a deleted binary; fails silently on Node upgrade — systemic fragility in worker lifecycle management.

- **#99186** — *"Tool results with Cyrillic UTF-8 rendered as image attachment in webchat"* (P1, closed) — [Link](https://github.com/openclaw/openclaw/issues/99186)  
  Multi-byte UTF-8 rendering failure in webchat — closed, presumed fixed, but indicates encoding fragility.

### Regressions mentioned

- **#98614** — *"sessions_spawn missing scope operator.write — introduced between v2026.6.1 and v2026.6.11"* — [Link](https://github.com/openclaw/openclaw/issues/98614)

---

## Feature Requests & Roadmap Signals

### High-priority user requests

| Issue | Summary | Likely next-release inclusion |
|-------|---------|-------------------------------|
| [#35203](https://github.com/openclaw/openclaw/issues/35203) | Multi-Agent Collaboration: Capability Profiling + Shared Blackboard + Layered Memory + Token Cost Governance | **Unlikely** — massive RFC, P2, needs security review; at least 2-3 releases out |
| [#32530](https://github.com/openclaw/openclaw/issues/32530) | Auto-discovery of agent configurations from external workspaces | **Possible** — moderate effort, strong UX improvement, could land in 2026.7.x |
| [#77165](https://github.com/openclaw/openclaw/issues/77165) | Auto-generate session titles via AI summarization | **Likely** — low-effort, highly visible UX win, P3 |
| [#11623](https://github.com/openclaw/openclaw/issues/11623) | Floating agent bubbles (Clawi) for macOS | **Unlikely** — P3, no maintainer activity, niche |
| [#75947](https://github.com/openclaw/openclaw/issues/75947) | UI quality update based on UX scoring | **Possible** — open PR, linked work, could land as iterative improvements |

### Beta/experimental features gaining traction

- Native Signal reply quotes ([#95718](https://github.com/openclaw/openclaw/pull/95718)) — ready for maintainer review
- iOS native SwiftUI redesign ([#99231](https://github.com/openclaw/openclaw/pull/99231)) — significant UX overhaul, in re-review loop
- Provider refusal failover chain ([#99164](https://github.com/openclaw/openclaw/pull/99164)) — targeted for next release to reduce silent failures

---

## User Feedback Summary

### Pain points (recurring themes)

1. **"Broken on upgrade"** — Multiple users report regressions after point releases (2026.5.27→5.30, 2026.6.10→6.11). Trust in patch releases is eroding.
2. **"Silent failures"** — Opaque errors (`Failed to optimize image`, `Cannot convert undefined or null to object`, `Codex stopped before confirming`) dominate the issue tracker. Users want actionable diagnostics.
3. **"Multi-turn reliability"** — Agent sessions that stall, produce no output, or hallucinate fabricated user turns are the #1 frustration.
4. **"Cross-platform inconsistency"** — iOS, Android, Telegram, WebChat, and OpenWebUI each have distinct failure modes for the same underlying operations (image uploads, streaming progress, tool output rendering).

### Satisfaction signals

- **GPT-5.6 support** in v2026.7.1-beta.1 was requested and is now available — users appreciate model currency.
- **Discord large-attachment fix** ([#99053](https://github.com/openclaw/openclaw/pull/99053)) addresses a painful silent-message-loss issue.
- **iOS native UI work** ([#99231](https://github.com/openclaw/openclaw/pull/99231)) is getting positive attention; re-review loop indicates maintainers are taking it seriously.

### Notable use case: Safety hallucination

Issue [#99253](https://github.com/openclaw/openclaw/issues/99253) — an assistant fabricated a timestamped user turn and responded to it — is a **critical safety event**. The user describes it as "more serious than a UI/rendering ambiguity." This underscores the need for transcript integrity verification in agent outputs.

---

## Backlog Watch

### Issues stale or unactioned for >30 days, still P1/P2

| Issue | Days open | Status | Why it matters |
|-------|-----------|--------|----------------|
| [#25592](https://github.com/openclaw/openclaw/issues/25592) | **129 days** | `no-new-fix-pr`, `needs-maintainer-review`, `needs-product-decision`, `needs-security-review` | The highest-commented issue. Text leakage = message loss + security risk. Dating from Feb 2026 — a concerning gap. |
| [#38327](https://github.com/openclaw/openclaw/issues/38327) | **118 days** | `no-new-fix-pr`, `needs-maintainer-review`, `needs-product-decision` | Null/undefined crash on Gemini. Impact: auth provider, crash-loop. |
| [#40880](https://github.com/openclaw/openclaw/issues/40880) | **115 days** | `no-new-fix-pr`, `needs-maintainer-review`, `needs-product-decision`, `needs-security-review` | Hardcoded 5 MB media limit; cannot be configured. Blocks real-world workflows. |
| [#73148](https://github.com/openclaw/openclaw/issues/73148) | **66 days** | `stale` | Opaque "Failed to optimize image" error. P1, but labeled stale — contradicting severity. |
| [#47910](https://github.com/openclaw/openclaw/issues/47910) | **108 days** | `stale`, `needs-maintainer-review`, `needs-product-decision` | Provider failover by failure class — auth-broken providers waste retries. Collects community frustration. |

### PRs awaiting maintainer attention

| PR | Days open | Status | Risk |
|----|-----------|--------|------|
| [#95718](https://github.com/openclaw/openclaw/pull/95718) | 11 days | `ready for maintainer look` | Low — Signal reply quotes, well-scoped |
| [#98527](https://github.com/openclaw/openclaw/pull/98527) | 2 days | `ready for maintainer look` | **Critical** — fixes Anthropic replay failure after compaction (directly addresses #92201, #98790) |
| [#68936](https://github.com/openclaw/openclaw/pull/68936) | **75 days** | Closed but massive (XL) | Auto-fix pipeline + Windows daemon; closed but no evidence of integration — potential process gap |

**Recommendation:** The backlog of high-severity issues (especially #25592 and #38327) without fix PRs or product decisions indicates the project needs a **prioritized bug-sweep release** (e.g., v2026.7.2) focused on the 5-6 most damaging, long-lived P1 regressions before adding new features. The GPT-5.6 support in today's release is valuable, but users are increasingly vocal about "working on the last release" rather than chasing model support.

---

## Cross-Ecosystem Comparison

# AI Agent Open-Source Ecosystem: Cross-Project Comparison Report

**Prepared:** 2026-07-03  
**Scope:** 11 projects in the personal AI assistant / agent open-source ecosystem  
**Data window:** Last 24 hours (2026-07-02 → 2026-07-03)

---

## 1. Ecosystem Overview

The personal AI agent open-source landscape is experiencing a **hyperactive development cycle**, with the seven most active projects collectively processing over **1,000 issues and PRs** in a single day. Quality control remains the ecosystem's biggest challenge—projects across the board are shipping beta releases with known regressions, and user trust in point-release stability is eroding. The community is converging on several shared priorities: **multi-agent collaboration**, **channel integration reliability** (Slack, WhatsApp, Telegram, Feishu), and **deployment flexibility** (thin-client desktops, environment-variable configuration, headless CLI operation). A notable divide is emerging between projects optimizing for **enterprise multi-tenancy** (IronClaw, ZeroClaw) versus those prioritizing **individual power-user experience** (Hermes Agent, NanoBot). Three projects—NullClaw, TinyClaw, and ZeptoClaw—show zero activity over the observation period, suggesting possible hibernation or deprioritization.

---

## 2. Activity Comparison

| Project | Issues Updated (24h) | PRs Updated (24h) | Merged/Closed PRs (24h) | Release Status | Health Signal |
|---|---|---|---|---|---|
| **OpenClaw** | 196 | 500 | 66 | v2026.7.1-beta.1 (today) | Very High Activity / Widening Backlog |
| **ZeroClaw** | 37 | 50 | 19 | v0.8.x (no new today) | High Activity / Healthy |
| **CoPaw** | 23 | 50 | 27 | v2.0.0-beta.2 (today) | High Activity / Growing Community |
| **IronClaw** | 23 | 50 | 21 | Pending v0.29.1 | High Activity / Platform Overhaul |
| **Hermes Agent** | 50 | 50 | 26 | v0.18.0 (2026.7.1) | High Activity / Effective Delivery |
| **NanoBot** | 98 | 63 | 28 | No new release | High Activity / Maintenance Push |
| **PicoClaw** | 2 | 25 | 14 | v0.2.9 (git 2992) | Moderate / Maintenance Focus |
| **NanoClaw** | 4 | 14 | 2 | No new release | Moderate / Good Triage |
| **LobsterAI** | 0 | 8 | 7 | No new release | Moderate / Polish Phase |
| **Moltis** | 0 | 3 | 1 | No new release | Low / Steady |
| **NullClaw** | 0 | 0 | 0 | N/A | **Inactive** |
| **TinyClaw** | 0 | 0 | 0 | N/A | **Inactive** |
| **ZeptoClaw** | 0 | 0 | 0 | N/A | **Inactive** |

**Key observations:**
- OpenClaw dominates raw volume but shows a **dangerous backlog**: 434 open PRs and 124 open issues, the highest in the ecosystem.
- NanoBot has the second-highest issue activity (98) despite a smaller codebase—indicating rapid user growth or poor stability.
- CoPaw's 27 merged/closed PRs in one day with 6 first-time contributors signals strong community onboarding.
- Three inactive projects may represent abandoned or stalled efforts.

---

## 3. OpenClaw's Position

**Advantages over peers:**

1. **Scale leadership**: 500 PRs in 24 hours dwarfs every other project—OpenClaw is the central reference implementation with the largest contributor base. GPT-5.6 support shipped within hours of availability demonstrates superior model currency.

2. **Integration breadth**: Telegram, Signal, Zalo, Slack, iMessage—OpenClaw's channel coverage exceeds all competitors. The external harness attachment (`openclaw attach`) is a unique architectural capability.

3. **Community visibility**: Issues like #25592 (inter-tool text leakage, 129 days open, 33 comments) are the ecosystem's most-discussed bugs, making OpenClaw the de facto standards-setter for what problems matter.

**Technical approach differences:**

| Dimension | OpenClaw | Peers (Typical) |
|---|---|---|
| Architecture | Modular gateway + harness; monorepo | Coordinated services (IronClaw); monolithic Golang (ZeroClaw) |
| Release cadence | Frequent betas (point releases weekly) | Milestone-driven (Hermes v0.18.0, CoPaw v2.0.0) |
| Language | Multi-language (monorepo) | Rust (ZeroClaw), Python (Hermes), Go (PicoClaw) |
| Memory model | Wiki + ambient persistence + active memory | Semantic/corporate memory (NanoBot); holographic memory (Hermes) |

**Community size comparison:**

- OpenClaw: ~196 issues + 500 PRs/day → **largest ecosystem by ~4x** vs. next largest (ZeroClaw at 50 PRs).
- However, Hermes Agent (50 issues, 50 PRs) has a **higher PR-to-issue ratio** (1.0 vs. OpenClaw's 2.5), indicating more efficient triage.
- CoPaw's first-time contributor inflow (6/day) exceeds OpenClaw's, suggesting better onboarding.

**Key weakness:** OpenClaw's quality gap (multiple P1 regressions from releases 30+ days ago, distribution integrity failure #98416) is eroding its trust advantage. The 434 open PR backlog risks maintainer burnout.

---

## 4. Shared Technical Focus Areas

The following requirements are emerging **independently across multiple projects**, indicating ecosystem-wide priorities:

| Focus Area | Projects Affected | Specific Need |
|---|---|---|
| **Multi-tenant configuration** | ZeroClaw (#8226), IronClaw (#5459), OpenClaw (implicit via multi-agent requests), NanoBot (#4253) | Per-conversation/agent model overrides, custom environment variables, admin-shared vs. user-private tool scopes |
| **Channel identity consistency** | NanoClaw (#2911, #2912), Moltis (#1116), CoPaw (#5721), Hermes (#52914) | Same user gets different IDs across WhatsApp paths (Baileys vs. Cloud); Signal DM prefix inconsistency; Feishu sender identity loss |
| **Oauth/credential UX** | IronClaw (#5576, #5502), CoPaw (#5705), NanoBot (#4632), Hermes (#23944) | Move from manual token paste to browser OAuth; environment-variable config for headless/container deployments |
| **Memory/context reliability** | OpenClaw (#92201, #98790), CoPaw (#5746, #5710), ZeroClaw (#8570), Hermes (#24558) | Anthropic replay failures, scroll context folding active tasks, CJK retrieval degradation, durable store seams |
| **Tool/MCP visibility consistency** | ZeroClaw (#8193, #8302), CoPaw (#5748), OpenClaw (#25592) | Tools present in gateway but invisible to TUI; agent hangs on tool failure; inter-tool text leaks as visible messages |
| **Thin-client deployment** | Hermes (#38602, 37👍), CoPaw (#5737), ZeroClaw (#7952) | Desktop client-only mode without local runtime bootstrap; CLI headless operation for non-GUI environments |

**Underlying pattern:** The ecosystem is evolving from single-user, single-machine agents toward **multi-tenant, multi-platform, enterprise-ready platforms**. Every project is hitting the same scaling pains simultaneously.

---

## 5. Differentiation Analysis

| Project | Primary Target User | Key Differentiator | Technical Architecture |
|---|---|---|---|
| **OpenClaw** | Developers / Modders | **Reference implementation**; greatest model & channel breadth; most extensible | Modular gateway + harness; monorepo |
| **Hermes Agent** | Power users / Desktop-first users | **Best desktop UX** (macOS Tahoe, iOS SwiftUI redesign); comprehensive UI across desktop, TUI, web | Python agent + desktop clients |
| **NanoBot** | Individual users / Chat-first | **Lightweight, fast iteration**; strong MCP support; GitHub Copilot provider integration | Node.js / TypeScript |
| **ZeroClaw** | Enterprise / Multi-agent operators | **Rust performance & safety**; Git forge channels (GitHub, Gitea); SOP ingress for workflow automation | Rust daemon + CLI + web |
| **IronClaw** | Enterprise / Platform builders | **Reborn platform overhaul**; rich OAuth/SSO; skill auto-discovery; OpenTelemetry observability | Rust microservices (ironclaw_common, ironclaw_skills) |
| **CoPaw** | Qwen ecosystem users / Chinese market | **Qwen-native**; strong CLI cron/hooks; Feishu integration; model auto-fallback | Python + v2.0.0 beta rearchitecture |
| **PicoClaw** | Embedded / IoT users | **Minimal footprint**; DeltaChat integration; Go performance | Go binary + lightweight |
| **NanoClaw** | Container orchestrators | **Agent templates hub**; Docker-first (`--shm-size`, `--init`); WhatsApp Cloud API | Python + container-native |
| **LobsterAI** | Chinese consumers | **DeepSeek optimization**; client app focus; scheduled tasks | Node.js / Electron |
| **Moltis** | WhatsApp-heavy users | **Privacy-focused WhatsApp integration** (LID-native addressing); simple, targeted | Rust |

**Critical architectural fork:** The Rust projects (ZeroClaw, IronClaw, Moltis) are converging on **memory safety and performance**, while Python/Node projects (OpenClaw, Hermes, NanoBot, CoPaw) prioritize **rapid feature iteration and model support**. This split will deepen as enterprise adoption drives demand for Rust's reliability guarantees.

---

## 6. Community Momentum & Maturity

**Tier 1 — Rapid Iteration (Shipping daily, high contribution velocity):**
- **OpenClaw**: Highest raw activity but **fragile quality**—shipping GPT-5.6 support while P1 regressions languish for 129 days. The 434 open PR backlog is unsustainable.
- **ZeroClaw**: Strong architectural vision (v0.9.0 tracker, memory overhaul, Git forge channels). 19 PRs merged in 24 hours is healthy. The S0 OOM bug (#5542, 85 days old) is the main risk.
- **CoPaw**: **Fastest-growing contributor base** (6 first-timers/day). v2.0.0-beta.2 instability warnings are honest, but the memory leak (#5720) and scroll context bug (#5746) need rapid attention.

**Tier 2 — Active Development (Weekly cycles, focused delivery):**
- **Hermes Agent**: Most **balanced** project—26 PRs merged/day with clear desktop-first identity. The 37-upvote thin-client request (#38602) is the strongest feature demand signal in the ecosystem.
- **IronClaw**: High intensity but **internally focused** (Reborn platform, OAuth infrastructure). Nightly E2E has failed for 37 days (#4108)—a concerning continuity gap.
- **NanoBot**: High issue volume (98/day) suggests **user growth outpacing stability**. Batch bug fixes (#4648) are effective but reactive.

**Tier 3 — Stabilizing / Maintenance (Slow burn):**
- **PicoClaw**: 14 PRs merged but mostly dependency bumps. The config migration crash (#3206) and Matrix reconnection gap (#3203) are critical blockers for new users.
- **NanoClaw**: Small but **focused**—WhatsApp adapter fixes arrived same-day as bug reports. Template hub (#2890) points to a clear v1.0 roadmap.
- **LobsterAI**: **Polish phase**—7 PRs merged, all fixes and cleanup. No new feature work visible. Stale issues (92 days old) erode community trust.
- **Moltis**: **Steady state**—maintainers merging targeted fixes (WhatsApp LID) but no significant community growth.

**Tier 4 — Inactive (No activity):**
- **NullClaw, TinyClaw, ZeptoClaw**: No updates in 24 hours. These may be dormant or abandoned.

---

## 7. Trend Signals

**1. The quality-vs-velocity tradeoff is reaching a breaking point.**
The ecosystem is shipping features faster than it can stabilize them. OpenClaw's distribution integrity failure (#98416), Hermes's QQBot reconnect regression (#52914), and CoPaw's v2.0.0b2 scroll context bug (#5746) all point to **insufficient regression testing**. AI agent developers adopting these projects for production should budget 20-30% overhead for patch tracking and rollback planning.

**2. Loosely-coupled MCP adopts, while deeply-integrated platforms diverge.**
The MCP (Model Context Protocol) standard is broadly supported (OpenClaw, NanoBot, ZeroClaw, CoPaw all reference it), but each project wraps it differently. For developers building multi-agent systems, this means MCP tools are portable, but tool visibility and error handling differ by platform. ZeroClaw's MCP visibility bug (#8193) is emblematic of this fragmentation.

**3. Channel parity is the new baseline, not a differentiator.**
Every active project supports at least Telegram, WhatsApp, Slack, and Discord. Differentiation now comes from **specific verticals**: ZeroClaw's Git forge channels, CoPaw's Feishu integration, Moltis's privacy-focused WhatsApp LID handling. Developers should evaluate not just which channels are supported, but **how well they handle edge cases** (identity consistency, reconnection, message delivery receipts).

**4. The "thin-client" pattern is the next battleground.**
Hermes (#38602, 37 upvotes) and CoPaw (#5737) both have active feature requests for **headless/CLI-only operation** connecting to remote runtimes. This mirrors the enterprise trend toward centralized agent infrastructure with lightweight clients. Expect ZeroClaw and IronClaw to follow suit, given their enterprise positioning.

**5. Memory management remains the hardest unsolved problem.**
Across all projects, memory subsystems are being rewritten or patched:
- OpenClaw: Active memory blocks, Anthropic replay failures
- ZeroClaw: Durable store seam, OOM in WSL2
- CoPaw: Memory leak, scroll context compression
- Hermes: Holographic memory CJK extraction fix

No project has a "good enough" solution yet. For AI agent developers, **expect memory-related breaking changes** in every major release for at least the next 6 months.

**6. Chinese-market projects are developing parallel infrastructure.**
CoPaw (Qwen-native), LobsterAI (DeepSeek-optimized), and NanoClaw (WeChat ecosystem) are building AI agents for the Chinese domestic market with distinct requirements: Feishu/DingTalk channels, DeepSeek/Qianwen model optimization, and simplified deployment. Companies targeting the Chinese AI agent market should evaluate these projects over the global alternatives.

---

**Bottom line for technical decision-makers:** For production deployments, **Hermes Agent** offers the best balance of stability, UX, and delivery cadence. For maximum extensibility and model support, **OpenClaw** remains the reference but requires careful regression management. For Rust-native performance and enterprise features, **ZeroClaw** is the most architecturally ambitious choice, albeit with the longest path to stability. The ecosystem is evolving fast—plan for quarterly architecture reviews and maintain rollback capability.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

Here is the NanoBot project digest for July 3, 2026.

---

### NanoBot Project Digest: 2026-07-03

### 1. Today's Overview
NanoBot is experiencing a period of extremely high activity, with 98 issues and 63 pull requests updated in the last 24 hours. A significant portion of this traffic appears to be driven by a proactive maintenance push from a core contributor (`hamb1y`), who has submitted a large batch of focused fix PRs. While no new releases were cut today, the volume of open issues (95) combined with a high volume of incoming PRs suggests the project is both actively resolving bugs and encountering new reports from a growing user base. Project health is strong, marked by rapid response to critical bugs, but the sheer volume may indicate a need for more maintainer bandwidth.

### 2. Releases
No new releases were published today.

### 3. Project Progress
Today saw a significant number of closed/merged PRs (28), indicating considerable progress. Key advancements include fixes for multiple validated bugs, as well as the addition of new features. Notable merged/closed changes include:
- **Batch Bug Fixes:** PR [#4648](https://github.com/HKUDS/nanobot/pull/4648) (closed) is a monolithic fix for 13 validated issues covering authentication, outbound security, Dream memory protection, tool call parsing, and Windows shell inconsistencies.
- **MCP Stability:** PR [#4666](https://github.com/HKUDS/nanobot/pull/4666) addresses MCP crash bugs by containing malformed tool results and handling MCP timeouts and errors gracefully.
- **New Provider Support:** PR [#4632](https://github.com/HKUDS/nanobot/pull/4632) added an **Anthropic OAuth** provider, allowing Claude subscription users to use NanoBot without a console API key.
- **Security Hardening:** PR [#4669](https://github.com/HKUDS/nanobot/pull/4669) now requires an API key to start the OpenAI-compatible API server. PR [#4668](https://github.com/HKUDS/nanobot/pull/4668) enforces outbound authorization policies for the `message` tool.
- **Cross-Channel Support:** PR [#4459](https://github.com/HKUDS/nanobot/pull/4459) added a new **Mattermost** channel integration with real-time messaging and streaming responses.

### 4. Community Hot Topics
The most active discussions center on feature enhancements and requests for deeper integration, indicating a mature user base looking to optimize and extend the agent.
- **DingTalk File Integration:** Issue [#3344](https://github.com/HKUDS/nanobot/issues/3344) (5 comments) remains a pain point for users on the Chinese DingTalk platform, where file uploads and mentions are sent as separate messages, breaking file ingestion.
- **Advanced Model Usage:** Issues [#4253](https://github.com/HKUDS/nanobot/issues/4253) (5 comments) and [#4419](https://github.com/HKUDS/nanobot/issues/4419) (5 comments) show users wanting fine-grained control, specifically per-conversation model overrides and automatic reasoning effort escalation for different task complexities.
- **Plugin Ecosystem:** Issue [#2231](https://github.com/HKUDS/nanobot/issues/2231) (5 comments) is a long-standing request for a formal plugin system similar to Copilot CLI or Claude Code, suggesting a desire for community-driven extensibility.
- **Anthropic OAuth:** Issue [#4604](https://github.com/HKUDS/nanobot/issues/4604) (5 comments, now with a PR [#4632](https://github.com/HKUDS/nanobot/pull/4632)) was a highly anticipated feature that has just been implemented.

### 5. Bugs & Stability
Several significant bugs were reported and addressed today, with high responsiveness from contributors.
- **Critical: MCP Tool Crash:** Issue [#4652](https://github.com/HKUDS/nanobot/issues/4652) (2 comments) reports that the entire NanoBot process crashes when an MCP tool call returns an error or empty data. **Status:** A fix is already submitted in PR [#4666](https://github.com/HKUDS/nanobot/pull/4666) (open).
- **High: Claude Sonnet 5 API Error:** Issue [#4683](https://github.com/HKUDS/nanobot/issues/4683) (2 comments) reports a `400 invalid_request_error` because the `temperature` parameter is not omitted for the `claude-sonnet-5` model. **Status:** Fixed in PR [#4685](https://github.com/HKUDS/nanobot/pull/4685) (open).
- **High: Copilot Token Refresh Race:** PR [#4684](https://github.com/HKUDS/nanobot/pull/4684) addresses a race condition in the GitHub Copilot provider that could cause token refresh failures under concurrent requests.
- **Moderate: SSRF Bypass Risk:** PR [#4671](https://github.com/HKUDS/nanobot/pull/4671) is an important security fix that pins validated DNS for SSRF checks, preventing potential bypasses in URL handling.
- **Moderate: Telegram Long Polling Hang:** Issue [#3626](https://github.com/HKUDS/nanobot/issues/3626) describes a silent hang in the Telegram long polling, where the bot appears alive but stops receiving updates. No fix PR is yet associated.

### 6. Feature Requests & Roadmap Signals
User requests are strongly focused on improving the agent's autonomy, voice capabilities, and integration with existing ecosystems.
- **Voice Output:** Issue [#4010](https://github.com/HKUDS/nanobot/issues/4010) (3 comments, 2 👍) requests text-to-speech (TTS) support to complete the conversational loop (STT/LLM/TTS). This is a highly logical next step for a voice-enabled assistant.
- **Per-Conversation Model Override:** Issue [#4253](https://github.com/HKUDS/nanobot/issues/4253) is a strong candidate for an upcoming minor release, as it adds significant flexibility without major architectural changes.
- **Plugin System:** Issue [#2231](https://github.com/HKUDS/nanobot/issues/2231) represents a major feature that would signal a shift from a monolithic agent to a platform. This is likely on the long-term roadmap but deprioritized due to the volume of current bug fixes.
- **OpenCode Integration:** Issue [#3436](https://github.com/HKUDS/nanobot/issues/3436) and PR [#4686](https://github.com/HKUDS/nanobot/pull/4686) (adding canonical OpenCode support) suggest an interest in using external code-generation agents for complex tasks.

### 7. User Feedback Summary
The feedback from the community highlights both the power and the occasional friction of using a highly configurable agent.
- **Pain Points:** Voice interaction latency (Issue [#3257](https://github.com/HKUDS/nanobot/issues/3257)) is a significant barrier for users in real-time scenarios. Cross-platform shell inconsistencies on Windows (Issue [#4544](https://github.com/HKUDS/nanobot/issues/4544)) remain a developer-user annoyance.
- **Satisfaction Drivers:** Users are actively using and relying on the agent for complex tasks like file management, email checking (Issue [#2954](https://github.com/HKUDS/nanobot/issues/2954)), and multi-channel orchestration. The rapid response from maintainers to critical bugs (e.g., MCP crashes, Sonnet 5 errors) is a positive signal of project reliability.
- **Feature Gaps:** The request for a plugin system is a recurring theme, suggesting that while the built-in tools are powerful, some users need specific, custom capabilities that are hard to implement within the current framework.

### 8. Backlog Watch
Several important issues and PRs are languishing without clear resolution and require maintainer attention.
- **Long-Running Bug:** Issue [#2829](https://github.com/HKUDS/nanobot/issues/2829) (Ollama tool calling broken) was reported on April 5 and has 3 comments but no fix PR. This is a critical integration that is currently broken for a major local LLM provider (Ollama).
- **Stalled Feature Request:** Issue [#2231](https://github.com/HKUDS/nanobot/issues/2231) (Plugin system) has 5 comments and is from March 18. It represents a strategic feature request with no official maintainer response.
- **Important Discussion:** Issue [#3074](https://github.com/HKUDS/nanobot/issues/3074) (How to push/send a message from API to another channel) describes the `message` tool reporting success but the message not being received. While PR [#4668](https://github.com/HKUDS/nanobot/pull/4668) now addresses the security aspect of this, the original asking user may still have the functional problem.
- **RFC Awaiting Response:** Issue [#3309](https://github.com/HKUDS/nanobot/issues/3309) (Per-chat group policy overrides for Telegram) is a well-defined RFC from April 19 with a 👍 reaction, suggesting user interest, but has no update from the core team.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

# Hermes Agent Project Digest — July 3, 2026

## Today's Overview

Hermes Agent shows high activity with 50 issues and 50 PRs updated in the last 24 hours, indicating strong community engagement and active development. The project maintains a healthy balance of open (42) and recently closed (8) issues, with 26 PRs merged or closed today alone—suggesting effective triage and delivery. No new releases were published, but the volume of merged PRs points to significant codebase improvements being integrated. The community is particularly vocal about desktop stability, gateway reliability across platforms (QQBot, Telegram), and prompt injection defense false positives, signaling both user enthusiasm and friction points.

## Releases

**No new releases published today.** The last available release remains v0.18.0 (2026.7.1). However, the high number of recently merged PRs targeting bugs across components (agent, gateway, CLI, desktop) suggests a cumulative patch release may be forthcoming.

## Project Progress

**26 pull requests were merged or closed today.** Notable fixes and improvements:

- **[PR #57446] — Desktop: macOS Tahoe traffic light titlebar fix** — Closed. Fixes overlapping titlebar controls on macOS 26+. [View on GitHub](https://github.com/NousResearch/hermes-agent/pull/57446)
- **[PR #57443] — Desktop UI: Cap overlay width at 75rem** — Closed. Improves Settings/Command Center readability on ultrawide displays. [View on GitHub](https://github.com/NousResearch/hermes-agent/pull/57443)
- **[PR #24734] — OpenRouter: Thread-safe async client initialization** — Closed. Fixes TOCTOU race condition causing duplicate clients under concurrent load. [View on GitHub](https://github.com/NousResearch/hermes-agent/pull/24734)
- **[PR #25757] — Feishu: Support additional merge_forward payload shapes** — Closed. Fixes placeholder text appearing instead of forwarded messages. [View on GitHub](https://github.com/NousResearch/hermes-agent/pull/25757)
- **[PR #22746] — Models.dev: Guard float() against non-numeric cost values** — Closed. Prevents crashes from malformed API pricing data. [View on GitHub](https://github.com/NousResearch/hermes-agent/pull/22746)
- **[PR #22624] — Qwen provider: Hoist misplaced system messages** — Closed. Fixes Jinja template errors on Qwen3.5/3.6 vLLM. [View on GitHub](https://github.com/NousResearch/hermes-agent/pull/22624)
- **[PR #22618] — Cron: Drop None entries from list-form deliver values** — Closed. Prevents scheduler crashes from YAML null values. [View on GitHub](https://github.com/NousResearch/hermes-agent/pull/22618)
- **[PR #22670] — Terminal: Reject foreground sleep >30s** — Closed. Prevents agent blockage from long-running sleep commands. [View on GitHub](https://github.com/NousResearch/hermes-agent/pull/22670)
- **[PR #24558] — Holographic memory: CJK-aware entity extraction** — Closed. Fixes silent retrieval degradation for Chinese/Japanese/Korean users. [View on GitHub](https://github.com/NousResearch/hermes-agent/pull/24558)
- **[PR #22544] — Process registry: Guard against malformed checkpoint JSON** — Closed. Prevents crashes from unexpectedly-shaped recovery payloads. [View on GitHub](https://github.com/NousResearch/hermes-agent/pull/22544)

New open PRs introduced today include:
- **[PR #57449] — Installer: Quote browser env override paths** — Fixes shell-sourcing failures with spaced paths. [View on GitHub](https://github.com/NousResearch/hermes-agent/pull/57449)
- **[PR #57448] — Google Meet plugin: Migrate OpenAI Realtime to GA protocol** — Fixes broken voice after OpenAI retired beta interface. [View on GitHub](https://github.com/NousResearch/hermes-agent/pull/57448)
- **[PR #57447] — Configurable background-review prompts** — New feature for prompt override without forking. [View on GitHub](https://github.com/NousResearch/hermes-agent/pull/57447)
- **[PR #57442] — Unit tests for path traversal detection** — Test coverage for security-critical helper. [View on GitHub](https://github.com/NousResearch/hermes-agent/pull/57442)
- **[PR #57445] — Dashboard auth: Catch NotImplementedError for password-only providers** — Fixes HTTP 500 crash. [View on GitHub](https://github.com/NousResearch/hermes-agent/pull/57445)

## Community Hot Topics

**Most Active Issues (by comments and reactions):**

1. **[Issue #52914] — QQBot infinite retry loop on connect()** (12 comments, 4 👍) — The QQBot gateway crashes after updating to a recent commit, with `connect()` receiving an unexpected keyword argument `is_reconnect`. This appears to be a regression from a refactor. [View on GitHub](https://github.com/NousResearch/hermes-agent/issues/52914)

2. **[Issue #36934] — /steer flagged as prompt injection by high-resistance models** (8 comments) — Claude Opus 4.8 falsely flags legitimate operator `/steer` input as prompt injection when a tool batch is in flight. The core issue is a collision between the tool channel injection defense and the steer channel. Shows the tension between security hardening and UX. [View on GitHub](https://github.com/NousResearch/hermes-agent/issues/36934)

3. **[Issue #38602] — Desktop Client-Only Installation** (8 comments, 37 👍) — Users strongly desire a thin-client desktop mode that connects to a remote Hermes instance without bootstrapping a local runtime. With 37 upvotes, this is the most-demanded feature in the current batch. [View on GitHub](https://github.com/NousResearch/hermes-agent/issues/38602)

4. **[Issue #53449] — Telegram: Duplicate replies on short messages** (4 comments) — Non-overflow replies are duplicated when stream delivery flags are lost, with the exact match check being too strict. Gateway reliability under cache invalidation patterns is the underlying challenge. [View on GitHub](https://github.com/NousResearch/hermes-agent/issues/53449)

5. **[Issue #47368] — Desktop "Delete profile" silently fails** (4 comments) — Profile deletion is cosmetic only; the profile directory survives on disk and reappears on restart. This erodes trust in desktop UI actions. [View on GitHub](https://github.com/NousResearch/hermes-agent/issues/47368)

**Underlying needs analysis:** Users are increasingly relying on Hermes as a persistent, multi-platform agent, and friction points in gateway reliability (QQBot, Telegram), desktop UX (profile deletion, session visibility), and security feature false positives are eroding the "set and forget" experience. The strong demand for thin-client desktop mode (Issue #38602) suggests growing enterprise/team deployments where local runtime bootstrap is undesirable.

## Bugs & Stability

**New bugs reported today (July 3):**

| Severity | Issue | Description | Fix PR Exists? |
|----------|-------|-------------|----------------|
| **P2** | [#56704](https://github.com/NousResearch/hermes-agent/issues/56704) | `computer_use` crashes on Linux/WSL: `int(None)` error on pid/window_id from `list_windows` | No |
| **P2** | [#57355](https://github.com/NousResearch/hermes-agent/issues/57355) | MCP server subprocess zombies accumulate on connection retry — 11 orphan processes observed | No |
| **P2** | [#52470](https://github.com/NousResearch/hermes-agent/issues/52470) | Dashboard auto-restart silently fails because subprocess inherits `_HERMES_GATEWAY=1` | No |
| **P2** | [#57390](https://github.com/NousResearch/hermes-agent/issues/57390) | STEER_CHANNEL_NOTE causes false-positive prompt injection self-compound loop (closed as duplicate of #36934) | No (tracked via #36934) |
| **P3** | [#57381](https://github.com/NousResearch/hermes-agent/issues/57381) | `hermes-setup` crashes on Python 3.14 — `distutils.version` removed | No |
| **P3** | [#57405](https://github.com/NousResearch/hermes-agent/issues/57405) | Desktop model selector crashes: `'dict' object has no attribute 'lower'` | No |
| **P3** | [#57444](https://github.com/NousResearch/hermes-agent/issues/57444) | Desktop: `/background` completed tasks never show result panel | No |
| **P3** | [#57347](https://github.com/NousResearch/hermes-agent/issues/57347) | Honcho client is per-process singleton; timeout config ignored until restart | No |

**Previously reported active regressions with ongoing impact:**
- **P2 — [#53049](https://github.com/NousResearch/hermes-agent/issues/53049)**: Left menu keeps refreshing/reloading after update, high CPU, 10,000+ updates (3 comments, needs-repro)
- **P2 — [#49978](https://github.com/NousResearch/hermes-agent/issues/49978)**: PageUp in Desktop breaks page layout (sidebar squeezed out)

**Today's closed issues indicate fixes for:**
- [#53773](https://github.com/NousResearch/hermes-agent/issues/53773) — TUI WebSocket disconnect during long-running delegate_task (P1, closed)
- [#57390](https://github.com/NousResearch/hermes-agent/issues/57390) — STEER_CHANNEL_NOTE prompt injection loop (P2, closed as duplicate)

**Severity assessment:** The most critical unaddressed bug is the `computer_use` crash on Linux/WSL (Issue #56704), which blocks an entire platform segment. The MCP zombie accumulation (Issue #57355) indicates a systemic resource management issue. The dashboard auto-restart failure (Issue #52470) is concerning as it breaks self-healing mechanisms.

## Feature Requests & Roadmap Signals

**Top community feature requests:**

1. **[Issue #38602] — Desktop Client-Only Installation** (37 👍) — Thin-client mode for connecting to remote Hermes. **Prediction:** Likely to be prioritized for v0.19.0 given high demand and strategic value for enterprise deployments.

2. **[Issue #23944] — Generic OAuth broker credential source** (2 👍) — Shared OAuth token rotation coordination across multiple runtimes. Already has a proposal with design considerations.

3. **[Issue #32474] — /queue cancel command** (1 👍) — Ability to inspect and clear queued prompts during long turns. Simple UX improvement that addresses a common frustration.

4. **[Issue #56687] — Desktop/Web UI support for Vertex provider and Service Account JSON upload** (1 👍) — Enterprise GCP users need GUI support for the newly added `vertex` provider.

5. **[Issue #9403] — Pricing overrides, contract pricing, and sync CLI** — Enterprise cost management Phase 4. Unimplemented but codebase already supports route-aware estimation.

6. **[Issue #3630] — Secrets Phase 4: Ephemeral Secrets, External Vaults, Audit** — Advanced security for production deployments. Long-standing (March 2026) with no movement.

**Expected in next release candidate:** Configurable background-review prompts (PR #57447), Google Meet OpenAI Realtime GA migration (PR #57448), installer path quoting fix (PR #57449), and accumulated bug fixes from the 26 merged PRs today.

## User Feedback Summary

**Positive signals:** Users appreciate the GCP Vertex provider support added in v0.18.0 (Issue #56687 calls it "excellent"). The community is actively contributing PRs (15 unique contributors in today's batch), indicating strong developer engagement.

**Pain points:**

- **Desktop reliability** is a recurring theme: profile deletion that doesn't work (Issue #47368), session list that doesn't update without restart (Issue #38270), UI breakage from PageUp (Issue #49978), model selector crashes (Issue #57405), menu refresh loops (Issue #53049)
- **Gateway fragmentation issues** across platform-specific bugs: QQBot (Issue #52914), Telegram duplicates (Issue #53449), Feishu merge_forward (PR #25757)
- **Prompt injection defense UX tension**: The system's security hardening is causing false positives for legitimate operator actions (Issues #36934, #57390), frustrating power users
- **Enterprise onboarding friction**: Thin-client mode (Issue #38602) and Vertex UI support (Issue #56687) are needed for teams/GCP shops
- **Python 3.14 breakage**: `distutils.version` removal crashes setup (Issue #57381), indicating forward-compatibility gaps

**Satisfaction assessment:** Moderate. The project is shipping fixes at a good cadence, but desktop stability and gateway reliability issues are creating a perception of brittleness. The high volume of "sweeper:risk-*" tagged issues suggests the team is aware and prioritizing reliability.

## Backlog Watch

**Long-unanswered items needing maintainer attention:**

| Issue | Age | Status | Priority | Why It Matters |
|-------|-----|--------|----------|----------------|
| [#8465](https://github.com/NousResearch/hermes-agent/issues/8465) — Proper LiteLLM support | ~3 months (Apr 12) | OPEN, P2, 5 👍 | High | Breaks custom provider context size detection for many users |
| [#24782](https://github.com/NousResearch/hermes-agent/issues/24782) — Subagent fallback uses parent's base_url | ~7 weeks (May 13) | OPEN, P2 | High | Breaks fallback model routing for delegate tasks |
| [#25106](https://github.com/NousResearch/hermes-agent/issues/25106) — CLI --global model switch doesn't persist all fields | ~7 weeks (May 13) | OPEN, P2 | Medium | Model switching is incomplete—fields silently lost |
| [#3630](https://github.com/NousResearch/hermes-agent/issues/3630) — Secrets Phase 4: Ephemeral Secrets, External Vaults | ~3 months (Mar 28) | OPEN, P3 | Medium | Enterprise security feature, no movement since filing |
| [#9403](https://github.com/NousResearch/hermes-agent/issues/9403) — Pricing overrides & contract pricing CLI | ~2.5 months (Apr 14) | OPEN, P3 | Medium | Enterprise cost management Phase 4 unimplemented |
| [#13490](https://github.com/NousResearch/hermes-agent/issues/13490) — Configurable TUI status bar | ~2.5 months (Apr 21) | OPEN, P3 | Low | User customization niche but requested |
| [#33485](https://github.com/NousResearch/hermes-agent/issues/33485) — Honcho hybrid memory CPython abort on shutdown | ~5 weeks (May 27) | OPEN, P3 | Medium | Process crashes on teardown with Honcho enabled |
| [#38270](https://github.com/NousResearch/hermes-agent/issues/38270) — Desktop doesn't show live Telegram sessions | ~1 month (Jun 3) | OPEN, P3 | Medium | Desktop/Telegram integration gap |

**Most critical backlog item:** Issue [#8465](https://github.com/NousResearch/hermes-agent/issues/8465) (LiteLLM support, 3 months old, 5 👍) blocks any user relying on custom models through LiteLLM—a common deployment pattern. The subagent fallback model bug (Issue #24782, 7 weeks) is similarly blocking for multi-model agent architectures.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

# PicoClaw Project Digest — 2026-07-03

## Today's Overview
A moderate activity day with 2 new issues opened and 25 PRs updated in the last 24 hours — a high number of dependency bumps (22 out of 25 PRs) suggests a focused maintenance push by Dependabot. Notably, 14 PRs were merged or closed, with 6 of those from the "stale" category, indicating the maintainers are actively catching up on older contributions. No new releases were published today. However, two bug reports surfaced that touch config migration and Matrix reconnection reliability — both merit attention for the next patch release. Overall, the project shows solid hygiene but could benefit from a structured release cycle to address accumulating bugs.

## Releases
**None**

No new releases were published in the last 24 hours. The latest available version remains **v0.2.9** (git 2992...).

## Project Progress
**14 PRs merged or closed today** — a productive cleanup session with several meaningful fixes advancing to main:

- **#3063** (merged) — `feat: add deltachat gateway` by trufae. This is a significant new feature adding DeltaChat as a messaging channel, expanding PicoClaw's federation capabilities.
- **#3160** (stale, closed) — `fix(auth): reject cross-site launcher setup requests` by danmobot. Security hardening for the auth setup endpoint.
- **#3161** (stale, closed) — `fix(exec): keep deny patterns active for custom allow rules` by danmobot. Key security fix preventing custom allow rules from bypassing deny patterns entirely.
- **#3158** (stale, closed) — `test: cover sandbox fs Windows path handling` by danmobot. Adds regression tests for Windows path compatibility.
- **#3165** (stale, closed) — `fix(openai_compat): recover Seed XML tool calls` by Alix-007. Restores tool call extraction from Volcengine Doubao Seed XML format.
- **#3171** (stale, closed, but now reopened) — `fix(line): add ok checks for sync.Map type assertions in Send` by chengzhichao-xydt. Prevents potential panics in LINE channel Send method.

Additionally, **8 Dependabot PRs** were merged/closed for frontend and Go dependency bumps (eslint, react-i18next, shadcn, typescript-eslint, @vitejs/plugin-react, anthropic-sdk-go, golang.org/x/crypto, copilot-sdk).

## Community Hot Topics
- **Issue #3206** — [v2→v3 config migration fails with false 'unknown field(s): build_info, session.dm_scope'](https://github.com/sipeed/picoclaw/issues/3206) — **Critical user-facing bug.** This is the highest-urgency item today: a fresh install of the latest release (v0.2.9) cannot even load its own config. The migration from v2 to v3 config schema is incorrectly flagging valid fields as "unknown". Any user attempting a first run or config update after upgrading will hit a hard block. **0 comments yet** — indicates users may be hitting this silently or it's newly discovered.
- **Issue #3203** — [[BUG] Matrix sync loop has no reconnection logic — silent death after network/server disruption](https://github.com/sipeed/picoclaw/issues/3203) — **High-severity reliability issue.** The Matrix `/sync` long-poll dies permanently on network disruption. Because the main process stays alive, systemd's auto-restart doesn't help — users lose Matrix functionality silently until manual restart. **0 comments** — this is also newly filed but signals a clear architectural gap in the Matrix channel.

## Bugs & Stability
**2 new bugs reported today, ranked by severity:**

| Severity | Issue | Description |
|----------|-------|-------------|
| **CRITICAL** | [#3206](https://github.com/sipeed/picoclaw/issues/3206) | v2→v3 config migration fails — `build_info` and `session.dm_scope` incorrectly rejected as unknown fields. **Blocks all config loading** for anyone upgrading or fresh installing v0.2.9. No fix PR open yet. |
| **HIGH** | [#3203](https://github.com/sipeed/picoclaw/issues/3203) | Matrix sync loop lacks reconnection logic — silent death after any network or homeserver disruption. Affects all users of the Matrix channel. No fix PR open yet. |

**Notable fix merged today:** [#3161](https://github.com/sipeed/picoclaw/pull/3161) fixed a security edge-case where custom allow patterns could bypass deny patterns entirely — this represents a potential privilege-escalation vector that is now closed.

**Regression concern:** PR #3171 (LINE channel sync.Map type assertion fix) was marked as `[stale]`, closed, but remains **OPEN** as an active PR — the label may have been applied incorrectly. This fix is important for preventing panics in the LINE channel.

## Feature Requests & Roadmap Signals
- **DeltaChat integration (#3063)** was merged today — this is now part of the codebase. Expect DeltaChat to be a core channel option in the next release.
- **Matrix reliability (#3203)** — while filed as a bug, the requirement for automatic reconnection logic in the Matrix sync loop is effectively a missing feature. If the maintainers prioritize this, it may land in v0.3.0 alongside other channel hardening.
- **Copilot SDK bump from v0.2.0 to v1.0.5** (#3207, #3177) — the two Dependabot PRs (one merged, one pending) to upgrade the Copilot SDK to a stable v1.0.x suggest maintainers are preparing for full GitHub Copilot channel support. This is a strong roadmap signal that the Copilot integration is maturing.

## User Feedback Summary
- **New install breakage:** Issue #3206 indicates that users who `pip install picoclaw` or download v0.2.9 fresh cannot even run `picoclaw status` — the config migration crashes immediately. This is likely causing significant dissatisfaction among new adopters.
- **Silent Matrix outages:** Issue #3203 describes a "silent death" pattern — the process stays alive but Matrix stops working. Users running PicoClaw as a systemd service may not discover the failure for hours. This is a pain point for anyone relying on Matrix for production messaging.
- **No explicit positive feedback captured today**, but the high number of merged PRs (14) suggests ongoing improvement work is valued by contributors.

## Backlog Watch
- **Issue #3206 (config migration failure)** — **Filed 2026-07-02, 0 comments, no fix PR.** This is the most critical item needing immediate maintainer attention. A quick hotfix should be prioritized.
- **Issue #3203 (Matrix reconnection)** — **Filed 2026-07-02, 0 comments, no fix PR.** High-impact but likely more complex (requires redesign of the sync loop).
- **PR #3171 (LINE channel fix)** — **Status inconsistent:** marked `[stale]`, closed, but still OPEN under "open: 11". The maintainers should clarify its status and merge it if ready. The fix prevents potential panics.
- **PR #3165 (Seed XML tool calls)** — **Closed as stale** despite containing a functional fix for Volcengine Doubao Seed extraction. If this is still needed, it should be revived or superseded by a new PR.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

# NanoClaw Project Digest — 2026-07-03

## 1. Today's Overview

Project activity is **high**, with 4 open issues and 14 pull requests updated in the last 24 hours. The majority of PRs (12 of 14) remain open, indicating a busy review pipeline. Two PRs were merged or closed today: a performance improvement for container `--shm-size` and `--init` support (#2771), and the first half of the agent-templates feature (#2890). Two **High** and **Medium** severity bugs were filed against the dual-WhatsApp channel system, both with corresponding fix PRs already submitted — a strong sign of rapid maintainer response. The community is actively contributing fixes, refactors, and new feature code.

## 2. Releases

No new releases published today.

## 3. Project Progress (Merged/Closed PRs)

Two PRs were closed today:

- **[#2890 — feat(templates): local template loader, ncl --template, and docs](https://github.com/nanocoai/nanoclaw/pull/2890)** (merged)
  Agent templates part 1: a local template loader and `ncl groups create --template <ref>` to stamp agent groups from templates. Sets the foundation for the setup-wizard flow (part 2, PR #2909).

- **[#2771 — perf(container): configurable --shm-size (default 1g) + --init for agent containers](https://github.com/nanocoai/nanoclaw/pull/2771)** (merged)
  Adds `--init` and configurable `--shm-size` to `docker run` arguments. Fixes Chromium crashes in `agent-browser` due to Docker's 64MB default `/dev/shm` limit. Default set to 1GB.

## 4. Community Hot Topics

- **[Issue #2912 — WhatsApp user IDs diverge between Baileys and Cloud paths](https://github.com/nanocoai/nanoclaw/issues/2912)**
  Type: Bug, Priority: Medium. The same human gets different user IDs depending on which WhatsApp path they use (native Baileys via `/add-whatsapp` vs. Business Cloud via `/add-whatsapp-cloud`). Roles and membership do not carry across. **Underlying need**: consistent identity resolution across channel variants — operators managing both channels cannot assign privileges once.

- **[Issue #2911 — WhatsApp Cloud adapter collides with native WhatsApp in the adapter registry](https://github.com/nanocoai/nanoclaw/issues/2911)**
  Type: Bug, Priority: High. Both WhatsApp paths register under the same `whatsapp` adapter key, silently disabling one and misrouting messages. **Underlying need**: proper adapter instance-key namespacing for multi-channel deployments. A fix PR (#2913) is already open.

- **[PR #2906 — feat: instance-wide default agent provider for new groups](https://github.com/nanocoai/nanoclaw/pull/2906)**
  Adds `DEFAULT_AGENT_PROVIDER` env var (default `claude`) stamped on group creation. **Underlying need**: operators managing many groups want to set provider once globally, not per-group.

- **[PR #2909 — feat(setup): template setup flow in the wizard and first-agent stamping](https://github.com/nanocoai/nanoclaw/pull/2909)**
  Part 2 of agent templates — setup wizard gains template selection from NanoClaw Hub or local FS. **Underlying need**: reducing onboarding friction for new deployments.

## 5. Bugs & Stability

**High Priority:**

- **[Issue #2911 — WhatsApp Cloud adapter collisions](https://github.com/nanocoai/nanoclaw/issues/2911)**
  Both WhatsApp paths register under key `whatsapp`. **Fix PR #2913** already submitted (register Cloud bridge under `whatsapp-cloud`). **Doc PR #2914** follows for webhook route and migration. Active fix.

**Medium Priority:**

- **[Issue #2912 — WhatsApp user ID divergence (JID vs bare wa_id)](https://github.com/nanocoai/nanoclaw/issues/2912)**
  Baileys vs Cloud paths yield different sender handles. No dedicated fix PR yet, but the issue has 0 comments — may be addressed by broader channel identity normalization.

**Other bugfixes in flight:**

- **[PR #2823](https://github.com/nanocoai/nanoclaw/pull/2823)** — Remove `groups/global/CLAUDE.md` that host deletes on startup.
- **[PR #2824](https://github.com/nanocoai/nanoclaw/pull/2824)** — Drop stale "Global Memory" instruction from main seed prompt.
- **[PR #2910](https://github.com/nanocoai/nanoclaw/pull/2910)** — Forbid repeating `send_message` content in final message block.
- **[PR #2915](https://github.com/nanocoai/nanoclaw/pull/2915)** — Stop recurring tasks forking into duplicates on completion/retry.

## 6. Feature Requests & Roadmap Signals

**Likely in next version:**

- **Agent Templates** — PR #2890 merged, #2909 stacked on top. Templates for first-agent setup via wizard are nearly complete. Expect template hub integration soon.
- **Instance-wide default agent provider** — PR #2906. Small, non-breaking, addresses operator pain.

**Under consideration / potential next:**

- **Codex provider template support** — PR #2908 adds persona prepend and git-independent skill discovery for Codex agents. Indicates broadening provider compatibility beyond Claude.
- **Web search utility skill** — PR #2725: multi-provider web search + extraction as a `wsp` CLI tool, no MCP. Could land as a supported skill.

## 7. User Feedback Summary

- **Positive signals:** Multiple contributors actively fixing bugs (CutSnake01, glifocat, Shufel83) and building features (amit-shafnir, Koshkoshinsk). High PR volume shows engaged community.
- **Pain points identified:**
  - Dual-WhatsApp identity fragmentation (#2912, #2911) — operators running both channels face split privileges and silent misrouting.
  - Recurring task duplication (#2915) — scheduled tasks fork on retry after container timeout, requiring manual dedup.
  - Setup friction — template wizard (#2909) addresses this directly.
  - Container defaults — `--shm-size` fix (#2771) suggests Chromium crashes were a known pain point.

## 8. Backlog Watch

- **[PR #2689 — fix(signal): DM platform ID consistency, isMention, and ask_question/approval delivery](https://github.com/nanocoai/nanoclaw/pull/2689)**
  Open since **June 4** (29 days). Signal DM first messages silently dropped; DM platform IDs lack `signal:` prefix. Critical for Signal channel users. Needs review/merge — may have merge conflicts after 29 days.

- **[PR #2725 — Add web-search-plus skill](https://github.com/nanocoai/nanoclaw/pull/2725)**
  Open since **June 10** (23 days). Self-contained utility skill with vendored engine. Awaiting maintainer review — no comments or activity from maintainers.

- None of the open issues are older than 2 days, indicating the maintainer team is triaging newly filed bugs promptly. The oldest open PRs (22–29 days) are the main backlog concern.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

# IronClaw Project Digest — 2026-07-03

## Today's Overview

IronClaw is in a period of **high-intensity development**, with 50 PRs and 23 issues updated in the last 24 hours, reflecting sustained momentum toward a major Reborn platform overhaul. The project is actively merging critical infrastructure fixes (21 merged/closed PRs today) while simultaneously surfacing **systemic stability issues** in the QA environment, particularly around Slack integrations, tool execution failures, and OAuth flows. The "Reborn" architecture track continues to absorb most engineering attention, with multiple PRs addressing coverage gaps, checkpoint forwarding bugs, and credential management. Notably, **no new releases** were cut today, suggesting the team is consolidating changes before a version bump.

## Releases

**No new releases today.** The pending release PR [#5311](https://github.com/nearai/ironclaw/pull/5311) (opened 2026-06-26) remains open, which would bump `ironclaw` from 0.24.0 → 0.29.1 with breaking changes in `ironclaw_common` (0.4.2 → 0.5.0) and `ironclaw_skills` (0.3.0 → 0.4.0). This release appears blocked on the current wave of Reborn fixes.

## Project Progress

**Merged/Closed PRs today (21 total):**

- **Reborn Infrastructure:**
  - [#5573](https://github.com/nearai/ironclaw/pull/5573) — Fixed Exa MCP SSE initialize parsing (unblocks web-search functionality)
  - [#5548](https://github.com/nearai/ironclaw/pull/5548) — Added C-TRACECAP + C-ATTACH turn-event sink and attachment read-port coverage
  - [#5547](https://github.com/nearai/ironclaw/pull/5547) — PR-C2 Tier-2 coverage for skills, durable storage, and error handling
  - [#5479](https://github.com/nearai/ironclaw/issues/5479) — Fixed one-runtime group harness multi-user actor failure (closed via PR)

- **OAuth & Slack:**
  - [#5502](https://github.com/nearai/ironclaw/pull/5502) — Slack personal OAuth browser Connect flow (user-token conversion)
  - [#5501](https://github.com/nearai/ironclaw/pull/5501) — Skip leak-sanitization for OAuth token exchange responses

- **Quality/Process:**
  - [#5559](https://github.com/nearai/ironclaw/pull/5559) — Added architecture sprawl checks to pre-commit safety scripts
  - [#5530](https://github.com/nearai/ironclaw/issues/5530) — Closed: Skill auto-activation criteria unreachable (identified as dead code path)

- **Closed Bugs:**
  - [#5571](https://github.com/nearai/ironclaw/issues/5571) — Web search failure caused by Exa upstream IP throttling (fix merged via #5573)
  - [#5505](https://github.com/nearai/ironclaw/issues/5505) — Routine creation prompt self-referential bug (closed)

## Community Hot Topics

**Most Active Issues:**

1. **[#5522](https://github.com/nearai/ironclaw/issues/5522)** — Reborn routine fails when reading Slack DMs (2 comments). This issue captures a **critical UX gap**: users cannot read Slack DMs via the Reborn agent, and the system enters a retry loop on `capability_info` without meaningful error recovery. This is a high-priority QA blocker.

2. **[#5459](https://github.com/nearai/ironclaw/issues/5459)** — Configurable skills and tools (2 comments, updated today). This is a **major feature epic** driving multiple PRs (#5525, #5513). Users and admins need granular control over tool/skill installation scopes (admin-shared vs user-private). The underlying need is **multi-tenant governance** for enterprise deployments.

3. **[#5552](https://github.com/nearai/ironclaw/issues/5552)** — Generic "invalid result" after multiple tool failures (1 comment). Users are frustrated by opaque error messages that don't indicate *which* tool failed or *why*. The Activity section is silent on failure details.

**Most Active PRs:**

1. **[#5362](https://github.com/nearai/ironclaw/pull/5362)** — "Harden Slack pairing activation flows" (XL size, updated today). This long-running PR addresses Slack account pairing UX across chat, Extensions, and connectable-channel surfaces.

2. **[#5576](https://github.com/nearai/ironclaw/pull/5576)** — "Slack personal OAuth + move credentials to UI setup" (opened today, all scopes tagged). This is a **massive consolidation PR** that moves Slack credential management from environment variables to the WebUI — a direct response to the admin credential configuration pain point.

3. **[#5280](https://github.com/nearai/ironclaw/pull/5280)** — "Trace Commons: instance-wide enrollment, per-user profiles" (XL, 10 scopes, DB migration). This adds observability infrastructure for debug and compliance use cases.

## Bugs & Stability

**Critical (P0-equivalent):**

- **[#5572](https://github.com/nearai/ironclaw/issues/5572)** — `HookedLoopCheckpointPort` fails to forward `stage_checkpoint_payload`/`load_checkpoint_payload`. **Any hooks-enabled coordinator turn fails at the Checkpoint stage.** This is a **fresh architecture bug** in the Reborn hooks middleware that completely blocks hook-dependent workflows. No fix PR yet.

**High (P1):**

- [#5522](https://github.com/nearai/ironclaw/issues/5522) — Reborn Slack DM read failure + capability_info retry loop (no fix PR)
- [#5504](https://github.com/nearai/ironclaw/issues/5504) — Routine creation hangs indefinitely without result/error (no fix PR)
- [#5527](https://github.com/nearai/ironclaw/issues/5527) — Filesystem idempotency write/read scope mismatch — "early replay-before-policy is dead in production" (no fix PR)

**Medium (P2):**

- [#5552](https://github.com/nearai/ironclaw/issues/5552) — Generic "invalid result" after tool failures (no fix PR)
- [#5508](https://github.com/nearai/ironclaw/issues/5508) — Slack delivery target not found despite active connection (no fix PR)
- [#5551](https://github.com/nearai/ironclaw/issues/5551) — Automation posts intermediate progress to Slack instead of final result (no fix PR)
- [#5558](https://github.com/nearai/ironclaw/issues/5558) — Vision model hallucinates image contents, accepts false corrections (no fix PR)
- [#5509](https://github.com/nearai/ironclaw/issues/5509) — Chat creation latency scales with accumulated history (no fix PR)

**Low (P3):**
- [#5557](https://github.com/nearai/ironclaw/issues/5557) — Logs deep link double-click requirement
- [#5556](https://github.com/nearai/ironclaw/issues/5556) — Active chat highlight persists in sidebar after navigation

**Notably Fixed Today:**
- [#5571](https://github.com/nearai/ironclaw/issues/5571) — Exa IP throttling causing web search failures (fix in #5573)
- [#5505](https://github.com/nearai/ironclaw/issues/5505) — Self-referential routine creation prompts (closed)

## Feature Requests & Roadmap Signals

**Highest Signal Features:**

1. **Configurable Tools & Skills ([#5459](https://github.com/nearai/ironclaw/issues/5459))**: This is the most active feature epic, with dedicated PRs [#5525](https://github.com/nearai/ironclaw/pull/5525) (private installs) and [#5513](https://github.com/nearai/ironclaw/pull/5513) (admin UI for credentials). Expected in **v0.30.x** — this is clearly the next milestone's headline feature.

2. **Slack Personal OAuth ([#5576](https://github.com/nearai/ironclaw/pull/5576))**: Moving from manual token paste to browser OAuth is a major UX win. This PR was opened today and already has extensive scope tagging — expect it to merge within days.

3. **Stable OAuth Auth-Relay Callback ([#5570](https://github.com/nearai/ironclaw/issues/5570))**: An enhancement request to enable Google SSO testing on per-PR preview deployments. This is an **engineering enablement** issue that will unblock CI/CD for OAuth-heavy features.

4. **Onboarding/NUX Demo ([#5565](https://github.com/nearai/ironclaw/pull/5565))**: A fresh PR for a handoff-ready new user experience with intent-based URL routing, OAuth entry, and mock-backed demo. This suggests the team is investing in first-time user retention.

**Predictions for Next Release:**
- Slack OAuth consolidation (PR #5576)
- Tool/skill scope control (PRs #5525, #5513)
- Final-answer nudge for Reborn (PR #5568)
- Type/trait dedup cleanup (PR #5567) — a maintenance win
- Design system tokens + /playground (PR #5563)

## User Feedback Summary

**Pain Points:**

1. **Opaque error handling**: Multiple bugs (#5552, #5522) show users receiving generic "invalid result" or "Failed" status with no indication of which tool failed or why. The `capability_info` retry loop in #5522 is particularly damaging as it provides no escape hatch.

2. **Slack integration fragility**: Three distinct Slack bugs today — DM read failure (#5522), delivery target not found (#5508), and intermediate progress leaks (#5551). Slack is clearly the most pain-prone integration surface.

3. **UI responsiveness degradation**: Chat creation latency grows with conversation history (#5509), mobile layout breaks with horizontal overflow (#5554), and the terminal button overlaps the chat composer (#5555). These suggest frontend state management is not scaling.

4. **Notification reliability**: Approval notifications disappear instead of persisting (#5553), and Logs deep links require two clicks (#5557). Users cannot reliably track automation approval workflows.

5. **Vision model trust**: The vision hallucination bug (#5558) — where the model falsely identifies images and accepts user corrections without re-analysis — undermines confidence in multimodal features.

**Satisfaction Signals:**
- The rapid merge of Slack OAuth PRs (#5502, #5501) and the new consolidation PR (#5576) suggests the team is responsive to the credential configuration pain.
- The coverage roadmap PRs (#5547, #5548) indicate investment in test quality, which should reduce regression frequency.

## Backlog Watch

**Long-running/Stale Issues:**

1. **[#4108](https://github.com/nearai/ironclaw/issues/4108)** — Nightly E2E failed (opened 2026-05-27, last updated 2026-07-02). This is a **critical stability signal** — nightly E2E has been failing for **37 days**. No fix PR. This should be the team's top infrastructure priority.

2. **[#5048](https://github.com/nearai/ironclaw/issues/5048)** — (Not in today's data but previously reported) — Enterprise SSO configuration UI remains unaddressed.

3. **[#5311](https://github.com/nearai/ironclaw/pull/5311)** — Release PR opened 2026-06-26 (7 days ago), still not merged. This is blocking all downstream consumers from receiving fixes. The PR has breaking API changes in two core crates.

4. **[#5084](https://github.com/nearai/ironclaw/pull/5084)** — Redesign automations page (opened 2026-06-18, 15 days open). This is a major UX overhaul that hasn't been merged despite being a "new contributor" PR — may need maintainer review bandwidth.

**Risk Watch:** The file system idempotency scope bug [#5527](https://github.com/nearai/ironclaw/issues/5527) ("early replay-before-policy is dead in production") has no fix PR and touches production data consistency. If triggered, this could cause **silent data corruption** in session replay workflows. This should be escalated.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

# LobsterAI Project Digest — 2026-07-03

## 1. Today's Overview
The project shows moderate activity with 8 PRs updated in the last 24 hours, of which 7 were merged or closed — indicating a healthy development cadence focused on bug fixes and polish. All 5 open Issues remain stale (last updated 3 months ago) with no new reports, suggesting user-reported problems may be stabilizing. No new releases were published. The day's work concentrated on fixing a white-screen crash, a scheduled-task notification bug, DeepSeek prompt cache stability, and unifying the engine startup UI into a continuous splash experience.

## 2. Releases
No new releases were published today.

## 3. Project Progress
Seven pull requests were merged or closed today, covering fixes and enhancements across renderer, main, OpenClaw, and cowork areas:

- **#2259 [CLOSED]** — `chore: optimize engine failure overlay` (area: renderer, main, openclaw, cowork) — Author: fisherdaddy. Improved the overlay shown when the engine fails.
- **#2258 [CLOSED]** — `fix(openclaw): stabilize DeepSeek prompt cache in long sessions` (area: docs, openclaw) — Author: btc69m979y-dotcom. Disables aggregate tool-result rewriting on the live prompt path to keep history byte-stable for provider prefix caches, while retaining per-result size caps and existing session/overflow recovery protections. Includes a privacy-safe DeepSeek V4 cache probe for diagnostics.
- **#2257 [CLOSED]** — `feat(cowork): unify engine startup screen into one continuous splash` (area: renderer, main, cowork) — Author: fisherdaddy. Adds a static pre-React splash in index.html that mirrors `EngineStartupOverlay`, so window show, renderer init, and engine startup read as one screen instead of a spinner handoff.
- **#2255 [CLOSED]** — `Fix/scheduled task none delivery` (area: renderer) — Author: tsonglew. Fixes a bug where switching a scheduled task's notification channel to "不通知" (no notification) did not take effect because the OpenClaw gateway `cron.update` patch-merges `delivery` and cannot clear a previously set property. This fix was subsequently superseded by #2256.
- **#2254 [CLOSED]** — `chore: update main page image` (area: docs) — Author: fisherdaddy. Updated project documentation imagery.
- **#2253 [CLOSED]** — `chore: update readme` (area: docs) — Author: fisherdaddy. Updated project README.
- **#2252 [CLOSED]** — `fix(settings): prevent white screen when deleting active custom model` (area: renderer) — Author: tsonglew. Fixed an async race condition where deleting the currently selected custom provider in Settings caused a white screen; the fix switched `activeProvider` away from the deleted key before awaiting `configService.updateConfig(...)`.

## 4. Community Hot Topics
All 5 open Issues remain stale (last updated 3 months ago) with minimal comment activity, so no active community discussions are driving engagement this week. The most notable patterns:

- **#1354** "让龙虾帮忙启动pageant后电脑蓝屏" (blue screen after starting pageant) — 2 comments. A user reports a crash condition that requires further diagnosis.
- **#1357** "帮我开启pageant"回答已经启动 实际未启动" (claims started but not actually started) — 1 comment. Functional gap in task execution feedback.
- **#1358** "定时任务点击之后没有任何交互" (no interaction after clicking scheduled task) — 1 comment. UX issue with task status visibility.

**Underlying need:** These issues together suggest users want reliable, verifiable execution of local system commands (pageant startup) and clear feedback on scheduled task states — both core to the "agent-as-assistant" value proposition.

## 5. Bugs & Stability
One significant crash bug and one functional bug were actively fixed today. No new user-reported bugs emerged:

| Severity | Issue/PR | Description | Status |
|----------|----------|-------------|--------|
| **Critical** | **#2252 → #2256** | **White screen crash when deleting active custom model in Settings** — The async `confirmDeleteCustomProvider` removed a provider but delayed switching `activeProvider`, causing the view to render with an invalid key. | **Fixed** (merged) |
| **High** | **#2255 → #2256** | **Scheduled task notification "不通知" not taking effect** — Edit page showed previously selected channel; `cron.update` patch-merge couldn't clear delivery property. | **Fixed** (merged) |
| **Low** | #1354, #1357, #1358, #1359, #1360 | Stale issues (3 months old) — pageant blue screen, false positive task status, missing task interaction feedback, deleted tasks reappearing on restart, missing agent name duplicate validation. | Not yet addressed |

## 6. Feature Requests & Roadmap Signals
No explicit feature requests were logged today, but several merged PRs point to ongoing roadmap priorities:

- **Unified startup experience** (#2257) — The continuous splash screen for engine startup suggests a focus on reducing perceived startup jank and improving first-launch polish.
- **DeepSeek prompt cache stability** (#2258) — Optimizing for long-session stability with a major LLM provider (DeepSeek V4) signals deepening support for premium AI models.
- **Scheduled task reliability** (#2255, #2256, #2252) — Multiple fixes around scheduled tasks and settings persistence suggest this feature is being hardened for production use.

**Prediction for next version:** Expect scheduled-task notification channel clearing to be fully working, custom model deletion to no longer crash the UI, and the startup flow to feel more seamless across the window show → renderer init → engine ready transition.

## 7. User Feedback Summary
User pain points remain concentrated on the reliability of local system actions:

- **False positive execution feedback** — Issue #1357 ("帮我开启pageant" responds "already started" but it isn't) undermines trust in agent task completion.
- **Crash after agent action** — Issue #1354 (blue screen after pageant launch) represents a severe stability concern, though it may be environmental/system-specific.
- **Confusing task persistence** — Issue #1359 (deleted tasks reappear on restart) creates confusion about state management.
- **Missing validation** — Issue #1360 (duplicate agent names allowed) indicates a need for basic input validation in agent creation UI.

Satisfaction signals are absent from the data — no positive user comments or reactions are visible in the tracked issues.

## 8. Backlog Watch
All 5 open Issues are **stale** (last updated 2026-04-02, over 3 months ago) with zero maintainer response visible:

| Issue | ID | Age (Days) | Priority | Reason for Concern |
|-------|----|-----------|----------|--------------------|
| Blue screen after pageant launch | **#1354** | 92 | **High** | System crash — may indicate deeper driver/handling issue |
| Pageant "started" false positive | **#1357** | 92 | **High** | User trust issue — agent claims completion incorrectly |
| Scheduled task no feedback | **#1358** | 92 | **Medium** | UX gap — users cannot tell if task started |
| Deleted tasks reappear | **#1359** | 92 | **High** | State persistence bug — data not truly deleted |
| Duplicate agent name allowed | **#1360** | 92 | **Low** | Validation missing — minor UX quality |

**Recommendation:** These issues should be triaged promptly; even if not reproducible, a maintainer acknowledgment would demonstrate community responsiveness. Issues #1354 and #1359, if reproducible, represent significant reliability defects.

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyagi">TinyAGI/tinyagi</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

# Moltis Project Digest — 2026-07-03

## Today's Overview
The Moltis project is in a moderate activity state today, with no new issues or releases, but three pull requests updated in the last 24 hours. Two PRs remain open, while one was closed, indicating steady but measured progress. The project's focus is clearly on critical infrastructure work, particularly around WhatsApp integration improvements. There are no open issues at all, which suggests good stability or that bugs are being caught and resolved quickly. The overall project health appears solid, with maintainers actively reviewing and merging speculative improvements.

## Releases
No new releases were published today.

## Project Progress
One pull request was closed/merged today:
- **#1116 [CLOSED]** `fix(whatsapp): deliver replies to @lid chats via PN JID rewrite` — This fix addresses a critical bug where replies sent to privacy-enabled WhatsApp users with `@lid` chats were being silently dropped. The message would be produced by the agent and visible in the web UI, but never reached the end user and no delivery receipt was returned. The PR rewrites the JID (Jabber ID) handling to properly route replies through push notifications.

Additionally, two new open PRs were updated:
- **#1144 [OPEN]** `feat(whatsapp): bump whatsapp-rust 0.5 -> 0.6 with LID-native addressing` ([View PR](https://github.com/moltis-org/moltis/pull/1144)) — This bumps the WhatsApp library from 0.5 to 0.6, migrating to LID (Login ID) native addressing, which is a follow-up to the fix in PR #1116.
- **#1143 [OPEN]** `Add Requesty as an OpenAI-compatible provider` ([View PR](https://github.com/moltis-org/moltis/pull/1143)) — Adds Requesty as a new LLM routing provider, mirroring the existing OpenRouter integration.

## Community Hot Topics
No issues or PRs have attracted comments or reactions today, with all three PRs showing zero reactions. While there is no direct community debate, the two open WhatsApp-related PRs (#1144, #1116) and the new provider PR (#1143) represent the most technically significant ongoing discussions. The WhatsApp LID migration (#1144) is particularly important as it directly affects message deliverability for privacy-enabled WhatsApp users, which is likely a widespread pain point. Contributors and maintainers appear to be working efficiently without significant debate or friction.

## Bugs & Stability
No new bugs, crashes, or regressions were reported in the last 24 hours. The only stability signal comes from the **#1116** fix that was merged today, which resolved a critical silent message drop bug for `@lid` chats. This bug was high severity — messages were produced but never delivered, with no error feedback. The fix was relatively quick (PR opened June 12, closed July 2), indicating responsive bug handling. No other stability concerns are present in the current data.

## Feature Requests & Roadmap Signals
Today's PRs signal two clear roadmap directions:

1. **WhatsApp Reliability Enhancements** — The LID-native addressing migration (#1144) is a follow-up to the fix in #1116, suggesting a systematic effort to harden WhatsApp integration. Expect this to land in the next release as it fixes a real-world delivery failure.
2. **Expanded LLM Provider Support** — The Requesty provider addition (#1143) indicates demand for more OpenAI-compatible routing options. This mirrors the existing OpenRouter integration pattern, making it highly likely to be merged soon. Further provider additions (similar to OpenRouter/Requesty) may come in subsequent releases.

These are both technical enhancements rather than user-visible features, but they directly improve reliability and flexibility for users.

## User Feedback Summary
No explicit user feedback was captured in today's data (no issues, comments, or reactions). However, the PR #1116 fix implicitly reveals a user pain point: messages sent to WhatsApp contacts with privacy-enabled LID chats were silently failing. This would have caused significant user dissatisfaction as replies appeared successful in the web UI but never reached the recipient. The hotfix timeline (opened June 12, closed July 2) suggests this was a known and actively addressed pain point. The Requesty provider PR (#1143) also reflects a user need for more LLM provider choice, likely driven by cost, latency, or availability concerns with existing providers.

## Backlog Watch
No issues or PRs are currently languishing without maintainer attention. All open PRs (#1143, #1144) were updated within the last 24 hours, indicating active review. The only closed PR (#1116) was recently merged and up to date. The backlog is effectively clear, with zero open issues and a small queue of well-maintained pull requests.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

# CoPaw Project Digest — 2026-07-03

## Today's Overview

CoPaw is in an intensive development phase with **v2.0.0-beta.2** just released, showing **high activity**: 23 issues updated and **50 PRs** updated in the last 24 hours, with an exceptional **27 merged/closed**. The project is balancing **pre-release stabilization** (v2.0.0 beta bug tracking) with **security hardening** (secret redaction, env var config) and **quality-of-life improvements** (CLI enhancement, text selection). A notable influx of **first-time contributors** (6 PRs from new contributors today) signals growing community engagement. However, **v2.0.0-beta.2** carries a clear instability warning and the pre-release issue tracker (#5273) remains open with active reports.

## Releases

**v2.0.0-beta.2** was released today (⚠️ early beta, breaking changes possible, not for production). This is the second beta for QwenPaw 2.0. Changelog primarily shows `feat(cli): add cron up` — CLI cron functionality is being introduced.

Users on v1.1.x series should **not** upgrade to v2.0.0-beta.2 for production use. Migration from v1.x to v2.0.0 beta is not advised at this stage.

## Project Progress

**27 PRs merged/closed** in the last 24 hours, including:

- **Security / Config**: [#5745](https://github.com/agentscope-ai/CoPaw/pull/5745) — Secret redaction in dialog artifacts; [#5740](https://github.com/agentscope-ai/CoPaw/pull/5740) — Env var references in JSON config; [#5738](https://github.com/agentscope-ai/CoPaw/pull/5738) — Multi-dimensional rate limiting (account/IP); [#5741](https://github.com/agentscope-ai/CoPaw/pull/5741) — Env var resolution + dialog log sanitization
- **Bug fixes**: [#5287](https://github.com/agentscope-ai/CoPaw/pull/5287) — Context compaction crash fix; [#5533](https://github.com/agentscope-ai/CoPaw/pull/5533) — Content safety error misclassification fix; [#5514](https://github.com/agentscope-ai/CoPaw/pull/5514) — Chat input queue session ID migration; [#5743](https://github.com/agentscope-ai/CoPaw/pull/5743) — CI bash 3.2 compatibility fix
- **UI/UX**: [#5620](https://github.com/agentscope-ai/CoPaw/pull/5620) — Agents page table readability improvements; [#5744](https://github.com/agentscope-ai/CoPaw/pull/5744) — Mobile chat history panel fix; [#5742](https://github.com/agentscope-ai/CoPaw/pull/5742) — Stream completion time display fix

**Notable open PRs** (under review/active):
- [#5597](https://github.com/agentscope-ai/CoPaw/pull/5597) — Per-agent and global LLM model fallback with safe retry boundaries
- [#5726](https://github.com/agentscope-ai/CoPaw/pull/5726) — Vision fallback for text-only models (implements #5615)
- [#5692](https://github.com/agentscope-ai/CoPaw/pull/5692) — Reranker for memory search results (reme0.4)

## Community Hot Topics

| Issue | Comments | Topic |
|-------|----------|-------|
| [#5630](https://github.com/agentscope-ai/CoPaw/issues/5630) | 8 | Custom Telegram BaseURL support |
| [#5403](https://github.com/agentscope-ai/CoPaw/issues/5403) | 7 | Browser autofill hijacking search input |
| [#5705](https://github.com/agentscope-ai/CoPaw/issues/5705) | 6 | Secret key security improvements (env var + log sanitization) |

**Analysis**: Security and configuration management are the dominant community concerns. Users are requesting more flexible deployment options (custom BaseURL), better secret handling, and UX polish. The [#5705](https://github.com/agentscope-ai/CoPaw/issues/5705) discussion has already generated **two parallel PRs** (#5740, #5741) from different contributors, showing strong community alignment on the need for env-var-based config.

## Bugs & Stability

**Critical bugs reported today (all with open PRs or active investigation):**

| Issue | Severity | Description | Fix Status |
|-------|----------|-------------|------------|
| [#5748](https://github.com/agentscope-ai/CoPaw/issues/5748) | **High** | Agent hangs indefinitely on tool call failure; typing indicator spins forever | PR [#5749](https://github.com/agentscope-ai/CoPaw/pull/5749) open |
| [#5746](https://github.com/agentscope-ai/CoPaw/issues/5746) | **High** | v2.0.0b2 scroll context compression folds active task, loses context mid-conversation | PR [#5747](https://github.com/agentscope-ai/CoPaw/pull/5747) open |
| [#5717](https://github.com/agentscope-ai/CoPaw/issues/5717) | **High** | Runtime 2.0 malformed tool-call history causes endless repeated tool execution | No PR yet |
| [#5720](https://github.com/agentscope-ai/CoPaw/issues/5720) | **High** | v1.1.12.post2 memory leak (150MB → 580MB in ~64 min) | No PR yet |
| [#5708](https://github.com/agentscope-ai/CoPaw/issues/5708) | **Medium** | Feishu interactive card messages not parsed | No PR yet |
| [#5710](https://github.com/agentscope-ai/CoPaw/issues/5710) | **Medium** | Context compression lacks anchor protection for critical messages | No PR yet |
| [#5725](https://github.com/agentscope-ai/CoPaw/issues/5725) | **Medium** | Console streaming causes browser lag (user reports DeepSeek doesn't have this issue) | No PR yet |
| [#5709](https://github.com/agentscope-ai/CoPaw/issues/5709) | **Medium** | Feishu channel incorrectly drops bot messages (multi-agent collaboration broken) | Closed (likely fixed) |
| [#5721](https://github.com/agentscope-ai/CoPaw/issues/5721) | **Medium** | Feishu group chats lose per-message sender identity in shared sessions | No PR yet |

**Regression alert**: The v2.0.0b2 scroll context bug (#5746) and the v1.1.12.post2 memory leak (#5720) both come from **stable releases**, suggesting quality issues in both tracks. The v2.0.0 beta pre-release tracker ([#5273](https://github.com/agentscope-ai/CoPaw/issues/5273)) remains the primary collection point for beta regressions.

## Feature Requests & Roadmap Signals

**High-priority / likely next-version features:**

- **Model auto-fallback**: [#5718](https://github.com/agentscope-ai/CoPaw/issues/5718) — Auto-switch model on quota/error (PR [#5597](https://github.com/agentscope-ai/CoPaw/pull/5597) already open)
- **Enhanced CLI**: [#5737](https://github.com/agentscope-ai/CoPaw/issues/5737) — CLI capabilities for non-GUI operation (pre-install skills, headless mode) — aligns with v2.0.0 beta CLI work
- **Vision fallback**: [#5615](https://github.com/agentscope-ai/CoPaw/issues/5615) related — PR [#5726](https://github.com/agentscope-ai/CoPaw/pull/5726) is implementation
- **Text selection in chat**: [#5712](https://github.com/agentscope-ai/CoPaw/issues/5712) — PR [#5739](https://github.com/agentscope-ai/CoPaw/pull/5739) implements this
- **Reranker for memory search**: PR [#5692](https://github.com/agentscope-ai/CoPaw/pull/5692) — likely for v2.0.0 or v2.1.0

**Prediction**: The model fallback feature (#5718/#5597) and CLI enhancement (#5737) are the strongest roadmap signals. Both align with the v2.0.0 "cron" and automation theme. The security improvements (#5705 → multiple PRs) will almost certainly land in the next stable release.

## User Feedback Summary

**Pain points (explicit and implicit):**

1. **Security & configuration friction**: Users deploying in restricted environments (containers, no GUI) need CLI/config-driven operations (#5737, #5705). The "tool approval still shows after disabling" bug (#5703) erodes trust in configuration controls.

2. **Multi-platform inconsistencies**: Feishu users face the most integration issues — card parsing (#5708), bot message filtering (#5709), sender identity loss (#5721). This suggests Feishu channel needs dedicated QA attention.

3. **Performance regressions**: The browser streaming lag (#5725) directly compared to DeepSeek's smooth experience reflects poorly on QwenPaw's frontend performance. Users are benchmarking against competitors.

4. **Memory bloat**: 37GB ChromaDB index (#4795, closed) and the new memory leak (#5720, open) indicate persistent memory management problems that erode trust for long-running deployments.

5. **Context management reliability**: Both scroll mode (#5746) and general context compression (#5710) show system-level AI context management is not yet robust enough for complex multi-step workflows.

**Satisfaction signals**: High volume of first-time contributors (6 today) suggests good onboarding and documentation quality. The Telegram BaseURL request (#5630) indicates users are successfully deploying in non-standard environments.

## Backlog Watch

**Issues needing maintainer attention:**

| Issue | Age | Severity | Reason |
|-------|-----|----------|--------|
| [#5720](https://github.com/agentscope-ai/CoPaw/issues/5720) | 1 day | **High** | v1.1.12.post2 memory leak, detailed root cause analysis provided by reporter — no maintainer response yet |
| [#5717](https://github.com/agentscope-ai/CoPaw/issues/5717) | 1 day | **High** | Runtime 2.0 tool-call loop — critical for v2.0.0-beta stability, no PR |
| [#5708](https://github.com/agentscope-ai/CoPaw/issues/5708) | 2 days | **Medium** | Feishu card parsing — user reported originally on 2026-06-13, resubmitted 2026-07-01 with no resolution |
| [#5725](https://github.com/agentscope-ai/CoPaw/issues/5725) | 1 day | **Medium** | Streaming performance regression — user provides clear comparison with DeepSeek; needs UX/performance team triage |
| [#5721](https://github.com/agentscope-ai/CoPaw/issues/5721) | 1 day | **Medium** | Feishu multi-agent collaboration broken (sender identity loss) — critical for enterprise use cases |

**PRs needing review:**
- [#5747](https://github.com/agentscope-ai/CoPaw/pull/5747) — Scroll context protection PR (fix for #5746 critical bug)
- [#5749](https://github.com/agentscope-ai/CoPaw/pull/5749) — Consumer timeout + typing auto-stop (fix for #5748)
- [#5597](https://github.com/agentscope-ai/CoPaw/pull/5597) — Model fallback (landmark feature, open since 2026-06-29)

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

# ZeroClaw Project Digest — 2026-07-03

## Today's Overview
ZeroClaw remains in a period of high development activity with 37 issues updated and 50 PRs updated in the last 24 hours, indicating a healthy, actively maintained project. The project recently merged 19 PRs and closed 4 issues, suggesting steady progress toward resolving open concerns. No new releases were published today, but several high-priority bugs and significant feature PRs (including a large memory subsystem overhaul and a Git forge channel) are actively under review. The project's v0.9.0 tracker (#7432) continues to coordinate auth, security, and breaking-change work, while the v0.8.3 tracker (#8073) focuses on observability, CI, and docs. Overall project health is strong, though several critical S1 bugs remain open, and the v0.8.x release cycle appears to be building toward a substantial v0.9.0 milestone.

## Releases
**No new releases today.** The latest release remains at v0.8.x (exact version not specified in data). Several release-tracker milestones are active:
- Tracker #8073 coordinates v0.8.3 work (observability, CI, docs, dependencies, install)
- Tracker #7432 coordinates v0.9.0 work (auth, security, gateway, breaking changes)

## Project Progress
**Merged/closed PRs today: 19** (from 50 total updated PRs). Notable recent closures and progress:

### Recently Merged/Closed Items
- **PR #8305** *(closed)* — fix(gateway-web): surface MCP servers in tools dashboard via API response. Fixes issue #8302 where configured MCP servers were invisible in the web dashboard.
- **Issue #8424** *(closed)* — RFC: `.ignore` file mechanism for workspace file protection. Closed after discussion; suggests maintainer feedback was incorporated.
- **Issue #4467** *(closed)* — RFC to add MCP resource and prompt support. Closed after implementation work.

### Key PRs Currently Open (indicates active development areas)
- **PR #8570** *(size:XL, risk:high)* — `feat(memory)`: epic A durable store seam — a major memory subsystem overhaul adding supersede, dedup, budget, and policy-gate features. This is the foundation for persistent memory in ZeroClaw.
- **PR #8609** *(size:XL, risk:high)* — First of a stacked 3-PR series adding Git forge channel (GitHub provider) with SOP ingress — significant new integration capability.
- **PR #8611** *(size:XL, risk:high)* — Second stacked PR, adding Gitea/Forgejo support for the Git channel.
- **PR #8618** *(docs)* — Third stacked PR, adding Git channel + SOP fan-in documentation pages.
- **PR #8619** *(size:L, risk:medium)* — Unified memory-context injection keyed on TurnOrigin ingress provenance — adds provenance tracking to turn handling.
- **PR #8567** *(size:L, risk:high)* — Runtime OTel content policy for LLM and tool I/O.
- **PR #8547** *(size:L, risk:high)* — Removes `rag-pdf` feature to clear RUSTSEC-2026-0192 (ttf-parser vulnerability).
- **PR #8463** *(size:S, risk:high)* — Caps interactive CLI stdin lines to 1 MiB (prevents unbounded memory allocation).
- **PR #8335** *(size:M, risk:high)* — Makes skills install/list/remove bundle-aware — critical fix for multi-agent skill management.

## Community Hot Topics

### Most Active Issues
1. **[#8193](https://github.com/zeroclaw-labs/zeroclaw/issues/8193)** — *(14 comments)* — **S1 Bug: MCP tools/tool_search missing from TUI sessions while gateway sees them.** This is the most active issue. Two users report MCP servers expose tools to the gateway but not to Zerocode TUI sessions. The root cause is actively being investigated. This is a workflow-blocking bug for MCP users.
2. **[#6808](https://github.com/zeroclaw-labs/zeroclaw/issues/6808)** — *(13 comments)* — **RFC: Work Lanes, Board Automation, and Label Cleanup.** Governance/process RFC with broad community engagement. Accepted and in rollout. Shows community interest in project management improvements.
3. **[#7462](https://github.com/zeroclaw-labs/zeroclaw/issues/7462)** — *(7 comments)* — **74 test failures on Windows.** Windows compatibility is a recurring pain point. PR #8604 (Windows CRT static linking) directly addresses related build issues.
4. **[#5542](https://github.com/zeroclaw-labs/zeroclaw/issues/5542)** — *(6 comments)* — **Consecutive OOM in WSL2.** Long-standing S0 severity bug (data loss / security risk) last updated today. Requires reproduction steps. Indicates memory management concerns in the daemon.
5. **[#8226](https://github.com/zeroclaw-labs/zeroclaw/issues/8226)** — *(5 comments)* — **Per-agent custom environment variables.** Community-requested feature for identity/parameter/token multi-tenancy. Blocked but actively discussed.
6. **[#6302](https://github.com/zeroclaw-labs/zeroclaw/issues/6302)** — *(5 comments)* — **Gemini 400 error — history serializer invariant violation.** High-risk bug affecting Gemini users via LiteLLM.

### Analysis of Underlying Community Needs
The community is actively engaged around three major themes: (1) MCP tool visibility/consistency across interfaces (TUI vs. web vs. gateway), (2) multi-tenancy and per-agent configuration (secrets, env vars, model selection), and (3) Windows/Linux cross-platform stability. The high activity on governance RFCs suggests a maturing project seeking better contribution processes.

## Bugs & Stability

### Active S1/S0 Critical Bugs (Ranked by Severity)

| Issue | Severity | Component | Summary | Fix PR? |
|-------|----------|-----------|---------|---------|
| [#5542](https://github.com/zeroclaw-labs/zeroclaw/issues/5542) | **S0** — data loss/security risk | runtime/daemon | Consecutive OOM in WSL2 | No |
| [#8193](https://github.com/zeroclaw-labs/zeroclaw/issues/8193) | **S1** — workflow blocked | zerocode/tui, tools, runtime, gateway | MCP tools missing from TUI sessions while gateway sees them | No (investigating) |
| [#8632](https://github.com/zeroclaw-labs/zeroclaw/issues/8632) | **S1** — workflow blocked | tooling/ci | Source install with embedded-web fails before generated web API client exists | No |
| [#8627](https://github.com/zeroclaw-labs/zeroclaw/issues/8627) | **S1** — workflow blocked | channel | WhatsApp Web device linking broken by new passkey/SHORTCAKE gate | No |
| [#8044](https://github.com/zeroclaw-labs/zeroclaw/issues/8044) | **P1** — high priority | gateway/security | Model override scope lacks per-sender authorization | No |
| [#7462](https://github.com/zeroclaw-labs/zeroclaw/issues/7462) | **S2** — degraded | tooling/ci | 74 test failures on Windows | PR #8604 (build fix) |
| [#8302](https://github.com/zeroclaw-labs/zeroclaw/issues/8302) | **S2** — degraded | web dashboard | MCP tools not shown in tools list | **PR #8305 closed/fixed** |
| [#8334](https://github.com/zeroclaw-labs/zeroclaw/issues/8334) | **S2** — degraded | skills/CLI | Skills install/list/remove target wrong directory | **PR #8335 open** |
| [#8631](https://github.com/zeroclaw-labs/zeroclaw/issues/8631) | **S2** — degraded | runtime/daemon (SOP engine) | Headless SOP steps recorded Completed without executing | No |
| [#8615](https://github.com/zeroclaw-labs/zeroclaw/issues/8615) | **S2** — degraded | provider | Compatible provider silently deletes content via unconditional `<think>` tag stripping | No |

### Notable Stability Observations
- The **Windows compatibility issue** (#7462) with 74 test failures is partially addressed by PR #8604 (static linking MSVC CRT), but the root cause of Unix-specific test commands and path semantics remains.
- **Security hardening** is active: PR #8574 adds regression tests for zip bomb inflation guards; PR #8463 caps stdin lines at 1 MiB; PR #8547 removes a `ttf-parser` vulnerability.
- The **WhatsApp Web channel** (#8627) is broken by upstream WhatsApp changes — indicates external service dependency risk.

## Feature Requests & Roadmap Signals

### High-Interest Community Feature Requests
1. **[#8226](https://github.com/zeroclaw-labs/zeroclaw/issues/8226)** — Per-agent custom environment variables (blocked, high risk)
2. **[#8550](https://github.com/zeroclaw-labs/zeroclaw/issues/8550)** — OpenAI-compatible chat completions endpoint (blocked, high risk) — **likely for v0.9.0** given RFC #8603 is also filed
3. **[#8600](https://github.com/zeroclaw-labs/zeroclaw/issues/8600)** — Easy per-chat model switching for multi-model providers (needs maintainer review)
4. **[#8602](https://github.com/zeroclaw-labs/zeroclaw/issues/8602)** — Enhanced `file_read` (line cap, charset detection, paged PDF, notebook awareness)
5. **[#7065](https://github.com/zeroclaw-labs/zeroclaw/issues/7065)** — Agent evaluation harness (`zeroclaw eval`) — replay + live modes
6. **[#6416](https://github.com/zeroclaw-labs/zeroclaw/issues/6416)** — Validate config.toml at quickstart for provider/settings incompatibilities

### Predictions for Next Version (v0.9.0 / near-term)
Based on active PRs and RFCs:
- **OpenAI-compatible endpoint** (issues #8550, #8603) — strong signals from two related issues; likely major v0.9.0 feature
- **Memory durable store** (PR #8570) — large PR under review; likely to land
- **Git forge channels** (PRs #8609, #8611, #8618) — stacked PRs under active development
- **Unified memory-context injection** (PR #8619) — provenance tracking for turn handling
- **Per-agent env variables** (#8226) — blocked but in tracker
- **OTel content policy** (PR #8567) — observability improvement

## User Feedback Summary

### Real User Pain Points
1. **MCP visibility inconsistency** (#8193, #8302): "configured mcp servers tools are not shown in the tools screen even though the agent can clearly sees them" — users confused when tools appear in some interfaces but not others.
2. **Windows compatibility** (#7462, #8604): User reports 74 test failures on Windows 11 (Simplified Chinese, code page 936). The project's Linux-only CI means Windows regressions go undetected.
3. **Multi-agent skill management** (#8334): "headline 'pull a skill and use it' flow is broken on multi-agent installs" — the core value proposition is degraded for multi-agent deployments.
4. **Content deletion** (#8615): "users invisibly lose response content" — the compatible provider's `<think>` tag stripping silently deletes content, breaking user trust.
5. **Model selection friction** (#8600): User coming from Moltis wants per-chat model switching with "the full set of models available from that provider."

### Satisfaction Signals
- **Feature parity requests** coming from users migrating from other tools (Moltis) — indicates ZeroClaw is attracting new users from competing projects.
- **RFC engagement** on governance (#6808) shows a community invested in project direction.
- **Multiple PR review chains** (especially the 3-PR stacked Git channel series) indicate maintainers are responsive and breaking large changes into reviewable pieces.

## Backlog Watch

### Issues Needing Maintainer Attention
| Issue | Days Open | Risk | Reason for Concern |
|-------|-----------|------|-------------------|
| [#5542](https://github.com/zeroclaw-labs/zeroclaw/issues/5542) | 85 days | **S0** — high | Consecutive OOM in WSL2 — needs reproduction steps (r:needs-repro label) |
| [#6302](https://github.com/zeroclaw-labs/zeroclaw/issues/6302) | 61 days | **P1** — high | Gemini 400 error in history serializer — affects users |
| [#7952](https://github.com/zeroclaw-labs/zeroclaw/issues/7952) | 14 days | **Blocked** — high | Publish full-channel prebuilt assets — needs maintainer review |
| [#6250](https://github.com/zeroclaw-labs/zeroclaw/issues/6250) | 62 days | **P1** — high | Route-layer auth middleware — follow-up issue, no-stale |
| [#8396](https://github.com/zeroclaw-labs/zeroclaw/issues/8396) | 6 days | **Blocked** — high | Wire-protocol-first provider model RFC — needs maintainer review |
| [#8600](https://github.com/zeroclaw-labs/zeroclaw/issues/8600) | 2 days | **Needs review** — high | Per-chat model switching — just filed, needs response |
| [#8602](https://github.com/zeroclaw-labs/zeroclaw/issues/8602) | 1 day | **Needs review** — high | Enhanced file_read — just filed, needs response |
| [#8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603) | 1 day | **Needs review** — high | OpenAI compatibility adapter RFC — just filed |

### PRs Needing Maintainer Attention
| PR | Days Open | Risk | Notes |
|----|-----------|------|-------|
| [#7946](https://github.com/zeroclaw-labs/zeroclaw/pull/7946) | 15 days | **High** | Context window ctx bar — needs-author-action label; may be stalled |
| [#8570](https://github.com/zeroclaw-labs/zeroclaw/pull/8570) | 2 days | **High** (XL size) | Memory durable store epic — large PR needs thorough review |
| [#8609](https://github.com/zeroclaw-labs/zeroclaw/pull/8609) | 1 day | **High** (XL size) | Git forge channel (GitHub) — first of stacked series |

*Generated from zeroclaw-labs/zeroclaw issue and PR data as of 2026-07-03.*

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*