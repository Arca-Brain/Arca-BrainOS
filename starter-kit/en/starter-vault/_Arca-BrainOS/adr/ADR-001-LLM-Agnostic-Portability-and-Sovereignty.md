---
date: "2026-08-09"
title: "ADR-001 : LLM-Agnostic Portability and Sovereignty (From Sovereign Cloud to 100% Local)"
status: "accepted"
tags:
  - adr
  - architecture
  - arca-brainos
  - retroactive-v1
target: "[[P-Sovereign-AI-Project]]"
---

# 📜 ADR-001 : LLM-Agnostic Portability and Sovereignty (From Sovereign Cloud to 100% Local)

> *Status: Retro-documented for Arca-BrainOS v1.0.0 release.*

---

## 1. Context & Problem Statement
Most AI-powered personal knowledge management (PKM) tools lock users into vendor dependency. They rely on proprietary closed APIs (OpenAI, Anthropic) or centralized cloud backends without privacy or Zero Data Retention (ZDR) guarantees.

This poses critical risks:
- **Loss of Sovereignty:** Entrusting private and strategic thoughts to third parties subject to extraterritorial jurisdiction (e.g. Cloud Act).
- **Planned Obsolescence:** If an API provider deprecates a model, raises pricing, or changes terms of service, the Second Brain stops working.
- **Enterprise Incompatibility:** High-security environments (defense, healthcare, banking, legal) strictly prohibit transmitting confidential knowledge to non-sovereign public clouds.

---

## 2. Decision
Arca-BrainOS is designed to be **100% LLM-agnostic and runtime-independent**:

1. **Universal Markdown Prompts & Skills:** All skills (`Skill_arca-*.md`), process guides (`Process-*.md`), and system constitutions (`AGENTS.md`) are written in plain deterministic Markdown, avoiding lock-in to proprietary agent frameworks (LangChain, AutoGen, CrewAI).
2. **Strict Engine vs Runner Decoupling:** The engine lives inside the local vault. Users can execute Arca-BrainOS on their preferred infrastructure:
   - *Leading Cloud Runners:* Google Antigravity CLI (Gemini Pro), Claude Code (Claude 3.5 Sonnet), OpenAI Codex.
   - *Sovereign & GDPR Cloud Providers:* Scaleway, Mistral AI, OVHcloud.
   - *100% Local & Air-Gapped Runners (ZDR):* Ollama, LM Studio, vLLM, llama.cpp (Qwen 2.5, DeepSeek, Llama 3).
3. **Format Longevity:** Even during complete network outages or vendor shutdowns, the vault remains readable, editable, and operable.

---

## 3. Consequences & Trade-offs
- **Immediate Benefits:**
  - Total data sovereignty and decade-long durability.
  - Portability across cloud and local execution.
  - Deployable in restricted corporate security environments.
- **Accepted Trade-offs & Constraints:**
  - Rejection of vendor-specific proprietary function-calling in favor of universal protocols (Markdown files, POSIX CLI, standard MCP).

---

## 4. Alternatives Considered
- **Dedicated Obsidian TypeScript Plugin:** Rejected because it would constrain execution to Obsidian rather than CLI or other environments.
- **External Python Framework (CrewAI, LangChain):** Rejected due to dependency overhead, API breaking changes, and high installation friction.

---

## 5. References & Links
- Core Project: [[P-Sovereign-AI-Project]]
- Manifesto: [[MANIFESTO.md]]
