# AI Open Source Trends 2026-07-09

> Sources: GitHub Trending + GitHub Search API | Generated: 2026-07-09 02:01 UTC

---

Here is the **AI Open Source Trends Report** for **2026-07-09**.

---

## 1. Today's Highlights

Today marks a decisive shift toward **production-ready AI agent infrastructure**. The trending list is dominated by projects that give AI agents "hands" (OfficeCLI for document automation), "eyes" (claude-video for visual input), and "memory" (TencentDB-Agent-Memory for persistent context). Notably, the open-source community is aggressively **reverse-engineering proprietary system prompts** (system_prompts_leaks surged +1,218 stars), signaling a hunger for transparency and replicability in agent behavior. Meanwhile, **Alibaba's zvec** entered the vector database arena with a lightweight, in-process design, challenging heavier incumbent solutions.

## 2. Top Projects by Category

### 🔧 AI Infrastructure
- **[zvec](https://github.com/alibaba/zvec)** — ⭐14.4K total / +395 today — Alibaba's lightweight, in-process vector database, claiming lightning-fast performance for embedded AI workloads.
- **[CubeSandbox](https://github.com/TencentCloud/CubeSandbox)** — ⭐564 today — Instant, concurrent, and secure sandbox execution for AI agents, addressing the safety gap in agent deployment.
- **[system_prompts_leaks](https://github.com/asgeirtj/system_prompts_leaks)** — ⭐54.2K total / +1,218 today — Extracted system prompts from 10+ major AI providers (Claude, GPT-5.5, Gemini, Grok); a critical resource for understanding and replicating proprietary agent behavior.
- **[rig](https://github.com/0xPlaygrounds/rig)** — ⭐7.9K total — Build modular and scalable LLM applications in Rust, gaining traction for its performance and safety guarantees.
- **[TencentDB-Agent-Memory](https://github.com/TencentCloud/TencentDB-Agent-Memory)** — ⭐318 today — A four-tier local memory pipeline for AI agents, delivering persistent context without external API dependencies.

### 🤖 AI Agents / Workflows
- **[OfficeCLI](https://github.com/iOfficeAI/OfficeCLI)** — ⭐1,717 today — The first Office suite purpose-built for AI agents to read, edit, and automate Word, Excel, and PowerPoint files in a single binary — no Office installation required.
- **[agent-skills](https://github.com/addyosmani/agent-skills)** — ⭐1,297 today — Production-grade engineering skills for AI coding agents; a curated library of reusable skill modules.
- **[DesktopCommanderMCP](https://github.com/wonderwhy-er/DesktopCommanderMCP)** — ⭐28 today — MCP server giving Claude terminal control, file system search, and diff file editing — bridging CLI and agentic workflows.
- **[superpowers](https://github.com/obra/superpowers)** — ⭐1,116 today — An agentic skills framework and software development methodology that standardizes how agents execute complex tasks.
- **[last30days-skill](https://github.com/mvanhorn/last30days-skill)** — ⭐352 today — An AI agent skill that researches any topic across Reddit, X, YouTube, HN, Polymarket, and the web, then synthesizes a grounded summary — a practical multi-source RAG skill.

### 📦 AI Applications
- **[claude-video](https://github.com/bradautomates/claude-video)** — ⭐951 today — Gives Claude the ability to watch any video by downloading, extracting frames, transcribing, and handing the content to the LLM — a breakthrough for video-based AI reasoning.
- **[RuView](https://github.com/ruvnet/RuView)** — ⭐799 today — Turns commodity WiFi signals into real-time spatial intelligence and vital sign monitoring without any camera — an innovative application of AI on non-visual sensory data.
- **[autoremesher](https://github.com/huxingyi/autoremesher)** — ⭐296 today — Automatic quad remeshing tool using AI for 3D model optimization, relevant for game development and digital twins.

### 🧠 LLMs / Training
- ***(No new training or model-weight projects appeared in today's trending list — reflecting a community focus on application-layer tools over foundational model work.)***

### 🔍 RAG / Knowledge
- **[Graphify-Labs/graphify](https://github.com/Graphify-Labs/graphify)** — ⭐80.5K total — AI coding assistant skill that turns any code folder, schema, or documentation into a queryable knowledge graph; a massively popular bridge between RAG and code intelligence.
- **[mem0ai/mem0](https://github.com/mem0ai/mem0)** — ⭐60.4K total — Universal memory layer for AI agents, providing persistent context and recall across sessions.
- **[infiniflow/ragflow](https://github.com/infiniflow/ragflow)** — ⭐84.6K total — Leading open-source RAG engine combining advanced retrieval with agent capabilities for a superior context layer.
- **[StarTrail-org/LEANN](https://github.com/StarTrail-org/LEANN)** — ⭐12.7K total — MLsys2026 paper implementation delivering 97% storage savings for RAG on personal devices, blending efficiency with privacy.

---

## 3. Trend Signal Analysis

The most explosive community attention today is on **agent "skills" and "hands"** — modules that give AI agents the ability to interact with real-world tools (OfficeCLI, DesktopCommanderMCP, agent-skills, superpowers). This signals a maturation from simple chat-based agents to **tool-using, task-executing autonomous workers**. The +1,717 stars for OfficeCLI suggest developers are eager to unlock document automation workflows that have been gated by proprietary APIs.

A new direction appearing for the first time is **sensory agent interfaces**: claude-video (video understanding) and RuView (WiFi-based sensing) extend agent perception beyond text. This could herald a wave of multimodal agent capabilities. Additionally, **system_prompts_leaks** (+1,218) reflects a community-demand for transparency and reproducibility — developers are tired of black-box agent behavior and are actively reverse-engineering prompts to replicate or improve upon proprietary systems.

The connection to recent LLM releases is indirect but clear: with models like Claude 5 and GPT-5.5 becoming more capable, the bottleneck has shifted from model intelligence to **agent infrastructure**. Projects like TencentDB-Agent-Memory and CubeSandbox directly address the memory and security gaps that prevent production deployment.

---

## 4. Community Hot Spots

- **[OfficeCLI](https://github.com/iOfficeAI/OfficeCLI)** — The most starred project today (+1,717). Any developer automating business workflows will want this. It closes the gap between AI agents and the world's most common document formats.
- **[system_prompts_leaks](https://github.com/asgeirtj/system_prompts_leaks)** — With 54K total stars and climbing, this repository is essential for anyone trying to understand or replicate cutting-edge agent behavior from Anthropic, OpenAI, and Google.
- **[agent-skills](https://github.com/addyosmani/agent-skills)** — From Google Chrome leadership, this is becoming the de-facto library of reusable, production-grade skills for coding agents. Watch for rapid community expansion.
- **[claude-video](https://github.com/bradautomates/claude-video)** — Video understanding for agents is an underserved space. This project could unlock new use cases in media analysis, surveillance, and education.
- **[zvec](https://github.com/alibaba/zvec)** — Alibaba entering the vector database space with a lightweight, in-process design challenges Qdrant, Milvus, and LanceDB. Worth evaluation for embedded or edge deployments.

---
*This digest is auto-generated by [agents-radar](https://github.com/leevaluder-maker/agents-radar).*