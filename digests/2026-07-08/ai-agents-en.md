# OpenClaw Ecosystem Digest 2026-07-08

> Issues: 500 | PRs: 500 | Projects covered: 13 | Generated: 2026-07-08 01:48 UTC

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

# OpenClaw Project Digest — 2026-07-08

## 1. Today's Overview

OpenClaw continues to show extremely high activity with 500 issues and 500 PRs updated in the last 24 hours, indicating a very actively maintained project. The open/active issue count stands at 379, while 121 issues were closed. On the PR side, 365 remain open and 135 were merged or closed. No new releases were published today. The project maintains a heavy focus on stability, with numerous critical (P1) and high-priority (P2) issues receiving attention, many tagged with the `diamond lobster` severity rating. A cluster of recent PRs suggests active work on mid-turn context precheck accuracy, media understanding/image handling, and memory UTF-16 safety.

## 2. Releases

No new releases were published today.

## 3. Project Progress

**Merged/Closed PRs Today:** 135 PRs were merged or closed in the last 24 hours. Notable closed items include:

- **#52972** (CLOSED) — *Bug: Incorrect 'I did not schedule a reminder' note appended to messages after scheduling cron reminders* — Fix merged for UX regression where successful cron scheduling appended a misleading "no reminder scheduled" note.
- **#90370** (CLOSED) — *[Feature Request] Support PostgreSQL as alternative to SQLite for internal storage* — Closed, though no release notes are available to confirm implementation details.
- **#45388** (CLOSED) — *TUI --session mode doesn't live-stream messages* — Resolved.
- **#40418** (CLOSED) — *Feature Request: Automated Session Memory Preservation & Synthesis* — Closed.

**Active PRs with meaningful progress today:**
- **#101953** (OPEN, today) — *fix(media-understanding): apply imageMaxDimensionPx resize to image description input* — Fixes phone-camera photos exceeding provider limits.
- **#101946** (OPEN, today) — *[AI] fix(memory): use truncateUtf16Safe for dreaming snippet truncation* — Prevents broken emoji rendering in daily memory.
- **#101926** (OPEN, today) — *fix(channels): keep native /think menus responsive* — Addresses Telegram `/think` menu unresponsiveness during slow model discovery.
- **#101762** (OPEN, today) — *fix(agent-core): skip handleRunFailure error forwarding for control-flow signals* — Prevents false error propagation during mid-turn context precheck.
- **#101920** (OPEN, today) — *fix(auto-reply): self-heal reply-session-init conflict instead of permanently wedging the session* — Fixes a session-wedging bug (#101909).

## 4. Community Hot Topics

The following issues and PRs generated the most community engagement (by comment count and reactions):

1. **#25592** (33 comments) — *[P1, diamond lobster] Text between tool calls leaks to messaging channels* — [Link](https://github.com/openclaw/openclaw/issues/25592). Core UX problem where internal processing text reaches users. Tagged with security and message-loss impacts. Community strongly engaged.

2. **#44925** (21 comments) — *[P1, diamond lobster] Subagent completion silently lost — no retry, no notification, no auto-restart on timeout* — [Link](https://github.com/openclaw/openclaw/issues/44925). Multiple subagent task orchestration failure modes causing silent data loss.

3. **#11829** (20 comments) — *Security Roadmap: Protecting API Keys from Agent Access* — [Link](https://github.com/openclaw/openclaw/issues/11829). Systemic security issue with API key exposure vectors.

4. **#22676** (17 comments) — *[P1, diamond lobster] Signal daemon stop() race condition on SIGUSR1 restart* — [Link](https://github.com/openclaw/openclaw/issues/22676). Process management bug causing orphaned processes and send failures.

5. **#22438** (17 comments) — *[P2, diamond lobster] Tiered bootstrap file loading for progressive context control* — [Link](https://github.com/openclaw/openclaw/issues/22438). Feature request for more efficient context window management.

6. **#39604** (13 comments, 👍 11) — *[P2, diamond lobster] Add tools.web.fetch.allowPrivateNetwork* — [Link](https://github.com/openclaw/openclaw/issues/39604). Highly upvoted feature request for private network access.

7. **#29387** (14 comments, 👍 5) — *[P1, diamond lobster] Bootstrap files in agentDir silently ignored* — [Link](https://github.com/openclaw/openclaw/issues/29387). Configuration bug where per-agent bootstrap files are not loaded.

8. **#96857** (12 comments, 👍 4) — *Normal tool text outputs can degrade to "(see attached image)" placeholders* — [Link](https://github.com/openclaw/openclaw/issues/96857). UX regression making agent blind to command outputs.

**Underlying needs:** The community is consistently asking for: (a) reliable subagent orchestration, (b) better context window management, (c) secret/key security, (d) stable multi-channel message delivery, and (e) improved observability into agent internals.

## 5. Bugs & Stability

**Critical/Severe Bugs (P1, diamond lobster rating):**

| Issue | Summary | Fix PR? |
|-------|---------|---------|
| #25592 | Text between tool calls leaks to messaging channels | No linked PR |
| #44925 | Subagent completion silently lost on timeout | No linked PR |
| #22676 | Signal daemon race condition on restart, orphaned processes | No linked PR |
| #29387 | Bootstrap files in agentDir silently ignored | No linked PR |
| #31583 | `exec` tool does not inherit `skills.entries.*.env` environment variables | No linked PR |
| #43367 | Multi-agent orchestration unstable: config overwrites, session-lock failures | No linked PR |
| #38327 | "Cannot convert undefined or null to object" with google-vertex/gemini-3.1 | No linked PR |
| #41165 | Telegram DMs pollute heartbeat/main session after fix | No linked PR |
| #99241 | Tool outputs render as image attachments, agent cannot read text | No linked PR |
| #85333 | Performance regression: `doctor --fix` 4-5x slower (55s → 229s+) | No linked PR |
| #42820 | Feishu send action polluted by poll schema prevents file send | No linked PR |
| #94846 | Cron isolated agentTurn skips delivery after recovered tool error | No linked PR |

**Regressions reported:**
- #31583: `exec` tool env variable inheritance regression
- #38327: google-vertex/gemini-3.1 "Cannot convert undefined or null to object" regression
- #43747: Memory management in chaos across users (different behavior, regression from prior consistent behavior)
- #38439: Webchat avatar endpoint returns 404 regression
- #41201: Control UI avatar broken image regression

**Issues with fix PRs in flight:**
- #101923 (image dimension limits) → fix PRs #101947 and #101953
- #101929 (mid-turn precheck over-counting) → fix PRs #101950, #101951, #101952
- #101909 (reply-session-init conflict) → fix PR #101920
- #97747 (re-entrant session write lock for compaction) → fix PR #101928
- #97602 (broken workspace avatars) → fix PR #97634
- #101718 (parent fork stalls on token probing) → fix PR #101932

## 6. Feature Requests & Roadmap Signals

**Most actionable feature requests (with community traction and maintainer labeling):**

1. **#22438** — *Tiered bootstrap file loading* (P2, diamond lobster) → [Link](https://github.com/openclaw/openclaw/issues/22438). Would address context window waste. Likely to appear in next minor release given systematic approach.
2. **#39604** — *Allow private network access for web_fetch* (P2, diamond lobster, 👍11) → [Link](https://github.com/openclaw/openclaw/issues/39604). Simple config toggle, high demand.
3. **#42475** — *Per-agent cost budget enforcement* (P2, diamond lobster) → [Link](https://github.com/openclaw/openclaw/issues/42475). Enterprise-grade feature for cost control.
4. **#22358** — *Post-subagent completion extension hook* (P2, diamond lobster) → [Link](https://github.com/openclaw/openclaw/issues/22358). Enables structured trajectory generation.
5. **#27445** — *announceTarget for sub-agent completion routing* (P2, diamond lobster, 👍5) → [Link](https://github.com/openclaw/openclaw/issues/27445). Enables main-agent orchestration of multi-step workflows.
6. **#35203** — *Multi-Agent Collaboration Enhancement: Capability Profiling + Shared Blackboard* (P2, tidepool) → [Link](https://github.com/openclaw/openclaw/issues/35203). Long-term architecture RFC.
7. **#20786** — *Telegram Business Bot support* (P2, diamond lobster, 👍6) → [Link](https://github.com/openclaw/openclaw/issues/20786). Growing demand for Telegram business features.
8. **#42840** — *MathJax/LaTeX Support in Control UI* (P2, diamond lobster, 👍9) → [Link](https://github.com/openclaw/openclaw/issues/42840). Strong community desire for scientific/math content rendering.
9. **#28300** — *Theme Customization System* (P2, tidepool, 👍5) → [Link](https://github.com/openclaw/openclaw/issues/28300). UX enhancement now in RFC stage.
10. **#37634** — *Sandbox writable workspaces with workspaceAccess "none"* (P1, diamond lobster, 👍7) → [Link](https://github.com/openclaw/openclaw/issues/37634). Sandbox usability improvement with high community backing.

**Predictions for next version:** Given the volume of P1/P2 diamond-lobster issues with active PRs, the next release will likely include: image/media dimension handling improvements, mid-turn context precheck accuracy fixes, memory UTF-16 safety improvements, session compaction/lock fixes, and sandbox writable workspace support.

## 7. User Feedback Summary

**Real user pain points expressed across issues:**
- **Data loss in multi-session workflows:** Multiple users report subagent completions silently lost (#44925), cron sessions overwriting shared files (#40001), and detached child work in multi-agent orchestration (#43367).
- **Context window management frustration:** Users want tiered bootstrap loading to avoid wasting tokens (#22438), and are hitting context overflow false positives (#101929).
- **Channel-specific message delivery issues:** Feishu file sends blocked (#42820), Telegram DMs polluting main session (#41165), image attachment placeholders making agent blind to tool outputs (#99241, #96857).
- **Configuration complexity:** Per-agent bootstrap files ignored (#29387), Docker sandbox workspace mounting broken (#31331), `exec` tool env vars not inherited (#31583).
- **Performance regressions:** `doctor --fix` 4-5x slower (#85333), memory management inconsistent across users (#43747).

**Positive signals:** Feature requests from the community are being labeled and triaged with product decisions and security reviews, indicating active maintainer engagement. Multiple users are running production deployments (Oracle Cloud, Telegram forum bots, multiple team setups).

**Dissatisfaction themes:** Users express frustration with "silent" failures — subagent completions disappearing without notification, cron sessions silently overwriting data, and tool errors leaking to channels as confusing warnings. Several Chinese-language issues (#90370, #42840) indicate growing non-English-speaking userbase seeking localization and PostgreSQL support.

## 8. Backlog Watch

**Issues needing maintainer attention (long-open, high severity, no linked PR):**

| Issue | Age | Summary | Status |
|-------|-----|---------|--------|
| #11829 | Created 2026-02-08 (5 months) | Security Roadmap: Protecting API Keys | Still open, no PR, security-critical |
| #25592 | Created 2026-02-24 (4.5 months) | Text between tool calls leaks to channels | Still open, no fix PR |
| #44925 | Created 2026-03-13 (4 months) | Subagent completion silently lost | Still open, no fix PR |
| #22676 | Created 2026-02-21 (4.5 months) | Signal daemon race condition | Still open, no fix PR |
| #29387 | Created 2026-02-28 (4.3 months) | Bootstrap files in agentDir ignored | Still open, no fix PR |
| #31583 | Created 2026-03-02 (4.2 months) | `exec` tool env var inheritance broken | Still open, no fix PR |
| #99451 | Created 2026-07-03 (5 days) | (Recent, but not yet triaged) | New issue, no maintainer response yet |

**Long-unanswered high-value PRs needing review:**
- **#98236** (created 2026-06-30, P1, gold shrimp) — *refactor: flip sessions and transcripts to sqlite storage* — [Link](https://github.com/openclaw/openclaw/pull/98236). Large refactor (XL size) touching nearly every subsystem. Tagged with multiple merge-risk labels. Has been in review for 8 days with extensive labeling but no merge. This is a foundational infrastructure change.
- **#100845** (created 2026-07-06, P2, platinum hermit) — *fix(cli): one-shot agent --local runs never export OTel diagnostics* — [Link](https://github.com/openclaw/openclaw/pull/100845). Tagged with automerge but still open after 2 days.
- **#100184** (created 2026-07-05, P3, silver shellfish) — *feat(sandbox): add skipSkillsSync config option* — [Link](https://github.com/openclaw/openclaw/pull/100184). Simple config feature, still awaiting review.

**Concern:** Several P1 diamond-lobster-rated issues have been open for 4+ months with no fix PR linked. This suggests either (a) these are extremely difficult problems requiring architectural changes, (b) maintainers are prioritizing differently, or (c) these issues are being tracked but not actively worked. The project's stability would benefit from progress updates or status changes on these long-standing critical items.

---

## Cross-Ecosystem Comparison

# Cross-Project Ecosystem Comparison Report — 2026-07-08

## 1. Ecosystem Overview

The open-source personal AI assistant ecosystem is experiencing a maturation phase, characterized by intense competition in stability and security hardening rather than novel feature velocity. Seven of eleven tracked projects showed meaningful activity today, with a combined total exceeding 700 issues and 750 PRs updated across the ecosystem. A notable trend is the coordinated security disclosure pattern—three projects (NanoBot, LobsterAI, TinyClaw) received critical vulnerability reports from the same researcher (YLChen-007), suggesting systematic ecosystem-wide auditing is underway. The landscape is bifurcating between large, resource-rich reference implementations (OpenClaw, Hermes Agent) and specialized, lightweight alternatives (PicoClaw, TinyClaw), with mid-tier projects like ZeroClaw and CoPaw showing the highest velocity-to-size ratios.

## 2. Activity Comparison

| Project | Issues Updated | PRs Updated | Release Today | Activity Level | Health Indicators |
|---------|---------------|-------------|---------------|----------------|-------------------|
| **OpenClaw** | 500 | 500 | None | 🔴 Extreme | 379 open issues, 135 PRs closed, strong triage |
| **ZeroClaw** | 23 | 50 | None | 🔴 Very High | 8 PRs merged, 3 security fixes |
| **CoPaw** | 16 | 38 | v2.0.0-beta.3 | 🔴 High | 15 PRs merged, pre-release stabilization |
| **Hermes Agent** | 50 | 50 | v0.18.1 | 🟡 High | 18 issues closed, 13 PRs merged, post-release |
| **NanoBot** | 12 | 32 | None | 🟡 High | 11 PRs merged, security disclosures |
| **NanoClaw** | 4 | 23 | None | 🟡 Moderate | 9 PRs merged, documentation refresh |
| **LobsterAI** | 9 | 16 | v2026.7.7 | 🟡 Moderate | 14 PRs merged, release sprint |
| **PicoClaw** | 7 | 4 | None | 🟢 Low | 1 PR merged, maintenance phase |
| **TinyClaw** | 9 | 0 | None | 🟢 Low | Security disclosures only, no code activity |
| **NullClaw** | 0 | 0 | None | ⚪ Inactive | — |
| **Moltis** | 0 | 0 | None | ⚪ Inactive | — |
| **ZeptoClaw** | 0 | 0 | None | ⚪ Inactive | — |

**Ecosystem totals:** ~630 issues, ~713 PRs updated, 3 releases published.

## 3. OpenClaw's Position

**Advantages:** OpenClaw operates at a scale unmatched across the ecosystem—its 500 daily issues/PRs exceed the combined activity of the next three most active projects (ZeroClaw, CoPaw, Hermes Agent). Its `diamond lobster` severity taxonomy and structured triage process represent the most mature quality management system observed. The project shows strong institutional backing with dedicated security roadmap tracking (#11829) and systematic regression monitoring.

**Technical approach:** OpenClaw's architecture is monorepo-based with comprehensive subagent orchestration, multi-channel message routing, and PostgreSQL support in development. Its `doctor --fix` diagnostic tool and TUI mode indicate a developer-centric design philosophy. The project maintains the deepest integration surface—supporting Telegram, Feishu, WebChat, cron scheduling, and file-based workflows simultaneously.

**Community scale:** With 135 PRs merged/closed daily, OpenClaw's contribution velocity is ~5x that of the nearest competitor (CoPaw at 15 merges). However, 379 open issues (76% of tracked) suggest triage capacity may be approaching saturation. The project's 4+ month unresolved P1 issues (subagent data loss, signal daemon races) indicate that even at this scale, architectural debt accumulates.

**Comparison to peers:**
- vs **Hermes Agent**: OpenClaw has ~10x more daily activity but higher issue resolution latency
- vs **ZeroClaw**: OpenClaw has broader channel support but less aggressive security patching (ZeroClaw fixed RUSTSEC-2026-0204 same-day)
- vs **CoPaw**: OpenClaw has more mature subagent orchestration but CoPaw's beta track moves faster on new features

## 4. Shared Technical Focus Areas

| Requirement | Affected Projects | Specific Needs |
|-------------|-------------------|----------------|
| **Subagent/multi-agent orchestration reliability** | OpenClaw, Hermes Agent, LobsterAI, ZeroClaw | Silent data loss on subagent timeout (#44925), unstable config isolation (#2293), context erasure on interrupt (#8794) |
| **Context window management** | OpenClaw, CoPaw, ZeroClaw | Frontend crashes on large sessions (#5401, #5479), wasted tokens from untiered bootstrapping (#22438), mid-turn precheck over-counting (#101929) |
| **API key/credential security** | OpenClaw, NanoBot, LobsterAI, TinyClaw, Hermes Agent | Key exposure via agent access (#11829), unauthenticated control planes (#4825, #2286, #294), stale credential pools (#55790) |
| **Channel-specific message delivery** | OpenClaw, NanoBot, CoPaw, ZeroClaw | WhatsApp group isolation (#4823), Feishu file sends blocked (#42820), Telegram DMs polluting main session (#41165) |
| **MCP tool reliability** | NanoBot, Hermes Agent, ZeroClaw | Subprocess leaks (#4843, #59349), MCP tool-schema OOM risk (#8642), reconnect crashes (#4764) |
| **Cross-platform Windows stability** | Hermes Agent, CoPaw, ZeroClaw | Zombie ports (#8800), sandbox ACE pollution (#5829), chat UI alignment (#60596) |
| **Security hardening (SSRF, TOCTOU, path traversal)** | NanoBot, LobsterAI, TinyClaw, NanoClaw, ZeroClaw | DNS rebinding (#4611), symlink traversal (#2288), unauthenticated webhooks (#2970), MCP tool filter bypass (#6699) |

## 5. Differentiation Analysis

| Dimension | OpenClaw | Hermes Agent | ZeroClaw | CoPaw | NanoBot | PicoClaw | TinyClaw |
|-----------|----------|--------------|----------|-------|---------|----------|----------|
| **Primary architecture** | Monorepo, multi-channel | Modular, plugin-based | Rust core, WASM tools | Plugin API, desktop | Lightweight, MCP-native | Embedded-first, minimal | Research prototype |
| **Target user** | Enterprise/deployment | Downstream consumers | Power users | Plugin developers | Hobbyists/makers | Edge/IoT | Security researchers |
| **Key differentiator** | Broadest integration surface | Fastest release cycle | Rust safety guarantees | Plugin ecosystem | Channel breadth | Minimal footprint | Novelty/experiment |
| **Language** | TypeScript/JavaScript | Python | Rust | Python | Python | C/Rust | Python |
| **Channel support** | 6+ (Telegram, Feishu, WebChat, CLI, cron, API) | 4+ (Discord, WebUI, CLI, API) | Telegram, Web Dashboard | 5+ (Matrix, DingTalk, Discord, CLI, API) | 8+ (WhatsApp, WeChat, Feishu, Matrix, Telegram, Slack, QQ, API) | 2+ (CLI, DeltaChat) | CLI only |
| **AI provider flexibility** | High (any OpenAI-compatible) | High (multi-provider) | Medium (limited config) | High (multi-provider) | Medium | Low (config-limited) | Low (Anthropic-focused) |
| **Security maturity** | Medium (roadmap exists, slow patching) | Medium | High (Rust, fast patches) | Medium | Low (disclosures unaddressed) | Low | Critical gaps |
| **Release cadence** | Daily (rolling) | Weekly (v0.18.x) | Weekly (v0.8.x) | Weekly (beta) | Bi-weekly (v0.2.x) | Monthly (v0.3.x) | No cadence |

**Strategy divergence:** The ecosystem shows three distinct approaches:
1. **Platform play** (OpenClaw, ZeroClaw): Build the broadest capability surface, accept complexity
2. **Integration focus** (NanoBot, CoPaw): Prioritize channel/plugin breadth over architecture
3. **Minimalist/specialist** (PicoClaw, TinyClaw, NullClaw): Trade capability for simplicity or novelty

## 6. Community Momentum & Maturity

### Tier 1: Rapid Iteration (daily releases/patches)
- **OpenClaw**: 500 daily updates, but 379 open issues indicate velocity-outpacing-quality
- **ZeroClaw**: Highest per-contributor output, security-first culture
- **CoPaw**: Beta track shows aggressive feature velocity (v2.0.0-beta.3 today)

### Tier 2: Stabilizing (weekly/bi-weekly cadence)
- **Hermes Agent**: Post-v0.18.1, shifting from feature to stability focus
- **NanoClaw**: Documentation refresh signals confidence in core stability
- **LobsterAI**: Released v2026.7.7, clearing bug backlog from April 2026

### Tier 3: Low Activity / Stagnating
- **PicoClaw**: Maintenance mode, 1 PR merged
- **TinyClaw**: Security disclosures with zero maintainer response—serious risk
- **NullClaw/Moltis/ZeptoClaw**: No activity, effectively inactive

### Key community health signals:
- **Positive**: 11 first-time contributor PRs across ecosystem today (3 in CoPaw, 3 in NanoClaw, 2 in ZeroClaw)
- **Concerning**: 4 projects have unaddressed security disclosures (NanoBot: 3, LobsterAI: 3, TinyClaw: 9, NanoClaw: 1)
- **Critical**: TinyClaw's 9 critical vulnerabilities with zero maintainer response in 24h is the ecosystem's most urgent failure

## 7. Trend Signals

### For AI Agent Developers

**1. Security is becoming a competitive differentiator**
- The coordinated YLChen-007 disclosures across NanoBot, LobsterAI, and TinyClaw signal a shift from "build first, secure later" to "security is a prerequisite"
- ZeroClaw's RUSTSEC-2026-0204 patch within 24 hours sets a new bar for response time
- **Takeaway**: Embed security audits into CI/CD now; agent developers will increasingly require SBOMs and vulnerability disclosure policies

**2. Multi-agent orchestration is the next frontier—and it's broken**
- Every major project (OpenClaw, Hermes Agent, ZeroClaw, CoPaw) has unresolved subagent data loss, context corruption, or config isolation bugs
- The ecosystem is discovering that subagent reliability is qualitatively harder than single-agent performance
- **Takeaway**: Invest in deterministic subagent session management; tools like zero-copy context passing and atomic state transitions are unmet needs

**3. Platform-specific stability is a growing pain point**
- Windows bugs appear across Hermes Agent (chat UI, WSL), CoPaw (sandbox ACE pollution), and ZeroClaw (zombie ports)
- The web dashboard/Chat UI is the most complained-about component across all projects
- **Takeaway**: Cross-platform testing remains underinvested; desktop UI frameworks (Tauri, Electron) introduce their own fragility

**4. The MCP protocol is creating new attack surfaces**
- MCP tool-schema OOM risk (ZeroClaw #8642), subprocess leaks (NanoBot #4843, Hermes Agent #59349), and bypassed policy filters (ZeroClaw #6699) all stem from the MCP integration layer
- **Takeaway**: MCP is not a security boundary; agent developers must implement their own policy enforcement and resource limits around MCP tools

**5. User demand is shifting from features to reliability**
- Community feedback across all projects shows frustration with "silent failures"—subagent completions disappearing, cron overwriting data, tool errors leaking as confusing warnings
- Feature requests are increasingly about configurability (notification toggles, tiered bootstrap loading, per-execution confirmation) rather than new capabilities
- **Takeaway**: The market is maturing; reliability and observability will determine which projects survive the 2027 consolidation phase

**6. Lightweight agents are emerging as a counter-trend**
- PicoClaw (embedded), TinyClaw (minimal), and NullClaw/Moltis (no activity but architectural simplicity) represent a backlash against OpenClaw's complexity
- The NanoKVM deployment (PicoClaw #3195) and DeltaChat integration signal demand for agents that run on resource-constrained devices
- **Takeaway**: There is room for a "Raspberry Pi-class agent" — none of the major projects currently serve this niche well

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

# NanoBot Project Digest — July 8, 2026

## Today's Overview

The NanoBot project is experiencing a very high-activity period, with 12 issues and 32 pull requests updated in the last 24 hours — significantly above the typical daily average. This surge is driven by a concentrated burst of new security disclosures, stability fixes for MCP and WebUI, and substantial community contributions. Activity is healthy, with 9 open issues and 21 open PRs indicating active triage and development. Notably, no new releases were published, suggesting the team is consolidating fixes before cutting a release.

## Releases

No new releases were published today. The last known version remains **0.2.2**, as referenced in issue reports. Users still on 0.1.5post2 are being encouraged to upgrade but report regressions (e.g., WhatsApp group behavior, streaming stalls). A point release or 0.2.3 is likely imminent given the number of merged fixes.

## Project Progress

**Merged/Closed PRs (11 total):** Several important fixes and features have been integrated:

- **#3378** (merged) — Adds a `camera_capture` tool for webcam photo capture via OpenCV (disabled by default). Enables physical world interaction.
- **#3517** (merged) — Fixes WeChat message drops after gateway restart due to stale `context_token`.
- **#3743** (merged) — Implements support for provider-hosted web search tools (e.g., Azure OpenAI `web_search` native tool) with local fallback, landing a long-running feature request.
- **#4763** (merged) — Feishu channel: adds new session divider messages, suppresses duplicate text bubbles for authorized `/new` commands.
- **#3232** (merged) — Refactors agent task done-callback logic and snapshot pending keys for readability and future-proofing.
- **#4611** (closed) — Security fix for DNS rebinding TOCTOU in SSRF validation (`validate_url_target` did not pin resolved IPs). Patch landed.

**Still open but advancing:** Bugfix PRs for WhatsApp group allowlist (#4834), multi-modal `.strip()` crash (#4837), and MCP reconnect crashes (#4843, #4764) are in review.

## Community Hot Topics

The most active discussions today center on **security vulnerabilities** and **regressions**:

- **#4825, #4826, #4827** (three linked issues by YLChen-007, all opened 2026-07-07) — **Security: WebUI bootstrap token issuance.** These report that any unprivileged localhost process can mint API-capable bearer tokens via `/webui/bootstrap` when no `tokenIssueSecret` or static token is configured. Each has 0 comments but represent a coordinated disclosure, likely part of a bug bounty or security audit. Very high attention needed.
- **#4611** (closed, 1 comment, security) — DNS rebinding TOCTOU fix was merged, indicating the maintainers responded quickly to a prior disclosure.
- **#4823** (open, 3 comments) — **WhatsApp group regression**: users report that after 0.2.2, group responses now leak to all groups the bot is in, and the `allow` filter for group IDs is broken. High frustration with migration friction.
- **#4013** (closed, 6 comments) — Stalled LLM stream after upgrading from 0.1.5post2 to 0.2.0, user needed workarounds to keep sessions alive. Representative of migration pain.

**Underlying needs:** The community is signaling strong demand for (a) stable migration paths across minor version bumps, (b) clear security hardening on the WebUI localhost surface, and (c) rapid patching of channel-specific regressions (WhatsApp, Matrix).

## Bugs & Stability

### Critical Severity
- **#4825/#4826/#4827 (Security: WebUI token minting)** — Unauthenticated localhost processes can obtain API bearer tokens. No fix PR yet, but issues are from a single reporter and likely under internal review. **No existing fix.**
- **#4611 (DNS rebinding TOCTOU)** — Fixed and closed. SSRF validation now pin resolved IPs.

### High Severity
- **#4835 (WebUI landing message routing)** — First message on landing page can be sent to an unrelated existing chat. **Fix PR #4836** submitted by the same reporter — likely to be merged soon.
- **#4823 (WhatsApp group allowlist broken post-0.2.2)** — Group responses leak across all groups, `allowFrom` does not accept group IDs. **Fix PR #4834** submitted by chengyongru.
- **#4800 (crash on multimodal messages)** — `.strip()` called on list-form `msg.content` crashes agent loop. **Fix PR #4837** submitted by Xingkai98.
- **#4805 (tool validation errors silently swallowed)** — `suppress(Exception)` in `prepare_call` hides critical validation failures. **Fix PR #4837** also addresses this.

### Medium Severity
- **#4841 (Matrix device untrusted)** — No cross-signing path for bot devices; permanent "Untrusted" warning in Element. No fix PR yet.
- **#4829 (Slack dependency missing aiohttp)** — Slack plugin cannot be enabled due to missing dependency in `pyproject.toml`. Workaround exists (manual install).
- **#4840 (zombie subprocess leak)** — Shell tool fails to reap zombie processes on all exit paths. **Fix PR #4840** submitted.
- **#4839 (Telegram HTML parse_mode overflow)** — Streamed responses break HTML formatting on chunk boundaries. **Fix PR #4839** submitted.
- **#4838 (QQ reconnect backoff)** — No exponential backoff leads to rapid reconnect loops. **Fix PR #4838** submitted.

**Overall stability assessment:** High volume of regressions from 0.2.x upgrades, but most have actively submitted fix PRs. The security disclosures are the most concerning gap.

## Feature Requests & Roadmap Signals

- **Provider-hosted web search (#3741 merged)** — Now supported via PR #3743. This is a major feature: users can enable Azure-native `web_search` tool with local fallback. Likely a key selling point for enterprise users on Azure.
- **MCP idle timeout auto-kill (#4506, open, conflict)** — Proposal to auto-kill idle MCP subprocesses to prevent resource leaks. Has conflict status but is being iterated on.
- **WebUI file edit diff view (#4828, open)** — PR adds unified diff rendering for file edit events in WebUI. This enhances the agent's code editing UX significantly.
- **Goal gating behind runtime mode (#4833, open)** — Replaces always-visible long_task/complete_goal tools with runtime-gated alternatives, moving long-goal skills into internal prompt templates. This restructures how the agent handles sustained tasks — a significant UX and architecture change likely for 0.3.0.
- **Camera capture tool (#3378 merged)** — New tool for physical world interaction. Likely to be part of next release.

**Prediction for next version (likely 0.2.3 or 0.3.0):** Expect security patches for WebUI bootstrap, WhatsApp group fix, multimodal crash fix, MCP reconnect stability, and the goal runtime gating. The camera capture and provider-hosted web search are already merged.

## User Feedback Summary

**Satisfaction:**
- Users report that 0.1.5post2 was "very good" (from #4013).
- The community is actively contributing PRs — 11 merged/closed today signals high engagement.
- Multiline input (Alt+Enter) was welcomed (#4832 follow-up).

**Pain Points:**
- **Migration friction:** Multiple users cite breakage after upgrading from 0.1.5post2 to 0.2.0/0.2.2. Specific complaints: 90-second stream stall (#4013), WhatsApp group leakage (#4823), and missing dependencies (#4829).
- **Security concerns:** Unauthenticated localhost token issuance is a significant trust issue for users running multi-tenant or shared environments.
- **Matrix encryption:** The "untrusted" device warning in Element is a persistent UX issue for users relying on E2EE.
- **Group messaging:** WhatsApp group allowlist regression is actively disrupting users who depend on group isolation.

**Overall sentiment:** The user base is technically engaged and active, but trust is being tested by regression density in the 0.2.x series. The swift response with fix PRs is partially mitigating frustration.

## Backlog Watch

| Item | Age | Type | Staleness | Why It Matters |
|------|-----|------|-----------|----------------|
| **#3741** (Provider-hosted web search) | 58 days | Feature (closed) | Closed today — resolved | Was the oldest open feature request; now merged. |
| **#4506** (MCP idle timeout auto-kill) | 13 days | Enhancement (open, conflict) | Updated 2026-07-07 | No merging progress; has conflict label. Resource leaks persist. |
| **#4013** (Stream stall) | 43 days | Bug (closed 2026-07-07) | Resolved | User waited 43 days for resolution; high latency on user-reported issues. |
| **#4841** (Matrix device untrusted) | 1 day | Bug (open) | New | No fix or maintainer response yet. Could persist for weeks if not prioritized. |

**Items needing maintainer attention:**
- **#4841 (Matrix trust)** — No comments, no PR. The Matrix integration is important for federated deployments; a fix requires cross-signing support.
- **#4506 (MCP idle timeout)** — Conflict label suggests design disagreements. Needs resolution to prevent zombie process accumulation.
- **#4611 (DNS rebinding)** — While closed, the underlying fix should be audited for completeness; SSRF is a high-severity surface.

**Overdue review:** Three security issues (#4825-#4827) have zero maintainer comments. A fast response (preliminary analysis or acknowledgment) is critical within 48 hours given their severity.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

# Hermes Agent Project Digest — 2026-07-08

## Today's Overview

Hermes Agent v0.18.1 was released yesterday, rolling up approximately 660 PRs merged since v0.18.0 (July 1) into a stable patch release for downstream consumers. Today's activity is very high: 50 issues and 50 PRs were updated in the last 24 hours, with 18 issues closed and 13 PRs merged. The project shows signs of a focused stabilization phase, with numerous bug fixes addressing MCP subprocess leaks, config cache staleness, desktop GUI/backend contract issues, and platform-specific problems on Windows. A significant number of duplicate bug reports (at least five in the latest issue set) suggest ongoing user confusion around known issues, though maintainer responsiveness appears strong given the volume of recently-closed items.

## Releases

**v2026.7.7 — Hermes Agent v0.18.1** (Released July 7, 2026)

This is a **patch release** that rolls up ~660 PRs merged since v0.18.0 (July 1). The release bundles bug fixes, hardening work, and in-progress feature work into a stable tagged release for downstream consumers including Docker images, hosted deployments, and PyPI.

- **Scope:** Bug fixes, hardening, and stabilization — no breaking changes documented
- **Migration notes:** Not explicitly stated, but given the patch-level increment, no migration steps should be required
- **Available on:** Docker images, hosted deployments, PyPI

## Project Progress

Today saw 13 PRs merged or closed, signaling continued momentum on critical fixes:

**Merged/Closed PR highlights:**
- [#60594](https://github.com/NousResearch/hermes-agent/pull/60594) — Fixed deprecated `datetime.utcnow()` calls in BlueBubbles iMessage adapter (Python 3.14 compatibility)
- [#60547](https://github.com/NousResearch/hermes-agent/pull/60547) — Approval gate fix: cron_mode deny now properly evaluated before session approval, preventing standing grants from overriding deny rules
- [#60611](https://github.com/NousResearch/hermes-agent/pull/60611) — Cron environment variable cleanup: `HERMES_CRON_SESSION` env var now properly unset after job completion to prevent leakage into interactive sessions
- [#60612](https://github.com/NousResearch/hermes-agent/pull/60612) — Gateway shutdown drain now includes in-flight cron jobs, preventing orphaned workers during `/update` shutdown
- [#60610](https://github.com/NousResearch/hermes-agent/pull/60610) — Terminal tool now guards `killpg` against own process group to prevent gateway self-SIGTERM crashes

## Community Hot Topics

**Most Active Issues:**

1. **[#19986](https://github.com/NousResearch/hermes-agent/issues/19986)** — "Make non-core bundled skills optional" (9 comments, 3 👍)
   - **Analysis:** The most active open issue proposes reducing the default installation footprint by making bundled skills optional. This signals user demand for a more modular, minimal install — likely driven by deployment in resource-constrained environments or CI/CD pipelines.

2. **[#55790](https://github.com/NousResearch/hermes-agent/issues/55790)** — "Stale credential pool entries cause removed providers to persist in model picker" (6 comments)
   - **Analysis:** A cross-component bug spanning Desktop UI and auth systems. The persistence of removed providers in the model picker suggests a fundamental credential lifecycle management gap. Users removing API keys expect immediate effect; the stale pool undermines trust in the UI's accuracy.

3. **[#60584](https://github.com/NousResearch/hermes-agent/issues/60584)** — "hermes chat -q clears screen + scrollback, destroying the response" (3 comments, quickly closed)
   - **Analysis:** A critical UX bug in one-shot mode — the tool literally destroys its own output. The rapid closure suggests maintainers prioritized this fix, though the severity (user cannot see the agent's response at all) explains the urgency.

**Most Active PRs (by engagement, though comment counts are undefined in data):** The PRs with notable progress or discussion include:
- [#60146](https://github.com/NousResearch/hermes-agent/pull/60146) — Discord `/branch` and `/merge` thread management, a significant new feature for Discord gateway users
- [#60417](https://github.com/NousResearch/hermes-agent/pull/60417) — Behavioral analysis `/behavior` command with 5-axis scoring, a novel analytics feature

## Bugs & Stability

**Critical (P1) bugs reported today:**
- [#60525](https://github.com/NousResearch/hermes-agent/issues/60525) — `write_file()` commits to disk before its own JSON/YAML/TOML syntax check, writing invalid content and reporting success. **Fix PR:** [#60618](https://github.com/NousResearch/hermes-agent/pull/60618) already submitted to gate the check before disk write.
- [#60610](https://github.com/NousResearch/hermes-agent/pull/60610) — Terminal tool's `killpg` can kill the gateway process itself. **Fix PR** submitted same-day.

**High (P2) bugs reported today:**
- [#60543](https://github.com/NousResearch/hermes-agent/issues/60543) — `/steer` race condition: out-of-band messages lost between tool batch drain and next API call (risk-session-state)
- [#60597](https://github.com/NousResearch/hermes-agent/issues/60597) — UI wrapper crash on Gemini provider: "Attempted to access streaming response content without having called read()" (needs-repro)
- [#60603](https://github.com/NousResearch/hermes-agent/issues/60603) — `/compress` command returns "not a quick/plugin/skill command: compress" in Desktop app
- [#60615](https://github.com/NousResearch/hermes-agent/issues/60615) — Honcho plugin ignores host-block config values for cadence and injection frequency
- [#60551](https://github.com/NousResearch/hermes-agent/issues/60551) — config.yaml write guard prevents `hermes config set` from writing list keys as scalars
- [#50404](https://github.com/NousResearch/hermes-agent/issues/50404) — Discord config not profile-isolated (desktop GUI changes affect all profiles)

**Medium (P3) bugs reported today:**
- [#60572](https://github.com/NousResearch/hermes-agent/issues/60572) — Dashboard spawns unnecessary MCP server processes at startup (fix PR [#60602](https://github.com/NousResearch/hermes-agent/pull/60602) submitted)
- [#60541](https://github.com/NousResearch/hermes-agent/issues/60541) — Desktop cold boot restores stale pinned session instead of current session
- [#60542](https://github.com/NousResearch/hermes-agent/issues/60542) — Desktop contract check only warns when backend is older (not GUI older)
- [#60536](https://github.com/NousResearch/hermes-agent/issues/60536) — Unspecified Windows/Desktop bug (needs-repro, paste.rs logs provided)
- [#60596](https://github.com/NousResearch/hermes-agent/issues/60596) — Windows Desktop chat UI alignment: messages centered instead of split left-right (closed as likely duplicate)

**Notable stability concern:** Multiple duplicate bug reports about MCP subprocess leaks ([#59349](https://github.com/NousResearch/hermes-agent/issues/59349), [#57228](https://github.com/NousResearch/hermes-agent/issues/57228), [#57355](https://github.com/NousResearch/hermes-agent/issues/57355)) — closed, suggesting these have known fixes in the pipeline.

## Feature Requests & Roadmap Signals

**Notable feature requests in today's data:**

1. **[#19986](https://github.com/NousResearch/hermes-agent/issues/19986)** — **Make non-core bundled skills optional** (P3, feature)
   - Likelihood for v0.19: Medium-High. Strong community support (5 weeks of discussion, 3 reactions). Aligns with containerization and CI/CD use cases where small images matter.

2. **[#60146](https://github.com/NousResearch/hermes-agent/pull/60146)** — **Discord `/branch` and `/merge` commands** for thread management
   - Likelihood for v0.19: Medium. The PR is open and actively being discussed; would significantly improve Discord gateway UX.

3. **[#60417](https://github.com/NousResearch/hermes-agent/pull/60417)** — **Behavioral analysis command** (`/behavior`) with 5-axis scoring
   - Likelihood for v0.19: Medium. Novel feature, potentially still in design phase.

4. **[#46524](https://github.com/NousResearch/hermes-agent/issues/46524)** — **Three new development skills** (brainstorming, verification-before-completion, finishing-a-development-branch)
   - Likelihood: Low-Medium. PR is 23 days old with no recent maintainer engagement.

5. **[#3335](https://github.com/NousResearch/hermes-agent/issues/3335)** — **Zulip integration and messaging support** (opened March 27, 2026 — over 3 months old)
   - Likelihood: Low. The PR precedes the current platform plugin system and needs significant rework. May be deprioritized.

**Prediction:** The next minor release (v0.19.0) will likely include the optional skills system and the Discord branch/merge feature, alongside accumulated stability fixes.

## User Feedback Summary

**Pain points expressed today:**

1. **Credential management confusion** — Users report that removed providers persist in model pickers ([#55790](https://github.com/NousResearch/hermes-agent/issues/55790)), config changes don't take effect until restart ([#18946](https://github.com/NousResearch/hermes-agent/issues/18946), [#50199](https://github.com/NousResearch/hermes-agent/issues/50199)), and Discord config is not profile-isolated ([#50404](https://github.com/NousResearch/hermes-agent/issues/50404)). This suggests a systemic trust issue: users cannot reliably predict which settings are live.

2. **Windows-specific frustration** — Multiple Windows bugs reported today: chat UI alignment ([#60596](https://github.com/NousResearch/hermes-agent/issues/60596)), WSL bash stub interference ([#60617](https://github.com/NousResearch/hermes-agent/pull/60617)), WhatsApp bridge console window ([#60605](https://github.com/NousResearch/hermes-agent/pull/60605)). The Windows experience appears significantly behind macOS/Linux.

3. **One-shot mode unusable** — Bug [#60584](https://github.com/NousResearch/hermes-agent/issues/60584) (screen clearing after `hermes chat -q`) made the core one-shot workflow non-functional. Rapid closure suggests this was treated as blocking.

4. **MCP tool reliability** — Multiple duplicate MCP subprocess leak reports indicate users are hitting `EMFILE` errors in production deployments. The fact that three separate reports exist suggests this is a widespread pain point.

**Satisfaction signals:** The high volume of issue reporting (50 in 24h) indicates an active, engaged user base that expects quality. The rapid triage and closure of many issues suggests maintainers are keeping up.

## Backlog Watch

**Long-unanswered important items needing maintainer attention:**

1. **[#19986](https://github.com/NousResearch/hermes-agent/issues/19986)** — Optional bundled skills (5 weeks old, 9 comments, 3 reactions). No maintainer response visible in activity. This is the highest-engagement open issue.

2. **[#3335](https://github.com/NousResearch/hermes-agent/pull/3335)** — Zulip integration (3.5 months old, needs rework for current plugin system). Likely abandoned or waiting for contributor bandwidth.

3. **[#42248](https://github.com/NousResearch/hermes-agent/issues/42248)** — Kanban workers deadlock with custom local model providers (4 weeks old). Uses `__psynch_cvwait` which signals a threading/process management issue — potentially affecting many users with local model deployments.

4. **[#45454](https://github.com/NousResearch/hermes-agent/issues/45454)** — Gateway crashes with `SystemExit: 75 (EX_TEMPFAIL)` on macOS (3.5 weeks old, persists across versions v0.14.0–v0.16.0). No fix PR or maintainer acknowledgment visible — concerning for macOS users.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

# PicoClaw Project Digest — 2026-07-08

## Today's Overview

PicoClaw saw moderate activity in the past 24 hours, with 7 issues updated (5 open, 2 closed) and 4 pull requests updated (3 open, 1 merged/closed). No new releases were published, indicating a stability or maintenance phase. Bug reporting remains active, with two freshly filed issues around rate limiting and OAuth integration, while a significant cleanup PR for the DeltaChat integration was updated. The project's triage cadence appears healthy, though several older issues and a consolidation of related OAuth bug reports suggest a need for maintainer prioritization.

## Releases

No new releases were published in the last 24 hours. The latest available version remains v0.3.1 (referenced in Issue #3232). Users on v0.2.8 and v0.2.9 continue to report bugs, indicating no patch releases have been cut recently for the reported issues.

## Project Progress

One pull request was closed/merged in the last 24 hours:

- **[PR #3157](https://github.com/sipeed/picoclaw/pull/3157) (CLOSED)** — `feat: add Android ADB remote operations tool` by @danmobot. This merges an experimental Android Debug Bridge (ADB) backed tool enabling remote device operations: device listing, status inspection, screenshots, UI hierarchy summaries, tap, swipe, text input, key events, and wake. Importantly, the PR explicitly does not expose arbitrary shell execution, suggesting a security-conscious design. This expands PicoClaw's agentic capabilities into mobile device control.

Other open PRs saw updates but remain unmerged:

- **[PR #3233](https://github.com/sipeed/picoclaw/pull/3233) (OPEN)** — `Fix pr 3222 backward compat` by @yaotukeji. A follow-up fix addressing backward compatibility concerns from the larger DeltaChat refactor.
- **[PR #3222](https://github.com/sipeed/picoclaw/pull/3222) (OPEN)** — `refactor(deltachat): cleanup implementation, documentation -320LOC` by @trufae. A large cleanup (-320 lines) removing legacy features, dropping password-based email configuration in favor of JSON-RPC secrets, renaming `invite_link` to `join_invite_link` and adding `show_invite_link`, and referencing an official relay list instead of hardcoding.
- **[PR #3226](https://github.com/sipeed/picoclaw/pull/3226) (OPEN)** — `fix(tools): stop write_file from coaching destructive overwrite (#3150)` by @ACMYuechen. Addresses a safety issue where the `write_file` tool's overwrite guard was coaching models toward destructive replacement of `memory/MEMORY.md`, rather than suggesting proper update patterns.

## Community Hot Topics

- **[Issue #3093](https://github.com/sipeed/picoclaw/issues/3093) (CLOSED)** — `[Feature] I need SimpleX or tox` by @Damian-o2. 5 comments, 1 👍. This request for additional messaging protocol support (SimpleX, Wire, or Tox) was closed as stale, suggesting maintainers are not prioritizing new protocol integrations.

- **[Issue #3153](https://github.com/sipeed/picoclaw/issues/3153) (OPEN)** — `[BUG] Volcengine Doubao Seed tool calls occasionally leak as <seed:tool_call> text` by @ms8great. 3 comments. A reliability concern where tool calls from `doubao-seed-2.0-pro` are rendered as raw XML text rather than executed. This points to a provider compatibility gap affecting real agent workflows.

- **[Issue #3232](https://github.com/sipeed/picoclaw/issues/3232) (OPEN)** — `[BUG] Rate limiting doesn't work if no fallback models is configured` by @VictorSu000. 0 comments (fresh). A new, high-signal bug: rate limiting (RPM configuration) is silently broken when no fallback models are set. This affects users who configure a single primary model—a common deployment pattern.

- **[Issue #3195](https://github.com/sipeed/picoclaw/issues/3195) (OPEN)** — `[BUG] OpenAI GPT does not work on NanoKVM with default config` by @rtadams89. 2 comments. A platform-specific breakage: the new PicoClaw-on-NanoKVM feature (NanoKVM 2.4.0) fails with `gpt-5.4` out of the box. This may deter edge device adopters.

## Bugs & Stability

| Severity | Issue | Summary | Status | Fix PR? |
|----------|-------|---------|--------|---------|
| **Critical** | [#3232](https://github.com/sipeed/picoclaw/issues/3232) | Rate limiting silently broken without fallback models | OPEN, fresh | None |
| **High** | [#3153](https://github.com/sipeed/picoclaw/issues/3153) | Doubao Seed tool calls leak as raw XML text | OPEN, stale | None |
| **High** | [#3195](https://github.com/sipeed/picoclaw/issues/3195) | OpenAI GPT fails on NanoKVM with default config | OPEN, stale | None |
| **Medium** | [#3197](https://github.com/sipeed/picoclaw/issues/3197) & [#3196](https://github.com/sipeed/picoclaw/issues/3196) | Codex and Antygravity OAuth login not working (duplicate reports) | OPEN, stale | None |
| **Medium** | [#3159](https://github.com/sipeed/picoclaw/issues/3159) (CLOSED) | Task repetition bug: second query re-executes first task | CLOSED, stale | None |

The rate limiting bug (#3232) is the most concerning new finding—it undermines a core reliability mechanism. The duplicate OAuth reports (#3197, #3196) from the same reporter suggest a consistent authentication failure that may be a regression introduced in v0.2.9. No fix PRs are yet linked to any of these open bugs.

## Feature Requests & Roadmap Signals

- **[PR #3157](https://github.com/sipeed/picoclaw/pull/3157) (MERGED)** — Android ADB remote tool. This is a clear roadmap signal: mobile device control is now a supported agent capability. Future releases may extend this with additional device types or richer primitives.

- **[Issue #3093](https://github.com/sipeed/picoclaw/issues/3093) (CLOSED)** — SimpleX/Tox gateway request. Closed as stale, indicating maintainers are not prioritizing new communication protocol support. Users interested in this feature may need to contribute it themselves.

- **[PR #3222](https://github.com/sipeed/picoclaw/pull/3222) (OPEN)** — The DeltaChat cleanup is substantial (-320 LOC) and includes breaking changes in configuration (dropping password-based email, renaming invite link endpoints). Once merged, this is likely to land in the next minor version (v0.4.x) and will require migration attention from DeltaChat users.

- **Prediction for next version**: The Android ADB tool (#3157) and the `write_file` safety fix (#3226) are strong candidates for inclusion in a v0.3.2 patch. The DeltaChat refactor (#3222) plus its backward compat follow-up (#3233) are more likely for v0.4.0 given their breaking scope.

## User Feedback Summary

- **Real pain points**: Multiple users report the tool "not working" out of the box on specific hardware (NanoKVM) or with specific providers (Doubao Seed, OpenAI GPT-5.4). This suggests documentation or default configuration gaps for new users.
- **Authentication friction**: Two nearly identical reports about OAuth login failures with Codex and Antygravity indicate a likely regression in authentication flow.
- **Task repetition**: A user (Issue #3159) reported the agent re-executing previous tasks when given sequential queries, disrupting multi-turn workflows.
- **Rate limiting surprise**: A v0.3.1 user discovered that RPM configuration is entirely ineffective without fallback models, which is counterintuitive.
- **Use case diversity**: Users are actively deploying PicoClaw on edge hardware (NanoKVM), inside Docker containers, and on Debian 13, indicating broadening adoption.

## Backlog Watch

The following issues and PRs have been open for extended periods without maintainer response or resolution:

- **[Issue #3153](https://github.com/sipeed/picoclaw/issues/3153) (OPEN, stale)** — Doubao Seed tool call leak. Filed 2026-06-22, last updated 2026-07-07. No maintainer assignment or triage label. Affects real agent reliability.
- **[Issue #3195](https://github.com/sipeed/picoclaw/issues/3195) (OPEN, stale)** — NanoKVM OpenAI failure. Filed 2026-06-30, last updated 2026-07-07. A high-visibility issue for a touted new feature.
- **[Issues #3196 & #3197](https://github.com/sipeed/picoclaw/issues/3196) (OPEN, stale)** — Duplicate OAuth login bugs. Both filed 2026-06-30, same reporter. No maintainer comment or resolution.
- **[PR #3222](https://github.com/sipeed/picoclaw/pull/3222) (OPEN)** — DeltaChat refactor. Filed 2026-07-03, updated 2026-07-07. Still pending review. The companion backward compat PR (#3233) suggests the original PR may have introduced regressions.

These items merit maintainer attention to prevent community frustration and signal project responsiveness.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

# NanoClaw Project Digest — 2026-07-08

## Today's Overview

NanoClaw shows **high activity** today with 23 pull requests updated in the last 24 hours, though 9 of those are documentation-focused PRs that were merged or closed. One open security issue (#2970) was filed yesterday and remains unaddressed. The project is in a **documentation refresh cycle** — four docs PRs (#2961–#2964) were merged to sync stale architecture, schema, and SDK documentation against the current `v2.1.38` codebase. There are **no new releases** today.

## Releases

**None** — no new releases were published in the last 24 hours. The last verified codebase snapshot is `v2.1.38` (commit `08a1ac9`).

## Project Progress

**Merged/Closed PRs (9 items):**
- [#2965](https://github.com/nanocoai/nanoclaw/pull/2965) — **Fix: rate limit event handling** — `ClaudeProvider.translateEvents` now correctly matches rate-limit events as a top-level SDK message type (upgraded from `@anthropic-ai/claude-agent-sdk` 0.2.x to 0.3.x)
- [#2964](https://github.com/nanocoai/nanoclaw/pull/2964) — **Docs: SDK deep-dive rewrite** — re-verified and updated `SDK_DEEP_DIVE.md` against the actual `0.3.197` SDK package
- [#2963](https://github.com/nanocoai/nanoclaw/pull/2963) — **Docs: architecture rewrite** — stale sections of `docs/architecture.md` and `agent-runner-details.md` rewritten to match current code
- [#2962](https://github.com/nanocoai/nanoclaw/pull/2962) — **Docs: DB schema sync** — `docs/db-central.md` and entity docs updated through migrations 010–018
- [#2961](https://github.com/nanocoai/nanoclaw/pull/2961) — **Docs: stale claims cleanup** — README, CONTRIBUTING, CLAUDE.md corrected (shipped skills removed from solicitation lists, signal/Matrix references cleaned up)
- [#2922](https://github.com/nanocoai/nanoclaw/pull/2922) — **Fix: Discord forwarded messages** — unwrapped forwarded-message snapshots so agents see actual forwarded content
- [#2919](https://github.com/nanocoai/nanoclaw/pull/2919) — **Test PR** — closed without merge (labelled as test)
- [#2804](https://github.com/nanocoai/nanoclaw/pull/2804) — **Fix: CLI messaging-groups create** — resolved `NOT NULL constraint failed` bug that made the create command completely non-functional
- [#1598](https://github.com/nanocoai/nanoclaw/pull/1598) — **Feat: add-remote-storage skill** — WebDAV/S3 via rclone + systemd with `ncl groups config add-mount/remove-mount` (still open but heavily updated)

**Key advancements:** Documentation staleness sweep completed (4 PRs); critical CLI bug fixed; Discord message forwarding patched; rate-limit event handling aligned with SDK 0.3.x.

## Community Hot Topics

**Most active discussions today (by updates):**

1. **[#2873](https://github.com/nanocoai/nanoclaw/pull/2873) — [OPEN] Fix: split pre-flight from credentials** (23 updates) — Long-running PR to refactor the skill update flow. The author is separating credential validation from code refresh, indicating a complex architectural need.
   - **Analysis:** Community investment in making the skill system more modular and less error-prone.

2. **[#2800](https://github.com/nanocoai/nanoclaw/pull/2800) — [OPEN] Fix: security - validate folder + restrict image-tag** (22 updates) — Addresses CWE-22 path traversal and image pinning in `ncl groups create/update`.
   - **Analysis:** Security-focused PR with strong maintainer engagement; community deeply concerned about injection vectors in the group creation flow.

3. **[#1598](https://github.com/nanocoai/nanoclaw/pull/1598) — [OPEN] Feat: add-remote-storage skill** (updates today) — WebDAV/S3 integration with rclone. Still open after 3 months, getting periodic updates.
   - **Analysis:** High demand for remote storage integration; this is a feature many self-hosters need.

## Bugs & Stability

**Critical:**
- [#2970](https://github.com/nanocoai/nanoclaw/issues/2970) — **Security: Local action forgery via unauthenticated forwarded gateway loopback webhook** *(New, opened 2026-07-07)* — The localhost-only webhook does not authenticate the sender before trusting forwarded gateway interaction events. **No fix PR exists yet.** This is a high-severity security vulnerability that could allow attackers to forge local actions.

**High:**
- [#2804](https://github.com/nanocoai/nanoclaw/pull/2804) — **CLI messaging-groups create broken** *(Merged)* — `NOT NULL constraint failed: messaging_groups.instance` made the entire create path dead. **Fixed and merged today.**

**Medium:**
- [#2966](https://github.com/nanocoai/nanoclaw/pull/2966) — **Agent runner: provider errors recorded as completed** *(Open, draft)* — Provider errors inside a consumed batch are incorrectly recorded as `completed` instead of `failed`. Coupled with missing failed-ack mirroring. Discussion ongoing.
- [#2922](https://github.com/nanocoai/nanoclaw/pull/2922) — **Discord: forwarded messages not visible to agents** *(Merged)* — Unwrapping issue where agents saw empty forwarded content. **Fixed.**

**Low:**
- [#2965](https://github.com/nanocoai/nanoclaw/pull/2965) — **Rate limit events not being recognized** *(Merged)* — SDK upgrade broke event type matching. **Fixed.**

## Feature Requests & Roadmap Signals

**Strong signals for next release:**
- **Agent Templates** — [#2909](https://github.com/nanocoai/nanoclaw/pull/2909) (open) adds a setup wizard flow with first-agent stamping from templates. Part 2 of 2 (template loader landed in #2890). Likely to ship soon.
- **Structured Skill Format (SSF) Migration** — [#2958](https://github.com/nanocoai/nanoclaw/pull/2958) (open) rebuilds the `add-teams` skill on the SSF base, replacing the 7-step Azure portal walk with a single `teams login` + `teams app create --json` flow. Signals a broader SSF adoption push.
- **Remote Storage** — [#1598](https://github.com/nanocoai/nanoclaw/pull/1598) (open, 3 months old) for WebDAV/S3. Continued activity suggests it may finally merge.

**Prediction:** The next release (v2.2.0?) will likely include the agent template wizard (#2909), SSF-based team setup (#2958), and potentially the supply-chain gate fix (#2973).

## User Feedback Summary

**Pain points:**
- **Approval race conditions** — [#2974](https://github.com/nanocoai/nanoclaw/pull/2974) identifies that pending approvals can be double-executed; the PR adds atomic claim semantics.
- **CLI usability** — The `messaging-groups create` command being dead (#2804) was a significant regression that affected all users of the CLI.
- **Forwarded message visibility** — Discord agents couldn't see forwarded content (#2922), impacting inter-agent communication.
- **Setup wizard UX friction** — [#2972](https://github.com/nanocoai/nanoclaw/pull/2972) addresses pairing card UX, "either/or" selectors, and spinner animations during skill steps — suggesting users found the wizard confusing or slow.

**Satisfaction signals:**
- Heavy community engagement on documentation updates (4 merged docs PRs in one day) indicates users are actively reading and relying on the docs.
- The volume of skill contributions (#2969 add-rtk fix, #2971 ncc utility skill, #2958 add-teams) suggests the skill system is healthy and attracting contributors.

## Backlog Watch

**Needs maintainer attention:**
- [#2970](https://github.com/nanocoai/nanoclaw/issues/2970) — **Security vulnerability: unauthenticated webhook** *(1 day old, 0 comments)* — No fix PR. This should be triaged ASAP as a security issue.
- [#1598](https://github.com/nanocoai/nanoclaw/pull/1598) — **add-remote-storage skill** *(3 months old, open)* — Repeated updates but no merge. Contributors may be losing momentum.
- [#2873](https://github.com/nanocoai/nanoclaw/pull/2873) — **Skill pre-flight refactor** *(11 days old, open)* — Heavy discussion but no resolution. May need architectural decision.
- [#2800](https://github.com/nanocoai/nanoclaw/pull/2800) — **Folder path traversal + image pinning** *(21 days old, open)* — Security fix still unmerged despite being flagged as CWE-22.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

# IronClaw Project Digest — 2026-07-08

## Today's Overview

Project activity remains high, with 32 issues and 50 PRs updated in the last 24 hours, indicating sustained development velocity. The team is making significant progress on code quality improvements, with multiple PRs focused on converting sparse struct literals to fluent default-backed setters across the codebase. Six PRs were merged or closed today, and 10 issues were resolved. The daily failure taxonomy report shows PinchBench integration tests continue to be a stability concern, while a Slack pairing flake has been identified and a fix PR is in flight. No new releases were published today.

## Releases

No new releases were published today.

## Project Progress

Six PRs were merged or closed today:
- **#5694** [bug_bash_P2] — Fixed `clientActionId()` throwing on insecure origins (plain HTTP), which was breaking all mutating v2 requests
- **#5696** [bug_bash_P2] — Hid unsupported operator-config fields (Embeddings, Temperature) from WebUI v2 Inference settings
- **#5698** [bug_bash_P3] — Surfaced tool permission save failures in WebUI v2 Settings Tools tab
- **#5554** [bug_bash_P2] — Fixed mobile chat layout horizontal overflow
- **#3083** [bug_bash_P2] — Fixed duplicate user creation due to missing loading state and submission debounce
- **#5466** — Closed: Parallel same-tenant turn-runs vs FilesystemTurnStateStore CAS/libsql backend (~10% failure)

Major ongoing efforts in the open PR queue include:
- **PR #5280** (Trace Commons) — Instance-wide enrollment, per-user profiles, and trace inspection (XL, core)
- **PR #5525** & **PR #5499** — Private tool installations for SSO users and WASM tool install from zip (part 1 and 2 of #5459)
- **PR #5659** — Critical security fix narrowing three tool-disclosure leak vectors (production change)
- **PR #5742** — Wiring memory prompt-context source with untrusted-memory envelope (production change)
- **PR #5789** — Fix for Slack pairing-code TTL flake

## Community Hot Topics

- **#5702** `[bug_bash_P2] GitHub issue search and create capabilities fail with HTTP 403` — 4 comments. Users cannot interact with GitHub issues despite configured integration. This is a significant workflow blocker for power users relying on GitHub automation.

- **#5747** `[OPEN] Reborn: No way to unpair Slack on the built-in host-beta mount` — 2 comments. Once a Slack user is paired, there is no UI or command to disconnect. `/pair` refuses to issue a new code, and no disconnect action exists in WebUI.

- **#5701** `[OPEN] Activity panel hides tool details and does not update during active run` — 2 comments. The activity panel collapses tool calls into summary lines without details, and does not update in real-time during runs.

- **#5776** `[OPEN] Long-output prompt causes repeated model timeouts` — 1 comment. Extreme long-output prompts exceed request timeout, and the failure path degrades the error to a generic "invalid result", hiding the root cause.

## Bugs & Stability

### Critical / P2 Issues:
- **#5702** GitHub integration returns HTTP 403 — blocks issue search/create workflows
- **#5701** Activity panel hides tool details, no real-time updates during runs
- **#5708** Error banners display outside chat message stream, stacking as floating elements
- **#5776** Long-output prompts cause repeated model timeouts degraded to generic errors — user cannot identify the real issue
- **#5553** Approval notifications disappear instead of remaining in notification history — critical for automation approval workflows

### P3 Issues (Lower Severity):
- **#5704** Image preview becomes transparent while chat is active
- **#5705** Terminal icon in chat UI has no disable option
- **#5706** Sidebar shows raw thread ID when instance is lagging
- **#5557** Logs deep link requires opening twice to load selected conversation

### Flaky Tests:
- **#5787** `slack_pairing_redeem_rejects_expired_code` — paused tokio clock vs chrono wall-clock TTL race. **Fix PR #5789** is open.

### Regression/Stability Improvements:
- **#5788** Daily failure taxonomy (2026-07-08) reports 7 non-pass PinchBench tasks, mostly model-quality partials. The long-running `gws_memory_…` suite continues to be a focus area.
- **#5466** (closed) — Parallel turn-runs against shared FilesystemTurnStateStore had ~10% failure rate
- **#5467** (closed) — In-memory ApprovalRequestStore discard_pending diverged from filesystem behavior (missing tombstone)

## Feature Requests & Roadmap Signals

### In Review / In Development:
- **#5786** — Expose OpenRouter upstream provider on ToolCompletionResponse — users need visibility into which upstream provider OpenRouter routed to
- **#5770** — Improve Reborn tool permission selects with a custom dropdown (replacing native `<select>` for consistency)
- **#5768** — Reborn Projects page has incomplete i18n coverage (Chinese users see mixed English/Chinese)
- **#5762** — Performance: recover row-store materializer throughput after starvation fix

### Design System Progress:
- **PR #5563** — Design system tokens + /playground (by new contributor achalvs) — foundational work for AI-autonomous UI improvements
- **PR #5565** — Onboarding/NUX demo with intent handoff, OAuth entry, chat-first workspace — suggests upcoming user experience overhauls

### Subagent Architecture:
- **PR #5748** — Canonical subagent thread-harness design document
- **PR #5749** — CAS-guarded delete_if_version on RootFilesystem (primitive for subagent await-edge delivery)

## User Feedback Summary

Several recurring pain points are visible:

1. **Integration Configuration Gaps**: Users cannot complete basic GitHub issue workflows (#5702), cannot unpair Slack (#5747), and have no way to configure or disable UI elements like the terminal icon (#5705).

2. **Usability Regressions**: The activity panel (#5701) and notification system (#5553) both fail to provide real-time feedback, which undermines trust in automation workflows.

3. **Error Transparency**: Long-output prompts returning generic "invalid result" errors (#5776) and error banners floating outside the message stream (#5708) make it difficult for users to diagnose and recover from failures.

4. **Localization Gaps**: The Reborn Projects page shows mixed English/Chinese (#5768), indicating i18n is still incomplete for the Reborn UI.

5. **Performance Anxiety**: Sidebar showing raw thread IDs under load (#5706) and logs deep links requiring double-clicks (#5557) suggest users experience lag under normal conditions.

## Backlog Watch

These older issues remain open and may need maintainer attention:

- **#3535** (2026-05-12) `[bug_bash_P1] UI Timestamps are incorrect for conversations` — P1 severity, 2 months old, no recent activity. Timestamps not reflecting actual message receipt time.
- **#4338** (2026-06-02) `[bug_bash_P2] Disconnected state shows misleading execution driver error (MiniMax-M2.7)` — Users getting confusing error messages when disconnected during task execution.
- **#5419** (2026-06-29) `[bug_bash_P3] No option to rename an automation` — Auto-generated automation names can be too long or unclear, with no post-creation rename capability.
- **#4108** (2026-05-27) `Nightly E2E failed` — Automated failure report, last updated 2026-07-07, suggesting nightly CI has been unstable for over a month.
- **#3081** (2026-04-29) `[bug_bash_P2] Portfolio extension shows misleading "Configure" button when no configuration is needed` — Oldest open issue in the top-30 list (over 2 months).

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

Here is the **LobsterAI Project Digest** for **2026-07-08**.

---

### 1. Today's Overview
The project saw a **high burst of activity**, with **16 PRs** updated (14 merged/closed) and **9 issues** updated (5 closed) in the last 24 hours, signaling a focused maintenance and release sprint. A new version (**2026.7.7**) was shipped, primarily featuring UI redesigns for scheduled tasks and new provider integrations. Notably, **three critical security vulnerabilities** were reported today (issues #2286, #2287, #2288), marking a major shift in project risk posture. The community is also actively discussing agent configuration isolation, indicating a growing user base experimenting with multi-agent setups.

### 2. Releases
- **New Version**: **LobsterAI 2026.7.7** (Released: 2026-07-07)
- **What's Changed**:
    - **Scheduled Task UI**: Redesigned the task list card with status chips, toggle switches, search functionality, and optimistic UI feedback (renderer).
    - **Provider Login**: Added **xAI (Grok) OAuth** login support.
- **Migration Notes**: No breaking changes or specific migration notes were listed.

### 3. Project Progress
**16 PRs** were updated; **14 were merged or closed**. Key advancements include:
- **Cowork Stability** (#2292): Fixed steer follow-up routing and replaced temporary new-chat sessions with real started sessions, improving multi-turn reliability.
- **Email Skill Overhaul** (#2275): Added multi-account support for the built-in IMAP/SMTP skill, including account management UI, provider presets, and connectivity testing. Maintains backward compatibility with legacy single-account `.env` files.
- **Analytics Fixes** (#2245): Corrected usage event reporting for skills, IM settings, sidebar toggles, custom model edits, and scheduled tasks.
- **Stale Bug Fixing**: Merged 7 legacy bugfix PRs (originally from April 2026) addressing:
    - NIM group type mapping errors (#1419).
    - SQLite write performance (debounced batch writes, #1410).
    - Memory migration flags (#1415).
    - CronJob re-entrancy and ghost events (#1420).
- **Release Branch Merge** (#2291): Merged `release/2026.7.6` into `main`, bringing cumulative fixes for OpenClaw, MCP import, and provider settings.

### 4. Community Hot Topics
- **Agent Content Isolation** (Issue #2293 | [Link](https://github.com/netease-youdao/LobsterAI/issues/2293))
    - **Activity**: Created yesterday, 1 comment.
    - **Analysis**: A user reports that modifying the "About You" or `USER.md` for one Agent propagates changes to all other Agents. This reveals a high demand for **true agent isolation**, likely stemming from power users who want distinct personalities or system prompts for different workflow contexts.
- **Security Vulnerabilities** (Issues #2286, #2287, #2288 | [Link to #2286](https://github.com/netease-youdao/LobsterAI/issues/2286))
    - **Activity**: All created yesterday, 0 comments each.
    - **Analysis**: While no comments yet, these represent the highest-stakes community engagement today. The disclosure of three distinct attack vectors (local token proxy, arbitrary file exfiltration via NIM, and symlink following) suggests an external security audit or a dedicated researcher is investigating the project.

### 5. Bugs & Stability
Three **high-severity security bugs** were disclosed, all with **zero fix PRs currently linked**:
- **Severity: Critical**
    - **#2286**: **Unauthenticated local token proxy**. Any local process can replay the victim’s authenticated server API requests. This is a classic "local privilege escalation via API token leakage".
    - **#2287**: **Arbitrary host-local file exfiltration**. Assistant-generated absolute paths in the NIM media flow can exfiltrate arbitrary local files to a remote server.
    - **#2288**: **Symlink traversal in HTML preview server**. The localhost preview server follows in-root symlinks, allowing arbitrary file disclosure.
- **Analysis**: These bugs directly threaten user data confidentiality. The lack of immediate fix PRs is concerning, though the issues were filed just yesterday. The maintainers are likely evaluating the architectural impact before patching.

### 6. Feature Requests & Roadmap Signals
- **Agent Delegation & Collaboration** (PR #2285 | [Link](https://github.com/netease-youdao/LobsterAI/pull/2285)): A new PR (still open) introduces "delegated subagent collaboration," allowing users to define which Agents can delegate tasks to others. This addresses the community’s need for agent orchestration.
- **Prediction for Next Version**: Based on the open PR (#2285) and the email skill overhaul, the next release will likely focus on **multi-agent workflows** (delegation subagents) and **enhanced skill management** (multi-account email). The security issues (##2286-2288) will likely force a hotfix release to patch the local token proxy and file handling flows.

### 7. User Feedback Summary
- **Pain Points**:
    - **Agent isolation issues** (Issue #2293): "Just changed one agent's profile and all others synced" – users want independent agent configurations.
    - **UI localization** (Closed #1416): English text in the "Current Plan" card overlaps with numbers due to missing responsive layout.
    - **Task UI overflow** (Closed #1413): When many skills are added to the input bar, the UI becomes unusable.
- **Satisfaction Indicators**:
    - **High engagement**: 14 PRs merged in 24 hours suggests users see active improvement.
    - **Complex feature usage**: Users are filing issues about agent profiles, NIM integration, and scheduled tasks, indicating a power user base that relies on advanced features.

### 8. Backlog Watch
- **Dependency Update Stagnation** (PR #1277 | [Link](https://github.com/netease-youdao/LobsterAI/pull/1277)):
    - **Status**: **Open for 97 days** (since April 2, 2026).
    - **Risk**: This PR bumps `electron` from 40.2.1 to 43.0.0 and `electron-builder`. **Major version gap (40 to 43)** implies substantial security patches, API deprecations, and performance improvements are being left on the table. This is a growing technical debt that could block future features or cause breakage in CI/CD pipelines.
- **Recommendation**: This PR should be reviewed and merged (or a decision documented) soon, especially given the new security concerns found today which may be mitigated by Electron’s sandbox enhancements in newer versions.

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyagi">TinyAGI/tinyagi</a></summary>

# TinyClaw Project Digest — 2026-07-08

## Today's Overview
TinyClaw (TinyAGI) saw no project activity beyond incoming issue reports in the last 24 hours. No new releases, no pull requests were opened, merged, or closed. The project received **9 new security-focused issues**, all filed by researcher **YLChen-007**, all in open state with zero comments and no maintainer response yet. The pattern suggests a coordinated security audit disclosure, rather than organic community bug reports. The lack of any PR activity or maintainer engagement on these critical issues is a significant concern for project health.

## Releases
**None.** No new releases were published in the last 24 hours or in recent history visible in the data.

## Project Progress
**No pull requests were merged or closed today.** There is no evidence of feature development, bugfixes, or code changes occurring in the past day.

## Community Hot Topics
All 9 open issues today are **security advisories** filed by the same researcher. None have comments or reactions yet. The most impactful ones include:

- **[#294 — Unauthenticated control-plane routes allow system prompt overwrite and daemon restart](https://github.com/TinyAGI/tinyagi/issues/294)** — Describes exposure of privileged HTTP routes without authentication, enabling remote control of core agent behavior.
- **[#293 — Path traversal via agent ID escapes workspace root](https://github.com/TinyAGI/tinyagi/issues/293)** — Allows unauthenticated file access outside sandbox via crafted `agent.id = ".."`.
- **[#292 — Administrative API allows persistent settings and prompt modification](https://github.com/TinyAGI/tinyagi/issues/292)** — No auth on `PUT /api/settings` and `POST /api/message`.
- **[#291 — Anthropic adapter disables dangerous-tool confirmation](https://github.com/TinyAGI/tinyagi/issues/291)** — `--dangerously-skip-permissions` flag unconditionally enabled.
- **[#290 — Terminal escape injection allows operator log spoofing](https://github.com/TinyAGI/tinyagi/issues/290)** — Attacker-controlled `message` content injected into terminal logs.
- **[#289 — Arbitrary local file exfiltration via outbound channel attachments](https://github.com/TinyAGI/tinyagi/issues/289)** — Unauthenticated file path submission in `files[]` parameter.
- **[#288 — Unauthenticated local control plane leaks live events and allows settings modification](https://github.com/TinyAGI/tinyagi/issues/288)** — Localhost REST + SSE control plane without auth.
- **[#287 — Pairing management API allows arbitrary approval of pending channel senders](https://github.com/TinyAGI/tinyagi/issues/287)** — No auth on pairing approval endpoints.
- **[#286 — Local control API allows persistent settings mutation, prompt overwrite, event stream access](https://github.com/TinyAGI/tinyagi/issues/286)** — Consolidated report of missing auth boundaries.

**Underlying need:** The community (or this researcher) is signaling that TinyAGI currently offers **no authentication layer on its control-plane API**, exposing any deployment — even local-only — to complete compromise. Urgent need for **mandatory authentication middleware** and **input validation** before any production use.

## Bugs & Stability
All 9 reports are **Critical** severity. No fix PRs exist yet. The core pattern across all issues:

- **Severity: CRITICAL** — Unauthenticated remote code execution / data exfiltration / privilege escalation potential.
- **Severity: CRITICAL** — Path traversal enabling arbitrary file read.
- **Severity: HIGH** — Terminal injection enabling operator deception.
- **Severity: CRITICAL** — Unauthenticated permanent configuration changes.
- **Severity: HIGH** — Anthropic tool-safety bypass.

No crashes, runtime regressions, or memory issues were reported — only security design flaws.

## Feature Requests & Roadmap Signals
No feature requests were filed today. The data is entirely composed of security vulnerability disclosures. There is no signal about desired new features from the community.

## User Feedback Summary
No user feedback or satisfaction data exists in today's activity. The entire issue set comes from a single security researcher, likely performing a systematic audit rather than reporting user experience issues. This absence of typical user feedback (bugs, complaints, praise) suggests either low community engagement or that the audit disclosures are pre-coordinated prior to any public disclosure.

## Backlog Watch
All 9 issues are **unanswered by maintainers** for less than 24 hours, so they are not yet in "backlog" status. However, the **complete lack of maintainer response** on any of the 9 critical issues is alarming and should be monitored closely. If no response appears in the next 48 hours, it would indicate a serious project maintenance risk. No older unanswered issues or PRs were present in today's data.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

# CoPaw Project Digest — 2026-07-08

## Today's Overview

CoPaw (formerly QwenPaw) shows high development velocity with **38 PRs** and **16 Issues** updated in the last 24 hours, signaling active pre-release stabilization for **v2.0.0-beta.3** which shipped today. The project released 1 new version—**v2.0.0-beta.3**—featuring rate-limit enhancements and a CI fix for macOS. Activity is dominated by bug fixes, security hardening (sandbox ACL pollution, `find -delete` bypass), and community feature contributions including 3 first-time contributor PRs. The open issue count (12 active) is well-managed relative to PR throughput, though several high-severity stability bugs remain open. The project maintains dual-track stability releases (v1.1.12.post3 verified and closed today) alongside the beta track.

## Releases

**v2.0.0-beta.3** (released 2026-07-07)

**Key Changes:**
- **Auth/Rate Limiting:** Added multi-dimensional rate-limit protection (`feat(auth): enhance rate limiting with multi-dimensional protection`)
- **CI/CD:** Fixed empty `extra_flags` shell expansion issue on macOS bash 3.2
- **Installation verification** completed internally (GitHub Actions bot tracked pass criteria across platforms)

**Breaking Changes:** None reported in the changelog.

**Migration Notes:** Users upgrading from v1.x should consult the v2.0.0 pre-release tracker (#5273) for known regressions. No breaking data format changes in this beta.

## Project Progress

**Merged/Closed PRs Today (15 total):**

| PR | Description | Impact |
|---|---|---|
| #5837 | Version bump to 2.0.0b4 (chore) | Prepares next beta cycle |
| #5832 | Remove default session approval level mode (feat, console) | UX simplification |
| #5820 | Usage-aware auto search + backend-specific embeddings (feat, memory) | Memory system optimization |
| #5786 | Three bug fixes: model matching, channel edge cases (#5709, #5773, #5784) | Cross-provider model config fix |
| #5819 | v1.1.12.post3 installation verification (closed, passed) | Stable track release verified |
| #5585 | Matrix streaming mode like Discord (feat, channels) | Real-time UX for Matrix |
| #4693 | Plugin-registered custom channels with schema-driven UI (feat, plugin) | Long-running plugin API enhancement |

**Active Development Themes:**
- **Memory system** (#5820, #5669): Adding rerank capabilities and usage tracking for auto-memory
- **Desktop app** (#5187, #5814): Windows GUI automation (UIA + Tauri) and bundled Node runtime for ACP
- **Grep tool** (#5840, #5834): Two community contributions improving `grep_search` output formatting and pipe-separated literal support
- **CI hardening** (#5844): Real-behavior-proof gate for external PRs + spam gate integration

## Community Hot Topics

### Most Active Discussions

1. **#5401** (15 comments) — **[BUG] Console crash: large tool-use history fails to render**  
   *Root cause identified:* Backend converts `tool_use`/`tool_result` to `type: "data"` `DataContent` which frontend cannot render. No fix PR yet.  
   *Severity:* High — renders sessions with many tool calls unusable.

2. **#5273** (10 comments, 1 👍) — **[Tracking] v2.0.0 Pre-release Bug & Issue Tracker**  
   Centralized tracker for beta regressions. Maintainer-driven. Updated daily.

3. **#5479** (6 comments) — **[BUG] Large session files (>500KB) crash frontend**  
   Related to #5401 but distinct — pure file size issue vs. content type issue. Both are frontend rendering stability problems.

4. **#5797** (4 comments) — **[Feature] Timed task notification toggle**  
   User wants configurable popup notifications (currently either always-on or always-off). Polarizing feature — some users find popups annoying, others need them as reminders.

### Underlying Needs
- **Frontend resilience** is the dominant community concern — two separate issues (#5401, #5479) both involve frontend crashes rendering sessions with complex/large histories
- **User agency** in notification behavior (#5797) — the community is pushing back against developer-dictated UX defaults
- **Windows security** (#5829) — sandboxing feature bleeding into system directory permissions is causing real application crashes

## Bugs & Stability

### Critical/High Severity (Open)

| Issue | Summary | Severity | Has Fix PR? |
|---|---|---|---|
| **#5829** | Windows AppContainer sandbox ACE pollutes C:\, causes Hermes Desktop GPU crashes | **Critical** — system-level side effect | No |
| **#5401** | Console frontend white-screens on sessions with large tool-use history | **High** — prevents viewing tool-heavy sessions | No |
| **#5479** | Sessions >500KB crash frontend with “unexpected error” | **High** — progressive loading needed | No |
| **#5842** | `find -delete` bypasses out-of-workspace file deletion check | **High** — security bypass of file_guard | **PR #5843** (open, fixes this) |
| **#5835** | `/stop` lacks user-level isolation, cross-user cancellation in DingTalk DM | **High** — multi-tenant data/control leakage | No |
| **#5789** | Context compression crash when model output exceeds JSON Schema `maxLength` | **Medium** — recoverable with schema validation fix | No |
| **#5759** | Plan mode repeatedly re-reads same file | **Medium** — performance/API waste | No |
| **#5775** | Auto-memory interval never triggers (state lost across per-request rebuilds) | **Medium** — memory persistence broken | **Closed** (#5786 merged, but may need re-verification) |

### Recently Fixed (Closed)

| Issue | Fix |
|---|---|
| #5774 | Google Gemini channel error — fixed by #5786 |
| #5785 | Can't select hidden folders (dot-prefixed) in coding mode — fixed by #5785 (closed) |
| #5775 | Auto-memory interval trigger — marked closed, likely addressed by #5786 or #5820 |

### Notable Regressions
- #5774 (Gemini channel) was introduced in v1.1.12.post2 and fixed in v1.1.12.post23 (per #5786)

## Feature Requests & Roadmap Signals

### Strong Community Demand (Likely for Next Release)

1. **#5797 — Timed task notification toggle**  
   *Prediction:* High probability for v2.0.0-beta.4 or v2.0.0-rc.1 — the issue has clear consensus (“let users choose”) and is relatively low-implementation-effort.

2. **#5312 — Desktop: minimize to system tray on close**  
   *Prediction:* Medium probability — tracked for desktop (#5312 has no PR yet, but desktop improvements are active via #5187 and #5814).

3. **#5821 — Granular `rejects_media` capability (per media type)**  
   *Prediction:* Low-medium — the feature request is well-scoped but specialized. May land as a follow-up to media handling improvements.

### Implemented Today
- **Hidden folder selection** (#5785) — closed, user request fulfilled
- **Auto path detection in desktop chat** (#5836) — new PR merging, allows clickable local file paths
- **Per-agent avatars** (#5826) — new feature from first-time contributor

## User Feedback Summary

### Pain Points
- **"Frontend crashes on large sessions are blocking my workflow"** — Multiple users (#5401, #5479) report inability to view sessions with extensive tool use or large JSON files. This is the most impactful UX issue.
- **"Notifications are too binary: either always annoy or never remind"** — User @happieme (#5797) articulates frustration with binary notification behavior, asking for per-task granularity.
- **"Windows sandbox broke my other apps"** — User @96loveslife (#5829) reports Hermes Desktop (Electron app) crashes due to CoPaw's sandbox ACE propagation.
- **"Auto-memory doesn't actually save"** — User @howyoungchen (#5775) reports memory interval feature is inoperative due to architectural state management issue.

### Satisfaction Signals
- **First-time contributor activity is strong** — 3 PRs from new contributors (#5840, #5834, #5826) submitted in 24h, indicating good onboarding and clear contribution paths
- **Matrix streaming mode** (#5585) merged — community member @Morxi contributed Discord-like streaming for Matrix, a significant UX improvement
- **Plugin channel system** (#4693) merged after long development — plugin developers now have a proper API, reducing friction for custom channel integrations

## Backlog Watch

### Issues Needing Maintainer Attention

| Issue | Age | Problem |
|---|---|---|
| **#5273** (v2.0.0 tracker) | 21 days | Active and updated, but some listed sub-issues may lack individual triage. Consider splitting into component-specific trackers. |
| **#5401** (tool-use rendering crash) | 15 days | High severity, 15 comments, no fix PR. Likely needs frontend-backend coordination. |
| **#5312** (tray minimize) | 20 days | 2 comments, no maintainer response. Low effort but clear UX win. |
| **#5835** (cross-user cancellation) | 1 day | Very new, but security-critical — DingTalk multi-tenant isolation fix should be prioritized. |

### Stale PRs

| PR | Age | Status |
|---|---|---|
| **#5187** (Windows desktop UIA automation) | 24 days | Open, under active development — no recent comments from maintainers. Long-running feature branch. |
| **#5669** (qwen3-rerank for memory search) | 8 days | First-time contributor, "Under Review" label — awaiting maintainer review. |

### Recommendation
- **Immediate priority:** Merge #5843 (fix `find -delete` bypass, critical security hole) and triage #5829 (Windows sandbox pollution, system-level impact)
- **Short-term (this week):** Assign someone to #5401/#5479 frontend rendering crash — these are the most user-visible bugs
- **Medium-term:** Review #5669 (memory rerank) and #5187 (Windows automation) to avoid PR stagnation

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

Here is the ZeroClaw project digest for 2026-07-08.

---

## ZeroClaw Project Digest
**Date:** 2026-07-08

### 1. Today's Overview
The project is experiencing a highly active period with 50 PRs and 23 issues updated in the last 24 hours, indicating significant development momentum. A major focus is on stabilizing security and core runtime systems, with several high-priority (P1) bug fixes targeting memory leaks, authentication weaknesses, and bypassed policy filters. The community is highly engaged, driving a surge of bug reports and feature requests, particularly around the Web Dashboard UI and CLI onboarding. While no new releases were published, the volume of merged PRs (8) suggests a batch of fixes is likely ready for a patch release.

### 2. Releases
- **New Releases:** 0
- **Latest Release:** None

### 3. Project Progress
Eight PRs were merged or closed today, primarily focused on operational stability and configuration usability.

- **Security Patch:** **[CLOSED] #8782** (by wangmiao0668000666) patched a critical vulnerability by bumping `crossbeam-epoch` from 0.9.18 to 0.9.20 to clear the `RUSTSEC-2026-0204` advisory, fixing an invalid pointer dereference.
- **UI/Config Polish:** Three PRs by yaotukeji (via the `Fix 8757` chain: **[CLOSED] #8820**, **[CLOSED] #8822**, **[CLOSED] #8813**) addressed a configuration discoverability issue ([#8757](https://github.com/zeroclaw-labs/zeroclaw/issues/8757)), adding a "Global settings" entry to the Channels config section for easier access to root-level fields like `show_tool_calls`.
- **Task & Feature Completion:** **[CLOSED] #8815** (by maksyms) implemented the `skill_manage.create` action, allowing agents to save new skills as bundles rather than loose `.md` files.

### 4. Community Hot Topics
The most active discussions reveal deep user interest in security controls, operational reliability, and platform stability.

- **[RFC #7155](https://github.com/zeroclaw-labs/zeroclaw/issues/7155) (6 comments):** The proposal for a per-execution confirmation tier (`allow/ask/deny`) for high-risk shell commands is a key community topic. The underlying need is for granular safety mechanisms that allow automation without sacrificing manual oversight, mirroring features seen in competing tools like Claude Code.
- **[Bug #6699](https://github.com/zeroclaw-labs/zeroclaw/issues/6699) (9 comments):** The discovery that `tool_filter_groups` is a no-op for MCP tools is a high-severity concern for users relying on tool gating. The discussion highlights confusion around MCP tool naming conventions and a need for clearer runtime policy enforcement.
- **[Bug #8800](https://github.com/zeroclaw-labs/zeroclaw/issues/8800) (1 comment):** The Windows zombie port issue on Windows 11 (25H2) is a critical stability blocker for a significant user base. This mirrors a common frustration with daemonized applications on Windows, where process cleanup is inconsistent.
- **[Feature #8803](https://github.com/zeroclaw-labs/zeroclaw/issues/8803) (0 comments):** The request to collapse intermediate steps in the web dashboard chat transcript is a strong quality-of-life signal. Users want the UI to be as smart as the agent, keeping the transcript readable across long-running, multi-tool sessions.

### 5. Bugs & Stability
Several high-severity bugs were reported, with fix PRs already in progress.

- **S1 - Workflow Blocked:**
    - **[Bug #8794](https://github.com/zeroclaw-labs/zeroclaw/issues/8794):** Stopping the agent mid-work in the web dashboard erases tool calls and thinking from the context, breaking message coherence. **No fix PR open.**
- **S2 - Degraded Behavior:**
    - **[Bug #8797](https://github.com/zeroclaw-labs/zeroclaw/issues/8797):** The `bind-telegram` setup instructions reference an unknown configuration property (`bot-token` vs `bot_token`). **Fix PR #8823** is open to correct the error message.
    - **[Bug #8800](https://github.com/zeroclaw-labs/zeroclaw/issues/8800):** Windows: killed daemon leaves port bound (zombie `LISTENING/CLOSE_WAIT`), preventing new daemon startups. **No fix PR open.**
    - **[Bug #8810](https://github.com/zeroclaw-labs/zeroclaw/issues/8810):** The Telegram documentation example is found to be incorrect.
    - **[Bug #8792](https://github.com/zeroclaw-labs/zeroclaw/issues/8792):** The left sidebar in the web dashboard is missing a "Skills" navigation entry.
    - **[Bug #8787](https://github.com/zeroclaw-labs/zeroclaw/issues/8787):** Skill-registered tools bypass `allowed_tools`/`excluded_tools` policy. **Fix PR #8788** is open to apply the denylist.
    - **[Bug #8804](https://github.com/zeroclaw-labs/zeroclaw/issues/8804):** Skills prompt advertises a callable-tool set that doesn't match the registry (MCP missing, target-less elevation over-listed). **Fix PR #8805** is open.
- **Security Integrity:**
    - **[Bug #8642](https://github.com/zeroclaw-labs/zeroclaw/issues/8642):** MCP tool-schema cloning drives unbounded RSS growth in the agent loop (OOM risk). **Fix PR #8817** is open to use `Arc<[u8]>` sharing.

### 6. Feature Requests & Roadmap Signals
Several new features from today’s activity are strong candidates for the next release (v0.8.3).

- **New Feature:**
    - **[RFC #8798](https://github.com/zeroclaw-labs/zeroclaw/issues/8798):** A proposal to consolidate the two parallel WebSocket protocols (`/ws/chat` and `/acp`) into a single wire format. This is a significant architectural clean-up that could simplify the gateway but is likely a larger effort for a later release.
- **Likely for v0.8.3 (based on existing PRs):**
    - **Hot-reload of log config:** **[Feature #8314](https://github.com/zeroclaw-labs/zeroclaw/issues/8314)** has a fix PR **(#8816)** open, making it a high-probability candidate.
    - **Per-execution shell confirmation:** **[RFC #7155](https://github.com/zeroclaw-labs/zeroclaw/issues/7155)** is actively discussed and could start as an experimental config option.
    - **Tool filter fix:** **[Bug #6699](https://github.com/zeroclaw-labs/zeroclaw/issues/6699)** has a fix PR **(#8819)** open.
- **Long-term Roadmap:**
    - **Full-channel prebuilt assets:** **[Feature #7952](https://github.com/zeroclaw-labs/zeroclaw/issues/7952)** is blocked awaiting maintainer review, suggesting the release pipeline needs more investment.
    - **SOP Authoring Surface:** **[Task #8736](https://github.com/zeroclaw-labs/zeroclaw/issues/8736)** tracks the completion of the `feat/sop-authoring` branch, which is a major feature for the next release cycle.

### 7. User Feedback Summary
User feedback today reflects a mix of high satisfaction with the system's ambition and significant frustration with stability and documentation.

- **Pain Points:**
    - **Windows Stability (S2):** The zombie port issue is a major blocker for Windows users.
    - **Documentation Quality (S3):** Multiple bug reports (#8797, #8810) indicate that setup guides are out of sync with the actual code, creating a poor first impression. One user in #8810 explicitly stated the "documentation is wrong."
    - **UI Workflow Disruption (S1):** The erasure of context upon stopping a task (#8794) is a workflow-killing bug for users managing long conversational threads.
- **Satisfaction Signals:**
    - The high volume of feature requests (e.g., #8803 for UI improvements, #8798 for protocol consolidation) suggests a user base that is actively trying to build deep integrations and workflows.
    - The prompt resolution of the `crossbeam-epoch` security advisory (fix PR #8782 merged today) demonstrates a strong commitment to security, which is likely valued by enterprise users.

### 8. Backlog Watch
Several high-priority items remain unresolved and require maintainer attention.

- **High Risk:**
    - **[Issue #7952](https://github.com/zeroclaw-labs/zeroclaw/issues/7952) (P2, Blocked):** Publishing full-channel prebuilt assets. This is blocked due to lack of a "maintainer review" and is a repeat signal that the release process is a bottleneck.
    - **[Issue #8519](https://github.com/zeroclaw-labs/zeroclaw/issues/8519) (P1, In Progress):** Reconciling `cargo-audit` and `cargo deny` drift for `wasmtime-wasi` CVEs. This is an open security advisory reconciliation task that has been active for a week.
- **Long-Standing Open Items:**
    - **[PR #8639](https://github.com/zeroclaw-labs/zeroclaw/pull/8639) (XL size):** The `TodoWrite` tracker for ZeroCode hasn't been updated in 24 hours and appears to be stalled. This is a major feature with a large blast radius.
    - **[PR #8496](https://github.com/zeroclaw-labs/zeroclaw/pull/8496) (L size):** The centralization of deferred-MCP access policy has been open for 10 days. It is a high-risk change that is likely waiting on code review.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*