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

# 🧠 Domaine de vie : {{title}}

---
### 📅 {{date:YYYY}}
- **🎯 Focus de l'année :** [Intention ou axe prioritaire de l'année pour cet Area]
- **🏁 Projets & chantiers de l'année :**
  - [[P-Nom-Projet]] : [Description rapide]

---
### 🟢 Projets Actifs
```dataview
TABLE last_session AS "Dernier Run", sessions_count AS "Sessions", total_time_saved AS "Gain IA"
FROM "1-Projects"
WHERE contains(areas, this.file.link) OR contains(file.outlinks, this.file.link)
SORT date(last_session) DESC
```

---
## 🌱 Idées Futurs (Backlog)
*Les graines de projets, intuitions et chantiers en incubation.*
- 💡 **[Catégorie] :** [[Lien-ou-Nom]] : [Description courte]

---
## 📅 Agenda Saisonnier
- ❄️ **Hiver (Nov / Mars) :** [Routines & chantiers récurrents d'hiver]
- 🌸 **Printemps (Avr / Juin) :** [Routines & chantiers récurrents de printemps]
- ☀️ **Été (Juil / Sept) :** [Routines & chantiers récurrents d'été]
- 🍂 **Automne (Oct / Déc) :** [Routines & chantiers récurrents d'automne]

---
## 🎯 Périmètre & Standard d'Exigence
> [!abstract] **Périmètre :** [Ce qui est couvert par ce domaine de vie]
> **Standard Visé :** [Niveau d'exigence minimal à maintenir au quotidien]

---
## 📚 Références & MOCs Thématiques
- **🧠 Thèmes & Cartes MOC :** [[T-Nom-Theme|🧠 MOC Thème]]
- **📖 Guides & Méthodes :** [[Guide-ou-Note|📖 Guide]]

---
### 📦 Projets Archivés & Terminés
```dataview
TABLE date_created AS "Créé le", last_session AS "Terminé le", total_time_saved AS "Gain IA Total"
FROM "4-Archives/Projets"
WHERE contains(areas, this.file.link) OR contains(file.outlinks, this.file.link)
SORT date(last_session) DESC
```

---
## 🪵 Journal & Bilan Historique de Responsabilité

### 📅 Historique des Années Précédentes
- **2025 :** [[Note-ou-Projet-2025]]
