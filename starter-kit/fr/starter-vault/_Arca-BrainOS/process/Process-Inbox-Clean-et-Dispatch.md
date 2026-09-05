---
Id: "202607172326"
category: Process
date-created: "2026-07-17"
tags:
  - process
  - inbox
  - pkm
  - ia
---
# Process : Inbox Clean & Dispatch

- **Fréquence** : Daily / Weekly (Idéalement en fin de journée ou lors de la revue hebdomadaire).
- **Déclencheur** : Accumulation de notes brutes, vocaux, idées volantes ou fichiers capturés dans `0-Inbox/`.
- **Fréquence** : Quotidienne ou hebdomadaire (session d'hygiène numérique).

---

## Input
* Fichiers bruts situés dans `0-Inbox/` (notes de réunion, vocaux retranscrits, captures web, PDFs).
* Structure des thèmes MOC (`T-`) dans `2-Ressources/Themes/` et projets actifs (`P-`) dans `1-Projects/`.

## Étapes
1. **Lancer le triage IA** : Invoquer la commande `arca-inbox-process` (ou `/inbox-process`) sur le dossier `0-Inbox/`.
2. **Normaliser le YAML** : L'IA nettoie et formate les métadonnées (Id, category, tags, status).
3. **Détecter les doublons & structurer les contenus** :
   - Si la note est une source externe (vidéo, podcast, livre) $\rightarrow$ Aiguiller automatiquement vers `arca-distill`.
   - Si la note est une idée personnelle / pensée volante $\rightarrow$ Invoquer `arca-organize-idea` (Conserver la Raw Note + Formuler l'Idée Clé + Générer les Actions Projets & Maillage).
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

## 💡 Exemples Concrets d'Exécution & Prompts Types

### Cas 1 : Traitement d'une Pensée Volante ou Idée Personnelle
- **Le Déclencheur Humain (Prompt Utilisateur) :**
  > Tapez dans votre terminal IA : `arca-inbox-process` (ou dans le chat : *"Trie mon Inbox et structure ma dernière idée"*).
- **État Initial (Input dans `0-Inbox/`) :**
  Une note brute de quelques lignes (ex: capture vocale sans frontmatter, titre vague, idées décousues).
- **Orchestration Agentique (Compétence [[Skill_arca-organize-idea]]) :**
  1. L'agent détecte qu'il s'agit d'une réflexion personnelle (et non d'un article externe).
  2. Il conserve l'intégralité du texte original dans une section `## 📝 Raw Note (Texte Brut d'Origine)`.
  3. Il reformule une **Idée Clé** synthétique en une phrase percutante.
  4. Il extrait les actions concrètes rattachées aux projets actifs (`P-`) et suggère les liens wikilinks vers les thèmes (`T-`).
  5. Il normalise les métadonnées YAML (`category: idea`, `tags: [...]`, `status: #reviewed`).
- **État Final (Output) :**
  La note est déplacée vers `2-Ressources/Notes/` et le projet concerné reçoit sa tâche à accomplir.

### Cas 2 : Réception d'un Article Web ou Document Externe
- **Le Déclencheur Humain (Prompt Utilisateur) :**
  > Tapez dans votre terminal IA : `arca-distill 0-Inbox/Article-Web-Capture.md`
- **État Initial (Input dans `0-Inbox/`) :**
  Une page web capturée via le web clipper ou un transcript brut.
- **Orchestration Agentique (Compétence [[Skill_arca-distill]]) :**
  1. Génération de la fiche conceptuelle `AI-Distil-[Nom].md` dans `2-Ressources/IA-generated/` ([[Skill_arca-synthesize]]).
  2. Ancrage automatique de la note dans la fiche Thème correspondante via [[Skill_arca-converge]].
  3. Scan d'impact sur les projets actifs via [[Skill_arca-impact]].
  4. Archivage physique de la note brute.
- **État Final (Output) :**
  L'Inbox est revenue à zéro, le savoir est distillé et ancré dans le graphe de connaissances.

### 🔗 Compétences Agentiques Associées
- [[Skill_arca-inbox-process]] : Triage, nettoyage YAML et routage de l'Inbox.
- [[Skill_arca-organize-idea]] : Structuration des idées brutes avec sanctuarisation de la pensée humaine.
- [[Skill_arca-distill]] : Master skill d'ingestion et distillation de sources externes.
- [[Skill_arca-create-note]] : Instanciation interactive de projets, thèmes et domaines.

## Douleurs principales
* Accumulation de fouillis numérique ("Inbox infini") créant de la charge mentale.
* Perte de notes personnelles saisies à la volée faute de maillage immédiat.

---

## Intégration IA & Répartition Humain/Machine

| Étape | Levier | Solution Technique (Skill / n8n) | Rôle Humain & Arbitrage | Statut |
| :--- | :--- | :--- | :--- | :--- |
| **1. Analyse & Normalisation** | **Agent IA** | Commande `arca-inbox-process` (Analyse sémantique & YAML). | **Aucun** : Exécution automatique de la propreté YAML. | 🟢 (Opérationnel) |
| **2. Triage & Aiguillage** | **Agent IA** | Détection automatique : Source externe vs Note personnelle. | **Validation** : Valider la nature de la note en cas d'ambiguïté. | 🟢 (Opérationnel) |
| **3. Initialisation & Chaînage** | **Agent IA** | Commande `arca-create-note` (`create-project`, `create-theme`, `create-domaine`). | **Validation Interactive** : Valider la proposition de maillage, l'instanciation en chaîne des nouveaux Thèmes (`themes`) et le scan de justification des Domaines (`areas`). | 🟢 (Opérationnel) |
| **4. Proposition de maillage** | **Agent IA** | Suggestion de wikilinks vers `T-` et `P-`. | **Arbitrage** : Accepter ou refuser les liens sémantiques. | 🟢 (Opérationnel) |
| **5. Classement physique** | **Automatisation** | Déplacement du fichier vers son dossier permanent (`1-Projects/`, `2-Ressources/Themes/`, etc.). | **Contrôle** : Validation du dossier cible. | 🟢 (Opérationnel) |

### 🧠 Part d'Arbitrage Humain & Gaps IA (Les ~20% restants)
* **Intention de capture** : Seul l'humain décide de capturer une idée volante initiale.
* **Résolution des ambiguïtés** : Quand une note personnelle touche à plusieurs domaines, l'humain choisit le projet/thème principal.
* **Refus de liens non pertinents** : L'humain garde le filtre de pertinence sur les connexions suggérées par l'IA.

**Pipeline complet** : Fichier brut dans Inbox $\rightarrow$ `arca-inbox-process` (Agent IA) $\rightarrow$ Validation Maillage (Humain) $\rightarrow$ Archivage (Auto).
