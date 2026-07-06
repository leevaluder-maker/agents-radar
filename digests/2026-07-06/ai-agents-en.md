# OpenClaw Ecosystem Digest 2026-07-06

> Issues: 500 | PRs: 500 | Projects covered: 13 | Generated: 2026-07-06 02:12 UTC

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

# OpenClaw Project Digest — 2026-07-06

## 1. Today's Overview

OpenClaw shows extremely high activity, with **500 issues and 500 PRs updated in the last 24 hours**, indicating a large, engaged community and significant development velocity. The project has **339 merged/closed PRs** and **428 open/active issues**, suggesting a healthy balance of code production and community reporting. A new beta release (v2026.7.1-beta.2) was published today, adding GPT-5.6 support. The backlog remains substantial, with many high-priority (P0/P1) issues tagged as `needs-maintainer-review` or `needs-product-decision`, indicating that maintainer bandwidth may be a bottleneck despite strong community contribution.

## 2. Releases

**New Release: v2026.7.1-beta.2**

Key changes:
- **OpenAI GPT-5.6 model family support** — OpenClaw now recognizes GPT-5.6 across catalog, capability, and runtime selection paths. (PR #98333, thanks @steipete-oai)
- **External harness attachment** — `openclaw attach` now launches an external harness against an existing Gateway session.

No breaking changes or migration notes were included in the release highlights.

## 3. Project Progress

**Merged/closed PRs today: 339**

Notable merged PRs:
- [#100434](https://github.com/openclaw/openclaw/pull/100434) — feat(ui): preview GitHub issues and pull requests on hover (Control UI improvement)
- [#100551](https://github.com/openclaw/openclaw/pull/100551) — fix(android): preserve chat sends across reconnect recovery
- [#97733](https://github.com/openclaw/openclaw/pull/97733) — feat: add channel pairing request hook (related to #68214, #89569)

Major areas of advancement visible in the PR activity:
- **Android app stability**: Multiple PRs addressing reconnection and send-message reliability
- **UI/UX improvements**: GitHub hover previews, update restart notifications
- **Channel integrations**: Tencent Hy3 provider (PR #99076), Telegram improvements
- **Authentication fixes**: Claude CLI auth via `apiKeyHelper` (PR #97492)

## 4. Community Hot Topics

**Most active issues by comment count:**

| Issue | Comments | Summary |
|-------|----------|---------|
| [#75](https://github.com/openclaw/openclaw/issues/75) | 110 | **Linux/Windows Clawdbot Apps** — 81👍; long-running request for desktop app support beyond macOS/iOS/Android |
| [#9443](https://github.com/openclaw/openclaw/issues/9443) | 26 | **Prebuilt Android APK releases** — user cannot compile from source; submitted via AI assistant |
| [#92201](https://github.com/openclaw/openclaw/issues/92201) | 20 | **Anthropic thinking signatures invalid on replay** — P1 reliability bug in embedded runner |
| [#48788](https://github.com/openclaw/openclaw/issues/48788) | 18 | **Centralized filename encoding utility** — multi-encoding Content-Disposition handling across channels |
| [#63918](https://github.com/openclaw/openclaw/issues/63918) | 17 | **Cron agentTurn sends `thinking=none` to OpenAI** — unsupported value error with gpt-5-nano |

**Key analysis:**
- **Cross-platform demand** is the single loudest signal (#75 with 110 comments, 81👍). Users want full desktop app support on Linux and Windows matching macOS feature parity.
- **AI-assisted submissions** are emerging (#9443 submitted on behalf of a user by their AI assistant), suggesting new usage patterns for the project's own issue tracker.
- **Anthropic/Claude integration** issues remain a hot pain point (#92201, #69118, #97492), especially around thinking signatures and session stability in group channels.

## 5. Bugs & Stability

**Critical (P0) issues:**

| Issue | Summary | Fix PR? |
|-------|---------|---------|
| [#9443](https://github.com/openclaw/openclaw/issues/9443) | Prebuilt Android APK releases — release blocker | No |
| [#48920](https://github.com/openclaw/openclaw/issues/48920) | Live docs ahead of release — `IsolatedSessions` in docs but not in shipped version | No |

**High severity (P1) issues:**

| Issue | Summary | Fix PR? |
|-------|---------|---------|
| [#92201](https://github.com/openclaw/openclaw/issues/92201) | Anthropic thinking signatures invalid on replay; recovery wrapper never fires | No |
| [#98416](https://github.com/openclaw/openclaw/issues/98416) | v2026.6.11 published dist missing reentrancy guard — reply session initialization conflict | No |
| [#48003](https://github.com/openclaw/openclaw/issues/48003) | Steer mode does not inject messages mid-turn for main sessions | PR open (#linked) |
| [#29387](https://github.com/openclaw/openclaw/issues/29387) | Bootstrap files in `agentDir` silently ignored | PR open (#linked) |
| [#64810](https://github.com/openclaw/openclaw/issues/64810) | Heartbeat/system events swallow in-progress Telegram replies | No |
| [#69118](https://github.com/openclaw/openclaw/issues/69118) | Claude CLI sessions reset on every turn in group channels | PR open (#linked) |
| [#51396](https://github.com/openclaw/openclaw/issues/51396) | `clearUnboundScopes` strips operator scopes unconditionally | PR open (#linked) |

**New bugs reported today (2026-07-06 activity):**
- [#100546](https://github.com/openclaw/openclaw/pull/100546) — fix(devices): recover unknown requestId approvals in password mode (fix PR open)
- [#100544](https://github.com/openclaw/openclaw/pull/100544) — fix(cli): sync root `--help` command descriptions with live registrations (fix PR open)
- [#100543](https://github.com/openclaw/openclaw/pull/100543) — fix(telegram): add missing "edit" retry context (fix PR open)

**Stability concerns:**
- **Session state/data loss** is a recurring theme across multiple P1 issues (#48003, #98416, #47975, #50165)
- **Memory leak** (#54155) — Gateway grows from 389MB to 14.7GB over 4 days; no fix PR spotted
- **Orphaned lock files** (#49603) — PID-based stale detection doesn't handle gateway restarts

## 6. Feature Requests & Roadmap Signals

**High-demand features with strong community support:**

| Feature | Issue | Reasoning for next release |
|---------|-------|---------------------------|
| **Linux/Windows Desktop Apps** | [#75](https://github.com/openclaw/openclaw/issues/75) | 110 comments, 81👍; long-standing need since Jan 2026 |
| **Prebuilt Android APK** | [#9443](https://github.com/openclaw/openclaw/issues/9443) | P0 release blocker; core team may prioritize |
| **Filesystem Sandboxing** | [#7722](https://github.com/openclaw/openclaw/issues/7722) | Security concern; multiple related issues (#6615 denylist, #45740 injection) |
| **Memory Trust Tagging** | [#7707](https://github.com/openclaw/openclaw/issues/7707) | Prevents memory poisoning; related to security hardening trend |
| **Masked Secrets** | [#10659](https://github.com/openclaw/openclaw/issues/10659) | Prevents API key leakage; high security impact |
| **Auto-update workflow** | [#12855](https://github.com/openclaw/openclaw/issues/12855) | Common UX expectation; configurable schedule |
| **Skill Priority Configuration** | [#50199](https://github.com/openclaw/openclaw/issues/50199) | Overlapping skill selection problem; clear UX need |

**Prediction:** The **Linux/Windows desktop app** request (#75) is the strongest roadmap signal, though its scope suggests it's a long-term feature. In the near term (next 1-2 releases), expect **security hardening** features (sandboxing, masked secrets, memory trust tagging) and **Android APK releases** to be prioritized, given the P0 status on #9443 and growing security-related issue volume.

## 7. User Feedback Summary

**Pain points expressed by users:**

1. **Platform gaps**: Multiple users express frustration that macOS has full app support while Linux and Windows users are left with CLI only (#75). One Chinese user (Issue #51429) reported a hardcoded Chinese developer's home path in the codebase — a serious professionalism concern.

2. **Reliability frustrations**: Users report silent data loss (WhatsApp missed messages #50093), hallucinated cron outputs (#49876), and sessions that appear complete before work finishes (#50165). @jimmylzt188 described "overlapping skills without clear selection rules" (#50199).

3. **Security anxiety**: @LumenLantern (#7707, #7722) filed two well-reasoned security feature requests about memory poisoning and filesystem access. @jmkritt (#10659) described a use case where "agents can **see** API keys" — a design concern. @ziens (#45740) demonstrated how the `gh-issues` skill injects un sanitized GitHub issue bodies into sub-agent prompts.

4. **Documentation drift**: @Stoff81 (#48920) called out that live docs contain features not yet released: "Heartbeat IsolatedSessions is in the live docs but not in the latest version." This erodes trust.

5. **AI assistant usage patterns**: Issue #9443 was "submitted on behalf of Lysen, by his AI assistant QING" — a novel pattern where users delegate issue filing to their agents, potentially increasing noise but also changing how maintainers should triage.

**Satisfaction signals:**
- High PR merge volume (339 today) suggests responsive maintainers
- Enthusiastic thanks in release notes (@steipete-oai thanked for GPT-5.6 support)
- Community members filing well-crafted feature RFCs (#35203, #48874) shows deep product engagement

## 8. Backlog Watch

**Long-unanswered high-impact issues needing maintainer attention:**

| Issue | Age | Status | Why it matters |
|-------|-----|--------|----------------|
| [#75](https://github.com/openclaw/openclaw/issues/75) | 6+ months | `needs-maintainer-review`, `needs-product-decision` | Most commented issue (110); core platform gap |
| [#7707](https://github.com/openclaw/openclaw/issues/7707) | 5+ months | `needs-maintainer-review`, `needs-product-decision` | Memory security; multiple security tags |
| [#10659](https://github.com/openclaw/openclaw/issues/10659) | 5+ months | `needs-maintainer-review`, `needs-product-decision`, `needs-security-review` | API key exposure risk |
| [#13700](https://github.com/openclaw/openclaw/issues/13700) | ~5 months | `needs-maintainer-review`, `needs-product-decision` | Session snapshots checkpointing — useful UX |
| [#29387](https://github.com/openclaw/openclaw/issues/29387) | ~4 months | `needs-maintainer-review`, `needs-product-decision`, `needs-security-review` | Bootstrap files silently ignored (P1 security) |
| [#45740](https://github.com/openclaw/openclaw/issues/45740) | ~4 months | `needs-maintainer-review`, `needs-product-decision`, `needs-security-review` | `gh-issues` skill prompt injection (P2 security) |
| [#48920](https://github.com/openclaw/openclaw/issues/48920) | ~3.5 months | `needs-maintainer-review`, `needs-product-decision` | Docs ahead of release — P0 regression |

**Stale issues with linked PRs not yet merged:**
- [#53628](https://github.com/openclaw/openclaw/issues/53628) — `XDG_CONFIG_HOME` not processed during skill install (P2, has linked PR)
- [#50090](https://github.com/openclaw/openclaw/issues/50090) — Community Skill Development & ClawHub ecosystem (P2, high potential impact)
- [#57901](https://github.com/openclaw/openclaw/issues/57901) — Safeguard compaction ignores `compaction.model` config (P2, has linked PR)

**Observation:** Many security-tagged issues (P1/P2) simultaneously carry `needs-maintainer-review`, `needs-product-decision`, AND `needs-security-review` tags, suggesting organizational delays in triage rather than technical difficulty. The security backlog appears to be a growing concern that may need dedicated security triage resources.

---

## Cross-Ecosystem Comparison

# Cross-Project Ecosystem Report — 2026-07-06

## 1. Ecosystem Overview

The personal AI assistant open-source ecosystem is experiencing a **divergent maturation phase**, characterized by one dominant project (OpenClaw) driving massive community velocity while specialized forks and alternatives carve distinct niches. A clear **architecture split** is emerging between monolithic, all-in-one frameworks (OpenClaw, IronClaw) and modular, minimalist approaches (NanoClaw, PicoClaw). Security and reliability concerns have become the ecosystem's most pressing shared challenge, with multiple projects simultaneously battling memory corruption bugs, MCP connection resilience failures, and credential leakage risks. The ecosystem is also seeing **geographic fragmentation**, with Chinese-language communities forming around projects like CoPaw and LobsterAI, while English-speaking communities cluster around the OpenClaw/NanoBot/Hermes stack. Overall activity remains robust—six of eleven tracked projects saw substantive updates today—but the distribution is highly uneven, with OpenClaw alone accounting for over 80% of total issue+PR activity.

---

## 2. Activity Comparison

| Project | Issues Updated (24h) | PRs Updated (24h) | New Release? | Health Score | Key Signal |
|---------|---------------------|-------------------|--------------|--------------|------------|
| **OpenClaw** | 500 | 500 | ✅ v2026.7.1-beta.2 | ⚡ Extreme (dominant) | 339 merged PRs/day; massive community |
| **NanoBot** | 2 | 18 | ❌ | 🟢 Active | Healthy PR pipeline; MCP stability focus |
| **Hermes Agent** | 50 | 50 | ❌ | 🟢 Very Active | MCP reconnect fixes converging |
| **PicoClaw** | 2 | 5 | ❌ | 🟡 Moderate | Security modernization (libolm→vodozemac) |
| **NanoClaw** | 0 | 5 | ❌ | 🟢 Stable | Zero open bugs; 3 features merged |
| **NullClaw** | 0 | 0 | ❌ | ⚫ Inactive | No activity detected |
| **IronClaw** | 4 | 27 | ❌ | 🟢 Very Active | Slack OAuth migration; 5 PRs merged |
| **LobsterAI** | 0 | 1 (merged) | ❌ | 🟡 Low Activity | Single UI polish PR; 95-day stale PR |
| **TinyClaw** | 0 | 0 | ❌ | ⚫ Inactive | No activity detected |
| **Moltis** | 0 | 0 | ❌ | ⚫ Inactive | No activity detected |
| **CoPaw** | 12 | 5 | ❌ | 🟡 Bug-Fix Sprint | 9 open bugs; active user testing |
| **ZeptoClaw** | 0 | 0 | ❌ | ⚫ Inactive | No activity detected |
| **ZeroClaw** | 23 | 50 | ❌ | 🟡 Intense/Unstable | Major features + P1 bugs + high PR count |

**Notes:**
- Health scores blend activity volume, bug severity, and community engagement
- "Inactive" (⚫) means zero commits, issues, or PRs in 24h—not necessarily abandoned
- ZeroClaw's high PR count (44 open) and 2 P1 bugs suggests development velocity outpacing stability

---

## 3. OpenClaw's Position

**Advantages vs. Peers:**
- **Community scale that no competitor approaches:** 500 issues + 500 PRs updated daily, with 339 merged/closed PRs in 24 hours. This is roughly 10x the activity of the next most active project (Hermes, IronClaw).
- **Feature breadth and release cadence:** Pushing beta releases with major model support (GPT-5.6) while juggling Android, Telegram, UI/UX, and authentication fixes across the same cycle.
- **Cross-platform demand validation:** Issue #75 (Linux/Windows desktop apps) has 110 comments and 81 upvotes—a clear signal that users see OpenClaw as their primary agent platform, not just a CLI tool.
- **Ecosystem gravity:** The `openclaw attach` external harness feature (v2026.7.1-beta.2) positions OpenClaw as an orchestrator that other tools integrate *into*.

**Technical Approach Differences:**
- OpenClaw is a **monolithic reference implementation** with embedded runners, Gateway sessions, and channel integrations built-in. This contrasts with NanoClaw's lightweight skill-based approach and ZeroClaw's MCP-centric modularity.
- OpenClaw appears to prioritize **feature completeness over architectural purity**, accepting technical debt (orphaned lock files, memory leaks) in exchange for rapid capability expansion.

**Community Size Comparison:**
- OpenClaw's community is an order of magnitude larger than any tracked peer. The closest competitors (Hermes, IronClaw, NanoBot) operate at ~50-100 issues+PRs/day combined.
- However, OpenClaw's 428 open issues and `needs-maintainer-review` bottlenecks suggest the community is outgrowing its governance structure.

**Vulnerability:** OpenClaw's scale creates a **maintainer bottleneck risk**—428 open issues, many with multiple triage tags, signal that community contribution volume exceeds core team bandwidth.

---

## 4. Shared Technical Focus Areas

| Focus Area | Affected Projects | Specific Needs |
|------------|------------------|----------------|
| **MCP Connection Resilience** | NanoBot, Hermes, ZeroClaw, OpenClaw | Reconnect crash fixes, zombie processes, stream-stale loops, cancel scope isolation |
| **Memory/State Corruption** | OpenClaw, PicoClaw, ZeroClaw | Write_file destructive overwrites, session data loss, context fragmentation |
| **Security Hardening** | OpenClaw, PicoClaw, NanoClaw, ZeroClaw | libolm→vodozemac migration, credential masking, filesystem sandboxing, SSRF prevention |
| **Desktop App Coverage** | OpenClaw (#75), NanoBot (implicit), CoPaw (mobile web) | Linux/Windows native apps, mobile responsiveness, Termux/Android support |
| **Tool-Call Reliability** | IronClaw, OpenClaw, NanoBot | Corrupted XML arguments, provider compat layers, tool-call loop breakers |
| **Provider Compatibility** | OpenClaw, IronClaw, CoPaw, ZeroClaw | Cross-provider model matching, OAuth flows, custom API endpoints |
| **Onboarding Friction** | ZeroClaw, NanoClaw, OpenClaw | Broken default configs, APK releases, wizard-based setup flows |

**Observations:**
- **MCP resilience** is the single most active cross-project fix area today, with NanoBot (#4764, #4701), Hermes (#59222 merged), and IronClaw all addressing similar reconnect/stale-session bugs.
- **Security** is rising as a shared concern, but response is uneven—PicoClaw and NanoClaw are proactively replacing crypto dependencies, while OpenClaw has security-tagged issues sitting unassigned for months.
- **Desktop/mobile platform gaps** are a recurring theme across Chinese and English-language communities, suggesting a universal user expectation for native app experiences.

---

## 5. Differentiation Analysis

| Dimension | OpenClaw | NanoBot | Hermes | IronClaw | NanoClaw | ZeroClaw |
|-----------|----------|---------|--------|----------|----------|----------|
| **Architecture** | Monolithic reference | Modular SDK + core | Agent framework | Production Rust system | Skill-based lightweight | MCP-centric modular |
| **Target User** | Power users, integrators | Python developers | Claude/OAI users | Enterprise Rust teams | Quick-start agent builders | Advanced orchestrators |
| **Primary Language** | Go (implied by CLI) | Python | Rust/Go? | Rust | Python | Rust |
| **Release Cadence** | Daily betas | Batch-based | Per-feature | Per-sprint | Per-feature | Between cycles |
| **Community Size** | ⭐⭐⭐⭐⭐ (Dominant) | ⭐⭐⭐ (Active) | ⭐⭐⭐⭐ (Very Active) | ⭐⭐⭐ (Active) | ⭐⭐ (Growing) | ⭐⭐⭐ (Active) |
| **Risk Level** | High (scale > governance) | Medium (stability gaps) | Medium (MCP issues) | Low (disciplined) | Very Low (zero bugs) | High (velocity > stability) |
| **Key Differentiator** | Maximum breadth | Python SDK ergonomics | Claude integration depth | Rust production rigor | Simplicity and guardrails | SOP/Goal-based workflows |

**Key Differences:**
- **NanoClaw** is the only project with **zero open bugs**—a remarkable achievement that suggests either a very small user base or exceptional quality control. Its guardrails feature (#2726) is unique in the ecosystem.
- **IronClaw** stands out for its **engineering discipline**: Rust typesystem, CI tripwires (#5637), coverage tracking (#5657), and a clear Slack OAuth migration plan. It's the only project that feels "enterprise-ready."
- **ZeroClaw** is the most **architecturally ambitious**, pushing SOP authoring (node-graph editor), Goal Mode, and MCP-centric modularity. But it's also the most unstable (2 P1 bugs, 44 open PRs).
- **Hermes** has the most **focused community identity** around Claude subscription access (#25267, 41👍), suggesting a product-market fit that other projects lack.

---

## 6. Community Momentum & Maturity

**Tier 1: Extreme Velocity (Rapid Iteration)**
- **OpenClaw** — Engine at full throttle. 339 PRs merged in 24 hours. But 428 open issues and triage bottlenecks suggest this pace may be unsustainable. The community is growing faster than governance.
- **ZeroClaw** — High-risk, high-reward. Major architectural features (SOP, Goal Mode) racing toward completion alongside a P1 bug pile. If they stabilize, they'll leapfrog peers in workflow sophistication.

**Tier 2: Very Active (Feature-Drive)**
- **Hermes Agent** — Strong MCP fix convergence today. The Claude subscription OAuth demand (#25267) gives it a clear growth vector. Healthy 50/50 issue/PR split.
- **IronClaw** — Most disciplined active project. Coordinated Slack migration, tool security hardening, and error surfacing. Low bug count relative to activity. Looks ready for a 0.29.1 release soon.
- **NanoBot** — Solid PR pipeline (18 updates) and MCP fixes in flight. The Python SDK bug (#4765) is a doc-sync issue, not a code quality problem. Stable, predictable velocity.

**Tier 3: Moderate (Consolidation/Polish)**
- **PicoClaw** — Steady maintenance with a clear security modernization goal (libolm→vodozemac). DeltaChat refactor (-320 LOC) shows code quality focus. Not feature-pushing but solid.
- **NanoClaw** — Almost eerie stability: 0 open bugs, 3 features merged, clear roadmap (templates, LiteLLM, guardrails). Small community but highly focused.
- **CoPaw** — In a bug-fix sprint after v1.1.12.post2. 9 open bugs, many with fix PRs already. This is a "stabilize then ship v2.0" phase, not growth.

**Tier 4: Low/Inactive**
- **LobsterAI** — 1 PR merged, one 95-day stale PR (#1349). Appears to be in maintenance mode or waiting for a v2.0 push.
- **NullClaw, TinyClaw, Moltis, ZeptoClaw** — Zero activity in 24h. These may be seasonal, abandoned, or very small projects between releases.

**Maturity Assessment:**
- **Most mature:** IronClaw (enterprise discipline), NanoClaw (zero-bug stability)
- **Most rapidly maturing:** ZeroClaw (if they land Goal Mode + SOP without regression cascade)
- **Most at risk of governance failure:** OpenClaw (scale without structure)
- **Most at risk of stagnation:** LobsterAI (single maintainer bottleneck)

---

## 7. Trend Signals

**1. MCP is the Universal Integration Layer—But It's Fragile**
Every major project except NanoClaw is fighting MCP-related bugs: connection drops, zombie processes, tool-call corruption, stream-stale loops. The ecosystem *needs* MCP to work as a standard, but the implementations are still fragile. **Signal:** Invest in MCP middleware resilience. The project that solves MCP stability first (Hermes and NanoBot are closest) will win integration credibility.

**2. Security Hardening is Shifting Left—From Maintenance to Feature**
Projects are no longer *reacting* to security bugs; they're *proactively* replacing dependencies (PicoClaw's libolm→vodozemac), adding guardrail systems (NanoClaw's /add-guardrails), and building credential-leak detectors. **Signal:** Security features are becoming competitive differentiators. The era of "ship fast, patch CVEs later" is ending in the AI agent space.

**3. The "Desktop Gap" is the New Mobile Gap**
OpenClaw's #75 (110 comments, 81👍), ZeroClaw's Android/Termux issues, and CoPaw's mobile web truncation all point to the same user need: **I want an agent that runs natively on my device, not in a browser tab.** The command-line-only era is meeting resistance. **Signal:** Desktop/Android-native releases will drive adoption growth. Projects without a desktop story (all except OpenClaw partial) are leaving users on the table.

**4. Chinese-Language Communities Are Becoming Self-Sufficient**
CoPaw, PicoClaw, and LobsterAI have significant Chinese-language issue trackers and communities. Issues are filed in Chinese, responses are in Chinese, and geographic needs (China-blocked APIs, WeChat/Feishu integrations) are driving feature priorities. **Signal:** The AI agent ecosystem is bifurcating along linguistic lines. Global projects must decide: invest in Chinese-language support or accept a parallel ecosystem.

**5. Onboarding is the #1 Growth Bottleneck**
ZeroClaw's broken default config (#8718), OpenClaw's prebuilt Android APK demand (#9443, P0), NanoBot's broken Python SDK example (#4765), and NanoClaw's template wizard (#2909) all point to the same truth: **users want to run, not configure.** The projects solving first-run experience (NanoClaw's wizard, OpenClaw's potential APK release) will have higher retention than those adding yet another provider integration.

**6. Subscription OAuth is the Next Frontier**
Hermes's #25267 (Claude subscription OAuth, 41👍) and IronClaw's Slack OAuth migration signal a shift: users want to bring their existing subscriptions, not manage API keys. **Signal:** OAuth support for Claude, ChatGPT, and other subscription services will be a major adoption driver in 2026 H2. The project that cracks "use your Claude subscription with our agent" will see rapid user growth.

**7. AI-Assisted Development is Changing Community Engagement**
OpenClaw's #9443 was submitted by an AI assistant on behalf of a human user. This is a new pattern: agents writing bug reports for their own frameworks. **Signal:** Expect an increase in automated, agent-originated issues. Maintainers need triage processes that can distinguish human-priority issues from AI-generated noise.

---

*Report generated 2026-07-06. Data sourced from project GitHub activity in the preceding 24 hours. Health assessments are relative within this tracked cohort and may not reflect absolute project viability.*

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

# NanoBot Project Digest — 2026-07-06

## Today's Overview
NanoBot sees moderate activity today with 2 new issues and 18 updated pull requests, though no new release is published. The repository shows a healthy burst of PR activity, with 3 PRs merged/closed including a critical fix for MCP reconnection crashes. Open PRs span important areas: MCP stability, subagent configurability, SSRF security hardening, and provider standardization. Community discussion is light today, but the development pipeline is full with 15 open PRs, indicating active work toward the next release.

## Releases
No new releases today. The latest available version remains as previously published.

## Project Progress
Three pull requests were merged or closed today:

- **#4554** (merged) — `fix(memory): block Dream from creating duplicate skills via write guard` by michaelxer. Adds a write guard to prevent Dream's skill creation from producing duplicate directories, directing it to edit existing skills instead. This resolves a behavioral issue in the memory/agent system.
- **#4441** (merged) — `fix(mcp): force-close streamable_http generator on reconnect failure` by michaelxer. Fixes a gateway crash (`RuntimeError: Attempted to exit cancel scope in a different task than it was entered in`) that occurred when MCP server sessions terminated during reconnection.
- **#4699** (closed) — `fix(providers): add Anthropic OAuth with env-var-aware login/logout` by axelray-dev. Integrates Anthropic OAuth provider with dual-source token reading (file + `CLAUDE_CODE_OAUTH_TOKEN` env var).

## Community Hot Topics
Activity levels are low today with minimal comments and reactions. The most notable items:

- **#4765** (created today) — [Bug] `Nanobot object does not support the asynchronous context manager protocol`. This is a fresh bug report with 1 comment and 1 reaction. The user reports that the Python SDK example from official docs throws an immediate error, while the web UI works fine. [Issue Link](https://github.com/HKUDS/nanobot/issues/4765)
- **#4702** — [Feature Request] Support custom API Base URL and request headers for Telegram Channel. Opened yesterday with no comments yet, but represents a clear user need for users in restrictive network environments. [Issue Link](https://github.com/HKUDS/nanobot/issues/4702)

The low engagement suggests either the issues are straightforward (awaiting maintainer response) or the community is quieter today.

## Bugs & Stability
One new bug and several critical/severe issues with active fix PRs:

### High Severity
- **#4765** [NEW] — `Nanobot object does not support the asynchronous context manager protocol`. Python SDK usage fails with immediate traceback. No fix PR yet. [Issue Link](https://github.com/HKUDS/nanobot/issues/4765)
- **#4671** `[priority: p0]` — SSRF security: DNS validation needed. Active PR **#4671** by hamb1y resolves this by pinning validated DNS for URL checks. [PR Link](https://github.com/HKUDS/nanobot/pull/4671)
- **#4764** `[priority: p1]` — MCP reconnect cancel scope isolation to prevent gateway crash. Active PR by tjc0726 addresses this. [PR Link](https://github.com/HKUDS/nanobot/pull/4764)
- **#4701** `[priority: p1]` — MCP tool call exceptions can crash the agent loop. Active PR by axelray-dev catches `BaseException` in all MCP wrappers. [PR Link](https://github.com/HKUDS/nanobot/pull/4701)
- **#4700** `[priority: p1]` — Long MCP-derived tool names exceed API limits. Active PR by thomya truncates names to comply. [PR Link](https://github.com/HKUDS/nanobot/pull/4700)

### Medium-Low Severity
- **#4545** `[priority: p1]` — Windows command execution inconsistent between single-line (`cmd.exe`) and multi-line (PowerShell). Active PR by dajiaohuang fixes this. [PR Link](https://github.com/HKUDS/nanobot/pull/4545)
- **#4698** `[priority: p2]` — OAuth CLI error messages differ between CLI and WebUI. Active PR by axelray-dev standardizes them. [PR Link](https://github.com/HKUDS/nanobot/pull/4698)

## Feature Requests & Roadmap Signals
New and notable feature requests from the community:

- **#4702** — Custom API Base URL and request headers for Telegram Channel. Users in restricted networks need flexibility beyond proxy configuration. Likely to be addressed in next minor release given Telegram channel usage. [Issue Link](https://github.com/HKUDS/nanobot/issues/4702)

Active feature PRs that have high likelihood of merging:
- **#4697** — Configurable MCP inheritance for specialist subagents (priority p1). Strong demand for subagent flexibility.
- **#4623** — Subagent spawn model override. Small, clean feature.
- **#4624** — Aggregated result mode for subagents. Adds buffering and combined results.
- **#4620** — Heartbeat trigger command. Addresses long-standing request #3437.
- **#4406** — Serper.dev web search provider. New provider addition.
- **#4763** — Feishu session divider and reasoning panel. Channel-specific improvement.

These features, especially subagent enhancements and the heartbeat command, are strong candidates for the next release.

## User Feedback Summary
Pain points expressed today:

- **Python SDK usability**: Issue #4765 shows a user cannot run the documented SDK example at all, despite the web UI working. This is a significant onboarding friction point — the official docs should provide a working first experience.
- **Telegram network restrictions**: Issue #4702 shows users in China or similar restricted environments need to route Telegram traffic through custom endpoints or add custom headers, which is currently hardcoded.
- **MCP reliability**: Multiple PRs (#4764, #4701, #4700) address crashes or errors stemming from MCP integrations, suggesting users are experiencing agent loop failures in production with MCP-based setups.

User satisfaction is mixed: the web UI is praised as "working well," but the Python SDK and MCP stability are clear friction points.

## Backlog Watch
Issues and PRs needing attention:

- **#4353** (created June 15) — `fix(transcription): convert audio to WAV 16k mono before STT`. Open PR with no recent activity. Blocked or waiting on review? [PR Link](https://github.com/HKUDS/nanobot/pull/4353)
- **#4406** (created June 18) — `feat(web-search): add Serper.dev provider`. Open PR with no activity since June 24. Minor provider addition that may be low priority. [PR Link](https://github.com/HKUDS/nanobot/pull/4406)
- **#4545** (created June 26) — `fix(exec): default Windows commands to PowerShell`. Open 10 days, no maintainer comments. Windows users are likely affected by inconsistent behavior. [PR Link](https://github.com/HKUDS/nanobot/pull/4545)

**Project health summary**: NanoBot is in an active development phase with strong throughput on bug fixes and features. The main risk areas are MCP stability (multiple high-severity fixes in flight) and documentation gaps (SDK example broken). The absence of a release suggests the team is batching these changes together.

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

# Hermes Agent Project Digest — 2026-07-06

## Today's Overview

Project activity is **very high**, with 50 issues and 50 PRs updated in the last 24 hours, indicating strong developer and community engagement. The open-to-closed ratio remains healthy (42 open vs. 8 closed issues; 34 open vs. 16 merged/closed PRs). The most prominent theme this week is **MCP (Model Context Protocol) connection resilience** — a cluster of related fixes is converging into a comprehensive solution for permanently-abandoned MCP servers. No new releases were published today.

## Releases

**None.** No releases were published in the last 24 hours. The latest public release remains at a previous tag.

## Project Progress

The following significant PRs were merged/closed today, representing major fixes and improvements:

- **MCP Reconnect Resilience (#59222)** — Salvages and unifies three prior PRs (#57615, #54139, #57477). MCP servers now reset retry budgets per healthy session, self-probe parked servers every 5 minutes, and re-register tools on revival. No longer permanently dead after transient blips. *Merged.*
- **MCP CLI Probe Timeout Fix (#59219)** — Salvages #34276, #56699, #54494. All six CLI/GUI MCP probe call sites now honor per-server `connect_timeout` config. *Merged.*
- **QQBot `is_reconnect` Parameter Fix (#59297)** — Fixes `TypeError` on QQAdapter reconnect by accepting the new `is_reconnect` kwarg. *Open.*
- **Auxiliary Client Credential Reuse (#59301)** — Auxiliary tasks (vision, compression, title gen) now work with named custom providers by reusing the main runtime's resolved credentials. *Open.*
- **Tool-Audit Skill (#58805)** — New bundled skill for agent self-monitoring of tool execution patterns. *Open.*
- **Crawl4ai Web Extraction Provider (#59300)** — New web extraction backend for self-hosted content scraping. *Open.*
- **Composite Toolset Fix (#59299)** — Prevents explicitly enabled subtools (e.g., `terminal` + `file`) from being disabled when the parent composite toolset (`coding`) is disabled. *Open.*
- **MCP OAuth Connect Timeout (#57353, #56699, #54494)** — Three separate PRs (all closed/merged) fix the 40-second hard timeout on OAuth login flows, now honoring per-server `connect_timeout`. *All merged.*

## Community Hot Topics

The most active discussions and reactions reveal two clear pain points:

1. **Claude Subscription OAuth (#25267)** — 41 👍, 9 comments. Users want to run Hermes with Claude as the backend *without* needing a separate API key, instead using their existing subscription via OAuth. This is a high-demand feature with significant community backing. *Issue #25267* (NousResearch/hermes-agent Issue #25267)

2. **Dashboard Reverse Proxy Flag (#34390)** — 9 comments. Request for an `--allowed-hosts` flag to make the dashboard work behind Tailscale Serve, nginx, or Caddy without DNS rebinding protection blocking legitimate reverse-proxy setups. *Issue #34390* (NousResearch/hermes-agent Issue #34390)

3. **Ollama Context Cap (#43900)** — 8 comments. Local Ollama models silently capped at 4096-token context despite GGUF metadata reporting larger capacity. Active discussion about the root cause (HuggingFace tokenizer vs. Ollama's `num_ctx` parameter). *Issue #43900* (NousResearch/hermes-agent Issue #43900)

4. **Terminal.cwd Config Ignored (#42961)** — 8 comments. The `terminal.cwd` config setting is silently discarded for the local backend; process cwd is always used. *Issue #42961* (NousResearch/hermes-agent Issue #42961)

## Bugs & Stability

**High Severity (P2):**

- **Sessions Stuck in Stream Stale Loop (#58962)** — [OPEN] Sessions permanently enter an infinite "Stream stale" loop after one timeout; all subsequent retries also stale. Affects OpenAI-compatible providers (Xiaomi). No linked fix PR yet. *Issue #58962* (NousResearch/hermes-agent Issue #58962)
- **Classic CLI /resume Hides Desktop Sessions (#59224)** — [OPEN] The `/resume` listing only shows sessions tagged `source="cli"`, hiding Desktop and WebUI sessions. Fix may require query filter change. *Issue #59224* (NousResearch/hermes-agent Issue #59224)
- **Fix PRs exist for:** MCP permanent abandonment (#59222 merged), QQBot reconnect TypeError (#59297 open), MCP CLI probe timeout (#59219 merged).

**Medium Severity (P3):**

- **Desktop Image Paste Sends File Path (#41556)** — [OPEN] Pasted images saved to disk but model receives only the file path, not the image data. *Issue #41556* (NousResearch/hermes-agent Issue #41556)
- **Web UI Chat Scrollbar Cannot Scroll to Bottom (#38669)** — [OPEN] Scrolling up then attempting to return to bottom causes scrollbar to jump back to top. *Issue #38669* (NousResearch/hermes-agent Issue #38669)

**Closed/Resolved:**

- **MCP OAuth Login Timeout (#24097)** — Closed as fixed by PR #59219. *Issue #24097* (NousResearch/hermes-agent Issue #24097)
- **Desktop-First Commits Degrading CLI/TUI (#59257)** — Closed as a bug report, likely resolved by PR #57000. *Issue #59257* (NousResearch/hermes-agent Issue #59257)

## Feature Requests & Roadmap Signals

- **Claude Subscription OAuth (#25267)** — Strong community demand (41 👍). This could appear in the next release if the maintainers prioritize subscription-based model access.
- **Dashboard --allowed-hosts Flag (#34390)** — A clear, low-risk config addition to support reverse-proxy deployments. Likely to be implemented soon.
- **Kanban Event Substrate (#49190)** — Generalizing Kanban notifications into a publish/subscribe system. More architectural than quick fix; likely a mid-term roadmap item.
- **Automated Workspace Memory (#38552)** — Agent remembers what directories are for across sessions. Complementary to memory improvements in #33856.

## User Feedback Summary

**Pain Points:**
- Subscription users feel **double-charged** when using Claude with Hermes — they pay for Claude subscription + API token usage. This is the most vocal complaint.
- MCP servers being **permanently abandoned** after transient failures was a top frustration; today's merged PRs directly address this.
- **Configuration inconsistencies** (terminal.cwd ignored, local provider lacks env var support) undermine the "configure once, run anywhere" promise.
- **Desktop app connectivity** issues (false "Could not connect" error, No. 3 by comment count) erode trust in the native desktop experience.

**Satisfaction Signals:**
- The community appreciates **rapid bug fixes** — multiple MCP reconnect PRs were merged within days of issue reports.
- Users are actively **requesting new integrations** (crawl4ai, Feishu/WhatsApp webhook hardening) showing strong engagement with the platform ecosystem.

## Backlog Watch

The following issues/PRs have been open for extended periods with no maintainer response or resolution:

- **#5388 — Context fragmentation** (2026-04-06, 2 comments) — Chinese-language report of severe context breakage when inserting intermediate context. No maintainer reply. *Issue #5388* (NousResearch/hermes-agent Issue #5388) — *Note: Could be a duplicate or language-barrier issue.*

- **#9318 — Auxiliary client falls back to "no-key-required"** (2026-04-14, 3 comments) — Per-task custom `base_url` without `api_key` silently skips auth. Pinged but no resolution. *Issue #9318* (NousResearch/hermes-agent Issue #9318) — *Note: Today's PR #59301 partially addresses this for named custom providers.*

- **#59232 — Spam/suggestion for monetized MCP server** (2026-07-05) — This is likely an unsolicited commercial pitch, not a real feature request. May warrant closure as invalid.

**Actionable backlog items needing maintainer attention:**

- **#58962 — Stream stale infinite loop** — No fix PR exists; P2 bug affecting sessions permanently.
- **#59224 — CLI /resume hides Desktop sessions** — Recently filed but no PR yet; P2 bug for multi-launcher users.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

# PicoClaw Project Digest — 2026-07-06

## Today's Overview
PicoClaw shows steady maintenance activity over the past 24 hours, with 2 issues updated (1 open, 1 closed) and 5 pull requests updated (4 open, 1 merged/closed). No new releases have been published. The project is actively processing infrastructure upgrades (Docker base image bumps, config cleanup) alongside a significant refactor of the DeltaChat module that reduces code by over 300 lines. A high-priority feature request to replace the unmaintained `libolm` with `vodozemac` remains open and has drawn community attention. Overall, the project is in a **healthy, moderately active** state with a clear focus on modernization and code quality.

## Releases
**No new releases** since the last digest.

## Project Progress
One pull request was merged/closed in the last 24 hours:

- **[PR #3189 (CLOSED)]** fix(line): explicitly ignore `resp.Body.Close()` errors in Send and classifySDKError — *Author: chengzhichao-xydt* — A stability fix for the LINE messaging channel, explicitly handling HTTP response body close errors in two code paths to prevent potential resource leaks or panics.

**Open but advancing PRs (all updated today):**

- **[PR #3222]** refactor(deltachat): cleanup implementation, documentation -320LOC — *Author: trufae* — A major cleanup dropping legacy features, password-based email config, and outdated tests; adds `join_invite_link` and `show_invite_link` methods; references official relay list website instead of a hardcoded copy.
- **[PR #3226]** fix(tools): stop `write_file` from coaching destructive overwrite (#3150) — *Author: ACMYuechen* — Directly addresses the "memory loss" bug (Issue #3150) by fixing the `write_file` tool to no longer frame existing files purely as "replace" or actively coach the model toward destructive overwrite.
- **[PR #3192]** chore(docker): bump goreleaser base images from alpine:3.21 to 3.23 — *Author: chengzhichao-xydt* — Infrastructure dependency update for consistency.
- **[PR #3191]** chore: remove duplicate `build/` entry in `.gitignore` — *Author: chengzhichao-xydt* — Minor config cleanup.

## Community Hot Topics

1. **[Issue #3088 (OPEN)]** [Feature] use `vodozemac` instead of `libolm` — *Author: pbsds* — ⭐ **Highest priority** | ❤️ 2 👍 | 💬 6 comments  
   *Link: [sipeed/picoclaw Issue #3088](https://github.com/sipeed/picoclaw/issues/3088)*  
   **Analysis:** This issue reflects strong community concern about security dependencies. The request to replace `libolm` (unmaintained, insecure) with `vodozemac` (the official replacement) is tagged `priority: high`. The community is actively discussing making `libolm` optional at compile time. This is the most impactful open feature request and represents a clear security modernization need.

2. **[Issue #3150 (CLOSED)]** [BUG] "它给自己整失忆了" (translation: "It lost its memory") — *Author: svier0* — 💬 5 comments  
   *Link: [sipeed/picoclaw Issue #3150](https://github.com/sipeed/picoclaw/issues/3150)*  
   *Now has a fix PR: [PR #3226](https://github.com/sipeed/picoclaw/pull/3226)*  
   **Analysis:** This Chinese-reported bug described the PicoClaw agent losing its memory context. It has now been assigned a targeted fix (#3226). The underlying need is robust tool behavior when updating memory files — the `write_file` tool was destructively overwriting rather than merging content.

## Bugs & Stability

| Severity | Issue | Status | Details |
|----------|-------|--------|---------|
| 🔴 **High** | [#3150](https://github.com/sipeed/picoclaw/issues/3150) "Memory loss bug" | **Fix PR exists (#3226)** | The `write_file` tool coached models toward destructive overwrite of `memory/MEMORY.md`, causing loss of agent state. Fix explicitly adds guard against this behavior. |
| 🟡 **Low** | [#3189](https://github.com/sipeed/picoclaw/pull/3189) (merged) LINE channel error handling | **Fixed** | Explicitly ignores `resp.Body.Close()` errors to prevent potential panics in LINE message sending. |

**No new bugs reported in the last 24 hours.** The existing high-severity memory bug has an active fix PR under review.

## Feature Requests & Roadmap Signals

1. **[Priority: HIGH]** **Replace libolm with vodozemac** (#3088) — Strong candidate for next release. Community consensus that `libolm` is a security liability. The request is well-scoped: make libolm optional at compile time, use vodozemac as primary. *Likely roadmap item for v0.2+.*

2. **DeltaChat module modernization** (PR #3222) — The ongoing refactor drops legacy features, removes password-based email config (moving secrets to JSON-RPC), and adds new invite link methods. *Signals a push toward cleaner, maintainable protocol integration.*

3. **Infrastructure upgrades** (PR #3192, PR #3191) — Docker base image bumps and .gitignore cleanup show ongoing maintenance hygiene. *Likely to be merged soon for next patch release.*

**Prediction:** The next release will likely include the `vodozemac` migration (if merged), the DeltaChat refactor, and the memory-write fix, representing a significant security and reliability update.

## User Feedback Summary

- **Pain Point:** Memory loss bug (#3150) — A Chinese-language user reported that PicoClaw "lost its memory," which was traced to the `write_file` tool's aggressive overwrite behavior. The community response (fix PR #3226) indicates strong developer attentiveness.
- **Security Concern:** The community is actively pushing for removal of `libolm` (#3088), demonstrating sophisticated awareness of dependency security. Users want upstream-protected, actively maintained cryptographic libraries.
- **Satisfaction Signal:** The DeltaChat refactor (PR #3222) removes hardcoded relay lists in favor of official website references, which aligns with user expectations for up-to-date, maintainable configurations.
- **Overall Sentiment:** Positive. The project is responsive to bug reports (fix PR within 16 days of issue creation) and community-driven security upgrades. No user frustration expressions observed.

## Backlog Watch

| Item | Created | Updated | Status | Maintainer Attention Needed? |
|------|---------|---------|--------|------------------------------|
| **[Issue #3088](https://github.com/sipeed/picoclaw/issues/3088)** — Replace libolm with vodozemac | 2026-06-09 | 2026-07-05 | Open, priority:high | **YES** — No maintainer response or assignment visible. High-priority security issue with clear implementation path. Needs triage. |
| **[PR #3192](https://github.com/sipeed/picoclaw/pull/3192)** — Bump alpine base images | 2026-06-27 | 2026-07-05 | Open | **LOW** — Simple dependency update, should be mergeable. |
| **[PR #3191](https://github.com/sipeed/picoclaw/pull/3191)** — Remove duplicate .gitignore entry | 2026-06-27 | 2026-07-05 | Open | **LOW** — Trivial cleanup. |
| **[PR #3222](https://github.com/sipeed/picoclaw/pull/3222)** — DeltaChat refactor | 2026-07-03 | 2026-07-05 | Open | **MEDIUM** — Large change (-320 LOC), needs thorough review. Could introduce regressions in DeltaChat integration. |

**Most critical item needing maintainer attention:** **Issue #3088** (vodozemac migration). With 2 upvotes, 6 comments, and a `priority: high` label, it represents the most impactful community-identified need. Assigning a maintainer and providing a timeline would significantly improve community trust.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

**NanoClaw Project Digest — 2026-07-06**

---

### 1. Today's Overview
NanoClaw shows a *recovery/consolidation* phase today with no new issues filed but a flurry of merged PRs that indicate significant feature completion. Although 0 issues were updated in the last 24 hours, 5 pull requests saw activity, with 3 merged/closed across several infrastructure and skills areas. The lack of new bug reports suggests recent master is stable, while the merged PRs point to the near-fortification of agent templating, guardrails, and channel formatting. Project activity today is **low in volume but high in impact**, with key long-running PRs finally reaching resolution.

---

### 2. Releases
- **No new releases** were cut in the last 24 hours. The last tagged release likely remains the prior version. Users tracking `master` should note no migration notes are required today.

---

### 3. Project Progress
Three pull requests were merged/closed today, advancing the project forward:

- **[#2908 — feat(codex): persona prepend + git-independent skill discovery for template agents](https://github.com/nanocoai/nanoclaw/pull/2908)** (merged, 4 files, +122/−5). This finalizes the agent-templates feature under the Codex provider. Key changes: persona prepending for template agents and provider-agnostic skill mirroring to `$HOME/.agents/skills` for Claude Codex integration. This is the infrastructure companion to the setup wizard in #2909.
- **[#2726 — feat: add /add-guardrails skill — per-agent-group input/output guardrails](https://github.com/nanocoai/nanoclaw/pull/2726)** (merged). Introduces deterministic regex/keyphrase rules for prompt-injection blocking and credential-leak detection, with `block`/`flag` actions, chat alerts, and a quarantine audit trail. This is a significant security hardening move for multi-agent deployments.
- **[#2766 — feat(channels): add .format-lint-off](https://github.com/nanocoai/nanoclaw/pull/2766)** (merged). A smaller but quality-of-life improvement allowing channel formatting linting to be disabled per-message or per-channel.

**Still open and high-signal:**  
- **[#2909 — feat(setup): template setup flow in the wizard and first-agent stamping](https://github.com/nanocoai/nanoclaw/pull/2909)** (still open, updated 2 days ago). This is the user-facing half of the template system, adding the interactive setup-wizard question *"How should we create your first agent?"*. Expect merge within ~48 hours.
- **[#2949 — [OPEN] feat(skill): /add-litellm — minimal model router](https://github.com/nanocoai/nanoclaw/pull/2949)** (still open, updated today). Adds a lightweight multi-model router supporting local servers and optional cloud endpoints. Still under review.

---

### 4. Community Hot Topics
There are **zero comments** on any of today's updated issues or PRs, and no reactions received. This suggests the community is either small, satisfied, or focused on silent usage. The **most significant items by strategic weight** are:

- **[#2949 — /add-litellm skill](https://github.com/nanocoai/nanoclaw/pull/2949)**: This is a utility skill that connects NanoClaw to LiteLLM, enabling dynamic model routing across providers. Although no comments exist, this addresses a **latent need for cost-optimized multi-provider access**—users likely want to mix local (Ollama/vLLM) and cloud (OpenAI/Anthropic) endpoints without hardcoding. The PR's silence may indicate the feature is self-evidently useful.
- **[#2909 — Setup wizard templates](https://github.com/nanocoai/nanoclaw/pull/2909)**: Though no community feedback is recorded, this PR directly lowers the onboarding barrier. Its delay in merging (last update July 5) suggests careful review on UX flow and edge cases.

**Underlying need pattern:** The community broadly wants *batteries-included onboarding* (templates, wizard) and *flexible model backend selection* (LiteLLM). Both are infrastructure plays rather than flashy features.

---

### 5. Bugs & Stability
- **No bugs, crashes, or regressions reported or fixed in the last 24 hours.**  
- The **/** `add-guardrails`** PR (#2726) that was merged directly addresses a security-class concern: credential leakage and prompt injection. This is a *proactive stability* feature rather than a reactive fix, but increases platform resilience.
- The **format-lint-off** (#2766) channel fix indirectly resolves any frustration with over-aggressive formatting on sensitive channels.

**Ranked severity:** No active bugs at any severity level.

---

### 6. Feature Requests & Roadmap Signals
No formal feature requests were filed as issues today. However, the PR pipeline signals clear roadmap intent:

**Likely next-version features (within 1-2 releases):**
1. **Agent Templates + Setup Wizard** — #2909 is the last piece; once merged, new users can bootstrap via a guided wizard rather than manual config.
2. **LiteLLM Integration** — #2949, if merged, will make NanoClaw a viable frontend for multi-model deployments (local + cloud), aligning with industry trends toward model-agnostic agent frameworks.
3. **Per-agent-group Guardrails** — Already merged (#2726), this will appear in the next release changelog as a security highlight.

**Predictable unspoken requests:** Users may soon request *template marketplaces* (import/export templates) and *guardrail rule libraries* (pre-built regexes for common injection patterns). No evidence of demand today, but logical next steps.

---

### 7. User Feedback Summary
**No direct user feedback (issues, comments, reactions) was captured today.** This is a data gap, likely indicating one of:
- The community is small but stable, preferring to use the tool without engaging on GitHub.
- Users are still adopting recent features (templates, guardrails) and have not yet formed complaints.
- The low issue count across the project (0 open issues) suggests a relatively *satisfied or low-engagement* user base.

**Pain points inferred from PRs:**
- Onboarding friction (addressed by #2909's wizard).
- Lack of model provider flexibility (addressed by #2949's LiteLLM router).
- Security concerns in multi-agent environments (addressed by #2726's guardrails).

No dissatisfaction signals detected.

---

### 8. Backlog Watch
- **There are zero open issues** in the project repository at this time — a highly unusual and positive signal for project health.  
- **Open PRs:**  
  - **[#2949](https://github.com/nanocoai/nanoclaw/pull/2949)** (open since July 4, last activity today) — Needs maintainer review for merge or revision.  
  - **[#2909](https://github.com/nanocoai/nanoclaw/pull/2909)** (open since July 2, last activity July 5) — The most impactful open PR; likely in final review. Could benefit from a maintainer's explicit approval or change requests.

**Recommendation:** Maintainers should prioritize closure of #2909 (setup wizard) to unblock the template feature timeline, and schedule a review for #2949 to avoid feature staleness.

---

**Overall Health Assessment:** 🟢 **Stable & progressing.** No regressions, no open bugs, and three high-value features merged in the last 24 hours. The only risk is lingering open PRs that may introduce entropy if not resolved soon. Community engagement is low but not alarming.

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

# IronClaw Project Digest — 2026-07-06

## Today's Overview

Project activity is **high** with 27 pull requests updated in the last 24 hours (22 open, 5 merged/closed) and 4 issues updated. The team is executing on a coordinated **Reborn Slack OAuth migration** across multiple stacked PRs (#5645, #5646, closed #5604, closed #5626), alongside production-hardening efforts in bridging tool security (#5659), agent loop robustness (#5666, #5663), and error handling (#5662). A new coverage-tracking issue for v1-only crates (#5657) signals ongoing architectural measurement discipline. A long-standing nightly E2E failure (#4108, open since May 27) remains unresolved but has seen recent updates.

## Releases

**No new releases** in the last 24 hours. The pending `0.29.1`+ release (PR #5598, open since July 3) would deliver breaking changes across `ironclaw_common` (0.4.2→0.5.0), `ironclaw_skills` (0.3.0→0.4.0), and the main `ironclaw` crate (0.24.0→0.29.1) — likely blocked until the Slack OAuth migration stack and the tool-disclosure fix land.

## Project Progress

**Five PRs merged/closed today:**
- **#5604** (CLOSED, XL) — BenKurrek: Removed Slack pairing flow in favor of personal OAuth setup across channels, CLI, tools, and CI. This is the foundational stack PR that **deleted the old pairing-code artifacts** and wired Slack OAuth as an installable channel entrypoint.
- **#5626** (CLOSED, XL) — ilblackdragon: Manifest-driven Slack ingress routes. **Deleted Rust policy literals** for `slack.events`/`slack.commands`; these routes are now declared as data in the extension manifest.
- **#5667** (CLOSED, XL, draft) — serrrfirat: Optimized hosted Postgres turn-state latency with RootFilesystem-backed append/row stores. **Note: draft was closed** ("I will chop this up") — will be broken into smaller PRs.
- **#5637** (CLOSED) — henrypark133: Added wiring-parity tripwire to assert harness runtime shape matches production local-dev composition.
- **#4002** (CLOSED, L) — dependabot: Bulk update of 16 GitHub Actions dependencies.

**Key active features advancing:**
- **Slack OAuth migration stack (3/4 and 4/4):** #5645 (XL, swapping pairing for personal OAuth, 121 files) and #5646 (M, rejecting legacy `[slack]` config fields at serve startup) remain open and review-ready.
- **Tool-call argument repair:** #5665 (XL) fixes provider-corrupted XML tool-call arguments from OpenAI-compatible providers.
- **Repetition breaker:** #5666 (XL, draft) breaks identical tool-call loops in the v1 agentic loop with corrective nudges.
- **Prompt-context hardening:** #5663 (L) adds compaction truncation, drop observability, and opt-in instruction budget.
- **Error surfacing:** #5662 (L) converts 90 `let _ = <fallible>` discard sites into explicit error handling.

## Community Hot Topics

**Most active issues (by recency/engagement):**
1. **#5647** — `[OPEN]` Bridged tool disclosure + narrowed capability allowlist strips bridge meta-tools (latent). Filed by henrypark133, 1 comment, **fix PR #5659 already submitted**. This is a security-class issue where the `CapabilitySurfaceProfileFilter` strips synthetic `ironclaw.*` bridge capability IDs from narrowed-allowlist callers crossing the 32-tool threshold.

2. **#4108** — `[OPEN]` Nightly E2E failed (since May 27, updated July 5). Bot-reported recurring E2E failure with no assignee. No comments — likely the team is treating this as a known intermittent infra issue.

3. **#5657** — `[OPEN]` Coverage scope: v1-only crates exempted from Reborn coverage denominator. Tracking issue for 4 crates exempted from coverage measurements.

**Most active PRs:**
- **#5662** (L, refactor: 90 sites) — ilblackdragon: Surfaces best-effort failures. High signal for production reliability.
- **#5665** (XL, fix provider tool-call corruption) — abbyshekit: Addresses real user-facing issues with OpenAI-compatible providers mangling tool call arguments.
- **#5645** (XL, Slack OAuth swap) — BenKurrek: Core architectural change with 121 files, multiple scopes, high review surface area.

## Bugs & Stability

**Ranked by severity:**

1. **🔴 [HIGH] #5647 — Bridge meta-tools stripped under narrowed allowlists** (latent severity) — When bridged tool disclosure defers a >32-tool catalog to bridge meta-tools, the synthetic capability IDs are **not part of any granted capability set**, causing tools to disappear. **Fix exists:** PR #5659 (released as PRODUCTION CHANGE) applies `CapabilitySurfaceProfileFilter` hardening with regression tests.

2. **🔴 [HIGH] #4108 — Nightly E2E failure** (ongoing since May 27) — Scheduled run fails with no root cause identified or assigned. Last updated July 5. No fix PR — the team appears to be accepting this as infrastructure noise.

3. **🟡 [MEDIUM] #5665 — Provider-corrupted tool-call arguments** — OpenAI-compatible providers (OpenRouter, NEAR AI Cloud) leak native XML tool-call format through the OpenAI compatibility layer. Fix in PR #5665.

4. **🟢 [LOW] #5661 — InMemory store parity gap** — CAS-contention + discard-tombstone coverage reveals a gap where `InMemoryTurnStateStore` doesn't match `FilesystemTurnStateStore` behavior under contention. Fix in PR #5661 (S, risk low).

5. **🟢 [LOW] #5663 — Silent context loss** — Prompt-context assembly could truncate silently; fix adds compaction truncation guards.

## Feature Requests & Roadmap Signals

**No explicit user feature requests** in the last 24 hours. Roadmap direction is clearly defined by the active PR stack:

- **Reborn Slack OAuth migration** (PRs #5645, #5646, closed #5604, #5626) — This is the dominant effort, likely targeting the next release (0.29.x). Predict delivery in **next 1-2 sprints**.
- **Bridged tool disclosure hardening** (#5659) — Security improvement likely to gate the next release.
- **Agent loop repetition breaker** (#5666, draft) — v1 agentic loop improvement, distinct from Reborn stop-condition work (#5287).
- **Prompt context assembly hardening** (#5663) — Three reliability improvements for prompt construction.
- **Benchmark narrower Reborn crate targets** (#5648) — CI optimization signals the team is managing compile-time regressions from the growing Reborn crate surface.

**Inferred roadmap priorities:** (1) Slack OAuth go-live, (2) Bridged tool security, (3) Agent loop robustness, (4) CI efficiency.

## User Feedback Summary

**No direct user-pain-point tracking** in this dataset (all issues/PRs are filed by core contributors or bots). However, inferred user-relevant signals:

- **Satisfaction driver:** The Slack OAuth migration (PR #5645) eliminates the pairing-code flow, a **user friction point** in the Slack integration.
- **Pain point addressed:** Provider-corrupted tool calls (#5665) directly affects users of OpenAI-compatible providers (OpenRouter, NEAR AI Cloud) — tool call arguments arriving truncated or with leaked XML tags.
- **Quality concern:** The long-running nightly E2E failure (#4108) may erode confidence in automated testing, though no user-facing regressions have been reported from it.
- **Developer UX:** The 90-site error surfacing (#5662) and coverage improvements (#5657, #5637) signal a team investing in **internal quality infrastructure** that will indirectly benefit users through fewer silent failures.

## Backlog Watch

**Items needing maintainer attention:**

1. **⚠️ #4108 — Nightly E2E failure** (open since May 27, 40 days, last updated July 5) — No assignee, no fix attempts visible. The "Full E2E / E2E (features)" job fails nightly. **Risk:** potential blind spot if this masks real regressions.

2. **#4032 — WASM dependency updates** (open since May 25) — Bumping `wit-component` 0.245.1→0.252.0 and `wit-parser`. Age suggests low priority or merge conflicts. No blocking concerns, but dependency hygiene matters.

3. **#5114 — Tokio ecosystem updates** (open since June 21) — Bumping `tokio-tungstenite`, `tokio-postgres-rustls`, `tower-http`, `hyper`. These are **security-relevant** dependency updates — prolonged open status could mean integration complexity. Worth maintainer review.

4. **#5550 — Bulk dependency update** (open since July 2) — 13 updates including `agent-client-protocol` 0.10.4→1.0.1 (major semver bump). The `agent-client-protocol` jump is notable — if it lands, may force API adaptations across the codebase.

---

*Generated from IronClaw GitHub activity for 2026-07-06. Data source: github.com/nearai/ironclaw.*

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

Here is the **LobsterAI Project Digest** for **2026-07-06**, based on the provided GitHub activity data.

---

### 1. Today's Overview
The project shows **very low activity** over the past 24 hours, with no new issues or releases. A single PR was quickly merged, indicating ongoing refinement of the UI/UX for task management. A significant "stale" PR (#1349), which adds real API validation for the POPO instant messaging connectivity test, remains open after three months, suggesting a potential bottleneck in maintenance or review. Overall, the project appears to be in a **maintenance and polish phase** rather than rapid development.

### 2. Releases
**None.** No new versions or tags were created today.

### 3. Project Progress
One PR was **merged/closed** today, advancing the project's frontend:

- **#2273 [CLOSED]** (Author: fisherdaddy): **feat(scheduledTask): task list card redesign with status chip, toggle, search, and optimistic UI feedback.** This update improves the renderer, main process, and OpenClaw areas by refreshing the task list UI. Key enhancements include visual status chips, search functionality, a toggle feature, and optimistic UI feedback for a smoother user experience.
    - **Link:** [PR #2273](https://github.com/netease-youdao/LobsterAI/pull/2273)

### 4. Community Hot Topics
There were zero comments or reactions across all open items today. The most notable discussion point remains the **persistent staleness of PR #1349**, which was updated yesterday but has no new comments:

- **#1349 [OPEN]** (Author: gongzhi-netease): **fix(im): add real API validation for POPO connectivity test.** This PR addresses a core quality issue where connectivity tests falsely passed even with invalid credentials. Despite being open since April 2nd and marked as stale, it was updated yesterday, indicating maintainers are aware but have not merged it.
    - **Link:** [PR #1349](https://github.com/netease-youdao/LobsterAI/pull/1349)
    - **Underlying Analysis:** The community (or internal team) has likely identified this as a critical *trust* issue. Users setting up IM integrations need immediate confidence that their credentials are correct; a false positive leads to downstream silent failures. The long delay suggests a complex dependency or a lack of priority for IM integrations.

### 5. Bugs & Stability
**No new bugs, crashes, or regressions** were reported today.

However, the unresolved fix in **PR #1349** represents a **High-severity** *logic bug* that remains unaddressed: the POPO connectivity test is currently a "hollow" check, always returning success. While no fix for other bugs was released, this bug fix itself is already written but stalled.

### 6. Feature Requests & Roadmap Signals
**No new feature requests** were submitted today.

**Roadmap Signal:** The merged PR #2273 signals that the team is actively working on **UI/UX modernization** for the scheduled task module. Expect further refinements to the task management interface (such as more advanced filtering or drag-and-drop reordering) in the next minor version.

### 7. User Feedback Summary
**No explicit user feedback** was recorded in issues or PR comments today.

**Derived Pain Point:** The stalled PR #1349 suggests a latent user pain point: **configuration validation**. Users (or internal testers) likely express frustration when entering invalid IM credentials results in a false "success" message. The lack of feedback also implies that users might have stopped reporting this issue, having either worked around it or abandoned the feature.

### 8. Backlog Watch
**One critical item** requires immediate maintainer attention:

- **PR #1349 [OPEN] – `fix(im): add real API validation for POPO connectivity test`**
    - **Age:** 95 days (since Apr 2, 2026)
    - **Risk:** This fix is essential for operational reliability. Allowing a known bug that validates credentials incorrectly to remain in the codebase degrades user trust in the entire connectivity subsystem. If this is not an API constraint issue, it should be prioritized for merge.
    - **Link:** [PR #1349](https://github.com/netease-youdao/LobsterAI/pull/1349)

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

# CoPaw Project Digest — 2026-07-06

## Today's Overview

CoPaw maintained a high level of development activity today with **12 open issues** and **5 open pull requests** updated in the last 24 hours, all remaining open with no closures or merges. The issue queue is dominated by **bug reports (9 of 12)** and **2 enhancement requests**, reflecting a period of active user testing and rapid feedback after the recent v1.1.12.post2 release. The PR queue shows focused backend and frontend fixes from both returning and first-time contributors, though the absence of any merged PRs today suggests maintainers are in a review-and-test cycle rather than a merge phase. No new releases were published. Overall, the project appears in a **stabilization and bug-fixing sprint**, with strong community engagement in reporting edge cases and proposing targeted fixes.

## Releases

**No new releases** were published today. The latest available version remains **v1.1.12.post2**.

---

## Project Progress

**No pull requests were merged or closed today.** All 5 open PRs are still under review:

- **PR #5786** *(yutai78786)* — A bundled fix addressing three identified issues: cross-provider model ID matching (#5784), missing Azure provider ID in provider form (#5709), and translation key typo (#5773). This PR is the most likely candidate for near-term merge.
- **PR #5792** *(Osamaali313, first-time contributor)* — Fixes agent message sanitation logic that incorrectly drops valid self-paired tool messages in AgentScope 2.0.
- **PR #5791** *(Osamaali313, first-time contributor)* — Fixes a display bug in the `formatCompact` utility where numbers near the top of a magnitude band (e.g., 999,999) render as non-compact "1000K" instead of "1M".
- **PR #5783** *(wananing)* — Fixes cron state API returning UTC instead of the job’s configured timezone (#5779).
- **PR #5777** *(jinliyl)* — Adds per-session auto-memory turn state tracking to `BaseMemoryManager` and middleware, improving memory management granularity.

**No feature advancements were completed today**, as all PRs remain open.

---

## Community Hot Topics

*Most active discussions based on comment count (3 comments each):*

1. **Issue #5770** — *[question] 希望V2.0的正式版推出之后，能够惊艳所有人！*  
   *Author: vipcys001-bot* | [Link](https://github.com/agentscope-ai/QwenPaw/issues/5770)  
   A user expresses anticipation for the upcoming v2.0 formal release. The 3 comments suggest team/community engagement around release roadmap expectations.

2. **Issue #5785** — *[Feature]: 我用coding模式，没法选隐藏文件夹*  
   *Author: ljw20180420* | [Link](https://github.com/agentscope-ai/QwenPaw/issues/5785)  
   A practical UX limitation: the coding mode file selector cannot pick hidden dotfiles. 3 comments indicate active troubleshooting.

3. **Issue #5784** — *[Bug]: 前端压缩阈值显示错误：同名模型跨 provider 时未校验 provider_id*  
   *Author: y0umu* | [Link](https://github.com/agentscope-ai/QwenPaw/issues/5784)  
   A clear bug found via LLM-assisted code reading, with a fix already submitted in PR #5786. 3 comments show team validation.

4. **Issue #5779** — *[Bug]: cron state API returns UTC time instead of job's configured timezone*  
   *Author: feng183043996* | [Link](https://github.com/agentscope-ai/QwenPaw/issues/5779)  
   Identified hardcoded UTC issue in cron manager with downstream fix in PR #5783.

**Analysis:** Community engagement reflects a **mature user base performing systematic testing** — issues are well-documented, often with root cause analysis and supporting PRs. The cross-provider model configuration (#5784) and cron timezone (#5779) are the most technically active topics.

---

## Bugs & Stability

*Bugs ranked by severity (High → Low):*

| Severity | Issue | Description | Status | Fix PR |
|----------|-------|-------------|--------|--------|
| **Critical** | #5789 | Context compression crashes when model output exceeds JSON Schema `maxLength` (200 char limit on `next_steps`) | Open, no fix PR | — |
| **High** | #5790 | Loading animation does not disappear after Agent response completes — persistent spinner in chat UI | Open, no fix PR | — |
| **High** | #5757 | Lark/Feishu IM channel not replying to consecutive messages; first message works, subsequent messages ignored | Open since Jul 3, 2 comments | — |
| **Medium** | #5787 | Mobile web UI bottom content truncated on all pages; buttons outside screen boundary | Open, no fix PR | — |
| **Medium** | #5782 | Google Gemini embedding via OpenAI-compatible endpoint returns `index=None`, silently disabling vector search (fallback to keyword search) | Open, no fix PR | — |
| **Medium** | #5788 | Skills list pagination broken: progressive rendering only shows 20 items; scroll-to-load-more fails due to CSS overflow | Open, no fix PR | — |
| **Medium** | #5781 | Offline Code mode cannot preview files because it requires online resource download | Open, no fix PR | — |
| **Low** | #5785 | Coding mode file selector cannot pick hidden dotfiles | Open, enhancement filed as bug | — |
| **Low** | #5784 | Frontend compression threshold displays wrong value across providers (same model name, different providers) | Open, fix in PR #5786 | ✅ #5786 |
| **Low** | #5779 | Cron state API returns UTC instead of configured timezone | Open, fix in PR #5783 | ✅ #5783 |

**Key stability concern:** Issue #5789 (context compression crash on JSON Schema validation) is the most severe — it can cause complete agent pipeline failure during memory compression. No fix PR exists yet. Issue #5790 (persistent loading spinner) degrades user experience but is cosmetic.

---

## Feature Requests & Roadmap Signals

1. **#5780** — *Multi-user account management for team use* (Enhancement, 1 comment)  
   *Author: 24krmb* | [Link](https://github.com/agentscope-ai/QwenPaw/issues/5780)  
   User requests proper team member management with role-based access control. Currently only single Bot account auth through IM channels. This is a **significant architectural feature** likely targeted for v2.0.

2. **#5785** — *Coding mode hidden folder selection* (Filed as Feature/Enhancement)  
   *Author: ljw20180420* | [Link](https://github.com/agentscope-ai/QwenPaw/issues/5785)  
   User needs the ability to select `.`-prefixed hidden directories in coding mode file picker.

3. **#5770** — *Anticipation for v2.0 formal release* (Question)  
   *Author: vipcys001-bot* | [Link](https://github.com/agentscope-ai/QwenPaw/issues/5770)  
   Community enthusiasm for the next major version suggests v2.0 is widely anticipated and likely in active development.

**Roadmap prediction:** Multi-user management (#5780) and the auto-memory state tracking (PR #5777) are v2.0-scale features. The current v1.1.x series appears focused on stabilizing provider compatibility and fixing regressions before the major release.

---

## User Feedback Summary

**Pain points (most frequently reported):**

- **IM channel instability** (#5757): Consecutive messages to Lark/Feishu bot go unanswered after the first reply — a critical issue for team deployments relying on chat interfaces.
- **Mobile responsiveness** (#5787): UI truncation on all pages for phone/tablet users, directly impacting mobile-first workflows.
- **Offline functionality gaps** (#5781): Code mode’s dependency on online resource downloads prevents fully offline operation, a barrier for users in restricted environments.
- **Configuration confusion** (#5784, #5782): Cross-provider model settings misbehave, and Google Gemini embeddings silently fail with no user notification.
- **Pagination/loading issues** (#5788, #5790): Skills list fails to load more items; chat UI shows persistent spinner — both degrade perceived performance.

**Satisfaction signals:**

- Users are **proactively reporting bugs with root cause analysis** (e.g., #5784 discovered via LLM-assisted code review, #5779 with exact line references), indicating a technically skilled and invested community.
- The enthusiasm for v2.0 (#5770) and the presence of first-time contributors (PR #5791, #5792) signal strong **community health and growth**.

**Developer sentiment:** The bug volume suggests v1.1.12.post2 was deployed with several edge cases, but the rapid creation of corresponding fix PRs (#5786, #5783) shows the team is responsive.

---

## Backlog Watch

*Issues/PRs requiring maintainer attention:*

| Item | Issue/PR | Age | Reason for Watch |
|------|----------|-----|------------------|
| **#5757** | Lark/Feishu not replying | **3 days** (since Jul 3) | High-severity IM channel bug, no fix PR, affects production deployments |
| **#5789** | Context compression JSON Schema crash | 1 day | Critical pipeline failure, no fix PR identified |
| **#5792** | First-time contributor PR (tool message sanitation) | 1 day | Needs maintainer review to encourage new contributor retention |
| **#5791** | First-time contributor PR (formatCompact rounding) | 1 day | Same — both PRs by Osamaali313, timely review signals community health |
| **#5777** | Auto-memory turn state management | 2 days | Architectural feature PR, likely v2.0 candidate, needs architectural review |

**No long-standing unanswered issues** were identified — all items are less than 4 days old, suggesting healthy maintainer attention.

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

Here is the ZeroClaw project digest for July 6, 2026.

---

### ZeroClaw Project Digest
**Date:** 2026-07-06
**Data Snapshot:** July 5-6, 2026

### 1. Today's Overview

ZeroClaw is undergoing a period of intense architectural evolution, with **23 issues** and **50 pull requests** updated in the last 24 hours. The project is clearly executing on two major, high-risk roadmap items: a comprehensive **Goal Mode** feature and the finalization of a **Standard Operating Procedure (SOP) authoring surface**. While feature work is aggressive, the volume of open PRs (44) and a series of P1 (critical) bugs suggests the development velocity is outpacing the stability cycle. The community is actively engaged in shaping the core architecture, debating RFCs on making the core leaner and proposing new compatibility layers.

### 2. Releases

**No new releases were published today.** The project appears to be between release cycles, with efforts concentrated on landing major feature branches (Goal Mode, SOP Authoring) and addressing a growing bug backlog.

### 3. Project Progress

**6 pull requests were merged or closed today**, indicating a modest rate of feature integration. Key landed or active developments include:

- **Bug Fixes & Security (Merged/Closed):**
    - **fix(gateway): reject empty bearer token** ([PR #8727](https://github.com/zeroclaw-labs/zeroclaw/pull/8727)): A defense-in-depth fix to reject empty authentication tokens.
    - **fix(zerocode): make Code help and keybindings reachable** ([PR #8705](https://github.com/zeroclaw-labs/zeroclaw/pull/8705)): UX improvements for the zerocode interface.
    - **fix(runtime): enforce leading user-turn invariant** ([PR #8696](https://github.com/zeroclaw-labs/zeroclaw/pull/8696)): A critical fix ensuring conversation structures are valid before being sent to providers, preventing hard-to-debug failures.
    - **fix(mcp): list bundled MCP tools on dashboard** ([PR #8703](https://github.com/zeroclaw-labs/zeroclaw/pull/8703)): Fixes a gap where MCP tools from bundles were invisible to users.

- **Active Features (Key Open PRs):**
    - **SOP Authoring Surface** ([PR #8736](https://github.com/zeroclaw-labs/zeroclaw/issues/8736)): A related tracker confirms a full authoring stack is in-progress, including a node-graph editor, live overlays, and a validation engine.
    - **Inkbox Channel** ([PR #8384](https://github.com/zeroclaw-labs/zeroclaw/pull/8384)): A large new native channel for Email/SMS/Voice/iMessage is under active development, indicating a push towards multi-modal, always-on agent identities.

### 4. Community Hot Topics

The most active discussions reveal a community focused on defining the project's long-term architecture and improving developer/user experience.

- **Architectural Direction & RFCs:**
    - **Splitting the Goal Mode Implementation** ([Issue #8681](https://github.com/zeroclaw-labs/zeroclaw/issues/8681)): This high-complexity tracker (8 comments) coordinates the breaking-down of the goal-mode feature. This is a purely internal discussion about how to structure a major feature release.
    - **Preferring a Lighter Core** ([Issue #6165](https://github.com/zeroclaw-labs/zeroclaw/issues/6165)): An ongoing RFC (8 comments) to define a stricter boundary for ZeroClaw's core by moving integrations to MCP servers or plugins. This signals a community interest in modularity and reducing the project's maintenance surface.
    - **OpenAI Compatibility Adapter** ([Issue #8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603)): An RFC for adding an OpenAI Chat Completions compatible API endpoint. The rationale is strong: enabling integrations with popular tools like Open WebUI and LobeChat. This is a strong signal of demand for ZeroClaw to become a drop-in replacement for other agent hosting platforms.

- **Feature Discussions:**
    - **Schema V4 Breaking Cut** ([Issue #8310](https://github.com/zeroclaw-labs/zeroclaw/issues/8310)): A proposal to clean up the config schema by removing deprecated settings. This indicates a push towards simplification and breaking changes on the horizon.

### 5. Bugs & Stability

The bug tracker shows a serious stability situation, with two **Priority 1 (P1)** bugs reported. While the count of new bugs is moderate, the severity is high.

- **P1 - Workflow Blocked / Critical:**
    - **`browser_open` hangs agent indefinitely** ([Issue #8560](https://github.com/zeroclaw-labs/zeroclaw/issues/8560)): A critical bug where agents freeze if the browser launcher fails (e.g., no display). It also mentions similar issues with TTS and FFmpeg, suggesting a systemic problem with subprocess management in headless environments. **No fix PR is open.**
    - **Stdio MCP servers become zombie processes** ([Issue #8731](https://github.com/zeroclaw-labs/zeroclaw/issues/8731)): A critical resource-management bug where MCP server processes are not cleaned up, leading to "zombie" processes that degrade system performance. This is dangerous for long-running daemons. **No fix PR is open.**
    - **`zeroclaw config init` ships broken config** ([Issue #8718](https://github.com/zeroclaw-labs/zeroclaw/issues/8718)): A high-impact onboarding bug where the default config template is rejected by the daemon, silently disabling voice transcription. This is a very poor first-user experience. **No fix PR is open.**

- **P2 - Degraded Behavior:**
    - **Runtime Policy for OTel Content** ([Issue #8462](https://github.com/zeroclaw-labs/zeroclaw/issues/8462)): A closed RFC that highlights a pending concern: exposing sensitive LLM/tool content to OpenTelemetry backends without a runtime policy to filter it.

### 6. Feature Requests & Roadmap Signals

The most significant roadmap signal is the plan for a **Schema V4 breaking change** ([Issue #8310](https://github.com/zeroclaw-labs/zeroclaw/issues/8310)), which aims to remove "dead, inert, SaaS, and CLI-wrapper config surface." This suggests the next major release will have a more streamlined, but disruptive, configuration model.

Other strong signals for near-term features include:
- **OpenAI Compatible API** ([Issue #8603](https://github.com/zeroclaw-labs/zeroclaw/issues/8603)): Likely a top candidate for the next version due to clear demand and potential to attract new users.
- **SOP Routing Enhancement** ([Issue #8719](https://github.com/zeroclaw-labs/zeroclaw/issues/8719)): A request to allow an SOP to continue to the next step when a `when` condition is false, enabling "multi-phase" workflows. This is a minor but powerful ergonomic improvement for the new SOP system.

### 7. User Feedback Summary

Real user pain is centered around configuration and reliability:

- **Frustration with Onboarding:** A user on Android/Termux ([Issue #7911](https://github.com/zeroclaw-labs/zeroclaw/issues/7911)) is blocked by a binary detection failure. The situation is exacerbated by the silent-transcription-breaking default config ([Issue #8718](https://github.com/zeroclaw-labs/zeroclaw/issues/8718)), creating a hostile setup experience.
- **Tooling for China:** A user ([PR #8737](https://github.com/zeroclaw-labs/zeroclaw/pull/8737)) has submitted a PR to add a Chinese-compatible web search provider (Bocha AI), as all current options are network-blocked in mainland China. This highlights a need for geo-aware feature design.
- **Need for Finer Configuration:** A user is struggling to disable caching for a specific Bedrock model ([Issue #8720](https://github.com/zeroclaw-labs/zeroclaw/issues/8720)), indicating that users require more granular, per-provider controls beyond what is currently available.

### 8. Backlog Watch

Several important items require maintainer attention to prevent stagnation:

- **Android Termux Setup** ([Issue #7911](https://github.com/zeroclaw-labs/zeroclaw/issues/7911)): Open for 18 days and marked `needs-author-action`. A user trying to install on Android is stuck. This is an important mobile use case that is currently orphaned.
- **Security Audit Skipped Skills** ([Issue #7861](https://github.com/zeroclaw-labs/zeroclaw/issues/7861)): Closed, but the feature request for `zeroclaw skills list` to show security-skipped skills is valuable for user awareness and safety. The closeness to the current security push (e.g., leak detector bug #8722) makes it relevant.
- **WASM Plugin Lifecycle Hooks** ([Issue #7822](https://github.com/zeroclaw-labs/zeroclaw/issues/7822)): An RFC that has been open since June 17th. Subscribing WASM plugins to lifecycle events is a powerful feature for the extensibility story, and its languishing suggests it is not a current priority.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*