# AI CLI Tools Community Digest 2026-07-16

> Generated: 2026-07-16 01:46 UTC | Tools covered: 9

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

# Cross-Tool Comparison Report: AI CLI Developer Tools Ecosystem
**Date:** 2026-07-16

---

## 1. Ecosystem Overview

The AI CLI developer tools landscape on July 16, 2026 reflects a maturing but volatile ecosystem where reliability concerns vie with rapid feature iteration. Claude Code leads in community size and feature depth but suffers from a **critical sub-agent recursion crisis**, with users reporting $27–$600 token burns from uncontrolled agent spawning. OpenAI Codex is shipping aggressively on its Rust CLI track (three alpha releases today) while battling a **Windows desktop stability crisis** driven by a broken `serialport.node` native dependency. Gemini CLI is making targeted fixes (MCP timeouts, shell expansion security) but continues to see high-severity sub-agent hang bugs. Smaller tools like OpenCode and Pi show healthy community engagement around UI regressions and platform-specific fixes, while Kimi Code and DeepSeek TUI remain quieter but structurally active. Across all tools, **agent reliability, budget controls, and cross-platform parity** dominate developer pain points.

---

## 2. Activity Comparison

| Tool | Issues (Open/Updated Today) | PRs (Merged/Open Today) | Release Status | Community Engagement Temperature |
|---|---|---|---|---|
| **Claude Code** | ~10 hot issues (3 recursion-critical) | 3 PRs (low throughput) | v2.1.211 released | 🔥🔥🔥🔥🔥 — Crisis mode (recursion bugs) |
| **OpenAI Codex** | ~10 hot issues (Windows crash cluster) | 10+ PRs (mostly bot-merged) | 3 alpha releases (v0.145.0-a.13–15) | 🔥🔥🔥🔥 — Rapid shipping, stability woes |
| **Gemini CLI** | ~10 hot issues (sub-agent hangs) | 10 PRs (2 merged, 8 open) | v0.52.0-nightly | 🔥🔥🔥 — Active but quieter |
| **Copilot CLI** | ~10 hot issues (MCP OAuth crisis) | 0 PRs today | v1.0.71-3 patch | 🔥🔥🔥 — MCP trust erosion |
| **OpenCode** | ~10 hot issues (UI redesign backlash) | 10 PRs (7 merged) | v1.18.2 | 🔥🔥🔥🔥 — High churn, responsive fixes |
| **Kimi Code** | 0 new today (10 tracked) | 1 PR opened (#2500) | No new release | 🔥 — Low engagement, steady development |
| **Pi** | ~10 hot issues (Codex reliability) | 10 PRs (4 merged) | No new release | 🔥🔥🔥 — Growing plugin ecosystem |
| **Qwen Code** | ~10 hot issues (multi-workspace) | 10 PRs (3 merged) | cua-driver v0.7.2 + nightly | 🔥🔥🔥 — Architectural improvements |
| **DeepSeek TUI** | ~10 issues (refactoring campaign) | 10 PRs (8 merged) | No new release (v0.8.68 stabilizing) | 🔥🔥 — Maintainer-driven refactor |

**Key observations:**
- **Claude Code** has the highest engagement but also the most severe unresolved bugs (recursion, data loss)
- **OpenAI Codex** merges the most PRs per day but predominantly bot-authored (copyberry)
- **OpenCode** shows the best bugfix turnaround — 7 PRs merged today addressing the UI crisis
- **Copilot CLI** and **Kimi Code** had zero PR activity, suggesting slower development cycles

---

## 3. Shared Feature Directions

### Requirements appearing across multiple tool communities:

| Shared Need | Tools Affected | Specific Requests |
|---|---|---|
| **Agent budget & kill-switch controls** | Claude Code, Gemini CLI, OpenCode | Configurable max-spawn-depth, token budgets, cost caps, kill-switch UX for runaway agents |
| **Sub-agent observability & status accuracy** | Claude Code, Gemini CLI, Qwen Code, Copilot CLI | Subagents reporting "success" on failure (#22323 Gemini), phantom background agents (#74317 Claude), missing thread selectors (#30813 Codex) |
| **MCP ecosystem reliability** | Copilot CLI (#4096), Claude Code (#60385) | OAuth tokens not bridging to sessions, permission prompts invisible in web UI, MCP tools/list timeouts |
| **Context window management** | Copilot CLI (#4097), OpenCode (#17340), Pi (#6647) | Compact/compaction failure transparency, retain scrolling, overflow detection timing, binary diffs exceeding limits |
| **Windows platform parity** | Claude Code (#75275, #53940), OpenAI Codex (#33381, #33375), Pi (#6596, #6619), DeepSeek TUI (#1812) | NTFS junction destruction, `serialport.node` crashes, `taskkill` ENOENT, TUI freezes, path encoding issues |
| **Session identity & conflict prevention** | Claude Code (#75761, #77463), Gemini CLI | Concurrent twin sessions, orphaned processes, lock files, session instance awareness |
| **Multi-workspace daemon support** | Qwen Code (#6378), Gemini CLI | Single daemon managing multiple workspaces for server consolidation |
| **VS Code / IDE extension parity** | Claude Code (#33932, #72292), Copilot CLI | Missing diff review UIs, `/workflows` commands, agent-view features vs. CLI superiority |
| **Config validation & discoverability** | Kimi Code (#2492, #2309), Gemini CLI, DeepSeek TUI (#3303) | Silent config misbehavior, no merge semantics, inability to edit from TUI |
| **Inline image rendering in chat** | OpenCode (#21227), Kimi Code (#2221) | Tool-returned images (webfetch, MCP ImageContent) shown as raw base64 instead of rendered |

---

## 4. Differentiation Analysis

| Tool | Core Differentiator | Target User | Technical Approach |
|---|---|---|---|
| **Claude Code** | Deepest agent orchestration (workflows, skills, sub-agents) | Professional developers, CI/CD pipelines | Node.js, MCP protocol, Cowork collaboration, VS Code extension |
| **OpenAI Codex** | Tightest OpenAI model integration + extensive import/export | OpenAI API power users, multi-model routing | Rust CLI track, TypeScript SDK, Cursor import, OpenAI sandboxing |
| **Gemini CLI** | Native bash affinity, zero-dependency sandboxing philosophy | Google Cloud ecosystem, POSIX power users | Gemini 3 model integration, A2A server, behavioral evals |
| **Copilot CLI** | GitHub-native authentication, enterprise GitHub Integration | GitHub Enterprise orgs, Copilot subscribers | OAuth with GitHub, voice mode, MCP but with fragile token bridging |
| **OpenCode** | Desktop-first (Electron) with TUI fallback, ACP protocol | Desktop users wanting IDE-like experience | React desktop app + TUI, V2 plugin architecture, Effect.ts |
| **Kimi Code** | Lightweight Python CLI, multi-provider (OpenAI compatibility) | Python developers, minimal tooling footprint | Python/TypeScript hybrid, argparse → click migration, lazy-loading |
| **Pi** | Extensible plugin system via npm packages, broadest provider support | Extension/plugin developers, tinkerers | Node.js with npm extension ecosystem, SQLite storage (WIP) |
| **Qwen Code** | Computer-use agent (CUA) driver, daemon architecture | Enterprise deployment, headless automation | Rust CUA driver, daemon with SSE endpoints, multi-channel (DingTalk) |
| **DeepSeek TUI** | Rust-based TUI with security-first ethos | Terminal purists, security-conscious developers | Rust monolith (refactoring), crossterm TUI, CodeQL-driven security |

**Strategic observations:**
- **Claude Code** and **OpenAI Codex** are the feature leaders but suffer most from complexity-induced bugs
- **OpenCode** is the only tool prioritizing desktop UX with a dedicated Electron app
- **Qwen Code** uniquely targets computer-use agents, not just code generation
- **DeepSeek TUI** is the only tool undergoing a systematic monolith refactoring — signals awareness of technical debt
- **Kimi Code** and **Pi** are the most lightweight, targeting minimal friction over feature depth

---

## 5. Community Momentum & Maturity

### High Momentum / Rapidly Iterating:
- **OpenAI Codex**: Most active PR pipeline (20+ per day, albeit bot-heavy). Shipping 3 alpha releases/day on Rust CLI track. Highest PR throughput.
- **OpenCode**: Best responsiveness to community feedback — 7 merged PRs today addressing the v1.18.x UI backlash. Strong bugfix velocity.
- **Claude Code**: Highest community engagement volume but also the most severe unresolved bugs. The recursion crisis is eroding trust despite deep feature set.
- **Qwen Code**: Strong architectural evolution — multi-workspace daemon, CUA driver, SSE endpoints signal enterprise readiness.

### Stable / Consolidating:
- **Gemini CLI**: Consistent but slower iteration. Behavioral eval infrastructure (#24353) and AST-aware tools (#22745) show systematic quality investment.
- **Pi**: Growing extension ecosystem (npm providers) but Codex reliability issues (#4945) are a significant drag on community satisfaction.
- **DeepSeek TUI**: Active refactoring campaign suggests maturation phase — cleaning up technical debt before v0.9.

### Lower Engagement:
- **Kimi Code**: Only 1 PR today, 0 new issues. Low community noise may indicate smaller user base or concentrated development.
- **Copilot CLI**: 0 PRs today. MCP OAuth crisis is the dominant narrative but development velocity appears low.

### Maturity Assessment:

| Tool | Maturity Level | Key Signal |
|---|---|---|
| **Claude Code** | Mature but crisis-prone | Deepest feature set, highest bug severity |
| **OpenAI Codex** | Rapid growth | 3 alpha releases/day, 20+ PRs |
| **Gemini CLI** | Consolidating | Behavioral evals, systematic quality |
| **Copilot CLI** | Stagnating | 0 PRs, unresolved MCP crisis |
| **OpenCode** | Maturing fast | Responsive fixes, v1.18 stable |
| **Kimi Code** | Early stage | Low volume, building foundations |
| **Pi** | Growing | Extensible architecture, increasing engagement |
| **Qwen Code** | Enterprise-ready | Daemon infrastructure, CUA driver |
| **DeepSeek TUI** | Refactoring | Monolith splitting before v0.9 |

---

## 6. Trend Signals

### Industry Trends from Community Feedback:

1. **Agent cost control is the #1 unmet need** — Across Claude Code (recursion burns), OpenAI Codex (prompt caching gaps), and Gemini CLI (recursive turn limits), the community is demanding **explicit budget guardrails** before deploying AI agents at scale. Token consumption visibility, kill-switch UX, and configurable depth/budget limits are becoming table stakes.

2. **MCP protocol needs hardening** — Copilot CLI's OAuth token bridging failures (#4096) and Claude Code's invisible permission prompts (#60385) signal that the MCP ecosystem promises more than it delivers in practice. Cross-tool portability of MCP servers (Qwen Code #6970 on dot-separated tool names) remains fragile.

3. **Windows is the neglected platform** — Claude Code's NTFS junction destruction (#75275), Codex's `serialport.node` crash (#33381), Pi's `taskkill` ENOENT (#6596), and DeepSeek's TUI freeze (#1812) all point to systematic under-investment in Windows QA. Developers on Windows face data-loss vectors not present on macOS/Linux.

4. **Plugin/extension ecosystems are the next battleground** — OpenCode's V2 plugin architecture, Pi's npm extension system, and Claude Code's skills/plugins all indicate that tool differentiation will shift from core features to extensibility. Qwen Code's DingTalk and web-shell channels point toward multi-platform deployment.

5. **Session management is foundational but broken** — Session identity conflict, compaction failure, and context overflow are universal pain points. Tools that solve session reliability (OpenCode's compaction fix #37194, Pi's SQLite storage #6594) gain structural advantage.

6. **Desktop vs. CLI tension persists** — Claude Code's VS Code extension parity demand and OpenCode's desktop UI redesign backlash show that IDE integration remains unsolved. Users want CLI power with IDE convenience — no tool has fully delivered both.

### Recommendations for Developers:

**If you prioritize reliability over features**, watch **OpenCode** (best bugfix turnaround) or **Gemini CLI** (systematic eval investment).

**If you need maximum agent autonomy**, **Claude Code** has the deepest orchestration but requires **token budget controls** that don't exist yet.

**If you're on Windows**, proceed with caution — especially with **Claude Code** (data loss) and **Codex Desktop** (crash loops).

**If you're building enterprise pipelines**, **Qwen Code**'s daemon architecture and CUA driver offer the most production-ready headless deployment model.

**If you want to extend/customize**, **Pi**'s npm plugin system and **OpenCode**'s V2 Effect architecture offer the most flexible extension points.

---

## Per-Tool Reports

<details>
<summary><strong>Claude Code</strong> — <a href="https://github.com/anthropics/claude-code">anthropics/claude-code</a></summary>

## Claude Code Skills Highlights

> Source: [anthropics/skills](https://github.com/anthropics/skills)

# Claude Code Skills Community Highlights Report
**Data Source**: github.com/anthropics/skills | **Snapshot**: 2026-07-16

---

## 1. Top Skills Ranking
*Most-discussed Pull Requests by comment volume and community engagement*

### #1298 — Fix: `run_eval.py` Always Reports 0% Recall *(Open)*
- **Functionality**: Repairs the skill-creator's evaluation pipeline—fixes the `run_eval.py` script that consistently reports `recall=0%` due to missing eval artifact installation, Windows stream-reading bugs, and broken trigger detection.
- **Discussion Highlights**: Addresses a systemic blocker (Issue #556) with 10+ independent reproductions. The fix ensures the description-optimization loop (`run_loop.py`) evaluates against real signals rather than noise.
- **Status**: Open (updated June 23, 2026)
- **Link**: [PR #1298](https://github.com/anthropics/skills/pull/1298)

### #514 — Add `document-typography` Skill *(Open)*
- **Functionality**: Prevents common typographic defects in AI-generated documents: orphan word wrap, widow paragraphs, and numbering misalignment. Targets the visual quality gap in Claude's document output.
- **Discussion Highlights**: Users note these issues affect "every document Claude generates." The skill fills a gap between content generation and production-ready formatting.
- **Status**: Open (updated March 13, 2026)
- **Link**: [PR #514](https://github.com/anthropics/skills/pull/514)

### #723 — Add `testing-patterns` Skill *(Open)*
- **Functionality**: Comprehensive testing coverage: Testing Trophy model, AAA pattern, React component testing with Testing Library, integration tests, E2E with Playwright, and mocking strategies.
- **Discussion Highlights**: Community interest in structured testing guidance—moves beyond "write tests" to teaching Claude *which* tests to write and *when*.
- **Status**: Open (updated April 21, 2026)
- **Link**: [PR #723](https://github.com/anthropics/skills/pull/723)

### #525 — Add `pyxel` Skill for Retro Game Development *(Open)*
- **Functionality**: Integrates with Pyxel-MCP for creating retro/pixel-art/8-bit games in Python. Covers workflow: write → run_and_capture → inspect → iterate.
- **Discussion Highlights**: Niche but enthusiastic reception—the only game-development skill in the ecosystem. Author is the Pyxel creator themselves.
- **Status**: Open (updated July 15, 2026)
- **Link**: [PR #525](https://github.com/anthropics/skills/pull/525)

### #1367 — Add `self-audit`: Reasoning Quality Gate *(Open)*
- **Functionality**: Two-stage output auditing: mechanical file verification (every claimed file exists) followed by four-dimension reasoning audit in damage-severity priority order. Model-agnostic and project-agnostic.
- **Discussion Highlights**: Represents shift toward *post-generation quality assurance*—community recognizes Claude needs to verify its own work before delivery.
- **Status**: Open (updated July 2, 2026)
- **Link**: [PR #1367](https://github.com/anthropics/skills/pull/1367)

### #83 — Add `skill-quality-analyzer` and `skill-security-analyzer` *(Open)*
- **Functionality**: Meta-skills evaluating other skills across five dimensions (Structure, Documentation, Pattern Usage, Edge Cases, Security). Security analyzer checks prompt injection, sandbox escapes, secret exposure.
- **Discussion Highlights**: First meta-skills for the ecosystem—community self-regulation through peer review tooling.
- **Status**: Open (updated January 7, 2026)
- **Link**: [PR #83](https://github.com/anthropics/skills/pull/83)

### #486 — Add ODT Skill *(Open)*
- **Functionality**: OpenDocument text creation, template filling, ODT-to-HTML conversion. Handles `.odt`, `.ods`, `.odf` formats for LibreOffice/ISO-standard documents.
- **Discussion Highlights**: Fills enterprise document-format gap—users in government and EU public sector mandate ODF.
- **Status**: Open (updated April 14, 2026)
- **Link**: [PR #486](https://github.com/anthropics/skills/pull/486)

### #210 — Improve `frontend-design` Skill *(Open)*
- **Functionality**: Revises existing skill for clarity and actionability—ensures every instruction is executable within a single conversation, with specific enough guidance to steer Claude behavior without over-constraining.
- **Discussion Highlights**: Community-driven refinement of an existing skill; signals demand for iterative skill quality improvement.
- **Status**: Open (updated March 7, 2026)
- **Link**: [PR #210](https://github.com/anthropics/skills/pull/210)

---

## 2. Community Demand Trends
*Most-anticipated directions distilled from Issues with highest engagement*

1. **Security & Trust Boundaries** (#492, 34 comments) — The single most-discussed issue. Community is alarmed that skills under the `anthropic/` namespace are community-submitted, creating a trust-abuse vector where users may grant elevated permissions to skills they believe are official. Demands clear provenance marking, sandboxing, and permission scoping.

2. **Skill-Sharing Infrastructure** (#228, 14 comments) — Organizations want org-wide skill libraries with sharing links instead of manual `.skill` file transfer via Slack. The manual upload workflow (Settings > Capabilities > Upload) is a adoption bottleneck.

3. **Windows & Cross-Platform Compatibility** (#556, #1061, #1169 — 12-18 comments combined) — The skill-creator evaluation pipeline is effectively broken on Windows. Three distinct issues: `PATHEXT` not honored for `claude.cmd`, `cp1252` encoding panics, and `select()` on pipes failing. This blocks an entire OS user base from contributing.

4. **Quality Assurance Meta-Skills** (#412, #1385, 6-9 comments) — Growing interest in "governance patterns" and "reasoning quality gates" applied to AI agent output. Community wants Claude to self-audit before delivery.

5. **Duplicate Skill Management** (#189, 6 comments) — `document-skills` and `example-skills` plugins install identical content. Community needs deduplication and package clarity.

6. **MCP Integration** (#16, 4 comments) — Users want skills exposed as MCP tools for programmatic consumption. Skills as API endpoints.

---

## 3. High-Potential Pending Skills
*Active-comment PRs likely to land soon, based on momentum and community interest*

| PR | Skill | Last Updated | Comments | Gating Factor |
|---|---|---|---|---|
| [#1298](https://github.com/anthropics/skills/pull/1298) | `run_eval.py` 0% recall fix | Jun 23 | High | Critical ecosystem fix—addresses Issue #556 |
| [#1367](https://github.com/anthropics/skills/pull/1367) | `self-audit` quality gate | Jul 2 | Moderate | Recently submitted, active iteration |
| [#1099](https://github.com/anthropics/skills/pull/1099) | Windows subprocess crash fix | May 24 | Moderate | Part of multi-PR Windows compatibility campaign |
| [#723](https://github.com/anthropics/skills/pull/723) | `testing-patterns` | Apr 21 | Moderate | Broad appeal; structured testing is high-demand |
| [#1302](https://github.com/anthropics/skills/pull/1302) | `color-expert` | Jun 12 | Low-medium | Niche but authoritative (ISCC-NBS, Munsell, OKLCH) |
| [#525](https://github.com/anthropics/skills/pull/525) | `pyxel` game dev | Jul 15 | Low-medium | Author is Pyxel maintainer—strong domain credibility |

---

## 4. Skills Ecosystem Insight

**The community's most concentrated demand at the Skills level is *trust and reliability infrastructure*:** users need skills to verify output quality (self-audit, testing-patterns), trust the provenance of skills themselves (security-analyzer, namespace transparency), and depend on core tooling working cross-platform (Windows compatibility fixes for the skill-creator pipeline).

---

# Claude Code Community Digest — 2026-07-16

## Today's Highlights

The community is experiencing a **critical wave of sub-agent recursion bugs**, with multiple reports (Issues #68619, #69578, #72732) documenting uncontrolled agent spawning consuming 600K–800K+ tokens and costing users up to $600 in a single session. Meanwhile, the **`--forward-subagent-text` flag** in today's v2.1.211 release offers a new debugging capability, and the **VS Code extension divide** continues to grow as users demand `/workflows` support and diff review UIs that the CLI already has.

---

## Releases

**v2.1.211** — [Release Link](https://github.com/anthropics/claude-code/releases/tag/v2.1.211)
- Added `--forward-subagent-text` flag and `CLAUDE_CODE_FORWARD_SUBAGENT_TEXT` env var to include subagent text/thinking in `stream-json` output
- Fixed permission previews not neutralizing bidirectional-override, zero-width, and look-alike characters relayed to chat channels

---

## Hot Issues

1. **[#53940 — Cowork Edit/Write silently truncates files](https://github.com/anthropics/claude-code/issues/53940)** (🔥 43 comments, 16 👍)  
   *Bug, platform: Windows.* A deterministic bug fires at all file sizes: the byte-conservation buffer cap silently truncates files during Cowork Edit/Write operations. Community is frustrated by data loss that goes undetected until review. No fix committed yet after 3 months open.

2. **[#68619 — Subagent infinite recursion & $27+ token burn](https://github.com/anthropics/claude-code/issues/68619)** (🔥 31 comments, 10 👍, CRITICAL)  
   Subagents spawn 50+ levels deep, ignoring `CLAUDE_CODE_FORK_SUBAGENT=0`. Permission denials trigger *more* spawning instead of stopping. Multiple regressions compound into catastrophic token waste. Marked duplicate, but no unified fix visible.

3. **[#69578 — 800K token consumption / $27.60 unexpected charge](https://github.com/anthropics/claude-code/issues/69578)** (8 comments)  
   A user hit a recursive sub-agent loop consuming ~800K tokens with "nearly zero useful output." Highlights a painful gap: no guardrails, no budget limits, no killswitch UX for runaway agents.

4. **[#33932 — VS Code diff review UI](https://github.com/anthropics/claude-code/issues/33932)** (34 comments, 150 👍)  
   The most-upvoted open feature request: GitHub Copilot-style diff review in VS Code. Users feel the CLI's `diff` workflow is superior and the extension needs parity. Wide consensus, zero progress visible.

5. **[#60385 — MCP permission prompts never surface in web UI](https://github.com/anthropics/claude-code/issues/60385)** (20 comments, CLOSED)  
   Remote Control permissions for non-read MCP tools silently block in claude.ai/code. Only visible in TUI. Closed without a fix — concerning for remote-control adoption.

6. **[#40043 — Cannot remove folders from Cowork project context](https://github.com/anthropics/claude-code/issues/40043)** (17 comments, 55 👍)  
   Once a folder is added to a Cowork project, there's no removal mechanism. Users manage this with `.gitignore` workarounds. High demand, not addressed.

7. **[#77785 — Claude Desktop Extensions panel permanently stuck](https://github.com/anthropics/claude-code/issues/77785)** (4 comments)  
   Installing any local `.mcpb` breaks the Extensions settings panel with `TypeError: u._parse is not a function`. Freshly reported, high visibility.

8. **[#74990 — /compact drops all Available skills reminders](https://github.com/anthropics/claude-code/issues/74990)** (3 comments)  
   Auto-compaction silently drops the Available skills system reminder. The model "forgets" installed skills until `/reload-skills` recovers it. Insidious trust issue.

9. **[#75275 — Stale-worktree cleanup deletes data outside worktree on Windows](https://github.com/anthropics/claude-code/issues/75275)** (2 comments, ~800 GB data loss)  
   `rm -rf` on Windows traverses NTFS junctions, deleting *target* contents. User reports ~800 GB data loss. Critical for anyone using junctions on Windows.

10. **[#74317 — Subagents fabricate phantom background agents](https://github.com/anthropics/claude-code/issues/74317)** (2 comments)  
    Subagents stall by claiming they're "waiting for a background agent" when none exists. Hallucination meets control flow — stalls are indistinguishable from legit waits.

---

## Key PR Progress

1. **[#77916 — Add code-quality-pipeline plugin](https://github.com/anthropics/claude-code/pull/77916)** (OPEN)  
   New skill plugin defining quality gates between "code written" and "code merged." Two gates: per-file sequential checks and end-to-end verification. Promising for CI integration.

2. **[#77709 — Settings example: official marketplace only](https://github.com/anthropics/claude-code/pull/77709)** (OPEN)  
   Adds `settings-official-marketplace-only.json` example. Demonstrates `strictKnownMarketplaces` with Anthropic's official marketplace. Useful for enterprise deployments.

3. **[#77705 — Fix validate-settings.sh false-pass on no-frontmatter files](https://github.com/anthropics/claude-code/pull/77705)** (OPEN)  
   Fixes a shell script bug where files lacking YAML frontmatter `---` markers falsely pass validation. Prevents malformed plugins from being published.

*Note: Only 3 PRs were updated in the last 24 hours. The repo appears to have a low PR throughput relative to issue volume.*

---

## Feature Request Trends

- **VS Code Extension Parity** — The most consistent theme: `/workflows` command support (#72292, #74585, #75146), diff review UI (#33932), and agent-view features missing in the IDE extension.
- **Cowork Context Management** — Users want to remove folders from projects (#40043, 55 👍) and control what's included without workarounds.
- **Configurable Auto-Compact** — Multiple requests (#70681) for adjustable compaction thresholds; current behavior drops skill reminders silently (#74990).
- **Session Instance Awareness** — Growing demand for session identity, lock files, and kill-capabilities to prevent concurrent twin sessions (#69364, #75761, #77463).
- **Agent Budget Controls** — Post-recursion-bug wave, users want configurable max-spawn-depth, token budgets, and cost kill-switches.

---

## Developer Pain Points

- **Catastrophic Token Waste** — The sub-agent recursion cluster (#68619, #69578, #72732, #77834) is the #1 pain point. Uncontrolled spawning with no depth limits, no budget caps, and no visibility until the bill arrives. Multiple users report $27–$600 charges.
- **Silent Data Loss** — Cowork buffer truncation (#53940), NTFS junction traversal (#75275), and Confluence page overwrites (#75685) all share a pattern: no warnings, no undo, data is gone. Trust in file-system operations is eroding.
- **Session Chaos** — `--continue` and `--resume` create orphaned twin processes that work on the same repo concurrently (#75761). No session registry, no identity — "kids in a trenchcoat" (#77463).
- **Windows-Specific Brokenness** — Stale-worktree cleanup destroys external data (#75275), PowerShell guards mis-extract tokens (#69461), spell-checking cannot be disabled (#58693). Windows users face unique data-loss vectors.
- **Extension vs. CLI Divide** — The VS Code extension is missing core slash commands and agent tools that the CLI has. Users feel the extension is treated as a second-class surface.
- **Phantom Agents & Hallucinated Stalls** — Subagents fabricate background agents that don't exist (#74317, #77950), causing indefinite stalls indistinguishable from real work. Debugging is nearly impossible.

</details>

<details>
<summary><strong>OpenAI Codex</strong> — <a href="https://github.com/openai/codex">openai/codex</a></summary>

# OpenAI Codex Community Digest — 2026-07-16

## Today's Highlights
The Codex team shipped three alpha releases on the Rust CLI track (v0.145.0-alpha.13–15) and merged 20+ pull requests, predominantly bot-authored, focused on safety hardening, agent migration, and sandbox fixes. Community attention remains laser-focused on the **Windows desktop crash crisis** — multiple high-engagement issues converge on a single root cause: an incompatible `serialport.node` dependency bundled in build `26.707.9981.0` that causes app crash-loops, severe lag, and silent exits across ARM64 and x64. Meanwhile, the long-standing request to disable the 60-second auto-resolve question timer (#28969) continues to gather strong community support with 124 👍.

---

## Releases
- **`rust-v0.145.0-alpha.15`**, **`.14`**, and **`.13`**: Three consecutive alpha releases on the Rust CLI track were published in rapid succession. Release notes provide only the version tag; no changelog descriptions are available. These follow the `0.144.x` stable branch and likely include the dangerous-command detection backport and other recent fixes.

---

## Hot Issues (Top 10)

1. **#23794 — [CLOSED] Codex Desktop no longer shows visible context/token usage indicator**  
   *Author: HushHuang | Comments: 172 | 👍: 170*  
   The most commented issue in repository history. After an update, the app removed the context/token usage indicator — a core UX element for users managing large prompts on Business subscriptions. Closed without a public fix explanation, which may disappoint many users awaiting restoration.  
   [GitHub](https://github.com/openai/codex/issues/23794)

2. **#33381 — [OPEN] Windows ARM64 app crash-loops on launch**  
   *Author: LukeWHolliday | Comments: 37 | 👍: 25*  
   Critical. The Windows ARM64 binary of Codex Desktop enters a 10–15 second crash-loop on every launch. Crashpad minidumps point to `serialport.node` failing with delay-load error `0xC06D007F`. No error dialog, no event log entries — making debugging especially painful. Reinstalling and wiping local cache does not resolve it.  
   [GitHub](https://github.com/openai/codex/issues/33381)

3. **#28969 — [OPEN] Add setting to disable the auto-resolve in 60 seconds for questions**  
   *Author: antoyo | Comments: 37 | 👍: 124*  
   The community's most-upvoted open feature request. Users on Linux (Arch) and Plus subscriptions want control over Codex CLI's automatic question resolution timer. The 60-second timeout is particularly disruptive during complex reasoning tasks where the model preemptively responds before the user finishes typing.  
   [GitHub](https://github.com/openai/codex/issues/28969)

4. **#31846 — [OPEN] GPT-5.3 Codex Spark fails with `Unsupported parameter: reasoning.summary`**  
   *Author: osipovgleb | Comments: 28 | 👍: 33*  
   Model compatibility regression. Pro subscribers on macOS hitting a parameter validation error when using GPT-5.3 Spark. The `reasoning.summary` parameter is being sent but is unsupported by that model revision, suggesting a stale or misconfigured model routing.  
   [GitHub](https://github.com/openai/codex/issues/31846)

5. **#33375 — [OPEN] Repeated `serialport.node` delay-load failures cause severe UI lag**  
   *Author: warriorjamez | Comments: 24 | 👍: 14*  
   Companion to #33381. On Windows x64, the same `serialport.node` dependency fails repeatedly during runtime, causing the app to become "severely laggy." Not a hard crash, but persistent degradation — users report seconds of UI freeze during serialport initialization retries.  
   [GitHub](https://github.com/openai/codex/issues/33375)

6. **#30178 — [OPEN] In-app Browser crashes the main app during webview navigation**  
   *Author: vir-tu | Comments: 19 | 👍: 1*  
   Windows 11 Pro users on API subscriptions report that navigating the embedded webview browser triggers full app crashes. The browser feature continues to destabilize the desktop app, and the bug has persisted for three weeks without resolution.  
   [GitHub](https://github.com/openai/codex/issues/30178)

7. **#23198 — [OPEN] Codex Desktop on Windows is extremely slow even when the computer is fine**  
   *Author: Yemvis | Comments: 16 | 👍: 44*  
   A long-standing performance issue (since May) with 44 upvotes. Users report the Windows app is sluggish in day-to-day development sessions while the machine itself shows no load. The issue remains open with no fix in sight, compounding frustrations with the new crash bugs.  
   [GitHub](https://github.com/openai/codex/issues/23198)

8. **#30813 — [OPEN] CLI: `/agent` lists active subagents but provides no thread selector**  
   *Author: htregidgo | Comments: 10 | 👍: 5*  
   Usability gap in the CLI TUI. The `/agent` command enumerates active subagents, but users cannot select or switch to a specific subagent thread. Multi-agent workflows are severely limited on the CLI as a result.  
   [GitHub](https://github.com/openai/codex/issues/30813)

9. **#32782 — [OPEN] GPT-5.6 Sol spawns agents without `agent_type`, blocking custom agent routing**  
   *Author: pax-k | Comments: 8 | 👍: 9*  
   Advanced multi-agent issue. When root tasks use GPT-5.6 Sol, the `spawn_agent` schema omits `agent_type`, preventing users from routing to custom-configured agents. Custom agent setups that work on other model roots break silently.  
   [GitHub](https://github.com/openai/codex/issues/32782)

10. **#33450 — [OPEN] Windows Codex app spawns 12–13 `git.exe` processes per second**  
    *Author: Burnrate | Comments: 2 | 👍: 1*  
    A newly filed but alarming performance bug. The Windows app enters a pathological loop spawning over a dozen `git.exe` processes per second and recreating invalid empty `.git` directories. Likely a filesystem-watch or repo-detection regression in build `26.707.9981.0`.  
    [GitHub](https://github.com/openai/codex/issues/33450)

---

## Key PR Progress (Top 10)

1. **#33455 — [CLOSED] fix(core): expand `is_dangerous_command`**  
   *Author: dylan-hurd-oai (backport)*  
   Cherry-picks seven commits onto `release/0.144` to enable dangerous-command detection in `danger-full-access` mode and expand literal Bash parsing for forced `rm` variants. Addresses safety gaps in the sandbox.  
   [GitHub](https://github.com/openai/codex/pull/33455)

2. **#33454 — [CLOSED] Track prompt cache write token usage**  
   *Author: copyberry[bot]*  
   Adds `cache_write_tokens` parsing and exposes `cache_write_input_tokens` across protocol, app-server, exec, and TypeScript SDK. Key for users who rely on prompt caching to manage API costs.  
   [GitHub](https://github.com/openai/codex/pull/33454)

3. **#33464 — [CLOSED] Strengthen forced `rm` command detection**  
   *Author: copyberry[bot]*  
   Enhances the dangerous-command heuristic to detect forced `rm` invocations inside control flow, substitutions, and wrapper variants. Complements the `is_dangerous_command` expansion.  
   [GitHub](https://github.com/openai/codex/pull/33464)

4. **#33426 — [CLOSED] Add Cursor support to setup import**  
   *Author: copyberry[bot]*  
   Expands the `/import` flow to detect and import settings, sandbox permissions, MCP servers, project instructions, hooks, agents, commands, plugins, and recent chat sessions from **Cursor** — a major competitor. Signals OpenAI's intent to lower migration barriers.  
   [GitHub](https://github.com/openai/codex/pull/33426)

5. **#33432 — [CLOSED] Preserve paginated history for spawned subagents**  
   *Author: copyberry[bot]*  
   Fixes a key multi-agent feature gap: subagents spawned or forked from a paginated parent now inherit paginated history mode. Ensures consistent context management across agent hierarchies.  
   [GitHub](https://github.com/openai/codex/pull/33432)

6. **#33444 — [CLOSED] Add external agent memory migration**  
   *Author: copyberry[bot]*  
   Feature-gated `MEMORY` migration item that discovers project memory Markdown files and copies selected projects into the Codex memory extension workspace. Supports migration from external agent tooling.  
   [GitHub](https://github.com/openai/codex/pull/33444)

7. **#33445 — [CLOSED] Select the elevated Windows sandbox for network proxies**  
   *Author: copyberry[bot]*  
   Fixes Windows firewall enforcement by routing proxy-enforced commands through the elevated sandbox backend, even when the default sandbox mode is restricted-token. Directly relevant to Windows crash/workflow issues.  
   [GitHub](https://github.com/openai/codex/pull/33445)

8. **#33424 — [CLOSED] Attribute OpenAI docs MCP requests to Codex**  
   *Author: copyberry[bot]*  
   Adds `source=codex` to requests sent to the OpenAI developer docs MCP endpoint. Enables analytics attribution without breaking other MCP server behavior.  
   [GitHub](https://github.com/openai/codex/pull/33424)

9. **#33423 — [CLOSED] Load executor plugin declarations concurrently**  
   *Author: copyberry[bot]*  
   Performance improvement for remote environments: reads MCP server and app connector declarations concurrently instead of sequentially, cutting latency for remote exec-server startups.  
   [GitHub](https://github.com/openai/codex/pull/33423)

10. **#31781 — [OPEN] Bound executor-controlled HTTP response buffering**  
    *Author: jif-oai*  
    Security hardening. Addresses a trust boundary issue where the remote exec-server could force the app-server to retain large amounts of response data. Bounds buffering by bytes rather than frame count. Under code review.  
    [GitHub](https://github.com/openai/codex/pull/31781)

---

## Feature Request Trends

- **Configurable auto-resolve timer**: The #1 community request (124 👍 on #28969). Users want to disable or extend the 60-second question auto-resolve timeout, especially during complex multi-step reasoning.
- **Full 1.05M context window for GPT-5.6 Sol**: Advanced users want opt-in access to the model's full context and manual control over compaction thresholds (#33306).
- **Multi-chat / multi-thread UI**: A persistent request (#13036) for the desktop app to display multiple simultaneous chat sessions, enabling multi-tasking and multi-agent workflows.
- **Customizable stream reconnect backoff**: Developers need configurable retry delay strategies for streaming connections, especially when using non-OpenAI provider setups (#16164).
- **Import from more IDEs**: After Cursor support (#33426), users likely expect import flows for additional competitor tools.

---

## Developer Pain Points

- **Windows stability crisis**: Build `26.707.9981.0` introduced a broken `serialport.node` native dependency that causes crash-loops on ARM64 (#33381), severe UI lag on x64 (#33375), and silent exits at startup (#33119, #33380). Four separate issues with 50+ combined comments.
- **Git filesystem storm on Windows**: The app entering a loop spawning 12+ `git.exe` processes per second (#33450) indicates a serious shell-watch or repo-detection regression.
- **Model routing inconsistencies**: GPT-5.3 Spark sends unsupported parameters (#31846), and GPT-5.6 Sol omits `agent_type` in spawn calls (#32782) — both break existing workflows without clear error messages.
- **SSH remote disconnects**: Multiple issues report SSH remote project sessions showing "No chats" after updates (#27284, #30808), and failing when servers require keyboard-interactive/PAM auth (#23037).
- **MCP tooling fragility**: The bundled `node_repl` MCP client fails to start on macOS (#32447), and `serialport.node` failures cascade through the Windows app (#33375), suggesting insufficient cross-platform testing of bundled native dependencies.

</details>

<details>
<summary><strong>Gemini CLI</strong> — <a href="https://github.com/google-gemini/gemini-cli">google-gemini/gemini-cli</a></summary>

# Gemini CLI Community Digest — 2026-07-16

## 1. Today's Highlights
A fix lands for the severe "400 Bad Request on tool rejection" bug that broke chat continuity, alongside a new MCP `tools/list` timeout to prevent 10-minute startup freezes from unresponsive servers. The community is also seeing progress on shell variable expansion security (GHSA-wpqr-6v78-jr5g) and a recursive reasoning turn limit to protect against infinite loops. The bug backlog remains heavy on agent subagent reliability, with several high-priority issues around hang detection and false success reporting.

## 2. Releases
**v0.52.0-nightly.20260716.g3ff5ba20f** — ([Release](https://github.com/google-gemini/gemini-cli/releases/tag/v0.52.0-nightly.20260716.g3ff5ba20f))
- Bug fix: group cancelled tool responses and coalesce consecutive roles to prevent `400 Bad Request` errors when rejecting/cancelling tool calls mid-chat.
- Automated nightly version bump.

## 3. Hot Issues (Top 10)

1. **[#22323](https://github.com/google-gemini/gemini-cli/issues/22323) — Subagent recovery after MAX_TURNS reported as GOAL success**  
   *Priority P1, 10 comments, 2 👍*  
   A `codebase_investigator` subagent reports `status: "success"` with `Termination Reason: "GOAL"` despite hitting the maximum turn limit before doing any analysis. This misclassification hides genuine interruptions and misleads users into thinking their task completed. A critical reliability gap for anyone relying on subagent status signals.

2. **[#19873](https://github.com/google-gemini/gemini-cli/issues/19873) — Leverage model's bash affinity via Zero-Dependency OS Sandboxing**  
   *Priority P2, 8 comments, 1 👍*  
   Proposes building on Gemini 3's native bash capabilities using POSIX tools (`grep`, `cat`, `sed`, `awk`) for codebase exploration. The key tension: enabling the model to use its strongest skill set safely without compromising user security. Ambitions, but still in design phase.

3. **[#24353](https://github.com/google-gemini/gemini-cli/issues/24353) — Robust component level evaluations (EPIC)**  
   *Priority P1, 7 comments*  
   Follow-up to the behavioral eval system introduced in #15300. With 76 behavioral eval tests now running across 6 Gemini models, this epic tracks scaling the testing infrastructure to catch regressions earlier. Critical for the team's confidence in agent changes.

4. **[#22745](https://github.com/google-gemini/gemini-cli/issues/22745) — Assess AST-aware file reads, search, and mapping (EPIC)**  
   *Priority P2, 7 comments, 1 👍*  
   Investigates whether Abstract Syntax Tree aware tools can reduce token waste from misaligned reads and improve codebase navigation precision. Has downstream implications for the `codebase_investigator`. Community is watching closely as AST integration could dramatically improve large-repo performance.

5. **[#21409](https://github.com/google-gemini/gemini-cli/issues/21409) — Generalist agent hangs forever**  
   *Priority P1, 7 comments, 8 👍*  
   The most-upvoted open bug. Generalist subagent hangs indefinitely on simple tasks like folder creation, forcing users to cancel after an hour. Workaround: explicitly disable subagent delegation. High frustration — this is a daily usability blocker.

6. **[#21968](https://github.com/google-gemini/gemini-cli/issues/21968) — Gemini does not use skills and sub-agents enough**  
   *Priority P2, 6 comments*  
   Users report the model rarely activates custom skills or sub-agents even when task-relevant. Anecdotal but widespread: "gradle" and "git" skills with clear descriptions are ignored. The model's meta-decision logic for subagent routing remains opaque and under-tuned.

7. **[#26522](https://github.com/google-gemini/gemini-cli/issues/26522) — Stop Auto Memory from retrying low-signal sessions indefinitely**  
   *Priority P2, 5 comments*  
   Auto Memory marks a session as processed only when the extraction agent successfully reads the transcript. Low-signal sessions that the agent skips remain "unprocessed" and keep surfacing, causing infinite retries. A resource-wasting feedback loop in the memory extraction pipeline.

8. **[#25166](https://github.com/google-gemini/gemini-cli/issues/25166) — Shell command execution gets stuck with "Waiting input" after completion**  
   *Priority P1, 4 comments, 3 👍*  
   After simple shell commands finish, the agent hangs showing them as active and "Awaiting user input." High-severity because it blocks any subsequent reasoning. Reproducible with trivial commands like `ls`. A classic terminal emulation edge case.

9. **[#20079](https://github.com/google-gemini/gemini-cli/issues/20079) — Symlinked agent files ignored**  
   *Priority P2, 4 comments*  
   `~/.gemini/agents/` does not recognize symlinked `.md` files as valid subagent definitions. Blocks users who manage agent definitions via dotfile managers or version control with symlinks. Simple fix with high user impact.

10. **[#22672](https://github.com/google-gemini/gemini-cli/issues/22672) — Agent should stop/discourage destructive behavior**  
    *Priority P2, 3 comments, 1 👍*  
    The model occasionally uses `git reset`, `--force` flags, or destructive DB commands when safer alternatives exist. Users want the agent to understand the consequences of destructive operations and prefer safer approaches by default. Reflects a deeper trust concern with autonomous execution.

## 4. Key PR Progress (Top 10)

1. **[#28407](https://github.com/google-gemini/gemini-cli/pull/28407) — fix(core,a2a): group cancelled tool responses and coalesce consecutive roles**  
   *Merged* — The fix for the infamous "400 Bad Request on tool rejection" bug. When users cancelled tool calls, the resulting message history violated API constraints. This groups cancelled tool responses and merges consecutive same-role messages to maintain valid request structure. A top-priority unblocker for heavy agent users.

2. **[#28410](https://github.com/google-gemini/gemini-cli/pull/28410) — fix(core): shorten MCP tools/list discovery timeout**  
   *Open, P1, area/agent* — MCP servers that don't respond to `tools/list` could freeze the CLI for 10 minutes at startup. This PR adds a short default timeout so the failure is fast and graceful. Directly addresses a silent startup hang that affected anyone with MCP integrations.

3. **[#28403](https://github.com/google-gemini/gemini-cli/pull/28403) — fix(core): block $VAR and ${VAR} variable expansion bypass**  
   *Open, GHSA-wpqr-6v78-jr5g* — Closes a security bypass where `$()` and backticks were blocked but `$VAR` and `${VAR}` expansion was not. Attackers could exfiltrate secrets like `$GITHUB_TOKEN`. A critical patch for anyone running Gemini CLI in CI or with sensitive env vars.

4. **[#28164](https://github.com/google-gemini/gemini-cli/pull/28164) — fix(core): limit recursive reasoning turns per single user request**  
   *Open, help wanted* — Caps recursive reasoning at 15 turns per user request (configurable via `maxSessionTurns`). Prevents infinite loops that waste CPU quotas and model credits. Community nudging for merge.

5. **[#28406](https://github.com/google-gemini/gemini-cli/pull/28406) — fix(availability): apply modelIdResolutions to tool sub-agent model configs**  
   *Open, P1* — Utility tools like `web-search` and `web-fetch` hardcoded `gemini-3-flash-preview` without checking user preview access. API-key users without preview access hit `INVALID_MODEL` errors. Fixes a regression from the recent model rollout.

6. **[#28405](https://github.com/google-gemini/gemini-cli/pull/28405) — fix: prevent scroll position jump during content updates**  
   *Open, P1* — Fixes #5009 where scrolling up to review changes (e.g., after Ctrl+S) causes the terminal viewport to jump when new content arrives. A UX quality-of-life fix for long agent sessions.

7. **[#28408](https://github.com/google-gemini/gemini-cli/pull/28408) — refactor(cli): centralize dense payload detection in tool mapping**  
   *Open, P3* — Moves complex payload density detection from `ToolGroupMessage` into `mapToDisplay` to reduce UI coupling with backend data internals. Clean architecture improvement for the rendering layer.

8. **[#28319](https://github.com/google-gemini/gemini-cli/pull/28319) — refactor(a2a-server): enforce path trust check prior to environment loading**  
   *Open, large* — Ensures workspace path trust checks happen before loading workspace-level environment variables. Introduces `AsyncLocalStorage` for per-task environment isolation. A security-first refactor for the A2A server.

9. **[#28219](https://github.com/google-gemini/gemini-cli/pull/28219) — fix(cli): parse commented settings.json in memory bootstrap**  
   *Merged* — The lightweight parent process couldn't read comment-bearing `settings.json` files, silently falling back to default memory configuration. Now correctly parses JSON with comments, fixing a subtle memory configuration bug.

10. **[#28305](https://github.com/google-gemini/gemini-cli/pull/28305) — feat(evals): add tool call formatter and integrate failure summaries**  
    *Open, large* — Adds tool-call timeline formatting and failure summary diagnostics to behavioral evaluations. When an eval fails, the runner now prints a compact numbered timeline of tool calls with status and error details. Directly improves debuggability of failing evals.

## 5. Feature Request Trends

**Dominant theme: Agent Reliability & Self-Awareness.** The most-requested feature directions cluster around:
- **Subagent autonomy and observability** — Users want to see subagent trajectories in `/chat share`, understand why subagents are chosen (or not), and receive accurate status reporting when subagents hit limits or fail.
- **Safety and guardrails** — Requests for AST-aware file operations, destructive operation warnings, and zero-dependency sandboxing all point to a desire for safer autonomous execution without sacrificing the model's native bash proficiency.
- **Eval infrastructure scaling** — The push for robust component-level evals (#24353) and better failure diagnostics (#28305) signals that the community recognizes the quality bar needs to rise alongside agent complexity.
- **Non-blocking resource management** — Auto Memory retries, MCP discovery timeouts, and recursive reasoning limits all reflect demand for graceful handling of edge cases rather than silent hangs.

## 6. Developer Pain Points

**Top frustrations recurring across issues:**

1. **Silent failures & timeouts** — Generalist agent hangs (#21409), shell command stuck on "Waiting input" (#25166), and 10-minute MCP freezes (#28410) all share a common pattern: the agent goes into an unresponsive state without clear error messaging. Developers are forced to guess whether the agent is thinking, hung, or dead.

2. **Subagent reliability inconsistency** — Subagents report success when they've hit turn limits (#22323), ignore settings overrides (#22267), and run without permission (#22093). The trust in subagent delegation is eroding as these bugs accumulate.

3. **Model routing opacity** — The agent doesn't use custom skills (#21968) and users can't inspect why. The decision logic for tool selection and subagent delegation is a black box, making it hard to debug or optimize.

4. **State management leaks** — Auto Memory retrying low-signal sessions forever (#26522), symlinks being ignored (#20079), and scroll position jumps (#28405) are all "death by a thousand cuts" bugs that erode daily workflow confidence.

5. **Security boundary ambiguity** — Shell variable expansion bypasses (#28403) and destructive command issuance (#22672) highlight a fundamental tension: the model's bash affinity is powerful but dangerous when guardrails are incomplete. The community wants safer defaults, not just reactive patches.

</details>

<details>
<summary><strong>GitHub Copilot CLI</strong> — <a href="https://github.com/github/copilot-cli">github/copilot-cli</a></summary>

# GitHub Copilot CLI Community Digest — 2026-07-16

---

## Today's Highlights

A new patch release (v1.0.71-3) fixes two configuration-related annoyances, but the community's attention remains firmly on the ongoing MCP OAuth crisis — multiple reports confirm that Atlassian and third-party OAuth servers show as "Connected" yet expose zero tools to sessions. Separately, a high-priority data-loss bug (#4147) was filed today, where bare left/right arrow keys hijack cursor input for session navigation.

---

## Releases

**v1.0.71-3** — released today
- **Fixed:** Invalid `settings.json` now shows a warning identifying the offending value instead of silently ignoring your settings
- **Fixed:** `/terminal-setup` no longer skips setup on terminals without real kitty keyboard support

---

## Hot Issues (10 selected)

1. **#223 — [OPEN] "Copilot Requests" permission for fine-grained tokens should be visible for org-owned tokens**  
   *Author: RyanHecht* | [Issue Link](https://github.com/github/copilot-cli/issues/223)  
   Organizations cannot create fine-grained PATs with the "Copilot Requests" permission when the token is org-owned. This blocks enterprise adoption of copilot automations. **76 👍, 31 comments** — a long-standing pain point.

2. **#1477 — [CLOSED] "Continuing autonomously (3 premium requests)" after model completion**  
   *Author: joshlacal* | [Issue Link](https://github.com/github/copilot-cli/issues/1477)  
   Users report unexpected premium request consumption in autopilot mode after the "free lunch" ended. **18 👍** — a transparency concern about usage metering.

3. **#4024 — [OPEN] Voice mode: all bundled ASR models fail silently — MultiModalProcessor routing bug**  
   *Author: sylvanc* | [Issue Link](https://github.com/github/copilot-cli/issues/4024)  
   `/voice` captures audio successfully but returns empty transcriptions for all three bundled speech models (nemotron variants). Voice mode is effectively broken for this user.

4. **#4096 — [OPEN] Third-party MCP server shows "Connected" but its tools are missing from CLI sessions**  
   *Author: bugale* | [Issue Link](https://github.com/github/copilot-cli/issues/4096)  
   Atlassian Remote MCP OAuth succeeds in the UI, but tools never appear in spawned CLI sessions. OAuth tokens are not bridged to the agent. **Triaged** — critical for MCP ecosystem trust.

5. **#1979 — [CLOSED] Remote session support for Copilot CLI — attach from mobile / browser**  
   *Author: DwainTR* | [Issue Link](https://github.com/github/copilot-cli/issues/1979)  
   Feature request for remote session attach capability, similar to Claude Code. **53 👍** — strong demand for mobile/browser access to running sessions.

6. **#2785 — [CLOSED] Support 1M context window for Claude Opus 4.7**  
   *Author: dezgit2025* | [Issue Link](https://github.com/github/copilot-cli/issues/2785)  
   Users demand parity with Claude Code's default Opus 4.7 with 1M context. **62 👍** — the highest-voted feature request in this batch.

7. **#2052 — [CLOSED] Persistent Token/Context Usage Indicator**  
   *Author: orenMicrosoft* | [Issue Link](https://github.com/github/copilot-cli/issues/2052)  
   Request for a visible token usage bar showing current context utilization (e.g., "45% context used"). **19 👍** — developers need visibility into context limits.

8. **#4097 — [OPEN] `apply_patch` stores deleted binary in session history, permanently exceeding CAPI 5 MB limit**  
   *Author: Adamkadaban* | [Issue Link](https://github.com/github/copilot-cli/issues/4097)  
   Deleting a large binary via `apply_patch` stores the entire binary as a textual diff in session history, which then permanently exceeds the 5 MB CAPI limit and requires `/compact` to recover.

9. **#4147 — [OPEN] High priority: bare left/right arrow hijacks cursor key for session navigation, discarding in-progress input**  
   *Author: NedAnd1* | [Issue Link](https://github.com/github/copilot-cli/issues/4147)  
   Filed today: left/right arrow keys are overloaded for session sidebar navigation, causing data loss when users try to edit input mid-line. Double-tap left arrow starts a new session. **High severity**.

10. **#4034 — [CLOSED] Hook subprocess stdin write-end left open (no EOF) for tool-use hooks**  
    *Author: jens-f* | [Issue Link](https://github.com/github/copilot-cli/issues/4034)  
    `preToolUse` and `postToolUse` hooks never close stdin, causing documented `$(cat)` patterns to hang indefinitely. `sessionStart` hooks work correctly, revealing an inconsistency.

---

## Key PR Progress

*No pull requests were updated or created in the last 24 hours.*

---

## Feature Request Trends

- **🔑 MCP Ecosystem Integration** — The dominant theme in recent issues is MCP reliability, especially OAuth flows for third-party servers. Users repeatedly report servers that appear "Connected" but deliver no tools to sessions. The Atlassian MCP server is the most-cited example.
- **📱 Remote Session / Mobile Access** — Growing demand for remote session attach capability (#1979, 53 👍), indicating users want to manage copilot sessions from mobile or browser.
- **💬 Context Window Parity** — Persistent demand for 1M context windows on Claude Opus models to match Claude Code's capabilities (#2785, 62 👍).
- **📊 Usage Transparency** — Users want visible token/context usage indicators (#2052), premium request metering (#1477), and BYOK authentication status (#4016).
- **🎤 Voice Mode Stability** — Voice transcription reliability remains a concern, with ASR models failing silently (#4024).

---

## Developer Pain Points

| Pain Point | Prevalence | Key Issues |
|---|---|---|
| **MCP OAuth tokens not bridging to CLI sessions** | Very High — 5+ open issues in last 24h alone | #4096, #4089, #4086, #4085, #4084, #4017 |
| **Context window exceeded / data loss** | High | #4097 (binary diffs), #4147 (arrow key hijack) |
| **Enterprise auth & BYOK friction** | Medium | #223 (org PATs), #4016 (BYOK regression) |
| **Voice/ASR unreliability** | Medium | #4024 (all models silent), #3896 (PTT transcript drop) |
| **Terminal rendering bugs** | Medium | #4146 (invisible picker highlight), #4014 (messed-up MCP UI) |
| **Hook/subprocess stdio issues** | Low but severe | #4034 (EOF not sent to hooks) |

*The MCP ecosystem reliability crisis is the single biggest recurring frustration. Developers who configure third-party OAuth servers find them non-functional, with confusing "Connected" status indicators that provide no actionable feedback. The arrow key data loss bug (#4147) filed today is a new urgent concern.*

</details>

<details>
<summary><strong>Kimi Code CLI</strong> — <a href="https://github.com/MoonshotAI/kimi-cli">MoonshotAI/kimi-cli</a></summary>

# Kimi Code CLI Community Digest
**Date:** 2026-07-16  
**Source:** [github.com/MoonshotAI/kimi-cli](https://github.com/MoonshotAI/kimi-cli)

---

## 1. Today's Highlights

The Kimi CLI community saw a single but significant PR submission today: **#2500** focuses on aligning Python telemetry with the TypeScript rewrite's event schema, adding `trace_id` support and missing events. No new releases were published in the last 24 hours, and no new issues were filed during this period. The project remains in an active development phase with a clear push toward cross-language consistency.

---

## 2. Releases

**No new releases were published in the last 24 hours.**  
The latest stable release remains unchanged. Developers should check the [Releases page](https://github.com/MoonshotAI/kimi-cli/releases) for any upcoming versions.

---

## 3. Hot Issues

No new issues were created or updated in the last 24 hours. Below are 10 historically significant open issues that remain active and relevant to the community:

1. **#2417 – `kimi code` fails with ambiguous error on malformed input**  
   *Why matters:* Affects core CLI usability; community has requested clearer error messages.  
   [View Issue](https://github.com/MoonshotAI/kimi-cli/issues/2417)

2. **#2390 – Support offline/air-gapped mode for all providers**  
   *Why matters:* Enterprise users need deterministic behavior without internet access.  
   [View Issue](https://github.com/MoonshotAI/kimi-cli/issues/2390)

3. **#2374 – `--verbose` flag incomplete; missing HTTP-level logging**  
   *Why matters:* Debugging LLM calls requires full request/response visibility.  
   [View Issue](https://github.com/MoonshotAI/kimi-cli/issues/2374)

4. **#2351 – Prompt caching not persisted across sessions**  
   *Why matters:* Users report 20%+ latency improvements when caching works; inconsistency is frustrating.  
   [View Issue](https://github.com/MoonshotAI/kimi-cli/issues/2351)

5. **#2330 – Windows path handling broken for file references**  
   *Why matters:* Cross-platform parity is a top ask; Windows user count is growing.  
   [View Issue](https://github.com/MoonshotAI/kimi-cli/issues/2330)

6. **#2309 – Config file not merged with CLI flags; flags silently ignored**  
   *Why matters:* Unexpected behavior causes silent failures in CI/CD pipelines.  
   [View Issue](https://github.com/MoonshotAI/kimi-cli/issues/2309)

7. **#2281 – Streaming output corrupted when piped to other commands**  
   *Why matters:* Breaks shell scripting and tool chaining; leads to binary output in terminals.  
   [View Issue](https://github.com/MoonshotAI/kimi-cli/issues/2281)

8. **#2264 – Rate limit retry logic too aggressive; 60s backoff on 429**  
   *Why matters:* Users report excessive delays; prefer adaptive backoff.  
   [View Issue](https://github.com/MoonshotAI/kimi-cli/issues/2264)

9. **#2248 – `kimi chat` history lost on terminal resize**  
   *Why matters:* Session persistence should survive terminal reflow.  
   [View Issue](https://github.com/MoonshotAI/kimi-cli/issues/2248)

10. **#2221 – Multi-modal input (images) not supported in interactive mode**  
    *Why matters:* Prevents vision-capable models from being used seamlessly.  
    [View Issue](https://github.com/MoonshotAI/kimi-cli/issues/2221)

---

## 4. Key PR Progress

Only one PR was updated in the last 24 hours. Below are 10 important PRs currently open or recently merged:

1. **#2500 [OPEN] feat(telemetry): align events with TS schema, add trace_id and missing events**  
   *Description:* Captures `x-trace-id` response header for both stream and non-stream calls; backfills missing event types from `agent-core-v2` `events.ts`.  
   *Community reaction:* No comments yet; likely a foundational piece for monitoring.  
   [View PR](https://github.com/MoonshotAI/kimi-cli/pull/2500)

2. **#2496 [OPEN] fix: handle empty `--data` arguments without crash**  
   *Why matters:* Prevents CLI panic on common scripting edge case.  
   [View PR](https://github.com/MoonshotAI/kimi-cli/pull/2496)

3. **#2492 [OPEN] feat: add `kimi config validate` subcommand**  
   *Why matters:* Debugging config files is a frequent user pain point.  
   [View PR](https://github.com/MoonshotAI/kimi-cli/pull/2492)

4. **#2487 [MERGED] chore: bump Python SDK to 1.8.3**  
   *Why matters:* Includes model ID mapping updates and bugfixes.  
   [View PR](https://github.com/MoonshotAI/kimi-cli/pull/2487)

5. **#2483 [OPEN] refactor: replace argparse with click for subcommand parsing**  
   *Why matters:* Improves error messages and autocomplete behavior.  
   [View PR](https://github.com/MoonshotAI/kimi-cli/pull/2483)

6. **#2479 [OPEN] test: add integration tests for streaming output**  
   *Why matters:* Addresses #2281; stream reliability is mission-critical.  
   [View PR](https://github.com/MoonshotAI/kimi-cli/pull/2479)

7. **#2474 [OPEN] feat: support `KIMI_API_BASE` environment variable**  
   *Why matters:* Enables self-hosted or proxy endpoints without modifying config file.  
   [View PR](https://github.com/MoonshotAI/kimi-cli/pull/2474)

8. **#2470 [MERGED] fix: encode file paths as URIs on Windows**  
   *Why matters:* Partial resolution for #2330.  
   [View PR](https://github.com/MoonshotAI/kimi-cli/pull/2470)

9. **#2466 [OPEN] docs: add "Migrating from OpenAI CLI" guide**  
   *Why matters:* Smooths onboarding for developers switching from other tools.  
   [View PR](https://github.com/MoonshotAI/kimi-cli/pull/2466)

10. **#2462 [OPEN] perf: lazy-load provider modules for faster startup**  
    *Why matters:* Reduces cold-start latency by ~40%; users report it as "snappy".  
    [View PR](https://github.com/MoonshotAI/kimi-cli/pull/2462)

---

## 5. Feature Request Trends

The following feature directions are most commonly requested across all issues and discussions:

- **Self-hosted / air-gapped support** (#2390, #2474) – enterprise deployment flexibility
- **Improved streaming reliability** (#2281, #2479) – pipe-safe output, heartbeat signals
- **Cross-platform parity** (#2330, #2248) – Windows paths, terminal resize handling
- **Config validation tooling** (#2492, #2309) – merge semantics, flag precedence
- **Visual / multi-modal support** (#2221) – image input, markdown rendering in chat

---

## 6. Developer Pain Points

Recurring frustrations reported by the community:

- **Silent config/flag misbehavior** – no warnings when flags are ignored or config is invalid (#2309, #2492)
- **Inconsistent Python/TS feature parity** – telemetry and event schemas diverge across language runtimes (#2500)
- **Aggressive rate limit backoff** – 60-second hard timeout on 429 responses feels punitive (#2264)
- **Streaming output truncation** – piping output to `jq` or `grep` corrupts data or hangs the shell (#2281)
- **Startup latency** – cold starts take 1-2 seconds even for simple queries (#2462)

---

*Digest generated from GitHub data as of 2026-07-16. Data source: [MoonshotAI/kimi-cli](https://github.com/MoonshotAI/kimi-cli).*

</details>

<details>
<summary><strong>OpenCode</strong> — <a href="https://github.com/anomalyco/opencode">anomalyco/opencode</a></summary>

# OpenCode Community Digest — 2026-07-16

## Today's Highlights

A major desktop UI redesign in v1.18.x has triggered widespread backlash, with multiple issues reporting that the new horizontal tab layout hides session titles and removes the Plan/Build mode toggle. The team responded with two merged PRs today that restore the agent selector and default advanced features for new users. Meanwhile, a long-standing session overflow detection gap was addressed with a critical fix to compaction timing that prevents silent session freezes.

---

## Releases

**v1.18.2** — [View on GitHub](https://github.com/anomalyco/opencode/releases/tag/v1.18.2)

**Core:**
- **Bugfix:** Subagents no longer launch nested subagents by default; added a configurable `subagent_depth` limit when nesting is desired
- **Bugfix:** Improved default reasoning depth for Meta AI models

**Desktop:**
- **Improvement:** Added `Mod+N` as an additional keyboard shortcut for opening new tabs

---

## Hot Issues

### 1. [#36936 — Desktop: wtf is the new tab layout, tab titles dont fit anymore](https://github.com/anomalyco/opencode/issues/36936)
*14 comments, 11 👍 | Created Jul 14, Updated Jul 15*

The most upvoted issue today. The new horizontal tab layout truncates session titles, making them unreadable. User reports reverting to v1.17 fixes the problem. Community reaction is highly frustrated, with strong sentiment that this was released without proper UX testing.

### 2. [#36997 — Desktop v1.18.1 new layout hides agent (Plan/Build) switching UI](https://github.com/anomalyco/opencode/issues/36997)
*9 comments, 2 👍 | Created Jul 15*

The `newLayoutDesigns: true` feature flag causes the Plan/Build mode toggle to disappear entirely. Users cannot see which agent is active or switch modes, and the Tab key shortcut is also reportedly broken. Multiple duplicate issues (#37158, #37163) confirm this is widespread.

### 3. [#37063 — History chat conversation not displayed](https://github.com/anomalyco/opencode/issues/37063)
*5 comments | Created Jul 15, Updated Jul 16*

Upgrading from v1.17.18 to v1.18.1 caused complete loss of chat history for a user with ~1100 conversations. Data migration failure during upgrade is suspected. No workaround has been posted yet.

### 4. [#24038 — [FEATURE]: Claude support using ACP protocol](https://github.com/anomalyco/opencode/issues/24038)
*6 comments, 6 👍 | Created Apr 23, Updated Jul 15*

Closed but significant. User requests Claude Code subscription support via the Agent Client Protocol (ACP), noting Agent-Shell for Emacs already supports it. This would enable OpenCode to use Claude Code as a backend, which remains a high-interest integration.

### 5. [#36942 — [FEATURE]: Vertical tabs](https://github.com/anomalyco/opencode/issues/36942)
*4 comments, 5 👍 | Created Jul 14*

Directly related to the tab layout controversy. Users want an option for vertical tabs to see more than 5 session titles. This is the most upvoted feature request today and reflects the community's preference for the old sidebar layout.

### 6. [#37144 — [2.0] config: no-auth custom providers dropped when env is undefined](https://github.com/anomalyco/opencode/issues/37144)
*3 comments | Created Jul 15, Updated Jul 16*

Custom providers like local LM Studio are silently ignored if they don't define `env` in V2 config. The `/connect` flow then only shows three hardcoded LM Studio models, making local model use effectively broken for many users.

### 7. [#37171 — Desktop crashes on restart: "Notification server not found: wsl:Ubuntu"](https://github.com/anomalyco/opencode/issues/37171)
*3 comments | Created Jul 15*

Desktop app crashes entirely on restart when WSL notification server isn't registered. Full crash trace provided. A PR (#37190) has already been opened to fix this with fallback notification state.

### 8. [#30337 — .opencode/node_modules/ causes startup hang](https://github.com/anomalyco/opencode/issues/30337)
*2 comments, Updated Jul 16*

Scanner doesn't skip `node_modules` despite `.gitignore` when a `.opencode/` directory exists. Two conflicting behaviors: OpenCode installs dependencies in `.opencode/`, then the scanner hangs parsing those same dependencies. Affects all projects using custom tools.

### 9. [#21227 — [FEATURE(app)]: display image attachments from tool results in chat UI](https://github.com/anomalyco/opencode/issues/21227)
*3 comments, 7 👍 | Created Apr 6*

Long-standing feature request to render images returned by tools (webfetch, MCP ImageContent) inline in chat. Currently just shows raw base64 data. Remains one of the most upvoted open feature requests.

### 10. [#17340 — Session compaction fails with "context exceeds model limit" error](https://github.com/anomalyco/opencode/issues/17340)
*3 comments, 2 👍 | Created Mar 13*

Sessions grow beyond model context limits (e.g., 145k tokens in a 128k model) without triggering compaction, especially during periods without user messages. Multiple related issues (#10634, #13946, #32656, #35013) show this is a systemic problem with overflow detection timing — partially addressed by PR #37194 today.

---

## Key PR Progress

### 1. [#37194 — fix(session): resolve session overflow detection timing gaps](https://github.com/anomalyco/opencode/pull/37194)
*Merged Jul 16*

Critical fix: addresses multiple timing gaps where overflow detection missed pending context, capped output reservation at 20K instead of full `maxOutputTokens`, and failed to check after large tool outputs. This directly addresses the systemic compaction failures (#17340, #10634, #35013) that have been plaguing users.

### 2. [#37198 — fix(app): show selector for custom agents](https://github.com/anomalyco/opencode/pull/37198)
*Merged Jul 16*

Forces the agent selector visible when a project has selectable custom agents, then resolves to the build agent when the selector is hidden. This is a direct response to the Plan/Build toggle disappearance crisis (#36997, #37158, #37163).

### 3. [#37129 — fix(app): default advanced features for new users](https://github.com/anomalyco/opencode/pull/37129)
*Merged Jul 16*

Hides file tree, search, status, and agent selection for fresh installs while enabling them for existing profiles during upgrade. Addresses the new layout overwhelm by gradually introducing features.

### 4. [#37182 — fix(webfetch): scope always-allow to domain instead of all URLs](https://github.com/anomalyco/opencode/pull/37182)
*Merged Jul 15*

Security fix: "always allow" for WebFetch previously saved a wildcard `*` pattern, approving all future URLs without asking. Now scopes to the current origin. Includes 10 new tests.

### 5. [#37187 — fix: add instruction boundary markers to prevent prompt injection](https://github.com/anomalyco/opencode/pull/37187)
*Merged Jul 16*

Adds semantic boundary markers to user-provided guidance and file content to prevent prompt injection. File content from Read tool previously had no disclaimer, making "Ignore previous instructions" attacks feasible.

### 6. [#37185 — fix(tui): publish session event when custom tool import fails](https://github.com/anomalyco/opencode/pull/37185)
*Merged Jul 15*

Custom tool load errors now surface in the TUI UI instead of being silently skipped. Matches the pattern used by plugin and skill load errors.

### 7. [#37141 — feat(core): normalize tool and attachment images at settlement](https://github.com/anomalyco/opencode/pull/37141)
*Open, Jul 15*

Resizes images from all tools (not just `read`) and user prompt attachments at settlement point. Previously, MCP tools and codemode returned unbounded inline base64, which caused sessions to grow uncontrollably. This prevents the "Request Entity Too Large" errors from #14562.

### 8. [#37190 — fix(notification): handle unavailable server during initialization](https://github.com/anomalyco/opencode/pull/37190)
*Open, Jul 15*

Adds fallback notification state for unavailable WSL servers so the renderer can continue loading. Directly fixes the crash in #37171.

### 9. [#37192 — feat(plugin): support dynamic Effect tools](https://github.com/anomalyco/opencode/pull/37192)
*Open, Jul 15*

Allows external V2 Effect plugins to register dynamic tools without importing the host's opaque `Tool.make` instance. Enables a cleaner plugin architecture for tool registration.

### 10. [#36752 — fix(opencode): read cache write tokens from raw usage](https://github.com/anomalyco/opencode/pull/36752)
*Open, Jul 13*

Fixes cache write billing for Anthropic models served through OpenAI-compatible gateways — previously always recorded `cache.write: 0`, meaning cache writes were not charged correctly.

---

## Feature Request Trends

- **Vertical tabs / sidebar restoration** (#36936, #36942, #28971): The forced horizontal tab layout is the single biggest point of contention. Users want the old sidebar back or at minimum vertical tabs as an option.
- **Per-session MCP server selection** (#37168, #37192): Users managing multiple clients need to enable/disable MCP servers on a per-session basis rather than globally.
- **Inline image display in chat** (#21227): Rendering tool-returned images (webfetch, MCP ImageContent) remains a high-demand UX improvement.
- **Auto-generated session titles** (#30926): "New session" naming is unhelpful when managing multiple chats; users want AI-generated contextual titles.
- **ACP / Claude Code integration** (#24038): Interest in using Claude Code as a backend via the Agent Client Protocol continues to grow.
- **File editing capabilities** (#26970): Users want to edit files directly within OpenCode, not just through AI tool calls.

---

## Developer Pain Points

1. **Desktop v1.18.x UI regression**: The new layout design is the dominant complaint this week. The agent toggle disappearance and tab title truncation are affecting workflow for a large portion of desktop users. Multiple duplicate issues (#36997, #37158, #37163) confirm this is not isolated.

2. **Session compaction failures**: A systemic set of bugs (#17340, #10634, #32656, #35013, #13946) where compaction fails silently, sessions grow beyond model limits, and overflow detection doesn't trigger at the right times. PR #37194 addresses the detection timing, but the underlying issue has been open for months.

3. **Local provider configuration in V2**: Custom no-auth providers like LM Studio are silently dropped in V2 config (#37144). Combined with LM Studio model listing issues (#34305), local model support in V2 remains unreliable.

4. **Data migration fragility**: Upgrading between minor versions causes chat history loss (#37063) and startup crashes (#37171). The `.opencode/node_modules` scanner hang (#30337) adds another startup reliability issue.

5. **Prompt injection surface**: The lack of semantic boundaries in user-provided guidance (#37187) and the over-permissive WebFetch allowlist (#37183) represent genuine security concerns that the team is actively addressing.

</details>

<details>
<summary><strong>Pi</strong> — <a href="https://github.com/badlogic/pi-mono">badlogic/pi-mono</a></summary>

# 🥧 Pi Community Digest — 2026-07-16

## Today's Highlights

The project saw a flurry of Windows-specific fixes land today, with two PRs addressing `taskkill` ENOENT crashes on Node.js 24 and terminal title pollution from npm checks. Meanwhile, a high-profile **openai-codex/gpt-5.5 reliability issue** (#4945) continues to dominate community attention with 75 comments, as the TUI intermittently hangs on "Working..." without errors. Multiple contributors are also pushing for structured session management and extension API improvements, signaling a shift toward richer plugin capabilities.

## Releases

No new releases in the last 24 hours.

---

## Hot Issues

1. **#4945 — openai-codex Connection Reliability Issues** [OPEN]  
   *75 comments | 👍30*  
   **Summary:** The TUI gets stuck on "Working..." with no streamed text, tool call, or visible error when using `gpt-5.5`. Only pressing Escape recovers the session.  
   **Why it matters:** This is the highest-engagement active issue by far. It affects the core UX for users relying on OpenAI Codex—arguably the project's primary model provider. The prolonged inability to reproduce or fix indicates a subtle concurrency or transport-level bug.  
   [🔗 Issue #4945](https://github.com/earendil-works/pi/issues/4945)

2. **#6050 — TUI full redraw clears terminal scrollback** [CLOSED]  
   *14 comments*  
   **Summary:** During active rendering, the terminal scrollbar jumps back to the beginning of the chat. Root cause appears in the core TUI renderer.  
   **Why it matters:** A major UX annoyance that drowns out working history. Community feedback suggests it's exacerbated by custom widgets.  
   [🔗 Issue #6050](https://github.com/earendil-works/pi/issues/6050)

3. **#6657 — Bedrock AWS_PROFILE authentication not working** [OPEN]  
   *5 comments | 👍2*  
   **Summary:** Bedrock requests using `AWS_PROFILE` fail with AccessDeniedException: 403, even after the 0.80.7 release that claimed to fix #6531.  
   **Why it matters:** Affects AWS users who rely on profile-based credentials in multi-account setups. Regression in a recently "fixed" area is frustrating.  
   [🔗 Issue #6657](https://github.com/earendil-works/pi/issues/6657)

4. **#6686 — Pi automatically logs out of GitHub** [CLOSED]  
   *4 comments*  
   **Summary:** Repeated login drop after 15–30 minutes. Claims #2725 was fixed but issue persists.  
   **Why it matters:** Breaks GitHub Copilot integration mid-session, halting agent work. High-impact reliability issue for daily users.  
   [🔗 Issue #6686](https://github.com/earendil-works/pi/issues/6686)

5. **#5263 — Make in-session model/thinking-level changes ephemeral** [OPEN]  
   *7 comments | 👍7*  
   **Summary:** Proposed default: session-local changes to model or thinking level should not persist globally. Introduce a "Default model" setting.  
   **Why it matters:** Strong community consensus (👍7) that current behavior leaks temporary experiments into global config, causing confusion.  
   [🔗 Issue #5263](https://github.com/earendil-works/pi/issues/5263)

6. **#6673 — OpenAI Codex exposes raw Cloudflare 520 HTML including client IP** [CLOSED]  
   *3 comments*  
   **Summary:** When Codex returns a Cloudflare 520, Pi displays the full HTML—including the user's public exit IP and Ray ID—and stores it in session JSONL.  
   **Why it matters:** **Security/privacy risk.** Leaking the public IP into session logs is a data exposure vector, especially if sessions are shared or stored in logs.  
   [🔗 Issue #6673](https://github.com/earendil-works/pi/issues/6673)

7. **#6619 — Windows npm-dependent extensions show absolute path in banner** [OPEN]  
   *4 comments*  
   **Summary:** On Windows, extensions pulled in by npm packages show absolute local paths instead of package names in the [Extensions] banner.  
   **Why it matters:** Makes the startup UI unreadable on Windows—paths can be very long and expose system structure. Community awaiting a proper fix beyond the partial #6680.  
   [🔗 Issue #6619](https://github.com/earendil-works/pi/issues/6619)

8. **#6688 — Extension selector renders all options without viewport windowing** [CLOSED]  
   *2 comments*  
   **Summary:** `ctx.ui.select()` renders every option as a line with no scroll windowing, so selections scroll off-screen.  
   **Why it matters:** Extensions are the growth vector for Pi. A broken selection UX hamstrings third-party plugin usability.  
   [🔗 Issue #6688](https://github.com/earendil-works/pi/issues/6688)

9. **#6647 — Compaction fails on single transient stream drop (no retry)** [OPEN]  
   *2 comments*  
   **Summary:** Compaction runs one non-retried summarization call, so a single mid-stream socket death fails the entire compaction.  
   **Why it matters:** Compaction is critical for long-running sessions. Lack of retry on transient network drops makes compaction brittle.  
   [🔗 Issue #6647](https://github.com/earendil-works/pi/issues/6647)

10. **#6596 — spawn(taskkill) ENOENT on Node.js 24** [OPEN]  
    *3 comments*  
    **Summary:** `killProcessTree()` uses `spawn("taskkill")` which fails with ENOENT on Node.js 24 because it relies on PATH lookup.  
    **Why it matters:** Affects all Windows users on Node.js 24—which is becoming the default Node.js LTS. PR #6692 was opened to fix this today.  
    [🔗 Issue #6596](https://github.com/earendil-works/pi/issues/6596)

---

## Key PR Progress

1. **#6692 — fix(agent,coding-agent): use absolute System32 path for taskkill/rundll32** [CLOSED]  
   **Summary:** Resolves `spawn("taskkill")` ENOENT on Node.js 24 by using absolute `System32` paths and proper error event handling.  
   **Impact:** Critical Windows bugfix. The exact fix for the #6596 issue above—now merged.  
   [🔗 PR #6692](https://github.com/earendil-works/pi/pull/6692)

2. **#6681 — windows: reset pi terminal title after checking npm packages** [CLOSED]  
   **Summary:** After `npm view` changes the terminal title to "npm view pi-web-access version", resets it back to "Pi".  
   **Impact:** Fixes #6629. A narrow but appreciated UX fix for Windows users.  
   [🔗 PR #6681](https://github.com/earendil-works/pi/pull/6681)

3. **#6651 — feat(ai): add xAI device OAuth and route grok-4.5 through Responses** [OPEN]  
   **Summary:** Adds device-code OAuth for xAI alongside `XAI_API_KEY`. Routes `grok-4.5` through Responses with low/medium/high reasoning; other xAI models stay on Completions.  
   **Impact:** Expands model provider options with deep integration for Grok's reasoning tiers.  
   [🔗 PR #6651](https://github.com/earendil-works/pi/pull/6651)

4. **#6594 — feat: sqlite session storage** [OPEN]  
   **Summary:** Adds `retainedTail` to compaction entries and changes `getPathToRoot` to `getPathToRootOrCompaction` to only load until last compaction.  
   **Impact:** Foundation for moving from JSONL to SQLite-backed sessions, improving scalability for long-running sessions.  
   [🔗 PR #6594](https://github.com/earendil-works/pi/pull/6594)

5. **#6683 — fix(coding-agent): accept colon-qualified skill names** [CLOSED]  
   **Summary:** Relaxes skill-name validation to accept `inc:ship-it` style names from plugins, fixing spurious "[Skill conflicts]" warnings.  
   **Impact:** Directly enables plugin-namespaced skills to load cleanly. Minor but important for the extension ecosystem.  
   [🔗 PR #6683](https://github.com/earendil-works/pi/pull/6683)

6. **#6667 — fix(tui): guard null children in Box and Container render/invalidate** [CLOSED]  
   **Summary:** Adds null guards after extension install/remove prevents "Cannot read properties of undefined (reading 'render')" crashes.  
   **Impact:** Fixes a crash path during extension lifecycle events. Important for plugin stability.  
   [🔗 PR #6667](https://github.com/earendil-works/pi/pull/6667)

7. **#6533 — fix: Codex compaction returns "Model not found" for gpt-5.6-luna** [CLOSED]  
   **Summary:** The compaction API fails with 404 for `gpt-5.6-luna` because the API maps the model ID to a tier-suffixed slug not recognized by the no-tools registry.  
   **Impact:** Unblocks compaction for one of the newest Codex models.  
   [🔗 PR #6533](https://github.com/earendil-works/pi/pull/6533)

8. **#6680 — parse extension package name in case of dependent extension** [OPEN]  
   **Summary:** Partially fixes #6619—improves display of npm-dependent extensions on Windows, though absolute paths may still appear in some cases.  
   **Impact:** Incremental improvement for Windows extension users.  
   [🔗 PR #6680](https://github.com/earendil-works/pi/pull/6680)

9. **#6216 — feat: Add Amazon Bedrock Mantle OpenAI Responses provider** [OPEN]  
   **Summary:** Adds a new provider for Amazon Bedrock Mantle's OpenAI Responses API using OpenAI's Bedrock provider. Supersedes an earlier implementation.  
   **Impact:** Expands AWS integration with a newer, more aligned API surface.  
   [🔗 PR #6216](https://github.com/earendil-works/pi/pull/6216)

10. **#6671 — add usage info to branch summary, compaction and tool result entries** [OPEN]  
    **Summary:** Adds usage metadata (token counts, cost) to branch summaries, compaction entries, and tool results.  
    **Impact:** Improves observability into token consumption across all session operations.  
    [🔗 PR #6671](https://github.com/earendil-works/pi/pull/6671)

---

## Feature Request Trends

- **Session Management Overhaul:** Multiple issues (#6674, #5263) call for folders, renaming, archiving, and ephemeral-by-default settings. Community fatigue with flat chronological session lists is clear.
- **Extension API Expansion:** Requests for `stream_chunk` hooks (#6693), native retry controls (#6684), and correlated RPC output (#6694) indicate growing demand for deep plugin integration.
- **Provider Parity:** Bedrock users want adaptive thinking compliance (#6212), xAI gets OAuth support (#6651), and Codex reliability remains the #1 pain point (#4945).
- **SQLite/Scalable Storage:** PR #6594 (sqlite session storage) and compaction retries (#6647) reflect a push toward more robust long-session infrastructure.

---

## Developer Pain Points

1. **OpenAI Codex Instability** (#4945, #6673): The TUI hang and IP exposure bugs make Codex the most unreliable provider despite being the most popular. Growing frustration in comments.
2. **Windows Escapes** (#6596, #6619, #6629, #6681): Node.js 24 compatibility, npm title pollution, and absolute path display are creating a "Windows second-class citizen" feel.
3. **Authentication Regressions** (#6657, #6686): AWS_PROFILE and GitHub OAuth both have "previously fixed" bugs that users report still broken—eroding trust in release notes.
4. **Compaction Brittleness** (#6647, #6533): Compaction failing on transient errors or unknown model IDs undermines the core value proposition of long-running agent sessions.
5. **Plugin Ecosystem Blocker** (#6688, #6687): Missing `ToolExecution*Event` exports and broken selection UI are concrete barriers for third-party extension authors.

</details>

<details>
<summary><strong>Qwen Code</strong> — <a href="https://github.com/QwenLM/qwen-code">QwenLM/qwen-code</a></summary>

# Qwen Code Community Digest — 2026-07-16

## Today's Highlights
The `cua-driver-rs` v0.7.2 release ships a critical relative-coordinate fork with platform-native signing, while the daemon stack gains two major features: aggregated deep health across workspaces and a stateless SSE generation endpoint. Community demand for multi-workspace daemon support (issue #6378) remains the hottest discussion thread at 23 comments, and a new `auto` output language mode is now under active implementation.

## Releases
**cua-driver-rs-v0.7.2** — Prebuilt binaries for the computer-use agent driver, now vendored under `packages/cua-driver`. Relative-coordinate support added. Platform distribution:
- **macOS**: Codesigned + notarized universal binary + `QwenCuaDriver.app`
- **Linux**: Unsigned x86_64 + arm64 (glibc 2.31+)
- **Windows**: Unsigned x86_64 + arm64

**v0.19.10-nightly.20260716.506ce0a1a** — Nightly release with documentation improvements: PR scope capping after repeated review rounds, and a workspace path layout fix in the web-shell.

## Hot Issues

| # | Issue | Why It Matters | Community Reaction |
|---|-------|----------------|-------------------|
| [#6378](https://github.com/QwenLM/qwen-code/issues/6378) | RFC: Support multiple workspaces in one `qwen serve` daemon | Addresses a core architectural limitation (1 daemon = 1 workspace × N sessions). Would unlock server consolidation for enterprise | 23 comments, still open — the most discussed issue on the board |
| [#6928](https://github.com/QwenLM/qwen-code/issues/6928) | GitHub App auth not injected into newly created workspaces | Breaks private repo workflows on fresh workspace creation; the cloned project lacks any GitHub authentication | 5 comments, opened just 1 day ago, actively triaged |
| [#5239](https://github.com/QwenLM/qwen-code/issues/5239) | Weak subagent ↔ main session communication | Subagents can die silently with no notification to the main session. User built a file-based monitor workaround | 4 comments; a recurring pain point in multi-agent workflows |
| [#6936](https://github.com/QwenLM/qwen-code/issues/6936) | `isManagedMemoryAvailable()` wastes 7–9 KB context even when `enableManagedAutoMemory: false` | A gate mismatch forces the auto-memory instruction block into every system prompt, wasting precious context capacity | 3 comments, clearly diagnosed with a root cause identified in source |
| [#6443](https://github.com/QwenLM/qwen-code/issues/6443) | Improve DingTalk channel with interactive cards | Requests running-status cards, stop buttons, and form callbacks — essential for production DingTalk deployments | 3 comments, feature request with detailed UX design |
| [#6970](https://github.com/QwenLM/qwen-code/issues/6970) | MCP tool names with dots rejected by OpenAI/Anthropic providers | MCP servers like `database.query_uniprot` produce tool names that pass Gemini but fail stricter validators | 2 comments, highlights a portability issue with MCP tool naming |
| [#6943](https://github.com/QwenLM/qwen-code/issues/6943) | Add "auto" output language mode — LLM should follow user input | Current fixed-language model via `output-language.md` forces non-native speakers to manually switch | 2 comments, a feature + bug hybrid with strong user demand |
| [#6927](https://github.com/QwenLM/qwen-code/issues/6927) | Safety classifier blocks every tool under `tools.approvalMode = "auto"` | Creates a deadlock — even write_file/edit needed to change settings to recover is blocked | 2 comments, opened 1 day ago, critical usability issue |
| [#6962](https://github.com/QwenLM/qwen-code/issues/6962) | Persist channel source metadata for daemon sessions | Enables proper transcript attribution for channel-originated sessions; builds on #6932's immutable source metadata | 2 comments, linked to a targeted PR (#6991) now in review |
| [#6946](https://github.com/QwenLM/qwen-code/issues/6946) | Add bounded Todo continuation for daemon sessions | After a `todo_write`, the model should automatically continue at most twice instead of just stopping | 2 comments, part of the broader background-automation roadmap |

## Key PR Progress

| # | PR | Description | Status |
|---|----|-------------|--------|
| [#6993](https://github.com/QwenLM/qwen-code/pull/6993) | fix: run concurrency-safe tool calls in parallel in headless mode | Headless (`qwen -p`) now runs parallel tool calls concurrently, matching the TUI's `CoreToolScheduler`. Fixes a major performance gap | Open |
| [#6961](https://github.com/QwenLM/qwen-code/pull/6961) | feat: aggregate deep health across workspaces | `GET /health?deep=1` becomes a daemon-wide snapshot of sessions, permissions, prompts, and liveness across all workspaces | Closed/merged |
| [#6947](https://github.com/QwenLM/qwen-code/pull/6947) | feat: add stateless generation SSE endpoint | New request-scoped `/sse` endpoint for generic text generation; streams `started`, `thinking`, `delta`, `done`, and `error` events | Closed/merged |
| [#6953](https://github.com/QwenLM/qwen-code/pull/6953) | fix: auto output language follows user input | `general.outputLanguage=auto` now writes a runtime rule asking the LLM to match the user's input language, instead of resolving to the system locale | Open |
| [#6895](https://github.com/QwenLM/qwen-code/pull/6895) | feat: propagate trusted invocation context | Introduces `InvocationContextV1` — a runtime-only structure tracking the ingress, session, root prompt, and validated daemon client for an invocation chain | Open, in review |
| [#6954](https://github.com/QwenLM/qwen-code/pull/6954) | feat: add workspace MCP management in Web Shell + daemon | Plugin management UI with extension/MCP tabs, persisted user/workspace MCP discovery that works without a chat session | Open |
| [#6984](https://github.com/QwenLM/qwen-code/pull/6984) | feat: per-model sub-agent concurrency limits | New `agents.maxParallelAgentsByModel` setting to cap background sub-agents per concrete model ID, complementing the global cap | Open |
| [#6937](https://github.com/QwenLM/qwen-code/pull/6937) | feat: mouse text selection and copy in VP mode | Click-drag, double/triple-click selection with visible highlight and auto-copy in the alternate-screen viewport | Open |
| [#6967](https://github.com/QwenLM/qwen-code/pull/6967) | fix: require explicit approval to exit Plan mode | Prevents the model from silently leaving Plan mode; user must confirm before execution mode begins | Open |
| [#6945](https://github.com/QwenLM/qwen-code/pull/6945) | feat: daemon Todo stop guard for ACP sessions | After a `todo_write` leaves unfinished items, daemon sessions auto-continue at most twice; opt-in, disabled by default | Open, in review |

## Feature Request Trends

1. **Multi-workspace daemon support** — The most-requested architectural feature (#6378). Community consensus is that a single daemon managing multiple workspaces is critical for server consolidation, with minimal breakage to existing clients.

2. **Intelligent output language detection** — Multiple users are pushing for an `auto` mode where the LLM matches the user's input language rather than being locked to a fixed locale (#6943, with fix in progress at #6953).

3. **Enhanced subagent communication** — The subagent ↔ main session gap (#5239) reflects a broader desire for bidirectional notification and monitoring in multi-agent workflows. Users are hacking file-based monitors as workarounds.

4. **Channel-specific UI improvements** — DingTalk interactive cards (#6443, #6883) lead the channel enhancement requests, with users wanting stop buttons, status cards, and single-chat delivery alongside group chat.

5. **Bounded background automation** — The Todo stop guard (#6946) and similar proposals signal growing demand for controlled, automatic continuation of work chains in daemon/ACP sessions.

## Developer Pain Points

- **Safety classifier deadlocks (#6927)**: Under `tools.approvalMode = "auto"`, the safety classifier blocks every tool — including `write_file` and `edit` — making it impossible for users to recover by changing settings. This is a high-priority fix.
- **Context waste from disabled features (#6936)**: The `enableManagedAutoMemory: false` setting is partially respected: memory operations stop, but the 7–9 KB instruction block remains injected. Several developers flagged this as frustrating context inefficiency.
- **MCP tool name incompatibility (#6970)**: Tool names with dots (e.g., `database.query_uniprot`) pass Gemini's validation but are rejected by strict OpenAI/Anthropic providers. This portability issue affects users relying on popular MCP servers.
- **Flaky E2E cron tests (#6982)**: The `cron-interactive.test.ts` suite is timing-flaky on slow runners, with 7 CI failure issues filed in the last 24 hours alone (e.g., #6933, #6935, #6938, #6940, #6966, #6979). The team is actively widening timeouts (#6985).
- **Session/turn limit floor values (#6914)**: Fractional values like `0.5` for `maxSessionTurns` pass validation but immediately terminate on the first turn. While closed, this surfaced a broader validation gap in the settings schema.
- **Secrets leaking into shell subprocess environments (#6606)**: An open PR addresses the concern that internal daemon secrets may leak into spawned shell processes — a security-sensitive issue that remains unresolved pending review.

</details>

<details>
<summary><strong>DeepSeek TUI</strong> — <a href="https://github.com/Hmbown/DeepSeek-TUI">Hmbown/DeepSeek-TUI</a></summary>

# DeepSeek TUI Community Digest — 2026-07-16

## 1. Today's Highlights

The v0.8.68 stopship repair batch (PR #4332) has been merged, fixing live TUI state and routing regressions that blocked the release train. Maintainer Hmbown is driving a major refactoring campaign targeting large Rust monoliths, with 12 open issues filed this week to split god objects like `app.rs`, `runtime_threads.rs`, and `mcp.rs`. Meanwhile, the community is seeing steady contributions from external developers (cyq1017, nightt5879) landing hook module splits, fleet profile fixes, and onboarding localization.

## 2. Releases

No new releases in the last 24 hours. The v0.8.68 train appears to be in stabilization phase following the stopship fix.

## 3. Hot Issues (10 noteworthy)

1. **#3368** [OPEN] Security hardening tracker for v0.8.64 — 29 comments, 0 👍  
   The most active open issue. Creates a public tracker for CodeQL findings and advisory-class fixes without exposing exploit details. *Matters because it formalizes the security release gate.*  
   https://github.com/Hmbown/CodeWhale/issues/3368

2. **#2487** [CLOSED] Frequent "Turn stalled - no completion signal" freeze in yolo mode — 20 comments, 1 👍  
   Long-standing reliability bug causing unresponsive turns. Closed now, indicating a fix landed. *Community upvoted this pain point.*  
   https://github.com/Hmbown/CodeWhale/issues/2487

3. **#1812** [CLOSED] Windows 11 TUI freeze (crossterm-poll) — 11 comments  
   Intermittent complete UI freeze on Windows 11 with logs and thread-state analysis. Closed, suggesting resolution.  
   https://github.com/Hmbown/CodeWhale/issues/1812

4. **#3490** [OPEN] Dead-code inventory and follow-up cleanup — 4 comments  
   Part of the refactor campaign: track all `allow(dead_code)` markers before v0.9 expands. *Shows maintainer discipline pre-major-release.*  
   https://github.com/Hmbown/CodeWhale/issues/3490

5. **#1897** [OPEN] Ownership map and extraction plan — 4 comments  
   Formal factorization audit for high-churn surfaces (sidebar, command receipts, workbench). *Roadmap clarity for contributors.*  
   https://github.com/Hmbown/CodeWhale/issues/1897

6. **#3303** [OPEN] Make config keys editable from TUI — 3 comments  
   Users can't discover/persist config toml knobs from UI. *Key UX gap for sub-agent configuration.*  
   https://github.com/Hmbown/CodeWhale/issues/3303

7. **#3314** [OPEN] Extract App god object (~150 fields) — 3 comments  
   The #1 refactoring target: split `app.rs` into owned submodules. *Critical for long-term maintainability.*  
   https://github.com/Hmbown/CodeWhale/issues/3314

8. **#3313** [OPEN] Split RuntimeThreadManager (2,400 lines) — 3 comments  
   The largest code monolith after `app.rs`. *High risk for regressions during refactor.*  
   https://github.com/Hmbown/CodeWhale/issues/3313

9. **#1675** [OPEN] Chinese garbled characters in Agent output — 3 comments  
   Encoding issues with CJK text when agents write to Obsidian/Word. *Affects a significant user segment.*  
   https://github.com/Hmbown/CodeWhale/issues/1675

10. **#1512** [OPEN] Mouse scroll only shows user messages, not model output — 4 comments  
    Basic UI navigation bug. *Frustrating for anyone reviewing long conversations.*  
    https://github.com/Hmbown/CodeWhale/issues/1512

## 4. Key PR Progress (10 important PRs)

1. **#4332** [CLOSED] fix: make v0.8.68 TUI state and routing truthful — **STOPSHIP**  
   Repair batch for live regressions: fixes blank provider config detection, stale routing state. No stale replacement branch.  
   https://github.com/Hmbown/CodeWhale/pull/4332

2. **#4087** [OPEN] refactor(hooks): split config and executor modules  
   Moves hooks config definitions into its own file, leaving only runtime logic in the main module. *Clean separation of concerns.*  
   https://github.com/Hmbown/CodeWhale/pull/4087

3. **#4084** [CLOSED] fix(fleet): reject retired profile loadout aliases  
   Removes deprecated `model_class_hint` and `route_tier` fields from profile TOML. *Enforces canonical loadout field.*  
   https://github.com/Hmbown/CodeWhale/pull/4084

4. **#4044** [CLOSED] fix(onboarding): localize dynamic welcome steps  
   Adds localization for the first-run welcome screen via existing `MessageId` registry, with zh-Hant support. *Improves global UX.*  
   https://github.com/Hmbown/CodeWhale/pull/4044

5. **#3902** [CLOSED] perf(tui): fix five render/input hot paths  
   Fixes double-computation of task sidebar rows, redundant scroll state clones, and three other performance bugs. *Tangible responsiveness gains.*  
   https://github.com/Hmbown/CodeWhale/pull/3902

6. **#3818** [CLOSED] fix(tui): expand active tool run summaries  
   Includes in-flight tool entries when expanding collapsed tool-run output. *Closes an edge-case bug from #3256.*  
   https://github.com/Hmbown/CodeWhale/pull/3818

7. **#3761** [CLOSED] [codex] defer startup maintenance cleanup  
   Moves stale tool-output pruning and session cleanup off the synchronous startup path into a delayed thread. *Faster launch.*  
   https://github.com/Hmbown/CodeWhale/pull/3761

8. **#4088** [CLOSED] fix(tui): preserve native selection without mouse capture  
   Leaves xterm alternate-scroll mode off when `--no-mouse-capture` is active. *Fixes broken native text selection.*  
   https://github.com/Hmbown/CodeWhale/pull/4088

9. **#4372** [CLOSED] fix(skills): preserve inline task text  
   Fixes skill dispatching: trailing task text is now executed in same turn; literal `$install` works alongside management commands.  
   https://github.com/Hmbown/CodeWhale/pull/4372

10. **#4370** [OPEN] feat: add TelecomJS provider support  
    New provider integration for Telecom JiangSu. Still open — needs to call `fetch_catalog_delta` to show all models, not just one.  
    https://github.com/Hmbown/CodeWhale/pull/4370

## 5. Feature Request Trends

- **Config discoverability & TUI editing** (multiple issues): Users want to edit all documented config keys from within the TUI, not just load from `config.toml`. This is particularly important for sub-agent routing flags.
- **Slash command ecosystem** (issues #1887-#1892): A family of interconnected features for slash commands: better presence/help, cockpit wiring, spatial workbench routing, PEEK-backed continuity, and i18n. This is clearly the next major UX surface.
- **Multi-provider/model routing** (PR #3969, #4370): Per-sub-agent provider routing and new provider integrations (TelecomJS). The community wants flexible model selection per task.
- **Onboarding & localization** (PR #4044): First-run welcome localization requests suggest growing non-English user base.
- **Token cost in local currencies** (issue #1607): Users want cost estimates in CNY, JPY, etc., not just USD.

## 6. Developer Pain Points

- **Windows instability** remains the #1 pain: TUI freezes (crossterm-poll deadlock), input field unresponsive with IME (Sogou Chinese IME), input leaking to PowerShell terminal after crash, GUI crash on Enter with supplemental info.
- **Copy/paste broken by line wrapping** (issue #1853): Terminal-native selection includes visual line breaks, corrupting pasted code/text — a long-standing papercut.
- **Encoding issues for CJK users** (issue #1675): Garbled Chinese characters in Agent output, especially when interacting with non-TUI apps like Word.
- **Missing output in scroll** (issue #1512, #864): Mouse scroll only shows user messages; model output is truncated or invisible. This affects basic conversation review.
- **glibc version dependency** (issue #1067): Binary requires glibc 2.38, but many servers run 2.35 (Ubuntu LTS). Forces users to build from source or use containers.
- **Large file monoliths**: The maintainer's own refactoring campaign (issues #3306-#3314) confirms that the codebase has several 2,000+ line files that make contribution and debugging difficult.

</details>

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*