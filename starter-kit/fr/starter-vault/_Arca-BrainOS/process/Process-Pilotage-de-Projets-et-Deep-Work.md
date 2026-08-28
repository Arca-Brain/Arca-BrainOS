---
id: "202607172325"
category: Process
date_created: "2026-07-17"
tags:
  - process
  - projet
  - deepwork
  - ia
---
# Process : Pilotage de Projets & Deep Work

- **Fréquence** : On Trigger (Au démarrage et à la clôture de chaque session Deep Work).
- **Déclencheur** : Décision d'ouvrir une session de travail sur un projet actif `P-[Nom]`.

---
## Input
* Note du projet cible `P-[Nom-Projet]` située dans `1-Projects/`.
* Notes de travail associées (`Working Documents`) référencées dans le projet.
* Journal de bord des sessions antérieures (`## 🪵 Journal de Bord des Sessions`).

## Étapes
1. **Démarrer & Cadrer la session** : Taper la commande `arca-resume @[Projet]` pour scanner l'état du projet, recevoir la proposition d'intention, **enregistrer l'horodate d'ouverture (HH:mm)** et initier le bloc de session dans le journal de bord.
2. **Clarifier l'intention** : Aligner l'IA sur l'objectif précis du jour en répondant au briefing interactif.
3. **Exécuter le travail (Deep Work)** : Produire les écrits, le code ou la méthode en pair-programming avec l'agent IA.
4. **Clôturer la session** : Taper la commande `arca-close-session @[Projet]` pour trier les tâches accomplies/restantes, enregistrer l'horodate de clôture, **calculer la durée réelle vs le temps estimé sans IA**, finaliser le journal de bord et mettre à jour les métadonnées cumulées du projet (`total_real_duration`, `total_estimated_manual`, `total_time_saved`).

## Méthode & Critères de Qualité
* **Structure requise** : Le projet `P-` doit conserver son plan strict (Working Docs, Actions Next, Jalons, Journal de bord) ainsi que ses métadonnées frontmatter de suivi de durée.
* **À faire absolument (DO)** :
  * Consigner systématiquement les verrous techniques, l'horodatage et les prochaines étapes précises en fin de session.
  * Préserver le texte original rédigé par l'humain dans les notes projets `P-` et leçons `L-`.
* **À éviter absolument (DON'T)** :
  * Ne pas démarrer une session sans intention claire.
  * Ne pas quitter un run sans fermer la session via `arca-close-session`.

## Output
* Briefing de cadrage validé en début de session + bloc de session initialisé avec l'heure d'ouverture.
* Tâches accomplies et cochées (`[x]`) dans la note projet `P-`.
* Bilan complet de session consigné dans le journal de bord et métadonnées YAML du projet à jour.

## Exemples
* Session de Deep Work sur `[[P-Cartographie-Processus-Persos-et-IA]]` ou `[[P-Arca-BrainOS]]`.

## Douleurs principales
* Oublier où l'on s'était arrêté lors de la dernière session de travail.
* Procrastination de démarrage par manque d'intention claire.
* Projets qui meurent ou stagnent faute d'évaluation réaliste du temps investi.

---

## Intégration IA & Répartition Humain/Machine

| Étape | Levier | Solution Technique (Skill / n8n) | Rôle Humain & Arbitrage | Statut |
| :--- | :--- | :--- | :--- | :--- |
| **1. Cadrage & Ré-immersion** | **Agent IA** | Commande `arca-resume` (Scanne le projet, horodate l'ouverture HH:mm & initie la session dans le journal). | **Intention** : Confirmer ou ajuster le focus proposé par l'IA. | 🟢 (Opérationnel) |
| **2. Exécution du travail** | **Agent + Humain** | Pair-programming, génération d'écrits assistée. | **Créativité & Jugement** : Décisions stratégiques et rédaction. | 🟢 (Opérationnel) |
| **3. Clôture & Journalisation** | **Agent IA** | Commande `arca-close-session` (Horodate de fin, calcul durée/ROI sans IA, mise à jour tâches & YAML cumulé). | **Validation** : Vérifier l'exactitude du bilan rédigé. | 🟢 (Opérationnel) |

### 🧠 Part d'Arbitrage Humain & Gaps IA (Les ~20% restants)
* **Discipline de déclenchement** : L'humain doit penser à lancer `arca-resume` pour cadrer et horodater la session, et exécuter `arca-close-session` à la clôture.
* **Choix du projet et de l'instant de travail** : L'IA n'initie pas les sessions de travail.
* **Garantie de souveraineté des contenus** : L'IA ne réécrit pas la vision humaine dans les notes `P-`.

**Pipeline complet** : `arca-resume` (Cadrage Agent) ➔ Clarification Intention (Humain) ➔ Session Deep Work (Co-création) ➔ `arca-close-session` (Clôture & Log).
