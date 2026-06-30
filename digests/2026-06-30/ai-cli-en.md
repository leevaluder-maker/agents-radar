# AI CLI Tools Community Digest 2026-06-30

> Generated: 2026-06-30 02:30 UTC | Tools covered: 9

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

# AI CLI Developer Tools: Cross-Tool Comparison Report
**Date:** 2026-06-30

---

## 1. Ecosystem Overview

The AI CLI tools landscape is experiencing intense competition and rapid iteration, with all major tools shipping weekly or daily releases. Agent reliability and cost transparency have emerged as the universal pain points across every tool, while sub-agent architectures—once a differentiator—are now table stakes. Enterprise adoption pressures are driving security hardening (PII redaction, sandbox escapes, auth improvements) across Claude Code, Codex, and Gemini CLI simultaneously. A notable bifurcation is emerging: established tools (Claude Code, Codex, Copilot CLI) focus on stability and enterprise features, while newer entrants (Pi, Kimi, Qwen Code) race to close feature gaps and fix fundamental UX issues. The ecosystem is maturing from "can it work?" to "can I trust it with production workloads?"—and the answer remains mixed.

---

## 2. Activity Comparison

| Tool | Hot Issues (24h) | PRs Updated (24h) | Release Status | Community Engagement Signal |
|------|-----------------|-------------------|----------------|---------------------------|
| **Claude Code** | 10 active (top: 146👍) | 3 | v2.1.196 (today) | High: legacy bug #26224 (146👍, 124 comments) persists since Feb |
| **OpenAI Codex** | 10 active (top: 276👍) | 10 | rust-v0.142.4 + alpha | Highest: #14593 (276👍, 626 comments) on token burning |
| **Gemini CLI** | 10 active (8+ avg👍) | 10 (3 merged) | v0.51.0-nightly (today) | Moderate: rapid PR churn, lower issue engagement |
| **Copilot CLI** | 10 active (5 avg👍) | Not tracked | v1.0.66-2 (today) | Moderate: critical agent session bug, UI regressions |
| **Kimi Code** | 1 active (0👍) | 0 | None | Low: dormant period, single UX issue |
| **OpenCode** | 10 active (16 avg👍) | 10 (1 merged) | v1.17.10 (recent) | High: 2 major stability bugs (segfault, compaction loop) |
| **Pi** | 10 active (10 avg👍) | 10 (mostly closed) | v0.80.x (stable) | Moderate: active bugfix wave, growing package ecosystem |
| **Qwen Code** | 10 active (varying) | 10 (rapid) | v0.19.3-nightly (today) | High: heavy community activity, multi-provider focus |
| **DeepSeek TUI** | 10 active (high token concern) | 10 (all merged) | v0.8.66 (gated) | Very High: 20+ PRs merged in 24h, cache hit ratio anger |

**Notable Observations:**
- **Codex** has the most engaged community by comment count (626 on #14593)
- **DeepSeek TUI** merged the most PRs in 24h (10), all focused on sub-agent freeze fixes
- **Kimi Code** is concerningly quiet—1 issue, 0 PRs, 0 releases
- **Claude Code** has the highest-upvoted unresolved bug (#26224, 146👍, 124 comments)

---

## 3. Shared Feature Directions

The following requirements appear across **three or more** tool communities:

| Requirement | Tools | Specific Pain Points |
|------------|-------|---------------------|
| **Sub-agent / Swarm Observability** | Claude Code, Codex, Gemini CLI, Copilot CLI, DeepSeek TUI | Users cannot debug what sub-agents are doing: blocked main loops, opaque failures, false "GOAL" success reporting. Request: per-subagent model/effort/trace visibility. |
| **Cost & Token Transparency** | Claude Code, Codex, Copilot CLI, OpenCode, DeepSeek TUI | Universal frustration: unexplained token consumption, rate limits at <100% usage, no session-level cost breakdown, runaway retries draining quotas overnight. |
| **Enterprise Auth & Compliance** | Claude Code, Codex, Copilot CLI, Gemini CLI, Pi | AWS Bedrock auth in extensions, org-managed configs, PII redaction, opt-in training data contribution, OAuth token pattern flexibility. |
| **TUI Customization** | Claude Code, Codex, Copilot CLI, Qwen Code, Pi | Customizable status lines, autoscroll controls, alt-screen toggles, input mode configuration (Enter vs Shift+Enter), hotbar opt-in. |
| **Platform-Specific Stability** | Claude Code, Codex, Gemini CLI, Copilot CLI, Qwen Code | Windows: missing UI elements, MCP batch file failures, sandbox regressions. macOS: zombie processes, SQLite write amplification. Linux: scroll refresh bugs. |
| **Background / Autonomous Operation** | Claude Code, Codex, Gemini CLI, Qwen Code, DeepSeek TUI | "Set and forget" workflows: autonomous loop mode, daemon-managed channels, background monitoring tools, session persistence without user input. |
| **Agent Failure Handling** | Claude Code, Codex, Gemini CLI, Copilot CLI, DeepSeek TUI | Infinite retry loops, false success reports, stuck sessions with no kill switch, tool call cascading without fallback strategies. |

**Emerging Pairwise Alignments:**
- **Claude Code ↔ OpenCode**: Both have compaction loops, session auto-compact failures, and demand for inline model switching
- **Codex ↔ DeepSeek TUI**: Both have dominant token/cost complaints (#1 issue by engagement)
- **Gemini CLI ↔ Qwen Code**: Both have subagent governance issues (false "GOAL" termination, tag leakage into parent context)
- **Pi ↔ Copilot CLI**: Both have TUI autoscroll/stream stability problems

---

## 4. Differentiation Analysis

### Feature Focus

| Tool | Primary Differentiator | Target User | Weakest Area |
|------|----------------------|-------------|-------------|
| **Claude Code** | Enterprise QoL (org defaults, session naming, Cowork) | Enterprise teams | Performance regression (#26224) eroding trust |
| **OpenAI Codex** | Multi-model support, Git security hardening | Security-conscious developers | Token/billing transparency is community's #1 complaint |
| **Gemini CLI** | AST-aware code navigation, agent evaluations | AI/ML researchers | Agent reliability (hangs, false successes) |
| **Copilot CLI** | GitHub ecosystem integration, plugin/skill system | GitHub-centric orgs | Windows fragility, agent session management |
| **Kimi Code** | Mobile CLI focus (hypothetically) | Mobile developers | Neglect: 1 issue, 0 PRs, 0 releases today |
| **OpenCode** | Plugin SDK, MCP prompts, free model support | Plugin developers, cost-sensitive users | Windows stability (Bun segfault), provider compatibility |
| **Pi** | Broad provider support, open package ecosystem | Self-hosters, provider-agnostic users | Provider error opacity, auth confusion |
| **Qwen Code** | Multi-provider (Qwen-native), daemon/channel architecture | Asian markets, multi-platform CI/CD | TUI rendering fragility, model-specific bugs |
| **DeepSeek TUI** | Aggressive sub-agent parallelism, YOLO/safety modes | Power users, high-throughput developers | Cache hit ratio (30% vs competitors' 95%+), token waste |

### Technical Approach Differences

| Dimension | Spectrum |
|----------|---------|
| **Model Strategy** | Single-model strongest (Claude Code) ↔ Multi-provider agnostic (Pi, Qwen Code, Codex) |
| **Agent Architecture** | Centralized agent (Copilot CLI) ↔ Heavy sub-agent fanout (DeepSeek TUI, Gemini CLI) |
| **Plugin Ecosystem** | Curated (Claude Code) ↔ Open MCP/plugin SDK (OpenCode, Pi, Copilot CLI) |
| **Platform Support** | macOS-first (Claude Code) ↔ Cross-platform with gaps (All—Windows is universally weakest) |
| **Deployment Model** | Cloud-dependent (Codex, Copilot CLI) ↔ Local-first with optional cloud (Gemini CLI, Pi) |

**Strategic Insight:** Claude Code and Codex are converging from opposite directions—Claude Code adding multi-model support, Codex adding enterprise features. The mid-tier tools (OpenCode, Pi, Qwen Code) are racing to match baseline reliability while differentiating on provider flexibility and plugin ecosystems. DeepSeek TUI is the most aggressive on sub-agent parallelism but pays the price in cache efficiency.

---

## 5. Community Momentum & Maturity

### Momentum Leaders (Rapidly Iterating)

| Tool | Metric | Evidence |
|------|--------|----------|
| **DeepSeek TUI** | PR velocity | 10 PRs merged in 24h, all blocking v0.8.66 release |
| **Qwen Code** | Release cadence | Nightly releases, heavy PR activity across daemon/TUI/providers |
| **Gemini CLI** | PR diversity | 10 PRs across core, tools, VS Code companion, security |
| **OpenCode** | Feature breadth | 10 PRs covering MCP prompts, observability hooks, free model support |

These four tools are in active "catch-up and differentiate" mode, shipping multiple features per week.

### Maturity Leaders (Stable but Slower)

| Tool | Metric | Evidence |
|------|--------|----------|
| **Claude Code** | Release stability | v2.1.196 with incremental QoL; rare major regressions |
| **Copilot CLI** | Ecosystem integration | Tighter GitHub integration, slower feature churn |
| **Pi** | Community trust | Growing package ecosystem, consistent bugfix cadence |

These tools prioritize reliability over feature velocity but risk falling behind on sub-agent and cost transparency demands.

### Concerning Signals

| Tool | Risk |
|------|------|
| **Kimi Code** | Near-zero activity suggests resource constraints or deprioritization |
| **Codex** | 626-comment issue (#14593) on token burning with no clear resolution path erodes user trust |
| **Claude Code** | #26224 (hanging bug) unresolved since February—critical for team trust |
| **Copilot CLI** | Multiple UI regressions in v1.0.65/v1.0.66 suggest testing gaps |

### Community Health Indicators

- **Best self-correction:** DeepSeek TUI—identified sub-agent freeze, merged 6+ PRs in 24h to fix
- **Best documentation:** Claude Code—org defaults, session naming, GCP deployment docs
- **Most vocal community:** Codex—626 comments on token issue, 407👍 on SQLite logging
- **Most fragmented:** Qwen Code—spread across multiple providers, each with distinct bugs

---

## 6. Trend Signals

### For AI CLI Developers & Tool Makers

1. **Sub-agent observability is the new "must-have"** — Every tool with sub-agents has users demanding visibility into what sub-agents are doing. This is the #1 missing capability across the ecosystem. Expect all tools to ship sub-agent dashboards/traces within 6 months.

2. **Token cost transparency is the #1 trust builder** — Multiple 400+ comment threads on unexplained token consumption. Tools that ship per-session cost breakdowns, rate limit visibility, and predictive warnings will win user trust. This is currently everyone's weakest area.

3. **Autonomous "set and forget" mode is the next frontier** — Qwen Code's bare `/loop` autonomous mode, Codex's background monitoring requests, and Claude Code's `/fork` for IDE all point toward users wanting agents that run independently, not just in chat-turn mode. Expect background agent capabilities to become a key differentiator.

4. **Platform parity remains unsolved** — Windows is universally the weakest platform across all tools (missing UI elements, sandbox failures, MCP process management). macOS has specific SQLite/Zombie process issues. Linux has TUI rendering bugs. Cross-platform testing is clearly an afterthought—tool that nails all three will have a competitive advantage.

5. **Plugin ecosystems are commoditizing** — OpenCode, Pi, and Copilot CLI all now support MCP/plugin APIs. Claude Code has Cowork partners. The differentiation is shifting from "do you support plugins?" to "how well do plugins integrate with your agent architecture and security model?"

6. **Security hardening is accelerating** — Multiple active PRs across all tools on sandbox escaping (Gemini CLI's `.gitconfig` write protection, Codex's Git command isolation, DeepSeek TUI's YOLO authority preservation). Enterprise compliance requirements are driving this, but it benefits all users.

7. **Cache hit ratio is becoming a competitive metric** — DeepSeek TUI's cache hit ratio complaint (#1177: 30% vs competitors' 95%+) signals that users compare cache efficiency across tools. As context windows grow and prompt caching becomes standard, cache optimization will be a key cost differentiator.

8. **False success reporting is dangerous** — Multiple tools (Gemini CLI, DeepSeek TUI) have bugs where agents report "GOAL" or "success" after hitting MAX_TURNS or failing silently. This is a critical trust issue for autonomous workflows—users can't rely on agents that lie about their status.

9. **The mobile CLI gap is real** — Kimi Code's single issue (#2479) about Enter key behavior on mobile highlights a neglected use case. As developers work from phones/tablets for incident response and quick edits, mobile CLI UX will become important. No tool currently handles this well.

10. **Configurable model routing is emerging** — Feature requests for inline model switching, compaction-specific cheaper models, and free-tier model selection all point toward users wanting granular control over which model handles which task. This is a natural evolution as tooling supports multiple providers.

### For Tool Evaluators

- **If you need enterprise stability:** Claude Code (v2.1.196) or Copilot CLI (v1.0.66-2)—but monitor their unresolved bugs
- **If cost is your primary concern:** Pi (open ecosystem) or OpenCode (free model support)—but expect configuration friction
- **If you need maximum sub-agent parallelism:** DeepSeek TUI (v0.8.66, once released)—but cache efficiency is poor
- **If you work across multiple models/providers:** Codex, Pi, or Qwen Code—but each has provider-specific bugs
- **If you're on Windows:** Proceed with caution—all tools have Windows-specific regressions. Copilot CLI's MCP batch file fix (#3958) and Qwen Code's tilde path fix (#6030) suggest active work, but no tool is Windows-robust yet.

---

**Bottom Line for June 30, 2026:** The AI CLI tools ecosystem is in a reliability race. Every tool has at least one "trust-eroding" bug (hanging sessions, false success reports, runaway costs). The winners will be those that fix these fundamental issues before racing to add features. DeepSeek TUI's 10-PR-in-24h response to sub-agent freezes is a model response; Codex's 626-comment token issue with no clear resolution is a cautionary tale. Enterprise adoption will hinge on which tools demonstrate they can be trusted with production workloads—and right now, none have fully earned that trust.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)

Here is the community highlights report for the anthropics/skills repository.

---

## Claude Code Skills Community Highlights Report (Data as of 2026-06-30)

### 1. Top Skills Ranking

The following pull requests represent the most-discussed Skill submissions, ranked by community attention (comments and engagement).

1.  **Skill Creator Fixes (Meta-Skill Infrastructure)**
    - **PR:** [#1298](https://github.com/anthropics/skills/pull/1298) (Open)
    - **Functionality:** A critical bug fix for the `skill-creator` meta-skill, addressing a pervasive issue where `run_eval.py` reported **0% recall** for all skill descriptions. This effectively broke the skill description optimization loop.
    - **Discussion:** This is the central fix for the most reported ecosystem bug (see Issue #556). The discussion covers the root cause (the eval system failing to install the artifact as a real skill) and multiple Windows-specific stream reading and parallel worker failures.
    - **Status:** Open. This is the highest-priority item for the skill-creator toolchain.

2.  **Document Typography Skill**
    - **PR:** [#514](https://github.com/anthropics/skills/pull/514) (Open)
    - **Functionality:** A quality-of-life skill that prevents orphan words, widowed headers, and numbering misalignment in AI-generated documents.
    - **Discussion:** Highly praised for solving a universal nuisance. The conversation focuses on refining the rules and edge cases for detection.
    - **Status:** Open.

3.  **ODT (OpenDocument) Skill**
    - **PR:** [#486](https://github.com/anthropics/skills/pull/486) (Open)
    - **Functionality:** Enables Claude Code to create, fill, read, and convert OpenDocument Format files (.odt, .ods), including HTML conversion.
    - **Discussion:** Driven by demand for LibreOffice and open-source document workflow support. The conversation covers template filling and complex format parsing.
    - **Status:** Open.

4.  **Frontend-Design Skill Improvement**
    - **PR:** [#210](https://github.com/anthropics/skills/pull/210) (Open)
    - **Functionality:** A comprehensive revision of the existing `frontend-design` skill to make instructions more actionable and concrete for Claude to follow in a single conversation.
    - **Discussion:** Focused on the philosophy of skill design: ensuring instructions are specific enough to steer behavior without being overly rigid.
    - **Status:** Open.

5.  **Testing-Patterns Skill**
    - **PR:** [#723](https://github.com/anthropics/skills/pull/723) (Open)
    - **Functionality:** A full-stack testing skill covering the Testing Trophy model, unit testing (AAA pattern), React component testing, and E2E patterns.
    - **Discussion:** A response to high demand for software quality skills. The community is validating the inclusion of specific libraries and testing frameworks.
    - **Status:** Open.

6.  **SAP Predictive Analytics Skill**
    - **PR:** [#181](https://github.com/anthropics/skills/pull/181) (Open)
    - **Functionality:** Integrates SAP's open-source tabular foundation model (SAP-RPT-1-OSS) for predictive analytics on SAP business data.
    - **Discussion:** A niche but strong enterprise demand signal. The conversation details how to interface Claude with the SAP model and its specific data formats.
    - **Status:** Open.

7.  **Self-Audit Skill (Four-Dimension Quality Gate)**
    - **PR:** [#1367](https://github.com/anthropics/skills/pull/1367) (Open)
    - **Functionality:** A universal quality assurance skill that audits Claude’s output across four dimensions (Completeness, Consistency, Grounding, Harmlessness) before delivery.
    - **Discussion:** Very recent (June 28), but rapidly gaining traction. The community is interested in making this a baseline step for all agentic workflows.
    - **Status:** Open.

### 2. Community Demand Trends

Analysis of the most active Issues reveals three primary demand vectors:

- **Cross-Platform & Windows Compatibility (High Urgency):** Issues [#556](https://github.com/anthropics/skills/issues/556), [#1061](https://github.com/anthropics/skills/issues/1061), and [#1169](https://github.com/anthropics/skills/issues/1169) detail a systemic failure of the `skill-creator` evaluation loop on Windows and Linux. The core problem (`run_eval.py` reporting 0% recall) is the single most blocking issue for the entire skill development pipeline. This is not a new skill, but a critical infrastructure requirement.

- **Trust & Security Governance:** Issue [#492](https://github.com/anthropics/skills/issues/492) (32 comments) exposes a major security concern: community skills are distributed under the `anthropic/` namespace, creating risks of trust boundary abuse. This has sparked discussions about namespace hygiene and permission models.

- **Enterprise & Organization Sharing:** Issue [#228](https://github.com/anthropics/skills/issues/228) (14 comments, 7 reactions) consistently demands a native mechanism for sharing skills within organizations, avoiding the current manual `.skill` file sharing process. This reflects a growing enterprise adoption base.

### 3. High-Potential Pending Skills

These PRs are not yet merged but have active discussions and are likely to land soon based on community and maintainer engagement:

- **Codebase Inventory & Audit:** PR [#147](https://github.com/anthropics/skills/pull/147) — A systematic 10-step workflow for identifying orphaned code and documentation gaps.
- **Persistent Agent Memory (shodh-memory):** PR [#154](https://github.com/anthropics/skills/pull/154) — A sophisticated pattern for maintaining context across AI agent conversations using a structured memory system.
- **Documentation & Contribution Standards:** PR [#95](https://github.com/anthropics/skills/pull/95) (System flowcharts) and PR [#509](https://github.com/anthropics/skills/pull/509) (CONTRIBUTING.md) — These are infrastructure PRs aimed at improving the repository’s health and on-boarding experience. PR #509 directly addresses the repo’s low community health score.

### 4. Skills Ecosystem Insight

**The community’s most concentrated demand is for a reliable, cross-platform skill development toolchain—specifically, the fix for the `run_eval.py` recall bug—before any new functional skill can be effectively validated or optimized.**

---

# Claude Code Community Digest — 2026-06-30

## Today's Highlights
A critical performance regression (#26224) affecting session throughput remains the community's top concern with 124 comments and 146 upvotes, persisting since February. On the positive side, v2.1.196 ships org-level model defaults and intelligible session naming—two long-requested quality-of-life improvements. The ecosystem sees growing friction around Cowork reliability on Windows and macOS, while a new wave of security-focused feature requests (PII redaction, opt-in training data contribution) signals maturing enterprise adoption concerns.

## Releases
**v2.1.196** (latest) — Two notable additions:
- **Org default model support**: Admins can now set organization-wide model defaults via the admin console. When a user hasn't explicitly chosen a model, `/model` displays "Org default" or "Role default" instead of forcing a selection.
- **Readable session names**: New sessions start with human-friendly default names, improving identification across multiple active sessions.

[View release](https://github.com/anthropics/claude-code/releases/tag/v2.1.196)

## Hot Issues

1. **[#26224 — Claude Code hanging/freezing on prompts for 5-20+ minutes](https://github.com/anthropics/claude-code/issues/26224)**  
   *Status: OPEN | Comments: 124 | 👍: 146*  
   The community's most-urgent bug. Sessions stall unpredictably for extended periods. 146 upvotes indicate widespread impact. Persistent since February without resolution—this is a top priority for team trust.

2. **[#20469 — Microsoft 365 Connector restricted from Max plan individual users](https://github.com/anthropics/claude-code/issues/20469)**  
   *Status: CLOSED | Comments: 58 | 👍: 62*  
   Controversial pricing gap: individual Max plan subscribers ($100-200/mo) cannot access M365 integration available to Team plan ($30/seat). 62 upvotes reflect significant frustration with tiered feature gating.

3. **[#48407 — Cowork tab missing in desktop app on Windows 11](https://github.com/anthropics/claude-code/issues/48407)**  
   *Status: OPEN | Comments: 35 | 👍: 16*  
   Core UI element missing entirely on Windows. Points to larger desktop app stability issues two months after initial report.

4. **[#69238 — No response from API error when Advisor is triggered](https://github.com/anthropics/claude-code/issues/69238)**  
   *Status: OPEN | Comments: 30 | 👍: 47*  
   Advisor triggers API connectivity failures even with functional base models. 47 upvotes signal broad annoyance. High-priority reliability concern.

5. **[#16128 — AWS Bedrock authentication support for Chrome extension](https://github.com/anthropics/claude-code/issues/16128)**  
   *Status: OPEN | Comments: 26 | 👍: 109*  
   Massive demand (109 upvotes) for enterprise cloud auth in the Chrome extension. Organizations blocked from using the extension with their Bedrock deployments.

6. **[#10258 — Cannot disable the buggy Interactive Question Tool](https://github.com/anthropics/claude-code/issues/10258)**  
   *Status: OPEN | Comments: 19 | 👍: 5*  
   No kill switch for a tool users find disruptive. Persistent since October 2025—a UX governance issue.

7. **[#23030 — Rate limit triggered before reaching session usage limit (71%)](https://github.com/anthropics/claude-code/issues/23030)**  
   *Status: OPEN | Comments: 10 | 👍: 13*  
   Max plan users hitting rate limits at 71% usage. Discrepancy between `/usage` reporting and actual throttling undermines trust in billing/usage transparency.

8. **[#67307 — Opus 4.8 malformed tool calls: stray tokens, missing `antml:` prefix](https://github.com/anthropics/claude-code/issues/67307)**  
   *Status: OPEN | Comments: 4 | 👍: 13*  
   Opus 4.8 intermittently emits malformed tool calls rendered as plain text, never executing. Critical for anyone using Opus as their primary reasoning model.

9. **[#72343 — Agent Teams: tmux/auto teammates crash on non-TTY stdin](https://github.com/anthropics/claude-code/issues/72343)**  
   *Status: OPEN | Comments: 3 | 👍: 0*  
   Fresh bug (filed yesterday). Agent Teams mode breaks inside tmux—spawned teammates die with `--print` errors. Critical blocker for terminal multiplexer users.

10. **[#71562 — `hasTrustDialogAccepted` never persisted to config](https://github.com/anthropics/claude-code/issues/71562)**  
    *Status: OPEN | Comments: 4 | 👍: 1*  
    Trust dialog acceptance not persisted across sessions on Linux. Reprompts indefinitely—minor but grating UX failure.

## Key PR Progress

1. **[#72363 — Gateway GCP example: Agent Platform rebrand and README cleanup](https://github.com/anthropics/claude-code/pull/72363)**  
   *Status: CLOSED*  
   Updates GCP deployment example prose to reflect Vertex AI → Agent Platform rebrand, maintaining backward searchability.

2. **[#72361 — Add Claude Gateway on GCP example deployment assets](https://github.com/anthropics/claude-code/pull/72361)**  
   *Status: CLOSED*  
   Publishes ready-to-use Terraform and script assets for Claude Gateway on Google Cloud, complementing existing docs. Aims to reduce deployment friction.

3. **[#72264 — docs: note Bash tool_input exposes additional fields](https://github.com/anthropics/claude-code/pull/72264)**  
   *Status: OPEN*  
   Documents that `Bash` tool payloads include `run_in_background`, `description`, and `timeout`—not just `command`. Prevents hook-writing surprises.

## Feature Request Trends

- **Agent observability gap**: Multiple requests (e.g., #72287) ask for per-subagent model/effort visibility in `/agents` UI and JSON output. Users need to debug agent swarm behavior without blocking the main loop.
- **Enterprise security posture**: Two new feature requests today (#72393, #72156) focus on opt-in PII-sanitized training data contribution and feedback redaction. Suggests growing enterprise compliance requirements.
- **Chrome extension parity**: Ongoing demand (#16128) for AWS Bedrock auth in Chrome extension. Extension continues to lag CLI/desktop in enterprise authentication support.
- **Conversation branching in IDE**: Request (#69272) to bring CLI's `/fork` command to VS Code extension. Power users want non-linear conversation management in their IDE.

## Developer Pain Points

- **Stability concerns dominate**: The persistent hanging bug (#26224) and Opus 4.8 malformed tool calls (#67307) erode confidence in core reliability. Both have high community engagement and long lifespans.
- **Rate limit transparency broken**: Users (#23030) report throttling at 71% session usage, contradicting displayed metrics. Billing/usage trust is fragile.
- **Cowork ecosystem fragility**: Windows users missing the Cowork tab (#48407), GitHub connector showing connected but exposing no tools (#61682), and empty Scheduled/Projects/Artifacts tabs (#71425) suggest the Cowork feature suffers from platform-specific bugs.
- **Plugin/marketplace directory corruption**: In-app plugin loader and CLI disagree on install paths (#71948), wiping marketplace directories on reload. Affects all plugins and MCP servers.
- **Session auto-compact not triggering**: Context compaction (#65379) fails after 80-100% usage, forcing manual intervention. Particularly impacts long-running IntelliJ sessions.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

# OpenAI Codex Community Digest — 2026-06-30

## Today's Highlights

Two pre-release versions landed today (rust-v0.142.4 and rust-v0.143.0-alpha.31), though both contain no user-facing changes. The community remains focused on systemic issues around quota accounting, excessive SSD write pressure from SQLite logging, and authentication deadlocks, with the top issue on token burning now at 626 comments. Security hardening continues to be a major theme in open PRs, particularly around Git command isolation and shell approval boundaries.

## Releases

Two versions were published in the last 24 hours:

- **rust-v0.142.4** — Chores only; no user-facing changes. [Changelog](https://github.com/openai/codex/compare/rust-v0.142.3...rust-v0.142.4)
- **rust-v0.143.0-alpha.31** — Pre-release alpha; changelog indicates "Release 0.143.0-alpha.31" with no further detail.

Omitted from detailed analysis as neither version introduces functional changes.

## Hot Issues

1. **[#14593 — "Burning tokens very fast"](https://github.com/openai/codex/issues/14593)**  
   *276 👍, 626 comments (highest engagement)* — A Business-tier VS Code user reports unusually fast token consumption that persists across updates. The extreme comment count suggests this is a widespread, unresolved pain point affecting many subscribers. Community speculation includes background model calls and misconfigured context windows.

2. **[#28224 — "Codex SQLite feedback logs can write ~640 TB/year"](https://github.com/openai/codex/issues/28224)**  
   *407 👍, 108 comments* — This issue documented catastrophic SSD wear from excessive SQLite logging. Three merged PRs (#29432, #29457, and another) reportedly reduced 85% of log volume. The author is closing the issue, but follow-up #29532 suggests the fix is incomplete on macOS.

3. **[#25749 — "Inaccessible legacy phone number verification"](https://github.com/openai/codex/issues/25749)**  
   *43 👍, 65 comments* — A user with Google OAuth + MFA on their OpenAI account is blocked from Codex because it demands SMS verification of a legacy phone number. No recovery path exists. This highlights a critical auth UX gap that can lock paying users out entirely.

4. **[#30224 — "X-OpenAI-Internal-Codex-Responses-Lite model not supported"](https://github.com/openai/codex/issues/30224)**  
   *20 👍, 59 comments* — Custom model users hitting API errors when using an internal header (`X-OpenAI-Internal-Codex-Responses-Lite`). Signals an undeclared API surface that breaks on certain model configurations.

5. **[#30002 — "Server-side quota over-reports consumption after 5h reset"](https://github.com/openai/codex/issues/30002)**  
   *6 👍, 29 comments* — Pro accounts hitting rate limits after only 41 minutes and ~1.35M tokens, while the same account earlier consumed ~156M tokens in a full 5h window. Suggests a server-side accounting bug that penalizes users unpredictably.

6. **[#29532 — "Persistent SQLite TRACE log churn on macOS after rust-v0.142.0"](https://github.com/openai/codex/issues/29532)**  
   *7 👍, 25 comments* — Even after the major fix in #28224, partial log spamming persists on macOS. The user identifies that PR #29457 did not fully address the root cause. Critical for Mac users concerned about SSD health.

7. **[#17827 — "Customizable status line"](https://github.com/openai/codex/issues/17827)**  
   *78 👍, 20 comments* — Feature request inspired by Claude Code's status line. Users want real-time visibility into token usage, model, rate limits, and git branch in the TUI. High community demand with low implementation complexity.

8. **[#25744 — "MCP helper processes and unreaped zombie children on macOS"](https://github.com/openai/codex/issues/25744)**  
   *3 👍, 10 comments* — Accumulated zombie processes from Computer Use / MCP helpers causing HID lag and WindowServer stalls. A system-level resource leak that degrades the entire macOS desktop experience.

9. **[#20570 — "Windows sandbox: CreateProcessAsUserW failed 1920"](https://github.com/openai/codex/issues/20570)**  
   *9 👍, 8 comments* — After upgrade to 0.128.0, Windows users hit sandbox runner errors. The 1920 error code (ERROR_CANNOT_IMPERSONATE) suggests an ACL or privilege regression in the Windows sandbox implementation.

10. **[#12498 — "Codex Cloud stops recognizing Git remote"](https://github.com/openai/codex/issues/12498)**  
    *5 👍, 9 comments* — Long-standing bug (since February 2026) where Codex Cloud loses Git remote awareness and only references a local 'work' workspace. Still open after four months — indicates either low priority or difficult root cause.

## Key PR Progress

1. **[#28714 — "Require approval for generic Git commands"](https://github.com/openai/codex/pull/28714)**  
   Tightens Git command classification after PSECOP-111 showed that argv-only "read-only" detection is unsafe. Repository config, TTY state, and attribute lookups can turn `git status` into a network operation.

2. **[#27914 — "Fail closed on executable Git worktree helpers"](https://github.com/openai/codex/pull/27914)**  
   Closes a supply-chain vector where Git worktree operations execute repository-selected content filters and merge drivers. Affects patch preflight, application, and revert flows.

3. **[#30645 — "Update safety notice wording"](https://github.com/openai/codex/pull/30645)**  
   Removes obsolete copy about Trusted Access for approved researchers in the TUI biosafety block. A cleanup PR reflecting policy changes in the safety notice system.

4. **[#30509 — "Allow review while MCP startup runs in background"](https://github.com/openai/codex/pull/30509)**  
   Decouples MCP initialization from foreground task state, allowing `/review` to open while servers start. Addresses a UX bottleneck where MCP startup blocked all interaction.

5. **[#30643 — "Bound Rendezvous WebSocket liveness"](https://github.com/openai/codex/pull/30643)**  
   Adds 60-second pong timeout and backpressure bounds for Noise Rendezvous WebSockets. Prevents silent executor disconnections from stalling sessions indefinitely.

6. **[#30642 — "Accept empty HTTP responses for MCP notifications"](https://github.com/openai/codex/pull/30642)**  
   Fixes a protocol compliance gap: MCP notifications can now accept empty 200 responses. Previously required a response body, which broke certain Streamable HTTP integrations.

7. **[#30516 — "Add explicit agent communication logging"](https://github.com/openai/codex/pull/30516)**  
   Adds structured TRACE-level logging under `codex_core::agent_communication` for mailbox enqueue and communication creation. Useful for debugging multi-agent flows.

8. **[#30315 — "Add generated token auth to app-server WebSockets"](https://github.com/openai/codex/pull/30315)**  
   Introduces 256-bit connection tokens for app-server WebSocket listeners, with a `--no-token-check` escape hatch. Strengthens local security for the desktop app's internal WebSocket surface.

9. **[#30618 — "fix(core): prevent tool-search rollout poisoning"](https://github.com/openai/codex/pull/30618)**  
   Fixes a critical durability bug: malformed `tool_search_call.arguments` from the Responses service could be persisted to rollouts, making sessions permanently unusable on resume. Prevents future occurrences.

10. **[#30632 — "perf: trace and reduce remote first-turn latency"](https://github.com/openai/codex/pull/30632)**  
    Adds W3C trace context propagation across Core, exec-server RPC, and the Noise relay. Removes several avoidable waits found during profiling, with stage-level spans for tool dispatch and RPC.

## Feature Request Trends

The following feature directions appear repeatedly across open issues and PRs:

1. **TUI customization** — Users want customizable status lines showing token usage, model, rate limits, and git state (#17827, multiple comments). Inspired by Claude Code's feature set.

2. **Background monitoring capabilities** — A call for an agent-callable `monitor` tool that wakes Codex on background events (logs, files, builds, CI) without polling (#29922). Users want Codex to react to system changes, not just turn-based input.

3. **Autoscroll controls** — Users request a setting to disable or control autoscroll behavior during long responses, especially for visual comfort (#23517, plus mentions in other threads).

4. **Sub-agent visibility** — After introducing sub-agents, users report difficulty managing and viewing them (#30237). Better sub-agent lifecycle management is a recurring ask.

5. **Self-hosted / offline reliability** — Issues around Git remote recognition (#12498), phone verification deadlocks (#25749), and sandbox failures (#20570) all point to demand for more resilient local-first operation.

## Developer Pain Points

**Quota and billing transparency** remains the #1 frustration. Multiple issues (#14593, #30002, #30641, #30525) report unexplained token consumption, incorrect quota resets, and a lack of visibility into what's consuming tokens. The 626-comment thread on token burning suggests OpenAI has not yet acknowledged the severity of this problem.

**Excessive SSD write pressure from logging** is the second most impactful issue. Even after partial fixes in v0.142.0, macOS and Windows users report ongoing SQLite write amplification (#29532, #29674). For developers on SSDs with limited endurance, this is a hardware risk.

**Windows sandbox and process management** is a consistent pain point: zombie processes (#25744), sandbox runner failures (#20570), locked executables during updates (#23320), and missing MCP servers (#26693, #30486). The Windows port continues to lag in reliability.

**Authentication deadlocks** — The inability to recover when a legacy phone number is inaccessible (#25749) is a critical blocker. Combined with VS Code Remote-SSH issues (#28427) and OAuth flows, auth reliability is degrading the developer experience across platforms.

**Git security hardening** — While the PR activity here is proactive, the volume of PRs addressing Git command execution risks (#28714, #27914, #28761, #28760, #29470) indicates that Codex's Git integration has multiple known supply-chain vulnerabilities that are actively being patched.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>

# Gemini CLI Community Digest — 2026-06-30

## Today's Highlights
Today's nightly `v0.51.0` release was published, continuing the rapid iteration cadence. Agent reliability remains the dominant theme, with ongoing work to fix subagent recovery false positives, hang conditions, and memory system bugs. Several critical PRs merged today address signal forwarding, URL sanitization, and subscription leaks in the VS Code companion.

---

## Releases
- **v0.51.0-nightly.20260630.gae0a3aa7b** — Automated nightly bump.  
  [Full Changelog](https://github.com/google-gemini/gemini-cli/compare/v0.51.0-nightly.20260629.gae0a3aa7b...v0.51.0-nightly.20260630.gae0a3aa7b)

---

## Hot Issues *(10 of 30+ updated today)*

1. **[#22323] Subagent recovery after MAX_TURNS reported as GOAL success**  
   `codebase_investigator` reports `status: "success"` / `Termination Reason: "GOAL"` even after hitting the max turn limit before any analysis. A dangerous false positive that undermines trust in subagent results. 8 comments.  
   [Issue](https://github.com/google-gemini/gemini-cli/issues/22323)

2. **[#24353] EPIC: Robust component level evaluations**  
   Follow-up to #15300 — 76 behavioral eval tests generated, now needing expansion across 6 supported Gemini models. Critical for CI gating. 7 comments.  
   [Issue](https://github.com/google-gemini/gemini-cli/issues/24353)

3. **[#22745] Assess AST-aware file reads, search, and mapping**  
   Investigating whether AST-aware tools reduce turns, token noise, and misaligned reads. Could significantly improve codebase_investigator quality. 7 comments.  
   [Issue](https://github.com/google-gemini/gemini-cli/issues/22745)

4. **[#21409] Generalist agent hangs forever**  
   Simple folder creation causes indefinite hang when agent defers to the generalist. Users forced to instruct model to avoid sub-agents entirely. 7 comments, 8 👍.  
   [Issue](https://github.com/google-gemini/gemini-cli/issues/21409)

5. **[#25166] Shell command execution stuck on "Awaiting input" after completion**  
   Extremely simple commands hang while UI shows them as active. High-frequency P1 affecting core workflow. 4 comments, 3 👍.  
   [Issue](https://github.com/google-gemini/gemini-cli/issues/25166)

6. **[#26525] Add deterministic redaction and reduce Auto Memory logging**  
   Auto Memory sends content to model context before redaction, and can log existing skills. Security/privacy concern for sensitive workspaces. 5 comments.  
   [Issue](https://github.com/google-gemini/gemini-cli/issues/26525)

7. **[#26522] Stop Auto Memory from retrying low-signal sessions indefinitely**  
   Low-signal sessions remain unprocessed and keep getting re-surfaced for extraction. Wastes model quota and CPU cycles. 5 comments.  
   [Issue](https://github.com/google-gemini/gemini-cli/issues/26522)

8. **[#21983] Browser subagent fails on Wayland**  
   Termination Reason: "GOAL" despite failure. Likely rendering pipeline incompatibility with Wayland compositors. 4 comments.  
   [Issue](https://github.com/google-gemini/gemini-cli/issues/21983)

9. **[#24246] 400 error with > 128 tools**  
   Agent loads all tools even when many are irrelevant; API rejects requests. Expect smarter tool scoping. 3 comments.  
   [Issue](https://github.com/google-gemini/gemini-cli/issues/24246)

10. **[#22186] "get-shit-done" output hook causes crash**  
    Crash during user summary printing — likely rendering or lifecycle race in the summary output hook. 3 comments.  
    [Issue](https://github.com/google-gemini/gemini-cli/issues/22186)

---

## Key PR Progress *(10 of 21 updated today)*

1. **[[MERGED] #27936] fix(vscode-ide-companion): add missing activate() Disposables**  
   Parentheses wrapping created comma expressions instead of separate push arguments, losing registrations.  
   [PR](https://github.com/google-gemini/gemini-cli/pull/27936)

2. **[[MERGED] #27942] fix(core): remove leading space in camelToSpace for capitalized keys**  
   Trailing `.trim()` applied only to `result.slice(1)`, so keys like "Id" produced " Id".  
   [PR](https://github.com/google-gemini/gemini-cli/pull/27942)

3. **[[OPEN] #28096] fix(core): drop late tool calls after SIGINT cancellation**  
   SIGINT during a turn could still execute a delayed tool call — the result gets submitted after user cancellation.  
   [PR](https://github.com/google-gemini/gemini-cli/pull/28096)

4. **[[OPEN] #28164] fix(core): limit recursive reasoning turns per single user request**  
   Hard limit of 15 recursive reasoning turns per request to protect CPU resources and API quotas from infinite loops.  
   [PR](https://github.com/google-gemini/gemini-cli/pull/28164)

5. **[[OPEN] #27971] fix(core): strip thoughts from scrubbed history turns**  
   Resolves "Thought Leakage" — model internal monologues leaking into plain-text history, causing infinite loops.  
   [PR](https://github.com/google-gemini/gemini-cli/pull/27971)

6. **[[OPEN] #28053] fix(core-tools): resolve defensive path resolution for @-reference files**  
   `read_file`/`replace`/`write_file` fail when model passes `@`-prefixed paths. Comprehensive fix with macOS test coverage.  
   [PR](https://github.com/google-gemini/gemini-cli/pull/28053)

7. **[[MERGED] #28215] Harden file-write scope: stop sandbox/auto-accept writes to .gemini and .gitconfig**  
   Auto-accept mode allowed agent to overwrite its own config — a sandbox escape vector under prompt injection.  
   [PR](https://github.com/google-gemini/gemini-cli/pull/28215)

8. **[[MERGED] #28200] fix: sanitize trailing periods from URLs in auth error messages**  
   Trailing `.` broke terminal hyperlink detection, making fix links unclickable.  
   [PR](https://github.com/google-gemini/gemini-cli/pull/28200)

9. **[[MERGED] #28202] fix: forward SIGINT/SIGTERM/SIGQUIT to child process during relaunch**  
   Ctrl+C during update killed the parent but left the child orphaned.  
   [PR](https://github.com/google-gemini/gemini-cli/pull/28202)

10. **[[MERGED] #28201] fix: remove double-wrapping of VS Code disposables causing subscription leak**  
    Second batch of VS Code disposable leak fixes — same comma-operator pattern as #27936.  
    [PR](https://github.com/google-gemini/gemini-cli/pull/28201)

---

## Feature Request Trends

| Theme | Count | Key Issues |
|---|---|---|
| **AST-aware code navigation** | 2 EPICs | #22745 — method-bound reads, #22746 — codebase mapping via tilth/glyph |
| **Subagent trajectory sharing** | 1 feature | #22598 — `/chat share` should include subagent traces for debugging |
| **Self-awareness & documentation** | 1 feature | #21432 — agent should know its own flags, hotkeys, and execution mechanics |
| **Browser agent resilience** | 1 feature | #22232 — session takeover, lock recovery for persistent browser profiles |
| **Component-level evaluations** | 1 EPIC | #24353 — standardize behavioral evals across all 6 Gemini model variants |

The strongest signal is the push for **AST-aware tools** to reduce turn count and token cost — two EPICs tracking pre-reading and codebase mapping improvements. There is also growing interest in **subagent visibility** (#22598) and **agent self-awareness** (#21432) as users struggle to debug opaque subagent behavior.

---

## Developer Pain Points

1. **Agent hangs / non-termination** — #21409 (generalist hang), #25166 (shell stuck on "Awaiting input"), #22186 (crash on summary)
2. **False success reporting** — #22323 (MAX_TURNS reported as GOAL), #21983 (browser agent fails but says GOAL)
3. **Subagent governance failures** — #22093 (subagents running despite being disabled), #21968 (subagents not used enough conversely)
4. **Auto Memory inefficiency** — #26522 (infinite retries on low-signal), #26525 (logging before redaction)
5. **Tool overload** — #24246 (400 error with >128 tools); model includes irrelevant tools, exhausting context
6. **VS Code companion instability** — #27945 (infinite sign-in loop), plus multiple PRs fixing leaked disposables (#27936, #28201)
7. **Configuration overrides ignored** — #22267 (browser agent ignores `settings.json` overrides like `maxTurns`)
8. **Destructive command execution** — #22672 (agent using `git reset --force` when safer alternatives exist)
9. **Tmp script pollution** — #23571 (model creating edit scripts across random directories, muddying commits)
10. **Signal handling** — SIGINT not forwarded during relaunch (#28202), late tool calls after cancellation (#28096)

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

# GitHub Copilot CLI Community Digest
**Date:** 2026-06-30

---

## Today's Highlights

A minor patch release (v1.0.66-2) shipped today, bringing long-awaited plugin coexistence for identically named skills and new LSP server logging capabilities. Meanwhile, the community continues to be frustrated by stuck Copilot Agent sessions and terminal rendering regressions, with several critical and high-upvoted issues still unaddressed.

---

## Releases

### v1.0.66-2
- **Added**
  - Allow skills with the same name from different plugins to coexist
  - Let integrations read and write CLI user settings
  - View LSP server logs in `/lsp logs` and `read_agent`
  - Prompt to install `gh` CLI when it is missing in GitHub repositories
  - Add GitHub attachment variants to prompt rendering

---

## Hot Issues (10 Noteworthy)

| # | Issue | Summary | Why It Matters | Community Reaction |
|---|-------|---------|----------------|-------------------|
| 1 | **[#1799](https://github.com/github/copilot-cli/issues/1799)** – How to turn off alt-screen views? | Users want a toggle to disable the new alt-screen terminal mode. | Breaking change for users who prefer the classic inline output; 7 upvotes with 10 comments signal broad impact. | ⚠️ Mixed – some see alt-screen as improvement, others as a blocker. |
| 2 | **[#2364](https://github.com/github/copilot-cli/issues/2364)** – [Critical] Copilot Agent session keeps running indefinitely | Agent sessions in org repos get stuck on the initial plan, never finishing. | Blocks enterprise workflows; no way to kill or reply to stuck sessions. | 🔴 High urgency – reported as critical by enterprise user. |
| 3 | **[#3909](https://github.com/github/copilot-cli/issues/3909)** – Feature: enterprise org server-managed settings | Org admins cannot push env variables to local CLI installs, only to Codespaces. | Enterprise adoption blocker; local CLI is increasingly important for hybrid dev setups. | 🟡 Low upvotes but strategically important for admins. |
| 4 | **[#3948](https://github.com/github/copilot-cli/issues/3948)** – `web_fetch` always fails with TypeError | `web_fetch` tool call fails on every URL despite working auth/proxy. | Core tooling broken for many users; reduces Copilot's ability to browse documentation. | 🟢 Active investigation – 2 comments, but no fix yet. |
| 5 | **[#3936](https://github.com/github/copilot-cli/issues/3936)** – Ctrl+G should expand paste tokens in $EDITOR | `compactPaste` collapsed pastes show literal tokens in editor; frustrates editing. | Quality-of-life regression vs Claude Code; parity expectation is strong. | 🟢 Positive engagement – clear feature parity ask. |
| 6 | **[#2654](https://github.com/github/copilot-cli/issues/2654)** – `session_store_sql` silently returns empty when sync is local | Agents can't tell cloud store is unavailable; gets empty results with no warning. | Misleading behavior leads agent to wrong conclusions; silent failure is dangerous for automated workflows. | 🟡 Low visibility but high risk if agents act on empty data. |
| 7 | **[#3957](https://github.com/github/copilot-cli/issues/3957)** – Unable to scroll through history on MBP trackpad | Trackpad scroll selects text instead of scrolling history in TUI. | 5 upvotes in 2 days; core navigation broken on MacBooks with Ghostty. | 🔴 Rapidly escalating – regression from v1.0.65. |
| 8 | **[#3958](https://github.com/github/copilot-cli/issues/3958)** – Windows: `.bat`/`.cmd` MCP servers fail to start | Regression in v1.0.66 for Windows MCP with batch files and args. | Blocks Windows MCP ecosystem; `cmd.exe` syntax error kills processes silently. | 🔴 Platform-specific regression with no workaround. |
| 9 | **[#3904](https://github.com/github/copilot-cli/issues/3904)** – CloudQueryError prevents `/chronicle standup` despite local fallback | Cloud session store error blocks feature even when local data exists. | Feature fragility; local vs cloud sync issues undermine trust in session persistence. | 🟡 Single report but touches core reliability. |
| 10 | **[#3962](https://github.com/github/copilot-cli/issues/3962)** – v1.0.65 not working at all | Blank output on startup with no error messages. | Full degradation; users cannot even see the prompt. | 🔴 Immediate attention needed – no comments yet, but affects basic usability. |

---

## Feature Request Trends

Based on the last 24 hours of issues, the most-requested feature directions are:

1. **Session Management & Organization**
   - [User-defined tags (searchable/filterable)](https://github.com/github/copilot-cli/issues/3970) – growing need to categorize sessions by project or workstream
   - [Plan status indicators on session list](https://github.com/github/copilot-cli/issues/3969) – visual badges to check progress at a glance
   - [Full file-tree browser for repository sessions](https://github.com/github/copilot-cli/issues/3971) – parity with folder-based sessions

2. **Enterprise Configuration Control**
   - [Org-managed settings/env for local CLI](https://github.com/github/copilot-cli/issues/3909) – push config centrally without relying on Codespaces

3. **Terminal & Input Ergonomics**
   - [Expand paste tokens in $EDITOR (Ctrl+G parity)](https://github.com/github/copilot-cli/issues/3936) – quality-of-life vs Claude Code
   - [Session retention/expiration visibility](https://github.com/github/copilot-cli/issues/3963) – users want to know when sessions will be wiped

4. **Plugin System Improvements**
   - [Warning when MCP servers share names across plugins](https://github.com/github/copilot-cli/issues/3893) – currently silently overwritten (addressed in v1.0.66-2)
   - [Git symlink support for plugin install on Windows](https://github.com/github/copilot-cli/issues/2286) – installs fail silently

---

## Developer Pain Points

| Category | Details |
|----------|---------|
| **Agent Session Stuck** | [#2364](https://github.com/github/copilot-cli/issues/2364), [#3600](https://github.com/github/copilot-cli/issues/3600) – Critical: sessions running for weeks/months with no kill switch. Enterprise users struggling. |
| **Terminal UI Regressions** | [#1799](https://github.com/github/copilot-cli/issues/1799) (alt-screen toggle), [#3957](https://github.com/github/copilot-cli/issues/3957) (trackpad scroll), [#3959](https://github.com/github/copilot-cli/issues/3959) (ghost characters on delete) – Multiple UI bugs in recent releases. |
| **Windows Bugs** | [#3958](https://github.com/github/copilot-cli/issues/3958) (MCP batch file regression), [#3973](https://github.com/github/copilot-cli/issues/3973) (MCP OAuth port conflict) – Windows ecosystem still fragile. |
| **Silent Failures** | [#2654](https://github.com/github/copilot-cli/issues/2654) (empty session store returns no error), [#3948](https://github.com/github/copilot-cli/issues/3948) (web_fetch fails silently) – Agents act on incorrect data. |
| **Startup & Installation** | [#3962](https://github.com/github/copilot-cli/issues/3962) (blank screen on v1.0.65), [#3967](https://github.com/github/copilot-cli/issues/3967) (vanished from Ubuntu) – Some users completely unable to launch. |
| **Billing & Quota Confusion** | [#2619](https://github.com/github/copilot-cli/issues/2619), [#2340](https://github.com/github/copilot-cli/issues/2340) – Users charged during trial or quota not resetting; support response times slow. |

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

# Kimi Code CLI Community Digest
**Date:** 2026-06-30  
**Data Source:** [github.com/MoonshotAI/kimi-cli](https://github.com/MoonshotAI/kimi-cli)

---

## 1. Today's Highlights
The repository saw a quiet day with no new releases or merged pull requests. Community attention is centered on a single open feature request (#2479) regarding poor Enter/Return key behavior, which highlights a growing frustration with mobile usability and desktop multiline input. No urgent bugs or security issues were reported, indicating a stable period for the CLI.

---

## 2. Releases
No new releases in the last 24 hours.

---

## 3. Hot Issues
*Only one issue was updated in the last 24 hours.*

| Issue | Title & Link | Why It Matters | Community Reaction |
|---|---|---|---|
| #2479 | [Bad usage of return and enter for desktop and mobile](https://github.com/MoonshotAI/kimi-cli/issues/2479) | Core UX pain point: mobile users cannot send prompts without accidental newlines, while desktop users cannot create new lines without Shift+Enter. This directly impacts daily workflow for both segments. | No engagement yet (0 comments, 0 👍). Likely a new submission. Expect significant traction given the universal friction described. |

---

## 4. Key PR Progress
No pull requests were updated in the last 24 hours.

_Note: For a comprehensive PR analysis, a longer time window (e.g., 7 days) is recommended._

---

## 5. Feature Request Trends
Based on the single open issue, the most demanded direction is:

- **Cross-platform input behavior refinement**  
  Users want the Enter key to behave contextually: send on mobile (single-line input), insert newline on desktop (multiline input), with an explicit send button or configurable shortcut. This is a classic "mode-switching" ergonomics request.

---

## 6. Developer Pain Points
- **Mobile CLI experience is broken** – pressing Enter sends prompt, making multi-line input or editing impossible on phones. No workaround mentioned.
- **Desktop multiline entry is non-obvious** – requiring `Shift+Enter` to insert a new line is counterintuitive for users accustomed to rich-text editors or chat interfaces.
- **No accessibility or customization** – users cannot rebind keys or choose between "Enter to send" and "Enter to newline" modes.

---

**Next Steps for Contributors:**  
- Engage on Issue #2479 to discuss mobile-friendly input modes (e.g., click-to-send button, configurable keybinding).  
- Consider a hotfix release that adds a `--multiline` flag or a `/send` slash command for mobile users.

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

# OpenCode Community Digest — 2026-06-30

## Today's Highlights
The community is experiencing two major stability pain points: a **Bun segmentation fault crash** on Windows in v1.17.10 (48 comments) and **excessive auto-compaction loops** that halt response generation entirely. A significant **architectural refactoring** push is underway, led by `jlongster`, to internalize service layers and remove `defaultLayer` exports — spanning several PRs. Meanwhile, the V2 TUI migration to the new `@opencode-ai/client` is being tracked, and the long-running **GPT models latency issue** (#29079) continues to dominate discussion with 118 comments.

## Hot Issues

1. **[#29079] GPT Models takes too long to respond** — 118 comments, 50 👍  
   Users report intermittent latency spikes (seconds to minutes) even for simple commands, specifically with GPT 5.4 xhigh. The high engagement suggests this is affecting a broad user base.  
   [GitHub](https://github.com/anomalyco/opencode/issue/29079)

2. **[#33742] OpenCode v1.17.10 crashes with Bun segmentation fault on Windows** — 48 comments, 46 👍  
   A critical regression requiring immediate attention. v1.17.9 is stable; v1.17.10 produces native Bun segfaults on Windows. High urgency.  
   [GitHub](https://github.com/anomalyco/opencode/issue/33742)

3. **[#5674] Custom OpenAI-compatible provider options not being passed to API calls** — 24 comments, 13 👍  
   `baseURL` and `apiKey` configured in `opencode.json` are silently ignored for custom providers. This has been open since December 2025 and continues to frustrate self-hosted users.  
   [GitHub](https://github.com/anomalyco/opencode/issue/5674)

4. **[#30680] OpenCode immediately enters auto-compaction loop and stops generating responses** — 10 comments  
   Even in an empty folder, the tool repeatedly auto-compacts, consuming tokens without producing responses. A fundamental workflow-blocking issue.  
   [GitHub](https://github.com/anomalyco/opencode/issue/30680)

5. **[#33998] GLM-5.2 prompt cache randomly drops to ~500 tokens on opencode-go** — 6 comments  
   Intermittent cache loss despite byte-identical system prompts over 36 calls. Cost-spiking behavior mirrors similar reports for GLM-5.1.  
   [GitHub](https://github.com/anomalyco/opencode/issue/33998)

6. **[#33696] GitHub Copilot provider broken** — 5 comments, 4 👍  
   After fresh auth flow, no models are found and the provider appears empty. Cache deletion does not resolve.  
   [GitHub](https://github.com/anomalyco/opencode/issue/33696)

7. **[#34537] Abnormal token consumption — overnight edit failures drained 80% of tokens** — 2 comments  
   A user reports an error, followed by repeated edit failures overnight consuming 80% of their token balance. A stark reminder of the cost of runaway retries.  
   [GitHub](https://github.com/anomalyco/opencode/issue/34537)

8. **[#34543] websearch connection failure with DeepSeek** — 2 comments  
   Native web search adaptor for DeepSeek fails with `Invalid schema for function 'web_search': schema must be a JSON Schema of type "object", got type "null"`.  
   [GitHub](https://github.com/anomalyco/opencode/issue/34543)

9. **[#34532] Persistent red status dot after tool-loader failure; only clean reinstall cleared it** — 2 comments  
   On macOS, a broken custom tool under the global tools directory leaves a persistent red status dot. Fixing the tool errors unblocks messaging, but the red dot remains until full reinstall.  
   [GitHub](https://github.com/anomalyco/opencode/issue/34532)

10. **[#25755] Temperature not sent in request body for custom OpenAI-compatible provider** — 1 comment  
    The `temperature` parameter configured in agent frontmatter or `opencode.json` is never included in the API request. Verified via tcpdump.  
    [GitHub](https://github.com/anomalyco/opencode/issue/25755)

## Key PR Progress

1. **[#34547] fix(ui): prevent tool status blank frame** — *Merged*  
   Fixes a flash of blank content during tool status transitions by syncing `data-active` before measuring the target width.  
   [GitHub](https://github.com/anomalyco/opencode/pull/34547)

2. **[#34533] fix(app): stabilize session timeline layout continuity** — *Open*  
   Addresses layout jank during streaming, resizing, virtualized rows, and disclosure state changes. Preserves bottom anchoring and scroll positions.  
   [GitHub](https://github.com/anomalyco/opencode/pull/34533)

3. **[#34531] feat(core): support MCP prompts** — *Open*  
   Exposes MCP prompt definitions and `getPrompt` through the core MCP client wrapper with stable sorting across connected servers.  
   [GitHub](https://github.com/anomalyco/opencode/pull/34531)

4. **[#34540] fix(session): replace throw error with logWarning during summary generation** — *Open*  
   Prevents summary generation from crashing when tool calls are attempted. Replaces a hard throw with a warning log. Closes #23709 and #24123.  
   [GitHub](https://github.com/anomalyco/opencode/pull/34540)

5. **[#34538] fix(provider): forward agent temperature for config-defined custom models** — *Open*  
   Defaults `temperature` capability to enabled for config-defined custom models, fixing a common pain point for self-hosted providers.  
   [GitHub](https://github.com/anomalyco/opencode/pull/34538)

6. **[#34517] refactor(opencode): remove app service layer exports** — *Open*  
   Internalizes service implementation layers behind exported nodes, reducing the public surface. Part of a broader `defaultLayer` elimination effort.  
   [GitHub](https://github.com/anomalyco/opencode/pull/34517)

7. **[#34516] refactor(opencode): use layer nodes in remaining harnesses** — *Open*  
   Converts remaining test harnesses to `AppNodeBuilder`/`LayerNode` graphs, completing the migration away from direct layer exports.  
   [GitHub](https://github.com/anomalyco/opencode/pull/34516)

8. **[#34519] refactor(opencode): keep plugin pty environment route local** — *Open*  
   Moves PTY environment provider into a route-local scope, removing a redundant generic provider.  
   [GitHub](https://github.com/anomalyco/opencode/pull/34519)

9. **[#33523] feat: Add LLM and session observability hooks** — *Open*  
   Adds four observability hooks to the plugin SDK, enabling plugins to observe the real LLM stream, tool execution, and agent-run data.  
   [GitHub](https://github.com/anomalyco/opencode/pull/33523)

10. **[#34060] feat(provider): add free model resolution for `--model free`** — *Open*  
    Introduces `--model free` for `opencode run` and TUI, which picks a random zero-cost model from OpenCode Zen.  
    [GitHub](https://github.com/anomalyco/opencode/pull/34060)

## Feature Request Trends
- **Session-scoped context contributions** (#34380): Embedders need app-owned context attached to sessions — not global agent identity or user transcript text. A new “keyed context” primitive is being proposed.
- **`disable-model-invocation` support in SKILL.md frontmatter** (#11972, #34498): Multiple requests mirroring Claude Code’s ability to prevent skills from calling models — a clear parity demand from the community.
- **Workspace/tool lifecycle hooks** (#15680): Plugins want to react to worktree create/remove/reset events, enabling automatic test database setup and similar workflows.
- **Total cost display for sessions** (#4925): Users want accumulated token cost including sub-agent usage, not just primary agent tokens.
- **LaTeX rendering in TUI** (#11655): Heavily upvoted (27 👍) request for proper mathematical notation display in the terminal UI.
- **V2 TUI migration tracking** (#34359): The official issue for moving the V2 TUI from legacy SDK to the new generated Promise client.
- **V2 config update endpoints** (#34450): Users need a way to programmatically update OpenCode configuration via API.

## Developer Pain Points
- **Runaway costs**: Issues #34537 (80% token loss overnight) and #30680 (auto-compaction loop) both describe scenarios where the tool consumes tokens without producing useful results — a critical trust issue.
- **Provider-specific regressions**: Multiple reports of broken providers (GitHub Copilot #33696, GLM cache drops #33998/#31348, DeepSeek websearch #34543) suggest testing gaps before releases.
- **Configuration options silently ignored**: The persistent `temperature` (#25755) and custom provider options (#5674) bugs show that user-configured parameters are not reliably forwarded to API calls — a fundamental correctness issue.
- **Windows stability**: The Bun segfault in v1.17.10 (#33742) and the general note that "Bun 1.3.14 segfaults lots on Windows" (PR #33822) point to platform-specific runtime fragility.
- **Filesystem notification delays**: Issue #34545 reports that generated files cannot be `@`-mentioned until OpenCode is restarted — a UX disruption for iterative workflows.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>

# Pi Community Digest — 2026-06-30

## Today's Highlights

A major wave of bug fixes landed this week addressing provider error transparency, stream recovery, and scroll behavior. The community is actively contributing provider integrations (Scaleway, Kimi), and the first package reports signal growing ecosystem vigilance. Three in-progress efforts target Anthropic OAuth flexibility, Xiaomi pricing corrections, and compaction summary localization.

## Releases

No new releases in the last 24 hours. Latest stable remains v0.80.x (with noted regression in Cloudflare Workers.AI on v0.80.1, see Issue #6021).

---

## Hot Issues

### 1. [#5825 — Streaming markdown forces scroll to bottom](https://github.com/earendil-works/pi/issues/5825) *(42 comments, CLOSED)*
Users with `clear on shrink` enabled experience aggressive auto-scrolling mid-stream, breaking read-along. A dedicated PR (#6026) aims to stabilize the status row. High engagement signals this is a common UX pain point.

### 2. [#4877 — Session folder collision](https://github.com/earendil-works/pi/issues/4877) *(20 comments, CLOSED)*
Different directory paths (e.g., `/a/b/c/d` vs `/a-b/c-d`) hash to the same session folder name due to path normalization. Root cause is in session storage logic. Community reaction is neutral but noted as a latent footgun.

### 3. [#6083 — LLM cache not working with z.ai GLM](https://github.com/earendil-works/pi/issues/6083) *(8 comments, CLOSED, 👍9)*
Multi-step tasks burn 10–20% session limit per turn because context caching fails for the GLM Coding Plan provider. High upvote count indicates many users are affected. No action taken yet beyond acknowledgment.

### 4. [#5871 — Anthropic OAuth detection hardcoded](https://github.com/earendil-works/pi/issues/5871) *(6 comments, OPEN, inprogress)*
The `isOAuthToken()` check only matches `sk-ant-oat` prefix, breaking scoped Anthropic API keys that look like regular keys (`sk-ant-api03-...`). Community is actively discussing a configurable OAuth token pattern.

### 5. [#5763 — Providers swallow HTTP error bodies](https://github.com/earendil-works/pi/issues/5763) *(5 comments, CLOSED)*
Gateway/proxy errors are opaque: Bedrock returns `Unknown: UnknownError`, OpenAI returns `403 status code (no body)`. Fix in PR #5832 surfaces the actual body, improving debugging for enterprise deployments.

### 6. [#6158 — Repeated tool calls loop without interruption](https://github.com/earendil-works/pi/issues/6158) *(3 comments, CLOSED)*
Agent loops on directory inspection commands (e.g., `ls` 6× in a row) instead of progressing to next action. This appears to be a model-specific issue rather than a core loop bug, but signals need for loop detection.

### 7. [#6124 — Devnagri text breaks harness UI](https://github.com/earendil-works/pi/issues/6124) *(3 comments, OPEN)*
Typing `नेटवर्क` corrupts the TUI display. Unicode rendering bug in the terminal component. Low engagement but significant for internationalization.

### 8. [#6138 — Incorrect pricing for Xiaomi MiMo models](https://github.com/earendil-works/pi/issues/6138) *(3 comments, OPEN, inprogress)*
Hardcoded prices in `xiaomi.models.js` don't match official MiMo pay-as-you-go pricing. Community is compiling corrected rate tables. Impact: users overpaying for cache reads.

### 9. [#6019 — OpenAI mid-stream retryable error not retried](https://github.com/earendil-works/pi/issues/6019) *(5 comments, CLOSED)*
When OpenAI returns a retryable error mid-response, Pi finalizes the message with `stopReason: "error"` instead of retrying. This contradicts OpenAI's own documentation and wastes tokens.

### 10. [#6157 — Compaction summary should be in session's language](https://github.com/earendil-works/pi/issues/6157) *(2 comments, OPEN)*
Non-English conversations get English compaction summaries. Feature request to localize `## Goal`/`## Progress` headers and the summary body to the session language. Low activity but resonates with international users.

---

## Key PR Progress

### 1. [#6170 — Avoid replaying historical inline images](https://github.com/earendil-works/pi/pull/6170) *(CLOSED)*
Stops replaying terminal image escape payloads when rebuilding historical session context. Live tool results still render images; history falls back to `[Image: ...]` labels. Prevents context bloat from large base64 images.

### 2. [#6169 — Disable padding for assistant messages](https://github.com/earendil-works/pi/pull/6169) *(OPEN)*
Adds a config option to remove padding around TUI assistant messages. Addresses zero-padding scope creep from #3454. Author `xl0` is a power user contributing consistently.

### 3. [#6051 — Recover from hung streams and retry unmodeled Bedrock errors](https://github.com/earendil-works/pi/pull/6051) *(CLOSED)*
Adds idle timeout (240s default) and connect timeout for Bedrock streams. Retries unmodeled errors instead of hanging indefinitely. Critical for Bedrock users in production.

### 4. [#5832 — Surface provider HTTP error body instead of opaque SDK message](https://github.com/earendil-works/pi/pull/5832) *(CLOSED)*
Fixes #5763. Drops error body swallowing for all providers. Now shows the actual HTTP response body (e.g., "403 - Rate limit exceeded") instead of opaque SDK wrappers.

### 5. [#6026 — Stabilize working status row](https://github.com/earendil-works/pi/pull/6026) *(CLOSED)*
Stabilizes the TUI status row during streaming, preventing scroll-to-bottom jumps. Fix for #5825. Community-requested fix after weeks of complaints.

### 6. [#6161 — Map Bedrock apiKey auth to bearer token env](https://github.com/earendil-works/pi/pull/6161) *(CLOSED)*
Maps Bedrock `apiKey` to `env.AWS_BEARER_TOKEN_BEDROCK` for Converse API, prevents double-forwarding of the same token. Required for OAuth-based Bedrock auth flows.

### 7. [#6156 — Return empty string for empty tool results](https://github.com/earendil-works/pi/pull/6156) *(CLOSED)*
Fixes OpenAI Responses/Completions handlers returning `(see attached image)` when tool result is text-only with no images. The confusion cost models tokens parsing nonexistent images.

### 8. [#5832 (cross-reference) — Body surfacing also improves Anthropic OAuth errors](https://github.com/earendil-works/pi/pull/5832)
The error body fix in #5832 also helps with OAuth debugging, making it easier to diagnose `sk-ant-oat` vs. scoped key mismatches.

### 9. [#6026 (cross-reference) — TUI stability reduces duplicate scroll reports](https://github.com/earendil-works/pi/pull/6026)
Expected to close duplicate scroll-related issues once merged. Community eagerly awaiting release.

### 10. [#6170 (cross-reference) — Image replay suppression reduces compaction overhead](https://github.com/earendil-works/pi/pull/6170)
Will reduce context window pressure by 10-30% for heavy-image sessions, directly addressing the 90k char thinking block issue (#6166).

---

## Feature Request Trends

1. **Provider Expansion & Flexibility**  
   - Scaleway Generative APIs (#6165), Kimi Coding provider fixes (#6164)  
   - Configurable OAuth token pattern for Anthropic instead of hardcoded prefix (#5871)

2. **Enterprise & Admin Features**  
   - `/etc` or `%ProgramData%` admin config overrides (#6159)  
   - `--profile` flag for per-project isolated state (#3966) — closed but conceptually active via community forks

3. **Non-English & I18N**  
   - Devnagri text rendering (#6124)  
   - Compaction summaries in session language (#6157)  
   - Unicode-aware padding/alignment

4. **Agent Control Enhancements**  
   - Steering messages that don't wake the agent (#5895)  
   - Expose `navigateTree()` on ExtensionContext for custom agent commands (#5932)

5. **Pricing & Cost Transparency**  
   - Hardcoded model pricing corrections (Xiaomi MiMo #6138, MiniMax M3 #6171)  
   - Mid-stream retryable error handling to avoid wasted tokens (#6019)

---

## Developer Pain Points

1. **Provider Error Opacity** — Multiple issues (#5763, #6019, #6133) highlight how HTTP errors, mid-stream failures, and rate limits produce cryptic or empty error messages. PR #5832 addresses this but not all providers are covered yet.

2. **OAuth/API Key Confusion** — The hardcoded `sk-ant-oat` check (#5871) breaks scoped Anthropic keys and creates a brittle auth system. Community wants a declarative API key type configuration.

3. **Stream Stability** — Scroll jumps (#5825), hung streams (#6051), ECONNRESET crashes (#6133), and missing retries (#6019) collectively make streaming unreliable under load.

4. **Context Window Inefficiency** — Large thinking blocks (#6166), historical image replay (#6170), and failed compaction caching (#6083) waste context tokens in long sessions.

5. **Package Ecosystem Trust** — Three package reports this week (#6155, #6154, #6153) flag dead repos, missing sources, and potential impersonation. Community is actively policing npm packages but needs better verification tooling.

6. **Scoped Key Handling** — Scoped Anthropic (#6093) and Bedrock OAuth (#6163) issues reveal that the provider auth layer doesn't gracefully handle non-standard key formats, forcing users into manual workarounds.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>

Here is the **Qwen Code Community Digest** for **2026-06-30**, based on the latest GitHub activity.

---

## Qwen Code Community Digest — 2026-06-30

### Today's Highlights
The project sees heavy community activity despite a partial release failure. Key focuses include **daemon reliability** (cold start latency, channel management), **subagent output sanitization**, and **platform-specific bug fixes** for Windows and Linux. A new autonomous mode for the `/loop` command is in active development, alongside a major push for **mobile web-shell UX** and **TLS support** for the `serve` command.

### Releases
- **[v0.19.3-nightly.20260630.e00fe6a27](https://github.com/QwenLM/qwen-code/releases/tag/v0.19.3-nightly.20260630.e00fe6a27)**: A nightly release with updated daemon documentation (Wave 2) and the beginning of a configurable auto- feature (PR #5954). Note: The previous nightly build (`v0.19.3-nightly.20260629`) failed due to integration Docker issues (Issue [#5969]).

### Hot Issues (Top 10)

1. **#401** **[Streaming setup timeout](https://github.com/QwenLM/qwen-code/issues/401)** — A long-standing bug where CLI users hit a 6-second timeout for streaming setup. The fix requires either reducing input length or increasing the configured timeout. High engagement (12 comments) suggests this is a common first-run frustration.

2. **#6004** **[MCP installation crash on MacOS](https://github.com/QwenLM/qwen-code/issues/6004)** — Installing MCP servers (`dsphper/lanhu-mcp`) causes the CLI to crash with a memory allocation failure (Scavenge). This is a high-priority MacOS/performance bug with a `welcome-pr` tag.

3. **#4748** **[Optimize daemon cold start latency](https://github.com/QwenLM/qwen-code/issues/4748)** — A performance enhancement aiming to reduce daemon cold start from 2.5s to ~1.5s. This is critical for users who frequently restart or use `qwen serve` in CI/CD pipelines.

4. **#5975** **[No stream activity for 120s](https://github.com/QwenLM/qwen-code/issues/5975)** — A regression in v0.19.3 causing the CLI to timeout after 19 chunks (2 minutes) during long streaming outputs. The community reports it is blocking heavy editing workflows.

5. **#5941** **[Scroll wheel jumps to top](https://github.com/QwenLM/qwen-code/issues/5941)** — On Windows, scrolling up during model output instantly jumps to the top of the conversation, making it impossible to read context during generation. A high-impact UI/UX bug.

6. **#5942** **[Anthropic prompt-cache misses](https://github.com/QwenLM/qwen-code/issues/5942)** — A costly performance bug. When using Anthropic backends, qwen-code fails to maintain prompt cache hits, dramatically increasing token costs compared to competitors like Claude Code. Community is tracking this for cost optimization.

7. **#6007** **[GLM-5.2 leaks thinking text](https://github.com/QwenLM/qwen-code/issues/6007)** — When using the `glm-5.2` model, internal reasoning tags (`<think>`/`</think>`) leak into the final output. This is a model-switching bug that breaks user-facing output formatting.

8. **#6030** **[Windows tilde path resolution](https://github.com/QwenLM/qwen-code/issues/6030)** — A file-operations bug where Windows users typing `~\docs` get the literal `~` character instead of resolving to the home directory. This breaks all home-relative path commands on Windows.

9. **#5971** **[TUI scroll refresh on Linux](https://github.com/QwenLM/qwen-code/issues/5971)** — A Linux-specific rendering bug where the TUI continuously re-scrolls from the beginning of the conversation during long outputs, rendering the terminal unusable.

10. **#6030** **[Exclude line numbers from clipboard](https://github.com/QwenLM/qwen-code/issues/6024)** — A quality-of-life request to strip gutter line numbers when copying code blocks from the TUI. Currently, copying includes numbers like `1 import React`, requiring manual cleanup.

### Key PR Progress (Top 10)

1. **[#6027](https://github.com/QwenLM/qwen-code/pull/6027)** — **Sanitize subagent result tags**: Fixes the leakage of internal XML tags (`<analysis>`, `<summary>`) into parent agent context and the daemon UI. Critical for maintaining a clean user experience in subagent workflows.

2. **[#6026](https://github.com/QwenLM/qwen-code/pull/6026)** — **Allow subagents to exit plan mode**: Fixes a state-management bug where subagents were stuck in plan mode even after `exit_plan_mode` succeeded. Unblocks multi-agent editing workflows.

3. **[#6031](https://github.com/QwenLM/qwen-code/pull/6031)** — **Daemon-managed channel worker**: Implements the core PR2 architecture for `qwen serve --channel`, allowing the daemon to spawn and manage out-of-process channel workers (DingTalk, Feishu, etc.). A major step toward background automation.

4. **[#6029](https://github.com/QwenLM/qwen-code/pull/6029)** — **Fix Windows tilde paths**: Resolves the path resolution bug for Windows backslash-separated tilde paths, bringing feature parity with POSIX behavior.

5. **[#6011](https://github.com/QwenLM/qwen-code/pull/6011)** — **Mouse support in TUI**: Adds mouse click and hover interactions to the alternate-screen mode. Enables clickable menus, dialogs, and permission prompts without keyboard navigation.

6. **[#6003](https://github.com/QwenLM/qwen-code/pull/6003)** — **Mobile sidebar drawer**: Replaces the hidden sidebar on mobile with an overlay drawer pattern. Unlocks session switching on mobile browsers for `qwen serve` web UI.

7. **[#5957](https://github.com/QwenLM/qwen-code/pull/5957)** — **Fix compression thresholds with escalated max_tokens**: Prevents API 400 errors by correctly subtracting reserved output tokens from the context window before computing compression thresholds.

8. **[#5998](https://github.com/QwenLM/qwen-code/pull/5998)** — **Structure DingTalk stream logs**: Replaces raw binary dumps with human-readable structured logs for DingTalk channel debugging. A win for maintainers managing multi-channel deployments.

9. **[#5999](https://github.com/QwenLM/qwen-code/pull/5999)** — **Emoji cleanup**: Completes the migration from width-2 emoji to width-1 Unicode text symbols across all TUI rendering paths, fixing alignment and rendering glitches.

10. **[#5991](https://github.com/QwenLM/qwen-code/pull/5991)** — **Autonomous loop mode**: A bare `/loop` now enters a self-paced autonomous mode, allowing the agent to continuously work on tasks (e.g., fixing flaky CI) without a predefined prompt or interval.

### Feature Request Trends

- **Background Automation (Roadmap)**: A clear trend toward "set and forget" capabilities. Multiple requests target autonomous loop modes ([#5990](https://github.com/QwenLM/qwen-code/issues/5990)), daemon-managed channel workers ([#5976](https://github.com/QwenLM/qwen-code/issues/5976), [#6010](https://github.com/QwenLM/qwen-code/issues/6010)), and background task execution.
- **Mobile & Web Shell**: Several requests focus on making `qwen serve` a first-class web application, including mobile responsive UIs ([#6000](https://github.com/QwenLM/qwen-code/issues/6000)), HTTPS/TLS support ([#6001](https://github.com/QwenLM/qwen-code/issues/6001)), and prompt queuing ([#6025](https://github.com/QwenLM/qwen-code/pull/6025)).
- **Hot-Reload System**: Issue [#3696](https://github.com/QwenLM/qwen-code/issues/3696) tracks the partial implementation of a comprehensive hot-reload system, with ongoing work for skills, MCP, and configuration changes without session restart.
- **Configurable Compaction Model**: A feature request ([#5956](https://github.com/QwenLM/qwen-code/issues/5956)) to allow using a cheaper/separate model for conversation compression, reducing cost and preserving context window space for the active model.
- **Inline Model Switching**: Users want inline model overrides ([#5967](https://github.com/QwenLM/qwen-code/issues/5967)) via `/model <id> <prompt>` for single-query model comparisons.

### Developer Pain Points

1. **Platform-Specific Terminal Rendering**: Windows (scroll jump, tilde paths) and Linux (scroll refresh) users report significant UI regressions. The TUI is clearly a high-priority area with ongoing, post-release fixes.
2. **Streaming Reliability**: Issues [#401](https://github.com/QwenLM/qwen-code/issues/401) and [#5975](https://github.com/QwenLM/qwen-code/issues/5975) indicate that streaming is a fragile subsystem. Timeouts and inactivity errors are common, especially after model-switching or with long inputs.
3. **Model & Provider Incompatibilities**: The project's support for many providers (Anthropic, GLM, OpenAI) leads to backend-specific bugs (prompt cache misses, thinking tag leaks). Developers are frustrated by inconsistent behavior between providers.
4. **Context Window Mismanagement**: Auto-compression is failing for users with escalated `max_tokens`, leading to API rejections. Coupled with subagent tag leaks consuming context, this creates a brittle experience for long sessions.
5. **No Safe Mode**: Despite a closed feature request ([#4883](https://github.com/QwenLM/qwen-code/issues/4883)), the lack of a `--safe-mode` flag remains a pain. Users troubleshooting crashes or rendering bugs have no clean-slate fallback for diagnostics.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>

Here is the **DeepSeek TUI (CodeWhale) Community Digest** for **2026-06-30**.

---

## 1. Today's Highlights
The **v0.8.66 release** is in active finalization, with a heavy focus on fixing fanout-induced UI freezes (the "multi sub-agent" freeze) and systemic YOLO mode approval overrides. A **torrent of 20+ high-priority PRs** merged in the last 24 hours target sub-agent lock contention and TUI text overflow, while the community continues to vocally demand fixes for poor input cache hit ratios (down to ~30%) compared to competitors.

## 2. Releases
No new releases in the last 24 hours. The community is currently orbiting **v0.8.66**, which is being gated by several blocking fixes (see #3800 cluster).

## 3. Hot Issues
1. **#1177 – 输入缓存命中率太低了**  
   *Severe frustration: cache hit ratio is far behind DeepSeek-Reasonix (95%+).*  
   User demands immediate improvement. 24 comments. [Link](https://github.com/Hmbown/CodeWhale/issues/1177)

2. **#1120 – Some problems with cache hits**  
   Community is confused about whether the `input_cache_miss` bug is fixed in v0.8.17. 21 comments. [Link](https://github.com/Hmbown/CodeWhale/issues/1120)

3. **#743 – Token消耗增大了很多**  
   *Half-day burn of 400M tokens* – users report excessive request density and poor interaction optimization. 13 comments. [Link](https://github.com/Hmbown/CodeWhale/issues/743)

4. **#3800 – v0.8.66: Release gate for multi sub-agent fanout freeze**  
   *Blocking the release.* The UI appears frozen during 20+ concurrent agent launches. 2 comments (but high PR activity). [Link](https://github.com/Hmbown/CodeWhale/issues/3800)

5. **#3819 – MCP OAuth authentication UX issues**  
   *Fresh today.* Stale tokens not auto-refreshing, silent errors, and foreground login timeouts. 1 comment. [Link](https://github.com/Hmbown/CodeWhale/issues/3819)

6. **#3799 – Fix TUI modal and text overflow layout systemically**  
   Bottom action rows clipped, long labels overflow. Affects the destructive approval modal. 1 comment. [Link](https://github.com/Hmbown/CodeWhale/issues/3799)

7. **#1512 – Mouse scroll wheel only shows my posts, not model output**  
   Introduced in v0.8.68. Basic scrolling UX is broken. 3 comments. [Link](https://github.com/Hmbown/CodeWhale/issues/1512)

8. **#1641 – Agent mode: add fallback strategy when tool calls fail**  
   Agents keep retrying the same tool instead of switching to alternatives when web search/API fails. 3 comments. [Link](https://github.com/Hmbown/CodeWhale/issues/1641)

9. **#1425 – 大文本处理工程后会话中断卡死**  
   *Russian novel analysis (~3M characters) kills the session.* Agent spawns 10 sub-agents, then `agent_wait` times out. 1 comment. [Link](https://github.com/Hmbown/CodeWhale/issues/1425)

10. **#2117 – Multi-skills: group skills manager**  
    Request to load multiple skills at once instead of individually. 1 comment. [Link](https://github.com/Hmbown/CodeWhale/issues/2117)

## 4. Key PR Progress
1. **#3820 – Sync Xiaomi MiMo Token Plan docs**  
   Adds Xiaomi MiMo v2.5 Pro UltraSpeed direct model support and Singapore/China/Amsterdam endpoints. [PR](https://github.com/Hmbown/CodeWhale/pull/3820)

2. **#3814 – Fix TUI: keep approval controls visible inline (#3799)**  
   *Critical UI fix.* Renders approval prompts as a compact card instead of a wrapping paragraph that clips controls on short terminals. *Merged.* [PR](https://github.com/Hmbown/CodeWhale/pull/3814)

3. **#3813 – Use nonblocking send for ListSubAgents refresh events (#3802)**  
   Prevents engine/TUI event loop stalls by using `try_send()` instead of blocking `.send().await` during status storms. *Merged.* [PR](https://github.com/Hmbown/CodeWhale/pull/3813)

4. **#3812 – Allow agent starts to join parallel dispatch batches (#3801)**  
   Fixes serialization of concurrent `agent` tool calls (now supports parallel dispatch for high fanout). *Merged.* [PR](https://github.com/Hmbown/CodeWhale/pull/3812)

5. **#3817 – Preserve standing YOLO authority for runtime continuations**  
   *Critical fix.* YOLO mode was losing its authority during force-push/PR-create actions from sub-agent handoffs. *Merged.* [PR](https://github.com/Hmbown/CodeWhale/pull/3817)

6. **#3815 – Hide Hotbar until explicit opt-in (#3807)**  
   Fresh installs no longer show Hotbar by default (kept as a config option). *Merged.* [PR](https://github.com/Hmbown/CodeWhale/pull/3815)

7. **#3816 – Persist sub-agent state off the manager write-lock hot path**  
   Splits JSON file I/O out of the write-lock to avoid contention during high fanout. *Merged.* [PR](https://github.com/Hmbown/CodeWhale/pull/3816)

8. **#3809 – Render sub-agent sidebar from a read-only snapshot (#3803)**  
   Eliminates write-lock contention on every UI refresh tick. *Merged.* [PR](https://github.com/Hmbown/CodeWhale/pull/3809)

9. **#3808 – try_lock shell manager in async UI refresh paths (#3804)**  
   Replaces blocking `std::sync::Mutex::lock()` with `try_lock()` to prevent render stalls. *Merged.* [PR](https://github.com/Hmbown/CodeWhale/pull/3808)

10. **#3789 – Show safety policy in /status**  
    Adds a Safety row to `/status` showing the current sandbox/network posture per mode (Plan=read-only, YOLO=unsandboxed). [PR](https://github.com/Hmbown/CodeWhale/pull/3789)

## 5. Feature Request Trends
- **Cache hit ratio parity** – The most aggressive demand: users want DeepSeek-Reasonix-level 95%+ cache hits (vs. current low/unknown ratio). See #1177, #1120, #1747.
- **Hotbar as a discoverable UI surface** – Epic #3389 explores an 8-slot MMO-style quick action bar, but directionally it is now hidden by default with explicit opt-in (#3807).
- **Multi-model provider UI** – Issue #2300 tracks Fleet loadout auto-selection and cleaner provider docs for vLLM/OpenAI endpoints.
- **Agent fallback strategies** – #1641 wants agents to degrade gracefully when external services fail (e.g., switch to web search alternative instead of retrying indefinitely).
- **Persistent permission rules** – #1186 proposes typed rules (tool name, command prefix, path pattern) with allow/deny/ask decisions.

## 6. Developer Pain Points
- **Poor input cache hit ratio** – Dominant Chinese/English sentiment that CodeWhale's cache is an order of magnitude worse than alternatives, leading to higher costs and slower runs (#1177, #1120).
- **Excessive token consumption** – Developers report 400M+ token burn in half a day due to overly dense request patterns, lack of smart caching, and bloated base prompts (#743, #1818).
- **TUI blocking and freezing** – Under high sub-agent fanout (10–20 concurrent agents), the UI becomes unresponsive. The current fix cluster (#3800-3809) specifically addresses this but it is still a painful "release blocker."
- **YOLO mode inconsistency** – Several PRs (#3790, #3817) had to repeatedly fix approval prompts firing even in YOLO mode. The root cause was an override in `auto_review`’s `safety_floor` that escaped mode authority.
- **Text overflow / layout clipping** – The modal and scrolling surfaces (#3799, #1512) are described as "destructive" to workflows because key content disappears below the visible frame.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*