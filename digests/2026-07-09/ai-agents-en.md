# OpenClaw Ecosystem Digest 2026-07-09

> Issues: 500 | PRs: 500 | Projects covered: 13 | Generated: 2026-07-09 02:01 UTC

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

# OpenClaw Project Digest — 2026-07-09

## Today's Overview

OpenClaw continues at extremely high activity levels, with 500 issues and 500 PRs updated in the last 24 hours. The open/active issue count stands at 456, with 44 resolved, while 408 PRs remain open against 92 merged/closed. **No new releases were published today**, suggesting the project is in a stabilization and bug-fixing phase rather than feature rollout. The high volume of open PRs (408) combined with the fact that many critical issues carry the `clawsweeper:needs-maintainer-review` and `clawsweeper:needs-product-decision` labels indicates a growing maintainer bottleneck. Community engagement remains strong, with numerous high-comment issues covering session-state corruption, message loss, and security concerns — several carrying the highest severity rating of `🦞 diamond lobster`.

## Releases

No new releases were published on 2026-07-09. The latest available version remains 2026.6.x series.

---

## Project Progress

**92 PRs were merged or closed today**, indicating active codebase maintenance. Notable changes that advanced:

### 🟢 Merged/Closed Highlights

| PR | Description | Impact |
|---|---|---|
| #99221 (closed) | **GitHub Enterprise data-residency Copilot auth** — `P0` diamond lobster | Enables Copilot authentication against `*.ghe.com` tenants; major enterprise adoption enabler |
| #97730 (closed) | **Tlon auth body bounded at 16 MiB** — prevents OOM on malicious responses | Security hardening |
| #96832 (closed) | **Sandbox skill sync uses config-resolved workspace** — fixes environment mismatch | Developer experience |
| #96723 (closed) | **Anthropic SSE streaming bounded at 16 MiB** (provider path) — prevents resource exhaustion | Stability / security |
| #96701 (closed) | **Anthropic SSE streaming bounded at 16 MiB** (agent transport) — same fix for agent layer | Stability / security |

### 🟡 Open PRs Advancing

Several high-impact PRs remain open with maintainer attention requested:

- **#96230** — `P1` platinum hermit: Stops gateway restart death-loop for wedged main sessions (related to #95750). **Size XL, merge-risk: 🚨 compatibility, session-state, availability**
- **#102284** — `P1` open: Fixes mid-turn context-overflow false positives by estimating pressure after tool-result projection (closes #101929)
- **#101276** — `P1` gold shrimp: Deny-over-allow exec approval denylist (#6615). **Size L, merge-risk: 🚨 compatibility, security-boundary** — re-review with P1 blockers resolved
- **#95419** — `P2` platinum hermit: Keeps isolated cron run status `ok` even when delivery fails (improves monitoring)
- **#95311** — `P1` platinum hermit: `disableBoundaryAwareCache` for DeepSeek/Xiaomi prompt-cache compatibility (closes #94518)
- **#93865** — `P2` platinum hermit: Mattermost thread history backfill after restart (closes #93204)
- **#94050** — `P2` platinum hermit: Strips volatile output from exec result hash to fix no-progress detection (closes #93917)

---

## Community Hot Topics

### 🔥 Most Active Issues

| Issue | Comments | 👍 | Title | Severity |
|---|---|---|---|---|
| [#25592](https://github.com/openclaw/openclaw/issues/25592) | 35 | 1 | Text between tool calls leaks to messaging channels | 🦞 Diamond lobster |
| [#44925](https://github.com/openclaw/openclaw/issues/44925) | 21 | 1 | Subagent completion silently lost — no retry, no notification | 🦞 Diamond lobster |
| [#48003](https://github.com/openclaw/openclaw/issues/48003) | 15 | 3 | Steer mode doesn't inject messages mid-turn for main sessions | 🦞 Diamond lobster |
| [#85333](https://github.com/openclaw/openclaw/issues/85333) | 15 | 1 | `openclaw doctor --fix` 4-5x slower on 2026.5.20 vs 2026.5.19 | 🐚 Platinum hermit |
| [#45740](https://github.com/openclaw/openclaw/issues/45740) | 14 | 1 | gh-issues skill injects untrusted issue body directly into sub-agent prompt | 🦞 Diamond lobster |

**Analysis:** The community is overwhelmingly focused on **session-state corruption and message loss** — the top-5 issues all involve data silently disappearing or being misrouted. Issue #25592 (35 comments) has been open since February 2026 and remains the most-discussed problem: internal processing output leaking to user-facing channels is a fundamental UX failure. Issue #44925 (subagent completion loss) and #48003 (steer mode mid-turn injection) both represent **reliability regressions** that undermine trust in multi-agent orchestration. The fact that these carry `🦞 diamond lobster` (highest severity) with `needs-maintainer-review` and `needs-product-decision` suggests **strategic ambiguity** about how to architect a fix.

### 🔥 Most Requested Features

| Issue | 👍 | Title |
|---|---|---|
| [#39604](https://github.com/openclaw/openclaw/issues/39604) | 11 | Add `tools.web.fetch.allowPrivateNetwork` for private network access |
| [#42840](https://github.com/openclaw/openclaw/issues/42840) | 9 | MathJax/LaTeX support in Control UI |
| [#45608](https://github.com/openclaw/openclaw/issues/45608) | 4 | Pre-reset agentic memory flush before `/new`/daily reset |

**Observation:** The private network access feature (#39604, 11 👍) is a strong signal from **enterprise and self-hosted users** who need agents to operate within their internal infrastructure. The UX polish feature (#42840, 9 👍) suggests academic/science users are active.

---

## Bugs & Stability

### 🚨 Critical (P0 — release-blocking)

| Issue | Title | Status |
|---|---|---|
| [#43661](https://github.com/openclaw/openclaw/issues/43661) | Session hangs indefinitely when compaction times out, causing repeated duplicate message sends | Open, no fix PR |
| [#48920](https://github.com/openclaw/openclaw/issues/48920) | Live Docs are ahead of release — `IsolatedSessions` feature documented but not in latest release | Open, no fix PR |

### 🔴 P1 High Severity (newly active today)

| Issue | Title | Fix PR? |
|---|---|---|
| [#25592](https://github.com/openclaw/openclaw/issues/25592) | Text between tool calls leaks to messaging channels | No |
| [#44925](https://github.com/openclaw/openclaw/issues/44925) | Subagent completion silently lost on timeout | No |
| [#48003](https://github.com/openclaw/openclaw/issues/48003) | Steer mode doesn't inject messages mid-turn | No |
| [#94228](https://github.com/openclaw/openclaw/issues/94228) | Native Anthropic: `thinking` blocks brick long tool-use threads (HTTP 400) | No |
| [#43367](https://github.com/openclaw/openclaw/issues/43367) | Multi-agent orchestration unstable: config overwrites, session-lock failures | No |
| [#99912](https://github.com/openclaw/openclaw/issues/99912) | Agent heartbeat routes to wrong agent's session | No |
| [#38327](https://github.com/openclaw/openclaw/issues/38327) | "Cannot convert undefined or null to object" with google-vertex/gemini-3.1 | No |
| [#45494](https://github.com/openclaw/openclaw/issues/45494) | Cron agent jobs silently time out during LLM API outages instead of fast-failing | No |
| [#45049](https://github.com/openclaw/openclaw/issues/45049) | Agent loop allows simulated tool calls instead of enforcing real tool invocation | No |

### 🟡 P2 Moderate Severity

| Issue | Title | Notes |
|---|---|---|
| [#45740](https://github.com/openclaw/openclaw/issues/45740) | gh-issues skill: untrusted issue body injected into sub-agent prompt (security) | Diamond lobster |
| [#39604](https://github.com/openclaw/openclaw/issues/39604) | No `allowPrivateNetwork` config for `web_fetch` | 11 👍 |
| [#40001](https://github.com/openclaw/openclaw/issues/40001) | Write tool lacks append mode — cron sessions overwrite shared files | Diamond lobster |
| [#43747](https://github.com/openclaw/openclaw/issues/43747) | Memory management in chaos — inconsistent behavior across users | 3 reporters |
| [#43996](https://github.com/openclaw/openclaw/issues/43996) | Sandbox container exits immediately with `no-new-privileges` | Diamond lobster |
| [#45718](https://github.com/openclaw/openclaw/issues/45718) | Session bloat: `skillsSnapshot` and `systemPromptReport` accumulate on every run | Diamond lobster |

### 🔴 Regression Cluster

Three regressions appeared in the P1 category today:
1. **#38327** — google-vertex/gemini-3.1 broken in 2026.3.2 (regression from previous working version)
2. **#45494** — Cron silent timeout regression (was fast-failing before)
3. **#38439** — Webchat avatar endpoint returns 404 regression

### 🛡️ Security Concerns

| Issue | Severity | Description |
|---|---|---|
| [#45740](https://github.com/openclaw/openclaw/issues/45740) | 🦞 Diamond | Untrusted issue body injected into sub-agent prompt (no sanitization) |
| [#45049](https://github.com/openclaw/openclaw/issues/45049) | 🦞 Diamond | Agent simulates tool calls instead of executing real ones — can bypass security controls |
| [#44905](https://github.com/openclaw/openclaw/issues/44905) | 🐚 Platinum | Discord leaks internal tool-call traces (NO_REPLY, raw JSON args) to channel |
| [#43996](https://github.com/openclaw/openclaw/issues/43996) | 🦞 Diamond | Sandbox exits with `no-new-privileges` — container escapes possible |

**Notable:** Three of the top-10 most-commented issues are security-related (#45740, #45049, #44905), indicating a concerning trend where **agent-controlled output is not properly isolated from end-user channels**.

---

## Feature Requests & Roadmap Signals

### Strong Community Demand (10+ 👍)

| Feature | Issue | Votes |
|---|---|---|
| Private network access (`tools.web.fetch.allowPrivateNetwork`) | [#39604](https://github.com/openclaw/openclaw/issues/39604) | 11 |
| MathJax/LaTeX rendering in Control UI | [#42840](https://github.com/openclaw/openclaw/issues/42840) | 9 |
| Pre-reset agentic memory flush | [#45608](https://github.com/openclaw/openclaw/issues/45608) | 4 |

### Predicted Next-Release Candidates

1. **OpenAI `refusal` field handling** — Three separate PRs (#102334, #102349, #102344) all address users seeing blank responses when OpenAI returns safety refusals. This is a **high-probability fix** for the next patch release, as multiple contributors independently identified and fixed the same bug.

2. **Exec approval denylist** — PR #101276 (deny-over-allow exec approval) has P1 status, maintainer review cleared, and supersedes an inactive author's work. Likely to merge soon.

3. **Anthropic image MIME type sanitization** — PR #102337 fixes HEIC/TIFF 400 errors. Small, targeted, urgent for iOS/iPhone users.

### Strategic Signals

- **Distributed Agent Runtime** (RFC #42026 — 3 👍, diamond lobster maturity): Proposes splitting gateway into control plane + agent compute. This would address many session-state and crash-loop issues by isolating agent processes. Given the ongoing stability problems, this RFC is likely to gain maintainer mindshare.
- **Gateway lifecycle hooks** (#43454, diamond lobster): onSubagentComplete, onToolCallThreshold, onTurnComplete — would enable better observability without polling. Community interest is moderate but the use case is clear.
- **Per-agent cost budgets** (#42475, diamond lobster): Daily/monthly spend caps enforced at gateway level. With `P2` priority and diamond lobster rating, this is likely on the roadmap for operators tired of runaway costs.

---

## User Feedback Summary

### 😡 Major Pain Points

1. **"My agent's internal processing is visible to users"** — #25592 (35 comments): Text between tool calls, error handling, and acknowledgments leak to Slack/iMessage channels. Users report confusion and privacy violations.

2. **"Subagent work is silently lost"** — #44925 (21 comments), #43367 (13 comments): Multi-agent orchestration is unreliable. Agents time out without notification, config gets overwritten under concurrent access, and child work detaches from the parent session.

3. **"Memory management is a mess"** — #43747 (9 comments): Three users report radically different memory behavior (one uses SQLite, one uses files, one never sees memory persist). Configuration is non-deterministic.

4. **"Performance regression: `doctor --fix` is 4-5x slower"** — #85333 (15 comments): A specific upgrade made a common command take 229 seconds vs 55 seconds. Users blame a "session snapshot path traversal bottleneck."

5. **"I see blank replies when OpenAI refuses content"** — Multiple duplicates: Safety refusals (e.g., "I cannot provide that information") are silently dropped, making the assistant appear broken.

### 😊 Positive Signals

- **Community is self-organizing**: Three independent contributors submitted PRs for the same OpenAI refusal bug, indicating strong developer engagement and a functioning review process.
- **Enterprise interest is growing**: GitHub Enterprise Copilot auth (#99221), private network access (#39604), and cost budgeting (#42475) all point to enterprise adoption.
- **Documentation is being produced**: Even though live docs are ahead of releases (#48920), the fact that users follow the docs suggests they find them useful and trust them.

### Use Cases Reported

- Telegram forum bots (multi-agent group chat)
- Discord community assistants (tool-call leaks reported here)
- GitHub issue triage automation (using gh-issues skill)
- Cron-based data processing (file overwrite issues)
- Browser automation (email provider signups)
- Scientific/mathematical communication (LaTeX request)
- Multi-user team deployments (memory inconsistency across colleagues)

---

## Backlog Watch

### 🔴 Critical Items Needing Maintainer Attention

| Issue | Age | Severity | Last Updated | Status |
|---|---|---|---|---|
| [#25592](https://github.com/openclaw/openclaw/issues/25592) | 136 days | 🦞 Diamond | 2026-07-09 | `needs-maintainer-review`, `needs-product-decision` |
| [#44925](https://github.com/openclaw/openclaw/issues/44925) | 119 days | 🦞 Diamond | 2026-07-09 | `needs-maintainer-review`, `needs-product-decision` |
| [#48003](https://github.com/openclaw/openclaw/issues/48003) | 116 days | 🦞 Diamond | 2026-07-09 | `needs-maintainer-review`, `needs-product-decision` |
| [#43367](https://github.com/openclaw/openclaw/issues/43367) | 121 days | 🦞 Diamond | 2026-07-09 | `needs-maintainer-review`, `needs-product-decision` |
| [#41744](https://github.com/openclaw/openclaw/issues/41744) | 122 days | 🦞 Diamond | 2026-07-09 | `needs-maintainer-review`, `needs-product-decision` |
| [#40001](https://github.com/openclaw/openclaw/issues/40001) | 124 days | 🦞 Diamond | 2026-07-08 | `needs-maintainer-review`, `needs-product-decision` |
| [#45740](https://github.com/openclaw/openclaw/issues/45740) | 118 days | 🦞 Diamond | 2026-07-08 | `needs-maintainer-review`, `needs-product-decision` |

### 🟡 Stale Issues Needing Revival

| Issue | Age | Description |
|---|---|---|
| [#41744](https://github.com/openclaw/openclaw/issues/41744) | 122 days | Feishu image tool loses media — `stale` label, diamond lobster |
| [#45314](https://github.com/openclaw/openclaw/issues/45314) | 119 days | Early abort response templates not populated — `stale` label, diamond lobster |
| [#45765](https://github.com/openclaw/openclaw/issues/45765) | 118 days | `OPENCLAW_HOME` nesting bug — `stale` label, diamond lobster |
| [#46252](https://github.com/openclaw/openclaw/issues/46252) | 118 days | Cost dashboard omits archive files, undercounting spend — `stale` label |

### ⚠️ Merge-Risk PRs Waiting for Review

| PR | Risk Flags | Status |
|---|---|---|
| [#96230](https://github.com/openclaw/openclaw/pull/96230) | 🚨 compatibility, session-state, availability | `ready for maintainer look` |
| [#101276](https://github.com/openclaw/openclaw/pull/101276) | 🚨 compatibility, security-boundary | `waiting on author` (re-review done) |
| [#95419](https://github.com/openclaw/openclaw/pull/95419) | 🚨 compatibility, message-delivery | `ready for maintainer look` |
| [#95311](https://github.com/openclaw/openclaw/pull/95311) | 🚨 compatibility, auth-provider | `ready for maintainer look` |
| [#93865](https://github.com/openclaw/openclaw/pull/93865) | 🚨 session-state, availability | `ready for maintainer look` |
| [#97189](https://github.com/openclaw/openclaw/pull/97189) | 🚨 security-boundary, availability | `waiting on author` |

### Trend Analysis

The backlog is **dominated by session-state and message-loss issues that have been open for 115-136 days**. All carry `clawsweeper:needs-maintainer-review` and `clawsweeper:needs-product-decision`, indicating that maintainers have not yet determined the strategic approach for these architectural problems. The growing pile of `stale`-labeled diamond lobster issues suggests **maintainer burnout or prioritization bottlenecks** — these are high-severity bugs that simply aren't getting attention. The simultaneous existence of 408 open PRs and 456 open/active issues, with many carrying maintainer-review labels, supports this interpretation.

---

## Health Indicators Summary

| Metric | Value | Assessment |
|---|---|---|
| Issues updated/24h | 500 | 🟢 Extremely active |
| PRs updated/24h | 500 | 🟢 Extremely active |
| Open issues | 456 | 🟡 High — sustainable if triaged |
| Open PRs | 408 | 🟡 Very high — risk of review bottleneck |
| New releases today | 0 | 🟡 Expected during stabilization |
| Diamond lobster issues open | ~25 | 🔴 High severity concentration |
| Issues with `needs-maintainer-review` | Majority | 🔴 Maintainer bottleneck |
| Security issues | 3+ active | 🟡 Concerning — needs prioritization |
| PRs with merge-risk flags | 10+ | 🟡 High — each could break session-state or compatibility |

**Overall:** OpenClaw is healthy in community engagement but **stressed in maintainer capacity**. The project is generating rapid improvement (92 merged PRs today) but accumulating architectural debt (session-state, message-loss, security boundary issues) that requires strategic decisions. Users are increasingly frustrated by silent failures and data leaks, while the maintainer team appears to be carefully deliberating solutions rather than rushing fixes. The next release will likely focus on **stabilization and security hardening**, with OpenAI refusal handling and Anthropic image MIME fixes being strong immediate candidates.

---

## Cross-Ecosystem Comparison

Here is the cross-project comparison report based on the July 9, 2026 digest data.

---

## Cross-Project Ecosystem Comparison Report
**Date:** 2026-07-09
**Scope:** OpenClaw, NanoBot, Hermes Agent, PicoClaw, NanoClaw, IronClaw, LobsterAI, TinyClaw, Moltis, CoPaw, ZeroClaw (11 projects)

### 1. Ecosystem Overview

The open-source personal AI assistant ecosystem is experiencing a period of **rapid maturation bifurcated by scale**. While the flagship project (OpenClaw) struggles with maintainer bottlenecks and architectural debt from session-state corruption, a second tier of projects (CoPaw, ZeroClaw, NanoClaw) is shipping beta features and stabilizing production workloads at breakneck velocity. A clear pattern has emerged: **multi-agent orchestration** and **context-window reliability** are the defining technical challenges of 2026, with nearly every project reporting data loss or session leakage as a top user complaint. Despite these growing pains, the community is self-organizing, with first-time contributors submitting high-quality patches for security vulnerabilities and provider compatibility across the ecosystem, signaling a healthy and sustainable developer base.

### 2. Activity Comparison

| Project | Open Issues | Open PRs | Release Today | Health Score | Assessment |
|---|---|---|---|---|---|
| **OpenClaw** | 456 | 408 | ❌ No | 🟡 Stressed | High community engagement, severe maintainer bottleneck |
| **NanoBot** | ~20 | 17 | ❌ No | 🟢 Healthy | Security-focused maintenance cycle |
| **Hermes Agent** | 45 | 47 | ✅ Yes (v0.18.2) | 🟢 Healthy | Very high activity, patch release shipped |
| **PicoClaw** | 2 | 0 | ❌ No | 🟢 Stable | Low activity, steady maintenance |
| **NanoClaw** | ~4 | ~24 | ❌ No | 🟢 Very High | Major feature train (scheduled tasks) |
| **IronClaw** | 21 | 39 | ❌ No | 🟢 High | Large refactor push (NEA-25) |
| **LobsterAI** | ~3 | ~3 | ❌ No | 🟡 Moderate | High fix cycle, clearing stale debt |
| **TinyClaw** | 0 | 0 | ❌ No | 🟢 Clean | No activity, post-audit lull |
| **Moltis** | 0 | 1 | ❌ No | 🟢 Quiet | Very low activity, single open PR |
| **CoPaw** | ~39 | ~47 | ✅ Yes (v2.0.0-beta.4) | 🟢 High | Beta stress-testing, responsive triage |
| **ZeroClaw** | 50 | 37 | ❌ No | 🟢 High | Architectural convergence on WASM plugins |

**Key Observation:** OpenClaw alone accounts for **86% of all open issues** (456/536) and **68% of open PRs** (408/601) in the ecosystem. This extreme concentration is both a sign of its dominance and a risk—bottlenecks at OpenClaw ripple across the ecosystem as projects dependent on it (PicoClaw, TinyClaw) wait for architectural decisions.

### 3. OpenClaw's Position

**Advantages:**
- **Dominant community gravity:** 500 issues/PRs updated daily dwarfs every other project (next closest: ZeroClaw at 100 updates).
- **Enterprise partnerships:** GitHub Enterprise Copilot auth support (#99221) and private network access requests signal high-value enterprise adoption.
- **Deepest provider support:** Anthropic, Google Vertex, OpenAI, DeepSeek, Plus all major channels (Slack, Mattermost, Discord, Telegram).

**Technical Approach Differences:**
- **Architecture:** Monolithic gateway design with composable agents vs. ZeroClaw's WASM plugin model and NanoClaw's TypeScript-first approach.
- **Security boundary:** OpenClaw's agent-controlled output isolation is weaker than peers—text leaks (#25592) and tool-call simulation (#45049) are unique to its architecture.
- **Review process:** Maintainer-driven vs. CoPaw's and NanoBot's community-inclusive review (3 first-time contributors merged in CoPaw today).

**Community Size:**
- OpenClaw's top issues have **35, 21, 15 comments** vs. ZeroClaw (13), CoPaw (12), suggesting 2-3x higher engagement per issue.
- **Maintainer bandwidth:** OpenClaw has 408 open PRs vs. 47 (CoPaw) and 37 (ZeroClaw)—a 5-10x ratio, suggesting either more contributors or slower reviews.

### 4. Shared Technical Focus Areas

The following requirements are emerging independently across multiple projects, indicating ecosystem-wide priorities:

| Requirement | Projects Affected | Common Pain Points |
|---|---|---|
| **Session-state reliability & data loss prevention** | OpenClaw, Hermes, CoPaw, ZeroClaw | Transcript deletion, message loss, silent reply drops, context corruption |
| **Multi-agent isolation** | OpenClaw, LobsterAI, NanoClaw | Config overwrites across agents, session-lock failures, IM channel collision |
| **Security hardening for SSRF / prompt injection** | OpenClaw, NanoBot, ZeroClaw, TinyClaw | Untrusted issue body injection, tool-call simulation, unauthorized token minting |
| **Context window overflow management** | OpenClaw, Hermes, CoPaw, ZeroClaw | Hallucination, infinite loops, compression erasing context, tool-call repetition |
| **OpenAI / provider compatibility** | OpenClaw, NanoBot, Hermes, ZeroClaw, CoPaw | Refusal field dropped, thinking blocks bricking threads, model routing failures |
| **Non-interactive / headless configuration** | NanoBot, NanoClaw, ZeroClaw | `--refresh` flags, automated deployments, CI/CD integration |
| **Cron / scheduled task reliability** | OpenClaw, Hermes, CoPaw, ZeroClaw, NanoClaw | Silent timeouts, file overwrites, "No thread attached" errors |
| **Desktop app UX parity** | Hermes, CoPaw, ZeroClaw | Zoom reset, CJK text cutoff, minimize-to-tray, stale status indicators |
| **Documentation vs. release alignment** | OpenClaw, CoPaw | Live docs ahead of releases, features documented but not shipped |

### 5. Differentiation Analysis

| Dimension | OpenClaw | NanoBot | Hermes | NanoClaw | CoPaw | ZeroClaw |
|---|---|---|---|---|---|---|
| **Target user** | Enterprise ops, multi-channel power users | DevOps, security-conscious | Desktop-first power users | Teams/enterprise scheduling | Production autonomous agents | WASM extenders, developers |
| **Primary language** | TypeScript | Python | Python | TypeScript | Python | Rust |
| **Architecture** | Monolithic gateway + composable agents | Modular Python packages | Desktop app + gateway | CLI-first, control-plane | Beta v2.0 unified | WASM plugin + OpenAI adapter |
| **Deployment** | Docker, self-hosted | pip, Docker | Desktop app (macOS/Windows) | pnpm, Docker | Docker, cloud | Rust binary, Docker, macOS |
| **Key innovation** | Deep multi-channel support | Security-first design | Desktop UX maturity | Scheduled tasks as infrastructure | Autonomous mode reliability | Plugin ecosystem via WASM |
| **Weakness** | Maintainer bottleneck, session bugs | Lower feature velocity | Windows UX gaps, data loss | Smaller community | Fresh install breakage | Desktop platform gaps |

### 6. Community Momentum & Maturity

**Tier 1 — Rapid Iteration (beta/active development):**
- **CoPaw:** 15 PRs merged today, shipped v2.0.0-beta.4, triaged 24 issues. Highest velocity per maintainer ratio.
- **ZeroClaw:** 13 PRs merged, WASM plugin track converging, SSRF audit complete. Architectural maturity increasing.
- **NanoClaw:** 4 PRs merged, 6-part scheduled tasks train in motion. Highest feature density with smallest team.

**Tier 2 — Stabilization & Hardening:**
- **OpenClaw:** 92 PRs merged, but 408 still open. Community engagement high, but maintainer throughput is the constraint. Session-state issues remain unresolved for 115+ days.
- **Hermes Agent:** 3 PRs merged, patch release v0.18.2 shipped. Desktop focus with many open UX fixes.
- **IronClaw:** 11 PRs merged, deep refactor (NEA-25) but P2 bugs from bug bash unresolved.

**Tier 3 — Maintenance / Low Activity:**
- **NanoBot:** Security patch cycle complete, low new feature velocity.
- **PicoClaw, TinyClaw, Moltis, ZeptoClaw:** One or zero active PRs. TinyClaw and Moltis have zero open issues.

### 7. Trend Signals

1. **"Silent failure is the new security breach."** OpenClaw (#25592), ZeroClaw (#6034), and CoPaw (#5846) all report issues where agents complete work without delivering output to users. Trust in autonomous agents depends on observability—this is the #1 architectural gap across the ecosystem.

2. **The WASM plugin model is winning.** ZeroClaw’s investment in WASM plugins (tracker #8850) and NanoBot’s modular Python packages represent a shift from monolithic agents to plugin-based architectures. OpenClaw’s monolithic gateway may face competitive pressure.

3. **Desktop users are underserved.** Hermes, CoPaw, and ZeroClaw all report broken Desktop experiences (macOS permission detection, Windows zoom reset, CJK text rendering). This is a significant growth opportunity for any project that can deliver a polished native experience.

4. **Multi-agent isolation is a prerequisite for enterprise adoption.** LobsterAI (#2293), OpenClaw (#43367), and NanoClaw (#2921) all struggle with config/session contamination between agents. Enterprise customers deploying multiple agents per team need strict tenant isolation.

5. **Cron/scheduled tasks are the killer app.** NanoClaw is building a 6-part feature train around them; CoPaw ships auto-approval fixes specifically for unattended operation; ZeroClaw agents don't even know they can use cron (#5862). Agents running on a schedule—not just interactive chat—is where the real productivity gains lie.

6. **Developer experience is converging on CLI-first.** NanoBot’s `--refresh` flag, NanoClaw’s `ncl tasks` resource, and ZeroClaw’s enhanced `file_read` tool all point to a trend: the CLI is the primary interface for power users, with UI being secondary polish.

7. **Provider diversity is a liability.** Every project has at least one bug related to OpenAI/Anthropic/LLM provider compatibility. The ecosystem needs a standardized provider abstraction layer that handles refusal, thinking blocks, image formats, and streaming edge cases uniformly.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

Here is the NanoBot project digest for July 9, 2026.

---

## NanoBot Project Digest for 2026-07-09

### 1. Today's Overview
The project is in a highly active maintenance and security cycle today, with a heavy focus on resolving a recently discovered cluster of vulnerabilities and stabilizing core infrastructure. Activity is very high: 8 issues were closed, and 17 pull requests remain open alongside 9 that were merged or closed. The development team is moving quickly to patch the WebUI bootstrap token vulnerabilities while also advancing features like guided setup flows, non-interactive configuration, and MCP reliability.

### 2. Releases
No new releases were published today.

### 3. Project Progress
Several key improvements and fixes were merged or closed today:

- **Security Fixes (Merged):**
    - **PR #4849** ([link](https://github.com/HKUDS/nanobot/pull/4849)): **Gate bootstrap API token issuance.** Splits WebSocket tokens from REST API tokens, requiring `tokenIssueSecret` or static `token` for API access. This directly closes security issues #4825, #4826, and #4827.
    - **PR #4856** ([link](https://github.com/HKUDS/nanobot/pull/4856)): **Restore localhost bootstrap API tokens.** Restores localhost access while keeping remote bootstrap blocked, providing a balanced fix for the token-minting vulnerability.
- **Refactoring (Merged):**
    - **PR #4848** ([link](https://github.com/HKUDS/nanobot/pull/4848)): Extracts turn hook assembly logic into a dedicated module (`nanobot.agent.turn_hooks`), improving code organization and testability.
- **Enhancements (Merged):**
    - **PR #4852** ([link](https://github.com/HKUDS/nanobot/pull/4852)): Implements `nanobot onboard --refresh`, enabling non-interactive configuration file updates for automated deployments.
- **Documentation (Merged):**
    - **PR #4850** ([link](https://github.com/HKUDS/nanobot/pull/4850)): Improves search entry pages and moves the heavy News block in the README to a release archive.

### 4. Community Hot Topics
The most active discussions center on critical vulnerabilities and infrastructure stability:

- **Security Vulnerability Spikes:** Issues #4825, #4826, and #4827 ([link](https://github.com/HKUDS/nanobot/issues/4825), [link](https://github.com/HKUDS/nanobot/issues/4826), [link](https://github.com/HKUDS/nanobot/issues/4827)) are a trio of closely related security reports filed on July 7th. They all detail the same core flaw: the WebUI bootstrap endpoint (`/webui/bootstrap`) mints API-capable bearer tokens to any unauthenticated localhost process. The maintainer reacted quickly, closing all three issues concurrently as PR #4849 was merged. The underlying need is for a clear authentication boundary between localhost convenience and remote security.

- **Persistent Prompt History Issue:** Issue #2463 ([link](https://github.com/HKUDS/nanobot/issues/2463)), closed today after being stale, remains a foundational architectural concern. The discussion (13 comments) reveals that NanoBot persists conversation history in a form different from the actual prompt prefix sent to the model, causing conflicts with OpenAI’s prompt caching mechanism. The deep need is for a more faithful persistence model to ensure API compliance and reproduceable AI behavior.

### 5. Bugs & Stability
Several bugs were identified, with fix PRs already in progress for the most severe:

- **Critical (Security): Unauthenticated WebUI Token Minting.** Issues #4825, #4826, #4827, and #4078 ([link](https://github.com/HKUDS/nanobot/issues/4078)) expose API endpoints that accept unauthenticated requests. **Fix PRs #4849 and #4856 are merged**, closing these issues.
- **High (Stability): MCP Reconnect Gateway Crash.**
    - **PR #4843** ([link](https://github.com/HKUDS/nanobot/pull/4843)): Fixes a crash during MCP reconnect by deferring stale `AsyncExitStack` cleanup.
    - **PR #4764** ([link](https://github.com/HKUDS/nanobot/pull/4764)): Provides an alternative fix to prevent gateway crashes during MCP streamable-http reconnects.
- **High (Stability): Zombie Processes.** **PR #4840** ([link](https://github.com/HKUDS/nanobot/pull/4840)) aims to fix a critical issue where zombie child processes are not reaped on all subprocess exit paths.
- **Medium (Bug): Slack Dependency Missing.** Issue #4829 ([link](https://github.com/HKUDS/nanobot/issues/4829)) reports that `aiohttp` is missing from the Slack plugin dependencies in `pyproject.toml`, preventing the Slack plugin from working.
- **Medium (Bug): Broad Exception Handling.** **PR #4816** ([link](https://github.com/HKUDS/nanobot/pull/4816)) proposes fixing an over-broad `BaseException` catch in tool execution that could swallow critical exceptions like `KeyboardInterrupt` and `SystemExit`.

### 6. Feature Requests & Roadmap Signals
Several features indicate likely directions for upcoming releases:

- **Non-Interactive Configuration:** Issue #4851 and PR #4852 (merged) add support for `nanobot onboard --refresh`, enabling automated, scriptable configuration updates. This suggests a growing need for devops-friendly, headless deployments.
- **RTK Command Rewriter:** PR #4854 ([link](https://github.com/HKUDS/nanobot/pull/4854)) introduces an opt-in RTK command rewriter for the `exec` tool, indicating a push toward safer, more controlled code execution environments.
- **Guided Setup Flows:** PR #4855 ([link](https://github.com/HKUDS/nanobot/pull/4855)) adds a productized setup surface for Channels with guided actions and validation, suggesting a focus on improving the initial user onboarding experience.
- **Sustained Goals Runtime Mode:** PR #4844 ([link](https://github.com/HKUDS/nanobot/pull/4844)) gates the "long goal" skill behind an explicit runtime mode, separating background goals from standard conversations.
- **Core Timer Tool:** PR #4853 ([link](https://github.com/HKUDS/nanobot/pull/4853)) adds a lightweight `nano_timer` tool for time, timezone, and calendar information, a low-risk utility likely to be accepted.

### 7. User Feedback Summary
The feedback cycle is heavily skewed towards security and reliability this week.

- **Pain Points:**
    - **Security Concerns:** The most acute pain is the unauthorized token minting vulnerability (#4825, #4826, #4827), which fundamentally undermines trust in local deployments.
    - **Configuration Friction:** Users managing automated deployments explicitly requested a non-interactive config refresh (#4851), highlighting that the current interactive `onboard` command is a barrier to automation.
    - **Documentation Inconsistency:** A PR (#4847) notes that the README advertises LangSmith integration as a working feature, but users report it is broken. This mismatch between documentation and reality is a source of frustration.
- **Use Case Signals:**
    - The Docker build-time dependency override (PR #4857) shows users want to customize their containerized NanoBot images beyond the default `whatsapp` extras.
    - The MCP stability fixes indicate that NanoBot is being used in environments where streamable-http MCP servers are a core architectural component.

### 8. Backlog Watch
The following items require maintainer attention or have remained unresolved for an extended period:

- **Issue #2463 (Closed, Persistent):** While closed today as stale, the underlying architectural issue of prompt-prefix preservation remains unresolved. This is a significant technical debt item that could lead to compliance issues with providers like OpenAI. **Needs a dedicated architectural proposal.**
- **PR #2873** ([link](https://github.com/HKUDS/nanobot/pull/2873)): An open PR from April 6th to fix Discord forwarded message handling. This has been open for over 3 months and needs a review.
- **PR #4460** ([link](https://github.com/HKUDS/nanobot/pull/4460)): A chore to bump Node.js to version 24, which was merged today, is a positive sign that the backlog of infrastructure updates is being addressed.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

# Hermes Agent Project Digest — July 9, 2026

## 1. Today's Overview

Hermes Agent is experiencing **very high activity** with 50 issues and 50 PRs updated in the last 24 hours, alongside a new patch release. The project has **45 open issues** and **47 open PRs**, indicating a vibrant but possibly stretched maintainer team. A same-day patch release (v0.18.2) addressed a critical Docker build dependency for WhatsApp integration. The community is highly engaged, particularly around Desktop app UX issues, gateway reliability, and feature requests for better session management. Today saw numerous new PRs targeting Python 3.14 compatibility, security pin updates, and bug fixes across the agent runtime.

## 2. Releases

### v2026.7.7.2 — Hermes Agent v0.18.2 (same-day patch)

- **Date:** July 7, 2026
- **Patch content:** Fixes WhatsApp Baileys dependency — unpinned from a git commit to use the published `7.0.0-rc13` release, resolving tagged-release Docker build failures.
- **Breaking changes:** None.
- **Migration notes:** No user-facing changes required.

## 3. Project Progress

**Merged/Closed PRs today (3 total):**

- **[#2270 — feat(gateway): Add Blooio as a first-class messaging platform](https://github.com/nousresearch/hermes-agent/pull/2270)** — Adds webhook-based inbound/outbound messaging, attachments, typing indicators, and thread support for Blooio, achieving parity with Telegram/Signal. This is a significant new gateway integration.

**Notable open PRs actively advancing fixes and features (no merged PRs yet today beyond #2270):**

- [#61247 — Preserve global providers in desktop model pickers](https://github.com/nousresearch/hermes-agent/pull/61247) — Fixes disappearing providers (e.g., `openai-codex`) after first message.
- [#61245 — fix(desktop): re-apply UI zoom after minimize/restore on Windows](https://github.com/nousresearch/hermes-agent/pull/61245) — Fixes Windows zoom reset after window cycling.
- [#61244 — fix(compressor): add return_exceptions=True to asyncio.gather](https://github.com/nousresearch/hermes-agent/pull/61244) — Prevents unhandled exceptions in trajectory compressor from crashing concurrent processing.
- [#61223 — feat(tools): add guarded codex exec bridge](https://github.com/nousresearch/hermes-agent/pull/61223) — New `codex_exec` tool for delegating repo work to Codex CLI.
- [#61224 — fix: Python 3.14 compatibility (3 separate commits)](https://github.com/nousresearch/hermes-agent/pull/61224) — Fixes `daemon_pool` worker signature, gateway liveness argv, and dotenv reload race.
- [#61227 — fix(checkpoint): gc with a prune grace window](https://github.com/nousresearch/hermes-agent/pull/61227) — Prevents dangling refs from concurrent GC operations.
- [#61228 — fix(agent): robust handling of context-window overflow on strict endpoints](https://github.com/nousresearch/hermes-agent/pull/61228) — Clamps `max_tokens` for strict endpoints like vLLM.
- [#61221 — fix(process_registry): background spawns inherit the venv environment](https://github.com/nousresearch/hermes-agent/pull/61221) — Fixes background processes crashing due to wrong Python interpreter.
- [#61222 — fix(prompts): KANBAN_GUIDANCE clarifies workers have their full toolset](https://github.com/nousresearch/hermes-agent/pull/61222) — Fixes workers blocking tasks due to misunderstanding available tools.
- [#53248 — fix: add per-job allow_silent flag for recurring jobs](https://github.com/nousresearch/hermes-agent/pull/53248) — Allows opting out of `[SILENT]` suppression for briefing/report jobs.
- [#54235 — fix: kill entire process tree on Windows to prevent GUI program hang](https://github.com/nousresearch/hermes-agent/pull/54235) — Fixes Windows GUI programs causing session hangs.
- [#54554 — fix(matrix): add MATRIX_ALLOWED_ROOMS_APPLY_TO_DMS for multi-profile isolation](https://github.com/nousresearch/hermes-agent/pull/54554) — Fixes Matrix DM room allowlist bypass for multi-profile setups.
- [#60829 — fix(web): harden desktop webapp chat and mobile controls](https://github.com/nousresearch/hermes-agent/pull/60829) — Adds browser-safe `<iframe>` fallback and mobile style fixes.
- [#58429 — fix: case-insensitive provider matching in model picker](https://github.com/nousresearch/hermes-agent/pull/58429) — Fixes `custom:My-Provider` not showing in Desktop model picker.
- [#58634 — fix(projects): add projects.enabled config toggle](https://github.com/nousresearch/hermes-agent/pull/58634) — Gates the v0.18 project subsystem behind a config toggle for backward compatibility.
- [#61248 — chore(deps): refresh security-sensitive pins](https://github.com/nousresearch/hermes-agent/pull/61248) — Updates `cryptography`, `python-multipart`, `starlette`, `pydantic-settings`, `tornado`, `Pygments`, and `pytest`.

## 4. Community Hot Topics

### Most Active Discussions

1. **[#39691 — feat(compression): integrate headroom-ai for tool output compression](https://github.com/nousresearch/hermes-agent/issues/39691)** (9 comments, 12 👍)
   - **Need:** Users want smarter, granular context compression beyond full-window LLM summarization. Proposes using headroom-ai to compress individual tool outputs, preserving more useful context while reducing token usage. High community interest suggests this is a priority feature.

2. **[#13891 — [CLOSED] Matrix gateway unable to decrypt message](https://github.com/nousresearch/hermes-agent/issues/13891)** (10 comments)
   - **Need:** Matrix users experience decryption failures after extended use, requiring room recreation. This closed issue reflects a long-standing pain point that was finally resolved or mitigated.

3. **[#59224 — Classic CLI /resume listing hides Desktop sessions](https://github.com/nousresearch/hermes-agent/issues/59224)** (8 comments)
   - **Need:** CLI users find Desktop-created sessions invisible in `/resume` listings. Cross-launcher session management is a clear usability gap for multi-surface users.

4. **[#569 — Feature: Agent Client Protocol (ACP) Server Mode](https://github.com/nousresearch/hermes-agent/issues/569)** (2 comments, 9 👍)
   - **Need:** Strong community desire to use Hermes inside editors (Zed, JetBrains, Neovim) via the ACP standard. This is a high-visibility integration request that would expand Hermes' reach significantly.

5. **[#18241 — TUI show thinking blocks and tool calls in chronological order](https://github.com/nousresearch/hermes-agent/issues/18241)** (2 comments, 4 👍)
   - **Need:** TUI users want chronological interleaving of thinking and tool calls from reasoning models, not grouped by type. This affects debugging and understanding agent behavior with modern reasoning models.

6. **[#50718 — Session visibility & notifications](https://github.com/nousresearch/hermes-agent/issues/50718)** (2 comments)
   - **Need:** Desktop users lack unread markers, needs-input cues, and OS-level notifications for background sessions. Key UX deficiency for users running multiple concurrent sessions.

## 5. Bugs & Stability

### High Severity (P1)

- **[#60955 — [CLOSED] hermes-fallback-bug-report](https://github.com/nousresearch/hermes-agent/issues/60955)** — Closed same-day. Fallback bug reported; fix likely included in patch.
- **[#61145 — Gateway session-hygiene auto-compress destructively DELETEs transcript](https://github.com/nousresearch/hermes-agent/issues/61145) (P1, open)** — **Critical data loss bug.** Auto-compression at 400 messages permanently deletes conversation history instead of soft-archiving. No fix PR yet. Highest-priority issue today.
- **[#13891 — [CLOSED] Matrix decryption failure](https://github.com/nousresearch/hermes-agent/issues/13891) (P1, closed)** — Resolved.

### Medium-High Severity (P2)

- **[#61220 — Session expiry finalization doesn't set end_reason](https://github.com/nousresearch/hermes-agent/issues/61220)** — Stale recovery reopens expired sessions with full history, creating confusion. Fix PR needed.
- **[#61207 — /plan doesn't write a plan file anymore](https://github.com/nousresearch/hermes-agent/issues/61207)** — Regression in the planning skill. Needs reproduction and fix.
- **[#61211/#61212 — WeCom file upload fails with Chinese filenames on Windows](https://github.com/nousresearch/hermes-agent/issues/61211)** — FileNotFoundError due to percent-encoded filename exceeding Windows MAX_PATH. Duplicate reports suggest Windows users with CJK filenames are actively affected.
- **[#58646 — QQ bot adapter startup failure: unexpected keyword argument 'is_reconnect'](https://github.com/nousresearch/hermes-agent/issues/58646)** — QQ bot gateway cannot reconnect due to API incompatibility.
- **[#39534 — Desktop cuts off Chinese prompts in chat window](https://github.com/nousresearch/hermes-agent/issues/39534)** — CJK text rendering bug in Desktop app.
- **[#28260 — [CLOSED] Self-signed HTTPS endpoints fail with APIConnectionError](https://github.com/nousresearch/hermes-agent/issues/28260)** — Closed today. SSL verification issue fixed for local HTTPS proxies.
- **[#48098 — Desktop stale "Summarizing thread" status](https://github.com/nousresearch/hermes-agent/issues/48098)** — UI remains stuck showing compaction status after model resumes work.
- **[#35419 — Silent fallback activation (no user notification)](https://github.com/nousresearch/hermes-agent/issues/35419)** — Fallback provider is activated but users are not informed.
- **[#5254 — Tool calls repeating with LM-Studio/Gemma4](https://github.com/nousresearch/hermes-agent/issues/5254)** — Fragmented tool calls due to streaming issues with local models.
- **[#39047 — Compression routes Gemini model to Codex backend, rejects with HTTP 400](https://github.com/nousresearch/hermes-agent/issues/39047)** — Provider-qualified model slugs misrouted during auxiliary compression tasks.
- **[#61099 — OpenRouter logs show 'Unknown' App for Hermes requests](https://github.com/nousresearch/hermes-agent/issues/61099)** — Inconsistent identification on OpenRouter which may affect rate limiting and analytics.
- **[#61048 — Kanban worker ignores fallback_providers](https://github.com/nousresearch/hermes-agent/issues/61048)** — Kanban tasks fail when primary provider is unavailable; fallback not applied.

### Fix PRs Available Today

| Issue | Fix PR | Status |
|---|---|---|
| #61145 (Transcript deletion) | — | No fix PR yet |
| #61207 (/plan regression) | — | No fix PR yet |
| #61211 (WeCom Windows filename) | — | No fix PR yet |
| #58646 (QQ bot reconnect) | — | No fix PR yet |
| #5254 (Tool call repetition) | — | No fix PR yet |
| #48098 (Stale compaction status) | — | No fix PR yet |
| #39534 (Chinese text cutoff) | — | No fix PR yet |
| #61220 (Session expiry) | — | No fix PR yet |
| #39047 (Gemini routing) | — | No fix PR yet |
| #61099 (OpenRouter identification) | — | No fix PR yet |
| #61048 (Kanban fallback) | — | No fix PR yet |
| #59224 (CLI /resume filtering) | — | No fix PR yet |
| #54201 (Windows process tree) | [PR #54235](https://github.com/nousresearch/hermes-agent/pull/54235) | Open |
| #54461 (Matrix DM isolation) | [PR #54554](https://github.com/nousresearch/hermes-agent/pull/54554) | Open |

## 6. Feature Requests & Roadmap Signals

### Features Likely for Next Version (v0.19)

1. **[#61223 — Guarded Codex exec bridge](https://github.com/nousresearch/hermes-agent/pull/61223)** — Already has an open PR. Likely to land soon, enabling Hermes to delegate coding tasks to Codex CLI securely.
2. **[#61193 — Full terminal command visibility in Desktop](https://github.com/nousresearch/hermes-agent/issues/61193)** — Requested today; high relevance for user trust and debugging.
3. **[#53617 — Desktop: keep reasoning panel expanded](https://github.com/nousresearch/hermes-agent/issues/53617)** — Simple UX toggle for reasoning model users. High impact, low complexity.
4. **[#52807 — UI for configuring custom API providers](https://github.com/nousresearch/hermes-agent/issues/52807)** — Would eliminate manual `config.yaml` editing. Aligns with Desktop app maturity goals.
5. **[#23524 — Per-cron reasoning effort overrides](https://github.com/nousresearch/hermes-agent/issues/23524)** — Granular control over cron job costs. Likely v0.19 candidate.
6. **[#569 — Agent Client Protocol (ACP) Server Mode](https://github.com/nousresearch/hermes-agent/issues/569)** — High upvote count (9). Would unlock editor integration with Zed, JetBrains, Neovim. Strategically important.
7. **[#39691 — headroom-ai tool output compression](https://github.com/nousresearch/hermes-agent/issues/39691)** — 12 👍, highest community interest. Smart compression is clearly a priority.

### Roadmap Signals

The project is moving toward:
- **Desktop maturity**: Multiple UX issues fixed (zoom, provider picker, stale status, Chinese text)
- **Cross-platform parity**: Windows-specific fixes (process tree kill, filename encoding, zoom)
- **Gateway ecosystem expansion**: Blooio integration merged, Matrix fixes, WeCom fixes, QQ bot fixes
- **Context optimization**: headroom-ai integration proposed, trajectory compressor hardened
- **Editor/IDE integration**: ACP protocol support per #569
- **Security hardening**: Security pin refresh PR, session hygiene data loss bug

## 7. User Feedback Summary

### Pain Points

1. **Data loss risk:** Session auto-compression permanently deleting transcripts ([#61145](https://github.com/nousresearch/hermes-agent/issues/61145)) is the most critical user trust issue.
2. **Windows UX deficiencies:** Chinese text cutoff ([#39534](https://github.com/nousresearch/hermes-agent/issues/39534)), zoom reset ([#61245](https://github.com/nousresearch/hermes-agent/issues/61245)), missing minimize-to-tray ([#61246](https://github.com/nousresearch/hermes-agent/issues/61246)), and GUI program hangs ([#54235](https://github.com/nousresearch/hermes-agent/pull/54235)) suggest Windows Desktop experience is behind macOS/Linux.
3. **Session management:** CLI/Desktop session visibility gap ([#59224](https://github.com/nousresearch/hermes-agent/issues/59224)), expired sessions reopening ([#61220](https://github.com/nousresearch/hermes-agent/issues/61220)), and missing notification cues ([#50718](https://github.com/nousresearch/hermes-agent/issues/50718)).
4. **Tool execution confusion:** Missing full command display in Desktop ([#61193](https://github.com/nousresearch/hermes-agent/issues/61193)), Kanban workers misunderstanding tool access ([#61222](https://github.com/nousresearch/hermes-agent/pull/61222)).
5. **Fallback reliability:** Silent activation ([#35419](https://github.com/nousresearch/hermes-agent/issues/35419)), Kanban ignoring fallback ([#61048](https://github.com/nousresearch/hermes-agent/issues/61048)).

### Satisfaction Signals

- Active community engagement with feature suggestions (12 👍 on compression, 9 👍 on ACP support).
- Quick response to critical bugs (P1 issues closed same-day, patch release within hours).
- Users actively testing on multiple platforms (Windows, macOS, Matirx, QQ, Telegram, WeCom).

## 8. Backlog Watch

### Long-unanswered Issues Needing Maintainer Attention

| Issue | Age | Priority | Summary |
|---|---|---|---|
| [#5254](https://github.com/nousresearch/hermes-agent/issues/5254) | 3+ months | P2 | Tool calls repeating with LM-Studio — likely a streaming protocol issue. Impacts local model users. |
| [#569](https://github.com/nousresearch/hermes-agent/issues/569) | 4+ months | — | ACP Server Mode for editor integration. High upvote count, strategic feature, no official roadmap commitment. |
| [#39047](https://github.com/nousresearch/hermes-agent/issues/39047) | 1+ month | P2 | Gemini model routing to wrong backend during compression. |
| [#35419](https://github.com/nousresearch/hermes-agent/issues/35419) | 1+ month | P2 | Silent fallback activation — users not notified of provider switching. |
| [#48098](https://github.com/nousresearch/hermes-agent/issues/48098) | 22 days | P2 | Desktop stale compaction status — UI not properly reflecting agent state. |
| [#39558](https://github.com/nousresearch/hermes-agent/issues/39558) | 1+ month | P3 | Assistant text before tool calls disappears from rendered thread. |
| [#39838](https://github.com/nousresearch/hermes-agent/issues/39838) | 1+ month | P2 | notification_sources config documented but never implemented in gateway. |
| [#18241](https://github.com/nousresearch/hermes-agent/issues/18241) | 2+ months | P3 | TUI chronological interleaving of thinking/tool calls. |

### No-Maintainer-Response Issues

- **All issues from July 9** (#61193, #61246, #61220, #61211, #61212, #61207, #61191, #61145) are very recent and likely awaiting triage.

### Overall Backlog Health

The project has ~90 open items (45 issues + 47 PRs). While many recent PRs address critical bugs, several P2 bugs (especially #5254, #39047, #35419) have remained open for over a month without a fix PR. The session hygiene data loss bug (#61145) is the most time-sensitive new issue. Maintainer bandwidth appears stretched given the volume of both issue reports and incoming PRs.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

**PicoClaw Project Digest — 2026-07-09**

**1. Today's Overview**
Project activity is moderate, with 3 pull requests merged (none remaining open) and 2 open issues updated within the last 24 hours. No new releases were published today. The merged PRs indicate steady progress on gateway reliability, channel extensibility, and provider compatibility, while the two open issues highlight ongoing user-facing concerns with NanoKVM deployment and a feature gap for the QQ channel. Overall, the project appears to be in a healthy maintenance-and-feature phase.

**2. Releases**
No new releases were published today. The latest available version remains unchanged.

**3. Project Progress**
Three pull requests were merged today, all closed/merged:

- **PR #2278** — `feat(gateway): fallback to wildcard bind with CIDR allowlist when loopback bind fails`  
  Author: Sakurapainting. Improves gateway startup reliability on environments where loopback is unavailable by implementing a controlled fallback to wildcard binding with a CIDR allowlist. (https://github.com/sipeed/picoclaw/pull/2278)

- **PR #2251** — `feat(channels): add Grafana Alertmanager webhook channel`  
  Author: loafoe. Adds a new `grafana_alertmanager` input-only channel that exposes a webhook endpoint for receiving alerts from Grafana Alertmanager, supports parsing Alertmanager payloads, and allows triggering specific skills via a `skill` configuration field. (https://github.com/sipeed/picoclaw/pull/2251)

- **PR #3234** — `CHORE (anthropic_messages): embed image media in user messages so vision models can see them`  
  Author: darren101004. Fixes a bug where the `anthropic_messages` provider's `buildRequestBody` only sent text content for user messages, dropping attached image media. Images (e.g., loaded via `load_image` as data URLs) are now properly included, enabling vision model replies. (https://github.com/sipeed/picoclaw/pull/3234)

**4. Community Hot Topics**
No issues or PRs currently show high comment or reaction counts (all have 0–2 comments and 0 👍). However:

- **Issue #3195** (2 comments): [BUG] OpenAI GPT does not work on NanoKVM with default config — this is the most-discussed item. The user describes failing to configure `gpt-5.4` after setting up PicoClaw on NanoKVM 2.4.0, pointing to a potential configuration or compatibility issue. (https://github.com/sipeed/picoclaw/issues/3195)

- **Issue #3201** (1 comment): [Feature] Support streaming output for QQ channel — a feature request that notes only Telegram and Pico WebSocket currently support streaming; the QQ channel does not. (https://github.com/sipeed/picoclaw/issues/3201)

**5. Bugs & Stability**
One bug was reported today (updated in the last 24h), though it was created earlier:

- **Issue #3195** — **Severity: High** (blocking functionality). OpenAI GPT models fail to work on NanoKVM with the default config. The user followed official documentation but cannot interact with PicoClaw. As of now, no fix PR exists. (https://github.com/sipeed/picoclaw/issues/3195)

**6. Feature Requests & Roadmap Signals**
- **QQ streaming output** (Issue #3201): Users want real-time incremental output for the QQ channel, mirroring capabilities already present in Telegram and Pico WebSocket. Likely candidate for the next minor release given the availability of a reference implementation. (https://github.com/sipeed/picoclaw/issues/3201)

- **Grafana Alertmanager channel** (PR #2251, *today merged*): Adds a new input channel for receiving alerts from Grafana Alertmanager with skill-triggering support. This signals growing enterprise/integration interest and may encourage further monitoring-related channel additions.

**7. User Feedback Summary**
- **Pain point**: A user deploying PicoClaw on NanoKVM (a new feature in NanoKVM 2.4.0) cannot use OpenAI GPT models despite following official configuration docs. This suggests either a missing configuration step, a compatibility regression, or a documentation gap.
- **Dissatisfaction**: One user explicitly requests streaming support for the QQ channel, implying that non-streaming responses are a meaningful limitation for that platform’s users.
- **Satisfaction**: No explicit positive feedback was captured in today’s data, but the new Grafana Alertmanager channel (merged today) likely addresses a previously unmet need for operations teams.

**8. Backlog Watch**
- **Issue #3195** (Open since 2026-06-30, updated today): No maintainer response or fix PR yet. Given it blocks core functionality on a supported hardware platform (NanoKVM), this warrants priority attention. (https://github.com/sipeed/picoclaw/issues/3195)

- **Issue #3201** (Open since 2026-07-01, updated today): Tagged `[stale]`, yet it remains unanswered by maintainers. The request for QQ streaming is feature-relevant and has a clear precedent, so a response or triage label update would improve community perception. (https://github.com/sipeed/picoclaw/issues/3201)

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

# NanoClaw Project Digest — 2026-07-09

## 1. Today's Overview

NanoClaw is experiencing **very high development momentum**, with **28 pull requests** updated in the last 24 hours — a significant surge indicating a major feature train is in active motion. The **scheduled-tasks feature series** (parts 1-5/6) is the dominant theme, with recent merges of `ncl CLI` parsing improvements and a large control-plane PR now open. **Two new issues** were filed today: one critical silent-reply bug in the opencode provider, and one user-requested Discord thread-renaming feature. Overall project health is **strong**, with core team deeply engaged across CLI, agent-runner, approvals, and skill infrastructure fronts.

## 2. Releases

**No new releases** today. The latest available version remains v2.1.17 (CHANGELOG expansion PR #2798 is still open).

## 3. Project Progress

**4 PRs merged/closed today**, reflecting significant forward motion:

- **#2980 [MERGED] — `ncl` CLI: verb-level args, deep help, server-rendered human view** (by omri-maya) — Part 1/6 of the scheduled-tasks train. Every `ncl` verb now has strict arg validation, fix-carrying error messages, and richer help output. Sets the foundation for the tasks resource that follows.
- **#2978 [MERGED] — CI: auto-label PRs from core team members** (by gabi-simons) — Extends the `label-pr.yml` workflow to automatically apply the `core-team` label, improving triage visibility.
- **#1702 [MERGED] — fix: break for-await loop on result to prevent IPC message loss** (by jbaruch) — A long-standing fix (first opened April 8) has finally been merged, addressing message loss in IPC communication loops.

**What advanced:**
- The **scheduled-tasks control plane** (#2981, 233 files changed) now has a full `ncl tasks` resource with CRUDL, pause/resume/cancel, isolated sessions, run history, and pre-task script gates.
- **Per-group harness capability toggles** (#2983) now disable agent-teams and workflow by default, reducing duplicate scheduling paths.
- **Agent-runner tool allowlist** (#2982) was reconciled with the pinned claude-code CLI (2.1.197), with a drift guard added to prevent future mismatches.
- **Agent template setup wizard** (#2909) is nearing completion, offering template-based first-agent creation in the `pnpm setup` flow.

## 4. Community Hot Topics

The **most active PRs** (by comment count, all with active discussion):

- **#2742 — PR Factory recipe** (opened June 11, 28 comments) — A published recipe that turns every PR into a reviewed, test-planned Slack thread via a dedicated worker agent. Deep community interest in autonomous PR review workflows.
- **#2921 — fix(compose): gate skill fragments on group skill selection** (opened July 3, open) — A bug fix that prevents `CLAUDE.md` composition from inlining all skills into all groups. Important for multi-group deployments.
- **#2981 — Scheduled tasks control plane** (opened yesterday, 233 files) — The largest PR in the batch, generating significant core-team review traffic due to its scope (command resource, isolated sessions, script gates).

**Underlying needs:**
- **Autonomous CI/review workflows** (#2742): Users want agents to handle PR triage, review, and testing autonomously, reducing human toil.
- **Structured skill management** (#2921, #2873): Operators need granular control over which skills apply to which agent groups, without accidental cross-contamination.
- **Scheduled task reliability** (#2981, #2980): Growing demand for cron-like agent execution that respects isolation and has proper observability.

## 5. Bugs & Stability

**High Severity:**

- **#2985 [OPEN] — opencode provider: silent no-reply when final text snapshot misses `session.idle`** — The messaging bot silently drops replies on long agentic turns using the opencode provider. No error is raised, making it appear the bot ignored the message. **No fix PR yet.** This is critical for production deployments using opencode.

**Medium Severity:**

- **#2921 [OPEN] — `composeGroupClaudeMd` inlines every skill into every group** — Breaks group-specific skill isolation. **Fix PR exists** (#2921), awaiting merge.
- **#2982 [OPEN] — Agent-runner `TOOL_ALLOWLIST` references five tools that don't exist on pinned CLI** — Causes tool-call failures. **Fix PR exists** (#2982), reconciling with claude-code 2.1.197.

**Low Severity:**

- **#2958 [OPEN] — add-teams skill rebuild** — No bug, but removes a ~7-step manual Azure portal walk in favor of CLI-first flow.
- **#2770 [OPEN] — Codex image generation events dropped** — `ProviderEvent` union missing `file` type; breaks delivery to chat. **Fix PR exists** (#2770).

## 6. Feature Requests & Roadmap Signals

**Strong roadmap signal — Scheduled Tasks**
The 6-part scheduled-tasks train (parts 1-5 now visible) represents the **largest infrastructure push in Q3**. Features shipping:
- Full `ncl tasks` CLI resource with create/update/run/pause/resume/cancel/append-log
- Per-series isolated sessions with run history
- Pre-task script gates for validation
- Server-rendered human view for CLI output

**Likely next version (v2.2.0) candidates:**
- **Agent templates** (#2909) — Setup wizard with template-based first-agent creation
- **Thread auto-rename** (#2984) — Discord threads renamed by topic instead of date stamps
- **Default agent provider** (#2906) — Instance-wide `DEFAULT_AGENT_PROVIDER` env var
- **Reject-with-reason for OneCLI credential cards** (#2941) — Extends approval cards to credential flows

**User-requested features:**
- **#2984 — Auto-rename Discord threads by topic** — User @eagansilverpathmarketing proposes a `rename_thread` tool to make busy servers scannable.
- **#2914 — WhatsApp Cloud webhook documentation** — Follow-up to the WhatsApp Cloud bridge fix (#2913).

## 7. User Feedback Summary

**Pain Points:**
- **Silent reply drops** (#2985): Production users hitting the opencode provider experience invisible failures — the agent completes work but nothing is delivered, with no error signal.
- **Thread naming** (#2984): Discord server operators find date-stamped threads impossible to scan on busy servers.
- **Tool allowlist drift** (#2982): CLI updates silently invalidate `TOOL_ALLOWLIST`, causing tool calls to fail without clear cause.

**Satisfaction Signals:**
- **CLI improvements** (#2980): The new verb-level arg validation and richer help output were proactively requested by users.
- **Scheduled tasks** (#2981): High core-team investment signals strong user demand for cron-like agent execution.
- **WhatsApp Cloud bridge** (#2913, #2914): Active development on multi-instance WhatsApp support for enterprise deployments.

**Use Cases:**
- **Enterprise scheduling** (scheduled tasks train): Automated daily reports, periodic data collection, maintenance windows.
- **Autonomous PR review** (#2742): Teams wanting agents to handle code review and testing without human intervention.
- **Multi-group deployments** (#2921, #2906): Organizations running multiple agent groups with different skill sets and providers.

## 8. Backlog Watch

**Long-unanswered PRs needing maintainer attention:**

| PR | Issue | Age | Status |
|----|-------|-----|--------|
| **#2770** | fix(codex): deliver harness file events + add `file` to ProviderEvent | 25 days | Open, core-team tagged; builds break without it |
| **#2906** | feat: instance-wide default agent provider for new groups | 8 days | Open, core-team tagged; needs review for v2.2 |
| **#2873** | fix(skills): split pre-flight from credentials so `/update-skills` can refresh code | 12 days | Open, core-team tagged; regression fix for skill updates |
| **#2798** | chore(release): expand CHANGELOG for v2.1.17 | 22 days | Open; documentation-only but blocking accurate release notes |
| **#2742** | feat(recipes): the PR Factory recipe | 28 days | Open, community interest; not yet merged despite age |

**Notable:** PR #1702 (IPC message loss fix) was finally merged today after **92 days** open. This suggests the backlog is being actively addressed, but some feature PRs (especially #2742 and #2770) risk similar long wait times.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

Here is the structured digest for the IronClaw project, generated from the provided GitHub data for 2026-07-09.

---

### IronClaw Project Digest — 2026-07-09

#### 1. Today’s Overview
Project activity is **very high**, driven by a substantial refactoring push across the codebase. In the last 24 hours, 50 Pull Requests were updated (39 open, 11 merged/closed) and 21 Issues were active (15 open). The major theme is the **NEA-25 unified extension surfaces refactor**, with a 7-PR stack (plus audit fixes) being worked on by core contributors. This architectural work is aimed at simplifying the extension model by retiring legacy channel and manifest concepts. Concurrently, a large batch of P2 and P3 bug reports from the on-going `bug_bash` were filed, highlighting several critical stability and UX issues in the new Reborn WebUI and automation runner.

#### 2. Releases
**None.** No new releases were recorded in the last 24 hours.

#### 3. Project Progress
**11 PRs were merged or closed today.** While the exact list of merged PRs is not detailed in the "latest PRs" section, the closing of Issues #5768, #5770, and #5787 indicates that several important fixes were successfully integrated:
- **i18n Coverage:** The Reborn Projects page now has complete internationalization coverage (`#5768`).
- **UI Consistency:** Tool permission selects in Reborn Settings have been improved with a custom dropdown (`#5770`).
- **Stability:** A flaky test (`slack_pairing_redeem_rejects_expired_code`), which suffered from a race condition, has been fixed (`#5787`).

Key open PRs advancing significant features include:
- **NEA-25 Stack:** PRs #5833, #5839, #5842, #5845, #5847, #5848, #5849, and #5850 represent a massive refactor to unify how extensions (channels, tools) are declared and surfaced. This includes retiring separate `slack_bot` and `slack_personal` extensions into a single `slack` extension.
- **Performance:** PR #5857 aims to reduce pre-model latency by caching filesystem descriptors for system skill bundles.
- **UX:** PR #5763 adds connection-loss error handling for SSE disconnects during run failures.
- **Administration:** PR #5525 introduces the ability for non-admin users to privately install tools from the registry.

#### 4. Community Hot Topics
The most active discussions are focused on the **NEA-25 refactor** and core quality-of-life bugs.

- **[PR #5857](http://github.com/nearai/ironclaw/pull/5857): perf(reborn): reduce API capacity pre-model latency** — This is a significant performance optimization stacked on a harness-only PR. While it has no comments, its `XL` size and focus on latency reduction make it a high-interest item for the team.
- **[Issue #5702](http://github.com/nearai/ironclaw/issue/5702): [bug_bash_P2] GitHub integration failing with HTTP 403** — With 4 comments, this is the most discussed open issue. The core problem appears to be an authentication or permission issue with the GitHub integration that prevents the agent from searching or creating issues, completely blocking a major capability.
- **[Issue #5836](http://github.com/nearai/ironclaw/issue/5836): Routine fails on every scheduled run with "No thread attached"** — This is a critical systemic issue (P2) for the automations feature, and the detailed failure description suggests it is being actively investigated.

#### 5. Bugs & Stability
The "bug bash" filed several significant bugs today, indicating areas of instability in the `reborn` stack.

**Critical / High Severity (P2):**
- **GitHub Integration Borked:** Issue [#5702](http://github.com/nearai/ironclaw/issue/5702) blocks all GitHub issue search/create capabilities.
- **Routine Runner Broken:** Issue [#5836](http://github.com/nearai/ironclaw/issue/5836) shows scheduled routines fail consistently with "No thread attached".
- **Context Compaction Crash:** Issue [#5838](http://github.com/nearai/ironclaw/issue/5838) causes runs to fail at the end due to a context compaction error, even after successful tool execution.
- **Slack Disconnect Blocked:** Issue [#5834](http://github.com/nearai/ironclaw/issue/5834) shows the agent incorrectly refuses to disconnect Slack.
- **Routine Action Buttons Do Nothing:** Issue [#5837](http://github.com/nearai/ironclaw/issue/5837) reports the "Open run" and "Logs" buttons on failed runs are unclickable, preventing debugging.

**Medium / Low Severity (P3):**
- **UI Polish:** Issues [#5835](http://github.com/nearai/ironclaw/issue/5835) (Jump to latest button positioning) and [#5705](http://github.com/nearai/ironclaw/issue/5705) (Terminal icon cannot be disabled) are reported as UI/UX annoyances.
- **Navigation:** Issue [#5557](http://github.com/nearai/ironclaw/issue/5557) details a persistent bug where logs deep-links require a double-click to load correctly.

**Fixes in Progress:** While no fix PRs are directly linked to the above P2 bugs, the closing of flaky test issue [#5787](http://github.com/nearai/ironclaw/issue/5787) shows the team is actively addressing CI instability.

#### 6. Feature Requests & Roadmap Signals
- **WebChat File Limit Increase:** Issue [#5820](http://github.com/nearai/ironclaw/issue/5820) explicitly requests raising the 10-file attachment limit in WebChat and surfacing overflow errors instead of silently dropping files. This is a strong signal for a near-term UX enhancement.
- **Admin Panel Improvements:** Issue [#5856](http://github.com/nearai/ironclaw/issue/5856) identifies a gap in the admin panel: there's no way to re-issue an API token for an existing user, and an orphaned "Create Token" button persists. This is a clear feature gap in the new admin UI.
- **Automation Renaming:** A closed issue [#5419](http://github.com/nearai/ironclaw/issue/5419) requesting the ability to rename automations was closed, likely indicating this feature has been implemented or is being tracked elsewhere.

Given the high volume of UX and stability issues from the bug bash, the next release will likely prioritize fixes for the P2 bugs in the routine runner and GitHub integration over brand-new features. The NEA-25 stack is a major architectural investment that may take several more cycles to fully land.

#### 7. User Feedback Summary
The bug bash data provides direct insights into real user pain points with the "Reborn" stack. The primary theme is **unreliability of core workflows**.
- **Automation Frustration:** Users cannot rely on scheduled routines to work, as they fail consistently with "No thread attached" (`#5836`).
- **Diagnostic Black Hole:** When workflows do fail, users cannot inspect the cause because the "Logs" and "Open run" buttons are not clickable (`#5837`).
- **Broken Integrations:** The GitHub integration is completely non-functional (`#5702`), and users feel locked into a Slack connection they cannot disconnect (`#5834`).
- **Workflow Interruption:** Complex runs that require multiple tool calls are failing with perplexing "context compaction" errors, discarding successful work (`#5838`).
- **UI Annoyances:** Users are irritated by persistent UI elements they can't remove (Terminal icon, `#5705`) and broken navigation (Double-clicking logs, `#5557`).

Overall, while the new UI and architecture are being pushed forward, user satisfaction is likely low for those attempting to use advanced features like automations and integrations.

#### 8. Backlog Watch
- **Issue #5557: Logs deep link requires opening twice** — This bug has been open since July 2nd (1 week) with no fix PR attached. It is a persistent navigation issue affecting the usability of the logs feature.
- **Issue #5702: GitHub integration HTTP 403** — Open since July 6th (3 days), this is a critical P2 bug blocking a core integration. It has received discussion but no linked fix PR.
- **Issue #5705: Terminal icon cannot be disabled** — Open since July 6th (3 days), this minor UX issue has no action. While low severity, its existence indicates a gap in UI customization.

The lack of linked fix PRs for the critical P2 bugs opened this week (`#5836`, `#5838`, `#5834`) suggests the team is currently absorbed in the NEA-25 refactor and may need to reprioritize to address these stability issues.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

Here is the **LobsterAI Project Digest** for **July 9, 2026**.

---

## LobsterAI Project Digest — 2026-07-09

### 1. Today's Overview
The LobsterAI project saw a significant spike in activity today, with 13 Pull Requests updated in the last 24 hours and 3 Issues showing movement. While no new releases were tagged, the development team closed 10 PRs—many of which addressed critical regressions reported by the community in recent weeks. The project is in a high-fix cycle, with the core maintainers heavily focused on stabilizing multi-agent functionality and IM channel scoping. Community sentiment remains engaged but strained, particularly around regression bugs introduced in version 4.1.

### 2. Releases
**None.**  
No new versions were released today. The last major version appears to be 4.1, which is currently the subject of several bug reports.

### 3. Project Progress
The following 10 PRs were closed/merged today, reflecting a heavy push on stability and feature refinement:

- **#2298** – `fix(im): scope channel session mappings by agent` — Prevents IM session collapse across different agents by scoping session keys to the agent ID.
- **#2297** – `fix(openclaw): default memory search to local FTS` — Ensures keyword-based memory search works even when embedding/vector search is disabled; includes a migration for existing users.
- **#2296** – `feat(cowork): add minimizable permission prompts` — Allows users to minimize permission request windows rather than blocking the UI; includes session-scoped pending badges.
- **#2295** – `fix(agent): scope USER.md bootstrap file per agent workspace` — Direct fix for Issue #2293 (see Bugs), preventing USER.md from being overwritten across agents.
- **#2285** – `feat(agents): support delegated subagent collaboration` — Large feature branch enabling users to delegate tasks to other agents as child sessions, synced via an allowlist.
- **#1401, #1402, #1403, #1404, #1406** – A batch of older "stale" PRs were closed today, fixing security (UUID entropy), multi-file attachment picker, i18n missing translation key, scheduled task UI/UX, and IM filter fallback.

**Key Takeaway:** The "stale" PR closure blitz (5 PRs from April) suggests the team is clearing their technical debt queue while also addressing immediate regressions.

---

### 4. Community Hot Topics

| Issue/PR | Type | Comments | Summary |
|----------|------|----------|---------|
| **#2293** | [OPEN Bug](https://github.com/netease-youdao/LobsterAI/issues/2293) | 1 | Multiple agents' `USER.md` files get overwritten by main agent on restart. User reports inability to differentiate agent behaviors. |
| **#1400** | [CLOSED](https://github.com/netease-youdao/LobsterAI/issues/1400) | 7 | **Most commented issue.** User reported unbounded restart loop after upgrade to 4.1, plus LLM model invocation failure. Contact info left for team follow-up. |
| **#1348** | [OPEN](https://github.com/netease-youdao/LobsterAI/issues/1348) | 1 | Stale issue: scheduled task name uniqueness not validated — a UX quality-of-life request. |
| **#1346 / #1347** | [OPEN PRs](https://github.com/netease-youdao/LobsterAI/pull/1346) | 0 | Two feature PRs (skills management, cron scheduling) from April remain unmerged. |

**Underlying Need:** The most active issues reveal a clear pattern: **users with multiple agents are experiencing data silo violations.** The community wants strict isolation of agent configurations (USER.md, IM sessions, memory) so that deploying multiple agents doesn’t lead to accidental overwrites.

---

### 5. Bugs & Stability

| Severity | Issue | Status | Notes |
|----------|-------|--------|-------|
| **Critical** | [#1400](https://github.com/netease-youdao/LobsterAI/issues/1400) — Gateway restart loop (v4.1) | Closed (stale) | Involves unbounded restart cycle + LLM API mismatch. No linked fix PR found; appears to have been closed without explicit resolution. This is a risk signal. |
| **High** | [#2293](https://github.com/netease-youdao/LobsterAI/issues/2293) — USER.md overwrite across agents | Open | **Fix PR merged today (#2295)**. Likely to be resolved in next build. |
| **Medium** | [#1348](https://github.com/netease-youdao/LobsterAI/issues/1348) — Duplicate scheduled task names | Open (stale) | Low impact, no fix in progress. |

**Bugs Ranked by Severity:**  
1. **Gateway restart loop (Critical)** – No verified fix in current PR queue; risk of lingering instability for v4.1 users.  
2. **Multi-agent config corruption (High)** – Fix already merged (#2295).  
3. **Task name validation (Low)** – Stale, non-urgent.

---

### 6. Feature Requests & Roadmap Signals

- **Delegated Subagent Collaboration (#2285)** – Merged today. This is a major architectural step: agents can now be delegated to perform sub-tasks within a parent conversation. Expect this in the next minor release.
- **Cron Custom Scheduling (#1347)** – Still open since April. If merged, would replace the current fixed-interval scheduling with user-defined cron expressions. This is the most likely next UX feature to land.
- **Skills Management (#1346)** – On hold since April; no recent commits. Lower priority.

**Prediction:** The next version (likely 4.2) will include delegated subagent collaboration and the USER.md isolation fix. Cron scheduling may follow in a subsequent patch.

---

### 7. User Feedback Summary

- **Pain Point #1 – Upgrade Breakage (Critical):** User `danielmonlite` described a "complete paralysis" after upgrading to v4.1, with infinite restarts and LLM conflicts. Frustration is high.
- **Pain Point #2 – Multi-Agent Isolation (High):** User `yepcn` reports that "different agents cannot have different needs" because configuration files are shared. The PR #2295 fix addresses this, but user satisfaction will depend on how quickly the fix ships.
- **Pain Point #3 – IM Session Collision:** Subtle issue where IM conversations across agents merged into one session. Fix merged today (#2298).
- **Positive Signal:** The community is actively filing structured bug reports and following up with reproduction steps (e.g., testing offline modifications to USER.md). This indicates a technically engaged user base.

---

### 8. Backlog Watch

| Issue/PR | Age | Risk | Needed Action |
|----------|-----|------|---------------|
| **[#1400](https://github.com/netease-youdao/LobsterAI/issues/1400)** — Gateway restart loop | ~3 months (Closed) | **High** | Though closed, there is no evidence of a fix. If this affects other v4.1 users, the issue may re-surface. Maintainers should audit the root cause. |
| **[#1346](https://github.com/netease-youdao/LobsterAI/pull/1346)** — Skills management PR | ~3 months (Open) | Medium | No maintainer review since April. If not being pursued, it should be formally declined or assigned. |
| **[#1347](https://github.com/netease-youdao/LobsterAI/pull/1347)** — Cron scheduling PR | ~3 months (Open) | Medium | Large feature with high community demand (tasks & scheduling). Needs a maintainer decision. |
| **[#1348](https://github.com/netease-youdao/LobsterAI/issues/1348)** — Duplicate task names | ~3 months (Open) | Low | Trivial fix; could be good for a first-time contributor or quick patch. |

**Maintainer Attention Needed:** The **v4.1 gateway restart loop (#1400)** remains the highest risk item in the backlog, even though the issue is closed. If this regression was not properly resolved, the project risks alienating users who rely on stable gateway operation.

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyagi">TinyAGI/tinyagi</a></summary>

Here is the **TinyClaw Project Digest** for **2026-07-09**.

---

## 1. Today's Overview
The TinyClaw project is in a **maintenance and hardening phase** with **no active issues** and **no new releases**. While there is no daily development motion today (0 open issues, 0 new releases), a significant security-focused pull request (#44) was merged yesterday, marking the completion of a full code-review and audit cycle. The project appears stable and clean, with no new bugs or regressions reported in the last 24 hours, but also with no visible new feature development.

## 2. Releases
**None.** No new versions were published today. The last release remains unlisted in this snapshot.

## 3. Project Progress
- **Merged/Closed PRs (last 24h): 1**
  - **PR #44 (Closed/Merged):** [Harden channel auth, file safety, and update integrity](https://github.com/TinyAGI/tinyagi/pull/44)
    - **Author:** coreyone
    - **Summary:** This PR resolved a full security/code-review audit. Key changes included:
      - Enforcing sender allowlists (default-on) across Telegram, Discord, WhatsApp, and queue processing.
      - Restricting outbound file handling to prevent path traversal and unauthorized access.
      - Strengthening bundle update and install integrity checks.
    - **Assessment:** This is a high-impact infrastructure improvement that closes a critical vulnerability window but introduces no new features.

## 4. Community Hot Topics
**No active discussions today.** There are zero open issues, and the only recent PR (#44) had no comments or reactions logged in the 24-hour window. The project currently lacks community engagement signals (no threads with high comment counts or emoji reactions). The underlying need appears to be around **trust and safety** rather than feature expansion.

## 5. Bugs & Stability
**None reported.** No bugs, crashes, or regressions were filed in the last 24 hours. The project maintains a clean state, likely due to the recent proactive hardening in PR #44.

## 6. Feature Requests & Roadmap Signals
**No explicit feature requests** were filed today. However, based on the PR activity, the following predictions can be made:
- **Next likely focus:** The completion of the security audit (PR #44) suggests the next version may focus on **multi-platform permission management** (allowlists), **safe file I/O**, and **input sanitization**.
- **Possible user-requested feature gap:** No feature requests exist, but users often follow security hardening with requests for **granular per-user access controls** and **audit logging dashboards**–these may appear in the next version.

## 7. User Feedback Summary
**No direct user feedback available** in the 24-hour window (no issues, no comments). Based on the PR context, the core user pain point being addressed was **unauthorized agent invocation and insecure file handling**. The satisfaction signal is neutral-positive: the merging of a large security PR indicates maintainers are responsive to safety concerns.

## 8. Backlog Watch
**No long-unanswered items.** There are zero open issues and zero open PRs. The backlog is fully clean. This is a healthy sign, but also indicates the project may be in a **low-activity maintenance holding pattern**. Maintainers should consider if there are unrecorded feature proposals or pending roadmap items to surface.

---

**Overall Project Health Rating:** ✅ **Stable / Low Activity** – Clean repo, recent major security upgrade, but no new feature work or community feedback visible.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

# Moltis Project Digest — 2026-07-09

## Today's Overview
Moltis shows **low activity** over the past 24 hours, with no new or updated issues and zero releases. A single open pull request (#1145) was updated, representing the only movement in the project. The absence of new bugs, merged PRs, or community discussion suggests either a maintenance lull or team focus on longer-running work. Overall project health appears stable but quiet, with no breaking changes or regressions to report.

## Releases
**None** — No new versions or tags were published in the last 24 hours.

## Project Progress
No pull requests were merged or closed today. The only PR updated was **#1145**, which remains open.

## Community Hot Topics
The only active item is **PR #1145** ([link](https://github.com/moltis-org/moltis/pull/1145)):
- **Title:** fix(caldav): avoid panic on non-ASCII datetime in normalise_datetime
- **Author:** Osamaali313
- **Reactions:** 0 👍 — Low community engagement, but the fix addresses a **runtime crash bug** that could affect any user syncing with non-ASCII CalDAV servers.
- **Underlying need:** Users relying on international calendars or servers with non-ASCII date strings are currently at risk of panics. The PR closes a safety gap in the CalDAV parsing layer.

## Bugs & Stability
**One high-severity bug** was identified but not yet merged:
- **Crash on non-ASCII datetime in `normalise_datetime`** — The `caldav` crate can panic when a remote CalDAV server returns dates with non-ASCII characters. The DATE branch performs unchecked byte-index slicing after an ASCII check, but the DATETIME branch lacks equivalent validation. **Severity: High** (causes process termination). A fix exists in **PR #1145** but is still open. While no new issues were filed today, this bug remains live and unreleased.

## Feature Requests & Roadmap Signals
No new feature requests were submitted today. The only signal is the stability-focused fix in #1145, which does not introduce new capabilities. No roadmap indicators are visible from the last 24 hours.

## User Feedback Summary
No user comments, reactions, or pain points were expressed today. The absence of feedback may indicate either general satisfaction or low usage patterns.

## Backlog Watch
No long-unanswered issues or PRs currently demand maintainer attention. PR #1145 is the only open item and is only one day old, so it is not yet considered backlogged. Maintainers should monitor it to ensure timely review and merge to prevent the panic from affecting production users.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

# CoPaw Project Digest — 2026-07-09

## 1. Today's Overview

Project CoPaw shows **very high development activity** with 47 PRs and 39 Issues updated in the last 24 hours, driven largely by the ongoing **v2.0.0-beta.4 release cycle** and a substantial community bug-reporting wave. A new beta release (v2.0.0-beta.4) shipped with critical fixes to the `scroll` context compression system. The community is actively stress-testing both v1.x and v2.0 beta builds, with significant attention on **context loss bugs**, **approval workflow regressions**, and **channel integration issues**. The project maintainers are responsive: 24 Issues were closed and 15 PRs were merged/closed today, suggesting strong triage velocity. Three first-time contributors submitted meaningful PRs, indicating healthy community onboarding.

## 2. Releases

**New: [v2.0.0-beta.4](https://github.com/agentscope-ai/CoPaw/releases/tag/v2.0.0-beta.4)**

**What's Changed:**
- Chore: version bump to 2.0.0b4 (by @rayrayraykk)
- Fix(scroll): protect the active turn during compression, add graduated pressure relief, and make recall failures unmistakable (by @niceIrene)

**Breaking Changes:** None documented

**Migration Notes:** None documented — this is a beta iteration primarily targeting the `scroll` context strategy issues reported on v2.0.0-beta.3

## 3. Project Progress

Today's merged/closed PRs (15 total) show focused stabilization work:

- **[PR #5864](https://github.com/agentscope-ai/CoPaw/pull/5864) (merged)** — Fix(mcp): apply runtime approval level to driver policy. Resolves a gap where MCP driver approval levels were not synced with the Console UI's effective tool approval setting.
- **[PR #5792](https://github.com/agentscope-ai/CoPaw/pull/5792) (merged)** — Fix(agents): stop dropping self-paired tool messages during sanitation. First-time contributor @Osamaali313 fixed a bug where valid AgentScope 2.0 self-paired tool messages were incorrectly stripped.
- **[PR #5844](https://github.com/agentscope-ai/CoPaw/pull/5844) (merged)** — CI: add real-behavior-proof gate + wire pr-spam-gate into tests.yml. Portfolio of test infrastructure hardening.

**Under Review PRs (not merged today but progressing):**
- [#5869](https://github.com/agentscope-ai/CoPaw/pull/5869) — Expose system commands in slash autocomplete across all UIs
- [#5801](https://github.com/agentscope-ai/CoPaw/pull/5801) — Add Zalo Bot channel (Vietnam's 100M+ user messenger)
- [#5187](https://github.com/agentscope-ai/CoPaw/pull/5187) — Windows desktop GUI automation via UIA + Tauri control mode (long-running, still active)

## 4. Community Hot Topics

| Issue/PR | Comments | Summary |
|----------|----------|---------|
| [#5757](https://github.com/agentscope-ai/CoPaw/issues/5757) | 12 | **Feishu channel not replying** after first message. Affects both Docker and AgentScope Platform instances. [OPEN] |
| [#5846](https://github.com/agentscope-ai/CoPaw/issues/5846) | 10 | **Approval popup still appears** in "Closed Mode" (auto-execute all tools) on v2.0.0b3. [CLOSED] |
| [#5171](https://github.com/agentscope-ai/CoPaw/issues/5171) | 9 | **Context compression completely erases context** when persona files exceed token thresholds, causing task interruption. [CLOSED] |
| [#5379](https://github.com/agentscope-ai/CoPaw/issues/5379) | 8 | **Fresh install yields Internal Server Error** — `get_remote_addr(transport)` failure. [OPEN] |
| [#5162](https://github.com/agentscope-ai/CoPaw/issues/5162) | 7 | **Conversation thinking logic enters infinite loop.** [CLOSED] |

**Underlying community needs:** Users are heavily invested in **reliable long-running autonomous operation** (cron, heartbeat, background tasks). The cluster of issues around approval popup bypass, context loss, and conversation stalling reveals that **production users need agents that can run unattended for hours**. The Feishu/IM channel silence issue (#5757) and the `browser_use` Docker failure (#5872) indicate the community is deploying CoPaw in real workplace integrations.

## 5. Bugs & Stability

**Critical (blocking user workflows):**

1. **[#5860](https://github.com/agentscope-ai/CoPaw/issues/5860)** — *v2.0.0-beta.3: Frequent conversation progress loss and infinite loops* (OPEN, 3 comments). Agent loses track of current query mid-task and reverts to answering previous questions. No explicit compression trigger shown. **Mitigation:** v2.0.0-beta.4 was released today specifically targeting scroll compression issues, but this was opened *after* the release, suggesting the fix may be incomplete for this edge case.

2. **[#5379](https://github.com/agentscope-ai/CoPaw/issues/5379)** — *Fresh install: `get_remote_addr(transport)` causes Internal Server Error* (OPEN, 8 comments). Blocks new users from accessing the web UI entirely. Community has been reporting this for 17 days with no fix PR linked.

3. **[#5846](https://github.com/agentscope-ai/CoPaw/issues/5846)** — *v2.0.0b3: "Closed Mode" still shows approval popup* (CLOSED). Very high severity for automation workflows. Likely fixed in v2.0.0-beta.4 or related MCP approval changes.

**High (degraded experience):**

4. **[#5868](https://github.com/agentscope-ai/CoPaw/issues/5868)** — *Matrix Channel: Token login fails after upgrade* (OPEN, 1 comment). Regressive — user reports v1.1.5.post1 worked, latest version broke. No fix PR.

5. **[#5863](https://github.com/agentscope-ai/CoPaw/issues/5863)** — *Coding Session: Image files display as binary code* (OPEN, 2 comments). Expected image rendering not implemented.

6. **[#5872](https://github.com/agentscope-ai/CoPaw/issues/5872)** — *Docker: `browser_use` fails due to dbus connection error* (OPEN, 1 comment). Chromium exits immediately in containerized deployments.

**Fix PRs in flight for known bugs:**
- [#5871](https://github.com/agentscope-ai/CoPaw/pull/5871) — Fixes scroll compression seam marking to prevent context anchoring on wrong turns.
- [#5870](https://github.com/agentscope-ai/CoPaw/pull/5870) — Fixes reasoning reflux loops by flipping `preserve_thinking` default to `false`.
- [#5866](https://github.com/agentscope-ai/CoPaw/pull/5866) — Fixes `rm -rf ${HOME}` bypass in security module.

## 6. Feature Requests & Roadmap Signals

**Most requested features from active issues:**

| Request | Issue | Momentum |
|---------|-------|----------|
| Agent team/swarm collaboration | [#5139](https://github.com/agentscope-ai/CoPaw/issues/5139) | CLOSED — 4 comments, may be in design phase |
| System notification sound on tool approval | [#5852](https://github.com/agentscope-ai/CoPaw/issues/5852) | OPEN — 2 comments, simple UX lift |
| Task completion notifications + multi-command queue | [#3302](https://github.com/agentscope-ai/CoPaw/issues/3302) | CLOSED — strong user desire for async workflows |
| Minimize to system tray (Desktop) | [#5312](https://github.com/agentscope-ai/CoPaw/issues/5312) | CLOSED — 3 comments, simple UX improvement |

**Likely candidates for v2.0.0 stable:**
- **Slash command autocomplete** ([PR #5869](https://github.com/agentscope-ai/CoPaw/pull/5869)) — under review, likely lands before RC.
- **Windows desktop GUI automation** ([PR #5187](https://github.com/agentscope-ai/CoPaw/pull/5187)) — still open after 25 days, significant feature for enterprise Windows users.
- **Memory search reranker** ([PR #5692](https://github.com/agentscope-ai/CoPaw/pull/5692)) — under review, adds post-retrieval reranking on top of reme0.4.

**Zalo Bot channel** ([PR #5801](https://github.com/agentscope-ai/CoPaw/pull/5801)) — a strategic expansion into Southeast Asian messaging market (100M+ users). Likely to land soon given first-time contributor energy and strong localization value.

## 7. User Feedback Summary

**Positive signals:**
- Community is actively **upgrading to v2.0 beta** and stress-testing it, indicating high trust in the project direction.
- First-time contributors are submitting substantial PRs (Zalo channel, security fixes, chat UX improvements).
- Users are deploying CoPaw in **production-like environments**: Docker on cloud servers, IM channels (Feishu, QQ, Matrix), cron/heartbeat autonomous workflows.

**Pain points (recurring themes):**

1. **Context management reliability** — Multiple issues (#5860, #5171, #5746, #5416) describe agents forgetting current task, reverting to old context, or entering infinite loops. This is the #1 stability concern.

2. **Installation friction** — Issue #5379 (Internal Server Error on fresh install) has been open 17 days. Issue #5166 (Python 3.13 `imghdr` module missing) also points to environment compatibility gaps.

3. **Autonomous mode leaks** — Issue #5846 (approval popup appearing in "Closed Mode") shows the auto-approval bypass is not yet reliable, which blocks users who need fully unattended operation.

4. **Console UI performance** — Issue #5725 (browser lag during streaming) and #5421 (agent/window switching stutter) indicate frontend rendering bottlenecks.

5. **Windows-specific friction** — Vector index persistence (#5259) and installation packaging (#5165) have Windows-only failures.

**User sentiment:** The community is technically sophisticated (mentioning specific model backends like deepseek, stepfun, opencode, and specific frameworks like Tavily, UIA). They are using CoPaw for **real productivity workflows** (scheduling, file management, knowledge extraction). Dissatisfaction centers on reliability in long-running scenarios, but overall engagement is high.

## 8. Backlog Watch

**Issues needing maintainer attention (high user investment, no response):**

| Issue | Days Open | Last Update | Notes |
|-------|-----------|-------------|-------|
| [#5379](https://github.com/agentscope-ai/CoPaw/issues/5379) — Internal Server Error on fresh install | 17 | 2026-07-08 | 8 comments, 0 maintainer responses visible |
| [#5259](https://github.com/agentscope-ai/CoPaw/issues/5259) — Windows vector index persistence failure | 22 | 2026-07-08 | 4 comments, only user-to-user discussion |
| [#5725](https://github.com/agentscope-ai/CoPaw/issues/5725) — Console browser lag during streaming | 7 | 2026-07-08 | 5 comments, no assigned label or fix PR |

**PRs lingering without merge attention:**

| PR | Days Open | Status | Notes |
|----|-----------|--------|-------|
| [#4171](https://github.com/agentscope-ai/CoPaw/pull/4171) — Memory-distill tool plugin | 60 days | Under Review | Large feature (title-diffing distillation engine); has been under review for 2 months |
| [#5187](https://github.com/agentscope-ai/CoPaw/pull/5187) — Windows desktop GUI automation | 25 days | Open | Complex feature; may be waiting for v2.0 base stabilization |
| [#5692](https://github.com/agentscope-ai/CoPaw/pull/5692) — Memory search reranker | 8 days | Under Review | Core feature for memory quality; should prioritize for v2.0 |

**Overall project health:** **Stable with high activity.** The v2.0 beta is generating constructive bug reports. The maintainer team is shipping rapid patch releases (beta.3 → beta.4 in ~1 day for the scroll fix). The biggest risk is the **fresh install breakage** (#5379) and the **context loss in v2.0** (#5860), which could frustrate first-time adopters. The Windows-specific gaps (vector persistence, packaging) represent a growing pain point as the user base expands beyond Linux.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

# ZeroClaw Project Digest
**Date:** 2026-07-09

---

## 1. Today's Overview

ZeroClaw shows **high development velocity** with 50 issues and 50 PRs updated in the last 24 hours, indicating an **active and well-maintained project**. The open-to-closed ratio for issues (40:10) and PRs (37:13) suggests healthy triage activity, though the backlog remains substantial. No new releases were published today, but significant architectural work is converging: the WASM plugin system (tracker #8850), an OpenAI-compatible gateway adapter (RFC #8603), and the ZeroCode TodoWrite tracker (PR #8639, merged) represent major feature milestones. The project is actively addressing **security-critical SSRF surfaces** (PR #8713) and **UTF-8 truncation bugs** (PR #8873) from recent audits.

---

## 2. Releases

**No new releases today.** The latest release remains the previous version; no migration notes or breaking changes to report.

---

## 3. Project Progress

The following **13 PRs were merged or closed** today (representing meaningful progress):

- **#8639 [Closed]** — `feat(zerocode): TodoWrite tracker for ZeroCode (RPC + ACP + durable persistence)` — Implements a live, read-only task tracker in ZeroCode, similar to Claude Code/OpenCode. Adds a `TodoWrite` tool that models call with a whole-list plan; daemon emits as a durable event stream. This is a **major ZeroCode feature milestone**.

- **#8861 [Closed]** — `fix(providers): resolve alias credential for model-catalog so native /models is used` — Fixes model-catalog endpoint backing model dropdowns; previously hard-coded `None` API key, breaking credentialed OpenAI-compatible families (xAI/Grok, Groq, DeepSeek).

- **#8795 [Closed]** — `fix(web): add Skills nav entry to left sidebar (#8792)` — UX fix: Skills page was reachable only by direct URL; now has a sidebar entry.

- **#8553 [Closed]** — `[Bug]: Agent cannot use environment variables as http_request secrets` — **Severity S1** (workflow blocked): fixed so environment variables work as `auth_secret` sources.

- **#8334 [Closed]** — `[Bug]: skills install/list/remove target data_dir, which no multi-agent runtime loads` — **Severity S2** fix for the skill installation flow on multi-agent setups.

- **#4873 [Closed]** — `[Bug]: After integrating Feishu, only the LLM is called by default instead of the Agent.` — Long-standing channel routing bug resolved.

- **#6173 [Closed]** — `[Bug]: model_switch tool does not persist across turns; gateway/UI path ignores it entirely` — Critical runtime bug for model persistence.

- **#7737 [Closed]** — `bug(channels): carry approval attribution without a global side channel` — Fixes a **concurrency race** in approval attribution.

- **#7690 [Closed]** — `feat(provider): cover responses-wire option propagation` — Test coverage improvement.

- **#8267 [Open – needs-author-action]** — `test(robot-kit): cover RobotConfig defaults and TOML round-trip` — Test infrastructure PR.

- **#8863 [Open]** — `feat(plugins): host-mediated outbound WebSocket for channel plugins` — Enables WASM-based channel plugins to make outbound WebSocket connections **without recompiling the binary**. Stacks on the new plugin infrastructure.

- **#8854 [Open]** — `refactor(providers): typed builders and normalization uniformity across the provider crate` — Standardizes provider constructors across 14+ providers, eliminating 7 anti-patterns. **Architecture improvement, 1.2k+ line change.**

- **#8874 [Open]** — `fix(ci): scope rustdoc --default-theme away from cargo test --doc (#8847)` — CI fix for Rust 1.96's stricter rustdoc argument parser.

---

## 4. Community Hot Topics

**Most active issues (by comment count):**

| Issue | Comments | Topic |
|-------|----------|-------|
| [#5862](https://github.com/zeroclaw-labs/zeroclaw/issues/5862) | 13 | Agent unaware of `zeroclaw cron` capability |
| [#6034](https://github.com/zeroclaw-labs/zeroclaw/issues/6034) | 7 | **S1**: User message loss in single/multi-turn dialogues with custom provider |
| [#8424](https://github.com/zeroclaw-labs/zeroclaw/issues/8424) | 7 | **RFC**: `.ignore` file mechanism for workspace file protection |
| [#6002](https://github.com/zeroclaw-labs/zeroclaw/issues/6002) | 5 | **S1**: Telegram channel not addressed to assistant correctly |
| [#6672](https://github.com/zeroclaw-labs/zeroclaw/issues/6672) | 5 | **S0**: `reasoning_content` not passed back in tool-call loops (Mimo thinking models) |
| [#8226](https://github.com/zeroclaw-labs/zeroclaw/issues/8226) | 5 | **RFC**: Per-agent custom environment variables for multi-tenancy |

**Underlying needs revealed:**
- **Agent self-awareness gap** (#5862, 13 comments): Users expect agents to know what built-in capabilities they have (e.g., cron). This signals a usability/onboarding gap where the agent's tool inventory is opaque to itself.
- **Provider compatibility debt** (#6034, #6672, #6002): Multiple high-severity bugs with custom/OAI-compatible providers indicate **fragile provider abstraction** — the OpenAI-compatible adapter layer may need hardening.
- **Security/configuration authority** (#8424, #8226): Users want fine-grained control over what the agent can read (`.ignore`) and per-agent identity isolation. These are architectural concerns that reflect **enterprise deployment needs**.

---

## 5. Bugs & Stability

**Critical/High Severity Bugs Updated Today (ranked by severity):**

| Severity | Issue | Description | Has Fix PR? |
|----------|-------|-------------|-------------|
| **S0 – Data Loss** | [#8094](https://github.com/zeroclaw-labs/zeroclaw/issues/8094) | Anthropic provider added in Quickstart unavailable until reset | No |
| **S0 – Data Loss** | [#6672](https://github.com/zeroclaw-labs/zeroclaw/issues/6672) | `reasoning_content` not passed back in Mimo thinking mode tool loops | No |
| **S0 – Data Loss** | [#6558](https://github.com/zeroclaw-labs/zeroclaw/issues/6558) | Custom provider error (405) — provider configuration failure | No |
| **S1 – Blocked** | [#6034](https://github.com/zeroclaw-labs/zeroclaw/issues/6034) | User message loss in dialogue with custom provider | No |
| **S1 – Blocked** | [#7527](https://github.com/zeroclaw-labs/zeroclaw/issues/7527) | macOS app not working — permission detection failure, empty page | No |
| **S1 – Blocked** | [#6002](https://github.com/zeroclaw-labs/zeroclaw/issues/6002) | Telegram message misrouting with llama.cpp | No |

**Stability notes:**
- **Kubernetes/container stability**: PR #8866 (`fix(daemon): share MCP registry across heartbeat ticks`) addresses an MCP server crash-loop pattern where each heartbeat tick spawned a new duplicate MCP connection. This affects **production deployments** using stdio MCP servers.
- **CI regression**: PR #8870 addresses a **red master CI** — two `zeroclaw-log` tests deterministically fail due to async write flushing.
- **UTF-8 crash regression**: PR #8873 (`fix(cli): UTF-8-safe stdin cap in exit prompt + audit trail`) is a follow-up to the panics from issue #7828, indicating this bug class **recurs** across the codebase.
- **SSRF vulnerability**: PR #8713 closes the third remaining SSRF surface from a July 3 security audit — the `file_download` tool now has an `allowed_private_hosts` opt-in gate.

---

## 6. Feature Requests & Roadmap Signals

**Likely candidates for next release (v0.8.3 or v0.9.0):**

- **#8850 — WASM Plugin Infrastructure** ([tracker](https://github.com/zeroclaw-labs/zeroclaw/issues/8850)): Moving optional channels/tools from compile-time feature flags to WASM plugins. **Status: In-progress, 4 comments today.** This is the most transformative architectural change — a stock binary can gain channels without recompiling. PR stack #8863 (WebSocket for channel plugins) and #8862 (webhook ingress) are landing now.

- **#8603 — OpenAI Chat Completions Compatibility Adapter** ([RFC](https://github.com/zeroclaw-labs/zeroclaw/issues/8603)): Exposes agent capabilities via OpenAI-compatible API (enabling Open WebUI, LobeChat, custom integrations). **4 comments, status: accepted.** High-impact for ecosystem integration.

- **#7543 — Multi-session support in web chat UI** ([feature](https://github.com/zeroclaw-labs/zeroclaw/issues/7543)): Session sidebar with new/switch/rename/delete per agent. **3 comments, updated today.** Prioritized by the community.

- **#8602 — Enhanced `file_read` tool** ([tracker](https://github.com/zeroclaw-labs/zeroclaw/issues/8602)): Default line cap, charset detection, paged PDF, notebook awareness, chunked binary reads. Aligns with Claude Code patterns.

- **#8071 — v0.8.3 Runtime Execution & Tools Tracker** ([tracker](https://github.com/zeroclaw-labs/zeroclaw/issues/8071)): The umbrella for the next release. **Active.**

**Prediction:** The WASM plugin initiative (#8850) and OpenAI compatibility adapter (#8603) are the two highest-impact features. The TodoWrite tracker (#8639, already merged) is practically in the next release. A **v0.8.3** release could land within 2–3 weeks given the current velocity.

---

## 7. User Feedback Summary

**Pain points expressed today:**

- **macOS experience broken** ([#7527](https://github.com/zeroclaw-labs/zeroclaw/issues/7527)): "The zeroclaw app can't detect granted permissions, display empty page. When quit and restart, the app's window disappeared." — **Desktop experience blocker for macOS 15.7.7 users.**

- **Provider setup friction** ([#8094](https://github.com/zeroclaw-labs/zeroclaw/issues/8094)): "When adding model it was showing on dashboard not in chat window until I reset." — **Quickstart workflow regression** where providers added via UI aren't visible to the chat.

- **Android/Termux unavailability** ([#7911](https://github.com/zeroclaw-labs/zeroclaw/issues/7911)): "Precompiled binary and local compilation both result in the unknown linux aarch64 binary being installed." — **Platform gap for mobile users.**

- **Context overflow / hallucination** ([#6517](https://github.com/zeroclaw-labs/zeroclaw/issues/6517)): "When conversation runs long enough to fill context window, bot starts hallucinating/drifting off-topic." — **Memory management pain** affecting long-running sessions.

**Themes:**
1. **Provider interoperability** is the #1 friction source (custom APIs, thinking mode, credential passing).
2. **Desktop/mobile platform support** (macOS, Android) is lagging behind the server-side development velocity.
3. **Security-conscious users** are actively requesting configuration authority mechanisms (`.ignore`, per-agent env vars, SSRF protection).

---

## 8. Backlog Watch

**Issues requiring maintainer attention (long-unanswered, important):**

| Issue | Open Since | Comments | Risk | Notes |
|-------|------------|----------|------|-------|
| [#7527](https://github.com/zeroclaw-labs/zeroclaw/issues/7527) | 2026-06-12 (27 days) | 1 | **High** | macOS app completely broken — **no maintainer response**. |
| [#7673](https://github.com/zeroclaw-labs/zeroclaw/issues/7673) | 2026-06-15 (24 days) | 3 | **High** | Native context compression RFC — **blocked, needs-author-action.** Author hasn't responded for 24 days. |
| [#7497](https://github.com/zeroclaw-labs/zeroclaw/issues/7497) | 2026-06-11 (28 days) | 3 | **High** | OCI registry for WASM plugin storage — **blocked.** Important for plugin distribution. |
| [#7215](https://github.com/zeroclaw-labs/zeroclaw/issues/7215) | 2026-06-04 (35 days) | 0 | **High** | Quickstart PR for webhook port field — **needs-author-action, stale-candidate.** Would improve FTUE. |
| [#6558](https://github.com/zeroclaw-labs/zeroclaw/issues/6558) | 2026-05-10 (60 days) | 4 | **Low** | Custom provider 405 error — **stale-candidate, needs-author-action.** Low risk but long unresolved. |

**Alert:** PR #8267 (`test(robot-kit): cover RobotConfig defaults`) has been labeled `stale-candidate` and `needs-author-action` since June 24 — test PRs with no maintainer review for 15 days risk being auto-closed. With 37 open PRs and 40 open issues needing author action, the project could benefit from **stale-bot threshold adjustment** or additional reviewer bandwidth.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*