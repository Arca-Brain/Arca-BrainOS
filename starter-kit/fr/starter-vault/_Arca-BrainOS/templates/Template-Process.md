---
id: "{{date:YYYYMMDD}}{{time:HHmm}}"
category: Process
trigger: "manual" # Options: daily | weekly | monthly | manual | on-trigger
date_created: "{{date:YYYY-MM-DD}}"
tags:
  - process
---
# Process : [Nom du Process]

- **Fréquence** : Daily / Weekly / Monthly / On Trigger / Manuel
- **Déclencheur** : [Ce qui lance le process : ex. Réception d'un mail, lundi matin 9h, achat...]
- **Temps actuel** : [Estimation du temps passé manuellement en minutes/heures]

---
## Input
* [Ce dont tu as besoin pour commencer : données, fichiers, informations requises]
* [Exemple : Notes quotidiennes de la semaine, feedback précédent]

## Étapes
1. [Étape 1 : description précise]
2. [Étape 2 : description précise]
3. [Étape 3 : description précise]

## Méthode & Critères de Qualité
* **Structure requise** : [Détail de la forme finale attendue]
* **À faire absolument (DO)** : [Règles de style, ton, impératifs]
* **À éviter absolument (DON'T)** : [Ce que l'IA fait d'habitude et qu'il faut bannir]

## Output
* [Ce que tu produis à la fin : livrable précis attendu avec template si possible]
* [Lien vers un exemple parfait / Master Template de référence]

## Exemples
*À alimenter après les premières utilisations.*

## Douleurs principales
* [Inscrire ici la douleur principale, la frustration ou la perte de temps qui amène à devoir créer ce process.]

---

## Intégration IA & Répartition Humain/Machine

| Étape | Levier | Solution Technique (Skill / n8n) | Rôle Humain & Arbitrage | Statut |
| :--- | :--- | :--- | :--- | :--- |
| 1. [Nom Étape 1] | [Humain / Agent / Auto] | [Outil, Script, Skill, n8n] | [Filtre, validation, saisie] | 🟢 / 🟡 / 🔴 |
| 2. [Nom Étape 2] | [Humain / Agent / Auto] | [Outil, Script, Skill, n8n] | [Filtre, validation, saisie] | 🟢 / 🟡 / 🔴 |
| 3. [Nom Étape 3] | [Humain / Agent / Auto] | [Outil, Script, Skill, n8n] | [Filtre, validation, saisie] | 🟢 / 🟡 / 🔴 |

### 🧠 Part d'Arbitrage Humain & Gaps IA (Les ~20% restants)
* **Intention & Pertinence** : [Pourquoi et quand l'humain prend la décision de déclencher le processus]
* **Cas aux limites (Edge cases)** : [Gestion des exceptions, manques de données, ou fusions]
* **Validation finale** : [Droit de regard et contrôle qualité avant modification des projets/fichiers]

**Pipeline complet** : [Étape 1] ➔ [Étape 2] ➔ [Étape 3] ➔ [Livrable Final]
