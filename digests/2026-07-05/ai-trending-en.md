# AI Open Source Trends 2026-07-05

> Sources: GitHub Trending + GitHub Search API | Generated: 2026-07-05 02:07 UTC

---

# AI Open Source Trends Report — 2026-07-05

## 1. Today's Highlights

The AI open-source ecosystem today is dominated by **agent skill ecosystems and token optimization**, reflecting a maturing phase where raw model capabilities are being wrapped in practical, cost-reducing tools. The standout project is **caveman** (1,089 stars today), a Claude Code skill that slashes 65% of token usage by adopting a primitive communication style — a playful but technically significant signal that token economics is now a first-class UX concern. Simultaneously, the explosion of **Agent Skills** repositories (three separate repos trending, with `mattpocock/skills` at +973 stars) indicates the community is standardizing how AI coding agents are extended, moving from ad-hoc prompt hacking to structured, shareable skill packages. The debut of **Strix** (+1,904 stars), an open-source AI penetration testing tool, marks a new vertical application wave where AI agents are turned toward cybersecurity. Notably, the **system_prompts_leaks** repo (+471 stars) continues to aggregate leaked system prompts from major AI labs, suggesting an ongoing community obsession with reverse-engineering frontier model behavior.

## 2. Top Projects by Category

### 🔧 AI Infrastructure (Frameworks, SDKs, Dev Tools)

| Project | Stars | Description |
|---------|-------|-------------|
| [usestrix/strix](https://github.com/usestrix/strix) | ⭐0 (+1,904 today) | Open-source AI penetration testing tool that finds and fixes application vulnerabilities using autonomous agents. |
| [Zackriya-Solutions/meetily](https://github.com/Zackriya-Solutions/meetily) | ⭐0 (+718 today) | Privacy-first AI meeting assistant with 4x faster Parakeet/Whisper live transcription, speaker diarization, and Ollama summarization — 100% local on Rust. |
| [alibaba/page-agent](https://github.com/alibaba/page-agent) | ⭐0 (+742 today) | JavaScript in-page GUI agent that lets users control web interfaces with natural language. |
| [googleworkspace/cli](https://github.com/googleworkspace/cli) | ⭐29,390 (topic:ai-agent) | AI-agent-ready CLI for Google Workspace (Drive, Gmail, Calendar) built from Google Discovery Service. |
| [crynta/terax-ai](https://github.com/crynta/terax-ai) | ⭐0 (+62 today) | Lightweight (7MB) terminal-first AI-native dev workspace. |

### 🤖 AI Agents / Workflows

| Project | Stars | Description |
|---------|-------|-------------|
| [openai/codex-plugin-cc](https://github.com/openai/codex-plugin-cc) | ⭐0 (+718 today) | OpenAI's plugin enabling Claude Code to delegate tasks to Codex for code review, signaling cross-model interoperability. |
| [JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman) | ⭐0 (+1,089 today) | Viral Claude Code skill that reduces token usage by 65% by "talking like a caveman" — a token-efficiency breakthrough. |
| [mattpocock/skills](https://github.com/mattpocock/skills) | ⭐0 (+973 today) | Production-grade Claude Code skills from a TypeScript expert, pushing skill standardization. |
| [NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent) | ⭐209,231 (topic:ai-agent) | "The agent that grows with you" — a state-of-the-art general-purpose AI agent framework. |
| [CherryHQ/cherry-studio](https://github.com/CherryHQ/cherry-studio) | ⭐48,160 (topic:ai-agent) | AI productivity studio with 300+ assistants and autonomous agents, unified access to frontier LLMs. |
| [HKUDS/nanobot](https://github.com/HKUDS/nanobot) | ⭐45,009 (topic:ai-agent) | Lightweight, open-source AI agent for tools, chats, and workflows — single-line install. |
| [bytedance/deer-flow](https://github.com/bytedance/deer-flow) | ⭐76,105 (topic:llm) | Long-horizon SuperAgent harness from ByteDance that researches, codes, and creates over multi-hour tasks. |

### 📦 AI Applications (Vertical Solutions)

| Project | Stars | Description |
|---------|-------|-------------|
| [santifer/career-ops](https://github.com/santifer/career-ops) | ⭐58,549 (topic:ai-agent) | AI-powered job search system built on Claude Code with 14 skill modes and PDF generation. |
| [CoplayDev/unity-mcp](https://github.com/CoplayDev/unity-mcp) | ⭐0 (+69 today) | MCP bridge between AI assistants and Unity Editor for managing assets, scenes, and scripts. |
| [dotnet/skills](https://github.com/dotnet/skills) | ⭐0 (+59 today) | Microsoft's official repository for skills to assist AI coding agents with .NET and C# development. |
| [hugohe3/ppt-master](https://github.com/hugohe3/ppt-master) | ⭐36,638 (topic:ai-agent) | AI that generates editable PowerPoint presentations from documents with charts, animations, and audio. |

### 🧠 LLMs / Training & Fine-Tuning

| Project | Stars | Description |
|---------|-------|-------------|
| [ollama/ollama](https://github.com/ollama/ollama) | ⭐175,470 (topic:llm) | Now supports Kimi-K2.6, GLM-5.1, MiniMax, and more — the go-to local LLM runner. |
| [huggingface/transformers](https://github.com/huggingface/transformers) | ⭐162,237 (topic:llm) | The canonical model-definition framework for all state-of-the-art ML models. |
| [vllm-project/vllm](https://github.com/vllm-project/vllm) | ⭐85,374 (topic:llm) | High-throughput LLM inference serving engine, essential production infrastructure. |
| [open-compass/opencompass](https://github.com/open-compass/opencompass) | ⭐7,154 (topic:llm-model) | Comprehensive LLM evaluation platform supporting 100+ datasets and major model families. |
| [AarambhDevHub/aarambh-ai](https://github.com/AarambhDevHub/aarambh-ai) | ⭐7 (topic:llm-model) | Pure Rust decoder-only LLM with INT4 quantization, LoRA/QLoRA, and GRPO alignment — from scratch. |

### 🔍 RAG / Knowledge Management

| Project | Stars | Description |
|---------|-------|-------------|
| [Graphify-Labs/graphify](https://github.com/Graphify-Labs/graphify) | ⭐77,699 (topic:rag) | Turn any folder of code, docs, or media into a queryable knowledge graph for AI coding assistants. |
| [mem0ai/mem0](https://github.com/mem0ai/mem0) | ⭐60,094 (topic:rag) | Universal memory layer for AI agents — persistent context across sessions. |
| [thedotmack/claude-mem](https://github.com/thedotmack/claude-mem) | ⭐85,843 (topic:rag) | Captures agent sessions, compresses with AI, injects context into future sessions — works across Claude Code, Codex, Gemini, and more. |
| [infiniflow/ragflow](https://github.com/infiniflow/ragflow) | ⭐84,280 (topic:rag) | Leading open-source RAG engine fusing retrieval with agent capabilities for LLMs. |
| [milvus-io/milvus](https://github.com/milvus-io/milvus) | ⭐45,072 (topic:vector-db) | Cloud-native vector database for scalable ANN search — production-grade AI retrieval. |
| [headroomlabs-ai/headroom](https://github.com/headroomlabs-ai/headroom) | ⭐56,547 (topic:rag) | Token compression library achieving 60-95% fewer tokens with same answers — MCP server and proxy. |

## 3. Trend Signal Analysis

**Token economy is the new frontier.** The explosive popularity of `caveman` (+1,089 stars) and `headroomlabs-ai/headroom` (56k total, both trending) reveals that the community has shifted from "can AI do this?" to "how can AI do this cheaper?" Token optimization — whether through communication compression, output pruning, or caching — is emerging as its own category of AI infrastructure. The fact that a joke skill like caveman achieves real 65% token reduction while going viral suggests serious cost pressures in production agent deployments.

**Agent skill ecosystems are standardizing rapidly.** Three trending repos (`mattpocock/skills`, `alirezarezvani/claude-skills`, `dotnet/skills`) plus the `agentskills/agentskills` specification repo point to the emergence of a **skill market** for AI coding agents. This mirrors the plugin economy that emerged around IDEs and Slack — but compressed into weeks rather than years. Microsoft's official participation (`dotnet/skills`) validates this as a platform shift.

**Cross-model interoperability is becoming real.** OpenAI's `codex-plugin-cc` — allowing Claude Code to delegate to Codex — signals that the AI coding assistant ecosystem is moving away from walled gardens. This, combined with `system_prompts_leaks` aggregating prompts from 10+ providers, suggests a future where agents route tasks across models based on cost/quality tradeoffs.

**Security as an agent use-case has arrived.** `strix` (+1,904 today) marks the first major open-source AI penetration testing tool to trend. The cybersecurity community is embracing AI agents for vulnerability discovery, which could dramatically change the economics of security testing.

**Local-first AI is mainstream.** Both `meetily` (Rust-based local transcription/summarization) and `ollama/ollama` (now supporting 7+ model families) confirm that on-device processing — for privacy, latency, and cost reasons — is no longer niche but a core design principle.

## 4. Community Hot Spots

- **🪨 Caveman token optimization** — [JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman): The most viral AI tool today, demonstrating that even "joke" projects can uncover serious cost-saving patterns. Developers should study its token-reduction methodology.

- **🎯 Agent Skills standardization** — [mattpocock/skills](https://github.com/mattpocock/skills), [agentskills/agentskills](https://github.com/agentskills/agentskills), [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills): The skill ecosystem is consolidating rapidly. Early adopters of structured skill development will have platform advantage as these tools proliferate.

- **🛡️ AI pen testing** — [usestrix/strix](https://github.com/usestrix/strix): The highest-star gainer today (+1,904). Security tooling powered by AI agents is a greenfield opportunity — expect rapid innovation here.

- **🧠 Persistent agent memory** — [thedotmack/claude-mem](https://github.com/thedotmack/claude-mem) (85k stars), [mem0ai/mem0](https://github.com/mem0ai/mem0) (60k stars): Both trending across topic searches. Solving session persistence is the "killer app" for production agents; this space is attracting massive community investment.

- **🔌 MCP ecosystem expansion** — [CoplayDev/unity-mcp](https://github.com/CoplayDev/unity-mcp), [ChromeDevTools/chrome-devtools-mcp](https://github.com/ChromeDevTools/chrome-devtools-mcp): The Model Context Protocol is being adopted beyond simple file access into game engines and browser devtools — watch for MCP becoming the universal integration standard for AI agents.

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*