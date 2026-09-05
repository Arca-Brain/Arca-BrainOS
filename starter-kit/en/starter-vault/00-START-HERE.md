---
date_created: 2026-09-05
title: "👋 Welcome to Arca-BrainOS: Quickstart Guide (3 Minutes)"
tags:
  - onboarding
  - guide
  - arca-brainos
status: #active
---

# 👋 Welcome to Your Arca-BrainOS Sandbox!

Congratulations on opening the **Arca-BrainOS Starter Vault**.

This vault is a pre-configured, fully autonomous, and secure environment. Your knowledge lives **100% locally in plain Markdown files (`.md`)**: you maintain complete data sovereignty with zero proprietary lock-in.

> 💡 **Personal Exploration Context:** This system is crafted for personal usage on your local machine. Take your time to explore freely!

---

## ⚡ Fast 2-Step Onboarding

### 1️⃣ Step 1: Launch Your AI Assistant (1 Minute)

Arca-BrainOS is orchestrated by a **local AI agent** that reads, links, and organizes your notes according to the system constitution (`_Arca-BrainOS/AGENTS.md`).

Open a terminal inside this vault folder and launch your preferred AI co-pilot:

- **Option A (Recommended & Free): Google Antigravity CLI / Gemini CLI**  
  Fast, generous rate limits, and free with a Google AI Studio API key.
- **Option B (Advanced & Powerful): Claude Code**  
  For users with an Anthropic / Claude account.
- **Option C (Multi-Model & Local): OpenCode**  
  Ideal for running local models (Ollama, Qwen, DeepSeek) or sovereign APIs.
- **Option D (Graphical IDE): Cursor or VS Code**  
  Simply open this vault folder in Cursor/VS Code and use the AI chat panel.

---

### 2️⃣ Step 2: Your First "Magic Run" in 30 Seconds

To witness how AI eliminates administrative friction without altering your core ideas, a sample raw note is waiting in your [`0-Inbox/`](0-Inbox/) folder:  
👉 [`0-Inbox/Raw-Idea-Agentic-Architecture.md`](0-Inbox/Raw-Idea-Agentic-Architecture.md)

#### 🪄 The Action to Take:
In your AI terminal chat, simply run:
```bash
arca-inbox-process
```
*(or prompt in plain English: "Process my inbox and organize new notes")*

#### 👁️ What Happens in 10 Seconds:
1. The AI agent analyzes your raw note without losing a single word of your original text.
2. It normalizes the YAML frontmatter (`category: idea`, `tags`, `status`).
3. It distills the core insight, preserves the raw text (*Raw Note*), and detects a link to the demo project [`1-Projects/P-Sovereign-AI-Project.md`](1-Projects/P-Sovereign-AI-Project.md).
4. It neatly files the processed note into [`2-Ressources/Notes/`](2-Ressources/Notes/): your inbox is back to clean (**Inbox Zero**)!

---

## 🎯 Second Experiment: Framing a Deep Work Session

To jump into a focused work session on a project without wandering:

Run in your AI terminal:
```bash
arca-resume 1-Projects/P-Sovereign-AI-Project.md
```

**What your co-pilot does:**
- Scans current project progress and active milestones.
- Suggests a clear **Session Intent** with 2 or 3 priority actions.
- Initializes a timestamped session log at the top of the project note.

When your work session is finished, run `arca-close-session 1-Projects/P-Sovereign-AI-Project.md` to compute your net time saved and record your session log.

---

## 🚀 Third Experiment: Create Your Own Project in 1 Line

Ready to launch a real-world personal or professional project (e.g., home renovation, learning a skill, fitness goal, travel, or writing)?

Simply run in your AI terminal:
```bash
create-project My New Project
```

**What your AI co-pilot does:**
1. Analyzes your project intent and determines whether it is an action-driven project (no theme needed) or an intellectual research project.
2. Scans your **Life Areas** in `3-Domaines-de-vie/`:
   - If an existing area matches, it proposes linking to it.
   - If your project introduces a new aspect of your life (e.g., `Home`, `Health`, `Finance`), it offers to **automatically create this new Life Area** and register it in the index.
3. If relevant, it links or creates matching MOC knowledge Themes.
4. Upon your confirmation in chat, your project note `P-[Name].md` is ready with milestones for your first `arca-resume`!

---

## 📊 Fourth Experiment: Discover Your Visual Cockpit (`Home.md`)

Once your first notes and projects are in place, Arca-BrainOS offers a centralized executive dashboard: [`Home.md`](Home.md). It displays an active overview of your current projects, weekly focus, and recent knowledge syntheses.

To enable the dynamic dashboard widgets via the community plugin **Dataview** (optional but highly recommended):

1. In Obsidian, open **Settings** (gear icon in the bottom-left corner) $\rightarrow$ **Community plugins**.
2. Click **Browse**, search for **Dataview**, click **Install**, and then **Enable**.
3. In the Dataview options, ensure these two settings are turned ON:
   - ✅ **Enable JavaScript Queries** (`dataviewjs`)
   - ✅ **Enable Inline JavaScript Queries**
4. Open [`Home.md`](Home.md): your dynamic dashboard and focus gauges will now render automatically with your live projects and notes!

---

## 🗺️ Understanding the Vault Structure (PARA Method)

The vault follows the **PARA** method adapted for AI orchestration:

- **`0-Inbox/`**: Single entry point for all raw captures, fleeting thoughts, and web clips.
- **`1-Projects/`**: Active ongoing projects with milestones and target outcomes (`P-[Name].md`).
- **`2-Ressources/`**: Long-term knowledge base, split into 3 clear layers:
  - `Notes/`: Human-authored thoughts and writing.
  - `Themes/`: MOC topic index cards (`T-[Topic].md`).
  - `IA-generated/`: Isolated sandbox where AI stores conceptual distillations (`AI-Distil-...`).
- **`3-Domaines-de-vie/`**: Ongoing areas of responsibility (Health, Career, Creativity...).
- **`4-Archives/`**: Cold storage for completed projects.
- **`_Arca-BrainOS/`**: The portable agentic engine (modular `skills/`, methodology `process/`, and note `templates/`).

---

## 💬 Questions or Need a Hand?

Arca-BrainOS is an open, collaborative project. If you hit any road bumps during setup, have ideas for improvements, or want to share your first use cases:

- Open a discussion or an issue on the GitHub repository: **[github.com/Arca-Brain/Arca-BrainOS/issues](https://github.com/Arca-Brain/Arca-BrainOS/issues)**
- To explore the philosophical vision, read the **[Arca-BrainOS Manifesto](../../MANIFESTO.md)**.
- Official GitHub Repository: **[github.com/Arca-Brain/Arca-BrainOS](https://github.com/Arca-Brain/Arca-BrainOS)**
