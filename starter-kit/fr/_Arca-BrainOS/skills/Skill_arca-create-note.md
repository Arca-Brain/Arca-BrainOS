---
name: arca-create-note
description: Instancier et mailler de manière interactive et assistée une note Projet (P-), Thème (T-) ou Domaine de vie (Area) avec validation humaine, détection des thèmes inexistants et scan de justification.
---

# 🛠️ Skill : arca-create-note (Création, Chaînage & Validation Interactive)

- **Processus de Référence :** [[Process-Inbox-Clean-et-Dispatch]] & [[Process-Capitalisation-et-Synthese-MOC]]

## Déclencheurs & Alias Spécifiques

Ce skill est déclenché par l'une des commandes ou alias suivants :

| Commande Directe / Alias | Action Immédiate Exécutée |
| :--- | :--- |
| `create-project`, `create-projet`, `arca-create-project`, `brain-create-project` | 🚀 Instancie un **Projet (`P-`)** dans `PATH_PROJECTS` |
| `create-incubation`, `arca-create-incubation`, `brain-create-incubation` | 🌱 Instancie un **Projet en Incubation (`P-`)** dans `PATH_PROJECTS/_Incubation` |
| `create-theme`, `arca-create-theme`, `brain-create-theme` | 📜 Instancie un **Thème (`T-`)** dans `PATH_THEMES` |
| `create-domaine`, `create-area`, `arca-create-area`, `brain-create-area` | 🧠 Instancie un **Domaine de Vie** dans `PATH_AREAS` |
| `create-note`, `arca-create-note`, `brain-create-note` | ❓ **Mode Interactif** (Demande quel type de note créer) |

---

## 🏛️ Règle d'Or : Validation Interactive Humaine
Avant toute modification ou création de fichier sur le disque, l'IA doit impérativement présenter ses propositions d'analyse (Domaines de vie rattachés, Thèmes MOCs existants, nouveaux Thèmes à créer, et Projets/Notes raccordés) et **demander la confirmation explicite de l'utilisateur** dans le chat.

---

## Workflow d'Exécution Séquentiel

### 1. Routage selon l'Alias Invoqué :
- **Si l'alias est spécifique** (ex: `create-project` ou `create-theme`) ➔ Sauter l'étape de qualification et exécuter directement la branche ciblée.
- **Si la commande est générique** (`create-note`) ➔ Demander à l'utilisateur : *"Quel type de note souhaites-tu créer : 1. Projet (`P-`), 2. Thème (`T-`), ou 3. Domaine de Vie ?"*

---

### 2. Branche A : Création d'un Projet (`P-[Nom-Projet].md`)

1. **Analyse Contextuelle & Scan des Connexions :**
   - Analyse le titre, le contexte ou la note brute source du projet.
   - Détermine la nature du projet :
     - **Projet intellectuel / recherche :** Vocation à s'adosser à des fiches de connaissances thématiques (`themes`).
     - **Projet pratique / vie réelle :** Vocation opérationnelle pure, ne requérant aucun Thème MOC (`themes: []`).
   - Scanne le Vault (`PATH_AREAS` et `PATH_THEMES`) pour identifier :
     - Le ou les **Domaines de Vie existants** rattachables (`areas`).
     - Les **Nouveaux Domaines de Vie suggérés** si aucun domaine existant ne correspond à ce pan de vie.
     - Le ou les **Thèmes (MOCs) existants** rattachés (`themes`).
     - Les **Nouveaux Thèmes suggérés** (si pertinent pour un projet intellectuel).

2. **Proposition Interactive à l'Humain :**
   Présenter clairement le diagnostic dans le chat :
   - 📌 **Nom du projet proposé :** `P-[Nom-Projet]`
   - 🚦 **Statut & Emplacement :**
     - **Actif :** Création à la racine `PATH_PROJECTS` (`status: "active"`, tag `statut/actif`)
     - **En incubation (Someday/Maybe) :** Création dans `PATH_PROJECTS/_Incubation/` (`status: "someday"`, tag `statut/someday`)
   - 🧠 **Domaine(s) de Vie :**
     - Si domaine existant : `[[Domaine-Existant]]`
     - Si nouveau domaine requis : `[[Nouveau-Domaine]]` *(Non présent dans `PATH_AREAS` : création proposée)*
   - 📜 **Thème(s) MOC :**
     - Si projet intellectuel : `[[T-Theme-Existant]]` ou `[[T-Nouveau-Theme]]` *(création proposée)*
     - Si projet pratique : *Aucun thème nécessaire (projet d'action concrète)* $\rightarrow$ `themes: []`
   - ⚠️ **Garde-fou en cas d'absence de Domaine :** Si l'utilisateur demande à ne spécifier aucun domaine, l'alerter :
     > *"Attention : sans Domaine de Vie rattaché, le projet n'apparaîtra pas dans la matrice de focalisation de `Home.md`. Nous te recommandons d'y associer au moins un domaine de responsabilité."*
   - ❓ **Demande de validation :** *"Valides-tu ce maillage et le statut (Actif ou Incubation) ? Souhaites-tu instancier dans la foulée le(s) nouveau(x) domaine(s) ou thème(s) ?"*

3. **Exécution & Chaînage (Après validation explicite) :**
   - **Si projet Actif :** Instancier `P-[Nom-Projet].md` dans `PATH_PROJECTS` avec `PATH_SYSTEM/templates/Template-Projet.md` (`status: "active"`, tag `statut/actif`). Renseigner la note dans `### 🏁 Projets & chantiers de l'année` des Domaines rattachés.
   - **Si projet en Incubation :** Instancier `P-[Nom-Projet].md` dans `PATH_PROJECTS/_Incubation/` avec `PATH_SYSTEM/templates/Template-Projet.md` (`status: "someday"`, tag `statut/someday`). Le projet s'affiche automatiquement dans la table Dataview d'incubation du Domaine rattaché.
   - **Chaînage Domaine de Vie :** Si un nouveau domaine a été validé, instancier immédiatement `[Nouveau-Domaine].md` dans `PATH_AREAS` avec `PATH_SYSTEM/templates/Template-Area.md`, et inscrire l'entrée dans `PATH_AREAS/README.md`.
   - **Chaînage Thème MOC :** Si un nouveau thème a été validé, instancier immédiatement `T-Nouveau-Theme.md` dans `PATH_THEMES` avec `PATH_SYSTEM/templates/Template-Theme.md`.
   - Journaliser l'instanciation et les créations en chaîne dans `PATH_SYSTEM/log.md`.

---

### 3. Branche B : Création d'un Thème (`T-[Nom-Theme].md`)

1. **Analyse Contextuelle & Scan des Connexions :**
   - Analyse le périmètre et la vision du thème.
   - Scanne `PATH_AREAS` pour identifier le ou les **Domaines de Vie parents** (`areas`).
   - Scanne `PATH_PROJECTS`, `PATH_ARCHIVES` et `PATH_NOTES` pour repérer les **Projets et Notes existants** rattachables à ce thème.

2. **Proposition Interactive à l'Humain :**
   Présenter clairement le diagnostic dans le chat :
   - 📜 **Nom du Thème proposé :** `T-[Nom-Theme]`
   - 🧠 **Domaine(s) de Vie parent(s) suggéré(s) :** `[[Domaine-Parent]]`
   - 🔗 **Projets & Notes existants à lier :** `[[P-Projet-1]]`, `[[Note-1]]`
   - ❓ **Demande de validation :** *"Confirmes-tu l'ouverture de ce thème et le raccordement de ces projets et notes existants ?"*

3. **Exécution (Après validation explicite) :**
   - Instancier `T-[Nom-Theme].md` dans `PATH_THEMES` avec [`Template-Theme.md`](file:///home/chug/2ndBrain/_Arca-BrainOS/templates/Template-Theme.md).
   - Mettre à jour les métadonnées `themes` des projets et notes validés.
   - Raccorder le thème aux fiches de Domaines parents.
   - Journaliser l'action dans `PATH_SYSTEM/log.md`.

---

### 4. Branche C : Création d'un Domaine de Vie (`[Nom-Domaine].md`)

1. **Scan de Justification & Audit du Vault :**
   - Scanne l'ensemble du Vault (`PATH_PROJECTS`, `PATH_ARCHIVES`, `PATH_THEMES`, `PATH_NOTES`) pour faire un **bilan de justification** : repérer les projets actifs, projets archivés, thèmes et notes orphelins qui légitiment l'ouverture de ce nouveau Domaine de responsabilité.

2. **Proposition Interactive & Rapport de Justification :**
   Présenter à l'utilisateur :
   - 🧠 **Nom du Domaine de Vie proposé :** `[Nom-Domaine]`
   - 📊 **Analyse de Justification (Contenu du Vault concerné) :**
     - Projets actifs & archivés à regrouper : `[[P-Projet-A]]`, `[[P-Projet-B]]`
     - Thèmes associés : `[[T-Theme-X]]`
   - 🎯 **Périmètre visé & Standard d'exigence proposé.**
   - ❓ **Demande de validation :** *"Confirmes-tu la création de ce Domaine de Vie et le rattachement de ces projets et thèmes ?"*

3. **Exécution (Après validation explicite) :**
   - Instancier `[Nom-Domaine].md` dans `PATH_AREAS` avec `PATH_SYSTEM/templates/Template-Area.md`.
   - Inscrire l'entrée dans `PATH_AREAS/README.md`.
   - Mettre à jour les métadonnées `areas` des projets et thèmes rattachés.
   - Journaliser l'action dans `PATH_SYSTEM/log.md`.

---

## 🛡️ Garde-fous & Sécurité
- **Bannissement du Tiret Cadratin :** Ne jamais utiliser de tiret cadratin (`—`) dans les synthèses ou notes rédigées pour l'utilisateur (remplacer par des deux-points `:`, des virgules `,` ou des parenthèses `()`).
- **Seuil de Modification Massive :** Si une création ou un maillage implique plus de 3 fichiers simultanés, solliciter une confirmation explicite dédiée dans le chat.
- **Transparence & Traçabilité :** Fournir un rapport d'exécution clair et concis dans le message de sortie.
