---
Id: "202607162356"
category: Process
date-created: "2026-07-16"
tags:
  - process
  - media
  - pkm
  - ia
---
# Process : Ingestion & Distillation de Médias

- **Fréquence** : Daily / Weekly (dès qu'un média à forte valeur ajoutée est consommé).
- **Déclencheur** : Découverte d'une vidéo YouTube, d'un podcast ou d'un article de référence.
- **Temps actuel** : ~1.5h à 3h par média (écoute passive + prise de notes manuelle + classement).

---
## Input
* Transcripts bruts YouTube, notes de lecture, articles web capturés dans `0-Inbox/`.
* Vos projets actifs `P-` dans `1-Projects/` pour l'analyse d'impact.

## Étapes
1. **Capturer la source brute** : Importer le transcript de la vidéo ou du média dans `0-Inbox/` (via `arca-youtube [URL]` ou web clipper).
2. **Générer la distillation conceptuelle** : L'IA rédige la synthèse conceptuelle structurée `AI-Distil-[Nom]` dans `2-Ressources/IA-generated/` via la compétence `arca-synthesize`.
3. **Ancrer dans les Thèmes MOC** : L'IA met à jour les fiches thématiques associées (`T-`) dans `2-Ressources/Themes/` via `arca-converge`.
4. **Analyser l'impact sur les projets** : L'IA propose des tâches d'action concrètes raccordées à vos projets actifs `P-` via `arca-impact`.
5. **Archiver la note brute** : Le transcript brut est déplacé de `0-Inbox/` vers `2-Ressources/Notes/`.

## Méthode & Critères de Qualité
* **Zone d'écriture IA** : Les synthèses générées sont TOUJOURS écrites dans `2-Ressources/IA-generated/` sans écraser les notes humaines.
* **À faire absolument (DO)** :
  * Conserver le lien vers la source originelle (`url`).
  * Valider les tâches proposées par `arca-impact` avant injection dans un projet humain.
* **À éviter absolument (DON'T)** :
  * Ne pas créer de notes orphelines sans MOC.
  * Ne pas modifier le contenu rédigé par l'humain dans les projets.

## Output
* Fichier brut déplacé dans `/2-Ressources/Notes/`.
* MOCs `T-` mis à jour avec les liens de la synthèse.
* Tâches de projet créées ou mises à jour dans `/1-Projects/`.

## 💡 Exemples Concrets d'Exécution & Prompts Types

### Cas 1 : Ingestion d'une Vidéo YouTube
- **Le Déclencheur Humain (Prompt Utilisateur) :**
  > Tapez dans votre terminal IA : `arca-youtube https://www.youtube.com/watch?v=...`
- **Orchestration Agentique (Compétence [[Skill_arca-youtube]]) :**
  Récupère la transcription textuelle, normalise les métadonnées (`url`, `category: media`) et génère la note brute dans `0-Inbox/Youtube/`.

### Cas 2 : Master Pipeline de Distillation Complète
- **Le Déclencheur Humain (Prompt Utilisateur) :**
  > Tapez dans votre terminal IA : `arca-distill 0-Inbox/Youtube/transcript-video.md`
- **Orchestration Agentique en 4 Temps (Compétence [[Skill_arca-distill]]) :**
  1. **Synthèse Conceptuelle ([[Skill_arca-synthesize]]) :** Rédige la synthèse structurée `AI-Distil-[Nom].md` dans `2-Ressources/IA-generated/` avec concepts clés, citation et métadonnées normalisées.
  2. **Ancrage Thématique ([[Skill_arca-converge]]) :** Met à jour la fiche Thème correspondante (`T-[Sujet].md`) dans `2-Ressources/Themes/` en intégrant le nouveau lien wikilink.
  3. **Analyse d'Impact Projets ([[Skill_arca-impact]]) :** Scanne les projets actifs `P-` et propose des actions concrètes découlant des nouveaux apprentissages.
  4. **Archivage Physique :** Déplace la note brute traitée hors de l'Inbox.
- **État Final (Output) :**
  Savoir extrait, indexé dans les MOCs thématiques, raccordé aux projets actifs et zéro encombrement d'Inbox.

### 🔗 Compétences Agentiques Associées
- [[Skill_arca-distill]] : Master skill d'orchestration de bout en bout.
- [[Skill_arca-synthesize]] : Rédaction de la note conceptuelle `AI-Distil-`.
- [[Skill_arca-converge]] : Ancrage structurel dans les Thèmes MOC (`T-`).
- [[Skill_arca-impact]] : Dérivation d'actions concrètes pour les projets actifs (`P-`).
- [[Skill_arca-youtube]] : Extraction de transcriptions vidéo vers l'Inbox.

## Douleurs principales
* Oublier 90% des enseignements d'une vidéo ou d'un podcast 48h après l'avoir écouté.
* Le temps et l'énergie requis pour faire une synthèse écrite de qualité.
* L'absence de connexion entre la théorie apprise (médias) et l'action réelle (projets).

## Intégration IA & Répartition Humain/Machine

| Étape | Levier | Solution Technique (Skill / n8n) | Rôle Humain & Arbitrage | Statut |
| :--- | :--- | :--- | :--- | :--- |
| **1. Capture de la source** | **Humain (assisté) / Auto** | Import manuel OU automatique via [[Script-get-Youtube-video]] (n8n). | **Filtre d'intention** : Choisir quelle source merite d'être capturée. | 🟢 (Opérationnel) |
| **2. Transcription** | **Automatisation** | Commande `arca-youtube [URL]` pour générer la note brute transcrite. | **Gaps IA** : Saisie manuelle / dictée pour livres physiques ou audio sans transcript. | 🟢 (Opérationnel) |
| **3. Distillation sémantique** | **Agent** | Commande `arca-distill [Fichier]` (déclenche `arca-synthesize`). | **Arbitrage fusions** : Décider s'il faut créer une nouvelle note ou fusionner avec une note existante. | 🟢 (Opérationnel) |
| **4. Convergence MOC / Index** | **Automatisation** | Workflow `arca-converge` qui met à jour l'index, le log et les thèmes `T-`. | **Surveillance** : Vérification passive du maillage sémantique. | 🟢 (Opérationnel) |
| **5. Analyse d'impact** | **Agent + Humain** | Workflow interactif `arca-impact` qui propose et insère les tâches de projet. | **Décision d'action** : Valider ou refuser les tâches proposées avant modification des projets `P-`. | 🟢 (Opérationnel) |
| **6. Archivage final** | **Automatisation** | Déplacement de la note brute vers le dossier Notes via l'API de fichiers. | **Contrôle** : Validation du rangement physique final. | 🟢 (Opérationnel) |

### 🧠 Part d'Arbitrage Humain & Gaps IA (Les ~20% restants)
* **Filtre de pertinence (Entrée)** : L'IA ne décide pas du choix des médias consommés. L'humain garde le contrôle sur l'intention d'apprentissage et la qualité des sources.
* **Médias hors-YouTube / Audio pur / Livres physiques** : Absence de transcription automatique pour les livres papier ou certains podcasts fermés, nécessitant une prise de notes/dictée initiale par l'humain.
* **Arbitrage des fusions et des doublons** : Choisir si un nouvel apport complète une note `AI-Distil-` existante (ex: Eliott Meunier) ou s'il justifie une note autonome.
* **Validation des actions sur les projets** : Seul l'humain valide l'ajout de tâches `- [ ]` dans ses projets actifs `P-` (respect inconditionnel du style et des priorités humaines).

**Pipeline complet** : URL/Livre (Humain) $\rightarrow$ `arca-youtube` (Auto) $\rightarrow$ `arca-distill` (Agent) $\rightarrow$ `arca-converge` (Auto) $\rightarrow$ `arca-impact` (Interactif Agent/Humain) $\rightarrow$ Déplacement de fichier (Auto).
