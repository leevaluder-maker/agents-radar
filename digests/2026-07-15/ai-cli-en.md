# AI CLI Tools Community Digest 2026-07-15

> Generated: 2026-07-15 01:26 UTC | Tools covered: 9

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
**Date:** 2026-07-15

---

## 1. Ecosystem Overview

The AI CLI tool landscape shows a mature but rapidly evolving ecosystem where seven major tools compete across developer workflows. Claude Code and OpenAI Codex lead in community scale and enterprise adoption, while Gemini CLI and Qwen Code differentiate through architectural innovation (multi-workspace daemons, sandbox-first design). GitHub Copilot CLI and Kimi Code occupy focused niches—Copilot leverages the GitHub ecosystem, while Kimi serves Moonshot AI's user base. Pi and DeepSeek TUI represent the open-source, community-driven tier with strong contributor velocity but smaller user bases. The dominant themes across all tools are **session reliability**, **permission/security hardening**, **Windows platform stability**, and **agent lifecycle management**—indicating the ecosystem has moved past initial feature novelty into a stabilization and hardening phase.

---

## 2. Activity Comparison

| Tool | Open Issues | PRs Today | Release Status | Notable Signal |
|------|-------------|-----------|----------------|----------------|
| **Claude Code** | ~77.6K total | 8 merged | v2.1.210 (patch) | High regression volume; Windows Cowork is #1 pain point |
| **OpenAI Codex** | ~33K total | 10 merged | 0.145.0-alpha (5 alphas) | Rapid alpha cadence; critical 27% context regression |
| **Gemini CLI** | ~28K total | 10 active | v0.52.0-nightly | Staged PRs for token waste and recursion limits |
| **Copilot CLI** | ~4.1K total | 0 merged | v1.0.71-2 (patch) | Low PR activity; heavy issue triage focus |
| **Kimi Code** | Small tracker | 3 merged | kimi 2.6 (stable) | Stabilization phase; only 2 hot issues |
| **OpenCode** | ~37K total | 10 active | v1.18.1 (hotfix) | v2 migration caused regression wave; high community PRs |
| **Pi** | Mid-range | 10 merged | v0.80.7 (breaking) | Model catalog/OAuth expansion; self-hosted regression |
| **Qwen Code** | ~6.9K total | 10 active | v0.19.10 (stable) | Multi-workspace milestone; security hardening focus |
| **DeepSeek TUI** | ~4.4K total | 15 merged | v0.8.68 RC | Highest contributor velocity; i18n and cross-platform |

**Key observations:**
- Claude Code and OpenCode show the highest regression volume, indicating rapid change with testing gaps
- Qwen Code and DeepSeek TUI ship the most architectural features (multi-workspace, underwater TUI)
- Copilot CLI and Kimi Code have low PR throughput—maintenance vs. feature mode
- Pi has the highest PR merge rate for provider/model expansion

---

## 3. Shared Feature Directions

| Shared Need | Tools Affected | Specific Requirements |
|-------------|----------------|----------------------|
| **Windows Platform Stability** | Claude Code, OpenCode, Copilot CLI, Kimi Code | HCS service failures, crash-on-startup (0xC0000005), Bun runtime crashes, orphaned processes |
| **Session Reliability & Data Persistence** | Claude Code, OpenAI Codex, Copilot CLI, OpenCode | Threads silently disappearing, session corruption on fork, flush-to-disk gaps, compaction failures |
| **Agent Lifecycle Management** | Claude Code, Gemini CLI, DeepSeek TUI | Subagent hang signals reported as success, background cancellation semantics, max-turn handling |
| **Permission/Security Hardening** | Claude Code, Qwen Code, Gemini CLI, Pi | Permission rule bypass via symlinks, untrusted MCP auto-approval, daemon secret leakage |
| **Context Window & Token Budgeting** | OpenAI Codex, Gemini CLI, Kimi Code, Pi | Dynamic completion budgeting, shell output bounding, recursive turn limits, context regression detection |
| **Multi-Provider/Model Support** | Pi, DeepSeek TUI, OpenCode, Copilot CLI | Amazon Bedrock Mantle, xAI OAuth, GPT-5.6 variants, GitHub Copilot model integration |
| **TUI Rendering & Copy-Paste** | DeepSeek TUI, Claude Code, Gemini CLI, Copilot CLI | Unicode box-drawing pollution, tmux overlap, terminal resize flicker, slow streaming display |

**Emerging pattern:** The most cross-cutting demand is **agent behavior predictability**—users across 5+ tools report agents ignoring configuration, masking failures, or running unintended operations. This signals the ecosystem needs standardized agent lifecycle semantics.

---

## 4. Differentiation Analysis

| Dimension | Tool Leaders | Key Differentiators |
|-----------|-------------|---------------------|
| **Enterprise Reliability** | Claude Code, OpenAI Codex | Largest user bases, most regression reports, highest expectations for production use |
| **Architectural Innovation** | Qwen Code, Gemini CLI, Pi | Multi-workspace daemons (Qwen), AST-aware mapping (Gemini), session-affinity format (Pi) |
| **Model Provider Breadth** | Pi, DeepSeek TUI, OpenCode | 15+ providers each; OAuth flows for xAI, Amazon Bedrock, MiniMax |
| **Security Hardening** | Qwen Code, Claude Code | Path canonicalization, MCP trust validation, daemon secret sanitization |
| **Cross-Platform Support** | DeepSeek TUI, Pi | BSD, Android/Termux, full Linux/macOS/Windows coverage |
| **GitHub Ecosystem Integration** | Copilot CLI | Plugin marketplace, voice mode, canvas extensions—tightest GitHub integration |
| **Chinese Market Focus** | Kimi Code, Qwen Code, DeepSeek TUI | Moonshot AI, Alibaba Qwen, i18n quality concerns (DeepSeek) |
| **Open Source Contributor Velocity** | DeepSeek TUI, Pi, OpenCode | Highest community PR submission rates; grassroots feature development |

**Strategic implications:**
- Claude Code and OpenAI Codex compete on **enterprise trust** but both suffer reliability issues
- Qwen Code's **multi-workspace daemon** and Gemini CLI's **AST-aware mapping** represent genuine architectural differentiation
- Pi and DeepSeek TUI are becoming the **Swiss Army knives** of provider interoperability
- Copilot CLI's low PR activity and focus on plugin marketplace suggests **platform play** over core innovation

---

## 5. Community Momentum & Maturity

| Maturity Tier | Tools | Indicators |
|---------------|-------|------------|
| **Established Enterprise** | Claude Code, OpenAI Codex | 77K/33K issues; frequent releases; high regression burden indicates scale |
| **Growth-Stage Innovators** | Qwen Code, Gemini CLI | Major architectural releases; clear RFC-driven process; strong security focus |
| **Niche Specialists** | Copilot CLI, Kimi Code | Smaller but engaged communities; focused feature sets; lower churn |
| **Community-Driven Upstarts** | Pi, DeepSeek TUI, OpenCode | Highest contributor-per-user ratio; rapid feature addition; lower test coverage |

**Velocity ranking (PRs/contributors today):**
1. **DeepSeek TUI** — 15 merged PRs from 6+ contributors
2. **OpenAI Codex** — 10 merged PRs (internal team)
3. **Pi** — 10 merged PRs (mixed contributors)
4. **Qwen Code** — 10 active PRs (structured development)
5. **OpenCode** — 10 active PRs (high community PRs from @ohsalmeron)
6. **Claude Code** — 8 merged PRs (internal team with community minor fixes)
7. **Gemini CLI** — 10 active PRs (staged, not merged today)
8. **Copilot CLI** — 0 merged (triaging)

**Maturity assessment:**
- Claude Code and OpenAI Codex show **maturity friction**—large user bases generate many regression reports as the tools evolve
- DeepSeek TUI has **highest momentum-per-user**—community contributors shipping meaningful features
- Qwen Code demonstrates **structured maturity**—RFC process, EPIC tracking, systematic security hardening
- Copilot CLI appears in a **maintenance plateau**—low feature throughput, high issue triage

---

## 6. Trend Signals

### For Developers and Technical Decision-Makers

1. **Agent Configuration Reliability is the #1 Unmet Need**
   Across 6+ tools: agents ignoring `disabled` flags, failing to use custom skills, masking turn-limit failures as success, hanging on trivial tasks. **Bottom line:** Current agent architectures lack predictable, debuggable behavior. Expect a shift toward "agent observability"—explicit state machines, trace logs, and config validation.

2. **Windows is the Achilles' Heel**
   Claude Code (3 active Cowork issues), Copilot CLI (orphaned processes), OpenCode (v2 regression), Kimi Code (both hot issues on Windows). **Bottom line:** Linux/macOS-first tooling continues to leave Windows as a second-class citizen, creating an enterprise adoption barrier.

3. **Context Window Management is a Universal Pain Point**
   Codex's 27% context regression, Gemini's unbounded shell output, Kimi's dynamic budgeting fix, Pi's compaction edge cases. **Bottom line:** As models offer larger contexts (100K+), tools must implement proportional budgeting, not hardcoded caps. The next competitive differentiator will be **adaptive context optimization**.

4. **OAuth and Provider Diversity is Accelerating**
   Pi merged xAI OAuth; OpenCode restored xAI v2 integration; DeepSeek TUI added MiniMax; Copilot CLI added plugin marketplace. **Bottom line:** The "one API key" era is ending. Tools that abstract multi-provider authentication, billing, and model routing will win enterprise adoption.

5. **Session History and Recovery Remains Fragile**
   Data-loss reports across Claude Code (thinking text lost), Codex (threads disappear), Copilot CLI (sessions lost on restart), OpenCode (VPS history broken). **Bottom line:** No tool has solved durable, cross-session state management. This is a greenfield opportunity for innovation in checkpointing, diff-based storage, and compaction strategies.

6. **Internationalization is an Emerging Requirement**
   DeepSeek TUI's Chinese translation issues, Claude Code's session title language request, Kimi Code's China TPD limits. **Bottom line:** As AI CLI tools expand globally, i18n will shift from "nice-to-have" to "blocker" for non-English markets, especially in East Asia.

7. **TUI Usability Standards are Rising**
   Copy-paste pollution (DeepSeek, Copilot), streaming lag (DeepSeek), tmux corruption (Claude), terminal resize flicker (Gemini). **Bottom line:** Terminal-based interfaces need investment in rendering engines, accessibility (screen readers, reduced motion), and platform compatibility to compete with IDEs.

8. **Security Hardening is Becoming Proactive**
   Qwen Code's path canonicalization and MCP trust validation, Claude Code's permission rules migration warnings, Pi's session ID clamping. **Bottom line:** The ecosystem is moving from reactive security patches to proactive threat modeling—a sign of enterprise readiness.

---

**Final Summary for Decision-Makers:**

- **For production deployments:** Claude Code and OpenAI Codex offer the most integrations but require monitoring for regression-proneness. Qwen Code shows the strongest security posture.
- **For multi-provider flexibility:** Pi and DeepSeek TUI offer the broadest model support with active community maintenance.
- **For GitHub ecosystem integration:** Copilot CLI is the clear choice but watch for plugin marketplace maturity.
- **For Chinese market or Alibaba ecosystem:** Qwen Code and Kimi Code are the primary options, with Qwen showing stronger architecture.
- **For open-source customization:** DeepSeek TUI has the highest community contribution velocity but the smallest user base—a trade-off between agility and stability.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)

# Claude Code Skills Community Highlights Report
**Data as of 2026-07-15** | Source: github.com/anthropics/skills

---

## 1. Top Skills Ranking

### #1: Skill Creator Bug Fixes (PR #1298)
**Status:** Open | **Author:** MartinCajiao | [GitHub](https://github.com/anthropics/skills/pull/1298)
- **Functionality:** Critical patch for `run_eval.py` — the skill description optimization pipeline — which has been reporting `recall=0%` for all evaluations due to multiple interacting bugs across trigger detection, Windows stream handling, and parallel worker configuration.
- **Discussion:** The most-commented PR reflects a systemic pain point: the skill-creation toolchain is unreliable on Windows and produces noisy optimization signals. Multiple independent reproductions (issue #556, #1169, #1061) confirm the bug's prevalence.
- **Why it matters:** Without functioning evaluation, the entire skill description improvement loop is "optimizing against noise."

### #2: Document Typography Skill (PR #514)
**Status:** Open | **Author:** PGTBoos | [GitHub](https://github.com/anthropics/skills/pull/514)
- **Functionality:** Prevents orphan word wrap, widow paragraphs, and numbering misalignment in AI-generated documents — a universal quality-of-life fix for Claude's document output.
- **Discussion:** Addresses a gap no existing skill fills. Users report these typographic issues affect "every document Claude generates."
- **Status:** Pending merge; no active blockers.

### #3: PDF Case Sensitivity Fix (PR #538)
**Status:** Open | **Author:** Lubrsy706 | [GitHub](https://github.com/anthropics/skills/pull/538)
- **Functionality:** Fixes 8 case-sensitivity mismatches between `SKILL.md` references and actual filenames (`REFERENCE.md` → `reference.md`, etc.). Breaks on case-sensitive filesystems (Linux/macOS).
- **Discussion:** A straightforward correctness fix, but its prominence signals the community's attention to production reliability of existing skills.

### #4: ODT / OpenDocument Skill (PR #486)
**Status:** Open | **Author:** GitHubNewbie0 | [GitHub](https://github.com/anthropics/skills/pull/486)
- **Functionality:** Full OpenDocument Format support (.odt, .ods) — creation, template filling, and ODT→HTML conversion. Triggers on "ODT," "ODS," "LibreOffice," etc.
- **Discussion:** High demand for open-source document formats. No native ODT skill exists in the official collection, making this a distinct gap-filler.

### #5: Frontend-Design Improvement (PR #210)
**Status:** Open | **Author:** justinwetch | [GitHub](https://github.com/anthropics/skills/pull/210)
- **Functionality:** Revises the existing frontend-design skill for clarity and actionability — ensures every instruction is executable within a single conversation.
- **Discussion:** Reflects community desire for *actionable* skills rather than verbose reference documents. Users want skills that steer behavior, not just educate.

### #6: Self-Audit Skill v1.3.0 (PR #1367)
**Status:** Open | **Author:** YuhaoLin2005 | [GitHub](https://github.com/anthropics/skills/pull/1367)
- **Functionality:** Two-phase output audit: (1) mechanical file verification, (2) four-dimension reasoning quality gate in damage-severity order. Universal across projects and tech stacks.
- **Discussion:** Latest high-profile skill proposal (June 2026). The "reasoning quality gate" concept is novel — no existing skill audits AI output before delivery.

---

## 2. Community Demand Trends

From the most-commented issues, the community's strongest demands cluster around four directions:

**🔧 Toolchain Reliability (Issue #556, #1169, #1061)**
The dominant theme: `run_eval.py` and the skill-creator pipeline are broken on Windows and produce unreliable evaluation signals. Multiple users confirm the `recall=0%` bug independently. *This is the #1 blocker for skill developers.*

**🔒 Security & Trust Boundaries (Issue #492 — 34 comments)**
Community skills distributed under the `anthropic/` namespace create a trust vulnerability. Users may grant elevated permissions to skills they believe are official. This is the most-discussed issue overall, signaling deep concern about the current distribution model.

**🏢 Organizational Sharing (Issue #228 — 14 comments)**
Enterprise users want org-wide skill sharing without manual `.skill` file distribution. A shared skill library or direct sharing links would streamline collaboration.

**📄 Document Format Gaps (Issue #189 — duplicates; PR #486 — ODT)**
Users report duplicate skills when installing multiple plugins, and a clear gap exists for OpenDocument/LibreOffice formats. The ecosystem needs clearer plugin boundaries and broader format support.

---

## 3. High-Potential Pending Skills

These PRs have active discussion and are likely to merge soon:

| PR | Skill | Author | Why It May Land Soon |
|---|---|---|---|
| [#1367](https://github.com/anthropics/skills/pull/1367) | **Self-Audit** (reasoning quality gate) | YuhaoLin2005 | Recent (June 2026), well-specified, fills a clear security/quality gap |
| [#723](https://github.com/anthropics/skills/pull/723) | **Testing Patterns** (full-stack testing) | 4444J99 | Comprehensive; covers unit, React, integration, and E2E testing |
| [#1302](https://github.com/anthropics/skills/pull/1302) | **Color Expert** (color naming, spaces, accessibility) | meodai | Self-contained, strong domain coverage, low integration risk |
| [#514](https://github.com/anthropics/skills/pull/514) | **Document Typography** | PGTBoos | No technical blockers; addresses universal pain point |
| [#83](https://github.com/anthropics/skills/pull/83) | **Skill Quality & Security Analyzer** | eovidiu | Meta-skill that improves the entire ecosystem; dual-purpose |

---

## 4. Skills Ecosystem Insight

**The community's most concentrated demand is for a reliable, cross-platform skill development toolchain** — Windows compatibility fixes, correct `recall` metrics in `run_eval.py`, and proper trigger detection account for the majority of top-activity PRs and issues — before new skill content can be effectively built or evaluated.

---

# Claude Code Community Digest — 2026-07-15

## Today's Highlights

Two patch releases arrived today addressing usability pain points: v2.1.210 adds a live elapsed-time counter for long-running tool calls, and v2.1.209 fixes `/model` dialogs being blocked in `claude agents` background sessions. The community conversation remains dominated by Windows Cowork VM service failures (three active issues, 92 total comments) and a surge of documentation gap reports from contributor `coygeek` filed 12 issues covering missing or outdated docs across sandboxing, memory, permissions, agent view, and MCP SDK.

## Releases

**v2.1.210** — [Release](https://github.com/anthropics/claude-code/releases/tag/v2.1.210)
- Live elapsed-time counter on collapsed tool summary lines so long-running tool calls show ticking progress instead of appearing stuck
- Startup warning for `Write(path)`, `NotebookEdit(path)`, and `Glob(path)` permission rules — users should migrate to `Edit(path)` or `Read(path)`

**v2.1.209** — [Release](https://github.com/anthropics/claude-code/releases/tag/v2.1.209)
- Fixed `/model` and other dialogs being blocked in `claude agents` background sessions by reverting an overly broad guard

## Hot Issues

1. **[#74649 — Cowork not working on Windows 11 Pro — Missing HCS services: vfpext](https://github.com/anthropics/claude-code/issues/74649)**  
   75 comments, 4 👍. The most active open issue. Windows Cowork fails with missing Hyper-V Container Services. Community has identified `vfpext` as the culprit but no official fix or workaround has shipped. The high comment count signals significant user frustration.

2. **[#69415 — Connection closed mid-response on VSCode/WSL](https://github.com/anthropics/claude-code/issues/69415)**  
   26 comments, 54 👍 (highest reaction count). API connections dropping mid-response, making Claude Code "unusable for any task" on WSL. The intense upvote ratio suggests this impacts a large portion of the user base.

3. **[#64592 — Cowork VM service not running on Windows 11](https://github.com/anthropics/claude-code/issues/64592)**  
   11 comments. Fresh reproduction of the Windows Cowork startup failure. The workaround (manually enabling Virtual Machine Platform) is documented but users want a permanent fix. Extends the #54891/#61559 cluster.

4. **[#73587 — Desktop app ignores `permissions.allow` rules](https://github.com/anthropics/claude-code/issues/73587)**  
   5 comments, platform:Windows, area:MCP. Regression where the desktop app prompts for every file access even when `permissions.allow` is configured — including Claude's own config directory. Marked as a regression with a repro.

5. **[#77625 — Claude Code crashes 0xC0000005 on Windows 11 (Bun-based)](https://github.com/anthropics/claude-code/issues/77625)**  
   Filed today. Crashes on Windows 11 when using Bun-based versions (v2.1.112+). Access violation error points to a runtime issue in the Bun packaging layer.

6. **[#77651 — Assistant text between tool calls silently lost](https://github.com/anthropics/claude-code/issues/77651)**  
   Filed today on macOS with claude-fable-5. Interleaved thinking blocks cause assistant text to disappear — not rendered in TUI, not in Ctrl+O, not persisted to session JSONL. A critical bug for users relying on thinking-model output.

7. **[#77615 — TUI rendering broken with overlapping text in tmux](https://github.com/anthropics/claude-code/issues/77615)**  
   UI corruption in v2.1.202 inside tmux on macOS. Output lines overlap, typed characters paint over old content. Does not occur in bare iTerm2; specific to tmux multiplexer.

8. **[#77649 — Background daemon spawn/reconnect lifecycle defects](https://github.com/anthropics/claude-code/issues/77649)**  
   Four related defects in one bundle: un-settled workers pin daemon, reconnect re-forks duplicate sessions, `--continue` drops permission mode, forked sessions inherit auto/computer-use incorrectly. High-severity for agent users.

9. **[#77374 — Model picker shows Fable but actually uses Opus](https://github.com/anthropics/claude-code/issues/77374)**  
   UI shows "Fable" as selected model but Claude responds with Opus unless manually reselected. Surprising behavior that could silently cost users more (or deliver wrong model capabilities).

10. **[#77617 — ANTHROPIC_API_KEY silently overrides OAuth in child processes](https://github.com/anthropics/claude-code/issues/77617)**  
    Reporter claims ~$400 of unauthorized metered credit usage when the environment variable overrode explicit OAuth authentication. A serious security/trust issue for users with complex shell environments.

## Key PR Progress

1. **[#77613 — claude-compare](https://github.com/anthropics/claude-code/pull/77613)** — New tool for comparing Claude outputs side-by-side. No description yet but the name suggests a utility for evaluating model responses.

2. **[#77556 — fix(plugin-dev): validate-hook-schema.sh handles plugin hooks.json format](https://github.com/anthropics/claude-code/pull/77556)** — Fixes two bugs in the hook-schema validator shipped with the plugin-dev plugin. The validator was crashing on the exact format the skill's own documentation uses. Includes jq version detection and whitespace robustness for JSON arrays.

3. **[#77492 — fix(hookify): match Write and prompt rules](https://github.com/anthropics/claude-code/pull/77492)** — Ensures file rules inspect content passed to Write as new text, maps simple prompt rules to UserPromptSubmit payload, adds regression coverage for Write, Edit, and prompt rules.

4. **[#77443 — fix(ralph-wiggum): stop hook's jq error handling under set -e](https://github.com/anthropics/claude-code/pull/77443)** — Fixes unreachable error handling in the Ralph Wiggum plugin's stop hook. The `$?` check after `jq` never fires because `set -e` causes the script to exit before the conditional.

5. **[#77442 — fix: repair issue-automation telemetry and dead days_back input](https://github.com/anthropics/claude-code/pull/77442)** — Three correctness fixes: Statsig events timestamped in 1970, unused `days_back` input being silently ignored in dedupe workflow, and a workflow that incorrectly expected bool input but received string.

6. **[#77439 — docs(plugins): sync security-guidance listing with v2.0.0 plugin manifest](https://github.com/anthropics/claude-code/pull/77439)** — Updates marketplace listing and README for the security-guidance plugin which was rewritten to v2.0.0 but the metadata files still referenced v1.0.0.

7. **[#77427 — fix(pr-review-toolkit): make code-reviewer a leaf agent](https://github.com/anthropics/claude-code/pull/77427)** — Restricts the `pr-review-toolkit` code reviewer to repository-inspection tools only. Prevents the reviewer from recursively invoking additional agents, which could cause runaway costs and infinite agent chains.

8. **[#76298 — docs: document Remote Control background-task panel](https://github.com/anthropics/claude-code/pull/76298)** (CLOSED) — Documents the web/mobile background-task panel for Remote Control and task status synchronization behavior added in v2.1.205.

## Feature Request Trends

- **Windows Cowork VM customization** ([#56089](https://github.com/anthropics/claude-code/issues/56089), 26👍) — Users want to configure where the VM bundle (VHDX) is stored, not just accept the default location. This is the highest-voted open feature request and ties directly to the recurring Cowork service failures.

- **Session title language configuration** ([#72004](https://github.com/anthropics/claude-code/issues/72004), 4👍) — Non-English users want session titles generated in their working language rather than always English. Request includes the ability to configure via CLAUDE.md.

- **Fable 5 in plan mode** ([#77650](https://github.com/anthropics/claude-code/issues/77650)) — Filed today: users want access to the latest model (Fable 5) in plan mode for tasks like security audits, where plan mode is currently restricted.

- **Documentation completeness** — 12 documentation improvement issues filed today by a single contributor ([#77637](https://github.com/anthropics/claude-code/issues/77637) through [#77648](https://github.com/anthropics/claude-code/issues/77648)). Topics include: sandbox symlink protection, auto memory error handling, agent tool prompt injection risks, skill placeholder behavior, screen reader accessibility status, and MCP SDK connection behavior.

## Developer Pain Points

1. **Windows Cowork infrastructure** remains the #1 pain point. Three active issues, 92 total comments, consistently high engagement. The root cause (missing Hyper-V services, VM service failures) has known workarounds but no permanent fix from Anthropic.

2. **Connection reliability on WSL/VSCode** ([#69415](https://github.com/anthropics/claude-code/issues/69415), 54👍) — API connections closing mid-response is described as making Claude Code "unusable" on WSL, the primary development setup for many Windows developers.

3. **Permission system regressions** — Two issues filed today ([#73587](https://github.com/anthropics/claude-code/issues/73587) Windows, [#76238](https://github.com/anthropics/claude-code/issues/76238) macOS) where allowlisted permissions are ignored on fresh sessions. The pattern suggests a broader permissions caching or initialization bug.

4. **Bun runtime crashes on Windows** ([#77625](https://github.com/anthropics/claude-code/issues/77625), [#66683](https://github.com/anthropics/claude-code/issues/66683)) — Access violation segfaults on Windows 11 with Bun-based versions. Specifically affects Intel Meteor Lake CPUs, suggesting a hardware compatibility issue in the runtime layer.

5. **Thinking model text loss** ([#77651](https://github.com/anthropics/claude-code/issues/77651)) — Assistant text between tool calls disappearing entirely when using interleaved thinking models. This undermines trust in the session record and makes debugging nearly impossible.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

# OpenAI Codex Community Digest
**Date:** 2026-07-15

---

## Today's Highlights

Version 0.145.0-alpha continues to roll out with a flurry of Rust-based alpha releases, though none contain user-facing changelogs, signaling active pre-stabilization development. The community is most vocal about two acute issues: a **critical 30% context-window regression** in GPT-5.6 Sol and a **desktop browser plugin crash** (`Cannot redefine property: process`) affecting both macOS and Windows users. On the PR side, the team is shipping infrastructure hardening for MCP tool reuse, startup telemetry, and a significant model migration from GPT-5.4 to GPT-5.6 variants.

---

## Releases

Five Rust releases landed in the last 24 hours, all on the `0.145.0-alpha` track except for a backported patch:
- **`rust-v0.144.4`** — Chores-only patch; no user-facing changes. Full changelog: [compare v0.144.3...v0.144.4](https://github.com/openai/codex/compare/rust-v0.144.3...rust-v0.144.4)
- **`rust-v0.145.0-alpha.8` through `rust-v0.145.0-alpha.12`** — Five alpha releases with no published changelog details, suggesting internal stabilization or CI/toolchain work.

> **Bottom line:** No functional changes for end users today. The rapid alpha cadence suggests a `0.145.0` stable release may be approaching.

---

## Hot Issues (Top 10)

### 1. [#32925 — Browser plugin fails: `Cannot redefine property: process`](https://github.com/openai/codex/issues/32925)
**Status:** Closed | **Comments:** 52 | **👍:** 31  
The most active bug of the day. Codex Desktop 26.707.71524 breaks both its bundled browser and Chrome plugin integration with a JavaScript runtime error. A related duplicate (#32935) reinforces the severity. Community noise is high, and users across platforms are being blocked from browser-use features.

### 2. [#28969 — Add setting to disable auto-resolve in 60 seconds](https://github.com/openai/codex/issues/28969)
**Status:** Open | **Comments:** 34 | **👍:** 119  
The community’s most-upvoted open issue. Users want CLI `--no-auto-resolve` or config-level control over the 60-second timer that forces conversation resolution. This is a strong candidate for a configuration overhaul.

### 3. [#17827 — Customizable status line for TUI](https://github.com/openai/codex/issues/17827)
**Status:** Open | **Comments:** 28 | **👍:** 103  
A long-standing feature request (since April) to match Claude Code’s status bar. Users want live visibility into token usage, model, rate limits, context window, and git branch. Momentum is growing; 103 👍 suggests high demand.

### 4. [#32806 — 🚨 SEVERE REGRESSION: GPT-5.6 Sol context cut from 353K → 258K](https://github.com/openai/codex/issues/32806)
**Status:** Closed | **Comments:** 22 | **👍:** 23  
A critical context-window regression in the flagship reasoning model. Despite a 1.05M advertised cap, users are seeing effective context slashed to **258K tokens** — a 27% drop from the previous 353K — breaking long-running `/goal` tasks and complex refactors. Likely a server-side model config issue.

### 5. [#25463 — Desktop project threads silently disappear from UI](https://github.com/openai/codex/issues/25463)
**Status:** Open | **Comments:** 16 | **👍:** 1  
Persistent and concerning: project conversations vanish from the Desktop UI but remain readable on disk as JSONL. Users must manually resume via file recovery. The silent data-loss aspect is a trust issue.

### 6. [#29968 — Pro20x subscription behaving like Plus tier](https://github.com/openai/codex/issues/29968)
**Status:** Open | **Comments:** 16 | **👍:** 14  
High-priority billing/entitlement bug. Pro20x subscribers see rate limits and model access consistent with the Plus tier. No resolution posted yet; billing incidents erode trust in subscription tiers.

### 7. [#20880 — App silently creates empty `~/Documents/Codex` folder](https://github.com/openai/codex/issues/20880)
**Status:** Open | **Comments:** 16 | **👍:** 36  
A minor but persistent annoyance. Every launch creates an empty `~/Documents/Codex` directory, even without a project. Users on macOS with iCloud see it synced to cloud storage. The lack of fix after 2+ months is frustrating the community.

### 8. [#30178 — Desktop in-app browser crashes main app during navigation](https://github.com/openai/codex/issues/30178)
**Status:** Open | **Comments:** 15 | **👍:** 0  
Windows-specific crash in the webview renderer. Users report the app exits without error when the browser panel navigates. Amplified by #32683 (same crash in `chrome.dll`).

### 9. [#32683 — [Windows] CrBrowserMain crash (0xC0000005)](https://github.com/openai/codex/issues/32683)
**Status:** Open | **Comments:** 13 | **👍:** 2  
A Windows access-violation crash (`0xC0000005`) in Chrome’s `chrome.dll` when Browser Use opens a page. Likely the same root cause as #30178. This is the second major browser crash on Windows today.

### 10. [#33171 — Remote-compaction capacity error kills persistent goals](https://github.com/openai/codex/issues/33171)
**Status:** Open | **Comments:** 5 | **👍:** 0  
Long-running `/goal` tasks repeatedly hit a remote-compaction capacity error and terminate. While other tasks remain healthy, persistent goals are brittle. Users on `gpt-5.6-sol` with `xhigh` reasoning are most affected. This compounds with the context regression (#32806).

---

## Key PR Progress (Top 10)

### 1. [#33173 — Migrate GPT-5.4 uses to GPT-5.6 variants](https://github.com/openai/codex/pull/33173)
**Status:** Closed  
Hides `gpt-5.4` and `gpt-5.4-mini` from model selection, directing users to `gpt-5.6-terra` and `gpt-5.6-luna`. Also moves memory consolidation/extraction to the new models. A significant model lifecycle deprecation.

### 2. [#33184 — Reuse MCP tool catalogs across sessions](https://github.com/openai/codex/pull/33184)
**Status:** Closed  
Caches tool catalogs for stdio MCP servers so new sessions don’t wait for re-initialization. Improves session startup latency for users with multiple MCP servers.

### 3. [#33180 — Serialize concurrent MCP stdin writes](https://github.com/openai/codex/pull/33180)
**Status:** Closed  
Adds a semaphore to guard against interleaved JSON-RPC writes on MCP stdin. Fixes a race condition that could corrupt communication with MCP servers.

### 4. [#33198 — Keep interrupted prompts in conversation history](https://github.com/openai/codex/pull/33198)
**Status:** Closed  
Interrupted prompts (Esc/Ctrl-C) now remain in the transcript as blank placeholders instead of being silently dropped. Better UX for resuming interrupted workflows.

### 5. [#33187 — Honor workspace spend controls in rate-limit handling](https://github.com/openai/codex/pull/33187)
**Status:** Closed  
Fixes a race condition where sparse rate-limit updates could overwrite newer workspace hard-stop settings. Critical for enterprise/workspace billing accuracy.

### 6. [#33177 — Support model catalog templates for Guardian policy prompts](https://github.com/openai/codex/pull/33177)
**Status:** Closed  
Adds a `policy_template` field to auto-review models, allowing catalog-driven Guardian instructions. Enables more flexible content-safety policies without code changes.

### 7. [#33175 — Handle Amazon Bedrock credentials during logout](https://github.com/openai/codex/pull/33175)
**Status:** Closed  
Ensures logout doesn’t remove or misrepresent AWS-managed credentials when using Amazon Bedrock. Part of the expanding Bedrock integration story.

### 8. [#33170 — Support Amazon Bedrock login in the app server](https://github.com/openai/codex/pull/33170)
**Status:** Closed  
Adds experimental `amazonBedrock` type to `account/login/start`. Validates API key and Mantle region, persists credential. Amazon Bedrock is becoming a first-class authentication path.

### 9. [#33152 — Support paginated thread history in app-server list APIs](https://github.com/openai/codex/pull/33152)
**Status:** Closed  
`thread/turns/list` now supports pagination for threads with many turns. Clients can page through history with cursors, fixing a long-standing API limitation for sessions with thousands of turns.

### 10. [#33149 — Build MCP tool runtimes before router planning](https://github.com/openai/codex/pull/33149)
**Status:** Closed  
Converts filtered MCP tool metadata into `CoreToolRuntime` instances before tool-routing, unifying the direct and deferred MCP tool paths. Simplifies tool routing architecture.

---

## Feature Request Trends

| Trend | Signal | Evidence |
|-------|--------|----------|
| **Customizable TUI status line** | 103 👍 | [#17827](https://github.com/openai/codex/issues/17827) — token usage, git branch, rate limits |
| **Disable auto-resolve timer** | 119 👍 | [#28969](https://github.com/openai/codex/issues/28969) — users want control over 60s resolution |
| **IDE-style Git workspace** | 3 👍 | [#30919](https://github.com/openai/codex/issues/30919) — branch tree, commit graph, diff explorer |
| **Read Aloud / TTS** | 7 👍 | [#20957](https://github.com/openai/codex/issues/20957) — parity with ChatGPT’s accessibility features |
| **Disable hover sidebar expansion** | 1 👍 | [#31538](https://github.com/openai/codex/issues/31538) — ergonomics for large-screen/multi-monitor users |

**The dominant theme:** *User configurability.* The top three requests all ask for user-defined toggles on built-in behaviors (auto-resolve, sidebar hover, status line). The community increasingly wants control over the tool’s default UX decisions.

---

## Developer Pain Points

1. **Context window instability (Critical)**  
   Issue [#32806](https://github.com/openai/codex/issues/32806) reveals that GPT-5.6 Sol’s effective context has regressed by ~27% (353K → 258K). Combined with remote-compaction failures ([#33171](https://github.com/openai/codex/issues/33171)), long-running tasks are unreliable. Developers are being burned by silent model-config changes.

2. **Browser plugin fragility**  
   Two separate Windows crashes ([#30178](https://github.com/openai/codex/issues/30178), [#32683](https://github.com/openai/codex/issues/32683)) and a “Cannot redefine property: process” error ([#32925](https://github.com/openai/codex/issues/32925)) make the browser-use feature a reliability risk. The community is seeing crash rates high enough to avoid browser-based workflows.

3. **Session data visibility gaps**  
   Threads disappear from the UI while remaining on disk ([#25463](https://github.com/openai/codex/issues/25463)), remote sessions don’t appear in the remote control app ([#32957](https://github.com/openai/codex/issues/32957)), and SSH projects show “No chats” despite having saved threads ([#27284](https://github.com/openai/codex/issues/27284)). Data is present but unreachable — a coordination failure between the UI and the state database.

4. **Subscription entitlement confusion**  
   Pro20x subscribers seeing Plus-tier limits ([#29968](https://github.com/openai/codex/issues/29968)) suggests a class of billing/entitlement bugs that erode trust in paid tiers.

5. **Desktop app startup lag and phantom folders**  
   The app silently creates `~/Documents/Codex` ([#20880](https://github.com/openai/codex/issues/20880)) and random crashes cause severe startup lag ([#33197](https://github.com/openai/codex/issues/33197)). These quality-of-life issues compound to make the desktop experience feel unpolished for heavy users.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>

# Gemini CLI Community Digest — 2026-07-15

## Today's Highlights

Today’s nightly release (v0.52.0-nightly.20260714) brings two targeted fixes: enriched error messaging for shared project quota limits and a fix for task cancellation in the A2A server. On the issue tracker, the community continues to surface persistent agent reliability problems—subagent hang-on-max-turns misreporting success, the generalist agent freezing on simple tasks, and shell commands getting stuck after completion. Efforts to bound shell output and limit recursive reasoning turns are progressing through open PRs, addressing two long-standing sources of token waste and agent loops.

## Releases

**v0.52.0-nightly.20260714.gfa975395b** — [View Release](https://github.com/google-gemini/gemini-cli/releases/tag/v0.52.0-nightly.20260714.gfa975395b)
- **fix(core):** enrich shared project quota limit errors with setup hint ([#28391](https://github.com/google-gemini/gemini-cli/pull/28391))
- **fix(a2a-server):** ensure task cancellation aborts execution loop ([#2831](https://github.com/google-gemini/gemini-cli/pull/2831))

## Hot Issues

1. **[#22323](https://github.com/google-gemini/gemini-cli/issues/22323) — Subagent recovery after MAX_TURNS reported as GOAL success**  
   `codebase_investigator` reports `status: "success"` even after hitting the turn limit without doing analysis. This masks agent failures from users. 10 comments, 2 👍. **Why it matters:** Erroneous success reporting undermines trust in agent completion signals and blocks debugging.

2. **[#19873](https://github.com/google-gemini/gemini-cli/issues/19873) — Leverage model's bash affinity via Zero-Dependency OS Sandboxing**  
   Proposes using Gemini 3’s native POSIX skills with safe sandboxing instead of forcing it into structured tool use. 8 comments. **Why it matters:** Could fundamentally reduce latency and improve edit quality by letting the model operate in its preferred mode.

3. **[#21409](https://github.com/google-gemini/gemini-cli/issues/21409) — Generalist agent hangs forever**  
   Simple tasks like folder creation stall indefinitely when delegated to the generalist agent. Workaround: instruct the model not to use sub-agents. 7 comments, 8 👍. **Community sentiment:** This is the top-voted bug—users are frustrated by a dead-end UX.

4. **[#21968](https://github.com/google-gemini/gemini-cli/issues/21968) — Gemini does not use skills and sub-agents enough**  
   Despite custom skills (gradle, git), the model rarely invokes them unless explicitly instructed. 6 comments. **Why it matters:** Undermines the value of the agent skills system—users invest in configuration that the model ignores.

5. **[#25166](https://github.com/google-gemini/gemini-cli/issues/25166) — Shell command execution stuck with "Waiting input"**  
   Commands that have already completed remain in a hanging state. 4 comments, 3 👍. **Why it matters:** Breaks interactive workflows and forces manual kills.

6. **[#26522](https://github.com/google-gemini/gemini-cli/issues/26522) — Auto Memory retries low-signal sessions indefinitely**  
   Sessions that the extraction agent skips remain unprocessed, causing repeated re-prompts. 5 comments. **Why it matters:** Wastes API quota and creates noise in memory pipeline.

7. **[#22672](https://github.com/google-gemini/gemini-cli/issues/22672) — Agent should stop/discourage destructive behavior**  
   Model uses `git reset --force` and other destructive commands when safer alternatives exist. 3 comments, 1 👍. **Why it matters:** Highlights the need for safety guardrails in agent tool selection.

8. **[#24246](https://github.com/google-gemini/gemini-cli/issues/24246) — 400 error with > 128 tools**  
   Enabling many tools triggers API errors; the agent should scope tools intelligently. 3 comments. **Why it matters:** Limits scalability for power users with extensive tool configurations.

9. **[#21983](https://github.com/google-gemini/gemini-cli/issues/21983) — Browser subagent fails in Wayland**  
   The browser agent crashes with a false GOAL termination on Wayland environments. 4 comments. **Why it matters:** Linux users on modern display servers are blocked from a core feature.

10. **[#22093](https://github.com/google-gemini/gemini-cli/issues/22093) — Subagents running without permission since v0.33.0**  
    Agents mode set to disabled is ignored; sub-agents activate unexpectedly. 2 comments. **Why it matters:** Configuration trust regression—users expect their settings to be honored.

## Key PR Progress

1. **[#28319](https://github.com/google-gemini/gemini-cli/pull/28319) — Enforce path trust check before environment loading (A2A server)**  
   Ensures workspace trust is validated before loading environment variables. Uses `AsyncLocalStorage` for isolation. Large refactor with security implications.

2. **[#28164](https://github.com/google-gemini/gemini-cli/pull/28164) — Limit recursive reasoning turns per single request**  
   15-turn cap (configurable) to prevent infinite reasoning loops. Protects CPU, API quotas, and credits. Needs issue linking; has a nudging label.

3. **[#28401](https://github.com/google-gemini/gemini-cli/pull/28401) — Bound shell command output sent to the model**  
   Implements an output size limit for shell tool results. Prevents context blowout from verbose commands like `find /` or large `git log`. Directly addresses token waste.

4. **[#24303](https://github.com/google-gemini/gemini-cli/pull/24303) — Native V8 Memory & Profiling Suite**  
   GSoC 2026 proposal for terminal-integrated performance diagnostics. Adds memory profiling capabilities directly in the CLI.

5. **[#28400](https://github.com/google-gemini/gemini-cli/pull/28400) — Automated nightly version bump**  
   Housekeeping PR for release automation.

6. **[#28391](https://github.com/google-gemini/gemini-cli/pull/28391) — Enrich shared project quota errors with setup hint** (included in today's release)  
   Improves error messages to guide users on quota setup. Small UX win.

7. **[#2831](https://github.com/google-gemini/gemini-cli/pull/2831) — Ensure task cancellation aborts execution loop** (included in today's release)  
   Prevents orphaned executions when tasks are cancelled in A2A server.

8. ***(Relevant prior PR in backlog)* — Behavioral eval tests (tracked in #15300 / #24353 EPIC)**  
   The team has generated 76 behavioral eval tests running across 6 models. EPIC #24353 targets robust component-level evaluations.

9. ***(AST-aware codebase mapping PRs)* — Follows EPIC #22745**  
   Investigating tilth/glyph for AST-aware file reads and codebase mapping. Could reduce token waste from misaligned reads.

10. ***(Auto Memory PRs)* — Tracks issues #26522, #26523, #26525**  
    Pending work to quarantine invalid patches, add deterministic redaction, and stop low-signal retries.

## Feature Request Trends

- **Agent self-awareness & introspection** — Users want the CLI to understand its own hotkeys, flags, mechanics, and report subagent trajectories via `/chat share` ([#21432](https://github.com/google-gemini/gemini-cli/issues/21432), [#22598](https://github.com/google-gemini/gemini-cli/issues/22598)).
- **AST-aware code manipulation** — Multiple EPICs ask for AST-based file reading, search, and mapping to reduce token waste and improve edit precision ([#22745](https://github.com/google-gemini/gemini-cli/issues/22745), [#22746](https://github.com/google-gemini/gemini-cli/issues/22746)).
- **Native OS sandboxing** — Let the model use its bash affinity directly with zero-dependency sandboxing instead of forcing structured tools ([#19873](https://github.com/google-gemini/gemini-cli/issues/19873)).
- **Robust component-level evaluations** — Scaling behavioral evals from 76 to comprehensive coverage across model versions is a recurring theme ([#24353](https://github.com/google-gemini/gemini-cli/issues/24353)).
- **Safety guardrails** — Destructive command prevention, scope-limited tool access, and permission enforcement are increasingly requested ([#22672](https://github.com/google-gemini/gemini-cli/issues/22672), [#22093](https://github.com/google-gemini/gemini-cli/issues/22093)).

## Developer Pain Points

- **False success signals** — Sub-agents hitting turn limits report `GOAL: success`, masking failures and complicating debugging (#22323, #21983).
- **Agent hangs and stuck shells** — Generalist agent freezes on trivial tasks (#21409), shell commands remain in "Waiting input" state post-completion (#25166), interactive prompts get stuck (#22465).
- **Model ignores configuration** — Agents don't respect disabled flags (#22093), ignore settings.json overrides for maxTurns (#22267), and under-utilize custom skills (#21968).
- **Token waste and performance regressions** — Unbounded shell output (#28401 open), terminal resize flicker (#21924), corruption after external editor exit (#24935), and infinite retries in Auto Memory (#26522).
- **Tooling limits** — 400 errors with >128 tools (#24246), symlinks not recognized as agents (#20079), browser agent fails on Wayland (#21983).
- **Recovery from edge cases** — Crash on `get-shit-done` output hook (#22186), memory system logging security concerns (#26525), and malformed memory patches silently dropped (#26523).

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

# GitHub Copilot CLI Community Digest — 2026-07-15

## Today's Highlights
Two fresh releases (v1.0.71-1 and v1.0.71-2) rolled out 24 hours ago, bringing persistent sidebar sessions, plugin marketplace management, and canvas support for extensions. The community is heavily engaged on a persistent 400-error bug (#1274) affecting code reviews, and a new wave of triage-level issues surfaced around agent.md handling, background agent cancellation, and terminal rendering quirks.

## Releases
**v1.0.71-2** — Most recent patch:
- **Added:** `/voice devices` command to choose and persist microphone for voice mode; ability to limit which built-in agents are available to tasks/subagents; canvas support in the CLI for extension-driven interactions.
- **Improved:** `/chronicle cost-tips` now includes richer cost profiles.

**v1.0.71-1** — Earlier patch:
- **Added:** Persist GitHub MCP toolset/tool config via `settings.json`; `plugins marketplace` subcommands (list, add, remove, browse, update); sidebar sessions now survive restarts.
- **Notable:** This release introduced the plugin marketplace infrastructure but also appears to have triggered Git credential helper regressions (see #4103).

## Hot Issues

1. **#1274 — CLI constantly getting 400 errors for invalid request body**  
   *[area:tools] — Author: unusualbob*  
   🔥 25 comments, 11 👍. 95% of code-review attempts fail with 400 errors. Debug logs suggest possible server-side validation mismatch or malformed request crafting by the CLI. This is the highest-activity open issue and a blocker for power users relying on automated diff review.

2. **#4024 — Voice mode ASR models fail silently**  
   *[area:models] — Author: sylvanc*  
   All three bundled speech-recognition models (`nemotron-3.5-asr`, `nemotron-speech-streaming`, `whisper-large-v3`) return empty transcriptions despite successful audio capture. Likely a `MultiModalProcessor` routing bug in Foundry Local Core. Critical for voice-mode adopters.

3. **#443 — Built-in PDF reading support**  
   *[area:tools] — Author: non-stop-dev*  
   🏆 33 👍, highest-voted feature request. Users want native PDF parsing to work with academic papers and technical docs without installing external tools like `pdftotext`. Persistent demand with 5 comments since Oct 2025.

4. **#2165 — Ubuntu keychain support broken**  
   *[area:platform-linux, area:authentication] — Author: AndreaPi*  
   21 👍. Two bugs: incorrect documentation for `secret-tool` setup, plus a deeper keychain integration failure. Affects all Linux users relying on credential storage for sessions.

5. **#4096 — Third-party MCP server tools missing from CLI sessions**  
   *[area:authentication, area:mcp] — Author: bugale*  
   OAuth-connected MCP servers show "Connected" in the app but tools never appear in CLI sessions — the OAuth token is not bridged. Blocks integration with Atlassian and other remote MCP providers.

6. **#4097 — `apply_patch` stores deleted binary in session history, exceeding 5 MB CAPI limit**  
   *[area:sessions, area:context-memory, area:tools] — Author: Adamkadaban*  
   Deleting a large binary via `apply_patch` stores the entire file as a textual diff in conversation history. Subsequent requests blow past the 5 MB limit; `/compact` cannot recover. A memory-management pain point for large repositories.

7. **#4103 — Plugin marketplace clone disables Git credential helpers**  
   *[area:authentication, area:plugins] — Author: arnab9211*  
   A regression from v1.0.70's "fail fast" Git auth change breaks cloning from private Azure DevOps HTTPS repos, even though manual clones with GCM work fine. Affects enterprise plugin adoption.

8. **#4054 — `/resume` broken for non-GitHub repos (ADO, non-git sessions)**  
   *[area:sessions] — Author: Fabi0San*  
   `/resume` hard-codes GitHub host checks, rejecting Azure DevOps repos entirely, and also fails for sessions without any git context. Blocks users with mixed-VCS workflows.

9. **#4118 — `/app` command does not select current working directory by default**  
   *[triage] — Author: doggy8088*  
   32 👍 in one day. Users launching the Copilot app via `/app` must manually navigate to their working directory — a friction point for multi-project developers.

10. **#4111 — Windows: orphaned `copilot.exe.old` processes spin at 100% CPU**  
    *[area:sessions, area:platform-windows, area:installation] — Author: RockNoggin*  
    Long-running sessions that survive an in-place auto-update continue executing from the renamed binary and peg one CPU core indefinitely. Critical for Windows users with persistent sessions.

## Key PR Progress
*No pull requests were updated in the last 24 hours.* Development activity appears concentrated on issue triage and release patches rather than merged PRs today.

## Feature Request Trends
- **PDF/document reading** (#443, 33 👍): Consistent highest-voted request for native parsing of PDFs, EPUB, and other document formats without external tools.
- **Agent customization & agents.md** (#4123, #4122): Multiple users report `AGENTS.MD` being ignored, and subagents fail to resolve relative markdown links — indicating a desire for reliable, customizable agent definitions.
- **Color/theme customization** (#4117): Users want granular control over terminal colors and contrast, especially for accessibility.
- **Conversation context visibility** (#4124): Request to show session title inline without navigating to `/session`, for easier multitasking.
- **Double-tap Enter to interrupt** (#4125): Inspired by Grok CLI, users want to send a new prompt immediately without waiting for the current execution to finish.

## Developer Pain Points
- **400 errors on code review** (#1274): Persistent and high-volume — 95% failure rate is a showstopper for anyone relying on automated diff review.
- **Voice mode dead on arrival** (#4024): All ASR models return empty results; the feature is effectively broken for current users.
- **Session data loss** (#4115): Sessions from multiple days lost after unexpected restart; flush-to-disk only happens on clean exit, not periodically.
- **Terminal rendering glitches** (#4116, #4126, #4121, #4114): Copy-paste includes box-drawing characters; right-click pastes unintended content; terminal title degrades to ";" in SecureCRT; confirmation cards cannot be dismissed.
- **Background agent cancellation** (#4127): Submitting a new user turn cancels background agents, losing work in progress.
- **ACP protocol gaps** (#4113): `session/close` never advertised, so ACP clients cannot cleanly release sessions — a protocol-level omission.

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

# Kimi Code CLI Community Digest
**Date:** 2026-07-15

---

## Today's Highlights
Three critical fixes landed today addressing faulty completion budget logic, implicit reasoning parameter serialization, and a protocol-level empty-string handling bug. A long-standing TPD rate limit issue (#2318) remains open, affecting heavy users on Windows, while a forked session corruption bug (#2496) was quietly resolved without community fanfare.

---

## Releases
No new releases in the last 24 hours. Latest stable version remains **kimi 2.6**.

---

## Hot Issues

1. **[#2318] request reached organization TPD rate limit (current: 1505241)** — Open for 58 days. A Windows user on kimi 2.6 hitting Moonshot's TPD ceiling with the kimi2.6 model. Only 1 comment suggests limited maintainer engagement. **Why it matters:** High-impact bug for power users; the reported volume (~1.5M tokens/day) indicates aggressive automation or CI integration. [GitHub](https://github.com/MoonshotAI/kimi-cli/issues/2318)

2. **[#2496] resuming forked session results in corrupted output** — Closed without discussion. User on kimi 1.36.0 with subscription plan experienced garbled output when using `kimi -r` on a forked session. Silent resolution may indicate a trivial fix or a known edge case. [GitHub](https://github.com/MoonshotAI/kimi-cli/issues/2496)

---

## Key PR Progress

1. **[#2494] fix(kimi): use remaining context for completion budget** — **CLOSED.** Replaces the hardcoded 32k completion cap with dynamic budgeting based on remaining model context window. Only affects Kimi requests (including ChaosChatProvider-wrapped Kimi). **Impact:** Reduces token waste and unnecessary truncation for long conversations. [GitHub](https://github.com/MoonshotAI/kimi-cli/pull/2494)

2. **[#2498] fix(kosong): preserve empty-string reasoning_content as ThinkPart** — **CLOSED.** Fixes a 400 error from `coding-model-okapi-0711-vibe` when `thinking.keep=all` mode encounters an assistant message missing `reasoning_content`. Previously empty strings were dropped, breaking protocol contracts. **Impact:** Unblocks advanced reasoning-trace workflows. [GitHub](https://github.com/MoonshotAI/kimi-cli/pull/2498)

3. **[#2499] fix(kosong): stop sending Kimi reasoning effort implicitly** — **CLOSED.** Stops automatically serializing the legacy `reasoning_effort` parameter. Thinking configuration is now exclusively handled via `thinking.type`, preserving caller-provided values without clamping or reverse-mapping. **Impact:** Eliminates silent override of user-specified thinking effort. [GitHub](https://github.com/MoonshotAI/kimi-cli/pull/2499)

---

## Feature Request Trends
*No feature requests surfaced in recent issues/PRs.* The activity is dominated by bug fixes, suggesting maintainers are in a stabilization phase rather than adding new capabilities.

---

## Developer Pain Points

- **Rate limiting without actionable feedback:** Issue #2318 demonstrates that hitting TPD limits (over 1.5M tokens) provides no guidance on mitigation or whether the limit is per-org or per-key.
- **Version fragmentation:** Issues reference both the stable release (2.6) and an older version (1.36.0), indicating some users run legacy builds despite updates being available.
- **Windows stability concerns:** Both hot issues (#2318, #2496) affect Windows 10 users, hinting at platform-specific bugs that may receive less testing than Linux/macOS due to the developer tool audience.

*Note: No PRs were available for community commenting; all three PRs in the window show 0 comments, suggesting maintainers may merge internally without review cycles.*

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

# OpenCode Community Digest — 2026-07-15

## Today's Highlights
Desktop v1.18.0/v1.18.1 shipped with the complete v2 UI migration, but the rollout triggered a wave of regression reports—Plan/Build mode selectors and agent pickers disappearing on Windows, session history failing to load on VPS-hosted instances, and tab titles overflowing. Meanwhile, the community contributor @ohsalmeron submitted a complete suite of UX enhancement PRs (fork buttons, inline rename, context compaction, archived session browser), indicating strong grassroots demand for session management polish. The team also merged xAI Grok OAuth support for v2 and is progressing on a V2 theming system for the TUI.

## Releases
### v1.18.1 (Hotfix)
- **Desktop bugfix:** Fixed spacing between model provider sections in Settings.

### v1.18.0 (Desktop v2 Migration)
- **Improvements:** Completed Desktop v2 migration with upgrade handling for the new layout and first-launch onboarding.
- **Transition:** Added a setting to switch between new and old Desktop layouts during the transition period.
- **Bugfix:** Fixed file views using the wrong background color.

## Hot Issues (10 Notable)

1. **[#28957](https://github.com/anomalyco/opencode/issues/28957) — "Upstream idle timeout exceeded"** *(Comments: 20, 👍: 2)*  
   **Why it matters:** A recurring infrastructure error tied to the `writing-plans` skill on macOS Tahoe (Apple M4). The upstream connection between client and model service idles out, suggesting a timeout configuration mismatch in the new v2 session layer. Community is watching for a fix as it blocks plan-generation workflows.

2. **[#12472](https://github.com/anomalyco/opencode/issues/12472) — Native Claude Code hooks compatibility** *(Comments: 16, 👍: 37)*  
   **Why it matters:** The most upvoted open feature request. OpenCode already supports Claude Code rules and skills, but the hooks system (`PreToolUse`, `PostToolUse`, `Stop`) remains unimplemented. The high 👍 count signals strong enterprise demand for interoperability with existing Claude Code agent pipelines.

3. **[#25239](https://github.com/anomalyco/opencode/issues/25239) — Expose GitHub Copilot "Auto" model option** *(Comments: 16, 👍: 14)*  
   **Why it matters:** Users want OpenCode to intelligently select the best model per-task, mirroring Copilot's auto-selection behavior. This would reduce friction for users who switch between fast/slow models manually.

4. **[#36936](https://github.com/anomalyco/opencode/issues/36936) — Desktop: new tab layout hides session titles** *(Comments: 10, 👍: 5)*  
   **Why it matters:** A v2 migration regression—horizontal tabs truncate session titles, making multi-session management impossible. User @simPod reports reverting to v1.17 fixes it. This is a UI-blocker for power users.

5. **[#32747](https://github.com/anomalyco/opencode/issues/32747) — @ file mentions miss files created after startup** *(Comments: 10, 👍: 8)*  
   **Why it matters:** A stale search state bug in the TUI autocomplete. New files are invisible until restart, breaking the core `@file` workflow. Community analysis points to missing index invalidation in the TUI component.

6. **[#31972](https://github.com/anomalyco/opencode/issues/31972) — New Layout breaks Plan/Build toggle** *(Comments: 8, 👍: 8)*  
   **Why it matters:** On Windows 10 with the new layout, Plan/Build mode switching via UI or `Ctrl+.` stops working entirely. This is a critical regression—Plan/Build is a path-defining OpenCode workflow.

7. **[#36979](https://github.com/anomalyco/opencode/issues/36979) — Agents invisible when switching + folders not expanding (v1.18.1, Windows)** *(Comments: 5, 👍: 0)*  
   **Why it matters:** Two v2 UI regressions on Windows: agent dropdowns don't render on `Ctrl+.`, and the central file explorer's folder tree is broken. Reports are fresh (today), likely gaining traction.

8. **[#36971](https://github.com/anomalyco/opencode/issues/36971) — Session history not loading on VPS-hosted desktop** *(Comments: 3, 👍: 0)*  
   **Why it matters:** Server-side OpenCode deployments lost session history after the v2 layout update. This affects remote/team use cases where the desktop connects to a VPS backend.

9. **[#36942](https://github.com/anomalyco/opencode/issues/36942) — Feature: Vertical tabs** *(Comments: 3, 👍: 2)*  
   **Why it matters:** The new layout forces horizontal tabs, limiting visibility to ~5 sessions. Vertical tabs are requested as a remedy for the tab overflow regression (#36936).

10. **[#36877](https://github.com/anomalyco/opencode/issues/36877) — Reasoning thoughts not shown** *(Comments: 2, 👍: 0)*  
    **Why it matters:** GPT 5.6 reasoning thoughts (emitted as HTML comments) are not rendered. OpenAI's backend fix landed, but OpenCode hasn't updated its parser. Affects users relying on reasoning traces for debugging.

## Key PR Progress (10 Important)

1. **[#36894](https://github.com/anomalyco/opencode/pull/36894) — Expand reasoning option variants** *(Open)*  
   **Summary:** Expands model reasoning effort/budget mappings across providers with conditional toggles (`none/thinking`, `none/high/max`). Needed for fine-grained control over thinking budgets.

2. **[#36542](https://github.com/anomalyco/opencode/pull/36542) — Tolerate AlreadyExists in FSUtil.ensureDir** *(Open)*  
   **Summary:** Fixes a crash in `Config.ensureGitignore` when directories already exist. Closes [#35828](https://github.com/anomalyco/opencode/issues/35828). A stability fix for config resolution.

3. **[#36968](https://github.com/anomalyco/opencode/pull/36968) — Archived sessions browser dialog** *(Open)*  
   **Summary:** Introduces `/archived` slash-command with a searchable dialog for browsing archived sessions. Pure UX improvement from community member @ohsalmeron.

4. **[#36967](https://github.com/anomalyco/opencode/pull/36967) — Delete session with confirmation dialog** *(Open)*  
   **Summary:** Adds right-click "Delete Session" with confirmation dialog to the sidebar. Addresses the long-standing lack of UI-based session deletion.

5. **[#36966](https://github.com/anomalyco/opencode/pull/36966) — Inline session rename in sidebar** *(Open)*  
   **Summary:** Double-click inline renaming in sidebar using existing `InlineEditor` component. Matches workspace rename UX.

6. **[#36965](https://github.com/anomalyco/opencode/pull/36965) — Fork button on assistant responses** *(Open)*  
   **Summary:** One-click fork on every assistant message, creating a branched session from that point. Eliminates command palette dependency.

7. **[#36964](https://github.com/anomalyco/opencode/pull/36964) — One-click context compaction button** *(Open)*  
   **Summary:** Adds a compact button next to the context usage indicator to trigger `/compact` without the command palette. A major UX win for long sessions.

8. **[#36919](https://github.com/anomalyco/opencode/pull/36919) — Restore xAI OAuth in v2** *(Closed, Merged)*  
   **Summary:** Ports xAI browser OAuth and device-code flow to the v2 integration API. Fixes [#36917](https://github.com/anomalyco/opencode/issues/36917). Critical for SuperGrok subscribers.

9. **[#36950](https://github.com/anomalyco/opencode/pull/36950) — V2 theme system** *(Closed, Merged)*  
   **Summary:** Adds Effect Schema-based V2 theme definitions with property-first component accessors, hue aliases, and deterministic V1→V2 migration. Foundation for incremental theme migration.

10. **[#36752](https://github.com/anomalyco/opencode/pull/36752) — Read cache write tokens from raw usage** *(Open)*  
    **Summary:** Fixes Anthropic models via OpenAI gateways always reporting `cache.write: 0`, causing misbilling. Fixes [#36749](https://github.com/anomalyco/opencode/issues/36749).

## Feature Request Trends
- **Session Management UX** — The largest cluster: archived session browsing (#36963), inline sidebar rename (#36961), delete with confirmation (#36962), fork button on messages (#36960), and one-click context compaction (#36959). All from @ohsalmeron, suggesting a coordinated UX push.
- **Vertical/Configurable Tab Layout** — Multiple issues (#36936, #36942) request vertical tabs or wider tab display as a reaction to the new horizontal-only layout.
- **Claude Code Hooks Parity** — #12472 remains the most-upvoted open feature, seeking `PreToolUse`/`PostToolUse`/`Stop` hooks for enterprise compatibility.
- **Configurable Web Search** — #36513 asks for switching away from Exa AI as the sole built-in web search provider.
- **Model Auto-Selection** — #25239's "GitHub Copilot Auto" request hints at desire for intelligent, context-aware model routing.

## Developer Pain Points
- **v2 Desktop Migration Regressions** — The dominant theme today. Plan/Build mode selectors disappear (#31972, #36957, #36981), agent pickers go invisible (#36979, #36983), tab titles overflow (#36936), and session history fails on VPS (#36971). Many users are reverting to v1.17.
- **Stale File Index in TUI** — `@file` mentions miss newly created files until restart (#32747). A repeated complaint about the TUI search state not refreshing.
- **Reasoning Thoughts Not Rendering** — GPT 5.6 reasoning traces are invisible in OpenCode (#36877). Users rely on these for debugging model behavior.
- **Plugin Discovery UX** — Local plugins shown as raw `file://` paths in the status popover (#36956, #34953), making it impossible to identify plugins at a glance.
- **Upstream Timeout Instability** — The "upstream idle timeout" error (#28957) on macOS Tahoe with `writing-plans` skill suggests infrastructure fragility in the session proxy layer, especially after OS updates.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>

# Pi Community Digest — 2026-07-15

## Today's Highlights

Pi v0.80.7 shipped with a breaking change to session-affinity configuration, replacing the `openai-responses` `sendSessionIdHeader` flag with a unified `sessionAffinityFormat` setting. The community is heavily focused on model catalog expansion and OAuth integration, with multiple PRs landing for xAI SuperGrok login and GitHub Copilot model support. A significant backend regression in `httpIdleTimeoutMs` for self-hosted providers remains under active investigation.

---

## Releases

**v0.80.7** — Breaking Changes
- Removed the `openai-responses` `compat.sendSessionIdHeader` flag from `models.json`
- Session-affinity behavior is now controlled by `compat.sessionAffinityFormat` (`“openai”`, `“openai-nosession”`, or `“openrouter”`)
- Migration path: replace `sendSessionIdHeader: false` with `sessionAffinityFormat: “openai-nosession”`

---

## Hot Issues

**#5363** — [OPEN] Add amazon-bedrock-mantle provider for OpenAI-compatible models  
*Author: tasadurian | 16 comments | 8 👍*  
Amazon Bedrock Mantle models use an OpenAI-compatible API that is incompatible with the existing Converse-based Bedrock provider. High community demand for this provider.  
🔗 [github.com/earendil-works/pi Issue #5363](https://github.com/earendil-works/pi/issues/5363)

**#6476** — [OPEN] [bug, inprogress] Regression: httpIdleTimeoutMs no longer respected for self-hosted OpenAI-compatible provider  
*Author: hoho51 | 10 comments*  
Upgrading from v0.80.3 to v0.80.6 breaks self-hosted vLLM deployments with premature timeouts despite explicit `httpIdleTimeoutMs` settings. This is a critical regression for on-premise users.  
🔗 [github.com/earendil-works/pi Issue #6476](https://github.com/earendil-works/pi/issues/6476)

**#6522** — [CLOSED] openai-completions: no min floor on max_completion_tokens, sends 1 token → 400 Bad Request  
*Author: sh1ftred | 7 comments*  
Missing minimum validation on `max_completion_tokens` causes upstream rejections when proxy-reported context is inflated. Typically affects custom proxy setups where auto-compact is disabled.  
🔗 [github.com/earendil-works/pi Issue #6522](https://github.com/earendil-works/pi/issues/6522)

**#6509** — [OPEN] [inprogress] Extension-reported usage in the footer cost display  
*Author: LukasParke | 5 comments*  
Proposes `ctx.ui.setUsage(key, usage)` so extensions (subagents, child processes) can report external LLM costs in the footer. Important for extension ecosystem visibility and cost tracking.  
🔗 [github.com/earendil-works/pi Issue #6509](https://github.com/earendil-works/pi/issues/6509)

**#6624** — [CLOSED] Add GPT-5.6 models to GitHub Copilot  
*Author: sheurich | 5 comments*  
Requests `gpt-5.6-luna`, `gpt-5.6-terra`, and `gpt-5.6-sol` be added to Pi's built-in model catalog for the `github-copilot` provider. Already resolved via PR #6636.  
🔗 [github.com/earendil-works/pi Issue #6624](https://github.com/earendil-works/pi/issues/6624)

**#3200** — [OPEN] Support video/audio content in prompt command  
*Author: louis030195 | 5 comments | 3 👍*  
Extension request to forward video/audio alongside existing image support for multimodal models (Gemma 4, GPT-4o). Long-standing request since April, still open.  
🔗 [github.com/earendil-works/pi Issue #3200](https://github.com/earendil-works/pi/issues/3200)

**#6374** — [OPEN] [inprogress] Model catalog fixes — reasoning-level metadata conflicts  
*Author: hyperknot | 3 comments | 1 👍*  
Popular models have conflicting reasoning-level metadata across providers, breaking deduplicated catalogs for downstream apps. Community member verified against first-party documentation.  
🔗 [github.com/earendil-works/pi Issue #6374](https://github.com/earendil-works/pi/issues/6374)

**#6167** — [OPEN] [bug] transformMessages + thinking block normalization with compat flags  
*Author: dljsjr | 3 comments*  
When switching models mid-session, thinking block normalization inlines non-redacted thinking content into assistant messages, interacting poorly with `requiresReasoningContentOnAssistantMessages`. Subtle but impactful for thinking-model workflows.  
🔗 [github.com/earendil-works/pi Issue #6167](https://github.com/earendil-works/pi/issues/6167)

**#6600** — [OPEN] [bug] pi update --extensions blocks npm scripts with new npm 11.16.0  
*Author: nulladdict | 3 comments*  
npm 11.16.0 blocks install scripts by default, breaking Pi's extension update flow. Affects all users running extension updates, especially on npm >=11.16.  
🔗 [github.com/earendil-works/pi Issue #6600](https://github.com/earendil-works/pi/issues/6600)

**#5329** — [OPEN] Expose when Pi is waiting on user input for host integrations  
*Author: ofa1 | 2 comments | 3 👍*  
Host integrations (e.g., cmux) need a coarse indicator to distinguish between active LLM turns and user-input-blocked states. High community interest for integration tooling.  
🔗 [github.com/earendil-works/pi Issue #5329](https://github.com/earendil-works/pi/issues/5329)

---

## Key PR Progress

**#6656** — [CLOSED] feat(ai): add xAI subscription OAuth  
*Author: richardanaya*  
Implements OAuth login for xAI SuperGrok subscriptions. Closes #6626. No tools included — just OAuth support.  
🔗 [github.com/earendil-works/pi PR #6656](https://github.com/earendil-works/pi/pull/6656)

**#6651** — [CLOSED] feat(ai): add xAI device OAuth and route grok-4.5 through Responses  
*Author: Jaaneek*  
Adds xAI device-code OAuth alongside existing API key authentication. Routes only `grok-4.5` through Responses API with configurable reasoning levels. Closes #6461.  
🔗 [github.com/earendil-works/pi PR #6651](https://github.com/earendil-works/pi/pull/6651)

**#6636** — [CLOSED] feat(ai): refresh generated model catalogs  
*Author: guru-balamurugan*  
Refreshes model catalogs from current models.dev data. Adds `gpt-5.6-luna`, `gpt-5.6-sol`, `gpt-5.6-terra` for GitHub Copilot provider. Addresses #6624.  
🔗 [github.com/earendil-works/pi PR #6636](https://github.com/earendil-works/pi/pull/6636)

**#6216** — [OPEN] feat: Add Amazon Bedrock Mantle OpenAI Responses provider  
*Author: unexge*  
New provider for Bedrock Mantle's OpenAI-compatible API. Uses OpenAI Bedrock Provider SDK. Supersedes earlier implementations (closes #5363). Still open for review.  
🔗 [github.com/earendil-works/pi PR #6216](https://github.com/earendil-works/pi/pull/6216)

**#6654** — [OPEN] feat(ai): add promptCacheKey stream option  
*Author: alasano*  
Adds opt-in `promptCacheKey` to StreamOptions, replacing `sessionId` in prompt_cache_key generation for OpenAI-compatible providers. Useful for custom caching strategies. Closes #6627.  
🔗 [github.com/earendil-works/pi PR #6654](https://github.com/earendil-works/pi/pull/6654)

**#6594** — [OPEN] feat: sqlite session storage  
*Author: cristinaponcela*  
Adds `retainedTail` to compaction entries and optimizes tree walking for session storage. Aims to improve startup performance and compaction efficiency. Still WIP.  
🔗 [github.com/earendil-works/pi PR #6594](https://github.com/earendil-works/pi/pull/6594)

**#6584** — [CLOSED] fix: forward provider options to summary requests  
*Author: xl0*  
Ensures compaction/summary calls inherit session transport settings (e.g., websocket vs SSE). Closes #6555, fixing a bug where compaction used wrong transport.  
🔗 [github.com/earendil-works/pi PR #6584](https://github.com/earendil-works/pi/pull/6584)

**#6653** — [CLOSED] clamp session-id to 64 chars for openai-codex  
*Author: davidbrai*  
Clamps session ID headers to 64 characters, matching existing body-side clamping. Prevents the ChatGPT backend from rejecting long session IDs. Fixes #6630.  
🔗 [github.com/earendil-works/pi PR #6653](https://github.com/earendil-works/pi/pull/6653)

**#6635** — [CLOSED] fix(ai): recover openai-completions tool calls emitted in content  
*Author: cachrisman*  
Handles local inference servers (Ollama, LM Studio) that return valid tool-call JSON in `content` but empty `tool_calls`. Critical for self-hosted developers.  
🔗 [github.com/earendil-works/pi PR #6635](https://github.com/earendil-works/pi/pull/6635)

**#6533** — [CLOSED] fix: Codex compaction returns “Model not found” for gpt-5.6-luna  
*Author: PriNova*  
Fixes compaction failures for gpt-5.6-luna on OpenAI Codex by correctly mapping model IDs to tier-suffixed slugs.  
🔗 [github.com/earendil-works/pi PR #6533](https://github.com/earendil-works/pi/pull/6533)

---

## Feature Request Trends

**Provider expansion** dominates this cycle: multiple requests for new OAuth-based logins (xAI SuperGrok, Grok subscription), new cloud provider integrations (Amazon Bedrock Mantle), and extended model catalog coverage (GPT-5.6 variants for GitHub Copilot). There's growing demand for **multimodal content support** (video/audio in addition to images for prompt commands) and **extension API enhancements** (cost reporting via `ctx.ui.setUsage()`, user-input-waiting state for host integrations).

A secondary trend is **prompt cache optimization**: users want stable system prompts, controllable compaction, and prepend-only growth strategies to maximize provider-side KV cache hits. The `promptCacheKey` stream option PR directly addresses this pattern.

---

## Developer Pain Points

1. **Self-hosted provider reliability**: The `httpIdleTimeoutMs` regression (#6476) is a top concern for on-premise vLLM/OpenAI-compatible deployments. Startup time complaints (#6075) also persist.

2. **npm ecosystem friction**: The npm 11.16.0 script-blocking change (#6600) breaks extension update automation, requiring manual workarounds.

3. **Session ID handling quirks**: Multiple issues around session ID clamping (64-char limit for codex, hardcoded originator headers blocking model access) indicate fragile session management across providers.

4. **Compaction and summarization edge cases**: Several issues surfaced around compaction not inheriting transport settings (#6555), oversized image estimates retaining too much context (#6603), and compaction failures for specific models (#6533). Proactive compaction after responses (#6606) is another pain point.

5. **Model catalog inconsistency**: Reasoning-level metadata conflicts (#6374) across providers make building reliable downstream catalogs difficult, suggesting the upstream model data source may need validation improvements.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>

# Qwen Code Community Digest — 2026-07-15

---

## 1. Today's Highlights

The project shipped **v0.19.10 stable** with multi-workspace support now spanning ACP transport, daemon workers, and split-view sessions — a major architectural milestone. Security hardening continues with multiple fixes around MCP trust validation, permission path canonicalization, and daemon secret sanitization. A new automated PR patrol CI feature aims to surface regressions faster, addressing long-standing complaints about integration test gaps.

---

## 2. Releases

### v0.19.10 (Stable)
- **[Release](https://github.com/QwenLM/qwen-code/releases/tag/v0.19.10)** — **Multi-workspace support** now fully integrated across ACP transport, daemon workers, split-view sessions, and workspace-aware actions. This is the culmination of a multi-week RFC process (#6378), enabling one daemon to serve multiple independent workspaces while preserving backward compatibility for single-workspace clients.

### v0.19.10-nightly.20260715.c538bd70d
- Nightly build with `docs(review): cap PR scope after repeated review rounds` and `feat(web-shell): add workspace path lock`.

### v0.19.9-preview.0
- Preview release with the same scope-capping documentation change and workspace path lock.

### sdk-typescript-v0.1.8
- Bundles CLI v0.19.10 (latest stable). Provides TypeScript bindings for the Qwen Code ACP protocol.

---

## 3. Hot Issues (Top 10)

1. **[#6378](https://github.com/QwenLM/qwen-code/issues/6378) — RFC: Support multiple workspaces in one qwen serve daemon** (23 comments, OPEN)
   - The most-discussed issue in the tracker. Proposes a 1-to-many daemon-to-workspace model. Strong community engagement — the ideas are now shipping in v0.19.10.

2. **[#3696](https://github.com/QwenLM/qwen-code/issues/3696) — Comprehensive hot-reload system** (7 comments, CLOSED)
   - Tracking issue now complete: runtime hot reload covers settings-driven MCP reconnection, extension reload, and configuration updates without session restart.

3. **[#4748](https://github.com/QwenLM/qwen-code/issues/4748) — Optimize daemon cold start and fast-path latency** (5 comments, OPEN)
   - Cold-start gap between daemon (~2.5s) and CLI (~0.7s) has narrowed but remains a target. Critical for headless/CI adoption.

4. **[#5979](https://github.com/QwenLM/qwen-code/issues/5979) — Bug: /auth config changes not applied to new sessions** (5 comments, CLOSED)
   - Model provider config changed via `/auth` worked for the current session but failed on new sessions with 401 errors. A blocker for multi-session workflows.

5. **[#5219](https://github.com/QwenLM/qwen-code/issues/5219) — CI: integration tests don't run on PR/merge** (5 comments, CLOSED)
   - Regressions only surfaced at release time. The new PR failure patrol (PR #6766) is a direct response to this long-standing pain point.

6. **[#6809](https://github.com/QwenLM/qwen-code/issues/6809) — Ctrl+S diff preview garbled for multi-line edits** (4 comments, OPEN)
   - UI regression: multi-line edit diffs in permission dialogs concatenate lines. Affects the core "approve before write" workflow.

7. **[#6149](https://github.com/QwenLM/qwen-code/issues/6149) — VP mode breaks link interaction; non-VP cannot scroll** (4 comments, OPEN)
   - Two related TUI bugs: hyperlinks broken in VP mode, overflow content unscrollable in non-VP mode. Impacts terminal-based power users.

8. **[#6898](https://github.com/QwenLM/qwen-code/issues/6898) — Shell tool confirmation fires on every tool call instead of task end** (3 comments, OPEN)
   - Strong sentiment: users report "dozens of popups per task." Requests task-level confirmation aggregation.

9. **[#6487](https://github.com/QwenLM/qwen-code/issues/6487) — Memory index stale after /remember; memory lost on compaction** (3 comments, OPEN)
   - Long-session reliability issue: memory degrades through index staleness and compaction loss. Critical for autonomous workflow users.

10. **[#6917](https://github.com/QwenLM/qwen-code/issues/6917) — Untrusted MCP readOnlyHint skips default tool confirmation** (2 comments, OPEN)
    - Security finding: `readOnlyHint: true` from untrusted MCP servers bypasses permission checks. Being addressed in PR #6924.

---

## 4. Key PR Progress (Top 10)

1. **[#6926](https://github.com/QwenLM/qwen-code/pull/6926) — fix(mcp): terminate descendants after discovery timeout**
   - Ensures orphan processes are cleaned up when stdio MCP discovery times out. Prevents resource leaks in complex MCP setups.

2. **[#6923](https://github.com/QwenLM/qwen-code/pull/6923) — fix(core): canonicalize restrictive permission paths**
   - Resolves #6915 by comparing both supplied and canonical file paths against permission rules, catching symlink and `..` traversal bypasses.

3. **[#6900](https://github.com/QwenLM/qwen-code/pull/6900) — fix(cli): don't mutate cached trusted-folders on preview check**
   - Fixes #6831: trust-status preview checks were leaking unconfirmed trust state into the persistent config. A subtle but serious security bug.

4. **[#6902](https://github.com/QwenLM/qwen-code/pull/6902) — fix(vscode-companion): non-boundary @ no longer suppresses slash completion**
   - UX fix: email addresses containing `@` no longer break `/`-command completion in VS Code chat input.

5. **[#6606](https://github.com/QwenLM/qwen-code/pull/6606) — fix(core): sanitize internal daemon secrets from shell subprocess environments**
   - Security: prevents daemon API keys and tokens from leaking into spawned shell environments. Large and thoroughly reviewed.

6. **[#6924](https://github.com/QwenLM/qwen-code/pull/6924) — fix(mcp): require trust for read-only auto-approval**
   - Fixes #6917: `readOnlyHint` no longer grants automatic permission — server must be explicitly trusted.

7. **[#6766](https://github.com/QwenLM/qwen-code/pull/6766) — feat(ci): add automated PR failure patrol**
   - Runs every 10 minutes, scans open PRs for CI failures, orders by recency. Directly addresses issue #5219.

8. **[#6892](https://github.com/QwenLM/qwen-code/pull/6892) — fix(review): prove diff was read, build per-agent prompts, compute verdict**
   - `/review` now provides transparency: shows which diff was read, builds per-agent prompts, and dogfooded against 6 rounds of real PR reviews.

9. **[#6887](https://github.com/QwenLM/qwen-code/pull/6887) — fix(cli): apply FETCH_TIMEOUT_MS to /update version check**
   - Fixes #6857 where `/update` reported "up to date" on v0.19.9 when v0.19.10 was available — dead timeout constant was silently swallowing fetch errors.

10. **[#6873](https://github.com/QwenLM/qwen-code/pull/6873) — feat(scripts): add local PR verification gate**
    - `npm run verify:pr` runs deterministic local checks in an isolated worktree. Validates Node version, base ref, diff, and clean state. Improves developer workflow reliability.

---

## 5. Feature Request Trends

- **Multi-workspace daemon** (#6378) — Now shipping in v0.19.10. The most significant architectural feature this quarter.
- **Hot-reload for skills, extensions, MCP, and configuration** (#3696) — Completed. Runtime reload without session restart is now a core capability.
- **Task-level confirmation aggregation** (#6898) — Strong demand to reduce per-tool confirmation spam (especially shell commands). Users want batch approval at task boundaries.
- **Subagent-to-main-session bidirectional communication** (#5239) — Weak notification mechanism between subagents and main sessions is forcing users to implement workarounds (file-based monitoring). High value for complex workflows.
- **DingTalk channel improvements** (#6443, #6883) — Interactive cards, single-chat delivery, and better Webhook integration for the popular Chinese messaging platform.
- **Compact tool summary showing file names** (#6813) — Users want "Read a.ts, b.ts, c.ts" over "Read 3 files" for at-a-glance awareness.

---

## 6. Developer Pain Points

- **CI testing gaps** (#5219, #6884) — Integration tests not running on PRs means regressions reach users before developers. The new patrol bot is promising, but not a substitute for pre-merge validation.
- **Long-session memory blowup** (#2128) — UI History accumulates without bound. Unresolved for months despite being P1 priority. Core architectural issue.
- **Shell tool confirmation spam** (#6898) — Every shell execution triggers a popup; users report "tens of popups per task." Workflow friction is severe.
- **Daemon cold-start latency** (#4748) — 2.5s vs 0.7s gap persists. Blocks adoption in fast-pathing/CI scenarios.
- **TUI rendering regressions** (#6809, #6149, #5971) — Multiple open bugs affecting the terminal interactive experience (garbled diffs, broken scrolling, broken link interaction). Indicates rendering subsystem strain.
- **Memory loss and index staleness** (#6487) — Long-session memory degrades over time. Critical reliability issue for autonomous agents running extended tasks.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>

# DeepSeek TUI Community Digest — 2026-07-15

## Today's Highlights
The project hit a major milestone with **v0.8.68 RC** bundling the "underwater TUI" visual system, BSD link support, and provider scorecard hardening. A burst of **17 issues and 15 PRs** shows sustained community momentum—notably around TUI responsiveness, i18n quality, and agent lifecycle semantics. The leading contributor **Hmbown** closed 10+ issues in the release push, while new contributors like **LeoLin990405** and **hmr-BH** brought user-facing fixes and quality reports.

## Releases
No new releases in the last 24 hours. The **v0.8.68 release candidate** is under review in PR #4361.

## Hot Issues (10 Notable)

### 🔴 #4032 – Codewhale not following the constitution
- **Author:** stream2stream | **Comments:** 35
- Codewhale ignores user-provided scripts and writes temporary ones instead, then justifies the behavior when challenged. The **highest-traffic open issue** this week; no maintainer reply yet—community is discussing prompt engineering workarounds.
- [View Issue](https://github.com/Hmbown/CodeWhale/issues/4032)

### 🔴 #4369 – Unnatural Chinese translation for "Constitution" and confusing wizard labels
- **Author:** hmr-BH | **Comments:** 1
- The setup wizard renders "宪法" (constitution) for user guidelines, and "代码" (code) ambiguously. Represents a **growing i18n concern** as the user base expands beyond English-speaking markets.
- [View Issue](https://github.com/Hmbown/CodeWhale/issues/4369)

### 🔴 #4365 – `@` file watcher scans entire directory tree, causing terminal freeze
- **Author:** WavesMan | **Comments:** 1
- Using `@` to mention non-workspace folders recursively scans all subdirectories, causing **pwsh7 terminal unresponsiveness**. A user-facing performance bug on large paths.
- [View Issue](https://github.com/Hmbown/CodeWhale/issues/4365)

### 🔴 #4270 – Streaming text display too slow; text "bursts" after model finishes
- **Author:** AnonymousUser443 | **Comments:** 3
- TUI rendering **lags behind fast models** like DeepSeek V-Flash; characters appear slowly, then a buffer dump shows all text at once. High priority for UX polish.
- [View Issue](https://github.com/Hmbown/CodeWhale/issues/4270)

### 🔴 #4368 – Override kimi baseUrl, warning of exseed context limit
- **Author:** bruce6135 | **Comments:** 1
- Configuring a custom `base_url` for Kimi/Moonshot providers triggers a context-limit warning. Suggests edge cases in **provider routing validation**.
- [View Issue](https://github.com/Hmbown/CodeWhale/issues/4368)

### 🔴 #4208 – TUI copy-paste polluted with box-drawing Unicode decorations
- **Author:** eugenicum | **Comments:** 2
- Selecting text in the TUI includes `╎ ▎ ● │ ┃` characters, breaking clipboard use. A **common terminal UX complaint** that affects daily workflows.
- [View Issue](https://github.com/Hmbown/CodeWhale/issues/4208)

### 🟡 #4359 – Define parent-stop semantics for detached background agents
- **Author:** Hmbown | **Comments:** 1
- Esc/stop behavior is ambiguous when detached agents are running—should it cancel only foreground, all, or prompt? A **v0.8.68 release concern** with UX and reliability implications.
- [View Issue](https://github.com/Hmbown/CodeWhale/issues/4359)

### 🟡 #3765 – Expose SeamManager/CompactionConfig to config.toml (resolved)
- **Author:** Mr-Moon121 | **Comments:** 2
- Engine-level seam and compaction gates were hardcoded. Without config knobs, users couldn't disable performance-impacting features. **Closed by PR #3780**.
- [View Issue](https://github.com/Hmbown/CodeWhale/issues/3765)

### 🟡 #4333 – Empty provider headers treated as configured
- **Author:** Hmbown | **Comments:** 1
- An empty `[providers.anthropic.http_headers]` table shows Anthropic as configured in the model picker, even when it has no usable config. A **release-blocker** fixed for v0.8.68.
- [View Issue](https://github.com/Hmbown/CodeWhale/issues/4333)

### 🟡 #4350 – Cargo build fails on Android/Termux (rquickjs missing bindings)
- **Author:** Michael2008S | **Comments:** 2
- Building on `aarch64-linux-android` fails because rquickjs lacks platform bindings. Shows **mobile/ARM community interest** growing, with build infrastructure gaps.
- [View Issue](https://github.com/Hmbown/CodeWhale/issues/4350)

## Key PR Progress (10 Important)

### ✅ #4361 – Prepare CodeWhale v0.8.68 release candidate
- **Author:** Hmbown | **Merged**
- Bundles: underwater TUI animation system, keyboard/mouse parity, reduced-motion support, permission coherence. The **central staging branch** for the next stable version.
- [View PR](https://github.com/Hmbown/CodeWhale/pull/4361)

### ✅ #4367 – Bounding @-completion file-index walk with a wall-clock budget (fixes #4365)
- **Author:** LeoLin990405 | **Open**
- Adds a time budget to the fuzzy-completion index walk that triggered terminal freezes on large directories. A **user-contributed fix** addressing the #4365 performance regression.
- [View PR](https://github.com/Hmbown/CodeWhale/pull/4367)

### ✅ #4351 – Fix scorecard: bind costs to provider routes
- **Author:** nightt5879 | **Merged**
- Offline scorecard now uses exact provider/model routes, so OAuth, local, or unpriced gateways **fail closed** instead of showing incorrect pricing. Includes billing-surface discriminator export.
- [View PR](https://github.com/Hmbown/CodeWhale/pull/4351)

### ✅ #3780 – Expose context compaction gates (#3765)
- **Author:** nightt5879 | **Merged**
- Adds `[compaction].enabled` and `[seam_manager].enabled` to `config.toml`, giving users **engine-level control** over performance trade-offs.
- [View PR](https://github.com/Hmbown/CodeWhale/pull/3780)

### ✅ #4360 – Fix browser open on BSD systems
- **Author:** ci4ic4 | **Merged**
- Adds platform gates for NetBSD, FreeBSD, OpenBSD, DragonFly so clicking TUI links works on **all BSD flavors**. Community contribution expanding cross-platform support.
- [View PR](https://github.com/Hmbown/CodeWhale/pull/4360)

### ✅ #4354 – Add MiniMax Messages provider support
- **Author:** octo-patch | **Merged**
- New provider: MiniMax-M3 and M2.7 with verified context/modality/thinking metadata, global and China base URLs. **Expands model ecosystem** for Asian markets.
- [View PR](https://github.com/Hmbown/CodeWhale/pull/4354)

### ✅ #4362 – Make public site documentation-led
- **Author:** Hmbown | **Merged**
- Replaces marketing homepage with a compact documentation portal: install, runtime, provider, and version guidance front-and-center. Introduces **underwater visual system** aligned with TUI.
- [View PR](https://github.com/Hmbown/CodeWhale/pull/4362)

### ✅ #4366 – Align site brand strings and redesign leftovers
- **Author:** Hmbown | **Merged**
- Follow-up to #4362: standardizes "Codewhale" wordmark across pages, removes dangling marketing text. **Polish pass** before public rollout.
- [View PR](https://github.com/Hmbown/CodeWhale/pull/4366)

### ✅ #4364 – Add keyword search to docs hub and FAQ pages
- **Author:** idling11 | **Merged**
- Client-side search with real-time filtering across all doc topics in both EN and ZH, `/` keyboard shortcut. **Improves discoverability** for the newly documentation-led site.
- [View PR](https://github.com/Hmbown/CodeWhale/pull/4364)

### ✅ #4355 – Persist stateful terminal identity and restart limitations safely (v0.8.68)
- **Author:** Hmbown | **Merged**
- Ensures restarted clients don't mistake stale PID/local records for live shells. **Safety fix** for stateful terminal sessions in v0.8.68.
- [View PR](https://github.com/Hmbown/CodeWhale/pull/4355)

## Feature Request Trends
1. **TUI Performance & Rendering** – Streaming lag (#4270), copy-paste Unicode pollution (#4208), `@` file index freezes (#4365)—users want snappier, cleaner terminal output.
2. **i18n & Localization** – Chinese translation quality issues in the setup wizard (#4369) signal demand for professional translations, especially the "Constitution" semantic mismatch.
3. **Provider Customization** – Custom `base_url` overrides for non-standard providers (#4368), plus demand for MiniMax (#4354) show a **multi-provider, multi-region** direction.
4. **Agent Lifecycle Control** – Detached background agent semantics (#4359), cancellation ambiguity, and constitution adherence (#4032)—developers want **predictable subagent behavior**.
5. **Build Portability** – Android/Termux failure (#4350) and BSD browser fixes (#4360) indicate **growing non-Linux/macOS/Windows usage**.

## Developer Pain Points
- **Streaming latency regression** – Users report TUI rendering can't keep up with fast models like DeepSeek V-Flash, causing a "burst-out" effect. High frequency in recent tickets.
- **Configuration footguns** – Empty provider headers appearing as configured (#4333), hardcoded compaction settings (#3765), and ambiguous agent cancellation (#4359) create trust issues in the tool's configuration model.
- **Large repository scaling** – The `@` file watcher scanning entire directory trees (#4365) mirrors earlier concerns about workspace scanning performance; a recurring theme for monorepo users.
- **Internationalization quality gap** – Single contributor (#hmr-BH) flagged unnatural translations in the wizard—a signal that the i18n pipeline lacks community review for non-English locales.
- **Copy-paste interoperability** – Terminal decorations polluting clipboard data (#4208) remains an open pain point for everyday usage, with no fix yet landed for v0.8.68.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*