# OpenClaw Ecosystem Digest 2026-07-11

> Issues: 429 | PRs: 500 | Projects covered: 13 | Generated: 2026-07-11 01:47 UTC

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

# OpenClaw Project Digest — 2026-07-11

## Today's Overview

The OpenClaw project shows **very high activity** today, with 429 issues and 500 PRs updated in the last 24 hours. Activity is concentrated on stability fixes (memory leaks, session state corruption, Discord reconnection) and security hardening (cross-plugin session access, exec approval race conditions). **193 issues and 192 PRs were closed/merged**, indicating strong velocity on bug fixes. No new releases were published. The Most impactful PRs target platform-level stability (macOS onboarding, Discord message loss, Anthropic thinking signature corruption) and a major Codex expansion that brings native session supervision to the fleet management layer.

## Releases

No new releases were published in the last 24 hours.

## Project Progress

The following high-impact PRs were **merged or closed** today, representing significant progress:

1. **Anthropic Extended Thinking Fix** (PR [#104043](https://github.com/openclaw/openclaw/pull/104043)) — Closes #103830. Fixes corrupted cryptographic signatures when an Anthropic extended-thinking stream is interrupted mid-turn. Any session replaying a truncated signature would previously brick permanently.

2. **Codex Native Session Supervision** (PR [#104045](https://github.com/openclaw/openclaw/pull/104045)) — Closes #103235. Codex sessions discovered on local/paired Macs are now writable: users can open, continue, and archive sessions. The separate Codex Supervisor plugin design is now integrated.

3. **UTF-16 Safety Fixes** (PRs [#104046](https://github.com/openclaw/openclaw/pull/104046), [#104047](https://github.com/openclaw/openclaw/pull/104047)) — Fixes surrogate-pair truncation in Active Memory search and Skill Workshop previews. Non-BMP characters (emoji) no longer produce broken text.

4. **Portable Table Presentation** (PR [#103583](https://github.com/openclaw/openclaw/pull/103583)) — Closes long-standing feature request #12602. Adds structured tabular output support for agents across Discord, Signal, Slack, Telegram, Feishu, and CLI.

5. **SSE Payload Size Cap** (PR [#101274](https://github.com/openclaw/openclaw/pull/101274)) — Caps JSON.parse at 16 MiB for Tlon SSE streams, preventing OOM crashes from malicious Urbit ship data.

6. **Control UI Login Flash Fix** (PR [#104042](https://github.com/openclaw/openclaw/pull/104042)) — Closes #103342. Token-authenticated sessions no longer flash the login gate on refresh.

## Community Hot Topics

1. **#99241 — Tool Outputs Rendered as Image Attachments** (🔗 [Issue](https://github.com/openclaw/openclaw/issues/99241))
   - 20 comments, 2 upvotes. When ANSI-heavy tool output exceeds rendering thresholds, results collapse to `(see attached image)` placeholders. **Agents cannot read their own tool output**, breaking long-running workflows. Tagged P1, platinum hermit severity.

2. **#102175 — Embedded Prompt Cache Breaks Across Boundaries** (🔗 [Issue](https://github.com/openclaw/openclaw/issues/102175))
   - 16 comments, 1 upvote. Regression where prompt-cache continuity is lost when sessions cross `room_event` turns, policy changes, memory compaction, or native Responses API boundaries. Affects long-lived embedded sessions.

3. **#10659 — Masked Secrets for API Keys** (🔗 [Issue](https://github.com/openclaw/openclaw/issues/10659))
   - 15 comments, 4 upvotes. Agents need to *use* API keys without *seeing* them. Current `.env` storage is fully readable by the LLM, enabling credential exfiltration via prompt injection.

4. **#91588 — Gateway Memory Leak (350MB → 15.5GB)** (🔗 [Issue](https://github.com/openclaw/openclaw/issues/91588))
   - 15 comments, 1 upvote. P0 critical: RSS grows to 15.5 GB over 2–3 days, forcing repeated OOM kills and `launchd-handoff` restart cycles. Gateway process is completely unstable under sustained load.

5. **#63829 — Per-Agent Memory-Wiki Vault Configuration** (🔗 [Issue](https://github.com/openclaw/openclaw/issues/63829))
   - 13 comments, 10 upvotes (highest reaction count). Multi-agent setups need isolated knowledge wikis instead of a single global vault. Strong community demand despite being closed — likely re-filed.

6. **#11665 — Webhook Sessions Don't Reuse Existing Sessions** (🔗 [Issue](https://github.com/openclaw/openclaw/issues/11665))
   - 11 comments. `sessionKey` parameter is documented but non-functional — `resolveCronSession()` always generates a new session. Multi-turn webhook conversations are impossible.

## Bugs & Stability

### P0 / Critical
- **Gateway Memory Leak** (#91588) — RSS grows from 350 MB to 15.5 GB over 2–3 days, then OOM-killed. **No fix PR yet**. This is the most severe stability issue in the repo.
- **Hosted Molty Model Selector Corruption** (#101763) — API receives `claude-opus-4.8` (dotted) instead of valid `claude-opus-4-8` (dashed). Every agent reply fails on Anthropic API. **No fix PR yet**.

### P1 / High
- **Prompt Cache Breaks Across Boundaries** (#102175) — Regression affecting embedded sessions. Long-lived sessions lose continuity on every ambient change.
- **WhatsApp Session Stalls on Long Model Calls** (#84569) — Sessions stall with incomplete turn (`payloads=0`), reply never delivered. **Has linked PR open** (#84569 → PR pending).
- **Codex App-Server Startup Exhaustion** (#83959) — Retries can exhaust before replacement server is ready, causing crash loops. **Has linked PR open**.
- **MacOS Onboarding Window Sizing** (PR [#99135](https://github.com/openclaw/openclaw/pull/99135)) — Window extends below screen on short displays, hiding navigation.

### P2 / Medium
- **Session pruneAfter Setting Ignored** (#103956) — Sessions grow unbounded regardless of configured pruning. **Fix PR exists** ([#104039](https://github.com/openclaw/openclaw/pull/104039)).
- **ACP Session Startup Failure** (PR [#103958](https://github.com/openclaw/openclaw/pull/103958)) — Fails when backend doesn't advertise thinking config (ACP_BACKEND_UNSUPPORTED_CONTROL).
- **Slack Bulk Action False Positives** (PR [#103445](https://github.com/openclaw/openclaw/pull/103445)) — `isBulkActionsBlock()` matches `_all_` substring anywhere, causing misclassification.
- **Runtime Config Activation Race** (PR [#103801](https://github.com/openclaw/openclaw/pull/103801)) — Hook/cron/channel changes left in mixed state for up to 5 minutes.

### Security
- **Cross-Plugin Session Mutation** (PR [#103534](https://github.com/openclaw/openclaw/pull/103534)) — One plugin's runtime could archive/delete sessions owned by a different plugin via `sessions.patch`.
- **External Content Pattern Scan Unbounded** (PR [#104038](https://github.com/openclaw/openclaw/pull/104038)) — Superlinear injection-monitoring patterns run against full uncapped body of untrusted hook content.
- **Deny-Over-Allow Exec Approval** (PR [#101276](https://github.com/openclaw/openclaw/pull/101276)) — Adds deny-list support to override allow-list approvals (feature + security fix).

## Feature Requests & Roadmap Signals

| Feature | Issue | Votes | Likely Next Version |
|---|---|---|---|
| **Masked Secrets** (API keys hidden from LLM) | [#10659](https://github.com/openclaw/openclaw/issues/10659) | 4 👍 | **High** — P1, strong security case |
| **Per-Agent Memory-Wiki Vaults** | [#63829](https://github.com/openclaw/openclaw/issues/63829) | 10 👍 | **High** — most upvoted, closed but likely re-filed |
| **Slack Block Kit Support** | [#12602](https://github.com/openclaw/openclaw/issues/12602) | 0 👍 | **Delivered today** in PR #103583 |
| **Webhook Multi-Turn Support** | [#11665](https://github.com/openclaw/openclaw/issues/11665) | 0 👍 | **Medium** — documented but broken, PR needed |
| **Filesystem Sandboxing Config** | [#7722](https://github.com/openclaw/openclaw/issues/7722) | 4 👍 | **Medium** — security feature, P2 |
| **Batch API Support (50% discount)** | [#9865](https://github.com/openclaw/openclaw/issues/9865) | 0 👍 | **Low** — non-urgent cost optimization |
| **Max Turns / Tool Calls Limit** | [#9912](https://github.com/openclaw/openclaw/issues/9912) | 1 👍 | **Medium** — addresses LLM compliance issues |
| **Sub-Agent Multi-Lane Concurrency** | [#10467](https://github.com/openclaw/openclaw/issues/10467) | 0 👍 | **Low** — advanced workflow orchestration |
| **Session End Hook Event** | [#10142](https://github.com/openclaw/openclaw/issues/10142) | 0 👍 | **Medium** — requested for Temporal integration |
| **Configurable Ack Reaction Emojis** | [#8508](https://github.com/openclaw/openclaw/issues/8508) | 6 👍 | **Medium** — high demand for contextual UX |
| **Group Chat Consolidation (`groupScope`)** | [#7524](https://github.com/openclaw/openclaw/issues/7524) | 4 👍 | **Medium** — DM equivalent is already supported |

## User Feedback Summary

**Pain Points with High Emotional Weight:**
- **Memory leaks ruin production deployments** (P0, #91588). Users report "repeated `launchd-handoff` restart cycles" — the gateway is effectively non-deployable for long-running servers.
- **Prompt cache breaks kill continuity** (#102175). Long-lived sessions lose context abruptly — described as "losing the plot" mid-task.
- **Agent-blind tool output** (#99241). The agent can't read its own `stderr`/`stdout`, which is often "the evidence needed" for decision-making. This is a fundamental trust issue.
- **Cross-plugin security gaps** (#103534). Users are uncomfortable that one plugin can silently archive another plugin's sessions — "last-write-wins race condition" language signals deep concern.
- **Session pruning is broken by design** (#103956). Even when users explicitly configure pruning, sessions grow unbounded — a configuration trust failure.

**Satisfaction Signals:**
- Strong community engagement: 429 issues in 24 hours, 500 PRs, 192 closed/merged
- High-velocity fix cycle: 4 critical-severity PRs merged today (Anthropic thinking, Codex supervision, UTF-16 safety, SSE cap)
- 10 upvotes on #63829 (per-agent wiki) reflects active multi-agent deployments
- 6 upvotes on #8508 (configurable ack emojis) shows investment in UX polish even during stability work

## Backlog Watch

These issues/PRs are **important but have not received recent maintainer attention**:

1. **[Open] #91588 — Gateway Memory Leak (P0, 6 weeks unanswered)** (🔗 [Issue](https://github.com/openclaw/openclaw/issues/91588))
   - The most severe stability bug in the repo. 15 comments, no fix PR. 15.5 GB RSS growth after 2–3 days of normal use. **Maintainer attention needed urgently.**

2. **[Open] #102175 — Prompt Cache Breaks Across Boundaries (P1, 3 days)** (🔗 [Issue](https://github.com/openclaw/openclaw/issues/102175))
   - Regression affecting all long-lived embedded sessions. 16 comments, no fix PR yet.

3. **[Open] #101763 — Hosted Molty Model Selector Corruption (P0, 4 days)** (🔗 [Issue](https://github.com/openclaw/openclaw/issues/101763))
   - All agent replies fail due to invalid model ID format. 7 comments, no fix PR. Affects paid hosting users.

4. **[Open] #7524 — Group Consolidation to Main Session (6 months old)** (🔗 [Issue](https://github.com/openclaw/openclaw/issues/7524))
   - 4 upvotes, community strongly wants multi-DM-equivalent for group chats. No maintainer response.

5. **[Open] #63829 — Per-Agent Memory-Wiki Vault (3 months, closed without resolution)** (🔗 [Issue](https://github.com/openclaw/openclaw/issues/63829))
   - 10 upvotes (highest in repo). Closed but the underlying need is unmet — likely re-filed soon.

6. **[Open] #10659 — Masked Secrets (5 months old)** (🔗 [Issue](https://github.com/openclaw/openclaw/issues/10659))
   - P1 feature request with 4 upvotes and strong security rationale. No PR movement despite being tagged `clawsweeper:fix-shape-clear`.

---

## Cross-Ecosystem Comparison

# Cross-Project Ecosystem Comparison Report
**Date:** 2026-07-11 | **Prepared for:** Technical Decision-Makers & AI Agent Developers

## 1. Ecosystem Overview

The personal AI agent open-source ecosystem is experiencing a **high-velocity maturation phase**, characterized by aggressive stability engineering alongside architectural expansion. Seven projects showed active development today, processing **~700+ combined issues and PRs**, with OpenClaw alone accounting for 929 updates. The landscape is bifurcating between **general-purpose agent frameworks** (OpenClaw, Hermes, NanoBot) and **specialized/lightweight tools** (PicoClaw, Moltis, TinyClaw). A clear pattern emerges: projects are converging on multi-agent delegation, context compression, memory persistence, and channel reliability as universal requirements, while diverging in architectural philosophy (monolithic vs. modular, central orchestration vs. peer routing). Security hardening is accelerating across the board, driven by production deployment feedback. Notably, the ecosystem is transitioning from "can it work?" to "can it stay up and stay secure?" — a hallmark of platform maturity.

## 2. Activity Comparison

| Project | Issues Updated | PRs Updated | Merged/Closed | Release Today | Velocity Score |
|---------|---------------|-------------|---------------|---------------|----------------|
| **OpenClaw** | 429 | 500 | 385 | None | 🔴 Maximum |
| **ZeroClaw** | 19 | 50 | 4 | None | 🟡 High |
| **IronClaw** | 36 | 50 | 23 | None | 🟡 High |
| **NanoBot** | 8 | 42 | 17 | None | 🟡 High |
| **Hermes Agent** | 50 | 50 | 8 | None | 🟡 High |
| **CoPaw** | 44 | 49 | 26 | **v2.0.0 Stable** | 🟡 High |
| **PicoClaw** | 3 | 18 | 1 | None | 🟢 Moderate |
| **NanoClaw** | 4 | 25 | 10 | None | 🟢 Moderate |
| **LobsterAI** | 6 | 17 | 10 | **v2026.7.10** | 🟢 Moderate |
| **NullClaw** | 2 | 0 | 0 | None | ⚪ Low |
| **Moltis** | 0 | 1 | 0 | None | ⚪ Low |
| **TinyClaw** | 0 | 0 | 0 | None | ⚪ Inactive |
| **ZeptoClaw** | 0 | 0 | 0 | None | ⚪ Inactive |

**Health Score Ranking:**
1. **OpenClaw** — Unmatched velocity; 193 issues + 192 PRs closed/merged in 24h. However, P0 memory leak (#91588) unresolved for 6+ weeks
2. **CoPaw** — Major v2.0.0 release with rapid hotfix cycle; critical sandbox regression (#5951) threatens Windows deployments
3. **IronClaw** — Strong feature velocity (episodic memory, dynamic tool retrieval) but Slack integration reliability is poor
4. **NanoBot** — Healthy fix pipeline; critical `/restart` auth vulnerability (#4776) and Ollama performance bug (#4867) need immediate attention
5. **ZeroClaw** — Rapid feature expansion offset by Gemini blocking bug (#8934) and 93-day-old Telegram issue (#5514)
6. **Hermes Agent** — Steady activity; P1 Bedrock credential bug (#28156) persists without fix PR
7. **NullClaw** — Security vulnerability in A2A route (#974) with no maintainer response; Telegram idle drop (#972) at 11 days

## 3. OpenClaw's Position

**Advantages vs. Peers:**
- **Scale and maturity:** 929 daily updates (429 issues + 500 PRs) dwarfs every other project — OpenClaw's community is ~5-10x larger than the next tier (IronClaw/ZeroClaw at ~86-100 updates)
- **Platform completeness:** Ships native Codex session supervision (#104045), multi-channel table rendering (#103583), and SSE payload protection (#101274) — features that peers are still designing
- **Security rigor:** Ghosted a cross-plugin session mutation fix (#103534), external content scanning bounds (#104038), and exec approval deny-override (#101276) — the only project proactively closing security gaps before exploitation
- **Fix velocity:** 4 critical-severity PRs merged in one day (Anthropic thinking, Codex supervision, UTF-16 safety, SSE cap)

**Technical Approach Differences:**
- OpenClaw uses a **monolithic plugin architecture** with a central gateway — high integration but also single points of failure (the Gateway memory leak #91588 is a P0 blocker)
- Contrast with **IronClaw's Reborn runtime** approach (gradual migration) and **NanoBot's modular subagent model** — OpenClaw is betting on integration density over architectural flexibility
- OpenClaw's **session supervision model** (Codex Supervisor now native) is more centralized than **ZeroClaw's ACP/routing approach** or **Hermes' multi-agent delegation via MCP**

**Community Size Comparison:**
- OpenClaw's 429 issues in 24h exceeds the total issue count of Hermes (50), IronClaw (36), and CoPaw (44) *combined*
- The 10 upvotes on #63829 (per-agent wiki) in OpenClaw is the single highest-reaction item across *all projects today*
- However, **user sentiment is more volatile** — OpenClaw users report "repeated launchd-handoff restart cycles" (#91588) with emotional weight approaching frustration, while IronClaw users are actively contributing large feature PRs (#5972-#5974)

## 4. Shared Technical Focus Areas

These requirements are emerging across multiple projects simultaneously:

| Requirement | Projects Affected | Specific Needs |
|-------------|-------------------|----------------|
| **Multi-agent delegation & isolation** | OpenClaw (#63829), NanoBot (#4623), IronClaw (#5974), Hermes (#32107), PicoClaw (#2937) | Per-agent memory vaults, model overrides, isolated context, subagent orchestration |
| **Memory persistence & context management** | OpenClaw (#102175), NanoBot (#4867), IronClaw (#5974), CoPaw (#5856), LobsterAI (#2311) | Cross-session recall, prompt caching, compaction reliability, token optimization |
| **Channel reliability & UX parity** | OpenClaw (#84569), ZeroClaw (#5514, #8950), IronClaw (#5943), NullClaw (#972), PicoClaw (#3240) | WhatsApp presence, Telegram multi-image, Slack DM correctness, Teams typing |
| **Security hardening** | OpenClaw (#103534, #10659), NanoBot (#4776), ZeroClaw (#8934), NullClaw (#974), PicoClaw (#3246) | Credential masking, cross-plugin isolation, bearer auth scoping, injection monitoring |
| **Provider compatibility** | OpenClaw (#101763), ZeroClaw (#8934), Hermes (#28156), PicoClaw (#3165), IronClaw (#5969) | Model-specific API quirks (dotted vs. dashed, thought tokens, OAuth refresh) |
| **Observability & debugging** | OpenClaw (#12602), NanoBot (#4877), Hermes (#62399), ZeroClaw (#8933), IronClaw (#5954) | Session search, error classification, OTel correlation, tool output visibility |

## 5. Differentiation Analysis

| Dimension | OpenClaw | IronClaw | NanoBot | ZeroClaw | Hermes Agent | CoPaw |
|-----------|----------|----------|---------|----------|--------------|-------|
| **Target User** | Enterprise/ops teams | Power multi-agent users | Developer-focused | Self-hosters/enthusiasts | Mid-market teams | Chinese enterprise |
| **Architecture** | Monolithic plugin/gateway | Reborn runtime migration | Modular subagent/hook | ACP wire protocol | Desktop+TUI+Web | AgentScope 2.0 OS |
| **Delegation Model** | Central supervisor (Codex) | Per-agent decentralization | `spawn` tool with overrides | ACP peer routing | MCP-based delegation | Multi-agent Cowork |
| **Memory Strategy** | Session + native wiki | Episodic memory (PR #5974) | Prompt-cache reliant | Skill-review forks | Compaction + tail floor | ReMe 0.4 kernel |
| **Channel Breadth** | 7+ channels (Discord/Signal/Slack/Telegram/Feishu/CLI) | Slack-heavy | WebUI + Feishu/WeChat | Telegram + ACP | Teams + Weixin | Desktop shell |
| **Key Differentiator** | **Scale & reliability engineering** | **Feature velocity** | **Developer experience** | **Protocol flexibility** | **Desktop integration** | **Sandbox security** |
| **Risk** | Memory leak (P0, 6 weeks) | Slack integration fragility | Auth vulnerability (P0) | Documentation quality | Bedrock provider gap | Windows sandbox crash |

**Architecture Spectrum:**
- **Centralized orchestration:** OpenClaw ← CoPaw ← IronClaw → Hermes → ZeroClaw → **Peer-to-peer routing**
- **OpenClaw** requires all agents to route through its gateway — yields full observability but single point of failure
- **ZeroClaw's ACP** and **NanoBot's subagent spawn** are more decentralized; each agent can be independently operated
- **Hermes' MCP approach** sits in the middle — agents communicate via protocol, not monolithic runtime

## 6. Community Momentum & Maturity

**Tier 1: Maximum Velocity & Maturity**
- **OpenClaw** — The clear market leader by activity. Shipping fixes faster than any peer. However, the P0 memory leak (#91588) at 6+ weeks is a concerning signal — the community may be outrunning maintainer capacity for the hardest problems.
- **CoPaw** — Major release (v2.0.0) with rapid hotfix turnaround. Windows sandbox regression is the primary risk to maintaining momentum.

**Tier 2: High Velocity, Rapidly Iterating**
- **IronClaw** — Strong feature PRs (episodic memory, tool retrieval, MCP timeouts) show architectural ambition. Bug bash results indicate a disciplined testing culture. Likely to leapfrog peers in memory capabilities within 2 releases.
- **ZeroClaw** — Balancing large feature PRs (SOP broker, git-catalog refactor) with mounting stability debt. The 93-day-old Telegram bug (#5514) and Gemini blocking bug (#8934) reduce user trust.
- **NanoBot** — Healthy velocity but two critical issues (#4776 auth, #4867 performance) without fixes threaten its "developer-friendly" value proposition.
- **Hermes Agent** — Steady contributor engagement. Desktop integration is the strongest differentiator. Bedrock provider gap (#28156) is the primary constraint.

**Tier 3: Moderate/Low Activity**
- **PicoClaw** — Deployed in ARM/edge environments (Raspberry Pi). Agent collaboration PR (#2937) stalled for 48 days indicates feature investment may be paused.
- **LobsterAI** — Just shipped a release. Multi-agent USER.md corruption (#2293) needs immediate attention.
- **NullClaw** — Two high-severity bugs, zero maintainer response. Risk of project abandonment.
- **Moltis/TinyClaw/ZeptoClaw** — Effectively dormant. Moltis has one PR (#1146 for GPT-5.6) awaiting review — a good onboarding opportunity.

## 7. Trend Signals

**For AI Agent Developers, the ecosystem data reveals:**

1. **The "Reliability Ceiling" is the new frontier.** Every major project (OpenClaw #91588, ZeroClaw #8654, CoPaw #5951) has a P0 stability issue that blocks production deployment. The next competitive advantage is **operational maturity**, not feature breadth.

2. **Context management is the most active engineering battleground.** IronClaw (episodic memory), OpenClaw (prompt cache continuity), NanoBot (Ollama caching), and CoPaw (compaction failures) are all investing heavily. **The project that ships reliable, low-cost, multi-session memory first will win enterprise adoption.**

3. **Security is becoming table stakes, not differentiation.** Cross-plugin isolation (OpenClaw), `/restart` auth (NanoBot), and A2A bearer scoping (NullClaw) are being discovered through production use, not proactive design. **All projects need a security audit before claiming production readiness.**

4. **Desktop/WebUI UX is a differentiator for adoption.** OpenClaw (login flash fix), Hermes (session search), and NanoBot (syntax highlighting) are investing in UI despite being "agent frameworks." **Command-line-only projects will struggle for mainstream adoption.**

5. **Multi-agent orchestration patterns are converging on "per-agent model override."** OpenClaw (#63829), NanoBot (#4623), IronClaw (#5974), and Hermes (#58731) all support or are building this. **The "one agent runs one model" paradigm is dead** — future architectures will route sub-tasks to specialized models.

6. **Provider lock-in is a growing risk for end users.** OpenClaw (#101763, dotted model ID), ZeroClaw (#8934, Gemini thought tokens), Hermes (#28156, Bedrock IAM) — **each provider pairing has unique failure modes** that bypass generic provider-agnostic code.

7. **The community is voting with "upvotes" for infrastructure, not features.** The highest-reacted items across all projects: memory isolation (OpenClaw #63829, 10 👍), multi-user support (Hermes #32107, 7 👍), and configurable ack emojis (OpenClaw #8508, 6 👍). **Users want reliable, configurable infrastructure — not novel agent capabilities.**

8. **Windows support is the weakest link.** CoPaw's sandbox crash (#5951), OpenClaw's UTF-16 surrogate pair fixes (#104046), and ZeroClaw's text replacement issues (#8945) all hit Windows users disproportionately. **If the ecosystem wants enterprise adoption, Windows parity is mandatory.**

---

**Bottom Line:** The personal AI agent ecosystem is in a consolidation phase — projects that solve reliability (memory leaks, session persistence, provider compatibility) will pull ahead. OpenClaw leads on raw velocity but the P0 memory leak creates a vulnerability window. IronClaw and NanoBot are strong contenders if they resolve their critical-security and performance gaps. CoPaw's v2.0.0 is a bold bet that could pay off if the sandbox regression is fixed quickly. NullClaw, Moltis, and TinyClaw risk obsolescence without renewed maintainer engagement.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

# NanoBot Project Digest
**Date:** 2026-07-11

---

## 1. Today's Overview

NanoBot is experiencing **high development velocity** with 42 pull requests updated in the last 24 hours and 8 active issues. The project shows strong momentum across multiple fronts: code editing reliability, subagent architecture, memory consolidation, and WebUI polish. Notably, **17 PRs were merged or closed** today, indicating active maintainer review and acceptance of contributions. The open/closed ratio for PRs (25:17) suggests a healthy balance of incoming work and completed features. No new releases were published today, so users are working from the latest commit on the main branch.

---

## 2. Releases

**No new releases were published today.**

---

## 3. Project Progress

**17 pull requests were merged or closed today**, reflecting substantial forward progress:

### 🎯 Key Merged/Closed PRs

- **[PR #4623 — feat(subagent): allow spawn model override](https://github.com/HKUDS/nanobot/pull/4623)** — Adds an optional `model` parameter to the `spawn` tool, enabling subagents to run on different models than the parent agent. *Closes Issue #4231.*
- **[PR #4635 — fix(tools): enforce exact edit_file line hints](https://github.com/HKUDS/nanobot/pull/4635)** — Transforms `line_hint` from a nearest-match preference to an exact consistency guard for `edit_file`, rejecting ambiguous edits before write. *Closes Issue #4634.*
- **[PR #4622 — feat(cron): support job model presets](https://github.com/HKUDS/nanobot/pull/4622)** — Adds `model_preset` support to cron jobs with propagation into bound turns and run records, without mutating the live agent model. *Closes Issue #4378.*
- **[PR #4876 — feat(webui): guide queued prompt with second Enter](https://github.com/HKUDS/nanobot/pull/4876)** — Improves WebUI responsiveness during active responses by allowing users to queue follow-up prompts with a deliberate second Enter.
- **[PR #4877 — feat(webui): highlight file previews and diffs](https://github.com/HKUDS/nanobot/pull/4877)** — Adds lazy Prism syntax highlighting to unified diffs and file previews in the WebUI, with language inference from file paths.
- **[PR #4832 — fix(cli): handle CSI-u Shift+Enter instead of dumping raw escapes](https://github.com/HKUDS/nanobot/pull/4832)** — Fixes a terminal regression for certain terminals that send CSI-u sequences on Shift+Enter.

### 🚀 Features That Advanced

- **Subagent model override** — Users can now specify a different model for subagents via the `spawn` tool.
- **Cron job model presets** — Scheduled tasks can now use dedicated model configurations.
- **WebUI polish** — Queued prompt guidance and syntax highlighting for code diffs.
- **Channel setup flows** — A new PR (#4855) adds guided setup surfaces for Feishu and WeChat channels.

---

## 4. Community Hot Topics

### Most Active Discussions

| Issue/PR | Type | Comments | Key Discussion |
|----------|------|----------|----------------|
| [#4253 — Override model per conversation](https://github.com/HKUDS/nanobot/issues/4253) | Issue | 6 | User wants to switch between OpenRouter (fast/cheap) and local LlamaCpp (private/slow) based on task sensitivity. This is the **most active open feature request** with technical design discussion underway. |
| [#4867 — Preserve exact prompt prefix for Ollama caching](https://github.com/HKUDS/nanobot/issues/4867) | Issue | 3 | Reports that Ollama takes an **extra 60 seconds per turn** because Nanobot doesn't preserve exact prompt structure for KV-cache reuse. The author describes this as "totally unusable" with 32GB VRAM. |
| [#4634 — edit_file disambiguation failures](https://github.com/HKUDS/nanobot/issues/4634) | Issue (Closed) | 2 | Identified as the "dominant failure mode" in offline edit benchmarks. **Now fixed in PR #4635 (merged today).** |

### Underlying Needs

1. **Model flexibility** — Users want per-conversation, per-task, and per-cron-job model selection (Issues #4253, #4231, #4378). The ecosystem needs granular model routing.
2. **Performance optimization** — The Ollama caching issue (#4867) highlights that Nanobot's prompt construction is breaking provider-level optimizations, making local inference impractical for some users.
3. **Edit reliability** — The `edit_file` disambiguation fix (#4634→#4635) addresses a core reliability pain point that was limiting code editing success rates.

---

## 5. Bugs & Stability

### 🔴 Critical

- [#4776 — `/restart` command has zero authorization](https://github.com/HKUDS/nanobot/issues/4776) — Any user who passes `is_allowed()` can kill the entire bot process. **No fix PR submitted yet.** This is a **security vulnerability** because it bypasses session locking.

### 🟠 High

- [#4835 — WebUI landing message sent to unrelated chat](https://github.com/HKUDS/nanobot/issues/4835) — Race condition when queuing first message during chat creation. **Closed but root cause may still exist in edge cases.**

### 🟡 Medium

- [#4842 — `asyncio.CancelledError` in MCP shutdown](https://github.com/HKUDS/nanobot/pull/4842) — MCP server termination within timeout causes unhandled `CancelledError`. **Fix PR #4842 is open** and labeled priority: p1.
- [#4843 — MCP reconnect gateway crash on stale stack cleanup](https://github.com/HKUDS/nanobot/pull/4843) — Stale `AsyncExitStack` cleanup during reconnect causes crashes. **Fix PR #4843 is open** and labeled priority: p1.

### 🟢 Low

- [#4872 — Dream creates empty git commits on no-op runs](https://github.com/HKUDS/nanobot/issues/4872) — Clutters repository with useless commits. **Fix PR #4873 is open.**

### Fix PRs Available

| Issue | Fix PR | Status |
|-------|--------|--------|
| #4867 (Ollama caching) | None yet | Requested |
| #4776 (/restart auth) | None yet | Open |
| #4842 (MCP CancelledError) | [#4842](https://github.com/HKUDS/nanobot/pull/4842) | Open, p1 |
| #4843 (MCP reconnect crash) | [#4843](https://github.com/HKUDS/nanobot/pull/4843) | Open, p1 |
| #4872 (empty dream commits) | [#4873](https://github.com/HKUDS/nanobot/pull/4873) | Open |

---

## 6. Feature Requests & Roadmap Signals

### Strong Signals for Next Release

1. **Per-conversation model override** ([#4253](https://github.com/HKUDS/nanobot/issues/4253)) — Already has 6 comments and active design discussion. With the `spawn model override` (#4231→#4623) and `cron model presets` (#4378→#4622) now merged, this is the next logical extension of the model-routing theme.

2. **Ollama prompt caching support** ([#4867](https://github.com/HKUDS/nanobot/issues/4867)) — Freshly filed but urgent (60-second overhead per turn). Likely to be prioritized given the severity.

3. **Aggregated subagent results** ([#4624](https://github.com/HKUDS/nanobot/pull/4624)) — Open PR adding a `subagentResultMode` configuration option for buffered/aggregated results. Shows architectural investment in subagent patterns.

4. **Sustained goals opt-in flag** ([#4879](https://github.com/HKUDS/nanobot/pull/4879)) — Makes `long_task` features opt-in (default off) because they "block user interaction." This addresses a clear usability pain point.

### Emerging Themes

- **Agent-to-Agent (A2A) delegation** — PR #4571 introduces native A2A peer delegation across agents with depth guards, enabling Supervisor→Researcher→Writer workflows. This is still in conflict resolution status.
- **Token optimization** — PR #4588 adds command-output compaction to reduce context tokens, addressing a complementary performance concern to the Ollama caching issue.

---

## 7. User Feedback Summary

### Pain Points

| Pain Point | Source | Severity |
|------------|--------|----------|
| "Totally unusable with Ollama and 32 GB VRAM" | [#4867](https://github.com/HKUDS/nanobot/issues/4867) | 🔴 Critical |
| "/restart kills all channels with zero auth" | [#4776](https://github.com/HKUDS/nanobot/issues/4776) | 🔴 Critical |
| "edit_file wrong-occurrence failures dominate benchmarks" | [#4634](https://github.com/HKUDS/nanobot/issues/4634) | 🟠 High (now fixed) |
| "Many unnecessary empty commits" | [#4872](https://github.com/HKUDS/nanobot/issues/4872) | 🟢 Low |
| "First message can be sent to wrong chat in WebUI" | [#4835](https://github.com/HKUDS/nanobot/issues/4835) | 🟡 Medium (closed) |

### Use Case Highlights

- **Privacy/time trade-off** — User alternates between OpenRouter (fast/paid) and local LlamaCpp (private/slow) based on task sensitivity (#4253).
- **Dream automation frustration** — Dream feature creates noisy git history, cluttering repositories with no-op commits (#4872→#4873).
- **Sustained goal blocks interaction** — Background goal pursuit prevents normal agent interaction during long tasks (#4879).

### Sentiment

The community is **actively contributing** (42 PRs today) but **vocal about critical performance and security issues**. The Ollama caching bug (#4867) is generating strong negative sentiment because it renders local inference impractical for even well-resourced users.

---

## 8. Backlog Watch

### Issues Needing Maintainer Attention

| Issue | Age (Days) | Last Updated | Risk |
|-------|-----------|--------------|------|
| [#4776 — `/restart` authorization](https://github.com/HKUDS/nanobot/issues/4776) | 5 | 2026-07-10 | 🔴 **Security vulnerability** — No fix PR. User reports "zero authorization checks." |
| [#4867 — Ollama prompt caching](https://github.com/HKUDS/nanobot/issues/4867) | 1 | 2026-07-10 | 🔴 **Performance critical** — 60-second overhead cited. No fix PR yet. |

### PRs Stalled in Conflict/Review

| PR | Age (Days) | Status | Reason |
|----|-----------|--------|--------|
| [#4205 — Mailbox-backed subagent results](https://github.com/HKUDS/nanobot/pull/4205) | 36 | Open, conflict | Long-running architectural change with merge conflicts. |
| [#4571 — Native A2A peer delegation](https://github.com/HKUDS/nanobot/pull/4571) | 13 | Open, conflict | Complex feature with depth-doors; conflicts with other subagent work. |
| [#4588 — Tool output compaction](https://github.com/HKUDS/nanobot/pull/4588) | 12 | Open, conflict | Performance optimization conflicting with other token management work. |

### Recommendations

1. **Prioritize `/restart` authorization fix** (#4776) — Security vulnerability with no fix PR after 5 days is concerning.
2. **Accelerate Ollama caching fix** (#4867) — The "60 seconds per turn" claim makes Nanobot unusable for a major provider's local models.
3. **Resolve conflicts on stalled PRs** (#4205, #4571, #4588) — These represent significant architectural improvements that are aging without resolution.

---

*Generated from NanoBot GitHub data (github.com/HKUDS/nanobot) on 2026-07-11.*

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

# Hermes Agent Project Digest — 2026-07-11

## Today's Overview

Hermes Agent shows **high activity** today with 50 issues and 50 PRs updated in the last 24 hours. The project maintains a healthy open/closed ratio with 45 active issues and 5 closed, alongside 47 open PRs and 3 merged/closed. No new releases were published today. The community is actively contributing across multiple areas including desktop UI, context compression, delegation, security, and bug fixes. The volume suggests a well-maintained project with responsive maintainers and an engaged contributor base.

## Releases

No new releases were published today. The latest available version remains v0.18.2 (2026.7.7.2) as referenced in recent bug reports.

## Project Progress

**3 PRs merged/closed today:**

- **#61336** — [CLOSED] fix(agent): repair MCP tool names with dropped `mcp__server__` prefix. Fixes a bug where models (notably GLM) emit MCP tool names without the full prefix (e.g., `list_memory_projects` instead of `mcp__basic_memory__list_memory_projects`). The existing fuzzy-match repair pipeline now handles this case. *(Author: yingliang-zhang)*
- **#50295** — [CLOSED] Bedrock Claude `/usage` shows cost unknown — pricing table lacked cache cost fields and cross-region prefix normalization. This fix enables proper cost reporting for Bedrock prompt caching. *(Author: teknium1)*
- **#10835** — [CLOSED] Feature request to expose Hermes memory (MEMORY.md/USER.md) via MCP server was closed. (Author: easyvibecoding)

**Notable open PRs advancing today:**
- **#62389** — Implements the **prune-first phase** for context compression (related to Issue #513), an LLM-free tool-output elision that fires on an absolute token budget. Opt-in and disabled by default. *(Author: trac3r00)*
- **#62392** — Adds configurable foreground execution for delegation, allowing parent agents to wait for child results in the current turn. *(Author: vdanda1515)*
- **#60662** — Makes the compaction tail floor configurable via `max_tail_message_floor`, addressing user needs for custom context window management. *(Author: yingliang-zhang)*
- **#62399** — Adds title-based search with ranking to the desktop session list, addressing UX complaints about finding sessions in large lists. *(Author: Kyzcreig)*

## Community Hot Topics

**Most Active Issues (by comments):**

1. **[#52496 — Dashboard model switcher rewrites named custom providers to openrouter](https://github.com/NousResearch/hermes-agent/issues/52496)** (7 comments) — A provider configuration bug where the Web Dashboard persists wrong provider names for custom providers defined in `config.yaml`. Users need to manually re-select providers after every page refresh.

2. **[#48098 — Desktop shows stale "Summarizing thread" status after compaction resumes](https://github.com/NousResearch/hermes-agent/issues/48098)** (7 comments) — UI state management bug where compaction status labels persist even after the model resumes work, confusing users about whether the agent is still busy.

3. **[#28156 — Bedrock+Claude: wizard accepts Bearer-only setup but runtime fails on missing IAM](https://github.com/NousResearch/hermes-agent/issues/28156)** (5 comments, P1) — A high-priority bug affecting AWS Bedrock users. The setup wizard accepts incomplete credentials, but runtime fails. Also shows unroutable US/global profiles for EU region users. This is the highest-severity (P1) open issue.

4. **[#10835 — Expose Hermes memory via MCP server](https://github.com/NousResearch/hermes-agent/issues/10835)** (5 comments, CLOSED) — Heavy demand for memory tool exposure surfaced through MCP. Closed today, suggesting resolution or deferral.

5. **[#513 — Two-Phase Context Management (prune before compaction)](https://github.com/NousResearch/hermes-agent/issues/513)** (4 comments) — Inspired by Kilocode, this feature request has gained traction and now has an implementation PR (#62389) open. Proposes cheaper, better context management through phased pruning.

**Most Reacted Issues:**
- **#32107 — Multiple users per agent with separated context** (👍 7) — Strong community demand for multi-user support for small businesses and product integrations.

## Bugs & Stability

**Critical/P1 Bugs:**
- **[#28156](https://github.com/NousResearch/hermes-agent/issues/28156) (P1)** — Bedrock+Claude: Wizard accepts incomplete credentials, runtime fails with missing IAM. Profile picker shows US/global profiles in EU region. *No fix PR identified.*

**P2 Bugs Reported/Updated Today:**
- **[#52496](https://github.com/NousResearch/hermes-agent/issues/52496)** — Dashboard custom provider persistence corruption (named custom providers rewritten to openrouter).
- **[#48098](https://github.com/NousResearch/hermes-agent/issues/48098)** — Desktop sticky "Summarizing thread" label after compaction resumes.
- **[#60385](https://github.com/NousResearch/hermes-agent/issues/60385)** — MCP server processes leak on transport reconnection. *No fix PR.*
- **[#55677](https://github.com/NousResearch/hermes-agent/issues/55677)** (CLOSED) — Context compaction fails with Jinja template error, corrupting sessions. *Closed today.*
- **[#62170](https://github.com/NousResearch/hermes-agent/issues/62170)** — TUI shows stale session content after switching sessions (v0.18.1). *Needs repro.*
- **[#54756](https://github.com/NousResearch/hermes-agent/issues/54756)** — TUI/Desktop stuck in busy state after task completes with empty final response.
- **[#57828](https://github.com/NousResearch/hermes-agent/issues/57828)** — Lazy backend refresh failures corrupt venv; update has no recovery path.
- **[#62394](https://github.com/NousResearch/hermes-agent/issues/62394)** (NEW) — Teams typing indicator animates forever — suspected leaked `_keep_typing` task.
- **[#62383](https://github.com/NousResearch/hermes-agent/issues/62383)** (NEW) — Weixin iLink cron delivery fails with rate-limited error when `context_token` is stale.
- **[#62346](https://github.com/NousResearch/hermes-agent/pull/62346)** (PR, OPEN) — Fixes credential-bearing env vars leaking into terminal snapshots. Security vulnerability fix in progress.

**Other Bugs:**
- **[#40077](https://github.com/NousResearch/hermes-agent/issues/40077) (P3)** — Desktop crashes on NVIDIA 580+ drivers (Ubuntu 24.04). Community has workarounds but no fix PR.
- **[#62324](https://github.com/NousResearch/hermes-agent/issues/62324) (P3)** — Desktop terminal fails because `stage-native-deps.mjs` drops execute bit on node-pty's spawn-helper.
- **[#53329](https://github.com/NousResearch/hermes-agent/issues/53329) (P3)** — Non-git project folders show duplicate lanes in sidebar.
- **[#62341](https://github.com/NousResearch/hermes-agent/issues/62341) (P3)** — "No runs yet" shown for `no_agent` cron jobs despite successful executions.

## Feature Requests & Roadmap Signals

**High-Community-Interest Features:**
1. **Per-subagent model override** ([#58731](https://github.com/NousResearch/hermes-agent/issues/58731)) — Request to route different subagent roles to different models, noting that the master-worker pattern benefits from specialized models per role. **Likely next version** given existing delegation infrastructure.

2. **UI for custom provider configuration** ([#52807](https://github.com/NousResearch/hermes-agent/issues/52807)) — Users want to configure third-party API providers through UI instead of editing `config.yaml`. Lower priority given complexity.

3. **Volatile skills** ([#36656](https://github.com/NousResearch/hermes-agent/issues/36656), 👍 2) — Load skill content for one turn only to avoid bloating conversation history. Requests for skills optimization with 66+ active skills.

4. **Message timestamps in agent context** ([#62369](https://github.com/NousResearch/hermes-agent/issues/62369), NEW) — Inject timestamps so the agent can distinguish events across multi-day sessions.

5. **Multiple users per agent with separated context** ([#32107](https://github.com/NousResearch/hermes-agent/issues/32107), 👍 7) — Small business use case: 4-person startup wants product integration with per-user context isolation.

6. **Per-profile tab lease/registry** ([#62339](https://github.com/NousResearch/hermes-agent/issues/62339)) and **per-tab CDP target routing** ([#62338](https://github.com/NousResearch/hermes-agent/issues/62338)) — Coordination for concurrent browser agents sharing profiles.

**Likely to Ship in Next Release:**
- Two-phase context compression (PR #62389 for Issue #513)
- Configurable `max_tail_message_floor` (PR #60662)
- Desktop session title search (PR #62399)
- Configurable foreground delegation (PR #62392)
- Desktop model defaults fix (PR #62395)

## User Feedback Summary

**Pain Points:**
- **Provider configuration friction** (#52496, #52807) — Custom providers require manual `config.yaml` edits and the dashboard breaks them. Multiple users asking for GUI configuration.
- **UI confusion in multi-session workflows** (#62170, #48098, #54756) — Stale state, stuck busy indicators, and indistinguishable message bubbles (#57104) cause confusion during active use.
- **Context management unpredictability** (#55677, #513) — Session corruption from compaction failures and desire for more controllable/cheaper context management.
- **Missing production features** (#32107, #62369, #58731) — Multi-user support, time awareness, and per-subagent model routing are blockers for business/product integration.

**Satisfaction Signals:**
- Active community contribution across PRs and issues suggests high engagement.
- The two-phase compression feature (Issue #513) has a real implementation PR from a community member, showing investment in improving core functionality.
- Multiple contributors working on security hardening (#61352, #62346, #3630) indicates a mature project recognizing enterprise needs.

## Backlog Watch

**Issues Needing Maintainer Attention:**

1. **[#32107](https://github.com/NousResearch/hermes-agent/issues/32107) — Multiple users per agent** (👍 7, Created 2026-05-25, Last updated 2026-07-10) — Highest-reaction issue on this watchlist. No assignee, no milestone. Small business adoption blocker.

2. **[#36656](https://github.com/NousResearch/hermes-agent/issues/36656) — Volatile skills** (👍 2, Created 2026-06-01, Last updated 2026-07-10) — Unanswered by maintainers. Performance optimization that would benefit heavy skill users.

3. **[#3630](https://github.com/NousResearch/hermes-agent/issues/3630) — Phase 4 Advanced Security** (Created 2026-03-28, P3) — Ephemeral secrets, external vault integration, audit. Part of a phased rollout; no visible progress since March.

4. **[#40077](https://github.com/NousResearch/hermes-agent/issues/40077) — Desktop crashes on NVIDIA 580+ drivers** (Created 2026-06-05, Ubuntu 24.04) — No fix PR or acknowledged workaround from maintainers.

5. **[#46947](https://github.com/NousResearch/hermes-agent/issues/46947) — No way to set email subject** (Created 2026-06-16) — Hardcoded "Re: Hermes Agent" prevents agent-initiated email use cases like cron reports.

6. **[#9403](https://github.com/NousResearch/hermes-agent/issues/9403) — Pricing overrides, contract pricing, sync CLI** (Created 2026-04-14) — Phase 4 pricing architecture unimplemented despite route-aware estimation existing.

**Stale PRs:**
- **PR #44130** — Fork remote update detection (Opened 2026-06-11, last updated today) — Desktop update checks for fork installations. No merge activity.
- **PR #43265** — macOS desktop self-update fail-fast recovery (Opened 2026-06-10) — Revived from a closed PR but still open after a month.
- **PR #39192** — Desktop bootstrap install stamps (Opened 2026-06-04) — Harden bootstrap identity tracking.

*Note: "Long-unanswered" is relative to the project's high activity rate. Most issues receive updates within days; these represent the longest-known gaps.*

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

# PicoClaw Project Digest — 2026-07-11

## 1. Today's Overview

PicoClaw shows moderate activity today with 3 issues updated and 18 pull requests updated in the last 24 hours, though one PR was the only merge/close event. The project is in a healthy maintenance cycle: three active PRs from contributor `corporatepiyush` focus on performance and security hardening, while feature work around WhatsApp presence and OAuth correctness is also moving forward. No new releases were published, but the open PR queue (17 open) indicates sustained community and core team development.

---

## 2. Releases

No new releases were published today. The latest known version remains **v0.2.9** (referenced in Issue #3178).

---

## 3. Project Progress

One pull request was merged/closed today:

- **[PR #3179] [CLOSED] fix(whatsapp): reconnect after websocket drops** — *Author: Alix-007*. This fix improves WhatsApp bridge reliability by implementing automatic reconnection after websocket read failures, adding read deadline and ping/pong handlers, and dispatching inbound messages asynchronously to keep the read loop alive. Addresses the underlying issue reported in closed Issue #3178 (WhatsApp websocket timeout).

---

## 4. Community Hot Topics

The most active items by comments and reactions:

- **[Issue #3178 — [CLOSED] WhatsApp Websocket Timeout](https://github.com/sipeed/picoclaw/issues/3178)** (2 comments, updated 2026-07-10) — The closed bug described stale connection behavior in the WhatsApp channel when using Docker with launchpad. Though closed, it was directly addressed by merged PR #3179.

- **[PR #3165 — fix(openai_compat): recover Seed XML tool calls](https://github.com/sipeed/picoclaw/pull/3165)** (Author: Alix-007, updated 2026-07-10, stale) — A long-running PR to recover Volcengine Doubao Seed XML tool calls from OpenAI-compatible responses. Has been open since June 24, suggesting either complexity in review or lower priority.

- **[PR #2937 — Feat/agent collaboration](https://github.com/sipeed/picoclaw/pull/2937)** (Author: afjcjsbx, updated 2026-07-10, stale) — A major feature introducing an internal Agent Collaboration Bus with per-agent mailboxes, collaboration threads, and permission-aware routing. Open since May 24, it signals strong interest in multi-agent coordination but may need maintainer attention to progress.

**Underlying needs**: The community is pushing for WhatsApp reliability (presence, reconnection), OAuth provider compatibility, and multi-agent collaboration infrastructure. The agent collaboration PR (#2937) in particular suggests users are building complex multi-agent workflows on PicoClaw.

---

## 5. Bugs & Stability

Three issues or PRs address bugs, ranked by severity:

1. **CRITICAL — [Issue #3239](https://github.com/sipeed/picoclaw/issues/3239): OAuth refresh requests use incompatible provider semantics and can race**  
   *Author: greencabe | Created: 2026-07-10 | Comments: 0*  
   The `auth.RefreshAccessToken` method sends the same form-encoded payload to all OAuth providers and includes a fixed `scope`, causing runtime failures (OpenAI expects JSON; others may reject the scope). A fix exists: **[PR #3241 — fix(auth): make OAuth refresh provider-correct and concurrency-safe](https://github.com/sipeed/picoclaw/pull/3241)** (also by greencabe, opened same day).

2. **HIGH — [PR #3248](https://github.com/sipeed/picoclaw/pull/3248): fix: bump Go to 1.25.12 to remediate stdlib vulnerabilities**  
   *Author: afjcjsbx | Created: 2026-07-10*  
   Bumps Go toolchain to patch `GO-2026-5856` in `crypto/tls` and `GO-2026-4970` in `os`. Two CVEs in the standard library directly affect PicoClaw deployments.

3. **MEDIUM — [PR #3246](https://github.com/sipeed/picoclaw/pull/3246): fix: security and robustness hardening (MQTT TLS, OAuth timeouts, bounded search reads)**  
   *Author: corporatepiyush | Created: 2026-07-10*  
   MQTT channel was hardcoded with `InsecureSkipVerify: true`, disabling TLS certificate verification for all broker connections. Also adds OAuth request timeouts and bounds on search read concurrency.

---

## 6. Feature Requests & Roadmap Signals

Two feature requests opened today with fix PRs attached:

- **[Issue #3240](https://github.com/sipeed/picoclaw/issues/3240): Add typing presence to WhatsApp native replies** — *Author: greencabe*  
  Requests WhatsApp typing indicator while agent prepares a reply. A companion **[PR #3242](https://github.com/sipeed/picoclaw/pull/3242)** implements `channels.TypingCapable` with composing/paused states and 10-second refreshes.

- **[Issue #3239](https://github.com/sipeed/picoclaw/issues/3239) (OAuth refresh)** includes both a bug report and implied feature request for provider-correct token refresh. PR #3241 addresses this.

**Likely for next minor version:** WhatsApp typing presence (PR #3242), OAuth provider-correct refresh (PR #3241), Go toolchain security bump (PR #3248), and MQTT TLS hardening (PR #3246). All are small, focused changes with immediate user impact or security benefit.

**Longer-term signals:** The still-open agent collaboration PR (#2937) and the Simplex channel addition (PR #3193) suggest the platform is expanding its channel and multi-agent capabilities.

---

## 7. User Feedback Summary

Pain points expressed in today's issues and PRs:

- **WhatsApp UX gap** (Issue #3240): Users see no feedback between sending a message and receiving a bot reply, even when processing takes several seconds. The typing presence implementation directly addresses this dissatisfaction.

- **Deployment friction on ARM** (PR #3205): A user running on Raspberry Pi 3 B+ had to add their own ARM build target and fix 9router gateway response parsing. Indicates Linux ARM support is incomplete.

- **OAuth integration complexity** (Issue #3239): Users integrating OpenAI as an OAuth provider hit runtime failures because refresh logic assumed all providers use the same API semantics. This is a real blocker for multi-provider setups.

- **WebSocket reliability** (Issue #3178, closed): WhatsApp connection timeouts in Docker environments were a user-reported pain point now resolved by PR #3179.

---

## 8. Backlog Watch

Items needing maintainer attention:

1. **[PR #2937 — Feat/agent collaboration](https://github.com/sipeed/picoclaw/pull/2937)** — Open since **2026-05-24** (48 days). A large, foundational feature for inter-agent communication. No recent review activity. Risk of merge conflicts or community frustration if left stale.

2. **[PR #1951 — Move installation scripts from docs repo to here](https://github.com/sipeed/picoclaw/pull/1951)** — Open since **2026-03-24** (109 days). A simple infrastructure reorganization that has been waiting for over three months.

3. **[PR #3165 — fix(openai_compat): recover Seed XML tool calls](https://github.com/sipeed/picoclaw/pull/3165)** — Open since **2026-06-24** (17 days). Addresses compatibility with Volcengine Doubao/Seed models. May block users of that provider.

4. **[PR #3208 — build(deps): bump maunium.net/go/mautrix](https://github.com/sipeed/picoclaw/pull/3208)** — Open since **2026-07-02** (9 days). A dependency bump for the Matrix protocol library (0.27.0 → 0.28.1) that could affect Matrix channel reliability. Stale-labeled.

All stale-labeled PRs (those with `[stale]` in title) would benefit from maintainer review or explicit decision to close.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

Here is the NanoClaw project digest for 2026-07-11, generated from the provided GitHub activity data.

---

## NanoClaw Project Digest — 2026-07-11

### 1. Today's Overview

The project is in a period of **very high velocity**, driven overwhelmingly by a single maintainer or core team executing a coordinated cleanup and architecture refactor. Today saw **25 pull requests** updated, with **10 merged or closed**, indicating a significant batch of work being finalized. This activity appears to be part of a deliberate engineering sprint, focusing on fixing timestamp conventions, formalizing channel configuration, and addressing long-standing bugs in CLI workflows. The presence of an open Issue (#3001) regarding a fundamental architectural flaw (stale symlinks) suggests that while the project is shipping fixes quickly, some systemic issues remain under investigation.

### 2. Releases

- **No new releases today.** The latest publicly available version remains unchanged.

### 3. Project Progress (Merged/Closed PRs)

The bulk of today's closed PRs (10 items) demonstrate a concentrated effort on **correctness, configuration, and developer tooling**.

- **Timestamp Standardization (Core Team):** A major cleanup effort to enforce a unified timestamp convention across the entire codebase. Three PRs (#3005, #3006, #3007) ensure storage uses ISO-Z UTC while display uses local time, fixing a subtle bug where task timestamps rendered with the wrong offset compared to chat timestamps.
- **Channel Architecture Refactor:** The core team merged a series of PRs (#3009, #3010, #3011) to shift channel behavior configuration (engage mode, threading, sender policy) from hardcoded core logic to being **declared by each adapter**. This is a significant architectural improvement that will make adding new channels more predictable. #3009 specifically fixed a bloat issue where all channel formatting skills were installed for every agent.
- **Developer Tools & Docs:** A new `scripts/context-preview.ts` tool (#3004) was added to simulate different scenarios and print exactly what an agent sees. PR #3003 added documentation warnings against unbounded wait loops in the `agent-browser` skill.
- **WhatsApp Stability:** Issue #3008 fixed a critical bug where cached group metadata broke sender-key distribution messages (SKDM) in LID-mode WhatsApp groups, which would have caused message delivery failures.

### 4. Community Hot Topics

- **#3001: Stale skill symlinks after refactor (OPEN)** [Link](https://github.com/nanocoai/nanoclaw/issues/3001)
    - *Underlying Need:* This represents a significant **data integrity and maintainability** concern. Users who created groups before a major refactor are silently running outdated skill versions, leading to unpredictable agent behavior. The community needs a reliable, visible migration path for existing deployments.
- **#3014: Fix for `hasIdenticalSend` bounding (OPEN)** [Link](https://github.com/nanocoai/nanoclaw/pull/3014)
    - *Underlying Need:* This fix targets the agent runner's core logic for preventing duplicate sends. The community likely values this as a stability fix, ensuring the system correctly identifies and handles messages that are already in-flight.

### 5. Bugs & Stability

- **(High) #3001: Stale skill copies block symlinks** [Link](https://github.com/nanocoai/nanoclaw/issues/3001)
    - *Status:* **Open.** A design flaw where groups created before April 21st's refactor have hard copies of skills that override new shared symlinks. No fix PR exists yet, making this the most critical stability risk today.
- **(Medium) #8966 (PR #3008): WhatsApp SKDM breakage in LID groups** [Link](https://github.com/nanocoai/nanoclaw/pull/3008)
    - *Status:* **Fixed.** A critical bug causing message delivery failures for WhatsApp users in LID-mode groups. A fix PR has been submitted.
- **(Medium) #2415: `ncl groups create` skips `container_configs` row** [Link](https://github.com/nanocoai/nanoclaw/issues/2415)
    - *Status:* **Closed.** This was a reproducible bug causing the first container spawn to fail. The closure indicates a fix has been deployed in a previous merge.
- **(Medium) #2389: CLI wirings don't auto-create destinations** [Link](https://github.com/nanocoai/nanoclaw/issues/2389)
    - *Status:* **Closed.** Another CLI workflow bug where messages were silently dropped. Now resolved.

### 6. Feature Requests & Roadmap Signals

- **Provider-Agnostic Persistent Memory (Core Team):** PRs #3012 and #3013 are a major new feature being introduced. This will give agents a shared, persistent memory tree that survives across sessions and is compatible with multiple agent providers (likely Codex and OpenCode). This is a strong signal that the next release will focus on long-term memory.
- **Unified iMessage Channel (Community):** PR #2999 proposes merging the two separate iMessage backends (local and hosted) into a single, unified channel skill. This addresses a user pain point of having to install and configure two separate skills for the same service.
- **Telegram Rich Rendering (Community):** PR #2877 is an older, long-running feature request to leverage the Telegram Bot API 10.1's native rich message rendering. This is still open, indicating it is a complex or lower-priority community contribution.

### 7. User Feedback Summary

- **Pain Point - Silent Failures:** Multiple issues from users (`glifocat`, `alexli-77`) reveal a pattern where failures are silent. Agents drop messages due to missing destinations (#2389), and containers fail to spawn with no clear CLI error (#2415).
- **Pain Point - Upgrade Risk:** The stale skill symlink issue (#3001) creates a significant trust gap for existing users. The fear of "silent breakage" after an update is a major source of dissatisfaction.
- **General Sentiment:** The rapid closure of significant bugs (#2415, #2389) and the release of powerful new tools (#3004) are likely positive signals for the user base, demonstrating responsiveness from the core team.

### 8. Backlog Watch

- **Issue #2877 / PR #2877: Telegram rich rendering** [Link](https://github.com/nanocoai/nanoclaw/pull/2877)
    - *Status:* Open since **2026-06-28** (13 days). This is a substantial community feature addition that could improve the user experience for a major channel (Telegram). Its long idle time without maintainer review could be demotivating for external contributors. A status update on its path to merge is warranted.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

Here is the NullClaw project digest for July 11, 2026.

---

## NullClaw Project Digest: 2026-07-11

### 1. Today's Overview
NullClaw shows low activity today with no new releases or merged pull requests. The project is currently stable in terms of code changes, but user reports indicate two significant open issues that require attention. While the core backend appears operational, community members are experiencing specific integration failures with Telegram and security concerns with the shared bearer authentication system. The maintainer activity is currently focused on triage rather than active feature development.

### 2. Releases
None. No new versions have been published.

### 3. Project Progress
No pull requests were merged or closed today. No new feature advancements or fixes were committed.

### 4. Community Hot Topics
Two issues dominate community discussion today, both concerning critical functional bugs:

- **Issue #972** ([Link](https://github.com/nullclaw/nullclaw/issues/972)): "Telegram channel stop respond after some idle time" — This issue has the most engagement with 2 comments. Users report that the Telegram integration drops off after overnight idle periods, even though the backend (`nullclaw agent -m "ping"`) appears to run fine. This suggests a connection timeout or session refresh bug rather than a complete application crash.

- **Issue #974** ([Link](https://github.com/nullclaw/nullclaw/issues/974)): "NullClaw shared bearer A2A route allows cross-caller task and context reuse" — This is a fresh, high-concern security report. The user demonstrates that sharing a bearer token allows one agent to read another's task history and reuse their context, representing a fundamental authorization gap in the A2A (Agent-to-Agent) route.

### 5. Bugs & Stability
Two bugs reported, with **Issue #974** ranked as **Critical** (security) and **Issue #972** ranked as **High** (functional outage):

- **Critical - Security: Issue #974** — Authorization bypass in A2A route. Bearer token validation does not scope tasks and context to the caller. An attacker with a valid token can replay another user's session. No fix PR exists.
- **High - Functional: Issue #972** — Telegram channel dies after idle period. Likely a session management bug in the Telegram integration wrapper or a timeout in the polling mechanism. No fix PR exists.

### 6. Feature Requests & Roadmap Signals
No explicit feature requests were submitted today. However, **Issue #974** strongly signals an architectural need: the A2A route must implement caller identity and task ownership validation beyond a simple shared bearer token. This is likely to drive a security patch in the next version.

### 7. User Feedback Summary
User feedback reflects two pain points:
- **Reliability pain**: A user (i11010520) is experiencing intermittent unavailability of the Telegram channel. The frustration is mitigated by the backend still working, but the "dead after idle" behavior makes the assistant unreliable for persistent use.
- **Security distress**: A user (N0zoM1z0) discovered and disclosed a clear authorization bypass. This indicates a trust gap in multi-tenant or multi-agent setups.

Overall satisfaction is muted by these two blocking issues; no positive feedback was recorded today.

### 8. Backlog Watch
One long-standing issue requires maintainer attention:

- **Issue #972** (Updated 2026-07-10, Created 2026-06-30) — This issue has remained open for 11 days with 2 comments but no official response from maintainers. Since it affects a core integration (Telegram), it should be prioritized for triage, root cause analysis, or further information gathering from the reporter.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

# IronClaw Project Digest — 2026-07-11

## Today's Overview
IronClaw shows **high engineering velocity** with 50 PRs and 36 issues updated in the last 24 hours, reflecting a mature project in active development. The team merged 15 PRs and closed 8 issues, with significant focus on **loop resilience**, **error recovery**, and **hardening the Reborn runtime**. Three large feature PRs (#5974 episodic memory, #5972 per-turn tool retrieval, #5973 MCP timeouts) opened today signal major capability expansions. The bug bash results continue to surface persistent UX and reliability issues, but the team is systematically addressing them with fix PRs in parallel.

## Releases
No new releases were published today. The last release PR (#5598) remains open with breaking changes to `ironclaw_common` (0.4.2 → 0.5.0) and `ironclaw_skills` (0.3.0 → 0.4.0). Migration notes will be available when released.

## Project Progress
**15 merged/closed PRs today**, driving forward stability and core features:

- **Loop resilience overhaul**: PR #5959 (merged) introduces deep availability retries, iteration backstop (256 ceiling via #5960), and model-visible tool-failure reasons — directly addressing the 65% vs 30% benchmark gap against Hermes
- **Compaction fix**: PR #5895 treats compaction failures as recoverable skips instead of terminal run failures, closing #5838
- **Boot crash fix**: PR #5967 stops crash-looping from invalid extension manifests (#5966) at startup
- **MCP registration store**: PR #5950 (merged) and #5916 (superseded) add per-user MCP registration infrastructure
- **System prompt improvement**: PR #5844 tells agents to compute with tools, not in their heads
- **Bug fixes**: PR #5817 fixes decimal numbers being treated as capability IDs; PR #5961 adds "Verify Before You Finish" coding discipline

## Community Hot Topics

### Most Active Issues
1. **#5948** (5 comments) — Assistant incorrectly reports GitHub extension as activated when only installed. *Need: Accurate extension state representation in agent responses*
2. **#5747** (3 comments, closed) — No way to unpair Slack on built-in host-beta mount. *Need: Disconnect capability parity across all channel mounts*
3. **#5891** (2 comments) — "Last completed" shows active run timestamp instead of finished execution. *Need: Correct run state reporting in UI*

### Most Active PRs
1. **#5974** (new, XL) — Episodic memory for cross-session summaries and recall. *Community interest: Persistent memory is a top-requested AI assistant feature*
2. **#5972** (new, XL) — Per-turn tool retrieval with `find_tools` discovery. *Need: Reducing prompt token usage in tool-heavy deployments*
3. **#5973** (new, XL) — MCP per-server timeouts + background-job bridge. *Need: Configurable timeouts for long-running MCP operations*

All links: Issues | PRs

## Bugs & Stability

### Critical (P1)
- **#5943**: Slack DM action posts to current channel instead of DMs — misdirecting private communications. *No fix PR yet*
- **#5945**: Run fails with "model provider was unavailable" after long multi-tool execution (34 tools observed) — potential timeout or resource exhaustion. *PR #5959 addresses this with retry logic*
- **#5944**: Slack DM silently fails but reports success — misleading success status. *No fix PR yet*

### High (P2)
- **#5836**: Routine fails every 5 minutes with "No thread attached" — 0% success rate for scheduled routines
- **#5834**: Slack disconnect request incorrectly rejected by agent — user cannot disconnect Slack through agent
- **#5885**: Approval notification opens action but approval card is missing — users cannot approve/deny
- **#5879**: Stale error banner persists after successful follow-up — confusing UX
- **#5707**: Routine creation exposes internal implementation details — security/information leak
- **#5946**: Assistant mutates Google Sheet before confirming Slack trigger availability — unwanted data changes
- **#5955**: Multistep workflows with sub-agents hit tool-call limit or stop progressing

### Medium (P3)
- **#5948**: Assistant incorrectly reports extension as activated
- **#5891**: "Last completed" shows active run timestamp
- **#5889**: "Load older messages" button non-functional
- **#5947**: Thread deletion requires page refresh to update UI

### Fixed Today
- **#5838** (closed): Context compaction errors after successful tool execution — fixed by PR #5895
- **#5966** (closed): Boot crash-loop from stale first-party manifest — fixed by PR #5967
- **#5837** (closed): Routine run action buttons not clickable
- **#5835** (closed): "Jump to latest" button positioning issues

## Feature Requests & Roadmap Signals

**Strong roadmap signals from today's PRs:**
1. **Episodic memory** (PR #5974) — cross-session summaries + recall, highly likely for next major release. This addresses the long-standing lack of persistent context in IronClaw
2. **Per-turn dynamic tool retrieval** (PR #5972) — reduces prompt tokens via cosine similarity search, expected in next release for tool-heavy deployments
3. **MCP enhancements** (PR #5973) — configurable timeouts and background jobs, indicates MCP is becoming a first-class integration path
4. **Per-user MCP registration** (PR #5970) — tenant-scoped extension registration, likely part of enterprise/hosting features
5. **Error classification funnel** (PR #5954) — systematic run failure classification, signals move toward better error observability

**User-requested features:**
- GLM-5.2 model not in default opencode list (#5969) — need for broader model support
- Generic HTTP tool failing with third-party APIs (#5968) — MCP-only integration path is limiting
- Unify Reborn dropdown styling (#5938) — UI polish for production readiness
- Retire v1 runtime (#5935) — migration to Reborn-only codebase

## User Feedback Summary

**Pain Points:**
1. **Integration reliability is poor**: Slack DM delivery silently fails (#5944), Slack actions post to wrong channels (#5943), GitHub extension state is misreported (#5948)
2. **Scheduled routines unreliable**: 0% success rate for every-5-minute routines (#5836) undermines automation use cases
3. **Long-running workflows fail unpredictably**: Multi-tool executions crash with opaque errors (#5945), context compaction fails (#5838)
4. **No way to undo integrations**: Once paired with Slack, users cannot disconnect (#5747, #5834) — creates lock-in concern
5. **UI state is confusing**: Stale error banners, non-functional buttons, wrong timestamps degrade confidence (#5879, #5837, #5891)

**Positive Signals:**
- Users are actively building multi-step workflows with sub-agents (#5955) — indicates power users pushing capabilities
- Google Sheets integration is being used (#5946) — real productivity use case
- Community contributors are submitting large feature PRs (#5972, #5973, #5974) — healthy open-source engagement

## Backlog Watch

**Issues requiring maintainer attention:**
1. **#5741** (2 comments, no update in 4 days) — `builtin.http.save` fails with OutputTooLarge for large web pages. *Affects core utility for saving web content, no assigned fix*
2. **#5640** (2 comments, 6 days open) — Harness gap: `hook_security_audit_sink` always None in integration tests. *Security audit coverage gap persists with no PR linked*
3. **#5860** (2 comments, 1 day) — Tool details only appear after tool call completes. *UX issue affecting real-time debugging during tool execution*
4. **#5707** (2 comments) — Routine creation exposes internal details. *Security concern, no fix PR yet*

**Stale PRs needing review:**
- **#5598** (release PR, 8 days open) — Blocking breaking changes to `ironclaw_common` and `ironclaw_skills` from reaching users
- **#5926** (dependabot, 1 day open) — 20 dependency updates including major bump of `agent-client-protocol` (0.10.4 → 1.2.0) — risk of breaking changes

**Pattern to watch**: Multiple P2 bugs from the bug bash (issues #5885, #5879, #5707, #5946) have been open 1-2 days without linked fix PRs, suggesting the team is prioritizing the new feature PRs (#5972-#5974) over bug fixes today.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

Here is the structured project digest for **LobsterAI** based on the GitHub data from **2026-07-11**.

---

## LobsterAI Project Digest — 2026-07-11

### 1. Today's Overview
The project is experiencing a period of **high release velocity** with a new version published yesterday (2026.7.10) and a flurry of merged pull requests. Today’s activity shows a strong focus on **bug fixing and stability**, particularly around the Cowork collaborative mode, IM scheduled tasks, and memory index migration. **17 PRs were updated** in the last 24 hours, with **10 merged/closed**, indicating a disciplined team processing fixes and improvements quickly. However, a **high-priority bug** concerning multi-agent `USER.md` corruption (#2293) remains open and is attracting community attention. The presence of several long-stale PRs suggests a backlog of community contributions awaiting maintainer review.

### 2. Releases
**New Version:** [LobsterAI 2026.7.10](https://github.com/netease-youdao/LobsterAI/releases/tag/2026.7.10)

**What's Changed:**
- **feat(agents):** Support for "delegated subagent collaboration" was introduced, allowing agents to delegate tasks to sub-agents.
- **feat(cowork):** Minimizable permission prompts were added, improving the UX for modal dialogues during collaboration.
- The full changelog is available via the release link above.

**Breaking Changes & Migration Notes:** None explicitly stated. The release appears to be additive and patch-focused.

### 3. Project Progress
The following major fixes and features were merged/closed today:
- **[#2316] Fix (renderer):** Prevented the Windows title bar logo from compressing when the sidebar is collapsed with an update badge.
- **[#2315] Fix (cowork):** Connected a queued follow-up coordinator to process follow-ups across sessions and while the app is minimized.
- **[#2314] Fix (scheduled-task):** Preserved the original casing of WeCom and DingTalk group IDs for delivery, fixing a routing regression from a previous PR (#2306).
- **[#2313] Fix (cowork):** Fixed a bug where only the selected queued steer should be submitted, ensuring FIFO processing integrity.
- **[#2312] Fix (cowork):** Resolved a state loss issue related to the `askuser` minimize functionality.
- **[#2311] Fix (memory):** Implemented a critical migration for FTS-only memory indexes across all agents, ensuring compatibility and safe retry on failure.
- **[#2310] Feat (cowork):** Added support for attaching folders as context, using native path resolution instead of uploading contents.

### 4. Community Hot Topics
- **[#2293] — Multi-agent USER.md Overwrite Bug (Updated: 2026-07-10)**
    - **Link:** [Issue #2293](https://github.com/netease-youdao/LobsterAI/issues/2293)
    - **Activity:** 3 comments, opened by yepcn.
    - **Analysis:** This is the most active issue. The user reports that after a recent update, modifying the `USER.md` or agent settings for one agent overwrites the same file for all other agents. This is a **high-impact regression** for users who rely on distinct agent personalities/instructions. The reporter suspects it is a recent bug, and the lack of maintainer response here is a growing concern.

- **[#1337] — Feature Request: Chat List Time Grouping (Updated: 2026-07-10)**
    - **Link:** [Issue #1337](https://github.com/netease-youdao/LobsterAI/issues/1337)
    - **Activity:** 1 comment, opened by MaoQianTu.
    - **Analysis:** A long-standing feature request for adding time-based grouping (Today, Yesterday, Week) to the session sidebar. While stale, it received an update today, likely due to the linked PR (#1338) being discussed or rebased.

### 5. Bugs & Stability
- **[HIGH] USER.md Overwrite Bug (#2293):**
    - **Severity:** High. This bug breaks a core feature (multi-agent functionality) by causing configuration collisions.
    - **Status:** Open. No maintainer response or fix PR has been linked yet. This should be the team's top priority.
- **[MEDIUM] IM Group ID Routing (#2314 / #2306):**
    - **Severity:** Medium. Affects scheduled tasks for DingTalk and WeCom groups. The fix was merged today, resolving the issue.
- **[LOW/MEDIUM] Stale PR #1333 (i18n & UX):**
    - **Severity:** Low. Addresses minor i18n label errors and escape key functionality. The PR is still open.
- **[CLOSED] Stale: Scheduled Task Toggle (#1392):**
    - **Severity:** Low-Medium. The bug was about buttons not responding. It was closed as stale, meaning the team may not have been able to reproduce it or the user did not follow up.

### 6. Feature Requests & Roadmap Signals
- **Session List Time Grouping (Demand: Medium)**
    - **PR:** [#1338](https://github.com/netease-youdao/LobsterAI/pull/1338)
    - **Prediction:** This is a high-consensus feature requested by multiple users. The PR has been open for months but was just updated. Given the recent UX fixes to the sidebar (logo compression, badge), this could be a prime candidate for the next release to improve the mature user experience.
- **Workdays (Mon-Fri) Schedule Option (Demand: Low)**
    - **PR:** [#1335](https://github.com/netease-youdao/LobsterAI/pull/1335)
    - **Prediction:** A niche but useful power-user feature for scheduling. Unlikely to be a priority unless the team is targeting enterprise workflows.
- **MCP JSON Import (Demand: Low-Medium)**
    - **PR:** [#1336](https://github.com/netease-youdao/LobsterAI/pull/1336)
    - **Prediction:** A quality-of-life improvement for developers. It is a clean, isolated feature that could be merged after code review.

### 7. User Feedback Summary
- **Pain Point (High):** The multi-agent issue (#2293) is causing **significant frustration**. The user expresses confusion ("不知道其他用户遇到过这个问题么？") and has gone as far as to manually edit workspace files, only to have them overwritten on restart. This points to a lack of trust in the current version.
- **Satisfaction (Neutral):** The rapid merging of bugs today (#2314, #2315, #2312) suggests the team is responsive to post-release issues, which generally reduces user dissatisfaction.
- **Use Case:** Power users are clearly leveraging the multi-agent feature for distinct workflows and are sensitive to state corruption.

### 8. Backlog Watch
The following items are flagged as `stale` and have received no maintainer response for months. They represent a **risk of community disengagement**:

- **[#1276] CI Dependabot PR (Open since Apr 2)**
    - **Link:** [PR #1276](https://github.com/netease-youdao/LobsterAI/pull/1276)
    - **Risk:** Low. General dependency update. Stale CI PRs indicate delayed maintainer attention to automation health.
- **[#1275] CI Dependabot PR (Open since Apr 2)**
    - **Link:** [PR #1275](https://github.com/netease-youdao/LobsterAI/pull/1275)
    - **Risk:** Low.
- **[#1331] Feature: Error State Badge (Open since Apr 2)**
    - **Link:** [PR #1331](https://github.com/netease-youdao/LobsterAI/pull/1331)
    - **Risk:** Medium. A high-quality feature addition with clear UX value (red dot for error sessions). The contributor (MaoQianTu) is also the author of the closed stale issue #1330. Ignoring this may discourage a valuable contributor.
- **[#1333] i18n Fix (Open since Apr 2)**
    - **Link:** [PR #1333](https://github.com/netease-youdao/LobsterAI/pull/1333)
    - **Risk:** Low. A minor fix but another sign of backlog.

**Action Required:** The maintainers should triage the long-open `area: renderer` stale PRs and the high-severity USER.md bug to prevent regression damage and maintain contributor morale.

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyagi">TinyAGI/tinyagi</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

# Moltis Project Digest — 2026-07-11

## 1. Today's Overview

Moltis saw minimal activity in the last 24 hours, with zero new issues and no merged pull requests or releases. The project’s single active pull request, #1146, remains open and updated yesterday, representing the only development motion. Overall, the project appears to be in a quiet, steady state with no reported bugs or community fire-drills. While low activity can indicate stability, it may also signal a need for renewed maintainer engagement to keep momentum.

## 2. Releases

No new releases were published in the last 24 hours. No release notes or migration guides are available for this period.

## 3. Project Progress

No pull requests were merged or closed in the last 24 hours. The project made no forward progress on features, fixes, or documentation changes during this period.

## 4. Community Hot Topics

The only item of community interest is:

- **PR #1146 – Add GPT-5.6 model support**  
  *Author: PeterDaveHello | Created: 2026-07-09 | Updated: 2026-07-10 | Comments: 0 | 👍: 0*  
  [GitHub Link](https://github.com/moltis-org/moltis/pull/1146)  

This PR registers GPT-5.6 Sol, Terra, and Luna models in the OpenAI and OpenAI Codex fallback catalogs, applies the new 1.05M context window limit and 372K backend limit, and replaces superseded model references in examples and documentation. The lack of comments or reactions suggests the community has not yet reviewed or discussed this proposal.

**Underlying need:** The PR addresses the need to stay current with fast-moving LLM provider releases—users want access to the latest model versions, accurate context limits, and updated configuration examples without breaking existing workflows.

## 5. Bugs & Stability

No bugs, crashes, or regressions were reported in the last 24 hours. There were no open issues of any kind. The project currently has no stability concerns on record.

## 6. Feature Requests & Roadmap Signals

No new feature requests were submitted in the last 24 hours. However, the open PR #1146 signals a clear roadmap direction: adding support for GPT-5.6 family models. This is likely to be included in the next minor release, given the PR is already written and waiting for review. No other roadmap signals are present.

## 7. User Feedback Summary

No user feedback (comments, reactions, support questions) was recorded in the last 24 hours across any issue or PR. There is no data to report on pain points, use cases, or satisfaction levels for this period.

## 8. Backlog Watch

There are no long-unanswered issues or pull requests in the backlog. The project’s backlog is currently empty, which may indicate either excellent maintainer responsiveness or a low volume of community contributions. The open PR #1146 has been awaiting review for one day and does not yet warrant a “backlog” label, but maintainer attention on it is recommended to prevent stagnation.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

Here is the CoPaw project digest for **2026-07-11**.

---

# CoPaw Project Digest (2026-07-11)

**Project:** CoPaw (github.com/agentscope-ai/CoPaw)
**Date:** 2026-07-11

---

### 1. Today's Overview

The project is in an extremely active state following the release of **v2.0.0 Stable**. Activity is characterized by a burst of bug reports and hotfix PRs targeting regressions introduced by the major architecture upgrade (AgentScope 2.0 migration, Runtime 2.0). A total of 44 issues and 49 PRs were updated in the last 24 hours, indicating a high-velocity patch cycle. While the community is largely celebrating the stable release, the initial feedback is heavily weighted toward "critical" stability and operational issues, particularly related to the new sandbox system and memory module.

### 2. Releases

**Three new versions published in the last 24 hours:**
- **v2.0.0 (Stable):** The major v2.0.0 release. The headline change is the **Runtime 2.0 refactor**, migrating the core kernel to AgentScope 2.0 architecture. This is a high-impact release featuring a new "Agent OS" paradigm.
- **v2.0.0-beta.7:** A late pre-release focusing on polishing the website copy/visuals for the 2.0 launch and fixing a critical memory bug where `session_id` was not propagated to ReMe summarization tasks.
- **v2.0.0-beta.6:** A late pre-release focused on unit testing for the channels module and fixing a bug where tool result error states were not properly forwarded to the frontend envelope.

**Breaking Changes & Migration Notes:**
- **Breaking:** This release fundamentally changes the runtime dependency from `agentscope==1.0.20` to AgentScope 2.0. This likely breaks custom agents, tools, and integrations that relied on the 1.x API.
- **Memory:** The v2.0.0 release uses the ReMe 0.4 memory kernel. Memories, logs, and sessions from v1.1.x may not be fully compatible without explicit migration steps. The community is asking for a formal upgrade guide ([#5948](https://github.com/agentscope-ai/QwenPaw/issues/5948)).

### 3. Project Progress (Merged/Closed PRs)

26 PRs were merged or closed today, focusing on stabilization:

- **Critical Bug Fixes:**
    - [PR #5953](https://github.com/agentscope-ai/QwenPaw/pull/5953): Fixes a major issue where truncated large tool outputs contained a "recall" prompt that caused agents to loop.
    - [PR #5949](https://github.com/agentscope-ai/QwenPaw/pull/5949): Fixes a MCP access policy bug where "allow/deny" settings were not immediately applied.
    - [PR #5938](https://github.com/agentscope-ai/QwenPaw/pull/5938): Fixes a memory attribution bug where command-triggered archival failed to attach a `session_id`.
- **Hotfixes:**
    - [PR #5936](https://github.com/agentscope-ai/QwenPaw/pull/5936): Reverted a PR that injected per-message timestamps due to "ugly display."
    - [PR #5927](https://github.com/agentscope-ai/QwenPaw/pull/5927): Fixes a `UnicodeDecodeError` on Chinese Windows environments.
- **Ops & Documentation:**
    - [PR #5942](https://github.com/agentscope-ai/QwenPaw/pull/5942): Bumps the version to v2.0.0.
    - [PR #5940](https://github.com/agentscope-ai/QwenPaw/pull/5940): Updates the project homepage copy for the v2.0 release.
    - [PR #5932](https://github.com/agentscope-ai/QwenPaw/pull/5932): Updates project documentation for v2.0.

### 4. Community Hot Topics

The most active discussions are driven by **v2.0.0 regressions**:

- **[Issue #5951](https://github.com/agentscope-ai/QwenPaw/issues/5951) (CRITICAL): Desktop shell sandbox causing system instability.** Top comment count (5). A user reports that the new sandbox feature (likely `icacls` logic) causes recursive PowerShell windows to spawn, consuming 20GB+ of RAM. The user states they *must* roll back to v1.1.12.post3, indicating a blocker for production use on Windows.
- **[Issue #5947](https://github.com/agentscope-ai/QwenPaw/pull/5949) (HIGH): MCP tool access policy not applied.** Users report that setting a tool to "denied" in the MCP configuration is ignored, and the agent can still call it. A fix PR ([#5949](https://github.com/agentscope-ai/QwenPaw/pull/5949)) was opened and merged quickly, showing strong maintainer response.
- **[Issue #5906](https://github.com/agentscope-ai/QwenPaw/issues/5906) (MEDIUM): Antiduplication feature is overly aggressive.** Users with multi-step reasoning find the anti-repetition safety catch is triggering a "Doom loop" detection after only 6 iterations, even when the conversation is novel.

### 5. Bugs & Stability

Today's reports indicate significant regressions in v2.0.0.

- **CRITICAL: System Crash/Denial of Service**
    - **[#5951](https://github.com/agentscope-ai/QwenPaw/issues/5951):** Desktop shell sandbox causes infinite process recursion and memory exhaustion. **No fix PR exists yet.**
    - **[#5950](https://github.com/agentscope-ai/QwenPaw/issues/5950):** Memory indexer fails on Chinese content due to character-based (instead of token-based) truncation against the embedding model’s context limit.
- **HIGH: Functional Breakage**
    - **[#5947](https://github.com/agentscope-ai/QwenPaw/issues/5947):** MCP access policy (allow/deny) is a no-op. **Fix exists:** [PR #5949](https://github.com/agentscope-ai/QwenPaw/pull/5949).
    - **[#5929](https://github.com/agentscope-ai/QwenPaw/issues/5929) / [#5946](https://github.com/agentscope-ai/QwenPaw/issues/5946):** Truncated tool results trick the agent into calling `recall_history` unnecessarily. **Fix exists:** [PR #5953](https://github.com/agentscope-ai/QwenPaw/pull/5953).
    - **[#5952](https://github.com/agentscope-ai/QwenPaw/issues/5952):** Auto-memory fails on import error (`ImportError: No module named 'agentscope.tool._builtin._scripts'`) in v2.0.0.
    - **[#5954](https://github.com/agentscope-ai/QwenPaw/issues/5954):** A generic "Is a directory" error when trying to access the MCP folder in the workspace.
- **MEDIUM: Logic Errors**
    - **[#5856](https://github.com/agentscope-ai/QwenPaw/issues/5856):** Context compaction converts structured `tool_call` data to plain text for LLM summarization, corrupting the agent's ability to function.

### 6. Feature Requests & Roadmap Signals

Several user requests suggest high demand for **operational maturity**:

- **Session Management ([#5903](https://github.com/agentscope-ai/QwenPaw/issues/5903)):** A highly requested feature for grouping and importing/exporting sessions. A formal design proposal has been opened ([#5943](https://github.com/agentscope-ai/QwenPaw/issues/5943)), suggesting this is a confirmed P0 for a future sprint.
- **UI/UX Quality-of-Life ([#5909](https://github.com/agentscope-ai/QwenPaw/issues/5909)):** A design proposal for a configurable theme/skin module has been received, indicating work on visual customization is in the pipeline.
- **Upgrade Guide ([#5948](https://github.com/agentscope-ai/QwenPaw/issues/5948)):** A user is requesting a migration guide for v2.0. This is a classic indicator that the upgrade process is not frictionless.

**Prediction for v2.0.1 / v2.1.0:** The roadmap likely focuses on stabilizing the sandbox and MCP subsystems. The next minor version should include the *session grouping* feature and an official *upgrade guide*.

### 7. User Feedback Summary

- **Satisfaction:** The release of v2.0.0 is generating positive sentiment regarding the new architecture and agent features. ([#5945](https://github.com/agentscope-ai/QwenPaw/issues/5945): "v2.0.0正式版本,终于发布了!☀").
- **Dissatisfaction / Pain Points:**
    - **Windows Sandbox:** The top source of frustration. The sandbox feature is currently a blocker for Windows users, causing system-level instability ([#5951](https://github.com/agentscope-ai/QwenPaw/issues/5951)).
    - **MCP Control:** Users expect granular control over their tools; the allow/deny list not working undermines trust in the safety configuration ([#5947](https://github.com/agentscope-ai/QwenPaw/issues/5947)).
    - **Missing Documentation:** The lack of an upgrade guide is a specific pain point for users trying to migrate from v1.x ([#5948](https://github.com/agentscope-ai/QwenPaw/issues/5948)).

### 8. Backlog Watch

- **[Issue #5929](https://github.com/agentscope-ai/QwenPaw/issues/5929) (CRITICAL):** "Disappearing tool results" bug. While a fix PR ([#5953](https://github.com/agentscope-ai/QwenPaw/pull/5953)) is active, the underlying issue where context summarization destroys tool call structure remains a major architectural flaw that could resurface.
- **[Issue #5906](https://github.com/agentscope-ai/QwenPaw/issues/5906) (MEDIUM):** The "Doom loop" logic needs a re-evaluation. The heuristic for "repetition" is clearly too simple, causing frequent false positives for agents that perform complex reasoning. This requires maintainer attention to refine the trigger threshold or logic.
- **[Issue #3437](https://github.com/agentscope-ai/QwenPaw/issues/3437) (LOW):** Request for Kimi API support. This is a long-standing feature request (4 months old) that remains unaddressed. With v2.0.0's provider abstraction, this might be a good candidate for a community contribution.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

# ZeroClaw Project Digest — 2026-07-11

## Today's Overview

ZeroClaw shows **high activity** with 19 issues updated and 50 PRs updated in the last 24 hours, indicating a rapidly evolving codebase in the middle of significant feature work. The project has 17 open/active issues and 46 open PRs, reflecting an active development cycle with substantial parallel workstreams. No new releases were cut today, but the volume of merged/closed PRs (4) and the depth of open PRs suggest v0.8.3 is in active preparation.

---

## Releases

**None** — No releases published in the last 24 hours. The last release was v0.8.2; the v0.8.3 milestone is actively tracked (see Issues #8073 and #8363).

---

## Project Progress

**Merged/Closed in last 24h:** 4 PRs merged or closed. Key highlights:

- **#8677** (closed, enhancement): Added `uses_memory` checkbox to web gateway UI for automation jobs — resolves a long-standing UI gap where memory configuration was only settable via TOML config.
- **#8397** (closed, enhancement): Exposed per-cron-job `uses_memory` flag in CLI and `cron_add`/`cron_update` tools, plus documentation. Precedes the UI work in #8677.

**Note:** The remaining 2 merged/closed items were not explicitly detailed in the top-20 PR list but contributed to overall progress.

**Active feature advancement:** Multiple large PRs remain in review, including the SOP approval broker (#8880, 2.8K lines), plugin TCP outbound support (#8923), and the channel WebSocket consolidation RFC leading to refactoring (#8830).

---

## Community Hot Topics

**Most active issues by engagement:**

1. **[#5514] — Bug: Agent request appends subsequent images on Telegram** — 6 comments, open since April 8. This long-standing multi-image issue is the most-discussed open bug. Users are experiencing duplicate agent responses when sending ≥2 images via Telegram, highlighting a gap in the gateway's image batching logic.

2. **[#8654] — Bug: skill-review fork panics (SIGSEGV)** — 3 comments, marked priority:p1, risk:high. A daemon-crashing out-of-bounds slice access in the skill review background fork. A fix PR (#8680) is already open.

3. **[#8798] — RFC: Consolidate /ws/chat and /acp wire protocols** — RFC discussion with 2 comments. This architectural proposal could reshape the gateway's WebSocket layer, reducing code duplication across 2,132 lines of `ws.rs`.

**Most active PRs:**

- **#8680** (fix for #8654): The most critical fix PR, targeting the SIGSEGV crash in skill-review. Marked priority:p1.
- **#8638** (large skills refactor): 2.8K-line refactor replacing built-in ClawHub with git-catalog selector. This architectural change is controversial — it removes a privileged third-party source and could break existing skill installations.
- **#8880** (SOP approval broker): Another 2K+ line PR implementing group-membership and quorum authorization over the SOP gate chokepoint.

**Underlying needs:** The community is balancing three competing demands: (1) **stability** — crashes and duplicated output are the most urgent pain points; (2) **feature depth** — SOP approval, plugins, and channel consolidation all represent major architectural investments; (3) **documentation quality** — Telegram docs are explicitly called out as wrong (#8810), eroding trust.

---

## Bugs & Stability

**New bugs reported today (2026-07-10/11):**

| Severity | Issue | Summary | Fix PR? |
|----------|-------|---------|---------|
| **S1 — workflow blocked** | [#8934] | Gemini function calls fail because `thought_signature` is dropped from assistant history — blocks all Gemini tool use | None yet |
| **S2 — degraded** | [#8936] | `loop_detector::hash_value` deep-clones entire tool-args JSON tree on every tool call — RSS growth on long turns | None yet |
| **S2 — degraded** | [#8952] | Streamed pre-tool narration is duplicated when turn text has leading/trailing whitespace | None yet |
| **S2 — degraded** | [#8929] | Streamed narration duplicated when final display text is trimmed | None yet |
| **S2 — degraded** | [#8950] | Telegram `setMyCommands` rejected with BOT_COMMANDS_TOO_MUCH when tools+skills+builtins exceed 100 — command menu never registers | None yet |
| **S2 — degraded** | [#8945] | ZeroCode input box blocks macOS text replacements | None yet |
| **S2 — degraded** | [#8944] | ZeroCode transcript mouse copy blocks word-level text selection | None yet |
| **S3 — minor** | (#5514) | Duplicate agent responses on multi-image Telegram sends | None yet |

**Critical regression alert:** The Gemini `thought_signature` bug (#8934) is the most severe new issue — it completely blocks Gemini function calling, a core LLM provider path. No fix PR exists yet.

**Ongoing high-severity:** The `skill-review` SIGSEGV (#8654) remains the highest-priority active bug with a fix PR (#8680) in review. A second crash-path issue (#8936) — the loop_detector deep-clone — creates a compounding risk on tool-heavy turns.

---

## Feature Requests & Roadmap Signals

**Today's new feature requests:**

1. **[#8958]** — ACP agent selection via `?agent=` query param for multi-agent endpoints. **Relevance:** A real third-party client (Thunderbolt from Mozilla Thunderbird) was connected to a self-hosted ZeroClaw gateway, highlighting an interoperability gap. This signals growing external ecosystem interest.

2. **[#8933]** — Add `gen_ai.conversation.id` for cross-turn session correlation in OTel export. **Relevance:** Standardization pressure from observability tooling — aligns with the v0.8.3 observability tracker (#8073).

3. **RFC #8798** — Consolidate `/ws/chat` and `/acp` onto a single wire protocol. This architectural RFC, if accepted, would be a significant v0.9+ project.

**Predictions for next version (v0.8.3):**

- **Definite inclusion:** `uses_memory` flag exposure in CLI and web UI (already merged in #8397 and #8677)
- **Likely inclusion:** Streamed narration deduplication fix (#8952/#8929) — these are polish bugs blocking a stable release
- **Possible inclusion (if fix lands):** Gemini `thought_signature` fix (#8934) — a release without working Gemini would be problematic
- **Unlikely inclusion:** RFC #8798 consolidation — too architectural for a point release

---

## User Feedback Summary

**Real pain points expressed:**

- **Documentation frustration:** Issue #8810 from user `cr3a7ure` explicitly calls the Telegram documentation "wrong" and uses strong language ("slop remains slop") — indicating that docs quality is eroding user trust
- **Setup friction:** User `cr3a7ure` also criticizes "the output of some commands" as unhelpful, suggesting the CLI error messages need improvement
- **Multi-image Telegram UX:** Users sending 2+ images get duplicate agent responses — the longest-standing open bug (#5514, since April) is a persistent annoyance
- **Crash frustration:** The skill-review SIGSEGV (#8654) forces daemon restarts on tool-heavy turns — a clear reliability concern

**Satisfaction signals:**
- External client integration (Thunderbolt using ACP) demonstrates real-world adoption
- Multiple contributors actively submitting PRs (new names: `tzy-17`, `wangmiao0668000666`, `ozpool`) suggests a healthy onboarding experience

---

## Backlog Watch

**Long-unanswered items needing maintainer attention:**

| Issue | Created | Days Open | Type | Risk |
|-------|---------|-----------|------|------|
| [#5514] — Multi-image Telegram bug | 2026-04-08 | **93 days** | Bug | Medium — persistent minor bug |
| [#6563] — ComfyUI as shared media provider | 2026-05-10 | **62 days** | Feature | High — large feature, no PR |
| [#8139] — Session TTL for channels (PR) | 2026-06-22 | **19 days** | Enhancement | High — large PR with no recent review activity |

**PRs needing maintainer attention:**

- **#8638** (skills git-catalog refactor) — Open since July 3, 2.8K lines, labeled `size:L` and `risk:high`. This is a controversial architectural change removing ClawHub support. No maintainer approval/rejection signal in the last 24h.
- **#8139** (session TTL feature) — Open since June 22, labeled `risk:high, size:M`. No recent activity from maintainers. Fallow PRs of this size risk merge conflicts.
- **#8751** (LocalWhisperConfig defaults fix) — Open since July 6, closes a critical config bug (#8718) where zero defaults break Whisper integration. Needs review.

**Recommended actions:**
1. Prioritize review of #8751 (Whisper config) and #8680 (SIGSEGV fix) — both are small, high-severity fixes
2. Issue triage for #5514 (93-day-old Telegram bug) — either commit to a fix timeline or close as known limitation
3. Provide guidance on #8638 — the ClawHub removal is a breaking change that needs a deprecation notice or migration path before the next release

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*