---
date: "2026-08-09"
title: "ADR-007 : Dichotomie des Projets (Recherche Intellectuelle vs Monde Réel)"
status: "accepted"
tags:
  - adr
  - architecture
  - arca-brainos
  - retroactif-v1
target: "[[P-Arca-BrainOS]]"
---

# 📜 ADR-007 : Dichotomie des Projets (Recherche Intellectuelle vs Monde Réel)

> *Statut : Rétro-documenté pour la version v1.0.0 d'Arca-BrainOS.*

---

## 1. Contexte & Problématique
Les frameworks PKM académiques (Zettelkasten, systèmes MOC purs) sont conçus presque exclusivement pour des chercheurs, des étudiants ou des créateurs de contenu manipulant des abstractions intellectuelles.
Or, la vie réelle d'un utilisateur d'Arca-BrainOS comporte deux dimensions indissociables :
- Des projets intellectuels et digitaux (architecture logicielle, veille IA, écriture de livres, stratégie produit).
- Des projets pragmatiques et physiques dans le monde réel (chantier de rénovation, rééducation médicale, organisation d'un trek ou voyage, gestion administrative).

Forcer un projet concret (ex : rééducation de cheville ou travaux dans une maison) à se relier artificiellement à des fiches de "Thèmes MOC" génère une surcharge cognitive inutile et décrédibilise le Second Cerveau.

---

## 2. Décision Retenue
Il est acté de formaliser dans `Skill_arca-create-note` une **dichotomie explicite de qualification des projets** :

1. **Les Projets de Recherche / Intellectuels :**
   - Vocation conceptuelle : ils s'adossent à des fiches thématiques de connaissances.
   - Modèle YAML : déclarent à la fois leur Domaine de responsabilité (`areas: ["[[Travail]]"]`) et un ou plusieurs Thèmes MOC (`themes: ["[[T-PKM]]", "[[T-Intelligence-Artificielle]]"]`).
2. **Les Projets Pratiques / Monde Réel :**
   - Vocation opérationnelle pure : ils visent un accomplissement physique concret.
   - Modèle YAML : rattachés obligatoirement à leur Domaine de vie (`areas: ["[[Sante]]"]`), mais avec une liste de thèmes explicitement vide (`themes: []`).
3. **Égalité de Traitement dans le Système :**
   - Les deux archétypes bénéficient exactement de la même rigueur de pilotage : gabarit `P-[Nom].md`, suivi d'objectifs, décompte de temps, cockpit `Home.md` et sessions de Deep Work.

---

## 3. Conséquences & Compromis
- **Bénéfices immédiats :**
  - Fin de l'artifice : l'utilisateur ne crée plus de thèmes forcés ou bidons pour piloter sa vie pratique.
  - Clarté holistique : les Domaines de vie (`3-Domaines-de-vie/`) englobent l'ensemble des énergies de l'utilisateur (intellectuelles et physiques).
  - Adoption naturelle : le Second Cerveau devient l'outil central de toute la vie, et pas seulement du travail numérique.
- **Compromis & Contraintes assumés :**
  - Les requêtes et scripts doivent gérer gracieusement les projets ayant `themes: []`.

---

## 4. Alternatives Écartées
- **Séparer la vie professionnelle et la vie personnelle dans deux coffres distincts :** Rejeté car cela fragmente la vision d'ensemble et empêche les bilans de vie harmonieux.
- **Obligation de thèmes pour tous les projets :** Rejetée car elle crée une friction de saisie absurde sur les projets du quotidien.

---

## 5. Références & Liens
- Projet Maître : [[1-Projects/P-Arca-BrainOS|P-Arca-BrainOS]]
- Exemple Terrain Concret : [[1-Projects/P-Reeducation-Marche-Vision-Oviedo|Projet Rééducation Marche & Vision]]
- Compétence Dédiée : [[_Arca-BrainOS/skills/Skill_arca-create-note|Skill_arca-create-note]]
