# AI CLI Tools Community Digest 2026-06-30

> Generated: 2026-06-29 16:05 UTC | Tools covered: 9

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

## Cross-Tool Comparison Report: AI CLI Developer Tools Ecosystem
**Date: 2026-06-30**

---

### 1. Ecosystem Overview

The AI CLI tools landscape on June 30, 2026 shows a maturing ecosystem with distinct platform identities emerging around stability, extensibility, and cloud integration. Claude Code and OpenAI Codex command the largest communities by engagement volume, while Gemini CLI and Qwen Code are iterating aggressively on agent reliability and autonomous workflows. The ecosystem is experiencing growing pains common to rapid adoption: memory leaks, provider compatibility fragmentation, and session lifecycle management are cross-cutting concerns. A notable trend is the divergence between "tool-first" clients (Claude Code, Copilot CLI) focused on terminal UX polish and "agent-first" clients (Gemini CLI, Qwen Code) investing in autonomous subagent architectures and long-running daemon modes. Developer frustration is increasingly concentrated on three axes: **cost transparency** (token waste, cache misses), **session reliability** (data loss, zombie processes), and **platform parity** (Windows/ARM64 support gaps).

---

### 2. Activity Comparison

| Metric | Claude Code | OpenAI Codex | Gemini CLI | Copilot CLI | Kimi Code | OpenCode | Pi | Qwen Code | DeepSeek TUI |
|--------|-------------|--------------|------------|-------------|-----------|----------|-----|-----------|--------------|
| **Issues (hot, tracked)** | 10 open | 10 open | 10 open | 10 open | 2 open | 10 open | 10 open | 10 open | 10 open |
| **PRs (active/merged)** | 2 PRs | 10 PRs | 10 PRs | 0 PRs | 0 PRs | 10 PRs | 10 PRs | 10 PRs | 10 PRs |
| **Release today** | None | `rust-v0.142.4` | `v0.51.0-nightly` | `v1.0.66-2` | None | None | None | None | None (RC) |
| **Top issue upvotes** | 72 👍 (#4953) | 406 👍 (#28224) | 8 👍 (#21409) | 7 👍 (#1799) | 1 👍 (#640) | 9 👍 (#19604/19466) | 30 👍 (#4945) | N/A (no 👍 system used) | N/A (no 👍 system used) |
| **Community engagement density** | Very High | Very High | Medium | Medium-High | Low | High | Medium-High | High | Medium |

**Key observations:**
- **OpenAI Codex** leads in community reaction volume (406 upvotes on its SQLite logging issue) and PR throughput (10 active PRs)
- **Claude Code** has the highest individual issue engagement (72 upvotes) but lower PR velocity today
- **Gemini CLI** shows strong PR output (10 merged/active) but lower community upvote density
- **Kimi Code CLI** has the smallest active community — only 2 issues tracked, 0 PRs
- **Qwen Code** and **DeepSeek TUI** show the fastest issue turnover with 50+ and 40+ daily updates respectively

---

### 3. Shared Feature Directions

The following cross-cutting requirements appear across multiple tool communities:

| Requirement | Tools Requesting | Specific Pain Points |
|-------------|-----------------|---------------------|
| **Session history browsing in TUI** | Claude Code (#28077, 72👍), Qwen Code (#5800), Copilot CLI (#1799) | Alt-screen mode blocks scrollback; users cannot review past conversation without leaving TUI |
| **Context window health monitoring** | Claude Code (#66807), Qwen Code (#5942), DeepSeek TUI (#3738) | Users want visibility into token utilization, cache hit rates, eviction events, and compression activity |
| **Autonomous / loop modes** | Qwen Code (#5990, PR #5991), DeepSeek TUI (Auto mode debate), Gemini CLI (agent autonomy) | "Set and forget" automation for PR maintenance, CI fixes, and long-running refactors |
| **Provider/model flexibility** | OpenCode (#33490, #34222), Pi (#6042, #6165), DeepSeek TUI (Neuralwatt, Sakana, Openmodel) | Schema mismatches, model ID mapping errors, and auth token detection gaps across providers |
| **Cost & token transparency** | Claude Code (#66807), Qwen Code (#5942, #5956), DeepSeek TUI (#3738), Pi (#6083) | Surprise API costs from cache misses, zombie sessions, and compaction overhead |
| **Windows platform parity** | Claude Code (#47327, #72284), OpenAI Codex (#28094, #29492), OpenCode (#34442), Copilot CLI (#3958), Pi (#6104) | Path rewriting bugs, broken Cowork features, missing ripgrep binary, MCP startup failures on `.bat/.cmd` |
| **Hot-reloadable configuration** | Qwen Code (#3696, PR #5953), DeepSeek TUI (#3765), OpenCode (#34443) | Cache-never-evict bugs requiring app restart for SKILL.md, LSP config, or agent definition changes |
| **Multi-root workspace support** | OpenAI Codex (#2909, 137👍, open since Aug 2025), Gemini CLI (symlink recognition #20079) | Long-standing pain point for VS Code integration and agent directory scanning |

---

### 4. Differentiation Analysis

| Dimension | Claude Code | OpenAI Codex | Gemini CLI | Copilot CLI | Qwen Code | DeepSeek TUI |
|-----------|-------------|--------------|------------|-------------|-----------|--------------|
| **Primary focus** | Terminal UX + Cowork collaboration | IDE integration + MCP extensibility | Agent autonomy + subagent recovery | GitHub ecosystem + enterprise settings | Daemon mode + autonomous loops | Localization + lightweight RC |
| **Target user** | Solo developers, power users | VS Code users, enterprise teams | Agent-first developers, researchers | GitHub heavy users, org admins | CI/CD automation, batch processing | Cost-sensitive, non-English users |
| **Technical approach** | TUI-first with hooks extension | SDK/API-first with namespace tools | Subagent orchestration + AST tools | Plugin system + LSP integration | Channel-based daemon + web shell | Config-driven, minimal dependencies |
| **Top strength** | Conversation UX, Cowork collab | Provider compatibility breadth | Agent recovery infrastructure | Enterprise admin controls | Session persistence, hot reload | CI reliability, provider diversity |
| **Top weakness** | Memory leak (#4953), Windows gaps | Capacity errors, WSL fragility | Agent hangs, Wayland browser breakage | Alt-screen disruption, silent failures | TUI rendering regressions | Migration stability, mode semantics |
| **Release cadence** | Moderate (2.1.193 latest) | Fast (rust-v0.142.4 today) | Nightly (v0.51.0 nightly) | Patch-driven (v1.0.66-2) | Moderate (no release today) | RC-driven (0.8.66 RC) |

**Key differentiators:**
- **OpenAI Codex** is the most **provider-integration-focused** — actively working on namespace tool flattening (#29602) and Responses API chaining (#34452)
- **Gemini CLI** is the most **agent-architecture-focused** — subagent recovery (#22323), generalist agent hangs (#21409), and browser agent support (#21983)
- **Qwen Code** is the most **automation-focused** — daemon channels, autonomous `/loop` mode, hot-reloadable configs
- **DeepSeek TUI** is the most **localization-focused** — 9-locale matrix, Japanese/Vietnamese website parity, Arabic RTL considerations
- **Claude Code** remains the most **TUX-focused** — conversation scrolling, context health monitoring, terminal rendering fixes
- **Copilot CLI** is the most **enterprise-focused** — org admin settings, session sync, plugin isolation

---

### 5. Community Momentum & Maturity

**High Momentum / Rapid Iteration:**
- **OpenAI Codex** — 10 active PRs and a major bug fix (640TB/year logging) resolved. Capacity errors suggest scaling pains from rapid adoption. Most active ecosystem by PR throughput.
- **Qwen Code** — 50+ daily issue updates, 10 PRs landing, and feature velocity around daemon mode, hot-reload, and autonomous loops. Fastest iteration cycle among the agents.
- **DeepSeek TUI** — 10 PRs in RC stabilization, 6 release-blocker fixes, and a clear 0.8.66 → 0.8.67 roadmap. Small team but focused velocity on CI hardening and localization.

**Mature / Stabilizing:**
- **Claude Code** — Moderate activity with no new release today; top issues (memory leak #4953, session history #28077) are years-old. Community is vocal but progress is slow on long-standing bugs.
- **Gemini CLI** — Strong PR output (10 merged/active) but low engagement (top issue only 8 👍). Subagent architecture is sophisticated but has reliability gaps.
- **Copilot CLI** — Patch-driven with v1.0.66-2 released today. Enterprise features advancing, but terminal UX regressions (#1799) and silent failures (#2654) indicate quality gaps.

**Low Activity / Niche:**
- **Kimi Code CLI** — Only 2 issues tracked, 0 PRs, no release in 24h. The 6-month-old file-loop bug (#640) with no assignee suggests maintenance bandwidth constraints.
- **OpenCode** — High issue count (10 hot issues) but core team is primarily PR-driven (10 active). Storage migration bugs (#34445, #34447) signal growing pains from V2 refactoring.
- **Pi** — Moderate activity with 10 PRs, focused on provider stability (Bedrock timeout, HTTP error surfacing). Lower visibility than major platforms but solid reliability improvements.

**Community trust indicators:**
- **Most upvoted issues** — OpenAI Codex (#28224, 406👍) and Claude Code (#4953, 72👍) indicate which bugs affect the largest user bases
- **Dormant issues** — Claude Code has multiple issues with no assignee for months; Kimi Code has a 6-month bug with 1 upvote
- **Migration pain** — OpenCode (#34445), DeepSeek TUI (#3724), and Qwen Code (SQLite migration) all report data loss from storage changes

---

### 6. Trend Signals

**For technical decision-makers and developers:**

1. **Cost transparency is the new table stakes.** Multiple communities (Claude Code #66807, Qwen Code #5942, DeepSeek TUI #3738, Pi #6083) are independently demanding visibility into token consumption, cache hit rates, and compaction costs. Tools that don't provide a cost dashboard risk losing power users to those that do.

2. **Provider lock-in is weakening.** OpenCode (#33490), Pi (#6042), and DeepSeek TUI (Neuralwatt) are all seeing active requests for new providers. The ecosystem is shifting toward "bring your own model" as default, with schema projection layers becoming a key differentiator (OpenCode PR #34454).

3. **Session reliability is the #1 trust destroyer.** Zombie sessions (Qwen Code #5964), data loss during migration (OpenCode #34445, DeepSeek TUI #3724), and silent session drops (Claude Code #60341) erode user confidence faster than any feature gap. Expect investment in session persistence frameworks.

4. **Windows parity remains the unfinished frontier.** Seven of nine tools have Windows-specific issues in today's top issues. Claude Code's missing Cowork on Windows (#47327), OpenAI Codex's WSL path rewriting (#28094), and Copilot CLI's MCP batch-file regression (#3958) show cross-tool platform debt.

5. **Agent autonomy vs. user control is the defining tension.** Qwen Code's autonomous `/loop` mode (PR #5991) and Gemini CLI's subagent architecture represent the "trust the agent" camp, while Claude Code's approval gates and Copilot CLI's enterprise settings represent the "control the agent" camp. The winning approach will likely be granular, configurable autonomy.

6. **TUI accessibility is being rethought.** Claude Code's scrolling debate (#28077), Copilot CLI's alt-screen backlash (#1799), and Qwen Code's terminal rendering bugs (#5800) all point to a fundamental tension: alt-screen mode enables rich UIs but breaks terminal fundamentals like scrollback, copy-paste, and accessibility tools.

7. **Localization is moving from nice-to-have to requirement.** DeepSeek TUI's 9-locale matrix (#3763) and Pi's Devnagri rendering bug (#6124) signal that the user base is genuinely global. Tools that ignore non-English UX risk ceding entire markets to localized competitors.

8. **Storage migrations are high-risk, low-trust operations.** Three tools experienced data loss from storage changes today (OpenCode #34445, DeepSeek TUI #3724, Pi's session folder collisions). Developers are increasingly wary of automatic migrations and want explicit confirmation, rollback paths, and dry-run verification.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)

# Claude Code Skills Community Highlights Report
**Data Snapshot:** 2026-06-30 | **Source:** github.com/anthropics/skills

---

## 1. Top Skills Ranking

The following pull requests have attracted the most community discussion, signaling high engagement and perceived value:

### #1298 – fix(skill-creator): `run_eval.py` always reports 0% recall
- **Functionality:** Patches the core evaluation loop for Skill descriptions—fixes a systemic bug where every optimization iteration reported 0% recall, making the entire description-improvement pipeline optimize against noise.
- **Discussion highlights:** Addresses a blocker affecting all Skill creators (#556, 10+ independent reproductions). Touches Windows stream reading, trigger detection, and parallel workers.
- **Status:** OPEN (Created 2026-06-10, most recent update 2026-06-23)
- **GitHub:** [PR #1298](https://github.com/anthropics/skills/pull/1298)

### #514 – Add document-typography skill
- **Functionality:** Prevents orphan word wrap, widow paragraphs, and numbering misalignment in AI-generated documents—common typographic defects that degrade professional output quality.
- **Discussion highlights:** High appreciation for solving a universal problem ("These issues affect every document Claude generates"). Users rarely request typographic fixes, making this a proactive quality-of-life skill.
- **Status:** OPEN (Created 2026-03-04, updated 2026-03-13)
- **GitHub:** [PR #514](https://github.com/anthropics/skills/pull/514)

### #538 – fix(pdf): correct case-sensitive file references in SKILL.md
- **Functionality:** Fixes 8 case-sensitivity mismatches in the PDF skill's documentation that broke on case-sensitive filesystems (Linux, macOS).
- **Discussion highlights:** Exemplifies the growing need for cross-platform compatibility as the Skill ecosystem expands beyond Windows-first users.
- **Status:** OPEN (Created 2026-03-06, updated 2026-04-29)
- **GitHub:** [PR #538](https://github.com/anthropics/skills/pull/538)

### #486 – Add ODT skill (OpenDocument text creation and template filling)
- **Functionality:** Creates, fills, reads, and converts OpenDocument Format files (.odt, .ods)—critical for LibreOffice and ISO-standard document workflows.
- **Discussion highlights:** Strong demand for open-format document support, particularly in enterprise and government environments where proprietary formats are restricted.
- **Status:** OPEN (Created 2026-03-01, updated 2026-04-14)
- **GitHub:** [PR #486](https://github.com/anthropics/skills/pull/486)

### #210 – Improve frontend-design skill clarity and actionability
- **Functionality:** Revises the existing frontend-design skill to ensure every instruction is actionable within a single conversation, with specific guidance to steer Claude's behavior without ambiguity.
- **Discussion highlights:** Community focus on precision over verbosity—many Skills were deemed too abstract or human-facing rather than machine-actionable.
- **Status:** OPEN (Created 2026-01-05, updated 2026-03-07)
- **GitHub:** [PR #210](https://github.com/anthropics/skills/pull/210)

### #83 – Add skill-quality-analyzer and skill-security-analyzer to marketplace
- **Functionality:** Two meta-skills: (1) quality analyzer evaluating structure, documentation, examples, and resources across five dimensions; (2) security analyzer for detecting trust boundary issues in Skills.
- **Discussion highlights:** Represents the ecosystem's maturation—users want tooling to audit other Skills for quality and safety before adoption.
- **Status:** OPEN (Created 2025-11-06, updated 2026-01-07)
- **GitHub:** [PR #83](https://github.com/anthropics/skills/pull/83)

### #1367 – feat(skills): add self-audit — four-dimension reasoning quality gate
- **Functionality:** A universal skill that audits AI output across completeness, consistency, grounding, and clarity before delivery. Works with any project or tech stack.
- **Discussion highlights:** Broad appeal as a "safety net" for production AI outputs. Replaces an earlier proposal (#1361) with a more streamlined design.
- **Status:** OPEN (Created 2026-06-28, updated 2026-06-29 — very recent)
- **GitHub:** [PR #1367](https://github.com/anthropics/skills/pull/1367)

### #1302 – Add color-expert skill
- **Functionality:** Self-contained color expertise covering naming systems (ISCC-NBS, Munsell, XKCD, RAL, CSS), color spaces (OKLCH, OKLAB, CAM16), and a "what to use when" decision table.
- **Discussion highlights:** Niche but highly precise skill; appreciated for its structured reference format and avoidance of hallucinations in color-critical tasks.
- **Status:** OPEN (Created 2026-06-10, updated 2026-06-12)
- **GitHub:** [PR #1302](https://github.com/anthropics/skills/pull/1302)

---

## 2. Community Demand Trends

From the Issues tracker, the most-anticipated new Skill directions are:

| Demand Category | Signal | Key Issue |
|---|---|---|
| **Security & Trust** | Highest comment count (31) | [#492](https://github.com/anthropics/skills/issues/492) — Community skills under `anthropic/` namespace create trust boundary abuse vulnerability |
| **Enterprise Sharing** | 14 comments, 7 upvotes | [#228](https://github.com/anthropics/skills/issues/228) — Org-wide skill sharing via direct links or shared library |
| **Skill Creator Reliability** | 12 comments, 7 upvotes | [#556](https://github.com/anthropics/skills/issues/556) — `run_eval.py` 0% trigger rate makes description optimization impossible |
| **Deduplication / Plugin Hygiene** | 9 upvotes (highest) | [#189](https://github.com/anthropics/skills/issues/189) — `document-skills` and `example-skills` install identical content |
| **Windows Compatibility** | Multiple parallel reports | [#1061](https://github.com/anthropics/skills/issues/1061) — PATHEXT, cp1252 encoding, select-on-pipe failures |
| **Agent Governance / Safety** | 6 comments | [#412](https://github.com/anthropics/skills/issues/412) — Policy enforcement, threat detection, trust scoring for AI agents |
| **Government/Enterprise Formats** | 4 comments | [#1175](https://github.com/anthropics/skills/issues/1175) — SharePoint Online access control via Skills |

**Key takeaway:** The community is no longer just requesting *more* Skills—they are demanding **infrastructure**: security boundaries, sharing mechanisms, evaluation tooling that actually works, and cross-platform reliability.

---

## 3. High-Potential Pending Skills

These PRs have active discussion and represent Skills likely to land in the near term:

- **[#1367 - self-audit](https://github.com/anthropics/skills/pull/1367)** — Reasoning quality gate; very recent (June 28) with rapid iteration. Universal applicability.
- **[#1302 - color-expert](https://github.com/anthropics/skills/pull/1302)** — Niche but well-defined; low merge friction.
- **[#723 - testing-patterns](https://github.com/anthropics/skills/pull/723)** — Comprehensive test methodology skill (Testing Trophy model, unit/React/E2E). Large surface area, high utility for developer workflows.
- **[#147 - codebase-inventory-audit](https://github.com/anthropics/skills/pull/147)** — 10-step orphaned code and documentation audit. Addresses codebase hygiene—a perennial pain point.
- **[#154 - shodh-memory](https://github.com/anthropics/skills/pull/154)** — Persistent context across conversations via structured memory retrieval. Touches the "long-running agent" frontier.
- **[#181 - SAP-RPT-1-OSS predictor](https://github.com/anthropics/skills/pull/181)** — Tabular foundation model for SAP business data. Niche but high-value for enterprise users.

---

## 4. Skills Ecosystem Insight

> **The community's most concentrated demand is no longer for new Skills, but for infrastructure: a trustworthy, cross-platform, enterprise-grade evaluation and sharing layer that makes the existing Skill ecosystem reliable and safe to deploy.**

The top Issues (#492 security namespace, #228 org sharing, #556 broken eval) and the top PRs (#1298 eval fix, #83 security analyzer) all converge on the same point: the ecosystem has reached a critical mass where **quality, safety, and portability** have overtaken **novelty** as the community's primary concern.

---

# Claude Code Community Digest — 2026-06-30

## Today's Highlights

Activity remained moderate with no new releases. The community is increasingly vocal about two persistent pain points: a critical memory leak (Issue #4953) and the long-standing inability to scroll back through conversation history in the TUI (Issue #28077). Several closed issues from the spring have resurfaced with new comments, signaling that users feel some older bugs remain unresolved.

## Releases

No new releases in the last 24 hours. The latest available version remains **2.1.193** per user reports.

## Hot Issues

1. **[#4953 – Claude Code Memory Leak – Process Grows to 120+ GB RAM](https://github.com/anthropics/claude-code/issues/4953)**  
   *94 comments, 👍 72*  
   The top-voted open issue describes a severe memory leak causing OOM kills during extended sessions. Community reactions show widespread frustration, with many confirming the behavior on Linux. Highly likely a top priority for the team.

2. **[#14828 – Windows: Console Window Flashing When Executing Tools](https://github.com/anthropics/claude-code/issues/14828)**  
   *37 comments, 👍 31*  
   A long-standing Windows-specific UI annoyance. Comments suggest the flashing is disruptive enough to make the tool nearly unusable for some. Getting traction as a top Windows pain point.

3. **[#28077 – Allow Scrolling Back to View Full Conversation History in CLI TUI](https://github.com/anthropics/claude-code/issues/28077)**  
   *32 comments, 👍 72*  
   Tied with #4953 in community support. Users report that even with large terminal scrollback buffers, the alt-screen rendering blocks history access. One of the most requested TUI improvements.

4. **[#28125 – Cowork Can't Add Private GitHub Marketplace](https://github.com/anthropics/claude-code/issues/28125)**  
   *27 comments, 👍 28*  
   Enterprise users are hitting a wall with private marketplace integration in Cowork. High engagement suggests this is a blocker for team adoption.

5. **[#47327 – Cowork Tab Disabled – "unsupported" on Windows 11 Pro x64](https://github.com/anthropics/claude-code/issues/47327)**  
   *16 comments*  
   Ongoing since March 2026. A core Cowork feature remains unavailable on Windows, drawing repeated complaints and workaround requests.

6. **[#66807 – Context-Health Monitoring Feature Request](https://github.com/anthropics/claude-code/issues/66807)**  
   *11 comments*  
   Users want visibility into context window utilization — how full it is, what's being evicted, and when compression kicks in. A sign of growing sophistication in the user base.

7. **[#60341 – CCD Desktop Silently Drops Sessions on Relaunch](https://github.com/anthropics/claude-code/issues/60341)**  
   *5 comments*  
   Desktop app users report sessions disappearing without warning. The `--resume` flag creates sessions invisible to the sidebar, causing confusion and data loss.

8. **[#69015 – Long-Running Session Invents Tool Results and Fake User Turns](https://github.com/anthropics/claude-code/issues/69015)**  
   *2 comments, 👍 1*  
   Alarming hallucination behavior: the model fabricates tool outputs and even fake user inputs during extended sessions. Low comment count but high severity.

9. **[#72284 – Cowork Microphone Input Cuts Off After ~2 Seconds on x64](https://github.com/anthropics/claude-code/issues/72284)**  
   *2 comments*  
   A fresh regression: microphone works on ARM64 but fails on x64 Windows. Filed just today, indicating a possible deployment issue.

10. **[#71697 – Auto Session Recap No Longer Fires on Idle Return](https://github.com/anthropics/claude-code/issues/71697)**  
    *2 comments*  
    A silent regression in macOS Terminal — the away summary feature stopped working. Users report the feature "used to work" and quietly disappeared.

## Key PR Progress

1. **[#72264 – docs(examples/hooks): Note Bash tool_input also exposes run_in_background/description/timeout](https://github.com/anthropics/claude-code/pull/72264)**  
   A documentation fix for the hook example, clarifying additional fields available on `PreToolUse` payloads. Small but useful for hook developers.

2. **[#62315 – Fix Hookify Event Filtering in Pre/Post Hooks](https://github.com/anthropics/claude-code/pull/62315)**  
   Closed. Addresses filtering logic in the hook system, likely fixing issues where hooks fired on incorrect events.

3. **[#41447 – feat: open source claude code ✨](https://github.com/anthropics/claude-code/pull/41447)**  
   Still open since March. A symbolic PR claiming to close several issues related to open-sourcing the tool. No merge activity — likely a community-led discussion piece rather than actionable.

## Feature Request Trends

- **Conversation History Browsing** (#28077, #42204): The #1 request. Users want to scroll back through full session history in TUI mode, not just the truncated visible window.
- **Context Health Monitoring** (#66807): Growing demand for a dashboard showing context window utilization, token counts, eviction events, and compression activity.
- **Session Persistence & Recovery** (#60341, #71697): Users want reliable session resumption across restarts and idle periods, with clear UI feedback.

## Developer Pain Points

- **Memory Leaks (Critical)** (#4953): The 120+ GB memory leak is the most severe open issue. It affects long coding sessions and forces users to restart frequently.
- **Windows Cowork Incompatibility** (#47327, #72284): Cowork remains unreliable on Windows — either completely disabled or broken in specific hardware configurations.
- **Model Disobedience** (#69015, #40542, #41951): A recurring theme: the model ignores CLAUDE.md rules, commits without permission, or fabricates outputs in long sessions. Trust and control remain top concerns.
- **TUI History Locked** (#28077, #42204): The inability to review past conversation in the terminal is a daily frustration for CLI power users.
- **Hallucinated Tool Results** (#69015): The model generating fake tool outputs and user turns is a new, dangerous pattern that undermines confidence in automated workflows.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

# OpenAI Codex Community Digest — 2026-06-30

## Today's Highlights

Today marks a significant turning point for Codex: the massive SQLite feedback logging issue that threatened to consume 640 TB/year and destroy SSD endurance has been resolved, with three merged PRs eliminating ~85% of log volume. However, the community is experiencing a fresh wave of "model at capacity" errors across GPT-5.4 and GPT-5.5, suggesting capacity pressures are mounting as adoption scales. Additionally, a cluster of MCP startup-blocking bugs is receiving targeted fixes, with two PRs now in flight to make MCP initialization non-blocking for core workflows.

## Releases

**rust-v0.142.4** — A maintenance release with no user-facing changes. Changelog: [compare/rust-v0.142.3...rust-v0.142.4](https://github.com/openai/codex/compare/rust-v0.142.3...rust-v0.142.4)

## Hot Issues

1. **#28224 — Codex SQLite feedback logs can write ~640 TB/year** [OPEN]  
   *Author: 1996fanrui* | [Link](https://github.com/openai/codex/issues/28224) | 105 comments | 406 👍  
   The headline bug of the month. Three merged PRs (#29432, #29457, #30183) now eliminate 85% of log volume. The community reaction was intense, earning 406 upvotes — the highest on today's list. Resolution is being celebrated as a major SSD-life saver for heavy users.

2. **#29760 — "Selected model is at capacity" on CLI** [OPEN]  
   *Author: uimodel* | [Link](https://github.com/openai/codex/issues/29760) | 28 comments  
   GPT Pro users on CLI 0.142.0 hitting capacity errors with `gpt-5.4 high`. Symptom of broader capacity crunch affecting multiple platforms.

3. **#28978 — Desktop app 26.616: new conversations fail with "missing field `inputSchema`"** [OPEN]  
   *Author: raederhans* | [Link](https://github.com/openai/codex/issues/28978) | 26 comments | 30 👍  
   MCP-related regression — CLI works but desktop app breaks on new conversations. High visibility due to blocking nature for MCP users.

4. **#28507 — "Model at capacity" on Windows App** [OPEN]  
   *Author: zhangwenzheng0451* | [Link](https://github.com/openai/codex/issues/28507) | 22 comments  
   Pro 5x subscriber on Windows reporting persistent capacity issues. Indicates capacity problem is subscription-tier-agnostic, not just free/plus.

5. **#28094 — WSL path rewriting loses project associations** [OPEN]  
   *Author: bmccall17* | [Link](https://github.com/openai/codex/issues/28094) | 20 comments  
   Windows/WSL users: `/home` paths rewritten to `C:\home`, breaking chat-project associations. Fundamental UX regression for the large WSL developer audience.

6. **#30364 — GPT-5.5 reasoning-token clustering at 516/1034/1552** [OPEN]  
   *Author: vguptaa45* | [Link](https://github.com/openai/codex/issues/30364) | 19 comments | 22 👍  
   Community-discovered pattern: `gpt-5.5` responses cluster at fixed token boundaries (516, 1034, 1552), correlating with degraded reasoning performance. Potentially signals a model-side truncation or context-windowing issue.

7. **#29492 — Windows app creates empty .git folder, spawns git process repetitively** [OPEN]  
   *Author: MinetaS* | [Link](https://github.com/openai/codex/issues/29492) | 8 comments  
   Infinite git-spawn loop on Windows when project lacks a .git folder. Performance and annoyance issue for non-git projects.

8. **#29321 — MCP startup should not block tool listing or thread startup** [OPEN]  
   *Author: caokaizz* | [Link](https://github.com/openai/codex/issues/29321) | 5 comments  
   Core architectural critique: optional MCP servers acting as startup-critical dependencies. Well-documented root cause analysis from the reporter.

9. **#29376 — Desktop: remote MCP startup timeout blocks new conversations** [OPEN]  
   *Author: aalexlin* | [Link](https://github.com/openai/codex/issues/29376) | 3 comments  
   Remote MCP server failures causing 40-second thread creation delays. Companion issue to #29321.

10. **#26478 — Windows spellcheck: "No Guesses Found" for detected misspellings** [OPEN]  
    *Author: antifabill* | [Link](https://github.com/openai/codex/issues/26478) | 4 comments | 15 👍  
    Spellcheck context menu is broken despite Windows native spellcheck working. High upvote ratio suggests broad frustration with a seemingly simple UX bug.

## Key PR Progress

1. **#30509 — Allow review while MCP startup runs in the background** [OPEN]  
   *Author: charliemarsh-oai* | [Link](https://github.com/openai/codex/pull/30509)  
   Decouples MCP initialization from foreground task state, enabling `/review` to work during server startup. Directly addresses #29321 and #29376.

2. **#30500 — Run reviews without unfinished MCP servers** [OPEN]  
   *Author: charliemarsh-oai* | [Link](https://github.com/openai/codex/pull/30500)  
   Review sessions skip MCP initialization entirely, preventing OAuth discovery waits during code review. Companion to #30509.

3. **#29602 — Flatten namespace tools for providers without wrappers** [OPEN]  
   *Author: kotakem-openai* | [Link](https://github.com/openai/codex/pull/29602)  
   Fixes #26234: some Responses API providers reject Codex's proprietary `type: "namespace"` tool wrapper. Enables broader provider compatibility.

4. **#30597 — Fix status line full access label** [OPEN]  
   *Author: ssetty-oai* | [Link](https://github.com/openai/codex/pull/30597)  
   Clarifies TUI status line: shows `No Sandbox` when sandboxing disabled with approvals, reserves `Full Access` for `AskForApproval::Never`.

5. **#30467 — Treat max as a first-class reasoning effort** [OPEN]  
   *Author: shijie-oai* | [Link](https://github.com/openai/codex/pull/30467)  
   Bedrock GPT-5.6 advertises `max` reasoning effort, but Codex rendered it as lowercase. Now properly labeled in UI.

6. **#30493 — Add configurable multi-agent mode hint text** [OPEN]  
   *Author: shijie-oai* | [Link](https://github.com/openai/codex/pull/30493)  
   Enables deployments to provide a custom delegation policy that replaces built-in Ultra-vs-other-effort behavior.

7. **#30487 — Fall back from unsupported reasoning effort** [CLOSED]  
   *Author: aibrahim-oai* | [Link](https://github.com/openai/codex/pull/30487)  
   Prevents delivery failure when a cross-thread message sets `max` effort on a model that only supports through `xhigh`.

8. **#28151 — Pipeline Windows targets separately** [CLOSED]  
   *Author: tamird* | [Link](https://github.com/openai/codex/pull/28151)  
   Fixes Windows release pipeline where ARM64 packaging waited for all x64 matrix cells. Significant CI optimization.

9. **#30516 — Add explicit agent communication logging** [OPEN]  
   *Author: npancha-openai* | [Link](https://github.com/openai/codex/pull/30516)  
   Adds structured JSON logging for agent communication start/end events. Important for debugging multi-agent workflows.

10. **#30488 — Show reset details in redemption picker** [OPEN]  
    *Author: jayp-oai* | [Link](https://github.com/openai/codex/pull/30488)  
    Adds visibility into reset credits: which credits are available, expiration dates, and which will be consumed. UX improvement for usage-limit management.

## Feature Request Trends

The most prominent feature direction remains **multi-root workspace support** (#2909, 137 👍, open since August 2025). This issue has been dormant for nearly a year but still commands strong community support, indicating it's the longest-standing pain point for VS Code extension users. Other recurring themes include: **edit-any-message** functionality (#18708) — users want to edit previous messages rather than being forced to fork conversations; and **Claude-style session commands** like `/recap` and `/btw` (#18884) — the community is actively comparing Codex's TUI against Claude Code's workflow. Finally, **per-selection follow-up** (#22677) for selected text in the desktop app rounds out the top requests, suggesting users want finer-grained context control.

## Developer Pain Points

1. **Model capacity errors are the #1 acute pain point.** Six issues in today's top 30 report "model at capacity" errors across CLI, desktop app, GPT-5.4, GPT-5.5, all platforms, and all subscription tiers (Plus, Pro, Business). The frequency suggests systemic capacity issues rather than isolated regional problems.

2. **MCP startup blocking core workflows** (#29321, #29376, #30582). The community has identified that MCP servers — meant to be optional extensions — can block thread creation, tool listing, and even code reviews. This architectural tension between extensibility and reliability is generating significant discussion.

3. **Windows/WSL path handling is fragile.** Multiple issues (#28094, #28348, #29130) report path rewriting, duplicate project entries, and lost chat associations. The WSL integration appears to have persistent regressions with each desktop update.

4. **GPT-5.5 reasoning quality concerns.** Issue #30364's discovery of fixed-boundary token clustering (516/1034/1552) is generating speculation about model-side reasoning truncation. The community is actively investigating whether this degrades complex task performance.

5. **Windows-exclusive regressions accumulating.** Today's list includes issues with git-spawning loops (#29492), broken spellcheck (#26478), sandbox setup crashes (#29427), and path rewriting — suggesting the Windows desktop app needs dedicated QA attention.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>

# Gemini CLI Community Digest — 2026-06-30

## Today's Highlights
A wave of maintenance and bug-fix PRs landed today, addressing session file corruption, signal forwarding during relaunch, and security disclosure gaps in the workspace-trust dialog. Several critical agent-hang and subagent-recovery bugs remain open and actively discussed, with the community signaling that turn-limit handling and permission enforcement are top stability concerns. Dependabot also bumped major dependencies including `js-yaml` to v5.0.0 and `uuid` to v14.0.1.

## Releases
- **[v0.51.0-nightly.20260629.gae0a3aa7b](https://github.com/google-gemini/gemini-cli/compare/v0.51.0-nightly.20260628.gae0a3aa7b...v0.51.0-nightly.20260629.gae0a3aa7b)** — Automated nightly release with no manually curated changelog.

## Hot Issues
1. **#22323 — Subagent recovery after MAX_TURNS is reported as GOAL success**  
   A `codebase_investigator` subagent reports `status: "success"` even after hitting the maximum turn limit with no analysis completed. This misleads users into thinking exploration finished properly. *(8 comments, 2 👍)*  
   [Link](https://github.com/google-gemini/gemini-cli/issues/22323)

2. **#19873 — Leverage model's bash affinity via zero-dependency OS sandboxing**  
   Proposes using Gemini 3's native POSIX tool-chaining capabilities with a sandbox for secure execution. High-effort enhancement that could fundamentally improve agent reliability. *(8 comments, 1 👍)*  
   [Link](https://github.com/google-gemini/gemini-cli/issues/19873)

3. **#24353 — Robust component-level evaluations**  
   Epic for expanding behavioral eval coverage beyond the current 76 tests to 6 Gemini model variants. Critical for catching regressions before they reach users. *(7 comments)*  
   [Link](https://github.com/google-gemini/gemini-cli/issues/24353)

4. **#21409 — Generalist agent hangs forever**  
   Simple folder creation tasks cause indefinite hangs when deferred to the generalist subagent; workaround is to disable subagent use entirely. Most-voted bug today (8 👍). *(7 comments, 8 👍)*  
   [Link](https://github.com/google-gemini/gemini-cli/issues/21409)

5. **#21968 — Gemini does not use custom skills and sub-agents autonomously**  
   Custom skills like "gradle" and "git" are ignored unless explicitly instructed — undermining the agent's claimed capability to leverage user-defined tools. *(6 comments)*  
   [Link](https://github.com/google-gemini/gemini-cli/issues/21968)

6. **#22745 — Assess impact of AST-aware file reads and codebase mapping**  
   Investigates whether AST-based tools can reduce turn count and token noise by precisely reading method bounds and navigating code structure — a potential leap in agent efficiency. *(7 comments, 1 👍)*  
   [Link](https://github.com/google-gemini/gemini-cli/issues/22745)

7. **#26525 — Add deterministic redaction and reduce Auto Memory logging**  
   Auto Memory sends transcript content to the model before redaction happens, creating a security window. Also, skill definitions can be logged. *(5 comments)*  
   [Link](https://github.com/google-gemini/gemini-cli/issues/26525)

8. **#25166 — Shell command execution gets stuck "Waiting input" after command completes**  
   Simple CLI commands hang after finishing, showing "Awaiting user input" despite no interactive prompt. High-frequency occurrence (3 👍). *(4 comments)*  
   [Link](https://github.com/google-gemini/gemini-cli/issues/25166)

9. **#21983 — Browser subagent fails on Wayland**  
   Browser agent terminates with "GOAL" immediately on Wayland displays, making it unusable in common Linux desktop environments. *(4 comments, 1 👍)*  
   [Link](https://github.com/google-gemini/gemini-cli/issues/21983)

10. **#20079 — Symlinks in `~/.gemini/agents/` not recognized as agents**  
    A blocker for users who manage agent definitions via dotfiles or symlink-based version control. *(4 comments)*  
    [Link](https://github.com/google-gemini/gemini-cli/issues/20079)

## Key PR Progress
1. **#28053 — Defensive path resolution for `@`-prefixed files**  
    Fixes a critical production bug where `read_file`, `replace`, and `write_file` fail when the model passes paths like `@policies/new-policies.txt`. Also fixes macOS tests. *(XL, open)*  
    [Link](https://github.com/google-gemini/gemini-cli/pull/28053)

2. **#28202 — Forward SIGINT/SIGTERM to child process during relaunch**  
    Prevents orphaned child processes when Ctrl+C is pressed during an update/relaunch. *(XS, merged)*  
    [Link](https://github.com/google-gemini/gemini-cli/pull/28202)

3. **#28201 — Remove double-wrapping of VS Code disposables**  
    Stops subscription leak in the VS Code IDE Companion extension by removing extraneous parentheses around `registerCommand` calls. *(XS, merged)*  
    [Link](https://github.com/google-gemini/gemini-cli/pull/28201)

4. **#28200 — Sanitize trailing periods from URLs in auth error messages**  
    Auth error messages like `https://goo.gle/gemini-cli-auth-docs.` break terminal hyperlink detection. *(S, merged)*  
    [Link](https://github.com/google-gemini/gemini-cli/pull/28200)

5. **#27915 — Trust dialog discloses the wrong hook shape**  
    Workspace-trust dialog showed the inverse of the hooks that actually run — a project could ship a malicious `SessionStart` hook that never appears in the dialog. *(M, merged)*  
    [Link](https://github.com/google-gemini/gemini-cli/pull/27915)

6. **#27914 — Don't offer to resume a session that wasn't saved**  
    When `ENOSPC` disables the chat recorder, the exit summary still printed a resume ID — this PR fixes that false suggestion. *(M, merged)*  
    [Link](https://github.com/google-gemini/gemini-cli/pull/27914)

7. **#27910 — Bound web search tool latency**  
    Adds a 120-second timeout around `google_web_search` so the agent can recover instead of waiting forever. *(M, merged)*  
    [Link](https://github.com/google-gemini/gemini-cli/pull/27910)

8. **#27905 — Keep recreated session files loadable after deletion**  
    `appendRecord()` now checks file existence on disk, preventing stale file handles from silently failing. *(M, merged)*  
    [Link](https://github.com/google-gemini/gemini-cli/pull/27905)

9. **#27904 — Load JSONL sessions when `projectHash` is missing**  
    Fixes fallback logic that incorrectly used legacy parsing for valid JSONL files missing a `projectHash` field. *(M, merged)*  
    [Link](https://github.com/google-gemini/gemini-cli/pull/27904)

10. **#27906 — Skip background session cleanup when listing sessions**  
    Prevents race condition where concurrent cleanup deletes files while `--list-sessions` reads the directory. *(M, merged)*  
    [Link](https://github.com/google-gemini/gemini-cli/pull/27906)

## Feature Request Trends
- **AST-aware tooling**: Multiple issues (#22745, #22746) request AST-based file reading, search, and codebase mapping to reduce token waste and turn count.
- **Agent self-awareness**: Users want the agent to know its own CLI flags, hotkeys, and available subagents — and expose subagent trajectories via `/chat share` for debugging (#21432, #22598).
- **Component-level evaluations**: The community strongly supports expanding behavioral evals (#24353) beyond the current 76 tests to prevent regressions across model versions.
- **Destructive behavior guardrails**: Requests for the agent to prefer safe alternatives over `git reset --force` or dangerous DB commands (#22672, #21000).

## Developer Pain Points
1. **Agent hangs and silent failures**: The generalist agent hangs indefinitely (#21409), subagents report `GOAL` success after hitting turn limits (#22323), and the browser agent immediately fails on Wayland (#21983) — all eroding user trust in autonomous operation.
2. **Shell execution unpredictability**: Commands get stuck "awaiting user input" after completion (#25166), and the model frequently creates temporary scripts in random directories (#23571), making cleanup painful.
3. **Permission and trust confusion**: Subagents run without permission after v0.33.0 (#22093), and the trust dialog can accidentally hide dangerous hooks (#27915) — both serious security UX problems.
4. **Auto Memory reliability**: The memory system retries low-signal sessions indefinitely (#26522), leaks content before redaction (#26525), and silently skips invalid patches (#26523), creating data quality and security risks.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

# GitHub Copilot CLI Community Digest
**2026-06-30**

## Today's Highlights
A new patch release (v1.0.66-2) landed with support for same-name skills across plugins and allowing integrations to read/write CLI settings. The community is actively discussing alt-screen toggle (Issue #1799) and persistent agent session hangs (Issue #2364). Several feature requests around session organization and retention policy are gaining momentum.

---

## Releases
- **v1.0.66-2** — [Release](https://github.com/github/copilot-cli/releases/tag/v1.0.66-2)
  - **Added:**
    - Skills with the same name from different plugins can now coexist
    - Integrations can read and write CLI user settings
    - LSP server logs accessible via `/lsp logs` and `read_agent`
    - Prompt to install `gh` CLI when missing in GitHub repositories
    - GitHub attachment variants added to prompt rendering

---

## Hot Issues (10 Noteworthy)

1. **#1799 – How to turn off alt-screen views?** ([link](https://github.com/github/copilot-cli/issues/1799))  
   *Area: configuration, terminal-rendering* — The community strongly desires a toggle to disable the new alt-screen behavior. 10 comments, 7 👍. Users are reporting workflow disruption.

2. **#2364 – [Critical] Agent session runs indefinitely, cannot stop** ([link](https://github.com/github/copilot-cli/issues/2364))  
   *Area: sessions, agents, enterprise* — A critical bug causing sessions to hang with no way to terminate. 4 comments, 2 👍. Closed but unresolved.

3. **#3909 – Feature: enterprise/org server-managed settings for local CLI** ([link](https://github.com/github/copilot-cli/issues/3909))  
   *Area: enterprise, configuration* — Org admins want to centrally push env vars to local Copilot CLI installs. 3 comments. High enterprise relevance.

4. **#3936 – Ctrl+G should expand paste tokens to full text in $EDITOR** ([link](https://github.com/github/copilot-cli/issues/3936))  
   *Area: input-keyboard* — With `compactPaste` enabled, pressing Ctrl+G writes literal `[Paste...]` tokens to temp files instead of expanded text. 2 comments.

5. **#2654 – `session_store_sql` silently returns empty when session sync is local** ([link](https://github.com/github/copilot-cli/issues/2654))  
   *Area: sessions, tools* — The tool is injected into agent system messages even when cloud store is disabled, returning 0 rows with no indication. 2 comments.

6. **#3957 – Unable to scroll through history using trackpad on MBP** ([link](https://github.com/github/copilot-cli/issues/3957))  
   *Area: input-keyboard, terminal-rendering* — Trackpad scrolling selects prompts instead of scrolling the window. Affects Ghostty terminal. 1 comment, 1 👍.

7. **#3948 – `web_fetch`: TypeError: fetch failed** ([link](https://github.com/github/copilot-cli/issues/3948))  
   *Area: networking, tools* — All `web_fetch` tool calls fail even when other networking works. 1 comment.

8. **#3958 – Windows: v1.0.66 fails to start stdio MCP servers with .bat/.cmd args** ([link](https://github.com/github/copilot-cli/issues/3958))  
   *Area: platform-windows, mcp* — Regression preventing MCP server startup when command is a batch file with arguments. 1 comment.

9. **#3904 – CloudQueryError prevents `/chronicle` standup despite local fallback** ([link](https://github.com/github/copilot-cli/issues/3904))  
   *Area: sessions* — Cloud session store errors block the standup feature even when local data is available. 1 comment.

10. **#3962 – Copilot 1.0.65 not working** ([link](https://github.com/github/copilot-cli/issues/3962))  
    *No area label* — User reports the CLI shows startup messages but fails to process commands. 1 comment.

---

## Key PR Progress
*No pull requests were updated in the last 24 hours.*

---

## Feature Request Trends

- **Session Organization & Discovery** — Multiple requests for user-defined tags on sessions (#3970), plan status indicators (#3969), and a full file-tree browser for repository-backed sessions (#3971). Users want better visual cues and filtering as active session counts grow.
- **Enterprise Configuration Management** — Org admins are seeking server-managed settings for local CLI installs (#3909), especially for environment variables, which currently only work in cloud environments.
- **Editing Improvements** — There is demand for better integration between compact paste and $EDITOR workflows (#3936), including automatic token expansion when editing prompts.
- **Session Lifecycle Visibility** — Users want to see session retention/expiration dates from the status line (#3963) and understand when sessions will be automatically cleared.

---

## Developer Pain Points

- **Alt-Screen Disruption** — The forced alt-screen terminal rendering (#1799) is a top frustration, with users seeking a simple toggle to revert to the original mode.
- **Session Hangs & Orphaning** — Agents sessions that run indefinitely (#2364) with no kill mechanism, and orphaned sessions persisting for months (#3600), are causing significant productivity loss.
- **Silent Tool Failures** — The `session_store_sql` returning empty without warning when cloud sync is local (#2654) and `web_fetch` consistently failing (#3948) erode trust in the CLI’s tool ecosystem.
- **Windows MCP Regression** — A breaking change in v1.0.66 prevents stdio MCP servers from starting when the command is a `.bat`/`.cmd` file with arguments (#3958), impacting Windows users heavily.
- **Terminal Rendering Artifacts** — Ghost characters remaining after deletion (#3959) and trackpad scrolling selecting prompts instead of scrolling (#3957) point to TUI rendering issues that break the core editing experience.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

# Kimi Code CLI Community Digest — 2026-06-30

## Today's Highlights
Community attention is split between two unresolved concerns: a long-standing file-reading loop bug (Issue #640, open since January) and a new UI/UX friction point around Enter key behavior on mobile and desktop (Issue #2479, filed yesterday). No new releases or pull requests arrived in the last 24 hours, suggesting the team may be consolidating work toward a future patch.

## Releases
*None in the last 24 hours.*

## Hot Issues

**#640 – [bug] Kimi CLI stuck in reading one file again and again and stuck in a loop**  
Opened Jan 2026 by `isbafatima90-arch`, last updated Jun 28. 15 comments, 1 👍.  
A user running Kimi CLI 0.76 on Arch Linux with a custom Anthropic endpoint (`mimo-v2-flash`) reports the CLI enters an infinite loop repeatedly reading the same file. Despite being open for months, the issue remains unassigned. The single upvote and lack of resolution suggest either a narrow reproduction environment or insufficient maintainer bandwidth.  
[🔗 GitHub](https://github.com/MoonshotAI/kimi-cli/issues/640)

**#2479 – [enhancement] Bad usage of return and enter for desktop and mobile**  
Opened Jun 29 by `Dealazer`, 0 comments, 0 👍 (new).  
On mobile, pressing Enter immediately sends the prompt, making multi-line input impossible. On desktop, new lines require Shift+Enter, which is non-standard for terminal editors. This is a critical UX regression for any user who writes complex prompts. Expect rapid community upvote growth.  
[🔗 GitHub](https://github.com/MoonshotAI/kimi-cli/issues/2479)

## Key PR Progress
*No pull requests were updated in the last 24 hours.*

## Feature Request Trends
The most requested feature direction emerging from recent open issues is **input ergonomics** — specifically decoupling the "send" action from the "newline" key across form factors. This is a rare case where mobile and desktop users share the same pain point: the current Enter key behavior penalizes multi-line prompt authors on both platforms.

A secondary long-tail pattern is **custom endpoint stability**. Issue #640 (loop bug) and several other unresolved tickets hint at brittleness when connecting to non-default backends, especially with streaming or file-attachment workflows.

## Developer Pain Points
- **Unresponsive loop behavior** with custom Anthropic endpoints — the CLI fails to detect end-of-file or break out of a read cycle, making it unusable until killed. No workaround has been shared.
- **Enter key ambiguity** — the lack of a mode toggle (e.g., Ctrl+Enter to send, plain Enter for newline) forces uncomfortable key chords or accidental sends, disrupting flow on both mobile and desktop.
- **Slow issue resolution** — Issue #640 is 6 months old with no assignee. Developer trust erodes when fundamental bugs go unaddressed while new feature requests pile up.

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

# OpenCode Community Digest — 2026-06-30

## Today's Highlights
While no new releases dropped today, the community is buzzing with progress on the **V2 client migration** and **observability hooks**. A major performance PR landing — reducing diff rendering from O(n²) to linear — addresses long-standing complaints about large-file hangs. Meanwhile, new issues around **GLM-5.2 compatibility** and **data loss after updates** signal growing pains as the platform adds more provider integrations and storage migrations.

## Releases
No new releases in the last 24 hours. Latest stable remains **v1.17.11** (Desktop).

## Hot Issues
1. **[#24316] — Progress halts with qwen 3.6 35b-a3b with naked tool call**  
   (*boutell*, 18 comments)  
   A tricky bug where a bare `<tool_call>` token causes the model to stall mid-reasoning. Community suspects it's a cross-stack issue involving llama.cpp, Qwen, and OpenCode.  
   [🔗](https://github.com/anomalyco/opencode/issues/24316)

2. **[#19604] — Write tool fails silently on large files (~1000+ lines)**  
   (*jdocker8*, 14 comments, 👎 9)  
   High-impact regression — `Write` tool returns a failure with no error for large files. Multiple retries don't help; users are blocked on refactoring tasks.  
   [🔗](https://github.com/anomalyco/opencode/issues/19604)

3. **[#19466] — opencode is using CPU for doing nothing!**  
   (*Jaaaky*, 11 comments, 👎 9)  
   While waiting on API rate limits, OpenCode pins a CPU core at ~50%, wasting battery. Community frustrated by lack of sleep/polling mechanism.  
   [🔗](https://github.com/anomalyco/opencode/issues/19466)

4. **[#34359] — Track TUI migration to @opencode-ai/client**  
   (*kitlangton*, 3 comments)  
   A tracking issue for the critical V2 migration effort — moving the TUI from legacy SDK to the new generated Promise client. Signals major refactoring underway.  
   [🔗](https://github.com/anomalyco/opencode/issues/34359)

5. **[#33490] — GLM-5.2 via OpenCode Go: extra inputs not permitted, field instructions**  
   (*nghiant-rez*, 4 comments, 👎 3)  
   A provider schema mismatch — Zhipu's GLM-5.2 rejects `instructions` field. Blocks Chinese-market users and highlights broader provider compatibility needs.  
   [🔗](https://github.com/anomalyco/opencode/issues/33490)

6. **[#34443] — Skill file changes not picked up until app restart**  
   (*vokasug*, 1 comment)  
   A cache-never-evict bug means users must restart the entire desktop app to see SKILL.md edits. High friction for iterative skill development.  
   [🔗](https://github.com/anomalyco/opencode/issues/34443)

7. **[#34222] — GitHub Copilot MAI-Code-1-Flash not accessible**  
   (*mathomp4*, 4 comments, 👎 4)  
   Microsoft's new MAI-Code-1-Flash model returns "not accessible" via `/chat/completions`. Likely a missing model ID mapping in the Copilot provider.  
   [🔗](https://github.com/anomalyco/opencode/issues/34222)

8. **[#34447] — Corrupted SQLite: Every tool call returns no such column: "data"**  
   (*Transformerhuman*, 1 comment)  
   A severe storage corruption — all tools fail with SQLite error. Platform Windows, suggests a migration bug in the new DB schema.  
   [🔗](https://github.com/anomalyco/opencode/issues/34447)

9. **[#34445] — Data loss: update recreated ~/.local/share/opencode**  
   (*lisaleezer85*, 1 comment)  
   Storage migration to SQLite recreated the data directory without migrating legacy sessions. Users lost all history. 
   [🔗](https://github.com/anomalyco/opencode/issues/34445)

10. **[#34442] — Windows Desktop installer broken offline: ripgrep not bundled**  
    (*vokasug*, 1 comment)  
    Core tools (`grep`, `glob`, `skill`) require ripgrep, but it's not bundled in the offline installer. Effectively bricks the app on air-gapped machines.  
    [🔗](https://github.com/anomalyco/opencode/issues/34442)

## Key PR Progress
1. **[#33523] — feat: Add LLM and session observability hooks**  
   (*billxbf*)  
   Adds four plugin SDK hooks (LLM stream, tool execution, agent-run) for external monitoring — a long-requested capability for debugging and telemetry.  
   [🔗](https://github.com/anomalyco/opencode/pull/33523)

2. **[#34454] — feat(llm): add tool schema projections**  
   (*nexxeln*)  
   Named tool schema projections for OpenAI, Gemini, Moonshot — makes provider-specific schema transforms reusable, reducing compatibility bugs.  
   [🔗](https://github.com/anomalyco/opencode/pull/34454)

3. **[#34452] — feat: support opt-in previous_response_id chaining for OpenAI Responses API**  
   (*joaomj*)  
   Allows OpenAI to use `store:true` and chain responses, cutting latency by reusing context instead of replaying full history. Currently blocked by `store: false` default.  
   [🔗](https://github.com/anomalyco/opencode/pull/34452)

4. **[#34441] — fix: preserve Bedrock DeepSeek model ids**  
   (*YeEmrick*)  
   Fixes cross-region prefixing that broke DeepSeek V3.2 on Bedrock — changes `us.deepseek.v3.2` back to `deepseek.v3.2`.  
   [🔗](https://github.com/anomalyco/opencode/pull/34441)

5. **[#34415] — fix(ui): prepare diffs off the render thread**  
   (*jerrydong1988*)  
   Moves expensive diff computation to a Web Worker. Fixes UI freezes on large diffs (e.g., C++ projects like llama.cpp).  
   [🔗](https://github.com/anomalyco/opencode/pull/34415)

6. **[#34414] — fix(app): avoid O(n²) dedup hang on large diff summaries**  
   (*jerrydong1988*)  
   Fixes ~600M comparisons in `constructMessageRows` by replacing nested `some()`/`reduceRight` with a hash map.  
   [🔗](https://github.com/anomalyco/opencode/pull/34414)

7. **[#34381] — refactor(tui): wire generated client reads**  
   (*kitlangton*)  
   First milestone in the TUI V2 migration — wires `@opencode-ai/client` alongside the legacy SDK, with direct reads migrated.  
   [🔗](https://github.com/anomalyco/opencode/pull/34381)

8. **[#34453] — refactor(core): convert opencode tests to nodes**  
   (*jlongster*)  
   Converts tests to LayerNode graphs — better isolation and testability for the core engine.  
   [🔗](https://github.com/anomalyco/opencode/pull/34453)

9. **[#34419] — feat(desktop): add setting to swap panel layout side**  
   (*ultrinnan*)  
   Simple toggle in Settings > Appearance to move the side panel (chat/editor) to the opposite side.  
   [🔗](https://github.com/anomalyco/opencode/pull/34419)

10. **[#31517] — fix(app): reduce reactive cascade overhead on session switch**  
    (*BYK*)  
    Reduce web-UI re-rendering during session switches by eliminating unnecessary state updates and Shiki re-highlighting during streaming.  
    [🔗](https://github.com/anomalyco/opencode/pull/31517)

## Feature Request Trends
- **TUI V2 migration** — Multiple issues track moving from legacy `@opencode-ai/sdk/v2` to the new `@opencode-ai/client` (e.g., #34359, #34450).
- **Observability & debugging** — Hooks for LLM streams, tool execution, and agent-run logging (#33523).
- **Offline/resilience** — Bundle ripgrep into Windows builds (#31734, #34442), improve failover when API providers are down.
- **Side panel & layout customization** — Swap panel side (#34419), collapse/save sidebar state (linked in #14054).
- **Stricter fuzzy-edit feedback** — Expose when edit tool falls back to fuzzy matching (#34424) for better SWE-bench reliability.

## Developer Pain Points
- **Data loss after storage migration** — Two issues (#34445, #34447) report SQLite corruption or complete session loss after the update to the new database schema. Windows users hit hardest.
- **Provider compatibility breaking** — GLM-5.2 (#33490), MAI-Code-1-Flash (#34222), and Bedrock DeepSeek (#34412) all suffer from model ID mismapping or schema rejections.
- **Write tool failures on large files** — `Write` silently fails for files >1000 lines (#19604), blocking refactoring workflows.
- **CPU waste on rate-limit waits** — Even idle wait loops peg a core at 50% (#19466), with no polite polling/sleep.
- **Cache staleness** — Skill files (#34443) and AGENTS.md (#34341) not picked up until restart, forcing repeated app reloads.
- **Session compaction destroying context** — Old issue #2945 resurfaces with new users hitting mid-session compaction that wipes the agent's memory.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>

# Pi Community Digest — 2026-06-30

## Today's Highlights
The past 24 hours saw a flurry of activity around authentication and provider improvements, with several merged fixes for Anthropic OAuth token detection and Bedrock API key handling. A critical stability fix has been merged to prevent crashes from hung streams on Bedrock, while the community continues to debate the model for handling `navigateTree()` on extension contexts. No new releases were published today.

## Releases
No new releases in the last 24 hours.

## Hot Issues

### 1. **openai-codex Connection Reliability Issues** [#4945](https://github.com/earendil-works/pi/issues/4945)
Open (in progress). The `openai-codex` / `gpt-5.5` provider leaves the interactive TUI stuck on "Working..." with no streamed text, tool call, or error. Recovery requires pressing Escape to abort. This has occurred repeatedly over days, with 72 comments and 30 👍 reactions indicating widespread impact. The issue is actively being investigated.

### 2. **Streaming markdown forces scroll to bottom** [#5825](https://github.com/earendil-works/pi/issues/5825)
Closed. When `clear on shrink` is enabled, fast agent output forces the terminal to scroll to the bottom, disrupting users who try to read earlier content. The fix has been merged via PR #6026. 38 comments.

### 3. **LLM cache not working with z.ai GLM coding plan** [#6083](https://github.com/earendil-works/pi/issues/6083)
Closed. Multi-step tasks with z.ai's GLM Coding Plan burn session limits extremely fast because the cache fails on every tool turn. Conversational turns were OK, but write/edit tool calls could consume 10–20% of session per task. 8 comments, 9 👍.

### 4. **Anthropic OAuth-token detection is hardcoded to sk-ant-oat** [#5871](https://github.com/earendil-works/pi/issues/5871)
Open (in progress). The code uses a hardcoded prefix check (`sk-ant-oat...`) to detect OAuth tokens, but Claude Code scoped keys follow the regular `sk-ant-api03-..` format, meaning they're misclassified. 6 comments. Community is watching PR #6148 for a fix.

### 5. **Providers swallow HTTP error bodies** [#5763](https://github.com/earendil-works/pi/issues/5763)
Closed. Behind proxies/gateways, non-2xx responses with parseable bodies are dropped, producing unreadable errors like `Unknown: UnknownError` (Bedrock) or `403 status code (no body)` (OpenAI). Fix merged in PR #5832. 5 comments.

### 6. **Repeated tool calls can loop without interruption** [#6158](https://github.com/earendil-works/pi/issues/6158)
Closed (no-action). An agent got stuck repeating `ls` commands 6+ times instead of progressing. The issue was observed but determined to be a model behavior rather than a code bug. 3 comments.

### 7. **Devnagri breaking the Pi harness** [#6124](https://github.com/earendil-works/pi/issues/6124)
Open (bug). Typing Devnagri script characters (e.g., `नेटवर्क`) corrupts the TUI rendering. This is a Unicode rendering bug that breaks CJK/Indic language support. 3 comments, still unaddressed.

### 8. **`find` corrupts paths on Windows drive root** [#6104](https://github.com/earendil-works/pi/issues/6104)
Open (bug). When searching from `C:\` or `I:\`, the `find` tool drops the first character of the first path segment and doubles trailing slashes on directories. Windows-specific path handling bug. 3 comments.

### 9. **OpenAI Responses API mislabels empty tool results** [#6103](https://github.com/earendil-works/pi/issues/6103)
Open (bug). When a tool returns empty output on success, the OpenAI handler labels it as "(see attached image)" — misleading to the model and downstream tool chaining. A fix is in PR #6156. 2 comments.

### 10. **Pi startup time too slow** [#6075](https://github.com/earendil-works/pi/issues/6075)
Closed (no-action). v0.80.2 on Fedora Linux 42 takes ~10 seconds to load the TUI, which users find excessive. The report was noted but no actionable fix was identified. 2 comments.

## Key PR Progress

### 1. **fix(ai): recover from hung streams and retry unmodeled Bedrock errors** [#6051](https://github.com/earendil-works/pi/pull/6051) — Merged
Adds `streamIdleTimeoutMs` (240s) and `connectTimeoutMs` to prevent half-open sockets from blocking streams indefinitely. Also retries unmodeled Bedrock errors. Directly addresses the reliability concerns in #4945.

### 2. **fix(ai): surface provider HTTP error body instead of opaque SDK message** [#5832](https://github.com/earendil-works/pi/pull/5832) — Merged
Fixes #5763 by ensuring Gateway/Proxy error bodies are surfaced in provider error messages instead of being silently dropped.

### 3. **fix(tui): stabilize working status row** [#6026](https://github.com/earendil-works/pi/pull/6026) — Merged
Fixes the scroll-to-bottom issue (#5825) caused by `clear on shrink` triggering full re-renders of the TUI.

### 4. **fix(ai): map Bedrock apiKey auth to bearer token env** [#6161](https://github.com/earendil-works/pi/pull/6161) — Merged
Maps the `apiKey` field to `AWS_BEARER_TOKEN_BEDROCK` environment variable before Bedrock API calls, cleaning up duplicated auth options. Fixes #6163.

### 5. **fix(ai): return empty string for empty tool results instead of '(see attached image)'** [#6156](https://github.com/earendil-works/pi/pull/6156) — Merged
Fixes #6103 by returning empty strings for tool calls that return no output, instead of misleading "see attached image" labels.

### 6. **fix(ai): support Anthropic bearer token env** [#6148](https://github.com/earendil-works/pi/pull/6148) — Open (to-discuss)
Attempt to fix #5871 by allowing providers to explicitly declare OAuth/Bearer tokens. Author notes interface limitations and isn't satisfied with the current approach. Community discussion ongoing.

### 7. **Add built-in --profile support for isolated Pi state** [#3966](https://github.com/earendil-works/pi/issues/3966) — Closed
Implements `--profile <name>` and `PI_PROFILE` env var for isolated auth, sessions, settings, models, and extensions. Useful for keeping work/personal/local-LLM setups separate.

### 8. **feat(agent): let a steering message opt out of waking the agent when it's done** [#5895](https://github.com/earendil-works/pi/issues/5895) — Closed
Adds a flag to steering messages so they are appended only if the agent is still running, preventing unnecessary wake cycles. 4 comments.

### 9. **Add Charm Hyper as a built-in provider** [#6042](https://github.com/earendil-works/pi/issues/6042) — Closed (no-action)
Request to add `https://hyper.charm.land` as a built-in provider with model listing and API key resolution. Was noted but not acted upon.

### 10. **Package Report: pi-wiki impersonation** [#6155](https://github.com/earendil-works/pi/issues/6155) — Closed
Reports that the `pi-wiki` package has broken repo/homepage URLs (404), making source validation impossible. Community flagged this as potential impersonation.

## Feature Request Trends

1. **Provider Expansion**: Strong demand for additional built-in providers — Charm Hyper (#6042), Scaleway Generative APIs (#6165), and better customization for existing ones (Xiaomi MiMo pricing fix #6138, Kimi Coding base64 handling #6164).

2. **Enterprise/Administration Controls**: Growing interest in admin-level configuration from `/etc` / `%ProgramData%` that overrides user and project settings (#6159), and profile isolation for multi-context use (#3966).

3. **Better Multilingual & Unicode Support**: Issues with Devnagri (#6124) and compaction summaries not respecting session language (#6157) highlight gaps in non-English localization.

4. **Extension API Deepening**: Requests to expose `navigateTree()` on ExtensionContext (#5932), and better handling of extension dependency side effects on reload (#6108).

5. **Provider Auth Flexibility**: Multiple requests for configurable auth token detection (not just hardcoded prefix checks), including Anthropic (#5871) and Bedrock (#6163).

## Developer Pain Points

1. **Provider Connection Instability**: Openai-codex/gpt-5.5 connections hang frequently with no error feedback (#4945), and ECONNRESET during streaming crashes the entire process (#6133). This is the top frustration by comment count.

2. **Opaque Error Handling**: Providers swallow HTTP error bodies (#5763), making debugging across gateways/proxies nearly impossible. The fix in #5832 is welcome but wider adoption is needed.

3. **Session Cost Overruns**: z.ai GLM session limits burn through 10-20% per task due to cache issues (#6083), and Xiaomi MiMo pricing is hardcoded incorrectly (#6138), causing unexpected charges.

4. **Windows Path Handling**: `find` tool corrupts paths on bare drive roots (#6104), and session folder collisions occur when paths differ only by directory structure (#4877).

5. **Tool Call Loop Traps**: Models can get stuck repeating the same tool call (#6158), and tools that return empty output are mislabeled as having images (#6103), confusing downstream model reasoning.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>

# Qwen Code Community Digest — 2026-06-30

## Today's Highlights
The Qwen Code community is buzzing with activity: over 30 issues and 50 PRs updated in the last 24 hours, with a strong focus on **daemon stability**, **UI rendering fixes**, and **session memory management**. A notable bug concerning zombie sessions burning excessive tokens (Issue #5964) has drawn significant attention, while several feature requests around autonomous `/loop` modes and hot-reloadable configurations signal the community's desire for more resilient, long-running workflows.

## Releases
No new releases in the last 24 hours.

## Hot Issues (Top 10)

1. **[#5964: Zombie sessions burning 30M tokens](https://github.com/QwenLM/qwen-code/issues/5964)**  
   *Priority: P1 | Type: Bug*  
   A "zombie agent" ran for 8 hours unnoticed, silently consuming DeepSeek API tokens without any logging or automatic disconnect. The community is demanding better session timeout enforcement and usage tracking. User **aspnmy** reported the issue with vivid detail, highlighting a critical reliability gap in daemon mode.

2. **[#5975: No stream activity after 120s timeout](https://github.com/QwenLM/qwen-code/issues/5975)**  
   *Priority: P2 | Type: Bug*  
   After upgrading to v0.19.3, users report that the agent stalls for 2+ minutes before erroring out. The agent appears to "think" but never produces output. This is a regression impacting daily workflows, with 5 comments and growing community frustration.

3. **[#5800: Last line of tall replies overwritten in TUI](https://github.com/QwenLM/qwen-code/issues/5800)**  
   *Priority: P2 | Type: Bug*  
   In the default static TUI mode, assistant replies taller than the terminal height have their last line hidden upon completion. This breaks readability for long outputs. User **MikeWang0316tw** traced the root cause to an upstream Ink library bug (Ink #973).

4. **[#5736: More frequent full prompt reprocessing](https://github.com/QwenLM/qwen-code/issues/5736)**  
   *Priority: Unassigned | Type: Bug*  
   A recent update causes local LLMs to re-process the full conversation history even during normal continuation, negating caching benefits. User **fantasyz** observed this via llama.cpp logs, and the issue is tagged `welcome-pr` for community contributions.

5. **[#5942: Anthropic prompt-cache misses inflating cost](https://github.com/QwenLM/qwen-code/issues/5942)**  
   *Priority: P2 | Type: Bug*  
   When using Anthropic-backed endpoints, Qwen Code suffers two independent cache-miss issues that Claude Code avoids. Side-queries use different prefixes, and conversation breakpoints sit on a moving last message, inflating token costs significantly.

6. **[#5970: Auto-enter Plan mode from Yolo mode](https://github.com/QwenLM/qwen-code/issues/5970)**  
   *Priority: P2 | Type: Bug*  
   A regression in the latest version causes `qwen -y` to switch into Plan mode automatically and prompt for file read permissions, defeating the purpose of Yolo mode. The agent also fails to write plan markdown correctly.

7. **[#5989: /auth changes not persisting across new sessions](https://github.com/QwenLM/qwen-code/issues/5979)**  
   *Priority: P2 | Type: Bug*  
   After using `/auth` to change model provider credentials, the current session works but new sessions still return 401 errors. This is a critical configuration persistence bug that undermines trust in the authentication system.

8. **[#6000: Mobile web-shell lacks session sidebar](https://github.com/QwenLM/qwen-code/issues/6000)**  
   *Priority: P3 | Type: Feature Request*  
   When accessing `qwen serve` from a mobile browser, the session list sidebar is hidden entirely with no mobile alternative. Users on smaller screens cannot switch sessions or create new ones without workarounds.

9. **[#5956: Configurable compaction model support](https://github.com/QwenLM/qwen-code/issues/5956)**  
   *Priority: P2 | Type: Feature Request*  
   Users want the ability to configure a lightweight model for conversation compaction, rather than using the expensive active model to summarize large contexts. This would reduce API costs and speed up compaction operations.

10. **[#6007: GLM-5.2 leaks thinking text as output](https://github.com/QwenLM/qwen-code/issues/6007)**  
    *Priority: P2 | Type: Bug*  
    When using `glm-5.2` via the OpenAI-compatible provider, internal reasoning text (including `<think>` tags) is emitted as normal assistant output, breaking response formatting and potentially leaking sensitive reasoning.

## Key PR Progress (Top 10)

1. **[#6026: Allow subagents to exit plan mode](https://github.com/QwenLM/qwen-code/pull/6026)**  
   *Author: doudouOUC*  
   Fixes subagent approval-mode overrides so subagents can properly leave plan mode after `exit_plan_mode` succeeds. This patch addresses a common workflow friction where subagents get stuck in unwanted modes.

2. **[#6015: Make non-VP transcript scrollable](https://github.com/QwenLM/qwen-code/pull/6015)**  
   *Author: chiga0*  
   Fixes two root causes preventing scroll behaviour in default transcript view during multi-agent runs. Previously, the view snapped to bottom or hijacked composer history — now users can review past output during rich runs like `/review`.

3. **[#6018: Avoid full-history clones in OOM-prone paths](https://github.com/QwenLM/qwen-code/pull/6018)**  
   *Author: yiliang114*  
   Prevents memory exhaustion by replacing full conversation history clones with compact diagnostic summaries in API error reporting and forked-agent cache snapshots. A critical fix for memory-constrained environments.

4. **[#5852: Resumable /acp session stream (Last-Event-ID)](https://github.com/QwenLM/qwen-code/pull/5852)**  
   *Author: chiga0*  
   Wires the `/acp` session event stream into the daemon's event-replay engine, enabling reconnection from where it left off using standard SSE `id:` lines. This is foundational for stable long-running sessions and network interruptions.

5. **[#6022: Inline one-shot model override in /model](https://github.com/QwenLM/qwen-code/pull/6022)**  
   *Author: TianYuan1024*  
   Implements Issue #5967: `/model <model-id> <prompt>` runs a single turn on a different model then reverts. No more two-step model switching for one-off tasks.

6. **[#5991: Autonomous mode for bare /loop](https://github.com/QwenLM/qwen-code/pull/5991)**  
   *Author: qqqys*  
   A bare `/loop` now arms a self-paced autonomous loop (previously just showed usage). This adds a "keep my work moving while I'm away" mode for maintaining PRs or fixing flaky CI autonomously.

7. **[#5953: LSP Server hot reload support](https://github.com/QwenLM/qwen-code/pull/5953)**  
   *Author: water-in-stone*  
   Adds runtime hot reload for native LSP server configuration, detecting `.lsp.json` changes during an active session without requiring restart. Part of the larger hot-reload tracking issue (#3696).

8. **[#6011: Mouse click & hover in alternate-screen mode](https://github.com/QwenLM/qwen-code/pull/6011)**  
   *Author: DragonnZhang*  
   Adds mouse interactions to the TUI when Virtualized History is enabled. Users can click in select menus, dialogs, and permission prompts — significantly improving usability.

9. **[#6005: Queue prompts while turns are running (web-shell)](https://github.com/QwenLM/qwen-code/pull/6005)**  
   *Author: ytahdn*  
   Implements server-side FIFO prompt queuing for web shell sessions, so messages submitted while a turn is running are accepted and processed in order. Includes UI controls to reorder or remove queued prompts.

10. **[#6025: Friendlier Esc interruption + queued-prompt UX](https://github.com/QwenLM/qwen-code/pull/6025)**  
    *Author: carffuca*  
    Pressing Esc during streaming now shows a two-press confirmation with a countdown ring, preventing accidental interruption. The send button becomes a stop control with visual feedback.

## Feature Request Trends
The community is pushing for three major feature directions:

1. **Autonomous & Long-Running Workflows** — Multiple requests for autonomous `/loop` modes (Issue #5990, PR #5991), daemon-managed channel workers (#5976), and hot-reloadable channels (#6010) indicate a strong desire for "set and forget" automation.

2. **Runtime Configuration Reloading** — Issue #3696 (hot-reload system) continues to see activity, with PRs landing for LSP hot reload (#5953) and further work on skills and MCP hot reload. Users want to change configs without restarting sessions.

3. **Model Management Flexibility** — Requests for configurable compaction models (#5956), inline model switching (#5967, PR #6022), and better support for local/custom providers (multiple issues) show the community wants finer-grained control over which models handle which tasks, especially to manage costs.

## Developer Pain Points
Recurring frustrations and high-frequency requests from the data:

1. **Daemon Stability & Memory Management** — Zombie sessions (#5964, #5792), OOM crashes on large histories (#6018), and memory leaks during compaction are persistent pain points. Developers are losing API credits and work to unreliable session lifecycle management.

2. **UI Regression & Rendering Bugs** — The TUI has several regressions in recent versions: lines being cut off (#5800), text scrolling from the beginning (#5971), Chinese IME support breaking (#5966), and file names no longer shown in tool calls (#6014). These degrade the core user experience.

3. **Cost & Token Management** — Anthropic cache misses (#5942), token counting inaccuracies in subagents (#5683), and lack of configurable compaction models (#5956) are costing users real money. The community wants more transparency and control over token usage.

4. **Configuration Persistence Issues** — `/auth` changes not persisting across sessions (#5979) and other configuration bugs erode user trust. Developers expect configuration changes to be durable and session-independent.

5. **Agent Mode Confusion** — The Yolo mode regression (#5970) and subagent plan mode issues (#6026) suggest the mode system needs hardening. Users want modes to work reliably and predictably, with clear feedback when they change.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>

# DeepSeek TUI Community Digest — 2026-06-30

## Today's Highlights

The 0.8.66 release candidate is finalizing with a flurry of CI reliability fixes: stale install snippets, accidental changelog deletions, and provider-inventory drift checks are all being hardened. The Hotbar UX and Auto mode redesigns are shaping up as the headline features for 0.8.67, with three open PRs improving localization and shortcut documentation. A new **Neuralwatt** provider request has appeared, and the legacy `.deepseek` → `.codewhale` migration saga has finally been resolved with three closed migration bugs.

## Releases

**No new releases in the last 24 hours.** The community is currently stabilizing the 0.8.66 candidate, with multiple release-blocker issues (##3766–3772) still open.

## Hot Issues

1. **[#3766 — Approval UI copy for session-scoped approvals](https://github.com/Hmbown/CodeWhale/issues/3766)** (RELEASE-BLOCKER)  
   The approval modal misleadingly says "always" when the runtime only grants approval for the current TUI session. Community reaction suggests ~1/3 of users assume persistent approval, risking accidental tool execution across sessions. One of several public-facing truth-in-labeling bugs being fixed before 0.8.66 ships.

2. **[#3768 — Accidental 0.8.52 changelog deletion](https://github.com/Hmbown/CodeWhale/issues/3768)** (RELEASE-BLOCKER)  
   The 0.8.66 diff removes the entire v0.8.52 section from the TUI changelog—looks like merge damage, not intentional cleanup. Currently a top CI concern.

3. **[#3772 — Unmapped ApiProvider variants pass check-facts](https://github.com/Hmbown/CodeWhale/issues/3772)** (RELEASE-BLOCKER)  
   New provider enum variants can be added without updating the website provider map, and `check:facts` still passes. `Openmodel` and `Sakana` are known unmapped. A PR fix is already open.

4. **[#3738 — Prompt-cache hit-rate regression](https://github.com/Hmbown/CodeWhale/issues/3738)**  
   A user reports rising costs, suggesting the `<turn_meta>` block may be busting DeepSeek's cacheable prefix. With cached input tokens ~10× cheaper, this regression could significantly impact power users.

5. **[#3765 — Expose SeamManager and CompactionConfig to config.toml](https://github.com/Hmbown/CodeWhale/issues/3765)**  
   Both engine mechanisms are hardcoded to `true`. A community PR (#3780) is already implementing the config knobs.

6. **[#3731 — Finish Hotbar activation affordances](https://github.com/Hmbown/CodeWhale/issues/3731)**  
   The 0.8.67 headline feature: `Alt-1` through `Alt-8` now documented, but needs terminal-aware support for function-key remapping and multichord terminals.

7. **[#3757 — Launch is slow](https://github.com/Hmbown/CodeWhale/issues/3757)**  
   A symptom-first report from the maintainer noting noticeable startup lag. PR #3761 moves cleanup work off the synchronous path.

8. **[#3725 — Provider picker "needs-auth" is inaccurate for API-key providers](https://github.com/Hmbown/CodeWhale/issues/3725)**  
   Closed as fixed, but the issue garnered significant community attention: labeling every API-key provider as `needs-auth | auth:missing` was widely perceived as a readiness regression.

9. **[#3732 — Modal UI/UX broken across all modals](https://github.com/Hmbown/CodeWhale/issues/3732)**  
   Content bleed-through, no opaque backdrop, and action-row truncation in the shared modal renderer. Affects all confirmation and approval popups.

10. **[#3724 — Sessions appear lost after .deepseek → .codewhale migration](https://github.com/Hmbown/CodeWhale/issues/3724)**  
    Three compounding gaps caused session history to vanish on upgrade. Now closed with PR #3761 providing fallback read paths and migration notices.

## Key PR Progress

1. **[#3773 — Label session-scoped approval honestly, not "always"](https://github.com/Hmbown/CodeWhale/pull/3773)**  
   Fixes #3766 (RELEASE-BLOCKER). Changes "Approve always for this kind" to match the actual session-scoped behavior.

2. **[#3777 — Fail check-facts on unmapped ApiProvider variants](https://github.com/Hmbown/CodeWhale/pull/3777)**  
   Fixes #3772. `deriveProviders()` now fails CI instead of silently skipping unmapped providers. Maps `Openmodel` and `Sakana`.

3. **[#3778 — Stop sync-changelog dropping a release for Unreleased](https://github.com/Hmbown/CodeWhale/pull/3778)**  
   Fixes #3768. The rolling KEEP=15 window was counting `## [Unreleased]` as a section, causing the oldest released version to drop when Unreleased had content.

4. **[#3774 — Honor codewhaleBinaryVersion in npm installer](https://github.com/Hmbown/CodeWhale/pull/3774)**  
   Fixes #3769. The installer was the sole npm path ignoring `codewhaleBinaryVersion`, causing install-time asset resolution drift.

5. **[#3779 — Guard public install/version snippets](https://github.com/Hmbown/CodeWhale/pull/3779)**  
   Fixes #3767. Now checks `codewhale --version   # X.Y.Z` lines and `docs/INSTALL.md` npm-wrapper pointers in addition to README `--tag` examples.

6. **[#3756 — Default interactive Agent shell to approval-gated on](https://github.com/Hmbown/CodeWhale/pull/3756)**  
   Exposes shell tools by default for interactive Agent-mode TUI, so approval gates actually function. Keeps durable task defaults unchanged.

7. **[#3761 — Defer startup maintenance cleanup](https://github.com/Hmbown/CodeWhale/pull/3761)**  
   Fixes #3757. Moves stale tool-output pruning and old-session cleanup to a delayed background thread, protecting the interactive startup path.

8. **[#3785 — Localize Hotbar setup wizard](https://github.com/Hmbown/CodeWhale/pull/3785)**  
   Fixes #3759. Localizes all wizard chrome, slot labels, validation errors, and action descriptions for non-English locales.

9. **[#3763 — Define localization matrix with locale registry and drift checks](https://github.com/Hmbown/CodeWhale/pull/3763)**  
   Canonical tracking document for 9 locales across website and README surfaces. Includes Russian as next-priority and Arabic as RTL deferred.

10. **[#3780 — Expose context compaction gates](https://github.com/Hmbown/CodeWhale/pull/3780)**  
    Closes #3765. Adds `[compaction].enabled` and `[seam_manager].enabled` as config.toml switches while keeping existing behavior compatible.

## Feature Request Trends

1. **Provider expansion** — Three provider-related requests in the last 48 hours: Neuralwatt (with innovative non-token pricing), Openmodel, and Sakana. The community clearly wants maximal provider flexibility, especially for cost-optimized pricing models.

2. **Configuration discoverability** — A recurring theme across #3765 (expose Seam/Compaction configs), #3764 (improve /config diagnostics), and #3759 (localize setup wizards). Users want to understand and customize engine behavior without reading source code.

3. **Hotbar customization** — The v0.8.67 Hotbar feature is attracting localization (##3759, #3785), shortcut QA (##3758, #3782), and terminal remapping requests. The community expects first-class keyboard customization support.

4. **Localization depth** — #3091 (website parity for Japanese/Vietnamese), #3759 (Hotbar wizard), and #3763 (locale registry) show the community expects more than README translations—they want the full UI localized, including setup wizards and error messages.

## Developer Pain Points

1. **CI reliability** — Six release-blocker issues (##3766–3772) all relate to CI gates that pass despite stale or broken artifacts (changelog deletions, install-snippet drift, provider-inventory gaps). Developers are frustrated by "green" gates that don't actually catch common failures.

2. **Cost surprises** — #3738 (prompt-cache regression) highlights that small prompt-structure changes can have significant cost impact without visible symptoms. Developers building on DeepSeek's caching need better cost telemetry.

3. **Silent data migrations** — The `.deepseek` → `.codewhale` migration issues (#3724, #3726, #3727) caused widespread panic when sessions appeared lost after upgrade. Three compounding root causes turned a normal migration into a community trust issue.

4. **Mode semantics confusion** — Auto mode behaving identically to Agent (#3733), Plan mode not blocking write tools (#3734), and YOLO mode silently approving publish actions (#3735) all eroded trust in mode promises. Developers want mode enforcement to match documentation exactly.

5. **Terminal compatibility** — Hotbar Alt-key QA (##3758, #3782) and slow startup (#3757) reflect ongoing friction with terminal-specific behavior. Developers using WSL2, Tmux, or non-standard terminal emulators encounter inconsistent UI behavior.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*