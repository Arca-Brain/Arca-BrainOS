---
id: "{{date:YYYYMMDD}}{{time:HHmm}}"
category: "Area"
status: "active"
date_created: "{{date:YYYY-MM-DD}}"
tags:
  - area
  - para
quality_standard: ""
last_review: "{{date:YYYY-MM-DD}}"
banner: ""
---

# 🧠 Life Area : {{title}}

---
### 📅 {{date:YYYY}}
- **🎯 Yearly Focus :** [Main intention or priority focus for the year]
- **🏁 Projects & Initiatives :**
  - [[P-Project-Name]] : [Short description]

---
### 🟢 Active Projects
```dataview
TABLE last_session AS "Last Run", sessions_count AS "Sessions", total_time_saved AS "AI Time Saved"
FROM "1-Projects"
WHERE contains(areas, this.file.link) OR contains(file.outlinks, this.file.link)
SORT date(last_session) DESC
```

---
## 🌱 Backlog & Future Ideas
- 💡 **[Category] :** [[Link-or-Name]] : [Short description]

---
## 🎯 Scope & Quality Standard
> [!abstract] **Scope :** [What is covered by this life area]
> **Quality Standard :** [Minimal standard of excellence to maintain]

---
## 📚 References & MOCs
- **🧠 Themes & MOC Cards :** [[T-Theme-Name|🧠 Theme MOC]]
- **📖 Guides & Methods :** [[Guide-or-Note|📖 Guide]]

---
### 📦 Archived & Completed Projects
```dataview
TABLE date_created AS "Created At", last_session AS "Completed At", total_time_saved AS "Total Time Saved"
FROM "4-Archives/Projets"
WHERE contains(areas, this.file.link) OR contains(file.outlinks, this.file.link)
SORT date(last_session) DESC
```
