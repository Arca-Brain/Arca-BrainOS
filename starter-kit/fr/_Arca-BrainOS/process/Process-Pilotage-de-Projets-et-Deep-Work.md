---
Id: "202607172325"
category: Process
date-created: "2026-07-17"
tags:
  - process
  - projet
  - deepwork
  - ia
---
# Process : Pilotage de Projets & Deep Work

- **Fréquence** : On Trigger (Au démarrage et à la clôture de chaque session Deep Work).
- **Déclencheur** : Décision d'ouvrir une session de travail sur un projet actif `P-[Nom]`.
- **Temps actuel** : ~15 à 30 min par session (perte de temps à ré-immerger son esprit du contexte et actions faites, hésitation sur les priorités, absence de compte-rendu).

---
## Input
* Note du projet cible `P-[Nom-Projet]` située dans `1-Projects/`.
* Notes de travail associées (`Working Documents`) référencées dans le projet.
* Journal de bord des sessions antérieures (`## 🪵 Journal de Bord des Sessions`).

## Étapes
1. **Démarrer & Cadrer la session** : Taper la commande `arca-resume @[Projet]` pour scanner l'état du projet, recevoir la proposition d'intention, **enregistrer l'horodate d'ouverture (HH:mm)** et initier le bloc de session dans le journal de bord.
2. **Clarifier l'intention** : Aligner l'IA sur l'objectif précis du jour en répondant au briefing interactif.
3. **Exécuter le travail (Deep Work)** : Produire les écrits, le code ou la méthode en pair-programming avec l'agent IA.
4. **Clôturer la session** : Taper la commande `arca-close-session @[Projet]` pour trier les tâches accomplies/restantes, enregistrer l'horodate de clôture, **calculer la durée réelle vs le temps estimé sans IA**, finaliser le journal de bord et mettre à jour les métadonnées cumulées du projet.

## Méthode & Critères de Qualité
* **Structure requise** : Le projet `P-` doit conserver son plan strict (Working Docs, Actions Next, Jalons, Journal de bord) ainsi que ses métadonnées frontmatter de suivi de durée.
* **À faire absolument (DO)** :
  * Consigner systématiquement les verrous techniques, l'horodatage et les prochaines étapes précises en fin de session.
  * Preserver le texte original rédigé par l'humain dans les notes projets `P-` et leçons `L-`.
* **À éviter absolument (DON'T)** :
  * Ne pas démarrer une session sans intention claire.
  * Ne pas quitter un run sans fermer la session via `arca-close-session`.

## Output
* Briefing de cadrage validé en début de session + bloc de session initialisé avec l'heure d'ouverture.
* Tâches accomplies et cochées (`[x]`) dans la note projet `P-`.
* Bilan complet de session (horaires, durée réelle, temps estimé sans IA, gain de productivité, tâches et verrous) consigné dans le journal de bord et métadonnées YAML du projet à jour.

## 💡 Exemples Concrets d'Exécution & Prompts Types

### Cas 1 : Démarrage d'une Session de Travail (Cadrage Cognitif)
- **Le Déclencheur Humain (Prompt Utilisateur) :**
  > Tapez dans votre terminal IA : `arca-resume 1-Projects/P-Arca-BrainOS.md` (ou dans le chat : *"Relance la session sur mon projet Arca-BrainOS"*).
- **État Initial (Avant la commande) :**
  L'utilisateur revient sur le projet après plusieurs jours d'absence. La note projet contient de nombreuses tâches et les comptes-rendus des sessions passées.
- **Orchestration Agentique (Compétence [[Skill_arca-resume]]) :**
  1. L'agent lit les 2 ou 3 dernières entrées du journal de bord pour comprendre l'historique récent et les verrous.
  2. Il identifie les prochains jalons à livrer dans `## 📌 Livrables & Jalons (Milestones)`.
  3. Il formule un diagnostic clair : État des lieux, Prochain livrable, et propose une **Intention de Session** ciblée (2 ou 3 actions clés).
  4. Dès validation par l'humain, il injecte le bloc de session actif horodaté au sommet de `## 🪵 Journal de Bord des Sessions` et ajoute une entrée dans `_Arca-BrainOS/log.md`.
- **État Final (Output) :**
  L'utilisateur est ré-immergé en 30 secondes sans fatigue mentale et la session est activement cadrée.

### Cas 2 : Clôture de Session & Calcul du ROI Temporel
- **Le Déclencheur Humain (Prompt Utilisateur) :**
  > Tapez dans votre terminal IA : `arca-close-session 1-Projects/P-Arca-BrainOS.md` (ou dans le chat : *"Ferme la session pour ce projet"*).
- **État Initial (Avant la commande) :**
  La session de travail est terminée, plusieurs tâches ont été accomplies et cochées (`[x]`).
- **Orchestration Agentique (Compétence [[Skill_arca-close-session]]) :**
  1. L'agent inventorie les tâches réalisées et les tâches restantes par sous-sections.
  2. Il demande à l'utilisateur sa durée réelle de travail (ex: "45 minutes").
  3. Il estime le temps qu'aurait pris ce travail sans IA (benchmark MIT/Harvard) et calcule le temps net économisé ainsi que le multiplicateur de vitesse (ex: vitesse x4.5).
  4. Il rédige le compte-rendu complet de la session au sommet du journal de bord et met à jour les métadonnées cumulées du YAML (`sessions_count`, `total_real_duration`, `total_time_saved`).
  5. Il consigne la fermeture dans `_Arca-BrainOS/log.md`.
- **État Final (Output) :**
  Le travail est capitalisé, les progrès sont mesurables et la mémoire du projet est préservée.

### 🔗 Compétences Agentiques Associées
- [[Skill_arca-resume]] : Cadrage cognitif et initiation horodatée du journal de session.
- [[Skill_arca-close-session]] : Clôture de session, bilan d'avancement, calcul de productivité ROI et consolidation YAML.

## Douleurs principales
* Oublier où l'on s'était arrêté lors de la dernière session de travail (perte de contexte cognitif).
* Procrastination de démarrage par manque d'intention claire.
* Projets qui meurent ou stagnent faute d'évaluation réaliste du temps investi et du ROI de l'IA.

---

## Intégration IA & Répartition Humain/Machine

| Étape | Levier | Solution Technique (Skill / n8n) | Rôle Humain & Arbitrage | Statut |
| :--- | :--- | :--- | :--- | :--- |
| **1. Cadrage & Ré-immersion** | **Agent IA** | Commande `arca-resume` (Scanne le projet, horodate l'ouverture HH:mm & initie la session dans le journal). | **Intention** : Confirmer ou ajuster le focus proposé par l'IA. | 🟢 (Opérationnel) |
| **2. Exécution du travail** | **Agent + Humain** | Pair-programming, génération d'écrits assistée. | **Créativité & Jugement** : Décisions stratégiques et rédaction. | 🟢 (Opérationnel) |
| **3. Clôture & Journalisation** | **Agent IA** | Commande `arca-close-session` (Horodate de fin, calcul durée/ROI sans IA, mise à jour tâches & YAML cumulé). | **Validation** : Vérifier l'exactitude du bilan rédigé. | 🟢 (Opérationnel) |

### 🧠 Part d'Arbitrage Humain & Gaps IA (Les ~20% restants)
* **Discipline de déclenchement (Risque d'oubli humain)** : L'IA ne peut pas détecter passivement le début ou la fin d'un temps de travail. L'humain doit penser à lancer `arca-resume` pour cadrer et horodater la session, et impérativement exécuter `arca-close-session` à la clôture pour finaliser la durée et alimenter le ROI cumulé.
* **Choix du projet et de l'instant de travail** : L'IA n'initie pas les sessions de travail ; l'humain garde le contrôle du timing et de l'énergie.
* **Arbitrage des priorités métier** : Si une urgence survient pendant le run, l'humain réoriente l'intention.
* **Garantie de souveraineté des contenus** : L'IA ne réécrit pas la vision humaine dans les notes `P-`.

**Pipeline complet** : `arca-resume` (Cadrage Agent + Horodate Début + Init Journal) $\rightarrow$ Clarification Intention (Humain) $\rightarrow$ Session Deep Work (Co-création) $\rightarrow$ `arca-close-session` (Clôture, Horodate Fin, Calcul ROI & Log Agent).
