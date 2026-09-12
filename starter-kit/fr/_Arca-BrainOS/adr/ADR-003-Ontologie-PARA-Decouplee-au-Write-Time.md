---
date: "2026-08-09"
title: "ADR-003 : Ontologie PARA Découplée au Write-Time vs Dossiers Hiérarchiques Rigides"
status: "accepted"
tags:
  - adr
  - architecture
  - arca-brainos
  - retroactif-v1
target: "[[P-Arca-BrainOS]]"
---

# 📜 ADR-003 : Ontologie PARA Découplée au Write-Time vs Dossiers Hiérarchiques Rigides

> *Statut : Rétro-documenté pour la version v1.0.0 d'Arca-BrainOS.*

---

## 1. Contexte & Problématique
La méthode PARA classique (Tiago Forte) organise les connaissances en 4 répertoires physiques stricts : *Projects, Areas, Resources, Archives*.
Dans la pratique quotidienne d'un Second Cerveau augmenté par l'IA, ce modèle présente des faiblesses structurelles majeures :
- **L'hésitation permanente de classement :** Une note technique est-elle une ressource ou fait-elle partie d'un projet ? L'utilisateur s'épuise à ranger au lieu de produire.
- **La rupture de contexte :** Déplacer un dossier de projet vers les archives brise l'accès aux connaissances qui y ont été produites.
- **L'échec du RAG naïf :** Découper des notes rangées en vrac dans des sous-dossiers pour les indexer dans une base vectorielle produit des hallucinations et des réponses imprécises, car les modèles ne perçoivent pas la hiérarchie implicite des répertoires.

---

## 2. Décision Retenue
Il est acté de remplacer la hiérarchie de dossiers fermée par une **ontologie relationnelle qualifiée à l'écriture (Write-Time Ontology)**, tout en conservant les 5 conteneurs de cycle de vie PARA :

1. **Les Dossiers comme Simples Sas de Cycle de Vie :**
   - Les répertoires (`0-Inbox/`, `1-Projects/`, `2-Ressources/`, `3-Domaines-de-vie/`, `4-Archives/`) ne servent qu'à indiquer la maturité et le statut opérationnel d'un document, jamais son thème intellectuel.
2. **Typage Fort des Entités par Préfixes Canoniques :**
   - `P-[Nom]` : Projet actif orienté vers un livrable daté.
   - `T-[Nom]` : Thème MOC (Map of Content), carte conceptuelle agissant comme carrefour sémantique.
   - `[Domaine]` : Domaine de vie (Area de responsabilité pérenne sans date de fin).
3. **Maillage Déterministe au Write-Time :**
   - Chaque projet `P-` déclare obligatoirement dans son frontmatter son Domaine (`areas: ["[[Travail]]"]`) et ses Thèmes de rattachement (`themes: ["[[T-PKM]]"]`).
   - L'IA et l'utilisateur tissent des wikilinks bidirectionnels explicites (`[[...]]`) dès la création des notes. Le graphe de connaissances est déterministe et autosuffisant, rendant obsolète le besoin d'un RAG vectoriel probabiliste.

---

## 3. Conséquences & Compromis
- **Bénéfices immédiats :**
  - Fin de la friction de rangement : une note peut appartenir simultanément à plusieurs thèmes sans duplication de fichier.
  - Précision maximale pour l'IA : en ouvrant une note, l'agent dispose immédiatement du contexte global grâce aux liens déclarés.
  - Pérennité des archives : archiver un projet consiste à déplacer un seul fichier dans `4-Archives/Projets/`, sans briser aucun lien sémantique avec les thèmes.
- **Compromis & Contraintes assumés :**
  - Rigueur obligatoire dans le maintien des métadonnées frontmatter YAML (`areas`, `themes`, `tags`).

---

## 4. Alternatives Écartées
- **PARA pur à sous-dossiers rigides :** Rejeté car il enferme la pensée en silos et force l'utilisateur à naviguer dans une arborescence profonde.
- **RAG sémantique aveugle (Vector Database sans ontologie) :** Rejeté car il traite toutes les notes comme des fragments de texte indifférenciés sans comprendre les liens hiérarchiques et opérationnels.

---

## 5. Références & Liens
- Projet Maître : [[1-Projects/P-Arca-BrainOS|P-Arca-BrainOS]]
- Note de Distillation Clé : [[2-Ressources/IA-generated/AI-Distil-Pourquoi-vous-devez-maitriser-l-ontologie|Jonas Roman : Ontologie Write-Time vs RAG naïf]]
- Modèle de Création : [[_Arca-BrainOS/skills/Skill_arca-create-note|Skill_arca-create-note]]
