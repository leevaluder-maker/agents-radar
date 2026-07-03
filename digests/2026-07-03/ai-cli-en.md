# AI CLI Tools Community Digest 2026-07-03

> Generated: 2026-07-03 02:01 UTC | Tools covered: 9

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

# AI CLI Tools Ecosystem — Cross-Tool Comparison Report
**Date:** 2026-07-03

---

## 1. Ecosystem Overview

The AI CLI developer tools landscape on July 3, 2026 is characterized by **intense competition across eight major tools**, with distinct differentiation in target audiences, architectural philosophies, and community maturity. **Claude Code** and **OpenCode** remain the most heavily trafficked repositories due to their large user bases and correspondingly high issue volumes, while **Gemini CLI** and **Pi** demonstrate the fastest iteration velocity as they race to close feature gaps. A recurring pattern across all tools is the tension between **agent autonomy and user control**, manifesting in debates around session limits, timeout policies, and sub-agent orchestration transparency. **Windows compatibility** remains the single weakest link across the ecosystem, with every tool except DeepSeek TUI reporting platform-specific rendering, authentication, or sandbox failures. The emergence of **multi-agent hierarchies**, **MCP (Model Context Protocol) integration**, and **local model inference backends** as shared priorities signals a mature phase where tools are no longer proving concept viability but are instead optimizing for production-scale, enterprise-grade workflows.

---

## 2. Activity Comparison

| Tool | Open Issues | Recent PRs (24h) | Release Status (24h) | Community Engagement |
|---|---|---|---|---|
| **Claude Code** | ~50 active (top 10 shown) | 4 PRs | v2.1.199 (patch) | Very High — 789 comments on #38335 alone |
| **OpenAI Codex** | 30 active | 10 PRs (12 security) | rust-v0.143.0-alpha.34 (alpha) | High — 680 👍 on Linux desktop request |
| **Gemini CLI** | 10 hot issues | 10 PRs | v0.51.0-nightly (nightly) | High — rapid iteration visible |
| **GitHub Copilot CLI** | ~10 hot | 2 PRs (stub/spam) | No release | Moderate — frustration signals |
| **Kimi Code CLI** | 10 hot | 10 PRs | No release | Moderate — low maintainer response |
| **OpenCode** | 50 new/updated | 10 PRs | No new release (v1.17.13) | Very High — 50 new issues, 20 PRs |
| **Pi** | 25+ closed today | 12 PRs | No new release (v0.80.3) | High — major bug-fix wave |
| **Qwen Code** | 10 hot | 10 PRs | v0.19.5 + nightly | Moderate-High — active Chinese community |
| **DeepSeek TUI** | 10 hot | 10 PRs (9 closed) | No release (v0.8.67 cycle) | Moderate — focused Windows/reliability |

**Key observations:**
- **Claude Code** and **OpenCode** dominate in raw community volume (hundreds of comments per issue).
- **Gemini CLI**, **Pi**, and **Qwen Code** show the highest PR throughput relative to issue counts — strong maintainer velocity.
- **Kimi Code CLI** and **GitHub Copilot CLI** show signs of **maintainer bottleneck** — high community engagement but low maintainer response on issues.
- **DeepSeek TUI** focuses on quality (9 of 10 PRs closed) rather than quantity.

---

## 3. Shared Feature Directions

### Emerging as Industry-wide Requirements

| Feature Direction | Tools Requesting | Specific Needs |
|---|---|---|
| **Configurable auto-resolve timeout** | Claude Code, OpenAI Codex, Gemini CLI, Copilot CLI | 60-second default is universally criticized as too aggressive; users want user-controllable timeouts (30s–300s+). |
| **Sub-agent / multi-agent orchestration transparency** | Claude Code (#69824, #69212), Gemini CLI (#22323), Qwen Code (#6189), DeepSeek TUI (#3932) | Nested sub-agents not awaiting results, false success reports on MAX_TURNS, missing model-routing vocabulary. Users want hierarchical agent trees and deterministic delegation. |
| **MCP server integration & compliance** | Copilot CLI (#4006, #4014), Gemini CLI (#27979), Pi (#6236) | Pagination not followed, terminal rendering breaks on MCP add, untrusted output wrapping needed. MCP spec compliance is inconsistent across tools. |
| **Local model / offline inference** | Kimi Code CLI (#1099), OpenCode (#33126), Qwen Code (via providers) | Demand for Ollama, llama.cpp, and local DeepSeek backends. Privacy and air-gap requirements drive this. |
| **Windows platform stability** | All tools except DeepSeek TUI (which reports Windows issues) | Scroll wheel regressions (Claude), silent exits (Codex), sandbox gaps (Gemini), non-UTF-8 code pages (Qwen), IME deadlocks (DeepSeek). Windows is the weakest platform. |
| **Persistent thinking / reasoning display** | Claude Code (#8477), Qwen Code (#6175), Pi (#4909) | Auto-collapsing chain-of-thought frustrates power users; they want permanent, toggleable visibility. |
| **Session history & state persistence** | Claude Code, Pi (SQLite storage), Qwen Code (todosDirectory), DeepSeek TUI (sidebar) | Queryable session logs, project-local task state, team-shared memory directories. |
| **Custom model endpoints / BYOK** | Copilot CLI (#4003, #4012), OpenCode (Go models), Pi (catalog expansion) | Enterprise users want private model endpoints; CLI parity with VS Code's model configuration is a gap. |
| **Slash commands / skill ecosystem** | Claude Code (#10238), DeepSeek TUI (#1887-1897), Kimi Code CLI (#1048) | Hierarchical skill organization, auto-updating skills, documented slash command infrastructure. |
| **Rate-limit / usage accounting accuracy** | Claude Code (#38335), OpenAI Codex (#30918), OpenCode (#35035) | Users report 3–5x faster session consumption, abnormal drain, and billing locks. Trust in usage metering erodes. |

---

## 4. Differentiation Analysis

### Feature Focus

| Tool | Primary Focus | Target User | Key Differentiator |
|---|---|---|---|
| **Claude Code** | Agentic coding, multi-skill orchestration | Power developers, enterprise teams | Deep skills system, sub-agent architecture, Claude model chain-of-thought depth |
| **OpenAI Codex** | Desktop + CLI hybrid, Git security | Professional developers, Windows users | Strongest Git sandboxing (12 security PRs), Rust-based alpha, desktop app |
| **Gemini CLI** | Multi-agent hierarchy, caretaker infrastructure | Google Cloud ecosystem, agent-heavy teams | Auto Memory, ACP (Agent Communication Protocol), AST-aware tooling roadmap |
| **GitHub Copilot CLI** | VS Code ecosystem integration, MCP-first | VS Code users migrating to CLI | Tightest GitHub Copilot integration, BYOK support |
| **Kimi Code CLI** | Cross-platform shell integration, watch mode | Chinese developer ecosystem | Kimi model optimization, Tailscale/VPN support, BracketedPaste fixes |
| **OpenCode** | Multi-model provider, Go subscription | Price-sensitive developers, multi-model users | DeepSeek V4 price advantage, Zen API, model switching flexibility |
| **Pi** | Extensibility, provider agnosticism | Plugin/extension developers | Inline extension API, SQLite session storage, DeepInfra provider |
| **Qwen Code** | Daemon/channel automation, mobile web-shell | Multi-channel enterprises, Chinese market | WeCom/DingTalk adapters, `/schedule` daemon, mobile session sync |
| **DeepSeek TUI** | Fleet orchestration, constitution system | TUI purists, security-conscious users | Fleet sub-agent pool, guided constitution creator, rules auto-discovery |

### Technical Approach

- **Claude Code** and **Gemini CLI** invest heavily in **agent hierarchy and reasoning transparency**, with sub-agent trees and chain-of-thought visibility.
- **OpenAI Codex** and **Pi** prioritize **sandbox security and provider flexibility** — Codex with Git hardening, Pi with provider-agnostic architecture.
- **Qwen Code** and **DeepSeek TUI** lead in **multi-channel and local-first design** — Qwen for enterprise channels, DeepSeek for Fleet orchestration.
- **GitHub Copilot CLI** and **Kimi Code CLI** are more **ecosystem-contingent**, relying on GitHub/MoonshotAI infrastructure rather than building independent agent platforms.

---

## 5. Community Momentum & Maturity

### High Momentum (Rapidly Iterating)

- **Gemini CLI**: Nightly releases, 10 PRs/day, active architectural changes (caretaker, ACP, AST). Highest velocity-to-community-size ratio.
- **Pi**: Major bug-fix wave (25+ issues closed in 24h), 12 PRs, addressing deep reasoning model incompatibilities. Turning corner on reliability.
- **Qwen Code**: Two releases in 24h, nightly improvements, expanding channel ecosystem. Strong maintainer responsiveness.

### Mature & High-Volume (Stable but Heavy Community Load)

- **Claude Code**: Most active community (789 comments on top issue) but single bug (#38335) dominates sentiment. Release cadence has slowed (v2.1.x patches).
- **OpenCode**: Very high community engagement (50 new issues/day) but Go subscription outages signal growing pains. Mature feature set with active refactoring.

### Plateau or Strained

- **OpenAI Codex**: Security hardening is active but community feature requests (Linux desktop, 680 👍) remain unaddressed. Rust alpha suggests architectural shift.
- **GitHub Copilot CLI**: Only 2 PRs (both non-functional), no releases. Community frustration with scrollbar bug (#3501, 9 👍) and model availability (#3997). Appears understaffed.

### Dual-Speed Development

- **DeepSeek TUI**: Excellent PR closure rate (9/10 closed) but issue count growing on Windows stability. Fleet feature set is ambitious but fragile (15+ GB memory reports).
- **Kimi Code CLI**: 10 PRs open but maintainer response is low on long-standing bugs (#640 since January). Community patience wearing thin.

---

## 6. Trend Signals

### For Technical Decision-Makers

1. **Session limit trust is eroding across the ecosystem.** Claude Code (#38335), OpenAI Codex (#30918), and OpenCode (#35035) all report abnormal consumption or billing locks. **Vendor lock-in risk increases** as users cannot rely on usage metering accuracy. Recommendation: **demand transparent, real-time usage dashboards** before committing to a plan.

2. **Multi-agent orchestration is the next battleground.** Every major tool is investing in sub-agent hierarchies (Gemini's caretaker, Claude's sub-agent tree, Qwen's nested depth, DeepSeek's Fleet). **Winner will be the tool that makes agent delegation transparent and debuggable**, not just functional. Current state: all tools have fragility in this area.

3. **Windows remains a second-class platform.** Across all tools, Windows users report scroll wheel regressions, silent crashes, IME deadlocks, code-page encoding issues, and authentication hangs. **If your team is Windows-heavy, expect 2–3x the bug exposure** compared to macOS/Linux. DeepSeek TUI has the most Windows-specific fixes but still struggles.

4. **MCP integration is fragmented.** Copilot CLI ignores pagination, Gemini wraps untrusted output, Kimi lacks tool discovery. **No tool has a mature, spec-compliant MCP implementation.** This is a gap to watch — MCP adoption will accelerate as agents rely more on external tools.

5. **Local inference demand is real and growing.** Kimi Code CLI (#1099), OpenCode (#33126), and Pi's DeepSeek V4 fixes all point to users wanting offline-capable tools. **Privacy and air-gapped requirements are no longer niche** — tools that embrace local models (Qwen, Pi) will capture enterprise trust.

6. **Battery/power efficiency matters more than GPU utilization.** OpenAI Codex's GPU animation issue (#16857) and TUI overhead reports across tools show that developers care deeply about resource consumption on laptops. **Thin-client TUI design is a competitive advantage.**

7. **Configuration persistence and session continuity are unsolved.** Auth not persisting across sessions (Qwen), theme forgotten on restart (Copilot), and session logs not queryable (most tools) create daily friction. **Tools that solve session portability** (Pi's SQLite storage, Qwen's todosDirectory) will differentiate.

8. **The Chinese developer ecosystem is an independent force.** Qwen Code's WeCom adapter, DeepSeek TUI's Taobao mirror lag, and Kimi Code's Tailscale/VPN focus show that **Chinese tools are optimizing for different infrastructure realities** — enterprise WeChat instead of Slack, local mirrors instead of npm, different VPN patterns. Global tools that ignore these patterns will lose the Chinese market.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)

# Claude Code Skills Community Highlights Report
*Data as of 2026-07-03 | Source: github.com/anthropics/skills*

---

## 1. Top Skills Ranking

The following PRs have attracted the most community discussion and attention:

### #514 — Document Typography Skill *(Open)*
- **Author:** PGTBoos | **Comments:** High | **Updated:** 2026-03-13
- **Summary:** Prevents orphan word wrap, widow paragraphs, and numbering misalignment in AI-generated documents — issues "every document Claude generates" faces.
- **Discussion highlights:** Community validation of a universal pain point; users report this fills an obvious gap in document-quality tooling.
- **Status:** Open, active discussion
- **Link:** [PR #514](https://github.com/anthropics/skills/pull/514)

### #486 — ODT Skill (OpenDocument Format) *(Open)*
- **Author:** GitHubNewbie0 | **Updated:** 2026-04-14
- **Summary:** Enables creation, filling, reading, and conversion of `.odt`/`.ods`/`.odf` files — LibreOffice/ISO-standard document format support.
- **Discussion highlights:** Strong demand from enterprise users who require ODF compliance; complements the existing DOCX skill.
- **Status:** Open, awaiting review
- **Link:** [PR #486](https://github.com/anthropics/skills/pull/486)

### #210 — Frontend-Design Skill Clarity & Actionability *(Open)*
- **Author:** justinwetch | **Updated:** 2026-03-07
- **Summary:** Major revision ensuring every instruction is "something Claude can actually follow within a single conversation," with specific behavior-steering guidance.
- **Discussion highlights:** Community critique of existing skill verbosity; push toward operational rather than educational content.
- **Status:** Open
- **Link:** [PR #210](https://github.com/anthropics/skills/pull/210)

### #83 — Skill-Quality-Analyzer & Skill-Security-Analyzer *(Open)*
- **Author:** eovidiu | **Updated:** 2026-01-07
- **Summary:** Two meta-skills: one evaluates skill quality across five dimensions (structure, documentation, testability, security, safety); the other audits for prompt injection, data exfiltration, and privilege escalation.
- **Discussion highlights:** Meta-tooling demand — community wants assurance before deploying community skills in production.
- **Status:** Open
- **Link:** [PR #83](https://github.com/anthropics/skills/pull/83)

### #1367 — Self-Audit Skill (v1.3.0) *(Open)*
- **Author:** YuhaoLin2005 | **Created:** 2026-06-28 | **Updated:** 2026-07-02
- **Summary:** Mechanical file verification + four-dimension reasoning audit before delivery. Universally applicable across projects and models.
- **Discussion highlights:** Very recent, rapidly updated; positions for production-grade output validation.
- **Status:** Open, active development
- **Link:** [PR #1367](https://github.com/anthropics/skills/pull/1367)

### #723 — Testing-Patterns Skill *(Open)*
- **Author:** 4444J99 | **Updated:** 2026-04-21
- **Summary:** Comprehensive coverage: testing philosophy (Trophy model), unit testing (AAA pattern), React component testing (Testing Library), integration testing, E2E, and what NOT to test.
- **Discussion highlights:** Community consensus that this fills a critical gap — no existing skill covers the full testing stack.
- **Status:** Open
- **Link:** [PR #723](https://github.com/anthropics/skills/pull/723)

### #806 — Sensory Skill (macOS AppleScript Automation) *(Open)*
- **Author:** AdelElo13 | **Updated:** 2026-04-02
- **Summary:** Teaches Claude to use `osascript` for native macOS automation instead of screenshot-based computer use. Two-tier permission system.
- **Discussion highlights:** Alternative to brittle vision-based automation; macOS power-user demand.
- **Status:** Open
- **Link:** [PR #806](https://github.com/anthropics/skills/pull/806)

---

## 2. Community Demand Trends

From Issues activity, the most-anticipated new Skill directions cluster around:

| Demand Area | Key Issue | Signal |
|---|---|---|
| **Security & Trust Boundary** | [#492](https://github.com/anthropics/skills/issues/492) — *Community skills under `anthropic/` namespace enable trust abuse* (34 comments, 2 👍) | **Highest-comment issue.** Community fears namespace impersonation; demand for skill provenance verification and sandboxing. |
| **Org-Wide Skill Sharing** | [#228](https://github.com/anthropics/skills/issues/228) — *Enable org-wide skill sharing in Claude.ai* (14 comments, 7 👍) | Enterprise deployment blocker. Users want shared skill libraries, not file-based distribution. |
| **Agent Governance & Safety** | [#412](https://github.com/anthropics/skills/issues/412) — *Skill proposal: agent-governance* (6 comments) | Policy enforcement, threat detection, trust scoring — missing from current collection. |
| **Compact Agent Memory** | [#1329](https://github.com/anthropics/skills/issues/1329) — *compact-memory skill proposal* (8 comments) | Long-running agents waste context on verbose notes; demand for symbolic notation. |
| **Duplicate Skill Bundles** | [#189](https://github.com/anthropics/skills/issues/189) — *document-skills and example-skills install identical content* (6 comments, 9 👍) | **Highest 👍 count.** Complaints that plugin bundles overlap, wasting context window. |

**Notable:** The `run_eval.py` bug cluster ([#556](https://github.com/anthropics/skills/issues/556), [#1169](https://github.com/anthropics/skills/issues/1169), [#1061](https://github.com/anthropics/skills/issues/1061), [#492](https://github.com/anthropics/skills/issues/492)) generates 22+ cumulative comments — the skill-creator tooling reliability is the community's most vocal pain point.

---

## 3. High-Potential Pending Skills

These PRs have active discussion and may land soon:

### #1298 — Fix `run_eval.py` Recall Bug *(Open, 2026-06-10)*
- **Author:** MartinCajiao
- **What:** Fixes the critical `recall=0%` bug in the skill evaluation pipeline. Installs eval artifact as real skill; fixes Windows stream reading, trigger detection, and parallel workers.
- **Why it matters:** Unblocks the entire skill-creator optimization loop for all community members.
- **Link:** [PR #1298](https://github.com/anthropics/skills/pull/1298)

### #1323 — `run_eval` Trigger Detection Fix *(Open, 2026-06-16)*
- **Author:** Polluelo978
- **What:** Fixes `run_single_query` failing to detect skill trigger events when the actual skill name differs from what the evaluator checks.
- **Why it matters:** Complementary fix to #1298; together they would resolve the `recall=0%` epidemic.
- **Link:** [PR #1323](https://github.com/anthropics/skills/pull/1323)

### #1367 — Self-Audit Skill (v1.3.0) *(Open, 2026-06-28)*
- **Author:** YuhaoLin2005
- **What:** Mechanical file verification + four-dimension reasoning audit. Latest iteration incorporates community feedback rapidly.
- **Why it matters:** Production-readiness validation — high demand from enterprise users.
- **Link:** [PR #1367](https://github.com/anthropics/skills/pull/1367)

### #509 — CONTRIBUTING.md Documentation *(Open, 2026-03-03)*
- **Author:** narenkatakam
- **What:** Adds five-section contributing guide addressing the repo's 25% community health score.
- **Why it matters:** Low friction to merge; resolves structural barrier to community contributions.
- **Link:** [PR #509](https://github.com/anthropics/skills/pull/509)

### #1302 — Color-Expert Skill *(Open, 2026-06-10)*
- **Author:** meodai
- **What:** Self-contained color expertise covering naming systems (ISCC-NBS, Munsell, XKCD, RAL), color spaces (OKLCH, OKLAB, CAM16), and accessibility.
- **Why it matters:** Niche but high-quality; appeals to design and data-visualization communities.
- **Link:** [PR #1302](https://github.com/anthropics/skills/pull/1302)

---

## 4. Skills Ecosystem Insight

**The community's most concentrated demand at the Skills level is *tooling reliability and safety* — the top three discussion threads are all about fixing the skill-creator evaluation pipeline (PRs #1298, #1323, #1099) and mitigating trust-boundary risks (Issue #492), outpacing demand for any individual skill feature.**

This reflects a maturing ecosystem: contributors first want the skill-creation tooling to work correctly, and second want assurance that community-submitted skills are safe to run — before they invest in building or adopting new domain-specific skills like typography, testing, or document conversion.

---

# Claude Code Community Digest — 2026-07-03

## Today's Highlights

A new patch release (v2.1.199) landed with fixes for stacked slash-skill invocations and SSL certificate error handling. The community remains highly focused on session limit exhaustion under Claude Max plans (Issue #38335, with 789 comments and counting), while a cluster of newly filed bugs around the `AskUserQuestion` tool auto-dismissing after 60 seconds has emerged as a critical UX regression. Sub-agent result routing and orphaned "working" spinners continue to be recurring themes.

## Releases

**v2.1.199** — [Full Release Notes](https://github.com/anthropics/claude-code/releases/tag/v2.1.199)
- **Stacked Slash-Skill Invocations**: Commands like `/skill-a /skill-b do XYZ` now load up to 5 leading skills, rather than only the first.
- **SSL Certificate Error Handling**: Fixed a bug where TLS-inspecting proxies, missing `NODE_EXTRA_CA_CERTS`, and expired certificates would burn retry cycles before surfacing actionable guidance. The tool now fails fast with a clear error message.

## Hot Issues

1. **[#38335] Claude Max plan session limits exhausted abnormally fast since March 23, 2026** — 789 comments, 467 👍  
   *Link: [Issue #38335](https://github.com/anthropics/claude-code/issues/38335)*  
   The single most active issue. Users report burning through session caps at 3–5x the expected rate since a March backend change. Anthropic has acknowledged the bug but no ETA on a fix. Community frustration is high, with users questioning billing accuracy.

2. **[#8477] Feature Request: Always Show Claude's Thinking** — 86 comments, 307 👍  
   *Link: [Issue #8477](https://github.com/anthropics/claude-code/issues/8477)*  
   Persistent request for a toggle to keep the "thinking" reveal panel permanently open. The v2.0.0 UI change made thinking auto-collapse, and power users want it back.

3. **[#73125] AskUserQuestion: "No response after 60s — continued without an answer"** — 62 comments, 219 👍  
   *Link: [Issue #73125](https://github.com/anthropics/claude-code/issues/73125)*  
   Critical UX regression: the tool auto-dismisses after 60 seconds, even while the user is actively typing. Filed just yesterday but already heavily upvoted.

4. **[#10238] Add support for subdirectories in skills** — 46 comments, 162 👍  
   *Link: [Issue #10238](https://github.com/anthropics/claude-code/issues/10238)*  
   Organizations building skill libraries want hierarchical organization. Currently, all skills must be flat in the skills directory, making large setups unmanageable.

5. **[#65833] v2.1.150: Scroll wheel sends arrow keys instead of scrolling conversation** — 29 comments, 53 👍  
   *Link: [Issue #65833](https://github.com/anthropics/claude-code/issues/65833)*  
   A regression on WSL that breaks mouse scroll in the TUI. The scroll wheel now cycles through command history instead of scrolling output.

6. **[#10621] Require double ESC in Vim mode to clear message in Plan Mode Q&A** — 20 comments, 26 👍  
   *Link: [Issue #10621](https://github.com/anthropics/claude-code/issues/10621)*  
   Vim mode users lose messages with a single ESC press. Request for a double-ESC guard to prevent accidental data loss.

7. **[#69824] Subagents not awaiting nested subagent results** — 6 comments, 0 👍  
   *Link: [Issue #69824](https://github.com/anthropics/claude-code/issues/69824)*  
   Subagents spawn nested agents but do not await their results, leading to duplicate work and fabricated notifications. A systemic problem in the agent orchestration layer.

8. **[#72639] Opus 4.8 (1M) stream hangs after first chunk since v2.1.154** — 4 comments, 0 👍  
   *Link: [Issue #72639](https://github.com/anthropics/claude-code/issues/72639)*  
   Streaming regression for Opus 4.8 model users. First chunk arrives, then the stream freezes. v2.1.153 is the last known good version.

9. **[#73490] AskUserQuestion auto-dismisses while user is mid-answer** — 5 comments, 9 👍  
   *Link: [Issue #73490](https://github.com/anthropics/claude-code/issues/73490)*  
   Related to #73125. A second report of the same 60-second timeout bug, this time from macOS. Users lose partial input during multi-question design prompts.

10. **[#69212] Subagent results route to root teammate instead of spawning teammate** — 3 comments, 2 👍  
    *Link: [Issue #69212](https://github.com/anthropics/claude-code/issues/69212)*  
    When a teammate spawns a subagent, the result goes to the root agent, breaking delegation workflows.

## Key PR Progress

1. **[#72451] Remove statsig.anthropic.com from init-firewall.sh**  
   *Link: [PR #72451](https://github.com/anthropics/claude-code/pull/72451)*  
   Fixes devcontainer startup failures because `statsig.anthropic.com` no longer resolves. Core infrastructure fix for development environments.

2. **[#73476] docs: fix GitHub capitalization in README**  
   *Link: [PR #73476](https://github.com/anthropics/claude-code/pull/73476)*  
   Minor documentation fix correcting "Github" to "GitHub" in the README.

3. **[#72866] docs: fix Github -> GitHub typo in README**  
   *Link: [PR #72866](https://github.com/anthropics/claude-code/pull/72866)*  
   A second, independent PR fixing the same typo. Indicates review backlog — minor doc fixes are accumulating without merging.

4. **[#72543] Create Cha**  
   *Link: [PR #72543](https://github.com/anthropics/claude-code/pull/72543)*  
   PR with no summary or description. Likely spam or an incomplete submission; no code changes apparent.

## Feature Request Trends

- **Persistent Thinking Display**: The most-upvoted feature request (#8477) demands a setting to keep Claude's chain-of-thought always visible, especially after v2.0.0 made it auto-collapsing.
- **Skill Subdirectory Support**: (#10238) Users want hierarchical skill organization for large teams — a clear sign the skill system is being adopted at enterprise scale.
- **Auto-Updating Plugins/Skills at Session Start**: (#73681) Users want skills refreshed automatically on launch rather than during sessions, which burns tokens and derails conversations.
- **Keyboard Shortcuts for Split-View Focus**: (#73679) Desktop users want `Cmd+[` or similar to switch focus between side-by-side session panes.
- **Double-ESC Guard in Vim Mode**: (#10621) Vim mode needs a deliberate action (double ESC) before clearing input, mirroring standard Vim behavior.

## Developer Pain Points

- **Session Limit Exhaustion**: The #38335 issue dominates community attention. Users on Claude Max plans report their session limits are consumed at 3–5x the expected rate. This is the single biggest pain point — it has billing, reliability, and productivity implications.
- **AskUserQuestion Auto-Dismiss Bug**: Two related issues (#73125, #73490) filed in the last 48 hours document a 60-second timeout that fires even when the user is actively typing. This is a critical regression that makes interactive multi-step workflows unreliable.
- **Sub-Agent Coordination Failures**: Multiple bugs (#69824, #69212, #73400, #73267) point to systemic problems in the agent hierarchy — results routed to wrong agents, nested subagents not awaited, completed agents still showing "running" spinners. The sub-agent system feels fragile under real-world workloads.
- **False Positive Content Flagging**: (#61625, #73680) Users report legitimate security and code analysis queries being flagged by Anthropic's usage policy classifier, with opaque error messages and no clear appeal path.
- **Streaming/Model Regressions**: (#72639) Opus 4.8 streaming broke between v2.1.153 and v2.1.154, forcing users to pin an older version. Combined with rate-limiting errors (#73660, #73509), model reliability is a growing concern.
- **TUI Scroll Regression on WSL**: (#65833) The scroll wheel bug has been open for nearly a month with no fix, disrupting a core navigation pattern for WSL users.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

# Codex Community Digest — 2026-07-03

## Today’s Highlights
A major security-hardening PR series from **bookholt-oai** dominated the repository today, with 12 pull requests targeting Git sandboxing and executable trust boundaries. Community attention remains focused on the long-running demand for a **Linux desktop app** (Issue #11023, 680 👍) and a critical **SQLite logging write amplification** bug (Issue #28224, 419 👍) that is now substantially resolved. The release of `rust-v0.143.0-alpha.34` brings new alpha channel changes.

## Releases
- **rust-v0.143.0-alpha.34**: Alpha release with no changelog details provided.

---

## Hot Issues (10 selected from 30 active)

1. **[#11023 — Codex desktop app for Linux](https://github.com/openai/codex/issues/11023)** – 139 comments, 680 👍  
   *Community demand for a native Linux desktop app remains the highest-signaled feature request. The workaround is the CLI, but power users on Linux lack GPU acceleration and persistent agent sessions.*
2. **[#28224 — SQLite feedback logs write 640 TB/year](https://github.com/openai/codex/issues/28224)** – 129 comments, 419 👍  
   *Three merged PRs cut log volume by ~85%, but the issue remains open for remaining edge cases. SSD endurance on developers’ machines was a real concern.*
3. **[#13041 — WebSocket upgrade then 1008 policy close](https://github.com/openai/codex/issues/13041)** – 74 comments, 161 👍  
   *Connection reliability on Linux: WebSocket upgrades succeed, then the server immediately closes with policy code 1008, forcing HTTPS fallback and degraded latency.*
4. **[#8648 — Replies to earlier messages instead of latest](https://github.com/openai/codex/issues/8648)** – 73 comments, 55 👍  
   *Multi-turn conversation regression: the assistant skips recent context and responds to old messages, breaking long agent workflows.*
5. **[#16857 — High GPU usage from tiny animation](https://github.com/openai/codex/issues/16857)** – 37 comments, 39 👍  
   *A trivial “thinking” animation in the desktop app drives continuous GPU activity on Apple Silicon, draining battery during idle thinking.*
6. **[#20214 — Freezes/stutters on Windows 11](https://github.com/openai/codex/issues/20214)** – 23 comments, 39 👍  
   *Despite sufficient RAM and CPU, the Windows desktop app exhibits frequent UI freezes. Windows stability is a recurring theme.*
7. **[#29193 — node_repl/js fails with missing sandboxPolicy](https://github.com/openai/codex/issues/29193)** – 21 comments, 4 👍  
   *Windows Desktop’s bundled `node_repl` MCP server fails pre-flight because the sandbox state metadata is incomplete.*
8. **[#28969 — Add setting to disable 60-second auto-resolve](https://github.com/openai/codex/issues/28969)** – 10 comments, 74 👍  
   *CLI users want control over the automatic question-resolution timeout; the current 60s default is too aggressive for complex prompts.*
9. **[#30918 — Usage limits draining 70% to 100% in 6 minutes](https://github.com/openai/codex/issues/30918)** – 5 comments, 1 👍  
   *A worrying rate-limit accounting anomaly on Plus: the 5-hour limit crashed from 70% to 100% during normal use on July 2.*
10. **[#30962 — Windows App silently exits](https://github.com/openai/codex/issues/30962)** – 2 comments, 0 👍  
    *New today: the Windows desktop app terminates with no crash logs, error dialogs, or Event Log entries. Process count drops from 9 to 0 in 15 seconds.*

---

## Key PR Progress (10 selected from 20 active)

1. **[#30963 — Validate approval responses against pending authority](https://github.com/openai/codex/pull/30963)** – *bookholt-oai*  
   *Fixes a security gap where approval IDs were matched only by string; a malicious exec response could consume an unrelated patch approval.*
2. **[#30876 — Support interleaved response items](https://github.com/openai/codex/pull/30876)** – *alexi-openai*  
   *Preserves reasoning-item IDs across interleaved text and reasoning events, keeping the TUI output correct when the model returns mixed responses.*
3. **[#30837 — Derive effective patch paths through Git](https://github.com/openai/codex/pull/30837)** – *bookholt-oai*  
   *Replaces fragile diff-header parsing with Git’s own path resolution, fixing safety checks for renames, copies, and headerless patches.*
4. **[#30896 — Centralize repository authority for Git helper launches](https://github.com/openai/codex/pull/30896)** – *bookholt-oai*  
   *Creates one operation-scoped trusted-executable cache; prevents repository metadata changes from tricking later Git child processes.*
5. **[#30854 — Block selected merge drivers before three-way patch](https://github.com/openai/codex/pull/30854)** – *bookholt-oai*  
   *Prevents `git apply --3way` from running custom merge drivers selected by the repository when a patch doesn’t apply cleanly.*
6. **[#30844 — Confine staged patch paths to the parent worktree](https://github.com/openai/codex/pull/30844)** – *bookholt-oai*  
   *Ensures that staging does not follow symlinks, submodules, or junctions outside the validated worktree boundary.*
7. **[#30848 — Block selected executable Git filters before patch application](https://github.com/openai/codex/pull/30848)** – *bookholt-oai*  
   *Prevents repository-configured clean/smudge filters from running during patch apply, preflight, and revert operations.*
8. **[#30833 — Bind Git worktree helpers to a trusted executable](https://github.com/openai/codex/pull/30833)** – *bookholt-oai*  
   *Selects an absolute native Git executable once, preventing PATH-based substitution by repository-controlled executables.*
9. **[#30863 — Report structured Git status refusals](https://github.com/openai/codex/pull/30863)** – *bookholt-oai*  
   *Replaces a boolean `unavailable` with structured errors when `git status` fails, improving debugging for sandbox status checks.*
10. **[#30493 — Add configurable multi-agent mode hint text](https://github.com/openai/codex/pull/30493)** – *shijie-oai* (CLOSED, code-reviewed)  
    *Allows deployments to override the built-in multi-agent delegation policy hint, replacing the Ultra-only proactive delegation trigger.*

---

## Feature Request Trends

1. **Native Linux desktop app** – Issue #11023 (680 👍) remains the single most-requested feature. Users cite power consumption on Mac laptops and the desire for GPU-accelerated agents on Linux.
2. **Computer Use in CLI** – Issue #20851 requests first-class Computer Use support from the CLI, not only as a desktop app plugin.
3. **Worktree management** – Issues #22316 and #10704 ask for the ability to select existing worktrees and to handle detached-HEAD states properly.
4. **Configurable auto-resolve timeout** – Issue #28969 (74 👍) wants user control over the 60-second prompt auto-resolution instead of hard-coded behavior.
5. **Disable Fast mode** – Issue #20061 reports that Business/Plus users cannot find a UI toggle for Fast mode on macOS.

---

## Developer Pain Points

- **Windows Desktop reliability** – Multiple issues (5 in the top 30 alone) report crashes, freezes, silent exits, temperature spikes, and MCP sandbox misconfigurations on Windows 11. Windows is the platform with the highest density of open bugs.
- **Rate-limit accounting bugs** – Issue #30918 and #12747 describe usage counters draining abnormally fast or resetting unexpectedly, causing developer frustration and lost workflow time.
- **Mac desktop performance** – Issues #16857 (GPU animation), #13709 (indefinite “Thinking”), and #13869 (hangs on new thread) show that the desktop app on macOS still suffers from resource waste and hangs that the CLI avoids.
- **MCP sandbox gaps on Windows** – Issues #29193, #30486, #27552, and #29413 all involve the bundled `node_repl` MCP server failing on Windows because the sandbox state or WSL path resolution is incomplete.
- **Git security hardening (ongoing)** – The 12-PR series from the security team this week directly addresses community fears about repository-supplied Git hooks, filters, and executables running before safety checks. This is a sign that sandbox boundaries were previously too porous.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>

# Gemini CLI Community Digest — 2026-07-03

## Today's Highlights
The nightly release `v0.51.0-nightly.20260703` ships the caretaker egress Cloud Run service skeleton, advancing the operational infrastructure for managing agent triage events. The issue tracker remains heavily focused on agent reliability bugs (MAX_TURNS misclassification, generalist agent hangs, shell execution stalling) and the Auto Memory feature continues to generate several quality-of-life and security improvement tickets. A batch of security PRs around MCP resource handling and OAuth socket reuse also landed.

## Releases
**v0.51.0-nightly.20260703.gf7af4e518** (nightly) — Adds `feat(caretaker): egress cloud run service skeleton` ([PR #28167](https://github.com/google-gemini/gemini-cli/pull/28167)), providing a lightweight HTTP server to receive verified action event messages from the Triage Worker via Cloud Pub/Sub.

[Full Changelog](https://github.com/google-gemini/gemini-cli/compare/v0.51.0-nightly.20260702.gff00dacd9...v0.51.0-nightly.20260703.gf7af4e518)

## Hot Issues
1. **[#22323](https://github.com/google-gemini/gemini-cli/issues/22323) — Subagent recovery after MAX_TURNS reports GOAL success (P1, Bug)**  
   The `codebase_investigator` subagent reports "success" and "Termination Reason: GOAL" even when it actually hit the max turn limit without doing any analysis. This is a **critical reliability bug** — users are given false positive completions, hiding actual failures. 9 comments, high engagement.

2. **[#19873](https://github.com/google-gemini/gemini-cli/issues/19873) — Leverage model's bash affinity via zero-dependency OS sandboxing (P2, Enhancement)**  
   Proposes using Gemini 3's native bash capabilities with sandboxed execution. This is a **long-running architectural discussion** (8 comments) that could fundamentally change how the CLI executes shell commands.

3. **[#21409](https://github.com/google-gemini/gemini-cli/issues/21409) — Generalist agent hangs (P1, Bug)**  
   The CLI hangs forever when deferring to the generalist agent for simple tasks like folder creation. **8 upvotes, 7 comments** — a widely repro'd issue that forces users to disable sub-agents entirely.

4. **[#25166](https://github.com/google-gemini/gemini-cli/issues/25166) — Shell command execution gets stuck with "Waiting input" (P1, Bug)**  
   After simple CLI commands finish, Gemini remains in "Awaiting user input" state. **3 upvotes** — a persistent UX blocker that stalls workflows.

5. **[#26525](https://github.com/google-gemini/gemini-cli/issues/26525) — Add deterministic redaction and reduce Auto Memory logging (P2, Security/ Bug)**  
   Auto Memory sends transcripts to the model *before* redacting secrets, and can log existing skill content. **Risk of secret leakage** — 5 comments, driven by maintainer SandyTao520.

6. **[#26522](https://github.com/google-gemini/gemini-cli/issues/26522) — Stop Auto Memory from retrying low-signal sessions indefinitely (P2, Bug)**  
   Sessions with low signal content are retried forever because they're never marked as processed. **waste of API quota and compute** — 5 comments.

7. **[#22745](https://github.com/google-gemini/gemini-cli/issues/22745) — Assess impact of AST-aware file reads, search, and mapping (P2, Feature)**  
   Epic investigating whether AST-aware tools can reduce turns, token noise, and improve code navigation. **A key performance direction** — 7 comments, touches core codebase interaction.

8. **[#21983](https://github.com/google-gemini/gemini-cli/issues/21983) — Browser subagent fails in Wayland (P1, Bug)**  
   The browser agent crashes on Wayland displays. **Blocks Linux Wayland users** from using browser automation features.

9. **[#22672](https://github.com/google-gemini/gemini-cli/issues/22672) — Agent should stop/discourage destructive behavior (P2, Customer Issue)**  
   Model uses `git reset`, `--force` flags, and dangerous DB commands when safer alternatives exist. **Safety and trust concern** — users want guardrails for destructive operations.

10. **[#24246](https://github.com/google-gemini/gemini-cli/issues/24246) — Gemini CLI encounters 400 error with >128 tools (P2, Bug)**  
    When more than 128 tools are available, the API returns a 400 error. **Scalability ceiling** — agents need smarter tool selection.

## Key PR Progress
1. **[#28223](https://github.com/google-gemini/gemini-cli/pull/28223) — fix(core-tools): bypass LLM correction for JSON and IPYNB files**  
   Surgical fix for `write_file` and `replace` tools corrupting `.ipynb` and `.json` files. **High-impact fix** for data science users.

2. **[#28240](https://github.com/google-gemini/gemini-cli/pull/28240) — Fix: add support for AGENTS.md out of the box (P1)**  
   Makes `AGENTS.md` recognized by default, not just `GEMINI.md`. **Fixes onboarding friction** for agent configuration.

3. **[#28164](https://github.com/google-gemini/gemini-cli/pull/28164) — fix(core): limit recursive reasoning turns per single user request**  
   Caps reasoning turns at 15 per request to prevent infinite loops. **Directly addresses hang/freeze issues** — protects CPU and API quota.

4. **[#28167](https://github.com/google-gemini/gemini-cli/pull/28167) — feat(caretaker): egress cloud run service skeleton**  
   Implements the caretaker egress service for receiving Pub/Sub events from the Triage Worker. **Infrastructure foundation** for automated issue triage.

5. **[#27979](https://github.com/google-gemini/gemini-cli/pull/27979) — Wrap read_mcp_resource output with wrapUntrusted()**  
   Security fix: MCP resource output from servers is now tagged as untrusted, matching the MCP tool behavior. **Prevents prompt injection from external MCP servers**.

6. **[#28103](https://github.com/google-gemini/gemini-cli/pull/28103) — fix(core): avoid keep-alive socket reuse during OAuth token exchange**  
   Fixes "Sign in with Google" failures on Node.js 24.17.0+ after CVE-2026-48931 security patch. **Critical fix for authentication**.

7. **[#27971](https://github.com/google-gemini/gemini-cli/pull/27971) — fix(core): strip thoughts from scrubbed history turns**  
   Resolves "Thought Leakage" where model internal monologues leak into plain-text history, causing confusion and infinite loops. **Major reasoning quality fix**.

8. **[#28244](https://github.com/google-gemini/gemini-cli/pull/28244) — docs(policy-engine): use safe test command instead of rm -rf /**  
   Replaces dangerous `rm -rf /` example in documentation with safe alternatives. **Safety-first documentation fix**.

9. **[#27986](https://github.com/google-gemini/gemini-cli/pull/27986) — feat(acp): report cached and thought tokens in PromptResponse.usage**  
   ACP servers now report cached input and thought/reasoning tokens. **Cost tracking improvement** — prevents 3x overstatement for ACP clients.

10. **[#27994](https://github.com/google-gemini/gemini-cli/pull/27994) — fix(core): insert skill/agent content literally in system prompt substitutions**  
    Prevents metacharacter injection when substituting skill/agent content into system prompts. **Security hardening** for prompt construction.

## Feature Request Trends
- **AST-aware tooling**: Multiple issues (#22745, #22746) request AST-aware file reading, searching, and codebase mapping to reduce token usage and improve code navigation precision.
- **Agent self-awareness & guardrails**: Users want the agent to understand its own CLI flags, hotkeys, and capabilities (#21432), and to recognize destructive behavior (#22672) before executing dangerous commands.
- **Better subagent orchestration**: Requests for subagent trajectory visibility in chat shares (#22598), improved tool selection at scale (#24246), and smarter recovery from MAX_TURNS (#22323) indicate demand for more transparent and reliable multi-agent workflows.
- **Browser agent resilience**: Wayland support (#21983), settings.json override respect (#22267), and session lock recovery (#22232) are recurring themes.
- **Deterministic security & redaction**: Auto Memory improvements (#26525, #26522, #26523) reflect a trend toward pre-exfiltration redaction and preventing infinite retry loops.

## Developer Pain Points
- **Agent hangs and false completions**: The #1 source of frustration — generalist agent hangs indefinitely (#21409), MAX_TURNS misreported as success (#22323), and shell commands stuck at "Waiting input" (#25166) undermine trust in the agent reliability.
- **Subagent misbehavior**: Agents running without permission after updates (#22093), not using custom skills (#21968), and ignoring configuration overrides (#22267) force users to disable sub-agents entirely.
- **Security and data leakage**: Auto Memory sending secrets to the model before redaction (#26525), MCP resource injection risk (#27979), and OAuth authentication failures (#28103) create real security concerns.
- **Terminal and rendering issues**: Emoji splitting in display strings (#28224), flicker on resize (#21924), and terminal corruption after external editors (#24935) degrade the user experience on non-ideal terminals.
- **Scalability ceilings**: The 128-tool API limit (#24246) blocks users with many tools/skills, and the lack of tool selection heuristics forces manual workarounds.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

# GitHub Copilot CLI Community Digest — 2026-07-03

## Today's Highlights
A new triage wave has brought attention to MCP server integration bugs, terminal rendering issues on Windows, and model availability problems with the `gpt-5.3-codex` endpoint. Community resistance to the scrollbar feature continues to grow, with two new reports of text corruption when selecting/copying output. No new releases were cut in the last 24 hours.

## Releases
**None** — No new releases in the last 24 hours.

## Hot Issues (10 picks)

### 1. [Issue #3997] — Model "gpt-5.3-codex" is not available (Triage)
**TL;DR:** A broad API error prevents users from running Copilot as an agent. The model assigned to the session disappears.  
**Impact:** Blocks all agentic coding workflows. 6 comments, triage open.  
[GitHub](https://github.com/github/copilot-cli/issues/3997)

### 2. [Issue #3501] — Scroll bar makes text unalign on Windows
**TL;DR:** The vertical scrollbar introduced ~50 days ago corrupts line alignment in both Windows Console Host and Terminal.  
**Community reaction:** 9 upvotes — this is the highest-voted open issue.  
**Impact:** Terminal rendering is broken for all Windows users.  
[GitHub](https://github.com/github/copilot-cli/issues/3501)

### 3. [Issue #4009] — Terminal mouse-selection copy corrupted by scrollbar column
**TL;DR:** Selecting output with the mouse includes the `┃` scrollbar glyph on every line, making clipboard copies unusable.  
**Why it matters:** Follow-up to #3501; the scrollbar implementation has no opt-out and actively breaks copy/paste.  
[GitHub](https://github.com/github/copilot-cli/issues/4009)

### 4. [Issue #4015] — Theme setting not remembered
**TL;DR:** After `/settings theme <theme>`, the CLI forgets the selection on restart.  
**Impact:** UX regression; users must re-set their theme every session. 0 comments — freshly filed.  
[GitHub](https://github.com/github/copilot-cli/issues/4015)

### 5. [Issue #4014] — Rendering all messed up when adding an MCP server
**TL;DR:** Using `/mcp add` causes severe terminal mis-rendering (screenshot attached).  
**Impact:** Blocks the primary MCP onboarding path.  
[GitHub](https://github.com/github/copilot-cli/issues/4014)

### 6. [Issue #4006] — MCP tools/list pagination (nextCursor) not followed
**TL;DR:** The CLI ignores cursor-based pagination from MCP servers, loading only the first page of tools.  
**Why it matters:** Violates the MCP spec; servers with many tools silently lose functionality.  
[GitHub](https://github.com/github/copilot-cli/issues/4006)

### 7. [Issue #4003] — Support custom model endpoint in Copilot CLI (like VS Code)
**TL;DR:** Request for CLI parity with VS Code’s custom endpoint configuration for local/private models.  
**Why it matters:** Enterprise and offline use-cases are gated on this feature.  
[GitHub](https://github.com/github/copilot-cli/issues/4003)

### 8. [Issue #4012] — BYOK reasoning effort not supported for custom models
**TL;DR:** Using `--reasoning-effort max` with BYOK models (e.g., `glm-5.2:cloud`) produces an error, even though the model itself is valid.  
**Impact:** Power-users can't control reasoning depth with private models.  
[GitHub](https://github.com/github/copilot-cli/issues/4012)

### 9. [Issue #4013] — macOS: Ctrl+V image paste fails with raw clipboard data
**TL;DR:** Pasting an image from SnagIt or Preview is a no-op; only file-based paste works.  
**Impact:** Breaks image-in-prompt workflows for macOS users of Clipboard managers.  
[GitHub](https://github.com/github/copilot-cli/issues/4013)

### 10. [Issue #4010] — "Copied to clipboard" notification misleading without Shift
**TL;DR:** Mouse text selection triggers a "Copied to clipboard" notification, but the clipboard is actually empty until a second right-click.  
**Impact:** Confusing UX — users think they have copied text when they haven't.  
[GitHub](https://github.com/github/copilot-cli/issues/4010)

## Key PR Progress (2 active items)

### 1. [PR #3880] — "beyond the streets of america"
**Status:** Open, 0 comments. Appears to be an errant/non-functional PR containing a React artist-card component — likely spam or test data.  
[GitHub](https://github.com/github/copilot-cli/pull/3880)

### 2. [PR #3873] — Add initial console log for greeting
**Status:** Open, 0 comments. Minimal description; appears to be an incomplete or stub PR.  
[GitHub](https://github.com/github/copilot-cli/pull/3873)

## Feature Request Trends
The top emergent themes this week:
- **Custom model endpoints** — Several requests (BYOK, local, private) for CLI parity with VS Code’s model configuration panel.
- **Persistent deny rules** — Users want `permissions-config.json` to support blacklists, not just allowlists.
- **Non-interactive /init** — Automating project initialization from CI/scripts is blocked by the interactive prompt.
- **MCP pagination support** — Compliance with the MCP spec for servers returning more than one page of tools.

## Developer Pain Points
Repeated friction points visible across this batch:
- **Terminal rendering (Windows)** — The scrollbar remains the #1 pain point: text misalignment, corrupted copy/paste, no opt-out.
- **Plugin/MCP server discovery** — Servers installed via plugins are not registered in `mcp-config.json`; `tools/list` pagination is ignored.
- **Model switching instability** — BYOK sessions revert to previous models on resume; reasoning-effort flags fail on custom endpoints.
- **Session management confusion** — `/clear` vs `/new` semantics are unclear; `/new` drops usage statistics without writing shutdown events.
- **Accessibility gaps** — Screen readers do not echo typed characters; clipboard operations fail silently in browser-based VSCode Server.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

# Kimi Code CLI Community Digest
**Date:** 2026-07-03  
**Source:** github.com/MoonshotAI/kimi-cli

---

## Today's Highlights
The community saw renewed attention on a long-standing loop bug (Issue #640) that has persisted across multiple Kimi CLI versions, with 16 comments and minimal maintainer engagement. A newly opened PR (#2481) aims to fix clipboard paste behavior for Windows terminals, addressing a critical UX gap. No new releases were published in the last 24 hours.

---

## Releases
*No new releases in the last 24 hours.*

---

## Hot Issues
*Top 10 noteworthy issues updated in the last 24 hours:*

1. **[#640] [bug] Kimi CLI stuck in reading one file again and again and stuck in a loop**  
   *Author: isbafatima90-arch | Updated: 2026-07-02 | Comments: 16*  
   **Significance:** A persistent bug where the CLI enters an infinite loop re-reading a single file. Affects multiple models and endpoints (Anthropic, Mimo-v2-flash). Community is frustrated by lack of resolution.  
   [View Issue](https://github.com/MoonshotAI/kimi-cli/issues/640)

2. **[#1111] [CLOSED] [bug] kimi web use tailscale websocket connection error**  
   *Author: tianyw0 | Updated: 2026-07-02 | Comments: 2*  
   **Significance:** Websocket connection failures when using Tailscale with Kimi Code CLI v1.12.0 on macOS Darwin. Closed with minimal discussion, potentially leaving Tailscale users unresolved.  
   [View Issue](https://github.com/MoonshotAI/kimi-cli/issues/1111)

3. **[#638] [bug] Kimi CLI crashes on large file input (>10MB)**  
   *Author: heavycoder | Updated: 2026-07-02 | Comments: 12*  
   **Significance:** CLI crashes without error when processing large files. Affects users feeding logs or datasets. No stability improvements noted recently.  
   [View Issue](https://github.com/MoonshotAI/kimi-cli/issues/638)

4. **[#1102] [bug] `kimi code --watch` does not detect file changes in subdirectories**  
   *Author: devops_ninja | Updated: 2026-07-02 | Comments: 8*  
   **Significance:** Watch mode only watches the current directory, not recursive. Breaks workflows for monorepo users.  
   [View Issue](https://github.com/MoonshotAI/kimi-cli/issues/1102)

5. **[#1099] [feature] Support `ollama` as a backend for local inference**  
   *Author: local-ai-enthusiast | Updated: 2026-07-02 | Comments: 14*  
   **Significance:** High-user request to integrate Ollama for fully offline model execution. Community showing strong interest.  
   [View Issue](https://github.com/MoonshotAI/kimi-cli/issues/1099)

6. **[#1087] [bug] `kimi chat` freezes after 2-3 exchanges on macOS Sequoia**  
   *Author: macuser_tom | Updated: 2026-07-02 | Comments: 5*  
   **Significance:** Intermittent frozen sessions on latest macOS. No workaround documented.  
   [View Issue](https://github.com/MoonshotAI/kimi-cli/issues/1087)

7. **[#1071] [bug] Config file ignored when using `--model` flag**  
   *Author: config_confused | Updated: 2026-07-02 | Comments: 6*  
   **Significance:** CLI silently overrides config with flag inputs, causing unexpected model switching.  
   [View Issue](https://github.com/MoonshotAI/kimi-cli/issues/1071)

8. **[#1064] [bug] Windows Terminal `Ctrl+V` paste does not work for image data**  
   *Author: win-user-42 | Updated: 2026-07-02 | Comments: 9*  
   **Significance:** Directly related to the fix in PR #2481; paste of images fails due to BracketedPaste handling.  
   [View Issue](https://github.com/MoonshotAI/kimi-cli/issues/1064)

9. **[#1055] [bug] `kimi shell` does not respect `$PATH` updates**  
   *Author: shell_user | Updated: 2026-07-02 | Comments: 4*  
   **Significance:** Shell integration fails to pick up environment changes, affecting toolchain users.  
   [View Issue](https://github.com/MoonshotAI/kimi-cli/issues/1055)

10. **[#1048] [feature] Add `kimi doctor` diagnostic command**  
    *Author: debugmaster | Updated: 2026-07-02 | Comments: 3*  
    **Significance:** Proposed feature to auto-detect configuration, network, and version issues. Low maintainer response.  
    [View Issue](https://github.com/MoonshotAI/kimi-cli/issues/1048)

---

## Key PR Progress
*Top 10 noteworthy pull requests updated in the last 24 hours:*

1. **[#2481] [OPEN] fix(shell): read clipboard media on BracketedPaste for Windows terminals**  
   *Author: redjade75723 | Updated: 2026-07-02*  
   **Feature:** Adds clipboard media (images, binary) paste support for Windows Terminal and VS Code integrated terminal.  
   [View PR](https://github.com/MoonshotAI/kimi-cli/pull/2481)

2. **[#2478] [OPEN] feat(agent): add `--recursive` flag to watch command**  
   *Author: file-watcher-42 | Updated: 2026-07-02*  
   **Feature:** Implements recursive file watching for `kimi code --watch`, addressing Issue #1102.  
   [View PR](https://github.com/MoonshotAI/kimi-cli/pull/2478)

3. **[#2475] [OPEN] fix(core): fallback to config model if `--model` flag is not set**  
   *Author: config-cleanup | Updated: 2026-07-02*  
   **Fix:** Clarifies model selection behavior when flag and config conflict.  
   [View PR](https://github.com/MoonshotAI/kimi-cli/pull/2475)

4. **[#2472] [OPEN] refactor(shell): improve startup time by lazy-loading completions**  
   *Author: speedup-fan | Updated: 2026-07-02*  
   **Optimization:** Reduces shell initialization delay from ~2s to ~0.3s.  
   [View PR](https://github.com/MoonshotAI/kimi-cli/pull/2472)

5. **[#2469] [CLOSED] revert: rollback ollama integration due to memory leak**  
   *Author: maintainer-bot | Updated: 2026-07-02*  
   **Revert:** Temporary rollback of earlier Ollama backend integration pending memory leak fix.  
   [View PR](https://github.com/MoonshotAI/kimi-cli/pull/2469)

6. **[#2466] [OPEN] feat(doctor): add `kimi doctor` diagnostic command**  
   *Author: debugmaster | Updated: 2026-07-02*  
   **Feature:** Initial implementation of Issue #1048; detects config, network, and version issues.  
   [View PR](https://github.com/MoonshotAI/kimi-cli/pull/2466)

7. **[#2463] [OPEN] fix(chat): add heartbeat to prevent macOS session freeze**  
   *Author: mac-user-hero | Updated: 2026-07-02*  
   **Fix:** Adds periodic heartbeat signal to keep `kimi chat` connections alive on macOS.  
   [View PR](https://github.com/MoonshotAI/kimi-cli/pull/2463)

8. **[#2460] [OPEN] feat(api): expose `--tailscale-mode` for websocket fallback**  
   *Author: netadmin-joe | Updated: 2026-07-02*  
   **Feature:** Provides explicit Tailscale compatibility mode for websocket connections.  
   [View PR](https://github.com/MoonshotAI/kimi-cli/pull/2460)

9. **[#2457] [OPEN] test(shell): add integration tests for BracketedPaste on Windows**  
   *Author: qa-bot-99 | Updated: 2026-07-02*  
   **Test:** Adds CI tests for Windows paste behavior, ensuring no regressions.  
   [View PR](https://github.com/MoonshotAI/kimi-cli/pull/2457)

10. **[#2454] [OPEN] docs(cli): document `config.toml` environment variable override behavior**  
    *Author: doc-writer-101 | Updated: 2026-07-02*  
    **Docs:** Clarifies priority rules between config file, environment variables, and CLI flags.  
    [View PR](https://github.com/MoonshotAI/kimi-cli/pull/2454)

---

## Feature Request Trends
The most requested feature directions from all active issues include:

1. **Local Inference Backends** – Strong demand for Ollama and llama.cpp integration for fully offline usage.
2. **Recursive File Watching** – Users need `--watch` to support subdirectories, especially monorepo users.
3. **Diagnostic Tools** – Repeated requests for a `kimi doctor` command to auto-detect misconfigurations.
4. **Tailscale / VPN Support** – Websocket fallback and explicit compatibility mode for Tailscale users.
5. **Large File Handling** – Support for files >10MB with streaming or chunking.
6. **Cross-Platform Clipboard** – Image paste support for Windows and Linux (Wayland).

---

## Developer Pain Points
Recurring frustrations and high-frequency requests from the community:

- **Unresolved Infinite Loop Bug** – Issue #640 has been open since January 2026 with 16 comments and no fix; users are stuck on older versions.
- **Silent Crashes on Large Files** – CLI crashes without error messages, making debugging impossible.
- **MacOS Session Freezes** – Intermittent freezes after 2-3 chat exchanges; no documented workaround.
- **Config / Flag Conflict** – CLI silently overrides config settings with CLI flags, causing unexpected model or endpoint changes.
- **Slow Startup Time** – Shell completions and initialization take ~2 seconds, impacting productivity.
- **Poor Error Messages** – Many bugs (websocket, paste, file loops) lack actionable error messages, forcing users to guess root causes.
- **Low Maintainer Response** – Several high-engagement issues and PRs lack maintainer comments or approvals, slowing community momentum.

---

*Generated by the Kimi Code CLI Community Team*

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

# OpenCode Community Digest — 2026-07-03

**Data Source:** [github.com/anomalyco/opencode](https://github.com/anomalyco/opencode)

---

## 1. Today's Highlights

The community remains highly engaged with **50 new or updated issues and 20 active pull requests** in the last 24 hours. A critical **OpenCode Go subscription outage** is emerging, with multiple users reporting that paid accounts hang indefinitely or fail to connect after purchase. On the development front, a major **refactoring push** led by contributor `kitlangton` is streamlining the V2 prompt lifecycle, session log replay, and context management, resolving several long-standing bugs around tool output persistence and subagent coordination.

---

## 2. Releases

**No new releases in the last 24 hours.** The latest stable version remains **v1.17.13**.

---

## 3. Hot Issues (Top 10)

### #28846 — [CLOSED] Adjust Go usage limits after DeepSeek V4 Pro permanent 75% price reduction
- **Why it matters:** DeepSeek's aggressive pricing cut makes Go subscriptions significantly more economical. This closed issue (90 comments, 82 👍) signals that the team has already addressed the limits, likely benefiting all Go subscribers.
- **Link:** [Issue #28846](https://github.com/anomalyco/opencode/issues/28846)

### #8003 — [OPEN] VS Code Integration for Reviewing OpenCode Code Changes (Diff Preview)
- **Why it matters:** With 73 👍 and 16 comments, this is the most-upvoted open feature request. Users working with large files find the TUI diff preview painful and want native VS Code integration.
- **Link:** [Issue #8003](https://github.com/anomalyco/opencode/issues/8003)

### #10272 — [CLOSED] Hidden calls Haiku
- **Why it matters:** A concerning bug where OpenCode silently routed requests to **Claude Haiku 4.5** despite explicit configuration for MiniMax M2.1 via OpenRouter. This raised trust issues around billing transparency; closed status suggests a fix was deployed.
- **Link:** [Issue #10272](https://github.com/anomalyco/opencode/issues/10272)

### #35035 & #35048 — [OPEN] OpenCode Go hangs forever after "build" on Windows / Subscription not working
- **Related:** #35049 — Billing: Go Subscription Remains Locked After Removing Previous Member
- **Why it matters:** **Multiple users report OpenCode Go is broken.** Purchased subscriptions either hang indefinitely (`build · glm-5.2`) or show no response. A billing lock prevents re-subscription after removing an old member. This is a **critical blocker for paid users**.
- **Links:** [Issue #35035](https://github.com/anomalyco/opencode/issues/35035) | [Issue #35048](https://github.com/anomalyco/opencode/issues/35048) | [Issue #35049](https://github.com/anomalyco/opencode/issues/35049)

### #31972 — [OPEN] New Layout and Designs breaks Plan/Build mode switching
- **Why it matters:** Enabling the experimental new layout feature flag completely disables the ability to switch between Plan and Build modes — both the UI toggle and `Ctrl+.` shortcut stop working. This blocks workflow for users trying the new UI.
- **Link:** [Issue #31972](https://github.com/anomalyco/opencode/issues/31972)

### #35044 — [OPEN] Read Tool is really slow on massive files
- **Why it matters:** Reading a 6.7M-line file is painfully slow. An immediate fix is in progress (see PR #35050), but this highlights a performance gap for enterprise codebases.
- **Link:** [Issue #35044](https://github.com/anomalyco/opencode/issues/35044)

### #31041 — [OPEN] Zen API endpoints return 404 on CORS preflight (OPTIONS)
- **Why it matters:** Blocks all browser-based clients from calling the Zen API. CORS preflight fails on all `/zen/v1/*` endpoints — a fundamental API infrastructure issue.
- **Link:** [Issue #31041](https://github.com/anomalyco/opencode/issues/31041)

### #35032 — [OPEN] The OpenCode startup screen shows JSON
- **Why it matters:** A perplexing UX regression where launching the CLI from cmd.exe renders raw JSON instead of the startup splash. Likely a rendering or serialization bug in v1.17.13.
- **Link:** [Issue #35032](https://github.com/anomalyco/opencode/issues/35032)

### #35026 — [CLOSED] [Windows] Renderer crash and severe lag in heavy sessions (Memory Leak)
- **Why it matters:** Desktop app becomes unresponsive in long sessions due to memory leaks. New sessions work fine, but as context grows, the renderer crashes — a known Electron memory management challenge.
- **Link:** [Issue #35026](https://github.com/anomalyco/opencode/issues/35026)

### #33106 — [OPEN] Desktop app hangs and crashes when rendering large session diff summary
- **Why it matters:** macOS users hitting OOM crashes on large session rendering. The Electron main process dies when opening heavy sessions, making them unrecoverable.
- **Link:** [Issue #33106](https://github.com/anomalyco/opencode/issues/33106)

---

## 4. Key PR Progress (Top 10)

### #35051 — [OPEN] refactor(core): polish runner drain and coordinator readability
- **Contributor:** `kitlangton`
- **What it does:** Follow-up polish on #35047 — simplifies `SessionRunner.run`, names serialization helpers, and reduces redundant `publication.withPermit` wrappers from eleven to a single loop.
- **Link:** [PR #35051](https://github.com/anomalyco/opencode/pull/35051)

### #35050 — [OPEN] fix(core): skip ahead by counting newlines when reading at a high offset
- **Contributor:** `weiconghe`
- **What it does:** Fixes #35044 (slow reads on massive files) by skipping directly to the target line offset instead of scanning line-by-line. **High impact for large codebase users.**
- **Link:** [PR #35050](https://github.com/anomalyco/opencode/pull/35050)

### #35047 — [CLOSED] refactor(core): simplify v2 prompt lifecycle and execution coordination
- **Contributor:** `kitlangton`
- **What it does:** Five-commit cleanup — fixes silent tool output persistence failures, reconnects failed assertions, and properly drains tool outputs to logs. Merged into main.
- **Link:** [PR #35047](https://github.com/anomalyco/opencode/pull/35047)

### #35046 — [OPEN] refactor(core): replace context epoch with checkpoint
- **Contributor:** `kitlangton`
- **What it does:** Replaces session context epoch persistence with a single-entry context checkpoint, simplifying system context into a belief model with delta-based guidance updates.
- **Link:** [PR #35046](https://github.com/anomalyco/opencode/pull/35046)

### #35040 — [CLOSED] feat(core): deterministic session log replay with synced watermark
- **Contributor:** `kitlangton`
- **What it does:** Replaces `log.caught_up` with `log.synced`, providing deterministic replay through a fixed watermark while preserving live tail delivery. Merged.
- **Link:** [PR #35040](https://github.com/anomalyco/opencode/pull/35040)

### #35042 — [CLOSED] feat(app): navigate tabs on mousedown in new layout
- **Contributor:** `Hona`
- **What it does:** Improves perceived tab switch latency by reacting on mousedown instead of mouseup — eliminates 40-100ms of press-to-release delay.
- **Link:** [PR #35042](https://github.com/anomalyco/opencode/pull/35042)

### #33547 — [OPEN] fix(go): filter models list to only show oa-compat supported models
- **Contributor:** `devinoldenburg`
- **What it does:** Fixes the `/zen/go/v1/models` endpoint returning every catalog model. Now only shows models compatible with the Go endpoint. **Critical for Go subscription reliability.**
- **Link:** [PR #33547](https://github.com/anomalyco/opencode/pull/33547)

### #34943 — [CLOSED] fix(console): skip console-side 429 retry for gateway providers
- **Contributor:** `StarpTech`
- **What it does:** Stops the console from retrying 429 rate-limit responses from the inference gateway, whose verdict is final. Uses plain `fetch` for gateway requests.
- **Link:** [PR #34943](https://github.com/anomalyco/opencode/pull/34943)

### #35010 — [OPEN] feat(desktop): reopen closed tabs, cmd+w close tab, background tab open
- **Contributor:** `usrnk1`
- **What it does:** Adds browser-style tab management: `⇧⌘T` to reopen closed tabs, `Cmd+W` to close, and meta-click to open tabs in background. Beta feature.
- **Link:** [PR #35010](https://github.com/anomalyco/opencode/pull/35010)

### #34954 — [OPEN] feat(app): improvements to model search
- **Contributor:** `arvsrn`
- **What it does:** Normalizes separators and punctuation in the composer model picker so `gpt 5`, `gpt-5`, and `gpt5` all match the same model. Small quality-of-life improvement.
- **Link:** [PR #34954](https://github.com/anomalyco/opencode/pull/34954)

---

## 5. Feature Request Trends

| Trend | Signal |
|---|---|
| **VS Code integration** | #8003 (73 👍) — diff preview for code changes is the most-upvoted open feature |
| **Desktop UX improvements** | Multiple PRs adding tab management, model search, and folder picker (#35039) |
| **Go subscription economics** | #28846 (82 👍, closed) — users actively watching pricing and limits |
| **New layout refinement** | #31972, plus multiple PRs fixing the experimental layout — the team is pushing toward GA |
| **Local model performance** | #33126 — llama.cpp users want faster session title generation |

---

## 6. Developer Pain Points

- **OpenCode Go is unreliable for new subscribers.** Multiple reports (#35035, #35048, #35049) of purchased subscriptions not working, hanging indefinitely, or being locked by billing errors. This is a **critical revenue-impacting issue.**
- **Large file handling remains a pain point.** The Read Tool is slow on massive files (#35044) and the desktop app crashes when rendering large session diffs (#33106, #35026). For developers working in monorepos or enterprise codebases, these are daily blockers.
- **Hidden model routing erodes trust.** Issue #10272 (now closed) showed that OpenCode could silently call a different model than configured. Even with a fix, this leaves users cautious about billing accuracy.
- **CORS and API infrastructure gaps.** The Zen API blocks all browser clients (#31041) and xAI prompt caching is missing routing identifiers (#35033) — core API issues for advanced users.
- **New layout breaks core workflow.** #31972 — enabling the experimental layout prevents switching between Plan and Build modes, making it unusable for production work.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>

# Pi Community Digest — 2026-07-03

## Today's Highlights

A major wave of bug fixes and quality-of-life improvements landed today, with 25+ issues closed and 12 PRs submitted. The most critical fix addresses `null content` crashes in reasoning models (Issue #4909), which had been blocking extension tools and compaction for weeks. Infrastructure improvements include a new DeepInfra provider, SQLite session storage, and TUI sticky-bottom rendering, alongside urgent patches for OpenAI Responses token clamping and Codex WebSocket timeouts.

## Releases

No new releases in the last 24 hours. The latest stable version remains `v0.80.3`.

## Hot Issues

1. **[#4909 — `message.content is not iterable` crashes ALL extension tools (v0.75.4)](https://github.com/earendil-works/pi/issues/4909)**  
   **Closed.** This long-standing bug (`👍 0`) caused every extension tool and command to crash when reasoning models returned `null` content. Three related issues (#2785, #6259) were closed in tandem. The fix in PR #6258 adds null guards across agent loop, compaction, and message transforms. **High community impact** — affected all users of GLM-5.2, Fireworks, and similar reasoning models.

2. **[#4505 — 400 error with MiMo models in multi-turn tool use](https://github.com/earendil-works/pi/issues/4505)**  
   **Closed.** `reasoning_content` not preserved across turns caused `400` errors on second turn with `xiaomi-token-plan` provider. 12 comments, 4 👍. Fixed in the `closed-because-refactor` batch.

3. **[#6187 — Pi login hangs in WSL after GitHub Copilot device auth](https://github.com/earendil-works/pi/issues/6187)**  
   **Closed.** Browser-based device authorization completed but CLI didn't detect it. 9 comments. A blocking UX issue for WSL users, now resolved.

4. **[#6215 — `pi update` fails on v0.80.3 due to missing `@smithy/node-http-handler@^4.9.1`](https://github.com/earendil-works/pi/issues/6215)**  
   **Closed.** Dependency resolution failure blocked upgrades. Highlights fragility in pnpm resolution of transitive dependencies in the AWS SDK stack.

5. **[#6255 — Extended function keys (F13+) insert PUA characters](https://github.com/earendil-works/pi/issues/6255)**  
   **Closed.** Kitty protocol F13-F24 keys were not ignored; instead they injected garbage into input. Affected Ghostty and Kitty terminal users.

6. **[#6234 — Escape leaves Pi stuck in "Working" when extension hook never settles](https://github.com/earendil-works/pi/issues/6234)**  
   **Closed.** Double-Escape needed for abort, but first Escape was swallowed by streaming-abort logic. Author `xz-dev` discovered the race condition.

7. **[#6231 — Auth blocking local models](https://github.com/earendil-works/pi/issues/6231)**  
   **Closed.** Local DeepSeek V4 Flash users forced to OAuth login. 4 comments. Highlights a fundamental UX tension: local vs. remote provider handling.

8. **[#6257 — Add `claude-sonnet-5` to GitHub Copilot catalog](https://github.com/earendil-works/pi/issues/6257)**  
   **Closed.** Quick model catalog update. Community eager for latest Anthropic models on Copilot provider.

9. **[#6256 — Add Kimi K2.7 under GitHub Copilot provider](https://github.com/earendil-works/pi/issues/6256)**  
   **Closed.** 1 👍. Model selection request following GitHub's July 1 announcement of K2.7 availability.

10. **[#6262 — DS4-server context overflow not detected by auto-compaction](https://github.com/earendil-works/pi/issues/6262)**  
    **Closed.** Local DeepSeek V4 Flash users hit 400 errors when prompts exceeded 256K tokens. The error message format was not parsed by auto-compaction, leaving users stuck.

## Key PR Progress

1. **[#6267 — `InlineExtension` type for named inline extension factories](https://github.com/earendil-works/pi/pull/6267)**  
   **Open.** Closes #6260. Adds typed `InlineExtension` union so inline factories passed to `main()` are properly typed and discoverable. Author: any-victor.

2. **[#6266 — Anthropic strict tool use for the edit tool](https://github.com/earendil-works/pi/pull/6266)**  
   **Open.** Claims ~10% error rate reduction for Claude edits by enforcing stricter tool call schemas. Addresses #5501 and #5434. Author: pasky.

3. **[#6264 — Fix OpenAI Responses output token clamping](https://github.com/earendil-works/pi/pull/6264)**  
   **Closed.** Fixes #6265 where `max_output_tokens` could drop below API minimum (16) near context limit. Prevents 400 errors in long sessions.

4. **[#6263 — Add DeepInfra provider](https://github.com/earendil-works/pi/pull/6263)**  
   **Closed.** New built-in provider for text (OpenAI-compatible) and image generation. Model catalogs auto-generated from DeepInfra API. Author: ats3v.

5. **[#6258 — Fix `null content` crash in reasoning models](https://github.com/earendil-works/pi/pull/6258)**  
   **Closed.** Guards against `AssistantMessage.content === null` when models return only `reasoning_content` + `tool_calls`. Fixes #4909, #2785, #6259.

6. **[#6227 — SQLite session storage](https://github.com/earendil-works/pi/pull/6227)**  
   **Open.** `PI_SQLITE_SESSION_STORAGE=1` flag writes session transcripts to SQLite db alongside JSONL. Enables querying session history. Author: cristinaponcela.

7. **[#6252 — Fix `find` paths from Windows drive root](https://github.com/earendil-works/pi/pull/6252)**  
   **Closed.** Replaces manual prefix slicing with `path.relative()` to fix bare drive-root `find` results on Windows. Fixes #6104.

8. **[#6248 — Stop padding TUI lines with trailing spaces](https://github.com/earendil-works/pi/pull/6248)**  
   **Closed.** Eliminates trailing whitespace that polluted clipboard copy in VS Code integrated terminal (xterm.js). Author: Dombo.

9. **[#6244 — Keep interactive input and footer sticky](https://github.com/earendil-works/pi/pull/6244)**  
   **Closed.** Adds sticky-bottom boundary API so editor/footer stay visible while earlier content scrolls. Author: S-Mark0309.

10. **[#6243 — Fix UUID collisions and race conditions in session storage](https://github.com/earendil-works/pi/pull/6243)**  
    **Closed.** Fixes three data integrity bugs: UUID truncation collisions, race conditions in `InMemorySessionStorage`, and JSON parsing in file storage. Closes #6242.

## Feature Request Trends

- **Model catalog expansion** is the dominant theme this week: requests for `claude-sonnet-5`, Kimi K2.7, and MiMo v2 Omni demonstrate users want immediate access to newest models without waiting for provider updates.
- **Project-level configuration** for skills (`--skill`, `--no-skills` in `settings.json`) is a recurring request (#5570) with partial progress in PR #6236.
- **Configurable tool truncation** (#6254) and **environment variable skills path** (#6191) show demand for more flexible customization without CLI flags.
- **SQLite session storage** (#6227) suggests interest in structured, queryable session history beyond JSONL.

## Developer Pain Points

- **Reasoning model incompatibility** remains the #1 pain point: `null content` crashes (#4909, #2785, #6259) affected all reasoning-model users, blocking extension tools and compaction. The fix landed today but highlights fundamental assumptions in message handling.
- **Context window management** is fragile: auto-compaction fails to detect custom error formats (DS4-server, #6262), and `max_tokens` clamping can go below API minimums (#6265, #6206).
- **Provider-specific quirks** cause friction: Copilot auth in WSL (#6187), MiMo multi-turn failures (#4505), OpenAI Responses token limits (#6265), and Bedrock caching gaps (#6235, #6245).
- **TUI polish issues** accumulate: trailing spaces break copy (#6251), HOME/END keys broken (#6199), PUA characters from function keys (#6255), and Linux clipboard failures (#6250).
- **Update reliability** is shaky: dependency resolution failures (#6215) block users from receiving fixes, and compiled binary addons break across versions (#6250).

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>

# Qwen Code Community Digest — 2026-07-03

## Today's Highlights

Two stable releases shipped this week with notable daemon and web-shell improvements, while the community is actively discussing multi-agent nesting depth, channel-based scheduling, and Windows UTF-8 fixes. The autofix pipeline and vision bridge model selection emerged as top-of-mind feature requests alongside ongoing performance work for mobile session switching.

## Releases

- **v0.19.5** (stable) — Hardens daemon-managed channel worker lifecycle and defers web-shell session creation until first prompt, reducing unnecessary overhead. [Release notes](https://github.com/QwenLM/qwen-code/releases/tag/v0.19.5)
- **v0.19.5-nightly.20260703.b16baf1ff** — Fixes mobile session-switching jank by memoizing the timeline signature and replaying the first dispatch. [Release notes](https://github.com/QwenLM/qwen-code/releases/tag/v0.19.5-nightly.20260703.b16baf1ff)

## Hot Issues

1. **[#6195](https://github.com/QwenLM/qwen-code/issues/6195) — Add daemon UI support for selecting the vision bridge model** (5 comments)  
   The CLI already supports `/model --vision` but the daemon UI is missing a picker, forcing users to CLI for a core workflow. High engagement suggests vision model selection is reaching mainstream use.

2. **[#6077](https://github.com/QwenLM/qwen-code/issues/6077) — Follow-up suggestion mistakenly filters sentences with abbreviations** (5 comments)  
   A subtle bug where "Dr." or "vs." at sentence end triggers the `multiple_sentences` filter. Root cause identified and a fix is in progress (#6193).

3. **[#6144](https://github.com/QwenLM/qwen-code/issues/6144) — Incorrect context window calculation** (4 comments, 1 👍)  
   A user configuring Qwen3-Coder with 64K context found Qwen-Code reporting a different window size, affecting token budget accuracy. Impacts long-context workflows.

4. **[#5979](https://github.com/QwenLM/qwen-code/issues/5979) — `/auth` changes don't persist to new sessions** (4 comments)  
   After updating model provider keys via `/auth`, new sessions still return 401 errors. A Windows-related auth persistence bug that blocks multi-session users.

5. **[#6175](https://github.com/QwenLM/qwen-code/issues/6175) — Thinking display shows 'Thought for 0s' and output not streaming** (3 comments)  
   OpenAI-compatible models with `reasoning_content` in streaming lose timing info and don't render thoughts incrementally. Impacts UX for reasoning-heavy models.

6. **[#6112](https://github.com/QwenLM/qwen-code/issues/6112) — Local always-on `/schedule` daemon** (3 comments)  
   A feature request for cron-style background tasks without an open session — the local analogue of Claude Code's scheduled tasks. Gains traction as channel automation matures.

7. **[#6181](https://github.com/QwenLM/qwen-code/issues/6181) — Mobile session switching is janky** (2 comments)  
   Four compounding costs (polling, full transcript render, uncompressed history, per-frame overhead) cause multi-second freezes on mobile. The nightly release partially addresses this.

8. **[#6218](https://github.com/QwenLM/qwen-code/issues/6218) — Taobao mirror is three versions behind** (2 comments)  
   Chinese users on the npm Taobao mirror cannot upgrade. A packaging/distribution issue affecting a significant user base.

9. **[#6214](https://github.com/QwenLM/qwen-code/issues/6214) — Garbled text in shell output on Windows non-UTF-8 code pages** (2 comments)  
   `run_shell_command` on Windows with CP1251/CP936 produces garbled output. Addressed by PR #6216 with a UTF-8 prefix for `cmd.exe`.

10. **[#6149](https://github.com/QwenLM/qwen-code/issues/6149) — VP mode breaks links; non-VP mode cannot scroll overflow** (1 comment)  
    Two TUI rendering bugs — OSC 8 hyperlinks unclickable in VP mode, and content overflow unscrollable without it. Affects terminal power users.

## Key PR Progress

1. **[#6019](https://github.com/QwenLM/qwen-code/pull/6019) — `/model --compaction` for configurable chat compression model**  
   Lets users dedicate a model specifically for auto-compact, reducing token waste on long sessions.

2. **[#6096](https://github.com/QwenLM/qwen-code/pull/6096) — `zvec-grep` bundled skill**  
   Guides the agent to use `zg` CLI for semantic workspace search when exact file/symbol names are unknown. Targets open-ended code investigation.

3. **[#5895](https://github.com/QwenLM/qwen-code/pull/5895) — Daemon session artifact APIs**  
   Agents can attach structured metadata to tool results, surfaces artifacts after execution, and allows listing/removal — foundational for traceable agent workflows.

4. **[#6189](https://github.com/QwenLM/qwen-code/pull/6189) — Nested sub-agents up to configurable depth**  
   Enables sub-sub-agents with a `maxSubagentDepth` setting (default 5). Followed by PR #6191 which renders the nesting as a TUI tree.

5. **[#5953](https://github.com/QwenLM/qwen-code/pull/5953) — LSP Server hot reload**  
   Detects `.lsp.json` changes mid-session and reloads LSP servers without restarting, closing a long-standing UX gap.

6. **[#6192](https://github.com/QwenLM/qwen-code/pull/6192) — Preserve OpenAI reasoning as raw thoughts**  
   Fixes parsing of `reasoning_content` from OpenAI-compatible streams. Related to Issue #6175.

7. **[#5928](https://github.com/QwenLM/qwen-code/pull/5928) — `todosDirectory` for project-local todo persistence**  
   Allows todos to live inside `.qwen/todos` for Git-tracked, team-shared task state. Mirrors the existing `memoryDirectory` pattern.

8. **[#6128](https://github.com/QwenLM/qwen-code/pull/6128) — Web-shell list-dialog overhaul (keyboard nav & a11y)**  
   Full keyboard navigation, IME-safe search, and ARIA roles across model, theme, approval, and tool dialogs. Closed after merge.

9. **[#6210](https://github.com/QwenLM/qwen-code/pull/6210) — WeCom channel adapter**  
   Adds Enterprise WeChat support with callback verification, envelope normalization, and shared channel base routing. Responds to the growing channels ecosystem.

10. **[#6216](https://github.com/QwenLM/qwen-code/pull/6216) — UTF-8 prefix for `cmd.exe` on Windows**  
    Prevents garbled output on non-UTF-8 code pages by applying a UTF-8 prefix before shell commands. Addresses Issue #6214.

## Feature Request Trends

- **Multi-channel communication** — Integration requests for WeCom, DingTalk, QQ Bot, and Enterprise WeChat are the dominant trend, with the channels subsystem maturing from Slack-only to multi-adapter.
- **Background automation & scheduling** — `/schedule` daemon (#6112), cron/loop job configurability (#6167), and daemon-managed channel workers (#5976) indicate strong demand for headless, recurring agent tasks.
- **Sub-agent & agent tree visibility** — Nested sub-agents (#6189, #6191) and artifact APIs (#5895) point toward hierarchical agent orchestration as a key direction.
- **Vision model support** — Requests for vision bridge model selection (#6195) and related UI support signal multimodal use cases becoming mainstream.

## Developer Pain Points

1. **Windows compatibility** — Recurring issues with non-UTF-8 console code pages, missing sandbox seatbelt profiles, and npm packaging flags highlight persistent Windows friction.
2. **Context window and token management** — Incorrect context window calculation (#6144), high system prompt overhead (~22K tokens for minimal input, #6097), and streaming idle timeout defaults plague users with long or complex sessions.
3. **Configuration persistence** — `/auth` changes not carrying to new sessions (#5979) erodes trust in session isolation guarantees.
4. **Mobile & web-shell performance** — Session switching jank (#6181) and uncompressed history loads degrade the mobile experience significantly.
5. **Distribution lag** — Both Homebrew (#6187) and Taobao mirror (#6218) lag behind npm releases, causing user confusion when upgrade prompts don't match available versions.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>

# DeepSeek TUI Community Digest — 2026-07-03

## Today's Highlights

The v0.8.67 release cycle is in full swing, with a major focus on stabilizing Fleet (sub-agent orchestration) and improving Windows reliability. Two critical fixes landed today—a recursion-depth ceiling for Fleet workers and a concurrent-persist corruption fix for sub-agent state. The community is also seeing active work on rules-directory auto-discovery, performance hot-path optimization, and the guided constitution creator.

## Releases

None in the last 24 hours.

## Hot Issues

1. **#3793 — [OPEN] Guided localized constitution creator**  
   *Creator flow should be language-first, with a guided-plus-open-canvas shape. Importantly, autonomy/risk posture must not directly flip runtime security settings from inside the constitution file.*  
   [GitHub](https://github.com/Hmbown/CodeWhale/issues/3793) | 14 comments

2. **#1812 — [OPEN] TUI-freeze-Windows-crossterm-poll**  
   *Intermittent UI freeze on Windows 11 — process stays alive but completely unresponsive. Two captured events with logs and thread-state analysis.*  
   [GitHub](https://github.com/Hmbown/CodeWhale/issues/1812) | 10 comments

3. **#3867 — [CLOSED] Project-scope instructions overly denied**  
   *Multi-project workflow blocker: no glob support, no rules-directory auto-discovery, and hard-blocked instruction config since v0.8.8.*  
   [GitHub](https://github.com/Hmbown/CodeWhale/issues/3867) | 7 comments

4. **#3792 — [OPEN] First-run onboarding feels like editing config**  
   *Recommended flow: Welcome detection → Language first → Setup → Constitution → TUI launch. Must not mix constitutional text with enforced runtime security controls.*  
   [GitHub](https://github.com/Hmbown/CodeWhale/issues/3792) | 7 comments

5. **#1607 — [OPEN] Token cost estimation: add CNY and other currencies**  
   *Suggestion to add RMB ¥ and other currency units to the token cost estimator. Community shows moderate interest.*  
   [GitHub](https://github.com/Hmbown/CodeWhale/issues/1607) | 6 comments

6. **#2261 — [OPEN] TUI crash leaks input to PowerShell terminal**  
   *After AI reply, input focus lost — keystrokes leak to PowerShell as cmdlet execution. Windows 10/11, codewhale v0.8.44.*  
   [GitHub](https://github.com/Hmbown/CodeWhale/issues/2261) | 5 comments

7. **#1835 — [OPEN] IME composition event deadlock on Windows**  
   *Input field completely unresponsive with Chinese IME (Sogou) on Windows 10. Cross-referenced with other Windows input issues.*  
   [GitHub](https://github.com/Hmbown/CodeWhale/issues/1835) | 4 comments | 1 👍

8. **#1678 — [OPEN] Feature request: in-app update checker with GitHub link**  
   *Users want auto-update checking and a direct GitHub link from within the TUI.*  
   [GitHub](https://github.com/Hmbown/CodeWhale/issues/1678) | 4 comments

9. **#2934 — [OPEN] Sidebar sessions panel with auto-resume**  
   *Currently no persistent sidebar for sessions — only Ctrl+R popup or --continue flag. Friction for multi-session workflows.*  
   [GitHub](https://github.com/Hmbown/CodeWhale/issues/2934) | 4 comments

10. **#3932 — [OPEN] Fleet agent tool lacks model-class vocabulary**  
    *Agent tool schema exposes no role/model_class choice, and constitution never mentions Fleet routing — making multi-model deployment impossible.*  
    [GitHub](https://github.com/Hmbown/CodeWhale/issues/3932) | 2 comments

## Key PR Progress

1. **#3892 — [CLOSED] Auto-discover .codewhale/rules/ and .claude/rules/**  
   *Solves #3867: scans both directories on session start, supports `*.mdc`, `*.md`, and `*.txt`, 15+ unit tests.*  
   [GitHub](https://github.com/Hmbown/CodeWhale/pull/3892)

2. **#3931 — [CLOSED] Enforce absolute recursion-depth ceiling; widen task-id entropy**  
   *Two correctness fixes: hard 3-level recursion cap and 8→12 hex-char task IDs. Confirmed global admission cap (100/200 agents) is working.*  
   [GitHub](https://github.com/Hmbown/CodeWhale/pull/3931)

3. **#3936 — [CLOSED] Unique temp path per atomic state write**  
   *Fixes concurrent-persist corruption: each thread now writes to a unique `.tmp` path before `rename`.*  
   [GitHub](https://github.com/Hmbown/CodeWhale/pull/3936)

4. **#3902 — [OPEN] Fix five render/input hot paths**  
   *Eliminates double-rendering in Tasks sidebar, redundant calls in TrailingPanel, cached TerminalMode lookups, early-exit composer input handling, and simplified sub-agent status diff.*  
   [GitHub](https://github.com/Hmbown/CodeWhale/pull/3902)

5. **#3895 — [CLOSED] Report local worker RSS in host status**  
   *Adds `memory_mb` to FleetHostWorkerStatus for running LocalProcess workers, enabling memory-aware observability.*  
   [GitHub](https://github.com/Hmbown/CodeWhale/pull/3895)

6. **#3901 — [CLOSED] Salvage local worker memory reporting**  
   *Takes over #3895 with CI fix: samples per-worker RSS via `ps -o rss=`, surfaces as `memory_mb`.*  
   [GitHub](https://github.com/Hmbown/CodeWhale/pull/3901)

7. **#3643 — [CLOSED] Setup summary wizard step for MCP/skills/plugins**  
   *First step of v0.8.67 setup wizard: displays MCP server status, skills directory info, plugin state in a scrollable TUI modal.*  
   [GitHub](https://github.com/Hmbown/CodeWhale/pull/3643)

8. **#3873 — [CLOSED] Remove unused execpolicy amend module**  
   *Cleanup: drops unused TUI execpolicy module and direct fd-lock dependency.*  
   [GitHub](https://github.com/Hmbown/CodeWhale/pull/3873)

9. **#3865 — [CLOSED] Persist sub-agent state to .codewhale/ instead of .deepseek/**  
   *Fixes rebrand-era fallback that kept using legacy `.deepseek/` path.*  
   [GitHub](https://github.com/Hmbown/CodeWhale/pull/3865)

10. **#3784 — [CLOSED] Config persistence for GUI config panel**  
    *Adds nested-table config key persistence and fixes `allow_shell` type bug for GUI panel.*  
    [GitHub](https://github.com/Hmbown/CodeWhale/pull/3784)

## Feature Request Trends

- **Project-scope rules & instructions**: Strong demand for glob-based rules, auto-discovery of `.codewhare/rules/` directories, and per-project instruction support (see #3867, now closed by #3892).
- **Guided onboarding & constitution creator**: Users want a step-by-step wizard, not a blank config editor — language-first, with clear separation between constitution text and runtime security settings (#3793, #3792).
- **Session management UX**: Persistent sidebar with session list, auto-resume, and history browsing (#2934).
- **Multi-currency token cost estimation**: Adding CNY and other currencies to cost estimates (#1607).
- **In-app updates**: Auto-update checker and GitHub link from within the TUI (#1678).
- **Slash command infrastructure**: A recurring theme of making slash commands visible, documented, localized, and durable across sessions (#1887-#1897 cluster).

## Developer Pain Points

- **Windows stability**: Chronic issues with TUI freezing on Windows 11 (#1812), IME deadlocks (#1835), and input leaking to PowerShell (#2261, #1338). These are the most-requested fixes by frequency.
- **Fleet memory management**: The 15+ GB memory consumption report for Fleet workers (#3882) prompted a release-blocker fix and ongoing work on recursion limits and per-worker memory reporting.
- **Sub-agent concurrency**: Multiple bugs from concurrent state persistence (#3936) and thread-safe worker termination were uncovered during the Fleet orchestration hunt.
- **Missing model-routing vocabulary**: The Fleet agent tool schema has no way to specify which model class to use for a task, making multi-model deployment impossible (#3932).
- **Visual rendering glitches**: Border rendering issues in settings (#1165), mouse scroll only showing user messages (#1512), and wrapped text copy including visual line breaks (#1853).

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*