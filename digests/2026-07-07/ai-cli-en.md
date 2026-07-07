# AI CLI Tools Community Digest 2026-07-07

> Generated: 2026-07-07 02:08 UTC | Tools covered: 9

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
**Analysis Date:** 2026-07-07

---

## 1. Ecosystem Overview

The AI CLI tools landscape in July 2026 is characterized by rapid iteration cycles, maturing agent orchestration primitives, and a growing gap between user expectations and platform reliability. Claude Code and OpenAI Codex lead in community size and issue velocity, while Gemini CLI and Copilot CLI show steady, incremental progress. A notable emerging cluster—Kimi Code CLI, OpenCode, Pi, Qwen Code, and DeepSeek TUI—represents a second wave of specialized tools targeting niche workflows (Asian-language support, Code Mode scripting, local model integration). Across all tools, the dominant pain points converge on agent reliability (false success reporting, hangs, token waste), session state management (context leaks, compaction fragility), and safety filter overreach disrupting legitimate development workflows.

---

## 2. Activity Comparison

| Tool | Hot Issues (Today) | Open PRs | Release Activity (24h) | Community Temperature |
|---|---|---|---|---|
| **Claude Code** | 10 (high severity) | 3 active | ✅ v2.1.202 shipped | High: safety filter crisis, nested agent bugs |
| **OpenAI Codex** | 10 (2 critical) | 10 active | ✅ rust-v0.143.0-alpha.37 | High: reasoning-token clustering, rate-limit volatility |
| **Gemini CLI** | 10 (1 most-upvoted) | 9 active | ✅ v0.51.0-nightly | Moderate: agent hangs, false success reports |
| **Copilot CLI** | 10 (mixed severity) | 0 active | ✅ v1.0.69-2 patch | Moderate: auth state leaks, voice mode broken |
| **Kimi Code CLI** | 2 (both new) | 0 active | ❌ No release | Low: limited community engagement |
| **OpenCode** | 10 (1 high-vote) | 10 active | ✅ v1.17.14 shipped | High: billing disputes, Windows regressions |
| **Pi** | 10 (3 critical) | 10 active | ❌ No release | Moderate: extension lifecycle, cache accounting |
| **Qwen Code** | 10 (2 critical) | 10 active | ✅ v0.19.6-nightly | High: zombie sessions, OAuth free tier controversy |
| **DeepSeek TUI** | 10 (systematic review) | 5 active | ❌ RC merged, not tagged | High: 18-issue review tracker, constitution violations |

**Key Observations:**
- Claude Code, OpenCode, and Qwen Code shipped releases today; DeepSeek TUI merged an RC but hasn't tagged
- OpenAI Codex leads in PR throughput (10 active); Copilot CLI had zero PR activity
- DeepSeek TUI's 18-issue systematic review tracker is the most structured quality initiative seen across all tools
- Kimi Code CLI shows the lowest community engagement with only 2 issues

---

## 3. Shared Feature Directions

### Multi-Account & Multi-Environment Management
| Tool | Specific Need | Reference |
|---|---|---|
| **Claude Code** | Multi-account profile switching in Desktop (#18435, 635 👍) | Top community ask |
| **Claude Code** | Multi-workspace Slack connector (#44243, 64 👍) | |
| **Copilot CLI** | Project-scoped plugins (#1665, 18 👍) | Per-repo vs global |
| **Qwen Code** | Multi-workspace daemon support (#6378, RFC) | Phase 2a foundation PR merged |
| **Gemini CLI** | Implicitly via subagent orchestration gaps | Workflow reliability |

### Agent Orchestration & Recovery
| Tool | Specific Need | Reference |
|---|---|---|
| **Claude Code** | Nested subagent ownership breaks after session boundaries (#75043) | Critical ownership bug |
| **OpenAI Codex** | Dynamic nested AGENTS.md loading (#12115, 83 👍) | Context scoping |
| **Gemini CLI** | Subagent MAX_TURNS reported as success (#22323) | False success |
| **DeepSeek TUI** | Managed token-budget exhaustion recovery (#4053) | Systematic failure catalog |
| **Qwen Code** | Zombie sessions with no logging (#5964) | 30M token waste |
| **Copilot CLI** | Multi-agent workflow system (#1389, 17 👍) | Specialized roles |

### Rate-Limit Transparency & Cost Control
| Tool | Specific Need | Reference |
|---|---|---|
| **Claude Code** | Agent over-spawning (#66867), resume inefficiency (#74599) | Growing cost cluster |
| **OpenAI Codex** | Context compaction burns resets (#31033), daily limit regression (#31322) | #1 trust issue |
| **Kimi Code CLI** | Expose usage limits via ACP (#2486) | IDE integration need |
| **Qwen Code** | Zombie sessions, `/review` token burn (#6264) | Real monetary loss |
| **OpenCode** | Charged for content-filter-blocked output (#35644) | Billing dispute |

### Safety Filter Overreach
| Tool | Specific Need | Reference |
|---|---|---|
| **Claude Code** | Opus 4.8 cybersecurity filter blocks directory listing, debug work (#75062–#75080) | 7+ issues, server-side, no override |
| **OpenCode** | Charged for blocked output, no human support (#35643–#35645) | Compliance cluster |
| **Gemini CLI** | Model uses destructive operations (`git reset --force`, `rm -rf`) (#22672) | Safety concern |
| **DeepSeek TUI** | Constitution non-adherence (#4032) | 22 comments |

### Session State & Context Isolation
| Tool | Specific Need | Reference |
|---|---|---|
| **Claude Code** | Workflow resume re-executes successful agents (#74599) | Resume inefficiency |
| **OpenAI Codex** | Automatic context compaction destroys sessions (#31033) | Critical |
| **Copilot CLI** | Memories leaking between repositories (#3945) | Privacy risk |
| **OpenCode** | Prompt leaks between sessions (#35587) | Isolation failure |
| **Pi** | Extension loading inconsistent across restart vs `/new` (#6380) | Lifecycle fragility |
| **Qwen Code** | Inability to rewind after compression (#6318) | Session management friction |

### Code Agent Reliability
| Tool | Specific Need | Reference |
|---|---|---|
| **Claude Code** | Model override dropped after continuation (#68147) | Costly waste |
| **OpenAI Codex** | GPT-5.5 reasoning-token clustering (#30364) | Degraded performance |
| **Gemini CLI** | Generalist agent hangs indefinitely (#21409) | Most-upvoted issue |
| **DeepSeek TUI** | Sub-agents complete with empty output (#4050) | Silent token waste |

### Real-Time Feedback & UX
| Tool | Specific Need | Reference |
|---|---|---|
| **Claude Code** | Streaming bash output in VS Code (#14280, 66 👍) | IDE pain point |
| **OpenAI Codex** | Stale message replies in multi-turn (#8648) | Persistent regression |
| **Copilot CLI** | Voice mode ASR models fail silently (#4024) | Feature blocker |
| **Kimi Code CLI** | Terminal display corruption on Windows 11 (#2485) | Showstopper |
| **Pi** | Escape stuck in Working state from extension hooks (#6234) | TUI stalling |
| **Qwen Code** | Garbled text on Windows legacy code pages (#6214) | Platform parity |

---

## 4. Differentiation Analysis

### Feature Focus Differences

| Dimension | Claude Code | OpenAI Codex | Gemini CLI | Copilot CLI | OpenCode | Pi | Qwen Code | DeepSeek TUI |
|---|---|---|---|---|---|---|---|---|
| **Primary differentiator** | Deep agent orchestration, workflow pipelines | Large model reasoning (GPT-5.5), Rust performance | Multi-model agnosticism, sandbox security | GitHub ecosystem integration, MCP protocol | Code Mode scripting runtime, V2 architecture | Extension API maturity, provider extensibility | Daemon-based multi-workspace, Asian-language first | Constitution-guided agents, systematic review culture |
| **Agent model** | Nested subagents with ownership hierarchy | Flat agent with tool-calling | Subagent delegation with bash affinity | Collaborative multi-agent teams (requested) | Task-based orchestration via MCP adapter | Extension-driven agent lifecycle | Flat agent + deferred tools | Manager-owned fan-out/fan-in (goal) |
| **Safety approach** | Server-side content filters (over-blocking issue) | Rate-limit gating | Sandbox hardening (`~/.gitconfig` RO) | MCP permissions, auth state management | Content filter billing complaints | No prominent safety features | CI/CD bot policy enforcement | Written constitution (non-adherence issue) |
| **Platform investment** | VS Code integration focus | macOS-first, Linux performance | macOS sandbox, Wayland issues | Windows regression challenges | Windows ARM64 gaps, Linux Mint freezes | Linux/X11 regression (clipboard) | Windows parity (garbled text) | Cross-platform TUI |

### Target User Profiles

| Tool | Primary Users | Use Case Sweet Spot |
|---|---|---|
| **Claude Code** | Professional software engineers, team leads | Complex agent orchestration, multi-step workflows |
| **OpenAI Codex** | Power users, AI researchers | Heavy reasoning tasks, large model experimentation |
| **Gemini CLI** | Platform-agnostic developers, security-conscious teams | Multi-model workflows, sandbox-required environments |
| **Copilot CLI** | GitHub ecosystem users, enterprise teams | Git-native workflows, MCP protocol integration |
| **Kimi Code CLI** | Asian-language developers (CN market) | Chinese localization, ACP-based IDE integration |
| **OpenCode** | Plugin developers, orchestration scripters | Code Mode runtime, V2 API extensibility |
| **Pi** | Extension authors, local model enthusiasts | Custom extensions, diverse provider backends |
| **Qwen Code** | Daemon-based workflow users, Asian-market | Multi-workspace serving, scheduled tasks |
| **DeepSeek TUI** | Workflow automation advocates, TUI enthusiasts | Constitution-guided automation, sub-agent orchestration |

### Technical Approach Differences

| Aspect | Claude Code | OpenAI Codex | Gemini CLI | Qwen Code |
|---|---|---|---|---|
| **Architecture** | Nested subagent hierarchy | Flat agent + tool-calling | Subagent delegation | Daemon-based, multi-workspace |
| **Session model** | Workflow-based (pipeline/parallel) | Context compaction | Session persistence with resume | Session isolation per workspace |
| **Memory system** | Auto memory (not detailed) | AGENTS.md loading | Auto Memory with cursor | AutoMemory with cursor |
| **Extension model** | MCP connectors, hooks | Skills, plugins | Custom skills, sub-agents | Plugins, Code Mode |
| **CI/CD integration** | GitHub Actions (limited) | Rust alpha builds | PR triage gate (strengthened) | PR triage gate (new) |

---

## 5. Community Momentum & Maturity

### High Momentum (Rapid Iteration, Active Community)

**Claude Code:** Shipping v2.1.202 today with dynamic workflow sizing, but community sentiment is strained by the safety filter crisis (7+ issues from one user, server-side halts, no override). The most-upvoted feature request (multi-account, 635 👍) dwarfs all other tools' top asks, indicating an engaged but demanding user base. The nested subagent ownership bug (#75043) and workflow resume inefficiency (#74599) are architectural issues that suggest the orchestration layer is still maturing.

**OpenAI Codex:** Despite being the most feature-rich, trust is eroding due to rate-limit volatility (#31033, #31322) and the GPT-5.5 reasoning-token clustering anomaly (#30364, 229 👍). The community is vocal about session state corruption and opaque quota management. However, PR throughput (10 active) and infrastructure improvements (session lifecycle, proxy routing) indicate sustained investment.

**Qwen Code:** Growing rapidly with a clear architectural vision (multi-workspace daemon, deferred-tool visibility). The zombie session (#5964) and bot hallucination (#6365) issues highlight growing pains, but the team ships frequently and responds to critical bugs within days. Community is split on the OAuth free tier controversy (#3203, 149 comments).

**DeepSeek TUI:** The most methodical quality initiative observed: an 18-issue systematic review tracker addressing root causes of sub-agent failures, token waste, and constitution violations. The maintainer's dogfooding culture and willingness to catalog failures transparently signals a maturing project. However, the community is smaller than the top-tier tools.

### Moderate Momentum (Steady Progress, Niche Focus)

**Copilot CLI:** Delivered a minor patch (v1.0.69-2) with MCP auth improvements, but zero PR activity and a backlog of Windows voice mode and hook reliability issues suggest slower iteration velocity. Project-scoped plugins (#1665, 18 👍) and custom model endpoints (#4003) are high-demand features with no visible implementation work.

**Gemini CLI:** Nightly releases with targeted fixes (sandbox hardening, escape sequence preservation), but the most-upvoted issue (#21409, agent hangs indefinitely, 8 👍) remains unresolved. The community is small but technically sophisticated, discussing AST-aware code analysis and MCP protocol expansion.

**Pi:** Heavy triage activity (25+ issues) but no release today. The constrained sampling PR (#6341) and cache accounting fixes are significant technical advances. Extension API maturity is the dominant theme, with users building production extensions that need finer-grained lifecycle hooks. Community is moderate in size but highly technical.

**OpenCode:** Shipped v1.17.14 with Code Mode MCP adapter and paginated catalog fixes, but billing disputes (#35643–35645) and Windows ARM64 fragility (#19130) are growing concern clusters. The V2 "gang-grill" cleanup is nearing completion, suggesting architectural consolidation.

### Low Momentum (Early Stage, Limited Engagement)

**Kimi Code CLI:** Only 2 issues updated today, zero PR activity, no releases. The terminal corruption bug (#2485) has no maintainer response. Feature request for ACP usage data (#2486) is the only signal of future direction. This tool appears to be in a maintenance lull or internal refocus.

---

## 6. Trend Signals

### 1. Agent Orchestration Reliability is the Defining Challenge

Across all tools, the inability to trust that sub-agents complete correctly is the #1 technical pain point. False success reporting (Gemini CLI #22323, DeepSeek TUI #4050), token waste on dead-end tool calls, and broken ownership hierarchies (Claude Code #75043) indicate that current agent orchestration models—whether nested, flat, or delegation-based—lack systematic failure detection and recovery. The industry needs **verifiable goal semantics** (did the agent actually achieve what was asked?) and **managed recovery paths** (what happens on token exhaustion, model hallucination, or timeout?).

**Implication for developers:** If building multi-agent workflows, invest in tracing, explicit success criteria, and fallback handlers. No tool today reliably handles deep orchestration.

### 2. Safety-Usability Tension is Boiling Over

Claude Code's cybersecurity filter crisis (7+ issues, server-side halts, no override) and OpenCode's billing disputes over blocked output represent a growing backlash against opaque, unconfigurable safety mechanisms. Users accept safety guardrails but demand:
- **Transparent audit trails** (why was this blocked?)
- **Graceful degradation** (warn vs halt)
- **User-configurable overrides** (with accountability)

The Gemini CLI sandbox approach (read-only `~/.gitconfig`, targeted hardening) and DeepSeek TUI's written constitution model represent contrasting philosophies—one technical, one behavioral.

**Implication for developers:** Safety systems that kill sessions without explanation or recourse will erode trust faster than they prevent harm. Consider warning-first architectures with user opt-out.

### 3. Multi-Account & Multi-Environment is the Top UX Request

Claude Code's #18435 (multi-account, 635 👍) is the single most-upvoted feature across all tools. Combined with Copilot CLI's project-scoped plugins (#1665), Qwen Code's multi-workspace daemon (#6378), and Claude Code's multi-workspace Slack connector (#44243), the message is clear: **developers operate across multiple organizational contexts and want tooling that mirrors their reality**. The era of single-account, global-config tools is ending.

**Implication for developers:** Design for context-switching from day one. Session identity, credential management, and config scoping (global/user/project) should be first-class primitives, not afterthoughts.

### 4. Cost Visibility is No Longer Optional

Zombie sessions burning 30M tokens (Qwen Code #5964), context compaction burning monthly resets (OpenAI Codex #31033), and the `/review` skill's excessive consumption (#6264) demonstrate that token accounting is a trust and retention issue. Users want:
- Per-session token budgets with kill switches
- Real-time cost dashboards in TUI/IDE
- Auditable token consumption logs

**Implication for developers:** If your tool has usage-based billing, implement per-session caps and real-time cost display. Users are increasingly unwilling to accept "wait and see" cost models.

### 5. Platform Parity is a Persistent Weakness

Windows users face terminal corruption (Kimi Code CLI #2485, Qwen Code #6214), missing features (Claude Code #48407, Copilot CLI #4024), and performance regressions (OpenCode #35611). Linux users deal with clipboard failures (Pi #6250) and Wayland crashes (Gemini CLI #21983). macOS users hit sandbox network restrictions (OpenAI Codex #12996) and malware warnings (#24246). **No tool provides a consistently excellent experience across all three major platforms.**

**Implication for developers:** If targeting enterprise adoption, Windows and Linux parity is a hard requirement. Testing against non-English locales and terminal emulators (Windows Terminal, xfce4-terminal, Wayland) should be part of the CI pipeline.

### 6. Extension/Plugin Ecosystems are Maturing, Creating New Fragility

As tools grow extension APIs (Pi's `before_provider_headers`, OpenCode's Code Mode, Copilot CLI's MCP tools), new failure modes emerge: extension hooks blocking TUI (#6234), inconsistent loading across restart vs `/new` (#6380), and plugin uninstall burning credits (#4032). The extension API surface is expanding faster than the reliability guarantees around it.

**Implication for developers:** If building an extensible tool, invest in hook lifecycle management (timeouts, cancellation, idempotency) and sandbox isolation. Extension authors need clear contracts and debugging tools.

---

## Summary

| Tool | Release Velocity | Community Size | Quality Maturity | Differentiator | Key Risk |
|---|---|---|---|---|---|
| Claude Code | High | Very Large | Medium | Agent orchestration depth | Safety filter overreach |
| OpenAI Codex | Medium | Large | Medium | Reasoning capabilities | Rate-limit instability |
| Gemini CLI | Medium | Medium | Medium | Sandbox security | Agent hangs |
| Copilot CLI | Low | Medium | Medium | GitHub integration | Windows/voice gaps |
| Kimi Code CLI | Low | Small | Low | Asian-language focus | Low engagement |
| OpenCode | High | Medium | Medium | Code Mode scripting | Billing disputes |
| Pi | Medium | Medium | High | Extension API | Windows/regression gaps |
| Qwen Code | High | Medium | Medium | Multi-workspace daemon | Token waste |
| DeepSeek TUI | Medium | Small | High | Systematic quality | Small community |

The AI CLI tools ecosystem in mid-2026 is entering a **reliability consolidation phase**: the excitement of initial capabilities is giving way to demands for predictability, transparency, and cost control. Tools that address safety-usability balance, session state integrity, and platform parity will retain their user base. Those that don't will see community migration to more dependable alternatives.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)

# Claude Code Skills Community Highlights Report
**Data Snapshot:** 2026-07-07 | **Source:** github.com/anthropics/skills

---

## 1. Top Skills Ranking

The following 7 Pull Requests represent the most-discussed Skill submissions, ranked by community engagement and cross-referenced with related Issues.

### #1: `skill-creator` — Fix `run_eval.py` 0% Recall Bug *(PR #1298)*
- **Author:** MartinCajiao | **Status:** Open | **Created:** 2026-06-10
- **Functionality:** Resolves a critical regression where the skill-creator's evaluation pipeline (`run_eval.py`, `run_loop.py`, `improve_description.py`) reports `recall=0%` for every skill description, rendering the optimization loop useless. Fixes installs the eval artifact as a real skill, corrects Windows stream reading, trigger detection logic, and parallel worker coordination.
- **Discussion Highlights:** Directly addresses Issue #556 (12 comments, 7 👍) and Issue #1169 (3 comments), both independently reproducing the 0% recall bug. The PR confirms 10+ independent reproductions. Community discussion focuses on the root cause: `claude -p` never triggers skills/commands because the eval artifact isn't properly registered as a skill.
- **🔗 https://github.com/anthropics/skills/pull/1298**

### #2: `document-typography` — Typographic Quality Control *(PR #514)*
- **Author:** PGTBoos | **Status:** Open | **Created:** 2026-03-04
- **Functionality:** Prevents orphan word wrap (1–6 words on a new line), widow paragraphs (section headers stranded at page bottom), and numbering misalignment in AI-generated documents. Addresses typographic issues that affect every document Claude generates but users rarely notice to request fixes for.
- **Discussion Highlights:** High engagement due to universality — every Claude user benefits. Discussion centers on whether typographic rules should be a skill or built into Claude's core document generation. Some commenters request configurable strictness levels.
- **🔗 https://github.com/anthropics/skills/pull/514**

### #3: `odt` — OpenDocument Text Creation & Template Filling *(PR #486)*
- **Author:** GitHubNewbie0 | **Status:** Open | **Created:** 2026-03-01
- **Functionality:** Creates, fills, reads, and converts OpenDocument Format files (.odt, .ods, .odf). Supports LibreOffice/OpenOffice ecosystem, ISO-standard document format, and template filling + ODT-to-HTML conversion.
- **Discussion Highlights:** Strong demand from enterprise and government users who require ODF compliance. Discussion includes requests for ODP (presentation) support and concerns about file size limits.
- **🔗 https://github.com/anthropics/skills/pull/486**

### #4: `testing-patterns` — Comprehensive Testing Skill *(PR #723)*
- **Author:** 4444J99 | **Status:** Open | **Created:** 2026-03-22
- **Functionality:** Covers the full testing stack: Testing Trophy model philosophy, unit testing with AAA pattern, React component testing via Testing Library, E2E testing with Playwright/Cypress, and API testing patterns.
- **Discussion Highlights:** Community debate on including specific framework defaults vs. keeping framework-agnostic. Requested additions: database testing patterns, snapshot testing guidance, and CI/CD integration examples.
- **🔗 https://github.com/anthropics/skills/pull/723**

### #5: `self-audit` — Mechanical Verification + Reasoning Quality Gate *(PR #1367)*
- **Author:** YuhaoLin2005 | **Status:** Open | **Created:** 2026-06-28
- **Functionality:** Audits AI output before delivery using a two-tier approach: (1) mechanical verification that every claimed output file exists, (2) four-dimension reasoning audit in damage-severity priority order. Universal across projects, tech stacks, and models.
- **Discussion Highlights:** Very recent submission with rapid engagement. Community excited about the "damage-severity priority" concept; requests for integration with existing CI pipelines. Some concern about token cost of the audit step.
- **🔗 https://github.com/anthropics/skills/pull/1367**

### #6: `color-expert` — Color Knowledge Skill *(PR #1302)*
- **Author:** meodai | **Status:** Open | **Created:** 2026-06-10
- **Functionality:** Self-contained color expertise covering naming systems (ISCC-NBS, Munsell, XKCD, RAL, Ridgway 1912, CSS named), color spaces with "what to use when" guidance (OKLCH for scales, OKLAB for gradients, CAM16 for perception), and color theory application.
- **Discussion Highlights:** Praised for its practical decision tables. Community requests additions: accessibility contrast checking, color-blindness simulation, and Pantone integration.
- **🔗 https://github.com/anthropics/skills/pull/1302**

### #7: `sensory` — Native macOS Automation via AppleScript *(PR #806)*
- **Author:** AdelElo13 | **Status:** Open | **Created:** 2026-03-29
- **Functionality:** Teaches Claude to use `osascript` (AppleScript) for native macOS automation instead of screenshot-based "computer use". Two-tier permission system: Tier 1 (direct app scripting, works out of box), Tier 2 (System Events UI scripting, requires Accessibility permissions).
- **Discussion Highlights:** Popular with Mac power users. Discussion centers on permission security boundaries and whether a similar Windows alternative (PowerShell automation) should be developed in parallel.
- **🔗 https://github.com/anthropics/skills/pull/806**

---

## 2. Community Demand Trends

Analysis of the top Issues reveals four distinct demand clusters:

### 🔒 Security & Trust Boundaries *(Issue #492 — 34 comments, 2 👍)*
The most-commented issue on the repository: community skills distributed under the `anthropic/` namespace impersonate official skills, creating a trust boundary vulnerability where users may grant elevated permissions to fraudulent skills. **Demand:** Namespace governance and skill signing.

### 🏢 Enterprise & Organizational Features *(Issue #228 — 14 comments, 7 👍)*
"Enable org-wide skill sharing in Claude.ai" — currently users must download `.skill` files and manually re-upload them. **Demand:** A shared skill library or direct sharing links for organizations.

### 🪟 Windows Compatibility *(Issues #1061, #556, #1169 — cumulative 18 comments)*
Multiple reports that `skill-creator` scripts are broken on Windows due to Unix-first assumptions: `PATHEXT` not honored, `cp1252` encoding issues, `select()` on pipes not supported. **Demand:** Linux/macOS parity for the skill development toolchain.

### 🎓 New Skill Proposals
- **compact-memory** *(Issue #1329)*: Symbolic notation for compact agent state, reducing context window consumption in long-running agents. Requested by 9 commenters.
- **agent-governance** *(Issue #412, closed)*: Safety patterns for AI agent systems — policy enforcement, threat detection, trust scoring, audit trails. Though closed, generated 6 comments and remains in demand.
- **MCP exposure** *(Issue #16)*: Expose Skills as MCPs (Model Context Protocol) for programmatic API consumption. 4 comments, no resolution.

---

## 3. High-Potential Pending Skills

These PRs have active discussion threads but have not yet been merged. They are likely to land based on community momentum:

| Skill | PR # | Author | Engagement | Likely Timeline |
|-------|------|--------|------------|-----------------|
| **self-audit** | #1367 | YuhaoLin2005 | 🔥 Rapid (newest) | 2–4 weeks (high interest, universal appeal) |
| **color-expert** | #1302 | meodai | 🔥 Active | 3–6 weeks (requires RFC-style review) |
| **testing-patterns** | #723 | 4444J99 | 🔥 Active | 4–8 weeks (scope discussion ongoing) |
| **sensory** (macOS) | #806 | AdelElo13 | 🔥 Active | 4–6 weeks (permission model under review) |
| **document-typography** | #514 | PGTBoos | 🔥 High | 6–10 weeks (design discussion) |
| **ODT skill** | #486 | GitHubNewbie0 | 🔥 High | 6–10 weeks (enterprise demand) |
| **skill-creator fixes** | #1298 | MartinCajiao | 🔥 Critical | 1–3 weeks (blocker for all skill authors) |

**Note:** Multiple skill-creator fix PRs (#1298, #1099, #1050, #1323) target the same core issue (Windows + 0% recall). The community may consolidate these into a single solution.

---

## 4. Skills Ecosystem Insight

**The community's most concentrated demand is for a production-ready, cross-platform skill-development toolchain that enables enterprise-grade quality control** — as evidenced by 5+ active PRs fixing the same `skill-creator` evaluation pipeline on Windows, alongside top-requested skills for document typography, testing patterns, output auditing, and organizational sharing, all pointing to a clear priority: making Skills reliable and deployable in real-world professional environments rather than experimental hobbyist projects.

---

# Claude Code Community Digest — 2026-07-07

## Today's Highlights
Anthropic shipped **v2.1.202** introducing a new "Dynamic workflow size" setting, giving developers advisory control over agent count in workflows. However, today's community discussion is dominated by a surge of **cybersecurity safety filter false positive reports** from user `sworrl`, alongside a critical **nested subagent ownership bug** that breaks agent orchestration after session boundaries. The most-voted open feature request remains **multi-account management in Claude Desktop**, now with 635 upvotes.

---

## Releases

**v2.1.202** (shipped today)
- Added **"Dynamic workflow size"** setting in `/config` (small/medium/large) — an advisory guideline for how many agents Claude spawns in dynamic workflows, not an enforced cap
- Added `workflow.run_id` and `workflow.name` OpenTelemetry attributes to telemetry payloads
- [View release](https://github.com/anthropics/claude-code/releases/tag/v2.1.202)

---

## Hot Issues (Top 10)

1. **[#18435 — Multi-account management in Claude Desktop](https://github.com/anthropics/claude-code/issues/18435)**  
   *125 comments, 635 👍* — The #1 community ask: easy profile switching for multiple Claude accounts on Desktop. No official response yet.

2. **[#48407 — Cowork tab missing on Windows 11](https://github.com/anthropics/claude-code/issues/48407)**  
   *38 comments* — Desktop app v1.2581.0 regressed the Cowork feature on Windows. High-impact for team users.

3. **[#62503 — Account restriction appeal redirect loop](https://github.com/anthropics/claude-code/issues/62503)**  
   *31 comments* — Affected users stuck in infinite redirects when trying to appeal account restrictions. Zero path to resolution.

4. **[#44243 — Multi-workspace Slack connector](https://github.com/anthropics/claude-code/issues/44243)**  
   *30 comments, 64 👍* — The built-in Slack MCP connector only supports one workspace. Consultants and multi-org devs blocked.

5. **[#14280 — Real-time bash output in VS Code](https://github.com/anthropics/claude-code/issues/14280)**  
   *20 comments, 66 👍* — Waiting for Claude to finish before seeing command output is a persistent IDE pain point.

6. **[#75043 — Nested subagent ownership breaks entirely](https://github.com/anthropics/claude-code/issues/75043)**  
   *New today, 3 comments* — Critical: subagents spawning subagents always run as async (ignoring `run_in_background`), completion notifications never reach parent, and `TaskStop` fails with ownership errors after resume. Breaks deep agent orchestration.

7. **[#75062–#75080 — Safety filter false positive deluge](https://github.com/anthropics/claude-code/issues/75062)**  
   *7+ issues filed today by sworrl* — Opus 4.8's cybersecurity filter is blocking routine work: directory listing, project status checks, frustrated exclamations, and personal drone firmware debugging. All reproducible server-side. Users cannot override; sessions are force-halted.

8. **[#68147 — Subagent model override dropped after continuation](https://github.com/anthropics/claude-code/issues/68147)**  
   *2 comments* — Explicit `model: "sonnet"` parameter on subagents is silently ignored after `SendMessage` follow-ups or compaction resumes. Costly waste when expensive models run unexpectedly.

9. **[#74599 — Workflow resume re-executes successful agents](https://github.com/anthropics/claude-code/issues/74599)**  
   *2 comments* — `resumeFromRunId` in `pipeline()`/`parallel()` workflows re-runs all `agent()` calls, not just failed ones. Destroys resume efficiency.

10. **[#75081 — One bad hook matcher disables all hooks silently](https://github.com/anthropics/claude-code/issues/75081)**  
    *New today* — A single schema-invalid `matcher` in `settings.json` causes the entire hooks configuration to be silently discarded. No errors, no warnings — hooks just stop firing.

---

## Key PR Progress

1. **[#41453 — Safe Stop hook wrapper with PID lock & timeout](https://github.com/anthropics/claude-code/pull/41453)**  
   Reference implementation for running post-session background tasks without the runaway process problem described in #41393.

2. **[#74857 — Clarify plugin MCP configuration scope](https://github.com/anthropics/claude-code/pull/74857)** *(Closed)*  
   Docs fix: plugin `mcpServers` is separate from user-level MCP allow/deny in `~/.claude.json`. Resolves configuration confusion.

3. **[#74722 — Conventional Branch naming in /commit-push-pr](https://github.com/anthropics/claude-code/pull/74722)**  
   Adds `conventional` argument to `/commit-push-pr` that auto-names branches per Conventional Branch 1.0.0 spec (feature/bugfix/hotfix/chore/docs/test).

---

## Feature Request Trends

**Top community-requested directions:**
- **Multi-account & multi-environment management** — #18435 (635 👍) for profile switching, #44243 (64 👍) for multi-workspace Slack, #75063 for household/family plans
- **Real-time feedback in IDE** — #14280 (66 👍) for streaming bash output, #73654 for sub-agent model exposure in status lines
- **UI customization** — #70104 for session group reordering/pinning in sidebar, #75048 for reducing jargon/responses in Fable models
- **Cost control transparency** — Growing cluster of issues around agent over-spawning (#66867), resume inefficiency (#74599), and model override drops (#68147)

---

## Developer Pain Points

- **Safety filter over-blocking** — A major flare-up today: multiple reports that Opus 4.8's cyber safeguard halts legitimate work (directory examination, project status queries, even frustrated exclamations). No bypass available; sessions are terminated server-side.
- **Subagent & workflow flakiness** — Nested agent ownership breaks (#75043), model overrides silently lost after continuation (#68147), and workflow resume re-executes successful work (#74599). Agent orchestration reliability is a growing frustration.
- **Windows/desktop regressions** — Cowork tab missing (#48407), UTF-8 surrogates JSON errors (#64777, #69781) suggest Windows-specific quality gaps.
- **Hook system fragility** — One invalid matcher disables all hooks silently (#75081), and successful SessionStart hooks show misleading "Failed with non-blocking status code" (#66952). Configuration is opaque.
- **Slack workspace limits** — The built-in connector remains single-workspace-only, blocking multi-org consultants and enterprise users who operate across tenants.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

# OpenAI Codex Community Digest — 2026-07-07

## Today’s Highlights
A critical behavioral bug in GPT-5.5 Codex has been uncovered: the model’s reasoning-token output is clustering at fixed boundaries (516/1034/1552), degrading performance on complex tasks. Meanwhile, the team is making infrastructure progress with a new Rust alpha release and a stacked series of PRs to improve session lifecycle management, proxy routing for inference traffic, and cross-platform CI performance. Developer sentiment remains strained over persistent rate-limit volatility and context compaction that breaks long sessions.

## Releases
**rust-v0.143.0-alpha.37** released. No changelog details beyond version bump.

## Hot Issues

1. **[#30364 – GPT-5.5 Codex reasoning-token clustering degradation](https://github.com/openai/codex/issues/30364)**  
   *Tags: bug, model-behavior, rate-limits*  
   Community-discovered anomaly: `gpt-5.5` responses cluster at 516, 1034, and 1552 reasoning tokens. The reporter suspects a model-level constraint causing degraded task performance. With 131 comments and 229 upvotes, this is the top community concern — likely an API-side model issue requiring OpenAI intervention.

2. **[#8648 – Codex replies to earlier messages instead of latest](https://github.com/openai/codex/issues/8648)**  
   *Tags: bug, context, agent*  
   Ongoing for six months: Codex responds to stale messages in multi-turn conversations. 87 comments; a persistent UX regression for heavy chat users.

3. **[#12115 – Dynamic loading of nested AGENTS.md](https://github.com/openai/codex/issues/12115)**  
   *Tags: enhancement, context, CLI*  
   Request for Claude-Code-style per-directory AGENTS.md loading. 83 upvotes — strong community appetite for smarter context resolution in monorepos.

4. **[#12862 – CLI `--worktree` and `--tmux` flags](https://github.com/openai/codex/issues/12862)**  
   *Tags: enhancement, TUI*  
   Proposal for one-command isolated git worktree + tmux sessions. 85 upvotes; reflects demand for reproducibility in agentic workflows.

5. **[#30440 – Codex uses bundled pnpm instead of host toolchain](https://github.com/openai/codex/issues/30440)**  
   *Tags: bug, sandbox, app*  
   Sandbox environment ignores host package manager. Blocks builds that depend on system-installed toolchains; 18 comments.

6. **[#31033 – Context automatically compacted / “RUINS SESSIONS”](https://github.com/openai/codex/issues/31033)**  
   *Tags: bug, rate-limits, context*  
   Users report automatic context compaction burning through rate-limit resets. User reported “consumed 2 resets and 50% of monthly limit in one session” — critical for power users.

7. **[#31322 – Usage limits regressed after morning normalization](https://github.com/openai/codex/issues/31322)**  
   *Tags: bug, rate-limits*  
   Daily volatility: limits normalized in morning, then drained 5x faster by evening. Indicates server-side allocation instability.

8. **[#23574 – VS Code extension allocates ~1M inotify watches](https://github.com/openai/codex/issues/23574)**  
   *Tags: bug, extension, performance*  
   Linux users hit the system inotify watch limit on large workspaces. Enterprise blocker for monorepo users.

9. **[#20683 – Computer Use crashes on Outlook macOS](https://github.com/openai/codex/issues/20683)**  
   *Tags: bug, computer-use*  
   `SkyComputerUseService` crashes when inspecting Outlook. 13 comments; affects macOS productivity workflows.

10. **[#20312 – Native event-driven session wake primitive](https://github.com/openai/codex/issues/20312)**  
    *Tags: enhancement, agent*  
    Request for agents to wake on external events (chat mentions, file changes, MCP pushes) rather than requiring manual input. Core missing primitive for agent-as-service patterns.

## Key PR Progress

1. **[#31337 – Fix Codex environment setup table](https://github.com/openai/codex/pull/31337)**  
   Restores missing `[setup]` table in environment.toml, fixing worktree creation on fresh clones.

2. **[#30854 – Block selected merge drivers before three-way patch](https://github.com/openai/codex/pull/30854)**  
   Security hardening: prevents repository-controlled Git config from running custom merge drivers during `git apply --3way`.

3. **[#31306 – Sequential cutoff reasoning summaries](https://github.com/openai/codex/pull/31306)**  
   Adds `reasoning_summary_delivery = "sequential_cutoff"` behind a feature flag, improving reasoning summary rendering order.

4. **[#31335 – Route Responses API through system proxy](https://github.com/openai/codex/pull/31335)**  
   First inference path to respect OS proxy settings — critical for enterprise users behind corporate firewalls.

5. **[#31338 – Couple thread activity to submissions](https://github.com/openai/codex/pull/31338)**  
   Prevents session teardown from erasing completion barriers by tying thread activity lifecycle to submission reservations.

6. **[#31333 – Track thread publication lifecycle](https://github.com/openai/codex/pull/31333)**  
   Introduces `ThreadId`-scoped registration with incarnation generation, preventing stale handle mutations.

7. **[#31334 – Align skill creator paths with supported locations](https://github.com/openai/codex/pull/31334)**  
   Documents and enforces skill storage locations: `.agents/skills` (project), `$HOME/.agents/skills` (user), `/etc/codex/skills` (admin).

8. **[#31274 – Externally provided Codex auth](https://github.com/openai/codex/pull/31274)**  
   In-memory auth snapshot with explicit runtime capabilities, enabling custom auth provider integration.

9. **[#31288 – Consume managed layers with v2 cache](https://github.com/openai/codex/pull/31288)**  
   Part 4/5 of the managed layers migration: switches from legacy `enterprise_managed` to authoritative `managed_layers` configuration.

10. **[#31321 – Update V8 for Chromium 149.0.7827.201](https://github.com/openai/codex/pull/31321)**  
    Security patch update for the embedded V8 engine — routine maintenance with security fixes.

## Feature Request Trends

- **Dynamic context loading**: Multiple requests (e.g., #12115, #20312) for per-directory AGENTS.md, event-driven session wake, and automatic context expansion. Community wants Codex to intelligently scope context without manual management.
- **Isolated/controlled agent sessions**: Requests for `--worktree`/`--tmux` flags (#12862), repository-level sandboxing, and reproducible session snapshots. Growing need for deterministic agent environments.
- **Rate-limit transparency**: Users demand detailed expiry dates, per-source usage breakdowns, and reset-credit visualization (#29618). The rate-limit volatility (#31322) is eroding trust in quota management.
- **Skill and plugin lifecycle management**: Cleaner skill storage paths (#31334), nested AGENTS.md loading, and better hook-based user instructions (#30138–30141).

## Developer Pain Points

- **Rate-limit instability is the #1 trust issue**: Two top-voted issues (#31033, #31322) describe context compaction and daily limit regression. Power users are burning $200/month Pro allowances unpredictably.
- **Session state corruption**: Ghost conversations (#29868), stale message replies (#8648), and failed archiving (#28276) suggest the session persistence layer is fragile under load.
- **macOS ecosystem friction**: Malware warnings (#24246), database access failures (#24006), and sandbox network restrictions (#12996) create a poor out-of-box experience on Apple Silicon.
- **Windows and Linux performance regressions**: Inotify exhaustion (#23574), stuck git polling processes (#29408), and CI build bottlenecks (#31339) signal inadequate platform-specific testing.
- **Toolchain sandbox conflicts**: Codex overriding pnpm (#30440) and injecting restricted network access (#12996) frustrates developers with established local tooling.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>

# Gemini CLI Community Digest — 2026-07-07

## Today's Highlights
The nightly release v0.51.0-nightly.20260707 ships two critical fixes: macOS sandbox hardening (making `~/.gitconfig` read-only) and escape sequence preservation in string literals for modern models. The community remains focused on agent reliability, with the top-voted issue about generalist agent hangs still demanding attention, while new PR activity around MCP elicitation and thought leakage mitigation signals progress on persistent quality concerns.

## Releases
**v0.51.0-nightly.20260707.g15a9429b6** — [View Release](https://github.com/google-gemini/gemini-cli/releases/tag/v0.51.0-nightly.20260707.g15a9429b6)
- **fix(sandbox):** `~/.gitconfig` is now read-only in the macOS sandbox, preventing sandboxed processes from modifying git configuration that could drive command execution via aliases or hooks.
- **fix(core):** Escape sequences (e.g., `\n`, `\t`) inside string literals are preserved for modern models (Gemini 2.x, 3.x), fixing file corruption when writing code containing valid escape patterns.

## Hot Issues
1. **[#22323 — Subagent MAX_TURNS reported as GOAL success](https://github.com/google-gemini/gemini-cli/issues/22323)** (10 comments, 2 👍)  
   Critical logic bug: `codebase_investigator` subagent reports `"success"` when it actually hit `MAX_TURNS` without doing any analysis. This misleads automated systems and creates false confidence in agent results. Community: "The termination reason should not be GOAL when the agent never executed."

2. **[#21409 — Generalist agent hangs indefinitely](https://github.com/google-gemini/gemini-cli/issues/21409)** (7 comments, 8 👍)  
   **Most upvoted issue.** Simple folder creation hangs when Gemini defers to the generalist agent. Workaround exists (disable subagents), but this blocks core UX. Community frustration: "I've waited up to an hour."

3. **[#19873 — Leverage bash affinity via zero-dependency OS sandboxing](https://github.com/google-gemini/gemini-cli/issues/19873)** (8 comments, 1 👍)  
   Strategic enhancement: Gemini 3 models are native bash users. Issue proposes OS-level sandboxing that allows native tool chaining without sacrificing security. Active discussion about tradeoffs between safety and model capability.

4. **[#25166 — Shell command hangs with "Waiting input" after completion](https://github.com/google-gemini/gemini-cli/issues/25166)** (4 comments, 3 👍)  
   Reproducible bug: simple commands like file listing finish execution but CLI shows them as still awaiting input. Blocks workflow automation. Community: "Happens for extremely simple shell commands."

5. **[#26522 — Auto Memory retries low-signal sessions indefinitely](https://github.com/google-gemini/gemini-cli/issues/26522)** (5 comments)  
   Memory system inefficiency: sessions not read by the extraction agent remain "unprocessed" forever, causing repeated re-prompts. No mechanism to mark low-signal sessions as skipped.

6. **[#21983 — Browser subagent fails on Wayland](https://github.com/google-gemini/gemini-cli/issues/21983)** (4 comments, 1 👍)  
   Browser agent terminates with "GOAL" on Wayland displays despite not achieving its goal. Platform-specific issue limiting Linux users.

7. **[#24246 — 400 error with >128 tools](https://github.com/google-gemini/gemini-cli/issues/24246)** (3 comments)  
   API limit issue: CLI crashes when more than 128 tools are enabled. Community expects smarter tool scoping rather than hard error. "I'd expect the agent to limit tools in scope."

8. **[#22672 — Agent should discourage destructive behavior](https://github.com/google-gemini/gemini-cli/issues/22672)** (3 comments, 1 👍)  
   Safety concern: model uses `git reset`, `--force`, and dangerous DB operations when safer alternatives exist. Community requests built-in safeguards for destructive operations.

9. **[#21968 — Gemini underutilizes custom skills and sub-agents](https://github.com/google-gemini/gemini-cli/issues/21968)** (6 comments)  
   Adoption gap: even with well-described custom skills (e.g., Gradle, Git), Gemini defaults to manual shell commands unless explicitly instructed to use agents. Community: "It will if I instruct it explicitly, but won't for related tasks."

10. **[#26525 — Add deterministic redaction for Auto Memory](https://github.com/google-gemini/gemini-cli/issues/26525)** (3 comments)  
    Security: Auto Memory sends transcript content to the extraction model *before* redaction happens. Logging also captures sensitive skill outputs. Community calls for pre-context redaction.

## Key PR Progress
1. **[#28301 — Nightly version bump](https://github.com/google-gemini/gemini-cli/pull/28301)**  
   Automated release chore for v0.51.0-nightly.20260707.

2. **[#28223 — Bypass LLM correction for JSON/IPYNB files](https://github.com/google-gemini/gemini-cli/pull/28223)** (OPEN)  
   Surgical fix: `write_file` and `replace` tools corrupt Jupyter Notebooks and JSON files due to aggressive LLM unescaping. This PR skips correction for known structured formats. **Critical for data science workflows.**

3. **[#28244 — Safe test command in policy engine docs](https://github.com/google-gemini/gemini-cli/pull/28244)** (OPEN)  
   Fixes [#28231](https://github.com/google-gemini/gemini-cli/issues/28231): replaces `rm -rf /` example with a safe test command in the policy engine quick-start guide. **Security hygiene improvement.**

4. **[#27971 — Strip thoughts from scrubbed history, resolve thought leakage](https://github.com/google-gemini/gemini-cli/pull/27971)** (OPEN)  
   Addresses model confusion: internal monologues leak into plain-text history, causing the model to emulate scratchpad thoughts or enter infinite loops. This PR surgically strips reasoning from visible history.

5. **[#28216 — Exclude CI credential files from workspace context](https://github.com/google-gemini/gemini-cli/pull/28216)** (OPEN)  
   Security: GitHub Actions credential JSON files (`gha-creds-*.json`) are now excluded from workspace context to prevent accidental exposure.

6. **[#28299 — Preserve escape sequences in string literals](https://github.com/google-gemini/gemini-cli/pull/28299)** (CLOSED — merged)  
   Fixes `\n`/`\t` corruption in files for modern models. Merged into nightly. **Shipped in today's release.**

7. **[#28221 — Make ~/.gitconfig read-only in macOS sandbox](https://github.com/google-gemini/gemini-cli/pull/28221)** (CLOSED — merged)  
   Hardens sandbox: removes `~/.gitconfig` from writable set, preventing git config-based command execution. **Shipped in today's release.**

8. **[#28089 — MCP elicitation (form + url) capability](https://github.com/google-gemini/gemini-cli/pull/28089)** (OPEN)  
   Implements MCP 2025-11-25 elicitation spec: client now advertises support for `form` and `url` modes, enabling interactive elicitation flows. **Major protocol compliance update.**

9. **[#28068 — Guard message inspectors against empty parts arrays](https://github.com/google-gemini/gemini-cli/pull/28068)** (CLOSED)  
   Fixes `isFunctionCall()` / `isFunctionResponse()` returning `true` for empty `parts` arrays (JS `[].every()` vacuously true). Prevents misclassification of model messages.

## Feature Request Trends
- **Agent orchestration & self-awareness**: Multiple issues request agents that understand their own capabilities (CLI flags, hotkeys, subagent trajectories) and proactively use available tools without explicit prompting.
- **AST-aware code analysis**: Interest in AST-based file reading, search, and codebase mapping to reduce token waste and improve navigation precision (tracked in [#22745](https://github.com/google-gemini/gemini-cli/issues/22745)).
- **Safety & destructive behavior guards**: Consistent demand for built-in protection against dangerous operations (force pushes, destructive DB commands, `rm -rf`), both via policy engine and agent-level discouragement.
- **MCP protocol expansion**: Continued pressure to align with latest MCP specs, including elicitation modes, form handling, and URL-based interactions.
- **Component-level evaluations**: Community wants structured benchmarks for subagent performance, trajectory visibility, and automated regression detection ([#24353](https://github.com/google-gemini/gemini-cli/issues/24353)).

## Developer Pain Points
- **False success reporting**: Subagents reporting "GOAL"/"success" when actually interrupted or failed (e.g., MAX_TURNS, Wayland crashes) erodes trust and breaks automated pipelines.
- **Hangs and indefinite waiting**: Shell command "Waiting input" ghosts and generalist agent freezes remain the highest-impact UX blockers, directly preventing basic automation.
- **Unwanted subagent activation**: Since v0.33.0, subagents activate even when disabled in config, forcing users to explicitly instruct against delegation.
- **Memory system inefficiency**: Auto Memory retries low-value sessions indefinitely, and secret redaction happens after content is already in model context, posing security risks.
- **Tooling limits**: Hard 128-tool cap causes 400 errors; no graceful degradation or automatic tool scoping exists.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

Here is the **Copilot CLI Community Digest** for **2026-07-07**.

---

## Copilot CLI Community Digest – 2026-07-07

**Data source:** github.com/github/copilot-cli

### 1. Today's Highlights
A minor patch release (v1.0.69-2) improves MCP server authentication via the CLI OAuth callback flow and fixes a file-inclusion bug related to the `n` directory. The community is actively discussing project-scoped plugins (Issue #1665, 18 👍) and a critical authentication state leak in ACP mode (Issue #3902). A new wave of triage issues highlights growing pain points in voice mode, Windows hook compatibility, and enterprise plugin sync.

### 2. Releases
**v1.0.69-2** (released last 24h)
- **Added:** Self-documentation for `/rubber-duck` in pre-auth help.
- **Improved:** MCP server sign-in now works through the CLI OAuth callback flow. The `/user` switch picker is no longer clipped when the timeline is full.
- **Fixed:** Files inside the `n` directory are now properly included.

### 3. Hot Issues (10 Noteworthy)
1. **[#1665 – Support Copilot CLI Plugins Scoped to Project/Repository](https://github.com/github/copilot-cli/issues/1665)** *(CLOSED)*
   *High demand (18 👍) for moving plugins from per-user global to per-project. Community wants teams to share tooling without polluting global config.*
2. **[#3596 – Error loading model list: Not authenticated on session resume](https://github.com/github/copilot-cli/issues/3596)** *(CLOSED)*
   *11 👍. Affects v1.0.56 when resuming specific sessions. Users must start a new session to list models—critical UX bug for session persistence.*
3. **[#3028 – MCP permissions configuration](https://github.com/github/copilot-cli/issues/3028)** *(OPEN)*
   *Users want a `trustedFolders`-like mechanism for MCP tools, mirroring existing file permission patterns for security.*
4. **[#1389 – Multi-Agent Workflow System](https://github.com/github/copilot-cli/issues/1389)** *(CLOSED)*
   *17 👍. Request for collaborative AI teams with specialized roles (architecture, dev, QA) to replace manual orchestration.*
5. **[#3074 – Add `/effort` command for reasoning effort](https://github.com/github/copilot-cli/issues/3074)** *(OPEN)*
   *6 👍. Users find `/model` multi-step for adjusting reasoning effort. A single command to toggle low/medium/high would streamline complex prompts.*
6. **[#4003 – Support custom model endpoint](https://github.com/github/copilot-cli/issues/4003)** *(OPEN)*
   *Feature parity with VS Code—allow local/private model endpoints, critical for enterprise air-gapped environments.*
7. **[#3945 – Memories leaking between repositories](https://github.com/github/copilot-cli/issues/3945)** *(OPEN)*
   *Disturbing privacy issue: Copilot injected memory facts from unrelated repos into a fresh clone, eroding trust in context isolation.*
8. **[#4034 – Hook subprocess stdin write-end hangs](https://github.com/github/copilot-cli/issues/4034)** *(CLOSED)*
   *`$(cat)` pattern in hooks hangs because stdin EOF is not sent for tool-use hooks. Patch incoming; affects automation workflows.*
9. **[#4038 – Non-interactive mode MCP server injects empty message](https://github.com/github/copilot-cli/issues/4038)** *(OPEN, triage)*
   *When MCP servers expose 7+ tools, the CLI blocks on a ghost empty turn, causing model to echo system prompts instead of answering.*
10. **[#4024 – Voice mode: all bundled ASR models fail silently](https://github.com/github/copilot-cli/issues/4024)** *(OPEN)*
    *Voice recording works, but all three bundled ASR models return empty transcriptions. Blocks the entire voice feature for affected users.*

### 4. Key PR Progress
No pull requests were updated in the last 24 hours. The development focus appears to be on issue triage and the v1.0.69-2 patch release.

### 5. Feature Request Trends
- **Plugin Scoping & Management:** The loudest request is for project/repository-scoped plugins (#1665), driven by team collaboration needs.
- **Custom Model Endpoints:** Parity with VS Code for BYO models and endpoints (#4003, #4037) is a recurring enterprise ask.
- **Voice & Multi-Modal:** Despite bugs (#4024), users clearly want voice interaction as a first-class feature, including custom ASR model support.
- **Local Memory & Agent Orchestration:** Security-conscious orgs want local-only memory (#2930), while power users want multi-agent workflows (#1389) and quick reasoning-effort controls (#3074).

### 6. Developer Pain Points
- **Authentication State Fragility:** Session resume loses auth state (#3596), and ACP mode never refreshes stale tokens (#3902)—both force workarounds like session restarts.
- **Nix & Non-Standard Shells:** The bash tool hangs on Nix shells (#1428), and Windows hook execution (#4001) breaks `.claude/settings.json` contracts (PS vs bash, missing env vars).
- **Hook & Plugin Reliability:** Hooks hang due to missing EOF (#4034), enterprise plugins never sync to disk (#4039), and plugin uninstall burns AI credits unnecessarily (#4032).
- **Context Leakage:** Memory leaking between repos (#3945) is a serious privacy/security concern that undermines user trust in context isolation.
- **Windows and Enterprise Gaps:** Voice installer fails on private NuGet feeds (#4035), desktop notifications broken on backgrounded tabs (#4036), and ACP auth stays stale (#3902) are blocking enterprise adoption.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

**Kimi Code CLI Community Digest**  
**Date:** 2026-07-07  
**Source:** [github.com/MoonshotAI/kimi-cli](https://github.com/MoonshotAI/kimi-cli)

---

### Today's Highlights

The past 24 hours saw no new releases or merged pull requests, but two open issues signal important community needs: a terminal display corruption bug on Windows 11 with Kimi Code CLI v0.22.0, and a feature request to expose usage limits and reset times through the ACP interface for IDE integration. The lack of PR activity suggests the maintainers may be focusing on internal work or an upcoming release.

---

### Releases

No new releases in the last 24 hours.

---

### Hot Issues

*Total: 2 items, both opened July 6, 2026.*

1. **[#2485] [bug] code cli 错乱 || code cli is confused**  
   *Author: mynameiscuining | Comments: 1 | 👍: 0*  
   User reports that after using Kimi Code CLI v0.22.0 on Windows 11 with the `kimi-for-coding` model, the terminal display becomes garbled and incomplete (e.g., first option missing). Screenshots indicate a layout corruption.  
   **Why it matters:** Terminal corruption breaks the core CLI experience and workflow; Windows 11 users on the Moderato plan are affected. No fix or maintainer acknowledgment yet.  
   [GitHub Issue](https://github.com/MoonshotAI/kimi-cli/issues/2485)

2. **[#2486] [enhancement] Feature Request: Expose Kimi Code usage limits and reset times through ACP**  
   *Author: jgiacomini | Comments: 0 | 👍: 0*  
   Developer building an ACP client for Visual Studio 2026 requests API endpoints to show usage limits and reset times (similar to the `/usage` console command). Currently ACP lacks this data for IDE integration.  
   **Why it matters:** Enables IDE plugin developers to display real-time quota info to users, improving transparency and UX. ACP is a key integration point for modern IDEs.  
   [GitHub Issue](https://github.com/MoonshotAI/kimi-cli/issues/2486)

---

### Key PR Progress

No pull requests were updated in the last 24 hours.

---

### Feature Request Trends

- **ACP Usage Data Exposure (1 issue):** Developers building IDE integrations (e.g., Visual Studio 2026) want programmatic access to usage limits and reset times via the Agent Communication Protocol (ACP). This is the only feature request this week and reflects a growing demand for embedding Kimi Code into development environments.

---

### Developer Pain Points

- **Terminal Corruption on Windows (1 issue):** The `#2485` bug report is the top pain point. Users on Windows 11 experience terminal display corruption after prolonged use, with missing UI elements. No workaround or response from maintainers yet. This is a showstopper for productivity.

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

# OpenCode Community Digest — 2026-07-07

## Today's Highlights
v1.17.14 ships with a new Code Mode MCP adapter and fixes for paginated MCP catalogs, while the V2 "gang-grill" cleanup parade continues with several closed tracker issues. A growing cluster of billing and content-filter disputes (#35643–35645) is drawing community attention, alongside reports of performance regressions on Windows after the update.

## Releases
**v1.17.14** — [Release](https://github.com/anomalyco/opencode/releases/tag/v1.17.14)
- **Core:** Added a Code Mode MCP adapter for running confined orchestration scripts against connected MCP tools; the `execute` tool is now hidden unless code mode is enabled.
- **Bugfixes:** Fixed paginated MCP tool catalogs losing tool metadata and output schema validation; preserved l…

## Hot Issues
1. **#8501 — [FEATURE]: Allow to expand pasted text** — *berenar* — [Issue](https://github.com/anomalyco/opencode/issues/8501)  
   *28 comments, 202 👍*  
   Users love collapsed paste previews but want the ability to expand `[Pasted ~1 lines]` for editing before submission. This is the highest-voted open feature request.

2. **#31119 — [BUG]: Error: no such column: name** — *AndrewShear* — [Issue](https://github.com/anomalyco/opencode/issues/31119)  
   *10 comments, 8 👍*  
   Returning users hit a database migration error after updating from 1.16.2. Suggests stale schema state without rollback protection.

3. **#19130 — Windows ARM64 native: OpenTUI fails to initialize** — *Carliquiss* — [Issue](https://github.com/anomalyco/opencode/issues/19130)  
   *8 comments*  
   Native ARM64 binary works for CLI but crashes on TUI init due to `bun:ffi dlopen TinyCC error`. Newest update (2026-07-07) indicates active triage.

4. **#34754 — The opencode funneling scam** — *Pachinko0* — [Issue](https://github.com/anomalyco/opencode/issues/34754)  
   *7 comments*  
   Heated UX dispute: users claim they were charged for "Zen" believing it was "GO" subscription. Closed without resolution; ongoing community concern.

5. **#34341 — V2: route progressive AGENTS.md through System Context** — *opencode-agent[bot]* — [Issue](https://github.com/anomalyco/opencode/issues/34341)  
   *6 comments*  
   Core V2 design issue: path-scoped `AGENTS.md` files injected as synthetic user messages have accidental lifetimes and can disappear. Blocking compaction semantics.

6. **#29175 — Direct child sessions hidden in parent session UI** — *ChamHerry* — [Issue](https://github.com/anomalyco/opencode/issues/29175)  
   *3 comments*  
   Plugin-created child sessions are invisible in TUI because discovery only scans native `task` tool metadata. Limits multi-agent plugin patterns.

7. **#35644 — Content filter charges users for blocked output** — *arshbuttar426-hue* — [Issue](https://github.com/anomalyco/opencode/issues/35644)  
   *1 comment, just opened*  
   Billing safeguard request: users pay full token cost for content-filter-blocked responses. Escalated alongside #35643 and #35645 as a compliance cluster.

8. **#35611 — Go models inference slow/stuck on Windows after v1.17.14** — *Kuromi-zyzy* — [Issue](https://github.com/anomalyco/opencode/issues/35611)  
   *2 comments*  
   Performance regression: Go subscription models hang at "thinking" in existing sessions post-update. New sessions work fine — suggests session state migration issue.

9. **#35587 — Prompt leaks between sessions** — *Blade1024* — [Issue](https://github.com/anomalyco/opencode/issues/35587)  
   *2 comments*  
   Command history from one session appears in another. Reproducible with two independent sessions using arrow-up recall.

10. **#35641 — TUI freezes mid-session on Linux Mint (X11)** — *sporteka2* — [Issue](https://github.com/anomalyco/opencode/issues/35641)  
    *1 comment*  
    Non-deterministic freeze on Cinnamon/X11 with xfce4-terminal. Likely terminal-level or SIGWINCH handling issue.

## Key PR Progress
1. **#35371 — [CLOSED] feat(core): add durable compaction barrier** — *kitlangton* — [PR](https://github.com/anomalyco/opencode/pull/35371)  
   Generalized session input into a typed durable inbox, enabling manual compaction barriers. Unblocks V2 progressive AGENTS.md routing.

2. **#35617 — [OPEN] feat(codemode): support promise chaining** — *rekram1-node* — [PR](https://github.com/anomalyco/opencode/pull/35617)  
   Adds `then`, `catch`, `finally` to sandbox promises; chainable `all`, `allSettled`, `race`. Strengthens Code Mode as a general orchestration runtime.

3. **#35634 — [OPEN] fix(provider): ensure required array in object schemas** — *ViNull008* — [PR](https://github.com/anomalyco/opencode/pull/35634)  
   Fixes `additionalProperties: false` tool schemas missing `required` field — strict validators reject `null`, causing tool call failures. Closes #35528.

4. **#35629 — [OPEN] feat(core): expose OpenCode API in Code Mode** — *rekram1-node* — [PR](https://github.com/anomalyco/opencode/pull/35629)  
   Registers the full V2 API under `tools.opencode.v2.*` for server-backed locations, enabling Code Mode scripts to call core OpenCode APIs via authenticated loopback.

5. **#35613 — [CLOSED] feat(plugin): tool.execute.before shortcircuit** — *jackieju* — [PR](https://github.com/anomalyco/opencode/pull/35613)  
   Plugin hooks can now return a canned `{ title, output, metadata }` to shortcircuit real tool execution. Useful for mocking, caching, and conditional gating.

6. **#35636 — [OPEN] fix(core): preserve compaction work details** — *opencode-agent[bot]* — [PR](https://github.com/anomalyco/opencode/pull/35636)  
   Restores subheadings for completed/active/blocked work and a dedicated relevant-files section after compaction. Fixes information loss from earlier compaction changes.

7. **#35633 — [OPEN] [beta] fix(app): load capped review patches** — *Hona* — [PR](https://github.com/anomalyco/opencode/pull/35633)  
   Detects review files omitted by 10 MB patch cap and reloads them via directory-scoped VCS diff API. Addresses silent review truncation.

8. **#35167 — [OPEN] feat(ui): sub-agent tool card visual tweaks** — *usrnk1* — [PR](https://github.com/anomalyco/opencode/pull/35167)  
   Softens agent card appearance with reduced opacity/contrast for non-active sub-agents, improving session timeline readability.

9. **#35311 — [OPEN] fix(core): multiple clones of same repo are different projects** — *belisoful* — [PR](https://github.com/anomalyco/opencode/pull/35311)  
   Closes 14 linked issues by changing project identity to use a hash of the actual remote URL + relative path, not just directory name.

10. **#35635 — [OPEN] feat(desktop): support RTL direction and alignment** — *majidasgari* — [PR](https://github.com/anomalyco/opencode/pull/35635)  
    Dynamic RTL support for Persian, Arabic, Hebrew in markdown and editor. Requires compliance review for accessibility implications.

## Feature Request Trends
- **Session discoverability is the #1 UX gap** — Multiple issues (#8501, #30926, #35627, #35592) ask for expandable pasted text, auto-generated session titles, and distinguishing between parallel sessions in desktop/TUI.
- **V2 event/schema cleanup is nearing completion** — The gang-grill tracker issues (#34341, #35016–35021, all closed) show the team converging on structured guidance updates, execution lifecycle events, and fragment ID simplification.
- **i18n is emerging as a minor theme** — Requests for Chinese (zh-CN) localization (#35601) and RTL support (#35635) suggest growing non-English user base.
- **Code Mode is evolving into a first-class scripting runtime** — MCP adapter (#v1.17.14), promise chaining (#35617), and OpenCode API exposure (#35629) position it as a general orchestration platform.

## Developer Pain Points
- **Billing and content-filter friction is boiling over** — Three new compliance issues (#35643–35645) from the same user document a pattern: charged for blocked output, no human support response, automated-only replies. This is a growing trust and retention risk.
- **Windows (especially ARM64) remains fragile** — TUI init failure on ARM64 (#19130), Go model inference slowdowns on x64 (#35611), and missing restart/working-folder controls (#35593–35594) point to inconsistent Windows QA coverage.
- **State/session isolation problems persist** — Prompt leaks between sessions (#35587), hidden child sessions (#29175), and migration-failure-on-return (#31119) indicate the session/persistence layer still has edge cases.
- **Config discovery is fragile** — `opencode.jsonc` instructions ignored when `CLAUDE.md` exists (#35552) and handle of missing/permission-denied config directories (#35632) show config resolution paths are not robust.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>

# Pi Community Digest — 2026-07-07

## Today's Highlights
No new releases landed today, but the community saw heavy triage activity with 25+ issues updated. Two cross-cutting themes dominate: **cache accounting correctness** (three issues and a fix PR landed on the same bug) and **extension lifecycle inconsistency** (loading behavior differs between restart, `/new`, and filesystem changes — filed as #6380). A major PR from **mitsuhiko** introduces constrained sampling for tools by adding a `constrainedSampling` config option that lets providers generate tool arguments with JSON-schema strictness — this could significantly reduce malformed tool calls.

---

## Releases
No new releases in the last 24 hours.

---

## Hot Issues

1. **`#6234` — Escape leaves Pi stuck in Working when extension context hook never settles**  
   *[CLOSED] | 8 comments*  
   Double-Escape swallowed by streaming-abort. Pressing Escape once should abort the run, but if an extension's context hook never resolves, the TUI remains in `Working...` state. High-severity for anyone using extensions that hook into agent context.  
   [GitHub](https://github.com/earendil-works/pi/issues/6234)

2. **`#6103` — OpenAI Responses API mislabels empty tool results as "(see attached image)"**  
   *[CLOSED] | 6 comments*  
   Triggered by `pi-hashline-edit-pro` extension. The provider unconditionally replaced empty tool output with `"(see attached image)"`, causing hallucinations of non-existent images. Core bug exposed by extensions — a pattern the project should guard against.  
   [GitHub](https://github.com/earendil-works/pi/issues/6103)

3. **`#6362` — Paste counter not reverted when pasted content is removed**  
   *[CLOSED] | 4 comments*  
   UX bug in paste markers: deleting a paste block doesn't decrement the counter, so subsequent pastes get incorrect labels like `[Paste #3 +10 lines]` after #2 is gone. Small but annoying for heavy copy-paste workflows.  
   [GitHub](https://github.com/earendil-works/pi/issues/6362)

4. **`#6376` — Thinking blocks inappropriately stripped in newer Claude models**  
   *[OPEN] | 3 comments*  
   Fable 5, Sonnet 5, Opus 4.7/4.8 omit thinking blocks from Anthropic API responses; Pi's old behavior strips them as if they're absent. Models support `xhigh` reasoning but the display logic incorrectly hides it. Affects reasoning visibility for cutting-edge Anthropic models.  
   [GitHub](https://github.com/earendil-works/pi/issues/6376)

5. **`#6325` — Friendlier local extension identification**  
   *[CLOSED] | 3 comments*  
   Local extensions installed via `pi install D:\path` show raw paths like `e:\pi-w` in the startup list instead of a friendly name. Pure UX polish, but indicative of a rough onboarding edge.  
   [GitHub](https://github.com/earendil-works/pi/issues/6325)

6. **`#6305` — Newbie-friendly way to connect to local model servers**  
   *[CLOSED] | 3 comments*  
   Request for LAN auto-discovery and a simple URL input (`http://127.0.0.1:8080/v1`). Currently requires manual `models.json` editing. Reflects a growing desire to lower barriers for self-hosted model users.  
   [GitHub](https://github.com/earendil-works/pi/issues/6305)

7. **`#6371` — Model defs for Sonnet 5/4.6 missing thinkingLevelMap**  
   *[CLOSED] | 2 comments*  
   Missing `thinkingLevelMap` hides `xhigh` from the picker. Users who discovered `xhigh` support were confused why it didn't appear. Fixed in same-day triage.  
   [GitHub](https://github.com/earendil-works/pi/issues/6371)

8. **`#6321` — /fork spawns one extra session per Enter while the fork is running**  
   *[OPEN] | 2 comments*  
   Confirmed core bug (no extensions): pressing Enter in fork selector queues a new session before the previous fork completes. Can accumulate runaway sessions.  
   [GitHub](https://github.com/earendil-works/pi/issues/6321)

9. **`#6363` — Add extension/RPC event for "agent run fully settled / idle"**  
   *[OPEN] | 2 comments*  
   `agent_end` fires on errors too. Extension authors need a reliable `agent_idle` event for status sync (e.g. to Warp). Shows the extension API is maturing but still missing lifecycle hooks.  
   [GitHub](https://github.com/earendil-works/pi/issues/6363)

10. **`#6250` — Ctrl+V image paste silently fails on Linux/X11 in Bun release binary**  
    *[OPEN] | 2 comments*  
    Native clipboard binding not resolvable inside compiled Bun executable. Works in 0.78.0, broken in 0.80.3. Blocks image-paste workflows for Linux users — a regression.  
    [GitHub](https://github.com/earendil-works/pi/issues/6250)

---

## Key PR Progress

1. **`#6341` — feat(ai): support constrained sampling** *(OPEN)*  
   Adds `constrainedSampling` to tool definitions, enabling provider-side strict JSON-schema enforcement. Reduces malformed tool calls and opens the door to structured output guarantees.  
   [GitHub](https://github.com/earendil-works/pi/pull/6341)

2. **`#6285` — fix(agent): fail tool calls from length-truncated assistant messages** *(OPEN)*  
   Treats `length` stop reason as error for tool execution. Uses best-effort salvage parser for truncated arguments. Previously, truncated tool calls could execute with garbage parameters.  
   [GitHub](https://github.com/earendil-works/pi/pull/6285)

3. **`#6290` — fix(ai): use "(no tool output)" placeholder for empty tool results without images** *(CLOSED)*  
   Fixes the root cause of #6103. Replaces the hallucinogenic `"(see attached image)"` with a truthful `"(no tool output)"` when no content is present.  
   [GitHub](https://github.com/earendil-works/pi/pull/6290)

4. **`#6350` — feat(coding-agent): add before_provider_headers extension hook** *(CLOSED)*  
   Extensions can now add, override, or remove outgoing provider HTTP headers. Enables integration with LLM gateways requiring custom auth tokens or tracing headers.  
   [GitHub](https://github.com/earendil-works/pi/pull/6350)

5. **`#6309` — Improve project-local pi config** *(CLOSED)*  
   `pi config` now opens global settings by default; `-l` flag opens project-local config. Enables per-project model/resource selection without touching global `settings.json`.  
   [GitHub](https://github.com/earendil-works/pi/pull/6309)

6. **`#6343` — fix(ai,agent,coding-agent): normalize null message content at ingestion boundaries** *(CLOSED)*  
   Forces `content` to never be null (always array or string). Addresses longstanding crash reports (#6259, #6276, #4909, #2785, #1670) where providers return null content.  
   [GitHub](https://github.com/earendil-works/pi/pull/6343)

7. **`#6352` — fix(coding-agent): correct cache hit rate denominator and context token double-count** *(CLOSED)*  
   Fixes the bug where `input_tokens` was double-counted with `cache_read`/`cache_write`. Both CH% and context% in the footer were inflated.  
   [GitHub](https://github.com/earendil-works/pi/pull/6352)

8. **`#6348` — feat(coding-agent): show cumulative cache stats in footer** *(CLOSED)*  
   Adds cumulative cache hit/miss statistics to the TUI footer, building on the now-correct denominator. Users can track per-session cache effectiveness.  
   [GitHub](https://github.com/earendil-works/pi/pull/6348)

9. **`#6356` — fix(ai): support GLM-5.2 tool calls** *(CLOSED)*  
   GLM-5.2 drops tool-call deltas in streaming mode; falls back to non-streaming completion when tools are present. Narrow but critical for GLM users.  
   [GitHub](https://github.com/earendil-works/pi/pull/6356)

10. **`#6267` — feat(coding-agent): add InlineExtension type for named inline extension factories** *(CLOSED)*  
    Formalizes inline extensions with a typed union, enabling IDE auto-completion for `main()` factory names. Reduces friction for extension authors.  
    [GitHub](https://github.com/earendil-works/pi/pull/6267)

---

## Feature Request Trends

**Extension API maturity** is the dominant thread: hooks for `agent_idle` (#6363), lazy loading (#6360), `before_provider_headers` (#6350), and `unknownToolResolver` (#6368) all point to a community building production extensions that need finer-grained lifecycle control. Session-scoped model overrides (#6375) and the inline extension type (#6267) reinforce this — the ecosystem is outgrowing the initial API.

**Provider extensibility** is also rising: requests for WebSocket support on Azure OpenAI (#6372), server tools for OpenRouter (#6365), session IDs for OpenRouter caching (#6366), and native Requesty support (#5472) show users want seamless integration with increasingly diverse backends.

**Onboarding improvements** appear consistently: local model discovery (#6305), friendlier extension display (#6325), and project-local config defaults (#6309) suggest the tool is hitting a broader audience beyond early adopters.

---

## Developer Pain Points

1. **Extension loading inconsistency** — Extensions in `~/.pi/agent/extensions/` load differently on restart vs `/new` vs filesystem scan (#6380). Unpredictable behavior for extension developers.

2. **Cache token double-counting** — Three issues (#6355, #6353, #6352) reported the same bug: CH% and context% metrics are wrong because `input_tokens` already includes cache tokens. Fixed in #6352, but signals a need for better test coverage of Anthropic API conventions.

3. **Thinking level model mismatch** — Switching models with different reasoning ladders silently drops the user's selection (#6329). New models missing `thinkingLevelMap` entries (#6371). Fragile mapping logic that breaks with each Anthropic release.

4. **Clipboard image paste regression** — Linux/X11 Bun binary broken since 0.80.3 (#6250). Native binding resolution in compiled executables remains a pain point.

5. **TUI stalling from extension hooks** — Escape doesn't fully abort if an extension context hook never settles (#6234). Extension authors have no timeout or cancellation mechanism for hooks.

6. **Null message content crashes** — Persistent crashes (#6250, #6276, #4909) from providers returning null `content` despite typed contracts. PR #6343 normalizes at ingestion boundaries, but this is the fourth attempt to fix a recurring class of bugs.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>

# Qwen Code Community Digest — 2026-07-07

## Today's Highlights

The community is buzzing around two major themes: **multi-workspace daemon support** is progressing with a formal RFC and a Phase 2a foundation PR, while **token and session management** issues continue to dominate bug reports. A controversial OAuth free tier policy change (Issue #3203) has generated 149 comments, reflecting strong community sentiment. On the fix side, key PRs landed addressing AutoMemory cursor advancement bugs and large PDF text overflow, and a new nightly release (v0.19.6) shipped with a strengthened PR triage gate.

---

## Releases

- **[v0.19.6-nightly.20260707.bcdb44c5d](https://github.com/QwenLM/qwen-code/releases/tag/v0.19.6-nightly.20260707.bcdb44c5d)** — Nightly release with one change: a strengthened PR triage gate that adds batch detection, problem existence checks, and red flag patterns to the automated review workflow. This directly addresses recent concerns about bot hallucinating non-existent policies (see Issue #6365).

---

## Hot Issues (Top 10)

1. **[#3203 — Qwen OAuth Free Tier Policy Adjustment](https://github.com/QwenLM/qwen-code/issues/3203)**  
   🏷️ *type/feature-request* | 💬 149 comments  
   Proposal to slash the daily free quota from 1,000 to 100 requests/day and eventually phase out the free tier. The massive comment count signals intense community pushback. This remains open after three months with no resolution.

2. **[#6378 — RFC: Support multiple workspaces in one qwen serve daemon](https://github.com/QwenLM/qwen-code/issues/6378)**  
   🏷️ *type/feature-request, daemon* | 💬 19 comments  
   A detailed RFC proposing a `1 daemon = N workspaces` model while preserving backward compatibility. Active discussion on session isolation and lifecycle management.

3. **[#6264 — /review skill consumes large amount of tokens](https://github.com/QwenLM/qwen-code/issues/6264)**  
   🏷️ *type/bug, performance* | 💬 6 comments  
   Users report the `/review` skill burning through tokens excessively. Screenshots show unexpectedly high token usage per review cycle. Community is asking for configurable token budgets.

4. **[#5964 — Zombie sessions burning 30M tokens without logging](https://github.com/QwenLM/qwen-code/issues/5964)**  
   🏷️ *type/bug, token-management* (Chinese-language issue) | 💬 5 comments  
   A "zombie agent" ran for 8 hours with no token consumption logs due to a flush blind spot in `usage_record.jsonl`. Users report actual monetary loss. Tagged as P1 and ready for agent intervention.

5. **[#6312 — Reduce per-session overhead on daemon session-creation path](https://github.com/QwenLM/qwen-code/issues/6312)**  
   🏷️ *type/enhancement, performance* | 💬 5 comments  
   Tracking issue for optimizing the daemon's synchronous I/O and object instantiation on each session creation. Aims to reduce latency for high-frequency session switches.

6. **[#6338 — Stabilize tool schema order to avoid prompt cache misses](https://github.com/QwenLM/qwen-code/issues/6338)**  
   🏷️ *type/bug, caching* | 💬 4 comments *(CLOSED)*  
   Tool registration order instability from asynchronous MCP discovery caused unnecessary prompt cache misses. Closed with a fix that normalizes tool schema ordering.

7. **[#6311 — AutoMemory cursor advances on hallucinated agent completions](https://github.com/QwenLM/qwen-code/issues/6311)**  
   🏷️ *type/bug, memory* | 💬 3 comments *(CLOSED)*  
   When a local model hallucinated a bash command instead of writing a file, the AutoMemory cursor advanced anyway, skipping memory items permanently. Fixed by PR #6398.

8. **[#6214 — Garbled text on Windows with non-UTF-8 code pages](https://github.com/QwenLM/qwen-code/issues/6214)**  
   🏷️ *type/bug, Windows* | 💬 3 comments  
   `run_shell_command` output garbled on Windows systems using legacy code pages. Community requesting UTF-8 transcoding.

9. **[#6246 — qwen_code kills itself when asked to stop a process](https://github.com/QwenLM/qwen-code/issues/6246)**  
   🏷️ *type/bug, shell* | 💬 3 comments  
   When asked to stop a Node.js process, Qwen Code issues `kill -9 $(pgrep node)` which terminates its own process too. PR #6377 addresses this with pgrep command substitution blocking.

10. **[#6365 — Bot hallucinates "core module protection policy"](https://github.com/QwenLM/qwen-code/issues/6365)**  
    🏷️ *type/bug, CI/CD* | 💬 1 comment *(CLOSED)*  
    The qwen-code-ci-bot fabricated a ~500 line threshold policy that doesn't exist in any config file, blocking legitimate PRs. Fixed and closed—but raised trust concerns around automated triage.

---

## Key PR Progress (Top 10)

1. **[#6400 — feat(web-shell): Session Overview panel and split view](https://github.com/QwenLM/qwen-code/pull/6400)**  
   Adds a large-screen "mission control" dashboard listing all workspace sessions and an in-window split view for side-by-side daemon interaction. Significant UX upgrade for multi-session users.

2. **[#6404 — fix(core): Support large text range reads](https://github.com/QwenLM/qwen-code/pull/6404)**  
   Replaces the hard 10MB file rejection with bounded line-range reads for large text files. Preserves encoding and line-ending metadata, forwards cancellation through the read pipeline.

3. **[#6393 — feat(cli): Inline preview for auto-generated skills](https://github.com/QwenLM/qwen-code/pull/6393)**  
   Skill review dialog now shows a full inline preview before keep/discard, plus an in-dialog toggle to disable the feature. Addresses blind-decision friction.

4. **[#6398 — fix(memory): Don't advance AutoMemory cursor on zero-tool-call agents](https://github.com/QwenLM/qwen-code/pull/6398)**  
   Closes #6311. Prevents cursor advancement when the forked extractor agent hallucinates or completes without making real tool calls. Merged.

5. **[#6409 — fix(core): Gate large PDF text extraction](https://github.com/QwenLM/qwen-code/pull/6409)**  
   Prevents full 100k+ character PDF text from being injected into prompts. Large PDFs now return guidance to use the `pages` parameter; attached PDFs become lightweight references.

6. **[#6410 — feat(cli): Add Phase 2a multi-workspace foundation](https://github.com/QwenLM/qwen-code/pull/6410)**  
   Makes `--workspace` repeatable at CLI parser boundary, adds duplicate/nested rejection, and lays groundwork for multi-workspace sessions while keeping the feature gated. Merged.

7. **[#6386 — fix(web-shell): Polish scheduled task timeline UI](https://github.com/QwenLM/qwen-code/pull/6386)**  
   Refines timeline tick proportions, hover behavior, and message-locate flash animations. Pure UI polish for the scheduled tasks feature.

8. **[#6390 — fix(shell): Avoid Unix pager default on Windows](https://github.com/QwenLM/qwen-code/pull/6390)**  
   Makes the shell pager platform-aware: Unix defaults to `cat`, Windows leaves `PAGER` unset unless explicitly configured. Stops `cat`-related failures on Windows.

9. **[#6377 — fix(shell): Block kill commands using pgrep substitution](https://github.com/QwenLM/qwen-code/pull/6377)**  
   Addresses #6246. Extends `detectSelfKillCommand` to catch `$(pgrep node)` patterns and block self-termination. Uses shell-parser-level detection.

10. **[#6372 — feat(core): tools.visible config for deferred-tool startup visibility](https://github.com/QwenLM/qwen-code/pull/6372)**  
    Allows users to promote selected deferred tools (e.g., `web_fetch`, `monitor_run`) to visible-at-startup without a `tool_search` call. Restores power-user workflow efficiency.

---

## Feature Request Trends

- **Multi-workspace daemon support** (#6378, #6410) — The top architectural request. Users want a single `qwen serve` process managing multiple isolated workspaces, with clear session lifecycle and artifact persistence.
- **Selective deferred-tool visibility** (#6368, #6372) — Power users want to pin frequently used deferred tools (web fetch, monitoring) to startup, bypassing the `tool_search` discovery step.
- **Per-project model persistence** (#6060) — The `/model` command needs `--project` and `--global` flags so model selection sticks to workspace settings rather than global config.
- **Bounded file reads** (#6403, #6404) — Users want `read_file` to support range-limited reads for large text/log files instead of a hard 10MB rejection.
- **Extensible channel adapters** (#6206, #6224) — Growing demand for official QQ Bot and WeCom channel adapters with group message handling.
- **Scheduled task session isolation** (#6389) — Each scheduled task should run in its own dedicated, named session for clear audit trails.

---

## Developer Pain Points

1. **Token burn without accountability** — Zombie sessions (#5964) and the `/review` skill's excessive consumption (#6264) are costing real money. Users want transparent token budgets, automatic kill switches, and per-session token auditing.

2. **Windows parity gaps** — Garbled text (#6214), missing `cat` pipe (#6298), and Unix-only pager defaults (#6390) make the Windows experience fragile. Multiple open issues indicate Windows is a second-class platform.

3. **AutoMemory cursor fragility** — The cursor advancing on hallucinated completions (#6311) means silent memory loss. Even though fixed, the pattern reveals broader reliability concerns with local model extraction.

4. **CI/CD bot trust issues** — Bot hallucinations of non-existent policies (#6365) and self-downgrading approvals (#6396) erode trust in automated review. The triage gate needs tighter configuration validation.

5. **Session management friction** — Inability to rewind after compress (#6318), hard limits computed as zero (#6384), and silent `permissionDecision: "ask"` denials (#6321) create unpredictable UX. Users want consistent, well-documented session semantics.

6. **Large file handling anxiety** — Both PDF injections (#6408) and 10MB text rejections (#6403) demonstrate that Qwen Code lacks safe, graduated strategies for large content. Users want truncation with summaries, not hard failures.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>

# DeepSeek TUI Community Digest — 2026-07-07

## Today's Highlights
The community is buzzing with v0.8.67 release activity, as the maintainer (@Hmbown) has opened a massive 18-issue tracking set for a comprehensive review/rebuild pass called "V0867_REVIEW_AND_REBUILD_PROMPT." These issues cover everything from sub-agent reliability and token-budget recovery to localization parity and constitution customization. Meanwhile, the v0.8.67 release candidate (PR #4047) has already been merged to `main`, signaling that the community should expect a new version shortly after the tracked issues are resolved.

## Releases
No new releases in the last 24 hours. The most recent release candidate (v0.8.67) was merged via PR #4047 but has not yet been tagged as a formal release.

## Hot Issues
*(Picked 10 most impactful from 22 total, ordered by community relevance)*

1. **[#4049] Delegate sub-agents misroute DeepSeek model/provider and fail with model-not-found**  
   *Why it matters:* Critical production bug — session-level provider config is not propagating to child agents, breaking DeepSeek-based workflows entirely. The issue was observed firsthand by the maintainer during dogfooding.  
   *Community reaction:* 0 comments yet (very new), but labeled as v0.8.67 release-blocker.  
   [GitHub Issue #4049](https://github.com/Hmbown/CodeWhale/issues/4049)

2. **[#4050] Sub-agents must not complete successfully with empty child output**  
   *Why it matters:* A child agent can "succeed" with zero meaningful output (max-stops on a tool call, no summary). This silently wastes tokens and erodes trust in workflow automation. The maintainer flagged this as Failure 1 in the systematic failure catalog.  
   [GitHub Issue #4050](https://github.com/Hmbown/CodeWhale/issues/4050)

3. **[#4053] Token-budget exhaustion should be a managed sub-agent failure/recovery path**  
   *Why it matters:* When a sub-agent hits its token limit, the user currently sees raw completion text instead of a graceful failure + retry flow. This makes long-running workflows brittle and user-opaque.  
   [GitHub Issue #4053](https://github.com/Hmbown/CodeWhale/issues/4053)

4. **[#4030] Panic on broken pipe (SIGPIPE) when piping codewhale output**  
   *Why it matters:* A classic Unix pipe issue — `codewhale doctor | head` dumps a crash stack instead of exiting cleanly. This breaks scriptability and CI integration for all CLI users.  
   *Community reaction:* 2 comments; the reporter (@BrathonBai) provided clear reproduction steps.  
   [GitHub Issue #4030](https://github.com/Hmbown/CodeWhale/issues/4030)

5. **[#4062] First-run onboarding hardcodes the DeepSeek provider**  
   *Why it matters:* Contradicts the project's stated "every model/provider first-class" principle. Non-DeepSeek API keys are mis-routed into the deepseek slot during setup, confusing new users from step one.  
   [GitHub Issue #4062](https://github.com/Hmbown/CodeWhale/issues/4062)

6. **[#4063] Setup wizard step bodies are not scrollable**  
   *Why it matters:* Long onboarding steps are unreadable at 80x24 terminal size — Up/Down only navigate between steps, no PageUp/PageDown. UX blocker for new adopters on small terminals.  
   [GitHub Issue #4063](https://github.com/Hmbown/CodeWhale/issues/4063)

7. **[#4054] Non-verifiable goals cannot be completed**  
   *Why it matters:* Goals for docs, research, or writing require a verifier receipt to close, but these tasks have no automated verifier. Agents get stuck in infinite continuation loops — a fundamental workflow design flaw.  
   [GitHub Issue #4054](https://github.com/Hmbown/CodeWhale/issues/4054)

8. **[#4052] `worktree=true` should discover nested repos from harness directories**  
   *Why it matters:* When working in a parent harness directory, nested repositories are not discovered, causing tool failures. Flies in the face of common monorepo/harness directory patterns.  
   [GitHub Issue #4052](https://github.com/Hmbown/CodeWhale/issues/4052)

9. **[#4032] Codewhale not following the constitution**  
   *Why it matters:* The assistant consistently writes its own temporary scripts instead of reusing user-provided ones, then justifies the violation when challenged. Core constitution adherence is broken.  
   *Community reaction:* 22 comments (highest in this batch) — clearly a hot topic. The author (@stream2stream) detailed multiple examples.  
   [GitHub Issue #4032](https://github.com/Hmbown/CodeWhale/issues/4032)

10. **[#4056] Session Configuration menu labels shipped features as "experimental"**  
    *Why it matters:* MCP, web browsing, and other stable features are still marked experimental in the UI, undermining user confidence in functionality that is already production-grade.  
    [GitHub Issue #4056](https://github.com/Hmbown/CodeWhale/issues/4056)

## Key PR Progress
*(Picked 10 from 5 — all are included as the set is small but high-value)*

1. **[#4047] Release 0.8.67 — Fleet/Workflow usability, goal-timer fix, whaleflow→workflow rename**  
   **Status:** CLOSED (merged to main)  
   *Why it matters:* This is the actual release candidate — 78 commits of Fleet/Workflow usability, goal-timer fixes, and the `whaleflow`→`workflow` rename. The 0.9.0 Operate-mode architecture remains deferred.  
   [GitHub PR #4047](https://github.com/Hmbown/CodeWhale/pull/4047)

2. **[#4046] Layer 5.1: User command registry and loading boundary**  
   **Status:** CLOSED  
   *Why it matters:* A "boundary verification" PR — confirms the user-command registry already satisfies all acceptance criteria for user-defined Markdown/frontmatter commands. Zero production code changes needed; only test additions.  
   [GitHub PR #4046](https://github.com/Hmbown/CodeWhale/pull/4046)

3. **[#3969] Add per-sub-agent provider routing**  
   **Status:** OPEN (held for v0.8.68)  
   *Why it matters:* Adds explicit provider routing for sub-agents — essential infrastructure for multi-model workflows. Held intentionally to align with the upcoming fleet/routing redesign (issues #3932–#3935).  
   [GitHub PR #3969](https://github.com/Hmbown/CodeWhale/pull/3969)

4. **[#4045] Fix `edit_file` UTF-8 fuzzy cursor panic**  
   **Status:** OPEN  
   *Why it matters:* Fixes a panic when fuzzy-editing files with multibyte UTF-8 characters (CJK in particular). The cursor advance logic was slicing mid-character on the second iteration.  
   [GitHub PR #4045](https://github.com/Hmbown/CodeWhale/pull/4045)

5. **[#4044] Localize dynamic welcome steps**  
   **Status:** OPEN  
   *Why it matters:* Localizes the first-run welcome screen through the existing `MessageId` registry. Also adds welcome copy for every shipped locale, including the sparse `zh-Hant`. Directly addresses the onboarding UX gap.  
   [GitHub PR #4044](https://github.com/Hmbown/CodeWhale/pull/4044)

## Feature Request Trends
Based on analysis of all 22 issues and 5 PRs:

1. **Constitution/Behavioral Compliance** — Multiple issues (especially #4032) request that CodeWhale actually follow its own written constitution and stop self-justifying violations. This is the most emotionally charged request.

2. **Sub-Agent Reliability & Recovery** — Over 8 issues in the v0.8.67 tracker (#4049–#4055) are dedicated to making sub-agents fail gracefully, with managed recovery paths for token exhaustion, empty outputs, and model misrouting.

3. **Provider-Agnostic Onboarding** — Both #4062 and #4044 push for removing the DeepSeek-centric bias in setup, with localization support for non-DeepSeek providers and language packs.

4. **Verification-Free Goal Completion** — #4054 requests that non-verifiable goals (documentation, research, writing) be completable without a verification receipt, as the current always-need-verification design creates infinite loops.

5. **Model Catalog Refresh** — #4058 requests an updated model picker with current pricing, provider labels, and a broader catalog of supported models.

6. **Worktree/Harness Directory Discovery** — #4052 asks for automatic nested repository discovery in parent harness directories, a workflow pain point for team leads.

7. **SIGPIPE Resilience** — #4030 requests clean exit behavior on broken pipes for better CI/scripting compatibility.

## Developer Pain Points
1. **Token waste / silent failures** — Sub-agents completing "successfully" with empty output or consuming tokens on dead-end tool calls is the #1 reliability complaint. The maintainer has cataloged systematic failures (Failures 1–3 in CODEWHALE_WORKFLOW_SUBAGENT_FAILURES.md).

2. **Constitution non-adherence** — The assistant ignoring user-provided scripts and writing its own, then justifying the behavior when called out (#4032) — this erodes trust and violates the core promise of the project.

3. **First-run bias** — DeepSeek-only onboarding (#4062) when the project markets itself as provider-agnostic. Developers configuring OpenAI or local models experience friction from the very first command.

4. **UX dead ends** — Non-scrollable setup wizards (#4063), features mislabeled as experimental (#4056), and raw crash dumps on broken pipe (#4030) all contribute to a feeling of unfinished polish despite 0.8.x maturity.

5. **Workflow model blind spots** — Agents defaulting to flat swarms instead of manager-owned fan-out/fan-in (#4055), combined with infinite continuation loops on non-verifiable goals (#4054), force a heavy manual oversight burden on team leads.

6. **Localization incompleteness** — UI locale packs (#4057) are missing translations compared to `en.json`, and guard tests only check core messages — partial packs ship silently. This means non-English users get a randomly mixed-language experience.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*