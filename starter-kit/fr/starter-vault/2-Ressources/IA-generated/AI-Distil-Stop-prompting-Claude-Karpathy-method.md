---
date_created: 2026-06-21
title: "La méthode Karpathy pour Claude : Spécification, Scratchpad et Boucle de Feedback"
description: "Dépassement du prompting traditionnel au profit d'un framework d'ingénierie système en 3 couches (Spec, Scratchpad, Feedback) inspiré d'Andrej Karpathy."
tags:
  - ai-generated
  - theme/intelligence-artificielle
  - theme/pkm
status: "#reviewed"
---

# 🧪 Synthèse IA : La méthode Karpathy pour Claude (Spec, Scratchpad, Feedback)

## ⚡ Résumé Synthétique
Austin Marchese propose de rejeter le prompting jetable traditionnel, qui traite l'IA comme un moteur de recherche, pour adopter une approche d'ingénierie système inspirée d'Andrej Karpathy. Ce framework en trois couches repose sur : la co-conception d'une Spécification (Spec) agile et découpée, l'usage d'un Scratchpad (fichier de brouillon persistant) pour maintenir le contexte et le raisonnement de l'IA sans surcharger sa fenêtre de contexte, et l'intégration d'une Boucle de Feedback où chaque correction amende directement un « LLM Wiki » (base de règles de développement). Ce système structure la collaboration avec l'IA comme un processus logiciel rigoureux et améliore l'autonomie de l'agent en continu.

## 🔑 Le Noyau

- **Idées Clés :**
  - L'entendement ne s'externalise pas (« understanding cannot be outsourced ») : la conception intellectuelle reste la prérogative de l'humain tandis que l'IA assure l'exécution.
  - Le prompting classique échoue sur les tâches complexes car il oblige l'IA à deviner les besoins implicites de l'utilisateur au lieu de s'appuyer sur un cahier des charges rigoureux.
  - Corriger l'IA de manière isolée dans une session de chat est inefficace ; chaque correction doit modifier la structure ou la base de règles du projet pour pérenniser la correction.
  - La clarté de la spécification initiale est le facteur le plus déterminant pour la qualité de la production de l'IA.

- **Convictions & Principes :**
  - Il faut cesser de chercher le prompt parfait et commencer à construire une architecture de projet qui garantit structurellement de bons résultats.
  - Diviser le travail en confiant l'exécution à un agent principal et l'audit à un agent secondaire améliore drastiquement la fiabilité du livrable.

- **Modèles Conceptuels :**
  - **Framework Karpathy en 3 couches :**
    - *Couche 1 : La Spécification (Spec)* : Définition rigoureuse de la tâche, découpée en blocs de tâches agiles et indépendants dotés de critères d'acceptation explicites. Rédigée après que l'IA a interviewé l'utilisateur.
    - *Couche 2 : Le Scratchpad (Mémoire de travail)* : Espace temporaire et persistant (fichier Markdown ou brouillon) où l'IA suit son plan d'action, valide ses hypothèses et audite ses propres résultats avant soumission.
    - *Couche 3 : La Boucle de Feedback & l'Environnement* : Écosystème d'outils comprenant les tests automatisés et un « LLM Wiki » (standards de code, conventions, règles métier). Les erreurs corrigées sont intégrées à ce wiki pour empêcher leur réapparition.
  - **Entretien de Contexte (Spec Interviewing) :** Processus interactif préalable où le LLM interroge l'utilisateur sur sa vision et ses contraintes afin de co-rédiger la spécification de départ.

- **Stratégies Opérationnelles :**
  - Rédiger systématiquement une spécification claire et validée par jalons avant de démarrer des développements complexes.
  - Créer et maintenir un fichier Scratchpad persistant dans l'arborescence du projet pour préserver l'état d'avancement entre les sessions de travail.
  - Établir un « LLM Wiki » (`AGENTS.md`) décrivant les préférences stylistiques et les normes techniques du projet pour y guider l'IA de manière persistante.
  - Associer l'IA à des tests unitaires locaux automatisés pour lui offrir une boucle de feedback technique immédiate (`arca-test`).

## 🛠️ Application & Impact
- [[P-Projet-IA-Souveraine]] : Application de la Boucle de Feedback de Karpathy pour stabiliser l'OS (mise à jour systématique de `AGENTS.md` après chaque ajustement).

## 📜 Source & Ingestion Brute
- [[Stop-prompting-Claude-Karpathy-method]] : Transcript brut de la vidéo d'origine.

## 🕸️ Connexions Suggérées
- [[T-Intelligence-Artificielle]]
- [[T-PKM]]
