# AI CLI Tools Community Digest 2026-07-12

> Generated: 2026-07-12 01:50 UTC | Tools covered: 9

- [Claude Code](https://github.com/anthropics/claude-code)
- [OpenAI Codex](https://github.com/openai/codex)
- [Gemini CLI](https://github.com/google-gemini/gemini-cli)
- [GitHub Copilot CLI](https://github.com/github/copilot-cli)
- [Kimi Code CLI](https://github.com/MoonshotAI/kimi-cli)
- [OpenCode](https://github.com/anomalyco/opencode)
- [Pi](https://github.com/badlogic/pi-mono)
- [Qwen Code](https://github.com/QwenLM/qwen-code)
- [DeepSeek TUI](https://github.com/Hmbown/DeepSeek-TUI)
- [Claude Code Skills](https://github.com/anthropics/skills)

---

## Cross-Tool Comparison

# Cross-Tool AI CLI Ecosystem Comparison Report
**Date: 2026-07-12 | Prepared for: Technical Leadership**

---

## 1. Ecosystem Overview

The AI CLI tools landscape continues to mature rapidly, with **eight major tools** now showing distinct evolutionary paths. **Claude Code, OpenAI Codex, and Gemini CLI** dominate community engagement (55+ comment threads on critical bugs), while **Qwen Code** and **CodeWhale** represent the fastest-growing open-source alternatives with intense infrastructure-focused iteration. A clear **platform divide** persists: macOS stability regressions plague both Claude Code and Codex, while Windows users face systemic sandbox and HCS service failures across Claude Code, Codex, and GitHub Copilot CLI. **MCP (Model Context Protocol) integration** has emerged as the dominant cross-cutting concern—every tool reported authentication, tool discovery, or lifecycle bugs. Notably, **GPT-5.6 model support** is driving rapid-fire provider patches across Pi, Codex, and OpenCode, with model catalog fragmentation creating integration friction.

---

## 2. Activity Comparison (Last 24 Hours)

| Tool | Hot Issues | New PRs | Release Status | Key Signal |
|------|-----------|---------|----------------|------------|
| **Claude Code** | 10 active | 5 PRs | No release | Windows Cowork blocker (#74649, 52 comments) |
| **OpenAI Codex** | 10 active | 10 PRs | No release | GPT-5.6 Sol subagent model forcing (#31814, 102 👍) |
| **Gemini CLI** | 10 active | 6 PRs | No release | Subagent false success reports (#22323, P1) |
| **GitHub Copilot CLI** | 10 active | 1 PR | No release | MCP OAuth token bridging failures (multiple issues) |
| **Kimi Code CLI** | 5 active | 5 PRs | No release | ACP server parity gap closed (#2490) |
| **OpenCode** | 10 active | 10 PRs | No release | GPT-5.6 Luna 404 bug (#36140, 70 👍) |
| **Pi** | 10 active | 14 PRs | No release | GPT-5.6 ecosystem wave (6+ related PRs) |
| **Qwen Code** | 10 active | 10 PRs | No release | Multi-workspace daemon RFC (#6378, 20 comments) |
| **DeepSeek TUI (CodeWhale)** | 6 active | 4 PRs | No release | Anthropic API tool schema strictness (#4329) |

**Observations:** Pi had the highest PR throughput (14 merged/opened) driven by GPT-5.6 support. No tool released a new version in the last 24 hours, suggesting a consolidation phase between release cycles.

---

## 3. Shared Feature Directions

The following requirements appear consistently across **3+** tool communities:

### Cross-Tool Priorities

| Requirement | Tools Requesting | User Pain Point |
|-------------|-----------------|-----------------|
| **Inter-session communication** | Claude Code (#24798), OpenCode (#16992 `/btw`), Pi (Ctrl-P history) | Multi-session workflows without context silos |
| **Configurable data directories** | Claude Code (#57998 Windows), Pi (session persistence), Gemini CLI (symlink support #20079) | Enterprise deployment, cloud-managed environments |
| **Session persistence & crash recovery** | Qwen Code (#6695, #6730), Copilot CLI (#4098 truncated events), Claude Code (#76769 MCP server respawn) | Loss of work after daemon restart or crash |
| **Usage/spend transparency** | Claude Code (#74709, #76793), Codex (#32486), Pi (#6347 token billing fix) | Cost management, unexpected model downgrades |
| **Subagent model selection** | Codex (#31814, #32291), Gemini CLI (#21968), Claude Code (Skill-constrained agents) | Mixing cheap/expensive models for orchestration vs. execution |
| **MCP authentication reliability** | Copilot CLI (#4085, #4089, #4096), Qwen Code (#6639 401 handling), Pi (#6496 OpenRouter affinity) | OAuth tokens that never bridge to sessions |
| **Platform-specific sandbox fixes** | Claude Code (#74649 Windows HCS), Codex (#32487 Windows Smart App Control), Gemini CLI (#21983 Wayland) | OS version fragmentation blocking entire user populations |
| **Tool output fidelity** | Qwen Code (#4077 YAML headers), Gemini CLI (#28247 `ls` globs), Claude Code (#76795 bash permissions) | Mismatch between tool-rendered content and actual file state |

### Emerging Pattern: Agent Transparency
Multiple tools (Gemini CLI #21763, #22598; Qwen Code #6487; Claude Code #24798) show growing demand for **visible subagent trajectories**, false-success detection, and memory index consistency. Users want to see *why* an agent failed, not just that it did.

---

## 4. Differentiation Analysis

| Dimension | Claude Code | OpenAI Codex | Gemini CLI | Pi | Qwen Code |
|-----------|-------------|-------------|-------------|-----|-----------|
| **Primary Focus** | Session orchestration, multi-agent workflows | MultiAgent V2 architecture, sandbox security | Agent reliability, memory systems | GPT-5.6 provider integration, TUI polish | Daemon lifecycle, workspace management |
| **Target User** | Power devs in enterprise Windows/macOS | CLI power users, MultiAgent orchestrators | Research/engineering teams | Individual devs, multi-provider users | Open-source teams, Chinese-language community |
| **Architecture** | Plugin-based (MCP), session-centric | Deferred executors, environment snapshots | Skills + subagents, config-heavy | Provider-abstracted, compact session model | Single-daemon, Web Shell + CLI hybrid |
| **Key Strength** | Community engagement (55+ comment threads) | Performance caching PRs (9 landed) | Systematic testing (76 eval tests) | Fastest PR throughput (14/day) | Infrastructure RFCs (multi-workspace) |
| **Key Weakness** | Windows ecosystem fragility | Rate-limit UI bugs, subagent steering | Agent hangs, opaque debugging | Model catalog fragmentation | Memory/index corruption over long sessions |
| **Release Cadence** | Moderate, security-focused | Moderate, infrastructure-heavy | Slower, quality-assurance oriented | Fast, GPT-5.6 driven | Fast, open-source volunteer driven |

### Strategic Position Notes
- **Claude Code** is the *community voice* leader—its issues attract the most engagement, but execution speed lags behind need (Windows fixes slow).
- **OpenAI Codex** is the *infrastructure innovator*—9 performance/caching PRs in one batch, but subagent UX (#31814) creates friction.
- **Pi** is the *fast follower*—aggressively merging GPT-5.6 support across all providers, winning community trust with speed.
- **Qwen Code** is the *architecture pioneer*—multi-workspace daemons and runtime channel control signal where the ecosystem is heading.
- **GitHub Copilot CLI** is struggling with **MCP integration quality**—multiple OAuth issues suggest this feature was rushed.

---

## 5. Community Momentum & Maturity

### Mature & High-Engagement
- **Claude Code**: Strongest per-issue engagement (average 15+ comments on top issues). Users self-organize to debug (@76802). Mature plugin ecosystem with security hardening PRs.
- **OpenAI Codex**: High upvote counts (432 👍 on #28224). Community actively collaborates on fixes (3 PRs merged for one bug). **Most systematic testing culture** (eval coverage expansion).

### Rapidly Iterating
- **Pi**: **14 PRs in 24 hours**—fastest cycle time. Developer role RFC (#6534) shows architectural ambition. GPT-5.6 wave suggests ability to pivot quickly.
- **Qwen Code**: **10 PRs + multi-workspace RFC** in one day. Strong Chinese-language ecosystem. Community is design-collaborative (20 comments on RFC).
- **CodeWhale**: 4 PRs/day, growing i18n base (Korean locale). NetBSD support signals BSD community interest.

### Struggling
- **GitHub Copilot CLI**: **1 PR in 24 hours** with 10 active issues. MCP OAuth bugs (#4085, #4089) show integration immaturity. Low community engagement (0 upvotes on most issues) suggests users may be migrating.
- **Kimi Code CLI**: Smallest issue volume (5). PRs fixing basic bugs (ellipsis width, missing timestamps) suggest earlier development stage.

### Maturity Metrics

| Tool | Avg. Comments/Top Issue | New Contributors (Implied) | Bug-to-Fix Latency |
|------|------------------------|--------------------------|-------------------|
| **Claude Code** | ~25 | Moderate | Slow (Windows, multi-week) |
| **OpenAI Codex** | ~35 | High (new PR authors) | Fast (3 PRs for one bug) |
| **Gemini CLI** | ~6 | Moderate | Moderate |
| **Copilot CLI** | ~1 | Low | Slow (1 PR/day) |
| **Pi** | ~2 | High (mitsuhiko, new contributors) | Fastest (same-day) |
| **Qwen Code** | ~7 | Moderate | Fast (same-day for recognized bugs) |

---

## 6. Trend Signals

### What the Community is Telling Us

1. **Agent reliability is the #1 market requirement.** Across all tools, the most-upvoted bugs involve agents hanging, lying about success, or ignoring user directives. **False success signals** (Gemini #22323, Copilot #4089) are uniquely damaging—they erode trust faster than crashes.

2. **MCP integration is harder than vendors expected.** Every tool reported authentication, tool discovery, or lifecycle bugs. The **OAuth token bridging gap** (Copilot CLI #4085, #4096; Qwen Code #6639) suggests the spec doesn't handle credential propagation well. **This is a standards gap**, not just implementation bugs.

3. **Session durability is the new black.** Users expect long-running sessions to survive daemon restarts, network interruptions, and model switches. Qwen Code's multi-workspace RFC and Claude Code's inter-session communication (#24798) point toward **session persistence as a platform feature**.

4. **Windows is the neglected stepchild.** Despite massive Windows user bases, Claude Code (#74649), Codex (#32487), and Copilot CLI (#4095) all have Windows-specific blockers with no confirmed workarounds. **Enterprise adoption will stall** without cross-platform parity.

5. **GPT-5.6 created a model catalog crisis.** Pi merged 6+ PRs just to handle model naming, endpoints, reasoning levels, and prompt cache options. Codex and OpenCode have Luna-not-found bugs. **Provider abstraction layers need urgent attention**—the current model of hardcoded tables doesn't scale.

6. **Open-source tools are catching up.** Qwen Code (10 PRs/day), CodeWhale (4 PRs/day), and Pi (14 PRs/day) are iterating faster than proprietary counterparts. The **Chinese-language ecosystem** (Qwen Code, Kimi Code) is particularly active, suggesting a geographic shift in contributor base.

### Recommendations for Developers

- **If you need reliability today:** OpenAI Codex (best testing culture) or Pi (fastest bug fixes)
- **If you need Windows support:** Wait. All Windows implementations are fragile. Consider Pi (agnostic provider layer) as a hedge.
- **If you need multi-session orchestration:** Claude Code's community is designing the patterns; Qwen Code's architecture supports it.
- **If you want to contribute:** Qwen Code (active RFCs, welcoming community) or CodeWhale (growing i18n, BSD support needed)

### Watch Items

- **MCP OAuth specification updates**—if the spec fixes token bridging, half the issues in Copilot CLI and Qwen Code disappear.
- **Claude Code Windows team velocity**—a Windows fix for #74649 would unblock enterprise adoption.
- **GPT-5.6 model catalog standardization**—watch for Pi's `models.dev` refactor (#35985) as potential industry pattern.
- **Session persistence protocols**—Qwen Code's `SessionRecoveryService` (#6730) may become reference architecture.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)

Here is the community highlights report based on the official `anthropics/skills` repository data.

---

## Claude Code Skills Community Highlights Report
**Date:** 2026-07-12 | **Source:** github.com/anthropics/skills

### 1. Top Skills Ranking (By Discussion Activity)

The most-watched Pull Requests reveal intense focus on tooling reliability, document quality, and workflow automation.

1.  **Skill-Creator Fixes (Multiple PRs)**
    - **PRs:** #1298, #1099, #1050, #1323, #362
    - **Summary:** A cluster of high-activity PRs addressing a critical bug where `run_eval.py` reports **0% recall** on every test query. The root cause spans Windows compatibility (subprocess pipes, `PATHEXT`, encoding) and logic errors in trigger detection. Multiple contributors (MartinCajiao, joshuawowk, gstreet-ops, Mr-Neutr0n) are collaborating to fix the core evaluation loop.
    - **Status:** All Open (Highly Active)

2.  **document-typography Skill**
    - **PR:** #514
    - **Summary:** Prevents orphan word wrap, widow paragraphs, and numbering misalignment in AI-generated documents. Addresses a universal pain point for Claude-generated reports and PDFs.
    - **Discussion:** Community users confirm these issues occur with every generated document. The skill is well-received for solving a problem users rarely think to ask for.
    - **Status:** Open ([View PR](https://github.com/anthropics/skills/pull/514))

3.  **ODT Skill (OpenDocument Format)**
    - **PR:** #486
    - **Summary:** Enables creation, template filling, and HTML conversion of `.odt` and `.ods` files (LibreOffice/OpenOffice).
    - **Discussion:** Strong demand for open-source document formats. Discussion focuses on template parsing reliability and binary file handling.
    - **Status:** Open ([View PR](https://github.com/anthropics/skills/pull/486))

4.  **Self-Audit Skill**
    - **PR:** #1367
    - **Summary:** A meta-skill that audits AI output before delivery. Features mechanical file verification followed by a four-dimension reasoning audit (damage-severity priority).
    - **Discussion:** High interest in output safety and verification. The zero-trust approach resonates with enterprise users demanding verifiable AI outputs.
    - **Status:** Open ([View PR](https://github.com/anthropics/skills/pull/1367))

5.  **testing-patterns Skill**
    - **PR:** #723
    - **Summary:** Comprehensive testing skill covering the Testing Trophy model, unit tests (AAA pattern), React Testing Library, and Cypress for E2E.
    - **Discussion:** Positive reception for full-stack coverage. Community requests include adding mocking examples and performance testing. Well-structured for developer onboarding.
    - **Status:** Open ([View PR](https://github.com/anthropics/skills/pull/723))

6.  **color-expert Skill**
    - **PR:** #1302
    - **Summary:** Self-contained color expertise covering naming systems (ISCC-NBS, Munsell, XKCD), color spaces (OKLCH, OKLAB, CAM16), and contrast safety.
    - **Discussion:** Unique and well-researched. Design-focused users appreciate the structured "what to use when" tables. Low controversy; high utility.
    - **Status:** Open ([View PR](https://github.com/anthropics/skills/pull/1302))

### 2. Community Demand Trends (From Issues)

The top Issues reveal five key demand vectors:

- **Security & Trust**: Issue #492 (34 comments) demands protection against namespace impersonation where community skills appear as official `anthropic/` skills. This is the most-discussed issue overall.
- **Skill-Creator Reliability**: Issues #556, #1169, and #1061 document the same 0% recall bug appearing across multiple environments. This is the **#1 blocker** for community skill creation.
- **Organizational Sharing**: Issue #228 requests native org-wide skill sharing without manual `.skill` file forwarding. Enterprise adoption hinges on this.
- **Deduplication**: Issue #189 identifies that `document-skills` and `example-skills` plugins distribute identical skill files, causing context-window bloat. This indicates poor plugin organization.
- **Platform Expansion**: Issue #29 requests Bedrock compatibility; Issue #16 proposes exposing skills as MCPs. Users want portability beyond Claude Code.

### 3. High-Potential Pending Skills (Active but Unmerged)

These PRs have active discussion and are likely to land soon:

| Skill | PR | Key Feature | Status |
|---|---|---|---|
| **skill-quality-analyzer** | #83 | Five-dimension meta-skill evaluation (structure, security, documentation) | Open, active |
| **SAP-RPT-1-OSS predictor** | #181 | Tabular foundation model for enterprise SAP data | Open, niche value |
| **Compact Memory** | #1329 (Issue) | Symbolic notation for reducing long-running agent context | Issue, strong concept |
| **Agent Governance** | #412 (Issue) | Safety patterns (policy enforcement, threat detection, audit) | Closed, but high interest |
| **Reasoning Quality Gate** | #1385 (Issue) | Pre-task calibration + adversarial review pipeline | New proposal, high potential |
| **web-artifacts-builder fix** | #1362 (Issue) | Fixes pnpm ≥10.1 builds, stale favicon, font inlining | Reproducible bugs, likely merged |

### 4. Skills Ecosystem Insight

**The community’s most concentrated demand is for a reliable, cross-platform skill-creation infrastructure—the core eval loop remains broken on Windows and produces 0% recall for all users, stalling the entire skill pipeline and outpacing demand for any single functional skill.**

The ecosystem is in a "tools before toys" phase: contributors are investing more in fixing the `run_eval.py` evaluator (5+ PRs, 3+ Issues) than in creating new skills. Until the skill-creator loop is stable, the community is unable to objectively optimize skill descriptions, making all new skill submissions effectively unvalidated.

---

# Claude Code Community Digest — 2026-07-12

## Today's Highlights

The community remains vocal about session-level quality-of-life improvements, with **inter-session communication** (Issue #24798) hitting 55 comments and a **Windows Cowork regression** (#74649) drawing 52 comments as a critical blocker. A new wave of macOS and Windows **connection stability bugs** (#75897, #76802) and **silent model fallback without user notification** (#76793) are generating fresh concern. Several minor bug reports and enhancement requests entered the queue, but no new releases landed today.

## Releases

No new releases in the last 24 hours.

## Hot Issues

1. **#24798 – Inter-session communication for multi-Claude workflows**  
   *Open · 55 comments · 18 👍*  
   Users running multiple parallel Claude Code sessions want direct message passing and dependency sequencing between them. Highly engaged discussion suggests this is a pressing need for large-project workflows.  
   [GitHub](https://github.com/anthropics/claude-code/issues/24798)

2. **#74649 – [BUG] Missing HCS services: vfpext — Cowork not working on Windows 11 Pro**  
   *Open · 52 comments*  
   A major Windows blocker: the `vfpext` HCS service is absent for some users, completely breaking Cowork functionality. No workaround confirmed yet.  
   [GitHub](https://github.com/anthropics/claude-code/issues/74649)

3. **#17951 – Terminal Title Configuration (Script-Based)**  
   *Open · 24 comments · 32 👍*  
   Users want the terminal title to be script-configurable (like `statusLine`) for better session identification in multi-tab environments. Strong community backing.  
   [GitHub](https://github.com/anthropics/claude-code/issues/17951)

4. **#36800 – Duplicate channel plugin process spawns causing 409 Conflict**  
   *Closed · 16 comments · 6 👍*  
   A mid-session bug that spawns duplicate Telegram plugin instances, causing cascading tool loss. Closed, but the root-cause pattern (lifecycle mismanagement) remains relevant.  
   [GitHub](https://github.com/anthropics/claude-code/issues/36800)

5. **#57998 – CLAUDE_DATA_DIR env var for Windows**  
   *Open · 10 comments · 12 👍*  
   Users on Windows want a configurable data directory to relocate `%APPDATA%\Claude`. Growing demand as cloud-managed Windows environments become more common.  
   [GitHub](https://github.com/anthropics/claude-code/issues/57998)

6. **#75897 – ConnectionRefused on macOS — persists after full reinstall**  
   *Open · 2 comments · 2 👍*  
   A regression on macOS 2.1.204 that makes the API unreachable despite a clean reinstall, safe mode, and reboot. No fix yet.  
   [GitHub](https://github.com/anthropics/claude-code/issues/75897)

7. **#76793 – Silent model fallback: Fable 5 → Opus 4.8 with no notification**  
   *Open · 1 comment*  
   Mid-session model downgrade without any user-facing notification when a usage limit is hit. Users demand at minimum a toast or chat notice.  
   [GitHub](https://github.com/anthropics/claude-code/issues/76793)

8. **#76795 – Bash permission matcher misparses quoted `|` in grep patterns**  
   *Open · 1 comment*  
   A subtle permissions bug: a quoted pipe character inside a grep argument defeats the allowlist matcher, forcing unnecessary user prompts.  
   [GitHub](https://github.com/anthropics/claude-code/issues/76795)

9. **#76500 – Agent Teams mailbox: 5-62 min delays, lost reports, queue leaks**  
   *Open · 1 comment*  
   Four distinct delivery defects in the experimental Agent Teams feature: turn-boundary delays up to 62 minutes, missing final reports, `/clear` queue leak, and stalled shutdown handshake.  
   [GitHub](https://github.com/anthropics/claude-code/issues/76500)

10. **#76769 – stdio MCP server SIGINT'd + not respawned ~4h after spawn (2.1.207 regression)**  
    *Open · 1 comment*  
    A regression in v2.1.207: stdio MCP servers are killed after 4 hours and not respawned, breaking long-running sessions. No workaround for the unreconnectable transport.  
    [GitHub](https://github.com/anthropics/claude-code/issues/76769)

## Key PR Progress

1. **#39043 – Remove "retro-futuristic" recommendation from Frontend Design Skill**  
   *Open* — A light touch by t3dotgg removing an opinionated style recommendation from the built-in Frontend Design skill.  
   [GitHub](https://github.com/anthropics/claude-code/pull/39043)

2. **#76673 – Fix reproducibility audit design defects (Japanese)**  
   *Closed* — Addresses audit findings in issue triage behavior, lifecycle state management, and hook execution safety.  
   [GitHub](https://github.com/anthropics/claude-code/pull/76673)

3. **#76640 – Load macOS system certificates and handle NO_PROXY blackhole for Bun runtime**  
   *Open* — Fixes "Self-signed certificate detected" errors on macOS when using Bun, by loading the system certificate store and fixing `NO_PROXY` environment variable handling.  
   [GitHub](https://github.com/anthropics/claude-code/pull/76640)

4. **#76581 – Harden YAML, path, and symlink handling in plugin scripts**  
   *Open* — Brings security hardening to official plugin examples: prevents YAML frontmatter breakout, path traversal, and symlink-based credential overwrite attacks.  
   [GitHub](https://github.com/anthropics/claude-code/pull/76581)

5. **#76576 – Align userConfig docs and hook validator with v2.1.207 shell-injection fix**  
   *Open* — Updates plugin documentation and validation to reflect that v2.1.207 now rejects `${user_config.*}` in shell-form hook commands and no longer reads `pluginConfigs` from project-level settings.  
   [GitHub](https://github.com/anthropics/claude-code/pull/76576)

## Feature Request Trends

- **Session orchestration & multi-session workflows**: The top-voted open feature (#24798) and several related requests (#76777 for `/fork` while busy) show strong demand for coordinating multiple Claude sessions rather than working in isolated silos.
- **Desktop ↔ CLI parity**: Users increasingly expect the Desktop app's Code window to match CLI capabilities — mid-task steering message injection (#71726) and terminal title configurability (#17951) are two prominent gaps.
- **Configurable data directories**: On Windows, the inability to relocate `%APPDATA%\Claude` (#57998) is a recurring pain point for enterprise and multi-user environments.
- **Spend & usage transparency**: Requests for threshold notifications at 80%/90%/100% spend (#74709) and visible model-switch notifications (#76793) reflect growing concern about cost management and unexpected behavior.
- **Pasted text editing**: Users want the ability to expand, view, and edit collapsed pasted text in the prompt before sending (#76801) — a small UX gap with outsized impact on workflows involving large code blocks.

## Developer Pain Points

1. **Windows ecosystem fragility**: Missing HCS services (#74649), `cmd.exe ENOENT` for preview (#68341), and WSL installation prompts on native Windows (#76804) continue to plague Windows users.
2. **Silent model and transport switches**: The lack of user notification when the model silently downgrades (#76793) or when MCP servers are killed and not respawned (#76769) undermines trust in session continuity.
3. **Connection instability**: Recurring reports of `ConnectionRefused` on macOS (#75897) and Windows (#76802) indicate underlying networking or certificate handling issues that evade simple reinstalls.
4. **Agent Teams reliability**: Despite being experimental, the mailbox defects (#76500) — multi-minute delays, lost reports, and incomplete shutdowns — make the feature nearly unusable for anyone who needs reliable task completion.
5. **Permission matcher brittleness**: The Bash permission regex failing on quoted arguments (#76795) continues a pattern (#16561, #27688, #30519) where subtle input patterns bypass security heuristics or cause unnecessary friction.
6. **Fable 5 safeguard over-triggering**: Multiple reports (#76800) of legitimate personal device configuration work (phone flashing, homelab setup) being flagged by Fable 5's safeguards and forcing model downgrades.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

# OpenAI Codex Community Digest — 2026-07-12

## Today's Highlights
The Codex community remains highly engaged, with a major cluster of attention around the **GPT-5.6 Sol subagent model forcing** (Issue #31814) and the **SQLite feedback log write amplification bug** (Issue #28224), which has been largely resolved after three merged PRs. A critical **Computer Use crash on macOS 15.7.7** (Issue #32032) and a **Windows sandbox failure** blocking Smart App Control users (Issue #32487) emerged as new platform-specific blockers. On the infrastructure side, a batch of 9 performance/caching PRs from late June landed this week, addressing deferred executors, environment snapshots, and MCP plugin metadata caching.

## Releases
No new releases in the last 24 hours.

---

## Hot Issues (10 selected)

### 1. [Bug/CLI/Performance] SQLite feedback logs can write ~640 TB/year and rapidly consume SSD endurance
- **Final status:** Issue #28224 (CLOSED after three merged PRs)
- **Why it matters:** This was a severe storage and hardware degradation bug. The 85% log reduction confirms the fix is effective, but the scale of the original problem (hundreds of TB/year) raised alarm across the community.
- **Community reaction:** 432 👍, 145 comments — high engagement, with active collaboration on debugging and testing the fix in PRs #29432, #29457, and (implied) #294XX.
- **Link:** https://github.com/openai/codex/issues/28224

### 2. [Bug/CLI/Subagent/Config] GPT-5.6 Sol cannot specify subagent models, forcing all subagents to also be Sol instances
- **Status:** OPEN, #31814
- **Why it matters:** This is a core architectural friction point for MultiAgent V2. Users who want to mix GPT-5.6 Sol (for orchestration) with cheaper models (e.g., GPT-5.5) for subagents cannot do so. The `hide_spawn_agent_metadata` flag hides far more than its name suggests, breaking documented workflows.
- **Community reaction:** 102 👍, 49 comments — significant, with detailed reproduction steps and frustrated references to the docs.
- **Link:** https://github.com/openai/codex/issues/31814

### 3. [Bug/App/Computer-Use] Computer Use 1.0.1000366 crashes at launch on macOS 15.7.7 due to missing Swift Concurrency symbol
- **Status:** OPEN, #32032
- **Why it matters:** This is a launch-blocker for an entire platform version. The native helper fails during dyld symbol resolution, preventing MCP/UI control initialization. The issue references #22822, suggesting a recurring problem.
- **Community reaction:** 11 👍, 20 comments — focused discussion, likely affecting macOS users on the latest OS update.
- **Link:** https://github.com/openai/codex/issues/32032

### 4. [Bug/Rate-Limits/App] Reset failed, did not apply and 1 reset is wasted
- **Status:** OPEN, #31606
- **Why it matters:** Rate-limit resets are a valuable paid resource. A UI or server-side bug that consumes a reset without applying it is a direct loss of value for users, eroding trust in the billing system.
- **Community reaction:** 41 👍, 34 comments — frustration is high, as the bug is easily reproducible and costly.
- **Link:** https://github.com/openai/codex/issues/31606

### 5. [Bug/CLI] `rg` is blocked by macOS
- **Status:** OPEN, #28190
- **Why it matters:** This is a platform compatibility issue affecting macOS users who rely on ripgrep (`rg`) for code search. The bug has been open for nearly a month with 46 comments and 71 👍, indicating a broad impact.
- **Community reaction:** 71 👍, 46 comments — many users report similar issues with other Unix tools, hinting at a systemic CI/signing problem.
- **Link:** https://github.com/openai/codex/issues/28190

### 6. [Bug/App/Session] Codex Desktop meta-bug: unbounded session/turn state causes freezes, context bloat, and lost active-turn control
- **Status:** OPEN, #25779
- **Why it matters:** This meta-bug captures a recurring class of session management failures. The unbounded state accumulation leads to freezes and context bloat, which affects heavy users running long sessions.
- **Community reaction:** 7 👍, 6 comments — lower engagement, but high relevance for power users.
- **Link:** https://github.com/openai/codex/issues/25779

### 7. [Bug/Windows/Sandbox] Windows sandbox fails with Smart App Control enabled because unsigned `node_repl.exe` is blocked
- **Status:** OPEN, #32487
- **Why it matters:** This is a new blocker for Windows 11 Pro users with Smart App Control enabled. The unsigned runtime binary prevents sandbox creation entirely, which is a security vs. usability conflict.
- **Community reaction:** 0 👍, 3 comments — early stage, but likely to grow as more Windows users encounter it.
- **Link:** https://github.com/openai/codex/issues/32487

### 8. [Enhancement/App] Codex desktop app for Linux
- **Status:** OPEN, #11023
- **Why it matters:** This is the most-upvoted open feature request (733 👍). Despite the macOS app being "almost unusable" (referenced existing bug), the Linux community remains persistent in requesting native support. This issue has been open for 5 months with 164 comments.
- **Community reaction:** 733 👍, 164 comments — sustained, high-urgency demand.
- **Link:** https://github.com/openai/codex/issues/11023

### 9. [Enhancement/CLI/Config/Plan] Add setting to disable the auto-resolve in 60 seconds for questions
- **Status:** OPEN, #28969
- **Why it matters:** The auto-resolve feature (where Codex auto-confirms an answer after 60 seconds) is a workflow disruptor for users who need to review or edit responses before accepting. This is a UX friction point that affects power users.
- **Community reaction:** 105 👍, 26 comments — strong demand for a configuration toggle.
- **Link:** https://github.com/openai/codex/issues/28969

### 10. [Bug/Extension/Skills/App-Server] Regression: newer VS Code Codex extension crashes on curated plugin `ngs-analysis` defaultPrompt >128 chars
- **Status:** OPEN, #28330
- **Why it matters:** This is a regression that breaks a curated plugin provided by the app-server, causing immediate crashes on fresh install. It demonstrates a CI/CD gap in validating plugin metadata length constraints.
- **Community reaction:** 7 👍, 6 comments — focused debugging, with users confirming the version boundary.
- **Link:** https://github.com/openai/codex/issues/28330

---

## Key PR Progress (10 selected)

### 1. [CLOSED] Publish new releases to R2
- **PR #31806** by `zsol-openai`
- **Summary:** Adds a shadow copy of Codex installer releases to Cloudflare R2 for faster/more reliable downloads, without changing existing GitHub Releases pipeline.
- **Why it matters:** Infrastructure improvement for CI/CD reliability and download performance.
- **Link:** https://github.com/openai/codex/pull/31806

### 2. [CLOSED] Core: inherit current step environments in subagents
- **PR #30016** by `sayan-oai` (code-reviewed)
- **Summary:** Fixes a stale-environment bug where subagents spawned after a deferred executor became available would inherit the old `TurnContext` snapshot instead of the current request-owned environment.
- **Why it matters:** Ensures subagents see correct filesystem state, fixing a class of session inconsistency bugs.
- **Link:** https://github.com/openai/codex/pull/30016

### 3. [CLOSED] Core: refresh turn diff roots from step context
- **PR #30017** by `sayan-oai`
- **Summary:** Fixes the diff tracker to use environment roots from the current step context, not the turn-start snapshot, so deferred/attached environments produce correct path formatting.
- **Why it matters:** Prevents incorrect diff display when environments become available mid-turn.
- **Link:** https://github.com/openai/codex/pull/30017

### 4. [CLOSED] Core: pass step environments to turn input extensions
- **PR #30020** by `sayan-oai`
- **Summary:** Extends the turn-input extension lifecycle to receive the first request-owned `StepContext`, allowing extensions to see the current environment.
- **Why it matters:** Enables extensions to act on the correct environment state, improving integration reliability.
- **Link:** https://github.com/openai/codex/pull/30020

### 5. [CLOSED] Cache stable executor skills and project them per model step
- **PR #29960** by `jif-oai` (code-reviewed)
- **Summary:** Caches skill metadata from stable executors so they are discovered once, not re-read per model step. Environmental changes trigger a cache refresh.
- **Why it matters:** Significant performance improvement for multi-step sessions, reducing repeated I/O and latency.
- **Link:** https://github.com/openai/codex/pull/29960

### 6. [CLOSED] Cache stable plugin metadata separately from live MCP runtimes
- **PR #29946** by `jif-oai` (code-reviewed)
- **Summary:** Separates plugin manifest caching (stable) from live MCP server connections (volatile), so a lost connection does not invalidate the cached metadata.
- **Why it matters:** Improves resilience and reduces unnecessary re-discovery when MCP servers reconnect.
- **Link:** https://github.com/openai/codex/pull/29946

### 7. [CLOSED] Make Windows executable resolution deterministic
- **PR #30036** by `jif-oai`
- **Summary:** Ensures that when `lpApplicationName` is absent, Windows resolves the executable after Codex applies the requested child environment, preventing accidental use of the wrong `PATH`.
- **Why it matters:** Fixes a class of platform-specific launch bugs where environment variables were ignored.
- **Link:** https://github.com/openai/codex/pull/30036

### 8. [CLOSED] CI: publish versioned bash fork artifacts
- **PR #30135** by `bolinfest`
- **Summary:** Establishes an independent, versioned artifact pipeline for the patched Bash shell (forked for Codex), following the same pattern used for zsh. Avoids rebuilding Bash for every Rust release.
- **Why it matters:** Reduces CI build times and artifact size by decoupling shell updates from Codex core releases.
- **Link:** https://github.com/openai/codex/pull/30135

### 9. [CLOSED] Restrict hosted threads to server-registered tools
- **PR #31526** by `richardc-oai`
- **Summary:** Adds a `server_registered_tools_only` feature flag that restricts hosted app-server sessions to only use tools from a strict MCP allowlist, preventing extraneous native/hosted/extension tools from being injected.
- **Why it matters:** Security and correctness — ensures server-controlled environments only use explicitly approved tools.
- **Link:** https://github.com/openai/codex/pull/31526

### 10. [CLOSED] Preserve parent sandbox enforcement for memory consolidation
- **PR #32441** by `copyberry[bot]`
- **Summary:** Passes the parent turn's permission profile (including sandbox overrides) to the memory consolidation agent, ensuring consolidated context respects original security boundaries.
- **Why it matters:** Prevents memory consolidation from escalating permissions or bypassing sandbox restrictions.
- **Link:** https://github.com/openai/codex/pull/32441

---

## Feature Request Trends

1. **Linux Desktop App** (Issue #11023, 733 👍) — Remains the single most-demanded feature. The community is persistent, with 164 comments over 5 months.
2. **Headless Remote Linux Hosts for Mobile** (Issue #23200, 31 👍) — Users want to use Codex mobile as a control layer for always-on Linux servers without requiring a desktop app to stay online.
3. **Disable Auto-Resolve** (Issue #28969, 105 👍) — A strong push for user-configurable behavior around the 60-second auto-resolve.
4. **Subagent Model Selection** — Multiple issues (#31814, #32291) request fine-grained control over which model is used for subagents, especially in MultiAgent V2.
5. **Configurable Context Window Warning** (Issue #32486) — Users want opt-in or warnings before sessions enter the higher-usage pricing band for GPT-5.6.

---

## Developer Pain Points

1. **Rate-Limit & Quota UI Bugs** — Multiple issues (#31606, #31322, #32410, #32484) report unreliable rate-limit displays, wasted resets, and fluctuating remaining quotas. This erodes trust in the billing system.
2. **Platform-Exclusive Sandbox Failures** — Windows-specific bugs (#22428, #28248, #32487) and macOS-specific bugs (#28190, #32032) create fragmented user experiences and block entire OS versions.
3. **Subagent & MultiAgent V2 Friction** — Issues #31814 and #32291 highlight that the subagent model steering is broken in practice, contradicting documentation and limiting advanced users.
4. **Session & State Management** — Issues #25779 and #30350 describe unbounded state accumulation, lost conversations, and unclear lifecycle for secondary/side sessions — a recurring pain point for power users.
5. **Extension Plugin Metadata Validation Gaps** — Issue #28330 demonstrates a regression where server-curated plugins with invalid metadata (defaultPrompt > 128 chars) crash the VS Code extension on install, indicating insufficient CI validation of plugin manifests.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>

# Gemini CLI Community Digest — 2026-07-12

## Today's Highlights
The Gemini CLI team continues churning on agent reliability, with long-standing bugs around subagent lifecycle and shell command hangs maintaining high community engagement. A significant batch of memory system quality issues from SandyTao520 remains active, while PRs this week bring long-awaited security improvements like circular reference guards in config merging and strict path trust checks for the A2A server. No releases dropped in the last 24 hours.

## Releases
None in the last 24 hours.

## Hot Issues
1. **[#22323 — Subagent recovery after MAX_TURNS is reported as GOAL success, hiding interruption](https://github.com/google-gemini/gemini-cli/issues/22323)**  
   Priority P1, 10 comments, 2 👍. The `codebase_investigator` subagent lies about having reached a goal when it actually hit `MAX_TURNS` before doing any analysis. This breaks trust in subagent self-reporting and makes debugging agent failures extremely difficult.

2. **[#24353 — Robust component level evaluations](https://github.com/google-gemini/gemini-cli/issues/24353)**  
   Priority P1, 7 comments. Tracks the expansion of behavioral eval coverage from an initial 76 tests to wider coverage across 6 supported Gemini models. Signals growing maturity in systematic quality assurance.

3. **[#21409 — Generalist agent hangs](https://github.com/google-gemini/gemini-cli/issues/21409)**  
   Priority P1, 7 comments, 8 👍. Community-flagged: deferring to the generalist agent causes indefinite hangs, even for trivial tasks like folder creation. Workaround (instructing the model not to use subagents) undermines the entire agent architecture.

4. **[#22745 — Assess the impact of AST-aware file reads, search, and mapping](https://github.com/google-gemini/gemini-cli/issues/22745)**  
   Priority P2, 7 comments, 1 👍. EPIC exploring AST-aware tools to reduce token waste and agent turns from misaligned file reads. High potential for improving agent efficiency on large codebases.

5. **[#21968 — Gemini does not use skills and sub-agents enough](https://github.com/google-gemini/gemini-cli/issues/21968)**  
   Priority P2, 6 comments. Anecdotal but important: users report custom skills and sub-agents are ignored unless explicitly invoked, even when the model is performing tasks they directly describe.

6. **[#25166 — Shell command execution gets stuck with "Waiting input" after command completes](https://github.com/google-gemini/gemini-cli/issues/25166)**  
   Priority P1, 4 comments, 3 👍. A recurring frustration: simple shell commands hang at "Awaiting user input" despite having finished. Breaks autonomous scripting workflows.

7. **[#26522 — Stop Auto Memory from retrying low-signal sessions indefinitely](https://github.com/google-gemini/gemini-cli/issues/26522)**  
   Priority P2, 5 comments. Auto Memory's extraction agent only marks sessions as processed when it reads them; low-signal sessions are retried forever, wasting API quota and compute.

8. **[#22672 — Agent should stop/discourage destructive behavior](https://github.com/google-gemini/gemini-cli/issues/22672)**  
   Priority P2, 3 comments, 1 👍. The model sometimes uses `git reset`, `--force`, or destructive DB operations when safer alternatives exist. Reflects a broader need for safety guardrails beyond prompt engineering.

9. **[#21983 — browser subagent fails in wayland](https://github.com/google-gemini/gemini-cli/issues/21983)**  
   Priority P1, 4 comments, 1 👍. Browser agent crashes on Wayland with a `GOAL` termination reason that masks the actual failure. Another instance of misleading success signals.

10. **[#20079 — ~/.gemini/agents/filename.md is not recognized as an agent if filename.md is a symlink](https://github.com/google-gemini/gemini-cli/issues/20079)**  
    Priority P2, 4 comments. Symlinks in the agents directory are silently ignored, breaking workflows that manage agent definitions across dotfile repos or package managers.

## Key PR Progress
1. **[#28359 — fix(core): strip login/interactive shell wrappers in stripShellWrapper](https://github.com/google-gemini/gemini-cli/pull/28359)**  
   Fixes a security gap where shell wrappers like `bash -lc "..."` were not recognized, bypassing the policy engine's re-checks. Essential for safe command execution.

2. **[#28349 — fix(cli): guard customDeepMerge against circular references](https://github.com/google-gemini/gemini-cli/pull/28349)**  
   Fixes #28270 — a crash in the settings manager when config objects contain circular references (e.g., `obj.self = obj`). Prevents `RangeError: Maximum call stack` from killing startup.

3. **[#28319 — refactor(a2a-server): enforce path trust check prior to environment loading](https://github.com/google-gemini/gemini-cli/pull/28319)**  
   Security hardening: ensures workspace path trust is verified **before** loading environment variables, preventing an untrusted workspace from leaking or modifying sensitive env state.

4. **[#28164 — fix(core): limit recursive reasoning turns per single user request](https://github.com/google-gemini/gemini-cli/pull/28164)**  
   Now closed. Caps recursive reasoning at 15 turns per request (configurable via `maxSessionTurns`). Protects against infinite loops consuming local CPU and API credits.

5. **[#28183 — fix(vscode-ide-companion): preserve terminal focus when closing diff tabs](https://github.com/google-gemini/gemini-cli/pull/28183)**  
   UX fix for VS Code companion: diff preview tabs no longer steal keyboard focus from the integrated terminal after approving edits. Reduces friction in iterative editing flows.

6. **[#28247 — fix(core): match ls ignore globs by relative path](https://github.com/google-gemini/gemini-cli/pull/28247)**  
   Fixes #28207. `ls` ignore patterns like `node_modules/**` now match against workspace-relative paths instead of only basenames. Uses `picomatch` for consistent glob semantics.

7. **[#28248 — docs: explain MCP env expansion](https://github.com/google-gemini/gemini-cli/pull/28248)**  
   Adds documentation for `$VAR`, `${VAR}`, `${VAR:-fallback}`, and Windows `%VAR%` syntax in MCP server path/environment config. Also documents unsupported syntaxes to reduce user confusion.

8. **[#28023 — chore(deps): bump @modelcontextprotocol/sdk from 1.23.0 to 1.26.0](https://github.com/google-gemini/gemini-cli/pull/28023)**  
   Dependency bump for the VS Code IDE companion. Closed; ensures compatibility with newer MCP specification features.

9. **[#28183 — (listed above, already counted)]**

10. **[#28359, #28349, #28319 — all listed above]**

## Feature Request Trends
- **AST-aware codebase tools:** Multiple issues (#22745, #22746) push for AST-based file reading, search, and codebase mapping to reduce token waste and agent turn count on large repositories.
- **Subagent transparency & control:** Users want subagent trajectories visible in `/chat share` (#22598), better bug reports that include subagent context (#21763), and tighter control over when subagents are invoked (#21968, #22093).
- **Destructive operation guardrails:** Growing demand for the agent to prefer safe alternatives over `--force`, `git reset`, or direct DB manipulation (#22672).
- **Self-awareness / documentation:** The CLI should be able to explain its own flags, hotkeys, and capabilities to users (#21432).
- **Memory system improvements:** Auto Memory needs limits on retry loops (#26522), proper redaction guarantees (#26525), and quarantine of invalid patches (#26523).

## Developer Pain Points
1. **Agent reliability is the #1 frustration.** The top-voted issues all involve agents hanging, incorrectly reporting success, or ignoring configuration (hangs: #21409 with 8 👍; waiting input: #25166 with 3 👍; false success: #22323).
2. **Subagent behavior is unpredictable.** Users report subagents running without permission after updates (#22093), and the generalist agent refusing to use custom skills (#21968).
3. **Configuration is fragile.** Symlinks are silently ignored in `~/.gemini/agents/` (#20079), circular references crash the settings manager (#28270), and `settings.json` overrides are ignored by the browser agent (#22267).
4. **Shell execution degrades UX.** Commands hang at "Waiting input" (#25166), Vite and other interactive prompts deadlock the agent (#22465), and the model litters temp scripts across the workspace (#23571).
5. **Debugging is opaque.** Bug reports lack subagent context (#21763), false success signals mask real failures (#22323, #21983), and there is no way to easily share subagent trajectories for review (#22598).

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

**Subject:** GitHub Copilot CLI Community Digest — July 12, 2026

---

### 1. Today's Highlights
This week’s digest is dominated by a surge of integration pain points, particularly around **MCP (Model Context Protocol) OAuth flows** and **Voice Mode reliability**. Multiple reports indicate that third-party MCP servers (especially Atlassian) show as "Connected" in the UI but expose zero tools to sessions, or drop connections after ~90 seconds. Additionally, a critical bug in `apply_patch` can permanently bloat session histories with deleted binary data, pushing conversations over the CAPI 5 MB limit. On the positive side, the community continues to push for better session sync across apps and dynamic context injection in Skills.

---

### 2. Releases
No new releases in the last 24 hours. The latest available build remains unchanged.

---

### 3. Hot Issues (10 noteworthy)

1. **#4024 – Voice mode: all bundled ASR models fail silently**  
   *[area:models]*  
   The `nemotron-3.5-asr-streaming-0.6b` and `nemotron-speech-streaming` models record audio but return empty transcriptions. Likely a `MultiModalProcessor` routing bug for RNNT in Foundry Local Core. 7 comments, no upvotes.  
   [Link](https://github.com/github/copilot-cli/issues/4024)

2. **#4098 – Resuming a session leaves truncated/concatenated events in events.jsonl**  
   *[triage]*  
   Malformed JSONL records prevent sessions from being resumed a second time. Discovered by user `Adamkadaban` with a reproducible payload. 2 comments.  
   [Link](https://github.com/github/copilot-cli/issues/4098)

3. **#4097 – apply_patch stores deleted binary in session history, permanently exceeding CAPI 5 MB limit**  
   *[triage]*  
   Deleting a large binary via `apply_patch` stores the entire binary as a textual diff in `result.detailedContent`. The `/compact` command cannot shrink this, breaking all subsequent requests. Zero comments.  
   [Link](https://github.com/github/copilot-cli/issues/4097)

4. **#4089 – Atlassian MCP server: OAuth succeeds but zero tools exposed**  
   *[area:authentication, area:mcp]*  
   OAuth completes, server shows green, but no `atlassian-*` tools appear. Other HTTP MCP servers (LeanIX, Lucid) work fine. 2 comments.  
   [Link](https://github.com/github/copilot-cli/issues/4089)

5. **#4096 – Third-party MCP server tools missing despite "Connected" badge (OAuth token never bridged)**  
   *[triage]*  
   Similar to #4089: OAuth tokens are stored but never passed to the CLI session agent. 0 comments.  
   [Link](https://github.com/github/copilot-cli/issues/4096)

6. **#4085 – MCP OAuth flow broken: servers marked needs-auth during discovery, connections drop after ~90s**  
   *[area:authentication, area:mcp]*  
   OAuth flow is initiated but immediately cancelled because no auth handler is registered. Even retries eventually mark servers as `needs-auth`. 0 comments.  
   [Link](https://github.com/github/copilot-cli/issues/4085)

7. **#4095 – Windows: plugin update fails with "Access is denied (os error 5)" when VS Code is running**  
   *[triage]*  
   The Copilot extension holds watcher handles on `installed-plugins`, blocking `copilot plugin update`. Workaround: close VS Code. 0 comments.  
   [Link](https://github.com/github/copilot-cli/issues/4095)

8. **#4094 – Deleting a session in the app doesn't remove it from session-store.db (orphaned session)**  
   *[triage]*  
   Sessions deleted from the Copilot app UI remain in the shared store, causing VS Code Copilot Chat to show ghost sessions. 0 comments.  
   [Link](https://github.com/github/copilot-cli/issues/4094)

9. **#4083 – Voice mode download fails with corporate proxy ENOTFOUND**  
   *[area:networking, area:installation]*  
   The Foundry Local Core runtime download does not respect corporate proxy settings. User provided a patch script. 0 comments.  
   [Link](https://github.com/github/copilot-cli/issues/4083)

10. **#4093 – web_search tool returns hallucinated answers with no grounding**  
    *[area:tools]*  
    The built-in AI-powered search returns confident but entirely fabricated citations when retrieval finds nothing relevant. 0 comments.  
    [Link](https://github.com/github/copilot-cli/issues/4093)

---

### 4. Key PR Progress (1 notable PR)

- **#2565 – install: guard against duplicate PATH entries on reinstall**  
  *Author: marcelsafin*  
  Running the installer twice appends PATH entries without deduplication. The PR adds a guard using `command -v copilot` but acknowledges it requires a shell restart to work. Updated July 11.  
  [Link](https://github.com/github/copilot-cli/pull/2565)

> *No other PR activity in the last 24h.*

---

### 5. Feature Request Trends

- **Session sync across apps** – Users want bidirectional sync of sessions between Copilot CLI and the Copilot Desktop App (Issue #4082).
- **Dynamic context injection in Skills** – Ability to run shell commands inline via `!`{cmd} in `SKILL.md` to inject live data, rather than relying on static context files (Issue #4088).
- **Voice mode UX improvements** – Auto-submit on spacebar release (PTT send) and temporary muting of system playback during voice capture (Issues #4090, #4092).
- **BYOK model discovery** – Allow custom providers to expose available models automatically rather than requiring manual `COPILOT_MODEL` configuration (Issue #3795).
- **Global instruction documentation** – Clearer docs on how `AGENTS.md` / `CLAUDE.md` / `instructions.md` are resolved in multi-project setups (Issue #3983).

---

### 6. Developer Pain Points

- **MCP OAuth is unreliable** – Multiple issues (#4084, #4085, #4086, #4089, #4096) report that OAuth-protected MCP servers show as connected but never expose tools. The token bridging from app UI to CLI session appears to be broken or incomplete.
- **Voice mode has systemic failures** – ASR models fail silently (#4024), proxy downloads time out (#4083), and UX shortcuts are missing (#4090, #4092).
- **Session/memory corruption** – Truncated JSONL events (#4098), orphaned session records (#4094), and unbounded binary blobs in `apply_patch` (#4097) all point to fragility in session store management.
- **Windows file locking** – VS Code holds handles on plugin directories, preventing updates (#4095).
- **Hallucinated web search** – The `web_search` tool fabricates answers when retrieval fails, undermining trust (#4093).

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

# Kimi Code CLI Community Digest
**Date: 2026-07-12**

---

## Today's Highlights

Three Fix PRs landed in the last 24 hours addressing long-standing quality-of-life bugs. A phantom `CHANGELOG` skill entry continues to confuse users, and a new fix ensures background agent tasks finally report their run duration. Meanwhile, the ACP server parity gap with the interactive CLI was closed—globally configured MCP servers now load for multi-session clients.

---

## Releases

No new releases in the last 24 hours.

---

## Hot Issues

1. **#2491 — Bug: `CHANGELOG.md` incorrectly listed as a skill**  
   *Author: zhangleilaoge*  
   The `/skill` autocomplete surfaces a `CHANGELOG` entry that points to a plugin's `CHANGELOG.md` rather than a valid skill definition. Users who rely on skill autocomplete may accidentally invoke a no-op. No comments or reactions yet.  
   [View Issue](https://github.com/MoonshotAI/kimi-cli/issues/2491)

2. **#1762 — Core bug that triggered PR #1771**  
   Tool message content arrays causing `400` errors in Chat Completions API. This has been open since April and is finally being addressed.  
   [View Issue](https://github.com/MoonshotAI/kimi-cli/issues/1762)

3. **#2464 — ACP server missing global MCP config**  
   Multi-session clients (Zed, JetBrains) only see built-in tools. This parity gap has been a top user complaint for weeks.  
   [View Issue](https://github.com/MoonshotAI/kimi-cli/issues/2464)

4. **MCP server connection failures crash workers**  
   Uncaught `MCPRuntimeError` from port conflicts or network issues leaves the frontend stuck in "thinking" indefinitely.  
   [Referenced in PR #1769](https://github.com/MoonshotAI/kimi-cli/pull/1769)

5. **Background agent tasks missing duration**  
   Unlike bash tasks, agent tasks never set `runtime.started_at`, so users can't see how long background operations took.  
   [Referenced in PR #2493](https://github.com/MoonshotAI/kimi-cli/pull/2493)

6. **`shorten_middle` function overshoots target width**  
   Truncation does not account for `"..."` ellipsis length, causing output to be up to 3 characters too wide.  
   [Referenced in PR #2492](https://github.com/MoonshotAI/kimi-cli/pull/2492)

7. **Global MCP config not loaded in ACP server**  
   Duplicate concern to #2464; affects all external tool integrations.  
   [Referenced in PR #2490](https://github.com/MoonshotAI/kimi-cli/pull/2490)

---

## Key PR Progress

1. **#1771 — fix: always stringify tool message content in Chat Completions provider**  
   *Author: he-yufeng*  
   Converts `content` arrays to strings for `role: "tool"` messages, fixing `400` errors when multiple `ContentPart`s are returned. Critical for providers that enforce strict schema compliance.  
   [View PR](https://github.com/MoonshotAI/kimi-cli/pull/1771)

2. **#1769 — fix: graceful degradation when MCP server fails to connect**  
   *Author: he-yufeng*  
   Catches `MCPRuntimeError` in `_agent_loop()` to prevent worker crashes and frontend freezes. Now logs the error and continues with degraded tool access.  
   [View PR](https://github.com/MoonshotAI/kimi-cli/pull/1769)

3. **#2493 — Fix: record started_at for background agent tasks**  
   *Author: nankingjing*  
   Mirrors the bash worker behavior — sets `runtime.started_at` during agent task startup so users can finally see how long background operations run.  
   [View PR](https://github.com/MoonshotAI/kimi-cli/pull/2493)

4. **#2492 — fix: shorten_middle output exceeds target width by ellipsis length**  
   *Author: nankingjing*  
   Adjusts left/right slice computations to reserve 3 characters for the `"..."` ellipsis. Small but impactful for terminal UI alignment.  
   [View PR](https://github.com/MoonshotAI/kimi-cli/pull/2492)

5. **#2490 — fix(acp): load global MCP config in kimi acp server**  
   *Author: nankingjing*  
   Reuses the MCP config loading logic from the interactive CLI so `kimi acp` users see their custom tools. Closes #2464.  
   [View PR](https://github.com/MoonshotAI/kimi-cli/pull/2490)

---

## Feature Request Trends

- **Global MCP config parity across all CLI modes** — Users expect the same custom tools whether in interactive `kimi`, background tasks, or ACP sessions. PR #2490 addresses this directly.
- **Better error handling for MCP connection failures** — Instead of silent crashes or infinite "thinking" states, users want graceful degradation with clear logs.
- **Consistent telemetry for background operations** — Both bash and agent tasks should track and report duration, status transitions, and completion outcomes.
- **String/ellipsis handling in utility functions** — Small but recurring formatting bugs erode trust in terminal output accuracy.

---

## Developer Pain Points

- **Phantom skill entries** – Autocomplete shows non-skill files (`CHANGELOG.md`), wasting developer time and disrupting workflows.
- **Inconsistent background task tracking** – Agent tasks silently lose duration data while bash tasks correctly record it, creating confusion and making performance debugging harder.
- **ACP server tool parity** – Users configuring MCP servers for interactive use are frustrated when third-party editors and orchestrators can't see them.
- **String formatting off-by-one errors** – Truncation functions that exceed width targets cause visual glitches in terminal UIs, especially in status bars and logs.

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

# OpenCode Community Digest — 2026-07-12

## Today's Highlights
This week's digest focuses heavily on the **GPT-5.6 Luna integration bug** (#36140), which has been breaking OAuth-based usage for many users and has accumulated **70 upvotes**. CPU usage regressions remain a persistent pain point across multiple versions. On the PR side, a batch of **V2 TUI fixes** from kitlangton and the community landed today, fixing duplicate log events, subagent picker behavior, and server startup error messages. A new `opencode run --help` experience is also being refined with improved error propagation.

## Releases
No new releases were published in the last 24 hours.

## Hot Issues (Top 10)

1. **#36140 — GPT-5.6 Luna returns model not found with ChatGPT OAuth** (👍 70)
   A critical bug where `gpt-5.6-luna`, listed as a built-in OpenAI model, fails with HTTP 404 when using ChatGPT OAuth. Workaround exists (fallback to `gpt-4.1`), but the model selector is broken for many. A corresponding PR (#36476) is open.  
   [GitHub](https://github.com/anomalyco/opencode/issues/36140)

2. **#16992 — [FEATURE]: add /btw command** (👍 153)
   Inspired by Anthropic's Claude Code, this is the most upvoted feature request this cycle. The `/btw` command lets developers provide additional context mid-conversation without interrupting the model's current output.  
   [GitHub](https://github.com/anomalyco/opencode/issues/16992)

3. **#30086 — High CPU usage in newer versions of OpenCode** (👍 13)
   A recent regression causing high CPU use even with few sessions. Users report system-wide lag with 3+ sessions, where 10 were previously fine.  
   [GitHub](https://github.com/anomalyco/opencode/issues/30086)

4. **#8806 — [FEATURE]: Provide llms.txt and docs as markdown** (👍 35)
   Request for structured docs (`llms.txt`) so LLM tools can ingest OpenCode documentation more effectively. Reflects a growing demand for AI-friendly project documentation.  
   [GitHub](https://github.com/anomalyco/opencode/issues/8806)

5. **#4751 — [CLOSED] Add config option to disable copy-on-select** (👍 18)
   Closed as resolved after 25 comments. Users with the habit of selecting text while reading were frustrated by clipboard pollution. A config toggle was added.  
   [GitHub](https://github.com/anomalyco/opencode/issues/4751)

6. **#29548 — OpenAI provider headers timeout after 10000ms** (👍 4)
   A regression in v1.15.11 broke OpenAI provider requests for some users. Workaround: manually increase `headerTimeout`. The team is investigating the root cause.  
   [GitHub](https://github.com/anomalyco/opencode/issues/29548)

7. **#19466 — OpenCode using CPU while waiting for API rate limits** (👍 11)
   Idle CPU usage hits ~50% of a core during API retry backoff. Users expect near-zero CPU when simply waiting.  
   [GitHub](https://github.com/anomalyco/opencode/issues/19466)

8. **#22132 — OpenCode hangs with local Ollama provider** (👍 5)
   Simple prompts hang when using Ollama via `@ai-sdk/openai-compatible`. Direct API calls to `/v1/chat/completions` work fine, pointing to an integration bug.  
   [GitHub](https://github.com/anomalyco/opencode/issues/22132)

9. **#36247 — GPT-5.6 Codex OAuth uses wrong context limits** (👍 0 but high signal)
   Codex OAuth inherits the wrong input budget for GPT-5.6 models. The model thinks it has 1.05M metadata context, but the actual backend limit is 500k total.  
   [GitHub](https://github.com/anomalyco/opencode/issues/36247)

10. **#36465 — "Revert message" should not modify code without warning** (👍 0)
    A UX concern: the revert feature silently restores old code state, which can corrupt Git history if used on old conversations. Requesting a confirmation dialog.  
    [GitHub](https://github.com/anomalyco/opencode/issues/36465)

## Key PR Progress (Top 10)

1. **#36479 — fix(tui): lower durable event log level** (CLOSED)
   Fixes duplicate log lines when multiple TUI clients are connected. Events now logged at DEBUG level to avoid massive log growth.  
   [GitHub](https://github.com/anomalyco/opencode/pull/36479)

2. **#36478 — fix(cli): preserve server startup failure cause** (OPEN)
   Improves error messages when the background server fails. Before: "Failed to start server". After: "Failed to start server: NotFound: FileSystem.rea...".  
   [GitHub](https://github.com/anomalyco/opencode/pull/36478)

3. **#36477 — fix(core): settle malformed tool input on failure** (CLOSED)
   Malformed streamed tool JSON now produces one truthful failure instead of two (the second caused by the unresolved call at the next prompt).  
   [GitHub](https://github.com/anomalyco/opencode/pull/36477)

4. **#36480 — fix(tui): improve subagent picker states** (OPEN)
   Distinguishes foreground (spinner) vs backgrounded (label) subagents in the V2 picker. Keeps Ctrl-B backgrounding active.  
   [GitHub](https://github.com/anomalyco/opencode/pull/36480)

5. **#36475 — fix(cli): keep update preflight visible through TUI loading** (OPEN)
   Previously, the "Ready" footer destroyed the renderer, leaving a blank terminal while the TUI initialized. Now the preflight stays visible until loading completes.  
   [GitHub](https://github.com/anomalyco/opencode/pull/36475)

6. **#36471 — feat(tui): paste clipboard on right click** (OPEN)
   Enables right-click to paste in the TUI prompt when mouse capture is active. Addresses a common usability gap for mouse users.  
   [GitHub](https://github.com/anomalyco/opencode/pull/36471)

7. **#36469 — fix(tui): respect sidebar width threshold** (OPEN)
   Removes an override that caused the sidebar to reopen unexpectedly. Persisted `autoHide` setting now controls sidebar visibility correctly.  
   [GitHub](https://github.com/anomalyco/opencode/pull/36469)

8. **#35985 — fix(provider): derive reasoning variants from models.dev** (OPEN)
   Major refactor: instead of hardcoding model ID/version tables, reasoning variants are now derived from `models.dev`. Shares mappings across Core and legacy paths.  
   [GitHub](https://github.com/anomalyco/opencode/pull/35985)

9. **#35762 — fix(tui): restore subagent navigation** (OPEN)
   Closes three related issues (#34457, #32432, #15972) by restoring nested subagent navigation and fixing cancelled subagent interactions.  
   [GitHub](https://github.com/anomalyco/opencode/pull/35762)

10. **#36468 — fix(opencode): preserve valid empty JSON config** (OPEN)
    Fixes a bug where inserting `$schema` into an empty config object added a trailing comma, breaking JSON validity.  
    [GitHub](https://github.com/anomalyco/opencode/pull/36468)

## Feature Request Trends

- **"By the way" context injection** (#16992, 153 👍) — The most-requested feature. Users want to add mid-response context without interrupting the model's output.
- **AI-friendly documentation** (#8816, 35 👍) — Demand for `llms.txt` and structured markdown docs so LLMs can reference OpenCode docs internally.
- **Session picker on startup** (#36134) — Users want `opencode --resume` or `opencode -s` to quickly pick from recent sessions without remembering session IDs.
- **Opt-in anonymized data sharing** (#35303) — A small but vocal group of users wants to volunteer conversation data to improve open-source models.
- **Bell ANSI for user acknowledgment** (#36472) — A notification bell when the model requires user input or finishes processing, useful for tmux/pane workflows.

## Developer Pain Points

- **CPU usage regressions** (multiple issues: #30086, #4804, #19466) — The #1 source of frustration. CPU spikes during idle, API backoff, and normal use are a recurring theme across versions. Users are downgrading to older releases.
- **GPT-5.6 Luna + Codex OAuth failures** (#36140, #36247, #36427) — Model not found errors and incorrect context limits are blocking users who rely on the latest OpenAI models.
- **Config parsing fragility** (#36468, #36458) — Invalid JSON from `$schema` insertion, ignored TUI config, and broken `--log-level` are wasting developer time on configuration debugging.
- **Provider timeout regressions** (#29548, #22132) — Both OpenAI and Ollama providers have seen regressions failing with timeouts or hangs, forcing users to dig into config workarounds.
- **Duplicate event logging** (#36283, #36446, #36479) — For multi-client setups, identical events are logged N times per event, producing rapid log growth and performance issues.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>

# Pi Community Digest — 2026-07-12

## Today's Highlights
GPT-5.6 family (Sol/Terra/Luna) support dominated today’s activity, requiring coordinated fixes across providers, reasoning levels, prompt caching, and compaction. The team merged 14 PRs in the last 24 hours, with major work on Codex WebSocket account binding and a new developer message role RFC making its first appearance.

## Releases
No new releases in the last 24 hours.

## Hot Issues

1. **[#6475 — Add GPT-5.6 (Sol/Terra/Luna) to GitHub Copilot provider](https://github.com/earendil-works/pi/issues/6475)** (👍 8)  
   GitHub Copilot rolled out GPT-5.6 models today. Community enthusiasm is high, driving rapid downstream fixes across reasoning, caching, and compaction.

2. **[#6097 — Add support for 'max' thinking level](https://github.com/earendil-works/pi/issues/6097)** (👍 18)  
   GPT-5.6 Sol introduces a sixth `max` reasoning level mirroring Anthropic’s Opus. The highest-voted open request this week; OpenAI just announced these capabilities.

3. **[#5916 — Support provider extensions with model aliases and improve search](https://github.com/earendil-works/pi/issues/5916)** (12 comments)  
   Users need a UI/extension point to configure OpenRouter provider overrides. Currently requires hand-editing `models.json` for per-model API keys and model mapping.

4. **[#6524 — Hide GPT-5.6 reasoning-summary empty placeholders](https://github.com/earendil-works/pi/issues/6524)**  
   Thinking blocks show empty HTML comments (`<!-- -->`) with GPT-5.6 Terra/Sol. Visual polish issue affecting user experience at the reasoning-summary boundary.

5. **[#6502 — Windows Terminal scrolls to top when pi-tui sends ESC[3J](https://github.com/earendil-works/pi/issues/6502)**  
   TUI redraw clears terminal scrollback buffer via `\x1b[3J`. Windows Terminal interprets this aggressively, breaking scroll position on every redraw.

6. **[#6456 — ctrl-p should show previous prompt / input](https://github.com/earendil-works/pi/issues/6456)**  
   UX friction: muscle memory from bash/Codex/Claude expects Ctrl-P for history navigation, but Pi uses it for model switching. Simple ergonomic regression.

7. **[#6513 — Codex cached WebSocket retains previous account after credentials change](https://github.com/earendil-works/pi/issues/6513)**  
   Security-sensitive bug: switching accounts mid-session can route user B’s requests through user A’s authenticated socket, leaking `previous_response_id` continuity.

8. **[#6522 — openai-completions: no min floor on max_completion_tokens, sends 1 token → 400](https://github.com/earendil-works/pi/issues/6522)**  
   With compaction disabled and inflated context ratios, clamped `max_tokens` can round to 1, causing non-recoverable 400 errors. A clamping regression from #6206.

9. **[#6498 — Tools and system prompt CLI options not persisted in session](https://github.com/earendil-works/pi/issues/6498)**  
   `-t`, `-nt`, `--system-prompt` flags are lost on session resume (`-r`/`-c`). Breaks workflows that require consistent tooling across sessions.

10. **[#6472 — compaction.enabled=false bypassed by overflow recovery path](https://github.com/earendil-works/pi/issues/6472)**  
    Setting `compaction.enabled: false` is ineffective—overflow recovery triggers compaction regardless. User intent is fully ignored in edge cases.

## Key PR Progress

1. **[#6534 — feat(ai): add developer message role](https://github.com/earendil-works/pi/pull/6534)** (OPEN)  
   Experimental PR by mitsuhiko implementing [RFC 54](https://rfc.earendil.com/0054/). Adds a `developer` message role alongside existing `user`/`assistant`. Early-stage but architecturally significant.

2. **[#6496 — fix(ai): support OpenRouter session affinity](https://github.com/earendil-works/pi/pull/6496)** (OPEN)  
   OpenRouter requires `session_id` in headers for prompt caching stickiness. Builds on existing per-provider header customization introduced in 0.80.x.

3. **[#6533 — fix: Codex compaction returns "Model not found" for gpt-5.6-luna](https://github.com/earendil-works/pi/pull/6533)** (OPEN)  
   GPT-5.6 Luna fails on compact/auto-compact through Codex API. The internal model slug mapping doesn’t recognize the tier-suffixed form used by compaction’s no-tools registry.

4. **[#6544 — fix(ai): route GitHub Copilot MAI-Code models through /responses endpoint](https://github.com/earendil-works/pi/pull/6544)** (OPEN)  
   Follows #6538; routes `mai-code-1-flash-picker` to Copilot’s `/responses` endpoint instead of the non-functional `/chat/completions`.

5. **[#6539 — fix(ai): bind Codex WebSocket reuse to account](https://github.com/earendil-works/pi/pull/6539)** (CLOSED)  
   Fixes #6513 by keying cached WebSockets on normalized endpoint + JWT account claim. Prevents cross-account request leaking during credential changes.

6. **[#6528 — fix(ai): support GPT-5.6 prompt cache options](https://github.com/earendil-works/pi/pull/6528)** (CLOSED)  
   Adds `prompt_cache_options: { mode: "implicit", ttl: "30m" }` for GPT-5.6 OpenAI Responses. Legacy models keep existing `prompt_cache_retention` behavior.

7. **[#6530 — perf(coding-agent): cut Node CLI startup cost](https://github.com/earendil-works/pi/pull/6530)** (CLOSED)  
   Fast-paths `--version` before loading main module tree; moves Bun-only virtual module imports out of Node path. Reduces cold-start latency significantly.

8. **[#6532 — Fix Bedrock AWS_PROFILE authentication regression](https://github.com/earendil-works/pi/pull/6532)** (CLOSED)  
   After Bedrock API-key support landed, `getEnvApiKey()`’s internal `<authenticated>` string was sent as a bearer token, causing 403s. Separates credential type from value.

9. **[#6540 — fix(coding-agent): surface provider errors to the LLM via advisories](https://github.com/earendil-works/pi/pull/6540)** (CLOSED)  
   Context overflow, retry exhaustion, and compaction failures were silently dropped. Now injected as advisories so the LLM can recover instead of producing silent failures.

10. **[#6474 — feat(ai): support message-anchored tool loading](https://github.com/earendil-works/pi/pull/6474)** (CLOSED)  
    Enables tools to be introduced mid-conversation via `addedTools` in messages, rather than requiring all tools in the initial request. Leverages Anthropic’s tool-reference support.

## Feature Request Trends

- **GPT-5.6 ecosystem integration** dominates: prompt cache options, Responses Lite, reasoning level `max`, compact/message-anchored tool loading, and model catalog entries across OpenAI, Codex, and GitHub Copilot providers.
- **Provider flexibility** is a close second: users want OpenRouter model aliases (extensible via UI), LLM Gateway as a built-in provider, and GitHub Copilot `auto` pseudo-model for tier-limited accounts.
- **Extension API maturation**: opaque attachments in RPC, deferred reload requests, compaction lifecycle hooks, and public `pi-ai` API subpath exports are all being actively shaped.
- **Context visibility**: users repeatedly ask for pre-configuration impact estimates for extensions/skills, and for compaction summaries respecting session locale.

## Developer Pain Points

- **Windows Terminal rendering**: the `\x1b[3J` scrollback-clear sequence breaks scrolling in Windows Terminal. Users expect cross-platform TUI stability.
- **Credential/account lifecycle bugs**: Bedrock `AWS_PROFILE` regression, Codex WebSocket account leaking, and OpenRouter session affinity gaps all point to insufficient credential-context isolation.
- **Configuration intent not respected**: `compaction.enabled: false` silently bypassed, CLI flags lost on session resume, CLI options not serialized—users expect explicit settings to be authoritative.
- **Model catalog fragmentation**: GPT-5.6 requires different endpoints (`/responses` vs `/chat/completions`), different payloads (prompt cache options, reasoning levels), and different compaction paths per provider—each gap causes 400/404 failures in production.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>

# Qwen Code Community Digest — 2026-07-12

## Today's Highlights

The Qwen Code project is experiencing a major infrastructure push around **daemon lifecycle management**, with multiple RFCs and PRs targeting multi-workspace support, session crash recovery, and runtime channel control. Meanwhile, a cluster of bugs around **memory compaction**, **clipboard handling**, and **token limits for Claude Opus 4.6+** have been closed with fixes landing. The community is actively contributing to Web Shell UX improvements, particularly around workspace context, git branch display, and inline composer tooltips.

## Releases

No new releases in the last 24 hours. The latest stable is likely the prior version (0.19.x, suggested by issue references).

---

## Hot Issues (10 of 30)

### 🔥 Critical / High Attention

1. **[RFC] Support multiple workspaces in one qwen serve daemon** [#6378](https://github.com/QwenLM/qwen-code/issues/6378)
   - *20 comments* — An RFC proposing a shift from `1 daemon = 1 workspace × N sessions` to a multi-workspace model. This would fundamentally change how teams manage isolated projects via a single daemon. The discussion is deep, with implications for auth, session routing, and CLI ergonomics.

2. **Daemon restart drops workspaces registered from Web Shell** [#6726](https://github.com/QwenLM/qwen-code/issues/6726)
   - *Closed* — Confirms that dynamically added workspaces are ephemeral; daemon restart loses them. Directly related to #6378. Community consensus: workspace persistence must be part of the multi-workspace RFC.

3. **Deferred tool discovery invalidating prompt cache prefixes** [#6721](https://github.com/QwenLM/qwen-code/issues/6721)
   - *4 comments, open* — When a deferred tool is revealed, the real schema is injected into provider tool declarations, breaking prompt caching. This is a performance regression for long sessions. PR #6723 addresses the fix.

4. **Memory index stale after `/remember`; content lost on compaction** [#6487](https://github.com/QwenLM/qwen-code/issues/6487)
   - *3 comments, open* — Two independent memory degradation mechanisms: stale in-memory index after `/remember`, and managed-memory content cleared by microcompaction. Duplicate report in #6713. The community sees this as a critical UX blocker for long-running agents.

5. **Claude Opus 4.6–4.8 fall back to incorrect 200K/64K limits** [#6719](https://github.com/QwenLM/qwen-code/issues/6719)
   - *Closed* — Opus 4.7/4.8 were not recognized in token-limit rules, falling back to generic Claude 200K input / 64K output instead of the official 1M/128K. Also: #6734 fixed an off-by-one where `128k` was `131072` vs Anthropic's `128000`.

### 🐞 Bugs with Community Engagement

6. **JetBrains ACP agent does not receive user prompt** [#6581](https://github.com/QwenLM/qwen-code/issues/6581)
   - *8 comments, closed* — IntelliJ user prompt is not forwarded to Qwen Code agent when using local Ollama models. The bootstrap context arrives, but the actual user message is dropped. Community identified the root cause in ACP protocol handshake.

7. **MCP servers with HTTP transport show offline on 401** [#6639](https://github.com/QwenLM/qwen-code/issues/6639)
   - *3 comments, closed* — OAuth recovery flow is not triggered for HTTP-transport MCP servers that return 401. Servers permanently show "offline". PR #6732 provides the fix.

8. **DashScope/Qwen models return empty content intermittently** [#6670](https://github.com/QwenLM/qwen-code/issues/6670)
   - *1 comment, closed* — Stream occasionally returns empty or truncated responses, causing `InvalidStreamError`. Affects qwen3-max and qwen3.7-max. Community requesting rate-limit awareness and retry logic.

9. **read_file adds extra rendering (YAML/Markdown headers)** [#4077](https://github.com/QwenLM/qwen-code/issues/4077)
   - *2 comments, still open since May* — `read_file` transforms content (e.g., adding `---`) before output, causing `edit_file` to fail because the LLM uses transformed content for search. Old but still unresolved — community frustration is visible.

10. **Ctrl+V paste broken on macOS standalone** [#6590](https://github.com/QwenLM/qwen-code/issues/6590)
    - *5 comments, closed* — Missing native module `@teddyzhu/clipboard` in standalone macOS builds. Image paste silently fails. PR with fix welcome; root cause and patch are well-documented in the issue.

---

## Key PR Progress (10 of 20)

### Infrastructure & Daemon

1. **Feat: Runtime daemon channel control** [#6741](https://github.com/QwenLM/qwen-code/pull/6741) — *Open* — Adds HTTP endpoints and CLI commands (`qwen channel`) for enabling/reloading/stopping channel workers at runtime. Critical for teams that need to swap model providers without daemon restart.

2. **Feat: Extension management v2 for `qwen serve`** [#6638](https://github.com/QwenLM/qwen-code/pull/6638) — *Open* — Introduces per-workspace activation policies for extensions, layered over shared user-level artifacts. Enables workspace-specific tool configurations.

3. **Feat: Support runtime workspace removal** [#6745](https://github.com/QwenLM/qwen-code/pull/6745) — *Open* — Companion to the multi-workspace RFC. Allows trusted workspaces to be removed at runtime without daemon restart.

4. **Fix: Prompt cache stabilization for deferred tools** [#6723](https://github.com/QwenLM/qwen-code/pull/6723) — *Open* — Instead of revealing deferred tool schemas into provider declarations, returns schemas as model-visible context. Preserves prompt cache prefixes. Addresses #6721.

### Web Shell & UX

5. **Feat: Workspace Goals page** [#6561](https://github.com/QwenLM/qwen-code/pull/6561) — *Open* — Adds a dedicated Goals page to Web Shell, and fixes `/goal` being silently lost after daemon resume. Significant for session persistence.

6. **Feat: Git branch display in composer toolbar** [#6725](https://github.com/QwenLM/qwen-code/pull/6725) — *Open* — Shows current git branch of the active workspace. Part of a larger toolbar redesign trend (#6699, #6702).

7. **Fix: Duplicate inline composer tag tooltips** [#6729](https://github.com/QwenLM/qwen-code/pull/6729) — *Closed* — Native `title` and custom React tooltips conflicted. Now uses `aria-describedby` association for custom tooltips.

### Core & Performance

8. **Feat: Add `/reload-env` command** [#6707](https://github.com/QwenLM/qwen-code/pull/6707) — *Open* — Hot-reload environment variables and API keys without restarting the session. Community request for seamless key rotation.

9. **Perf: Lazy-load web-tree-sitter runtime** [#6747](https://github.com/QwenLM/qwen-code/pull/6747) — *Open* — Changes static import to dynamic first-use import. Improves startup time for sessions that don't use code parsing.

10. **Fix: OAuth recovery after HTTP 401 for MCP servers** [#6732](https://github.com/QwenLM/qwen-code/pull/6732) — *Closed* — Restores OAuth flow for Streamable HTTP MCP servers. Uses bounded HEAD probe to detect 401 challenges, then runs interactive auth.

---

## Feature Request Trends

1. **Multi-workspace daemon architecture** — The dominant theme. RFC #6378, PRs #6745, #6740, and #6638 all tackle aspects of supporting multiple isolated workspaces under a single `qwen serve` process.

2. **Session persistence & crash recovery** — Multiple requests for automatic interrupted-turn continuation after daemon restart (#6695), a unified `SessionRecoveryService` (#6730), and durable chat recording (#6742).

3. **Web Shell toolbar enhancements** — A coordinated push to add workspace switcher, execution context, and git branch buttons (#6699, #6702, #6725). Inspired by Codex desktop client layouts.

4. **Inline commands & model switching** — `/model <id> <prompt>` for one-line model overrides (#5967), `/reload-env` for key hot-reload (#6707), and `Ctrl+S` to stash input (#6669). Community wants less friction in interactive use.

5. **Tool reliability improvements** — Fast-apply model for `edit_file` (#282), `zvec-grep` semantic search tool (#6096), and configurable shell command timeouts (#6628). Developers want fewer hallucinated edits.

---

## Developer Pain Points

1. **Memory and session state degradation** — Issues #6487, #6713, and #6721 all point to memory/index corruption over long sessions. The `/remember` command creates stale indices, microcompaction clears managed memory, and deferred tool discovery breaks prompt caching. This is the #1 pain point for production users.

2. **Token limit misconfigurations** — Claude Opus 4.6+ models (#6719, #6734) and Qwen 3.7 Max (#6666) have incorrect or inconsistent token limits. Developers report hitting API errors silently.

3. **ACP / IDE integration fragility** — JetBrains ACP not forwarding user prompts (#6581), OAuth not triggering on 401 (#6639), and broken clipboard on macOS standalone (#6590). The IDE plugin ecosystem feels less mature than the CLI.

4. **Tool output fidelity** — `read_file` rendering YAML/Markdown headers (#4077) causing `edit_file` to fail is an old issue (May 2025) still unresolved. The community is visibly annoyed: *“读出来的内容和磁盘上不一样——这属于工具的实现缺陷。”*

5. **Durability assumptions** — Chat recording reports success before JSONL writes are durable (#6742), and workspace registrations vanish after daemon restart (#6726). Several "success" signals are premature, eroding trust for automated workflows.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>

# DeepSeek TUI Community Digest — 2026-07-12

## 1. Today's Highlights

The project (now tracked under the broader **CodeWhale** repository) remains highly active with no new releases but a steady flow of issues and PRs. Key developments include a fix for the Anthropic API `tool_use`/`tool_result` mismatch error, a Korean locale PR nearing full coverage, and ongoing subagent performance investigations after high-worker cancellation. Six issues and four PRs were updated in the last 24 hours, reflecting continued momentum in TUI, subagent, and platform portability work.

## 2. Releases

No new releases in the last 24 hours.

## 3. Hot Issues (Top 10)

1. **#4329 — Anthropic API `tool_use`/`tool_result` error**  
   *Author: lixin34 | Updated: 2026-07-12 | Comments: 3*  
   A user reports HTTP 400 errors when `tool_use` IDs lack corresponding `tool_result` blocks. This indicates strict schema enforcement by Anthropic's API.  
   [🔗 Issue](https://github.com/Hmbown/CodeWhale/issues/4329)

2. **#4326 — RSS spike after cancelling 32-worker storm**  
   *Author: Hmbown | Updated: 2026-07-11 | Comments: 1*  
   High fan-out (32 workers) shows responsiveness, but RSS refuses to settle after cancellation. Performance-critical investigation to rule out memory leaks.  
   [🔗 Issue](https://github.com/Hmbown/CodeWhale/issues/4326)

3. **#4227 — CodeWhale tsunami onboarding workflow**  
   *Author: JayBeest | Updated: 2026-07-11 | Comments: 5*  
   Proposes a skill/workflow to auto-setup dev environments amid 10+ PRs/day velocity. Community interest in reducing contributor friction is evident.  
   [🔗 Issue](https://github.com/Hmbown/CodeWhale/issues/4227)

4. **#4345 — Key binding unfriendly for terminal**  
   *Author: hutong9 | Updated: 2026-07-11 | Comments: 2*  
   Non-ASCII keyboard input in TUI is disrupted; user requests terminal-native handling. A TUI accessibility pain point.  
   [🔗 Issue](https://github.com/Hmbown/CodeWhale/issues/4345)

5. **#4350 — Cargo build fails on Android/Termux (aarch64-linux-android)**  
   *Author: Michael2008S | Updated: 2026-07-11 | Comments: 1*  
   `rquickjs` lacks bindings for `aarch64-linux-android`. Blocking mobile development enthusiasts.  
   [🔗 Issue](https://github.com/Hmbown/CodeWhale/issues/4350)

6. *#4345 (listed above) also qualifies as top TUI input bug.*

7. **#4326 (reiteration)** — Core maintainer flagged; likely to drive worker lifecycle improvements.

8. **#4227 (reiteration)** — 5 comments indicate active community design input.

9. **#4329 (reiteration)** — Direct API integration breakage demands priority.

10. **#4350 (reiteration)** — Represents growing demand for mobile/alternative platform support.

## 4. Key PR Progress (Top 10)

1. **#4349 — NetBSD build support**  
   *Author: ci4ci4 | Updated: 2026-07-11*  
   Generates missing `rquickjs` bindings for NetBSD (also applicable to FreeBSD, OpenBSD, DragonFly). Expands platform reach.  
   [🔗 PR](https://github.com/Hmbown/CodeWhale/pull/4349)

2. **#4348 — Fix Anthropic cache-write token billing**  
   *Author: knqiufan | Updated: 2026-07-11*  
   Properly separates `cache_creation_input_tokens` into own variable, adds `cache_write_per_million` pricing, and wires 5-minute write rates to TUI.  
   [🔗 PR](https://github.com/Hmbown/CodeWhale/pull/4348)

3. **#4347 — Korean (ko) locale**  
   *Author: moduvoice | Updated: 2026-07-11*  
   Adds `ko.json` with all 752 leaf keys translated. Major i18n milestone for Korean-speaking users.  
   [🔗 PR](https://github.com/Hmbown/CodeWhale/pull/4347)

4. **#4346 — Fix tool input_schema for Anthropic (oneOf/anyOf/allOf)**  
   *Author: qinlinwang | Updated: 2026-07-11*  
   Sanitizes top-level JSON schema combinators to avoid Anthropic HTTP 400 rejections. Direct fix for Issue #4329.  
   [🔗 PR](https://github.com/Hmbown/CodeWhale/pull/4346)

5. **#4349 (reiteration)** — Critical for NetBSD/BSD ecosystem.

6. **#4348 (reiteration)** — TUI pricing accuracy is a user-facing quality metric.

7. **#4347 (reiteration)** — Signals growing non-English contributor base.

8. **#4346 (reiteration)** — PR directly linked to open bug; high urgency.

9. *(No additional top PRs beyond these 4 in last 24h)*

10. *(No additional top PRs beyond these 4 in last 24h)*

## 5. Feature Request Trends

- **CodeWhale dev environment automation** (Issue #4227): A workflow skill to auto-sync, build, and test for contributors is gaining traction, reflecting the project's high PR velocity.
- **i18n expansion**: The Korean locale PR (and implicit demand from non-English issues like #4345) points toward broader language support as a community priority.
- **Terminal-native key handling** (#4345): Users increasingly expect TUI to correctly handle non-ASCII and terminal-specific input without workarounds.

## 6. Developer Pain Points

- **Anthropic API strictness** (#4329, #4346): Schema enforcement around `tool_use`/`tool_result` ordering and `oneOf`/`anyOf`/`allOf` in tool definitions continues to cause 400 errors. Fixes are in progress but highlight fragility of provider adapter code.
- **Worker lifecycle and memory** (#4326): After high-concurrency (32-worker) cancellation, RSS does not settle. Community suspects allocator retention or genuine leak; maintainer is investigating.
- **Platform portability gaps** (#4350, #4349): `rquickjs` bindings are missing for Android (`aarch64-linux-android`) and BSDs, blocking contributors on non-Linux/non-macOS systems.
- **TUI input handling** (#4345): Non-ASCII keyboard input in the terminal is “unfriendly,” indicating a need for improved `crossterm` or `ratatui` interaction patterns.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*