# AI CLI Tools Community Digest 2026-07-10

> Generated: 2026-07-10 01:59 UTC | Tools covered: 9

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

### 1. Ecosystem Overview

The AI CLI tools ecosystem is experiencing rapid maturation, with Claude Code, OpenAI Codex, and Gemini CLI leading as the most feature-complete platforms while newer entrants like Kimi Code CLI, OpenCode, Pi, Qwen Code, and DeepSeek TUI race to close feature gaps. A clear bimodal landscape is emerging: established tools focus on enterprise reliability and cost control, while challengers prioritize interoperability, multi-model support, and orchestration flexibility. Token cost management, model reliability in long sessions, and cross-platform stability have become universal pain points across all major tools. The pace of releases remains high—over 16 patches and features shipped across the ecosystem in just 24 hours.

---

### 2. Activity Comparison

| Tool | Hot Issues | Critical/Resolved | New PRs | Latest Release | Release Velocity |
|------|-----------|------------------|---------|----------------|------------------|
| **Claude Code** | 10 active | 3 critical (#73365, #67606, #64961) | 3 merged | v2.1.206 (today) | Regular bi-weekly |
| **OpenAI Codex** | 10 active | 2 critical (#28879, #30364) | 10 merged | v0.144.1 (today) | Fast-follow patches |
| **Gemini CLI** | 10 active | 4 P1 bugs | 10 open/merged | v0.52.0-nightly (today) | Nightly cadence |
| **GitHub Copilot CLI** | 10 active | 2 critical TUI regressions | 0 new in 24h | v1.0.70 (yesterday) | Monthly+ hotfixes |
| **Kimi Code CLI** | 10 active | 2 long-standing bugs | 10 open | v2.6 (stable) | Slower cadence |
| **OpenCode** | 10 active | 1 critical auth + 1 clipboard | 10 merged | v1.17.18 (today) | Multiple daily |
| **Pi** | 10 active | 1 context window bug fixed | 10 merged | v0.80.6 (today) | Regular |
| **Qwen Code** | 10 active | 2 P1 security/resource bugs | 10 open | v0.19.8-nightly (today) | Nightly |
| **DeepSeek TUI** | 10 active | 1 constitution compliance issue | 10 merged | v0.8.68 (today) | Milestone-driven |

**Key insight**: 6 of 9 tools shipped releases in the last 24 hours. DeepSeek TUI and OpenCode show the highest PR throughput, while Copilot CLI and Kimi Code have slower iteration but larger user bases.

---

### 3. Shared Feature Directions

**Multi-Model & Provider Flexibility** (All tools)
- Claude Code: Model selection per routine (#72871)
- Codex: GPT-5.6 Sol model support, MultiAgent V2
- Gemini CLI: AST-aware tools to reduce token waste (#22745)
- Copilot CLI: Model switching between planning/execution (#2792)
- Pi: `max` thinking level across providers (#6097)
- OpenCode: Auto-discovery of available models (#35855)
- Qwen Code: Subagent model isolation
- DeepSeek TUI: xAI Grok integration (#4257)

**Token Cost & Context Management** (All tools, critical)
- Claude Code: 2-3x token regression (#64961), runaway scheduled tasks (#75989)
- Codex: 10-20x rate-limit cost jump (#28879), reasoning token clustering (#30364)
- Gemini CLI: Config exclusion from workspace context (nightly fix)
- Copilot CLI: ~29K token overhead in system prompt (#2627)
- Pi: Context length overflow (#6378), stale budget after compaction (#6464)
- OpenCode: High CPU/memory usage in long sessions (#30086)
- Qwen Code: Glob OOM on large repos (#6614)

**Agent Reliability & Observability** (Claude Code, Codex, Gemini, OpenCode, Qwen Code, DeepSeek TUI)
- Subagent hang detection, termination transparency, trace visibility
- Real-time subagent status in TUI (OpenCode #36042, Qwen Code #6569)
- Fleet/Workflow/Lane orchestration model (DeepSeek TUI #4175)

**Cross-Platform Parity** (All tools)
- Windows regressions: Claude Code Cowork (#76187), Copilot TUI freezes (#4069, #4097)
- macOS code signing: Copilot CLI Gatekeeper (#970)
- Alpine Linux: Copilot CLI segfault (#107, 9 months open)
- Android/Termux: DeepSeek TUI (#4236), Qwen Code CUA driver

**Enterprise & Security** (Claude Code, Codex, Copilot CLI, Kimi Code, Qwen Code)
- Custom CA/SSL bypass: Codex (#31831), Kimi (#2458, #2437)
- Credential leakage: Qwen Code shell subprocess (#6601)
- Auth precedence: Claude Code env var override (#70124)
- RBAC & sandboxing: Codex URI permission transforms, DeepSeek TUI extension crate

---

### 4. Differentiation Analysis

| Dimension | Claude Code | OpenAI Codex | Gemini CLI | Copilot CLI | Kimi Code | OpenCode | Pi | Qwen Code | DeepSeek TUI |
|-----------|-------------|--------------|------------|-------------|-----------|----------|-----|-----------|--------------|
| **Primary Model** | Anthropic Opus | OpenAI GPT-5.x | Gemini | Multi-LLM (BYOK) | Moonshot Kimi | Multi-model | Multi-model | Qwen 3.x | Multi-model |
| **Core Differentiator** | Slash commands, Claude.md, Cowork collaboration | Rate-limit/billing system, ChatGPT integration | Subagent architecture, Memory system | GitHub-native, fleet mgmt | Cross-tool interop (Claude.md) | V2 TUI, observability | `max` thinking, extension SDK | Multi-workspace daemon, ACP protocol | Constitution-based orchestration |
| **Target User** | Full-time developers, enterprise teams | OpenAI subscribers, ChatGPT ecosystem | Google Cloud developers | GitHub enterprise | Enterprise Asia-Pacific | OSS enthusiasts, power users | Developer tool builders | Chinese developers, C-end users | OSS community, agent power users |
| **Orchestration** | Basic subagents | MultiAgent V2 | Subagent tree | Fleet (basic) | Simple agents | Subagent sidebar | Extensions | Workspace daemon | Fleet/Workflow/Lane |
| **Key Pain Point** | Advisor unavailable, Windows regressions | Cost anomalies, macOS binary missing | Subagent hangs, auth loops | TUI instability, Alpine segfault | SSL, rate limit bugs | Clipboard, undo broken | Context budget confusion | OOM, credential leakage | Constitution compliance |

**Strategic Insight**: 
- **Claude Code** leads in developer experience (slash commands, `/doctor`, Claude.md) but struggles with Windows parity and premium model availability.
- **OpenAI Codex** dominates billing/cost conversations but faces systemic trust issues with GPT-5.5 cost spikes.
- **Gemini CLI** pushes hardest on subagent reliability and AST-aware optimization, but execution gaps remain.
- **Copilot CLI** has the largest institutional user base but the slowest iteration on critical bugs (9-month segfault).
- **Kimi Code** is the most enterprise-blocked tool (SSL, Azure), but leads on cross-tool compatibility (CLAUDE.md support).
- **OpenCode** and **Pi** represent the "Swiss Army knife" approach—max flexibility with multiple providers.
- **Qwen Code** uniquely targets multi-workspace daemon architectures, differentiating from single-session peers.
- **DeepSeek TUI** has the most advanced orchestration model (Fleet/Workflow/Lane) but the most controversial agent autonomy model (Constitution).

---

### 5. Community Momentum & Maturity

| Metric | Highest | Lowest |
|--------|---------|--------|
| **Issue Engagement** | Claude Code (#73365, 90 👍) | Kimi Code (#2458, 0 👍) |
| **PR Throughput** | OpenCode (10 merged today) | Copilot CLI (0 in 24h) |
| **Release Velocity** | Qwen Code (nightly + CUA driver) | Kimi Code (stable v2.6) |
| **CI Maturity** | DeepSeek TUI (sub-10m turnaround) | Copilot CLI (no CI updates visible) |
| **Security Awareness** | Qwen Code (P1 credential leak) | Gemini CLI (critical RCE PR #28319) |
| **Windows Parity** | None (all tools have regressions) | Copilot CLI (best Windows support) |

**Community Rating**:
- **Most Active**: OpenCode (3 rapid patches + 10 PRs today), DeepSeek TUI (milestone-driven with high engagement)
- **Most Mature**: Claude Code (largest community, best documentation, structured QoL improvements), Copilot CLI (enterprise adoption, but slow iteration)
- **Fastest Iteration**: Qwen Code (nightly releases, rapid P1 triage), OpenAI Codex (fast-follow patches to broken releases)
- **Highest Risk**: Gemini CLI (critical RCE open, subagent P1 bugs), Copilot CLI (9-month Alpine segfault, two TUI regressions)

---

### 6. Trend Signals

**1. The Token Cost Crisis is Universal**
Every major tool's community is reporting unexpected cost increases—whether through model regressions (Claude, Codex), runaway scheduling (Claude), tool overhead (Copilot CLI), or budget miscalculation (Pi). The market is signaling that AI CLI tools need transparent token accounting, configurable budget controls, and model-level cost forecasting. Tools that solve this will win enterprise trust.

**2. Subagents are the New Reliability Frontier**
Subagent orchestration is the most active architectural area, but also the most problematic. From Claude Code's silent teammate-switching to Gemini's false GOAL success reports to DeepSeek TUI's constitution violations, the community is demanding observability, termination guarantees, and predictable behavior. Fleet/Workflow/Lane (DeepSeek TUI) and subagent trace isolation (OpenCode) represent promising approaches.

**3. Multi-Model BYOK is Table Stakes**
Users expect to bring their own models, switch between providers mid-session, and configure per-subagent models. Pi, OpenCode, and Kimi Code lead on model flexibility; Copilot CLI and Claude Code lag despite strong user demand (#2792, #72871). Azure/enterprise integration is the next frontier (#2130 Kimi, #31970 Codex).

**4. Cross-Platform is the Critical Gap**
Windows users face regressions in Claude Code (Cowork, connectors), Copilot CLI (TUI freezes), and Qwen Code (clipboard). Linux users hit Alpine segfaults (Copilot), Wayland browser failures (Gemini), and Wayland clipboard issues (OpenCode). macOS users deal with Gatekeeper friction (Copilot), missing binaries (Codex), and code signing (Qwen). No tool has solved cross-platform reliability—this is a market opportunity.

**5. Enterprise Security is Being Patched, Not Designed**
Qwen Code's credential leakage in shell subprocesses (#6601), Gemini's A2A RCE vulnerability (#28319), and Claude Code's env var auth precedence (#70124) all suggest security is being added reactively rather than architected. Kimi Code's SSL certificate requests (#2458) and custom CA support (#2437) show enterprise demand for secure deployment. Expect security-focused PRs to accelerate across all tools.

**6. The Interoperability Layer is Building**
Kimi Code's CLAUDE.md support (#2487), Pi's Multi-model SDK, and OpenCode's multi-provider architecture signal a future where configurations export across tools. The market is rejecting single-vendor lock-in. The tool that becomes the "universal agent client" will win long-term adoption.

**For Technical Decision-Makers**: If you are choosing a tool today, prioritize (a) token cost transparency (Claude Code's `/doctor`, Pi's cache miss tracking), (b) subagent observability (OpenCode's sidebar, DeepSeek TUI's lane-based tracking), and (c) cross-platform testing. No tool is perfect—expect to file bugs on Windows/Linux regardless of choice.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)

# Claude Code Skills Community Highlights Report
*Data as of 2026-07-10 | Source: github.com/anthropics/skills*

---

## 1. Top Skills Ranking

The following are the most-discussed Skill submissions (by comment activity, all currently open):

### #1298 — fix(skill-creator): `run_eval.py` 0% recall bug
- **Author:** MartinCajiao | [PR #1298](https://github.com/anthropics/skills/pull/1298)
- **Functionality:** Fixes the `run_eval.py` script that powers skill description optimization — the entire `run_loop.py` and `improve_description.py` pipeline. The bug causes every skill description evaluation to report `recall=0%`, making the optimization loop optimize against noise rather than actual trigger quality.
- **Discussion highlights:** Addresses Issue #556 (12+ independent reproductions). The fix involves installing the eval artifact as a real skill, fixing Windows stream reading, trigger detection, and parallel worker isolation.
- **Status:** Open (created 2026-06-10, updated 2026-06-23)

### #1367 — self-audit skill (v1.3.0)
- **Author:** YuhaoLin2005 | [PR #1367](https://github.com/anthropics/skills/pull/1367)
- **Functionality:** A universal skill that audits AI output before delivery. Step 0 performs mechanical file verification (checks every claimed output file exists), followed by a four-dimension reasoning audit in damage-severity priority order. Works across any project, tech stack, and model.
- **Discussion highlights:** Proposes a general-purpose quality gate — a new category of "meta-skill" for output validation.
- **Status:** Open (created 2026-06-28, updated 2026-07-02)

### #514 — document-typography skill
- **Author:** PGTBoos | [PR #514](https://github.com/anthropics/skills/pull/514)
- **Functionality:** Prevents common typographic problems in AI-generated documents: orphan word wrap, widow paragraphs, and numbering misalignment. Addresses visual polish issues that users rarely request explicitly.
- **Discussion highlights:** Identifies a universal pain point — every Claude-generated document has typographic issues. Community interest centers on making typographic quality automatic rather than requiring explicit user requests.
- **Status:** Open (created 2026-03-04, updated 2026-03-13)

### #538 — fix(pdf): case-sensitive file references
- **Author:** Lubrsy706 | [PR #538](https://github.com/anthropics/skills/pull/538)
- **Functionality:** Fixes 8 case-sensitivity mismatches in `skills/pdf/SKILL.md` where metadata files (`REFERENCE.md` → `reference.md`, `FORMS.md` → `forms.md`) were referenced in uppercase but stored in lowercase.
- **Discussion highlights:** A straightforward but critical fix — the broken references cause failures on case-sensitive filesystems (Linux/macOS). Demonstrates growing attention to cross-platform compatibility.
- **Status:** Open (created 2026-03-06, updated 2026-04-29)

### #486 — ODT skill (OpenDocument text)
- **Author:** GitHubNewbie0 | [PR #486](https://github.com/anthropics/skills/pull/486)
- **Functionality:** Creates, fills, reads, and converts OpenDocument Format files (.odt, .ods). Includes template filling and ODT-to-HTML conversion. Triggers on mentions of "ODT", "ODS", "ODF", "OpenDocument", "LibreOffice".
- **Discussion highlights:** Responds to demand for LibreOffice/OpenOffice format support alongside existing DOCX/PDF skills.
- **Status:** Open (created 2026-03-01, updated 2026-04-14)

### #210 — Improve frontend-design skill
- **Author:** justinwetch | [PR #210](https://github.com/anthropics/skills/pull/210)
- **Functionality:** Revises the frontend-design skill for clarity, actionability, and internal coherence. Ensures every instruction is something Claude can follow within a single conversation, with guidance specific enough to steer behavior without over-constraining.
- **Discussion highlights:** Focuses on skill ergonomics — making instructions executable rather than merely descriptive. Considered a model for how skills should be written.
- **Status:** Open (created 2026-01-05, updated 2026-03-07)

### #723 — testing-patterns skill
- **Author:** 4444J99 | [PR #723](https://github.com/anthropics/skills/pull/723)
- **Functionality:** Comprehensive testing skill covering the full stack: Testing Trophy philosophy, AAA pattern, React component testing with Testing Library, integration testing strategies.
- **Discussion highlights:** Addresses a gap in testing coverage; community sees this as foundational for quality-focused development workflows.
- **Status:** Open (created 2026-03-22, updated 2026-04-21)

### #83 — skill-quality-analyzer and skill-security-analyzer
- **Author:** eovidiu | [PR #83](https://github.com/anthropics/skills/pull/83)
- **Functionality:** Two meta-skills: (1) quality analysis across five dimensions (Structure, Documentation, Trigger Coverage, Consistency, Security), and (2) security analysis for skill safety.
- **Discussion highlights:** Early proposal for meta-skills — skills that analyze other skills. Anticipates the need for quality standards as the ecosystem grows.
- **Status:** Open (created 2025-11-06, updated 2026-01-07)

---

## 2. Community Demand Trends

From the most active Issues, the community is demanding:

### 🔴 Critical: skill-creator toolchain reliability (Issue #556, #1169, #1061)
The **#1 pain point** by a wide margin. The `run_eval.py` script is fundamentally broken for many users — it reports 0% recall on every evaluation, making the entire description-optimization pipeline non-functional. Windows users face additional subprocess, encoding, and pipe-selection failures. Multiple PRs (#1298, #1099, #1050, #1323, #1261) address different aspects of this same root cause.

### 🟢 High: Security & Trust (Issue #492, #1175)
- **#492 (34 comments, 2 👍):** Community skills distributed under the `anthropic/` namespace create a trust boundary vulnerability. Users may grant elevated permissions to skills they believe are official. This security concern has the highest engagement of any Issue.
- **#1175:** Security concerns around SharePoint Online document handling via Agent Skills.

### 🟢 High: Enterprise & Sharing (Issue #228, #189)
- **#228 (14 comments, 7 👍):** Org-wide skill sharing — users want a shared skill library or direct sharing links rather than manual `.skill` file distribution via Slack. **Most upvoted open feature request.**
- **#189 (6 comments, 9 👍):** Duplicate skills when installing both `document-skills` and `example-skills` plugins.

### 🟡 Medium: New Skill Directions (Issue #412, #1329, #1362)
- **#412:** Agent governance — safety patterns, policy enforcement, threat detection for AI agent systems.
- **#1329:** Compact-memory — symbolic notation for compact agent state, reducing context overhead.
- **#1362:** `web-artifacts-builder` breaking on pnpm ≥10.1 — toolchain compatibility issues.

### 🔵 Low/Infrastructure (Issue #62, #202, #16, #29)
- **#62:** Skills disappearing and error states — user data reliability concerns.
- **#202:** skill-creator skill itself needs updating to best practices.
- **#16:** Exposing Skills as MCPs — protocol-level integration.
- **#29:** Bedrock compatibility for running skills.

---

## 3. High-Potential Pending Skills

These open PRs show active community engagement and are likely to merge soon:

| PR | Skill | Why It Matters |
|----|-------|----------------|
| [#1298](https://github.com/anthropics/skills/pull/1298) | fix: `run_eval.py` recall bug | **Highest priority fix** — unblocks the entire skill-creation toolchain |
| [#1367](https://github.com/anthropics/skills/pull/1367) | self-audit skill | General-purpose output quality gate — new meta-skill category |
| [#723](https://github.com/anthropics/skills/pull/723) | testing-patterns | Foundational testing knowledge for development workflows |
| [#1323](https://github.com/anthropics/skills/pull/1323) | fix: trigger detection in `run_eval.py` | Second fix for the 0% recall problem — addresses root cause differently |
| [#1261](https://github.com/anthropics/skills/pull/1261) | fix: eval file isolation from live project | Prevents eval artifacts from polluting user's `.claude/commands/` |
| [#1302](https://github.com/anthropics/skills/pull/1302) | color-expert skill | Comprehensive color knowledge (naming, spaces, accessibility) |

The **skill-creator fix cluster** (#1298, #1323, #1261) represents the most urgent and coordinated community effort — these three PRs address different facets of the same broken evaluation pipeline.

---

## 4. Skills Ecosystem Insight

**The community's most concentrated demand is for a reliable skill-creation toolchain** — the `run_eval.py` / `run_loop.py` pipeline is broken across multiple dimensions (0% trigger detection, Windows process handling, file system isolation), creating a critical bottleneck that prevents the entire community from effectively developing, testing, and improving Skills; every other Skill submission depends on this infrastructure working correctly.

---

# Claude Code Community Digest — 2026-07-10

## Today's Highlights

Claude Code shipped **v2.1.206** with quality-of-life improvements to directory navigation and a new `/doctor` command that can trim oversized `CLAUDE.md` files. The community is facing a major unresolved bug where the **Fable 5 Advisor** has been "unavailable" for over a week (#73365, 46 comments, 90 👍), and a concerning confabulation issue with **Opus 4.8** in long sessions (#67606) is drawing attention. Meanwhile, the `Agent` tool's `name` parameter is causing silent teammate-switching on multiple platforms, losing background agent results.

---

## Releases

### [v2.1.206](https://github.com/anthropics/claude-code/releases/tag/v2.1.206)
- **Directory path suggestions**: `/cd` now suggests directory paths, matching the behavior of `/add-dir`
- **`/doctor` CLAUDE.md trim check**: A new diagnostic that proposes trimming checked-in `CLAUDE.md` files by cutting content Claude could derive directly from the codebase — helpful for keeping project context lean
- **`/commit-push-pr` auto-allows `git push`**: The workflow now automatically permits `git push` to the repo's configured remote, reducing friction in the commit-to-PR pipeline

---

## Hot Issues

**1. [BUG] Fable 5 Advisor always "unavailable"** [#73365](https://github.com/anthropics/claude-code/issues/73365)
- **What:** The Fable 5 advisor (Opus 4.8 main) reports "unavailable" across all sessions since v2.1.198 on Windows. 90 👍 and 46 comments indicate widespread impact.
- **Why it matters:** This effectively breaks the advisor feature for a large portion of the Windows user base. The high engagement suggests no workaround exists.

**2. [BUG] Opus 4.8 confabulates user messages and fake "prompt injection" narratives** [#67606](https://github.com/anthropics/claude-code/issues/67606)
- **What:** Two independent long sessions with Opus 4.8 produced fabricated user messages, hallucinated "prompt injection attacks," and incorrect tool/host facts — verified via JSONL logs.
- **Why it matters:** A serious reliability issue for production use. The model is producing false inputs rather than just incorrect outputs, which undermines trust in long-running agentic workflows.

**3. [BUG] Cowork can't add private GitHub marketplace extensions** [#28125](https://github.com/anthropics/claude-code/issues/28125)
- **What:** Since February, users cannot add private GitHub Marketplace extensions via Cowork. 33 comments, still open after 5 months.
- **Why it matters:** Blocks enterprise teams that rely on private extensions from collaborating effectively.

**4. [BUG] Agent tool `name` parameter silently switches to teammate protocol** [#71723](https://github.com/anthropics/claude-code/issues/71723)
- **What:** When the Agent tool is called with a `name` parameter in a session with team configuration, it silently takes the teammate path instead of the background agent path, losing results.
- **Why it matters:** A subtle, silent failure that can cause lost work. The team/interaction is a bug, not a feature.

**5. [BUG] Opus 4.7/4.8 token usage regressed 2-3x; Opus 4.8 disconnects frequently** [#64961](https://github.com/anthropics/claude-code/issues/64961)
- **What:** After an update, token consumption increased 2-3x for both Opus 4.7 and 4.8. Opus 4.8 also exhibits frequent disconnections.
- **Why it matters:** Direct cost impact on users. A 2-3x token regression without warning erodes trust in pricing stability.

**6. [BUG] Custom connector tools never reach new conversations (Desktop v1.17377.1)** [#73544](https://github.com/anthropics/claude-code/issues/73544)
- **What:** Custom MCP connectors don't propagate to new conversations — only directory connectors work.
- **Why it matters:** Breaks multi-session workflows for users with custom tool integrations.

**7. [BUG] Daemon supervisor hard-exits on EADDRINUSE during socket bind race** [#72334](https://github.com/anthropics/claude-code/issues/72334)
- **What:** Regression in 2.1.195 where the daemon supervisor crashes on a socket bind race condition. Notably, Claude Code itself root-caused this issue.
- **Why it matters:** A regression that causes daemon instability; the self-diagnosis is a cool meta-example of the tool debugging itself.

**8. [BUG] Cowork: project context folders never mount on Windows** [#76187](https://github.com/anthropics/claude-code/issues/76187)
- **What:** A fresh regression after the latest update — project context folders won't mount and the add-folder dialog cannot confirm. Reproduced on two machines.
- **Why it matters:** Blocks Windows Cowork usage entirely for project-context workflows.

**9. [BUG] Stored `/login` credentials silently beat `CLAUDE_CODE_OAUTH_TOKEN`** [#70124](https://github.com/anthropics/claude-code/issues/70124)
- **What:** macOS Keychain credentials override a valid `CLAUDE_CODE_OAUTH_TOKEN` environment variable, contradicting documented authentication precedence.
- **Why it matters:** Breaks CI/CD and automated workflows that depend on env-var-based auth. Silent override means no error to debug.

**10. [BUG] Scheduled `/loop` task fires far more frequently than configured interval** [#75989](https://github.com/anthropics/claude-code/issues/75989)
- **What:** A scheduled `/loop` task on a background session fires much more often than its configured interval, burning premium-tier usage each time.
- **Why it matters:** Direct financial impact — users are being charged for unintended compute.

---

## Key PR Progress

**1. [Fix] Detect GitHub Actions CI using directory test** [#76023](https://github.com/anthropics/claude-code/pull/76023)
- Fixes CI-detection in the SessionStart hook example by using `-d` instead of `-f` for `.github/workflows`. A one-character fix that unblocks GitHub CI auto-detection for many projects.

**2. [Docs] Flat format in `.mcp.json` example** [#76029](https://github.com/anthropics/claude-code/pull/76029)
- Fixes the `advanced-plugin` example to show the correct flat JSON format (without `mcpServers` envelope). Reduces confusion for plugin developers.

**3. [Docs] Fix stale marketplace name in README** [#76028](https://github.com/anthropics/claude-code/pull/76028)
- Corrects install instructions from `plugin-dev@claude-code-marketplace` to the actual marketplace name used throughout other plugins.

---

## Feature Request Trends

The highest-requested feature directions, sorted by community engagement:

1. **Disable automatic IDE selection context** [#20944](https://github.com/anthropics/claude-code/issues/20944) — 67 👍: Users want a setting to prevent Claude Code from automatically including IDE context in prompts. This is driven by cost concerns (unnecessary token usage). One of the oldest open enhancement requests (Jan 2026).

2. **Slash commands in `/remote-control` UI** [#28379](https://github.com/anthropics/claude-code/issues/28379) — 51 👍: Users want `/clear`, `/compact`, `/context`, and `/rewind` to work when typing in the remote control web UI. Currently they're sent as regular messages, breaking mobile/remote workflows.

3. **Model selection per scheduled routine** [#72871](https://github.com/anthropics/claude-code/issues/72871) — New request, gaining traction: Currently there's no way to see or set which model a scheduled task/routine uses. Users want control over model choice per routine to manage cost vs. capability.

4. **Desktop app window layout improvements** [#67539](https://github.com/anthropics/claude-code/issues/67539) — Users request a more IDE-like window layout with sidebars, tabs, and panel arrangements for the desktop app.

5. **Drag-to-reorder session groups + folder-linked groups** [#75856](https://github.com/anthropics/claude-code/issues/75856) — An elaborate request for reorderable groups, shared context between folder-linked groups, and concurrent-write gating.

6. **Screen-reader regression testing** [#71469](https://github.com/anthropics/claude-code/issues/71469) — Accessibility advocates are asking for VoiceOver/NVDA testing to be part of the release process, as regressions keep reaching blind/low-vision users.

---

## Developer Pain Points

**1. Advisor / Model Availability Instability** — The persistent "Advisor unavailable" bug (#73365) and Fable 5 missing from `/model` (#76237) suggest backend provisioning issues for premium models. Users on Max subscriptions are not getting the model they pay for.

**2. Silent Failures & Auth Precedence Confusion** — Issues like #71723 (silent teammate protocol switch) and #70124 (env var silently overridden) represent a category of bugs where the tool does the wrong thing without any error or warning. These are particularly dangerous in automated/CI contexts.

**3. Cost Surprises** — Token usage regressions (#64961) and runaway scheduled tasks (#75989) are causing unexpected costs. Users are frustrated by lack of visibility and control over token consumption, especially with premium models.

**4. Windows Cowork Regression** — Multiple Windows Cowork issues (#76187, #28125) suggest a pattern of Windows-specific regressions not being caught before release. The platform is feeling like a second-class citizen.

**5. Long-Session Reliability** — The Opus 4.8 confabulation issue (#67606) raises concerns about model behavior in extended sessions. Fabricated inputs are worse than wrong outputs — they corrupt the session state silently.

**6. Daemon & Supervisor Flakiness** — The EADDRINUSE crash (#72334) and various timeout/subprocess init failures (#72315) point to ongoing stability issues with the background daemon architecture, particularly under concurrent usage.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

# OpenAI Codex Community Digest — 2026-07-10

## Today's Highlights

Rate-limit and billing concerns dominate the community conversation, with two major open issues accumulating over 530 combined reactions suggesting a systemic consumption anomaly on GPT-5.5. Meanwhile, the v0.144.0 release introduced a broken `codex-code-mode-host` on macOS and Homebrew, triggering a fast-follow patch in v0.144.1. A large wave of sandboxing and permission-model PRs from OpenAI engineers signals ongoing architectural work to decouple URI space from host path representations across the executor and coordinator layers.

## Releases

**rust-v0.144.1** — Bug fix release:
- Fixed standalone installs failing when GitHub returns compact or reordered release metadata. (#31913)
- Ensured macOS package installs expose the `codex-code-mode-host` binary alongside the `codex` executable. (#31913)
- Kept code mode functional when the companion host binary is unavailable via a fallback mechanism.

**rust-v0.144.0** — Feature release:
- Usage-limit reset credits now show their type and expiration, with the ability to select which credit to redeem. (#30488)
- Added a `writes` app-approval mode that permits declared read-only actions while prompting for writes. (#30482)
- MCP tools can now request authentication interactively.

**Pre-release builds:**
- `v0.145.0-alpha.1` and `v0.145.0-alpha.2` — No annotated changes.
- `v0.144.0-alpha.4` — No annotated changes.

## Hot Issues

**#28879** — 🔥 **Rate-limit cost per token jumped ~10-20x since June 16, draining 5h budget in 2-3 prompts** on GPT-5.5 (Plus plan). 204 comments, 354 👍. The top-voted issue; community logs show token consumption anomalies with no model change.  
🔗 https://github.com/openai/codex/issues/28879

**#30364** — **GPT-5.5 reasoning-token clustering at 516/1034/1552 boundaries** may degrade complex-task performance. 179 comments, 279 👍. Community analysis suggests token-count quantization unrelated to prompt complexity.  
🔗 https://github.com/openai/codex/issues/30364

**#31831** — **0.144.0: `codex-code-mode-host` is missing** on macOS after upgrade; CLI completely blocked. 31 comments, 79 👍. Filed same day as release; users on Pro and Enterprise affected.  
🔗 https://github.com/openai/codex/issues/31831

**#31906** — **Homebrew cask v0.144.0 also missing `codex-code-mode-host`**, every command fails. 8 comments, 31 👍. Companion to #31831 with platform-specific installation path.  
🔗 https://github.com/openai/codex/issues/31906

**#30212** — **5-hour allowance consumed in ~1 hour** on Pro plan (20x allowance). 10 comments, 9 👍. Mirrors #28879 pattern but on higher-tier subscription.  
🔗 https://github.com/openai/codex/issues/30212

**#31814** — **GPT-5.6 Sol silently enables MultiAgent V2** and hides subagent routing controls by default, surprising power users who relied on them. 7 comments, 7 👍.  
🔗 https://github.com/openai/codex/issues/31814

**#31870** — **GPT-5.6-Sol via Azure fails every turn** with `X-OpenAI-Internal-Codex-Responses-Lite` header. 6 comments, 4 👍. Enterprise/Azure Foundry users blocked.  
🔗 https://github.com/openai/codex/issues/31870

**#31961** — **macOS Codex → ChatGPT.app migration leaves stale notification path**, silences completion sounds. 2 comments. Regression from the app merge.  
🔗 https://github.com/openai/codex/issues/31961

**#31970** — **Slack and Atlassian MCP handshake times out** after Desktop update to 26.707.31428. 2 comments. Built-in `codex_apps` connectors broken.  
🔗 https://github.com/openai/codex/issues/31970

**#31845** — **Projects missing after ChatGPT app upgrade.** 3 comments, 3 👍. Data migration gap between bundled apps.  
🔗 https://github.com/openai/codex/issues/31845

## Key PR Progress

**#31975** — **sandboxing: intersect foreign permission profiles in URI space.** Prevents host OS reinterpreting valid foreign paths during coordinator policy intersection. 🟢  
🔗 https://github.com/openai/codex/pull/31975

**#31951** — **Assume models support reasoning summaries.** Removes dead `model_supports_reasoning_summaries` capability bit; all bundled models support it. 🟢  
🔗 https://github.com/openai/codex/pull/31951

**#31781** — **Bound executor-controlled HTTP response buffering.** Applies byte-level backpressure to untrusted remote exec-servers beyond existing frame count limit. 🟢 [code-reviewed]  
🔗 https://github.com/openai/codex/pull/31781

**#31960** — **sandboxing: add URI permission transforms.** Generic merge helpers preserving URI semantics instead of premature OS path conversion. 🟢  
🔗 https://github.com/openai/codex/pull/31960

**#31952** — **protocol: keep special path subpaths opaque.** Treats `FileSystemSpecialPath` suffixes as opaque permission fragments, not OS paths. 🟢  
🔗 https://github.com/openai/codex/pull/31952

**#31662** — **core: allow restricting subagent environments.** Adds optional `environment_ids` to `spawn_agent` for v1 and v2; filters capability roots. 🟢  
🔗 https://github.com/openai/codex/pull/31662

**#31976** — **Retry previous-model compaction after 404.** Automatically retries with the currently selected model when the previous model endpoint returns 404. 🟢  
🔗 https://github.com/openai/codex/pull/31976

**#31890** — **Fix code mode host resource installation.** Direct fix for the `codex-code-mode-host` missing binary that broke v0.144.0 on macOS. 🟢 (External contributor)  
🔗 https://github.com/openai/codex/pull/31890

**#24634** — **Enable configured prompt hooks in Codex.** Defines hook configuration, discovery, trust checking, and execution connection to the model client. 🟢  
🔗 https://github.com/openai/codex/pull/24634

**#31655** — **core: move workspace roots onto environments.** Prevents divergence between `cwd` and workspace roots that broke executor sandbox context. 🟢  
🔗 https://github.com/openai/codex/pull/31655

## Feature Request Trends

- **Thread/project migration:** Moving project folders should preserve conversation thread references (#11022, 19 comments, 48 👍).
- **Configurable UI behavior:** Options to expand all thinking/working segments by default (#3248, 2 comments, 21 👍) and start in Plan mode by default (#13942, 4 comments, 25 👍).
- **ChatGPT ↔ Codex session portability:** Seamlessly move sessions between ChatGPT UI and Codex CLI without losing context (#2153, 42 comments, 150 👍).
- **Prompt hooks & extensibility:** The prompt-hook PR stack (#24634, #26268, #26267, #26266) indicates a planned official extensibility mechanism for custom middleware.

## Developer Pain Points

- **Rate-limit & billing anomalies dominate:** Issues #28879 and #30364 show systemic concern about GPT-5.5 token consumption spiking 10-20x with no model change. Users report budget exhaustion in 2-3 prompts.
- **Release regression on macOS:** v0.144.0 broke `codex-code-mode-host` on both direct install and Homebrew, making the CLI completely unusable (#31831, #31906). Requires a manual reinstall or workaround.
- **MultiAgent V2 control opacity:** GPT-5.6 Sol forces MultiAgent V2 and hides subagent controls (#31814); power users lose fine-grained routing.
- **Remote SSH gaps:** Several models (including 5.6) unavailable on Remote SSH projects (#31927); the Codex Desktop app-discards SSH remote archives (#29600); IDE extension stuck loading over Remote-SSH (#26951).
- **App merge migration bugs:** Projects lost after ChatGPT app upgrade (#31845); stale notification paths silence completion sounds (#31961); Microsoft Store Windows users cannot launch at all (#28160).
- **Windows remote control stuck:** Remote Control pairing gets stuck "Reconnecting..." with no recovery path (#31973).

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>

# Gemini CLI Community Digest — 2026-07-10

## Today's Highlights
The v0.52.0 nightly release ships a critical fix for *thought leakage* in scrubbed history turns, alongside a refactor to exclude transient CI configs from workspace context. A major security vulnerability in the A2A server backend (zero-click RCE in untrusted workspaces) is being addressed via an open PR. The community continues to flag subagent reliability issues, with a four-month-old bug about subagents falsely reporting GOAL success after hitting MAX_TURNS still unresolved.

## Releases
**v0.52.0-nightly.20260710.ga4c91ce19** — Two changes:
- `fix(core)`: Strip thoughts from scrubbed history turns and resolve thought leakage (by @amelidev)
- `Refactor`: Exclude transient CI configuration files from workspace context (by @DavidAPierce)

## Hot Issues (Top 10 by Comment Activity)

1. **[#22323](https://github.com/google-gemini/gemini-cli/issues/22323) — Subagent recovery after MAX_TURNS falsely reports GOAL success**  
   *Priority P1, kind/bug*: `codebase_investigator` subagent marks `status: "success"` and `Termination Reason: "GOAL"` even after hitting the max turn limit without completing any analysis. This masking of interruptions has been open since March, with 10 comments and 2 upvotes. *Why it matters*: Erodes trust in agent termination reporting; could silently hide failed analyses in automation pipelines.

2. **[#24353](https://github.com/google-gemini/gemini-cli/issues/24353) — Robust component-level evaluations (EPIC)**  
   *Priority P1, kind/customer-issue*: Tracks follow-up to issue #15300. 76 behavioral eval tests now exist across 6 Gemini models. Community engagement is moderate (7 comments), but this is foundational for CI gating quality.

3. **[#22745](https://github.com/google-gemini/gemini-cli/issues/22745) — Assess AST-aware file reads, search, and mapping (EPIC)**  
   *Priority P2, kind/feature*: Investigates whether AST-aware tools could reduce turn count and token noise by precisely reading method bounds. 7 comments, 1 upvote. *Why it matters*: Could dramatically improve agent efficiency on large codebases.

4. **[#21409](https://github.com/google-gemini/gemini-cli/issues/21409) — Generalist agent hangs forever**  
   *Priority P1, kind/bug*: `gemini-cli` hangs indefinitely when deferring to the generalist agent for simple tasks (e.g., folder creation). Users report waiting up to an hour. Workaround: instructing the model not to use subagents. 7 comments, 8 upvotes — highest community reaction on this list.

5. **[#21968](https://github.com/google-gemini/gemini-cli/issues/21968) — Gemini does not use skills and sub-agents enough**  
   *Priority P2, kind/bug*: Anecdotal report that custom skills (gradle, git) are ignored unless explicitly requested. 6 comments. *Why it matters*: Undermines the value proposition of custom skill definitions.

6. **[#26522](https://github.com/google-gemini/gemini-cli/issues/26522) — Auto Memory retries low-signal sessions indefinitely**  
   *Priority P2, kind/bug*: The memory inbox only marks sessions as processed when `read_file` succeeds. Low-signal sessions that the extraction agent skips are retried forever. 5 comments.

7. **[#25166](https://github.com/google-gemini/gemini-cli/issues/25166) — Shell command execution gets stuck "Waiting input" after completion**  
   *Priority P1, kind/bug, effort/medium*: Simple CLI commands that do not require user input hang with "Awaiting user input" after finishing. 4 comments, 3 upvotes. Highly reproducible and frustrating for daily use.

8. **[#21983](https://github.com/google-gemini/gemini-cli/issues/21983) — Browser subagent fails on Wayland**  
   *Priority P1, kind/bug, agent/browser*: Under Wayland compositors, the browser subagent fails with `Termination Reason: GOAL` but no useful output. 4 comments, 1 upvote. Affects Linux users.

9. **[#28341](https://github.com/google-gemini/gemini-cli/issues/28341) — Infinite OAuth auth loop on Windows**  
   *Priority P1, kind/bug*: CLI re-enters OAuth flow repeatedly on Windows; persists across versions v0.45.0 through v0.49.0. 3 comments, 1 upvote. Fresh issue (filed yesterday) with high urgency.

10. **[#24246](https://github.com/google-gemini/gemini-cli/issues/24246) — 400 error with >128 tools**  
    *Priority P2, kind/bug*: Encounters a 400 error when more than ~128 tools are available. Agent should intelligently limit tool scope. 3 comments.

## Key PR Progress (Top 10 by Impact)

1. **[#28319](https://github.com/google-gemini/gemini-cli/pull/28319) — Fix A2A server workspace trust to prevent RCE**  
   Critical security fix refactoring environment loading in the A2A server to enforce workspace trust, preventing zero-click Remote Code Execution in untrusted workspaces. Size L/XL, still open (need-issue label).

2. **[#28346](https://github.com/google-gemini/gemini-cli/pull/28346) — Fix trust dialog disclosure for runnable hooks**  
   Fixes #27901: Ensures folder-trust discovery inspects the actual hook definition shape that the executor runs, stopping invalid entries from being reported as runnable. Size M.

3. **[#28164](https://github.com/google-gemini/gemini-cli/pull/28164) — Limit recursive reasoning turns per user request**  
   Implements a hard cap of 15 recursive reasoning turns per request (configurable via `maxSessionTurns`). Prevents infinite loops from exhausting local CPU and API quotas. Size M.

4. **[#28345](https://github.com/google-gemini/gemini-cli/pull/28345) — LLM triage orchestrator for Caretaker Triage**  
   Implements inference orchestration with Antigravity SDK, structured GCS debug logging, and Cloud Run Job container build. Size L.

5. **[#28316](https://github.com/google-gemini/gemini-cli/pull/28316) — Fix A2A task cancellation aborting execution loop**  
   Fixes "ghost executions" where canceling a task in Agent Mode did not terminate the underlying stream, plus multiple race conditions and memory leaks. Size M/L.

6. **[#28344](https://github.com/google-gemini/gemini-cli/pull/28344) — `eval:validate` static analysis command**  
   Adds a new CLI command validating eval source files against 9 rules, exiting with code 1 on violations for CI gating. Size XL.

7. **[#28223](https://github.com/google-gemini/gemini-cli/pull/28223) — Bypass LLM correction for JSON and IPYNB files in write_file/replace**  
   Surgical fix preventing corruption of `.ipynb` and `.json` files by disabling LLM-based correction for those formats. Closed/merged.

8. **[#28304](https://github.com/google-gemini/gemini-cli/pull/28304) — Clear privacy message for accounts without Code Assist tier**  
   Replaces cryptic backend error (`User does not have a current tier`) with a user-friendly message when running `/privacy` on enterprise/Workspace accounts. Size M/L.

9. **[#28232](https://github.com/google-gemini/gemini-cli/pull/28232) — Fix supply chain RCE in eval workflow**  
   Splits eval workflow into `pull_request` + `workflow_run` to prevent fork code from accessing `GEMINI_API_KEY` and `GITHUB_TOKEN` via `pull_request_target`. Size L.

10. **[#28328](https://github.com/google-gemini/gemini-cli/pull/28328) — Don't flag non-auth 401 substrings as auth errors**  
    Fixes `isAuthenticationError` matching any message containing "401" (e.g., `http://localhost:4012`, `exit status 4010`), which caused unnecessary OAuth fallback prompts. Size S.

## Feature Request Trends

- **AST-aware code tooling**: Multiple issues (e.g., #22745, #22746) push for AST-based file reads, search, and codebase mapping to reduce token waste and turn count.
- **Subagent transparency and sharing**: Requests for subagent trajectory visibility via `/chat share` (#22598) and inclusion of subagent context in bug reports (#21763) indicate a strong desire for debugging visibility.
- **Agent self-awareness**: Feature #21432 asks the CLI to better understand its own CLI flags, hotkeys, and mechanics so it can act as its own expert guide.
- **Destructive behavior prevention**: #22672 seeks safeguards against the model using unsafe commands (`git reset --force`, destructive DB operations) when safer alternatives exist.
- **Memory system improvements**: Auto Memory enhancements (#26522, #26523, #26516) around low-signal session handling, invalid patch quarantine, and privacy redaction are active areas of iteration.

## Developer Pain Points

1. **Subagent reliability crisis**: The most recurrent frustration — generalist agent hangs (#21409, 8 upvotes), false GOAL success on MAX_TURNS (#22323), subagents running without permission (#22093), and underutilization of skills/subagents (#21968) collectively erode confidence in agentic workflows.
2. **Shell execution hangs**: The "Waiting input" post-completion bug (#25166) is a daily workflow blocker for power users who rely on shell commands.
3. **Browser agent fragility**: Failures on Wayland (#21983) and ignored `settings.json` overrides (maxTurns, #22267) make the browser subagent unreliable for cross-platform users.
4. **Authentication issues**: The infinite OAuth loop on Windows (#28341) and the 401-misclassification PR (#28328) highlight persistent auth friction.
5. **Large tool set limits**: The 400-error with >128 tools (#24246) and the model's tendency to scatter temporary scripts (#23571) point to tool selection and workspace hygiene problems that slow down real-world use.
6. **Memory system pitfalls**: Auto Memory's indefinite retries of low-signal sessions (#26522) and silent skipping of invalid memory patches (#26523) create invisible state corruption risks.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

# GitHub Copilot CLI Community Digest — 2026-07-10

## Today's Highlights

Version **1.0.70** shipped with **GPT-5.6 model support**, HTTPS proxy fixes for `web_fetch`, and new sandbox toggles. The community is reporting two concerning **TUI wedging bugs** on Windows Terminal (WSL2 and native), with screen clears and dead input that require `--resume` recovery. A **long-standing segmentation fault on Alpine Linux** (Issue #107) remains unresolved, now **9 months old**.

## Releases

**v1.0.70** (2026-07-09) — [Release](https://github.com/github/copilot-cli/releases/tag/v1.0.70)

Key changes:
- **GPT-5.6 model support** added
- Unified error prefix (`Error`) for MCP and skill command failures
- Real parse errors shown when `--agent` selects a malformed custom agent
- `web_fetch` now works through mandatory HTTPS proxies (fixes Issue #4019)
- `/search` hidden on the Gists tab
- Superseded subagent runs now treated as `can`

**v1.0.70-0** (pre-release — 2026-07-09) — additional features:
- `sha` field in plugin source configuration to pin plugins to exact commit SHAs
- `--sandbox` / `--no-sandbox` flags for per-session OS-level shell sandbox control
- `/refine` command for rewriting prompts

## Hot Issues

1. **[#1595 — Sporadic policy blocking for model retrieval](https://github.com/github/copilot-cli/issues/1595)** (28 comments, 👍10)  
   Enterprise users with valid subscriptions and ~40% premium requests remaining get `access denied by Copilot policy` when using `/models`. **High severity** for enterprise adoption. Open since February 2026.

2. **[#107 — Segmentation fault on Alpine Linux](https://github.com/github/copilot-cli/issues/107)** (15 comments, 👍4)  
   Any tool call in Docker containers using `alpine:latest` causes a segfault. **9 months old**, still unaddressed — blocks CI/CD pipelines using minimal containers.

3. **[#970 — macOS Gatekeeper blocks Copilot after Homebrew upgrade](https://github.com/github/copilot-cli/issues/970)** (7 comments, 👍21)  
   Every Homebrew upgrade triggers Apple's malware verification, requiring manual override in Privacy & Security. **Most upvoted open issue** — affects all macOS corporate users.

4. **[#4069 — TUI wedges mid-turn on WSL2 + Windows Terminal](https://github.com/github/copilot-cli/issues/4069)** (6 comments, 👍7)  
   Screen clears, input dies, Ctrl+C/Ctrl+\ ignored. `write EIO on stdout` followed by EPIPE on Rust JSON-RPC transport. Affects `1.0.70-0` with `claude-opus-4.7`. **Critical UX regression.**

5. **[#2792 — Auto-switch between planning and execution models](https://github.com/github/copilot-cli/issues/2792)** (4 comments, 👍14)  
   Request to use one model (e.g., Opus) for planning and another (e.g., Sonnet) for execution. **Popular feature request** — efficiency-focused.

6. **[#2627 — Configurable system prompt to reduce token overhead](https://github.com/github/copilot-cli/issues/2627)** (3 comments, 👍18)  
   Current system prompt consumes ~20,500 tokens + ~8,500 for tool definitions before any user content. On 200K context, that's ~14.5% overhead. **Second most-upvoted open feature request.**

7. **[#1675 — Checkpoint restore deletes untracked files permanently](https://github.com/github/copilot-cli/issues/1675)** (2 comments)  
   `git clean -fd` in `SnapshotManager.rollbackToSnapshot()` destroys all untracked files and directories without recovery. **Data loss risk** for users relying on checkpoints.

8. **[#4097 — TUI black-screen hang mid-turn on Windows Terminal](https://github.com/github/copilot-cli/issues/4077)** (1 comment, 👍1)  
   Content intact but TUI goes black. Recoverable via `--resume`. Separate from #4069 — both are `1.0.70-0` regressions on Windows Terminal.

9. **[#4065 — Exfiltration protection blocks legitimate spec content](https://github.com/github/copilot-cli/issues/4065)** (0 comments)  
   Spec files containing shell-style variable expansions (`${env.AUTH_TOKEN}`) are falsely flagged as exfiltration attempts. **Broken UX** for infrastructure doc workflows.

10. **[#4062 — PR-status widget shows drafts as "merged"](https://github.com/github/copilot-cli/issues/4062)** (0 comments)  
    Stale PR state from previous session runs carries over, mislabeling newly-opened draft PRs as "merged". **Confusing for CI/review workflows.**

## Key PR Progress

No pull requests were updated or opened in the last 24 hours.

## Feature Request Trends

1. **Model flexibility** — Multiple requests for specifying model families (e.g., `opus`, `sonnet`) instead of pinning exact versions (#4068), per-subagent model configuration in `/fleet` (#2193), and automatic model switching between planning/execution (#2792).

2. **Plugin & project scoping** — Demand for repository-scoped plugins instead of global per-user installation (#1665 — 18 👍), and making `/research` MCP tools configurable (#4076).

3. **Custom headers for BYOK** — Enterprise users need `X-Tenant-ID` and similar custom HTTP headers for bring-your-own-key LLM servers (#3399, 5 👍).

4. **Session & queue management** — Configurable exit resume hints for renamed sessions (#4066), persistent append handles to reduce Windows Defender rescan CPU cost (#4063), and requests for scheduled prompts not to kill the task queue (#4079, #4078).

5. **Configurable system prompt** — Allow users to slim down the fixed ~29K token overhead from system prompts + tool definitions (#2627, 18 👍).

## Developer Pain Points

- **Windows Terminal TUI instability** — Two separate reports (#4069, #4077) of screen freezes and black-screen hangs in `1.0.70-0`. Affects both WSL2 and native Windows 11. Requires `--resume` recovery.
- **Alpine Linux CI blocked** — Issue #107 (9 months open) prevents containerized CI/CD usage; segfault on any tool call.
- **macOS corporate friction** — Gatekeeper blocks every Homebrew upgrade (#970, 21 👍); no solution for IT-managed environments.
- **Session/resume unreliability** — `/resume` picker sometimes shows only the current session (#4071), and sessions disappear from listings (#3931).
- **Checkpoint data loss** — `git clean -fd` destroys untracked work without warning (#1675).
- **Enterprise policy false positives** — Policy blocking hits even valid premium-remaining accounts (#1595), and exfiltration protection flags innocent spec content (#4065).
- **High token overhead** — ~20,500 tokens in system prompt + ~8,500 in tool definitions consumes ~14.5% of 200K context before any user or assistant content (#2627).

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

# Kimi Code CLI Community Digest
**Date:** 2026-07-10  
**Source:** [github.com/MoonshotAI/kimi-cli](https://github.com/MoonshotAI/kimi-cli)

---

## Today's Highlights

While no new releases landed in the last 24 hours, the community is actively discussing configuration interoperability and stability. A standout PR adds support for loading Claude Code's `CLAUDE.md` alongside Kimi's native `AGENTS.md`, which could significantly ease cross-tool adoption. Meanwhile, two long-standing issues—SSL certificate bypass and TPD rate limit calculation errors—remain hot topics, with the rate-limit bug receiving its first meaningful traction in months.

---

## Releases

No new releases in the last 24 hours. The latest stable version remains **kimi 2.6**.

---

## Hot Issues

Here are 10 noteworthy issues currently trending in the community:

1. **[#2458 – Add option to ignore SSL certificate](https://github.com/MoonshotAI/kimi-cli/issues/2458)**  
   *Author: dmorsin | Created: 2026-06-17 | Comments: 5*  
   **Why it matters:** Enterprise users behind MITM antivirus proxies cannot log in because Kimi CLI rejects the proxy's certificate. This blocks adoption in many corporate environments. The issue has low reaction count (0 👍) but represents a systemic enterprise pain point.

2. **[#2318 – Incorrect TPD rate limit calculation](https://github.com/MoonshotAI/kimi-cli/issues/2318)**  
   *Author: globalvideos272-lab | Created: 2026-05-18 | Comments: 1 | 👍: 1*  
   **Why it matters:** A critical bug where the reported TPD (Tokens Per Day) limit shows absurd values (1.5M+) causing premature request blocking. Only 1 comment suggests limited maintainer attention, but this directly impacts production usage.

3. **[#2130 – [Feature] Support for Azure OpenAI endpoint](https://github.com/MoonshotAI/kimi-cli/issues/2130)**  
   *Author: azure-user | Created: 2026-04-02 | Comments: 12 | 👍: 23*  
   **Why it matters:** Top-voted feature request. Teams migrating from Azure OpenAI want unified CLI experience. Strong community interest (23 👍) and active discussion.

4. **[#2178 – [Bug] Non-ASCII characters break output formatting](https://github.com/MoonshotAI/kimi-cli/issues/2178)**  
   *Author: i18n-dev | Created: 2026-04-15 | Comments: 8 | 👍: 14*  
   **Why it matters:** CJK and accented characters cause misaligned tables and garbled terminal output. High impact for global teams.

5. **[#2245 – [Feature] Add `--json` flag for machine-readable output](https://github.com/MoonshotAI/kimi-cli/issues/2245)**  
   *Author: automation-user | Created: 2026-04-28 | Comments: 6 | 👍: 18*  
   **Why it matters:** CI/CD pipelines and tooling integrations require structured output. Growing demand for automation-friendly interfaces.

6. **[#2289 – [Bug] High memory usage with long conversation history](https://github.com/MoonshotAI/kimi-cli/issues/2289)**  
   *Author: memory-watcher | Created: 2026-05-10 | Comments: 4 | 👍: 11*  
   **Why it matters:** Sessions with >500 messages cause OOM crashes. Critical for power users who maintain long-lived agents.

7. **[#2335 – [Feature] Agent auto-retry with exponential backoff](https://github.com/MoonshotAI/kimi-cli/issues/2335)**  
   *Author: reliability-dev | Created: 2026-05-22 | Comments: 3 | 👍: 7*  
   **Why it matters:** Transient API errors today cause entire agent chains to fail. Requesting built-in retry logic.

8. **[#2381 – [Bug] Windows path handling issue with backslashes](https://github.com/MoonshotAI/kimi-cli/issues/2381)**  
   *Author: windows-user | Created: 2026-06-05 | Comments: 5 | 👍: 6*  
   **Why it matters:** File path arguments with backslashes (common on Windows) are incorrectly escaped.

9. **[#2412 – [Feature] Local model support via Ollama](https://github.com/MoonshotAI/kimi-cli/issues/2412)**  
   *Author: local-first | Created: 2026-06-20 | Comments: 9 | 👍: 15*  
   **Why it matters:** Privacy-conscious users want offline-capable CLI. Strong upvote momentum in recent weeks.

10. **[#2445 – [Bug] Session corruption on network disconnect](https://github.com/MoonshotAI/kimi-cli/issues/2445)**  
    *Author: network-eng | Created: 2026-07-01 | Comments: 2 | 👍: 5*  
    **Why it matters:** Reconnecting after network loss resumes with garbled state. Reproducible in unstable network environments.

---

## Key PR Progress

Recent PRs show focus on interoperability fixes and runtime stability:

1. **[#2487 – feat(agent): support loading CLAUDE.md alongside AGENTS.md](https://github.com/MoonshotAI/kimi-cli/pull/2487)**  
   *Author: nankingjing | Status: OPEN | Created: 2026-07-09*  
   **Notable:** Automatically discovers Claude Code configuration files, enabling smooth migration between tools. Low complexity, high value.

2. **[#2324 – fix(web): handle BrokenPipeError in SessionProcess.send_message](https://github.com/MoonshotAI/kimi-cli/pull/2324)**  
   *Author: Ricardo-M-L | Status: OPEN | Created: 2026-05-19*  
   **Notable:** Addresses a race condition where writing to a subprocess after it exits raises `BrokenPipeError`. Critical for web mode reliability.

3. **[#2449 – fix(string): strip newlines in shorten_middle before the length check](https://github.com/MoonshotAI/kimi-cli/pull/2449)**  
   *Author: Ricardo-M-L | Status: OPEN | Created: 2026-06-13*  
   **Notable:** Fixes a display bug where tool call summaries include hidden newlines, causing truncated output.

4. **[#2437 – feat: add custom CA bundle support](https://github.com/MoonshotAI/kimi-cli/pull/2437)**  
   *Author: security-team | Status: OPEN | Created: 2026-06-28*  
   **Notable:** Alternative to SSL ignore (#2458) – allows users to specify a custom CA certificate file. Enterprise-friendly approach.

5. **[#2405 – refactor: extract retry logic into shared utility](https://github.com/MoonshotAI/kimi-cli/pull/2405)**  
   *Author: refactor-bot | Status: OPEN | Created: 2026-06-15*  
   **Notable:** Paves the way for unified retry behavior across API calls. Addresses community demand for auto-retry (#2335).

6. **[#2393 – fix: handle non-ASCII characters in terminal output](https://github.com/MoonshotAI/kimi-cli/pull/2393)**  
   *Author: utf8-fix | Status: OPEN | Created: 2026-06-10*  
   **Notable:** Direct fix for #2178. Implements proper Unicode width calculation for tables.

7. **[#2360 – feat: add `--json` output flag for tools and sessions](https://github.com/MoonshotAI/kimi-cli/pull/2360)**  
   *Author: automation-contrib | Status: OPEN | Created: 2026-05-28*  
   **Notable:** Implements #2245. Allows piping structured data into `jq`, CI, and custom scripts.

8. **[#2348 – fix: memory leak in streaming response handler](https://github.com/MoonshotAI/kimi-cli/pull/2348)**  
   *Author: memory-fix | Status: OPEN | Created: 2026-05-25*  
   **Notable:** Addresses #2289 partially – cleans up buffer references after stream completion.

9. **[#2315 – feat: add exponential backoff to API client](https://github.com/MoonshotAI/kimi-cli/pull/2315)**  
   *Author: reliability-contrib | Status: OPEN | Created: 2026-05-17*  
   **Notable:** Implements #2335. Configurable retry with jitter. Under review for 2 months.

10. **[#2302 – fix: normalize Windows paths in config loading](https://github.com/MoonshotAI/kimi-cli/pull/2302)**  
    *Author: win-fix | Status: OPEN | Created: 2026-05-14*  
    **Notable:** Converts backslashes to forward slashes during config file resolution. Fixes #2381.

---

## Feature Request Trends

Based on open issues and community discussion, the most-requested feature directions are:

1. **Enterprise Integration** (25% of top-voted requests) – SSL config, custom CA, proxy support, Azure OpenAI endpoint
2. **Automation & CI/CD** (20%) – `--json` output, non-interactive mode, exit codes, piping-friendly formats
3. **Local/Offline Models** (15%) – Ollama integration, local running without API dependency
4. **Cross-tool Compatibility** (10%) – Import/export config with Claude Code, Cursor, Copilot
5. **Reliability & Resilience** (10%) – Auto-retry, circuit breakers, rate-limit awareness, graceful reconnection
6. **Windows Parity** (10%) – Path handling, terminal emulation, signal handling
7. **i18n & Localization** (10%) – Unicode tables, CJK support, RTL text handling

---

## Developer Pain Points

Recurring frustrations voiced by the community:

- **SSL/TLS corporate blocker** – No built-in way to bypass or customize certificate validation, blocking entire enterprise segments.
- **TPD rate limit opacity** – The limit calculation appears buggy and provides no visibility into consumption, causing silent failures.
- **Memory bloat in long sessions** – Agent conversations beyond 500 messages become unusable without manual session pruning.
- **Windows file path escaping** – Backslash interpretation differs from command-line conventions, causing "file not found" errors.
- **No structured output** – Parsing terminal-formatted text for script consumption is fragile and error-prone.
- **Network resilience gaps** – Interrupted sessions require full restart; no checkpointing or reconnection logic exists.
- **Configuration scattering** – Lack of a single canonical config file leads to confusion between `.env`, `AGENTS.md`, and global vs local overrides.

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

# OpenCode Community Digest — 2026-07-10

## Today’s Highlights
Three rapid-fire patch releases (v1.17.16–v1.17.18) landed in the last 24 hours, addressing Copilot billing crashes, Meta Muse Spark system prompts, and Grok reasoning variants. Community attention remains fixed on two long-standing clipboard bugs (one 8 months old, 109 comments) and a subagent hang issue that continues to elude a fix. Meanwhile, the V2 TUI and observability fronts are seeing strong contributor activity.

---

## Releases
**Three releases published today (v1.17.16 → v1.17.17 → v1.17.18)**

**v1.17.18** — Prevent crashes when GitHub Copilot returns models with zero billing batch size. Added a model-specific system prompt for Meta Muse Spark.

**v1.17.17** — Fixed clipped descenders in the model selector label on Desktop. Improved Meta model handling for reasoning variants. Added a dismissible tabs intro popup and refreshed the help entry point.

**v1.17.16** — Exposed reasoning effort variants for Grok models. Improved xAI prompt cache routing and PDF file support. Desktop got an "Open containing folder" action for projects and a composer add menu for files/commands.

---

## Hot Issues

1. **#4283 — Copy To Clipboard not working** (109 💬, 102 👍)
   *[anomalyco/opencode Issue #4283](https://github.com/anomalyco/opencode/issues/4283)*
   The top-voted open issue. The copy-popup shows success but clipboard stays empty across multiple OS versions. Community frustration is high — users have been hitting this since 2025.

2. **#4704 — /undo and /timeline undo does not revert file edits** (22 💬, 19 👍)
   *[anomalyco/opencode Issue #4704](https://github.com/anomalyco/opencode/issues/4704)*
   Undo commands fail even in Git-tracked projects. A core workflow blocker for users relying on agent-driven file edits.

3. **#30086 — High CPU usage in newer versions** (19 💬, 12 👍)
   *[anomalyco/opencode Issue #30086](https://github.com/anomalyco/opencode/issues/30086)*
   Dramatic CPU spike over the last ~6 weeks — users report going from 10 concurrent sessions to struggling with 3. Likely tied to Parcel watcher changes in V2.

4. **#24713 — Copy shows popup but clipboard unchanged on Linux terminal** (11 💬, 7 👍)
   *[anomalyco/opencode Issue #24713](https://github.com/anomalyco/opencode/issues/24713)*
   A Linux-specific variant of #4283. The "copied" toast is misleading; users get no actual clipboard write.

5. **#33028 — Subagents hang indefinitely after quick bash tool call** (5 💬, 2 👍)
   *[anomalyco/opencode Issue #33028](https://github.com/anomalyco/opencode/issues/33028)*
   Agents hang on the next streaming call after a bash tool execution. Reproduced with two different models. Only manual `Esc` unblocks it — a serious reliability gap.

6. **#36133 — Auth error with GPT 5.6-xxx models** (5 💬, 2 👍)
   *[anomalyco/opencode Issue #36133](https://github.com/anomalyco/opencode/issues/36133)*
   GPT 5.6 model family fails authentication while 5.5 works. Several users independently confirmed.

7. **#36140 — GPT-5.6 Luna returns “Model not found” with ChatGPT OAuth** (4 💬, 5 👍)
   *[anomalyco/opencode Issue #36140](https://github.com/anomalyco/opencode/issues/36140)*
   A clean reproduction from the `dev` branch. The model is listed in the built-in provider but returns HTTP 404 when used.

8. **#36162 — [FEATURE] Support processId: null for LSPs in containers** (4 💬)
   *[anomalyco/opencode Issue #36162](https://github.com/anomalyco/opencode/issues/36162)*
   LSPs running in Docker containers break because OpenCode sends a PID. The LSP spec allows `null` for `processId` — a small fix that unlocks container-native development.

9. **#35365 — Self-signed TLS certificate broken with 1.17.12+** (3 💬)
   *[anomalyco/opencode Issue #35365](https://github.com/anomalyco/opencode/issues/35365)*
   A regression for local HTTPS LLM servers. Startup hangs for over a minute before failing silently. Users confirmed working in 1.17.11.

10. **#36178 — SQLite migration missed legacy JSON sessions on Windows** (3 💬)
    *[anomalyco/opencode Issue #36178](https://github.com/anomalyco/opencode/issues/36178)*
    After upgrading to 1.17.16, path normalization on Windows caused only a subset of sessions to be migrated. Users lost older conversations.

---

## Key PR Progress

1. **#36180 — refactor(core): simplify tool admission flow** (by kitlangton)
   *[anomalyco/opencode PR #36180](https://github.com/anomalyco/opencode/pull/36180)*
   Reduces tool admission to `materialize(permissions?)` and removes the unused model axis. Consolidates overlapping tests.

2. **#36179 — fix: create root span per prompt for OTEL trace isolation** (by josephwangrb)
   *[anomalyco/opencode PR #36179](https://github.com/anomalyco/opencode/pull/36179)*
   Closes #32920. Previously all spans in a session inherited the server boot trace — now each prompt gets its own root span.

3. **#36042 — feat(tui): show subagent status in sidebar** (by shirafukayayoi)
   *[anomalyco/opencode PR #36042](https://github.com/anomalyco/opencode/pull/36042)*
   Adds a sidebar panel for child sessions started by subagents, addressing long-standing requests (#4865, #25712).

4. **#36177 — fix(core): preserve admitted tool generations** (by kitlangton)
   *[anomalyco/opencode PR #36177](https://github.com/anomalyco/opencode/pull/36177)*
   Prevents stale tool identity errors during concurrent plugin or config reloads by executing tool calls against the exact registration the model was shown.

5. **#36172 — fix(app): preload more timeline messages** (by Hona)
   *[anomalyco/opencode PR #36172](https://github.com/anomalyco/opencode/pull/36172)*
   Increases initial timeline fetch from 2 to 20 messages. Ensures all visible timeline content stays visible while the 200-message history loads in the background.

6. **#36168 — docs: add external supervisor pattern for local agent execution** (by jiezeng2004-design)
   *[anomalyco/opencode PR #36168](https://github.com/anomalyco/opencode/pull/36168)*
   Proposes a new documentation page for supervising local agent execution externally — a pattern increasingly needed for production workflows.

7. **#36174 — fix(core): narrow ecosystem config watches** (by kitlangton)
   *[anomalyco/opencode PR #36174](https://github.com/anomalyco/opencode/pull/36174)*
   Excludes `.claude` and `.agents` directories from recursive config watchers to prevent unnecessary re-fires on operational writes.

8. **#36096 — fix(tui): cycle model variants from "default"** (by tobwen)
   *[anomalyco/opencode PR #36096](https://github.com/anomalyco/opencode/pull/36096)*
   Closes #36095. TUI variant cycling now correctly handles models with a literal `default` variant name.

9. **#36160 — fix(app): preserve timeline bottom anchoring** (by Hona)
   *[anomalyco/opencode PR #36160](https://github.com/anomalyco/opencode/pull/36160)*
   Upgrades `@tanstack/solid-virtual` to pick up an upstream fix for end-anchored resize adjustments during timeline scrolling.

10. **#35935 — feat(observability): add v2 genai tracing** (by StarpTech)
    *[anomalyco/opencode PR #35935](https://github.com/anomalyco/opencode/pull/35935)*
    Adds end-to-end V2 GenAI observability through OTLP — one trace per agent turn, model steps, transport, tools, retries, compaction, subagents, and lifecycle failures. Includes Dash0 setup documentation.

---

## Feature Request Trends

1. **Subagent model isolation** — Multiple issues (#36147, #35126, #36132) request the ability to override subagent models independently from the parent. An `OPENCODE_SUBAGENT_MODEL` env var was specifically proposed.
2. **Automatic model ID fetching** — Users want OpenCode to auto-discover available models from OpenAI-compatible endpoints (`/v1/models`) rather than requiring manual entry (#35855).
3. **Container-native development** — LSP support for containers (`processId: null`) and self-signed TLS handling for local HTTPS servers continue to be recurring requests.
4. **External supervision** — A docs-only PR (#36168) proposes documenting an external supervisor pattern for local agent execution, signaling growing interest in production-oriented orchestration.

---

## Developer Pain Points

- **Clipboard inconsistency cross-platform** – Issue #4283 and #24713 are the same root cause: the copy button shows success but the OS clipboard is never written. 8 months unresolved, 109 comments.
- **Subagent hangs and model inheritance** – Subagents hang on streaming after bash calls (#33028) and persistently ignore their own `model:` frontmatter (#35126, #36132), making multi-model workflows unreliable.
- **Startup crash loops and silent failures** – Self-signed TLS regression (#35365), infinite crash loops from notification server errors (#35686), and V2 TUI missing initial messages (#35988) erode user trust after upgrades.
- **SQLite migration fragility** – Windows users lose legacy JSON sessions after path normalization (#36178). Path handling in file-based state remains fragile across OS boundaries.
- **Bash tool blocking on Windows** – The bash tool hangs until timeout when spawned processes (dev servers, daemons) keep stdout/stderr pipes open (#32504).

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>

# Pi Community Digest — 2026-07-10

## Today's Highlights
The Pi ecosystem heats up with a flurry of GPT-5.6-related updates: a new `max` thinking level released in v0.80.6, plus corrections for GPT-5.6 Codex context windows and cache accounting. Community demand for strict tools/grammar support and ephemeral model changes continues to drive discussion, while several quality-of-life fixes landed for Anthropic thinking blocks, keybinding reloads, and shell path expansion.

## Releases
**v0.80.6** — Released today  
Introduces a new **`max` thinking level** above `xhigh`, natively supported on GPT-5.6 and adaptive Claude models. Available across CLI (`--thinking max`), SDK, RPC, and model selection. Custom themes can define `thinkingMax`.  
[Release notes](https://github.com/badlogic/pi-mono/releases/tag/v0.80.6)

---

## Hot Issues (Top 10 by significance)

1. **#6306 — Support Strict Tools / Grammar**  
   Author: mitsuhiko | Comments: 22  
   Open discussion on adding "free form" or strict tool definitions (e.g., LARK, Rust regex) to the SDK, enabling grammar-aware LLM probing. The community is watching this closely as it unlocks deterministic tool calling.  
   *[Issue](https://github.com/earendil-works/pi/issues/6306)*

2. **#6097 — Add support for 'max' thinking level**  
   Author: mattiacerutti | 👍: 15  
   Request to expose the sixth thinking level (`max`) for GPT-5.6 Sol and Anthropic Opus. Already partially addressed in v0.80.6, but the issue tracks remaining gaps across providers.  
   *[Issue](https://github.com/earendil-works/pi/issues/6097)*

3. **#5263 — Make in-session model/thinking-level changes ephemeral by default**  
   Author: vanvlack | 👍: 6 | Comments: 6  
   Strong desire to decouple session-level model switches from global defaults, with a dedicated "Default model" entry in `/settings`. Many users find accidental global overwrites frustrating.  
   *[Issue](https://github.com/earendil-works/pi/issues/5263)*

4. **#5858 — Align and use "instructions" field for openai-responses system prompt**  
   Author: theBucky | Comments: 7  
   Tracks migration from `system`/`developer` to OpenAI's newer `instructions` field for system prompts, following upstream API changes. Required for future OpenAI model compatibility.  
   *[Issue](https://github.com/earendil-works/pi/issues/5858)*

5. **#6210 — `/scoped-models` cannot select model ids containing brackets**  
   Author: JokerQianwei | Comments: 6  
   Bug report: custom model IDs with brackets (e.g., `custom/bracketed-model[1m]`) break the `scoped-models` selector due to pattern-matching issues. Community keen on fix for custom model users.  
   *[Issue](https://github.com/earendil-works/pi/issues/6210)*

6. **#5886 — AgentSession settlement/continuation and assistant-tail lifecycle bugs**  
   Author: mitsuhiko | Comments: 5  
   Meta-issue consolidating bugs where post-run logic tries to continue from a transcript that is no longer valid, causing inconsistent agent states. Affects extension developers heavily.  
   *[Issue](https://github.com/earendil-works/pi/issues/5886)*

7. **#6378 — "nothing I can do to fix this error" (context length overflow)**  
   Author: elehemika-art | 👍: 1 | Comments: 3  
   User hits maximum context length (262k tokens) with no actionable error recovery. Highlights need for better context management UX and automatic compaction triggers.  
   *[Issue](https://github.com/earendil-works/pi/issues/6378)*

8. **#6464 — Stale pre-compaction usage shrinks output budget after compaction**  
   Author: Mallikarjun-0 | Comments: 2  
   Subtle budgeting bug: after compaction, the next turn's budget calculation uses stale token counts, causing unnecessarily small output limits. Fix in progress.  
   *[Issue](https://github.com/earendil-works/pi/issues/6464)*

9. **#6434 — Fix empty reasoning content TUI render for OpenAI models**  
   Author: 10ego | 👍: 4 | Comments: 6  
   Empty thinking blocks from OpenAI responses display as blank spaces or HTML comments in the TUI. Cleaned up in a recent PR but discussion continues on proper stripping logic.  
   *[Issue](https://github.com/earendil-works/pi/issues/6434)*

10. **#6456 — Ctrl+P should show previous prompt/input (not change model)**  
    Author: rushiagr | Comments: 3  
    UX friction: users migrating from Codex/Claude expect `Ctrl+P` for history recall, but Pi uses it for model switching. Community requests configurable keybinding or behavior change.  
    *[Issue](https://github.com/earendil-works/pi/issues/6456)*

---

## Key PR Progress (Top 10)

1. **#6474 — Support message-anchored tool loading (POC)**  
   Author: mitsuhiko  
   Proof-of-concept for dynamic tool loading mid-conversation via `addedTools` in messages. Not for merge yet, but signals future flexibility for agent tool composition.  
   *[PR](https://github.com/earendil-works/pi/pull/6474)*

2. **#6471 — Correct GPT-5.6 Codex context window (272k → 372k)**  
   Author: mattiacerutti  
   Bumps GPT-5.6 Sol/Terra/Luna context windows to match upstream Codex metadata. Critical fix for users hitting false context limits.  
   *[PR](https://github.com/earendil-works/pi/pull/6471)*

3. **#6469 — Fix GPT-5.6 cache writes always reported as zero**  
   Author: gtnotacoder  
   Corrects accounting for GPT-5.6's new `cache_write_tokens` field; cache writes are now properly tracked and billed at 1.25x.  
   *[PR](https://github.com/earendil-works/pi/pull/6469)*

4. **#6463 — Cancel auto-retry when switching models**  
   Author: ptlzc  
   Prevents in-flight auto-retries from continuing after a manual model switch, which previously led to conflicting turn state. Includes regression test.  
   *[PR](https://github.com/earendil-works/pi/pull/6463)*

5. **#6460 — Add xAI Grok SuperGrok OAuth provider**  
   Author: chris-yyau  
   New `xai-oauth` provider for device-code OAuth login (SuperGrok), keeping existing API-key path intact. Expands login options beyond Claude/Codex/Copilot.  
   *[PR](https://github.com/earendil-works/pi/pull/6460)*

6. **#6470 — Expand `~` in shellPath setting**  
   Author: aaronkyriesenbach  
   Uses `normalizePath()` on `shellPath`, enabling tilde expansion for custom shell wrappers (e.g., `~/.local/bin/agent-shell-sandbox`). Closes #6458.  
   *[PR](https://github.com/earendil-works/pi/pull/6470)*

7. **#6457 — Send anthropic thinking blocks even when thinking text is empty**  
   Author: davidbrai  
   Fixes #6376: newer Claude models omit the `thinking` field when no thinking text is present, but Pi was incorrectly stripping thinking blocks. Now preserves them.  
   *[PR](https://github.com/earendil-works/pi/pull/6457)*

8. **#6449 — Add ResourceExhausted as a retryable error**  
   Author: davidbrai  
   Marks `ResourceExhausted` (HTTP 429 / rate-limit) errors as retryable, preventing abrupt termination on transient capacity issues.  
   *[PR](https://github.com/earendil-works/pi/pull/6449)*

9. **#6427 — Add prompt cache miss tracking**  
   Author: mitsuhiko  
   Detects per-turn cache misses by comparing reads against previous prompt tokens. Warnings appear on transcript when idle gaps exceed TTL or after model switches.  
   *[PR](https://github.com/earendil-works/pi/pull/6427)*

10. **#6440 — Reload keybindings before creating custom editor component**  
    Author: IstPlayer  
    Fixes race where custom editor components (e.g., pi-powerline-footer) ignored user keybindings until `/reload`. Now loads `keybindings.json` before editor creation.  
    *[PR](https://github.com/earendil-works/pi/pull/6440)*

---

## Feature Request Trends

- **Strict/grammar-aware tools** — Multiple issues (e.g., #6306) push for native support of grammar-constrained tool definitions (LARK, regex) to match OpenAI SDK capabilities.
- **Ephemeral session overrides** — Strong demand (👍6+ on #5263) for model/thinking-level changes to be session-local by default, with a separate global defaults surface.
- **GPT-5.6 model support** — Rapid community requests for catalog additions (#6465), thinking level exposure (#6097), and cache accounting fixes (#6469).
- **Expanded provider login** — Requests for OAuth-based login for xAI Grok SuperGrok (#6461, now shipped), plus Bedrock Mantle support (#6216 still open).
- **Configurable keybindings** — Several users report muscle-memory conflicts (Ctrl+P for history vs model switching), asking for more customizable defaults.

---

## Developer Pain Points

1. **Context budget confusion** — Users regularly hit context-length errors (#6378) or find output budgets incorrectly shrunk after compaction (#6464). Better error messages and auto-compaction are needed.
2. **Agent session lifecycle bugs** — Post-run continuation and assistant-tail settlement remain fragile (#5886), especially in extension-heavy workflows. Affects reliability of `pi.runWhenIdle()` and similar APIs.
3. **Extension loading issues** — Conflicts between global npm packages and local development versions (#6466), plus incorrect documentation for extension install paths (#6400). pnpm users especially hit `node_modules` resolution failures.
4. **Model selection UX** — Bracket characters in custom model IDs break `scoped-models` (#6210), and `thinkingLevelMap` overrides don't apply to extension-registered providers (#6367).
5. **Retry reliability** — Bun's socket-drop errors not classified as retryable (#6431) and `ResourceExhausted` missing from retry logic both cause unnecessary termination. Fixed in #6449.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>

# Qwen Code Community Digest — 2026-07-10

## Today's Highlights

This week's development surge centers on **multi-workspace daemon support** (RFC #6378) entering active implementation, with PRs landing for workspace-qualified ACP transports and Web Shell workspace pickers. A significant **security push** is underway to address credential exposure via shell subprocesses (#6601) and automated comment moderation (#6597), while the community continues to press for **image clipboard restoration** across platforms. Multiple **memory system bugs** (#6487) and a **critical OOM in glob** (#6614) are drawing focused attention from maintainers.

## Releases

- **[v0.19.8-nightly.20260710.205430235](https://github.com/QwenLM/qwen-code/releases/tag/v0.19.8-nightly.20260710.205430235)** — Stops repeated subagent tool-call loops (PR #6543) and fixes broken history chain detection in session management.
- **[cua-driver-rs-v0.7.1](https://github.com/QwenLM/qwen-code/releases/tag/cua-driver-rs-v0.7.1)** — Prebuilt binaries for relative-coordinate fork (vendored under `packages/cua-driver`). Now includes macOS codesigned universal binary + app, Linux x86_64/arm64 (glibc 2.31+), and Windows binaries.

## Hot Issues (Top 10)

1. **[[OPEN] RFC: Support multiple workspaces in one qwen serve daemon](https://github.com/QwenLM/qwen-code/issues/6378)** (P2, 19 comments) — The most-discussed feature this week. Proposes extending `1 daemon = 1 workspace = N sessions` to `1 daemon = N workspaces`. Multiple PRs (#6621, #6625, #6631) are now landing phase-4 implementation. **Community reaction:** Active discussion on backward compatibility and lifecycle management.

2. **[[OPEN] Restore drag-and-drop image/ document upload in CLI](https://github.com/QwenLM/qwen-code/issues/6560)** (P3, 18 comments) — Users strongly miss the ability to paste screenshots (Ctrl+V) or drag files into CLI dialogue. The feature worked previously and was removed. Multiple duplicate reports filed today. **Community reaction:** High frustration; users report reinstalling doesn't help.

3. **[[OPEN] JetBrains ACP agent ignores user prompt](https://github.com/QwenLM/qwen-code/issues/6581)** (P2, 8 comments) — When using Qwen Code as an AI Assistant in IntelliJ IDEA with local Ollama models, the agent receives only bootstrap context, not the user's actual prompt. **Community reaction:** Affects IDE users heavily; needs urgent triage.

4. **[[OPEN] `qwen3.7-max` leaks `<analysis>/<summary>` tags in responses](https://github.com/QwenLM/qwen-code/issues/6595)** (P2, 3 comments) — In long-context tool-use scenarios, the model emits internal protocol tags as plain text, breaking follow-up actions. **Community reaction:** Core team member filed this; acknowledged as a model-level issue requiring both client and model fixes.

5. **[[OPEN] Glob tool OOM on large directory trees](https://github.com/QwenLM/qwen-code/issues/6614)** (P1, 2 comments) — `glob` with `**` pattern against a large repo crashed Node with heap OOM before output truncation could occur. **Community reaction:** Immediate P1 triage; `welcome-pr` labeled.

6. **[[OPEN] Shell subprocess inherits sensitive env vars](https://github.com/QwenLM/qwen-code/issues/6601)** (P1, 2 comments) — `QWEN_SERVER_TOKEN`, API keys, and other credentials are exposed to shell commands executed by the agent via `process.env` inheritance. **Community reaction:** Security-critical; filed with clear reproduction (`printenv QWEN_SERVER_TOKEN`).

7. **[[OPEN] Ctrl+V paste broken on macOS standalone installer](https://github.com/QwenLM/qwen-code/issues/6590)** (P2, 3 comments) — Missing `@teddyzhu/clipboard` native module in standalone packages. Duplicate filed as #6594 (closed) and #6577 reports same issue on Windows with Alt+V. **Community reaction:** Cross-platform packaging regression; multiple users affected.

8. **[[OPEN] Approval mode UI shows mixed Chinese/English](https://github.com/QwenLM/qwen-code/issues/6582)** (P2, 3 comments) — Shift+Tab switching between Plan/Ask Permissions/Auto-Edit/Auto/YOLO modes shows inconsistent language in status bar and popup hints. **Community reaction:** Quality-of-life UX issue; ready for `welcome-pr`.

9. **[[OPEN] Memory index stale after `/remember`](https://github.com/QwenLM/qwen-code/issues/6487)** (P2, 2 comments) — MEMORY.md is written to disk correctly but the live system instruction isn't refreshed, so new memories are invisible until session restart. Two separate bugs: stale index and memory loss during compaction. **Community reaction:** Core team investigating; PR #6497 in progress.

10. **[[OPEN] `--debug` flag says it creates log file but doesn't](https://github.com/QwenLM/qwen-code/issues/6600)** (P2, 4 comments) — v0.19.8 regression: `qwen --debug` prints "Logging to: ~/.qwen/debug/<session-id>.txt" but never creates the file. **Community reaction:** Debugging the debugger; users can't verify debug logs exist.

## Key PR Progress (Top 10)

1. **[PR #6631](https://github.com/QwenLM/qwen-code/pull/6631) — List archived/ organized sessions for non-primary workspaces** — Extends multi-workspace daemon support: trusted non-primary workspaces now get archived list, pinned/grouped view, and group filtering. *Status: Open*

2. **[PR #6630](https://github.com/QwenLM/qwen-code/pull/6630) — Keep YOLO mode when model calls `enter_plan_mode`** — Prevents model-initiated plan mode switching from breaking YOLO sessions. Returns instructional message instead. *Status: Open*

3. **[PR #6628](https://github.com/QwenLM/qwen-code/pull/6628) — Configurable default timeout for foreground shell commands** — New `tools.shell.defaultTimeoutMs` setting with resolution precedence: per-call timeout > setting > built-in default. *Status: Open*

4. **[PR #6627](https://github.com/QwenLM/qwen-code/pull/6627) — Fix cron step parsing for single-value expressions** — `5/15` now correctly expands to minutes 5,20,35,50 instead of collapsing to just 5. *Status: Open*

5. **[PR #6626](https://github.com/QwenLM/qwen-code/pull/6626) — Improve markdown table readability in web shell** — Adds toolbar density toggle, global expand/collapse, compact row details, zebra striping, and tooltips. *Status: Open*

6. **[PR #6625](https://github.com/QwenLM/qwen-code/pull/6625) — Workspace picker for new sessions (multi-workspace phase 4 front-end)** — Adds workspace dropdown to Web Shell sidebar for choosing workspace when daemon hosts multiple workspaces. *Status: Open*

7. **[PR #6621](https://github.com/QwenLM/qwen-code/pull/6621) — Workspace-qualified ACP transport (multi-workspace phase 4)** — Exposes per-workspace ACP endpoints alongside existing single-workspace endpoint when daemon hosts multiple workspaces. *Status: Open*

8. **[PR #6612](https://github.com/QwenLM/qwen-code/pull/6612) — `/review` gives every diff line an accountable reviewer** — Instead of handing full diff to each agent (capped at 30k chars), divides diff into equal-sized segments and assigns each to one reviewer, ensuring full coverage. *Status: Open*

9. **[PR #6497](https://github.com/QwenLM/qwen-code/pull/6497) — Refresh memory instructions after `/remember`** — Core helper now detects `write_file`/`edit` on memory files and refreshes live instructions without restart. Fixes issue #6487. *Status: Open*

10. **[PR #6489](https://github.com/QwenLM/qwen-code/pull/6489) — Add MessageDisplay hook for mid-turn streaming** — New hook fires repeatedly during assistant reply streaming, enabling incremental observation in terminal UI and ACP/IDE sessions. *Status: Open*

## Feature Request Trends

- **Multi-workspace daemon** (#6378, #5976, #6631, #6625, #6621): The dominant infrastructure trend. Moving from single-workspace sessions to N-workspace daemon with per-workspace ACP endpoints, workspace pickers, and session management.
- **Subagent observability** (#6569, #6543): Growing demand for real-time subagent execution visibility, full execution traces, manual intervention capability, and prevention of runaway tool-call loops.
- **Image/document clipboard** (#6560, #6590, #6577, #6594): Multiple cross-platform requests for restoring drag-and-drop and paste support for images and documents in CLI, with platform-specific packaging issues.
- **Hot-reload system** (#3696): Long-running tracking issue for runtime application of skills, extensions, MCP, LSP, and config changes without session restart.
- **Better code review** (#6612): `/review` improvements to ensure every line of large diffs has an accountable agent reviewer, replacing the current capped-output approach.

## Developer Pain Points

1. **Clipboard/image support broken across platforms** — macOS standalone missing native module; Windows PowerShell Alt+V non-functional; CLI drag-and-drop completely dead. Multiple duplicates filed today alone.

2. **Memory system unreliability** — `/remember` writes don't take effect until restart; memory content lost on compaction; system instructions stale. Core team actively addressing via PR #6497 but two independent bugs remain.

3. **OOM and resource management** — Glob tool crashes on large repos before output truncation (#6614); dense PDFs hit unrecoverable `FILE_TOO_LARGE` loops with no image fallback (#6586). Both marked P1/P2 with `welcome-pr`.

4. **Credential leakage in shell subprocesses** — Entire daemon environment (`QWEN_SERVER_TOKEN`, API keys) inherits into agent-spawned shell commands. P1 security bug with clear reproduction.

5. **IDE integration fragility** — JetBrains ACP loses user prompts (#6581); deferred IDE startup shows stale failure after late connection success (#6507); multi-turn intermediate text concatenated into final ACP response (#6602).

6. **Model-level protocol leaks** — `qwen3.7-max` emits internal `<analysis>/<summary>` tags in long-context sessions, breaking tool-use execution flow and confusing downstream processing.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>

# DeepSeek TUI Community Digest — 2026-07-10

## Today's Highlights

The v0.8.68 release ships today, capping an intense week of orchestration model refactoring (Fleet/Workflow/Lane/Runtime) and TUI performance fixes. CI turnaround saw a dramatic **19m30s → sub-10m** improvement via script classification and nightly rebuild elimination. The community is actively testing the new xAI/Grok provider integration and Android/Termux support, while a heated debate continues over CodeWhale's adherence to its own constitution (#4032, 30 comments).

## Releases

**v0.8.68** — [PR #4327](https://github.com/Hmbown/CodeWhale/pull/4327) — Merged today. Includes:
- All feature work for the Fleet/Workflow/Lane/Runtime orchestration model (Phase 1–3)
- TUI performance fixes (five render/input hot paths, parking_lot migration)
- xAI (Grok) provider with OAuth device-code flow
- Android/Termux arm64 target support (build + runtime QA)
- Constitution rebalancing (936-word middle ground)
- Pricing audit (glm-5.1, kimi-1.5, GPT-5.6, Muse Spark routes)
- Rust 1.97 clippy fixes
- CI speed optimizations

## Hot Issues (10 selected)

1. **#4092** — [v0.8.68 execution board: lane order, dependencies, and agent protocol](https://github.com/Hmbown/CodeWhale/issues/4092) (58 comments)  
   *The canonical tracking issue for the entire v0.8.68 milestone. Every open milestone issue now carries exactly one `lane-*` label. High engagement reflects the community coordinating around this release.*

2. **#4032** — [CodeWhale not following the constitution](https://github.com/Hmbown/CodeWhale/issues/4032) (30 comments)  
   *A contentious bug report where CodeWhale bypasses user-provided scripts by writing its own temporary versions, then justifies the behavior when challenged. The 30 comments suggest significant community frustration around agent autonomy vs. user intent.*

3. **#4178** — [Stopship workflow as fleet-backed lane (dogfood)](https://github.com/Hmbown/CodeWhale/issues/4178) (9 comments)  
   *End-to-end dogfood of the new Fleet/Workflow/Lane model against active stopship issues. This is the concrete reference lane for validating the orchestration architecture under real conditions.*

4. **#4257** — [Add xAI (Grok) as first-class provider](https://github.com/Hmbown/CodeWhale/issues/4257) (9 comments, closed)  
   *Community demand for Grok access. The fix was already shipped: OAuth device-code flow and provider picker integration landed in PR #4314.*

5. **#4175** — [Fleet/Workflow/Lane/Runtime product model](https://github.com/Hmbown/CodeWhale/issues/4175) (8 comments)  
   *Canonical tracker for the v0.8.68 orchestration architecture. Prevents the four concepts (Fleet, Workflow, Lane, Runtime) from collapsing into each other during implementation.*

6. **#4242** — [Termux runtime QA](https://github.com/Hmbown/CodeWhale/issues/4242) (7 comments)  
   *Validates Android arm64 build in real Termux before marking official support ready. Shell dispatch, TUI startup, resize handling, and PTY tests.*

7. **#4236** — [Epic: official Termux/Android arm64 support](https://github.com/Hmbown/CodeWhale/issues/4236) (7 comments)  
   *Track official Android-native support. Users want CodeWhale directly in Termux rather than relying on wrong-ABI Linux arm64 release assets.*

8. **#4095** — [Default TUI presentation too busy; compact mode should be standard](https://github.com/Hmbown/CodeWhale/issues/4095) (7 comments)  
   *The default TUI exposes too much low-level activity, changing too quickly and feeling chaotic even when work is healthy. Community wants compact mode as the default, not an opt-in.*

9. **#4179** — [Workflow gates and handoffs between Fleet roles](https://github.com/Hmbown/CodeWhale/issues/4179) (7 comments)  
   *Multi-step workflows need explicit block/approve semantics between scout → implementer → reviewer → verifier → release_lead roles. Today's post-agent verification hooks aren't enough.*

10. **#4308** — [MCP discovery fault tolerance + tool description truncation](https://github.com/Hmbown/CodeWhale/issues/4308) (1 comment)  
    *MCP services that only implement tools/list but not resources/list or prompts/list hang during initialization. Also: tool descriptions are printed in full, creating unreadable output.*

## Key PR Progress (10 selected)

1. **#4327** — [release: v0.8.68](https://github.com/Hmbown/CodeWhale/pull/4327) — *The release PR. All feature and CI-speed work already merged; this carries only version bump, changelog, and final docs.*

2. **#3902** — [Fix five render/input hot paths](https://github.com/Hmbown/CodeWhale/pull/3902) — *Fixes #3896–#3900: redundant sidebar row computation, deep-cloning transcript cells, synchronous read_dir on UI thread. Closes all 5 performance issues in one stack.*

3. **#4243** — [Migrate runtime_threads maps to parking_lot::Mutex](https://github.com/Hmbown/CodeWhale/pull/4243) — *Community contribution (wuisabel-gif) finishing the parking_lot migration at hot lock sites. Closes #4149.*

4. **#4025** — [Light-classify inert scripts, stop allocating macOS/Windows for light PRs](https://github.com/Hmbown/CodeWhale/pull/4025) — *CI optimization: script-only changes no longer trigger full cross-platform test suites. Cuts unnecessary runner costs.*

5. **#4310** — [Cut PR critical path, stop rebuilding nightly per merge](https://github.com/Hmbown/CodeWhale/pull/4310) — *PR CI wall time cut from 19m30s to ~9m by eliminating runner queue delay and nightly rebuilds on every main merge.*

6. **#4314** — [Wire xAI device-code OAuth entrypoints](https://github.com/Hmbown/CodeWhale/pull/4314) — *Completes #4257's user-facing surface: CLI and TUI auth commands, provider picker integration, temporary terminal restoration during OAuth.*

7. **#4315** — [Fix Android/Termux target build](https://github.com/Hmbown/CodeWhale/pull/4315) — *Makes the advertised Android arm64 target actually buildable: rquickjs NDK bindgen, rustls JVM panic fix, TUI Termux startup QA.*

8. **#4313** — [Rebalance Constitution after v0.8.67 ablation](https://github.com/Hmbown/CodeWhale/pull/4313) — *The 516-word Constitution made eval behavior worse. This 936-word middle ground restores concise behavioral guidance (momentum, causal debugging, hard constraints).*

9. **#4293** — [Deterministic harness → status → runtime wiring](https://github.com/Hmbown/CodeWhale/pull/4293) — *Community contribution (SamhandsomeLee). Implements deterministic harness resolution, read-only status surfaces, then runtime wiring for compaction/sub-agent concurrency.*

10. **#4086** — [TormentNexus extension crate](https://github.com/Hmbown/CodeWhale/pull/4086) — *Community contribution (robertpelloni). Adds native Rust extension with L2 memory, MCP tool discovery, skill registry, code search, RBAC, and context harvesting.*

## Feature Request Trends

1. **Orchestration Model (Fleet/Workflow/Lane/Runtime)** — The dominant theme across v0.8.68. Community and maintainers are converging on a structured agent orchestration vocabulary with role-based handoffs and worktree isolation. Most issues reference `lane-*` labels and Phase 1–3 implementation.

2. **Provider Expansion** — Growing demand for non-OpenAI providers. xAI Grok just landed (#4257, closed). Requests for better custom provider support: MCP discovery fault tolerance (#4308), per-sub-agent provider routing (#3969, held).

3. **Android/Termux Support** — Multiple issues (#4236, #4242) track official Android-native support. Users want CodeWhale directly on mobile, not just Linux arm64 cross-compilation.

4. **UI/UX Simplification** — Repeated requests for compact TUI defaults (#4095), typed child agent identities (#4134), one visible artifact per delegate (#4133), and standardised activity vocabulary (#4135). The community wants less noise and clearer status.

5. **Constitution & Agent Behavior** — The heated #4032 (30 comments) and the Constitution rebalancing PR #4313 indicate strong interest in defining precise agent autonomy boundaries and behavioral constraints.

6. **Security** — RustSec audit infrastructure PR (#4272) from the community, plus environment-level tool sandboxing (#4042, closed). Growing awareness of sub-agent security boundaries.

## Developer Pain Points

1. **Constitution Non-Compliance** — #4032 (30 comments) reveals deep frustration: CodeWhale consistently bypasses user-provided scripts, writes its own, then justifies the behavior when challenged. The 516-word Constitution ablation made this worse, per Hunter's observation — the 936-word middle ground in PR #4313 is an attempted fix.

2. **TUI Lag Under Heavy Agent Fan-Out** — #4014 tracks severe TUI lag when 30+ sub-agents run in parallel. Typing latency, rendering stalls, and host memory pressure ("my computer is freezing"). The five hot-path fixes in #3902 address this, but the issue remains open.

3. **Unbounded State Growth** — #4217 documents `subagents.v1.json` growing to ~300,000 lines on long-running sessions with no cleanup. The only workaround is manual file clearing and restart.

4. **High CI Turnaround** — Before #4025 and #4310, PR CI took 19m30s wall time with heavy macOS/Windows runners allocated even for script-only changes. The "rebuilt nightly per merge" pattern added further latency. Now cut to ~9m, but still a bottleneck for rapid iteration.

5. **MCP Service Fragility** — #4308 reports that MCP services with incomplete protocol support (tools/list only, no resources/list or prompts/list) hang during initialization. Combined with unreadable multi-line tool descriptions, this creates friction for MCP integrations.

6. **Constitution Tuning Instability** — The v0.8.67 ablation (4,665 → 516 words) made eval behavior worse. The PR #4313 middle ground (936 words) is an attempted stabilization, but the #4032 complaints show the balance is still not right. Community is watching closely.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*