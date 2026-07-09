# AI CLI Tools Community Digest 2026-07-09

> Generated: 2026-07-09 02:01 UTC | Tools covered: 9

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
**Date: July 9, 2026**

---

## 1. Ecosystem Overview

The AI CLI development tools landscape is experiencing a clear maturity inflection point, characterized by three dominant themes: **cost governance** (token consumption management), **agent reliability** (loop detection, state persistence), and **platform extensibility** (MCP, plugins, custom providers). Claude Code and OpenAI Codex remain the most mature and contested leaders, with Claude Code driving hierarchical agent architectures and Codex wrestling with a critical GPT-5.5 tool-calling regression. Gemini CLI and Copilot CLI occupy a solid mid-tier, focused on subagent reliability fixes and enterprise authentication flows respectively. The Korean/TUI-native tools—Qwen Code, DeepSeek TUI (CodeWhale), and Pi—show remarkable iteration velocity, with CodeWhale merging 10+ PRs daily in its v0.8.68 milestone sprint. Kimi Code remains the outlier with negligible activity, suggesting either stagnation or a strategic pivot. The ecosystem-wide signal is clear: **agent cost and trust are the new battlegrounds**, surpassing raw capability as the primary differentiator.

---

## 2. Activity Comparison

| Tool | Open Issues (Hot) | PRs (24h/Active) | Release Today | Key Velocity Signal |
|------|-------------------|-------------------|---------------|---------------------|
| **Claude Code** | ~10 active hot issues | 7 key PRs tracked | ✅ v2.1.205 | High community engagement (80+ combined comments on top issues); agent orchestration megathreads dominate |
| **OpenAI Codex** | ~10 active hot issues | 10 key PRs tracked | ✅ 2 alpha SDK releases (Rust) | Systematic HTTP client migration; GPT-5.5 regression creating urgent noise |
| **Gemini CLI** | 10 hot issues | 10 key PRs tracked | ✅ v0.50.0 stable + v0.51.0-preview.0 | Security-critical RCE fix underway; subagent reliability is the dominant theme |
| **Copilot CLI** | 10 hot issues | 2 PRs (low activity) | ❌ No release | Stalled velocity; community focused on long-standing bugs (#3158 infinite loop) |
| **Kimi Code** | 1 single issue | 0 PRs | ❌ No release | **Negligible activity** – potential abandonment signal |
| **OpenCode** | 10 hot issues | 10 key PRs tracked | ❌ No release (v1.17.14 latest) | 8 bug-fix PRs from single contributor (HOYALIM); high CPU regression concern |
| **Pi** | 10 hot issues | 7 PRs merged | ❌ No release (v0.80.3 latest) | High closure rate (18 issues, 6 PRs merged); compaction bugs are acute |
| **Qwen Code** | 10 hot issues | 10 PRs tracked | ✅ v0.19.8 | Rapid iteration; multi-workspace daemon RFC under active debate |
| **DeepSeek TUI (CodeWhale)** | 10 hot issues | 10+ PRs merged | ❌ No release (v0.8.68 milestone) | **Highest velocity** – 10+ PRs/day; systematic milestone execution |

---

## 3. Shared Feature Directions

The following requirements appear across **three or more** tool communities, indicating strong ecosystem convergence:

### Agent Cost Governance & Transparency
| Theme | Affected Tools | Specific Requests |
|------|----------------|-------------------|
| Token consumption visibility | **Claude Code**, **OpenCode**, **Pi**, **Gemini CLI** | Real-time token burn rate, per-model cost breakdown, TPS display |
| Spending caps & controls | **Claude Code**, **Copilot CLI**, **OpenCode** | Configurable quotas, parallelization limits, auto-shutdown on budget exhaustion |
| Prompt cache observability | **Pi**, **OpenCode** | Cache hit/miss tracking, cache miss warnings per turn |

### Agent Reliability & State Management
| Theme | Affected Tools | Specific Requests |
|------|----------------|-------------------|
| Loop/circuit breaker detection | **Claude Code**, **OpenCode**, **Gemini CLI**, **Pi** | Infinite loop prevention in sub-agents; Cap recursive reasoning turns |
| Session lifecycle management | **Claude Code**, **Copilot CLI**, **OpenCode**, **Pi** | Session delete, resume, fork, archive; configurable data retention |
| Sub-agent state persistence | **Claude Code**, **OpenCode**, **Pi** | Persistent state across sessions; sub-agent checkpoint/resume |

### MCP & Plugin Ecosystem Expansion
| Theme | Affected Tools | Specific Requests |
|------|----------------|-------------------|
| MCP client capabilities | **OpenCode**, **Gemini CLI** | Full spec compliance (streaming, sampling), SSRF protection |
| Custom slash commands | **Copilot CLI**, **Claude Code** | Extensible prompt files (`.github/prompts/`) |
| Plugin system hooks | **Pi**, **Claude Code** | `session_before_load` hooks, lifecycle event plugins |

### Model & Provider Flexibility
| Theme | Affected Tools | Specific Requests |
|------|----------------|-------------------|
| Model family aliasing | **Copilot CLI**, **Pi** | Specify `opus`, `sonnet` instead of exact version strings |
| Multi-provider routing | **DeepSeek TUI**, **Copilot CLI** | Per-agent provider assignment; BYOK support |
| Custom CA/SSL handling | **Kimi Code**, **Qwen Code** | Enterprise proxy compatibility; NO_PROXY support |

### Platform Parity (Windows / Linux)
| Theme | Affected Tools | Specific Requests |
|------|----------------|-------------------|
| Windows ecosystem gaps | **Claude Code**, **OpenAI Codex** | Cowork unavailable, sandbox fragility, HCS services missing |
| Linux clipboard/terminals | **OpenCode**, **Pi** | `xclip`/`wl-clipboard` preinstalled, CJK rendering fixes |

---

## 4. Differentiation Analysis

| Tool | Primary Differentiator | Target User | Technical Approach | Weakness |
|------|------------------------|-------------|-------------------|----------|
| **Claude Code** | Hierarchical agent teams (Opus orchestrator + Sonnet workers) | Power developers, multi-agent orchestration | Configurable `Task`/`Agent` primitives; session persistence | Runaway token consumption eroding cost trust |
| **OpenAI Codex** | Tight GPT integration; Rust SDK alpha | Enterprise, Python/JS developers | HTTP client factory pattern; distributed tracing | GPT-5.5 tool-calling regressions damaging reliability |
| **Gemini CLI** | Tool Registry feature; MCP security focus | Google Cloud ecosystem, enterprise | A2A server; Cedar-based policy enforcement | Subagent reliability is weakest across all tools |
| **Copilot CLI** | GitHub ecosystem integration; BYOK model support | GitHub-centric developers, corporate | C# runtime; `--acp` multi-provider mode | Stalled iteration; infinite re-plan loop (#3158) undermines agent trust |
| **Kimi Code** | Moonshot AI ecosystem | Chinese market (speculative) | Unknown | **Near-zero community activity** – likely abandoned |
| **OpenCode** | Go-based plan/usage APIs; MCP client spec compliance | Go developers, cloud engineers | `models.dev` catalog integration; AI SDK providers | High CPU regression; subagent hang/loop fragility |
| **Pi** | Session format as platform (v3 JSONL); Bun runtime | Experimental devs, agent session explorers | In-memory session storage; compaction state management | Compaction edge cases making long sessions unrecoverable |
| **Qwen Code** | Multi-workspace daemon; QQ/WeCom channel integration | Chinese market, enterprise ops | V2 daemon architecture; channel adapters | CI/CD reliability (3 release failures this week); Windows gaps |
| **DeepSeek TUI** | **Highest iteration velocity** (10+ PRs/day); TUI-first | TUI power users, Ratatui/crossterm developers | Sub-agent sandboxing by environment; Fleet profile system | Project velocity overwhelms contributors; rendering QA still open |

**Key Insight**: The market is bifurcating between **platform tools** (Claude Code, Codex, Gemini) that prioritize agent orchestration and enterprise security, and **niche-performer tools** (CodeWhale, Pi, Qwen Code) that prioritize iteration speed and specific platform advantages (TUI, Chinese channels, Go ecosystem). Kimi Code and Copilot CLI risk being left behind due to velocity gaps.

---

## 5. Community Momentum & Maturity

### High Momentum (Rapid Iteration, Growing User Base)
| Tool | Signal | Evidence |
|------|--------|----------|
| **DeepSeek TUI (CodeWhale)** | **Highest velocity** | 10+ PRs/day; systematic v0.8.68 milestone execution with dedicated lanes; 4+ contributors actively shipping |
| **OpenCode** | Sustained bug-fix throughput | 8 PRs from HOYALIM in one batch; MCP capability issue at 25 👍 shows engaged user base |
| **Pi** | High issue closure rate | 18 issues closed, 6 PRs merged in 24h; responsive maintainer (@mitsuhiko active) |
| **Qwen Code** | Feature velocity | 10+ PRs open simultaneously; multi-workspace RFC under active debate (19 comments) |

### Steady Maturity (Stable, Large User Base)
| Tool | Signal | Evidence |
|------|--------|----------|
| **Claude Code** | Highest community engagement | #56913 agent orchestration (43 comments), #42249 token consumption (39 comments); 80+ combined comments across top issues |
| **OpenAI Codex** | Systematic infrastructure migration | HTTP client factory pattern (multiple PRs); Rust SDK alpha releases; deep enterprise focus |
| **Gemini CLI** | Security-first maturity | RCE vulnerability fix (#28319); SSRF protection (#28112); clear P1/P2 issue triage system |

### Stagnation Risk
| Tool | Signal | Evidence |
|------|--------|----------|
| **Copilot CLI** | Low PR velocity | Only 2 PRs in 24h, both minimal; critical infinite loop bug (#3158) unresolved; no release this week |
| **Kimi Code** | **Near-zero activity** | 1 open issue, 0 PRs, no release; likely project abandonment or strategic siloing |

### Community Health Metrics
| Metric | Claude Code | Codex | Gemini | Copilot | Kimi | OpenCode | Pi | Qwen | CodeWhale |
|--------|-------------|-------|--------|---------|------|----------|-----|------|-----------|
| Hot Issues with 10+ comments | 5 | 4 | 4 | 2 | 0 | 4 | 4 | 3 | 6 |
| Peak issue engagement | 43 comments | 40 comments | 10 comments | 32 comments | 2 comments | 23 comments | 4 comments | 19 comments | 51 comments |
| Top-voted feature (👍) | 51 (#26904) | 150 (#2153) | 8 (#21409) | 99 (#618) | 0 | 96 (#16017) | 6 (#5263) | N/A | N/A |
| New contributors (24h) | 1+ | 2+ | 3+ | 0 | 0 | 1+ | 2+ | 1+ | 4+ |

---

## 6. Trend Signals

### 1. Agent Cost Is the New Differentiator
The single loudest signal across the ecosystem is **runaway token consumption eroding user trust**. Claude Code (#42249, #55053, #67506), OpenCode (#31942, #33028), Gemini CLI (#26522), and Pi (#6429) all report users burning through quotas 5–10× faster than expected. The community response is converging: circuit breakers, loop detection, configurable caps, and per-turn cost transparency. **Tools that solve cost governance first will win enterprise adoption.**

### 2. Sub-Agent Reliability Is the Hardest Unsolved Problem
Every tool with sub-agent capabilities—Claude Code (#72080, #67636), Gemini CLI (#22323, #21409), OpenCode (#35952, #31942), Qwen Code (#6505)—reports identical failure patterns: sub-agents entering infinite loops, falsely reporting success after hitting limits, and lacking kill switches. The **hierarchical agent architecture is aspirational but not yet production-reliable**. Circuit breakers and trajectory observability are the most demanded fixes.

### 3. Platform Extensibility Is the New Baseline
The ecosystem is converging on a **plugin/MCP-first architecture**: Claude Code (protect-mcp plugin, hooks), OpenCode (MCP client capabilities), Gemini CLI (Tool Registry, SSRF protection), Copilot CLI (custom slash commands), Pi (session hooks). MCP compliance is no longer optional—it's the integration standard. Tools without MCP support (Kimi Code) or with incomplete MCP (OpenCode) are facing community pressure.

### 4. TUI-First Tools Are Driving UX Innovation
CodeWhale and Pi demonstrate that **TUI-first design enables rapid iteration** unmatched by CLI/IDE hybrids. CodeWhale's 10+ PRs/day velocity and Pi's compaction state management show that focused TUI tools can outpace generalist platforms in specific domains. The convergence of CodeWhale and OpenCode around `models.dev` catalog integration signals a potential **ecosystem standard for model metadata**.

### 5. Enterprise Adoption Hinges on Security & Proxy
The RCE vulnerability in Gemini CLI (#28319), SSL issues in Kimi Code (#2458), SSRF gaps in OpenAI Codex (#31361, #31363), and OAuth fragility in Copilot CLI (#4016, #2112) all point to the same truth: **enterprise infra compatibility is the gatekeeper for CLIs in corporate environments**. NO_PROXY support, custom CA certificates, and managed proxy routing are becoming table stakes.

### 6. Windows Remains a Second-Class Platform
Despite significant Windows user bases, Claude Code (#74649), OpenAI Codex (#29072), and Qwen Code (#6334) all report distinctive Windows-only blockers (HCS services, sandbox executable location, stale temp directories). **No tool has achieved Windows parity**, creating an opportunity for the tool that invests in cross-platform reliability.

### Reference Value for Developers

- **If you need agent orchestration**: Claude Code is the most mature, but budget for token costs. Monitor #56913 for hierarchical agent progress.
- **If you need enterprise security**: Gemini CLI (Cedar policies, MCP SSRF, RCE fix) and OpenAI Codex (HTTP client factory, signed receipts) are leading. Watch for Copilot CLI BYOK stability.
- **If you need TUI performance**: CodeWhale (10+ PRs/day) and Pi (session format innovation) are the fastest-moving. Expect rapid improvements in sub-agent tool scoping.
- **If you need cost control**: No tool has solved this yet. OpenCode's Go plan APIs (#16017) and Pi's prompt cache tracking (#6427) are early signals. Avoid deep investment in any tool until cost transparency improves.
- **If you need Chinese ecosystem integration**: Qwen Code (WeCom channels, QQ Bot) and CodeWhale (hot reloads, Android/Termux) are building for those markets. Kimi Code is currently dormant.
- **If you need stable x-platform support**: OpenAI Codex has the most systematic migration to proxy compliance. Copilot CLI is the most GitHub-native but risks stagnation.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)

# Claude Code Skills Community Highlights Report
**Data as of 2026-07-09** | Source: [github.com/anthropics/skills](https://github.com/anthropics/skills)

---

## 1. Top Skills Ranking

The following pull requests represent the most-discussed Skill submissions, ranked by community attention (comments + cross-referenced Issues).

### #1: `skill-creator` Fix — run_eval.py Recall Failure
**PR [#1298](https://github.com/anthropics/skills/pull/1298)** | Author: MartinCajiao | Status: **Open (2026-06-10)**

A comprehensive fix for `run_eval.py`'s systemic 0% recall bug affecting `run_loop.py` and `improve_description.py`. The root cause: the eval artifact was not installed as a real skill, combined with Windows stream-reading incompatibilities and parallel worker detection issues. This PR consolidates fixes across 10+ independent reproductions (linked to Issue #556). The description-optimization loop has been optimizing against noise, making this the single most impactful fix for skill authors.

### #2: `document-typography` — Typographic Quality Control
**PR [#514](https://github.com/anthropics/skills/pull/514)** | Author: PGTBoos | Status: **Open (2026-03-04)**

A dedicated skill for preventing orphan word wraps (1–6 words spilling to next line), widow paragraph headers stranded at page bottom, and numbering misalignment in AI-generated documents. Discussion highlights that these issues affect nearly every generated document and users rarely request fixes explicitly—making this an ideal "silent quality" skill.

### #3: `self-audit` — Mechanical Verification + Reasoning Quality Gate
**PR [#1367](https://github.com/anthropics/skills/pull/1367)** | Author: YuhaoLin2005 | Status: **Open (2026-06-28)**

A universal skill that audits AI output before delivery: mechanical file verification (Step 0) followed by a four-dimension reasoning audit in damage-severity priority order. Designed to work with any project, tech stack, or model. The community is actively discussing the trade-offs of pre-delivery auditing vs. post-hoc correction.

### #4: `testing-patterns` — Full-Stack Testing Coverage
**PR [#723](https://github.com/anthropics/skills/pull/723)** | Author: 4444J99 | Status: **Open (2026-03-22)**

Covers the Testing Trophy model, unit testing (AAA pattern), React component testing, and explicit guidance on what NOT to test. The discussion focuses on balancing comprehensiveness with token efficiency in the skill definition.

### #5: `odt` — OpenDocument Text Creation & Template Filling
**PR [#486](https://github.com/anthropics/skills/pull/486)** | Author: GitHubNewbie0 | Status: **Open (2026-03-01)**

Adds support for creating, filling, reading, and converting `.odt` and `.ods` files—targeting LibreOffice and ISO-standard document workflows. Includes ODT-to-HTML conversion. The discussion reflects strong demand from European government and education sectors where ODF is mandatory.

### #6: `frontend-design` Improvement
**PR [#210](https://github.com/anthropics/skills/pull/210)** | Author: justinwetch | Status: **Open (2026-01-05)**

Revises the frontend-design skill for clarity, actionability, and internal coherence. Every instruction must be something Claude can execute within a single conversation. Discussion centered on reducing ambiguity in visual design heuristics.

### #7: `color-expert` — Comprehensive Color Knowledge
**PR [#1302](https://github.com/anthropics/skills/pull/1302)** | Author: meodai | Status: **Open (2026-06-10)**

A self-contained color-expertise skill covering ISCC-NBS, Munsell, XKCD, RAL, Ridgway 1912, CSS named color systems, plus a "what to use when" table for color spaces (OKLCH for scales, OKLAB for gradients, CAM16 for perception). Gaining rapid community interest for design and data-visualization workflows.

---

## 2. Community Demand Trends

**Most-Anticipated New Skill Directions** (from Issues with high engagement):

| Trend | Key Issue | Demand Signal |
|-------|-----------|---------------|
| **Skill Security & Trust Boundaries** | [#492](https://github.com/anthropics/skills/issues/492) (34 comments) | Community fears impersonation attacks under `anthropic/` namespace; demands official verification badges and sandboxing |
| **Org-Wide Skill Sharing** | [#228](https://github.com/anthropics/skills/issues/228) (14 comments, 7 👍) | Enterprise teams need shared skill libraries; manual `.skill` file distribution is a blocker |
| **Skill-Creator Toolchain Reliability** | [#556](https://github.com/anthropics/skills/issues/556) (12 comments, 7 👍), [#1061](https://github.com/anthropics/skills/issues/1061), [#1169](https://github.com/anthropics/skills/issues/1169) | Windows compatibility, 0% recall bugs, and YAML parsing failures dominate author complaints |
| **Agent Governance & Safety Patterns** | [#412](https://github.com/anthropics/skills/issues/412) (6 comments) | Policy enforcement, threat detection, trust scoring, audit trails for agent systems |
| **Deduplication / Plugin Architecture** | [#189](https://github.com/anthropics/skills/issues/189) (6 comments, 9 👍) | `document-skills` and `example-skills` plugins install identical content; community wants a clean plugin model |
| **MCP Export for Skills** | [#16](https://github.com/anthropics/skills/issues/16) (4 comments) | Expose skill logic as Model Context Protocol endpoints for programmatic use |

---

## 3. High-Potential Pending Skills

These PRs have active comment threads and broad community interest but remain unmerged:

| Skill | PR | Author | Opened | Why It Matters |
|-------|----|--------|--------|----------------|
| **skill-quality-analyzer + skill-security-analyzer** | [#83](https://github.com/anthropics/skills/pull/83) | eovidiu | 2025-11-06 | Meta-skills that evaluate other skills across structure, documentation, and security dimensions |
| **SAP-RPT-1-OSS Predictor** | [#181](https://github.com/anthropics/skills/pull/181) | amitlals | 2025-12-28 | Enterprise demand: tabular foundation model for SAP business data predictive analytics |
| **Testing Patterns** | [#723](https://github.com/anthropics/skills/pull/723) | 4444J99 | 2026-03-22 | Most comprehensive testing skill proposed; covers Trophy model through React |
| **Self-Audit** | [#1367](https://github.com/anthropics/skills/pull/1367) | YuhaoLin2005 | 2026-06-28 | Universal pre-delivery quality gate; rapidly gaining discussion |
| **Compact-Memory** | [#1329](https://github.com/anthropics/skills/issues/1329) | WGlynn | 2026-06-17 | Symbolic notation for compact agent state; addresses context window pressure |

---

## 4. Skills Ecosystem Insight

**The community's most concentrated demand is for *reliable skill-authoring tooling* (Windows compatibility, trigger detection, YAML validation) and *quality/safety guardrails* (self-audit, typography, security analysis)—not flashy features, but the infrastructure to make Skills trustworthy, shareable, and correct across platforms.**

---

# Claude Code Community Digest — July 9, 2026

---

## Today's Highlights

Claude Code v2.1.205 ships with an important auto mode safety improvement that blocks tampering with session transcript files, plus fixes for `--json-schema` silently producing garbage on invalid schemas. The community remains laser-focused on runaway token consumption and agent orchestration—two long-running megathreads (#56913 on tiered autonomous agents and #42249 on extreme quota burn) continue to dominate discussion with over 80 combined comments. Agent cost governance is the defining theme of the week.

---

## Releases

**v2.1.205** — [Release Link](https://github.com/anthropics/claude-code/releases/tag/v2.1.205)

- **Auto mode guard:** Added a rule that blocks tampering with session transcript files.
- **`--json-schema` fixes:** Invalid schemas no longer silently produce unstructured output; schemas using the `format` keyword are now accepted.
- **Message delivery fix:** Resolved an issue where a message sent while Claude was working could be silently dropped.

---

## Hot Issues

1. **[#56913 — Make autonomous Claude Code actually viable: tiered Opus brains + Sonnet workers + persistent state](https://github.com/anthropics/claude-code/issues/56913)**  
   *43 comments, open since May 7.* The most active feature request on the tracker. Proposes a hierarchical agent architecture where Opus orchestrates and Sonnet sub-agents execute, with persistent state across sessions. Community strongly resonates; represents the aspirational ceiling for Claude Code as a long-running "brain."

2. **[#42249 — Extreme token consumption — quota depleted in minutes](https://github.com/anthropics/claude-code/issues/42249)**  
   *39 comments, 17 👍.* A systemic cost complaint. Users report normal development tasks (reading files, editing, git) burning through daily limits in ~1 hour. No official fix acknowledged yet; community is frustrated.

3. **[#55053 — Sudden 5-hour session window squeeze starting Apr 29](https://github.com/anthropics/claude-code/issues/55053)**  
   *37 comments, 12 👍.* Users report the session window depletes 5–10× faster than before. Sonnet sub-agents flagged as disproportionate consumers. One of several issues pointing to a regression in token accounting.

4. **[#74649 — Missing HCS services: vfpext — Cowork not working on Windows 11 Pro](https://github.com/anthropics/claude-code/issues/74649)**  
   *23 comments.* A blocker for Windows users trying to use the Cowork feature. Hyper-V Code Security services missing; affects productivity on a major platform.

5. **[#61993 — Sub-agents cannot spawn other sub-agents](https://github.com/anthropics/claude-code/issues/61993)**  
   *19 comments.* The `Task`/`Agent` primitives are not exposed in nested contexts on Windows. Limits composability of multi-agent workflows.

6. **[#67506 — Token consumption with Fable 5 not matching description](https://github.com/anthropics/claude-code/issues/67506)**  
   *16 comments, 1 👍.* Users claim the Fable 5 model burns tokens faster than documented. Another data point in the growing cost-accuracy trust gap.

7. **[#72080 — Sub-agents stuck in infinite loops consuming excessive tokens](https://github.com/anthropics/claude-code/issues/72080)**  
   *6 comments.* Main agent recovers from loops, but sub-agents now independently enter unbounded loops. Highlights weak guardrails in the agent runtime.

8. **[#67636 — Parallel agent spawning causes excessive token consumption before crashing](https://github.com/anthropics/claude-code/issues/67636)**  
   *5 comments.* Claude spawned 10–15 agents for tasks solvable by 1–2, costing "a few million tokens." Calls for parallelization limits and smarter task batching.

9. **[#75314 — 10 background Agent tasks stuck running for 34+ hours, no way to cancel](https://github.com/anthropics/claude-code/issues/75314)**  
   *3 comments.* Burned ~1M tokens with no kill switch. Exposes a critical gap in background job lifecycle management.

10. **[#26904 — Add /delete command to delete current session](https://github.com/anthropics/claude-code/issues/26904)**  
    *9 comments, 51 👍.* The most upvoted open feature request. Simple UX gap: users must manually navigate to delete a session. High demand, low implementation complexity.

---

## Key PR Progress

1. **[#75938 — fix(sweep): unstarve markStale via search API](https://github.com/anthropics/claude-code/pull/75938)**  
   Fixes the stale-issue labeling pipeline where skips permanently occupied the oldest-page slots. Ensures all eligible stale issues are eventually labeled.

2. **[#41447 — feat: open source claude code ✨](https://github.com/anthropics/claude-code/pull/41447)**  
   A long-running (since March 31) open-source-ification PR. Ties together multiple foundational issues. Still open; community eagerly watching.

3. **[#75541 — fix(sweep): paginate issue events and honor unlabeled](https://github.com/anthropics/claude-code/pull/75541)**  
   Prevents premature auto-closure of issues by properly paginating lifecycle label events. Fixes a bug where stale issues were closed without the label being applied.

4. **[#72014 — Add protect-mcp plugin: fail-closed Cedar policy gate + signed receipts](https://github.com/anthropics/claude-code/pull/72014)**  
   A security plugin that blocks policy-violating MCP tool calls before execution and emits offline-verifiable signed receipts. Significant for enterprise adoption.

5. **[#68673 — fix(scripts): break pagination when page is not full](https://github.com/anthropics/claude-code/pull/68673)**  
   Performance fix for pagination logic that was fetching unnecessary pages. Impacts script reliability at scale.

6. **[#75537 — fix(hook-development): recognize all five hook handler types](https://github.com/anthropics/claude-code/pull/75537)**  
   Documentation and validator fix: the plugin dev skill only knew 2 of 5 supported hook types. Essential for plugin authors.

7. **[#75529 — docs(code-review plugin): clarify relationship to bundled /code-review skill](https://github.com/anthropics/claude-code/pull/75529)**  
   Resolves namespace confusion between the `code-review` plugin (PR review via `gh`) and the built-in `/code-review` skill (local diff review). Adds namespace prefix to avoid collision.

---

## Feature Request Trends

- **Autonomous agent orchestration (#56913, #61993, #67636):** The community wants hierarchical agent teams—Opus for planning, Sonnet/Fable for execution—with persistent memory and cross-session state. This is the single most-discussed feature direction.
- **Conversation forking and branching (#46451):** Users want `/fork` to create divergent conversation paths without losing context, especially in VS Code.
- **Session lifecycle management (#26904, #60097):** Features like `/delete`, worktree display in the desktop UI status line, and session archiving are consistently upvoted.
- **Cost transparency and controls (#42249, #55053, #67506):** Real-time token burn rate, per-model cost breakdowns, and spending caps are implicitly requested across many bug reports.

---

## Developer Pain Points

1. **Runaway token consumption** — The dominant frustration across multiple issues. Users report quota depletion 5–10× faster than expected, sub-agents in infinite loops, parallel agent spawning without limits, and no way to cancel runaway background tasks. Trust in cost accuracy is eroding.

2. **Windows ecosystem gaps** — Cowork missing on Windows 11 (missing HCS services), cross-device rename errors with OneDrive, and IME input failures for CJK users in background session viewers. Windows remains a second-class platform.

3. **Context compression without transparency** — Long sessions silently drop old context, but the UI still shows the full history. Users are misled into thinking the model has access to past content when it does not. No warning, no opt-out.

4. **API reliability issues** — Recurring `ECONNRESET` errors, invalid UTF-8 surrogate errors during image attachment, and OAuth failures in Chrome extension. Network resilience remains a pain point.

5. **Plugin and config management bugs** — `claude plugin install --scope project` overwrites rather than merges `installed_plugins.json`. Windows drive-letter case not canonicalized, causing duplicate config entries. Minor but friction-inducing for power users.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

# OpenAI Codex Community Digest — July 9, 2026

## Today's Highlights

A **GPT-5.5 tool calling regression** in CLI 0.143.0 is generating widespread attention, with multiple reports of `unsupported call: exec_commandexec_command` errors caused by self-referential namespace bugs. On the infrastructure side, OpenAI engineers are systematically migrating HTTP clients to a shared factory pattern to ensure proxy policies apply universally. Two alpha releases of the Rust SDK (`v0.144.0-alpha.1` and `.2`) also dropped today.

---

## Releases

- **[rust-v0.144.0-alpha.1](https://github.com/openai/codex/releases/tag/rust-v0.144.0-alpha.1)** — Initial 0.144.0 alpha for the Rust SDK.
- **[rust-v0.144.0-alpha.2](https://github.com/openai/codex/releases/tag/rust-v0.144.0-alpha.2)** — Follow-up alpha release. No change notes provided.

---

## Hot Issues

1. **[#28224](https://github.com/openai/codex/issues/28224) — SQLite feedback logs write ~640 TB/year**  
   Originally flagged massive SSD wear from excessive telemetry logging. Three merged PRs reduced logs by ~85%. The issue is now closed, but the sheer scale of the original problem (640 TB/year) underscores how easily observability tooling can become a stability threat.

2. **[#31520](https://github.com/openai/codex/issues/31520) — CLI update fails: “Could not find Codex package or platform npm release assets”**  
   A blocking upgrade path for CLI users. The error message gives no remediation hint. 24 👍 indicates broad frustration. Affects users trying to update via the official `install.sh`.

3. **[#29072](https://github.com/openai/codex/issues/29072) — Windows App: `apply_patch` fails because sandbox-setup.exe cannot launch from package path**  
   40 comments, the most-engaged Windows-specific issue. The sandbox executable cannot resolve its own location when installed via the App package, breaking `apply_patch` entirely on Windows.

4. **[#31665](https://github.com/openai/codex/issues/31665) — GPT-5.5 tool calls fail with self-referential namespace**  
   Core regression: GPT-5.5 sends `exec_commandexec_command` (doubled namespace) on built-in tools. Multiple reports confirm the same pattern. CLI 0.143.0 is the trigger; earlier versions work fine.

5. **[#31611](https://github.com/openai/codex/issues/31611) — CLI 0.143.0: `unsupported call: exec_command` on Amazon Linux 2023**  
   Another tool-call regression on 0.143.0, this time on Amazon Linux. Downgrading to 0.140.0 restores functionality. Suggests a broader issue in the tool dispatch layer for this release.

6. **[#31609](https://github.com/openai/codex/issues/31609) — gpt-5.5 tool calling regression (macOS)**  
   Companion to #31665 on Darwin. Confirms the issue is cross-platform. The community reaction (3 👍 in hours) suggests many users are hitting this immediately after updating.

7. **[#31668](https://github.com/openai/codex/issues/31668) — Paid accounts: limits drain after one prompt, company credits burned in one day**  
   Systemic billing/rate-limit regression across multiple paid accounts. The reporter cites three related issues. If confirmed, this is a P0 for any organization on a usage-based plan.

8. **[#30248](https://github.com/openai/codex/issues/30248) — macOS Desktop spins at 100% CPU on launch from one active heartbeat automation RRULE**  
   A single automation recurrence rule causes permanent 100% CPU. Makes the desktop app unusable on launch. The narrow trigger makes this tricky to reproduce, but the impact is total UI freeze.

9. **[#2153](https://github.com/openai/codex/issues/2153) — ChatGPT integration (opened Aug 2025, still open)**  
   The oldest hot issue, with 150 👍 and 38 comments. Users want seamless session transfer between Codex CLI and ChatGPT web UI for brainstorming/research. No movement from OpenAI in nearly a year.

10. **[#20851](https://github.com/openai/codex/issues/20851) — First-class Computer Use in CLI**  
    Computer Use is currently desktop-only. Developers want parity in the CLI, especially for headless/CI environments. The existing implementation bundles a macOS `.app` helper, which is unusable on Linux/remote hosts.

---

## Key PR Progress

1. **[#31687](https://github.com/openai/codex/pull/31687) — exec-server: align JSON-RPC span attributes with app-server**  
   Adds `rpc.system`, `rpc.method`, and `rpc.request_id` to tracing spans. Makes cross-service debugging in distributed traces consistent.

2. **[#31683](https://github.com/openai/codex/pull/31683) — trace remote shell starts across core and exec server**  
   Closes a telemetry gap: remote exec-server shell commands now produce a unified OpenTelemetry waterfall across the local core and remote server processes. Essential for latency debugging.

3. **[#31361](https://github.com/openai/codex/pull/31361) — route model discovery through HTTP client factory**  
   Model catalog discovery previously bypassed `respect_system_proxy`. This PR ensures system proxy settings apply uniformly. Part of a larger client-factory migration.

4. **[#31652](https://github.com/openai/codex/pull/31652) — fix(tui): hide empty reasoning summaries**  
   Reasoning summaries containing `<!-- -->` were leaking into conversation history. Small UX fix, but important for cleanliness of persisted transcripts.

5. **[#31681](https://github.com/openai/codex/pull/31681) — core: move reasoning effort to step context**  
   Infrastructure change: reasoning effort now lives on per-step context rather than turn context, enabling dynamic adjustment between sampling steps.

6. **[#31644](https://github.com/openai/codex/pull/31644) — feat(linux-sandbox): route DNS through managed proxy**  
   Adds a DNS adapter inside bubblewrap namespaces so native DNS clients honor the managed proxy. Previously, DNS leaked outside the proxy scope on Linux.

7. **[#31363](https://github.com/openai/codex/pull/31363) — codex-api: route file uploads through HTTP client factory**  
   Completes proxy compliance for the three-step file upload flow (create, PUT, finalize). One fewer request path bypassing system proxy settings.

8. **[#31672](https://github.com/openai/codex/pull/31672) — Import enabled plugins from known marketplaces**  
   Enables discovery of marketplace-source plugins by reading the user-level registry. Supports file, URL, npm, and inline sources. Important for ecosystem extensibility.

9. **[#29869](https://github.com/openai/codex/pull/29869) — Preserve source chronology for imported sessions**  
   Imported sessions now retain original creation and activity timestamps. State-database rebuilds will preserve chronology. Essential for users migrating sessions between environments.

10. **[#30188](https://github.com/openai/codex/pull/30188) — feat(rollout): persist TurnItems for paginated thread rollouts**  
    New `history_mode = "paginated"` threads now save turn-level `ItemCompleted` events to JSONL. Legacy threads unchanged. Enables richer rollout analytics.

---

## Feature Request Trends

- **ChatGPT ↔ Codex session transfer** ([#2153](https://github.com/openai/codex/issues/2153), 150 👍) — The longest-standing request remains unaddressed. Users want to move conversations seamlessly between the web UI and CLI.
- **CLI-first Computer Use** ([#20851](https://github.com/openai/codex/issues/20851)) — Demand for headless browser/computer automation without requiring the desktop app.
- **Topic-based memory directories** ([#19758](https://github.com/openai/codex/issues/19758)) — Users want structured, agent-managed memory rather than a single `memory_summary.md`. Inspired by Claude Code's approach.
- **Higher session caps in VS Code** ([#15368](https://github.com/openai/codex/issues/15368)) — Power users bumping into hardcoded limits in the extension.
- **Better JetBrains feature parity** ([#22648](https://github.com/openai/codex/issues/22648)) — Missing `/plan`, `/goal`, and other CLI commands in the JetBrains extension.

---

## Developer Pain Points

- **GPT-5.5 tool-calling regressions in CLI 0.143.0** — Multiple issues (#31665, #31611, #31609, #31639) with the same root cause: self-referential namespaces on built-in tool calls. The release appears to have introduced a critical dispatch bug that affects every `exec_command`, `shell_command`, and `apply_patch` call.
- **Rate-limit / billing regressions** (#31668, #31682) — Paid accounts reporting limits consumed in a single prompt. At least three related issues filed. If systemic, this is a direct revenue-impacting bug.
- **Windows sandbox fragility** (#29072, #31511, #31549, #31564) — A cluster of Windows-specific issues: sandbox executables cannot find themselves, false "filename too long" errors, leaked helper processes, and Computer Use being entirely unavailable.
- **macOS 27 Beta incompatibility** (#31364, #31671) — The desktop app and CLI both have connectivity/submission issues on the new macOS 27 Beta 3, including failed WebSocket initiation.
- **Auto-approval policy not inherited by sub-agents** (#23324, #23664) — Sub-agents trigger approval prompts even for safe commands that the parent agent would auto-approve. Breaks automated workflows with delegated execution.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>

# Gemini CLI Community Digest — July 9, 2026

---

## 1. Today's Highlights

Two new releases landed today: **v0.50.0 stable** and **v0.51.0-preview.0**, bringing a new Tool Registry feature alongside critical CI fixes. A high-severity PR (#28319) addresses an RCE vulnerability in the A2A server by enforcing workspace trust during environment loading. Meanwhile, the community continues to be impacted by subagent misbehavior—most notably subagents falsely reporting success after hitting turn limits (#22323) and the generalist agent hanging indefinitely (#21409), both still unresolved despite months of triage.

---

## 2. Releases

**v0.51.0-preview.0** — *latest preview*
- What's Changed:
  - Fix for `no_proxy` test (`@jerrylin3321`)
  - Automated changelog update for v0.50.0-preview.1
  - Version bump to `0.51.0-nightly.20260625.g3fbf93e26`
- *[View Release](https://github.com/google-gemini/gemini-cli/releases/tag/v0.51.0-preview.0)*

**v0.50.0** — *latest stable*
- What's Changed:
  - **Feat/tool_registry** — new feature for managing tool availability
  - Fix: Release verification now ignores scripts (`npm ci --ignore-scripts`) (`@rmedranollamas`)
  - Fix: Prevent workspace binary shadowing in release verification (`@galdawave`)
- *[View Release](https://github.com/google-gemini/gemini-cli/releases/tag/v0.50.0)*

---

## 3. Hot Issues (10 noteworthy)

| # | Issue | Why it matters | Community |
|---|-------|----------------|-----------|
| 1 | **[Subagent recovery after MAX_TURNS reported as GOAL success](https://github.com/google-gemini/gemini-cli/issues/22323)** (P1, Bug) — `codebase_investigator` subagent returns `status: "success"` with `Termination Reason: "GOAL"` even though it hit the max turn limit without doing any analysis. Users get a false sense of completion. | 🟢 **10 comments** · 2 👍 — Persistent source of trust erosion; P1 indicates team is treating urgently. |
| 2 | **[Generalist agent hangs](https://github.com/google-gemini/gemini-cli/issues/21409)** (P1, Bug) — CLI defers to generalist agent and hangs indefinitely for simple tasks like folder creation. The only workaround is instructing the model to never use subagents. | 🟢 **7 comments** · 8 👍 — Highest 👍 count in active issues; severe UX blocker. |
| 3 | **[Gemini doesn't use skills and sub-agents enough](https://github.com/google-gemini/gemini-cli/issues/21968)** (P2, Bug) — Users report the model ignores custom skills and sub-agents even when tasks are directly related. Works only if explicitly instructed. | 🟢 **6 comments** — Core agent orchestration gap reduces the value of user-authored extensions. |
| 4 | **[Stop Auto Memory from retrying low-signal sessions indefinitely](https://github.com/google-gemini/gemini-cli/issues/26522)** (P2, Bug) — Auto Memory re-surfaces unprocessed sessions to the extraction agent repeatedly, even if they were deliberately skipped for low signal. | 🟢 **5 comments** — Memory hygiene degradation; leads to wasted API calls and token burn. |
| 5 | **[Shell command execution stuck on "Waiting input" after command completes](https://github.com/google-gemini/gemini-cli/issues/25166)** (P1, Bug) — Simple CLI commands hang with "Awaiting user input" despite already finishing. | 🟢 **4 comments** · 3 👍 — P1 severity; affects basic script execution reliability. |
| 6 | **[Browser subagent fails in Wayland](https://github.com/google-gemini/gemini-cli/issues/21983)** (P1, Bug) — `Termination Reason: GOAL` error in Wayland environments, making browser automation unusable for Linux/Wayland users. | 🟢 **4 comments** · 1 👍 — Linux compatibility gap. |
| 7 | **[Model frequently creates tmp scripts in random spots](https://github.com/google-gemini/gemini-cli/issues/23571)** (P2, Bug) — When shell execution is restricted, the model scatters edit scripts across directories, creating cleanup overhead before commits. | 🟢 **3 comments** — Workflow friction for users who value clean commits. |
| 8 | **[400 error with > 128 tools](https://github.com/google-gemini/gemini-cli/issues/24246)** (P2, Bug) — CLI crashes when more than 128 tools are available. Users expect smarter tool-scoping. | 🟢 **3 comments** — Scalability ceiling for power users with many MCP/agent tools. |
| 9 | **[Subagents running without permission since v0.33.0](https://github.com/google-gemini/gemini-cli/issues/22093)** (P2, Bug) — After update to v0.33.0, subagents began activating even with `agents: disabled` in config. User only wanted MCP functionality. | 🟢 **2 comments** — Consent/configuration enforcement regression. |
| 10 | **[LLM correction corrupts JSON and IPYNB files](https://github.com/google-gemini/gemini-cli/issues/28223)** (P2, Bug) — `write_file` and `replace` tools corrupt structured files when the LLM applies corrections. | — Fix PR open (#28223); high impact for data science workflows. |

---

## 4. Key PR Progress (10 important PRs)

| # | PR | What it does | Status |
|---|----|-------------|--------|
| 1 | **[fix(a2a-server): enforce workspace trust during env loading to prevent RCE](https://github.com/google-gemini/gemini-cli/pull/28319)** | Patches a zero-click Remote Code Execution vulnerability (b-519269096) by refactoring the A2A startup sequence. | 🟡 **Open** — size/m; critical security. |
| 2 | **[fix(core): limit recursive reasoning turns per single user request](https://github.com/google-gemini/gemini-cli/pull/28164)** | Caps recursive reasoning at 15 turns per request (configurable) to prevent infinite loops. Protects CPU and API quotas. | 🟡 **Open** — size/m; directly addresses user-reported hangs. |
| 3 | **[fix(a2a-server): ensure task cancellation aborts execution loop](https://github.com/google-gemini/gemini-cli/pull/28316)** | Canceling a task in Agent Mode now terminates the underlying stream, fixing "ghost executions." Also addresses race conditions and memory leaks. | 🟡 **Open** — size/l; trio of bug fixes. |
| 4 | **[fix(core-tools): bypass LLM correction for JSON and IPYNB files](https://github.com/google-gemini/gemini-cli/pull/28223)** | Surgical fix to prevent `write_file`/`replace` from corrupting `.json` and `.ipynb` files. | 🟡 **Open** — size/m; high impact for Jupyter/JSON users. |
| 5 | **[fix(cli): improve markdown rendering for CJK text and `__bold__` syntax](https://github.com/google-gemini/gemini-cli/pull/28309)** | Fixes hard line-wrapping and misinterpreted lists for CJK text; also handles double-underscore bold. | 🟡 **Open** — size/m; internationally focused UX fix. |
| 6 | **[fix(core): avoid keep-alive socket reuse during OAuth token exchange](https://github.com/google-gemini/gemini-cli/pull/28103)** | Works around CVE-2026-48931 on Node.js 24.17.0/22.23.0/26.3.0 to prevent "Premature close" errors in Google OAuth. | ✅ **Merged** — size/m; targeted security fix. |
| 7 | **[fix(mcp): add SSRF protection to OAuth metadata discovery](https://github.com/google-gemini/gemini-cli/pull/28112)** | Adds `isLoopbackHost()` and DNS validation to OAuth discovery flow, closing a SSRF gap relative to `web-fetch.ts`. | ✅ **Merged** — size/l; important for MCP security posture. |
| 8 | **[feat(caretaker-triage): implement main worker execution loop](https://github.com/google-gemini/gemini-cli/pull/28306)** | Implements Cloud Run Job execution loop, Pub/Sub egress publisher, and stubbed LLM triage orchestrator. | 🟡 **Open** — size/m; foundation for automated triage pipeline. |
| 9 | **[fix(cli): avoid splitting emoji when truncating display strings](https://github.com/google-gemini/gemini-cli/pull/28224)** | `sanitizeForDisplay` now counts grapheme clusters instead of UTF-16 code units, preventing emoji replacement characters. | 🟡 **Open** — size/s; small but visible polish fix. |
| 10 | **[fix(cli): parse commented settings.json in memory bootstrap](https://github.com/google-gemini/gemini-cli/pull/28219)** | Allows the lightweight CLI parent process to read comment-bearing `settings.json` without silently falling back to defaults. | 🟡 **Open** — size/s; fixes a silent configuration drop. |

---

## 5. Feature Request Trends

1. **AST-aware codebase tools** — Multiple issues (#22745, #22746) push for AST-aware file reads, search, and codebase mapping to reduce turn usage, improve precision, and cut token waste. Users want method-level boundaries instead of line-based reads.

2. **Subagent trajectory visibility** — The community consistently requests the ability to view, share, and debug subagent trajectories (#22598, #21763). The `/chat share` command should expose subagent context alongside main-session logs to improve debugging and eval workflows.

3. **Better tool selection and scoping** — Two directions: (a) the agent struggles with >128 tools (#24246) and needs smarter tool filtering; (b) the agent ignores custom skills and sub-agents (#21968) even when relevant. Users want the agent to proactively use—but not over-use—available tools.

4. **Automated evaluations and behavioral testing** — Issue #24353 is a meta-EPIC calling for component-level evaluations, building on the 76 behavioral eval tests already in the repo. The community wants systematic, regression-safe testing for agent behavior.

5. **Agent "self-awareness" and safety** — Issue #21432 requests that the CLI understand its own mechanics (flags, hotkeys, execution) well enough to be its own guide. Separately, #22672 asks for protection against destructive commands (e.g., `git reset --force`).

---

## 6. Developer Pain Points

**🟠 Subagent reliability is the #1 pain point.**
- False success reports (#22323), indefinite hangs (#21409), and ghost executions after cancellation (#28316) erode trust.
- Subagents activate despite explicit disabled configuration (#22093), breaking user expectations.

**🟠 Shell and command execution is fragile.**
- Commands get stuck on "awaiting input" after completion (#25166).
- Interactive prompts (e.g., `vite create`) cause the agent to freeze (#22465).
- The model scatters temporary scripts across directories, requiring manual cleanup (#23571).

**🟠 Auto Memory creates unbounded background work.**
- Low-signal sessions are retried indefinitely (#26522), wasting API credits.
- Memory patches silently skip invalid or malformed entries without feedback (#26523).
- Secrets redaction happens *after* content reaches model context, and logging may expose skill files (#26525).

**🟠 Configuration and rendering gaps.**
- Symlinked agent files are not recognized (#20079).
- `settings.json` with comments is silently ignored during bootstrap (#28219).
- CJK text is hard-wrapped and emoji is corrupted in terminal display (#28309, #28224).
- Terminal resize causes flickering due to lack of `RenderStatic` migration (#21924).

**🟠 Browser and platform issues.**
- Browser subagent fails entirely on Wayland (#21983).
- Browser agent ignores `settings.json` overrides like `maxTurns` (#22267).

---

*Data sourced from github.com/google-gemini/gemini-cli. Digest covers activity from 2026-07-08 to 2026-07-09.*

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

# GitHub Copilot CLI Community Digest — 2026-07-09

## Today's Highlights

The Copilot CLI community remains focused on long-standing agent reliability issues, particularly the **auto-compaction → infinite re-planning loop** bug that dominated issue volume this week. The long-running **custom slash commands** feature request (Issue #618) continues to lead community demand with 99 👍 across 32 comments. New triage issues today flag **model family aliasing** and **startup model resolution** gaps as emerging pain points for power users.

**No new releases** were published in the last 24 hours.

## Releases

No new releases detected in the last 24 hours. The current version in the wild remains **1.0.69** (as referenced in Issue #4059).

## Hot Issues (10 Noteworthy Items)

1. **#618 — Feature Request: Custom Slash Commands from `.github/prompts/`**  
   *Author: AungMyoKyaw | 👍 99 | 32 comments*  
   The highest-requested feature this month. Users want slash command extensibility (like Claude Code's custom commands) via prompt files in `.github/prompts/`, mirroring VS Code's Copilot extension behavior.  
   [github/copilot-cli Issue #618](https://github.com/github/copilot-cli/issues/618)

2. **#970 — macOS Gatekeeper blocks Copilot after Homebrew upgrades**  
   *Author: jdesulme | 👍 21 | 6 comments*  
   Corporate security policies prevent verified execution of the `copilot` binary post-upgrade. Users must manually approve via Privacy & Security settings each time.  
   [github/copilot-cli Issue #970](https://github.com/github/copilot-cli/issues/970)

3. **#2792 — Automatic model switching for planning vs execution**  
   *Author: hakontel | 👍 14 | 4 comments*  
   Proposed feature to use one model (e.g., cheaper/faster) for planning and another for execution. Reflects growing demand for cost-optimized agent workflows.  
   [github/copilot-cli Issue #2792](https://github.com/github/copilot-cli/issues/2792)

4. **#3158 — Plan→Compact→Re-Plan infinite loop (217 cycles)**  
   *Author: Akhi-microsoft | 4 comments*  
   High-severity agent bug: auto-compaction preserves the planning summary, causing the agent to re-read and re-plan instead of executing. Resulted in 217 planning cycles with zero file edits. Multiple duplicate issues filed by the same reporter (#3144–#3157). This remains the most critical unresolved agent defect.  
   [github/copilot-cli Issue #3158](https://github.com/github/copilot-cli/issues/3158)

5. **#4059 — `/models` does not show extended context pricing**  
   *Author: ecki | 1 comment (triage)*  
   UI gap in the model explorer: models with extended context (e.g., 1M tokens) have no key or navigation to view their separate pricing tier, making cost evaluation difficult.  
   [github/copilot-cli Issue #4059](https://github.com/github/copilot-cli/issues/4059)

6. **#4016 — BYOK (COPILOT_PROVIDER_*) broken in `--acp` mode**  
   *Author: gwexler-msft | 👍 2 | 1 comment*  
   Custom providers configured via environment variables work for `copilot -p` but fail in `--acp --stdio` mode with "-32000 Authentication required". Regression likely introduced between 1.0.61–1.0.68.  
   [github/copilot-cli Issue #4016](https://github.com/github/copilot-cli/issues/4016)

7. **#2112 — Stale keytar entries cause repeated OAuth popups on every launch**  
   *Author: AurelioBellettiGitHub | 👍 1 | 1 comment*  
   HTTP MCP servers trigger browser-based OAuth every launch because expired tokens stored in the OS keychain (via keytar) shadow valid file-cache tokens.  
   [github/copilot-cli Issue #2112](https://github.com/github/copilot-cli/issues/2112)

8. **#4053 — TUI hangs at 'Loading: N skills' on NFS/GPFS filesystems**  
   *Author: raylim | 1 comment*  
   Linux TUI mode hangs on distributed filesystems due to a SIGCHLD race condition when Tokio spawns `which gh` across 30+ concurrent threads. Affects corporate HPC environments.  
   [github/copilot-cli Issue #4053](https://github.com/github/copilot-cli/issues/4053)

9. **#4054 — `/resume` broken for all non-git sessions**  
   *Author: Fabi0San | 1 comment*  
   Sessions created outside git repos store `repository = '/'`, making them unselectable in the resume picker due to a git gate. Also: cross-session `/resume` commands mangle context.  
   [github/copilot-cli Issue #4054](https://github.com/github/copilot-cli/issues/4054)

10. **#4068 — Allow specifying model *family* instead of exact version**  
    *Author: alistardust | 0 comments (triage, just filed)*  
    Users want to specify `opus` or `sonnet` to automatically resolve to the latest stable release within that family, avoiding manual config updates on each model version bump.  
    [github/copilot-cli Issue #4068](https://github.com/github/copilot-cli/issues/4068)

## Key PR Progress

1. **#4057 — Install**  
   *Author: EverydayEvertime | Open*  
   A new installation-related PR. No detailed description available; likely a documentation or build script improvement.  
   [github/copilot-cli PR #4057](https://github.com/github/copilot-cli/pull/4057)

2. **#3708 — Add files via upload**  
   *Author: panchofrancisco1987-ui | Open*  
   Generic file upload PR with no semantic description. Minimal community engagement.  
   [github/copilot-cli PR #3708](https://github.com/github/copilot-cli/pull/3708)

*Note: Only 2 PRs were updated in the last 24h, both with minimal description/activity. Community development velocity appears low this window.*

## Feature Request Trends

- **Custom Slash Commands / Prompt Extensibility**: #618 remains the top-voted request. Users want to define team- or project-specific slash commands via `.github/prompts/` files, mirroring VS Code and Claude Code capabilities.
- **Model Flexibility**: Multiple requests (#2792, #4068, #4067) center on improving model selection: family-based aliasing, startup model configuration, and plan-vs-execution model separation. Users want to avoid hardcoding version strings.
- **Session Management**: Requests for configurable resume hints (#4066) and fixing `/resume` for non-git sessions (#4054) indicate growing reliance on session persistence for long-lived agent tasks.

## Developer Pain Points

- **Agent Context Compaction Bugs**: The **plan→compact→re-plan** infinite loop (#3158 and 14 duplicates) is the single most disruptive issue. It wastes entire sessions with no output, eroding trust in agent modes.
- **Authentication & BYOK Fragility**: Repeated regressions with custom providers in `--acp` mode (#4016), stale keychain entries (#2112), and OAuth popup spam are eroding confidence for enterprise/corporate users who need non-interactive auth.
- **Installation & Platform Friction**: macOS Gatekeeper blocks (#970), lack of cleanup of old CLI versions (2GB+ disk waste, #1624), and hangs on NFS filesystems (#4053) degrade the out-of-box experience, especially in managed/corporate environments.
- **Model Discovery UX**: The `/models` command lacks extended context pricing navigation (#4059), and custom models set in `settings.json` aren't respected at startup (#4067), forcing manual workarounds.
- **Exfiltration Protection False Positives**: Overly aggressive content filtering (#4065) blocks legitimate spec content containing shell-like syntax (e.g., `${env.VAR}`), frustrating developers using infrastructure-as-code patterns.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

# Kimi Code CLI Community Digest — 2026-07-09

## Today's Highlights
The project is currently in a low-activity period with no new releases or pull requests in the last 24 hours. The community's attention remains focused on a single open enhancement request regarding SSL certificate handling, which has sparked discussion due to enterprise environment constraints.

## Releases
No new versions were published in the last 24 hours.

## Hot Issues

1. **[#2458] Add option to ignore ssl certificate**  
   *Author: dmorsin | Updated: 2026-07-08 | Comments: 2*  
   A user behind an enterprise antivirus that uses man-in-the-middle SSL inspection cannot authenticate because the tool rejects the organization's re-signed certificate. This issue is important for enterprise adoption, but has drawn zero upvotes, suggesting it may be a niche need.  
   [GitHub Issue #2458](https://github.com/MoonshotAI/kimi-cli/issues/2458)

## Key PR Progress
No pull requests were updated in the last 24 hours.

## Feature Request Trends
Based on the sole active issue and recent historical data, the dominant feature request direction is **enterprise network compatibility**, specifically:
- SSL certificate bypass/ignore options for corporate proxy environments
- Support for custom CA certificates for organizations using MITM-based security tools

## Developer Pain Points
The primary recurring frustration identified is **SSL/TLS configuration inflexibility**:
- Developers in corporate environments with forced SSL inspection cannot use the CLI without workarounds
- No existing mechanism to trust organization-issued certificates or disable strict certificate validation
- This is a common blocker for enterprise adoption of CLI tools, and the lack of movement on this issue may indicate a gap in the project's target audience strategy

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

# OpenCode Community Digest — 2026-07-09

## Today’s Highlights
Today sees a major batch of **eight bug-fix PRs** from HOYALIM targeting performance regressions (prompt history bloat, session busy states, duplicate project init). The community is rallying around **MCP client capabilities** (Issue #28567) and **agent loop detection** (Issue #31942) as critical gaps. The long-running request for **Go plan usage APIs** (#16017) continues to dominate the feature discussion with 96 👍.

## Releases
No new releases in the last 24 hours. The latest stable remains **v1.17.14**, though users reported UI loading failures after disabling the new layout (#35701, closed).

## Hot Issues

1. **[#16017] Add Go plan usage/balance API endpoint** — 96 👍, 23 comments.  
   Long-standing request to expose rolling/weekly/monthly usage data via API. Dashboard already shows this data; users want programmatic access for billing monitoring.  
   [View Issue](https://github.com/anomalyco/opencode/issues/16017)

2. **[#28567] Full MCP client capabilities** — 25 👍, 22 comments. *CLOSED*  
   OpenCode’s MCP client lags behind the latest spec. Users blocked from streaming tools, sampling, and optional features. High demand for parity.  
   [View Issue](https://github.com/anomalyco/opencode/issues/28567)

3. **[#6096] Token-per-second display** — 60 👍, 19 comments.  
   Simple UX improvement: show TPS per message. Community strongly supports performance transparency.  
   [View Issue](https://github.com/anomalyco/opencode/issues/6096)

4. **[#30086] High CPU usage in recent versions** — 11 👍, 17 comments.  
   Regression: CPU spikes making 3+ sessions unusable. Users reporting dramatic slowdowns in the last week.  
   [View Issue](https://github.com/anomalyco/opencode/issues/30086)

5. **[#17953] Destructive file operation guardrails** — 0 👍, 10 comments. *CLOSED*  
   Follow-up to deletion without confirmation (#17949). Proposes user confirmation dialogs for bulk deletes. Modest community engagement but high safety relevance.  
   [View Issue](https://github.com/anomalyco/opencode/issues/17953)

6. **[#35556] V2: first Location can expose empty plugin generation** — 0 👍, 10 comments. *CLOSED*  
   Race condition: `PluginSupervisor` exposes service before initial reload completes, producing empty/partial plugin sets.  
   [View Issue](https://github.com/anomalyco/opencode/issues/35556)

7. **[#1934] Auto-run `aws sso login` on credential expiry** — 11 👍, 7 comments.  
   Frequent SSO expiration interrupts workflow. Users want automatic re-auth rather than manual restart.  
   [View Issue](https://github.com/anomalyco/opencode/issues/1934)

8. **[#31942] Agent loops 277 times on MCP resource_list without circuit breaker** — 0 👍, 2 comments.  
   Critical: agent exhausted workspace token spend by hammering a non-existent MCP resource. No loop detection.  
   [View Issue](https://github.com/anomalyco/opencode/issues/31942)

9. **[#23066] MCP elicitation support** — 21 👍, 3 comments. *CLOSED*  
   Enable human-in-the-loop workflows for MCP tools. Strong community interest despite closure.  
   [View Issue](https://github.com/anomalyco/opencode/issues/23066)

10. **[#35952] Tasks (subagents) not resumable on failure/freeze** — 0 👍, 2 comments.  
    Subagents stalling halfway through jobs cannot be restarted, wasting usage on stalled runs.  
    [View Issue](https://github.com/anomalyco/opencode/issues/35952)

## Key PR Progress

1. **[#36003] fix(models): fall back when catalog refresh stalls**  
   Prevents startup hang when `models.dev` fetch or cache lock stalls. Uses cached/empty fallback.  
   [View PR](https://github.com/anomalyco/opencode/pull/36003)

2. **[#36002] fix(session): settle busy status after stream close**  
   Session remained busy after stream closed, blocking further input. Fixes residual busy state.  
   [View PR](https://github.com/anomalyco/opencode/pull/36002)

3. **[#36000] fix(app): cap prompt history attachments**  
   Inline data URLs from attachments bloated persisted state to megabytes. Caps attachment size.  
   [View PR](https://github.com/anomalyco/opencode/pull/36000)

4. **[#36001] fix(session): preserve cache prefix across mode switch**  
   Mode switch broke prefix-cache locality, increasing costs. Preserves provider prefix across switches.  
   [View PR](https://github.com/anomalyco/opencode/pull/36001)

5. **[#35999] fix(session): separate active context tokens from usage totals**  
   Context meter conflated active context size with cumulative usage. Separates counters for accurate display.  
   [View PR](https://github.com/anomalyco/opencode/pull/35999)

6. **[#35998] fix(tui): avoid duplicate project initialization**  
   Concurrent loads of same directory caused duplicate initialization. Adds deduplication guard.  
   [View PR](https://github.com/anomalyco/opencode/pull/35998)

7. **[#31985] fix(shell): add PowerShell UTF-8 command wrapper on Windows**  
   Comprehensive fix for PowerShell encoding issues across multiple code paths. Closes 5 issues.  
   [View PR](https://github.com/anomalyco/opencode/pull/31985)

8. **[#35985] fix(provider): derive reasoning variants from models.dev**  
   Moves reasoning variants from hardcoded tables to `models.dev` schema for maintainability.  
   [View PR](https://github.com/anomalyco/opencode/pull/35985)

9. **[#35982] fix(provider): improve prompt caching**  
   Standardizes prompt caching across AI SDK providers (camelCase/snake_case/incompatible SDKs).  
   [View PR](https://github.com/anomalyco/opencode/pull/35982)

10. **[#34794] feat(provider): add --model free to pick random zero-cost model**  
    New flag selects a random free OpenCode Zen model per session.  
    [View PR](https://github.com/anomalyco/opencode/pull/34794)

## Feature Request Trends

- **MCP Ecosystem Expansion** — Requests for full protocol support (#28567), elicitation (#23066), and circuit breakers (#31942) highlight that MCP is now critical infrastructure.
- **Usage Transparency** — Strong demand for Go plan API endpoints (#16017) and token-per-second metrics (#6096) shows users want granular cost/performance visibility.
- **Subagent Reliability** — Non-resumable tasks (#35952), hang detection (#33028), and loop prevention (#31942) point to frustration with subagent fragility.
- **Linux CLI Polish** — Two requests (#35977, #35978) demand preinstalled clipboard tools (`xclip`, `xsel`, `wl-clipboard`) to avoid manual setup pain.
- **Session Lifecycle Management** — Configurable data retention (#34875), auto-resume after restart (#35646), and cached directory handling (#36004) show users want persistent, clean sessions.

## Developer Pain Points

1. **Performance regressions** — CPU spikes (#30086) and prompt history bloat (#36000) erode trust in newer versions.
2. **Subagent waste** — Agents hang (#33028), loop endlessly (#31942), and cannot be resumed (#35952), burning paid quota with no recovery path.
3. **Model/provider friction** — GLM-5.2 `instructions` field rejection (#33490), intermittent 500 errors on OpenCode Go (#30310), and encoding issues on Windows PowerShell (#31985) create constant configuration overhead.
4. **Copy/paste on Linux** — Two concurrent issues (#35977, #35978) highlight a long-standing CLI UX gap that new users hit immediately.
5. **SSO credential management** — Repeated `aws sso login` interruptions (#1934) disrupt cloud developers multiple times daily.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>

# Pi Community Digest — 2026-07-09

## Today's Highlights
A major flurry of activity around session lifecycle bugs and compaction edge cases dominated the last 24 hours, with significant contributions from @mitsuhiko and @Blue-B on settlement and large-session reliability. The team also closed 18 issues and merged 6 pull requests, including fixes for the Linux clipboard regression and GitHub Copilot's extended 1M token context window support. Notably, several new provider integration requests (Novita AI, Fable OAuth) signal growing demand for provider diversity.

## Releases
No new releases in the last 24 hours. Latest stable remains **v0.80.3**.

## Hot Issues

1. **[#5886](https://github.com/earendil-works/pi/issues/5886) — AgentSession settlement/continuation lifecycle bugs** (OPEN, 4 comments, 2👍)  
   @mitsuhiko consolidated a class of issues where post-run logic tries to continue an agent from a transcript that is no longer valid. Critical for agent reliability in long-running sessions.

2. **[#6303](https://github.com/earendil-works/pi/issues/6303) — Exponential retry backoff has no cap** (OPEN, 2 comments, 1👍)  
   Default `baseDelayMs=2000` can balloon to ~4 minutes by attempt 7. The `getRetrySettings()` API returns `maxRetryDelayMs` but the retry loop ignores it — a clear API/implementation mismatch.

3. **[#6434](https://github.com/earendil-works/pi/issues/6434) — Empty reasoning content render for OpenAI models** (CLOSED, 3 comments, 1👍)  
   Pi was not stripping OpenAI's `thinkingSignature` preamble, causing empty thinking blocks in the TUI. Quickly fixed via PR #6436.

4. **[#6429](https://github.com/earendil-works/pi/issues/6429) — `max_output_tokens=1` after compaction** (CLOSED, 1 comment)  
   A dangerous edge case: auto-compaction of long OpenAI sessions sets `max_output_tokens=1`, making every subsequent request fail with a 400 error. Highlights fragility in compaction state management.

5. **[#6425](https://github.com/earendil-works/pi/issues/6425) — Large compactions need chunking and failure backoff** (CLOSED, 1 comment)  
   @Blue-B reports that summary requests themselves become the fragile part once sessions grow large. A critical quality issue for power users running day-long sessions.

6. **[#6426](https://github.com/earendil-works/pi/issues/6426) — Model switch to smaller context window should pre-compact** (CLOSED, 1 comment)  
   Another compaction edge case: switching from a large-context to small-context model causes overflow before the new model gets a chance to answer.

7. **[#6424](https://github.com/earendil-works/pi/issues/6424) — Threshold auto-compaction can leave unfinished work idle** (CLOSED, 1 comment)  
   @Blue-B observed compaction appending a summary entry while the assistant was mid-turn with a placeholder. The compaction entry broke the turn's continuation.

8. **[#6431](https://github.com/earendil-works/pi/issues/6431) — Bun fetch socket drop not classified as retryable** (CLOSED, 1 comment)  
   Transient network drops on Bun cause termination without any retry. A critical gap in `isRetryableAssistantError` classification for the Bun runtime.

9. **[#6438](https://github.com/earendil-works/pi/issues/6438) — OpenCode provider 500 error for mimo-v2.5-free** (CLOSED, 1 comment)  
   Direct `curl` works but Pi gets a 500. Suggests mismatched request format or provider-specific header requirements.

10. **[#6406](https://github.com/earendil-works/pi/issues/6406) — Read-only config folder fails credential reads due to lock file creation** (CLOSED, 2 comments)  
    Pi creates a file lock even for read-only credential access, breaking systems with read-only `~/.pi/agent` directories. A usability issue for security-constrained environments.

## Key PR Progress

1. **[#6437](https://github.com/earendil-works/pi/pull/6437) — Update Copilot extended context windows** (MERGED)  
   Updates `contextWindow` to 1,000,000 tokens for models supporting GitHub's extended context. Implements @tim-hub's request from issue #6439.

2. **[#6436](https://github.com/earendil-works/pi/pull/6436) — Hide responses reasoning comment markers** (MERGED)  
   Strips `<!-- -->` separators from OpenAI visible reasoning while preserving signed reasoning for replay. Fixes #6434.

3. **[#6430](https://github.com/earendil-works/pi/pull/6430) — Fix fork menu double-select** (MERGED)  
   Closes the forking menu before starting the fork process to prevent duplicate session creation when extensions slow down teardown. Fixes #6321.

4. **[#6427](https://github.com/earendil-works/pi/pull/6427) — Add prompt cache miss tracking** (OPEN)  
   @mitsuhiko's PR detects cache misses per turn, warning the user at significant misses. Adds important observability for prompt caching economics.

5. **[#6418](https://github.com/earendil-works/pi/pull/6418) — Fix native clipboard in Bun release** (MERGED)  
   Two-part fix: copies `.node` files into the clipboard package and adds `xclip` fallback on X11. Fixes #6250.

6. **[#6417](https://github.com/earendil-works/pi/pull/6417) — Support custom metadata in JSONL session headers** (MERGED)  
   Adds optional `metadata?: Record<string, unknown>` to v3 JSONL session format. Addresses #6402.

7. **[#6413](https://github.com/earendil-works/pi/pull/6413) — Show git info in local version** (MERGED)  
   Closes #6412. Displays branch and commit hash in `pi --version` for local builds — helpful for debugging custom builds.

8. **[#6420](https://github.com/earendil-works/pi/issues/6420) — Add Novita AI as built-in provider** (CLOSED feature request)  
   OpenAI-compatible provider with base URL `https://api.novita.ai/openai`. Community interest in expanding default provider coverage.

9. **[#6419](https://github.com/earendil-works/pi/issues/6419) — Stabilize generated image model formatting** (CLOSED)  
   Proposes Biome-formatted TypeScript output from code generators to reduce formatting churn in PRs.

10. **[#6435](https://github.com/earendil-works/pi/issues/6435) — Export in-memory session storage** (CLOSED)  
    @stack1ng requests public export of the in-memory session storage implementation to enable extension developers to extend it cleanly.

## Feature Request Trends

- **Session lifecycle observability**: Multiple requests for cache hit/miss tracking (#6427), compaction diagnostics, and warning banners for state transitions.
- **Provider diversity**: Strong signals for built-in support for Novita AI (#6420), Fable OAuth (#6422), and OpenCode model fixes (#6438).
- **Ephemeral model changes**: #5263 (5 comments, 6👍) asks for in-session model/thinking changes to be ephemeral by default, with a new "Default model" settings entry. This is the most-upvoted open feature request.
- **Plugin system hooks**: #6428 requests a `session_before_load` hook so extensions can intervene before session files are read at startup.
- **Metadata extensibility**: #6402's custom metadata in JSONL headers was merged as #6417 — a sign that Pi's session format is becoming a platform for integrations.

## Developer Pain Points

1. **Compaction reliability**: The most acute pain point this week. Three issues (#6424, #6425, #6426) from @Blue-B alone describe distinct failure modes in large-session compaction, from unfinished work being interrupted to summary calls failing on their own. This is the silent productivity killer for users running hours-long agent sessions.

2. **Session settlement bugs**: #5886 highlights a class of bugs where post-run logic operates on stale transcript state. @mitsuhiko's meta-issue is a sign this is systemic rather than isolated.

3. **Cross-platform clipboard fragility**: #6250 (Linux/X11) and #6373 (general image paste) expose that Pi's clipboard handling has platform-specific regressions that are hard to test comprehensively.

4. **Provider model mapping drift**: #6204 (ghost model `mimo-v2-omni`) and #6438 (model works via curl but not Pi) suggest Pi's model metadata can desync from actual provider endpoints, causing silent failures.

5. **Token budget accounting**: #6429 (`max_output_tokens=1` after compaction) and #6378 (context length overflow without compression plugin guidance) show that Pi's token budget management across session lifecycle events has gaps that can make sessions unrecoverable.

6. **Retry transparency**: #6303 and #6431 demonstrate that Pi's retry logic is both unbounded (no cap on exponential backoff) and incomplete (not marking all transient errors as retryable), leading to either excessive wait times or premature termination.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>

# Qwen Code Community Digest
**Date: 2026-07-09**

---

## Today's Highlights
The v0.19.8 release ships with CLI serve environment isolation and WeCom channel documentation. A critical bug (Issue #6505) exposing indefinite subagent loop vulnerabilities was closed with a fix, while the community is actively debating a major RFC (Issue #6378) on multi-workspace daemon support. CI/CD reliability remains a pain point, with two release workflows failing due to quality checks.

---

## Releases
### [v0.19.8](https://github.com/QwenLM/qwen-code/releases/tag/v0.19.8)
- **New**: `feat(cli)` — Added serve environment isolation and total admission control (PR by @doudouOUC).
- **Docs**: Added WeCom to the channels overview (PR by @DragonnZhang).

---

## Hot Issues
**Top 10 noteworthy issues by community impact:**

1. **[RFC: Support multiple workspaces in one qwen serve daemon](https://github.com/QwenLM/qwen-code/issues/6378)** (OPEN, 19 comments)  
   *Why it matters:* This proposal reimagines the "1 daemon = 1 workspace × N sessions" model. Community heavily engaged; could reshape deployment patterns for teams running multiple projects.

2. **[Subagent reasoning loop can repeat identical tool calls indefinitely](https://github.com/QwenLM/qwen-code/issues/6505)** (CLOSED, 4 comments)  
   *Why it matters:* A subagent silently loops on identical tool calls while the main agent's loop detection fails — a concerning silent-fail pattern for production multi-agent setups.

3. **[hard limit: 0 when env-configured model reserves its full default context window for output](https://github.com/QwenLM/qwen-code/issues/6384)** (OPEN, 5 comments)  
   *Why it matters:* Context compression miscalculation leads to "hard limit: 0" errors — blocks users with certain model configurations entirely.

4. **[CI: qwen-code-action swallows stderr, making triage failures invisible](https://github.com/QwenLM/qwen-code/issues/6553)** (OPEN, 2 comments)  
   *Why it matters:* CI pipeline masks silent failures (API errors, empty model responses). Directly impacts release reliability (see Issue #6554).

5. **[Release Failed for v0.19.8-nightly](https://github.com/QwenLM/qwen-code/issues/6554)** (OPEN, 1 comment)  
   *Why it matters:* The quality job failed — third release failure this week (also #6476). Community relying on nightly builds will feel this.

6. **[Vision bridge image interpretation times out after 30000ms](https://github.com/QwenLM/qwen-code/issues/6524)** (CLOSED, 1 comment)  
   *Why it matters:* Hardcoded 30s timeout for image-to-text bridging fails on larger images via DashScope — no configurable override exists.

7. **[Anthropic Claude 4.8+ rejects requests with deprecated temperature parameter](https://github.com/QwenLM/qwen-code/issues/6519)** (CLOSED, 1 comment)  
   *Why it matters:* Blocking issue for any user on Claude Opus 4.8+; shows gap in model version compatibility testing.

8. **[WebShell user messages show serialized @ references instead of chips](https://github.com/QwenLM/qwen-code/issues/6536)** (OPEN, 1 comment)  
   *Why it matters:* UI regression degrades the @-mention UX — chips collapse to raw text post-send, confusing users.

9. **[Session history silently truncated when parentUuid chain has a missing link](https://github.com/QwenLM/qwen-code/issues/6501)** (CLOSED, 1 comment)  
   *Why it matters:* Data integrity issue: partial/failed writes can silently truncate history without alerting the user.

10. **[ProxyAgent does not support NO_PROXY](https://github.com/QwenLM/qwen-code/issues/6401)** (CLOSED, 2 comments)  
   *Why it matters:* Corporate proxy users cannot bypass internal hosts — a blocker for enterprise adoption. Now under autofix.

---

## Key PR Progress
**10 important PRs merged or in active review:**

1. **[feat(daemon): persist session artifacts across restarts](https://github.com/QwenLM/qwen-code/pull/6557)** (OPEN)  
   *What:* Replacement PR for #6259 (squashed). Implements V2 daemon session artifact metadata persistence — restores artifacts across restart/replay. Foundation for durable sessions.

2. **[fix(core): clamp max_tokens to the context window; retire the output reservation](https://github.com/QwenLM/qwen-code/pull/6556)** (OPEN)  
   *What:* Fixes Issue #6384 root cause: auto-compaction now uses full context window; output requests match available capacity. Direct fix for "hard limit: 0" errors.

3. **[feat(cli): List persisted sessions for trusted workspaces](https://github.com/QwenLM/qwen-code/pull/6558)** (OPEN)  
   *What:* Trusted non-primary workspace sessions can now list persisted sessions — enables multi-workspace visibility while maintaining trust gates.

4. **[feat(channels): support webhook-triggered channel tasks](https://github.com/QwenLM/qwen-code/pull/6495)** (OPEN)  
   *What:* External webhook POST events can trigger Qwen-generated responses in daemon-managed channels — bridges Qwen into event-driven pipelines.

5. **[feat(scheduled-tasks): add isolated run mode via create_sub_session tool](https://github.com/QwenLM/qwen-code/pull/6535)** (OPEN, in review)  
   *What:* New daemon-only tool spawns isolated sub-sessions for cron tasks — prevents context pollution between scheduled runs.

6. **[fix: apply prettier formatting](https://github.com/QwenLM/qwen-code/pull/6555)** (OPEN)  
   *What:* 74 files with whitespace-only changes to fix the nightly release quality job. Necessary infrastructure fix.

7. **[fix(vscode-companion): don't override cursorPosition=0](https://github.com/QwenLM/qwen-code/pull/2971)** (OPEN)  
   *What:* Long-standing bugfix for VS Code autocomplete misfire when cursor is at position 0. Important for IDE users.

8. **[feat(hooks): add MessageDisplay hook for mid-turn streaming](https://github.com/QwenLM/qwen-code/pull/6489)** (OPEN)  
   *What:* New hook fires repeatedly during streaming — enables incremental observation of replies. Addresses a long-standing gap in hook coverage.

9. **[feat(qqbot): group message handling and cron-msg-experimental](https://github.com/QwenLM/qwen-code/pull/6457)** (OPEN)  
   *What:* Final part of QQ Bot channel adapter — keyword triggers, @-mentions, and cron support. Final step for QQ integration.

10. **[ci(autofix): Add single-target scheduler](https://github.com/QwenLM/qwen-code/pull/6547)** (CLOSED)  
   *What:* Autofix now scans only one PR per 10-minute run — prevents resource contention. Improves CI stability for automated fixes.

---

## Feature Request Trends
| Theme | Signal | Community Sentiment |
|-------|--------|-------------------|
| **Multi-workspace daemon** | Issue #6378 (19 comments, RFC) | Active debate on design trade-offs. High demand from power users managing multiple projects. |
| **Read-only Advisor loop** | Issue #6542 (new, 1 comment) | Desire for a structured second-opinion system for complex tasks — shows hunger for reliability in agentic workflows. |
| **Background task awareness in hooks** | Issue #6529 (closed, 3 comments) | Users want hooks to report cron/background task status at stop events — growing need for observability. |
| **Configurable timeouts** | Issues #6308 (AutoMemory), #6524 (vision bridge) | Multiple requests to make hardcoded timeouts configurable — consistent pattern across features. |
| **Channel message control** | Issue #6392 (dmPolicy), #6538 (payload diagnostics) | Operators want granular DM disable and better debugging for channel adapters — enterprise governance. |
| **Sub-session isolation** | PR #6535 (isolated cron runs) | Clear demand for sandboxed execution contexts to prevent cross-task context pollution. |

---

## Developer Pain Points
1. **Silent CI failures** — Issue #6553, #6554, #6476: Three release failures this week, with stderr being swallowed by CI scripts. Developers are blind to root causes without manual triage.

2. **Context/token miscalculations** — Issue #6384: The "hard limit: 0" bug blocks all requests for certain model configurations. A critical confidence-breaker.

3. **Subagent loop vulnerabilities** — Issue #6505: The main agent's LoopDetectionService doesn't cover subagents. Developers running multi-agent workflows risk infinite loops without warning.

4. **Windows extension installs** — Issue #6334: Git clone failures due to stale temp directories persist. Still a barrier for Windows users despite multiple fixes.

5. **Model version compatibility gaps** — Issue #6519: Deprecated parameters for new model versions (Claude 4.8+). Indicates insufficient testing against fast-moving upstream models.

6. **Worktree/workspace memory pollution** — Issue #6449: Shared project memory causes context contamination across parallel worktrees. Developers report constant LLM "self-management" overhead trying to clean up noise.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>

# DeepSeek TUI Community Digest — 2026-07-09

## Today's Highlights

The v0.8.68 milestone is reaching its final sprint with 20+ PRs merged in the last 24 hours, focusing on Fleet agent profile consolidation, catalog automation, and Android/Termux support. The community's prolific contributor JayBeest continues to drive sub-agent tool scoping work, while maintainer Hmbown has been systematically closing out performance and UX stopship items from the cutover checklist. A notable new contributor (hongqitai) landed a significant localization extraction PR.

## Releases

No new releases in the last 24 hours. The project remains in the v0.8.68 milestone cycle with active work on `work/v0.9.0-cutover` branch.

## Hot Issues

1. **[#4092 — v0.8.68 execution board: lane order, dependencies, and agent protocol (canonical packet)](https://github.com/Hmbown/CodeWhale/issues/4092)**  
   *51 comments* — The canonical tracking issue for the entire v0.8.68 milestone. Documents lane architecture (meta, fleet, catalog, perf, inspector, stopship, copy) and serves as the single entry point for all milestone agents. High community engagement reflects its role as the coordination hub.

2. **[#4042 — feat: Environment-level tool sandboxing for sub-agents](https://github.com/Hmbown/CodeWhale/issues/4042)**  
   *12 comments (CLOSED)* — JayBeest's comprehensive analysis of CodeWhale's tool restriction enforcement across sessions, sub-agents, Fleet, and MCP. Confirmed `--disallowed-tools` exists and works. Closed by PR #4096 which added the implementation plan and Phase 1 code.

3. **[#3965 — Per-sub-agent provider assignment (explicit routing) + LM Studio support](https://github.com/Hmbown/CodeWhale/issues/3965)**  
   *7 comments (CLOSED)* — A well-articulated user request from JayBeest for per-child provider routing, including custom OpenAI-compatible providers like LM Studio. Closed by PR #4262 which made AgentProfile the canonical surface without introducing separate routing configs.

4. **[#3488 — v0.8.68: Unicode, CJK, and terminal-width rendering QA](https://github.com/Hmbown/CodeWhale/issues/3488)**  
   *3 comments (OPEN)* — A persistent QA lane tracking rendering problems broader than single widgets: CJK text, mixed-width Unicode, wrapped output, and terminal-width changes. Has been open since June 23 with slow but steady attention — a lingering blocker for international users.

5. **[#4227 — feat: 🐋 help JayBeest keep up with the CodeWhale tsunami 🌊](https://github.com/Hmbown/CodeWhale/issues/4227)**  
   *2 comments (OPEN)* — A creative meta-issue from JayBeest requesting a workflow that pulls latest main, rebuilds, and runs smoke tests to stay current with the project's 10+ PRs/day velocity. Reflects the challenge of contributing to a hyperactive codebase.

6. **[#4097 — v0.8.67: Parent model burns turns with peek+sleep polling loop](https://github.com/Hmbown/CodeWhale/issues/4097)**  
   *1 comment (CLOSED)* — Mr-Moon121 reports a regression of #3183 where parent agents enter wasteful `peek → sleep → peek` loops instead of passively waiting for sub-agents. A performance concern that undermines the sub-agent architecture's efficiency.

7. **[#4184 — Use Models.dev as the source of truth for provider and model metadata](https://github.com/Hmbown/CodeWhale/issues/4184)**  
   *3 comments (CLOSED)* — A strategic pivot to align CodeWhale's model catalog with the Models.dev catalog used by OpenCode. Generated a family of dependent issues (#4185-#4188) for normalization, caching, and fallback behavior. Signals long-term convergence with ecosystem standards.

8. **[#3757 — v0.8.67: Launch is slow; profile and remove startup inefficiency](https://github.com/Hmbown/CodeWhale/issues/3757)**  
   *3 comments (CLOSED)* — A symptom-first performance report about slow TUI startup. Addressed by PR #3761 which defers non-critical maintenance (stale tool-output pruning, session cleanup) to a background thread. A good example of the project's responsive bug-to-fix cycle.

9. **[#3990 — v0.8.68 UX: slash autocomplete repeats aliases already shown](https://github.com/Hmbown/CodeWhale/issues/3990)**  
   *1 comment (CLOSED)* — A stopship-grade UX bug where `/p` shows `/clear or /qingping` then repeats `(aliases: /qingping)`. Fixed in PR #4254. The "stopship" lane label signals maintainer commitment to polish before release.

10. **[#4238 — v0.8.68: Make Android sandbox and secret-store behavior explicit](https://github.com/Hmbown/CodeWhale/issues/4238)**  
    *1 comment (CLOSED)* — Part of the Android/Termux support push. Ensures Termux doesn't advertise unsupported Linux Landlock/bwrap sandbox and that approval-gated tools work without OS keychain. Shows careful platform-gating philosophy.

## Key PR Progress

1. **[#4264 — v0.8.68: cache command and regex hot paths](https://github.com/Hmbown/CodeWhale/pull/4264)**  
   Merged. Introduces process-lifetime static caching for command groups, a bounded user-regex LRU cache, and `FastHashMap`/`FastHashSet` for internal maps. Fixes #4155 and #4154.

2. **[#4096 — docs + feat: sub-agent tool scoping plan and Phase 1 implementation](https://github.com/Hmbown/CodeWhale/pull/4096)**  
   Merged (by JayBeest). Three documentation files plus Phase 1 implementation for sub-agent tool scoping (#4042). Reflects a mature contributor relationship where users produce both analysis and code.

3. **[#4263 — v0.8.68 batch: Android updater, Termux docs, perf consts, sub-agent tool sandbox](https://github.com/Hmbown/CodeWhale/pull/4263)**  
   Merged. A multi-lane batch covering Android asset selection for updater (#4241), string constant extraction (#4158), and sub-agent tool sandbox compile guards. Clean example of batched milestone PRs.

4. **[#4225 — refactor(localization): extract hardcoded localization texts into locales files](https://github.com/Hmbown/CodeWhale/pull/4225)**  
   Merged (by hongqitai). Extracts hardcoded texts into `crates/tui/locales` with multi-language translations. Includes `tr` in tests for non-English devices. Welcome new contributor landing a significant infrastructure improvement.

5. **[#4262 — fix(fleet): route AgentProfile pins through custom providers](https://github.com/Hmbown/CodeWhale/pull/4262)**  
   Merged. Makes AgentProfile the canonical surface for per-child provider routing, including user-named OpenAI-compatible providers (LM Studio). Explicitly declines merging stale PR #3969 as-is — shows disciplined architecture decisions.

6. **[#3902 — perf(tui): fix the five render/input hot paths](https://github.com/Hmbown/CodeWhale/pull/3902)**  
   **OPEN** — Fixes #3896–#3900 with per-issue commits plus follow-ups for regressions found by adversarial multi-agent review. Not yet merged despite being open since July 2. The multi-agent review approach is notable for AI-native development.

7. **[#3761 — [codex] defer startup maintenance cleanup](https://github.com/Hmbown/CodeWhale/pull/3761)**  
   Merged (by nightt5879). Moves stale tool-output pruning and old session cleanup off the synchronous interactive path into a delayed maintenance thread. Fixes #3757. Demonstrates effective performance triage.

8. **[#4252 — feat(tui): six-view model picker catalog browsing](https://github.com/Hmbown/CodeWhale/pull/4252)**  
   Merged. Expands `/model` from two views to six: Configured, Catalog, Recent, Coding, Cheap, Long context. Cycle with `A` key. Implements #4115 and significantly improves model discovery UX.

9. **[#4243 — perf(tui): migrate runtime_threads maps to parking_lot::Mutex](https://github.com/Hmbown/CodeWhale/pull/4243)**  
   Merged (by wuisabel-gif). Migrates `RuntimeThreadManager` maps from `std::sync` to `parking_lot::Mutex`. New contributor claimed the issue and delivered — a model for onboarding.

10. **[#4251 — tui: make work_update the canonical progress tool](https://github.com/Hmbown/CodeWhale/pull/4251)**  
    Merged. Consolidates multiple progress reporting tools into a single `work_update` tool, keeping `checklist_*` and `todo_*` as hidden compat aliases. Simplifies the model-facing API surface.

## Feature Request Trends

1. **Sub-agent tool sandboxing and scoping** — Multiple issues (#4042, #4096) request granular control over which tools sub-agents can access. The community wants environment-level enforcement, not just documentation.

2. **Per-agent provider routing** — Users (#3965, #4262) want to assign different providers/models to individual sub-agents rather than inheriting the parent's provider. LM Studio and custom OpenAI-compatible endpoints are the flagship use case.

3. **Live model catalog integration** — A strong push (#4184, #4255, #4252) to replace curated model metadata with live Models.dev catalog, including refresh policies, normalization, and offline fallbacks. Tracks OpenCode alignment.

4. **Android/Termux support** — A new feature front (#4236–#4242) for official Android arm64 builds. Includes updater asset selection, Termux documentation, platform-specific sandbox gating, and QA matrices.

5. **Turn-level TUI inspection** — Requests (#4102, #4107) for a unified turn inspector that shows the complete agent reasoning loop, including LSP repair state, rather than separate leaf-level detail views.

## Developer Pain Points

1. **Project velocity overwhelm** — Issue #4227 ("help JayBeest keep up with the CodeWhale tsunami") explicitly calls out the 10+ PRs/day cadence. Even motivated contributors struggle to stay synced with `main`. Several PRs note "will rebase" or "held for sequencing."

2. **Configuration path confusion** — Issues #3986 and #4254 highlight that onboarding UX displays hardcoded paths (`~/.codewhale/config.toml`) even when `CODEWHALE_HOME` overrides them. Users in isolated/managed installs get misled.

3. **Sub-agent performance regressions** — Issue #4097 reports that parent agents fall into wasteful polling loops when waiting for sub-agents, a regression from earlier throttling work in #3183. The peek+sleep pattern burns model turns uselessly.

4. **Duplicate UI information** — Issue #3990 (alias duplication in slash autocomplete) and #3993 (Fleet setup wizard interleaved list rows) reflect recurring TUI rendering polish gaps that the "stopship" lane is systematically addressing.

5. **Multiple provider/model truth sources** — Issues #4184, #4188, and others note that CodeWhale currently maintains overlapping hand-curated model data alongside config hardcodes alongside bundled JSON. The community wants unification before adding more sources.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*