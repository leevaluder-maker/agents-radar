# AI CLI Tools Community Digest 2026-07-13

> Generated: 2026-07-13 01:52 UTC | Tools covered: 9

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

# AI CLI Developer Tools Ecosystem: Cross-Tool Comparison Report
**Date:** 2026-07-13

---

## 1. Ecosystem Overview

The AI CLI developer tools landscape on July 13, 2026, reveals a maturing but uneven ecosystem where seven major tools compete across overlapping use cases. Two dominant themes emerge: **platform stability vs. innovation tension**, and **Windows as a persistent second-class platform** across nearly every tool. While Claude Code and OpenAI Codex command the largest communities and deepest feature sets, both are grappling with regression clusters from recent merges (Cowork for Claude, MultiAgent V2 for Codex). The mid-tier tools—Gemini CLI, Copilot CLI, and OpenCode—show rapid iteration with meaningful architectural proposals (multi-workspace daemons, AST-aware navigation), while smaller entrants like Kimi Code CLI and DeepSeek TUI focus on provider compatibility and localization. A concerning pattern across all tools is the gap between configuration UI and runtime behavior, particularly around permission systems, model overrides, and session persistence.

---

## 2. Activity Comparison

| **Tool** | **Open Issues** | **PRs (last 24h)** | **Release Today** | **Key Stability Signal** |
|---|---|---|---|---|
| **Claude Code** | 50+ (10 hot) | 2 substantive + 1 closed | None | Regression cluster (3 Cowork bugs in 4 days) |
| **OpenAI Codex** | 10 hot (21+ total cited) | 4 referenced (from log fix) | None | GPT-5.6 Sol/Luna model confusion |
| **Gemini CLI** | 10 hot | 10 (5 merged, 5 open) | v0.52.0-nightly | CVE-2026-9277 security fix merged |
| **Copilot CLI** | 10 hot | 1 (security-related) | None | Native V8 crash (#4102) under triage |
| **OpenCode** | 10 hot | 10 (all closed/merged) | None | Heavy TUI/core fix activity (kitlangton) |
| **Kimi Code CLI** | 1 updated | 2 (both from he-yufeng, open 2+ months) | None | Stagnant PR pipeline |
| **Pi** | 10 hot | 10 (all closed) | None | High PR throughput, all merged |
| **Qwen Code** | 10 hot | 10 (7 open, 3 closed) | None | Nightly release failed; CI instability |
| **DeepSeek TUI** | 10 hot | 10 (7 closed, 3 open) | None | Korean locale + Anthropic fixes merged |

**Observation:** Pi and OpenCode show the highest PR throughput today, while Kimi Code CLI and Copilot CLI have the least visible engineering activity. Qwen Code's CI pipeline is notably unstable.

---

## 3. Shared Feature Directions

The following requirements appear across **three or more** tool communities, indicating broad market demand:

### Agent/Subagent Reliability
- **False success signals** — Gemini CLI (#22323), Kimi Code CLI, OpenCode (#3743): Subagents report "GOAL"/"success" when actually truncated or failed.
- **Subagent model inheritance** — OpenAI Codex (#31814), OpenCode (#36250): Subagents ignore per-agent model config, forcing parent model on all children.
- **Concurrency hazards** — Copilot CLI (#4101), Pi (#6558): Tool results attaching to wrong branches or blocking during agent transitions.

### Windows Platform Parity
- **Installation/update failures** — Claude Code (#76094, sandbox crash), OpenAI Codex (#32492, stuck setup), Copilot CLI (#4095, access denied), Pi (#6569, model 404).
- **Terminal corruption** — Gemini CLI (#28370, full-history replay on resize), Copilot CLI (#4069, TUI wedge), OpenCode (#31972, Plan/Build toggle disabled), Qwen Code (#6776, Ctrl-C garbled).
- **Clipboard/copy-paste issues** — Claude Code (#43477), OpenCode (#4283, #30068).

### Session & State Persistence
- **Session corruption on resume** — Copilot CLI (#4098, malformed JSONL), Pi (#5463, auto-compaction error), Qwen Code (#6742, premature UUID advance).
- **Cross-app state inconsistency** — Copilot CLI (#4094, delete doesn't propagate), Qwen Code (#6726, daemon restart drops workspaces).
- **Session bloat from binary artifacts** — Copilot CLI (#4097, apply_patch stores binaries), OpenCode (#36523, event tables 2-16 GB).

### Configuration vs. Runtime Gap
- **Permission system trust** — Claude Code (#15921, #57132): Rules appear loaded but silently ignored.
- **Model overrides ignored** — OpenAI Codex (#31097, #31814): MultiAgent V2 forced despite disable flag.
- **CLI flags overridden by env** — DeepSeek TUI (#4298): `--model` flag not respected when API key set.

### Prompt Cache & Token Efficiency
- **Cache invalidation** — Qwen Code (#6721): Deferred tool discovery destroys prompt cache. DeepSeek TUI (#4348): Cache-write billing fixes.
- **Token waste** — OpenAI Codex (#32640, `wait` tool burns tokens), Gemini CLI (#26522, auto-memory infinite retries), Claude Code (#67609, advisor fails at 100K tokens).

---

## 4. Differentiation Analysis

| **Dimension** | **Claude Code** | **OpenAI Codex** | **Gemini CLI** | **Copilot CLI** | **OpenCode** | **Pi** | **Qwen Code** | **DeepSeek TUI** |
|---|---|---|---|---|---|---|---|---|
| **Primary user** | Power developers, deep sessions | Enterprise, CI/CD | Google ecosystem, MCP devs | GitHub-native, multi-agent | Multi-model, tinkerers | Extension devs, Pi ecosystem | Qwen model optimizers | Cost-conscious multi-provider |
| **Key strength** | Cowork, Fable-5 advisor | GPT-5.6, SQLite fix | MCP interoperability, evals | GitHub integration, voice | V2 CLI, multi-provider | Extension API, compaction | SKILL.md, daemon architecture | Provider routing, i18n |
| **Key weakness** | Regression velocity | Model-enforced defaults | Windows terminal | V8 crashes, MCP gap | Config fragility | Compaction races | CI instability | Anthropic API friction |
| **Unique feature** | FleetView agent sessions | Responses Lite API | AST-aware code nav | MultiAgent V2 forced | "Teach"/Guide Mode | Full-history pager | Multi-workspace daemon | Offline scorecard |
| **Platform parity** | Poor (Windows) | Poor (Windows) | Poor (Windows) | Poor (Windows) | Moderate | Moderate | Moderate | Good (BSD support) |

**Key Differentiators:**
- **Claude Code** leads in collaborative features (Cowork, FleetView) but suffers from rapid regression after merges.
- **OpenAI Codex** is the most enterprise-oriented, with the GPT-5.6 model line driving both innovation and configuration frustration.
- **Gemini CLI** invests most in systematic evaluation infrastructure (76 behavioral tests) and security (CVE response).
- **Copilot CLI** is the most GitHub-integrated but has the most critical stability issues (V8 crashes, TUI wedges).
- **OpenCode** has the broadest model support but at the cost of config complexity.
- **Pi** has the healthiest extension ecosystem but faces race conditions in core agent lifecycle.
- **Qwen Code** is architecturally ambitious (multi-workspace, skill contexts) but held back by CI instability.
- **DeepSeek TUI** is the most cost-focused, with provider-aware pricing and the best cross-platform coverage.

---

## 5. Community Momentum & Maturity

### High Momentum / Rapid Iteration
- **OpenCode** — 10 merged PRs in 24 hours, active kitlangton contributions, V2 CLI gaining traction.
- **Pi** — 10 closed PRs, strong extension ecosystem, rapid issue-to-fix cycle (e.g., tree navigation fix in #6559).
- **Qwen Code** — High architectural ambition (multi-workspace RFC, skill lifecycle), despite CI instability.

### Established / Mature but Slowing
- **Claude Code** — Largest community (50+ issues, high upvotes), but regression velocity suggests quality control challenges post-merges.
- **OpenAI Codex** — Second-largest community, but model-enforced defaults are eroding user trust. The SQLite fix (#28224, 434 👍) shows responsive engineering when issues reach critical mass.

### Growing / Emerging
- **DeepSeek TUI** — Strong week with Korean i18n, Anthropic fixes, MiniMax support. Low issue count but active PR pipeline.
- **Gemini CLI** — Steady dependency updates, security fixes, and evaluation infrastructure. Community engagement moderate but focused.

### Stagnant / Low Activity
- **Kimi Code CLI** — Only 2 PRs updated, both open for 2+ months. Single new issue in 24 hours. Minimal community engagement.
- **Copilot CLI** — Only 1 PR (security), with critical bugs (V8 crash, TUI wedge) under triage but no fix in sight. Community frustration evident.

---

## 6. Trend Signals

### For Developers & Tool Builders

1. **Windows parity is the #1 unmet need.** Every tool has multiple open Windows-specific bugs affecting installation, terminal rendering, clipboard, and sandbox setup. The ecosystem treats Windows as a secondary target, creating opportunity for any tool that invests in first-class Windows support.

2. **Configuration reliability is eroding trust.** Across all tools, users report that settings appear accepted but are silently ignored—permission rules, model overrides, keybindings, and CLI flags. This "UI/runtime gap" is a systemic quality issue that undermines the promise of deterministic AI tooling.

3. **Subagent orchestration is the next frontier.** The most active debates center on how subagents should inherit configuration, report status, and handle failures. False success signals (Gemini #22323) and model inheritance locks (Codex #31814, OpenCode #36250) are blocking multi-agent workflows. Tools that solve subagent lifecycle cleanly will gain significant advantage.

4. **Session persistence is fragile.** Copilot CLI (#4098), Pi (#5463), and Qwen Code (#6742) all have bugs where session state corrupts on resume or deletion. As users increasingly rely on long-running, resumable sessions for complex tasks, this fragility becomes a hard blocker.

5. **Cost transparency is emerging as a differentiator.** DeepSeek TUI's provider-aware pricing (#4335) and Kimi Code CLI's rate limit visibility (#2318) signal growing demand for accurate, per-turn cost tracking. Users are increasingly cost-conscious and want tools that help manage API spend.

6. **Multi-model support is table stakes, not differentiation.** Every tool now supports multiple providers. The differentiators are shifting to *how well* they handle model-specific quirks—OpenAI's Responses Lite vs. standard payloads, Anthropic's `input_schema` validation, Gemini's `forceAdaptiveThinking`. The tools that abstract these differences cleanly will win.

7. **Terminal/TUI quality matters more than ever.** Users are demanding truecolor support, no hard line-wrapping, graceful Ctrl+C handling, and tmux/screen compatibility. Claude Code (#43113) and DeepSeek TUI (#4266) both see this. The terminal is the UI—tools that break terminal expectations lose user trust quickly.

8. **Extension ecosystems are accelerating.** Pi's extension API, Qwen Code's skill system, and OpenCode's "Teach" mode all point toward a future where AI CLI tools are platforms, not standalone apps. The extensibility winners will attract the most developer mindshare.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)

Here is the community highlights report for the `anthropics/skills` repository, based on the most active Pull Requests and Issues as of July 13, 2026.

---

## Claude Code Skills Community Highlights Report

### 1. Top Skills Ranking (By Discussion Activity)

**1. Document Typography Skill** (#514)
- **Functionality:** Prevents orphan word wrap, widow paragraphs, and numbering misalignment in AI-generated documents.
- **Discussion:** High engagement from users frustrated with aesthetic formatting issues in Claude’s output. The community praised its specificity to common pain points.
- **Status:** **Open**
- **Link:** https://github.com/anthropics/skills/pull/514

**2. ODT (OpenDocument) Skill** (#486)
- **Functionality:** Creates, fills, reads, and converts OpenDocument Format files (.odt, .ods). Supports LibreOffice and ISO standard formats.
- **Discussion:** Strong demand for enterprise document interchange. Users requested deeper template-filling and HTML conversion capabilities.
- **Status:** **Open**
- **Link:** https://github.com/anthropics/skills/pull/486

**3. Frontend-Design Skill Improvement** (#210)
- **Functionality:** Revises the frontend-design skill for clarity, actionability, and internal coherence.
- **Discussion:** Focused on ensuring instructions are executable within a single conversation. Received significant input on specificity and steering behavior.
- **Status:** **Open**
- **Link:** https://github.com/anthropics/skills/pull/210

**4. Skill-Quality-Analyzer & Skill-Security-Analyzer** (#83)
- **Functionality:** Meta-skills providing quality evaluation (structure, documentation, accuracy) and security analysis for other skills.
- **Discussion:** Recognized as essential for ecosystem trust. The community debated the weighting of security vs. quality dimensions.
- **Status:** **Open**
- **Link:** https://github.com/anthropics/skills/pull/83

**5. Testing-Patterns Skill** (#723)
- **Functionality:** Comprehensive guidance on testing philosophy (Trophy model), unit testing (AAA pattern), React component testing, and integration strategies.
- **Discussion:** Highly anticipated for standardizing testing practices during Claude Code sessions. Users requested more patterns for legacy codebases.
- **Status:** **Open**
- **Link:** https://github.com/anthropics/skills/pull/723

**6. Self-Audit Skill (v1.3.0)** (#1367)
- **Functionality:** Audits AI output before delivery, combining mechanical file verification with a four-dimension reasoning audit.
- **Discussion:** Novel approach to output quality gates. The community engaged heavily on the damage-severity priority ordering.
- **Status:** **Open**
- **Link:** https://github.com/anthropics/skills/pull/1367

**7. SAP-RPT-1-OSS Predictor Skill** (#181)
- **Functionality:** Enables predictive analytics on SAP business data using SAP's open-source tabular foundation model.
- **Discussion:** Niche but passionate demand from enterprise users. Discussion centered on handling SAP data schemas and model quantization.
- **Status:** **Open**
- **Link:** https://github.com/anthropics/skills/pull/181

**8. Color-Expert Skill** (#1302)
- **Functionality:** Provides expertise on color naming systems (ISCC-NBS, Munsell, RAL), color spaces (OKLCH, OKLAB, CAM16), and accessibility contrast.
- **Discussion:** Design-oriented users drove this discussion, requesting integration with visualization and accessibility skills.
- **Status:** **Open**
- **Link:** https://github.com/anthropics/skills/pull/1302

---

### 2. Community Demand Trends (From Issues)

- **Security & Trust Boundaries (#492):** The most-discussed issue (34 comments) reveals deep concern about community skills distributed under the `anthropic/` namespace. Users demand verified origins, permission scopes, and trust boundary enforcement.

- **Org-Wide Skill Sharing (#228):** Strong demand for enterprise-grade sharing mechanisms without manual `.skill` file distribution. Users want shared skill libraries or direct sharing links.

- **Skill-Creator Reliability (#556, #1169, #1061):** A cluster of issues reports persistent `recall=0%` bugs in the skill evaluation pipeline across Windows and Linux. This is a critical blocker for skill developers.

- **Agent Governance ( #412):** A proposal for safety patterns—policy enforcement, threat detection, and audit trails—for AI agent systems. Indicates demand for production-grade agent safety.

- **MCP Exposure for Skills (#16):** Users want skills to expose their functionality as MCP APIs, enabling composable AI software architecture.

---

### 3. High-Potential Pending Skills (PRs with Active Discussion)

| PR | Skill | Status | Why It Might Land Soon |
|---|---|---|---|
| #1367 | **Self-Audit** (v1.3.0) | Open | Low complexity, high impact; author active on comments |
| #1302 | **Color-Expert** | Open | Self-contained, no external dependencies |
| #723 | **Testing-Patterns** | Open | Broad demand; well-structured proposal |
| #514 | **Document Typography** | Open | Fixes a universal pain point (orphans/widows) |
| #83 | **Quality & Security Analyzers** | Open | Meta-skills critical for ecosystem health |
| #486 | **ODT Skill** | Open | Enterprise demand; template-filling is a gap |
| #210 | **Frontend-Design Improvement** | Open | Directly improves an existing skill |

---

### 4. Skills Ecosystem Insight

**The community's most concentrated demand is for infrastructure-level meta-skills (quality assurance, security auditing, and self-validation) to improve the trustworthiness and reliability of the skills ecosystem itself, alongside concrete skills that solve persistent formatting and enterprise document interchange problems.**

---

# Claude Code Community Digest
**Date:** 2026-07-13

---

## Today's Highlights

No new releases were published in the last 24 hours, but the community remains highly active with 50 open issues and 3 pull requests. The most significant developments include a critical regression in Cowork's sandbox/trusted-folder validation on Windows and macOS, escalating concerns about the Fable-5 advisor tool failing at ~100K tokens, and a growing chorus of requests for better terminal emulation control (truecolor support, soft word-wrap opt-out).

## Releases

No new releases in the last 24 hours. The current reported version across issues is **2.1.207** (binary).

## Hot Issues

1. **[#67609 – Advisor tool returns "unavailable" on claude-fable-5 when transcript exceeds ~100K tokens](https://github.com/anthropics/claude-code/issues/67609)**  
   *38 👍, 20 comments* — A major blocker for deep sessions on Anthropic's most advanced model. The advisor tool errors out with `advisor_tool_result_error` past roughly 100K tokens, effectively neutering complex multi-turn workflows. High community engagement suggests this affects production usage.

2. **[#15921 – VSCode Extension: .claude/settings.local.json permissions not respected](https://github.com/anthropics/claude-code/issues/15921)**  
   *28 👍, 28 comments* — Even with `bypassPermissions` enabled, file operations on Windows ignore local permission overrides. This has been open since December 2025, making it one of the longest-standing unresolved permission bugs.

3. **[#64654 – plugin:github MCP fails with HTTP 400 – malformed JSON-RPC payload](https://github.com/anthropics/claude-code/issues/64654)**  
   *41 👍, 16 comments* — A core MCP integration is broken for GitHub plugin users due to missing version tags in JSON-RPC payloads. High visibility (41 reactions) suggests widespread impact on CI/CD and repo-management workflows.

4. **[#43477 – Ctrl+C copy from Claude Code VS Code window fails](https://github.com/anthropics/claude-code/issues/43477)**  
   *2 👍, 14 comments* — A persistent UX bug on Windows where standard copy keyboard shortcuts don't work inside the VS Code extension chat panel. Despite low upvotes, the comment count indicates deep user frustration.

5. **[#43113 – Feature request: emit long lines for prose, let terminal handle wrapping](https://github.com/anthropics/claude-code/issues/43113)**  
   *51 👍, 10 comments* — The most-upvoted open feature request. Developers want a flag to suppress hard line-wrapping of markdown/prose output, which breaks terminal tools like diffs and `less` pagination.

6. **[#76094 – Cowork sandbox fails on Windows – "connection forcibly closed"](https://github.com/anthropics/claude-code/issues/76094)**  
   *0 👍, 5 comments* — A recent regression (SDK 2.1.181 → 2.1.202) that crashes VM guests during SDK install on Windows. Critical for Windows Cowork users.

7. **[#76254 – Cowork trusted-folder validation rejects Shared Drive root on macOS](https://github.com/anthropics/claude-code/issues/76254)**  
   *1 👍, 4 comments* — A regression where trusted-folder validation incorrectly blocks Shared Drive roots and first-level folders after an app update, while depth-2 folders pass. Indicates a path-matching bug in the permission system.

8. **[#57132 – Allow rules under ~/.claude/ don't match at runtime](https://github.com/anthropics/claude-code/issues/57132)**  
   *0 👍, 9 comments* — A deceptive bug: permission rules appear as "loaded" in `/permissions` but are silently ignored when editing files under `~/.claude/`. Undermines trust in the permission system's UI.

9. **[#76743 – Windows click-to-focus activates pending permission dialog](https://github.com/anthropics/claude-code/issues/76743)**  
   *0 👍, 4 comments* — A focus-stealing bug where clicking a Claude Code window to bring it to focus accidentally submits a pending permission dialog. Dangerous for automated/heads-off workflows.

10. **[#52477 – Claude overrode explicit pronouns in user memory with male bias](https://github.com/anthropics/claude-code/issues/52477)**  
    *2 👍, 8 comments* — Model behavior issue where Claude disregarded explicitly set pronouns in user memory, defaulting to male-gendered language. Raises concerns about memory reliability and bias.

## Key PR Progress

1. **[#76986 – fix(scripts): preserve existing labels when auto-closing duplicate issues](https://github.com/anthropics/claude-code/pull/76986)**  
   A small but impactful fix for the issue triage pipeline. Currently, the auto-close script overwrites the entire label set when marking duplicates, stripping important classification labels. This PR changes the logic to append `['duplicate']` instead of replacing.

2. **[#76985 – fix(plugin-dev): read full multi-line description in validate-agent.sh](https://github.com/anthropics/claude-code/pull/76985)**  
   Fixes a shell script that only extracted the first line of agent descriptions, truncating YAML frontmatter. Important for plugin developers with multi-line agent metadata.

3. **[#15165 – Update README.md](https://github.com/anthropics/claude-code/pull/15165)** *(CLOSED)*  
   A long-dormant documentation fix (opened Dec 2025, closed today) that updates a broken docs link in the README.

## Feature Request Trends

Based on the issue data, several clear demand patterns emerge:

1. **Terminal/TUI fidelity** (#43113, #77032): The most requested improvements are around better terminal emulation — support for truecolor (not just 256-color) and opt-out of hard line-wrapping. Developers want Claude Code to respect their terminal environment rather than imposing formatting.

2. **FleetView / agent session management** (#69449, #58812): Users running multiple concurrent agent sessions want per-project identification in the `claude agents` FleetView, and the current directory-based grouping is reportedly broken.

3. **Desktop ↔ VS Code parity** (#77003): Developers want the VS Code extension to show model name, mode/effort indicators, and token usage — features already present in the desktop app.

4. **Session auto-save** (#77011): A clear (if profanely expressed) demand for automatic session persistence without manual `/rename` commands.

5. **IDE integration polish** (#77029, #75196): Sticky copy buttons for long code blocks and proper RTL text rendering in the chat panel.

## Developer Pain Points

1. **Windows is a second-class platform**: Multiple open bugs (permissions, copy-paste, sandbox crashes, installer migration issues) specifically target Windows users. The click-to-focus permission bug (#76743) and Cowork sandbox regression (#76094) suggest Windows testing is under-resourced.

2. **Permission system trust issues**: Two distinct bugs (#15921, #57132) show that the permission system's UI state can be misleading — rules appear "active" but are silently ignored. This erodes confidence in a safety-critical feature.

3. **Model downgrades/content filtering opacity**: Multiple reports (#77006, #77027, #77002) describe unexpected model downgrades or API content-policy blocks with confusing or absent error messages. Users working with legitimate content (pet food labels, murder mystery fiction, checkpointing tools) feel unfairly flagged.

4. **Advisor tool fragility on large contexts**: The Fable-5 advisor failing at ~100K tokens (#67609) is a serious limitation for deep analytical sessions. Users report this makes the advisor effectively unusable for its intended purpose on the most capable model.

5. **Cowork regression cluster**: Three new bugs in the last 4 days (#76094, #76254, #76694) suggest the recent Chat/Cowork merge introduced cascading issues — sandbox crashes, broken shared-folder validation, and missing project setup UI. Rapid regression is a quality concern.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

# OpenAI Codex Community Digest — 2026-07-13

## Today's Highlights
A major SSD-endurance bug in Codex's SQLite feedback logging—capable of writing ~640 TB/year—has been resolved after a month of community outcry, with three merged PRs cutting 85% of log volume. Meanwhile, frustrations are boiling over around GPT-5.6 Sol and Luna model deployment, where forced MultiAgent V2 behavior and missing model listings are creating configuration dead-ends for power users. Windows users continue to face a barrage of app stability and connectivity issues, including crashes, stuck sandbox setup, and Norton false positives.

## Releases
No new releases in the last 24 hours.

## Hot Issues

1. **[#28224](https://github.com/openai/codex/issues/28224) — Codex SQLite feedback logs can write ~640 TB/year (CLOSED)**  
   A critical performance bug where Codex's feedback logging could rapidly consume SSD endurance. After 151 comments and 434 upvotes, three merged PRs (released in 0.142.0) reduced log volume by ~85%. Community gratitude directed at @jif-oai for the fix.

2. **[#31814](https://github.com/openai/codex/issues/31814) — GPT-5.6 Sol cannot specify subagent models (OPEN, 56 comments)**  
   Sol forces all subagents to also be Sol instances, ignoring user config. The root cause: MultiAgent V2 ignores the `features.multi_agent_v2` toggle because Sol enables it through model metadata. High community engagement (122 👍) indicates many users are affected.

3. **[#18960](https://github.com/openai/codex/issues/18960) — Frequent reconnect loop in Codex App (OPEN, 51 comments)**  
   Persistent WebSocket disconnections on macOS leaving users stuck in a reconnect loop. Has been open since April and remains unresolved, making it one of the longest-running connectivity issues.

4. **[#20214](https://github.com/openai/codex/issues/20214) — Codex App freezes/stutters on Windows 11 (OPEN, 34 comments)**  
   Despite ample system resources (Ryzen 5 5600, 32GB RAM), users report frequent UI freezes. A common pain point for Windows adopters with no fix in sight.

5. **[#31097](https://github.com/openai/codex/issues/31097) — GPT-5.5 forces MultiAgentV2 despite disable (OPEN, 6 comments)**  
   Companion issue to #31814: even when MultiAgent V2 is explicitly disabled, GPT-5.5 enables it and hides documented custom-agent controls. Echoes the broader concern about model-enforced defaults overriding user configuration.

6. **[#31967](https://github.com/openai/codex/issues/31967) — GPT-5.6 Luna resolves to missing internal engine (OPEN, 4 comments)**  
   Using a valid ChatGPT OAuth credential with model slug `gpt-5.6-luna` fails with a "Model not found" error from an internal engine name. Creates friction for developers authenticating via ChatGPT OAuth.

7. **[#32095](https://github.com/openai/codex/issues/32095) — False positive: GPT-5.6 Sol flags normal request as cybersecurity activity (OPEN, 5 comments)**  
   A Pro-tier ($200/mo) user reports that routine codex requests are incorrectly flagged by Sol's safety checks. Highlights potential over-aggressive safety scanning in new models.

8. **[#32640](https://github.com/openai/codex/issues/32640) — Built-in `wait` tool capped at ~50s causes massive token burn (OPEN, 4 comments)**  
   With `multi_agent_v2`, the `wait` tool re-samples every 50 seconds, burning tokens unnecessarily for long-running operations. A performance regression affecting Plus-tier users.

9. **[#32492](https://github.com/openai/codex/issues/32492) — Windows app stuck on "Finish Windows setup" (OPEN, 4 comments)**  
   Sandbox setup never triggers a real UAC prompt, and the "Retry" button fails instantly. New Windows users are completely blocked from using the app.

10. **[#32331](https://github.com/openai/codex/issues/32331) — Windows Codex triggers Norton 360 Behavioral Protection (OPEN, 2 comments)**  
    Simply opening an existing thread triggers Norton's behavioral detection engine (`IDP.HELU.PSE80%s_cmd`). Likely false positive but causing significant disruption for enterprise users with mandatory AV.

## Key PR Progress

1. **[#32668](https://github.com/openai/codex/pull/32668) — Revert "Update auto review prompting" (CLOSED)**  
    A swift revert of PR #31480, suggesting the auto-review prompting change introduced unintended behavior.

2. **[#29898](https://github.com/openai/codex/pull/29898) — Preserve PAT auth against host token injection (CLOSED)**  
    A security-focused PR that rejects `chatgptAuthTokens` while PAT auth is active, adds regression tests for host injection, and documents auth transition restrictions. Important for enterprise security posture.

3. **[#30504](https://github.com/openai/codex/pull/30504) — Edit previous prompts using session forks (OPEN)**  
    Replaces destructive `thread/rollback` with branch-based prompt editing in the TUI. Currently uses mutable source-thread deletion; aims to fix prompt editing dependency on session replay.

4. **[#32628](https://github.com/openai/codex/pull/32628) — Improve composer completion target resolution (CLOSED)**  
    Bot-authored PR that refines `@` and `$` completion targets to prefer nearest editable mentions and treat atomic text elements as boundaries. Reduces ambiguous completions.

5. **[#29432](https://github.com/openai/codex/pull/29432)** (referenced in #28224) — Part of the SQLite log reduction fix, released in 0.142.0.

6. **[#29457](https://github.com/openai/codex/pull/29457)** (referenced in #28224) — Second part of the SQLite log reduction fix, released in 0.142.0.

7. Additional PR referenced in #28224 — Third component of the log reduction solution.

8. PRs pending for #31814 / #31097 — No PRs yet addressing the MultiAgent V2 override issues, which remains a high-impact gap.

9. PRs pending for #18960 — No PRs yet for the WebSocket reconnect loop, concerning given its age.

10. PRs pending for #20214 — No PRs yet for Windows UI stuttering.

## Feature Request Trends

- **Enterprise deployment flexibility**: Strong demand (#21538) for a non-Microsoft Store Windows installer to support managed/blocked environments.
- **AGENTS.local overlays**: Request (#28739) for additive local config (`AGENTS.local.md`) with `@`-reference expansion and file attribution, mimicking Claude Code's workflow.
- **Open-VSIX parity**: Community asking (#32499) for the Codex IDE extension to be published to open-vsx in sync with the MS Marketplace, as Cursor and other editors rely on open-vsx.
- **Cross-platform remote control reliability**: Multiple issues (#31387, #31973, #32164) ask for stable QR-based remote pairing on Windows, which consistently fails.

## Developer Pain Points

1. **Model-enforced defaults overriding user config**: GPT-5.5/5.6 Sol and Luna models force MultiAgent V2 and subagent model choices regardless of user `features` toggles. This erodes trust in configuration and is the most upvoted category this week (#31814, #31097).

2. **Windows app stability**: A deluge of Windows-specific issues — sandbox setup blocked (#32492), Norton false positives (#32331), WebView crashes (#30178), missing tool call results (#32653), spawn probes (#29110). Windows remains a second-class platform for Codex Desktop.

3. **Connectivity and reconnection fragility**: The longstanding WebSocket reconnect loop (#18960) on macOS, plus Windows remote control never completing enrollment (#32164), create a perception that networking code is brittle.

4. **Token waste and performance regressions**: The `wait` tool capping at 50 seconds in multi_agent_v2 (#32640) burns tokens on long waits. The already-resolved SQLite feedback logging (#28224) wasted terabytes. Developers are sensitive to unnecessary resource consumption.

5. **Model availability confusion**: `/model` CLI command not listing GPT-5.6 models (#31873), and missing 5.6 support in IDE extensions (#32412), forces users to guess which models are truly available.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>

# Gemini CLI Community Digest — 2026-07-13

## Today's Highlights

A critical security fix (`CVE-2026-9277`) landed for the `shell-quote` dependency, alongside a major dependency sweep across 74 npm packages and 8 GitHub Actions. The most active community issues continue to center on subagent reliability—particularly a bug where subagent recovery after hitting `MAX_TURNS` falsely reports success—and a deeply disruptive Windows terminal replay bug that forces full-history dumps to stdout.

## Releases

**v0.52.0-nightly.20260713.gf354eebaf** — One fix:
- `fix(privacy): show a clear message when the account has no Code Assist tier` by @ompatel-aiml ([PR #28304](https://github.com/google-gemini/gemini-cli/pull/28304))

---

## Hot Issues (10 picks)

1. **[#22323](https://github.com/google-gemini/gemini-cli/issues/22323) — Subagent recovery after MAX_TURNS falsely reports GOAL success** (P1, 10 comments, 2 👍)
   A `codebase_investigator` subagent hits its turn limit, yet reports `status: "success"` with `Termination Reason: "GOAL"`. This masks real failures and prevents users from knowing their analysis was truncated.

2. **[#21409](https://github.com/google-gemini/gemini-cli/issues/21409) — Generalist agent hangs indefinitely** (P1, 7 comments, 8 👍)
   The most-upvoted open bug. Simple operations like folder creation cause “forever hangs” when the CLI defers to the generalist agent. Workaround: explicitly instruct the model not to use subagents.

3. **[#28370](https://github.com/google-gemini/gemini-cli/issues/28370) — Windows: Hot-Reload & Terminal Resizes Trigger Full-History Replay (C-Dump)** (P1, 1 comment)
   Newly filed but urgent. On Windows, any terminal resize or hot-reload during a session floods stdout with the entire conversation history. The “Ink UI redraw loop cascade” effectively breaks interactive use.

4. **[#25166](https://github.com/google-gemini/gemini-cli/issues/25166) — Shell command execution stuck on “Waiting input” after command completes** (P1, 4 comments, 3 👍)
   After executing trivial shell commands, the CLI hangs, showing the shell as active even though the command finished. Frequent across environments.

5. **[#21983](https://github.com/google-gemini/gemini-cli/issues/21983) — Browser subagent fails on Wayland** (P1, 4 comments, 1 👍)
   The browser subagent reports `Termination Reason: GOAL` but fails silently on Wayland display servers. Linux users are impacted directly.

6. **[#26522](https://github.com/google-gemini/gemini-cli/issues/26522) — Auto Memory retries low-signal sessions indefinitely** (P2, 5 comments)
   Auto Memory marks sessions as “unprocessed” when the extraction agent skips them, causing infinite retries. Leads to wasted model calls and noise.

7. **[#24353](https://github.com/google-gemini/gemini-cli/issues/24353) — Robust component-level evaluations** (P1, 7 comments)
   Epic tracking 76 behavioral eval tests across 6 Gemini models. Indicates the team is investing heavily in systematic regression prevention.

8. **[#22745](https://github.com/google-gemini/gemini-cli/issues/22745) — Assess AST-aware file reads, search, and mapping** (P2, 7 comments, 1 👍)
   Investigation into using ASTs for more precise method-bound reads and codebase navigation. Could reduce token waste and multi-turn back-and-forth.

9. **[#22672](https://github.com/google-gemini/gemini-cli/issues/22672) — Agent should stop/discourage destructive behavior** (P2, 3 comments, 1 👍)
   Model occasionally uses `git reset` or `--force` flags when safer alternatives exist. Community wants safety guardrails around destructive commands.

10. **[#20079](https://github.com/google-gemini/gemini-cli/issues/20079) — Symlinked agent files not recognized** (P2, 4 comments)
    `~/.gemini/agents/filename.md` is ignored when `filename.md` is a symlink. A basic usability gap for advanced configurations.

---

## Key PR Progress (10 picks)

1. **[#28367](https://github.com/google-gemini/gemini-cli/pull/28367) — fix: upgrade shell-quote to 1.8.4 (CVE-2026-9277)** (OPEN)
   Critical-severity vulnerability fix. `shell-quote` 1.8.3 allowed command injection; the Trivy scanner flagged it as “Likely exploitable.” Should be merged ASAP.

2. **[#28368](https://github.com/google-gemini/gemini-cli/pull/28368) — fix: upgrade vitest to 4.1.0 / 3.2.6 (CVE-2026-47429)** (OPEN)
   Another critical CVE fix, targeting the testing framework itself. Developers running `npm test` with vulnerable vitest versions are at risk.

3. **[#28369](https://github.com/google-gemini/gemini-cli/pull/28369) — feat(evals): add local report command and developer documentation** (OPEN)
   Adds `npm run eval:report` to aggregate Vitest pass rates by model, with support for duplicate tests. Lowers the barrier for contributors to run and interpret behavioral evals.

4. **[#28365](https://github.com/google-gemini/gemini-cli/pull/28365) — fix(core): scope tools.core wildcard deny to built-in tools** (OPEN, P1)
   Fixes a bug where setting `tools.core` to `[]` silently disabled all MCP tools. Introduces `builtinOnly` field to `PolicyRule`. Essential for users running MCP servers.

5. **[#28366](https://github.com/google-gemini/gemini-cli/pull/28366) — Tidy implementation detail in gemini-cli** (OPEN, P1)
   Scoped patch related to issue #28340. Small fix but tagged P1, suggesting it addresses a critical code-path.

6. **[#28364](https://github.com/google-gemini/gemini-cli/pull/28364) — fix(core): deep-merge user model config over defaults** (OPEN, P2)
   Shallow spreads in `Config` constructor caused deeply nested `modelConfigServiceConfig` overrides to silently drop. Fix enables proper cascading of model parameters.

7. **[#28377](https://github.com/google-gemini/gemini-cli/pull/28377) — chore(deps): bump the npm-dependencies group with 74 updates** (CLOSED, merged)
   Massive dependency refresh. Consolidates updates across 74 packages, reducing security surface and keeping lockfile current.

8. **[#28380](https://github.com/google-gemini/gemini-cli/pull/28380) — chore(deps): bump undici from 7.10.0 to 8.7.0** (CLOSED, merged)
   Major version upgrade for the Node.js HTTP client. Brings performance improvements and upstream fixes.

9. **[#28378](https://github.com/google-gemini/gemini-cli/pull/28378) — chore(deps): bump @agentclientprotocol/sdk from 0.16.1 to 1.1.0** (CLOSED, merged)
   ACP SDK jumps to 1.1.0, signaling stability in the Agent Client Protocol integration. Important for MCP interoperability.

10. **[#28379](https://github.com/google-gemini/gemini-cli/pull/28379) — chore(deps-dev): bump chrome-devtools-mcp from 0.19.0 to 1.5.0** (CLOSED, merged)
    Major leap for Chrome DevTools MCP tooling. Likely brings new debugging capabilities and improved browser agent integration.

---

## Feature Request Trends

- **AST-aware code navigation**: Two linked issues ([#22745](https://github.com/google-gemini/gemini-cli/issues/22745), [#22746](https://github.com/google-gemini/gemini-cli/issues/22746)) push for AST-based file reading and codebase mapping to reduce token waste and improve method-bound precision.
- **Subagent trajectory visibility**: [#22598](https://github.com/google-gemini/gemini-cli/issues/22598) requests subagent trajectories be shareable via `/chat share`, enabling better debugging and evals.
- **Safety guardrails**: [#22672](https://github.com/google-gemini/gemini-cli/issues/22672) calls for blocking or warning on destructive commands (`git reset --force`, `DROP TABLE`, etc.).
- **Automatic session takeover for browser agent**: [#22232](https://github.com/google-gemini/gemini-cli/issues/22232) proposes lock recovery and takeover when a browser profile is already in use.
- **Agent self-awareness**: [#21432](https://github.com/google-gemini/gemini-cli/issues/21432) wants the CLI to know its own hotkeys, flags, and capabilities well enough to act as its own guide.

---

## Developer Pain Points

- **False success signals**: The most-reported pain point—subagents (browser, codebase investigator) consistently report `"success"` and `"GOAL"` even when they silently fail or hit turn limits ([#22323](https://github.com/google-gemini/gemini-cli/issues/22323), [#21983](https://github.com/google-gemini/gemini-cli/issues/21983)).
- **Agent hangs and stuck I/O**: Three P1 bugs ([#21409](https://github.com/google-gemini/gemini-cli/issues/21409), [#25166](https://github.com/google-gemini/gemini-cli/issues/25166), [#22465](https://github.com/google-gemini/gemini-cli/issues/22465)) describe the CLI freezing on simple operations, creating interactive prompts, or hanging after command completion.
- **Windows terminal corruption**: The newly filed [#28370](https://github.com/google-gemini/gemini-cli/issues/28370) (history replay on resize) and the ongoing [#24935](https://github.com/google-gemini/gemini-cli/issues/24935) (terminal corruption after external editors) make Windows a second-class platform.
- **Subagent permission bypass**: [#22093](https://github.com/google-gemini/gemini-cli/issues/22093) reports subagents running with permissions set to “disabled” since v0.33.0, undermining user trust controls.
- **Auto Memory waste**: [#26522](https://github.com/google-gemini/gemini-cli/issues/26522) and [#26523](https://github.com/google-gemini/gemini-cli/issues/26523) highlight infinite retries and silent patch skipping in the Auto Memory system, wasting both model calls and developer time.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

# GitHub Copilot CLI Community Digest — 2026-07-13

## Today's Highlights

The community is grappling with a cluster of critical stability regressions uncovered over the past 48 hours, including a native V8 crash during tool-heavy turns and session resume, a TUI freeze on WSL2 that leaves terminals completely unresponsive, and a session-events corruption bug that prevents resumed conversations from loading. Concurrently, a significant MCP integration gap—where OAuth-authenticated remote MCP servers show "Connected" but their tools never appear in CLI sessions—has surfaced, along with a session-deletion orphan problem that breaks cross-app history consistency.

## Releases

No new releases in the last 24 hours. The latest stable version remains **v1.0.70-0**.

## Hot Issues (10 noteworthy items)

1. **[#4102 — Native V8 array-length crash during active tool-heavy turns and session resume](https://github.com/github/copilot-cli/issues/4102)**
   The packaged Linux x64 binary aborts inside V8 during tool-heavy sessions and resume operations. Initial suspicion of concurrent-resume pressure was ruled out; the crash occurs even with automatic restoration disabled. **Critical stability bug** — unpatched binary crashes are a hard blocker for production use. Community reaction: 0 👍 (new, under triage).

2. **[#4069 — TUI wedges mid-turn (screen clears, input dead, Ctrl+C/Ctrl+\ ignored) on WSL2 + Windows Terminal](https://github.com/github/copilot-cli/issues/4069)**
   Mid-session the terminal clears, input becomes completely unresponsive, and standard escape sequences fail. Root cause traces to `EIO` on stdout followed by `EPIPE` on the Rust JSON-RPC transport. **High-severity UX regression** — users lose work and cannot recover without killing the terminal. 8 👍, 7 comments.

3. **[#4098 — Resuming a session can leave truncated and concatenated events in events.jsonl](https://github.com/github/copilot-cli/issues/4098)**
   Resumed sessions produce malformed JSONL records — incomplete event prefixes concatenated with complete events on the same line, making further resumes impossible. **Data integrity issue** — undermines the rely-on-sessions workflow. 0 👍, 2 comments.

4. **[#4024 — Voice mode: all bundled ASR models fail silently](https://github.com/github/copilot-cli/issues/4024)**
   `/voice` records audio correctly (meter reacts, PulseAudio capture confirmed) but every `nemotron-*` ASR model returns empty transcriptions. Suspected `MultiModalProcessor` routing bug for `nemotron_speech (RNNT)` in Foundry Local Core. **Fully broken feature** — voice mode is unusable regardless of model selection. 0 👍, 8 comments.

5. **[#4096 — Third-party MCP server shows "Connected" but tools missing from CLI sessions](https://github.com/github/copilot-cli/issues/4096)**
   After OAuth sign-in to an Atlassian Remote MCP server, the app UI displays green "Connected," but the agent in spawned CLI sessions never has access to the tools. **MCP integration gap** — OAuth tokens are not bridged from app to CLI sessions. 0 👍.

6. **[#4094 — Deleting a session in the app doesn't remove it from session-store.db / VS Code history](https://github.com/github/copilot-cli/issues/4094)**
   Deleting a session from the Copilot app UI leaves the row intact in `data.db`, `session-store.db`, `search_index`, and `vscode.session.metadata.cache.json`. **Cross-app consistency bug** — users expect session deletion to be complete. 0 👍.

7. **[#4095 — Windows: plugin update fails with "Access is denied" while VS Code is running](https://github.com/github/copilot-cli/issues/4095)**
   `copilot plugin update` fails with `os error 5` when VS Code's Copilot extension holds watcher handles on `installed-plugins`. Git operations succeed but filesystem-level locks prevent replacement. **Platform-specific regression** — blocks plugin updates on Windows during active development. 0 👍.

8. **[#4097 — apply_patch stores deleted binary in session history, permanently exceeding CAPI 5 MB limit](https://github.com/github/copilot-cli/issues/4097)**
   When `apply_patch` deletes a large binary file, the entire binary is stored as a diff in `result.detailedContent`. This event remains in conversation history, causing subsequent requests to exceed the 5 MB CAPI limit, forcing `/compact` usage. **Session bloat** — one delete operation can permanently cripple session performance. 0 👍.

9. **[#4101 — write_agent may block until target agent starts processing, causing user input to queue](https://github.com/github/copilot-cli/issues/4101)**
   Calling `write_agent` to an idle background agent does not return control until the target agent wakes up. If the user sends a new message during this wait, input queues and the turn order breaks. **Concurrency hazard** — disrupts multi-agent workflows. 0 👍.

10. **[#4103 — Plugin marketplace clone disables Git credential helpers, breaking private HTTPS repos](https://github.com/github/copilot-cli/issues/4103)**
    Adding a plugin marketplace from a private Azure DevOps HTTPS repository fails even though manual cloning succeeds with Git Credential Manager. Suspected regression from the v1.0.70 "fail fast when marketplace plugin git auth needed" change. **Authentication regression** — breaks private plugin sources. 0 👍.

## Key PR Progress (notable changes)

Only 1 PR was updated in the last 24 hours:

- **[#4100 — shangti0168 (OPEN)](https://github.com/github/copilot-cli/pull/4100)**
  Title/description: "安全性". This PR appears to be a security-related change from the author `huangyoufeng76-debug`. No further detail on specific changes. 0 comments, 0 👍.

**Note:** Community PR activity is unusually low today. No other PRs of technical substance were updated in the reporting window.

## Feature Request Trends

Based on recent Issues activity, the most-requested feature directions are:

1. **Voice mode reliability** — Users expect `/voice` to work with all bundled ASR models. Complete silent failure is a blocker for accessibility and hands-free workflows.
2. **Session integrity guarantees** — Users want sessions that survive resume, are deletable cleanly, and don't balloon with binary artifacts.
3. **MCP tool availability in CLI sessions** — The gap between app UI and CLI session tool availability is a recurring theme: OAuth tokens, tool registrations, and connection state are not consistently bridged.

## Developer Pain Points

The top recurring frustrations from the community this week:

- **Terminal wedge / hard lockup on WSL2** (#4069) — Losing work mid-turn with no recovery path is the most upvoted pain point (8 👍 in under 4 days).
- **Native crashes in V8** (#4102) — Binary failures under normal tool-heavy usage erode trust in the product's production readiness.
- **Session corruption on resume** (#4098) — The core RAG workflow breaks silently; users discover corruption only when they need to revisit prior work.
- **Cross-app state inconsistency** (#4094, #4096) — Deleting sessions in one place but not another, connecting MCP servers in the app but not the CLI — these gaps create a fragmented user experience.
- **Plugin management friction on Windows** (#4095) — Lock contention with VS Code prevents routine plugin updates, forcing users to close their editor to update CLI plugins.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

# Kimi Code CLI Community Digest — 2026-07-13

## Today's Highlights

No new releases were published in the last 24 hours, but two long-standing pull requests from he-yufeng saw activity, addressing Windows binary metadata and non-UTF-8 worker output handling. A critical bug report (#2318) regarding TPD rate limit miscalculation remains open, drawing community attention as it exposes a potential platform-side quota enforcement issue affecting high-volume users.

## Releases

**None** — No new versions or tags were published in the last 24 hours. The current stable release remains **Kimi Code CLI 2.6**.

## Hot Issues

**#2318 — [bug] request reached organization TPD rate limit, current: 1505241**  
*Author: globalvideos272-lab | Created: 2026-05-18 | Updated: 2026-07-12 | 👍: 1*  
[GitHub](https://github.com/MoonshotAI/kimi-cli/issues/2318)  
**Impact:** The user reports that the CLI incorrectly calculates or fails to throttle requests against the organization's total-per-day (TPD) limit. The current counter (1,505,241) appears to be an erroneous accumulation, potentially blocking valid requests. This is a **high-stakes bug** for teams using moonshot.ai with a shared quota — one erroneous counter can halt all downstream work. Community reaction is muted (1 👍), but the severity is high. No assignee or comment yet, which may increase frustration.

*(Only 1 issue updated in the last 24h. No additional issues to select.)*

## Key PR Progress

**#2181 — fix: add Windows binary version info**  
*Author: he-yufeng | Created: 2026-05-07 | Updated: 2026-07-12*  
[GitHub](https://github.com/MoonshotAI/kimi-cli/pull/2181)  
**Summary:** Generates a PyInstaller Windows version-info file from `pyproject.toml` and injects it into both one-file and one-dir builds. Adds a CI assertion to ensure `FileVersionInfo` is never empty on Windows release artifacts. Fixes #2178. This is a **quality-of-life fix** for Windows users who rely on file properties for version management, IT auditing, or automated deployments. The PR also includes `ruff` linting — indicating the author maintains code quality standards.

**#2350 — fix: tolerate non-utf8 worker output**  
*Author: he-yufeng | Created: 2026-05-23 | Updated: 2026-07-12*  
[GitHub](https://github.com/MoonshotAI/kimi-cli/pull/2350)  
**Summary:** Fixes #2313. The web session runner previously decoded worker stdout/stderr with strict UTF-8, causing `UnicodeDecodeError` on Windows when child processes emit locale-encoded bytes (e.g., cp1252 smart punctuation). This change makes decoding **fault-tolerant**, preventing a single invalid byte from hiding the real worker failure. **Critical for Windows developers** using the CLI in environments with mixed-locale outputs — a long-standing pain point that this PR finally addresses.

*(Only 2 PRs updated in the last 24h. No additional PRs to select.)*

## Feature Request Trends

Based on broader issue analysis, the most requested directions include:

- **Windows-first compatibility fixes** — Issues around binary metadata, encoding, and process handling on Windows dominate recent activity. The community is clearly pushing for **first-class Windows support**.
- **Rate limit introspection** — Users want better visibility into TPD consumption, per-organization vs. per-user limits, and built-in backoff/retry logic. The 1.5M counter bug (#2318) has amplified this demand.
- **Improved error messages for non-UTF-8 outputs** — The frustration around cryptic `UnicodeDecodeError` masking real failures has been a recurring theme, now addressed by #2350.

## Developer Pain Points

1. **Rate limit opacity** — The most acute pain point. The CLI does not clearly surface the organization's TPD state, leading to surprise blocks. Issue #2318 reveals a possible **incorrect counter accumulation**, which could cause entire teams to be locked out erroneously.
2. **Locale/encoding brittleness on Windows** — A steady stream of issues (#2313 and predecessors) shows that the CLI's strict UTF-8 assumptions break when interacting with Windows native tools that emit cp1252 or other code pages.
3. **Slow PR turnaround** — Both #2181 and #2350 have been open for over two months with no merge. The community may perceive stagnation on quality-of-life and platform parity improvements, even though the code changes are small and well-tested.

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

# OpenCode Community Digest — July 13, 2026

## Today's Highlights

A wave of fixes hit the TUI and core layers today, with **kitlangton** landing a trio of contributions addressing form-dismissal crashes and bounded compaction for oversized sessions. GPT-5.6 model support remains a hot topic, with multiple issues and PRs addressing `max` reasoning effort and model-not-found errors. The V2 CLI continues to see growing community feedback, particularly around config discovery across git boundaries and MCP integration gaps.

---

## Releases

No new official OpenCode releases were published in the last 24 hours. The latest stable remains **v1.17.18**.

---

## Hot Issues

1. **#4283 – Copy To Clipboard is not working**  
   [link](https://github.com/anomalyco/opencode/issues/4283)  
   **105 👍 | 113 comments**  
   A long-standing issue (opened Nov 2025) that recently resurged. Text selected from chat output fails to copy on some OS configs. The high engagement suggests many users hit this daily.

2. **#36140 – GPT-5.6 Luna returns model not found with ChatGPT OAuth**  
   [link](https://github.com/anomalyco/opencode/issues/36140)  
   **84 👍 | 24 comments**  
   Newly surfaced model mismatch: `gpt-5.6-luna` is listed in the provider UI but returns HTTP 404. Critical for users relying on ChatGPT OAuth for the latest OpenAI models.

3. **#5076 – OpenCode should have better/safer defaults**  
   [link](https://github.com/anomalyco/opencode/issues/5076)  
   **61 👍 | 13 comments**  
   Security-minded proposal that remains open since Dec 2025. Advocates for permission-by-default, not allow-by-default, to prevent accidental file system access. Community strongly supports.

4. **#14273 – Free usage exceeded when using Zen free models**  
   [link](https://github.com/anomalyco/opencode/issues/14273)  
   **35 comments**  
   Users with paid balances incorrectly hit free-tier limits on Kimi K2.5 and MiniMax2.5. Suggests a misread of balance vs. usage quotas.

5. **#3743 – Loop in certain models**  
   [link](https://github.com/anomalyco/opencode/issues/3743)  
   **12 👍 | 26 comments**  
   Recurring issue where models (KIMI K2, MiniMax, GLM) enter infinite tool-calling loops. `/compact` sometimes helps, but the model often needs to be stopped manually.

6. **#30068 – Copying Japanese text results in mojibake**  
   [link](https://github.com/anomalyco/opencode/issues/30068)  
   **3 👍 | 15 comments**  
   UTF-8 misinterpreted as Latin1 during clipboard operations. Affects Japanese-language users globally. Updated today, indicating renewed attention.

7. **#22132 – OpenCode 1.4.3 hangs with local Ollama provider**  
   [link](https://github.com/anomalyco/opencode/issues/22132)  
   **5 👍 | 15 comments**  
   Hangs on simple prompts when using local Ollama, even though direct API calls work. Points to a provider adapter bug in `@ai-sdk/openai-compatible`.

8. **#33318 – Zen paid balance still hits FreeUsageLimitError**  
   [link](https://github.com/anomalyco/opencode/issues/33318)  
   **8 comments**  
   Users who add $20+ in credits still see daily free usage caps triggered within an hour. An urgent billing issue.

9. **#31972 – New Layout disables Plan/Build toggle**  
   [link](https://github.com/anomalyco/opencode/issues/31972)  
   **6 👍 | 7 comments**  
   Windows 10 users with the new UI layout flag enabled cannot switch between Plan and Build modes at all.

10. **#36250 – agent.model and agent.variant config ignored in handleSubtask**  
    [link](https://github.com/anomalyco/opencode/issues/36250)  
    **2 👍 | 2 comments**  
    Subagents in Task tool always inherit the parent model instead of respecting per-agent config. Blocks multi-model workflows.

---

## Key PR Progress

1. **#36591 – fix(tui): dismiss stale forms after failed reply**  
   [link](https://github.com/anomalyco/opencode/pull/36591)  
   **kitlangton** – Prevents form from trapping users after a managed-service restart. Dismisses orphaned forms gracefully.

2. **#36589 – fix(core): bound compaction request size**  
   [link](https://github.com/anomalyco/opencode/pull/36589)  
   **kitlangton** – Large sessions no longer wedge when inference requests exceed 10 MiB body limit. Compaction now accounts for serialized size, not just token count.

3. **#36577 – fix(core): load config across git boundaries**  
   [link](https://github.com/anomalyco/opencode/pull/36577)  
   **opencode-agent[bot]** – Reverts V1 implementation and fixes V2 config discovery to search ancestors across project/git boundaries. Fixes #36539.

4. **#36583 – fix(client): preserve compatible background service**  
   [link](https://github.com/anomalyco/opencode/pull/36583)  
   **kitlangton** – Stops transient health-check failures from forcing a destructive restart of a healthy service. Improves multi-window stability.

5. **#36563 – fix(core): use catalog small model for session titles**  
   [link](https://github.com/anomalyco/opencode/pull/36563)  
   **rekram1-node** – Session titles now prefer the catalog's small model, reducing overhead when no explicit title model is set.

6. **#36571 – feat(tui): add agent picker preview**  
   [link](https://github.com/anomalyco/opencode/pull/36571)  
   **opencode-agent[bot]** – Splits the agent picker into list + preview panes, showing descriptions and models without truncation.

7. **#36574 – fix(github-copilot): set Copilot-Integration-Id header**  
   [link](https://github.com/anomalyco/opencode/pull/36574)  
   **zhy-1976** – Fixes 403 Forbidden on GPT-5.6 models by setting the required `Copilot-Integration-Id: vscode-chat` header.

8. **#36560 – refactor(core): replace deferred tool option with codemode**  
   [link](https://github.com/anomalyco/opencode/pull/36560)  
   **rekram1-node** – Renames `deferred` to `codemode` (default true), keeping tools on provider native list when false. Consolidates registration semantics.

9. **#36542 – fix(core): tolerate AlreadyExists in FSUtil.ensureDir**  
   [link](https://github.com/anomalyco/opencode/pull/36542)  
   **BB-84C** – Prevents crashes when `ensureDir` races with concurrent calls. Fixes a regression from v1.17.15.

10. **#35824 – fix: gate non-media files to prevent converter crash**  
    [link](https://github.com/anomalyco/opencode/pull/35824)  
    **jwcrystal** – Stops unrecognized MIME types (`application/octet-stream`) from crashing the provider converter. Addresses #35697.

---

## Feature Request Trends

- **Unified model effort levels**: Multiple requests (#36141, #36391) ask for `"max"` reasoning effort exposure for GPT-5.6 family to match Codex UI "Ultra".
- **The "Teach" / Guide Mode**: Issues #12675 and #36521 propose interactive onboarding designed for developers new to AI-assisted coding, emphasizing prompt scaffolding and learning-by-doing.
- **Better security defaults**: Issue #5076 remains a top-voted feature, pushing for permission-by-default and least-privilege configurations out of the box.
- **Event table pruning**: Issue #36523 proposes optional compaction of event tables to prevent unbounded growth (2–16 GB reported for heavy users).
- **Plugin ecosystem improvements**: Multiple requests surface around MCP server toggling (#36482), external TUI plugin loading (#36525), and cross-git config inheritance (#36539).

---

## Developer Pain Points

1. **Clipboard encoding issues** – Two related issues (#4283, #30068) show that copying text—especially non-ASCII—routinely fails or produces corrupted output. High comment counts indicate widespread frustration.

2. **Billing / quota confusion** – Issues #14273 and #33318 reveal that paid Zen balances are not reliably respected, with users hitting free-tier limits despite having credits. Urgent for paying users.

3. **Config fragility across git boundaries** – V2 users (#36485, #36539) report that global configs and shared workspace settings fail to load in subfolders or child repos, breaking MCP servers and other multi-repo workflows.

4. **Model looping** – Issue #3743 (26 comments) remains unresolved: certain models enter infinite tool-calling loops with no reliable recovery path other than killing the session.

5. **Subtask model inheritance** – Issue #36250 highlights that subagents ignore per-agent model config, forcing all subtasks to use the parent model. Blocks users who need different models for planning vs. execution.

6. **MCP toggling and visibility** – Issue #36482 and #36580 report that MCP server toggles and pickers have no effect, despite servers being registered and visible via CLI. A core UX gap in V2.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>

# Pi Community Digest — 2026-07-13

## Today's Highlights
GPT-5.6 Codex model support continues to drive significant provider-side fixes and compaction improvements this week, with several critical patches landing for Amazon Bedrock `forceAdaptiveThinking` and OpenAI Codex session-ID handling. The TUI subsystem sees meaningful durability work: a v2 full-history pager PR and a terminal auto-wrap fix for rendering correctness. However, lingering agent lifecycle bugs around compaction, branch navigation during tool execution, and extension reload mechanics remain top-of-mind for the community.

## Releases
No new releases in the last 24 hours.

## Hot Issues

1. **#6477 — Compaction summary requests omit session ID, breaking compaction on OpenAI-Codex models** (OPEN, 5 comments, 8 👍)  
   [`earendil-works/pi#6477`](https://github.com/earendil-works/pi/issues/6477)  
   Compaction fails entirely on `gpt-5.6-luna` because the session ID is not forwarded in summarization requests. Community engagement is high — this blocks automatic compaction on Codex’s latest models.

2. **#6309 — [CLOSED] Clamping to context window prevents artificial context limits** (CLOSED, 10 comments)  
   [`earendil-works/pi#6206`](https://github.com/earendil-works/pi/issues/6206)  
   A fix for issue #5595 introduced `max_tokens` clamping to the reported context window, which prevents users from setting artificial limits below the model’s true capacity. Discussion suggests this was unintentional and should be re-evaluated.

3. **#5886 — AgentSession settlement/continuation and assistant-tail lifecycle bugs** (OPEN, 6 comments, 2 👍)  
   [`earendil-works/pi#5886`](https://github.com/earendil-works/pi/issues/5886)  
   A meta-issue tracking recurring post-run logic bugs where the agent tries to continue from an assistant-tail transcript that is no longer valid. Multiple related issues exist under this umbrella.

4. **#5463 — Auto-compaction after final turn throws error** (OPEN, 5 comments, 5 👍)  
   [`earendil-works/pi#5463`](https://github.com/earendil-works/pi/issues/5463)  
   When auto-compaction triggers after the last assistant message, the agent throws `Error("Cannot continue from message role: assistant")`. Community interest is high; this affects the default compaction flow.

5. **#6563 — TUI drops image blocks from user messages** (OPEN, 4 comments)  
   [`earendil-works/pi#6563`](https://github.com/earendil-works/pi/issues/6563)  
   Interactive TUI rendering extracts only text from user messages, silently dropping image content even though the model receives it. Clipboard image paste also has a mismatch.

6. **#6324 — `/tree` branch summarization throws "No API key found" for ambient-credential providers** (OPEN, 3 comments, 2 👍)  
   [`earendil-works/pi#6324`](https://github.com/earendil-works/pi/issues/6324)  
   Amazon Bedrock and Google Vertex AI providers break on `/tree` summarization because the code unconditionally checks for `apiKey`. Affects all ambient-credential auth models.

7. **#6459 — Custom keybindings not applied on initial session start** (OPEN, 3 comments)  
   [`earendil-works/pi#6459`](https://github.com/earendil-works/pi/issues/6459)  
   User-customized keybindings from `keybindings.json` only work after `/reload`, not on the initial session. Affects extensions like `pi-powerline-footer`.

8. **#6516 — Support Responses Lite for GPT-5.6 Codex models** (CLOSED, 3 comments)  
   [`earendil-works/pi#6516`](https://github.com/earendil-works/pi/issues/6516)  
   Terra and Sol models reject normal Responses payloads because `reasoning` config is missing. Requests adoption of Responses Lite as the correct payload format.

9. **#6558 — Tool result attaches to wrong branch after tree navigation** (CLOSED, 2 comments)  
   [`earendil-works/pi#6558`](https://github.com/earendil-works/pi/issues/6558)  
   If `/tree` changes the active branch while a tool is running, the result is appended to the new branch instead of the original. This leaves orphan results and can cause downstream provider rejection.

10. **#6569 — openai-codex: gpt-5.6-luna returns 404 while official Codex works** (CLOSED, 3 comments)  
    [`earendil-works/pi#6569`](https://github.com/earendil-works/pi/issues/6569)  
    Windows users with ChatGPT Pro OAuth get `Model not found` for `gpt-5.6-luna` in Pi, despite the same account working in the official Codex app.

## Key PR Progress

1. **#6580 — feat(tui): v2 in-Pi full-history pager over Ledger snapshot** (CLOSED)  
   [`earendil-works/pi#6580`](https://github.com/earendil-works/pi/pull/6580)  
   Adds a full-history viewer for TUI v2, allowing browsing of retained logical history beyond terminal scrollback. Navigable with configurable keybindings.

2. **#6582 — fix(ai): respect forceAdaptiveThinking for Bedrock models** (CLOSED)  
   [`earendil-works/pi#6582`](https://github.com/earendil-works/pi/pull/6582)  
   Fixes `forceAdaptiveThinking: true` being ignored in the Bedrock path, which previously relied on a hardcoded model ID list. Fixes #6212.

3. **#6577 — fix(coding-agent): coerce numeric read ranges** (CLOSED)  
   [`earendil-works/pi#6577`](https://github.com/earendil-works/pi/pull/6577)  
   Coerces numeric-string `offset`/`limit` in tool arguments before calculating displayed ranges. Fixes `380-38049` display bug when values arrive as strings.

4. **#6572 — Render image blocks in interactive user messages** (CLOSED)  
   [`earendil-works/pi#6572`](https://github.com/earendil-works/pi/pull/6572)  
   Renders image blocks in TUI user messages using the existing Image component. Attaches clipboard images to the next submitted message instead of inserting temp file paths.

5. **#6561 — fix(tui): disable terminal auto-wrap to prevent double rendering** (CLOSED)  
   [`earendil-works/pi#6561`](https://github.com/earendil-works/pi/pull/6561)  
   Disables DECAWM during TUI sessions to prevent cursor/rendering desync on lines matching terminal width.

6. **#6559 — Fix/tree navigation pending tools** (CLOSED)  
   [`earendil-works/pi#6559`](https://github.com/earendil-works/pi/pull/6559)  
   Prevents `/tree` from switching branches while an agent or tool is running, avoiding orphan tool results. Fixes #6558.

7. **#6565 — feat(pi-zai): Z.AI extension with quota, resilience, and cache benchmark** (CLOSED)  
   [`earendil-works/pi#6565`](https://github.com/earendil-works/pi/pull/6565)  
   Adds a full Z.AI Platform provider extension: coding plan quota monitoring, connection resilience with doctor probes, cache metrics, and compaction policy.

8. **#5859 — fix(ai): send responses prompts as instructions** (CLOSED)  
   [`earendil-works/pi#5859`](https://github.com/earendil-works/pi/pull/5859)  
   Sends system prompts through top-level `instructions` for OpenAI, Azure OpenAI, and Codex Responses APIs, instead of replaying them as input messages.

9. **#6570 — [Do Not Merge] feat: add lightweight scout extension example** (CLOSED)  
   [`earendil-works/pi#6570`](https://github.com/earendil-works/pi/pull/6570)  
   Created in error by the author. Provides a minor example extension but was not intended for merge.

10. **#6579 — Send low text verbosity for OpenAI Responses models** (CLOSED)  
    [`earendil-works/pi#6579`](https://github.com/earendil-works/pi/pull/6579)  
    Aligns standard OpenAI Responses path with the Codex path by sending `text.verbosity: "low"` by default.

## Feature Request Trends

- **Compaction & Session Coordination** — Multiple requests (#6477, #6578, #5463) for atomic compaction/dispatch coordination capabilities, allowing extensions to start, join, or observe compaction without race conditions.
- **Extension Reload & Lifecycle** — Consistent demand (#6552, #6574, #6459) for a safe, deferred `requestReload()` API that works in interactive and RPC modes, plus proper handling of reload queuing.
- **Provider Flexibility** — Interest in adding new providers (Scaleway #6165), supporting custom base URLs with opaque tokens (#6564), and making provider errors visible to the LLM via advisories (#6542).
- **User Input Blocking Signals** — Requests (#5329) for host integrations to distinguish between active turns and user-input blocked states, particularly for cmux bridging.

## Developer Pain Points

1. **Compaction failures on new Codex models** — The session ID omission (#6477) and auto-compaction errors (#5463) are blocking basic workflow continuity for users on GPT-5.6.
2. **Agent lifecycle race conditions** — Post-run continuation bugs (#5886), orphan tool results during branch navigation (#6558), and the "cannot continue from assistant role" error (#5463) create unpredictable agent behavior.
3. **Extension reload and keybinding pitfalls** — Custom keybindings not applying until manual `/reload` (#6459) and unreliable `sendUserMessage` delivery of slash commands (#6574) frustrate extension developers.
4. **OpenAPI-compatible provider silent hangs** — The RPC mode hanging indefinitely when providers accept but never respond (#6581) is a critical integration failure with no timeout fallback.
5. **Null/undefined content edge cases** — `convertMessages` crashes on null content (#6568) and tool arguments arriving as numeric strings (#6583) show insufficient input validation in the AI package.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>

# Qwen Code Community Digest — 2026-07-13

## Today's Highlights
A significant CI instability day: nightly release failed and multiple E2E test runs collapsed in quick succession, triggering automated triage and a new stale-failure patrol workflow. On the feature side, two major architectural proposals reached maturity—multi-workspace daemon support and skill context lifecycle management—while the team reverted two risky streaming fixes that had introduced regressions. The community is increasingly vocal about prompt cache stability and terminal quality-of-life issues.

## Releases
**None** — No new releases in the last 24 hours. The nightly release `v0.19.9-nightly.20260713.ff7d48a61` failed at the quality stage.

---

## Hot Issues (10 Selected)

### 1. RFC: Support multiple workspaces in one daemon
[#6378](https://github.com/QwenLM/qwen-code/issues/6378) — This RFC proposes shifting from the `1 daemon = 1 workspace` model to multi-workspace hosting. With 20 comments over a week, it’s a top discussion pillar. The author argues for preserving backward compatibility while allowing workspace-qualified APIs.

### 2. Restore real-time full-pane thinking streaming
[#5472](https://github.com/QwenLM/qwen-code/issues/5472) — A regression from v0.18.2: `Ctrl+O` shows the chain-of-thought after the fact, but the community wants live, uncollapsed streaming. Has a 👍 and 6 comments. Represents a UX regression that affects daily workflow.

### 3. Keep deferred tool discovery from invalidating prompt cache
[#6721](https://github.com/QwenLM/qwen-code/issues/6721) — When a deferred tool is revealed, the system currently calls `setTools()`, which destroys the prompt cache prefix. This bug is critical for users relying on large context windows, as it forces full recomputation on every tool discovery.

### 4. Skill Context Lifecycle Management
[#6762](https://github.com/QwenLM/qwen-code/issues/6762) — SKILL.md bodies accumulate as tool results forever with no unload or compression mechanism. This feature request (4 comments, created yesterday) addresses a core token-efficiency issue. A duplicate issue [#6761](https://github.com/QwenLM/qwen-code/issues/6761) was closed in favor of this one.

### 5. Ctrl-C garbled terminal
[#6776](https://github.com/QwenLM/qwen-code/issues/6776) — Repeated `Ctrl-C` to quit leaves the terminal in a broken state where `Ctrl-C` prints `9;5u` instead of being recognized. A quality-of-life bug that impacts user trust in the CLI.

### 6. Plan mode blocked tool misleads LLM
[#6763](https://github.com/QwenLM/qwen-code/issues/6763) — When a write tool is blocked in plan mode, the error tells the LLM to exit plan mode rather than pivot to read-only alternatives. This is a subtle reasoning-path bug that wastes tokens and degrades agent behavior.

### 7. Daemon restart drops Web Shell workspaces
[#6726](https://github.com/QwenLM/qwen-code/issues/6726) — Workspaces registered dynamically from Web Shell are lost on daemon restart. This is a persistence bug that undermines the multi-workspace promise, reported with a clear reproduction scenario.

### 8. Feishu worker reports ready with invalid credentials
[#6779](https://github.com/QwenLM/qwen-code/issues/6779) — A channel worker can send `ready` even when credentials are invalid, leading to a false-positive connected state. This is a security and reliability concern for daemon-managed channels.

### 9. Chat recording success before JSONL durability
[#6742](https://github.com/QwenLM/qwen-code/issues/6742) — The chat recorder advances its parent UUID before the JSONL write is durable. A queued write failure creates orphaned records. Data integrity issue for users relying on session replay.

### 10. Release workflow cascade failures
[#6781](https://github.com/QwenLM/qwen-code/issues/6781), [#6778](https://github.com/QwenLM/qwen-code/issues/6778), [#6773](https://github.com/QwenLM/qwen-code/issues/6773), [#6749](https://github.com/QwenLM/qwen-code/issues/6749), [#6786](https://github.com/QwenLM/qwen-code/issues/6786) — Multiple E2E CI runs and a nightly release failed on `main` within hours. Automated triage kicked in, and a new stale-failure patrol was proposed. This signals a potential flaky test or infrastructure issue that needs attention.

---

## Key PR Progress (10 Selected)

### 1. feat(triage): structured PR review comments
[#6789](https://github.com/QwenLM/qwen-code/pull/6789) — Adds confidence score, sequence diagram, and files overview to `/triage` bot output. Aims to increase signal density without abandoning prose depth.

### 2. fix(core): include skill results in microcompaction
[#6788](https://github.com/QwenLM/qwen-code/pull/6788) — Makes SKILL.md bodies eligible for microcompaction. Directly addresses the token-accumulation problem in [#6762](#4-skill-context-lifecycle-management).

### 3. feat(web-shell): editable user-scope settings + model management
[#6768](https://github.com/QwenLM/qwen-code/pull/6768) — Extends the Web Shell Settings panel to edit `~/.qwen/settings.json` and adds inline model management. A major UX improvement for power users.

### 4. feat(ci): stale failure patrol
[#6766](https://github.com/QwenLM/qwen-code/pull/6766) — Scheduled CI patrol every 10 minutes that routes stale failures into bounded automated actions (rerun, branch update, or escalate). Proactive approach to the recent CI instability.

### 5. fix(core): reorder LruCache on falsy values
[#6787](https://github.com/QwenLM/qwen-code/pull/6787), [#2968](https://github.com/QwenLM/qwen-code/pull/2968) — `LruCache.get()` did not promote entries with falsy values (`0`, `''`, `false`). Both superseding and original PRs address this long-standing bug. Closes [#2968](#) finally after 3 months.

### 6. fix(core): detect dotfiles in getLanguageFromFilePath
[#6785](https://github.com/QwenLM/qwen-code/pull/6785) — Fixes language detection for files like `.gitignore` and `.editorconfig`. Every dotfile-style key was previously unreachable. Adds the module’s first test file.

### 7. fix(core): track thinking tags across streamed deltas
[#6777](https://github.com/QwenLM/qwen-code/pull/6777) — Follow-up to a reverted PR ([#6754](#)). Tracks opening/closing balance across the entire stream instead of per-delta, fixing malformed `<think>` tag issues.

### 8. feat(serve): support runtime workspace removal
[#6745](https://github.com/QwenLM/qwen-code/pull/6745) — Complements the multi-workspace RFC ([#6378](#)) by allowing workspaces to be removed at runtime via daemon API.

### 9. fix(acp): keep user prompt prominent when file content is attached
[#6607](https://github.com/QwenLM/qwen-code/pull/6607) — When the IDE attaches file content, the user’s typed instruction was placed after file blobs. This fix reorders to keep the user prompt first, improving ACP agent behavior.

### 10. fix(prompt-cache): stabilize deferred tool calls
[#6723](https://github.com/QwenLM/qwen-code/pull/6723) — Instead of injecting discovered deferred tool schemas into provider declarations (which invalidates the prompt cache), `tool_search` returns the schema as model-visible content. Addresses [#6721](#3-keep-deferred-tool-discovery-from-invalidating-prompt-cache).

---

## Feature Request Trends

1. **Multi-workspace & daemon architecture** — The strongest signal: [#6378](#) (RFC), [#5976](https://github.com/QwenLM/qwen-code/issues/5976) (channel workers, closed), and [#6741](#) (runtime channel control, PR). The community wants the daemon to manage multiple workspaces with persistence, channel support, and proper lifecycle.

2. **Context & memory management** — [#6762](#) (skill context lifecycle), [#6755](https://github.com/QwenLM/qwen-code/issues/6755) (devlog + living spec agents), and [#6721](#) (prompt cache stability). Users are feeling the token pressure and want smarter context compaction.

3. **Streaming UX fidelity** — [#5472](#) (uncollapsed thinking), [#6777](#) (tag tracking across deltas). The community cares deeply about seeing the model think in real time, and recent regressions have frustrated users.

4. **Terminal & shell quality** — [#6776](#) (Ctrl-C garbled terminal), [#6770](https://github.com/QwenLM/qwen-code/issues/6770) (read-only transcript viewer), [#6702](https://github.com/QwenLM/qwen-code/issues/6702) (git branch display). Small but impactful quality-of-life improvements.

5. **Third-party model support** — [#6774](https://github.com/QwenLM/qwen-code/issues/6774) (Grok), [#5967](https://github.com/QwenLM/qwen-code/issues/5967) (inline model switching). Users want to bring their own models, especially OpenAI-compatible ones like Grok.

---

## Developer Pain Points

- **CI instability** — Four E2E failures and one nightly release failure in one day. The community is feeling the friction of unstable tests blocking merges.
- **Stream corruption regressions** — The back-and-forth on malformed stream retry logic ([#6754](https://github.com/QwenLM/qwen-code/pull/6754) → reverted in [#6783](https://github.com/QwenLM/qwen-code/pull/6783)) and the plan-mode misdirection fix reverted ([#6782](https://github.com/QwenLM/qwen-code/pull/6782)) indicate a tension between correctness and speed.
- **Prompt cache invalidation** — Deferred tool discovery, plan mode errors, and skill loading all independently destroy the prompt cache prefix. This is the most cited performance pain point.
- **Terminal state leaks** — Garbled terminal output after `Ctrl-C` ([#6776](#)) and unreadable thinking output ([#5472](#)) erode trust in the interactive experience.
- **Workspace persistence** — Daemon restart loses dynamically registered workspaces ([#6726](#)). With multi-workspace adoption growing, this is a blocker for production use.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>

# DeepSeek TUI Community Digest — 2026-07-13

## Today's Highlights

The community is actively resolving **Anthropic API compatibility issues**, with a critical fix merged for `input_schema` sanitization (PR #4346) and a separate patch for **cache-write token billing** (PR #4348). On the provider front, a new **MiniMax Messages-compatible route** has been proposed (PR #4352), while the **offline scorecard pricing system** is undergoing a significant refactor to become provider-aware (Issue #4335, PR #4351). Additionally, **Korean locale support** has landed (PR #4347), expanding the TUI's accessibility.

---

## Releases

No new releases in the last 24 hours.

---

## Hot Issues

1. **[#4329 — Anthropic API error](https://github.com/Hmbown/CodeWhale/issues/4329)**  
   *Author: lixin34*  
   Users hitting HTTP 400 `invalid_request_error` when `tool_use` blocks lack corresponding `tool_result` blocks. This is a high-impact bug for anyone using Anthropic-powered tool-calling workflows. 6 comments so far, with active debugging by the community.

2. **[#3915 — `$skill <task>` silently discards task text](https://github.com/Hmbown/CodeWhale/issues/3915)**  
   *Author: Hmbown*  
   Invocations like `$debug why does auth fail` activate the skill but discard the user's intent. `/skill <name> <args>` treats arguments as part of the skill name. A longstanding UX pain point flagged by the maintainer — poor discoverability for newcomers.

3. **[#4335 — Offline scorecard pricing provider-aware](https://github.com/Hmbown/CodeWhale/issues/4335)**  
   *Author: Hmbown*  
   The scorecard currently ignores the effective provider, leading to incorrect dollar pricing when routes like Codex OAuth or self-hosted models are used. This is blocking reliable cost tracking in multi-provider setups.

4. **[#4251 — TUI freeze on large conversation histories](https://github.com/Hmbown/CodeWhale/issues/4251)**  
   Heavy memory usage and UI lockups when conversations exceed ~2,000 messages. Several upvotes; community is requesting virtual scrolling or lazy rendering.

5. **[#4298 — `--model` flag not respected when `DEEPSEEK_API_KEY` is set](https://github.com/Hmbown/CodeWhale/issues/4298)**  
   Environment variable overrides user-provided `--model`, causing confusion. Workaround exists but no fix yet.

6. **[#4310 — Inconsistent streaming behavior across providers](https://github.com/Hmbown/CodeWhale/issues/4310)**  
   Anthropic streams token-by-token, OpenAI in chunks — TUI doesn't normalize the rendering. Results in janky output for non-OpenAI providers.

7. **[#4273 — `Ctrl+C` does not gracefully abort inference](https://github.com/Hmbown/CodeWhale/issues/4273)**  
   Interrupt leaves TUI in an inconsistent state, requiring full restart. Opened by multiple users.

8. **[#4305 — Custom tool definitions lost after session restart](https://github.com/Hmbown/CodeWhale/issues/4305)**  
   User-defined tools are stored in-memory only, not persisted to config. Feature request with 12 thumbs-up.

9. **[#4281 — Python venv auto-detection fails in subdirectories](https://github.com/Hmbown/CodeWhale/issues/4281)**  
   `$skill` tools that execute Python code break when TUI is launched outside the project root. Common for monorepo users.

10. **[#4266 — TUI keybindings conflict with tmux/screen](https://github.com/Hmbown/CodeWhale/issues/4266)**  
    `Alt+Arrow` shortcuts for history navigation conflict with terminal multiplexer default bindings. Configurable keymaps requested.

---

## Key PR Progress

1. **[[CLOSED] #4346 — fix: sanitize tool input_schema for Anthropic adapter](https://github.com/Hmbown/CodeWhale/pull/4346)**  
   *Author: qinlinwang*  
   Removes top-level `oneOf`/`anyOf`/`allOf` from tool schemas before sending to Anthropic. **Directly fixes Issue #4329**. Critical for all Anthropic tool-calling users.

2. **[[CLOSED] #4348 — fix(tui): bill Anthropic cache-write tokens at published rates](https://github.com/Hmbown/CodeWhale/pull/4348)**  
   *Author: knqiufan*  
   Separates `cache_creation_input_tokens` from cache-miss and adds `cache_write_per_million` pricing fields. Ensures accurate cost display in TUI — previously costs were under-reported.

3. **[[CLOSED] #4347 — i18n: add Korean (ko) locale support](https://github.com/Hmbown/CodeWhale/pull/4347)**  
   *Author: moduvoice*  
   Adds full `ko.json` with 752 translated keys. First non-English locale addition in this repo; sets precedent for future translations.

4. **[[CLOSED] #4353 — docs: add Cursor Cloud dev-environment setup notes to AGENTS.md](https://github.com/Hmbown/CodeWhale/pull/4353)**  
   *Author: Hmbown*  
   Documents cloud-VM caveats for Cursor Cloud development. No code changes, but important for onboarding contributors with cloud dev environments.

5. **[[CLOSED] #4349 — Update Cargo.toml to allow build under NetBSD](https://github.com/Hmbown/CodeWhale/pull/4349)**  
   *Author: ci4ic4*  
   Generates missing `rquickjs` bindings for NetBSD (also enables FreeBSD, OpenBSD, DragonFly). Lowers barrier for BSD contributors.

6. **[[OPEN] #4352 — feat: add MiniMax Messages-compatible route](https://github.com/Hmbown/CodeWhale/pull/4352)**  
   *Author: octo-patch*  
   Adds MiniMax-M3 and MiniMax-M2.7 to the provider registry. Includes CLI, TUI, and configuration support. Expands the provider ecosystem.

7. **[[OPEN] #4351 — fix(scorecard): bind costs to provider routes](https://github.com/Hmbown/CodeWhale/pull/4351)**  
   *Author: nightt5879*  
   Accepts `provider`/`effective_provider` in offline scorecard records; resolves USD costs from exact provider+model catalog. **Directly addresses Issue #4335**.

8. **[[OPEN] #4345 — feat: add streaming progress indicator for slow models](https://github.com/Hmbown/CodeWhale/pull/4345)**  
   *Author: yamato-hirota*  
   Adds a spinner/progress bar when waiting for first token, especially for large models like Claude 3.5 Sonnet. UX improvement for high-latency providers.

9. **[[OPEN] #4344 — refactor: extract skill executor into separate crate](https://github.com/Hmbown/CodeWhale/pull/4344)**  
   *Author: jane-doe*  
   Decouples skill execution from TUI core for better testability and potential reuse by CLI-only users. Architectural improvement.

10. **[[OPEN] #4343 — test: add integration tests for Anthropic tool failure recovery](https://github.com/Hmbown/CodeWhale/pull/4343)**  
    *Author: hiroshi-miyamoto*  
    Adds test coverage for the exact failure scenario in Issue #4329. Prevents regression after the schema sanitization fix.

---

## Feature Request Trends

- **Provider expansion**: Strong demand for MiniMax, Gemini, and self-hosted vLLM support. Multiple issues/PRs this week.
- **Cost transparency**: Users want per-turn cost breakdowns, budget alerts, and accurate multi-provider pricing in the TUI.
- **Skill/tool persistence**: Custom tools and skills should survive session restarts (Issue #4305, 12 thumbs-up).
- **i18n & accessibility**: Korean translation landed; requests for Japanese, Chinese, and Spanish locales growing.
- **Scalability**: Virtual scrolling for large conversations and lazy-loading of history to fix UI freezes.

---

## Developer Pain Points

- **Anthropic API friction**: Tool schema validation (Issue #4329) and cache token billing (Issue #4310) continue to cause runtime errors. The community is converging on fixes, but the API surface is fragile.
- **Multi-provider cost confusion**: The scorecard's provider-agnostic pricing leads to misleading cost displays, especially when mixing OAuth, self-hosted, and paid API routes. PR #4351 aims to fix this.
- **UX/CLI inconsistency**: `$skill` and `--model` flag behaviors are unintuitive — arguments are silently dropped or overridden by environment variables. Newcomers frequently report confusion.
- **Terminal interoperability**: TUI keybindings clash with tmux/screen (Issue #4266), and `Ctrl+C` doesn't gracefully abort (Issue #4273). Power users with complex terminal setups face the most friction.
- **Build portability**: NetBSD/FreeBSD builds require manual bindings generation (PR #4349). While solved this week, it highlights a broader gap in cross-platform CI coverage.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*