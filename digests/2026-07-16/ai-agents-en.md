# OpenClaw Ecosystem Digest 2026-07-16

> Issues: 467 | PRs: 500 | Projects covered: 13 | Generated: 2026-07-16 01:46 UTC

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

# OpenClaw Project Digest — 2026-07-16

## 1. Today's Overview
OpenClaw shows **sustained high-velocity development** with **467 issues updated (301 open, 166 closed)** and **500 PRs updated (322 open, 178 merged/closed)** in the last 24 hours — indicating a large and active contributor base. A new release **v2026.7.2-beta.1** shipped today, featuring **remote coding sessions**, cloud worker support, and terminal-based session resumption. Despite this momentum, the project is grappling with a **critical stability crisis**: multiple P0/P1 startup crash-loop bugs (issues #107220, #107227, #107694, #107727) affecting the gateway's **2026.7.1 → 2026.7.2 upgrade path**, particularly around legacy state migration conflicts. The community is highly engaged, with long-running enhancement requests (notably #75 for Linux/Windows apps, 113 comments) and widespread frustration around session-state corruption and auth provider failures.

## 2. Releases
**New: v2026.7.2-beta.1** (openclaw 2026.7.2-beta.1)

**Highlights:**
- **Remote coding sessions**: Run Control UI sessions on cloud workers; open Codex and Claude catalog sessions in terminals on their owning hosts; resume OpenCode and Pi sessions directly in a terminal.
- **Native automation and nodes**: Expanded support for cloud-worker-based agent execution.
- No explicit breaking changes or migration notes were published in the release description (truncated in data).

**Context**: This release appears to address several of the session-resumption and remote-workflow friction points raised in earlier community feedback (e.g., issue #91009, #96834). However, it ships against the backdrop of **at least six P0 crash-loop bugs** tied to 2026.7.1's state migration guard, which remain open.

## 3. Project Progress
24 PRs were merged or closed today (via the data set's `closed` status on updates from 2026-07-16). Notable examples:

| PR | Scope | Description |
|---|---|---|
| [#108549](https://openclaw/openclaw/pull/108549) | CI/Extensions | `fix(ci): restore strict plugin deadcode check` — Maintainer fix (steipete) |
| [#108547](https://openclaw/openclaw/pull/108547) | Anthropic | `refactor(deadcode): tighten Anthropic extension roots` — Removes unused exports |
| [#108530](https://openclaw/openclaw/pull/108530) | Plugins | `fix(plugins): handle multi-element npm view arrays in metadata normalizer` |
| [#108268](https://openclaw/openclaw/pull/108268) | TUI | `fix(tui): preserve emoji in split local shell output` |
| [#107388](https://openclaw/openclaw/pull/107388) | Codex/Delivery | `fix(codex): keep omitted-final source replies from releasing the turn` — Blocks premature turn release in `message_tool_only` mode |
| [#103076](https://openclaw/openclaw/issues/103076) | State Migration | Closed as bug — `additional legacy-state migration sources still block gateway startup after #102780` |
| [#107227](https://openclaw/openclaw/issues/107227) | Gateway | Closed — `startup-migration gate is fatal, but repair path doesn't resolve conflict` |
| [#107330](https://openclaw/openclaw/issues/107330) | Update | Closed — `OpenClaw Update 2026.7.1 Crash` on Windows |

**Key advancement**: The state-migration crash-loop saga is being aggressively patched, with multiple P0 issues closed today. The autonomous agent loop PR [#108206](https://openclaw/openclaw/pull/108206) (`feat(loop): implement autonomous agent loop (/loop) with token budget guard`) is a significant new capability under review.

## 4. Community Hot Topics
The most active and resonant discussions reveal deep user frustration with **session reliability** and **auth provider failures**.

| Issue/PR | Comments | 👍 | Summary |
|---|---|---|---|
| [#75](https://openclaw/openclaw/issues/75) — **Linux/Windows Clawdbot Apps** | 113 | 81 | Longest-running feature request (since Jan 2026). Users strongly desire parity with macOS/iOS. Persistent "P2, help wanted" — no maintainer commitment yet. |
| [#104721](https://openclaw/openclaw/issues/104721) — **All tool results return "(see attached image)" placeholder** | 17 | 1 | **P0 regression** — `file read` returns placeholder string instead of actual content. Users describe it as "completely broken." |
| [#102020](https://openclaw/openclaw/issues/102020) — **Second message fails with "reply session initialization conflicted"** | 14 | 1 | **Cross-channel, position-dependent** — blocks multi-turn conversation entirely on Signal and WhatsApp. |
| [#91009](https://openclaw/openclaw/issues/91009) — **Codex PreToolUse hook relay spawns CPU-bound processes** | 12 | 2 | **P1 crash-loop** — identifies resource exhaustion vector in Codex integration. |
| [#84583](https://openclaw/openclaw/issues/84583) — **Cron announce delivery triggers EmbeddedAttemptSessionTakeoverError** | 12 | 3 | Users reporting cron jobs corrupting active chat sessions. |
| [#94518](https://openclaw/openclaw/issues/94518) — **DeepSeek cache hit rate <10% after 6.x upgrade** | 9 | 10 | **10 upvotes** — strongest community signal on performance regression. DeepSeek users are losing cost efficiency. |
| [#107449](https://openclaw/openclaw/issues/107449) — **cron tool JSON Schema incompatible with llama.cpp tool parser** | 10 | 3 | Blocks local model users entirely on 2026.7.1. |
| [#107227](https://openclaw/openclaw/issues/107227) — **Gateway crash-loops with no documented remedy** | 8 | 3 | Users report "refusing to start, crash-looping under launchd" — high frustration with no workaround. |

**Underlying need**: The community is crying out for **reliable session lifecycle management** and **graceful error recovery**. The pattern across all top-voted issues is that transient failures (auth expirations, cron conflicts, quota exhaustion) cascade into permanent session corruption or gateway unavailability.

## 5. Bugs & Stability
**Critical (P0) — Active, with fix PRs or imminent closure:**

| Issue | Impact | Status |
|---|---|---|
| [#107220](https://openclaw/openclaw/issues/107220) — Gateway crash-loop: legacy memory sidecar `meta`/`chunks` conflicts are fatal | Crash-loop at startup | **OPEN** — P0, `needs-maintainer-review`, `needs-product-decision` |
| [#107694](https://openclaw/openclaw/issues/107694) — Gateway fails due to strict startupMigrationWarnings guard on benign skips | Crash-loop at startup | **OPEN** — P0, `needs-maintainer-review` |
| [#107727](https://openclaw/openclaw/issues/107727) — Gateway refuses readiness after update (plugin metadata conflict) | Gateway never comes up | **CLOSED** (today) |
| [#107330](https://openclaw/openclaw/issues/107330) — Windows `openclaw update` crash | Process crashes | **CLOSED** (today) |
| [#103076](https://openclaw/openclaw/issues/103076) — Additional legacy-state migration sources blocking startup | Crash-loop | **CLOSED** (today) |
| [#107227](https://openclaw/openclaw/issues/107227) — Startup-migration gate fatal, `doctor` doesn't resolve | Crash-loop | **CLOSED** (today) |
| [#101763](https://openclaw/openclaw/issues/101763) — Hosted Molty model selector doesn't persist (dotted id) | Every reply fails | **OPEN** — P0, UX release blocker |
| [#104721](https://openclaw/openclaw/issues/104721) — All tool results return placeholder string | Complete functional breakage | **OPEN** — P0, regression |

**High (P1) — Active Bug Reports:**

| Issue | Impact | Status |
|---|---|---|
| [#102020](https://openclaw/openclaw/issues/102020) — Second message fails cross-channel | Session blocked | **OPEN** |
| [#91009](https://openclaw/openclaw/issues/91009) — CPU-bound hooks processes | Crash-loop | **OPEN** — linked PR open |
| [#107449](https://openclaw/openclaw/issues/107449) — llama.cpp tool parser incompatibility | Local models broken | **OPEN** — linked PR open |
| [#106779](https://openclaw/openclaw/issues/106779) — Local llama.cpp provider fails (400 error) | Local models broken | **OPEN** |
| [#96834](https://openclaw/openclaw/issues/96834) — WhatsApp image wedges lane ~3 min | Session stall | **OPEN** |
| [#94518](https://openclaw/openclaw/issues/94518) — DeepSeek cache hit rate collapse | Cost/fidelity regression | **OPEN** — linked PR open |
| [#85103](https://openclaw/openclaw/issues/85103) — Model fallback chain not triggered on quota exhaustion | Auto-recovery broken | **OPEN** — stale |

**Stability Assessment**: The project is in a **stability trough** following the 2026.7.1 release. The new strict legacy state migration guard is too aggressive, treating benign/skippable migration warnings as fatal startup blockers. At least 5 distinct P0 crash-loop variants were reported within days of the release. The good news: maintainers are closing these rapidly (3 closed today), but the volume suggests a systemic gap in migration testing.

## 6. Feature Requests & Roadmap Signals

**Most requested by community (by engagement):**
1. **Linux/Windows Clawdbot Apps** (#75) — 81 👍, 113 comments; oldest open enhancement.
2. **Multi-LLM intelligent router** (#107686) — Request to reduce token costs by routing tasks to appropriate models (vision, debug, agentic). Could influence next version's economical agent path.
3. **AI safety & quality observability** (#82548) — Operational telemetry for prompt injection, citation quality, human feedback. P2.
4. **Multi-slot memory role architecture** (#88504) — Large XL PR still open; would give memory lifecycle awareness, curation via LLM.
5. **Subagent isolation** (#96975) — Return only status + session link from subagents, not full completion payload.
6. **Autonomous agent loop** (#108206, discussed in PRs above) — `/loop` command with token budget guard. Likely to land in 2026.7.2 stable.

**Prediction for next release (2026.7.2 stable):**
- **Remaining state-migration fixes** (P0 gate crash-loops will be resolved before stable — clear maintainer priority).
- **Autonomous agent loop** (`/loop`) may make it in as new capability.
- **Multi-slot memory** (PR #88504) if it gets maintainer review this week.
- **ACP session fixes** (PR #108392) for OpenCode compatibility.

## 7. User Feedback Summary

**Pain Points (high frequency):**
- **Upgrade breakage**: Multiple users report that upgrading from 2026.6.x → 2026.7.x causes gateway to refuse to start, with no documented remedy or autofix path. User Marvinthebored: _"refusing to start, crash-looping under launchd, with no documented remedy."_
- **Session corruption**: Users describe cascading failures — expired OAuth, cron interference, timeout compaction — that leave sessions permanently dead or wedged. Issue #80040 documents three compound failure modes in a single cascade.
- **Local model users are second-class citizens**: Issues #106779, #107449, #90288 highlight that llama.cpp, DeepSeek, and non-Anthropic providers suffer from missing tool parser compatibility and hard-coded timeouts.
- **Developer friction**: The `openclaw doctor --fix` command is not resolving the 2026.7.1 migration conflicts (multiple users report this), undermining trust in the repair tooling.

**Satisfaction signals:**
- The **new v2026.7.2-beta.1** features (remote coding sessions, cloud worker sessions, terminal session resume) are directly responsive to long-requested workflow improvements.
- **High engagement volume**: 467 issues + 500 PRs updated in 24h indicates a healthy, active community — users are engaged enough to file detailed bug reports with root-cause analysis.
- **Praise for rapid bug fixes**: Issues closed within 1-2 days of reporting (e.g., #107727, #107330, #107683) show maintainers are responsive.

## 8. Backlog Watch
These important issues/PRs have been open for extended periods without maintainer resolution:

| Item | Age | Status | Why It Matters |
|---|---|---|---|
| [#75](https://openclaw/openclaw/issues/75) — **Linux/Windows Clawdbot Apps** | 197 days | OPEN, P2, `help wanted` | Single highest-signal feature request (81 👍). No maintainer commitment. Project risks alienating non-Apple users. |
| [#11665](https://openclaw/openclaw/issues/11665) — **Webhook hook sessions should reuse existing session** | 158 days | OPEN, P2, linked PR open | Multi-turn webhook support documented but broken since at least Feb 2026. Blocks production webhook workflows. |
| [#9607](https://openclaw/openclaw/issues/9607) — **Himalaya skill: missing email formatting philosophy** | 161 days | OPEN, P3, linked PR open | Documentation gap for the email skill — users are getting incorrect formatting behavior. |
| [#85103](https://openclaw/openclaw/issues/85103) — **Model fallback chain not triggered on provider-wide quota exhaustion** | 56 days | OPEN, P1, stale | **Stale tag applied** to a P1 bug. Automatic fallback is a core reliability feature — leaving this unaddressed undermines production deployments. |
| [#80040](https://openclaw/openclaw/issues/80040) — **Cascading failure: invalidated OAuth, duplicate tool execution, context loss** | 67 days | OPEN, P2, `needs-maintainer-review` | Users report three compound failures with no resolution path. |
| [#75648](https://openclaw/openclaw/issues/75648) — **Embedded-run upstream timeout hard-coded at ~60s** | 76 days | CLOSED (stale-closed) | **Concern**: A feature request for a configurable timeout was closed without resolution. This limit is still hard-coded. |

**Recommendation**: The maintainers should urgently re-evaluate the **stale-closed** PR #75648 (configurable provider timeout) — it was closed without merging a fix, but the underlying limitation remains live in production. Additionally, P1 issues with the `stale` label (like #85103) should be escalated rather than deprioritized.

---

## Cross-Ecosystem Comparison

# Cross-Project Comparison Report: Personal AI Assistant Open-Source Ecosystem

## 1. Ecosystem Overview

The personal AI assistant open-source ecosystem is experiencing a **divergent maturation phase**, where individual projects are simultaneously pushing toward production-grade reliability while expanding into multi-provider, multi-channel, and multi-user architectures. The common thread across all active projects is a **crisis of complexity**—as agents gain autonomy (tool use, memory, delegation), the underlying session lifecycle management, state persistence, and error recovery mechanisms are failing under real-world strain. Projects that shipped major architectural overhauls (OpenClaw, Hermes Agent, IronClaw, CoPaw) are all in stability troughs, while newer or smaller projects (Moltis, NanoClaw) are benefiting from lessons learned and iterating with more conservative release cadences. The ecosystem is splitting into **two tiers**: projects building for developer/enterprise extensibility (OpenClaw, Hermes Agent, ZeroClaw) and those optimizing for end-user experience with opinionated defaults (NanoBot, LobsterAI, TinyClaw).

---

## 2. Activity Comparison

| Project | Issues Updated (24h) | PRs Updated (24h) | Release Today | Health Signal |
|---|---|---|---|---|
| **OpenClaw** | 467 (301 open) | 500 (322 open) | ✅ v2026.7.2-beta.1 | **Stability trough** — high velocity but critical P0 crash-loop bugs |
| **NanoBot** | 24 (3 open) | 26 (20 open) | None | **Strong hardening** — security audit completed, rapid bug closure |
| **Hermes Agent** | 50 (24 open) | 50 (44 open) | None | **Review bottleneck** — high activity but 6/50 PRs merged |
| **PicoClaw** | 6 (3 open) | 2 (2 open) | None | **Moderate** — two critical regressions open with no fix PRs |
| **NanoClaw** | 2 (1 open) | 11 (7 open) | None | **High velocity** — 4 PRs merged, infrastructure hardening |
| **NullClaw** | 0 | 0 | — | **Dormant** — no activity |
| **IronClaw** | 23 (18 open) | 38 (25 open) | None | **Intense stabilization** — Slack lifecycle crisis, Reborn migration |
| **LobsterAI** | — | 17 (6 open) | ✅ v2026.7.15 | **Release mode** — 11 PRs merged, but reverted a previous fix |
| **TinyClaw** | 0 | 1 (1 open) | None | **Quiet** — stable but low activity |
| **Moltis** | 1 (1 open) | 6 (0 open) | None | **Maintenance sprint** — 6 PRs merged, clean slate |
| **CoPaw** | 50 (18 open) | 43 (21 open) | None | **Post-v2.0 crisis** — memory leaks, context loss; 22 PRs merged |
| **ZeroClaw** | 38 (18 open) | 50 (38 open) | None | **Major push** — 12 PRs merged, OIDC auth landed, v0.9.0 preparation |

**Health tiers:**
- **Critical/crash-risk:** OpenClaw, PicoClaw
- **Intensive stabilization:** Hermes Agent, IronClaw, CoPaw, ZeroClaw
- **Healthy iteration:** NanoBot, NanoClaw, Moltis, LobsterAI
- **Low activity:** TinyClaw, NullClaw

---

## 3. OpenClaw's Position

**Advantages:**
- **Scale**: 467 issues + 500 PRs/24h is 5-10× any other project—OpenClaw has the largest contributor base and community engagement by a significant margin
- **Release discipline**: Ships beta releases even during stability crises (v2026.7.2-beta.1), showing commitment to continuous delivery
- **Feature breadth**: Remote coding sessions, cloud worker support, terminal resumption—capabilities others are still designing (cf. Hermes Agent's #64182 plugin expansion)
- **State migration management**: Despite the crash-loop crisis, the team is aggressively patching (5 P0 issues closed in 24h); the root cause (aggressive migration guard) is being addressed systematically

**Technical approach differences:**
- **Session model**: OpenClaw uses a **legacy-state-migration** pattern with strict guards that proved too aggressive; others (NanoBot, Moltis) use **schema-versioned persistence** with graceful fallback
- **Plugin system**: OpenClaw has a mature dead-code checker in CI (#108549); Hermes Agent is still designing its plugin interface (#64182)
- **Provider architecture**: OpenClaw supports Anthropic, Codex, and cloud workers; ZeroClaw leads with 5+ provider families, OpenAI-compatible endpoint

**Community size comparison:**
- OpenClaw is **10-50× more active** than any peer in raw issue/PR counts
- However, OpenClaw's crash-loop saga (6+ P0 issues) suggests the maintainer team may be **overwhelmed by scale**—bug density correlates with contribution velocity
- NanoBot's security audit closing 42 findings in days shows the efficiency possible in smaller, focused teams

---

## 4. Shared Technical Focus Areas

| Requirement | Projects Affected | Specific Pain Points |
|---|---|---|
| **Session lifecycle reliability** | OpenClaw, NanoBot, Hermes Agent, PicoClaw, IronClaw, CoPaw | Crash-loops on startup (OpenClaw #107220), heartbeat selection fails (NanoBot #4924), desktop session ID drift (Hermes #65297), Slack disconnect rejected (IronClaw #5834), context loss in v2.0 (CoPaw #6148) |
| **Memory & context management** | OpenClaw, Hermes Agent, CoPaw, ZeroClaw, Moltis | Conversation vs. persistent memory confusion (ZeroClaw #9048), prefix cache misses (Hermes #63713), 48GB RAM consumption (CoPaw #6124), context window misconfiguration (Moltis #1150) |
| **Multi-provider fallback & routing** | OpenClaw, NanoClaw, ZeroClaw, Moltis | Quota exhaustion breaks (OpenClaw #85103), Claude↔Codex fallback (NanoClaw #3057), kimi-code streaming error (ZeroClaw #5600), per-topic routing request (Moltis #574) |
| **Scriptable/toolable API surfaces** | Hermes Agent, ZeroClaw, OpenClaw, LobsterAI | `--output-format json` (Hermes #3326, since March), provider/model inventory (Hermes #23359), OpenAI-compatible endpoint (ZeroClaw #8486) |
| **Container/deployment ease** | NanoClaw, Moltis, ZeroClaw, CoPaw | host.docker.internal resolution (NanoClaw #3052), systemd-less fallback (Moltis #1153), CI timeout on build (ZeroClaw #9098), non-Tauri variant (CoPaw #6076) |
| **Security & multi-user isolation** | NanoBot, ZeroClaw, Hermes Agent, IronClaw | `process_direct()` bypasses auth (NanoBot #4779), OIDC auth (ZeroClaw #7141), delegate-task approval context loss (Hermes #37935, CVSS 7.0), per-user secrets (IronClaw #6118) |

**Cross-cutting insight**: **Session lifecycle reliability** is the #1 shared failure mode across 6 of 12 projects. The ecosystem needs a shared pattern or library for idempotent session initialization with graceful migration—every team is solving the same problem differently and failing in similar ways.

---

## 5. Differentiation Analysis

| Dimension | OpenClaw | NanoBot | Hermes Agent | ZeroClaw | CoPaw | LobsterAI |
|---|---|---|---|---|---|---|
| **Target user** | Power developers, multi-tool | Community/enterprise, multi-channel | Researchers, plugin developers | Infrastructure-first, providers | Chinese market, Qwen ecosystem | Consumer desktop/mobile |
| **Primary channel** | Terminal, cloud workers | Telegram, Signal, WeChat | LINE, Telegram, desktop app | TUI (ZeroCode), web dashboard | Feishu, web | Desktop app, WeChat bot |
| **Provider focus** | Anthropic (Codex/Claude) | Multi-provider (Codex, Qwen, DeepSeek) | Anthropic + open models | 5+ families (kimi, OpenAI, Anthropic) | Qwen models, MCP tools | GPT-5.6, Grok 4.5, DeepSeek |
| **Architecture** | Monolithic with plugins | Modular channels + gateway | Core agent + plugin expansion | Runtime + gateway + firmware | Tauri desktop app + Python backend | Electron desktop app |
| **Memory model** | Legacy-state migration | Shared memory tree (provider-agnostic, #3012) | SessionDB with prefix cache | Conversation vs. persistent memory (RFC #9048) | ReMe + Scroll context system | LLM cache (stale LRU fix #1322) |
| **Deployment** | `openclaw doctor` CLI | Docker, `setup/*.sh` | Nix, hermetic launcher | CI builds (firmware + runtime) | Windows/Ubuntu installer | Windows installer, web |
| **Key differentiator** | Largest contributor base, remote coding | Security-first, rapid audit capability | Plugin interface design, research-grade | Multi-user auth, OIDC, A2A agent discovery | Qwen-native, Chinese enterprise | Consumer UX, ad-supported model |

**Notable gaps:**
- **Non-Apple desktop**: OpenClaw #75 (Linux/Windows apps, 81 👍, 197 days open) is a reputational risk
- **Chinese market**: CoPaw leads for Chinese users; OpenClaw, Hermes have limited support
- **Consumer UI polish**: LobsterAI excels; OpenClaw, Hermes Agent, ZeroClaw are developer-oriented

---

## 6. Community Momentum & Maturity

**Tier 1 — Hyper-growth / Scaling pain** (rapid iteration, stability issues):
- **OpenClaw**: Highest raw activity, but P0 bugs per feature ratio is concerning. The 500 PRs/24h figure may include bot/CI noise, but the underlying contributor growth is real. **Risk**: maintainer burnout if crash-loop cycle repeats.
- **ZeroClaw**: 50 PRs/24h, RFC-driven development, shipping security infrastructure. **Strongest roadmap clarity** of any project.
- **Hermes Agent**: 50 PRs/24h but only 6 merged—review bottleneck. If resolved, could match OpenClaw's velocity.

**Tier 2 — Stabilization / Hardening** (post-major-release, fixing regressions):
- **CoPaw**: Recovering from v2.0 launch; 22 PRs merged today, memory leak fix merging. **Positive trajectory** if context loss issues are resolved.
- **IronClaw**: Reborn migration is the focus; 13 PRs merged, but Slack lifecycle is unresolved. **Medium risk**—Slack is core to their value proposition.
- **NanoBot**: Finished security audit (42 findings, all closed). **Most mature** in terms of code quality and safety.
- **PicoClaw**: Only 2 regressions open but no fix PRs. **Smallest active team**—risk of stagnation.

**Tier 3 — Steady state / Low velocity** (stable, incremental):
- **Moltis**: 6 PRs merged in 24h, clean slate. **Balanced**—responsive but not overwhelmed.
- **NanoClaw**: 4 PRs merged, focusing on infrastructure. **Growing**—added OpenCode provider today.
- **LobsterAI**: Released today, merging features. **Consumer-focused**—less community engagement but clear release cadence.
- **TinyClaw, NullClaw**: Near-dormant. **Needs revival or archiving** if maintainers have moved on.

---

## 7. Trend Signals

**1. Session lifecycle is the new "login"** — Across 6+ projects, session initialization, migration, and recovery are the #1 failure mode. The ecosystem needs standardized patterns (e.g., idempotent init, graceful degradation, repair tooling). **Impact**: AI agent developers should invest in robust session management before adding features.

**2. Multi-provider is table stakes, not differentiator** — Every active project supports 2+ providers. The differentiator is now **intelligent routing** (cost, latency, capability awareness) and **graceful fallback** on quota exhaustion. OpenClaw #107686 (multi-LLM router), NanoClaw #3057 (Claude↔Codex fallback), and Moltis #574 (per-topic routing) confirm this shift.

**3. Memory is fracturing into two paradigms** — Projects are splitting between **conversation-as-memory** (session logs with retrieval) and **agent-curated long-term memory** (persistent knowledge stores). ZeroClaw RFC #9048 explicitly calls out the confusion. **Trend**: Expect convergence toward a hybrid model (session + curated) within 6 months.

**4. Security is moving from optional to mandatory** — NanoBot's 42-finding audit, ZeroClaw's OIDC/auth RFC closures, and Hermes Agent's CVSS 7.0 `delegate-task` bug (#37935) show that multi-user and enterprise use cases are driving fundamental security architecture changes. **Implication**: Next-gen agents will need pluggable auth, per-actor permissions, and audit trails by default.

**5. Windows desktop is the underserved frontier** — OpenClaw #75 (81 👍, 197 days), CoPaw #6076 (non-Tauri for old OS), and Hermes Agent #65299 (Windows console popups) all highlight gaps. Projects that solve Windows desktop well (LobsterAI is closest) will capture significant non-developer user share.

**6. Observability is becoming a feature, not infrastructure** — ZeroClaw #6641 (turn-level OTel traces), Hermes Agent #23359 (provider inventory API), and OpenClaw #82548 (AI quality observability) show that developers want **operational telemetry for agent behavior**, not just system metrics. Expect agent-specific monitoring tools (prompt injection detection, citation quality scoring, human feedback loops) to emerge as standalone products.

**7. The "local model citizen" problem persists** — OpenClaw #106779 (llama.cpp broken), ZeroClaw #5600 (kimi-code streaming errors), and NanoBot #4934 (Qwen thinking leakage) confirm that local/reasoning models remain poorly supported. **Strategic gap**: Projects that invest in provider abstraction layers with protocol-level compatibility checks will win the self-hosted market.

---

**Bottom line for decision-makers**: If you need **scale and ecosystem**, bet on OpenClaw but plan for migration friction. For **production reliability**, NanoBot or Moltis offer the best stability-to-feature ratio. For **Chinese market reach**, CoPaw is the clear leader. The most important architectural decision you can make today is how you handle **session lifecycle**—every project is failing here, and your own agent system will too unless you invest in idempotent, migration-safe initialization patterns from day one.

---

## Peer Project Reports

<details>
<summary><strong>NanoBot</strong> — <a href="https://github.com/HKUDS/nanobot">HKUDS/nanobot</a></summary>

# NanoBot Project Digest — 2026-07-16

## 1. Today's Overview
NanoBot is in an intensive maintenance and hardening cycle, with 24 issues and 26 PRs updated in the last 24 hours. The project demonstrates exceptionally strong community engagement, with 21 of 24 issues closed — most from a comprehensive security and correctness audit that found 42 findings across the codebase. Six PRs were merged today covering provider proxy consistency, gateway shutdown ordering, multimodal message handling, markdown deduplication, WebUI fixes, and dev dependency alignment. The project's focus has clearly shifted from feature velocity to stability, security hardening, and addressing architectural debt, indicating a maturing codebase preparing for production reliability.

## 2. Releases
No new releases today.

## 3. Project Progress
**Merged/Closed PRs (6):**
- **[#4944]** `fix(gateway): stop channels before draining tasks` — Fixes DingTalk Stream reconnection swallowing during shutdown (by chengyongru)
- **[#4943]** `fix(providers): honor Codex proxy config consistently` — Activate explicit `--config` path before OAuth login handlers, propagate proxy settings (by chengyongru)
- **[#4870]** `Share channel markdown helpers` — Adds shared Markdown utilities; reuses code-block protection, pipe-table parsing, and table rendering across Telegram, Signal, and Feishu (by Kokeip)
- **[#4813]** `fix(loop): guard .strip() on msg.content against list-form multimodal data` — Fixes AttributeError when channels deliver multimodal content (by axelray-dev)
- **[#4649]** `fix(webui): correct activity timer duration` — Timer now measures from user turn start instead of first activity row (by chengyongru)
- **[#4926]** `fix: include Feishu SDK in dev dependencies` — Ensures `lark-oapi` is installed with `uv sync --extra dev` (by ruirui6946)

**Key fixes advanced:**
- Gateway shutdown ordering now prevents channel SDK reconnection hangs
- Codex provider proxy configuration is now consistently applied to OAuth, image generation, and HTTP requests
- Multimodal messages no longer crash command dispatch paths
- Channel markdown converters consolidated from 3 duplicated implementations into shared utilities

## 4. Community Hot Topics
**Most Active Discussions:**

- **[Issue #4924](https://github.com/HKUDS/nanobot/issues/4924)** — *Heartbeat selection fails with unifiedSession: true* (4 comments)  
  A bug report about `_pick_heartbeat_target_from_sessions` failing when sessions are empty but unified mode is enabled. This is actively being addressed by **[PR #4928](https://github.com/HKUDS/nanobot/pull/4928)** which persists the latest concrete channel route and uses it for heartbeat delivery.

- **[Issue #4779](https://github.com/HKUDS/nanobot/issues/4779)** — *Security: process_direct() bypasses channel-level authorization* (2 comments)  
  Critical security finding from the deep audit, now closed after 9 days. Six or more callers can bypass all channel `is_allowed()` checks.

- **[Issue #4934](https://github.com/HKUDS/nanobot/issues/4934)** — *Qwen models expose thinking/reasoning content* (1 comment)  
  User-reported issue about Qwen 3.x models leaking verbose reasoning text into chat responses. Being fixed by **[PR #4946](https://github.com/HKUDS/nanobot/pull/4946)** which adds a `_QWEN_THINK_MODELS` exclusion list.

**Underlying needs:** The community is demanding production-grade security hardening, multi-user safety, and provider compatibility. The unified session heartbeat issue (#4924) reflects growing adoption of multi-channel setups. The Qwen thinking model issue (#4934) shows increasing demand for reasoning-model support with proper content filtering.

## 5. Bugs & Stability
**High Priority (fix PRs exist):**
- **Heartbeat selection failure with unifiedSession** (#4924, open) — `_pick_heartbeat_target_from_sessions` fails when no sessions exist but unified mode is active. **Fix PR:** [#4928](https://github.com/HKUDS/nanobot/pull/4928)
- **Qwen thinking models leak reasoning content** (#4934, open) — Verbose thinking text exposed in chat responses. **Fix PR:** [#4946](https://github.com/HKUDS/nanobot/pull/4946)
- **Session metadata lost after restart** (#4940, open) — Legacy filename format causes `workspace_scope` to be lost. **Fix PR:** [#4941](https://github.com/HKUDS/nanobot/pull/4941)
- **Hard context overflow reprompt** (#4925, open) — Agent fails on extreme context overflow. **Fix PR:** [#4925](https://github.com/HKUDS/nanobot/pull/4925)

**Closed bugs from audit (all resolved):**
- `process_direct()` bypasses channel authorization — CLOSED (#4779)
- 'system' channel messages bypass all checks — CLOSED (#4778)
- `/stop` command cancels other users' tasks — CLOSED (#4777)
- `/restart` command has zero authorization — CLOSED (#4776)
- `.strip()` crashes on multimodal messages — CLOSED, fixed by PR #4813
- Token budget returns 128 when context window disabled — CLOSED (#4802)
- Global ExecSessionManager shared across loops — CLOSED (#4793)
- Consolidator WeakValueDictionary GC vulnerability — CLOSED (#4789)

**Regressions:** PR [#4944](https://github.com/HKUDS/nanobot/pull/4944) fixed a regression where DingTalk Stream transport could swallow reconnections during gateway shutdown (introduced by channel drain ordering changes). PR [#4941](https://github.com/HKUDS/nanobot/pull/4941) addresses a regression from the collision-resistant path change that broke legacy session metadata reads.

## 6. Feature Requests & Roadmap Signals
**In Development (open PRs):**
- **[#4942](https://github.com/HKUDS/nanobot/pull/4942)** — *Session-local triggers*: Agents can create, list, enable, disable, and remove local triggers per conversation. Includes a `local-trigger` skill explaining when to use local vs. cron/heartbeat.
- **[#4620](https://github.com/HKUDS/nanobot/pull/4620)** — *Heartbeat trigger command*: CLI `nanobot heartbeat trigger` with `--dry-run`, `--json`, and explicit channel/chat-id options. Addresses #3437.
- **[#4937](https://github.com/HKUDS/nanobot/pull/4937)** — *One-click Deploy to Render*: Gateway + WebUI as single service, with persistent session history and memory.
- **[#4621](https://github.com/HKUDS/nanobot/pull/4621)** — *Memory archive with provenance context*: Bounded MEMORY.md excerpts in Consolidator prompts, source-discipline rules for user facts vs. inferred observations.
- **[#4919](https://github.com/HKUDS/nanobot/pull/4919)** — *Custom Telegram Bot API base URL*: Lets Telegram channel target self-hosted Bot API servers or enterprise gateways (addresses #4702).

**Prediction for next release:** Session-local triggers (#4942) and heartbeat trigger CLI (#4620) are likely candidates for the next minor release, given their maturity and community demand for agent-defined automation. The Telegram custom API base (#4919) also has strong enterprise use-case appeal.

## 7. User Feedback Summary
**Pain points expressed:**
- **Qwen model thinking leakage** (#4934): "verbose reasoning content to leak into chat responses" — users expect clean final answers, especially for simple queries.
- **Session metadata loss after restart** (#4940): "workspace_scope metadata is silently lost after restarting nanobot" — breaks custom project paths for WebUI users relying on legacy session file formats.
- **Unified session heartbeat failures** (#4924): Users configuring unified sessions see broken heartbeat delivery, disrupting proactive message workflows.

**Satisfaction signals:**
- The deep security audit (42 findings, all closed) demonstrates maintainer commitment to production safety.
- Multiple contributors (axelray-dev, Kokeip, ruirui6946, yu-xin-c, chengyongru) submitting simultaneous fixes shows healthy collaborative development.
- The channel markdown deduplication (#4870) was contributed by a community member, indicating growing contributor base and attention to code quality.

## 8. Backlog Watch
**Long-unanswered items needing attention:**
- **Cron job context reuse** (#4082, closed today) — Repeated cron runs share fixed session context. While closed, the underlying architectural issue of stable session keys for scheduled tasks may resurface.
- **Invalid config silently falls back to defaults** (#4067, closed today) — Config errors can change runtime behavior silently. Fix PR #4918 (open) centralizes config persistence but has a conflict marker.
- **WebSocket proactive message drops** (#4062, closed today) — Messages dropped when no subscriber is connected. The transcript persistence gap remains for offline periods.
- **Message tool authorization bypass** (#4076, closed today) — Outbound recipient authorization missing. No fix PR identified yet — requires architectural change for outbound policy enforcement.

**Open PRs with potential conflicts:**
- **[#4918](https://github.com/HKUDS/nanobot/pull/4918)** (config persistence refactor) — Has a conflict marker
- **[#4822](https://github.com/HKUDS/nanobot/pull/4822)** (WebUI automation source preservation) — Has a conflict marker
- **[#4908](https://github.com/HKUDS/nanobot/pull/4908)** (self-contained channels refactor) — Large architectural change (27 commits) that may need maintainer review bandwidth

</details>

<details>
<summary><strong>Hermes Agent</strong> — <a href="https://github.com/nousresearch/hermes-agent">nousresearch/hermes-agent</a></summary>

# Hermes Agent Project Digest
**Date:** 2026-07-16

---

## 1. Today's Overview

Project activity remains extremely high, with 50 issues and 50 PRs updated in the last 24 hours—suggesting a sustained, well-maintained development pace. 26 issues were closed yesterday versus 24 remaining open/active, indicating a healthy closure rate. On the PR side, only 6 of 50 updated were merged or closed, leaving 44 open PRs; this suggests a growing review bottleneck, particularly around features flagged with `sweeper:risk-*` labels for broad blast radius. No new releases were cut today, which is notable given the volume of merged fixes and pending features awaiting tagging.

---

## 2. Releases

No new releases were published on 2026-07-16. The stable track (v0.18.2) continues to serve as the latest publicly available version.

---

## 3. Project Progress

Six PRs were merged or closed today:

- **#9030** (`ToolRegistry type safety and repr`) — Merged; adds explicit types to `ToolEntry` fields and a concise `repr` for debugging, improving developer experience for tool plugins.
- **#65237** (`fix(nix): dirty-tree wrapper bug + filtered rebuild scope + overlay alias`) — Fixes a real wrapper-generation bug in the Nix build, shrinks per-derivation source filtering, and simplifies the overlay to a pure alias.
- **#65261** (`fix(codex): honor CODEX_HOME during migration`) — Ensures the `CODEX_HOME` environment variable is respected when `migrate()` is called without an explicit `codex_home` argument.
- **#65292** (`fix: make Hermes launcher survive home directory changes`) — Fixes installer-generated launcher breakage when users change usernames or restore profiles on new machines.
- **#63555** (duplicate feature for suppressing system messages) — Closed as duplicate alongside broader work on configurable system message suppression.

Two serious P0 bugs from yesterday (see Section 5) were confirmed fixed on `main`.

---

## 4. Community Hot Topics

**Most Active Issue:**
- **[#64182 — Plugin Interface Expansion Tracking (12 comments)](https://github.com/nousresearch/hermes-agent/issues/64182)** — A community-driven reference plan for expanding the core agent's plugin interface, distilled from Discord discussions. With 12 comments and a P3 priority, this is the most actively discussed initiative today. The community is converging on a design to unblock long-queued PRs.

**Heavily Reacted Issue:**
- **[#3326 — `--output-format json` flag (5 👍)](https://github.com/nousresearch/hermes-agent/issues/3326)** — First opened in March 2026, this feature request for structured CLI output continues to attract support. Users need scriptable access for CI pipelines and MCP servers, a gap that #23359 (provider/model inventory) also highlights.

**Notable High-Engagement Bugs:**
- **[#63911 — Telegram DM topic mode root-lobby gate swallows kanban wake events (5 comments)](https://github.com/nousresearch/hermes-agent/issues/63911)** — Closed today; a subtle interaction where Telegram DM topic mode's lobby gate silently dropped kanban wake events with no `thread_id`, causing completions to never be processed.
- **[#23359 — Provider/model inventory lacks scriptable surface (4 comments)](https://github.com/nousresearch/hermes-agent/issues/23359)** — Five different PRs have reinvented model listing, and four issues are blocked. Users are frustrated by the lack of a single, stable API endpoint.

**Analysis:** The community's top pain points are converging around **programmability** (scriptable CLI, API endpoints for inventory) and **plugin interface stability**. The Plugin Interface Expansion tracking issue (#64182) may become the highest-priority roadmap item as it directly unblocks multiple contributor PRs.

---

## 5. Bugs & Stability

**P0 (Critical) — Fixed on `main`:**
- **[#63712 — AsyncSessionDB methods silently dropped without `await`](https://github.com/nousresearch/hermes-agent/issues/63712)** — A `__getattr__` trap returned coroutine functions instead of executing them, causing lost writes and `RuntimeWarning`. Fixed via #63712 (`sweeper:implemented-on-main`).
- **[#63713 — Session system_prompt persists as `null` → prefix cache misses permanently](https://github.com/nousresearch/hermes-agent/issues/63713)** — Every turn rebuilt the system prompt from scratch, destroying prefix cache benefits. Fixed on `main`.

**P2 (High) — New Today:**
- **Desktop session identity drift bugs (three reports):**
  - [#65297 — Image paste broken due to session ID drift](https://github.com/nousresearch/hermes-agent/issues/65297) — `image.attach` and `prompt.submit` reference different session IDs on macOS.
  - [#64789 — `prompt.submit` targets stale runtime A when route/stored session point to B](https://github.com/nousresearch/hermes-agent/issues/64789) — Desktop session routing race condition.
  - [#52514 — Checkpoint restore fails with "target user message no longer in session history"](https://github.com/nousresearch/hermes-agent/issues/52514) — Open since June 25.
- [#65300 — New session ignores config.yaml default, reuses sticky composer model](https://github.com/nousresearch/hermes-agent/issues/65300) — Desktop persists a stale model from local storage instead of seeding from configuration.
- [#44771 — Curator LLM review enters 4-hour loop consuming 91M tokens](https://github.com/nousresearch/hermes-agent/issues/44771) — Symlinked skill clusters trigger infinite consolidation loops. Open since June 12.
- [#65034 — Dashboard Full Backup fails silently (CLI argument syntax mismatch)](https://github.com/nousresearch/hermes-agent/issues/65034) — Backup button triggers indefinite "running" state, no `.zip` produced.
- [#37935 — `delegate-task` approval context not preserved (CVSS 7.0/High)](https://github.com/nousresearch/hermes-agent/issues/37935) — Security issue where executor submissions lose approval context. Open since June 3.

**P3 (Medium) — New Today:**
- [#65299 — Photon sidecar subprocesses show Windows console popups](https://github.com/nousresearch/hermes-agent/issues/65299) — Related to the earlier #63698 (closed/fixed), but on a different subsystem (Photon/npm sidecars).
- [#65307 — Webhook endpoint crashes on non-ASCII signature headers](https://github.com/nousresearch/hermes-agent/pull/65307) — PR submitted with fix.

**New PR Fixes Available:**
- [#65260 — Bound session state growth (28 GiB database)](https://github.com/nousresearch/hermes-agent/pull/65260) — Addresses a production issue where live database reached 28 GiB, delaying restart by 8.5 minutes.
- [#65305 — API server crashes on non-ASCII bearer tokens](https://github.com/nousresearch/hermes-agent/pull/65305) — Security fix: return 401 instead of crashing.
- [#65304 — Hermes launcher survives home directory changes](https://github.com/nousresearch/hermes-agent/pull/65304) — Multiple duplicates this week, including #65292 already merged.

**Stability Concern:** The cluster of Desktop session drift bugs (#65297, #64789, #52514) suggests a systemic concurrency issue in the Desktop app's session routing layer. The `sweeper:risk-session-state` label appears on 7+ active issues/PRs, indicating the team is aware this is a high-risk area.

---

## 6. Feature Requests & Roadmap Signals

**High Likelihood for Next Release:**
- **Updater Rework** ([PR #65296](https://github.com/nousresearch/hermes-agent/pull/65296)) — A 61-commit, 101-file redesign of the install/update system with managed release bundles and atomic slots. This is the largest PR in flight and likely targets the next minor version.
- **Plugin Interface Expansion** ([#64182](https://github.com/nousresearch/hermes-agent/issues/64182)) — Community-driven tracking issue; the 12 comments and Discord origin suggest this is being actively designed for the next release cycle.

**Moderate Likelihood:**
- **Persistent exponential cooldown manager** ([PR #56613](https://github.com/nousresearch/hermes-agent/pull/56613)) — Disk-persisted cooldown state for provider failover, replacing ad-hoc timestamps.
- **Configurable system message suppression** ([#63555](https://github.com/nousresearch/hermes-agent/issues/63555), closed/duplicate) — Multiple users want to suppress "Working..." and "Self-improvement review" messages on chat platforms.

**Lower Likelihood but Notable:**
- **`--output-format json`** ([#3326](https://github.com/nousresearch/hermes-agent/issues/3326), 5 👍) — Strong community demand but open since March 2026; may be blocked by #23359.
- **PreToolUse enforcement hook** ([#63770](https://github.com/nousresearch/hermes-agent/issues/63770)) — Users want behavioral rules that survive recency bias in deep debugging loops.
- **Canonical provider/model inventory API** ([#23359](https://github.com/nousresearch/hermes-agent/issues/23359)) — Four blocked issues suggest this is a critical infrastructure need.

**Trend to Watch:** Multiple feature requests are converging on **context preservation** — session checkpoint export/import (#63748), per-run metadata propagation to MCP (#64890), and the `--resume` session bridging gap. This suggests users are running increasingly complex multi-session workflows and hitting context-loss pain points.

---

## 7. User Feedback Summary

**Common Pain Points (in order of frequency):**
1. **Desktop session integrity issues** — Multiple users report sessions that disappear after restart (#63516), fail to persist (#63474), or suffer from ID drift (#65297, #64789, #52514). This is the #1 user-facing stability concern.
2. **Windows console flashing** — Two independent reports (#63698 closed, #65299 open) confirm Windows `windows_hide_console: true` is not fully respected across all subsystems.
3. **Missing scriptable/API surfaces** — Users orchestration via CI/MCP cannot get structured output (#3326) or enumerate providers/models programmatically (#23359).
4. **Over-intrusive system messages** — Users on chat platforms (LINE, Telegram) want config switches to suppress "Working..." and "Self-improvement review" messages (#63555).

**Satisfaction Indicators:**
- Customization flexibility is highly valued (#63923 — preserving user customizations across updates).
- The `--tui` interface is appreciated in constrained environments like Termux (#63668).
- The Kanban/goal mode is being actively used despite the dispatcher bug (#63396 closed/fixed).

**Dissatisfaction Signals:**
- The #44771 curator loop consuming 91M tokens represents a real cost exposure for paid-API users.
- Session state growth to 28 GiB (#65260) indicates a scaling issue for heavy users.

---

## 8. Backlog Watch

**Critical Attention Needed:**
- **[#37935 — `delegate-task` approval context loss (CVSS 7.0, P2)](https://github.com/nousresearch/hermes-agent/issues/37935)** — Open since June 3, no fix PR linked. Security-adjacent with High CVSS v4.0 score.
- **[#44771 — Curator LLM review 4-hour loop (P2)](https://github.com/nousresearch/hermes-agent/issues/44771)** — Active since June 12 with only 2 comments; economic impact (91M tokens) warrants escalation.

**Stale High-Value Feature Requests:**
- **[#3326 — `--output-format json` (5 👍, since March 27)](https://github.com/nousresearch/hermes-agent/issues/3326)** — Strong community support but no assignee. Blocked by lack of scriptable inventory API.
- **[#23359 — Provider/model inventory (since May 10)](https://github.com/nousresearch/hermes-agent/issues/23359)** — Directly blocking 5 PRs and 4 issues. Should be prioritized alongside #64182.

**PRs Awaiting Maintainer Review:**
- **[PR #43332 — QQBot Windows local file delivery (P2, since June 10)](https://github.com/nousresearch/hermes-agent/pull/43332)** — Platform-specific fix for Chinese users; may be lower priority for the core team.
- **[PR #4816 — Terminal sandbox overrides for messaging (P2, since April 3)](https://github.com/nousresearch/hermes-agent/pull/4816)** — A 3+ month old PR rebased to current `main`. Broad blast radius with `sweeper:risk-security-boundary` may explain the delay.
- **[PR #56613 — Cooldown manager (P3, since July 1)](https://github.com/nousresearch/hermes-agent/pull/56613)** — Waiting for decision on design approach.
- **[PR #60086 — MoA Copilot slots routing (P3, since July 7)](https://github.com/nousresearch/hermes-agent/pull/60086)** — Needs review on a targeted model-routing fix.

**Overall Backlog Health Assessment:** The project has a healthy number of recent PRs, but 44 open PRs with only 6 merged/closed in 24h suggests the team is struggling to keep pace with contributions. The sheer volume of `sweeper:risk-*` labels (present on 8+ items) indicates the review process is bottlenecked by risk-assessment overhead rather than code quality. The Plugin Interface Expansion (#64182) may be the team's attempt to reduce this friction by standardizing plugin contribution pathways.

</details>

<details>
<summary><strong>PicoClaw</strong> — <a href="https://github.com/sipeed/picoclaw">sipeed/picoclaw</a></summary>

Here is the PicoClaw project digest for **2026-07-16**.

---

## PicoClaw Project Digest – 2026-07-16

### 1. Today's Overview
Activity is moderate today, with 6 issues updated and 2 pull requests active, though no new releases are on the board. The maintainer team closed 3 stale bugs (related to Volcengine tool calls and OAuth login), signaling ongoing housekeeping, but the remaining open issues point to two **critical regressions** in the latest v0.3.1 release. Community interest appears to be shifting toward infrastructure: one user opened a feature request for stateless gateway sessions, and a pending PR refactors the DeltaChat integration. Overall, the project looks healthy but is dealing with a notable **ARM64 packaging gap** and a **hook deserialization defect** that will likely demand immediate attention.

### 2. Releases
**No new releases today.** The latest stable release remains v0.3.1 (build 2026-07-03). Users are advised to verify their architecture compatibility when downloading from picoclaw.io, as noted in Issue #3260.

### 3. Project Progress
No PRs were merged or closed today. Two PRs remain open:
- **#3259** – Update PicoClaw description for parallelization (minor documentation tweak, likely to merge quickly).
- **#3222** – refactor(deltachat): cleanup implementation, -200LOC – A significant cleanup removing legacy features, deprecated fallbacks, hardcoded relay lists, and password-based email configuration. This has been pending since July 3 and could land this week.

### 4. Community Hot Topics
- **#3153 (Closed)** – [BUG] Volcengine Doubao Seed tool calls leak as raw `<seed:tool_call>` text (4 comments). This was a critical functional bug for users of Volcengine Coding Plan with `doubao-seed-2.0-pro`. Though now closed as stale, it received the most community attention in the last 24 hours (likely prior engagement). The core issue—tool call execution bypassing the intended pipeline—reflects a deeper concern about parser robustness for non-standard model outputs.
- **#3196 / #3197 (Closed)** – Two identical reports of Codex and Antyggravity OAuth login failures (2 comments each). Both were closed as stale, but the fact two users reported the same issue suggests a possible auth integration regression that may resurface.

### 5. Bugs & Stability
| Severity | Issue | Description | Fix PR? |
|----------|-------|-------------|---------|
| **High** | [#3260 (Open)](https://github.com/sipeed/picoclaw/issues/3260) | **ARM64 launcher missing** in v0.3.1 release download – Raspberry Pi 3B users cannot run the downloaded binary because the ARM64 archive contains no launcher. | No |
| **High** | [#3258 (Open)](https://github.com/sipeed/picoclaw/issues/3258) | **Process Hook `before_tool` modify broken** – The `decision` field is discarded, and arguments are misparsed due to a deserialization defect. Likely affects all custom tool hooks using modification logic. | No |
| Low (closed) | #3153, #3196, #3197 | Stale bugs closed today. Historical issues (Volcengine tool call leakage, OAuth login) now considered inactive. | N/A |

**Summary:** Two high-severity regressions are open without fix PRs. Both impact core functionality (ARM64 deployment and tool hooks). The hook bug (#3258) especially may block developers building custom Telegram/CLI tools.

### 6. Feature Requests & Roadmap Signals
- **#3257 (Open)** – **Stateless/no-history mode for gateway sessions**: The user requests the ability to start fresh conversations in gateway mode without deriving session keys from channel/chat IDs (as happens today). This would align gateway behavior with the CLI’s `--session` flag and is a clean, low-risk addition. **Prediction:** Likely merged in v0.3.2 if author submits a PR.
- **#3171 (future signal)** – Note: No explicit roadmap signals were found in today's updates, but the ongoing DeltaChat refactor (#3222) suggests the maintainer team is investing in communication channel maturity over new feature scope.

### 7. User Feedback Summary
- **Pain Points:**
  - ARM64 users (Raspberry Pi, aarch64) cannot use the official download page (#3260) – a fundamental distribution issue.
  - Hook developers face silent data corruption: `before_tool` modifications are ignored or misparsed (#3258), forcing workarounds.
  - Gateway mode is less flexible than CLI for managing conversation state (#3257).
- **Satisfaction:** The closing of three stale bugs indicates the team is listening to old reports, but no positive user feedback was recorded today.

### 8. Backlog Watch
- **#3222 (Open, since 2026-07-03)** – refactor(deltachat) PR: -200 LOC, touches core email/chat integration. No comments from maintainers since creation. This is a candidate for review this week to avoid merge conflicts.
- **#3260 (Open, since 2026-07-15)** – ARM64 launcher missing: zero comments, zero reactions. This is a potentially critical **download-page-level bug** that could discourage new Raspberry Pi users. **Needs immediate maintainer response.**
- **#3258 (Open, since 2026-07-15)** – Hook deserialization defect: zero replies. Likely affects many custom tool pipelines. Needs a reproduction from maintainers and either a hotfix or a workaround guide.

</details>

<details>
<summary><strong>NanoClaw</strong> — <a href="https://github.com/qwibitai/nanoclaw">qwibitai/nanoclaw</a></summary>

# NanoClaw Project Digest — 2026-07-16

## Today's Overview

The NanoClaw project shows **high development velocity** today with 11 pull requests updated in the last 24 hours, alongside 2 issues updated and no new releases. Activity is concentrated on infrastructure hardening: transient delivery failures, container lifecycle management, provider configuration validation, and cross-provider memory unification. Several closed PRs indicate the team has successfully merged **multi-provider memory support** (PR #3012) and the **Codex counterpart** (PR #3013), as well as a one-command deploy script (PR #3055) and a new OpenCode agent provider (PR #3056). The overall project health is robust, with active development across core infrastructure, provider support, and operational tooling.

## Releases

**No new releases today.** The latest release remains unlisted. However, given the volume of merged PRs (4 closed/merged) and the addition of a deploy script (PR #3055) and a new provider (PR #3056), a release candidate or patch release may be imminent.

## Project Progress

**4 PRs were closed/merged today**, marking tangible feature advancement:

- **#3056** (merged) — **OpenCode provider added** (`feat(opencode): add OpenCode as an agent provider`). This adds OpenCode as a first-class agent provider in the container agent-runner, including subprocess lifecycle management, MCP server configuration translation, and idle-timeout handling. This expands NanoClaw's multi-provider strategy beyond Claude and Codex.

- **#3013** (closed) — **Codex shared memory on session start** (`feat(codex): load shared memory on session start`). Implements the Codex counterpart for the provider-agnostic memory system, registering the `SessionStart` command hook and refreshing canonical memory entries.

- **#3012** (closed) — **Provider-agnostic persistent memory** (`feat(memory): add provider-agnostic persistent memory`). Scaffolds a shared memory tree across agent providers, including `memory/index.md` and `memory/system/definition.md` per agent group, loaded on startup, clear, and compaction.

- **#3055** (merged) — **One-command deploy script** (`feat: add deploy.sh for one-command redeploys`). Adds `deploy.sh` with SSH-based git pull, build, and service restart, aligning with existing `setup/*.sh` conventions.

Additionally, 7 PRs remain open, signaling ongoing work across delivery reliability, quota fallback, container lifecycle, and approval system unification.

## Community Hot Topics

**Highest engagement:** The most active items today focus on **delivery reliability and data integrity**:

- **Issue #3058** (1 comment) — *Transient outbound-send failures are permanently dropped after 3 fast retries*. This issue identifies a subtle but impactful bug: the delivery system treats all failures identically, permanently dropping messages on transient network issues. A fix PR (#3059) is already open, indicating the team is responding rapidly.

- **Issue #3054** (closed, 0 comments) — *agent_message_policies rows can outlive their group/connection*. FK constraint failures and stale gate entries identified during group deletion and CLI destination removal. This was closed, likely with an accompanying fix.

**Underlying community needs:** These issues reveal that as NanoClaw scales multi-provider and multi-channel support, data consistency and reliability engineering are emerging as top community concerns. Users are encountering edge cases where transient infrastructure failures (network blips, process termination timing) cause permanent data loss or orphaned database rows.

## Bugs & Stability

**Ranked by severity:**

1. **Critical** — **Issue #3058** (OPEN): *Transient outbound-send failures permanently dropped after 3 fast retries*. **Fix PR #3059 exists.** This is a data-loss bug: any network blip during message delivery permanently drops the agent's reply after 3 retries. The fix distinguishes transient failures (network, timeout, 429/5xx) from permanent ones (validation errors). **Implication:** Until this fix lands, users may lose agent responses during infrastructure hiccups.

2. **High** — **Issue #3054** (CLOSED): *agent_message_policies rows can outlive their group/connection*. FK constraint failures on group delete, stale gate entries on destination removal. **Fix likely applied during issue closure.** This bug could block database migrations and group management operations.

3. **Medium** — **PR #3053** (OPEN): *Container never exits on its own, rides to 30-min SIGTERM*. `processQuery` keeps the SDK stream open after a turn, blocking the poll loop and causing container build-up. **Fix in open PR.** This causes wasted compute resources and potential resource exhaustion in high-traffic deployments.

4. **Low** — **PR #3052** (OPEN): *host.docker.internal resolution fails under Colima/Lima/Rancher Desktop*. VM-based macOS runtimes don't inject the host-gateway mapping. **Fix in open PR.** Affects Mac developers using alternative Docker runtimes.

## Feature Requests & Roadmap Signals

Several signals point to NanoClaw's strategic direction:

1. **Automatic Claude↔Codex quota fallback** (PR #3057, OPEN) — Per-agent-group automatic failover when Claude hits quota mid-turn, plus Telegram/WhatsApp channel adapters and pilot activation. This is a major feature: it ensures uninterrupted agent operation during provider API limits and extends channel support beyond the current surface. Likely heading into the next feature release.

2. **OpenCode as agent provider** (PR #3056, merged) — Explicitly expands provider support beyond Anthropic's Claude and Amazon's Codex. This suggests the platform is being architected to support any LLM-backed agent runtime.

3. **Unified approval lifecycle** (PR #3040, OPEN, core-team) — Consolidates approval holds behind one contract. This is an infrastructure improvement likely prompted by the `agent_message_policies` FK bug (#3054).

4. **Provider preflight validation** (PR #3051, OPEN) — Preflight validation before saving provider config. Indicates user demand for preventing misconfigurations that cause runtime failures.

**Prediction:** The next release (likely 0.x or a minor patch) will include PR #3057 (quota fallback + new channels) and #3059 (transient failure fix), given their complementary nature—the quota fallback feature introduces new failure modes that the delivery fix addresses.

## User Feedback Summary

Real pain points and use cases derived from today's activity:

1. **Data loss frustration** (Issue #3058) — Users are experiencing lost agent replies during transient network degradation. The retry logic is too aggressive and lacks failure-type discrimination. **Immediate satisfaction concern** — users want delivery guarantees.

2. **Operational complexity** (PR #3055, PR #3053) — Users need one-command deployment and are experiencing container orchestration headaches (containers never exiting, resource bloat). The deploy script addresses the former; the idle-standown fix addresses the latter.

3. **Cross-platform compatibility** (PR #3052) — Mac developers using alternative Docker runtimes cannot resolve host names, breaking development workflows. **Deployment friction** for the non-Docker-Desktop ecosystem.

4. **Provider management friction** (PR #3051, Issue #3054) — Users hitting FK errors and stale configuration states during group management. The preflight validation suggests users want safety nets before saving changes.

5. **Satisfaction signal:** The community is actively contributing fixes (11 PRs), suggesting high engagement and investment in NanoClaw's reliability.

## Backlog Watch

Items requiring maintainer attention:

1. **PR #2591** (OPEN, 54 days old) — *fix: namespace user IDs by channel-type prefix, not bare colon*. Updated today (2026-07-15) but open since May 22. This is a significant refactor of user ID handling across channels. The long review cycle may indicate complexity or maintainer bandwidth constraints. **Risk:** This PR has high surface area (namespace changes touch every channel adapter); merge conflicts likely.

2. **PR #3057** (OPEN, 1 day old) — *feat: automatic Claude↔Codex quota fallback (+ Telegram/WhatsApp channels)*. This is a large, cross-cutting feature PR opened yesterday. Given its scope (quota fallback + new channel adapters + pilot activation), it warrants close review and may need to be split into incremental PRs.

3. **No long-unanswered issues found.** The project maintains strong responsiveness—both issues updated in the last 24h received immediate attention (one closed, one with an open fix PR).

---

*Generated from NanoClaw GitHub activity on 2026-07-16.*

</details>

<details>
<summary><strong>NullClaw</strong> — <a href="https://github.com/nullclaw/nullclaw">nullclaw/nullclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>IronClaw</strong> — <a href="https://github.com/nearai/ironclaw">nearai/ironclaw</a></summary>

Here is the IronClaw project digest for **2026-07-16**.

---

### 1. Today's Overview

The IronClaw project is in a period of **high-intensity stabilization and architectural overhaul**. Activity is extremely high, with 38 updated Pull Requests and 23 Issues reflecting a coordinated push to address systemic regressions, particularly in the Slack/Extensions channel lifecycle. The team is actively working on the "Reborn" runtime migration, as evidenced by a massive "unified generic extension runtime" PR (#6116) and a PR to remove the retired v1 runtime (#6123). Despite no new releases, the volume of merged fixes and regression tests indicates a project in a critical quality-assurance and refactoring phase, with a clear focus on resolving top-priority user-facing bugs.

### 2. Releases

There are no new releases for this date.

### 3. Project Progress (Merged/Closed PRs)

Thirteen PRs were merged or closed today, representing significant progress in bug-fixing and test infrastructure:

- **Slack Stability (#6135):** A large PR was merged to ensure Slack recovers correctly after OAuth activation, specifically fixing catalog construction failures when assets are missing. This is a direct response to the persistent Slack lifecycle bugs.
- **Auth & Lifecycle Auditing (#6128):** A fix was merged that addresses multiple blockers identified during an auth/lifecycle audit, including scope ceilings, Notion refresh issues, and fan-out retryability.
- **UI Polish (#6084, #6082, #6083, #6087):** Several closed PRs improve the user experience: replacing native browser `confirm()` dialogs with a shared Reborn modal, fixing the Extensions Registry to load without enrichment delay, and handling extension catalog load failures gracefully.
- **Automation/StaleSurface (#6055):** The team added integration coverage for crucial scenarios like `StaleSurface` refresh and channel cleanup on extension removal.
- **WebUI Fixes (#6044, #6083):** A fix landed for the intermittent Enter-key-not-submitting bug, and native confirmation dialogs were addressed.

### 4. Community Hot Topics

The most active discussions center on the **systemic failure of the Slack integration lifecycle**, which has become the project's most critical pain point.

- **[#6105 Extension/channel lifecycle state-machine test](https://github.com/nearai/ironclaw/issues/6105):** This issue explicitly calls out Slack as the "#1 user-facing bug family," having regressed across four QA waves. The core team (ilblackdragon) and community contributors are deeply engaged in designing a state-machine test to lock down the install→connect→disconnect→reconnect→uninstall flow. The need is for a fundamental, testable solution rather than point-fixes.
- **[#5834 Slack disconnect request is incorrectly rejected](https://github.com/nearai/ironclaw/issues/5834) & [#5877 Slack notification delivered to wrong user](https://github.com/nearai/ironclaw/issues/5877):** These P1 and P2 bugs highlight a deeper architectural flaw in how the agent manages channel state and user identity, eroding user trust in the platform's core communication features.

### 5. Bugs & Stability

The bug report from today’s activity is heavily concentrated on Slack and the new Reborn UI, with several regressions noted.

**Critical/P1 (User-blocking):**
- **[#5877 (OPEN)] Slack notification delivered to wrong user:** A severe data-leakage and trust concern.
- **[#5943 (OPEN)] Slack DM action posts to current channel instead of user's DMs:** Directly breaks the primary use case for Slack DMs.
- **[#6125 (OPEN) "Busy" error blocking user messages during routine execution:** Complete UI lockout for users with background automations.

**High/P2 (Major quality degradation):**
- **[#5834 (OPEN) Slack disconnect rejected by agent:** Core functionality is non-functional.
- **[#5944 (OPEN) Slack DM silently fails but reports success:** Misleading success state makes debugging impossible.
- **[#5882 (OPEN) Repeated reconnect leaves auth in broken state:** User has to reinstall the extension.
- **[#6127 (OPEN) "Previous run still in progress" on first execution:** Misleading UI status.
- **[#6044 (CLOSED) Enter key does not submit:** Fixed, but was a regressive UX issue.

**Medium/P3 (Minor but numerous):**
- **[#6126 (OPEN) No loading state on first message:** Poor UX for new conversations.
- **[#6117 (OPEN) Untranslated region names:** Low priority but inconsistent UI.

**Fix PRs in Progress:**
- Several of these bugs have active fix PRs. #6129 and #6130 directly address OAuth and Slack lifecycle issues. #5910 is a bot-authored fix for approval gate hydration.

### 6. Feature Requests & Roadmap Signals

The roadmap is clearly dominated by the "Reborn" transition and the need for **proactive system stability** rather than reactive bug fixes.

- **"Reborn" Tier-2 Test Harness:** Multiple PRs today (#6131, #6132, #6133, #6134) are building out a new, robust integration test suite with fault injection, LLM fixtures, and SSE wire-contract tests. This is a massive, deliberate investment in preventing regressions.
- **Per-User Secrets Management (#6118):** A frontend feature request to expose admin-level user secrets management in the WebUI. This is a clear gap between backend capability and admin UX.
- **Unified Generic Extension Runtime (#6116):** The largest active PR points to a future where all extensions (Slack, etc.) run on a single, honest state-machine model. This is the foundational fix for the current lifecycle bugs.
- **V1 Runtime Removal (#6123):** The project is aggressively "burning the boats" on the legacy v1 runtime, signaling a complete commitment to the Reborn architecture in the next release.

### 7. User Feedback Summary

User sentiments, inferred from bug reports authored by QA members, indicate **high dissatisfaction with reliability and transparency**.

- **Dissatisfaction with Slack:** Users are frustrated by a "broken" and "misleading" experience. The pattern of "success" messages paired with silent failures (#5944) and wrong-user delivery (#5877) destroys confidence in the product.
- **Frustration with Being Locked Out:** The `"This message wasn't sent because Ironclaw was busy"` error (#6125) is a classic worst-case UX: the user is told their message won't be sent while the system is *actively failing to do what they asked*. This is a near-total loss of function.
- **Need for Visual Feedback:** The "blank screen" on first chat (#6126) and slow-loading registry (#6052) show that even when the system works, the lack of progress indicators makes it *feel* broken.

### 8. Backlog Watch

While activity is high, some complex or lower-priority items face a risk of stagnation:

- **[#5910 fix: hydrate approval gates on notification open (OPEN, AUTO)](https://github.com/nearai/ironclaw/pull/5910):** This bot-authored PR has been open for nearly a week without significant human review, possibly because it touches the complex channel lifecycle which is being overhauled by #6116.
- **[#5598 chore: release (OPEN, 13 days old)](https://github.com/nearai/ironclaw/pull/5598):** This open release PR indicates that the project is in a state where a stable release is being block due to the scale of active work on the "unified vs main" reconciliation. The many breaking changes listed (API changes in `ironclaw_common` and `ironclaw_skills`) suggest a significant pending version bump that is likely waiting for the Reborn migration to settle.

</details>

<details>
<summary><strong>LobsterAI</strong> — <a href="https://github.com/netease-youdao/LobsterAI">netease-youdao/LobsterAI</a></summary>

Based on the provided GitHub data for LobsterAI (github.com/netease-youdao/LobsterAI), here is the project digest for **2026-07-16**.

# Project Digest: LobsterAI - 2026-07-16

## 1. Today's Overview
The project is in **high-activity release mode**, with 17 PRs updated and the immediate release of version `2026.7.15`. The team merged 11 PRs in the last 24 hours, focusing on a major UI/UX overhaul of the update system, settings panel, and model support. A new open issue regarding in-app advertising indicates potential user pushback. The team appears to be aggressively closing out old stale issues (#1381-#1385) while merging significant feature work (GPT-5.6, Grok 4.5).

## 2. Releases
**New Version: [LobsterAI 2026.7.15](https://github.com/netease-youdao/LobsterAI/releases/tag/2026.7.15)**
- **Optimized File Card:** Improved rendering for file attachments.
- **Windows Installer:** Added an opt-in Windows web installer target.
- **Homepage Revamp:** The "cowork" homepage quick-action scenarios have been redesigned.
- **Breaking Changes:** None explicitly declared.
- **Migration:** No migration notes provided; standard update path assumed.

## 3. Project Progress
**Major Feature & Fix Merge Spree (11 Merges):**
- **New Model Support:** [PR #2332](https://github.com/netease-youdao/LobsterAI/pull/2332): Added **GPT-5.6** and **Grok 4.5** as default models with a deduplication migration path.
- **Update Overhaul:** [PR #2333](https://github.com/netease-youdao/LobsterAI/pull/2333) & [#2338](https://github.com/netease-youdao/LobsterAI/pull/2338): Introduced a blocking overlay during updates with progress, scrollable release notes, and keyboard focus lock.
- **Settings UI:** [PR #2336](https://github.com/netease-youdao/LobsterAI/pull/2336): Reorganized General settings into labelled cards (Basics, Notifications, Data & Privacy).
- **Bug Fixes:** Fixed a content copy bug ([#2335](https://github.com/netease-youdao/LobsterAI/pull/2335)) and restored IM session loading state ([#2334](https://github.com/netease-youdao/LobsterAI/pull/2334)).
- **Model Permission Rollback:** [PR #2340](https://github.com/netease-youdao/LobsterAI/pull/2340): Reverted a previous fix regarding "model not allowed" ([#2337](https://github.com/netease-youdao/LobsterAI/pull/2337)), suggesting the fix had unintended consequences.

## 4. Community Hot Topics
- **[Issue #2342](https://github.com/netease-youdao/LobsterAI/issues/2342) (Open): "Can the lower-left ad be permanently closed?"** - This is the **only active issue** and has strong emotional weight. A user in version `v2026.7.15` is seeing a pop-up advertisement for the first time. They want a permanent toggle to disable it. This suggests a potential monetization feature that may upset the user base.
- **Stale Issues Closed (Batch):** The team closed 5 old issues (created 2026-04-03) from users `QinGang746`, `isaiah5818`, and `ZlsMzs`. These covered:
    - **WeChat Bot Sync:** Identical text not syncing correctly ([#1383](https://github.com/netease-youdao/LobsterAI/issues/1383)).
    - **Session History Bug:** Deleting a WeChat task did not clear history on re-query ([#1385](https://github.com/netease-youdao/LobsterAI/issues/1385)).

## 5. Bugs & Stability
- **Regression (High Severity):** A previous fix for "model not allowed" was **reverted** ([#2340](https://github.com/netease-youdao/LobsterAI/pull/2340)). This implies the original bug (models being incorrectly blocked) may still be present.
- **Content Copy Bug (Fixed):** [PR #2335](https://github.com/netease-youdao/LobsterAI/pull/2335) fixed a bug where copying content failed. Fix is live in `2026.7.15`.
- **Cached Bug (Pending):** [PR #1322](https://github.com/netease-youdao/LobsterAI/pull/1322) (True LRU eviction for LLM cache) remains **open and stale** (since April 2nd). Cache performance issues may persist.
- **Multi-File Upload (Fixed):** [PR #1372](https://github.com/netease-youdao/LobsterAI/pull/1372) (Stale, Closed): Fixed the bug where selecting multiple files only kept the last one. This fix appears to have been applied retroactively.

## 6. Feature Requests & Roadmap Signals
- **User Request: Ad-Free Experience ([#2342](https://github.com/netease-youdao/LobsterAI/issues/2342)):** The user demands a permanent disable option for a new ad. If this is a test, the backlash may cause the team to revert or hide it behind a toggle.
- **Upcoming Feature: Update Blocking Overlay ([#2333](https://github.com/netease-youdao/LobsterAI/pull/2333)):** This is now live. It prevents user interaction during updates, a stability feature.
- **New Model Support:** The addition of GPT-5.6 and Grok 4.5 is aggressive. The team is prioritizing cutting-edge model compatibility.

## 7. User Feedback Summary
- **Pain Points:**
    - **WeChat Bot Unreliability:** Multiple issues from April were just closed today regarding session history and sync errors ([#1383](https://github.com/netease-youdao/LobsterAI/issues/1383), [#1385](https://github.com/netease-youdao/LobsterAI/issues/1385)). Users experienced data loss/confusion.
    - **Intrusive Advertising:** A single user is very unhappy about a new ad appearing in the bottom-left corner. This is a potential hot-button issue for the wider user base.
- **Satisfaction:** The rapid merging of features (new models, UI improvements) indicates a responsive team, but the regression reversion ([#2340](https://github.com/netease-youdao/LobsterAI/pull/2340)) may cause user frustration with model access.

## 8. Backlog Watch
- **[PR #1322](https://github.com/netease-youdao/LobsterAI/pull/1322) (Stale, Open):** This PR fixes a significant caching bug (LLM memory judge cache using insertion order instead of LRU). It has been open since April 2nd, 2026 (~105 days) with no recent maintainer activity. This is the most critical backlog item affecting performance.
- **[PR #1277](https://github.com/netease-youdao/LobsterAI/pull/1277) (Stale, Open):** A Dependabot PR bumping Electron from v40 to v43. This is a major version jump and requires careful review to avoid breaking the desktop client.
- **Stale Dependabot PRs:** Four Dependabot CI updates ([#2164](https://github.com/netease-youdao/LobsterAI/pull/2164), [#2165](https://github.com/netease-youdao/LobsterAI/pull/2165), [#2166](https://github.com/netease-youdao/LobsterAI/pull/2166), [#2167](https://github.com/netease-youdao/LobsterAI/pull/2167)) have been open for over a month, risking CI failures from outdated tooling.

</details>

<details>
<summary><strong>TinyClaw</strong> — <a href="https://github.com/TinyAGI/tinyagi">TinyAGI/tinyagi</a></summary>

# TinyClaw Project Digest — 2026-07-16

## Today's Overview
Activity on TinyClaw remains minimal, with no issues updated in the last 24 hours and no new releases. One pull request remains open from yesterday, suggesting a low-velocity period with no urgent community interactions. The project appears stable but not actively advancing, with maintainers likely focusing on review of the single open PR. Overall project health is quiet but not dormant.

## Releases
No new releases were published today. The latest available release remains unchanged. No migration notes or breaking changes to report.

## Project Progress
No pull requests were merged or closed today. The only active PR is **#295**, still open with no comments or reviews from maintainers or contributors.

## Community Hot Topics
The only active item is **PR #295**:
- **Fix: print the "New leader" note after removing a team leader**  
  Author: Osamaali313 | Updated: 2026-07-15 | GitHub: [TinyAGI/tinyagi PR #295](https://github.com/TinyAGI/tinyagi/pull/295)  
  *Analysis:* The PR addresses a CLI bug where after removing a team leader, the success message was built using an "always-false" condition, causing the leadership change confirmation not to be printed. The fix ensures the new leader message is properly displayed. This indicates a real user confusion point and a small but meaningful usability improvement. No community reactions yet, suggesting low awareness or engagement around this fix.

## Bugs & Stability
No new bugs, crashes, or regressions were reported today. The single open PR fixes an existing CLI output bug that is low severity — it affects user experience (missing confirmation message) but does not break core functionality. No fix PRs were merged, but PR #295 targets this exact issue.

## Feature Requests & Roadmap Signals
No new feature requests were filed today. No roadmap hints or signal emerged from issues or comments. The project's trajectory remains unclear from recent data alone.

## User Feedback Summary
No user feedback, pain points, or satisfaction signals appeared today. The lack of any issue reports or comments suggests either high satisfaction with current functionality or low usage/engagement.

## Backlog Watch
There are no long-unanswered issues or PRs requiring maintainer attention. PR #295 (open for one day) is not yet stale. No historic issues are awaiting action. The backlog is effectively empty.

</details>

<details>
<summary><strong>Moltis</strong> — <a href="https://github.com/moltis-org/moltis">moltis-org/moltis</a></summary>

Here is the Moltis project digest for **2026-07-16**.

---

### Moltis Project Digest – 2026-07-16

**1. Today’s Overview**
The project shows a **high level of maintenance and integration activity** following a lull in issue creation. While only one issue was active in the last 24 hours, six pull requests were **merged/closed**, signaling a focused sprint on provider stability, dependency hygiene, and infrastructure support. No new releases were published today, but the PR volume suggests a release candidate may be imminent. The project appears to be in a **stable but feature-expanding phase**, with emphasis on reducing friction for self-hosted and containerized environments.

**2. Releases**
*None.* No new releases were published on 2026-07-16. The latest release remains the previous version.

**3. Project Progress**
Six pull requests were merged today, covering three main themes:

- **Provider Support & Model Metadata**:
  - **#1151** – Added support for **MiniMax M3** while retaining M2.7 in the static model registry. Includes context-window and image-input metadata for both global and China endpoints. ([PR #1151](https://github.com/moltis-org/moltis/pull/1151))
  - **#1150** – Centralized context-window fallback mappings and added dynamic parsing of Copilot live model metadata; improves reliability for model capability detection. ([PR #1150](https://github.com/moltis-org/moltis/pull/1150))
  - **#1152** – Fixed token expiry deadlock for `openai-codex` provider by deriving expiry from the JWT `exp` claim instead of a null value. ([PR #1152](https://github.com/moltis-org/moltis/pull/1152))

- **External Agent Integration**:
  - **#1149** – Added auto-detection for **ACP-based agents** (Claude, Pi, Gemini, Kimi, Kiro, OpenClaw, etc.), including a separate binary detection path for Claude ACP. ([PR #1149](https://github.com/moltis-org/moltis/pull/1149))

- **Infrastructure & Dependencies**:
  - **#1153** – Added a **systemd-less service fallback** for Linux containers (e.g., devbox, Coder), using a user-owned supervisor script with full lifecycle commands. ([PR #1153](https://github.com/moltis-org/moltis/pull/1153))
  - **#1148** – Routine dependency bumps for `esbuild` and `vite` across npm directories. ([PR #1148](https://github.com/moltis-org/moltis/pull/1148))

**4. Community Hot Topics**
The only active issue, **#574 ([Feature] Model Routing Per Topic)** ([Issue #574](https://github.com/moltis-org/moltis/issues/574)), continues to attract attention with **1 comment and 1 reaction**. The request asks for per-topic routing of queries to different models (e.g., code generation vs. creative writing). The lack of recent maintainer response (last updated 2026-07-15) suggests the feature may still be in the backlog. The underlying need is for **intelligent workload distribution across multiple LLM providers** without manual provider switching.

**5. Bugs & Stability**
- **Fixed – High Severity**: *Token expiry deadlock in openai-codex provider* (**PR #1152**). Sessions were breaking after ~10 days with no recovery. The fix now derives `expires_at` from the JWT `exp` claim. This was a critical session-halting bug for heavy users of the codex provider.
- **Fixed – Medium Severity**: *Context window misconfiguration* (**PR #1150**). Model capabilities were not correctly wired to context-window values, potentially causing truncation or failures. Centralized fallback mappings and dynamic parsing resolve this.
- **No new bugs or regressions** were reported in the last 24 hours.

**6. Feature Requests & Roadmap Signals**
The most prominent signal is **Issue #574 (Model Routing Per Topic)**. Given the merged PRs today that expanded dynamic provider/model metadata (PR #1150) and added new mini-providers (PR #1151), the infrastructure now exists to support such routing. It is plausible that **per-topic routing will be considered for the next minor release** (e.g., v0.9.x). Additionally, the auto-detection of ACP agents (PR #1149) signals a roadmap move toward **multi-agent runtime orchestration**.

**7. User Feedback Summary**
- **Pain Points Addressed**:
  - Token expiry in codex provider was a daily frustration (now fixed).
  - Users in containerized environments without systemd can now run Moltis as a service (PR #1153).
- **Unaddressed Desires**:
  - The model routing feature (Issue #574) has received a single upvote but no roadmap commitment; users likely want to avoid manual provider switching.
- **Satisfaction Signals**: High PR merge velocity (6 in 24h) suggests maintainers are responsive to infrastructure and provider reliability issues, which generally improves user trust.

**8. Backlog Watch**
- **Issue #574 – Model Routing Per Topic** ([Issue #574](https://github.com/moltis-org/moltis/issues/574)): Created **101 days ago**, last commented on yesterday. This is the **only open issue** with no resolution or milestone. It represents a significant usability gap for advanced users. If the maintainers plan to include it, it should be triaged soon; otherwise, a status update would help manage community expectations.
- **No stale PRs** are currently awaiting maintainer action; all recent PRs were closed or merged promptly.

</details>

<details>
<summary><strong>CoPaw</strong> — <a href="https://github.com/agentscope-ai/CoPaw">agentscope-ai/CoPaw</a></summary>

Based on the GitHub data from the CoPaw repository (github.com/agentscope-ai/CoPaw) for the period ending 2026-07-16, here is the project digest.

---

# CoPaw Project Digest: 2026-07-16

## 1. Today's Overview
CoPaw is currently experiencing a period of intense development and community engagement. The **high volume of open issues (18 active out of 50 total updated)** and **open PRs (21)** indicates a major stabilization and feature-development phase following the release of QwenPaw v2.0.0. The **v2.0 transition is the dominant theme**, with several critical user reports regarding memory management, context handling, and configuration migration. Despite no new releases today, activity suggests a patch release (e.g., v2.0.0.post3 or v2.0.1) is imminent, with maintainers actively reviewing and merging fixes for high-priority regressions (e.g., memory leaks, context limits). The project is highly responsive, with many issues being closed quickly and PRs submitted within hours of bug reports.

## 2. Releases
**No new releases were published today.** The latest available version is inferred to be v2.0.0.post2, based on multiple bug reports referencing this version.

## 3. Project Progress
**Total Closed/Merged PRs Today: 22**

Several significant fixes and features advanced to the `main` branch:

- **Memory & Indexing Fixes:**
    - **PR #6153** (`feat(memory): enhance ReMe configuration and indexing safeguards`) by *jinliyl*: Upgraded the ReMe dependency to `0.4.1.1` and added a 10 MiB file size limit for indexing to prevent memory exhaustion.
    - **PR #6142** (`fix(console): require auto_memory_interval as int >= 0, disallow empty`) by *zhaozhuang521*: Added validation to allow users to disable (set to 0) the automatic memory interval, addressing a user-reported bug.
- **Bug Fixes & Configuration:**
    - **PR #6140** (`fix(utils): add errors='replace' to _run_command for GBK compatibility`) by *liu6yi1*: A fix for encoding issues on Windows systems using GBK locales.
    - **PR #6039** (`fix(mcp): resolve ${VAR} env references in legacy driver migration`) by *TinyBai*: Fixed a critical v2.0 migration bug where environment variable placeholders in MCP tool configurations were not being resolved.
- **CI & Infrastructure:**
    - **PR #6143** (`ci: pass Supabase config to website build`) by *Osier-Yi*: Enables configuration for the website's backend services.
    - **PR #6147** (`feat(website): add blog view/like counts and switch GA to QwenPaw property`) by *yuluo1007*: Migrated website analytics to the correct property.

## 4. Community Hot Topics
The highest-activity discussions highlight the core challenges and desires of the user base.

- **[Issue #6129]** *[Bug]: Missing spaces and line feeds in thinking blocks* – A UI/UX bug where spaces disappear from the agent's reasoning output while streaming. This is a high-priority cosmetic fix with a corresponding merge-ready PR (#6139). [View Issue](https://github.com/agentscope-ai/QwenPaw/issues/6129)
- **[Issue #6125]** *[Feature]: 有支持政企版的银河麒麟操作系统的计划吗？* : A request for support on the Kylin OS, a Linux-based OS used in Chinese government/enterprise sectors. This signals a desire for broader Linux distribution support beyond Ubuntu/Debian. [View Issue](https://github.com/agentscope-ai/QwenPaw/issues/6125)
- **[Issue #2969 / #4259]** *[Feature]: 增加个人知识库的功能 / 增加预制 Agent 模板* : Two long-running, popular feature requests (5 and 3 comments, 3 👍 total). Users consistently ask for pre-built agent templates and integrated personal knowledge base functionality to lower the barrier for non-technical users. [View Issue #2969](https://github.com/agentscope-ai/QwenPaw/issues/2969) | [View Issue #4259](https://github.com/agentscope-ai/QwenPaw/issues/4259)
- **[Issue #6076]** *[Question]: Are there plans to release a non-Tauri variant for QwenPaw 2.0?* – A user requests support for old OS environments (Windows 7) where the new Tauri-based desktop app doesn't run. [View Issue](https://github.com/agentscope-ai/QwenPaw/issues/6076)

## 5. Bugs & Stability
Several significant bugs were reported today, primarily related to the v2.0 upgrade.

- **Critical / High Severity:**
    - **Memory Leak & Startup Failure ([Issue #6124])**: *BaiYouQing* reported that the new ReMe memory background loops consume 48GB+ of RAM during startup and never complete. A PR (#6153) has been submitted to mitigate this by limiting file sizes and upgrading the library. [View Issue](https://github.com/agentscope-ai/QwenPaw/issues/6124)
    - **Context Loss / "Amnesia" ([Issue #6148])**: *laeni* and others report that v2.0 frequently forgets earlier parts of a conversation, lacks proper context compression, and truncates messages. They link this to the new Scroll context management system. A fix PR (#6123) is currently open. [View Issue](https://github.com/agentscope-ai/QwenPaw/issues/6148)
- **Medium Severity:**
    - **Configuration Migration Issues ([Issue #6155])**: *yguangg* reported that upgrading from 1.x to 2.0 breaks embedding configurations (missing dimension passing) and causes issues with auto-memo filters. [View Issue](https://github.com/agentscope-ai/QwenPaw/issues/6155)
    - **Model Execution Errors ([Issue #6141])**: *xlg1024* reported a `MODEL_EXECUTION_ERROR` after aborting a mission, leaving the session unusable. [View Issue](https://github.com/agentscope-ai/QwenPaw/issues/6141)
    - **Web UI Validation ([Issue #6132])**: *manjieqi* reported that the auto-memory interval cannot be set to 0 to disable the feature. This was immediately fixed by PR #6142, which was already merged. [View Issue](https://github.com/agentscope-ai/QwenPaw/issues/6132)

## 6. Feature Requests & Roadmap Signals
Several requests suggest the direction for the next minor release:

- **Strong Candidate for Next Version:**
    - **Integrated Knowledge Base ([Issue #2969])**: Extremely high demand. A built-in RAG feature is the #1 most upvoted open request. It is likely being actively developed behind the scenes.
    - **Agent Templates ([Issue #4259])**: Directly addresses the barrier for non-technical users. A likely feature for a future v2.1 release.
    - **Worker & Multi-Agent UX ([Issue #6136])**: *Chen-Jianxiong* reported that the "leader" agent rarely invokes other agents automatically. Improving agent-to-agent collaboration orchestration is a key roadmap item.
- **Lower Priority / Specialized:**
    - **Canonical OS Support ([Issue #6076])**: Request for non-Tauri builds to support Windows 7.
    - **Government OS Support ([Issue #6125])**: Request for Kylin OS support.
    - **Desktop Workflow Improvements ([Issue #6083])**: A request for a quick-access button to agent output files in the Desktop app.

## 7. User Feedback Summary
- **Satisfaction:** Users are clearly testing the new v2.0 architecture deeply, suggesting strong engagement. The quick discovery and reporting of bugs (memory leaks, context loss) indicates a high degree of usage.
- **Dissatisfaction & Pain Points:**
    1.  **PostgreSQL/Database Schema Migration ([Issue #6155])**: Users are frustrated by failed migrations and *"失忆症很严重"* (severe amnesia) in v2.0, which is a critical usability regression.
    2.  **Memory & Context Limits ([Issue #6124])**: Memory leaks that peg the system at 48GB+ are a blocking issue for users with smaller RAM or using the desktop app.
    3.  **Steep Learning Curve ([Issue #4259])**: Users explicitly state that setting up agents from scratch is hard for non-technical people. They want templates.
- **Key Use Cases:** The data reveals a heavy reliance on:
    - **Agent-to-Agent Delegation**: Orchestrating complex, multi-step tasks between specialized agents.
    - **External Tool Integration**: Heavy use of MCP tools (Tavily, Browser Use) and Feishu channel.
    - **Multi-Agent Workflows**: Using the `/mission` command and worker agents for parallel tasks.

## 8. Backlog Watch
Two issues/requests have been open for an extended period and require maintainer attention:

- **[Issue #2907]** *[Question]: PR #2448 need review* (Created: 2026-04-03): A contributor asking for a review of a PR that blocks further development. This is 3.5 months old and is an indicator of stalled community contribution. [View Issue](https://github.com/agentscope-ai/QwenPaw/issues/2907)
- **[Issue #2909]** *[Question]: how to debug the long run task...* (Created: 2026-04-03): A user asking for debugging guidance for long-running agent-to-agent tasks that get cancelled. This is a support request that may point to a deeper platform stability issue. [View Issue](https://github.com/agentscope-ai/QwenPaw/issues/2909)

</details>

<details>
<summary><strong>ZeptoClaw</strong> — <a href="https://github.com/qhkm/zeptoclaw">qhkm/zeptoclaw</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>ZeroClaw</strong> — <a href="https://github.com/zeroclaw-labs/zeroclaw">zeroclaw-labs/zeroclaw</a></summary>

# ZeroClaw Project Digest — 2026-07-16

## Today's Overview

ZeroClaw shows **very high activity** with 38 issues and 50 PRs updated in the last 24 hours, indicating a major development push. The project closed 20 issues and merged/closed 12 PRs today, including significant infrastructure work around provider stability and security architecture. No new releases were cut today, but the project is actively preparing for a v0.9.0 milestone with multiple RFCs being finalized. Several critical bugs affecting workflow-blocked (S1 severity) users remain open, though fix PRs are in flight for some.

---

## Releases

**None** — No new releases today. The last attempted release (v0.8.3) failed due to CI timeout issues, with a fix PR (#9098) raised today to raise build matrix timeout from 40 to 90 minutes.

---

## Project Progress

**12 PRs merged/closed today**, reflecting substantial forward momentum:

- **Provider stability fixes** — Multiple PRs addressed streaming and tool-call reliability:
  - [#9060](https://github.com/zeroclaw-labs/zeroclaw/pull/9060): Normalize malformed native tool-call arguments before outbound requests (OpenAI-format providers)
  - [#8838](https://github.com/zeroclaw-labs/zeroclaw/pull/8838): Idle-bound SSE streaming on shared transport
  - [#9070](https://github.com/zeroclaw-labs/zeroclaw/pull/9070): Flush open tool_use block at message_stop (Anthropic)
  - [#9090](https://github.com/zeroclaw-labs/zeroclaw/pull/9090): Enforce tool-call pairing at one canonical chokepoint

- **Runtime improvements**:
  - [#9062](https://github.com/zeroclaw-labs/zeroclaw/pull/9062): Gate execute_pipeline sub-tools by per-agent access policy
  - [#8845](https://github.com/zeroclaw-labs/zeroclaw/pull/8845): Rebuild live sessions on agents.<alias>.model_provider edits
  - [#9083](https://github.com/zeroclaw-labs/zeroclaw/pull/9083): Trim context overflow to model window with attribute compactions

- **Security & config**:
  - [#8672](https://github.com/zeroclaw-labs/zeroclaw/pull/8672): Multi-user auth providers, permission profiles, and principal isolation (closed)
  - [#8754](https://github.com/zeroclaw-labs/zeroclaw/pull/8754): Schema V4 cut with breaking changes (skills, inert tunable, summary_model)
  - [#8901](https://github.com/zeroclaw-labs/zeroclaw/pull/8901): Strip comment bureaucracy across the tree

- **CI & release**:
  - [#9098](https://github.com/zeroclaw-labs/zeroclaw/pull/9098): Raise build matrix timeout to 90 minutes (v0.8.3 fix)
  - [#8874](https://github.com/zeroclaw-labs/zeroclaw/pull/8874): Fix rustdoc --default-theme scoping

---

## Community Hot Topics

**Most active discussions (by comment count):**

1. **[Bug #5600](https://github.com/zeroclaw-labs/zeroclaw/issues/5600)** (12 comments) — *kimi-code provider streaming error*: Open since April, still unresolved. Users report workflow-blocking failure when using `thinking` mode with compatible providers. The error trace suggests a mismatch between provider capability advertising and actual API behavior. **High community impact** as it affects any provider that advertises reasoning support.

2. **[RFC #7141](https://github.com/zeroclaw-labs/zeroclaw/issues/7141)** (7 comments, *closed*) — *OIDC authentication provider support*: Closed today, signaling a major security milestone. This tracking issue umbrellaed the pluggable auth-provider work now landed in PR #8672.

3. **[RFC #9048](https://github.com/zeroclaw-labs/zeroclaw/issues/9048)** (4 comments, *open*) — *Separate conversation history from agent-curated long-term memory*: Filed just two days ago but already gathering traction. The issue argues that runtime, gateway, and channel code are mixing `MemoryCategory::Conversation` with long-term memory, creating confusion between session logs and persisting knowledge.

4. **[Feature #8046](https://github.com/zeroclaw-labs/zeroclaw/issues/8046)** (4 comments, *open*) — *Optional Telegram webhook mode*: Users want webhook support alongside the current long-polling implementation, especially for public-facing deployments where latency matters.

**Underlying need**: The community is consistently asking for **reliable streaming** (multiple bug reports about hanging connections), **configurable provider behavior** (vision capability toggle), and **clearer memory lifecycle semantics** (separate conversation vs. persistent memory).

---

## Bugs & Stability

**New bugs reported today (2026-07-15 to 2026-07-16):**

| Issue | Severity | Summary | Fix PR? |
|-------|----------|---------|---------|
| [#9092](https://github.com/zeroclaw-labs/zeroclaw/issues/9092) | S2 - degraded | ZeroCode keystroke lag in long sessions (full history re-render) | None yet |
| [#9089](https://github.com/zeroclaw-labs/zeroclaw/issues/9089) | S2 - degraded | `[AUDIO:]` markers not recognized in tool output (only `[IMAGE:]` works) | None yet |
| [#9078](https://github.com/zeroclaw-labs/zeroclaw/issues/9078) | S2 - degraded | Serial transport desynchronized after non-matching response ID | None yet |

**Critical open bugs (S1 - workflow blocked):**
- [#5600](https://github.com/zeroclaw-labs/zeroclaw/issues/5600) — kimi-code streaming error (open since April, 12 comments, no fix)
- [#8559](https://github.com/zeroclaw-labs/zeroclaw/issues/8559) — Agents stop work when exiting web dashboard chat window
- [#8794](https://github.com/zeroclaw-labs/zeroclaw/issues/8794) — Stopping agent mid-work erases tool calls/thinking from context

**Stability note**: Today's merged PRs ([#8838](https://github.com/zeroclaw-labs/zeroclaw/pull/8838), [#9060](https://github.com/zeroclaw-labs/zeroclaw/pull/9060), [#9070](https://github.com/zeroclaw-labs/zeroclaw/pull/9070)) collectively address streaming reliability across five provider families and tool-call pairing logic, which should reduce the recurrence of stalled agent turns.

---

## Feature Requests & Roadmap Signals

**Hot features requested this week:**

1. **ZeroCode UI improvements** — Two features from `IftekharUddin`: show version in TUI top bar ([#9093](https://github.com/zeroclaw-labs/zeroclaw/issues/9093)) and clarify Code session history vs. persistent memory isolation ([#9047](https://github.com/zeroclaw-labs/zeroclaw/issues/9047))

2. **Turn-level OTel trace correlation** ([#6641](https://github.com/zeroclaw-labs/zeroclaw/issues/6641)) — Nest `llm.call` / `tool.call` / `memory.*` spans under a single turn trace. In-progress with 6 comments.

3. **RunPod/ComfyUI image generation** ([#7875](https://github.com/zeroclaw-labs/zeroclaw/issues/7875)) — Community member `Audacity88` wants provider-scoped config for RunPod, avoiding shared config bloat.

4. **CI coverage for firmware protocol** ([#9079](https://github.com/zeroclaw-labs/zeroclaw/issues/9079)) — New contributor `Rhoahndur` requests adding firmware crate tests to CI.

**Likely for next version (v0.9.0):** Based on RFC closures today, v0.9.0 will include the **OIDC auth provider** ([#7141](https://github.com/zeroclaw-labs/zeroclaw/issues/7141)), **pluggable security enforcement** ([#7142](https://github.com/zeroclaw-labs/zeroclaw/issues/7142)), and **A2A agent discovery** ([#7218](https://github.com/zeroclaw-labs/zeroclaw/issues/7218)). The **OpenAI-compatible chat completions endpoint** ([#8486](https://github.com/zeroclaw-labs/zeroclaw/pull/8486)) is also likely for v0.9.0.

---

## User Feedback Summary

**Pain points expressed today:**
- **Memory isolation confusion** — Users find it unclear when the Code tab writes to persistent memory vs. session history ([#9047](https://github.com/zeroclaw-labs/zeroclaw/issues/9047))
- **Agent interruption destroys context** — Susyabashti reports that stopping an agent mid-work erases tool calls and thinking from context ([#8794](https://github.com/zeroclaw-labs/zeroclaw/issues/8794)), a significant UX regression
- **Cannot work while agent is running** — Exiting the web dashboard chat window kills active agent tasks ([#8559](https://github.com/zeroclaw-labs/zeroclaw/issues/8559))
- **Audio support gap** — Tools that output audio markers (`[AUDIO:...]`) send literal text to the model instead of being parsed ([#9089](https://github.com/zeroclaw-labs/zeroclaw/issues/9089))
- **ZeroCode performance** — Keystroke lag in long sessions due to full history re-render ([#9092](https://github.com/zeroclaw-labs/zeroclaw/issues/9092))

**Satisfaction signals:** The rapid closure of RFCs and merge of security infrastructure suggests maintainers are shipping on schedule, which the community has responded to with constructive feature requests rather than complaints about stagnation.

---

## Backlog Watch

**Long-unanswered items needing maintainer attention:**

| Issue | Created | Age | Status | Risk |
|-------|---------|-----|--------|------|
| [#5600](https://github.com/zeroclaw-labs/zeroclaw/issues/5600) (kimi-code streaming) | 2026-04-10 | **97 days** | OPEN, P1, no-stale | High — blocks all kimi-code provider users |
| [#8358](https://github.com/zeroclaw-labs/zeroclaw/issues/8358) (zerorelay milestone) | 2026-06-26 | 20 days | OPEN, P2, no-stale | High — NAT traversal blocker |
| [#6641](https://github.com/zeroclaw-labs/zeroclaw/issues/6641) (OTel traces) | 2026-05-13 | 64 days | OPEN, P2, in-progress | Medium — observability gap |
| [#7821](https://github.com/zeroclaw-labs/zeroclaw/pull/7821) (SandboxPolicyConfig) | 2026-06-17 | 29 days | OPEN, needs-author-action | High — sandbox backend wiring not landed |
| [#8486](https://github.com/zeroclaw-labs/zeroclaw/pull/8486) (OpenAI endpoint) | 2026-06-29 | 17 days | OPEN, needs-author-action | High — 3rd-party integration enabler |

**Critical observation**: Issue #5600 (kimi-code provider streaming) has been open for 97 days with 12 comments and remains at P1 severity. This is the oldest unresolved workflow-blocking issue. The provider team has addressed related streaming issues (PR #8838 merged today), but the kimi-code specific error path may not be fully covered — worth a maintainer check.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*