# OpenClaw Ecosystem Digest 2026-06-30

> Issues: 500 | PRs: 500 | Projects covered: 13 | Generated: 2026-06-29 16:05 UTC

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
**Date:** 2026-06-30

## Today's Overview

OpenClaw shows very high community activity with 500 issues and 500 PRs updated in the last 24 hours, alongside one new beta release. The project maintains a healthy balance of 398 open/active issues against 102 closed, though PRs are heavily skewed toward open (452) versus merged/closed (48), indicating a significant review bottleneck. Key development areas include SQLite session/transcript migration (tracked across multiple high-comment issues), channel-specific improvements (Slack, Mattermost, Telegram), and continued work on session state stability. The release of `v2026.6.11-beta.2` brings enhanced channel control features but critical P1 bugs around session write-lock timeouts and Telegram message drops remain unresolved.

## Releases

**New Release:** `v2026.6.11-beta.2` — openclaw 2026.6.11-beta.2

**Highlights:**
- **Slack relay mode** for more flexible channel operations
- **Native Mattermost `/oc_queue`** support
- **Per-DM model overrides** enabling granular channel tuning
- Community contributions from @sjf-oa, @amknight, @xydigit-zt, @thomaszta, and @gandalf-at-lerian

No breaking changes or migration notes were documented in the release data.

## Project Progress

**Merged/Closed PRs today:** 48

Notable closed items include:
- **Issue #50248** (closed): Session cleanup bug falsely pruning fresh cron sessions with valid transcripts — fix applied
- **Issue #83184** (closed): Heartbeat-driven agent replies stuck with `pendingFinalDelivery` — resolved
- **Issue #86827** (closed): Group chat sessions stuck in 'failed' state silently dropping messages — fixed
- **Issue #85822** (closed): Silent 48s post-run lane retention on Discord turns — resolved
- **Issue #79308** (closed): Telegram group replies sent to wrong chat_id — fixed

Active PRs progressing project forward include:
- **#97861** — Count bashExecution and summary turns in pre-prompt overflow precheck (agents area)
- **#97860** — Keep failed agent turns visibly failed in web UI (fixes false success display)
- **#97848** — Bound OpenAI SSE response reads via guarded model fetch (security hardening)
- **#97827** — Keep Tavily exec SecretRefs resolved in Tool Search (auth reliability fix)

## Community Hot Topics

### Most Active (by comment count)

| Issue/PR | Comments | Reactions | Topic |
|----------|----------|-----------|-------|
| [#75 - Linux/Windows Clawdbot Apps](https://openclaw/openclaw Issue #75) | **110** | 81 👍 | Platform expansion request — most popular feature request |
| [#88838 - SQLite migration accessor seam](https://openclaw/openclaw Issue #88838) | **36** | 3 👍 | Core architecture migration — Path 3 consolidation |
| [#77598 - Live dev agent behavior tracking](https://openclaw/openclaw Issue #77598) | **22** | 1 👍 | Observability/monitoring of autonomous agent behavior |
| [#86538 - Session write-lock timeouts](https://openclaw/openclaw Issue #86538) | **18** | 1 👍 | Critical P1 bug blocking subagent delivery lanes |
| [#80319 - QA tool-defaults suite conflation](https://openclaw/openclaw Issue #80319) | **17** | 1 👍 | Testing infrastructure cleanup needed |

### Underlying Needs Analysis

1. **Platform parity (Issue #75):** The most vocal community need — 110 comments and 81 upvotes — is for Linux and Windows desktop apps. Current macOS/iOS/Android coverage is insufficient for many users, and this remains the #1 feature demand.

2. **Session state architecture (Issues #88838, #79902-79905):** Multiple high-activity issues revolve around SQLite migration, transcript read APIs, and session lineage. The community is heavily engaged in the Path 3 storage flip, indicating this is the most critical near-term architectural change.

3. **Delivery reliability:** Issues around write-lock timeouts (#86538), heartbeat failures (#83184, closed today), and silent message drops (#80520, #86827 closed) dominate active discussions, suggesting that session state management under load is a top community pain point.

## Bugs & Stability

### Critical (P1) Issues Reported/Updated Today

| Issue | Severity | Impact | Fix PR Exists? |
|-------|----------|--------|----------------|
| [#86538 - Session write-lock timeouts](https://openclaw/openclaw Issue #86538) | **P1** | Blocks subagent delivery lanes | No — open, needs fix |
| [#80520 - Telegram messages silently dropped](https://openclaw/openclaw Issue #80520) | **P1** | Message loss, no error logged | No — open, needs info |
| [#91363 - Isolated cron LLM failures](https://openclaw/openclaw Issue #91363) | **P1** | Cron jobs fail consistently | No — open, needs live repro |
| [#74586 - AM embedded run aborts memory_search](https://openclaw/openclaw Issue #74586) | **P1** | Tool call timeout misclassification | No — open, needs live repro |
| [#75782 - Embedded-run auth stage 10-15s](https://openclaw/openclaw Issue #75782) | **P1** | Latency bottleneck | No — open, needs live repro |
| [#77642 - Duplicate answers regression](https://openclaw/openclaw Issue #77642) | **P1** | Missing tool results, synthetic errors | No — open, needs live repro |
| [#79752 - Gzip not decompressed Node v26](https://openclaw/openclaw Issue #79752) | **P1** | Discord/HTTP failures on macOS | No — open, needs live repro |
| [#78055 - Subagent stale output](https://openclaw/openclaw Issue #78055) | **P1** | Stale completions delivered | No — open, needs source repro |

### Regressions (P1-P2)

- **Discord channel loading broken** in 2026.5.4+ (Issue #77930) — regression in beta.2/beta.3 vs beta.1 and 2026.4.29
- **Bare `/new` and `/reset` no longer trigger persona greeting** (Issue #77733) — regression in 2026.5.3
- **Bare /new and /reset no longer trigger persona greeting** (Issue #77733) — regression in 2026.5.3 vs 4.x

### Security Impact Issues

| Issue | Impact | Status |
|-------|--------|--------|
| [#78308 - Channel-mediated approval for MCP tools](https://openclaw/openclaw Issue #78308) | Security | Open, needs security review |
| [#80213 - Skill author-defined setup hook](https://openclaw/openclaw Issue #80213) | Security | Open, needs security review |
| [#86881 - Gateway-lite mode](https://openclaw/openclaw Issue #86881) | Security | Open, needs security review |
| [#94147 - macOS CLLocationManager TCC abuse](https://openclaw/openclaw Issue #94147) | Security | Open, Chinese-language report on macOS permission bug |

## Feature Requests & Roadmap Signals

### Top User-Requested Features (by engagement)

| Issue | Feature | Engagement | Likelihood for Next Release |
|-------|---------|------------|----------------------------|
| [#75](https://openclaw/openclaw Issue #75) | Linux/Windows desktop apps | **110 comments, 81 👍** | Medium — massive demand but large scope |
| [#79077](https://openclaw/openclaw Issue #79077) | Telegram bot-to-bot and guest-bot modes | **8 comments, 8 👍** | High — Telegram recently released these features |
| [#78301](https://openclaw/openclaw Issue #78301) | Plugin loader: better validation errors | **5 comments, 2 👍** | Medium — operator frustration is high |
| [#79458](https://openclaw/openclaw Issue #79458) | i18n for slash command descriptions | **5 comments, 1 👍** | Low — P3 priority |

### Roadmap Signals

1. **SQLite storage migration (Path 3):** Issues #88838, #79902, #79903, #79904, #79905 all point toward a major architectural shift. Active implementation PR #96625 is the single Path 3 lane. Expected in next 1-2 releases.

2. **Channel portfolio expansion:** Telegram guest/bot-to-bot support (#79077), Gateway-lite mode (#86881), and Mattermost improvements point to multi-channel as a strategic focus.

3. **Developer experience:** Feature requests for setup hooks (#80213), better plugin validation (#78301), and i18n (#79458, #79034) suggest community wants easier plugin development.

## User Feedback Summary

### Pain Points (Frequency)

1. **Session state reliability** — multiple P1 bugs around write-locks, delivery failures, and silent message drops are the most common urgent complaint
2. **Latency in multi-agent setups** — non-default agents suffer 10-17s initialization overhead (Issue #80607), auth stages block for 10-15s (#75782)
3. **Regression anxiety** — several regressions in recent releases (Discord #77930, greetings #77733) suggest testing coverage gaps
4. **Plugin development friction** — silent contract failures (#78301), no setup hooks (#80213)

### Positive Signals

- New release with community-contributed features (Slack, Mattermost, per-DM overrides)
- Heavy community engagement in issue triage and PR review
- Long-standing bugs being closed (#50248, #83184, #86827)
- Active maintainer presence on critical Path 3 migration

## Backlog Watch

### Long-Unanswered Important Issues

| Issue | Created | Days Open | Priority | Nature |
|-------|---------|-----------|----------|--------|
| [#77642 - Duplicate answers regression](https://openclaw/openclaw Issue #77642) | 2026-05-05 | **56** | P1 | Regression blocking user experience |
| [#80520 - Telegram messages silently dropped](https://openclaw/openclaw Issue #80520) | 2026-05-11 | **50** | P1 | Complete message loss |
| [#74586 - AM embedded run aborts memory_search](https://openclaw/openclaw Issue #74586) | 2026-04-29 | **62** | P1 | Tool timeout misclassification |
| [#79077 - Telegram bot-to-bot/guest support](https://openclaw/openclaw Issue #79077) | 2026-05-07 | **54** | P2 | Platform parity — 8 upvotes |
| [#78308 - MCP approval envelope](https://openclaw/openclaw Issue #78308) | 2026-05-06 | **55** | P2 | Security feature |

### PRs Awaiting Maintainer Action (Most Stale)

| PR | Created | Days Open | Status |
|----|---------|-----------|--------|
| [#65205 - Discord Activities support](https://openclaw/openclaw PR #65205) | 2026-04-12 | **79** | Waiting on author |
| [#65783 - Memory surrogate pairs fix](https://openclaw/openclaw PR #65783) | 2026-04-13 | **78** | Waiting on author |
| [#64546 - Mattermost HMAC forge fix](https://openclaw/openclaw PR #64546) | 2026-04-11 | **80** | Needs proof |
| [#62682 - Terminal abort vs retryable failure](https://openclaw/openclaw PR #62682) | 2026-04-07 | **84** | Ready for maintainer look |
| [#62063 - Swedish UI locale](https://openclaw/openclaw PR #62063) | 2026-04-06 | **85** | Waiting on author |

**Concern:** Several security-adjacent PRs (e.g., #64546 — Mattermost HMAC forgery) have been stalled for 80+ days without maintainer review. Given the security impact labels, this represents a backlog risk.

### Project Health Assessment

| Metric | Value | Assessment |
|--------|-------|------------|
| Issues updated/24h | 500 | Very high community engagement |
| PRs updated/24h | 500 | Heavy development activity |
| Issue close rate | 20.4% (102/500) | Moderate — many issues waiting triage |
| PR merge rate | 9.6% (48/500) | **Low** — significant review bottleneck |
| P1 issues open with no fix | 7 | Concerning — critical bugs unresolved |
| Stale PRs (>50 days) | 6 | Maintainer capacity concern |
| New release | 1 | Active release cadence |

**Overall:** OpenClaw is a highly active project with strong community contributions but faces significant maintainer review bottlenecks. The critical Path 3 SQLite migration appears to be the main engineering focus, while user-facing regressions and message loss bugs accumulate. The upcoming 1-2 releases should prioritize closing the stalled P1 bugs and merging the long-waiting security fixes.

---

## Cross-Ecosystem Comparison

# Cross-Project Ecosystem Comparison Report
**Date:** 2026-06-30

---

## 1. Ecosystem Overview

The open-source personal AI assistant ecosystem is experiencing **sustained hyper-growth**, with seven actively developing projects collectively processing **~1,200+ issues and ~700+ PRs** in a single 24-hour window. The landscape is bifurcating into two tiers: **mature core platforms** (OpenClaw, ZeroClaw, IronClaw, CoPaw) investing in enterprise-grade session management, security hardening, and multi-channel expansion, versus **focused newcomers** (NanoBot, NanoClaw, NullClaw, PicoClaw) prioritizing developer ergonomics, lightweight deployment, and specific integration niches. A common theme across all projects is the **urgent migration toward SQLite-based session storage**, improved **model provider fallback chains**, and **agent-to-agent (A2A) delegation protocols**—indicating the ecosystem is converging on architectural standards while differentiating on channel support, plugin models, and target user personas.

---

## 2. Activity Comparison

| Project | Issues Updated (24h) | PRs Updated (24h) | New Release | Health Score* | Activity Tier |
|---------|---------------------|-------------------|-------------|---------------|---------------|
| **OpenClaw** | 500 | 500 | ✅ v2026.6.11-beta.2 | ⚠️ Moderate | **Hyper-active** |
| **ZeroClaw** | 50 | 50 | ❌ | 🔴 Needs attention | **Very High** |
| **Hermes Agent** | 50 | 50 | ❌ | 🔴 Needs attention | **Very High** |
| **CoPaw** | 30 | 50 | ❌ (v2.0.0-beta.1 pending) | 🟢 Strong | **Very High** |
| **IronClaw** | 6 | 50 | ❌ (release PR #5311 open) | 🟢 Strong | **High** |
| **LobsterAI** | 11 | 40 | ✅ v2026.6.29 | 🟢 Strong | **High** |
| **NanoBot** | 5 | 28 | ❌ | 🟢 Strong | **High** |
| **NanoClaw** | 0 | 9 | ❌ | 🟢 Strong | **Moderate** |
| **NullClaw** | 0 | 4 | ❌ | 🟢 Strong | **Low** |
| **PicoClaw** | 1 | 2 | ❌ | 🟢 Strong | **Low** |
| **ZeptoClaw** | 0 | 0 | ❌ | N/A | **Inactive** |
| **TinyClaw** | 0 | 0 | ❌ | N/A | **Inactive** |
| **Moltis** | 0 | 0 | ❌ | N/A | **Inactive** |

*Health Score: `🟢 Strong` = low critical bugs, active maintainers, good close-to-open ratio. `⚠️ Moderate` = high activity but PR bottleneck. `🔴 Needs attention` = high severity bugs unaddressed, stale critical items.*

---

## 3. OpenClaw's Position

**Advantage:** OpenClaw remains the **ecosystem’s reference implementation** and most trafficked project (500+ issues/PRs daily). It leads in multi-channel maturity (Slack, Mattermost, Telegram, Discord) and has the largest community (500+ active contributors per day). The `v2026.6.11-beta.2` release demonstrates continued feature velocity with community contributions from 6+ external authors.

**Technical Approach Differences:**
- **Session architecture:** OpenClaw is pioneering the **Path 3 SQLite migration** (#88838)—a core architectural shift that other projects (ZeroClaw, CoPaw) are likely to adopt or parallel.
- **Plugin system:** Unlike NanoBot's `Dream` skill generation or ZeroClaw's WASM plugins, OpenClaw uses a **channel-agnostic plugin loader** with staged permissions.
- **Review bottleneck:** While volume is unmatched, OpenClaw's **9.6% PR merge rate** (48/500) is significantly lower than NanoBot (10/28 = 36%) and CoPaw (20/50 = 40%), indicating a scaling challenge in maintainer capacity.

**Community Size Comparison:**

| Metric | OpenClaw | ZeroClaw | CoPaw | NanoBot |
|--------|----------|----------|-------|---------|
| Issues/24h | 500 | 50 | 30 | 5 |
| PRs/24h | 500 | 50 | 50 | 28 |
| Merge rate | 9.6% | ~4%* | 40% | 36% |
| Critical P1s open | 7 | 5 | 3 | 0 |

*Estimated from open vs. closed ratios.

---

## 4. Shared Technical Focus Areas

Multiple projects are converging on these requirements:

### Session State & Storage
| Requirement | Projects | Notes |
|-------------|----------|-------|
| **SQLite session migration** | OpenClaw (#88838), ZeroClaw (#8054 tool-availability ctx), CoPaw (#5571 v2 beta storage) | Core architectural shift |
| **Write-lock reliability** | OpenClaw (#86538, P1), CoPaw (#4873 polling loops) | Parallel execution stress |
| **Transcript persistence** | OpenClaw (#50248 cron sessions), LobsterAI (#2190 cron normalization) | Cron/delayed execution |

### Model Provider Reliability
| Requirement | Projects | Notes |
|-------------|----------|-------|
| **Fallback chain management** | Hermes Agent (#54983 merged), CoPaw (#5572, #5527 vision fallback), ZeroClaw (#5600 Kimi broken) | Multi-provider strategy |
| **Streaming stability** | NanoBot (#4567 WeChat relay), ZeroClaw (#5600 Kimi streaming), NullClaw (#971 native SSE) | Provider-agnostic streaming |
| **Context caching optimization** | CoPaw (#3891 DeepSeek cache 95%), NanoBot (#4222 prefix caching defeat) | Cost reduction priority |

### Agent-to-Agent Communication
| Requirement | Projects | Notes |
|-------------|----------|-------|
| **A2A delegation protocol** | NanoBot (#4571), ZeroClaw (#7218 RFC `.well-known/agent-card.json`) | Interoperability standard |
| **Per-subagent model overrides** | OpenClaw (per-DM overrides), NanoBot (#4570 merged) | Model routing granularity |

### Security Hardening
| Requirement | Projects | Notes |
|-------------|----------|-------|
| **Symlink attack prevention** | NanoClaw (#2828, #2879 merged) | CWE-59 container security |
| **Credential redaction** | NanoBot (#4584 merged, MCP URLs) | Log sanitization |
| **Plugin sandbox limits** | ZeroClaw (#8491 WASM fuel/memory) | Execution isolation |

---

## 5. Differentiation Analysis

| Dimension | OpenClaw | ZeroClaw | CoPaw | NanoBot | Hermes Agent | LobsterAI |
|-----------|----------|----------|-------|---------|--------------|-----------|
| **Primary user** | Advanced tinkerers, multi-channel operators | Rust/CLI developers | Chinese IM users (Feishu/DingTalk) | Developers building custom assistants | Generalist agents, desktop users | Enterprise/team deployment |
| **Language** | TypeScript/Node | Rust | Python | Python | TypeScript/Rust | TypeScript |
| **Channel focus** | Broad (Slack, TG, Discord, Mattermost) | Gateway, WebSocket | Feishu, DingTalk, WeChat | Telegram, WeChat | Desktop CLI/Web | Cowork collaboration |
| **Plugin model** | Channel-agnostic loader | WASM sandboxed | AgentScope 2.0 middleware | Dream skill generator | MCP tools | OpenClaw plugins |
| **Deployment target** | Self-hosted, desktop apps | Container, CLI | Server/IM channel | Lightweight, edge | Desktop, CLI | Enterprise server |
| **Release cadence** | Bi-weekly betas | Sprint-based (v0.8.x) | Major milestones (v2.0 beta) | Continuous (no release) | Weekly patches | Weekly patches |

**Key Differentiation Highlights:**
- **ZeroClaw** is the only project with **WASM-based plugin sandboxing**—a unique security architecture for untrusted code execution.
- **CoPaw** has the **strongest East Asian IM integration** (Feishu, DingTalk, WeChat) with channel-specific UX patterns (tooltip, queue, debounce).
- **NanoBot** offers **unique features**: `Dream` skill auto-generation, `ask_clarification` tool, and **per-provider proxy configuration** for corporate firewalls.
- **Hermes Agent** leads in **desktop/CLI** real-time interaction with native REPL improvements and session continuity.

---

## 6. Community Momentum & Maturity

### Activity Tiers

**Tier 1: Hyper-Active (500+ daily updates)**
- **OpenClaw** — Reference implementation, massive community, struggling with review bottleneck (9.6% merge rate)

**Tier 2: Very High (50-100 daily updates)**
- **ZeroClaw** — Rapid sprint toward v0.8.3, high severity bugs but responsive maintainers
- **Hermes Agent** — Burst of contributions (50 PRs/24h) but low close rate (10%)
- **CoPaw** — Preparing v2.0.0-beta.1, high merge velocity (40%), strong Chinese community

**Tier 3: High (10-50 daily updates)**
- **IronClaw** — Rust-based, enterprise-focused, slow but steady with 19 PRs merged today
- **LobsterAI** — Stabilization phase after v2026.6.29 release, 39 PRs merged
- **NanoBot** — Developer-focused, zero critical bugs, strong PR hygiene (36% merge rate)

**Tier 4: Low/Inactive**
- **NanoClaw, NullClaw, PicoClaw** — Maintenance mode or intermittent bursts
- **TinyClaw, ZeptoClaw, Moltis** — Inactive (0 updates in 24h)

### Maturity Assessment

| Project | Phase | Key Indicator |
|---------|-------|---------------|
| OpenClaw | **Mature but scaling** | Architectural migration (SQLite Path 3) underway |
| CoPaw | **Nearing major release** | v2.0.0-beta.1 installation verification |
| IronClaw | **Stable enterprise** | Release packaging, capability policies |
| ZeroClaw | **Active growth** | v0.8.x tracker, WASM plugin infrastructure |
| NanoBot | **Developmental sprint** | A2A delegation, context compression |
| LobsterAI | **Stabilization** | High merge rate post-release |
| Hermes Agent | **Triage overload** | Low close rate, many P1s open |

---

## 7. Trend Signals

### For AI Agent Developers

1. **Monetization through caching optimization**: DeepSeek's pricing model (4-20x cache hit vs. miss) is driving feature requests across CoPaw and NanoBot. **Cost-aware agent architectures** that optimize prefix caching are becoming a competitive differentiator.

2. **The rise of "silent" and "conditional" agents**: Multiple projects (ZeroClaw #8410, OpenClaw #50248) are addressing the need for **event-driven, no-reply** agents that execute tasks without user-facing output—critical for background automation and cron workflows.

3. **Russian doll architecture**: The trend toward **subagent spawning** with per-subagent model overrides (NanoBot #4570, OpenClaw per-DM overrides) signals that **hierarchical agent teams** with model-level routing are becoming standard practice.

4. **Security as a feature, not an afterthought**: Symlink attack prevention (NanoClaw), credential redaction (NanoBot), WASM sandboxing (ZeroClaw), and channel-mediated approval (OpenClaw) show that **agent security is now a top-tier requirement** for production deployment.

5. **Observability gaps are critical adoption blockers**: Users across OpenClaw, CoPaw, and ZeroClaw consistently report frustration with **"black box" failures**—generic errors when tools fail, invisible caching defeats, and silent message drops. **Surface-level failure diagnostics** (IronClaw #5338, #5403) are becoming a survival feature.

6. **Cross-platform session continuity remains unsolved**: No project has shipped true **session portability** (e.g., desktop → Telegram → desktop) though Hermes Agent (#54981) and OpenClaw are receiving requests. This is the **next frontier for user experience** in personal AI assistants.

7. **Maintainer bottleneck is ecosystem-wide**: Merge rates across all high-activity projects remain below 40%, with OpenClaw at critical 9.6%. **The ecosystem is producing faster than it can consume**, suggesting a need for automated CI/CD pipelines and maintainer delegation models.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

Here is the NanoBot project digest for **2026-06-30**.

---

## NanoBot Project Digest: 2026-06-30

### 1. Today's Overview
NanoBot is experiencing a high-activity sprint, with **28 PRs updated in the last 24 hours**—nearly double the issue activity—indicating a strong push toward feature completion and stabilization. The project has **5 active open issues** and **18 open PRs**, suggesting maintainers are prioritizing code review and integration over new feature requests. The absence of a new release today is expected given the volume of open work currently in the pipeline. Overall, project health is robust, with significant efforts on agent-to-agent delegation, context optimization, and credential security.

### 2. Releases
**No new releases today.** The latest release remains [pending integration of the current open PR batch](/).

---

### 3. Project Progress (Merged/Closed PRs Today)
Ten PRs were closed or merged today, covering major enhancements and critical fixes:

- **Agent-to-Agent Delegation (A2A):** [#4570 (CLOSED)](https://github.com/HKUDS/nanobot/pull/4570) extended the `spawn` tool to allow per-subagent model overrides, closing [#4231]. This allows users to route different subtasks to different models.
- **WebUI Polish:** [#4585 (CLOSED)](https://github.com/HKUDS/nanobot/pull/4585) added default session timestamps and Markdown export in the sidebar, closing [#4579].
- **Security & Config Stability:**
  - [#4583 (CLOSED)](https://github.com/HKUDS/nanobot/pull/4583) fixed a `NoneType` crash in config migration when tool sections are empty.
  - [#4584 (CLOSED)](https://github.com/HKUDS/nanobot/pull/4584) patched a credential leak by redacting URLs in MCP connection logs.
- **API & Provider Enhancements:**
  - [#4502 (CLOSED)](https://github.com/HKUDS/nanobot/pull/4502) added generic and GitHub webhook triggers for the gateway.
  - [#4392 (CLOSED)](https://github.com/HKUDS/nanobot/pull/4392) made tool result microcompaction configurable via `agents.defaults.microcompactToolResults`, addressing cache invalidation complaints.
- **Channels:** [#4567 (CLOSED)](https://github.com/HKUDS/nanobot/pull/4567) fixed a WeChat streaming bug by ensuring LLM calls are buffered, dodging a relay issue that dropped tool-use fields.
- **Other:** [#4554](https://github.com/HKUDS/nanobot/pull/4554) introduced a write guard to prevent Dream from creating duplicate skills.

---

### 4. Community Hot Topics

1. **#660: "Ultra-lightweight" claim vs. Node.js dependency (CLOSED)**
   - [Issue #660](https://github.com/HKUDS/nanobot/issue/660) | 15 comments | 5 👍
   - **Analysis:** This older, now-closed issue ignited a debate on the project's branding. Users felt the `Dockerfile`’s Python + Node.js requirement contradicted the "ultra-lightweight" pitch. The community's underlying need is for a **truly minimal deployment** option. This signal likely drove the recent config/context optimization PRs (#4581, #4588) to reduce runtime bloat.

2. **#4419: Automatic reasoning effort escalation**
   - [Issue #4419](https://github.com/HKUDS/nanobot/issue/4419) | 4 comments | 0 👍
   - **Analysis:** A detailed feature request to dynamically adjust the `reasoningEffort` parameter for models (e.g., default for simple, escalated for complex). The user wants **adaptive intelligence** without manual config toggling. This aligns with the broader "spawn with model presets" (#4291) trend.

3. **#4010: Text-to-Speech / Voice Output**
   - [Issue #4010](https://github.com/HKUDS/nanobot/issue/4010) | 2 comments | 2 👍
   - **Analysis:** Users want to close the voice loop: input exists, output does not. This is a high-signal feature request (2👍 on a quiet issue) for voice-native channels like Telegram/WeChat. Expect a TTS integration in the next major cycle.

---

### 5. Bugs & Stability

| Severity | Bug Description | Issue/PR | Status |
| :--- | :--- | :--- | :--- |
| **High** | **Credential leak:** MCP server URLs containing tokens/userinfo logged as plaintext. | [#4584 (CLOSED)](https://github.com/HKUDS/nanobot/pull/4584) | **Fixed** via redaction. |
| **High** | **Config crash:** `load_config()` crashed with `NoneType` error when `tools.exec` section is null. | [#4583 (OPEN)](https://github.com/HKUDS/nanobot/pull/4583) | **Fixed** via null guard. |
| **Medium** | **WeChat relay failure:** Non-streaming calls to Anthropic relays dropped `tool_use` IDs/names. | [#4567 (CLOSED)](https://github.com/HKUDS/nanobot/pull/4567) | **Fixed** by forcing streaming + buffering. |
| **Medium** | **Prefix caching defeat:** `max_messages` truncation and microcompaction mutate the message prefix every turn, breaking prompt caching. | [#4222 (CLOSED)](https://github.com/HKUDS/nanobot/issue/4222) | **Mitigated** by [#4392](https://github.com/HKUDS/nanobot/pull/4392) (configurable microcompaction). |

**Summary:** Zero critical crashes remain open; two security/crash bugs were patched today.

---

### 6. Feature Requests & Roadmap Signals

Based on merged PRs and high-activity issues, the following features are nearing implementation or are strong candidates for **v0.12.x**:

- **Agent-to-Agent (A2A) Delegation:** [#4571 (OPEN)](https://github.com/HKUDS/nanobot/pull/4571) implements native peer delegation with a depth guard. Likely to merge next sprint.
- **Context Cost Optimization:** [#4581 (OPEN)](https://github.com/HKUDS/nanobot/pull/4581) and [#4588 (OPEN)](https://github.com/HKUDS/nanobot/pull/4588) propose token compression for tool outputs. Addresses the #660 "lightweight" grievance directly.
- **Multi-Provider Proxy Support:** [#4578 (OPEN)](https://github.com/HKUDS/nanobot/pull/4578) adds per-provider proxy config (e.g., for OpenAI Codex behind corporate firewalls).
- **Clarification Tool:** [#4527 (OPEN)](https://github.com/HKUDS/nanobot/pull/4527) adds a built-in `ask_clarification` tool to handle ambiguous user queries, improving agent confidence.
- **Conda Environment Support:** [#4580 (OPEN)](https://github.com/HKUDS/nanobot/issue/4580) requests subprocess execution within conda environments—a strong signal from scientific/ML users.
- **Dream Memory Hygiene:** [#4589 (OPEN)](https://github.com/HKUDS/nanobot/pull/4589) adds directives to prevent MEMORY.md bloat. Expected to merge quickly as it’s prompt-only.

**Prediction:** The next release will likely bundle the **A2A delegation**, **context compression**, and **webhook triggers**.

---

### 7. User Feedback Summary

- **Pain Point – "Lightweight" Branding:** Issue #660 revealed skepticism about the Node.js dependency. Users deploying on edge devices want a **pure Python** or **smaller Docker image**. The PRs #4581/#4588 directly respond to this by reducing token/footprint costs.
- **Pain Point – Caching Invalidation:** Issue #4222 (closed) and PR #4392 (merged) addressed long-standing frustration that context caching was useless. Users are relieved but still want more stable prefix caching.
- **Satisfaction – WebUI:**
  - PR #4585 (session timestamps + Markdown export) was warmly received based on the quick close and linked issue (#4579).
  - The new `ask_clarification` tool (#4527) addresses confusion from open-ended queries, which users dislike.
- **Dissatisfaction – Voice Loop:** Issue #4010 (TTS) has no activity beyond the initial request. Users on voice-first channels (Telegram) remain unsatisfied.

---

### 8. Backlog Watch

- **#4222 (CLOSED, but unaddressed core issue):** The prefix caching defeat is "fixed" by making microcompaction optional (#4392), but the core `max_messages` drift remains. A deeper fix is needed for true caching stability.
- **#4179 (Referenced in PR #4571):** The A2A delegation issue. While PR #4571 exists, it is **not yet merged**. Users waiting for multi-agent teams should watch this PR.
- **#4580 (OPEN, low engagement):** The request for conda environment support has **only 1 comment**. This may indicate lower demand, but it's a blocker for scientific users. Maintainers have not responded.
- **Dream Skill Duplication (#4554):** The merged guard is a band-aid. The root cause—Dream lacking awareness of existing skills—remains unfixed. A more semantic dedup is still needed.

**Maintainer Attention Needed:** The **conda environment request** (#4580) and the **persistent A2A PR** (#4571) are the two highest-priority items awaiting maintainer review.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

Based on the GitHub data for Hermes Agent (NousResearch/hermes-agent) on 2026-06-30, here is the project digest.

---

### Hermes Agent Project Digest — 2026-06-30

**Data Snapshot:** The last 24 hours show extremely high activity with 50 updated issues and 50 updated PRs, indicating a major surge in community and development engagement. The repository saw only 6 closed items (5 merged/closed PRs and 1 closed issue), suggesting a heavy focus on new contributions and triage rather than rapid merging. There were no new releases today.

### 1. Today's Overview
The Hermes Agent project is experiencing a notable spike in activity, with the last 24 hours alone seeing 50 updated issues and 50 updated pull requests. Despite this high volume, the closure rate is very low (1 issue, 5 PRs), suggesting the maintainers are in a heavy triage and review cycle. The influx appears to be driven by a wave of bug reports, feature requests, and security-focused contributions, with the community actively identifying critical edge cases in Docker sandboxing, session management, and credential handling. The project remains in a highly active development state, but the bottleneck is clearly on merging changes rather than filing them.

### 2. Releases
There are **no new releases** to report. The last snapshot remains the same as the previous period.

### 3. Project Progress
Five pull requests were merged or closed today:
- **[PR #54992](https://github.com/NousResearch/hermes-agent/pull/54992):** An invalid PR regarding gateway install profile service was closed.
- **[PR #44042](https://github.com/NousResearch/hermes-agent/pull/44042):** A documentation fix was merged to clarify the `deliver=local` behavior for cron jobs, improving user understanding of save-only delivery.
- **[PR #54983](https://github.com/NousResearch/hermes-agent/pull/54983):** A feature to improve models fallback management was merged, wiring a new backend API and UI panel for managing fallback providers without CLI configuration.
- **[PR #27648](https://github.com/NousResearch/hermes-agent/pull/27648):** The same fallback management feature (potentially a duplicate or backport) was also closed.
- **[PR #54953](https://github.com/NousResearch/hermes-agent/issues/54953):** A bug report regarding unbounded JSON body reads in the Nous billing client was closed.

The main advance is the completion of the **Fallback Chain management feature** (PRs #54983/#27648), which will allow users to manage model fallback providers directly from the web dashboard.

### 4. Community Hot Topics
The most active discussions are centered on high-impact bugs and systemic architectural issues:
- **"Setup sabotages computer integrity"** ([Issue #18357](https://github.com/NousResearch/hermes-agent/issues/18357)): A highly negative report with 5 comments details how the Hermes install script hijacks global npm installs to `~/.hermes/node`, breaking unrelated software. This highlights a critical **user trust and system compatibility** pain point.
- **"Docker cold-start sandbox escape"** ([Issue #54354](https://github.com/NousResearch/hermes-agent/issues/54354), [PR #54982](https://github.com/NousResearch/hermes-agent/pull/54982)): A P2 bug documenting that the first tool call executes on the host OS before the Docker image is pulled. This is a security boundary issue that has drawn significant attention, along with its corresponding fix PR.
- **"Agent Cache Cross-Process Guard"** ([Issue #54947](https://github.com/NousResearch/hermes-agent/issues/54947)): A P0 bug reporting spurious cache invalidation on session-id switches, causing severe performance degradation. Despite the high severity tag, the lack of comments suggests it may be under active investigation internally.
- **Vision Fallback Chain Broken** ([Issue #51513](https://github.com/NousResearch/hermes-agent/issues/51513)): A consolidated report detailing 4 compound bugs rendering the vision fallback chain completely non-functional. This indicates a significant reliability gap in a core feature.

### 5. Bugs & Stability
The project reports a high number of P1, P2, and P0 bugs today, indicating a decline in perceived stability.

**P1 (Critical):**
- **[#54919](https://github.com/NousResearch/hermes-agent/issues/54919):** Hermes fails to launch on Windows due to a UV trampoline error. No fix PR exists yet.

**P0 (Urgent):**
- **[#54947](https://github.com/NousResearch/hermes-agent/issues/54947):** Agent cache cross-process guard spuriously invalidates, causing performance issues.

**P2 (High):**
- **[#18357](https://github.com/NousResearch/hermes-agent/issues/18357):** npm install hijacking/system sabotage.
- **[#54354](https://github.com/NousResearch/hermes-agent/issues/54354):** Docker cold-start sandbox escape (**Fix PR #54982** is open).
- **[#16417](https://github.com/NousResearch/hermes-agent/issues/16417):** Custom provider model names corrupted (`.` replaced with `-`).
- **[#51513](https://github.com/NousResearch/hermes-agent/issues/51513):** Vision fallback chain completely broken.

**P3 (Medium/Low):**
- Several bugs reported include: message leaks between sessions ([#54929](https://github.com/NousResearch/hermes-agent/issues/54929)), gateway going offline ([#53456](https://github.com/NousResearch/hermes-agent/issues/53456)), Docker tool path issues ([#54354](https://github.com/NousResearch/hermes-agent/issues/54354)), and IME/composer edge cases in the desktop app ([#45999](https://github.com/NousResearch/hermes-agent/pull/45999)).

### 6. Feature Requests & Roadmap Signals
The community is requesting significant cross-platform enhancements and developer experience improvements:
- **Cross-Platform Session Continuity** ([#54981](https://github.com/NousResearch/hermes-agent/issues/54981)): Users want to resume a Desktop session from Telegram and vice versa. This is a high-value UX feature likely to be fast-tracked.
- **Hot-Reload Plugins** ([#54941](https://github.com/NousResearch/hermes-agent/issues/54941)): A request for `/reload-plugins` to avoid restarting sessions, signaling a need for more dynamic and user-friendly configuration.
- **LSP Integration** ([#516](https://github.com/NousResearch/hermes-agent/issues/516)): A long-standing feature request for IDE-level code intelligence, which remains a strong roadmap signal.
- **Telegram Rich Markdown** ([#54986](https://github.com/NousResearch/hermes-agent/pull/54986)): An open PR adding an opt-in rich message format for Telegram, indicating a move toward better platform-specific formatting.

### 7. User Feedback Summary
User feedback today is overwhelmingly negative, focusing on installation and security issues:
- **High Dissatisfaction:** The "npm global install hijacking" bug ([#18357](https://github.com/NousResearch/hermes-agent/issues/18357)) has led to accusations of "computer sabotage," reflecting extreme frustration with the installer’s behavior.
- **Cross-Platform Fragility:** Reports from Windows ([#54919](https://github.com/NousResearch/hermes-agent/issues/54919)) and Android (Nix-On-Droid, [#54984](https://github.com/NousResearch/hermes-agent/issues/54984)) show that setup remains unreliable across different operating systems.
- **Quality of Service:** The vision fallback chain being completely broken ([#51513](https://github.com/NousResearch/hermes-agent/issues/51513)) undermines trust in a core feature.
- **Positive Signals:** Despite the bug reports, the community remains engaged by submitting well-structured feature requests (session continuity, plugin reload) and contributive code (Spanish locale, security fixes).

### 8. Backlog Watch
Several important items remain unanswered or require maintainer attention:
- **[Issue #532](https://github.com/NousResearch/hermes-agent/issues/532) (P3, 5 comments):** Feature request for an ephemeral tunnel-based file upload (`/upload` command) is 4 months old but has no assigned milestone.
- **[PR #6826](https://github.com/NousResearch/hermes-agent/pull/6826) (P3, Open):** A feature adding `fastCRW` as a web backend has been open for nearly 3 months without a merge or significant maintainer review.
- **[PR #36960](https://github.com/NousResearch/hermes-agent/pull/36960) (P2, Open):** A bugfix for the Windows `/restart` chain has been open for a month and is tagged `needs-decision`, indicating a stalled review process for a platform-critical fix.
- **[Issue #51513](https://github.com/NousResearch/hermes-agent/issues/51513) (P2, Open):** The report consolidating the broken vision fallback chain was created just a week ago but is a critical user-facing problem that needs immediate resource allocation.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

Here is the structured PicoClaw project digest for **June 30, 2026**.

---

## PicoClaw Project Digest — 2026-06-30

**Source:** github.com/sipeed/picoclaw

### 1. Today's Overview

The project is currently in a **low-activity maintenance phase**, with only two PRs and one issue updated in the last 24 hours. No new releases were cut, and the single active issue was closed due to staleness. The community's primary energy is focused on **completing new gateway integrations** and closing out legacy feature proposals. While there are no recent breaking changes or release notes, the project appears stable but could benefit from a maintainer push to address the backlog.

### 2. Releases

**None.** No new releases were published in the last 24 hours. The latest available version remains unchanged.

### 3. Project Progress

One pull request was closed today (not merged), and one remains open.

- **Closed (Stale):** #2964 **Feat/image_input_compression** — This PR aimed to add configurable inbound image compression for the vision pipeline. It was closed due to inactivity despite describing a clear improvement (multi-level compression policy). The feature was not merged.  
  [GitHub: PR #2964](https://github.com/sipeed/picoclaw/pull/2964)

- **Open (Active):** #3063 **feat: add deltachat gateway** — Authored by `trufae`, this PR remains open after 22 days. It introduces a new gateway for Delta Chat (decentralized messenger), adding both code and documentation. This is the most significant active contribution.  
  [GitHub: PR #3063](https://github.com/sipeed/picoclaw/pull/3063)

**No features were merged today.**

### 4. Community Hot Topics

Only one issue had traction in the last 24 hours:

- **#2984** [Closed] **[Feature][Protocol] Add explicit turn completion signal for Pico WebSocket clients**  
  *Comments: 4 | 👍: 2*  
  This issue requested a deterministic signal (`turn.complete`) for WebSocket clients. It was closed as stale, but the 4 comments indicate genuine demand. Developers want to know exactly when an agent finishes a response, separate from streaming events.  
  [GitHub: Issue #2984](https://github.com/sipeed/picoclaw/issues/2984)

**Takeaway:** The underlying need is **predictable state management** for external clients building conversational UI on top of PicoClaw.

### 5. Bugs & Stability

**No new bugs, crashes, or regressions were reported today.** The only issue closed ( #2984 ) was a feature request, not a bug. No open issues are tagged as bugs.

**Health signal:** Low bug churn indicates stable core functionality, but also potentially unaddressed latent issues.

### 6. Feature Requests & Roadmap Signals

- **Explicit Turn Completion Signal (#2984):** Although closed, this request has strong community support (2 👍, 4 comments) and represents a clear UX gap for WebSocket developers. Predict this will be revisited in a future release (v0.22+).

- **Image Input Compression (#2964):** The PR was not merged but describes a real bottleneck for users sending large images over resource-limited channels. This is a likely candidate for a smaller maintainer-led PR in a minor release.

- **Delta Chat Gateway (#3063):** If merged, this will expand PicoClaw's reach into decentralized messaging, signaling a roadmap shift toward non-encrypted, self-hosted chat integrations.

**Prediction:** The next minor release will likely include the Delta Chat gateway, and possibly a lightweight "turn.complete" event if the core team picks up #2984.

### 7. User Feedback Summary

- **Pain Point:** Developers integrating PicoClaw into custom WebSocket clients are frustrated by the lack of a clear "agent finished" event. They currently rely on heuristics (timers, silence detection) which are unreliable.
- **Use Case Reflected:** Real-time conversational AI deployed in third-party UIs (e.g., dashboards, custom chatbots).
- **Satisfaction:** Neutral. No complaints about core performance or stability, but feature velocity is low. The Delta Chat community appears enthusiastic about the new gateway.

### 8. Backlog Watch

These items have remained unanswered or stale for extended periods and need maintainer attention:

- **#3063 [Open]** *feat: add deltachat gateway* (last updated 1 day ago) — No maintainer review comments. If this PR is viable, it should be merged or given feedback to avoid becoming stale like #2964.  
  [GitHub: PR #3063](https://github.com/sipeed/picoclaw/pull/3063)

- **#2984 [Closed - Stale]** *[Feature][Protocol] Add explicit turn completion signal* — The underlying need remains unmet. A follow-up issue or re-opening via maintainer support is recommended.  
  [GitHub: Issue #2984](https://github.com/sipeed/picoclaw/issues/2984)

- **#2964 [Closed - Stale]** *Feat/image_input_compression* — A clear, scoped PR that was abandoned. Maintainers should assess if the feature is still desired and possibly merge a simplified version.  
  [GitHub: PR #2964](https://github.com/sipeed/picoclaw/pull/2964)

**Conclusion:** Project is stable but risks feature stagnation. Maintainer intervention is needed on the backlog to prevent valuable community contributions from going stale.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

# NanoClaw Project Digest — 2026-06-30

## Today's Overview
NanoClaw shows **moderate activity** today with zero new issues but **9 pull requests being updated in the last 24 hours**, of which **3 were closed or merged**. No new releases were published. Activity is concentrated on **channel adapter stabilization** (Slack Socket Mode, Discord fixes), **security hardening** (symlink escape containment), and **infrastructure improvements** (dashboard pusher, Coolify deployment). The project is in a **consolidation phase**, with the core team focusing on closing out feature branches and addressing vulnerability reports rather than shipping new capabilities.

## Releases
**None** — no new versions were published today. The last release remains unspecified.

## Project Progress
**3 PRs merged/closed today**, representing meaningful advances:

- **#2883 (merged)** — `feat: voice-notify v3` — Voice notification summarization now uses 5-category intent routing (`action/silent/navigate/tech_status/notify`), skips code blocks and long tables, and adds a runtime kill-switch (`VOICE_SUMMARY_VERSION=off`). All 38 tests passing. *(Author: tier2tech-tian)*
- **#2882 (merged)** — `fix(ncl): default messaging-groups create instance to channel_type` — Resolves a `NOT NULL` constraint violation on the `instance` column by ensuring the generic CRUD layer includes the field. *(Author: omri-maya)*
- **#2879 (merged)** — `fix(agent-to-agent): containment-check target inbox in forwardAttachedFiles` — Patches symlink-follow vulnerability (CWE-59) in agent-to-agent attachment forwarding, mirroring existing defensive patterns in `session-manager.ts`. *(Author: johnmathews)*

## Community Hot Topics
The most active contributions today show a **focus on channel expansion and security**:

- **#2884 (OPEN)** — *feat(discord): add Discord channel adapter* — Substantial addition of a Discord Gateway-mode adapter with reply-context extraction and a fix for approval-button routing. Signals strong community interest in multi-platform support. [Link](https://github.com/nanocoai/nanoclaw/pull/2884)
- **#2885 (OPEN)** — *fix(setup): offer Slack Socket Mode in the guided setup flow* — Addresses a merge gap where Slack Socket Mode was added to the `channels` branch but never reached `main`, leaving the trunk setup flow still webhook-only. [Link](https://github.com/nanocoai/nanoclaw/pull/2885)
- **#2871 (OPEN)** — *feat(dashboard): add dashboard pusher with OpenCode support* — Adds a 60-second state snapshot POSTer to a `@nanoco/nanoclaw-dashboard` server, suggesting growing interest in observability infrastructure. [Link](https://github.com/nanocoai/nanoclaw/pull/2871)

**Underlying need**: The community clearly wants **production-grade multi-channel support** (Discord, Slack Socket Mode) and **operational visibility** (dashboards, deployment recipes).

## Bugs & Stability
**Two security bugs reported with fix PRs today**, both related to symlink-follow attacks (CWE-59):

| Severity | Issue | Fix PR |
|----------|-------|--------|
| **Critical** | #2828 — Arbitrary host file write via symlink in inbox attachment writes | **#2880 (OPEN)** — Contains symlink escapes in `src/session-manager.ts` using `lstat`, `realpath`, `isPathInside`, and exclusive write flags |
| **Critical** | #2828 (A2A variant) — Attachment forwarding follows symlinked target inbox | **#2879 (MERGED)** — Same defensive pattern applied to cross-agent attachment flows |

**Other fixes:**
- **#2881 (OPEN)** — Discord button `custom_id` delimiter parsing bug: raw `\n` delimiter not decoded, causing `resolveSelectedOption` failures. *(Author: jeevesforjoel)*
- **#2882 (MERGED)** — CLI `ncl messaging-groups create` crashing with `NOT NULL` constraint violation.

## Feature Requests & Roadmap Signals
Based on open PRs and recent merges, likely next-version candidates:

1. **Discord channel adapter** (#2884) — Likely to merge next, completes the multi-channel story alongside Slack
2. **Slack Socket Mode on main** (#2885) — Blocked by branch strategy, but clearly intended for trunk
3. **Dashboard pusher** (#2871) — Signals shift toward production observability; may be gated by dashboard server readiness
4. **Coolify deployment support** (#2875) — Container/skill PR for self-hosted deployments, suggests demand for non-Docker Compose deployment paths

**Predictions**: Next version will likely include Discord support, Slack Socket Mode, the dashboard pusher, and the voice-notify v3 features already merged.

## User Feedback Summary
While no direct user comments were present in today's data, the following **pain points are inferable** from the issue/pr content:

- **Setup friction**: Slack Socket Mode missing from main's guided setup forces users into webhook-only mode, a clear UX regression (#2885)
- **CLI reliability**: `ncl messaging-groups create` was silently failing for users due to missing column declaration (#2882)
- **Security concerns**: The symlink-follow vulnerabilities (#2828) suggest users are running agent containers in multi-tenant or semi-trusted environments
- **Voice automation needs**: The voice-notify v3 features suggest users need smarter filtering for audio summaries in operational contexts

## Backlog Watch
**No long-unanswered issues or PRs** were identified in today's data. All open PRs are under a week old and actively maintained. The project appears well-groomed, with maintainers responding to PRs within 1–2 days. The only item worth monitoring is **#2885** (Slack Socket Mode setup fix) — it depends on a branch-merge decision that could delay its arrival on `main`.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

Here is the project digest for **NullClaw** on **2026-06-30**.

---

# NullClaw Project Digest — 2026-06-30

## 1. Today's Overview
NullClaw saw low-activity maintenance today with zero new Issues opened and no new releases. However, there was a flurry of PR activity (4 PRs updated) primarily focused on improving the developer and user experience for the CLI agent. A previously closed PR on CLI input handling was re-opened, suggesting a reversion or a refinement was necessary. The project remains stable, with maintainer attention directed toward polishing the streaming tool-calling path and the interactive REPL.

## 2. Releases
**No new releases today.** The latest stable release remains unchanged.

## 3. Project Progress
One PR was closed/merged today, and one was updated (re-opened) for the same feature area:

- **[#960 (CLOSED)] fix(cli): handle arrow keys in agent REPL**
  - Author: vernonstinebaker | Updated: 2026-06-29
  - Summary: Added a low-level, allocation-free line editor for the `nullclaw agent` REPL, enabling POSIX raw-mode for proper arrow key, history, and cursor navigation. This PR was initially closed but has a follow-up (see below).
  - Link: [PR #960](https://github.com/nullclaw/nullclaw/pull/960)

- **[#970 (OPEN)] fix(cli): handle arrow keys in agent REPL**
  - Author: vernonstinebaker | Created: 2026-06-29
  - Summary: A nearly identical re-submission of PR #960. This likely includes additional fixes or rebasing after the initial closure.
  - Link: [PR #970](https://github.com/nullclaw/nullclaw/pull/970)

## 4. Community Hot Topics
Activity was low on discussion (no comments or reactions on recent items), but two PRs stand out as the most technically significant:

- **#971 — Native tool calls during SSE streaming** (OPEN)
  - *Underlying need:* Users want providers that support native tool calls during streaming to work correctly, rather than being downgraded to prompt-injection tool formats. This directly impacts latency and output quality for streaming agents.
  - Link: [PR #971](https://github.com/nullclaw/nullclaw/pull/971)

- **#970 / #960 — Arrow key handling in REPL** (OPEN / CLOSED)
  - *Underlying need:* Developers using the interactive CLI agent need a usable terminal experience. The re-submission indicates the fix required iteration.
  - Link: [PR #970](https://github.com/nullclaw/nullclaw/pull/970)

## 5. Bugs & Stability
- **No new bugs or crashes reported today.**
- **Severity:** None. The project appears stable in terms of user-reported regressions.

## 6. Feature Requests & Roadmap Signals
No explicit feature requests were filed today. However, based on the PRs, the following roadmap signals are visible:

- **High Priority — Enhanced streaming tool integration:** PR #971 indicates the team is actively decoupling native tool call support from the streaming path. This is a strong candidate for the next minor version, as it unblocks providers with native streaming tooling.
- **Medium Priority — CLI UX polish:** The REPL arrow key handling (PR #970) is a quality-of-life fix that will likely land in a patch release soon.

## 7. User Feedback Summary
There is no new direct user feedback (comments, reactions) in the data. Based on the PR activity:
- **Pain points:** The current agent REPL is difficult to use for long interactive sessions (control characters printed instead of cursor movement). Additionally, streaming with native tools is broken.
- **Use cases:** Developers using NullClaw for interactive terminal agents and streaming applications.
- **Satisfaction:** Likely neutral; these are technical fixes rather than feature requests, indicating the core product is stable but the polish layer needs attention.

## 8. Backlog Watch
- **#956 — [dependencies, docker] ci(deps): bump alpine from 3.23 to 3.24**
  - Author: dependabot[bot] | Updated: 2026-06-29
  - Status: **OPEN** (no maintainer review)
  - Risk: Low. This is a routine base image bump. If left unmerged for too long, the Docker images will lag behind security patches in the Alpine 3.24 release.
  - Link: [PR #956](https://github.com/nullclaw/nullclaw/pull/956)

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

Here is the IronClaw project digest for 2026-06-30.

---

## IronClaw Project Digest — 2026-06-30

### 1. Today's Overview
The project is in a **high-activity phase**, with 50 pull requests updated in the last 24 hours, split evenly between open (31) and merged/closed (19). While no new releases were cut, the team is aggressively pushing toward a release, with the release preparation PR (#5311) still open. Core contributors are focused on **WebUI v2 localization, real-time tool activity display, and surfacing specific failure details** to agents and users. Six issues were updated, with one significant bug closed and a daily failure taxonomy report filed, indicating a healthy discipline around observability and regression tracking.

### 2. Releases
**No new releases today.** The most recent release candidate is being prepared in PR #5311, which packages breaking changes across `ironclaw_common` (0.4.2 → 0.5.0) and `ironclaw_skills` (0.3.0 → 0.4.0). No migration notes are available yet.

### 3. Project Progress (Merged/Closed PRs Today)
19 PRs were closed or merged. Notable advances include:

- **Rust Toolchain Upgrade** (#5405, closed): Workspace Rust version raised from 1.92 to 1.96, centralizing MSRV and updating Docker build surfaces.
- **Advisory Management** (#5408, closed): A cargo-deny ignore was added for an unreachable Wasmtime WASI advisory (`RUSTSEC-2026-0188`), keeping CI green without an urgent dependency bump.
- **CI Stability** (#5400, closed): Fixed Windows clippy failures and stabilized extension crate name parsing in CI, improving cross-platform reliability.
- **Dependency Updates** (#5391, closed): Bumped 8 dependencies including `agent-client-protocol` (0.10.4 → 1.0.0) and `webpki-roots` (1.0.7 → 1.0.8).

### 4. Community Hot Topics
No single issue or PR attracted significant comment traffic in the last 24 hours. However, the following items show sustained engineering attention:

- **Capability Policy (E2E)** (#5394, open): Tied to Issue #5385, this XL-sized PR implements fine-grained user permission policies (owner/admin/member). This is a foundational feature for multi-tenant and enterprise deployments.
- **Failure Detail Surfacing** (#5338, open, #5403, open): Two PRs and a closed bug (#5196) attack the same root cause: when a tool or capability fails, the model/user gets a generic error instead of actionable details. This is the most active thematic area, with multiple contributors working to "un-strip" error messages while protecting secrets.
- **Release Preparation** (#5311, open): The release PR carries breaking API changes, indicating major internal refactoring is landing soon.

### 5. Bugs & Stability

| Severity | Issue | Summary | Fix Status |
|----------|-------|---------|------------|
| **Medium** | #5196 *(CLOSED)* | "Ask each time" tool permission fails with auth error, triggers duplicate approval flow | **Closed** – fix appears landed |
| **Low** | #5412 *(OPEN)* | WebUI v2 log entry text not selectable/copyable | No fix PR yet; unassigned |
| **Low** | #4108 *(OPEN)* | Nightly E2E scheduled run failed (2nd occurrence since May 27) | Unassigned; likely CI flakiness |
| **Info** | #5411 *(OPEN)* | Daily failure taxonomy (2026-06-29): 111 non-pass tasks in pinchbench with DeepSeek-V4-Flash, dominant failure category is "model/provider errors" | Used to guide the fix work in #5403 |

**Analysis**: The most impactful bug from the user perspective (duplicate approval flow, #5196) has been closed. The E2E nightly flakiness (#4108) is a long-running stability concern, currently open for over a month.

### 6. Feature Requests & Roadmap Signals

- **Capability Policy System** (#5385, open): A fine-grained user permission model (admin/member/owner) is under active development. This is a strong candidate for the **next release** as it directly supports enterprise self-hosting use cases.
- **Final-Answer Nudge for Interactive Runs** (#5304, open): Will prevent empty turn closures in chat, improving user experience for conversational agents. Likely to land soon.
- **Global Auto-Approve Settings** (#4776, closed): The ability to set global always-allow rules for tools has been implemented in the Reborn WebUI. This bridges the gap between security (ask each time) and convenience.

### 7. User Feedback Summary
- **Pain Point (Resolved)**: The "Ask each time" tool permission flow was producing authorization errors and requiring double approval. This has been fixed in #5196.
- **Pain Point (Open)**: Logs in WebUI v2 cannot be selected or copied (#5412), which is a significant usability regression for debugging and monitoring.
- **Use Case Advancement**: The Capability Policy (#5385) directly addresses the need for **role-based access control** in multi-user IronClaw instances, a frequent request from community and enterprise adopters.
- **Transparency Improvement**: The daily failure taxonomy (#5411) and the work to surface detailed failure reasons (#5338, #5403) show the team is actively addressing the "black box" problem where agents fail without explanation.

### 8. Backlog Watch
- **#4108 – Nightly E2E Failed**: Open since **May 27** (33 days). This recurring CI failure is a potential sign of flaky tests or an underlying stability issue that has not been prioritized. It may be blocking PR merges or masking other regressions.
- **#4841 – "No run-borking failures"**: Open since **June 13** (17 days). This XL-sized PR aims to eliminate terminal errors that kill runs without recovery. It has not been merged, suggesting the scope is complex or dependencies (like the failure detail work in #5338) are being landed first.
- **#5412 – WebUI Logs Not Selectable**: Only one day old but filed as a `P2` bug. Given the high volume of UI polish work in flight, this may get picked up quickly if it impacts developer workflow.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

# LobsterAI Project Digest — 2026-06-30

## 1. Today's Overview

The project maintains a **high level of release-cycle activity**, with **40 PRs updated in the last 24 hours** (1 open, 39 merged/closed) and a **new release (2026.6.29)** promoted to main. The issue tracker saw **11 updated issues** (8 open/active, 3 closed), with several long-standing issues receiving attention after months of inactivity. The release consolidation is clearly the dominant theme — the team is aggressively merging fixes, reverting accidental merges, and stabilizing the OpenClaw and Cowork subsystems. **Project health is strong** but there is visible friction around cron session handling, plugin approval routing, and conversation rail UX that are being addressed in real-time.

## 2. Releases

**New Release: [LobsterAI 2026.6.29](https://github.com/netease-youdao/LobsterAI/releases/tag/2026.6.29)** (released 2026-06-29)

Key changes:
- **OpenClaw fixes**: Plugin approvals now properly routed through permissions; user-turn cache stability preserved; agent bootstrap workspace kept separate from task `cwd`; cron run follow-up history preserved.
- **Cowork fixes**: Cleaned navigation rail previews; conversation rail tooltip, hover, and lazy-navigation fixes reapplied.
- **General**: Route plugin approvals through Cowork permissions.

**No breaking changes or migration notes** are documented. The release is a **stabilization patch** containing multiple backports from the `v2026.6.1` patch cycle.

## 3. Project Progress

39 PRs were merged/closed today. The distribution across areas:

| Area | Count | Key Changes |
|------|-------|-------------|
| **OpenClaw** | ~12+ | Cron session sync, legacy storage migration, plugin preinstallation (QQ, Discord, NIM), run-cwd patch, approval routing |
| **Cowork** | ~8+ | Conversation rail tooltips, navigation cleanup, revert/reapply cycles |
| **Renderer** | ~6+ | Alignment of OpenClaw metadata expectations, scheduled-task state clarification |
| **Docs** | ~4+ | AGENTS.md refresh, repository guidance updates |
| **Dependencies** | ~2 | Electron bump from 40.2.1 to 42.5.0 |

**Notable feature advancements:**
- **Preinstalled OpenClaw plugins**: QQ and Discord channels are now preinstalled via the existing `openclaw.plugins` flow ([PR #2198](https://github.com/netease-youdao/LobsterAI/pull/2198)) — indicating expansion of IM channel integration.
- **Cron session model improved**: Run-scoped cron session keys now normalize to a stable per-agent/per-job cache key, so repeated runs reuse one local Cowork session ([PR #2190](https://github.com/netease-youdao/LobsterAI/pull/2190)).
- **NIM plugin runtime compiled**: Shared TypeScript plugin package preparation extracted; NIM channel's TypeScript-only runtime entry now compiled before OpenClaw CLI installation ([PR #2186](https://github.com/netease-youdao/LobsterAI/pull/2186)).

## 4. Community Hot Topics

The most active Issues/PRs (highest comment counts) are all **older issues receiving renewed attention** after being stale:

| # | Title | Comments | Status | Area |
|---|-------|----------|--------|------|
| [#2079](https://github.com/netease-youdao/LobsterAI/issues/2079) | Execution result window freezes when scrolling to top | 2 | Open | UI |
| [#2131](https://github.com/netease-youdao/LobsterAI/issues/2131) | LobsterAI support for Hermes agent? | 2 | Open | Feature Request |
| [#2120](https://github.com/netease-youdao/LobsterAI/issues/2120) | Suggestions: task queue, runtime limit, UI layout | 2 | Open | UX / Feature |
| [#2121](https://github.com/netease-youdao/LobsterAI/issues/2121) | Suspicion of bug: repeated output consuming tokens | 2 | Open | Bugs |

**Underlying needs analysis:**
- **#2121** (repeated output consuming tokens) is a **blocker-level concern** — if verified, it suggests a memory leak or chat-loop bug in the Cowork/OpenClaw runtime that could silently drain user credits.
- **#2120** (task queue, runtime limit, UI layout) reflects a **power-user workflow gap**: users want to batch tasks without losing monitoring continuity.
- **#2131** (Hermes agent support) signals interest in **multi-agent interoperability** — users want to plug external agent frameworks into LobsterAI.

## 5. Bugs & Stability

**Severity: High**
- **[#2121](https://github.com/netease-youdao/LobsterAI/issues/2121) — Repeated output consuming tokens**: User reports that Claw is outputting repeated text, potentially wasting tokens. No fix PR identified yet. **No response from maintainers** (0 comments from dev team).

**Severity: Medium**
- **[#2079](https://github.com/netease-youdao/LobsterAI/issues/2079) — Execution result window freezes when scrolling to top**: Reproducible freeze on 2026.5.27. Still open after a month.
- **[#1388](https://github.com/netease-youdao/LobsterAI/issues/1388) — Email configuration test connectivity hangs indefinitely**: Stale for ~3 months. No resolution.

**Severity: Low** (all stale, all >2 months old, but recently updated on 2026-06-29)
- [#1386](https://github.com/netease-youdao/LobsterAI/issues/1386) — Share screenshot truncates long conversations.
- [#1389](https://github.com/netease-youdao/LobsterAI/issues/1389) — English language: Chinese selection items show English.
- [#1390](https://github.com/netease-youdao/LobsterAI/issues/1390) — Scheduled task update sometimes unresponsive.

**Recent fix PRs** for related stability concerns:
- #2222, #2223 — Cowork conversation rail tooltip cleanup fixes visual bugs.
- #2217 — OpenClaw plugin approval routing fix.
- #2219 — User-turn serialization cache stability fix.
- #2220 — Cron run follow-up history preservation.

## 6. Feature Requests & Roadmap Signals

**Hot requests from the community:**

1. **Hermes agent support** ([#2131](https://github.com/netease-youdao/LobsterAI/issues/2131)) — User wants LobsterAI to support the Hermes agent framework. **Prediction**: Given the team's focus on OpenClaw plugin extensibility (QQ, Discord, NIM), Hermes integration is plausible but not imminent — likely 2-3 releases out.

2. **Task queue / pre-input** ([#2120](https://github.com/netease-youdao/LobsterAI/issues/2120), item 1) — User wants to input subsequent tasks while one is running, inspired by Workbuddy. **Prediction**: High probability for next release — the cron session normalization (#2190) and scheduled-task state refinement (#2191) directly address this workflow gap.

3. **Extended single-task runtime** ([#2120](https://github.com/netease-youdao/LobsterAI/issues/2120), item 2) — User experiences `terminated` during long-running data scripts. **Prediction**: Already being addressed — the `cwd` patch and user-turn cache fixes improve stability. Runtime configurability may appear in 2026.7.x.

4. **UI layout: 3-column grid** ([#2120](https://github.com/netease-youdao/LobsterAI/issues/2120), item 3) — User requests 3-column skill display for 2560x1600 screens. **Prediction**: Low priority — the team is focused on functional fixes over cosmetic UI changes.

## 7. User Feedback Summary

**Pain points:**
- **Token waste** — User suspects repeated Claw output is burning through credits ([#2121](https://github.com/netease-youdao/LobsterAI/issues/2121)). This is a **trust-eroding issue** if unaddressed.
- **Subscription policy** — User expressed frustration that 5500 unused subscription credits were reset at month end ([#2081](https://github.com/netease-youdao/LobsterAI/issues/2081)). This is a **business logic / policy complaint**, not a technical bug, but it reflects user dissatisfaction with the pricing model.
- **Stability gaps** — The execution window freeze ([#2079](https://github.com/netease-youdao/LobsterAI/issues/2079)) and long task termination ([#2120](https://github.com/netease-youdao/LobsterAI/issues/2120)) suggest the runtime is still fragile under sustained usage.

**Satisfaction signals:**
- The **high PR merge velocity** (39 merged/closed in 24h) demonstrates responsiveness — users filing bugs around the release date are seeing rapid turnarounds.
- The release notes show systematic improvement in areas users complain about (e.g., cron sessions, plugin approvals, conversation rail).

**Use case patterns:**
- **Data monitoring** (Claw for data fetching) — Users are using Claw as a long-running data pipeline monitor.
- **Batch automation** — Users want to queue tasks without blocking.
- **Multi-agent experimentation** — Users asking about Hermes suggests experimentation with alternative agent runtimes alongside LobsterAI's native OpenClaw.

## 8. Backlog Watch

Stale Issues (>60 days without resolution, no recent maintainer response):

| # | Title | Opened | Last Updated | Notes |
|---|-------|--------|--------------|-------|
| [#1386](https://github.com/netease-youdao/LobsterAI/issues/1386) | Share screenshot truncation | 2026-04-03 | 2026-06-29 | Updated but no fix |
| [#1388](https://github.com/netease-youdao/LobsterAI/issues/1388) | Email config test hangs | 2026-04-03 | 2026-06-29 | No response from maintainer |
| [#1389](https://github.com/netease-youdao/LobsterAI/issues/1389) | Language display bug | 2026-04-03 | 2026-06-29 | Cosmetic, but no fix |
| [#1390](https://github.com/netease-youdao/LobsterAI/issues/1390) | Scheduled task update unresponsive | 2026-04-03 | 2026-06-29 | Intermittent, no fix |
| [#1277](https://github.com/netease-youdao/LobsterAI/pull/1277) | Electron dependency bump | 2026-04-02 | 2026-06-29 | **Open** PR — 89 days stale, dependabot-managed |

**Critical watch item**: [#2079](https://github.com/netease-youdao/LobsterAI/issues/2079) (freeze on scroll) has been open for **one month** with only community comments — no maintainer acknowledgment. Given its reproducibility, this warrants immediate attention.

**Recommendation**: The team should triage the three stale email/screenshot/task bugs (all opened 2026-04-03) — they may be fixed by the ongoing OpenClaw/Cowork stabilization work, but lack of assignees or labels suggests they are invisible to the active development cycle.

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

**Generated from GitHub data (github.com/agentscope-ai/CoPaw)**

---

## Today's Overview

CoPaw shows **very high development activity** today, with 30 updated issues and 50 updated pull requests in the last 24 hours. The project is in a **major milestone transition**: a `v2.0.0-beta.1` release candidate (Issue #5571) is under installation verification, signaling an imminent major version launch. Community engagement remains robust, with 9 issues closed and 20 PRs merged/closed during the period. The backlog of 21 open/active issues suggests active triage is occurring, though several high-impact bugs (DeepSeek cache, tool card counts, model fallback) remain unresolved. Notably, multiple contributors are submitting substantive fixes, including first-time contributor [wananing] with two PRs addressing core tool result handling.

---

## Releases

**No new releases** were published in the last 24 hours. However, Issue #5571 confirms that **QwenPaw v2.0.0-beta.1** is currently undergoing installation verification across platforms, with a deadline of 2026-06-26 14:11 UTC. This beta includes significant architectural changes (Runtime v2, scroll-based context management, Langfuse trace restoration), and its release will likely trigger a wave of community feedback and bug reports.

---

## Project Progress

**20 PRs were merged/closed today**, indicating substantial development throughput. Key merged/closed items include:

- **#5625** (closed, test-label-permission) — Internal CI/label permission testing
- **#5614** (closed, docs(context)) — Updated context management documentation, replacing old backpack analogy with scroll strategy explanation
- **#5601** (closed, fix(channel)) — Restored tool-guard approval notifications to IM channels (Feishu, WeCom, Telegram) after Runtime v2 refactoring broke the pipeline
- **#5511** (closed, fix(observability)) — Restored Langfuse trace grouping via 2.0 hook and middleware integration, a critical fix for users relying on observability
- **#5543** (closed, fix(tool-calls)) — Fixed `functionDeclaration` schema missing `type` field (`"type":"null"` breaking third-party model endpoints)
- **#5505** (closed, fix(MiniMax-M3)) — Fixed bug where MiniMax-M3 image safety rejections were incorrectly cached as `rejects_media=True`, causing subsequent vision requests to be stripped
- **#4939** (closed, feature(cron)) — Added `qwenpaw cron update` subcommand, addressing long-standing user frustration with cron job modification workflow

**Key open PRs advancing the codebase:**
- **#5628** (fix tool card counts) — Directly addresses the highly-voted #5624 bug
- **#5510** (defense-in-depth tool result capping at execution layer) — Prevents context explosion when LLM calls fail, proposed as a fix for #5342
- **#5296** (ADBPG memory REST-only migration) — Removes legacy SQL path for ADBPG long-term memory

---

## Community Hot Topics

### Most Active Issues & PRs

1. **#3891** [OPEN] DeepSeek prefix cache hit rate ~95% — **5 comments, 👍1**  
   *Link: agentscope-ai/QwenPaw Issue #3891*  
   **Analysis:** This long-standing issue (created April 2026, still open) describes a financially significant problem: with DeepSeek's 4-20x price difference between cache hit/miss, even 5% cache misses represent substantial cost waste. The user has documented specific caching patterns and suggests optimization strategies. This issue has remained unresolved for 2+ months, suggesting the fix involves non-trivial changes to the provider prefix caching layer.

2. **#5624** [OPEN] Tool call result card count always shows 1 — **3 comments**  
   *Link: agentscope-ai/QwenPaw Issue #5624*  
   **Analysis:** This bug affects multiple tools (`glob_search`, `read_file`) and has immediate user impact—users cannot trust the UI's summary counts. A fix PR (#5628) was submitted on the same day, indicating the team is prioritizing this. The issue reveals a gap in how AgentScope 2.0's MCP text block results are rendered in the console UI.

3. **#4873** [OPEN] Two subagents cause infinite polling loop, Feishu cannot interrupt — **3 comments**  
   *Link: agentscope-ai/QwenPaw Issue #4873*  
   **Analysis:** A critical usability bug where parallel subagent execution triggers runaway `check_agent_task` loops, rendering the system unusable on Feishu. The inability to interrupt from Feishu (vs. Dashboard) highlights a channel-specific design asymmetry. This bug has been open since June 1, suggesting architectural complexity.

4. **#5342** [OPEN] Hard cap on tool result size at execution layer — **3 comments**  
   *Link: agentscope-ai/QwenPaw Issue #5342*  
   **Analysis:** This defense-in-depth feature request identifies a cascading failure pattern where LLM 502 errors skip the pruning hook, causing context explosion. The proposed PR #5510 directly addresses this, indicating the team agrees with the diagnosis.

5. **#5573** [OPEN] DeepSeek V4 thinking mode 400 errors on non-official endpoints — **3 comments**  
   *Link: agentscope-ai/QwenPaw Issue #5573*  
   **Analysis:** A well-documented bug affecting users of third-party DeepSeek endpoints. The user (self-described non-Python programmer) found the fix themselves but needs maintainer validation. Two distinct 400 errors are identified: missing `reasoning_content` in streaming responses and un-sanitized `type: null` in tool schemas.

### Underlying Needs
The most active threads reveal three community priorities:
1. **Cost optimization** (DeepSeek caching) — Users are sensitive to API pricing differences
2. **UI reliability** (tool card counts, badge display) — Trust in visual feedback is essential
3. **Parallel execution stability** — Multi-agent workflows are breaking core loops

---

## Bugs & Stability

### High Severity (Active, No Fix Yet)

| Issue | Description | Impact | Fix PR? |
|-------|-------------|--------|---------|
| **#4873** | Two subagents cause infinite polling loop, Feishu cannot interrupt | **Critical** — System unusable in parallel scenarios | No |
| **#5573** | DeepSeek V4 thinking mode 400 errors on non-official endpoints | **High** — Blocks usage on third-party DeepSeek endpoints | No (user workaround provided) |
| **#5561** | Long Feishu replies fail, sent as files instead | **High** — Blocks normal communication on Feishu channel | No |

### High Severity (Fix PR Submitted or Merged)

| Issue | Description | Status | Fix PR |
|-------|-------------|--------|--------|
| **#5624/#5626** | Tool card counts always show 1 | Open + PR submitted | #5628 ✅ |
| **#5505** | MiniMax-M3 `rejects_media=True` cached incorrectly | **CLOSED** | Merged ✅ |
| **#5543** | Tool schema `type: null` breaking third-party models | **CLOSED** | Merged ✅ |
| **#5342** | Context explosion when LLM fails | PR #5510 under review | #5510 |

### Medium Severity

- **#5587** (Qwen-Image Tool install error) — Blocks image generation tool installation
- **#5555** (Latest version increasingly laggy) — Performance regression, no specifics provided
- **#5591** (Excessive log spam from inbox polling) — Annoying but non-critical, fixed for Linux
- **#5584** (Cannot connect custom ascend-vllm model) — Regression since v1.1.7, blocks self-hosted deployments

### Regressions
- **#5584** explicitly identifies a regression: v1.1.7 worked, later versions cannot connect to custom models
- **#5555** reports performance degradation in recent versions (though lacking details)

---

## Feature Requests & Roadmap Signals

### Most Requested Features

1. **Model automatic fallback/degradation**  
   Issues: **#5572** (auto-switch on quota exhausted/timeout), **#5527** (dynamic model switching like AgentScope 2.0)  
   *Signals:* Multiple users independently requesting this; one fix suggested in #5527 references AgentScope 2.0's dynamic switching capability. **Likely in v2.0.0-beta.1 or shortly after.**

2. **Conversation checkpoint/save on abnormal shutdown**  
   Issue: **#5579** — Conversation loss on `reboot` commands or crashes  
   *Signals:* Described two real-world scenarios (agent execution of reboot, service crash). **Urgent for production users**, but no PR yet.

3. **DingTalk channel enhancements**  
   Issues: **#5593** (previewable image messages), **#5564** (@mention support), **#5603** (streaming output too slow), **#5621** (sandbox docs)  
   *Signals:* Heavy DingTalk user base with specific IM integration pain points. Multiple PRs address pieces (#5601 for notifications, #5617 for debounce toggle).

4. **Vision fallback for text-only models**  
   Issue: **#5615** — Auto-generate image descriptions when model lacks vision  
   *Signals:* References existing implementations in qclaw/codex. **Would reduce user confusion** when uploading images to non-vision models.

5. **Memory search with reranker**  
   Issue: **#5588** — Two-stage retrieval with dedicated reranker model  
   *Signals:* Well-argued case for improving long-term memory accuracy. References reME service's existing `enable_llm_rerank` option.

### Likely Near-Term Features

- **Tool result hard cap at execution layer** (PR #5510 under review) — Defense-in-depth for context explosion
- **Plugin middleware registration** (PR #5221 open) — Will enable ecosystem extensibility
- **Windows system tray icon** (Issue #5622) — Desktop UX improvement
- **Custom model protocol support** (Issue #5609) — For non-standard API endpoints

---

## User Feedback Summary

### Pain Points

- **"DeepSeek prefix cache hit rate ~95% means I'm overpaying by 5% on every request"** (#3891) — Financially burdensome for heavy users
- **"Latest version is getting laggy"** (#5555) — Performance degradation likely from added features
- **"Cannot connect my custom ascend-vllm model anymore"** (#5584) — Regression blocking self-hosted users
- **"The / slash command can only add one skill at a time"** (#5589) — Minor UX friction in daily workflow
- **"DingTalk streaming output is character-by-character slow"** (#5603) — Frustration with IM response speed
- **"If I reboot my server during a conversation, everything is lost"** (#5579) — Trust issue for critical usage

### Satisfaction Signals

- **"I modified the code myself and it works now, hoping the maintainer can verify"** (#5573) — User invested enough to fix and submit
- **"v1.1.7 could connect, later versions cannot"** (#5584) — Indicates user has been using the project long-term
- **Multiple users asking for model fallback** (#5527, #5572) — Suggests the system is being used for production workloads where reliability matters

### Unmet Expectations

Several users report that "other software works fine" with their custom models (#5584), suggesting CoPaw's model compatibility layer has regressed or is more restrictive than alternatives.

---

## Backlog Watch

### Long-Open Issues Needing Maintainer Attention

| Issue | Age | Status | Why Watching |
|-------|-----|--------|--------------|
| **#3891** DeepSeek prefix cache hit rate | **64 days** (since Apr 27) | OPEN, 5 comments, 👍1 | High financial impact; no maintainer response visible |
| **#4873** Subagent infinite polling + Feishu interrupt | **29 days** (since Jun 1) | OPEN, 3 comments | Critical bug for parallel workflows; no fix PR |
| **#2495** MCP tool list visibility | **92 days** (since Mar 29) | CLOSED but requires verification | Feature already requested 3 months ago; verify if v2.0.0-beta.1 includes this |
| **#5527** Dynamic model switching | **5 days** | CLOSED | User asked about AgentScope 2.0 feature parity — maintainer may want to confirm support in beta |

### PRs Needing Review

- **#5510** (tool result hard cap) — Under Review for 5 days, addresses critical #5342
- **#5296** (ADBPG memory REST-only) — Open for 12 days, significant architectural change
- **#5442** (mission mode + Runtime v2) — Open for 7 days, blocks mission mode feature
- **#5570** (desktop plugin install storm fix) — Open for 4 days, fixes memory exhaustion bug (#5550)

### Release Watch

- **#5571** (v2.0.0-beta.1 installation verification) — Deadline was June 26, 14:11 UTC. As of June 30, this issue has **0 comments**, meaning it may have passed verification silently, or verification is incomplete. **Maintainers should confirm beta release status.**

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

Here is the ZeroClaw project digest for 2026-06-30.

---

## ZeroClaw Project Digest: 2026-06-30

### 1. Today's Overview
Project activity is **very high**, with 50 issues and 50 PRs updated in the last 24 hours, representing a large spike in developer contribution. The majority of issues remain open (44/50) and carry `priority:p1` or `p2` labels, indicating a project in deep active development targeting a `v0.8.x` milestone. A significant cluster of work focuses on **correcting tool-availability mismatches across entry points** (Issue #8054), **enhancing WASM plugin infrastructure**, and **improving CI/security posture**. The maintainer team is highly responsive, with many PRs opened and merged today to address critical bugs and "needs-maintainer-review" items.

### 2. Releases
**No new releases** were published today. The project appears to be in a heavy development sprint between releases, with multiple tracker issues (e.g., #7314, #8071, #8360) coordinating work toward a `v0.8.3` milestone.

### 3. Project Progress
Several pull requests were merged or closed today, advancing key features and stability fixes:

- **Core Runtime & Provider Fixes:**
    - [PR #8500 (closed)](https://github.com/zeroclaw-labs/zeroclaw/pull/8500): Fixed a dependency security issue by bumping `anyhow` to patch `RUSTSEC-2026-0190`.
    - [PR #8419 (closed)](https://github.com/zeroclaw-labs/zeroclaw/pull/8419): Added calendar no-show SOP (Standard Operating Procedure) triggers to the runtime.
- **CI & Security:**
    - [PR #8168 (closed)](https://github.com/zeroclaw-labs/zeroclaw/pull/8168): Added Trivy container scanning for PR and release Docker images.
    - [PR #8388 (closed)](https://github.com/zeroclaw-labs/zeroclaw/pull/8388): Replaced unsafe `.unwrap()` calls with `.expect()` in the tool-call-parser for better error messages.
- **WASM & Plugins:**
    - [PR #8491 (open)](https://github.com/zeroclaw-labs/zeroclaw/pull/8491): Introduced per-call execution limits for WASM plugins (fuel, memory) and a new configuration taxonomy (`[plugins.limits]`).
- **SOP & Event Sources:**
    - [PR #8461 (open)](https://github.com/zeroclaw-labs/zeroclaw/pull/8461): Added a new filesystem event source to the SOP engine, allowing agents to react to file changes.

### 4. Community Hot Topics
The most active discussions highlight deep architectural concerns around tool routing, prompt consistency, and security:

- **[Issue #8054](https://github.com/zeroclaw-labs/zeroclaw/issues/8054) (9 comments):** System prompt tool-availability mismatch across all entry points (channels, gateway, WebSocket). This is a critical follow-up to a previous fix, indicating a systemic architectural flaw in how tool lists are computed per-turn.
- **[Issue #6909](https://github.com/zeroclaw-labs/zeroclaw/issues/6909) (6 comments):** RFC for "Computer-use" support (desktop GUI interaction). A highly requested feature with parallels to competitors like OpenAI Codex, signaling strong market/user demand for desktop automation.
- **[Issue #5600](https://github.com/zeroclaw-labs/zeroclaw/issues/5600) (11 comments):** A blocking bug with the Kimi provider where streaming API calls fail with a "reasoning_content is missing" error. This has been open since April and remains a high-impact pain point for users of that specific provider.
- **[Issue #7218](https://github.com/zeroclaw-labs/zeroclaw/issues/7218) (5 comments):** RFC for A2A (Agent-to-Agent) discovery using `.well-known/agent-card.json`. This groundwork is focused on interoperability with external agent systems, a strategic priority for the "claw" ecosystem.

### 5. Bugs & Stability
Several high-priority bugs were reported or updated, indicating areas of friction in the current build:

- **High Risk:**
    - **[Issue #8410](https://github.com/zeroclaw-labs/zeroclaw/issues/8410) (p2):** Channel tasks lack a first-class "no-reply" outcome. Conditional tasks like "only reply if there is new email" still send a visible response when silent is expected, degrading user experience.
    - **[Issue #8312](https://github.com/zeroclaw-labs/zeroclaw/issues/8312) (p1):** A data-loss bug in the translation tool (`fill-translations`). Stale map entries re-ship leaked text, causing silent data integrity issues. *(Related PR in flight: #8057/8056 CI tasks)*.
    - **[Issue #8334](https://github.com/zeroclaw-labs/zeroclaw/issues/8334) (p1):** The `skills install/list/remove` CLI commands target the wrong data directory for multi-agent installs, breaking the core skill management workflow.
- **Medium Risk:**
    - **[Issue #7862](https://github.com/zeroclaw-labs/zeroclaw/issues/7862) (p1):** OpenAI-compatible providers (e.g., vLLM) receive an empty tool list with `tool_choice: "auto"`, causing HTTP 400 errors. This blocks any request for users of certain local LLM backends.
- **Fix PRs Active:**
    - [PR #8496 (open)](https://github.com/zeroclaw-labs/zeroclaw/pull/8496): Fixes the deferred-MCP (Model Context Protocol) access policy, directly addressing Surface 1(b) of the critical Issue #8054.
    - [PR #8488 (open)](https://github.com/zeroclaw-labs/zeroclaw/pull/8488): Fixes channel prompt tool-availability, directly addressing Surface 1(a) of Issue #8054.
    - [PR #8466 (open)](https://github.com/zeroclaw-labs/zeroclaw/pull/8466): Prevents panics in the gateway pairing database, replacing them with proper error propagation.

### 6. Feature Requests & Roadmap Signals
Today's activity strongly signals a focus on **enterprise readiness, extensibility, and platform maturity** for the `v0.8.x` release.

- **Likely for v0.8.x:**
    - **[#8054](https://github.com/zeroclaw-labs/zeroclaw/issues/8054) & related PRs:** The tool-availability fix is critical and likely to be merged before any release.
    - **[#7314](https://github.com/zeroclaw-labs/zeroclaw/issues/7314) (WASM Plugin Program) & [PR #8491](https://github.com/zeroclaw-labs/zeroclaw/pull/8491) (Execution Limits):** These are part of the v0.8.3 tracker, making WASM plugin sandboxing a top priority.
    - **[#8056](https://github.com/zeroclaw-labs/zeroclaw/issues/8056) / [#8057](https://github.com/zeroclaw-labs/zeroclaw/issues/8057) (CI Security Jobs):** Implementation PRs are being merged, suggesting this will be hardened for the next release.
- **Future Direction:**
    - **[#6909](https://github.com/zeroclaw-labs/zeroclaw/issues/6909) (Computer-Use):** This is a major feature but remains an open RFC, likely targeted for a later release (post-v0.8.x).
    - **[#8170](https://github.com/zeroclaw-labs/zeroclaw/issues/8170) (In-app Upgrade):** A user-visible web dashboard feature for self-updating, which would improve operator UX significantly.

### 7. User Feedback Summary
User pain points are clearly visible in the issue tracker, focusing on **reliability and logical consistency**:

- **Provider Incompatibility (High Pain):** Users of Kimi (Issue #5600) and vLLM (Issue #7862) are experiencing blocked workflows due to API spec mismatches. The long duration of the Kimi bug is a source of dissatisfaction.
- **Confusing UI/UX (Medium Pain):** A user reports that help text and keybindings in the ZeroCode TUI are "misleading or unreachable, especially on macOS" (Issue #7800). This points to a need for better platform-specific documentation.
- **Silent Failures (Medium Pain):** The "NO_REPLY" sentinel text issue (Issue #2128, closed but recent) and the new "no-reply" gap (Issue #8410) show a pattern where conditional silence is not properly handled, causing unwanted noise in channels.
- **Positive Signals (Satisfaction):** The high volume of contributor-led RFCs (e.g., #7218 for A2A, #7497 for OCI registries) and quick turnaround on CI fixes suggests the community is engaged and the maintainers are responsive to technical debt.

### 8. Backlog Watch
Two items require immediate maintainer attention due to their age, severity, or stalled status:

- **[Issue #5600](https://github.com/zeroclaw-labs/zeroclaw/issues/5600) (Bug, Kimi Provider, P1):** Open since April 10, 2026. This is a critical workflow blocker for a specific provider that has not been resolved. The *reasoning_content* error pattern suggests a tight coupling with the streaming architecture.
- **[Issue #6074](https://github.com/zeroclaw-labs/zeroclaw/issues/6074) (Audit, P2):** Open since April 24, 2026. This tracks 153 lost commits from a mass revert. While acknowledged, there has been no visible recovery effort, representing a significant risk of re-introducing old bugs or losing prior bug fixes. This is a structural risk that needs a clear "resurrected" or "will not fix" status.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*