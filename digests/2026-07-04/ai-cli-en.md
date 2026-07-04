# AI CLI Tools Community Digest 2026-07-04

> Generated: 2026-07-04 01:59 UTC | Tools covered: 9

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

# AI CLI Tools Ecosystem: Cross-Tool Comparison Report — 2026-07-04

---

## 1. Ecosystem Overview

The AI CLI tool landscape is undergoing rapid maturation, characterized by a security-first pivot across major players. Claude Code and OpenAI Codex shipped urgent security patches this week (permission mode defaults, Git config isolation), while Gemini CLI and DeepSeek TUI are investing in agent architecture hardening. The community is converging around two technical themes: **subagent orchestration reliability** and **model compatibility fragility** as models evolve faster than tool integration layers. OpenCode and Pi demonstrate that the ecosystem is expanding beyond first-party tools into community-driven alternatives with multi-provider support. A clear tension exists between pushing autonomous agent capabilities and maintaining user trust through safety guardrails.

---

## 2. Activity Comparison

| Tool | Issues (24h) | PRs (24h) | Release Status |
|---|---|---|---|
| **Claude Code** | 50 updated, 10 hot | 7 (3 duplicates) | v2.1.200, v2.1.201 (patch releases) |
| **OpenAI Codex** | 10 hot | 10 active | Rust SDK alpha (no main app release) |
| **Gemini CLI** | 10 hot | 10 active | v0.51.0-nightly.20260704 |
| **GitHub Copilot CLI** | 10 hot | 0 | No new release |
| **OpenCode** | 10 hot | 10 active | No new release |
| **Pi** | 10 hot | 10 active | No new release |
| **Qwen Code** | 10 hot | 10 active | v0.19.6, cua-driver-rs v0.7.0 |
| **DeepSeek TUI** | 10 hot | 10 active | v0.8.67 RC (pre-release) |
| **Kimi Code CLI** | 0 | 0 | No activity |

**Key observations:**
- **Qwen Code** and **OpenCode** show highest PR velocity alongside high issue throughput
- **Claude Code** dominates in raw issue volume (50 updated) but has thin PR pipeline
- **GitHub Copilot CLI** has zero PR activity — a concerning signal for a widely-used tool
- **Kimi Code** is effectively dormant with zero activity

---

## 3. Shared Feature Directions

| Requirement | Affected Tools | Specific Needs |
|---|---|---|
| **Subagent lifecycle management** | Claude Code, Gemini CLI, OpenCode | Memory leaks on deep nesting, orphaned agents, max-turn success misreporting, cancellation UX |
| **Per-agent/provider routing** | OpenAI Codex, DeepSeek TUI, Claude Code | Route sub-agents to different models/providers (e.g., local LM Studio for simple tasks, cloud for complex) |
| **Session persistence & resume** | Claude Code, OpenAI Codex, Gemini CLI | Stale indexes, compaction data loss, WebSocket timeout without reconnect, cross-device sync |
| **Security hardening** | OpenAI Codex, Claude Code, Qwen Code | Git config isolation, worktree isolation safety, subprocess sandboxes, permission model defaults |
| **Model compatibility fixes** | Claude Code, Pi, Copilot CLI | Hallucinated tool keys, raw tag emission, null content crashes, streaming parser fragility |
| **Configuration discovery** | Claude Code, OpenCode | Settings resolved against cwd vs git root, env shadowing, provider auth persistence |
| **Multi-platform parity** | Claude Code, OpenAI Codex, Pi | Windows crashes, macOS permission fatigue, WSL auth hangs, Wayland browser agent failures |
| **Context compaction preservation** | OpenAI Codex, Pi | Dropped AGENTS rules, language-mismatched summaries, UX regressions in compaction checkpoints |

---

## 4. Differentiation Analysis

| Tool | Primary Focus | Target User | Technical Approach |
|---|---|---|---|
| **Claude Code** | Agent tree orchestration, Sonnet/Opus model integration | Power developers, Anthropic ecosystem | Deep model integration, `/config` system, subagent memory model |
| **OpenAI Codex** | Multi-model platform, security sandboxing | Enterprise, multi-provider workflows | Git patch safety, rate-limit transparency, Windows sandbox |
| **Gemini CLI** | Agent reliability, MCP ecosystem | Google Cloud developers, MCP adopters | Nightly releases, skills system, AGENTS.md default context |
| **GitHub Copilot CLI** | Familiar Copilot experience, VS Code integration | Mainstream GitHub developers | Minimal churn, alt-screen TUI, MCP pagination issues |
| **OpenCode** | V2 migration, billing/subscription UX | Community, multi-provider users | MCP lifecycle, form service, close-to-tray UX, Go subscription |
| **Pi** | Multi-provider flexibility, edit tool reliability | Tool reliability seekers, Claude/GPT users | Strict tool schemas, provider expansion (GLM, Azure), Zen mode |
| **Qwen Code** | Qwen model ecosystem, channel integration | QwenLM users, Chinese market | Daemon dashboard, WeCom/QQ integration, mobile session fixes |
| **DeepSeek TUI** | Constitution-first UX, per-subagent routing | Power users, privacy-conscious | Local-first, LM Studio support, dynamic MCP servers |

**Key differentiators:**
- **Claude Code** leads in agent tree complexity but struggles with memory management at scale
- **OpenAI Codex** is most advanced in security sandboxing (Git config validation, patch ops safety)
- **Pi** has the strongest edit tool reliability story with strict schema enforcement
- **DeepSeek TUI** is unique in its constitution-first security model and per-agent routing
- **Qwen Code** has the richest channel integration (QQ, WeCom, Web Shell)

---

## 5. Community Momentum & Maturity

**High Momentum (rapid iteration, high activity):**
- **Qwen Code** — Most active release schedule (2 releases + SDK in 24h), strong PR pipeline, active maintainer response
- **OpenCode** — High PR velocity, V2 migration signals long-term investment, billing bug cluster indicates growing paid user base
- **DeepSeek TUI** — Pre-release RC with 22+ closed items, clear roadmap to v0.8.68, strong maintainer engagement

**Established & Mature (stable but slower iteration):**
- **Claude Code** — High issue volume but thin PR pipeline; v2.1.x patch cycle suggests maintenance mode on core, cautious feature rollout
- **OpenAI Codex** — Security-focused PRs suggest enterprise hardening, but slower user-facing feature velocity

**Concerning Signals:**
- **GitHub Copilot CLI** — Zero PRs and unresolved high-severity Windows crash (#4026) since May suggests under-resourcing
- **Kimi Code CLI** — Complete inactivity — likely unmaintained or deprioritized
- **Gemini CLI** — Nightly releases show active development, but agent hang bugs (#21409, #25166) unresolved across multiple releases indicate fundamental reliability gaps

**Community Health:**
- **Highest community engagement** (by comment/upvote volume): Claude Code (#73125 with 110 comments), OpenAI Codex (#30224 with 68 comments)
- **Most responsive maintainers**: DeepSeek TUI (22+ issues closed in 24h), OpenCode (PRs merged daily)
- **Most polarized community**: Claude Code (AskUserQuestion timeout backlash), OpenAI Codex (GPT-5.5 model regression concerns)

---

## 6. Trend Signals

### Industry Trends from Community Feedback

1. **Agent safety is the #1 user concern.** The AskUserQuestion timeout debacle (Claude Code) and subagent permission bypass (Gemini CLI) demonstrate that shipping autonomous agent features without adequate user controls erodes trust rapidly. Expect **mandatory human-in-the-loop approval gates** to become industry standard.

2. **Model compatibility is a growing pain point.** Claude Opus 4.8 emitting raw tool tags, GPT-5.5 token clustering degrading reasoning, and Gemini agents ignoring custom skills all point to a widening gap between model capabilities and tool integration layers. **Four tools (Claude Code, Pi, Copilot CLI, Qwen Code) have active issues around model hallucination of tool schemas.** This suggests tool-call schema hardening is a systematic, cross-vendor problem.

3. **Subagent orchestration without garbage collection is unsustainable.** Multiple tools (Claude Code, Gemini CLI, OpenCode) report memory leaks, orphaned processes, and unrecoverable agent failures when users push beyond simple hierarchies. **Expect garbage collection and subagent lifecycle management to become a core architectural feature** — not just an edge case fix.

4. **Windows remains a second-class platform.** Unresolved crashes (Copilot CLI #4026, since May), path translation bugs (Codex WSL issues, Pi WSL login hangs), and rendering issues (OpenCode paste, Pi terminals) consistently plague Windows users despite significant market share.

5. **Local-first and multi-provider are converging.** DeepSeek TUI's per-agent routing to LM Studio, Pi's GLM/Azure provider additions, and OpenCode's multi-provider architecture signal that **users want to mix cloud and local models within the same workflow.** This is a strategic opportunity for privacy-conscious deployments.

6. **Billing/credit transparency is broken across the board.** OpenCode's Go subscription bugs, Codex's Exec quota drain during idle, and Claude Code's session cost projection contradictions all indicate that **usage-based pricing models lack the instrumentation and UX transparency users need to trust them.**

7. **MCP (Model Context Protocol) is becoming a standard integration surface.** Qwen Code's @ mention panel, DeepSeek TUI's dynamic MCP server infrastructure, and Copilot CLI's MCP pagination issues all point to MCP as the emerging ecosystem protocol for tool extensibility.

### Reference Value for Developers

- **If you're building AI-powered developer tools**, invest in **tool-call schema validation** (Pi's strict edit tool approach) and **configurable agent timeout approval** (Claude Code's rollback to opt-in).
- **If you're deploying agentic workflows in production**, prioritize **subagent lifecycle observability** (memory limits, orphan detection, cancellation UX) and **sandboxed execution** (Codex's Git config isolation, Qwen's subprocess isolation).
- **If you're choosing a CLI tool**, evaluate the **model compatibility track record** — tools with strict schema enforcement (Pi, Qwen Code) are better positioned for the current era of model volatility.
- **If you're supporting enterprise deployments**, **Windows parity** and **authentication persistence** (env shadowing, OAuth re-auth failures) remain unresolved gaps across nearly all tools.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)

# Claude Code Skills Community Highlights Report
**Data as of 2026-07-04** | Source: github.com/anthropics/skills

---

## 1. Top Skills Ranking

The following PRs have attracted the most community discussion and represent the most-watched Skill development activity:

### #1298 — fix(skill-creator): run_eval.py always reports 0% recall
**Status:** Open | [View PR](https://github.com/anthropics/skills/pull/1298) | Author: MartinCajiao

Fixes the foundational `run_eval.py` script that powers the description-optimization loop. The bug causes every skill description to score `recall=0%` regardless of content, making the optimization loop optimize against noise. Fixes include installing the eval artifact as a real skill, Windows stream reading, trigger detection, and parallel worker support. This PR directly addresses the most critical infrastructure bug in the skill-creator ecosystem.

### #1367 — feat(skills): add self-audit — mechanical verification + four-dimension reasoning quality gate
**Status:** Open | [View PR](https://github.com/anthropics/skills/pull/1367) | Author: YuhaoLin2005

Introduces a universal auditing skill that runs mechanical file verification (checking claimed output files exist) followed by a four-dimension reasoning audit in damage-severity priority order. Designed to work with any project, tech stack, or model. Discussion focuses on whether auditing should be a Skill or built into the Claude Code runtime, with strong community interest in output quality guarantees.

### #514 — Add document-typography skill
**Status:** Open | [View PR](https://github.com/anthropics/skills/pull/514) | Author: PGTBoos

Prevents orphan word wrap, widow paragraphs, and numbering misalignment in AI-generated documents. Addresses a universal pain point: typographic defects that appear in every document Claude generates. The discussion highlights demand for "polish" Skills that refine Claude's output after initial generation.

### #538 — fix(pdf): correct case-sensitive file references in SKILL.md
**Status:** Open | [View PR](https://github.com/anthropics/skills/pull/538) | Author: Lubrsy706

Fixes 8 case-sensitivity mismatches between SKILL.md and actual file names (e.g., `REFERENCE.md` → `reference.md`). While technically a bug fix, this PR has drawn attention because it exposes broader cross-platform compatibility issues — Linux users running Skills created on macOS hit silent failures.

### #486 — Add ODT skill — OpenDocument text creation and template filling
**Status:** Open | [View PR](https://github.com/anthropics/skills/pull/486) | Author: GitHubNewbie0

Provides ODT creation, template filling, and ODT-to-HTML conversion. Discussion reveals strong demand for LibreOffice/OpenDocument format support alongside the existing DOCX/PDF skills. Community members note that government and enterprise clients frequently require ODF formats.

### #723 — feat: add testing-patterns skill
**Status:** Open | [View PR](https://github.com/anthropics/skills/pull/723) | Author: 4444J99

Comprehensive testing skill covering the Testing Trophy model, unit testing (AAA pattern), React component testing (Testing Library), integration testing, E2E testing (Playwright, Cypress), and visual regression testing. Discussion highlights the need for a testing Skill that works across languages and frameworks, not just JavaScript ecosystems.

### #83 — Add skill-quality-analyzer and skill-security-analyzer to marketplace
**Status:** Open | [View PR](https://github.com/anthropics/skills/pull/83) | Author: eovidiu

Two meta-skills: one for evaluating Skill quality across five dimensions (Structure & Documentation, Coverage & Triggers, Actionability & Precision, Safety & Security, Efficiency), and one for security analysis. This PR has sparked debate about whether meta-analysis Skills should be in the main repository or a separate tools repository.

---

## 2. Community Demand Trends

From the most-commented Issues, the community's strongest demands are:

- **Skill-creator reliability (Critical):** Issues #556, #1169, and #1061 all describe the same fundamental bug — `run_eval.py` reports 0% recall on every query, making the description-optimization loop useless. This is the #1 blocker for the entire Skill development workflow, especially on Windows. *(7 👍, 12 comments)*

- **Enterprise skill sharing & governance:** Issue #492 (34 comments, 2 👍) exposes a trust boundary vulnerability — community Skills distributed under the `anthropic/` namespace could deceive users into granting elevated permissions. Issue #228 (14 comments, 7 👍) asks for org-wide skill sharing without manual file transfer. Together, these signal demand for enterprise-grade distribution and security controls.

- **Duplicate skill management:** Issue #189 (6 comments, 9 👍) reports that `document-skills` and `example-skills` plugins install identical content, wasting context window space. Community wants deduplication logic in the plugin system.

- **Multi-platform compatibility:** Issues #1061 and #184 highlight that Skills development tooling is effectively Linux-only. Windows users face subprocess PATHEXT issues, cp1252 encoding crashes, and broken `select` on pipes. Cross-platform reliability is a recurring demand.

- **Non-technical skill expansion:** Issues #1329 (compact-memory for agent state notation), #412 (agent-governance safety patterns), and the color-expert PR (#1302) show demand for Skills that address agent behavior and reasoning patterns, not just file format conversion.

- **Skills as MCPs:** Issue #16 proposes exposing Skills as MCP endpoints, signaling community desire for interoperability between Claude Code and the broader AI tool ecosystem.

---

## 3. High-Potential Pending Skills

These open PRs have active discussion and are likely to be merged soon:

| PR | Skill | Author | Last Updated | Key Strength | Link |
|---|---|---|---|---|---|
| #1367 | self-audit | YuhaoLin2005 | 2026-07-02 | Universal output quality gate; works with any project/model | [PR #1367](https://github.com/anthropics/skills/pull/1367) |
| #1302 | color-expert | meodai | 2026-06-12 | Comprehensive color naming, spaces, palettes, accessibility | [PR #1302](https://github.com/anthropics/skills/pull/1302) |
| #1323 | skill-creator trigger detection fix | Polluelo978 | 2026-06-25 | Fixes recall=0% by matching real skill names and handling non-Skill tools | [PR #1323](https://github.com/anthropics/skills/pull/1323) |
| #806 | sensory (macOS AppleScript automation) | AdelElo13 | 2026-04-02 | Native macOS automation without screenshot-based computer use | [PR #806](https://github.com/anthropics/skills/pull/806) |
| #723 | testing-patterns | 4444J99 | 2026-04-21 | Full testing stack coverage (unit through E2E, visual regression) | [PR #723](https://github.com/anthropics/skills/pull/723) |
| #509 | CONTRIBUTING.md (documentation) | narenkatakam | 2026-03-19 | Addresses community health gap (25% → improved score) | [PR #509](https://github.com/anthropics/skills/pull/509) |

The Windows compatibility fixes (#1298, #1099, #1050, #1323) and UTF-8 validation improvements (#362, #361) are critical infrastructure PRs that unblock all other Skill development on non-Linux platforms. Expect these to land first as they are preconditions for the ecosystem to grow.

---

## 4. Skills Ecosystem Insight

**The community's most concentrated demand is for a reliable, cross-platform skill-creator foundation** — the top 10 of 15 most-commented issues and 6 of 20 most-commented PRs are all Windows compatibility or eval-script bug fixes that collectively render the skill optimization loop non-functional on any platform, effectively stalling the entire Skill development pipeline until resolved.

---

# Claude Code Community Digest — 2026-07-04

---

## 1. Today's Highlights

Two patch releases (v2.1.200, v2.1.201) landed in the last 24 hours, addressing the controversial `AskUserQuestion` auto-continue behavior and refining Sonnet 5 session handling. The community remains highly active with 50 issues updated, including a massive 110-comment thread on the new `AskUserQuestion` 60-second timeout that shipped just two days ago — signaling a feature that shipped before it was fully configurable. Several critical subagent orchestration bugs were reported, pointing to growing pains as users push Claude Code's agent tree capabilities to their limits.

---

## 2. Releases

Two versions shipped in the last 24 hours:

**v2.1.201** — Small behavioral fix: Claude Sonnet 5 sessions no longer use the mid-conversation system role for harness reminders.

**v2.1.200** — Two significant changes:
- **`AskUserQuestion` dialogs no longer auto-continue by default.** Users must now explicitly opt into an idle timeout via `/config`. This is a direct response to the backlash from v2.1.198's default 60-second auto-select behavior.
- **Default permission mode changed to "Manual"** across CLI, `--help`, VS Code, and JetBrains. The flags `--permission-mode manual` and `"defaultMode": "manual"` are now the effective defaults, tightening the default security posture.

---

## 3. Hot Issues (Top 10 by Relevance)

### [#73125 — AskUserQuestion: "No response after 60s — continued without an answer"](https://github.com/anthropics/claude-code/issues/73125)
**110 comments | 353 👍 | Status: OPEN | Tags: bug, api:bedrock, platform:linux, area:tui, area:tools, platform:vscode**

The highest-velocity bug right now. Users across every platform report that `AskUserQuestion` auto-selects the default answer after 60 seconds of inactivity. This was shipped as default behavior in v2.1.198 and only made opt-in via `/config` in today's v2.1.200. Community anger is high — this is seen as a dangerous default that can silently approve unintended actions.

### [#74006 — Contradictory 'session limit resets at X' times; background subagents die terminally](https://github.com/anthropics/claude-code/issues/74006)
**6 comments | Status: OPEN | Tags: bug, platform:macos, area:cost, area:agents**

A deep investigation into Claude Fable 5 session accounting. The user documents contradictory cost-reset projections within a single session and reports that background subagents die silently without recovery. Points to a systemic issue in how the agent orchestrator manages subagent lifetimes and cost tracking.

### [#74035 — Deeply-nested subagent fan-out causes unbounded memory growth → host-level OOM](https://github.com/anthropics/claude-code/issues/74035)
**2 comments | Status: OPEN | Tags: bug, has repro, platform:linux, perf:memory, area:agents**

Notable because the report was **authored by Claude Code itself** via self-analysis after being OOM-killed. Deeply nested subagent trees don't release memory when branches complete, leading to host-level out-of-memory kills. A strong indicator that the subagent memory model needs garbage collection.

### [#70315 — Assistant hallucinates fake user/system turns with stop_reason=null (re-report, wrongly auto-closed)](https://github.com/anthropics/claude-code/issues/70315)
**12 comments | Status: OPEN | Tags: bug, has repro, platform:macos, area:model, area:core, platform:intellij**

A frustrating saga — the user's original report was auto-closed as a duplicate without resolution. The bug persists on Opus 4.8: the model fabricates fake conversation turns, making it unusable for some users. Highlights ongoing issues with the bot's duplicate-detection triage.

### [#74023 — .claude/settings.json resolves against literal cwd, not git root](https://github.com/anthropics/claude-code/issues/74023)
**3 comments | Status: OPEN | Tags: bug, has repro, platform:linux, area:core**

Subdirectory launches silently discard all project-level settings. If you `cd` into a subdirectory and launch Claude Code, your carefully crafted `.claude/settings.json` at the repo root is ignored. A sharp edge for monorepo users.

### [#74032 — Worktree isolation inflates spawned-shell env past ARG_MAX → E2BIG](https://github.com/anthropics/claude-code/issues/74032)
**1 comment | Status: OPEN | Tags: bug, has repro, platform:macos, area:agents, area:skills, area:agent-view**

After dispatching a subagent with `isolation: 'worktree'`, **every subsequent Bash call in the parent session fails** with `E2BIG: argument list too long`. Even `echo ok` breaks. The environment variable spillover is unrecoverable without a full restart.

### [#73487 — AskUserQuestion auto-selects default answer, no way to configure or disable](https://github.com/anthropics/claude-code/issues/73487)
**7 comments | 8 👍 | Status: OPEN | Tags: enhancement, platform:windows, area:tui**

Filed against v2.1.198, this issue captures the frustration that v2.1.200 partially addressed. The user explicitly asks for a disable option, which is now available via `/config` — but only after this issue was filed.

### [#74060 — Cloud web session (claude.ai/code) hangs indefinitely after initialization](https://github.com/anthropics/claude-code/issues/74060)
**1 comment | Status: OPEN | Tags: bug, area:claude-code-web, platform:web**

The web version of Claude Code appears broken for at least one user — initializes successfully but never responds to any message. Could indicate a server-side regression.

### [#74065 — Voice agent prompts incorrectly flagged by safety filters](https://github.com/anthropics/claude-code/issues/74065)
**0 comments | Status: OPEN | Tags: bug, platform:macos, area:model, needs-repro**

A user reports that simple prompt engineering for voice agents triggers safety guardrails. Minimal detail provided, but follows a pattern of false-positive safety flags seen in other recent issues.

### [#74063 — Opus 4.8 intermittently emits tool calls as literal text](https://github.com/anthropics/claude-code/issues/74063)
**0 comments | Status: OPEN | Tags: bug, platform:macos, area:model**

A concerning model-level bug: Opus 4.8 sometimes outputs raw `<invoke name="Read">` tags as visible text instead of executing them as tool calls. The model also emits corrupted prefix words ("court", "count", "course") before the raw tags. If widespread, this renders Opus 4.8 unreliable for agentic workflows.

---

## 4. Key PR Progress

### [#74021 — fix(security-guidance): allow null findings in StructuredOutput schema](https://github.com/anthropics/claude-code/pull/74021)
**OPEN | Author: sourabharsh**

A pragmatic fix: when the commit reviewer's model finds no vulnerabilities, it sometimes returns `null` instead of `[]`, causing a full retry cycle. This was observed across 31 review sessions. The change makes the schema accept `null`, saving a wasted turn.

### [#74010 — enhance(feature-dev): add system design patterns, edge cases, and operational context](https://github.com/anthropics/claude-code/pull/74010)
**OPEN | Author: sourabharsh**

Substantially expands the `code-architect` agent with three new reasoning steps: system design pattern analysis, edge case identification, and operational context mapping. This bridges the gap between high-level architecture prompts and concrete codebase implementation.

### [#74009 — fix(plugin-dev): use "asks to" in skill-development and plugin-settings descriptions](https://github.com/anthropics/claude-code/pull/74009)
**OPEN | Author: sourabharsh**

Completes a consistency sweep that missed two skill descriptions. A small but important fix for plugin authors relying on consistent skill metadata.

### [#42701 — fix init-firewall.sh crash from ipset when domain resolves to repeated IPs](https://github.com/anthropics/claude-code/pull/42701)
**CLOSED (merged) | Author: michaelkonecny**

Fixes a devcontainer launch failure. When `marketplace.visualstudio.com` resolves to duplicate IPs, `ipset` throws a non-zero exit. The fix adds `-exist` to `ipset` to handle duplicates gracefully.

### [#66854 — "toekn" (typo PR, unresolved)](https://github.com/anthropics/claude-code/pull/66854)
**OPEN | Author: apaimabong-design**

A stray PR with an empty description and a typo in the title. Has been open since June 10 with no activity. Unclear intent.

### [#73999 — fix(plugin-dev): use "asks to" in skill descriptions (closed duplicate of #74009)](https://github.com/anthropics/claude-code/pull/73999)
**CLOSED | Author: sourabharsh**

Original submission of the consistency fix, superseded by #74009.

### [#74007 — enhance(feature-dev): add system design patterns (closed duplicate of #74010)](https://github.com/anthropics/claude-code/pull/74007)
**CLOSED | Author: sourabharsh**

Original submission closed in favor of #74010.

**Note:** The PR list is thin today — only 7 items total, with 3 from the same author (sourabharsh) and 2 duplicates. Internal Anthropic contributors appear to be the primary PR authors visible in this window.

---

## 5. Feature Request Trends

The following feature directions are clearly emerging from the issue tracker:

**1. Linux Desktop Build (🔥 Hottest Request)**
Issue [#65697](https://github.com/anthropics/claude-code/issues/65697) hit **495 👍** and 51 comments before being closed — but it was marked `[invalid]` or otherwise unresolved, despite massive demand. The community clearly wants a native Linux desktop GUI for Claude, not just the CLI.

**2. Secrets Redaction & Security Hardening**
Multiple issues ([#65122](https://github.com/anthropics/claude-code/issues/65122), [#59296](https://github.com/anthropics/claude-code/issues/59296)) call for automated redaction of `.env`, `.ssh/*`, and other sensitive files when read by the Bash tool. Users are willing to contribute regex sets and test suites.

**3. Configurable AskUserQuestion Timeout**
Now partially addressed in v2.1.200, but [#73487](https://github.com/anthropics/claude-code/issues/73487) shows the feature shipped as opt-out (dangerous) before being switched to opt-in.

**4. Multi-Account Switching in Mobile ([#36151](https://github.com/anthropics/claude-code/issues/36151))**
**116 comments, 415 👍** — the most active feature request overall. Users with multiple Claude accounts (e.g., work + personal) want seamless switching without shared email workarounds.

**5. Cross-Branch Diff Comparison ([#23626](https://github.com/anthropics/claude-code/issues/23626))**
Users want Claude to diff against branches other than `main`, a staple workflow in trunk-based development.

**6. RISC-V Linux Binary Support ([#59813](https://github.com/anthropics/claude-code/issues/59813))**
A niche but growing request as RISC-V hardware becomes more available. Currently Claude Code only ships for x86_64 and arm64 Linux.

---

## 6. Developer Pain Points

**The AskUserQuestion Timeout Debacle**
The most visceral frustration this week. Shipping a 60-second auto-continue as *default* behavior was a trust-eroding move. The community interpreted this as: "Claude will silently proceed if you step away for a minute." v2.1.200's rollback to opt-in is positive, but the damage to user confidence is real.

**Subagent Orchestration Instability**
An alarming cluster of bugs around subagent management:
- Memory leaks from nested fan-out ([#74035](https://github.com/anthropics/claude-code/issues/74035))
- Orphaned "Running" subagents after parent completion ([#73916](https://github.com/anthropics/claude-code/issues/73916))
- Dead background agents with no recovery ([#74006](https://github.com/anthropics/claude-code/issues/74006))
- Worktree isolation breaking all subsequent shell execution ([#74032](https://github.com/anthropics/claude-code/issues/74032))

The subagent system was clearly designed for simple hierarchies, but users are pushing into deeply nested trees — and the runtime isn't handling it.

**Settings Resolution Disconnect**
[#74023](https://github.com/anthropics/claude-code/issues/74023) highlights that `.claude/settings.json` resolves against the literal `cwd`, not the git root. This means launching Claude Code from a subdirectory silently loses all project-level configuration — no warning, no fallback. A silent data-loss bug for monorepo developers.

**Model Reliability on Opus 4.8**
[#70315](https://github.com/anthropics/claude-code/issues/70315) (hallucinated conversation turns) and [#74063](https://github.com/anthropics/claude-code/issues/74063) (raw tool tag emission) suggest Opus 4.8 has regressed in agentic reliability. Users are reporting that the model cannot be trusted for autonomous workflows.

**macOS Permission Fatigue**
[#74064](https://github.com/anthropics/claude-code/issues/74064) captures a UX pain point: every Claude Code auto-update changes the binary path, causing macOS to re-prompt for Accessibility/Screen Recording permissions. This breaks headless automation setups and annoys desktop users.

**Bot-Triaged Issue Closures**
[#70315](https://github.com/anthropics/claude-code/issues/70315) and [#65122](https://github.com/anthropics/claude-code/issues/65122) both describe issues where a bot auto-closed valid reports as "duplicates" without proper resolution. The community is growing frustrated with automated triage that lacks context awareness.

**Session Resume Failures**
[#74043](https://github.com/anthropics/claude-code/issues/74043) (stale session index after directory changes) and [#74059](https://github.com/anthropics/claude-code/issues/74059) (`e.includes` crash on resume) indicate that session persistence — a core feature — has regressed in v2.1.x.

---

*Digest generated 2026-07-04 from github.com/anthropics/claude-code activity in the preceding 24 hours.*

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

# OpenAI Codex Community Digest — 2026-07-04

## Today's Highlights

The Codex community is facing two converging crises: GPT-5.5 shows signs of performance degradation due to token clustering at fixed boundaries, and a growing number of users report that the "X-OpenAI-Internal-Codex-Responses-Lite" header blocks GPT-5.5 entirely across multiple platforms. Meanwhile, the engineering team is shipping a substantial security hardening initiative, with six new PRs today focused on Git configuration isolation and patch operation safety. The community's loudest feature demand remains cross-device real-time session synchronization.

## Releases

- **rust-v0.143.0-alpha.35** — No detailed changelog was provided. This appears to be an upstream Rust SDK bump for the Codex CLI ecosystem.

## Hot Issues

1. **#30364 — GPT-5.5 reasoning-token clustering at 516/1034/1552**  
   *Impact: High* — A user discovered that GPT-5.5 responses are not uniformly distributed but cluster at fixed token boundaries (516, 1034, 1552). This pattern correlates with degraded reasoning-to-output ratios on complex tasks. With 53 upvotes and 37 comments, this has quickly become the week's most debated model-behavior issue.  
   🔗 https://github.com/openai/codex/issues/30364

2. **#30224 — "This model is not supported when using X-OpenAI-Internal-Codex-Responses-Lite"**  
   *Impact: Critical* — The most commented issue (68 comments) across all open items. Users on Plus subscriptions on Windows 11 cannot use the Responses-Lite header with GPT-5.5. Multiple duplicate issues (#30406, #30912, #30595) confirm the same error on macOS and CLI, suggesting a systematic auth-routing or model-gating bug.  
   🔗 https://github.com/openai/codex/issues/30224

3. **#20214 — Codex App freezes/stutters on Windows 11 Pro**  
   *Impact: High* — With 40 upvotes, this long-running performance issue (since April) remains unresolved. Users report stuttering even on AMD Ryzen 5 systems with 32 GB RAM. No workaround has emerged.  
   🔗 https://github.com/openai/codex/issues/20214

4. **#7291 — VSCode extension failed to revert changes**  
   *Impact: Medium* — A 7-month-old bug in the VS Code extension (v0.4.46) where Codex cannot undo applied edits. With 47 comments and 16 upvotes, this remains a significant trust issue for developers relying on Codex for iterative refactoring.  
   🔗 https://github.com/openai/codex/issues/7291

5. **#25792 — Context compaction forgets AGENTS rules (97% → 42% regression)**  
   *Impact: High* — When Codex automatically compacts long-session context, AGENTS rules are lost, causing task progress to jump backward. This is a serious reliability concern for multi-hour coding sessions.  
   🔗 https://github.com/openai/codex/issues/25792

6. **#30009 — apply_patch fails with Windows sandbox error**  
   *Impact: Medium* — File edits through the Windows sandbox fail consistently. Relevant given today's security PR pipeline — the sandbox is a critical safety boundary.  
   🔗 https://github.com/openai/codex/issues/30009

7. **#30137 — "significant reduction in intelligence. feels like gpt 5.5 got downgraded to 5.3"**  
   *Impact: High* — A Pro subscriber reports that GPT-5.5's reasoning quality dropped noticeably in late June. This aligns with the token-clustering findings in #30364 and suggests a possible model configuration regression.  
   🔗 https://github.com/openai/codex/issues/30137

8. **#26429 — Computer Use plugin disappears after Codex Desktop restart**  
   *Impact: Medium* — macOS users lose the Computer Use capability after restarting Codex. The plugin remains "unavailable" until a manual reconfiguration.  
   🔗 https://github.com/openai/codex/issues/26429

9. **#29413 — WSL workspace: node_repl rejects /mnt/c sandboxCwd before Chrome bootstrap**  
   *Impact: Medium* — A path-ordering issue on Windows + WSL where the node REPL environment breaks because the Chrome browser bootstrap hasn't completed. This affects developers using WSL-based workflows.  
   🔗 https://github.com/openai/codex/issues/29413

10. **#31054 — Codex Desktop consumes Exec quota while idle**  
    *Impact: Medium* — Users observed their Exec quota decreasing at ~1% intervals even when Codex Desktop is idle with no visible background activity. Quitting the app stops the drain. The community is watching for official confirmation.  
    🔗 https://github.com/openai/codex/issues/31054

## Key PR Progress

1. **#31070, #31071, #31072 — Git configuration authorization trilogy**  
   *Significance: High* — Three PRs from `bookholt-oai` that form the core of a Git security hardening effort. They validate primary config sources, authorize included paths (`include.path`, `includeIf`), and bind the validated config to the child process performing mutations. This prevents repository-controlled config injection during patch operations.  
   🔗 https://github.com/openai/codex/pull/31070  
   🔗 https://github.com/openai/codex/pull/31071  
   🔗 https://github.com/openai/codex/pull/31072

2. **#31069 — Bind Git configuration environment for patch operations**  
   *Significance: High* — Ensures that `GIT_CONFIG_GLOBAL`, `GIT_CONFIG_SYSTEM`, and related environment variables are consistent between validation and execution. Prevents per-process config drift attacks.  
   🔗 https://github.com/openai/codex/pull/31069

3. **#31058 — Retry model capacity errors**  
   *Significance: High* — Introduces structured retry logic for model-capacity HTTP 503 errors: three attempts with jittered 30s/2m/5m backoff. This improves resiliency during peak usage and is likely a response to the recent GPT-5.5 capacity issues.  
   🔗 https://github.com/openai/codex/pull/31058

4. **#30395 — Expose rate-limit reset credit details (app-server)**  
   *Significance: Medium* — Adds a v2 endpoint that returns available reset credits, their expiry times, and a method to consume a specific credit. This enables proper redemption UI in the client.  
   🔗 https://github.com/openai/codex/pull/30395

5. **#30488 — Show reset details in CLI redemption picker**  
   *Significance: Medium* — Companion to #30395. Users can now see exactly which reset credits they have, sorted by expiry date, before choosing one to redeem.  
   🔗 https://github.com/openai/codex/pull/30488

6. **#30854 — Block selected merge drivers before three-way patch application**  
   *Significance: Medium* — Prevents `git apply --3way` from running custom merge drivers or damaging unrelated staged work. Part of the broader patch safety initiative.  
   🔗 https://github.com/openai/codex/pull/30854

7. **#30850 — Block selected Git filters before staging patch paths**  
   *Significance: Medium* — Ensures that staged patch paths are exact file paths and cannot cause Git to recurse into unexpected directories or run repository-selected filters.  
   🔗 https://github.com/openai/codex/pull/30850

8. **#30982 — Allow extension-managed Apps authentication**  
   *Significance: Medium* — Enables VS Code or other IDE extensions to manage Codex App authentication tokens. This is foundational for deeper IDE integration.  
   🔗 https://github.com/openai/codex/pull/30982

9. **#30628 — Trust protected PowerShell parsers and reject untrusted wrappers**  
   *Significance: Medium* — On Windows, Codex now inspects the actual PowerShell binary before running commands, rejecting repository- or model-selected wrappers. This closes a command-injection vector.  
   🔗 https://github.com/openai/codex/pull/30628

10. **#30833 — Bind Git worktree helpers to a trusted executable**  
    *Significance: Medium* — Forces Codex to use a single absolute Git executable path validated outside the workspace, preventing PATH-based substitution attacks.  
    🔗 https://github.com/openai/codex/pull/30833

## Feature Request Trends

- **Real-time multi-device synchronization** (#31062): The top emergent request. Users want Codex App and CLI sessions to sync state (conversation history, active tasks, file edits) across devices without manual export/import.
- **Per-subagent model/provider selection** (#14039, 12 👍): Users want spawned subagents to use different models (e.g., cheap model for simple iterations, expensive model for complex reasoning) than the parent session.
- **Multi-repository workspace support** (#26338, 8 👍): App users need Codex to recognize and correctly operate across parent folders containing multiple independent Git repos.
- **Duplicate issue consolidation**: The community is frustrated by 5+ open issues describing the same "Responses-Lite model not supported" error. A single tracking issue with pinned resolutions would improve triage.
- **Rate-limit transparency**: Multiple issues request real-time quota usage dashboards within the app, not just the web Analytics page.

## Developer Pain Points

1. **GPT-5.5 reliability crisis**: Two distinct failure modes — token clustering degrading performance (#30364) and outright model rejection via Responses-Lite (#30224) — are eroding trust. Some users report GPT-5.5 now "feels like 5.3" (#30137).

2. **Windows sandbox fragility**: Path translation issues between WSL and Windows (`/mnt/c`), visible PowerShell windows during background polling (#26613), and `apply_patch` failures (#30009) make Windows a second-class platform.

3. **Context compaction data loss**: Long-running sessions are punished by compaction that drops AGENTS rules and resets task progress (#25792). This is a critical UX issue for agent-driven workflows.

4. **Quota drain ambiguity**: Unexplained Exec quota consumption during idle periods (#31054) and desynchronized usage counters between web and app (#23192) create uncertainty about what actions actually consume credits.

5. **Plugin availability after restart**: Computer Use (#26429) and Browser plugins (#25353) fail to re-register after Codex restart, requiring manual intervention. This breaks unattended/CI workflows.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>

**Subject:** Gemini CLI Community Digest – 2026-07-04

Here is the community digest for the Gemini CLI, based on the latest GitHub activity.

### 1. Today's Highlights

The primary focus this week is on **agent reliability and safety**, with several high-priority bugs concerning agent hangs, incorrect success reporting, and destructive command approval being actively tracked. A new nightly release (v0.51.0) is out, and the community is seeing significant movement on PRs targeting shell parameter expansion security and MCP resource routing fixes.

### 2. Releases

- **v0.51.0-nightly.20260704.gf7af4e518**: A new nightly release was published today.
    - **Full Changelog**: https://github.com/google-gemini/gemini-cli/compare/v0.51.0-nightly.20260703.gf7af4e518...v0.51.0-nightly.20260704.gf7af4e518

### 3. Hot Issues

1.  **#22323**: [BUG] Subagent recovery after MAX_TURNS is reported as GOAL success. The `codebase_investigator` subagent incorrectly reports `status: "success"` even after hitting the max turn limit without completing its analysis. This is a critical P1 bug that undermines the reliability of agent orchestration. (Comments: 9 | 👍: 2)
    - **Link**: https://github.com/google-gemini/gemini-cli/issues/22323

2.  **#21409**: [BUG] Generalist agent hangs forever on simple tasks like folder creation, requiring users to instruct the model to avoid using sub-agents. This is a P1 issue with high community upvotes, indicating a fundamental stability problem in the agent routing logic. (Comments: 7 | 👍: 8)
    - **Link**: https://github.com/google-gemini/gemini-cli/issues/21409

3.  **#25166**: [BUG] Shell command execution gets stuck with "Waiting input" after the command completes. This P1 core bug affects simple, non-interactive commands, causing the CLI to hang indefinitely and breaking the user's workflow. (Comments: 4 | 👍: 3)
    - **Link**: https://github.com/google-gemini/gemini-cli/issues/25166

4.  **#22186**: [BUG] The `get-shit-done` output hook causes the CLI to crash when printing the user summary. This P1 bug interrupts what should be the final output of a session. (Comments: 3 | 👍: 0)
    - **Link**: https://github.com/google-gemini/gemini-cli/issues/22186

5.  **#22093**: [BUG] Sub-agents are being run without permission since v0.33.0. Users who disabled agents are finding them activated automatically, raising significant privacy and security concerns. (Comments: 2 | 👍: 0)
    - **Link**: https://github.com/google-gemini/gemini-cli/issues/22093

6.  **#21983**: [BUG] The browser subagent fails on Wayland display servers. This P1 bug blocks a key agent feature for users on common Linux distributions. (Comments: 4 | 👍: 1)
    - **Link**: https://github.com/google-gemini/gemini-cli/issues/21983

7.  **#19873**: [ENHANCEMENT] Leverage model's bash affinity via zero-dependency OS sandboxing. This is a long-running P2 feature request to improve safety and performance by letting the model use native shell tools directly in a sandboxed environment. (Comments: 8 | 👍: 1)
    - **Link**: https://github.com/google-gemini/gemini-cli/issues/19873

8.  **#22745**: [ENHANCEMENT] Assess the impact of AST-aware file reads, search, and mapping. An EPIC to improve code understanding by using AST-aware tools to reduce turns, token usage, and improve navigation accuracy. (Comments: 7 | 👍: 1)
    - **Link**: https://github.com/google-gemini/gemini-cli/issues/22745

9.  **#21968**: [BUG] Gemini does not use custom skills and sub-agents enough. Users report that the model fails to autonomously leverage defined skills (e.g., for Git or Gradle) even when the task is highly relevant, severely limiting the extensibility of the CLI. (Comments: 6 | 👍: 0)
    - **Link**: https://github.com/google-gemini/gemini-cli/issues/21968

10. **#26522**: [BUG] Auto Memory retries low-signal sessions indefinitely. The memory extraction agent gets stuck in a loop re-processing sessions it has already decided are low-value, wasting API calls and slowing down the system. (Comments: 5 | 👍: 0)
    - **Link**: https://github.com/google-gemini/gemini-cli/issues/26522

### 4. Key PR Progress

1.  **#28247**: **fix(core): match ls ignore globs by relative path**. Fixes #28207 by ensuring ignore patterns like `**/build` correctly filter files in subdirectories. Important for accurate workspace visibility.
    - **Link**: https://github.com/google-gemini/gemini-cli/pull/28247

2.  **#28175**: **fix(policy): require confirmation for shell parameter expansion**. A security-focused PR that downgrades allow-listed commands with shell parameter expansion to require user confirmation, denying them outright in YOLO mode.
    - **Link**: https://github.com/google-gemini/gemini-cli/pull/28175

3.  **#28143**: **fix(core): resolve MCP resources by server to prevent cross-server confusion**. Fixes a critical bug where two MCP servers with identical resource URIs could return the wrong content, a key improvement for MCP interoperability.
    - **Link**: https://github.com/google-gemini/gemini-cli/pull/28143

4.  **#28178**: **fix(security): require approved bot patch artifacts**. Enhances CI/CD security by requiring an explicit approval marker before the CLI bot can apply a patch, creating a fail-closed pipeline.
    - **Link**: https://github.com/google-gemini/gemini-cli/pull/28178

5.  **#27971**: **fix(core): strip thoughts from scrubbed history turns**. Resolves a "Thought Leakage" issue where internal model monologues leaked into history, causing confusion and infinite loops in subsequent turns.
    - **Link**: https://github.com/google-gemini/gemini-cli/pull/27971

6.  **#28183**: **fix(vscode-ide-companion): preserve terminal focus when closing diff tabs**. A UX fix for the VS Code extension that restores focus to the integrated terminal after an edit is approved, improving workflow speed.
    - **Link**: https://github.com/google-gemini/gemini-cli/pull/28183

7.  **#28240**: **Fix #28227: add support for AGENTS.md out of the box**. Makes the `AGENTS.md` file a default context file, ensuring custom agent definitions are automatically recognized without manual configuration.
    - **Link**: https://github.com/google-gemini/gemini-cli/pull/28240

8.  **#28144**: **fix(cli): detect available editors lazily to avoid slow startup**. Fixes slow startup times on Windows by moving editor detection from module-scope instantiation to lazy loading.
    - **Link**: https://github.com/google-gemini/gemini-cli/pull/28144

9.  **#28149**: **fix(skills): respect .gitignore/.geminiignore in skill resource listing**. Ensures that when listing a skill's available resources, files ignored by `.gitignore` or `.geminiignore` are excluded, reducing noise for the model.
    - **Link**: https://github.com/google-gemini/gemini-cli/pull/28149

10. **#28140**: **fix(deps): patch shell command dependency advisories**. A proactive security update for `shell-quote` and `simple-git` dependencies used around shell command handling.
    - **Link**: https://github.com/google-gemini/gemini-cli/pull/28140

### 5. Feature Request Trends

The community is increasingly requesting **autonomous and intelligent agent behavior**. Key trends include:
- **Self-Awareness & Configuration**: Ensuring the agent knows its own capabilities, hotkeys, and flags to act as a self-guiding tool (e.g., `#21432`).
- **Sandboxed Execution**: Moving toward native shell command execution in a safe, sandboxed environment to reduce latency and improve model performance (`#19873`).
- **Intelligent Code Navigation**: Strong interest in AST-aware tools to improve the precision of code reading, searching, and mapping to reduce turn count and token waste (`#22745`, `#22746`).
- **Safety & Guardrails**: A clear push for the agent to recognize and avoid destructive operations (e.g., destructive `git` commands, direct database manipulation) (`#22672`).

### 6. Developer Pain Points

A recurring theme is **unreliable and unpredictable agent behavior**, which erodes developer trust:
- **Hangs & Crashes**: The generalist agent hanging (`#21409`), shell commands getting stuck (`#25166`), and hook crashes (`#22186`) are high-frequency, high-severity issues.
- **Poor Tool Utilization**: The model's failure to autonomously use user-defined skills and sub-agents (`#21968`) frustrates developers who have set up the system for specific workflows.
- **Configuration Ignorance**: The agent and sub-agents frequently ignore user-defined settings (e.g., `maxTurns`, disabled agents), leading to unexpected behavior (`#22267`, `#22093`).
- **Memory System Flaws**: The Auto Memory system has several bugs, including infinite retries on low-signal sessions (`#26522`) and insecure logging practices (`#26525`), indicating it is not yet production-ready.
- **Security & Context**: Users report concerns about sensitive information from subagent traces not being included in bug reports (`#21763`) and commands running without proper confirmation (`#22093`).

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

# GitHub Copilot CLI Community Digest — 2026-07-04

## Today's Highlights
The repository remains stable with no new releases in the last 24 hours, but issue activity has intensified as we enter July. A recurring crash on Windows (Issue #4026) has emerged as a top concern, while the community continues to push back against the alt-screen terminal rendering introduced months ago (Issue #1799). Several triage-stage bugs around MCP server integration, voice mode reliability, and session isolation suggest the CLI's expanding feature surface is introducing edge cases that need attention.

## Releases
No new releases in the last 24 hours.

## Hot Issues (Top 10)

1. **#1799 – How to turn off alt-screen views?** (OPEN, 11 comments, 👍7)  
   *[area:configuration, area:terminal-rendering]*  
   This long-running request reflects deep community frustration. The alt-screen mode, introduced months ago, still lacks an opt-out toggle. Users working in split terminals or CI-like environments find it disruptive.  
   [View Issue](https://github.com/github/copilot-cli/issues/1799)

2. **#3997 – Model "gpt-5.3-codex" is not available** (OPEN, 9 comments)  
   *[triage]*  
   A bug affecting Copilot Web's agent mode. Users are blocked from running code-generation tasks due to a server-side model routing error. Likely an upstream provisioning issue, but no workaround has been offered.  
   [View Issue](https://github.com/github/copilot-cli/issues/3997)

3. **#4026 – Copilot CLI crashes repeatedly on Windows** (OPEN, 0 comments, *just filed*)  
   *[triage]*  
   A native runtime crash affecting v1.0.15 through v1.0.53+ on Windows, unresolved since May 2026. Crashes are non-deterministic during normal use. High priority due to reproducibility across versions and lack of root cause.  
   [View Issue](https://github.com/github/copilot-cli/issues/4026)

4. **#1504 – Add custom theme support** (OPEN, 7 comments, 👍20)  
   *[area:theming-accessibility]*  
   The most-upvoted open feature request. Users want to define and share custom themes via JSON. The new `/settings theme` command (introduced in v1.0.69) has a related bug (#4015) where themes aren't persisted.  
   [View Issue](https://github.com/github/copilot-cli/issues/1504)

5. **#4024 – Voice mode: all bundled ASR models fail silently** (OPEN, 0 comments)  
   *[triage]*  
   `/voice` records audio but returns empty transcriptions for all three bundled speech models. Points to a routing bug in `MultiModalProcessor` for the `nemotron_speech` RNNT model. Blocks all speech-to-text functionality.  
   [View Issue](https://github.com/github/copilot-cli/issues/4024)

6. **#4016 – BYOK rejected in --acp mode** (OPEN, 0 comments)  
   *[area:authentication, area:non-interactive, area:models]*  
   A regression from v1.0.61–1.0.68 where custom providers configured via `COPILOT_PROVIDER_*` still require GitHub login in `--acp` mode. Previously fixed in #3048, now re-emerged. Critical for enterprise BYOK users.  
   [View Issue](https://github.com/github/copilot-cli/issues/4016)

7. **#4006 – MCP `tools/list` pagination not followed** (OPEN, 0 comments)  
   *[area:mcp]*  
   Copilot CLI ignores the `nextCursor` field in MCP `tools/list` responses, silently loading only the first page of tools. Violates MCP spec and breaks integrations with servers returning more than one page of tools.  
   [View Issue](https://github.com/github/copilot-cli/issues/4006)

8. **#4013 – macOS: Ctrl+V image paste fails with raw clipboard data** (OPEN, 0 comments)  
   *[area:input-keyboard]*  
   Ctrl+V is a no-op when clipboard contains raw image data (e.g., from SnagIt, Preview). Drag-and-drop works. A macOS-specific input handling gap that affects visual workflow users.  
   [View Issue](https://github.com/github/copilot-cli/issues/4013)

9. **#4010 – "Copied to clipboard" notification is misleading** (OPEN, 0 comments)  
   *[area:input-keyboard]*  
   On macOS (Ghostty terminal), mouse selection shows "Copied to clipboard" even when nothing is copied. Right-click then pastes stale content on the second click. A UX regression in clipboard interaction.  
   [View Issue](https://github.com/github/copilot-cli/issues/4010)

10. **#4020 – IDE auto-connect falsely skipped as "already in use"** (OPEN, 0 comments)  
    *[triage]*  
    After forking and closing a session, the original session cannot reconnect to the IDE — it believes the session is still claimed. Session lifecycle cleanup appears incomplete.  
    [View Issue](https://github.com/github/copilot-cli/issues/4020)

## Key PR Progress
No pull requests were updated in the last 24 hours.

## Feature Request Trends
- **Persistent / shareable themes** (#1504, #4015): The community wants user-defined themes stored reliably, with the ability to share JSON-based theme files.
- **Non-interactive `/init`** (#4011): Developers want to integrate `copilot init` into shell scripts and CI pipelines without hanging on interactive prompts.
- **Configurable scrolling / TUI ergonomics** (#4018): Mouse-wheel scroll speed in VS Code's integrated terminal is much faster than native shell — a sensitivity setting is requested.
- **Asynchronous read-only slash commands** (#3829): `/mcp show` and `/plugin list` only execute after an agent turn; users want them to run immediately like `/tasks`.
- **Headless agent tool resolution** (#4023): Category aliases like `web` or `search` silently resolve to no tool in `--agent` mode — users want explicit fallback or error messages.

## Developer Pain Points
- **Terminal rendering regressions** (#1799, #4009, #4010): Alt-screen lock-in, corrupted copy due to scrollbar glyphs, and spurious clipboard notifications are degrading the core TUI experience.
- **Voice / ASR not functional** (#4024): The `/voice` feature is effectively broken on Linux with all three bundled models, undermining a headline feature.
- **MCP integration gaps** (#4006, #2709): Pagination and plugin `.mcp.json` merging are both broken, meaning complex MCP toolchains don't load fully.
- **Session state bleeding** (#4025, #4020): Shared `session-state.json` causes cross-project history recall, and session cleanup doesn't release IDE connections.
- **Windows stability** (#4026, #3570, #4014): Unresolved native crashes, broken touch scrolling, and rendering corruption when adding MCP servers make the Windows experience unreliable.
- **Authentication regressions** (#4016): BYOK in `--acp` mode requires GitHub login despite being configured for custom providers — a recurring issue that erodes trust in enterprise deployment.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

No activity in the last 24 hours.

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

# OpenCode Community Digest — 2026-07-04

## Today's Highlights

The OpenCode community is buzzing with activity around V2 (2.0) infrastructure work, including MCP lifecycle APIs, session log determinism, and shell event alignment. Several high-severity subscription and billing bugs have surfaced, with multiple users reporting that paid "Go" subscriptions are not being recognized, causing false "free usage exceeded" errors. A long-standing bash-tool hang bug has finally seen two fix attempts, one merged and one still open.

## Releases

No new releases in the last 24 hours.

## Hot Issues

1. **[#35142 — Insufficient balance in free model](https://github.com/anomalyco/opencode/issues/35142)**  
   *39 comments | 👍 3*  
   User reports insufficient balance errors on the DeepSeek V4 Flash Free model. The issue includes garbled text suggesting a UI rendering problem alongside the billing error. High comment volume indicates many users are hitting similar credit limits unexpectedly.

2. **[#30086 — High CPU usage in newer versions](https://github.com/anomalyco/opencode/issues/30086)**  
   *15 comments | 👍 8*  
   CPU usage spiked dramatically in recent updates, degrading performance from 10 concurrent sessions to just 3. The most upvoted open issue this week, affecting users with multiple active workflows.

3. **[#13626 — Auto-sync projects in web UI from server](https://github.com/anomalyco/opencode/issues/13626)**  
   *10 comments | 👍 8*  
   Long-standing feature request (since Feb) asking for automatic project sync when opening OpenCode Web on a new device. Still unresolved, gaining steady traction.

4. **[#26038 — `/exit` in PowerShell closes the terminal](https://github.com/anomalyco/opencode/issues/26038)**  
   *9 comments | 👍 2*  
   `/exit` command bleeds through to close the PowerShell host instead of just the OpenCode session. A dangerous UX foot-gun for Windows users.

5. **[#33696 — GitHub Copilot provider broken](https://github.com/anomalyco/opencode/issues/33696)**  
   *8 comments | 👍 5*  
   After re-authentication, no models are found and the provider fails silently. Impacts a large user base reliant on Copilot as a provider backend.

6. **[#12219 — OpenRouter credit/token limit errors on Kimi 2.5 Free](https://github.com/anomalyco/opencode/issues/12219)**  
   *7 comments | 👍 6*  
   Users requesting 32K tokens on a free model with zero available credits receive unhelpful error messages. The community wants better error messaging and default token budgeting.

7. **[#35215 — Go models not working after update](https://github.com/anomalyco/opencode/issues/35215)**  
   *4 comments | 👍 0*  
   Paid subscription models stopped working post-update with "Upstream request failed" from Console Go. Coupled with #35191 and #35252, this is a **critical billing bug cluster**.

8. **[#35191 — Go subscription active but "Free Usage Exceeded"](https://github.com/anomalyco/opencode/issues/35191)**  
   *2 comments | 👍 0*  
   Identical theme: paid subscribers are incorrectly blocked. API key and provider connection appear correct, but app rejects usage.

9. **[#35252 — Go subscription not working (refund request)](https://github.com/anomalyco/opencode/issues/35252)**  
   *1 comment | 👍 0*  
   User explicitly requests a refund due to multi-day Go subscription outage. Signals escalations risk.

10. **[#25664 — `pkill -f` command causes tool call hang](https://github.com/anomalyco/opencode/issues/25664)**  
    *2 comments | 👍 5*  
    Renamed processes with `-f` flag hang bash tool calls until timeout. Now has a fix in review (#35241/#35245).

## Key PR Progress

1. **[#35247 — feat(tui): compact shell progress output](https://github.com/anomalyco/opencode/pull/35247)**  
   *Merged* — Replaces raw terminal redraw spam with compact TUI progress bars during shell commands. A major UX win for long-running operations.

2. **[#35241 — fix(shell): three timeouts and an exit fallback for bash tool hang class](https://github.com/anomalyco/opencode/pull/35241)**  
   *Merged* — Fixes the `pkill -f` hang (#25664) by not waiting on Node's `close` event for forked grandchildren. Three-layer timeout plus exit fallback.

3. **[#35245 — fix(shell): bound bash-tool hangs via scope teardown](https://github.com/anomalyco/opencode/pull/35245)**  
   *Open* — Alternative approach to #35241, uses scope teardown instead of multiple timeouts. Still under review.

4. **[#35235 — refactor(core): step ledger and classified settlement](https://github.com/anomalyco/opencode/pull/35235)**  
   *Merged* — Behavior-preserving refactor of the V2 runner's settlement system. All 144 runner-adjacent tests pass with zero logic changes. Foundation for upcoming V2 features.

5. **[#35259 — feat(desktop): add close-to-tray behavior](https://github.com/anomalyco/opencode/pull/35259)**  
   *Open* — Windows/Linux: closing the last window hides to system tray instead of quitting. Includes tray menu with Show/Quit actions.

6. **[#35257 — fix(desktop): match rounded window background](https://github.com/anomalyco/opencode/pull/35257)**  
   *Open* — Syncs Electron native window background with app theme to fix white corners on rounded Windows windows. Includes Playwright regression test.

7. **[#35232 — feat(core): wire execute tool for V2 MCP](https://github.com/anomalyco/opencode/pull/35232)**  
   *Open* — Adds V2 core execute tool backed by CodeMode over MCP, making execute the default MCP exposure path. Supports child call metadata preservation.

8. **[#35222 — fix: surface task_id in interrupted tool error text](https://github.com/anomalyco/opencode/pull/35222)**  
   *Open* — Persists and surfaces sub-agent task IDs in error text so LLMs can resume aborted sub-agents. Critical for agentic reliability.

9. **[#35237 — feat(console): enforce 10MB request body limit on Zen API](https://github.com/anomalyco/opencode/pull/35237)**  
   *Open* — Caps Zen API request bodies at 10MB to prevent resource exhaustion. Includes chunked request counting.

10. **[#35189 — feat(tui): render forms and route question tool through form service](https://github.com/anomalyco/opencode/pull/35189)**  
    *Open* — First client consumer of the new V2 Form service. Migrates `QuestionTool` onto structured forms, improving interactive UX for user prompts.

## Feature Request Trends

- **V2 Migration Completion** — Multiple issues (#34435, #35018, #35015) focus on porting MCP lifecycle, session log determinism, and shell event alignment to the V2 architecture. The core team is methodically plugging V1 gaps.
- **Subscription/credit UX** — The cluster of Go subscription bugs (not recognized, false exceeded errors) suggests a systemic billing validation issue. Users want transparent credit display and clear error messaging.
- **Ecosystem Expansion** — Requests to add community tools like `oh-my-loop` (#35251, #35075) to the ecosystem docs are active. The plugin/ecosystem directory is becoming a distribution channel.
- **Human-in-the-Loop Controls** — #35239 proposes a HITL approval gate after plan composition, allowing users to review plans before execution. Reflects demand for safer autonomous agents.
- **Web UI Feature Parity** — #13626 (auto-sync), #22925 (async prompt message IDs) show the web UI still lags behind TUI and desktop in key workflow capabilities.

## Developer Pain Points

1. **Bugs causing model/credit lockout** — Multiple users with paid Go subscriptions are unable to use the product at all (#35215, #35191, #35252). This is the highest-severity cluster, with a refund request already filed.
2. **Inconsistent provider authentication** — GitHub Copilot provider (#33696) and custom ESM providers on Electron (#31909) fail after clean auth flows. Devs report configuration burnout.
3. **Bash tool instability** — The `pkill -f` hang (#25664) was finally fixed (#35241), but the issue underscores persistent fragility in shell tool process management.
4. **Windows-specific UX regressions** — Pasting broken (#35258), `/exit` closes terminal (#26038), rounded corners mismatch (#35257). Windows users face a degraded experience vs. macOS/Linux.
5. **Credit/token management opacity** — Free model users hit "insufficient balance" (#35142) and "request requires more credits" (#12219) without clear path to resolution. Better defaults and error messaging are needed.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>

# Pi Community Digest — 2026-07-04

## Today's Highlights
The community is converging on two major themes: **tool reliability** and **model compatibility**. A flurry of fixes landed for the edit tool's struggles with newer Claude models, while persistent issues around OpenAI Codex connection stability and dependency resolution during updates continue to frustrate users. The ecosystem also saw strong contributions around new provider integrations (GLM, DeepInfra) and a major PR to harden tool-call argument parsing.

---

## Releases
No new releases in the last 24 hours.

---

## Hot Issues (Top 10)

1. **[#4945 — openai-codex Connection Reliability Issues](https://github.com/earendil-works/pi/issues/4945)**  
   *73 comments, 30 👍*  
   Long-running issue where `gpt-5.5` leaves the TUI stuck on `Working...` with no output or error. Only recovery is pressing Escape. Community frustration is high—this has been open since May.

2. **[#6215 — pi update fails on 0.80.3 due to missing @smithy/node-http-handler@^4.9.1](https://github.com/earendil-works/pi/issues/6215)**  
   *22 comments*  
   A dependency resolution failure blocking upgrades to 0.80.3. PNPM's registry metadata becomes stale; PR #6279 now adds a `pnpm store prune` hint in the error path.

3. **[#6187 — Pi login hangs in WSL after browser-based device authorization](https://github.com/earendil-works/pi/issues/6187)**  
   *15 comments*  
   WSL users cannot complete Copilot login—device authorization confirms in browser but the terminal never detects it. A frustrating cross-platform gap.

4. **[#6278 — New Claude models fail ~20% of edits with hallucinated extra keys](https://github.com/earendil-works/pi/issues/6278)**  
   *12 comments*  
   Sonnet 5, Fable 5, Opus 4.8 emit extra fields like `new_text_x`, `type`, `closeenough` in edit tool calls. Critical UX bug; already fixed by PR #6283.

5. **[#5501 — Tolerate extra keys on edit tool edits[] items](https://github.com/earendil-works/pi/issues/5501)**  
   *10 comments*  
   Prior proposal to drop `additionalProperties: false` on edit schema. Resurfaced because #6278 proves models will keep inventing keys; this schema hardening is now urgent.

6. **[#6157 — Compaction summary should be in the session's language](https://github.com/earendil-works/pi/issues/6157)**  
   *4 comments*  
   Non-English sessions get compaction checkpoints with English headers like `## Goal`. Small but impactful localization UX improvement.

7. **[#6239 — HTTP 524 (Cloudflare timeout) should be retryable](https://github.com/earendil-works/pi/issues/6239)**  
   *3 comments*  
   Proxied Anthropic API calls hit Cloudflare 524 timeouts, but Pi doesn't retry. Session abortion vs. graceful retry is causing data loss for proxy users.

8. **[#6238 — supportsDeveloperRole: false ignored in v0.80.3](https://github.com/earendil-works/pi/issues/6238)**  
   *3 comments*  
   Upgrade regression: custom `openai-completions` providers with `"supportsDeveloperRole": false` now send `role: "developer"` anyway. Breaks API backends that reject developer role.

9. **[#6268 — Codex websocket terminates after 60 minutes, does not retry](https://github.com/earendil-works/pi/issues/6268)**  
   *3 comments*  
   Long-running Codex tasks hit a hard 60-minute WebSocket limit with no auto-reconnect. The session just stops.

10. **[#6259 — 'content is not iterable' when reasoning models return null content during tool use](https://github.com/earendil-works/pi/issues/6259)**  
    *3 comments*  
    GLM-5.2 and similar reasoning models return `content: null` when emitting `reasoning_content` + `tool_calls`. Causes crashes across compaction and rendering. Related to #6276.

---

## Key PR Progress (Top 10)

1. **[#6294 — Improve pi config add-ons UX](https://github.com/earendil-works/pi/pull/6294)**  
   *louis030195*  
   Reworks `pi config` around an Add-ons mental model with package-level toggles, detail panes, and subagent model-fit guidance. A significant UX modernization.

2. **[#6292 — Fix Cloudflare account ID resolution for key-only credentials](https://github.com/earendil-works/pi/pull/6292)**  
   *markphelps*  
   Addresses #6021's root cause: Cloudflare Workers AI still returned 404 because account ID wasn't resolved from ambient env when only API key was provided.

3. **[#6290 — Use "(no tool output)" placeholder for empty tool results without images](https://github.com/earendil-works/pi/pull/6290)**  
   *tzwm*  
   Fixes model hallucination: previously, empty tool results (e.g., `grep` with no matches) were replaced with `"(see attached image)"`, causing the model to imagine images.

4. **[#6285 — Stop salvaging malformed tool-call argument JSON](https://github.com/earendil-works/pi/pull/6285)**  
   *mitsuhiko*  
   A major correctness fix: malformed tool-call arguments are now preserved as `malformedArguments` with `{}` fallback instead of being silently repaired. Invasive but important.

5. **[#6283 — Strip hallucinated extra keys from edit tool edits[]](https://github.com/earendil-works/pi/pull/6283)**  
   *legacy7838-create*  
   Fixes #6278: strips invented keys like `newText_x`, `type`, `closeenough` from edit calls. Quick fix for the immediate crisis with new Claude models.

6. **[#6279 — Add pnpm self-update prune hint](https://github.com/earendil-works/pi/pull/6279)**  
   *rajp152k*  
   Fixes #6215: adds a `pnpm store prune` hint to the update failure path, helping users recover from stale registry metadata in pnpm.

7. **[#6266 — Anthropic: strict tool use for the edit tool](https://github.com/earendil-works/pi/pull/6266)**  
   *pasky*  
   Implements strict tool-use schema enforcement for Claude. Reduces edit failure rate from ~10% to near-zero by constraining the tool definition more tightly.

8. **[#6273 — Add Zen mode tool call labels](https://github.com/earendil-works/pi/pull/6273)**  
   *WilsonLe*  
   New `/settings` toggle for compact tool-call labels in the TUI. Uses GPT-5.4-mini for async, non-blocking summarization of tool calls. A power-user productivity feature.

9. **[#6271 — Add GLM API provider](https://github.com/earendil-works/pi/pull/6271)**  
   *hututuQQQ*  
   First-class support for Z.AI and Zhipu AI GLM endpoints (`glm` and `glm-cn`), sharing the `ZAI_API_KEY` credential. Grows the provider ecosystem significantly.

10. **[#3799 — Add Azure Cognitive Services as provider](https://github.com/earendil-works/pi/pull/3799)**  
    *marcbloech*  
    Long-standing PR (since April!) adding support for `*.cognitiveservices.azure.com` URLs alongside existing `*.openai.azure.com`. Finally merged.

---

## Feature Request Trends

The most-requested feature directions visible across this week's issues:

1. **Provider Expansion** — Multiple requests for new built-in providers: Kimi K2.7 under Copilot (#6256), DeepInfra (#6270), GLM (#6271). Users want easy access to the latest models without manual config.

2. **Session UX Improvements** — AI-generated session titles (#6209), named exit resume hints (#6296), active tool visibility in TUI footer (#6277). The community wants richer session metadata and glanceable context.

3. **Multi-Account Credential Management** — #2976 requests automatic credential rotation for Google providers. Interest in enterprise-grade API key management is emerging.

4. **Sandbox Hardening** — Issues #6299, #6298, #6297 from a single contributor detail VM egress defaults, untrusted subagent hardening, and filesystem sandbox completeness. Signals demand for security-aware multi-tenant deployments.

5. **Agentic Loop Resume Without Sending a Message** — #3721 asks for the ability to resume an interrupted agent loop without sending a new user message that influences the model's output. A nuanced UX request for power users.

---

## Developer Pain Points

1. **Tool Reliability Degradation with Newer Models** — Both Claude and GPT models are increasingly failing with the edit tool (#6278, #5501, #6015). The root cause: models hallucinate extra keys or malformed arguments. Fixes are landing but the trend is worrying.

2. **Dependency Resolution Blocking Updates** — #6215 shows pnpm's stale registry metadata can completely block `pi update`. Workaround (`pnpm store prune`) is only now being documented.

3. **Cross-Platform Authentication Issues** — WSL users (#6187) and WebSocket timeout victims (#6268) face show-stopping login and session interruptions that are platform-specific and hard to debug.

4. **Null/Undefined Content Crashes** — Multiple issues (#6259, #6276, #6290) stem from code paths that assume `message.content` is always an array or always non-null. Reasoning models and empty tool results trigger unguarded iterations, causing hard crashes.

5. **Provider Configuration Regressions** — #6238 (developer role override ignored) and #6239 (non-retryable 524) are regression bugs introduced in 0.80.3 that break custom provider setups.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>

# Qwen Code Community Digest — 2026-07-04

## Today's Highlights
The team shipped **v0.19.6** with mobile session-switch fixes and a **cua-driver-rs v0.7.0** with relative-coordinate support. A major CI reliability issue (autofix branch switching) was identified and is being actively patched. Community attention is focused on context window miscalculation, streaming tool-call drops, and several new feature requests for daemon UI dashboards and WeCom integration.

## Releases
- **[v0.19.6-nightly.20260704.5dc2e1501](https://github.com/QwenLM/qwen-code/releases/tag/v0.19.6-nightly.20260704.5dc2e1501):** Strengthened PR gate with batch detection, problem existence check, and red flag patterns.
- **[v0.19.6](https://github.com/QwenLM/qwen-code/releases/tag/v0.19.6):** Fixed mobile session-switch jank in web-shell (memoized timeline signature, replay-first dispatch) and resolved a macOS seat issue.
- **[cua-driver-rs-v0.7.0](https://github.com/QwenLM/qwen-code/releases/tag/cua-driver-rs-v0.7.0):** Prebuilt binaries with relative-coordinate fork support for macOS (codesigned universal binary), Linux (x86_64 + arm64), and Windows (x86_64 + arm64). Enable via configuration.

## Hot Issues (Top 10)

1. **[#6144 — Incorrect context window calculation](https://github.com/QwenLM/qwen-code/issues/6144)**  
   A user reports Qwen-Code miscalculates the available context window for a Qwen3-Coder instance configured with 64K tokens. Community engagement is high (6 comments, 1 👍). This is a core reliability issue affecting advanced model configurations.

2. **[#6265 — tool_search invalidates KV-cache on deferred-tool load](https://github.com/QwenLM/qwen-code/issues/6265)**  
   A performance bug where `tool_search` triggers three operations that break KV-cache continuity, causing unnecessary recomputation. Welcome for PRs.

3. **[#6264 — /review skill consumes excessive tokens](https://github.com/QwenLM/qwen-code/issues/6264)**  
   Users report token usage spikes during `/review` sessions. The issue includes screenshots showing high token consumption; community suspects prompt bloat.

4. **[#6249 — Streaming tool calls with empty arguments silently dropped](https://github.com/QwenLM/qwen-code/issues/6249)**  
   Critical bug for OpenAI-compatible providers: empty `function.arguments` strings are dropped, causing retry loops with "Model stream ended with empty response text." This affects all parameterless tool calls.

5. **[#6281 — Autofix review-address fails to switch branches after build changes](https://github.com/QwenLM/qwen-code/issues/6281)**  
   CI pipeline issue: `Qwen Autofix` cannot switch branches when build artifacts (e.g., NOTICES.txt) are modified. Blocks automated fixes; an autofix is in progress.

6. **[#6230 — QuickPick dropdowns lose focus during /auth process](https://github.com/QwenLM/qwen-code/issues/6230)**  
   UX bug in VS Code: losing focus during OAuth quickpick resets the entire configuration flow. Force users to re-enter settings. Fixed in PR #6274.

7. **[#6283 — settings.env values silently shadowed by .env files](https://github.com/QwenLM/qwen-code/issues/6283)**  
   Environment loading order issue: `.env` files override `settings.env` on restart, causing API keys to not persist. Under review with a fix in PR #6284.

8. **[#6246 — Cannot recognize its own child processes](https://github.com/QwenLM/qwen-code/issues/6246)**  
   When asked to stop a Node.js process, Qwen Code kills *all* Node.js processes including itself. Process ownership detection is missing.

9. **[#6244 — Extension capability changes not reliably communicated to the model](https://github.com/QwenLM/qwen-code/issues/6244)**  
   When extensions are enabled/disabled mid-session, the model doesn't always learn about new tools or lost capabilities, causing hallucinated tool calls.

10. **[#6282 — transform_data does not enforce subprocess isolation](https://github.com/QwenLM/qwen-code/issues/6282)**  
    Security finding: the `transform_data` handler lacks filesystem/network isolation wrappers despite its documentation promising isolated execution. P1 priority.

## Key PR Progress (Top 10)

1. **[#6273 — Model fallback chain](https://github.com/QwenLM/qwen-code/pull/6273)**  
   Adds configurable fallback to backup models on capacity/availability errors, preserving retry logic. Essential for production reliability.

2. **[#6284 — Fix persistent 401 after API key change](https://github.com/QwenLM/qwen-code/pull/6284)**  
   Fixes three edge cases: empty-string env vars, incorrect load order, and stale cached auth. Directly addresses #6283.

3. **[#6272 — Daemon status page](https://github.com/QwenLM/qwen-code/pull/6272)**  
   New Web Shell dashboard showing `GET /daemon/status` with health badge, triage list, and runtime information. CLOSED and merged.

4. **[#6225 — Preserve tools prefix in side-query for Anthropic cache hits](https://github.com/QwenLM/qwen-code/pull/6225)**  
   Performance fix for Anthropic API: keeps the `tools` array identical across side-queries to avoid guaranteed cache misses.

5. **[#6242 — Custom @ mention panel for web-shell](https://github.com/QwenLM/qwen-code/pull/6242)**  
   Replaces inline autocomplete with a multi-level reference panel supporting files, extensions, and MCP resources with keyboard navigation.

6. **[#6232 — ECharts full data blocks in web-shell](https://github.com/QwenLM/qwen-code/pull/6232)**  
   Adds compact `echarts-fulldata` envelope with dataset, options, and data ref resolution for large artifacts. Enables visual chart rendering.

7. **[#6278 — Multi-folder workspace support for file boundaries](https://github.com/QwenLM/qwen-code/pull/6278)**  
   Extends `resolveWithinWorkspace` to handle VSCode multi-folder workspaces, fixing `path_outside_workspace` errors.

8. **[#6204 — QQ Bot streaming with idle-flush and tool-call protection](https://github.com/QwenLM/qwen-code/pull/6204)**  
   Adds streaming infrastructure to the QQ channel adapter with buffering, coordination, and stale-callback protection.

9. **[#6288 — Treat request timeout of 0 as disabled](https://github.com/QwenLM/qwen-code/pull/6288)**  
   Makes `generationConfig.timeout: 0` disable the timeout entirely instead of aborting immediately, matching existing idle timeout behavior.

10. **[#6238 — Stop-hook continuations get fresh tool-call budget](https://github.com/QwenLM/qwen-code/pull/6238)**  
    Each blocking Stop-hook iteration now gets its own per-turn budget and the cap is configurable, fixing `/goal` loop exhaustion.

## Feature Request Trends
- **Daemon & Dashboard UI**: Multiple requests for richer daemon visualization (#6252 — status dashboard, #6195 — vision bridge model selector). The merged #6272 is an immediate response.
- **Channel Integration**: Strong community interest in WeCom (WeChat Enterprise) channel (#6208) and QQ Bot streaming improvements.
- **Visual Chart Rendering**: Requests for pluggable chart rendering in markdown output (#6226, #6232) — likely driven by data analysis workflows.
- **Configuration & Extensibility**: Making hardcoded limits configurable (e.g., cron job expiration #6167, tool-call budget #6238, request timeout #6288).
- **Process & Sandbox Improvements**: Better process ownership detection (#6246) and security isolation (#6282) are emerging concerns.

## Developer Pain Points
1. **Context window miscalculation** (#6144) — undermines trust in model configuration accuracy.
2. **Empty response retry loops** (#6249, #3804) — streaming parser fragility wastes tokens and frustrates users.
3. **Authentication persistence failures** (#6283, #6230, #6251) — API keys and OAuth sessions fail across restarts or focus changes.
4. **CI/CD brittleness** (#6281, #6199) — build artifacts and secret detection break automated release pipelines.
5. **Tool state management** (#5894, #6244, #6237) — tool results leak across responses, and extension changes aren't reflected to the model.
6. **Token efficiency** (#6264, #5939) — `/review` and other skills consume unexpectedly large token budgets without clear culprit.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>

# DeepSeek TUI Community Digest — 2026-07-04

## Today's Highlights

The community is in the final push for **v0.8.67**, with the maintainer closing 22+ issues and PRs in the last 24 hours alone. The release focuses on a **constitution-first setup wizard**, multi-provider routing, and UX hardening. Meanwhile, a critical **sub-agent failure** regression on OpenAI Codex was resolved, shifting attention to v0.8.68 roadmap items like debugger protocol support, per-project memory, and the long-requested **per-sub-agent provider routing**.

---

## Releases

**No new releases in the last 24 hours.** The project is currently between v0.8.67 RC and final release. Users are advised to build from `main` or use the `codewhale update` mechanism for the latest fixes.

---

## Hot Issues

1. **#3965 – Per-sub-agent provider assignment (explicit routing) + LM Studio support**  
   *Author: JayBeest | Open | Comments: 7*  
   An active user proposes a natural extension of the v0.8.67 multi-provider work: route specific sub-agent roles (e.g., `explore`, `format`) to specific providers like local LM Studio. This is **the most upvoted community feature request** and has already spawned a PR (#3969).  
   [🔗 Issue #3965](https://github.com/Hmbown/CodeWhale/issues/3965)

2. **#3275 – CodeWhale overly involved in self-questioning/answering, deviating from intent**  
   *Author: yekern | Open | Comments: 17 | Longest-running open issue*  
   A persistent behavioral regression: the agent enters a self-driven loop proposing, answering, and executing without user confirmation. The community has flagged this as both a **reliability and security concern**, and it remains the top-voted unresolved UX regression.  
   [🔗 Issue #3275](https://github.com/Hmbown/CodeWhale/issues/3275)

3. **#3793 – Guided localized constitution creator (not blank prompt editor)**  
   *Author: Hmbown | Open | Comments: 16*  
   Core to the v0.8.67 setup experience: the maintainer wants a **language-first, guided-plus-open-canvas** flow for creating constitutions, with autonomy/risk posture separated from runtime security. This is a design centerpiece for the release.  
   [🔗 Issue #3793](https://github.com/Hmbown/CodeWhale/issues/3793)

4. **#3406 – Runtime posture card with constitution boundary**  
   *Author: Hmbown | Closed | Comments: 16*  
   Established the security principle that a constitution should not silently change runtime posture. This was a **design prerequisite** for #3793 and introduces an explicit `ask-first / normal agent / high-trust local` selector.  
   [🔗 Issue #3406](https://github.com/Hmbown/CodeWhale/issues/3406)

5. **#3792 – Make first-run onboarding feel like starting CodeWhale, not editing config**  
   *Author: Hmbown | Open | Comments: 8*  
   A core UX concern: the setup flow must keep the constitution central but not mix it with enforced runtime controls. The spine emphasizes language selection first, then constitution, then provider/routing.  
   [🔗 Issue #3792](https://github.com/Hmbown/CodeWhale/issues/3792)

6. **#3884 – Codex sub-agents fail with "Responses API request failed"**  
   *Author: Hmbown | Closed | Comments: 4*  
   A **release-blocker** that broke orchestrated work: sub-agents under Codex failed before returning any findings. The fix was merged in the last 24 hours.  
   [🔗 Issue #3884](https://github.com/Hmbown/CodeWhale/issues/3884)

7. **#4026 – Light theme: terminal selection highlight invisible**  
   *Author: boekhoffm | Open | Comments: 2*  
   A straightforward but impactful UX bug: mouse text selection on light theme has no visible highlight. This affects accessibility and daily use for light-theme users.  
   [🔗 Issue #4026](https://github.com/Hmbown/CodeWhale/issues/4026)

8. **#3961 – Make new-version prompts persistent and actionable**  
   *Author: Hmbown | Open | Comments: 2*  
   The update machinery exists but the user experience gap is the weak point: notifications are easily dismissed or missed. Requesting a sticky prompt with clear action buttons.  
   [🔗 Issue #3961](https://github.com/Hmbown/CodeWhale/issues/3961)

9. **#4009 – Agent sidebar does not reflect cancellations**  
   *Author: Hmbown | Closed | Comments: 0*  
   During dogfooding, the team found that cancelled sub-agents don't visually update and the sidebar non-interactive. Fixed in v0.8.67 RC.  
   [🔗 Issue #4009](https://github.com/Hmbown/CodeWhale/issues/4009)

10. **#4008 – Make links in TUI messages clickable/openable**  
    *Author: Hmbown | Closed | Comments: 0*  
    Links rendered in messages were not actionable. Fixed via OSC 8 support for v0.8.67 RC.  
    [🔗 Issue #4008](https://github.com/Hmbown/CodeWhale/issues/4008)

---

## Key PR Progress

1. **#4023 – Harden v0.8.67 RC surfaces** (merged)  
   A comprehensive RC hardening PR addressing stream timeout config, plugin paths, copy, provider routing, OAuth messaging, cost display, OSC 8 links, and subagent sidebar interactivity.  
   [🔗 PR #4023](https://github.com/Hmbown/CodeWhale/pull/4023)

2. **#3969 – Add per-sub-agent provider routing** (open)  
   Community-contributed implementation of #3965: a new `[subagents.routes.<role>]` config table. Enables running `explore`/`format` on local LM Studio while `generator` uses OpenAI.  
   [🔗 PR #3969](https://github.com/Hmbown/CodeWhale/pull/3969)

3. **#3967 – Avoid redundant composer input wrapping per frame** (open)  
   Performance fix: redundant wrapping in `layout_input_with_scroll` was causing up to 5x unnecessary render work. Fixes #3909.  
   [🔗 PR #3967](https://github.com/Hmbown/CodeWhale/pull/3967)

4. **#3869 – Add dynamic MCP server infrastructure to McpPool** (open)  
   Foundation for runtime-started MCP servers from conversation context. Enables AI agents to spin up MCP servers dynamically via a `start_mcp_server` tool.  
   [🔗 PR #3869](https://github.com/Hmbown/CodeWhale/pull/3869)

5. **#3866 – LLM can start MCP servers from chat context** (open)  
   Adds the actual `start_mcp_server` tool supporting stdio and HTTP transports. Builds on #3869.  
   [🔗 PR #3866](https://github.com/Hmbown/CodeWhale/pull/3866)

6. **#3972 – Allow longer quiet reasoning waits** (merged)  
   Raises default stream idle timeout from 300s to 900s and makes TUI watchdog respect configured budget. Addresses deep reasoning sessions timing out.  
   [🔗 PR #3972](https://github.com/Hmbown/CodeWhale/pull/3972)

7. **#4024 – Align v0.8.67 QA script with repo constitution source** (merged)  
   Fixes the setup QA test to use canonical binary paths and match the new `repo_constitution` source kind in doctor output.  
   [🔗 PR #4024](https://github.com/Hmbown/CodeWhale/pull/4024)

8. **#3785 – Localize Hotbar setup wizard** (open)  
   Localizes the Hotbar setup wizard chrome, action names, and descriptions so non-English flows aren't dominated by English labels.  
   [🔗 PR #3785](https://github.com/Hmbown/CodeWhale/pull/3785)

9. **#3781 – Feat/opencode zen provider** (open)  
   New provider integration for OpenCode ZEN.  
   [🔗 PR #3781](https://github.com/Hmbown/CodeWhale/pull/3781)

10. **#3762 – Redesign homepage with trust strip, GitHub nav, and mirror footer** (open)  
    Web redesign adding MIT license, local-first, provider count, and security model trust strip. Also adds China mirrors (CNB, Tsinghua).  
    [🔗 PR #3762](https://github.com/Hmbown/CodeWhale/pull/3762)

---

## Feature Request Trends

**1. Per-sub-agent provider routing (highest demand)**  
Multiple users want to pin specific sub-agent roles to specific providers/models — especially local endpoints like LM Studio for fast tasks and cloud for heavy generation. Community-contributed PR #3969 is the direct response.

**2. Structured code search and AST-backed tools**  
The v0.8.68 roadmap includes AST-backed search, edit previews, and a debugger protocol surface. Users want refactors that are safer than grep-and-patch.

**3. Persistent and actionable update notifications**  
The existing update machinery works but the in-app user experience is weak. Users want sticky, dismissible prompts with clear "Update Now / Later" buttons.

**4. Project-scoped memory / recall**  
Current memory is user-scoped Markdown only. The community wants lightweight per-project convention storage and recall for agents.

**5. Dynamic MCP server support**  
Two related PRs (#3869, #3866) enable LLMs to start MCP servers at runtime — users see this as a foundational capability for flexible tool ecosystems.

---

## Developer Pain Points

- **Agent autonomy overreach** (Issue #3275): The most persistent UX regression. Agents enter self-driven loops of proposing and executing without user confirmation, especially disruptive for security-sensitive workflows. Has survived multiple releases.
- **Light theme rendering issues** (#4026): Mouse selection highlights are invisible on light theme — a basic accessibility failure that affects daily use.
- **Truncation throughout the TUI** (Issues #3994, #3992, #3989, #3988): Multiple pickers, footers, and list views truncate text mid-word or mid-token without ellipsis, making the interface feel broken at standard terminal widths (80-120 columns).
- **Plugin state not persisted** (#3918): `/plugin enable|disable` writes to an in-memory map that resets on every launch — a significant reliability gap for users who customize their plugin setup.
- **Sub-agent cancellation not reflected in sidebar** (#4009): Cancelled agents remain visible as active, creating confusion during orchestrated workflows. Fixed in RC but indicative of ongoing sidebar staleness issues.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*