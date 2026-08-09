---
id: "202607162356"
category: Process
date_created: "2026-07-16"
tags:
  - process
  - media
  - pkm
  - ia
---
# Process : Ingestion & Distillation de Médias

- **Fréquence** : Daily / Weekly (dès qu'un média à forte valeur ajoutée est consommé).
- **Déclencheur** : Découverte d'une vidéo YouTube, d'un podcast ou d'un article de référence.

---
## Input
* Transcripts bruts YouTube, notes de lecture, articles web capturés dans `0-Inbox/`.
* Vos projets actifs `P-` et leçons `L-` dans `1-Projects/` pour l'analyse d'impact.
* Vos thèmes `T-` dans `2-Ressources/Themes/` (racine et sous-dossiers thématiques) pour la convergence.

## Étapes
1. **Capturer la source** : Capturer la source pour stocker la source brute dans `0-Inbox/`.
2. **Lancer la distillation** : Invoquer la commande `arca-distill [Nom-de-Fichier]` (ou `arca-distill` tout court).
3. **Générer la note de synthèse** : Le skill `arca-synthesize` crée la note `AI-Distil-[Nom]` dans `2-Ressources/IA-generated/`.
4. **Ancrer la note (Convergence MOC)** : Le skill `arca-converge` met à jour les cartes de contenu `T-` dans `2-Ressources/Themes/` et met à jour l'index.
5. **Évaluer l'impact sur les projets** : Le skill `arca-impact` scanne vos projets `P-` et propose d'y insérer des tâches concrètes.
6. **Archiver** : Déplacer la note d'Inbox brute vers sa destination physique finale sous `2-Ressources/Notes/`.

## Méthode & Critères de Qualité
* **Structure requise** : Frontmatter YAML strict avec guillemets `" "` et champ `status: "#new"`.
* **À faire absolument (DO)** :
  * Conserver la traçabilité de la source originale.
  * Valider les tâches proposées par `arca-impact` avant injection dans un projet humain.
* **À éviter absolument (DON'T)** :
  * Ne pas créer de notes orphelines sans MOC.
  * Ne pas modifier le contenu rédigé par l'humain dans les projets.

## Output
* Fichier brut déplacé dans `/2-Ressources/Notes/`.
* MOCs `T-` mis à jour avec les liens de la synthèse.
* Tâches de projet créées ou mises à jour dans `/1-Projects/`.

## Exemples
* Vidéo YouTube ou article web distillé avec succès en fiche `AI-Distil-`.

## Douleurs principales
* Oublier 90% des enseignements d'une vidéo ou d'un podcast 48h après l'avoir écouté.
* Le temps et l'énergie requis pour faire une synthèse écrite de qualité.
* L'absence de connexion entre la théorie apprise (médias) et l'action réelle (projets).

---

## Intégration IA & Répartition Humain/Machine

| Étape | Levier | Solution Technique (Skill / n8n) | Rôle Humain & Arbitrage | Statut |
| :--- | :--- | :--- | :--- | :--- |
| **1. Capture de la source** | **Humain (assisté) / Auto** | Import manuel ou via script d'ingestion. | **Filtre d'intention** : Choisir quelle source mérite d'être capturée. | 🟢 (Opérationnel) |
| **2. Transcription** | **Automatisation** | Commande `arca-youtube [URL]` pour générer la note brute transcrite. | **Gaps IA** : Saisie manuelle / dictée pour livres physiques sans transcript. | 🟢 (Opérationnel) |
| **3. Distillation sémantique** | **Agent** | Commande `arca-distill [Fichier]` (déclenche `arca-synthesize`). | **Arbitrage fusions** : Décider s'il faut créer une nouvelle note ou fusionner avec une note existante. | 🟢 (Opérationnel) |
| **4. Convergence MOC / Index** | **Automatisation** | Workflow `arca-converge` qui met à jour l'index, le log et les thèmes `T-`. | **Surveillance** : Vérification passive du maillage sémantique. | 🟢 (Opérationnel) |
| **5. Analyse d'impact** | **Agent + Humain** | Workflow interactif `arca-impact` qui propose et insère les tâches de projet. | **Décision d'action** : Valider ou refuser les tâches proposées avant modification des projets `P-`. | 🟢 (Opérationnel) |
| **6. Archivage final** | **Automatisation** | Déplacement de la note brute vers le dossier Notes via l'API de fichiers. | **Contrôle** : Validation du rangement physique final. | 🟢 (Opérationnel) |

### 🧠 Part d'Arbitrage Humain & Gaps IA (Les ~20% restants)
* **Filtre de pertinence (Entrée)** : L'IA ne décide pas du choix des médias consommés.
* **Arbitrage des fusions et des doublons** : Choisir si un nouvel apport complète une note `AI-Distil-` existante.
* **Validation des actions sur les projets** : Seul l'humain valide l'ajout de tâches `- [ ]` dans ses projets actifs `P-`.

**Pipeline complet** : URL/Livre (Humain) ➔ `arca-youtube` (Auto) ➔ `arca-distill` (Agent) ➔ `arca-converge` (Auto) ➔ `arca-impact` (Interactif Agent/Humain) ➔ Déplacement de fichier (Auto).
