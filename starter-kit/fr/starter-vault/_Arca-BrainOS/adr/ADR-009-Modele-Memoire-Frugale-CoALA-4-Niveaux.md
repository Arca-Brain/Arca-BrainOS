---
date: "2026-09-10"
title: "ADR-009 : Modèle de Mémoire Frugale CoALA à 4 Niveaux (_Arca-BrainOS/memory.md)"
status: "accepted"
tags:
  - adr
  - architecture
  - arca-brainos
  - retroactif-v1
target: "[[P-Arca-BrainOS]]"
---

# 📜 ADR-009 : Modèle de Mémoire Frugale CoALA à 4 Niveaux (_Arca-BrainOS/memory.md)

> *Statut : Rétro-documenté pour la version v1.0.0 d'Arca-BrainOS.*

---

## 1. Contexte & Problématique
La gestion de la mémoire est le défi central des systèmes agentiques. Deux approches naïves échouent régulièrement :
- **L'amnésie totale :** L'agent redémarre de zéro à chaque session, obligeant l'utilisateur à répéter inlassablement ses préférences stylistiques et ses conventions techniques.
- **La saturation dynamique (Bases vectorielles type MemGPT) :** Injecter l'historique complet des conversations dans une base vectorielle surcharge le contexte de jetons inutiles, engendre des hallucinations et transforme la mémoire en une boîte noire incontrôlable.

---

## 2. Décision Retenue
Il est acté d'implémenter une **architecture de mémoire étagée en 4 strates transparentes**, inspirée du framework CoALA (*Cognitive Architectures for Language Agents*) et adaptée au texte brut Obsidian :

1. **Mémoire Procédurale (Les Savoir-Faire) :**
   - Codifiée dans la constitution universelle [[AGENTS.md]], les compétences exécutables (`_Arca-BrainOS/skills/`) et les fiches de méthodes (`_Arca-BrainOS/process/`).
2. **Mémoire Épisodique (L'Histoire Vécue) :**
   - Consignée de façon indélébile dans les journaux de bord chronologiques de chaque projet `1-Projects/[P-Nom].md` et dans le registre d'audit `_Arca-BrainOS/log.md`.
3. **Mémoire Sémantique (Le Savoir du Monde) :**
   - Structurée dans le graphe de connaissances, les Cartes de Contenu MOCs (`2-Ressources/Themes/T-*.md`) et les distillations conceptuelles (`2-Ressources/IA-generated/AI-Distil-*.md`).
4. **Mémoire de Travail Court/Moyen Terme (`_Arca-BrainOS/memory.md`) :**
   - Fichier texte frugal agissant comme le buffer d'apprentissage immédiat de l'agent.
   - **Règle d'or frugale :** Plafond strict fixé entre 40 et 50 lignes au total.
   - N'accueille que les préférences stylistiques et habitudes techniques ayant fait l'objet d'un arbitrage formel de l'utilisateur, soumises à un élagage périodique.

---

## 3. Conséquences & Compromis
- **Bénéfices immédiats :**
  - Zéro dérive contextuelle : l'agent intègre instantanément les préférences sans saturer sa fenêtre de contexte.
  - Transparence totale : l'utilisateur peut inspecter et corriger `memory.md` directement dans son éditeur.
  - Coût d'inférence minimal : aucune dépendance envers un service d'embedding ou une base vectorielle payante.
- **Compromis & Contraintes assumés :**
  - Exige une discipline d'élagage régulier pour ne pas dépasser le seuil des 50 lignes.

---

## 4. Alternatives Écartées
- **Base de données vectorielle dynamique de souvenirs :** Rejetée pour son opacité, son coût en tokens et son instabilité.
- **Inscrire les préférences directement dans `AGENTS.md` :** Rejeté car `AGENTS.md` est la constitution immuable du coffre et ne doit pas subir d'écritures quotidiennes volatiles.

---

## 5. Références & Liens
- Projet Maître : [[1-Projects/P-Arca-BrainOS|P-Arca-BrainOS]]
- Note de Conception : [[0-Inbox/Brainstorm-Framework-CoALA-et-Amelioration-Memoire-Arca-BrainOS|Brainstorm CoALA & 4 Mémoires]]
- Fichier Système : [[_Arca-BrainOS/memory.md|Mémoire Opérationnelle Frugale]]
