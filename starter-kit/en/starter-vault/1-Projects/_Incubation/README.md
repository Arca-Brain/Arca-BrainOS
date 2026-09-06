# 🌱 Project Incubation Folder (Someday / Maybe)

This folder hosts dormant projects, structured ideas, and backlogs that are not currently committed to your active Deep Work cycle.

---

## 🎯 Philosophy & GTD Golden Rule
- **Zero Mental Friction:** Keep only projects you are actively moving forward (or temporarily blocked) at the root of `1-Projects/`.
- **Project vs Raw Seed:**
  - A single-line idea or intuition remains a bullet in the `## 🌱 Backlog & Future Ideas` section of its corresponding Life Area.
  - A `P-[Project-Name].md` file in this `_Incubation/` folder is justified as soon as the project starts having specifications, links, or Working Documents.

---

## 🏷️ Standard Frontmatter for an Incubating Project
```yaml
---
id: "YYYYMMDDHHmm"
category: "Project"
status: "someday" # Key incubation flag
date_created: "YYYY-MM-DD"
tags:
  - project
  - status/someday
areas:
  - "[[Area-Name]]" # Mandatory: linked to a Life Area
themes:
  - "[[T-Theme-Name]]" # Optional: backed by an MOC theme
last_session: ""
sessions_count: 0
total_real_duration: "0h00"
total_estimated_manual: "0h00"
total_time_saved: "0h00"
---
```

---

## 🚀 Transition to Active (Waking Up a Project)
To activate an incubating project:
1. Move the Markdown file from `1-Projects/_Incubation/` to the root of `1-Projects/`.
2. Update the frontmatter:
   - `status: "active"`
   - Replace tag `status/someday` with `status/active`.
3. Launch your first Deep Work session with `arca-resume [[P-Project-Name]]`.
