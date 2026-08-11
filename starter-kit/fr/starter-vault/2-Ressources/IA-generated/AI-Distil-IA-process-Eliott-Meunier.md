---
date_created: 2026-07-16
title: "L'IA par les processus : méthode CMA et fiches process"
description: "Déléguer à l'IA en formalisant le savoir tacite sous forme de fiches process et en distinguant agents supervisés et automatisations."
tags:
  - ai-generated
  - theme/intelligence-artificielle
  - theme/pkm
  - theme/workflow
status: "#reviewed"
---

# 🧪 Synthèse IA : L'IA par les processus (Méthode CMA & Fiches Process)

## ⚡ Résumé Synthétique
L'utilisation de l'IA au coup par coup (mode conversationnel) est inefficace pour réaliser de réels gains de productivité. Pour rentabiliser l'IA, il faut adopter une approche axée sur les processus (Process-Driven) en explicitant son savoir tacite via la méthode CMA (Clarifier, Mapper, Amplifier). En cartographiant les tâches quotidiennes selon leur trigger (Daily, Weekly, Monthly, On Trigger, Manuel) et en utilisant une fiche process standardisée (Inputs, Étapes, Méthode, Outputs), il devient possible d'intégrer l'IA de manière structurée : soit sous forme d'agents supervisés par l'humain pour les tâches de jugement et créatives, soit sous forme d'automatisations pures (comme n8n) pour les tâches répétitives sans valeur ajoutée.

## 🔑 Le Noyau

- **Idées Clés :**
  - L'échec des projets d'intégration de l'IA (80% d'échecs) provient du manque de structure et de l'absence de documentation préalable des processus.
  - Le gain de temps réel ne s'obtient pas par du prompting ad-hoc ("chat standard"), mais par une approche systématique et reproductible.
  - La méthode de travail est plus importante que le modèle d'IA utilisé : la qualité des résultats dépend de la méthode d'excellence injectée dans la fiche process.
  - La formalisation du savoir tacite (règles inconscientes) en savoir explicite permet de déléguer l'exécution à bas coût à une IA ou à un tiers humain.

- **Convictions & Principes :**
  - L'IA n'a pas de critères de qualité innés ; c'est à l'humain de concevoir et documenter une méthode d'excellence pour guider l'IA.
  - L'optimisation réaliste et très rentable consiste à améliorer chaque processus existant de 30% plutôt que d'espérer un remplacement total par l'IA.

- **Modèles Conceptuels :**
  - **Méthode CMA** :
    - **Clarifier** : Documenter son identité et son contexte.
    - **Mapper** : Cartographier ses processus et localiser les points d'intervention de l'IA.
    - **Amplifier** : Construire les agents et automatisations.
  - **Matrice des Triggers** : Classification des processus selon leur déclencheur pour déterminer le ROI d'automatisation.
  - **Arbre de décision Agent vs Automatisation** :
    - *Agent* : S'active sur commande, assiste l'humain dans des tâches nécessitant un jugement, de l'intuition ou de la créativité.
    - *Automatisation* : S'exécute seule en arrière-plan pour des tâches répétitives, déterministes, sans besoin de validation humaine.

- **Stratégies Opérationnelles :**
  - Rédiger des fiches de processus standardisées contenant les sections : Inputs, Étapes, Méthode & Critères de Qualité, Outputs.
  - Segmenter les tâches complexes en sous-étapes pour attribuer chaque étape à un agent IA ou à une automatisation.
  - Remplacer les heures passées à trier ses notes volantes par un agent de tri automatique (`arca-inbox-process`) qui comprend le sujet et classe la note dans le bon dossier.

## 🛠️ Application & Impact
- [[P-Projet-IA-Souveraine]] : Référence vers la Méthode CMA & Fiches Processus.

## 📜 Source & Ingestion Brute
- [[Elliot Meunier - utiliser IA avec template process]] : Transcript brut de la vidéo d'origine.

## 🕸️ Connexions Suggérées
- [[T-Intelligence-Artificielle]]
- [[T-PKM]]
