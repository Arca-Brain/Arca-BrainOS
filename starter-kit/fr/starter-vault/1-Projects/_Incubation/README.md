# 🌱 Dossier d'Incubation des Projets (Someday / Maybe)

Ce dossier accueille les chantiers, idées structurées et projets en sommeil qui ne sont pas actuellement engagés dans votre cycle actif de Deep Work.

---

## 🎯 Philosophie & Règle d'Or GTD
- **Zéro charge mentale :** Ne conservez à la racine de `1-Projects/` que les chantiers sur lesquels vous avancez activement (ou bloqués temporairement).
- **Projet vs Simple Graine :** 
  - Une simple idée ou intuition en une ligne reste une puce dans la section `## 🌱 Idées Futurs (Backlog)` de son Domaine de vie (`3-Domaines-de-vie/`).
  - Une note `P-[Nom-Projet].md` dans ce dossier `_Incubation/` est justifiée dès lors que le projet commence à avoir une spécification, des liens ou des documents de travail (`Working Documents`).

---

## 🏷️ Frontmatter Standard d'un Projet Incubé
```yaml
---
id: "YYYYMMDDHHmm"
category: "Projet"
status: "someday" # Marqueur clé d'incubation
date_created: "AAAA-MM-JJ"
tags:
  - projet
  - statut/someday
areas:
  - "[[Nom-Du-Domaine]]" # Obligatoire : raccordement au Domaine de vie
themes:
  - "[[T-Nom-Theme]]"   # Optionnel : adossé à un thème MOC
last_session: ""
sessions_count: 0
total_real_duration: "0h00"
total_estimated_manual: "0h00"
total_time_saved: "0h00"
---
```

---

## 🚀 Transition vers l'Actif (Réveil de Projet)
Pour activer un projet incubé :
1. Déplacez le fichier Markdown depuis `1-Projects/_Incubation/` vers la racine de `1-Projects/`.
2. Modifiez le frontmatter :
   - `status: "active"`
   - Remplacez le tag `statut/someday` par `statut/actif`.
3. Lancez la première session de travail avec `arca-resume [[P-Nom-Projet]]`.
