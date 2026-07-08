# AI CLI Tools Community Digest 2026-07-08

> Generated: 2026-07-08 01:48 UTC | Tools covered: 9

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
**Date: 2026-07-08**

---

## 1. Ecosystem Overview

The AI CLI developer tools landscape is entering a **maturity phase marked by platform-specific regressions and cost transparency demands**. Claude Code and OpenAI Codex dominate community engagement, while Gemini CLI and Qwen Code push aggressive infrastructure automation and multi-workspace scalability respectively. OpenCode is navigating a complex V2 migration, and smaller tools (Pi, DeepSeek TUI/CodeWhale) focus on extension architecture and TUI stability. A shared pattern across all major tools is **growing developer frustration with undocumented cost changes, safety filter overreach, and Windows stability gaps**—suggesting the ecosystem is moving from "can it work?" to "can we trust it in production?"

---

## 2. Activity Comparison

| Tool | New Issues (24h) | Active PRs | Releases Today | Community Signal |
|------|-----------------|------------|----------------|------------------|
| **Claude Code** | 21 | 2 | v2.1.203–204 (2) | High—cost bugs dominate |
| **OpenAI Codex** | ~10 | 10 | rust-v0.143.0 | High—GPT-5.5 token bug trending |
| **Gemini CLI** | ~5 | 10 | v0.51.0-nightly | Moderate—agent reliability focus |
| **GitHub Copilot CLI** | ~8 | 0 | v1.0.69 (2 variants) | Low—no PRs, plugin stability issues |
| **Kimi Code** | 0 | 0 | None | Minimal—stable with one feature request |
| **OpenCode** | ~8 | 10 | v1.17.15 | Moderate—V2 migration active |
| **Pi** | ~10 | 10 | None | Low—quality-of-life fixes |
| **Qwen Code** | ~10 | 10 | v0.19.7 + nightly | Moderate—daemon optimization |
| **DeepSeek TUI (CodeWhale)** | ~8 | 10 | v0.8.67 | High—rebranding + stabilization |

---

## 3. Shared Feature Directions

### Cost Transparency & Token Budget Controls
- **Claude Code** (#41506, #38029, #28927, #33978): Max Plan token spikes, silent billing changes, demand for `claude usage` command
- **OpenAI Codex** (#28969): Request to disable auto-resolve timer; GPT-5.5 token clustering bug (#30364) highlights model cost opacity
- **Qwen Code** (#6264): `/review` skill consumes excessive tokens; users want configurable budgets
- **DeepSeek TUI/CodeWhale** (#528, #2956): Cache-maximal context management, repeated transcript payload reduction
- **OpenCode** (#30706): Cache-write pricing gaps and zero-cost report inaccuracies

### Cross-Platform Stability (Windows/Linux)
- **Claude Code**: WSL2 resume freeze (#75496), Windows terminal freeze (#75497), JetBrains path bugs
- **OpenAI Codex**: 13GB memory leaks from duplicate MCP pools (#31499), nonpaged pool leaks (#16786), sandbox permission bugs (#31511)
- **GitHub Copilot CLI**: NFS/Tokio race condition (#4053), Windows PowerShell hook breakage (#4001)
- **Qwen Code**: Shell tool fails on Windows cmd.exe (#6298), Windows-style artifact path validation (#6483)
- **DeepSeek TUI/CodeWhale**: Windows TUI freeze/crossterm deadlock (#1812), input leakage to PowerShell (#2261), IME deadlock (#1835)
- **Gemini CLI**: Browser agent fails on Wayland (#21983), terminal flicker on resize (#21924)

### Safety Filter & Permission Model Feedback
- **Claude Code**: 3 new cybersecurity false positives blocking reverse-engineering work (#75491, #75503, #75504)
- **OpenAI Codex**: Auto-resolve prematurely closes questions (#28969), memory writability confusion (#19195)
- **Gemini CLI**: Agent uses `git reset`/`--force` without prompting (#22672); community wants sandbox-level guardrails
- **GitHub Copilot CLI**: `preToolUse` hook forces confirmation even when `permissionDecision: allow` (#2643)

### Plugin/Extension Ecosystem Maturation
- **GitHub Copilot CLI**: `/plugins` dashboard shipped in v1.0.69, but duplicate MCP processes (#4049) and broken hooks persist
- **Pi**: Extension loading performance (#6360, #6400), prompt guideline API (#5711), session name events (#6175)
- **Claude Code**: Plugin MCP configuration scope clarification PR (#75252)
- **OpenCode**: V2 plugin discovery gaps (#33896)—skills registered via API not showing in `/skills`
- **Qwen Code**: `MessageDisplay` hook for mid-turn streaming (#6488); `PreToolUse` `ask` silently denied (#6321)

---

## 4. Differentiation Analysis

| Dimension | Claude Code | OpenAI Codex | Gemini CLI | GitHub Copilot | Qwen Code | OpenCode | Pi | CodeWhale |
|-----------|-------------|--------------|------------|----------------|-----------|----------|----|-----------|
| **Primary Focus** | Production coding, long sessions | Multi-agent workflows, IDE integration | Agent infrastructure, automated triage | Sandbox policy, plugin ecosystem | Daemon scalability, multi-workspace | V2 migration, plugin-first | Extension API, lightweight TUI | Autonomous workflows, Fleet routing |
| **Target User** | Professional devs on Max plan | End-to-end automation teams | Google Cloud ecosystem devs | GitHub-integrated teams | Qwen model ecosystem; enterprise | Multi-provider power users | Experimental/tinker devs | Autonomous agent enthusiasts |
| **Key Strength** | SOTA model, hook ecosystem | Telemetry, session lifecycle | Caretaker automation, eval infrastructure | GitHub integration | Multi-workspace daemon | Provider-agnostic V2 TUI | Extensible, reasoning model support | Autonomous workflow lanes |
| **Key Weakness** | Cost transparency, Windows | GPT-5.5 token bugs, Windows leaks | Subagent reliability | Plugin fragility, no PRs today | Token overhead, Windows | V2 parity gaps | Reasoning model fragility | Windows stability, rebranding friction |
| **Technical Approach** | Proprietary Opus model, max context | Rust rewrite, telemetry-first | Subagent delegation, eval-driven | Sandbox-first, MCP integration | C++/daemon, SDK-first | TypeScript, plugin SDK | TypeScript, extension API | Rust-based TUI, Fleet provider routing |

---

## 5. Community Momentum & Maturity

### High Momentum / Rapid Iteration
- **OpenAI Codex**: 10 active PRs, telemetry infrastructure PRs (#30667–#30675), session lifecycle overhaul—signs of a team scaling rapidly
- **DeepSeek TUI/CodeWhale**: Rebranding to CodeWhale with structured release trains (v0.8.68 execution board #4092), aggressive bugfix velocity (10 PRs)
- **Qwen Code**: Multi-workspace RFC (#6378, 19 comments), mid-turn streaming hooks, SDK control methods—expanding scope quickly

### Moderate / Stable Iteration
- **Gemini CLI**: Caretaker Agent infrastructure maturing (3 PRs), eval harness professionalizing (#28169, #28305), but subagent reliability issues persist
- **OpenCode**: V2 migration progressing steadily (TUI tracking issue #34359, durable AGENTS.md #34341), but Windows regressions (#35828) emerging
- **Pi**: Quality-of-life and extension API improvements (10 PRs), reasoning model fragility remains a systemic risk

### Low Momentum / Stability Concerns
- **Claude Code**: Despite 21 new issues, only 2 minor patches shipped; Windows regressions and 4+ month-old cost bugs (#41506) unresolved—community trust eroding
- **GitHub Copilot CLI**: Zero PRs in 24h, #53 (10-month-old feature request) still unaddressed, multiple plugin/sandbox regressions—stagnation risk
- **Kimi Code**: Zero issues, zero PRs, zero releases—either stable or dormant; monitoring required

---

## 6. Trend Signals

### Near-Term (Next 3–6 Months)
1. **Cost transparency will become a competitive differentiator.** Community backlash against silent billing changes (Claude Code #28927) and token clustering bugs (Codex #30364) suggests tools that ship first-party usage analytics will gain trust. Expect `claude usage`-style commands across the ecosystem.

2. **Safety filter calibration is overdue.** Three false positives in a single day on Claude Code signals over-tuned filters. This creates demand for per-domain safety toggles, appeal mechanisms, and open filter logs—features no major tool currently offers.

3. **Windows support is the new "table stakes."** Every tool except Kimi Code reports Windows-specific regressions. Teams that invest in Windows CI/CD and cross-platform testing (e.g., eliminating `cat` on cmd.exe) will capture the underserved Windows developer segment.

### Medium-Term (6–12 Months)
4. **Agent observability will become a core product category.** The GPT-5.5 reasoning-token clustering bug (#30364) and Gemini's false `GOAL` success (#22323) reveal a critical gap: users cannot inspect agent reasoning or reliably detect failures. Tools like CodeWhale (#4094 sub-agent detail panel) and Codex (telemetry PRs) are early movers.

5. **Multi-model provider routing is becoming standard.** CodeWhale (#2300), OpenCode (provider-agnostic), and Qwen Code (multi-workspace daemon) all support or are building model-agnostic architectures. Single-model lock-in (Claude Code's Opus dependence) may become a liability.

6. **Plugin/extension ecosystems will consolidate around MCP.** GitHub Copilot CLI's MCP integration, Pi's extension API, and OpenCode's plugin SDK all point toward MCP as the standardization layer. Tools that don't support MCP (Kimi Code) risk isolation.

### Long-Term (12+ Months)
7. **Autonomous workflows require self-healing agents.** CodeWhale's "Turn stalled — no completion signal" (#2487) and Gemini's generalist agent hang (#21409) show that current agents cannot recover from stalls. Expect investment in completion-signal timeouts, agent health checks, and automatic rollback.

8. **Developer trust is the scarcest resource.** Undocumented billing changes, safety false positives, and silent failures erode trust faster than features build it. Tools that prioritize transparency (open changelogs, cost dashboards, model behavior diffs) will win long-term adoption over those that optimize for short-term edge.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)

# Claude Code Skills Community Highlights Report
**Data as of 2026-07-08 | Source: github.com/anthropics/skills**

---

## 1. Top Skills Ranking

The following pull requests attracted the most community discussion and represent the most-watched Skill activity in the repository:

### #1298 — fix(skill-creator): `run_eval.py` always reports 0% recall
**Status:** Open | **Author:** MartinCajiao | **Created:** 2026-06-10  
**Link:** https://github.com/anthropics/skills/pull/1298

**Functionality:** Fixes the skill-creator's evaluation pipeline (`run_eval.py`, `run_loop.py`, `improve_description.py`) which reports `recall=0%` for every description due to a combination of missing eval artifact installation, Windows stream-reading bugs, incorrect trigger detection logic, and broken parallel workers. The description-optimization loop has been optimizing against noise.

**Discussion Highlights:** Addresses Issue #556 (12 comments, 7 upvotes) and multiple independent reproductions. The PR touches four distinct root causes, making it the most comprehensive fix for the skill-creator's broken evaluation loop. Blocked by two prior Windows fixes (#1050, #1099) that must land first.

---

### #514 — Add document-typography skill
**Status:** Open | **Author:** PGTBoos | **Created:** 2026-03-04  
**Link:** https://github.com/anthropics/skills/pull/514

**Functionality:** Provides typographic quality control for AI-generated documents, preventing orphan word wrap (1–6 words on a new line), widow paragraphs (headers stranded at page bottom), and numbering misalignment. Targets a universal pain point in Claude-generated documents.

**Discussion Highlights:** Strong community resonance — these issues affect every document Claude generates. The skill is narrow in scope but immediately useful across all document output. Community noted that typographic quality is rarely requested by users but consistently degrades output quality.

---

### #538 — fix(pdf): correct case-sensitive file references in SKILL.md
**Status:** Open | **Author:** Lubrsy706 | **Created:** 2026-03-06  
**Link:** https://github.com/anthropics/skills/pull/538

**Functionality:** Fixes 8 case-sensitivity mismatches in `skills/pdf/SKILL.md` where `REFERENCE.md` and `FORMS.md` were referenced in uppercase but actually stored as lowercase files. Breaks on case-sensitive filesystems (Linux/macOS default).

**Discussion Highlights:** Long review cycle (updated through April 29). A simple but critical fix for cross-platform compatibility. Generated discussion about establishing case-sensitivity conventions for all skills going forward.

---

### #486 — Add ODT skill — OpenDocument text creation and template filling
**Status:** Open | **Author:** GitHubNewbie0 | **Created:** 2026-03-01  
**Link:** https://github.com/anthropics/skills/pull/486

**Functionality:** Enables Claude to create, fill, read, and convert OpenDocument Format files (.odt, .ods). Covers LibreOffice document creation, template filling, ODT-to-HTML conversion, and ISO-standard office document generation.

**Discussion Highlights:** Addresses a clear gap in the document-format support. Community discussion centered on whether .ods spreadsheet support should be split into a separate skill. The PR triggers on any mention of ODT, ODS, ODF, or LibreOffice.

---

### #210 — Improve frontend-design skill clarity and actionability
**Status:** Open | **Author:** justinwetch | **Created:** 2026-01-05  
**Link:** https://github.com/anthropics/skills/pull/210

**Functionality:** Revises the frontend-design skill so every instruction is concretely actionable within a single conversation. Improves internal coherence and ensures guidance is specific enough to steer Claude's behavior without ambiguity.

**Discussion Highlights:** Long-running discussion about skill design philosophy — whether skills should be instructional (tell Claude what to do) or aspirational (describe desired outcomes). This PR represents the "instructional" camp and generated substantial debate about skill architecture best practices.

---

### #83 — Add skill-quality-analyzer and skill-security-analyzer to marketplace
**Status:** Open | **Author:** eovidiu | **Created:** 2025-11-06  
**Link:** https://github.com/anthropics/skills/pull/83

**Functionality:** Two meta-skills: `skill-quality-analyzer` evaluates Skills across five dimensions (Structure & Documentation at 20%, plus other criteria), and `skill-security-analyzer` audits Skills for security issues. Both are "meta-skills" designed to evaluate other Skills.

**Discussion Highlights:** The longest-open PR among top entries (since November 2025). Generated discussion about whether meta-skills belong in the main repository or in a separate marketplace tier. Raises governance questions about who validates the validators.

---

### #1367 — feat(skills): add self-audit — mechanical verification + four-dimension reasoning quality gate
**Status:** Open | **Author:** YuhaoLin2005 | **Created:** 2026-06-28  
**Link:** https://github.com/anthropics/skills/pull/1367

**Functionality:** A universal audit skill that verifies output before delivery — first checks that all claimed output files exist mechanically, then runs a four-dimension reasoning audit in damage-severity priority order. Works with any project or model.

**Discussion Highlights:** Very recent but already gathering attention. The "damage-severity priority" ordering is innovative — checks most critical failures first. Community interest in making this a required pre-delivery step for all agentic workflows.

---

## 2. Community Demand Trends

Analysis of the most-discussed Issues reveals five concentrated demand directions:

### 🔴 Security & Trust Boundaries (Issue #492 — 34 comments, highest engagement)
**Trend:** The community is deeply concerned about community skills distributed under the `anthropic/` namespace creating a trust boundary vulnerability. Users may grant elevated permissions to skills they believe are official.  
**Signal:** This is the single most-commented Issue in the repository. There is demand for namespace governance, permission scoping, and official vs. community skill labeling.  
**Link:** https://github.com/anthropics/skills/issues/492

### 🔴 Skill-Creator Reliability (Issue #556 — 12 comments, 7 upvotes)
**Trend:** The `run_eval.py` evaluation pipeline is fundamentally broken — it reports 0% recall on every query, making the description-optimization loop optimize against noise. Multiple contributors have submitted PRs (#1298, #1099, #1050, #1323) but none have merged.  
**Signal:** High demand for a working skill-development toolchain before the community can reliably contribute new skills.  
**Link:** https://github.com/anthropics/skills/issues/556

### 🟡 Organization-Wide Skill Sharing (Issue #228 — 14 comments, 7 upvotes)
**Trend:** Enterprise users want to share skills within organizations without manual file transfer. Currently requires downloading `.skill` files, sending via Slack, and manual upload.  
**Signal:** Demand for a shared skill library, direct sharing links, or org-level skill management in Claude.ai.  
**Link:** https://github.com/anthropics/skills/issues/228

### 🟡 Duplicate Skills from Plugin Overlap (Issue #189 — 6 comments, 9 upvotes)
**Trend:** Installing `document-skills` and `example-skills` plugins produces identical skills, wasting context window space.  
**Signal:** The community wants clear plugin boundaries and deduplication logic. Highest upvote-to-comment ratio in the top Issues.  
**Link:** https://github.com/anthropics/skills/issues/189

### 🟢 Windows Compatibility (Issue #1061 — 3 comments)
**Trend:** Multiple reports that skill-creator scripts fail on Windows due to Unix-first assumptions: missing `PATHEXT` handling, `cp1252` encoding issues, `select()` on pipes.  
**Signal:** Growing Windows developer base for Claude Code; compatibility fixes are becoming prerequisites for other improvements.  
**Link:** https://github.com/anthropics/skills/issues/1061

---

## 3. High-Potential Pending Skills

These open PRs have active discussion and are likely to land in the near future:

| PR | Skill | Author | Created | Status Signal |
|---|---|---|---|---|
| [#1302](https://github.com/anthropics/skills/pull/1302) | **color-expert** — Color naming systems (ISCC-NBS, Munsell, XKCD, RAL), color space selection tables (OKLCH, OKLAB, CAM16) | meodai | 2026-06-10 | Complete, well-scoped, single-responsibility skill |
| [#806](https://github.com/anthropics/skills/pull/806) | **sensory** — Native macOS automation via `osascript`/AppleScript instead of screenshot-based computer use | AdelElo13 | 2026-03-29 | Two-tier permission system; fills macOS automation gap |
| [#723](https://github.com/anthropics/skills/pull/723) | **testing-patterns** — Full testing stack: philosophy (Testing Trophy), unit testing (AAA), React component testing, E2E | 4444J99 | 2026-03-22 | Comprehensive; covers Testing Library, Cypress, Playwright |
| [#1367](https://github.com/anthropics/skills/pull/1367) | **self-audit** — Mechanical file verification + four-dimension reasoning quality gate | YuhaoLin2005 | 2026-06-28 | Universal; very recently opened but high innovation |
| [#181](https://github.com/anthropics/skills/pull/181) | **SAP-RPT-1-OSS predictor** — Tabular foundation model for SAP business data analytics | amitlals | 2025-12-28 | Niche but enterprise-relevant; Apache 2.0 model |

---

## 4. Skills Ecosystem Insight

**The community's most concentrated demand is for a *reliable skill-development toolchain* — the skill-creator pipeline remains broken across all platforms (0% recall bug, Windows incompatibility), creating a systemic bottleneck where every new Skill submission depends on first fixing the evaluation infrastructure, while the parallel security concern about namespace trust boundaries is the most-engaged governance conversation in the repository.**

---

# Claude Code Community Digest — 2026-07-08

## Today's Highlights

Anthropic shipped two minor patches (v2.1.203–204) addressing session-keepalive and headless hook streaming, but the community remains focused on long-running cost concerns and a fresh wave of Windows-specific regressions. Three cybersecurity safety-filter false positives were filed today blocking legitimate reverse-engineering work, adding to growing tension around Opus 4.8's safety layer. A total of 21 new issues were opened in the last 24 hours, with several zero-comment reports that merit attention.

## Releases

**[v2.1.204](https://github.com/anthropics/claude-code/releases/tag/v2.1.204)** — Bugfix: Fixed hook events not streaming during SessionStart hooks in headless sessions, preventing remote workers from being idle-reaped mid-hook.

**[v2.1.203](https://github.com/anthropics/claude-code/releases/tag/v2.1.203)** — UX enhancements: Added a warning when login is about to expire so re-authentication can happen before background sessions are interrupted; added a grey ⏸ badge to the footer when in manual permission mode; added session's additional working directories to the footer.

## Hot Issues

1. **[#41506](https://github.com/anthropics/claude-code/issues/41506) — Max Plan: 3–5x token usage increase (52 comments, 26 👍)**  
   Longest-running cost bug. Multiple users on the $100/month Max plan report silent token consumption spikes since late March. Community speculation points to a model-side change or a context window leak in resumed sessions. **Why it matters:** Directly impacts developer budgets with no opt-in.

2. **[#38029](https://github.com/anthropics/claude-code/issues/38029) — Abnormal consumption on session resume (23 comments, 33 👍)**  
   Mac users report that resuming sessions consumes significantly more tokens than fresh starts. Likely causal link with #41506. **Why it matters:** Session resume is a core workflow; inflated costs erode trust.

3. **[#75496](https://github.com/anthropics/claude-code/issues/75496) — `claude --resume` freezes on WSL2 (new, 2 comments)**  
   Cold-resume renders a screen that accepts no keyboard input. Reproduced under bash/fish and tmux. **Why it matters:** Blocking UX regression for WSL2 users, the primary Windows dev environment.

4. **[#73365](https://github.com/anthropics/claude-code/issues/73365) — Fable 5 advisor always "unavailable" on Windows (12 comments, 31 👍)**  
   v2.1.198 regression: Opus 4.8 (advisor) shows as unavailable across all sessions. High engagement suggests many depend on advisor features. **Why it matters:** Core model availability broken on a major platform.

5. **[#28927](https://github.com/anthropics/claude-code/issues/28927) — Silent billing change in v2.1.51 (16 comments, 19 👍)**  
   1M context moved to extra-usage-only without changelog entry. JSONL evidence shows identical workloads billed differently. **Why it matters:** Undocumented billing changes erode developer confidence in cost predictability.

6. **[#75491](https://github.com/anthropics/claude-code/issues/75491) — Safety block on drone app reverse-engineering (new, 1 comment)**  
   Legitimate analysis of cert/command timing halted by Opus 4.8 cyber safety filter. **Why it matters:** Third false positive today — pattern suggests over-tuned filters are blocking authorized security work.

7. **[#61021](https://github.com/anthropics/claude-code/issues/61021) — Text selection broken in VS Code terminal (10 comments, 7 👍)**  
   Recent change prevents Ctrl+C copy after text selection when Claude Code is running in VS Code terminal. **Why it matters:** Fundamental terminal interaction broken for VS Code users.

8. **[#42765](https://github.com/anthropics/claude-code/issues/42765) — OAuth redirect_uri uses localhost, violating RFC 8252 (6 comments, 17 👍)**  
   Using `localhost` instead of `127.0.0.1` breaks OAuth on certain Linux configurations. **Why it matters:** Protocol violation means some users can't authenticate at all.

9. **[#75497](https://github.com/anthropics/claude-code/issues/75497) — `claude --resume` causes complete terminal freeze on v2.1.204 Windows (new, 1 comment)**  
   Confirmed regression in today's release. Terminal unresponsive after resume. **Why it matters:** Shipping a regression that blocks resume is a serious quality miss.

10. **[#33978](https://github.com/anthropics/claude-code/issues/33978) — Built-in usage analytics command (18 comments, 10 👍)**  
    Proposal for `claude usage` to consolidate cost visibility. Consolidates 10+ related issues. **Why it matters:** Lack of basic usage tooling is driving sustained community frustration.

## Key PR Progress

1. **[#73476](https://github.com/anthropics/claude-code/pull/73476) — Fix GitHub capitalization in README**  
    Minor doc fix, but first external contribution workflow visible. Signals community engagement on documentation quality.

2. **[#75252](https://github.com/anthropics/claude-code/pull/75252) — Clarify plugin MCP configuration scope**  
    Clarifies that plugin `mcpServers` is separate from user-level allow/deny lists. Reopened after fork deletion. Important for plugin ecosystem clarity.

3. (Remaining 8 PRs not shown in data — likely zero activity beyond these two in the window)

## Feature Request Trends

Three persistent themes emerge from today's issue stream:

1. **Cost Transparency & Controls** — Issues #41506, #38029, #28927, #33978, and #75480 all demand better visibility into token consumption, billing changes, and usage analytics. The `claude usage` command proposal (#33978) has become the focal request, consolidating 10+ related issues. Community wants API-level cost tracking, not just UI badges.

2. **Safety Filter Calibration** — Three new issues today (#75491, #75503, #75504) document Opus 4.8 cybersecurity filters blocking authorized reverse-engineering work. Pattern suggests over-aggressive safety gating on the "cyber" domain. Developers want appeal mechanisms or per-domain safety toggles.

3. **Cross-Platform Stability** — Windows/WSL2 issues dominate today's new reports: resume freezes (#75496, #75497), JetBrains path serialization bugs (#75498), Dispatch pairing failures (#75499), and installation failures (#75485). The macOS vs. Windows quality gap is widening.

## Developer Pain Points

- **Cost unpredictability** remains the #1 pain point. Multiple open issues (some 4+ months old) with no resolution. The top two issues by engagement (#41506, #38029) are both cost-related, and fresh reports continue.
- **Windows/WSL2 quality regressions** are accelerating. Today alone: resume terminal freeze (v2.1.204 regression), WSL2 keyboard input freeze, JetBrains path handling bugs, and installation failures. Developers report being unable to use core workflows.
- **Undocumented changes** to billing (#28927) and model behavior erode trust. Community is actively maintaining JSONL diffs to prove changes.
- **Safety false positives** blocking legitimate work (cybersecurity analysis, reverse engineering) create workflow-halting friction with no clear recourse.
- **Terminal/UI corruption** issues (#68461, #75482) continue in iTerm2 and fullscreen mode, suggesting TUI renderer needs deeper work despite multiple patches.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

# OpenAI Codex Community Digest
**Date: 2026-07-08**

---

## Today's Highlights

The community is buzzing around a critical model-behavior bug in GPT-5.5 where reasoning-token clustering at specific boundaries (516/1034/1552) may degrade complex task performance. Meanwhile, the team shipped rust-v0.143.0 with remote plugins enabled by default and system proxy support for macOS/Windows, alongside a wave of infrastructure PRs focused on atomic teardown coordination and session lifecycle tracing. Windows stability remains a top concern, with multiple memory leak and crash reports.

---

## Releases

### [rust-v0.143.0](https://github.com/openai/codex/releases/tag/rust-v0.143.0)
- **Remote plugins** are now enabled by default, featuring richer catalog rows, npm marketplace sources, and visible remote/local version differentiation (#30297, #26705, #29375, #30981)
- **System proxy support**: Codex now routes authentication and Responses API traffic through macOS and Windows system proxies, including PAC file support
- Two alpha previews (0.143.0-alpha.38, 0.143.0-alpha.39) were also released

---

## Hot Issues

### 🔴 Critical Community Concern
1. **[#30364 – GPT-5.5 reasoning-token clustering at 516/1034/1552 degrading performance](https://github.com/openai/codex/issues/30364)**
   *156 comments, 251 👍*
   A deeply investigated bug report showing that `gpt-5.5` responses disproportionately land at fixed reasoning token boundaries, coinciding with lower reasoning quality. This has sparked intense community analysis—one of the most upvoted and commented issues this month.

### 🟠 High-Impact Bugs
2. **[#25792 – Context compaction forgets AGENTS rules, task progress jumps from 97% to 42%](https://github.com/openai/codex/issues/25792)**
   *13 comments*
   A long-task reliability nightmare: after automatic context compaction, critical AGENTS.md rules are dropped, causing tasks to regress dramatically. Serious concern for production workflows.

3. **[#28726 – Codex IDE extension freezes code-server sidebar on Chromium](https://github.com/openai/codex/issues/28726)**
   *14 comments*
   Linux remote development users hit a hard freeze when opening the Codex sidebar. Notably works on Android Samsung Internet but fails on desktop Chromium—suggests a rendering engine specific issue.

4. **[#23574 – VS Code extension allocates ~1M inotify watches on Linux large workspaces](https://github.com/openai/codex/issues/23574)**
   *9 comments, 9 👍*
   Monorepo users beware: the extension can exhaust system inotify watcher limits, potentially crashing the editor. A persistent issue for large-workspace Linux developers.

5. **[#31499 – Windows Desktop app-server spawns duplicate MCP stdio process pools (183 node.exe, 13GB memory)](https://github.com/openai/codex/issues/31499)**
   *3 comments*
   A severe resource leak on Windows: duplicate MCP processes spawn repeatedly and aren't cleaned up, consuming massive memory. Links to related issues #28361 and #30430.

### 🟡 Noteworthy Issues
6. **[#28969 – Request: setting to disable 60-second auto-resolve for questions](https://github.com/openai/codex/issues/28969)**
   *12 comments, 88 👍*
   Strong community demand for control over the automatic question resolution timer. Users want to prevent premature closure during complex troubleshooting.

7. **[#31511 – apply_patch and view_image fail with false "os error 206" on Windows](https://github.com/openai/codex/issues/31511)**
   *3 comments*
   A sandbox permissions bug where restricted Windows profiles trigger a misleading "filename too long" error on paths only 60–70 characters long.

8. **[#31506 – ChatGPT login token missing api.responses.write scope](https://github.com/openai/codex/issues/31506)**
   *2 comments (CLOSED)*
   Authentication scoping issue: ChatGPT Plus users logged in via CLI lack the `api.responses.write` scope, breaking core functionality. Closed quickly—likely patched.

9. **[#21753 – Full Claude Code Hook Parity (29+ hooks)](https://github.com/openai/codex/issues/21753)**
   *26 comments, 19 👍*
   Umbrella tracker for 29+ lifecycle hooks to match Claude Code's automation surface. High community interest for CI/CD and IDE automation workflows.

10. **[#19195 – Make Codex memory writability explicit when `memories = true`](https://github.com/openai/codex/issues/19195)**
    *12 comments*
    Confusing UX: despite enabling `memories`, model prompts still contain "Never update memories" instructions. Users need clear writability indicators for memory features.

---

## Key PR Progress

### 🏗 Infrastructure & Performance
1. **[#31283 – Support extension-owned turn items](https://github.com/openai/codex/pull/31283)**
   *Open*
   Adds `codex-extension-items` crate so extensions can own `TurnItem` schemas without Core awareness. Enables cleaner standalone image generation integration.

2. **[#31503 – Detect Codex installs managed by pnpm](https://github.com/openai/codex/pull/31503)**
   *Open (code-reviewed)*
   Fixes a bug where global pnpm installs were treated as npm, causing wrong commands in `codex doctor` and update flows. Small but important for package manager diversity.

3. **[#30887 – Speed up reverse history search](https://github.com/openai/codex/pull/30887)**
   *Open*
   Major UX improvement: previously fetched one entry at a time (reopening/locking `history.jsonl` each time). Now batches fetches, dramatically reducing latency for scrolling through history.

4. **[#30670 – Avoid duplicate first-turn filesystem discovery](https://github.com/openai/codex/pull/30670)**
   *Open*
   First-turn startup was walking the filesystem twice (once for AGENTS.md, once for skills warmup). This PR eliminates redundant scanning, improving cold-start response time.

### 🔄 Session Lifecycle & Reliability
5. **[#31473 – Emit canonical review mode items](https://github.com/openai/codex/pull/31473)**
   *Open*
   Moves review-mode markers (entered/exited) onto canonical `TurnItem` lifecycle, enabling better tracking and event-driven workflows around code review sessions.

6. **[#31400 – Claim thread teardown groups atomically](https://github.com/openai/codex/pull/31400)** *(CLOSED)* + **[#31395](https://github.com/openai/codex/pull/31395)** *(CLOSED)* + **[#31388](https://github.com/openai/codex/pull/31388)** *(CLOSED)* + **[#31392](https://github.com/openai/codex/pull/31392)** *(CLOSED)* + **[#31399](https://github.com/openai/codex/pull/31399)** *(CLOSED)*
   A coordinated batch of 5 PRs from the same author (winston-openai) overhauling idle thread teardown, resume atomicity, teardown admission serialization, and group teardown claiming. These together prevent race conditions during session lifecycle transitions.

### 📊 Telemetry & Observability
7. **[#30667 – Correlate WebSocket stage timing](https://github.com/openai/codex/pull/30667)** *(CLOSED)*
   Adds client-side timestamps and parses server timing sidebands (pre-inference, routing, queue, TTFT, sampling) for Responses API WebSocket requests.

8. **[#30672 – Trace session startup stages](https://github.com/openai/codex/pull/30672)** *(CLOSED)*
   Breaks Core initialization into attributable stages: rollout setup, git probing, AGENTS refresh, skills warmup, etc. Critical for diagnosing slow session starts.

9. **[#30673 – Trace tool dispatch stages](https://github.com/openai/codex/pull/30673)** *(CLOSED)*
   Adds observability to tool dispatch: parallel-execution locks, lifecycle hooks, handler invocation, policy checks, and approval work.

10. **[#30675 – Trace RPC transport in exec-server](https://github.com/openai/codex/pull/30675)** *(CLOSED)*
    Propagates W3C trace context through exec-server RPC without changing wire format. Measures queue residence, serialization, write, decode, response dispatch.

---

## Feature Request Trends

1. **Claude Code Feature Parity** – The most persistent demand. Issues like #21753 (29+ hooks) and #12115 (nested AGENTS.md) show the community wants Codex to match or exceed Claude Code's automation and context management capabilities.

2. **Memory & Context Transparency** – Users want explicit control over memory writability (#19195), reliable AGENTS.md preservation during compaction (#25792), and nested AGENTS.md support (#12115). Memory/context behavior needs to be predictable.

3. **Remote & Cross-Platform Connectivity** – Strong demand for better SSH key authentication (#22857), working remote notifications (#20930), stable mobile-to-desktop connections (#25595), and consistent system proxy support (addressed in v0.143.0).

4. **Performance Observability** – The telemetry PRs (#30667–#30675) and the reverse history search PR (#30887) reflect community demand for understanding and optimizing Codex's internal operations.

---

## Developer Pain Points

1. **Windows Stability Crisis** – Multiple reports of exploding memory (13GB+ from duplicate MCP pools #31499, nonpaged pool leaks #16786), update failures that don't restart (#29787), disappearing conversations (#25397, #29868), and sandbox permission bugs (#31511, #31510). Windows users face the highest friction.

2. **Session & Context Unreliability** – The compaction bug (#25792) where task progress resets from 97% to 42% is a trust-eroding issue. Ghost conversations (#29868) and disappearing sessions (#24077, #25397) compound the frustration.

3. **IDE Extension Fragility** – Codex VS Code extension crashes on startup (#30360), freezes code-server (#28726), and exhausts system resources (#23574). The extension experience lags behind the CLI and Desktop app.

4. **Model Behavior Opacity** – The GPT-5.5 token clustering bug (#30364) highlights a lack of visibility into model reasoning internals. Combined with the auto-resolve timer (#28969) that closes questions prematurely, developers feel they lack control over how Codex handles their tasks.

5. **Authentication Scoping** – The login token missing `api.responses.write` scope (#31506, quickly closed) and insufficient Trusted Access verification feedback (#31505) create friction during setup and secure workflows.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>

# Gemini CLI Community Digest — 2026-07-08

## Today's Highlights

The team landed two major Caretaker Agent infrastructure PRs, bringing automated LLM triage and egress action handling closer to production. Meanwhile, a critical bug remains open where subagent recovery after hitting `MAX_TURNS` is falsely reported as goal success, and the generalist agent hang issue continues to attract community attention with 8 upvotes. Nightly build v0.51.0 includes sandbox and escape sequence fixes.

## Releases

**[v0.51.0-nightly.20260707.g15a9429b6](https://github.com/google-gemini/gemini-cli/releases/tag/v0.51.0-nightly.20260707.g15a9429b6)** — Two fixes:
- **fix(sandbox):** `~/.gitconfig` is now read-only in the macOS sandbox, preventing unwanted configuration writes from subagent processes.
- **fix(core):** Escape sequences within string literals are now preserved for modern models, resolving a class of string corruption bugs in agent tool calls.

## Hot Issues

1. **[#22323 — Subagent recovery after MAX_TURNS reported as GOAL success](https://github.com/google-gemini/gemini-cli/issues/22323)** — P1 bug where `codebase_investigator` hits its turn limit but reports `status: "success"` with `Termination Reason: "GOAL"`. This masks genuine failures and undermines trust in agent self-reporting. 10 comments, 2 👍.

2. **[#21409 — Generalist agent hangs](https://github.com/google-gemini/gemini-cli/issues/21409)** — P1, highest community engagement (8 👍). The CLI hangs indefinitely when delegating to the generalist agent for simple tasks like folder creation. Users confirm that disabling subagent delegation resolves the issue.

3. **[#24353 — Robust component level evaluations](https://github.com/google-gemini/gemini-cli/issues/24353)** — Epic tracking the maturation of behavioral eval infrastructure beyond the initial 76 tests across 6 models. Drives confidence in agent changes. 7 comments.

4. **[#22745 — Assess AST-aware file reads, search, and mapping](https://github.com/google-gemini/gemini-cli/issues/22745)** — Epic investigating whether AST-aware tools can reduce turns by precisely reading method bounds, reducing token noise. Could significantly improve codebase investigator accuracy. 7 comments.

5. **[#25166 — Shell command stalls with "Waiting input" after completion](https://github.com/google-gemini/gemini-cli/issues/25166)** — P1, effort/medium. Shell commands finish execution but the agent remains stuck on "Awaiting user input." Affects simple commands that never prompt for input. 3 👍.

6. **[#21983 — Browser subagent fails on Wayland](https://github.com/google-gemini/gemini-cli/issues/21983)** — P1. Browser agent terminates with `GOAL` immediately on Wayland displays, making it unusable on many Linux desktop environments.

7. **[#21968 — Gemini does not use skills and sub-agents enough](https://github.com/google-gemini/gemini-cli/issues/21968)** — Users report the model rarely invokes custom skills and sub-agents autonomously, even when highly relevant. Requires explicit instruction to use them. 6 comments.

8. **[#26522 — Auto Memory retries low-signal sessions indefinitely](https://github.com/google-gemini/gemini-cli/issues/26522)** — The memory extraction agent only marks sessions as processed after a successful `read_file`. Low-signal sessions are re-surfaced infinitely, causing wasted LLM calls.

9. **[#22672 — Agent should stop destructive behavior](https://github.com/google-gemini/gemini-cli/issues/22672)** — The model occasionally uses `git reset`, `--force` flags, or destructive DB commands when safer alternatives exist. Community calls for sandbox-level guardrails.

10. **[#20079 — Symlinked agent files not recognized](https://github.com/google-gemini/gemini-cli/issues/20079)** — `~/.gemini/agents/filename.md` symlinks are silently ignored. Blocks users who manage agents via dotfile repos or symlink farms.

## Key PR Progress

1. **[#28307 — LLM triage orchestrator & GCS debug logger (CLOSED)](https://github.com/google-gemini/gemini-cli/pull/28307)** — Implements `triage_orchestrator.py` using Antigravity SDK, structured GCS logging, and Docker build config for the Caretaker cloud job. Includes end-to-end integration test.

2. **[#28303 — Octokit GitHub action handler for egress service (CLOSED)](https://github.com/google-gemini/gemini-cli/pull/28303)** — Enables automated issue commenting and label assignment from the Caretaker agent via GitHub App auth. Part 2 of the Egress Service rollout.

3. **[#28306 — Main worker execution loop & egress publisher (OPEN)](https://github.com/google-gemini/gemini-cli/pull/28306)** — Implements the Cloud Run Job main loop and Pub/Sub egress publisher. The `triage_orchestrator` is stubbed and will be filled by #28307.

4. **[#28305 — Tool call formatter & failure summaries for evals (OPEN)](https://github.com/google-gemini/gemini-cli/pull/28305)** — When behavioral evals fail, the runner now prints a compact, numbered timeline of tool calls with status and error details. Dramatically improves debugability of eval failures.

5. **[#28169 — Eval coverage report command (OPEN)](https://github.com/google-gemini/gemini-cli/pull/28169)** — Adds `npm run eval:coverage` to cross-reference eval inventory with the tool registry. Helps identify untested tools.

6. **[#27971 — Fix thought leakage from scrubbed history (CLOSED)](https://github.com/google-gemini/gemini-cli/pull/27971)** — Surgical fix strips model internal monologue/reasoning thoughts from history turns. Prevents the model from emulating scratchpad patterns and entering infinite loops.

7. **[#28304 — Clearer privacy message for non-Code Assist accounts (OPEN)](https://github.com/google-gemini/gemini-cli/pull/28304)** — Replaces raw backend errors with a human-readable explanation when `/privacy` is used on Workspace/enterprise accounts without Code Assist tier.

8. **[#28089 — MCP elicitation (form + url) capability (CLOSED)](https://github.com/google-gemini/gemini-cli/pull/28089)** — Implements MCP protocol form and URL elicitation modes per the 2025-11-25 spec. Client now advertises elicitation support and handles form-based tool prompts.

9. **[#28096 — Drop late tool calls after SIGINT cancellation (CLOSED)](https://github.com/google-gemini/gemini-cli/pull/28096)** — Fixes #28091: a SIGINT during a turn could still execute delayed tool-call chunks. Now cancels remaining tool calls and prevents side-effects post-cancellation.

10. **[#28244 — Safe test command in policy-engine docs (OPEN)](https://github.com/google-gemini/gemini-cli/pull/28244)** — Replaces the `rm -rf /` example in policy engine quick-start with `curl http://localhost:3000` to avoid accidental damage during documentation testing.

## Feature Request Trends

- **Automated triage & caretaker infrastructure:** Multiple PRs and issues (#24353, the `caretaker-triage` stack) point toward a systematic push for LLM-driven issue triage, automated eval runs, and bot-mediated workflow management.
- **AST-aware codebase tooling:** Two active epics (#22745, #22746) explore AST-level file reading, search, and codebase mapping to reduce turn count and token waste in agent operations.
- **Subagent trajectory visibility:** Requests (#22598) to expose subagent reasoning in `/chat share` outputs for better debugging and eval review.
- **MCP & protocol expansion:** Multiple MCP-related PRs (#28089, elicitation support; #27200, retry logic) suggest ongoing investment in the MCP integration surface.
- **Evaluation infrastructure maturation:** PRs for eval coverage reports (#28169) and failure summaries (#28305) indicate the team is professionalizing their eval harness.

## Developer Pain Points

- **False success reporting:** Agents hitting `MAX_TURNS` and reporting `GOAL` success (#22323) is the most dangerous pattern — it hides real failures from users and automated systems.
- **Agent hangs and stuck processes:** The generalist agent hang (#21409) and shell command "Waiting input" stall (#25166) are top-voted P1 bugs, severely disrupting automation workflows.
- **Subagent autonomy problems:** Users report agents both under-using skills (#21968) and running subagents despite disabled settings (#22093), indicating poor configuration respect.
- **Low-signal memory retries:** Auto Memory's indefinite retrying of unreadable sessions (#26522) wastes both tokens and time, with no quarantine mechanism for invalid patches (#26523).
- **Destructive command risk:** The model's tendency to use `git reset`, `--force`, and destructive DB commands (#22672) without prompting is a recurring concern, especially for production-adjacent workflows.
- **Linux desktop gaps:** The browser agent failing on Wayland (#21983) and terminal flicker on resize (#21924) degrade the experience for a significant subset of Linux users.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

**GitHub Copilot CLI Community Digest**
**Date: 2026-07-08**

---

## 1. Today's Highlights

The CLI team shipped **v1.0.69** with smarter sandbox policy badge labeling and a new `/plugins` dashboard, but the community remains in limbo on the long-standing issue #53 requesting restoration of “GitHub Copilot” CLI commands — still unresolved after 10 months with no official response. A surge of triage-level bugs emerged overnight, including critical crashes on NFS filesystems, broken `/resume` for non-git sessions, and plugin installation failures on Windows, signaling a period of instability across sandboxing, plugins, and MCP integrations.

---

## 2. Releases

**v1.0.69** (2026-07-07)
- Labeled built-in file edits with a *(sandbox policy)* badge instead of *(sandboxed)*, clarifying they follow sandbox policy best-effort (not OS-level sandbox).
- Reloaded installed plugin extensions without requiring a session restart.
- Added a `/plugins` dashboard for centralized plugin management.

**v1.0.69-3** (prerelease)
- Allowed built-in file edits to bypass the sandbox when explicitly approved by the user.
- `web_fetch` now respects the active sandbox network policy; hosts can opt-in via `sandbox.allowBypass` to approve one-time fetch bypasses.

*No new releases in the last 24 hours beyond these two.*

---

## 3. Hot Issues (10 Noteworthy)

1. **[#53 – Bring back GitHub Copilot in the CLI commands](https://github.com/github/copilot-cli/issues/53)**  
   *Status:* OPEN | 👍 75 | Comments: 37 | Created: Sep 2025  
   The most upvoted issue. After 10 months without official response, the community has begun creating fork-based alternatives (e.g., `shell-ai`). This remains a top concern for workflow continuity.

2. **[#2643 – preToolUse hook confirmation dialog appears even with permissionDecision: allow](https://github.com/github/copilot-cli/issues/2643)**  
   *Status:* OPEN | 👍 2 | Comments: 12  
   Plugin devs cannot silently rewrite commands — the CLI forces an interactive confirmation every time, blocking automation use cases.

3. **[#3123 – /research can't write research report](https://github.com/github/copilot-cli/issues/3123)**  
   *Status:* OPEN | 👍 5 | Comments: 5  
   The `/research` agent fails to save markdown reports because the “create” tool is unavailable. Fundamental workflow gap for research-oriented users.

4. **[#4001 – Windows hooks executed via PowerShell, not bash; $CLAUDE_PROJECT_DIR unset](https://github.com/github/copilot-cli/issues/4001)**  
   *Status:* OPEN | 👍 0 | Comments: 3  
   Cli enforces `.claude/settings.json` hooks but fails to execute them correctly on Windows, breaking all repo-level settings for Windows users.

5. **[#4053 – TUI hangs on NFS/GPFS due to SIGCHLD race](https://github.com/github/copilot-cli/issues/4053)**  
   *Status:* OPEN | 👍 0 | Comments: 1  
   Critical startup hang when home directory is on network filesystems. Root cause: `which gh` subprocess spawned with 30+ concurrent threads collides on SIGCHLD.

6. **[#4054 – /resume broken for all non-git sessions](https://github.com/github/copilot-cli/issues/4054)**  
   *Status:* OPEN | 👍 0 | Comments: 1  
   Sessions created outside git repos store `repository = '/'`, making them unselectable via the resume picker — a catch-22.

7. **[#4038 – Non-interactive mode: late-connecting MCP server injects empty user message](https://github.com/github/copilot-cli/issues/4038)**  
   *Status:* OPEN | 👍 0 | Comments: 1  
   MCP servers with 7+ tools cause the CLI to append an empty user message, making the model echo system prompts instead of answering queries.

8. **[#3440 – session.disconnect() does not kill stdio MCP server processes](https://github.com/github/copilot-cli/issues/3440)**  
   *Status:* CLOSED | 👍 0 | Comments: 2  
   Child processes spawned for stdio MCP servers survive `session.disconnect()`, only dying on `CopilotClient.stop()`. Memory leak risk in long-running sessions.

9. **[#4049 – Docker stdio MCP servers duplicated on /new and /resume](https://github.com/github/copilot-cli/issues/4049)**  
   *Status:* OPEN | 👍 0 | Comments: 0  
   Running `/new` or resuming sessions spawns duplicate Docker MCP clients without cleanup. Duplicates accumulate across the entire CLI process lifetime.

10. **[#4041 – web_fetch fails on all URLs in IPv4-only sandbox environments](https://github.com/github/copilot-cli/issues/4041)**  
    *Status:* OPEN | 👍 0 | Comments: 0  
    The `web_fetch` tool errors with “TypeError: fetch failed” on every URL in IPv4-only environments, blocking users behind pure IPv4 networks.

---

## 4. Key PR Progress

*No pull requests were updated in the last 24 hours.*

---

## 5. Feature Request Trends

- **Plugin & Extension Ecosystem** (7+ issues): Community wants interactive input variables (`${input:...}`), project-scoped canvas routing, and reliable hook execution. The `/plugins` dashboard in v1.0.69 is a step forward.
- **Custom Model / BYOK Integration** (2 issues): Users demand the ability to use their own LLMs (DeepSeek, BYOK) in ACP server mode — the hardcoded `gpt-5.4-mini` in the `explore` tool (#3954) is a recurring blocker.
- **Sandbox Control & Transparency** (3 issues): Requests for configurable sandbox bypass, permissive network policies, and clear documentation for Windows sandbox requirements.
- **Session Management** (2 issues): Need for branch name control in `create_project`/`create_session` and better handling of non-git sessions.

---

## 6. Developer Pain Points

- **Unstable Plugin/Sandbox Interactions**: Multiple reports of plugin syncing failures (#4039), duplicated MCP processes (#4049), and broken sandbox policies on Windows (#4001, #4046) are eroding confidence in the plugin infrastructure.
- **Platform-Specific Regressions**: NFS/Tokio race condition (#4053), Windows PowerShell hook breakage (#4001), and IPv4-only network failures (#4041) suggest insufficient cross-platform testing.
- **Agent Reliability Issues**: The `/research` tool cannot save files (#3123), custom agents revert to defaults mid-session (#4047), and `/delegate` ignores branch instructions (#2729) — core agent functionality remains fragile.
- **UI/UX Friction**: Random text injection in input fields (#4051), model picker overlay obscuring prompts (#4043), and unattached desktop notifications (#4036) degrade daily developer experience.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

**Kimi Code CLI Community Digest**
**Date:** 2026-07-08

---

### 1. Today's Highlights
No new releases or merged pull requests occurred in the last 24 hours. The community's focus remains on a long-standing feature request for Figma MCP support (opened March 2026), which has seen recent activity and continued support from developers. The project appears to be in a stable phase with no critical bugs or breaking changes reported today.

---

### 2. Releases
**None** – No new versions were published in the last 24 hours.

---

### 3. Hot Issues
*Notable issues from the backlog, selected for relevance and community engagement.*

1. **#1604 – [Enhancement] Figma MCP Support**  
   *Author: maoxian-1*  
   *Updated: 2026-07-07* | *👍: 2*  
   **Why it matters:** This request aims to integrate with Figma’s MCP (Machine Common Protocol) catalog, which requires pre-registration. Developers want seamless design-to-code workflows directly from the CLI. Community interest suggests this is a high-value integration for frontend/AI-assisted design teams.  
   [GitHub Link](https://github.com/MoonshotAI/kimi-cli/issues/1604)

*(Note: Only one issue was updated in the last 24h. To meet the 10-item quota, I would typically scan the broader open issues list. Since no other issues were updated today, I highlight this single issue and note that the rest of the backlog shows no new activity.)*

---

### 4. Key PR Progress
**None** – No pull requests were updated in the last 24 hours.

---

### 5. Feature Request Trends
- **Design Tool Integration (Figma MCP):** The most vocal request is for native support of Figma’s MCP protocol. Developers want bidirectional data exchange (design components ↔ code) without manual pre-registration hurdles.
- **No other major feature trends** emerged in the last 24 hours. The backlog is quiet, indicating stable core functionality with focused demand on a single integration.

---

### 6. Developer Pain Points
- **External Service Pre-registration Friction:** The Figma MCP request (#1604) highlights frustration with external dependencies that require pre-registration (e.g., API keys, service authorizations). Developers expect the CLI to abstract these steps or provide guided onboarding.
- **Low Issue Activity (24h):** While not a pain point per se, the lack of new bug reports or support queries suggests either high stability or low engagement—both worth monitoring for community health.

---

*All links are to the [MoonshotAI/kimi-cli](https://github.com/MoonshotAI/kimi-cli) repository.*

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

# OpenCode Community Digest — 2026-07-08

## Today's Highlights

The team shipped **v1.17.15** with two core bugfixes, including better Z.ai context-window overflow classification and graceful config-directory handling. V2 migration continues to dominate the issue tracker, with the **TUI migration to `@opencode-ai/client`** and **durable AGENTS.md routing** making progress. A recurring theme of **Mac terminal rendering issues** has seen significant community traction, with multiple long-standing thread closures today.

---

## Releases

### v1.17.15
| Component | Change |
|---|---|
| **Core** | Better classification of Z.ai context-window overflow errors so oversized requests surface the right failure mode (`@fengjikui`) |
| **Core** | Handle unavailable config directories more gracefully when reading config files |
| **Desktop** | Restore model details tooltips in the model picker |

[View Release](https://github.com/anomalyco/opencode/releases/tag/v1.17.15)

---

## Hot Issues (Top 10)

### 1. [#6823 — CLI colors have low contrast on macOS Terminal (black / Pro theme)](https://github.com/anomalyco/opencode/issues/6823)
**Status:** CLOSED (updated today) | **Comments:** 16 | **Reactions:** 👍17  
**Why it matters:** This long-standing theme rendering issue (7 months open) has been resolved. The high upvote count (most-reacted issue today) shows this affected many macOS users. The fix likely addresses the root cause shared by several duplicate reports (#4461, #10054, #4721, #6923).

### 2. [#4461 — Input text is black on black](https://github.com/anomalyco/opencode/issues/4461)
**Status:** CLOSED (updated today) | **Comments:** 13 | **Reactions:** 👍6  
**Why it matters:** Another macOS Terminal.app rendering bug resolved today, closely related to #6823. The screenshot showed `/models` command input invisible against the Pro theme background—a critical usability blocker for TUI users.

### 3. [#34359 — Track TUI migration to `@opencode-ai/client`](https://github.com/anomalyco/opencode/issues/34359)
**Status:** OPEN | **Comments:** 9 | **Reactions:** 0  
**Why it matters:** This V2 umbrella issue tracks moving the entire TUI from the legacy SDK to the new generated Promise client. It's the foundational work enabling most other V2 TUI features. Still 9 comments deep with active architecture discussion.

### 4. [#35556 — V2: first Location can expose an empty plugin generation](https://github.com/anomalyco/opencode/issues/35556)
**Status:** OPEN | **Comments:** 8 | **Reactions:** 0  
**Why it matters:** A subtle race condition where `PluginSupervisor` exposes its service before initial reload completes. This affects the reliability of first-time session initialization in V2, a critical onboarding touchpoint.

### 5. [#34341 — V2: route progressive AGENTS.md through durable Instructions](https://github.com/anomalyco/opencode/issues/34341)
**Status:** OPEN | **Comments:** 7 | **Reactions:** 0  
**Why it matters:** Defines the V2 semantics for path-scoped `AGENTS.md` instructions. Current approach injects discovered files as synthetic user messages, which makes them non-durable (lost on compaction). The proposed fix would make them persistent instruction state.

### 6. [#10054 — Mac terminal (zsh) can't see any text](https://github.com/anomalyco/opencode/issues/10054)
**Status:** CLOSED (updated today) | **Comments:** 6 | **Reactions:** 👍1  
**Why it matters:** Another macOS Terminal rendering issue resolved, reinforcing that today's closure cluster addresses a systematic color theme problem.

### 7. [#34497 — Support file attachments in V2 prompts](https://github.com/anomalyco/opencode/issues/34497)
**Status:** OPEN | **Comments:** 4 | **Reactions:** 0  
**Why it matters:** File attachments don't currently work in V2 prompts, breaking a key V1 workflow. Community agent-bot filed this with clear reproduction—blocking migration for users who rely on context-rich attachments.

### 8. [#34835 — V2: improve UX for provider content-filter finishes](https://github.com/anomalyco/opencode/issues/34835)
**Status:** OPEN | **Comments:** 3 | **Reactions:** 0  
**Why it matters:** Provider content filters (e.g., Anthropic's safety filters) currently render as an awkward "finished" state. The product shape needs design input to handle blocked output gracefully across clients.

### 9. [#34766 — V2 TUI: follow-up prompts should render optimistically](https://github.com/anomalyco/opencode/issues/34766)
**Status:** CLOSED (updated today) | **Comments:** 3 | **Reactions:** 0  
**Why it matters:** Queued prompts now show pending state in V2 TUI, matching V1 behavior. Gone from "invisible queue" to visible user feedback.

### 10. [#35828 — Windows TUI fails when project `.opencode` already exists](https://github.com/anomalyco/opencode/issues/35828)
**Status:** OPEN | **Comments:** 1 | **Reactions:** 0  
**Why it matters:** Fresh critical bug in v1.17.15: `Config.loadInstanceState` fails trying to re-create an existing `.opencode` directory on Windows. New today—expect hotfix attention.

---

## Key PR Progress (Top 10)

### 1. [#35829 — feat(app): add inline file browser tabs](https://github.com/anomalyco/opencode/pull/35829)
**Author:** Hona | **Status:** OPEN  
**Summary:** Adds inline Open File tab, project tree, and TanStack-backed file search to the V2 review pane. Integrates preview and pinned file tabs with existing session layout.

### 2. [#35820 — fix(core): resume sessions after restart](https://github.com/anomalyco/opencode/pull/35820)
**Author:** kitlangton | **Status:** CLOSED  
**Summary:** Durably records session execution lifecycle outcomes. Recovers sessions interrupted by server shutdown using existing cross-process lock and stale-tool reconciliation. Closes #35646.

### 3. [#35826 — fix(cli): elect one managed daemon](https://github.com/anomalyco/opencode/pull/35826)
**Author:** kitlangton | **Status:** OPEN  
**Summary:** Acquires a process-lifetime lock before service route construction, preventing concurrent daemon instances on the same channel. Prerequisite for session recovery (#35646).

### 4. [#35497 — feat(core): make path-local instruction discovery durable](https://github.com/anomalyco/opencode/pull/35497)
**Author:** kitlangton | **Status:** OPEN  
**Summary:** Replaces synthetic message injection for discovered `AGENTS.md` files with durable schema/event system. Stacked on #35583 rename. Prevents instruction loss during compaction.

### 5. [#35188 — feat(core): implement models fallback](https://github.com/anomalyco/opencode/pull/35188)
**Author:** ReStranger | **Status:** OPEN  
**Summary:** Adds fallback model configuration for agents—if primary model fails, gracefully degrades to specified fallback. Community contributor PR.

### 6. [#35818 — fix(core): skip non-vcs location watcher](https://github.com/anomalyco/opencode/pull/35818)
**Author:** opencode-agent[bot] | **Status:** OPEN  
**Summary:** Skips `LocationWatcher` entirely for non-VCS locations, preventing unnecessary watcher registration. Replaces non-Git watcher expectation with regression test. Closes #35813.

### 7. [#35817 — fix(core): preserve provider metadata namespaces](https://github.com/anomalyco/opencode/pull/35817)
**Author:** opencode-agent[bot] | **Status:** OPEN  
**Summary:** Preserves complete provider metadata across start/delta/end events by namespace. Merges reasoning metadata through native and AI SDK routes. Retains flattened session compatibility.

### 8. [#35796 — fix(tui): clear stale tool preparation state](https://github.com/anomalyco/opencode/pull/35796)
**Author:** opencode-agent[bot] | **Status:** OPEN  
**Summary:** Fixes race where fetched message snapshots were overwritten by stale live `pending` tool state. Prefers server projection when refresh observes completed assistant message.

### 9. [#34634 — feat(core): resolve v2 prompt attachments](https://github.com/anomalyco/opencode/pull/34634)
**Author:** opencode-agent[bot] | **Status:** CLOSED  
**Summary:** Resolves file/directory attachments before durable admission. Inlines text into prompt text, converts local image/PDF URLs to data URLs for stable replay. Closes #34497.

### 10. [#35755 — fix(core): wait for plugin readiness](https://github.com/anomalyco/opencode/pull/35755)
**Author:** kitlangton | **Status:** OPEN  
**Summary:** Pending Config and SDK plugin updates now drain before session execution reads plugin state. Each model step pinned to one coherent plugin generation. Fails closed with typed `Session.AgentNotFoundError`.

---

## Feature Request Trends

1. **V2 TUI Parity (highest priority):** The dominant trend is bringing V2 TUI to functional parity with V1. Specific asks include: queued prompt visibility, `/move` command support, @-tagged file resolution, file attachments, and consistent form UI patterns.

2. **Durable Instruction State:** Multiple issues/PRs address making `AGENTS.md` and path-local instructions durable (not lost on compaction). This reflects a demand for **persistent project configuration** that survives session boundaries.

3. **Provider Login Expansion:** Several open issues (#34778, #34779, #34780) request V2 support for xAI Grok, GitHub Copilot, and Snowflake Cortex OAuth logins—all V1 features missing from the V2 migration.

4. **Cost Transparency:** Issue #30706 highlights gaps in cost tracking, particularly around cache-write pricing and zero-cost reports. Community wants accurate token/cost accounting.

5. **Session List Filtering:** Closed PR #34967 delivered `parentID` filtering, but the broader request pattern includes better session discovery, subagent management, and resumption workflows.

---

## Developer Pain Points

1. **macOS Terminal Color Rendering (Resolved):** The #1 pain point by community engagement (17 upvotes, 16 comments) was invisible text on the default Pro theme. Today's multiple issue closures suggest the root cause (likely terminal color detection or theme fallback) is now fixed.

2. **Windows Platform Issues:** Two new Windows-specific bugs today: TUI startup failure when `.opencode` exists (#35828) and port locking on exit (#32932). Windows users face distinct reliability problems.

3. **V2 Plugin Discovery Gaps:** Developers registering skills via V2 plugin API (`ctx.skill.transform()`) find them missing from `/skills` command results (#33896). Plugin tool registration is partially broken.

4. **Directory Attachments Breaking V2:** Attaching directories to prompts fails with unsupported media type errors (#34821). The fix is in PR review (#34844), but the bug blocks users who rely on multi-file context.

5. **Provider Content Filter UX:** Content-filter stops leave users confused—the turn "finishes" but no output appears (#34835). Better user-facing messaging is needed across all clients.

6. **Race Conditions at Startup:** Multiple issues (#35556, #35755) describe race conditions where plugin state isn't ready when sessions start. The "empty plugin generation" and "blank session flash" (#32535) damage first-impression reliability.

---

*Generated from anomalyco/opencode repository data. Digest date: 2026-07-08.*

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>

# Pi Community Digest — 2026-07-08

## Today's Highlights
The Pi community saw a cluster of quality-of-life fixes landing this week, with deep attention to extension loading performance and TUI stability. A significant conversation emerged around null-safety for reasoning model outputs and stricter context window clamping. Several "last-read" issues were closed, signaling a cleaning of triage backlog.

## Releases
No new releases in the last 24 hours.

---

## Hot Issues

### #6259 — fix: 'content is not iterable' when reasoning models return null content during tool use
*Author: kermankohli | Comments: 12 | 👍: 0*
**Why it matters:** A critical bug affecting all users of reasoning models (GLM-5.2, Fireworks) that return only `reasoning_content` + `tool_calls` without text `content`. The resulting `null` `AssistantMessage.content` crashes multiple code paths. Triaged as closed with a to-discuss tag.
🔗 [earendil-works/pi#6259](earendil-works/pi%20Issue%20#6259)

### #5501 — tolerate extra keys on edit tool edits[] items
*Author: wighawag | Comments: 11 | 👍: 0*
**Why it matters:** Models sometimes append stray keys (e.g. `newText_strip`, `newText_2`) after long `newText` values. The `edit` tool's JSON schema with `additionalProperties: false` rejects these, breaking agent runs. Closed with a simple schema relaxation.
🔗 [earendil-works/pi#5501](earendil-works/pi%20Issue%20#5501)

### #6234 — Escape leaves Pi stuck in Working when an extension context hook never settles
*Author: xz-dev | Comments: 10 | 👍: 0*
**Why it matters:** Pressing Escape during an active run is meant to abort, but if an extension event hook never settles, the TUI remains stuck in "Working..." state. Double-Escape handling is also broken. Open, high visibility.
🔗 [earendil-works/pi#6234](earendil-works/pi%20Issue%20#6234)

### #6206 — Clamping to context window prevents artificial context limits, distinct from maxTokens
*Author: DanielThomas | Comments: 5 | 👍: 0*
**Why it matters:** Recent fix (commit 09f1059) clamps `max_tokens` to the reported context window. This prevents users from setting an artificially lower context window distinct from output token limits. Open, affecting advanced users.
🔗 [earendil-works/pi#6206](earendil-works/pi%20Issue%20#6206)

### #6210 — /scoped-models cannot select model ids containing brackets
*Author: JokerQianwei | Comments: 5 | 👍: 0*
**Why it matters:** Users with custom model IDs containing brackets (e.g. `custom/bracketed-model[1m]`) cannot select them via `/scoped-models`. Likely a regex or parsing bug. Open.
🔗 [earendil-works/pi#6210](earendil-works/pi%20Issue%20#6210)

### #6362 — The paste counter is not reverted when pasted content is removed
*Author: affanali2k3 | Comments: 5 | 👍: 0*
**Why it matters:** When large pasted content (marked with `[Paste #1 +10 lines]`) is partially backspaced, the paste index marker is not reverted, causing mismatched paste-marker state and confusing UX. Closed as no-action.
🔗 [earendil-works/pi#6362](earendil-works/pi%20Issue%20#6362)

### #6226 — "Streams end without finish_reason" error when provider omits finish_reason for tool calls
*Author: dbrll | Comments: 4 | 👍: 0*
**Why it matters:** Providers like GLM 5.1 via NVIDIA NIM close streams without emitting `finish_reason` during tool calls. Adding a guard in `openai-completions.ts` solves this. Closed.
🔗 [earendil-works/pi#6226](earendil-works/pi%20Issue%20#6226)

### #6318 — pi-keyrouter doesn't see its config
*Author: TheK0tYaRa | Comments: 4 | 👍: 0*
**Why it matters:** The `pi-keyrouter` extension (v0.4.0) fails to detect its expected configuration file after creation. Reported as "malicious or unsafe behavior", but is a config path detection bug. Closed.
🔗 [earendil-works/pi#6318](earendil-works/pi%20Issue%20#6318)

### #6237 — pi installed by bun still uses #!/usr/bin/node
*Author: futu2 | Comments: 4 | 👍: 0*
**Why it matters:** Installing Pi via `bun` installs a `cli.js` with `#!/usr/bin/node` shebang, causing errors on systems without Node.js (only Bun). Closed with no action.
🔗 [earendil-works/pi#6237](earendil-works/pi%20Issue%20#6237)

### #3896 — TUI cursor stays active when terminal window loses focus
*Author: Br1NKOL | Comments: 3 | 👍: 7*
**Why it matters:** Pi's TUI cursor remains a filled active block even when the terminal loses focus. Other CLIs (Codex) show an inactive/hollow cursor. High 👍 count relative to comment count indicates a widely felt UX annoyance. Closed as last-read.
🔗 [earendil-works/pi#3896](earendil-works/pi%20Issue%20#3896)

---

## Key PR Progress

### #6405 — Update extensions documentation to explicitly point to locations used when installing extensions from npm/git
*Author: JustTooKrul | Closed* — Addresses a recurring confusion: Pi installs extensions in locations LLMs don't know to check. Docs now explicitly list npm/git install paths.
🔗 [earendil-works/pi#6405](earendil-works/pi%20PR%20#6405)

### #6169 — Disable padding for assistant messages
*Author: xl0 | Closed* — Fixes a UI spacing issue where assistant messages had unwanted padding. Closes #6168.
🔗 [earendil-works/pi#6169](earendil-works/pi%20PR%20#6169)

### #5846 — fix(tui): stabilize streaming code fence rendering
*Author: xl0 | Closed* — Significant fix for TUI markdown rendering instability during streaming. Closes #5825.
🔗 [earendil-works/pi#5846](earendil-works/pi%20PR%20#5846)

### #5913 — Stable markdown working
*Author: xl0 | Closed* — Companion to #5846, another attempt at stabilizing markdown rendering during streaming. ref #5825.
🔗 [earendil-works/pi#5913](earendil-works/pi%20PR%20#5913)

### #5711 — feat(coding-agent): add extension prompt guideline API
*Author: xl0 | Closed* — Adds an API for extensions to inject prompt guidelines. Closes #5710. Verified working.
🔗 [earendil-works/pi#5711](earendil-works/pi%20PR%20#5711)

### #6175 — fix(coding-agent): emit session name changes to extensions
*Author: xl0 | Closed* — Extensions now receive session name change events. Closes #6174.
🔗 [earendil-works/pi#6175](earendil-works/pi%20PR%20#6175)

### #6063 — Extension stats
*Author: xl0 | Closed* — Adds extension usage statistics. Also fixes OSC garbage printed after exit with `PI_STARTUP_BENCHMARK=1`. Closes #6062.
🔗 [earendil-works/pi#6063](earendil-works/pi%20PR%20#6063)

### #5085 — Expose full tool definitions from getAllTools
*Author: xl0 | Closed* — Extensions now receive a read-only copy of full tool definitions. Better than the earlier approach in #4954.
🔗 [earendil-works/pi#5085](earendil-works/pi%20PR%20#5085)

### #5756 — feat(coding-agent): Expose edit-diff for extensions
*Author: xl0 | Closed* — Extensions can now access edit diff data. Closes #5755.
🔗 [earendil-works/pi#5756](earendil-works/pi%20PR%20#5756)

### #5379 — Store user scoped local package installs as absolute paths
*Author: xl0 | Closed* — Fixes relative path issues for local package installs in user config. Closes #5378.
🔗 [earendil-works/pi#5379](earendil-works/pi%20PR%20#5379)

---

## Feature Request Trends

1. **Extension loading performance** — Multiple issues (#6360, #6400) ask for deferred/lazy extension loading to reduce startup time. #6360 proposes three preload modes (lazy/async/sync).
2. **First-class provider support** — Requests for new providers (Eden AI #6403, DeepInfra #6399, moonshotai/Kimi) indicate the community wants broader model access without manual config.
3. **Session metadata and no-session modes** — Feature requests for opaque custom metadata in JSONL headers (#6402), and starting a "no-session" even with `-r` (#6401), suggest power users want more control over session lifecycle.
4. **Image handling** — #6373 highlights that clipboard images are not sent to LLMs, and there's no remote model inference support for images. An old gap coming back.
5. **Global skill location detection** — #6408 shows the coding agent struggles to resolve global vs. project-local skill paths, a common UX issue.

---

## Developer Pain Points

- **Reasoning model incompatibility** — Two issues (#6259, #6226) highlight that Pi's code is not built to handle the quirks of reasoning models (null content, missing `finish_reason`). This is a systemic fragility.
- **Extension config discovery** — #6318 (pi-keyrouter config), #6400 (extension install paths), and #6406 (read-only config file locking) show that Pi's extension/config system is brittle under real-world filesystem configurations.
- **Escape handling reliability** — #6234's stuck-in-Working state after Escape is a critical usability issue that persists across multiple versions.
- **Token/context confusion** — #6206 (context clamping), #6378 (400 context length errors), and #6326 (custom_message bypassing compaction) show that users frequently hit token accounting issues that break their workflows.
- **TUI polish regression** — #3896 (focus cursor), #6362 (paste counter), and #6169 (padding) indicate that TUI details are getting attention but still have rough edges after the markdown streaming refactors.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>

# Qwen Code Community Digest — 2026-07-08

## Today's Highlights
Two patch releases (v0.19.7 and v0.19.7-nightly) shipped, primarily fixing the PR triage bot and adding WeCom channel documentation. The community is heavily focused on daemon performance and session management, with the RFC for multi-workspace daemon support (#6378) drawing 19 comments. Several recurring pain points around token consumption, Windows compatibility, and memory management continue to drive active PRs and issue discussions.

## Releases
- **v0.19.7** — Fixes the PR triage gate with batch detection and red flag patterns (#5723); includes an unreview tool for agent review workflows.
- **v0.19.7-nightly.20260708.394c1a289** — Same changes as v0.19.7 plus WeCom channel docs (#6490).
- **v0.19.6-preview.0** — Preview release containing only the WeCom channel documentation update.

**Full Changelogs**: [v0.19.7](https://github.com/QwenLM/qwen-code/com) | [v0.19.7-nightly](https://github.com/QwenLM/qwen-code/) | [v0.19.6-preview.0](https://github.com/QwenLM/qwen-code/com)

## Hot Issues (Top 10)

1. **#6378 — RFC: Multi-workspace daemon** (19 comments)  
   Proposes a 1-daemon-to-N-workspaces model while preserving backward compatibility. The core challenge is per-session overhead reduction — a tracking issue (#6312) has already been opened. This is the most active discussion this week.

2. **#6264 — `/review` skill consumes excessive tokens** (8 comments)  
   Users report the review skill burning through context windows. Screenshots show token usage spikes — community is asking for configurable token budgets or chunked review. [Issue](https://github.com/QwenLM/qwen-code/issues/6264)

3. **#6312 — Tracking: reduce per-session overhead on daemon** (5 comments)  
   Each `session/new` or `session/load` re-runs synchronous I/O on a shared event loop. Community is analyzing the hot path for optimization. [Issue](https://github.com/QwenLM/qwen-code/issues/6312)

4. **#6298 — Shell tool fails on Windows with stdout** (5 comments)  
   `run_shell_command` pipes output through `cat`, which doesn't exist in Windows `cmd.exe`. A known platform gap with a proposed welcome-PR label. [Issue](https://github.com/QwenLM/qwen-code/issues/6298)

5. **#6265 — `tool_search` invalidates KV-cache** (5 comments)  
   Every deferred-tool load triggers `setTools()` which flushes the LLM server's KV-cache. Degrades performance on repeated tool discovery calls. [Issue](https://github.com/QwenLM/qwen-code/issues/6265)

6. **#6384 — Hard limit: 0 when model reserves full context for output** (5 comments)  
   Environment-configured models can reserve their entire context window for output, causing `Context is too large` errors before any request is sent. User confusion about misconfigured limits. [Issue](https://github.com/QwenLM/qwen-code/issues/6384)

7. **#6318 — Unable to `/rewind` after `/compress`** (4 comments)  
   Rewinding to a pre-compression position fails — the session history after compression becomes non-navigable. Affects long-running sessions. [Issue](https://github.com/QwenLM/qwen-code/issues/6318)

8. **#6414 — VS Code connection failure** (3 comments)  
   "Failed to connect to Qwen agent" in VS Code extension — likely a daemon handshake issue. User provided a screenshot but no logs. [Issue](https://github.com/QwenLM/qwen-code/issues/6414)

9. **#6488 — Missing mid-turn streaming hook** (3 comments)  
   No hook event fires during assistant streaming — only `Stop` fires after the full turn. Gap for consumers wanting incremental UI updates. [Issue](https://github.com/QwenLM/qwen-code/issues/6488)

10. **#6321 — `PreToolUse` hook `ask` silently denied** (3 comments)  
    The `permissionDecision: "ask"` hook response is documented but never shows a confirmation prompt — tool calls are silently rejected. [Issue](https://github.com/QwenLM/qwen-code/issues/6321)

## Key PR Progress (Top 10)

1. **#6493 — Fix Web Shell daemon session counting**  
   Makes the usage dashboard count daemon sessions correctly (previously only read persisted `usage_record.jsonl`). [PR](https://github.com/QwenLM/qwen-code/pull/6493)

2. **#6482 — Bounded replay snapshot history**  
   Limits live-session replay to a serialized-byte cap, dropping older history. Critical for daemon memory management. [PR](https://github.com/QwenLM/qwen-code/pull/6482)

3. **#6448 — Show file path in compact tool summary**  
   Improves CLI output by showing actual file paths rather than generic "Read 1 file" for single collapsible tools. [PR](https://github.com/QwenLM/qwen-code/pull/6448)

4. **#6456 — Add `working_dir` to Agent tool for subagents**  
   Pins sub-agents to existing git worktrees, providing sandboxed file/shell resolution. Significant for multi-branch workflows. [PR](https://github.com/QwenLM/qwen-code/pull/6456)

5. **#6492 — SDK control request methods**  
   Adds `set_effort()`, `switch_model()`, `get_usage()`, and `get_context()` to both Python and TypeScript SDKs — runtime control over reasoning, models, and context. [PR](https://github.com/QwenLM/qwen-code/pull/6492)

6. **#6457 — QQ Bot group message handling**  
   Complete QQ Bot channel with keyword triggers, @-mention detection, and cron-msg-experimental support (251 files, 1 commit). [PR](https://github.com/QwenLM/qwen-code/pull/6457)

7. **#6393 — Inline skill preview and editor handoff**  
   Auto-generated skills show an inline preview before commit, plus an off switch. Closes the "blind accept/discard" gap for skill generation. [PR](https://github.com/QwenLM/qwen-code/pull/6393)

8. **#6489 — `MessageDisplay` hook for mid-turn streaming**  
   Implements the feature requested in #6488 — fires repeatedly as assistant replies stream. Enables incremental UI in CLI and ACP/IDE sessions. [PR](https://github.com/QwenLM/qwen-code/pull/6489)

9. **#6446 — Relay ACP permission requests through channels**  
   Routes ACP permission requests through channel chat (approve once/always/deny) instead of auto-approving. Fixes security gap in channel adapters. [PR](https://github.com/QwenLM/qwen-code/pull/6446)

10. **#6483 — Reject Windows-style artifact paths**  
    Tightens `record_artifact` validation to reject backslash traversal and Windows absolute paths on POSIX/Linux, preventing path injection. [PR](https://github.com/QwenLM/qwen-code/pull/6483)

## Feature Request Trends

- **Multi-workspace daemon** (#6378) — The highest-activity thread this week. Users want to run `qwen serve` once and manage multiple project workspaces without separate daemon processes.
- **Streaming hooks** (#6488, #6321, #6489) — Demand for mid-turn hook events (not just `Stop`/`SubagentStop`) to enable incremental UI updates and real-time tool permission prompts.
- **Channel expansion** — WeCom (merged), DingTalk interactive cards (#6443), and QQ Bot group support (#6457) show strong interest in enterprise messaging integrations.
- **Skill/workflow enhancements** (#6452) — Users want "prompt as code" with branching logic, plus integration with external workflow engines (Dify, n8n). The `/review` token consumption issue (#6264) is driving the conversation.
- **Memory and session management** — Better worktree memory isolation (#6449), stale index after `/remember` (#6487), and per-project model overrides (#6052) are recurring themes.

## Developer Pain Points

1. **Token consumption spikes** — The `/review` skill (#6264) and large PDF reads (#6408) can blow past context limits. Users want token budgets, chunked processing, and better diagnostics before requests fail.
2. **Windows compatibility** — Shell tool fails when stdout is produced (#6298); artifact path validation needed for Windows-style paths (#6483). Cross-platform testing seems insufficient.
3. **Session history degradation** — `/rewind` after `/compress` (#6318), stale memory indices (#6487), and daemon session reordering (#6438) make long-running sessions unreliable.
4. **Silent failures** — `PreToolUse` hook `ask` is silently denied (#6321), non-SSE 200 responses logged as empty interactions (#6465), and plan mode content leakage (#6237). Users report bugs with no clear error messages.
5. **Context overhead** — Startup context (skills list, CLAUDE.md) pollutes session titles (#6419); re-invoking skills appends duplicate instructions (#6427). Wasteful token usage on every session load.
6. **Pricing/auth friction** — Multiple subscription access issues (#6477, #6475) and hard-to-read auth URLs in non-interactive mode (#6428) create onboarding hurdles.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>

# DeepSeek TUI Community Digest — 2026-07-08

## Today's Highlights

The project has formally rebranded to **CodeWhale**, with v0.8.67 as the last release under the legacy `deepseek-tui` name—all future releases ship as `codewhale`. Today’s activity is dominated by **v0.8.68 stabilization**: critical bugfixes for sub-agent detail panels, Ctrl+C handling in raw-mode, and Fleet setup modal alignment, plus a CI fix to prevent bot auto-labeling loops. The milestone execution board (#4092) is now the canonical packet for all v0.8.68 work, consolidating lane-ordered agent workflows with stopship, catalog, workflow UI, TUI copy, and release-gate phases.

## Releases

- **v0.8.67** — Final release under the legacy `deepseek-tui` npm package. The canonical project, command, and npm package are now **CodeWhale**. Users still on `deepseek` / `deepseek-tui` names are directed to [docs/REBRAND.md](https://github.com/Hmbown/CodeWhale/blob/main/docs/REBRAND.md) for migration instructions. No functional changes in this version.

## Hot Issues

| # | Issue | Why It Matters | Community Signal |
|---|-------|----------------|-----------------|
| [#2487](https://github.com/Hmbown/CodeWhale/issues/2487) | `yolo` mode freezes: "Turn stalled — no completion signal" | Core usability blocker for autonomous mode; user cannot recover after stall | 20 comments, long-running (since June 1) |
| [#3144](https://github.com/Hmbown/CodeWhale/issues/3144) | Add natural-language auto-review policy & pre-push review gate | Responds to Cursor's security/review advances; critical for autonomous safety | 14 comments, closed — design accepted |
| [#3063](https://github.com/Hmbown/CodeWhale/issues/3063) | v0.8.59 release tracker: TUI mouse-report leak on macOS | Stabilization release after v0.8.58; addresses cross-platform input leak | 11 comments, closed — shipped |
| [#1812](https://github.com/Hmbown/CodeWhale/issues/1812) | Windows TUI freeze (crossterm poll deadlock) | Windows 11 intermittent freeze — process lives but UI unresponsive; two captured events with logs | 11 comments, closed — regression watch |
| [#4092](https://github.com/Hmbown/CodeWhale/issues/4092) | v0.8.68 execution board (canonical agent packet) | Central triage packet replacing July 7 packet; every milestone issue gets one `lane-*` label | 10 comments, **OPEN** — active coordination hub |
| [#4094](https://github.com/Hmbown/CodeWhale/issues/4094) | Sub-agent detail panel empty/freezes TUI during active work | Dogfood-found UX blocker — critical for debugging agent workflows | 4 comments, **OPEN** — release blocker |
| [#2261](https://github.com/Hmbown/CodeWhale/issues/2261) | Windows TUI crash: input leaks to PowerShell | Critical Windows usability: focus loss causes TUI input to be executed by shell | 6 comments, closed — high urgency |
| [#1835](https://github.com/Hmbown/CodeWhale/issues/1835) | Windows: IME composition event deadlock | Chinese IME users cannot type; input field completely unresponsive | 5 comments, closed — key localization issue |
| [#1472](https://github.com/Hmbown/CodeWhale/issues/1472) | Deadlock: API connection stall blocks on pipe_read | Process hangs unrecoverably when API stalls; Ctrl+C ineffective | 2 comments, closed — reliability risk |
| [#2300](https://github.com/Hmbown/CodeWhale/issues/2300) | Multi-model compatibility & automatic Fleet loadout selection | Preserves user request for multi-model support; used as acceptance fixture for v0.8.65 routing | 8 comments, closed — feature milestone |

## Key PR Progress

| # | PR | Description | Status |
|---|-----|-------------|--------|
| [#4181](https://github.com/Hmbown/CodeWhale/pull/4181) | Fix Fleet setup modal role/profile roster editor | Aligns modal with role/profile editing instead of provider-scoped model picker; persists provider+model route identity | **OPEN** |
| [#4189](https://github.com/Hmbown/CodeWhale/pull/4189) | Fix CI: only auto-label `agent-ready` on issue open | Prevents bot from re-adding label on every label edit; stops triage-intent conflicts | Merged |
| [#4182](https://github.com/Hmbown/CodeWhale/pull/4182) | Populate sub-agent detail panel with live activity | Fixes #4094: shows tool calls, status, final summary/handoff; bounds/truncates long trails | Merged |
| [#4180](https://github.com/Hmbown/CodeWhale/pull/4180) | Normalize raw Ctrl+C byte for PTY quit-arm flow | Fixes #4090: canonicalizes 0x03 before disposition routing; adds regression tests for double-Ctrl+C | Merged |
| [#4163](https://github.com/Hmbown/CodeWhale/pull/4163) | v0.8.68 agent execution lanes & milestone sync | Wave-based workflow files (stopship→catalog→workflow UI→TUI copy→release gate) plus playbook | Merged |
| [#4099](https://github.com/Hmbown/CodeWhale/pull/4099) | Full 0.8.68 release train | Six commits: completion polling fails closed; cancel interrupts; TUI fix for mouse-mode state machine; expanded TUI config for modes | Merged |
| [#3902](https://github.com/Hmbown/CodeWhale/pull/3902) | Fix five render/input hot paths (#3896–#3900) | Fixes double-render of Tasks sidebar, per-frame TTY resize, sub-agent map rebuild, input buffering; four regressions caught by adversarial review | **OPEN** |
| [#4044](https://github.com/Hmbown/CodeWhale/pull/4044) | Localize dynamic welcome steps | First-run welcome screen through `MessageId` registry; renders actual onboarding gates; adds sparse `zh-Hant` locale | **OPEN** |
| [#4045](https://github.com/Hmbown/CodeWhale/pull/4045) | Fix `edit_file` UTF-8 fuzzy cursor panic | CJK multibyte character slicing panic fixed; normalized cursor advances by code point | Merged |
| [#4088](https://github.com/Hmbown/CodeWhale/pull/4088) | Preserve native selection without mouse capture | Fixes #4026: leaves alternate-scroll mode off when `--no-mouse-capture` active; host terminal fully owns drag selection | Merged |

## Feature Request Trends

1. **Autonomous workflow reliability** — Multiple issues (#2487, #3144, #4092) highlight demand for self-healing agent loops, completion-signal timeouts that fail closed rather than fabricate success, and pre-push security review gates.

2. **Multi-model provider routing** — #2300 and PRs #4181, #3969 show strong interest in per-sub-agent provider selection, Fleet loadout auto-selection, and clear documentation distinguishing `provider = vllm` vs `openai`.

3. **Cache-maximal context management** — #528, #2956, #2953 advocate for re-reading active files instead of summarizing, reducing repeated transcript payload, and slimming the base prompt toward Codex-parity token usage.

4. **WhaleFlow workflow mode** — #2981, #2973, #2979 drive toward production async executor with bounded concurrency, cooperative cancellation, token/cost budgets, and TUI monitoring surfaces for run/inspect/replay.

5. **Hotbar quick-action surface** — #2061, #2071, #2072 request an optional 8-slot MMO-style action bar with opt-in setup wizard and documentation — currently off by default per v0.8.66 direction.

6. **Windows IME & input method compatibility** — #1835, #2261, #1812 expose ongoing pain with Chinese IME deadlock, input leakage to PowerShell, and crossterm poll freezes on Windows 11.

## Developer Pain Points

- **Windows stability remains the top friction point**: Three separate issues (#1812, #2261, #1835) report TUI freezes, input leakage to host shell, and IME deadlock — all on Windows 10/11 with crossterm. The v0.8.59 mouse-report leak fix (#3063) addresses the macOS side, but Windows still lacks a complete fix for the poll-level freeze.

- **Agent completion stalling is the #1 runtime frustration**: #2487 shows users cannot recover from "Turn stalled — no completion signal" in `yolo` mode; the `continue` command does not resume. Community response (20 comments) indicates this blocks full autonomous usage.

- **Sub-agent observability is too thin**: #4094 (4 comments, release-blocker) was found during dogfood: opening a sub-agent detail panel for a running worker shows almost nothing. Developers debugging multi-agent workflows need live tool-call tracking.

- **Rebranding migration overhead**: v0.8.67 stops `deepseek-tui` releases; users must follow `docs/REBRAND.md` to migrate to `codewhale`. While not a bug, this creates a coordination burden for existing scripts and CI pipelines.

- **CI labeling fights human triage**: #4189 fix shows that the auto-label bot re-added `agent-ready` to issues where a human deliberately removed it, causing triage context loss. This points to a broader need for smarter CI/triage interaction patterns.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*