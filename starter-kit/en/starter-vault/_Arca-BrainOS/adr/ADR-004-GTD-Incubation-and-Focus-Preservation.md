---
date: "2026-08-09"
title: "ADR-004 : GTD Incubation (1-Projects/_Incubation/) and Active Focus Preservation"
status: "accepted"
tags:
  - adr
  - architecture
  - arca-brainos
  - retroactive-v1
target: "[[P-Sovereign-AI-Project]]"
---

# 📜 ADR-004 : GTD Incubation (1-Projects/_Incubation/) and Active Focus Preservation

> *Status: Retro-documented for Arca-BrainOS v1.0.0 release.*

---

## 1. Context & Problem Statement
Knowledge workers easily accumulate dormant or exploratory projects. When dormant ideas mix directly with active commitments in `1-Projects/`, cognitive overload occurs and dashboard views (`Home.md`) become cluttered.

---

## 2. Decision
Arca-BrainOS establishes a **formal GTD incubation airlock**:

1. **Dedicated Directory:** `1-Projects/_Incubation/` holds projects in incubation (`status: someday` or `status: incubating`).
2. **Active Focus Protection:** The active root `1-Projects/` is strictly reserved for current, committed projects (`status: active`).
3. **Automated Promotion/Demotion:** Managed through `arca-create-note` and session reviews.

---

## 3. Consequences & Trade-offs
- **Immediate Benefits:**
  - Crystal-clear daily focus on current active projects.
  - Zero guilt about capturing exploratory ideas without polluting active dashboards.
- **Accepted Trade-offs & Constraints:**
  - Extra folder path to configure (`PATH_INCUBATION`).

---

## 4. Alternatives Considered
- **Tagging projects `#someday` inside active folder:** Rejected because physical clutter in file explorer persists.
- **Keeping ideas as loose Inbox notes:** Rejected because incubating projects need structured templates, milestones, and links.

---

## 5. References & Links
- Core Project: [[P-Sovereign-AI-Project]]
