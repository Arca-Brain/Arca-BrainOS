---
id: "202607172326"
category: Process
date_created: "2026-07-17"
tags:
  - process
  - inbox
  - pkm
  - ia
---
# Process : Inbox Clean & Dispatch

- **Fréquence** : Daily / Weekly (Idéalement en fin de journée ou lors de la revue hebdomadaire).
- **Déclencheur** : Accumulation de notes brutes, vocaux, idées volantes ou fichiers capturés dans `0-Inbox/`.

---

## Input
* Fichiers bruts situés dans `0-Inbox/` (notes de réunion, vocaux retranscrits, captures web, PDFs).
* Structure des thèmes MOC (`T-`) dans `2-Ressources/Themes/` et projets actifs (`P-`) dans `1-Projects/`.

## Étapes
1. **Lancer le triage IA** : Invoquer la commande `arca-inbox-process` (ou `/inbox-process`) sur le dossier `0-Inbox/`.
2. **Normaliser le YAML** : L'IA nettoie et formate les métadonnées (`id`, `category`, `tags`, `status`).
3. **Détecter les doublons & structurer les contenus** :
   - Si la note est une source externe (vidéo, podcast, livre) ➔ Aiguiller automatiquement vers `arca-distill`.
   - Si la note est une idée personnelle / pensée volante ➔ Invoquer `arca-organize-idea` (Conserver la Note Brute + Formuler l'Idée Clé + Générer les Actions Projets & Maillage).
4. **Valider les propositions d'actions & maillage** : L'humain accepte ou ajuste les actions projets et correspondances suggérées par l'IA.
5. **Conserver ou déplacer la note** : Garder la note d'idée dans `0-Inbox/` si des actions restent à planifier, ou la ranger dans `2-Ressources/Notes/` ou `1-Projects/`.

## Méthode & Critères de Qualité
* **Structure requise** : L'Inbox doit tendre vers "Inbox Zero" à la fin de chaque session d'hygiène.
* **À faire absolument (DO)** :
  * Détecter systématiquement si une note brute est une ressource externe à distiller ou une note personnelle.
  * Valider les liens wikilinks proposés avant déplacement.
* **À éviter absolument (DON'T)** :
  * Ne pas laisser s'accumuler plus de 10 notes brutes dans l'Inbox sans traitement.
  * Ne pas classer une note sans un frontmatter YAML propre.

## Output
* Inbox vidée ou qualifiée ("Inbox Zero").
* Sources externes transférées vers le pipeline de distillation (`arca-distill`).
* Notes personnelles qualifiées et classées dans leur dossier définitif.

## Exemples
* Session de triage de l'Inbox avec qualification automatique de notes vocales et d'articles web.

## Douleurs principales
* Accumulation de fouillis numérique ("Inbox infini") créant de la charge mentale.
* Perte de notes personnelles saisies à la volée faute de maillage immédiat.

---

## Intégration IA & Répartition Humain/Machine

| Étape | Levier | Solution Technique (Skill / n8n) | Rôle Humain & Arbitrage | Statut |
| :--- | :--- | :--- | :--- | :--- |
| **1. Analyse & Normalisation** | **Agent IA** | Commande `arca-inbox-process` (Analyse sémantique & YAML). | **Aucun** : Exécution automatique de la propreté YAML. | 🟢 (Opérationnel) |
| **2. Triage & Aiguillage** | **Agent IA** | Détection automatique : Source externe vs Note personnelle. | **Validation** : Valider la nature de la note en cas d'ambiguïté. | 🟢 (Opérationnel) |
| **3. Initialisation Directe** | **Agent IA** | Skill `arca-create-note` (`create-project`, `create-theme`, `create-domaine`). | **Intention** : Spécifier le titre, le domaine et le thème de la nouvelle note. | 🟢 (Opérationnel) |
| **4. Proposition de maillage** | **Agent IA** | Suggestion de wikilinks vers `T-` et `P-`. | **Arbitrage** : Accepter ou refuser les liens sémantiques. | 🟢 (Opérationnel) |
| **5. Classement physique** | **Automatisation** | Déplacement du fichier vers son dossier permanent (`1-Projects/`, `2-Ressources/Themes/`, etc.). | **Contrôle** : Validation du dossier cible. | 🟢 (Opérationnel) |

### 🧠 Part d'Arbitrage Humain & Gaps IA (Les ~20% restants)
* **Intention de capture** : Seul l'humain décide de capturer une idée volante initiale.
* **Résolution des ambiguïtés** : Quand une note personnelle touche à plusieurs domaines, l'humain choisit le projet/thème principal.
* **Refus de liens non pertinents** : L'humain garde le filtre de pertinence sur les connexions suggérées par l'IA.

**Pipeline complet** : Fichier brut dans Inbox ➔ `arca-inbox-process` (Agent IA) ➔ Validation Maillage (Humain) ➔ Archivage (Auto).
