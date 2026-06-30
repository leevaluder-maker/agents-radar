# OpenClaw Ecosystem Digest 2026-06-30

> Issues: 395 | PRs: 500 | Projects covered: 13 | Generated: 2026-06-30 02:30 UTC

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

# OpenClaw Project Digest
**Date: 2026-06-30**

## Today's Overview

OpenClaw demonstrates exceptionally high activity with **395 issues** and **500 pull requests** updated in the last 24 hours, indicating a vibrant open-source project with sustained contributor engagement. The vast majority of issues (85%) remain open and actively discussed, suggesting ongoing development rather than a maintenance-only phase. No new releases were published today, but the project shows continuous improvement through 55 recently merged/closed PRs. The community is highly engaged on challenging topics including session management, authentication providers, and multi-agent reliability, while maintainers are actively reviewing and requesting behavior proofs on incoming patches.

## Releases

**No new releases today.** The project has no publicly listed releases in the monitored period, suggesting that while development is extremely active, the maintainers may be batching changes for a future stable release.

## Project Progress

- **55 pull requests** were merged or closed in the last 24 hours, indicating steady codebase evolution
- Notable fix areas advanced:
  - **Infrastructure/Proxy**: PR #97713 applies enhanced `NO_PROXY` matching to the global undici dispatcher, fixing proxy bypass issues for internal plugin requests (fixes `#95998`)
  - **Discord Slash Commands**: PR #75961, a long-running feature, remains open but ready for maintainer review—adds deployable slash commands
  - **Session Integrity**: PR #95715 preserves user model overrides during compaction (fixes `#95696`)
  - **Configuration Validation**: PR #65359 allows `historyLimit: 0` in GroupChatSchema, fixing a schema mismatch bug (`#65305`)
  - **Automation Infrastructure**: PR #97962 routes DM testing through reusable channel scenario drivers, improving QA reliability

## Community Hot Topics

### Most Active Issues
- **Issue #75** (110 comments, 81 👍) — [Linux/Windows Clawdbot Apps](https://github.com/openclaw/openclaw/issues/75): The highest-engagement item by far. Users are strongly requesting desktop agent apps for non-macOS platforms. The emotional investment and long-standing nature (created Jan 2026) suggests this is a critical feature gap for a significant portion of the user base.

- **Issue #86538** (18 comments) — [Session write-lock timeouts block subagent delivery lanes](https://github.com/openclaw/openclaw/issues/86538): A P1 bug affecting core session concurrency, with clear reproduction steps. The high relative engagement for a technical bug underscores its systemic impact.

- **Issue #94518** (8 👍, 6 comments) — [DeepSeek cache hit rate <10% after 6.x upgrade](https://github.com/openclaw/openclaw/issues/94518): A performance regression that's generating strong user reaction (highest 👍 count outside the platform request). Users are actively affected by increased costs due to poor caching behavior.

- **Issue #80319** (17 comments) — [QA tool-defaults suite conflates Codex-native vs dynamic tools](https://github.com/openclaw/openclaw/issues/80319): Technical debt surfacing in the QA infrastructure, with maintainers clarifying the actual scope of the problem.

### Most Active Pull Requests
- **PR #96106** (Discord reasoning/thinking display): Ready for maintainer look with screenshot proof, addressing a user-visible feature gap
- **PR #75961** (Discord slash command deploy): Long-running (since May 2) but still awaiting maintainer, indicating maintainer bandwidth constraints

**Underlying Needs**: The community is demanding (1) cross-platform desktop support, (2) better session-level concurrency handling, (3) performance consistency across version upgrades, and (4) improved Discord integration for their agent workflows.

## Bugs & Stability

### Critical/Severe (P1)
- **#97877** (NEW) — [empty-error-retry blocked by hadPotentialSideEffects](https://github.com/openclaw/openclaw/issues/97877): Silent terminal failure after any prior tool call when a transient 5xx error occurs. No PR linked yet—fresh bug.
- **#86538** — [Session write-lock timeouts blocking subagent delivery](https://github.com/openclaw/openclaw/issues/86538): High-severity concurrency bug. Open PRs linked for fix.
- **#94518** — [DeepSeek cache hit rate regression](https://github.com/openclaw/openclaw/issues/94518): Performance bug causing increased API costs. No linked fix PR.
- **#81567** — [GPT-4o sessions exit after single response](https://github.com/openclaw/openclaw/issues/81567): Breaks multi-turn tool loops with GPT-4o. Open, needs live reproduction.

### Medium (P2)
- **#96857** — [Tool text outputs degrade to placeholder](https://github.com/openclaw/openclaw/issues/96857): Agents seeing "(see attached image)" instead of actual tool output. Recent report, no fix yet.
- **#82070** — [CLI ~14s cold-start regression](https://github.com/openclaw/openclaw/issues/82070): Startup overhead affecting all CLI commands on Linux since 2026.5.12.
- **#82678** — [`'none'` string truncates assistant responses](https://github.com/openclaw/openclaw/issues/82678): String parsing bug with no `}` terminator causing data loss in tool calls.

### Key Observations
- **Regressions are clustered**: Multiple P1 bugs are "regressions (worked before, now fails)" — the 2026.5.7→2026.5.12→2026.6.x upgrade path appears to have introduced several session-state and auth-provider related issues.
- **No fix PRs exist for most P1 items**: Only a few high-severity bugs have linked PRs, suggesting a fix queue backlog.
- **Stability watch**: #81934 reports multiple critical failures on macOS after updating to 2026.5.12 (Gmail, Dropbox, PDF generation all broke). This suggests broader testing gaps in the release pipeline.

## Feature Requests & Roadmap Signals

### High-Community-Demand Features
- **Linux/Windows Desktop Apps** (#75): Strongest demand signal. Likely to be prioritized given the 110 comments and 81 👍. Prediction: This could enter development within 2-3 release cycles if maintainer bandwidth allows.
- **Skill Author Setup Hooks** (#80213, 7 comments, 4 👍): Desired by plugin developers for post-install configuration scripts.
- **Linear Persistent Workspace Mode for Blind Users** (#82450, 5 comments, 1 👍): An accessibility feature request from a dedicated user with a powerful use-case story. Low volume but high impact for inclusivity.

### Plugin Ecosystem Features
- **Stable Plugin SDK Surface for Skills** (#81913): Multiple plugin authors requesting public SDK contracts rather than accessing internal modules. Signals maturation of the plugin ecosystem.
- **Pre-routing Inbound Hook** (#81061, 7 comments, 3 👍): Architecture-level feature request for channel bridging/proxying use cases.

### Predicted Next-Version Candidates
Based on activity and priority signals:
1. Fixes for the DeepSeek caching regression (#94518)
2. Session write-lock resolution (#86538)
3. Discord slash command deployment (#75961) — very close to merging
4. Potential backport of GPT-4o tool-loop fix (#81567)

## User Feedback Summary

### Positive Sentiments
- **Powerful AI work interface**: User @xiaopinpin-music (Issue #82450) calls OpenClaw "one of the most powerful AI work interfaces I have ever used," citing daily usage for video, browser automation, and AI-assisted workspace management.
- **Broad use cases**: Users are leveraging OpenClaw for real-world productivity (social media, blogging, music research) and technical workflows (browser automation, DevOps).

### Pain Points
- **Upgrade anxiety**: Multiple users report "everything worked before, then I updated" — the 2026.5.12 and 2026.6.x upgrades seem to have introduced regressions that erode trust.
- **Session reliability**: Several reports of "silent drops" (Telegram #80520, followup agent #80700) where messages disappear without user notification. This is the worst failure mode for chat-based agents.
- **Cross-platform gaps**: Linux and Windows users feel left behind compared to macOS first-class support (#75, #82070).
- **Telegram group interaction issues**: Bot reply context loss (#82002) and silent message drops (#80520) are specific pain points for Telegram power users.

### Dissatisfaction Signals
- Users are filing issues showing costs increasing (#94518 - cache misses, #95121 - timeouts on tiny replies)
- The "off-meta tidepool" and "platinum hermit" issue ratings suggest some reports are being de-prioritized relative to their user impact

## Backlog Watch

### Issues Needing Maintainer Attention
- **Issue #75** (Jan 2026, 110 comments): Linux/Windows apps. Very old, very active. Needs a product decision or roadmap acknowledgment.
- **Issue #77642** (May 5, 2026): [Duplicate answers + synthetic errors regression](https://github.com/openclaw/openclaw/issues/77642). P1 with 5 comments but stale since May despite being a "5.3 regression."
- **Issue #80040** (May 10, 2026): Triple cascading failure (OAuth + tool execution + context loss). Open for 7 weeks with no resolution path visible.
- **Issue #82070** (May 15, 2026): 14-second CLI cold start. A month old without fix.

### Stale PRs Requiring Review
- **PR #75961** (May 2): [Discord slash commands](https://github.com/openclaw/openclaw/pull/75961) — "ready for maintainer look" for nearly 60 days.
- **PR #65359** (Apr 12): [historyLimit: 0 fix](https://github.com/openclaw/openclaw/pull/65359) — Ready for maintainer for 79 days.
- **PR #61775** (Apr 6): [Makefile enhancement](https://github.com/openclaw/openclaw/pull/61775) — Ready for 85 days.

### Risk Assessment
The combination of (1) 335 open active issues, (2) 445 open PRs, (3) multiple P1 bugs without linked fixes, and (4) PRs waiting 2-3 months for review suggests maintainer bandwidth is a growing constraint. The project is healthy but may need additional committers or process changes (e.g., automated triage, community maintainer program) to sustain the current velocity without accumulating debt.

---

## Cross-Ecosystem Comparison

**Cross-Project Ecosystem Intelligence Report**
**Covering: OpenClaw, NanoBot, Hermes Agent, PicoClaw, NanoClaw, NullClaw, IronClaw, LobsterAI, CoPaw, ZeroClaw**
**Date Range: 2026-06-30**

---

## 1. Ecosystem Overview

The open-source personal AI agent ecosystem is experiencing explosive growth, driven by the convergence of large-language-model commoditization, multi-channel messaging requirements, and demand for autonomous tool use. On June 30, 2026, the monitored projects collectively processed over **630 issues and 750 pull requests** in 24 hours, indicating a vibrant, fast-moving landscape. The market is bifurcating into two architectural approaches: monolithic "AI operating systems" (OpenClaw, ZeroClaw, IronClaw) that provide full desktop-to-agent experiences, and lightweight, embeddable runtime agents (NanoBot, NullClaw, NanoClaw) optimized for specific workflows. A shared struggle across all projects is **maintainer bandwidth constraints**, with multiple critical bugs and feature requests remaining unaddressed for weeks despite high community activity. The ecosystem is maturing toward platform stability, but the velocity of LLM provider changes—especially around reasoning models, streaming tool calls, and caching—continues to outpace project release cycles.

---

## 2. Activity Comparison

| Project | Issues Updated/Active | PRs Updated/Open | Release Status | Health Score | Core Focus |
|---|---|---|---|---|---|
| OpenClaw | 395 / 335 | 500 / 445 | No release | 🟡 High velocity, stretched maintainers | Full-stack AI OS (desktop, multi-agent) |
| NanoBot | 7 / 4 | 33 / 24 | No release | 🟢 Responsive, focused | Lightweight runtime, WebUI, multi-channel |
| Hermes Agent | 50 / 47 | 50 / 46 | No release | 🟡 Active, security bugs P1 | Multi-gateway agent (Telegram, Slack, Desktop) |
| ZeroClaw | 50 / 43 | 50 / 41 | Pre-v0.8.3 | 🟡 Heavy integration, blocked bugs | WASM plugins, A2A discovery, channels |
| IronClaw | 14 / 10 | 50 / 30 | No release | 🟢 Stabilization phase | "Reborn" engine, WebUI v2, enterprise RBAC |
| CoPaw | 31 / 19 | 50 / 24 | No release | 🟢 Productive, 2.0.0 prep | AgentScope 2.0, Chinese market, plugins |
| LobsterAI | 8 / 8 | 40 / 1 | **v2026.6.29** | 🟢 Release-ready | Desktop agent, Cowork UI, plugin preinstalls |
| NanoClaw | 1 / 1 | 7 / 5 | No release | 🟡 Narrow, Discord focus | Discord/Slack adapters, voice-notify |
| NullClaw | 1 / 1 | 4 / 3 | No release | 🟢 Steady, small scope | CLI REPL, streaming tool calls |
| PicoClaw | 3 / 3 | 3 / 3 | v0.2.9 | 🟡 Low throughput, stale PRs | Lightweight, DeltaChat, enterprise costs |

**Key Observations:**
- **OpenClaw dominates** in raw volume but shows signs of review bottleneck (445 open PRs, 335 open issues).
- **LobsterAI** is the only project to ship a release today, with disciplined merge discipline (39/40 PRs closed).
- **ZeroClaw** has the most blocked critical bugs (4 P1s), signaling integration risk before v0.8.3.
- **NanoBot** and **IronClaw** show the best bug-to-fix cycle (same-day PRs for critical issues).

---

## 3. OpenClaw's Position

**Advantages vs. Peers:**
- **Community size**: 395 daily issues + 500 PRs—**orders of magnitude larger** than any peer (next is Hermes Agent at 50/50). This creates the richest feedback loop and fastest bug discovery.
- **Feature breadth**: No other project covers desktop apps, Discord integration, multi-agent reliability, and plugin SDK simultaneously. This makes OpenClaw the "platform of record" for AI agent developers.
- **Technical depth**: Issues like session write-lock concurrency (#86538), DeepSeek caching regression (#94518), and GPT-4o tool loop (#81567) are problems that only emerge at very high usage scales.

**Technical Approach Differences:**
- Unlike NanoBot's lightweight runtime or NullClaw's CLI-first design, OpenClaw is building a **full operating system abstraction** (session management, auth providers, proxy infrastructure, plugin SDK). This creates higher complexity but also higher ceiling.
- OpenClaw's **monorepo/community-driven model** differs from IronClaw's more structured, team-led development (fewer but more targeted PRs).

**Community Size Comparison:**
- OpenClaw's active daily engagement (395 issues, 500 PRs) is ~8x Hermes Agent, ~10x CoPaw, ~50x NanoBot. However, OpenClaw's maintainer bandwidth appears tighter—PRs wait 60-85 days for review, while Hermes Agent, NanoBot, and IronClaw respond within hours or days.

**Risk**: Maintainer bottleneck could cause contributor fatigue. The 85% open issue rate and 89% open PR rate suggest the project is **growing faster than its governance capacity**.

---

## 4. Shared Technical Focus Areas

The following requirements emerged independently across multiple projects, indicating industry-wide pain points:

| Requirement | Affected Projects | Specific Signals |
|---|---|---|
| **Streaming tool call reliability** | OpenClaw (#81567 GPT-4o loop), NullClaw (#971 native tools during SSE), ZeroClaw (#5600 kimi-code streaming 400 error) | Models increasingly require streaming, but implementations break multi-turn tool orchestrations. |
| **LLM provider abstraction hardening** | NanoBot (#4595 tool ID corruption), Hermes Agent (#55276 reasoning_effort silent drop), CoPaw (#5573 DeepSeek thinking mode), ZeroClaw (#8054 tool availability mismatch) | Every new provider (DeepSeek, Kimi, llama.cpp) introduces schema or behavior edge cases. |
| **Context & cache optimization** | OpenClaw (#94518 DeepSeek cache <10%), CoPaw (#3891 DeepSeek cache hit rate 95%), LobsterAI (#2121 token waste), IronClaw (#5149 progressive tool disclosure) | API costs dominate user complaints; caching and prompt compression are top engineering priorities. |
| **Multi-channel message size handling** | Hermes Agent (#55309 lone surrogate Telegram), CoPaw (#5561 Feishu long messages to file), ZeroClaw (#8410 no-reply outcome for tasks), LobsterAI (#1386 share truncation) | Channels (Telegram, Feishu, WeChat) impose content length limits; agents must gracefully degrade or split. |
| **Cross-platform desktop parity** | OpenClaw (#75 Linux/Windows apps), Hermes Agent (#27282 macOS TUI exit), ZeroClaw (#7800 macOS keybinding confusion) | macOS is the default target; Linux/Windows users feel left behind. |
| **Security: credential redaction & sandboxing** | NanoBot (#4594 shell path extraction after `=`, #4584 MCP credential redaction), Hermes Agent (#20591 credential pool stale os.environ), CoPaw (#5621 sandbox docs), IronClaw (#5425 multi-user RBAC) | As agents gain file/tool access, credential leakage and escape containment are systemic risks. |

---

## 5. Differentiation Analysis

| Dimension | OpenClaw | NanoBot | Hermes Agent | ZeroClaw | IronClaw |
|---|---|---|---|---|---|
| **Target User** | Power users, multi-agent developers | Cost-conscious tinkerers, enterprise ops | Telegram/WhatsApp-first users | Plugin developers, DIY agents | QA teams, enterprise deployments |
| **Architecture** | Monolithic AI OS, full-stack | Lightweight runtime, WebUI-first | Multi-gateway proxy | WASM plugins + A2A | Engine (Reborn) + WebUI v2 |
| **Key Differentiator** | Largest community, deepest feature set | Fastest bug-to-fix cycle, token optimization | Telegram/WhatsApp reliability | WASM sandboxing, provider flexibility | Enterprise RBAC, test infrastructure |
| **Risk Profile** | Maintainer bottleneck, regression clusters | Small team, limited feature scope | macOS/persistence bugs | Blocked critical bugs pre-release | Integration complexity (2.0 migration) |
| **Release Cadence** | Unclear (batched) | Regular (implied) | Infrequent | Pre-v0.8.3 milestone | Unknown (stabilization) |

**Notable Niches:**
- **NanoClaw** focuses on Discord/Slack socket adapters—a specific platform gap.
- **NullClaw** targets CLI purists with REPL improvements.
- **PicoClaw** leans toward privacy-centric protocols (DeltaChat, SimpleX, Tox).
- **LobsterAI** is the only project with Chinese-optimized channels (WeChat, DingTalk, Feishu, QQ) and a release pipeline.

---

## 6. Community Momentum & Maturity

**Tier 1 – Rapidly Iterating (High activity, high risk):**
- **OpenClaw**: 395 daily issues, 500 PRs—raw momentum is unmatched, but the backlog (335 open issues, 445 open PRs) signals a project straining under its own growth. Regression clusters from 2026.5.7→2026.6.x upgrades erode trust.
- **ZeroClaw**: 50 issues + 50 PRs daily, but 4 blocked P1 bugs threaten the v0.8.3 milestone. High ambition (WASM, A2A) but integration risk.

**Tier 2 – Stabilizing (High activity, improving quality):**
- **IronClaw**: 14 issues, 50 PRs—controlled, team-led. Focus on porting legacy tests and hardening Reborn engine. Lowest risk profile among high-activity projects.
- **CoPaw**: 31 issues, 50 PRs—productive cycle with 52% PR close rate. Approaching 2.0.0 release with documentation updates and security docs.
- **LobsterAI**: Only 8 issues, but shipped a release with 39/40 PRs closed. Most disciplined release process in the ecosystem.

**Tier 3 – Steady (Moderate activity, narrow focus):**
- **NanoBot**: 7 issues, 33 PRs—responsive maintainers fix critical bugs same-day. Small but healthy.
- **Hermes Agent**: 50 issues, 50 PRs—active community but P1 bugs (credential pool, TUI exit) remain unfixed for 44–55 days. Maintainer gaps are visible.
- **NanoClaw**: 1 issue, 7 PRs—Discord-focused, moderate activity.
- **NullClaw**: 1 issue, 4 PRs—CLI-focused, low volume.

**Tier 4 – Low Activity:**
- **PicoClaw** (3 issues, 3 PRs—stale DeltaChat PR at 22 days, no maintainer response).
- **TinyClaw, Moltis, ZeptoClaw**: Zero activity in 24 hours.

---

## 7. Trend Signals

**For AI Agent Developers:**

1. **The "Streaming Tax" is real.** Every project that supports tool calls during streaming (NullClaw, ZeroClaw) is encountering provider-specific bugs. Developers should expect to invest heavily in streaming tool orchestration—it is not yet standardized across LLM backends.

2. **Provider diversity is a double-edged sword.** Users demand multiple providers (OpenAI, DeepSeek, Kimi, Anthropic, llama.cpp), but each new provider introduces schema edge cases. Projects that abstract provider differences (like OpenClaw's plugin SDK) will win over those hardcoding per-provider logic.

3. **Cache optimization is the new performance frontier.** DeepSeek cache miss costs (4x-10x premium) are driving dedicated engineering at OpenClaw, CoPaw, and IronClaw. Developers building cost-sensitive agents should prioritize prefix caching, context compaction, and progressive tool disclosure.

4. **Channel reliability > channel breadth.** Telegram, Feishu, and WeChat are the most buggy channels across multiple projects. Users will tolerate fewer channels if the ones that exist are reliable. Hermes Agent's Telegram issues and CoPaw's Feishu problems show that "just add a channel" is not a sustainable strategy.

5. **Security is catching up to adoption.** Credential leakage (NanoBot, Hermes Agent), symlink-follow attacks (NanoClaw), and missing sandboxing (CoPaw adding docs, IronClaw adding RBAC) indicate that the industry is transitioning from "move fast" to "secure the stack." Expect sandbox documentation and credential redaction to become baseline requirements, not differentiators.

6. **Desktop parity remains unsolved.** The most-upvoted feature across the ecosystem is OpenClaw's Linux/Windows desktop app request (#75, 110 comments, 81 👍). Developers targeting power users cannot assume macOS-only environments.

7. **Maintainer bandwidth is the ecosystem's single point of failure.** OpenClaw (445 open PRs), Hermes Agent (P1 bugs unfixed for 55 days), and PicoClaw (22-day stale PR) all show that community enthusiasm exceeds maintainer capacity. **The next infrastructure trend should be community triage programs, automated regression detection, and release automation**—not more features.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

**Project Name:** NanoBot  
**Date:** 2026-06-30  
**Source Data:** GitHub (github.com/HKUDS/nanobot)

---

### 1. Today’s Overview

NanoBot is in a period of **high activity and strong community engagement**, with **33 pull requests** updated in the last 24 hours—an unusually high number that suggests a maintainer push or major feature integration day. **24 PRs remain open**, with **9 merged or closed**, indicating healthy throughput. **7 issues** were updated in the last 24 hours, with **3 closed and 4 active**. Notably, **0 new releases** were tagged today, meaning all this activity is targeted at the development branch. The project is seeing contributions across multiple domains: security (credential redaction), performance (context pruning), platform support (WhatsApp, GitHub Enterprise), and bug fixes. Community energy is high, but the volume of open PRs (24) suggests a potential **review bottleneck** that could slow momentum.

### 2. Releases

**No new releases today.**  
The latest stable release remains unreferenced. All activity is in the `main` or feature branches.

### 3. Project Progress

**Merged/Closed PRs (9 total):**

| PR | Focus | Summary |
|----|-------|---------|
| [#4600](https://github.com/HKUDS/nanobot/pull/4600) | WebUI | Refined prompt minimap rail – moved to left, compact Codex-like styling |
| [#4502](https://github.com/HKUDS/nanobot/pull/4502) | Infrastructure | Added gateway webhook triggers for inbound event-driven workflows |
| [#4597](https://github.com/HKUDS/nanobot/pull/4597) | Test/Chore | Closed as test issue (no impact) |

**Key closed issues:**
- [#660](https://github.com/HKUDS/nanobot/issues/660) – "Ultra-lightweight" branding debate resolved; dependency on Node.js acknowledged
- [#4222](https://github.com/HKUDS/nanobot/issues/4222) – `max_messages` truncation bug fixed (prompt caching invalidation)

**Notable feature advances in open/merged PRs:**
- **Context optimization** ([#4581](https://github.com/HKUDS/nanobot/pull/4581), [#4588](https://github.com/HKUDS/nanobot/pull/4588)): Aggressive token reduction via output compaction and pruning
- **Typed runtime events** ([#4590](https://github.com/HKUDS/nanobot/pull/4590)): Structured outbound events for UI and bus reliability
- **Session-bound local triggers** ([#4591](https://github.com/HKUDS/nanobot/pull/4591)): Workspace-scoped trigger system for workflows

### 4. Community Hot Topics

**Most Active Issues (by comments & reactions):**

1. **[#660](https://github.com/HKUDS/nanobot/issues/660)** [CLOSED] *“Ultra-lightweight” branding vs. Node.js dependency*  
   - **15 comments, 5 👍**  
   - *Analysis:* Strong community pushback on marketing language. Users value **honest resource labeling**. Closed with likely documentation update, but sentiment may linger.

2. **[#4419](https://github.com/HKUDS/nanobot/issues/4419)** [OPEN] *Automatic reasoning effort escalation*  
   - **4 comments**  
   - *Analysis:* Users want **adaptive compute** for reasoning models—start cheap, escalate when stuck. Growing demand given proliferation of deep-thinking LLMs.

3. **[#4595](https://github.com/HKUDS/nanobot/issues/4595)** [OPEN] *`apply_final_call_ids` overwriting correct tool call IDs*  
   - **New today, 0 comments** but linked to [#4596](https://github.com/HKUDS/nanobot/pull/4596) which has a fix  
   - *Analysis:* High severity, quick response from community (PR submitted same day). Shows **healthy bug-to-fix cycle**.

**Most Active PRs (by comment count):**

- [#4596](https://github.com/HKUDS/nanobot/pull/4596) (fix for #4595) – Streaming tool call ID corruption
- [#4594](https://github.com/HKUDS/nanobot/pull/4594) – Shell path extraction after `=` (security boundary fix)
- [#4601](https://github.com/HKUDS/nanobot/pull/4601) – WhatsApp read receipts (new channel feature)

**Underlying needs:** Users demand **honest documentation**, **session reliability** (especially streaming), **cross-platform polish** (WhatsApp, enterprise providers), and **cost-efficiency** (token reduction).

### 5. Bugs & Stability

**Bugs reported today (2026-06-30):**

| Severity | Issue | PR Fix Exists? | Summary |
|----------|-------|----------------|---------|
| 🔴 **Critical** | [#4595](https://github.com/HKUDS/nanobot/issues/4595) | ✅ [#4596](https://github.com/HKUDS/nanobot/pull/4596) | `apply_final_call_ids` corrupts tool_call IDs for non-file-edit tools. **Permanent session poisoning.** Duplicate IDs break downstream agents. Fixed in same day. |
| 🟠 **High** | [#4592](https://github.com/HKUDS/nanobot/issues/4592) | ✅ [#4594](https://github.com/HKUDS/nanobot/pull/4594) | ExecTool path extraction fails after `=` (e.g., `--output=/etc/passwd`). **Security bypass** of workspace containment. Fix ready. |
| 🟡 **Medium** | [#4599](https://github.com/HKUDS/nanobot/issues/4599) | ✅ [#4602](https://github.com/HKUDS/nanobot/pull/4602) | Linux install script crashes in TUI. Root cause: non-interactive terminal (e.g., `curl | sh`). Fix skips wizard gracefully. |
| ⚪ **Low** | [#4597](https://github.com/HKUDS/nanobot/issues/4597) | N/A | Test/placeholder issue. No impact. |

**Summary:** Today’s bug intake is **above average in severity** (critical + high), but the project is responding **extremely fast**—all fixes have matching PRs filed within hours. This indicates a **responsive maintainer team or a trusted contributor network**.

### 6. Feature Requests & Roadmap Signals

**Features requested today or recently gaining traction:**

| Feature | Issue/PR | Likelihood for Next Release | Reasoning |
|---------|----------|----------------------------|-----------|
| **Automatic reasoning effort escalation** | [#4419](https://github.com/HKUDS/nanobot/issues/4419) | 🟢 High | Growing provider support; fits NanoBot's "adaptive agent" narrative |
| **GitHub Copilot Enterprise/GHE support** | [#4598](https://github.com/HKUDS/nanobot/pull/4598) | 🟢 High | PR already open; enterprise users are a key demographic |
| **WhatsApp read receipts (blue double-check)** | [#4601](https://github.com/HKUDS/nanobot/pull/4601) | 🟢 High | Simple, well-scoped PR; improves user experience |
| **Provider-scoped proxy config** | [#4578](https://github.com/HKUDS/nanobot/pull/4578) | 🟢 High | Enterprise/corporate network necessity |
| **Dream duplicate skill guard** | [#4554](https://github.com/HKUDS/nanobot/pull/4554) | 🟡 Medium | Prevents memory bloat; important for self-improving agents |
| **Markdown session export** | [#4587](https://github.com/HKUDS/nanobot/pull/4587) | 🟡 Medium | Quality-of-life; pending WebUI polish |
| **Context optimization (pruning/compaction)** | [#4581](https://github.com/HKUDS/nanobot/pull/4581), [#4588](https://github.com/HKUDS/nanobot/pull/4588) | 🟢 High | Directly reduces costs; community strongly positive |

**Prediction:** The **next release** will likely include the context optimization stack, GitHub Copilot enterprise support, provider proxy, and the WhatsApp read receipts. Reasoning escalation may slip to the release after.

### 7. User Feedback Summary

**Pain Points (explicit or implicit from issues):**
- **Honesty about dependencies:** Issue #660 shows users felt misled by "ultra-lightweight" claims when Node.js is required. **Suggestion:** Update README to clarify minimal vs. typical footprint.
- **Session reliability:** Bug [#4222](https://github.com/HKUDS/nanobot/issues/4222) (prompt caching invalidation) and [#4595](https://github.com/HKUDS/nanobot/issues/4595) (tool ID poisoning) suggest **context management is fragile** under load or streaming. Users are frustrated by "permanent session poisoning."
- **Install friction:** [#4599](https://github.com/HKUDS/nanobot/issues/4599) highlights that **`curl | sh` patterns** are not gracefully handled. This is a standard pattern in the AI/DevOps community; fixing it removes a barrier to adoption.

**Use Cases (positive signals):**
- **Cost-conscious users:** Two large PRs on context optimization (tokens → cost) indicate that **budget-aware deployment is a core use case**. Many users are running NanoBot on personal hardware or under API budgets.
- **Enterprise integration:** Provider proxy, GHE support, and webhook triggers point to **professional/team deployments**.
- **Multi-platform agents:** WhatsApp channel improvements show demand for **non-LLM-native interfaces**.

**Sentiment:** Generally positive but **demanding**. The community has high standards for UI polish, real-time reliability, and honest marketing. Users are willing to contribute fixes (fast PR turnaround on critical bugs), suggesting a **strong, technical user base**.

### 8. Backlog Watch

**Issues and PRs needing maintainer attention (aging or high-impact):**

| Item | Age | Risk | Notes |
|------|-----|------|-------|
| [#4293](https://github.com/HKUDS/nanobot/pull/4293) *Subagent result injection* | 19 days open | 🟡 Medium | Blocks cron/subagent interactions. No maintainer response visible. |
| [#4554](https://github.com/HKUDS/nanobot/pull/4554) *Dream duplicate skill guard* | 4 days open | 🟡 Medium | Memory hygiene; could degrade Dream reliability over time. |
| [#4583](https://github.com/HKUDS/nanobot/pull/4583) *Null section migration guard* | 1 day open | 🟢 Low | Minor config robustness; should be quick to review. |
| [#4577](https://github.com/HKUDS/nanobot/pull/4577) *bwrap sandbox mounts test* | 2 days open | 🟢 Low | Test-only; no functional impact, but sandbox security is important. |
| [#4584](https://github.com/HKUDS/nanobot/pull/4584) *MCP credential redaction* | 1 day open | 🔴 **Watch** | **Security-critical.** Prevents credential leakage in logs. Should be prioritized over cosmetic PRs. |

**Summary:** The backlog is **not severe** (no items older than 3 weeks). The main concern is **review capacity**—24 open PRs is a lot, and security-critical items ([#4584](https://github.com/HKUDS/nanobot/pull/4584), [#4594](https://github.com/HKUDS/nanobot/pull/4594)) should be merged before feature work. The project is healthy but could benefit from **dedicated review days** to reduce the open PR count.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

# Hermes Agent Project Digest — 2026-06-30

## Today's Overview

High activity across the Hermes Agent project, with 50 issues and 50 PRs updated in the last 24 hours (47 open issues, 46 open PRs) — indicating a sustained development pace with a strong community contribution stream. The bulk of activity centers on bug fixes, security hardening, and quality-of-life improvements across gateways (Telegram, WhatsApp, Slack), the Desktop app, and core agent infrastructure. No new releases were published today, but multiple high-severity bugs from the past week (large-integer coercion, credential leakage, WebSocket OOM risks) now have fix PRs in flight. Maintainer bandwidth appears stretched, with several important feature requests and bug reports accumulating comments but lacking maintainer responses.

## Releases

No new releases on 2026-06-30.

## Project Progress

**4 PRs merged/closed today:**

- **#55363 [`fix(desktop)`](https://github.com/NousResearch/hermes-agent/pull/55363)** — Refresh sessions on profile scope changes; avoids duplicate refresh on initial gateway-open load. Merged.
- **#55355 [`fix(homeassistant)`](https://github.com/NousResearch/hermes-agent/pull/55355)** — Bound REST error response reads in Home Assistant plugin to prevent unbounded memory usage. Merged.
- **#54911 [`refactor(docker)`](https://github.com/NousResearch/hermes-agent/pull/54911)** — Unify Docker CI between architectures, use GHA cache everywhere. Merged.
- **#52570 [`add timings report to CI`](https://github.com/NousResearch/hermes-agent/pull/52570)** — New CI feature adding timing reports against main. Merged.

Notable open PRs that advanced substantive features:
- **#55364 [`Embedded agent browser`](https://github.com/NousResearch/hermes-agent/pull/55364)** — Adds browser pane for agent observe/control with element inspector. Large feature; no comments yet.
- **#55315 [`Preserve large integers in tool-argument coercion`](https://github.com/NousResearch/hermes-agent/pull/55315)** — Fixes critical float-rounding bug that corrupted Discord/Telegram IDs >2^53.
- **#55345 [`WebSocket message size limit`](https://github.com/NousResearch/hermes-agent/pull/55345)** — Security fix preventing OOM crashes from oversized messages.
- **#55352 [`Credential redaction in debug logging`](https://github.com/NousResearch/hermes-agent/pull/55352)** — Security fix preventing credential leakage to logs.

## Community Hot Topics

### Most Commented Issues

**[#27282 — TUI gateway exits mid-turn with stdin EOF (10 comments)](https://github.com/NousResearch/hermes-agent/issues/27282)**
Apple Silicon (macOS) users experiencing TUI session drops with `reason=stdin EOF (TUI closed the command pipe)`. Author notes this is specific to built-in memory (not byterover), suggesting a general variant of #14036. Mac-first agent users are disproportionately affected; no fix PR identified yet.

**[#21172 — First-class Loop Contract for cron-backed agents (6 comments)](https://github.com/NousResearch/hermes-agent/issues/21172)**
Feature request for declarative budget/stop/refresh/scope controls on persistent cron-backed agent loops. Linked to Boris Cherny's (Head of Claude Code) public statements about persistent vs one-shot agent sessions. Signals growing demand for production-grade agent scheduling.

**[#17565 — Configurable Temperature Parameter (5 comments, 6 👍)](https://github.com/NousResearch/hermes-agent/issues/17565)**
Users reporting severe hallucinations because temperature is hardcoded. The 6 upvotes make this the most-upvoted open feature request in the top 30. Not yet addressed in any open PR.

### Most Upvoted

**[#17565 — Temperature parameter (6 👍)](https://github.com/NousResearch/hermes-agent/issues/17565)**
**[#50775 — Telegram macOS ghosting/double-text (4 👍)](https://github.com/NousResearch/hermes-agent/issues/50775)**
**[#49289 — Deleted profile icon persists in Desktop (2 👍)](https://github.com/NousResearch/hermes-agent/issues/49289)**

**Analysis:** Community sentiment centers on three themes: (1) **agent reasoning quality** — users need temperature control to combat hallucinations, (2) **Desktop UX polish** — visual glitches in profile management and Telegram streaming erode confidence, (3) **persistent agent operations** — demand for cron/scheduling infrastructure is growing.

## Bugs & Stability

### Critical/Severe (P1)

- **[#20591 — Credential pool reads stale os.environ](https://github.com/NousResearch/hermes-agent/issues/20591)** — P1, `sweeper:risk-security-boundary`. Code doesn't match documented behavior; `.env` is supposed to override parent-process env vars but doesn't. Security boundary risk. No fix PR.

- **[#27282 — TUI gateway exits mid-turn on macOS](https://github.com/NousResearch/hermes-agent/issues/27282)** — P1, `sweeper:risk-session-state`. Session-breaking for macOS TUI users. No fix PR.

### High/Important (P2)

- **[#55314 — Tool-argument coercion rounds large integers through float](https://github.com/NousResearch/hermes-agent/issues/55314)** — **Fix PR #55315 open.** Corrupts Discord/Telegram IDs >9,007,199,254,740,991. Fix by original reporter is in review.
- **[#55345 — WebSocket OOM crash from oversized messages](https://github.com/NousResearch/hermes-agent/pull/55345)** — **Fix PR #55345 open.** 16 MiB limit being added; targets #53142.
- **[#55309 — Lone surrogate in Telegram reply crashes delivery](https://github.com/NousResearch/hermes-agent/issues/55309)** — `sweeper:risk-message-delivery`. Model response raw SDK content not sanitized before Telegram API call. No fix PR.
- **[#55305 — ZFS SQLite WAL corruption with multiple connections](https://github.com/NousResearch/hermes-agent/issues/55305)** — Session-breaking for users on ZFS filesystems (TrueNAS). `apply_wal_with_fallback()` handling needed. No fix PR.
- **[#55130 — Dashboard 500s with basic auth only + non-loopback bind](https://github.com/NousResearch/hermes-agent/issues/55130)** — Dashboard completely unreachable for this configuration. No fix PR.
- **[#55276 — reasoning_effort silently dropped for custom/zai providers](https://github.com/NousResearch/hermes-agent/issues/55276)** — Users paying for reasoning models aren't getting reasoning. No fix PR.
- **[#32207 — /clear command freezes terminal on Windows/WSL](https://github.com/NousResearch/hermes-agent/issues/32207)** — Terminal freeze forces new session. No fix PR.

## Feature Requests & Roadmap Signals

### Likely in Next Release

- **Large-integer coercion fix** (#55314 → PR #55315) — Critical for Discord/Telegram gateway reliability. Already submitted by the bug reporter, likely merges quickly.
- **WebSocket size limit** (#53142 → PR #55345) — Security fix, already open, targets OOM vulnerability.
- **Credential redaction in logs** (#53143 → PR #55352) — Security fix, straightforward, likely merges.
- **Bounded error-body reads across gateways** (PRs #55362, #55357, #55354, #55355) — Series of defense-in-depth fixes submitted today by `ooiuii`. Momentum suggests merging.

### Possible in Next Release (Based on Active PRs)

- **Embedded agent browser with element inspector** (PR #55364) — Large feature, no comments yet, but author `7eusy` submitted today. If maintainer bandwidth permits.
- **Kanban worker lanes with Codex CLI adapter** (PR #29777) — Long-pending (since May 21). Significant infrastructure change; momentum uncertain.
- **Dashboard session stats performance improvement** (PR #48932) — Single GROUP BY query replacing O(N) loop. Open since June 19.

### Predictive — What the Data Suggests

The **temperature configuration feature** (#17565, 6 👍) has the strongest user demand signal among unimplemented features. Combined with the reasoning_effort being silently dropped (#55276), there is a clear **emergent need for granular model configuration control**. Expect a governance/settings abstraction to appear in the 0.17–0.18 timeframe.

The **persistent cron-backed agents** discussion (#21172) aligns with Boris Cherny's commentary on agent workflows shifting from one-shot to persistent. This is a strategic signal — don't expect immediate implementation, but it points toward the long-term product direction.

## User Feedback Summary

### Pain Points

1. **macOS TUI instability** (#27282): "gateway exits mid-turn" — core tooling unreliable on Apple Silicon.
2. **Telegram message quality degradation** (#53632, #55265, #50775): Tables broken in cron deliveries, ghosting/double-text on macOS client, forum-topic routing regression — Telegram channel remains the most buggy platform.
3. **Windows/WSL terminal freezes** (#32207): `/clear` command completely breaks the terminal.
4. **Agent ignores rules in memory/skills** (#49764): "Hermes Agent has rules in two places... but reliably ignores them." User frustration with rule adherence is a recurring theme.
5. **SSH tunnel settings not persisted** (#32626): Desktop app forgets SSH configuration on restart.

### Satisfaction Signals

- **High community engagement** — 50+ issues and PRs updated today alone; users are actively contributing fixes (witness `ooiuii`'s series of bounded-read PRs).
- **Rapid bug-to-fix turnaround** — #55314 (large integers) was filed and has a fix PR the same day. #55345 (WebSocket OOM) has a fix within hours.
- **Feature contributions accepted** — New chat width setting (#55287), stable project collapse icon (#55366), and timing reports in CI (#52570) all merged or active.

### Dissatisfaction Signals

- **Maintainer response gaps** — #17565 (temperature, 6 👍, open since April 29) has no maintainer comment. #21172 (loop contract, open since May 7) silent. #25083 (protected skills) silent since May 13.
- **Unresolved P1 bugs** — #20591 (credential pool) and #27282 (TUI exit) remain open without fix PRs despite their severity labels.

## Backlog Watch

### Issues Needing Maintainer Attention

1. **[#17565 — Configurable Temperature](https://github.com/NousResearch/hermes-agent/issues/17565)**
   - **Created:** 2026-04-29 (63 days ago)
   - **Signal:** 6 👍, 5 comments
   - **Status:** No maintainer response. Hardcoded temperature causing hallucinations. Highest-upvoted unimplemented feature.

2. **[#21172 — First-class Loop Contract](https://github.com/NousResearch/hermes-agent/issues/21172)**
   - **Created:** 2026-05-07 (54 days ago)
   - **Signal:** 6 comments, references CEO-level product direction
   - **Status:** No maintainer response. Strategic product feature.

3. **[#25083 — Immutable/protected skills](https://github.com/NousResearch/hermes-agent/issues/25083)**
   - **Created:** 2026-05-13 (48 days ago)
   - **Signal:** 4 comments
   - **Status:** No maintainer response. Governance/safety feature.

4. **[#20591 — Credential pool stale os.environ (P1)](https://github.com/NousResearch/hermes-agent/issues/20591)**
   - **Created:** 2026-05-06 (55 days ago)
   - **Signal:** Security boundary risk, P1 label
   - **Status:** No fix PR. Code doesn't match documented behavior.

5. **[#27282 — TUI exit mid-turn on macOS (P1)](https://github.com/NousResearch/hermes-agent/issues/27282)**
   - **Created:** 2026-05-17 (44 days ago)
   - **Signal:** Session-breaking for macOS users, P1 label
   - **Status:** No fix PR. 10 comments indicates community discussion but no resolution.

### PRs Needing Attention

- **[#29777 — Kanban worker lanes + Codex CLI adapter](https://github.com/NousResearch/hermes-agent/pull/29777)**
  - **Created:** 2026-05-21 (40 days ago)
  - **Signal:** Substantial infrastructure change; no activity in 40 days
  - **Risk:** Stale PR; may require rebase or maintainer decision

- **[#48932 — Dashboard session stats performance](https://github.com/NousResearch/hermes-agent/pull/48932)**
  - **Created:** 2026-06-19 (11 days ago)
  - **Signal:** Clean performance improvement; no maintainer review
  - **Risk:** Low-priority but easy win

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

Here is the structured project digest for PicoClaw, based on the provided GitHub data for **2026-06-30**.

---

### PicoClaw Project Digest — 2026-06-30

#### 1. Today's Overview
Project activity remains moderate but healthy, with three Issues and three Pull Requests receiving updates in the last 24 hours. No releases were published today, and the backlog continues to show signs of slow merging of features. The project appears to be in a steady state of feature development and bug fixing, though maintainer response time for both stale Issues and open PRs could be improved. While no major breakthroughs occurred today, the introduction of AWS Bedrock prompt caching signals a focus on enterprise-grade performance optimization.

#### 2. Releases
**No new releases** published today. The latest release remains at **v0.2.9** (as referenced in Issue #3090). The next release may include the pending DeltaChat gateway and token usage features from open PRs.

#### 3. Project Progress
- **No PRs were merged or closed today.** All three open PRs remained active but unmerged:
  - **#3063 (feat: add DeltaChat gateway)** — A new feature adding a DeltaChat messaging gateway, pending review.
  - **#3163 (feat(bedrock): leverage Converse prompt caching)** — Adds cost-saving prompt caching for AWS Bedrock users.
  - **#3156 (feat(pico): emit per-turn LLM token usage)** — Provides per-conversation token tracking over the Pico channel for downstream cost analysis.

#### 4. Community Hot Topics
- **#3093 — [Feature] I need SimpleX or Tox (4 comments, 1 👍)**
  A user is requesting integration with privacy-focused messaging protocols (SimpleX, Tox, Wire). This issue has some community interest but has not received a maintainer response. The underlying need is for secure, decentralized communication gateways.
  [View Issue](https://github.com/sipeed/picoclaw/issues/3093)

- **#3153 — [BUG] Volcengine Doubao Seed tool calls leak as raw text (2 comments)**
  A functional regression on the Volcengine model (Doubao Seed) where tool calls are printed to the user instead of executed. This is a high-visibility LLM integration bug affecting a specific provider.
  [View Issue](https://github.com/sipeed/picoclaw/issues/3153)

- **#3063 — [PR] feat: add DeltaChat gateway (1 comment, 0 👍)**
  The DeltaChat gateway addition is the only new feature PR that closes a previously opened feature request. It has been open for 22 days without merge.
  [View PR](https://github.com/sipeed/picoclaw/pull/3063)

#### 5. Bugs & Stability
- **Severity: High** — **#3153 — Volcengine Doubao Seed tool calls leak as raw text**
  When using `doubao-seed-2.0-pro`, tool calls are sometimes returned as raw `<seed:tool_call>` text instead of being executed by the agent. This breaks the core conversation loop for users of that model. No fix PR is yet linked.
  [View Issue](https://github.com/sipeed/picoclaw/issues/3153)

- **Severity: Medium** — **#3090 — Panel does not work on Safari iOS <16.4 (Closed)**
  This bug has been closed, likely with a fix included in v0.2.9 (the version initially affected was v0.2.8). The issue concerned the web panel failing to load on older iOS versions.
  [View Issue](https://github.com/sipeed/picoclaw/issues/3090)

#### 6. Feature Requests & Roadmap Signals
Two clear signals for the upcoming roadmap are visible:
- **Messaging Gateway Expansion**: Issue #3093 asks for SimpleX, Tox, or Wire. Combined with the open PR #3063 (DeltaChat), this suggests the community is actively pushing PicoClaw toward privacy-respecting, decentralized messaging backends. **Prediction**: DeltaChat will likely land in the next minor release (v0.3.x), with Tox/SimpleX following in a subsequent version.
- **Cost & Usage Tracking**: PR #3156 (token usage emission) and PR #3163 (Bedrock prompt caching) both focus on reducing cost and increasing observability for LLM calls. **Prediction**: These will likely merge into v0.2.10 and immediately serve enterprise/ops users.

#### 7. User Feedback Summary
- **Pain Point**: Volcengine Doubao Seed users are experiencing silent failures where tool calls are not executed, degrading trust in the agent (Issue #3153).
- **Requested Use Case**: A segment of the community wants PicoClaw to act as a bridge to encrypted/peer-to-peer networks (SimpleX, Tox, Wire) beyond the current IRC/Matrix/Telegram backends (Issue #3093).
- **Satisfaction**: The quick closure of the iOS Safari panel bug (Issue #3090) indicates good responsiveness for critical front-end fixes, but the lack of response to the feature request suggests a prioritization gap.

#### 8. Backlog Watch
- **#3063 — feat: add DeltaChat gateway** — Open for 22 days, no maintainer comments. This is a long-standing feature request now with a submitted PR. A decision is overdue.
  [View PR](https://github.com/sipeed/picoclaw/pull/3063)

- **#3093 — [Feature] I need SimpleX or Tox** — Open since June 10, no official maintainer response despite 4 comments and a 👍. This is becoming a stale feature request that needs a roadmap commitment or rejection.
  [View Issue](https://github.com/sipeed/picoclaw/issues/3093)

- **#3156 — feat(pico): emit per-turn LLM token usage** — Open for 8 days, no comments from maintainers. While new, this PR is high-value and risk-low; a review should be prioritized to prevent it from going stale.
  [View PR](https://github.com/sipeed/picoclaw/pull/3156)

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

# NanoClaw Project Digest — 2026-06-30

## Today's Overview
NanoClaw shows moderate activity today with 7 pull requests updated in the last 24 hours (5 still open, 2 merged/closed) and 1 new open issue. The project remains in a steady feature-acceleration phase, with major integration work converging around Discord and Slack Socket Mode adapters. A critical bug report around Discord image/file attachment handling has surfaced, along with solid progress on security hardening, agent configuration inheritance, and a new dashboard-pusher feature with OpenCode support. Overall project health is positive, with diverse contributors addressing both infrastructure improvements and urgent user-facing issues.

## Releases
No new releases were published today.

## Project Progress
Two PRs were merged/closed today:
- **#2883 — feat: voice-notify v3 意图分流 + kill-switch** (merged/closed) — Advanced the voice notification system with 5-category intent routing (action/silent/navigate/tech_status/notify), skipping code blocks and long tables, and adding a `VOICE_SUMMARY_VERSION=off` runtime kill-switch. All 38 tests passing.
- **#2882 — fix(ncl): default messaging-groups create instance to channel_type** (merged/closed) — Fixed a `NOT NULL` constraint violation in `ncl messaging-groups create` where the `instance` column was missing from the CRUD insert column list after migration 016.

Notable open PRs that advanced:
- **#2886** — Fixes new agents on single-provider installs inheriting the install's provider, avoiding 401 errors
- **#2880** — Security fix for CWE-59 symlink-follow vulnerabilities in attachment writes (addresses #2828)
- **#2885** — Brings Slack Socket Mode setup into the `main` branch guidance flow
- **#2884** — Adds full Discord channel adapter with Gateway mode, concurrent dispatch, and approval-button routing fix
- **#2871** — New dashboard pusher collecting state snapshots to a `@nanoco/nanoclaw-dashboard` server

## Community Hot Topics
- **Issue #2888 — [OPEN] Discord (and likely other url-only chat-sdk adapters) drop image/file attachments** ([link](nanocoai/nanoclaw/issues/2888)) — The only issue updated today, with 1 comment. Agent only sees filename metadata in Discord, never actual file content. Root cause identified in `messageToInbound` of `chat-sdk-bridge.ts`: attachment bytes are never fetched. High-impact for Discord-first users.

- **PR #2884 — feat(discord): add Discord channel adapter** ([link](nanocoai/nanoclaw/pull/2884)) — Author rudgalvis adds the actual Discord adapter code, making this the hottest feature thread. Includes a fix for Gateway approval-button routing among Discord bots, addressing a key UX friction point.

- **PR #2885 — fix(setup): offer Slack Socket Mode in the guided setup flow** ([link](nanocoai/nanoclaw/pull/2885)) — Community interest in Slack integration is high; this PR resolves a setup-side regression where Socket Mode was merged to the wrong branch and missing from `main`.

## Bugs & Stability

| Severity | Issue | Status | Notes |
|----------|-------|--------|-------|
| **Critical** | #2888 — Discord drops image/file attachments | Open, no fix PR yet | Metadata-only, never fetches bytes; affects all url-only chat-sdk adapters |
| **High** | #2886 — 401 errors on single-provider installs when creating new agents | Fix PR open | New agents inherit wrong provider; affects onboarding |
| **High** | #2880 — CWE-59 symlink-follow → arbitrary host file write | Fix PR open (#2880) | Compromised agent containers can escape session dirs via symlinks |
| **Medium** | #2882 — `ncl messaging-groups create` fails with NOT NULL constraint | Fixed/merged | Regression from migration 016; affects CLI users |
| **Medium** | #2884 — Discord DM approval buttons not routing correctly | Fix included in PR #2884 | Gateway approval-card routing broken across Discord bots |

## Feature Requests & Roadmap Signals
- **Discord channel adapter (PR #2884)** — In-flight; likely to ship in next release. Gateway mode with concurrent dispatch fills a major platform gap for community managers and multi-platform teams.
- **Dashboard pusher + OpenCode support (PR #2871)** — New telemetry/observability feature from grantland. Suggests roadmap interest in managed monitoring and OpenCode compatibility.
- **Voice-notify intent routing (PR #2883, merged)** — Already landed. Indicates demand for smart notification triage in voice workflows.
- **Slack Socket Mode setup flow (PR #2885)** — Pending merge into `main`. Suggests Slack remains a high-priority platform for the user base.

**Prediction for next release:** Discord adapter (#2884), provider inheritance fix (#2886), and Slack Socket Mode setup (#2885) are likely to ship together as a "platform expansion" minor release. The dashboard pusher (#2871) may follow in a subsequent release depending on review.

## User Feedback Summary
- **Pain point (Discord attachments):** User eagansilverpathmarketing reports that Discord image/screenshot/file sharing is completely broken — the agent never sees content, only metadata. Telegram works fine. This is a blocker for any visual or document-based workflows on Discord.
- **Pain point (onboarding):** Single-provider installations (e.g., OpenAI-only) experience 401 errors when users connect new agents via chat channels because the system default-provider logic ignores the install's actual configured provider.
- **Positive signal:** Multiple contributors (thisdotrob, johnmathews, rudgalvis, grantland, tier2tech-tian, omri-maya) active today, indicating a healthy community with distributed ownership.
- **Satisfaction indicator:** The voice-notify v3 PR (#2883) passed 38/38 tests and C1 review, suggesting strong quality control and a team responsive to feature refinement requests.

## Backlog Watch
- **Issue #2828 (referenced in PR #2880)** — Symlink-follow arbitrary file write vulnerability. PR #2880 by johnmathews provides the fix; needs maintainer review and merge. This is a security issue with potential host compromise.
- **PR #2871 (dashboard pusher)** — Open since 2026-06-27, no comments/reviews yet. May need maintainer attention to avoid stalling a useful observability feature.
- **PR #2884 (Discord adapter)** — Core feature but no comments from maintainers yet. Given that #2888 (Discord attachment bug) directly impacts Discord users, this PR becomes more urgent.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

# NullClaw Project Digest — 2026-06-30

## Today’s Overview
Project activity is moderate, with 1 open issue and 4 pull requests updated in the last 24 hours. A single user-reported bug (#972) regarding Telegram channel responsiveness has emerged, while the maintainers are actively working on two key feature branches: native tool-call support during streaming (#971) and CLI REPL improvements (#970/#960). No new releases have been published today. Overall, the project shows steady development velocity with a focus on both user-facing stability and internal streaming architecture.

## Releases
No new releases.

## Project Progress
One pull request was closed/merged today:
- **#960 (CLOSED)** `fix(cli): handle arrow keys in agent REPL` — Implemented a small allocation-free line editor for the interactive `nullclaw agent` REPL, enabling POSIX raw-mode input for arrow keys, history navigation, cursor movement, backspace/delete, Home/End, and word-left/right sequences. This addresses a long-standing UX pain point in terminal usage.

Two new open PRs continue pending work:
- **#971** `feat(streaming): native tool calls during SSE streaming` — Decouples native tool-call support from the streaming path, allowing providers that support native tools during streaming to emit them properly.
- **#970** `fix(cli): handle arrow keys in agent REPL` — Appears to be a rework or follow-up to the now-merged #960 (same summary), suggesting iterative improvement.

## Community Hot Topics
- **#972 (OPEN)** `[bug] telegram channel stop respond after some idle time` — The only active issue, reported by i11010520. The Telegram channel stops responding after overnight idle periods, while the backend appears to run normally (`nullclaw agent -m "ping"` returns expected output). Zero comments or reactions so far, but it highlights a potential keepalive or session expiry problem in the Telegram integration.

- **#971 (OPEN)** `feat(streaming): native tool calls during SSE streaming` — Submitted by vernonstinebaker, this PR addresses a fundamental limitation where the agent loop disabled native tools during streaming, forcing them into prompt-injection format. No comments yet, but the fix is architectural and likely to be well-received by users relying on streaming.

- **#956 (OPEN)** `[dependencies, docker] ci(deps): bump alpine from 3.23 to 3.24` — Automated dependency bump from Dependabot. Low engagement but important for Docker image security and compatibility.

## Bugs & Stability
**Medium severity:**
- **#972 (OPEN)** — Telegram channel stops responding after idle period overnight. Backend remains operational, suggesting a session/connection timeout issue rather than a full crash. No fix PR exists yet. Likely root cause: Telegram bot polling or long-poll timeout without reconnection logic.

No critical errors, crashes, or regressions were reported today.

## Feature Requests & Roadmap Signals
- **Native tool calls during streaming (#971)** — This is a clear signal that users need tool orchestration to work seamlessly with SSE streaming. Once merged, it will likely be included in the next minor release.
- **CLI arrow key support (#960/#970)** — Already merged, indicating the maintainers are prioritizing terminal UX improvements. Users can expect a smoother interactive experience in upcoming releases.
- **Telegram idle timeout (#972)** — Though a bug, it may prompt a feature enhancement for session keepalive or automatic reconnection in the channel adapter.

## User Feedback Summary
- **Pain point:** Users are experiencing session drops in Telegram after idle periods, forcing them to restart interactions (bug #972).
- **Satisfaction:** The merged REPL arrow key fix (#960) addresses a common frustration with terminal-based interaction.
- **Use case:** The streaming tool-call PR (#971) suggests users are running long-running, tool-heavy agents where streaming response and real-time tool execution are critical.

## Backlog Watch
- **#956 (OPEN)** `ci(deps): bump alpine from 3.23 to 3.24` — Opened 2026-06-15, last updated 2026-06-29. Still unmerged. If a security vulnerability is present in Alpine 3.23, this could become urgent. Maintainers should prioritize review.
- **#972 (OPEN)** — Reported today, but currently unattended. No maintainer response yet. Given it affects a core channel (Telegram), a quick triage comment or assignment would be advisable.

No long-unanswered issues requiring immediate maintainer attention beyond these two items.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

Here is the IronClaw project digest for **2026-06-30**.

---

### IronClaw Project Digest — 2026-06-30

### 1. Today's Overview
The IronClaw project is exhibiting **very high activity** as it enters a major stabilization and quality assurance phase for the "Reborn" engine and WebUI v2. In the last 24 hours, 14 issues were updated (10 open) alongside a massive 50 Pull Requests (20 merged/closed), indicating a significant push to land features and fixes. The focus is heavily on porting legacy test coverage, hardening new features like routines and tool permissions, and addressing a barrage of bugs identified during QA and daily benchmarking. No new formal releases were tagged today, suggesting the team is consolidating code before a future cut.

### 2. Releases
**None.** No new releases were published in the last 24 hours.

### 3. Project Progress
The core team merged/closed 20 pull requests today, demonstrating strong momentum in several key areas:
- **Test Infrastructure:** Significant effort went into expanding the Reborn test framework. PR [#5402](https://github.com/nearai/ironclaw/pull/5402) landed shared-persistence integration tests covering approvals, auth, and memory. PR [#5427](https://github.com/nearai/ironclaw/pull/5427) extracted mock-MCP scaffolding for better test organization.
- **Feature Stabilization:** PR [#5401](https://github.com/nearai/ironclaw/pull/5401) localized WebUI v2 tool and extension copy. PR [#5423](https://github.com/nearai/ironclaw/pull/5423) made QA routine test wording more flexible. PR [#5422](https://github.com/nearai/ironclaw/pull/5422) fixed the `/canary` PR validation workflow, streamlining the CI/QA pipeline.
- **E2E & Legacy Porting:** Several PRs (#5371, #5372) porting browser coverage for chat history, auth, and approval UX were closed and merged, marking progress in replacing legacy E2E suites.
- **CI & QA Automation:** PR [#5424](https://github.com/nearai/ironclaw/pull/5424) improved failure reporting by linking failed QA cases directly to CI artifacts. PR [#5406](https://github.com/nearai/ironclaw/pull/5406) integrated QA sheet prompts directly into the live runner for more realistic testing.

### 4. Community Hot Topics
While there were no issues with high comment counts or reactions today, several issues generated significant development follow-up, indicating they are pain points for the team:
- **Daily Failure Taxonomy ([#5411](https://github.com/nearai/ironclaw/issues/5411)):** This automated report is a critical health monitor, identifying the top regression causes. Today's report (from DeepSeek-V4-Flash runs) is driving targeted fixes for response quality, tool calling, and authorization.
- **"Ask each time" Tool Permission Failure ([#5196](https://github.com/nearai/ironclaw/issues/5196)):** This issue, detailing a duplicate approval flow after authorization failure, was closed today, suggesting a fix has been merged.
- **Multi-Tool Workflow Failure ([#5415](https://github.com/nearai/ironclaw/issues/5415)):** Tagged P1 (Critical), this bug where 18-25 tool calls lead to a "protocol violation" is a top concern. It highlights a systemic stability limit in complex multi-step workflows.

### 5. Bugs & Stability
A significant batch of bugs was reported in a QA session, indicating an intensive stabilization effort. Ranked by severity:
- **P1 (Critical):** [#5415](https://github.com/nearai/ironclaw/issues/5415) — Multi-tool Google Sheets workflow fails consistently with a "protocol violation" error after ~18-25 tool calls. This is a blocking issue for complex automations. No immediate fix PR was observed.
- **P2 (High):** [#5416](https://github.com/nearai/ironclaw/issues/5416) — Incorrect Google connection state causing a contradictory authentication flow and misleading user error messages. [#5417](https://github.com/nearai/ironclaw/issues/5417) — Wrong skill activated for Hacker News search, indicating a skill routing regression.
- **P3 (Medium):** [#5418](https://github.com/nearai/ironclaw/issues/5418) — Message ordering in conversation UI is incorrect after tool activity. [#5419](https://github.com/nearai/ironclaw/issues/5419) — No UI option to rename an automation, reducing user control.
- **Other Notable Bugs:**
    - [#5420](https://github.com/nearai/ironclaw/issues/5420) — Routine delivery target is a global default, not per-routine, causing cross-automation interference.
    - [#5421](https://github.com/nearai/ironclaw/issues/5421) — Web search under Reborn is not "zero-config" and re-prompts for auth even when chat works.
    - [#5426](https://github.com/nearai/ironclaw/issues/5426) — "System drive is not available" error preventing routine creation on staging.

### 6. Feature Requests & Roadmap Signals
- **Context Management (Progressive Tool Disclosure):** The large PR [#5149](https://github.com/nearai/ironclaw/pull/5149) (still open) proposes a major optimization to reduce model call prompt sizes by only sending relevant tool schemas instead of all ~91. This is flag-gated and default-off, likely targeting the next release.
- **Multi-User RBAC:** A design proposal (PR [#5425](https://github.com/nearai/ironclaw/pull/5425)) was drafted and reviewed today, aiming to converge on a multi-user capability policy without creating new architectural layers. This is a strong signal for enterprise/team features on the roadmap.

### 7. User Feedback Summary
Today's data reveals quantifiable user pain points from QA sessions and production regression suites:
- **Pain Point: Workflow Reliability:** The most critical feedback is the failure of complex workflows like multi-tool Google Sheets operations. The "protocol violation" error and the 18-25 tool call limit suggest a hard cap or resource leak that severely impacts user goals.
- **Pain Point: Misleading UI/State:** Issues like the contradictory Google auth state, incorrect message ordering, and the global routine delivery target show that the UI state machine is frequently out of sync with the backend, leading to user confusion.
- **Satisfaction (Implicit):** The rapid closure of issues like the OAuth refresh silence ([#5413](https://github.com/nearai/ironclaw/issues/5413)) and the "Ask each time" permission flow ([#5196](https://github.com/nearai/ironclaw/issues/5196)) indicates the team is actively addressing high-impact UX problems.

### 8. Backlog Watch
- **Stalled E2E Regression:** [#4108](https://github.com/nearai/ironclaw/issues/4108) ("Nightly E2E failed") was updated today but has been open for over a month with no resolution. This represents a persistent gap in the safety net for the main branch, which could be masking other regressions.
- **Dependency Update Halt:** PR [#3706](https://github.com/nearai/ironclaw/pull/3706) (bumping `postcss` and `@remotion` dependencies in the docs) has been open since mid-May. While low risk, it remains unmerged, potentially blocking other dependency updates or docs builds.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

Here is the structured project digest for LobsterAI on 2026-06-30.

---

## LobsterAI Project Digest | 2026-06-30

### 1. Today's Overview
The project experienced a **major release spike** with 39 PRs merged/closed in the last 24 hours, culminating in the **2026.6.29 release**. This represents a high-velocity day, likely a release stabilization push (end-of-June release cycle). Maintainers were highly active: 8 issues remain open, but 3 were resolved. The volume of closed PRs (39) relative to open (1) indicates a disciplined merge window. Activity was dominated by bug fixes, plugin/agent integration stability, and dependency updates.

### 2. Releases
**New Version:** **LobsterAI 2026.6.29** (Released 2026-06-29)
- **Key Fixes:**
  - **OpenClaw:** Route plugin approvals through permissions; fixed a regression where agent bootstrap workspace was conflated with task `cwd` (fixing identity/persona files being read from project directory instead of agent workspace).
  - **Cowork:** Cleaned navigation rail previews and tooltip alignment; restored full conversation rail navigation after an accidental revert.
  - **Preserved user turn cache stability** and cron run follow-up history.
- **Breaking Changes:** None indicated. The release is a hotfix/patch release on top of v2026.6.1.
- **Migration Notes:** Users running v2026.6.1 should upgrade immediately to resolve the agent workspace isolation bug (identity/persona/long-term memory loading from wrong directory).

### 3. Project Progress
**40 PRs updated; 39 merged/closed, 1 open.**
- **OpenClaw Plugin & Agent Stability (Major advance):**
  - [#2227](https://github.com/netease-youdao/LobsterAI/pull/2227) – Fixed agent bootstrap workspace isolation from task `cwd`
  - [#2219](https://github.com/netease-youdao/LobsterAI/pull/2219) – Patched user-turn serialization cache stability for v2026.6.1.1
  - [#2220](https://github.com/netease-youdao/LobsterAI/pull/2220) – Preserved cron run follow-up history during sync
  - [#2190](https://github.com/netease-youdao/LobsterAI/pull/2190) – Synced cron run sessions across agents
  - [#2218](https://github.com/netease-youdao/LobsterAI/pull/2218) – Cleaned navigation rail previews
- **Cowork UI fixes:**
  - [#2223](https://github.com/netease-youdao/LobsterAI/pull/2223) – Cleaned and aligned conversation rail tooltips (removed plan-mode tags, increased preview length)
  - [#2225](https://github.com/netease-youdao/LobsterAI/pull/2225) – Reverted accidental merge of conversation rail changes from `main` (then reapplied correctly on release branch)
- **Plugin Preinstalls & Deployment:**
  - [#2198](https://github.com/netease-youdao/LobsterAI/pull/2198) – Preinstalled QQ and Discord plugins
  - [#2182](https://github.com/netease-youdao/LobsterAI/pull/2182) – Supported upgraded IM plugin installs (DingTalk, Lark, WeCom, POPO)
  - [#2186](https://github.com/netease-youdao/LobsterAI/pull/2186) – Compiled NIM plugin runtime entry
- **Dependency Bump:** [#1277](https://github.com/netease-youdao/LobsterAI/pull/1277) – Bumped Electron from 40.2.1 to 42.5.0 (still open; outdated but not stale)

### 4. Community Hot Topics
| Issue | Title | Comments | Underlying Need |
|-------|-------|----------|-----------------|
| [#2079](https://github.com/netease-youdao/LobsterAI/issues/2079) | Execution result window freezes when scrolling to top | 2 | **Severe UX bug** – application hangs on scrolling; affects users running long scripts. |
| [#2131](https://github.com/netease-youdao/LobsterAI/issues/2131) | Support for Hermes Agent? | 2 | **Feature request** – community interest in integrating Hermes protocol agent(s); indicates desire for multi-agent framework support. |
| [#2120](https://github.com/netease-youdao/LobsterAI/issues/2120) | Feature suggestions (task queue, extended runtime, UI columns) | 2 | **Workflow improvement** – user wants task pre-queuing, longer monitoring sessions, and better 3-column UI for large screens. |

**Analysis:** The community is pushing for **production-grade monitoring** (longer runtime, no freezes) and **multi-agent integration** (Hermes). The task queuing request mirrors WorkBuddy's approach, suggesting users are looking for a more robust AI-assisted workflow orchestration layer.

### 5. Bugs & Stability
**High Severity (Reproducible, Active):**
- [#2079](https://github.com/netease-youdao/LobsterAI/issues/2079) – **Execution window freezes** on scroll to top (reproducible). No fix PR linked.
- [#2121](https://github.com/netease-youdao/LobsterAI/issues/2121) – **Token waste suspicion**: repeated text outputs. No fix PR linked.

**Medium Severity (UI/UX, Stale):**
- [#1389](https://github.com/netease-youdao/LobsterAI/issues/1389) – English language selection shows Chinese text in options.
- [#1386](https://github.com/netease-youdao/LobsterAI/issues/1386) – Sharing long conversations truncates output image.
- [#1388](https://github.com/netease-youdao/LobsterAI/issues/1388) – Email test connectivity hangs indefinitely with bad password.

**Resolved in v2026.6.29:**
- The workspace isolation bug ([#2227](https://github.com/netease-youdao/LobsterAI/pull/2227)) was likely causing agent persona/memory file corruption for local users. This is a critical fix.
- Cron run history loss ([#2220](https://github.com/netease-youdao/LobsterAI/pull/2220)) and user-turn cache stability ([#2219](https://github.com/netease-youdao/LobsterAI/pull/2219)) were also resolved.

### 6. Feature Requests & Roadmap Signals
**User-requested features with high likelihood for next release:**
- **Task pre-queuing** (from [#2120](https://github.com/netease-youdao/LobsterAI/issues/2120)) – Users want to input tasks while one is running. Expect this in v2026.7.x as it aligns with existing cron/session improvements.
- **Extended monitoring runtime** (from [#2120](https://github.com/netease-youdao/LobsterAI/issues/2120)) – "terminated" errors on long scripts. Likely to be addressed after the freeze bug.
- **Hermes Agent support** (from [#2131](https://github.com/netease-youdao/LobsterAI/issues/2131)) – This is a roadmap signal; no maintainer response yet, but the plugin/agent architecture improvements in this release (OpenClaw 2026.6.1.1) suggest the project is preparing for multi-agent protocols.

**Long-standing signal:**
- [#1386](https://github.com/netease-youdao/LobsterAI/issues/1386) – Share feature truncation (since April 2026) remains unassigned.

### 7. User Feedback Summary
- **Dissatisfied:** Users reported **token waste** ([#2121](https://github.com/netease-youdao/LobsterAI/issues/2121)) and **unexpected subscription credit loss** ([#2081](https://github.com/netease-youdao/LobsterAI/issues/2081) – closed with anger: "来搞笑的吧???"). The credit reset policy (monthly expiration) caused significant frustration.
- **Positive workflow:** User [nbjoe](https://github.com/nbjoe) is actively using Claw for data monitoring and wants longer runs, indicating the tool is being used for **real production workloads**.
- **UI complaints:** 2560×1600 users find the skill interface (2 columns) ugly; request 3 columns. Expect UI improvements in next release.

### 8. Backlog Watch
**Critical open issues needing maintainer response (>80 days old):**
- [#1386](https://github.com/netease-youdao/LobsterAI/issues/1386) – Share feature truncation (opened April 3, 2026; last comment April 3). **83 days stale.**
- [#1388](https://github.com/netease-youdao/LobsterAI/issues/1388) – Email connectivity test hang (opened April 3, 2026). **83 days stale.**
- [#1390](https://github.com/netease-youdao/LobsterAI/issues/1390) – Scheduled task update failure (opened April 3, 2026). **83 days stale.**

**Dependency PR (still open):**
- [#1277](https://github.com/netease-youdao/LobsterAI/pull/1277) – Electron dependency bump (Electron 40→42). Despite being open for 88 days, it has 0 comments and no maintainer review. This is a security risk given the large version jump.

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

# CoPaw Project Digest — 2026-06-30

## Today's Overview

CoPaw shows a **high-activity** day with 50 PRs updated (24 open, 26 closed/merged) and 31 issues updated (19 active, 12 closed). The project is approaching a **2.0.0 release milestone**, evidenced by documentation updates and removal of legacy features (`/plan` command). No new releases today, but the rapid closure rate (52% of PRs, 39% of issues) suggests a productive maintenance and feature cycle. The community is actively reporting bugs across desktop, channels, and model integration, while maintainers are responding quickly with fix PRs. The **agentscope 2.0 migration** (#5542) continues to ripple through the codebase, with several PRs cleaning up deprecated components and updating documentation.

## Releases

*No new releases today.*

## Project Progress

**Merged/Closed PRs (26 today, selected highlights):**

- **Desktop stability fix** — [#5570](https://github.com/agentscope-ai/QwenPaw/pull/5570) (closed): Fixed two compounding defects: a plugin dependency install loop with no lock causing `pip install` storms, and orphaned backend processes. Addresses issue #5550.
- **Windows CI reliability** — [#5627](https://github.com/agentscope-ai/QwenPaw/pull/5627) (closed): Raised HTTP timeout and added per-test hang safeguards for Windows nightly tests, fixing `httpx.ReadTimeout` failures on 2-core runners.
- **Tool card counting fix** — [#5628](https://github.com/agentscope-ai/QwenPaw/pull/5628) (closed): Fixed tool result badge counts (e.g., `glob_search`, `read_file`) that always showed `1` by counting lines from normalized display text.
- **Chat UI capabilities** — [#5515](https://github.com/agentscope-ai/QwenPaw/pull/5515) (closed): Updated `@agentscope-ai/chat` to beta and enabled new chat UI capabilities.
- **Documentation updates** — [#5610](https://github.com/agentscope-ai/QwenPaw/pull/5610), [#5614](https://github.com/agentscope-ai/QwenPaw/pull/5614), [#5631](https://github.com/agentscope-ai/QwenPaw/pull/5631): Updated docs for QwenPaw 2.0.0, context management, and scrolling strategy.
- **2.0.0 cleanup** — [#5634](https://github.com/agentscope-ai/QwenPaw/pull/5634): Dropped `SLASH-006` plan command test after AgentScope 2.0 removal.
- **Security documentation** — [#5621](https://github.com/agentscope-ai/QwenPaw/pull/5621): Added comprehensive Sandbox section covering OS kernel-level isolation, macOS Seatbelt, Linux Bubblewrap.

## Community Hot Topics

| Issue/PR | Comments | Type | Summary |
|---|---|---|---|
| [#3891](https://github.com/agentscope-ai/QwenPaw/issues/3891) | 5 | Issue (Open) | **DeepSeek prefix cache hit rate too low (~95%)** — 5% uncached costs 4x-10x more; optimization needed |
| [#5550](https://github.com/agentscope-ai/QwenPaw/issues/5550) | 4 | Bug (Closed) | **Remote SSH plugin dep loop + orphaned backends** — fixed by PR #5570 |
| [#5624](https://github.com/agentscope-ai/QwenPaw/issues/5624) | 3 | Bug (Closed) | **Tool card count always shows 1** — fixed by PR #5628 |
| [#5561](https://github.com/agentscope-ai/QwenPaw/issues/5561) | 3 | Bug (Open) | **Feishu bot drops long replies**, only sends as file |
| [#5342](https://github.com/agentscope-ai/QwenPaw/issues/5342) | 3 | Feature (Open) | **Hard cap on tool result size** — context explosion defense |
| [#5505](https://github.com/agentscope-ai/QwenPaw/issues/5505) | 3 | Bug (Closed) | **MiniMax-M3 image safety rejection cached incorrectly** |

**Underlying needs:**
- **Cost optimization** (#3891): Users are paying 4-10x more for DeepSeek API calls due to suboptimal prefix caching. DeepSeek-V4 pricing discrepancy (¥0.5 vs ¥2 per million tokens) makes this a high-impact cost issue.
- **Desktop reliability** (#5550, fix merged): The "fork-bomb" of `pip install` processes and orphaned backends was a critical stability threat.
- **Channel UX** (#5561): Feishu long messages being downgraded to files indicates a gap in message size handling.

## Bugs & Stability

| Severity | Issue | Description | Fix PR |
|---|---|---|---|
| **Critical** | [#5550](https://github.com/agentscope-ai/QwenPaw/issues/5550) | Remote SSH plugin dep install storm + orphaned backends (memory exhaustion) | [#5570](https://github.com/agentscope-ai/QwenPaw/pull/5570) ✅ |
| **High** | [#5624](https://github.com/agentscope-ai/QwenPaw/issues/5624) | Tool card count always shows `1` — misleading UX | [#5628](https://github.com/agentscope-ai/QwenPaw/pull/5628) ✅ |
| **High** | [#5505](https://github.com/agentscope-ai/QwenPaw/issues/5505) | MiniMax-M3: image rejection cached as `rejects_media=True`, stripping subsequent vision requests | Seen fix approach |
| **Medium** | [#5573](https://github.com/agentscope-ai/QwenPaw/issues/5573) | DeepSeek V4 thinking mode: streaming `reasoning_content` missing, `type: null` in tool schemas causing 400 errors | Open |
| **Medium** | [#5554](https://github.com/agentscope-ai/QwenPaw/issues/5554) | WeChat Work: file messages silently dropped — channel restart interrupts processing | Open |
| **Medium** | [#5561](https://github.com/agentscope-ai/QwenPaw/issues/5561) | Feishu bot drops long messages, sends as file instead | Open |
| **Low** | [#5587](https://github.com/agentscope-ai/QwenPaw/issues/5587) | Qwen-Image Tool install error | Open |
| **Low** | [#5591](https://github.com/agentscope-ai/QwenPaw/issues/5591) | Excessive log spam from inbox polling (40k+ lines/night) | Open |

**Emerging regression risk**: #5543 reports that `"type":"null"` in function declarations causes failures with third-party model proxies — a schema compliance issue that may affect more users as multi-provider setups grow.

## Feature Requests & Roadmap Signals

| Issue | Feature | Community Demand | Likely Next Version |
|---|---|---|---|
| [#5572](https://github.com/agentscope-ai/QwenPaw/issues/5572) | Auto model fallback on quota/timeout/failure | High — 2+ similar requests | ✅ Likely (v2.0) |
| [#5527](https://github.com/agentscope-ai/QwenPaw/issues/5527) | Dynamic model switching (AgentScope 2.0) | High — part of 2.0 roadmap | ✅ Planned |
| [#5342](https://github.com/agentscope-ai/QwenPaw/issues/5342) | Hard cap on tool result size | Medium — defense against context explosion | Being worked on (#5510) |
| [#5615](https://github.com/agentscope-ai/QwenPaw/issues/5615) | Vision fallback: text model auto-calls vision model for image description | Medium | Possible |
| [#5579](https://github.com/agentscope-ai/QwenPaw/issues/5579) | Conversation checkpoint save on abnormal interruption | Medium | Possible |
| [#5588](https://github.com/agentscope-ai/QwenPaw/issues/5588) | Memory search with dedicated reranker | Low-Medium | Unlikely soon |
| [#5630](https://github.com/agentscope-ai/QwenPaw/issues/5630) | Custom Telegram BaseURL | Low | Possible (small scope) |
| [#5622](https://github.com/agentscope-ai/QwenPaw/issues/5622) | Windows desktop tray icon | Low | Possible |
| [#4939](https://github.com/agentscope-ai/QwenPaw/issues/4939) | `cron update` subcommand | Low — already exists as API but no CLI | Quick win |

**Roadmap signals**: The v2.0.0 branch shows clear focus on AgentScope 2.0 integration (dynamic models, plan mode removal), context management overhaul (scroll strategy), and governance generalization (#5546). The security docs addition (#5621) suggests sandboxing will be a pillar of v2.0.

## User Feedback Summary

**Positive patterns:**
- Swift maintainer response — bugs like #5550 (desktop crash) and #5624 (tool card count) were fixed within hours or days
- Community actively participates in debugging (e.g., #5573 includes user-validated fix suggestions)
- Clear migration path to 2.0.0 with documentation updates (#5610, #5614, #5631)

**Pain points (from highest to lowest priority):**
1. **Cost sensitivity**: DeepSeek cache miss pricing is a major pain point (#3891) — users want every % of cache hit rate optimized
2. **Channel reliability**: Feishu (#5561), WeChat (#5554), DingTalk (#5603) all have message handling issues that break core workflows
3. **Model compatibility**: DeepSeek V4 thinking mode (#5573), MiniMax-M3 caching bug (#5505), custom model connections (#5584) — multi-model support needs hardening
4. **Desktop stability**: The plugin dep loop (#5550) caused real memory exhaustion — now fixed, but trust needs rebuilding
5. **Performance regression**: v1.1.12.post2 users report increasing sluggishness (#5555), likely tied to context/scroll changes
6. **Conversation loss**: No checkpointing on abnormal termination or host reboot (#5579) is a critical trust issue for production use

**Satisfaction indicators:**
- Still-active community with 31+ issues and 50+ PRs per day
- Multiple first-time contributors (#5633, #5510)
- Chinese-language issues are the majority, showing strong adoption in China market
- Feature requests are well-scoped with concrete use cases

## Backlog Watch

| Issue | Age | Priority | Reason for Watch |
|---|---|---|---|
| [#4873](https://github.com/agentscope-ai/QwenPaw/issues/4873) | 29 days | **Critical** | Two subagents cause infinite parent polling loop — Feishu side cannot interrupt. Affects multi-agent production workflows. |
| [#3891](https://github.com/agentscope-ai/QwenPaw/issues/3891) | 64 days | **High** | DeepSeek cache optimization — oldest open issue with high cost implications. No maintainer response visible. |
| [#5342](https://github.com/agentscope-ai/QwenPaw/issues/5342) | 10 days | **High** | Context explosion defense — open with PR #5510 under review. Needs attention to avoid regression from the simpler fix. |
| [#5573](https://github.com/agentscope-ai/QwenPaw/issues/5573) | 4 days | **Medium** | DeepSeek V4 thinking mode 400 errors — community-provided fix that needs maintainer validation. |
| [#5555](https://github.com/agentscope-ai/QwenPaw/issues/5555) | 4 days | **Medium** | General sluggishness in latest version — could be regression from v2.0 changes. |
| [#5579](https://github.com/agentscope-ai/QwenPaw/issues/5579) | 3 days | **Medium** | Conversation loss on abnormal termination — data loss risk for production use. |

**Maintainer attention needed:**
- No response on oldest open feature (#3891, 64 days) — community may feel ignored
- #4873 (29 days, subagent polling bug) is blocking multi-agent adoption
- #5573 (DeepSeek thinking mode) has a community-contributed fix that needs peer review
- #5543 (null type in function schema) is a compliance issue affecting third-party model proxies

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

Here is the ZeroClaw project digest for June 30, 2026, based on the provided GitHub data.

---

## ZeroClaw Project Digest — 2026-06-30

### 1. Today's Overview

ZeroClaw is in an intense period of development, with extremely high activity across 50 recently updated issues and 50 pull requests. The project is heavily focused on stabilizing a major upcoming release (v0.8.3), with critical workstreams dedicated to a new WASM-based plugin runtime, provider compatibility fixes, and channel expansion. While no new releases were cut today, the volume of open work is substantial, with 43 active issues and 41 open PRs, indicating the core team is deep in an integration and stabilization phase. The project's health is mixed; while progress on new features like streaming channels and A2A discovery is strong, several high-risk, critical (P1) bugs concerning provider tool calling and multimodal routing remain unresolved, with several listed as blocked or `in-progress`.

### 2. Releases

**None.**

No new releases were published in the last 24 hours.

### 3. Project Progress

Several PRs were merged or closed today, representing progress in provider compatibility, internationalization, and quality-of-life fixes:

- **Provider Fixes (Merged):**
    - **[PR #8510](zeroclaw-labs/zeroclaw/pull/8510) (Closed):** Fixed a critical bug where empty assistant tool-call content was sent as `""` instead of being omitted in OpenAI-compatible requests, which would break strict backends like OpenRouter and Azure.
- **Internationalization (Merged):**
    - **[PR #8469](zeroclaw-labs/zeroclaw/pull/8469) (Closed):** Added missing chat toolbar button translations for Chinese, Japanese, Spanish, French, and German.
- **Bug Fixes (Merged):**
    - **[Issue #2128](zeroclaw-labs/zeroclaw/issue/2128) (Closed):** Fixed a long-standing bug where cron and heartbeat tasks would send the literal string `"NO_REPLY"` to users instead of staying silent.
    - **[Issue #8327](zeroclaw-labs/zeroclaw/issue/8327) (Closed):** Fixed native tool calling with providers like llama.cpp, where `[IMAGE:data:...]` markers in tool results were sent as plain text instead of structured image URLs, inflating token usage.
    - **[Issue #8379](zeroclaw-labs/zeroclaw/issue/8379) (Closed):** Added opt-in passive context gathering for WhatsApp Web group chats, allowing the bot to store context from unaddressed messages without triggering a turn.

### 4. Community Hot Topics

The community's focus is on core functionality, particularly provider reliability and the new plugin architecture.

- **Most Active Bug:** **[Issue #5600](zeroclaw-labs/zeroclaw/issue/5600)** (P1, 11 comments) — A workflow-blocking bug where using the `kimi-code` provider in streaming mode causes a 400 error due to a missing `reasoning_content` field. This indicates significant pressure on the project to support a wide range of Chinese providers, but also uncovers edge cases in the provider abstraction layer.
- **Architecture & Usability Debate:** **[Issue #8054](zeroclaw-labs/zeroclaw/issue/8054)** (P1, blocked, 9 comments) — A critical systemic bug where the system prompt incorrectly tells reasoning models "no tools are available" on certain entry points (e.g., WebSocket, multimodal). This is a high-risk, blocked item that is a follow-up to a fix that only covered one path, showing the difficulty of maintaining consistency across a multi-channel architecture.
- **Desktop Control Requests:** **[Issue #6909](zeroclaw-labs/zeroclaw/issue/6909)** (6 comments) — An RFC for "computer-use" (screen capture and mouse/keyboard control) has significant traction. Users want ZeroClaw to match capabilities of proprietary systems like OpenAI Codex, highlighting a key feature gap for power users.
- **Skill Plugin Evolution:** **[Issue #6140](zeroclaw-labs/zeroclaw/issue/6140)** (3 comments) — The proposal for "hybrid plugins" (markdown skills + WASM binaries) continues to generate discussion, representing the community’s desire for a powerful, sandboxed plugin system that moves beyond simple prompt injection.

### 5. Bugs & Stability

The project is grappling with several high-severity bugs that are blocking core workflows and threatening stability.

| Severity | Issue | Summary | Status | Notes |
| :--- | :--- | :--- | :--- | :--- |
| **S1 - Blocked** | [#8054](zeroclaw-labs/zeroclaw/issue/8054) | System prompt tool-availability mismatch across entry points. | **Blocked** / Accepted | High risk. A fix for the main path exists (PR #8053) but other paths remain broken. |
| **S1 - Blocked** | [#7756](zeroclaw-labs/zeroclaw/issue/7756) | Native/MCP tools unavailable on OpenAI Reasoning and Anthropic turns. | Accepted | **High risk.** Directly impacts the functionality of the MCP ecosystem. Fix potentially complex. |
| **S1 - Blocked** | [#5600](zeroclaw-labs/zeroclaw/issue/5600) | kimi-code provider error during streaming tool calls. | Accepted / No-stale | High risk, provider-specific. |
| **S1 - Blocked** | [#8505](zeroclaw-labs/zeroclaw/issue/8505) | Telegram channel cannot be configured via CLI/ZeroCode. | New (2026-06-29) | A regression or documentation gap causing user frustration. |
| **S2 - Degraded** | [#8410](zeroclaw-labs/zeroclaw/issue/8410) | Channel tasks need a first-class `no-reply` outcome (still send visible "silence"). | Accepted | Related to the fix for #2128. The fix for cron/heartbeat didn't cover all task types. |
| **S2 - Degraded** | [#8312](zeroclaw-labs/zeroclaw/issue/8312) | `fill-translations` leak-repair leaves stale entries that re-ship leaked text. | In Progress / Accepted | A subtle data-loss bug in the translation pipeline. |
| **S2 - Degraded** | [#8334](zeroclaw-labs/zeroclaw/issue/8334) | `skills install` targets `data_dir`, which multi-agent runtimes don't load. | In Progress / Accepted | **High risk.** Breaks the core "install a skill and use it" flow for most users. |
| **S2 - Degraded** | [#6841](zeroclaw-labs/zeroclaw/issue/6841) | Vision provider silently ignored; images routed to fallback provider. | Closed | Root cause found and fix merged. |

### 6. Feature Requests & Roadmap Signals

The **v0.8.3** milestone is clearly the center of gravity, with several high-priority feature trackers active. The following are likely to be included:

- **WASM Plugin Runtime:** Trackers [#7314](zeroclaw-labs/zeroclaw/issue/7314) and RFCs [#7497](zeroclaw-labs/zeroclaw/issue/7497) (OCI registries for plugins) and [#8135](zeroclaw-labs/zeroclaw/issue/8135) (Wasm-first runtime) are all actively discussed. This is the most significant architectural shift on the roadmap.
- **A2A (Agent-to-Agent) Discovery:** RFC [#7218](zeroclaw-labs/zeroclaw/issue/7218) is proposing a `.well-known/agent-card.json` standard for multi-agent interoperability.
- **In-App Upgrades:** RFC [#8170](zeroclaw-labs/zeroclaw/issue/8170) and its implementation in PR [#8173](zeroclaw-labs/zeroclaw/pull/8173) is a strong user-requested feature to allow upgrades from the web dashboard without CLI commands.
- **New Channels:** Significant effort is being put into new channels: a full **GitHub channel** (PR #8504) with SOP ingress, an **Inkbox channel** for email/SMS/voice (PR #8384), and streaming support for **DingTalk** (PR #8495) and **Matrix** (PR #8443).

### 7. User Feedback Summary

- **Pain Point (Configuration & Onboarding):** The project is receiving mixed feedback on usability. A new user reported being unable to configure the Telegram channel ([Issue #8505](zeroclaw-labs/zeroclaw/issue/8505)), and another complained that code help and keybindings in the TUI are "misleading or unreachable," especially on macOS ([Issue #7800](zeroclaw-labs/zeroclaw/issue/7800)). This suggests that as complexity grows, the project is straining to keep its onboarding and documentation clear.
- **Pain Point (Provider Reliability):** The high volume of provider-specific bugs (kimi-code, OpenAI reasoning, llama.cpp) indicates that users are actively trying to use ZeroClaw with a diverse set of backends and are hitting edge cases in the provider abstraction layer.
- **Satisfaction (Feature Velocity):** The rapid addition of new channels and the ambitious WASM plugin RFC suggest the core community is engaged and satisfied with the project's technical direction, even if stability is an ongoing concern.

### 8. Backlog Watch

Several important items are showing signs of stagnation or require immediate maintainer attention to avoid blocking the v0.8.3 release:

- **Blocked P1 Bugs:** **[Issue #8054](zeroclaw-labs/zeroclaw/issue/8054)** (Tool mismatch) and **[Issue #7756](zeroclaw-labs/zeroclaw/issue/7756)** (MCP tools unavailable) are high-risk, critical bugs that are listed as `status:blocked` or awaiting a maintainer to determine the full fix strategy. Their status is a major risk to the next release.
- **In-Progress Tracker Without Movement:** **[Issue #6074](zeroclaw-labs/zeroclaw/issue/6074)** (Tracking 153 lost commits from a bulk revert) is a housekeeping audit that has been open since April. While not a code bug, ignoring this could lead to future regressions if previously fixed bugs re-emerge.
- **Stalled RFCs:** **[Issue #8462](zeroclaw-labs/zeroclaw/issue/8462)** (Runtime Policy for OTel Content) and **[Issue #8170](zeroclaw-labs/zeroclaw/issue/8170)** (In-app upgrade) are both marked with `needs-maintainer-review`. They need a decision or next step from the core team to either advance or defer.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*