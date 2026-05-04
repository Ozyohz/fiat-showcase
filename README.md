<p align="center">
  <img src="https://img.shields.io/badge/FIAT-AI%20Agent%20Platform-0d1117?style=for-the-badge&logo=openai&logoColor=white&labelColor=0d1117" alt="FIAT" />
</p>

<h1 align="center">🤖 FIAT — Full-stack Intelligent Agent Toolkit</h1>

<p align="center">
  <b>A production-grade AI agent platform with multi-agent orchestration, real-time streaming, and a modern glassmorphism UI.</b>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10+-3776AB?style=flat-square&logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/TypeScript-5.x-3178C6?style=flat-square&logo=typescript&logoColor=white" />
  <img src="https://img.shields.io/badge/React-18-61DAFB?style=flat-square&logo=react&logoColor=black" />
  <img src="https://img.shields.io/badge/FastAPI-0.115-009688?style=flat-square&logo=fastapi&logoColor=white" />
  <img src="https://img.shields.io/badge/Tailwind%20CSS-4-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white" />
  <img src="https://img.shields.io/badge/License-Private-red?style=flat-square" />
</p>

---

## 📌 Overview

**FIAT** is a full-stack AI agent platform I designed and built. It supports single-agent chat, multi-agent orchestration, RAG pipelines, knowledge bases, and more — all behind a unified API and a polished React frontend.

> ⚠️ This is a **private project** — this repo contains only the README for portfolio purposes. The full source code is available upon request.

---

## ✨ Key Features

### 🧠 Intelligent Agent System
- **ReAct Agent Loop** — reasoning + action cycle with tool calls, powered by a ported & extended Claude Code engine
- **Multi-agent Orchestration** — phased, hierarchical, and plan-build modes with automatic task decomposition
- **Smart Routing** — auto-classifies user intent and routes to the best agent or orchestration strategy
- **Human-in-the-loop (HITL)** — real-time interruption, approval gates, and seamless resume

### 🔗 Multi-Agent Architecture
- **Onion Middleware Stack** — tracing → guard → rate-limit → budget → routing → context, each handling pre/post phases
- **CC Worker Pool** — singleton pool with semaphore-based concurrency control for both user-facing and internal task agents
- **Orchestration Managers** — `PhasedManager`, `HierarchicalManager`, `PlanBuildManager` with nestable delegation
- **Handoff Tools** — lightweight Swarm-style agent-to-agent delegation via tool calls

### 🗃️ Knowledge & Memory
- **RAG Pipeline** — multi-format document ingestion (PDF, DOCX, PPTX, Excel), chunking, vector search (Milvus, Qdrant, MongoDB)
- **Knowledge Base** — graph-based knowledge system with semantic search and citation tracking
- **Memory System** — short-term (in-memory), long-term (Redis, SQLite), with automatic compression
- **Brain / Vault** — wiki-like knowledge management with frontmatter, git-backed versioning

### 🛠️ Tools & Integrations
- **MCP Support** — Model Context Protocol client with fine-grained callable functions
- **A2A Protocol** — Google's Agent-to-Agent protocol for inter-service agent communication
- **Plugin System** — extensible plugin architecture for custom tools and capabilities
- **40+ Built-in Tools** — code execution, shell, web search, file operations, data analysis, and more

### 📡 Real-time & Streaming
- **SSE Streaming** — `thinking → token_chunk → done` event protocol for real-time chat
- **Realtime Voice Agent** — voice input/output with WebSocket support
- **Temporal Workflows** — durable, long-running agent workflows with progress tracking

### 🎨 Frontend (React + Tailwind CSS 4)
- **Glassmorphism Design** — dark-first theme with backdrop blur, teal accents, and smooth animations
- **45+ Pages** — chat, agents, models, tools, RAG, memory, knowledge graph, organization, automation, tracing, and more
- **Real-time UI** — streaming chat, live tracing, interactive pipeline visualization

---

## 🏗️ Architecture

```
┌────────────────────────────────────────────────────────────┐
│                     ENTRY POINTS                           │
│  /chat/stream   /a2a   Temporal   /workflows               │
└──────┬────────────┬────────┬──────────┬────────────────────┘
       │            │        │          │
       ▼            ▼        ▼          ▼
┌────────────────────────────────────────────────────────────┐
│              ONION MIDDLEWARE STACK                         │
│  Tracing → Guard → RateLimit → Budget → Routing → Context  │
└──────────────────────┬─────────────────────────────────────┘
                       │
          ┌────────────┼────────────┐
          ▼            ▼            ▼
   ┌──────────┐ ┌───────────┐ ┌──────────┐
   │  Single  │ │  Multi-   │ │   Task   │
   │  Agent   │ │  Agent    │ │  Agent   │
   │ (CC Eng) │ │ Orchestr. │ │ (Internal│
   └──────────┘ └─────┬─────┘ └──────────┘
                      │
         ┌────────────┼────────────┐
         ▼            ▼            ▼
   ┌──────────┐ ┌──────────┐ ┌──────────┐
   │  Phased  │ │ Hierarch.│ │ PlanBuild│
   │  Manager │ │  Manager │ │  Manager │
   └──────────┘ └──────────┘ └──────────┘
                      │
                      ▼
         ┌──────────────────────┐
         │    CC Worker Pool    │
         │  (Semaphore-bounded) │
         │  Each worker = full  │
         │  CC Engine session   │
         └──────────────────────┘
```

---

## 🧰 Tech Stack

| Layer | Technologies |
|-------|-------------|
| **Backend** | Python 3.10+, FastAPI, SQLAlchemy, Alembic, Pydantic |
| **Frontend** | React 18, TypeScript, Vite, Tailwind CSS 4, Zustand |
| **AI / LLM** | OpenAI, Anthropic, DashScope (Qwen), Gemini, Ollama |
| **Protocols** | MCP (Model Context Protocol), A2A (Agent-to-Agent), SSE |
| **Vector DBs** | Milvus, Qdrant, MongoDB, OceanBase |
| **Memory** | Redis, SQLite, In-Memory, Mem0 |
| **Orchestration** | Temporal (durable workflows), asyncio concurrency |
| **Observability** | OpenTelemetry, Langfuse, custom tracing |
| **Infrastructure** | Docker, Docker Compose, K8s-ready |

---

## 📊 Scale

| Metric | Value |
|--------|-------|
| **Backend modules** | 30+ Python modules (~200k+ LoC) |
| **API routes** | 100+ REST endpoints |
| **Frontend pages** | 45+ React pages |
| **Supported LLM providers** | 5+ (OpenAI, Anthropic, Qwen, Gemini, Ollama) |
| **Vector DB integrations** | 5 (Milvus, Qdrant, MongoDB, MySQL, OceanBase) |
| **Built-in tools** | 40+ |

---

## 🖼️ Screenshots

> Screenshots are available upon request. The frontend features a dark glassmorphism design with teal accents, streaming chat, knowledge graph visualization, and a multi-agent pipeline builder.

---

## 👤 Author

**Luan Dang Quang**  
📧 Ozyohz@gmail.com  
🔗 [GitHub](https://github.com/Ozyohz)

---

<p align="center">
  <i>Built with ❤️ and a lot of caffeine ☕</i>
</p>
